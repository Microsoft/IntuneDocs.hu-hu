---
# required metadata

title: iOS-alkalmazások felügyeletre való előkészítése az alkalmazásburkoló eszközzel | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# iOS-alkalmazások mobilalkalmazás-felügyeletre való előkészítése az alkalmazásburkoló eszközzel
A **Microsoft Intune App Wrapping Tool for iOS** nevű alkalmazásburkoló eszközzel módosíthatja a belső fejlesztésű IOS-alkalmazások viselkedését, így az alkalmazások kódjának módosítása nélkül korlátozhatja az alkalmazások funkcióit.

Az eszköz egy Mac OS parancssori alkalmazás, amely „burkolót” hoz létre az alkalmazások körül. Az alkalmazások feldolgozását követően az Ön által beállított [mobilalkalmazás-kezelési szabályzat](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) használatával módosíthatja az alkalmazások működését.

Az eszköz letöltéséhez keresse fel a [Microsoft Intune App Wrapping Tool for iOS](http://www.microsoft.com/en-us/download/details.aspx?id=45218) weblapot..

## 1. lépés: Az alkalmazásburkoló eszköz használatára vonatkozó előfeltételek teljesítése

|Követelmény|További információ|
|---------------|--------------------------------|
|Támogatott operációs rendszer és eszközkészlet|Az alkalmazásburkoló eszközt OS X 10.8.5 vagy újabb rendszerű Mac számítógépen kell futtatni, amelyen telepítve van az XCode eszközkészlet 5-ös vagy újabb verziója.|
|Aláíró tanúsítvány és létesítési profil|Rendelkeznie kell egy Apple aláíró tanúsítvánnyal és létesítési profillal. Lásd az [Apple fejlesztői dokumentációját](https://developer.apple.com/)..|
|Alkalmazás feldolgozása az alkalmazásburkoló eszközzel|Az alkalmazást vállalatának vagy egy független szoftverszállítónak kell létrehoznia és aláírnia. Az eszköz nem használható az Apple Store áruházból származó alkalmazások feldolgozásához. Az alkalmazásoknak az iOS 7.0-s vagy újabb verziójához kellett készülnie. Az alkalmazásoknak a Position Independent Executable (PIE) formátumot kell használniuk. A PIE formátumról az Apple fejlesztői dokumentációjában talál további információkat. Végül az alkalmazásoknak **.app** vagy **.ipa** kiterjesztésűeknek kell lenniük.|
|Az alkalmazásburkoló eszköz által nem feldolgozható alkalmazások|Titkosított alkalmazások, aláíratlan alkalmazások, kiterjesztett fájlattribútumokkal rendelkező alkalmazások.|
|Az Azure Active Directory Authentication Libraryt (ADAL-t) használó alkalmazások|Ha az alkalmazás ADAL-t használ, legalább az ADAL 1.0.2-es verzióját kell tartalmaznia, és a fejlesztőnek hozzáférést kell adnia az alkalmazás számára az Intune mobilalkalmazás-kezelési erőforráshoz.<br /><br />Az ADAL használatával kapcsolatban lásd a jelen cikkben alább található [Az Azure Active Directory Libraryt (ADAL) használó alkalmazásokra vonatkozó tájékoztatás](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#information-for-apps-that-use-the-azure-active-directory-library) cím részt.|
|Jogosultságok beállítása az alkalmazáshoz|Az alkalmazás burkolása előtt jogosultságokat kell megadnia, amelyek az általában megadottak mellett további engedélyekkel és képességekkel ruházzák fel az alkalmazást. További utasításokért lásd az [Alkalmazásjogosultságok beállítása](#setting-app-entitlements) című részt.|

## 2. lépés: Az alkalmazásburkoló eszköz telepítése

1.  A **Microsoft letöltőközpont** [Microsoft Intune App Wrapping Tool for iOS](https://www.microsoft.com/download/details.aspx?id=45218) lapján töltse le a Mac gépre készült alkalmazásburkoló eszköz teljepítőfájlját.

2.  A Mac számítógépen kattintson duplán a **Microsoft Intune App Wrapping Tool for iOS.dmg** telepítőfájlra..

3.  Válassza az **Elfogadom** lehetőséget a végfelhasználói licencszerződés elfogadásához. A telepítő csatlakozik és megjelenik a Mac számítógépen.

4.  Nyissa meg a telepítőt, és másolja a megjelenített fájlokat egy új mappába a Mac számítógépen. Most már leválaszthatja a csatlakoztatott telepítő meghajtóját.

    Most már készen áll az alkalmazásburkoló eszköz futtatására.

## 3. lépés: Az alkalmazásburkoló eszköz futtatása

1.  A Mac számítógépen nyissa meg a terminálablakot, és keresse meg azt a mappát, ahová mentette a fájlokat. Mivel a végrehajtható fájl a csomagon belül található, a parancsot a következőképpen kell futtatnia:
```
    ./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB –a 20e1cd0d-268e-4308-9583-02ae97dd353e –r https://contoso/ -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|Tulajdonság|További információ|
  |------------|--------------------|
  |**-h**|A rendelkezésre álló parancssori tulajdonságok megjelenítése az alkalmazásburkoló eszközhöz|
  |**-i**|A bemeneti alkalmazás elérési útjának és nevének megadása|
  |**-o**|A feldolgozott alkalmazás mentéséhez használandó elérési út megadása|
  |**-p**|Az iOS-alkalmazások létesítési profiljához vezető elérési út megadása|
  |**-c**|Az aláíró tanúsítvány SHA1 kivonatának megadása.|
  |**-a**|A bemeneti alkalmazás ügyfél-azonosítója (GUID formátumban), ha az alkalmazás Azure Active Directory-tárakat használ (nem kötelező)|
  |**-r**|A bemeneti alkalmazás átirányítási URI-címe, ha az alkalmazás Azure Active Directory-tárakat használ (nem kötelező)|
  |**-v**|Kimeneti részletes üzenetek a konzolhoz (nem kötelező)|

2. A feldolgozás befejezése után megjelenik **Az alkalmazás burkolása sikerült** üzenet.

    Hiba esetén további segítségért lásd: [Hibaüzenetek](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) .

3.  A burkolt alkalmazást a korábban megadott kimeneti mappába menti a rendszer. Most már feltöltheti az alkalmazást az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ba, és társíthatja egy mobilalkalmazás-felügyeleti házirenddel.

    > [!IMPORTANT]
    > Az alkalmazást új alkalmazásként kell feltöltenie. Az alkalmazás korábbi, burkolatlan verziója nem frissíthető.

    Most már telepítheti az alkalmazást az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-csoportokba, és az alkalmazás már futni fog a megadott alkalmazáskorlátozásokat használó eszközön.

## Hibaüzenetek és naplófájlok
Az alábbi információkat használva háríthatja el az alkalmazásburkoló eszközzel kapcsolatos hibákat.

### Hibaüzenetek
Ha az alkalmazásburkoló eszköz befejezése sikertelen, az alábbi hibaüzenetek valamelyike jelenik meg:

|Hibaüzenet|További információ|
|-----------------|--------------------|
|Adjon meg egy érvényes iOS-létesítési profilt.|Előfordulhat, hogy a létesítési profil nem érvényes. Ellenőrizze, hogy rendelkezik-e megfelelő engedélyekkel az eszközökhöz, és hogy a profilja megfelelően be van-e állítva fejlesztéshez vagy terjesztéshez. A létesítési profilja esetleg le is járhatott.|
|Adjon meg egy érvényes bemeneti alkalmazásnevet.|Győződjön meg arról, hogy helyesen adta meg a bemeneti alkalmazás nevét.|
|Adjon meg érvényes elérési utat a kimeneti alkalmazáshoz.|Győződjön meg arról, hogy a kimeneti alkalmazás megadott elérési útja létezik és helyes.|
|Adjon meg egy érvényes bemeneti létesítési profilt.|Győződjön meg arról, hogy érvényes létesítésiprofil-nevet és -kiterjesztést adott meg. Előfordulhat, hogy hiányoznak jogosultságok a létesítési profiljához, vagy nem vette fel a **–p** parancssori kapcsolót.|
|A megadott bemeneti alkalmazás nem található. Adjon meg egy érvényes nevet és elérési utat a bemeneti alkalmazáshoz.|Győződjön meg arról, hogy a bemeneti alkalmazás elérési útja érvényes és létezik. Ellenőrizze, hogy a bemeneti alkalmazás az adott helyen található-e.|
|A megadott bemeneti létesítési profilfájl nem található. Adjon meg egy érvényes bemeneti létesítési profilfájlt.|Győződjön meg arról, hogy a bemeneti létesítési fájl elérési útja érvényes és a megadott fájl létezik.|
|A megadott kimeneti alkalmazásmappa nem található. Adjon meg érvényes elérési utat a kimeneti alkalmazáshoz.|Győződjön meg arról, hogy a megadott kimeneti elérési út érvényes és létezik.|
|A kimeneti alkalmazás kiterjesztése nem .ipa.|Az alkalmazásburkoló eszköz csak **.app** és **.ipa** kiterjesztést fogad el. Ellenőrizze, hogy a kimeneti fájl kiterjesztése érvényes-e.|
|Érvénytelen aláíró tanúsítványt adott meg. Adjon meg egy érvényes Apple aláíró tanúsítványt.|Ellenőrizze, hogy a helyes aláíró tanúsítványt töltötte-e le az Apple fejlesztői portáljáról. Előfordulhat az is, hogy a tanúsítvány lejárt. Ha Apple-tanúsítványa és létesítési profilja használható az alkalmazások megfelelő aláírásához az Xcode-on belül, akkor érvényesek az alkalmazásburkoló eszközhöz.|
|A megadott bemeneti alkalmazás érvénytelen. Adjon meg egy érvényes alkalmazást.|Győződjön meg arról, hogy .app vagy .ipa fájlként összeállított, érvényes iOS-alkalmazással rendelkezik.|
|A megadott bemeneti alkalmazás titkosítva van. Adjon meg egy érvényes titkosítatlan alkalmazást.|Az alkalmazásburkoló eszköz nem támogatja a titkosított alkalmazásokat. Adjon meg egy titkosítatlan alkalmazást.|
|A megadott bemeneti alkalmazás nem Position Independent Executable (PIE) formátumú. Adjon meg egy érvényes alkalmazást PIE formátumban.|A Position Independent Executable (PIE) formátumú alkalmazások egy véletlenszerű memóriacímre tölthetők be futtatás közben, ami biztonsági szempontból előnyökkel járhat. További tudnivalókért tanulmányozza az Apple fejlesztői dokumentációját.|
|A megadott bemeneti alkalmazás már be van burkolva. Adjon meg egy érvényes burkolatlan alkalmazást.|Az eszköz által már feldolgozott alkalmazás nem dolgozható fel. Ha ismét fel szeretne dolgozni egy alkalmazást, az alkalmazás eredeti verzióját használva futtassa az eszközt.|
|A megadott bemeneti alkalmazás nincs aláírva. Adjon meg egy érvényes aláírt alkalmazást.|Az alkalmazásburkoló eszköz megköveteli az alkalmazások aláírását. A fejlesztői dokumentációból megtudhatja, hogy miként írhat alá burkolt alkalmazásokat.|
|A megadott bemeneti alkalmazásnak .ipa vagy .app formátumúnak kell lennie.|Az alkalmazásburkoló eszköz csak .app és .ipa kiterjesztést fogad el. Ellenőrizze, hogy a bemeneti fájl érvényes kiterjesztéssel rendelkezik-e, és .app vagy .ipa fájlként lett-e összeállítva.|
|A megadott bemeneti alkalmazás már burkolt, és a házirendsablon legújabb verziójában van.|Az alkalmazásburkoló eszköz nem fog újraburkolni egy már meglévő burkolt alkalmazást a házirendsablon legújabb verziójával.|
|Az Azure Active Directory megadott ügyfél-azonosítója nem megfelelően formázott GUID azonosító. Adjon meg egy érvényes ügyfél-azonosítót.|Az Ügyfél-azonosító paraméter használata esetén GUID formátumú, érvényes Ügyfél-azonosító paramétert adjon meg.|
|Az Azure Active Directory megadott válasz URI-ja nem megfelelően formázott URI. Adjon meg egy érvényes válasz URI-t.|A válasz URI parancssori tulajdonság használata esetén ellenőrizze, hogy érvényes válasz URI-t adott-e meg.|
|Figyelmeztetés: Nem adta meg az SHA1 tanúsítvány kivonatát. Ellenőrizze, hogy a burkolt alkalmazás alá van-e írva a telepítés előtt.|Adjon meg egy érvényes SHA kivonatot (a **– c** parancssori tulajdonság használatával).|

### Az alkalmazásburkoló eszköz naplófájljai
Az alkalmazásburkoló eszközzel burkolt alkalmazások az iOS-ügyféleszköz konzoljára írt naplófájlokat hoznak létre. Ezek az adatok akkor hasznosak, ha problémákat tapasztal az alkalmazással kapcsolatban, és meg kell állapítania az alkalmazásburkoló eszközzel kapcsolatos hibát. Az adatokat az alábbi lépéseket követve olvashatja be:

1.  Az alkalmazást futtatva reprodukálja a hibát.

2.  Gyűjtse össze a konzol kimenetét az Apple [telepített iOS-alkalmazások hibakeresésére](https://developer.apple.com/library/ios/qa/qa1747/_index.html) vonatkozó utasításait követve..

3.  A következő szkriptet a konzolon megadva szűrje a mentett naplókat az alkalmazáskorlátozások kimenetre:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    A szűrt naplót elküldheti a Microsoftnak.

    > [!NOTE]
    > A naplófájlban a „buildszám” az Xcode buildszámának felel meg.

    A burkolt alkalmazások lehetőséget biztosítanak a felhasználóknak, hogy az alkalmazás összeomlása után közvetlenül az eszközről küldjenek e-mailt. A felhasználók elküldhetik Önnek a naplót, hogy megvizsgálja és szükség esetén továbbítsa azt a Microsoftnak.

## Az Azure Active Directory Libraryt (ADAL) használó alkalmazásokra vonatkozó tájékoztatás
Az ebben a szakaszban található információk csak az Azure Active Directory Libraryt (ADAL) használó alkalmazásokra vonatkoznak. Ha nem biztos abban, hogy alkalmazása használja-e ezt a tárat, lépjen kapcsolatba az alkalmazás fejlesztőjével.

Az alkalmazásnak 1.0.2-es vagy újabb ADAL-verziót kell tartalmaznia.

Az ADAL tárat használó alkalmazások esetében az alábbiaknak kell teljesülniük:

-   Az alkalmazásnak tartalmaznia kell egy ADAL verziót, amely az 1.0.2-esnél újabb

-   A fejlesztőnek hozzáférést kell adnia az alkalmazás számára az Intune Mobilalkalmazás-kezelés erőforráshoz az alábbiak szerint: [Az ADAL-t használó alkalmazások által követendő lépések](#steps-to-follow-for-apps-that-use-adal)..

### A beszerzendő azonosítók áttekintése
Az ADAL tárat használó alkalmazásoknak az Azure felügyeleti portálján keresztül regisztrálniuk kell ahhoz, hogy alkalmazásukhoz beszerezzenek két egyedi azonosítót:

|Azonosító|További információ|Alapértelmezett érték|
|--------------|--------------------|-----------------|
|**Ügyfél-azonosító**|Az Azure Active Directoryval történő regisztrálást követően minden alkalmazáshoz létrejön egy egyedi GUID azonosító.<br /><br />Ha ismeri az alkalmazások adott ügyfél-azonosítóját, megadhatja ezt az értéket. Egyéb esetekben az alapértelmezett értéket kell használni.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**Átirányítási URI**|A fejlesztők által az alkalmazásuk Azure Active Directoryban való regisztrálásakor megadható URI érték annak biztosításához, hogy a hitelesítési tokenek kifejezetten az adott végpontra kerüljenek vissza.<br /><br />Az átirányítási URI megadása nem kötelező paraméter az alkalmazásburkoló eszközhöz. Ha nincs megadva, az alapértelmezett URI-t fogja használni.|urn:ietf:wg:oauth:2.0:oob|


### Az ADAL-t használó alkalmazások által követendő lépések

1.  Ha szeretné áttekinteni, hogy milyen értékeket kell kapnia, olvassa el [A beszerzendő azonosítók áttekintése](#overview-of-identifiers-you-need-to-get) című részt.

2.  Állítsa be a mobilalkalmazás-felügyelet elérését az Azure Active Directoryban az alábbi lépésekkel:

    1. Jelentkezzen be egy meglévő Azure Active Directory-fiókba az Azure felügyeleti portálján.

    2.  Kattintson a **meglévő LOB-alkalmazás regisztrációja** elemre az Azure Active Directoryban.

    3.  A konfigurálási résznél válassza a **Configure Access to Web APIs in other applications** (Webes API-k más alkalmazásokban való elérésének konfigurálása) lehetőséget..

    4.  A **Permission to other applications** (Engedélyek más alkalmazásoknak) rész első legördülő listájából válassza az **Intune Mobile Application Management** (Intune Mobilalkalmazás-kezelés) lehetőséget..

        Ezután már használhatja az alkalmazás ügyfél-azonosítóját az alkalmazásburkoló eszközben. Az alkalmazás ügyfél-azonosítója az Azure Active Directory felügyeleti portálon található, ahogy az [A beszerzendő azonosítók áttekintése](#overview-of-identifiers-you-need-to-get) című részben is olvasható.

3.  Az alkalmazásburkoló eszközben parancssori tulajdonságként használja a **Client-ID** (az **–a** tulajdonságot használva) és a **Redirect-URI** értéket. Ha nem rendelkezik ezekkel az értékekkel, az eszköz az alapértelmezett értékeket fogja használni. Mindkét értéket meg kell adni, egyébként a végfelhasználó nem tudja sikeresen hitelesíteni a feldolgozott alkalmazást.

### Tanúsítvány, létesítési profil és hitelesítési követelmények

|Követelmény|Részletek|
|---------------|-----------|
|Létesítési profil|**Mielőtt hozzáadja a létesítési profilt, ellenőrizze, hogy érvényes-e** – Az iOS-alkalmazások feldolgozásakor az alkalmazásburkoló eszköz nem ellenőrzi, hogy a létesítési profil lejárt-e. Ha lejárt létesítési profil van megadva, az alkalmazásburkoló eszköz tartalmazza a lejárt létesítési profilt, és addig nem szerez tudomást a problémáról, amíg az alkalmazás telepítése meg nem hiúsul egy iOS-eszközön.|
|Tanúsítvány|**Mielőtt megadná a tanúsítványt, ellenőrizze, hogy érvényes-e** – Az iOS-alkalmazások feldolgozásakor az alkalmazásburkoló eszköz nem ellenőrzi, hogy a tanúsítvány lejárt-e. Ha lejárt tanúsítvány kivonatát adja meg, az eszköz feldolgozza és aláírja az alkalmazást, de nem tudja telepíteni az eszközökre.<br /><br />**Győződjön meg róla, hogy a burkolt alkalmazás aláírásához megadott tanúsítvány rendelkezik-e egyezéssel a létesítési profilban** – Az eszköz nem ellenőrzi, hogy a létesítési profil rendelkezik-e egyezéssel a burkolt alkalmazás aláírásához megadott tanúsítványhoz.|
|Hitelesítés|A titkosítás működéséhez az eszközöknek PIN-kódkészlettel kell rendelkezniük. Azokon az eszközökön, amelyekhez burkolt alkalmazást telepített, az eszközön lévő állapotjelző sáv megérintése esetén a felhasználónak újra hitelesíteni kell az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-nal. A burkolt alkalmazások alapértelmezett szabályzata a *hitelesítés újraindításkor*. Az iOS minden külső értesítést (például egy telefonhívást) az alkalmazásból való kilépésként és annak újraindításaként kezel.<br /><br />Burkolt alkalmazások esetén a rendszer azt az első felhasználót gyorsítótárazza, aki bejelentkezik bármelyik burkolt alkalmazásba. Ezt követően csak az a felhasználó férhet hozzá az alkalmazáshoz. A felhasználó alaphelyzetbe állításához az eszköz regisztrációját meg kell szüntetni, majd újból regisztrálni kell.|

### Hibaelhárítás és technikai megjegyzések az ADAP-pal kapcsolatban

-   Ha nem találhatók ADAL-erőforrások, az eszköz az ADAL dinamikus tárát fogja tartalmazni. Az eszköz meg fogja keresni az ADAL **ADALiOS.bundle** nevű tárát a gyökérmappában.

-   Az eszköz nem keres ADAL bináris fájlokat (ha vannak) az alkalmazásban. Ha az alkalmazás elavult verzióhoz kapcsolódik, futásidejű hibák jelentkezhetnek a bejelentkezés során, ha engedélyezve vannak hitelesítési házirendek.

-   [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] lekéri az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM erőforrás-azonosítójához tartozó AAD tokent. A rendszer ugyanakkor nem használja semmilyen hívásban, amely a token érvényességének ellenőrzésére szolgálna. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] csak a bejelentkezett felhasználó egyszerű felhasználónevét olvassa be az alkalmazás elérésének meghatározásához. Az AAD token nem használatos a további szolgáltatáshívásokhoz.

-   A hitelesítési tokenek az ugyanazon közzétevőtől származó alkalmazások között vannak megosztva, mivel tárolásuk megosztott kulcsláncban történik. Ha el szeretne különíteni egy adott alkalmazást, másik aláíró tanúsítványt és létesítési profilt kell használnia az alkalmazáshoz.

-   Megelőzhetők az ismétlődő bejelentkezési utasítások, ha megadja az alkalmazás ügyfél-azonosítóját és átirányítási URI-ját. Ezt az ügyfél-azonosítót regisztrálni kell a közzétett [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM erőforrás-azonosító eléréséhez az AAD irányítópultján. Ennek elmaradása esetén bejelentkezési hiba lép fel, amikor az alkalmazás fut.

## Alkalmazásjogosultságok beállítása
Az alkalmazást a burkolása előtt **jogosultságok** megadásával további engedélyekkel és képességekkel láthatja el. Ezek segítségével tovább bővítheti az alkalmazás által elvégezhető tevékenységek körét.  A kódaláírás során a rendszer **jogosultságot tartalmazó fájlt** használ a speciális engedélyek (például megosztott kulcslánchoz való hozzáférés) megadásához az alkalmazáson belül. Az alkalmazás **képességek** néven ismert specifikus szolgáltatások az alkalmazásfejlesztés során az Xcode-on belül engedélyezhetők. Miután engedélyezte őket, a képességek megjelennek a jogosultságokat tartalmazó fájlban. A jogosultságokról és képességekről az iOS Developer Library [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Képességek hozzáadása) című témakörében olvashat bővebben. A támogatott képességek teljes listáját a [Supported capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html) (Támogatott képességek) című témakörben találja..

### Az iOS rendszerhez készült alkalmazásburkoló eszköz támogatott képességei

|Képesség|Leírás|Ajánlott útmutatás|
|--------------|---------------|------------------------|
|Alkalmazáscsoportok|Alkalmazáscsoportok használatával biztosíthatja több alkalmazás hozzáférését a megosztott tárolókhoz, és engedélyezheti a folyamatközi kommunikációt az alkalmazások között.<br /><br />Az alkalmazáscsoportok engedélyezéséhez nyissa meg a **Képességek** panelt, és az **Alkalmazáscsoportok** részen kattintson a **BE** kapcsolóra. Felvehet alkalmazáscsoportokat, illetve kijelölhet meglévőket.|Alkalmazáscsoportok használatakor használjon címfeloldási DNS-t:<br /><br />*csoport.com.cégnév.Alkalmazáscsoport*|
|Háttérmódok|A háttérmódok engedélyezése lehetővé teszi az iOS-alkalmazás futtatását a háttérben.||
|Adatvédelem|Az adatvédelem biztosítja az iOS-alkalmazás által a lemezen tárolt fájlok védelmét. Az adatvédelem az adott eszközökön megtalálható beépített titkosítási hardvert használja a fájlok titkosított formában történő tárolásához a lemezen. Az alkalmazást úgy kell létrehozni, hogy használjon adatvédelmet.||
|Alkalmazáson belüli vásárlás|Az alkalmazáson belüli vásárlás közvetlenül az alkalmazásba beépít egy áruházat azáltal, hogy engedélyezi az áruházhoz csatlakozást és a felhasználó fizetéseinek biztonságos feldolgozását. Az alkalmazáson belüli vásárlás segítségével szedheti be a továbbfejlesztett funkciókért vagy az alkalmazása által használható további tartalomért járó díjakat.||
|Kulcslánc megosztása|A kulcslánc megosztása lehetővé teszi, hogy az alkalmazása jelszavakat osszon meg a kulcsláncban a csapata által fejlesztett egyéb alkalmazásokkal.|Kulcslánc megosztásakor használjon címfeloldási DNS-t:<br /><br />*com.cégnév.Kulcslánccsoport*|
|Személyes VPN|A személyes VPN engedélyezésével lehetővé teszi az alkalmazásnak, hogy egyéni VPN-rendszerkonfigurációt hozzon létre és szabályozzon a Hálózati bővítmény keretrendszer használatával.||
|Leküldéses értesítések|Az Apple Push Notification szolgáltatás (APNs) lehetővé teszi, hogy a nem az előtérben futó alkalmazások értesítsék a felhasználót arról, hogy információi vannak a számára.|A leküldéses értesítések működéséhez alkalmazásspecifikus létesítési profilt kell használnia.<br /><br />Kövesse az [Apple fejlesztői dokumentációjában](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) megadott lépéseket..|
|Vezeték nélküli tartozék konfigurációja|A vezeték nélküli tartozék konfigurációja felveszi a külsőtartozék-támogatási keretrendszert a projektjébe, és lehetővé teszi az alkalmazásnak az MFi Wi-Fi tartozékok konfigurálását.||

### A jogosultságok engedélyezésének lépései

1.  Képességek engedélyezése az alkalmazásban:

    1.  Az Xcode-ban keresse meg az alkalmazás célját, és kattintson a **Képességek** panelre.

    2.  Kapcsolja be a megfelelő képességeket. Az egyes képességekről és a megfelelő értékek meghatározásáról az iOS Developer Library [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Képességek hozzáadása) című témakörében olvashat bővebben.

    3.  Jegyezze fel a folyamat során létrehozott azonosítókat.

    4.  Készítse el és írja alá a burkolandó alkalmazást.

2.  Jogosultságok engedélyezése a létesítési profiljában:

    1.  Jelentkezzen be az Apple Developer Member Center webhelyre.

    2.  Hozzon létre egy létesítési profilt az alkalmazásához. Utasításokért lásd: [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS](http://blogs.technet.com/b/microsoftintune/archive/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios.aspx) (Az Intune App Wrapping Tool for iOS előfeltételeinek megteremtése)..

    3.  A létesítési profiljában engedélyezze ugyanazokat a jogosultságokat, amelyekkel az alkalmazásában rendelkezik. Adja meg ugyanazokat az azonosítókat, amelyeket az alkalmazása fejlesztése során adott meg.

    4.  Fejezze be a létesítési profil varázslót, és töltse le a fájlt.

3.  Ellenőrizze, hogy minden előfeltétel teljesült-e, majd burkolja az alkalmazást.

### A jogosultságokkal kapcsolatos gyakori hibák elhárítása
Ha az iOS rendszerhez készült alkalmazásburkoló eszköz jogosultsággal kapcsolatos hibát jelenít meg, próbálkozzon meg az alábbi hibaelhárítási lépésekkel.

|Probléma|Ok|Megoldás|
|---------|---------|--------------|
|Nem sikerült a bemeneti alkalmazás által létrehozott jogosultságok elemzése.|Az alkalmazásburkoló eszköz nem tudja olvasni az alkalmazásból kinyert jogosultságfájlt. Előfordulhat, hogy a jogosultságfájl helytelenül formázott.|Vizsgálja meg az alkalmazásához tartozó jogosultságfájlt. Ehhez kövesse az alábbi utasításokat. A jogosultságfájl vizsgálatakor ellenőrizze, hogy nem tartalmaz-e hibás szintaxist. A fájlnak XML formátumúnak kell lennie.|
|A létesítési profilban jogosultságok hiányoznak (a hiányzó jogosultságok listában láthatók). Csomagolja újra az alkalmazást egy olyan létesítési profillal, amely tartalmazza ezeket a jogosultságokat.|A létesítési profilban engedélyezett jogosultságok és az alkalmazásban engedélyezett képességek között eltérés tapasztalható. Ez az eltérés érvényes az adott képességekhez (vagyis az alkalmazáscsoportokhoz, kulcslánc-hozzáféréshez stb.) társított azonosítókra is.|Általában létrehozhat egy új létesítési profilt, amely ugyanazokat a képességeket engedélyezi, mint az alkalmazás. Ha nem egyeznek meg a profil és az alkalmazás között az azonosítók, az alkalmazásburkoló eszköz lecseréli őket (ha tudja). Ha az új létesítési profil létrehozását követően továbbra is megjelenik a hibaüzenet, próbálja meg eltávolítani a jogosultságokat az alkalmazásból az **–e** paraméter használatával (lásd az alábbi „Jogosultságok eltávolítása az alkalmazásból az –e paraméter használatával” című részt).|

### Aláírt alkalmazás meglévő jogosultságainak megkeresése
Aláírt alkalmazás és létesítési profil meglévő jogosultságainak ellenőrzése:

1.  Keresse meg az .ipa fájlt, és módosítsa .zip kiterjesztésűre.

2.  Bontsa ki a .zip fájlt. Ez a művelet létrehoz egy Payload nevű mappát, amely tartalmazza az .app csomagot.

3.  A codesign eszközzel ellenőrizze a jogosultságokat az .app csomagon az alábbi módon:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    ahol a `YourApp.app` a .app csomag tényleges neve.

4.  A security eszközzel ellenőrizze az alkalmazás beágyazott létesítési profiljának jogosultságait:

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    ahol a `YourApp.app` a .app csomag tényleges neve.

### Jogosultságok eltávolítása az alkalmazásból az –e paraméter használatával
Ezzel a paranccsal eltávolítja az alkalmazásból azon engedélyezett képességeket, amelyek nem szerepelnek a jogosultságokat tartalmazó fájlban. Ha olyan képességeket távolít el, amelyeket az alkalmazás használ, az az alkalmazás meghibásodásához vezethet. Hiányzó képességeket például abban az esetben érdemes eltávolítani, ha egy partner által fejlesztett alkalmazás alapértelmezés szerint rendelkezik az összes képességgel.

```
./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Biztonság és adatvédelem az alkalmazásburkoló eszköz esetén
Az alkalmazásburkoló eszköz használatakor kövesse az alábbi biztonsági és adatvédelmi gyakorlati tanácsokat.

-   Az aláíró tanúsítványnak, a létesítési profilnak és a megadott üzletági alkalmazásnak ugyanazon a Mac számítógépen kell lennie, amelyet az alkalmazásburkoló eszköz futtatásához használ. Ha a fájlok egy UNC elérési úton vannak, győződjön meg arról, hogy elérhetők a Mac számítógépről. Az elérési utat IPsec- vagy SMB-aláírással védeni kell.

    Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] konzolra importált burkolt alkalmazásnak ugyanazon a számítógépen kell lennie, mint amelyen az eszközt futtatja. Ha a fájl egy UNC elérési úton van, győződjön meg arról, hogy az elérhető az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] konzolt futtató számítógépen. Az elérési utat IPsec- vagy SMB-aláírással védeni kell.

-   IPsec- vagy SMB-aláírással védeni kell azt a környezetet, ahová az alkalmazásburkoló eszközt a Microsoft letöltőközpont webhelyéről letölti.

-   Az Ön által feldolgozott alkalmazásnak megbízható forrásból kell származnia ahhoz, hogy a támadások elleni védelmét biztosítani lehessen.

-   Győződjön meg arról, hogy az alkalmazásburkoló eszközben megadott kimeneti mappa (különösen ha az egy távoli mappa) védett.

-   A fájlfeltöltési párbeszédpanelt tartalmazó iOS-alkalmazások lehetővé tehetik a felhasználóknak, hogy megkerüljék az alkalmazáshoz megadott vágási, másolási és beillesztési korlátozásokat. A felhasználók a fájlfeltöltési párbeszédpanelt használhatják például az alkalmazásadatok képernyőfelvételének feltöltéséhez.

-   Amikor a felhasználók egy burkolt alkalmazásból figyelik az eszközükön lévő dokumentummappát, egy **.msftintuneapplauncher**nevű mappát láthatnak. Ha ez a mappa megváltozott vagy törölték, az hatással lehet a korlátozott alkalmazások megfelelő működésére.

### További információ
- [Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Alkalmazások előkészítése a mobilalkalmazás-felügyeletre az SDK segítségével](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO1-->


