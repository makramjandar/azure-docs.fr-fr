---
title: Créer et gérer Azure Cosmos DB avec des modèles Resource Manager
description: Utiliser des modèles Azure Resource Manager afin de créer et configurer Azure Cosmos DB pour l’API Core (SQL)
author: markjbrown
ms.service: cosmos-db
ms.subservice: cosmosdb-sql
ms.topic: how-to
ms.date: 03/24/2021
ms.author: mjbrown
ms.openlocfilehash: dd70e196180c68d6a498d147493411e6d1703e59
ms.sourcegitcommit: 32e0fedb80b5a5ed0d2336cea18c3ec3b5015ca1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105034042"
---
# <a name="manage-azure-cosmos-db-core-sql-api-resources-with-azure-resource-manager-templates"></a>Gérer les ressources de l’API Core (SQL) Azure Cosmos DB à l’aide de modèles Azure Resource Manager

[!INCLUDE[appliesto-sql-api](includes/appliesto-sql-api.md)]

Dans cet article, vous apprenez à utiliser des modèles Azure Resource Manager pour faciliter le déploiement et la gestion de vos bases de données, conteneurs et comptes Azure Cosmos DB.

Cet article présente uniquement des exemples de modèles Azure Resource Manager pour des comptes de l’API Core (SQL). Vous trouverez également des exemples de modèles pour les API [Cassandra](templates-samples-cassandra.md), [Gremlin](templates-samples-gremlin.md), [MongoDB](templates-samples-mongodb.md) et [Table](templates-samples-table.md).

> [!IMPORTANT]
>
> * Les noms de compte sont limités à 44 caractères, tout en minuscules.
> * Pour changer les valeurs de débit, redéployez le modèle avec les valeurs de RU/s mises à jour.
> * Quand vous ajoutez ou supprimez des emplacements dans un compte Azure Cosmos, vous ne pouvez pas simultanément modifier d’autres propriétés. Ces opérations doivent être effectuées séparément.
> * Les ressources Azure Cosmos DB ne peuvent pas être renommées, car cela enfreint les règles de traitement des URI de ressources par Azure Resource Manager.

Pour créer l’une des ressources Azure Cosmos DB ci-dessous, copiez l’exemple de modèle suivant dans un nouveau fichier json. Vous pouvez éventuellement créer un fichier json de paramètres à utiliser lors du déploiement de plusieurs instances de la même ressource avec des valeurs et noms différents. Il existe de nombreuses façons de déployer des modèles Azure Resource Manager, notamment : le [Portail Azure](../azure-resource-manager/templates/deploy-portal.md), [Azure CLI](../azure-resource-manager/templates/deploy-cli.md), [Azure PowerShell](../azure-resource-manager/templates/deploy-powershell.md) et [GitHub](../azure-resource-manager/templates/deploy-to-azure-button.md).

<a id="create-autoscale"></a>

## <a name="azure-cosmos-account-with-autoscale-throughput"></a>Compte Azure Cosmos avec débit approvisionné en mode de mise à l’échelle automatique

Ce modèle crée un compte Azure Cosmos dans deux régions avec des options de cohérence et de basculement, ainsi qu’une base de données et un conteneur configurés pour le débit approvisionné en mode de mise à l’échelle automatique et dont la plupart des options de stratégie sont activées. Ce modèle est également disponible pour un déploiement en un clic à partir de la galerie de modèles de démarrage rapide Azure.

[:::image type="content" source="../media/template-deployments/deploy-to-azure.svg" alt-text="Déployer sur Azure":::](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-cosmosdb-sql-autoscale%2Fazuredeploy.json)

:::code language="json" source="~/quickstart-templates/101-cosmosdb-sql-autoscale/azuredeploy.json":::

<a id="create-analytical-store"></a>

## <a name="azure-cosmos-account-with-analytical-store"></a>Compte Azure Cosmos avec le magasin analytique

Ce modèle crée un compte Azure Cosmos dans une région avec un conteneur dont une durée de vie analytique est activée et avec des options de débit manuel ou de mise à l’échelle automatique. Ce modèle est également disponible pour un déploiement en un clic à partir de la galerie de modèles de démarrage rapide Azure.

