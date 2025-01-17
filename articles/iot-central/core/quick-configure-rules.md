---
title: Démarrage rapide – Configurer des règles et des actions dans Azure IoT Central
description: Dans le cadre de ce démarrage rapide, vous découvrez, en tant que générateur, comment configurer des règles et des actions basées sur la télémétrie dans votre application Azure IoT Central.
author: dominicbetts
ms.author: dobett
ms.date: 11/16/2020
ms.topic: quickstart
ms.service: iot-central
services: iot-central
ms.custom: mvc
ms.openlocfilehash: f65614de97e8ff6eed732e624ae30c3f2b70bd60
ms.sourcegitcommit: 272351402a140422205ff50b59f80d3c6758f6f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2021
ms.locfileid: "107589004"
---
# <a name="quickstart-configure-rules-and-actions-for-your-device-in-azure-iot-central"></a>Démarrage rapide : Configurer des règles et des actions pour votre appareil dans Azure IoT Central

Dans ce guide de démarrage rapide, vous allez créer une règle qui envoie un e-mail quand l’humidité signalée par le capteur d’un appareil dépasse 55 %.

## <a name="prerequisites"></a>Prérequis

Avant de commencer, vous devez suivre les deux guides de démarrage rapide précédents : [Créer une application Azure IoT Central](./quick-deploy-iot-central.md) et [Ajouter un appareil simulé à votre application IoT Central](./quick-create-simulated-device.md) pour créer le modèle d’appareil **Sensor Controller** avec lequel travailler.

## <a name="create-a-telemetry-based-rule"></a>Créer une règle basée sur la télémétrie

1. Pour ajouter une nouvelle règle basée sur la télémétrie à votre application, dans le volet de gauche, sélectionnez **Règles**.

1. Pour créer une nouvelle règle, sélectionnez **+ Nouveau**.

1. Entrez **Humidité ambiante** comme nom de la règle.

1. Dans la section **Appareils cibles**, sélectionnez **Sensor Controller** comme modèle d’appareil. Cette option filtre les appareils auxquels s’applique la règle par type de modèle d’appareil. Vous pouvez ajouter d’autres critères de filtre en sélectionnant **+ Filtre**.

1. Dans la section **Conditions**, vous définissez ce qui déclenche votre règle. Utilisez les informations suivantes pour définir une condition basée sur la télémétrie de température :

    | Champ        | Valeur            |
    | ------------ | ---------------- |
    | Mesure  | SensorHumid      |
    | Opérateur     | est supérieur à  |
    | Valeur        | 55               |

    Pour ajouter d’autres conditions, sélectionnez **+ Condition**.

    :::image type="content" source="media/quick-configure-rules/condition.png" alt-text="Capture d’écran montrant la condition de règle":::

1. Pour ajouter une action d'e-mail à exécuter quand la règle se déclenche, sélectionnez **+ E-mail**.

1. Utilisez les informations du tableau suivant pour définir votre action, puis sélectionnez **Terminé** :

    | Paramètre   | Valeur                                             |
    | --------- | ------------------------------------------------- |
    | Nom complet | Action d'e-mail de l'opérateur                          |
    | À        | Votre adresse e-mail                                |
    | Notes     | L’humidité ambiante a dépassé le seuil. |

    > [!NOTE]
    > Pour recevoir une notification par courrier électronique, l’adresse e-mail doit être un [ID d’utilisateur dans l’application](howto-administer.md), et l’utilisateur doit s’être connecté au moins une fois à l’application.

    :::image type="content" source="media/quick-configure-rules/action.png" alt-text="Capture d’écran montrant une action d’e-mail ajoutée à la règle":::

1. Sélectionnez **Enregistrer**. Votre règle est listée dans la page **Règles**.

## <a name="test-the-rule"></a>Tester la règle

Peu après l’enregistrement de la règle, elle devient active. Lorsque les conditions définies dans la règle sont remplies, votre application envoie un e-mail à l’adresse que vous avez spécifiée dans l’action.

> [!NOTE]
> Une fois le test terminé, désactivez la règle pour ne plus recevoir d’alertes dans votre boîte de réception.

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez appris comment :

* Créer une règle basée sur la télémétrie
* Ajouter une action

Pour en savoir plus sur la surveillance des appareils connectés à votre application, passez au démarrage rapide :

> [!div class="nextstepaction"]
> [Utiliser Azure IoT Central pour surveiller vos appareils](quick-monitor-devices.md).
