---
title: Guide pratique pour diagnostiquer et résoudre les problèmes dans Azure Spring Cloud par soi-même
description: Découvrez comment diagnostiquer et résoudre les problèmes dans Azure Spring Cloud par vous-même.
author: MikeDodaro
ms.author: brendm
ms.service: spring-cloud
ms.topic: how-to
ms.date: 05/29/2020
ms.custom: devx-track-java
ms.openlocfilehash: 03b29e6ddd16731073b33fef14d5aafb54df2abe
ms.sourcegitcommit: b28e9f4d34abcb6f5ccbf112206926d5434bd0da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107227855"
---
# <a name="self-diagnose-and-solve-problems-in-azure-spring-cloud"></a>Diagnostiquer et résoudre les problèmes dans Azure Spring Cloud par vous-même

**Cet article s'applique à :** ✔️ Java ✔️ C#

L service de diagnostics Azure Spring Cloud est une expérience interactive vous permettant de résoudre les problèmes de votre application sans besoin de configuration. La fonctionnalité de diagnostic Azure Spring Cloud identifie les incidents et vous guide vers les informations qui vous aident au dépannage et à la résolution des problèmes.

## <a name="prerequisites"></a>Prérequis
Pour effectuer cet exercice, vous avez besoin des éléments suivants :

* Un abonnement Azure. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) avant de commencer.
* Une instance du service Azure Spring Cloud déployée. Pour bien démarrer, suivez notre [guide de démarrage rapide sur le déploiement d’une application via Azure CLI](spring-cloud-quickstart.md).
* Au moins une application déjà créée dans votre instance de ce service.

## <a name="navigate-to-the-diagnostics-page"></a>Accédez à la page Diagnostics.
1. Connectez-vous au portail Azure.
2. Accédez à la page **Vue d’ensemble** de votre instance Azure Spring Cloud.
3. Dans le volet de navigation de gauche, sélectionnez **Diagnostiquer et résoudre les problèmes**.

 ![Boîte de dialogue diagnostiquer et résoudre](media/spring-cloud-diagnose/diagnose-solve-dialog.png)

 ## <a name="search-logged-issues"></a>Rechercher des problèmes journalisés
Pour rechercher un problème, vous pouvez effectuer une recherche en saisissant un mot clé ou en cliquant sur un groupe de solutions pour explorer tous les résultats de cette catégorie.

 ![Rechercher des problèmes](media/spring-cloud-diagnose/search-detectors.png)

La sélection de **Vérification de l’intégrité de Config Server**, **État d’intégrité de Config Server** ou **Historique des mises à jour de Config Server** affiche différents résultats.

![Options de problèmes](media/spring-cloud-diagnose/detectors-options.png)

Recherchez votre détecteur cible, puis cliquez dessus pour l’exécuter. Un résumé des diagnostics s’affichera une fois que vous aurez exécuté le détecteur. Vous pouvez sélectionner **Afficher le rapport complet** pour vérifier les détails du diagnostic ou cliquer sur le bouton **Afficher les vignettes du menu** pour revenir à la liste des détecteurs.

 ![Résumé des diagnostics](media/spring-cloud-diagnose/summary-diagnostics.png)

Dans la page Détails du diagnostic, vous pouvez modifier l’intervalle de temps des diagnostics à l’aide du contrôleur dans l’angle supérieur droit. Pour afficher plus de métriques ou de journaux, activez/désactivez chaque diagnostic. Il peut y avoir un délai de 15 minutes pour les métriques et les journaux.

 ![Détails des diagnostics](media/spring-cloud-diagnose/diagnostics-details.png)

Certains résultats contiennent de la documentation connexe.

 ![Détails connexes](media/spring-cloud-diagnose/related-details.png)

## <a name="next-steps"></a>Étapes suivantes
* [Superviser les ressources Spring Cloud avec des alertes et des groupes d’actions](spring-cloud-tutorial-alerts-action-groups.md)
* [Contrôles de sécurité pour le service Azure Spring Cloud](spring-cloud-concept-security-controls.md)