---
title: iOS-alkalmazások burkolása az Intune Alkalmazásburkoló eszközzel
description: Megtudhatja, hogyan burkolhatja az iOS-alkalmazásait anélkül, hogy módosítaná magának az alkalmazásnak a programkódját. Előkészítheti az alkalmazásokat a mobilalkalmazás-felügyeleti szabályzatok alkalmazására.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c535dbd91605a41fdc1c526ecd8ff9d9fc9e2448
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730283"
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>iOS-alkalmazások előkészítése alkalmazásvédelmi szabályzatokkal való felügyeletre az Intune alkalmazásburkoló eszközével

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

A Microsoft Intune App Wrapping Tool for iOS nevű alkalmazásburkoló eszközzel engedélyezheti az Intune alkalmazásvédelmi szabályzatait a saját fejlesztésű IOS-alkalmazásokra az alkalmazás kódjának módosítása nélkül.

Az eszköz egy macOS parancssori alkalmazás, amely „burkolót” hoz létre az alkalmazások körül. Az alkalmazások feldolgozását követően az [alkalmazásvédelmi szabályzatok](../apps/app-protection-policies.md) érvénybe léptetésével módosíthatja az alkalmazások működését.

Az eszköz letöltéséhez keresse fel a [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) weblapot a GitHubon.



## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszköz általános előfeltételei

Az alkalmazásburkoló eszköz futtatása előtt bizonyos általános előfeltételeknek kell teljesülnie:

* Töltse le a [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) eszközt a GitHubról.

* Az OS X 10.8.5-ös vagy újabb verzióját futtató macOS-számítógép, amelyen telepítve van az Xcode eszközkészlet 9-es vagy újabb verziója.

