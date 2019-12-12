---
title: Alkalmazási entitások referenciája
titleSuffix: Microsoft Intune
description: Referencia-témakör az Intune-adattárház API entitásgyűjteményeiben található Alkalmazás kategóriához.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a8fa34673340e4adca7b64707d8c79d4808460
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74290948"
---
# <a name="reference-for-application-entities"></a>Alkalmazás-entitások referencia

Az **alkalmazás** kategóriája az olyan eszközökhöz tartozó entitásokat tartalmazza, amelyek a következő információkat követik nyomon:

- Az alkalmazás verziói
- Az alkalmazás telepítési forrása
- Az alkalmazást létrehozó fejlesztők típusai
- Az alkalmazáshoz tartozó felügyelt szoftverek típusa, például **sidecar** („oldalkocsis”) vagy **asztali**
- Az alkalmazás mennyiségi vásárlási programbeli (VPP) állapota

## <a name="apprevisions"></a>appRevisions

Az **AppRevision** entitás listázza az alkalmazások összes verzióját.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| appKey |Az alkalmazás egyedi azonosítója. |123 |
| applicationId |Az alkalmazás egyedi azonosítója – Az AppKey-hez hasonlít, de természetes kulcs. |b66bc706-ffff-7437-0340-032819502773 |
| változat |A bináris feltöltése során a rendszergazda által említett verzió. |2 |
| title |Az alkalmazás címe. |Excel |
| közzétevő |Az alkalmazás kiadója. |Microsoft |
| uploadState |Az alkalmazás feltöltésének állapota. |1 |
| appTypeKey |A következő szakaszban leírt AppType érték hivatkozása. | |
| vppProgramTypeKey |A következő szakaszban leírt VppProgramType érték hivatkozása. | |
| creationTime |A jelen változat létrehozásának ideje. |2016.11.23 12:00:00 |
| modifiedTime |A legutóbbi, jelen változattal kapcsolatos bármilyen módosítás ideje. |2016.11.23 12:00:00 |
| méret |A bináris mérete. | |
| startDateInclusiveUTC |A jelen változat adattárházban történő létrehozásának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |
| endDateExclusiveUTC |A jelen változat elavulásának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |
| isCurrent |Jelzi, hogy az alkalmazásverzió aktuális-e az adattárházban. |Igaz/hamis |
| rowLastModifiedDateTimeUTC |Az alkalmazásverzió legutóbbi módosításának dátuma és időpontja (UTC) az adattárházban. |2016.11.23 12:00:00 |

## <a name="apptypes"></a>appTypes

Az **appType** entitás az alkalmazás telepítési forrásait listázza.

| Tulajdonság  | Description |
|---------|------------|
| appTypeID |A típus azonosítója |
| appTypeKey |A kulcs helyettes kulcsa |
| appTypeName |Alkalmazás típusa |

### <a name="example"></a>Példa

| AppTypeID  | Név | Description |
|---------|------------|--------|
| 0 |Android store app | Android Áruházbeli alkalmazás. |
| 1 |Android LOB app | Üzletági Android-alkalmazás. |
| 2 |Managed Android store app (MAM) | Android Áruházbeli alkalmazás, amelyen engedélyezve van a felügyelet. |
| 3 |iOS store app | iOS Store-alkalmazás. |
| 4 |iOS LOB app | Üzletági iOS-alkalmazás. |
| 5 |Managed iOS store app (MAM?) | iOS-alkalmazás, amelyen engedélyezve van a felügyelet. |
| 6 |O365 Pro Plus Suite | A Windows 10-hez készült Office 365 Pro Plus Csomag. |
| 7 |Web app | Webes alkalmazás. |
| 8 |Windows Phone 8.1 store app | Windows Phone 8.1-es Áruházbeli alkalmazás. |
| 9 |Windows store app | Windows Áruházbeli alkalmazás. |
| 10 |Windows LOB apps | AppX-alapú üzletági Windows-alkalmazás. |
| 11 |Windows Mobile MSI | MSI-alapú üzletági alkalmazás. |
| 12 |Windows Phone LOB app | Üzletági Windows Phone-alkalmazás. |


## <a name="vppprogramtypes"></a>vppProgramTypes

A **vppProgramType** entitás az alkalmazás lehetséges VPP-programtípusait listázza.

| Tulajdonság  | Description |
|---------|------------|
| vppProgramTypeID | A típus azonosítója. |
| vppProgramTypeKey | A kulcs helyettes kulcsa. |
| vppProgramTypeName | A VPP program típusa. |

### <a name="example"></a>Példa

| VppProgramID  | Név | Description |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | A Microsoft VPP-programja. |
| 00000000-0000-0000-0000-000000000000 | Not Yet Available (Még nem érhető el) | Alapértelmezett érték, nincs VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Az Apple VPP-programja. |



## <a name="applicationinventories"></a>applicationInventories

A **applicationInventory** entitás felsorolja az eszközön talált alkalmazásokat a leltár gyűjtése során.

| Tulajdonság  | Description |
|---------|------------|
| deviceKey | Az Intune-eszközazonosítót tartalmazó eszköztáblára mutató hivatkozás. |
| dateKey | A leltári napot megadó dátumtáblázat-hivatkozás. |
| applicationName | Az alkalmazás neve. |
| applicationVersion | Az alkalmazás verziója. |
| bundleSize | Az alkalmazás mérete bájtban. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

A **mobileAppInstallState** entitás a mobileszköz telepítési állapotát jelöli, miután hozzá lett rendelve egy olyan csoporthoz, amely eszközöket, felhasználókat vagy mindkettőt tartalmaz.

| Tulajdonság | Description |
|---|---|
| appInstallStateKey | A fiókhoz tartozó alkalmazástelepítési állapot egyedi azonosítója. |
| appInstallState | Az alkalmazástelepítési állapot felsorolásértéke. |
| appInstallStateName | Az alkalmazástelepítési állapot neve. |



