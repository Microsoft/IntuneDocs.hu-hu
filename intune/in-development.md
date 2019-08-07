---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833550"
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

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>IOS-alkalmazások eltávolítási viselkedésének szabályozása az eszköz regisztrációjának törlése során <!-- 3504144 -->
A rendszergazdák kezelhetik, hogy egy alkalmazás törlődik-e, vagy megmaradnak-e az eszközön, ha az eszköz regisztrálva van a felhasználó vagy az eszköz csoport szintjén. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Üzleti alkalmazások kategorizálása Microsoft Store <!-- 3926922 -->
A vállalati alkalmazások Microsoft Store kategorizálható. Ehhez válassza az **Intune** > **ügyfélalkalmazások** > alkalmazásai lehetőséget > Válassza ki a Microsoft Store for Business alkalmazást > **alkalmazás-információ** > **kategóriát**. A legördülő menüben rendeljen hozzá egy kategóriát.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune app Protection-szabályzatok (alkalmazás) Android és iOS rendszerű eszközökön lehetővé teszik a szervezeti fiókok alkalmazás-értesítési tartalmának szabályozását. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy nem érhető el az összes alkalmazás-kompatibilis alkalmazáshoz. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz <!-- 3041956  -->
Az androidos munkahelyi Profilos eszközökön elérhető alkalmazások telepítéséhez megtekintheti az alkalmazás telepítési állapotát és a felügyelt Google Play-alkalmazások telepített verzióját. További információ: [az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](android-enterprise-overview.md) -nal és a [felügyelt Google Play-alkalmazás típusa](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Néhány nem felügyelt iOS-eszközre vonatkozó korlátozás csak az iOS 13,0-es kiadással lesz felügyelve <!-- 4867809  -->
Egyes beállítások a felügyelt eszközökre lesznek érvényesek, az iOS 13,0-es kiadásával kezdődően. Ezek a beállítások a következők:

- Alkalmazás-áruház, dokumentumok megtekintése, játékok
  - Alkalmazás-áruház
  - Explicit iTunes, zene, podcast vagy Hírek tartalma
  - Game Center ismerősök hozzáadása
  - Többrésztvevős játékok
- Beépített alkalmazások
  - Kamera
    - FaceTime
  - Safari
    - Autofill
- Felhő és tárolás
  - Biztonsági mentés az iCloudba
  - ICloud-dokumentumok szinkronizálásának letiltása
  - ICloud-kulcstartó szinkronizálásának letiltása

Ha ezek a beállítások az iOS 13,0-es kiadás előtt konfigurálhatók és nem felügyelt eszközökhöz vannak hozzárendelve, a rendszer továbbra is alkalmazza a beállításokat a nem felügyelt eszközökre. Az eszközök az iOS 13,0-re való frissítés után is érvényben maradnak. Ezek a korlátozások el lesznek távolítva a nem felügyelt eszközökön, amelyek biztonsági mentése és visszaállítása megtörtént. 

Az aktuális beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-ios.md).

Érintett kiadások:  
- iOS 13,0 és újabb verziók

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>Új beállítások és meglévő beállítások módosítása az iOS-és macOS-eszközök funkcióinak korlátozásához <!-- 4867699 4867709  -->
Létrehozhat olyan profilokat, amelyekkel korlátozhatja a beállításokat iOS és MacOS rendszerű eszközökön (az**eszköz konfigurációs** >  **profiljainak** >  **létrehozása** >  írja be > **eszköz korlátozásait**). A következő funkciók lesznek hozzáadva:

- A **MacOS** > -**eszköz korlátozása** > a**felhőre és**a tárhelyre az új **handoff** beállítással letilthatja a felhasználók számára, hogy egy MacOS-eszközön dolgozhassanak, és folytatják a munkát egy másik MacOS vagy iOS rendszerű eszközön.
  Ha szeretné megtekinteni az aktuális beállításokat, lépjen a [MacOS eszközbeállítások lehetőségre, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-macos.md).
