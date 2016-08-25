---
title: "iOS-hoz készült Microsoft Intune App SDK – fejlesztői útmutató | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: 820ec2da0554f0af383895482241be7d1c0cf305


---

# iOS-hoz készült Microsoft Intune App SDK – fejlesztői útmutató

> [!NOTE]
> Először célszerű elolvasnia az [Intune App SDK használatának első lépései](intune-app-sdk-get-started.md) útmutatót, amely bemutatja az integráció előkészítését a támogatott platformokon.* 

Az iOS-hoz készült Microsoft Intune App SDK lehetővé teszi, hogy az Intune mobilalkalmazás-felügyeleti (MAM) funkcióját beépítse iOS-alkalmazásába. Az Intune App SDK-ba integrált MAM-kompatibilis alkalmazások lehetővé teszik a rendszergazdák számára a szabályzatok érvénybe léptetését az aktívan felügyelt alkalmazásokban.

# Az SDK tartalma

Az iOS-hoz készült Intune App SDK magában foglalja a statikus könyvtárat, az erőforrásfájlokat, az API-fejléceket, a hibakeresési beállításokat tartalmazó plist-fájlt és a konfiguráló eszközt. A mobilalkalmazások tartalmazhatják az erőforrásfájlokat, és általában statikus módon csatolhatók a könyvárakhoz a szabályzatok érvénybe léptetéséhez. A speciális Intune MAM-funkciók használata API-k segítségével kényszeríthető ki.
Ez az útmutató az iOS-hoz készült Intune App SDK integrációja során használt alábbi összetevőket ismerteti:

* **`libIntuneMAM.a`**: Az Intune App SDK-könyvtár. Ha projektjéhez csatolja ezt a könyvtárat, MAM-kompatibilissé teheti mobilalkalmazásait. Ehhez útmutatást „Az alkalmazás elkészítése az Intune App SDK-val” című szakaszban talál.

* **`IntuneMAMResources.Bundle`**: Azon erőforrásokat tartalmazó forráscsomag, amelyre az SDK támaszkodik. 

* **Headers**: az Intune App SDK API-jainak elérhetővé tétele. Ha API-t használ, meg kell adnia az API-t tartalmazó fejlécfájlt. 

# Az Intune App SDK működése

Az iOS-hoz készült Intune App SDK révén minimális kódmódosítással adhat hozzá felügyeleti funkciókat az iOS-alkalmazásokhoz. A kódmódosítás mértékének csökkentésével gyorsabban dobhatja piacra, és stabilabbá teheti a mobilalkalmazást. 

Az alkalmazást a statikus könyvtárhoz kell csatolni, és az alkalmazásnak tartalmaznia kell az erőforrás-csomagot is. A MAMDebugSettings.plist fájl használata nem kötelező, segítségével a MAM-szabályzatok által felügyelt alkalmazások működését szimulálhatja anélkül, hogy Microsoft Intune-on keresztül telepítené az alkalmazást. A hibakeresési buildekben a MAMDebugSettings.plist fájlban lévő szabályzatok érvénybe léptetéséhez a fájlt az alkalmazás Dokumentumok könyvtárába kell másolni az iTunes-fájlmegosztás segítségével .

# Az alkalmazás elkészítése az Intune App SDK-val 

Kövesse az alábbi lépéseket az Intune App SDK engedélyezéséhez:

1. A következőképp kapcsolódhat a `libIntuneMAM.a` könyvtárhoz:

    Húzza a libIntuneMAM.a könyvtárat a projekthez használni kívánt elemek „Linked Frameworks and Libraries”(Csatolt keretrendszerek és könyvtárak) listájába.  

    ![Intune App SDK (iOS) - csatolt keretrendszerek és könyvtárak](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)
 
    **Megjegyzés**: ha közzétesz egy alkalmazást az App Store-ban, a hibakeresési verzió helyett használja a libIntuneMAM.a végleges verzióját. A végleges verziót a „release” (kiadás) mappában találja. A hibakeresési verzió részletes kimenettel rendelkezik, ami ideális az Intune App SDK hibáinak feltárására.

2. Vegye fel a következő iOS-keretrendszereket a projekthez (ha hiányoznak):
    * `MessageUI.framework`
    * `Security.framework`
    * `MobileCoreServices.framework`
    * `SystemConfiguration.framework`
    * `libsqlite3.dylib`
    * `libc++.dylib`
    * `ImageIO.framework`
    * `LocalAuthentication.Framework`
    * `AudioToolbox.framework`<br>

    **Megjegyzés**: ha az alkalmazást iOS7-re fejlesztették, állítsa a `LocalAuthentication.Framework` „Status" (Állapot) attribútumát „Optional" (Választható) értékre. 

    Ha a „Status" (Állapot) nincs beállítva, az alkalmazás nem indul el iOS7-en.

    **Megjegyzés**: az Xcode 7 a `.dylib` helyett már `.tbd`.

