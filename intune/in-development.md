---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7150fd7b930e04b375d402877cfe733bb52e9c84
ms.sourcegitcommit: 01a4e09eb27bfed14121de1a4ad56142b7d56eb2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481986"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Fejlesztés a Microsoft Intune – október 2019

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

### <a name="additional-app-configuration-variable-available----4969237----"></a>További elérhető az alkalmazás konfigurációs változója <!-- 4969237  -->
Alkalmazás-konfigurációs házirend létrehozásakor a konfigurációs beállítások részeként felveheti a `AAD Device ID` konfigurációs változót. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** > **Hozzáadás**lehetőséget. Adja meg a konfigurációs szabályzat adatait, és válassza a **konfigurációs beállítások** lehetőséget a **konfigurációs beállítások** panel megtekintéséhez.

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>Sötét mód iOS-Céges portál <!-- 4911422  -->
A sötét üzemmódot az iOS-Céges portál tervezték. Töltse le a vállalati alkalmazásokat, kezelje az eszközöket, és szerezze be támogatását az Ön által választott színsémában. További információ az iOS Céges portálről: [a Microsoft Intune céges portál alkalmazás konfigurálása](company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Ismeretlen forrásból származó alkalmazások telepítésének megakadályozása androidos vállalati eszközökön <!-- 4760025  -->
Az Android Enterprise Work Profile eszköz esetében soha nem lehetséges, hogy a végfelhasználók alkalmazásokat telepítsenek ismeretlen forrásokból a munkahelyi profilba. Lehetősége van arra is, hogy ezt a korlátozást a személyes profilra is kiterjessze. Ha engedélyezi ezt a korlátozást, a végfelhasználók az Android Enterprise Work Profile eszközein is meg lesznek akadályozva az ismeretlen forrásból származó alkalmazások betöltését az eszközük személyes részére. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Az App Protection felhasználói felületének és az iOS-alkalmazások kiépítési felhasználói felületének frissítése <!-- 4102027, 4102029  -->
Az alkalmazás-védelmi szabályzatok és az iOS-alkalmazások létesítési profiljainak az Intune-ban való létrehozásához és szerkesztéséhez szükséges felhasználói felület frissülni fog. A felhasználói felület változásai a következők:
- Egyszerűsített felhasználói felület, amely egy, egy panelen belül tömörített varázsló-stílusú formátumot használ. 
- A létrehozási folyamatra vonatkozó frissítés, amely tartalmazza a hozzárendeléseket.
- A tulajdonságok megtekintésekor beállított összes dolog összefoglaló lapja új házirend létrehozása vagy egy tulajdonság szerkesztésekor. Emellett a tulajdonságok szerkesztésekor az összefoglalás csak a szerkesztett tulajdonságok kategóriájában lévő elemek listáját jeleníti meg.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Házirend-készletek nevű felügyeleti objektumok csoportjainak létrehozása <!-- 3762880  -->
A házirend-készletek lehetővé teszik, hogy a már meglévő felügyeleti entitásokra mutató hivatkozásokat hozzon létre, amelyeket egyetlen fogalmi egységként kell azonosítani, megcélozni és figyelni. A házirend-készletek nem helyettesítik a meglévő fogalmakat vagy objektumokat. A rendszergazda továbbra is hozzárendelheti az egyes objektumokat, ahogy azok még ma működnek. Az egyes objektumokat egy házirend-készlet hivatkozik rá. Ezért az egyes objektumok módosításai a házirend-készletben is megjelennek.  Az Intune-ban a házirend- **készletek** > **Létrehozás** gombra kattintva hozhat létre új házirend-készletet. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Win32-alkalmazások Windows 10 S üzemmódú eszközökön <!-- 3747604  --> 
Win32-alkalmazásokat telepíthet és futtathat a Windows 10 S Mode által felügyelt eszközökön. A Windows Defender Application Control (WDAC) PowerShell-eszközeivel létrehozhat egy vagy több kiegészítő szabályzatot az S üzemmódhoz. Írja alá a kiegészítő szabályzatokat az Eszközkezelő-aláírási portálon, majd töltse fel és terjessze a szabályzatokat az Intune-on keresztül. Az Intune-ban ezt a képességet az **ügyfélalkalmazások** > **Windows 10 S kiegészítő szabályzatok**kiválasztásával találja meg. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Alkalmazás rendelkezésre állásának beállítása dátum és idő alapján <!-- 3510685  -->
Rendszergazdaként konfigurálhatja a szükséges alkalmazás kezdési idejét és határidejét. A kezdési időpontban az Intune felügyeleti bővítmény elindítja az alkalmazás tartalmának letöltését és gyorsítótárazását. Az alkalmazás a határidő lejártakor lesz telepítve. Az elérhető alkalmazások esetében a kezdési idő akkor fog megjelenni, amikor az alkalmazás látható Céges portálban. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások**lehetőséget. Ezután válasszon ki egy adott alkalmazást a listából, vagy válassza a **Hozzáadás** lehetőséget egy új alkalmazás hozzáadásához. Az alkalmazás panelen válassza a **hozzárendelések** > **Csoport hozzáadása**elemet. Állítsa a **hozzárendelés típusát** **kötelező** értékre, majd válassza a **befoglalt csoportok**lehetőséget. Állítsa be, hogy az **alkalmazás minden felhasználó számára kötelező legyen** **, és válassza** a **Szerkesztés** lehetőséget a **végfelhasználói élmény** beállításainak módosításához. A **végfelhasználói élmény** panelen szükség szerint állítsa be a **szoftver rendelkezésre állási idejét** . További információ az alkalmazások hozzáadásáról: [Alkalmazások hozzáadása Microsoft Intunehoz](apps-add.md).


### <a name="require-win32-apps-to-restart----3136567----"></a>Win32-alkalmazások újraindításának megkövetelése <!-- 3136567  -->
A sikeres telepítés után a Win32-alkalmazások újraindítására lehet szükség. Azt is megteheti, hogy az újraindítás előtt ki kell választania az időt (a türelmi időszakot).

### <a name="company-portal-app-on-windows----1808082----"></a>Céges portál alkalmazás Windows rendszeren <!-- 1808082  -->
A Windows rendszerű eszközökön a Céges portál alkalmazás frissülni fog, hogy megjelenjenek a bejelentések a felhasználóknak, még akkor is, ha az alkalmazás be van zárva. A frissítés csak akkor jeleníti meg az elérhető alkalmazások értesítéseit, ha a telepítés állapota befejeződött vagy sikertelen. A Céges portál alkalmazás nem jeleníti meg a szükséges alkalmazások értesítéseit.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Alkalmazás-telepítési állapotüzenetek Céges portál <!-- 2514416  -->
A Céges portál alkalmazás további alkalmazás-telepítési állapotüzenetek jelennek meg a végfelhasználók számára. Az új Win32-függőségi funkciókra az alábbi feltételek érvényesek:
- Az alkalmazás telepítése nem sikerült. A rendszergazda által definiált függőségek nem teljesültek.
- Az alkalmazás telepítése sikeresen megtörtént, de újraindítást igényel.
- Az alkalmazás telepítése folyamatban van, de a folytatáshoz újraindítás szükséges.

### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Microsoft Edge Beta társítása macOS-hez <!-- 4678761  -->
A Microsoft Edge Beta legújabb verzióját a macOS rendszerű eszközökhöz hozzáadhatja és hozzárendelheti az Intune-hoz. Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** > **Microsoft Edge-MacOS** **hozzáadása** > elemet. Ezután rendelje hozzá a Microsoft Edge Beta-t a kívánt csoportokhoz. A Microsoft AutoUpdate (MAU) naprakészen tartja a Microsoft Edge-t. A Microsoft Edge-vel kapcsolatos további információkért lásd: [webes elérés kezelése a Microsoft Edge és a Microsoft Intune használatával](manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune app Protection-szabályzatok (alkalmazás) Android és iOS rendszerű eszközökön lehetővé teszik a szervezeti fiókok alkalmazás-értesítési tartalmának szabályozását. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy nem érhető el az összes alkalmazás-kompatibilis alkalmazáshoz. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz <!-- 3041956  -->
Az androidos munkahelyi Profilos eszközökön elérhető alkalmazások telepítéséhez megtekintheti az alkalmazás telepítési állapotát és a felügyelt Google Play-alkalmazások telepített verzióját. További információ: [az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](android-enterprise-overview.md) -nal és a [felügyelt Google Play-alkalmazás típusa](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Új eszköz konfigurációs beállításai felügyelt iOS-és iPadOS-eszközökhöz <!-- 5199328  -->
IOS-és iPadOS-eszközökön létrehozhat egy profilt a szolgáltatások és beállítások korlátozásához az eszközökön (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **iOS/iPadOS** for platform > **eszköz** a profil típusának korlátozásai). Új beállítások is megadhatók: 
- Hozzáférés hálózati meghajtóhoz a Files alkalmazásban  
- Hozzáférés USB-meghajtóhoz a Files alkalmazásban 
- Wi-Fi mindig be van kapcsolva 

Az aktuális beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-ios.md).

Érintett kiadások:
- iOS 13,0 és újabb verziók
- iPadOS 13,0 és újabb verziók

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Az Automatikus csatlakozás beállítás el lesz távolítva a Wi-Fi profilokban az Android és az Android Enterprise rendszerhez <!-- 5021055  -->
Az Android és az Android rendszerű vállalati eszközökön létrehozhat egy Wi-Fi profilt különböző beállítások konfigurálásához (**eszköz konfigurációja** > **profilok** > **create Profile** > **Android** vagy **Android Enterprise** a platform > a **Wi-Fi** profil típusa). A **kapcsolat automatikus** beállítása el lesz távolítva, mivel az [Android nem támogatja](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Ha ezt a beállítást egy Wi-Fi profilban használja, észreveheti, hogy a **Csatlakozás automatikusan** nem fog működni. Semmilyen műveletet nem kell elvégeznie, de vegye figyelembe, hogy ez a beállítás el lesz távolítva az Intune felhasználói felületén.

Az aktuális beállítások megtekintéséhez lépjen az [Android Wi-Fi beállítások](wi-fi-settings-android.md) vagy az [Android Enterprise Wi-Fi beállítások](wi-fi-settings-android-enterprise.md)elemre.

Érintett kiadások:
- Android
- Vállalati Android

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Globális HTTP-proxy létrehozása androidos vállalati eszköz tulajdonosi eszközein <!-- 4816339  -->
Az Android Enterprise rendszerű eszközökön létrehozhat egy VPN-profilt különböző VPN-ügyfelekkel (az**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **Android Enterprise** for platform > **eszköz tulajdonosa > A profil** típusa > a **kapcsolat**). Egy globális HTTP-proxy konfigurálható úgy, hogy az megfeleljen a szervezete webes böngészési szabványainak. A HTTP-webhelyekre ugrást használó alkalmazások ezt a proxyt használják.

Érintett kiadások:
- Androidos vállalati eszköz tulajdonosa

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Új eszköz belső vezérlőprogram-konfigurációs felületének profilja a Windows 10 és újabb rendszerű eszközökhöz <!-- 2266073  -->
Windows 10 és újabb rendszereken létrehozhat egy eszköz-konfigurációs profilt a beállítások és szolgáltatások vezérléséhez (**eszköz konfigurációja** > **profilok** > **create Profile** > **Windows 10 és újabb verziók** a platformhoz). Egy új, az eszköz belső vezérlőprogram-konfigurációs felületének profilja lesz, amely lehetővé teszi az Intune számára az UEFI-(BIOS-) beállítások kezelését.

A konfigurálható beállítások áttekintését itt tekintheti meg: a [szolgáltatások és beállítások alkalmazása az eszközökön a Microsoft Intune eszköz profiljainak használatával](device-profiles.md).

Érintett kiadások:
- Windows 10 RS5 (1809) és újabb verziók egyes OEM-eken

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>PKCS-tanúsítványok macOS rendszerhez  <!-- 1333650                -->
A macOS rendszerű eszközökön teljes körű támogatást biztosítunk a PKCS-tanúsítványokhoz. A felhasználók a Testreszabás tárgya és a tulajdonos alternatív neve mezők használatával telepíthetik a felhasználói és az eszköz tanúsítványait. Egy új beállítás is elérhető lesz, amely lehetővé teszi az összes alkalmazás elérését, ami lehetővé teszi, hogy az összes társított alkalmazás hozzáférhessen a titkos kulcshoz. A beállítással kapcsolatos további információkért tekintse meg a következő Apple-dokumentációt: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Származtatott hitelesítő adatok a mobileszközök tanúsítványokkal való kiépítéséhez      <!--  1736036, 1736037, 1772050      --> 
Támogatni fogjuk a származtatott hitelesítő adatok támogatását, amely támogatja a *National Institute of Standards and Technology (NIST) 800-157* szabványt a tanúsítványok eszközökre való központi telepítéséhez.  A származtatott hitelesítő adatok a személyes személyazonosság-ellenőrzés (PIV) vagy a Common Card (CAC) kártya (például intelligens kártya) használatára támaszkodnak. A felhasználók a számítógépen lévő intelligens kártyával hitelesítik magukat, majd a származtatott hitelesítő szolgáltató által igényelt folyamatot követően beküldenek egy tanúsítványt a felügyelt eszközhöz.   

A származtatott hitelesítő adatoknak a tanúsítvány lekéréséhez való használatának folyamata eltér a SCEP-vagy PKCS-tanúsítvány-profilok használatával, de a végeredmény ugyanaz, mint az alkalmazások hitelesítéséhez, a VPN-hez, a Wi-Fi-hez vagy az e-mailekhez használható hitelesítési tanúsítványokkal rendelkező mobileszközök. profilok.   

További információ: [származtatott PIV hitelesítő adatok](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) a www.nccoe.nist.gov címen.

A származtatott hitelesítő adatok kezdeti kiadása támogatja az iOS rendszeren a Entrust Datacard, a közbenjáró és a DISA fajtatiszta-t. A későbbi kiadásokban a további platformok és származtatott hitelesítőadat-szolgáltatók is támogatottak lesznek.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Eszközök beléptetése

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>Itt adhatja meg, hogy az operációs rendszer mely operációsrendszer-verzióit regisztrálja munkahelyi profillal vagy az eszközök rendszergazdai regisztrálásával <!-- 4350697 -->
Az Intune-eszközök típusának korlátozásai segítségével megadhatja, hogy mely felhasználói eszközök fogják használni az Android Enterprise munkahelyi profil regisztrációját vagy az Android-eszközök rendszergazdai regisztrációját. Ehhez nyissa meg az **Intune** > **eszközök beléptetése** > **regisztrációs korlátozás** > **Létrehozás korlátozás** > **eszköz típusának korlátozása** > **platform beállításait**.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Az Autopilot-eszközökhöz tartozó eszköznév értékének szerkesztése <!-- 4816775 -->
Szerkesztheti az Azure AD-hez csatlakoztatott Autopilot-eszközökhöz tartozó eszköznév értékét. Ehhez nyissa meg az **Intune** > **eszközök beléptetése** > **Windows-regisztráció** > **Windows Autopilot** > **eszközök** > Válassza ki az eszközt, > a jobb oldali ablaktáblában módosítsa az eszköz neve értéket > **Mentés** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS-eszközök esetén szabja testre a beléptetési folyamat adatvédelmi képernyőjét a Céges portál <!-- 4394993  -->
A Markdown segítségével testre szabhatja a Céges portál adatvédelmi képernyőjét, amelyet a végfelhasználók az iOS-regisztráció során látnak. Pontosabban testreszabhatja azon dolgok listáját, amelyeket a szervezete nem lát vagy tesz az eszközön.

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Az Autopilot-eszközökhöz tartozó címke értékének szerkesztése<!-- 4816775 -->
Az Autopilot-eszközöknél szerkesztheti a csoport címkének értékét. Ehhez nyissa meg az **Intune** > **eszközök beléptetése** > **Windows-regisztráció** > **Windows**Autopilot  > **eszközök** > Válassza ki az eszközt, > a jobb oldali ablaktáblán módosítsa a csoport címke értékét > **Mentés** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Felhasználói felület frissítése a Windows 10-es frissítési gyűrűk létrehozásához és szerkesztéséhez  <!-- 4099089          -->   
Az Intune-hoz készült Windows 10-es frissítési körök frissített létrehozási és szerkesztési felhasználói felületét mutatjuk be.  A felhasználói felület módosításai a következőket tartalmazzák:  
- Leegyszerűsítheti a meglévő felhasználói élményt egy olyan varázsló-stílusú formátum használatával, amely egy panelen van tömörítve. Ez a felhasználói felületi frissítés elvégzi a panel terjeszkedését, amely megköveteli, hogy az informatikai szakemberek részletesen megvizsgálják a mély paneles útvonalakat.   
- Módosítsa a létrehozás folyamatát a hozzárendelések belefoglalásához.  
- A tulajdonságok megtekintésekor beállított összes dolog összegzett oldalának hozzáadása egy új frissítési kör létrehozása előtt és egy tulajdonság szerkesztésekor. A szerkesztéskor az összefoglalás csak a szerkesztett tulajdonságok egy kategóriáján belüli elemek listáját jeleníti meg.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Felhasználói felület frissítése iOS-szoftverfrissítések létrehozásához és szerkesztéséhez  <!-- 4099090        -->   
Az iOS-szoftverfrissítések az Intune-ba való frissítésének és szerkesztésének új felhasználói felületét mutatjuk be. A felhasználói felület módosításai a következőket tartalmazzák:
- Leegyszerűsítheti a meglévő felhasználói élményt egy olyan varázsló-stílusú formátum használatával, amely egy panelen van tömörítve. Ez a felhasználói felületi frissítés elvégzi a panel terjeszkedését, amely megköveteli, hogy az informatikai szakemberek részletesen megvizsgálják a mély paneles útvonalakat.  
- Az iOS szoftverfrissítési házirend létrehozási folyamata frissíti a hozzárendeléseket is 
- Az iOS-szoftverfrissítés házirendje tartalmazni fogja a tulajdonságok megtekintésekor beállított összes dolog összefoglaló lapját, mielőtt új házirendet hozna létre, és egy tulajdonságot szerkeszt. A szerkesztéskor az összefoglalás csak a szerkesztett tulajdonságok egy kategóriáján belüli elemek listáját jeleníti meg.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>JAMF-felügyeletet igénylő macOS-felhasználói csoportok célzása <!-- 4061739 -->
A felhasználók adott csoportjainak megcélzásával megkövetelheti, hogy a macOS-eszközeiket a JAMF kezelje. Ez a célzás lehetővé teszi, hogy a JAMF-megfelelőségi integrációt a macOS-eszközök egy részhalmazára alkalmazza, míg más eszközöket továbbra is az Intune kezel. Azt is lehetővé teszi, hogy fokozatosan áttelepítse a felhasználók eszközeit az egyik MDM a másikba.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Új korlátozások a Windows-eszközök átnevezéséhez <!-- 3478938 -->
Az eszközök neveinek a következő szabályokat kell követniük:
- legfeljebb 15 karakter (63 bájtnál kisebbnek vagy azzal egyenlőnek kell lennie, a záró NULL értékkel nem együtt)
- Nem null vagy üres karakterlánc
- Engedélyezett ASCII: Betűk (a-z, A-Z), számok (0-9) és kötőjelek
- Engedélyezett Unicode: karakter > = 0x80, érvényes UTF8-nak kell lennie, IDN-leképezhető (RtlIdnToNameprepUnicode sikeres; lásd: RFC 3492)
- A nevek nem tartalmazhatnak számokat, és nem kezdődhet számmal.
- Nincs szóköz a névben
- Nem engedélyezett karakterek: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Szoftverfrissítések központi telepítése macOS-eszközökre <!-- 3194876 -->
A macOS-eszközök csoportjaira telepíthet szoftverfrissítéseket. Ez a szolgáltatás kritikus, belső vezérlőprogram, konfigurációs fájl és egyéb frissítéseket tartalmaz. Frissítéseket küldhet a következő eszköz-bejelentkezéshez, vagy kiválaszthat egy heti ütemtervet a frissítések központi telepítésére a beállított időpontokban. Ez a funkció segít abban az esetben, ha az eszközöket a szokásos munkaidőn kívül szeretné frissíteni, vagy ha az ügyfélszolgálat teljes mértékben személyzettel rendelkezik. Emellett részletes jelentést is kap az összes olyan macOS-eszközről, amelyen telepítve vannak a frissítések. Az egyes frissítések állapotának megjelenítéséhez a jelentést eszközönként is megtekintheti.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>Új Android-jelentés az eszközök áttekintése oldalon <!-- 2984353  -->
Új jelentést fogunk hozzáadni az eszközök áttekintése oldalhoz, amely megjeleníti, hogy hány androidos eszköz van regisztrálva az egyes eszközkezelés megoldásokban. Ez a diagram a munkahelyi profilt, a teljes körűen felügyelt, a dedikált és az eszköz-rendszergazda által beléptetett eszközök számát jeleníti meg. A jelentés megtekintéséhez válassza az **Intune** > **eszközök**@no__t – 3 –**Áttekintés**lehetőséget.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>A Windows Autopilot üzembe helyezési jelentései <!-- 3856172  -->
Az új jelentések részletesen ismertetik a Windows Autopilot szolgáltatásban üzembe helyezett összes eszközt. Ezek az adatszolgáltatások az üzembe helyezés után 30 napig lesznek elérhetők. A jelentés megtekintéséhez nyissa meg az **Intune** > **eszközök beléptetése** > **monitor** >  Autopilot-alapú**üzembe helyezést**.

### <a name="updated-support-experience-------5012398------"></a>Frissített támogatási élmény   <!--  5012398    -->
A folyamatos tökéletesítések részeként frissíteni fogjuk a konzolon belüli támogatási élményt az Intune-ban.  Fejlesztjük a konzolon belüli keresést és visszajelzést a gyakori problémákról, és egyszerűsítheti a munkafolyamatot, hogy kapcsolatba lépjen a támogatási szolgálattal.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még:
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new.md).