- Az **iOS** > -**eszközök korlátozásai**esetében néhány változás van:
  - **A beépített alkalmazások** > megkeresik**az iPhone-t (csak felügyelt eszköz esetén)** : Új beállítás, amely letiltja ezt a funkciót a Find My app szolgáltatásban. 
  - **A beépített alkalmazások** > megkeresik**a barátaikat (csak felügyelt eszköz esetén)** : Új beállítás, amely letiltja ezt a funkciót a Find My app szolgáltatásban. 
  -  > **Wi-Fi állapot vezeték nélküli módosítása (csak felügyelt eszköz esetén)** : Új beállítás, amely megakadályozza, hogy a felhasználók bekapcsolják vagy kikapcsolják a Wi-Fi-t az eszközön.
  - **Billentyűzet és szótár** > **QuickPath (csak felügyelt eszköz esetén)** : Új beállítás, amely letiltja a QuickPath funkciót.
  - **Felhő és tárolás**: A **tevékenységek folytatását** a rendszer átnevezi a **handoff**.

  Az aktuális beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-ios.md).

Érintett kiadások:  
- macOS 10,15 és újabb verziók
- iOS 13 és újabb verziók

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>Azon alkalmazások, fájlok, dokumentumok és mappák szabályozása, amelyek akkor jelennek meg, amikor a felhasználó bejelentkezik macOS-eszközökre <!--3914202  -->
A MacOS rendszerű eszközökön is engedélyezheti és konfigurálhatja a szolgáltatásokat (az**eszköz konfigurációs** > **profiljaiban** > **létrehozhat egy profilt** > **MacOS** platform > **eszköz funkciói** a következőhöz: Profil típusa). 

Az új bejelentkezési elemek beállításai szabályozzák, hogy mely alkalmazások, fájlok, dokumentumok és mappák legyenek megnyitva, amikor a felhasználó bejelentkezik a regisztrált eszközre. 

Az aktuális beállítások megtekintéséhez válassza a [MacOS-eszköz szolgáltatás beállításai az Intune-ban](macos-device-features-settings.md)lehetőséget.

Érintett kiadások:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>Új funkciók androidos vállalati dedikált eszközökhöz többalkalmazásos módban <!-- 3755304 3041943 3041946  -->
Az androidos vállalati dedikált eszközökön a funkciók és a beállítások a kioszk stílusú környezetben vezérelhetők. Ehhez válassza az eszköz- **konfigurációs** > **profilok** > **create Profile** > **Android Enterprise** for platform > **eszköz tulajdonosa, eszköz korlátozások** a profil típusa beállításnál.

A következő funkciók lesznek hozzáadva:
- **Dedikált eszközök** > **multi-app**: A **virtuális Kezdőlap gombja** az eszközön lévő felugró ablak használatával jeleníthető meg, vagy a képernyőn lebegve, így a felhasználók áthelyezhetik azt.
- **Dedikált eszközök** > **multi-app**: A zseblámpa- **hozzáférés** lehetővé teszi a felhasználók számára a zseblámpa használatát. 
- **Dedikált eszközök** > **multi-app**: A **Media Volume Control** lehetővé teszi a felhasználók számára az eszköz adathordozó-kötetének vezérlését egy csúszka használatával. 
- **Dedikált eszközök** > **multi-app**:  Képernyővédő engedélyezése, egyéni rendszerkép feltöltése és a képernyővédő megjelenítésének vezérlése.

Az aktuális beállítások megtekintéséhez lépjen az [Android Enterprise Device Settings elemre az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md#dedicated-device-settings).

Érintett kiadások:  
- Androidos vállalati dedikált eszközök

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Új alkalmazás-és konfigurációs profilok Android Enterprise teljes körűen felügyelt eszközökhöz <!-- 3574215  -->
A profilok használatával olyan beállításokat konfigurálhat, amelyek VPN-, e-mail-és Wi-Fi-beállításokat alkalmaznak az Android Enterprise teljes körűen felügyelt eszközökre. A következőket teheti:
- Az alkalmazások profiljaival telepítheti az Outlook, a Gmail és a Nine Work e-mail-beállításait.
- A megbízható főtanúsítványok beállításainak üzembe helyezéséhez használjon eszköz-konfigurációs profilokat.
- A VPN-és Wi-Fi-beállítások üzembe helyezéséhez használjon eszköz-konfigurációs profilokat.

A felhasználók a VPN-, Wi-Fi-és e-mail-profilokhoz tartozó felhasználónevével és jelszavával hitelesítve lesznek. A tanúsítvány alapú hitelesítés jelenleg nem érhető el. 

Érintett kiadások:  
- Android Enterprise teljes körűen felügyelt

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Az iOS rendszerhez készült IKEv2 VPN-profilok támogatása <!-- 1943438 -->
A IKEv2 protokoll használatával VPN-profilokat hozhat létre az iOS natív VPN-ügyfél számára. A IKEv2 egy új kapcsolattípus az **eszköz konfigurációs** > **profiljaiban** > **profil** > létrehozása**iOS** for platform > **VPN** a profil típusa > **Beállítások**.

Ezek a VPN-profilok a natív VPN-ügyfelet konfigurálja. Tehát a felügyelt eszközökre nincs telepítve vagy leküldve VPN-ügyfélalkalmazások. Ehhez a szolgáltatáshoz regisztrálni kell az eszközöket az Intune-ban (MDM-regisztráció).

Az aktuálisan konfigurálható VPN-beállítások megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS](vpn-settings-ios.md)-eszközökön a Microsoft Intune.

