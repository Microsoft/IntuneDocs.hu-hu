---
title: Mobilalkalmazás-felügyelet (MAM)
titleSuffix: Microsoft Intune
description: Az Intune-adattárház API-ban található entitásgyűjtemények mobilalkalmazásfelügyelet-kategóriájára vonatkozó referencia-témakör.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb1833a6a54fe0a7f78958e653468921df952b4d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505693"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Mobilalkalmazás-felügyelet (MAM) típusú entitások referenciája

A **Mobilalkalmazás-felügyelet** kategória a következő mobilalkalmazásokkal kapcsolatos entitásokat tartalmazza:

- Apps
- példányszám
- Bejelentkezési állapot
- Állapotadatok
- Szabályzat állapota
- Beléptetés állapota
- Platformtípusok

## <a name="mamapplications"></a>MamApplications

A **mamApplication** entitás a mobileszköz-felügyelet (MAM) használatával felügyelt ÜZLETÁGI (LOB) alkalmazásokat sorolja fel a vállalaton belüli regisztráció nélkül.

| Tulajdonság | Description | Példa |
|---------|------------|--------|
| mamApplicationKey |A MAM-alkalmazás egyedi azonosítója. | 432 |
| mamApplicationName |A MAM-alkalmazás neve. |MAM-alkalmazás példájának neve |
| mamApplicationId |A MAM-alkalmazás alkalmazás-azonosítója. | 123 |
| isDeleted |Jelzi, hogy frissítve lett-e ez a MAM-alkalmazásrekord. <br>Igaz – a MAM-alkalmazáshoz új, frissített mezőkből álló rekord tartozik a táblában. <br>Hamis – a MAM-alkalmazás legfrissebb rekordja. |Igaz/hamis |
| startDateInclusiveUTC |A MAM-alkalmazás adattárházban történő létrehozásának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |
| deletedDateUTC |Az IsDeleted paraméter True (Igaz) értékre módosulásának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |
| rowLastModifiedDateTimeUTC |A MAM-alkalmazás adattárházban történő utolsó módosításának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |


## <a name="mamapplicationinstances"></a>MamApplicationInstances

A **mamApplicationInstance** entitás a felügyelt mobileszköz-felügyeleti (MAM) alkalmazásokat sorolja fel felhasználónként eszközönként. Az entitásban felsorolt összes felhasználó és eszköz védelem alatt áll, vagyis legalább egy MAM-szabályzat hozzájuk van rendelve.


|          Tulajdonság          |                                                                                                  Description                                                                                                  |               Példa                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               A MAM-alkalmazáspéldány egyedi azonosítója az adattárházban – helyettes kulcs.                                                                |                 123                  |
|           userId           |                                                                              Azon felhasználó felhasználói azonosítója, aki ezt a MAM-alkalmazást telepítette.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              A MAM-alkalmazáspéldány egyedi azonosítója – hasonló az ApplicationInstanceKey-hez, de az azonosító természetes kulcs.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | Annak a MAM-alkalmazásnak az azonosítója, amelyhez a MAM-alkalmazás példánya létrejött.   | 2016.11.23 12:00:00   |
|     applicationVersion     |                                                                                     A MAM-alkalmazás verziószáma.                                                                                      |                  2                   |
|        createdDate         |                                                                 A MAM-alkalmazáspéldány rekordjának létrehozási dátuma. Az érték lehet null is.                                                                 |        2016.11.23 12:00:00        |
|          Platform          |                                                                          Az eszköz platformja, amelyen ez a MAM-alkalmazás telepítve van.                                                                           |                  2                   |
|      platformVersion       |                                                                      Az eszköz platformjának verziója, amelyen ez a MAM-alkalmazás telepítve van.                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            A MAM-SDK verziója, amellyel az adott MAM-alkalmazást becsomagolták.                                                                            |                 3.2                  |
| mamDeviceId | Annak az eszköznek az azonosítója, amelyhez a MAM-alkalmazás példánya társítva van.   | 2016.11.23 12:00:00   |
| mamDeviceType | Annak az eszköznek a típusa, amellyel a MAM-alkalmazás-példány társítva van.   | 2016.11.23 12:00:00   |
| mamDeviceName | Annak az eszköznek a neve, amelyhez a MAM Application instance társítva van.   | 2016.11.23 12:00:00   |
|         isDeleted          | Jelzi, hogy frissítve lett-e ez a MAM-alkalmazásrekord. <br>Igaz – a MAM-alkalmazáspéldányhoz új, frissített mezőkből álló rekord tartozik a táblában. <br>Hamis – a MAM-alkalmazás legfrissebb rekordja. |              Igaz/hamis              |
|   startDateInclusiveUtc    |                                                              A MAM-alkalmazáspéldány adattárházban történő létrehozásának dátuma és időpontja (UTC).                                                               |        2016.11.23 12:00:00        |
|       deletedDateUtc       |                                                                             Az IsDeleted paraméter True (Igaz) értékre módosulásának dátuma és időpontja (UTC).                                                                              |        2016.11.23 12:00:00        |
| rowLastModifiedDateTimeUtc |                                                           A MAM-alkalmazáspéldány adattárházban történő utolsó módosításának dátuma és időpontja (UTC).                                                            |        2016.11.23 12:00:00        |


