---
title: A Microsoft Intune újdonságai a korábbi hónapokból – Azure | Microsoft Docs
titleSuffix: ''
description: Az Intune újdonságai oldalán korábban megjelenő információkat olvashatja
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/8/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 327e0d56400a2aac545d1bae92279e242aa2006a
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585224"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>A Microsoft Intune újdonságai – korábbi hónapok

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

<!-- ########################## -->
## <a name="december-2018"></a>December 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="updates-for-application-transport-security----748318---"></a>Az Application Transport Security frissítései <!-- 748318 -->

A Microsoft Intune a Transport Layer Security (TLS) 1.2 + verzióját támogatja a legjobb minőségű titkosítás biztosításához, hogy az Intune alapértelmezés szerint biztonságosabb legyen, és más Microsoft-szolgáltatásokhoz, például Microsoft Office 365-hez legyen igazítva. Ezen követelmény kielégítése érdekében az iOS és a macOS rendszerű céges portálok érvényesítik az Apple frissített Application Transport Security (ATS) követelményeit, amelyek a TLS 1.2 +-t is igénylik. Az ATS szigorúbb biztonsági előírásokat érvényesít az alkalmazások közötti minden olyan kommunikációra, amely HTTPS-protokollon keresztül történik. Ez a változás az Intune-ügyfeleket az iOS-és macOS-Céges portál alkalmazások használatával befolyásolja. További információt az [Intune támogatási blogjában](https://aka.ms/compportalats)talál.

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Az Intune app SDK a 256 bites titkosítási kulcsokat fogja támogatni <!-- 1832174 -->
Az Androidhoz készült Intune app SDK mostantól 256 bites titkosítási kulcsokat használ, ha a titkosítást az alkalmazás-védelmi szabályzatok engedélyezik. Az SDK továbbra is támogatást nyújt a 128 bites kulcsokhoz a régebbi SDK-verziót használó tartalommal és alkalmazásokkal való kompatibilitás érdekében.

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>A Microsoft automatikus frissítési verziójának 4.5.0 szükséges a macOS-eszközökhöz <!-- 3503442 -->
A Céges portál és más Office-alkalmazások frissítéseinek folytatásához az Intune által felügyelt macOS-eszközöknek frissíteniük kell a Microsoft automatikus frissítési 4.5.0. Előfordulhat, hogy a felhasználók már rendelkeznek ezzel a verzióval az Office-alkalmazásokhoz.

### <a name="device-management"></a>Eszközkezelés

#### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Az Intune macOS 10,12-es vagy újabb verzióját igényli <!-- 2827778 -->
Az Intune mostantól a macOS 10,12-es vagy újabb verzióját igényli. A korábbi macOS-verziókat használó eszközök nem használhatják a Céges portál az Intune-ba való regisztráláshoz. Ha támogatási támogatást és új funkciókat szeretne kapni, a felhasználóknak frissíteniük kell az eszközt macOS 10,12 vagy újabb verzióra, és frissíteniük kell a Céges portált a legújabb verzióra.

<!-- ########################## -->
## <a name="november-2018"></a>November 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Alkalmazások eltávolítása a vállalat által birtokolt felügyelt iOS-eszközökön <!-- 1281677 -->
Bármely alkalmazást eltávolíthat a vállalat által birtokolt felügyelt iOS-eszközökön. Ha az **Eltávolítás** hozzárendelési típussal megcélozza a felhasználó- vagy eszközcsoportokat, akkor bármilyen alkalmazást el tud távolítani. Személyes és nem felügyelt iOS-eszközök esetében a továbbiakban csak az Intune használatával telepített alkalmazásokat tudja majd eltávolítani.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Az Intune Win32-alkalmazás tartalmának letöltése <!-- 2617320 -->
A Windows 10 RS3 és újabb rendszerű ügyfelek letöltik az Intune Win32-alkalmazás tartalmát egy kézbesítési optimalizálási összetevő használatával a Windows 10-ügyfélen. A kézbesítési optimalizálás a társ-társ funkciókat biztosítja, amelyet alapértelmezés szerint be kell kapcsolni. A kézbesítési optimalizálás jelenleg a csoportházirend használatával konfigurálható. További információ: [a Windows 10 kézbesítési optimalizálása](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization).

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Végfelhasználói eszköz és alkalmazás tartalmának menüje <!-- 2771453 -->
A végfelhasználók mostantól használhatják a helyi menüt az eszközön és az alkalmazásokban olyan gyakori műveletek elindításához, mint például az eszköz átnevezése vagy a megfelelőség ellenőrzése.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Egyéni háttér beállítása a felügyelt kezdőképernyő alkalmazásban  <!-- 3041945 -->
Olyan beállítást adunk hozzá, amely lehetővé teszi a felügyelt kezdőképernyő alkalmazás háttérképének testreszabását androidos nagyvállalati, többalkalmazásos és kioszk módú eszközökön.  **Egyéni URL-háttér** konfigurálásához nyissa meg az Azure portalon az Intune > Eszközkonfiguráció elemet. Jelöljön ki egy jelenlegi eszközkonfigurációs profilt, vagy hozzon létre újat kioszkbeállításainak szerkesztéséhez.
A kioszk beállításainak megtekintéséhez tekintse meg az [androidos vállalati eszközök korlátozásait](../configuration/device-restrictions-android-for-work.md)ismertető témakört.

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Alkalmazás-védelmi szabályzat-hozzárendelés mentése és alkalmazása <!-- 3104570 -->
Most már jobban kézben tarthatja az [alkalmazás-védelmi szabályzat-hozzárendeléseket](../apps/app-protection-policies.md#assign-a-windows-10-policy-to-users). Amikor kijelöli a *hozzárendeléseket* egy házirend hozzárendeléseinek beállításához vagy szerkesztéséhez, a módosítás előtt **mentenie** kell a konfigurációt. Az **elvet** lehetőséggel törölheti az összes olyan módosítást, amelyet a belefoglalási vagy kizárási listához tartozó módosítások mentése nélkül el szeretne végezni.  A Mentés vagy az Elvetés megkövetelésével csak a kívánt felhasználók kapnak egy alkalmazás-védelmi szabályzatot.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Új Microsoft Edge böngésző-beállítások Windows 10 és újabb rendszerekhez <!-- 3174639 -->
Ez a frissítés új beállításokat tartalmaz, amelyek segítségével szabályozhatja és kezelheti az eszközökön futó Microsoft Edge böngészőt. A beállítások listáját lásd: [eszközök korlátozásai a Windows 10 rendszerhez (és újabb verziók)](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Új alkalmazások támogatása az App Protection-szabályzatokkal <!-- 3330037 -->
Mostantól a következő alkalmazások kezelhetők az [Intune app Protection-szabályzatokkal](../apps/app-protection-policies.md):
- Stream (iOS)
- TEENDŐk (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Az alkalmazás-védelmi házirendek használatával biztosíthatja a vállalati adatok védelmét és szabályozhatja az alkalmazások adatátvitelét, például az Intune-szabályzat által felügyelt egyéb alkalmazásokhoz. Megjegyzés: Ha a folyamat még nem látható a konzolon, akkor a folyamat létrehozásakor vagy szerkesztésekor, illetve az alkalmazás-védelmi szabályzatok használatakor is felveszi a folyamatot. Ehhez használja a **+ További alkalmazások** lehetőséget, majd adja meg a flow *alkalmazás azonosítóját* a beviteli mezőben. Android esetén a *com. microsoft. flow*és az iOS használata a *com. microsoft. procsimo*.


### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>IOS 12 OAuth támogatása iOS-es e-mail-profilokban <!--2155106 -->
Az Intune iOS e-mail-profiljai támogatják az iOS 12-es nyílt engedélyezést (OAuth). Ennek a funkciónak a megtekintéséhez hozzon létre egy új profilt (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **iOS** a platformhoz > **E-mail** a profiltípushoz), vagy frissítsen egy létező iOS-es e-mail-profilt. Ha engedélyezi az OAuth-hitelesítést egy olyan profilban, amely már üzembe van helyezve a felhasználóknál, akkor a felhasználóknak újra el kell végezniük a hitelesítést, és le kell ismét tölteniük az e-mailjeiket.

Az [iOS-es e-mail-profilok](../configuration/email-settings-ios.md) szakaszban további információt talál az OAuth e-mail-profilban való használatáról.

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Hálózati Access Control (NAC) támogatása az iOS-hez készült Citrix SSO-hoz <!-- 3259404 -->
A Citrix olyan frissítést adott ki a Citrix Gateway számára, amely engedélyezi a hálózati Access Control (NAC) számára az iOS rendszerhez készült Citrix SSO használatát az Intune-ban. A ben engedélyezheti, hogy az Intune-ban található VPN-profilban szerepeljen az eszköz azonosítója, majd ezt a profilt az iOS-eszközökre küldje el. A funkció használatához telepítenie kell a legújabb frissítést a Citrix Gateway-hez.

A [VPN-beállítások konfigurálása iOS-eszközökön](../configuration/vpn-settings-ios.md#base-vpn-settings) további információkat nyújt a NAC használatáról, beleértve néhány további követelményt is. 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>az iOS-és macOS-verziók száma és a létrehozási számok láthatók <!-- 1892471 -->
Az **Eszközmegfelelőség** > **Eszközmegfelelőség** megjeleníti az iOS és macOS operációs rendszerek verzióit, amelyek elérhetők a megfelelőségi szabályzatokkal. Ez a frissítés tartalmazza a Build számát, amely mindkét platformhoz konfigurálható.
A biztonsági frissítések megjelenésekor az Apple általában megtartja a verziószámot, de a buildszám változik. A megfelelőségi szabályzat buildszámának segítségével könnyen ellenőrizheti, hogy telepítve van-e a biztonsági frissítés.
A szolgáltatás használatához lásd: [iOS](../protect/compliance-policy-create-ios.md#device-health) -és [MacOS](../protect/compliance-policy-create-mac-os.md#device-properties) -megfelelőségi szabályzatok.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>A frissítési körök cseréje a Windows 10 és újabb rendszerekre vonatkozó kézbesítési optimalizálási beállításokkal történik <!-- 2753807 -->
A kézbesítési optimalizálás egy új konfigurációs profil a Windows 10 és újabb rendszerekhez. Ez a funkció egyszerűbbé teszi a szoftverfrissítések a szervezeten belüli eszközökre való továbbítását. Ez a frissítés azt is lehetővé teszi, hogy az új és a meglévő frissítési körök beállításait egy konfigurációs profil használatával adja meg.
A kézbesítési optimalizálás konfigurációs profiljának konfigurálásához lásd: [Windows 10 (és újabb) kézbesítési optimalizálási beállítások](../configuration/delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Az iOS-és macOS-eszközökhöz hozzáadott új eszköz-korlátozási beállítások <!-- 2827760 -->
Ez a frissítés az iOS 12-es verzióban kiadott iOS-és macOS-eszközök új beállításait tartalmazza:

**iOS-beállítások**: 
- Általános: alkalmazások eltávolításának letiltása (csak felügyelt eszköz esetén)
- Általános: USB-korlátozott üzemmód letiltása (csak felügyelt eszköz esetén)
- Általános: az automatikus dátum és idő kényszerítése (csak felügyelt eszköz esetén)
- Password (jelszó): jelszó automatikus kitöltésének tiltása (csak felügyelt eszköz esetén)
- Password (jelszó): a jelszó-közelségi kérelmek letiltása (csak felügyelt eszköz esetén)
- Password (jelszó): a jelszó megosztásának letiltása (csak felügyelt eszköz esetén)

**MacOS-beállítások**: 
- Password (jelszó): a jelszó automatikus kitöltésének letiltása
- Password (jelszó): a jelszó-közelségi kérelmek letiltása
- Password (jelszó): a jelszó megosztásának letiltása

További információ ezekről a beállításokról: [iOS](../configuration/device-restrictions-ios.md) -és [MacOS](../configuration/device-restrictions-macos.md) -eszközök korlátozási beállításai.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>A hibrid Azure Active Directory csatlakoztatott eszközök Autopilot-támogatása (előzetes verzió) <!-- 1048100-->
Az Autopilot segítségével mostantól hibrid, Azure Active Directory-hoz csatlakoztatott eszközöket állíthat be. A hibrid Autopilot funkció használatához az eszközöket csatlakoztatni kell a szervezet hálózatához. További információt a [Deploy hybrid Azure AD joined devices using Intune and Windows Autopilot](../enrollment/windows-autopilot-hybrid.md) (Hibrid, Azure AD-hez csatlakoztatott eszközök üzembe helyezése az Intune és a Windows Autopilot használatával) című cikkben talál.
Ez a funkció néhány napon belül kerül bevezetésre a felhasználók között. Előfordulhat tehát, hogy Ön nem tudja követni ezeket a lépéseket addig, amíg a fiókjában is meg nem jelenik ez az újítás.

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Válassza ki a regisztráció állapota lapon nyomon követett alkalmazásokat<!-- 2531007 -->
Kiválaszthatja, hogy mely alkalmazások legyenek követve a regisztráció állapota lapon. Amíg ezek az alkalmazások nem települnek, a felhasználó nem használhatja az eszközt. További információ: [regisztráció állapotának beállítása lap](../enrollment/windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Autopilot-eszköz keresése sorozatszám alapján <!--2595788 -->
Mostantól sorozatszám alapján is megkeresheti az Autopilot-eszközöket. Ehhez válassza az eszközök **beléptetése**  >  a**Windows-beléptetés**  > **eszközök** > írja be a sorozatszámot a **Keresés sorozatszám szerint** mezőben > nyomja le az ENTER billentyűt.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Az Office-ProPlus telepítésének nyomon követése <!--2620217 -->
A felhasználók a [regisztráció állapota lapon](../enrollment/windows-enrollment-status.md)követhetik nyomon az [Office-ProPlus](../apps/apps-add-office365.md) telepítési folyamatát. További információ: [regisztráció állapotának beállítása lap](../enrollment/windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Lejáró VPP-token vagy Céges portál alacsonyan futó licenc riasztásai <!-- 2237572 -->
Ha mennyiségi vásárlási programot (VPP) használ a Céges portál előzetes kiépítéséhez a DEP-regisztráció során, akkor az Intune riasztást küld, ha a VPP-token hamarosan lejár, és ha a Céges portál-licencek alacsonyan futnak.

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>macOS Készülékregisztrációs program támogatás az Apple School Manager-fiókokhoz <!--3006133 -->
Az Intune mostantól támogatja a Készülékregisztrációs program használatát macOS-eszközökön az Apple School Manager-fiókokhoz.  További információ: [MacOS-eszközök automatikus regisztrálása az Apple School Managerrel vagy Készülékregisztrációs program](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="new-intune-device-subscription-sku---3312071--"></a>Új Intune-eszköz előfizetési SKU <!--3312071-->
A vállalatok számára az eszközkezelés költségeinek csökkentéséhez már elérhető egy új, eszközalapú előfizetési termékváltozat. Ennek az Intune-beli eszköz-termékváltozatnak a licencelése eszközönként történik, havi elszámolással. Az ár a licencprogramtól függően változik. Közvetlenül a Microsoft 365 felügyeleti központban érhető el, valamint a [nagyvállalati szerződés](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), a [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA), a [Microsoft Open szerződések](https://partner.microsoft.com/licensing/licensing-agreements)és a [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) segítségével. .

### <a name="device-management"></a>Eszközkezelés

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>A kioszk mód ideiglenes felfüggesztése Android-eszközökön a módosítások elvégzéséhez <!-- 3041935 -->
Ha többalkalmazásos kioszkmódban használ Android-eszközöket, előfordulhat, hogy a rendszergazdáknak módosításokat kell végrehajtaniuk az eszközön. Ez a frissítés olyan új többalkalmazásos kioszk-beállításokat tartalmaz, amelyek lehetővé teszik a rendszergazda számára, hogy PIN-kód használatával ideiglenesen felfüggessze a kioszk-üzemmódot, és hozzáférést kapjon a teljes eszközhöz.
A kioszk beállításainak megtekintéséhez tekintse meg az [androidos vállalati eszközök korlátozásait](../configuration/device-restrictions-android-for-work.md)ismertető témakört.

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Virtuális Home gomb engedélyezése androidos vállalati kioszk-eszközökön  <!-- 3042021 -->
Az új beállítás segítségével a felhasználók az eszközön lévő többfunkciós gombra való koppintással válthatnak a többalkalmazásos kioszkeszközökön található Managed Home Screen alkalmazás és az egyéb hozzárendelt alkalmazások között. Ez a beállítás igen hasznosnak bizonyul olyan esetekben, amikor a felhasználó kioszkalkalmazása nem reagál megfelelően a „vissza” gomb megnyomására. Ezt a beállítást Ön konfigurálni tudja majd az egyetlen célra használható céges Android-eszközökön. A **Virtuális kezdőképernyő gomb** be- és kikapcsolásához válassza az Azure portalon az Intune > Eszközök konfigurálása elemet. Jelöljön ki egy jelenlegi eszközkonfigurációs profilt, vagy hozzon létre újat kioszkbeállításainak szerkesztéséhez.
A kioszk beállításainak megtekintéséhez tekintse meg az [androidos vállalati eszközök korlátozásait](../configuration/device-restrictions-android-for-work.md)ismertető témakört.




<!-- ########################## -->
## <a name="october-2018"></a>Október 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Hozzáférés a Key profil tulajdonságaihoz a vállalati portál alkalmazás használatával <!-- 772203 -->
A végfelhasználók mostantól a Céges portál alkalmazással hozzáférhetnek a legfontosabb fióktulajdonságokhoz és -műveletekhez, például a jelszó-visszaállításhoz. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>a harmadik féltől származó billentyűzetek az iOS-alkalmazások beállításai által blokkolva <!-- 1248481 -->
Az Intune-rendszergazdák az iOS-es eszközökön letilthatják a harmadik féltől származó billentyűzeteket, ha azok a szabályzat által védett alkalmazásokon hozzáférnek a céges adatokhoz. Ha az alkalmazásvédelmi szabályzat (APP) a harmadik félhez tartozó billentyűzetek letiltására van beállítva, az eszköz használója üzenetet kap, amikor először fér hozzá ilyen billentyűzettel a céges adatokhoz. A natív billentyűzeten kívül minden más lehetőség le van tiltva, és a felhasználók nem láthatják ezeket. A felhasználók csak egyszer látják az üzenetet. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Az Intune-alkalmazások felhasználói fiókhoz való hozzáférése felügyelt Android-és iOS-eszközökön <!-- 1248496 -->
A Microsoft Intune rendszergazdájaként szabályozhatja, hogy melyik felhasználói fiókok legyenek hozzáadva a Microsoft Office-alkalmazásokhoz a felügyelt eszközökön. A hozzáférést korlátozhatja csak a szervezeti felhasználói fiókokra, és blokkolhatja a személyes fiókok használatát a regisztrált eszközökön. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Az Outlook iOS-és Android-alkalmazás konfigurációs szabályzata <!--1828527 -->
Mostantól létrehozhat egy Outlook iOS és Android alkalmazáskonfigurációs szabályzatot iOS és Android rendszerekhez az olyan helyszíni felhasználók számára, akik az alapszintű hitelesítést és az ActiveSync protokollt használják. További konfigurálási beállítások lesznek hozzáadva az engedélyezésüket követően az iOS és Android rendszerre készült Outlookhoz.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus nyelvi csomagok <!-- 1833450 -->
Az Intune rendszergazdájaként további nyelveket helyezhet üzembe az Intune által felügyelt Office 365 Pro Plus alkalmazások számára. Az elérhető nyelvek listája tartalmazza a nyelvi csomag **Típusát** (alap, részleges vagy nyelvi ellenőrzési) is. Az Azure Portalon válassza a **Microsoft Intune** > **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** lehetőséget. Az **Alkalmazás hozzáadása** panelen, az **Alkalmazástípusok** listáján, válassza az **Office 365 csomag** alatti **Windows 10** lehetőséget. Az **Alkalmazáscsomag beállításai** panelen válassza a **Nyelvek** lehetőséget.

#### <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows rendszerű üzletági (LOB) alkalmazások fájlkiterjesztés <!-- 1884873 -->
A Windows LOB-alkalmazások fájlkiterjesztés a következőt tartalmazza: *. msi*, *. Appx*, *. appxbundle*, *. msix*és *. msixbundle*. Az alkalmazásokat az **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** lehetőséggel adhatja hozzá a Microsoft Intune-hoz. Megjelenik az **Alkalmazás hozzáadása** panel, ahol kiválaszthatja az **Alkalmazás típusát**. Windowsos üzletági alkalmazásokhoz válassza az **Üzletági alkalmazás** lehetőséget az alkalmazás típusa területen, válassza az **Alkalmazáscsomag-fájl** elemet, majd adjon meg egy megfelelő kiterjesztésű telepítőfájlt.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Windows 10-es alkalmazások üzembe helyezése az Intune-nal <!-- 2309001 -->
Az üzleti alkalmazások és a Vállalati Microsoft Áruházbeli alkalmazások meglévő támogatására építve a rendszergazdák a szervezetük legtöbb meglévő alkalmazását az Intune segítségével telepíthetik a végfelhasználók Windows 10 rendszerű eszközeire. A rendszergazdák a Windows 10-es felhasználók számára több különböző formátumban adhatják hozzá, telepíthetik vagy eltávolíthatják az alkalmazásokat, például MSI-k, setup.exe fájlok vagy az MSP használatával. Az Intune a letöltést és a telepítést megelőzően kiértékeli a követelményszabályokat és a Windows 10 Műveletközpontján keresztül értesíti a végfelhasználókat a telepítés állapotáról vagy az újraindítási követelményekről. Ez a funkció gyakorlatilag lehetővé teszi, hogy az ez iránt érdeklődő szervezetek az Intune-ba és a felhőbe helyezzék át e műveleteiket. Ez a funkció jelenleg nyilvános előzetes verzióban érhető el, és várhatóan a következő néhány hónap során jelentős új képességekkel fog bővülni. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>A webes adatvédelemre vonatkozó szabályzat (alkalmazás) beállításai <!-- 2662995 -->
A webes tartalmakra vonatkozó APP szabályzatok beállításait az Android- és iOS-eszközökön is frissítjük, hogy hatékonyabban kezelhetők legyenek a webes http- és https-hivatkozások, valamint az univerzális iOS-hivatkozásokon és Android-alkalmazáshivatkozásokon keresztüli adatátvitel. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Végfelhasználói eszköz és alkalmazás tartalmának menüje <!-- 2771453 -->
A végfelhasználók mostantól az eszközök és alkalmazások helyi menüjéből is elvégezhetnek olyan gyakori műveleteket, mint például egy eszköz átnevezése vagy a megfelelőség ellenőrzése. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>A Windows Céges portálon használható billentyűparancsok <!-- 2771518 -->
A végfelhasználók mostantól az eszközökre és alkalmazásokra vonatkozó műveleteket a Windows rendszerű céges portál billentyűparancsaival is aktiválhatják.

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Nem biometrikus PIN-kód megkövetelése megadott időkorlát után <!-- 1506985 -->
Mivel az Intune nem biometrikus PIN-kód megadását írja elő a rendszergazda által meghatározott időtúllépés után, ezzel magasabb szintű védelmet biztosít a mobilalkalmazás-kezelést (MAM) engedélyező alkalmazások számára azáltal, hogy korlátozza a biometrikus azonosításnak a céges adatokhoz való hozzáférés érdekében történő használatát. A beállítások APP/MAM szolgáltatást engedélyező alkalmazásokhoz való hozzáférésre használt Touch ID (iOS), Face ID (iOS), Android Biometric és egyéb jövőbeli biometrikus hitelesítési módszereket alkalmazó felhasználókra vonatkoznak. E beállítások segítségével az Intune-rendszergazdák részletesen szabályozhatják a felhasználók hozzáférését, így megelőzhetik azokat az eseteket, amikor a több ujjlenyomatos vagy egyéb biometrikus hozzáférési módszert használó eszközről céges adatok juthatnak illetéktelen felhasználók birtokába. Az Azure Portalon nyissa meg a **Microsoft Intune** oldalt. Válassza az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** > **Szabályzat hozzáadása** > **Beállítások** lehetőséget. Az adott beállításokhoz keresse meg a **Hozzáférés** lehetőséget. A hozzáférésre vonatkozó beállításokról az [iOS-beállítások](../apps/app-protection-policy-settings-ios.md#access-requirements) és az [Android-beállítások](../apps/app-protection-policy-settings-android.md#access-requirements) oldalon tájékozódhat.

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Intune-alkalmazások adatátviteli beállításai iOS-MDM regisztrált eszközökön <!-- 2244713 -->
Elkülönítheti az Intune APP adatátviteli beállítások iOS rendszerű, MDM-et engedélyező eszközökön való szabályozását a regisztrált felhasználók személyazonosságának megadásától, amely Egyszerű felhasználónévként (UPN) is ismert. Az IntuneMAMUPN-t nem használó rendszergazdák nem tapasztalnak majd működésbeli változást. Ha ez a funkció elérhetővé válik, a regisztrált eszközök adatátviteli viselkedésének vezérléséhez IntuneMAMUPN-t használó rendszergazdáknak át kell tekinteniük az új beállításokat, és szükség szerint frissíteniük kell APP-beállításaikat.

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32-alkalmazások <!-- 2617325 -->
Konfigurálhatja a Win32-alkalmazások telepítését az egyes felhasználók felhasználói környezetében, de választhatja azt is, hogy az eszköz összes felhasználója esetében telepíti az alkalmazást.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32-alkalmazások és PowerShell-parancsfájlok <!-- 2617330 -->
A végfelhasználóknak nem kell többé bejelentkezniük az eszközön a Win32-alkalmazások telepítéséhez és a PowerShell-parancsfájlok végrehajtásához. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Ügyfél-alkalmazás telepítésének hibaelhárítása <!-- 1363711 -->
Az ügyfélalkalmazások telepítésével kapcsolatban felmerülő hibák elhárításához a **Hibaelhárítás** panelen található **Alkalmazástelepítés** címkével ellátott oszlopban talál segítséget. A **Hibaelhárítás** panel megtekintéséhez válassza az Intune-portálon a **Súgó és támogatás** részben található **Hibaelhárítás** elemet.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>DNS-utótagok létrehozása a VPN-konfigurációs profilokban a Windows 10 rendszerű eszközökön<!-- 1333668 -->
Egy VPN-eszközregisztrációs profil létrehozásakor (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **Windows 10 és újabb** platform > **VPN** profiltípus) meg kell adni néhány DNS-beállítást. Ezzel a frissítéssel egyszerre több **DNS-utótag** is megadható az Intune-ban. A DNS-utótagok használatakor a rendszer a hálózati erőforrások rövid nevére keres rá a teljes tartománynév (FQDN) helyett. Ezzel a frissítéssel a DNS-utótagok sorrendje is módosítható az Intune-ban.
A jelenlegi DNS-beállításokat [a Windows 10 VPN-beállításaival](../configuration/vpn-settings-windows-10.md#dns-settings) foglalkozó cikk ismerteti.
Érvényes: Windows 10 rendszerű eszközökre

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>A always-on VPN for Android vállalati munkahelyi profilok támogatása <!-- 1333705 -->
Ez a frissítés lehetővé teszi a mindig bekapcsolt VPN-kapcsolatok használatát a felügyelt munkahelyi profillal rendelkező Android Enterprise rendszerű eszközökön. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal újraindítható, ha a felhasználó feloldja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. A kapcsolat „zárolt” módba is állítható, amely blokkol minden hálózati forgalmat, amíg a VPN-kapcsolat aktív.
A Mindig bekapcsolt VPN a következő helyen engedélyezhető: **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **Android Enterprise** platform > **Eszközkorlátozások** > **Kapcsolatok** lehetőséget.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>SCEP-tanúsítványok kiadása felhasználó nélküli eszközökhöz <!-- 1744554 -->
A tanúsítványok jelenleg felhasználók részére vannak kiállítva. Ezzel a frissítéssel az SCEP-tanúsítványok már eszközök, köztük felhasználó nélküli eszközök, például kioszkok részére is kiállíthatók (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **Windows 10 vagy újabb** platform > **SCEP-tanúsítvány** elemet). Egyéb frissítések:
- Az SCEP-profil **Tulajdonos** tulajdonsága mostantól egy egyéni szövegmező, amely új változókat is tartalmazhat. 
- Az SCEP-profilokban a **Tulajdonos alternatív neve (SAN)** tulajdonság mostantól tábla formátumú, és új változókat is tartalmazhat. A táblában a rendszergazdák megadhatnak attribútumokat, és a hozzájuk tartozó értéket egy egyéni szövegmezőben tölthetik ki. Az SAN a következő attribútumokat támogatja: 
  - DNS
  - E-mail cím
  - UPN

  Ezek az új változók statikus szöveggel adhatók meg egy egyéni szövegmezőben. Például a DNS-attribútumok a következő formátumban adhatók meg: `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > A kapcsos zárójel, pontosvessző és függőleges vonal szimbólumok „ { } ; | ” nem használhatók az SAN statikus szövegében. A kapcsos zárójeleknek mindig az új eszköztanúsítvány valamely változóját kell közrefogniuk ahhoz, hogy az elfogadható legyen mint `Subject` vagy `Subject alternative name`. 

Új változók az eszköztanúsítványokban:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
> - A `{{FullyQualifiedDomainName}}` csak a Windows rendszerű és tartományhoz csatlakoztatott eszközök esetén működik. 
> - Ha a tárgyban megad olyan eszköztulajdonságokat, mint az IMEI, a sorozatszám vagy a teljesen minősített tartománynév, vagy az eszköztanúsítványban megadja a SAN-azonosítót, vegye figyelembe, hogy ezeket a tulajdonságokat az eszközhöz hozzáféréssel rendelkező személyek meghamisíthatják. 

Az SCEP-tanúsítványprofilok létrehozásakor jelenleg használható változókat az [SCEP-tanúsítványprofil létrehozása](../protect/certificates-profile-scep.md#create-a-scep-certificate-profile) cikk ismerteti. 

Érvényes: Wi-Fi támogatással rendelkező Windows 10 és újabb, valamint iOS rendszerekre

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Nem megfelelő eszközök távoli zárolása <!-- 2064495 -->
A megfelelőségi szabályzatokhoz létrehozható egy olyan művelet, amely távolról zárolja a nem megfelelő eszközöket. Ehhez az Intune **Eszközmegfelelőség** menüjében hozzon létre egy új szabályzatot, vagy válasszon ki egy meglévőt, majd kattintson a **Tulajdonságok** elemre. Válassza a **Meg nem felelés esetén végrehajtandó műveletek** > **Hozzáadás** lehetőséget, majd az eszköz távoli zárolását.
Támogatott a következő rendszereken: 
- Android:
- iOS
- macOS
- Windows 10 mobil verzió 
- Windows Phone 8.1 és újabb verziók 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>A Windows 10-es és újabb kioszk-profilok fejlesztése a Azure Portal <!-- 2748224 -->
Ez a frissítés a következő fejlesztéseket vezeti be a Windows 10 rendszerű kioszk eszközkonfigurációs profilokban (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **Windows 10 és újabb** platform > **Kioszk (előzetes verzió)** profiltípus): 
- Jelenleg több kioszkprofil is létrehozható ugyanazon az eszközön. Ezzel a frissítéssel az Intune eszközönként már csak egy kioszkprofilt támogat. Ha továbbra is több kioszkprofilt kíván használni ugyanazon eszközön, használhat egy egyéni URI-t.
- A **többalkalmazásos kioszk** profilokban kiválaszthatja az alkalmazás csempéinek méretét és sorrendjét a **Start menü elrendezéséhez** az alkalmazásrácson. Ha ennél több testreszabási lehetőségre van szüksége, továbbra is feltölthet egy XML-fájlt.
- A kioszk böngészőbeállításai át lettek helyezve a **Kioszk** beállításaiba. Jelenleg a **Kioszk böngészőbeállításai** saját kategóriával rendelkeznek az Azure Portalon.
A Windows 10 és újabb verziókra vonatkozik

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>PIN-kód kérése, ha az ujjlenyomatokat vagy a Face ID-t egy iOS-eszközön módosítja  <!-- 2637704  -->
A felhasználókat mostantól PIN-kód megadására kéri a rendszer azt követően, hogy biometrikus módosításokat hajtanak végre iOS-eszközükön. Ebbe beletartoznak a regisztrált ujjlenyomat- és face ID-azonosítást érintő módosítások is. A kérés időzítése attól függ, hogy a *hozzáférés újraellenőrzésére vonatkozó követelmények* konfigurációja hány perc után lépi túl az időt.  Ha nincs beállítva PIN-kód, a rendszer új beállítására kéri a felhasználót. 
 
Ez a funkció csak az iOS-ben érhető el, és a működéséhez szükséges az alkalmazások integrálása az Intune APP SDK for iOS 9.0.1-es vagy újabb verziójával. Az SDK-integráció szükséges a viselkedés kényszeríthetőségéhez a megcélzott alkalmazásoknál. Ez az integráció fokozatosan történik, és az egyes alkalmazáscsapatoktól függ. Néhány alkalmazás, amely ezek között szerepelhet: WXP, Outlook, Managed Browser és Yammer.

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Hálózati hozzáférés-vezérlés támogatása iOS VPN-ügyfeleken <!-- 1333693 -->
Az ebben a frissítésben biztosított új beállítás lehetővé teszi a Hálózati hozzáférés-vezérlést (NAC), amikor VPN-konfigurációprofilt hoz létre a Cisco AnyConnect, az F5 Access és a Citrix SSO for iOS esetében. E beállítással az eszköz NAC-azonosítója feltüntethető a VPN-profilban. Jelenleg nincsenek olyan VPN-ügyfelek vagy NAC-partnermegoldások, amelyek támogatnák ezt az új NAC-azonosítót, de [támogatási blogbejegyzésünkből](ttps://aka.ms/iOS12_and_vpn) értesülhet az esetleges változásokról.

A NAC használatához a következőt kell tennie:
1. Jelentkezzen be, és állítsa be, hogy az Intune feltüntesse az eszközazonosítókat a VPN-profilokban.
2. Frissítse a NAC-szolgáltató szoftverét/belső vezérlőprogramját a tőle közvetlenül kapott útmutatást követve.

Erről az iOS-VPN-profilon belüli beállításról a [VPN-beállítások hozzáadása iOS rendszerű eszközökön a Microsoft Intune-ban](../configuration/vpn-settings-ios.md) című cikkben tájékozódhat. A hálózati hozzáférés-vezérlésről a [Hálózati hozzáférés-vezérlés (NAC) integrálása az Intune-nal](../protect/network-access-control-integrate.md) című cikkben tájékozódhat. 

A következőre vonatkozik: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>E-mail profil eltávolítása egy eszközről, még akkor is, ha csak egy e-mail-profil van <!-- 1818139 -->
Korábban nem tudott e-mail-profilt eltávolítani az adott eszközről, *ha* az volt az egyetlen e-mail-profil rajta. E frissítésnek köszönhetően ez most megváltozik. Mostantól akkor is eltávolíthat e-mail-profilt, ha az az egyetlen, amely az eszközön található. További információt [Az e-mail-beállítások konfigurálása a Microsoft Intune-ban](../configuration/email-settings-configure.md) című GitHub dokumentumban talál.

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell-parancsfájlok és HRE <!-- 2309469 -->
Az Intune-beli PowerShell-parancsfájlok beállíthatók úgy, hogy AAD-eszközbiztonsági csoportokat célozzanak meg.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Új "a jelszó megadása kötelező" alapértelmezett beállítás Android, Android Enterprise rendszerhez<!-- 2649963 -->
Új megfelelőségi szabályzat létrehozásakor (Platform > Rendszerbiztonság > **Intune** > **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** > **Android** vagy **Android Enterprise**) a következőképpen módosul a **Jelszó kötelező típusa** beállítás alapértelmezett értéke:

Erről: Alapértelmezett eszköz Erre: Legalább számok

A következőkre vonatkozik: Android, Android Enterprise

Ezekről a beállításokról az [Android](../protect/compliance-policy-create-android.md) és az [Android Enterprise](../protect/compliance-policy-create-android-for-work.md) oldalakon tájékozódhat.

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Előmegosztott kulcs használata Windows 10 Wi-Fi-profilban <!-- 2662938 -->
E frissítés révén előre megosztott kulcsot (PSK) használhat a WPA/WPA2 személyes biztonsági protokollal a Windows 10-es Wi-Fi-konfigurációprofil hitelesítéséhez. Meghatározhatja a mért hálózatokra vonatkozó költségkonfigurációt is a 2018. október 10-i frissítésű Windows 10 rendszert használó eszközök esetében.

Jelenleg importálni kell a Wi-Fi-profilokat vagy egyéni profilt kell létrehozni az előre megosztott kulcsok használatához. A jelenlegi beállításokat a [Windows 10 Wi-Fi beállításait](../configuration/wi-fi-settings-windows.md) ismertető cikk írja le. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>A PKCS-és SCEP-tanúsítványok eltávolítása az eszközökről <!-- 3218390 -->
Bizonyos forgatókönyvek esetében a PKCS- és SCEP-tanúsítványok akkor is megmaradnak az eszközökön, ha szabályzatot távolít el egy csoportból, konfigurációt vagy telepített megfelelőséget töröl, illetve ha valamelyik rendszergazda meglévő SCEP- vagy PKCS-profilt frissít. E frissítéssel változik ez a működési logika. Egyes forgatókönyvek esetében eltávolítjuk az eszközökről a PKCS- és a SCEP-tanúsítványokat, míg mások esetében a tanúsítványok megmaradnak az eszközön. E tanúsítványokról a [SCEP- vagy PKCS-tanúsítványok eltávolítása a Microsoft Intune-ban](../protect/remove-certificates.md) című cikkben tájékozódhat.

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Forgalomirányító használata macOS-eszközökön a megfelelőség érdekében <!-- 2504381 -->
E frissítés tartalmazza a macOS rendszerre készült Gatekeeper technológiát, amely az eszközök megfelelőségének kiértékelésére szolgál. A Gatekeeper funkció beállításáról a [macOS-es eszközök megfelelőségi szabályzatainak hozzáadása az Intune-nal](../protect/compliance-policy-create-mac-os.md) című cikkben tájékozódhat.


### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Az Autopilot-profil alkalmazása a regisztrációhoz még nem regisztrált 10 eszközön <!-- 1558983 -->
AutoPilot-profilokat alkalmazhat a beléptetett Windows 10-es eszközökön, amelyek még nem lettek regisztrálva az AutoPilotba. Az AutoPilot profilban válassza a **Minden megcélzott eszköz átalakítása az AutoPilotra** lehetőséget, amely automatikusan regisztrálja a nem AutoPilot-eszközöket az AutoPilot üzembehelyezési szolgáltatással. A regisztráció feldolgozása 48 órát is igénybe vehet. A regisztrációjuk törlése és a visszaállításuk után az AutoPilot üzembe helyezi az eszközöket.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Több regisztrációs állapot lap profil létrehozása és társítása Azure AD-csoportokhoz <!-- 2526564 -->
Mostantól több regisztrálási állapot oldalprofilt is [létrehozhat és hozzárendelhet](../enrollment/windows-enrollment-status.md) az Azure ADD-csoportokhoz.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Áttelepítés Készülékregisztrációs programról az Apple Business Managerbe az Intune-ban <!--2748613-->
Az Intune-ban működik az Apple üzleti Manager (ABM), és a fiókok frissíthetők a Készülékregisztrációs programból (DEP) az ABM-be. A folyamat az Intune-ban ugyanaz. Ha az Apple-fiókját a DEP-ről az ABM-re szeretné frissíteni, lépjen a [https://support.apple.com/HT208817]( https://support.apple.com/HT208817)webhelyre.

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Riasztási és beléptetési állapot lapja az eszközök beléptetése – áttekintés oldalon <!--2748656-->
A riasztások és a beléptetési hibák mostantól külön lapfüleken jelennek meg az Eszközök beléptetése áttekintő oldalon.

#### <a name="enrollment-abandonment-report----1382924---"></a>Regisztráció megszakítása jelentés <!-- 1382924 -->
A regisztrációmegszakítással kapcsolatos további részleteket tartalmazó új jelentés a **Eszközregisztráció** > **Figyelés** szakaszban áll rendelkezésre. További információt a [Céges portállal történő regisztráció megszakítása – jelentés](../enrollment/enrollment-report-company-portal-abandon.md) című cikkben talál.

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Új Azure Active Directory használati feltételek funkció <!-- 2870393 -->
Az Intune-ra vonatkozó Általános Szerződési Feltételek helyett mostantól használhatja az Azure Active Directory-ra vonatkozó Általános Szerződési Feltételek funkciót. Az Azure AD Használati feltételek funkciója nagyobb rugalmasságot biztosít abban, hogy mely feltételek jelenjenek meg és mikor, továbbá jobb honosítástámogatást, jobb feltételmegjelenítés-vezérlést és jobb jelentéskészítési funkciókat nyújt. Az Azure AD Használati feltételek funkciójához Prémium P1 szintű Azure Active Directory szükséges, amely az Enterprise Mobility + Security E3 csomagnak is része. További információt [A céges felhasználói hozzáférési használati feltételek kezelése](../enrollment/terms-and-conditions-create.md) című cikkben talál.

#### <a name="android-device-owner-mode-support---3188762--"></a>Android-eszköz tulajdonosi üzemmódjának támogatása <!--3188762-->
A Samsung Knox Mobile Enrollment esetében az Intune mostantól támogatja az eszközöknek az Android Device Owner kezelési módra való regisztrációját. A Wi-Fi- és mobilhálózatok felhasználói az eszköz első bekapcsolása után csupán néhány érintéssel regisztrálhatnak. További információ: [Eszközök automatikus regisztrációja a Samsung Knox Mobile Enrollmenttel](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Eszközkezelés
#### <a name="new-settings-for-software-updates------1907869---"></a>A szoftverfrissítések új beállításai   <!-- 1907869 -->  
- Mostantól bizonyos értesítéseket konfigurálhat a végfelhasználók számára a legújabb szoftverfrissítések telepítésének befejezéséhez szükséges újraindítások riasztására.   
- Mostantól újraindítási figyelmeztetést állíthat be a munkaidőn kívüli újraindításhoz, amely támogatja a BYOD-forgatókönyveket.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Windows Autopilot-regisztrált eszközök csoportosítása korrelátor-azonosító alapján <!-- 2075110 -->
Az Intune mostantól támogatja a Windows rendszerű eszközök korrelátorazonosító alapján történő csoportosítását, ha regisztrációjuk az [Autopilot for existing devices](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) (Autopilot meglévő eszközökön) című cikkben leírtak szerint, a Configuration Manager használatával történt. A korrelátorazonosító az Autopilot konfigurációs fájljának egyik paramétere. Az Intune az [Azure AD-eszközök enrollmentProfileName attribútumát](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) automatikusan az ezzel megegyező „OfflineAutopilotprofile-<correlator ID>” attribútumra állítja be. Így tetszőleges dinamikus Azure AD-csoportok hozhatók létre korrelátorazonosító alapján az offline Autopilot-regisztrációk enrollmentprofileName attribútuma használatával. További információt a [Windows Autopilot for existing devices](../enrollment/enrollment-autopilot.md#windows-autopilot-for-existing-devices) (Windows Autopilot meglévő eszközökön) című cikkben talál.

#### <a name="intune-app-protection-policies----2984657---"></a>Intune app Protection-szabályzatok <!-- 2984657 -->
Az Intune alkalmazásvédelemre vonatkozó szabályzatának segítségével többféle adatvédelmi beállítást konfigurálhat az Intune védelemben részesített alkalmazásaira, például a Microsoft Outlookra és a Microsoft Wordre vonatkozóan. E beállítások megjelenését és működését az [iOS](../apps/app-protection-policy-settings-ios.md) és az [Android](../apps/app-protection-policy-settings-android.md) esetében is módosítottuk, így könnyebben találhatja meg az egyes beállításokat. A szabályzatra vonatkozó beállítások három kategóriába tartoznak:
- **Adatáthelyezés** – Ebbe a csoportba tartoznak az adatszivárgás elleni védelem (DLP) vezérlői, például a kivágás, a másolás, a beillesztés és a mentés másként művelet korlátozásai. Ezek a beállítások szabják meg, hogy hogyan kezelhetik a felhasználók az adatokat az alkalmazásokban.
- **Hozzáférési követelmények** – Ez a csoport tartalmazza a PIN-kód alkalmazásonkénti beállítási lehetőségeit, amelyek meghatározzák, hogyan férnek hozzá a végfelhasználók az alkalmazásokhoz egy munkahelyi környezetben.  
- **Feltételes bevezetés** – Ebbe a csoportba olyan beállítások tartoznak, mint az operációs rendszerre vonatkozó minimális beállítások, a függetlenítésészlelés és a rootolt eszközök felderítése, valamint az offline türelmi időszakok.  
  
A beállítások funkciói nem módosulnak, de könnyebben találhatók majd meg, ha Ön a szabályzatlétrehozási folyamatban dolgozik.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Az alkalmazások korlátozása és a vállalati erőforrásokhoz való hozzáférés letiltása Android-eszközökön <!-- 2451462  -->  
Az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** > **Android** > **Rendszerbiztonság** területen, az *Eszközbiztonság* szakaszban megjelent egy új, **Korlátozott alkalmazások** nevű beállítás. A **Korlátozott alkalmazások** beállítás egy megfelelőségi szabályzattal tiltja le a céges erőforrásokhoz való hozzáférést, ha bizonyos alkalmazások telepítve vannak az eszközön. Az eszköz addig nem megfelelőnek minősül, amíg a korlátozott alkalmazásokat el nem távolítják róla.
A következőkre vonatkozik: 
- Android:

### <a name="intune-apps"></a>Intune-alkalmazások

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Az Intune legfeljebb 8 GB méretű csomagot támogat a LOB-alkalmazásokhoz <!-- 1727158 -->
Az Intune 8 GB-ra növelte a Line-of-business- (LOB) alkalmazások maximális csomagméretét. További információt az [Alkalmazások hozzáadása a Microsoft Intune-hoz](../apps/apps-add.md) című cikkben talál.

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Egyéni arculat hozzáadása Céges portál alkalmazáshoz <!-- 1916266 -->
A Microsoft Intune rendszergazdájaként Ön olyan egyéni márkaemblémát tölthet fel, amely háttérképként jelenik majd meg a felhasználónak az iOS Céges portál alkalmazásban található profiloldalán. További információkat a Céges portál alkalmazás konfigurálásáról [a Microsoft Intune Céges portál alkalmazás konfigurálását](../apps/company-portal-app.md) ismertető cikkből tudhat meg.

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Az Intune az Office honosított nyelvét fogja fenntartani az Office végfelhasználói gépeken való frissítésekor. <!-- 2971030 -->
Amikor az Intune telepíti az Office-t a végfelhasználó számítógépén, a végfelhasználók automatikusan ugyanazt a nyelvcsomagokat kapják meg, amelyekkel már eddig is rendelkeztek a korábbi .MSI Office-telepítések esetében. További információt az [Office 365-alkalmazások hozzárendelése Windows 10-es eszközökhöz a Microsoft Intune-nal](../apps/apps-add-office365.md) című cikkben talál.

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Új Intune-támogatás a Microsoft 365-eszközkezelés portálon <!-- 3076965 -->
Hamarosan új Súgó és támogatás felületet vezetünk be az Intune esetében a [Microsoft 365 Eszközkezelési portálon]( http://devicemanagement.microsoft.com). Az új felületen saját szavaival fejtheti ki problémáját, valamint hibaelhárítási ötleteket kaphat, és webalapú szervizelési tartalmakat találhat. Ezeket a megoldásokat szabályokon alapuló gépi tanulási algoritmus biztosítja a felhasználók kérései alapján.  

A problémákra összpontosító útmutatáson túl használhatja az új esetkészítő munkafolyamatot is, amellyel e-mailen vagy telefonon keresztül nyithat támogatási eseteket.  

A bevezetésben részt vevő ügyfelek esetében ez az új felület lép a jelenlegi Súgó és támogatás felület helyébe, rajta az előre kijelölt lehetőségek olyan állandó készletével, amely a konzol azon területén alapul, ahová Ön a Súgó és támogatás megnyitásakor kerül.  

*Ez az új Súgó és támogatás nem minden bérlőre van bevezetve, és az Eszközkezelő portálon érhető el. Az új felhasználói élmény résztvevői véletlenszerűen vannak kiválasztva az elérhető Intune-bérlők közül. Új bérlők lesznek hozzáadva a bevezetés kibontásához.*  

További információ: [Súgó és támogatás](get-support.md#help-and-support-experience) a Microsoft Intune támogatásának beszerzéséhez.  

#### <a name="powershell-module-for-intune--preview-available----951068---"></a>Az Intune PowerShell-modulja – előzetes verzió <!-- 951068 -->
A [GitHub](https://aka.ms/intunepowershell) felületén mostantól új PowerShell-modul áll rendelkezésre, amely a Microsoft Graph-on keresztül nyújt támogatást az Intune API-hez. A modul használatáról az ugyanezen a helyen található README részen tájékozódhat.

<!-- ########################## -->
## <a name="september-2018"></a>Szeptember 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Az App Protection-állapot csempék ismétlődésének eltávolítása <!-- 3083391 -->
A **Felhasználó állapota – iOS** és a **Felhasználó állapota – Android** csempék egyaránt jelen voltak az **Ügyfélalkalmazások – Áttekintés** oldalon, valamint az **Ügyfélalkalmazások – Alkalmazásvédelem állapota** oldalon. Az ismétlődés megszüntetése érdekében az állapotcsempék el lettek távolítva az **Ügyfélalkalmazások – Áttekintés** oldalról. 

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>További külső hitelesítésszolgáltatók támogatása (CA) <!-- 3093107 -->
Az Egyszerű tanúsítványigénylési protokoll (SCEP) segítségével mostantól kiadhat új tanúsítványokat, és meg is újíthat tanúsítványokat a Windows, iOS, Android és macOS rendszerű mobileszközökön.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Az Intune az iOS 10-es és újabb verzióinak támogatására helyezi át <!-- 2454656 -->  
Az Intune-regisztráció, a céges portál és felügyelt böngésző mostantól csak az iOS 10 vagy újabb rendszert futtató iOS-eszközöket támogatják. A szervezet érintett eszközeinek és felhasználóinak megtekintéséhez az Azure Portalon lépjen az Intune > **Eszközök** > **Minden eszköz** elemre. Szűrje a találatokat operációs rendszer alapján, és az **Oszlopok** elemre kattintva megjelenítheti az operációs rendszerekre vonatkozó adatokat. Kérje meg az érintett felhasználókat, hogy frissítsék az eszközeiket egy támogatott operációsrendszer-verzióra.  

Ha az alábbi eszközök közül valamelyikkel rendelkezik, vagy szeretné ezek közül valamelyiket regisztrálni, ne feledje, hogy azok csak az iOS 9-es vagy régebbi verziókat támogatják.  Az Intune Céges portál további eléréséhez ezeket az eszközöket olyanokra kell cserélnie, amelyek támogatják az iOS 10-es és újabb verzióit:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3. generáció) 
* iPad Mini (1. generáció)  

### <a name="device-management"></a>Eszközkezelés

#### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Microsoft 365 eszközkezelés felügyeleti központ <!-- 3078424 -->
Az Microsoft 365 egyik ígérete az egyszerűsített adminisztráció, és az évek során a háttérbeli Microsoft 365-szolgáltatások integrálva vannak a végpontok közötti forgatókönyvek, például az Intune és az Azure AD feltételes hozzáférés terén. Az új [Microsoft 365 felügyeleti központ](http://devicemanagement.microsoft.com) az a hely, amely összevonja, egyszerűsíti és integrálja a rendszergazdák felhasználói élményét. Az Eszközfelügyelet szakértői munkaterület könnyű hozzáférést biztosít az összes eszköz- és alkalmazásfelügyeleti információhoz és feladathoz, amelyre a szervezetnek szüksége lehet. Ez várhatóan a vállalati végfelhasználói számítástechnikai csapatok elsődleges felhőbeli munkaterületévé fog válni.


<!-- ########################## -->
## <a name="august-2018"></a>Augusztus 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Csomag-bújtatási támogatás iOS-alapú VPN-profilokhoz egyéni és Pulse Secure-kapcsolati típusok esetén <!-- 1520957 -->
Az iOS-es alkalmazásonkénti VPN-profilok használatakor választhat az alkalmazásiréteg-beli (alkalmazásproxy) és csomagszintű (csomagalagút) alagútkezelés között. Ezek a beállítások a következő kapcsolattípusokkal érhetők el:
- Egyéni VPN
- Pulse Secure Ha nem biztos a megfelelő értékben, tekintse meg a VPN-szolgáltató dokumentációját.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Az iOS-szoftverfrissítések megjelenítésének késleltetése az eszközön <!-- 1949583 -->
Az Intune > **Szoftverfrissítések** > **iOS-es szabályzatok frissítése** területen konfigurálhatja, hogy mely napon, mely időpontban ne telepítsenek frissítéseket az eszközök. Egy jövőbeli frissítéssel 1-90 napig késleltetheti a szoftverfrissítések láthatóvá válását az eszközön. 
A [Microsoft Intune iOS frissítési szabályzatok konfigurálása](../protect/software-updates-ios.md) területen látható a jelenlegi beállítások listája.

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus-verzió <!-- 2213968 -->
Amikor Intune-t használó Windows 10 rendszerű eszközökhöz rendeli hozzá az Office 365 ProPlus-alkalmazásokat, kiválaszthatja az Office-verziót. Az Azure Portalon válassza a **Microsoft Intune** > **Alkalmazások** > **Alkalmazás hozzáadása** lehetőséget. Ezután válassza az **Office 365 ProPlus csomag (Windows 10)** lehetőséget a **Típus** legördülő menüből. Kattintson az **Alkalmazáscsomag beállításai** elemre a kapcsolódó panel megjelenítéséhez. Állítsa be a **Frissítési csatornát** például a **Havonta** értékre. Azt is megteheti, hogy az **Igen** elemre kattintva törli az Office (msi) másik verzióját a végfelhasználói eszközökről. Kattintson az **Adott** elemre az Office adott verziójának telepítéséhez a végfelhasználói eszközök kiválasztott csatornáján. Ekkor kiválaszthatja az Office **adott verzióját** a használathoz. Az elérhető verziók idővel változni fognak. Ezért egy új központi telepítés létrehozásakor újabb verziók válhatnak elérhetővé, és előfordulhat, hogy egyes régebbi verziók már nem érhetők el. A jelenleg üzemelő példányok továbbra is a régebbi verziót telepítik, de a verziólista csatornánként folyamatosan frissül. További információkért lásd: [Az Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>A Windows 10 VPN-hez készült DNS-beállítások regisztrálásának támogatása <!-- 2282852 -->
A Windows 10 VPN-profilokat ettől a frissítéstől kezdve úgy is konfigurálhatja, hogy egyéni profilok használata nélkül is dinamikusan regisztrálják a belső DNS-ben a VPN-interfészhez rendelt IP-címeket.
A [Windows 10 VPN-beállítások](../configuration/vpn-settings-windows-10.md) című témakörben további információkat talál a jelenleg elérhető VPN-profilbeállításokról.

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>A macOS Céges portál telepítője már tartalmazza a verziószámot a telepítő fájljának nevében. <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>iOS automatikus alkalmazások frissítései <!-- 2729759 -->
Az automatikus alkalmazásfrissítések eszköz- és felhasználói licencelésű alkalmazások esetén is működnek az iOS 11.0 és újabb verzióin.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>A Windows Hello fogja megcélozni a felhasználókat és az eszközöket <!-- 1106609 -->
A [Windows Hello for Business](../protect/windows-hello.md) szabályzatának létrehozásakor a szabályzat az összes cégen belüli felhasználóra vonatkozik (a bérlő egészén). Ezzel a frissítéssel a szabályzat alkalmazható lesz egy adott eszközkonfigurációs szabályzatot használó konkrét felhasználókra és eszközökre is (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **Identitásvédelem** > **Windows Hello for Business**).
Az Azure Portalon az Intune-ban a Windows Hello konfigurációja és beállításai az **Eszközregisztráció** és az **Eszközkonfiguráció** területen is jelen vannak. Az **Eszközregisztráció** a teljes céget célozza (a bérlő egészén), és támogatja a Windows AutoPilot (Kezdőélmény) programot. Az **Eszközkonfiguráció** azokat az eszközöket és felhasználókat célozza, amelyek a bejelentkezéskor alkalmazott szabályzatot használják.
Ez a funkció az alábbiakra vonatkozik:  
- Windows 10 és újabb
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>A Zscaler az iOS-es VPN-profilok számára elérhető kapcsolat <!-- 1769858 -->
Az iOS-es VPN-eszközregisztrációs profil létrehozásakor (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **iOS** platform > **VPN** profiltípus), több kapcsolattípus áll rendelkezésre, többek között a Cisco és a Citrix. Ez a frissítés a Zscalert is hozzáadja a kapcsolattípusokhoz. 
[Az iOS rendszerű eszközökre vonatkozó VPN-beállítások](../configuration/vpn-settings-ios.md) című cikk felsorolja az elérhető kapcsolattípusokat.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>FIPS mód vállalati Wi-Fi profilokhoz Windows 10 rendszerhez <!-- 1879077 -->
Mostantól engedélyezhető a Federal Information Processing Standards (FIPS) Windows 10-es nagyvállalati Wi-Fi-profilokhoz az Azure-beli Intune-portálon. Ügyeljen arra, hogy a FIPS mód a Wi-Fi-infrastruktúrán is engedélyezve legyen, ha a Wi-Fi-profilokon engedélyezi.
A Wi-Fi-profilok létrehozását a [Wi-Fi-beállítások Windows 10 és újabb rendszerű eszközökhöz az Intune-ban](../configuration/wi-fi-settings-windows.md) című témakör ismerteti.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Az S-Mode vezérlése a Windows 10 és újabb rendszerű eszközökön – nyilvános előzetes verzió <!-- 1958649 -->
Ettől a funkciófrissítéstől kezdve olyan eszközkonfigurációs profilt hozhat létre, amely a Windows 10 rendszerű eszközön kikapcsolja az S módot, vagy megakadályozza, hogy a felhasználók kikapcsolják az S módot. Ez a funkció a következő helyen található meg: Intune > **Eszközkonfiguráció** > **Profilok** >  **Windows 10 és újabb** > **Kiadásfrissítés és módkapcsoló**.
Az S módról az [S módú Windows 10 bemutatása](https://www.microsoft.com/windows/s-mode) című részben talál több információt.
Érvényes: a [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) legfrissebb buildjére (amíg az előzetes verzióban van).

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>A Windows Defender ATP konfigurációs csomagja automatikusan hozzáadódik a konfigurációs profilhoz <!-- 2144658 -->
Ha a [Komplex veszélyforrások elleni védelem használata mellett készít elő](../protect/advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile) eszközöket az Intune-ban, ehhez korábban le kellett töltenie egy konfigurációs csomagot, melyet aztán hozzáadott a konfigurációs profilhoz. Ettől a frissítéstől kezdve az Intune automatikusan megkapja a csomagot a Windows Defender biztonsági központtól, és hozzáadja azt az Ön profiljához.
A Windows 10 és újabb verziókra vonatkozik.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>A felhasználók csatlakozásának megkövetelése az eszköz telepítésekor <!--2311457-->
Az eszközprofilok beállíthatók úgy, hogy megköveteljék az eszköz hálózathoz csatlakozását, mielőtt továbblépnének a Hálózat oldalon a Windows 10 telepítése során. Amíg ez a funkció előzetes verziójú, a beállítás használatához a Windows Insider 1809-es buildje, vagy annál újabb verzió szükséges.
Érvényes: a [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) legfrissebb buildjére (amíg az előzetes verzióban van).

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Korlátozza az alkalmazásokat, és letiltja a vállalati erőforrásokhoz való hozzáférést iOS és Android rendszerű eszközökön <!-- 2451462 -->
Az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** > **iOS** > **Rendszerbiztonság** területen új, **Korlátozott alkalmazások** beállítás jelent meg. Az új beállítás egy megfelelőségi szabályzattal tiltja le a céges erőforrásokhoz való hozzáférést, ha bizonyos alkalmazások telepítve vannak az eszközön. Az eszköz addig nem megfelelőnek minősül, amíg a korlátozott alkalmazásokat el nem távolítják róla.
A következőre vonatkozik: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Modern VPN-támogatás frissítései iOS rendszerhez <!-- 2459928, 1819876, and 2650856 -->
Ez a frissítés a következő iOS VPN-ügyfelekhez nyújt támogatást:
- F5 Access (3.0.1 és újabb verziók)
- Citrix SSO
- Palo Alto Networks GlobalProtect (5.0 és újabb verziók) Szintén ebben a frissítésben:
- A jelenlegi **F5 Access** kapcsolattípus új neve iOS rendszeren **F5 Access Legacy**.
- A jelenlegi **Palo Alto Networks GlobalProtect** kapcsolattípus új neve iOS rendszeren **Palo Alto Networks GlobalProtect (legacy)** .
Az ezekkel a kapcsolattípusokkal létező profilok továbbra is működnek a megfelelő örökölt VPN-ügyfelekkel. Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN, vagy Palo Alto Networks GlobalProtect 4.1 vagy korábbi verzió iOS-es használata esetén át kell térnie az új alkalmazásokra. Tegye meg ezt minél előbb annak érdekében, hogy a VPN hozzáférhető legyen az iOS-eszközökön, amikor iOS 12-re frissülnek.
Az iOS 12-ről és a VPN-profilokról a [Microsoft Intune ügyfélszolgálat blogjában](https://go.microsoft.com/fwlink/?linkid=2013806) talál további információt.

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Megfelelőségi szabályzatok exportálása a klasszikus Azure-portálról, és azok újbóli létrehozása az Azure-beli Intune-portálon <!-- 2469637 -->
A klasszikus Azure-portálon létrehozott megfelelőségi szabályzatok hamarosan elavulnak. Áttekintheti és törölheti a meglévő megfelelőségi szabályzatokat, de már nem frissítheti őket. Ha megfelelőségi szabályzatokat kell az Azure-beli Intune-portálra migrálnia, akkor veszővel tagolt ( *.csv*) fájlként exportálhatja azokat. Ezt követően a fájlban lévő adatok felhasználásával újra létrehozhatja a szabályzatokat az Azure-beli Intune-portálon.

> [!IMPORTANT]
> A klasszikus Azure-portál kivonása után többé nem fér majd hozzá megfelelőségi szabályzataihoz, és meg sem tekintheti azokat. Ezért ne feledje exportálni és az Azure Portalon újra létrehozni szabályzatait még a klasszikus Azure-portál elavulása előtt.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile – új Mobile Threat Defense-partner <!-- 22662717 -->
A mobileszköz-hozzáférés a vállalati erőforrásokhoz a feltételes hozzáférés használatával szabályozható a jobb Mobile, a Microsoft Intune rendszerbe integrált Mobile Threat Defense-megoldás kockázatértékelése alapján.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>A Céges portál zárolása Egyalkalmazásos módban, amíg a felhasználó be nem jelentkezik <!--1067692 --> 
A Céges portált egyalkalmazásos módban is futtathatja, ha a DEP-regisztráció során a felhasználót a beállítási asszisztens helyett a Céges portálon keresztül hitelesíti. Ez a beállítás a beállítási asszisztens futtatása után azonnal zárolja az eszközt, így a felhasználónak a hozzáféréshez be kell jelentkeznie. A folyamat biztosítja, hogy az eszköz az előkészítés teljes folyamatán végigmenjen, és ne maradjon hozzárendelt felhasználó nélkül.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Felhasználó és felhasználóbarát név kiosztása egy Autopilot-eszközhöz <!--1346521 -->
Mostantól [egyetlen Autopilot-eszközhöz is rendelhető felhasználó](../enrollment/enrollment-autopilot.md). A rendszergazdák rövid nevet is létrehozhatnak a felhasználó üdvözléséhez az eszköz AutoPilottal történő beállításakor.
Érvényes: a [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) legfrissebb buildjére (amíg az előzetes verzióban van).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>VPP-eszköz licencek használata a Céges portál előzetes kiépítéséhez a DEP-regisztráció során <!-- 1608345 -->
Mostantól mennyiségi vásárlási program (Volume Purchase Program, VPP-) eszközlicencekkel előre is kiépítheti a Céges portált, amikor regisztrál a készülékregisztrációs programban (DEP-ben). Ehhez a [regisztrációs profil létrehozása vagy szerkesztése](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) során kell megadni a Céges portál telepítéséhez használni kívánt VPP-jogkivonatot. Fontos, hogy a jogkivonat ne járjon le, és hogy elég licenccel rendelkezzen a Céges portál alkalmazáshoz. Amennyiben a jogkivonat lejár vagy a licencei elfogynak, az Intune az App Store-beli Céges portált fogja leküldeni (ilyenkor a rendszer kéri az Apple-azonosítót).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Megerősítés szükséges a Céges portál előzetes kiépítés során használt VPP-token törléséhez <!-- 2237634 -->
Mostantól meg kell erősíteni az olyan Volume Purchase Program- (VPP-) jogkivonatok törlését, amelyek éppen a Céges portál előre kiépítéséhez vannak használatban a DEP-regisztráció során.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>A Windows Personal-eszközök regisztrálásának letiltása <!-- 1849498 -->
[Letilthatja a Windows rendszerű személyes eszközök](../enrollment/enrollment-restrictions-set.md) regisztrációját az Intune [mobileszköz-kezelésében](../enrollment/windows-enroll.md). Ez a funkció nem alkalmas az [Intune PC-ügynök](../manage-windows-pcs-with-microsoft-intune.md) használatával regisztrált eszközök letiltásához. Ez a funkció a következő néhány hét során lesz bevezetve, így előfordulhat, hogy nem látja azonnal a felhasználói felületen.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Számítógépnév mintázatának megadása Autopilot-profilban <!--1849855-->
[Gépnév-sablont adhat meg](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) a [gép nevének](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) Autopilot-regisztráció során történő létrehozásához és beállításához. Érvényes: a [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) legfrissebb buildjére (amíg az előzetes verzióban van).

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>A Windows Autopilot-profilok esetében elrejtheti a fiók módosítása lehetőséget a vállalati bejelentkezési oldalon és a tartományi hiba oldalon. <!--1901669 -->
[Új Windows Autopilot-profilbeállítások](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) állnak rendelkezésre a rendszergazdák részére, amelyekkel elrejthetik a fiókváltoztatás lehetőségét a céges bejelentkezési oldalon és a tartományi hibalapon. A beállítás elrejtése akkor lehetséges, ha az Azure Active Directoryban konfigurálva van a Vállalati védjegyezés. Érvényes: a [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) legfrissebb buildjére (amíg az előzetes verzióban van).

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-támogatás az Apple Készülékregisztrációs programhoz <!-- 747651 -->
Az Intune mostantól támogatja a macOS rendszerű eszközök regisztrálását az Apple készülékregisztrációs programjába (DEP). További információkért lásd: [macOS-eszközök automatikus regisztrálása az Apple készülékregisztrációs programjával (DEP)](../enrollment/device-enrollment-program-enroll-macos.md).

### <a name="device-management"></a>Eszközkezelés

#### <a name="delete-jamf-devices----2653306--"></a>JAMF-eszközök törlése <!-- 2653306-->
A JAMF által felügyelt eszközök az **Eszközök** > JAMF-eszköz kiválasztása > **Törlés** lehetőséggel törölhetők.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Terminológia módosítása a "kivonás" és a "Törlés" értékre <!-- 2175759 -->
A Graph API-val való konzisztencia érdekében az Intune felhasználói felületén és a dokumentációban az alábbi terminológiai változásokat vezettük be:
- A **Céges adatok eltávolítása** kifejezést a „Kivonás” kifejezés váltja fel
- A **Gyári beállítások visszaállítása** kifejezést a **törlés** váltja fel

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Megerősítési párbeszédpanel, ha a rendszergazda megpróbálja törölni MDM Push-tanúsítvány <!-- 297909500-->
Ha valaki egy Apple MDM Push-tanúsítvány törlését kezdeményezi, egy megerősítő párbeszédpanelen megjelenik a kapcsolódó iOS- és macOS-eszközök száma. A tanúsítvány törlése esetén ezeket az eszközöket újra kell regisztrálni.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>A Windows Installer további biztonsági beállításai <!-- 2282430 -->
Engedélyezheti a felhasználóknak az alkalmazástelepítések szabályozását. Ha engedélyezve van, azok a telepítések, amelyek a biztonság megsértése miatt le lettek volna állítva engedélyt kapnak a folytatásra. Megadhatja, hogy a Windows Installer emelt szintű engedélyeket használjon, amikor programokat telepít a rendszerben. Emellett engedélyezheti a Windows Information Protection (WIP) elemek indexelését és az ezekre vonatkozó metaadatok titkosítatlan helyen való tárolását. A szabályzat tiltásakor a WIP által védett elemek nem lesznek indexelve és nem jelennek meg a Cortana vagy a fájlkezelő eredményei között. Ezeknek a beállításoknak a funkciói alapértelmezés szerint le vannak tiltva. 

#### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Új felhasználói élmény frissítése a Céges portál webhelyhez <!--2000968 -->
A felhasználók visszajelzései alapján új funkciókkal egészült ki a Céges portál webhely. Jelentős javulást fog tapasztalni eszközei már meglévő funkciói és használhatósága terén. Új, modern és rugalmas külsőt kaptak a webhely különböző területei, &ndash;köztük az eszközadatok, a visszajelzés, a támogatás és az eszközök áttekintése&ndash;. Amit még tapasztalni fog:

- Zökkenőmentes munkafolyamatok minden eszközplatformon
- Hatékonyabb eszközazonosítási és beléptetési folyamatok
- Praktikusabb hibaüzenetek
- Barátságosabb nyelvezet, kevesebb műszaki zsargon
- Alkalmazások közvetlen hivatkozásainak megoszthatósága
- Nagy méretű alkalmazáskatalógusok javított teljesítménye
- Nagyobb hozzáférhetőség minden felhasználó számára  

Az [Intune Céges portál webhelyének dokumentációja](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) frissítve lett, hogy tükrözze a változásokat. Az alkalmazás fejlesztéseire a [Felhasználói felületi frissítések az Intune végfelhasználói alkalmazásaiban](../whats-new-app-ui.md) oldalon láthat egy példát.  

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Továbbfejlesztett jailbreak-észlelés a megfelelőségi jelentésekben<!-- 2198738 -->
A továbbfejlesztett függetlenítésészlelés beállítás állapota mostantól minden megfelelőségi jelentésben megjelenik a felügyeleti konzolon.

### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="scope-tags-for-policies---1081974---"></a>Szabályzatok hatókör-címkéi <!--1081974 -->
[Hatókörcímkék létrehozásával](scope-tags.md) korlátozható a hozzáférés az Intune erőforrásaihoz. Adjon hozzá hatókörcímkét egy szerepkör-hozzárendeléshez, majd adja hozzá a hatókörcímkét egy konfigurációs profilhoz. A szerepkör csak a megfelelő hatókörcímkével rendelkező (vagy hatókörcímke nélküli) erőforrásokhoz férhet hozzá.





<!-- ########################## -->
## <a name="july-2018"></a>Július 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>MacOS-alapú üzletági (LOB) alkalmazások támogatása <!-- 1895847 -->
A Microsoft Intune lehetővé teszi macOS üzletági alkalmazások **Kötelező** vagy **Regisztrációval elérhető** beállítással való üzembe helyezését. A végfelhasználók elvégezhetik az alkalmazások **Rendelkezésre álló** állapotban való üzembe helyezését a macOS-es céges portálon vagy a [Céges portál webhelyén](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>beépített iOS-alapú alkalmazás-támogatás a teljes képernyős módban <!-- 2051098 -->
iOS-eszközökön a Store-alkalmazások és a Felügyelt alkalmazások mellet mostantól a beépített alkalmazásoknál is (mint például a Safari) kiválasztható a Kioszk mód.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus-alkalmazások üzembe helyezésének szerkesztése <!-- 2150145 -->
Microsoft Intune-rendszergazdaként több lehetősége van saját Office 365 Pro Plus üzemelő példányainak szerkesztésére. Továbbá, ezentúl már nem szükséges törölni az üzemelő példányokat az alkalmazáscsomag tulajdonságainak megváltoztatásához. Az Azure Portalon válassza a **Microsoft Intune** > **Ügyfélalkalmazások** > **Alkalmazások** lehetőséget. Az alkalmazások listáján jelölje ki a saját Office 365 Pro Plus csomagot.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>Az Androidhoz készült Intune app SDK frissítve már elérhető <!-- 2744271-->
Elérhető az Androidhoz használható Intune App SDK frissített verziója, mely támogatja az Android P kiadását. Ha Ön alkalmazásfejlesztő, és az Intune App SDK-t használja Androidhoz, telepítenie kell az Intune App SDK frissített verzióját, hogy biztosíthassa az Intune megfelelő működését az alkalmazásainál Android P-eszközökön. Az Intune App SDK jelen frissített verziója tartalmaz egy beépülő modult, amely gondoskodik az SDK frissítéseiről. A már meglévő integrált kódokat nem szükséges újraírnia. További információt az [Intune App SDK Androidhoz](https://github.com/msintuneappsdk/ms-intune-app-sdk-android) című témakörben talál. Ha az Intune-hoz a régi megjelölő stílust használja, javasoljuk, hogy használja az aktatáska ikont. A márkajelzési részletekről [ebben a GitHub-adattárban](https://github.com/msintuneappsdk/intune-app-partner-badge) tájékozódhat.

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>További szinkronizálási lehetőségek a windowsos Céges portál alkalmazásban  
A Windowsos Céges portál alkalmazás mostantól lehetővé teszi, hogy a szinkronizálási folyamatot közvetlenül a Windows tálcájáról vagy a Start menüből is elindíthassa. Ez a funkció abban az esetben igazán hasznos, ha csak szinkronizálni szeretné eszközeit, hogy utána hozzáférhessen a vállalati erőforrásokhoz. Az új funkció eléréséhez jobb gombbal kattintson a Céges portál alkalmazás ikonjára a tálcán vagy a Start menüben. A megjelenő menüpontok közül (azaz a gyorslistában) válassza **Az eszköz szinkronizálása** lehetőséget. A Céges portál megnyílik a **Beállítások** lapra, és elindítja a szinkronizálást. Az új funkciókkal kapcsolatban tekintse [meg a felhasználói felület újdonságait](../whats-new-app-ui.md).   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Új böngészési élmény a windowsos céges portál alkalmazásban  
Ha a windowsos Céges portál alkalmazásban alkalmazásokat böngész vagy keres, mostantól válthat a meglévő **Csempék** nézet és az újonnan hozzáadott **Részletek** nézet között. Az új nézet az alkalmazások adatait jeleníti meg, például a nevet, a kiadót, a kiadás dátumát és a telepítés állapotát.  

Az **Alkalmazások** lapon található egy **Telepítve** nézet is, amely a befejezett és a folyamatban lévő telepítések adatait jeleníti meg. Az új nézet megtekintéséhez lásd: [Az alkalmazásfelhasználói felület újdonságai](../whats-new-app-ui.md)  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>A céges portál alkalmazás továbbfejlesztett felhasználói élménye készülékregisztráció-kezelők használatakor  
Ha egy készülékregisztráció-kezelő (DEM) bejelentkezik a windowsos céges portál alkalmazásba, az alkalmazás csak a készülékregisztráció-kezelő jelenlegi, éppen futó eszközét jeleníti meg. Ennek a fejlesztésnek köszönhetően kevesebb olyan időtúllépés fog történni, amely korábban akkor jelentkezett, ha az alkalmazás megpróbálta megjeleníteni a kezelő által regisztrált összes eszközt.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Alkalmazás-hozzáférés letiltása nem jóváhagyott eszközök gyártói és modelljei alapján  <!-- 1425689 ! -->
Az Intune rendszergazdái egy adott Android-gyártókat és/vagy iOS-modelleket tartalmazó listát kényszeríthetnek az Intune App Protection-szabályzatokkal. A rendszergazda egy pontosvesszőkkel elválasztott listában adhat meg gyártókat az Android-szabályzatokhoz, valamint eszközmodelleket az iOS-szabályzatokhoz. Az Intune App Protection-szabályzatok csak Android- és iOS-eszközökre vonatkoznak. A megadott listán két különálló művelet hajtható végre:
- Az alkalmazás-hozzáférés letiltása a nem megadott eszközökön,
- vagy a vállalati adatok szelektív törlése a nem megadott eszközökön. 

A felhasználó nem férhet hozzá a célalkalmazáshoz, ha az nem felel meg a szabályzat feltételeinek. A rendszer a beállítások alapján letilthatja a felhasználót, vagy szelektíven törölheti annak vállalati adatait az alkalmazáson belül. IOS-eszközökön a funkcióhoz az alkalmazásoknak (például WXP, Outlook, Managed Browser, Yammer) integrálniuk kell az Intune App SDK-t, hogy a megcélzott alkalmazásokon kötelezővé lehessen tennie ezt a funkciót. Ez az integráció fokozatosan történik, és az egyes alkalmazáscsapatoktól függ. Android-eszközökön ennek a funkciónak a használatához a Céges portál legújabb verziójára van szükség. 

A végfelhasználói eszközökön az Intune-ügyfél az Application Protection-szabályzatok Intune-panelén megadott egyszerű sztringegyezések alapján végez műveleteket. Ez teljes mértékben az eszköz által jelentett értéktől függ. Ennek fényében a rendszergazának kell ügyelnie arra, hogy a kívánt viselkedés az elvártnak megfelelően működjön. Ezt úgy lehet elérni, ha teszteli a beállítást különböző eszközgyártókkal és -modellekkel egy kisebb felhasználói csoportban. A Microsoft Intune-ban válassza az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** lehetőséget az alkalmazásvédelmi szabályzatok megtekintéséhez és hozzáadásához. Az alkalmazásvédelmi szabályzatokkal kapcsolatos további információért lásd: [Mik azok az alkalmazásvédelmi szabályzatok](../apps/app-protection-policy.md) és [Szelektív adattörlés alkalmazásvédelmi szabályzatok hozzáférési műveleteivel az Intune-ban](../apps/app-protection-policies-access-actions.md).

#### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Hozzáférés macOS Céges portál kiadás előtti buildhez <!-- 1734766 -->
A Microsoft AutoUpdate-tel regisztrálhat, hogy korábban megkapja a buildeket, ha csatlakozik az Insider programhoz. A regisztráció lehetővé teszi a frissített Céges portál használatát, még mielőtt az elérhetővé válna a végfelhasználók számára. További információért lásd a [Microsoft Intune blogját](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Eszköz megfelelőségi szabályzatának létrehozása macOS-eszközökön a tűzfalbeállítások használatával <!-- 1497640 -->
Amikor új macOS-es megfelelőségi szabályzatot hoz létre (**Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** > **Platform: macOS** > **Rendszerbiztonság**), a **Tűzfal** új beállításai válnak elérhetővé: 

- **Tűzfal**: Konfigurálhatja a bejövő kapcsolatok kezelését a környezetében.
- **Bejövő kapcsolatok**: **Letilthatja** az összes bejövő kapcsolatot az olyan alapvető internetes szolgáltatások kivételével, mint a DHCP, a Bonjour vagy az IPSec. Ez a beállítás letiltja az összes megosztási szolgáltatást is.
- **Rejtett üzemmód**: a rejtett üzemmód **engedélyezésével** megakadályozhatja, hogy a számítógép válaszoljon a bejövő kérelmekre. Az eszköz továbbra is válaszol az engedélyezett alkalmazásoktól érkező kérelmekre.

A macOS 10.12 és újabb verziókra vonatkozik

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Új Wi-Fi-eszköz konfigurációs profil a Windows 10 és újabb rendszerekhez <!-- 1879077 -->
Wi-Fi profilok jelenleg XML-fájlok használatával importálhatók és exportálhatók. A frissítésnek köszönhetően a Wi-Fi eszközkonfigurációs profilok már közvetlenül az Intune-ban is létrehozhatóak, ahogyan néhány más platform esetében is.

A profil létrehozásához nyissa meg az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **Windows 10 vagy újabb** > **Wi-Fi** elemet. 

A Windows 10 és újabb verziókra vonatkozik.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kioszk – elavult, szürkén jelenik meg, és nem módosítható <!-- 2149998 -->
A kioszk (előzetes verzió) szolgáltatás (**eszköz konfigurációja** > **profilok** > **create Profile** > **Windows 10 és újabb** > **eszköz korlátozásai**) elavult, és lecserélve a [kioszk beállításai Windows 10 és újabb verziók](../configuration/kiosk-settings.md). A frissítés után a **Kioszkmód – Elavult** funkció már nem lesz kiválasztható, és a felhasználói felület nem módosítható és nem frissíthető. 

A kioszkmód a [Kioszk beállítások Windows 10 vagy újabb rendszerekhez](../configuration/kiosk-settings.md) lehetőség használatával engedélyezhető.

Windows 10 vagy újabb, és a Windows Holographic for Business rendszerekre vonatkozik

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>Harmadik féltől származó hitelesítésszolgáltatók használatára szolgáló API-k <!-- 2184013 -->
A frissítés tartalmaz egy Java API-t, amely engedélyezi a külső hitelesítésszolgáltatók számára az Intune- és az SCEP-integrációt. A felhasználók így hozzáadhatják egy profilhoz az SCEP-tanúsítványt, és alkalmazhatják az MDM-et használó eszközökre.

Az Intune jelenleg az [Active Directory tanúsítványszolgáltatást használó SCEP-kérelmeket](../protect/certificates-scep-configure.md) támogatja.

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Váltás a képernyő végének megjelenítéséhez vagy nem megjelenítéséhez a kioszk böngészőben <!-- 2455253 -->
Mostantól konfigurálható, hogy a kioszkmódú böngészőkben megjelenjen-e a Munkamenet vége gomb. A vezérlő az **Eszközkonfiguráció** > **Kioszkmód (előzetes verzió)**  >  **kioszkmódú webböngésző** alatt található. Bekapcsolása esetén, ha a felhasználó a gombra kattint, az alkalmazás megerősítést kér a munkamenet befejezéséhez. Megerősítés után a böngésző minden böngészési adatot töröl, és visszatér az alapértelmezett URL-címre.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>ESIM-beli mobil konfigurációs profil létrehozása <!-- 2564077 -->
Az **Eszközkonfiguráció** alatt létre lehet hozni egy eSIM mobilprofilt. Importálható lesz egy fájl, amely a mobilszolgáltató által megadott mobiltelefon-aktiválási kódokat tartalmazza. Ezek a profilok aztán alkalmazhatók lesznek az eSIM LTE-t engedélyező Windows 10 rendszerű eszközökön, amilyen a Surface Pro LTE és más eSIM-képes eszközök.

Ellenőrizze, hogy [eszközei támogatják-e az eSIM-profilokat](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

A Windows 10 és újabb verziókra vonatkozik.

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Válassza ki az eszközök kategóriáit a hozzáférés munkahelyi vagy iskolai beállítások használatával <!-- 1058963 eenotready --> 
Ha engedélyezte az [eszközcsoport-leképezést](../enrollment/device-group-mapping.md), a Windows 10-felhasználókat felkéri a rendszer egy eszközkategória választására, miután regisztráltak a **Gépház** > **Fiókok** > **Hozzáférés munkahelyi vagy iskolai rendszerhez** területen elérhető **Csatlakozás** gombbal. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>A sAMAccountName használata az e-mail profilok fiókjának felhasználónevéhez <!-- 1500307 -->
Fiókhoz tartozó felhasználónévként használhatja a helyszíni **sAMAccountName** nevet az Android-, iOS- és Windows 10 rendszerű e-mail-profilokhoz. Használhatja az Azure Active Directory (Azure AD) `domain` vagy `ntdomain` attribútumából is a tartományt. Vagy adjon meg egy egyéni statikus tartományt.

A funkció használatához szinkronizálnia kell a(z) `sAMAccountName` attribútumot a helyszíni Active Directory-környezetből az Azure AD-ra.

[Android](../configuration/email-settings-android.md), [iOS](../configuration/email-settings-ios.md), [Windows 10 és későbbi verziókra](../configuration/email-settings-windows-10.md) vonatkozik.

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Lásd az eszköz konfigurációs profiljainak ütközését <!-- 1556983 -->
Az **Eszközkonfiguráció** alatt megjelenik a meglévő profilok listája. Ez a frissítés ezt egy újabb oszloppal bővíti, amely az ütköző profilokról közöl részleteket. Egy ütközést jelző sor kiválasztásával megjeleníthető az ütközést okozó beállítás és profil. 

További tudnivalók a [konfigurációs profilok kezeléséről](../configuration/device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Az eszközök megfelelőségének új állapota <!-- 2308882 -->
A következő új állapotok lettek hozzáadva az **Eszközmegfelelőség** > **Szabályzatok** > egy szabályzat kijelölése > **Áttekintés** alatt:
- Sikerült
- Hiba
- Ütközés
- Függőben
- Nem alkalmazható Egy olyan kép is megjelenik, amely mutatja a más platformon lévő eszközszámot. Például egy iOS-profil megtekintése esetén a profilhoz rendelt, nem iOS rendszerű eszközök száma is látható lesz az új csempén. Lásd: [Eszközmegfelelési szabályzatok](../protect/compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Az eszközök megfelelősége támogatja a harmadik féltől származó víruskereső megoldásait <!-- 2325484 -->
Eszközmegfelelőségi szabályzat létrehozásakor (**Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** > **Platform: Windows 10 és későbbi verziók** > **Beállítások** > **Rendszerbiztonság**), új **[Eszközbiztonsági](../protect/compliance-policy-create-windows.md)** beállítások láthatók: 
- **Vírusvédelem**: Ha a **Szükséges** lehetőség van beállítva, a Windows Security Centerben regisztrált vírusvédelmi megoldások (például Symantec és Windows Defender) használatával ellenőrizheti a megfelelőséget. 
- **Kémprogram-elhárító**: Ha a **Szükséges** lehetőség van beállítva, a Windows Security Centerben regisztrált kémprogram-elhárító megoldások (például Symantec és Windows Defender) használatával ellenőrizheti a megfelelőséget. 

A Windows 10 és újabb verziókra vonatkozik 

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>A Samsung Knox Mobile Enrollment használatával regisztrált Androidos eszközök automatikus megjelölése „cégesként”. <!-- 2404851 -->
A Samsung Knox Mobile Enrollment használatával regisztrált Androidos eszközök alapértelmezés szerint **céges** megjelölést kapnak az **Eszköz tulajdonosa** alatt. Ezentúl nincs szükség a céges eszközök IMEI- vagy sorozatszám alapján történő manuális azonosítására a Knox Mobile Enrollment használatával végzett regisztráció előtt.

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>A beléptetési program jogkivonatait tartalmazó profilok oszlop nélküli eszközök <!-- 1853904 -->
A regisztrációs program tokenlistájában van egy olyan új oszlop, amelyben a hozzárendelt profil nélküli eszközök száma látható. Ez lehetővé teszi, hogy a rendszergazdák profilokat rendeljenek hozzá ezekhez az eszközökhöz, mielőtt a felhasználóknak kiosztanák őket. Az új oszlop megtekintéséhez válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget.

### <a name="device-management"></a>Eszközkezelés

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eszközök tömeges törlése az eszközök panelen <!-- 1793693 -->
Az Eszközök panelen mostantól egyszerre több eszközt is törölhet. Válassza az **Eszközök** > **Minden eszköz** lehetőséget >jelölje ki a törölni kívánt eszközöket > válassza a **Törlés** lehetőséget. A nem törölhető eszközök esetében riasztás fog megjelenni.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Google Name-változások az Android for Work és a play for Work szolgáltatásban <!--842873 -->
Az Intune a Google egyes márkaneveit érintő változtatásaihoz igazodva frissítette az „Android for Work” terminológiáját. Az „Android for Work” és a „Play for Work” kifejezések használata megszűnt. A szövegkörnyezettől függően eltérő terminológiát használunk:
- Az „Android Enterprise” az általános, korszerű androidos felügyeleti környezetre vonatkozik.
- A „Munkahelyi profil” vagy a „Profil tulajdonosa” kifejezés a munkahelyi profilokkal felügyelt hozott eszközökre (BYOD) vonatkozik.
- A „Felügyelt Google Play” kifejezés a Google Áruházra vonatkozik.

#### <a name="rules-for-removing-devices----1609459---"></a>Az eszközök eltávolítására vonatkozó szabályok <!-- 1609459 -->
Új szabályok érhetők el, melyekkel automatikusan eltávolíthatja azokat az eszközöket, amelyek nem jelentkeztek be az Ön által megadott számú napon keresztül. Az új szabály megtekintéséhez nyissa meg az **Intune** panelt, és válassza az **Eszközök**, majd az **Eszközök adattörlési szabályai** lehetőséget.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Vállalati tulajdonú, Egyalkalmazásos támogatás Android-eszközökhöz <!-- 1630973 -->

Az Intune támogatja a gondosan felügyelt, zárolt, kioszkstílusú Android-eszközöket. Ez lehetővé teszi a rendszergazdák számára, hogy egyetlen alkalmazásra vagy kis alkalmazáskészletre szűkítsék az eszközhasználatot, és megakadályozzák, hogy a felhasználók más alkalmazásokat engedélyezzenek vagy más műveleteket hajtsanak végre az eszközön. Az Android-kioszk beállításához lépjen az Intune > **Eszközregisztráció** > **Android-regisztráció** > **Kioszk- és feladatalapú eszközök regisztrációja** területre. További információért lásd: [Vállalati androidos kioszkeszközök regisztrálásának beállítása](../enrollment/android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Ismétlődő vállalati eszközök azonosítóinak soron belüli áttekintése <!-- 2203794-->
A céges azonosítók feltöltésekor az Intune az ismétlődések listázásával most lehetőséget ad a döntésre, hogy cseréli vagy megtartja a meglévő információt. Az ismétlődések esetén készülő jelentés akkor jelenik meg, ha az **Eszközregisztráció** > **Céges eszközazonosítók** > **Azonosítók hozzáadása** lehetőséget választja. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Vállalati eszközök azonosítóinak manuális hozzáadása <!-- 2203803 -->
Már hozzáadhatja manuálisan a céges eszközök azonosítóit. Válassza az **Eszközregisztráció** > **Céges eszközazonosítók** > **Hozzáadás** lehetőséget. 


<!-- ########################## -->
## <a name="june-2018"></a>Június 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Microsoft Edge Mobile-támogatás az Intune app Protection-szabályzatokhoz <!-- 1817882 -->
A Microsoft Edge mobilböngésző mostantól támogatja az Intune-ban meghatározott alkalmazásvédelmi szabályzatokat.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>A társított alkalmazás felhasználói modell AZONOSÍTÓjának (AUMID) beolvasása a Microsoft Store for Business-alkalmazások számára kioszk módban <!-- 1560077 ! -->
Az Intune mostantól beolvashatja a Microsoft Store for Business (Metaadatmezőit) alkalmazások alkalmazás felhasználói modell-azonosítóit (AUMIDs), hogy a kioszk profil jobb konfigurációt nyújtson.

További információ a Microsoft Store Vállalatoknak alkalmazásairól: [A Microsoft Store Vállalatoknak áruházban vásárolt alkalmazások felügyelete](../apps/windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Új Céges portál branding oldal <!-- 1916370 -->
A Céges portál védjegyzési lapja új elrendezést, szövegtartalmat és elemleírásokat kapott.


### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo – új Mobile Threat Defense-partner <!-- 1169249 -->
A mobileszköz-hozzáférés a vállalati erőforrásokhoz a feltételes hozzáférés használatával szabályozható a Pradeo által végzett, a Microsoft Intune-nal integrálható mobil veszélyforrások elleni védelmi megoldás alapján.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>FIPS mód használata a NDES tanúsítvány-összekötővel <!-- 1333688 -->
Ha az NDES tanúsítvány-összekötőt olyan számítógépre telepítették, amelyen a Federal Information Processing Standard (FIPS) üzemmód engedélyezve volt, a tanúsítványok kiadása és visszavonása nem az elvárható módon működött. Ettől a frissítéstől kezdve az NDES tanúsítvány-összekötőhöz FIPS-támogatás is tartozik. 

A frissítés a következőket is tartalmazza:

- Az NDES tanúsítvány-összekötő megköveteli a .NET-keretrendszer 4.5-ös verzióját, amely automatikusan része a Windows Server 2016 és Windows Server 2012 R2 rendszereknek. Korábban a .NET 3.5 keretrendszer volt a minimálisan elvárt verzió.
- Az NDES tanúsítvány-összekötő tartalmazza a TLS 1.2 támogatását. Ha tehát a kiszolgáló, amelyen az NDES tanúsítvány-összekötő telepítve van, támogatja a TLS 1.2-t, akkor a TLS 1.2 lesz használva. Amennyiben a kiszolgáló nem támogatja a TLS 1.2 verziót, a TLS 1.1 lesz használva. Az eszközök és a kiszolgáló közötti hitelesítéshez jelenleg a TLS 1.1 van használatban.

További információ: [SCEP-tanúsítványok konfigurálása és használata](../protect/certificates-scep-configure.md) és [PKCS-tanúsítványok konfigurálása és használata](../protect/certficates-pfx-configure.md).

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>A Palo Alto Networks GlobalProtect VPN-profiljainak támogatása <!-- 1333680 ! -->
Ez a frissítés lehetővé teszi a Palo Alto Networks GlobalProtect szolgáltatás választását a VPN-kapcsolat típusaként az Intune-beli VPN-profilokban (**Eszközök konfigurálása** > **Profilok** > **Profil létrehozása** > **Profil típusa** > **VPN**). Ebben a kiadásban az alábbi platformok támogatottak: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>A helyi eszközök biztonsági beállításainak beállításai <!-- 1403702 -->
További helyi eszközbiztonsági beállításokat adhat meg a Windows 10 rendszerű eszközökhöz. Ezek a további beállítások a következő területeken érhetők el: Microsoft hálózati ügyfél, Microsoft hálózati kiszolgáló, hálózati hozzáférés és biztonság, valamint interaktív bejelentkezés. Ezeket a beállításokat az Endpoint Protection kategóriában érheti el, amikor létrehoz egy Windows 10-es eszközkonfigurációs szabályzatot.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Kioszk mód engedélyezése Windows 10-es eszközökön <!-- 1560072 ! -->
Windows 10-eszközökön létrehozhat egy konfigurációs profilt, és engedélyezheti a kioszkmódot (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > **Windows 10** > **Eszközkorlátozások** > **Kioszkmód**). Ebben a frissítésben a **Kioszk (előnézet)** beállítást **Kioszk (elavult)** névre neveztük át. A **Kioszk (elavult)** beállítás használata már nem javasolt, de a júliusi frissítésig még működik. A **Kioszk (elavult)** beállítást az új **Kioszkmód** profiltípus helyettesíti (**Profil létrehozása** > **Windows 10** > **Kioszk (előnézet)** ), amely a kioszkok Windows 10 RS4-es és újabb verziós konfigurációjához tartalmaz beállításokat.

A Windows 10 és újabb verziókra vonatkozik.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Az eszköz profil grafikus felhasználói diagramja visszatért <!-- 2160133 -->
Az eszközprofil grafikus felhasználói diagramján megjelenített számok javításakor (**Eszközkonfiguráció** > **Profilok** > Válasszon ki egy meglévő profilt > **Áttekintés**) ideiglenesen eltávolítottuk a grafikus felhasználói diagramot.

Ezzel a frissítéssel visszatér a grafikus felhasználói diagram, amely az Azure Portalon jelenik meg.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>A Windows Autopilot-regisztráció támogatása felhasználói hitelesítés nélkül <!-- 1165118 -->
Az Intune mostantól támogatja a Windows Autopilot-alapú beléptetést felhasználóhitelesítés nélkül. Ez egy új funkcionalitás, melyet a Windows Autopilot beléptetési profilban érhet el úgy, hogy az „Autopilot Deployment mode” (Autopilot telepítési módja) beállítást „Self-Deploying” (Öntelepítés) értékre állítja.  Az ilyen típusú regisztráció sikeres elvégzéséhez az eszközön a Windows 10 Insider Preview Build 17672 vagy újabb verziónak kell futnia, és rendelkeznie kell egy TPM 2.0 lapkával. Mivel nem igényel felhasználóhitelesítést, ennek a lehetőségnek a használata csak olyan eszközökhöz javasolt, amelyekhez fizikailag is hozzáfér.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Új nyelv/régió beállítás az OOBE beállításakor az Autopilot esetében <!-- 1821766 -->
A kezdőélmény automata profiljaiban egy új konfigurációs beállítás érhető el, amellyel megadható a profilok nyelve és régiója. Az új beállítás eléréséhez válassza az **Eszközök beléptetése** > **Windows-regisztráció** > **Telepítési profilok** > **Profil létrehozása** > **Telepítési mód** = **Öntelepítés** > **Konfigurált alapértelmezések** lehetőséget.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Új beállítás az eszköz billentyűzetének konfigurálásához <!-- 1821768 -->
A kezdőélmény automata profiljaiban egy új beállítás lesz elérhető, amellyel konfigurálható a billentyűzet. Az új beállítás eléréséhez válassza az **Eszközök beléptetése** > **Windows-regisztráció** > **Telepítési profilok** > **Profil létrehozása** > **Telepítési mód** = **Öntelepítés** > **Konfigurált alapértelmezések** lehetőséget.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Csoportos célzásra áthelyezett Autopilot-profilok <!-- 1877935 -->
Az AutoPilot Deployment-profilok AutoPilot-eszközöket tartalmazó Azure AD-csoportokhoz rendelhetők hozzá.

### <a name="device-management"></a>Eszközkezelés

#### <a name="set-compliance-by-device-location----851881----"></a>Megfelelőség beállítása eszköz helye szerint <!-- 851881 ! -->
Bizonyos esetekben érdemes a vállalati erőforrásokhoz való hozzáférést egy adott helyre korlátozni, amelyet hálózati kapcsolattal ad meg. Hozhat létre mostantól megfelelőségi szabályzatot (**Eszközmegfelelőség** > **Helyek**) az eszköz IP-címe alapján. Ha az eszköz az IP-címtartományon kívülre kerül, akkor nem férhet hozzá a vállalati erőforrásokhoz.

A következőkre vonatkozik: Android 6.0-s és újabb eszközök frissített Céges portál alkalmazással

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Fogyasztói alkalmazások és tapasztalatok megelőzése a Windows 10 Enterprise RS4 Autopilot-eszközökön<!-- 1621980 -->
Le fogja tudni tiltani a fogyasztói alkalmazások és funkciók telepítését a Windows 10 Enterprise RS4 rendszerű AutoPilot-eszközökön. A szolgáltatás eléréséhez válassza az **Intune** > **Eszközök konfigurálása** > **Profilok** > **Profil létrehozása** > **Platform** = **Windows 10 vagy újabb** > **Profiltípus** = **Eszközkorlátozások** > **Konfigurálás** > **Windows Reflektorfény** > **Fogyasztói funkciók** lehetőséget. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>A Windows 10 legújabb szoftverfrissítéseinek eltávolítása <!-- 1732948 -->
Ha kritikus problémát tapasztal a Windows 10 rendszerű gépein, akkor választhatja az utolsó funkciófrissítés vagy az utolsó minőségi frissítés eltávolítását (vagyis a korábbi verzió visszaállítását). A funkciófrissítések és minőségi frissítések eltávolításának lehetősége csak ahhoz a karbantartási csatornához érhető el, amelyhez az eszköz tartozik. Az eltávolítás aktivál egy szabályzatot, mely visszaállítja az előző frissítést a Windows 10 rendszerű gépein. A funkciófrissítések esetében korlátozhatja 2–60 napra a legújabb verzió eltávolításának lehetőségét. A szoftverfrissítés-eltávolítási beállítások megadásához válassza a **Szoftverfrissítések** lehetőséget az Azure Portal **Microsoft Intune** paneljén. Ezután a **Szoftverfrissítések** panelen válassza a **Windows 10-es frissítési körök** lehetőséget. Itt végül választhatja az **Áttekintés** szakaszban lévő **Eltávolítás** lehetőséget.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Az IMEI és a sorozatszám összes eszközének keresése <!-- 1793685 -->
Mostantól kereshet IMEI- és sorozatszámokra a Minden eszköz panelen (az e-mail-cím, UPN, eszköznév és felügyeleti név lehetősége továbbra is elérhető). Válassza az Intune-ban az **Eszközök** > **Minden eszköz** lehetőséget, és írja be a kívánt keresési feltételt a keresőmezőbe.

#### <a name="management-name-field-will-be-editable----1875989---"></a>A felügyelet neve mező szerkeszthető lesz <!-- 1875989 -->
Szerkesztheti a Felügyeleti név mezőt az eszköz **Tulajdonságok** panelén. A mező szerkesztéséhez válassza az **Eszközök** > **Minden eszköz** > Válassza ki az eszközt > **Tulajdonságok** lehetőségét. A Felügyeleti név mezővel egyéni módon azonosíthat egy eszközt.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Új minden eszköz szűrő: eszköz kategória <!-- 1878520 -->
Mostantól szűrheti a **Minden eszköz** listát eszközkategória szerint. Ehhez válassza az **Eszközök** > **Minden eszköz** > **Szűrő** > **Eszközkategória** lehetőséget.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>A TeamViewer használata az iOS-és MacOS-eszközök megosztására <!-- 1985547 -->
A rendszergazdák ezentúl a [TeamViewerhez](../remote-actions/teamviewer-support.md) csatlakozva képernyőmegosztást kezdeményezhetnek iOS- és macOS-eszközökkel. Az iPhone-, iPad- és macOS-felhasználók valós időben megoszthatják a képernyőjüket bármilyen más asztali vagy mobileszközzel. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Több Exchange Connector-támogatás <!-- 2070451 -->
Mostantól nemcsak egy Microsoft Intune Exchange Connectort használhat bérlőnként. Az Intune mostantól több Exchange-összekötőt is támogat, így több helyszíni Exchange-szervezettel is beállíthatja az Intune feltételes hozzáférését.

A helyszíni Intune Exchange Connector segítségével annak alapján kezelheti az eszközök helyszíni Exchange-postafiókokhoz történő hozzáférését, hogy az adott eszköz regisztrálva van-e az Intune-ban, és megfelel-e az Intune eszközmegfelelőségi szabályzatainak. Az összekötő beállításához töltse le a helyszíni Intune Exchange Connectort az Azure Portalról, és telepítse egy Exchange-szervezeten belüli kiszolgálón. A Microsoft Intune irányítópultján válassza a **Helyszíni hozzáférés** lehetőséget, majd a **Telepítés** területen kattintson az **Exchange ActiveSync Connector** lehetőségre. Töltse le a helyszíni Exchange Connectort, és telepítse egy Exchange-szervezeten belüli kiszolgálón. Most, hogy már nem csupán egy Exchange Connectort használhat bérlőnként, ugyanezekkel a lépésekkel letöltheti és telepítheti az összekötőt minden további Exchange-szervezethez, ha vannak ilyenek.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Új eszköz hardver részletei: CCID <!-- 2156657 -->
A Chip Card Interface Device (CCID) azonosító mostantól elérhető minden eszközhöz. A megtekintéséhez válassza az **Eszközök** > **Minden eszköz** > kívánt eszköz > **Hardver** lehetőséget, és ellenőrizze a **Hálózati adatok** szakaszt.

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Minden felhasználó és minden eszköz társítása hatókör-csoportként <!-- 2196803 -->
Minden felhasználót, eszközt és a hatókörcsoportok felhasználóit és eszközeit hozzárendelheti. Ehhez válassza az **Intune-szerepkörök** > **Összes szerepkör** > **Szabályzat- és profilkezelés** > **Hozzárendelések** > hozzárendelés kiválasztása > **Hatókör (csoportok)** lehetőséget.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>Az iOS-és macOS-eszközökhöz tartozó UDID-információk <!-- 2219806 -->
Az iOS- és macOS-eszközök UDID (Unique Device Identifier) azonosítójának megtekintéséhez válassza az **Eszközök** > **Minden eszköz** > kívánt eszköz > **Hardver** lehetőséget. Az UDID csak vállalati eszközökhöz érhető el (ezt az **Eszközök** > **Minden eszköz** > kívánt eszköz > **Tulajdonságok** > **Eszköz tulajdonjoga** lehetőséget választva állíthatja be).

### <a name="intune-apps"></a>Intune-alkalmazások

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Továbbfejlesztett hibaelhárítás az alkalmazások telepítéséhez <!-- 928990 -->
A Microsoft Intune MDM által felügyelt eszközökön néha sikertelenek lehetnek az alkalmazástelepítések. Ilyen esetekben nem könnyű megérteni a hiba okát, illetve elhárítani azt. Bevezetjük az alkalmazás-hibaelhárítási funkcióink nyilvános előzetes verzióját. Ennek keretében megjelenik egy új, **Kezelt alkalmazások** nevű csomópont minden egyedülálló eszköz alatt. Ez a Intune MDM-en keresztül szolgáltatott alkalmazások listáját tartalmazza. A csomóponton belül az alkalmazástelepítési állapotokat tekintheti meg. Ha kijelöl egy önálló alkalmazást, megnyithatja annak hibaelhárítási nézetét. A hibaelhárítási nézetben megtekintheti az alkalmazás végpontok közötti életciklusát, például a létrehozási, a módosítási, a célzási dátumot, valamint az alkalmazás egy eszközre való továbbításának dátumát. Továbbá ha az alkalmazás telepítése sikertelen volt, megjelenik egy hibakód, és egy hasznos üzenet a hiba okáról. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune app Protection-szabályzatok és Microsoft Edge <!-- 1818968 -->
A Microsoft Edge mobilböngésző (iOS és Android) mostantól támogatja a Microsoft Intune alkalmazásvédelmi szabályzatait. A Microsoft Edge alkalmazásban a vállalati Azure AD-fiókkal bejelentkező iOS-és Android-eszközök felhasználóit az Intune fogja védeni. iOS-eszközökön a **Require managed browser for web content** (Felügyelt böngésző megkövetelése a webes tartalmakhoz) szabályzat engedélyezi a felhasználóknak a hivatkozások felügyelt Microsoft Edge-ben való megnyitását.

<!-- ########################## -->
## <a name="may-2018"></a>2018. május

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Az alkalmazás-védelmi szabályzatok konfigurálása <!-- 2144597 Part 2 -->

Az Azure Portalon, ahelyett hogy az Intune App Protection szolgáltatáspanelre lépne, mostantól elegendő egyszerűen az Intune-t megnyitnia. Most már az Intune egyetlen helyén érhetők csak el az alkalmazásvédelmi szabályzatok. Az összes alkalmazásvédelmi szabályzatát megtalálhatja az Intune **Mobilalkalmazás** paneljén, az **Alkalmazásvédelmi szabályzatok** területen. Ez az integráció leegyszerűsíti a felhőbeli szolgáltatások adminisztrációját. Ne feledje, hogy minden alkalmazásvédelmi szabályzat elérhető már az Intune-ban, és a korábban konfigurált összes szabályzatot módosíthatja. Az Intune app Policy Protection (APP) és a feltételes hozzáférés (CA) szabályzatok mostantól **feltételes hozzáférés**alatt találhatók, amelyek a **Microsoft Intune** panel **kezelés** szakaszában vagy a **Biztonság** szakaszának  **Azure Active Directory** panel. A feltételes hozzáférési szabályzatok módosításáról további információt a [feltételes hozzáférés Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)című témakörben talál. További információ: [Mik azok az alkalmazásvédelmi szabályzatok?](../apps/app-protection-policy.md)

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Szabályzatok, alkalmazások, tanúsítványok és hálózati profilok telepítésének megkövetelése <!-- 1553555 -->
A rendszergazdák letilthatják, hogy a végfelhasználók hozzáférhessenek a Windows 10-es RS4 asztalhoz, amíg az Intune nem telepít házirendeket, alkalmazásokat és tanúsítvány-és hálózati profilokat az Autopilot-eszközök kiépítéséhez. További információért lásd: [Regisztrációs állapotlap beállítása](../enrollment/windows-enrollment-status.md).

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Samsung Knox Mobile-regisztráció támogatása <!--1112863-->
A Intune a Samsung Knox Mobile Enrollmenttel (KME-vel) való használatával nagy mennyiségű céges tulajdonú Android-eszközt regisztrálhat. A Wi-Fi- és mobilhálózatok felhasználói az eszköz első bekapcsolása után csupán néhány érintéssel regisztrálhatnak. A Knox Deployment App használatával az eszközök Bluetooth vagy NFC segítségével regisztrálhatók. További információ: [Eszközök automatikus regisztrációja a Samsung Knox Mobile Enrollmenttel](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás 

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Segítség kérése a Windows 10 Céges portál <!-- 1874137 -->
A Windows 10 Céges portál mostantól alkalmazáshasználati naplókat küld közvetlenül a Microsoftnak, ha egy felhasználó segítséget kér egy problémához. Így könnyebben háríthatók el és oldhatók meg a Microsoftnak továbbított problémák.

<!-- ########################## -->
## <a name="april-2018"></a>Április 2018

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>PIN-kód támogatása MAM-PIN-kódban Androidon<!-- 1438086 -->

Az Intune-rendszergazdák alkalmazásindítási követelményként állíthatnak be PIN-jelszót a numerikus MAM PIN-kód helyett. Ha a beállítás engedélyezve van, akkor a rendszer a felhasználót egy PIN-jelszó beállítására kéri, amelyet kötelező alkalmaznia, mielőtt hozzáférhetne a MAM-kompatibilis alkalmazásokhoz. A PIN-jelszó olyan numerikus PIN-kód, amely legalább egy speciális karaktert vagy kisbetűt/nagybetűt is tartalmaz. Az Intune a PIN-jelszót a hagyományos, numerikus PIN-kódhoz hasonlóan támogatja: állíthat be minimális jelszóhosszt, és engedélyezheti a karakterek és sorozatok ismétlődését a felügyeleti konzolon. Ennek a funkciónak a használatához a Céges portál legújabb verziójára van szükség Android rendszerben. Ez a funkció már elérhető az iOS rendszerben.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>MacOS-alapú üzletági (LOB) alkalmazások támogatása <!-- 1473977 -->
A Microsoft Intune támogatni fogja a macOS-hoz készült LOB-alkalmazások telepítését az Azure Portalról. Ezzel a funkcióval hozzáadhat egy macOS-hoz készült LOB-alkalmazást az Intune-hoz, miután azt előkészítette egy, a GitHubon elérhető eszközzel. Válassza az Azure Portalon az **Intune** panel **Ügyfélalkalmazások** elemét. Az **Ügyfélalkalmazások** panelen válassza az **Alkalmazások** > **Hozzáadás** lehetőséget. Az **Alkalmazás hozzáadása** panelen válassza az **Üzletági alkalmazás** lehetőséget. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Beépített minden felhasználó és minden eszköz csoport az Android Enterprise Work Profile alkalmazás-hozzárendeléshez <!-- 1813073 -->
Ön használhatja a beépített **Minden felhasználó** és **Minden eszköz** csoportokat az Android Enterprise munkahelyiprofil-alkalmazásainak hozzárendelése esetében. További információ: [Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban](../apps/apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Az Intune újra fogja telepíteni a felhasználók által eltávolított szükséges alkalmazásokat <!-- 1947010 -->
Ha egy végfelhasználó eltávolít egy kötelező alkalmazást, az Intune a 7 napos újraértékelési ciklus kivárása helyett 24 órán belül automatikusan újratelepíti az alkalmazást.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Az alkalmazás-védelmi szabályzatok konfigurálási helyének frissítése <!-- 2144597 -->

A Microsoft Intune-beli Azure Portalon ideiglenesen átirányítás lesz érvényben az **Intune App Protection** szolgáltatás paneljéről a **Mobilalkalmazás** panelre. Fontos megjegyezni, hogy már minden alkalmazásvédelmi szabályzat megtalálható az Intune **Mobilalkalmazás** paneljén, az alkalmazáskonfigurációban. Az Intune App Protection szolgáltatás megnyitása helyett csak az Intune-t kell majd megnyitnia. 2018. áprilisban megszüntetjük az átirányítást, és teljes mértékben eltávolítjuk az **Intune App Protection** szolgáltatás paneljét, így az Intune alkalmazásvédelmi szabályzatait ezentúl egyetlen helyen tekintheti meg. 

**Hogyan érint ez engem?**
Ez a változás a különálló Intune-t használó ügyfeleket és a hibrid (az Intune-t a Configuration Managerrel használó) ügyfeleket egyaránt érinti. Az integráció leegyszerűsíti a felhőfelügyelet adminisztrációját.

**Hogyan készüljek fel a változásra?**
Az **Intune App Protection** szolgáltatás panelje helyett az **Intune-t** jelölje meg kedvencként, és mindenképpen ismerkedjen meg az alkalmazásvédelmi szabályzatok munkafolyamatával az Intune **Mobilalkalmazás** paneljén. Egy rövid ideig átirányítás lesz érvényben, majd az **App Protection** panel el lesz távolítva. Ne feledje, hogy az összes alkalmazás-védelmi szabályzat már az Intune-ban van, és a feltételes hozzáférési szabályzatok bármelyike módosítható. A feltételes hozzáférési szabályzatok módosításáról további információt a [feltételes hozzáférés Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)című témakörben talál. További információ: [Mik azok az alkalmazásvédelmi szabályzatok?](../apps/app-protection-policy.md) 

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Az eszköz profil diagramja és az állapot lista a csoport összes eszközét megjeleníti <!-- 1449153 -->
Eszközprofil konfigurálásakor (**Eszközök konfigurálása** > **Profilok**) kiválasztja az eszközprofilt, például iOS. Ezután hozzárendeli ezt a profilt egy csoporthoz, mely tartalmaz iOS- és nem iOS-eszközöket is. A grafikus diagramon lévő számlálón az látható, hogy a profil alkalmazva lett az iOS- *és* a nem iOS-eszközökre is (**Eszközök konfigurálása** > **Profilok** > meglévő profil > **Áttekintés**). Amikor a grafikus diagramot választva megjeleníti az **Áttekintés** lapot, az **Eszközállapot** terület felsorolja a csoport összes eszközét, nemcsak az iOS-eszközöket. 

A jelen frissítés megjelenése után a grafikus diagram (**Eszközök konfigurálása** > **Profilok** > meglévő profil > **Áttekintés**) csak az adott eszközprofil számlálóját jeleníti meg. Ha például az eszközprofil iOS-eszközökre van alkalmazva, akkor a diagram csak az iOS-eszközök számát jeleníti meg. A grafikus diagram választása és az **Eszközállapot** lista megnyitása esetén is csak az iOS-eszközök lesznek felsorolva.

A jelen frissítés elkészültéig a grafikus felhasználói diagramot ideiglenesen eltávolítottuk. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Always On VPN for Windows 10 <!--1333666 -->

Jelenleg a [Minden bekapcsolva](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) trigger a Windows 10-eszközökön csak OMA-URI-val létrehozott egyéni VPN-profil segítségével használható.

A frissítés révén a rendszergazdák engedélyezhetik a Mindig bekapcsolva beállítást a Windows 10 VPN-profilokban közvetlenül az Azure Portalon elérhető Intune konzolról. A Mindig bekapcsolva beállítású VPN-profilok automatikusan csatlakoznak az alábbi esetekben:

- Felhasználói bejelentkezés az eszközre
- Hálózatváltozás az eszközön
- Az eszköz képernyője ismét bekapcsol, miután ki volt kapcsolva

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Új nyomtatóbeállítások az oktatási profilokhoz <!-- 1308900 -->

Az oktatási profilok új beállításai a **Nyomtatók** kategória **Nyomtatók**, **Alapértelmezett nyomtató**, **Új nyomtatók hozzáadása** területén érhetők el.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Hívóazonosító megjelenítése a személyes profilban – Android Enterprise Work-profil <!--1098984 -->
Előfordulhat, hogy az eszközön személyes profilt használó végfelhasználók nem látják egy munkahelyi kapcsolat hívásazonosítójának részleteit. 

Ezzel a frissítéssel új beállítás válik elérhetővé az **Android Enterprise** > **Eszközkorlátozások** > **Munkaprofil-beállítások** menüpontban:
- Munkahelyi kapcsolat hívásazonosítójának megjelenítése a személyes profilban

Engedélyezése (konfigurálás nélkül) esetén a munkahelyi hívó részletei megjelennek a személyes profilban. Tiltása esetén a munkahelyi hívó részletei nem jelennek meg a személyes profilban. 

A következőkre vonatkozik: Android munkahelyi profilos eszközök Android v6.0 és újabb operációs rendszerekkel

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Új Windows Defender hitelesítőadat-őr beállításai hozzáadva az Endpoint Protection-beállításokhoz <!--1102252 --><!--from 1802 and 1804-->

Ezzel a frissítéssel a [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Eszközkonfiguráció** > **Profilok** > **Endpoint protection**) az alábbi beállításokkal bővült: 

- **Windows Defender Credential Guard**: Bekapcsolja a Credential Guardot virtualizálás-alapú biztonsággal. Ennek a funkciónak a bekapcsolása segít megvédeni a hitelesítő adatokat a következő újraindításkor, ha a **Platformbiztonsági szint a Biztonságos rendszerindítással** és a **Virtualizálás-alapú biztonság** egyaránt be van kapcsolva. A lehetőségek a következők:
  - **Letiltva**: Ha a Credential Guard előzőleg be volt kapcsolva az **Engedélyezve zárolással** lehetőséggel, akkor ez távolról kikapcsolja a Credential Guardot.

  - **Engedélyezve UEFI-zárolással**: Ezzel a beállítással biztosíthatja, hogy a Credential Guard ne lehessen letiltható egy beállításkulccsal vagy egy csoportházirenddel. Ha ennek a beállításnak a használata után le szeretné tiltani a Credential Guardot, akkor a Csoportházirendet „Letiltva” állapotra kell állítania. Ezt követően távolítsa el a biztonsági funkciót mindegyik számítógépen egy fizikailag jelen lévő felhasználóval. Ezekkel a lépésekkel törölhető az UEFI-ban megőrzött konfiguráció. Amíg megvannak a UEFI-konfigurációk, a Credential Guard engedélyezve marad.

  - **Engedélyezve zárolás nélkül**: Távolról letilthatja a Credential Guardot egy csoportházirenddel. Azokon az eszközökön, amelyek ezt a beállítást használják, legalább a Windows 10 1511-es verziójának kell futnia.

Az alábbi függő technológiák automatikusan engedélyezve lesznek a Credential Guard konfigurálásakor: 

- **Virtualizálás-alapú biztonság (VBS) engedélyezése**: Bekapcsolja a virtualizálás-alapú biztonságot (VBS-t) a következő újraindításkor. A virtualizálás-alapú biztonság a Windows hipervizorral nyújt támogatást biztonsági szolgáltatásokhoz, és Biztonságos rendszerindítás szükséges hozzá.
- **Biztonságos rendszerindítás közvetlen memóriaeléréssel (DMA-val)** : Bekapcsolja a VBS-t a biztonságos rendszerindítás és a közvetlen memóriaelérés funkcióival. A DMA-védelemhez hardveres támogatás szükséges, és csak a megfelelően konfigurált eszközökön alkalmazható. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Egyéni tulajdonos nevének használata a SCEP-tanúsítványon <!-- 2064190 -->
Használhatja az **OnPremisesSamAccountName** köznapi nevet egyéni tulajdonosként az SCEP-tanúsítványprofilokban. Így használhatja például a következőt: `CN={OnPremisesSamAccountName})`.

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Az androidos vállalati munkahelyi profilokhoz tartozó kamera és képernyőfelvételek letiltása <!-- 1098977 -->
Két új tulajdonság érhető el letiltásra, amikor az Android-eszközökhöz eszközkorlátozásokat állít be: 
- Kamera: Letiltja a hozzáférést az eszközön lévő összes kamerához
- Képernyőfelvétel: Letiltja a képernyőfelvételt, és megakadályozza a tartalom megjelenítését a biztonságos videokimenettel nem rendelkező megjelenítő eszközökön

Hatókör: Az Android Enterprise munkahelyi profiljai.

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Cisco AnyConnect-ügyfél használata iOS-hez <!-- 1333708 -->

Új VPN-profil iOS-hez történő létrehozásakor mostantól két lehetőség közül lehet választani: **Cisco AnyConnect** és **Cisco Legacy AnyConnect**. A Cisco AnyConnect-profilok a 4.0.7x és újabb verziókat támogatják. Meglévő iOS Cisco AnyConnect VPN-profiljai a **Cisco Legacy AnyConnect** nevet kapják, és továbbra is úgy működnek a Cisco AnyConnect 4.0.5x és régebbi verzióival, mint eddig.

> [!NOTE]
> Ez a módosítás csak az iOS-re vonatkozik. Az Android és az Android Enterprise munkahelyi profiljaiban, valamint a macOS rendszerű platformokon továbbra is csak egyetlen Cisco AnyConnect lehetőség áll rendelkezésre.


### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Új regisztrációs lépések a macOS magas Sierra 10.13.2 +-t használó eszközökön lévő felhasználók számára <!--1734567 -->
A macOS High Sierra 10.13.2 rendszer bevezette a „felhasználó által jóváhagyott” mobileszköz-kezelési regisztrációt. A jóváhagyott regisztrációk lehetővé teszik az Intune-nak bizonyos biztonsági szempontból kényes beállítások kezelését. További információt az Apple támogatási dokumentumában találhat itt: https://support.apple.com/HT208019.

A macOS rendszerhez készült Céges portál alkalmazással regisztrált eszközök „felhasználó által nem jóváhagyott” állapotúként vannak minősítve, hacsak a felhasználó manuálisan jóváhagyást nem ad a Rendszerbeállítások menü megnyitásával. Emiatt a macOS rendszerhez készült Céges portál alkalmazás mostantól a regisztrációs folyamat végén átirányítja a macOS 10.13.2 és újabb rendszerek felhasználóit a regisztrációjuk manuális jóváhagyásához. Az Intune felügyeleti konzolja jelenti, ha egy regisztrált eszközt jóváhagyott a felhasználó.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>A JAMF által regisztrált macOS-eszközök mostantól regisztrálhatnak az Intune-ban <!-- 2370684 -->
A macOS-es Céges portál 1.3 és 1.4 verziója nem regisztrálta sikeresen a Jamf-eszközöket az Intune-nal. A macOS portál 1.4.2 verziója kijavítja ezt a hibát.

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Az Android rendszerhez készült Céges portál alkalmazásban frissített Súgó <!-- 1631531 -->
Az Android platform ajánlott eljárásaihoz igazodva frissítettük az Androidhoz készült Céges portál alkalmazás Súgó funkcióját. Mostantól ha a felhasználók problémát észlelnek az alkalmazásban, a **Menü** > **Súgó** lehetőségre koppintva az alábbi tevékenységeket végezhetik:
- Diagnosztikai naplókat küldhetnek a Microsoftnak.
- Egy eseményazonosítót és a hibát ismertető e-mailt írhatnak a céges ügyfélszolgálatnak.  

A frissített ügyféltámogatást a [Naplók elküldése e-mailben](/intune-user-help/send-logs-to-your-it-admin-by-email-android) és a [Hibák elküldése a Microsoftnak](/intune-user-help/send-logs-to-microsoft-android) területen érheti el.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Új beléptetési hiba trendjeinek diagramja és meghibásodási okai tábla <!-- 1471783 -->
A Regisztráció áttekintése lapon megtekintheti a regisztrációs hibák trendjét és az öt leggyakoribb hibaokot. A diagramra vagy a táblázatra kattintva hozzáférhet a részletesebb adatokhoz, valamint hibaelhárítási tanácsokat és szervizelési javaslatokat is találhat.


### <a name="device-management"></a>Eszközkezelés

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>A komplex veszélyforrások elleni védelem (ATP) és az Intune teljes mértékben integrálva van <!-- 1629303 -->

A [Komplex veszélyforrások elleni védelem](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) megállapítja a Windows 10 rendszerű eszközök kockázati szintjét. A Windows Defender biztonsági központban (ATP portál) kapcsolatot hozhat létre a Microsoft Intune-nal. Ennek létrehozása után egy Intune-megfelelőségi szabályzat alapján meg lesz határozva az elfogadható fenyegetettségi szint. Ha túllépi a fenyegetés szintjét, egy Azure Active Directory (AD) feltételes hozzáférési szabályzat letilthatja a hozzáférést a szervezeten belüli különböző alkalmazásokhoz.

Ez a funkció teszi lehetővé az ATP számára a fájlok vizsgálatát, a fenyegetések észlelését, és a Windows 10 rendszerű eszközöket érintő kockázatok jelentését.

Lásd: [az ATP engedélyezése feltételes hozzáféréssel az Intune-ban](../protect/advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Felhasználó nélküli eszközök támogatása <!-- 1637553 -->
Az Intune támogatja a megfelelőség kiértékelését a felhasználó nélküli eszközökön is, ideértve például a Microsoft Surface Hub eszközt. A megfelelőségi szabályzat alkalmazható közvetlenül eszközökre. Ezért a megfelelőség (vagy meg nem felelőség) megállapítható a társított felhasználó nélküli eszközök esetében is.

#### <a name="delete-autopilot-devices----1713650---"></a>AutoPilot-eszközök törlése <!-- 1713650 -->
Az Intune-rendszergazdák [törölhetik az Autopilot-eszközöket](../enrollment/enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Továbbfejlesztett eszköz-törlési élmény <!--1832333 -->
Mostantól nem kell eltávolítania a céges adatokat vagy visszaállítania a gyári beállításokat, mielőtt [törölhetne egy eszközt az Intune-ból](../remote-actions/devices-wipe.md#delete-devices-from-the-intune-portal).

Az új törlési funkció eléréséhez jelentkezzen be az Intune-ba, és válassza az **Eszközök** > **Minden eszköz** > eszköz neve > **Törlés** lehetőséget.

Ha továbbra is szeretné alaphelyzetbe állítani vagy kivonni az eszközöket, használhatja a megszokott **Céges adatok eltávolítása** és **Gyári beállítások visszaállítása** lehetőséget, mielőtt a **Törlés** lehetőséget választaná. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Az iOS-hangok lejátszása elveszett módban <!-- 1947769 -->
Amikor egy felügyelt iOS-eszköz a mobileszköz-kezelés (MDM) [Elveszett üzemmódjában](../remote-actions/device-lost-mode.md) van, [lejátszhat egy hangot](../remote-actions/device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Eszközök** > **Minden eszköz** > válasszon iOS-eszközt > **Áttekintés** > **Egyebek**). A hang lejátszása egészen addig folytatódik, amíg az eszköz ki nem lép az Elveszett üzemmódból, vagy a felhasználó le nem tiltja a hangot az eszközön. iOS 9.3-as és újabb rendszerű eszközökre érvényes.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Az Intune-eszközön végzett keresések webes eredményeinek letiltása vagy engedélyezése <!--1972804-->

A rendszergazdák mostantól letilthatják az eszközön a keresések webes eredményeit.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Továbbfejlesztett hibaüzenetek Apple MDM Push-tanúsítvány feltöltési hiba esetén <!-- 2172331 -->

A hibaüzenet elmagyarázza, hogy ugyanazt az Apple ID-t kell használni egy meglévő MDM-tanúsítvány megújításakor.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>A macOS-Céges portál tesztelése a virtuális gépeken <!-- 2216679 -->

Közzétettünk egy útmutatót IT-rendszergazdák számára, amelyben segítséget kapnak ahhoz, hogy a macOS-hez készült Céges portál alkalmazást teszteljék virtuális gépeken a Parallels Desktopban és a VMware Fusionben. További információt a [Virtuális macOS-gépek regisztrálása teszteléshez](../enrollment/macos-enroll.md#enroll-virtual-macos-machines-for-testing) című témakörben talál.

### <a name="intune-apps"></a>Intune-alkalmazások

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Az iOS rendszerhez készült Céges portál alkalmazás felhasználói élményének frissítése <!--1412866 -->
Nagyszabású felhasználóiélmény-frissítést adtunk ki az iOS-es Céges portál alkalmazáshoz. A frissítéshez teljes vizuális átalakulás is tartozik, amely modernebb megjelenést és élményt biztosít. Az alkalmazás működését változatlanul hagytuk, használhatóságát és kezelhetőségét azonban fejlesztettük.  

Amit még tapasztalni fog:
- IPhone X támogatása.
- Gyorsabb alkalmazásindítás és betöltés, amellyel a felhasználók időt takarítanak meg.
- A felhasználóknak a legfrissebb állapotinformációkat nyújtó újabb folyamatjelző sávok.
- A felhasználói naplófeltöltés módjának fejlesztése, hogy a hibákat egyszerűbb legyen bejelenteni.  

A frissített megjelenés megtekintésez lépjen [Az alkalmazásfelhasználói felület újdonságai](../whats-new-app-ui.md) területre.

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Helyszíni Exchange-adatainak védelme az Intune-alkalmazás és a HITELESÍTÉSSZOLGÁLTATÓ használatával <!-- 1056954 -->
Mostantól a helyszíni Exchange-adatokhoz való Outlook Mobile-hozzáférést az Intune App Policy Protection (APP) és a feltételes hozzáférés segítségével védheti. Alkalmazásvédelmi szabályzat hozzáadásához vagy módosításához az Azure Portalon válassza a **Microsoft Intune** > **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** lehetőséget. A funkció használata előtt győződjön meg arról, hogy megfelel az [iOS-es és Androidos Outlook követelményeinek](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx).


### <a name="user-interface"></a>Felhasználói felület

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Továbbfejlesztett eszközök csempéi a Windows 10-es Céges portál <!--2213364 -->

Frissítettük a csempéket, így most már jobban hozzáférhetőek a gyengén látó felhasználók számára is, és jobb teljesítményt nyújtanak a képernyőolvasó eszközök használatakor.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Diagnosztikai jelentések küldése a macOS rendszerhez készült Céges portál alkalmazásban <!-- 2216677 -->
Frissült a macOS-eszközökhöz készült Céges portál alkalmazás, így jobb lehetőségeket nyújt a felhasználóknak az Intune-nal kapcsolatos hibák jelentésére. A dolgozói a Céges portál alkalmazásból a következőket tehetik meg:

- Diagnosztikai jelentések feltöltése közvetlenül a Microsoft fejlesztői csapatának.
- Incidensazonosító elküldése e-mailben a vállalata informatikai támogatási csoportjának.

További információt a [Néhány hiba macOS esetén](/intune-user-help/send-errors-macos) című témakörben talál.

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Az Intune alkalmazkodik a Windows 10 Céges portál alkalmazásának Fluent kialakítási rendszeréhez <!-- 1195010 -->
A Windows 10-es Intune Céges portál alkalmazást frissítettük a [Fluent Design System navigációs nézetével](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Az alkalmazás oldalán egy statikus, függőleges lista jelenik meg a legfelső szintű oldalakkal. A gyors megtekintéshez és az oldalak közötti váltáshoz kattintson bármelyik hivatkozásra. Egy frissítéssorozattal adaptív, kényelmesebb és ismerősebb Intune-élményt szeretnénk létrehozni. Ez a sorozat első frissítése. A frissített megjelenés megtekintésez lépjen [Az alkalmazásfelhasználói felület újdonságai](../whats-new-app-ui.md) területre.

<!-- ########################## -->
## <a name="march-2018"></a>2018. március

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Riasztások lejáró iOS-es üzletági (LOB) alkalmazások Microsoft Intune <!-- 748789 -->

Az Intune az Azure Portalon keresztül értesítést küld a hamarosan lejáró üzletági iOS-alkalmazásokról. Az üzletági iOS-alkalmazás új verziójának letöltésekor az Intune eltávolítja a lejárati értesítést az alkalmazáslistáról. A lejárati értesítés csak az újonnan feltöltött üzletági iOS-alkalmazások esetében lesz aktív. Az üzletági iOS-alkalmazások kiépítési profiljának lejárata előtt 30 nappal egy figyelmeztetés jelenik meg. A lejárat után a figyelmeztetés Lejárt állapotúra módosul.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>A Céges portál témák testreszabása hexadecimális kódokkal <!--1049561 -->

Hexadecimális kódokkal testreszabhatja a témák színeit a Céges portál alkalmazásaiban. A hexadecimális kód megadásakor az Intune meghatározza a szövegszín és a háttérszín közötti legnagyobb kontrasztot eredményező szövegszínt. A szöveg színéről és a céges emblémáról is megtekinthet egy-egy előnézeti képet az **Ügyfélalkalmazások** > **Céges portál** területen.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Alkalmazások hozzárendelésének kizárása az Android Enterprise-csoportok alapján <!-- 1813081 -->

Az Android Enterprise (korábbi nevén Android for Work) a befoglaló és kizáró csoportokat támogatja, de az előre létrehozott **Minden felhasználó** és **Minden eszköz** beépített csoportokat nem. További információ: [Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban](../apps/apps-inc-exl-assignments.md).


### <a name="device-management"></a>Eszközkezelés

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome----2258071---"></a>Az összes eszköz exportálása CSV-fájlokba az IE-ben, a Microsoft Edge-ben vagy a Chrome-ban <!-- 2258071 -->
Az **Eszközök** > **Minden eszköz** területen **exportálhatja** az eszközöket egy CSV formátumú listába. Az Internet Explorer (IE) 10000 eszköznél kevesebbel rendelkező felhasználói sikeresen exportálhatják a fájljaikat több fájlba. Minden fájl legfeljebb 10000 eszközt tartalmaz.

A Microsoft Edge és a Chrome > 30000 eszközzel rendelkező felhasználói több fájlba is exportálhatjuk az eszközeiket. Minden fájl legfeljebb 30000 eszközt tartalmaz.

Az [Eszközkezelés](../remote-actions/device-management.md) területen további részletek jelennek meg a kezelt eszközökkel végezhető műveletekről.

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Új biztonsági fejlesztések az Intune szolgáltatásban  <!-- 1637539 -->   

Az Azure-beli Intune-on egy új váltógombot vezettünk be, amellyel az Intune különálló verziójának ügyfelei a szabályzattal nem rendelkező eszközöket **Megfelelőként** (kikapcsolt biztonsági funkció) vagy **Nem megfelelőként** (bekapcsolt biztonsági funkció) kezelhetik. Így meggyőződhetnek arról, hogy az erőforrások csak az eszközmegfelelőség értékelése után válnak elérhetővé.

Ez a funkció attól függően érinti Önt, hogy már hozzárendelt-e megfelelőségi szabályzatokat.

- Ha Ön új vagy meglévő fiókot használ, és az eszközeihez nincsenek hozzárendelve megfelelőségi szabályzatok, a váltógomb automatikusan a **Megfelelő** értékre lesz beállítva. A funkció a konzolon alapértelmezés szerint ki van kapcsolva. Ez nincs hatással a végfelhasználókra.
- Ha Ön új vagy meglévő fiókot használ, és vannak olyan eszközei, melyekhez van hozzárendelve megfelelőségi szabályzat, a váltógomb automatikusan a **Nem megfelelő** értékre lesz beállítva. A funkció alapértelmezés szerint be van kapcsolva a márciusi frissítés bevezetésekor.

Ha feltételes hozzáféréssel (CA) használ megfelelőségi szabályzatokat, és a funkció be van kapcsolva, a CA innentől fogva letilt minden olyan eszközt, amelyhez nincs hozzárendelve legalább egy megfelelőségi szabályzat. Az ezen eszközökhöz társított végfelhasználók, akik korábban hozzáférhettek a levelezéshez, elveszítik a hozzáférésüket, hacsak nem rendel hozzá legalább egy megfelelőségi szabályzatot minden eszközhöz.   

Megjegyzés: Bár a váltógomb alapértelmezett állapota megjelenik a felhasználói felületen az Intune szolgáltatás márciusi frissítése után, az állapot nincs azonnal kényszerítve. A váltógombon elvégzett módosítások nem lesznek hatással az eszközmegfelelőségre mindaddig, amíg nem ellenőrizzük a fiók működő váltógombját. A fiókja tesztelésének befejezéséről az Üzenetközpontban értesítjük. Ez a márciusi Intune-frissítések után néhány napot is igénybe vehet.

**További információ**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Továbbfejlesztett jailbreak-észlelés <!-- 846515 -->

A függetlenítés (jailbreakelés) bővített észlelése egy új megfelelőségi beállítás, amelynek segítségével az Intune hatékonyabban értékelheti a feltört eszközöket. A beállítás révén az eszköznek gyakrabban, a helyalapú szolgáltatások és az akkumulátor fokozott használatával kell bejelentkeznie az Intune-ba.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Jelszavak alaphelyzetbe állítása Android O-eszközökön <!-- 1238299 -->
A munkahelyi profillal rendelkező, regisztrált Android 8.0-eszközökön visszaállíthatja a jelszavakat. Amikor egy „Jelszó visszaállítása” kérelmet küld egy Android 8.0-eszköznek, az egy új eszközfeloldó jelszót vagy egy kezelt profilra vonatkozó kérdést állít be az aktuális felhasználónak. A jelszó vagy a kérdés a küldés után azonnal életbe lép.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Megfelelőségi szabályzatok megcélzása az eszközökhöz az erőforráscsoportok között <!--1307012 -->

A megfelelőségi szabályzatokat felhasználói csoportokban lévő felhasználókra alkalmazhatja. Ezzel a frissítéssel a megfelelőségi szabályzatokat eszközcsoportokban lévő eszközökre alkalmazhatja. Az eszközcsoportok részeként szereplő eszközök nem kapnak megfelelőségi műveletet.

#### <a name="new-management-name-column----1333586---"></a>Új felügyeleti név oszlop <!-- 1333586 -->
 Az Eszközök panelen új oszlop érhető el, **Felügyeleti név** elnevezéssel. Ez egy automatikusan létrehozott, nem szerkeszthető név, amely az alábbi képlet alapján rendelődik hozzá az egyes eszközökhöz:
- Az összes eszköz alapértelmezett neve: <username><em><devicetype></em><enrollmenttimestamp>
- Tömegesen hozzáadott eszközökhöz: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

Ez egy választható oszlop az Eszközök panelen. Alapértelmezés szerint nem érhető el, csak az Oszlopválasztó használatával lehet hozzáférni. Az új oszlop nincs hatással az eszköz nevére.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>az iOS-eszközöket 15 percenként kéri a rendszer a PIN-kód megadására <!--1550837 -->
Miután megfelelőségi vagy konfigurációs szabályzatot alkalmazott egy iOS-eszközre, a felhasználóktól 15 percenként egy PIN-kódot kér a rendszer. A kérések mindaddig megjelennek, amíg a felhasználó nem ad meg egy PIN-kódot.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Automatikus frissítések időzítése <!--1805514 -->
Az Intune-nal igény szerint telepítheti az automatikus frissítéseket a [Windows frissítési köreinek beállításaival](../protect/windows-update-for-business-configure.md). Ezzel a frissítéssel ismétlődő frissítéseket ütemezhet, amelyek a hetet, a napot és az időt is tartalmazzák.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Teljesen megkülönböztető név használata SCEP-tanúsítvány tulajdonosként <!--2221763 -->
SCEP-tanúsítványprofil létrehozásakor meg kell adnia a tulajdonos nevét. Ezzel a frissítéssel használhatja a teljesen megkülönböztető nevet. A **Tulajdonos neve** területen válassza az **Egyéni** lehetőséget, majd írja be a következőt: `CN={{OnPrem_Distinguished_Name}}`. Az `{{OnPrem_Distinguished_Name}}` változó használatához ügyeljen rá, hogy az `onpremisesdistingishedname` felhasználói attribútumot szinkronizálja az Azure AD-vel az [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) segítségével.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Bluetooth-kapcsolat megosztásának engedélyezése – Android for Work <!--1098983 -->
Alapértelmezés szerint az Android megakadályozza a munkahelyi profil névjegyeinek Bluetooth-eszközökkel való szinkronizálását. Ennek eredményeképpen a munkahelyi profil névjegyei nem jelennek meg a hívóazonosítón a Bluetooth-eszközökön.

Ez a frissítés egy új beállítást jelenít meg az **Android for Work** > **Eszközkorlátozások** > **Munkahelyi profil beállításai** területen:
- Névjegyek megosztása Bluetooth-kapcsolattal

Az Intune-rendszergazda konfigurálhatja ezeket a beállításokat a megosztás engedélyezéséhez. Ez akkor hasznos, ha egy eszközt egy autóalapú Bluetooth-eszközzel szeretne párosítani, amely megjeleníti a hívóazonosítót a kihangosítós használat során. Ha a beállítás engedélyezve van, a munkahelyi profil névjegyei megjelennek. Ha a beállítás le van tiltva, a munkahelyi profil névjegyei nem jelennek meg.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Forgalomirányító konfigurálása a macOS-alkalmazás letöltési forrásának vezérléséhez <!-- 1690459 -->

Megvédheti eszközeit a kéretlen alkalmazásoktól a Gatekeeper konfigurálásával, amely szabályozza, hogy mely helyekről tölthetők le alkalmazások. A következő letöltésforrásokat konfigurálhatja: **Mac App Store**, **Mac App Store és azonosított fejlesztők**, vagy **Mindenhonnan**. Azt is beállíthatja, hogy a felhasználók telepíthetnek-e alkalmazásokat úgy. hogy a CTRL + kattintás segítségével felülírják a Gatekeeper szabályozásait.

Ezek a beállítások az **Eszközkonfiguráció** -> **Profil létrehozása** -> **macOS** -> **Endpoint protection** területen találhatók meg.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>A Mac-alkalmazás tűzfalának konfigurálása <!-- 1690461 -->

Konfigurálhatja a Mac-alkalmazástűzfalat. Ennek révén alkalmazásonként, és nem portonként szabályozhatja a kapcsolódásokat. Így könnyebb kihasználni a tűzfalvédelem előnyeit, és meggátolni, hogy kéretlen alkalmazások foglalják le az engedélyezett alkalmazások számára megnyitott hálózati portokat.

Ez a funkció az **Eszközkonfiguráció** -> **Profil létrehozása** -> **macOS** -> **Endpoint protection** területen található meg.

A Tűzfal beállítás engedélyezése után két stratégia szerint konfigurálhatja a tűzfalat:

- Minden bejövő kapcsolat letiltása

   A megcélzott eszközökön letilthat minden bejövő kapcsolatot. Ha emellett dönt, az összes alkalmazás számára le lesznek tiltva a bejövő kapcsolatok.

- Egyes alkalmazások engedélyezése vagy letiltása

   A megadott alkalmazások számára engedélyezheti vagy tilthatja a bejövő kapcsolatok fogadását. A rejtett üzemmód engedélyezésével megakadályozhatja a válaszadást az ellenőrzési kérelmekre.

#### <a name="detailed-error-codes-and-messages----1376342---"></a>Részletes hibakódok és üzenetek <!-- 1376342 -->

A hibakódok és hibaüzenetek részletesebben megtekinthetők az Eszközkonfigurációban. A továbbfejlesztett jelentés bemutatja a beállításokat, azok állapotát és a hibakeresés részleteit.

##### <a name="more-information"></a>További információ

- Minden bejövő kapcsolat letiltása

   Ez a beállítás megakadályozza, hogy a megosztási szolgáltatások (például a fájlmegosztás és a képernyőmegosztás) bejövő kapcsolatokat fogadjanak. A következő rendszerszolgáltatások továbbra is fogadhatnak bejövő kapcsolatokat:
  - configd – DHCP és más hálózati konfigurációs szolgáltatások megvalósítása
  - mDNSResponder – Bonjour megvalósítása
  - racoon – IPSec implementálása

    Megosztási szolgáltatások használata előtt gondoskodjon róla, hogy a **Bejövő kapcsolatok** lehetőség a **Nincs konfigurálva** (és ne a **Letiltás**) értékre legyen beállítva.

- Rejtett üzemmód

   Ha ezt az üzemmódot engedélyezi, a számítógép nem fog válaszolni az ellenőrzési kérelmekre. A számítógép továbbra is válaszol az engedélyezett alkalmazásokhoz tartozó kérelmekre. Az olyan váratlan kérelmeket, mint az ICMP (ping), a rendszer figyelmen kívül hagyja.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Ellenőrzés letiltása az eszköz újraindításakor <!--1805490 -->
Az Intune-nal vezérelheti a [kezelt szoftverfrissítéseket](../protect/windows-update-for-business-configure.md). Ezzel a frissítéssel elérhetővé válik és alapértelmezés szerint hozzá lesz adva az <strong>Újraindítási ellenőrzések</strong> tulajdonság. Az eszközök újraindításakor végzett (például az aktív felhasználókra vagy az akkumulátor szintjére vonatkozó) rendszeres ellenőrzések átugrásához válassza a <strong>Kihagyás</strong> lehetőséget.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Új Windows 10 Insider Preview-csatornák elérhetők üzembe helyezési gyűrűkhöz <!-- 1746293 -->
Mostantól az alábbi Windows 10 Insider Preview-szolgáltatáscsatornákat választhatja Windows 10-es telepítési körök létrehozásakor:
- Windows Insider build &#8208; gyors
- Windows Insider build &#8208; lassú
- A Windows Insider build kiadása 

További információ ezekről a csatornákról: [Az Insider Preview buildek kezelése](https://insider.windows.com/for-business-organization-admin/).   
További információ a telepítési csatornák Intune-beli létrehozásáról: [Szoftverfrissítések kezelése az Intune-ban](../protect/windows-update-for-business-configure.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Új Windows Defender Exploit Guard-beállítások <!-- 1631893 -->

Hat új <strong>Támadási felület csökkentése</strong> beállítás és bővített <strong>Mappahozzáférés felügyelete: Mappavédelem</strong> funkciók érhetők el. Ezeket a beállításokat az alábbi helyen találhatja meg: Eszközkonfiguráció\Profilok\
Profil létrehozása\Endpoint Protection\Windows Defender - biztonsági rés kiaknázása elleni védelem.

#### <a name="attack-surface-reduction"></a>Támadási felület csökkentése

|Beállítás neve  |Beállítás lehetőségei  |Description  |
|---------|---------|---------|
|Zsarolóprogramok elleni speciális védelem|Engedélyezve, Naplózás, Nincs konfigurálva|Zsarolóprogramok elleni agresszív védelem.|
|A Windows helyi biztonsági szervezet alrendszeréből történő hitelesítő adatok lopásának megjelölése|Engedélyezve, Naplózás, Nincs konfigurálva|A Windows helyi biztonsági szervezet alrendszeréből történő hitelesítő adatok lopásának megjelölése (lsass.exe).|
|Folyamatlétrehozás a PSExec- és WMI-parancsokból|Tiltás, Naplózás, Nincs konfigurálva|A PSEx-ec és WMI-parancsokból eredő folyamatlétrehozások letiltása.|
|Nem megbízható és aláíratlan, USB-ről futó folyamatok|Tiltás, Naplózás, Nincs konfigurálva|Nem megbízható és aláíratlan, USB-ről futó folyamatok letiltása.|
|Az elterjedtségre, korra és megbízható listákra vonatkozó kritériumoknak nem megfelelő végrehajtható fájlok|Tiltás, Naplózás, Nincs konfigurálva|Az elterjedtségre, korra és megbízható listákra vonatkozó kritériumoknak nem megfelelő végrehajtható fájlok letiltása.|

#### <a name="controlled-folder-access"></a>Mappahozzáférés felügyelete

|              Beállítás neve               |                                                              Beállítás lehetőségei                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappavédelem (már implementálva) | Nincs konfigurálva, Engedélyezés, Csak naplózás (már implementálva)<br><br> <strong>Új</strong><br>Lemezmódosítás letiltása, lemezmódosítás naplózása |             |

Fájlok és mappák védelme a nemkívánatos alkalmazások által végrehajtott, jogosulatlan módosítások ellen.<br><br>**Engedélyezés**: Megakadályozza, hogy a nem megbízható alkalmazások módosítsák vagy töröljék a védett mappák fájljait, valamint hogy lemezszektorokra írjanak.<br><br>
**Csak a lemezmódosítások letiltása**:<br>Nem engedélyezi a nem megbízható alkalmazásoknak, hogy lemezszektorokra írjanak. A nem megbízható alkalmazások továbbra is módosíthatják vagy törölhetik a védett mappák fájljait.|

### <a name="intune-apps"></a>Intune-alkalmazások

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory webhelyek igénybe vehetik a Intune Managed Browser alkalmazást, és támogatják az egyszeri bejelentkezést a Managed Browserhoz (nyilvános előzetes verzió) <!-- 710595 -->

Az Azure Active Directory (Azure AD) használatával korlátozhatja a webhelyekhez való hozzáférést mobileszközökön az Intune Managed Browser alkalmazással. A felügyelt böngészőben a webhelyadatok biztonságosan lesznek tárolva, és elkülönülnek a felhasználók személyes adataitól. A Managed Browser ezen kívül az Azure AD által védett helyek esetén támogatni fogja az egyszeri bejelentkezést is. A Managed Browserbe való bejelentkezés után, vagy ha a Managed Browsert az Intune által kezelt más alkalmazással használják, lehetővé válik, hogy a Managed Browser használatával anélkül lehessen elérni az Azure AD által védett vállalati helyeket, hogy a felhasználónak meg kellene adnia a hitelesítő adatait. Ez a funkció olyan helyeknél érhető el, mint az Outlook Web Access (OWA) vagy a SharePoint Online, továbbá olyan helyek esetén (például intranet), amelyek az Azure alkalmazásproxyn keresztül érhetőek el. További információ: [hozzáférés-vezérlés Azure Active Directory feltételes hozzáférésben](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Céges portál alkalmazás androidos vizuális frissítésekhez <!--976944 -->

Az Android [Material Design](https://material.io/) irányelveihez igazodva frissítettük az Androidhoz készült Céges portál alkalmazást. Az új ikonok képét [Az alkalmazás felhasználói felületének újdonságai](../whats-new-app-ui.md) cikkben tekintheti meg.

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Céges portál-regisztráció javult <!-- 1874230 eeready-->
A Céges portálon az 1703-as vagy annál újabb verziójú Windows 10 rendszerrel eszközt regisztráló ügyfelek az alkalmazás elhagyása nélkül hajthatják végre a regisztráció első lépését.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>A HoloLens és a Surface Hub mostantól megjelenik az eszközök listájánál <!--1725868 -->
Az Androidhoz készült Céges portál alkalmazás már támogatja az Intune-ban regisztrált HoloLens- és Surface Hub-eszközök megjelenítését.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Mennyiségi vásárlási program-(VPP-) e-könyvek egyéni könyv szerinti kategóriái <!-- 1488911 -->
Egyéni e-könyv-kategóriákat hozhat létre, majd hozzájuk rendelheti a mennyiségi vásárlási programon belüli e-könyveket. A végfelhasználók egyaránt látni fogják az újonnan létrehozott e-könyv-kategóriákat és a hozzájuk rendelt könyveket. További információ: [Mennyiségi programban vásárolt alkalmazások és könyvek kezelése a Microsoft Intune-nal](../apps/vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>A Windows-alkalmazásra vonatkozó Céges portál alkalmazások visszajelzések küldésének támogatása lehetőség <!-- 2070166 -->
2018. április 30-tól a Windows Céges portál **Visszajelzés küldése** funkciója csak a Windows 10 évfordulós frissítését (1607) vagy újabb verziót futtató eszközökön érhető el. Visszajelzés nem küldhető a Windows Céges portál a következő verziókkal történő használatakor:  
- Windows 10, 1507-es kiadás  
- Windows 10, 1511-es kiadás  
- WVPN-profilokdows Phone 8.1 

Ha az eszköze a Windows 10 RS1 és későbbi verziót futtatja, töltse le a Windows Céges portál legújabb verzióját az Áruházból. Ha egy nem támogatott verziót használ, az alábbi csatornákon keresztül küldhet visszajelzést: 
- A Visszajelzési központ alkalmazás Windows 10-en
- E-mail WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Új Windows Defender Application Guard-beállítások <!-- 1631890 -->

- **Grafikus gyorsítás engedélyezése**: A rendszergazdák engedélyezhetik egy virtuális grafikai processzor használatát a Windows Defender alkalmazásőr számára. Ezzel a beállítással a CPU a vGPU-ra terhelheti a grafikai renderelést. Ez javíthatja a teljesítményt a magas grafikai igényű webhelyekkel történő munka, valamint a tárolón belüli videók megtekintése során.

- **SaveFilestoHost**: A rendszergazdák engedélyezhetik a tárolóban futó Microsoft Edge fájljainak a gazdafájlrendszerbe való áttérését. Ennek a beállításnak a bekapcsolásával a felhasználók letölthetik tárolóban futó Microsoft Edge-fájlokat a gazdafájlrendszerbe.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>A felügyeleti állapot alapján megcélozott MAM-védelmi szabályzatok <!-- 1665993 -->
Célzott MAM-szabályzatokat hozhat létre az eszköz felügyeleti állapota alapján:
- **Android-eszközök** – nem felügyelt és Intune által felügyelt eszközöket, valamint Intune által felügyelt Android Enterprise- (korábban Android for Work-) profilokat célozhat meg.
- **iOS-eszközök** – nem felügyelt (csak MAM) vagy Intune által felügyelt eszközöket célozhat meg.

    > [!NOTE]
    > - A funkció iOS-támogatása 2018. áprilisban jelenik meg.

További információ: [Eszközkezelési állapottól függő alkalmazásvédelmi szabályzatok](../apps/app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>A Windows Céges portál alkalmazás nyelvének fejlesztése <!-- 1683758 -->
Fejlesztettük a Windows 10-hez készült Céges portál nyelvét, hogy közérthetőbb és az Ön vállalatára jellemzőbb legyen. Ha meg szeretne tekinteni néhány mintát, lépjen a [Az alkalmazásfelhasználói felület újdonságai](../whats-new-app-ui.md) oldalra.

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>A felhasználói adatvédelemmel kapcsolatos dokumentumok új kiegészítései <!-- 1440709 -->
Szeretnénk nagyobb irányítást adni a felhasználóknak az adataik védelmével kapcsolatban, így frissítettük a Céges portál a helyben tárolt adatok megtekintésére és eltávolítására vonatkozó leírásokat tartalmazó dokumentumokat. A frissítéseket itt tekintheti meg:

- **Android**: [Android-eszköz regisztrációjának törlése az Intune-ból](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, ha a felhasználó nem fogadta el a használati feltételeket**: [Az eszközkezelés eltávolítása, ha nem fogadta el a használati feltételeket](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**: [iOS-eszköz eltávolítása az Intune-ból](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**: [Windows-eszköz eltávolítása az Intune-ból](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>2018. február

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-támogatás több Apple DEP-/Apple School Manager-fiókhoz <!-- 747685 -->

Az Intune mostantól támogatja az eszközök regisztrációját akár 100 különböző [Apple Device Enrollment Program (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) vagy [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md) típusú fiókból. Minden egyes feltöltött token külön használható fel a regisztrációs profilokhoz és eszközökhöz. Automatikusan társíthat másik regisztrációs profilt minden egyes feltöltött DEP/School Manager-tokenhez. Ha több School Manager-tokent tölt fel, egyszerre csak egyet tud megosztani a Microsoft School Data Sync-kel.

Az áttelepítés után az Apple DEP vagy ASM rendszer Graphon keresztüli kezeléséhez használt bétaverziós Graph API-k és közzétett parancsfájlok nem fognak többé működni. Már fejlesztés alatt állnak az új bétaverziós Graph API-k, és az áttelepítés után kiadjuk őket.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Regisztráció korlátozása felhasználónként <!-- 1634444 eeready wnready -->
A **Hibaelhárítás** panelen a **Hozzárendelések** lista [Regisztrációs korlátozások](../enrollment/enrollment-restrictions-set.md) elemét választva megjeleníthetők az egyes felhasználókra vonatkozó **regisztrációs korlátozások**.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Új lehetőség felhasználói hitelesítésre az Apple tömeges beléptetéséhez <!-- 747625 eeready -->

> [!NOTE]
> Ez azonnal látható az új bérlők számára. A meglévő bérlők számára a áprilisban válik elérhetővé a funkció. A bevezetés befejezéséig elképzelhető, hogy nem lehet hozzáférni az új funkciókhoz.

Az Intune mostantól lehetővé teszi az eszközök Céges portál alkalmazással való hitelesítését az alábbi regisztrációs módszerek használatakor:

- Apple Készülékregisztrációs program
- Apple School Manager
- Apple Configurator-regisztráció

A Céges portál lehetőség használatakor kényszerítheti az Azure Active Directory többtényezős hitelesítését anélkül, hogy blokkolná ezen regisztrációs módszereket.

A Céges portál lehetőség választásakor az Intune kihagyja a felhasználóhitelesítést az iOS beállítási asszisztensben, és felhasználói affinitáson alapuló regisztrációt végez. Ez azt jelenti, hogy az eszköz kezdetben felhasználó nélküli eszközként lesz regisztrálva, így nem kapja meg a felhasználói csoportokhoz tartozó konfigurációkat és szabályzatokat. Ehelyett csak az eszközcsoportoktól kap konfigurációkat és szabályzatokat. Az Intune automatikusan telepíti a Céges portál alkalmazást az eszközön. A Céges portál alkalmazást elindító és abba bejelentkező első felhasználót társítja az Intune az eszközhöz. Ezen a ponton a felhasználó már megkapja a felhasználói csoporthoz tartozó konfigurációkat és szabályzatokat. Ezt a felhasználótársítást csak a regisztráció megismétlésével lehet megváltoztatni.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune-támogatás több Apple DEP-/Apple School Manager-fiókhoz <!-- 747685 eeready -->

Az Intune mostantól támogatja az eszközök regisztrációját akár 100 különböző Apple Device Enrollment Program (DEP) vagy Apple School Manager típusú fiókból. Minden egyes feltöltött token külön használható fel a regisztrációs profilokhoz és eszközökhöz. Automatikusan társíthat másik regisztrációs profilt minden egyes feltöltött DEP/School Manager-tokenhez. Ha több School Manager-tokent tölt fel, egyszerre csak egyet tud megosztani a Microsoft School Data Sync-kel.

Az áttelepítés után az Apple DEP vagy ASM rendszer Graphon keresztüli kezeléséhez használt bétaverziós Graph API-k és közzétett parancsfájlok nem fognak többé működni. Már fejlesztés alatt állnak az új bétaverziós Graph API-k, és az áttelepítés után kiadjuk őket.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Távoli nyomtatás biztonságos hálózaton keresztül <!-- 1709994  -->
A PrinterOn vezeték nélküli nyomtatási megoldásaival a felhasználók távolról nyomtathatnak, bárhol és bármikor, egy biztonságos hálózaton keresztül. A PrinterOn integrálva lesz az Intune APP SDK-val mind az iOS, mind pedig az Android rendszerhez. Ehhez az alkalmazáshoz az Intune felügyeleti konzol **Alkalmazásvédelmi szabályzatok** paneljével társíthat alkalmazásvédelmi szabályzatokat. A végfelhasználók letölthetik a „PrinterOn for Microsoft” alkalmazást a Play Áruházból vagy az iTunes áruházból, és használhatják azt az Intune rendszerükben.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>macOS Céges portál az eszköz beléptetési kezelőjét használó regisztrációk támogatása <!-- 1352411 -->

A felhasználók a Készülékregisztráció-kezelővel regisztrálhatnak a macOS Céges portálra.

### <a name="device-management"></a>Eszközkezelés

#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender állapot-és veszélyforrások állapotáról készült jelentések <!--854704 -->

A Windows Defender állapotának megértése kulcsfontosságú a Windows rendszerű számítógépek kezelésében.  Ezzel a frissítéssel az Intune új jelentéseket és tevékenységeket ad hozzá a Windows Defender ügynök állapotához. Ha összesített állapotjelentést használ, az [Eszközmegfelelőségi tevékenységprofil](../protect/compliance-policy-monitor.md) területen azok az eszközök lesznek láthatóak, amelyeknek a következő elemek egyikére van szüksége:
- aláírás-frissítés
- Indítsa újra
- kézi beavatkozás
- teljes vizsgálat
- egyéb, beavatkozást igénylő ügynökállapotok

Az állapotkategóriákhoz tartozó részletes jelentések ismertetik a figyelmet igénylő, illetve a **tisztaként** jelentő számítógépeket.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Az eszközök korlátozásának új adatvédelmi beállításai <!--1308926 -->
Az eszközök számára [két új adatvédelmi beállítás](../configuration/device-restrictions-windows-10.md#privacy) érhető el:
- **Felhasználói tevékenységek közzététele**: A megosztott élmények és a feladatváltóban nemrég használt erőforrások megelőzéséhez ezt a beállítást **tiltsa le**.
- **Csak a helyi tevékenységek**: A csak a helyi tevékenységek alapján megosztott használat és a feladatváltóban nemrég használt erőforrások felderítésének megelőzéséhez ezt a beállítást **tiltsa le**.

#### <a name="new-settings-for-the-microsoft-edge-browser---1469166---"></a>A Microsoft Edge böngésző új beállításai <!--1469166 -->
A Microsoft Edge böngészőt használó eszközök számára [két új beállítás](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser) érhető el: **A kedvencek fájl elérési útja** és **A Kedvencek módosításai**.

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="protocol-exceptions-for-applications---1035509---"></a>Alkalmazások protokoll-kivételeinek <!--1035509 -->

Az Intune mobilalkalmazás-kezelésének (MAM) adatátviteli szabályzatában kivételeket hozhat létre, így megnyithat konkrét nem kezelt alkalmazásokat. Az ilyen alkalmazásoknak az informatikai részleg bizalmát kell élvezniük. A létrehozott kivételen kívül az adatátvitel továbbra is csak azokra az alkalmazásokra korlátozódik, amelyeket az Intune kezel, ha az adatátviteli szabályzat **csak felügyelt alkalmazásokhoz** van konfigurálva. Korlátozásokat protokollokkal (iOS) vagy csomagokkal hozhat létre (Android).

Például hozzáadhatja kivételként a Webex-csomagot az MAM adatátviteli szabályzatához. Ezzel lehetővé teszi a kezelt Outlook-emailek Webex-hivatkozásai számára, hogy közvetlenül a Webex alkalmazásban nyíljanak meg. Az adatátvitel továbbra is korlátozva marad az egyéb nem kezelt alkalmazásokban. További információt [Az adatátviteli szabályzat kivételei alkalmazások esetén](../apps/app-protection-policies-exception.md) című témakörben találhat.

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows Information Protection (folyamatban lévő) titkosított adatforgalom a Windows keresési eredményei között <!-- 1469193 -->
A Windows Információvédelem (WIP) szabályzatban egy beállítás érhető el annak megadásához, hogy a WIP által titkosított adatok megjelenjenek-e a Windows keresési találatai között. Ezt az alkalmazásvédelmi szabályzatot a Windows Információvédelem szabályzatának **Speciális beállításai** között, a **Titkosított elemek keresésének engedélyezése a Windows Search szolgáltatás indexelőprogramjában** lehetőséggel állíthatja be. Az alkalmazásvédelmi szabályzatot a *Windows 10* platformhoz kell beállítani, az alkalmazásszabályzat **Regisztrációs állapot** értékeként pedig a **Regisztrációval** értéket kell megadni. További információ: [Titkosított elemek keresésének engedélyezése a Windows Search szolgáltatás indexelőprogramjában](../apps/windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Saját frissítésű Mobile MSI-alkalmazás konfigurálása <!-- 1740840 -->
Az ismert önfrissítő MSI-mobilalkalmazásokat konfigurálhatja úgy, hogy figyelmen kívül hagyják a verzióellenőrzési folyamatot. Ez a funkció akkor hasznos, ha nem szeretne versenyhelyzetbe kerülni. Ilyen típusú versenyhelyzet például akkor fordulhat elő, ha az alkalmazást egyszerre frissíti automatikusan a fejlesztő és az Intune. Mindkettő megpróbálja kényszeríteni az alkalmazás egy verziójának használatát a Windows-ügyfélen, ami üközést eredményezhet. Az ilyen automatikusan frissített MSI-alkalmazások esetében konfigurálhatja az **Alkalmazásverzió figyelmen kívül hagyása** beállítást az **Alkalmazásadatok** panelen. Ha ezt a beállítást átállítja az **Igen** értékre, a Microsoft Intune nem veszi tekintetbe a Windows-ügyfélen telepített alkalmazás verzióját.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Az Intune-ban támogatott alkalmazás-licencek kapcsolódó készletei <!-- 1864117 -->
Az Azure Portalbeli Intune a felhasználói felület egyedülálló alkalmazáselemeként támogatja a kapcsolódó alkalmazáslicenc-készleteket. Ezenkívül a Vállalati Microsoft Áruházból szinkronizált, offline licencelt alkalmazások egyetlen alkalmazásbejegyzésben lesznek összesítve, az egyes csomagok üzembe helyezési részleteit pedig migráljuk az egyedülálló bejegyzésbe. Ha meg szeretné tekinteni a kapcsolódó alkalmazáslicenc-készleteket az Azure Portalon, válassza az **Ügyfélalkalmazások** panel **Alkalmazáslicencek** lehetőségét.

### <a name="device-configuration"></a>Eszközök konfigurálása
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Windows Information Protection (folyamatban lévő) fájlkiterjesztések az automatikus titkosításhoz <!-- 1463582 -->
A Windows Információvédelem (WIP) szabályzatának egy beállításával megadható, hogy milyen kiterjesztésű fájlok legyenek automatikusan titkosítva, ha Server Message Block (SMB) megosztásról másolják őket a vállalatnak a WIP-szabályzat alapján meghatározott területén belül.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Erőforrásfiók-beállítások konfigurálása a Surface Hubokban

A Surface Hubok erőforrásfiók-beállításai távolról konfigurálhatók.

A Surface Hub az erőforrásfiókkal hitelesíthető a Skype/Exchange felé, így bekapcsolódhat az értekezletbe.
Célszerű létrehozni egy egyedi erőforrásfiókot, hogy a Surface Hub konferenciateremként jelenjen meg az értekezletben.
Az erőforrásfiók megjelenhet például **Konferenciaterem B41/6233** néven.

> [!NOTE]
> - Ha üresen hagy egyes mezőket, azzal felülírja a korábban konfigurált eszközattribútumokat.
>
> - Az erőforrásfiók tulajdonságai dinamikusan változhatnak a Surface Hubon. Például ha be van kapcsolva a jelszóváltoztatás. Így előfordulhat, hogy az Azure-konzol értékei csak egy kis idő múlva jelennek meg valós értékekként az eszközön.
>
>   Ha meg szeretné tekinteni a Surface Hub aktuálisan konfigurált beállításait, az erőforrásfiók adatait belefoglalhatja a hardverleltárba (amely jelenleg egy 7 napos intervallummal bír), vagy megjelenítheti azokat írásvédett tulajdonságokként. A távoli művelet után a pontosság javítása érdekében lekérheti a paramétereket közvetlenül a művelet futtatása után, így frissítheti a Surface Hub fiókját vagy paramétereit.

##### <a name="attack-surface-reduction"></a>Támadási felület csökkentése

|Beállítás neve  |Beállítás lehetőségei  |Description  |
|---------|---------|---------|
|Jelszóval védett végrehajtható tartalom futtatása e-mailből|Tiltás, Naplózás, Nincs konfigurálva|E-mailből letöltött jelszóval védett végrehajtható fájlok futtatásának megakadályozása.|
|Zsarolóprogramok elleni speciális védelem|Engedélyezve, Naplózás, Nincs konfigurálva|Zsarolóprogramok elleni agresszív védelem.|
|A Windows helyi biztonsági szervezet alrendszeréből történő hitelesítő adatok lopásának megjelölése|Engedélyezve, Naplózás, Nincs konfigurálva|A Windows helyi biztonsági szervezet alrendszeréből történő hitelesítő adatok lopásának megjelölése (lsass.exe).|
|Folyamatlétrehozás a PSExec- és WMI-parancsokból|Tiltás, Naplózás, Nincs konfigurálva|A PSEx-ec és WMI-parancsokból eredő folyamatlétrehozások letiltása.|
|Nem megbízható és aláíratlan, USB-ről futó folyamatok|Tiltás, Naplózás, Nincs konfigurálva|Nem megbízható és aláíratlan, USB-ről futó folyamatok letiltása.|
|Az elterjedtségre, korra és megbízható listákra vonatkozó kritériumoknak nem megfelelő végrehajtható fájlok|Tiltás, Naplózás, Nincs konfigurálva|Az elterjedtségre, korra és megbízható listákra vonatkozó kritériumoknak nem megfelelő végrehajtható fájlok letiltása.|

##### <a name="controlled-folder-access"></a>Mappahozzáférés felügyelete

|              Beállítás neve               |                                                              Beállítás lehetőségei                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappavédelem (már implementálva) | Nincs konfigurálva, Engedélyezés, Csak naplózás (már implementálva)<br><br> <strong>Új</strong><br>Lemezmódosítás letiltása, lemezmódosítás naplózása |             |

Fájlok és mappák védelme a nemkívánatos alkalmazások által végrehajtott, jogosulatlan módosítások ellen.<br><br>**Engedélyezés**: Megakadályozza, hogy a nem megbízható alkalmazások módosítsák vagy töröljék a védett mappák fájljait, valamint hogy lemezszektorokra írjanak.<br><br>
**Csak a lemezmódosítások letiltása**:<br>Nem engedélyezi a nem megbízható alkalmazásoknak, hogy lemezszektorokra írjanak. A nem megbízható alkalmazások továbbra is módosíthatják vagy törölhetik a védett mappák fájljait.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>A Windows 10 és újabb megfelelőségi szabályzatok rendszerbiztonsági beállításainak kiegészítése <!--1704133-->

Elérhető a Windows 10 megfelelőségi beállításainak bővítése, amely a tűzfalat és a Windows Defender víruskeresőt is kötelezővé teszi.

### <a name="intune-apps"></a>Intune-alkalmazások

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>A vállalati Microsoft Store offline alkalmazásainak támogatása <!--1222672-->
A Vállalati Microsoft Áruházban vásárolt offline alkalmazások mostantól szinkronizálhatók az Azure Portallal. Ezeket az alkalmazásokat eszközcsoportok vagy felhasználói csoportok számára telepítheti. Az offline alkalmazásokat az Intune, és nem az Áruház telepíti.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>A munkahelyi profilban lévő fiókok manuális hozzáadásának vagy eltávolításának megakadályozása a végfelhasználók számára <!-- 1728700 -->

A Gmail alkalmazás egy Android for Work-profilba történő telepítésekor az Android for Work Eszközkorlátozások profiljának **Fiók hozzáadása és eltávolítása** beállítása segítségével megakadályozható, hogy a végfelhasználók manuálisan fiókokat adjanak hozzá vagy távolítsanak el.

<!-- ########################## -->
## <a name="january-2018"></a>2018. január

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Riasztások a hamarosan lejáró lejárt jogkivonatok és tokenek esetén <!-- 1639263 -->
Az áttekintő lap mostantól riasztást jelenít meg a lejárt és hamarosan lejáró tokenekről. Az egyes tokenekhez tartozó riasztásra kattintva elérheti a token részleteinek lapját.  Ha több tokenről szóló riasztásra kattint, akkor a rendszer megjeleníti az adott állapotú tokenek listáját. A rendszergazdáknak meg kell újítaniuk a tokenjeiket, mielőtt lejárnának.

### <a name="device-management"></a>Eszközkezelés

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Távoli "Törlés" parancs támogatása macOS-eszközökhöz <!-- 1438084 -->

A rendszergazdák távolról is kiadhatnak törlési parancsot a macOS rendszerű eszközökön.

> [!IMPORTANT]
> A törlési parancs nem vonható vissza, ezért legyen óvatos a használatakor.

A törlési parancs eltávolítja az összes adatot az eszközről, az operációs rendszert is ideértve. Emellett az Intune-ból is eltávolítja az eszközt. Nem jelenik meg figyelmeztetés a felhasználónak, és a törlés a parancs kiadása után azonnal megkezdődik.

Be kell állítania egy 6 számjegyből álló helyreállítási PIN-kódot. Ezzel a PIN-kóddal feloldhatja az eszköz zárolását a törlést követően, mely után megkezdődik az operációs rendszer újratelepítése. A törlés megkezdése után megjelenik a PIN-kód az eszköz Intune-beli áttekintő paneljén. A PIN-kód a törlés végrehajtása alatt végig látható marad. A törlés után az eszköz eltűnik az Intune rendszerből. Ne felejtse el feljegyezni ezt a helyreállítási PIN-kódot az eszköz helyreállítását végző személy számára.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>IOS Volume beszerzési programbeli jogkivonat licencének visszavonása <!-- 820870 -->
Visszavonhatja az adott VPP-tokenhez tartozó összes iOS Volume Purchasing Program-alkalmazás (VPP-alkalmazás) licencét.

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>IOS mennyiségi vásárlási programbeli alkalmazások visszavonása  <!-- 820863 -->
Ha egy adott eszközhöz egy vagy több iOS Volume Purchase Program-alkalmazás is tartozik, akkor visszavonhatja az eszköztől az eszközalapú alkalmazáslicencet. Az alkalmazáslicenc visszavonása nem törli a vonatkozó VPP-alkalmazást az eszközről. A VPP-alkalmazás törléséhez az **Eltávolítás** műveletre kell módosítania a hozzárendelési műveletet. További információért olvassa el a [Mennyiségi vásárlási program keretében vásárolt iOS-alkalmazások kezelése a Microsoft Intune-nal](../apps/vpp-apps-ios.md) című témakört.

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Office 365 Mobile-alkalmazások kiosztása iOS-és Android-eszközökhöz beépített alkalmazás-típus használatával <!-- 1332318 -->
A **Beépített** alkalmazástípussal könnyebben hozhat létre és rendelhet Office 365-alkalmazásokat a felügyelt iOS- és Android-eszközeihez. Ezek az alkalmazások olyan 0365-alkalmazásokat tartalmaznak, mint a Word, az Excel, a PowerPoint és a OneDrive. Az alkalmazástípushoz konkrét alkalmazásokat rendelhet hozzá, valamint szerkesztheti az alkalmazásadatok konfigurációját.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Alkalmazások hozzárendelésének belefoglalása és kizárása csoportok alapján <!-- 1406920 -->

Az alkalmazások társítása során, illetve a társítás típusának kiválasztása után megadhatja a belefoglalni, valamint a kizárni kívánt csoportokat.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Az alkalmazás-konfigurációs szabályzatot hozzárendelheti a csoportokhoz a hozzárendelések belefoglalásával és kizárásával is  <!-- 1480316 -->

A hozzárendelések belefoglalásának és kizárásának kombinációjával alkalmazáskonfigurációs szabályzatot rendelhet a felhasználók és eszközök egy csoportjához. A hozzárendeléseket vagy egyénileg kijelölt csoportokként, vagy virtuális csoportként lehet kiválasztani. A virtuális csoportok a következőket tartalmazhatják: **Minden felhasználó**, **Minden eszköz**, és **Minden felhasználó és minden eszköz**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>A Windows 10 kiadás frissítési szabályzatának támogatása   <!-- 903672(archived), 1119689 -->  
A Windows 10-hez létrehozhat olyan kiadásfrissítési szabályzatot, amely a Windows 10-es eszközöket az alábbi verziókra frissíti: Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education és Windows 10 Professional Education N. A Windows 10 kiadásfrissítéseiről a [Windows 10 kiadásfrissítéseinek konfigurálása](../configuration/edition-upgrade-configure-windows-10.md) című témakörből tájékozódhat.

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Az Intune-hoz tartozó feltételes hozzáférési szabályzatok csak a Azure Portal érhetők el  <!-- 1737088 1634311 -->

Ettől a kiadástól kezdődően feltételes hozzáférési szabályzatok konfigurálására és felügyeletére az [Azure Portal ](https://portal.azure.com) **Azure Active Directory** > **Feltételes hozzáférés** menüpontjában van lehetőség. A kényelmes használat céljából ez a panel az Intune-ban is elérhető az Azure Portal **Intune** > **Feltételes hozzáférés** menüpontjában.

#### <a name="updates-to-compliance-emails---1637547---"></a>A megfelelőségi e-mailek frissítései <!--1637547 -->

A nem megfelelő eszközökről értesítő e-mailekben szerepelnek a nem megfelelő eszközök adatai.

### <a name="intune-apps"></a>Intune-alkalmazások

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Új funkciók a "Feloldás" művelethez Android-eszközök esetén <!--1583480-->

Az Androidhoz készült Céges portál alkalmazás bővíti az **eszközbeállítások frissítése** esetén használható „Feloldás” műveletet az [eszköztitkosítási problémák](/intune-user-help/encrypt-your-device-android) megoldásához.

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>A távoli zárolás elérhető Céges portál alkalmazásban Windows 10 rendszeren <!--676506-->
A végfelhasználók mostantól távolról zárolhatják az eszközeiket a Windows 10-es Céges portál alkalmazásból. Ez nem jelenik meg a helyi eszközön, amit aktívan használnak.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>A Windows 10-es Céges portál alkalmazás megfelelőségi problémáinak egyszerűbb megoldása <!--676546-->
A Windows-eszközök végfelhasználói mostantól rá tudnak koppintani a Céges portál alkalmazásban az okra, amely miatt az eszköz nem felel meg valamelyik biztonsági szabálynak. Amikor csak lehetséges, ennek hatására meg fog jelenni az a beállítási képernyő, ahol kezelhető a probléma.

<!-- ########################## -->
## <a name="december-2017"></a>2017. december

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Új automatikus újratelepítési beállítás <!-- 1469168 -->
Az **Automatikus újbóli üzembe helyezés** beállítás lehetővé teszi a rendszergazdai jogosultságokkal rendelkező felhasználóknak, hogy az eszköz zárolási képernyőjén a **CTRL + Win + R** billentyűkombinációval törölhessék az összes felhasználói adatot és beállítást. Ennek hatására automatikusan megtörténik az eszköz újbóli konfigurálása és regisztrálása felügyeletre. A beállítás a Windows 10 > Eszközkorlátozások > Általános > Automatikus újbóli üzembe helyezés menüpontban található. További részletekért lásd: [Eszközkorlátozásokra vonatkozó beállítások az Intune-ban Windows 10 esetén](../configuration/device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>További forrásoldali kiadások támogatása a Windows 10 kiadás frissítési szabályzatában  <!-- 903672,  1119689 -->
Mostantól a Windows 10 kiadásfrissítési szabályzatával további Windows 10-kiadásokról is frissíthet (például Windows 10 Pro, Windows 10 Pro Education és Windows 10 Cloud). Korábban a támogatott kiadásfrissítési útvonalak korlátozottabbak voltak. További információért lásd: [A Windows 10 kiadásfrissítéseinek konfigurálása](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Új Windows Defender Security Center (WDSC) eszköz konfigurációs profiljának beállításai <!-- 1335507 -->

Az Intune eszközkonfigurációs profiljának beállításai új szakasszal bővültek. Ez a **Windows Defender biztonsági központ** néven szerepel az Endpoint Protection szakasznál. A rendszergazdák beállíthatják, hogy a Windows Defender biztonsági központ alkalmazás mely területei legyenek elérhetők a végfelhasználók számára. Ha a rendszergazda elrejti a Windows Defender biztonsági központ valamelyik területét, a felhasználó eszközén nem fognak megjelenni az adott területtel kapcsolatos értesítések.

A rendszergazdák a következő területeket rejthetik el a Windows Defender biztonsági központ eszközkonfigurációs profilbeállításai közül:
- Vírusok és veszélyforrások elleni védelem
- Eszközteljesítmény és -állapot
- Tűzfal és hálózatvédelem
- Alkalmazás- és böngészővezérlés
- Családi beállítások

A rendszergazdák azt is személyre szabhatják, hogy a felhasználók melyik értesítéseket kapják meg. Beállítható például, hogy a felhasználók a Windows Defender biztonsági központ összes látható területének értesítéseit megkapják, vagy csak a kritikus értesítéseket. A nem kritikus értesítések közé tartoznak a Windows Defender víruskereső rendszeres összefoglalói és a vizsgálatok befejezését jelző értesítések. Minden más értesítés kritikusnak minősül. Emellett testre is szabhatja az értesítések tartalmát, például a rendszergazda elérhetőségét beágyazhatja a felhasználók eszközein megjelenő értesítések szövegébe.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Több összekötő támogatása a SCEP és a PFX-tanúsítványok kezelésére <!-- 1361755 -->

Azok az ügyfeleink, akik helyszíni NDES-összekötővel kézbesítik a tanúsítványokat az eszközökre, mostantól több összekötőt is beállíthatnak egy bérlőben.

Ez az új funkció támogatja az alábbi forgatókönyvet:

- **Magas rendelkezésre állás**

Az egyes NDES-összekötők lekérik a tanúsítványkérelmeket az Intune-ból.  Ha az egyik NDES-összekötő offline állapotba kerül, a másik összekötő folytathatja a kérelmek feldolgozását.

#### <a name="customer-subject-name-can-use-aad_device_id-variable-----1468599---"></a>Az ügyfél tulajdonosának neve AAD_DEVICE_ID változót is használhat  <!-- 1468599 -->

Az SCEP-tanúsítványprofilok Intune-ban való létrehozásakor mostantól használhatja az AAD_DEVICE_ID változót az egyéni tulajdonosnevek létrehozásakor.   Az ilyen SCEP-profillal való tanúsítványkéréskor a rendszer lecseréli a változót a tanúsítványkérelmező eszköz AAD-eszközazonosítójára.


### <a name="device-management"></a>Eszközkezelés

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>JAMF által regisztrált macOS-eszközök kezelése az Intune eszköz-megfelelőségi motorral <!-- 1592747 -->
Mostantól a Jamf a macOS-eszközök eszközállapotát is elküldheti az Intune-nak, az pedig vizsgálni fogja, hogy megfelelnek-e az eszközök az Intune konzolban meghatározott szabályzatoknak. Az eszköz megfelelőségi állapota, valamint más feltételek (például a hely, a felhasználói kockázat stb.) alapján a feltételes hozzáférés kikényszeríti az Azure AD-vel összekapcsolt Felhőbeli és helyszíni alkalmazásokhoz (például az Office 365-hoz) hozzáférő macOS-eszközök megfelelőségét. Tudjon meg többet [a Jamf-integráció beállításáról](../protect/conditional-access-integrate-jamf.md) és [a Jamf által felügyelt eszközök megfelelőségének kényszerítéséről](../protect/conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Új iOS-eszköz művelete   <!-- 1424701 -->

Mostantól leállíthatja az iOS 10.3 rendszerű felügyelt eszközöket. Ez a művelet azonnal leállítja az eszközt, anélkül, hogy a végfelhasználót figyelmeztetné. A **Leállítás (csak felügyelt eszköz esetén)** műveletet az eszköztulajdonságoknál találhatja, amikor kiválaszt egy eszközt az **Eszköz** tevékenységprofilban.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Dátum-és időmódosítások letiltása Samsung Knox-eszközökön <!-- 1468103 -->

Bevezettünk egy új funkciót, melynek segítségével letilthatja a dátum- és időmódosítást a Samsung Knox-eszközökön. Ezt a következő területen találhatja meg: **Eszközkonfigurációs profilok** > **Eszközkorlátozások (Android)**  > **Általános**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Surface Hub erőforrás-fiók támogatott <!-- 1566442  -->

Egy új eszközművelet segítségével mostantól a rendszergazdák megadhatják és frissíthetik a Surface Hubhoz társított erőforrásfiókot.

A Surface Hub az erőforrásfiókkal hitelesíthető a Skype/Exchange felé, így bekapcsolódhat az értekezletbe. Létrehozhat egy egyedi erőforrásfiókot, hogy a Surface Hub konferenciateremként jelenjen meg az értekezletben. Az erőforrásfiók megjelenhet például *Konferenciaterem B41/6233* néven. A Surface Hub-erőforrásfiókot (vagyis az eszközfiókot) általában a konferencia helyszínéhez kell beállítani akkor, amikor az erőforrásfiók egyéb paramétereit is meg kell változtatni.

Ha a rendszergazdák megpróbálják frissíteni az eszköz erőforrásfiókjának adatait, meg kell adniuk az eszközhöz rendelt Active Directory-beli/Azure Active Directory-beli hitelesítő adatokat. Ha az eszköznél jelszóváltoztatás van beállítva, a rendszergazdának az Azure Active Directoryban kell megkeresnie a jelszót.

> [!NOTE]
> A mezőket egy csomagban küldi el a rendszer, és az összes korábban beállított mező értékét felülírja. Az üres mezők is felülírják a meglévő mezőket.

A rendszergazdák a következő beállításokat konfigurálhatják:

- **Erőforrásfiók**
  - **Active Directory-felhasználó**

    Tartománynév\felhasználónév vagy egyszerű felhasználónév (UPN): user@domainname.com

  - **Jelszó**

- **További nem kötelezően kitöltendő erőforrásfiók-paraméterek**  (az adott erőforrásfiókkal kell beállítani)

  - **Jelszóváltoztatás gyakorisága**

    Gondoskodik róla, hogy a fiók jelszavát a Surface Hub biztonsági okokból minden héten automatikusan frissítse. A funkció bekapcsolását követően a további paraméterek beállításához új jelszót kell kérni a fiókhoz az Azure Active Directoryban.

  - **SIP-cím**

    Csak abban az esetben szükséges, ha az automatikus felfedezés sikertelen.

  - **E-mail**

    Az eszköz/erőforrásfiók e-mail-címe.

  - **Exchange-kiszolgáló**

    Csak abban az esetben szükséges, ha az automatikus felfedezés sikertelen.

  - **Naptár-szinkronizálás**

    A naptár-szinkronizálás és más Exchange Server-szolgáltatások engedélyezését teszi lehetővé. Például: értekezlet-szinkronizálás.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Office-alkalmazások telepítése macOS-eszközökön <!-- 1494311 -->
Mostantól macOS-eszközökre is telepíthetők az Office-alkalmazások. Az új alkalmazástípusnak köszönhetően telepíteni lehet a Word, az Excel, a PowerPoint, az Outlook és a OneNote alkalmazást. Az alkalmazások a Microsoft AutoUpdater (MAU) szolgáltatást is tartalmazzák, amely segít a biztonság megőrzésében és az alkalmazások folyamatos frissítésében.

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>IOS Volume beszerzési programbeli token törlése <!-- 820879 -->
A konzol segítségével törölheti az iOS Volume Purchasing Program (VPP) tokenjét. Ez akkor lehet szükséges, ha egy VPP-token több példányban van meg.

### <a name="intune-apps"></a>Intune-alkalmazások


### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Az aktuális felhasználó nevű új entitás jelenleg aktív felhasználói adatként van korlátozva <!-- 1667026 -->

A **Felhasználók** entitásgyűjtemény a vállalaton belül hozzárendelt licenccel rendelkező összes Azure Active Directory- (Azure AD-) felhasználót tartalmazza. Például az elmúlt egy hónap során hozzáadhattak az Intune-hoz egy felhasználót, majd el is távolíthatták onnan. A felhasználó a jelentés időpontjában nincs jelen, de az adatok tartalmazzák a felhasználót és állapotát. Ekkor létrehozhat egy olyan jelentést, amely megjeleníti a felhasználó korábbi jelenlétének időtartamát az adatokban.

Ezzel szemben az új **Aktuális felhasználó** entitásgyűjtemény csak azokat a felhasználókat tartalmazza, akiket nem távolítottak el. Az **Aktuális felhasználó** entitásgyűjtemény csak a jelenleg aktív felhasználókat tartalmazza. Az **Aktuális felhasználó** entitásgyűjteménnyel kapcsolatban az [Aktuális felhasználó típusú entitás referenciája](../developer/reports-ref-data-model.md) oldalon talál további információkat.

### <a name="updated-graph-apis----1736360---"></a>Frissített Graph API-k <!-- 1736360 -->

A jelen kiadásban frissítettük az Intune-hoz készült bétaverziós Graph API-k egy részét. További információt a [Graph API havi változásnaplójában](https://developer.microsoft.com/graph/docs/concepts/changelog) találhat.

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Az Intune támogatja a Windows Information Protection (folyamatban lévő) alkalmazások megtagadását <!-- 1479103 -->
A tiltott alkalmazásokat az Intune-ban lehet meghatározni. Tiltás esetén az adott alkalmazás nem férhet hozzá vállalati információkhoz, ellentétben az engedélyezett listán lévő alkalmazásokkal. További információért lásd: [A Windows Information Protection ajánlott letiltási listája](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).

<!-- ########################## -->
## <a name="november-2017"></a>2017. november

### <a name="troubleshoot-enrollment-issues-----746324---"></a>Regisztrálási problémák elhárítása  <!-- 746324 -->

A **Hibaelhárítás** munkaterületen mostantól megtalálhatók a felhasználói regisztrálással kapcsolatos problémák. A hiba adatai és a megoldáshoz javasolt lépések segítséget nyújtanak a rendszergazdának és az ügyfélszolgálati munkatársaknak a hibalehárításban. A rendszer nem jegyez fel minden regisztrálási hibát, és bizonyos hibáknál nem kínál fel megoldási javaslatokat.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Csoporthoz rendelt regisztrációs korlátozások <!-- 747598 -->

Intune-rendszergazdaként mostantól létrehozhat [egyéni, eszköztípusra és eszközkorlátra vonatkozó regisztrációs korlátozásokat a felhasználói csoportok számára](../enrollment/enrollment-restrictions-set.md).

Az Intune Azure Portalon akár 25 példányt hozhat létre az egyes korlátozástípusokból, amelyeket aztán felhasználói csoportokhoz rendelhet. A csoportkorlátozások felülírják az alapértelmezett korlátozásokat.

Egy korlátozástípus minden példánya egy szigorúan rendezett listában található. Ez a sorrend határozza meg az ütközések feloldásának prioritási értékét. Azokra a felhasználókra, akiket egynél több korlátozáspéldány érint, csak a legmagasabb prioritási értékkel rendelkező példány korlátozása vonatkozik. Egy adott példány prioritását a listán való húzással módosíthatja.

Ez a funkció az Android for Work-beállítások az Android for Work-regisztráció menüjéből a Regisztrációs korlátozások menübe való migrálásának során jelenik meg. Mivel a migrálás több napig is eltarthat, előfordulhat, hogy a fiókja a novemberi kiadás többi részére vonatkozóan frissül, a Regisztrációs korlátozások csoport-hozzárendelés funkciója azonban még nem jelenik meg.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Több hálózati eszközök tanúsítványigénylési szolgáltatásának (NDES) támogatása <!-- 1528104 -->

A hálózati eszközök tanúsítványigénylési szolgáltatása (NDES) lehetővé teszi a mobileszközökön tartományi hitelesítő adatok nélkül futó szoftverek számára, hogy az egyszerű tanúsítványigénylési protokoll (SCEP) alapján tanúsítványokat szerezzenek be.
Ez a frissítés több NDES-összekötő támogatását teszi lehetővé.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android for Work-eszközök kezelése az Android-eszközöktől függetlenül <!-- 1490731 EEready-->

Az Intune támogatja az Android for Work-eszközök regisztrációjának az Android-platformtól független kezelését. Ezek a beállítások az **Eszközregisztráció** > **Regisztrációs korlátozások** > **Eszköztípus-korlátozások** területen kezelhetők. (Korábban az **Eszközregisztráció** > **Android for Work-regisztráció** > **Az Android for Work regisztrációs beállításai** területen voltak elérhetők.)

Alapértelmezés szerint az Android for Work-eszközök beállításai ugyanazok, mint az Android-eszközöké. Az Android for Work-beállítások módosítása után ez azonban már nem lesz így.

Ha letiltja a személyes Android for Work-regisztrációt, csak a vállalati Android-eszközök regisztrálhatók Android for Work-eszközként.

Az új beállítások használata során vegye figyelembe a következőket:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Ha még soha nem végzett előkészítést Android for Work-regisztrációhoz

Az új Android for Work-platform le van tiltva az alapértelmezett Eszköztípus-korlátozások beállításban. A funkció előkészítése után engedélyezheti az eszközök számára az Android for Work-regisztrációt. Ehhez meg kell változtatnia az alapértelmezett korlátozást, vagy létre kell hoznia egy új eszköztípus-korlátozást, amely felülírja az alapértelmezett eszköztípus-korlátozást.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Ha már végzett előkészítést Android for Work-regisztrációhoz

Ha már korábban végzett előkészítést, a további lépések a választott beállításoktól függnek:

| Beállítás | Az Android for Work állapota az alapértelmezett Eszköztípus-korlátozás beállításban | Megjegyzések |
| --- | --- | --- |
| **Minden eszköz felügyelete Android-eszközként** | Blokkolt | Minden Android-eszköznek regisztrálnia kell az Android for Work nélkül. |
| **Minden támogatott eszköz felügyelete Android for Work-eszközként** | Engedélyezett | Minden, az Android for Worköt támogató Android-eszközt regisztrálni kell az Android for Workkel. |
| **Csak a megadott csoportokban szereplő felhasználók támogatott eszközeinek felügyelete Android for Work-eszközként** | Blokkolt | Létrejött egy különálló eszköztípus-regisztrációs szabályzat, amely felülírja az alapértelmezettet. Ez a szabályzat határozza meg a korábban az Android for Work-beléptetés engedélyezéséhez kiválasztott csoportokat. A kiválasztott csoportok felhasználói továbbra is regisztrálhatják az Android for Work-eszközeiket. A többi felhasználó nem regisztrálhat eszközöket az Android for Workkel. |

A kívánt szabály minden esetben megmarad. Önnek nem kell semmilyen további lépést végeznie a környezetében az Android for Work globális vagy csoportonkénti engedélyezésének fenntartásához.

### <a name="google-play-protect-support-on-android----908720---"></a>Google Play Protect-támogatás Androidon <!-- 908720 -->

Az Android Oreo megjelenésétől kezdve a Google egy új védelmi funkciót vezetett be Google Play Protect néven, amely lehetővé teszi, hogy a felhasználók és a szervezetek biztonságos alkalmazásokat és biztonságos Android-rendszerképeket futtassanak. Az Intune mostantól támogatja a Google Play Protect-funkciókat, például a SafetyNet távoli igazolást. A rendszergazdák olyan megfelelőségi szabályzatokat állíthatnak be, amelyek megkövetelik a Google Play Protect konfigurálását és biztonságos állapotát.
A **SafetyNet eszközigazolás** beállítás azt követeli meg, hogy az eszköz kapcsolódjon egy Google-szolgáltatáshoz, amely igazolja, hogy az eszköz a biztonságot tekintve kifogástalan állapotban van. Android for Work esetén a rendszergazda megadhat egy olyan konfigurációs profilbeállítást is, amely megköveteli, hogy a telepített alkalmazások állapotát Google Play-szolgáltatások ellenőrizzék. Ha egy eszköz nem felel meg a Google Play Protect követelményeinek, a feltételes hozzáférés megakadályozhatja, hogy a felhasználók hozzáférjenek a vállalati erőforrásokhoz.

- Lásd: [Eszközmegfelelőségi szabályzat létrehozása a Google Play Protect engedélyezéséhez ‒ útmutató](../protect/compliance-policy-create-android.md).

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Felügyelt alkalmazások által engedélyezett szöveges protokoll <!-- 1414050  -->

Az Intune App SDK által felügyelt alkalmazások SMS-eket küldhetnek.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Az alkalmazás telepítésére vonatkozó jelentés frissítve, hogy tartalmazza a telepítés függőben állapotát <!-- 1249446 -->  

Az **Alkalmazás telepítésének állapota** jelentés, amely az **Ügyfélalkalmazások** terület **Alkalmazás** listájában tekinthető meg az egyes alkalmazásokhoz, mostantól tartalmazza a **Telepítés függőben** állapotot is a felhasználókra és az eszközökre vonatkozóan.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>iOS 11 app Inventory API mobil veszélyforrások észleléséhez <!-- 1391759 -->

Az Intune mind a személyes, mind a vállalati tulajdonban lévő eszközöktől alkalmazásleltár-adatokat gyűjt, amelyeket elérhetővé tesz a Mobil fenyegetésészlelés szolgáltatói, például a Lookout for Work számára. Az alkalmazásleltárt iOS 11 vagy újabb operációs rendszerrel rendelkező felhasználóktól gyűjtheti be.

**Alkalmazásleltár**  
Az Intune mind a személyes, mind a vállalati tulajdonban lévő, iOS 11 vagy újabb operációs rendszerű eszközöktől alkalmazásleltár-adatokat küld az Ön Mobil fenyegetésészlelés-szolgáltatójának. Az alkalmazásleltár adatai az alábbiakat tartalmazzák:

- Alkalmazásazonosító
- Alkalmazásverzió
- Alkalmazás rövid verziója
- Alkalmazásnév
- Alkalmazás csomagjának mérete
- Alkalmazás dinamikus mérete
- Az alkalmazás ellenőrzési állapota
- Az alkalmazás felügyeleti állapota

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Hibrid MDM-felhasználók és-eszközök migrálása az önálló Intune-ba <!-- 1463747 wnready -->
Az Azure Portalon mostantól új folyamatok és eszközök érhetők el a felhasználók és eszközeik hibrid MDM-ből Intune-ba való áthelyezésének elvégzéséhez, melyekkel az alábbiakra van lehetősége:
- Szabályzatok és profilok másolása a Configuration Manager-konzolból az Intune-ba az Azure Portal használatával
- Felhasználók részhalmazának áthelyezése az Intune-ba az Azure Portal használatával, miközben a többi felhasználó a hibrid MDM-ben marad
- Eszközök migrálása az Intune-ba az Azure Portal használatával újbóli regisztráció nélkül

A részletekért lásd: [Hibrid MDM-felhasználók és -eszközök migrálása az önálló Intune szolgáltatásba](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Magas rendelkezésre állású helyszíni Exchange Connector támogatása  <!-- 676614 -->
Miután az Exchange Connector létrehoz egy kapcsolatot az Exchange-lel a megadott ügyfél-hozzáférési kiszolgáló (CAS) használatával, az összekötő mostantól képes a többi CASs felderítésére. Ha az elsődleges CAS elérhetetlenné válik, az összekötő átvált egy másik CAS-ra (ha elérhető), amíg az elsődleges CAS elérhetősége helyre nem áll. További információért lásd: [Magas rendelkezésre állású helyszíni Exchange Connector támogatása](../protect/exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>IOS-eszköz távoli újraindítása (csak felügyelt eszköz esetén) <!-- 1424595 -->

Eszközművelettel újraindíthat egy felügyelt, iOS 10.3 vagy újabb operációs rendszerű eszközt. További információ az eszköz-újraindítás műveletről: [Az eszközök távoli újraindítása az Intune-nal](../remote-actions/device-restart.md).

> [!Note]
> Ehhez a parancshoz felügyelt eszközökre és az **Eszközzárolás** hozzáférési jogosultságra van szükség. Az eszköz azonnal újraindul. A PIN-kóddal zárolt iOS-eszközök nem csatlakoznak újra a Wi-Fi-hálózatokra az újraindítás után, így előfordulhat, hogy ilyen esetekben nem tudnak kommunikálni a kiszolgálóval.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Egyszeri bejelentkezés támogatása iOS rendszerhez <!-- 1333645 -->  

Az iOS-felhasználók is használhatják az egyszeri bejelentkezést. Azok az iOS-alkalmazások, amelyek az egyszeri bejelentkezés hasznos forgalmában található felhasználói hitelesítő adatok keresésére vannak kódolva, ezzel a hasznosforgalom-konfigurációs frissítéssel fognak működni. Emellett az egyszerű felhasználónévvel és az Intune-eszközazonosítóval is konfigurálhatja az egyszerű nevet és a tartományt. A részletekért lásd: [Az Intune konfigurálása egyszeri bejelentkezéshez iOS-es eszközökön](../configuration/ios-device-features-settings.md#single-sign-on).

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Az "iPhone megkeresése" elem hozzáadása a személyes eszközökhöz <!--1427287-->
Mostantól megtekintheti, hogy az iOS-eszközökön be van-e kapcsolva az aktiválási zár. Ez a szolgáltatás korábban a klasszikus Intune-portálon volt elérhető.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Felügyelt macOS-eszköz távoli zárolása az Intune-nal <!-- 1437691 -->

Zárolhatja az elveszett macOS-eszközöket, és beállíthat egy hat számjegyű jelszó-helyreállító PIN-kódot. A zárolt eszköz **Az eszköz áttekintése** panelén megjelenik a PIN-kód mindaddig, amíg az eszköznek nem kell egy másik műveletet végrehajtania.

További információ: [Felügyelt eszközök távoli zárolása az Intune-nal](../remote-actions/device-remote-lock.md).

### <a name="new-scep-profile-details-supported----1559808---"></a>Az új SCEP-profil részletei támogatottak <!-- 1559808 -->

A rendszergazdák további beállításokat adhatnak meg a SCEP-profilok létrehozásakor Windows-, iOS-, macOS- és Android-platformokon.  A rendszergazdák a tárgy névformátumának IMEI-t, sorozatszámot vagy köznapi nevet adhatnak meg, beleértve az e-mail-címeket.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>Az adatmegőrzés a gyári beállítások visszaállítása során  <!--1588489 -->
A Windows 10 rendszer 1709-es és újabb verziójának gyári beállításokra való visszaállítása egy új funkcióval bővült. A rendszergazdák megszabhatják, hogy az eszközregisztráció és egyéb kiépített adatok megmaradjanak-e az eszközökön a gyári beállítások visszaállítása után.

A következő adatok maradnak meg az eszközön a gyári beállítások visszaállításakor:
- Az eszközhöz társított felhasználói fiókok
- A gép állapota (tartományhoz való csatlakozás, Azure Active Directory-csatlakozás)
- MDM-regisztráció
- Az eredeti berendezésgyártók által telepített alkalmazások (áruház és Win32-alkalmazások)
- Felhasználói profil
- A felhasználói profilon kívüli felhasználói adatok
- Felhasználói automatikus bejelentkezés

Az alábbi adatok nem őrződnek meg:
- Felhasználói fájlok
- A felhasználók által telepített alkalmazások (áruház és Win32-alkalmazások)
- Nem alapértelmezett eszközbeállítások


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>A Windows 10-es frissítési kör hozzárendelései megjelennek <!-- 1621837 -->
**Hibaelhárítás** során az éppen megtekintett felhasználónál láthatja a Windows 10 frissítési körének hozzárendeléseit.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender komplex veszélyforrások elleni védelem jelentéskészítési gyakoriságának beállításai  <!-- 1455974  -->
A Windows Defender Komplex veszélyforrások elleni védelem (WDATP) szolgáltatással a rendszergazdák kezelhetik a felügyelt eszközök jelentéseinek gyakoriságát. Az új **Telemetriai jelentések gyakoriságának növelése** beállítással a WDATP gyakrabban gyűjt adatokat és méri fel a kockázatokat. A jelentések alapértelmezett beállítása optimalizálja a sebességet és a teljesítményt. A jelentések gyakoriságának növelése értékes lehet a magas fokú kockázattal bíró eszközök esetében. Ez a beállítás a **Windows Defender ATP** profilban, az **Eszközkonfigurációk** területen érhető el.

### <a name="audit-updates----1412961---"></a>Frissítések naplózása <!-- 1412961 -->  
Az Intune-naplózás az Intune-hoz kapcsolódó változtatási műveletekről szolgáltat információt.  Minden létrehozási, frissítési, törlési és távoli feladatműveletet rögzít és egy évig megőriz.  Az Azure Portalon megtekintheti az elmúlt 30 nap naplózási adatait számítási feladatonként, szűrhető állapotban.  Egy kapcsolódó Graph API segítségével lekérheti az elmúlt egy év tárolt naplózási adatait.

A naplózás funkció a **FIGYELÉS** csoportban érhető el. A csoportban minden számítási feladathoz tartozik egy **Naplók** menüpont.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>Céges portál macOS-alkalmazás érhető el <!--1541700-->
A macOS-hez készült Intune Céges portál frissített felhasználói felületet kapott, és ezentúl átláthatóbban jeleníti meg a regisztrált eszközökkel kapcsolatos, felhasználók számára szükséges információkat és megfelelőségi értesítéseket. És ha az Intune Céges portál már telepítve van az eszközre, a macOS-hez készült Microsoft AutoUpdate gondoskodni fog a frissítéséről is. Az új, macOS-hez készült Intune Céges portál alkalmazást az Intune Céges portál webhelyről, macOS-eszközzel bejelentkezve töltheti le.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>A Microsoft Planner már része a jóváhagyott alkalmazások Mobile App Management (MAM) listájának.  <!-- 1248473 -->
A Microsoft Planner alkalmazás iOS és Android rendszerű eszközök számára készült verziói a mobilalkalmazás-kezelési MAM-lista engedélyezett alkalmazásai közé tartoznak. Az alkalmazás az összes bérlőre vonatkozóan konfigurálható az Azure Portal Intune App Protection paneljén.
- További tudnivalók az [engedélyezett alkalmazások MAM-listájáról](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Alkalmazáson belüli VPN-követelmények frissítési gyakorisága iOS-eszközökön   <!-- 1547061 -->  
A rendszergazdák mostantól eltávolíthatják az alkalmazásonkénti VPN követelményét az iOS-eszközökről. Az érintett eszközök állapota a következő Intune-bejelentkezés után frissül (ez általában 15 percen belül következik be).  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>System Center Operations Manager felügyeleti csomag támogatása az Exchange connectorhoz <!-- 885457 -->
Az Exchange Connector System Center Operations Manager felügyeleti csomagja mostantól segít az Exchange Connector naplófájljainak elemzésében. Ez a funkció számos lehetőséget nyújt a szolgáltatás figyelésére hibaelhárítás esetén.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Közös felügyelet Windows 10-es eszközökhöz  <!-- 1243445 -->
A közös felügyelet olyan megoldás, amely a hagyományos és a modern felügyelet között teremt átjárhatóságot, és lehetővé teszi a fokozatos áttérést. Közös felügyelet esetén a Windows 10-es eszközöket együttesen felügyeli a Configuration Manager és a Microsoft Intune, és emellett az Azure Active Directoryhoz (AD) és az Azure Active Directoryhoz (Azure AD) is csatlakoztatva vannak.  Ez a konfiguráció lehetővé teszi, hogy idővel át lehessen térni a modern megoldásra, de elegendő időt hagy a vállalatnak, ha pillanatnyilag nincs mód az azonnali áttérésre.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Windows-regisztráció korlátozása operációsrendszer-verzió alapján <!-- 245498 -->
Az Intune-rendszergazdák mostantól megadhatják az eszközregisztrációhoz megkövetelt minimális és maximális Winows 10-verziót. Ezek a korlátozások a **Platformkonfigurációk** panelen állíthatók be.

Az Intune továbbra is támogatja Windows 8.1 rendszerű számítógépek és telefonok regisztrációját. Alsó és felső korlát azonban csak a Windows 10 verzióihoz állítható be. A 8.1-es eszközök regisztrációjának engedélyezéséhez az alsó korlátot üresen kell hagyni.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Riasztások a Windows Autopilot nem hozzárendelt eszközeihez  <!-- 1631236 -->
Új Windows AutoPilot-hozzárendelés nélküli eszközökre vonatkozó riasztás érhető el a **Microsoft Intune** > **Eszközregisztráció** > **Áttekintés** oldalon. Ez a riasztás azt mutatja meg, hogy az AutoPilot-programban hány eszközhöz nincs hozzárendelve AutoPilot Deployment-profil. A riasztás adatai alapján a profilok létrehozhatók és a hozzárendelés nélküli eszközökhöz rendelhetők. A riasztásra kattintva megjelenik a Windows AutoPilot-eszközök részletes adatokat is tartalmazó, teljes listája. További információt a [Windows-eszközök regisztrálása a Windows AutoPilot Deployment Program használatával](../enrollment/enrollment-autopilot.md) című témakörben találhat.


### <a name="refresh-button-for-devices-list-------1333581---"></a>Eszközök listájának frissítése gomb    <!-- 1333581 -->
Mivel az eszközlista nem frissül automatikusan, a listában megjelenő eszközök a Frissítés gombbal frissíthetők.

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>A Symantec Cloud Certification Authority (CA) támogatása  <!-- 1333638 -->    
Az Intune mostantól támogatást nyújt a Symantec Cloud CA-hez, amely lehetővé teszi, hogy az Intune Tanúsítvány-összekötő a Symantec Cloud CA-től származó PKCS-tanúsítványokat bocsásson ki az Intune által felügyelt eszközökhöz. Ha már használja az Intune Tanúsítvány-összekötőt a Microsoft hitelesítésszolgáltatóval (CA), akkor az Intune Tanúsítvány-összekötő meglévő beállításaival hozzáadhatja a Symantec CA-támogatást is.

### <a name="new-items-added-to-device-inventory-----1404455---"></a>Az eszközök leltározásához hozzáadott új elemek   <!--1404455 -->
A következő új elemek érhetők el mostantól a [regisztrált eszközök által rögzített leltárban](../remote-actions/device-inventory.md):

- Wi-Fi MAC-címe
- Teljes tárterület
- Összes szabad terület
- MEID
- Előfizető szolgáltatója

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Alkalmazások hozzáférésének beállítása minimális Android biztonsági javítással az eszközön<!-- 1278463 -->   
A rendszergazdák meghatározhatják, hogy az eszközön milyen minimális szintű Android biztonsági javításnak kell telepítve lennie ahhoz, hogy felügyelt fiók esetén hozzáférést kapjon a felügyelt alkalmazásokhoz.

> [!Note]  
> Ez a funkció csak azokat a biztonsági javítási szinteket határozza meg, amelyeket a Google az Android 6.0 vagy újabb verzióihoz tesz közzé.

### <a name="app-conditional-launch-support----1193313---"></a>Alkalmazás – feltételes indítási támogatás <!-- 1193313 -->
A rendszergazdák most már beállíthatnak egy követelményt az Azure felügyeleti portálján, amely a mobilalkalmazás-kezelésen (MAM) keresztül PIN-jelszót követel meg numerikus PIN-kód helyett, amikor az alkalmazás elindul. Ha a beállítás engedélyezve van, akkor a rendszer a felhasználót egy PIN-jelszó beállítására kéri, amelyet kötelező alkalmaznia, mielőtt hozzáférhetne a MAM-kompatibilis alkalmazásokhoz. A PIN-jelszó olyan numerikus PIN-kód, amely legalább egy speciális karaktert vagy kisbetűt/nagybetűt is tartalmaz. Az Intune jelen kiadása ezt a funkciót **csak iOS** esetén támogatja. Az Intune a PIN-jelszót a PIN-kódhoz hasonlóan támogatja minimális jelszóhossz megkövetelésével és karakterek és sorozatok ismétlődésének engedélyezésével. A funkcióhoz az alkalmazásoknak (például WXP, Outlook, Managed Browser, Yammer) integrálniuk kell az Intune App SDK-t ennek a funkciónak a kódjával, hogy a megcélzott alkalmazásoknál kötelezővé lehessen tenni a PIN-jelszóbeállításokat.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Az üzletági alkalmazás verziószáma az eszköz telepítési állapotáról szóló jelentésben <!-- 1233999 -->
Ettől a kiadástól kezdve az eszköz telepítési állapotjelentése megjeleníti az iOS-es és androidos üzletági alkalmazások verziószámát. A verziószám hasznos lehet az alkalmazás hibakeresésénél, vagy ha olyan eszközöket szeretne megtalálni, amelyek elavult verziószámú alkalmazásokat futtatnak.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>A rendszergazdák mostantól konfigurálhatja az eszköz tűzfalbeállítások beállításait az eszköz konfigurációs profiljának használatával. <!-- 951708 -->   
A rendszergazdák bekapcsolhatják a tűzfalat az eszközökhöz, és különféle protokollokat konfigurálhatnak tartományhoz, valamint privát és nyilvános hálózathoz.  Ezek a tűzfalbeállítások az „Endpoint Protection” profilban találhatók.

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>A Windows Defender Application Guard segít megvédeni az eszközöket a szervezet által meghatározott nem megbízható webhelyekről <!-- 958257 -->   
A rendszergazdák az egyes helyeket a Windows Information Protection munkafolyamattal, vagy az eszközkonfiguráció alatt található új „Hálózathatár” (Network boundary) profil használatával jelölhetik meg „megbízható” (trusted) vagy „vállalati” (corporate) típusúként. Ha olyan helyet néznek meg a Microsoft Edge böngészőben, amely nem szerepel a 64-bites Windows 10-es eszköz megbízhatónak jelölt hálózathatárainak listáján, akkor az egy Hyper-V virtuális számítógép böngészőjében fog megnyílni.

Az Application Guard az eszközkonfigurációs profilok között, az „Endpoint Protection” profilban található. A rendszergazdák ott konfigurálhatják a virtualizált böngésző és a gazdagép közötti és a nem megbízható és megbízható helyek közötti interakciót, valamint a virtualizált böngészőben generált adatok tárolását. Ahhoz hogy az Application Guard használható legyen egy eszközön, először konfigurálni kell egy hálózathatárt. Fontos, hogy egy eszközhöz csak egy hálózathatár legyen definiálva.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>A Windows Defender-alkalmazások vezérlése a Windows 10 Enterprise-ban lehetővé teszi, hogy csak a meghatalmazott alkalmazások legyenek megbízhatók <!-- 1031096 -->    
Ma már naponta több ezer rosszindulatú fájlt hoznak létre, így az aláírás-alapú felderítést használó víruskereső használata már nem nyújt elegendő biztonságot a kártevők elleni védelemben, hiszen újabb és újabb típusú támadások jelennek meg. A Windows 10 Enterprise rendszeren használható Windows Defender Alkalmazásvezérlés használatával különféle eszközkonfigurációs módokat lehet beállítani, többek között olyat, amelynél az alkalmazások megbízhatónak minősülnek mindaddig, amíg egy víruskereső vagy más biztonsági megoldás le nem tiltotta őket, vagy olyat, amelynél az operációs rendszer csak a vállalat által engedélyezett alkalmazásokat tekinti megbízhatónak. Az alkalmazások megbízhatósága a Windows Defender Alkalmazásvezérlésben állítható be.

Az Intune-ban az alkalmazásvezérlési szabályzatok beállíthatók „csak naplózási” vagy kötelező módban is. „Naplózási módban” az alkalmazások nincsenek letiltva. A „naplózási mód” minden eseményt egy ügyfélnaplóban rögzít. Az is beállítható, hogy csak a Windows-összetevők és a Microsoft Áruházbeli alkalmazások futtatása legyen engedélyezve, de az Intelligent Security Graphban megbízhatóként meghatározott további alkalmazások futtatása is engedélyezhető.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Az ablak Defender Exploit Guard a Windows 10 Behatolás-megelőzési képességeinek új készlete <!-- 1063615 -->   
A Windows Defender Exploit Guard olyan szabályokat tartalmaz, amelyekkel csökkenthető az alkalmazások rosszindulatú kihasználása, megelőzhetőek a makró- és parancsfájl-fenyegetések, automatikusan letilthatók a nem megbízhatónak tekintett IP-címek, és biztosítható az adatok védelme a zsarolóprogramok és az ismeretlen fenyegetések ellen. A Windows Defender Exploit Guard az alábbi összetevőket tartalmazza:

- A **támadási felület csökkentése** olyan szabályokat tartalmaz, amelyek lehetővé teszik a makrók, parancsfájlok és e-mailek fenyegetések elleni megelőzését.
- A **Felügyelt mappahozzáférés** automatikusan letiltja a védett mappák tartalmához való hozzáférést.
- A **Hálózati szűrő** minden alkalmazás esetében letiltja az alacsony megbízhatóságú IP-címek vagy tartományok felé irányuló kimenő adatforgalmat
- A **Biztonsági rések elleni védelem** a memóriára, a vezérlésfolyamra és a szabályzatokra vonatkozó korlátozásokat tartalmaz, amelyekkel megvédhetők az alkalmazások a biztonsági résektől.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>PowerShell-parancsfájlok kezelése az Intune-ban Windows 10-es eszközök esetén <!-- 790537 -->

Az Intune felügyeleti bővítményével Windows 10-es eszközökön futtatandó PowerShell-parancsfájlokat tölthet fel az Intune-ba. A bővítmény kiegészíti a Windows 10 mobileszköz-kezelési (MDM-) funkcióit, és könnyebbé teszi a modern felügyeletre való váltást. További részleteket a [PowerShell-parancsfájlok kezelése az Intune-ban Windows 10-es eszközök esetén](../apps/intune-management-extension.md) című témakörben találhat.

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Új Windows 10-es eszközkorlátozási beállítások      <!-- 1308850 -->
- Üzenetek (csak mobil) – szöveges vagy MMS-üzenetek letiltása
- Jelszó – beállítások FIPS engedélyezésére, valamint Windows Hello-eszközök és másodlagos eszközök hitelesítéshez való használatára 
- Képernyő – beállítások GDI-méretezés ki- és bekapcsolására régebbi alkalmazások esetén

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>A Windows 10-es kioszk mód eszközének korlátozásai <!-- 1308872 -->   
Windows 10-es eszközök esetén lehetséges a teljes képernyős mód kötelezővé tétele, ami a felhasználók számára egy előre meghatározott alkalmazáscsoportot tesz csak elérhetővé.  Ehhez egy Windows 10-es eszközkorlátozási profilt kell létrehozni, és meg kell adni a teljes képernyős beállításokat.

A teljes képernyős mód két lehetőséget támogat: az **egyetlen alkalmazás** módot (csak egy alkalmazás futtatható), és a **több alkalmazás** módot (alkalmazások egy csoportja érhető el).  Önnek kell meghatároznia a felhasználói fiókot és az eszköznevet, amely meghatározza a támogatott alkalmazásokat).  Bejelentkezés után a felhasználó csak a meghatározott alkalmazásokhoz férhet hozzá.  További információt az [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) témakörben talál. 

A teljes képernyős módhoz az alábbiak szükségesek:

- MDM-szolgáltatóként az Intune-t kell beállítani.
- A céleszközön már telepítve kell lenniük az alkalmazásoknak.
- Az eszköznek [megfelelően kiépített](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions) állapotban kell lennie.

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Új eszköz konfigurációs profil hálózati határok létrehozásához <!-- 1311967 -->   
Egy **Hálózathatár** nevű új eszközkonfigurációs profil található meg a többi eszközkonfigurációs profil között. Ezzel a profillal olyan online erőforrásokat határozhat meg, amelyeket vállalatiként és megbízhatóként szeretne definiálni. Ahhoz, hogy az eszközön használható legyen a Windows Defender Application Guard és a Windows Information Protection vagy más funkciók, *először* definiálnia kell az eszközhöz egy hálózathatárt. Fontos, hogy egy eszközhöz csak egy hálózathatár legyen definiálva.

Definiálhat felhőbeli erőforrásokat, IP-címtartományokat és belső proxykiszolgálókat is, amelyeket megbízhatóként szeretne megjelölni. Definiálás után a hálózathatárt más funkciók is felhasználhatják, például a Windows Defender Application Guard vagy a Windows Information Protection.

### <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Két további beállítás a Windows Defender víruskeresőhöz <!-- 1338409 -->  
**Fájlblokkolási szint**

| | |
|---|---|
| Nincs konfigurálva | A **Nincs konfigurálva** beállítás a Windows Defender víruskereső alapértelmezett blokkolási szintjét használja, és erős szintű észlelést végez anélkül, hogy a kockázatmentes fájlok észlelésének kockázatát növelné. |
| Magas | A **Magas** beállítás erős szintű észlelést eredményez.
| Magas +  | A **Magas +** beállítás a Magas szintet további védelmi funkciókkal bővíti ki, ami hatással lehet az ügyfélteljesítményre.
| Zéró tolerancia  | A **Zéró tolerancia** minden ismeretlen végrehajtható állományt letilt. |

Noha valószínűtlen, hogy megtörténik, elképzelhető, hogy a **Magas** beállításnál egyes kockázatmentes fájlok is észlelve lesznek.
Javasoljuk, hogy a fájlblokkolás szintjénél az alapértelmezés szerinti **Nincs konfigurálva** beállítást alkalmazza.

**Időtúllépési bővítmény felhőalapú fájlvizsgálathoz**  

| | |
|--|--|
| Másodpercek száma (0-50) | Adja meg azt a maximális időt, ameddig a Windows Defender víruskeresőnek blokkolnia kell a fájlt, amíg meg nem érkezik az eredmény a felhőből. Az alapértelmezett érték 10 másodperc. Az itt megadott érték (legfeljebb 50 másodperc) hozzáadódik ehhez a 10 másodperchez. A vizsgálat a legtöbb esetben a maximális időnél jelentősen rövidebb ideig tart. Az idő növelésével azonban elegendő időt biztosíthat ahhoz, hogy a felhő alaposan megvizsgálja a gyanús fájlokat. Javasoljuk, hogy engedélyezze ezt a beállítást, és értékeként legalább 20 másodpercet adjon meg. |

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Citrix VPN hozzáadott Windows 10-es eszközökhöz <!-- 1512457 -->  
A Citrix VPN konfigurálható Windows 10 rendszerű eszközökhöz. A Citrix VPN az **Alapszintű VPN** panelen, a *Kapcsolat típusának kiválasztása* listában választható ki a Windows 10 VPN-konfigurálásakor vagy később.

> [!Note]
> A Citrix-konfiguráció iOS és Android rendszerekhez már korábban is elérhető volt.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>A Wi-Fi-kapcsolatok támogatják az előre megosztott kulcsokat iOS rendszeren <!-- 1550823 -->
Az ügyfelek konfigurálhatják a Wi-Fi-profilokat úgy, hogy azok előmegosztott kulcsokat (PSK) használjanak a WPA/WPA2-Personal-kapcsolatokhoz iOS-eszközökön. Ezek a profilok akkor lesznek leküldve a felhasználó eszközére, amikor regisztrálja az eszközt az Intune-ban.

A profilnak az eszközre való leküldése után a következő lépés a profil konfigurációjától függ.  Ha automatikus csatlakozásra van beállítva, akkor ezt teszi, amikor a hálózatra legközelebb szükség lesz.  Manuálisan csatlakozó profil esetén a felhasználónak kell aktiválnia a kapcsolatot.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Hozzáférés az iOS-hez készült felügyelt alkalmazási naplókhoz <!-- 1469920 -->
Azon végfelhasználók, akiknél telepítve van a Managed Browser alkalmazás, a Microsoft által közzétett valamennyi alkalmazás felügyeleti állapotát láthatják és naplófájlokat küldhetnek a felügyelt iOS-alkalmazásaik hibaelhárításához.

A Managed Browser hibaelhárítási módjának iOS-eszközökön való engedélyezéséről [A felügyelt alkalmazások naplóinak elérése a Managed Browser használatával iOS rendszeren](../apps/app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios) című témakörben találhat további információt.

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Az eszköz beállítási munkafolyamatának fejlesztései az iOS rendszerhez készült Céges portál 2.9.0 verziójában <!-- 1417174 -->

Az iOS rendszerhez készült Céges portál alkalmazás eszközbeállítási munkafolyamatának továbbfejlesztése. Nyelvezete felhasználóbarátabb lett, képernyőit – ahol lehetett – összevontuk. A nyelvezet jobban igazodik a céghez, mivel a cég neve megjelenik a telepítés során látható szövegekben. A frissített munkafolyamatot a  [Felhasználói felületi frissítések az Intune végfelhasználói alkalmazásaiban](../whats-new-app-ui.md) oldalon tekintheti meg.


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>A felhasználói entitás a legújabb felhasználói adattípust tartalmazza az adatraktár adatmodelljében <!-- 1544273 -->
Az Intune-adattárház adatmodelljének első verziója csak a legújabb Intune-előzményadatokat tartalmazta. A jelentéskészítők így nem tudták felmérni a felhasználók aktuális állapotát. Ebben a frissítésben a **Felhasználói entitás** a legújabb felhasználói adatokkal lett feltöltve.

<!-- ########################## -->
## <a name="october-2017"></a>2017. október

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>az iOS és az Android rendszerű üzletági alkalmazás verziószáma látható <!-- 1380712 -->

Az Intune alkalmazásai mostantól megjelenítik az üzletági iOS- és Android-alkalmazások verziószámait. A számok az Azure Portal alkalmazáslistáján, valamint az Alkalmazás áttekintése panelen jelennek meg. A végfelhasználók az alkalmazásszámot a céges portál alkalmazásban és a webportálon tekinthetik meg.

__Teljes verziószám:__ A teljes verziószám azonosítja az alkalmazás egy konkrét verzióját. A szám az alábbi formátumban jelenik meg: _Verzió_(_Build_). Például: 2.2(2.2.17560800)

A teljes verziószám két részből áll:

- **Verzió**  
  A verziószám az alkalmazás természetes nyelven olvasható kiadási száma. A végfelhasználók ezzel azonosítják az alkalmazás különböző kiadásait.

- **Buildszám**  
  A buildszám egy olyan belső szám, amelyet alkalmazásdetektáláshoz és az alkalmazások szoftveres felügyeletéhez használnak. A buildszám az alkalmazás olyan iterációira vonatkozik, amely a kód változásaira hivatkozik.

A verziószámokról és az üzletági alkalmazások fejlesztéséről további információt a [Bevezetés a Microsoft Intune App SDK használatába](../developer/app-sdk-get-started.md#line-of-business-app-version-numbers) című cikkben találhat.

### <a name="device-and-app-management-integration----677972---"></a>Eszközök és alkalmazások kezelésének integrációja <!-- 677972 -->   
Mivel az Intune-alapú mobileszköz-kezelés (MDM) és a mobilalkalmazás-kezelés (MAM) most már egyaránt elérhető az Azure Portalról, az Intune elkezdte integrálni az alkalmazás- és az eszközkezelés rendszergazdai felületét. Ez a változás az eszköz- és az alkalmazáskezelés egyszerűsítését szolgálja.

Az MDM és a MAM változásairól az [Intune-ügyfélszolgálat blogjában](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/) tájékozódhat.

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Új beléptetési riasztások Apple-eszközökhöz <!-- 1471790 -->
A regisztrálás áttekintési oldalán hasznos figyelmeztetések jelennek meg a rendszergazdák számára az Apple-eszközök felügyeletével kapcsolatban. A figyelmeztetések akkor jelennek meg az Áttekintés lapon, amikor az Apple MDM leküldéses értesítései lejárnának vagy már lejártak, amikor a Készülékregisztrációs program lejárna vagy már lejárt, illetve akkor, amikor nem hozzárendelt eszközök vannak a Készülékregisztrációs programban.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Támogatási jogkivonat cseréje az alkalmazás konfigurálásához az eszközök beléptetése nélkül <!-- 1080364 -->

A tokeneket az alkalmazáskonfigurációk dinamikus értékeihez használhatja olyan eszközökön található alkalmazásokhoz, amelyek nincsenek regisztrálva. További információ: [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközregisztráció nélkül](../apps/app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>A Windows 10-es Céges portál alkalmazás frissítései <!--1299474-->
Frissítettük a Windows 10-es Céges portál alkalmazás beállítások oldalát, hogy egységesebbek legyenek a beállítások és a beállításoknál elvégezhető felhasználói műveletek. Az elrendezését is átalakítottuk, hogy jobban igazodjon a többi Windows-alkalmazáséhoz. [Az alkalmazásfelhasználói felület újdonságai](../whats-new-app-ui.md) oldalon talál előtte/utána összehasonlító képeket.

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>A végfelhasználók tájékoztatása a Windows 10-es eszközökhöz kapcsolódó eszközökről <!--1337920-->
A Windows 10-es Céges portál alkalmazásban található Eszköz részletei képernyőhöz hozzáadtuk a **Tulajdonjog típusa** oldalt. Ez lehetővé teszi a felhasználók számára, hogy közvetlenül az Intune végfelhasználói docs-ból ezen az oldalon tudjon meg többet az adatvédelemről. Ezeket az információkat a **Névjegy** képernyőn is megtalálhatja.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Visszajelzési kérések az Android rendszerhez készült Céges portál alkalmazáshoz <!--1165249-->
Az androidos Céges portál alkalmazás mostantól végfelhasználói visszajelzés küldésére szólít fel. A visszajelzés közvetlenül a Microsofthoz érkezik, és lehetőséget nyújt a végfelhasználók számára, hogy értékelhessék az alkalmazást a nyilvános Google Play Áruházban. A visszajelzés küldése nem kötelező, és a felhasználók könnyen bezárhatják a felszólítást, hogy folytathassák a munkát az alkalmazásban.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>A felhasználók segítése az androidos Céges portál alkalmazással <!-- 1573324, 1573150, 1558616, 1564878 -->

Az Androidhoz készült Céges portál alkalmazás olyan utasításokkal bővült, amelyekkel a végfelhasználók könnyebben megérthetik, és – ahol lehetséges – egyedül megoldhatják az új használati eseteket.
- A végfelhasználókat az alkalmazás az [Azure Active Directory Portalra](https://account.activedirectory.windowsazure.com/r/#/profile) irányítja, ahol eltávolíthatják az eszközöket, ha elérték a maximálisan hozzáadható eszközök számát.
- A végfelhasználók ekkor utasításokat kapnak, amelyekkel [kijavíthatják az aktiválási hibákat a Samsung Knox-eszközökön](https://go.microsoft.com/fwlink/?linkid=859718), vagy [kikapcsolhatják az energiatakarékos üzemmódot](/intune-user-help/power-saving-mode-android). Ha a megoldások egyike sem oldja meg a problémát, segítséget nyújtunk a [naplófájlok a Microsoftnak való küldéséhez](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Új "Feloldás" művelet érhető el az Android-eszközökhöz <!-- 1583480 -->

Az Androidhoz készült céges portál alkalmazás egy új „Feloldás” műveletet vezet be az _Eszközbeállítások frissítése_ lapon. A beállítás kiválasztásával a végfelhasználó közvetlenül ahhoz a beállításhoz kerül, amely az eszköz nem megfelelőségét okozza. Az Androidhoz készült céges portál alkalmazás ezt a műveletet jelenleg az [eszköz PIN-kódja](/intune-user-help/set-your-pin-or-password-android), [az USB-hibakeresés](/intune-user-help/you-need-to-turn-off-usb-debugging-android) és az [Ismeretlen források](/intune-user-help/you-need-to-turn-off-unknown-sources-android) beállításokhoz támogatja.

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Az eszköz beállításának állapotjelzője Android Céges portál <!-- 1565657 -->
Az androidos Céges portál alkalmazás egy telepítési állapotjelzőt jelenít meg a felhasználó számára az eszközregisztráció során. Az állapotjelző a következő új állapotokat jeleníti meg: „Az eszköz beállítása...”, ezután „Az eszköz regisztrálása...”, majd „Az eszköz regisztrációjának befejezése...”, végül „Az eszköz beállításának befejezése...”.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Tanúsítványalapú hitelesítés támogatása az iOS rendszerhez készült Céges portál <!--1029830-->
Mostantól támogatjuk a tanúsítványalapú hitelesítést (CBA) az iOS-es céges portál alkalmazásban. A CBA-hitelesítést használó felhasználóknak meg kell adniuk a felhasználónevüket, majd a „Bejelentkezés tanúsítvánnyal” hivatkozásra kell koppintaniuk. A CBA már eddig is támogatva volt az androidos és a windowsos céges portál alkalmazásban. További információt a [Bejelentkezés a céges portál alkalmazásba](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) oldalon talál.

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>A regisztrációval vagy anélkül is elérhető alkalmazások mostantól anélkül telepíthetőek, hogy a rendszer a regisztrálást kérné. <!-- 1334712 -->

Azok a céges alkalmazások, amelyek regisztrációval és anélkül is elérhetőek az Androidhoz készült Céges portál alkalmazásban, mostantól anélkül is telepíthetők, hogy a rendszer regisztrációt kérne.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>A Windows AutoPilot üzembe helyezési program támogatása a Microsoft Intune-ban  <!-- 747617  -->
Mostantól használhatja az Intune-nal a Windows AutoPilot üzembe helyezési programot, amellyel lehetővé teheti, hogy a felhasználók az informatikai szolgálat közreműködése nélkül helyezzék üzembe vállalati eszközeiket. A kezdőélményt (OOBE) testre szabhatja, és útmutatást nyújthat a felhasználóknak ahhoz, hogy eszközeiket az Azure AD-hez csatlakoztassák, és azokta az Intune-ban regisztrálják. A Microsoft Intune és a Windows AutoPilot együttes használatával kiküszöbölhető az operációsrendszer-lemezképek üzembe helyezésének, fenntartásának és kezelésének feladatai. További részletekért lásd: [Windows-eszközök regisztrálása a Windows AutoPilot Deployment Program használatával](../enrollment/enrollment-autopilot.md).

### <a name="quickstart-for-device-enrollment-----1425655---"></a>Útmutató az eszközök regisztrálásához  <!-- 1425655 --> 
A gyors útmutató mostantól elérhető az **eszközök regisztrálásával** , és a platformok felügyeletére és a beléptetési folyamat konfigurálására mutató hivatkozásokat tartalmaz. Minden tételhez egy rövid leírás tartozik, valamint hivatkozások olyan forrásokra, amelyek lépésenkénti útmutatót és dokumentációt tartalmaznak, és amelyekkel leegyszerűsíthető a folyamat.

### <a name="device-categorization----1427491---"></a>Eszköz kategorizálása <!-- 1427491 -->
Az **Eszközök > Áttekintés** panelen található regisztrált eszközök platformdiagramja platformok szerint (Android, iOS, macOS, Windows és Windows Mobile) rendezi az eszközöket.  A másféle operációs rendszert futtató eszközök az „Egyéb” kategóriában találhatóak.  Ilyenek lehetnek például a Blackberry, a Nokia és más gyártók eszközei.  

A bérlőhöz tartozó érintett eszközök megtekintéséhez válassza a **Kezelés > Minden eszköz** elemet, majd használja a **Szűrőt** az **Operációs rendszer** mezőre.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – új Mobile Threat Defense-partner   <!-- 954681 -->  
A mobileszköz-hozzáférés a vállalati erőforrásokhoz a feltételes hozzáférés használatával szabályozható a Zimperium által végzett, a Microsoft Intune-nal integrálható mobil veszélyforrások elleni védelmi megoldás alapján.

#### <a name="how-integration-with-intune-works"></a>Hogyan működik az Intune-nal való integráció
A kockázatfelmérés a Zimperiumot futtató eszközökről gyűjtött telemetriai adatokon alapul. Az EMS feltételes hozzáférési szabályzatait az Intune-eszköz megfelelőségi szabályzatai által engedélyezett Zimperium kockázatértékelés alapján konfigurálhatja, amellyel engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz az észlelt fenyegetések alapján.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>A Windows 10-es eszközkorlátozási profil új beállításai  <!--- 978575, 1308849, -->  
A Windows Defender SmartScreen kategóriában új beállításokat adunk a Windows 10-es eszközkorlátozási profilhoz.

A Windows 10-es eszközkorlátozási profillal kapcsolatban lásd: [Windows 10-es és újabb eszközkorlátozási beállítások](../configuration/device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Távoli támogatás Windows és Windows Mobile rendszerű eszközökhöz   <!-- 1070473 -->  
Az Intune-ból a külön megvásárolható [TeamViewer](https://www.teamviewer.com) szoftverrel lehet távsegítséget nyújtani a Windows és Windows Mobile rendszerű eszközök felhasználóinak.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Eszközök vizsgálata a Windows Defenderrel <!-- 1280988  1280990   -->
Windows 10 rendszerű felügyelt eszközökön a Windows Defender víruskereső használható **gyorsvizsgálat** és **teljes vizsgálat** futtatására, valamint **aláírások frissítésére**. Az eszköz áttekintő paneljén válassza ki az eszközön futtatni kívánt műveletet. A rendszer megerősítést fog kérni, mielőtt a parancsot lefuttatná az eszközön. 

**Gyorsvizsgálat**: A gyorsvizsgálat azokat a helyeket vizsgálja meg, ahol a kártevő általában indításhoz lehet regisztrálva, például a beállításkulcsok és az ismert indítási Windows-mappák. A gyorsvizsgálat átlagosan öt percig tart. Az **Állandó valós idejű védelem** a fájlok megnyitásakor, bezárásakor és a mappa megjelenítésekor megvizsgálja a fájlokat. Ez a beállítás a gyorsvizsgálattal együtt segít kiszűrni azokat a kártevőket, amelyek akár a rendszert, akár a kernelt fertőzték meg. A vizsgálat végén a felhasználók saját eszközeiken nézhetik meg a vizsgálat eredményeit. 

**Teljes vizsgálat**: Teljes vizsgálatot olyan eszközökön célszerű futtatni, amelyeken korábban kártevő-fenyegetést találtak, hogy feltárhatóak legyenek a kártevő esetleges inaktív komponensei mélyebb tisztítás érdekében, továbbá igény szerinti vizsgálatra is használható. A teljes vizsgálat körülbelül egy órát vehet igénybe. A vizsgálat végén a felhasználók saját eszközeiken nézhetik meg a vizsgálat eredményeit. 

**Aláírások frissítése**: Az aláírások frissítése parancs frissíti a Windows Defender víruskereső kártevő-definícióit és aláírásait. Ezzel biztosítható, hogy a Windows Defender víruskereső hatékonyan észlelhesse a kártevőket. Ez a funkció csak a Windows 10 rendszert futtató eszközökön érhető el, és internetkapcsolat szükséges hozzá. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Az engedélyezés/letiltás gomb el lesz távolítva az Intune-beli Intune-hitelesítésszolgáltató lapról Azure Portal  <!-- 1400455 -->
 Az Intune-beli tanúsítvány-összekötő beállításánál egy lépést szükségtelenné teszünk. Jelenleg először le kell tölteni a tanúsítvány-összekötőt, és ezután engedélyezni kell azt az Intune-konzolon. Ha azonban letiltja az összekötőt az Intune-konzolon, az összekötő továbbra is kibocsát tanúsítványokat.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Októbertől az Engedélyezés/Letiltás gomb nem jelenik meg többé az Azure Portal Hitelesítésszolgáltató lapján. Az összekötő funkció továbbra is változatlan marad. Az Intune-ban regisztrált eszközökhöz továbbra is üzembe lesznek helyezve a tanúsítványok. A tanúsítvány-összekötőt továbbra is le lehet tölteni, és telepíteni is lehet. A tanúsítványok kibocsátásának leállítását azonban most már nem a tanúsítvány-összekötő letiltásával, hanem annak telepítésével lehet elérni.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Ha jelenleg letiltott állapotban van a tanúsítvány-összekötője, akkor azt el kell távolítania.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Új beállítások a Windows 10 Team-eszközök korlátozási profiljához   <!--- 1308838 -->
Az új kiadásban számos új beállítási lehetőséget tettünk elérhetővé a Windows 10 Team eszközkorlátozási profiljához, hogy hatékonyabban lehessen vezérelni a Surface Hub-eszközöket.

A profilról további információt a [Windows 10 Team eszközkorlátozási beállításai](../configuration/device-restrictions-windows-10-teams.md) című témakörben talál.

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Az Android-eszközök felhasználói számára az eszköz dátumának és időpontjának megváltoztatásának megakadályozása  <!-- 1333292 -->
Egy [Androidos egyéni eszközszabályzat](../configuration/custom-settings-android.md) használatával megakadályozható, hogy a felhasználó megváltoztassa az Android-eszköz rendszeridejét.

Ehhez hozzon létre egy egyéni Android-szabályzatot ezzel az URI-val: ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange Állítsa **TRUE** (igaz) értékre, majd rendelje hozzá a kívánt csoportokhoz.

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker-eszköz konfigurációja <!-- 1397398 -->
A **Windowsos titkosítás > Alapbeállítások** területen elérhetővé a **Figyelmeztetés más lemeztitkosítás esetén** beállítás is, amellyel letilthatja azt a [figyelmeztetést](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption), amely akkor jelenik meg, ha az eszközön más lemeztitkosítás is használatban van.  A figyelmeztetés a végfelhasználó hozzájárulását kéri a BitLocker eszközön való beállításához, és a hozzájárulásig letiltja a BitLocker telepítését.  Az új beállítással letiltható a végfelhasználó számára megjelenő figyelmeztetés.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>A Volume Purchase program for Business alkalmazások most már szinkronizálva lesznek az Intune-Bérlővel <!-- 800882 -->  
Az iTunes Connectben megadott, megfelelő jogosultságokkal rendelkező Volume Purchase Program (VPP) for Business-tagoknak külsős fejlesztők is terjeszthetik alkalmazásaikat. Ezek a VPP for Business-tagok be tudnak jelentkezni a Volume Purchase Program App Store áruházba, és ott meg tudják venni azokat az alkalmazásokat, amelyekre szükségük van.

Ebben a kiadásban a végfelhasználók által a VPP for Business keretében megvásárolt alkalmazások Intune-bérlőikkel szinkronizálják magukat.

### <a name="select-apple-countryregion-store-to-sync-vpp-apps-----1332311---"></a>Válassza az Apple ország/régió tároló elemet a VPP-alkalmazások szinkronizálásához  <!-- 1332311 -->  
A VPP-token feltöltésekor beállíthatja a Volume Purchase program (VPP) ország/régió tárolóját. Az Intune az adott VPP ország/régió tárolóban lévő összes területi beállításhoz a VPP-alkalmazásokat szinkronizálja.

> [!NOTE]  
> Napjainkban az Intune csak a VPP ország/régió áruházból származó VPP-alkalmazásokat szinkronizálja, amelyek megfelelnek az Intune-bérlő létrehozásának az Intune-beli területi beállításának.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>A munkahelyi és a személyes profilok közötti másolás és beillesztés tiltása az Android for Work szolgáltatásban <!-- 1098994 -->
Ebben a kiadásban lehetséges úgy konfigurálni az Android for Work-profilt, hogy az letiltsa a munkahelyi és személyes fiókok közötti másolást és beillesztést. Az új beállítás a **Munkahelyi profil beállításai** között, az **Android for Work** platform **Eszközkorlátozások** területén található.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>IOS-alkalmazások létrehozása az adott regionális Apple App Store-ra korlátozva <!-- 1281692 -->
Megadhatja az ország/régió területi beállítását egy Apple App Store által felügyelt alkalmazás létrehozása során.

> [!Note]  
> Jelenleg csak olyan Apple App Store által felügyelt alkalmazásokat hozhat létre, amelyek az USA-beli ország/régió tárolóban találhatók.

### <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>IOS VPP-felhasználó és-eszköz licencelt alkalmazásainak frissítése  <!-- 1305564 -->  
Az iOS-es VPP-token úgy is konfigurálható, hogy frissítse az összes olyan alkalmazást, amelyet az adott tokenhez vásároltak az Intune szolgáltatáson keresztül. Az Intune észlelni fogja, ha az adott VPP-alkalmazáshoz frissítés érhető el az alkalmazás-áruházban, és ezt követően automatikusan leküldi a frissítéseket az eszközre, amikor az legközelebb bejelentkezik.

A VPP-token beállításáról és az automatikus frissítésekről lásd: [Mennyiségi vásárlási program keretében vásárolt iOS-alkalmazások kezelése a Microsoft Intune-nal] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Az Intune-adattárház adatmodelljébe felvett felhasználó-eszköz társítási entitások gyűjteménye <!-- 1187917 -->
A felhasználók és eszközök gyűjteményének társítását végző felhasználói eszköztársítási információ használatával jelentéseket és adatvizualizációkat hozhat létre. Az adatmodell a Power BI-fájlon (PBIX) keresztül érhető el az adattárház Intune-oldaláról az OData-végpont használatával vagy egyéni ügyfél létrehozásával.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>A szabályzat megfelelőségének áttekintése a Windows 10 frissítési gyűrűkhöz <!-- 1067886 -->
A Windows 10-es frissítési körök szabályzatjelentéseit meg lehet majd tekinteni a Szoftverfrissítések > Frissítési körök telepítési állapota szerint területen. A szabályzatjelentés tartalmazza a konfigurált frissítési körök telepítési állapotát. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Új jelentés, amely a régebbi iOS-verziókkal rendelkező iOS-eszközöket sorolja fel   <!-- 1352223 -->
Az **Elavult iOS-eszközök** jelentést a **Szoftverfrissítések** munkaterületről lehet elérni. A jelentésben megtekintheti az iOS frissítési szabályzatok által megcélzott és elérhető frissítésekkel rendelkező felügyelt iOS-eszközök listáját. Minden eszköz mellett látható lesz egy állapotleírás is, amelyből kiderül, hogy az adott eszköz miért nem frissült automatikusan. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Alkalmazás-védelmi szabályzat-hozzárendelések megtekintése hibaelhárításhoz <!--  1475003 -->
A következő kiadásban megjelenik az **Alkalmazásvédelmi szabályzat** lehetőség is a hibakeresési panelen elérhető **Hozzárendelések** legördülő listában. Az alkalmazásvédelmi szabályzatok lehetőség kiválasztásával megtekintheti a kiválasztott felhasználókhoz hozzárendelt alkalmazásvédelmi szabályzatokat.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Az eszköz beállítási munkafolyamatainak fejlesztései Céges portál <!--1490692-->
Továbbfejlesztettük az androidos Céges portál alkalmazás eszközbeállítási munkafolyamatát. Nyelvezete felhasználóbarátabb, vállalatra szabottabb. Képernyőit – ahol lehetett – összevontuk. Az újításokat megtekintheti a [ felhasználói felület újdonságait](whats-new-app-ui.md#week-of-october-2-2017) bemutató oldalon.

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Az Android-eszközökön található névjegyekhez való hozzáférésre vonatkozó kérések jobb útmutatója <!--1484985-->

Gyakran előfordul, hogy a felhasználóknak engedélyt kell adniuk az androidos Céges portál alkalmazásnak a Kapcsolatok használatára. Ha egy végfelhasználó elutasítja ezt a hozzáférést, a rendszer egy alkalmazáson belüli értesítést fog látni, amely riasztást küld a feltételes hozzáférés biztosításához. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Biztonságos indítási szervizelés Android rendszerhez <!--1490712-->

Az Android-eszközök végfelhasználói mostantól rá tudnak koppintani a Céges portál alkalmazásban az okra, amely miatt az eszköz nem felel meg valamelyik biztonsági szabálynak. Amikor csak lehetséges, ennek hatására meg fog jelenni az a beállítási képernyő, ahol kezelhető a probléma. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>További leküldéses értesítések az Android Oreo Céges portál alkalmazás végfelhasználói számára <!--1475932-->

A végfelhasználók számára további értesítések jelennek meg, amelyek jelzik, hogy az Android Oreo Céges portál alkalmazása mikor végez háttérműveleteket (például szabályzatok lekérése az Intune szolgáltatástól). Ez átláthatóbbá teszi a végfelhasználók számára a Céges portál az eszközeiken végzett felügyeleti feladatait. Ez a [Céges portál felhasználói felülete optimalizálásának](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) része, amelyet az Android Oreo rendszeren futó Céges portál alkalmazáshoz végzünk. 

Az Android Oreóban engedélyezett új felhasználóifelület-elemekhez további optimalizálások tartoznak.  A végfelhasználók számára további értesítések jelennek meg, amelyek jelzik, hogy a Céges portál mikor végez háttérműveleteket, például szabályzatok lekérését az Intune szolgáltatástól.  Ez átláthatóbbá teszi a végfelhasználók számára, hogy a Céges portál mikor hajt végre felügyeleti feladatokat az eszközön.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Az Android rendszerhez készült Céges portál alkalmazás új viselkedése a munkahelyi profilokkal <!-- 1485783 -->

Android for Work-eszköz munkahelyi profillal történő regisztrálása után a munkahelyi profil Céges portál alkalmazása végzi el az eszközön a felügyeleti feladatokat. 

Hacsak nem használ MAM-használatot támogató alkalmazást a személyes profilban, az androidos Céges portál alkalmazásra már nincs szükség. Ezért a munkahelyi profil hatékony használhatósága érdekében a munkahelyi profil sikeres regisztrálása után az Intune elrejti a személyes Céges portál alkalmazást.

Az Androidhoz készült Céges portál alkalmazás a személyes profilban bármikor engedélyezhető. Ehhez keresse meg a [Céges portál alkalmazást a Play Áruházban](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal), és koppintson az **Engedélyezés** lehetőségre.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Céges portál a Windows 8,1 és Windows Phone-telefon 8,1 rendszerre való áttérés fenntartási módba <!--1428681-->

2017 októberétől a Windows 8.1 és Windows Phone 8.1 rendszerekhez készült Céges portál alkalmazás fenntartási módba kerül. Ez azt jelenti, hogy ezeken a platformokon továbbra is jár támogatás az alkalmazásokhoz és a meglévő használati forgatókönyvekhez (például regisztrálás és megfelelőség). Az alkalmazások továbbra is letölthetők a meglévő kiadási csatornákon keresztül, például a Microsoft Áruházból. 

A fenntartási módban ezekhez az alkalmazásokhoz azonban már csak fontos biztonsági frissítések lesznek elérhetőek. Más típusú frissítések és új funkciók már nem jelennek meg ezekhez az alkalmazásokhoz. Ha az új funkciókat szeretné használni, azt javasoljuk, hogy frissítse az eszközt Windows 10 vagy Windows 10 Mobile rendszerre. 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Nem támogatott Samsung Knox-eszközök regisztrációjának letiltása  <!-- 1490695 -->

A Céges portál alkalmazás csak a támogatott Samsung Knox-eszközöket próbálja meg regisztrálni. Az MDM-regisztrációt megakadályozó Knox-aktiválási hibák elkerülése érdekében az alkalmazás csak a [Samsung által közzétett eszközlistán](https://www.samsungknox.com/knox-supported-devices/knox-workspace) szereplő eszközöket próbálja meg regisztrálni. Előfordulhat, hogy egy Samsung-eszköz bizonyos modelljei támogatják a Knox platformot, míg más modelljei nem. Egy adott eszköz megvásárlása és üzembe helyezése előtt egyeztesse a viszonteladóval, hogy az eszköz Knox-kompatibilis-e. Az ellenőrzött eszközök teljes listáját megtalálhatja az [Android- és Samsung Knox Standard-eszközök konfigurációs szabályzatának beállításai](supported-devices-browsers.md#intune-supported-web-browsers) című témakörben.

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Az Android 4,3-es és alacsonyabb szintű támogatásának vége <!-- 1171126, 1326920 -->
A felügyelt alkalmazások és az Androidra készült Céges portál alkalmazás esetén az Android 4.4-es vagy újabb verziója követelmény lesz a vállalati erőforrások eléréséhez. Decemberre az összes regisztrált eszköz ki lesz vonva, így elveszti hozzáférését a vállalati erőforrásokhoz. Ha MDM nélküli alkalmazásvédelmi szabályzatokat használ, akkor az alkalmazások nem jutnak hozzá a frissítésekhez és a használhatóságuk idővel romlani kezd.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>A végfelhasználók tájékoztatása a regisztrált eszközökön látható eszközökről <!--1165314-->
A Céges portál alkalmazások Eszköz részletei képernyője kiegészül a **Tulajdonjog típusa** oldallal. Így a felhasználók közvetlenül a [Milyen adatok láthatók a cég számára?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) című cikkből fognak tudni tájékozódni az adatvédelmi kérdésekről. Ez terveink szerint az összes Céges portál alkalmazásban meg fog jelenni a közeljövőben. Az iOS kapcsán ezt a funkciót [szeptemberben](#september-2017) jelentettük be.

<!-- ########################## -->
## <a name="september-2017"></a>2017. szeptember

### <a name="intune-supports-ios-11---1428975--"></a>Az Intune támogatja az iOS 11-et <!--1428975-->
Az Intune támogatja az iOS 11-et. Ezt korábban bejelentettük az [Intune támogatási blogjának](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/) oldalán.

### <a name="end-of-support-for-ios-80----1164477---"></a>Az iOS 8,0 támogatásának vége <!-- 1164477 -->
A felügyelt alkalmazások és az iOS-re készült Céges portál alkalmazás esetén az iOS 9.0-s vagy újabb verziója követelmény lesz a vállalati erőforrások eléréséhez. Azok az eszközök, amelyeket nem frissítenek még szeptember előtt, többé nem fognak hozzáférni a Céges portálhoz vagy azokhoz az alkalmazásokhoz. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>A Windows 10-es Céges portál alkalmazáshoz hozzáadott frissítési művelet <!--1132468-->
A Windows 10-es céges portál alkalmazásban lehetőség lesz az adatok frissítésére. Ezt lefelé húzással, vagy asztali gépeken az F5 billentyű megnyomásával lehet majd elvégezni.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>A végfelhasználók tájékoztatása arról, hogy milyen eszköz-információ látható az iOS-hez <!--739894-->

Az iOS rendszerhez készült Céges portál alkalmazásban az eszköz adatai képernyőhöz hozzáadott **tulajdonosi típust** . Ez lehetővé teszi a felhasználók számára, hogy közvetlenül az Intune végfelhasználói docs-ból ezen az oldalon tudjon meg többet az adatvédelemről. Ezeket az információkat a névjegy képernyőn is megtalálhatja.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Az Androidhoz készült Céges portál alkalmazás regisztráció nélküli elérésének engedélyezése a végfelhasználók számára <!---1169910--->

A végfelhasználóknak rövidesen mát nem kell regisztrálniuk az eszközüket az Android rendszerre készült Céges portál alkalmazás eléréséhez. Az alkalmazásvédelmi szabályzatokat használó szervezetek végfelhasználói többé nem fognak az eszközük regisztrálására felszólító figyelmeztetést kapni a Céges portál alkalmazás megnyitásakor. A végfelhasználók alkalmazásokat is tudnak majd telepíteni a Céges portálról az eszköz regisztrálása nélkül. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Könnyebben érthető megfogalmazás az Androidhoz készült Céges portál alkalmazáshoz <!---1396349--->  

Egyszerűsítettük az Androidhoz készült Céges portál alkalmazás regisztrálási folyamatának leírását, hogy a végfelhasználók könnyebben tudják elvégezni a regisztrálást. Ha egyéni regisztrációs dokumentációval rendelkezik, frissítse az új képernyők megjelenítéséhez. Mintaképeket a [Felhasználói felületi frissítések az Intune végfelhasználói alkalmazásaiban](whats-new-app-ui.md#week-of-september-11-2017) című oldalon találhat.

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10 Céges portál alkalmazás hozzáadása a Windows Information Protection a házirend engedélyezése <!-- 677129 -->

Frissítettük a Windows 10-es Céges portál alkalmazást, amely így támogatja a Windows Információvédelmet. Az alkalmazást hozzá lehet adni a WIP engedélyezési szabályzatához. A változásnak köszönhetően az alkalmazást a későbbiekben nem szükséges hozzáadni a **Kivételek** listához.


<!-- ########################## -->
## <a name="august-2017"></a>2017. augusztus

### <a name="improvements-to-device-overview----1404453---"></a>Az eszközök áttekintésének fejlesztése <!-- 1404453 -->  
A fejlesztéseknek köszönhetően az eszközök áttekintésében mostantól megjelennek a regisztrált eszközök, az Exchange ActiveSync által kezeltek viszont ki lesznek hagyva. Az Exchange ActiveSync által kezelt eszközök a regisztrált eszközökéitől eltérő felügyeleti beállításokkal rendelkeznek. A regisztrált eszközök számát összesítve és platform szerinti lebontásban is megtekintheti az Intune-ban az Azure Portal **Eszközök** > **Áttekintés** menüpontjában.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Az Intune által gyűjtött eszközleltár fejlesztései
<!-- 961134, 1104426, 1281327, 1333543 -->
Ebben a kiadásban a következő fejlesztések lettek végrehajtva a kezelt eszközök által gyűjtött leltáradatokkal kapcsolatban:
 
- Mostantól Android-eszközök esetében hozzá lehet adni egy legutóbbi javítási szintet megjelenítő oszlopot az eszközleltárhoz. Ennek megtekintéséhez adja a **Security patch level** (Biztonsági javítási szint) oszlopot az eszközlistához.
- Az eszközök szűrésénél most már az eszköz regisztrációjának dátuma alapján is szűrhet. Például megadhatja, hogy csak azok az eszközök jelenjenek meg, melyeket egy adott dátum után regisztráltak.
- Fejlesztéseket hajtottunk végre a **Last Check-in Date** (Utolsó beadás dátuma) szűrőjén.
- Az eszközlistában most már megjelenítheti a céges eszközök telefonszámát.
Továbbá, a szűrőablakban mostantól már telefonszám alapján is kereshet az eszközök között.

További információt az eszközleltárral kapcsolatban [Az Intune-eszközleltár megtekintése](../remote-actions/device-inventory.md) című cikkben talál.

### <a name="conditional-access-support-for-macos-devices"></a>Feltételes hozzáférési támogatás macOS-eszközökhöz 
<!-- 720172 -->
Mostantól beállíthat egy feltételes hozzáférési szabályzatot, amely megköveteli, hogy a Mac-eszközök regisztrálva legyenek az Intune-ban, és megfeleljenek az eszköz megfelelőségi házirendjének. A felhasználók megtehetik például, hogy letöltik a macOS-re készült Intune Céges portál alkalmazást és regisztrálják Mac-eszközeiket az Intune-ba. Az Intune kiértékeli, hogy a Mac-eszköz eleget tesz vagy sem többek között a PIN-kódra, a titkosításra, az operációs rendszer verziójára és a rendszerintegritásra vonatkozó követelményeknek.

- További információ a [MacOS-eszközök feltételes hozzáférésének támogatásáról](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>A macOS-hez készült Céges portál alkalmazás nyilvános előzetes verzióban érhető el <!---1484796--->
A macOS-hez készült Céges portál alkalmazás mostantól elérhető a nyilvános előzetes verzióban a feltételes hozzáféréshez a Enterprise Mobility + Securityban. Ez a kiadás a macOS 10.11-es és későbbi verzióit támogatja. Letöltés: [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Új Windows 10-es eszközkorlátozási beállítások    
<!--1063965, 1308850  -->
Ebben a kiadásban új beállítási lehetőségekkel bővült a [Windows 10-es eszközkorlátozási profil](/intune/device-restrictions-windows-10), a következő kategóriákban:

- Windows Defender SmartScreen
- Alkalmazás-áruház

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>A Windows 10-es Endpoint Protection-eszközprofil BitLocker-beállításainak frissítései
<!--1459533 -->    
Ebben a kiadásban a következő fejlesztéseket hajtottuk végre a Windows 10-es Endpoint Protection-eszközprofil BitLocker-beállításainak működésében:
 
- A BitLocker **operációsrendszer-meghajtó beállításai**területen a **BitLocker beállítása nem kompatibilis TPM-lapka**esetén beállításnál a **Letiltás**, korábban lehetőségre kattintva a BitLocker ténylegesen engedélyezve lesz. Javítottuk a beállítást, így kiválasztás esetén most már letiltja a BitLockert.
- A **BITLOCKER operációsrendszer-meghajtó beállításai**területen a **tanúsítványalapú adat-helyreállítási ügynök**beállításnál mostantól explicit módon blokkolhatja a tanúsítványalapú adat-helyreállítási ügynököt. Az ügynök ugyanakkor alapértelmezés szerint engedélyezve van.
- A **Rögzített adatmeghajtók BitLocker-beállításai** között az **Adat-helyreállítási ügynök** beállításnál mostantól letilthatja az adat-helyreállítási ügynököt.
További információ: [Endpoint Protection-beállítások Windows 10 és újabb rendszerű eszközökön](../protect/endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Új bejelentkezett felület az Android Céges portál felhasználók és az alkalmazás-védelmi házirend felhasználói számára <!-- 621669 -->
A végfelhasználók az Androidhoz készült Céges portál használatával most már az Android rendszerű eszköz regisztrációja nélkül is böngészhetnek az alkalmazások között, felügyelhetnek eszközöket, valamint megtekinthetik az informatikai részleg elérhetőségeit. Ezenkívül ha egy végfelhasználó már egy, az Intune alkalmazásvédelmi szabályzata által védett alkalmazást használ, és elindítja az Androidhoz készült Céges portált, már nem kap felszólítást az eszköz regisztrációjára.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Új beállítás az Android Céges portál alkalmazásban az akkumulátor-optimalizálás váltásához <!--1405990-->
Az Androidhoz készült Céges portál alkalmazás **Beállítások** oldala új beállítással bővült, amellyel a felhasználók könnyen kikapcsolhatják az akkumulátor-optimalizálást a Céges portál és a Microsoft Authenticator alkalmazásokhoz. A beállításon látható alkalmazásnév attól függően változik, hogy melyik alkalmazás kezeli a munkahelyi fiókot. Az e-mailek és adatok szinkronizálását végző munkahelyi alkalmazások teljesítménynövelése érdekében az akkumulátor-optimalizálás kikapcsolását javasoljuk. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Többszörös identitás támogatása az iOS-hez készült OneNote számára      <!-- 1234281 -->
A felhasználók mostantól több fiókot (munkahelyit és személyeset) is használhatnak az iOS-hez készült Microsoft OneNote-ban. Anélkül alkalmazhatók alkalmazásvédelmi szabályzatok a munkahelyi jegyzetfüzetekben található céges adatokra, hogy ez hatással lenne a személyes jegyzetfüzetekre. A szabályzat azt például lehetővé teszi, hogy a felhasználó adatokat kereshessen a céges jegyzetfüzetekben, azt viszont megakadályozza, hogy azokat kimásolja onnan, és beillessze egy személyes jegyzetfüzetbe.
 
- További információ azon alkalmazásokról, amelyek támogatják az [alkalmazásvédelmet és a többszörös identitást](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) az Intune-nal.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Új beállítások alkalmazások engedélyezéséhez és letiltásához Samsung Knox Standard-eszközökön
<!-- 1305423 822899-->  
Ebben a kiadásban új [eszközkorlátozási beállítások](../configuration/device-restrictions-android.md) jelennek meg, amelyekkel megadhatók a következő alkalmazáslisták:
 
- Felhasználók által telepíthető alkalmazások
- Felhasználók által nem futtatható alkalmazások
- Az eszközön a felhasználó elől rejtett alkalmazások
 
Az alkalmazás megadható URL-cím vagy csomagnév alapján, vagy kiválasztható a felügyelt alkalmazások listájából.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Új Azure AD alkalmazás-alapú feltételes hozzáférési szabályzat felhasználói felületi hivatkozása az Intune-ból
<!-- 1016201 -->
A rendszergazdák mostantól az alkalmazás-alapú feltételes házirendeket az új feltételes hozzáférési szabályzat felhasználói felületén is megadhatják az Azure AD-munkaterhelésben. A Azure Portal Intune App Protection szakaszának alkalmazás-alapú feltételes hozzáférése ott marad, és párhuzamosan fog megjelenni. Az Intune számítási feladatában az új feltételes hozzáférési szabályzat felhasználói felületének kényelmi hivatkozása is rendelkezésre áll.

- További információ az [alkalmazás-alapú feltételes hozzáférésről az Azure ad-](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)ben.

<!-- ########################## -->
## <a name="july-2017"></a>2017. július

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Android-és iOS-eszközök regisztrálási korlátozásának korlátozása operációsrendszer-verzió alapján  <!--- 1333256,  1245463 --->
Az Intune támogatja az iOS- és Android-eszközök regisztrálásának operációsrendszer-verziószám alapján történő korlátozását. Az **Eszköztípuskorlát** szakaszban az adminisztrátor a platformkonfiguráció megadásával korlátozhatja a regisztrálást egy minimális és maximális operációsrendszer-verziószám között. Az Android operációsrendszer-verzióit főverzió.alverzió.build.javítás formában kell megadni, ahol az alverzió, a build és a javítás megadása nem kötelező. Az iOS-verziókat főverzió.alverzió.build formában kell megadni, ahol az alverzió és a build megadása nem kötelező. További információ [az eszköz regisztrációs korlátozásokról](../enrollment/enrollment-restrictions-set.md).

>[!NOTE]
>Nem korlátozza az Apple készülékregisztrációs programok vagy az Apple Configuratoron keresztül végzett regisztrációt.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Az Android, iOS és macOS rendszerű eszközök személyes tulajdonú eszközökre való regisztrálásának korlátozása  <!--- 1333272,  1333275, 1245709 --->
Az Intune korlátozhatja a személyes eszközök regisztrációját a céges eszközök IMEI-számait tartalmazó engedélyezési lista alapján. Ez a szolgáltatás most már iOS, Android, és macOS rendszereken is elérhető az Intune-ban az eszközök sorozatszámainak használatával. A sorozatszámot az Intune-ba feltöltve előre bejelenthető, hogy az eszköz vállalati tulajdonban van. A regisztrációs korlátozásokkal letilthatók a személyes tulajdonban lévő (BYOD) eszközök, így csak vállalati tulajdonú eszközök regisztrációja lesz engedélyezett. További információ [az eszköz regisztrációs korlátozásokról](../enrollment/enrollment-restrictions-set.md).

Sorozatszámok úgy tölthetők fel, hogy az **Eszközregisztráció** > **Céges készülékazonosítók** szakaszban a **Hozzáadás** gombra kattint, majd feltölt egy .CSV fájlt (fejléc nélkül, két oszloppal a sorozatszámoknak és más részleteknek, például az IMEI-számoknak). A személyes tulajdonban lévő eszközök letiltásához válassza az **Eszközregisztráció** > **Regisztrációs korlátozások** lehetőséget. Az **Eszköztípus-korlátozások** szakaszban válassza az **Alapértelmezés** majd a **Platformkonfigurációk** lehetőséget. **Engedélyezheti** vagy **Tilthatja** a személyes tulajdonban lévő iOS, Android, és macOS rendszerű eszközöket.


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Új eszközbeállítások az eszközök Intune-nal való szinkronizálásának kényszerítéséhez <!-- 711369 -->
Ebben a kiadásban új eszközműveletet vezettünk be, amely a választott eszköz azonnali bejelentkezését kényszeríti ki az Intune-nál. Bejelentkezéskor az eszköz azonnal fogadja az összes hozzárendelt, függőben lévő műveletet vagy szabályzatot.  Ez a művelet segíthet a vonatkozó szabályzatok azonnali ellenőrzésében és a hibák elhárításában anélkül, hogy ki kellene várni a következő ütemezett bejelentkezést.
További információkért lásd: [Eszköz szinkronizálása](../remote-actions/device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Felügyelt iOS-eszközök kényszerített telepítése a legújabb elérhető szoftverfrissítés automatikus telepítésére <!-- 777100 -->
Új szabályzat érhető el a Szoftverfrissítések munkaterületen, amellyel kikényszeríthető a legújabb elérhető szoftverfrissítés automatikus telepítése a felügyelt iOS-eszközöknél. További információt az [iOS-es frissítési szabályzatok konfigurálása](/intune/software-updates-ios) című cikkben talál.

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Ellenőrzési pont – új Mobile Threat Defense-partner  <!-- 954651, 1172027 -->
A mobil eszközök hozzáférését a vállalati erőforrásokhoz a feltételes hozzáférés használatával szabályozhatja a következő, a Microsoft Intune-nal integrálható, a mobil veszélyforrások elleni védelmi megoldás által végzett kockázatértékelés alapján.

#### <a name="how-integration-with-intune-works"></a>Hogyan működik az Intune-nal való integráció?
A kockázatfelmérés a Checkpoint SandBlast Mobile-t futtató eszközökről gyűjtött telemetriai adatokon alapul. Az EMS feltételes hozzáférési szabályzatok az Intune-eszközök megfelelőségi szabályzatai által engedélyezett, az ellenőrzőponton alapuló mobileszköz-kockázatértékelés alapján konfigurálhatók. Az észlelt fenyegetések alapján engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Alkalmazás üzembe helyezése elérhetőként a vállalati Microsoft Storeban <!-- 748101 -->
Ettől a kiadástól kezdve a rendszergazdák a Vállalati Microsoft Áruházat is beállíthatják elérhetőként. Ha ez elérhetőként van beállítva, a felhasználók az alkalmazást anélkül telepíthetik a Céges portál alkalmazásból vagy weboldalról, hogy átirányítanák őket a Microsoft Áruházba.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Felhasználói felületi frissítések a Céges portál webhelyhez <!--1313244 part 1-->
A [Céges portál webhely](https://portal.manage.microsoft.com) felhasználói felületén számos frissítést hajtottunk végre a végfelhasználói élmény javítása érdekében.

- __Továbbfejlesztett alkalmazáscsempék__ Az alkalmazásikonok mostantól automatikusan generált háttérrel jelennek meg az ikon meghatározó színe alapján (amennyiben az érzékelhető). Amennyiben alkalmazható a funkció az ikonra, ez a háttér felváltja a szürke kontúrt, amely eddig keretezte az ikonokat az alkalmazáscsempén.

    Egy hamarosan megjelenő kiadástól kezdve a Céges portál webhely a nagyméretű ikonokat fogja megjeleníteni, amennyiben lehetséges. Javasoljuk, hogy a rendszergazdák minimum 120x120 pixeles, nagy felbontású ikonokkal tegyék közzé az alkalmazásokat. 

- __Navigációs változások__ A navigációs sáv elemei a bal felső sarokban látható hamburger menübe kerültek át. A Kategóriák lap el lett távolítva. A felhasználók mostantól böngészés közben szűrhetik kategória szerint a tartalmat.

- __Kiemelt alkalmazások frissítései__ A webhelyhez hozzáadtunk egy új oldalt, ahol a felhasználók a megadott kiemelt alkalmazások között böngészhetnek, és finomhangolásokat végeztünk a honlap Kiemelt szakaszának felhasználói felületén.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>iBooks-támogatás a Céges portál webhelyhez <!--1231841-->
Egy dedikált oldalt adtunk hozzá a Céges portál webhelyéhez, ahol a felhasználók böngészhetik és letölthetik az iBooks szolgáltatás e-könyveit. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>További ügyfélszolgálati hibaelhárítási részletek <!---  Applies to 1263399, 1326964, 1341642 --->
Az Intune-ban frissült a hibaelhárítási adatok megjelenítésének módja, és bővültek a rendszergazdák és segélyszolgálati munkatársak számára biztosított információk. Az új verzióban egy **Hozzárendelések** nevű táblázat foglalja össze a felhasználó összes, csoporttagságok alapján meglévő hozzárendelését. A lista a következőket tartalmazza:
- Mobilalkalmazásokban
- Megfelelőségi szabályzatok
- Konfigurációs profilok

Ezenkívül az **Eszközök** táblázat kiegészült az **Azure AD-csatlakozás típusa** és az **Azure AD-kompatibilis** oszloppal. További információt a [Segítség a felhasználóknak a problémák elhárításában](../help-desk-operators.md) című cikkben talál.



### <a name="intune-data-warehouse-public-preview"></a>Intune-adattárház (nyilvános előzetes verzió)
Az Intune-adattárház napi adatgyűjtéssel dokumentálja a bérlő állapotelőzményeit. Az adatokat egy Power BI-fájl (PBIX), egy sok elemzőeszközzel kompatibilis OData-hivatkozás, vagy a REST API használatával is elérheti. További információt [Az Intune-adattárház használata](../developer/reports-nav-create-intune-reports.md) című témakörben talál.


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>A Windows 10-es Céges portál alkalmazáshoz elérhető világos és sötét módok <!---676547--->
A végfelhasználók kiválaszthatják a Windows 10 rendszerre készült Céges portál alkalmazás színhasználatát. Ezt a felhasználó a Céges portál alkalmazás Beállítások szakaszában változtathatja meg. A változás az után jelenik meg, hogy a felhasználó újraindítja az alkalmazást. A Windows 10 1607-es és újabb verziói esetén az alkalmazás alapértelmezés szerint a rendszer beállításait használja. A Windows 10 1511-es és korábbi verziói esetén az alkalmazás alapértelmezés szerint a világos üzemmódot használja.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>A végfelhasználók számára a Windows 10 Céges portál alkalmazásban való címkézésének engedélyezése a felhasználók számára <!---807046-->
A végfelhasználók mostantól közvetlenül a Windows 10 rendszerhez készült Céges portál alkalmazásban címkézhetik meg az eszközt, hogy kiválasszák, melyik eszközcsoporthoz tartozik.

<!-- ########################## -->
## <a name="june-2017"></a>2017. június

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Új szerepköralapú adminisztrációs hozzáférés az Intune-rendszergazdák számára   <!-- 1099990 -->  
Az Azure AD feltételes hozzáférési szabályzatok megtekintéséhez, létrehozásához, módosításához és törléséhez új feltételes hozzáférési rendszergazdai szerepkör kerül. Korábban csak a globális rendszergazdák és a biztonsági rendszergazdák rendelkeztek ilyen engedéllyel. Az Intune-rendszergazdák ebben a szerepkör-engedélyben is megadhatók, hogy hozzáférjenek a feltételes hozzáférési házirendekhez.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Vállalati tulajdonú eszközök címkézése sorozatszámmal <!-- 1215070 -->  
Az Intune már támogatja az iOS-, a macOS- és az Android-sorozatszámok feltöltését céges eszközazonosítókként. Jelenleg nem lehet a sorozatszámokat személyes eszközök regisztrálásból való kitiltására használni, mert a rendszer nem ellenőrzi a sorozatszámokat a regisztrálás során. A személyes eszközök sorozatszám alapján történő blokkolása a közeljövőben válik elérhetővé.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Új távoli műveletek iOS-eszközökhöz <!-- 854689 -->
Ebben a kiadásban két új műveletet tettünk elérhetővé az Apple Osztályterem alkalmazást kezelő megosztott iPad-eszközökkel kapcsolatban:

- [Aktuális felhasználó kijelentkezése](../remote-actions/device-logout-user.md) – kijelentkezik egy kiválasztott IOS-eszköz aktuális felhasználóját.
- [Felhasználó eltávolítása](../remote-actions/device-remove-user.md) – Eltávolítja a kiválasztott felhasználót egy iOS-eszköz helyi gyorsítótárából.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Megosztott iPadek támogatása az iOS-es osztályterem alkalmazással <!-- 1044681 -->
Ebben a kiadásban kibővült az iOS-es Osztályterem alkalmazás felügyeletének támogatása, így olyan diákok felügyeletére is van lehetőség, akik a megosztott iPadekre saját felügyelt Apple ID-val jelentkeznek be.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Beépített Intune-alkalmazások módosításai <!-- 1332306 -->
Korábban az Intune számos beépített alkalmazást tartalmazott, melyeket hamar hozzá lehetett rendelni egy kategóriához. A visszajelzések alapján azonban eltávolítottuk ezt a listát, és többé már nem jelennek meg beépített alkalmazások.
Ugyanakkor ha vannak olyan beépített alkalmazások, melyeket korábban már hozzárendelt valamelyik kategóriához, azok továbbra is meg fognak jelenni az alkalmazások listáján. Ezek az alkalmazások szükség szerint továbbra is hozzárendelhetők.
Terveink szerint egy későbbi kiadásban elérhetővé teszünk majd egy egyszerűbb módszert a beépített alkalmazások Azure Portalról történő kiválasztására és hozzárendelésére.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Az Office 365-alkalmazások egyszerűbb telepítése <!--- 1121362 --->
Az új **Office 365 ProPlus** alkalmazástípus megkönnyíti Office 365 ProPlus 2016-alkalmazásoknak a felügyelt, a Windows 10 legújabb verzióját futtató eszközökhöz rendelését. Emellett lehetőség nyílik a Microsoft Project és a Microsoft Visio telepítésére is, ha rendelkezik hozzájuk való saját licencekkel. A kívánt alkalmazásokat a rendszer összecsomagolja, és azok egyetlen alkalmazásként jelennek meg az Intune-konzol alkalmazáslistájában.
További információt a [Office 365-alkalmazások hozzáadása Windows 10 esetén](../apps/apps-add-office365.md) című témakörben talál.


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>A vállalati Microsoft Store offline alkalmazásainak támogatása <!--- 777044 --->
A Vállalati Microsoft Áruházban vásárolt offline alkalmazások mostantól szinkronizálhatók az Azure Portallal. Ezeket az alkalmazásokat eszközcsoportok vagy felhasználói csoportok számára telepítheti. Az offline alkalmazásokat az Intune, és nem az Áruház telepíti.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>A Microsoft Teams mostantól a jóváhagyott alkalmazások alkalmazás-alapú HITELESÍTÉSSZOLGÁLTATÓI listájának része   <!-- 1257019 -->
Az iOS és Android rendszerhez készült Microsoft Teams alkalmazás mostantól a jóváhagyott alkalmazások részét képezi az Exchange-hez és a SharePoint Online-hoz készült alkalmazás-alapú feltételes hozzáférési szabályzatokhoz. Az alkalmazás a Azure Portal Intune App Protection paneljén is konfigurálható az alkalmazás-alapú feltételes hozzáférést használó összes bérlőhöz.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Felügyelt böngésző és alkalmazásproxy-integráció <!-- 1287310 -->
Az Intune Managed Browser integrálható az Azure AD alkalmazásproxy szolgáltatásával így az éppen távolról dolgozó felhasználók is elérhetik a belső webhelyeket. A felhasználók a szokásos módon egyszerűen beírják a hely URL-címét a böngésző címsorába, a Managed Browser pedig átirányítja a kérést az alkalmazásproxy webátjárójára. További információ: [Az internet-hozzáférés kezelése felügyelt böngészőszabályzatokkal](../apps/app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>A Intune Managed Browser új alkalmazás-konfigurációs beállításai <!-- 682951 -->
Ebben a kiadásban további konfigurációs lehetőségekkel bővült az iOS és Android rendszerű Intune Managed Browser alkalmazás. A böngésző alapértelmezett kezdőlapjának és könyvjelzőinek beállítása alkalmazáskonfigurációs szabályzattal is lehetséges.
További információ: [Az internet-hozzáférés kezelése felügyelt böngészőszabályzatokkal](../apps/app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>BitLocker-beállítások Windows 10 rendszerhez  <!-- 951707 -->
A Windows 10 rendszerű eszközök BitLocker-beállításai már új Intune-eszközprofillal is konfigurálhatók. Megkövetelheti például az eszközök titkosítását, és megadhat további, a BitLocker bekapcsolásakor alkalmazandó beállításokat is.
További információ: [Endpoint Protection-beállítások Windows 10 és újabb rendszerű eszközökön](../protect/endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>A Windows 10-es eszközkorlátozási profil új beállításai <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
Ebben a kiadásban új beállítási lehetőségekkel bővült a Windows 10-es eszközkorlátozási profil, a következő kategóriákban:

- Windows Defender
- Mobilhálózati és egyéb kapcsolatok
- Zárolási képernyő felülete
- Személyes adatok védelme
- Keresés
- Windows Reflektorfény
- Microsoft Edge böngésző

További információ a Windows 10 beállításairól: [Windows 10 és újabb rendszerek eszközkorlátozási beállításai](../configuration/device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Az Android rendszerhez készült Céges portál alkalmazás új végfelhasználói élményt nyújt az alkalmazás-védelmi házirendekhez <!--1305217-->
A felhasználók visszajelzései alapján úgy módosítottuk az Androidhoz készült Céges portál alkalmazást, hogy egy **Céges tartalom elérése** gombot is hozzáadtunk. Ez mentesíti a végfelhasználót attól, hogy az egész regisztrációs folyamaton végig kelljen mennie, ha csak olyan alkalmazásokat kíván elérni, amelyek az Intune mobilalkalmazás-felügyelet egyik funkcióját, az alkalmazásvédelmi szabályzatokat támogatják. A változásokat áttekintheti az [újdonságok az alkalmazás felhasználói felületén](whats-new-app-ui.md) című oldalon.

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Új menü művelet a Céges portál egyszerű eltávolításához <!--1164569-->
Felhasználói visszajelzések alapján az androidos Céges portál alkalmazásban új menüművelet jelent meg, amellyel a Céges portál eszközről való eltávolítása kezdeményezhető. A művelet megszünteti az eszköz Intune-felügyeletét, így a felhasználó az alkalmazást is eltávolíthatja az eszközről. Ezekről a változtatásokról bővebb információt talál az [újdonságok az alkalmazás felhasználói felületén](whats-new-app-ui.md) és [Az Android végfelhasználói dokumentációja](/intune-user-help/unenroll-your-device-from-intune-android) témakörökben.

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Az alkalmazások szinkronizálásának fejlesztése a Windows 10 alkotói frissítésével <!--676505-->
A Windows 10-es Céges portál alkalmazás automatikusan kezdeményez szinkronizálást alkalmazástelepítési kérésekhez Windows 10 alkotói frissítést (1703-as verziót) futtató eszközök esetén. Ez csökkenti a függőben lévő szinkronizálás során feltorlódó alkalmazástelepítési műveletek számát. Emellett a felhasználók manuálisan is kezdeményezhetnek szinkronizálást az alkalmazásban. A változásokat áttekintheti az [újdonságok az alkalmazás felhasználói felületén](whats-new-app-ui.md) című oldalon.

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Új interaktív felület a Windows 10-es Céges portál <!---1058938--->
A Windows 10-es Céges portál alkalmazás tartalmazni fog egy interaktív Intune-útmutatót a nem azonosított vagy regisztrált eszközökhöz. Az új útmutató olyan részletes utasításokat tartalmaz, amelyek végigvezetik a felhasználókat a feltételes hozzáférési funkciók azonosításához szükséges Azure Active Directory-regisztrálás és az eszközkezelési funkciókhoz szükséges MDM-regisztrálás lépésein. Az útmutató a Céges portál kezdőlapján lesz elérhető. A felhasználók akkor is használhatják az alkalmazást, ha nem végezték el a regisztrálást és a beléptetést, de így korlátozottan használhatják csak a funkciókat.

Ez a frissítés csak a Windows 10 évfordulós frissítést (1607-es) vagy újabb verziókat futtató eszközökön látható. A változásokat áttekintheti az [újdonságok az alkalmazás felhasználói felületén](whats-new-app-ui.md) című oldalon.


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Általánosan elérhető a Microsoft Intune-konzol és a feltételes hozzáférés rendszergazdai konzolja
Már általánosan elérhető az új Azure Portalbeli Intune rendszergazdai konzolja, valamint a feltételes hozzáférés rendszergazdai konzolja is. Az Azure Portalbeli Intune-nal most már egyetlen és egységes rendszergazdai felületen kezelhető az összes Intune-beli MAM- és MDM-funkció, és mindemellett az Azure AD csoportosítási és célzási képességei is kihasználhatók. Az Azure-ban a feltételes hozzáférés az Azure AD-ben és az Intune-ban széles körű funkciókkal bővült egy egységes konzolon. Felügyeleti szempontból lényeges, hogy az Azure-platformra való váltásnak köszönhetően most már modern böngészők is használhatók.

A portal.azure.com webhelyen elérhető Azure Portalon az Intune mostantól az **előzetes** címke nélkül jelenik meg.

Meglévő ügyfeleinknek jelenleg nincs ezzel kapcsolatos teendője, kivéve, ha olyan üzeneteket kaptak az üzenetközpontban, amelyek a csoportok migrálása érdekében bizonyos műveletek elvégzésére kérik őket. Előfordulhat, hogy az üzenetközpontban értesítés tájékoztatja arról, hogy a migrálás hosszabb időt vehet igénybe a mi oldalunkon jelentkező hibák miatt. Továbbra is intenzíven dolgozunk az érintett ügyfelek migrálásának befejezése érdekében.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Továbbfejlesztett alkalmazáscsempék az iOS-es Céges portál alkalmazásban
Frissítettük a kezdőlapon található alkalmazáscsempék megjelenését annak érdekében, hogy a Céges portálhoz beállított márkaszínek jelenjenek meg rajtuk. További információt az [alkalmazás felhasználói felületének újdonságai](whats-new-app-ui.md) témakörben talál.

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Az iOS-es Céges portál alkalmazásban elérhető a fiókválasztó
Akik iOS-es eszközt használnak, a Céges portálba való bejelentkezés után az új fiókválasztót is látni fogják, ha más Microsoft-alkalmazásokba is munkahelyi vagy iskolai fiókjukkal jelentkeznek be. További információt az [alkalmazás felhasználói felületének újdonságai](whats-new-app-ui.md) témakörben talál.

<!-- ########################## -->
## <a name="may-2017"></a>2017. május

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>MDM-szolgáltató módosítása a felügyelt eszközök regisztrációjának törlése nélkül <!--1103950-->
Már anélkül módosíthatja az MDM-szolgáltatót, hogy fel kellene vennie a kapcsolatot a Microsoft ügyfélszolgálatával, valamint anélkül, hogy el kellene végeznie a meglévő felügyelt eszközök regisztrációjának törlését és a regisztráció újbóli elvégzését. A Configuration Manager-konzolon [módosíthatja az MDM-szolgáltatót](/sccm/mdm/deploy-use/change-mdm-authority) a Configuration Manager (hibrid) beállításról Microsoft Intune (önálló) beállításra, vagy fordítva.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Továbbfejlesztett értesítés a Samsung Knox indítási PIN-kódjaihoz <!--1087143-->
Amikor a végfelhasználóknak a titkosítási megfelelőség céljából be kell állítaniuk egy indítási PIN-kódot a Samsung Knox rendszerű eszközeiken, a megjelenített értesítés átirányítja őket a Gépház alkalmazás megfelelő menüjébe az értesítésre való koppintáskor.  Korábban az értesítésre való koppintással a végfelhasználó a jelszómódosítási képernyőre került.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Az Apple School Manager (ASM) támogatása megosztott iPad-támogatással <!-- 748864, 770395-->

Az Apple készülékregisztrációs programja helyett az Intune az Apple School Manager (ASM) használatával támogatja az iOS-es eszközök alapértelmezett regisztrációját. ASM típusú beléptetésre van szükség a megosztott iPadek Osztályterem alkalmazásának használatához, valamint az adatok Microsoft School Data Sync (SDS) szolgáltatáson keresztüli szinkronizálásához az ASM és az Azure Active Directory között. További információ: [iOS-eszközök regisztrációjának engedélyezése az Apple School Manager-ben](../enrollment/apple-school-manager-set-up-ios.md).

> [!NOTE]
> Ahhoz, hogy megosztott iPadeket konfigurálhasson az Osztályterem alkalmazáshoz, szükség van az iOS oktatási funkcióinak konfigurálására, ami jelenleg nem elérhető az Azure-ban.  Ezt a funkciót hamarosan elérhetővé tesszük.

### <a name="device-management"></a>Eszközkezelés

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Távsegítség nyújtása Android-eszközökhöz a TeamViewer használatával <!-- 675418 -->

Az Intune-ból a külön megvásárolható [TeamViewer](https://www.teamviewer.com) szoftverrel lehet távsegítséget nyújtani az androidos eszközök felhasználóinak. További információt a [Távsegítség nyújtása az Intune által felügyelt Android-eszközökhöz](../remote-actions/teamviewer-support.md) témakörben talál.

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Új alkalmazás-védelmi szabályzatok – feltételek a MAM-hoz <!-- 679864 -->

A nem regisztrált felhasználókra vonatkozóan olyan követelményeket állíthat be a MAM szolgáltatásban, amely az alábbiakat írja elő:

- Az alkalmazás minimális verziószáma
- Az operációs rendszer minimális verziószáma
- A megcélzott alkalmazás minimális Intune App SDK-verziószáma (csak iOS)

A funkció Androidon és iOS-en egyaránt elérhető. Az Intune támogatja az operációs rendszerek, az alkalmazások és az Intune App SDK minimális verziószámának kényszerítését. Az integrált SDK-val rendelkező iOS-es alkalmazások az SDK szintjén állíthatják be a minimális verziószám kényszerítését. A felhasználó nem fog tudni hozzáférni a megcélzott alkalmazáshoz, ha az alkalmazásvédelmi szabályzat minimális követelményei a fenti három szinten nem teljesülnek. Ilyenkor a felhasználó eltávolíthatja a fiókját (többszörös identitást használó alkalmazások esetén), bezárhatja az alkalmazást, vagy frissítheti az operációs rendszert vagy az alkalmazást.

További beállítások konfigurálásával nem zavaró értesítésben lehet javasolni a felhasználóknak az operációs rendszer vagy az alkalmazás frissítését. Az ilyen értesítéseket be lehet zárni, és az alkalmazás a megszokott módon használható.

További információt [Az iOS-es alkalmazásfelügyeleti szabályzat beállításai](../apps/app-protection-policy-settings-ios.md) és [Alkalmazásvédelmi szabályzatok androidos beállításai](../apps/app-protection-policy-settings-android.md) témakörökben talál.

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Az Android for Work alkalmazás-konfigurációinak konfigurálása <!-- 621621 -->
Néhány áruházból származó androidos alkalmazás támogatja a felügyelt konfigurációs lehetőséget is, amellyel a rendszergazda meghatározhatja, hogyan fusson az alkalmazás a munkahelyi profilban. Az Intune most már lehetővé teszi, hogy megnézhesse az alkalmazás által támogatott konfigurációs lehetőségeket, amelyeket az Azure Portalon egy konfigurációtervezővel vagy JSON-szerkesztővel meg is változtathat. További információt az [Alkalmazáskonfigurációk használata Android for Workhöz](../apps/app-configuration-policies-use-android.md) témakörben talál.

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Új alkalmazás-konfigurációs képesség MAM-regisztráció nélkül <!-- 677969 -->
Mostantól a regisztráció nélküli MAM csatornáján keresztül is létrehozhat alkalmazáskonfigurációs szabályzatokat. Ez a funkció megegyezik a mobileszköz-kezelési (MDM) alkalmazáskonfigurációnál elérhető alkalmazáskonfigurációs szabályzatok funkciójával. A regisztráció nélküli MAM-ot használó alkalmazáskonfigurációra [Az internet-hozzáférés Managed Browser-szabályzatokkal való kezelése a Microsoft Intune-ban](../apps/app-configuration-managed-browser.md) című témakörben talál példát.

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Az engedélyezett és a letiltott URL-címek konfigurálása a Managed Browser számára <!-- 682960 -->
Mostantól konfigurálható engedélyezett és letiltott alkalmazások URL-jeinek listája az Intune Managed Browser számára. Ehhez az Azure Portal alkalmazáskonfigurációs beállításait használhatja. Ezt a beállítást attól függetlenül lehet konfigurálni, hogy az felügyelt vagy nem felügyelt eszközön van-e használatban. További információkért lásd: [Az internet-hozzáférés kezelése Managed Browser-szabályzatokkal a Microsoft Intune-ban](../apps/app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Alkalmazás-védelmi házirend helpdesk nézete <!-- 1069473 -->
Az informatikai segélyszolgálat felhasználói mostantól a Hibaelhárítás panelen ellenőrizhetik a felhasználói licencek állapotát és felhasználókhoz rendelt és alkalmazásvédelmi szabályzatokkal kezelt alkalmazások állapotát. További részleteket a [Hibaelhárítás](./help-desk-operators.md) témakörben talál.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Webhely-látogatások vezérlése iOS-eszközökön <!-- 723832 -->
Mostantól az alábbi két módszer valamelyikével szabályozhatja, hogy az iOS-es eszközök felhasználói mely webhelyeket nyithatják meg:

- Engedélyezett és letiltott URL-ek megadása az Apple beépített webtartalomszűrőjével

- Csak a megadott webhelyek elérésének engedélyezése a Safari böngészőnek. Minden megadott webhelyhez könyvjelző jön létre a Safariban.

További információt a [Webtartalomszűrő beállításai iOS-eszközökön](../configuration/ios-device-features-settings.md#web-content-filter) témakörben talál.

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Eszköz engedélyeinek előzetes konfigurálása Android for Work-alkalmazásokhoz <!-- 621614 -->
Az Android for Work-eszközök munkahelyi profiljába telepített alkalmazások esetén konfigurálni lehet az egyes alkalmazások engedélyezési állapotát.  Alapértelmezés szerint az eszközengedélyeket (például hozzáférés a tartózkodási hely adataihoz vagy az eszköz kamerájához) megkövetelő androidos alkalmazások felszólítják a felhasználókat az engedélyek elfogadására vagy elutasítására.  Például ha egy alkalmazás az eszköz mikrofonját használja, a rendszer felszólítja a végfelhasználót, hogy adjon engedélyt az alkalmazásnak a mikrofon használatára. Ezzel a funkcióval engedélyeket határozhat meg a végfelhasználó nevében.  Az engedélyeket háromféleképpen konfigurálhatja: a) automatikus elutasítás a felhasználó értesítése nélkül, b) automatikus jóváhagyás a felhasználó értesítése nélkül, valamint c) a felhasználó elfogadásra vagy elutasításra való felszólítása. További információt az [Android for Work-eszközök korlátozásaira vonatkozó beállítások a Microsoft Intune-ban](../configuration/device-restrictions-android-for-work.md) című témakörben talál.

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Alkalmazás-specifikus PIN-kód definiálása Android for Work-eszközökhöz <!-- 728976, 1102534 -->
A munkahelyi profillal rendelkező, Android for Work-eszközként kezelt Android 7.0 vagy újabb rendszerű eszközök esetén a rendszergazda meghatározhat egy olyan PIN-kód-szabályzatot, amely csak a munkahelyi profilba telepített alkalmazásokra vonatkozik.  A lehetőségek a következők:

- Eszközre érvényes PIN-kód-szabályzat meghatározása – a felhasználónak ezt a PIN-kódot kell használnia az eszköz feloldására.
- Munkahelyi profilra érvényes PIN-kód-szabályzat meghatározása – a rendszer a PIN-kód megadását kéri a felhasználótól a munkahelyi profilban található bármely alkalmazás megnyitásakor.
- Eszközre és munkahelyi profilra egyaránt érvényes szabályzat meghatározása – a rendszergazdának lehetősége van eszközre és munkahelyi profilra egyaránt érvényes, különböző erősségű PIN-kód-szabályzat meghatározására (például 4 számjegyből álló PIN-kód az eszköz feloldásához, illetve 6 számjegyből álló PIN-kód a munkahelyi alkalmazások megnyitásához).

További információt az [Android for Work-eszközök korlátozásaira vonatkozó beállítások a Microsoft Intune-ban](../configuration/device-restrictions-android-for-work.md) című témakörben talál.

> [!NOTE]
> Ez a funkció csak Android 7.0 vagy újabb rendszereken érhető el.  Alapértelmezés szerint a végfelhasználónak lehetősége van két külön-külön definiált PIN-kód használatára, vagy dönthet úgy, hogy a két meghatározott PIN-kód összevonásával csak az erősebbet használja.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Új beállítások Windows 10-es eszközökhöz <!-- 978585 -->
Újabb [windowsos eszközkorlátozási beállításokat](../configuration/device-restrictions-windows-10.md) vezettünk be, amelyek a vezeték nélküli kijelzőkhöz, az eszközfelderítéshez, a feladatváltáshoz vagy a SIM-kártyák hibaüzeneteihez hasonló szolgáltatásokat szabályoznak.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Tanúsítványok konfigurációjának frissítései <!-- 918991 and 823198 -->
SCEP-tanúsítványprofil létrehozásakor iOS, Android és Windows-eszközök esetén a <strong>Tulajdonos nevének formátuma</strong> beállításnál az<strong>Egyéni</strong> lehetőség is választható. A jelen frissítés előtt az <strong>Egyéni</strong> mező csak iOS-eszközök esetén volt elérhető. További információ: [SCEP-tanúsítványprofil létrehozása](../protect/certificates-profile-scep.md).

PKCS-tanúsítványprofil létrehozásakor a **Tulajdonos alternatív neve** értékeként az **Egyéni Azure Ad-attribútum** lehetőség is választható. Az **Egyéni Azure Ad-attribútum** kiválasztásakor a **Részleg** lehetőség is megjelenik. További információ: [PKCS-tanúsítványprofil létrehozása](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Több olyan alkalmazás konfigurálása, amely akkor futtatható, ha egy Android-eszköz kioszk módban van <!-- 662059 -->
Korábban csak egy alkalmazást lehetett úgy konfigurálni, hogy az Android-eszközön teljes képernyős módban fusson. Mostantól több alkalmazás is konfigurálható így az alkalmazásazonosító vagy az áruházi URL-cím használatával, de kiválasztható egy már felügyelt Android-alkalmazás is. További információt [A teljes képernyős mód beállításai](../configuration/device-restrictions-android.md#kiosk) témakörben talál.

<!-- ########################## -->
## <a name="april-2017"></a>2017. április

### <a name="support-for-managing-the-apple-classroom-app"></a>Támogatás az Apple Osztályterem alkalmazás felügyeletéhez
Az iOS-es Osztályterem alkalmazás mostantól felügyelhető iPad eszközökön. Miután telepítette az Osztályterem alkalmazást a tanári iPad-en a megfelelő osztály- és tanulói adatokkal, majd beállította az osztályhoz rendelt tanulói iPad-eket, az alkalmazás segítségével a tanári iPad-ről vezérelheti őket.
További információt [Az iOS oktatási funkcióinak konfigurálása](education-settings-configure-ios.md) című cikkben talál.

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Felügyelt konfigurációs beállítások támogatása Android-alkalmazásokhoz <!-- 621621 -->
A Play áruházban lévő, felügyelt konfigurációs lehetőségeket támogató androidos alkalmazásokat az Intune-nal is lehet konfigurálni.  Ezzel a funkcióval az IT-részleg megnézheti az egyes alkalmazásokban használható konfigurációs értékek listáját, és útmutatásokkal ellátott, kiváló felhasználói felületen konfigurálhatják ezeket az értékeket.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Új Android-szabályzat összetett PIN-kódokhoz <!-- 722069 -->
5\.0-s vagy újabb Android rendszerű eszközökhöz tartozó androidos eszközprofilban meg lehet adni a Komplex numerikus értéket kötelező [jelszótípusként](../configuration/device-restrictions-android.md#password).  Ezzel a beállítással lehet megakadályozni, hogy a felhasználók ismétlődő vagy egymást követő számokból álló PIN-kódot (például 1111 vagy 1234) válasszanak.

### <a name="additional-support-for-android-for-work-devices"></a>Kibővített támogatás Android for Work-eszközökhöz
- **Jelszó-és munkahelyi profil beállításainak kezelése** <!-- 612808 -->

  Az új Android for Work-eszközkorlátozási szabályzattal kezelhetők a felügyelt Android for Work-eszközök jelszó- és munkahelyiprofil-beállításai.

- **A munkahelyi és a személyes profilok közötti adatmegosztás engedélyezése** <!-- 1045102 -->

Az Android for Work-eszközkorlátozási szabályzat új lehetőségekkel segíti a munkahelyi és személyes profil közötti adatmegosztás konfigurálását.

- **A munkahelyi és a személyes profilok közötti másolás és beillesztés korlátozása** <!-- 1046094 -->

  Az Android for Work-eszközökhöz készült új egyéni eszközprofillal megszabhatja, hogy engedélyezi-e a munkahelyi és a személyes profilok közötti másolást és beillesztést.

További információt az [Eszközkorlátozások az Android for Work esetén](../configuration/device-restrictions-android-for-work.md) című témakörben talál.

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>LOB-alkalmazások kiosztása iOS-és Android-eszközökhöz <!-- 1057568 -->
Az [iOS-re](../apps/lob-apps-ios.md) (.ipa-fájlok) és [Androidra](../apps/lob-apps-android.md) (.apk-fájlok) készült üzletági (LOB) alkalmazásokat felhasználókhoz vagy eszközökhöz rendelheti hozzá.


### <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Új eszköz-szabályzatok iOS rendszerhez <!-- 723774, 723815, 723826, 723830 -->
- **A kezdőképernyőn látható alkalmazások** – Azt határozza meg, mely alkalmazásokat láthatják a felhasználók [iOS-es eszközeik kezdőképernyőjén](../configuration/ios-device-features-settings.md#home-screen-layout). Ez a szabályzat megváltoztatja a Kezdőképernyő elrendezését, de nem helyez üzembe semmilyen alkalmazást.

- **Kapcsolódás AirPrint-eszközökhöz** – Azt határozza meg, hogy mely [AirPrint-eszközökhöz](../configuration/ios-device-features-settings.md#airprint) (hálózati nyomtatókhoz) kapcsolódhatnak az adott iOS-es eszköz végfelhasználói.

- **Kapcsolódás AirPlay-eszközökhöz** – Azt határozza meg, hogy mely [AirPlay-eszközökhöz](../configuration/ios-device-features-settings.md) (például Apple TV-hez) kapcsolódhatnak az adott iOS-es eszköz végfelhasználói.

- **Egyéni üzenet a zárolási képernyőn** – Az alapértelmezett helyett egyéni üzenetet állíthat be az iOS-es eszköz zárolási képernyőjére. További információt az [Elveszett eszköz mód aktiválása iOS-eszközökön](../remote-actions/device-lost-mode.md) témakörben talál

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>IOS-alkalmazások leküldéses értesítéseinek korlátozása <!-- 723767 -->
Az Intune-os eszközkorlátozási profilokban már a következő [értesítési beállításokat](../configuration/ios-device-features-settings.md#app-notifications) is konfigurálhatja iOS-es eszközökhöz:

- Adott alkalmazás értesítéseinek teljes körű be- vagy kikapcsolása
- Adott alkalmazás értesítési központban megjelenő értesítéseinek be- vagy kikapcsolása
- Riasztástípus megadása (**None** – Nincs, **Banner** – Szalag vagy **Modal Alert** – Modális riasztás)
- Jelvények engedélyezése az alkalmazásnak
- Értesítési hangok engedélyezése az alkalmazásnak.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>IOS-alkalmazások konfigurálása önálló alkalmazás módban való futtatásra <!-- 737837 -->
Intune-eszközprofillal mostantól konfigurálhatja az iOS-es eszközöket megadott alkalmazások [autonóm egyalkalmazásos módban](../configuration/device-restrictions-ios.md#autonomous-single-app-mode) való futtatására. Ha ez a mód konfigurálva van, és az alkalmazást elindítják, az eszközön nem lehet másik alkalmazást futtatni. Célszerű például így konfigurálni az olyan alkalmazásokat, amelyekkel a felhasználók vizsgázhatnak az eszközön. Az alkalmazás használatának befejezésekor vagy a szabályzat eltávolításakor az eszköz visszatér a szokásos állapotába.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Megbízható tartományok konfigurálása az e-mailekhez és a webes böngészéshez iOS-eszközökön <!-- 723765 -->
Az iOS-es eszközkorlátozási profilokban a következő [tartománybeállításokat](../configuration/device-restrictions-ios.md#domains) konfigurálhatja:

- **Jelöletlen levelezési tartományok** – a felhasználó által az itt megadottól különböző tartománnyal küldött vagy fogadott e-mailek meg lesznek jelölve nem megbízhatóként.

- **Felügyelt webtartományok** – az itt megadott URL-címekről letöltött dokumentumok felügyeltnek minősülnek (csak a Safari esetében).  

- **Jelszavak automatikus kitöltése a Safariban** – a felhasználók csak olyan URL-eken menthetik jelszavaikat a Safariban, amelyek egyeznek az itt megadott mintákkal. Ez a beállítás csak felügyelt módú, többfelhasználós konfigurációval nem rendelkező eszközön használható. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>IOS-Céges portál elérhető VPP-alkalmazások <!-- 748782 -->
A mennyiségi vásárlási program (VPP) keretében vásárolt iOS-es alkalmazásokat **Elérhető** telepítésként hozzárendelheti végfelhasználókhoz, akik Apple Store-fiókkal telepíthetik az alkalmazást.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Az Apple VPP Store-ból származó e-könyvek szinkronizálása <!-- 800878 -->
Az Apple mennyiségi vásárlásra szolgáló áruházából vásárolt [könyvek szinkronizálhatók](../apps/vpp-apps-ios.md) az Intune-nal, és kioszthatók felhasználóknak.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Többfelhasználós felügyelet a Samsung Knox standard-eszközökön <!-- 971988 -->
A Samsung Knox Standard rendszerű eszközökön mostantól használható az Intune [többfelhasználós felügyelete](../enrollment/android-enroll.md). Ilyenkor a felhasználók Azure Active Directory-beli hitelesítő adataikkal jelentkezhetnek be és ki az eszközön, de az központi felügyelet alatt marad, akár használatban van, akár nem.  A bejelentkezett végfelhasználó hozzáfér az alkalmazásokhoz, és a rá érvényes szabályzatok is működnek. A felhasználói kijelentkezéskor az összes alkalmazásadat törlődik.

### <a name="additional-windows-device-restriction-settings----818566---"></a>További Windows-eszközök korlátozási beállításai <!-- 818566 -->
Továbbfejlesztettük a [Windows-eszközök korlátozására](../configuration/device-restrictions-windows-10.md) vonatkozó további beállításokat, például a Microsoft Edge böngésző további támogatását, az eszköz zárolási képernyőjének testreszabását, a Start menü testreszabási funkcióit, a Windows reflektorfény keresési háttérképét és a proxy beállítását.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Többfelhasználós támogatás a Windows 10 alkotói frissítéséhez <!-- 822547 -->
A [többfelhasználós felügyelet](../enrollment/windows-enroll.md) támogatását kiterjesztettük a Windows 10 alkotói frissítését futtató, Azure Active Directory-tartományhoz csatlakozó eszközökre. Ez azt jelenti, hogy az eszközre minden egyes, Azure AD-s hitelesítő adataival bejelentkező általános jogú felhasználó a saját felhasználónevéhez rendelt alkalmazásokat és szabályzatokat kapja meg. A felhasználók jelenleg nem használhatják a Céges portált önkiszolgálói forgatókönyvek esetén (például alkalmazások telepítése).

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Új Start a Windows 10 rendszerű számítógépekhez<!-- 1004830 -->
A Windows 10-es PC-ken már elérhető az új [Újrakezdés eszközművelet](../remote-actions/device-fresh-start.md).  amely eltávolítja a PC-re telepített alkalmazásokat, és automatikusan a Windows legújabb verziójára frissíti a gépet. Így egyszerűbben eltávolíthatók az új gépeken gyakran előtelepítve megtalálható számítógépgyártói (OEM) alkalmazások. A konfigurációval meg lehet adni, hogy a művelet a felhasználói adatokat is eltávolítsa-e.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>További Windows 10-es frissítési útvonalak <!-- 903672 -->
Mostantól olyan [kiadásfrissítési szabályzatok](../configuration/edition-upgrade-configure-windows-10.md) is létrehozhatók, amelyekkel az alábbi Windows 10-kiadásokra frissíthetők az eszközök:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10-es eszközök tömeges regisztrálása <!-- 747607 -->
Mostantól a Windows Configuration Designer (WCD) használatával a Windows 10 alkotói frissítéssel rendelkező nagy számú eszközt csatlakoztathat az Azure Active Directoryhez és az Intune-hoz. Ha Azure AD-bérlőhöz be szeretné kapcsolni a [tömeges MDM-regisztrálást](../enrollment/windows-bulk-enroll.md), a Windows Configuration Designerrel hozzon létre olyan kiépítési csomagot, amely csatlakoztatja az eszközöket az Azure AD-bérlőhöz, majd alkalmazza a csomagot a csoportosan regisztrálni és felügyelni kívánt vállalati tulajdonú eszközökre. A csomag alkalmazása után az Azure AD-be csatlakozik, regisztrálva lesz az Intune-ban, és készen áll az Azure AD-felhasználók bejelentkezésére.  Az Azure AD-felhasználók általános jogú felhasználók ezeken az eszközökön, akik megkapják majd a kijelölt szabályzatokat és a kötelező alkalmazásokat. Az önkiszolgáló és a Céges portált használó módszer jelenleg nincs támogatva.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Új MAM-beállítások a PIN-kód és a felügyelt tárolóhelyek helyeihez <!-- 581122, 736644 -->
Két új alkalmazásbeállítás segíti a mobileszköz-felügyeletet (MAM):

- **Disable app PIN when device PIN is managed** (Alkalmazás PIN-kódjának letiltása felügyelt eszköz-PIN-kód esetén) – a rendszer észleli, hogy van-e eszköz-PIN-kód a regisztrált eszközön, és ha van, mentesíti a felhasználót az alkalmazásvédelmi szabályzatok által megkövetelt alkalmazás-PIN-kód megadása alól, ily módon kevesebbszer kell PIN-kódot megadni a regisztrált eszközökön a MAM-mal védett alkalmazások megnyitásakor. A funkció Androidon és iOS-en egyaránt elérhető.

- **A társzolgáltatások kijelölése, melyekbe menthetők a vállalati adatok** – itt lehet megadni, hogy mely tárolóhelyekre mentse a rendszer a vállalati adatokat. A felhasználók csak a kijelölt tárolóhelyekre menthetnek, a fel nem sorolt tárolóhelyek tehát le lesznek tiltva.

  A támogatott tárhelyszolgáltatások:

  - OneDrive
  - Vállalati SharePoint Online
  - Helyi tárhely

### <a name="help-desk-troubleshooting-portal----907448---"></a>Ügyfélszolgálati hibaelhárítási portál <!-- 907448 -->
Az új [hibaelhárítási portálon](../help-desk-operators.md) az ügyfélszolgálati munkatársak és az Intune-rendszergazdák áttekinthetik a felhasználók és eszközeik listáját, és az Intune technikai problémáinak elhárítását is elvégezhetik.

<!-- ########################## -->
## <a name="march-2017"></a>2017. március

### <a name="support-for-ios-lost-mode---431695--"></a>IOS elveszett mód támogatása <!--431695-->
Az iOS 9.3 és újabb verziói esetében az Intune már az **Elveszett módot** is támogatja. Ezzel letiltható az eszközön minden tevékenység, a zárolási képernyőn pedig üzenet és kapcsolatfelvételhez használható telefonszám jelenik meg.

A végfelhasználó csak akkor tudja feloldani az eszközt, ha a rendszergazda kikapcsolja az Elveszett módot. Ha az Elveszett mód be van kapcsolva, az Intune-konzolon az **Eszköz megkeresése** művelet használatával megjelenítheti az eszköz tartózkodási helyét egy térképen.

A funkció csak felügyelt módban lévő, DEP-pel regisztrált, céges tulajdonban lévő iOS-eszközökön használható.

További információt [A Microsoft Intune-eszközfelügyelet ismertetése](../remote-actions/device-management.md) című témakörben talál.

### <a name="improvements-to-device-actions-report---677150--"></a>Az eszközre vonatkozó műveletek jelentésének fejlesztése <!--677150-->
A jobb teljesítmény érdekében fejlesztéseket végeztünk az eszközműveleti jelentéseknél. A jelentéseken ezen kívül állapot szerinti szűrések is végezhetők. Például olyan módon is szűrhetőek a jelentések, hogy csak a végrehajtott eszközműveletek jelenjenek meg.”

### <a name="custom-app-categories---748805--"></a>Egyéni alkalmazások kategóriái <!--748805-->
Mostantól kategóriákat hozhat létre, szerkeszthet és rendelhet hozzá az Intune-ba felvett alkalmazásokhoz. Jelenleg csak angol nyelven lehet kategóriákat megadni.
Lásd: [Alkalmazás hozzáadása az Intune-hoz](../apps/apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>LOB-alkalmazások kiosztása nem regisztrált eszközökkel rendelkező felhasználók számára <!--748823-->
Mostantól attól függetlenül kioszthat üzletági alkalmazásokat a felhasználóknak, hogy az eszközeik regisztrálva vannak-e az Intune-ban. Ha valamely felhasználó eszköze nincs regisztrálva az Intune-ban, a Céges portál alkalmazás helyett a Céges portál webhelyen telepíthetik az alkalmazást.

### <a name="new-compliance-reports---846671--"></a>Új megfelelőségi jelentések <!--846671-->
A megfelelőségi jelentések megmutatják a cég eszközeinek megfelelőségi helyzetét, így lehetővé válik a felhasználók által tapasztalt megfelelőségi problémák gyors elhárítása. Az alábbi információkat tekintheti meg:

- Az eszközök összesített megfelelőségi állapota
- Az egyes beállítások megfelelőségi állapota
- Az egyes szabályzatok megfelelőségi állapota

A jelentések segítségével egy-egy eszköz részletesebben is megvizsgálható, és ellenőrizhető, hogy mely beállítások és szabályzatok vonatkoznak rá.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Közvetlen hozzáférés az Apple regisztrálási forgatókönyvekhez <!--951869-->
A 2017. január után létrehozott Intune-fiókok esetében az Intune lehetővé tette az Apple regisztrálási forgatókönyvek közvetlen elérését az Azure Portalon elérhető Eszközregisztrációs munkafolyamat használatával. Korábban az Apple-regisztrálási betekintés csak az Azure Portalon található hivatkozásokkal volt elérhető. A 2017 januárja előtt létrehozott Intune-fiókok esetében ezek a funkciók egy egyszeri áttelepítést követően válnak elérhetővé az Azure-ban. Az áttelepítés menetrendje még nem elérhető, de a lehető legrövidebb időn belül tájékoztatást adunk róla. Ha a jelenlegi fiókkal nem érhető el a betekintés, javasoljuk, hogy hozzon létre egy próbafiókot az új lehetőségek kipróbálásához.


<!-- ########################## -->
## <a name="february-2017"></a>2017. február

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>A mobileszköz-beléptetés korlátozásának lehetősége <!--747600, 795782-->
Az Intune új regisztrációs korlátozásokat léptet életbe, amelyek azt szabályozzák, hogy mely mobileszközplatformok számára engedélyezett a regisztráció. Az Intune az alábbi mobileszközplatformokat különbözteti meg: iOS, macOS, Android, Windows és Windows Mobile.

- A mobileszköz-regisztráció korlátozása nem terjed ki a számítógépes ügyfelek regisztrációjára.  
- Csak az iOS és az Android esetében van még egy lehetőség a személyes tulajdonban lévő eszközök regisztrációjának letiltására.

Az Intune mindaddig személyes tulajdonúként jelöli meg az összes új eszközt, amíg az [alábbi cikkben](../enrollment/device-enrollment.md) ismertetett módon a rendszergazda meg nem jelöli azokat céges eszközökként.

### <a name="view-all-actions-on-managed-devices---677150--"></a>A felügyelt eszközökön lévő összes művelet megtekintése <!--677150-->
Az új __Eszközműveletek__ jelentés megmutatja, hogy mely felhasználó hajtott végre távoli műveleteket az eszközön (például gyári alaphelyzetbe állítás), valamint megjeleníti az adott művelet állapotát is. Lásd: [Mi az eszközfelügyelet?](../remote-actions/device-management.md)

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>A nem felügyelt eszközök hozzáférhetnek a hozzárendelt alkalmazásokhoz <!--664691-->
A Céges portál webhely átalakításának részeként az iOS-es és az Androidos felhasználók olyan alkalmazásokat telepíthetnek, amelyek hozzárendelés esetén a nem felügyelt eszközökön regisztráció nélkül érhetők el. Miután a felhasználók az Intune-beli hitelesítő adataikkal bejelentkeztek a Céges portál webhelyre, megtekinthetik a hozzájuk rendelt alkalmazások listáját. A regisztráció nélkül elérhető alkalmazások csomagjait a Céges portál webhelyről lehet letölteni. A telepítéskor regisztrációt kérő alkalmazásokat ez a változás nem érinti, mivel a rendszer az ilyen alkalmazások telepítésekor felszólítja a felhasználókat az eszközök regisztrációjára.

### <a name="custom-app-categories---748805--"></a>Egyéni alkalmazások kategóriái <!--748805-->
Mostantól kategóriákat hozhat létre, szerkeszthet és rendelhet hozzá az Intune-ba felvett alkalmazásokhoz. Jelenleg csak angol nyelven lehet kategóriákat megadni.
Lásd: [Alkalmazás hozzáadása az Intune-hoz](../apps/apps-add.md).

### <a name="display-device-categories---814654--"></a>Eszközök kategóriáinak megjelenítése <!--814654-->
Mostantól az eszközkategória külön oszlopként jelenik meg az eszközlistában. A kategória módosítására szintén van lehetőség az Eszköztulajdonságok panel Tulajdonságok szakaszában. Lásd: [Alkalmazás hozzáadása az Intune-hoz](../apps/apps-add.md).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Windows Update konfigurálása a vállalati beállításokhoz <!--776716-->

A Windows 10 frissítéseinek biztosítására a jövőben a Windows szoftverszolgáltatás használatos. A Windows 10-től kezdődően minden új funkció- és minőségi frissítés magában foglalja valamennyi korábbi frissítés tartalmát. Ennek köszönhetően a legújabb frissítés telepítésével biztosítható, hogy a Windows 10 eszközök teljesen naprakészek legyenek. A Windows korábbi verzióitól eltérően a frissítés egy része helyett már a teljes frissítést telepíteni kell.

A Vállalati Windows Update használatával egyszerűbbé válik a frissítések kezelése, így nem szükséges külön jóváhagyni az egyes frissítéseket az eszközcsoportokhoz. A különböző környezetekben továbbra is kezelhető a kockázat egy frissítéstelepítési stratégia konfigurálásával, és a Windows Update gondoskodik a frissítések megfelelő időpontban történő telepítéséről. A Microsoft Intune lehetővé teszi a frissítési beállítások konfigurálását az eszközökön és a frissítések telepítésének késleltetését. Az Intune nem tárolja a frissítéseket, csak a frissítési szabályzat-hozzárendelést. Az eszközök közvetlenül a Microsoft Update-hez fordulnak a frissítésekért. A **Windows 10 frissítési körök** az Intune használatával konfigurálhatók és kezelhetők. A frissítési kör olyan beállításokat tartalmaz, amelyek a Windows 10 frissítések telepítésének ütemezését és mikéntjét konfigurálják. További információt [A Vállalati Windows Update beállításainak konfigurálása](../protect/windows-update-for-business-configure.md) című témakörben talál.