3. Húzza az `IntuneMAMResources.bundle` erőforrás-csomagot a „Copy Bundle Resources” (Erőforrás-csomagok másolása) alatti „Build Phases” (Összeállítási fázisok) elemre a projektbe való felvételhez. 

    ![Intune App SDK( iOS) – erőforrás-csomagok másolása](../media/intune-app-sdk-ios-copy-bundle-resources.png)

4. Írja be a `-force_load {PATH_TO_LIB}/libIntuneMAM.a` utasítást a következő helyek egyikére, kicserélve a `{PATH_TO_LIB}` sort az Intune App SDK elérési útjával:
    * a projekt OTHER_LDFLAGS build-konfigurációs beállítása 
    * a felhasználói felület „Other Linker Flags" (Más csatoló jelzők) területe<br>

    **Megjegyzés**: a `PATH_TO_LIB`, megkereséséhez jelölje ki a `libIntuneMAM.a` fájlt és válassza az Infó mutatása lehetőséget a Fájl menüből. Másolja és illessze be a „Hol” kérdésnél látható információt (az elérési utat) az Infó ablak Általános szakaszából.

5. Ha a mobilalkalmazás fő Nib vagy a Storyboard fájlt definiál a `info.plist`fájlban, távolítsa el a Main Storyboard vagy a Main Nib fájlmezőket. Adja meg a korábban eltávolított Storyboard- vagy Nib-értékeket egy `IntuneMAMSettings` nevű új szótárban, a következő kulcsnevekkel:
    * `MainStoryboardFile`
    * `MainStoryboardFile~ipad`
    * `MainNibFile`
    * `MainNibFile~ipad `
    
    Ha a mobilalkalmazás nem definiálja a fő Nib vagy Storyboard fájlt az `info.plist`fájlban, ezek a beállítások **nem szükségesek**. 

    **Megjegyzés**: az `info.plist` fájlt nyers formátumban megtekintve láthatja a kulcsneveket. Kattintson jobb gombbal a dokumentum törzsében bárhol, és válassza a „Show Raw Keys/Values” (Nyers kulcs/érték megjelenítése) nézetet.

6. Engedélyezze a kulcsláncmegosztást (ha még nincs engedélyezve) a projekthez használni kívánt elemeken a „Capabilities” (Képességek) lehetőségre kattintva, majd kapcsolja be a „Keychain Sharing” (kulcsláncmegosztás) csúszkát. A következő lépéshez szükséges a kulcsláncmegosztás.

    **Megjegyzés**: A telepítési profil esetében elengedhetetlen az új kulcsláncmegosztási értékek támogatása. A kulcslánc-hozzáférési csoportoknak támogatniuk kell a helyettesítő karaktert. Ezt a `.mobileprovision` fájl szövegszerkesztőben való megnyitásával ellenőrizheti, rákeresve a „keychain-access-groups"(kulcslánc-hozzáférési csoportok) kifejezésre. Itt meggyőződhet arról, hogy rendelkezik-e helyettesítő karakterrel, ilyen például a következő: 

       <key>keychain-access-groups</key>
       <array>
       <string>YOURBUNDLESEEDID.*</string>
       </array>

7. Miután engedélyezte a kulcsláncmegosztást, az alábbi lépéseket követve létrehozhat egy különálló hozzáférési csoportot, amelyen az Intune App SDK adatait tárolhatja. A kulcslánc-hozzáférési csoportokat a felhasználói felületet vagy a jogosultságokat tartalmazó fájlt használva hozhatja létre:

    A felhasználói felület használata kulcslánc-hozzáférési csoport létrehozására: 
    
    * Ha a mobilalkalmazás nem határozott meg kulcslánc-hozzáférési csoportokat, vegye fel az alkalmazás csomagazonosítóját az első csoport létrehozásához.
    * Vegye fel a com.microsoft.intune.mam. megosztott kulcslánc-csoportot. Ez a hozzáférési csoport az Intune App SDK-adatok tárolására szolgál.  
    * Húzza az `com.microsoft.adalcache` csoportot a meglévő hozzáférési csoportokhoz. 
 
    ![Intune App SDK (iOS) – kulcsláncok megosztása](../media/intune-app-sdk-ios-keychain-sharing.png)

    Ha a felhasználói felület helyett a jogosultságokat tartalmazó fájlt használja a kulcslánc-hozzáférési csoport létrehozására, az `$(AppIdentifierPrefix)` előtaggal együtt be kell illesztenie a kulcslánc-hozzáférési csoportot a jogosultságokat tartalmazó fájlba. Például: `$(AppIdentifierPrefix)com.microsoft.intune.mam` és `$(AppIdentifierPrefix)com.microsoft.adalcache`.

    **Megjegyzés**: a jogosultságokat tartalmazó fájl egy egyedi XML-fájl a mobilalkalmazásban, amely speciális engedélyeket adhat meg az iOS-alkalmazásban.

