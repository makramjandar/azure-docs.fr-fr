---
title: Créer un cloud privé Azure VMware Solution
description: Étapes de création d’un cloud privé Azure VMware Solution à l’aide du portail Azure.
ms.topic: include
ms.date: 04/07/2021
ms.openlocfilehash: 6b4e5631d1a4b6c5bf56b01aba12752595ef63b8
ms.sourcegitcommit: 6ed3928efe4734513bad388737dd6d27c4c602fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2021
ms.locfileid: "107073612"
---
<!-- Used in deploy-azure-vmware-solution.md and tutorial-create-private-cloud.md -->

1. Connectez-vous au [portail Azure](https://portal.azure.com).

1. Sélectionnez **Créer une ressource**. Dans la zone de texte **Rechercher dans la Place de marché**, tapez `Azure VMware Solution`, puis sélectionnez **Azure VMware Solution** dans la liste. Dans la fenêtre **Azure VMware Solution**, sélectionnez **Créer**.

1. Sous l’onglet **De base**, entrez des valeurs pour les champs. Le tableau suivant liste les propriétés des champs.

   | Champ   | Valeur  |
   | ---| --- |
   | **Abonnement** | Abonnement que vous prévoyez d’utiliser pour le déploiement.|
   | **Groupe de ressources** | Groupe de ressources pour vos ressources de cloud privé. |
   | **Lieu** | Sélectionnez un emplacement, comme **USA Est**.|
   | **Nom de la ressource** | Nom de votre cloud privé Azure VMware Solution. |
   | **Référence (SKU)** | Sélectionnez la valeur de référence SKU suivante : AV36 |
   | **Hôtes** | Nombre d’hôtes à ajouter au cluster du cloud privé. La valeur par défaut est 3. Elle peut être augmentée ou diminuée après le déploiement.  |
   | **Bloc d’adresses** | Entrez un bloc d’adresses IP pour le réseau CIDR pour le cloud privé, par exemple 10.175.0.0/22. |
   | **Réseau virtuel** | Sélectionnez un réseau virtuel ou créez-en un pour le cloud privé Azure VMware Solution.  |

   :::image type="content" source="../media/tutorial-create-private-cloud/create-private-cloud.png" alt-text="Sous l’onglet De base, entrez des valeurs pour les champs." border="true":::

1. Quand vous avez terminé, sélectionnez **Vérifier + créer**. Dans l’écran suivant, vérifiez les informations entrées. Si elles sont toutes correctes, sélectionnez **Créer**.

   > [!NOTE]
   > Cette étape prend environ 3 à 4 minutes. L’ajout d’un seul nœud dans un cluster existant/le même cluster prend entre 30 et 45 minutes.

1. Vérifiez que déploiement a réussi. Accédez au groupe de ressources que vous avez créé et sélectionnez votre cloud privé.  Quand le déploiement est terminé, vous voyez l’état **Réussi**. 

   :::image type="content" source="../media/tutorial-create-private-cloud/validate-deployment.png" alt-text="Vérifiez que déploiement a réussi." border="true":::
