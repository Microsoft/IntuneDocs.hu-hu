---
title: Android-alkalmazások burkolása az Intune Alkalmazásburkoló eszközzel
description: Megtudhatja, hogyan burkolhatja az Android-alkalmazásait anélkül, hogy módosítaná magának az alkalmazásnak a programkódját. Előkészítheti az alkalmazásokat a mobilalkalmazás-felügyeleti szabályzatok alkalmazására.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 732e391ad3c85c1f3f5da36b3424544cf1cdf4aa
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71238788"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Android-alkalmazások előkészítése alkalmazásvédelmi szabályzatokkal való felügyeletre az Intune alkalmazásburkoló eszközével

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

A Microsoft Intune App Wrapping Tool for Android alkalmazásburkoló eszközzel módosíthatja a belső fejlesztésű Android-alkalmazások viselkedését, így az alkalmazások kódjának módosítása nélkül korlátozhatja az alkalmazások funkcióit.

Ez az eszköz egy windowsos parancssori alkalmazás, amely PowerShell-ablakban fut, és „beburkolja” az Android-alkalmazást. Az alkalmazás beburkolását követően az Intune-ban [mobilalkalmazás-kezelési szabályzatok](app-protection-policies.md) konfigurálásával módosíthatja az alkalmazás funkcióit.