8. Az iOS 9-es vagy újabb verziójára fejlesztett mobilalkalmazásoknak tartalmazniuk kell az összes `UIApplication canOpenURL` számára átadott protokollt a mobilalkalmazás `LSApplicationQueriesSchemes` fájljának `info.plist` tömbjében. Emellett minden egyes listázott protokollhoz egy új protokollt kell felvenni az `-intunemam`. A `http-intunemam`, `https-intunemam` és `ms-outlook-intunemam` elemet is fel kell venni a tömbbe. 

9. Ha az alkalmazás az `info.plist file`határozza meg az URL-sémákat, mindegyikhez vegyen fel új sémát az `-intunemam` utótaggal együtt.

10. Ha az alkalmazás jogosultságaiban meghatározott alkalmazáscsoportok találhatók, vegye fel ezeket a csoportokat az `IntuneMAMSettings` szótárban az `AppGroupIdentitifiers` kulcs karakterlánctömbjeként.

11. A mobilalkalmazást ADAL-könyvtárhoz is kapcsolhatja. Az Objective C-hez készült ADAL-könyvtár [elérhető a Githubon](https://github.com/AzureAD/azure-activedirectory-library-for-objc).

    **Megjegyzés**: az Intune App SDK-t 2015/6/19-től az ADAL broker fiókkóddal tesztelték. Győződjön meg arról, hogy az ADAL-könyvtár legújabb/működő verziójához kapcsolódik-e.

12. Húzza az `ADALiOSBundle.bundle resource` erőforrás-csomagot a „Copy Bundle Resources” (Erőforrás-csomagok másolása) alatti „Build Phases” (Összeállítási fázisok) elemre a projektbe való felvételhez.

13. Használja a `-force_load PATH_TO_ADAL_LIBRARY` összekötő lehetőséget a könyvtárhoz kapcsolódáshoz.

    Írja be a `-force_load {PATH_TO_LIB}/libADALiOS.a` utasítást a projekt OTHER_LDFLAGS build-konfigurációs beállításába vagy az „Other Linker Flags” (Más csatoló jelzők) helyre a felhasználói felületen. A „PATH_TO_LIB”helyett adja meg az ADAL bináris helyét. 

Ha a mobilalkalmazás ADAL-t használ a saját hitelesítéshez, tekintse át az Azure Directory hitelesítési könyvtárának beállításaival foglalkozó szakaszt, amely itt található.

## Telemetria 

Az iOS-hoz készült Intune App SDK alapértelmezés szerint naplózza a használati eseményekkel kapcsolatos telemetrikus adatokat, amelyeket a rendszer elküld a Microsoft Intune-nak.

A rendszer a következő használati események adatait naplózza: 

1. Az alkalmazások indítása: a Microsoft Intune tájékozódhat a különböző felügyeleti típusú MAM-kompatibilis alkalmazások használatáról.

2. EnrollApplication API-hívás: a Microsoft Intune a sikerességi arányról és az enrollApplication ügyféloldali hívásainak egyéb teljesítménymutatóiról is gyűjt információkat.

**Megjegyzés**: ha nem kíván az Intune App SDK-ból származó telemetrikus adatokat küldeni a Microsoft Intune-nak a mobilalkalmazásról, **le kell tiltania** az Intune App SDK-ban a telemetria-rögzítést. Ehhez állítsa a `MAMTelemetryDisabled` tulajdonság értékét „Igen”-re az `IntuneMAMSettings`.

## Az Azure Directory hitelesítési könyvtár (ADAL) beállításainak konfigurálása (nem kötelező)

Az Intune App SDK az ADAL-t hitelesítésre és a feltételes indítási forgatókönyvek készítésére használja. Az ADAL használata során az alkalmazáshoz tartozó jogkivonatok biztonsága érdekében az alkalmazások használata legtöbbször regisztrációhoz, egyedi azonosítóhoz (más néven `ClientID`) és egyéb azonosítókhoz kötött. Az Intune App SDK az alapértelmezett regisztrációs értékeket használja, amikor kapcsolatba lép az Azure Active Directoryval.  Ha maga az alkalmazás használja az ADAL-t a hitelesítési forgatókönyvéhez, a meglévő regisztrációs értékeket figyelembe véve felül kell bírálnia az alapértelmezett Intune App SDK-t, hogy a felhasználókat ne kelljen kétszer hitelesíteni (egyszer az Intune App SDK-ban, és egyszer az alkalmazásban). 

Ha az alkalmazás maga használja az ADAL-t a hitelesítéshez, az alábbi lépések szükségesek. Ha a mobilalkalmazás független az ADAL-tól, nincs szükség további műveletre. 

1. A projekt `Info.plist`fájljában az `IntuneMAMSettings` szótár alatt található `ADALClientId`nevű kulcsban adja meg az ADAL-hívásokhoz használható `ClientID` -t. 

2. A projekt `Info.plist`fájljában az `IntuneMAMSettings` szótár alatt található `ADALRedirectUri`nevű kulcsban adja meg az ADAL-hívásokhoz használható átirányítási URI-t. Az alkalmazás átirányítási URI-formátumától függően előfordulhat, hogy az `ADALRedirectScheme` beállításait is meg kell adnia.

## A bővítmények összeállítása (nem kötelező) 

Ha bővítményeket állít össze, kövesse a mobilalkalmazások összeállítására vonatkozó útmutatást, amelyet „Az alkalmazás összeállítása Intune App SDK-val” című szakaszban találhat itt. Emellett frissítse az összes bővítmény info.plist fájlját, hogy felvehesse az IntuneMAMSettings szótár alatt található ContainingAppBundleId kulcsot az azt tartalmazó alkalmazás csomagazonosítójával.

## A keretrendszer összeállítása (nem kötelező)

Az Intune App SDK legújabb módosításainak köszönhetően nem kell lefordítania a mobilalkalmazást az adott csatoló jelzőkkel, ha a mobilalkalmazás beágyazott alkalmazás-keretrendszert tartalmaz. 

## Képfájlok indításkor (nem kötelező)

Ha a Microsoft Intune aktívan felügyeli a MAM-kompatibilis alkalmazásokat, az Intune App SDK az alkalmazás indításakor kezdőképernyő megjelenítésével jelzi a felhasználóknak, hogy az alkalmazás felügyelet alatt áll. A megjelenítendő képfájl(ok) felvételére „A munkahely kezeli” indítási oldalon van lehetősége. A képek esetében kövesse az alábbi iránymutatásokat:

* Vegye fel a fájlneveket a `IntuneMAMSettings` könyvtár alatt az alkalmazás info.plist fájljában a `SplashIconFile` és `SplashIconFile~ipad`. 

* A kép mérete és a követelmények

    * 180 x 180 az iPhone 6s Plus és az iPhone 6 Plus, 120 x 120 más iPhone-modellek és 152 x 152 az iPad esetében. 
    
    * Távolítsa el a `.png` kiterjesztést a fájl nevéből 
    
    * Használja a `@2x` utótagot a kétszeres méretarányú verziókhoz, és a `@3x` utótagot a képfájlok háromszoros méretarányához. Ha nem megfelelő méretűek a képek, úgy lesznek méretezve, hogy elférjenek. Ha a SplashIconFile értékek nincsenek megadva, az Intune App SDK kiválaszt egy alkalmazásikont (60 x 60 az összes iPhone, 76 x 76 az iPad esetében).

**Megjegyzés**: ez a képernyő minden indításkor megjelenik, de a felhasználó véglegesen eltávolíthatja.

# Az Intune App SDK-beállítások konfigurálása

Az alkalmazás `IntuneMAMSettings` fájljában található `info.plist` könyvtár az Intune App SDK konfigurálására szolgál. A támogatott beállítások listája a következő: 

Néhány beállításról már volt szó korábbi szakaszokban, néhány pedig nem vonatkozik minden alkalmazásra. 

Beállítás  | Típus  | Meghatározás | Kötelező?
--|--|--|--
ADALClientId  | Karakterlánc  | Az alkalmazás AAD ügyfél-azonosítója. | Szükséges, ha az alkalmazás ADAL-t használ.
ADALRedirectUri  | Karakterlánc  | Az alkalmazás AAD átirányítási URI-ja. | Szükséges, ha az alkalmazás ADAL-t használ. 
AppGroupIdentifier | A karakterlánc tömbje  | Az alkalmazáscsoportok tömbje az alkalmazás jogosultságainak com.apple.security.application-groups szakaszában. | Szükséges, ha az alkalmazás alkalmazáscsoportokat használ.
ContainingAppBundleId  | Karakterlánc | Megadja a bővítményt tartalmazó alkalmazás csomagazonosítóját. | IOS-bővítményekhez szükséges.
MainNibFile<br>MainNibFile~ipad  | Karakterlánc  | Ennek a beállításnak tartalmaznia kell az alkalmazás fő Nib-fájljának nevét.  | Szükséges, ha az alkalmazás a MainNibFile-t az info.plist-ben definiálja.
MainStoryboardFile<br>MainStoryboardFile~ipad  | Karakterlánc  | Ennek a beállításnak tartalmaznia kell az alkalmazás fő storyboard-fájljának nevét. | Szükséges, ha az alkalmazás a UIMainStoryboardFile-t az info.plist-ben definiálja.
SplashIconFile <br>SplashIconFile ~ ipad  | Karakterlánc  | Megadja az Intune-kezdőkép ikonfájlt. A „Képfájlok indításkor” témájú szakaszban talál további információt. | Nem kötelező.
SplashDuration | Szám | Az Intune kezdőképernyő megjelenésének minimális időtartama (másodpercben) az alkalmazás indításakor. Az alapértelmezett érték 1.5. | Nem kötelező.
ADALLogOverrideDisabled | Logikai  | Megadásával az SDK átirányítja az összes ADAL naplófájlt (beleértve az esetleges ADAL-hívásokat az alkalmazásból) a saját naplófájljába. Az alapértelmezett érték a Nem. Állítsa be az Igen értéket, ha az alkalmazás visszahívná a saját ADAL-naplóját. | Nem kötelező.

# Fejlécek az Intune App SDK-ban 

A következő fejlécek az API-függvényhívásokat is tartalmazzák, amelyek az Intune App SDK funkcióinak engedélyezéséhez szükségesek. 

    IntuneMAMAsyncResult.h
    IntuneMAMDataProtectionInfo.h
    IntuneMAMDataProtectionManager.h
    IntuneMAMFileProtectionInfo.h
    IntuneMAMFileProtectionManager.h
    IntuneMAMPolicyDelegate.h
    IntuneMAMLogger.h

# Intune App SDK-hibakeresés Xcode-ban

A MAM-kompatibilis alkalmazások Microsoft Intune-beli tesztelése előtt használhatja az Xcode-ban a `Settings.bundle` csomagot. Ez lehetővé teszi a tesztszabályzatok beállítását az Intune elérése nélkül. Az engedélyezéshez tegye a következőket:

* Vegye fel a `Settings.bundle` csomagot jobb gombbal kattintva a projekt legfelső mappájára. Válassza a „Hozzáadás -> Új fájl” lehetőséget a menüből. Válassza a „Források” alatt található „Settings Bundle" nevű sablont, és vegye fel.

* Ha hibakeresési buildet használ, másolja a `MAMDebugSettings.plist` fájlt a `Settings.bundle`.

* A `Root.plist` fájlban (a Settings.bundle csomagban) vegye fel előnyként a „Típust” (Child Pane) és a „Fájlnevet” ( `MAMDebugSettings`.

* A „Settings (Beállítások) > Saját-alkalmazás-neve” területen kapcsolja be az „Enable Test Policies (Tesztszabályzatok engedélyezése)" beállítást.

* Indítsa el az alkalmazást (az Xcode-on kívül vagy belül). 

* A „Settings > Saját-alkalmazás-neve -> Enable Test Policies" területen engedélyezze például a „PIN” szabályzatot.

* Indítsa el az alkalmazást (az Xcode-on kívül vagy belül). Ellenőrizze, hogy a PIN-kód megfelelően működik-e.

> [!NOTE]
> Most már használhatja a „Settings -> Saját-alkalmazás-neve -> Enable Test Policies” lehetőséget a beállítások ki- és bekapcsolására.

# Ajánlott gyakorlati tanácsok iOS-ban

Az alábbiakban néhány gyakorlati tanácsot ajánlunk az iOS-alapú fejlesztéshez:

Az iOS fájlrendszere megkülönbözteti a kis-és nagybetűket. Győződjön meg arról, hogy a megfelelő betűk szerepelnek a fájlnevekben, például a `libIntuneMAM.a` és `IntuneMAMResources.bundle`.

Ha az Xcode nem találja a `libIntuneMAM.a`könyvtárat, a problémát megoldhatja a könyvtár elérési útjának keresőútvonalakba való felvételével.




<!--HONumber=Jun16_HO4-->


