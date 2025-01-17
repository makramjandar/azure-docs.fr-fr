---
author: baanders
description: Fichier include pour les limites Azure Digital Twins
ms.service: digital-twins
ms.topic: include
ms.date: 6/9/2020
ms.author: baanders
ms.openlocfilehash: 4a69b2ff15fc4857e9fb292d2f753aa68ed875d4
ms.sourcegitcommit: f28ebb95ae9aaaff3f87d8388a09b41e0b3445b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "100370095"
---
### <a name="functional-limits"></a>Limitations fonctionnelles

Le tableau suivant liste les limites opérationnelles d’Azure Digital Twins. 

> [!TIP]
> Pour pouvoir appliquer les recommandations de modélisation dans le cadre de ces limites opérationnelles, consultez [Bonnes pratiques en matière de conception de modèles](../articles/digital-twins/concepts-models.md#best-practices-for-designing-models).

| Domaine | Fonctionnalité | Limite par défaut | Ajustable ? |
| --- | --- | --- | --- |
| Ressource Azure | Nombre d’instances Azure Digital Twins dans une région, par abonnement | 10 | Oui |
| Jumeaux numériques | Nombre de jumeaux dans une instance Azure Digital Twins | 200 000 | Oui |
| Jumeaux numériques | Nombre de relations entrantes à un seul jumeau | 5 000 | Non |
| Jumeaux numériques | Nombre de relations sortantes à partir d’un seul jumeau | 5 000 | Non |
| Jumeaux numériques | Taille maximale (du corps JSON dans une requête PUT ou PATCH) d’un seul jumeau | 32 Ko | Non |
| Jumeaux numériques | Taille maximale de la charge utile de requête | 32 Ko | Non | 
| Routage | Nombre de points de terminaison pour une même instance Azure Digital Twins | 6 | Non |
| Routage | Nombre d’itinéraires pour une même instance Azure Digital Twins | 6 | Oui |
| Modèles | Nombre de modèles dans une même instance Azure Digital Twins | 10 000 | Oui |
| Modèles | Nombre de modèles qui peuvent être chargés en un seul appel d’API | 250 | Non |
| Modèles | Taille maximale (du corps JSON dans une requête PUT ou PATCH) d’un seul modèle | 1 Mo | Non |
| Modèles | Nombre d’éléments retournés sur une même page | 100 | Non |
| Requête | Nombre d’éléments retournés sur une même page | 100 | Oui |
| Requête | Nombre d’expressions `AND` / `OR` dans une requête | 50 | Oui |
| Requête | Nombre d’éléments de tableau dans une clause `IN` / `NOT IN` | 50 | Oui |
| Requête | Nombre de caractères dans une requête | 8,000 | Oui |
| Requête | Nombre de `JOINS` dans une requête | 5 | Oui |

### <a name="rate-limits"></a>Limites du taux de transfert

Le tableau suivant reflète les limites de débit de différentes API.

| API | Fonctionnalité | Limite par défaut | Ajustable ? |
| --- | --- | --- | --- |
| API Modèles | Nombre de demandes par seconde | 100 | Oui |
| API Digital Twins | Nombre de demandes par seconde | 2 000 | Oui |
| API Digital Twins | Nombre d’opérations de création/suppression par seconde pour l’**ensemble des jumeaux et des relations** | 50 | Oui |
| API Digital Twins | Nombre d’opérations de création/mise à jour/suppression par seconde sur un **jumeau unique** ou ses relations | 10 | Non |
| API de requête | Nombre de demandes par seconde | 500 | Oui |
| API de requête | [Unités de requête](../articles/digital-twins/concepts-query-units.md) par seconde | 4 000 | Oui |
| API Routage d’événement | Nombre de demandes par seconde | 100 | Oui |

### <a name="other-limits"></a>Autres limites

Les limites des types de données et des champs dans les documents DTDL pour les modèles Azure Digital Twins sont disponibles dans la documentation des spécifications sur GitHub : [*DTDL (Digital Twins Definition Language) – version 2*](https://github.com/Azure/opendigitaltwins-dtdl/blob/master/DTDL/v2/dtdlv2.md).
 
Pour des détails sur la latence des requêtes et les limitations de requête, consultez [*Procédure : Interroger le graphique de jumeaux*](../articles/digital-twins/how-to-query-graph.md).