## <a name="mamcheckins"></a>MamCheckins

A **mamCheckin** entitás a Mobile Application Management (MAM) alkalmazás példányának az Intune szolgáltatásban való beadásakor összegyűjtött adatokat jeleníti meg. 

> [!Note]  
> Ha az alkalmazáspéldány naponta többször is bejelentkezik, azokat az adattárház egyetlen bejelentkezésként tárolja.

| Tulajdonság | Description | Példa |
|---------|------------|--------|
| dateKey |A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve a MAM-alkalmazás bejelentkezése. | 20160703 |
| applicationInstanceKey |A MAM-alkalmazás bejelentkezéséhez társított alkalmazáspéldány kulcsa. | 123 |
| userKey |A MAM-alkalmazás bejelentkezéséhez társított felhasználó kulcsa. | 4323 |
| mamApplicationKey |A MAM-alkalmazás bejelentkezéséhez társított alkalmazás kulcsa. | 432 |
| deviceHealthKey |A MAM-alkalmazás bejelentkezéséhez társított DeviceHealth kulcsa. | 321 |
| platformKey |A MAM-alkalmazás bejelentkezéséhez társított eszköz platformját jelöli. |123 |
| effectiveAppliedPolicyKey |A bejelentkező MAM-alkalmazáshoz társított érvényben levő hozzárendelt szabályzatot jelöli. Az érvényben levő hozzárendelt szabályzat az adott alkalmazásra és felhasználóra vonatkozó szabályzatok összevonásának eredménye. | 322 |
| pastCheckInDate |A MAM-alkalmazás utolsó bejelentkezésének dátuma és időpontja. Az érték lehet null is. |2016.11.23 12:00:00 |


## <a name="mamdevicehealth"></a>mamDeviceHealth

A **mamDeviceHealth** entitás azokat az eszközöket jelöli, amelyeken a Mobile Application Management (MAM) szabályzatok telepítve vannak, még akkor is, ha azok a jailbroken vannak.

| Tulajdonság | Description | Példa |
|---------|------------|--------|
| deviceHealthKey |Az eszköz és a hozzá tartozó eszközállapot egyedi azonosítója az adattárházban – helyettes kulcs. |123 |
| deviceHealth |Az eszköz és a hozzá tartozó eszközállapot egyedi azonosítója – hasonló a DeviceHealthKey-hez, de az azonosító természetes kulcs. |b66bc706-FFFF-7777-0340-032819502773 |
| deviceHealthName |Az eszköz állapotát jelöli. <br>Not available – nincs információ az eszközről. <br>Healthy – az eszköz nem jailbreakelt. <br>Unhealthy – az eszköz jailbreakelt. |Not Available Healthy Unhealthy |
| rowLastModifiedDateTimeUtc |Az adott MAM-eszközállapot adattárházban történt utolsó módosításának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

A **mamEffectivePolicy** entitás felsorolja az összes, a szervezetben alkalmazott mobileszköz-kezelési (MAM) szabályzatot. Az érvényben levő hozzárendelt szabályzat az adott alkalmazásra és felhasználóra vonatkozó szabályzatok összevonásának eredménye.

| Tulajdonság | Description | Példa |
|---------|------------|--------|
| effectivePolicyKey |Az érvényben levő MAM-szabályzat egyedi azonosítója az adattárházban. |2 |
| realPolicyKey |A MAM-szabályzat informatikai szakember által létrehozott egyedi azonosítója. |1 |
| rowCreatedDateTimeUtc |Az érvényben levő MAM-szabályzat adattárházban történt létrehozásának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |

## <a name="mamplatforms"></a>MamPlatforms

A **mamPlatform** entitás felsorolja azokat a platformokat és típusokat, amelyeken telepítve van a Mobile Application Management (MAM) alkalmazás.


|          Tulajdonság          |                                    Description                                    |                         Példa                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     A platform egyedi azonosítója az adattárházban – helyettes kulcs.      |                           123                           |
|          Platform          | A platform egyedi azonosítója – a PlatformKey-hez hasonló, de természetes kulcs. |                           123                           |
|        platformName        |                                   A platform neve                                   | Nem érhető el <br>Nincsenek <br>Windows <br>iOS <br>Android. |
| rowLastModifiedDateTimeUtc | A platform adattárházban történt utolsó módosításának dátuma és időpontja (UTC).  |                 2016.11.23 12:00:00                  |

