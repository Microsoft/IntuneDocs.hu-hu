---
title: A Microsoft Intune beállítása
description: Az Intune-előfizetés használatának megkezdéséhez szükséges követelmények és előfeltételek
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f818c35a008c24a529967b09a37917343433ff7d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-intune"></a>Az Intune beállítása

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Ezek a beállítási lépések segítenek az Intune mobileszköz-kezelésének (MDM) engedélyezésében. A felhasználóknak csak az eszközkezelés beállítása után adhat hozzáférési jogosultságot a vállalati erőforrásokhoz, és csak ezután kezelheti az eszközök beállításait.

Néhány lépés, például az Intune-előfizetés és az MDM-jogosultság beállítása, a legtöbb forgatókönyv esetén szükséges. Egyéb lépések, például egyéni tartomány konfigurálása vagy alkalmazások hozzáadása, nem kötelezőek, és a vállalat igényeitől függnek.

Ha jelenleg a Microsoft System Center Configuration Managerrel felügyeli a számítógépeket és a kiszolgálókat, [kiterjesztheti a Configuration Manager hatáskörét, hogy a mobileszközöket is felügyelje](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

>[!TIP]
>Ha egy erre jogosult csomagban megvásárol legalább 150 Intune-licencet, akkor használhatja a *FastTrack Center értékcsomagot*. Ennek a szolgáltatásnak a keretében a Microsoft szakemberei együttműködnek Önnel a környezete Intune-hoz való előkészítése érdekében. Lásd: [FastTrack Center juttatás az Enterprise Mobility + Securityhez (EMS)](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).



| Lépések |                                                                                                                       Állapot                                                                                                                       |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   1   |                                        [Támogatott konfigurációk](supported-devices-browsers.md) – Tudnivalók a kezdés előtt. Ez a szakasz tartalmazza a támogatott konfigurációkat és a hálózati követelményeket.                                         |
|   2   |                                                                 [Bejelentkezés az Intune-ba](account-sign-up.md) – Jelentkezzen be a próba-előfizetésbe, vagy hozzon létre egy új Intune-előfizetést.                                                                  |
|   3   |                [Tartománynév konfigurálása](custom-domain-name-configure.md) – DNS-regisztráció beállítása a vállalat tartománynevének Intune-nal való összekapcsolásához. Ezáltal a felhasználók egy ismerős tartományban kapcsolódhatnak az Intune-hoz, és használhatják az erőforrásokat.                |
|   4   |                                   [Felhasználók hozzáadása](users-add.md) – Felhasználók manuális hozzáadása, vagy kapcsolódás az Active Directoryhoz a felhasználók és az Intune szinkronizálásához. Kötelező, kivéve, ha az eszközei „felhasználó nélküliek”, például kioszkeszközök.                                    |
|   5   |                                            [Licencek kiosztása](licenses-assign.md) – Engedélyezheti az Intune használatát a felhasználók számára. Minden felhasználóhoz vagy felhasználó nélküli eszközhöz Intune-licenc szükséges a szolgáltatás eléréséhez.                                             |
|   6   |                                               [Csoportok hozzáadása](groups-add.md) – Felhasználói és eszközcsoportok használata a kezelési feladatok egyszerűsítésére. A csoportokat alkalmazások, beállítások és más erőforrások hozzárendelésére használhatja.                                                |
|   7   |                                                                        [Alkalmazások hozzáadása](apps-add.md) – Az alkalmazásokat hozzá lehet rendelni a csoportokhoz, és automatikusan vagy választható módon telepíthetők.                                                                         |
|   8   | [Eszközök konfigurálása](device-profiles.md) – Az eszközbeállítások kezelésére alkalmas profilok beállítása. Az eszközprofilokkal előre lehet konfigurálni az e-mailek, a VPN, a Wi-Fi és az eszközfunkciók beállításait. Az eszközök hozzáférésének korlátozására is alkalmasak, amivel védheti az eszközöket és az adatokat is. |
|   9   |       [Céges portál testreszabása](company-portal-app.md) – Testre szabhatja az Intune céges portálját, amelyet a felhasználók az eszközök regisztrálására és alkalmazások telepítésére használhatnak. Ezek a beállítások a Céges portál alkalmazásban és az Intune céges portál webhelyén is megjelennek.       |
|  10   |                                [Eszközregisztráció engedélyezése](mdm-authority-set.md) – Engedélyezheti iOS-, Windows-, Android- és Mac-eszközök kezelését az Intune-ban az MDM-jogosultság beállításával és meghatározott platformok engedélyezésével.                                 |
|  11   |                                                        [Alkalmazásszabályzatok konfigurálása](app-protection-policy.md) – Konkrét beállításokat adhat meg a Microsoft Intune alkalmazásvédelmi szabályzatainak alapján.                                                         |

