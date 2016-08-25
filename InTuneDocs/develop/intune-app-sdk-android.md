---
title: "A Microsoft Intune App SDK Androidon – útmutató fejlesztőknek | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2915cca314b489bbcb590d01b03a0b38134fa619
ms.openlocfilehash: d2e4b6903d86b79edd9c758b2ce51733831e785a


---

# A Microsoft Intune App SDK Androidon – útmutató fejlesztőknek

> [!NOTE]
> Kezdésként érdemes lehet elolvasni [Az Intune APP SDK áttekintése](intune-app-sdk.md) című cikket, amely ismerteti az SDK aktuálisan elérhető funkcióit és az integrációval kapcsolatos előkészületeket a támogatott platformokon. 

# Az SDK tartalma 

Az Intune App SDK for Android egy szabványos androidos függvénytár, amely nem rendelkezik külső függőségekkel. Az SDK összetevői:  

* **`Microsoft.Intune MAM.SDK.jar`**: Azok a felületek, amelyek ahhoz szükségesek, hogy az alkalmazásokban a MAM engedélyezve legyen, és a Microsoft Intune Munkahelyi portál alkalmazásával lehetséges legyen az együttműködés. Az alkalmazásoknak androidos függvénytárhivatkozásként kell megadniuk.

*  **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**: Azok a felületek, amelyek az androidos v4 támogatási könyvtárat használó alkalmazásokban a MAM engedélyezéséhez szükségesek.  Az ezen támogatást igénylő alkalmazásoknak közvetlenül kell hivatkozniuk a jar-fájlra. 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**: Azok a felületek, amelyek az androidos v7 támogatási könyvtárat használó alkalmazásokban a MAM engedélyezéséhez szükségesek.   Az ezen támogatást igénylő alkalmazásoknak közvetlenül kell hivatkozniuk a jar-fájlra

* **Az erőforrás-könyvtár**: Azok az erőforrások (például karakterláncok), amelyeket az SDK alkalmaz. 

* **`Microsoft.Intune.MAM.SDK.aar`**: Az SDK-összetevők a Support.V4 és a Support.V7 jar-fájlok kivételével. Ez a fájl az egyes összetevők helyett használható, ha a buildelési rendszer támogatja az AAR-fájlokat.

* **`AndroidManifest.xml`**: A további belépési pontok és a könyvtárakra vonatkozó követelmények. 

* **`THIRDPARTYNOTICES.TXT`**: Attribútumértesítés, amely elismeri az alkalmazásba összeállítani kívánt külső és/vagy OSS-kódot. 

# Követelmények 

Az Intune App SDK egy lefordított androidos projekt. Ennek eredményeként nagymértékben független az alkalmazás által a minimális vagy a cél API-verzióhoz használt Android-verziótól. Az SDK az Android API 14 (Android 4.0 +) – Android 24 közötti verziókat támogatja. 

# Az Intune App SDK működése 

Az Intune App SDK az alkalmazás forráskódjának módosítását igényli az alkalmazás-felügyeleti szabályzatok engedélyezéséhez. Ez az androidos alaposztályok egyenértékű felügyelt osztályokra való cseréjén keresztül történik, amelyekre a dokumentum a `MAM`. Az SDK-osztályok az androidos alaposztály és az alkalmazás saját származtatott verziója között helyezkednek el.  Egy tevékenység esetén ez például egy hasonló öröklési hierarchiát eredményez: `Activity ->MAMActivity->AppSpecificActivity`.

Amikor a `AppSpecificActivity` kommunikálni szeretne a szülőjével, pl. a `super.onCreate())` elemmel, a `MAMActivity` a szülőosztály annak ellenére, hogy az öröklési hierarchiában van és lecserél néhány módszert. Az androidos alkalmazások egyedülálló móddal rendelkeznek, és az egész rendszerhez hozzáférhetnek a környezeti objektumon keresztül.  A beépített Intune App SDK-val rendelkező alkalmazások viszont kettős móddal rendelkeznek, az alkalmazások továbbra is hozzáférhetnek a rendszerhez a környezeti objektumon keresztül, de a használt alaptevékenységtől függően a környezeti objektumot vagy az Android biztosítja, vagy intelligens módon vált a rendszer korlátozott nézete és az Android által biztosított környezet között.

