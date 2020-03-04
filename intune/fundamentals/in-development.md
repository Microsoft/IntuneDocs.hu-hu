---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260231"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>Fejlesztés a Microsoft Intune – március 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Webes klipek átcélzása a Microsoft Edge-be iOS-/iPadOS-eszközökön<!-- 5455276 -->
Az iOS-/iPadOS-eszközökön rögzített webalkalmazásként feldolgozható webklipeket frissíteni kell. Az újonnan telepített webklipek a Microsoft Edge-ben nyílnak meg a Intune Managed Browser helyett, ha egy védett böngészőben kell megnyitni. A meglévő webklipeket újra meg kell célozni, hogy a Managed Browser helyett a Microsoft Edge-ben nyíljon meg.

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>macOS-és iOS-Céges portál frissítései<!-- 5779439, 5780234  -->
A macOS és az iOS Céges portál profil panelje frissülni fog a kijelentkezés gombbal. Emellett ez a frissítés a macOS Céges portál profil paneljének felhasználói felületének fejlesztéseit is tartalmazza. További információ a Céges portálről: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>A branding és a Testreszabás panel frissítései<!-- 5236032 -->
Frissíti az Intune panelt, amely a "branding and customization" elnevezésű, és a következő funkciókat tartalmazza:

- A panel átnevezése a **testreszabáshoz**.
- A beállítások szervezésének és kialakításának javítása.
- A beállítások szövegének és elemleírásának javítása.