* A bemeneti iOS-alkalmazást vállalatának vagy egy független szoftverszállítónak kell létrehoznia és aláírnia.

  * A bemeneti alkalmazásfájlnak **.ipa** vagy **.app** kiterjesztésűnek kell lennie.

  * A bemeneti alkalmazást az iOS 10-es vagy újabb verziójára kell fordítani.

  * A bemeneti alkalmazás nem lehet titkosított.

  * A bemeneti alkalmazás nem rendelkezhet kiterjesztett fájlattribútumokkal.

  * A bementi alkalmazás jogosultságait az Intune alkalmazásburkoló eszköz használata előtt be kell állítani. A [jogosultságok](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html) a meglévők mellett további engedélyekkel és képességekkel ruházzák fel az alkalmazást. További utasításokért lásd az [Alkalmazásjogosultságok beállítása](#setting-app-entitlements) című részt.

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>Az App Wrapping Tool Apple Developerre vonatkozó előfeltételei

Ha burkolt alkalmazásokat kizárólag a szervezete felhasználói számára szeretne terjeszteni, szüksége lesz egy fiókra az [Apple Developer Enterprise Programban](https://developer.apple.com/programs/enterprise/), valamint az Apple Developerhez csatolt, az alkalmazás-aláíráshoz használt néhány entitásra.

Az iOS-alkalmazások szervezeten belüli felhasználók számára való terjesztésével kapcsolatban további információkat talál a hivatalos útmutatóban: [Az Apple Developer Enterprise Program alkalmazásainak terjesztése](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1).

Az Intune által burkolt alkalmazások terjesztéséhez az alábbiakra van szükség:

* Fejlesztői fiók az Apple Developer Enterprise Programban.

* Aláíró tanúsítvány belső és alkalmi terjesztéshez érvényes csoportazonosítóval.

  * Az Intune App Wrapping Tool paramétereként az aláíró tanúsítvány SHA1 kivonatát kell megadni.


* Belső terjesztési létesítési profil.

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Az Apple Developer Enterprise-fiók létrehozásának lépései
1. Keresse fel az [Apple Developer Enterprise Program webhelyét](https://developer.apple.com/programs/enterprise/).

2. Kattintson a lap jobb felső részén látható **Enroll** (Regisztráció) lehetőségre.

3. Tekintse át a regisztrációhoz szükséges feltételeket. Kattintson a lap alján látható **Start Your Enrollment** (Regisztráció indítása) lehetőségre.

4. **Jelentkezzen be** a szervezet Apple ID-jával. Ha még nem rendelkezik azonosítóval, kattintson a **Create Apple ID** (Apple ID létrehozása) gombra.

5. Válassza ki az **Entitástípust**, és kattintson a **Folytatás** gombra.

6. Töltse ki az űrlapot a szervezet adataival. Kattintson a **Folytatás**gombra. Ekkor az Apple felveszi Önnel a kapcsolatot, hogy ellenőrizze jogosultságát a szervezet regisztrálására.

8. Az ellenőrzés után kattintson az **Agree to License** (Elfogadom a licencfeltételeket) gombra.

9. A licencfeltételek elfogadása után a befejező lépés **a program megvásárlása és aktiválása**.

10. Ha Ön csoportügynök (a szervezet nevében az Apple Developer Enterprise Programba belépő személy), kezdje a csoport kiépítésével: vonjon be csoporttagokat, és rendeljen hozzájuk szerepköröket. A csoport szervezésével kapcsolatban az Apple-dokumentáció [Managing Your Developer Account Team](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1) (Fejlesztői fiók csapatának szervezése) című fejezete nyújt útmutatást.

### <a name="steps-to-create-an-apple-signing-certificate"></a>Az Apple aláíró tanúsítvány létrehozásának lépései

1. Keresse fel az [Apple fejlesztői portált](https://developer.apple.com/).

2. Kattintson a lap jobb felső részén látható **Account** (Fiók) lehetőségre.

3. **Jelentkezzen be** a szervezet Apple ID-jával.

4. Kattintson a **Certificates, IDs & Profiles** (Tanúsítványok, azonosítók és profilok) lehetőségre.

   ![Apple fejlesztői portál – tanúsítványok, azonosítók & profilok](./media/app-wrapper-prepare-ios/iOS-signing-cert-1.png)

5. Kattintson az ![Apple fejlesztői portál plusz jel](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) jelre a jobb felső sarokban iOS-tanúsítvány hozzáadásához.

6. A **Production** (Éles üzem) alatt létrehozhat **Belső és Ad Hoc** tanúsítványokat.

   ![Belső és Ad Hoc tanúsítvány kiválasztása](./media/app-wrapper-prepare-ios/iOS-signing-cert-3.png)

   >[!NOTE]
   >Ha az alkalmazást nem tervezi terjeszteni, csak belső tesztelésre szánja, akkor iOS App Development (iOS-alkalmazásfejlesztési) tanúsítványt is használhat a Production típusú helyett. Fejlesztői tanúsítvány használata esetén bizonyosodjon meg róla, hogy a mobil kiépítési profil megadja, hogy mely eszközökre fog települni az alkalmazás.

7. Kattintson a **Next** (Folytatás) gombra a lap alján.

8. Olvassa el az útmutatót a **Certificate Signing Request (CSR)** (tanúsítvány-aláírási kérelem) Keychain Access alkalmazással való létrehozásáról macOS rendszerű számítógépen.

   ![CSR létrehozásának útmutatója](./media/app-wrapper-prepare-ios/iOS-signing-cert-4.png)

9. A fenti útmutatót használva hozzon létre tanúsítvány-aláírási kérelmet. Indítsa el a macOS-számítógépen a **Keychain Access** alkalmazást.

10. A képernyő felső részén a macOS menüsorában válassza a **Keychain Access > Certificate Assistant (Tanúsítványsegéd) >  Request a Certificate From a Certificate Authority (Tanúsítvány kérése hitelesítésszolgáltatótól)** elemet.  

    ![Tanúsítvány kérése hitelesítésszolgáltatótól a Keychain Access alkalmazásban](./media/app-wrapper-prepare-ios/iOS-signing-cert-5.png)

11. CSR-fájl létrehozásához kövesse az Apple fejlesztői webhely fenti útmutatóját. A CSR-fájlt mentse el a macOS-számítógépre.

    ![Adja meg a kért tanúsítvány adatait](./media/app-wrapper-prepare-ios/iOS-signing-cert-6.png)

12. Térjen vissza az Apple fejlesztői webhelyre. Kattintson a **Folytatás** gombra. Töltse fel a CSR-fájlt.

13. Az Apple létrehozza az aláíró tanúsítványt. Töltse le, majd mentse el egy könnyen megtalálható helyre a macOS-számítógépen.

    ![Aláíró tanúsítvány letöltése](./media/app-wrapper-prepare-ios/iOS-signing-cert-7.png)

14. A tanúsítvány kulcslánchoz való hozzáadásához kattintson duplán a letöltött tanúsítványfájlra.

15. Nyissa meg újra a **Keychain Access** alkalmazást. Az ablak jobb felső részében található keresősávval keresse meg a tanúsítványt. Kattintson jobb egérgombbal a megtalált elemre a menü megjelenítéséhez, majd kattintson a **Get Info** (Információk) lehetőségre. A példaképernyőkön fejlesztési tanúsítványt használunk éles üzemi tanúsítvány helyett.

    ![Tanúsítvány hozzáadása a kulcslánchoz](./media/app-wrapper-prepare-ios/iOS-signing-cert-8.png)

16. Ekkor megjelenik egy információs ablak. Görgessen az ablak aljára, és keresse meg a **Fingerprints** (Ujjlenyomatok) címkét. Másolja ki az (itt homályosan látható) **SHA1** sztringet, és használja ezt az App Wrapping Tool -c paraméterének argumentumaként.

    ![iPhone Information – ujjlenyomatok SHA1-karakterlánca](./media/app-wrapper-prepare-ios/iOS-signing-cert-9.png)



### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>Belső terjesztési létesítési profil létrehozásának lépései

1. Látogasson vissza az [Apple fejlesztői portálra](https://developer.apple.com/account/), és **jelentkezzen be** a szervezeti Apple ID-jával.

2. Kattintson a **Certificates, IDs & Profiles** (Tanúsítványok, azonosítók és profilok) lehetőségre.

3. Kattintson az ![Apple fejlesztői portál plusz jel](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) jelre a jobb felső sarokban iOS-beli létesítési profil hozzáadásához.

4. A **Distribution** (Terjesztés) alatt létrehozhat **In House** (Belső) létesítési profilt.

   ![Belső létesítési profil kiválasztása](./media/app-wrapper-prepare-ios/iOS-provisioning-profile-1.png)

5. Kattintson a **Folytatás** gombra. Fontos, hogy az előzőekben létrehozott aláíró-tanúsítványt összekapcsolja a létesítési profillal.

6. Az útmutató alapján töltse le a profilt (.mobileprovision kiterjesztéssel) a macOS-számítógépre.

7. Mentse a fájlt egy könnyen megtalálható helyre. Ezt a fájlt kell majd használni az App Wrapping Tool -p paraméteréhez.



## <a name="download-the-app-wrapping-tool"></a>Az App Wrapping Tool letöltése

1. Töltse le az alkalmazásburkoló eszköz fájljait a [GitHubról](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) egy macOS-számítógépre.

2. Kattintson duplán a **Microsoft Intune App Wrapping Tool for iOS.dmg** fájlra. Megjelenik a végfelhasználói licencszerződés (EULA) ablaka. Figyelmesen olvassa el a dokumentumot.

3. A licencszerződés elfogadásához válassza az **Elfogadom** lehetőséget, amivel a csomagot az adott számítógéphez rendeli.

## <a name="run-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszköz futtatása

### <a name="use-terminal"></a>Terminál használata

Nyissa meg a macOS terminált, és futtassa az alábbi parancsot:

```bash
/Volumes/IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Egyes paraméterek megadása nem kötelező, amint az az alábbi táblázatban látható.

**Példa:** A következő példa parancs futtatja az alkalmazás burkoló eszközét az SajátPr. ipa nevű alkalmazásban. Meg van adva benne egy létesítési profil és az aláíró tanúsítvány SHA-1 kivonata. Ezzel írja alá az eszköz a beburkolt alkalmazást. A kimeneti alkalmazás (MyApp_Wrapped.ipa) elkészül, és a felhasználó Asztal mappájába kerül.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>Parancssori paraméterek
Az alkalmazásburkoló eszközzel a következő parancssori paraméterek használhatók:

|Tulajdonság|Használat|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. A fájlnév végződése .app vagy .ipa legyen. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**| Részletes használati információkat jelenít meg az alkalmazásburkoló eszközben elérhető parancssori tulajdonságokról. |
|**– AA**|Választható `<Authority URI of the input app if the app uses the Azure Active Directory Authentication Library>` azaz `login.windows.net/common` |
|**– AC**|Választható `<Client ID of the input app if the app uses the Azure Active Directory Authentication Library>` Ez az ügyfél-azonosító mezőben lévő GUID az alkalmazás regisztráció paneljén az alkalmazás listájában található. |
|**– AR**|Választható `<Redirect/Reply URI of the input app if the app uses the Azure Active Directory Authentication Library>` Ez az alkalmazás-regisztrációban konfigurált átirányítási URI. Általában ez az alkalmazás URL-protokollja, amelyet a Microsoft Authenticator alkalmazás a felügyelt hitelesítés után visszatérhet. |
|**-v**| (Nem kötelező) Részletes üzeneteket jelenít meg a konzolon. A hibakeresést célszerű ezzel a kapcsolóval végezni. |
|**-e**| (Nem kötelező) Ezzel a kapcsolóval utasíthatja az alkalmazásburkoló eszközt a hiányzó jogosultságok törlésére alkalmazásfeldolgozás közben. További részletek az [Alkalmazásjogosultságok beállítása](#setting-app-entitlements) című részben olvashatók.|
|**-xe**| (Nem kötelező) Információkat jelenít meg az alkalmazás iOS-bővítményeiről, továbbá arról, hogy ezek milyen jogosultságokkal használhatók. További részletek az [Alkalmazásjogosultságok beállítása](#setting-app-entitlements) című részben olvashatók. |
|**-x**| (Nem kötelező) `<An array of paths to extension provisioning profiles>`. Akkor használja, ha az alkalmazáshoz bővítménylétesítési profil szükséges.|
|**-b**|(Nem kötelező) A -b argumentumok nélküli használatával a burkolt kimeneti alkalmazás csomagverziója ugyanaz lesz, mint a bementi alkalmazásé (nem ajánlott). <br/><br/> A `-b <custom bundle version>` használatával a burkolt alkalmazás egyéni CFBundleVersion-számmal fog rendelkezni. Ha egyéni CFBundleVersion-számot szeretne megadni, célszerű a natív alkalmazás CFBundleVersion-számában a legalacsonyabb értékű tagot megnövelni, például 1.0.0 -> 1.0.1. |
|**– Citrix**|Választható Adja meg a Citrix XenMobile app SDK-t (csak a hálózatra vonatkozó változat). A beállítás használatához telepíteni kell a [CITRIX MDX eszközkészletet](https://docs.citrix.com/en-us/mdx-toolkit/about-mdx-toolkit.html) . |
|**-f**|(Nem kötelező) `<Path to a plist file specifying arguments.>` Ez a kapcsoló a [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-fájl neve előtt használandó, ha az IntuneMAMPackager többi tulajdonságát (például -i, -o és -p) a plist-sablonban adja meg. Lásd a plist használata argumentumok megadásához című részt. |

### <a name="use-a-plist-to-input-arguments"></a>Plist használata argumentumok megadásához
Az App Wrapping Tool egyszerűen futtatható úgy is, ha minden parancssori argumentumot egy [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-fájlban ad meg. A plist az XML-hez hasonló fájlformátum, amelyben űrlapon lehet megadni a parancssori argumentumokat.

Az IntuneMAMPackager/Contents/MacOS mappában nyissa meg a `Parameters.plist` nevű üres plist-sablont egy szövegszerkesztő alkalmazással vagy az Xcode-dal. Írja be az alábbi kulcsokhoz tartozó argumentumokat:

| Plist-kulcs | Type |  Alapértelmezett érték | Megjegyzések |
|------------------|-----|--------------|-----|
| Bemeneti alkalmazáscsomag elérési útja |Sztring|empty| Ugyanaz, mint az -i|
| Kimeneti alkalmazáscsomag elérési útja |Sztring|empty| Ugyanaz, mint az -o|
| Létesítési profil elérési útja |Sztring|empty| Ugyanaz, mint a -p|
| SHA-1 tanúsítvány kivonata |Sztring|empty| Ugyanaz, mint a -c|
| ADAL-szolgáltató |Sztring|empty| Ugyanaz, mint az-AA|
| ADAL-ügyfél azonosítója |Sztring|empty| Ugyanaz, mint az-AC|
| ADAL válasz URI-ja |Sztring|empty| Ugyanaz, mint az-AR|
| Részletes üzenetek engedélyezve |Logikai|false| Ugyanaz, mint a -v|
| Hiányzó jogosultságok eltávolítása |Logikai|false| Ugyanaz, mint a -c|
| Az alapértelmezett Build frissítésének tiltása |Boolen|false| Ugyanaz, mint a -b argumentumok nélkül|
| Build sztringjének felülbírálása |Sztring|empty| A burkolt kimeneti alkalmazás egyéni CFBundleVersion-száma|
| A Citrix XenMobile app SDK belefoglalása (csak hálózati változat)|Logikai|false| Ugyanaz, mint a-Citrix|
| Bővítménylétesítési profilok elérési útjai |Sztringek tömbje|empty| Az alkalmazás bővítménylétesítési profiljainak tömbje.


Futtassa az IntuneMAMPackager parancsot, egyetlen argumentumként a plist-fájlt megadva:

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>A burkolás után

A beburkolási folyamat befejezése után megjelenik egy üzenet tájékoztat a burkolás sikerességéről. Hiba esetén további segítségért lásd: [Hibaüzenetek](#error-messages-and-log-files) .

A burkolt alkalmazást a korábban megadott kimeneti mappába menti a rendszer. Most már feltöltheti az alkalmazást az Intune felügyeleti konzolra, és társíthatja egy mobilalkalmazás-felügyeleti szabályzathoz.

> [!IMPORTANT]
> A burkolt alkalmazás feltöltésénél megpróbálhat egy régebbi verziót frissíteni, ha az alkalmazás egy régebbi (burkolt vagy natív) verziója már korábban üzembe lett helyezve az Intune-ban. Hiba esetén az alkalmazást új alkalmazásként töltse fel, és törölje a korábbi verziót.

Mostantól telepítheti az alkalmazást a felhasználócsoportok számára, és alkalmazásvédelmi szabályzatokat léptethet érvénybe az alkalmazásra vonatkozóan. Az alkalmazás ezt követően a megadott alkalmazásvédelmi szabályzatoknak megfelelően fut az eszközön.

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>Milyen gyakran érdemes újraburkolni az iOS-alkalmazást az Intune alkalmazásburkoló eszközével?
Általában az alábbi esetekben van szükség az alkalmazások újraburkolására:
* Maga az alkalmazás új verzióban jelent meg. Az alkalmazás előző verziója a burkolás után az Intune-konzolba lett feltöltve.
* Az Intune iOS-hez használható alkalmazásburkoló eszközének olyan új verziója jelent meg, amely lehetővé teszi a fontosabb hibajavításokat vagy meghatározott alkalmazásvédelmi szabályzatokkal kapcsolatos Intune-funkciókat. Ilyen új verzió 6-8 hetente jelenik meg, és a [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) GitHub-tárházban érhető el.

iOS-alkalmazások esetében az alkalmazás aláírásához használt tanúsítvány- vagy létesítési profiltól eltérő profillal is burkolhatók az alkalmazások, azonban ha az alkalmazásban megadott jogosultságok nem szerepelnek az új létesítési profilban, a burkolás meghiúsul. Ha az „-e” parancssori opcióval (amely eltávolítja a hiányzó jogosultságokat az alkalmazásból) kényszeríti a sikeres burkolást az ilyen esetekben, előfordulhat, hogy az alkalmazás nem megfelelően fog működni.

Ajánlott eljárások az újraburkoláshoz:
* Győződjön meg arról, hogy egy másik létesítési profil rendelkezik minden olyan szükséges jogosultsággal, amelyekkel a korábbi létesítési profilok is rendelkeztek. 

## <a name="error-messages-and-log-files"></a>Hibaüzenetek és naplófájlok
Az alábbi információkat használva háríthatja el az alkalmazásburkoló eszközzel kapcsolatos hibákat.

### <a name="error-messages"></a>Hibaüzenetek
Ha az alkalmazásburkoló eszköz nem jár sikerrel, az alábbi hibaüzenetek valamelyike jelenik meg a konzolon:

|Hibaüzenet|További információ|
|-----------------|--------------------|
|Adjon meg egy érvényes iOS-létesítési profilt.|Előfordulhat, hogy a létesítési profil nem érvényes. Ellenőrizze, hogy rendelkezik-e megfelelő engedélyekkel az eszközökhöz, és hogy a profilja megfelelően be van-e állítva fejlesztéshez vagy terjesztéshez. A létesítési profilja esetleg le is járhatott.|
|Adjon meg egy érvényes bemeneti alkalmazásnevet.|Győződjön meg arról, hogy helyesen adta meg a bemeneti alkalmazás nevét.|
|Adjon meg érvényes elérési utat a kimeneti alkalmazáshoz.|Győződjön meg arról, hogy a kimeneti alkalmazás megadott elérési útja létezik és helyes.|
|Adjon meg egy érvényes bemeneti létesítési profilt.|Győződjön meg arról, hogy érvényes létesítésiprofil-nevet és -kiterjesztést adott meg. Előfordulhat, hogy hiányoznak jogosultságok a létesítési profiljából, vagy nem vette fel a –p parancssori kapcsolót.|
|A megadott bemeneti alkalmazás nem található. Adjon meg egy érvényes nevet és elérési utat a bemeneti alkalmazáshoz.|Győződjön meg arról, hogy a bemeneti alkalmazás elérési útja érvényes és létezik. Ellenőrizze, hogy a bemeneti alkalmazás az adott helyen található-e.|
|A megadott bemeneti létesítési profilfájl nem található. Adjon meg egy érvényes bemeneti létesítési profilfájlt.|Győződjön meg arról, hogy a bemeneti létesítési fájl elérési útja érvényes és a megadott fájl létezik.|
|A megadott kimeneti alkalmazásmappa nem található. Adjon meg érvényes elérési utat a kimeneti alkalmazáshoz.|Győződjön meg arról, hogy a megadott kimeneti elérési út érvényes és létezik.|
|A kimeneti alkalmazásnak nem **.ipa** a kiterjesztése.|Az alkalmazásburkoló eszköz csak az **.app** és az **.ipa** kiterjesztést fogadja el. Ellenőrizze, hogy a kimeneti fájl kiterjesztése érvényes-e.|
|Érvénytelen aláíró tanúsítványt adott meg. Adjon meg egy érvényes Apple aláíró tanúsítványt.|Ellenőrizze, hogy a helyes aláíró tanúsítványt töltötte-e le az Apple fejlesztői portáljáról. Lehetséges, hogy a tanúsítvány lejárt, vagy hiányzik egy publikus vagy titkos kulcs. Ha Apple-tanúsítványa és létesítési profilja használható az alkalmazások megfelelő aláírásához az Xcode-on belül, akkor érvényes az alkalmazásburkoló eszközhöz.|
|A megadott bemeneti alkalmazás érvénytelen. Adjon meg egy érvényes alkalmazást.|Győződjön meg arról, hogy .app vagy .ipa fájlként összeállított, érvényes iOS-alkalmazással rendelkezik.|
|A megadott bemeneti alkalmazás titkosítva van. Adjon meg egy érvényes titkosítatlan alkalmazást.|Az alkalmazásburkoló eszköz nem támogatja a titkosított alkalmazásokat. Adjon meg egy titkosítatlan alkalmazást.|
|A megadott bemeneti alkalmazás nem Position Independent Executable (PIE) formátumú. Adjon meg egy érvényes alkalmazást PIE formátumban.|A Position Independent Executable (PIE) formátumú alkalmazások egy véletlenszerű memóriacímre tölthetők be futtatás közben. Ez biztonsági előnyökkel járhat. A biztonsági előnyökről az Apple fejlesztői dokumentációjában talál további tájékoztatást.|
|A megadott bemeneti alkalmazás már be van burkolva. Adjon meg egy érvényes burkolatlan alkalmazást.|Az eszköz által már feldolgozott alkalmazás nem dolgozható fel. Ha ismét fel szeretne dolgozni egy alkalmazást, az alkalmazás eredeti verzióját használva futtassa az eszközt.|
|A megadott bemeneti alkalmazás nincs aláírva. Adjon meg egy érvényes aláírt alkalmazást.|Az alkalmazásburkoló eszköz megköveteli az alkalmazások aláírását. A fejlesztői dokumentációból megtudhatja, hogy miként írhat alá burkolt alkalmazásokat.|
|A megadott bemeneti alkalmazásnak .ipa vagy .app formátumúnak kell lennie.|Az alkalmazásburkoló eszköz csak .app és .ipa kiterjesztést fogad el. Ellenőrizze, hogy a bemeneti fájl érvényes kiterjesztéssel rendelkezik-e, és .app vagy .ipa fájlként lett-e összeállítva.|
|A megadott bemeneti alkalmazás már burkolt, és a házirendsablon legújabb verziójában van.|Az alkalmazásburkoló eszköz nem burkol újra egy már meglévő burkolt alkalmazást a szabályzatsablon legújabb verziójával.|
|FIGYELMEZTETÉS Nem adott meg SHA1 tanúsítvány kivonatát. Ellenőrizze, hogy a burkolt alkalmazás alá van-e írva a telepítés előtt.|Adjon meg egy érvényes SHA1 kivonatot a –c parancssori kapcsoló után. |

### <a name="log-files-for-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszköz naplófájljai
Az alkalmazásburkoló eszközzel burkolt alkalmazások az iOS-ügyféleszköz konzoljára írt naplófájlokat hoznak létre. Ezek az adatok akkor hasznosak, ha problémát tapasztal az alkalmazással kapcsolatban, és meg kell állapítania, hogy a hiba az alkalmazásburkoló eszközzel kapcsolatos-e. Az adatokat az alábbi lépéseket követve olvashatja be:

1. Az alkalmazást futtatva reprodukálja a hibát.

2. Gyűjtse össze a konzol kimenetét az Apple [telepített iOS-alkalmazások hibakeresésére](https://developer.apple.com/library/ios/qa/qa1747/_index.html)vonatkozó utasításait követve.

3. A következő szkriptet a konzolon megadva szűrje a mentett naplókat az alkalmazáskorlátozások kimenetre:

    ```bash
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```

    A szűrt naplót elküldheti a Microsoftnak.

    > [!NOTE]
    > A naplófájlban a „buildszám” az Xcode buildszámának felel meg.

    A burkolt alkalmazások lehetőséget biztosítanak a felhasználóknak, hogy az alkalmazás összeomlása után közvetlenül az eszközről küldjenek e-mailt. A felhasználók elküldhetik Önnek a naplót, hogy megvizsgálja, és szükség esetén továbbítsa azt a Microsoftnak.


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>Tanúsítvány, létesítési profil és hitelesítési követelmények

Az alkalmazásburkoló eszköz iOS-verziójának optimális működéséhez bizonyos követelményeknek teljesülniük kell.

|Követelmény|Részletek|
|---------------|-----------|
|iOS-beli létesítési profil|Használat előtt ellenőrizze a létesítési profil érvényességét. iOS-alkalmazások feldolgozásakor az alkalmazásburkoló eszköz nem ellenőrzi a létesítési profil érvényességét. Ha lejárt létesítési profil van megadva, az alkalmazásburkoló eszköz tartalmazza a lejárt létesítési profilt, és addig nem szerez tudomást a problémáról, amíg az alkalmazás telepítése meg nem hiúsul egy iOS-eszközön.|
|iOS-beli aláíró tanúsítvány|Mielőtt megadja az aláíró tanúsítványt, ellenőrizze, hogy érvényes-e. iOS-alkalmazások feldolgozásánál az alkalmazásburkoló eszköz nem ellenőrzi a tanúsítvány érvényességét. Ha lejárt tanúsítvány kivonatát adja meg, az eszköz feldolgozza és aláírja az alkalmazást, de nem tudja telepíteni az eszközökre.<br /><br />Ügyeljen rá, hogy a beburkolt alkalmazás aláírására használt tanúsítvány megtalálható legyen a létesítési profilban. Az eszköz nem ellenőrzi, hogy a létesítési profil rendelkezik-e egyezéssel a burkolt alkalmazás aláírásához megadott tanúsítványhoz.|
|Hitelesítés|A titkosítás működéséhez az eszközöknek PIN-kóddal kell rendelkezniük. Olyan eszközökön, amelyekre telepít egy beburkolt alkalmazást, az eszköz állapotsávjának megérintése esetén a felhasználónak újra be kell jelentkezni a munkahelyi vagy iskolai fiókjával. A burkolt alkalmazások alapértelmezett szabályzata a *hitelesítés újraindításkor*. Az iOS minden külső értesítést (például telefonhívást) az alkalmazásból való kilépésként és az alkalmazás újraindításaként kezel.


## <a name="setting-app-entitlements"></a>Alkalmazásjogosultságok beállítása
Az alkalmazást a burkolása előtt *jogosultságok* megadásával további engedélyekkel és képességekkel láthatja el. Ezek segítségével tovább bővítheti az alkalmazás által elvégezhető tevékenységek körét. A kódaláírás során a rendszer *jogosultságot tartalmazó fájlt* használ a speciális engedélyek (például megosztott kulcslánchoz való hozzáférés) megadásához az alkalmazáson belül. Az alkalmazás *képességek* néven ismert konkrét szolgáltatásai az alkalmazásfejlesztés során az Xcode-on belül engedélyezhetők. Miután engedélyezte őket, a képességek megjelennek a jogosultságokat tartalmazó fájlban. A jogosultságokról és képességekről az iOS Developer Library [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Képességek hozzáadása) című témakörében olvashat bővebben. A támogatott képességek teljes listáját a [Supported capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html) (Támogatott képességek) című témakörben találja.

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>Az iOS rendszerhez készült alkalmazásburkoló eszköz támogatott képességei

|Képesség|Leírás|Ajánlott útmutatás|
|--------------|---------------|------------------------|
|Alkalmazáscsoportok|Alkalmazáscsoportok használatával biztosíthatja több alkalmazás hozzáférését a megosztott tárolókhoz, és engedélyezheti a folyamatközi kommunikációt az alkalmazások között.<br /><br />Az alkalmazáscsoportok engedélyezéséhez nyissa meg a **Capabilities** (Képességek) panelt, és kattintson az **On** (Bekapcsolás) lehetőségre az **App Groups** (Alkalmazáscsoportok) beállításnál. Felvehet alkalmazáscsoportokat, illetve kijelölhet meglévőket.|Alkalmazáscsoportok használatakor használjon címfeloldási DNS-t:<br /><br />*csoport.com.cégnév.Alkalmazáscsoport*|
|Háttérbeli üzemmódok|A háttérbeli üzemmódok engedélyezése esetén az iOS-alkalmazás tovább futhat a háttérben is.||
|Adatvédelem|Az adatvédelem biztosítja az iOS-alkalmazás által a lemezen tárolt fájlok védelmét. Az adatvédelem az adott eszközökön megtalálható beépített titkosítási hardvert használja a fájlok titkosított formában történő tárolásához a lemezen. Az alkalmazást úgy kell létrehozni, hogy használjon adatvédelmet.||
|Alkalmazáson belüli vásárlás|Az alkalmazáson belüli vásárlás beépít egy áruházat magába az alkalmazásba azáltal, hogy engedélyezi az áruházhoz való csatlakozást és a felhasználó fizetéseinek biztonságos feldolgozását. Az alkalmazáson belüli vásárlás segítségével szedheti be a továbbfejlesztett funkciókért vagy az alkalmazása által használható további tartalomért járó díjakat.||
|Kulcslánc megosztása|A kulcslánc megosztása lehetővé teszi, hogy az alkalmazása jelszavakat osszon meg a kulcsláncban a csapata által fejlesztett egyéb alkalmazásokkal.|Kulcslánc megosztásakor fordított DNS jelölésmódot használjon:<br /><br />*com.cégnév.Kulcslánccsoport*|
|Személyes VPN|A személyes VPN engedélyezésével lehetővé teszi az alkalmazásnak, hogy egyéni VPN-rendszerkonfigurációt hozzon létre és szabályozzon a Hálózati bővítmény keretrendszer használatával.||
|Leküldéses értesítések|Az Apple Push Notification szolgáltatás (APNs) lehetővé teszi, hogy a nem az előtérben futó alkalmazások értesítsék a felhasználót arról, hogy információi vannak a számára.|A leküldéses értesítések működéséhez alkalmazásspecifikus létesítési profilt kell használnia.<br /><br />Kövesse az [Apple fejlesztői dokumentációjában](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) megadott lépéseket.|
|Vezeték nélküli tartozék konfigurációja|A vezeték nélküli tartozék konfigurációja felveszi a külsőtartozék-támogatási keretrendszert a projektjébe, és lehetővé teszi az alkalmazásnak az MFi Wi-Fi tartozékok beállítását.||

### <a name="steps-to-enable-entitlements"></a>A jogosultságok engedélyezésének lépései

1. Képességek engedélyezése az alkalmazásban:

    a.  Az Xcode-ban keresse meg az alkalmazás célját, és kattintson a **Capabilities** (Képességek) elemre.

    b.  Kapcsolja be a megfelelő képességeket. Az egyes képességekről és a megfelelő értékek meghatározásáról az iOS Developer Library [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Képességek hozzáadása) című témakörében olvashat bővebben.

    c.  Jegyezze fel a folyamat során létrehozott azonosítókat. Ezekre `AppIdentifierPrefix` értékekként lehet hivatkozni.

    d.  Készítse el és írja alá a burkolandó alkalmazást.

2. Jogosultságok engedélyezése a létesítési profiljában:

    a.  Jelentkezzen be az Apple Developer Member Center webhelyre.

    b.  Hozzon létre egy létesítési profilt az alkalmazásához. Utasításokért lásd: [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/) (Az Intune App Wrapping Tool for iOS előfeltételeinek megteremtése).

    c.  A létesítési profiljában engedélyezze ugyanazokat a jogosultságokat, amelyekkel az alkalmazásában rendelkezik. Adja meg ugyanazokat az azonosítókat (`AppIdentifierPrefix` értékek), amelyeket az alkalmazása fejlesztése során adott meg. 

    d.  Fejezze be a létesítési profil varázslót, és töltse le a fájlt.

3. Ellenőrizze, hogy minden előfeltétel teljesült-e, majd burkolja az alkalmazást.

### <a name="troubleshoot-common-errors-with-entitlements"></a>A jogosultságokkal kapcsolatos gyakori hibák elhárítása
Ha az iOS-hez készült alkalmazásburkoló eszköz jogosultsággal kapcsolatos hibát jelenít meg, próbálkozzon az alábbi hibaelhárítási lépésekkel.

|Probléma|Ok|Megoldás:|
|---------|---------|--------------|
|Nem sikerült a bemeneti alkalmazás által létrehozott jogosultságok elemzése.|Az alkalmazásburkoló eszköz nem tudja olvasni az alkalmazásból kinyert jogosultságfájlt. Előfordulhat, hogy a jogosultságfájl helytelenül formázott.|Vizsgálja meg az alkalmazásához tartozó jogosultságfájlt. A következő útmutatás elmagyarázza ennek módját. A jogosultságfájl vizsgálatakor ellenőrizze, hogy nem tartalmaz-e hibás szintaxist. A fájlnak XML formátumúnak kell lennie.|
|A létesítési profilban jogosultságok hiányoznak (a hiányzó jogosultságok listában láthatók). Csomagolja újra az alkalmazást egy olyan létesítési profillal, amely tartalmazza ezeket a jogosultságokat.|A létesítési profilban engedélyezett jogosultságok és az alkalmazásban engedélyezett képességek között eltérés tapasztalható. Ez az eltérés érvényes az adott képességekhez (vagyis az alkalmazáscsoportokhoz, kulcslánc-hozzáféréshez stb.) társított azonosítókra is.|Általában létrehozhat egy új létesítési profilt, amely ugyanazokat a képességeket engedélyezi, mint az alkalmazás. Ha nem egyeznek meg a profil és az alkalmazás között az azonosítók, az alkalmazásburkoló eszköz lecseréli őket (ha tudja). Ha az új létesítési profil létrehozását követően továbbra is megjelenik a hibaüzenet, próbálja meg eltávolítani a jogosultságokat az alkalmazásból az –e paraméter használatával (lásd a „Jogosultságok eltávolítása az alkalmazásból az –e paraméter használatával” című részt).|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Aláírt alkalmazás meglévő jogosultságainak megkeresése
Aláírt alkalmazás és létesítési profil meglévő jogosultságainak ellenőrzése:

1. Keresse meg az .ipa fájlt, és módosítsa .zip kiterjesztésűre.

2. Bontsa ki a .zip fájlt. Ez a művelet létrehoz egy Payload nevű mappát, amely tartalmazza az .app csomagot.

3. A codesign eszközzel ellenőrizze a jogosultságokat az .app csomagon (a `YourApp.app` helyére adott .app csomag nevét kell beírni):

    ```bash
    codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4. A security eszközzel ellenőrizze a jogosultságokat az .app beépített létesítési profilján (a `YourApp.app` helyére adott .app csomag nevét kell beírni).

    ```bash
    security cms -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Jogosultságok eltávolítása az alkalmazásból az –e paraméterrel
Ezzel a paranccsal eltávolítja az alkalmazásból azon engedélyezett képességeket, amelyek nem szerepelnek a jogosultságokat tartalmazó fájlban. Ha olyan képességeket távolít el, amelyeket az alkalmazás használ, az az alkalmazás meghibásodásához vezethet. Hiányzó képességeket például abban az esetben érdemes eltávolítani, ha egy partner által fejlesztett alkalmazásnak alapértelmezés szerint minden képessége megvan.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszközzel kapcsolatos biztonsági és adatvédelmi szempontok
Az alkalmazásburkoló eszköz használata során kövesse az alábbi biztonsági és adatvédelmi gyakorlati tanácsokat.

- Az aláíró tanúsítványnak, a létesítési profilnak és a megadott üzletági alkalmazásnak ugyanazon a macOS-számítógépen kell lennie, mint amelyet az alkalmazásburkoló eszköz futtatásához használ. Ha a fájlok egy UNC elérési úton vannak, ellenőrizze, hogy elérhetők-e a macOS -számítógépről. Az elérési utat IPsec- vagy SMB-aláírással védeni kell.

    A felügyeleti konzolra importált beburkolt alkalmazásnak ugyanazon a számítógépen kell lennie, mint amelyen az eszközt futtatja. Ha a fájl egy UNC elérési úton van, győződjön meg róla, hogy a mappa elérhető a felügyeleti konzolt futtató számítógépről. Az elérési utat IPsec- vagy SMB-aláírással védeni kell.

- IPsec- vagy SMB-aláírással kell védeni azt a környezetet, ahová az alkalmazásburkoló eszközt a GitHub-tárházból letölti.

- A feldolgozott alkalmazásnak megbízható forrásból kell származnia ahhoz, hogy a támadások elleni védelmét biztosítani lehessen.

- Gondoskodjon az alkalmazásburkoló eszközben megadott kimeneti mappa védelméről, különösen ha távoli mappáról van szó.

- A fájlfeltöltési párbeszédpanelt tartalmazó iOS-alkalmazások lehetővé tehetik a felhasználóknak, hogy megkerüljék az alkalmazáshoz megadott kivágási, másolási és beillesztési korlátozásokat. A felhasználók a fájlfeltöltési párbeszédpanelt használhatják például az alkalmazásadatok képernyőfelvételének feltöltéséhez.

- Amikor egy burkolt alkalmazásból figyeli az eszközükön lévő dokumentummappát, láthatja az .msftintuneapplauncher nevű mappát. Ha módosítja vagy törli ezt a mappát, az hatással lehet a korlátozott alkalmazások megfelelő működésére.

## <a name="intune-app-wrapping-tool-for-ios-with-citrix-mdx-mvpn"></a>Intune alkalmazásburkoló eszköz iOS rendszerhez Citrix MDX mVPN-nel
Ez a funkció az iOS rendszerre készült Citrix MDX alkalmazásburkolóval való integrációt jelenti. Az integráció egyszerűen egy további, opcionális parancssori jelzőt (`-citrix`) az általános Intune alkalmazásburkoló eszközökhöz.

### <a name="requirements"></a>Követelmények

A `-citrix` jelző használatához telepíteni kell az adott macOS-eszközre az [iOS rendszerre készült Citrix MDX alkalmazásburkolót](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) is. A letöltések a [Citrix XenMobile letöltései](https://www.citrix.com/downloads/xenmobile/) között találhatók, és a Citrix ügyfelei számára csak bejelentkezés után érhetők el. Győződjön meg arról, hogy az alapértelmezett helyre van telepítve: `/Applications/Citrix/MDXToolkit`. 

> [!NOTE] 
> Az Intune és a Citrix integrációját csak az iOS 10 és újabb rendszerű eszközök támogatják.

### <a name="use-the--citrix-flag"></a>A `-citrix` jelző használata
Egyszerűen futtassa az általános alkalmazásburkoló parancsot, és fűzze hozzá a `-citrix` jelzőt. A `-citrix` jelző jelenleg nem használ argumentumokat.

**Használat formátuma**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioing profile paths>] [-citrix]
```

**Példaparancs**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true -citrix
```

## <a name="getting-logs-for-your-wrapped-applications"></a>Naplófájlok beszerzése burkolt alkalmazásokhoz
Hibaelhárítás során az alábbi lépésekkel szerezhet be naplófájlokat a burkolt alkalmazásaihoz.

1. Nyissa meg az iOS beállításkezelő alkalmazását az eszközön, és válassza a kívánt LOB-alkalmazást.
2. Állítsa a **Diagnostics Console** beállítást a **Be** állásba.
3. Indítsa el a LOB-alkalmazást.
4. Kattintson az „Első lépések” hivatkozásra.
5. Most már megoszthatja a naplófájlokat e-mailben, vagy átmásolhatja őket egy OneDrive-helyre.

> [!NOTE]
> A naplózási funkció engedélyezve van az Intune alkalmazásburkoló eszköz 7.1.13-as vagy újabb verziójával burkolt alkalmazásokban.

## <a name="see-also"></a>Lásd még:

- [Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal](apps-prepare-mobile-application-management.md)
- [Általános kérdések, problémák és megoldások az eszközök házirendjével és profiljaival](../configuration/device-profile-troubleshoot.md)
- [Alkalmazások előkészítése a mobilalkalmazás-felügyeletre az SDK segítségével](app-sdk.md)