Az androidos Intune App SDK a Vállalati portál alkalmazásnak az eszközön való jelenlétére támaszkodik a MAM-szabályzatok engedélyezéséhez. Amikor a Vállalati portál alkalmazás nincs jelen, a MAM-engedélyezett alkalmazás viselkedése nem módosul, és úgy fog működni, mint bármely más mobilalkalmazás. Ha a Vállalati portál telepítve van, és a felhasználóra vonatkozó szabályzattal rendelkezik, az SDK belépési pontjai aszinkron módon inicializálódnak. Az inicializálás csak akkor szükséges, amikor az Android először hozza létre a folyamatot. Az inicializálás során létrejön a kapcsolat a Vállalati portál alkalmazással, és letöltődik az alkalmazáskorlátozási szabályzat.  

# Az Intune App SDK integrálása
 
A korábban ismertetetteknek megfelelően az SDK az alkalmazás forráskódjának módosítását igényli az alkalmazás-felügyeleti szabályzatok engedélyezéséhez. A következő lépések szükségesek a MAM engedélyezéséhez az alkalmazásban: 

## Az osztályok, a metódusok és a tevékenységek lecserélése a MAM-kompatibilis megfelelőkre (kötelező) 

* Az androidos alaposztályokat MAM-megfelelőjükkel kell helyettesíteni. Ehhez az alábbi táblázatban felsorolt osztályok összes példányát le kell cserélni az Intune App SDK-beli megfelelőjükre.  

    | Androidos osztály | Intune App SDK-beli helyettesítése |
    |--|--|
    | android.app.Activity | MAMActivity |
    | android.app.ActivityGroup | MAMActivityGroup |
    | android.app.AliasActivity | MAMAliasActivity |
    | android.app.Application | MAMApplication |
    | android.app.DialogFragment | MAMDialogFragment |
    | android.app.ExpandableListActivity | MAMExpandableListActivity |
    | android.app.Fragment | MAMFragment |
    | android.app.IntentService | MAMIntentService |
    | android.app.LauncherActivity | MAMLauncherActivity |
    | android.app.ListActivity | MAMListActivity |
    | android.app.NativeActivity | MAMNativeActivity |
    | android.app.PendingIntent | MAMPendingIntent |
    | android.app.Service | MAMService |
    | android.app.TabActivity | MAMTabActivity |
    | android.app.TaskStackBuilder | MAMTaskStackBuilder |
    | android.app.backup.BackupAgent | MAMBackupAgent |
    | android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | android.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | android.content.BroadcastReceiver | MAMBroadcastReceiver |
    | android.content.ContentProvider | MAMContentProvider |
    | android.os.Binder | MAMBinder * |
    | android.provider.DocumentsProvider | MAMDocumentsProvider |
    | android.preference.PreferenceActivity | MAMPreferenceActivity |

    * A Binder cseréje a MAMBinder metódussal csak akkor szükséges, ha a Binder nem jön létre egy AIDL-felületről.

    **Microsoft.Intune.MAM.SDK.Supp, vagy egyt.v4.jar**:

    | Androidos osztály Intune MAM | SDK-beli helyettesítése |
    |--|--|
    | Android.support.v4.App.DialogFragment | MAMDialogFragment
    | android.support.v4.app.FragmentActivity | MAMFragmentActivity
    | android.support.v4.app.Fragment | MAMFragment
    | Android.support.v4.App.TaskStackBuilder | MAMTaskStackBuilder
    | Android.support.v4.Content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Supp, vagy egyt.v7.jar**:

    |Androidos osztály | Intune MAM SDK-beli helyettesítése |
    |--|--|
    |Android.support.v7.App.ActionBarActivity | MAMActionBarActivity |


