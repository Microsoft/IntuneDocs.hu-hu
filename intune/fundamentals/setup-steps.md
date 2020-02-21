---
title: A Microsoft Intune beállítása
description: Az Intune-előfizetés használatának megkezdéséhez szükséges követelmények és előfeltételek
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b12781c55abc3ce7d9e964b0f139fc4c1d1fd69b
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529362"
---
# <a name="set-up-intune"></a>Az Intune beállítása

Ezek a beállítási lépések segítenek az Intune mobileszköz-kezelésének (MDM) engedélyezésében. A felhasználóknak csak az eszközkezelés beállítása után adhat hozzáférési jogosultságot a vállalati erőforrásokhoz, és csak ezután kezelheti az eszközök beállításait.

Néhány lépés, például az Intune-előfizetés és az MDM-jogosultság beállítása, a legtöbb forgatókönyv esetén szükséges. Egyéb lépések, például egyéni tartomány konfigurálása vagy alkalmazások hozzáadása, nem kötelezőek, és a vállalat igényeitől függnek.

Ha jelenleg a Microsoft Endpoint Configuration Manager használatával felügyeli a számítógépeket és a kiszolgálókat, akkor [a felhőhöz csatolhatja a Configuration Managert a közös felügyelettel](https://docs.microsoft.com/configmgr/comanage/overview).

>[!TIP]
>Ha egy erre jogosult csomagban megvásárol legalább 150 Intune-licencet, akkor használhatja a *FastTrack Center értékcsomagot*. Ennek a szolgáltatásnak a keretében a Microsoft szakemberei együttműködnek Önnel a környezete Intune-hoz való előkészítése érdekében. Lásd: [FastTrack Center juttatás az Enterprise Mobility + Securityhez (EMS)](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).

| Lépések | Állapot  |
|---|---|
|   1   | [Támogatott konfigurációk](supported-devices-browsers.md) – Tudnivalók a kezdés előtt. Ez a szakasz tartalmazza a támogatott konfigurációkat és a hálózati követelményeket.|
|   2   |  [Bejelentkezés az Intune-ba](account-sign-up.md) – Jelentkezzen be a próba-előfizetésbe, vagy hozzon létre egy új Intune-előfizetést. |
|   3   | [Tartománynév konfigurálása](custom-domain-name-configure.md) – DNS-regisztráció beállítása a vállalat tartománynevének Intune-nal való összekapcsolásához. Ezáltal a felhasználók egy ismerős tartományban kapcsolódhatnak az Intune-hoz, és használhatják az erőforrásokat. |
|   4   | [Felhasználók](users-add.md) és [csoportok](../groups-add.md) hozzáadása – felhasználók és csoportok hozzáadása, illetve Active Directory összekötése az Intune-nal való szinkronizáláshoz. Kötelező, kivéve, ha az eszközei „felhasználó nélküliek”, például kioszkeszközök. A csoportokat alkalmazások, beállítások és más erőforrások hozzárendelésére használhatja.|
|   5   | [Licencek kiosztása](../licenses-assign.md) – Engedélyezheti az Intune használatát a felhasználók számára. Minden felhasználóhoz vagy felhasználó nélküli eszközhöz Intune-licenc szükséges a szolgáltatás eléréséhez. |
|   6   | [A Mdm](../mdm-authority-set.md) -szolgáltató beállítása – a felügyeleti feladatok egyszerűbbé tételéhez használja a felhasználók és az eszközök csoportját. A csoportokat alkalmazások, beállítások és más erőforrások hozzárendelésére használhatja. |
|   7   | [Alkalmazások hozzáadása](../apps/apps-add.md) – Az alkalmazásokat hozzá lehet rendelni a csoportokhoz, és automatikusan vagy választható módon telepíthetők. |
|   8   | [Eszközök konfigurálása](../configuration/device-profiles.md) – Az eszközbeállítások kezelésére alkalmas profilok beállítása. Az eszközprofilokkal előre lehet konfigurálni az e-mailek, a VPN, a Wi-Fi és az eszközfunkciók beállításait. Az eszközök hozzáférésének korlátozására is alkalmasak, amivel védheti az eszközöket és az adatokat is. |
|   9   |  [Céges portál testreszabása](../apps/company-portal-app.md) – Testre szabhatja az Intune céges portálját, amelyet a felhasználók az eszközök regisztrálására és alkalmazások telepítésére használhatnak. Ezek a beállítások a Céges portál alkalmazásban és az Intune céges portál webhelyén is megjelennek.       |
|  10   | [Eszközök beléptetésének engedélyezése](mdm-authority-set.md) – az iOS-/iPadOS-, Windows-, Android-és Mac-eszközök Intune-felügyeletének engedélyezése a Mdm-szolgáltató beállításával és adott platformok engedélyezésével. |
|  11   |  [Alkalmazásszabályzatok konfigurálása](../apps/app-protection-policy.md) – Konkrét beállításokat adhat meg a Microsoft Intune alkalmazásvédelmi szabályzatainak alapján. |
