---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c2b9429bf5b50ac5e416c4a7b356627e9cc9fb1
ms.sourcegitcommit: f75386986d24e7d5dd63a3f1a0a014cb52056063
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560105"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Fejlesztés a Microsoft Intune – augusztus 2019

A készültség és a tervezés elősegítése érdekében ez az oldal felsorolja az Intune felhasználói felületének frissítéseit és a fejlesztés alatt álló, de még nem kiadott funkciókat. Továbbá:

- Ha várható, hogy a módosítás előtt végre kell hajtania a lépéseket, közzé kell tenni egy kiegészítő Office Message Center-bejegyzést.
- Ha egy szolgáltatás éles környezetben, előzetes verzióként vagy általánosan elérhetőként van elindítva, a szolgáltatás leírása kikerül ezen az oldalon, [](whats-new.md)és az Újdonságok oldalára kerül.
- Ez az oldal és az [új oldal](whats-new.md) rendszeresen frissül. További hírekért látogasson vissza.
- Tekintse meg a [M365 ütemtervet](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) a stratégiai termékekhez és a határidőkhöz.

> [!Note]
> Ezek az elemek tükrözik a Microsoft aktuális elvárásait az Intune-képességekről a jövőbeli kiadásokban. A dátumok és az egyes funkciók változhatnak. A fejlesztés nem minden eleme rendelkezik a funkció leírásával ezen a lapon.

**RSS-hírcsatorna**: Értesítést kaphat az oldal frissítésekor, ha a következő URL-címet másolja és beillesztette a hírcsatorna-olvasóba:`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Alkalmazáskezelés

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune app Protection-szabályzatok (alkalmazás) Android és iOS rendszerű eszközökön lehetővé teszik a szervezeti fiókok alkalmazás-értesítési tartalmának szabályozását. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy nem érhető el az összes alkalmazás-kompatibilis alkalmazáshoz. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz <!-- 3041956  -->
Az androidos munkahelyi Profilos eszközökön elérhető alkalmazások telepítéséhez megtekintheti az alkalmazás telepítési állapotát és a felügyelt Google Play-alkalmazások telepített verzióját. További információ: [az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](android-enterprise-overview.md) -nal és a [felügyelt Google Play-alkalmazás típusa](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Az iOS rendszerhez készült IKEv2 VPN-profilok támogatása <!-- 1943438 -->
A IKEv2 protokoll használatával VPN-profilokat hozhat létre az iOS natív VPN-ügyfél számára. A IKEv2 egy új kapcsolattípus az **eszköz konfigurációs** > **profiljaiban** > **profil** > létrehozása**iOS** for platform > **VPN** a profil típusa > **Beállítások**.

Ezek a VPN-profilok a natív VPN-ügyfelet konfigurálja. Tehát a felügyelt eszközökre nincs telepítve vagy leküldve VPN-ügyfélalkalmazások. Ehhez a szolgáltatáshoz regisztrálni kell az eszközöket az Intune-ban (MDM-regisztráció).

Az aktuálisan konfigurálható VPN-beállítások megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS](vpn-settings-ios.md)-eszközökön a Microsoft Intune.

A következőre vonatkozik: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Eszközök beléptetése

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS-eszközök esetén szabja testre a beléptetési folyamat adatvédelmi képernyőjét a Céges portál <!-- 4394993  -->
A Markdown segítségével testre szabhatja a Céges portál adatvédelmi képernyőjét, amelyet a végfelhasználók az iOS-regisztráció során látnak. Pontosabban testreszabhatja azon dolgok listáját, amelyeket a szervezete nem lát vagy tesz az eszközön.

<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="import-and-export-security-baselines------3408610------------"></a>Biztonsági alaptervek importálása és exportálása    <!--3408610          -->  
Hozzáadjuk a biztonsági alapkonfigurációk exportálásához és importálásához szükséges képességet. Ez a funkció lehetővé teszi a testreszabásokat, és megoszthatja őket az Intune-környezetek között.

<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még:
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new.md).




