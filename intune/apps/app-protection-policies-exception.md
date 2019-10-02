---
title: Az adatátviteli szabályzat kivételei alkalmazások esetén
titleSuffix: Microsoft Intune
description: Kivételeket hozhat létre az Intune Mobilalkalmazás-kezelés (MAM) adatátviteli szabályzataihoz.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ada0f7fc7ed21750adf20a63d229f9a188cf34f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731371"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Kivételek létrehozása az Intune Mobilalkalmazás-kezelés (MAM) adatátviteli szabályzataihoz

A rendszergazdák kivételeket hozhatnak létre az Intune Mobilalkalmazás-kezelés (MAM) adatátviteli szabályzataihoz. A kivételekkel meghatározható, hogy mely nem felügyelt alkalmazások végezhetnek felügyelt alkalmazásokból kiinduló és oda irányuló adatátvitelt. Az informatikai szervezetnek meg kell bíznia a kivételek listáján szereplő nem felügyelt alkalmazásokban. 

>[!WARNING] 
> Az adatátviteli szabályzat kivételeinek módosítása az Ön felelőssége. A szabályzathoz való hozzáadással engedélyezi, hogy a nem felügyelt alkalmazások (azaz az Intune által nem kezelt alkalmazások) hozzáférjenek a felügyelt alkalmazások által védett adatokhoz. A védett adatokhoz való hozzáférés azonban biztonsági kockázatokkal járhat. Ezért csak olyan alkalmazások esetén hozzon létre adatátviteli kivételeket, amelyeket megbízhatónak tekint a cég, de amelyek nem támogatják az Intune alkalmazásvédelmi szabályzatokat (más néven APP-t). Emellett csakis olyan alkalmazásokhoz ajánlott kivételeket megadni, amelyek nem jelentenek adatszivárgási kockázatot.

Az Intune alkalmazás-védelmi szabályzatában az alkalmazás **az adatok más alkalmazásokba való átvitelének engedélyezése** a **házirend által felügyelt alkalmazások** számára beállítás azt jelenti, hogy az alkalmazás csak az Intune által kezelt alkalmazások számára tud adatátvitelt továbbítani. Ha engedélyezni szeretné az adatátvitelt olyan alkalmazások számára, amelyek nem támogatják az Intune-alkalmazást, akkor kivételeket hozhat létre ehhez a Szabályzathoz a **válassza ki az alkalmazások elemet a kivételhez**. A kivételekkel az Intune által kezelt alkalmazások URL-protokoll (iOS) vagy csomagnév (Android) alapján hívhatnak meg nem kezelt alkalmazásokat. Alapértelmezés szerint az Intune hozzáadja a fontos natív alkalmazásokat a kivételek alapértelmezett listájához. 

> [!NOTE]
> Az adatátviteli szabályzat kivételeinek módosítása vagy bővítése, például a korlátozások kivágása, másolása és beillesztése, nincs hatással más alkalmazásvédelmi szabályzatokra. 

## <a name="ios-data-transfer-exceptions"></a>Az iOS-es adatátviteli szabályzat kivételei
Az iOS-es szabályzatok esetén URL-protokoll alapján konfigurálhatók az adatátviteli kivételek. Ha kivételt szeretne hozzáadni, olvassa el az alkalmazás fejlesztője által készített dokumentációt, és ellenőrizze, milyen URL-protokollok vannak támogatva. További információ az iOS-adatátviteli kivételekről: [iOS-alkalmazás védelmi szabályzatának beállításai – adatátviteli kivételek](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> A Microsoft nem rendelkezik olyan módszerrel, amellyel manuálisan megkereshető lenne az URL protokoll alkalmazáskivételek külső alkalmazásokhoz való létrehozáshoz. 

## <a name="android-data-transfer-exceptions"></a>Az androidos adatátviteli szabályzat kivételei
Az androidos szabályzatok esetén alkalmazáscsomagok alapján konfigurálhatók az adatátviteli kivételek. A kivétel létrehozásához a kivételként hozzáadni kívánt alkalmazás csomagnevét a **Google Play** áruházban az alkalmazás oldalán találja meg. További információ az androidos adatátviteli kivételekről: az [Android-alkalmazás védelmi házirendjének beállításai – adatátviteli kivételek](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Az alkalmazás csomagazonosítóját úgy tudja megtalálni, hogy a Google Play áruházban megkeresi az alkalmazás oldalát. A csomagazonosítót az alkalmazáscsomag URL-címe tartalmazza. Például a Microsoft Word alkalmazás azonosítója **com.microsoft.office.word**.

### <a name="example"></a>Példa
Ha a **Webex** csomagot kivételként hozzáadja a MAM adatátviteli szabályzatához, akkor a felügyelt Outlook-e-mailekben a Webex-hivatkozásokat közvetlenül a Webex-alkalmazásban lehet megnyitni. Az adatátvitel azonban továbbra is korlátozva marad az egyéb nem kezelt alkalmazásokban.

- iOS-es **WebEx** -példa:   Ha a **WebEx** alkalmazást szeretné felvenni, hogy az Intune által felügyelt alkalmazások meg tudják hívni, adatátviteli kivételt kell hozzáadnia a következő sztringhez: <code>wbx</code>
    
- iOS **Maps** – példa:   Ha fel szeretné venni a natív **Maps** alkalmazást, hogy az Intune által felügyelt alkalmazások is meghívhatók legyenek, adatátviteli kivételt kell hozzáadnia a következő sztringhez: <code>maps</code>

- Androidos **WebEx** -példa:   Ha a **WebEx** alkalmazást szeretné felvenni, hogy az Intune által felügyelt alkalmazások meg tudják hívni, adatátviteli kivételt kell hozzáadnia a következő sztringhez: <code>com.cisco.webex.meetings</code>
    
- Androidos **SMS** -példa:   Ha a natív **SMS** -alkalmazást szeretné felvenni, hogy az Intune által felügyelt alkalmazások különböző üzenetkezelési alkalmazásokban és Android-eszközökön is meghívhatják azokat, a következő sztringek esetében adatátviteli kivételeket kell hozzáadnia: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>További lépések

- [Alkalmazásvédelmi szabályzatok létrehozása és telepítése](app-protection-policies.md)
- [iOS-es alkalmazásvédelmi szabályzat beállításai – Adatátviteli kivételek](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Androidos alkalmazásvédelmi szabályzat beállításai – Adatátviteli kivételek](app-protection-policy-settings-android.md#data-transfer-exemptions)