[:::image type="content" source="../media/template-deployments/deploy-to-azure.svg" alt-text="Déployer sur Azure":::](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-cosmosdb-sql-analytical-store%2Fazuredeploy.json)

:::code language="json" source="~/quickstart-templates/101-cosmosdb-sql-analytical-store/azuredeploy.json":::

<a id="create-manual"></a>

## <a name="azure-cosmos-account-with-standard-provisioned-throughput"></a>Compte Azure Cosmos avec débit approvisionné en mode standard

Ce modèle crée un compte Azure Cosmos dans deux régions avec des options de cohérence et de basculement, ainsi qu’une base de données et un conteneur configurés pour le débit approvisionné en mode standard et dont la plupart des options de stratégie sont activées. Ce modèle est également disponible pour un déploiement en un clic à partir de la galerie de modèles de démarrage rapide Azure.

[:::image type="content" source="../media/template-deployments/deploy-to-azure.svg" alt-text="Déployer sur Azure":::](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-cosmosdb-sql%2Fazuredeploy.json)

:::code language="json" source="~/quickstart-templates/101-cosmosdb-sql/azuredeploy.json":::

<a id="create-sproc"></a>

## <a name="azure-cosmos-db-container-with-server-side-functionality"></a>Conteneur Azure Cosmos DB avec des fonctionnalités côté serveur

Ce modèle crée une base de données, un conteneur et un compte Azure Cosmos avec une procédure stockée, un déclencheur et une fonction définie par l’utilisateur. Ce modèle est également disponible pour un déploiement en un clic à partir de la galerie de modèles de démarrage rapide Azure.

[:::image type="content" source="../media/template-deployments/deploy-to-azure.svg" alt-text="Déployer sur Azure":::](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-cosmosdb-sql-container-sprocs%2Fazuredeploy.json)

:::code language="json" source="~/quickstart-templates/101-cosmosdb-sql-container-sprocs/azuredeploy.json":::

<a id="create-rbac"></a>

## <a name="azure-cosmos-db-account-with-azure-ad-and-rbac"></a>Compte Azure Cosmos DB avec Azure AD et RBAC

Ce modèle crée un compte SQL Cosmos, une définition de rôle gérée en mode natif et une attribution de rôle gérée en mode natif pour une identité AAD. Ce modèle est également disponible pour un déploiement en un clic à partir de la galerie de modèles de démarrage rapide Azure.

[:::image type="content" source="../media/template-deployments/deploy-to-azure.svg" alt-text="Déployer sur Azure":::](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-cosmosdb-sql-rbac%2Fazuredeploy.json)

:::code language="json" source="~/quickstart-templates/101-cosmosdb-sql-rbac/azuredeploy.json":::

<a id="free-tier"></a>

## <a name="free-tier-azure-cosmos-db-account"></a>Compte Azure Cosmos DB de niveau Gratuit

Ce modèle crée un compte Azure Cosmos de niveau Gratuit et une base de données avec un débit partagé qui peut être partagé avec un maximum de 25 conteneurs. Ce modèle est également disponible pour un déploiement en un clic à partir de la galerie de modèles de démarrage rapide Azure.

[:::image type="content" source="../media/template-deployments/deploy-to-azure.svg" alt-text="Déployer sur Azure":::](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-cosmosdb-free%2Fazuredeploy.json)

:::code language="json" source="~/quickstart-templates/101-cosmosdb-free/azuredeploy.json":::

## <a name="next-steps"></a>Étapes suivantes

Voici quelques ressources supplémentaires :

* [Documentation Azure Resource Manager](../azure-resource-manager/index.yml)
* [Schéma de fournisseurs de ressources Azure Cosmos DB](/azure/templates/microsoft.documentdb/allversions)
* [Modèles Démarrage rapide Azure Cosmos DB](https://azure.microsoft.com/resources/templates/?resourceType=Microsoft.Documentdb&pageNumber=1&sort=Popular)
* [Résolution des erreurs courantes dans des déploiements Azure avec Azure Resource Manager](../azure-resource-manager/templates/common-deployment-errors.md)