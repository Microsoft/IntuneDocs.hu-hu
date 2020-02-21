---
title: Az adatátviteli szabályzat kivételei alkalmazások esetén
titleSuffix: Microsoft Intune
description: Kivételeket hozhat létre a Intune App Protection házirend (alkalmazás) adatátviteli házirendjében.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77a4f0ea0ee076907d2a6cd14000c5cf319231e6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513775"
---
# <a name="how-to-create-exceptions-to-the-intune-app-protection-policy-app-data-transfer-policy"></a>Kivételek létrehozása a Intune App Protection szabályzat (alkalmazás) adatátviteli házirendjében

Rendszergazdaként kivételeket hozhat létre a Intune App Protection házirend (alkalmazás) adatátviteli házirendjében. A kivételekkel meghatározható, hogy mely nem felügyelt alkalmazások végezhetnek felügyelt alkalmazásokból kiinduló és oda irányuló adatátvitelt. Az informatikai szervezetnek meg kell bíznia a kivételek listáján szereplő nem felügyelt alkalmazásokban. 

>[!WARNING] 
> Az adatátviteli szabályzat kivételeinek módosítása az Ön felelőssége. A szabályzathoz való hozzáadással engedélyezi, hogy a nem felügyelt alkalmazások (azaz az Intune által nem kezelt alkalmazások) hozzáférjenek a felügyelt alkalmazások által védett adatokhoz. A védett adatokhoz való hozzáférés azonban biztonsági kockázatokkal járhat. Ezért csak olyan alkalmazások esetén hozzon létre adatátviteli kivételeket, amelyeket megbízhatónak tekint a cég, de amelyek nem támogatják az Intune alkalmazásvédelmi szabályzatokat (más néven APP-t). Emellett csakis olyan alkalmazásokhoz ajánlott kivételeket megadni, amelyek nem jelentenek adatszivárgási kockázatot.

Az Intune alkalmazás-védelmi szabályzatában az alkalmazás **az adatok más alkalmazásokba való átvitelének engedélyezése** a **házirend által felügyelt alkalmazások** számára beállítás azt jelenti, hogy az alkalmazás csak az Intune által kezelt alkalmazások számára tud adatátvitelt továbbítani. Ha engedélyezni szeretné az adatátvitelt olyan alkalmazások számára, amelyek nem támogatják az Intune-alkalmazást, akkor kivételeket hozhat létre ehhez a Szabályzathoz a **válassza ki az alkalmazások elemet a kivételhez**. A kivételek lehetővé teszik az Intune által kezelt alkalmazások számára a nem felügyelt alkalmazások meghívását az URL-protokoll (iOS/iPadOS) vagy a csomag neve (Android) alapján. Alapértelmezés szerint az Intune hozzáadja a fontos natív alkalmazásokat a kivételek alapértelmezett listájához. 

> [!NOTE]
> Az adatátviteli szabályzat kivételeinek módosítása vagy bővítése, például a korlátozások kivágása, másolása és beillesztése, nincs hatással más alkalmazásvédelmi szabályzatokra. 

## <a name="ios-data-transfer-exceptions"></a>Az iOS-es adatátviteli szabályzat kivételei
Az iOS/iPadOS-alapú házirendek esetében az adatátviteli kivételeket URL-protokoll szerint konfigurálhatja. Ha kivételt szeretne hozzáadni, olvassa el az alkalmazás fejlesztője által készített dokumentációt, és ellenőrizze, milyen URL-protokollok vannak támogatva. További információ az iOS/iPadOS adatátviteli kivételekről: [iOS/iPadOS app Protection házirend-beállítások – adatátviteli kivételek](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> A Microsoft nem rendelkezik olyan módszerrel, amellyel manuálisan megkereshető lenne az URL protokoll alkalmazáskivételek külső alkalmazásokhoz való létrehozáshoz. 

## <a name="android-data-transfer-exceptions"></a>Az androidos adatátviteli szabályzat kivételei
Az androidos szabályzatok esetén alkalmazáscsomagok alapján konfigurálhatók az adatátviteli kivételek. A kivétel létrehozásához a kivételként hozzáadni kívánt alkalmazás csomagnevét a **Google Play** áruházban az alkalmazás oldalán találja meg. További információ az androidos adatátviteli kivételekről: az [Android-alkalmazás védelmi házirendjének beállításai – adatátviteli kivételek](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Az alkalmazás csomagazonosítóját úgy tudja megtalálni, hogy a Google Play áruházban megkeresi az alkalmazás oldalát. A csomagazonosítót az alkalmazáscsomag URL-címe tartalmazza. Például a Microsoft Word alkalmazás azonosítója **com.microsoft.office.word**.

### <a name="example"></a>Példa
Ha a **Webex** csomagot kivételként hozzáadja a MAM adatátviteli szabályzatához, akkor a felügyelt Outlook-e-mailekben a Webex-hivatkozásokat közvetlenül a Webex-alkalmazásban lehet megnyitni. Az adatátvitel azonban továbbra is korlátozva marad az egyéb nem kezelt alkalmazásokban.

- iOS/iPadOS **WebEx** -példa: Ha engedélyezni szeretné, hogy az Intune által felügyelt alkalmazások meg tudják hívni az **WebEx** alkalmazást, a következő sztringhez adatátviteli kivételt kell hozzáadnia: <code>wbx</code>
    
- iOS/iPadOS **Maps** – példa: Ha engedélyezni szeretné, hogy az Intune által felügyelt alkalmazások meg tudják hívni a natív **Maps** alkalmazást, a következő sztringhez adatátviteli kivételt kell hozzáadnia: <code>maps</code>

- Androidos **WebEx** -példa: Ha engedélyezni szeretné, hogy az Intune által felügyelt alkalmazások meghívja a **WebEx** alkalmazást, a következő sztringhez adatátviteli kivételt kell hozzáadnia: <code>com.cisco.webex.meetings</code>
    
- Androidos **SMS** -példa: Ha engedélyezni szeretné, hogy az Intune által felügyelt alkalmazások különböző üzenetkezelési alkalmazásokban és Android-eszközökön is meghívhatják a natív **SMS** -alkalmazást, a következő karakterláncokhoz kell adatátviteli kivételeket hozzáadnia: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

- Android- **tanúsítvány telepítője** – példa: Ha a natív **tanúsítvány-telepítő** alkalmazást szeretné felvenni, hogy az Android rendszerhez készült Outlook képes legyen egy e-mail-mellékletként megjelenő S/MIME-tanúsítványt telepíteni az Android-tárolóba, hozzá kell adnia az adatátviteli kivételt a következő sztringhez: <code>com.android.certinstaller</code>. További információ: [érzékenység címkézése és védelme az Outlookban iOS/iPadOS és Android rendszerhez](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/sensitive-labeling-and-protection-outlook-for-ios-android).

## <a name="next-steps"></a>További lépések

- [Alkalmazásvédelmi szabályzatok létrehozása és telepítése](app-protection-policies.md)
- [iOS/iPadOS alkalmazás-védelmi szabályzat beállításai – adatátviteli kivételek](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Androidos alkalmazásvédelmi szabályzat beállításai – Adatátviteli kivételek](app-protection-policy-settings-android.md#data-transfer-exemptions)
