---
title: Configurer Azure Key Vault à l’aide de CLI
description: Comment configurer Key Vault pour les machines virtuelles avec Azure CLI ?
author: mimckitt
ms.service: virtual-machines
ms.subservice: security
ms.workload: infrastructure-services
ms.topic: how-to
ms.date: 02/24/2017
ms.author: mimckitt
ms.custom: devx-track-azurecli
ms.openlocfilehash: 84a88c9c563141d6e6e9ba1584d577addcade8fe
ms.sourcegitcommit: f28ebb95ae9aaaff3f87d8388a09b41e0b3445b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "102565221"
---
# <a name="how-to-set-up-key-vault-for-virtual-machines-with-the-azure-cli"></a>Comment configurer Key Vault pour les machines virtuelles avec Azure CLI

Dans la pile Azure Resource Manager, les secrets/certificats sont modélisés en tant que ressources fournies par Key Vault. Pour en savoir plus sur Azure Key Vault, consultez [Qu’est-ce qu’Azure Key Vault ?](../../key-vault/general/overview.md) Pour que Key Vault puisse être utilisé avec des machines virtuelles Azure Resource Manager, la propriété *EnabledForDeployment* doit être définie sur true dans Key Vault. Cet article explique comment configurer Key Vault pour l’utiliser avec des machines virtuelles Azure à l’aide d’Azure CLI. 

Pour suivre ces étapes, vous avez besoin de la dernière version [d’Azure CLI](/cli/azure/install-az-cli2) et devez vous connecter à un compte Azure avec [az login](/cli/azure/reference-index).

## <a name="create-a-key-vault"></a>Créer un coffre de clés
Créez un coffre de clés et affectez la stratégie de déploiement avec [az keyvault create](/cli/azure/keyvault). L’exemple suivant crée un coffre de clés nommé `myKeyVault` dans le groupe de ressources `myResourceGroup` :

```azurecli
az keyvault create -l westus -n myKeyVault -g myResourceGroup --enabled-for-deployment true
```

## <a name="update-a-key-vault-for-use-with-vms"></a>Mettre à jour un coffre de clés pour l’utiliser avec des machines virtuelles
Définissez la stratégie de déploiement sur un coffre de clés avec [az keyvault update](/cli/azure/keyvault). Les mises à jour suivantes créent un coffre de clés nommé `myKeyVault` dans le groupe de ressources `myResourceGroup` :

```azurecli
az keyvault update -n myKeyVault -g myResourceGroup --set properties.enabledForDeployment=true
```

## <a name="use-templates-to-set-up-key-vault"></a>Utilisation de modèles pour configurer Key Vault
Quand vous utilisez un modèle, vous devez définir la propriété `enabledForDeployment` sur `true` pour la ressource Key Vault de la façon suivante :

```json
{
    "type": "Microsoft.KeyVault/vaults",
    "name": "ContosoKeyVault",
    "apiVersion": "2015-06-01",
    "location": "<location-of-key-vault>",
    "properties": {
    "enabledForDeployment": "true",
    ....
    ....
    }
}
```

## <a name="next-steps"></a>Étapes suivantes
Pour connaître les autres options que vous pouvez configurer lorsque vous créez un coffre de clés à l’aide de modèles, consultez la rubrique [Créer un coffre de clés](https://azure.microsoft.com/documentation/templates/101-key-vault-create/).