* Olyan androidos belépési pont használatakor, amely felül lett írva MAM-megfelelőjével a belépési pont életciklusának egy alternatív verzióját kell használni (a `MAMApplication`osztály kivételével).

    Így például a `MAMActivity`, származtatásakor az `onCreate` felülírása helyett, és a `super.onCreate`metódus hívásakor a tevékenységnek felül kell írnia az `onMAMCreate` metódust, és a`uper.onMAMCreate`. Ez lehetővé teszi (többek között) tevékenységek indításának korlátozását bizonyos esetekben. 

# Alkalmazás részvételét igénylő szolgáltatások engedélyezése 

Egyes szabályzatokat az SDK önállóan nem tud megvalósítani. Ahhoz, hogy az alkalmazás szabályozhassa e funkciók működését, elérhetővé kell tenni több, az alábbi `AppPolicy` felületen található API-t.  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

## Az alkalmazásbeli mentési viselkedés vállalati rendszergazda általi szabályozásának engedélyezése

Számos alkalmazás valósít meg olyan funkciókat, amelyek lehetővé teszik a végfelhasználó számára fájlok mentését a helyi háttértárra vagy egy másik szolgáltatásba. Az Intune App SDK lehetővé teszi a vállalati rendszergazdáknak az adatszivárgás elleni, a szervezetek igényei szerinti házirendmegkötések alkalmazásával.  A rendszergazda által szabályozható házirendek egyike, hogy a felhasználók menthetnek-e személyes adattárba. Ide tartoznak a helyi mentési helyek, az SD-kártyák és a biztonsági mentési szolgáltatások. A funkció engedélyezéséhez alkalmazás részvételére van szükség. Ha az alkalmazás lehetővé teszi a személyes vagy felhőbeli helyekre való mentést közvetlenül az alkalmazásból, a funkciót meg kell valósítani annak biztosításához, hogy a vállalati rendszergazda szabályozhassa, hogy engedélyezett-e a mentés az adott helyre, vagy sem. Az alábbi API lehetővé teszi, hogy az alkalmazás megállapítsa, hogy a személyes tárolóba való mentés engedélyezett-e az aktuális felügyeleti házirend szerint. Az alkalmazás ekkor érvényesítheti a házirendet, mivel meg tudja állapítani, hogy elérhető-e személyes adattár a felhasználó számára az alkalmazáson keresztül.  

Az alkalmazás a következő hívással megállapíthatja, hogy a házirend érvényesítve van-e: 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**Megjegyzés**: A MAMComponents.get(AppPolicy.class) mindig nem null értékű alkalmazás-szabályzatot ad vissza, akkor is, ha az eszköz vagy az alkalmazás nem áll felügyelet alatt. 

## Annak lehetővé tétele, hogy az alkalmazás észlelhesse, hogy szükség van-e a PIN-kódokra vonatkozó szabályzatra
 
 Bizonyos további szabályzatok esetében az alkalmazás esetleg letilthat egyes funkciókat, hogy azok ne ismétlődjenek az Intune App SDK-ban. Például ha az alkalmazás saját PIN-kódot kérő felhasználói felülettel rendelkezik, akkor előfordulhat, hogy le kívánja tiltani, ha az SDK úgy van beállítva, hogy a felhasználónak PIN-kódot kell megadnia. 

Annak megállapításához, hogy PIN-kódokra vonatkozó szabályzat a PIN-kód rendszeres bevitelének megkövetelése van konfigurálva, az alkalmazás a következő hívást használhatja: 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

## Regisztráció az SDK értesítéseihez  