Ha szeretné megkeresni ezeket a beállításokat az Intune-ban, keresse meg a [Microsoft Endpoint Manager felügyeleti központját](https://go.microsoft.com/fwlink/?linkid=2109431) , és válassza a **bérlői felügyelet** > **Testreszabás**lehetőséget. További információ a meglévő testreszabásról: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>Az iOS Microsoft Azure AD SSO-alkalmazás bővítményének konfigurálása<!-- 567534  -->
Az Microsoft Azure AD csapat fejleszt egy átirányítási egyszeri bejelentkezési (SSO) alkalmazás-bővítményt, amely lehetővé teszi, hogy az iOS és a iPadOS 13.0 + felhasználók zökkenőmentesen hozzáférjenek a Microsoft-alkalmazásokhoz és-webhelyekhez egyetlen bejelentkezéssel. Ha a HRE SSO-alkalmazás bővítménye megjelent, az egyszeri **bejelentkezéses** bővítményt a felügyeleti konzolon, minimális kattintással konfigurálhatja az **eszköz funkcióinak** > . 

Az iOS SSO-alkalmazás bővítményeivel, illetve az eszköz szolgáltatásainak konfigurálásával kapcsolatos további információkért lásd az [egyszeri bejelentkezés alkalmazás bővítményét](~/configuration/device-features-configure.md#single-sign-on-app-extension).

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>Céges portál az iOS-hez a tájképi üzemmód támogatásához<!--6048329  -->
A felhasználók regisztrálhatják az eszközeiket, megkereshetik az alkalmazásokat, és beszerezhetik az informatikai támogatási szolgálatot a választott képernyő tájolással. Az alkalmazás automatikusan felismeri és módosítja a képernyőket álló vagy fekvő üzemmódra, kivéve, ha a felhasználók álló módban zárolják a képernyőt. 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>Annak konfigurálása, hogy a beléptetés elérhető-e Céges portál Android és iOS rendszerhez<!-- 4260128 idready idstaged -->
Új beállítás érhető el, amely lehetővé teszi annak konfigurálását, hogy az eszközök regisztrációja az Android-és iOS-eszközökön a Céges portál elérhető-e, és kérés nélkül, vagy a felhasználók számára elérhetetlenné válik. Ha szeretné megkeresni ezeket a beállításokat az Intune-ban, keresse meg a [Microsoft Endpoint Manager felügyeleti központját](https://go.microsoft.com/fwlink/?linkid=2109431) , és válassza a **bérlői felügyelet** > **Testreszabás** >  > **eszközök regisztrációjának** **szerkesztése** lehetőséget. További információ a meglévő Céges portál testreszabásáról: [a Microsoft Intune céges portál alkalmazás konfigurálása](~/apps/company-portal-app.md).

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>Továbbfejlesztett bejelentkezési élmény a Céges portál Android rendszerhez<!-- 6103997  -->
Több bejelentkezési képernyő elrendezését frissítjük az androidos Céges portál alkalmazásban, hogy a felhasználói élmény modern, egyszerű és tiszta legyen.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Vezetékes hálózati eszközök konfigurációs profiljai macOS-eszközökhöz<!-- 3508686  -->
A rendszer elérhetővé teszi az új macOS-eszköz konfigurációs profilt, amely a vezetékes hálózatokat (az**eszköz konfigurációját** > **profilokat** > a **profil létrehozása** > **MacOS** platformon > **vezetékes hálózat** profil típusa) beállítására. Ezzel a szolgáltatással 802.1 x-profilokat hozhat létre a vezetékes hálózatok kezeléséhez, és ezeket a vezetékes hálózatokat a macOS-eszközökre is üzembe helyezheti.

A következőkre vonatkozik:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>A IKEv2 VPN-kapcsolatokkal rendelkező VPN-profilok mindig az iOS/iPadOS eszközökön használhatók <!-- 1947932  -->
IOS-/iPadOS-eszközökön létrehozhat egy IKEv2-kapcsolattal rendelkező VPN-profilt (az**eszköz konfigurációjának** > **profiljait** > **profil létrehozása** > **iOS/iPadOS** for platform > **VPN** a profil típusa). A jövőbeli frissítésekben a IKEv2-mel is konfigurálhatja az Always-on. Ha be van állítva, a IKEv2 VPN-profilok automatikusan csatlakoznak, és csatlakoztatva maradnak (vagy gyorsan újracsatlakozhatnak) a VPN-hez. A hálózat vagy az eszközök újraindítása esetén is csatlakoztatva marad.

IOS/iPadOS esetén a always-on VPN a IKEv2-profilokra korlátozódik.

Az aktuálisan konfigurálható IKEv2-beállítások megtekintéséhez lépjen a [VPN-beállítások hozzáadása iOS/iPadOS eszközökhöz a Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

A következőkre vonatkozik:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>Továbbfejlesztett felhasználói felületi élmény a konfigurációs profilok iOS/iPadOS és macOS rendszerű eszközökön való létrehozásakor<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
Ha iOS/iPadOS vagy macOS rendszerű eszközökhöz hoz létre profilt, a rendszer frissíti az Endpoint Management felügyeleti központban található felhasználói élményt. Ez a változás hatással van a következő eszköz-konfigurációs profilokra (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > **iOS** vagy **MacOS** for platform):

- Egyéni: iOS/iPadOS, macOS
- Eszköz szolgáltatásai: iOS/iPadOS, macOS
- Eszköz korlátozásai: iOS/iPadOS, macOS
- Endpoint Protection: macOS
- Bővítmények: macOS
- Preferencia fájl: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>Továbbfejlesztett felhasználói felületi élmény OEMConfig-konfigurációs profilok létrehozásakor androidos vállalati eszközökön<!-- 5568645   -->
Ha androidos vállalati eszközökhöz hoz létre vagy szerkeszt egy OEMConfig-profilt, a rendszer frissíti az Endpoint Management felügyeleti központ felületét. A frissített élmény áttekintést nyújt a konfigurált beállításokról. Ez a változás hatással van a OEMConfig-eszköz konfigurációs profiljára (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > **Android Enterprise** for platform > **OEMConfig** ).

Ez a funkció az alábbiakra vonatkozik:
- Vállalati Android 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>A vállalati alkalmazások megbízhatósági beállításai módosításának beállítása el lesz távolítva az iOS/iPadOS-eszközök korlátozási profiljaiból<!-- 6225131  -->
IOS-/iPadOS-eszközökön létre kell hoznia egy eszköz-korlátozási profilt (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > **iOS/iPadOS** a platform > **eszközre vonatkozó korlátozások** a profil típusa esetén). A **vállalati alkalmazások megbízhatósági beállításai módosítási** beállítást a rendszer eltávolítja az Apple-től, és eltávolítja az Intune-ból. Ha jelenleg ezt a beállítást használja egy profilban, az nem érinti a profilt, és addig marad a profilban, amíg új profilt nem hoz létre. Ez a beállítás az Intune összes jelentéskészítési szolgáltatásában is el lesz távolítva.

A következőkre vonatkozik:
- iOS/iPadOS

A korlátozható beállítások megjelenítéséhez nyissa meg az [iOS és a iPadOS beállításait a funkciók engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-ios.md).

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>Az eszköz konfigurációs profiljának beállításai és értékei frissülni fognak a Windows platformokon<!-- 4091122 -->
Ha Windows platformokhoz hoz létre konfigurációs profilokat (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > bármely **Windows** -lehetőség a platformhoz), egyes beállítások és azok értékei eltérnek a CSP-től, és zavaró lehet. A rendszer frissíti a beállítások nevét és azok értékeit.

A következőkre vonatkozik:

- Windows 10 és újabb rendszerű eszközök konfigurációs profiljai
- Windows holografikus for Business-eszköz konfigurációs profiljai
- Windows 8,1-eszköz konfigurációs profiljai
- Windows Phone-telefon 8,1-es eszköz konfigurációs profiljai

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>Továbbfejlesztett felhasználói felületi élmény az eszközök korlátozási profiljainak létrehozásakor Android-és androidos vállalati eszközökön<!-- 5841361 -->
Ha Android-vagy androidos vállalati eszközökhöz hoz létre profilt, a rendszer frissíti az Endpoint Management felügyeleti központban található felhasználói élményt. Ez a változás hatással van a következő eszköz-konfigurációs profilokra (**eszközök** > **konfigurációs profilok** > **profil létrehozása** > **Android-eszköz rendszergazdája** vagy **Android Enterprise** for platform):

- Eszközök korlátozásai: Android-eszköz rendszergazdája
- Eszköz korlátozásai: androidos vállalati eszköz tulajdonosa
- Eszközök korlátozásai: androidos vállalati munkahelyi profil

A konfigurálható eszközök korlátozásával kapcsolatos további információkért lásd: [Android-eszköz rendszergazdája](../configuration/device-restrictions-android.md) és [Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>Kötegek és kötegek törlése az OEMConfig-eszköz konfigurációs profiljaiban androidos vállalati eszközökön<!-- 5550355  -->
Az Android Enterprise rendszerű eszközökön OEMConfig-profilokat hozhat létre és frissíthet. A felhasználók törölhetik a csomagokat és a kötegeket az Intune-ban található **Configuration Designer** használatával.

A OEMConfig-profilokkal kapcsolatos további információkért lásd: [androidos vállalati eszközök használata és kezelése a OEMConfig-ben Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Ez a funkció az alábbiakra vonatkozik:
- Vállalati Android

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>A WPA és a WPA2 támogatása iOS-es vállalati Wi-Fi-profilokban<!--6215273   -->
Hozzáadjuk a *biztonsági típus* mezőt az [iOS rendszerhez készült vállalati Wi-Fi profilhoz](../configuration/wi-fi-settings-ios.md) (**eszközök** > **konfigurációs profilok** > **profil létrehozása** és az **iOS/iPadOS** a *platformhoz* , majd **Wi-Fi** a *profilhoz* ). Ez hasonló az iOS rendszerhez készült alapszintű Wi-Fi profilhoz elérhető beállításokhoz. Ez a módosítás lehetővé teszi, hogy új profilokat hozzon létre, amelyek a **WPA-Enterprise** vagy a **WPA/WPA2-Enterprise**biztonsági típust határozzák meg, majd megadhatja az *EAP-típus*kijelölését.

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>Új felhasználói élmény tanúsítvány-, e-mail-, VPN-és Wi-Fi-profilokhoz<!-- 5615208   -->
A [felhasználói élmény](../configuration/device-profile-create.md) frissítése a Endpoint Management felügyeleti központban (**eszközök** > **konfigurációs profilok** > **create Profile**) a következő profilok létrehozásához és módosításához. Az új felület ugyanazokat a beállításokat fogja megmutatni, mint korábban, de olyan varázsló-szerű élményt használ, amely nem igényel annyi vízszintes görgetést. Nem kell módosítania a meglévő konfigurációkat az új felülettel.
- Származtatott hitelesítő adat
- E-mail
- PKCS-tanúsítvány
- PKCS importált tanúsítvány
- SCEP-tanúsítvány
- Megbízható tanúsítvány
- VPN
- Wi-Fi

(**Eszközök** > **konfigurációs profilok** > **profil létrehozása**, majd a *Profil típusa* beállításnál válassza ki a fenti profilok bármelyikét.)

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>A Microsoft Defender ATP-alkalmazás konfigurálása macOS rendszerhez  <!-- 5520115  -->
Hamarosan konfigurálhatja a Microsoft Defender ATP alkalmazás [beállításait](../protect/endpoint-protection-macos.md) a MacOS-t futtató eszközökhöz az Endpoint Protection-eszköz konfigurációs profiljának részeként (**eszközök** > **konfigurációs profilok** > **profil létrehozása**, a *platformhoz*tartozó **MacOS** , majd az **Endpoint Protection** a *Profil típusa*esetén). A macOS-eszköz konfigurációjának nyolc beállítása lesz. 

A Defender ATP a macOS 10,13 (High Sierra) és újabb verziókban támogatott, és a [Microsoft DEFENDER ATP](../apps/apps-advanced-threat-protection-macos.md) alkalmazást a beállítás érvénybe léptetése *után* telepíteni kell az eszközre. A beállításokat az alkalmazás üzembe helyezése előtt el kell juttatni az eszközre. A macOS bétaverziója nem támogatott.

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>Új FileVault-beállítás macOS Endpoint Protection eszköz-konfigurációs házirendhez<!-- 5459801   -->
Új beállítást adunk hozzá a FileVault kategóriához a [macOS Endpoint Protection](../protect/endpoint-protection-macos.md) sablonban: helyreállítási kulcs elrejtése. (**Eszközök** > **konfigurációs profilok** > **profil létrehozása**, válassza a *platformon* a **MacOS** lehetőséget, majd a *Profil típusa* **végpont-védelmét** ). Ez a beállítás elrejti a felhasználó személyes kulcsát a FileVault 2 titkosítás során. Az eszköz felhasználója bármikor megtekintheti személyes helyreállítási kulcsát az iOS vállalati portál alkalmazásból vagy a titkosított macOS-eszköz céges portál webhelyéről. A személyes helyreállítási kulcs megtekintéséhez nyissa meg az eszköz adatait, és kattintson a *helyreállítási kulcs beolvasása*lehetőségre.

Ez a beállítás nem érhető el a korábban létrehozott házirendben. Ha ezt a beállítást szeretné használni, újra létre kell hoznia FileVault szabályzatokat. 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>Felhasználói felület frissítése a megfelelőségi szabályzat konfigurálásakor <!-- 3961639  -->
A megfelelőségi szabályzatok konfigurálásának felhasználói felületét a Microsoft Endpoint Managerben (**eszközök** > **megfelelőségi szabályzatok** > **szabályzatok** > **házirend létrehozása**) című témakör frissíti. Ekkor megjelenik egy új felhasználói élmény, amely ugyanazokat a beállításokat és részleteket tartalmazza, mint amelyeket korábban használt. Az új felhasználói felület egy varázslóhoz hasonló folyamatot követ a megfelelőségi szabályzat létrehozásához, és tartalmazza azt a lapot, amelyen hozzáadhat *hozzárendeléseket* a Szabályzathoz, majd egy *Összefoglaló* oldalt, ahol a szabályzat létrehozása előtt áttekintheti a konfigurációt. 

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>Kézbesítési optimalizálási ügynök konfigurálása Win32-alkalmazás tartalmának letöltésekor<!-- 5410945  -->
A kézbesítési optimalizálási ügynököt beállíthatja a Win32-alkalmazások tartalmának háttérbeli vagy előtéri módban való letöltéséhez a hozzárendelés alapján. A meglévő Win32-alkalmazások esetében a tartalom továbbra is letölthető háttér módban. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **konfigurációs profilok** > **profil létrehozása**lehetőséget. A **platformként**válassza a **Windows 10 és újabb** lehetőséget. A **Profil típusa**területen válassza a **kézbesítés optimalizálása**lehetőséget. A kézbesítési optimalizálással kapcsolatos további információkért lásd: [win32 app Management – kézbesítési optimalizálás](~/apps/apps-win32-app-management.md#delivery-optimization).


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Windows-eszközök elsődleges felhasználójának módosítása <!-- 3794742 -->
Megváltoztathatja az elsődleges felhasználót a Windows Hybrid és az Azure AD-hez csatlakoztatott eszközökhöz. Ehhez nyissa meg az **Intune** > **eszközök** > **minden eszköz** > válasszon egy eszközt > **Tulajdonságok** > **elsődleges felhasználó**. 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>Új Android-jelentés az Android-eszközökről – Áttekintés lap<!-- 5435435 -->
A Microsoft Endpoint Manager felügyeleti konzolját az Android-eszközök áttekintése oldalon fogjuk felvenni, amely megjeleníti, hogy hány androidos eszköz van regisztrálva az egyes eszközkezelés megoldásokban. Ez a diagram (például az Azure-konzolon már meglévő diagram) megjeleníti a munkahelyi profilt, a teljes körűen felügyelt, a dedikált és az eszköz rendszergazdája által beléptetett eszközök számát. A jelentés megtekintéséhez válassza az **eszközök** > **Android** > **Áttekintés**elemet.

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>PowerShell-parancsfájlok támogatása BYOD-eszközökhöz<!-- 1862833  -->
A PowerShell-parancsfájlok támogatják az Azure AD által regisztrált eszközöket az Intune-ban. A PowerShellről további információt a [Windows 10-es eszközökön futó PowerShell-parancsfájlok használata az Intune-ban](~/apps/intune-management-extension.md)című témakörben talál. Ez a funkció nem támogatja a Windows 10 Home Edition rendszert futtató eszközöket.

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>További adattárház-eszközök leltározási tulajdonságai<!-- 6125732  -->
A további eszközbeállítások tulajdonságai az Intune-adattárház használatával lesznek elérhetők. A következő tulajdonságok lesznek elérhetők az [eszközök](~/developer/intune-data-warehouse-collections.md#devices) gyűjteményén keresztül:
- Tárolókapacitás 
- Memória kapacitása
- Office 365-verzió
- Eszköz modellje

További információ az adattárházról: [Microsoft Intune adattárház API](~/developer/reports-nav-intune-data-warehouse.md).

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>Útmutató a felhasználóknak az Android-eszközök rendszergazdai felügyeletéről a munkahelyi profil kezeléséhez<!--5857738-->
Új megfelelőségi beállítást adunk ki az androidos eszközök rendszergazdai platformján. Ez a beállítás lehetővé teszi, hogy az eszköz nem megfelelő, ha az eszköz rendszergazdája felügyeli.

A nem megfelelő eszközökön az **eszközbeállítások frissítése** oldalon a felhasználók az **új eszközkezelés beállítására** vonatkozó üzenet jelenik meg. Ha a **feloldás** gombra koppintanak, a következők vezérlik:

1. Az eszköz-rendszergazda felügyeletének törlése
2. Regisztrálás a munkahelyi profil kezelése szolgáltatásban
3. A megfelelőségi problémák megoldása 
 
A Google az új Android-kiadásokban csökkenti az eszközkezelők támogatását, így a modern, gazdagabb és biztonságosabb eszközkezelés az Android Enterprise használatával történik.  Az Intune csak az Android 10 vagy újabb rendszerű, a Q2 CY2020-t futtató, az eszköz rendszergazdája által felügyelt Android-eszközök teljes támogatását biztosítja. Az Android 10 vagy újabb rendszert futtató, a Samsung által felügyelt eszközök nem lesznek teljesen felügyelve. Különösen az érintett eszközök nem kapják meg az új jelszóra vonatkozó követelményeket. További információkért tekintse meg ezt a [közleményt](#decreasing-support-for-android-device-administrator).

### <a name="retire-noncompliant-devices---1827291---"></a>Nem megfelelő eszközök kivonása<!-- 1827291 -->
Új opcionális megfelelőségi műveletet adunk hozzá egy nem megfelelő eszköz kivonásához (**eszközök** > **megfelelőségi szabályzatok** > **szabályzatok** > **házirend létrehozása** , majd az elérhető *műveletek* megtekintése a nem *megfelelőségi műveletek* lapon).  A nem megfelelő eszközök kivonása eltávolítja az összes vállalati adatforrást, és eltávolítja az eszközt az Intune-nal is. Ez a művelet akkor fut le, ha a beállított érték napokban van megadva. A minimális érték 30 nap.  Explicit rendszergazdai jóváhagyás szükséges az eszközök kivonásához a *nem megfelelő eszközök* kivonása szakasz használatával, ahol a rendszergazdák kihasználhatják az összes jogosult eszközt.

### <a name="new-information-in-device-details---5604099---"></a>Új információ az eszköz részleteiben<!-- 5604099 -->
Az eszközök **Áttekintés** lapján a következő információk jelennek meg:
- Tárolási kapacitás (az eszközön található fizikai tárterület mennyisége)
- Memória kapacitása (a fizikai memória mennyisége az eszközön)

### <a name="script-support-for-macos-devices---4280361----"></a>Parancsfájl-támogatás macOS-eszközökhöz<!-- 4280361  -->
A macOS-eszközökhöz parancsfájlokat adhat hozzá és telepíthet. Ez a támogatás kibővíti a macOS-eszközök natív MDM funkcióinak a macOS-eszközökön való használatának lehetőségeit. 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>Súgó és támogatás munkafolyamat-frissítés a további szolgáltatások támogatásához<!-- 5654170 -->
A Microsoft Endpoint Manager felügyeleti központban a Súgó és támogatás lapot frissítjük, így kiválaszthatja a használni kívánt felügyeleti típust, hogy jobban meg lehessen adni az adott támogatást (**Hibaelhárítás + támogatás** >  **Súgó és támogatás**). Ezzel a módosítással a következő felügyeleti típusok közül választhat:
- Configuration Manager (tartalmazza a Desktop Analytics szolgáltatást)
- Intune
- Megosztott kezelés

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Származtatott hitelesítő adatok támogatása androidos COBO-eszközökön<!--4839592-->
A származtatott hitelesítő adatokat az Android Enterprise teljes körűen felügyelt eszközökön is használhatja. A támogatás a Entrust Datacard, a közbenjáró és a DISA fajtatiszta hitelesítő adatok beolvasására is használható. Az alkalmazás-hitelesítés, a Wi-Fi, a VPN, az S/MIME-aláírás és/vagy az azt támogató alkalmazások esetében a rendszer származtatott hitelesítő adatokat használhat.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>A Microsoft Defender víruskereső és a Windows biztonsági élmény beállításainak kezelése a vírusvédelmi szabályzat használatával<!--6131401 -->
A *végpontok biztonsági* csomópontján megadhatja a **víruskereső**beállításait. Ha a szabályzatot a víruskeresőhöz konfigurálja, a Windows 10-es eszközökhöz tartozó beállításokat a következő két profillal adhatja meg:

- Microsoft Defender víruskereső: a felhőalapú védelem, a víruskeresők kizárása, a szervizelés, a vizsgálati beállítások és egyéb beállítások kezelése.
- Windows biztonsági élmény: felügyelheti, hogy a felhasználók hogyan használják a Windows biztonsági beállításokat az eszközökön. Beállíthatja, hogy a végfelhasználók hogyan tekinthetik meg a Microsoft Defender Security centert és a kapott értesítéseket.

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>Felhasználó személyes titkosított helyreállítási kulcsa<!-- 6273943 -->
Új Intune-szolgáltatás lesz elérhető, amely lehetővé teszi a felhasználók számára, hogy a Mac-eszközök személyes titkosított **FileVault** helyreállítási kulcsát az Android céges portál alkalmazáson vagy az Android Intune-alkalmazáson keresztül tudják beolvasni. A Céges portál alkalmazásban és az Intune-alkalmazásban is megjelenik egy hivatkozás, amely megnyitja a Chrome böngészőt a webes Céges portál, ahol a felhasználó láthatja a Mac-eszközök eléréséhez szükséges **FileVault** helyreállítási kulcsot. A titkosítással kapcsolatos további információkért lásd: az [eszközök titkosításának használata az Intune](~/protect/encrypt-devices.md)-nal.

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>A macOS-eszközök adatvédelmi beállításai<!-- 2934232 --> 
A macOS Catalina 10,15 kiadásával az Apple új biztonsági és adatvédelmi fejlesztéseket adott hozzá. Alapértelmezés szerint az alkalmazások és a folyamatok felhasználói engedély nélkül nem férhetnek hozzá az adott információhoz. Ha a felhasználók nem biztosítanak beleegyezik, előfordulhat, hogy az alkalmazások és a folyamatok nem fognak működni. Az Intune olyan beállítások támogatását adja hozzá, amelyek lehetővé teszik a rendszergazdák számára, hogy a végfelhasználók nevében engedélyezzék vagy engedélyezzék az Adathozzáférési engedélyt a macOS 10,14-es vagy újabb verzióját futtató eszközökön. Ezek a beállítások biztosítják, hogy az alkalmazások és a folyamatok továbbra is megfelelően működjenek, és csökkentsék a végfelhasználók által felmerülő kérések számát. 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>Frissített felhasználói felületi szöveg és címkék a Windows 10-es Endpoint Protection-profil beállításaihoz<!-- 5983747 -->
A Windows 10-es eszközök konfigurációs profiljaiként konfigurált különféle beállítások szövegét frissítjük, hogy könnyebben megismerhető legyen a használni kívánt beállítások és eredmények. 

A frissíteni kívánt beállítások közé tartozik a Windows 10-es eszközök konfigurációs profiljai a következőhöz: 
- [Eszközökre vonatkozó korlátozások](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Microsoft Defender Antivirus  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Microsoft Defender víruskereső

Az Intune által támogatott beállítások nem változnak. Ez csak a felhasználói felület szövegének frissítése a Microsoft Endpoint Management felügyeleti központban. 


<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>További információ
A legutóbbi fejleményekről a [Microsoft Intune újdonságai](whats-new.md)című témakörben olvashat bővebben.



