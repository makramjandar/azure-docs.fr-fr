---
title: Surveiller l’intégrité d’une application Azure IoT Central | Microsoft Docs
description: En tant qu’opérateur ou administrateur, surveillez l’intégrité globale des appareils connectés à votre application IoT Central.
author: dominicbetts
ms.author: dobett
ms.date: 01/27/2021
ms.topic: how-to
ms.service: iot-central
services: iot-central
ms.openlocfilehash: df89d53e6b5043c1ef3caa1c92f2abaae542d6ec
ms.sourcegitcommit: 950e98d5b3e9984b884673e59e0d2c9aaeabb5bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2021
ms.locfileid: "107599007"
---
# <a name="monitor-the-overall-health-of-an-iot-central-application"></a>Superviser l’intégrité globale d’une application IoT Central

> [!NOTE]
> Les métriques sont uniquement disponibles pour les applications de la version 3 d’IoT Central. Pour savoir comment vérifier la version de votre application, consultez [À propose de votre application](./howto-get-app-info.md).

*Cet article s’applique aux opérateurs et aux administrateurs.*

Dans cet article, vous allez apprendre à utiliser l’ensemble des métriques fournies par IoT Central pour évaluer l’intégrité des appareils connectés à votre application IoT Central et l’intégrité des exportations de données en cours d’exécution.

Les métriques sont activées par défaut pour votre application IoT Central et vous y accédez à partir du [portail Azure](https://portal.azure.com/). La [plateforme de données Azure Monitor expose ces métriques](../../azure-monitor/essentials/data-platform-metrics.md) et offre plusieurs moyens d’interagir avec elles. Par exemple, vous pouvez utiliser des graphiques dans le portail Azure, une API REST ou des requêtes dans PowerShell ou Azure CLI.

### <a name="trial-applications"></a>Applications d’évaluation

Les applications qui utilisent le plan d’essai gratuit n’ont pas d’abonnement Azure associé et ne prennent donc pas en charge les métriques d’Azure Monitor. Vous pouvez [convertir une application en plan de tarification standard](./howto-view-bill.md#move-from-free-to-standard-pricing-plan) et accéder à ces métriques.

## <a name="view-metrics-in-the-azure-portal"></a>Afficher les métriques dans le portail Azure

Les étapes suivantes partent du principe que vous disposez d’une [application IoT Central](./quick-deploy-iot-central.md) avec quelques [appareils connectés](./tutorial-connect-device.md) ou une [exportation de données](howto-export-data.md) en cours d’exécution.

Pour afficher les métriques IoT Central dans le portail :

1. Accédez à votre ressource d’application IoT Central dans le portail. Par défaut, les ressources IoT Central se trouvent dans un groupe de ressources appelé **IOTC**.
1. Pour créer un graphique à partir des métriques de votre application, sélectionnez **Métriques** dans la section **Surveillance**.

![Métriques Azure](media/howto-monitor-application-health/metrics.png)

### <a name="azure-portal-permissions"></a>Autorisations de Portail Azure

L’accès aux métriques dans le portail Azure est géré par le [contrôle d’accès en fonction du rôle Azure](../../role-based-access-control/overview.md). Utilisez le portail Azure pour ajouter des utilisateurs à l’application, au groupe de ressources ou à l’abonnement IoT Central pour leur accorder l’accès. Vous devez ajouter un utilisateur dans le portail, même s’il a déjà été ajouté à l’application IoT Central. Utilisez des [rôles intégrés Azure](../../role-based-access-control/built-in-roles.md) pour un contrôle d’accès plus précis.

## <a name="iot-central-metrics"></a>Métriques IoT Central

Pour obtenir la liste des métriques actuellement disponibles pour IoT Central, consultez [Métriques prises en charge avec Azure Monitor](../../azure-monitor/essentials/metrics-supported.md#microsoftiotcentraliotapps).

### <a name="metrics-and-invoices"></a>Métriques et factures

Les métriques peuvent être différer des valeurs figurant sur votre facture Azure IoT Central. Cette situation se produit pour plusieurs raisons :

- Les [plans de tarification standard](https://azure.microsoft.com/pricing/details/iot-central/) d’IoT Central incluent deux appareils et des quotas de message variables gratuitement. Si les éléments gratuits sont exclus de la facturation, ils sont toujours comptabilisés dans les métriques.

- IoT Central génère automatiquement une identité d’appareil de test pour chaque modèle d’appareil dans l’application. Cette identité d’appareil est visible sur la page **Gérer l’appareil de test** pour un modèle d’appareil. Les créateurs de solutions peuvent choisir de valider leurs modèles d’appareils avant de les publier en générant du code qui utilise ces identités d’appareil de test. Si ces appareils sont exclus de la facturation, ils sont toujours comptabilisés dans les métriques.

- Bien que les métriques puissent afficher un sous-ensemble de communications appareil-à-cloud, toutes les communications entre l’appareil et le cloud [comptent comme un message pour la facturation](https://azure.microsoft.com/pricing/details/iot-central/).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez appris à utiliser des modèles d’application, l’étape suivante conseillée est d’apprendre à [gérer IoT Central à partir du portail Azure](howto-manage-iot-central-from-portal.md).