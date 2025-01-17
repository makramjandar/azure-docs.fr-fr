---
title: Déployer et configurer Azure VMware Solution
description: Découvrez comment utiliser les informations collectées au cours de la phase de planification pour déployer et configurer le cloud privé Azure VMware Solution.
ms.topic: tutorial
ms.custom: contperf-fy21q3
ms.date: 02/17/2021
ms.openlocfilehash: 48b6927407a95d41603c3032f298ffc28def9693
ms.sourcegitcommit: f28ebb95ae9aaaff3f87d8388a09b41e0b3445b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "103462454"
---
# <a name="deploy-and-configure-azure-vmware-solution"></a>Déployer et configurer Azure VMware Solution

Dans cet article, vous allez utiliser les informations de la [section de planification](production-ready-deployment-steps.md) pour déployer et configurer Azure VMware Solution. 

>[!IMPORTANT]
>Si vous n’avez pas encore défini ces informations, revenez à la [section de planification](production-ready-deployment-steps.md) avant de continuer.


## <a name="create-an-azure-vmware-solution-private-cloud"></a>Créer un cloud privé Azure VMware Solution

Respectez les conditions préalables et suivez les étapes du tutoriel [Créer un cloud privé Azure VMware Solution](tutorial-create-private-cloud.md). Vous pouvez créer un cloud privé Azure VMware Solution en utilisant le [portail Azure](tutorial-create-private-cloud.md#azure-portal) ou [Azure CLI](tutorial-create-private-cloud.md#azure-cli).  

>[!NOTE]
>Pour une vue d’ensemble de bout en bout de cette étape, consultez la vidéo [Azure VMware Solution : Déploiement](https://www.youtube.com/embed/gng7JjxgayI).

## <a name="create-the-jump-box"></a>Créer le serveur de renvoi

>[!IMPORTANT]
>Si vous avez laissé l’option **Réseau virtuel** vierge au cours de l’approvisionnement initial sur l’écran **Créer un cloud privé**, suivez le didacticiel [Configurer la mise en réseau pour votre cloud privé VMware](tutorial-configure-networking.md)**avant** de passer à cette section.  

Après le déploiement d’Azure VMware Solution, vous allez créer le serveur de rebond du réseau virtuel qui se connecte à vCenter et NSX. Une fois que vous avez configuré les circuits ExpressRoute et ExpressRoute Global Reach, le serveur de renvoi n’est pas nécessaire.  Mais il est pratique d’accéder à vCenter et à NSX dans votre Azure VMware Solution.  

:::image type="content" source="media/pre-deployment/jump-box-diagram.png" alt-text="Créer la jumpbox Azure VMware Solution" border="false" lightbox="media/pre-deployment/jump-box-diagram.png":::

Pour créer une machine virtuelle dans le réseau virtuel que vous avez [identifié ou créé dans le cadre du processus de déploiement](production-ready-deployment-steps.md#attach-azure-virtual-network-to-azure-vmware-solution), suivez les instructions ci-dessous : 

[!INCLUDE [create-avs-jump-box-steps](includes/create-jump-box-steps.md)]

## <a name="connect-to-a-virtual-network-with-expressroute"></a>Connexion à un réseau virtuel avec ExpressRoute

>[!IMPORTANT]
>Si vous avez déjà défini un réseau virtuel dans l’écran de déploiement dans Azure, passez à la section suivante.

Si vous n’avez pas défini de réseau virtuel à l’étape de déploiement et que vous avez l’intention de connecter ExpressRoute d’Azure VMware Solution à une passerelle ExpressRoute existante, suivez les étapes ci-dessous.

[!INCLUDE [connect-expressroute-to-vnet](includes/connect-expressroute-vnet.md)]

## <a name="verify-network-routes-advertised"></a>Vérifier les itinéraires réseau publiés

Le serveur de rebond se trouve dans le réseau virtuel où Azure VMware Solution se connecte via son circuit ExpressRoute.  Dans Azure, accédez à l’interface réseau du serveur de rebond et [affichez les itinéraires effectifs](../virtual-network/manage-route-table.md#view-effective-routes).

Dans la liste des itinéraires effectifs, vous devriez voir les réseaux créés dans le cadre du déploiement d’Azure VMware Solution. Vous verrez plusieurs réseaux dérivés du [réseau `/22` que vous avez défini](production-ready-deployment-steps.md#ip-address-segment-for-private-cloud-management) lors de la [création d’un cloud privé](#create-an-azure-vmware-solution-private-cloud).  

:::image type="content" source="media/pre-deployment/azure-vmware-solution-effective-routes.png" alt-text="Vérifiez les itinéraires réseau publiés à partir de Azure VMware Solution sur un réseau virtuel Azure" lightbox="media/pre-deployment/azure-vmware-solution-effective-routes.png":::

Dans cet exemple, le réseau 10.74.72.0/22 entré pendant le déploiement dérive les réseaux /24.  Si vous voyez un résultat similaire, vous pouvez vous connecter à vCenter dans Azure VMware Solution.

## <a name="connect-and-sign-in-to-vcenter-and-nsx-t"></a>Connectez-vous à vCenter et à NSX-T

Connectez-vous au serveur de rebond que vous avez créé à l’étape précédente. Une fois que vous êtes connecté, ouvrez un navigateur web et connectez-vous à vCenter et à NSX-T Manager.  

Vous pouvez identifier les adresses IP et les informations d’identification de vCenter et de la console NSX-T Manager dans le portail Azure.  Sélectionnez votre cloud privé, puis **Gérer** > **Identité**.

>[!TIP]
>Sélectionnez **Générer un nouveau mot de passe** pour générer de nouveaux mots de passe vCenter et NSX-T.

:::image type="content" source="media/tutorial-access-private-cloud/ss4-display-identity.png" alt-text="Affichez les URL et les informations d’identification vCenter et NSX Manager du cloud privé." border="true":::



## <a name="create-a-network-segment-on-azure-vmware-solution"></a>Créez un segment réseau dans Azure VMware Solution

Vous utilisez NSX-T Manager pour créer des segments réseau dans votre environnement Azure VMware Solution.  Vous avez défini les réseaux que vous souhaitez créer dans la [section de planification](production-ready-deployment-steps.md).  Si vous ne les avez pas définis, revenez à la [Section de planification](production-ready-deployment-steps.md) avant de continuer.

>[!IMPORTANT]
>Assurez-vous que le bloc d’adresses réseau CIDR que vous avez défini n’empiète sur rien dans vos environnements Azure ou locaux.  

Pour créer un segment réseau NSX-T dans Azure VMware Solution, suivez le didacticiel [Créer un segment réseau NSX-T dans Azure VMware Solution](tutorial-nsx-t-network-segment.md).

## <a name="verify-advertised-nsx-t-segment"></a>Vérifier le segment NSX-T publié

Revenez à l’étape [Vérifier les itinéraires réseau publiés](#verify-network-routes-advertised) . Vous verrez d’autres routes dans la liste représentant les segments réseau que vous avez créés à l’étape précédente.  

Pour les machines virtuelles, vous allez attribuer les segments que vous avez créés à l’étape [Créer un segment réseau sur Azure VMware Solution](#create-a-network-segment-on-azure-vmware-solution).  

Comme DNS est requis, identifiez le serveur DNS que vous souhaitez utiliser.  

- Si vous avez configuré ExpressRoute Global Reach, utilisez le serveur DNS que vous utiliserez en local.  
- Si vous avez un serveur DNS dans Azure, utilisez-le.  
- Si vous n’en avez pas, utilisez le serveur DNS que votre serveur de rebond utilise.

>[!NOTE]
>Cette étape consiste à identifier le serveur DNS, et aucune configuration n’est effectuée à cette étape.

## <a name="optional-provide-dhcp-services-to-nsx-t-network-segment"></a>(Facultatif) Fournir des services DHCP au segment réseau NSX-T

Si vous envisagez d’utiliser DHCP sur vos segments NSX-T, poursuivez la lecture de cette section. Dans le cas contraire, passez à la section [Ajouter une machine virtuelle sur le segment réseau NSX-T](#add-a-vm-on-the-nsx-t-network-segment) .  

Maintenant que vous avez créé votre segment réseau NSX-T, vous pouvez créer et gérer DHCP dans Azure VMware Solution de deux manières :

* Si vous utilisez NSX-T pour héberger votre serveur DHCP, vous devez [créer un serveur DHCP](manage-dhcp.md#create-a-dhcp-server) et [relayer vers ce serveur](manage-dhcp.md#create-dhcp-relay-service). 
* Si vous utilisez un serveur DHCP externe tiers sur votre réseau, vous devez [créer un service de relais DHCP](manage-dhcp.md#create-dhcp-relay-service).  Pour cette option, [vous devez uniquement effectuer la configuration du relais](manage-dhcp.md#create-dhcp-relay-service).


## <a name="add-a-vm-on-the-nsx-t-network-segment"></a>Ajouter une machine virtuelle au segment de réseau NSX-T

Dans votre Azure VMware Solution vCenter, déployez une machine virtuelle et utilisez-la pour vérifier la connectivité entre vos réseaux Azure VMware Solution et :

- Internet
- Réseaux virtuels Azure
- Local.  

Déployez la machine virtuelle comme vous le feriez dans n’importe quel environnement vSphere.  Attachez la machine virtuelle à l’un des segments réseau que vous avez créés précédemment dans NSX-T.  

>[!NOTE]
>Si vous configurez un serveur DHCP, vous obtenez la configuration réseau de la machine virtuelle à partir de celle-ci (n’oubliez pas d’en configurer l’étendue).  Si vous envisagez une configuration statique, configurez comme vous le feriez normalement.

## <a name="test-the-nsx-t-segment-connectivity"></a>Testez la connectivité des segments NSX-T

Connectez-vous à la machine virtuelle créée à l’étape précédente et vérifiez la connectivité.

1. Effectuez un test ping d’une adresse IP sur Internet.
2. Dans un navigateur web, accédez à un site Internet.
3. Effectuez un test ping sur le serveur de rebond qui se trouve sur le réseau virtuel Azure.

Azure VMware Solution est désormais opérationnel et vous avez pu établir une connectivité avec et depuis le réseau virtuel Azure et Internet.

## <a name="next-steps"></a>Étapes suivantes

Dans la section suivante, vous allez connecter Azure VMware Solution à votre réseau local via ExpressRoute.
> [!div class="nextstepaction"]
> [Connecter Azure VMware Solution à votre environnement local](azure-vmware-solution-on-premises.md)