A következőre vonatkozik: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Eszközök beléptetése

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>További képernyők kihagyása a beállítási Asszisztensben <!--4877451 -->
Készülékregisztrációs program profilokat is beállíthat, hogy kihagyja a következő beállítási asszisztens képernyőket: 
- Képernyő időpontja
- Touch ID beállítása

Ehhez nyissa meg az **eszközök** > beléptetése**Apple-regisztráció** > beléptetési**program** jogkivonatait > Válassza ki a tokent > **profilok** > válasszon egy profilt > **Tulajdonságok** > **szerkesztése** a **beállítási asszisztens testreszabása**mellett.
További információ a beállítási asszisztens testreszabásáról: [Apple beléptetési profil létrehozása ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Android beléptetési eszköz rendszergazdai támogatása <!-- 4869749  -->
Az Android-eszköz rendszergazdai beléptetési beállítása az Android-eszközök regisztrálási lapjára lesz felvéve (**Intune** > -**eszközök regisztrációjának** > **Android**-regisztrációja). Az Android-eszközök rendszergazdája alapértelmezés szerint továbbra is engedélyezve lesz az összes bérlő esetében.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS-eszközök esetén szabja testre a beléptetési folyamat adatvédelmi képernyőjét a Céges portál <!-- 4394993  -->
A Markdown segítségével testre szabhatja a Céges portál adatvédelmi képernyőjét, amelyet a végfelhasználók az iOS-regisztráció során látnak. Pontosabban testreszabhatja azon dolgok listáját, amelyeket a szervezete nem lát vagy tesz az eszközön.

<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Az Android-eszköz hardveres oldalán található szám összeállítása <!-- 4461910  -->
Minden Android-eszköz hardver lapján egy új bejegyzés tartalmazni fogja az eszköz operációs rendszerének Build-számát.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Az eszköz automatikus törlési időkorlátjának beállítása 30 nap alatt <!--4231059  -->
Az automatikus eszköz kitakarítási időkorlátja az utolsó bejelentkezés után 30 nap (az aktuális korlát helyett a 90 nap) állítható be. Ehhez nyissa meg az **Intune** > -**eszközök** > **telepítő** > **eszközének karbantartási szabályait**.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

### <a name="default-scope-tag----3702875---"></a>Alapértelmezett hatókör címkéje <!-- 3702875 -->
Elérhető lesz egy új beépített alapértelmezett hatóköri címke. A hatóköri címkéket támogató összes címkézetlen Intune-objektum automatikusan hozzá lesz rendelve az alapértelmezett hatókör-címkéhez. Az **alapértelmezett** hatókör címkét a rendszer hozzáadja az összes meglévő szerepkör-hozzárendeléshez, hogy a paritást a felügyeleti felülettel fenntartsa. Ha nem szeretné, hogy a rendszergazda megtekintse az alapértelmezett hatókörű címkékkel rendelkező Intune-objektumokat, távolítsa el az alapértelmezett hatóköri címkét a szerepkör-hozzárendelésből. Ez a funkció hasonló a System Center Configuration Manager biztonsági hatókörök szolgáltatásához.

<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="import-and-export-security-baselines------3408610------------"></a>Biztonsági alaptervek importálása és exportálása    <!--3408610          -->  
Hozzáadjuk a biztonsági alapkonfigurációk exportálásához és importálásához szükséges képességet. Ez a funkció lehetővé teszi a testreszabásokat, és megoszthatja őket az Intune-környezetek között.

<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még:
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new.md).




