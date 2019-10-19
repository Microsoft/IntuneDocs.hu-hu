---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601518"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Fejlesztés a Microsoft Intune – október 2019

A készültség és a tervezés elősegítése érdekében ez az oldal felsorolja az Intune felhasználói felületének frissítéseit és a fejlesztés alatt álló, de még nem kiadott funkciókat. Az oldalon található információk mellett:

- Ha várható, hogy a módosítás előtt végre kell hajtania a lépéseket, közzé kell tenni egy kiegészítő bejegyzést az Office Message Centerben.
- Ha egy szolgáltatás éles környezetbe kerül, akár előzetes, akár általánosan elérhető, a szolgáltatás leírása az oldalról az [újdonságokra](whats-new.md)kerül át.
- Ez az oldal és az [új](whats-new.md) oldal rendszeresen frissül. További hírekért látogasson vissza.
- Tekintse meg a stratégiai termékek és ütemtervek [Microsoft 365 ütemtervét](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) .

> [!NOTE]
> Ez az oldal az Intune-funkciókra vonatkozó jelenlegi elvárásait mutatja be egy későbbi kiadásban. Előfordulhat, hogy a dátumok és az egyes funkciók változhatnak. Ez a lap nem ismerteti a fejlesztés összes funkcióját.

**RSS-hírcsatorna**: az alábbi URL-cím másolásával és a hírcsatorna-olvasóba való beillesztésével megtudhatja, hogy az oldal frissítése megtörtént-e: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Alkalmazáskezelés

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Sötét üzemmód alkalmazása iOS-Céges portál <!-- 4911422  -->
A sötét üzemmódot iOS-Céges portál tervezték. Letöltheti a vállalati alkalmazásokat, kezelheti az eszközöket, és támogatást kaphat a választott színsémában. További információ az iOS Céges portálról: [a Microsoft Intune céges portál alkalmazás konfigurálása](../apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Win32-alkalmazások futtatása Windows 10-es S üzemmódú eszközökön <!-- 3747604  --> 
A Windows 10 S módban felügyelt eszközökön Win32-alkalmazásokat telepíthet és futtathat. Hozzon létre egy vagy több kiegészítő szabályzatot az S üzemmódhoz a Windows Defender Application Control (WDAC) PowerShell-eszközök használatával. A kiegészítő szabályzatok aláírásához használja az eszköz Guard-aláírási portálját. Ezután töltse fel és terjessze a szabályzatokat az Intune-on keresztül. 

Az Intune-ban ezt a képességet az **ügyfélalkalmazások** > **Windows 10 S kiegészítő szabályzatok**kiválasztásával találja meg. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Alkalmazás rendelkezésre állásának beállítása dátum és idő alapján <!-- 3510685  -->
Rendszergazdaként konfigurálhatja a szükséges alkalmazás kezdési idejét és határidejét. A kezdési időpontban az Intune felügyeleti bővítmény letölti az alkalmazás tartalmát, és gyorsítótárazza. Az alkalmazás a határidő lejártakor lesz telepítve. Az elérhető alkalmazások esetében a kezdési időpont akkor fog megjelenni, amikor az alkalmazás megjelenik a Céges portálban. 

Az alkalmazások rendelkezésre állásának beállítása dátum és idő alapján:

1. Az Intune-ban válassza a **Client apps** > **alkalmazások**elemet. 
1. Válasszon ki egy alkalmazást a listából, vagy adjon hozzá egy újat a **Hozzáadás gombra**kattintva. 
1. Az alkalmazás panelen válassza a **hozzárendelések** > **Csoport hozzáadása**elemet. 
1. Állítsa a **hozzárendelés típusát** **kötelező** értékre, majd válassza a **befoglalt csoportok**lehetőséget. 
1. Állítsa be **ezt az alkalmazást az összes felhasználó** számára az **Igen**értékre. 
1. Válassza a **Szerkesztés** lehetőséget a **végfelhasználói élmény** beállításainak módosításához. 
1. A **végfelhasználói élmény** panelen szükség szerint állítsa be a **szoftver rendelkezésre állási idejét** . 

További információt az [Alkalmazások hozzáadása a Microsoft Intune-hoz](../apps/apps-add.md) című cikkben talál.

### <a name="require-win32-apps-to-restart----3136567----"></a>Win32-alkalmazások újraindításának megkövetelése <!-- 3136567  -->
A sikeres telepítés után a Win32-alkalmazás újraindítását is megkövetelheti. Kiválaszthatja, hogy mennyi idő (türelmi időszak) legyen az újraindítás előtt.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Értesítések megjelenítése a Windows Céges portál alkalmazásához <!-- 1808082  -->
A Windows-eszközökön a Céges portál alkalmazást frissítjük a bejelentési értesítések megjelenítéséhez a felhasználók számára, még akkor is, ha az alkalmazás be van zárva. A frissítés csak akkor jeleníti meg az elérhető alkalmazások értesítéseit, ha a telepítés állapota befejeződött vagy sikertelen. A Céges portál alkalmazás nem jeleníti meg az értesítéseket a szükséges alkalmazásokhoz.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>A Céges portál alkalmazás telepítési állapotüzenetek megjelenítése <!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.
- Az alkalmazás telepítése sikeresen megtörtént, de újraindítást igényel.
- Az alkalmazás telepítése folyamatban van, de a folytatáshoz újraindítás szükséges.

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>A Microsoft Edge bétaverziójának kiosztása macOS-hez <!-- 4678761  -->
A Microsoft Edge Beta legújabb verzióját hozzáadhatja és hozzárendelheti a macOS-eszközökhöz készült Intune-hoz. 

A Microsoft Edge bétaverziójának a macOS-eszközökhöz való hozzárendeléséhez:
1. Az Intune-ban válassza a **Client apps** > **alkalmazások** > **alkalmazás hozzáadása** > **Microsoft Edge-MacOS**elemet. 
1. Rendelje hozzá a Microsoft Edge Beta-t a kívánt csoportokhoz. A Microsoft AutoUpdate (MAU) naprakészen tartja a Microsoft Edge-t. 
 
A Microsoft Edge-vel kapcsolatos további információkért lásd: [webes elérés kezelése a Microsoft Edge és a Microsoft Intune használatával](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune alkalmazás Android-és iOS-eszközökön lehetővé teszi az alkalmazások értesítési tartalmának vezérlését a szervezeti fiókok számára. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy az összes APP-kompatibilis alkalmazáshoz nem érhető el. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Új eszköz belső vezérlőprogram-konfigurációs felületének profilja a Windows 10 és újabb rendszerű eszközökhöz <!-- 2266073  -->
Windows 10 és újabb rendszereken a beállítások és funkciók vezérléséhez létrehozhat egy eszköz-konfigurációs profilt: 

1. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
1. A platform esetében válassza a **Windows 10 és újabb**lehetőséget. 
 
Az új eszköz belső vezérlőprogram-konfigurációs felületének típusa lehetővé teszi az Intune számára az UEFI-(BIOS-) beállítások kezelését.

Az aktuálisan konfigurálható beállításokkal kapcsolatos további információkért lásd: a [szolgáltatások és beállítások alkalmazása az eszközökön a Microsoft Intune eszköz profiljainak használatával](../configuration/device-profiles.md).

Ez a funkció a Windows 10 RS5 (1809) és újabb verziókra vonatkozik az eszközök kijelölésekor.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Eszközök beléptetése

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>IOS-eszközök esetén a Céges portál beléptetési adatvédelmi ablakának testreszabása <!-- 4394993  -->
A Markdown segítségével testre szabhatja a felhasználók által az iOS-regisztráció során megjelenő Céges portál adatvédelmi időszakot. Pontosabban testreszabhatja azon dolgok listáját, amelyeknek a szervezete nem látja vagy végezheti az eszközt.

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>A csoport címke értékének szerkesztése az Autopilot-eszközökhöz<!-- 4816775 -->
Az Autopilot-eszközökhöz a **Group címke** értékét is szerkesztheti:

1. Válassza **az Intune** > **eszközök beléptetése** > **Windows-beléptetés** > **Windows Autopilot** > **eszközök**elemet.
1. Válassza ki az eszközt.
1. A jobb oldali ablaktáblán módosítsa a **csoport címke** értékét.
1. Válassza a **Mentés** lehetőséget.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>JAMF-felügyeletet igénylő macOS-felhasználói csoportok célzása <!-- 4061739 -->
A felhasználók meghatározott csoportjait megcélozhatja, hogy a macOS-eszközöket a JAMF kezelje. Ez a célzás lehetővé teszi, hogy a JAMF-megfelelőségi integrációt a macOS-eszközök egy részhalmazára alkalmazza, míg más eszközöket továbbra is az Intune kezel. A célzás azt is lehetővé teszi, hogy fokozatosan áttelepítse a felhasználók eszközeit egy mobileszköz-felügyeleti (MDM) rendszerről a másikra.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Szoftverfrissítések központi telepítése macOS-eszközökre <!-- 3194876 -->
A macOS-eszközök csoportjaira telepíthet szoftverfrissítéseket. Ez a szolgáltatás kritikus, belső vezérlőprogram, konfigurációs fájl és egyéb frissítéseket tartalmaz. A frissítéseket a következő eszköz beadásával küldheti el. Vagy kiválaszthat egy heti ütemtervet a frissítések telepítéséhez a beállított időszakokban vagy azokon kívül is. 

Ez a funkció segít abban az esetben, ha az eszközöket a szokásos munkaidőn kívüli vagy azon kívüli órákban szeretné frissíteni, amikor az ügyfélszolgálata teljesen munkatársa. Emellett részletes jelentést is kap az összes olyan macOS-eszközről, amelyen telepítve vannak a frissítések. Egy adott frissítés állapotának megjelenítéséhez az eszköz segítségével megtekintheti a jelentést.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Figyelés és hibaelhárítás

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Android-jelentés az eszközök – áttekintés oldalon <!-- 2984353  -->
Új jelentést fogunk hozzáadni az **eszközök áttekintés** lapjához. A jelentés azt jeleníti meg, hogy hány androidos eszköz van regisztrálva az egyes eszközkezelés megoldásokban. A diagramon a munkahelyi profil, a teljes körűen felügyelt, a dedikált és az eszköz-rendszergazda által regisztrált eszközök száma látható. 

A jelentés megtekintéséhez válassza az **Intune**  > **eszközök**  > **Áttekintés**elemet.

### <a name="updated-support-experience-------5012398------"></a>Frissített támogatási élmény   <!--  5012398    -->
A folyamatos fejlődés részeként frissíteni fogjuk a konzolon belüli támogatási élményt az Intune-ban.  Javítani fogjuk a konzolon belüli kereséseket és visszajelzéseket a gyakori problémák esetén, és a munkafolyamatot egyszerűsítjük, hogy kapcsolatba lépjenek a támogatási szolgálattal.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>További információ
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.
