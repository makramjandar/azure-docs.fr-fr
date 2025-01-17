---
title: Disponibilité des régions et résidence des données
titleSuffix: Azure AD B2C
description: Disponibilité des régions, résidence des données et informations sur les locataires Azure Active Directory B2C en préversion.
services: active-directory-b2c
author: msmimart
manager: celestedg
ms.service: active-directory
ms.workload: identity
ms.topic: reference
ms.date: 03/31/2021
ms.author: mimart
ms.subservice: B2C
ms.custom: references_regions
ms.openlocfilehash: 6e724b3517d9e5a63d8699e9f66c51cf41f02012
ms.sourcegitcommit: 99fc6ced979d780f773d73ec01bf651d18e89b93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106092515"
---
# <a name="azure-active-directory-b2c-region-availability--data-residency"></a>Azure Active Directory B2C : Disponibilité des régions et résidence des données

La disponibilité régionale et la résidence des données sont deux concepts très différents qui ne s’appliquent pas à Azure Active Directory B2C de la même façon qu’à Azure. Cet article explique les différences entre ces deux concepts et compare la manière dont ils s’appliquent à Azure et Azure Active Directory B2C.

Azure Active Directory B2C est **généralement disponible dans le monde entier** avec l’option de **résidence des données** dans les régions **États-Unis, Europe ou Asie-Pacifique**. Azure AD B2C est en **version préliminaire publique** en Australie.

La [disponibilité régionale](#region-availability) fait référence à l’endroit où se trouve le service pour utilisation.

La [résidence des données](#data-residency) fait référence à l’endroit où sont stockées les données des utilisateurs.

## <a name="region-availability"></a>Disponibilité des régions

Azure Active Directory B2C est disponible dans le monde entier via le cloud public Azure.

Cela diffère du modèle suivi par la plupart des autres services Azure, qui associent généralement la *disponibilité* à la *résidence des données*. C’est le cas par exemple dans la page [Produits disponibles par région](https://azure.microsoft.com/regions/services/) et la [calculatrice de tarification Active Directory B2C](https://azure.microsoft.com/pricing/details/active-directory-b2c/).

## <a name="data-residency"></a>Résidence des données

Azure AD B2C stocke les données utilisateur dans la région États-Unis, Europe ou Asie-Pacifique.

La résidence des données est déterminée par le pays ou la région que vous sélectionnez quand vous [créez un locataire Azure AD B2C](tutorial-create-tenant.md) :

![Capture d’écran d’un formulaire Créer un locataire, choisir un pays ou une région.](./media/data-residency/data-residency-b2c-tenant.png)

Les données des pays/régions suivants sont conservées aux **États-Unis** :

> États-Unis (US), Canada (CA), Costa Rica (CR), République dominicaine (DO), El Salvador (SV), Guatemala (GT), Mexique (MX), Panama (PA), Porto Rico (PR) et Trinité-et-Tobago (TT).

Les données des pays/régions suivants sont conservées en **Europe** :

> Algérie (DZ), Autriche (AT), Azerbaïdjan (AZ), Bahreïn (BH), Bélarus (BY), Belgique (BE), Bulgarie (BG), Croatie (HR), Chypre (CY), République tchèque (CZ), Danemark (DK), Égypte (EG), Estonie (EE), Finlande (FT), France (FR), Allemagne (DE), Grèce (GR), Hongrie (HU), Islande (IS), Irlande (IE), Israël (IL), Italie (IT), Jordanie (JO), Kazakhstan (KZ), Kenya (KE), Koweït (KW), Lettonie (LV), Liban (LB), Liechtenstein (LI), Lituanie (LT), Luxembourg (LU), Macédoine du Nord (ML), Malte (MT), Monténégro (ME), Maroc (MA), Pays-Bas (NL), Nigéria (NG), Norvège (NO), Oman (OM), Pakistan (PK), Pologne (PL), Portugal (PT), Qatar (QA), Roumanie (RO), Russie (RU), Arabie saoudite (SA), Serbie (RS), Slovaquie (SK), Slovénie (ST), Afrique du Sud (ZA), Espagne (ES), Suède (SE), Suisse (CH), Tunisie (TN), Turquie (TR), Ukraine (UA), Émirats arabes unis (AE) et Royaume-Uni (GB).

Les données des pays/régions suivants sont conservées en **Asie-Pacifique** :

> Afghanistan (AF), Région administrative spéciale de Hong Kong (HK), Inde (IN), Indonésie (ID), Japon (JP), Corée (KR), Malaisie (MY), Philippines (PH), Singapour (SG), Sri Lanka (LK), Taïwan (TW) et Thaïlande (TH)

Les données des pays/régions suivants sont conservées en **Australie** (préversion) :

> Australie et Nouvelle Zélande

Les pays/régions suivants sont en cours d’ajout à cette liste. Pour le moment, vous pouvez toujours utiliser Azure Active Directory B2C en choisissant l’un des pays ci-dessus.

> Argentine, Brésil, Chili, Colombie, Équateur, Iraq Paraguay, Pérou, Uruguay et Venezuela

## <a name="remote-profile-solution"></a>Solution Profil distant

Avec les [stratégies personnalisées](custom-policy-overview.md) Azure AD B2C, vous pouvez intégrer des [services API RESTful](custom-policy-rest-api-intro.md), ce qui vous permet de stocker et de lire des profils utilisateur à partir d’une base de données distante (telle qu’une base de données marketing, un système CRM ou une application métier).  
- Au cours des flux d’inscription et de modification du profil, Azure AD B2C appelle une API REST personnalisée pour rendre le profil utilisateur persistant dans la source de données distante. Les informations d’identification de l’utilisateur sont stockées dans un répertoire Azure AD B2C. 
- Après la connexion, une fois que les informations d’identification ont été validées avec un compte local ou social, Azure AD B2C appelle l’API REST, qui envoie l’identificateur unique de l’utilisateur en tant que clé primaire d’utilisateur (adresse e-mail ou objectId utilisateur). L’API REST lit les données de la base de données distante et retourne le profil utilisateur.  

Une fois l’inscription, la modification de profil ou la connexion terminée, Azure AD B2C inclut le profil utilisateur dans le jeton d’accès qui est retourné à l’application. Pour plus d’informations, consultez l’[exemple de solution Profil distant Azure AD B2C](https://github.com/azure-ad-b2c/samples/tree/master/policies/remote-profile) dans GitHub.

## <a name="next-steps"></a>Étapes suivantes

- [Créez un locataire Azure AD B2C](tutorial-create-tenant.md).
