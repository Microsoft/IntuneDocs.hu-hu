---
# required metadata

title: Android-alkalmazások előkészítése az App Wrapping Tool eszközzel való kezeléshez| Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Android-alkalmazások előkészítése mobilalkalmazás-felügyelethez az Intune App Wrapping Tool eszközével
A **Microsoft Intune App Wrapping Tool for Android** eszköz használatával módosítható a belső fejlesztésű Android-alkalmazások viselkedése, így az alkalmazás kódjának módosítása nélkül állíthatja be annak funkcióit.

Ez az eszköz egy Windows-os parancssori alkalmazás, amely PowerShell ablakban fut, és „beburkolja” az alkalmazást. Az alkalmazás feldolgozását követően az Ön által beállított [mobilalkalmazás-kezelési házirend](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) használatával módosíthatja az alkalmazás funkcióit.

Ha az alkalmazás az Azure Active Directory Authentication Library (ADAL) hitelesítési tárat használja, az alkalmazás burkolása előtt végre kell hajtania az itt leírt lépéseket: [Az Azure Active Directory Authentication Libraryt használó alkalmazások burkolása](#how-to-wrap-apps-that-use-the-azure-active-directory-library). Ha nem biztos abban, hogy alkalmazása használja-e ezt a tárat, lépjen kapcsolatba az alkalmazás fejlesztőjével.

Az eszköz futtatása előtt olvassa el a következő cikket: [Az alkalmazásburkoló eszköz futtatásához kapcsolódó biztonsági szempontok](#security-considerations-for-running-the-app-wrapping-tool). Az eszköz letöltéséhez keresse fel a [Microsoft Intune App Wrapping Tool for Android](https://www.microsoft.com/download/details.aspx?id=47267) weboldalt..

## 1. lépés: Az alkalmazásburkoló eszköz használatára vonatkozó előfeltételek teljesítése

-   Az alkalmazásburkoló eszköz futtatásához egy Windows 7 vagy újabb operációs rendszerrel ellátott Windows számítógépre van szükség.

-   A bemeneti alkalmazásnak érvényes Android alkalmazáscsomagnak kell lennie, amely bővítményfájllal **.apk** rendelkezik, továbbá:

    -   Nem lehet titkosított

    -   Nem lehet már beburkolva az alkalmazásburkoló eszközzel

    -   Android 4.0 vagy újabb operációs rendszerre készült

-   Vállalata által kifejlesztett vagy annak számára készült alkalmazás. Az eszköz nem használható a Google Play áruházból letöltött alkalmazások feldolgozásához.

-   Az alkalmazásburkoló eszköz futtatásához telepítenie kell a [Java Runtime Environment](http://java.com/download/) legújabb verzióját, majd meg kell bizonyosodnia arról, hogy a Windows környezeti változók között a Java elérési útvonalának a következő van megadva: **C:\ProgramData\Oracle\Java\javapath**. További segítségért tekintse meg a következőt: [Java dokumentáció](http://java.com/download/help/)..

    > [!NOTE]
    > Egyes esetekben a Java 32 bites verziója memóriaproblémákat okozhat. Javasoljuk, hogy telepítse a 64 bites verziót.

## 2. lépés: Az alkalmazásburkoló eszköz telepítése

1.  A Microsoft letöltőközpontból töltse le és nyissa meg a Windows-számítógépre készült alkalmazásburkoló eszközhöz tartozó telepítőfájlt.

2.  Fogadja el a licencszerződést, majd fejezze be a telepítést.

Jegyezze fel a mappa nevét, ahová az eszközt telepítette. Az alapértelmezett hely a következő: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**..

## 3. lépés: Az alkalmazásburkoló eszköz futtatása

1.  Azon a Windows-számítógépen, amelyre az alkalmazásburkoló eszközt telepítette, egy PowerShell-ablak nyílik meg.

2.  Az eszköz telepítési mappájából importálja az alkalmazásburkoló eszköz PowerShell-modulját:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Futtassa az eszközt az **invoke-AppWrappingTool** paranccsal, amelyhez az alábbi paraméterek használhatók. Az opcionálisként megjelölt paraméterek az Azure Active Directory Authentication Library (ADAL) tárral működő alkalmazásokhoz használandók. További információ: [Az Azure Active Directory Authentication Libraryt használó alkalmazások burkolása](#how-to-wrap-apps-that-use-the-azure-active-directory-library)..

|Paraméter|További információ|Példák|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Az Android-forrásalkalmazás (.apk) elérési útja.| |
|**-OutputPath**&lt;String&gt;|A „kimeneti” Android-alkalmazás elérési útja. Ha ez megegyezik az InputPath értékével, a burkolás sikertelen lesz.| |
|**-KeyStorePath**&lt;karaktersor&gt;|Az aláíráshoz használt nyilvános és titkos kulcsból álló kulcspárt tartalmazó kulcstárfájl elérési útja.| |
|**-KeyStorePassword**&lt;SecureString&gt;|A kulcstár visszafejtésére szolgáló jelszó.| |
|**-KeyAlias**&lt;String&gt;|Az aláíráshoz használt kulcs neve.| |
|**-KeyPassword**&lt;SecureString&gt;|Az aláíráshoz használt titkos kulcs visszafejtésére szolgáló jelszó.| |
|**-SigAlg**&lt;SecureString&gt;|Az aláíráshoz használandó aláírási algoritmus neve. Az algoritmusnak kompatibilisnek kell lennie a titkos kulccsal.|Példák: SHA256withRSA, SHA1withRSA, MD5withRSA|
|**-ClientID**&lt;GUID&gt;|A bemeneti alkalmazás Azure Active Directory-ügyfél-azonosítója (opcionális).| |
|**-AuthorityURI**&lt;Uri&gt;|A bemeneti alkalmazás Azure Active Directory hitelesítésszolgáltatói URI-je (opcionális).| |
|**-SkipBroker**&lt;Boolean&gt;|Azt jelzi, hogy a bemeneti alkalmazás támogatja-e az eszközre érvényes közvetített egyszeri bejelentkezést (opcionális). |**True** (Igaz) – a bemeneti alkalmazás nem támogatja az eszközre érvényes közvetített egyszeri bejelentkezést. Ebben az esetben használja a NonBrokerRedirectURI paramétert. **False** (Hamis) – a bemeneti alkalmazás támogatja az eszközre érvényes közvetített egyszeri bejelentkezést.|
|**-NonBrokerRedirectURI**&lt;URI&gt;|Az Azure Active Directory használandó átirányítási URI-je, ha a SkipBroker értéke True (Igaz) – opcionális.|  |


**&lt;CommonParameters&gt;**
    (opcionális – olyan gyakori PowerShell-paramétereket támogat, mint például a verbose, a debug stb.)

- A gyakori paraméterek listáját lásd itt: [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx)..

- Az eszközhöz tartozó súgó megtekintéséhez írja be az alábbi parancsot:

    ```
    Help Invoke-AppWrappingTool
    ```
- Ha többet szeretne tudni az Azure Active Directory (AAD) integrációjáról, olvassa el a következő részt: [Az Azure Active Directory Libraryt használó alkalmazások burkolása](#how-to-wrap-apps-that-use-the-azure-active-directory-library)..

**Például:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    Invoke-AppWrappingTool –InputPath <input-app.apk> -OutputPath <output-app.apk> -KeyStorePath <path-to-signing.keystore> -KeyAlias <signing-key-name> -ClientID <xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx> -AuthorityURI <http://AzureActiveDirectory.Authority.URL> -SkipBroker<$True|$False> -NonBrokerRedirectURI <urn:xxx:xx:xxxx:xx:xxx>

A rendszer a következő információkat fogja kérni: **KeyStorePassword** és **KeyPassword**..

A beburkolt alkalmazás létrehozása és mentése egy naplófájllal együtt, a megadott kimeneti elérési úton történik.

## Az alkalmazásburkoló eszköz futtatásához kapcsolódó biztonsági szempontok
A lehetséges hamisítási, információfelfedési és a jogok kiterjesztéséből adódó támadások megelőzése érdekében:

-   Győződjön meg róla, hogy a bemeneti üzletági alkalmazás, a kimeneti alkalmazás és a Java KeyStore ugyanazon számítógépen található, ahol az alkalmazásburkoló eszköz fut.

-   Importálja a kimeneti alkalmazást az Intune-konzolra ugyanazon a számítógépen, ahol az eszköz fut.

-   Ha a kimeneti alkalmazás és az eszköz univerzális elnevezési konvenció (UNC) szerinti elérési útvonalon található, és az eszközt és a bemeneti fájlokat nem ugyanazon a számítógépen futtatja, a környezet biztonságos beállításait az [Internet Protocol Security (IPsec)](http://en.wikipedia.org/wiki/IPsec) vagy a [Server Message Block (SMB) aláírás](https://support.microsoft.com/en-us/kb/887429) használatával adhatja meg..

-   Győződjön meg arról, hogy az alkalmazás megbízható forrásból származik, különösen akkor, ha az Azure Active Directory (AAD) szolgáltatást használja, amely a futtatás ideje alatt hozzáférést biztosíthat az alkalmazás számára az ADD-jogkivonatokhoz.

-   Tegye biztonságossá a beburkolt alkalmazást tartalmazó kimeneti könyvtárat. Fontolja meg a kimeneti oldal számára egy felhasználói szintű könyvtár használatát.

## Az Azure Active Directory Authentication Libraryt használó alkalmazások burkolása
Ha az alkalmazás az Azure Active Directory Authentication Library (ADAL) hitelesítési tárat használja, az alkalmazás burkolása előtt végezze el az alábbi lépéseket.

### 1. lépés: Az ADAL követelményeinek való megfelelés ellenőrzése
Az ADAL tárat használó alkalmazások esetében az alábbiaknak kell teljesülniük:

-   Az alkalmazásnak 1.0.2-es vagy újabb ADAL-verziót kell tartalmaznia.

-   A fejlesztőnek hozzáférést kell biztosítania az alkalmazásnak az Intune mobilalkalmazás-kezelés erőforráshoz a [3. lépés: A mobilalkalmazás-felügyelet elérésének konfigurálása az AAD-ben](#step-3-configure-access-to-mobile-app-management-in-aad) részben leírtak szerint..

### 2. lépés: Az alkalmazás regisztrálásakor kapott azonosítók ellenőrzése
A következő lépésben az Azure felügyeleti portálon kell regisztrálnia az ADAL-t és az Azure Active Directoryt (AAD) használó alkalmazásokat ahhoz, hogy megkapja a következő táblázatban felsorolt egyedi azonosítókat. Az azonosítókat ezután az ADAL és az alkalmazás integrációjához át kell adnia a fejlesztőnek.

|Azonosító|További információ|Alapértelmezett érték|
|--------------|--------------------|-----------------|
|**Ügyfél-azonosító**|Egyedi GUID-azonosító, amelyet a rendszer az AAD-vel való regisztráció után generál az alkalmazás számára.<br /><br />Ha ismeri, adja meg az alkalmazás ügyfél-azonosítóját. Ellenkező esetben használja az alapértelmezett értéket.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**Hitelesítésszolgáltatói URI**|A hitelesítésszolgáltatói egységes erőforrás-azonosító (URI) értéke AAD-objektumokhoz (például felhasználókhoz és csoportokhoz).<br /><br />A hitelesítésszolgáltatói URI paramétert nem kötelező megadni az alkalmazásburkoló eszközhöz. Ha nem adja meg a paramétert, a rendszer az alapértelmezett URI-t használja.||
|**SkipBroker**|Az érték azt jelzi, hogy a rendszer a vállalati portált fogja-e közvetítőként használni.<br /><br />**True** (Igaz) – a rendszer nem a vállalati portált fogja használni az ADAL-hitelesítéshez.<br /><br />**False** (Hamis) – a rendszer a vállalati portált fogja használni az ADAL-hitelesítéshez. A vállalati portál a beléptetett felhasználót használja egyszeri bejelentkezéshez.||
|**Nem közvetített átirányítási URI**|Ezt a bejelentkezési azonosítót kell használni, ha az ADAL nem használja a közvetítőalkalmazást (az Intune vállalati portált).|urn:ietf:wg:oauth:2.0:oob|
|**Erőforrás-azonosító**|Az alkalmazás AAD-erőforrásaira mutat.||

### 3. lépés: A mobilalkalmazás-felügyelet elérésének konfigurálása az AAD-ben
Mielőtt használhatná egy alkalmazás AAD-beli regisztrációs értékeit az alkalmazásburkoló eszközben, az alkalmazás fejlesztőjének hozzáférést kell adnia az alkalmazásnak az Intune mobilalkalmazás-kezelés erőforráshoz. Ehhez végezze el a következő lépéseket:

1.  Jelentkezzen be egy meglévő AAD-fiókba az Azure felügyeleti portálján.

2.  Válassza az **existing LOB application registration**(meglévő LOB-alkalmazás regisztrációja) elemet..

3.  A **configure** (konfigurálás) csoportban válassza a **Configure Access to Web APIs in other applications** (Webes API-k más alkalmazásokban való elérésének konfigurálása) lehetőséget..

4.  A **Permission to other applications** (Engedélyek más alkalmazásoknak) csoport első legördülő listájából válassza az **Intune Mobile Application Management** (Intune mobilalkalmazás-kezelés) lehetőséget..

Ezután már használhatja az alkalmazás ügyfél-azonosítóját az alkalmazásburkoló eszközben. Az ügyfél-azonosító az Azure Active Directory felügyeleti portálon található – lásd a táblázatot itt: [2. lépés: Az alkalmazás regisztrálásakor kapott azonosítók ellenőrzése](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app)..

### 4. lépés: Az AAD-azonosítóértékek használata az alkalmazásburkoló eszközben
A regisztrációs folyamat során kapott azonosítóértékeket adja meg parancssori tulajdonságként az alkalmazásburkoló eszközben. A táblázatban szereplő összes értéket meg kell adnia ahhoz, hogy a felhasználók sikeresen hitelesítsék az alkalmazást. Ha nem adja meg valamelyiket, a rendszer az alapértelmezett értéket fogja használni.

|Azonosító|Paraméter|
|--------------|-------------|
|Ügyfél-azonosító|ClientID|
|Hitelesítésszolgáltatói URI|Authority-URI|
|SkipBroker (Nincs közvetítés)|SkipBroker|
|Nem közvetített átirányítási URI|NonBrokerRedirectURI|
|Erőforrás-azonosító|ResourceID|
Az alkalmazás burkolásakor tartsa szem előtt a következőket:

-   Az alkalmazásburkoló eszköz nem keres ADAL bináris fájlokat (ha vannak) az alkalmazásban. Ha az alkalmazás a bináris fájlok elavult verziójára hivatkozik, és hitelesítési házirendek vannak engedélyezve, a bejelentkezés során futásidejű hibák jelentkezhetnek.

-   A hitelesítés sikerességének ellenőrzéséhez az
  [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] lekéri a MAM-erőforrás-azonosítóhoz társított AAD-tokent. A rendszer ugyanakkor nem használja a tokent semmilyen hívásban, amely a token érvényességének ellenőrzésére szolgálna. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] csak a bejelentkezett felhasználó egyszerű felhasználónevét olvassa be az alkalmazás általi hozzáférés megállapításához. Az AAD token nem használatos a további szolgáltatáshívásokhoz.

-   A hitelesítési tokenek az egy kiadótól származó alkalmazások esetén azonosak, tárolások ugyanis közös kulcsláncban történik. Ha el szeretne különíteni egy adott alkalmazást, másik aláíró tanúsítványt, létesítésiprofil-kulcstárat és -kulcsaliast kell használnia hozzá.

-   Az alkalmazás ügyfél-azonosítójának és hitelesítésszolgáltatói URI-jének megadásával megelőzhetők az ismétlődő bejelentkezéskérések. Az AAD-irányítópulton a közzétett [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM-erőforrás-azonosítóhoz való hozzáféréshez regisztrálnia kell az ügyfél-azonosítót. Ha nem regisztrálja az ügyfél-azonosítót, az alkalmazás futtatásakor a felhasználónál bejelentkezési hiba fog történni.


### További információ
- [Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Alkalmazások előkészítése a mobilalkalmazás-felügyeletre az SDK segítségével](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO1-->


