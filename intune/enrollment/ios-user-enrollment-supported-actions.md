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
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ffabcace189efd60e9d532172ecd1f2a048eec2c
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562411"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Az Apple User beléptetésével támogatott Intune-műveletek és-beállítások

A felhasználó beléptetése az eszközkezelés lehetőségeinek egy részhalmazát támogatja. Ha egy korábban már meglévő konfigurációs profilt alkalmaz egy felhasználó beléptetési eszközére, a rendszer csak a felhasználói beléptetés által támogatott beállításokat alkalmazza az adott eszközre.

> [!NOTE]
> Az Apple felhasználói regisztrációjának támogatása az Intune-ban jelenleg előzetes verzióban érhető el.

## <a name="password-settings"></a>Jelszóbeállítások

Ha a felhasználói beléptetési eszközökön bármilyen jelszót konfigurál, az **egyszerű jelszavak** beállítás automatikusan **letiltja a blokkolás**értéket, és egy 6 számjegyű PIN-kódot kényszerít ki.

Például beállíthatja a **jelszó lejárati** beállítását, és leküldheti a szabályzatot a felhasználó által regisztrált eszközökre. Az eszközökön a következők történnek:
- A **jelszó lejárati** beállítását a rendszer figyelmen kívül hagyja.
- Az egyszerű jelszavak (például `1111` vagy `1234`) nem engedélyezettek.
- Egy 6 számjegyű PIN-kód kényszerítve.

## <a name="administrator-remote-device-actions-and-options"></a>Rendszergazdai távoli eszközök műveletei és beállításai
A rendszergazdák a következő műveleteket és beállításokat hajthatják végre a felhasználói beléptetési eszközökön:
- Kivonás
- Törlés
- Távoli zárolás
- Sync

Az összes többi művelet nem támogatott.

## <a name="end-user-actions"></a>Végfelhasználói műveletek
A felhasználók beléptetési eszközein a végfelhasználók a Céges portál alkalmazásból és webhelyről is elvégezhetik ezeket a műveleteket az eszközön:
- Átnevezése. Ez a művelet csak a felhasználó felé néző névre vonatkozik a Céges portálon belül. Az eszköz nem lesz teljesen átnevezve az adott környezeten kívülről.
- Eltávolítás
- Távoli zárolás
- Állapot ellenõrzése

## <a name="app-deployment-options"></a>Alkalmazás központi telepítési beállításai
A következő típusú alkalmazások telepíthetők a felhasználó beléptetési eszközeire:
- Felhasználói licenccel rendelkező mennyiségi vásárlási terv (VPP) alkalmazások, beleértve az egyéni alkalmazásokat
- Üzletági (LOB) alkalmazások
- Webalkalmazások

## <a name="other-supported-options"></a>Egyéb támogatott beállítások

Az alábbi beállítások támogatottak az Intune-ban az Apple User beléptetés használatával beléptetett eszközökhöz:
- Alkalmazáson belüli VPN. Ez a támogatás kizárja a Safari-tartományokat, mivel a felhasználói regisztráció nem támogatja a Safari-beállítások konfigurálását.
- Fi 
- Vállalati alkalmazás eltávolítása a regisztráció törlése után
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
- A SCEP felhasználói profiljainak sorozatszáma a tulajdonos nevének formátuma.
- Eszköz szintű VPN.
- Eszköz licenccel rendelkező VPP-alkalmazás üzembe helyezése.
- Az App Store-alkalmazások telepítése felügyelt alkalmazásként.
- A felügyelt APFS-köteten kívüli alkalmazások MDM ellenőrzése.
- Az alkalmazás-védelmi szabályzatok továbbra is érvényesek lesznek ezekre az alkalmazásokra. Azonban nem fogja tudni átvenni a felügyeletet, vagy felügyelt verziót telepíteni az alkalmazások közül, hacsak a felhasználó nem törli őket az eszközről.
- A felügyeletet igénylő műveletek, konfigurációk, beállítások és parancsok. 

## <a name="options-not-supported-in-preview"></a>Az előzetes verzióban nem támogatott beállítások
- A személyes tulajdonban lévő eszközök engedélyezésére/letiltására vonatkozó beléptetési eszközök típusai 

## <a name="known-issues-in-preview"></a>Az előzetes verzióban ismert problémák
- VPP-licenc visszavonása: a licenc visszavonásáról szóló értesítés nem jelenik meg. A jelenlegi viselkedés az, hogy a visszavonás sikeres, de a végfelhasználó nem kap értesítést. 
- VPP Application Reporting: az ügyfélalkalmazások > alkalmazások > [alkalmazás neve] > eszköz telepítési állapotában található jelentésben a felhasználó által beléptetett eszközökre telepített VPP-alkalmazások jelentése "sikertelen", még akkor is, ha az alkalmazás sikeresen üzembe helyezte az eszközt. 
- Application Reporting: a felhasználói regisztrációval nem támogatott alkalmazások típusai esetén a jelentések nem releváns hibaüzeneteket biztosíthatnak. 
- Céges portál az alkalmazás felhasználói felületén: a felhasználók az összes megcélozt alkalmazást láthatják, függetlenül attól, hogy támogatottak-e a felhasználók által regisztrált eszközök. 
- Céges portál az alkalmazás felhasználói felületén: a felhasználók ugyanazt a szöveget látják, amely azt jelzi, hogy mely szervezetek láthatják és nem látják a felhasználók és eszközök regisztrálását.
- Ha a felhasználó a "saját szervezetem az eszköz tulajdonosa" lehetőséget választja a beléptetés során, az eszköz az Intune-ban továbbra is személyesként van megjelölve, kivéve, ha a felügyeleti konzolon vagy gráfon keresztül másképp módosítják 
- Beléptetési célzás: a iPadOS nem szerepel a platform-választóban. a iPadOS előzetes verzióban érhető el, de explicit módon nem szerepel a felügyeleti konzolon. 


## <a name="next-steps"></a>További lépések

[IOS-és iPadOS-felhasználói regisztráció beállítása](ios-user-enrollment.md)
