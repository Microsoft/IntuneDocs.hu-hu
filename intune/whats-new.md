---
title: Újdonságok a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Az Azure-beli Intune-portál újdonságai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 29483c7694ef96a026942a670aa8a52cb8cc8857
ms.sourcegitcommit: f75386986d24e7d5dd63a3f1a0a014cb52056063
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560132"
---
# <a name="whats-new-in-microsoft-intune"></a>Újdonságok a Microsoft Intune-ban

Heti összesítésben olvashat a Microsoft Intune újdonságairól. Megtalálhatja a [fontos megjegyzéseket](#notices), a [korábbi kiadásokat](whats-new-archive.md)és az [Intune szolgáltatás frissítéseinek kiadásával](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)kapcsolatos információkat is. 

> [!Note]
> A [havi frissítés](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) akár három napot is igénybe vehet, és a következő sorrendben fog megjelenni:
> - 1\. nap: Ázsia és a Csendes-óceáni térség (APAC)
> - 2\. nap: Európa, Közel-Kelet, Afrika (EMEA)
> - 3\. nap: Észak-Amerika
> 
> Egyes funkciók bevezetése több hetet igénybe vehet, így előfordulhat, hogy nem elérhetők a felhasználók számára az első héten.
>
> A kiadásban a közelgő funkciók listáját a [fejlesztés lapon](in-development.md) találja.

**RSS-hírcsatorna**: Értesítést kaphat az oldal frissítésekor, ha a következő URL-címet másolja és beillesztette a hírcsatorna-olvasóba:`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-august-12-2019"></a>2019. augusztus 12-i hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>IOS-alkalmazások eltávolítási viselkedésének szabályozása az eszköz regisztrációjának törlése során <!-- 3504144   -->
A rendszergazdák kezelhetik, hogy egy alkalmazás el lett-e távolítva vagy meg van-e őrizni az eszközön, ha az eszköz regisztrálva van a felhasználó vagy az eszköz csoport szintjén. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Üzleti alkalmazások kategorizálása Microsoft Store <!-- 3926922 -->
A vállalati alkalmazások Microsoft Store kategorizálható. Ehhez válassza az **Intune** > **ügyfélalkalmazások** > alkalmazásai lehetőséget > Válassza ki a Microsoft Store for Business alkalmazást > **alkalmazás-információ** > **kategóriát**. A legördülő menüben rendeljen hozzá egy kategóriát.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Testreszabott értesítések Microsoft Intune alkalmazás felhasználói számára <!-- 4843354  -->
Az Androidhoz készült Microsoft Intune alkalmazás mostantól támogatja az egyéni leküldéses értesítések megjelenítését, valamint az iOS és Android rendszerhez készült Céges portál alkalmazásokban nemrégiben hozzáadott támogatással való összehangolását. További információt [az egyéni értesítések küldése az Intune-ban](custom-notifications.md)című témakörben talál.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>Új funkciók androidos vállalati dedikált eszközökhöz többalkalmazásos módban <!-- 3755304 3041943 3041946   -->
Az Intune-ban a funkciók és beállítások az androidos vállalati dedikált eszközökön a kioszk stílusú környezetben vezérelhetők (az**eszköz konfigurációs** > **profiljai** > az Android-**profil létrehozása** >  **Enterprise** for platform > **eszköz tulajdonosa, eszközök korlátozásai** a profil típusa).

Ebben a frissítésben a következő szolgáltatások lesznek hozzáadva:

- **Dedikált eszközök** > **multi-app**: A **virtuális Kezdőlap gombja** az eszközön lévő felugró ablak használatával jeleníthető meg, vagy a képernyőn lebegve, így a felhasználók áthelyezhetik azt.
- **Dedikált eszközök** > **multi-app**: A zseblámpa- **hozzáférés** lehetővé teszi a felhasználók számára a zseblámpa használatát. 
- **Dedikált eszközök** > **multi-app**: A **Media Volume Control** lehetővé teszi a felhasználók számára az eszköz adathordozó-kötetének vezérlését egy csúszka használatával. 
- **Dedikált eszközök** > **multi-app**:  **Képernyővédő engedélyezése**, egyéni rendszerkép feltöltése és a képernyővédő megjelenítésének vezérlése.

Az aktuális beállítások megtekintéséhez lépjen az [Android Enterprise Device Settings elemre az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md#dedicated-device-settings).

Érintett kiadások:  
- Androidos vállalati dedikált eszközök

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Új alkalmazás-és konfigurációs profilok Android Enterprise teljes körűen felügyelt eszközökhöz <!-- 3574215 3574238 3574235 3574232   -->
A profilok használatával olyan beállításokat konfigurálhat, amelyek a VPN-, e-mail-és Wi-Fi-beállításokat alkalmazzák az androidos vállalati eszköz tulajdonos (teljes mértékben felügyelt) eszközeire. Ebben a frissítésben a következőket teheti:

- Alkalmazás- [konfigurációs szabályzatok](app-configuration-policies-use-android.md) használatával telepítheti az Outlook, a Gmail és a Nine Work e-mail-beállításait.
- A [megbízható főtanúsítványok beállításainak](certificates-configure.md)üzembe helyezéséhez használjon eszköz-konfigurációs profilokat.
- A VPN-és [Wi-Fi-](wi-fi-settings-android-enterprise.md) beállítások üzembe helyezéséhez használjon eszköz [-](vpn-settings-android-enterprise.md) konfigurációs profilokat.

> [!IMPORTANT]
> Ezzel a funkcióval a felhasználók a VPN-, Wi-Fi-és e-mail-profilokhoz tartozó felhasználónevével és jelszavával hitelesítik magukat. A tanúsítvány alapú hitelesítés jelenleg nem érhető el. 

Érintett kiadások:  
- Androidos vállalati eszköz tulajdonosa (teljes mértékben felügyelt)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>A macOS-eszközökre való bejelentkezéskor megnyíló alkalmazások, fájlok, dokumentumok és mappák szabályozása <!--3914202   -->
A MacOS-eszközökön engedélyezheti és konfigurálhatja a szolgáltatásokat (az**eszköz konfigurációs** >  > **profiljai** > a profil**MacOS** for platform > **eszköz funkciói** a profilok típusához) . 

Ebben a frissítésben új bejelentkezési elemek beállításával szabályozhatja, hogy mely alkalmazások, fájlok, dokumentumok és mappák nyílnak meg, amikor a felhasználó bejelentkezik a regisztrált eszközre. 

Az aktuális beállítások megtekintéséhez válassza a [MacOS-eszköz szolgáltatás beállításai az Intune-ban](macos-device-features-settings.md)lehetőséget.

Érintett kiadások:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>A határidők lecserélik a Windows Update gyűrűk lefoglalt újraindítási beállításait   <!-- 4464404        -->
A legutóbbi Windows- [karbantartási változások](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)összehangolásához az Intune Windows 10-es frissítési gyűrűk mostantól [támogatják a határidők beállításait](windows-update-settings.md). A *határidők* határozzák meg, hogy egy eszköz Mikor telepítse a szolgáltatást és a biztonsági frissítéseket.  A Windows 10 1903-es vagy újabb verzióját futtató eszközökön a *határidők* felülírják a felvállalt újraindítási konfigurációkat.  A jövőben a *határidők* felülírják a Windows 10 korábbi verzióiban a megjelenő újraindítást is.  

Ha nem konfigurálja a határidőket, az eszközök továbbra is használják a kapcsolódó újraindítási beállításokat, azonban az Intune a későbbi frissítésekben nem [fogja támogatni a](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) felvállalt újraindítási beállítások támogatását.  

Tervezze meg a *határidők* használatát a Windows 10-es eszközökön. A *határidők* beállításainak megadása után módosíthatja az Intune-konfigurációkat, hogy a rendszer ne konfigurálja a folyamatban lévő újraindítást. Ha a nincs konfigurálva értékre van állítva, az Intune leállítja a beállítások kezelését az eszközökön, de nem távolítja el a beállítás utolsó konfigurációját az eszközről. Ezért a felvállalt újraindításhoz beállított utolsó konfigurációk aktív állapotban maradnak, és csak az Intune-tól eltérő módon módosítják ezeket a beállításokat. Később, amikor az eszközök Windows-verziója megváltozik, vagy ha a *határidőkhöz* tartozó Intune-támogatás a Windows rendszerű eszközökre bővül, az eszköz a már meglévő új beállításokat fogja használni.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>Több Microsoft Intune tanúsítvány-összekötő támogatása   <!--   4704642      -->
Az Intune mostantól támogatja több [Microsoft Intune tanúsítvány-összekötő](certficates-pfx-configure.md)telepítését és használatát a PKCS-műveletekhez. Ez a változás támogatja a terheléselosztást és az összekötő magas rendelkezésre állását. Minden összekötő-példány feldolgozhatja a tanúsítványkérelmek az Intune-ból.  Ha az egyik összekötő nem érhető el, a többi összekötő továbbra is feldolgozza a kérelmeket. 

Több összekötő használatához nincs szükség az összekötő szoftver legújabb verziójára való frissítésre.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>Új beállítások és meglévő beállítások módosítása az iOS-és macOS-eszközök funkcióinak korlátozásához <!-- 4867699 4867709   -->
Az iOS és MacOS rendszerű eszközök beállításainak korlátozására szolgáló profilokat hozhat létre (az**eszköz konfigurációs** > **profiljai** > a platform típusaként**iOS** vagy **MacOS** **profilt** > hozhatnak létre > **Eszköz korlátozásai**). Ez a frissítés a következő funkciókat tartalmazza:

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

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>Néhány nem felügyelt iOS-eszközre vonatkozó korlátozás csak az iOS 13,0-es kiadással lesz felügyelve <!-- 4867809   -->
Ebben a frissítésben egyes beállítások csak a felügyelt eszközökre vonatkoznak az iOS 13,0 kiadással. Ha ezek a beállítások az iOS 13,0-es kiadás előtt konfigurálhatók és nem felügyelt eszközökhöz vannak hozzárendelve, a rendszer továbbra is alkalmazza a beállításokat a nem felügyelt eszközökre. Az eszközök az iOS 13,0-re való frissítés után is érvényben maradnak. Ezek a korlátozások el lesznek távolítva a nem felügyelt eszközökön, amelyek biztonsági mentése és visszaállítása megtörtént. 

Ezek a beállítások a következők:

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

Az aktuális beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-ios.md).

Érintett kiadások:  
- iOS 13,0 és újabb verziók

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>Továbbfejlesztett eszköz állapota macOS FileVault titkosításhoz  <!-- 4944983         -->
A macOS rendszerű eszközökön a FileVault titkosításhoz több [eszköz állapotüzenetek](encryption-monitor.md#device-encryption-status) is frissültek.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>A jelentések egyes Windows Defender víruskereső-keresési beállításai sikertelen állapotot mutatnak <!-- 5119229 -->
Az Intune-ban házirendeket hozhat létre a Windows Defender víruskereső használatával a Windows 10 rendszerű eszközök vizsgálatához (az**eszköz konfigurációs** > **profiljai** > a**Windows 10-es és újabb** **profilok** > létrehozása a következőhöz: platform > **eszközre vonatkozó korlátozások** a profil típusa > **Windows Defender Antivirus**). A jelentéskészítés elvégzéséhez szükséges **napi gyors vizsgálat** és rendszervizsgálati idő a sikertelen állapotot jelzi, ha valójában sikeres állapotot jelent. 

Ebben a frissítésben ez a viselkedés kijavítva van. Így a **napi gyors vizsgálat** és a rendszervizsgálatok elvégzéséhez szükséges idő a sikeres ellenőrzések sikerességi állapotát jeleníti **meg** , és sikertelen állapotot jelez, ha a beállítások nem lesznek alkalmazva. 

A Windows Defender víruskereső beállításaival kapcsolatos további információkért lásd: [Windows 10 (és újabb) eszközbeállítások, amelyekkel engedélyezheti vagy korlátozhatja a szolgáltatásokat az Intune használatával](device-restrictions-windows-10.md#windows-defender-antivirus). 

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="default-scope-tags----3702875----"></a>Alapértelmezett hatókör-Címkék <!-- 3702875  -->
Mostantól elérhető egy új beépített alapértelmezett hatóköri címke. A hatóköri címkéket támogató összes nem címkézett Intune-objektum automatikusan hozzá lesz rendelve az alapértelmezett hatókör-címkéhez. Az **alapértelmezett** hatókör címkét a rendszer hozzáadja az összes meglévő szerepkör-hozzárendeléshez a paritásnak a rendszergazdai felülettel való fenntartásához. Ha nem szeretné, hogy a rendszergazda az alapértelmezett hatókör címkével lássa el az Intune-objektumokat, távolítsa el az alapértelmezett hatóköri címkét a szerepkör-hozzárendelésből. Ez a funkció a System Center Configuration Manager biztonsági hatókörök funkciójának hasonló. További információ: a [RBAC és a hatókör-címkék használata](scope-tags.md)a terjesztéshez.

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Android beléptetési eszköz rendszergazdai támogatása <!-- 4869749   -->
Az Android-eszköz rendszergazdai beléptetési lehetősége hozzá lett adva az Android-eszközök regisztrálási lapjához (**Intune** > -**eszközök regisztrációjának** > **Android**-regisztrációja). Az Android-eszközök rendszergazdája alapértelmezés szerint továbbra is engedélyezve lesz az összes bérlő esetében.  További információ: Android- [eszközök rendszergazdai regisztrációja](android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>További képernyők kihagyása a beállítási Asszisztensben <!--4877451  -->
Készülékregisztrációs program profilokat is beállíthat, hogy kihagyja a következő beállítási asszisztens képernyőket:
- iOS rendszerhez
    - Megjelenését
    - Expressz nyelv
    - Előnyben részesített nyelv
    - Eszközről az eszközre való Migrálás
- MacOS esetén
    - Képernyő időpontja
    - Touch ID beállítása

A beállítási asszisztens testreszabásával kapcsolatos további információkért lásd: [Apple beléptetési profil létrehozása iOS rendszerhez](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) és [Apple regisztrációs profil létrehozása MacOS rendszerhez ](device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Felhasználói oszlop hozzáadása az Autopilot-eszköz CSV-feltöltési folyamatához <!-- 3823054 -->
Mostantól hozzáadhat egy felhasználói oszlopot az Autopilot-eszközökhöz tartozó CSV-feltöltéshez. Ez lehetővé teszi a felhasználók tömeges hozzárendelését a CSV importálásakor. A CSV-sorok új formátuma így néz ki: sorozatszám, Windows-termék-azonosító, hardver-kivonat, opcionális-csoport-címke, opcionálisan hozzárendelt felhasználó. További információ: [Windows-eszközök regisztrálása az Intune-ban a Windows Autopilot használatával](enrollment-autopilot.md).


### <a name="device-management"></a>Eszközkezelés

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Az eszköz automatikus törlési időkorlátjának beállítása 30 nap alatt <!--4231059  -->
Megadhatja az automatikus eszköz tisztítási időkorlátját, amely az utolsó bejelentkezés után 30 nap (az előző korlát helyett a 90 nap). Ehhez nyissa meg az **Intune** > -**eszközök** > **telepítő** > **eszközének karbantartási szabályait**.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Az Android-eszköz hardveres oldalán található szám összeállítása <!-- 4461910   -->
Minden Android-eszköz hardver lapján megjelenik egy új bejegyzés, amely tartalmazza az eszköz operációs rendszerének Build-számát. További információ: [az eszköz adatainak megtekintése az Intune-ban](device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Hét augusztus 5-ig, 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>A zebra Technologies egy támogatott OEM OEMConfig az androidos vállalati eszközökön  <!-- 4843713 -->

Az Intune-ban létrehozhat eszköz-konfigurációs profilokat, és beállításokat alkalmazhat az androidos vállalati eszközökre a OEMConfig használatával (**eszköz-konfigurációs** > **profilok** > **létrehozási profil létrehozása**  >   **Android Enterprise** for platform > **OEMConfig** ).

Ebben a frissítésben a zebra Technologies a OEMConfig által támogatott eredeti berendezésgyártó (OEM). További információ a OEMConfig-ről: [androidos vállalati eszközök használata és kezelése a OEMConfig](android-oem-configuration-overview.md)-mel.

Érintett kiadások:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>2019. július 22-i hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>Felhasználók és csoportok testreszabott értesítései    <!-- 16766574          -->
Egyéni leküldéses értesítések küldése a Céges portál alkalmazásból az Intune-nal felügyelt iOS-és Android-eszközökön lévő felhasználóknak. Ezek a mobil leküldéses értesítések nagyon testreszabhatók ingyenes szöveggel, és bármilyen célra használhatók. A szervezet különböző felhasználói csoportjaira is megcélozhatja őket. További információ: [Egyéni értesítések](custom-notifications.md).

#### <a name="googles-device-policy-controller-app----3041950----"></a>A Google eszköz házirend-vezérlő alkalmazás <!-- 3041950  -->
A felügyelt kezdőképernyő alkalmazás mostantól hozzáférést biztosít a Google androidos eszköz házirend-alkalmazásához. A felügyelt kezdőképernyő alkalmazás egy egyéni indító, amelyet az Intune-ban regisztrált eszközökhöz az Android Enterprise (AE) dedikált eszközként használnak többalkalmazásos kioszk mód használatával. Elérheti az Android-eszköz házirend-alkalmazását, vagy megtekintheti a felhasználókat az Android-eszközök házirend-alkalmazásához, támogatási és hibakeresési célból. Ez az indítási képesség akkor érhető el, amikor az eszköz regisztrálja és zárolja a felügyelt kezdőképernyőn. A funkció használatához nincs szükség további telepítésekre.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>Az Outlook védelmi beállításai iOS és Android rendszerű eszközökhöz <!-- 3212619 -->
Mostantól az iOS és az Android rendszerhez készült általános alkalmazások és adatvédelem konfigurációs beállításait is konfigurálhatja az egyszerű Intune rendszergazdai vezérlőkkel az eszközök regisztrálása nélkül. Az alkalmazás általános beállításainak megadása a rendszergazdák számára lehetővé teszi, hogy az Outlookot az iOS és az Android rendszerhez a regisztrált eszközökön is kezelhesse. Az Outlook-beállításokkal kapcsolatos további információkért lásd: [az Outlook telepítése iOS-és Android-alkalmazásokhoz konfigurációs beállítások](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Az "alkalmazhatósági szabályok" használata Windows 10-es eszközök konfigurációs profiljainak létrehozásakor <!-- 2549910 eeready   idstaged -->

Windows 10-es eszköz konfigurációs profiljait hoz létre (az**eszköz konfigurációs** > **profiljai** > a platformra > az **alkalmazhatósági szabályokhoz**tartozó**profil létrehozása** > **Windows 10** profilt). Ebben a frissítésben létrehozhat egy alkalmazhatósági **szabályt** , hogy a profil csak egy adott kiadásra vagy adott verzióra vonatkozzon. Létrehozhat például egy olyan profilt, amely lehetővé teszi egyes BitLocker-beállítások használatát. A profil hozzáadása után alkalmazzon egy alkalmazhatósági szabályt, hogy a profil csak a Windows 10 Enterprise rendszert futtató eszközökre vonatkozzon.

Alkalmazhatósági szabály hozzáadásához lásd: [alkalmazhatósági szabályok](device-profile-create.md#applicability-rules).

Érintett kiadások: Windows 10 és újabb

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>A jogkivonatok használata az eszközre jellemző információk hozzáadásához az egyéni profilokban iOS-és macOS-eszközökhöz <!-- 3330008  -->
Az iOS-és MacOS-eszközökön egyéni profilokat használhat az Intune-ban nem beépített beállítások és szolgáltatások konfigurálásához (az**eszköz konfigurációs** > **profiljai** > az**iOS** vagy MacOS rendszerhez készült**profil** > létrehozása)a platform > **Egyéni** profil típusa). Ebben a frissítésben tokeneket adhat hozzá a `.mobileconfig` fájlokhoz az eszközre vonatkozó információk hozzáadásához. Hozzáadhat `Serial Number: {{serialnumber}}` például a konfigurációs fájlhoz az eszköz sorozatszámának megjelenítéséhez.

Egyéni profil létrehozásához tekintse meg az [Egyéni iOS-beállítások](custom-settings-ios.md) vagy a MacOS-es [Egyéni beállítások](custom-settings-macos.md)című témakört.

Érintett kiadások:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Új Configuration Designer az Android Enterprise-hoz készült OEMConfig-profil létrehozásakor <!-- 3712769   -->
Az Intune-ban létrehozhat egy OEMConfig-alkalmazást használó eszköz-konfigurációs profilt (az eszköz konfigurációjának > profiljait, > profilt hozhat létre > Android Enterprise platformon > OEMConfig). Ha ezt teszi, a rendszer egy JSON-szerkesztőt nyit meg a sablon és az értékek módosításával. 

Ez a frissítés egy továbbfejlesztett felhasználói élményt biztosító konfigurációs tervezőt tartalmaz, amely az alkalmazásban beágyazott részleteket jeleníti meg, beleértve a címeket, a leírásokat és egyebeket. A JSON-szerkesztő továbbra is elérhető, és a Configuration Designerben végrehajtott módosításokat jeleníti meg.

Az aktuális beállítások megtekintéséhez válassza az androidos [vállalati eszközök használata és kezelése a OEMConfig](android-oem-configuration-overview.md)-mel című témakört.

Érintett kiadások: Vállalati Android

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Frissített felhasználói felület a Windows Hello konfigurálásához  <!-- 4089576            -->
Frissítettük a konzolt, amelyben az [Intune-t a vállalati Windows Hello használatára konfigurálja](windows-hello.md). A konfigurációs beállítások mostantól a konzol ugyanazon paneljén érhetők el, ahol engedélyezheti a Windows Hello használatát. 


#### <a name="intune-powershell-sdk----4924113---"></a>Intune PowerShell SDK <!-- 4924113 --> 
Az Intune PowerShell SDK, amely a Microsoft Graphon keresztül támogatja az Intune API-t, a 6.1907.1.0 verzióra frissült. Az SDK mostantól a következőket támogatja:
- Együttműködik Azure Automationokkal.
- A csak az alkalmazásra vonatkozó hitelesítési olvasási műveleteket támogatja. 
- Támogatja a rövid rövidített neveket aliasként.
- Megfelel a PowerShell elnevezési konvencióinak. Pontosabban a `PSCredential` (z) paramétert ( `Connect-MSGraph` a parancsmagon) át `Credential`lett nevezve a következőre:.
- A nem támogatja manuálisan a `Content-Type` fejléc értékének megadását a `Invoke-MSGraphRequest` parancsmag használatakor.

További információ: [POWERSHELL SDK Microsoft Intune Graph API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>Regisztrációs korlátozások frissítései  <!-- 2871968 -->
Az új bérlők regisztrálási korlátozásai frissültek, így az androidos vállalati munkahelyi profilok alapértelmezés szerint engedélyezve vannak. A meglévő bérlők semmilyen változást nem fognak tapasztalni. Az androidos vállalati munkahelyi profilok használatához továbbra is [össze kell kapcsolnia Intune-fiókját a felügyelt Google Play](https://docs.microsoft.com/intune/connect-intune-android-enterprise)-fiókkal.

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Felhasználói felületi frissítések az Apple-regisztrációhoz és a regisztrációs korlátozásokhoz <!--4089575, 4089579  -->
A következő folyamatok mindegyike egy varázsló stílusú felhasználói felületet használ:
- Apple-eszközök beléptetése. További információ: iOS- [eszközök automatikus regisztrálása az Apple Készülékregisztrációs program](device-enrollment-program-enroll-ios.md).
- Regisztráció korlátozásának létrehozása. További információkért lásd a [regisztrációs korlátozások beállítása](enrollment-restrictions-set.md)című témakört.

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>A vállalati eszközök azonosítóinak előzetes konfigurációjának kezeléséhez Android Q-eszközökhöz <!-- 4711509  idmiss -->
Az Android Q (v10)-ben a Google eltávolítja a MDM-ügynököket a örökölt felügyelt (eszköz-rendszergazda) Android-eszközökön az eszköz-azonosító információk összegyűjtéséhez.  Az Intune olyan funkcióval rendelkezik, amely lehetővé teszi a rendszergazdák számára, hogy előre konfigurálják az eszközök [sorozatszámait vagy IMEI-listáját](https://docs.microsoft.com/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number) , hogy automatikusan címkével lássa el ezeket az eszközöket a vállalat tulajdonában. Ez a funkció nem működik az eszköz rendszergazdája által felügyelt Android Q-eszközökön.  Függetlenül attól, hogy az eszköz sorozatszáma vagy IMEI-je fel van-e töltve, a rendszer mindig személyesnek tekinti az Intune-regisztráció során.  A regisztráció után manuálisan is átválthatja a vállalati tulajdont.  Ez csak az új regisztrációkat érinti, és a meglévő regisztrált eszközöket nem érinti.  A munkahelyi profillal felügyelt Android-eszközöket ez a változás nem érinti, és továbbra is működik, ahogy ma.  Emellett az eszköz-rendszergazdaként regisztrált Android Q-eszközök nem tudnak a sorozatszámot vagy IMEI-t jelenteni az Intune-konzolon az eszköz tulajdonságaiként.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Az androidos vállalati regisztrációk (munkahelyi profil, dedikált eszközök és teljes körűen felügyelt eszközök) ikonjai módosultak. <!-- 4977730 -->
Az Android Enterprise beléptetési profilok ikonjai módosultak. Az új ikonok megjelenítéséhez nyissa meg az **Intune** > **regisztrációs** > **Android-regisztráció** > a beléptetési **profilok**szakaszban.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Windows diagnosztikai adatgyűjtés módosítása <!-- 4113859 -->
A diagnosztikai adatgyűjtés alapértelmezett értéke megváltozott a Windows 10 1903-es vagy újabb verzióját futtató eszközökön. A Windows 10 1903-től kezdődően a diagnosztikai adatgyűjtés alapértelmezés szerint engedélyezve van. A Windows diagnosztikai adatok fontos műszaki adatok a Windows-eszközökről az eszközről, valamint a Windows és a kapcsolódó szoftverek működésének módjáról. További információ: [Windows diagnosztikai adatok konfigurálása a szervezetben](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Az Autopilot-eszközök is a "teljes" telemetria vannak kiválasztva, kivéve, ha az Autopilot-profilban nincs más beállítva a [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Eszközkezelés

#### <a name="improve-device-location---3855417----"></a>Az eszköz helyének javítása<!-- 3855417  -->
Az eszköz megkeresése művelettel nagyíthatja az eszköz pontos koordinátáit. Az elveszett iOS-eszközök megkeresésével kapcsolatos további információkért lásd: [elveszett iOS-eszközök](device-locate.md)megkeresése.


### <a name="device-security"></a>Eszköz biztonsága

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Speciális beállítások a Windows Defender-tűzfalhoz (nyilvános előzetes verzió)  <!--  1311949     -->  
Az Intune használatával kezelheti az egyéni tűzfalszabályok az Endpoint Protection [eszköz konfigurációs profiljának részeként](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) a Windows 10 rendszerben. A szabályok megadhatják a bejövő és kimenő viselkedést az alkalmazásokhoz, a hálózati címekhez és a portokhoz. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>Frissített felhasználói felület a biztonsági alapkonfigurációk kezeléséhez   <!-- 4091125     -->
A biztonsági alaptervek [létrehozásához és szerkesztéséhez](security-baselines.md#create-the-profile) az Intune-konzolon frissítettük az élményt. A módosítások a következők:

Egyszerűbb varázsló-stílusú formátum, amely egyetlen panelre van tömörítve. egy panelen belül. Ez az új kialakítás a panel terjeszkedésével foglalkozik, amely megköveteli, hogy az informatikai szakemberek több különálló ablaktáblán is megvizsgálják a részletezést.  
Mostantól a létrehozási és szerkesztési élmény részeként is létrehozhat hozzárendeléseket, ahelyett, hogy később vissza kellene térnie az alaptervek hozzárendeléséhez. Az új alapkonfiguráció létrehozása előtt megtekintheti a beállítások összegzését, és egy meglévőt is szerkeszthet. A szerkesztéskor az összefoglalás csak a szerkesztett tulajdonságok egy kategóriájában beállított elemek listáját jeleníti meg.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019. július 15-i hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Felügyelt kezdőképernyő és felügyelt beállítások ikonjai <!-- 4918107 -->
Frissült a felügyelt kezdőképernyő alkalmazás ikonja és a **felügyelt beállítások** ikon. A felügyelt kezdőképernyő alkalmazást csak az Intune-ban regisztrált eszközök használják az Android Enterprise (AE) dedikált eszközként, és több alkalmazásból álló kioszk módban futnak. A felügyelt kezdőképernyő alkalmazással kapcsolatos további információkért lásd: [az Android Enterprise rendszerhez készült Microsoft Managed Home Screen alkalmazás konfigurálása](app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Androidos eszközök házirendje androidos vállalati dedikált eszközökön <!-- 4918136 -->
Az Android-eszközök házirendje alkalmazást a felügyelt kezdőképernyő alkalmazás hibakeresési képernyőjéről érheti el. A felügyelt kezdőképernyő alkalmazást csak az Intune-ban regisztrált eszközök használják az Android Enterprise (AE) dedikált eszközként, és több alkalmazásból álló kioszk módban futnak. További információ: [az Android Enterprise rendszerhez készült Microsoft Managed Home Screen alkalmazás konfigurálása](app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates----3902931---"></a>iOS-Céges portál frissítései <!-- 3902931 -->
Az iOS app Management-kérések vállalatának neve lecseréli az aktuális "i.manage.microsoft.com" szöveget. A felhasználók például a "i.manage.microsoft.com" helyett a cég nevét fogják látni, ha a felhasználók iOS-alkalmazást próbálnak telepíteni a Céges portálról, vagy amikor a felhasználók engedélyezik az alkalmazás felügyeletét. Ezt a rendszer a következő néhány nap során minden ügyfélnek bevezeti.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>FileVault kezelése macOS rendszerhez   <!--  3858502 + 4557986 + 1210104  -->
Az Intune segítségével kezelheti [a MacOS-eszközök FileVault](encrypt-devices.md)-titkosítását. Az eszközök titkosításához az Endpoint Protection-eszköz konfigurációs profilját kell használnia.

A FileVault-támogatás magában foglalja a titkosítatlan eszközök titkosítását, az eszközök személyes helyreállítási kulcsának letétjét, a személyes titkosítási kulcsok automatikus vagy manuális elforgatását, valamint a vállalati eszközök legfontosabb lekérését. A végfelhasználók a Céges portál webhelyet is használhatják a titkosított eszközök személyes helyreállítási kulcsának beszerzéséhez. 

Kibővítettük a titkosítási jelentést is, hogy a BitLocker melletti [FileVault kapcsolatos információk](encryption-monitor.md) is szerepeljenek, így egyetlen helyen tekintheti meg az összes eszköz titkosítási részleteit. 

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>A Windows Autopilot alaphelyzetbe állítása eltávolítja az eszköz elsődleges felhasználóját <!-- 4156123 -->
Ha az Autopilot alaphelyzetbe állítását egy eszközön használja, az eszköz elsődleges felhasználója el lesz távolítva. A következő felhasználó, aki az Alaphelyzetbe állítás után bejelentkezik, elsődleges felhasználóként lesz beállítva. A szolgáltatás a következő néhány nap során minden ügyfelünk számára elérhetővé válik.

## <a name="week-of-july-8-2019"></a>2019. július 8. hét

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Új Office-, Windows-és OneDrive-beállítások a Windows 10 felügyeleti sablonokban <!-- 3510695 -->

Létrehozhat olyan felügyeleti sablonokat az Intune-ban, amelyek a helyszíni csoportházirend-kezelést utánozzák (az**Eszközkezelő** > **profilok** > a**profil** > **Windows 10-es és újabb verzióinak** létrehozására használhatók a következőhöz: platform > **felügyeleti sablon** a profil típusaként).

Ez a frissítés több Office-, Windows-és OneDrive-beállítást is tartalmaz, amelyeket hozzáadhat a sablonokhoz. Ezekkel az új beállításokkal mostantól konfigurálhatja a 2500-es, 100%-os beállításokat.

A szolgáltatással kapcsolatos további tudnivalókért tekintse meg a csoportházirend [-beállítások konfigurálása az Intune-ban című témakört a Windows 10-es sablonok használatával](administrative-templates-windows.md).

Érintett kiadások: Windows 10 és újabb

## <a name="week-of-july-1-2019"></a>2019. július 1. hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>HRE és alkalmazás androidos vállalati eszközökön <!-- 3574267 -->
Teljes körűen felügyelt Android Enterprise-eszközök bevezetésével a felhasználók most már regisztrálva lesznek Azure Active Directory (HRE) az új vagy gyári visszaállítási eszköz kezdeti beállítása során. A teljes körűen felügyelt eszközhöz korábban a telepítés befejeződése után a felhasználónak manuálisan kell elindítania a Microsoft Intune alkalmazást a HRE-regisztráció elindításához. Most, amikor a felhasználó a kezdeti beállítás után az eszköz kezdőlapján landol, az eszköz regisztrálása és regisztrálása is megtörténik.

A HRE-frissítések mellett az Intune app Protection-szabályzatok (alkalmazás) mostantól teljes körűen felügyelt Android Enterprise-eszközökön is támogatottak. Ez a funkció az üzembe helyezés során elérhetővé válik. További információ: felügyelt [Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune](apps-add-android-for-work.md)-nal.

## <a name="week-of-june-24-2019"></a>2019. június 24-i hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Annak konfigurálása, hogy melyik böngésző számára engedélyezett a szervezeti adatkapcsolat <!-- 3145939 -->
Az Android és iOS rendszerű eszközökön elérhető Intune App Protection szabályzatok mostantól lehetővé teszik, hogy az Intune Managed Browser vagy a Microsoft Edge alkalmazáson kívül egy adott böngészőre is átvigye a szervezeti webhivatkozásokat.  További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>Minden alkalmazás lap az online/offline Microsoft Store for Business Apps szolgáltatást azonosítja<!--4089647 -->
A **minden alkalmazás** oldalon elérhetők az Microsoft Store for Business (MSFB) alkalmazások online vagy offline alkalmazásként való azonosítására szolgáló címkék is. Minden MSFB-alkalmazás már tartalmaz egy utótagot **online** vagy **offline állapotba**. Az alkalmazás részletei lap a **licenc típusát** is tartalmazza, és **támogatja az eszközök környezetének telepítését** (csak offline licenccel rendelkező alkalmazások) kapcsolatos információk.

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Céges portál alkalmazás a Windows megosztott eszközökön <!--4393553 -->
A felhasználók mostantól hozzáférhetnek a Céges portál alkalmazáshoz a Windows megosztott eszközökön. A végfelhasználók egy **megosztott** címkét fognak látni az eszköz csempén. Ez a Windows Céges portál alkalmazás 10.3.45609.0 és újabb verziójára vonatkozik.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Az összes telepített alkalmazás megtekintése új Céges portál weboldalról <!-- 4224326 -->
A Céges portál webhely új **telepített alkalmazások** lapja felsorolja a felhasználó eszközeire telepített összes felügyelt alkalmazást (mindkettő szükséges és elérhető). A hozzárendelés típusa mellett a felhasználók láthatják az alkalmazás közzétevőjét, a közzététel dátumát és a jelenlegi telepítési állapotot. Ha még nem tette meg a felhasználók számára szükséges vagy elérhető alkalmazásokat, egy üzenet jelenik meg arról, hogy nincs telepítve vállalati alkalmazás. Ha szeretné megtekinteni az új lapot a weben, lépjen a [céges portál](https://portal.manage.microsoft.com) webhelyére, és kattintson a **telepített alkalmazások**elemre.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>Az új nézet lehetővé teszi, hogy az alkalmazások felhasználói lássák az eszközre telepített összes felügyelt alkalmazást. <!-- 2352913 -->  
A Windows Céges portál alkalmazás mostantól felsorolja a felhasználó eszközére telepített összes felügyelt alkalmazást (mindkettő kötelező és elérhető). A felhasználók láthatják a megkísérelt és függőben lévő alkalmazás-telepítéseket, valamint a jelenlegi állapotukat is. Ha még nem tette meg a felhasználók számára a szükséges vagy elérhető alkalmazásokat, megjelenik egy üzenet, amely arról tájékoztatja, hogy nincsenek telepítve a vállalati alkalmazások. Az új nézet megjelenítéséhez nyissa meg a céges portál navigációs ablaktáblát, és válassza az **alkalmazások** > **telepített alkalmazások**elemet.    

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Kernel-bővítmények beállításainak konfigurálása macOS-eszközökön <!-- 2043024 -->
MacOS-eszközökön létrehozhat egy eszköz-konfigurációs profilt (az**eszköz konfigurációs** > **profiljait** > a**profil létrehozása** > a platform **MacOS** lehetőséget választva). Ez a frissítés olyan új beállításokat tartalmaz, amelyek lehetővé teszik a kernel-bővítmények konfigurálását és használatát az eszközökön. Hozzáadhat konkrét bővítményeket, vagy engedélyezheti az összes bővítményt egy adott partnertől vagy fejlesztőtől.

További információ erről a szolgáltatásról: a [kernel-bővítmények áttekintése](kernel-extensions-overview-macos.md) és a [kernel-bővítmény beállításai](kernel-extensions-settings-macos.md).

A következőkre vonatkozik: macOS 10.13.2 és újabb verziók

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>A csak áruházból származó alkalmazások Windows 10-es eszközökön való beállítása további konfigurációs beállításokat tartalmaz <!-- 2697002 -->
Ha Windows-eszközökhöz hoz létre egy eszköz-korlátozási profilt, a **csak az áruházból származó alkalmazásokat** használhatja, így a felhasználók csak a Windows App Store áruházból telepítik az alkalmazásokat (**eszköz-konfigurációs** > **profilok**  >  **Profil létrehozása** Windows 10 **és újabb verziók** a platform > **eszköz korlátozásai** a profil típusa).  >  Ebben a frissítésben ez a beállítás ki van bővítve a további beállítások támogatásához. 

Az új beállítás megjelenítéséhez nyissa meg a [Windows 10 (és újabb) eszközbeállítások beállításait a szolgáltatások engedélyezéséhez vagy korlátozásához](device-restrictions-windows-10.md#app-store).

Érintett kiadások: Windows 10 és újabb

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Több Zebra Mobility Extensions-eszköz profiljának üzembe helyezése egy eszközön, azonos felhasználói csoporton vagy azonos eszközök csoporton <!-- 4089955 -->
Az Intune-ban az eszköz konfigurációs profiljában a zebra Mobility Extensions (MX) segítségével testre szabhatja az Intune-ba nem beépített Zebra-eszközök beállításait. Jelenleg egyetlen eszközre is telepíthet egyetlen profilt. Ebben a frissítésben több profilt is üzembe helyezhet:
- Ugyanazon felhasználói csoport
- Ugyanazok az eszközök csoport
- Egyetlen eszköz

Az MX használata az Intune-ban című témakörben Microsoft Intune bemutatja, hogyan használhatók a zebra- [eszközök a zebra Mobility Extensions bővítménnyel](android-zebra-mx-overview.md) .

Érintett kiadások: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Egyes kioszk-beállítások iOS-eszközökön a "letiltás" értékkel vannak beállítva, az "engedélyezés" kifejezés helyett <!-- 4404075  -->
Ha iOS-eszközökön hoz létre egy eszköz-korlátozási profilt (az eszköz**konfigurációs** > **profiljai** > az**iOS** -es**profil** > létrehozása platform > **eszköz korlátozásai** Profil típusa > **kioszk**), beállíthatja az **automatikus zárolást**, a **csengetés kapcsolóját**, a **képernyő**elforgatását, a **képernyő alvó állapotának**és a **hangerő gombját**. 

Ebben a frissítésben az értékek **blokkolva** vannak (blokkolja a funkciót), és **nincs konfigurálva** (engedélyezi a funkciót). A beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait a funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-ios.md#kiosk-supervised-only). 

A következőre vonatkozik: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>A jelszó-hitelesítéshez használja a Face ID-t iOS-eszközökön <!-- 4490704 -->
IOS-eszközökhöz tartozó eszköz-korlátozási profil létrehozásakor ujjlenyomatot használhat a jelszóhoz. Ebben a frissítésben az ujjlenyomat jelszavának beállításai is lehetővé teszik az arc-felismerést (az**eszköz konfigurációs** > **profiljainak** > **profil** > létrehozása**iOS** platformon > **eszköz** a profil típusának korlátozásai > **jelszó**). Ennek eredményeképpen a következő beállítások változtak:

- Az **ujjlenyomat feloldása** most érintse meg az **azonosító és a Face ID feloldása**lehetőséget.
- Az **ujjlenyomat módosítása (csak felügyelt** eszköz esetén) most érintse meg az **azonosító és a Face ID módosítását (csak felügyelt**eszköz esetén).

A Face ID az iOS 11,0-es és újabb verzióiban érhető el. A beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-ios.md#password).

A következőre vonatkozik: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>A játékok és az App Store-szolgáltatások iOS-eszközökön való korlátozása mostantól a minősítési régiótól függ <!-- 4593948 -->
IOS-eszközökön engedélyezheti vagy korlátozhatja a játékokhoz, az App Store-hoz és a dokumentumok megtekintéséhez kapcsolódó funkciókat (az**eszköz konfigurációs** > **profiljainak** > **profil** > létrehozása**iOS** for platform > A profil típusa > **App Store, doc Viewing, Gaming**). Kiválaszthatja a minősítési régiót is, például a Egyesült Államok. 

Ebben a frissítésben az **alkalmazások** szolgáltatás egy gyermek minősítési régióba kerül, és a minősítési régiótólfügg. A beállítások megjelenítéséhez nyissa meg az [IOS-eszköz beállításait, és engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-ios.md#app-store-doc-viewing-gaming).

A következőre vonatkozik: iOS

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>A Windows Autopilot alaphelyzetbe állítása eltávolítja az eszköz elsődleges felhasználóját <!-- 4156123 -->
Ez a szolgáltatás késleltetve lett, és egy közelgő Sprint-ben jelenik meg.    

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Windows Autopilot-támogatás hibrid Azure AD-csatlakozáshoz <!-- 4809146-->
A meglévő eszközökhöz készült Windows Autopilot mostantól támogatja a hibrid Azure AD-csatlakozást (a meglévő Azure AD-csatlakozás támogatása mellett). A Windows 10 1809-es vagy újabb verziójára vonatkozik. További információ: [a Windows Autopilot a meglévő eszközökhöz](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### <a name="device-management"></a>Eszközkezelés

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Tekintse meg az androidos eszközök biztonsági javítási szintjét <!-- 4461911 -->
Most már megtekintheti az Android-eszközök biztonsági javítási szintjét. Ehhez válassza az **Intune** > -**eszközök** > **minden eszköz** lehetőséget, > Válassza ki az eszközt > **hardver**lehetőséget.
A javítási szint az **operációs rendszer** szakaszban szerepel.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Hatókör-címkék társítása egy biztonsági csoportban lévő összes felügyelt eszközhöz <!-- 3173810 -->
Mostantól hozzárendelheti a hatókörhöz tartozó címkéket egy biztonsági csoporthoz, és a biztonsági csoportban lévő összes eszköz hozzá lesz rendelve a hatókörhöz tartozó címkékhez is. Az ezekben a csoportokban lévő összes eszköz hozzá lesz rendelve a hatókör címkéhez is. Az ezzel a szolgáltatással beállított hatókör-címkék felülírják az aktuális eszköz hatóköre címkék folyamatával beállított hatóköri címkéket. További információ: [a RBAC és a hatókör-címkék használata a terjesztéshez](scope-tags.md).

### <a name="device-security"></a>Eszköz biztonsága

#### <a name="use-keyword-search-with-security-baselines-------"></a>Kulcsszavas keresés használata biztonsági alaptervekkel <!--  -->
A [biztonsági](security-baselines.md#create-the-profile)alapkonfigurációk létrehozásakor vagy szerkesztésekor megadhat kulcsszavakat az új *keresési* sávban a keresési feltételeket tartalmazó elérhető csoportok szűréséhez. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>A biztonsági alapkonfigurációk szolgáltatás mostantól általánosan elérhető  <!-- 3785395 -->
A **biztonsági** alapkonfigurációk szolgáltatás előzetes verzióban érhető el, és mostantól általánosan elérhető (GA).  Ez azt jelenti, hogy a szolgáltatás készen áll az éles környezetben való használatra. Az egyes alapkonfigurációk azonban előzetes verzióban is megmaradhatnak, és a saját ütemezésük alapján kiértékelik és kiadhatják a GA-nak.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>A MDM biztonsági alapkonfiguráció sablonja már általánosan elérhető   <!-- 3794072, 4217151,  3534649 -->
A MDM biztonsági alapkonfiguráció sablonja ki lett helyezve az előzetes verzióra, és már általánosan elérhető (GA). A GA-sablon a 2019-as **Mdm biztonsági**alapkonfigurációként van azonosítva.  Ez egy új sablon, és nem az előzetes verzióról való frissítés.  Új sablonként át kell tekintenie a [benne található beállításokat](security-baseline-settings-windows.md), majd új profilokat kell létrehoznia a sablon üzembe helyezéséhez az eszközön. Más biztonsági alapkonfigurációk is megmaradhatnak az előzetes verzióban. Az elérhető alapkonfigurációk listáját itt tekintheti meg: [elérhető biztonsági](security-baselines.md#available-security-baselines)alapkonfigurációk.  

Az új sablon mellett a *május 2019 sablon Mdm biztonsági* alapterve a következő két beállítást tartalmazza, amelyeket nemrégiben jelentettünk be a fejlesztési cikkben:  
- Zárolás felett: Alkalmazások hang aktiválása zárolt képernyőről  
- DeviceGuard: A virtualizálás-alapú biztonság (VBS) használata az eszközök következő újraindításakor.  

A *május 2019-es Mdm biztonsági* alapkonfiguráció több új beállítás hozzáadását is magában foglalja, mások eltávolítását, valamint egy beállítás alapértelmezett értékének egy változatát. Az előzetes verzióról a GA-re való változások részletes listáját az **új sablon**változásai című részben tekintheti meg.

#### <a name="security-baseline-versioning-----3194322---"></a>Biztonsági alapterv verziószámozása  <!-- 3194322 -->
Az Intune biztonsági alapkonfigurációi támogatják a verziószámozást. Ha ezzel a támogatással az egyes biztonsági alapkonfigurációk új verziói jelennek meg, akkor a meglévő biztonsági alapkonfigurációkat úgy frissítheti, hogy az új alapterv újbóli létrehozása és üzembe helyezése nélkül is felhasználható legyen. Emellett az Intune-konzolon megtekintheti az egyes alapbeállításokkal kapcsolatos információkat, például az alapkonfigurációt használó egyedi profilok számát, a profilok által használt különböző alapkonfigurációkat, valamint az adott biztonság legújabb kiadását. az alapterv volt.  További információ: **biztonsági**alaptervek.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>A bejelentkezési beállításhoz tartozó biztonsági kulcsok használata áthelyezve  <!-- 4501151 -->
A **bejelentkezéshez használt** "Identity Protection" nevű eszköz konfigurációs beállítása már nem található a *Windows Hello for Business konfigurálásának*albeállításaként. Ez most egy legfelső szintű beállítás, amely mindig elérhető, még akkor is, ha nem engedélyezi a vállalati Windows Hello használatát. További információ: [Identity Protection](identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>Új engedélyek a hozzárendelt csoport rendszergazdái számára   <!-- 4504437   -->
Az Intune beépített iskolai rendszergazdai szerepköre mostantól rendelkezik a felügyelt alkalmazások létrehozására, olvasására, frissítésére és törlésére (szifilisz) vonatkozó engedélyekkel. Ez a frissítés azt jelenti, hogy ha Intune for Education-beli csoport-rendszergazdaként van társítva, mostantól létrehozhatja, megtekintheti, frissítheti és törölheti az iOS-MDM Push-tanúsítvány, az iOS MDM-kiszolgálói tokeneket, valamint az iOS VPP-tokeneket az [összes meglévő engedélyével](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)együtt. A fenti műveletek elvégzéséhez nyissa meg a **bérlői beállítások** > **iOS-eszközök felügyeletét**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>Az alkalmazások a Graph API használatával felhasználói hitelesítő adatok nélkül hívhatják meg az olvasási műveleteket <!-- 4655885 -->
Az alkalmazások felhasználói hitelesítő adatok nélkül hívhatják meg az Intune-Graph API olvasási műveleteit az alkalmazás identitásával. További információ az Intune-hoz készült Microsoft Graph API eléréséről: az [Intune használata a Microsoft Graphban](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Hatókör-címkék alkalmazása Microsoft Store vállalati alkalmazásokhoz <!-- 4392555 -->
Mostantól alkalmazhat hatókör-címkéket Microsoft Store vállalati alkalmazásokhoz. A hatókör-címkékkel kapcsolatos további információkért lásd: [a szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez](scope-tags.md).

## <a name="week-of-june-17-2019"></a>2019. június 17-i hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune alkalmazás új funkciói
Új funkciókkal bővült az Androidhoz készült Microsoft Intune alkalmazás (előzetes verzió). A teljes körűen felügyelt Android-eszközök felhasználói mostantól a következőket tehetik:  

* Megtekintheti és kezelheti az Intune Céges portál vagy Microsoft Intune alkalmazással regisztrált eszközöket.    
* Segítségért forduljon a szervezethez.    
* Küldjön visszajelzést a Microsoftnak.    
* Megtekintheti a feltételeket és kikötéseket, ha azokat a szervezete állítja be.    

## <a name="week-of-june-10-2019"></a>2019. június 10-i hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>A GitHubon elérhető Intune SDK-integrációt bemutató új minta alkalmazások <!-- 2653471 -->
A msintuneappsdk GitHub-fiók új, az iOS (Swift), az Android, a Xamarin. iOS, a Xamarin Forms és a Xamarin. Android alkalmazásokhoz készült példákkal bővült. Ezeknek az alkalmazásoknak a célja, hogy kiegészítsék meglévő dokumentációját, és bemutatjuk, hogyan integrálhatja az Intune APP SDK-t a saját Mobile Apps szolgáltatásba. Ha olyan alkalmazás fejlesztője van, amelynek további Intune SDK-útmutatásra van szüksége, tekintse meg a következő csatolt mintákat:
- [Csevegés](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) – natív iOS (Swift) azonnali üzenetküldési alkalmazás, amely a Azure Active Directory Authentication Library (ADAL) protokollt használja a felügyelt hitelesítéshez.
- [TASKER](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) – a ADAL-t a felügyelt hitelesítéshez használó natív androidos Todo-lista alkalmazás.
- [TASKER](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) – Xamarin. Android Todo-lista alkalmazás, amely ADAL használ a felügyelt hitelesítéshez, ez a tárház a Xamarin. Forms alkalmazást is tartalmazza.
- [Xamarin. iOS minta alkalmazás](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – A barebones Xamarin. iOS minta alkalmazás.

## <a name="week-of-may-27-2019"></a>Május 27., 2019. hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Az Android-eszközökön feltehetően ártalmas alkalmazások jelentése <!-- 4223162 -->
Az Intune mostantól további jelentéskészítési információkat biztosít az Android-eszközökön található potenciálisan ártalmas alkalmazásokról. 

## <a name="week-of-may-20-2019"></a>2019. május 20. hét 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="windows-company-portal-app----3316993---"></a>Windowsos Munkahelyi portál alkalmazás <!-- 3316993 -->
A Windows Céges portál alkalmazás mostantól egy új lap címkével ellátott **eszközeit**fogja tartalmazni. Az **eszközök** lap megjeleníti a végfelhasználók összes regisztrált eszközét. Ha a 10.3.4291.0 vagy újabb verziót használja, a felhasználók ezt a változást fogják látni a Céges portálban. További információ a Céges portál konfigurálásáról: [Microsoft Intune céges portál alkalmazás konfigurálása](company-portal-app.md).

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Az Autopilot-eszköz Rendeléskód attribútumának neve a csoport címkére módosult <!-- 4659453 -->

Ahhoz, hogy intuitívabb legyen, a **Rendeléskód** -attribútum neve az Autopilot-eszközökön **csoport címkére**módosult. Ha a CSV-t használja az Autopilot-eszköz adatainak feltöltésére, akkor a Group címkét oszlop fejlécként kell használni, a Rendeléskód nem.  

## <a name="week-of-may-13-2019"></a>Május 13-i hét, 2019 

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Az Intune-szabályzatok frissítik a hitelesítési módszert és Céges portál alkalmazás telepítését  <!-- 1927359  -->
A beállítási Asszisztensen keresztül már regisztrált eszközökön az Apple vállalati eszközök egyik regisztrációs módszerén keresztül az Intune többé nem fogja támogatni a Céges portál, ha az App Store-ból végfelhasználók manuálisan telepítik. Ez a változás csak akkor jelentősége, amikor Ön az Apple beállítási asszisztens regisztráció során hitelesítsék magukat. Ez a változás csak is hatással van a regisztrált iOS-eszközöket:  
* Az Apple configuratorral

* Apple üzleti vezető

* Apple School Manager

* Apple Device Enrollment Program (DEP)

Ha a felhasználók a vállalati portál alkalmazást az App store áruházból telepítik, és próbálja meg, ezek eszközöket regisztrálni, akkor egy hibaüzenetet fog kapni. Ezeket az eszközöket a rendszer csak akkor fogja használni, ha a regisztráció során az Intune automatikusan leküldte a Céges portál. Regisztrációs profilok az Intune-ban az Azure Portalon is frissülnek, így megadhatja, hogy miképpen hitelesítik eszközök, és ha kapnak a vállalati portál alkalmazást. Ha azt szeretné, hogy a DEP-eszközök felhasználói szeretné, hogy a vállalati portálon, szüksége lesz a beállítások megadása egy regisztrációs profilt. 

Emellett az iOS-Céges portálban az **eszköz azonosítása** képernyő is törlődik. Ezért a rendszergazdáknak, akik engedélyezni szeretnék a feltételes hozzáférést, vagy vállalati alkalmazásokat kell telepíteniük, frissíteniük kell a DEP regisztrációs profilt. Ez a követelmény csak akkor érvényes, ha a DEP-regisztráció a beállítási asszisztenssel van hitelesítve. Ebben az esetben a Céges portált az eszközre kell leküldeni. Ehhez válassza az **Intune** > -**eszközök** > beléptetése**Apple-regisztráció** > beléptetési**program** jogkivonatok lehetőséget > Válassza ki a tokent > **profilokat** > válasszon egy profilt >  **Tulajdonságok** > a **telepítési céges portál** beállítása **Igen**.

Ha a Céges portál a már regisztrált DEP-eszközökön szeretné telepíteni, akkor az Intune-ban > ügyfélalkalmazások elemre kell kattintania, és felügyelt alkalmazásként kell leküldeni az alkalmazás-konfigurációs házirendekkel. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Annak konfigurálása, hogy a végfelhasználók hogyan frissíthetnek egy üzletági (LOB) alkalmazást egy alkalmazás-védelmi házirend használatával <!-- 3568384 -->
Most már beállíthatja, hogy a végfelhasználók hol szerezhetik be az üzletági (LOB) alkalmazások frissített verzióját. A végfelhasználók láthatják ezt a szolgáltatást a **minimális app Version** feltételes indítási párbeszédpanelen, amely arra kéri a végfelhasználókat, hogy frissítsen az üzletági alkalmazás minimális verziójára. Ezeket a frissítés részleteit a LOB-alkalmazás védelmi házirendjének (alkalmazás) részeként kell megadnia. Ez a funkció iOS és Android rendszereken érhető el. IOS rendszeren ez a funkció megköveteli, hogy az alkalmazás integrálva legyen (vagy becsomagolva a burkoló eszköz használatával) az iOS-hez készült Intune SDK-val. 10.0.7 vagy újabb. Androidon a szolgáltatáshoz a legújabb Céges portál szükséges. Annak konfigurálásához, hogy a végfelhasználó hogyan frissítsen egy LOB-alkalmazást, az alkalmazásnak szüksége van egy felügyelt alkalmazás-konfigurációs `com.microsoft.intune.myappstore`szabályzatra, amelyet a kulcsával eljuttatott. Az elküldés érték határozza meg, hogy a végfelhasználó melyik tárolóban tölti le az alkalmazást. Ha az alkalmazás a Céges portálon keresztül lett telepítve, akkor az értéknek `CompanyPortal`kell lennie. Bármely más áruház esetében teljes URL-címet kell megadnia.

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Intune felügyeleti bővítmény PowerShell-parancsfájlok  <!-- 3734186  -->
Konfigurálhatja a PowerShell-parancsfájlokat úgy, hogy az eszközön a felhasználó rendszergazdai jogosultságával fussanak. További információ: PowerShell- [parancsfájlok használata a Windows 10-es eszközökön az Intune-ban](intune-management-extension.md) és a [win32 app managementben](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Androidos vállalati alkalmazások kezelése <!-- 4459905 -->
Annak érdekében, hogy a rendszergazdák könnyebben konfigurálják és használják az Android Enterprise managementet, az Intune automatikusan négy általános androidos vállalati alkalmazást ad hozzá az Intune felügyeleti konzolhoz. A négy androidos vállalati alkalmazás a következő alkalmazások:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – az Android Enterprise teljes körűen felügyelt forgatókönyvekhez használható.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – segít bejelentkezni a fiókjába, ha kétfaktoros ellenőrzést használ.
- **[Intune céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – az alkalmazás-és az Android Enterprise Work-profil forgatókönyvek esetében használatos.
- [Felügyelt kezdőképernyő](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – az Android Enterprise dedikált/kioszk forgatókönyvek esetében használható.

Korábban a rendszergazdáknak manuálisan kell megkeresniük és jóváhagynia ezeket az alkalmazásokat a [felügyelt Google Play áruházban](https://play.google.com/store/apps) a telepítés részeként. Ez a módosítás eltávolítja ezeket a korábban kézi lépéseket, így egyszerűbbé és gyorsabbá teszi az ügyfelek számára az Android Enterprise Management használatát.

A rendszergazdák láthatják, hogy ezek a négy alkalmazás automatikusan hozzá lesz adva az Intune-alkalmazások listájához, amikor először csatlakoznak az Intune-bérlőhöz a felügyelt Google Play szolgáltatáshoz. További információ: [az Intune-fiók összekötése a felügyelt Google Play-fiókkal](connect-intune-android-enterprise.md). Azok a bérlők, akik már csatlakoztak a bérlőhöz, vagy akik már használják az Android Enterprise-t, nincs szükség a rendszergazdákra. A következő négy alkalmazás automatikusan megjelenik a május 2019 szolgáltatás bevezetésének befejezését követő 7 napon belül.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>A PFX tanúsítvány-összekötő frissítése a Microsoft Intune  <!-- 1533038 -->
Kiadott egy frissítést a [pfx tanúsítvány-összekötőhöz Microsoft Intune számára](certficates-pfx-configure.md#whats-new-for-connectors) , amely egy olyan hibával foglalkozik, amelyben a meglévő pfx-tanúsítványok továbbra is újrafeldolgozásra kerülnek, ami miatt az összekötő leállítja az új kérések feldolgozását.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Intune-beli biztonsági feladatok a Defender ATP-ben (nyilvános előzetes verzió)     <!-- 3208597 -->
A nyilvános előzetes verzióban az Intune használatával kezelheti a [Microsoft Defender komplex veszélyforrások elleni védelem (ATP) biztonsági](atp-manage-vulnerabilities.md)feladatait. Ez az ATP-integráció és a kockázati alapú megközelítés a végponti biztonsági rések és helytelen konfigurációk felderítéséhez, rangsorolásához és javításához, valamint a felderítés és a hibák enyhítése közötti idő csökkentéséhez.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>TPM-chipkészlet keresése Windows 10-es eszköz megfelelőségi szabályzatában <!-- 3617671   idstaged-->
Számos Windows 10 és újabb rendszerű eszköz rendelkezik platformmegbízhatósági modul (TPM) chipsettel. Ez a frissítés egy új megfelelőségi beállítást tartalmaz, amely ellenőrzi a TPM-lapka verzióját az eszközön. 

A [Windows 10-es és újabb megfelelőségi szabályzatok beállításai](compliance-policy-create-windows.md#device-security) ezt a beállítást ismertetik.

Érintett kiadások: Windows 10 és újabb

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Annak megakadályozása, hogy a végfelhasználók módosíthassák a személyes hozzáférési pontokat, és tiltsa le a Siri Server naplózását iOS-eszközökön <!-- 4097904   -->  
Eszköz-korlátozási profilt hoz létre az iOS-eszközön (az eszköz**konfigurációs** > **profiljai** > az**iOS** -es**profil** > létrehozása a platformhoz > **eszköz korlátozásai** a profilhoz típus). Ez a frissítés olyan új beállításokat is tartalmaz, amelyeket konfigurálhat:

- **Beépített alkalmazások**: Kiszolgálóoldali naplózás a Siri-parancsokhoz
- **Vezeték nélküli**: Személyes hozzáférési pont felhasználói módosítása (csak felügyelt eszköz esetén)

Ezeknek a beállításoknak a megtekintéséhez nyissa meg az iOS és a [vezeték nélküli beállítások](device-restrictions-ios.md#wireless)iOS-hez című [beépített alkalmazás beállításait](device-restrictions-ios.md#built-in-apps) .

A következőkre vonatkozik: iOS 12,2 és újabb

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Új osztályterem alkalmazás-eszköz korlátozási beállításai macOS-eszközökhöz <!-- 4097905   --> 
A MacOS-eszközökhöz létrehozhat eszköz-konfigurációs profilokat (az eszköz**konfigurációs** > **profiljaiban** > **létrehozhat profilt** > **MacOS** platform > eszközre vonatkozó **korlátozásokat** a következőhöz: Profil típusa). Ez a frissítés magában foglalja az új osztályterem alkalmazás beállításait, a képernyőképek blokkolásának lehetőségét, valamint az iCloud Photo Library letiltásának lehetőségét.

Ha szeretné megtekinteni az aktuális beállításokat, lépjen a [MacOS eszközbeállítások lehetőségre, hogy engedélyezze vagy korlátozza a szolgáltatásokat az Intune használatával](device-restrictions-macos.md).

A következőkre vonatkozik: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Az App Store-beállítások eléréséhez használt iOS-jelszó átnevezve<!-- 4557891  -->
Az **App Store-hoz való hozzáféréshez használt jelszót** a rendszer átnevezi az **iTunes Store-jelszó megkövetelésére az összes vásárláshoz (az** **eszköz konfigurációs** > **profiljainak** > **profil** > létrehozása**iOS** a platform > **eszközre vonatkozó korlátozások** a profil típusa > **App Store, doc Viewing és Gaming**).

Az elérhető beállítások megjelenítéséhez nyissa meg az [App Store, a doc Viewing, a Gaming iOS beállításait](device-restrictions-ios.md#app-store-doc-viewing-gaming).

A következőre vonatkozik: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender komplex veszélyforrások elleni védelem alapterve (előzetes verzió)  <!--  3754134 -->
Bővítettük a [Microsoft Defender komplex veszélyforrások elleni védelemhez](security-baseline-settings-defender-atp.md) tartozó biztonsági alapkonfiguráció előzetes verzióját. Ez az alapterv akkor érhető el, ha a környezet megfelel a [Microsoft Defender komplex veszélyforrások elleni védelem](advanced-threat-protection.md#prerequisites)használatának előfeltételeinek.

### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>A Windows-regisztráció állapota lap (ESP) már általánosan elérhető <!-- 3605348 -->
A regisztráció állapota lap már nem előzetes verzió. További információ: [regisztráció állapotának beállítása lap](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Intune felhasználói felület frissítése – Autopilot beléptetési profil létrehozása  <!-- 4593669 -->
Az Autopilot-beléptetési profil létrehozásához szükséges felhasználói felület frissítve lett az Azure felhasználói felületi stílusokkal való összehangolás érdekében. További információt az Autopilot- [beléptetési profil létrehozása](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile)című témakörben talál. A továbbítást követően további Intune-forgatókönyvek is frissülnek az új felhasználói felületi stílusba.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Az Autopilot alaphelyzetbe állításának engedélyezése az összes Windows-eszközön <!-- 4225665 -->
Az Autopilot alaphelyzetbe állítása mostantól minden Windows-eszközön működik, még azok is, amelyek nincsenek konfigurálva a regisztrációs állapot lap használatára. Ha a regisztráció állapotát jelző lap nem lett konfigurálva az eszközre a kezdeti eszközök beléptetése során, az eszköz a bejelentkezés után egyenesen az asztalra kerül. Akár nyolc órát is igénybe vehet, és az Intune-ban megfelelőnek tűnik. További információ: [eszközök alaphelyzetbe állítása a távoli Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)alaphelyzetbe állításával.

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Az összes eszköz keresésekor nem szükséges pontos IMEI-formátum <!--30407680 -->
A **minden eszköz**keresésekor nem szükséges szóközöket bevenni az IMEI-számba.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Az eszközök az Apple Portalon való törlése az Intune-portálon jelenik meg <!--2489996 -->
Ha egy eszközt törölnek az Apple Készülékregisztrációs program vagy az Apple Business Manager portálról, az eszköz automatikusan törlődik az Intune-ból a következő szinkronizálás során.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>A regisztráció állapota lap most nyomon követi a Win32-alkalmazásokat <!-- 2714451 -->
Ez csak a Windows 10 1903-es vagy újabb verzióját futtató eszközökre vonatkozik. További információ: [regisztráció állapotának beállítása lap](windows-enrollment-status.md).

### <a name="device-management"></a>Eszközkezelés

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Eszközök tömeges visszaállítása és törlése a Graph API használatával <!-- 3295288 -->
Most visszaállíthatja és törölheti a több mint 100 eszközt a Graph API használatával.


### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>A titkosítási jelentés kívül esik a nyilvános előzetes verzióban   <!-- 4587546      -->
A [BitLocker és az eszközök titkosítására vonatkozó jelentés](encryption-monitor.md) már általánosan elérhető, és már nem része a nyilvános előzetes verziónak. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Az Outlook-aláírás és a biometrikus beállítások iOS és Android rendszerű eszközökhöz <!-- 4050557 -->
Mostantól megadhatja, hogy az alapértelmezett aláírás engedélyezve van-e az Outlookban iOS-és Android-eszközökön. Emellett dönthet úgy is, hogy lehetővé teszi a felhasználók számára, hogy megváltoztassák a biometrikus beállításokat az Outlookban az iOS-ben.

## <a name="week-of-may-6-2019"></a>Május 6-i hét, 2019 

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Hálózati Access Control (NAC) támogatása az iOS-eszközökre vonatkozó F5-hozzáféréshez <!-- 4500808 -->

F5 kiadott egy frissítést a BIG-IP 13-hez, amely lehetővé teszi, hogy a nagyvállalati funkciók F5-ös verzióhoz hozzáférjenek az Intune-ban A szolgáltatás használata:

- A BIG-IP frissítése a 13.1.1.5 frissítéséhez. A BIG-IP 14 nem támogatott.
- A BIG-IP integrálása az Intune-nal a NAC-hoz. Az [áttekintés lépései: Az APM konfigurálása eszköz-testtartási ellenőrzésekhez Endpoint Management](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)rendszerekkel.
- Jelölje be a **hálózati Access Control (NAC) engedélyezése** beállítást a VPN-profilban az Intune-ban.

Az elérhető beállítások megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS-eszközökön](vpn-settings-ios.md)című témakört.

A következőre vonatkozik: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>A PFX tanúsítvány-összekötő frissítése a Microsoft Intune <!-- doc-vso 1521237  -->  
Kiadott egy frissítést a [pfx tanúsítvány-összekötőhöz a Microsoft Intune számára](certficates-pfx-configure.md#whats-new-for-connectors) , amely 5 perctől 30 másodpercre lecsökken a lekérdezési időköz.

## <a name="week-of-april-22-2019"></a>2019. április 22-i hét

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>A megfelelőség-kezelő használata a Microsoft Intune értékelésének létrehozásához<!-- 4404750 -->

[Megfelelőség-kezelő](https://servicetrust.microsoft.com/ComplianceManager) (egy másik Microsoft-webhely megnyitása) munkafolyamat-alapú kockázatfelmérési eszköz a Microsoft szolgáltatás megbízhatósági portálján. Lehetővé teszi a szervezet Microsoft-szolgáltatásokkal kapcsolatos szabályozási megfelelőségi tevékenységeinek nyomon követését, hozzárendelését és ellenőrzését. Saját megfelelőségi értékelést hozhat létre az Office 365, az Azure, a Dynamics, a Professional Services és az Intune használatával. Az Intune-ban két értékelés érhető el: FFIEC és GDPR.

A megfelelőség-kezelő a Microsoft által felügyelt vezérlők és a szervezet által felügyelt vezérlőelemek lebontásával segít összpontosítani az erőfeszítéseket. Elvégezheti az értékeléseket, majd exportálhatja és kinyomtathatja az értékeléseket.

[Szövetségi pénzügyi intézmények felülvizsgálati Tanácsa (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (egy másik Microsoft-webhely megnyitása) a megfelelőség a FFIEC által kiadott online banki szabványok halmaza. Ez az Intune-t használó pénzügyi intézmények által kért Értékelés. Azt értelmezi, hogy az Intune hogyan segít a nyilvános Felhőbeli munkaterhelésekkel kapcsolatos FFIEC-kiberbiztonsági-irányelvek teljesítésében. Az Intune FFIEC-felmérése a második FFIEC értékelés a megfelelőség-kezelőben.

A következő példában a FFIEC-vezérlők részletezése látható. A Microsoft 64-es vezérlőket tartalmaz. A fennmaradó 12 vezérlőért felelős.

![Tekintse meg a FFIEC Intune-értékelését, beleértve az ügyfél-és a Microsoft-műveleteket is](./media/intune-ffiec-assessment-status.png)

[Általános adatvédelmi rendelet (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (egy másik Microsoft-webhely megnyitása) az Európai Unió (EU) törvénye, amely segít a magánszemélyek és az adataik védelmében. Az adatvédelmi szabályozásoknak való megfelelés érdekében a GDPR a leginkább kért Értékelés. 

A következő példában a GDPR-vezérlők részletezése látható. A Microsoft 49-es vezérlőket tartalmaz. A fennmaradó 66-ellenőrzésért felelős.

![Tekintse meg a GDPR Intune-értékelését, beleértve az ügyfél-és a Microsoft-műveleteket is](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>2019. április 15-i hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>OpenSSL titkosítás androidos alkalmazás-védelmi házirendekhez <!-- 3747362 -->
Az Android-eszközökön az Intune app Protection-szabályzatok (alkalmazás) mostantól a FIPS 140-2 szabványnak megfelelő OpenSSL titkosítási függvénytárat használ. További információ: az [Android-alkalmazások védelmére vonatkozó házirend-beállítások](app-protection-policy-settings-android.md) [titkosítási](app-protection-policy-settings-android.md#encryption) szakasza Microsoft Intune.

#### <a name="enable-win32-app-dependencies----2617348----"></a>Win32-alkalmazások függőségeinek engedélyezése <!-- 2617348  -->
Rendszergazdaként szükség lehet arra, hogy a Win32-alkalmazás telepítése előtt más alkalmazások is a függőségként legyenek telepítve. Pontosabban, az eszköznek a Win32-alkalmazás telepítése előtt telepítenie kell a függő alkalmazást (ka) t. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás** elemet az **alkalmazás hozzáadása** panel megjelenítéséhez. Az **alkalmazás típusaként**válassza a **Windows-alkalmazás (Win32)** lehetőséget. Az alkalmazás hozzáadása után a **függőségek** lehetőség kiválasztásával hozzáadhatja azokat a függő alkalmazásokat, amelyeket telepíteni kell a Win32-alkalmazás telepítése előtt. További információ: az [önálló Intune-win32 app Management](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Az alkalmazások verziójának telepítési információi a Microsoft Store for Business alkalmazásokhoz <!-- 3537391   -->
Az alkalmazás-telepítési jelentések a Microsoft Store for Business alkalmazások alkalmazás-verziójának információit tartalmazzák. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások**lehetőséget. Válasszon ki egy **Microsoft Store for Business alkalmazást** , majd válassza az **eszköz telepítésének állapota** lehetőséget a **figyelés** szakaszban.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>A Win32-alkalmazások követelmény-szabályainak kiegészítése <!-- 3676883   -->
A követelmények szabályai a PowerShell-parancsfájlok, a beállításjegyzék-értékek és a fájlrendszer-információk alapján hozhatók létre. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**lehetőséget. Ezután válassza a **Windows-alkalmazás (Win32)** lehetőséget az alkalmazás **hozzáadása** panel **alkalmazás típusa** területén.  Válassza a **követelmények** > **Hozzáadás** lehetőséget a további követelmények szabályainak konfigurálásához. Ezután válassza a **Fájltípus**, a **beállításjegyzék**vagy a **parancsfájl** lehetőséget a **követelmény típusaként**. További információ: [win32 app Management](apps-win32-app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>A Win32-alkalmazások konfigurálása az Intune-ban regisztrált Azure AD-hez csatlakoztatott eszközökre <!-- 3695227  -->
Hozzárendelheti a Win32-alkalmazásokat az Intune-ban regisztrált Azure AD-hez csatlakoztatott eszközökhöz. További információ az Intune-beli Win32-alkalmazásokról: [win32 app Management](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---794259----"></a>Az eszköz áttekintése az elsődleges felhasználót mutatja <!--794259  -->
Az eszköz áttekintő oldala az elsődleges felhasználót, más néven a felhasználó-eszköz kapcsolat felhasználóját (UDA) fogja megjeleníteni. Az eszköz elsődleges felhasználójának megtekintéséhez válassza az **Intune** > -**eszközök** > **minden eszköz** lehetőséget > válasszon ki egy eszközt. Az elsődleges felhasználó megjelenik az **Áttekintés** oldal tetején.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>További felügyelt Google Play-alkalmazások jelentéskészítése androidos vállalati munkahelyi Profilos eszközökhöz <!-- 4105925  -->
Az Android Enterprise Work profiling-eszközökre telepített felügyelt Google Play-alkalmazások esetében megtekintheti az eszközre telepített alkalmazás adott verziószámát. Ez csak a szükséges alkalmazásokra vonatkozik.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Harmadik féltől származó iOS-billentyűzetek <!-- 4111843   -->
Az iOS platformon a **harmadik féltől származó billentyűzetek** beállításához az Intune app Protection-szabályzat (alkalmazás) támogatása már nem támogatott. Ezt a beállítást nem fogja tudni konfigurálni az Intune felügyeleti konzolján, és nem lesz kikényszerítve az ügyfélen az Intune app SDK-ban.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>A bejelentkezési beállítások és a vezérlés újraindítási beállításainak megadása macOS-eszközökön <!-- 1210083  -->
MacOS-eszközökön létrehozhat egy eszköz konfigurációs profilt (eszköz-**konfigurációs** > **profilok** > **profil létrehozása** > válassza a **MacOS** for platform > **eszköz funkciók** a profilhoz lehetőséget. típus). Ez a frissítés új bejelentkezési ablak-beállításokat tartalmaz, például egyéni szalagcímet jelenít meg, kiválaszthatja a felhasználók bejelentkezésének módját, az energiaellátási beállítások megjelenítését és elrejtését.

A beállítások megtekintéséhez válassza a MacOS- [eszköz funkció beállításait](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>WiFi konfigurálása Android Enterprise rendszerű eszközökön, a több alkalmazásból álló kioszk módban futó eszköz tulajdonos dedikált eszközei <!--3041940  -->
Engedélyezheti az Android Enterprise, az eszköz tulajdonosának beállításait, ha dedikált eszközként fut többalkalmazásos kioszk módban. Ebben a frissítésben engedélyezheti a felhasználók számára a WiFi-hálózatok konfigurálását és kapcsolódását (**Intune** > -**eszköz konfigurációs** > **profiljai** > Android-**profil létrehozása** >  **Enterprise** for platform > **csak eszköz tulajdonosa, eszközök korlátozásai** a profil típusa > **dedikált eszközök** > **kioszk mód**: **Multi-app** > **WiFi-konfiguráció**). 

Az összes konfigurálható beállítás megjelenítéséhez nyissa meg az [Android Enterprise-eszköz beállításait a funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md).

Érintett kiadások: Több alkalmazásból álló kioszk módban futó androidos vállalati dedikált eszközök


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>A Bluetooth és a párosítás konfigurálása az Android Enterprise-on, az eszköz tulajdonosának dedikált eszközei többalkalmazásos kioszk módban <!-- 3041941  -->
Engedélyezheti az Android Enterprise, az eszköz tulajdonosának beállításait, ha dedikált eszközként fut többalkalmazásos kioszk módban. Ebben a frissítésben engedélyezheti a végfelhasználók számára a Bluetooth használatát és a párosítást Bluetooth-kapcsolaton keresztül (**Intune** > -**eszköz konfigurációs** > **profiljai** > **profil létrehozása**  >   **Android Enterprise** for platform > **eszköz tulajdonosa,** eszközök korlátozásai a profil típusa > **dedikált eszközök** > **kioszk mód**: **Multi-app** > **Bluetooth-konfiguráció**). 

Az összes konfigurálható beállítás megjelenítéséhez nyissa meg az [Android Enterprise-eszköz beállításait a funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md).

Érintett kiadások: Több alkalmazásból álló kioszk módban futó androidos vállalati dedikált eszközök

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>OEMConfig-eszközök konfigurációs profiljainak létrehozása és használata az Intune-ban <!-- 3305883  -->
Ebben a frissítésben az Intune támogatja az androidos vállalati eszközök konfigurálását a OEMConfig. Konkrétan létrehozhat egy eszköz-konfigurációs profilt, és beállításokat alkalmazhat az androidos vállalati eszközökre a OEMConfig használatával (az**eszköz konfigurációs** > **profiljai** > a**profil létrehozása**  >   **Android Enterprise** platformhoz).

A számítógépgyártók támogatása jelenleg OEM-alapú. Ha a használni kívánt OEMConfig-alkalmazás nem érhető el a OEMConfig-alkalmazások listájában `IntuneOEMConfig@microsoft.com`, lépjen kapcsolatba.

A szolgáltatással kapcsolatos további információkért tekintse meg az androidos nagyvállalati [eszközök használata és kezelése a Microsoft Intune OEMConfig](android-oem-configuration-overview.md)című témakört.

Érintett kiadások: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Értesítések Windows Update  <!-- 3316758, 3316782  -->
Két *felhasználói élményre vonatkozó beállítást* adtunk hozzá az Intune-konzolon belül felügyelhető Windows Update Ring-konfigurációkhoz. Mostantól a következőket teheti:
- A [Windows-frissítések keresésének](windows-update-settings.md)tiltása vagy engedélyezése a felhasználóknak.
- Kezelheti a felhasználók által megjelenített [Windows Update értesítési szintet](windows-update-settings.md) .

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Az Android Enterprise, az eszköz tulajdonosa új eszköz korlátozási beállításai <!-- 3574254  -->
Az Android Enterprise rendszerű eszközökön létrehozhat egy eszköz-korlátozási profilt, amely lehetővé teszi a szolgáltatások engedélyezését vagy korlátozását, a jelszó-szabályok beállítását és egyebeket (az**eszköz konfigurációs** > **profiljainak** > **profil létrehozása** > válassza  **Az Android Enterprise** for platform > **eszköz tulajdonosa csak > eszköz korlátozásai** a profil típusa esetén). 

Ez a frissítés új jelszavas beállításokat tartalmaz, lehetővé teszi az alkalmazások teljes hozzáférését Google Play Áruház a teljes körűen felügyelt eszközökhöz és egyebekhez. A beállítások aktuális listájának megtekintéséhez lépjen az [Android Enterprise-eszköz beállításai lehetőségre a funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md). 

Érintett kiadások: Android Enterprise teljes körűen felügyelt eszközök

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>TPM-chipkészlet keresése Windows 10-es eszköz megfelelőségi szabályzatában <!-- 3617671 -->

Ez a szolgáltatás késleltetve van, és a tervek szerint később lesz közzétéve.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Frissített felhasználói felületi változások a Microsoft Edge böngészőhöz Windows 10 és újabb rendszerű eszközökön <!-- 3775833   -->
Az eszköz konfigurációs profiljának létrehozásakor engedélyezheti vagy korlátozhatja a Microsoft Edge-szolgáltatásokat a Windows 10 és újabb rendszerű eszközökön (az**eszköz konfigurációs** > **profiljaiban** > **profilokat**  >   **hozhat létre A platformhoz tartozó Windows 10 és újabb verziók** esetében > **eszközre vonatkozó korlátozásokat** a profil típusa > **Microsoft Edge böngésző**). Ebben a frissítésben a Microsoft Edge-beállítások jobban leíró jellegűek, és könnyebben megérthetők. 

A funkciók megjelenítéséhez nyissa meg a [Microsoft Edge böngésző eszközének korlátozási beállításait](device-restrictions-windows-10.md#microsoft-edge-browser).

Érintett kiadások: Windows 10 és újabb

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Bővített támogatás Android Enterprise teljes körűen felügyelt eszközökhöz (előzetes verzió)  <!--   3903241, 3903244, 3903246   -->
Még egy nyilvános előzetes verzióban is kibővítettük az Android Enterprise teljes körűen felügyelt eszközök támogatását (az[első a 2019 januárjában jelent](whats-new.md#week-of-january-14-2019) meg, amely a következőket tartalmazza: 

- A teljes körűen felügyelt és dedikált eszközökön [megfelelőségi szabályzatokat](compliance-policy-create-android-for-work.md) hozhat létre a jelszó-szabályok és az operációs rendszerre vonatkozó követelmények betartásához (**eszköz megfelelőségi** > **szabályzatok** > **létrehozása házirend**  >  Az **Android Enterprise** for platform > **eszköz tulajdonosa** a profil típusaként). 

  A dedikált eszközökön előfordulhat, hogy az eszköz **nem megfelelőként**jelenik meg. A feltételes hozzáférés nem érhető el dedikált eszközökön. Ügyeljen arra, hogy minden feladatot vagy műveletet végrehajtson, hogy a dedikált eszközök megfeleljenek a hozzárendelt szabályzatoknak.

- [Feltételes hozzáférés](conditional-access.md) – az Androidra érvényes feltételes hozzáférési szabályzatok az Android Enterprise teljes körűen felügyelt eszközökre is érvényesek. A felhasználók mostantól regisztrálhatják teljes mértékben felügyelt eszközét Azure Active Directory a **Microsoft Intune alkalmazással**. Ezután tekintse meg és oldja meg a szervezeti erőforrások elérésére vonatkozó megfelelőségi problémákat.

- Új végfelhasználói alkalmazás (Microsoft Intune alkalmazás) – új végfelhasználói alkalmazás érhető el az Android rendszerű, teljes körűen felügyelt eszközökhöz, amelyeket **Microsoft Intune**. Ez az új alkalmazás könnyű és modern, és hasonlóan működik a Céges portál alkalmazáshoz, de a teljes körűen felügyelt eszközökhöz. További információ: [Microsoft Intune alkalmazás a Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune)áruházban.

Az Android teljes körűen felügyelt eszközeinek beállításához lépjen az **eszközök** > regisztrálása**Android-regisztráció** > **vállalat által birtokolt, teljes körűen felügyelt felhasználói eszközök**elemre. A teljes körűen felügyelt Android-eszközök támogatása előzetes verzióban érhető el, és előfordulhat, hogy egyes Intune-funkciók nem teljesen működőképesek.  

Ha többet szeretne megtudni erről az előzetes verzióról, tekintse meg a blogot, [Microsoft Intune-Preview 2 for Android Enterprise teljes körűen felügyelt eszközeit](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Profil beállítása a képernyők kihagyására a beállítási asszisztens során <!-- 2276470  -->
MacOS-regisztrációs profil létrehozásakor beállíthatja, hogy a következő képernyők bármelyikét kiugorja, amikor a felhasználó áthalad a beállítási Asszisztensen:
- Megjelenését
- Hang megjelenítése
- iCloudStorage ha új profilt hoz létre, vagy szerkeszt egy profilt, a kijelölt kihagyási képernyőknek szinkronizálnia kell az Apple MDM-kiszolgálóval.  A felhasználók manuálisan is szinkronizálhatják az eszközöket, így nincs késés a profil módosításainak felvételekor.
További információ: macOS- [eszközök automatikus regisztrálása a Készülékregisztrációs program vagy az Apple School Managerrel](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Csoportos eszköz elnevezése vállalati iOS-eszközök regisztrálásakor<!--3566569  -->
Ha az Apple vállalati beléptetési módszereit (DEP/ABM/ASM) használja, megadhatja az eszköz nevének formátumát a bejövő iOS-eszközök automatikus neveként. Megadhat egy olyan formátumot, amely tartalmazza az eszköz típusát és a sorozatszámot a sablonban. Ehhez válassza az **Intune** > -**eszközök** > beléptetése**Apple-regisztráció** > beléptetési**program** > jogkivonatok lehetőséget, és**válassza ki a jogkivonat** >létrehozása elemet.profil > -**eszköz elnevezési formátuma** Szerkesztheti a meglévő profilokat, de csak az újonnan szinkronizált eszközök lesznek érvényesek.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Frissített alapértelmezett időtúllépési üzenet a regisztráció állapota lapon <!-- 3959331 -->
Frissítettük az alapértelmezett időtúllépési üzenet felhasználóit, ha a regisztrációs állapot lap (ESP) meghaladja az ESP-profilban megadott időtúllépési értéket. Az új alapértelmezett üzenet az, amit a felhasználók látnak és segítenek megérteni a következő műveleteket az ESP-telepítéssel.  

### <a name="device-management"></a>Eszközkezelés

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Nem megfelelő eszközök kivonása  <!-- 1827291   -->
A szolgáltatás késleltetve lett, és egy későbbi kiadásra van tervezve.


### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Az Intune-adattárház 1.0-s verziójának módosításai visszaállnak a bétaverzióba <!-- 4403765 -->
Ha a 1.0-s verzió először mutatkozott be a 1808-ben, a Beta API néhány jelentős módon eltért. 1903 ezek a változások a Beta API-verzióba kerülnek vissza. Ha olyan fontos jelentésekkel rendelkezik, amelyek a Beta API verzióját használják, javasoljuk, hogy a módosítások elvégzése érdekében váltson át a jelentéseket a 1.0-s verzióra. További információkért lásd: [az Intune-adattárház API változási naplójának módosítása](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>A biztonsági alapterv állapotának figyelése (nyilvános előzetes verzió) <!-- 3082047 --> 
A biztonsági alapkonfigurációk figyeléséhez egy [kategóriánkénti nézetet](security-baselines-monitor.md#per-category-view) adtunk hozzá. (A biztonsági alapkonfigurációk az előzetes verzióban maradnak). A kategóriánkénti nézet az alaptervből származó összes kategóriát jeleníti meg, valamint az adott kategóriába tartozó egyes állapotüzenetek alá tartozó eszközök százalékos arányát. Most már láthatja, hogy hány eszköz nem felel meg az egyes kategóriáknak, helytelenül vannak konfigurálva, vagy nem alkalmazhatók.

### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Az Apple VPP-tokenek hatókör-címkéi <!--2371886  -->
Mostantól hozzáadhat hatókör-címkéket az Apple VPP-tokenekhez. Csak az azonos hatókörű címkével rendelkező felhasználók férhetnek hozzá az Apple VPP-tokenhez az adott címkével. A jogkivonattal vásárolt VPP-alkalmazások és-e-könyvek a hatókörük címkéit öröklik. A hatókör-címkékkel kapcsolatos további információkért lásd: [RBAC és hatóköri címkék használata](scope-tags.md).







## <a name="week-of-april-1-2019"></a>2019. április 1. hét

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Frissített tanúsítvány-összekötők  <!-- ICM 113304612 -->
Az [Intune tanúsítvány-összekötőhöz és a pfx tanúsítvány-összekötőhöz](certficates-pfx-configure.md#whats-new-for-connectors)is kiadott frissítéseket a Microsoft Intunehoz. Az új kiadások számos ismert problémát javítanak.  

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Az iOS rendszerhez készült Céges portál alkalmazás felhasználói élményének frissítése <!-- 2536024 -->
Az iOS-eszközökhöz készült Céges portál alkalmazás kezdőlapja újratervezve. Ezzel a módosítással a Kezdőlap jobban követheti az iOS felhasználói felületének mintáit, és jobb felderíthetővé teheti az alkalmazásokat és az e-könyveket.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Az iOS 12 eszköz felhasználóinak Céges portál regisztrációjának módosításai <!--3448635 -->  
Az iOS-es beléptetési képernyők és lépések Céges portál frissült az Apple iOS 12,2-ben kiadott MDM-regisztráció módosításaival. A frissített munkafolyamat a következőket kéri a felhasználóktól:  

* A Céges portál webhely megnyitásának engedélyezése a Safari számára, és a Céges portál alkalmazásba való visszatérés előtt töltse le a felügyeleti profilt.  
* A beállítások alkalmazás megnyitásával telepítse a felügyeleti profilt az eszközére.
* A regisztráció befejezéséhez térjen vissza a Céges portál alkalmazáshoz.  

A regisztrációs lépések és képernyők frissítésével kapcsolatban lásd: [IOS-eszköz regisztrálása az Intune-ban](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>2019. március 25-i hét

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>A Power BI megfelelőségi alkalmazás támogatása az adattárház paneljén Microsoft Intune <!-- 4260871 -->
Korábban a **letöltés Power bi fájl** hivatkozás az Intune- **adattárház** panelen letöltött egy Intune-adattárház-jelentést (. pbix fájl). Ezt a jelentést a Power BI megfelelőségi alkalmazás váltotta fel. A Power BI megfelelőségi alkalmazás nem igényel speciális betöltést vagy beállítást. Közvetlenül a Power BI online portálon nyílik meg, és a hitelesítő adatai alapján kifejezetten az Intune-bérlő adatait jeleníti meg. Az Intune-ban kattintson az Intune- **adattárház beállítása** hivatkozásra az Intune panel jobb oldalán. Ezután kattintson az **Power bi alkalmazás**beolvasása elemre. További információ: [Kapcsolódás az Adattárházhoz Power bi használatával](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>2019. március 18. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>A Microsoft Visio és a Microsoft Project üzembe helyezése <!-- 3725386  -->
Most már telepítheti a Microsoft Visio Pro for Office 365 és a Microsoft Project online asztali ügyfelet független alkalmazásként Windows 10-es eszközökre Microsoft Intune használatával, ha ezekhez az alkalmazásokhoz saját licence van. Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás** elemet az **alkalmazás hozzáadása** panel megjelenítéséhez. Az **alkalmazás hozzáadása** panelen válassza a **Windows 10** lehetőséget az **alkalmazás típusaként**. Ezután válassza az **alkalmazáscsomag konfigurálása** elemet a telepítendő alkalmazások kiválasztásához. További információ a Windows 10-es eszközök Office 365-alkalmazásairól: [office 365-alkalmazások kiosztása Windows 10-es eszközökhöz Microsoft Intune használatával](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 terméknév változása <!-- 3593653  -->
**A Microsoft Visio Pro for Office 365** mostantól a **Microsoft Visio online 2**. csomagjának lesz a neve.  A Microsoft Visio szolgáltatással kapcsolatos további információkért lásd: [Visio online 2. csomag](https://products.office.com/visio/visio-online-plan-2). További információ a Windows 10-es eszközök Office 365-alkalmazásairól: [office 365-alkalmazások kiosztása Windows 10-es eszközökhöz Microsoft Intune használatával](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Az Intune app Protection-szabályzat (alkalmazás) karakteres korlátjának beállítása <!-- 3291302  -->
Az Intune-rendszergazdák kivételt adhatnak meg az Intune-alkalmazás számára a kivágási **, másolási és beillesztési műveletek korlátozása más alkalmazásokkal** házirend-beállítással.  Rendszergazdaként megadhatja, hogy hány karakterből lehet kivágni vagy másolni egy felügyelt alkalmazást. Ez a beállítás lehetővé teszi a megadott számú karakter megosztását bármely alkalmazásra, a "Kivágás, másolás és beillesztés más alkalmazásokkal" beállítástól függetlenül. Vegye figyelembe, hogy az Androidhoz készült Intune Céges portál alkalmazás verziójának 5.0.4364.0 vagy újabb verziójúnak kell lennie. További információ: [iOS](app-protection-policy-settings-ios.md#data-protection)-adatvédelem, Android- [Adatvédelem](app-protection-policy-settings-android.md#data-protection)és az ügyfélalkalmazás- [védelmi naplók áttekintése](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Office Deployment Tool (ODT) XML az Office ProPlus telepítéséhez <!-- 3192477   -->
Az Office Pro Plus egy példányának létrehozásakor az Intune felügyeleti konzolján megadhatja az Office Deployment Tool (ODT) XML-t. Ez nagyobb testreszabhatóság lehetővé tétele, ha a meglévő Intune felhasználói felületi lehetőségek nem felelnek meg az igényeinek. További információ: [office 365-alkalmazások kiosztása Windows 10-es eszközökhöz Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) és [konfigurációs beállításokkal az Office-telepítő eszközhöz](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Az alkalmazás ikonjai ekkor automatikusan generált háttérrel jelennek meg <!-- 1429026  -->
A Windows Céges portál alkalmazásban az alkalmazás ikonjai mostantól automatikusan generált háttérrel jelennek meg az ikon domináns színe alapján (ha ez észlelhető). Ha alkalmazható, ez a háttér azt a szürke szegélyt váltja fel, amely korábban már látható az alkalmazás csempén. A felhasználók ezt a változást a Céges portál későbbi verzióiban fogják látni a 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Elérhető alkalmazások telepítése a Céges portál alkalmazással a Windows tömeges beléptetése után <!-- 2751523   -->
Azok a Windows-eszközök, amelyek az Intune-ba regisztrált [Windows csoportos](windows-bulk-enroll.md) beléptetéssel (kiépítési csomagokkal) a céges portál alkalmazás használatával telepíthetik az elérhető alkalmazásokat. A Céges portál alkalmazással kapcsolatos további információkért lásd: [a Windows 10 céges portál manuális hozzáadása](store-apps-company-portal-app.md) és [az Microsoft Intune céges portál alkalmazás konfigurálása](company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>A Microsoft Teams alkalmazás az Office App Suite részeként is kiválasztható <!-- 3828932  -->
A Microsoft Teams alkalmazás az Office Pro Plus App Suite telepítésének részeként is beépíthető vagy kizárható. Ez a funkció az Office Pro Plus Build Number 16.0.11328.20116 + csomaggal működik. A felhasználónak ki kell jelentkeznie, majd be kell jelentkeznie az eszközre a telepítés befejezéséhez. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**lehetőséget. Válassza ki az **Office 365 Suite** -alkalmazások egyikét, majd válassza az **App Suite konfigurálása**lehetőséget.

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Alkalmazás automatikus elindítása, ha a Windows 10 és újabb rendszerű eszközökön több alkalmazást futtat kioszk módban <!-- 2351390 -->

Windows 10 és újabb rendszerű eszközökön az eszközt teljes képernyős módban futtathatja, és számos alkalmazást futtathat. Ebben a frissítésben van egy automatikus **indítási** beállítás (az**eszköz konfigurációs** > **profiljai** > a**Windows 10-es és újabb verziók** **létrehozása** > platform > **kioszk** for Profil típusa > **többalkalmazásos kioszk**). Ezzel a beállítással automatikusan elindíthat egy alkalmazást, amikor a felhasználó bejelentkezik az eszközre.

A teljes képernyős beállítások listájának és leírásának megtekintéséhez lásd: a [Windows 10 és újabb rendszerű eszközök beállításai, amelyek kioszkként futnak az Intune-ban](kiosk-settings-windows.md).

Érintett kiadások: Windows 10 és újabb

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Az operatív naplók a nem megfelelő eszközök részleteit is mutatják <!-- 4063755  -->
Amikor az Intune az Azure monitor szolgáltatásban naplózza a funkciókat, az operatív naplókat is átirányíthatja. Ebben a frissítésben az operatív naplók a nem megfelelő eszközökről is biztosítanak információkat. 

További információ erről a szolgáltatásról: [naplófájlok küldése tárolóba, Event hubokba vagy log analyticsbe az Intune-ban](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Naplók átirányítása Azure Monitorre több Intune-beli számítási feladatban <!-- 3804627 -->
Az Intune-ban átirányíthatja a naplózási és működési naplókat az események hubokba, a Storage-ba és a log analyticsbe Azure monitor (**Intune** > **figyelési** > **diagnosztikai beállítások**). Ebben a frissítésben ezeket a naplókat több Intune-beli számítási feladatban is átirányíthatja, beleértve a megfelelőséget, a konfigurációkat, az ügyfélalkalmazások és egyebeket. 

Ha többet szeretne megtudni a Azure Monitor útválasztási naplóiról, tekintse meg a [naplófájlok küldése tárolóba, az Event hubokba vagy a log analyticsbe](review-logs-using-azure-monitor.md)című témakört.

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Mobilitási bővítmények létrehozása és használata az androidos Zebra-eszközökön az Intune-ban <!-- 3305880   -->
Ebben a frissítésben az Intune támogatja az androidos Zebra-eszközök konfigurálását. Pontosabban létrehozhat egy eszköz-konfigurációs profilt, és beállításokat alkalmazhat az Android Zebra-eszközökre a StageNow által generált Mobility Extensions (MX) profilok használatával (az**eszköz konfigurációs** > **profiljai**  > Profil > létrehozása**Android** for platform > **MX-profil (csak Zebra)** a profil típusa esetén).

A szolgáltatással kapcsolatos további információkért lásd: a [Zebra-eszközök használata és kezelése a mobilitási bővítményekkel az Intune-ban](android-zebra-mx-overview.md).

Érintett kiadások: Android

### <a name="device-management"></a>Eszközkezelés

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Titkosítási jelentés Windows 10-es eszközökhöz (nyilvános előzetes verzió)<!-- 2351538 -->  
Az új [titkosítási jelentés (előzetes verzió)](encryption-monitor.md) használatával megtekintheti a Windows 10-es eszközök titkosítási állapotának részleteit. Az elérhető részletek közé tartozik az eszközök TPM-verziója, a titkosítás készültsége és az állapot, a hibajelentés és egyebek.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Hozzáférés a BitLocker helyreállítási kulcsaihoz az Intune-portálon (nyilvános előzetes verzió) <!-- 2351547   -->  
Mostantól az Intune-nal [](encryption-monitor.md) is megtekintheti a BitLocker-kulcs azonosítóját és a BitLocker helyreállítási kulcsait a Azure Active Directoryból.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-támogatás az Intune-forgatókönyvekhez iOS-és Android-eszközökön <!-- 3411007 -->
A Microsoft Edge minden olyan felügyeleti forgatókönyvet támogat, mint a Intune Managed Browser a végfelhasználói élmény fokozása mellett. Az Intune-szabályzatok által engedélyezett Microsoft Edge Enterprise-funkciók közé tartozik a kettős identitás, az alkalmazás-védelmi házirendek integrációja, az Azure alkalmazásproxy-integráció, valamint a felügyelt kedvencek és a Kezdőlap parancsikonjai. További információ: [Microsoft Edge-támogatás](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Az Exchange Online/Intune-összekötő elavult csak EAS-eszközök támogatása <!--3105122  -->
Az Intune-konzol már nem támogatja az Exchange Online-hoz az Intune-összekötővel csatlakoztatott EAS-eszközök megtekintését és felügyeletét. Ehelyett a következő lehetőségek közül választhat:
- Eszközök regisztrálása a mobileszköz-felügyeletben (MDM)
- Intune App Protection szabályzatok használata az eszközök kezeléséhez
- Exchange-vezérlők használata az [ügyfelek és a mobil Exchange Online-](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) ban vázolt módon

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>A [név] használatával keresse meg a pontos eszköz minden eszköz lapját. <!--4254930 -->
Most már megkeresheti az eszköznév pontos nevét. Nyissa meg az **Intune** > -**eszközök** > **minden eszköz** {} > a keresőmezőbe, és az eszköz nevét adja meg, hogy pontos egyezést keressen. Például: **{Device12345}** .

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>További összekötők támogatása a bérlő állapota lapon <!-- 3617202  -->
A [bérlő állapota lap](tenant-status.md) ekkor megjeleníti a további összekötők állapotinformációkat, beleértve a *Windows Defender komplex veszélyforrások elleni védelmet* (ATP) és más Mobile Threat Defense-összekötőket.

### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Az Intune csak olvasási hozzáférésének engedélyezése néhány Azure Active Directory szerepkörhöz <!-- 3637917  -->
Az Intune írásvédett hozzáférése a következő Azure AD-szerepkörökhöz lett megadva. Az Azure AD-szerepkörökhöz megadott engedélyek felülírják az Intune szerepköralapú hozzáférés-vezérléssel (RBAC) biztosított engedélyeket.

Csak olvasási hozzáférés az Intune-beli naplózási információkhoz:

- Megfelelőségi rendszergazda
- Megfelelőségi adatkezelő

Csak olvasási hozzáférés az összes Intune-adattal:

- Biztonsági rendszergazda
- Biztonsági operátor
- Biztonsági olvasó

További információ: [szerepköralapú hozzáférés-vezérlés](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>A hatókör címkéi az iOS-alkalmazások létesítési profiljaihoz <!--2934430   -->
Hozzáadhat egy hatóköri címkét egy iOS-alkalmazás létesítési profiljához, így csak a szerepkörökhöz hozzárendelt felhasználók férhetnek hozzá az iOS-alkalmazások létesítési profiljához. További információ: [RBAC és hatókör-címkék használata](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Alkalmazás-konfigurációs házirendek hatókör-címkéi <!--2371891   -->
Hatókör-címkét adhat hozzá egy alkalmazás-konfigurációs házirendhez, így csak a szerepkörökhöz hozzárendelt felhasználók férhetnek hozzá az alkalmazás konfigurációs házirendjéhez. Az alkalmazás-konfigurációs házirend csak az ugyanahhoz a hatóköri címkéhez hozzárendelt alkalmazásokhoz célozható vagy társítható. További információ: [RBAC és hatókör-címkék használata](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-támogatás az Intune-forgatókönyvekhez iOS-és Android-eszközökön <!-- 3411007 -->
A Microsoft Edge minden olyan felügyeleti forgatókönyvet támogat, mint a Intune Managed Browser a végfelhasználói élmény fokozása mellett. Az Intune-szabályzatok által engedélyezett Microsoft Edge Enterprise-funkciók közé tartozik a kettős identitás, az alkalmazás-védelmi házirendek integrációja, az Azure alkalmazásproxy-integráció, valamint a felügyelt kedvencek és a Kezdőlap parancsikonjai. További információ: [Microsoft Edge-támogatás](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>2019. február 25-i hét

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell-modul <!-- 951068  -->
Az Intune PowerShell-modul, amely a Microsoft Graphon keresztül támogatja az Intune API-t, mostantól elérhető a [Microsoft PowerShell-Galéria](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [A modul használatának részletei](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Példa a modult használó forgatókönyvekre](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Továbbfejlesztett támogatás a kézbesítés optimalizálásához  <!--3183757  -->
Kibővítettük az Intune támogatását a kézbesítés optimalizálásának konfigurálásához. Mostantól az Intune-konzolról is konfigurálhatja a [kézbesítési optimalizálási beállítások](delivery-optimization-settings.md) kibontott listáját, és megcélozhatja azokat az eszközökre.


## <a name="week-of-february-18-2019"></a>2019. február 18. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Az Intune kihasználja a Google Play Protect API-kat Android-eszközökön <!-- 2577355   -->
Egyes IT-rendszergazdák egy BYOD-környezettel szembesülnek, ahol a végfelhasználók felhasználhatják a begyökerező vagy a mobiltelefonról érkező felhasználókat. Ez a viselkedés, miközben néha nem szándékosan van kipróbálva, a rendszer számos olyan Intune-szabályzat megkerülését eredményezi, amely a szervezet végfelhasználói eszközökön tárolt adatainak védelme érdekében be van állítva. Így az Intune a regisztrált és a nem regisztrált eszközök gyökerét és szökik észlelését is lehetővé teszi. Ebben a kiadásban az Intune mostantól kihasználja a Google Play Protect API-kat, hogy hozzáadja a meglévő gyökérszintű észlelési ellenőrzésekhez a nem regisztrált eszközökhöz. Míg a Google nem osztja meg a legfelső szintű észlelési ellenőrzéseket, az API-k elvárják, hogy észlelni tudják az eszközeiket az eszköz testreszabásával kapcsolatban, hogy az operációs rendszer újabb frissítései a régebbi eszközökön legyenek leképezve. Ezek a felhasználók Ezután letilthatja a vállalati adatok elérését, vagy a vállalati fiókjaikat a szabályzattal kompatibilis alkalmazásokból is törölhetik. További érték esetén a rendszergazda mostantól több jelentéskészítési frissítést is tartalmaz a Intune App Protection panelen – a "megjelölt felhasználók" jelentés megmutatja, hogy mely felhasználók észlelhetők a Google Play Protect biztonság API-vizsgálatán keresztül, a "potenciálisan ártalmas alkalmazások" jelentés Megjeleníti, hogy mely alkalmazások észlelhetők a Google ellenőrzési alkalmazások API-vizsgálatán keresztül. Ez a funkció Androidon érhető el.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>A Win32-alkalmazások információi a Hibaelhárítás panelen érhetők el <!-- 2617342   -->
Mostantól az Intune-alkalmazások hibaelhárítási paneljén is gyűjthet egy Win32-alkalmazás telepítésének sikertelen naplófájljait. Az alkalmazások telepítésével kapcsolatos hibaelhárítással kapcsolatos további információkért lásd: az [alkalmazások telepítésével kapcsolatos problémák elhárítása](troubleshoot-app-install.md) és a [Win32-alkalmazások](apps-win32-app-management.md#troubleshoot-win32-app-issues)hibáinak elhárítása.

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Alkalmazások állapotának részletei iOS-alkalmazásokhoz <!-- 3761235   -->
A következőhöz kapcsolódó új alkalmazás-telepítési hibaüzenetek találhatók:
- Nem sikerült a VPP-alkalmazások megosztott iPadre való telepítésekor
- Hiba az App Store letiltásakor
- Nem található a VPP-licenc az alkalmazáshoz
- Nem sikerült telepíteni a rendszeralkalmazásokat a MDM Provider szolgáltatással
- Nem sikerült telepíteni az alkalmazásokat, ha az eszköz elveszett vagy teljes képernyős módban van
- Nem sikerült telepíteni az alkalmazást, ha a felhasználó nincs bejelentkezve az App Store-ba

Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások** > "alkalmazás neve" > **eszköz telepítési állapota**lehetőséget. Az új hibaüzenetek az **állapot részletei** oszlopban lesznek elérhetők.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Új alkalmazás-kategóriák képernyő a Windows 10-es Céges portál alkalmazásban<!-- 3834780  -->
Az alkalmazás- **Kategóriák** nevű új képernyő lett hozzáadva az alkalmazások böngészési és kiválasztási élményének javításához a Windows 10-es céges portál. A felhasználók mostantól a **Kiemelt**, az **oktatási**és a **termelékenység**kategóriák szerint rendezve láthatják az alkalmazásaikat. Ez a módosítás Céges portál 10.3.3451.0 és újabb verziókban jelenik meg. Az új képernyő megtekintéséhez tekintse [meg az alkalmazás felhasználói felületének újdonságai](https://docs.microsoft.com/intune/whats-new-app-ui)című témakört. A Céges portál alkalmazásokkal kapcsolatos további információkért lásd: [alkalmazások telepítése és megosztása](/intune-user-help/install-apps-cpapp-windows)az eszközön.  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Megfelelőségi alkalmazás Power BI <!-- 1455231 doc-work-item -->
Az Intune [megfelelőségi (adattárház-)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) alkalmazásával érheti el az Intune-adattárházat Power bi online-ban. Ezzel a Power BI alkalmazással mostantól a telepítés nélkül is elérheti és megoszthatja az előre létrehozott jelentéseket anélkül, hogy a böngészőt el kellene hagynia. További információkért lásd: a [log-Power bi megfelelőségi alkalmazás módosítása](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>A PowerShell-parancsfájlok 64 bites gazdagépen futtathatók 64 bites eszközökön <!-- 1862675   -->
Ha egy PowerShell-parancsfájlt ad hozzá egy eszköz konfigurációs profiljához, a parancsfájl a 32 bites verzióban, még a 64 bites operációs rendszereken is végrehajtja. Ezzel a frissítéssel a rendszergazda a 64 bites PowerShell-gazdagépen futtathatja a szkriptet a 64 bites eszközökön (az**eszköz konfigurációs** > **PowerShell** > -parancsfájljaihoz**adja hozzá** > a**configure**  > parancsot **Futtassa a szkriptet 64 bites PowerShell-gazdagépen**).

A PowerShell használatával kapcsolatos további információkért lásd: [PowerShell-parancsfájlok az Intune-ban](intune-management-extension.md).

Érintett kiadások: Windows 10 és újabb

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>a macOS-felhasználók a jelszavuk frissítésére kérik <!-- 1873216 -->
Az Intune a macOS-eszközök **ChangeAtNextAuth** beállítását érvényesíti. Ez a beállítás hatással van a végfelhasználók és az eszközök megfelelőségi jelszavas szabályzatokkal vagy az eszköz korlátozási jelszavas profiljaival. A rendszer egyszer kéri a végfelhasználókat a jelszavuk frissítésére. Ez akkor fordul elő, amikor egy felhasználó először futtat egy hitelesítést igénylő feladatot, például bejelentkezik az eszközre. A felhasználókat arra is kérheti, hogy a rendszergazdai jogosultságokat igénylő bármit, például a kulcstartók elérésének kérésével frissítse a jelszavát. 

A rendszergazda által megjelenő új vagy meglévő jelszóházirend-módosítások ismét frissítik a felhasználókat a jelszavuk frissítéséhez.

Érintett kiadások:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>SCEP-tanúsítványok társítása egy felhasználó nélküli macOS-eszközhöz  <!-- 2340521  -->
Egyszerű tanúsítványigénylési protokoll (SCEP) tanúsítványokat a macOS-eszközökhöz, például a felhasználói affinitás nélküli eszközökhöz, valamint a tanúsítvány profiljának a Wi-Fi-vagy VPN-profilokhoz való társításához rendelhet hozzá. Ez kibővíti azt a támogatást, amelyhez már hozzá van rendelve a SCEP-tanúsítványok a Windows, iOS és Android rendszerű [felhasználói affinitással rendelkező és azok nélküli eszközökhöz](certificates-scep-configure.md#create-a-scep-certificate-profile) .  Ezzel a frissítéssel kiválaszthatja az *eszköz* SCEP, ha a MacOS-hez konfigurálja a tanúsítvány-profilt.

Érintett kiadások: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune feltételes hozzáférés felhasználói felületének frissítése   <!-- 2432313   -->
Javítottuk a feltételes hozzáférés felhasználói felületét az Intune-konzolon. Ezek a következők:
- Lecserélte az Intune *feltételes hozzáférés* paneljét Azure Active Directoryról a panelre. Ez biztosítja, hogy a [feltételes hozzáférés](conditional-access.md) összes beállítását és konfigurációját (amely egy Azure ad-technológia marad) az Intune-konzolon belülről elérheti. 
- Átnevezte a helyszíni *hozzáférés* panelt az *Exchange*-hozzáférésre, és áthelyezte az *Exchange Service Connector* telepítőjét erre az átnevezett panelre.  Ez a változás összevonja az [Exchange Online-hoz és a helyszíni környezethez kapcsolódó részletek konfigurálásának és figyelésének](exchange-connector-install.md)helyét.  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>A teljes képernyős böngésző és a Microsoft Edge böngésző alkalmazásai a Windows 10-es eszközökön is futtathatók a kioszk módban <!-- 2935135   -->
A Windows 10-es eszközök teljes képernyős módban futtathatók egy alkalmazás vagy számos alkalmazás futtatásához. Ez a frissítés több módosítást is tartalmaz a böngészőbeli alkalmazások teljes képernyős módban való használatával, beleértve a következőket:

- A Microsoft Edge böngésző vagy a kioszk böngésző hozzáadása a kioszk eszközön futó alkalmazásokhoz (**eszköz-konfigurációs** > **profilok** > **új profil** > **Windows 10 és újabb verziók** a platform > **kioszkhoz** a profil típusa).
- Új funkciók és beállítások érhetők el az engedélyezéshez vagy a korlátozáshoz (az**eszköz konfigurációs** > **profiljai** > **új profil** > **Windows 10 és újabb verziók** a platform > **eszköz korlátozásai számára** profil típusa), beleértve a következőket:

- Microsoft Edge böngésző:
  - A Microsoft Edge kioszk mód használata
  - Böngésző frissítése üresjárati idő után

- Kedvencek és keresés:
  - Keresőmotor módosításának engedélyezése

A beállítások listáját a következő témakörben tekintheti meg:

- [A Windows 10 és újabb rendszerű eszközök beállításai kioszkként való futtatásra](kiosk-settings-windows.md)
- [Microsoft Edge böngésző eszköz korlátozásai](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Kedvencek és keresési eszközre vonatkozó korlátozások](device-restrictions-windows-10.md##favorites-and-search)

Érintett kiadások: Windows 10 és újabb

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Az iOS-és macOS-eszközök új eszköz-korlátozási beállításai <!-- 3448774   -->
Az iOS és MacOS rendszerű eszközökön bizonyos beállításokat és szolgáltatásokat korlátozhat (az**eszköz konfigurációs** > **profiljai** > **új profil** > **iOS** vagy **MacOS** platform >  **Az eszközre vonatkozó korlátozások** a profil típusa esetén). Ez a frissítés további funkciókat és beállításokat tartalmaz, amelyekkel szabályozható, például a képernyő időpontjának beállítása, a eSIM-beállítások és a mobil csomagok módosítása, valamint az iOS-eszközökön található további beállítások. Emellett a felhasználók a szoftverfrissítések láthatóságát, valamint a tartalom gyorsítótárazásának a macOS-eszközökön való blokkolását is késleltetheti. 

A korlátozni kívánt funkciók és beállítások megtekintéséhez tekintse meg a következőt:

- [iOS-eszközök korlátozási beállításai](device-restrictions-ios.md)
- [macOS-eszköz korlátozási beállításai](device-restrictions-macos.md)

Érintett kiadások:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>A "kioszk" eszközök mostantól "dedikált eszközök" néven jelennek meg az Android Enterprise-eszközökön <!-- 3598402   -->
Az Android-terminológiához való igazításhoz a **kioszk** az androidos vállalati eszközökhöz készült **dedikált eszközökre** változik (az**eszköz konfigurációs** > **profiljai** > a**profil létrehozása** > * * Android vállalati platform > **eszköz tulajdonosának csak** > a**dedikált eszközök** **korlátozása** > ).

Az elérhető beállítások megtekintéséhez válassza az [eszközbeállítások lehetőséget a funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md#dedicated-device-settings).

Érintett kiadások:  
Vállalati Android

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>A Safari és a késleltetés a felhasználó szoftverfrissítés láthatósága iOS-beállítások az Intune felhasználói felületén lesznek áthelyezve <!-- 3640850, 3803313   -->
IOS-eszközök esetén a Safari beállításait és a szoftverfrissítések konfigurálását is megadhatja. Ebben a frissítésben ezeket a beállításokat az Intune felhasználói felületének különböző részeire helyezi át:

- A Safari által áthelyezett Safari-beállítások (az eszköz**konfigurációs** > **profiljai** > **új profil** > **iOS** platform > eszközre vonatkozó **korlátozások** a profil típusa esetén) **[Beépített alkalmazások](device-restrictions-ios.md#built-in-apps)** .
- A **felügyelt iOS-eszközökre vonatkozó felhasználói szoftverfrissítés láthatósága** (a > szoftverfrissítési**frissítési szabályzatok iOS**rendszerhez) az **eszközre vonatkozó korlátozások** >  **[általános](device-restrictions-ios.md#general)** értékre vált.  További információ a meglévő szabályzatok hatásáról: [iOS-szoftverfrissítések](software-updates-ios.md#configure-the-policy). 

A beállítások listáját a következő témakörben tekintheti meg:

- [iOS-eszközök korlátozásai](device-restrictions-ios.md) 
- [iOS-szoftverfrissítések](software-updates-ios.md)

Ez a funkció az alábbiakra vonatkozik: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Az eszközbeállítások korlátozásait a rendszer az iOS-eszközökön a képernyő időpontjára átnevezi <!-- 3699164   -->
Konfigurálhatja a **korlátozásokat az eszközbeállítások** számára a felügyelt iOS-eszközökön (**az eszköz konfigurációs** > **profiljai** > **új profil** > **iOS** platformon > A profil típusának > **általános**) **eszközre vonatkozó korlátozásai** . Ebben a frissítésben ezt a beállítást a rendszer a képernyő időpontjára nevezi át **(csak felügyelt**eszköz esetén). 

A viselkedés ugyanaz. Kifejezetten 

- iOS-11.4.1 és korábbi verziók: A **Letiltás** megakadályozza, hogy a végfelhasználók saját korlátozásokat állítsanak be az eszközbeállítások számára. 
- iOS 12,0 és újabb verziók: A **Letiltás** beállítás megadásával megakadályozható, hogy a végfelhasználók saját **képernyős időt** állítsanak be az eszközbeállítások során, beleértve a tartalmakat & adatvédelmi korlátozásokat. Az iOS 12,0-re frissített eszközök többé nem látják a korlátozások lapot az eszközbeállítások lapon. Ezek a beállítások a **képernyőn**jelennek meg. 

A beállítások listáját az [iOS-eszközök korlátozásai](device-restrictions-ios.md#general)című témakörben tekintheti meg.

Érintett kiadások: 
- iOS


### <a name="device-management"></a>Eszközkezelés

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Regisztrált Windows-eszköz átnevezése <!-- 1911112  -->
Most már átnevezheti a regisztrált Windows 10-es eszközöket (RS4 vagy újabb). Ehhez válassza az **Intune** > -**eszközök** > **minden eszköz** lehetőséget > Válassza ki az eszközt > **nevezze át az eszközt**. Ez a funkció jelenleg nem támogatja a hibrid Azure AD Windows-eszközök átnevezését.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Hatókör-címkék automatikus társítása az adott hatókörrel rendelkező rendszergazda által létrehozott erőforrásokhoz <!-- 3173823  -->
Amikor egy rendszergazda létrehoz egy erőforrást, a rendszergazda számára rendelt összes hatókör-címke automatikusan hozzá lesz rendelve az új erőforrásokhoz.

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Sikertelen beléptetési jelentés az eszközök beléptetése panelre <!-- 3560202  -->
A **sikertelen regisztrációk** jelentés át lett helyezve az **eszközök** beléptetése panel **figyelő** szakaszába. Két új oszlop (regisztrációs módszer és operációsrendszer-verzió) lett hozzáadva.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Céges portál a lemondás jelentés átnevezve hiányos felhasználói regisztrációra <!--3815076 eemiss -->
A **céges portál** -megszakítási jelentés átnevezve **hiányos felhasználói regisztrációra**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>2019. február 4. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Intune macOS Céges portál sötét üzemmód <!-- 3300524  -->
Az Intune macOS Céges portál mostantól támogatja a sötét üzemmódot macOS rendszeren. Ha egy macOS 10.14 + eszközön engedélyezi a sötét üzemmódot, a Céges portál az adott üzemmódot tükröző színekre módosítja a megjelenését.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>2019. január 21. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Bejelentési értesítések a Win32-alkalmazásokhoz <!-- 3136566   -->
Az alkalmazás-hozzárendeléssel kapcsolatos végfelhasználói bejelentési értesítéseket nem lehet letiltani. Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** lehetőséget > Válassza ki az alkalmazás > **hozzárendelések** > **csoportok**lehetőséget. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Az Intune app Protection-szabályzatok felhasználói felületének frissítése <!-- 3251427  -->
Módosítottuk az Intune app Protection beállításainak és gombjainak feliratait, hogy könnyebben érthetőek legyenek. A módosítások némelyike a következőkből áll:  
- A vezérlőelemek **Igen** / **nem vezérlőkből** változnak, ígyelsődlegesen / azengedélyezésésaLetiltásengedélyezésevezérlőket / tiltják le. A címkék is frissülnek.  
- A beállítások formázva lesznek, így a beállítás és a címkéje egymás mellett, a vezérlőn belül, a jobb navigálás érdekében.   

Az alapértelmezett beállítások és a beállítások száma változatlan marad, de ez a módosítás lehetővé teszi, hogy a felhasználó könnyebben megértse, navigálja és használja a beállításokat a kiválasztott alkalmazás-védelmi szabályzatok alkalmazásához. További információ: [iOS-beállítások](app-protection-policy-settings-ios.md) és [Android-beállítások](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>További beállítások az Outlookhoz <!-- 3301182  -->
Mostantól az Intune-nal az iOS-hez és az Androidhoz készült Outlook további beállításait is konfigurálhatja:

- Csak a munkahelyi vagy iskolai fiókok használatának engedélyezése az Outlookban az iOS és az Android rendszerű eszközökön
- Modern hitelesítés üzembe helyezése az Office 365-ben és a modern hibrid hitelesítés helyszíni fiókoknál
- Az `SAMAccountName` e-mail-profil username (Felhasználónév) mezőjéhez használja az alapszintű hitelesítés kiválasztásakor
- Névjegyek mentésének engedélyezése
- Külső címzettek beállítása – levelezési tippek
- **Fókuszált beérkezett** fájlok konfigurálása
- A biometria megkövetelése az Outlook iOS-hez való hozzáféréséhez
- Külső lemezképek letiltása

> [!NOTE]
> Ha Intune App Protection házirendeket használ a vállalati identitásokhoz való hozzáférés kezelésére, érdemes megfontolnia, hogyne engedélyezze a biometrikus azonosítók megkövetelését. További információ: **vállalati hitelesítő adatok megkövetelése az** [iOS-hozzáférési beállítások](app-protection-policy-settings-ios.md#access-requirements) és az [Android-hozzáférési beállítások](app-protection-policy-settings-android.md#access-requirements)eléréséhez.

További információ: [Microsoft Outlook konfigurációs beállítások](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Androidos vállalati alkalmazások törlése <!-- 1352553 -->
A felügyelt Google Play-alkalmazásokat törölheti Microsoft Intuneról. Felügyelt Google Play-alkalmazás törléséhez nyissa meg Microsoft Intune a Azure Portal, és válassza az **ügyfélalkalmazások** > **alkalmazások**elemet. Az alkalmazás listából válassza a felügyelt Google Play alkalmazás jobb oldalán található három pontot (...), majd válassza a **Törlés** lehetőséget a megjelenített listából. Ha töröl egy felügyelt Google Play-alkalmazást az alkalmazások listájáról, a felügyelt Google Play-alkalmazás automatikusan nem lesz jóváhagyva.

#### <a name="managed-google-play-app-type----1352580---"></a>Felügyelt Google Play-alkalmazás típusa <!-- 1352580 -->
A **felügyelt Google Play** -alkalmazás típusa lehetővé teszi a felügyelt Google [Play-alkalmazások](https://play.google.com/work/search?q=microsoft&c=apps) konkrét hozzáadását az Intune-hoz. Intune-rendszergazdaként mostantól böngészhet, kereshet, jóváhagyhatja, szinkronizálhatja és hozzárendelheti a jóváhagyott felügyelt Google Play-alkalmazásokat az Intune-on belül.  Többé nem kell külön megkeresnie a felügyelt Google Play-konzolt, és többé nem kell újrahitelesítenie.  Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazások** > **Hozzáadás**lehetőséget. Az **alkalmazás típusa** listában válassza a **felügyelt Google Play** lehetőséget az alkalmazás típusa mezőben.

### <a name="default-android-pin-keyboard----3802457---"></a>Alapértelmezett androidos PIN-kód billentyűzete <!-- 3802457 -->
Azok a végfelhasználók, akik a "numerikus" PIN-kód típussal beállították az androidos eszközökön a Intune App Protection szabályzat (alkalmazás) PIN-kódját, az alapértelmezett Android-billentyűzetet fogják látni a korábban tervezett, rögzített androidos billentyűzet helyett. Ez a változás konzisztens volt az Android és az iOS alapértelmezett billentyűzetének használatakor, mind a "numerikus", mind a "PIN-kód" típusnál. További információ az Android rendszerhez készült végfelhasználói hozzáférési beállításokról, például az alkalmazás PIN-kódjáról: [Android-hozzáférési követelmények](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>A Microsoft által ajánlott beállítások használata biztonsági alaptervekkel (nyilvános előzetes verzió) <!-- 2055484   -->

Az Intune integrálható más, biztonsági célú szolgáltatásokkal, például a Windows Defender ATP-vel és az Office 365 ATP-vel. Az ügyfelek a Microsoft 365-szolgáltatásokon átívelő közös stratégiát és összefüggő, teljes körű biztonsági munkafolyamatokat kérnek. Célunk a stratégiák összehangolása és ezáltal olyan megoldások létrehozása, amelyek hidat képeznek a biztonsági műveletek és a gyakori felügyeleti feladatok között. Az Intune-ban ezen cél elérésére a Microsoft által ajánlott „biztonsági előírások” közzétételével törekszünk (**Intune** > **Biztonsági előírások**).  A rendszergazda biztonsági házirendeket hozhat létre közvetlenül ezekből az alaptervekről, majd telepítheti azokat a felhasználók számára. Testre szabhatja az ajánlott eljárásokat, hogy megfeleljenek a szervezet igényeinek. Az Intune biztosítja, hogy az eszközök megfeleljenek ezeknek az előírásoknak, és értesíti a rendszergazdákat, ha egy felhasználó vagy eszköz nem felel meg.

Ez a funkció nyilvános előzetes verzióban érhető el, így a most létrehozott profilok nem kerülnek át az általánosan elérhető (GA) biztonsági alapkonfigurációs sablonokra. Ezeket az előnézeti sablonokat nem ajánlott éles környezetben használni.

További információ a biztonsági alaptervekről: [a Windows 10 biztonsági alapkonfigurációjának létrehozása az Intune-ban](security-baselines-monitor.md).

Ez a funkció az alábbiakra vonatkozik: Windows 10 és újabb

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>A nem rendszergazdák engedélyezhetik a BitLocker használatát az Azure AD-hez csatlakoztatott Windows 10-es eszközökön<!-- 2147379   -->
Ha engedélyezi a BitLocker-beállítások Windows 10 rendszerű eszközökön (**eszközkonfiguráció** > **profilok** > **profil létrehozása**  >  **Windows 10 és újabb** tartozó platform > **az Endpoint protection** profiltípus > **Windows titkosítási**), akkor adja hozzá a BitLocker-beállítások. 

A frissítés tartalmaz egy új BitLocker beállítását, hogy általános jogú felhasználók (nem rendszergazda), engedélyezheti a titkosítást. 

A beállítások megjelenítéséhez nyissa meg a [Windows 10 Endpoint Protection-beállításai](endpoint-protection-windows-10.md#windows-encryption)című témakört.

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Configuration Manager megfelelőségének ellenőrzése <!-- 2192052  eepublished  -->
Ez a frissítés egy új System Center Configuration Manager megfelelőségi beállítást tartalmaz (az**eszköz megfelelőségi** > **szabályzatai** > a**Windows 10 és újabb**  >   >  **rendszerekhez tartozó házirendet hoznak létre Configuration Manager megfelelőség**). A Configuration Manager megfelelőségi jeleket küldi az Intune-nak. Ezzel a beállítással megkövetelheti, hogy az összes Configuration Manager-jel "megfelelő" értéket ad vissza.

Megkövetelhető például, hogy minden szoftverfrissítés telepítve legyen az eszközökön. A Configuration Managerben az ehhez a követelményhez tartozó állapot a „Telepítve”. Ha az eszközön bármely program ismeretlen állapotban van, akkor az eszköz nem megfelelő az Intune-ban.

A [Configuration Manager megfelelősége](compliance-policy-create-windows.md#configuration-manager-compliance) ezt a beállítást ismerteti.

Érintett kiadások: Windows 10 és újabb

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Háttérkép testreszabása felügyelt iOS-eszközökön az eszköz konfigurációs profiljának használatával <!-- 2809324   -->
Az iOS-eszközökhöz készült konfigurációs profil létrehozásakor testre szabhatja néhány funkciót (az**eszköz konfigurációs** > **profiljait** > a platformhoz tartozó**iOS** -es**profil** > létrehozása >  **Az eszköz funkciói** a profil típusa). Ez a frissítés új **tapéta** -beállításokat tartalmaz, amelyek lehetővé teszik, hogy a rendszergazda. png,. jpg vagy. jpeg képet használjon a kezdőképernyőn vagy a zárolási képernyőn. Ezek a háttérkép-beállítások csak a felügyelt eszközökre érvényesek. 

A beállítások listájáért lásd: iOS- [eszköz funkciójának beállításai](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Általánosan elérhető a Windows 10 kioszk <!-- 3594661  -->
Ebben a frissítésben a Windows 10-es és újabb rendszerű eszközökön a kioszk funkció általánosan elérhető (GA). Az összes felvehető és konfigurálható beállítás megjelenítéséhez tekintse meg a [Windows 10-es (és újabb) kioszk-beállítások](kiosk-settings.md)című témakört.

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>A névjegyek Bluetooth-kapcsolaton keresztüli megosztása el lesz távolítva az eszköz-korlátozásokkal > Android Enterprise-eszköz tulajdonosa <!-- 3598396   -->
Ha az androidos vállalati eszközökhöz hoz létre egy eszköz-korlátozási profilt, a rendszer **Bluetooth-kapcsolaton keresztül megosztja a partneri kapcsolatot** . Ebben a frissítésben a **névjegyek Bluetooth-kapcsolaton keresztüli megosztása** el lesz távolítva (az**eszköz konfigurációs** > **profiljainak** > **profil** > létrehozása**Android Enterprise** for platform >  **Az eszközökre vonatkozó korlátozások > az eszköz tulajdonosát** a profil típusa > **általános**). 

Az androidos vállalati eszközök tulajdonosi felügyelete nem támogatja a **névjegyek Bluetooth** -kapcsolaton keresztüli beállítását. Így ha eltávolítja ezt a beállítást, az nem érinti az eszközöket és a bérlőket, még akkor sem, ha ez a beállítás engedélyezve van és konfigurálva van a környezetben.

A beállítások aktuális listájának megtekintéséhez lépjen az [Android Enterprise-eszköz beállításai lehetőségre a funkciók engedélyezéséhez vagy korlátozásához](device-restrictions-android-for-work.md).

Érintett kiadások: Androidos vállalati eszköz tulajdonosa

### <a name="device-management"></a>Eszközkezelés

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Szelektív törlés támogatása beléptetési eszközök nélkül <!-- 1434452 -->
A Windows Information Protection regisztráció nélkül (folyamatban lévő – mi) lehetővé teszi, hogy az ügyfelek teljes MDM-regisztráció nélkül védjék a vállalati adataikat a Windows 10-es eszközökön. Ha a dokumentumok egy BEFEJEZetlen munkaterheléssel védettek, a védett adatok szelektíven törölhetők egy Intune-rendszergazda által. A felhasználó és az eszköz kiválasztásával, valamint a törlési kérelem elküldésével az összes, a folyamatban lévő munkaterületen keresztül védett adat használhatatlanná válik. Ehhez az Azure Portal Intune részén válassza a **Mobilalkalmazás** > **Alkalmazás szelektív törlése** lehetőséget.

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Új operatív naplók, és naplók küldésének lehetősége Azure Monitor szolgáltatásokba <!-- 3762211  -->
Az Intune beépített naplózási naplózással rendelkezik, amely nyomon követi az eseményeket. Ez a frissítés új naplózási funkciókat tartalmaz, beleértve a következőket: 
- Működési naplók (előzetes verzió), amelyek a regisztrált felhasználókra és eszközökre vonatkozó adatokat jelenítik meg, beleértve a sikeres és sikertelen kísérleteket.
- A naplók és az operatív naplók a Azure Monitorba küldhetők, beleértve a Storage-fiókokat, az Event hubokat és a log Analytics-t is. Ezek a szolgáltatások lehetővé teszik az olyan elemzések tárolását, mint például a splunk és a QRadar, valamint a naplózási adataik vizualizációinak beolvasása.

A [naplózási adatok elküldése a tárolóba, az Event hubokba vagy a log analyticsbe az Intune-ban](review-logs-using-azure-monitor.md) további információk jelennek meg a szolgáltatással kapcsolatban.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>További beállítási asszisztens képernyők kihagyása iOS DEP-eszközön <!-- 2687509  -->
A jelenleg kihagyható képernyők mellett beállíthatja az iOS DEP-eszközöket is, ha a felhasználó regisztrálja az eszközt: Hang-, adatvédelem-, Android-Migrálás, Kezdőlap gomb, iMessage & FaceTime, előkészítés, áttelepítés megtekintése, megjelenés, képernyő ideje, szoftverfrissítés, SIM-beállítás.
Válassza ki, amely a képernyők kihagyásához, lépjen a **eszközregisztráció** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > Válasszon egy tokent > **Profilok** > Válasszon egy profilt > **tulajdonságok** > **beállítási asszisztens testreszabása** > Válasszon **elrejtése**  bármely képernyők kihagyásához a > **OK**.
Ha új profilt hoz létre vagy szerkeszt egy profilt, a kijelölt kihagyási képernyőknek szinkronizálnia kell az Apple MDM-kiszolgálóval. A felhasználók manuálisan is szinkronizálhatják az eszközöket, így nincs késés a profil módosításainak felvételekor.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise-alkalmazás – alkalmazás üzembe helyezése <!-- 1171203 -->
A nem regisztrált app Protection-szabályzatok (APP-WE) üzembe helyezési forgatókönyve nélküli Android-eszközök esetén a felügyelt Google Play használatával telepítheti az áruházbeli alkalmazásokat és ÜZLETÁGI alkalmazásokat a felhasználók számára. Pontosabban megadhatja a végfelhasználók számára egy olyan alkalmazás-katalógust és telepítési folyamatot, amely már nem igényli a végfelhasználók számára, hogy az ismeretlen forrásból származó telepítések engedélyezésével fellazítsák az eszközeik biztonsági állapotát. Emellett ebben a telepítési forgatókönyvben egy jobb végfelhasználói élményt biztosít.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>2019. január 14-i hét

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Az Android vállalat által birtokolt, teljes körűen felügyelt eszközök támogatásának előzetes verziója <!-- 1574342  -->
Az Intune mostantól támogatja a teljes körűen felügyelt Android-eszközöket, a vállalat által birtokolt "eszköz tulajdonosa" forgatókönyvet, amelyben az eszközöket szorosan felügyelik, és az egyes felhasználókhoz kapcsolódnak. Ez lehetővé teszi a rendszergazdák számára a teljes eszköz felügyeletét, a szabályzatok kiterjesztett tartományának érvénybe léptetését a munkahelyi profilokhoz, és korlátozza a felhasználókat, hogy csak a felügyelt Google Play áruházból telepítsenek alkalmazásokat. További információkért lásd: az [Android teljes körűen felügyelt eszközök Intune-regisztrációjának beállítása](android-fully-managed-enroll.md) és [a dedikált eszközök vagy teljes körűen felügyelt eszközök regisztrálása](android-dedicated-devices-fully-managed-enroll.md).  Vegye figyelembe, hogy ez a funkció előzetes verzióban érhető el. Bizonyos Intune-képességek, például a tanúsítványok, a megfelelőség és a feltételes hozzáférés jelenleg nem érhetők el az Android teljes körűen felügyelt felhasználói eszközeivel.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>2019. január 7. hét

### <a name="app-management"></a>Alkalmazáskezelés

#### <a name="intune-app-pin----2298397---"></a>Intune-alkalmazás PIN-kódja <!-- 2298397 -->
A rendszergazdaként beállíthatja, hogy a végfelhasználók hány napig várhatják el az Intune-alkalmazás PIN-kódjának módosítását. Az új beállítás PIN-kód alaphelyzetbe állítása a *napok száma után* , és a Azure Portal elérhető az **Intune** > **ügyfélalkalmazások** > alkalmazás-**védelmi szabályzatok** > **házirend** létrehozásaelemérekattintva. >  **Beállítások** **Hozzáférési követelmények**.  >  [IOS](app-protection-policy-settings-ios.md) -és [Android](app-protection-policy-settings-android.md) -eszközökhöz érhető el, ez a funkció pozitív egész értéket támogat.


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune-eszközök jelentéskészítési mezői <!-- 2748738 -->
Az Intune további eszköz-jelentési mezőket biztosít, beleértve az alkalmazás regisztrációs AZONOSÍTÓját, az Android-gyártót, a modellt és a biztonsági javítás verzióját, valamint az iOS-modellt is. Az Intune-ban ezek a mezők az **ügyfélalkalmazások** > **app Protection állapotának** kiválasztásával és az App Protection-jelentés kiválasztásával érhetők el **: iOS, Android**. Emellett ezek a paraméterek segítségével konfigurálja a **engedélyezése** lista az eszköz gyártója (Android), a **engedélyezése** lista az eszköz modellje (Android és iOS) és a minimális Android biztonsági javítási szintnek verzió beállítását. 


### <a name="device-configuration"></a>Eszközök konfigurálása

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>A felügyeleti sablonok nyilvános előzetes verzióban érhetők el, és a saját konfigurációs profiljába kerülnek <!-- 3322847 -->

Az Intune-ban található felügyeleti sablonok (az**eszköz konfigurációja** > **Felügyeleti sablonok**) jelenleg nyilvános előzetes verzióban érhetők el. Ezzel a frissítéssel:

- A felügyeleti sablonok tartalmazzák az Intune-ban felügyelhető 300-beállításokat. Korábban ezek a beállítások csak megtalálható a Helyicsoportházirend-szerkesztő.
- A felügyeleti sablonok nyilvános előzetes verzióban érhetők el.
- A felügyeleti sablonok az **eszköz konfigurációjának** > **felügyeleti sablonjairól** az **eszköz konfigurációs** > **profiljaira** > térnek át a**profil létrehozása** > a következőben:  **Platform**, válassza a **Windows 10 és újabb** > a **Profil típusa**területen válassza a **Felügyeleti sablonok**lehetőséget.
- A jelentéskészítés engedélyezve van

A szolgáltatással kapcsolatos további információkért látogasson el a [Windows 10 sablonjaira a csoportházirend-beállítások konfigurálásához](administrative-templates-windows.md).

Érintett kiadások: Windows 10 és újabb

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Az S/MIME használata több eszköz titkosításához és aláírásához a felhasználó számára  <!-- 1333642 -->
A frissítés része az új importált tanúsítványprofilt használó S/MIME e-mail-titkosítás (**Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** > platform kiválasztása > **Importált PKCS-tanúsítvány** profiltípus). Az Intune-ban a tanúsítványok PFX formátumban importálhatók. Az Intune képes ugyanazokat a tanúsítványokat az egy felhasználó által regisztrált több eszközre is telepíteni. Ez a következőket is magában foglalja:
- A natív iOS-es e-mail-profil támogatja az S/MIME titkosítás PFX formátumú importált tanúsítványok használatával történő engedélyezését.
- A Windows Phone 10 rendszerű eszközök natív levelezőalkalmazása automatikusan az S/MIME tanúsítványt használja.
- A privát tanúsítványok több platformon is telepíthetők. A S/MIME-ot azonban nem minden e-mail-alkalmazás támogatja.
- Más platformokon az S/MIME engedélyezéséhez szükség lehet a levelező alkalmazás manuális konfigurálására.  
- Az S/MIME titkosítást támogató e-mail-alkalmazások esetleg az MDM által nem támogatható módon kezelik az S/MIME e-mail-titkosításhoz szükséges tanúsítványok fogadását, például a közzétevőjük tanúsítványtárából olvassák ki azokat.
A szolgáltatással kapcsolatos további információkért tekintse meg az [S/MIME-áttekintést az e-mailek aláírásához és titkosításához](certificates-s-mime-encryption-sign.md).
Támogatott a következő rendszereken: Windows, Windows Phone-telefon 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Új beállítások a szabályok automatikus csatlakoztatásához és a DNS-beállítások Windows 10 és újabb rendszerű eszközökön való használatakor <!-- 1333665, 2999078 -->
Windows 10 és újabb rendszerű eszközökön létrehozhat egy VPN-konfigurációs profilt, amely tartalmazza a tartományok feloldására szolgáló DNS-kiszolgálók listáját, például contoso.com. Ez a frissítés új beállításokat tartalmaz a névfeloldáshoz (**eszköz-konfigurációs** > **profilok** > **profil létrehozása** > válassza a **Windows 10 és újabb verziók** lehetőséget a platform > válassza a **VPN** lehetőséget a profil típusaként. > **DNS-beállítások** >**hozzáadása**): 
- **Automatikus összekapcsolás**: Ha **engedélyezve van**, az eszköz automatikusan csatlakozik a VPN-hez, amikor egy eszköz kapcsolatba lép egy megadott tartománnyal, például contoso.com.
- **Állandó**: Alapértelmezés szerint az összes névfeloldási házirend Table (NRPT) szabály aktív, ha az eszköz ehhez a VPN-profilhoz van csatlakoztatva. Ha a beállítás **engedélyezve** van egy NRPT-szabályon, a szabály aktív marad az eszközön, még akkor is, ha a VPN megszakad. A szabály addig marad, amíg el nem távolítja a VPN-profilt, vagy amíg a szabályt manuálisan nem távolítja el, ami a PowerShell használatával végezhető el.
A [Windows 10-es VPN-beállítások](vpn-settings-windows-10.md) a beállításokat ismertetik. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>A VPN-profilok megbízható hálózati észlelésének használata Windows 10-es eszközökön <!-- 1500165 -->
A megbízható hálózati észlelés használata esetén megakadályozhatja, hogy a VPN-profilok automatikusan hozzanak létre VPN-kapcsolatokat, ha a felhasználó már megbízható hálózaton van. Ezzel a frissítéssel hozzáadhat DNS-utótagokat a megbízható hálózatok észlelésének engedélyezéséhez a Windows 10 vagy újabb rendszerű eszközökön (az**eszköz konfigurációs** > **profiljai** > a**profil** > létrehozása**Windows 10 és később** a platform > a **VPN** a profil típusa).
[A Windows 10-es VPN-beállítások](vpn-settings-windows-10.md) sorolja fel az aktuális VPN-beállításokat.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Több felhasználó által használt Windows holografikus for Business-eszközök kezelése <!-- 1907917, 1063203 -->
Jelenleg az egyéni OMA-URI beállítás használatával konfigurálhatja a Windows 10 és a Windows holografikus for Business rendszerű eszközök megosztott számítógép-beállításait. Ezzel a frissítéssel új profilt ad hozzá a megosztott eszközbeállítások konfigurálásához (az**eszköz konfigurációs** > **profiljai** > **Windows 10 és újabb**  >  >  **profilok létrehozása Megosztott többfelhasználós eszköz**).
Ha többet szeretne megtudni erről a szolgáltatásról, lépjen az Intune-beállítások elemre a [megosztott eszközök kezeléséhez](shared-user-device-settings.md).
Érintett kiadások: Windows 10 és újabb verziók, Windows holografikus vállalatoknak

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Új Windows 10 frissítési beállítások <!--2626030  2512994  -->
A [Windows 10-es frissítési gyűrűkhöz](windows-update-for-business-configure.md)a következőket állíthatja be:
- **Automatikus frissítési viselkedés** – új lehetőség használata, alaphelyzetbe *állítás az alapértelmezett* értékre, ha vissza szeretné állítani az eredeti automatikus frissítési beállításokat egy Windows 10-es gépen az *október 2018 frissítést* futtató gépeken.
- A **felhasználó megakadályozása a Windows-frissítések szüneteltetésében** – új szoftverfrissítési beállítások konfigurálása, amely lehetővé teszi a felhasználók számára, hogy letiltsák vagy engedélyezzék a frissítések telepítését a gépek *beállításaiból* . 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>az iOS-es e-mail profilok az S/MIME-aláírást és a titkosítást is használhatják <!-- 2662949 -->
Létrehozhat egy olyan e-mail-profilt, amely különböző beállításokat tartalmaz. Ez a frissítés olyan S/MIME-beállításokat tartalmaz, amelyek az e-mailes kommunikációnak az iOS-eszközökön való aláírására és titkosítására használhatók (**eszköz-konfigurációs** > **profilok** > **profil létrehozása** > válassza az **iOS** lehetőséget platform > **e-mail-** profil típusa).
az [iOS e-mail konfigurációs beállításai](email-settings-ios.md) a beállításokat listázza.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Egyes BitLocker-beállítások a Windows 10 Pro kiadását támogatják<!-- 2727036 -->
Létrehozhat egy olyan konfigurációs profilt, amely az Endpoint Protection beállításait beállítja Windows 10-es eszközökön, beleértve a BitLockert is. Ez a frissítés az egyes BitLocker-beállításokhoz nyújt támogatást a Windows 10 Professional Edition rendszerhez. A védelmi beállítások megtekintéséhez válassza a [Windows 10 Endpoint Protection-beállítások](endpoint-protection-windows-10.md#windows-encryption)elemét.

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>A megosztott eszköz konfigurációját a rendszer a Azure Portal iOS-eszközök zárolási képernyőjének üzenetére átnevezi<!-- 2809362 -->
Az iOS-eszközökhöz készült konfigurációs profil létrehozásakor megadhatja a **megosztott eszköz konfigurációs** beállításait a zárolási képernyőn megadott szöveg megjelenítéséhez. Ez a frissítés a következő módosításokat tartalmazza: 
- A **megosztott eszköz konfigurációja** beállítások az Azure Portalon a rendszer átnevezi "Üzenet a zárolási képernyőn (csak felügyelt)" (**eszközkonfiguráció** > **profilok**  >  **Profil létrehozása** > Válasszon **iOS** tartozó platform > Válasszon **eszközfunkciók** profiltípus > **zárolása Üzenet képernyőn**).
- A zárolási képernyő üzeneteinek hozzáadásakor beszúrhat egy sorozatszámot, egy eszköznév vagy egy másik, az eszközre jellemző értéket változóként az **eszköz címkéjének adatai** és a **zárolási képernyő lábjegyzetében**. Beírhatja például `Device name: {{devicename}}` vagy `Serial number is {{serialnumber}}` kapcsos zárójelek használatával. [iOS-jogkivonatok](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) felsorolja a rendelkezésre álló jogkivonatokat használhat.
A [zárolási képernyőn lévő üzenetek megjelenítéséhez szükséges beállítások](shared-device-settings-ios.md) a beállításokat jelenítik meg.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Új App Store, doc Viewing, Gaming Device korlátozási beállítások hozzáadása iOS-eszközökhöz <!-- 2827760-->
Az **eszköz konfigurációs** > **profiljaiban** > **hozzon létre profil** > **iOS** for platform > **eszköz korlátozások** a profil típusa > **App Store, doc Viewing, Gaming**, a következő beállítások lesznek hozzáadva: A felügyelt alkalmazások számára lehetővé teszi a névjegyek írását a nem felügyelt Névjegyalbum-fiókok számára, hogy a nem felügyelt alkalmazások beolvassák a felügyelt névjegyek fiókjait a beállítások megtekintéséhez, lépjen az [iOS-eszközök korlátozásai](device-restrictions-ios.md#app-store-doc-viewing-gaming)közé

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Új értesítések, tippek és billentyűzár-beállítások az androidos vállalati eszközök tulajdonosi eszközeihez <!-- 3201839 3201843 -->
A frissítés számos új funkciót, a vállalati Android-eszköz tartalmaz az eszköz tulajdonosa futtatásakor. Ezeket a funkciókat használ, lépjen a **eszközkonfiguráció** > **profilok** > **profil létrehozása** > a **Platform**, válassza a **Android Enterprise** > a **profiltípus**, válassza a **csak az eszköz tulajdonosa** > **eszköz Korlátozások**.

Új funkciók: 

- Tiltsa le a rendszerértesítéseket, beleértve a bejövő hívásokat, a rendszerriasztásokat, a rendszerhibákat és egyebeket.
- Azt javasolja, hogy kiugorjon az első alkalommal megnyitott alkalmazásokhoz kapcsolódó oktatóanyagok és útmutatók.
- Tiltsa le a speciális billentyűzár-beállításokat, például a kamerát, az értesítéseket, az ujjlenyomatok feloldását és egyebeket.


A beállítások megjelenítéséhez nyissa meg az [Android Enterprise-eszközök korlátozási beállításait](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Az androidos vállalati eszközök tulajdonosi eszközei mindig a VPN-kapcsolatokon keresztül használhatók <!-- 3202194 -->
Ebben a frissítésben mindig bekapcsolt VPN-kapcsolatok Android enterprise eszköz tulajdonosa eszközökön is használhatja. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal újraindítható, ha a felhasználó feloldja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. A kapcsolat „zárolt” módba is állítható, amely blokkol minden hálózati forgalmat, amíg a VPN-kapcsolat aktív.
Engedélyezheti a mindig bekapcsolt VPN **eszközkonfiguráció** > **profilok** > **profil létrehozása**  >   **Android enterprise** tartozó platform > **eszközkorlátozások** az eszköz tulajdonosa csak > **kapcsolat** beállításait. A beállítások megjelenítéséhez nyissa meg az [Android Enterprise-eszközök korlátozási beállításait](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Új beállítás a Windows 10-es eszközök Feladatkezelő-folyamatainak befejezéséhez <!-- 3285177 --> 
A frissítés tartalmaz egy új beállítás a Feladatkezelő használatát a Windows 10 rendszerű eszközökön folyamatait. Eszközkonfigurációs profil használatával (**eszközkonfiguráció** > **profilok** > **profil létrehozása** > a **Platform** , válassza a **Windows 10-es** > a **profiltípus**, válassza a **eszközkorlátozások** > **általános** beállítások), engedélyezése vagy tiltása, ezt a beállítást választja.
A beállítások megtekintéséhez nyissa meg a [Windows 10-es eszközök korlátozási beállításait](device-restrictions-windows-10.md).
Érintett kiadások: Windows 10 és újabb


### <a name="device-enrollment"></a>Eszközök beléptetése

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Részletesebb regisztrációt korlátozó sikertelen üzenetküldés <!-- 3111564 -->
Részletesebb hibaüzenetek érhetők el, ha a regisztrációs korlátozások nem teljesülnek. Tekintse meg ezeket az üzeneteket, lépjen a **Intune** > **hibaelhárítás** >, és ellenőrizze a regisztrációs hibák tábla. További információ: a beléptetési [hibák listája](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Monitorozás és hibaelhárítás

#### <a name="tenant-status-dashboard-----1124854---"></a>Bérlői állapot irányítópultja  <!-- 1124854 -->
Az új [bérlő állapota lap](tenant-status.md) egyetlen helyet biztosít, ahol megtekintheti a bérlő állapotát és kapcsolódó részleteit.  Az irányítópult négy területre oszlik:
- **Bérlői adatok** – megjeleníti a bérlő nevét és helyét, a Mdm-szolgáltatót, a bérlő összes regisztrált eszközét, valamint a licencek számát. Ez a szakasz a bérlő aktuális szolgáltatásának kiadását is felsorolja.
- **Összekötő állapota** – megjeleníti a konfigurált elérhető összekötők adatait, és azokat is listázhatja, amelyek még nincsenek engedélyezve.  
   Az egyes összekötők aktuális állapota alapján a rendszer Kifogástalanként, figyelmeztetésként vagy sérültként jelöli meg őket. Válasszon ki egy összekötőt a részletezéshez, és tekintse meg a részleteket, vagy konfiguráljon további információkat.
- **Intune Service Health** – a Bérlővel kapcsolatos aktív incidensek és kimaradások részleteit jeleníti meg. Az ebben a szakaszban található információkat a rendszer közvetlenül az Office Message Centerből kéri le.
- **Intune Hírek** – megjeleníti a bérlőhöz tartozó aktív üzeneteket. Az üzenetek olyan dolgok, mint például az értesítések, amikor a bérlő megkapja az Intune legújabb funkcióit.  Az ebben a szakaszban található információkat a rendszer közvetlenül az Office Message Centerből kéri le.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Új Súgó-és támogatási élmény a Windows 10-es Céges portál <!-- 1488939-->
Az új Céges portál Súgó & támogatási oldal segít a felhasználóknak a hibaelhárításban, és segítséget kérni az alkalmazás-és hozzáférési problémákhoz. Az új lapon e-mail-hibaüzeneteket és a diagnosztikai napló részleteit is megtalálhatja, és megkeresheti a szervezet ügyfélszolgálatának részleteit. Emellett a kapcsolódó Intune-dokumentációra mutató hivatkozásokkal is megtalálják a gyakori kérdések szakaszt. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Új Súgó és támogatási élmény az Intune-hoz   <!-- #3307080 -->
Az új Súgó és támogatás élményét minden bérlő számára elérhetővé tesszük a következő néhány napban. Ez az új felhasználói felület elérhető az Intune-ban, és a [Azure Portalban](https://portal.azure.com/)található Intune-pengék használatával érhető el.
Az új felületen saját szavaival fejtheti ki problémáját, valamint hibaelhárítási ötleteket kaphat, és webalapú szervizelési tartalmakat találhat. Ezeket a megoldásokat egy, a felhasználói lekérdezések által vezérelt, szabályon alapuló gépi tanulási algoritmus segítségével ajánljuk. A probléma-specifikus útmutatás mellett az új eset-létrehozási munkafolyamattal is megnyithat egy támogatási esetet e-mailben vagy telefonon. Ez az új felhasználói élmény a Súgó és támogatás megnyitásakor a konzol területén alapuló, előre kiválasztott beállítások statikus készletének korábbi súgóját és támogatását váltja fel. További információkért lásd: [a Microsoft Intune támogatásának](get-support.md)beszerzése.

### <a name="role-based-access-control"></a>Szerepköralapú hozzáférés-vezérlés

#### <a name="scope-tags-for-apps----1081941---"></a>Alkalmazások hatókör-címkéi <!-- 1081941 -->
Hatókör-címkéket hozhat létre a szerepkörök és alkalmazások hozzáférésének korlátozásához. Hatókör-címkét adhat hozzá egy alkalmazáshoz, hogy csak a szerepkörökhöz hozzárendelt felhasználók férjenek hozzá az alkalmazáshoz. Jelenleg az Intune-hoz hozzáadott, felügyelt Google Play-vagy Apple Volume Purchase Program-(VPP-) alkalmazással megvásárolt alkalmazások nem rendelhetők hozzá hatóköri címkékhez (a jövőbeli támogatás tervezett). További információkért lásd: [hatókör-címkék használata a házirendek szűréséhez](scope-tags.md).

## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