Az Intune App SDK lehetővé teszi, hogy az alkalmazások szabályozhassák a viselkedést bizonyos szabályzatok, például egy távoli törlési szabályzat a vállalati rendszergazda általi használata esetén. Ehhez regisztrálnia kell az SDK által küldött értesítésekhez egy `MAMNotificationReceiver` osztály létrehozásával és annak regisztrálásával a következővel: `MAMNotificationReceiverRegistry`. Ez a fogadó és a fogadó által az  `App.onCreate`metódusban fogadni kívánt értesítés típusának megadásával történik, az alábbi példában látható módon:
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` egyszerűen értesítéseket fogad. Egyes értesítéseket közvetlenül az SDK kezel, mások az alkalmazás részvételét igénylik. Az alkalmazásnak igaz vagy hamis értéket kell visszaadnia egy értesítésből. Hacsak valamely, általa az értesítés eredményeként megkísérelt művelet sikertelen nem volt, mindig igaz értéket kell visszaadjon. A hiba jelenthető az Intune szolgáltatásnak, például ha az alkalmazás azt jelzi, hogy nem sikerült törölnie a felhasználói adatokat. A `MAMNotificationReceiver.onReceive`metódusban biztonságosan blokkolható; visszahívási metódusa nem a felhasználói felület szálán fut. 

A `MAMNotificationReceiver felület SDK-beli definíciója az alábbi: 

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

A következő értesítéseket küldi a program az alkalmazásnak, és némelyikük igényelheti az alkalmazás részvételét: 

* **`WIPE_USER_DATA` értesítés**: Ezt az értesítést a rendszer egy `MAMUserNotification` osztályban küldi el. Az értesítés érkezésekor az alkalmazásnak a `MAMUserNotification`. Az értesítést jelenleg az Intune szolgáltatás regisztrációjának törlésekor küldi a program. A regisztrációs folyamat során általában sor kerül a felhasználó elsődleges nevének megadására. Ha regisztrál ehhez az értesítéshez, az alkalmazásnak ellenőriznie kell, hogy az összes felhasználói adat törölve lett-e. Ha nem regisztrál, az alapértelmezett szelektív törlési viselkedés érvényesül. 

* **`WIPE_USER_AUXILIARY_DATA` értesítés**: Az alkalmazások akkor regisztrálhatnak erre az értesítésre, ha szeretnék, hogy az Intune App SDK végrehajtsa az alapértelmezett törlést, de bizonyos kiegészítő adatokat is törölni kívánnak.  

* **`REFRESH_POLICY` értesítés**: Ezt az értesítést a MAMNotification további adatok nélkül küldi. Az értesítés fogadásakor a gyorsítótárazott házirendet többé már nem kell érvénytelenítettnek tekinteni, ezért ellenőrizni kell, hogy mi a házirend. Ezt általában az SDK kezeli, azonban az alkalmazás kell kezelje, ha a házirend valamilyen állandó módon használt. 

## Függőben lévő leképezések és metódusok 

A MAM belépési pontok egyikéből való származtatás után a szokásos módon használhatja a környezetet tevékenységek indításához, a hozzá tartozó `PackageManager`használatához és így tovább.  A  `PendingIntents` kivételt képez ezen szabály alól. Az ilyen osztályok hívásakor módosítani kell az osztály nevét. A `PendingIntent.get*` használata helyett például a `MAMPendingIntents.get*` használandó. 

Bizonyos esetekben az androidos osztályban rendelkezésre álló metódus végsőként van megjelölve a helyettesítő MAM-osztályban. Ebben az esetben a helyettesítő MAM-osztály egy hasonlóan elnevezett metódust biztosít (általában a „MAM” utótaggal) amelyet felül kell írni. Így például a `ContentProvider.query`felülírása helyett a `MAMContentProvider.queryMAM`. A Java-fordítónak érvényesítenie kell a végső korlátozásokat az eredeti metódus véletlen felülbírálásának elkerülése érdekében az egyenértékű MAM-metódus helyett. 

# Biztonságimásolat-adatok védelme 

