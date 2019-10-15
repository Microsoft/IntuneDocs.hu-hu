---
title: Microsoft Intune app SDK Androidhoz – fejlesztői útmutató
description: Az Androidhoz készült Microsoft Intune app SDK lehetővé teszi az Intune Mobile App Management (MAM) integrálását az Android-alkalmazásba.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/14/2019
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
ms.openlocfilehash: b4316c155645ad8e956cfd89c448da688ac133b3
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314559"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Microsoft Intune app SDK Androidhoz – fejlesztői útmutató

> [!NOTE]
> Érdemes elolvasnia az [Intune app SDK áttekintése](app-sdk.md)című cikket, amely ismerteti az SDK aktuális funkcióit, és leírja, hogyan készüljön fel az integrációra az egyes támogatott platformokon.

Az Androidhoz készült Microsoft Intune app SDK lehetővé teszi az Intune app Protection-szabályzatok (más néven **alkalmazás** -vagy MAM-szabályzatok) beépítését a natív Android-alkalmazásba. Az Intune által felügyelt alkalmazások egyike az Intune app SDK-val integrált. Az Intune-rendszergazdák egyszerűen telepíthetnek alkalmazás-védelmi szabályzatokat az Intune által felügyelt alkalmazásba, ha az Intune aktívan kezeli az alkalmazást.


## <a name="whats-in-the-sdk"></a>Az SDK ismertetése

Az Intune app SDK a következő fájlokból áll:

