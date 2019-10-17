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
ms.openlocfilehash: fa3309cc1aad3f82499e37cf0d009da336b15cca
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502776"
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

### <a name="include-another-app-configuration-variable----4969237----"></a>Egy másik alkalmazás-konfigurációs változó belefoglalása <!-- 4969237  -->
Alkalmazás-konfigurációs házirend létrehozásakor a konfigurációs beállítások részeként felveheti a `AAD Device ID` konfigurációs változót. 

A `AAD Device ID` konfigurációs változó hozzáadása:
1. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** > **Hozzáadás**lehetőséget. 
1. Adja meg a konfigurációs szabályzat részleteit.
1. A **konfigurációs** beállítások panel megjelenítéséhez válassza a **konfigurációs beállítások**lehetőséget.

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Sötét üzemmód alkalmazása iOS-Céges portál <!-- 4911422  -->
A sötét üzemmódot iOS-Céges portál tervezték. Letöltheti a vállalati alkalmazásokat, kezelheti az eszközöket, és támogatást kaphat a választott színsémában. További információ az iOS Céges portálról: [a Microsoft Intune céges portál alkalmazás konfigurálása](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Ismeretlen forrásból származó alkalmazások telepítésének megakadályozása androidos vállalati eszközökön <!-- 4760025  -->
Az Android Enterprise Work Profile eszközein a végfelhasználók soha nem telepíthetik az ismeretlen forrásból származó alkalmazásokat a munkahelyi profilban. Dönthet úgy, hogy kiterjeszti ezt a korlátozást a személyes profilra is. Ha engedélyezi ezt a korlátozást, a végfelhasználók az Android Enterprise munkahelyi profil eszközei nem tudják majd az ismeretlen forrásból származó alkalmazásokat az eszközük személyes oldalára betölteni. 

### <a name="use-an-updated-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Frissített app Protection felhasználói felület és iOS-alkalmazás üzembe helyezési felhasználói felületének használata <!-- 4102027, 4102029  -->
A felhasználói felületet az alkalmazás-védelmi szabályzatok (alkalmazás) és az iOS-alkalmazások létesítési profiljainak az Intune-ban történő létrehozásához és szerkesztéséhez fogjuk frissíteni. A felhasználói felület változásai a következők:
- Egyszerűsített felület, amely egy varázsló stílusú formátumot használ egy panelen. 
- A létrehozási folyamatra vonatkozó frissítés, amely tartalmazza a hozzárendeléseket.
- Összefoglalás. Amikor új házirend létrehozása előtt vagy egy tulajdonság szerkesztésekor megtekinti a tulajdonságokat, megjelenik az összes beállítás összefoglaló lapja. Emellett a Tulajdonságok szerkesztése során az összefoglalás csak a szerkesztett tulajdonságok kategóriájában lévő elemeket sorolja fel.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Házirend-készletek nevű felügyeleti objektumok csoportjainak létrehozása <!-- 3762880  -->
A *házirend-beállításokkal* olyan meglévő felügyeleti entitásokra mutató hivatkozásokat hozhat létre, amelyeket azonosítani, megcélozni és egyetlen fogalmi egységként kell figyelni. A házirend-készletek nem helyettesítik a meglévő fogalmakat vagy objektumokat. A rendszergazdák továbbra is hozzárendelhetők az egyes objektumokhoz, ahogy ma még nem. A házirend-készletek az egyes objektumokra hivatkoznak. Ezért az egyes objektumok módosításai a házirend-készletben is megjelennek. 

Ha létre szeretne hozni egy szabályzatot az Intune-ban, válassza ki a következő **házirend-készleteket**:  > **Létrehozás**. 

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

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz <!-- 3041956  -->
Az androidos munkahelyi profilú eszközökön elérhető alkalmazások telepítéséhez megtekintheti az alkalmazás telepítési állapotát és a felügyelt Google Play-alkalmazások telepített verzióját. További információkért lásd: [az alkalmazás-védelmi szabályzatok figyelése](../apps/app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](../enrollment/android-enterprise-overview.md)-nal és a [Google Play-alkalmazások felügyelt típusai](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Új eszköz konfigurációs beállításai felügyelt iOS-és iPadOS-eszközökhöz <!-- 5199328  -->
IOS-és iPadOS-eszközökön létrehozhat egy profilt, amely az eszközök funkcióit és beállításait korlátozza:

1. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
1. A platform esetében válassza az **iOS/iPadOS**lehetőséget.
1. A profil típusa beállításnál válassza az **eszközök korlátozásai**elemet.

Az új beállításokat az alábbiak szerint vezérelheti: 
- Nyissa meg a hálózati meghajtót a fájlok alkalmazásban.  
- Nyissa meg az USB-meghajtót a Files alkalmazásban. 
- Tartsa meg a Wi-Fi-t. 

Az aktuális beállításokkal kapcsolatos további információkért lásd: [iOS-eszközbeállítások, amelyekkel engedélyezheti vagy korlátozhatja a szolgáltatásokat az Intune használatával](../configuration/device-restrictions-ios.md).

Az új beállítások a következőkre vonatkoznak:
- iOS 13,0 és újabb verziók.
- iPadOS 13,0 és újabb verziók.

### <a name="removal-of-automatic-connection-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>A Wi-Fi profilokban lévő automatikus kapcsolat eltávolítása Android-és Android Enterprise-eszközökön <!-- 5021055  -->
Az Android és az Android rendszerű vállalati eszközökön létrehozhat egy Wi-Fi profilt a különböző beállítások konfigurálásához: 

1. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
1. A platform esetében válassza az **Android** vagy az **Android Enterprise**lehetőséget.
1. A profil típusa beállításnál válassza a **Wi-Fi**lehetőséget. 

A **kapcsolat automatikus** beállítása el lesz távolítva, mert az [Android nem támogatja](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29).

Ha ezt a beállítást egy Wi-Fi-profilban használja, észreveheti, hogy a **Csatlakozás automatikusan** nem működik. Semmilyen műveletet nem kell elvégeznie, de vegye figyelembe, hogy ez a beállítás el lesz távolítva az Intune felhasználói felületéről.

Az aktuális beállításokkal kapcsolatos információkért lépjen az [Android Wi-Fi beállítások](../configuration/wi-fi-settings-android.md) vagy az [Android Enterprise Wi-Fi beállítások](../configuration/wi-fi-settings-android-enterprise.md)elemre.

A beállítás eltávolítása a következőkre vonatkozik:
- Android.
- Android Enterprise.

### <a name="global-http-proxy-on-android-enterprise-devices----4816339----"></a>Globális HTTP-proxy az Android Enterprise-eszközökön <!-- 4816339  -->
Az Android Enterprise rendszerű eszközökön egy globális HTTP-proxyt konfigurálhat a szervezet webböngészési szabványainak teljesítéséhez:

1. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
1. A platform esetében válassza az **Android Enterprise**lehetőséget.
1. Válassza ki az **eszköz tulajdonosát**.
1. A profil típusa beállításnál válassza az **eszközök korlátozásai**elemet. 
1. Válassza a **kapcsolat**lehetőséget. 
 
A proxy konfigurálása után az összes HTTP-forgalom fogja használni. Ez a funkció az eszköz-tulajdonos módban lévő androidos vállalati eszközökre vonatkozik.

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Új eszköz belső vezérlőprogram-konfigurációs felületének profilja a Windows 10 és újabb rendszerű eszközökhöz <!-- 2266073  -->
Windows 10 és újabb rendszereken a beállítások és funkciók vezérléséhez létrehozhat egy eszköz-konfigurációs profilt: 

1. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
1. A platform esetében válassza a **Windows 10 és újabb**lehetőséget. 
 
Az új eszköz belső vezérlőprogram-konfigurációs felületének típusa lehetővé teszi az Intune számára az UEFI-(BIOS-) beállítások kezelését.

Az aktuálisan konfigurálható beállításokkal kapcsolatos további információkért lásd: a [szolgáltatások és beállítások alkalmazása az eszközökön a Microsoft Intune eszköz profiljainak használatával](../configuration/device-profiles.md).

Ez a funkció a Windows 10 RS5 (1809) és újabb verziókra vonatkozik az eszközök kijelölésekor.

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>PKCS-tanúsítványok macOS rendszerhez  <!-- 1333650                -->
A macOS rendszerű eszközökön a nyilvános kulcsú titkosítási szabványok (PKCS) tanúsítványainak teljes körű támogatását vesszük fel. A felhasználók a **Testreszabás tárgya** és a **tulajdonos alternatív neve**mezőkkel telepíthetik a felhasználói és az eszköz tanúsítványait. 

Egy új, **az összes alkalmazás elérésének engedélyezése**nevű beállítással is rendelkezünk. Ezzel a beállítással engedélyezheti, hogy az összes társított alkalmazás hozzáférhessen a titkos kulcshoz. További információ erről a beállításról: [konfigurációs profil referenciája](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) a Developer.Apple.com.

### <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Származtatott hitelesítő adatok a mobileszközök tanúsítványokkal való kiépítéséhez      <!--  1736036, 1736037, 1772050      --> 
Hozzáadjuk a származtatott hitelesítő adatok támogatását, amely támogatja a *National Institute of Standards and Technology (NIST) 800-157* szabványt a tanúsítványok eszközökre való központi telepítéséhez.  A származtatott hitelesítő adatok személyes személyazonosság-ellenőrzés (PIV) vagy közös hozzáférési kártya (CAC) használatára támaszkodnak, például intelligens kártyára. A felhasználók az intelligens kártyájuk használatával hitelesítik magukat a számítógépen. Ezután tanúsítványt kérnek a felügyelt eszközhöz a származtatott hitelesítőadat-szolgáltató által igényelt folyamat után.   

A származtatott hitelesítő adatoknak a tanúsítvány beszerzéséhez való használatának folyamata eltér a SCEP-vagy PKCS-tanúsítványokat használó folyamatoktól. Az eredmény azonban ugyanaz: olyan mobileszközök esetében, amelyek hitelesítési tanúsítványokkal rendelkeznek az alkalmazás-hitelesítéshez, a VPN-hez, a Wi-Fi-hez vagy a levelezéshez használt profilokhoz. További információ: [származtatott PIV hitelesítő adatok](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) a NCCOE-on. NIST.gov.

A származtatott hitelesítő adatok kezdeti kiadása támogatja az iOS rendszeren a Entrust Datacard, a közbenjáró és a DISA fajtatiszta-t. A későbbi kiadásokban a további platformok és származtatott hitelesítőadat-szolgáltatók is támogatottak lesznek.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Eszközök beléptetése

### <a name="specify-which-android-device-os-versions-enroll-through-the-work-profile-and-which-enroll-through-the-device-administrator----4350697---"></a>Itt adhatja meg, hogy az Android-eszközök operációs rendszerének mely verziói regisztrálják a munkahelyi profilt, és hogy az eszköz rendszergazdája hogyan regisztrálhat <!-- 4350697 -->
Az Intune-eszközök típusának korlátozásai segítségével megadhatja, hogy az eszköz operációs rendszerének verziója használja-e az Android Enterprise munkahelyi profil regisztrációját vagy az Android-eszközök rendszergazdai regisztrációját. Ehhez az Intune-ban válassza az **eszközök beléptetése**@no__t-**1 regisztrációs korlátozások** > **Létrehozás korlátozás** > **eszköz típusának korlátozása** > **platform beállításait**.

### <a name="edit-the-device-name-value-for-autopilot-devices----4816775---"></a>Az Autopilot-eszközök eszköznév értékének szerkesztése <!-- 4816775 -->
Az Azure AD-hez csatlakoztatott Autopilot-eszközökhöz az **eszköznév** értékét szerkesztheti:

1. Válassza **az Intune** > **eszközök beléptetése** > **Windows-beléptetés** > **Windows Autopilot** > **eszközök**elemet.
1. Válassza ki az eszközt.
1. A jobb oldali ablaktáblán módosítsa az **eszköz nevének** értékét.
1. Válassza a **Mentés** lehetőséget.

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

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Felhasználói felület frissítése a Windows 10-es frissítési gyűrűk létrehozásához és szerkesztéséhez  <!-- 4099089          -->   
A Microsoft a Windows 10-es frissítési körökhöz készült felhasználói felületi élmények létrehozása és szerkesztése során is frissülni fog. Az új felhasználói felület a következőket teszi:  
- Egyszerűsítse a meglévő felhasználói élményt egy panel varázsló stílusú formátumának használatával. Ez a felhasználói felületi frissítés megkerüli a panel terjeszkedését, amely megköveteli, hogy az informatikai szakemberek mélyre utazzanak.   
- Módosítsa a létrehozás folyamatát a hozzárendelések belefoglalásához.  
- Adjon hozzá egy összefoglaló lapot. Az összefoglalás tartalmazza a tulajdonságok megtekintésekor felhasználható összes beállítást, amikor egy frissítési kör létrehozására készül, és ha szerkeszt egy tulajdonságot. A szerkesztéskor az összefoglalás csak a szerkesztett tulajdonságok kategóriájában lévő elemeket sorolja fel.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Felhasználói felület frissítése iOS-szoftverfrissítések létrehozásához és szerkesztéséhez  <!-- 4099090        -->   
Az iOS-szoftverfrissítések az Intune-ban való létrehozásával és szerkesztésével kapcsolatos újdonságok a KEZELŐFELÜLETen jelennek meg. Az új felhasználói felület a következőket teszi:
- Egyszerűsítse a meglévő felhasználói élményt egy panel varázsló stílusú formátumának használatával. Ez a felhasználói felületi frissítés megkerüli a panel terjeszkedését, amely megköveteli, hogy az informatikai szakemberek mélyre utazzanak.  
- Hozzárendelések belefoglalása az iOS szoftverfrissítési házirend létrehozása folyamatba. 
- Tartalmazzon egy összefoglaló lapot az iOS-szoftverfrissítés házirendjében. Az összefoglalás magában foglalja az összes beállítást, amikor a tulajdonságok megtekintésekor a szabályzat létrehozásával és egy tulajdonság szerkesztésével készül. A szerkesztéskor az összefoglalás csak a szerkesztett tulajdonságok kategóriájában lévő elemeket sorolja fel.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>JAMF-felügyeletet igénylő macOS-felhasználói csoportok célzása <!-- 4061739 -->
A felhasználók meghatározott csoportjait megcélozhatja, hogy a macOS-eszközöket a JAMF kezelje. Ez a célzás lehetővé teszi, hogy a JAMF-megfelelőségi integrációt a macOS-eszközök egy részhalmazára alkalmazza, míg más eszközöket továbbra is az Intune kezel. A célzás azt is lehetővé teszi, hogy fokozatosan áttelepítse a felhasználók eszközeit egy mobileszköz-felügyeleti (MDM) rendszerről a másikra.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Új korlátozások a Windows-eszközök átnevezéséhez <!-- 3478938 -->
Az eszközök neveinek a következő szabályokat kell követniük:
- 15 karakter vagy kevesebb (63 bájtnál kisebb vagy azzal egyenlő, nem tartalmaz záró NULL értéket)
- Nincs null értékű vagy üres karakterlánc
- Engedélyezett ASCII: betűk (a-z, A-Z), számok (0-9) és kötőjelek
- Engedélyezett Unicode: karakterek > = 0x80, érvényes UTF8, leképezhető by IDN (RtlIdnToNameprepUnicode sikeres; lásd: RFC 3492)
- A nevek nem tartalmazhatnak számokat, és nem kezdődhet számmal.
- Nincs szóköz a névben
- Nem engedélyezett karakterek: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Szoftverfrissítések központi telepítése macOS-eszközökre <!-- 3194876 -->
A macOS-eszközök csoportjaira telepíthet szoftverfrissítéseket. Ez a szolgáltatás kritikus, belső vezérlőprogram, konfigurációs fájl és egyéb frissítéseket tartalmaz. A frissítéseket a következő eszköz beadásával küldheti el. Vagy kiválaszthat egy heti ütemtervet a frissítések telepítéséhez a beállított időszakokban vagy azokon kívül is. 

Ez a funkció segít abban az esetben, ha az eszközöket a szokásos munkaidőn kívüli vagy azon kívüli órákban szeretné frissíteni, amikor az ügyfélszolgálata teljesen munkatársa. Emellett részletes jelentést is kap az összes olyan macOS-eszközről, amelyen telepítve vannak a frissítések. Egy adott frissítés állapotának megjelenítéséhez az eszköz segítségével megtekintheti a jelentést.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Figyelés és hibaelhárítás

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Android-jelentés az eszközök – áttekintés oldalon <!-- 2984353  -->
Új jelentést fogunk hozzáadni az **eszközök áttekintés** lapjához. A jelentés azt jeleníti meg, hogy hány androidos eszköz van regisztrálva az egyes eszközkezelés megoldásokban. A diagramon a munkahelyi profil, a teljes körűen felügyelt, a dedikált és az eszköz-rendszergazda által regisztrált eszközök száma látható. 

A jelentés megtekintéséhez válassza az **Intune** > **eszközök**@no__t – 3 –**Áttekintés**lehetőséget.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>A Windows Autopilot üzembe helyezési jelentései <!-- 3856172  -->
Az új jelentések részletesen ismertetik a Windows Autopilot szolgáltatásban üzembe helyezett összes eszközt. Ezek az adatszolgáltatások az üzembe helyezés után 30 napig lesznek elérhetők. 

A jelentés megtekintéséhez nyissa meg az **Intune** > **eszközök beléptetése** > **monitor** >  Autopilot-alapú**üzembe helyezést**.

### <a name="updated-support-experience-------5012398------"></a>Frissített támogatási élmény   <!--  5012398    -->
A folyamatos fejlődés részeként frissíteni fogjuk a konzolon belüli támogatási élményt az Intune-ban.  Javítani fogjuk a konzolon belüli kereséseket és visszajelzéseket a gyakori problémák esetén, és a munkafolyamatot egyszerűsítjük, hogy kapcsolatba lépjenek a támogatási szolgálattal.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>További információ
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.
