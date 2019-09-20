---
title: A Microsoft Intune App SDK iOS rendszeren – fejlesztői útmutató
description: Az iOS-hez készült Microsoft Intune App SDK lehetővé teszi, hogy Intune-alkalmazásvédelmi szabályzatokat (vagy más néven APP- vagy MAM-szabályzatokat) építsen be natív iOS-alkalmazásába.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/17/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb9d6921a3a2bfa3556e0a8b010e42dddc62a656
ms.sourcegitcommit: 89a973bbfa1702b2d275af6814874e4305bdcb77
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/19/2019
ms.locfileid: "71140738"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>A Microsoft Intune App SDK iOS rendszeren – fejlesztői útmutató

> [!NOTE]
> Javasoljuk, hogy olvassa el az [Intune App SDK használatának első lépései](app-sdk-get-started.md) című cikket, mely útmutatást nyújt az integráció előkészítéséhez a támogatott platformokon.

Az iOS-hez készült Microsoft Intune App SDK lehetővé teszi, hogy Intune-alkalmazásvédelmi szabályzatokat (vagy más néven APP- vagy MAM-szabályzatokat) építsen be natív iOS-alkalmazásába. A MAM-kompatibilis alkalmazás az, amelyik integrálva van az Intune App SDK-val. Mindez lehetővé teszi a rendszergazdáknak, hogy alkalmazásvédelmi szabályzatokat telepítsenek a mobilalkalmazásra vonatkozóan, ha az Intune aktívan felügyeli az alkalmazást.

## <a name="prerequisites"></a>Előfeltételek

* Szüksége lesz egy Mac OS operációs rendszerű számítógépre, amely az OS X 10.8.5 vagy újabb verzióját futtatja, és a Xcode 9-es vagy újabb verziójával is rendelkezik.

* Az alkalmazásnak az iOS 10-es vagy újabb verzióival kell működnie.

* Olvassa el [az iOS-hez készült Intune App SDK licencfeltételeit](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf). Nyomtassa ki és őrizze meg a licencfeltételeket. Az iOS-hez készült Intune App SDK letöltésével és használatával elfogadja licencfeltételeket.  Amennyiben a feltételeket nem fogadja el, ne használja a szoftvert.

