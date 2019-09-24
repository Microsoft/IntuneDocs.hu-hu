---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6c88dca505c3ef9d9d552e55e9991679f5f5e0fa
ms.sourcegitcommit: 5968a38c302394d4b0cf81156e7b52531cdec107
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71198820"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>Fejlesztés a Microsoft Intune – szeptember 2019

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

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Alkalmazás-telepítési állapotüzenetek Céges portál <!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.
- Az alkalmazás telepítése sikeresen megtörtént, de újraindítást igényel.
- Az alkalmazás telepítése folyamatban van, de a folytatáshoz újraindítás szükséges.

### <a name="macos-support-for-vpp-apps----3173501----"></a>a macOS-alkalmazások macOS-támogatása <!-- 3173501  -->
az Apple Business Manager használatával megvásárolt macOS-alkalmazások megjelennek a konzolon, amikor az Apple VPP-tokenek szinkronizálva vannak az Intune-ban. A-konzol használatával hozzárendelheti, visszavonhatja és újból hozzárendelheti a csoportok eszköz-és felhasználói licenceit. A Microsoft Intune segítségével kezelheti a vállalat által a cégnél való használatra megvásárolt VPP-alkalmazásokat:
- Licencinformációk jelentése az App Store-ból.
- A felhasznált licencek számának nyilvántartása.
- Annak megakadályozása, hogy több példányt telepítsen az alkalmazásból, mint amennyit vásárolt.
Az Intune-nal és a VPP-vel kapcsolatos további információkért lásd: [mennyiségi programban vásárolt alkalmazások és könyvek kezelése Microsoft Intuneokkal](vpp-apps.md).

### <a name="macos-support-for-web-apps----3174427----"></a>macOS-támogatás webes alkalmazásokhoz <!-- 3174427  -->
A webalkalmazások telepíthetők, amelyek lehetővé teszik a webes URL-címekhez való parancsikonok hozzáadását a dockhoz a macOS Céges portál használatával. A végfelhasználók a macOS Céges portál webalkalmazásának alkalmazás részletei lapján érhetik el a **telepítési** műveletet. A **web link** alkalmazás típusával kapcsolatos további információkért lásd: [Alkalmazások hozzáadása Microsoft Intunehoz](apps-add.md).

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Microsoft Edge Beta társítása macOS-hez <!-- 4678761  -->
A Microsoft Edge Beta legújabb verzióját a macOS rendszerű eszközökhöz hozzáadhatja és hozzárendelheti az Intune-hoz. Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** > **Microsoft Edge-MacOS** **hozzáadása** > elemet. Ezután rendelje hozzá a Microsoft Edge Beta-t a kívánt csoportokhoz. A Microsoft AutoUpdate (MAU) naprakészen tartja a Microsoft Edge-t. A Microsoft Edge-vel kapcsolatos további információkért lásd: [webes elérés kezelése a Microsoft Edge és a Microsoft Intune használatával](manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune app Protection-szabályzatok (alkalmazás) Android és iOS rendszerű eszközökön lehetővé teszik a szervezeti fiókok alkalmazás-értesítési tartalmának szabályozását. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy nem érhető el az összes alkalmazás-kompatibilis alkalmazáshoz. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz <!-- 3041956  -->
Az androidos munkahelyi Profilos eszközökön elérhető alkalmazások telepítéséhez megtekintheti az alkalmazás telepítési állapotát és a felügyelt Google Play-alkalmazások telepített verzióját. További információ: [az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](android-enterprise-overview.md) -nal és a [felügyelt Google Play-alkalmazás típusa](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
<!--## Device configuration-->

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Eszközök beléptetése

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS-eszközök esetén szabja testre a beléptetési folyamat adatvédelmi képernyőjét a Céges portál <!-- 4394993  -->
A Markdown segítségével testre szabhatja a Céges portál adatvédelmi képernyőjét, amelyet a végfelhasználók az iOS-regisztráció során látnak. Pontosabban testreszabhatja azon dolgok listáját, amelyeket a szervezete nem lát vagy tesz az eszközön.

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Szoftverfrissítések központi telepítése macOS-eszközökre <!-- 3194876 -->
A macOS-eszközök csoportjaira telepíthet szoftverfrissítéseket. Ez a szolgáltatás kritikus, belső vezérlőprogram, konfigurációs fájl és egyéb frissítéseket tartalmaz. Frissítéseket küldhet a következő eszköz-bejelentkezéshez, vagy kiválaszthat egy heti ütemtervet a frissítések központi telepítésére a beállított időpontokban. Ez segít abban az esetben, ha az eszközöket a normál munkaidőn kívül szeretné frissíteni, vagy ha az ügyfélszolgálat teljes mértékben munkatársaival rendelkezik. Emellett részletes jelentést is kap az összes olyan macOS-eszközről, amelyen telepítve vannak a frissítések. Az egyes frissítések állapotának megjelenítéséhez a jelentést eszközönként is megtekintheti.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

### <a name="updated-support-experience-------5012398------"></a>Frissített támogatási élmény   <!--  5012398    -->
A folyamatos tökéletesítések részeként frissíteni fogjuk a konzolon belüli támogatási élményt az Intune-ban.  Fejlesztjük a konzolon belüli keresést és visszajelzést a gyakori problémákról, és egyszerűsítheti a munkafolyamatot, hogy kapcsolatba lépjen a támogatási szolgálattal.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még:
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new.md).




