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
ms.openlocfilehash: 4bd5392abba3ea22127cb9bcbbb53ec4929f2d5e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166325"
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

### <a name="managed-google-play-private-lob-apps----1464182----"></a>Felügyelt Google Play Private LOB-alkalmazások <!-- 1464182  -->
Az Intune lehetővé teszi a rendszergazdák számára, hogy privát Android LOB-alkalmazásokat tegyenek közzé a Google Play szolgáltatásban az Intune-konzolon beágyazott iframe használatával.  Jelenleg a rendszergazdáknak el kell végezniük a LOB-alkalmazások közvetlen közzétételét a Google Play közzétételi konzolján, amely számos lépést igényel, és nagyon sok időt vesz igénybe.  Ez az új funkció lehetővé teszi a LOB-alkalmazások egyszerű közzétételét egy minimális lépéssel anélkül, hogy el kellene hagynia az Intune-konzolt.  A felügyelt Google Play szolgáltatást használó androidos vállalati felügyeleti forgatókönyvek bármelyike kihasználhatja ezt a funkciót (munkahelyi profil, dedikált, teljes körűen felügyelt és nem regisztrált eszközök).  Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**elemet. Ezután válassza a **felügyelt Google Play** lehetőséget az **alkalmazás típusa** listából. A felügyelt Google Play-alkalmazásokkal kapcsolatos további információkért lásd: [felügyelt Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune](apps-add-android-for-work.md)-nal.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Alkalmazás-telepítési állapotüzenetek Céges portál <!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.
- Az alkalmazás telepítése sikeresen megtörtént, de újraindítást igényel.
- Az alkalmazás telepítése folyamatban van, de a folytatáshoz újraindítás szükséges.