* **Microsoft. Intune. Mam. SDK.** alaptevékenység: az SDK-összetevők, kivéve a támogatási függvénytár jar-fájljait.
* **Microsoft. Intune. Mam. SDK. support. v4. jar**: a MAM azon alkalmazásokban való engedélyezéséhez szükséges osztályok, amelyek az Android v4 támogatási függvénytárat használják.
* **Microsoft. Intune. Mam. SDK. support. v7. jar**: a MAM azon alkalmazásokban való engedélyezéséhez szükséges osztályok, amelyek az Android v7 támogatási függvénytárat használják.
* **Microsoft. Intune. Mam. SDK. support. v17. jar**: a MAM azon alkalmazásokban való engedélyezéséhez szükséges osztályok, amelyek az Android v17 támogatási függvénytárat használják. 
* **Microsoft. Intune. Mam. SDK. support. Text. jar**: a MAM azon alkalmazásokban való engedélyezéséhez szükséges osztályok, amelyek a `android.support.text` csomagban az Android támogatási függvénytár osztályait használják.
* **Microsoft. Intune. Mam. SDK. DownlevelStubs.** féléves: ez az éves tevékenység olyan, az Android rendszerű rendszerosztályokat tartalmaz, amelyek csak az újabb eszközökön szerepelnek, de az `MAMActivity` metódusokban hivatkoznak rá. Az újabb eszközök figyelmen kívül hagyják ezeket a helyettes osztályokat. Ez az éves tevékenység csak abban az esetben szükséges, ha az alkalmazás a `MAMActivity` értékből származtatott osztályokra vonatkozó reflexiót hajt végre, és a legtöbb alkalmazásnak nem kell tartalmaznia. Az éves tevékenység az összes osztálya kizárására szolgáló rendszerállapot-szabályokat tartalmaz.
* **com. microsoft. Intune. Mam. Build. jar**: a Gradle beépülő modul [, amely az SDK integrálását segíti elő](#build-tooling).
* **Changelog. txt**: az egyes SDK-verziókban végrehajtott módosítások rekordját adja meg.
* **THIRDPARTYNOTICES. TXT**: az alkalmazásba lefordított, harmadik féltől származó és/vagy OSS-kódot igazoló jóváírási Megjegyzés.

## <a name="requirements"></a>Követelmények

### <a name="android-versions"></a>Android-verziók
Az SDK az Android API 19 (Android 4.4 +) használatát támogatja az Android API 28 használatával (Android 9,0).

### <a name="company-portal-app"></a>Céges portál alkalmazás
Az Androidhoz készült Intune app SDK az alkalmazás-védelmi szabályzatok engedélyezéséhez az eszközön a [céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) alkalmazás jelenlétén alapul. A Céges portál az Intune szolgáltatásból kéri le az alkalmazás-védelmi szabályzatokat. Az alkalmazás inicializálásakor betölti a szabályzatot és a kódot, hogy a házirendet érvényesítse a Céges portál.

> [!NOTE]
> Ha a Céges portál alkalmazás nem található az eszközön, az Intune által felügyelt alkalmazás ugyanúgy viselkedik, mint egy normál alkalmazás, amely nem támogatja az Intune app Protection-szabályzatokat.

Az eszközök regisztrációja nélküli alkalmazások védelméhez a felhasználónak _**nem**_ kell regisztrálnia az eszközt a céges portál alkalmazás használatával.

## <a name="sdk-integration"></a>SDK-integráció

### <a name="sample-app"></a>Minta alkalmazás
Az Intune app SDK-val való integrálásának példája a [githubon](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App)érhető el. Ez a példa a [Gradle Build beépülő modult](#gradle-build-plugin)használja.

### <a name="referencing-intune-app-libraries"></a>Az Intune-alkalmazás könyvtáraira hivatkozó

Az Intune app SDK egy szabványos androidos kódtár, amely nem rendelkezik külső függőségekkel. A **Microsoft. Intune. Mam. SDK.** az éves szerződés tartalmazza az alkalmazás-védelmi szabályzatok engedélyezéséhez szükséges interfészeket és a Microsoft Intune céges portál alkalmazással való együttműködéshez szükséges kódot.

A **Microsoft. Intune. Mam. SDK.** e-mailt az androidos függvénytár-hivatkozásként kell megadni. Ehhez nyissa meg az alkalmazás projektjét Android Studioban, és válassza a **fájl > új > új modul** lehetőséget, majd kattintson az importálás elemre **. JAR/.** Éves tevékenységi csomag. Ezután válassza ki a Microsoft. Intune. MAM. SDK. az androidos archív csomagot a modul létrehozásához. AAR. Kattintson a jobb gombbal az alkalmazás kódját tartalmazó modulra vagy modulokra, és válassza a **modul beállításai** > **függőségek fület**,  >  **+ ikon** > **modul** függőség > Válassza ki az imént létrehozott MAM SDK-val rendelkező modult > **OK gombra**. Ezzel biztosíthatja, hogy a modul a projekt létrehozásakor a MAM SDK-val legyen lefordítva.

Emellett a **Microsoft. Intune. Mam. SDK. support. xxx. jar** függvénytárak a megfelelő `android.support.XXX` függvénytárak Intune-változatait tartalmazzák. Nincsenek beépítve a Microsoft. Intune. MAM. SDK. e-mailt arra az esetre, ha egy alkalmazásnak nem kell a támogatási könyvtáraktól függ.

#### <a name="proguard"></a>ProGuard

Ha [a](http://proguard.sourceforge.net/) (vagy bármely más zsugorodó/eltorzító) mechanizmust a kiépítési lépésként használja, az SDK-nak további konfigurációs szabályokkal kell rendelkeznie, amelyeknek szerepelniük kell. A-t is beleértve. A buildben a szabályok automatikusan integrálva vannak a bevezetési lépésbe, és megőrzik a szükséges osztály-fájlokat.

A Azure Active Directory hitelesítési kódtárak (ADAL-EK) rendelkezhetnek saját korlátozásokkal. Ha az alkalmazás integrálja a ADAL-t, akkor a ADAL dokumentációját kell követnie ezekre a korlátozásokra.

### <a name="policy-enforcement"></a>Szabályzatbetartatás
Az Intune app SDK egy Android-könyvtár, amely lehetővé teszi, hogy az alkalmazás támogassa és részt vegyen az Intune-szabályzatok betartatásában. 

A legtöbb szabályzatot a rendszer félig automatikusan kényszeríti, de bizonyos szabályzatok az [alkalmazástól való kifejezett részvételt](#enable-features-that-require-app-participation)igénylik.
Függetlenül attól, hogy elvégezte-e a forrás-integrációt, vagy használja az integrációs eszközöket a kifejezetten részvételt igénylő szabályzatok használatához.

Az automatikusan érvényesített házirendek esetében az alkalmazásoknak több androidos alaposztályból származó öröklést kell cserélniük a MAM-vel egyenértékű örökléssel. A szükséges speciális cserék [alább](#class-and-method-replacements) láthatók, és manuálisan is elvégezhetők a forrás-integrációval, vagy automatikusan elvégezhető a Build-eszközökön keresztül.

### <a name="build-tooling"></a>Eszközök kiépítése
Az SDK Build-eszközöket (a Gradle-buildek beépülő modulját és a nem Gradle-buildekhez készült parancssori eszközt) biztosít, amelyekkel a rendszer automatikusan végrehajtja a MAM-alapú helyettesítő kihelyezéseket. Ezek az eszközök átalakítják a Java-fordítás által generált osztály-fájlokat, és nem módosítják az eredeti forráskódot.

Az eszközök csak [közvetlen cseréket](#class-and-method-replacements) hajtanak végre. Nem végeznek összetettebb SDK-integrációkat, például a [mentési házirendet](#enable-features-that-require-app-participation), a [többszörös identitást](#multi-identity-optional), az [app-We regisztrációt](#app-protection-policy-without-device-enrollment), a [AndroidManifest-módosításokat](#manifest-replacements) vagy a [ADAL-konfigurációt](#configure-azure-active-directory-authentication-library-adal) , ezért ezeket a az alkalmazás teljesen Intune engedélyezve van. Kérjük, figyelmesen tekintse át a dokumentáció további részét az alkalmazáshoz kapcsolódó integrációs pontokért.

> [!NOTE]
> Az eszközöket olyan projekten futtathatja, amely már a MAM SDK részleges vagy teljes forrás-integrálását végezte a manuális cserék használatával. A projektnek továbbra is függőségként kell kilistáznia a MAM SDK-t.

### <a name="gradle-build-plugin"></a>Gradle Build beépülő modul
Ha az alkalmazás nem az gradle-mel épít, ugorjon az [integrálás a parancssori eszközzel](#command-line-build-tool)elemre. 

Az App SDK beépülő modul az SDK részeként van kiosztva **GradlePlugin/com. microsoft. Intune. Mam. Build. jar**néven. Ahhoz, hogy a Gradle meg tudja találni a beépülő modult, hozzá kell adni a buildscript-osztályútvonal. A beépülő modul a [Javassist](https://jboss-javassist.github.io/javassist/)függ, amelyet szintén hozzá kell adni. Ha ezeket a osztályútvonal szeretné hozzáadni, adja hozzá a következőt a root `build.gradle`

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

Ezután az APK-projekthez tartozó `build.gradle` fájlban egyszerűen alkalmazza a beépülő modult a következőre:
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

Alapértelmezés szerint a beépülő modul **csak** `project` függőségeken fog működni.
A teszt fordítása nincs hatással. A konfigurációt a lista számára lehet megadni
*  Kizárandó projektek
*  [Felvenni kívánt külső függőségek](#usage-of-includeexternallibraries) 
*  A feldolgozásból kizárandó konkrét osztályok
*  A feldolgozásból kizárandó változatok. Ezek a teljes Variant névre vagy egyetlen ízra is vonatkozhatnak. Példa:
     * Ha az alkalmazáshoz `debug` és `release` is tartozik a @no__t (`savory`,-3} és {`vanilla`, `chocolate`}), megadható
     * @no__t – 0 – az összes változat kizárása a sós íz használatával vagy `savoryVanillaRelease` – csak az adott pontos változat kizárása.

#### <a name="example-partial-buildgradle"></a>Példa részleges Build. gradle

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

Ez a következő hatásokkal járhat:
* a `:product:FooLib` nem íródik újra, mert az `excludeProjects` része.
* a `:product:foo-project` újraírásra kerül, kivéve az `com.contoso.SplashActivity` esetében, amely kimarad, mert `excludeClasses`
* a `bar.jar` újra lett írva, mert az `includeExternalLibraries` része.
* a `zap.jar` **nem** íródik újra, mert nem projekt, és nem része a `includeExternalLibraries`
* a `com.contoso.foo:zap-artifact:1.0.0` újra lett írva, mert az `includeExternalLibraries` része.
* a `com.microsoft.bar:baz:1.0.0` újra lett írva, mert az `includeExternalLibraries` helyettesítő karakter (`com.microsoft.*`) használatával szerepel benne.
* a `com.microsoft.qux:foo:2.0` nem íródik újra, annak ellenére, hogy az megegyezik az előző elemmel megegyező helyettesítő karakterrel, mert az explicit módon ki van zárva egy tagadási mintával.

#### <a name="usage-of-includeexternallibraries"></a>A includeExternalLibraries használata

Mivel a beépülő modul csak a projekt függőségein működik (általában a `project()` függvény által), a `fileTree(...)` által vagy a mavenből vagy más csomagokból beszerzett függőségeket (például "`com.contoso.bar:baz:1.2.0`") meg kell adni a `includeExternalLibraries` tulajdonsághoz, ha a MAM az alábbiakban ismertetett feltételek alapján kell őket feldolgozni. A helyettesítő karakterek ("*") támogatottak. A `!` karakterrel kezdődő elemek nem vonhatók le, és olyan könyvtárak kizárására használhatók, amelyek egyébként helyettesítő karaktert tartalmaznak.

Az összetevő-jelöléssel rendelkező külső függőségek megadása esetén javasolt kihagyni a verziószámot a `includeExternalLibraries` értékben. Ha a verziót is tartalmazza, akkor a verziószámának pontosnak kell lennie. A dinamikus verzió specifikációi (például `1.+`) nem támogatottak.

Az általános szabály, amelyet meg kell határoznia, hogy a `includeExternalLibraries` függvénytárait is tartalmaznia kell-e két kérdés alapján:
1. Rendelkezik a könyvtár olyan osztályokkal, amelyekhez MAM-egyenértékű? Példák: `Activity`, `Fragment`, `ContentProvider`, `Service` stb.
2. Ha igen, használja az alkalmazás ezeket az osztályokat?

Ha mindkét kérdésre Igennel válaszol, akkor `includeExternalLibraries` értékre kell felvennie a könyvtárat. 

| Alkalmazási helyzet | Tartalmaznia kell? |
|--|--|
| Az alkalmazásban szerepel egy PDF-megjelenítő függvénytár, és a `Activity` megjelenítőt használja az alkalmazásban, amikor a felhasználók megpróbálnak megtekinteni PDF-fájlokat | Igen |
| Az alkalmazásban egy HTTP-függvénytárat is megadhat a továbbfejlesztett webes teljesítmény érdekében | Nem |
| Olyan függvénytárat tartalmaz, mint például a natív reakciót, amely `Activity`, `Application` és `Fragment` osztályból származtatott osztályokat tartalmaz, és ezeket az osztályokat használja vagy tovább származtatja az alkalmazásban | Igen |
| Olyan függvénytárat tartalmaz, mint például a natív reakciót, amely `Activity`, `Application` és `Fragment` osztályból származtatott osztályokat tartalmaz, de csak statikus segítőket vagy segédprogram-osztályokat használ. | Nem |
| Olyan függvénytárat tartalmaz, amely `TextView` értékből származtatott megtekintési osztályokat tartalmaz, és ezeket az osztályokat használja vagy tovább származtatja az alkalmazásban | Igen |

#### <a name="reporting"></a>Jelentések
A Build beépülő modul létre tud hozni egy HTML-jelentést az általa végrehajtott változásokról. A jelentés létrehozásához a `intunemam` konfigurációs blokkban `report = true` értéket kell megadnia. Ha a rendszer létrehozza a jelentést, a jelentés a Build könyvtárában található `outputs/logs` értékre lesz írva.

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

A gradle beépülő modul függőségi viszonyban van a [Javassist](https://jboss-javassist.github.io/javassist/), amelynek elérhetőnek kell lennie a gradle függőségi feloldásához (a fentiekben leírtak szerint). A Javassist kizárólag a beépülő modul futtatásakor használatos. A rendszer nem ad hozzá Javassist-kódot az alkalmazáshoz.

> [!NOTE] 
> Az Android Gradle beépülő modul és a Gradle 4,1 vagy újabb verziójának 3,0 vagy újabb verzióját kell használnia.

### <a name="command-line-build-tool"></a>Parancssori Build eszköz
Ha a Build Gradle használ, ugorjon a [következő szakaszra](#class-and-method-replacements).

A parancssori Build eszköz az SDK drop `BuildTool` mappájában érhető el. Ugyanezt a funkciót hajtja végre, mint a fent részletezett Gradle beépülő modul, de integrálható az egyéni vagy nem Gradle Build rendszerbe. Ahogy az általánosabb, összetettebb a meghívása, ezért a Gradle beépülő modult kell használni, ha erre van szükség.

#### <a name="using-the-command-line-tool"></a>A parancssori eszköz használata

A parancssori eszköz a `BuildTool\bin` könyvtárban található megadott segítő parancsfájlok használatával hívható meg.

Az eszköz a következő paramétereket várja.

| Paraméter | Leírás |
| -- | -- |
| `--input` | A módosítandó osztályokba tartozó JAR-fájlok és-könyvtárak pontosvesszővel tagolt listája. Ennek tartalmaznia kell az összes újraírni kívánt tégelyt/könyvtárat. |
| `--output` | A módosított osztályok tárolására szolgáló JAR-fájlok és-könyvtárak pontosvesszővel tagolt listája. Bemeneti bejegyzés esetén egy kimeneti bejegyzésnek kell szerepelnie, és sorrendben kell szerepelnie. |
| `--classpath` | A Build osztályútvonal. Ez a tégelyeket és az osztály-címtárakat is tartalmazhatja. |
| `--excludeClasses`| Az újraírásból kizárandó osztályok nevét tartalmazó pontosvesszővel tagolt lista. |

Minden paraméter megadása kötelező, kivéve a `--excludeClasses` értéket, amely nem kötelező.

> [!NOTE]
> A UNIX-hoz hasonló rendszerekben a pontosvessző a parancs elválasztója. Ha el szeretné kerülni, hogy a rendszerhéj el tudja végezni a parancsok felosztását, ügyeljen arra, hogy az egyes pontosvesszőket a "@no__t – 0, vagy a teljes paramétert idézőjelek közé zárja.

#### <a name="example-command-line-tool-invocation"></a>Példa parancssori eszköz meghívása

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Ez a következő hatásokkal járhat:

* a `product-foo-project` könyvtár újraírása `mam-build\product-foo-project`-re
* a `bar.jar` újraírása `mam-build\libs\bar.jar`-re
* a `zap.jar` **nem** íródik újra, mert csak a `--classpath` címen szerepel
* A `com.contoso.SplashActivity` osztály még **akkor sem íródik** újra, ha a `--input`

> [!NOTE] 
> A Build eszköz jelenleg nem támogatja az éves tevékenységi fájlokat. Ha a Build rendszer még nem tudja kibontani a `classes.jar` értéket az éves adatfájlok kezelésekor, ezt a Build eszköz meghívása előtt kell elvégezni.


## <a name="class-and-method-replacements"></a>Osztály-és metódus-visszahelyezések

Az Intune-felügyelet engedélyezéséhez az androidos alaposztályokat a megfelelő MAM-megfelelővel kell helyettesíteni. Az SDK-osztályok az androidos alaposztály és az alkalmazás saját származtatott verziója között élnek. Előfordulhat például, hogy egy alkalmazás tevékenysége egy olyan öröklési hierarchiával végződik, amely a következőképpen néz ki: `Activity` @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4. A MAM-réteg úgy szűri a rendszerműveleteket, hogy zökkenőmentesen biztosítson alkalmazást a világ felügyelt nézetével.

Az alaposztályokon kívül az alkalmazás egyes osztályait anélkül is használhatja (például `MediaPlayer`), hogy a MAM-val egyenértékűek voltak, és [egyes metódus-hívásokat is le kell cserélni](#wrapped-system-services). A pontos részleteket alább találja.

> [!NOTE] 
> Ha az alkalmazás integrálva van az SDK [Build-eszközökkel](#build-tooling), a következő osztály-és metódus-cserék automatikusan elvégzik.

| Androidos alaposztály | Intune app SDK-helyettesítés |
|--|--|
| Android. app. Activity | MAMActivity |
| Android. app. ActivityGroup | MAMActivityGroup |
| Android. app. AliasActivity | MAMAliasActivity |
| Android. app. Application | MAMApplication |
| Android. app. Dialog | MAMDialog |
| Android. app. AlertDialog. Builder | MAMAlertDialogBuilder |
| Android. app. DialogFragment | MAMDialogFragment |
| Android. app. ExpandableListActivity | MAMExpandableListActivity |
| Android. app. fragment | MAMFragment |
| Android. app. IntentService | MAMIntentService |
| Android. app. LauncherActivity | MAMLauncherActivity |
| Android. app. ListActivity | MAMListActivity |
| Android. app. ListFragment | MAMListFragment |
| Android. app. NativeActivity | MAMNativeActivity |
| Android. app. PendingIntent | MAMPendingIntent (lásd a [függőben lévő szándékot](#pendingintent)) |
| Android. app. Service | MAMService |
| Android. app. TabActivity | MAMTabActivity |
| Android. app. TaskStackBuilder | MAMTaskStackBuilder |
| Android. app. backup. BackupAgent | MAMBackupAgent |
| Android. app. backup. BackupAgentHelper | MAMBackupAgentHelper |
| Android. app. backup. FileBackupHelper | MAMFileBackupHelper |
| Android. app. backup. SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| Android. Content. BroadcastReceiver | MAMBroadcastReceiver |
| Android. Content. ContentProvider | MAMContentProvider |
| Android. os. kötő | MAMBinder (csak akkor szükséges, ha a kötőt nem az Android Interface Definition Language (AIDL) felületen hozza létre) |
| Android. Media. Media Player | MAMMediaPlayer |
| Android. Media. MediaMetadataRetriever | MAMMediaMetadataRetriever |
| Android. Provider. DocumentsProvider | MAMDocumentsProvider |
| Android. preferencia. PreferenceActivity | MAMPreferenceActivity |
| Android. support. multidex. MultiDexApplication | MAMMultiDexApplication |
| Android. widget. TextView | MAMTextView |
| Android. widget. AutoCompleteTextView | MAMAutoCompleteTextView |
| Android. widget. CheckedTextView | MAMCheckedTextView |
| Android. widget. EditText | MAMEditText |
| Android. inputmethodservice. ExtractEditText | MAMExtractEditText |
| Android. widget. MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Még akkor is, ha az alkalmazásnak nincs szüksége saját származtatott `Application` osztályra, [lásd: `MAMApplication`](#mamapplication) .

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft. Intune. MAM. SDK. support. v4. jar:

| Androidos osztály | Intune app SDK-helyettesítés |
|--|--|
| Android. support. v4. app. DialogFragment | MAMDialogFragment
| Android. support. v4. app. FragmentActivity | MAMFragmentActivity
| Android. support. v4. app. fragment | MAMFragment
| Android. support. v4. app. JobIntentService | MAMJobIntentService
| Android. support. v4. app. TaskStackBuilder | MAMTaskStackBuilder
| Android. support. v4. Content. FileProvider | MAMFileProvider
| Android. support. v4. Content. WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft. Intune. MAM. SDK. support. v7. jar:

|Androidos osztály | Intune app SDK-helyettesítés |
|--|--|
| Android. support. v7. app. AlertDialog. Builder | MAMAlertDialogBuilder |
| Android. support. v7. app. AppCompatActivity | MAMAppCompatActivity |
| Android. support. v7. widget. AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| Android. support. v7. widget. AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| Android. support. v7. widget. AppCompatEditText | MAMAppCompatEditText |
| Android. support. v7. widget. AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| Android. support. v7. widget. AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft. Intune. MAM. SDK. support. v17. jar:
|Androidos osztály | Intune app SDK-helyettesítés |
|--|--|
| Android. support. v17. Leanback. widget. SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft. Intune. MAM. SDK. support. Text. jar:
|Androidos osztály | Intune app SDK-helyettesítés |
|--|--|
| Android. support. Text. Emoji. widget. EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| Android. support. Text. Emoji. widget. EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| Android. support. Text. Emoji. widget. EmojiEditText | MAMEmojiEditText |
| Android. support. Text. Emoji. widget. EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Átnevezett metódusok
Sok esetben az Android osztályban elérhető metódus véglegesként van megjelölve a MAM-helyettesítő osztályban. Ebben az esetben a MAM helyettesítő osztály egy hasonlóan elnevezett metódust biztosít (általában `MAM` utótaggal), amelyet felül kell bírálni. Ha például `MAMActivity` értékről származtatja, a `onCreate()` felülbírálása és a `super.onCreate()` hívása helyett `Activity` a `onMAMCreate()` értéket kell megadnia, és meg kell hívnia a `super.onMAMCreate()`-öt. A Java-fordítónak meg kell kényszeríteni a végső korlátozásokat, hogy megakadályozza az eredeti metódus véletlen felülbírálását a MAM-egyenérték helyett.

### <a name="mamapplication"></a>MAMApplication
Ha az alkalmazás létrehoz egy `android.app.Application` alosztályt, akkor ehelyett létre **kell** hoznia egy `com.microsoft.intune.mam.client.app.MAMApplication` alosztályt. Ha az alkalmazás nem `android.app.Application`, akkor a AndroidManifest. xml fájl `<application>` címkéjén `"android:name"` attribútumként be **kell** állítania a `"com.microsoft.intune.mam.client.app.MAMApplication"` értéket.

### <a name="pendingintent"></a>PendingIntent
@No__t – 0 helyett a `MAMPendingIntent.get*` metódust kell használnia. Ezt követően a szokásos módon használhatja az eredő `PendingIntent` értéket.

### <a name="wrapped-system-services"></a>Becsomagolt rendszerszolgáltatások
Egyes rendszerszolgáltatási osztályokhoz statikus metódust kell meghívni egy MAM burkoló osztályon ahelyett, hogy közvetlenül meghívja a kívánt metódust a szolgáltatási példányon. A `getSystemService(ClipboardManager.class).getPrimaryClip()` hívása például `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)` hívásának kell lennie. Ezeket a kihelyezéseket nem ajánlott manuálisan elvégezni. Ehelyett hagyja meg a BuildPlugin.

| Androidos osztály | Intune app SDK-helyettesítés |
|--|--|
| Android. Content. ClipboardManager | MAMClipboard |
| Android. Content. ContentProviderClient | MAMContentProviderClientManagement |
| Android. Content. ContentResolver | MAMContentResolverManagement |
| Android. Content. PM. PackageManager | MAMPackageManagement |
| Android. app. DownloadManager | MAMDownloadManagement |
| Android. Print. PrintManager | MAMPrintManagement |
| Android. support. v4. Print. PrintHelper | MAMPrintHelperManagement |
| Android. View. View | MAMViewManagement |
| Android. View. DragEvent | MAMDragEventManagement |
| Android. app. NotificationManager | MAMNotificationManagement |
| Android. support. v4. app. NotificationManagerCompat | MAMNotificationCompatManagement |

Egyes osztályok a legtöbb módszerét beburkolták, például `ClipboardManager`, `ContentProviderClient`, `ContentResolver` és `PackageManager`, míg más osztályok esetében csak egy vagy két módszer van becsomagolva, például `DownloadManager`, `PrintManager`, `PrintHelper`, `View`, `DragEvent`, `NotificationManager` és 0. Ha nem használja a BuildPlugin, tekintse meg a MAM-vel egyenértékű osztályok által elérhető API-kat a pontos módszerhez.

### <a name="manifest-replacements"></a>Jegyzékfájlok kihelyezése
Előfordulhat, hogy a fenti osztályok közül néhányat végre kell hajtania a jegyzékfájlban, valamint a Java-kódban is. Speciális Megjegyzés:
* A `android.support.v4.content.FileProvider` kifejezésre mutató hivatkozásokat `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider` értékkel kell helyettesíteni.

## <a name="androidx-libraries"></a>AndroidX-kódtárak
Az Android P-vel a Google bejelentette a AndroidX nevű támogatási függvénytárak (átnevezve) egy új készletét, a 28-as verzió pedig a meglévő Android. support könyvtárak utolsó jelentős kiadását.

Az Android support libs-mel ellentétben a AndroidX-kódtárak nem biztosítanak MAM-változatokat. Ehelyett a AndroidX-et más külső kódtárként kell kezelni, és úgy kell konfigurálni, hogy a Build beépülő modul/eszköz átírja őket. A Gradle-buildek esetében ezt az `androidx.*` értékkel teheti meg a beépülő modul konfigurációjának `includeExternalLibraries` mezőjében. A parancssori eszköz meghívásakor az összes jar-fájlt explicit módon fel kell sorolni.

### <a name="pre-androidx-architecture-components"></a>AndroidX előtti architektúra-összetevők
Számos androidos architektúra-összetevő, például a Room, a ViewModel és a WorkManager újracsomagolták a AndroidX. Ha az alkalmazás ezen könyvtárak előre AndroidX változatait használja, győződjön meg arról, hogy az újraírások érvényesek, beleértve a `android.arch.*` értéket a beépülő modul konfigurációjának `includeExternalLibraries` mezőjében. Azt is megteheti, hogy frissíti a kódtárakat a AndroidX megfelelő értékekkel.

## <a name="sdk-permissions"></a>SDK-engedélyek

Az Intune app SDK három [Android rendszerbeli rendszerengedélyt](https://developer.android.com/guide/topics/security/permissions.html) igényel az azt integráló alkalmazásokhoz:

* `android.permission.GET_ACCOUNTS` (igény szerint, szükség esetén)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

A Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) megköveteli a felügyelt hitelesítés végrehajtásához szükséges engedélyeket. Ha ezeket az engedélyeket nem engedélyezi az alkalmazás, vagy a felhasználó visszavonja, akkor a közvetítőt (a Céges portál alkalmazást) igénylő hitelesítési folyamatok le lesznek tiltva.

## <a name="logging"></a>Naplózás

A naplózást korán kell inicializálni, hogy a legtöbbet kihasználja a naplózott adatai közül. a `Application.onMAMCreate()` általában a naplózás inicializálásának legjobb kiindulópontja.

Ha MAM-naplókat szeretne fogadni az alkalmazásban, hozzon létre egy [Java-kezelőt](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) , és adja hozzá a `MAMLogHandlerWrapper`-hez. Ez a művelet minden naplózási üzenet esetében meghívja a `publish()` értéket az alkalmazás-kezelőben.

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

## <a name="enable-features-that-require-app-participation"></a>Alkalmazások részvételét igénylő szolgáltatások engedélyezése

Számos alkalmazás-védelmi szabályzat létezik, az SDK nem valósítható meg saját maga. Az alkalmazás a következő `AppPolicy` felületen megtalált API-k használatával tudja vezérelni a funkciókat. @No__t-0 példány beolvasásához használja a `MAMPolicyManager.getPolicy` értéket.

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
> a `MAMPolicyManager.getPolicy` mindig nem null értékű alkalmazás-szabályzatot ad vissza, még akkor is, ha az eszköz vagy az alkalmazás nem az Intune felügyeleti szabályzata alá tartozik.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Példa: annak megállapítása, hogy szükséges-e PIN-kód az alkalmazáshoz

Ha az alkalmazás saját PIN-kódot használó felhasználói felülettel rendelkezik, akkor előfordulhat, hogy le szeretné tiltani, ha a rendszergazda úgy konfigurálta az SDK-t, hogy az alkalmazás PIN-kódját kéri. Annak megállapításához, hogy a rendszergazda telepítette-e az alkalmazáshoz tartozó PIN-szabályzatot az alkalmazáshoz, az aktuális végfelhasználónál hívja meg a következő metódust:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Példa: az elsődleges Intune-felhasználó meghatározása

A AppPolicy-ben elérhető API-k mellett az egyszerű felhasználónevet (**UPN**) is a `MAMUserInfo` felületen definiált `getPrimaryUser()` API teszi elérhetővé. Az egyszerű felhasználónév beszerzéséhez hívja a következőt:

```java
MAMComponents.get(MAMUserInfo.class).getPrimaryUser();
```

Az MAMUserInfo felület teljes definíciója a következő:

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

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Példa: annak megállapítása, hogy engedélyezett-e a Mentés eszközre vagy Felhőbeli tárhelyre

Számos alkalmazás valósít meg olyan funkciókat, amelyek lehetővé teszik a végfelhasználó számára fájlok mentését helyi vagy felhőalapú tárolási szolgáltatásba. Az Intune app SDK lehetővé teszi a rendszergazdák számára, hogy az adatszivárgás elleni védelemhez olyan házirend-korlátozásokat alkalmazzanak, amelyek megfelelnek a szervezetük számára.  A felügyelhető házirendek egyike, hogy a végfelhasználó menthet-e "személyes" nem felügyelt adattárba. Ide tartozik a helyi helyre, SD-kártyára vagy harmadik féltől származó biztonsági mentési szolgáltatásokra való mentés.

**A funkció engedélyezéséhez alkalmazás részvételére van szükség.** Ha az alkalmazás lehetővé teszi a személyes vagy Felhőbeli helyekre való mentést közvetlenül az alkalmazásból, meg kell valósítania ezt a szolgáltatást annak biztosításához, hogy a rendszergazda meg tudja határozni, hogy engedélyezett-e a Mentés az adott helyre. Az alábbi API lehetővé teszi, hogy az alkalmazás tudja, hogy a személyes tárolóba való mentés engedélyezett-e az Intune-rendszergazda aktuális szabályzata által. Az alkalmazás ezután kényszerítheti a szabályzatot, mivel a felhasználó az alkalmazáson keresztül elérhetővé teszi a felhasználók számára a személyes adattárt.  

A következő hívással állapíthatja meg, hogy a házirend ki van-e kényszerítve:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

A `service` paraméternek a következő `SaveLocation` értékek egyikének kell lennie:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

A `username` értéknek a menteni kívánt felhőalapú szolgáltatáshoz társított UPN/username/e-mail azonosítónak kell lennie (*nem* feltétlenül ugyanaz, mint a mentett dokumentumot birtokló felhasználó). Ha a HRE UPN és a Cloud Service-Felhasználónév közötti leképezés nem létezik, vagy a Felhasználónév nem ismert, akkor a null értéket kell használnia. a `SaveLocation.LOCAL` nem felhőalapú szolgáltatás, ezért mindig `null` username paraméterrel kell használni.

Az előző módszer annak meghatározására, hogy egy adott felhasználó házirendje engedélyezte-e az adatmentést különböző helyekre, `getIsSaveToPersonalAllowed()` volt ugyanazon a **AppPolicy** -osztályon belül. Ez a függvény már **elavult** , és nem használható, a következő hívás megegyezik a `getIsSaveToPersonalAllowed()` értékkel:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, null);
```

>[!NOTE]
> Ha a szóban forgó hely nem szerepel a **SaveLocations** enumerálásban, használja a `SaveLocation.OTHER` értéket.

### <a name="example-determine-if-notifications-with-organization-data-need-to-be-restricted"></a>Példa: annak megállapítása, hogy a szervezeti adattal rendelkező értesítéseket korlátozni kell-e

Ha az alkalmazás értesítéseket jelenít meg, akkor az értesítés megjelenítése előtt ellenőriznie kell az értesítéshez társított felhasználó értesítési korlátozási szabályzatát. A következő hívással állapíthatja meg, hogy a házirend ki van-e kényszerítve.

```java
NotificationRestriction notificationRestriction =
    MAMPolicyManager.getPolicyForIdentity(notificationIdentity).getNotificationRestriction();
```

Ha a korlátozás értéke @no__t – 0, az alkalmazás nem jelenítheti meg a Szabályzathoz társított felhasználó értesítéseit. Ha @no__t – 0, az alkalmazásnak olyan módosított értesítést kell megjelenítenie, amely nem tartalmaz szervezeti adatkészletet. Ha @no__t – 0, az összes értesítés engedélyezett.

Ha a `getNotificationRestriction` nincs meghívva, a MAM SDK a legjobb erőfeszítést tesz az értesítések automatikus korlátozására az egyszeres identitású alkalmazások esetében. Ha az automatikus blokkolás engedélyezve van, és a `BLOCK_ORG_DATA` be van állítva, akkor az értesítés egyáltalán nem jelenik meg. Részletesebb szabályozást a `getNotificationRestriction` értékkel ellenőrizheti, és megfelelően módosíthatja az alkalmazás-értesítéseket.

## <a name="register-for-notifications-from-the-sdk"></a>Regisztráció az SDK értesítéseire

### <a name="overview"></a>Áttekintés
Az Intune app SDK lehetővé teszi, hogy az alkalmazás szabályozza bizonyos szabályzatok, például a szelektív törlés működését, ha azokat a rendszergazda helyezi üzembe. Amikor egy rendszergazda üzembe helyez egy ilyen szabályzatot, az Intune szolgáltatás értesítést küld az SDK-nak.

Az alkalmazásnak regisztrálnia kell az SDK által küldött értesítésekhez egy `MAMNotificationReceiver` létrehozásával, és regisztrálnia kell `MAMNotificationReceiverRegistry`-re. Ezt úgy teheti meg, hogy megadja a fogadó és a kívánt értesítés típusát @no__t – 0, az alábbi példában látható módon:

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

A `MAMNotificationReceiver` illesztőfelület egyszerűen fogad értesítéseket az Intune szolgáltatástól. Egyes értesítéseket közvetlenül az SDK kezel, míg mások az alkalmazás részvételét igénylik. Az alkalmazásnak igaz vagy hamis értéket **kell** visszaadnia egy értesítésből. Minden esetben igaz értéket kell visszaadnia, kivéve, ha az értesítés eredményeként megkísérelt valamilyen művelet meghiúsult.

* Ezt a hibát jelenteni lehet az Intune szolgáltatásnak. Példa a jelentésre, ha az alkalmazás nem törli a felhasználói adatok törlését, miután a rendszergazda kezdeményezte a törlést.

>[!NOTE]
> A `MAMNotificationReceiver.onReceive` blokkolása biztonságos, mert a visszahívás nem fut a felhasználói felület szálán.

Az SDK-ban definiált `MAMNotificationReceiver` felületet a következők tartalmazzák:

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

Az alkalmazás a következő értesítéseket küldi el, és némelyikük megkövetelheti az alkalmazás részvételét:

* **WIPE_USER_DATA**: ezt az értesítést egy `MAMUserNotification` osztályban küldi el a rendszer. Ha ez az értesítés érkezik, az alkalmazásnak törölnie *kell* a felügyelt identitáshoz társított összes adatmennyiséget (`MAMUserNotification.getUserIdentity()`). Az értesítés különböző okok miatt fordulhat elő, többek között akkor is, ha az alkalmazás meghívja a `unregisterAccountForMAM` értéket, amikor egy rendszergazda elindít egy törlést, vagy ha a rendszergazda által kért feltételes hozzáférési szabályzatok nem teljesülnek. Ha az alkalmazás nem regisztrálja ezt az értesítést, a rendszer az alapértelmezett törlési viselkedést fogja végrehajtani. Az alapértelmezett viselkedés törli az egyetlen identitást tartalmazó alkalmazás összes fájlját, vagy a felügyelt identitással címkézett összes fájlt egy többszörös identitású alkalmazás esetében. Ez az értesítés soha nem lesz elküldve a felhasználói felületi szálon.

* **WIPE_USER_AUXILIARY_DATA**: az alkalmazások regisztrálhatnak erre az értesítésre, ha szeretné, hogy az INTUNE app SDK végrehajtsa az alapértelmezett szelektív törlési viselkedést, de továbbra is szeretné eltávolítani a kisegítő adatok törlését. Ez az értesítés csak a több identitást kezelő alkalmazások számára érhető el. Ez az értesítés soha nem lesz elküldve a felhasználói felületi szálon.

* **REFRESH_POLICY**: ez az értesítés egy `MAMUserNotification`. Ha ez az értesítés érkezik, az alkalmazás által gyorsítótárazott Intune-szabályzatokra vonatkozó döntéseket érvényteleníteni és frissíteni kell. Ha az alkalmazás nem tárol házirend-feltételezéseket, nem kell regisztrálnia ezt az értesítést. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

* **REFRESH_APP_CONFIG**: ez az értesítés egy `MAMUserNotification`. Az értesítés fogadásakor a gyorsítótárazott alkalmazás-konfigurációs összes adattal érvényteleníteni és frissíteni kell. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

* **MANAGEMENT_REMOVED**: ezt az értesítést a rendszer egy `MAMUserNotification` üzenetben küldi el, és tájékoztatja arról, hogy az alkalmazás nem lesz felügyelve. Ha nem felügyelt, többé nem fogja tudni beolvasni a titkosított fájlokat, olvassa el a MAMDataProtectionManager-mel titkosított, a titkosított vágólapra való interakciót, vagy más módon vegyen részt a felügyelt alkalmazás-ökoszisztémában. Tekintse meg az alábbi részleteket. Ez az értesítés soha nem lesz elküldve a felhasználói felületi szálon.

* **MAM_ENROLLMENT_RESULT**: ezt az értesítést a rendszer egy `MAMEnrollmentNotification` üzenetben küldi el, hogy tájékoztassa az alkalmazást arról, hogy egy alkalmazás-a beléptetési kísérlet befejeződött, és hogy megadja a kísérlet állapotát. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

* **COMPLIANCE_STATUS**: ez az értesítés egy `MAMComplianceNotification` címen kerül elküldésre, hogy a megfelelőségi szervizelési kísérlet eredménye alapján tájékoztassa az alkalmazást. A rendszer nem vállal garanciát arra vonatkozóan, hogy milyen szálat küld ez az értesítés.

> [!NOTE]
> Egy alkalmazásnak soha nem kell regisztrálnia a `WIPE_USER_DATA` és a `WIPE_USER_AUXILIARY_DATA` értesítések esetében is.

### <a name="management_removed"></a>MANAGEMENT_REMOVED

A @no__t 0 értesítés azt jelzi, hogy az Intune MAM-szabályzata már nem fogja felügyelni a korábban házirend által kezelt felhasználókat. Ehhez nincs szükség a felhasználói adatok törlésére vagy a felhasználó kijelentkezésére (ha törlésre van szükség, `WIPE_USER_DATA` értesítés lesz elküldve). Előfordulhat, hogy számos alkalmazásnak egyáltalán nem kell kezelnie ezt az értesítést, azonban a `MAMDataProtectionManager` használatát használó alkalmazásoknak [külön megjegyzésre van szükségük az értesítésről](#data-protection).

Ha a MAM meghívja az alkalmazás `MANAGEMENT_REMOVED` vevőkészülékét, a következők lesznek érvényesek:
* A MAM már visszafejti az alkalmazáshoz tartozó korábban titkosított fájlokat (de nem védett adatpuffereket). Az SDcard nyilvános helyein lévő fájlok, amelyek nem tartoznak közvetlenül az alkalmazáshoz (például a dokumentumok vagy a letöltési mappák), nem lesznek visszafejtve.
* A fogadó módszer által létrehozott új fájlok vagy védett adatpufferek (vagy bármely más, a fogadó indítása után futó kód) nem lesznek titkosítva.
* Az alkalmazás továbbra is hozzáfér a titkosítási kulcsokhoz, így a műveletek, például a visszafejtési adatpufferek sikeresek lesznek.

Ha az alkalmazás fogadója visszatér, a továbbiakban nem lesz hozzáférése a titkosítási kulcsokhoz.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Azure Active Directory Authentication Library (ADAL) konfigurálása

Először olvassa el a ADAL integrációs irányelveit a [githubon található ADAL-tárházban](https://github.com/AzureAD/azure-activedirectory-library-for-android).

Az SDK a [hitelesítési](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) és feltételes indítási forgatókönyvek [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) támaszkodik, amelyeknek az alkalmazásoknak [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)-vel való konfigurálására van szükségük. A konfigurációs értékeket a rendszer a AndroidManifest-metaadatokon keresztül közli az SDK-val.

Az alkalmazás konfigurálásához és a megfelelő hitelesítés engedélyezéséhez adja hozzá a következőt az alkalmazás-csomóponthoz a AndroidManifest. xml fájlban. Ezen konfigurációk némelyike csak akkor szükséges, ha az alkalmazás általános ADAL használ a hitelesítéshez. Ebben az esetben szüksége lesz az alkalmazás által használt konkrét értékekre, hogy regisztrálja magát a HRE. Erre azért van szükség, hogy a végfelhasználó ne Kérdezzen kétszer a hitelesítésre, mivel a HRE két különböző regisztrációs értéket ismer fel: egyet az alkalmazásból, egyet pedig az SDK-ból.

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

* A **szolgáltató a** használatban lévő HRE-szolgáltató. Ha ez az érték hiányzik, a rendszer a HRE nyilvános környezetét használja.
    > [!NOTE]
    > Ne állítsa be ezt a mezőt, ha az alkalmazás szuverén felhőben van.

* A **ClientID** a használni kívánt HRE-ClientID (más néven alkalmazás-azonosító). Ha az Azure AD-ben regisztrálva van, vagy az [alapértelmezett regisztrációt](#default-enrollment-optional) használja, akkor a saját alkalmazás ClientID kell használnia, ha nem integrálja az ADAL-t.

* A **NonBrokerRedirectURI** a HRE átirányítási URI-ja, amelyet a bróker nélküli esetekben kell használni. Ha nincs megadva, a rendszer a `urn:ietf:wg:oauth:2.0:oob` alapértelmezett értékét használja. Ez az alapértelmezett beállítás a legtöbb alkalmazás számára megfelelő.

  * A NonBrokerRedirectURI csak akkor használatos, ha a SkipBroker értéke "true" (igaz).

* A **SkipBroker** az alapértelmezett ADAL SSO-részvételi viselkedés felülbírálására szolgál. A SkipBroker csak olyan alkalmazások esetében szabad megadni, amelyek ClientID határoznak meg **, és** nem támogatják a felügyelt hitelesítést/eszközre kiterjedő egyszeri bejelentkezést. Ebben az esetben a tulajdonságot "true" értékre kell beállítani. A legtöbb alkalmazás nem állíthatja be a SkipBroker paramétert.

  * SkipBroker érték megadásához **meg kell adni egy ClientID a** jegyzékfájlban.

  * Ha meg van adva egy ClientID, az alapértelmezett érték a "false".

  * Ha a SkipBroker értéke "true" (igaz), a rendszer a NonBrokerRedirectURI fogja használni. Azok az alkalmazások, amelyek nem integrálják a ADAL-t (és ezért nincs ClientID), az alapértelmezett érték "true" (igaz) is.

### <a name="common-adal-configurations"></a>Általános ADAL-konfigurációk

Az alábbi gyakori módszerekkel konfigurálható az alkalmazások ADAL. Keresse meg az alkalmazás konfigurációját, és győződjön meg arról, hogy a ADAL metaadat-paramétereit (lásd fent) a szükséges értékekre állítja be. A hatóság minden esetben megadható, ha a nem alapértelmezett környezetekhez szükséges. Ha nincs megadva, a rendszer a nyilvános éles HRE-szolgáltatót fogja használni.

#### <a name="1-app-does-not-integrate-adal"></a>1. az alkalmazás nem integrálja az ADAL
A ADAL-metaadatok **nem** lehetnek jelen a jegyzékfájlban.

#### <a name="2-app-integrates-adal"></a>2. az alkalmazás integrálja a ADAL

|Szükséges ADAL paraméter| Value (Díj) |
|--|--|
| ClientID | Az alkalmazás ClientID (amelyet az Azure AD generál az alkalmazás regisztrálásakor) |

Szükség esetén a szolgáltató is megadható.

Regisztrálnia kell az alkalmazást az Azure AD-ben, és hozzáférést kell adnia az alkalmazásnak az alkalmazás-védelmi házirend szolgáltatáshoz:
* Az alkalmazások Azure AD-vel való regisztrálásával kapcsolatban [itt](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) talál további információt.
* Győződjön meg arról, hogy a lépéseket követve megadhatja az Android-alkalmazás engedélyeit az App Protection-házirend (alkalmazás) szolgáltatáshoz. Az [első lépések az INTUNE SDK-útmutatóban](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) című témakör útmutatását követve adja meg az alkalmazás hozzáférését az Intune app Protection szolgáltatáshoz (nem kötelező). 

Tekintse meg az alábbi [feltételes hozzáférés](#conditional-access) követelményeit is.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. az alkalmazás integrálja a ADAL-t, de nem támogatja a felügyelt hitelesítés/eszköz szintű egyszeri bejelentkezést

|Szükséges ADAL paraméter| Value (Díj) |
|--|--|
| ClientID | Az alkalmazás ClientID (amelyet az Azure AD generál az alkalmazás regisztrálásakor) |
| SkipBroker | **Igaz** |

Szükség esetén a szolgáltató és a NonBrokerRedirectURI is megadható.

### <a name="conditional-access"></a>Feltételes hozzáférés
A feltételes hozzáférés (CA) egy Azure Active Directory [funkció](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer) , amely a HRE-erőforrásokhoz való hozzáférés szabályozására használható. Az [Intune-rendszergazdák meghatározhatnak olyan hitelesítésszolgáltatói szabályokat](https://docs.microsoft.com/intune/conditional-access) , amelyek csak az Intune által felügyelt eszközökről és alkalmazásokból engedélyezik az erőforrás-hozzáférést. Ahhoz, hogy az alkalmazás megfelelő módon hozzáférhessen az erőforrásokhoz, az alábbi lépésekkel kell eljárnia. Ha az alkalmazás nem hoz HRE hozzáférési jogkivonatokat, vagy csak olyan erőforrásokhoz fér hozzá, amelyek nem lehetnek CA-védelemmel ellátva, akkor kihagyhatja ezeket a lépéseket.

1. Kövesse a [ADAL integrációs irányelveit](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Lásd: a Broker használatának különösen a 11. lépése.
2. [Az alkalmazás regisztrálása a Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   Az átirányítási URI-t a fenti ADAL-integrációs irányelvek között találja.
3. Állítsa be a manifest meta-adatok paramétereit a [Common ADAL konfigurációkon](#common-adal-configurations), a 2. elemnél.
4. Ellenőrizze, hogy minden megfelelően van-e konfigurálva, ha az [eszközön alapuló hitelesítésszolgáltatót](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) engedélyezte a [Azure Portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) és megerősíti
    - Az alkalmazásba való bejelentkezés a Intune Céges portál telepítésére és regisztrálására kéri
    - A regisztrációt követően az alkalmazásba való bejelentkezés sikeresen befejeződik.
5. Miután az alkalmazás beszállította az Intune APP SDK-integrációt, vegye fel a kapcsolatot msintuneappsdk@microsoft.com a jóváhagyott alkalmazások listájához az [alkalmazás-alapú feltételes hozzáféréshez](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. Miután hozzáadta az alkalmazást a jóváhagyott listához, ellenőrizze az [alkalmazáson alapuló hitelesítésszolgáltató konfigurálását](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) , és győződjön meg arról, hogy az alkalmazásba való bejelentkezés sikeresen befejeződött.

## <a name="app-protection-policy-without-device-enrollment"></a>Alkalmazás-védelmi szabályzat az eszközök regisztrációja nélkül

### <a name="overview"></a>Áttekintés
Az Intune app Protection szabályzata az eszközök regisztrációja nélkül, más néven az APP-WE vagy a MAM – lehetővé teszi az alkalmazások Intune általi felügyeletét anélkül, hogy az eszköznek regisztrálnia kell az Intune-MDM. ALKALMAZÁS – az eszközök regisztrálásával vagy anélkül is működik. A Céges portál továbbra is telepíteni kell az eszközre, de a felhasználónak nem kell bejelentkeznie a Céges portálba, és regisztrálnia kell az eszközt.

> [!NOTE]
> Az alkalmazások védelmi házirendjének az eszközök regisztrációja nélküli támogatásához minden alkalmazásra szükség van.

### <a name="workflow"></a>Munkafolyamat

Amikor egy alkalmazás új felhasználói fiókot hoz létre, regisztrálnia kell a fiókot az Intune app SDK-val való felügyelethez. Az SDK kezeli az alkalmazás APP-WE szolgáltatásban való regisztrálásának részleteit. Ha szükséges, a rendszer a megfelelő időközönként újrapróbálkozik a beléptetéssel, ha a hibák történnek.

Az alkalmazás az Intune app SDK-t is lekérdezheti egy regisztrált felhasználó állapotára vonatkozóan annak megállapítására, hogy a felhasználót le kell-e tiltani a vállalati tartalmak eléréséhez. Több fiók is regisztrálható a felügyelethez, de jelenleg csak egy fiók lehet aktív módon regisztrálni az APP-WE szolgáltatásban. Ez azt jelenti, hogy az alkalmazásban csak egy fiók fogadhat el alkalmazás-védelmi házirendet.

Az alkalmazásnak meg kell adnia egy visszahívást, amely a megfelelő hozzáférési token beszerzését kéri a Azure Active Directory Authentication Library (ADAL) által az SDK nevében. Feltételezzük, hogy az alkalmazás már használja az ADAL-t a felhasználói hitelesítéshez és a saját hozzáférési jogkivonatok beszerzéséhez.

Ha az alkalmazás teljesen eltávolítja a fiókot, meg kell szüntetnie a fiók regisztrációját annak jelzésére, hogy az alkalmazásnak többé nem kell házirendet alkalmaznia az adott felhasználóra. Ha a felhasználó regisztrálva lett a MAM-szolgáltatásban, a felhasználó regisztrációja törölve lesz, és az alkalmazás törlődik.

### <a name="overview-of-app-requirements"></a>Az alkalmazásra vonatkozó követelmények áttekintése

Az APP-WE integráció megvalósításához az alkalmazásnak regisztrálnia kell a felhasználói fiókot a MAM SDK-val:

1. Az alkalmazásnak _meg kell_ valósítania és regisztrálnia kell az `MAMServiceAuthenticationCallback` illesztőfelület egy példányát. A visszahívási példányt a lehető leghamarabb regisztrálni kell az alkalmazás életciklusában (általában az Application osztály `onMAMCreate()` metódusában).

2. Amikor létrejön egy felhasználói fiók, és a felhasználó sikeresen bejelentkezik a ADAL-be, az alkalmazásnak _meg kell_ hívnia a `registerAccountForMAM()`.

3. Felhasználói fiók eltávolításakor az alkalmazásnak meg kell hívnia a `unregisterAccountForMAM()` értéket, hogy eltávolítsa a fiókot az Intune-felügyeletből.

    > [!NOTE]
    > Ha a felhasználó átmenetileg kijelentkezik az alkalmazásból, az alkalmazásnak nem kell meghívnia `unregisterAccountForMAM()` értéket. A hívás elindíthat egy törlést, hogy teljesen eltávolítsa a felhasználó vállalati adatait.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager
Az összes szükséges hitelesítési és regisztrációs API megtalálható a `MAMEnrollmentManager` felületen. A `MAMEnrollmentManager` értékre való hivatkozás a következőképpen érhető el:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

A visszaadott `MAMEnrollmentManager` példány garantáltan nem lehet null értékű. Az API-metódusok két kategóriába sorolhatók: **hitelesítés** és **fiók regisztrálása**.

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

### <a name="account-authentication"></a>Fiók hitelesítése
Ez a szakasz a `MAMEnrollmentManager` hitelesítési API-módszereit és azok használatát ismerteti.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. Az alkalmazásnak meg kell valósítania a `MAMServiceAuthenticationCallback` felületet, hogy az SDK ADAL jogkivonatot kérjen az adott felhasználóhoz és erőforrás-AZONOSÍTÓhoz. A visszahívási példányt meg kell adni a `MAMEnrollmentManager` számára a `registerAuthenticationCallback()` metódus meghívásával. Előfordulhat, hogy a regisztrálási újrapróbálkozások vagy az alkalmazás-védelmi szabályzatok frissítési beadásának korai szakaszában szükség van egy jogkivonatra, így a visszahívás regisztrálása ideális hely az alkalmazás `MAMApplication` alosztályának `onMAMCreate()` metódusában.

2. A `acquireToken()` metódusnak meg kell kapnia a hozzáférési jogkivonatot az adott felhasználóhoz tartozó kért erőforrás-AZONOSÍTÓhoz. Ha nem tudja megkapni a kért jogkivonatot, a null értéket kell visszaadnia.

    > [!NOTE]
    > Győződjön meg arról, hogy az alkalmazás használja a `resourceId` és a `aadId` paramétert `acquireToken()` értékre, hogy a megfelelő jogkivonat beszerzése sikeres legyen.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Abban az esetben, ha az alkalmazás nem tud jogkivonatot biztosítani, ha az SDK meghívja a `acquireToken()`-t, például ha a csendes hitelesítés meghiúsul, és nem megfelelő idő a felhasználói felület megjelenítésére – az alkalmazás egy későbbi időpontban is megadhatja a tokent az `updateToken()` metódus meghívásával. Ugyanezt az egyszerű felhasználónevet, HRE-azonosítót és erőforrás-azonosítót is át kell adni a `acquireToken()` meghívása előtt `updateToken()` értéknek, valamint a végül megszerzett jogkivonatnak. Az alkalmazásnak a lehető leghamarabb meg kell hívnia ezt a metódust, miután null értéket adott vissza a megadott visszahívásból.

    > [!NOTE]
    > Az SDK meghívja a `acquireToken()` időszakot a token beszerzéséhez, ezért a `updateToken()` hívása nem feltétlenül szükséges. Erősen ajánlott azonban, mert segíthet a regisztrációk és az alkalmazás-védelmi szabályzatok beadásának időben történő beléptetésében.


### <a name="account-registration"></a>Fiók regisztrálása
Ez a szakasz a fiók regisztrációs API-módszereit ismerteti a `MAMEnrollmentManager` és használatuk során.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. A fióknak a felügyelethez való regisztrálásához az alkalmazásnak meg kell hívnia a `registerAccountForMAM()` értéket. A felhasználói fiókot az UPN és a HRE felhasználói azonosítója is azonosítja. A bérlői AZONOSÍTÓhoz a beléptetési adatközpontnak a felhasználó HRE-Bérlővel való hozzárendelésére is szükség van. A felhasználó hatósága is megadható az adott szuverén Felhőkkel való regisztráció engedélyezéséhez. További információ: [szuverén Felhőbeli regisztráció](#sovereign-cloud-registration).  Előfordulhat, hogy az SDK megpróbálta regisztrálni az alkalmazást az adott felhasználó számára a MAM-szolgáltatásban; Ha a regisztráció meghiúsul, a rendszer rendszeres időközönként újrapróbálkozik a regisztrációval, amíg a fiók nincs regisztrálva. Az újrapróbálkozási időszak általában 12-24 óra lesz. Az SDK aszinkron módon biztosítja a beléptetési kísérletek állapotát az értesítéseken keresztül.

2. Mivel a HRE-hitelesítés szükséges, a felhasználói fiók regisztrálásának legjobb ideje az, hogy a felhasználó bejelentkezett az alkalmazásba, és sikeresen hitelesítve lett a ADAL használatával. A felhasználó HRE-AZONOSÍTÓját és a bérlő AZONOSÍTÓját a rendszer a [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) objektum részeként visszaadja a ADAL hitelesítési hívásnak.
    * A bérlő azonosítója a `AuthenticationResult.getTenantID()` metódusból származik.
    * A felhasználóval kapcsolatos információ a `UserInfo` típusú alobjektumban található, amely `AuthenticationResult.getUserInfo()` értékből származik, és a HRE felhasználói AZONOSÍTÓját a rendszer a `UserInfo.getUserId()` hívásával kéri le az objektumból.

3. A fiókok Intune-felügyeletből való regisztrációjának megszüntetéséhez az alkalmazásnak meg kell hívnia a `unregisterAccountForMAM()` értéket. Ha a fiók sikeresen regisztrálva lett, és felügyelt, az SDK megszünteti a fiók regisztrációját és az adatok törlését. A rendszer leállítja a fiók rendszeres regisztrálási újrapróbálkozásait. Az SDK aszinkron módon adja meg a beléptetési kérések állapotát értesítés útján.

### <a name="sovereign-cloud-registration"></a>Szuverén Felhőbeli regisztráció
A [szuverén felhőalapú](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) alkalmazások számára **szükséges** , hogy a `authority` `registerAccountForMAM()` legyen.  Ezt úgy érheti el, ha `instance_aware=true` értéket ad meg a ADAL [1.14.0 +](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) AcquireToken-extraQueryParameters, majd a AuthenticationCallback AuthenticationResult `getAuthority()` meghívásával.

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
> Ne állítsa be a `com.microsoft.intune.mam.aad.Authority` meta-adatelem értéket a AndroidManifest. xml fájlban.

> [!NOTE]
> Győződjön meg arról, hogy a szolgáltató megfelelően van beállítva a `MAMServiceAuthenticationCallback::acquireToken()` metódusban.

#### <a name="currently-supported-sovereign-clouds"></a>Jelenleg támogatott szuverén felhők

1. Azure USA-beli kormányzati felhő

### <a name="important-implementation-notes"></a>Fontos megvalósítási megjegyzések

#### <a name="authentication"></a>Hitelesítés
* Ha az alkalmazás meghívja a `registerAccountForMAM()` értéket, akkor előfordulhat, hogy egy másik szálon röviddel azután visszahívást kap az `MAMServiceAuthenticationCallback` felületéről. Ideális esetben az alkalmazás a saját tokenjét a ADAL-ből szerezte be a fiók regisztrálása előtt, hogy felgyorsítsa a kért jogkivonat beszerzését. Ha az alkalmazás egy érvényes jogkivonatot ad vissza a visszahívásból, a beléptetés folytatódik, és az alkalmazás a végső eredményt egy értesítésen keresztül kapja meg.

* Ha az alkalmazás nem ad vissza érvényes HRE-tokent, a beléptetési kísérlet végső eredménye `AUTHENTICATION_NEEDED` lesz. Ha az alkalmazás értesítés útján kapja meg ezt az eredményt, erősen ajánlott a beléptetési folyamat felgyorsításához, ha a `acquireToken()` által korábban kért felhasználó és erőforrás jogkivonatát kéri le, és meghívja a `updateToken()` metódust a beléptetési folyamat elindításához. újra.

* Az alkalmazás regisztrálva van @no__t – 0 is meghívja, hogy a rendszer tokent szerezzen be a rendszeres alkalmazás-védelmi szabályzatok frissítéséhez. Ha az alkalmazás nem tud jogkivonatot biztosítani a kérelem során, akkor nem kap értesítést, de a rendszer megkísérli a jogkivonat beszerzését és a `updateToken()` meghívását a következő kényelmes időpontban a beadási folyamat felgyorsításához. Ha nem ad meg jogkivonatot, a rendszer a visszahívást továbbra is a következő beadási kísérlet során hívja meg.

* A szuverén felhők támogatásához meg kell adni a szolgáltatót.

#### <a name="registration"></a>Regisztráció
* Az Ön kényelme érdekében a regisztrációs módszerek a idempotens; a `registerAccountForMAM()`will például csak a fiók regisztrálását és az alkalmazás regisztrálását kísérli meg, ha a fiók még nincs regisztrálva, és a `unregisterAccountForMAM()` csak akkor törli a fiókot, ha az jelenleg regisztrálva van. A további hívások nem a-Ops, így nem árt, ha többször is meghívja ezeket a metódusokat. Emellett a metódusok és az eredmények közötti értesítések közötti levelezés nem garantált: Ha a `registerAccountForMAM()` azonosító egy már regisztrált identitáshoz van meghívva, előfordulhat, hogy az értesítés nem lesz újra elküldve az adott identitáshoz. Előfordulhat, hogy az értesítéseket a rendszer nem felel meg a metódusok meghívásának, mivel az SDK időről időre kipróbálhatja a regisztrációkat a háttérben, és az Intune szolgáltatástól kapott törlési kérések kiválthatják a regisztrációt.

* A regisztrációs metódusok tetszőleges számú különböző identitáshoz hívhatók, de jelenleg csak egy felhasználói fiók regisztrálható sikeresen. Ha több olyan felhasználói fiók van, amely az Intune-licenccel rendelkezik, és az App Protection-szabályzat által megcélozva van regisztrálva, akkor nincs garancia arra, hogy a versenyt megnyerje.

* Végül lekérdezheti a `MAMEnrollmentManager` értéket, és megtekintheti, hogy egy adott fiók regisztrálva van-e, és hogy a `getRegisteredAccountStatus()` metódus használatával beolvassa-e az aktuális állapotát. Ha a megadott fiók nincs regisztrálva, ez a metódus **Null értéket**ad vissza. Ha a fiók regisztrálva van, ez a metódus a fiók állapotát a `MAMEnrollmentManager.Result` enumerálás egyik tagjaként fogja visszaadni.

### <a name="result-and-status-codes"></a>Eredmény-és állapotkódok
Amikor a rendszer először regisztrálja a fiókot, a @no__t 0 állapotba kerül, ami azt jelzi, hogy a MAM-szolgáltatás kezdeti beléptetési kísérlete hiányos. A beléptetési kísérlet befejeződése után a rendszer értesítést küld az alábbi táblázatban szereplő egyik eredmény-kóddal. Emellett a `getRegisteredAccountStatus()` metódus visszaadja a fiók állapotát, így az alkalmazás mindig meghatározhatja, hogy a vállalati tartalomhoz való hozzáférés le van-e tiltva az adott felhasználó számára. Ha a beléptetési kísérlet sikertelen, a fiók állapota az idő múlásával változhat, mivel az SDK újrapróbálkozik a háttérben való regisztrációval.

|Eredmény kódja | Magyarázat |
| -- | -- |
| `AUTHORIZATION_NEEDED` | Ez az eredmény azt jelzi, hogy az alkalmazás regisztrált `MAMServiceAuthenticationCallback` példánya nem adta meg a tokent, vagy a megadott jogkivonat érvénytelen.  Az alkalmazásnak érvényes jogkivonatot kell bekérnie, és meg kell hívnia `updateToken()` értéket, ha lehetséges. |
| `NOT_LICENSED` | A felhasználó nem rendelkezik Intune-licenccel, vagy az Intune MAM szolgáltatással való kapcsolatfelvételre tett kísérlet meghiúsult.  Az alkalmazásnak nem felügyelt (normál) állapotban kell maradnia, és a felhasználónak nem szabad letiltani.  A regisztrációk rendszeres időközönként újrapróbálkoznak abban az esetben, ha a felhasználó a jövőben válik licencbe. |
| `ENROLLMENT_SUCCEEDED` | A beléptetési kísérlet sikeres volt, vagy a felhasználó már regisztrálva van.  Sikeres regisztráció esetén a rendszer egy házirend-frissítési értesítést küld az értesítés előtt.  A vállalati adatbázisokhoz való hozzáférést engedélyezni kell. |
| `ENROLLMENT_FAILED` | A beléptetési kísérlet sikertelen volt.  További részleteket az eszközök naplófájljaiban találhat.  Az alkalmazás ebben az állapotban nem engedélyezheti a vállalati adatelérést, mivel korábban azt állapították meg, hogy a felhasználó Intune-licenccel rendelkezik.|
| `WRONG_USER` | Egy eszközön csak egy felhasználó regisztrálhat egy alkalmazást a MAM szolgáltatásban. Ez az eredmény azt jelzi, hogy a felhasználó, akire ezt az eredményt szállították (a második felhasználó), a MAM-szabályzattal van megcélozva, de egy másik felhasználó már regisztrálva van. Mivel a MAM-szabályzat nem kényszeríthető ki a második felhasználó számára, az alkalmazás nem engedélyezheti a hozzáférést ehhez a felhasználó adataihoz (valószínűleg eltávolítja a felhasználót az alkalmazásból), kivéve, ha a felhasználó egy későbbi időpontban sikertelen lesz. A `WRONG_USER` eredmény megadásával párhuzamosan a MAM kérni fogja a meglévő fiók eltávolításának lehetőségét. Ha az emberi felhasználó igenlő válaszban válaszol, akkor a második felhasználó rövid idő múlva regisztrálhat. Amíg a második felhasználó regisztrálva marad, a MAM rendszeresen újrapróbálkozik a regisztrációval. |
| `UNENROLLMENT_SUCCEEDED` | A regisztráció törlése sikeres volt.|
| `UNENROLLMENT_FAILED` | A regisztráció megszüntetésére irányuló kérelem sikertelen volt.  További részleteket az eszközök naplófájljaiban találhat. Ez általában akkor fordul elő, ha az alkalmazás érvényes (sem null, sem üres) UPN-t továbbít. Az alkalmazás nem rendelkezik közvetlen, megbízható szervizeléssel. Ha ez az érték egy érvényes egyszerű felhasználónév regisztrációjának törlésekor érkezik, jelentse a hibát az Intune MAM csapatának.|
| `PENDING` | A felhasználó kezdeti beléptetési kísérlete folyamatban van.  Az alkalmazás képes blokkolni a vállalati adatbázisokhoz való hozzáférést, amíg a beléptetési eredmény ismertté nem válik, de erre nincs szükség. |
| `COMPANY_PORTAL_REQUIRED` | A felhasználó rendelkezik Intune-licenccel, de az alkalmazás csak akkor regisztrálható, ha az Céges portál alkalmazás telepítve van az eszközön. Az Intune app SDK megkísérli letiltani az alkalmazáshoz való hozzáférést az adott felhasználó számára, és a Céges portál alkalmazás telepítéséhez irányítja őket (részletekért lásd alább). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Céges portál követelmény kérésének felülbírálása (nem kötelező)
Ha a `COMPANY_PORTAL_REQUIRED` eredmény érkezik, az SDK letiltja a beléptetést kérő identitást használó tevékenységek használatát. Ehelyett az SDK a Céges portál letöltésére vonatkozó kérést jeleníti meg. Ha meg szeretné akadályozni ezt a viselkedést az alkalmazásában, a tevékenységek a `MAMActivity.onMAMCompanyPortalRequired` értéket is végrehajthatják.

Ezt a metódust az SDK az alapértelmezett blokkolási felhasználói felületének megjelenítése előtt hívja meg. Ha az alkalmazás megváltoztatja a tevékenység identitását, vagy törli a regisztrálni próbált felhasználó regisztrációját, az SDK nem blokkolja a tevékenységet. Ebben az esetben az alkalmazás feladata, hogy elkerülje a vállalati adatszivárgást. Csak a többszörös identitású alkalmazások (később tárgyalt) képesek megváltoztatni a tevékenység identitását.

Ha nem örökli explicit módon a `MAMActivity` értéket (mivel a Build-szerszámozás végrehajtja ezt a módosítást), de továbbra is kezelnie kell ezt az értesítést, akkor ehelyett az `MAMActivityBlockingListener` megvalósítását kell végrehajtania.

### <a name="notifications"></a>Értesítések
Ha az alkalmazás regisztrálja az **MAM_ENROLLMENT_RESULT**típusú értesítéseket, a rendszer elküld egy `MAMEnrollmentNotification` értéket, hogy tájékoztassa az alkalmazást a beléptetési kérelem befejeződéséről. A `MAMEnrollmentNotification` a `MAMNotificationReceiver` felületen keresztül érkezik, az SDK-ban található [értesítések regisztrálása](#register-for-notifications-from-the-sdk) részben leírtak szerint.

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

A `getEnrollmentResult()` metódus visszaadja a beléptetési kérelem eredményét.  Mivel a `MAMEnrollmentNotification` kiterjeszti `MAMUserNotification`-et, a felhasználó identitása is elérhető. Az alkalmazásnak meg kell valósítania a `MAMNotificationReceiver` felületet az értesítések fogadásához, az SDK-ban található [értesítések regisztrálásakor](#register-for-notifications-from-the-sdk) részletezve.

A regisztrált felhasználói fiók állapota megváltozhat, ha beléptetési értesítés érkezik, de az összes esetben nem változik (például ha `AUTHORIZATION_NEEDED` értesítés érkezik egy további tájékoztató eredmény (például `WRONG_USER`) után, annál több tájékoztató eredmény lesz a fiók állapotaként van karbantartva).  A fiók sikeres regisztrálása után az állapot `ENROLLMENT_SUCCEEDED` marad, amíg a fiók regisztrációja be nem fejeződik vagy nincs törölve.

## <a name="app-ca-with-policy-assurance"></a>ALKALMAZÁS-HITELESÍTÉSSZOLGÁLTATÓ házirend-garanciával

### <a name="overview"></a>Áttekintés
Ha az alkalmazás-HITELESÍTÉSSZOLGÁLTATÓ (feltételes hozzáférés) házirend-garanciával rendelkezik, az erőforrásokhoz való hozzáférés Intune App Protection szabályzatok alkalmazásán alapul.  A HRE ezt úgy kényszeríti, hogy az alkalmazást regisztrálni és felügyeli az alkalmazás, mielőtt jogkivonatot adna egy olyan alkalmazás-HITELESÍTÉSSZOLGÁLTATÓ eléréséhez, amelyhez házirend-megbízhatósági védelemmel ellátott erőforrás van társítva.  Az alkalmazásnak a ADAL-átvitelszervező jogkivonat-beszerzéséhez kell használnia, és a telepítés megegyeznek a [feltételes hozzáférésben](#conditional-access)leírtak szerint.

### <a name="adal-changes"></a>ADAL változásai
A ADAL-könyvtár egy új hibakódot tartalmaz, amely arról tájékoztatja az alkalmazást, hogy a jogkivonat beszerzése nem felel meg az alkalmazás felügyeletének.  Ha az alkalmazás megkapja ezt a hibakódot, meg kell hívnia az SDK-t, hogy megpróbálja elhárítani a megfelelőséget az alkalmazás regisztrálásával és a szabályzat alkalmazásával. Kivételt kap a ADAL `onError()` metódusa `AuthenticationCallback`, és a következő hibakód lesz: `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  Ebben az esetben a kivételt egy `IntuneAppProtectionPolicyRequiredException`-ra lehet átadni, amelyből a szervizelését-megfelelőségben való használatra további paramétereket lehet kinyerni (lásd az alábbi kódrészletet). A szervizelés sikeres befejezését követően az alkalmazás újrapróbálkozhat a jogkivonat-beszerzéssel a ADAL-on keresztül.

> [!NOTE]
> Ez az új hibakód és a házirend-megbízhatósággal rendelkező APP CA egyéb támogatása a ADAL könyvtárának 1.15.0 (vagy újabb verzió) szükséges.

### <a name="mamcompliancemanager"></a>MAMComplianceManager
A `MAMComplianceManager` illesztőfelület akkor használatos, ha a házirend által megkövetelt hiba érkezik a ADAL.  A `remediateCompliance()` metódust tartalmazza, amelyet hívni kell, hogy az alkalmazás megfelelő állapotba kerüljön. A `MAMComplianceManager` értékre való hivatkozás a következőképpen érhető el:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

A visszaadott `MAMComplianceManager` példány garantáltan nem lehet null értékű.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

A `remediateCompliance()` metódust úgy hívja meg, hogy megpróbálja a felügyelet alá helyezni az alkalmazást a HRE a kért jogkivonat megadására vonatkozó feltételeinek kielégítése érdekében.  Az első négy paraméter kinyerhető a ADAL `AuthenticationCallback.onError()` metódus által fogadott kivételből (lásd az alábbi kódrészletet).  Az utolsó paraméter egy olyan logikai érték, amely azt szabályozza, hogy a megfelelőségi kísérlet során megjelenik-e egy UX.  Ez egy egyszerű blokkolási folyamatjelző felület, amely olyan alkalmazások számára biztosít alapértelmezettként, amelyeknek nincs szükségük testreszabott UX megjelenítésére a művelet során.  A rendszer csak a megfelelőségi szervizelést fogja blokkolni, és nem jeleníti meg a végeredményt.  Az alkalmazásnak regisztrálnia kell egy értesítési fogadót a megfelelőségi szervizelési kísérlet sikerességének vagy meghibásodásának kezeléséhez (lásd alább).

A `remediateCompliance()` módszer a megfelelőség megállapításának részeként a MAM-regisztrációt is elvégezheti.  Előfordulhat, hogy az alkalmazás beléptetési értesítést kap, ha regisztrált egy értesítési fogadót a beléptetési értesítésekhez.  Az alkalmazás regisztrált `MAMServiceAuthenticationCallback` `acquireToken()` metódusával kap egy jogkivonatot a MAM-regisztrációhoz. @no__t – 0 lesz meghívva, mielőtt az alkalmazás megszerezte a saját jogkivonatát, ezért előfordulhat, hogy a sikeres jogkivonat-beszerzést követően az alkalmazás által végrehajtott könyvelési vagy fiók-létrehozási feladatok még nem lettek végrehajtva.  Ebben az esetben a visszahívásnak képesnek kell lennie a jogkivonat beszerzésére.  Ha nem tud visszaadni tokent `acquireToken()` értékből, a megfelelőségi szervizelési kísérlet sikertelen lesz.  Ha a `updateToken()` értéket a kért erőforrás érvényes jogkivonatával hívja meg, a megfelelőségi szervizelés azonnal újrapróbálkozik az adott jogkivonattal.

> [!NOTE]
> A csendes jogkivonat beszerzése továbbra is lehetséges a `acquireToken()` esetében, mivel a felhasználó már be van vezetve a közvetítő telepítésére és az eszköz regisztrálására, mielőtt `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` hiba érkezett.  Ez azt eredményezi, hogy a közvetítő érvényes frissítési tokent eredményez a gyorsítótárban, így a kért jogkivonat csendes acqisition sikeres lesz.

Íme egy minta, amely a házirend által igényelt hibát fogadja a `AuthenticationCallback.onError()` metódusban, és az `MAMComplianceManager` meghívásával kezeli a hibát.

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
Ha az alkalmazás regisztrálja az **COMPLIANCE_STATUS**típusú értesítéseket, a rendszer elküld egy `MAMComplianceNotification` értéket, hogy tájékoztassa az alkalmazást a megfelelőségi szervizelési kísérlet végső állapotáról. A `MAMComplianceNotification` a `MAMNotificationReceiver` felületen keresztül érkezik, az SDK-ban található [értesítések regisztrálása](#register-for-notifications-from-the-sdk) részben leírtak szerint.

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
| FÜGGŐBEN | A megfelelőség javítására tett kísérlet sikertelen volt, mert az állapot válasza még nem érkezett meg a szolgáltatástól, ha túllépte az időkorlátot. Az alkalmazásnak később újra kell próbálkoznia a jogkivonat-beszerzéssel. |
| COMPANY_PORTAL_REQUIRED | Ahhoz, hogy a megfelelőségi szervizelés sikeres legyen, a Céges portál telepíteni kell az eszközön.  Ha az Céges portál már telepítve van az eszközön, az alkalmazást újra kell indítani.  Ebben az esetben egy párbeszédpanel jelenik meg, amely arra kéri a felhasználót, hogy indítsa újra az alkalmazást. |

Ha a megfelelőségi állapot @no__t – 0, az alkalmazásnak újra kell indítania az eredeti jogkivonat-beszerzését (saját erőforráshoz). Ha a megfelelőségi szervizelési kísérlet meghiúsult, akkor a `getComplianceErrorTitle()` és a `getComplianceErrorMessage()` metódus honosított karakterláncokat ad vissza, amelyeket az alkalmazás megjelenít a végfelhasználónak, ha úgy dönt.  A hibák többsége nem pótolható az alkalmazásban, ezért az általános esetben lehet, hogy a fiók létrehozása vagy a bejelentkezés meghiúsul, és lehetővé teszi a felhasználó számára, hogy később próbálkozzon újra.  Ha a hiba tartósan fennáll, a MAM-naplók segíthetnek meghatározni az okot.  A végfelhasználó elküldheti a naplókat az [itt](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "E-mail-naplók a cég informatikai támogatási szolgálatának")található utasításokat követve.

Mivel a `MAMComplianceNotification` kiterjeszti `MAMUserNotification`-et, a felhasználó identitása is elérhető.

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
> A `remediateCompliance()` hívása előtt regisztrálni kell az értesítési fogadót, hogy elkerülje a versenyhelyzet kimaradása miatti feltételt.

### <a name="implementation-notes"></a>Implementációs megjegyzések
> [!NOTE]
> **Fontos változás!**  <br>
> Az alkalmazás `MAMServiceAuthenticationCallback.acquireToken()` metódusának *false értékűnek* kell lennie az új `forceRefresh` jelzőhöz a `acquireTokenSilentSync()` értékre.
> Korábban azt javasoljuk, hogy *igaz* értéket adjon a tokenek frissítésével kapcsolatos probléma megoldásához, de a ADAL probléma merült fel, amely megakadályozhatja a tokenek beszerzését bizonyos helyzetekben, ha ez a jelző *igaz*.
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ false);
```

> [!NOTE]
> Ha a Szervizelési kísérlet során egyéni blokkolási UX-t szeretne megjeleníteni, a showUX paraméternek *Hamis értéket* kell átadnia `remediateCompliance()` értékre. Győződjön meg arról, hogy az UX-t jeleníti meg, és először regisztrálja az értesítés-figyelőt a `remediateCompliance()` hívása előtt.  Ez megakadályozza azt a versenyhelyzet-feltételt, amelyben az értesítés kihagyható, ha a `remediateCompliance()` nagyon gyorsan meghiúsul.  Egy tevékenység alosztályának `onCreate()` vagy `onMAMCreate()` metódusa például ideális hely az értesítési figyelő regisztrálásához, majd a `remediateCompliance()` hívásához.  A `remediateCompliance()` paraméterei átadhatók az UX-nek a leképezési extrák számára.  Ha a megfelelőségi állapotra vonatkozó értesítés érkezik, megtekintheti az eredményt, vagy egyszerűen befejezheti a tevékenységet.

> [!NOTE]
> @no__t – 0 – regisztrálja a fiókot, és megkísérli a regisztrálást.  A fő jogkivonat beszerzése után a `registerAccountForMAM()` meghívása nem szükséges, de ez nem okoz kárt. Ha azonban az alkalmazás nem tudja beszerezni a jogkivonatot, és el szeretné távolítani a felhasználói fiókot, akkor a `unregisterAccountForMAM()` meghívásával el kell távolítania a fiókot, és meg kell akadályoznia a háttérben történő regisztrációt.

## <a name="protecting-backup-data"></a>Biztonsági mentési adatok védelme
Az Android Marshmallow (API 23) esetében az Android két módszert kínál az alkalmazások biztonsági mentésére. Minden lehetőség elérhető az alkalmazás számára, és különböző lépéseket igényel az Intune-adatvédelem megfelelő megvalósításának biztosításához. Az alábbi táblázatban áttekintheti a megfelelő adatvédelmi működéshez szükséges műveleteket.  A biztonsági mentési módszerekről az [Android API útmutatójában](https://developer.android.com/guide/topics/data/backup.html)olvashat bővebben.

### <a name="auto-backup-for-apps"></a>Alkalmazások automatikus biztonsági mentése
Az Android megkezdte az Android Marshmallow-eszközökön futó alkalmazások [automatikus teljes biztonsági mentését](https://developer.android.com/guide/topics/data/autobackup.html) a Google Drive alkalmazásban, függetlenül az alkalmazás cél API-jával. Ha a AndroidManifest. xml fájlban explicit módon beállította a `android:allowBackup` **értéket hamis**értékre, akkor az alkalmazás soha nem fog várólistára állítani az Android és a "vállalati" adatokat az alkalmazáson belül. Ebben az esetben nincs szükség további műveletre.

Alapértelmezés szerint azonban a `android:allowBackup` attribútum értéke TRUE (igaz), még akkor is, ha a jegyzékfájlban nincs megadva a `android:allowBackup`. Ez azt jelenti, hogy a rendszer automatikusan biztonsági másolatot készít az összes alkalmazásról a felhasználó Google Drive-fiókjába, amely egy alapértelmezett viselkedés, amely **adatszivárgási kockázatot**jelent. Ezért az SDK az alábbi módosításokat igényli az adatvédelem alkalmazásának biztosításához.  Fontos, hogy kövesse az alábbi irányelveket az ügyféladatok megfelelő védelme érdekében, ha azt szeretné, hogy az alkalmazás Android-alapú Marshmallow-eszközökön fusson.  

Az Intune lehetővé teszi az Androidról elérhető összes [automatikus biztonsági mentési funkció használatát](https://developer.android.com/guide/topics/data/autobackup.html) , beleértve az egyéni szabályok XML-ben való definiálásának lehetőségét is, de az adatok védelméhez az alábbi lépéseket kell követnie:

1. Ha az alkalmazás **nem** a saját egyéni BackupAgent használja, az alapértelmezett MAMBackupAgent használatával engedélyezheti az Intune-szabályzatoknak megfelelő automatikus biztonsági mentést. Helyezze el a következőket az alkalmazás jegyzékfájljában:

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```
    
2. **[Nem kötelező]** Ha nem kötelező egyéni BackupAgent implementált, mindenképpen a MAMBackupAgent vagy a MAMBackupAgentHelper használatát kell használnia. Tekintse meg a következő részeket. Érdemes lehet áttérni az Intune **MAMDefaultFullBackupAgent** (az 1. lépésben leírtak szerint), amely egyszerű biztonsági mentést tesz lehetővé az Android M és újabb verziókban.

3. Ha eldönti, hogy milyen típusú teljes biztonsági mentést kell kapnia az alkalmazásnak (szűretlen, szűrt vagy nincs), a `android:fullBackupContent` attribútumot igaz, hamis vagy XML-erőforrásként kell beállítania az alkalmazásban.

4. Ezután _**másolja át**_ a `android:fullBackupContent`-ba helyezett metaadatokat egy `com.microsoft.intune.mam.FullBackupContent` nevű metaadat-címkébe a jegyzékfájlban.

    **1. példa**: Ha azt szeretné, hogy az alkalmazás kizárások nélkül teljes biztonsági mentést készítsen, állítsa a `android:fullBackupContent` attribútumot és a `com.microsoft.intune.mam.FullBackupContent` metaadat-címkét **igaz**értékre:

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

    **3. példa**: Ha azt szeretné, hogy az alkalmazás teljes biztonsági mentést készítsen az XML-fájlban meghatározott egyéni szabályoknak megfelelően, állítsa az attribútumot és a metaadatok címkéjét ugyanarra az XML-erőforrásra:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```

### <a name="keyvalue-backup"></a>Kulcs/érték biztonsági mentés
A [kulcs/érték biztonsági mentés](https://developer.android.com/guide/topics/data/keyvaluebackup.html) lehetőség minden API 8 + számára elérhető, és az alkalmazáshoz tartozó adatok feltöltése az [Android Backup szolgáltatásba](https://developer.android.com/google/backup/index.html). Az alkalmazás felhasználónként megadott mennyisége 5 MB-ra van korlátozva. Ha kulcs/érték biztonsági mentést használ, **BackupAgentHelper** vagy **BackupAgent**kell használnia.

### <a name="backupagenthelper"></a>BackupAgentHelper
A BackupAgentHelper a natív Android-funkciók és az Intune MAM-integráció tekintetében könnyebben valósítható meg, mint a BackupAgent. A BackupAgentHelper lehetővé teszi, hogy a fejlesztő teljes fájlokat és közös beállításokat regisztráljon egy **FileBackupHelper** és egy **SharedPreferencesBackupHelper** (vagy), amelyek ezután a létrehozáskor hozzáadódnak a BackupAgentHelper. Kövesse az alábbi lépéseket a BackupAgentHelper Intune MAM-nal való használatához:

1. A többszörös identitású biztonsági mentés BackupAgentHelper való kihasználásához kövesse az Android-útmutatót a [BackupAgentHelper kiterjesztéséhez](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper).

2. Az osztálynak ki kell terjesztenie az BackupAgentHelper, a FileBackupHelper és a SharedPreferencesBackupHelper MAM-megfelelőjét.

|Androidos osztály | MAM-megfelelő |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Az irányelvek követése sikeres, többszörös identitású biztonsági mentést és visszaállítást eredményez.

### <a name="backupagent"></a>BackupAgent

A BackupAgent lehetővé teszi, hogy sokkal világosabb legyen a biztonsági mentésre vonatkozó információk. Mivel a fejlesztő meglehetősen felelős a megvalósításért, több lépésre van szükség a megfelelő adatvédelem biztosításához az Intune-ból. Mivel a munka nagy részét leküldik Önnek, a fejlesztőnek, az Intune-integrációnak valamivel több résztvevője van.

**A MAM integrálása:**

1. Olvassa el figyelmesen az Android-útmutatót a [kulcs/érték biztonsági mentéshez](https://developer.android.com/guide/topics/data/keyvaluebackup.html) , és kifejezetten [bővítse a BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) , hogy a BackupAgent-megvalósítás megfeleljen az Android-irányelveknek.

2. Az osztály kiterjesztése `MAMBackupAgent`.

**Többszörös identitás biztonsági mentése:**

1. A biztonsági mentés megkezdése előtt győződjön meg arról, hogy a rendszergazda valóban engedélyezte a biztonsági mentésre tervezett fájlok vagy adatpufferek **biztonsági mentését** a több identitást használó forgatókönyvekben. A `MAMFileProtectionManager` és a `MAMDataProtectionManager` `isBackupAllowed` függvényt biztosítjuk ennek meghatározásához. Ha a fájl vagy az adatpuffer biztonsági mentése nem engedélyezett, akkor ne folytassa azt a biztonsági mentésben.

2. Ha biztonsági másolatot szeretne készíteni az 1. lépésben ellenőrzött fájlokhoz tartozó identitásokról, akkor a biztonsági mentés egy pontján meg kell hívnia a `backupMAMFileIdentity(BackupDataOutput data, File … files)` értéket azokkal a fájlokkal, amelyekről az adatok kinyerését tervezi. Ez automatikusan új biztonsági mentési entitásokat hoz létre, és a `BackupDataOutput` értékre írja őket. Ezeket az entitásokat a rendszer automatikusan felhasználja a visszaállítás után.

**Többszörös identitás visszaállítása:**

Az adatbiztonsági mentési útmutató egy általános algoritmust határoz meg az alkalmazás adatainak visszaállításához, és a [BackupAgent kiterjesztése](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) szakaszban tartalmaz egy kód mintát. Ahhoz, hogy sikeres legyen a többszörös identitás visszaállítása, a kódban szereplő általános struktúrát kell követnie, különös tekintettel a következőkre:

1. A biztonsági mentési entitások átlépéséhez `while(data.readNextHeader())` hurkot kell használnia. Az előző kódban a `data` a helyi változó neve, amely az alkalmazásnak a visszaállításkor átadott **MAMBackupDataInput** .

2. Meg kell hívnia a `data.skipEntityData()` értéket, ha a `data.getKey()` nem egyezik a `onBackup` által írt kulccsal. Ennek a lépésnek a végrehajtása nélkül előfordulhat, hogy a visszaállítások sikertelenek lesznek. Az előző kódban a `data` a helyi változó neve, amely az alkalmazásnak a visszaállításkor átadott **MAMBackupDataInput** .

3. Ne térjen vissza a `while(data.readNextHeader())` konstruktorban található biztonsági mentési entitások fogyasztása során, mert az automatikusan írt entitások elvesznek. Az előző kódban a `data` a helyi változó neve, amely az alkalmazásnak a visszaállításkor átadott **MAMBackupDataInput** .

## <a name="multi-identity-optional"></a>Többszörös identitás (nem kötelező)

### <a name="overview"></a>Áttekintés
Alapértelmezés szerint az Intune app SDK az alkalmazás egészére alkalmazza a szabályzatot. A többszörös identitás egy opcionális Intune app Protection-szolgáltatás, amely lehetővé teszi, hogy a szabályzatot identitási szinten lehessen alkalmazni. Ez jelentősen több alkalmazás részvételét igényli, mint a többi alkalmazás-védelmi funkció.

> [!NOTE]
> Az alkalmazás megfelelő részvételének hiánya adatszivárgást és egyéb biztonsági problémákat eredményezhet.

Miután a felhasználó regisztrálta az eszközt vagy az alkalmazást, az SDK regisztrálja ezt az identitást, és figyelembe veszi az elsődleges Intune által felügyelt identitást. Az alkalmazás többi felhasználója nem felügyelt lesz kezelve, és nem korlátozott házirend-beállításokkal.

> [!NOTE]
> Jelenleg csak egy Intune által felügyelt identitás támogatott eszközönként.

Az identitás karakterláncként van definiálva. Az identitások a **kis-és nagybetűk megkülönböztetését**jelentik, és az SDK-nak küldött kérések nem adhatják vissza ugyanazt a burkolatot, amelyet eredetileg az identitás beállításakor használt.

Az alkalmazásnak tájékoztatnia *kell* az SDK-t, amikor módosítani kívánja az aktív identitást. Bizonyos esetekben az SDK is értesíti az alkalmazást, amikor szükség van az identitás megváltoztatására. A legtöbb esetben azonban a MAM nem tudja, hogy milyen adatok jelennek meg a felhasználói felületen, vagy egy adott időpontban használják a szálat, és az alkalmazásra támaszkodva a helyes identitást állítja be az adatszivárgás elkerülése érdekében. Az alábbi szakaszokban bizonyos, az alkalmazásra vonatkozó műveletet igénylő forgatókönyvek is felhívhatók.

### <a name="enabling-multi-identity"></a>A többszörös identitás engedélyezése
Alapértelmezés szerint az összes alkalmazás egyetlen identitású alkalmazásnak minősül. A következő metaadatok a AndroidManifest. xml fájlban való elhelyezésével deklarálhatja, hogy az alkalmazás több identitást is felismer.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Az identitás beállítása
A fejlesztők a következő szinteken állíthatják be az alkalmazás felhasználóinak identitását csökkenő prioritás szerint:

  1. Szál szintje
  2. `Context` (általában `Activity`) szint
  3. Folyamat szintje

A szál szintjén beállított identitás felülírja a `Context` szinten beállított identitást, amely felülírja a folyamat szintjén beállított identitást. A `Context` azonosítóhoz megadott identitás csak a megfelelő kapcsolódó helyzetekben használatos. A fájl i/o-műveleteihez például nincs társítva `Context`. Az alkalmazások leggyakrabban a `Context` identitást fogják beállítani egy `Activity` értékre. Egy alkalmazás *csak* akkor jelenítheti meg a felügyelt identitás adatait, ha a `Activity` identitás ugyanarra az identitásra van beállítva. Általánosságban elmondható, hogy a folyamat szintű identitás csak akkor hasznos, ha az alkalmazás csak egyetlen felhasználóval működik egyszerre az összes szálon. Előfordulhat, hogy számos alkalmazásnak nem kell igénybe vennie.

Ha az alkalmazás a `Application` környezetet használja a rendszerszolgáltatások beolvasásához, győződjön meg arról, hogy a szál vagy a folyamat identitása be van állítva, vagy hogy beállította-e a felhasználói felület identitását az alkalmazás `Application` környezetében.

Ha `setUIPolicyIdentity` vagy `switchMAMIdentity` értékkel frissíti a felhasználói felület identitását, akkor a két módszer @no__t – 2 értéket adhat át.

* `IGNORE_INTENT`: akkor használja, ha olyan Identity kapcsolót kér, amely figyelmen kívül hagyja az aktuális tevékenységhez társított szándékot.
  Példa:

  1. Az alkalmazás egy felügyelt dokumentumot tartalmazó felügyelt identitástól kapott szándékot, és az alkalmazás megjeleníti a dokumentumot.
  2. A felhasználó személyes identitására vált, így az alkalmazás a felhasználói felület identitásának kapcsolóját kéri. A személyes identitásban az alkalmazás már nem jeleníti meg a dokumentumot, ezért `IGNORE_INTENT` értéket kell használnia az Identity kapcsoló kérésekor.

  Ha nincs beállítva, az SDK azt feltételezi, hogy a legutóbbi szándék továbbra is használatban van az alkalmazásban. Ennek hatására a rendszer megkapja az új identitásra vonatkozó házirendet, hogy a szándékot a bejövő adatokként kezelje, és az identitását használja.

>[!NOTE]
> Mivel a `CLIPBOARD_SERVICE` a felhasználói felületi műveletekhez használatos, az SDK a `ClipboardManager` műveletekhez tartozó előtér-tevékenység felhasználói felületének identitását használja.
> A következő, `MAMPolicyManager` metódusok használhatók az identitás beállításához és a korábban beállított azonosító értékek beolvasásához.

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
> A NULL értékre állításával törölheti az alkalmazás identitását.
>
> Az üres karakterláncot olyan identitásként lehet használni, amely soha nem fogja tartalmazni az alkalmazás-védelmi házirendet.

#### <a name="results"></a>Eredmények
Az azonosító jelentés visszaküldési eredményének értékének beállításához használt összes módszer `MAMIdentitySwitchResult` használatával. Négy érték adható vissza:

| Visszatérési érték | Alkalmazási helyzet |
|--            |--        |
| `SUCCEEDED`    | Az identitás módosítása sikeres volt. |
| `NOT_ALLOWED`  | Az identitás módosítása nem engedélyezett. Ez akkor fordul elő, ha kísérlet történt a felhasználói felület (`Context`) identitás beállítására, ha egy másik identitás van beállítva az aktuális szálon. |
| `CANCELLED`    | A felhasználó megszakította az identitás módosítását, általában a PIN-kód vagy a hitelesítési kérés vissza gombjára kattintva. |
| `FAILED`       | Az identitás módosítása nem sikerült egy meghatározatlan okból.|

Az alkalmazásnak biztosítania kell, hogy az identitás-kapcsoló sikeres legyen a vállalati adatok megjelenítése vagy használata előtt. A folyamat-és a szál-identitási kapcsolók jelenleg mindig sikeresek lesznek a több identitást támogató alkalmazások esetében, azonban fenntartjuk a jogot a meghibásodási feltételek hozzáadására. A felhasználói felület identitásának kapcsolója sikertelen lehet az érvénytelen argumentumok esetén, ha az ütközik a szál identitásával, vagy ha a felhasználó nem törli a feltételes indítási követelményeket (például megnyomja a vissza gombot a PIN-kód képernyőjén). A sikertelen felhasználói felület identitásának alapértelmezett viselkedése egy tevékenységen a tevékenység befejezése (lásd a következőt: @no__t – 0).

Ha a `Context` identitást `setUIPolicyIdentity` értékre állítja, az eredmény aszinkron módon lesz jelentve. Ha a `Context` egy `Activity`, az SDK nem tudja, hogy az identitás sikeres volt-e, amíg el nem végzi a feltételes indítást, ami szükségessé teheti a felhasználónak a PIN-kód vagy a vállalati hitelesítő adatok megadását. Az alkalmazás megadhat egy `MAMSetUIIdentityCallback` értéket, hogy megkapja ezt az eredményt, vagy a visszahívási objektum nullát is megadhatja. Vegye figyelembe, hogy ha egy hívást kezdeményeznek `setUIPolicyIdentity`-ra, míg egy előző, az adott *kontextusban* `setUIPolicyIdentity` hívás eredményét még nem szállították el, az új visszahívás felülírja a régit, és az eredeti visszahívás soha nem fog eredményül jutni.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

A tevékenységek identitását közvetlenül `MAMActivity` metódussal is beállíthatja a `MAMPolicyManager.setUIPolicyIdentity` hívása helyett. Ehhez használja a következő metódust:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

Ha azt szeretné, hogy az alkalmazás értesítést kapjon az adott tevékenység identitásának módosítására tett kísérletek eredményéről, akkor a `MAMActivity` metódust is felülbírálhatja.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Ha nem bírálja felül a `onSwitchMAMIdentityComplete` értéket (vagy hívja meg a `super` metódust), egy tevékenység sikertelen identitás-kapcsolója azt eredményezi, hogy a tevékenység befejeződik. Ha felülbírálja a metódust, ügyelnie kell arra, hogy a vállalati adatok nem jelennek meg egy sikertelen identitás-kapcsoló után.

>[!NOTE]
> Az identitás váltásához szükség lehet a tevékenység újbóli létrehozására. Ebben az esetben a `onSwitchMAMIdentityComplete` visszahívás a tevékenység új példányára lesz továbbítva.


### <a name="implicit-identity-changes"></a>Implicit identitások módosítása
Amellett, hogy az alkalmazás képes megállapítani az identitást, egy szálat vagy egy környezet identitását, a másik Intune által felügyelt alkalmazástól érkező, az alkalmazásra vonatkozó szabályzattal beérkező adatoktól függően változhatnak.

#### <a name="examples"></a>Példák
1. Ha egy tevékenységet egy másik MAM-alkalmazás által elküldett `Intent` címről indít el, a tevékenység identitása a másik alkalmazásban a `Intent` elküldésekor érvényes identitás alapján lesz beállítva.

2. A szolgáltatások esetében a szál identitása a `onStart` vagy `onBind` hívás időtartamára hasonlóan lesz beállítva. A `onBind` által visszaadott @no__tre irányuló hívások esetén a szál identitását is átmenetileg beállítja.

3. A `ContentProvider` hívásai Hasonlóképpen a szál identitását is megadhatják az időtartamuk során.


    Emellett a tevékenység felhasználó általi interakciója implicit identitás-kapcsolót eredményezhet.

    **Példa:** A `Resume` művelet során az engedélyezési kérésből lemondott felhasználó egy üres identitásra való implicit kapcsolót eredményez.

    Az alkalmazás lehetősége van arra, hogy tájékoztassa ezeket a módosításokat, és ha szükséges, az alkalmazás megtilthatja őket. @no__t – 0 és `MAMContentProvider` – tegye elérhetővé a következő metódust, amelyet az alosztályok felülbírálnak:

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchResultCallback callback);
    ```

    A `MAMActivity` osztályban egy további paraméter is szerepel a metódusban:

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchReason reason,
      final AppIdentitySwitchResultCallback callback);
    ```

    * A `AppIdentitySwitchReason` rögzíti az implicit kapcsoló forrását, és elfogadja a `CREATE`, `RESUME_CANCELLED` és `NEW_INTENT` értékeket.  A `RESUME_CANCELLED` ok akkor használatos, ha a tevékenység folytatása PIN-kód, hitelesítés vagy más megfelelőségi felhasználói felület megjelenítését eredményezi, és a felhasználó az adott felhasználói felületen próbálkozik a megszakítással, általában a vissza gomb használatával.


    * A `AppIdentitySwitchResultCallback` a következő:

      ```java
      public interface AppIdentitySwitchResultCallback {
          /**
            * @param result
            *            whether the identity switch can proceed.
            */
          void reportIdentitySwitchResult(AppIdentitySwitchResult result);
        }
        ```

      Ahol a ```AppIdentitySwitchResult``` vagy `SUCCESS` vagy `FAILURE`.

A `onMAMIdentitySwitchRequired` metódust minden implicit identitás-módosításhoz meg kell hívni, kivéve azokon, amelyek a `MAMService.onMAMBind` által visszaadott kötésen keresztül történtek. A `onMAMIdentitySwitchRequired` alapértelmezett implementációja azonnal hívja meg a következőket:

* @no__t – 0, ha az OK `RESUME_CANCELLED`.

* @no__t – 0 minden más esetben.

  Nem valószínű, hogy a legtöbb alkalmazásnak más módon kell letiltania vagy elhalasztania az identitás kapcsolóját, de ha egy alkalmazásnak erre van szüksége, akkor a következő szempontokat kell figyelembe venni:

  * Ha az identitás kapcsolója le van tiltva, az eredmény ugyanaz lesz, mint ha a `Receive` megosztási beállítások megtiltották az adatok beléptetését.

  * Ha egy szolgáltatás fut a fő szálon, a `reportIdentitySwitchResult` metódust szinkron **módon kell** meghívni, vagy a felhasználói felület szála leáll.

  * A **`Activity`** létrehozáshoz a `onMAMIdentitySwitchRequired` a `onMAMCreate` előtt lesz meghívva. Ha az alkalmazásnak meg kell jelenítenie a felhasználói felületet annak megállapításához, hogy engedélyezi-e az identitás kapcsolóját, a felhasználói felületet egy *másik* tevékenység használatával kell megjeleníteni.

  * Egy **`Activity`** esetében, ha az üres identitásra való áttérést a `RESUME_CANCELLED` ok miatt kéri, az alkalmazásnak módosítania kell a folytatott tevékenységet az adott Identity kapcsolóval konzisztens adatok megjelenítéséhez.  Ha ez nem lehetséges, az alkalmazásnak el kell utasítania a kapcsolót, és a rendszer újra kéri a felhasználót, hogy tartsa be a folytatási identitáshoz tartozó szabályzatot (például az alkalmazás PIN-kód beléptetése képernyőn).

    > [!NOTE]
    > A többszörös identitású alkalmazások mindig fogadják a felügyelt és a nem felügyelt alkalmazásokból érkező bejövő adatok fogadását. Az alkalmazás feladata, hogy felügyelt módon kezelje a felügyelt identitásokból származó adatok mennyiségét.

  Ha a kért identitás felügyelve van (a `MAMPolicyManager.getIsIdentityManaged` beállítással ellenőrizze), de az alkalmazás nem tudja használni ezt a fiókot (például azért, mert a fiókokat, például az e-mail-fiókokat) először az alkalmazásban kell beállítani, akkor el kell utasítania az Identity kapcsolót.

#### <a name="build-plugin--tool-considerations"></a>Build beépülő modul/eszköz szempontjai
Ha nem ad explicit módon öröklést a `MAMActivity`, `MAMService`, vagy a `MAMContentProvider` (mivel lehetővé teszi, hogy a Build eszköz ezt a módosítást hajtsa végre), de továbbra is szükség van az identitás-kapcsolók feldolgozására, ehelyett a `MAMActivityIdentityRequirementListener` (`Activity`) vagy `MAMIdentityRequirementListener` (`Service` vagy `ContentProviders`) megvalósításához. .
A `MAMActivity.onMAMIdentitySwitchRequired` alapértelmezett viselkedése a `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)` statikus metódus meghívásával érhető el.

Hasonlóképpen, ha felül kell bírálnia `MAMActivity.onSwitchMAMIdentityComplete`, akkor a `MAMActivityIdentitySwitchListener` megvalósítását explicit módon, a `MAMActivity` értéktől függetlenül is végrehajthatja.

### <a name="preserving-identity-in-async-operations"></a>Identitás megőrzése aszinkron műveletekben
Gyakori művelet a felhasználói felületi szálon a háttérben végzett feladatok másik szálra való küldéséhez. A többszörös identitást használó alkalmazásoknak biztosítaniuk kell, hogy ezek a háttérben futó feladatok a megfelelő identitással működjenek, ami gyakran ugyanaz az identitás, amelyet az elküldött tevékenység használ. A MAM SDK a `MAMAsyncTask` és a `MAMIdentityExecutors` lehetőséget kínálja az identitás megőrzésének támogatásához.
Ezeket akkor kell használni, ha az aszinkron művelet egy fájlba írhatja a vállalati adatforrásokat, vagy más alkalmazásokkal kommunikálhat.

#### <a name="mamasynctask"></a>MAMAsyncTask
Ha `MAMAsyncTask` használatát szeretné használni, egyszerűen csak örökölje `AsyncTask` helyett, és cserélje le a `doInBackground` és a `onPreExecute` felülbírálásait `doInBackgroundMAM` és `onPreExecuteMAM` értékkel. A `MAMAsyncTask` konstruktor egy tevékenységi kontextust használ. Példa:

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
a `MAMIdentityExecutors` lehetővé teszi egy meglévő `Executor` vagy `ExecutorService` példány becsomagolását identitás-megőrzési `Executor` @ no__t-4 @ no__t-5 `wrapExecutor` és `wrapExecutorService` metódusokkal. Példa:

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>Fájl védelme
Minden fájlhoz társítva van egy, a létrehozáskor, a szál és a folyamat identitásán alapuló identitás. Ez az identitás a fájlok titkosítására és a szelektív törlésre is használható. Csak azok a fájlok lesznek titkosítva, amelyek identitása felügyelve van, és rendelkezik a titkosítást igénylő házirenddel. Az SDK alapértelmezett szelektív funkcióinak törlése csak azokat a fájlokat törli, amelyek a kezelt identitáshoz tartoznak, és amelyek törlését kérték. Az alkalmazás a `MAMFileProtectionManager` osztály használatával lekérdezheti vagy módosíthatja a fájlok identitását.

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

#### <a name="app-responsibility"></a>Alkalmazás felelőssége
A MAM nem tud automatikusan következtetést kikövetkeztetni a beolvasott fájlok és az `Activity` értékben megjelenített fájlok között. Az alkalmazásoknak a vállalati adatok megjelenítése előtt megfelelően *kell* beállítaniuk a felhasználói felület identitását. Ide tartoznak a fájlokból beolvasott adatok. Ha egy fájl az alkalmazáson kívülről származik (vagy egy `ContentProvider` vagy nyilvánosan írható helyről olvas), az alkalmazásnak meg *kell* próbálnia meghatározni a fájl identitását (a `MAMFileProtectionManager.getProtectionInfo` használatával), mielőtt a fájlból beolvasott adatokat megjelenítse. Ha `getProtectionInfo` nem null értékű, nem üres identitást jelez, a felhasználói *felület identitásának meg kell* egyeznie az identitással (`MAMActivity.switchMAMIdentity` vagy `MAMPolicyManager.setUIPolicyIdentity`). Ha az Identity kapcsoló nem sikerül, a fájlból származó adatok *nem* jeleníthetők meg.

Egy folyamat például a következőhöz hasonló lehet:
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
Ha egy korábban az egyidentitású Intune-integrációval kiadott alkalmazás több identitást is integrál, a korábban telepített alkalmazások átmeneti állapotba kerülnek (nem látható a felhasználó számára, nincs társított UX). Az alkalmazásnak nem *szükséges* explicitnek lennie ahhoz, hogy kezelni tudja ezt az áttérést. Az áttérés előtt létrehozott összes fájl felügyelt állapotba kerül (tehát titkosítva marad, ha a titkosítási házirend be van kapcsolva). Ha szükséges, a frissítés észlelésével és a `MAMFileProtectionManager.protect` használatával címkézheti az adott fájlokat vagy címtárakat az üres identitással (ami titkosítva fogja eltávolítani a titkosítást).

#### <a name="offline-scenarios"></a>Offline forgatókönyvek
A fájl identitásának címkézése érzékeny az offline üzemmódra. A következő szempontokat kell figyelembe venni:

* Ha a Céges portál nincs telepítve, a fájlok nem lehetnek Identity-Tagged.

* Ha a Céges portál telepítve van, de az alkalmazásnak nincs Intune MAM-szabályzata, a fájlok nem lehetnek megbízhatóan címkézve az identitással.

* Ha a fájl identitásának címkézése elérhetővé válik, az összes korábban létrehozott fájl személyes/nem felügyelt (üres karakterlánc-identitáshoz tartozó)ként lesz kezelve, kivéve, ha az alkalmazást korábban egyetlen identitással felügyelt alkalmazásként telepítették, amely esetben a rendszer a következőt kezeli: a regisztrált felhasználóhoz tartozó.

### <a name="directory-protection"></a>Címtár-védelem
A könyvtárak védelme a fájlok védelméhez használt `protect` módszer használatával lehetséges. A címtár védelme rekurzív módon, a címtárban található összes fájlra és alkönyvtárra, valamint a címtárban létrehozott új fájlokra is vonatkozik. Mivel a címtárszolgáltatások rekurzív módon lettek alkalmazva, a `protect` hívás hosszabb időt is igénybe vehet a nagyméretű könyvtárak esetében. Emiatt a védelmet alkalmazó alkalmazások nagy mennyiségű fájlt tartalmazó könyvtárba szeretnének futtatni `protect` aszinkron módon egy háttérben futó szálon.

### <a name="data-protection"></a>Data Protection
Nem lehet címkével ellátni több identitáshoz tartozó fájlt. Azok az alkalmazások, amelyeknek az adott fájl különböző felhasználóihoz tartozó adataikat kell tárolniuk, manuálisan is megtehetik a `MAMDataProtectionManager` által biztosított szolgáltatások használatával. Ez lehetővé teszi az alkalmazás számára az adatok titkosítását és egy adott felhasználóhoz való összekapcsolását. A titkosított adatforgalom alkalmas a fájlban lévő lemezre való tárolásra. Az identitáshoz kapcsolódó adatok lekérése és az adatok titkosítása később is megoldható.

A `MAMDataProtectionManager` használatát használó alkalmazásoknak egy fogadót kell alkalmazniuk a `MANAGEMENT_REMOVED` értesítéshez. Az értesítés befejeződése után az ezen az osztályon keresztül védett pufferek többé nem lesznek olvashatók, ha a fájlok titkosítása engedélyezve lett a pufferek védelme során. Az alkalmazások ezt a helyzetet úgy javíthatják, ha az értesítés során az összes pufferen meghívja a `MAMDataProtectionManager.unprotect` értéket. Az értesítés során a védelem meghívása is biztonságos, ha meg szeretné őrizni az azonosító adatokat – a titkosítás garantált, hogy az értesítés során le legyen tiltva.

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
Ha az alkalmazás a `ParcelFileDescriptor` értéktől eltérő vállalati adatokat biztosít `ContentProvider`-en keresztül, akkor az alkalmazásnak a (z) `MAMContentProvider` metódusban kell meghívnia a (z) `isProvideContentAllowed(String)` metódust, amely a tulajdonos identitás UPN-fájlját (egyszerű felhasználónév) továbbítja a tartalomhoz Ha ez a függvény Hamis értéket ad vissza, a tartalmat *nem* kell visszaadnia a hívónak. A tartalomszolgáltató által visszaadott fájl-leírókat a rendszer automatikusan kezeli a fájl identitása alapján.

Ha nem örökli a `MAMContentProvider` explicit módon, és ehelyett engedélyezi a Build-eszközkészletet a módosítás végrehajtásához, meghívhatja ugyanazt a metódus statikus verzióját: `MAMContentProvider.isProvideContentAllowed(provider,
contentIdentity)`.

### <a name="selective-wipe"></a>Szelektív törlés
Ha egy többszörös identitású alkalmazás regisztrálja a `WIPE_USER_DATA` értesítéseket, akkor az alkalmazás feladata, hogy eltávolítsa a felhasználó összes adatát, beleértve az összes olyan fájlt, amelyet az adott felhasználóhoz tartozó identitás-címkézett. Ha az alkalmazás egy fájlból távolítja el a felhasználói adatait, de más adatokkal kívánja hagyni a fájlt, akkor a fájl identitását módosítania *kell* (`MAMFileProtectionManager.protect` értékről egy személyes felhasználóra vagy az üres identitásra). Ha a titkosítási házirend használatban van, a rendszer nem fogja visszafejteni az összes olyan fájlt, amelyet a felhasználó töröl, és a törlés után elérhetetlenné válik az alkalmazás számára.

A `WIPE_USER_DATA`-hoz regisztrált alkalmazások nem kapják meg az SDK alapértelmezett szelektív törlési viselkedésének előnyeit. A többszörös identitást támogató alkalmazások esetében ez a veszteség nagyobb jelentőséggel bír, mivel a MAM alapértelmezett szelektív törlése csak azokat a fájlokat törli, amelyeknek az identitása törlést céloz meg. Ha a többszörös identitást támogató alkalmazás a MAM alapértelmezett szelektív törlést szeretné elvégezni, _**és**_ a saját, törlésre vonatkozó műveleteit szeretné elvégezni, akkor regisztrálnia kell `WIPE_USER_AUXILIARY_DATA` értesítésekre. Ezt az értesítést azonnal az SDK küldi el, mielőtt végrehajtja a MAM alapértelmezett szelektív törlését. Az alkalmazások soha nem regisztrálhatnak a `WIPE_USER_DATA` és a `WIPE_USER_AUXILIARY_DATA` értékre.

Az alapértelmezett szelektív törlés automatikusan lezárta az alkalmazást, befejezi a tevékenységeket, és megöli az alkalmazás folyamatát. Ha az alkalmazás felülbírálja az alapértelmezett szelektív törlést, érdemes lehet manuálisan bezárni az alkalmazást annak megakadályozása érdekében, hogy a felhasználó hozzáférjen a memóriában tárolt adatokhoz a törlés után.

## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Az Android-alkalmazások MAM-alapú megkeresésének engedélyezése (nem kötelező)
Az alkalmazásspecifikus kulcs-érték párok az Intune-konzolon konfigurálhatók a [MAM-We](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) és az [Android Enterprise](https://docs.microsoft.com/intune/app-configuration-policies-use-android)rendszerhez.
Ezeket a kulcs-érték párokat az Intune egyáltalán nem értelmezi, de átadja az alkalmazásnak. Az ilyen konfigurációt fogadni kívánó alkalmazások a `MAMAppConfigManager` és a `MAMAppConfig` osztályt is használhatják. Ha ugyanahhoz az alkalmazáshoz több házirend is vonatkozik, előfordulhat, hogy több ütköző érték is elérhető ugyanahhoz a kulcshoz.

> [!NOTE] 
> Konfigurációk beállítása a MAM-n keresztül történő kézbesítéshez – nem lehet delievered a `offline` (ha a Céges portál nincs telepítve).  Ebben az esetben csak az Android Enterprise AppRestrictions lesznek továbbítva egy `MAMUserNotification` értékkel egy üres identitáson.

### <a name="get-the-app-config-for-a-user"></a>Felhasználóhoz tartozó alkalmazás konfigurációjának beolvasása
Az alkalmazás konfigurációja a következőképpen kérhető le:
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
```

Ha nincs MAM-regisztrált felhasználó, de az alkalmazása továbbra is szeretné lekérni az androidos vállalati konfigurációt (amely nem egy adott felhasználóra vonatkozik), akkor null értékű vagy üres karakterláncot adhat át.

### <a name="conflicts"></a>Ütközések
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

```java
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
Az alkalmazás konfigurációja új értesítési típust hoz létre:
* **REFRESH_APP_CONFIG**: ezt az értesítést a rendszer egy `MAMUserNotification` üzenetben küldi el, és tájékoztatja az alkalmazásról, hogy az új alkalmazás-konfigurációs adatbázis elérhető.

### <a name="further-reading"></a>További olvasnivalók
A MAM megcélzó alkalmazások konfigurációs szabályzatának Androidon történő létrehozásával kapcsolatos további információkért tekintse meg a következő témakört: a MAM megcélzó alkalmazások konfigurációjának [használata az Android rendszerhez készült Microsoft Intune alkalmazás-konfigurációs szabályzatok használatáról](https://docs.microsoft.com/intune/app-configuration-policies-managed-app).

Az alkalmazás konfigurációja a Graph API használatával is konfigurálható. További információ: [Graph API docs for MAM Targeted config](https://docs.microsoft.com/graph/api/resources/intune-mam-targetedmanagedappconfiguration).

## <a name="style-customization-optional"></a>Stílus testreszabása (nem kötelező)
A MAM SDK által létrehozott nézetek vizuálisan testreszabhatók úgy, hogy jobban illeszkedjenek az alkalmazáshoz, amelyben integráltak. Testreszabhatja az elsődleges, a másodlagos és a háttérszínt, valamint az alkalmazás emblémájának méretét is. A stílus testreszabása nem kötelező, és a rendszer az alapértelmezett beállításokat használja, ha nincs beállítva egyéni stílus.

### <a name="how-to-customize"></a>Testreszabás
Ahhoz, hogy a stílus módosítása az Intune MAM nézeteire vonatkozzon, először létre kell hoznia egy stílus-felülbírálási XML-fájlt. Ezt a fájlt az alkalmazás "/res/XML" könyvtárába kell helyezni, és Ön is elnevezheti azt. Az alábbi példa azt a formátumot mutatja be, amelyet a fájlnak követnie kell.

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

Az alkalmazáson belül már meglévő erőforrásokat újra fel kell használni. Például a zöld színt kell megadnia a Colors. xml fájlban, és hivatkozni kell rá. A (z) "#0000ff" hexadecimális színkód nem használható. Az alkalmazás emblémájának maximális mérete 110 dip (DP). Kisebb embléma-képet is használhat, de a maximális méret betartása a legjobb találatokat eredményezi. Ha túllépi az 110 dip-korlátot, a rendszer lekicsinyíti a képet, és valószínűleg elmosódást okoz.

Alább látható az engedélyezett Style attribútumok teljes listája, az általuk vezérelt felhasználói felületi elemek, a hozzájuk tartozó XML-attribútumok, valamint a várt erőforrás típusa.

|Style attribútum | Érintett FELHASZNÁLÓIFELÜLET-elemek | Attribútum-elemnév neve | Várt erőforrástípus |
| -- | -- | -- | -- |
| Háttérszín | PIN-kód képernyő háttérszíne <Br>PIN-kód mező kitöltési színe | background_color | Szín |
| Előtér színe | Előtér szövegének színe <br> PIN-kód keretének alapértelmezett állapota <br> A PIN-kód beviteli mezőjében szereplő karakterek (beleértve a megzavarodott karaktereket), amikor a felhasználó PIN-kódot ad meg| foreground_color | Szín|
| Kiegészítő szín | PIN-kód keretének kiemelése <br> Hivatkozások |accent_color | Szín |
| Alkalmazás emblémája | Az Intune-alkalmazás PIN-kódjának képernyőjén megjelenő nagyméretű ikon | logo_image | Rajzolható |

## <a name="default-enrollment-optional"></a>Alapértelmezett regisztráció (nem kötelező)
Az alábbi útmutatást követve megkövetelheti a felhasználói rákérdezést az alkalmazás indításakor az automatikus APP-WE szolgáltatás beléptetéséhez (ez a szakasz ezt az **alapértelmezett regisztrációt** hívja meg), amely az Intune app Protection-szabályzatok alkalmazásával csak az Intune által védett felhasználók számára engedélyezi a SDK-val integrált Android LOB-alkalmazás. Azt is ismerteti, hogyan engedélyezhető az SSO az SDK-val integrált Android LOB-alkalmazáshoz. Ez **nem** támogatott olyan áruházbeli alkalmazások esetében, amelyeket nem Intune-felhasználók is használhatnak.

> [!NOTE] 
> Az **alapértelmezett regisztráció** előnyei közé tartozik egy egyszerűsített módszer a szabályzat beszerzéséhez az App-We szolgáltatásban az eszközön található alkalmazáshoz.

> [!NOTE] 
> Az **alapértelmezett regisztráció** a szuverén felhő.

Engedélyezze az alapértelmezett regisztrációt a következő lépésekkel:

1. Ha az alkalmazás integrálja az ADAL-t, vagy engedélyeznie kell az SSO-t, [konfigurálja a ADAL](#configure-azure-active-directory-authentication-library-adal) -t az [általános ADAL-konfigurációs](#common-adal-configurations) #2 után. Ha ez nem lehetséges, kihagyhatja ezt a lépést.
   
2. Engedélyezze az alapértelmezett regisztrációt úgy, hogy a következő értéket adja meg a jegyzékfájlban:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > Ennek az egyetlen MAM-integrációnak kell lennie az alkalmazásban. Ha bármilyen más kísérletet tesz a MAMEnrollmentManager API-k meghívására, ütközések lépnek fel.

3. A MAM-szabályzat engedélyezéséhez a következő értéket kell megadnia a jegyzékfájlban:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > Ez kényszeríti a felhasználót, hogy töltse le a Céges portál az eszközön, és a használat előtt végezze el az alapértelmezett regisztrációs folyamatot.

## <a name="limitations"></a>Korlátozások

### <a name="policy-enforcement-limitations"></a>Házirend-kényszerítési korlátozások

* **Tartalom**-feloldások használata: az "átvitel vagy fogadás" Intune-szabályzat letilthatja vagy részlegesen blokkolhatja a tartalom-feloldó használatát egy másik alkalmazásban található tartalomszolgáltató eléréséhez. Ez azt eredményezi, hogy `ContentResolver` metódus null értéket ad vissza, vagy a hiba értékét kidobja (például `openOutputStream` a következőt fogja eldobni: `FileNotFoundException`, ha le van tiltva). Az alkalmazás eldöntheti, hogy a tartalom-feloldón keresztüli adatírás sikertelen volt-e (vagy a házirend okozta volna) a hívással:

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    vagy ha nincs társított tevékenység:

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    Ebben a második esetben a többszörös identitású alkalmazásoknak ügyelniük kell a szál identitásának megfelelő beállítására (vagy egy explicit identitást kell átadnia a `getPolicy` hívásnak).

### <a name="exported-services"></a>Exportált szolgáltatások
Az Intune app SDK-ban található AndroidManifest. xml fájl **MAMNotificationReceiverService**tartalmaz, amelyeknek olyan exportált szolgáltatásnak kell lenniük, amely lehetővé teszi, hogy a céges portál értesítést küldjön egy felügyelt alkalmazásnak. A szolgáltatás ellenőrzi a hívót annak ellenőrzésére, hogy csak a Céges portál küldhet-e értesítéseket.

### <a name="reflection-limitations"></a>Reflexiós korlátozások
A MAM-alaposztályok némelyike (például `MAMActivity`, `MAMDocumentsProvider`) olyan metódusokat tartalmaz (az eredeti Android alaposztályok alapján), amelyek paraméter-vagy visszatérési típusokat használnak, csak bizonyos API-szintek felett jelennek meg. Emiatt előfordulhat, hogy az alkalmazás-összetevők összes metódusának enumerálásához nem mindig lehetséges a reflexió használata. Ez a korlátozás nem korlátozódik a MAM-ra, ugyanaz a korlátozás érvényes, ha az alkalmazás maga is megvalósítja ezeket a metódusokat az Android alaposztályai alapján.

### <a name="robolectric"></a>Robolectric
A MAM SDK viselkedésének tesztelése a Robolectric alatt nem támogatott. A MAM SDK-t a Robolectric alatt futó ismert problémák okozták, mivel a Robolectric alatt található viselkedések nem pontosan utánozzák a valós eszközökön vagy emulátorokon.

Ha tesztelni szeretné az alkalmazást a Robolectric alatt, az ajánlott megkerülő megoldás az, hogy az alkalmazás osztályának logikáját egy segítővé helyezze át, és az egység-tesztelési apk olyan alkalmazási osztállyal legyen létrehozva, amely nem örököl a MAMApplication.

## <a name="expectations-of-the-sdk-consumer"></a>Az SDK-fogyasztó elvárásai
Az Intune SDK fenntartja az Android API által biztosított szerződést, bár a házirend-kényszerítés eredményeképpen gyakrabban aktiválható a meghibásodási feltételek. Ezek az androidos ajánlott eljárások csökkentik a hibák valószínűségét:

* Azok az androidos SDK-függvények, amelyek NULL értékkel térhetnek vissza, nagyobb valószínűséggel lehetnek null értékűek.  A problémák minimalizálásához győződjön meg arról, hogy a megfelelő helyen vannak null értékű ellenőrzések.

* Az ellenőrizendő szolgáltatásokat a MAM-csere API-k segítségével kell ellenőrizni.

* Minden származtatott függvénynek a Super Class verziójára kell hívnia.

* Kerülje az API-k nem egyértelmű módon való használatát. Például a `Activity.startActivityForResult` használata a Requestcode furcsaságokat ellenőrzése nélkül furcsa viselkedést okoz.

## <a name="telemetry"></a>Telemetria

Az Androidhoz készült Intune app SDK nem szabályozza az alkalmazásból származó adatgyűjtés vezérlését. A Céges portál alkalmazás alapértelmezés szerint naplózza a rendszer által generált adattípusokat. Ezeket az adatMicrosoft Intune küldi a rendszer. A Microsoft-szabályzatok alapján semmilyen személyes adatot nem gyűjtünk.

> [!NOTE]
> Ha a végfelhasználók nem szeretnék elküldeni ezeket az adatfájlokat, ki kell kapcsolniuk a telemetria elemet a Céges portál alkalmazás beállítások területén. További információ: a [Microsoft használati adatok gyűjtésének kikapcsolása](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Ajánlott androidos eljárások

* Az összes függvénytár-projektnek ugyanazzal az Android: csomaggal kell rendelkeznie, ahol lehetséges. Ez nem fog szórványosan meghiúsulni a futási időben; Ez a probléma pusztán a létrehozás ideje. Az Intune app SDK újabb verziói el fogják távolítani a redundancia néhány verzióját.

* Használja a legújabb Android SDK Build-eszközöket.

* Távolítsa el az összes szükségtelen és használaton kívüli kódtárat (például Android. support. v4)

## <a name="testing"></a>Tesztelés
Tekintse meg a [tesztelési útmutatót](app-sdk-android-testing-guide.md).
