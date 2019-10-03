---
title: A Microsoft Intune App SDK Androidon – útmutató fejlesztőknek
description: Az Androidhoz készült Microsoft Intune App SDK lehetővé teszi, hogy az Intune mobilalkalmazás-felügyeleti (MAM) funkcióját beépítse Android-alkalmazásaiba.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1d1d0c52db57ca6b41c399aeefc948735eea0af
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830528"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>A Microsoft Intune App SDK Androidon – útmutató fejlesztőknek

> [!NOTE]
> Kezdésként érdemes lehet elolvasni [Az Intune APP SDK áttekintése](app-sdk.md) című cikket, amely ismerteti az SDK aktuálisan elérhető funkcióit, valamint az integrációval kapcsolatos előkészületeket a támogatott platformokon.

Az Androidhoz készült Microsoft Intune App SDK révén Intune-os alkalmazásvédelmi szabályzatokat (más néven **APP**- vagy MAM-szabályzatokat) építhet be natív Android-alkalmazásába. Intune által kezeltnek az Intune App SDK-val integrált alkalmazásokat nevezzük. A rendszergazdák egyszerűen telepíthetnek alkalmazásvédelmi szabályzatokat az Intune által kezelt alkalmazáshoz, ha az Intune aktívan felügyeli az alkalmazást.


## <a name="whats-in-the-sdk"></a>Az SDK tartalma

Az Intune App SDK-ban a következő fájlok találhatók:

* **Microsoft.Intune.MAM.SDK.aar**: Az SDK-összetevők, kivéve a támogatási függvénytár JAR-fájljait.
* **Microsoft.Intune.MAM.SDK.Supp, vagy egyt.v4.jar**: Az Android v4 támogatási függvénytárat használó alkalmazásokban a MAM engedélyezéséhez szükséges osztályok.
* **Microsoft.Intune.MAM.SDK.Supp, vagy egyt.v7.jar**: Az Android v7 támogatási függvénytárat használó alkalmazásokban a MAM engedélyezéséhez szükséges osztályok.
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: Az Android v17 támogató függvénytárat használó alkalmazásokban a MAM engedélyezéséhez szükséges osztályok. 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: A MAM olyan alkalmazásokban való engedélyezéséhez szükséges osztályok, amelyek az Android támogatási függvénytár `android.support.text` osztályait használják a csomagban.
* **Microsoft. Intune. Mam. SDK. DownlevelStubs. éves csomag**: Ez az éves tevékenység azokat az Android-rendszerosztályokat tartalmazza, amelyek csak az újabb eszközökön szerepelnek, de a `MAMActivity` metódusok hivatkoznak rá. Az újabb eszközök figyelmen kívül hagyják ezeket az osztálycsonkokat. Ez az éves tevékenység csak abban az esetben szükséges, ha az alkalmazás a `MAMActivity` értékből származtatott osztályokra vonatkozó reflexiót hajt végre, és a legtöbb alkalmazásnak nem kell tartalmaznia. Az éves tevékenység az összes osztálya kizárására szolgáló rendszerállapot-szabályokat tartalmaz.
* **com.microsoft.intune.mam.build.jar**: A Gradle beépülő modul [, amely az SDK integrálását segíti elő](#build-tooling).
* **Changelog. txt**: Az egyes SDK-verziókban végrehajtott módosítások rekordját adja meg.
* **THIRDPARTYNOTICES. TXT**:  Az alkalmazásba lefordított, harmadik féltől származó és/vagy OSS-kódot igazoló jóváírási értesítés.

## <a name="requirements"></a>Követelmények

### <a name="android-versions"></a>Android-verziók
Az SDK az Android API 19 (Android 4.4 +) használatát támogatja az Android API 28 használatával (Android 9,0).

### <a name="company-portal-app"></a>Vállalati portál alkalmazás
Az androidos Intune App SDK a [Céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) alkalmazással teszi lehetővé az alkalmazásvédelmi szabályzatok működését. A Céges portál az Intune szolgáltatástól kéri le az alkalmazásvédelmi szabályzatokat. Az alkalmazás az inicializáláskor betölti a Céges portálról a szabályzatot és a betartatásához szükséges kódot.

> [!NOTE]
> Ha a Céges portál alkalmazás nincs telepítve az eszközre, akkor az Intune által kezelt alkalmazás ugyanúgy működik, mint az általános, az Intune alkalmazásvédelmi szabályzatait nem támogató alkalmazások.

Az eszközregisztráció nélküli alkalmazásvédelem esetében a felhasználónak _**nem**_ kell regisztrálnia az eszközt a Céges portál alkalmazással.

## <a name="sdk-integration"></a>SDK-integráció

### <a name="sample-app"></a>Minta alkalmazás
Az Intune app SDK-val való integrálásának példája a [githubon](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) érhető el. Ez a példa a [Gradle Build beépülő modult](#gradle-build-plugin)használja.

### <a name="referencing-intune-app-libraries"></a>Hivatkozás Intune App-kódtárakra

Az Intune App SDK for Android egy szabványos, külső függőségek nélküli androidos függvénytár. A **Microsoft.Intune.MAM.SDK.aar**-ban megvannak mind az alkalmazásvédelmi szabályzatok használatát lehetővé tevő interfészek, mind pedig a Microsoft Intune Céges portál alkalmazással való együttműködéshez szükséges kód.

A **Microsoft.Intune.MAM.SDK.aar**-t androidos függvénytár-hivatkozásként kell megadni. Ehhez nyissa meg az alkalmazásprojektet az Android Studióban, válassza a **File > New > New module** (Fájl > Új > Új modul), majd az **Import .JAR/.AAR Package** (.JAR-/.AAR-csomag importálása) elemet. Ezután válassza ki a Microsoft. Intune. MAM. SDK. az androidos archív csomagot a modul létrehozásához. AAR. Kattintson a jobb gombbal az alkalmazáskódot tartalmazó modulra vagy modulokra, válassza a **Module Settings (Modul beállításai)**  > **Dependencies (Függőségek)**  >  **+ ikon** > **Module dependency (Modulfüggőség)** lehetőséget, adja meg a most létrehozott MAM SDK AAR-modult, és végül kattintson az **OK** gombra. Ezzel biztosíthatja, hogy a modul a MAM SDK-val forduljon le a projekt buildelésekor.

Ezenkívül a **Microsoft.Intune.MAM.SDK.Support.XXX.jar** kódtárak tartalmazzák a megfelelő `android.support.XXX` kódtárak Intune-változatait. Ezek nem kerültek bele a Microsoft.Intune.MAM.SDK.aar-ba, arra az esetre, ha egy alkalmazásnak nem kell függenie a támogatási kódtáraktól.

#### <a name="proguard"></a>ProGuard

Ha fordítási lépésként a [ProGuard](http://proguard.sourceforge.net/) (vagy bármely más zsugorítási/rejtjelezési mechanizmus) használt, az SDK olyan további konfigurációs szabályokkal rendelkezik, amelyeket fordításkor bele kell foglalni. A-t is beleértve. A buildben a szabályok automatikusan integrálva vannak a bevezetési lépésbe, és megőrzik a szükséges osztály-fájlokat.

Az Azure Active Directory Authentication Libraries (ADAL) szolgáltatásnak saját ProGuard-korlátozásai lehetnek. Ha az Ön alkalmazása az ADAL-lal van integrálva, ezen korlátozások tekintetében az ADAL dokumentációja a mérvadó.

### <a name="policy-enforcement"></a>Házirendek érvényesítése
Az Intune App SDK egy androidos függvénytár, amely lehetővé teszi, hogy az alkalmazás támogassa az Intune-szabályzatokat, és részt vegyen azok kikényszerítésében. 

A legtöbb szabályzatot a rendszer félig automatikusan kényszeríti, de bizonyos szabályzatok az [alkalmazástól való kifejezett részvételt](#enable-features-that-require-app-participation)igénylik.
Függetlenül attól, hogy elvégezte-e a forrás-integrációt, vagy használja az integrációs eszközöket a kifejezetten részvételt igénylő szabályzatok használatához.

Az automatikusan érvényesített házirendek esetében az alkalmazásoknak több androidos alaposztályból származó öröklést kell cserélniük a MAM-vel egyenértékű örökléssel. A szükséges speciális cserék [alább](#class-and-method-replacements) láthatók, és manuálisan is elvégezhetők a forrás-integrációval, vagy automatikusan elvégezhető a Build-eszközökön keresztül.

### <a name="build-tooling"></a>Build-eszközök
Az SDK Build-eszközöket (a Gradle-buildek beépülő modulját és a nem Gradle-buildekhez készült parancssori eszközt) biztosít, amelyekkel a rendszer automatikusan végrehajtja a MAM-alapú helyettesítő kihelyezéseket. Ezek az eszközök átalakítják a Java-fordítással létrehozott osztályfájlokat, és nem módosítják az eredeti forráskódot.

Az eszközök csak [közvetlen cseréket](#class-and-method-replacements) hajtanak végre. Bonyolultabb SDK-integrációkat, például [Mentés másként szabályzatot](#enable-features-that-require-app-participation), [Többszörös identitást](#multi-identity-optional), [App-WE-regisztrációt](#app-protection-policy-without-device-enrollment), [AndroidManifest-módosításokat](#manifest-replacements) vagy [ADAL-konfigurációt](#configure-azure-active-directory-authentication-library-adal) nem hajtanak végre, ezért ezeket még azelőtt kell elvégezni, mielőtt az alkalmazás teljesen engedélyezve lenne az Intune-ban. Olvassa el figyelmesen a dokumentáció többi részét az alkalmazás szempontjából releváns integrációs pontok megtalálásához.

> [!NOTE]
> Az eszközöket lehet olyan projekten is futtatni, amelyen manuális cserékkel már végrehajtották a MAM SDK részleges vagy teljes forrásintegrációját. A projektnek továbbra is függőségként kell listáznia a MAM SDK-t.

### <a name="gradle-build-plugin"></a>Gradle-build beépülő modul
Ha az alkalmazás nem jön létre a Gradle-lel, ugorjon az [Integrálása a parancssori eszközzel](#command-line-build-tool) szakaszra. 

Az App SDK beépülő modul terjesztése az SDK részeként történik a **GradlePlugin/com.microsoft.intune.mam.build.jar** fájlban. A Gradle csak akkor tudja megtalálni a beépülő modult, ha az hozzá van adva a buildscript classpath sorhoz. A beépülő modul a [Javassist](https://jboss-javassist.github.io/javassist/) eszközkészlettől függ, amelyet szintén fel kell venni. Ezeknek a classpath sorhoz adásához, adja hozzá a következőt a gyökérhez: `build.gradle`

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

Ezt követően az APK-projekt `build.gradle` fájljában egyszerűen alkalmazza a beépülő modult az alább módon:
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

Alapértelmezés szerint a beépülő modul **csak** a `project` függőségein fog működni.
A tesztfordítást nem érinti. Megadhat konfigurációt az alábbiak listázásához:
*  Kizárandó projektek
*  [Kizárandó külső függőségek](#usage-of-includeexternallibraries) 
*  Meghatározott osztályok a feldolgozásból való kizáráshoz
*  Változók a feldolgozásból való kizáráshoz. Ezek vonatkozhatnak a teljes változónévre vagy egyetlen ízre. Példa:
     * Ha az alkalmazás rendelkezik `debug` és `release` buildtípussal {`savory`, `sweet`} és {`vanilla` ízekkel, `chocolate`} akkor megadhatja, hogy
     * `savory` az összes sós ízű változó kizárásához, vagy megadhatja a `savoryVanillaRelease` értéket pontosan ennek az változónak a kizárásához.

#### <a name="example-partial-buildgradle"></a>Részleges példa: build.gradle

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"
    implementation "com.microsoft.qux:foo:2.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}
```

Ennek a hatása a következő lesz:
* A `:product:FooLib` nincs újraírva, mert azt az `excludeProjects` tartalmazza.
* A `:product:foo-project` újra van írva, kivéve a `com.contoso.SplashActivity` osztályt, ami ki van hagyva, mert azt az `excludeClasses` tartalmazza.
* A `bar.jar` újra van írva, mert azt az `includeExternalLibraries` tartalmazza.
* A `zap.jar`**nics** újraírva, mert az nem projekt, és azt az `includeExternalLibraries` nem tartalmazza.
* A `com.contoso.foo:zap-artifact:1.0.0` újra van írva, mert azt az `includeExternalLibraries` tartalmazza.
* A `com.microsoft.bar:baz:1.0.0` újra van írva, mert azt az `includeExternalLibraries` tartalmazza egy helyettesítő karakteren keresztül (`com.microsoft.*`).
* `com.microsoft.qux:foo:2.0`a nem íródik újra, annak ellenére, hogy az megegyezik az előző elemmel megegyező helyettesítő karakterrel, mert az explicit módon ki van zárva egy tagadási mintával.

#### <a name="usage-of-includeexternallibraries"></a>Az IncludeExternalLibraries használata

Mivel a beépülő modul csak projektfüggőségeken működik (amit általában a `project()` függvény biztosít) alapértelmezés szerint a `fileTree(...)` által megadott vagy a maven vagy egyéb csomagforrásból (például „`com.contoso.bar:baz:1.2.0`”) származó minden függőséget meg kell adni az `includeExternalLibraries` tulajdonság számára, ha ezeknek a MAM általi feldolgozása az alábbiakban leírt feltételek alapján szükséges. Helyettesítő karakterek (*) használhatók. A-től kezdődő `!` elemek nem vonhatók le, és olyan könyvtárak kizárására használhatók, amelyek egyébként helyettesítő karakterrel is rendelkezhetnek.

Ha külső függőségeket ad meg munkadarab-jelöléssel, akkor javasolt kihagyni a verzió-összetevőt az `includeExternalLibraries` értékéből. Ha belefoglalja a verziót, akkor annak pontos verziónak kell lennie. A dinamikus verziómegadások (pl. `1.+`) nem megengedettek.

Azt, hogy bele kell-e foglalnia a függvénytárakat az `includeExternalLibraries` sorba, általános szabályként két kérdés alapján döntheti el:
1. Tartalmaz a függvénytár olyan osztályokat, amelyhez rendelkezésre állnak MAM-megfelelők? Példák: `Activity`, `Fragment`, `ContentProvider`, `Service` stb.
2. Ha igen, használja az alkalmazás ezeket az osztályokat?

Ha mindkét kérdésre „igen” a válasz, akkor azt a függvénytárat bele kell foglalnia az `includeExternalLibraries` sorba. 

| Forgatókönyv | Tartalmaznia kell? |
|--|--|
| Belefoglal egy PDF-megtekintő függvénytárat az alkalmazásába, és a megtekintő `Activity` tevékenységét használja az alkalmazásban, amikor a felhasználók PDF-eket próbálnak megtekinteni | Igen |
| A továbbfejlesztett webes teljesítmény érdekében belefoglal egy HTTP-függvénytárat az alkalmazásába | Nem |
| Belefoglal egy olyan függvénytárat, mint a React Native, amely az `Activity`, az `Application` és a `Fragment` elemekből származtatott osztályokat tartalmaz, és felhasználja ezeket az osztályokat, vagy további származtatást végez belőlük az alkalmazásában | Igen |
| Belefoglal egy olyan függvénytárat, mint a React Native, amely az `Activity`, az `Application` és a `Fragment` elemekből származtatott osztályokat tartalmaz, de csak statikus segédeket vagy segédprogramosztályokat használ | Nem |
| Belefoglal egy olyan függvénytárat, amely a `TextView` osztályból származtatott megtekintési osztályokat tartalmaz, és felhasználja ezeket az osztályokat, vagy további származtatást végez belőlük az alkalmazásában | Igen |

#### <a name="reporting"></a>Jelentéskészítés
A Build beépülő modul létre tud hozni egy HTML-jelentést az általa végrehajtott változásokról. A jelentés létrehozásához a `report = true` `intunemam` konfigurációs blokkban kell megadni. Ha létrejött, a jelentés `outputs/logs` a Build könyvtárba kerül.

```groovy
intunemam {
    report = true
}
```

#### <a name="verification"></a>Ellenőrzés
A Build beépülő modul további ellenőrzéseket is futtathat, hogy megkeresse a lehetséges hibákat a feldolgozási osztályokban. A kéréshez a `intunemam` konfigurációs blokkban `verify = true` értéket kell megadnia. Vegye figyelembe, hogy ez több másodpercig is eltarthat, amíg a beépülő modul feladatát elvégezte.

```groovy
intunemam {
    verify = true
}
```

#### <a name="incremental-builds"></a>Növekményes buildek
A növekményes létrehozás támogatásának engedélyezéséhez a `intunemam` konfigurációs blokkban `incremental = true` értéket kell megadnia.  Ez egy kísérleti funkció, amelynek célja, hogy csak a módosított bemeneti fájlok feldolgozásával növelje a teljesítményt.  Az alapértelmezett konfiguráció a `false`.

```groovy
intunemam {
    incremental = true
}
```

#### <a name="dependencies"></a>Függőségek

A Gradle beépülő modul függőségben van a [Javassist](https://jboss-javassist.github.io/javassist/) eszközkészlettől, amelynek elérhetőnek kell lennie a Gradle számára a függőségfeloldáshoz (a fent leírtaknak megfelelően). A Javassist használata kizárólag a fordítás idején történik a beépülő modul futtatásakor. Az alkalmazáshoz nem lesz hozzáadva Javassist-kód.

> [!NOTE] 
> Az Android Gradle beépülő modul 3.0-s vagy újabb verzióját és a Gradle 4.1-es vagy újabb verzióját kell használnia.

### <a name="command-line-build-tool"></a>Parancssori fordítóeszköz
Ha a build a Gradle-t használja, ugorjon a [következő szakaszra](#class-and-method-replacements).

A parancssori fordítóeszköz az SDK-letöltés `BuildTool` mappájában található. Ugyanazt a feladatot látja el, mint a fent részletezett Gradle beépülő modul, de integrálható egyéni vagy nem Gradle build-rendszerekbe. Mivel ez generikusabb, nehezebb meghívni, ezért, ha lehetséges a Gradle beépülő modul használata javasolt.

#### <a name="using-the-command-line-tool"></a>A parancssori eszköz használata

A parancssori eszközt a megadott segítő parancsfájlokkal lehet meghívni, amelyek a `BuildTool\bin` könyvtárban találhatók.

Az eszköz a következő paramétereket várja.

| Paraméter | Leírás |
| -- | -- |
| `--input` | A módosításra váró osztályfájlok jar-fájljainak és könyvtárainak pontosvesszővel tagolt listája. Ennek tartalmaznia kell minden olyan jar-fájlt és könyvtárat, amelyet felül szeretne írni. |
| `--output` | A módosított osztályok tárolására szolgáló jar-fájlok és könyvtárak pontosvesszővel tagolt listája. Bemeneti bejegyzésenként egy kimeneti bejegyzésnek kell lennie, és ezeket sorrendben kell listázni. |
| `--classpath` | A build osztályútvonala. Ez tartalmazhat jar-fájlokat és osztálykönyvtárakat is. |
| `--excludeClasses`| Egy pontosvesszővel tagolt lista, amely tartalmazza azoknak az osztályoknak a nevét, amelyeket ki kell zárni az újraírásból. |

Az összes paramétert meg kell adni, kivéve az `--excludeClasses` paramétert, amely nem kötelező.

> [!NOTE]
> A UNIX-hoz hasonló rendszerekben a pontosvessző a parancs elválasztója. Ha el szeretné kerülni, hogy a rendszerhéj el tudja végezni a parancsok felosztását, ügyeljen arra, hogy az egyes pontosvesszőket a "@no__t – 0, vagy a teljes paramétert idézőjelek közé zárja.

#### <a name="example-command-line-tool-invocation"></a>Példa a parancssori eszköz meghívására

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Ennek a hatása a következő lesz:

* A `product-foo-project` könyvtár át lesz írva erre: `mam-build\product-foo-project`
* A `bar.jar` át lesz írva erre: `mam-build\libs\bar.jar`
* A `zap.jar`**nincs** átírva, mert az csak a `--classpath` listában van felsorolva
* A `com.contoso.SplashActivity` osztály **nincs** átírva, még akkor sem, ha az `--input` paraméterben van

> [!NOTE] 
> A build-eszköz jelenleg nem támogatja az aar-fájlokat. Ha a build-rendszer nem bontja ki a `classes.jar` fájlt az aar-fájlok feldolgozásakor, akkor ezt Önnek kell megtennie a build-eszköz meghívása előtt.


## <a name="class-and-method-replacements"></a>Osztályok és metódusok lecserélése

Az Intune-felügyelet engedélyezéséhez az androidos alaposztályokat a MAM-megfelelőjükkel kell helyettesíteni. Az SDK-osztályok az androidos alaposztály és az alkalmazás saját származtatott verziója között helyezkednek el. Alkalmazástevékenységek esetében ez például egy, az alábbihoz hasonló öröklési hierarchiát eredményez: `Activity` > `MAMActivity` >
`AppSpecificActivity`. A MAM-réteg szűrői rendszerműveleteket hívnak, hogy zökkenőmentesen biztosíthassák az alkalmazása számára a felügyelt nézetet.

Az alaposztályokon kívül bizonyos osztályokat az alkalmazás származtatás nélkül használhat (pl. `MediaPlayer`), ezenkívül kötelező MAM-megfelelőkkel is rendelkezik, és [bizonyos metódushívásokat szintén le kell cserélni](#wrapped-system-services). A pontos részletek az alábbiak.

> [!NOTE] 
> Ha az alkalmazás integrálva van az SDK [Build-eszközökkel](#build-tooling), a következő osztály-és metódus-cserék automatikusan elvégzik.

| Androidos alaposztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (lásd: [PendingIntent](#pendingintent)) |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (csak akkor szükséges, ha a Binder létrehozása nem androidos interfészdefiníciós nyelvű (AIDL-) interfészből történik) |
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.AutoCompleteTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Még ha az alkalmazásának nincs is szüksége saját, származtatott `Application` osztályra, [lásd `MAMApplication` alább](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| Android.support.v4.App.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| Android.support.v4.App.TaskStackBuilder | MAMTaskStackBuilder
| Android.support.v4.Content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Átnevezett metódusok
Sok esetben az androidos osztályban rendelkezésre álló metódus végsőként van megjelölve a helyettesítő MAM-osztályban. Ebben az esetben a helyettesítő MAM-osztály egy hasonlóan elnevezett metódust biztosít (általában a `MAM` utótaggal), amelyet felül kell írni. Így például a `MAMActivity` származtatásakor az `onCreate()` felülírása, illetve a `super.onCreate()` metódus hívása helyett az `Activity` tevékenységnek felül kell írnia az `onMAMCreate()` metódust, és meg kell hívnia a `super.onMAMCreate()` metódust. A Java-fordítónak érvényesítenie kell a végső korlátozásokat az eredeti metódus véletlen felülbírálásának elkerülése érdekében az egyenértékű MAM-metódus helyett.

### <a name="mamapplication"></a>MAMApplication
Ha az alkalmazása létrehozza az `android.app.Application` osztály egy alosztályát, akkor ehelyett **mindenképp** a `com.microsoft.intune.mam.client.app.MAMApplication` osztályból kell alosztályt létrehoznia. Ha az alkalmazása nem hoz létre alosztályt az `android.app.Application` osztályból, akkor **mindenképp** be kell állítania a `"com.microsoft.intune.mam.client.app.MAMApplication"` osztályt az `"android:name"` attribútumként az AndroidManifest.xml fájl `<application>` címkéjénél.

### <a name="pendingintent"></a>PendingIntent
A `PendingIntent.get*` helyett például a `MAMPendingIntent.get*` metódust kell használni. Az így létrejövő `PendingIntent` már szintén a megszokott módon használható.

### <a name="wrapped-system-services"></a>Burkolt rendszerszolgáltatások
Néhány rendszerszolgáltatási osztály esetében statikus metódushívás szükséges a MAM-burkolóosztályon a kívánt metódusnak közvetlenül a szolgáltatáspéldányon történő hívása helyett. A `getSystemService(ClipboardManager.class).getPrimaryClip()` hívásának például a `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)` hívásává kell alakulnia. Ezeknek a cseréknek a manuális végrehajtása nem javasolt. Ehelyett hagyja, hogy ezeket a BuildPlugin hajtsa végre.

| Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| Android. View. View | MAMViewManagement |
| Android. View. DragEvent | MAMDragEventManagement |
| Android. app. NotificationManager | MAMNotificationManagement |
| Android. support. v4. app. NotificationManagerCompat | MAMNotificationCompatManagement |

Egyes osztályok a legtöbb módszerét beburkolták, például `ClipboardManager`, `ContentProviderClient`, `ContentResolver` és `PackageManager`, míg más osztályok esetében csak egy vagy két módszer van becsomagolva, például `DownloadManager`, `PrintManager`, `PrintHelper`, `View`, `DragEvent`, `NotificationManager` és 0. Ha nem használja a BuildPlugin, tekintse meg a MAM-vel egyenértékű osztályok által elérhető API-kat a pontos módszerhez.

### <a name="manifest-replacements"></a>Cserék a jegyzékben
Lehetséges, hogy a fenti osztálycserék egy részét a jegyzékfájlban és a Java-kódban is el kell végezni. Különösen fontos:
* a jegyzékfájlban szereplő `android.support.v4.content.FileProvider`-hivatkozásokat le kell cserélni erre: `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>AndroidX függvénytárak
A Google az Android P-vel egy új (átnevezett) támogatási függvénytárhalmazt jelentett be, amelynek a neve AndroidX, és a 28-as verzió a meglévő android.support függvénytárak legújabb fő kiadása.

Az androidos támogatási függvénytáraktól eltérően az AndroidX függvénytárakhoz nem biztosítunk MAM-változókat. Ehelyett az AndroidX függvénytárat ugyanúgy kell kezelni, mint bármely más függvénytárat, és úgy kell konfigurálni, hogy átírja a build beépülő modulja/eszköze. A Gradle buildjeinek esetében ezt meg lehet tenni az `androidx.*` változónak a beépülő modul konfigurációjának `includeExternalLibraries` mezőjébe történő belefoglalásával. A parancssori eszköz indításainak kifejezetten listázniuk kell az összes jar-fájlt.

### <a name="pre-androidx-architecture-components"></a>AndroidX előtti architektúra-összetevők
Számos androidos architektúra-összetevő, például a Room, a ViewModel és a WorkManager újracsomagolták a AndroidX. Ha az alkalmazás ezen könyvtárak előre AndroidX változatait használja, győződjön meg arról, hogy az újraírások érvényesek, beleértve a `android.arch.*` értéket a beépülő modul konfigurációjának `includeExternalLibraries` mezőjében. Azt is megteheti, hogy frissíti a kódtárakat a AndroidX megfelelő értékekkel.

## <a name="sdk-permissions"></a>Az SDK engedélyei

Az Intune App SDK három [androidos rendszerengedélyt](https://developer.android.com/guide/topics/security/permissions.html) igényel azokhoz az alkalmazásokhoz, amelyekbe beépül:

* `android.permission.GET_ACCOUNTS` (kérése futásidőben történik, ha szükség van rá)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Az Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) a közvetített hitelesítés végrehajtásához igényli ezeket az engedélyeket. Ha az alkalmazás nem kapja meg ezeket az engedélyeket, vagy ha a felhasználó visszavonja ezeket az engedélyeket, akkor a közvetítőt igénylő hitelesítési folyamatok (a Munkahelyi portál alkalmazás) le lesznek tiltva.

## <a name="logging"></a>Naplózás

A naplózott adatok maximális hasznossága érdekében a naplózást célszerű korán inicializálni. Erre az `Application.onMAMCreate()` a legalkalmasabb hely.

Ha az alkalmazásban MSM-naplókat szeretne fogadni, hozzon létre [Java-kezelőt](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html), és vegye fel a `MAMLogHandlerWrapper`-be. Ez minden naplóüzenetre meghívja a `publish()` metódust az alkalmazás kezelőjén.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```

## <a name="enable-features-that-require-app-participation"></a>Alkalmazás részvételét igénylő szolgáltatások engedélyezése

Az SDK számos alkalmazásvédelmi szabályzatot nem tud önállóan implementálni. Az alkalmazás a saját működésének szabályozásával képes e funkciókat biztosítani. Ehhez több API-t használ, amelyek az alábbi `AppPolicy` felületen találhatók. Egy `AppPolicy`-példány beolvasásához használja a `MAMPolicyManager.getPolicy`-t.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
  * This function is now deprecated. Use getIsSaveToLocationAllowed(SaveLocation, String) instead
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows taking screenshots.
 *
 * @return True if screenshots will be blocked, false otherwise
 */
boolean getIsScreenCaptureAllowed();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Get the notification restriction. If {@link NotificationRestriction#BLOCKED BLOCKED}, the app must not show any notifications
 * for the user associated with this policy. If {@link NotificationRestriction#BLOCK_ORG_DATA BLOCK_ORG_DATA}, the app must show
 * a modified notification that does not contain organization data. If {@link NotificationRestriction#UNRESTRICTED
 * UNRESTRICTED}, all notifications are allowed.
 *
 * @return The notification restriction.
 */
NotificationRestriction getNotificationRestriction();

/**
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether file encryption is in use.
 * File encryption is transparent to the app and the app should not need to make any business logic decisions based on this.
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> A `MAMPolicyManager.getPolicy` mindig nem null értékű alkalmazásszabályzatot ad vissza – akkor is, ha az eszközre vagy az alkalmazásra nem vonatkozik Intune-beli felügyeleti szabályzat.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Példa: Annak megállapítása, hogy szükséges-e PIN-kód az alkalmazáshoz

Ha az alkalmazásnak saját felhasználói PIN-kódkezelő funkciója van, akkor azt célszerű letiltani, ha a rendszergazda úgy állította be az SDK-t, hogy az kérjen alkalmazás-PIN-kódot. Az alábbi metódust meghívva állapíthatja meg, hogy a rendszergazda telepített-e alkalmazás-PIN-szabályzatot az alkalmazáshoz az aktuális végfelhasználónál:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Példa: Annak megállapítása, hogy szükséges-e PIN-kód az alkalmazáshoz

Ha az alkalmazásnak saját felhasználói PIN-kódkezelő funkciója van, akkor azt célszerű letiltani, ha a rendszergazda úgy állította be az SDK-t, hogy az kérjen alkalmazás-PIN-kódot. Az alábbi metódust meghívva állapíthatja meg, hogy a rendszergazda telepített-e alkalmazás-PIN-szabályzatot az alkalmazáshoz az aktuális végfelhasználónál:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Példa: Az elsődleges Intune-felhasználó meghatározása

Az egyszerű felhasználónevet (**UPN**) az AppPolicy-ban elérhető API-kon felül a `MAMUserInfo` interfészben definiált `getPrimaryUser()` API is elérhetővé teszi. Az UPN-t az alábbi kódot meghívva kérheti le:

```java
MAMComponents.get(MAMUserInfo.class).getPrimaryUser();
```

Alább a MAMUserInfo interfész teljes definiálása olvasható:

```java
/**
 * External facing user information.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if neither the device nor app is enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Példa: Annak megállapítása, hogy engedélyezett-e a Mentés eszközre vagy Felhőbeli tárhelyre

Számos alkalmazás valósít meg olyan funkciókat, amelyek lehetővé teszik a végfelhasználó számára fájlok mentését helyi háttértárra vagy felhőbeli tárolószolgáltatásba. Az Intune App SDK lehetővé teszi a rendszergazdáknak az adatszivárgás ellen a szervezet igényei szerinti szabályzatkorlátozások alkalmazásával történő védekezést.  A rendszergazda által beállítható szabályzatok egyike arra vonatkozik, hogy a felhasználók menthetnek-e fájlokat nem felügyelt személyes adattárba. Ide tartoznak a helyi mentési helyek, az SD-kártyák és a harmadik felek biztonsági mentési szolgáltatásai.

**A funkció engedélyezéséhez az alkalmazás részvételére van szükség.** Ha az alkalmazás lehetővé teszi a személyes vagy a felhőbeli helyekre való mentést közvetlenül az alkalmazásból, ezt a funkciót meg kell valósítani annak biztosításához, hogy a rendszergazda szabályozhassa, engedélyezve van-e a mentés az adott helyre. Az alábbi API lehetővé teszi, hogy az alkalmazás megállapítsa, hogy a személyes tárolóba való mentés engedélyezve van-e az aktuális Intune-rendszergazda szabályzata szerint. Az alkalmazás ekkor érvényesítheti a házirendet, mivel meg tudja állapítani, hogy elérhető-e személyes adattár a felhasználó számára az alkalmazáson keresztül.  

Az alábbi hívással állapíthatja meg, hogy a szabályzat be van-e tartatva:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

A `service` paraméternek a következő `SaveLocation` értékek egyikének kell lennie:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

A következőnek kell lennie: a menteni kívánt felhőalapú szolgáltatáshoz tartozó UPN/username/e-mail (*nem* feltétlenül egyezik megazéppenmentettdokumentumotbirtoklófelhasználóval).`username` Ha a HRE UPN és a Cloud Service-Felhasználónév közötti leképezés nem létezik, vagy a Felhasználónév nem ismert, akkor a null értéket kell használnia. a `SaveLocation.LOCAL` nem felhőalapú szolgáltatás, ezért mindig `null` username paraméterrel kell használni.

Korábban ugyanezen **AppPolicy** osztály `getIsSaveToPersonalAllowed()` függvényével lehetett megállapítani, hogy az adott felhasználó szabályzata engedélyezi-e a mentést különféle helyekre. Ez a függvény mostanra **elavult**, és nem szabad használni. Az alábbi kód egyenértékű a `getIsSaveToPersonalAllowed()` függvénnyel:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, null);
```

>[!NOTE]
> A `SaveLocation.OTHER` akkor használatos, ha a szóban forgó hely nem szerepel a **SaveLocations** enumerációban.

### <a name="example-determine-if-notifications-with-organization-data-need-to-be-restricted"></a>Példa: Annak megállapítása, hogy korlátozva kell-e az értesítéseket a szervezeti adattal

Ha az alkalmazás értesítéseket jelenít meg, akkor az értesítés megjelenítése előtt ellenőriznie kell az értesítéshez társított felhasználó értesítési korlátozási szabályzatát. A következő hívással állapíthatja meg, hogy a házirend ki van-e kényszerítve.

```java
NotificationRestriction notificationRestriction =
    MAMPolicyManager.getPolicyForIdentity(notificationIdentity).getNotificationRestriction();
```

Ha a korlátozás értéke @no__t – 0, az alkalmazás nem jelenítheti meg a Szabályzathoz társított felhasználó értesítéseit. Ha @no__t – 0, az alkalmazásnak olyan módosított értesítést kell megjelenítenie, amely nem tartalmaz szervezeti adatkészletet. Ha @no__t – 0, az összes értesítés engedélyezett.

Ha a `getNotificationRestriction` nincs meghívva, a MAM SDK a legjobb erőfeszítést tesz az értesítések automatikus korlátozására az egyszeres identitású alkalmazások esetében. Ha az automatikus blokkolás engedélyezve van, és a `BLOCK_ORG_DATA` be van állítva, akkor az értesítés egyáltalán nem jelenik meg. Részletesebb szabályozást a `getNotificationRestriction` értékkel ellenőrizheti, és megfelelően módosíthatja az alkalmazás-értesítéseket.

## <a name="register-for-notifications-from-the-sdk"></a>Regisztráció az SDK értesítéseire

### <a name="overview"></a>Áttekintés
Az Intune App SDK lehetővé teszi, hogy az alkalmazás szabályozza bizonyos szabályzatok, például a szelektív törlési szabályzat működését, ha a rendszergazda telepítette őket. Amikor a rendszergazda alkalmaz egy ilyen szabályzatot, az Intune szolgáltatás értesítést küld az SDK-nak.

Ehhez regisztrálnia kell az SDK által küldött értesítésekre: hozzon létre egy `MAMNotificationReceiver` osztályt, és regisztrálja a következővel: `MAMNotificationReceiverRegistry`. Ez a fogadó és az `App.onCreate` metódusban fogadni kívánt értesítés típusának megadásával történik, az alábbi példában látható módon:

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

A `MAMNotificationReceiver` fogadja az értesítéseket az Intune szolgáltatástól. Egyes értesítéseket közvetlenül az SDK kezel, míg mások az alkalmazás részvételét igénylik. Az alkalmazásnak igaz vagy hamis értéket **kell** visszaadnia az értesítésekből. Hacsak valamely, általa az értesítés eredményeként megkísérelt művelet sikertelen nem volt, mindig igaz értéket kell visszaadjon.

* Ez a hiba megjelenhet az Intune szolgáltatásnak küldött jelentésben. Jelentendő helyzet lehet például az olyan eset, amikor az alkalmazás nem törli a felhasználói adatokat, miután a rendszergazda kezdeményezte a törlést.

>[!NOTE]
> A `MAMNotificationReceiver.onReceive` metódusban biztonságosan blokkolható, mivel a visszahívása nem a felhasználói felület szálán fut.

Alább látható az SDK-ban ily módon definiált `MAMNotificationReceiver` interfész:

```java
/**
 * The SDK is signaling that a MAM event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}
```

### <a name="types-of-notifications"></a>Az értesítések típusai

A következő értesítéseket küldi a program az alkalmazásnak, és némelyikük igényelheti az alkalmazás részvételét:

* **WIPE_USER_DATA**: Ezt az értesítést a rendszer egy `MAMUserNotification` osztályban küldi el. Ha ez az értesítés érkezik, az alkalmazásnak törölnie *kell* a felügyelt identitáshoz társított összes adatmennyiséget (`MAMUserNotification.getUserIdentity()`). Az értesítés különböző okok miatt fordulhat elő, többek között akkor is, ha az alkalmazás meghívja a `unregisterAccountForMAM` értéket, amikor egy rendszergazda elindít egy törlést, vagy ha a rendszergazda által kért feltételes hozzáférési szabályzatok nem teljesülnek. Ha az alkalmazás nem regisztrálja ezt az értesítést, a rendszer az alapértelmezett törlési viselkedést fogja végrehajtani. Az alapértelmezett viselkedés törli az egyetlen identitást tartalmazó alkalmazás összes fájlját, vagy a felügyelt identitással címkézett összes fájlt egy többszörös identitású alkalmazás esetében. Ez az értesítés soha nem lesz elküldve a felhasználói felületi szálon.

* **WIPE_USER_AUXILIARY_DATA**: Az alkalmazások regisztrálhatnak erre az értesítésre, ha azt szeretnék, hogy az Intune app SDK végrehajtsa az alapértelmezett szelektív törlési viselkedést, de továbbra is szeretné eltávolítani a kisegítő adatok törlését. Ez az értesítés csak a több identitást kezelő alkalmazások számára érhető el. Ez az értesítés soha nem lesz elküldve a felhasználói felületi szálon.

* **REFRESH_POLICY**: A rendszer ezt az értesítést küldi `MAMUserNotification`el. Ha ez az értesítés érkezik, az alkalmazás által gyorsítótárazott Intune-szabályzatokra vonatkozó döntéseket érvényteleníteni és frissíteni kell. Ha az alkalmazás nem tárol házirend-feltételezéseket, nem kell regisztrálnia ezt az értesítést. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

* **REFRESH_APP_CONFIG**: A rendszer ezt az értesítést küldi `MAMUserNotification`el. Az értesítés fogadásakor a gyorsítótárazott alkalmazás-konfigurációs összes adattal érvényteleníteni és frissíteni kell. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

* **MANAGEMENT_REMOVED**: A rendszer ezt az értesítést küldi el `MAMUserNotification` , és tájékoztatja arról, hogy az alkalmazás nem lesz felügyelve. Felügyelet nélkül az alkalmazás nem fogja tudni olvasni a titkosított fájlokat, a MAMDataProtectionManagerrel titkosított adatokat, kezelni a titkosított vágólapot, vagy bármilyen más módon részt venni a felügyelt alkalmazások ökoszisztémájában. Tekintse meg az alábbi részleteket. Ez az értesítés soha nem lesz elküldve a felhasználói felületi szálon.

* **MAM_ENROLLMENT_RESULT**: A rendszer ezt az értesítést küldi `MAMEnrollmentNotification` az alkalmazásnak, amely tájékoztatja az alkalmazást, hogy a beléptetési kísérlet befejeződött, és megadja a kísérlet állapotát. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

* **COMPLIANCE_STATUS**: A rendszer ezt az értesítést küldi `MAMComplianceNotification` , hogy tájékoztassa az alkalmazást a megfelelőségi szervizelési kísérlet eredményéről. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

> [!NOTE]
> Az alkalmazások nem regisztrálhatnak egyszerre a `WIPE_USER_DATA` és a `WIPE_USER_AUXILIARY_DATA` értesítésre.

### <a name="management_removed"></a>MANAGEMENT_REMOVED

Az `MANAGEMENT_REMOVED` értesítés azt jelzi, hogy az Intune MAM-szabályzata már nem fogja felügyelni a korábban házirend által kezelt felhasználókat. Ehhez nincs szükség a felhasználói adatok törlésére vagy a felhasználó kijelentkezésére (ha törlésre van szükség `WIPE_USER_DATA` , értesítést küld a rendszer). Előfordulhat, hogy számos alkalmazásnak egyáltalán nem kell kezelnie ezt az értesítést, azonban a `MAMDataProtectionManager` használatban lévő alkalmazásoknak külön megjegyzésre van szükségük [az értesítésről](#data-protection).

Ha a MAM meghívja az `MANAGEMENT_REMOVED` alkalmazás fogadóját, a következők lesznek érvényesek:
* A MAM már visszafejti az alkalmazáshoz tartozó korábban titkosított fájlokat (de nem védett adatpuffereket). Az SDcard nyilvános helyein lévő fájlok, amelyek nem tartoznak közvetlenül az alkalmazáshoz (például a dokumentumok vagy a letöltési mappák), nem lesznek visszafejtve.
* A fogadó módszer által létrehozott új fájlok vagy védett adatpufferek (vagy bármely más, a fogadó indítása után futó kód) nem lesznek titkosítva.
* Az alkalmazás továbbra is hozzáfér a titkosítási kulcsokhoz, így a műveletek, például a visszafejtési adatpufferek sikeresek lesznek.

Ha az alkalmazás fogadója visszatér, a továbbiakban nem lesz hozzáférése a titkosítási kulcsokhoz.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Az Azure Active Directory Authentication Library (ADAL) konfigurálása (nem kötelező)

Először olvassa el a [GitHub ADAL-kódtárában](https://github.com/AzureAD/azure-activedirectory-library-for-android) található ADAL-integrációs irányelveket.

Az SDK a hitelesítési és feltételes indítási forgatókönyvekhez az [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)-ra támaszkodik, amely a [hitelesítéshez](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) megköveteli, hogy az alkalmazásokat az [Azure Active Directoryval](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) konfigurálják. A konfigurációs értékeket az SDK az AndroidManifest metaadatain keresztül közli.

Az alkalmazás konfigurálásához és a megfelelő hitelesítés engedélyezéséhez vegye fel a következőket az AndroidManifest.xml-be. Ezen konfigurációk némelyike csak akkor szükséges, ha az alkalmazás általánosan az ADAL-t használja hitelesítéshez. Ebben az esetben azokra a konkrét értékekre is szüksége lesz, amelyekkel az alkalmazás az AAD-ben regisztrálja magát. Így lehet biztosítani, hogy a rendszer ne kérje kétszer a felhasználó hitelesítését. Az AAD ugyanis két különböző regisztrációs értéket ismer fel: egyet az alkalmazásból, egyet pedig az SDK-ból.

```xml
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.ClientID"
    android:value="your-client-ID-GUID" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
    android:value="your-redirect-URI" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.SkipBroker"
    android:value="[true | false]" />
```

### <a name="adal-metadata"></a>ADAL-metaadatok

* **Authority:** a használatban lévő AAD-szolgáltató. Ennek az értéknek a hiánya esetén a nyilvános AAD-környezet lesz használva.
    > [!NOTE]
    > Ne adjon meg értéket a mezőnek, ha az alkalmazása szuverén felhőt használ.

* A **ClientID** a használni kívánt HRE-ClientID (más néven alkalmazás-azonosító). Ha az Azure AD-ben regisztrálva van, vagy az [alapértelmezett regisztrációt](#default-enrollment-optional) használja, akkor a saját alkalmazás ClientID kell használnia, ha nem integrálja az ADAL-t.

* **NonBrokerRedirectURI:** a közvetítő nélküli esetekben használandó AAD átirányítási URI. Ha nincs megadva, a rendszer az alapértelmezett `urn:ietf:wg:oauth:2.0:oob` értéket használja. Ez a legtöbb alkalmazáshoz megfelelő.

  * A NonBrokerRedirectURI csak akkor használatos, ha a SkipBroker értéke "true" (igaz).

* A **SkipBroker** az alapértelmezett ADAL SSO-részvételi viselkedés felülbírálására szolgál. A SkipBroker csak olyan alkalmazások esetében szabad megadni, amelyek ClientID határoznak meg **, és** nem támogatják a felügyelt hitelesítést/eszközre kiterjedő egyszeri bejelentkezést. Ebben az esetben a tulajdonságot "true" értékre kell beállítani. A legtöbb alkalmazás nem állíthatja be a SkipBroker paramétert.

  * SkipBroker érték megadásához meg kell adni egy ClientID a jegyzékfájlban.

  * Ha meg van adva egy ClientID, az alapértelmezett érték a "false".

  * Ha a SkipBroker értéke "true" (igaz), a rendszer a NonBrokerRedirectURI fogja használni. Azok az alkalmazások, amelyek nem integrálják a ADAL-t (és ezért nincs ClientID), az alapértelmezett érték "true" (igaz) is.

### <a name="common-adal-configurations"></a>Általános ADAL-konfigurációk

A következőkben az alkalmazások ADAL-konfigurációjának gyakori eseteit mutatjuk be. Keresse meg az alkalmazásához illő esetet, és állítsa be az ADAL (fent ismertetett) metaadat-paramétereit a megfelelő értékekre. A hatóság minden esetben megadható, ha a nem alapértelmezett környezetekhez szükséges. Ha nincs megadva, a rendszer a nyilvános éles HRE-szolgáltatót fogja használni.

#### <a name="1-app-does-not-integrate-adal"></a>1. Az alkalmazás nem integrálja az ADAL-t
A ADAL-metaadatok **nem** lehetnek jelen a jegyzékfájlban.

#### <a name="2-app-integrates-adal"></a>2. Az alkalmazás integrálja az ADAL-t

|Szükséges ADAL-paraméter| Value |
|--|--|
| ClientID | Az alkalmazás ClientID azonosítója (az Azure AD állítja elő az alkalmazás regisztrálásakor) |

Szükség esetén a szolgáltató is megadható.

Regisztrálnia kell az alkalmazást az Azure AD-ben, és hozzáférést kell adnia az alkalmazásnak az alkalmazás-védelmi házirend szolgáltatáshoz:
* Az alkalmazások Azure AD-ban való regisztrálásáról [itt](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) találhat információt.
* Győződjön meg arról, hogy a lépéseket követve megadhatja az Android-alkalmazás engedélyeit az App Protection-házirend (alkalmazás) szolgáltatáshoz. Az [első lépések az INTUNE SDK](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) -útmutatóban című témakör útmutatását követve adja meg az alkalmazás hozzáférését az Intune app Protection szolgáltatáshoz (nem kötelező). 

Lásd emellett alább a [Feltételes hozzáférés](#conditional-access) követelményeit.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. Az alkalmazás integrálja a ADAL-t, de nem támogatja a felügyelt hitelesítés/eszköz szintű egyszeri bejelentkezést

|Szükséges ADAL-paraméter| Value |
|--|--|
| ClientID | Az alkalmazás ClientID azonosítója (az Azure AD állítja elő az alkalmazás regisztrálásakor) |
| SkipBroker | **True** |

Az Authority és a NonBrokerRedirectURI megadható szükséges esetén.

### <a name="conditional-access"></a>Feltételes hozzáférés
A feltételes hozzáférés egy Azure Active Directorybeli [szolgáltatás](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer), mellyel vezérelheti az AAD-erőforrások elérését. [Az Intune-rendszergazdák definiálhatnak feltételes hozzáférési szabályokat](https://docs.microsoft.com/intune/conditional-access), melyekkel az erőforrások elérését az Intune által felügyelt eszközökre és alkalmazásokra korlátozhatják. Kövesse az alábbi lépéseket annak biztosításához, hogy az alkalmazása el tudja érni a szükséges erőforrásokat. Ha az alkalmazása nem szerez be egyetlen AAD-hozzáférési tokent sem, vagy ha csak feltételes hozzáféréssel nem védhető erőforrásokhoz fér hozzá, akkor kihagyhatja ezeket a lépéseket.

1. Kövesse az [ADAL-integráció irányelveit](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Fordítson különös figyelmet a 11. lépésben ismertetett közvetítőhasználatra.
2. [Regisztrálja alkalmazását az Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   Az átirányítási URI-t megtalálhatja a fentebb hivatkozott ADAL-integrációs irányelvekben.
3. Állítsa be a jegyzékfájl metaadat-paramétereit az [Általános ADAL-konfigurációk](#common-adal-configurations) szerint (2. elem, fentebb).
4. Tesztelje a konfiguráció helyességét. Ehhez engedélyezze az [eszközalapú feltételes hozzáférést](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) az [Azure Portalon](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2), és bizonyosodjon meg a következőkről:
    - Hogy az alkalmazásába való bejelentkezéskor a rendszer kéri a Céges portál telepítését és regisztrálását.
    - Hogy a regisztrálás után sikeresen befejeződik az alkalmazásába való bejelentkezés.
5. Miután az alkalmazás beszállította az Intune app SDK- msintuneappsdk@microsoft.com integrációt, vegye fel a kapcsolatot a jóváhagyott alkalmazások listájával az [alkalmazás-alapú feltételes hozzáféréshez](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. Miután az alkalmazását hozzáadtuk a jóváhagyott alkalmazások listájához, ellenőrizze a rendszer működését. Ehhez [konfigurálja az alkalmazásalapú feltételes hozzáférést](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create), és győződjön meg róla, hogy az alkalmazásába való bejelentkezés sikeresen befejeződik.

## <a name="app-protection-policy-without-device-enrollment"></a>Eszközregisztráció nélküli alkalmazásvédelmi szabályzat

### <a name="overview"></a>Áttekintés
Az Intune APP-WE vagy MAM-WE néven is ismert eszközbeléptetés nélküli alkalmazásvédelmi szabályzata lehetővé teszi, hogy az Intune anélkül is felügyelhesse az alkalmazásokat, hogy az eszközök az Intune MDM-re regisztrálva lennének. Az APP-WE működik eszközbeléptetéssel és anélkül is. A Céges portál alkalmazást továbbra is telepíteni kell az eszközre, de a felhasználónak nem kell bejelentkeznie a Céges portálba és beléptetnie az eszközt.

> [!NOTE]
> Az összes alkalmazásnak támogatnia kell az alkalmazásvédelmi szabályzatok eszközbeléptetés nélküli használatát.

### <a name="workflow"></a>Munkafolyamat

Ha egy alkalmazás új felhasználói fiókot hoz létre, azt regisztrálnia kell felügyeletre az Intune App SDK-val. Az SDK kezeli az alkalmazás APP-WE szolgáltatásba való beléptetésének részleteit; szükség esetén a megfelelő időközönként újból megpróbálkozik a beléptetéssel, ha az sikertelen.

Az alkalmazás az Intune App SDK-tól kérdezheti le a regisztrált felhasználók állapotát is, amikor azt próbálja megállapítani, hogy az illetőt el kell-e tiltani a vállalati tartalom elérésétől. Több fiókot is lehet felügyeletre regisztrálni, de jelenleg egyszerre csak egy lehet aktívan beléptetve az APP-WE szolgáltatásba, és így az alkalmazásban is egyszerre csak egy fiók kaphat alkalmazásvédelmi szabályzatot.

Az alkalmazásnak visszahívás útján kell megszereznie a megfelelő hozzáférési jogkivonatot az Azure Active Directory Authentication Librarytől (ADAL) az SDK nevében. Az alapfeltevés az, hogy az alkalmazás már az ADAL-lal hitelesíti a felhasználókat és szerzi be a saját hozzáférési jogkivonatát.

Amikor az alkalmazás teljesen eltávolít egy fiókot, meg kell szüntetnie annak regisztrációját, így jelezve, hogy a továbbiakban az adott felhasználóra nem kell szabályzatot alkalmazni. Ha a felhasználó be volt léptetve a MAM-szolgáltatásba, akkor a beléptetés megszűnik, az alkalmazás pedig törlődik.

### <a name="overview-of-app-requirements"></a>Az alkalmazások követelményeinek áttekintése

Az APP-WE-integráció implementálásához az alkalmazásnak a felhasználói fiókot regisztrálnia kell a MAM SDK-val:

1. Az alkalmazásnak _kötelező_ a `MAMServiceAuthenticationCallback` interfész egy példányát implementálni és regisztrálni. A visszahívási példányt az alkalmazás életciklusának lehető legkorábbi pontján kell regisztrálni (jellemzően az alkalmazás osztályának `onMAMCreate()` metódusában).

2. Felhasználói fiók létrejötte és a felhasználó sikeres ADAL-bejelentkezése után alkalmazásnak _kötelező_ meghívni a `registerAccountForMAM()` metódust.

3. Felhasználói fiók eltávolítása után az alkalmazásnak az `unregisterAccountForMAM()` metódussal kell eltávolítania a fiókot az Intune-felügyeletből.

    > [!NOTE]
    > Ha egy felhasználó átmenetileg kijelentkezik az alkalmazásból, akkor nincs szükség az `unregisterAccountForMAM()` meghívására, mert előfordulhat, hogy ez törlést kezdeményez, és eltávolítja a felhasználó céges adatait.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager
Az összes szükséges hitelesítési és regisztrációs API a `MAMEnrollmentManager` interfészben található. `MAMEnrollmentManager`-hivatkozást az alábbi módon lehet szerezni:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

A visszaadott `MAMEnrollmentManager`-példány garantáltan nem null értékű. Az API-metódusok között vannak **hitelesítésre** és **fiókregisztrációra** használatosak.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>Fiókhitelesítés
Ez a szakasz a `MAMEnrollmentManager` hitelesítési API-metódusait és azok használatát ismerteti.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. Az alkalmazásnak a `MAMServiceAuthenticationCallback` interfész implementálásával kell biztosítania, hogy az SDK kérhessen ADAL-jogkivonatot az adott felhasználóhoz és erőforrás-azonosítóhoz. A `MAMEnrollmentManager` számára annak `registerAuthenticationCallback()` metódusát meghívva kell biztosítani a visszahívási példányt. Az alkalmazás életciklusának már korai szakaszában is szükség lehet jogkivonatra a beléptetési újrapróbálkozásokhoz vagy az alkalmazásvédelmi szabályzat frissítésének kereséséhez, így a visszahívást ideálisan az alkalmazás `MAMApplication` alosztályának `onMAMCreate()` metódusában érdemes regisztrálni.

2. A kért erőforrás-azonosítóra szóló hozzáférési jogkivonatot az `acquireToken()` metódusnak kell beszereznie az adott felhasználó számára. Ha ez nem sikerül, a metódusnak null értéket kell visszaadnia.

    > [!NOTE]
    > Győződjön meg arról, hogy az alkalmazás `resourceId` a `aadId` megfelelő jogkivonat beszerzése után az átadott `acquireToken()` paramétereket használja.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Ha az alkalmazás nem tud jogkivonatot biztosítani, amikor az SDK meghívja az `acquireToken()` metódust – például mert a csendes hitelesítés sikertelen és éppen nem lehet felhasználói felületet megjeleníteni –, később az `updateToken()` metódust meghívva teheti ezt meg. Az `updateToken()` metódusnak az `acquireToken()` korábbi meghívásakor használt UPN-t, AAD-azonosítót és erőforrás-ID kell átadni a végül beszerzett jogkivonattal együtt. Az alkalmazásnak a lehető leghamarabb meg kell hívnia ezt a metódust, miután a megadott visszahívás a null értéket adta.

    > [!NOTE]
    > Az SDK rendszeres időközönként megpróbálja az `acquireToken()` meghívásával megszerezni a jogkivonatot, így az `updateToken()` meghívása szigorúan véve nem szükséges, Erősen ajánlott azonban, mert segíthet a regisztrációk és az alkalmazás-védelmi szabályzatok beadásának időben történő beléptetésében.


### <a name="account-registration"></a>Fiókregisztráció
Ez a szakasz a `MAMEnrollmentManager` fiókregisztrációs API-metódusait és azok használatát ismerteti.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. A fiókokat az alkalmazásnak a `registerAccountForMAM()` metódust meghívva kell regisztrálnia a felügyelet alá. A felhasználói fiókot egyszerű felhasználóneve (UPN) és AAD-s felhasználói azonosítója is azonosítja. A beléptetési adatoknak a felhasználó AAD-bérlőjéhez társításához a bérlőazonosító is szükséges. A felhasználó hatósága is megadható az adott szuverén Felhőkkel való regisztráció engedélyezéséhez. További információ: [szuverén Felhőbeli regisztráció](#sovereign-cloud-registration).  Az SDK megpróbálhatja az adott felhasználó számára beléptetni az alkalmazást a MAM-szolgáltatásba. Ha a beléptetés sikertelen, akkor rendszeres időközönként újra fog próbálkozni vele, amíg a fiók regisztrációja meg nem szűnik. Az újrapróbálkozások időköze általában 12–24 óra. Az SDK aszinkron módon, értesítések útján közli a beléptetési kísérletek állapotát.

2. Mivel a HRE-hitelesítés szükséges, a felhasználói fiók regisztrálásának legjobb ideje az, hogy a felhasználó bejelentkezett az alkalmazásba, és sikeresen hitelesítve lett a ADAL használatával. A felhasználó HRE-azonosítóját és a bérlő azonosítóját az [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) objektum részeként a ADAL hitelesítési hívás adja vissza.
    * A bérlőazonosító az `AuthenticationResult.getTenantID()` metódusból származik.
    * A felhasználóval kapcsolatos adatok egy, az `AuthenticationResult.getUserInfo()` metódusból származó, `UserInfo` típusú alobjektumban találhatók meg, az AAD-beli felhasználót pedig ebből az objektumból lehet lekérni a `UserInfo.getUserId()` metódussal.

3. A fiókok Intune-felügyeleti regisztrációját az alkalmazásnak az `unregisterAccountForMAM()` metódust meghívva kell megszüntetnie. Ha a fiók sikeresen be lett léptetve, és felügyelt fiók lett, az SDK fogja megszüntetni a beléptetését és törölni az adatait. A rendszeres időközönkénti beléptetési próbálkozások abbamaradnak. Az SDK aszinkron módon adja meg a beléptetési kérések állapotát értesítés útján.

### <a name="sovereign-cloud-registration"></a>Regisztrálás szuverén felhőbe
A [szuverén felhőt használó](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) alkalmazásoknak **mindenképp** meg kell adniuk az `authority` beállítást a `registerAccountForMAM()` metódushoz.  Ezt úgy szerezheti be, hogy megadja az `instance_aware=true` értéket az ADAL [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken metódusának extraQueryParameters paraméterében, majd meghívja a `getAuthority()` metódust az AuthenticationCallback AuthenticationResult példányon.

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> Ne állítsa be a `com.microsoft.intune.mam.aad.Authority` meta-adatelem elemeket a AndroidManifest. xml fájlban.

> [!NOTE]
> Győződjön meg róla, hogy a szolgáltató (authority) megfelelően van beállítva a `MAMServiceAuthenticationCallback::acquireToken()` metódusban.

#### <a name="currently-supported-sovereign-clouds"></a>Jelenleg támogatott szuverén felhők

1. Azure USA-beli kormányzati felhő

### <a name="important-implementation-notes"></a>Fontos megjegyzések az implementálással kapcsolatban

#### <a name="authentication"></a>Authentication
* Amikor az alkalmazás meghívja a `registerAccountForMAM()` metódust, kis idővel utána visszahívást kaphat egy másik szálon a `MAMServiceAuthenticationCallback` interfészén. Ideális esetben az alkalmazás a saját tokenjét a ADAL-ből szerezte be a fiók regisztrálása előtt, hogy felgyorsítsa a kért jogkivonat beszerzését. Ha az alkalmazás egy érvényes jogkivonatot ad vissza a visszahívásból, a beléptetés folytatódik, és az alkalmazás a végső eredményt egy értesítésen keresztül kapja meg.

* Ha az alkalmazás nem ad vissza érvényes AAD-jogkivonatot, a beléptetés végeredménye `AUTHENTICATION_NEEDED` lesz. Ha az alkalmazás értesítést kap az eredményről, erősen ajánlott a beléptetési folyamat meggyorsítása azáltal, hogy beszerezze a jogkivonatot a korábban `acquireToken()` kért felhasználóhoz `updateToken()` és erőforráshoz, és felszólítja a metódust a következő kezdeményezésre: beléptetési folyamat.

* Az alkalmazás regisztrált `MAMServiceAuthenticationCallback` interfésze is meg lesz hívva az alkalmazásvédelmi szabályzatok frissítéseinek rendszeres kereséséhez szükséges jogkivonat beszerzése céljából. Ha az alkalmazás kérésre nem tudja biztosítani a kért jogkivonatot, akkor nem fog értesítést kapni, de meg kell próbálnia jogkivonatot beszerezni, és a legközelebbi alkalmas időpontban meghívni az `updateToken()` metódust a beléptetési folyamat meggyorsítása érdekében. A visszahívás akkor is meg lesz hívva a következő beléptetési kísérletnél, ha nincs jogkivonat.

* A szuverén felhők támogatásához meg kell adnia a szolgáltatót (authority).

#### <a name="registration"></a>Regisztráció
* Az egyszerűség kedvéért a regisztrációs metódusok idempotensek. A `registerAccountForMAM()` például csak akkor regisztrálja a fiókot és próbálja meg beléptetni az alkalmazást, ha a fiók még nincs regisztrálva, az `unregisterAccountForMAM()` pedig csak akkor törli a fiók regisztrációját, ha az az adott időpontban regisztrálva van. Az ismételt hívások hatástalanok lesznek, így ezeket a metódusokat következmény nélkül meg lehet hívni többször is. Ezenfelül a metódusok meghívása nem feltétlenül vált ki eredménnyel kapcsolatos értesítést, tehát amennyiben a `registerAccountForMAM()` metódust egy már regisztrált identitáshoz hívják meg, akkor az identitás nem feltétlenül kap újabb értesítést. Lehetnek olyan értesítések is, amelyek nem kapcsolódnak ezen metódusok meghívásához, mivel az SDK rendszeres időközönként próbálkozik beléptetésekkel a háttérben, az Intune szolgáltatástól érkező törlési kérések pedig kiválthatnak beléptetés-visszavonásokat.

* A regisztrációs metódusokat tetszőleges számú különböző identitáshoz meg lehet hívni, de jelenleg egyszerre csak egy felhasználói fiókot lehet sikeresen beléptetni. Ha több, az Intune-hoz licencelt és alkalmazásvédelmi szabályzattal célzott felhasználói fiókot regisztrálnak egyszerre vagy csaknem egy időben, akkor nem lehet előre tudni, hogy melyik nyeri a versenyt.

* Végül a `MAMEnrollmentManager` interfésztől lehet lekérdezni, hogy egy bizonyos fiók regisztrálva van-e, és a `getRegisteredAccountStatus()` metódussal lehet lekérni az aktuális állapotát. Ha a megadott fiók nincs regisztrálva, a metódus a **null** értéket adja vissza. Ha a fiók regisztrálva van, a metódus a `MAMEnrollmentManager.Result` enumeráció valamely elemével jelzi a fiók állapotát.

### <a name="result-and-status-codes"></a>Eredmény- és állapotkódok
A fiók az első regisztráció során `PENDING` állapotban kerül be a rendszerbe, jelezvén, hogy a MAM-szolgáltatásba való kezdeti beléptetési kísérlet még nem fejeződött be. A beléptetési kísérlet befejezése után egy értesítés jön létre az alábbi táblázatban felsorolt eredménykódok valamelyikével. Ezenkívül a `getRegisteredAccountStatus()` metódus visszaadja a fiók állapotát, hogy az alkalmazás bármikor el tudja dönteni, hogy letiltsa-e az adott felhasználó hozzáférését a vállalati tartalomhoz. Ha a beléptetési kísérlet sikertelen, a fiók állapota idővel változhat, amint az SDK a háttérben tovább próbálkozik a beléptetéssel.

|Eredménykód | Magyarázat |
| -- | -- |
| `AUTHORIZATION_NEEDED` | Ez az eredmény azt jelzi, hogy az alkalmazás regisztrált `MAMServiceAuthenticationCallback` példánya nem adta meg a tokent, vagy a megadott jogkivonat érvénytelen.  Az alkalmazásnak be kell szereznie egy jogkivonatot, és lehetőség szerint meg kell hívnia az `updateToken()` metódust. |
| `NOT_LICENSED` | A felhasználónak nincs Intune-licence, vagy sikertelen volt az Intune MAM-szolgáltatáshoz való kapcsolódás.  Az alkalmazásnak nem felügyelt (normál) állapotban kell tovább futnia, a felhasználót pedig nem kell blokkolni.  Amennyiben később a felhasználónak lesz licence, az SDK rendszeresen próbálkozik a beléptetéssel. |
| `ENROLLMENT_SUCCEEDED` | A beléptetési kísérlet sikeres volt, vagy a felhasználó már korábban be lett léptetve.  Sikeres beléptetés esetén ezt az értesítést megelőzően egy szabályzatfrissítési értesítést is küld a rendszer.  A vállalati adatokhoz való hozzáférést engedélyezni kell. |
| `ENROLLMENT_FAILED` | A beléptetési kísérlet sikertelen volt.  A további részletek az eszköznaplókban találhatók.  Az alkalmazás ebben az állapotban nem engedélyezheti a vállalati adatelérést, mivel korábban azt állapították meg, hogy a felhasználó Intune-licenccel rendelkezik.|
| `WRONG_USER` | Egy eszközön minden alkalmazást csak egy felhasználó léptethet be a MAM-szolgáltatásba. Ez az eredmény azt jelzi, hogy a felhasználó, akire ezt az eredményt szállították (a második felhasználó), a MAM-szabályzattal van megcélozva, de egy másik felhasználó már regisztrálva van. Mivel a MAM-szabályzat nem kényszeríthető ki a második felhasználó számára, az alkalmazás nem engedélyezheti a hozzáférést ehhez a felhasználó adataihoz (valószínűleg eltávolítja a felhasználót az alkalmazásból), kivéve, ha a felhasználó egy későbbi időpontban sikertelen lesz. A `WRONG_USER` eredmény megadásával párhuzamosan a MAM kérni fogja a meglévő fiók eltávolításának lehetőségét. Ha az emberi felhasználó igenlő válaszban válaszol, akkor a második felhasználó rövid idő múlva regisztrálhat. Amíg a második felhasználó regisztrálva marad, a MAM rendszeresen újrapróbálkozik a regisztrációval. |
| `UNENROLLMENT_SUCCEEDED` | A beléptetés megszüntetése sikeres volt.|
| `UNENROLLMENT_FAILED` | A beléptetés-megszüntetési kérés sikeres volt.  A további részletek az eszköznaplókban találhatók. Ez általában akkor fordul elő, ha az alkalmazás érvényes (sem null, sem üres) UPN-t továbbít. Az alkalmazás nem rendelkezik közvetlen, megbízható szervizeléssel. Ha ez az érték egy érvényes egyszerű felhasználónév regisztrációjának törlésekor érkezik, jelentse a hibát az Intune MAM csapatának.|
| `PENDING` | A felhasználó első beléptetési kísérlete folyamatban van.  Az alkalmazás a beléptetés eredményének ismertté válásáig letilthatja a vállalati adatokhoz való hozzáférést, de nem köteles így tenni. |
| `COMPANY_PORTAL_REQUIRED` | A felhasználónak van Intune-licence, de az alkalmazást nem lehet beléptetni, amíg a Céges portál alkalmazás nincs telepítve az eszközre. Az Intune App SDK megpróbálja megtagadni az alkalmazáshoz való hozzáférést az adott felhasználótól, és felszólítani a Céges portál alkalmazás telepítésére (részletek alább). |


### <a name="company-portal-requirement-prompt-override-optional"></a>A Céges portál követelményére való figyelmeztetés felülbírálása (nem kötelező)
`COMPANY_PORTAL_REQUIRED` eredmény esetén az SDK letiltja az ahhoz az identitáshoz kapcsolódó tevékenységeket, amelynek a beléptetése a kérés tárgya volt. Az SDK ezen tevékenységekre válaszul egy, a Céges portál alkalmazás letöltését kérő üzenetet jelenít meg. Ha ezt a saját alkalmazásában szeretné elkerülni, a tevékenységek implementálhatják a `MAMActivity.onMAMCompanyPortalRequired` metódust.

Ennek meghívása még az előtt történik, hogy az SDK megjelenítené az alapértelmezett letiltó felhasználói felületet. Ha az alkalmazás módosítja a tevékenység identitását, vagy törli a beléptetést megkísérlő felhasználó regisztrációját, az SDK nem fogja letiltani a tevékenységet. Ebben az esetben az alkalmazás feladata a vállalati adatszivárgás megakadályozása. Az aktív identitás megváltoztatására csak a többidentitású alkalmazások (lásd alább) képesek.

Ha explicit módon nem örököl `MAMActivity` osztályt (mivel a build-eszköz hajtja végre ezt a módosítást), de továbbra is kezelnie kell ezt az értesítést, akkor ehelyett implementálhatja a `MAMActivityBlockingListener` osztályt.

### <a name="notifications"></a>Értesítések
Ha az alkalmazás regisztrálja az **MAM_ENROLLMENT_RESULT**típusú értesítéseket, a rendszer elküld egy `MAMEnrollmentNotification` értéket, hogy tájékoztassa az alkalmazást a beléptetési kérelem befejeződéséről. A `MAMEnrollmentNotification` értesítés fogadása a `MAMNotificationReceiver` interfészen keresztül történik, a [Regisztráció az SDK értesítéseire](#register-for-notifications-from-the-sdk) című szakaszban leírtak szerint.

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

A `getEnrollmentResult()` metódus a beléptetési kérés eredményét adja vissza.  Mivel a `MAMEnrollmentNotification` a `MAMUserNotification` kiterjesztése, a beléptetési kérés által érintett felhasználó identitása is elérhető. Az alkalmazásnak ezen értesítések fogadásához a [Regisztráció az SDK értesítéseire](#register-for-notifications-from-the-sdk) című szakaszban leírtaknak megfelelően implementálnia kell a `MAMNotificationReceiver` interfészt.

A regisztrált felhasználói fiók állapota megváltozhat, ha beléptetési értesítés érkezik, de az összes esetben nem változik (például ha `AUTHORIZATION_NEEDED` egy további tájékoztató eredmény `WRONG_USER`, például a az eredmény a fiók állapotának megfelelően lesz karbantartva.  A fiók sikeres regisztrálása után az állapot `ENROLLMENT_SUCCEEDED` addig marad, amíg a fiók nincs regisztrálva, vagy nincs törölve.

## <a name="app-ca-with-policy-assurance"></a>ALKALMAZÁS-HITELESÍTÉSSZOLGÁLTATÓ házirend-garanciával

### <a name="overview"></a>Áttekintés
Ha az alkalmazás-HITELESÍTÉSSZOLGÁLTATÓ (feltételes hozzáférés) házirend-garanciával rendelkezik, az erőforrásokhoz való hozzáférés Intune App Protection szabályzatok alkalmazásán alapul.  A HRE ezt úgy kényszeríti, hogy az alkalmazást regisztrálni és felügyeli az alkalmazás, mielőtt jogkivonatot adna egy olyan alkalmazás-HITELESÍTÉSSZOLGÁLTATÓ eléréséhez, amelyhez házirend-megbízhatósági védelemmel ellátott erőforrás van társítva.  Az alkalmazásnak a ADAL-átvitelszervező jogkivonat-beszerzéséhez kell használnia, és a telepítés megegyeznek a [feltételes hozzáférésben](#conditional-access)leírtak szerint.

### <a name="adal-changes"></a>ADAL változásai
A ADAL-könyvtár egy új hibakódot tartalmaz, amely arról tájékoztatja az alkalmazást, hogy a jogkivonat beszerzése nem felel meg az alkalmazás felügyeletének.  Ha az alkalmazás megkapja ezt a hibakódot, meg kell hívnia az SDK-t, hogy megpróbálja elhárítani a megfelelőséget az alkalmazás regisztrálásával és a szabályzat alkalmazásával. A ADAL `onError()` `AuthenticationCallback`metódusa kivételt kap, és a hibakód `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`lesz.  Ebben az esetben a kivételt olyanra `IntuneAppProtectionPolicyRequiredException`lehet átadni, amelyből a szervizelését-megfelelőségben való használatra további paramétereket lehet kinyerni (lásd az alábbi kódrészletet). A szervizelés sikeres befejezését követően az alkalmazás újrapróbálkozhat a jogkivonat-beszerzéssel a ADAL-on keresztül.

> [!NOTE]
> Ez az új hibakód és a házirend-megbízhatósággal rendelkező APP CA egyéb támogatása a ADAL könyvtárának 1.15.0 (vagy újabb verzió) szükséges.

### <a name="mamcompliancemanager"></a>MAMComplianceManager
A `MAMComplianceManager` felületet akkor használja a rendszer, ha a házirend által megkövetelt hiba érkezik a ADAL.  Ez tartalmazza azt `remediateCompliance()` a metódust, amelyet meg kell hívni, hogy az alkalmazás megfelelő állapotba kerüljön. `MAMComplianceManager`-hivatkozást az alábbi módon lehet szerezni:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

A visszaadott `MAMComplianceManager`-példány garantáltan nem null értékű.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

A `remediateCompliance()` metódust úgy hívja meg, hogy megpróbálja a felügyelet alá helyezni az alkalmazást, hogy az megfeleljen a kért jogkivonat megadására vonatkozó HRE feltételeinek.  Az első négy paraméter kinyerhető a ADAL `AuthenticationCallback.onError()` metódus által fogadott kivételből (lásd az alábbi kódrészletet).  Az utolsó paraméter egy olyan logikai érték, amely azt szabályozza, hogy a megfelelőségi kísérlet során megjelenik-e egy UX.  Ez egy egyszerű blokkolási folyamatjelző felület, amely olyan alkalmazások számára biztosít alapértelmezettként, amelyeknek nincs szükségük testreszabott UX megjelenítésére a művelet során.  A rendszer csak a megfelelőségi szervizelést fogja blokkolni, és nem jeleníti meg a végeredményt.  Az alkalmazásnak regisztrálnia kell egy értesítési fogadót a megfelelőségi szervizelési kísérlet sikerességének vagy meghibásodásának kezeléséhez (lásd alább).

A `remediateCompliance()` módszer a megfelelőség megállapításának részeként a MAM-regisztrációt is elvégezheti.  Előfordulhat, hogy az alkalmazás beléptetési értesítést kap, ha regisztrált egy értesítési fogadót a beléptetési értesítésekhez.  Az alkalmazás regisztrálása `MAMServiceAuthenticationCallback` `acquireToken()` meghívja a metódust, hogy megkapjon egy jogkivonatot a MAM-regisztrációhoz. `acquireToken()`akkor lesz meghívva, ha az alkalmazás megszerezte a saját jogkivonatát, ezért a sikeres jogkivonat-beszerzést követően az alkalmazás által végrehajtott könyvelési vagy fiók-létrehozási feladatok még nem lettek végrehajtva.  Ebben az esetben a visszahívásnak képesnek kell lennie a jogkivonat beszerzésére.  Ha nem tud visszaadni jogkivonatot `acquireToken()`, a megfelelőségi szervizelési kísérlet sikertelen lesz.  Ha később a `updateToken()` kért erőforráshoz tartozó érvényes jogkivonatot hív meg, a rendszer azonnal újrapróbálkozik a megfelelőségi szervizeléssel az adott jogkivonattal.

> [!NOTE]
> A csendes jogkivonatok beszerzése `acquireToken()` továbbra is lehetséges, mivel a felhasználó már irányította a közvetítő telepítését, és a `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` hiba fogadása előtt regisztrálja az eszközt.  Ez azt eredményezi, hogy a közvetítő érvényes frissítési tokent eredményez a gyorsítótárban, így a kért jogkivonat csendes acqisition sikeres lesz.

Itt látható egy példa a szabályzat által igényelt hiba fogadására a `AuthenticationCallback.onError()` metódusban, és a `MAMComplianceManager` meghívásával kezelheti a hibát.

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>Állapotüzenetek
Ha az alkalmazás regisztrálja az **COMPLIANCE_STATUS**típusú értesítéseket, a rendszer elküld egy `MAMComplianceNotification` értéket, hogy tájékoztassa az alkalmazást a megfelelőségi szervizelési kísérlet végső állapotáról. A `MAMComplianceNotification` értesítés fogadása a `MAMNotificationReceiver` interfészen keresztül történik, a [Regisztráció az SDK értesítéseire](#register-for-notifications-from-the-sdk) című szakaszban leírtak szerint.

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

A `getComplianceStatus()` metódus visszaadja a megfelelőségi szervizelési kísérlet eredményét az `MAMCAComplianceStatus` enumerálásból származó értékként.

|Állapotkód | Magyarázat |
| -- | -- |
| ISMERETLEN | Az állapot ismeretlen. Ez egy nem várt hiba okát jelezheti. További információ a Céges portál naplókban található. |
| MEGFELELŐ | A megfelelőségi szervizelés sikeres volt, és az alkalmazás már megfelel a szabályzatnak. Az ADAL-jogkivonat beszerzését újra kell próbálkozni. |
| NOT_COMPLIANT | A megfelelőség javításának megkísérlése sikertelen volt.  Az alkalmazás nem megfelelő, és a rendszer nem próbálkozik újra a ADAL-jogkivonat megszerzésével, amíg a hiba feltétele nem lett kijavítva.  A rendszer további hibaüzeneteket továbbít a MAMComplianceNotification. |
| SERVICE_FAILURE | Hiba történt a megfelelőségi adatok Intune szolgáltatásból való beolvasására tett kísérlet során. További információ a Céges portál naplókban található. |
| NETWORK_FAILURE | Hiba történt az Intune szolgáltatáshoz való csatlakozás során. Az alkalmazásnak újra kell próbálkoznia a jogkivonat-beszerzéssel a hálózati kapcsolat visszaállításakor. |
| CLIENT_ERROR | A megfelelőség kijavítására tett kísérlet sikertelen volt az ügyféllel kapcsolatos valamilyen okból.  Például nincs jogkivonat vagy helytelen felhasználó. A rendszer további hibaüzeneteket továbbít a MAMComplianceNotification. |
| PENDING | A megfelelőség javítására tett kísérlet sikertelen volt, mert az állapot válasza még nem érkezett meg a szolgáltatástól, ha túllépte az időkorlátot. Az alkalmazásnak később újra kell próbálkoznia a jogkivonat-beszerzéssel. |
| COMPANY_PORTAL_REQUIRED | Ahhoz, hogy a megfelelőségi szervizelés sikeres legyen, a Céges portál telepíteni kell az eszközön.  Ha az Céges portál már telepítve van az eszközön, az alkalmazást újra kell indítani.  Ebben az esetben egy párbeszédpanel jelenik meg, amely arra kéri a felhasználót, hogy indítsa újra az alkalmazást. |

Ha a megfelelőségi állapot `MAMCAComplianceStatus.COMPLIANT`értéke, az alkalmazásnak újra el kell indítania az eredeti jogkivonat-beszerzését (a saját erőforrásaihoz). Ha a megfelelőségi szervizelési kísérlet sikertelen volt `getComplianceErrorTitle()` , `getComplianceErrorMessage()` a és metódusok olyan honosított karakterláncokat adnak vissza, amelyeket az alkalmazás a végfelhasználónak jeleníthet meg, ha úgy dönt.  A hibák többsége nem pótolható az alkalmazásban, ezért az általános esetben lehet, hogy a fiók létrehozása vagy a bejelentkezés meghiúsul, és lehetővé teszi a felhasználó számára, hogy később próbálkozzon újra.  Ha a hiba tartósan fennáll, a MAM-naplók segíthetnek meghatározni az okot.  A végfelhasználó elküldheti a naplókat az [itt](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "Naplók elküldése a cég támogatási szolgálatának e-mailben")található utasításokat követve.

A `MAMComplianceNotification` kibővítése `MAMUserNotification`óta azon felhasználó identitása is elérhető, akivel a szervizelést megkísérelték.

Íme egy példa arra, hogyan regisztrálhat egy fogadót egy névtelen osztály használatával a MAMNotificationReceiver felület megvalósításához:

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> Az értesítési fogadót a hívás `remediateCompliance()` előtt regisztrálni kell, hogy elkerülje azt a versenyhelyzet-feltételt, amely miatt az értesítés kimaradt.

### <a name="implementation-notes"></a>Megvalósításhoz fűzött megjegyzések
> [!NOTE]
> **Fontos változás!**  <br>
> Az alkalmazás `MAMServiceAuthenticationCallback.acquireToken()` metódusának *false értékűnek* kell lennie az új `forceRefresh` jelzőhöz a `acquireTokenSilentSync()` értékre.
> Korábban azt javasoljuk, hogy *igaz* értéket adjon a tokenek frissítésével kapcsolatos probléma megoldásához, de a ADAL probléma merült fel, amely megakadályozhatja a tokenek beszerzését bizonyos helyzetekben, ha ez a jelző *igaz*.
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ false);
```

> [!NOTE]
> Ha a Szervizelési kísérlet során egyéni blokkolási UX-t szeretne megjeleníteni, a showUX paraméternek `remediateCompliance()` *Hamis értéket* kell adnia. Meg kell győződnie arról, hogy a rendszer meghívja `remediateCompliance()`az UX-t, és először regisztrálja az értesítés-figyelőt.  Ez megakadályozza azt a versenyhelyzet-feltételt, amelyben az értesítés `remediateCompliance()` kihagyható, ha nagyon gyorsan leáll.  Például `onCreate()` egy tevékenység alosztályának vagy `onMAMCreate()` metódusának ideális hely az értesítési figyelő regisztrálása, majd a hívása `remediateCompliance()`.  A paramétereket a `remediateCompliance()` rendszer az UX-hez rendeli hozzá.  Ha a megfelelőségi állapotra vonatkozó értesítés érkezik, megtekintheti az eredményt, vagy egyszerűen befejezheti a tevékenységet.

> [!NOTE]
> `remediateCompliance()`regisztrálja a fiókot, és megkísérli a regisztrálást.  Ha a fő jogkivonat beszerzése megtörtént, a hívás `registerAccountForMAM()` nem szükséges, de ez nem okoz kárt. Ha azonban az alkalmazás nem tudja megnyerni a jogkivonatot, és el szeretné távolítani a felhasználói fiókot, a felhasználónak `unregisterAccountForMAM()` meg kell hívnia a fiók eltávolítását, és meg kell akadályoznia a háttérben történő regisztrációt.

## <a name="protecting-backup-data"></a>Biztonságimásolat-adatok védelme
Az Android Marshmallow (API 23) esetében az Android két módszert kínál az alkalmazásoknak az adataik biztonsági mentéséhez. Mindegyik lehetőség elérhető az alkalmazás számára, de különböző lépések végrehajtását igényli az Intune-adatvédelem megfelelő megvalósításához. Az alábbi táblázatban áttekintheti a megfelelő adatvédelmi működéshez szükséges műveleteket.  A biztonsági mentési módszerek részletes ismertetését az [Android API útmutatójában](https://developer.android.com/guide/topics/data/backup.html) olvashatja el.

### <a name="auto-backup-for-apps"></a>Alkalmazások automatikus biztonsági mentése
Az Android az Android Marshmallow rendszerű eszközökre telepített alkalmazásokhoz kezdte el kínálni a Google Drive-ra történő [automatikus teljes biztonsági mentést](https://developer.android.com/guide/topics/data/autobackup.html), függetlenül az alkalmazások cél API-jától. Ha az AndroidManifest.xml fájlban explicit módon **false** értékűre állítja az `android:allowBackup` attribútumot, akkor az alkalmazás soha nem kerül az Android által végrehajtott biztonsági mentések várólistájára, és a „vállalati” adatok megmaradnak az alkalmazásban. Ebben az esetben nincs további teendő.

Alapértelmezés szerint azonban az `android:allowBackup` attribútum true értékű még akkor is, ha az `android:allowBackup` nincs megadva a jegyzékfájlban. Ez azt jelenti, hogy az alkalmazások összes adatáról automatikus biztonsági másolat készül a felhasználó Google Drive-fiókjába, és ez olyan alapértelmezett működés, amely **adatszivárgási kockázatot** vet fel. Ezért az SDK az alább leírt módosításokat követeli meg az adatvédelem alkalmazásának biztosításához.  Fontos követnie az alábbi az irányelveket az ügyféladatok megfelelő védelme érdekében, ha az alkalmazást Android Marshmallow rendszerű eszközökön szeretné futtatni.  

Az Intune lehetővé teszi az Android összes elérhető [automatikus biztonsági mentési funkciójának](https://developer.android.com/guide/topics/data/autobackup.html) használatát, beleértve az egyéni szabályok definiálását XML-ben, de az adatok védelme érdekében követnie kell az alábbi lépéseket:

1. Ha az alkalmazás **nem** saját BackupAgentet használ, az alapértelmezett MAMBackupAgent használatával engedélyezheti az Intune szabályzatainak megfelelő automatikus teljes biztonsági mentéseket. Helyezze el az alábbi kódrészletet az alkalmazás jegyzékfájljában:

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```
    
2. **[nem kötelező]** Amennyiben saját BackupAgent implementálása mellett döntött, mindenképpen a MAMBackupAgent vagy a MAMBackupAgentHelper osztályt kell használnia. Lásd a következő szakaszokat. Fontolja meg az áttérést az Intune (az 1. lépésben ismertetett) **MAMDefaultFullBackupAgent** osztályának használatára, amely egyszerű biztonsági mentést tesz lehetővé Android M-en és újabb rendszereken.

3. Amikor eldönti, hogy az alkalmazásról milyen típusú teljes biztonsági mentés készüljön (szűretlen, szűrt, semmilyen), az `android:fullBackupContent` attribútumot be kell állítania igaz vagy hamis értékűre vagy egy XML-erőforrásra az alkalmazásban.

4. Minden, az `android:fullBackupContent` attribútumban elhelyezett adatot _**kötelező**_ egy `com.microsoft.intune.mam.FullBackupContent` nevű metaadatcímkébe másolni.

    **1. példa**: Ha azt szeretné, hogy az alkalmazás kizárások nélkül teljes biztonsági mentést készítsen, `android:fullBackupContent` állítsa az `com.microsoft.intune.mam.FullBackupContent` attribútumot és a metaadatok címkéjét **igaz**értékre:

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **2. példa**: Ha azt szeretné, hogy az alkalmazás használja az egyéni BackupAgent, és letiltsa a teljes, Intune-szabályzatoknak megfelelő, automatikus biztonsági mentést, állítsa **hamis**értékre az attribútumot és a metaadatok címkéjét:

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **3. példa**: Ha azt szeretné, hogy az alkalmazás egy XML-fájlban meghatározott egyéni szabályoknak megfelelően teljes biztonsági mentést készítsen, állítsa az attribútumot és a metaadatok címkéjét ugyanarra az XML-erőforrásra:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```

### <a name="keyvalue-backup"></a>Kulcs/érték biztonsági mentés
A [Key/Value Backup](https://developer.android.com/guide/topics/data/keyvaluebackup.html) (Kulcs/érték biztonsági mentés) lehetőség minden 8-as vagy újabb verziójú API számára elérhető, és az [Android Backup Service](https://developer.android.com/google/backup/index.html) szolgáltatásba tölti fel az adatokat, felhasználónként legfeljebb 5 MB-nyit. A Key/Value Backup használata esetén **BackupAgentHelper** vagy **BackupAgent** osztályt kell használni.

### <a name="backupagenthelper"></a>BackupAgentHelper
A BackupAgentHelper osztályt mind a natív androidos funkciókat, mind az Intune MAM-integrációt tekintve jóval egyszerűbb implementálni, mint a BackupAgentet. A BackupAgentHelper lehetővé teszi, hogy a fejlesztő teljes fájlokat és közös beállításokat regisztráljon rendre egy **FileBackupHelper** és egy **SharedPreferencesBackupHelper** osztályban, amelyek ezután létrehozáskor hozzáadódnak a BackupAgentHelper osztályhoz. Az alábbi lépéseket követve használhat BackupAgentHelper osztályt az Intune MAM-szolgáltatással:

1. Ha többidentitásos biztonsági mentést szeretne használni a BackupAgentHelper osztállyal, kövesse az [Extending BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper) (A BackupAgentHelper kiterjesztése) című angol nyelvű Android-útmutatót.

2. Osztályával terjessze ki a BackupAgentHelper, a FileBackupHelper és a SharedPreferencesBackupHelper osztályok MAM-os megfelelőjét.

|Androidos osztály | MAM-os megfelelő |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Ezen irányelvek betartása elősegíti a sikeres, többidentitásos biztonsági mentést és visszaállítást.

### <a name="backupagent"></a>BackupAgent

A BackupAgent segítségével sokkal egyértelműbben adható meg, hogy mely adatokról készüljön biztonsági mentés. Mivel az implementálás nagyrészt a fejlesztő felelőssége, több lépésre van szükség az Intune megfelelő adatvédelmének biztosításához. Azáltal, hogy a munka nagyobb része a fejlesztőre hárul, az Intune-integráció itt valamivel több jelentőséggel bír.

**MAM-integráció:**

1. Gondosan tanulmányozza át a [Key/Value Backup](https://developer.android.com/guide/topics/data/keyvaluebackup.html) (Kulcs/érték biztonsági mentés) és főleg az [Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) (A BackupAgent kiterjesztése) című Android-útmutatókat annak érdekében, hogy a BackupAgent-implementáció biztosan megfeleljen az androidos irányelveknek.

2. Osztályával terjessze ki a `MAMBackupAgent` osztályt.

**Többidentitásos biztonsági mentés:**

1. A biztonsági mentés megkezdése előtt ellenőrizze, hogy **a rendszergazda valóban engedélyezte-e** a szóban forgó fájlok vagy adatpufferek biztonsági mentését többidentitásos környezetben. Erre a célra szolgál a `MAMFileProtectionManager` és `MAMDataProtectionManager` osztályokban szereplő `isBackupAllowed` függvény. Ha valamely fájl vagy adatpuffer biztonsági mentése nem engedélyezett, azt ne vonja be a biztonsági mentésbe.

2. Ha a biztonsági mentés egy pontján biztonsági másolatot szeretne készíteni az 1. lépésben ellenőrzött fájlokhoz tartozó identitásokról, a `backupMAMFileIdentity(BackupDataOutput data, File … files)` függvényt kell meghívnia azokkal a fájlokkal, amelyekből adatokat szeretne kinyerni. Ez a művelet automatikusan új biztonsági mentési entitásokat hoz létre, és a `BackupDataOutput` kimenetre írja azokat. Ezeket az entitásokat automatikusan felhasználja a program a visszaállítás során.

**Többidentitásos visszaállítás:**

Az adatok biztonsági mentésével kapcsolatos Android-útmutatóban meg van adva egy általános algoritmus az alkalmazásadatok visszaállításához, az [Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) (A BackupAgent kiterjesztése) című szakaszban pedig kódminta is található. A sikeres, többidentitásos visszaállítás érdekében kötelező a kódmintában megadott általános struktúrát követni, különös tekintettel az alábbiakra:

1. A biztonsági mentési entitások átlépéséhez `while(data.readNextHeader())` hurkot kell használnia. Az előző kódban a `data` a helyi változó neve, amely az alkalmazásnak a visszaállításkor átadott **MAMBackupDataInput** .

2. Meg kell hívnia a `data.skipEntityData()` értéket, ha a `data.getKey()` nem egyezik a `onBackup` által írt kulccsal. Enélkül előfordulhat, hogy a visszaállítások nem járnak sikerrel. Az előző kódban a `data` a helyi változó neve, amely az alkalmazásnak a visszaállításkor átadott **MAMBackupDataInput** .

3. Ne térjen vissza a `while(data.readNextHeader())` konstruktorban található biztonsági mentési entitások fogyasztása során, mert az automatikusan írt entitások elvesznek. Az előző kódban a `data` a helyi változó neve, amely az alkalmazásnak a visszaállításkor átadott **MAMBackupDataInput** .

## <a name="multi-identity-optional"></a>Többszörös identitás (nem kötelező)

### <a name="overview"></a>Áttekintés
Az Intune App SDK alapértelmezés szerint az alkalmazás egészére alkalmazza a szabályzatot. A többszörös identitás az Intune-alkalmazásvédelem választható funkciója, amelynek engedélyezése esetén a szabályzatok identitásonként alkalmazhatók. Ez a többi alkalmazásvédelmi funkciónál jelentősen nagyobb mértékű közreműködést igényel az alkalmazástól.

> [!NOTE]
> Az alkalmazás megfelelő közreműködésének elmulasztása adatszivárgásokat és egyéb biztonsági problémákat okozhat.

Ha a felhasználó már beléptette az eszközt vagy az alkalmazást, az SDK regisztrálja ezt az identitást, és ezt tekinti az Intune-ban felügyelt elsődleges identitásnak. Az alkalmazás többi felhasználójával nem felügyeltként bánik, szabályzatbeállításaik korlátlanok.

> [!NOTE]
> Jelenleg eszközönként csak egy Intune által felügyelt identitás támogatott.

Az identitás sztringként van definiálva. Az identitásokban **nem számítanak különbözőnek a kis- és a nagybetűk**, és az SDK nem feltétlen olyan kis- és nagybetűkkel adja vissza a tőle kért identitásokat, mint ahogyan az az identitás beállításakor eredetileg meg volt adva.

Az alkalmazásnak tájékoztatnia *kell* az SDK-t, ha módosítani kívánja az aktív identitást. Egyes esetekben az SDK is értesíti az alkalmazást, ha identitásváltás szükséges. A legtöbb esetben azonban MAM nem ismeri a felhasználói felületen éppen megjelenített, vagy egy adott időben egy szálon használt adatokat, és az alkalmazásra hagyatkozik a helyes identitás beállításához az adatvesztés elkerülése érdekében. A következő szakaszokban néhány, az alkalmazás műveletét igénylő helyzetet tüntetünk fel.

### <a name="enabling-multi-identity"></a>A többszörös identitás engedélyezése
Alapértelmezés szerint az összes alkalmazás egyszeres identitással rendelkező alkalmazásnak minősül. Az AndroidManifest.xml-ben elhelyezett alábbi metaadatokkal lehet jelezni, hogy egy alkalmazás képes több identitás kezelésére.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Az identitás beállítása
A fejlesztők (csökkenő prioritási sorrendben) a következő szinteken állíthatják be az alkalmazás identitását:

  1. Szál szintje
  2. `Context`(általában `Activity`) szint
  3. Folyamat szintje

A szál szintjén beállított identitás felülírja a Context szintjén beállított identitást, és a `Context` szinten beállított identitás felülírja a folyamat szintjén beállított identitást. Az a `Context` alkalmazásban beállított identitás csak a megfelelő kapcsolódó helyzetekben használatos. A fájl i/o-műveleteihez például nincs társítva `Context`. Az alkalmazások leggyakrabban az `Context` identitást `Activity`fogják beállítani. Egy alkalmazás csak akkor jelenítheti meg a felügyelt identitás adatait `Activity` , ha az identitás ugyanarra az identitásra van beállítva. A folyamatszintű identitás általában csak akkor hasznos, ha az alkalmazás egyszerre csak egy-egy felhasználóval működik az összes szálon. Számos alkalmazásnak nem feltétlenül kell igénybe vennie.

Ha az alkalmazás a környezetet `Application` használja a rendszerszolgáltatások beolvasásához, győződjön meg arról, hogy a szál vagy a folyamat identitása be van állítva, vagy hogy beállította `Application` a felhasználói felület identitását az alkalmazás környezetében.

Ha speciális eseteket szeretne kezelni a felhasználói felület identitásának `switchMAMIdentity`a vagy a szolgáltatással való `setUIPolicyIdentity` frissítésekor, mindkét `IdentitySwitchOption` metódus egy adott értékeket adhat át.

* `IGNORE_INTENT`: Akkor használja, ha olyan Identity kapcsolót kér, amely figyelmen kívül hagyja az aktuális tevékenységhez társított szándékot.
  Példa:

  1. Az alkalmazás egy felügyelt dokumentumot tartalmazó felügyelt identitástól kapott szándékot, és az alkalmazás megjeleníti a dokumentumot.
  2. A felhasználó személyes identitására vált, így az alkalmazás a felhasználói felület identitásának kapcsolóját kéri. A személyes identitásban az alkalmazás már nem jeleníti meg a dokumentumot, így az Identity `IGNORE_INTENT` kapcsoló kérésekor lesz használatban.

  Ha nincs beállítva, az SDK azt feltételezi, hogy a legutóbbi szándék továbbra is használatban van az alkalmazásban. Ennek hatására a rendszer megkapja az új identitásra vonatkozó házirendet, hogy a szándékot a bejövő adatokként kezelje, és az identitását használja.

>[!NOTE]
> Mivel a `CLIPBOARD_SERVICE` a felhasználói felületi műveletekhez használatos, az SDK az előtéri `ClipboardManager` tevékenység felhasználói felületének identitását használja a műveletekhez.
> A `MAMPolicyManager` következő metódusaival lehet beállítani az identitást, illetve beolvasni a korábban beállított identitásértékeket.

```java
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback, final EnumSet<IdentitySwitchOption> options);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> Az alkalmazás identitását null értékre állítva törölheti.
>
> Az üres sztring használható olyan identitásként, amelyre biztosan nem vonatkozik alkalmazásvédelmi szabályzat.

#### <a name="results"></a>Eredmény
Az identitást beállító összes metódus a `MAMIdentitySwitchResult` objektummal adja vissza az eredményértékeket. Négy visszaadható érték van:

| Visszatérési érték | Forgatókönyv |
|--            |--        |
| `SUCCEEDED`    | Az identitásváltás sikeres volt. |
| `NOT_ALLOWED`  | Az identitásváltás nem engedélyezett. Ez akkor fordul elő, ha kísérlet történt a felhasználói felület (`Context`) identitás beállítására, ha egy másik identitás van beállítva az aktuális szálon. |
| `CANCELLED`    | A felhasználó megszakította az identitásváltást. Ez általában úgy történik, hogy megnyomja a Vissza gombot egy PIN-kódot kérő vagy hitelesítési üzenetnél. |
| `FAILED`       | Az identitásváltás ismeretlen okból nem sikerült.|

Az alkalmazásnak biztosítania kell, hogy az identitás-kapcsoló sikeres legyen a vállalati adatok megjelenítése vagy használata előtt. Jelenleg a folyamat- és a szálidentitás-váltások mindig sikeresek lesznek a több identitást támogató alkalmazások esetén, azonban fenntartjuk a jogot hibafeltételek hozzáadására. A felhasználói felület identitásváltása sikertelen lehet érvénytelen argumentumok esetén, ha az ütközne a szálidentitással, vagy ha a felhasználó a feltételes indítási követelményeit megszakítja (pl. a Vissza gombra kattint a PIN-kód képernyőn). A sikertelen felhasználói felület identitásának alapértelmezett viselkedése egy tevékenységen a tevékenység befejezése (lásd a következőt: @no__t – 0).

Ha a `Context` identitást `setUIPolicyIdentity` értékre állítja, az eredmény aszinkron módon lesz jelentve. Ha a `Context` egy `Activity`, az SDK nem tudja, hogy az identitás sikeres volt-e, amíg el nem végzi a feltételes indítást, ami szükségessé teheti a felhasználónak a PIN-kód vagy a vállalati hitelesítő adatok megadását. Az alkalmazás megadhat egy `MAMSetUIIdentityCallback` értéket, hogy megkapja ezt az eredményt, vagy a visszahívási objektum nullát is megadhatja. Vegye figyelembe, hogy ha egy hívást kezdeményeznek `setUIPolicyIdentity`-ra, míg egy előző, az adott *kontextusban* `setUIPolicyIdentity` hívás eredményét még nem szállították el, az új visszahívás felülírja a régit, és az eredeti visszahívás soha nem fog eredményül jutni.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

A tevékenységek identitását közvetlenül a `MAMActivity` egy metódusával, a `MAMPolicyManager.setUIPolicyIdentity` meghívása nélkül is beállíthatja. A metódus az alábbi:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

Az `MAMActivity` osztály metódusát felül is lehet bírálni, ha azt szeretné, hogy az alkalmazás értesítést kapjon a tevékenység identitásának módosítására tett kísérletek eredményéről.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Ha nem bírálja felül `onSwitchMAMIdentityComplete` (vagy hívja meg `super` a metódust), egy tevékenység sikertelen identitás-kapcsolója azt eredményezi, hogy a tevékenység befejeződik. Ha felülbírálja a metódust, ügyelnie kell arra, hogy a vállalati adatok nem jelennek meg egy sikertelen identitás-kapcsoló után.

>[!NOTE]
> Előfordulhat, hogy az identitásváltás után újból létre kell hozni a tevékenységet. Ebben az esetben a `onSwitchMAMIdentityComplete` visszahívása lesz elküldve a tevékenység új példányának.


### <a name="implicit-identity-changes"></a>Az identitás implicit megváltoztatása
Az alkalmazás identitásbeállítási képessége mellett a szálak és a környezetek identitása megváltoztatható a más, alkalmazásvédelmi szabályzattal ellátott Intune által kezelt alkalmazásból beérkező adatok alapján is.

#### <a name="examples"></a>Példák
1. Ha például egy tevékenység egy másik MAM-alkalmazás által küldött `Intent` alapján indul el, akkor a tevékenység identitása a másik alkalmazásban az `Intent` elküldésekor érvényes identitás alapján lesz beállítva.

2. A szolgáltatások esetében a szál identitása hasonlóan lesz beállítva az `onStart`- vagy az `onBind`-hívások időtartamára. Átmenetileg a `Binder`-be érkező, az `onBind` által visszaadott hívások is beállítják a szál identitását.

3. A beérkező hívások a `ContentProvider` esetében is hasonlóképpen beállítják a szál identitását az időtartamukra vonatkozóan.


    Ezenkívül a tevékenységekkel kapcsolatos felhasználói beavatkozások is előidézhetnek implicit identitásváltást.

    **Példa:** Ha egy felhasználó megszakítja az engedélyezési kérést `Resume` , az egy üres identitásra irányuló implicit kapcsolót fog eredményezni.

    Lehetőség van arra, hogy az alkalmazás értesüljön ezekről a váltásokról, és szükség esetén megtiltsa őket. A `MAMService` és a `MAMContentProvider` a következő, az alosztályok által felülbírálható metódust teszi elérhetővé:

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchResultCallback callback);
    ```

    A `MAMActivity` osztályban a metódusnak még egy paramétere van:

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchReason reason,
      final AppIdentitySwitchResultCallback callback);
    ```

    * Az `AppIdentitySwitchReason` rögzíti az implicit váltás forrását, és a következő értékeket tudja fogadni: `CREATE`, `RESUME_CANCELLED` és `NEW_INTENT`.  A `RESUME_CANCELLED` ok akkor használható, amikor a tevékenység folytatása PIN-kódot kérő, hitelesítési vagy egyéb megfelelőségi felhasználói felület megjelenítését idézi elő, és a felhasználó megpróbál kilépni erről a felhasználói felületről, általában a Vissza gomb használatával.


    * Az `AppIdentitySwitchResultCallback` a következőképpen történik:

      ```java
      public interface AppIdentitySwitchResultCallback {
          /**
            * @param result
            *            whether the identity switch can proceed.
            */
          void reportIdentitySwitchResult(AppIdentitySwitchResult result);
        }
        ```

      Az ```AppIdentitySwitchResult``` értéke `SUCCESS` vagy `FAILURE`.

Az `onMAMIdentitySwitchRequired` metódus hívandó az összes implicit identitásváltás esetében, kivéve azokat, amelyek a `MAMService.onMAMBind` által visszaadott Binderen keresztül történtek. Az `onMAMIdentitySwitchRequired` alapértelmezett implementációi a következő metódusokat hívják meg azonnal:

* `reportIdentitySwitchResult(FAILURE)`Ha ennek az oka `RESUME_CANCELLED`van.

* `reportIdentitySwitchResult(SUCCESS)` – minden más esetben.

  Nem valószínű, hogy az alkalmazások többségének másképpen kell blokkolnia vagy késleltetnie az identitásváltást, de ha mégis erre van szükség, akkor a következő szempontokat kell figyelembe venni:

  * Az identitásváltás blokkolásakor az eredmény ugyanaz lesz, mint amikor a `Receive` megosztási beállítások tiltják le az adatok beérkezését.

  * Ha egy szolgáltatás a főszálon fut, a `reportIdentitySwitchResult` hívását **kötelező** szinkron módon végrehajtani, ellenkező esetben a felhasználói felület szála leáll.

  * A **`Activity`** létrehozáselőtt`onMAMCreate`a rendszer a következőt fogja hívni:. `onMAMIdentitySwitchRequired` Ha az alkalmazásnak felhasználói felületet kell megjelenítenie annak megállapításához, hogy engedélyezhető-e az identitásváltás, akkor az adott felhasználói felületet *egy másik* tevékenységgel kell megjeleníteni.

  * Ha a-ben az üres identitásra való áttérést kéri `RESUME_CANCELLED`a rendszer, az alkalmazásnak módosítania kell a folytatott tevékenységet az adott Identity kapcsolóval összhangban lévő adatok megjelenítéséhez. **`Activity`**  Ha ez nem lehetséges, az alkalmazásnak el kell utasítania a váltást, és újból kérnie kell a felhasználót a folytatáshoz használt identitás szabályzatának teljesítésére (például a PIN-kód megadását kérő képernyőt megjelenítve).

    > [!NOTE]
    > A többszörös identitást támogató alkalmazások mindig fogadják a felügyelt és a nem felügyelt alkalmazásoktól érkező adatokat. Az alkalmazás feladata, hogy felügyelt módon kezelje a felügyelt identitásokból érkező adatokat.

  Ha a kért identitás felügyelt (ezt a `MAMPolicyManager.getIsIdentityManaged` metódussal lehet ellenőrizni), de az alkalmazás nem tudja használni a fiókot (például mert a fiókokat, így az e-mail-fiókokat először be kell állítani az alkalmazásban), akkor el kell utasítania az identitásváltást.

#### <a name="build-plugin--tool-considerations"></a>A build beépülő modullal/-eszközzel kapcsolatos szempontok
Ha nem ad explicit módon `MAMActivity`öröklést `MAMService`, vagy `MAMContentProvider` (mivel engedélyezte a Build-eszközkészletet a módosítás végrehajtásához), de továbbra is képesnek kell lennie az identitás-kapcsolók `MAMActivityIdentityRequirementListener` feldolgozására `Activity`, akkor ehelyett implementálhatja ( (a `Service` vagy`ContentProviders`aesetében). `MAMIdentityRequirementListener`
A `MAMActivity.onMAMIdentitySwitchRequired` alapértelmezett viselkedése a `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)` statikus metódus meghívásával érhető el.

Ehhez hasonlóan, ha felül kell bírálnia a `MAMActivity.onSwitchMAMIdentityComplete` osztályt, akkor implementálhatja a `MAMActivityIdentitySwitchListener` osztályt anélkül, hogy explicit módon örökölné a `MAMActivity` osztálytól.

### <a name="preserving-identity-in-async-operations"></a>Identitás megőrzése aszinkron műveleteknél
Gyakran előfordul a felhasználói felület szálán végrehajtott műveleteknél, hogy más szálaknak adnak át háttérfeladatokat. A többszörös identitást támogató alkalmazásoknak biztosítaniuk kell, hogy ezek a háttérfeladatok a megfelelő identitással fussanak, mely gyakran megegyezik az átadást végző tevékenység identitásával. A MAM SDK a `MAMAsyncTask` és a `MAMIdentityExecutors` osztály biztosításával nyújt segítséget az identitás megőrzéséhez.
Ezeket akkor kell használni, ha az aszinkron művelet egy fájlba írhatja a vállalati adatforrásokat, vagy más alkalmazásokkal kommunikálhat.

#### <a name="mamasynctask"></a>MAMAsyncTask
A használatához `MAMAsyncTask`egyszerűen örökölje a parancsot, `AsyncTask` és `doInBackground` cserélje le a és `onPreExecute` a és a `doInBackgroundMAM` `onPreExecuteMAM` rendszer felülbírálásait. A `MAMAsyncTask` konstruktorának paramétereként meg kell adnia a tevékenység kontextusát. Példa:

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
}
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
A `MAMIdentityExecutors` osztály segítségével az `Executor`- és `ExecutorService`-példányokat identitást megőrző `Executor`/`ExecutorService` osztályba burkolhatja a `wrapExecutor` és a `wrapExecutorService` metódus használatával. Példa:

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>Fájlvédelem
Amikor létrehozza a fájlokat, a rendszer identitást társít hozzájuk a szál és a folyamat identitása alapján. Ez az identitás lesz használva a fájltitkosításhoz és a szelektív törléshez is. Csak azok a fájlok lesznek titkosítva, amelyek identitása felügyelt, és szabályzata előírja a titkosítást. Az SDK alapértelmezett szelektív törlése csak azokat a felügyelt identitáshoz tartozó fájlokat fogja törölni, amelyekre törlést kértek. Az alkalmazás a `MAMFileProtectionManager` osztállyal kérdezheti le vagy módosíthatja a fájlok identitását.

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *       Identity to set.
    * @param file
    *       File to protect.
    *
    * @throws IOException
    *       If the file cannot be protected.
    */
   public static void protect(final File file, final String identity) throws IOException;

   /**
     * Protect a file obtained from a content provider. This is intended to be used for
     * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
     * It may also be used with descriptors referring to private files owned by this app.
     * It is not intended to be used for files owned by other apps and such usage will fail. If
     * creating a new file via a content provider exposed by another MAM-integrated app, the new
     * file identity will automatically be set correctly if the ContentResolver in use was
     * obtained via a Context with an identity or if the thread identity is set.
     *
     * This will synchronously trigger whatever protection is required for the file, and will tag
     * the file for future protection changes. If an identity is set on a directory, it is set
     * recursively on all files and subdirectories. If MAM is operating in offline mode, this
     * method will silently do nothing.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
     */
    public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

}

public interface MAMFileProtectionInfo {
    String getIdentity();
}
 ```

#### <a name="app-responsibility"></a>Alkalmazás feladatköre
A MAM nem következtethet automatikusan kapcsolatra a beolvasott fájlok és egy `Activity` által megjelenített adatok között. Az alkalmazásoknak a vállalati adatok megjelenítése előtt be *kell* állítaniuk a megfelelő felhasználóifelület-identitást. Ez érvényes a fájlokból beolvasott adatokra is. Az alkalmazáson kívüli forrásból (ami lehet egy `ContentProvider` vagy egy nyilvánosan írható hely) származó fájlok esetén az alkalmazásnak meg *kell* kísérelnie a fájl identitásának megállapítását (a `MAMFileProtectionManager.getProtectionInfo` használatával), mielőtt megjelenítené a fájlból beolvasott információt. Ha a `getProtectionInfo` nem null, nem üres identitást jelez, a felhasználói felület identitását azzal egyezőre *kell* beállítani (a `MAMActivity.switchMAMIdentity` vagy a `MAMPolicyManager.setUIPolicyIdentity` használatával). Ha az identitásváltás nem sikerül, a fájl adatait *nem szabad* megjeleníteni.

A folyamat lehet például a következőhöz hasonló:
* A felhasználó kiválasztja az alkalmazásban megnyitni kívánt dokumentumot.
  * A megnyitott folyamat során az adatok lemezről való olvasása előtt az alkalmazás megerősíti a tartalom megjelenítéséhez használandó identitást:

    ```java
    MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    if (info != null)
        MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback, EnumSet.noneOf<IdentitySwitchOption.class>)
    ```

  * Az alkalmazás addig vár, amíg vissza nem jelenti a visszahívás eredményét.
  * Ha a jelentett eredmény hiba, az alkalmazás nem jeleníti meg a dokumentumot.
* Megnyílik az alkalmazás, és megjeleníti a fájlt.
  
#### <a name="single-identity-to-multi-identity-transition"></a>Egyetlen identitás a többszörös identitás átváltásához
Ha egy korábban az egyidentitású Intune-integrációval kiadott alkalmazás több identitást is integrál, a korábban telepített alkalmazások átmeneti állapotba kerülnek (nem látható a felhasználó számára, nincs társított UX). Az alkalmazásnak nem *szükséges* explicitnek lennie ahhoz, hogy kezelni tudja ezt az áttérést. Az áttérés előtt létrehozott összes fájl felügyelt állapotba kerül (tehát titkosítva marad, ha a titkosítási házirend be van kapcsolva). Ha szeretné, a frissítés `MAMFileProtectionManager.protect` észlelésével azonosíthatja az adott fájlokat vagy címtárakat az üres identitással (amely titkosítva fogja törölni a titkosítást).

#### <a name="offline-scenarios"></a>Kapcsolat nélküli forgatókönyvek
A fájl identitásának címkézésénél az offline mód különbségnek számít. A következő szempontokat kell figyelembe venni:

* Ha a Céges portál nincs telepítve, akkor a fájlok nem láthatók el identitáscímkével.

* Ha a Céges portál telepítve van, de az alkalmazásra nem vonatkozik Intune MAM-szabályzat, akkor a fájlokat nem lehet megbízhatóan ellátni identitáscímkével.

* Amikor elérhetővé válik a fájlok identitáscímkézése, akkor az összes korábban létrehozott fájl személyesként/nem felügyeltként (az üres karakterláncú identitáshoz tartozó fájlként) lesz kezelve, kivéve, ha az alkalmazás korábban egyidentitásos felügyelt alkalmazásként lett telepítve: ebben az esetben a fájlok a beléptetett felhasználóhoz tartozó fájlokként lesznek kezelve.

### <a name="directory-protection"></a>Könyvtárvédelem
A könyvtárakat is a fájlok védelmére szolgáló `protect` metódussal lehet védeni. A könyvtárvédelem rekurzívan érvényes a könyvtárban lévő összes fájlra és alkönyvtárra, illetve a benne létrehozott új fájlokra. Emiatt a nagy méretű könyvtárak esetében a `protect` hívás hosszabb ideig tarthat. Éppen ezért a sok fájlt tartalmazó könyvtárakra védelmet alkalmazó alkalmazásoknak érdemes a `protect` hívást aszinkron módon, háttérszálon futtatni.

### <a name="data-protection"></a>Adatvédelem
A fájlok nem címkézhetők meg több identitáshoz tartozó fájlként. Azok az alkalmazások, amelyeknek egy fájlban kell tárolniuk különböző felhasználók adatait, manuálisan tehetik meg ezt a `MAMDataProtectionManager` által biztosított szolgáltatásokkal. Ez lehetővé teszi az alkalmazás számára az adatok titkosítását és hozzákötését egy adott felhasználóhoz. A titkosított adatok lemezen, fájlban tárolhatók. Az identitáshoz tartozó adatokat lekérdezheti, és az adatokat visszafejtheti.

A `MAMDataProtectionManager` osztályt hasznosító alkalmazásoknak fogadót kell implementálniuk a `MANAGEMENT_REMOVED` értesítéshez. Az értesítés lefutása után az ezen osztállyal védett pufferek nem lesznek olvashatóak, ha a fájltitkosítást a pufferek védett állapotában kapcsolták be. Az alkalmazás az értesítés során az összes puffer meghívásával `MAMDataProtectionManager.unprotect` javíthatja ezt a helyzetet. Az értesítés időtartama alatt a protect metódust is biztonságosan meg lehet hívni, ha az identitásadatokat meg szeretnék őrizni – a titkosítás ez idő alatt garantáltan le van tiltva.

```java

public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
     * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
     *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
     *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
     *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
     *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
     * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
     *            stream must have been returned by a previous call to
     *            protect OR input.markSupported() must return true.
     *            Otherwise it will be impossible to get protection info
     *            without advancing the stream position. The stream must be
     *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
     *            returned by a previous call to protect() or a copy of
     *            such bytes.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```

### <a name="content-providers"></a>Tartalomszolgáltatók
`ParcelFileDescriptor` Ha az alkalmazás nem a-n `ContentProvider`keresztül biztosít vállalati adatokat, az alkalmazásnak meg `MAMContentProvider`kell hívnia a metódust `isProvideContentAllowed(String)` a alkalmazásban, a tulajdonos identitás UPN-fájljának (egyszerű felhasználóneve) átadásával a tartalomhoz. Ha ez a függvény hamis értéket ad vissza, akkor a tartalmat *nem szabad* visszaadnia a hívónak. A tartalomszolgáltatón keresztül visszaadott fájlleírók kezelése automatikusan a fájl identitása alapján történik.

Ha nem örökli `MAMContentProvider` explicit módon, és ehelyett engedélyezi a Build-eszközkészletet a módosítás elvégzéséhez, meghívhatja ugyanazt a metódus statikus verzióját: `MAMContentProvider.isProvideContentAllowed(provider,
contentIdentity)`.

### <a name="selective-wipe"></a>Szelektív törlés
Ha egy többidentitású alkalmazás regisztrál a `WIPE_USER_DATA` értesítésekre, akkor az alkalmazás felelőssége, hogy eltávolítsa a törölt felhasználóhoz tartozó összes adatot, ideértve az összes olyan fájlt is, amely meg lett jelölve az adott felhasználói identitáshoz tartozóként. Ha az alkalmazás eltávolítja a felhasználói adatokat egy fájlból, de a fájl többi adatát meg kívánja őrizni, akkor *mindenképp* meg kell változtatnia a fájl identitását (egy személyes felhasználóra vagy egy üres identitásra, a `MAMFileProtectionManager.protect` segítségével). Ha használ titkosítási szabályzatot, akkor a felhasználóhoz tartozó törlendő fájlokat a rendszer nem fejti vissza, és így ezek tartalma elérhetetlen lesz az alkalmazás számára a törlés után.

A `WIPE_USER_DATA` értesítésekre regisztráló alkalmazások nem részesülnek az SDK alapértelmezett szelektív törlési funkciójának előnyeiben. A többidentitásos alkalmazások esetében ez nagyobb jelentőségű tényező lehet, mivel a MAM alapértelmezett szelektív törlése csak a törlendő identitáshoz tartozó fájlokat fogja törölni. Ha a többidentitásos alkalmazás szeretné végrehajtatni a MAM alapértelmezett szelektív törlését, _**és**_ ezenfelül saját törlési műveleteit is végre szeretné hajtani, akkor célszerű feliratkoznia a `WIPE_USER_AUXILIARY_DATA` értesítésekre. Ezt az értesítést az SDK közvetlenül azelőtt küldi el, hogy végrehajtaná a MAM alapértelmezett szelektív törlési műveletét. Egy alkalmazásnak soha nem kell regisztrálnia `WIPE_USER_AUXILIARY_DATA`mind a, mind `WIPE_USER_DATA` a esetében.

Az alapértelmezett szelektív törlés automatikusan lezárta az alkalmazást, befejezi a tevékenységeket, és megöli az alkalmazás folyamatát. Ha az alkalmazás felülbírálja az alapértelmezett szelektív törlést, érdemes lehet manuálisan bezárni az alkalmazást annak megakadályozása érdekében, hogy a felhasználó hozzáférjen a memóriában tárolt adatokhoz a törlés után.

## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Célzott MAM-konfiguráció engedélyezése Android-alkalmazásokhoz (nem kötelező)
Az alkalmazásspecifikus kulcs-érték párok az Intune-konzolon konfigurálhatók a [MAM-We](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) és az [Android Enterprise](https://docs.microsoft.com/intune/app-configuration-policies-use-android)rendszerhez.
A kulcs-érték párokat az Intune nem értelmezi, hanem továbbadja az alkalmazásnak. Azon alkalmazások, amelyek ilyen konfigurációt kívánnak kapni, a `MAMAppConfigManager` és `MAMAppConfig` osztályokat használhatják ehhez. Ha több szabályzat ugyanazon alkalmazást célozza, valószínűleg több ütköző érték érhető el ugyanazon kulcshoz.

> [!NOTE] 
> Konfigurációk beállítása a MAM-n keresztül történő kézbesítéshez – nem lehet delievered a `offline` (ha a Céges portál nincs telepítve).  Ebben az esetben csak az Android Enterprise AppRestrictions lesznek `MAMUserNotification` továbbítva egy üres identitáson keresztül.

### <a name="get-the-app-config-for-a-user"></a>Felhasználóhoz tartozó alkalmazás konfigurációjának beolvasása
Az alkalmazás konfigurációja a következőképpen kérhető le:
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
```

Ha nincs MAM-regisztrált felhasználó, de az alkalmazása továbbra is szeretné lekérni az androidos vállalati konfigurációt (amely nem egy adott felhasználóra vonatkozik), akkor null értékű vagy üres karakterláncot adhat át.

### <a name="conflicts"></a>Ütközik
A MAM-alkalmazás konfigurációjában beállított értékek felülbírálják az Android Enterprise config-ban ugyanazzal a kulccsal beállított értéket. 

Ha egy rendszergazda egymásnak ellentmondó értékeket állít be ugyanahhoz a kulcshoz (például a különböző alkalmazás-konfigurációs készletek azonos kulccsal való megcélzásával több, ugyanazt a felhasználót tartalmazó csoportra), az Intune nem oldja meg automatikusan ezt az ütközést, és minden értéket megtesz elérhető az alkalmazás számára. 

Az alkalmazás egy `MAMAppConfig` objektumból kérheti le az adott kulcs összes értékét:
```java
List<Boolean> getAllBooleansForKey(String key)
List<Long> getAllIntegersForKey(final String key)
List<Double> getAllDoublesForKey(final String key)
List<String> getAllStringsForKey(final String key)
```

vagy kérjen egy kiválasztott értéket:
```java
Boolean getBooleanForKey(String key, BooleanQueryType queryType)
Long getIntegerForKey(String key, NumberQueryType queryType)
Double getDoubleForKey(String key, NumberQueryType queryType)
String getStringForKey(String key, StringQueryType queryType)

enum BooleanQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns true if any of the values are true.
     */
    Or,
    /**
     * In case of conflict, returns false if any of the values are false.
     */
    And
}

enum NumberQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns the minimum Integer.
     */
    Min,
    /**
     * In case of conflict, returns the maximum Integer.
     */
    Max
}

enum StringQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns the first result ordered alphabetically.
     */
    Min,

    /**
     * In case of conflict, returns the last result ordered alphabetically.
     */
    Max
}
```

Az alkalmazás a kulcs-érték párok készletének listájára is kérheti a nyers adatmennyiséget.

```
List<Map<String, String>> getFullData()
```

### <a name="full-example"></a>Teljes példa
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
String fooValue = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    fooValue = chooseBestValue(values);
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
Long barValue = appConfig.getIntegerForKey("bar", MAMAppConfig.NumberQueryType.Min);
```

### <a name="notification"></a>Értesítés
Az alkalmazás konfigurációja egy új értesítéstípust ad hozzá:
* **REFRESH_APP_CONFIG**: A rendszer ezt az értesítést küldi `MAMUserNotification` el, és tájékoztatja az alkalmazásról, hogy az új alkalmazás-konfigurációs adatbázis elérhető.

### <a name="further-reading"></a>További olvasnivalók
A célzott MAM-alkalmazáskonfigurációs szabályzat Android rendszerben való létrehozásáról lásd [A Microsoft Intune alkalmazáskonfigurációs szabályzatainak használata Android rendszerben](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) célzott MAM-alkalmazáskonfigurációról szóló szakaszát.

Az alkalmazás konfigurációja a Graph API használatával is konfigurálható. További információ: [Graph API docs for MAM Targeted config](https://docs.microsoft.com/graph/api/resources/intune-mam-targetedmanagedappconfiguration).

## <a name="style-customization-optional"></a>Stílus testreszabása (nem kötelező)
A MAM SDK-ban létrehozott nézetek megjelenését testre lehet szabni, hogy jobban illeszkedjenek az SDK-t integráló alkalmazáshoz. Meg lehet szabni az elsődleges, a másodlagos és a háttérszínt, valamint az alkalmazás emblémájának méretét. Ez a testreszabás nem kötelező. Ha nincs konfigurálva egyéni stílus, a rendszer az alapértelmezéseket használja.

### <a name="how-to-customize"></a>A testreszabás menete
Ha módosítani szeretné az Intune MAM-nézeteinek stílusát, először készítsen stílus-felülíró XML-fájlt. Ezt helyezze el az alkalmazás „/res/xml” könyvtárában, és adjon neki tetszőleges nevet. Az alábbi példa bemutatja a fájl szükséges formátumát.

```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

Az alkalmazásban már meglévő erőforrásokat kell újrahasználnia, tehát például a zöld színt a colors.xml fájlban kell definiálni, és itt hivatkozni, de a „#0000ff” hexa színkódot itt nem használhatja. Az alkalmazásembléma legfeljebb 110 dip (dp) méretű lehet. Kisebb emblémát is megadhat, de az optimális megjelenés érdekében érdemes kihasználni a maximális méretet. Ha túllépi a 110 dipes határt, a képet a rendszer lekicsinyíti, amitől valószínűleg homályos lesz.

Alább felsoroljuk az összes megengedett stílusattribútumot, az általuk szabályozott felületi elemeket, XML-attribútumnevüket és a hozzájuk várt erőforrástípusokat.

|Stílusattribútum | Érintett felületi elem | Attribútumelem neve | Várt erőforrástípus |
| -- | -- | -- | -- |
| Háttérszín | A PIN-kódot bekérő képernyő háttérszíne <Br>A PIN-kód mezőjének kitöltőszíne | background_color | Szín |
| Előtérszín | Előtérbeli szöveg színe <br> A PIN-kód mezőjének szegélyszíne alapértelmezett állapotban <br> A PIN-kód mezőjébe beírt (akár rejtjelezett) karakterek színe| foreground_color | Szín|
| Kiemelőszín | A PIN-kód mezőjének szegélyszíne kiemelt állapotban <br> Hivatkozások |accent_color | Szín |
| Alkalmazás emblémája | Az Intune PIN-kódot bekérő képernyőjén megjelenő nagy ikon | logo_image | Rajzolható |

## <a name="default-enrollment-optional"></a>Alapértelmezés szerinti regisztráció (választható)
Az alábbiakban útmutatást találhat egy APP-WE szolgáltatás automatikus regisztrációjához szükséges, az alkalmazásindításkor megjelenő felhasználói kérés beállításához (ebben a szakaszban erre **alapértelmezett regisztráció** néven hivatkoztunk), valamint ahhoz, hogy hogyan kényszerítheti az Intune alkalmazásvédelmi szabályzatait, hogy csak az Intune által védett felhasználók használhassák a SDK-val integrált Android LOB-alkalmazást. A cikk emellett ismerteti, hogyan engedélyezhető az SSO az SDK-val integrált Android LOB-alkalmazáshoz. Ezt **nem** támogatják azok az áruházbeli alkalmazások, amelyeket nem Intune-felhasználók is használhatnak.

> [!NOTE] 
> Az **alapértelmezett regisztráció** előnyei közé tartozik egy egyszerűsített módszer az eszközön található alkalmazás az APP-WE szolgáltatástól lekért szabályzatához.

> [!NOTE] 
> Az **alapértelmezett regisztráció** a szuverén felhő.

Engedélyezze az alapértelmezett regisztrációt a következő lépésekkel:

1. Ha az alkalmazás integrálja az ADAL-t, vagy engedélyeznie kell az SSO-t, [konfigurálja a ADAL](#configure-azure-active-directory-authentication-library-adal) -t az [általános ADAL-konfigurációs](#common-adal-configurations) #2 után. Ha ez nem lehetséges, kihagyhatja ezt a lépést.
   
2. Engedélyezze az alapértelmezett regisztrációt úgy, hogy a következő értéket adja meg a jegyzékfájlban:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > Ez lehet az alkalmazás egyetlen MAM-WE-integrációja. Ha bármilyen más próbálkozás történik MAMEnrollmentManager API-k hívására, problémák merülnek fel.

3. A szükséges MAM-szabályzat engedélyezéséhez írja az alábbi értéket a jegyzékfájlba:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > Ez kényszeríti a felhasználót, hogy letöltse a Céges portált az eszközre, és a használat előtt elvégezze az alapértelmezett regisztrációt.

## <a name="limitations"></a>Korlátozások

### <a name="policy-enforcement-limitations"></a>Szabályzatbetartatási korlátozások

* **Tartalom**-feloldók használata: Az "átvitel vagy fogadás" Intune-szabályzat letilthatja vagy részlegesen blokkolhatja a tartalom-feloldó használatát egy másik alkalmazásban található tartalomszolgáltató eléréséhez. Ez azt eredményezi `ContentResolver` , hogy a metódusok null értéket adnak vissza, vagy hibát jeleznek `FileNotFoundException` ( `openOutputStream` például blokkolva lesznek). Az alkalmazás a következő hívással állapíthatja meg, hogy a tartalomfeloldón keresztüli adatírás sikertelenségét házirend okozta (vagy hogy egy házirend ilyen hibát okozna):

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    vagy ha nincs társított tevékenység:

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    A második esetben a több identitást használó alkalmazásoknak ügyelniük kell a szálidentitás megfelelő beállítására (vagy explicit identitásértéket kell átadniuk a `getPolicy` metódushívásban).

### <a name="exported-services"></a>Exportált szolgáltatások
Az Intune App SDK-ban szereplő AndroidManifest.xml fájlban szerepel a **MAMNotificationReceiverService** szolgáltatás, amelynek exportált szolgáltatásnak kell lennie ahhoz, hogy a Céges portál értesítéseket küldhessen a kezelt alkalmazásoknak. A szolgáltatás ellenőrzi a hívót annak ellenőrzéséhez, hogy csak a vállalati portál számára engedélyezett-e az értesítések küldése.

### <a name="reflection-limitations"></a>A reflexió korlátozásai
A MAM-alaposztályok némelyike (például `MAMActivity`, `MAMDocumentsProvider`) olyan metódusokat tartalmaz (az eredeti Android alaposztályok alapján), amelyek paraméter-vagy visszatérési típusokat használnak, csak bizonyos API-szintek felett jelennek meg. Ezen okból kifolyólag nem mindig enumerálható reflexióval az alkalmazás-összetevők összes metódusa. Ez a korlátozás nemcsak a MAM-ra érvényes, hanem akkor is jelentkezne, ha az alkalmazás saját maga implementálná az adott metódusokat az Android-alaposztályokból.

### <a name="robolectric"></a>Robolectric
A MAM SDK-funkcionalitás Robolectric keretrendszerrel való tesztelése nem támogatott. A MAM SDK-t a Robolectric alatt futó ismert problémák okozták, mivel a Robolectric alatt található viselkedések nem pontosan utánozzák a valós eszközökön vagy emulátorokon.

Ha tesztelni szeretné az alkalmazást a Robolectric alatt, az ajánlott megkerülő megoldás az, hogy az alkalmazás osztályának logikáját egy segítővé helyezze át, és az egység-tesztelési apk olyan alkalmazási osztállyal legyen létrehozva, amely nem örököl a MAMApplication.

## <a name="expectations-of-the-sdk-consumer"></a>Az SDK-használók elvárásai
Az Intune SDK fenntartja az Android API által biztosított szerződést, bár a szabályzatok betartatása miatt gyakrabban léphetnek fel hibaállapotok. Az alábbi androidos gyakorlati tanácsok csökkentik a hibák valószínűségét:

* Azon androidos SDK-függvények, amelyek null értékkel is visszatérhetnek, nagyobb valószínűséggel lesznek null értékűek.  A problémák minimalizálása érdekében biztosítsa, hogy a megfelelő helyeken legyenek null-ellenőrzések.

* A lekérdezhető funkciókat a MAM-os helyettesítő API-kkal kell lekérdezni.

* Minden származtatott függvénynek meg kell hívnia a szülőosztálybeli verzióját.

* Kerülje az API-k nem egyértelmű módon való használatát. Így például az `Activity.startActivityForResult` requestCode ellenőrzése nélküli használata működésbeli furcsaságokat idézhet elő.

## <a name="telemetry"></a>Telemetria

Az Androidhoz készült Intune App SDK nem szabályozza az alkalmazásából való adatgyűjtést. A Céges portál alkalmazás alapértelmezés szerint naplózza a rendszer által generált adattípusokat. Az adatokat az SDK a Microsoft Intune-nak küldi el. A Microsoft-szabályzatok alapján semmilyen személyes adatot nem gyűjtünk.

> [!NOTE]
> Ha a végfelhasználók nem szeretnének ilyen adatokat küldeni, ki kell kapcsolniuk a telemetriát a Céges portál alkalmazás Beállítások menüpontjában. További információt [A használatra vonatkozó adatok Microsoft általi gyűjtésének kikapcsolása](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android) című témakörben találhat. 

## <a name="recommended-android-best-practices"></a>Ajánlott gyakorlati tanácsok Androidon

* Lehetőség szerint minden kódtárprojektnek azonos android:package csomagot kell használnia. Ez nem fog szórványos hibákat jelenteni futásidőben, mivel ez a probléma pusztán a buildelés során áll fenn. Az Intune App SDK újabb verziói ki fognak küszöbölni bizonyos párhuzamosságokat.

* Mindig az elérhető legújabb Android SDK buildelőeszközeit használja.

* Távolítsa el a felesleges és használaton kívüli kódtárakat (például android.support.v4)

## <a name="testing"></a>Tesztelés
Tekintse meg a [tesztelési útmutatót](app-sdk-android-testing-guide.md).