* Töltse le az iOS-re készült Intune App SDK fájljait a [GitHubról](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk-repository"></a>Az SDK-tárház ismertetése

A következő fájlok olyan alkalmazásokhoz/bővítményekhez kapcsolódnak, amelyek nem tartalmaznak Swift-kódot, vagy a Xcode a 10,2 előtti verzióval vannak lefordítva:

* **IntuneMAM. Framework**: Az Intune app SDK keretrendszere. Javasoljuk, hogy az Intune ügyfélalkalmazások felügyeletének engedélyezéséhez csatolja ezt a keretrendszert az alkalmazáshoz vagy a bővítményekhez. Előfordulhat azonban, hogy néhány fejlesztő előnyben részesíti a statikus könyvtár teljesítménybeli előnyeit. Tekintse meg a következőket.

* **libIntuneMAM.a**: Az Intune app SDK statikus könyvtára. A fejlesztők dönthetnek úgy, hogy a keretrendszer helyett a statikus könyvtárat kapcsolják össze. Mivel a statikus kódtárak a létrehozáskor közvetlenül az alkalmazásba vagy a bővítmény bináris fájljába vannak beágyazva, bizonyos indítási idejű teljesítménybeli előnyökkel jár a statikus könyvtár használata. Az alkalmazásba való integrálás azonban bonyolultabb folyamat. Ha az alkalmazás bármely bővítményt tartalmaz, a statikus függvénytár az alkalmazáshoz és a bővítményekhez való csatolása nagyobb méretű alkalmazáscsomag-méretet eredményez, mivel a statikus függvénytár be lesz ágyazva az egyes alkalmazások/bővítmények bináris fájljaiba. A keretrendszer használatakor az alkalmazások és a bővítmények megoszthatják az Intune SDK bináris fájlját, ami kisebb méretű alkalmazásokhoz vezet.

* **IntuneMAMResources. Bundle**: Az SDK által használt erőforrásokat tartalmazó erőforrás-csomag. Az erőforrás-köteg csak olyan alkalmazások esetében szükséges, amelyek integrálják a statikus könyvtárat (libIntuneMAM. a).

A következő fájlok relevánsak a Swift-kódot tartalmazó alkalmazások/bővítmények számára, és a Xcode 10.2 +:

* **IntuneMAMSwift. Framework**: Az Intune app SDK Swift keretrendszere. Ez a keretrendszer tartalmazza az alkalmazás által meghívott API-k összes fejlécét. Csatolja ezt a keretrendszert az alkalmazáshoz/bővítményekhez az Intune ügyfélalkalmazások felügyeletének engedélyezéséhez.

* **IntuneMAMSwiftStub.framework**: Az Intune app SDK Swift helyettes keretrendszere. Ez egy kötelező függőség a IntuneMAMSwift. Framework számára, mely alkalmazásoknak/bővítményeknek kell kapcsolódniuk.


A következő fájlok tartoznak az összes alkalmazáshoz/egységhez:

* **IntuneMAMConfigurator**: Az alkalmazás vagy a bővítmény info. plist fájljának konfigurálására szolgáló eszköz az Intune felügyeletének minimálisan szükséges módosításaival. Az alkalmazás vagy a bővítmény funkciójának függvényében előfordulhat, hogy további manuális módosításokat kell végeznie az info. plist fájlban.

* **Fejlécek**: Elérhetővé teszi a nyilvános Intune app SDK API-kat. Ezek a fejlécek a IntuneMAM/IntuneMAMSwift keretrendszerek részét képezik, így a keretrendszerek valamelyikét használó fejlesztőknek nem kell manuálisan hozzáadniuk a saját projekthez a fejléceket. A statikus könyvtárral (libIntuneMAM. a) összekapcsoló fejlesztőknek manuálisan kell tartalmazniuk ezeket a fejléceket a projektben.

Az alábbi fejlécfájlok tartalmazzák azokat az API-kat, adattípusokat és protokollokat, melyek az Intune APP SDK-val elérhetővé válnak a fejlesztők számára:

-  IntuneMAMAppConfig.h
-  IntuneMAMAppConfigManager.h
-  IntuneMAMDataProtectionInfo.h
-  IntuneMAMDataProtectionManager.h
-  IntuneMAMDefs.h
-  IntuneMAMDiagnosticConsole. h
-  IntuneMAMEnrollmentDelegate.h
-  IntuneMAMEnrollmentManager.h
-  IntuneMAMEnrollmentStatus.h
-  IntuneMAMFileProtectionInfo.h
-  IntuneMAMFileProtectionManager.h
-  IntuneMAMLogger.h
-  IntuneMAMPolicy.h
-  IntuneMAMPolicyDelegate.h
-  IntuneMAMPolicyManager.h
-  IntuneMAMVersionInfo.h

A fejlesztők a IntuneMAM. h fájl importálásával is elérhetővé tehetik az összes korábbi fejléc tartalmát.


## <a name="how-the-intune-app-sdk-works"></a>Az Intune App SDK működése

Az iOS-hoz készült Intune App SDK révén minimális kódmódosítással adhat hozzá felügyeleti funkciókat az iOS-alkalmazásokhoz. Minél kevesebb a kód a piacra kerülési időt, de nem befolyásolja a mobil alkalmazása egységességét és stabilitását.


## <a name="build-the-sdk-into-your-mobile-app"></a>Az SDK beépítése a mobilalkalmazásba

Az Intune App SKD engedélyezéséhez kövesse az alábbi lépéseket:

1. **1. lehetőség – keretrendszer (ajánlott)** : Ha a Xcode 10.2 + alkalmazást használja, és az alkalmazás/bővítmény a Swift kódot, `IntuneMAMSwift.framework` a `IntuneMAMSwiftStub.framework` hivatkozást és a célt tartalmazza: Húzza a mutatót a projekt céljaként szolgáló **beágyazott bináris fájlok** listájára. `IntuneMAMSwift.framework` `IntuneMAMSwiftStub.framework`

    Ellenkező esetben a `IntuneMAM.framework` cél hivatkozása: Húzza az `IntuneMAM.framework` keretrendszert a projekthez használni kívánt elemek **Embedded Binaries** (Beágyazott bináris fájlok) listájába.

   > [!NOTE]
   > Ha a keretrendszert használja, manuálisan kell eltávolítania a szimulátorarchitektúrákat az univerzális keretrendszerből, mielőtt beküldi az alkalmazást az App Store-ba. További információért lásd [Az alkalmazás beküldése az App Store-ba](#submit-your-app-to-the-app-store) című témakört.

   **2. lehetőség – statikus könyvtár**: Ez a beállítás csak olyan alkalmazások/bővítmények esetében érhető el, amelyek nem tartalmaznak Swift-kódot, vagy a Xcode < 10,2-es verzióval készültek. A `libIntuneMAM.a` könyvtárra mutató hivatkozás. Húzza a `libIntuneMAM.a` könyvtárat a projekthez használni kívánt elemek **Linked Frameworks and Libraries** (Csatolt keretrendszerek és könyvtárak) listájába.

    ![Intune App SDK (iOS) – csatolt keretrendszerek és könyvtárak](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Írja be a `-force_load {PATH_TO_LIB}/libIntuneMAM.a` utasítást a következő helyek egyikére, kicserélve a `{PATH_TO_LIB}` sort az Intune App SDK elérési útjával:
   * A projekt `OTHER_LDFLAGS` Build konfigurációs beállítása.
   * A Xcode felhasználói felületének **másik mutatója**.

     > [!NOTE]
     > A `PATH_TO_LIB` megkereséséhez jelölje ki a `libIntuneMAM.a` fájlt és, és válassza a **File** (Fájl) menü **Get Info** (Információ megjelenítése) parancsát. Másolja és illessze be a **Where** (Hely) feliratnál látható információt (az elérési utat) az **Info** (Információ) ablak **General** (Általános) szakaszából.

     Húzza az `IntuneMAMResources.bundle` erőforrás-csomagot a **Copy Bundle Resources** (Erőforrás-csomagok másolása) alatti **Build Phases** (Összeállítási fázisok) elemre a projektbe való felvételhez.

     ![Intune App SDK (iOS) – erőforráscsomagok másolása](./media/intune-app-sdk-ios-copy-bundle-resources.png)
         
2. Vegye fel a következő iOS-keretrendszereket a projektbe:  
-  MessageUI.framework  
-  Security.framework  
-  MobileCoreServices.framework  
-  SystemConfiguration.framework  
-  libsqlite3.tbd  
-  libc++.tbd  
-  ImageIO.framework  
-  LocalAuthentication.framework  
-  AudioToolbox.framework  
-  QuartzCore.framework  
-  WebKit.framework

3. Engedélyezze a kulcsláncmegosztást (ha még nincs engedélyezve) a projekthez használni kívánt elemeken a **Capabilities** (Képességek) lehetőségre kattintva, majd kapcsolja be a **Keychain Sharing** (Kulcsláncmegosztás) kapcsolót. A következő lépéshez szükséges a kulcsláncmegosztás.

   > [!NOTE]
   > A telepítési profil esetében elengedhetetlen az új kulcsláncmegosztási értékek támogatása. A kulcslánc-hozzáférési csoportoknak támogatniuk kell a helyettesítő karaktert. Ezt úgy is megtekintheti, ha megnyitja a. mobileprovision fájlt egy szövegszerkesztőben, megkeresi a **kulcstartó-hozzáférési csoportokat**, és gondoskodik arról, hogy legyen helyettesítő karaktere. Példa:
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. A kulcstartó megosztásának engedélyezése után kövesse az alábbi lépéseket egy külön hozzáférési csoport létrehozásához, amelyben az Intune app SDK tárolja az adattárolót. A kulcslánc-hozzáférési csoportokat a kezelőfelületet vagy a jogosultságokat tartalmazó fájl használatával hozhatja létre. Ha a felhasználói felületet használja a kulcstartó-hozzáférési csoport létrehozásához, kövesse az alábbi lépéseket:

     a. Ha a Mobile alkalmazás nem rendelkezik definiált kulcstartó-hozzáférési csoportokkal, adja hozzá az alkalmazás köteg-AZONOSÍTÓját az **első** csoporthoz.
    
    b. Húzza a `com.microsoft.intune.mam` megosztott kulcslánccsoportot a meglévő hozzáférési csoportokhoz. Ez a hozzáférési csoport az Intune App SDK-adatok tárolására szolgál.
    
    c. Vegye fel a `com.microsoft.adalcache` csoportot a meglévő hozzáférési csoportokba.
    
      ![Intune App SDK (iOS) – kulcsláncok megosztása](./media/intune-app-sdk-ios-keychain-sharing.png)
    
    d. Ha a jogosultságokat tartalmazó fájlt közvetlenül szerkeszti, ahelyett hogy a korábban bemutatott Xcode felhasználói felületet használná a kulcslánc-hozzáférési csoportok létrehozásához, fűzze a `$(AppIdentifierPrefix)` előtagot a kulcslánc hozzáférési csoportokhoz (az Xcode ezt automatikusan megteszi). Példa:
    
      - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
      - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
      > [!NOTE]
      > A jogosultságokat tartalmazó fájl egy XML-fájl, amely minden mobilalkalmazásnál egyedi. és speciális engedélyek és képességek meghatározására szolgál az iOS-alkalmazásban. Ha az alkalmazása eddig nem rendelkezett jogosultságokat tartalmazó fájllal, a kulcsláncmegosztás engedélyezésekor (3. lépés) az Xcode generál egyet. Győződjön meg arról, hogy az alkalmazás köteg-azonosítója a lista első bejegyzése.

5. Az alkalmazáshoz tartozó Info.plist fájl `LSApplicationQueriesSchemes` tömbjében tüntessen fel minden protokollt, amelyet az alkalmazás átad az `UIApplication canOpenURL` számára. Ne felejtse el menteni a módosításokat, mielőtt folytatná a következő lépéssel.

6. Ha az alkalmazás még nem használ FaceID-t, győződjön meg róla, hogy az [NSFaceIDUsageDescription Info.plist kulcs](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75) az alapértelmezett üzenettel van konfigurálva. Ez kötelező, mivel az iOS így tudata a felhasználóval, hogy az alkalmazás hogyan használja a FaceID-t. A FaceID egy Intune App Protection szabályzatbeállítással alkalmazás-hozzáférési módként használható, ha ezt a rendszergazda konfigurálta.

7. Fejezze be az alkalmazás Info.plist fájljának konfigurálását az [SDK adattárában](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) található IntuneMAMConfigurator eszközzel. Az eszköz három paraméterrel rendelkezik:

   |Tulajdonság|Használat|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  Választható`<Path to the output plist>` |

Ha nem adja meg az „-o” paramétert, a bemeneti fájl helyben lesz módosítva. Az eszköz idempotens, és az Info.plist fájl vagy a jogosultságok változása esetén újra kell futtatnia. Emellett ha frissíti az Intune SDK-t, javasoljuk, hogy töltse le és futtassa az eszköz legújabb verzióját, mert elképzelhető, hogy megváltoztak az Info.plist fájl konfigurációs követelményei a legújabb kiadásban.

## <a name="configure-adalmsal"></a>ADAL/MSAL konfigurálása

Az Intune app SDK a hitelesítési és feltételes indítási forgatókönyvekhez használhatja a [Azure Active Directory hitelesítési függvénytárat](https://github.com/AzureAD/azure-activedirectory-library-for-objc) vagy a [Microsoft hitelesítési függvénytárát](https://github.com/AzureAD/microsoft-authentication-library-for-objc) . Emellett a ADAL/MSAL-ra is támaszkodik, hogy regisztrálja a felhasználói identitást a MAM szolgáltatásban eszközök regisztrálási forgatókönyvek nélkül történő felügyeletéhez.

A ADAL/MSAL általában az alkalmazások regisztrálását igénylik Azure Active Directory (HRE), és egyedi ügyfél-azonosítót és átirányítási URI-t kell létrehoznia az alkalmazás számára biztosított jogkivonatok biztonságának garantálása érdekében. Ha az alkalmazás már használja a ADAL vagy a MSAL a felhasználók hitelesítéséhez, az alkalmazásnak a meglévő regisztrációs értékeit kell használnia, és felül kell bírálnia az Intune app SDK alapértelmezett értékeit. Ez biztosítja azt, hogy a felhasználóknak ne kelljen kétszer hitelesíteniük magukat (egyszer az Intune App SDK felé, egyszer pedig az alkalmazás felé).

Ha az alkalmazás még nem használja a ADAL vagy a MSAL-t, és nincs szüksége a HRE-erőforrásokhoz való hozzáférésre, nem kell beállítania ügyfélalkalmazás-regisztrációt a HRE, ha a ADAL integrálását választja. Ha úgy dönt, hogy integrálja a MSAL-t, konfigurálnia kell egy alkalmazás regisztrációját, és felül kell bírálnia az Intune-ügyfél alapértelmezett AZONOSÍTÓját és átirányítási URI-JÁT  

Javasoljuk, hogy az alkalmazás a [ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) vagy a [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases)legújabb verziójára mutasson.

### <a name="link-to-adal-or-msal-binaries"></a>Hivatkozás ADAL vagy MSAL bináris fájlokra

**1. lehetőség –** Az [alábbi lépéseket](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) követve összekapcsolhatja az alkalmazást a ADAL bináris fájljaival.

**2. lehetőség –** Azt is megteheti, hogy [ezeket az utasításokat](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation) követve összekapcsolja az alkalmazást a MSAL bináris fájljaival.

1. Ha az alkalmazás nem határozott meg kulcslánc-hozzáférési csoportokat, hozza létre az első csoportot az alkalmazás csomagazonosítójának felvételével.

2. Engedélyezze a ADAL/MSAL egyszeri bejelentkezést (SSO) a kulcstartó `com.microsoft.adalcache` -hozzáférési csoportok hozzáadásával.

3. Ha explicit módon beállítja az ADAL megosztott gyorsítótárának kulcslánccsoportját, akkor feltétlenül a következő értékre állítsa: `<appidprefix>.com.microsoft.adalcache`. Az ADAL ezt állítja be, hacsak Ön felül nem bírálja. Ha egyéni kulcslánccsoportot szeretne megadni a `com.microsoft.adalcache` helyett az Info.plist fájl „IntuneMAMSettings” szakaszában, azt az `ADALCacheKeychainGroupOverride` kulccsal kell megadnia.

### <a name="configure-adalmsal-settings-for-the-intune-app-sdk"></a>Az Intune app SDK ADAL/MSAL beállításainak konfigurálása

Ha az alkalmazás már használja az ADAL-t vagy a MSAL-t a hitelesítéshez, és saját Azure Active Directory beállításai vannak, akkor kényszerítheti az Intune app SDK-t, hogy ugyanazokat a beállításokat használja a HRE-alapú hitelesítés során. Ezzel biztosítható, hogy az alkalmazás ne kérje a hitelesítést kétszer is a felhasználótól. Az [Intune App SDK-beállítások konfigurálása](#configure-settings-for-the-intune-app-sdk) című témakörben tájékoztatást talál a következő beállítások értékének kitöltéséről:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Ha az alkalmazás már használja az ADAL-t vagy a MSAL-t, a következő konfigurációk szükségesek:

1. Adja meg az ADAL-hívásokhoz használandó ClientID-t a projekt Info.plist fájljában, az **IntuneMAMSettings** szótár alatt található `ADALClientId` nevű kulcsban.

2. A szintén az **IntuneMAMSettings** szótár alatt található `ADALAuthority` nevű kulcsban adja meg az Azure AD-szolgáltatót.

3. A szintén az **IntuneMAMSettings** szótár alatt található `ADALRedirectUri` nevű kulcsban adja meg az ADAL-hívásokhoz használandó átirányítási URI-t. Másik lehetőségként megadhatja az `ADALRedirectScheme` kulcsot is, ha az alkalmazás átirányítási URI-ja `scheme://bundle_id` formátumú.

Az alkalmazások felülbírálhatják ezeket az Azure AD-beállításokat futtatáskor. Ehhez egyszerűen állítsa be az `aadAuthorityUriOverride`, `aadClientIdOverride` és az `aadRedirectUriOverride` tulajdonságot az `IntuneMAMPolicyManager` példányon.

4. Győződjön meg arról, hogy az iOS-alkalmazás engedélyeit az App Protection-szabályzat (APP) szolgáltatáshoz adja meg. Az [első lépések az INTUNE SDK-útmutatóban](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) című témakör útmutatását követve[adja meg az alkalmazás hozzáférését az Intune app Protection szolgáltatáshoz (nem kötelező)](https://docs.microsoft.com/intune/app-sdk-get-started#give-your-app-access-to-the-intune-app-protection-service-optional).  

> [!NOTE]
> Az Info.plist fájl használatát javasoljuk az összes olyan beállításhoz, amely statikus, és nem igényel futtatáskori meghatározást. Az `IntuneMAMPolicyManager`-tulajdonságokhoz rendelt értékek elsőbbséget élveznek az Info.plist fájlban megadott hasonló értékekkel szemben, és még az alkalmazás újraindítása után is megmaradnak. Az SDK továbbra is használni fogja ezeket szabályzat-ellenőrzéshez egészen a felhasználó regisztrációjának törléséig, vagy addig, amíg nem módosítja vagy törli az értékeket.

### <a name="if-your-app-does-not-use-adal-or-msal"></a>Ha az alkalmazás nem használja a ADAL vagy a MSAL

Ahogy korábban említettük, az Intune app SDK a hitelesítési és feltételes indítási forgatókönyvekhez használhatja a [Azure Active Directory hitelesítési függvénytárat](https://github.com/AzureAD/azure-activedirectory-library-for-objc) vagy a [Microsoft hitelesítési függvénytárát](https://github.com/AzureAD/microsoft-authentication-library-for-objc) . Emellett a ADAL/MSAL-ra is támaszkodik, hogy regisztrálja a felhasználói identitást a MAM szolgáltatásban eszközök regisztrálási forgatókönyvek nélkül történő felügyeletéhez. Ha **az alkalmazás nem használja a ADAL vagy a MSAL a saját hitelesítési mechanizmusához**, akkor előfordulhat, hogy egyéni HRE-beállításokat kell konfigurálnia attól függően, hogy melyik hitelesítési függvénytárat szeretné integrálni:   

ADAL – az Intune app SDK alapértelmezett értékeket biztosít a ADAL paraméterekhez, és kezeli az Azure AD-vel való hitelesítést. A fejlesztőknek nem kell megadniuk a korábban említett ADAL-beállítások értékeit. 

MSAL – a fejlesztőknek létre kell hozniuk egy alkalmazás regisztrációját a HRE-ben egy egyéni átirányítási URI-val az [itt](https://github.com/AzureAD/microsoft-authentication-library-for-objc/wiki/Migrating-from-ADAL-Objective-C-to-MSAL-Objective-C#app-registration-migration)megadott formátumban. A fejlesztőknek be `ADALClientID` kell `ADALRedirectUri` állítania a korábban említett és a beállításokat `aadClientIdOverride` , `aadRedirectUriOverride` vagy a `IntuneMAMPolicyManager` példányon a megfelelő és a tulajdonságokat. A fejlesztőknek azt is biztosítaniuk kell, hogy az előző szakaszban 4. lépéssel megadják az alkalmazás regisztrációs hozzáférését az Intune app Protection szolgáltatáshoz.

### <a name="special-considerations-when-using-msal"></a>A MSAL használata során felmerülő különleges szempontok 

1. **Tekintse meg a webnézetet** – ajánlott, hogy az alkalmazások ne használják a SFSafariViewController, a SFAuthSession vagy a ASWebAuthSession webnézetként bármely, az alkalmazás által kezdeményezett MSAL interaktív hitelesítési művelethez. Ha valamilyen oknál fogva az alkalmazásnak az egyik interaktív MSAL-hitelesítési művelethez is használnia kell ezeket a webnézeteket, akkor `SafariViewControllerBlockedOverride` az `true` alkalmazás info. plist fájljában is be kell állítania a `IntuneMAMSettings` szótár alá. FIGYELMEZTETÉS Ezzel kikapcsolja az Intune SafariViewController hookokat az Auth-munkamenet engedélyezéséhez. Ez kockázatos adatszivárgást tesz lehetővé az alkalmazásban, ha az alkalmazás a SafariViewController használatával tekinti meg a vállalati adatforrásokat, így az alkalmazás nem jelenítheti meg a vállalati adattípusokat ezen webnézet-típusok közül.
2. A **ADAL és a MSAL összekapcsolása** esetén a fejlesztőknek engedélyeznie kell a lehetőséget, ha azt szeretnék, hogy az Intune előnyben részesítette a MSAL a ADAL- Alapértelmezés szerint az Intune a támogatott ADAL-verziókat részesíti előnyben a támogatott MSAL-verziókhoz, ha mindkettő a futtatókörnyezethez van csatolva. Az Intune csak a támogatott MSAL `IntuneMAMUseMSALOnNextLaunch` `true` - `NSUserDefaults`verziót részesíti előnyben, ha az Intune első hitelesítési műveletének időpontjában a (z). Ha `IntuneMAMUseMSALOnNextLaunch` a `false` értéke vagy nincs beállítva, az Intune az alapértelmezett viselkedéshez fog visszatérni. Ahogy a neve is sugallja, a `IntuneMAMUseMSALOnNextLaunch` változás a következő indításkor lép érvénybe.


## <a name="configure-settings-for-the-intune-app-sdk"></a>Az Intune App SDK-beállítások konfigurálása

Az Intune App SDK beállítását és konfigurálását az alkalmazás Info.plist fájljában található **IntuneMAMSettings** szótárral végezheti el. Ha az IntuneMAMSettings szótár nem látható az Info.plist fájlban, létre kell hoznia azt.

Az IntuneMAMSettings szótárban az alábbi támogatott beállításokkal konfigurálhatja a Intune App ADK-t.

Egy részükről már volt szó korábbi szakaszokban, más részük pedig nem vonatkozik minden alkalmazásra.

Beállítás  | Type  | Meghatározás | Kötelező?
--       |  --   |   --       |  --
ADALClientId  | Sztring  | Az alkalmazás Azure AD ügyfél-azonosítója. | Minden olyan alkalmazáshoz szükséges, amely a MSAL és bármely olyan ADAL alkalmazást használja, amely egy nem Intune-beli HRE-erőforráshoz fér hozzá. |
ADALAuthority | Sztring | Az alkalmazás használatban lévő Azure AD-szolgáltatója. Használja azt a saját környezetet, ahol az AAD-fiókok konfigurálása megtörtént. | Kötelező, ha az alkalmazás ADAL vagy MSAL használ egy nem Intune-beli HRE-erőforrás eléréséhez. Ha ez az érték hiányzik, a rendszer egy Intune-beli alapértelmezett értéket használ.|
ADALRedirectUri  | Sztring  | Az alkalmazás Azure AD átirányítási URI-ja. | ADALRedirectUri vagy ADALRedirectScheme szükséges minden olyan alkalmazáshoz, amely a MSAL-t és bármely olyan ADAL-alkalmazást használ, amely nem Intune HRE-erőforráshoz fér hozzá.  |
ADALRedirectScheme  | Sztring  | Az alkalmazás Azure AD átirányítási sémája. Használható az ADALRedirectUri helyett, ha az alkalmazás átirányítási URI-ja `scheme://bundle_id` formátumú. | ADALRedirectUri vagy ADALRedirectScheme szükséges minden olyan alkalmazáshoz, amely a MSAL-t és bármely olyan ADAL-alkalmazást használ, amely nem Intune HRE-erőforráshoz fér hozzá. |
ADALLogOverrideDisabled | Logikai  | Megadja, hogy az SDK átirányítsa-e az összes ADAL-/MSAL-naplót (beleértve az alkalmazásból származó ADAL-hívásokat is) a saját naplófájlba. Az alapértelmezett érték a Nem. Állítsa az Igen értékre, ha az alkalmazás a saját ADAL/MSAL-napló visszahívását fogja beállítani. | Nem kötelező. |
ADALCacheKeychainGroupOverride | Sztring  | Megadja a ADAL-/MSAL-gyorsítótárhoz a "com. microsoft. adalcache" helyett használandó kulcstartó csoportot. Vegye figyelembe, hogy ez nem tartalmazza az app-id előtagot. Ezt az előtagot futás közben fogja megkapni a sztring. | Nem kötelező. |
AppGroupIdentifiers | karakterláncok tömbje  | Az alkalmazáscsoportok tömbje az alkalmazás jogosultságainak com.apple.security.application-groups szakaszában. | Szükséges, ha az alkalmazás alkalmazáscsoportokat használ. |
ContainingAppBundleId | Sztring | Megadja a bővítményt tartalmazó alkalmazás csomagazonosítóját. | IOS-bővítményekhez szükséges. |
DebugSettingsEnabled| Logikai | Ha YES értékű, használhatók a Settings csomagban található tesztszabályzatok. Az alkalmazásokat *tilos* úgy szállítani, hogy engedélyezve van bennük ez a beállítás. | Nem kötelező. Az alapértelmezett érték a nem. |
MainNibFile<br>MainNibFile~ipad  | Sztring  | Ennek a beállításnak tartalmaznia kell az alkalmazás fő Nib-fájljának nevét.  | Kötelező, ha az alkalmazás a MainNibFile-t az Info.plist fájlban definiálja. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | Sztring  | Ennek a beállításnak tartalmaznia kell az alkalmazás fő storyboard-fájljának nevét. | Kötelező, ha az alkalmazás a UIMainStoryboardFile-t az Info.plist fájlban definiálja. |
AutoEnrollOnLaunch| Logikai| Megadja, hogy az alkalmazás megpróbáljon-e automatikusan regisztrálni indításkor, ha meglévő felügyelt identitást érzékel, és ha korábban még nem történt regisztráció. Az alapértelmezett érték a Nem. <br><br> Megjegyzések: Ha nem található felügyelt identitás, vagy az identitáshoz nem érhető el érvényes jogkivonat a ADAL-/MSAL-gyorsítótárban, a beléptetési kísérlet a hitelesítő adatok kérése nélkül csendesen meghiúsul, kivéve, ha az alkalmazás az Igen értékre állítja be a MAMPolicyRequired. | Nem kötelező. Az alapértelmezett érték a nem. |
MAMPolicyRequired| Logikai| Azt adja meg, hogy megakadályozza-e a rendszer az alkalmazás elindítását, ha az alkalmazásnak nincs Intune alkalmazásvédelmi szabályzata. Az alapértelmezett érték a Nem. <br><br> Megjegyzések: Az alkalmazás nem küldhető el az App Store-ba az MAMPolicyRequired beállítás Igen értékre állításával. HA a MAMPolicyRequired értéke IGEN, az AutoEnrollOnLaunch beállítását is IGEN értékre kell állítani. | Nem kötelező. Az alapértelmezett érték a nem. |
MAMPolicyWarnAbsent | Logikai| Azt adja meg, hogy figyelmeztesse-e az alkalmazás a felhasználót az indítás közben, ha az alkalmazásnak nincs Intune alkalmazásvédelmi szabályzata. <br><br> Megjegyezés: A felhasználók továbbra is használhatják az alkalmazást házirend nélkül, miután elutasította a figyelmeztetést. | Nem kötelező. Az alapértelmezett érték a nem. |
MultiIdentity | Logikai| Azt adja meg, hogy az alkalmazás képes-e kezelni a többszörös identitást. | Nem kötelező. Az alapértelmezett érték a nem. |
SafariViewControllerBlockedOverride | Logikai| Letiltja az Intune SafariViewController hookot a MSAL-hitelesítés engedélyezéséhez SFSafariViewController, SFAuthSession vagy ASWebAuthSession használatával. | Nem kötelező. Az alapértelmezett érték a nem. Figyelmeztetés: adatszivárgást eredményezhet, ha nem megfelelően használják. Csak akkor engedélyezze, ha feltétlenül szükséges. A részletekért tekintse meg a [MSAL használatakor felmerülő különleges szempontokat](#special-considerations-when-using-msal) .  |
SplashIconFile <br>SplashIconFile ~ ipad | Sztring  | Az Intune-kezdőképet (indítóképernyőt) tartalmazó ikonfájlt határozza meg. | Nem kötelező. |
SplashDuration | Szám | Az Intune-kezdőképernyő megjelenésének minimális időtartama (másodpercben) az alkalmazás indításakor. Az alapértelmezett érték 1.5. | Nem kötelező. |
BackgroundColor| Sztring| A kezdő- és a PIN-kód bevitelére szolgáló képernyő háttérszínét adja meg. Hexadecimális RGB-sztringet fogad el „#XXXXXX” alakban, amelyben az X-ek helyén számjegy (0–9), illetve és A és F közötti nagybetű állhat. A kettőskereszt jel kihagyható.   | Nem kötelező. Alapértelmezése a világosszürke szín. |
ForegroundColor| Sztring| Megadja az indítási és a PIN-kód (például a szöveg színe) képernyő előtéri színét. Hexadecimális RGB-sztringet fogad el „#XXXXXX” alakban, amelyben az X-ek helyén számjegy (0–9), illetve és A és F közötti nagybetű állhat. A kettőskereszt jel kihagyható.  | Nem kötelező. Alapértelmezett értéke a fekete. |
AccentColor | Sztring| Meghatározza a PIN-kód képernyő ékezetes színét, például a gomb szövegének színét és a mező kiemelésének színét. Hexadecimális RGB-sztringet fogad el „#XXXXXX” alakban, amelyben az X-ek helyén számjegy (0–9), illetve és A és F közötti nagybetű állhat. A kettőskereszt jel kihagyható.| Nem kötelező. Alapértéke a rendszer kék színe. |
MAMTelemetryDisabled| Logikai| Az határozható meg vele, hogy az SDK ne küldjön telemetriai adatokat a háttérrendszerének.| Nem kötelező. Az alapértelmezett érték a nem. |
MAMTelemetryUsePPE | Logikai | Itt adhatja meg, hogy a MAM SDK-t küldjön-e adatokat a PPE telemetriai háttérrendszernek. Akkor használja ezt a beállítást, ha teszteli az alkalmazásokat az Intune szabályzatával. Megakadályozhatja vele, hogy a teszt telemetriai adatai keveredjenek az ügyfelek adataival. | Nem kötelező. Az alapértelmezett érték a nem. |
MaxFileProtectionLevel | Sztring | Nem kötelező. Itt engedélyezheti az alkalmazásnak az által támogatott maximális `NSFileProtectionType` szintnek a meghatározását. Ez az érték felülbírálja a szolgáltatás által küldött szabályzatot, ha a szint magasabb, mint amit az alkalmazás támogatni képes. A lehetséges értékek: `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`.|
OpenInActionExtension | Logikai | A beállítása YES a műveleti bővítményekben való megnyitáshoz. További információért lásd az Adatok megosztása az UIActivityViewController használatával szakaszt. |
WebViewHandledURLSchemes | Sztringek tömbje | Az alkalmazás WebView-ja által kezelt URL-sémát határozza meg. | Kötelező, ha az alkalmazás olyan WebView-t használ, amely az URL-címeket hivatkozásokkal és/vagy javascripttel kezeli. |

## <a name="receive-app-protection-policy"></a>Alkalmazásvédelmi szabályzat fogadása

### <a name="overview"></a>Áttekintés

Az Intune alkalmazásvédelmi szabályzatának fogadásához az alkalmazásoknak regisztrációs kérelmet kell kezdeményezniük az Intune MAM szolgáltatásban. Az Intune konzollal konfigurálhatja az alkalmazásokat az alkalmazásvédelmi szabályzat eszközregisztrációtól független fogadására. Az **APP-WE** vagy MAM-WE néven is ismert eszközregisztráció nélküli alkalmazásvédelmi szabályzat lehetővé teszi, hogy az Intune anélkül is felügyelhesse az alkalmazásokat, hogy az eszközök az Intune mobileszköz-felügyeletre (MDM) regisztrálva lennének. Mindkét esetben szükséges regisztrálni az Intune MAM szolgáltatásban a szabályzat fogadásához.

> [!Important]
> Az iOS-hez készült Intune app SDK 256 bites titkosítási kulcsokat használ, ha az adatvédelmi szabályzatok engedélyezik a titkosítást. A védett adatmegosztás engedélyezéséhez minden alkalmazásnak rendelkeznie kell egy aktuális SDK-verzióval.

### <a name="apps-that-already-use-adal-or-msal"></a>ADAL vagy MSAL már használó alkalmazások

Azok az alkalmazások, amelyek már használják a ADAL vagy `registerAndEnrollAccount` a MSAL, `IntuneMAMEnrollmentManager` a felhasználó sikeres hitelesítését követően meg kell hívni a metódust a példányon:

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

Az SDK a `registerAndEnrollAccount` metódus meghívásával regisztrálja a felhasználói fiókot, és megpróbálja regisztrálni az alkalmazást ennek a fióknak a nevében. Ha a regisztráció bármilyen okból nem sikerül, az SDK 24 óra múlva újra próbálkozik. Hibakeresési célokra az alkalmazás egy delegálton keresztül fogadhat [értesítéseket](#status-result-and-debug-notifications) a regisztrációs kérések eredményéről.

Az API meghívása után az alkalmazás a szokásos módon működhet tovább. Ha a regisztráció sikeres, az SDK értesíti a felhasználót, hogy újra kell indítani az alkalmazást. Ekkor a felhasználó azonnal újraindíthatja az alkalmazást.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal-or-msal"></a>ADAL vagy MSAL nem használó alkalmazások

Azok az alkalmazások, amelyek nem jelentkeznek be a felhasználóhoz a ADAL vagy a MSAL használatával, továbbra is fogadhatnak alkalmazás-védelmi szabályzatot az Intune MAM szolgáltatásból, ha az API-t úgy hívja meg, hogy az SDK kezelje Az alkalmazásoknak ezt a módszert kell használniuk abban az esetben, ha nem hitelesítették a felhasználót az Azure AD-vel, ugyanakkor szükség van az alkalmazásvédelmi szabályzat lekérésére az adatok védelméhez. Ilyen például, ha másik hitelesítési szolgáltatást használ az alkalmazásba való bejelentkezésre, vagy ha az alkalmazás egyáltalán nem támogatja a bejelentkezést. Ehhez az alkalmazás használhatja az `IntuneMAMEnrollmentManager` példány `loginAndEnrollAccount` metódusát:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

A metódus meghívása esetén az SDK hitelesítő adatok megadását kéri a felhasználótól, ha nem található meglévő token///jogkivonat. Az SDK ezután megpróbálja regisztrálni az alkalmazást az Intune MAM szolgáltatásban a megadott felhasználói fiók nevében. A metódus nil (nulla) identitással is meghívható. Ez esetben az SDK regisztrálja az eszköz meglévő felügyelt felhasználóját (az MDM esetében), vagy ha nem talál meglévő felhasználót, kéri a felhasználótól a felhasználónevet.

Ha a regisztráció sikertelen, az alkalmazásnak valamikor a jövőben újra meg kell vizsgálnia az API meghívásának lehetőségét, függően a sikertelenség részleteitől. Az alkalmazás egy delegálton keresztül fogadhat [értesítéseket](#status-result-and-debug-notifications) a regisztrációs kérések eredményéről.

Az API meghívása után az alkalmazás a szokásos módon működhet tovább. Ha a regisztráció sikeres, az SDK értesíti a felhasználót, hogy újra kell indítani az alkalmazást.

Példa:

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Indításkor az Intune kezelheti a hitelesítést és a regisztrációt

Ha azt szeretné, hogy az Intune SDK a ADAL/MSAL használatával és az alkalmazás befejezése előtt is kezeljen minden hitelesítést, és az alkalmazásnak mindig az alkalmazás-szabályzatot kell használnia `loginAndEnrollAccount` , nem szükséges az API használata. Egyszerűen megadhatja a két alábbi beállításhoz a YES értéket az alkalmazás Info.plist fájljának IntuneMAMSettings szótárában.

Beállítás  | Type  | Meghatározás |
--       |  --   |   --       |  
AutoEnrollOnLaunch| Logikai| Megadja, hogy az alkalmazás megpróbáljon-e automatikusan regisztrálni indításkor, ha meglévő felügyelt identitást érzékel, és ha korábban még nem történt regisztráció. Az alapértelmezett érték a Nem. <br><br> Megjegyezés: Ha nem található felügyelt identitás, vagy az identitáshoz nem érhető el érvényes jogkivonat a ADAL-/MSAL-gyorsítótárban, a beléptetési kísérlet a hitelesítő adatok kérése nélkül csendesen meghiúsul, kivéve, ha az alkalmazás az Igen értékre állítja be a MAMPolicyRequired. |
MAMPolicyRequired| Logikai| Azt adja meg, hogy megakadályozza-e a rendszer az alkalmazás elindítását, ha az alkalmazásnak nincs Intune alkalmazásvédelmi szabályzata. Az alapértelmezett érték a Nem. <br><br> Megjegyezés: Az alkalmazás nem küldhető el az App Store-ba az MAMPolicyRequired beállítás Igen értékre állításával. HA a MAMPolicyRequired értéke IGEN, az AutoEnrollOnLaunch beállítását is IGEN értékre kell állítani. |

Ha ezt a beállítást választja az alkalmazáshoz, akkor regisztráció után nem kell az alkalmazás újraindításával foglalkoznia.

### <a name="deregister-user-accounts"></a>Felhasználói fiókok regisztrációjának megszüntetése

Mielőtt egy felhasználó kijelentkezik az alkalmazásból, az alkalmazásnak meg kell szüntetnie a felhasználó regisztrációját az SDK-ban. Ez a következőket garantálja:

1. Nem lesznek további próbálkozások a felhasználói fiók regisztrálására.

2. Az alkalmazásvédelmi szabályzat el lesz távolítva.

3. Ha az alkalmazás szelektív törlést kezdeményez (igény szerint), akkor az összes céges adat törlődik.

A felhasználó kijelentkeztetése előtt az alkalmazásnak meg kell hívnia a következő metódust az `IntuneMAMEnrollmentManager` példányon:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Ezt a metódust még a felhasználó Azure AD-jogkivonatainak törlése előtt kell meghívni. Az SDK-nak azért van szüksége a felhasználói fiók AAD-jogkivonatára vagy -jogkivonataira, hogy a felhasználó nevében küldhessen el bizonyos kéréseket az Intune MAM szolgáltatásnak.

Ha az alkalmazás saját maga gondoskodik a felhasználó céges adatainak törléséről, akkor a `doWipe` jelző false értékre állítható. Ellenkező esetben az alkalmazás az SDK-t utasíthatja a szelektív törlés indítására. Ennek eredményeképpen létrejön egy hívás az alkalmazás szelektív törlési delegáltja felé.

Példa:

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>Állapot-, eredmény- és hibakeresési értesítések

Az alkalmazás az Intune MAM-szolgáltatásokhoz intézett kérések közül a következők esetében tudja fogadni az állapot-, eredmény- és hibakeresési értesítéseket:

* Regisztrációs kérések
* Szabályzatfrissítési kérések
* Regisztrációtörlési kérések

Az értesítéseket delegáltmetódusok adják át. Ezeket a `IntuneMAMEnrollmentDelegate.h` fájl tartalmazza:

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;
```

Ezek a delegáltmetódusok egy `IntuneMAMEnrollmentStatus` objektumot adnak vissza, amely a következő információkat tartalmazza:

* A kéréshez társított fiók identitását
* A kérés eredményét jelölő állapotkódot
* Az állapotkód leírását tartalmazó hibaüzenet-sztringet
* Egy `NSError` objektumot. Ezt az objektumot az `IntuneMAMEnrollmentStatus.h` nevű fájl definiálja a visszaadható konkrét állapotkódokkal együtt.

### <a name="sample-code"></a>Mintakód

A következők a delegáltmetódusok megvalósítására szolgálnak példákkal:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>Alkalmazás-újraindítás

Amikor egy alkalmazás először kap MAM-szabályzatokat, újra kell indulnia a szükséges beavatkozási pontok alkalmazása érdekében. Az SDK biztosít egy delegáltmetódust az `IntuneMAMPolicyDelegate.h` fájlban, amellyel értesíteni lehet az alkalmazást az újraindítás szükségességéről.

```objc
 - (BOOL) restartApplication
```

A metódus visszatérési értéke közli az SDK-val, hogy az alkalmazásnak kell-e kezelni a szükséges újraindítást:

* Ha a visszatérési érték true (igaz), akkor az alkalmazásnak kell kezelnie az újraindítást.

* Ha a visszatérési érték false, akkor az SDK fogja újraindítani az alkalmazást a metódus visszatérése után. Az SDK azonnal megjelenít egy párbeszédpanelt, amely arra kéri a felhasználót, hogy indítsa újra az alkalmazást.

## <a name="customize-your-apps-behavior-with-apis"></a>Az alkalmazás viselkedésének testreszabása API-kkal

Az Intune App SDK több olyan API-val rendelkezik, amelyeket meg lehet hívni az alkalmazáshoz telepített Intune APP-szabályzat információinak beolvasásához. Ezekkel az adatokkal testre lehet szabni az alkalmazás viselkedését. Az alábbi táblázat néhány, a használatban lévő Intune-osztályról tartalmaz információkat.

Osztály | Leírás
----- | -----------
IntuneMAMPolicyManager.h | Az IntuneMAMPolicyManager osztály közzé teszi az alkalmazáshoz telepített Intune APP-szabályzatot. Olyan API-kat tesz közzé, amelyek hasznosak lehetnek [több identitás engedélyezésekor](app-sdk-ios.md#enable-multi-identity-optional). |
IntuneMAMPolicy.h | Az IntuneMAMPolicy osztály közzétesz néhány, az alkalmazásra vonatkozó MAM-szabályzatbeállítást. Ezeknek a szabályzatbeállításoknak a közzététele azért történt, hogy az alkalmazás testre szabhassa a felhasználói felületét. A legtöbb szabályzatbeállítást az SDK kényszeríti, nem az alkalmazás. Az alkalmazás által implementálandó egyetlen beállítás a Mentés másként vezérlő. Ez az osztály közzétesz néhány, a Mentés másként vezérlő végrehajtásához szükséges API-t. |
IntuneMAMFileProtectionManager.h | Az IntuneMAMFileProtectionManager osztály olyan API-kat tesz közzé, amelyeket az alkalmazás fájlok és könyvtárak védelmére használhat a megadott identitás alapján. Az identitást kezelheti az Intune, vagy lehet nem felügyelt, és az SDK alkalmazza a megfelelő MAM-szabályzatot. Ennek az osztálynak a használata nem kötelező. |
IntuneMAMDataProtectionManager.h | A IntuneMAMDataProtectionManager osztály olyan API-kat tesz közzé, amelyeket az alkalmazás használhat adatpufferek védelmére a megadott identitás alapján. Az identitást kezelheti az Intune, vagy lehet nem felügyelt, és az SDK ennek megfelelően alkalmazza a titkosítást. |

## <a name="implement-save-as-controls"></a>A Mentés másként vezérlőinek implementálása

Az Intune lehetővé teszi a rendszergazdák számára a felügyelt alkalmazások adatmentéshez használható tárolási helyeinek meghatározását. Az alkalmazások lekérhetik az engedélyezett tárolási helyek listáját az Intune App SDK-tól az `IntuneMAMPolicy.h` fájlban meghatározott `isSaveToAllowedForLocation` API használatával.

Mielőtt az alkalmazások felügyelt adatokat menthetnének felhőbeli tárhelyre vagy helyi adattárolókba, az `isSaveToAllowedForLocation` API használatával ellenőriznie kell, hogy a rendszergazda engedélyezte-e az adatmentést az adott helyre.

Az alkalmazásoknak az `isSaveToAllowedForLocation` API használatakor át kell adniuk a tárolási hely UPN-jét, amennyiben az elérhető.

### <a name="supported-save-locations"></a>Támogatott mentési helyek

Az `isSaveToAllowedForLocation` API által biztosított állandókkal ellenőrizhető, hogy a rendszergazda engedélyezi-e az adatok mentését az `IntuneMAMPolicy.h` fájlban meghatározott alábbi helyekre:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Az alkalmazásoknak az `isSaveToAllowedForLocation` állandóival kell ellenőrizniük, hogy az adatok menthetők-e „felügyeltnek” tekintett, például a OneDrive Vállalati verziójába, vagy „személyes” helyekre. Emellett akkor is szükséges az API használata, ha az alkalmazás nem képes megállapítani egy adott helyről, hogy az „felügyelt” vagy „személyes”.

A „személyes” helyeket az `IntuneMAMSaveLocationOther` állandó képviseli.

Az `IntuneMAMSaveLocationLocalDrive` állandót akkor érdemes használni, amikor az alkalmazás a helyi eszközre ment adatot.

## <a name="share-data-via-uiactivityviewcontroller"></a>Adatok megosztása az UIActivityViewController használatával

A 8.0.2 kiadásától kezdődően az Intune App SDK képes szűrni az `UIActivityViewController`-műveleteket, hogy csak az Intune által kezelt megosztott helyek legyenek kijelölhetők. Ezt a működést az alkalmazás adatátviteli szabályzata fogja szabályozni.

### <a name="copy-to-actions"></a>„Másolás ide” műveletek

Dokumentumoknak az `UIActivityViewController` és az `UIDocumentInteractionController` általi megosztásakor az iOS másolási műveletet jelenít meg a megosztott dokumentum megnyitását támogató alkalmazások mindegyike mellett. Az alkalmazások az Info.plist fájljukban lévő `CFBundleDocumentTypes` beállításban közlik a támogatott dokumentumok típusát. Ez a megosztástípus többé nem lesz elérhető, ha a szabályzat tiltja a nem felügyelt alkalmazásokkal való megosztást. Helyette a felhasználónak egy felhasználói felület nélküli műveleti bővítményt kell hozzáadnia az alkalmazásokhoz, amely az Intune APP SDK-ra hivatkozik. A műveleti bővítmény mindössze egy kódcsonk. A fájlmegosztó viselkedést az SDK implementálja. Kövesse az alábbi lépéseket:

1. Az alkalmazás Info.plist fájljában a `CFBundleURLTypes` alatt szerepelnie kell legalább egy schemeURL-definíciónak.

2. Az alkalmazásnak és a műveleti bővítménynek benne kell lennie legalább egy közös alkalmazáscsoportban, az alkalmazáscsoportnak pedig szerepelnie kell az `AppGroupIdentifiers` tömbben az alkalmazás és bővítmény IntuneMAMSettings katalógusaiban.

3. A műveleti bővítmény neveként adja meg a „Megnyitás a következőben:” szöveget az alkalmazás nevével kiegészítve. Szükség esetén az Info.plist fájl honosítható.

4. Adjon meg egy sablonikont a bővítményhez az [Apple fejlesztői dokumentációjában](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/) leírt módon. Ezek a képek az IntuneMAMConfigurator eszközzel is generálhatók az alkalmazás .app mappájából. Ehhez futtassa a következőt:

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. A bővítmény Info.plist fájljában az IntuneMAMSettings alatt adjon meg egy logikai típusú beállítást, melynek neve `OpenInActionExtension`, értéke pedig YES.

6. Konfigurálja az `NSExtensionActivationRule` szabályt, hogy támogasson egyetlen fájlt és az alkalmazás `CFBundleDocumentTypes` tulajdonságának minden típusát, amely `com.microsoft.intune.mam` előtaggal rendelkezik. Ha az alkalmazás például a public.text és public.image típusokat támogatja, akkor az aktiválási szabály a következő lesz:

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>Meglévő megosztási és műveleti bővítmények frissítése

Ha az alkalmazás már tartalmaz megosztási vagy műveleti bővítményeket, akkor az Intune-típusok engedélyezéséhez módosítani kell azok `NSExtensionActivationRule` beállítását. Minden kiterjesztéssel megadott támogatott típushoz új típust kell megadni a `com.microsoft.intune.mam` előtaggal. Ha a meglévő aktiválási szabály például a következő:  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

Akkor az alábbi módon kell módosítani:

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> Az Intune-típusok a IntuneMAMConfigurator-eszköz használatával adhatók az aktiválási szabályhoz. Ha a meglévő aktiválási szabály előre definiált sztringkonstansokat használ (például NSExtensionActivationSupportsFileWithMaxCount, NSExtensionActivationSupportsText stb.), akkor a predikátumok szintaxisa nagyon bonyolulttá válhat. Az IntuneMAMConfigurator-eszköz arra is felhasználható, hogy az aktiválási szabályt sztringkonstansokból predikátumsztringgé alakítsa az Intune-típusok hozzáadása során.

### <a name="what-the-ui-should-look-like"></a>Hogyan kell kinéznie a felhasználói felületnek?

Régi felhasználói felület:

![Adatmegosztás – az iOS régi megosztási felhasználói felülete](./media/sharing-UI-old.png)

Új felhasználói felület:

![Adatmegosztás – iOS új megosztási felhasználói felület](./media/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>Célzott konfiguráció (APP/MAM-alkalmazáskonfiguráció) engedélyezése iOS-alkalmazásokhoz

A célzott MAM-konfiguráció (másként MAM-alkalmazáskonfiguráció) lehetővé teszi, hogy az alkalmazások konfigurációs adatokat fogadjanak az Intune App SDK-ból. Ezeknek az adatoknak a formátumát és változatait az alkalmazás tulajdonosának/fejlesztőjének kell meghatároznia és kommunikálnia az Intune-ügyfelek felé.

Az Intune-rendszergazdák az Intune Azure Portalon és az Intune Graph API-val célozhatják és telepíthetik a konfigurációs adatokat. Az iOS-hez készült Intune App SDK 7.0.1-es és újabb verzióiban a célzott MAM-konfigurációban résztvevő alkalmazások a MAM szolgáltatáson keresztül kaphatják meg a célzott MAM-konfigurációs adatokat. Az alkalmazáskonfigurációs adatokat az MDM-csatorna helyett az MAM szolgáltatásán keresztül közvetlenül az alkalmazásba küldi a rendszer. Az Intune App SDK egy osztályt biztosít az ezekről a konzolokról lekért adatok eléréséhez. Az előfeltételek a következők:

* Ahhoz, hogy el lehessen érni a célzott MAM-konfigurációs felhasználói felületet, az alkalmazást regisztrálni kell az Intune MAM szolgáltatásban. További információkért lásd: [Alkalmazásvédelmi szabályzat fogadása](#receive-app-protection-policy).

* Foglalja bele az `IntuneMAMAppConfigManager.h` kódot az alkalmazás forrásfájljába.

* Az alkalmazás konfigurációs objektumának beszerzéséhez hívja az `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` funkciót.

* Hívja a megfelelő szelektort az `IntuneMAMAppConfig` objektumon. Ha például az alkalmazás kulcsa egy sztring, akkor használhatja a `stringValueForKey` vagy az `allStringsForKey` lehetőséget. A visszatérési értékek és a hibaállapotok részletes leírását lásd: `IntuneMAMAppConfig.h`.

További információ a Graph API funkcióiról: [Graph API-segédlet](https://developer.microsoft.com/graph/docs/concepts/overview).

A célzott MAM-alkalmazáskonfigurációs szabályzat iOS rendszerben való létrehozásáról lásd [A Microsoft Intune alkalmazáskonfigurációs szabályzatainak használata iOS rendszerben](https://docs.microsoft.com/intune/app-configuration-policies-use-ios) célzott MAM-alkalmazáskonfigurációról szóló szakaszát.

## <a name="telemetry"></a>Telemetria

Az iOS-hez készült Intune App SDK alapértelmezés szerint a következő eseménytípusokkal kapcsolatos telemetriai adatokat naplózza:

* **Alkalmazás elindítása**: Microsoft Intune a MAM-kompatibilis alkalmazások felügyeleti típussal való használatának megismeréséhez (MAM MDM-mel, MAM MDM-regisztráció nélkül stb.).

* **Beléptetési hívások**: Ha segítségre van Microsoft Intune a sikerességi arányról és az ügyfél oldaláról indított beléptetési hívások egyéb teljesítmény-metrikáinak megismeréséhez.

* **Intune-műveletek**: A problémák diagnosztizálásához és az Intune működőképességének biztosításához adatokat gyűjtünk az Intune SDK-műveletekről.

> [!NOTE]
> Ha nem kíván az Intune App SDK-ból származó telemetriai adatokat küldeni a Microsoft Intune-nak a mobilalkalmazásból, le kell tiltania az Intune App SDK-ban a telemetriai adatok rögzítését. Ehhez állítsa a `MAMTelemetryDisabled` tulajdonságot YES értékre az IntuneMAMSettings szótárban.

## <a name="enable-multi-identity-optional"></a>A többszörös identitás engedélyezése (nem kötelező)

Az SDK alapértelmezés szerint az alkalmazás egészére alkalmazza a szabályzatot. A MAM többszörös identitás szolgáltatásával engedélyezhető a szabályzatok identitásszintű alkalmazása. Ebből az alkalmazásnak nagyobb részt kell vállalnia, mint a MAM többi funkciójából.

Az alkalmazásnak tájékoztatnia kell az App SDK-t, ha módosítani kívánja az aktív identitást. Az SDK szintén értesíti az alkalmazást, ha identitásváltás szükséges. Jelenleg csak egy felügyelt identitás támogatott. Ha a felhasználó már regisztrálta az eszközt vagy az alkalmazást, az SDK ezt az identitást használja, és ezt tekinti az elsődleges felügyelt identitásnak. Az alkalmazás többi felhasználójával nem felügyeltként bánik, szabályzatbeállításaik korlátlanok.

Felhívjuk, hogy az identitás egyszerűen egy sztringként van definiálva. Az identitás karakterláncában a kis- és nagybetűk nincsenek megkülönböztetve. Az SDK nem feltétlenül olyan kis- és nagybetűkkel adja vissza a tőle kért identitásokat, mint ahogyan az az identitás beállításakor eredetileg meg volt adva.

### <a name="identity-overview"></a>Az identitások áttekintése

Az identitás egyszerűen egy fiók felhasználóneve (például user@contoso.com). A fejlesztők a következő szinteken állíthatják be az alkalmazás identitását:

* **Folyamat identitása**: A teljes folyamatra vonatkozó identitást állítja be, és főleg egyetlen identitást használó alkalmazásokhoz használatos. Ez az identitás hatással van minden műveletre, fájlra és a kezelőfelületre is.

* **Felhasználói felület identitása**: Meghatározza, hogy a fő szálon milyen szabályzatok vannak alkalmazva a felhasználói felületi feladatokhoz, például kivágási/másolási/beillesztési, PIN-kód, hitelesítés és adatmegosztás. A kezelőfelület identitása nincs hatással a fájlműveletekre, például a titkosításra vagy a biztonsági mentésre.

* **Szál identitása**: Befolyásolja, hogy milyen szabályzatok érvényesek az aktuális szálra. Ez az identitás hatással van minden műveletre, fájlra és a kezelőfelületre is.

Az identitás helyes beállítása az alkalmazás feladata, függetlenül attól, hogy felügyelt felhasználóról van-e szó vagy sem.

Minden szálnak minden pillanatban van egy effektív identitása mind a kezelőfelületi műveletekre, mind a fájlműveletekre vonatkozóan. A rendszer ennek az identitásnak az alapján határozza meg, hogy kell-e alkalmazni szabályzatokat, és ha igen, milyeneket. Ha az identitás „no identity”, vagy ha nem felügyelt felhasználóról van szó, a rendszer nem alkalmaz szabályzatokat. Az alábbi ábrán látható, hogy a rendszer miként határozza meg a tényleges identitásokat.

  ![Intune app SDK (iOS): Identitás-meghatározási folyamat](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>Szálak várólistái

Az alkalmazások gyakran indítanak aszinkron és szinkron feladatokat a szálak várólistáinak. Az SDK elfogja a Grand Central Dispatch (GCD) típusú hívásokat, és az aktuális szál identitását társítja az indított hívásokhoz. A feladatok befejezésekor az SDK átmenetileg módosítja a szál identitását a feladathoz társított identitásra, befejezi a feladatokat, majd visszaállítja a szál eredeti identitását.


Tekintettel arra, hogy az `NSOperationQueue` a GCD-re épül, az `NSOperations` műveletek azzal az identitással futnak, amely a szál identitása volt az adott művelet `NSOperationQueue` várólistába való felvételekor. Az `NSOperations` műveletek és a GCD segítségével közvetlenül indított függvények módosíthatják is a szál aktuális identitását, amikor futnak. Ez az identitás felülbírálja az indító száltól örökölt identitást.

### <a name="file-owner"></a>A fájl tulajdonosa

Az SDK nyilvántartja a helyi fájltulajdonosok identitását, és annak megfelelően alkalmazza a szabályzatokat. A rendszer a fájlhoz a létrehozásakor vagy csonkolási módban való megnyitásakor rendeli hozzá a tulajdonost. A rendszer tulajdonosként a műveletet végrehajtó szál effektív fájlműveleti identitását állítja be.

Az alkalmazások explicit módon is megadhatják a fájl tulajdonosát az `IntuneMAMFilePolicyManager` segítségével. Az alkalmazások az `IntuneMAMFilePolicyManager` segítségével kérhetik le a fájl tulajdonosát, és állíthatják be a kezelőfelület identitását a fájl tartalmának megjelenítése előtt.

### <a name="shared-data"></a>Megosztott adatok

Ha az alkalmazás olyan fájlokat hoz létre, amelyek felügyelt és nem felügyelt felhasználóktól származó adatokat is tartalmaznak, akkor az alkalmazás felelős a felügyelt felhasználó adatainak titkosításáért. Az adatokat a `protect` és az `unprotect` API-k segítségével titkosíthatja az `IntuneMAMDataProtectionManager` eszközben.

A `protect` metódus identitást fogad el paraméterként. Ez lehet felügyelt és nem felügyelt felhasználó is. Felügyelt felhasználó esetén titkosítja az adatokat. Nem felügyelt felhasználó esetén az identitást kódoló fejlécet ad hozzá az adatokhoz, de nem titkosítja az adatokat. A `protectionInfo` metódussal lehet bekérni az adat tulajdonosát.

### <a name="share-extensions"></a>Megosztási bővítmények

Ha az alkalmazás megosztási bővítményt tartalmaz, a megosztás alatt álló elem tulajdonosa az `IntuneMAMDataProtectionManager` `protectionInfoForItemProvider` metódusával kérhető le. Ha a megosztott elem fájl, az SDK kezeli a fájl tulajdonosának beállítását. Ha a megosztott elem adat, és az adatok fájlban lesznek tárolva, akkor az alkalmazás felelős a fájl tulajdonosának beállításáért és a `setUIPolicyIdentity` API meghívásáért, mielőtt megjelenítené az adatokat a kezelőfelületen.

### <a name="turn-on-multi-identity"></a>A többszörös identitás bekapcsolása

Alapértelmezés szerint az alkalmazások egyszeres identitásnak minősülnek. Az SDK a folyamat identitását a regisztrált felhasználóhoz állítja be. A többszörös identitás támogatás engedélyezéséhez a `MultiIdentity` nevű és YES értékű beállítást kell felvenni az alkalmazás Info.plist fájljába, az IntuneMAMSettings szótárba.

> [!NOTE]
> Ha engedélyezve van a többszörös identitás, a folyamat identitása, a kezelőfelület identitása és a szálak identitása nil lesz. Ezek megfelelő beállítása az alkalmazás feladata.

### <a name="switch-identities"></a>Identitásváltás

* **Az alkalmazás által kezdeményezett identitásváltás**:

    A többszörös identitású alkalmazásokat az indításkor ismeretlen, nem felügyelt fiókkal futó alkalmazásnak tekinti a rendszer. A feltételes indítási felhasználói felület nem fut le, és a szabályzatokat sem foganatosítja a rendszer az alkalmazásra. Az alkalmazás feladata, hogy értesítse az SDK-t minden alkalommal, amikor módosítani kell az identitást. Erre általában olyankor kerül sor, amikor az alkalmazás arra készül, hogy adatokat jelenítsen meg egy bizonyos felhasználói fióknak.

    Ilyen például, amikor a felhasználó megpróbál megnyitni egy dokumentumot, egy postaládát vagy egy jegyzetfüzetlapot. Az alkalmazásnak értesítenie kell az SDK-t, mielőtt ténylegesen megnyitja a fájlt, a postaládát vagy a lapot. Ez a `IntuneMAMPolicyManager` `setUIPolicyIdentity` API-jával történik. Ezt az API-t kell meghívni attól függetlenül, hogy felügyelt vagy nem felügyelt felhasználóról van-e szó,. Ha a felhasználó felügyelt, az SDK elvégzi a feltételes indítás ellenőrzését (jailbreak-észlelés, PIN-kód, hitelesítés stb.).

    Az identitásváltás eredményét aszinkron módon, egy befejezéskezelővel adja vissza. Az alkalmazásnak egészen addig el kell halasztania a dokumentum, postaláda vagy lap megnyitását, amíg nem kap vissza sikeres eredménykódot. Ha az identitásváltás sikertelen, az alkalmazásnak vissza kell vonnia a műveletet.

* **Az SDK által kezdeményezett identitásváltás**:

    Az SDK-nak bizonyos esetekben arra kell kérnie az alkalmazást, hogy váltson át egy bizonyos identitásra. A többszörös identitású alkalmazásoknak meg kell valósítaniuk az `IntuneMAMPolicyDelegate` `identitySwitchRequired` metódusát ahhoz, hogy kezelni tudják az ilyen kérést.

    Ha ezt a metódust meghívják, és az alkalmazás képes kezelni a megadott identitásra való átváltási kérést, akkor az `IntuneMAMAddIdentityResultSuccess` értéket kell átadnia a befejezéskezelőbe. Ha az alkalmazás nem képes kezelni az identitásváltást, akkor az `IntuneMAMAddIdentityResultFailed` értéket kell átadnia a befejezéskezelőbe.

    Az alkalmazásnak nem kell meghívnia az `setUIPolicyIdentity` metódust erre a hívásra válaszul. Ha az SDK-nak arra kell megkérnie az alkalmazást, hogy egy nem felügyelt felhasználói fiókra váltson, akkor az üres sztringet adja át az `identitySwitchRequired` hívásban.

* **Szelektív törlés**:

    Az alkalmazás szelektív törlése esetén az SDK a `IntuneMAMPolicyDelegate` `wipeDataForAccount` metódusát hívja meg. Az alkalmazás felelős azért, hogy törölje a felhasználó fiókját és a hozzá kapcsolódó adatokat. Az SDK képes arra, hogy töröljön minden fájlt, amely a felhasználó tulajdonában van. Akkor teszi ezt, ha az alkalmazás a „FALSE” eredményt adja vissza a `wipeDataForAccount` hívásból.

    Vegye figyelembe, hogy a metódus meghívása egy háttérszálból történik. Az alkalmazás csak akkor adhat vissza értéket, ha a felhasználóhoz tartozó összes adat el lett távolítva (a fájlok kivételével, amennyiben az alkalmazás „FALSE” eredményt ad vissza).

## <a name="ios-best-practices"></a>Gyakorlati tanácsok iOS rendszerhez

Az alábbiakban néhány gyakorlati tanácsot kínálunk iOS-alapú fejlesztéshez:

* Az iOS fájlrendszere megkülönbözteti a kis-és nagybetűket. Ügyeljen a kis- és nagybetűk helyes használatára az olyan fájlneveknél, mint például a `libIntuneMAM.a` vagy az `IntuneMAMResources.bundle`.

* Ha az Xcode nem találja a `libIntuneMAM.a` könyvtárat, a probléma megoldásához vegye fel a könyvtár elérési útját a keresőútvonalakba.

## <a name="faqs"></a>Gyakori kérdések

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>Az összes API címezhető natív Swift vagy Objective-C és Swift együttes használatával?

Az Intune App SDK API-k csak Objective-C nyelven érhetők el, és nem támogatják a **natív** Swiftet. A Swift Objective-C-vel való együttműködésére van szükség.

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>Az alkalmazásom minden felhasználóját regisztrálni kell az APP-WE szolgáltatásban?

Nem. Valójában csak a munkahelyi vagy iskolai fiókokat kell regisztrálni az Intune App SDK-ban. Az alkalmazások feladata azt eldönteni, hogy egy fiók munkahelyi, illetve iskolai környezetben használatos-e.

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>Mi a teendő azokkal a felhasználókkal, akik már bejelentkeztek az alkalmazásba? Regisztrálni kell őket?

Az alkalmazás felelős a felhasználók regisztrálásáért a sikeres hitelesítésüket követően. Szintén az alkalmazás felelős minden olyan fiók regisztrálásáért, amely már azelőtt jelen lehetett, mielőtt az alkalmazás kiegészült az MDM nélküli MAM funkcióval.

Erre a célra az alkalmazásnak a `registeredAccounts:` metódust kell használnia. Ez a metódus egy NSDictionary értéket ad vissza, amely tartalmazza az Intune MAM szolgáltatásban regisztrált valamennyi fiókot. Ha nem szerepel a listában valamelyik, az alkalmazásban már meglévő fiók, akkor az alkalmazásnak regisztrálnia kell a `registerAndEnrollAccount:` metódussal.

### <a name="how-often-does-the-sdk-retry-enrollments"></a>Milyen gyakran próbálkozik újra az SDK a regisztrációval?

Az SDK 24 órás időközönként automatikusan újrapróbálkozik minden korábban sikertelen regisztrációval. Az SDK azért teszi ezt, hogy ha egy felhasználó szervezete azután aktiválta a MAM szolgáltatást, hogy a felhasználó bejelentkezett az alkalmazásba, a felhasználó akkor is sikeresen regisztráljon, és megkapja a szabályzatokat.

Az SDK felhagy az újrapróbálkozással, ha azt észleli, hogy a felhasználó sikeresen regisztrálta az alkalmazást. Ez azért van így, mert egy adott időpontban csak egy felhasználó regisztrálhat egy alkalmazást. A felhasználó regisztrációjának visszavonása esetén újrakezdődnek az ismételt próbálkozások, ugyanolyan 24 órás időközzel.

### <a name="why-does-the-user-need-to-be-deregistered"></a>Miért kell megszüntetni a felhasználó regisztrációját?

Az SDK a következő műveleteket végzi el a háttérben, rendszeres időközönként:

* Ha az alkalmazás még nincs regisztrálva, 24 óránként megpróbál regisztrálni minden regisztrált fiókot.
* Ha az alkalmazás regisztrálva van, az SDK 8 óránként keresi meg a MAM-szabályzat esetleges frissítéseit.

A felhasználó regisztrációjának megszüntetése esetén értesíti az SDK-t arról, hogy a felhasználó nem használja tovább az alkalmazást, és hogy az SDK leállíthatja az adott felhasználói fiók esetében a rendszeres műveleteket. Az alkalmazás regisztrációjának visszavonását, és ha szükséges, az adatok szelektív törlését is kezdeményezi.

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>True-ra állítsam a doWipe jelzőt a regisztrációt megszüntető metódusban?

Ezt a metódust még azelőtt kell meghívni, hogy a felhasználót kijelentkezteti az alkalmazásból.  Ha a kijelentkezés keretében törli a felhasználó adatait az alkalmazásból, akkor a `doWipe` jelző false-ra állítható. Ha viszont az alkalmazás nem törli a felhasználó adatait, akkor a `doWipe` jelzőt true-ra kell állítani, hogy az SDK törölhesse az adatokat.

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>Vannak más módszerek az alkalmazások regisztrációjának megszüntetésére?

Igen, a rendszergazda szelektív törlési parancsot is küldhet az alkalmazásnak. Ezzel megszünteti és törli a felhasználó regisztrációját, és törli a felhasználó adatait is. Az SDK automatikusan kezeli ezt a helyzetet, és a regisztrációt megszüntető delegáltmetóduson keresztül küld értesítést.

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>Van olyan mintaalkalmazást, amely bemutatja, hogyan kell integrálni az SDK-t?

Igen! A Microsoft nemrégiben átalakította a nyílt forráskódú mintaalkalmazást, a [Wagr for iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App) alkalmazást. A Wagr most már engedélyezve van az alkalmazásvédelmi szabályzathoz az Intune App SDK használatával.

### <a name="how-can-i-troubleshoot-my-app"></a>Hogyan tudom elhárítani az alkalmazást?

Az iOS rendszerhez készült Intune SDK 9.0.3 + támogatja a diagnosztikai konzol hozzáadását a Mobile alkalmazásban a házirendek és a naplózási hibák teszteléséhez. `IntuneMAMDiagnosticConsole.h`meghatározza azt `IntuneMAMDiagnosticConsole` az osztály felületet, amelyet a fejlesztők az Intune diagnosztikai konzol megjelenítésére használhatnak. Ez lehetővé teszi a végfelhasználók és a fejlesztők számára a tesztelést az Intune-naplók összegyűjtésére és megosztására az esetlegesen felmerülő problémák diagnosztizálásához. Ez az API nem kötelező a integrátorok számára.

## <a name="submit-your-app-to-the-app-store"></a>Az alkalmazás beküldése az App Store-ba

Az Intune App SDK statikus könyvtára és keretrendszere egyaránt univerzális bináris build. Ez azt jelenti, hogy az összes eszköz- és szimulátorarchitektúrához biztosítanak kódot. Az Apple elutasítja az App Store-ba beküldött alkalmazásokat, ha szimulátorkódot tartalmaznak. Ha a statikus erőforrástáron alapuló fordítást végez csak eszközön használható build elkészítésére, akkor a csatoló automatikusan törli a szimulátorkódot. Végezze el az alábbi lépéseket, amelyek segítségével garantáltan nem marad szimulátorkód az alkalmazásban, amikor feltölti azt az App Store-ba.

1. Ügyeljen rá, hogy az `IntuneMAM.framework` az asztalon legyen.

2. Futtassa a következő parancsokat:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```

    Az első parancs törli a szimulátorarchitektúrákat a keretrendszer DYLIB-fájljából. A második parancs visszamásolja a csak eszközökhöz kapcsolódó DYLIB-fájlt a keretrendszer könyvtárába.