Az Android Marshmallow (API 23) esetében az Android két módszert kínál az alkalmazásoknak az adataik biztonsági mentésére. Ezek a lehetőségek alkalmazása rendelkezésére állnak, és különböző lépéseket igényelnek a MAM-adatvédelem megfelelő alkalmazásának biztosításához. Az alábbi táblázatban a megfelelő adatvédelmi működéshez szükséges megfelelő műveletek gyors áttekintését tekintheti meg.  További információ: [Útmutató androidos fejlesztőknek az adatok biztonsági mentéséhez](http://developer.android.com/guide/topics/data/backup.html.). 

## Automatikus, teljes biztonsági mentés

Az Android M-től kezdődően az Android a cél API-tól független teljes biztonsági mentési funkciókat kínál az alkalmazásoknak Android M-alapú eszközökön. Amennyiben az `android:allowBackup` attribútum értéke nem hamis, az alkalmazások teljes, szűretlen biztonsági mentéseket kapnak alkalmazásaikról. Ez adatszivárgási kockázatot jelenthet, ezért az SDK az alábbi táblázatban leírt módosításokat követeli meg az adatvédelem alkalmazásának biztosítása érdekében.  Fontos, hogy az ügyfél adatainak védelméhez megfelelően kövesse az alábbi útmutatást.  Ha az `android:allowBackup=false` beállítást adja meg, alkalmazását az operációs rendszer soha nem helyezi várólistára a biztonsági mentésekhez, és nincs több teendő a MAM-hoz, mivel nem készül biztonsági mentés.
 
 ## „kulcs/érték” biztonsági mentések

Ez a beállítás minden API esetén elérhető, és a `BackupAgent` , illetve a `BackupAgentHelper`. 

### A BackupAgentHelper használata

`BackupAgentHelper` megvalósítása jóval egyszerűbb, mint a `BackupAgent` osztályé, mind a natív androidos funkciókat, mind a MAM-integrációt tekintve. `BackupAgentHelper` lehetővé teszi, hogy a fejlesztő teljes fájlokat és közös beállításokat regisztráljon egy `FileBackupHelper` vagy egy `SharedPreferencesBackupHelper` osztályban, amelyeket a rendszer ezt követően létrehozáskor hozzáad a `BackupAgentHelper` osztályhoz. 

### A BackupAgent használata

`BackupAgent` segítségével jóval egyértelműbben adható meg, hogy mely adatokról készüljön biztonsági mentés. Azonban ezen beállítások használata esetén nem lehet kihasználni a biztonsági mentési Android-keretrendszer lehetőségeit.  Mivel a megvalósítás nagyrészt a fejlesztő felelőssége, több lépésre van szükség a megfelelő adatvédelem biztosításához a MAM-ból. Azáltal, hogy a munka nagyobb része a fejlesztőre hárul, itt a MAM-integráció nagyobb jelentőséggel bír. 

#### Az alkalmazás nem rendelkezik biztonságimásolat-készítő ügynökkel
  
A fejlesztő lehetőségei az `Android:allowbBackup =true`:

##### Teljes biztonságimásolat-készítés konfigurációs fájl alapján: 

Adjon meg egy erőforrást a `com.microsoft.intune.mam.FullBackupContent` metaadat-kódcímke alatt a jegyzékfájlban. példa:
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Adja hozzá a következő attribútumot az `<application>` címkében: `android:fullBackupContent="@xml/my_scheme"`, ahol a `my_scheme` az alkalmazásbeli XML-erőforrás. 

##### Teljes biztonságimásolat-készítés kizárások nélkül 

Adjon meg egy címkét a jegyzékfájlban, például: `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
Adja hozzá a következő attribútumot az `<application>` címkében: `android:fullBackupContent="true"`.

#### Az alkalmazás rendelkezik biztonságimásolat-készítő ügynökkel

Kövesse a fenti `BackupAgent` , illetve a `BackupAgentHelper` szakaszok ajánlásait 

Fontolja meg az áttérést a `MAMDefaultFullBackupAgent`használatára, amely az Android M esetében egyszerű biztonsági mentést tesz lehetővé. 

### A biztonsági mentés előtti teendők

Mielőtt megkezdené a biztonsági mentést, ellenőrizze, hogy a menteni tervezett fájlokról vagy adatpufferekről valóban engedélyezett-e biztonsági mentést készíteni. Ennek meghatározásához a mellékelt `isBackupAllowed` függvényt használhatja a `MAMFileProtectionManager` , illetve a `MAMDataProtectionManager` esetében. Ha a fájlok vagy a puffer biztonsági mentése nem engedélyezett, ne próbálja továbbra is azt a biztonsági mentésben alkalmazni.

Ha a biztonsági mentés során egy ponton biztonsági mentést szeretne készíteni az 1. lépésben ellenőrzött fájlok identitásáról, a `backupMAMFileIdentity(BackupDataOutput data, File … files)` eszközt azon fájlokkal kell meghívnia, amelyekből adatokat szeretne kinyerni. Ez a művelet automatikusan új biztonsági mentési entitásokat hoz létre, és a `BackupDataOutput` kimenetre írja azokat. Ezeket az entitásokat automatikusan felhasználja a program a visszaállítás során. 

## Az Azure Directory Authentication (ADAL) konfigurálása (nem kötelező)  

Az SDK a hitelesítési és feltételes indítási forgatókönyvekhez az ADAL-ra támaszkodik, amely megköveteli, hogy az alkalmazások bizonyos Azure Active Directory-beállításokkal rendelkezzenek. A konfigurációs értékeket az SDK az `AndroidManifest` metaadatain keresztül közli. Az alkalmazás konfigurálásához és a megfelelő hitelesítés engedélyezéséhez adja hozzá a következőket az `AndroidManifest`. Ezen konfigurációk némelyike csak akkor szükséges, ha az alkalmazás az ADAL-t hitelesítéshez használja. Ebben az esetben szüksége lesz az adott értékekre, amelyek segítségével az alkalmazás az AAD-ben regisztrálja magát. Ez annak biztosítása érdekében történik, hogy rendszer nem fogja kétszer kérni a felhasználó hitelesítését, ugyanis az AAD két különböző regisztrációs értéket ismer fel: egyet az alkalmazásból, egyet pedig az SDK-ból. 

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

A GUID-azonosítóknak nem kell kezdő vagy záró kapcsos zárójelet tartalmazniuk.

### Általános ADAL-konfigurációk 

Az alábbiak a fenti értékek általános beállításai. 

#### Az alkalmazás nem integrálja az ADAL-t

* A szolgáltatót arra a kívánt környezetre kell beállítani, ahol AAD-fiókok vannak konfigurálva.

* A SkipBroker igaz értékű kell, hogy legyen.

#### Az alkalmazás integrálja az ADAL-t

* A szolgáltatót arra a kívánt környezetre kell beállítani, ahol AAD-fiókok vannak konfigurálva.

* Ügyfél-azonosítóként az alkalmazás ügyfél-azonosítóját kell beállítani.

* `NonBrokerRedirectURI` értékeként az alkalmazáshoz tartozó érvényes átirányítási URI-t kell beállítani.
    * Or `urn:ietf:wg:oauth:2.0:oob` értéket kell beállítani érvényes AAD átirányítási URI-ként.

* A SkipBroker értékét hamisra kell állítani (vagy el kell hagyni)

* Az AAD-t a közvetítő átirányítási URI-jának elfogadására kell konfigurálni.

#### Az alkalmazás integrálja az ADAL-t, de nem támogatja az AAD-hitelesítő alkalmazást.

* A szolgáltatót arra a kívánt környezetre kell beállítani, ahol AAD-fiókok vannak konfigurálva.

* Ügyfél-azonosítóként az alkalmazás ügyfél-azonosítóját kell beállítani.

* `NonBrokerRedirectURI` értékeként az alkalmazáshoz tartozó érvényes átirányítási URI-t kell beállítani.

    * Or `urn:ietf:wg:oauth:2.0:oob` értéket kell beállítani érvényes AAD átirányítási URI-ként.

## Az SDK naplózásának engedélyezése 

A naplózás a `java.util.logging` keretrendszeren keresztül zajlik. A naplók fogadásához állítsa be a globális naplózást a [Java technikai útmutató](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). Az alkalmazástól függően általában az `App.onCreate` a legjobb hely a naplózás indításához. Vegye figyelembe, hogy naplóüzenetek osztálynév szerinti kulccsal vannak ellátva, amely rejtjelzett lehet.

# Ismert platformkorlátozások 

## Fájlok méretkorlátai 

Az Android rendszerben a Dalvik végrehajtható fájlformátumra vonatkozó korlátozások problémává válhatnak ProGuard nélkül futó nagyméretű kódbázis esetében. Konkrétan a következő korlátozások fordulhatnak elő: 

* A mezőkre vonatkozó 65 KB-os korlát.

* A metódusokra vonatkozó 65 KB-os korlát.

Nagyszámú projekt belefoglalásakor minden android:package megkapja az R egy példányát, ami jelentősen növeli a mezők számát a kódtárak hozzáadása során. A következők javaslatok segíthetnek, ezen korlátozás hatásának mérséklésében:
 
* Lehetőség szerint minden kódtárprojektnek azonos android:package csomagot kell használnia. Ez nem fog szórványos hibákat jelenteni a működéskor, mivel ez a probléma pusztán a felépítés során jelentkezik.   Emellett az Android SDK újabb verziói előre feldolgozzák a DEX-fájlokat a redundancia csökkentése érdekében. Ez még tovább csökkenti a mezőktől való távolságot.

* Használja az elérhető legújabb Android SDK buildet.

* Távolítsa el a felesleges és használaton kívüli kódtárakat (pl. `android.support.v4`)

## Házirend-kényszerítési korlátozások

**Képernyőfelvétel**: Az SDK nem tud új képernyőfelvétel-beállítási értéket kikényszeríteni azon tevékenységeknél, amelyeknél már lefutott az Activity.onCreate. Ez olyan időszakot eredményezhet, amikor az alkalmazás a képernyőfelvételek letiltására lett konfigurálva, de továbbra is lehet képernyőfelvételt készíteni.

**Tartalomfeloldók használata*: Az átviteli vagy a fogadási házirend részben vagy teljesen blokkolhatja a tartalomfeloldók használatát más alkalmazások tartalomszolgáltatójának eléréséhez. Ennek következtében a ContentResolver metódusok null vagy hibaértéket fognak visszaadni (például az `openOutputStream` a `FileNotFoundException` kivételhibát fogja okozni, ha blokkolva van). Az alkalmazás a következő hívással állapíthatja meg, hogy a tartalomfeloldón keresztüli adatírás sikertelenségét házirend okozta (vagy hogy egy házirend ilyen hibát okozna):

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Exportált szolgáltatások**: Az Intune App SDK által tartalmazott `AndroidManifest.xml` fájl tartalmazza a `MAMNotificationReceiverService`szolgáltatást, amelynek exportált szolgáltatásnak kell lennie, hogy lehetővé tegye a vállalati portálnak az értesítések küldését egy felkészített alkalmazásnak. A szolgáltatás ellenőrzi a hívót annak ellenőrzéséhez, hogy csak a vállalati portál számára engedélyezett-e az értesítések küldése. 

# Ajánlott gyakorlati tanácsok Androidban 

Az Intune SDK fenntartja az Android API által biztosított szerződést, bár a házirendi beállítások miatt gyakrabban léphetnek fel hibaállapotok. Az alábbi androidos gyakorlati tanácsok csökkentik a hibák valószínűségét: 

* Azon androidos SDK-függvények, amelyek null értékkel térhetnek vissza, nagyobb valószínűséggel lesznek null értékűek.  A problémák minimalizálása érdekében biztosítsa, hogy a megfelelő helyeken legyenek null-ellenőrzések.

* Az SDK API-kon keresztül ellenőrizni kell azokat a funkciókat, amelyek ellenőrizhetők.

* Minden származtatott függvénynek meg kell hívnia a szülőosztálybeli verzióját.

* Kerülje az API-k nem egyértelmű módon való használatát. Így például az `Activity.startActivityForResult/onActivityResult` használata a requestCode ellenőrzése nélkül működésbeli furcsaságokat idézhet elő.



<!--HONumber=Jun16_HO4-->