Az eszköz futtatása előtt olvassa el a következő cikket: [Az alkalmazásburkoló eszköz futtatásához kapcsolódó biztonsági szempontok](#security-considerations-for-running-the-app-wrapping-tool). Az eszköz letöltéséhez keresse fel a [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) oldalát a GitHubon.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszköz használatára vonatkozó előfeltételek teljesítése

- Az alkalmazásburkoló eszköz futtatásához egy Windows 7 vagy újabb operációs rendszerű Windows-számítógépre van szükség.

- A bemeneti alkalmazásnak .apk kiterjesztésű érvényes Android-alkalmazáscsomagnak kell lennie, továbbá:

  - Nem lehet titkosítva.
  - Nem lehet már beburkolva az Intune App Wrapping Tool segítségével.
  - Android 4.0-s vagy újabb operációs rendszerre kellett készülnie.

- Vállalata által kifejlesztett vagy vállalata számára készült alkalmazásnak kell lennie. Az eszköz nem használható a Google Play áruházból letöltött alkalmazásokkal.

- Az alkalmazásburkoló eszköz futtatásához telepítenie kell a [Java Runtime Environment](https://java.com/download/) legújabb verzióját, majd meg kell bizonyosodnia arról, hogy a Windows környezeti változók között a Java elérési útvonalának a következő van megadva: C:\ProgramData\Oracle\Java\javapath. További segítségért tekintse meg a [Java dokumentációt](https://java.com/download/help/).

    > [!NOTE]
    > Egyes esetekben a Java 32 bites verziója memóriaproblémákat okozhat. Tanácsos a 64 bites verziót telepíteni.

- Az Android megköveteli, hogy minden alkalmazáscsomag (.apk) alá legyen írva. Létező tanúsítványok **újbóli használatához** és az aláíró tanúsítványok teljes útmutatójához lásd: [Aláíró tanúsítványok és burkolóalkalmazások újbóli használata](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps). A keytool.exe végrehajtható Java-eszközzel létrehozhatja a kimeneti burkolt alkalmazás aláírásához szükséges **új** hitelesítő adatokat. Minden beállított jelszónak biztonságosnak kell lennie, de jegyezze fel őket, mert szükség van rájuk az alkalmazásburkoló eszköz futtatásához.

    > [!NOTE]
    > Az Intune alkalmazásburkoló eszköz nem támogatja a Google v2 és hamarosan megjelenő v3 alkalmazás-aláíró sémáit. Miután becsomagolta az .apk fájlt az Intune alkalmazásburkoló eszközzel, javasoljuk, hogy használja a [Google által biztosított Apksigner eszközt]( https://developer.android.com/studio/command-line/apksigner). Ezzel biztosíthatja, hogy miután az alkalmazás eljut a végfelhasználói eszközökre, elindítható legyen az Android szabványoknak megfelelően. 

- Választható Bizonyos esetekben előfordulhat, hogy egy alkalmazás a Dalvik végrehajtható fájl (DEX) korlátját a becsomagolás során hozzáadott Intune MAM SDK-osztályok miatt elérheti. A DEX-fájlok az Android-alkalmazások fordításának részei. Az Intune alkalmazás-burkoló eszköz automatikusan kezeli a Dex-fájl túlcsordulását az alkalmazások csomagolása során a minimális, 21 vagy magasabb szintű API- [val (a v-től). 1.0.2501.1](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android/releases)). A < 21 minimális API-val rendelkező alkalmazások esetében ajánlott eljárás a minimális API-szint megemelése a burkoló `-UseMinAPILevelForNativeMultiDex` jelzője használatával. Ha az ügyfelek nem tudják megemelni az alkalmazás minimális API-szintjét, akkor a következő DEX túlcsordulási megkerülő megoldás érhető el. Bizonyos szervezeteknél előfordulhat, hogy az alkalmazás fordításával (azaz az alkalmazás-Build csapatával) együtt kell működnie:
* Használja a beguard eszközt az alkalmazás elsődleges DEX-fájljából származó nem használt osztályok eltávolításához.
* Az Android Gradle beépülő modul v 3.1.0 vagy újabb verzióját használó ügyfelek esetén tiltsa le a [D8-dexer](https://android-developers.googleblog.com/2018/04/android-studio-switching-to-d8-dexer.html).  

## <a name="install-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszköz telepítése

1. A [GitHub-tárházból](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) egy Windows-számítógépre töltse le az Intune App Wrapping Tool for Android InstallAWT.exe teleptőfájlját. Nyissa meg a telepítőfájlt.

2. Fogadja el a licencszerződést, majd fejezze be a telepítést.

Jegyezze fel a mappa nevét, ahová az eszközt telepítette. Az alapértelmezett hely: C:\Program Files (x86) \Microsoft Intune Mobile Application Management\Android\App burkoló eszköz.

## <a name="run-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszköz futtatása

1. Azon a Windows-számítógépen, amelyre az alkalmazásburkoló eszközt telepítette, egy PowerShell-ablak nyílik meg.

2. Az eszköz telepítési mappájából importálja az alkalmazásburkoló eszköz PowerShell-modulját:

   ```PowerShell
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Az eszközt az **invoke-AppWrappingTool** paranccsal futtathatja, a következő szintaxissal:

   ```PowerShell
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   Az alábbi táblázat az **invoke-AppWrappingTool** parancs tulajdonságait ismerteti:

|Tulajdonság|Információ|Példa|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Az Android-forrásalkalmazás (.apk) elérési útja.| |
 |**-OutputPath**&lt;String&gt;|A „kimeneti” Android-alkalmazás elérési útja. Ha ez megegyezik az InputPath értékével, a burkolás sikertelen lesz.| |
|**-KeyStorePath**&lt;String&gt;|Az aláíráshoz használt nyilvános és titkos kulcsból álló kulcspárt tartalmazó kulcstárfájl elérési útja.|A kulcstárfájlok alapértelmezés szerint a „C:\Program Files (x86)\Java\jreX.X.X_XX\bin” könyvtárban találhatók. |
|**-KeyStorePassword**&lt;SecureString&gt;|A kulcstár visszafejtésére szolgáló jelszó. Az Android elvárja, hogy minden alkalmazáscsomag (.apk) alá legyen írva. A Java keytool segítségével hozza létre a KeyStorePassword kulcsot. További információk a Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) osztályról.| |
|**-KeyAlias**&lt;String&gt;|Az aláíráshoz használt kulcs neve.| |
|**-KeyPassword**&lt;SecureString&gt;|Az aláíráshoz használt titkos kulcs visszafejtésére szolgáló jelszó.| |
|**-SigAlg**&lt;SecureString&gt;| (Nem kötelező) Az aláíráshoz használandó aláírási algoritmus neve. Az algoritmusnak kompatibilisnek kell lennie a titkos kulccsal.|Példák: SHA256withRSA, SHA1withRSA|
|**-UseMinAPILevelForNativeMultiDex**| Választható Ezzel a jelzővel növelheti a forrás Android-alkalmazás minimális API-szintjét 21-re. Ez a jelző megkéri a megerősítést, mert korlátozza, hogy ki és milyen módon telepítheti az alkalmazást. A felhasználók a "-Confirm: $false" paraméternek a PowerShell-parancshoz való hozzáfűzésével hagyhatják el a megerősítő párbeszédpanelt. A jelzőt csak olyan alkalmazások ügyfelei használhatják, amelyek minimális API-val < 21-et használnak, és a DEX túlcsordulási hibái miatt nem sikerült becsomagolni azokat. | |
| **&lt;CommonParameters&gt;** | (Nem kötelező) A parancs támogatja gyakran használt PowerShell-paramétereket, mint például a verbose, a debug stb. |


- A gyakori paraméterek listáját lásd itt: [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Az eszköz használatáról részletes információt olvashat az alábbi parancs használatával:

    ```PowerShell
    Help Invoke-AppWrappingTool
    ```

**Példa:**

Importálja a PowerShell modult.

```PowerShell
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```

Futtassa az alkalmazásburkoló eszközt a HelloWorld.apk natív alkalmazáson.

```PowerShell
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Az eszköz kérni fogja következő információkat: **KeyStorePassword** és **KeyPassword**. Adja meg a kulcstárfájlok létrehozásánál használt hitelesítő adatokat.

Az eszköz generálja a beburkolt alkalmazást, és menti a naplófájllal együtt a megadott kimeneti elérési útra.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>Milyen gyakran érdemes újraburkolni az Android-alkalmazást az Intune alkalmazásburkoló eszközével?
Általában az alábbi esetekben van szükség az alkalmazások újraburkolására:
* Maga az alkalmazás új verzióban jelent meg. Az alkalmazás előző verziója a burkolás után az Intune-konzolba lett feltöltve.
* Az Intune Androidhoz használható alkalmazásburkoló eszközének olyan új verziója jelent meg, amely lehetővé teszi a fontosabb hibajavításokat vagy meghatározott alkalmazásvédelmi szabályzatokkal kapcsolatos Intune-funkciókat. Ilyen új verzió 6-8 hetente jelenik meg, és a [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) GitHub-tárházban érhető el.

Ajánlott eljárások az újraburkoláshoz: 
* A buildelési folyamat során használt aláíró tanúsítványok megtartása – lásd: [Aláíró tanúsítványok és burkolóalkalmazások újbóli használata](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps)

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>Az aláíró tanúsítványok és a burkolóalkalmazások újbóli használata
Az Android minden alkalmazás esetében érvényes tanúsítvánnyal való aláírást követel meg ahhoz, hogy azokat Android-eszközökre lehessen telepíteni.

A beburkolt alkalmazások aláírása elvégezhető a burkolási folyamat részeként, vagy pedig a burkolás *után*, meglévő aláíró eszközökkel (ekkor a rendszer minden, a burkolás előtt az alkalmazásban található aláírási információt elvet). Amennyiben ez lehetséges, az összeállítási folyamatban már felhasznált aláírási információkat kell felhasználni a burkolás során. Egyes szervezetekben elképzelhető, hogy ehhez a kulcstároló tulajdonosával (azaz az alkalmazás-összeállító csapattal) való együttműködés szükséges. 

Ha az előző aláíró tanúsítvány nem használható, vagy ha az alkalmazás korábban még nem lett telepítve, az [Android fejlesztői útmutatójának](https://developer.android.com/studio/publish/app-signing.html#signing-manually) utasításai alapján létrehozhat egy új aláíró tanúsítványt.

Ha az alkalmazás korábban már telepítve lett egy másik aláíró tanúsítvánnyal, az alkalmazást a frissítés után nem lehet feltölteni az Intune-ba. Ha az alkalmazás egy másik tanúsítvánnyal van aláírva, mint amellyel az alkalmazás össze lett állítva, az alkalmazásfrissítési forgatókönyvek megszakadnak. Ennek megfelelően minden új aláíró tanúsítványt karban kell tartani az alkalmazásfrissítésekhez. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Az alkalmazásburkoló eszköz futtatásához kapcsolódó biztonsági szempontok
A lehetséges hamisítási, információfelfedési és a jogok kiterjesztéséből adódó támadások megelőzése érdekében:

- Győződjön meg róla, hogy a bemeneti üzletági (LOB) alkalmazás, a kimeneti alkalmazás és a Java KeyStore ugyanazon a Windows-számítógépen található, ahol az alkalmazásburkoló eszköz fut.

- Importálja a kimeneti alkalmazást az Intune-ba ugyanazon a számítógépen, ahol az eszköz fut. További információ a Java kulcseszközről: [kulcseszköz](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html).

- Ha a kimeneti alkalmazás és az eszköz UNC elérési úton található, és az eszközt és a bemeneti fájlokat nem ugyanazon a számítógépen futtatja, a környezetet az [IPsec](https://wikipedia.org/wiki/IPsec) vagy [SMB-aláírás](https://support.microsoft.com/kb/887429) segítségével teheti biztonságossá.

- Ügyeljen rá, hogy az alkalmazás megbízható forrásból származzon.

- Tegye biztonságossá a beburkolt alkalmazást tartalmazó kimeneti könyvtárat. Fontolja meg a kimeneti oldal számára egy felhasználói szintű könyvtár használatát.

## <a name="see-also"></a>Lásd még:
- [Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal](apps-prepare-mobile-application-management.md)

- [A Microsoft Intune App SDK Androidon – útmutató fejlesztőknek](app-sdk-android.md)