### <a name="managed-google-play-iframe-support----2871756----"></a>Felügyelt Google Play iframe-támogatás <!-- 2871756  -->
Az Intune a felügyelt Google Play iframe segítségével közvetlenül az Intune-konzolon fogja támogatni a webes hivatkozások hozzáadását és kezelését.  Ez lehetővé teszi, hogy a rendszergazdák elküldjék az URL-címet és az ikont, majd ezeket a hivatkozásokat a normál Android-alkalmazásokhoz hasonló eszközökre telepítse. A felügyelt Google Play szolgáltatást használó androidos vállalati felügyeleti forgatókönyvek bármelyike kihasználhatja ezt a funkciót (munkahelyi profil, dedikált, teljes körűen felügyelt és nem regisztrált eszközök).  Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**elemet. Ezután válassza a **felügyelt Google Play** lehetőséget az **alkalmazás típusa** listából. A felügyelt Google Play-alkalmazásokkal kapcsolatos további információkért lásd: [felügyelt Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune](apps-add-android-for-work.md)-nal.

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

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Az Intune-alkalmazások Graph API műveleteinek olvasása és írása <!-- 5031704  -->
Az alkalmazások az Intune-Graph API az olvasási és írási műveletekkel is meghívhatják az alkalmazás-identitás felhasználói hitelesítő adatok nélkül. További információ az Intune-hoz készült Microsoft Graph API eléréséről: az [Intune használata a Microsoft Graphban](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune app Protection-szabályzatok (alkalmazás) Android és iOS rendszerű eszközökön lehetővé teszik a szervezeti fiókok alkalmazás-értesítési tartalmának szabályozását. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy nem érhető el az összes alkalmazás-kompatibilis alkalmazáshoz. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz <!-- 3041956  -->
Az androidos munkahelyi Profilos eszközökön elérhető alkalmazások telepítéséhez megtekintheti az alkalmazás telepítési állapotát és a felügyelt Google Play-alkalmazások telepített verzióját. További információ: [az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](android-enterprise-overview.md) -nal és a [felügyelt Google Play-alkalmazás típusa](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>A regisztrációs típus megjeleníti az eszközök funkcióit, az eszközök korlátozásait és a bővítményi profilokat az iOS-és macOS-beállításokhoz. <!-- 4886161  -->

Az Intune-ban létrehozhat profilokat az iOS-és MacOS-eszközökhöz (az eszköz**konfigurációs** > **profiljai** > az**iOS** vagy **MacOS** rendszerek**létrehozása** > platform > **eszköz funkciói** , **Eszközök korlátozásai**vagy **bővítmények** a profil típusához). A profilokban jelenleg elérhető beállítások vannak felsorolva. 

Egy későbbi frissítés során az Intune-portálon elérhető beállítások a beléptetési típus szerint lesznek kategorizálva:

- iOS
  - Minden regisztrációs típus
  - Eszközök beléptetése és automatikus eszközök beléptetése
  - Automatikus eszközök beléptetése

- macOS
  - Minden regisztrációs típus
  - Eszközök beléptetése
  - Felhasználó által jóváhagyott és automatizált eszközök beléptetése
  - Automatikus eszközök beléptetése

Érintett kiadások:

- iOS
  - [Eszközfunkciók](ios-device-features-settings.md)
  - [Eszközkorlátozások](device-restrictions-ios.md)

- macOS
  - [Eszközfunkciók](macos-device-features-settings.md)
  - [Eszközkorlátozások](device-restrictions-macos.md)
  - [Bővítmények](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>A teljes képernyős módban futó, felügyelt iOS-eszközök új hang-vezérlési beállításai <!-- 4892835  -->

Az Intune-ban házirendeket hozhat létre a felügyelt iOS-eszközök kioszkként való futtatásához, vagy dedikált eszközként (az**eszköz konfigurációs** > **profiljainak** > **profil** > létrehozása**iOS** platformon >A profilhoz > kioszkhoz tartozó eszközök korlátozásai **(csak felügyelt eszköz esetén)** ). 

A jövőbeli frissítésekben új beállítások is megadhatók:

- Hangvezérelt **vezérlés**: Kioszk módban engedélyezheti a hangvezérelt vezérlést az eszközön.
- **A hangvezéreltség módosítása**: Lehetővé teszi a felhasználók számára, hogy kioszk módban módosítsák az eszköz hangvezérlési beállítását.

Az aktuális beállítások megjelenítéséhez nyissa meg az [iOS kioszk (csak felügyelt) beállításokat](device-restrictions-ios.md#kiosk).

Érintett kiadások:

- iOS 13,0 és újabb verziók

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>Egyszeri bejelentkezés használata az iOS-és macOS-eszközökön futó alkalmazásokhoz és webhelyekhez <!-- 4893175  -->
Egy későbbi frissítés során az iOS-és MacOS-eszközökhöz tartozó új egyszeri bejelentkezési beállítások lesznek elérhetők (az**eszköz konfigurációs** > **profiljai** > az**iOS** -vagy **MacOS** -es**profil létrehozása** >  platform > **eszköz jellemzői** a profil típusaként).

Ezekkel a beállításokkal konfigurálhatja az egyszeri bejelentkezési élményt, különösen a Kerberos-hitelesítést használó alkalmazásokhoz és webhelyekhez. Választhat egy általános hitelesítő adatok egyszeri bejelentkezési alkalmazás-bővítménye és az Apple beépített Kerberos-bővítménye közül.

Az eszköz aktuálisan konfigurálható szolgáltatásainak megtekintéséhez nyissa meg az [iOS-eszközök funkcióit](ios-device-features-settings.md) és a [MacOS-eszközök funkcióit](macos-device-features-settings.md).

Érintett kiadások:

- iOS 13,0 és újabb verziók
- macOS 10,15 és újabb verziók

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>Tartományok hozzárendelése macOS-10.15 és-eszközökön futó alkalmazásokhoz <!-- 4898079  -->
MacOS-eszközökön különböző funkciókat konfigurálhat, és leküldheti ezeket a funkciókat az eszközökre egy szabályzat használatával (az**eszköz konfigurációs** > **profiljaiban** > a**profil** > létrehozása**MacOS** for platform > **eszköz jellemzői** a profil típusaként). A jövőbeli frissítésekben a tartományokat hozzárendelheti az alkalmazásaihoz. Ez a szolgáltatás segít megosztani a hitelesítő adatokat az alkalmazással kapcsolatos webhelyekkel, és használható az Apple egyszeri bejelentkezési bővítménnyel, az univerzális hivatkozásokkal és a jelszavak automatikus kitöltésével. 

Az aktuálisan konfigurálható szolgáltatások megjelenítéséhez nyissa meg a [MacOS-eszköz szolgáltatás beállításait az Intune-ban](macos-device-features-settings.md).

Érintett kiadások:

- macOS 10,15 és újabb verziók

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>Az iOS-es felügyelt eszközökön lévő alkalmazások megjelenítéséhez vagy elrejtéséhez használja az iTunes alkalmazás-áruház URL-címe "iTunes" és "alkalmazások" elemét. <!-- 4928474  --> 
Az Intune-ban szabályzatokat hozhat létre a felügyelt iOS-eszközökön lévő alkalmazások megjelenítéséhez vagy elrejtéséhez (az**eszköz konfigurációs** > **profiljaiban** > **létrehozhat egy profilt** > **iOS** platform > **eszközhöz** a profil típusának korlátozásai > az **alkalmazások megjelenítése vagy elrejtése (csak felügyelt eszköz esetén)** ). 

Megadhatja az iTunes alkalmazás-áruház URL-címét `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`, például:. A jövőbeli frissítésekben használhatja `apps` a (z) és `itunes` az URL-címet is, például:

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

További információ ezekről a beállításokról: [alkalmazások megjelenítése vagy elrejtése](device-restrictions-ios.md#show-or-hide-apps).

Érintett kiadások:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Az iOS rendszerhez készült IKEv2 VPN-profilok támogatása <!-- 1943438 -->
A IKEv2 protokoll használatával VPN-profilokat hozhat létre az iOS natív VPN-ügyfél számára. A IKEv2 egy új kapcsolattípus az **eszköz konfigurációs** > **profiljaiban** > **profil** > létrehozása**iOS** for platform > **VPN** a profil típusa > **Beállítások**.

Ezek a VPN-profilok a natív VPN-ügyfelet konfigurálja. Tehát a felügyelt eszközökre nincs telepítve vagy leküldve VPN-ügyfélalkalmazások. Ehhez a szolgáltatáshoz regisztrálni kell az eszközöket az Intune-ban (MDM-regisztráció).

Az aktuálisan konfigurálható VPN-beállítások megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS](vpn-settings-ios.md)-eszközökön a Microsoft Intune.

A következőre vonatkozik: iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>Eszközök beléptetése

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Az új bérlők alapértelmezetten az Android-eszközök rendszergazdájának felügyeletével lesznek elérhetők <!-- 4869790  -->
Az Android rendszerű eszközök rendszergazdai képességeit az Android Enterprise váltja fel. Ezért javasoljuk, hogy az Android Enterprise új regisztrációkat használjon. A jövőbeli frissítésekben az új bérlőknek a következő előfeltételeket kell végrehajtaniuk az Android-regisztrációban az eszköz rendszergazdai felügyeletének használatához: Nyissa meg az **Intune** > -**eszközök regisztrációjának** > **Android-regisztrációja** > **személyes és vállalati tulajdonú eszközök eszköz-felügyeleti jogosultságok** > **használata eszközt az eszközök felügyeletére szolgáló rendszergazda**.

A meglévő bérlők semmilyen változást nem fognak tapasztalni a környezetében. 

További információ az Android-eszközök rendszergazdájáról az Intune-ban: [Android-eszközök rendszergazdai regisztrációja](android-enroll-device-administrator.md).

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS-eszközök esetén szabja testre a beléptetési folyamat adatvédelmi képernyőjét a Céges portál <!-- 4394993  -->
A Markdown segítségével testre szabhatja a Céges portál adatvédelmi képernyőjét, amelyet a végfelhasználók az iOS-regisztráció során látnak. Pontosabban testreszabhatja azon dolgok listáját, amelyeket a szervezete nem lát vagy tesz az eszközön.

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Szoftverfrissítések központi telepítése macOS-eszközökre <!-- 3194876 -->
A macOS-eszközök csoportjaira telepíthet szoftverfrissítéseket. Ez a szolgáltatás kritikus, belső vezérlőprogram, konfigurációs fájl és egyéb frissítéseket tartalmaz. Frissítéseket küldhet a következő eszköz-bejelentkezéshez, vagy kiválaszthat egy heti ütemtervet a frissítések központi telepítésére a beállított időpontokban. Ez segít abban az esetben, ha az eszközöket a normál munkaidőn kívül szeretné frissíteni, vagy ha az ügyfélszolgálat teljes mértékben munkatársaival rendelkezik. Emellett részletes jelentést is kap az összes olyan macOS-eszközről, amelyen telepítve vannak a frissítések. Az egyes frissítések állapotának megjelenítéséhez a jelentést eszközönként is megtekintheti.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>Egyéni értesítések küldése egy eszközre <!-- 4928910  -->
Egyéni értesítéseket küldhet azokhoz az eszközökhöz, amelyeken telepítve van a Céges portál vagy az Intune alkalmazás. Ehhez nyissa meg az **Intune** > -**eszközök** > **minden eszköz** > Válassza ki az eszközt > **további** > **Egyéni értesítés küldése**lehetőséget. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Az Android Enterprise teljes körűen felügyelt funkcióinak frissítései <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Az Android teljes körűen felügyelt eszközeihez a következő támogatást fogjuk hozzáadni:

- A teljes körűen felügyelt Androidhoz tartozó SCEP-tanúsítványok tanúsítvány-hitelesítésre lesznek elérhetők az eszköz tulajdonosaként kezelt eszközökön. A SCEP-tanúsítványok már támogatottak a munkahelyi profil eszközein.  Az SCEP-tanúsítványokkal a következőket teheti: <!-- 5227935 -->
    - SCEP-profil létrehozása az Android Enterprise DO szakaszban
    - SCEP-tanúsítványok csatolása Wi-Fi-profil hitelesítéshez
    - SCEP-tanúsítványok csatolása a VPN-profilokhoz hitelesítéshez
    - SCEP-tanúsítványok csatolása e-mail-profilokhoz a hitelesítéshez (az alkalmazás konfigurációja alapján)
- Az Android rendszerű vállalati eszközökön a rendszeralkalmazások támogatottak. Az Intune-ban egy androidos nagyvállalati rendszeralkalmazást kell hozzáadnia az **ügyfélalkalmazások** > **alkalmazások** > **hozzáadása**lehetőség kiválasztásával. Az **alkalmazás típusa** listában válassza az **Android Enterprise System app**elemet. További információk az alkalmazások Intune-hoz való hozzáadásáról: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md). <!-- 4062195 -->
- Az **eszköz megfelelősége** > **Android Enterprise** > -**eszköz tulajdonosában**létrehozhat egy megfelelőségi szabályzatot, amely beállítja a Google biztonság igazolási szintjét.   <!-- 4631425 -->
- Az Android Enterprise teljes körűen felügyelt eszközökön a Mobile Threat Defense-szolgáltatók lesznek támogatottak. Az **eszköz megfelelősége** > **Android Enterprise** > -**eszköz tulajdonosa**lehetőség van egy elfogadható kockázati szint kiválasztására. <!-- 4631440 --> Az [Android vállalati beállítások az eszközök megfelelő vagy nem megfelelőként való megjelölésére az Intune](compliance-policy-create-android-for-work.md#device-owner) -ban az aktuális beállítások szerepelnek.


Érintett kiadások: 
- Android Enterprise teljes körűen felügyelt eszközök

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

### <a name="updated-support-experience-------5012398------"></a>Frissített támogatási élmény   <!--  5012398    -->
A folyamatos tökéletesítések részeként frissíteni fogjuk a konzolon belüli támogatási élményt az Intune-ban.  Fejlesztjük a konzolon belüli keresést és visszajelzést a gyakori problémákról, és egyszerűsítheti a munkafolyamatot, hogy kapcsolatba lépjen a támogatási szolgálattal.     

<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Illetéktelen védelem a Windows Defender Víruskeresőben  <!-- 4705448       -->
Az Intune által a Windows Defender víruskeresőhöz felügyelhető beállításokhoz az *illetéktelen hozzáférést biztosító védelmet* fogjuk hozzáadni. A Windows 10-es Endpoint Protection eszköz konfigurációs profiljának használatával engedélyezheti a illetéktelen hozzáférést a védelem be-és kikapcsolásához.  További információ az illetéktelen hozzáférést biztosító védelemről: a [biztonsági beállítások módosításának megakadályozása](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) a Windows dokumentációjában. 


<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még:
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new.md).




