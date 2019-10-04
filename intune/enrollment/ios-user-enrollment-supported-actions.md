---
title: Az Apple User beléptetésével támogatott Intune-műveletek és-beállítások
titleSuffix: Microsoft Intune
description: Megtudhatja, hogy mely Intune-műveletek és-beállítások támogatottak az Apple User beléptetéssel
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: acf1112f96b28b156b3c4857485de30d7ad553ef
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955434"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Az Apple User beléptetésével támogatott Intune-műveletek és-beállítások

A felhasználó beléptetése az eszközkezelés lehetőségeinek egy részhalmazát támogatja. Ha egy korábban már meglévő konfigurációs profilt alkalmaz egy felhasználó beléptetési eszközére, a rendszer csak a felhasználói beléptetés által támogatott beállításokat alkalmazza az adott eszközre.

## <a name="password-settings"></a>Jelszóbeállítások

Ha a felhasználói beléptetési eszközökön bármilyen jelszót konfigurál, az **egyszerű jelszavak** beállítás automatikusan **letiltja a blokkolás**értéket, és egy 6 számjegyű PIN-kódot kényszerít ki.

Például beállíthatja a **jelszó lejárati** beállítását, és leküldheti a szabályzatot a felhasználó által regisztrált eszközökre. Az eszközökön a következők történnek:
- A **jelszó lejárati** beállítását a rendszer figyelmen kívül hagyja.
- Az egyszerű jelszavak, például `1111` a `1234`vagy a, nem engedélyezettek.
- Egy 6 számjegyű PIN-kód kényszerítve.

## <a name="administrator-remote-device-actions-and-options"></a>Rendszergazdai távoli eszközök műveletei és beállításai
A rendszergazdák a következő műveleteket és beállításokat hajthatják végre a felhasználói beléptetési eszközökön:
- Kivonás
- Törlés
- Távoli zárolás
- Szinkronizálás

Az összes többi művelet nem támogatott.

## <a name="end-user-actions"></a>Végfelhasználói műveletek
A felhasználók beléptetési eszközein a végfelhasználók a Céges portál alkalmazásból és webhelyről is elvégezhetik ezeket a műveleteket az eszközön:
- Átnevezése. Ez a művelet csak a felhasználó felé néző névre vonatkozik a Céges portálon belül. Az eszköz nem lesz teljesen átnevezve az adott környezeten kívülről.
- Eltávolítás
- Távoli zárolás
- Állapot ellenõrzése

## <a name="other-supported-options"></a>Egyéb támogatott beállítások

Az alábbi beállítások támogatottak az Intune-ban az Apple User beléptetés használatával beléptetett eszközökhöz:
- Alkalmazáson belüli VPN. Ez a támogatás kizárja a Safari-tartományokat, mivel a felhasználói regisztráció nem támogatja a Safari-beállítások konfigurálását.
- Wi-Fi 
- Vállalati alkalmazás eltávolítása a regisztráció törlése után
- Alkalmazás központi telepítése felhasználó által licencelt mennyiségi vásárlási terv (VPP) használatával
- Jailbreak-észlelés

A következő korlátozások támogatottak:
- Vállalati dokumentumok megtekintése a nem felügyelt alkalmazásokban
- Nem vállalati dokumentumok megtekintése a vállalati alkalmazásokban
- Nem felügyelt alkalmazások olvasásának engedélyezése a felügyelt névjegyek fiókjaiból
- AirDrop nem felügyelt célhelyként
- Szükséges titkosított biztonsági mentés
- Felügyelt alkalmazások szinkronizálása a felhővel
- Vezérlési központ hozzáférése az eszköz zárolt állapotában
- Értesítési központ hozzáférése az eszköz zárolt állapotában
- Ma nézet, ha az eszköz zárolva van
- Képernyőképek letiltása
- Vállalati könyv biztonsági mentésének letiltása
- A vállalati könyv metaadatainak szinkronizálásának letiltása
- Biztonsági másolat titkosításának engedélyezése
- Figyelje meg a csukló észlelését
- Siri letiltása
- Siri letiltása az eszköz zárolt állapotában
- A Safari csalások elleni figyelmeztetésének megkövetelése
- Diagnosztika küldésének tiltása az Apple-nek


## <a name="options-not-supported"></a>A beállítások nem támogatottak
A felhasználó beléptetésével regisztrált eszközökön a következő beállítások nem támogatottak. Ha ezekre a beállításokra van szüksége, tekintse meg az eszközök regisztrálását a személyes tulajdonú eszközökhöz vagy a vállalati eszközök automatikus regisztrálásához.
- Alkalmazás-leltár gyűjtése a felügyelt APFS-köteten kívüli alkalmazásokhoz.
- A tanúsítványok és létesítési profilok leltárának gyűjtése a felügyelt APFS-köteten kívül.
- UDID és egyéb állandó eszköz-azonosítók gyűjtése.
- A felhasználói regisztráció minden regisztrált eszköz egyedi regisztrációs AZONOSÍTÓját támogatja, de ez az azonosító nem marad meg a regisztráció törlése után.
- A következő Intune-funkciók nem támogatottak a korlátozás miatt:
- A SCEP felhasználói profiljainak neve a soros numbe. r formátuma
- Eszköz szintű VPN.
- Eszköz licenccel rendelkező VPP-alkalmazás üzembe helyezése.
- A felügyelt APFS-köteten kívüli alkalmazások MDM ellenőrzése.
- Az alkalmazás-védelmi szabályzatok továbbra is érvényesek lesznek ezekre az alkalmazásokra. Azonban nem fogja tudni átvenni a felügyeletet, vagy felügyelt verziót telepíteni az alkalmazások közül, hacsak a felhasználó nem törli őket az eszközről.
- A felügyeletet igénylő műveletek, konfigurációk, beállítások és parancsok. 

## <a name="next-steps"></a>További lépések

[IOS-és iPadOS-felhasználói regisztráció beállítása](ios-user-enrollment.md)