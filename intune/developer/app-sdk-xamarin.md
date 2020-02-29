---
title: Microsoft Intune App SDK Xamarin Bindings
description: Az Intune App SDK Xamarin Bindings lehetővé teszik az Intune alkalmazásvédelmi szabályzatok használatát a Xamarinnal készített iOS- és Android-alkalmazásokban.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183cc5ed233de4a3285cf5cfd3290aead9c1de72
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181908"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin Bindings

> [!NOTE]
> Először célszerű elolvasnia az [Intune App SDK használatának első lépései](app-sdk-get-started.md) című cikket, amely bemutatja az integráció előkészítését a támogatott platformokon.

## <a name="overview"></a>Házirend
Az [Intune App SDK Xamarin Bindings](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) lehetővé teszi az [Intune alkalmazásvédelmi szabályzatok](../apps/app-protection-policy.md) használatát a Xamarinnal készített iOS- és Android-alkalmazásokban. A kötések lehetővé teszik a fejlesztők számára, hogy Intune alkalmazásvédelmi funkciókat építsenek be a Xamarin-alapú alkalmazásaikba.

A Microsoft Intune App SDK Xamarin Bindings lehetővé teszi, hogy Intune alkalmazásvédelmi szabályzatokat (vagy más néven alkalmazás- vagy MAM-szabályzatokat) építsen be a Xamarinnal fejlesztett alkalmazásokba. A MAM-kompatibilis alkalmazás az, amelyik integrálva van az Intune App SDK-val. Mindez lehetővé teszi a rendszergazdáknak, hogy alkalmazásvédelmi szabályzatokat telepítsenek a mobilalkalmazásra vonatkozóan, ha az Intune aktívan felügyeli az alkalmazást.

## <a name="whats-supported"></a>Támogatott források és műveletek

### <a name="developer-machines"></a>Fejlesztői gépek
* Windows (Visual Studio version 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>Mobilalkalmazás-platformok
* Android:
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune mobilalkalmazás-kezelési helyzetek

* Intune APP-WE (eszközregisztráció nélkül)
* Intune MDM által regisztrált eszközök
* Külső EMM által regisztrált eszközök

Az Intune App SDK Xamarin Bindingsszal létrehozott Xamarin-alkalmazásokra mostantól alkalmazhatók az Intune alkalmazásvédelmi szabályzatai az Intune mobileszköz-felügyeletében (MDM) regisztrált eszközökön és a nem regisztrált eszközökön is.

## <a name="prerequisites"></a>Előfeltételek

A [licencfeltételek](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf) áttekintése. Nyomtassa ki és őrizze meg a licencfeltételeket. Az Intune App SDK Xamarin Bindings letöltésével és használatával elfogadja licencfeltételeket. Amennyiben a feltételeket nem fogadja el, ne használja a szoftvert.

Az Intune SDK a [hitelesítésre](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) és a feltételes indítási forgatókönyvekre támaszkodik [Active Directory-hitelesítési tárre (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) , amelyeknek az alkalmazásoknak a [Azure Active Directoryval](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)való konfigurálására van szükségük. 

Ha az alkalmazás már konfigurálva van a ADAL vagy a MSAL használatára, és rendelkezik a saját egyéni ügyfél-azonosítójával a hitelesítéshez a Azure Active Directory használatával, győződjön meg arról, hogy a Xamarin-alkalmazás engedélyeit az Intune Mobile Application Management (MAM) szolgáltatáshoz adja meg majd. Az útmutató az Intune[app Protection szolgáltatáshoz](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)című szakaszában található útmutatást követve megtudhatja, [Hogyan](app-sdk-get-started.md)érheti el az alkalmazást az Intune-hoz.

## <a name="security-considerations"></a>Biztonsági megfontolások

A lehetséges hamisítási, információfelfedési és a jogok kiterjesztéséből adódó támadások megelőzése érdekében:

* Győződjön meg arról, hogy a Xamarin-alkalmazások fejlesztése biztonságos munkaállomáson történik.
* Győződjön meg arról, hogy a kötések érvényes Microsoft-forrásból származnak:
  * [MS Intune app SDK NuGet-profil](https://www.nuget.org/profiles/msintuneappsdk)
  * [Intune app SDK Xamarin GitHub-adattár](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* Konfigurálja a NuGet konfigurációját úgy, hogy az aláírt, nem módosított NuGet-csomagokat Bízzon meg a projektben.
További információ: [aláírt csomagok telepítése](https://docs.microsoft.com/nuget/consume-packages/installing-signed-packages) .
* Gondoskodjon a Xamarin alkalmazást tartalmazó kimeneti könyvtár védelméről. Fontolja meg a kimeneti oldal számára egy felhasználói szintű könyvtár használatát.


## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Az Intune alkalmazásvédelmi szabályzatainak engedélyezése az iOS-mobilalkalmazásban
1. Adja hozzá Xamarin.iOS-projektjéhez a [Microsoft.Intune.MAM.Xamarin.iOS NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS).
2. Kövesse az Intune App SDK iOS-mobilalkalmazásokba való integrálásához szükséges általános lépéseket. Kezdhet az [iOS-hez készült Intune App SDK – fejlesztői útmutató](app-sdk-ios.md#build-the-sdk-into-your-mobile-app) című témakör integrálási útmutatásának 3. lépésével. Az IntuneMAMConfigurator futtatásáról szóló szakasz utolsó lépését átugorhatja, mivel az eszköz része a Microsoft.Intune.MAM.Xamarin.iOS csomagnak, és a build időpontjában automatikusan futtatva lesz.
    **Fontos**: A kulcslánc megosztásának alkalmazások számára való engedélyezése kissé eltérő a Visual Studióban és az Xcode-ban. Nyissa meg az alkalmazás jogosultságokat tartalmazó plist-fájlját, és győződjön meg arról, hogy az „Enable Keychain” („Kulcslánc engedélyezése”) lehetőség engedélyezve van, és hogy ebben a szakaszban a megfelelő kulcslánc-megosztási csoportok szerepelnek. Ezután győződjön meg arról, hogy a projekt „iOS Bundle Signing” („iOS-kötegaláírási”) beállításai között a konfigurációk és platformok összes megfelelő kombinációjához meg van adva a jogosultságokat tartalmazó plist-fájl a „Custom Entitlements” („Egyéni jogosultságok”) mezőben.
3. Miután hozzáadta a kötéseket, és megfelelően konfigurálta az alkalmazást, az alkalmazás megkezdheti az Intune SDK API-jának használatát. Ehhez a következő névteret kell hozzáadnia:

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. Az alkalmazásvédelmi szabályzatok fogadásának megkezdéséhez az alkalmazást regisztrálni kell az Intune MAM szolgáltatásban. Ha az alkalmazás nem az [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) vagy a [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) tárral hitelesíti a felhasználókat, Ön pedig ezt az Intune SDK-val szeretné kezelni, az alkalmazásnak át kell adnia a felhasználó egyszerű felhasználónevét az IntuneMAMEnrollmentManager LoginAndEnrollAccount metódusának:

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      Az alkalmazások üres értékűek is lehetnek, ha a felhasználó egyszerű felhasználóneve ismeretlen a hívás idején. Ebben az esetben a rendszer az e-mail-címet és a jelszót kéri a felhasználóktól.
      
      Ha az alkalmazás már az ADA vagy az MSAL segítségével hitelesíti a felhasználókat, egyszeri bejelentkezést (SSO) konfigurálhat az alkalmazás és az Intune SDK között. Először felül kell bírálnia az Intune SDK által az alkalmazáshoz használt alapértelmezett HRE-beállításokat. Ezt az alkalmazás info. plist fájljának IntuneMAMSettings-szótárán keresztül teheti meg, az [iOS-hez készült Intune app SDK Fejlesztői útmutatójában](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)leírtak szerint, vagy megteheti a kódban a INTUNEMAMSETTINGS osztály HRE felülbírálás tulajdonságai között. Az Info.plist fájlt alkalmazó módszer használata ajánlott az olyan alkalmazások esetében, melyek ADAL-beállításai statikusak, míg a felülbírálási tulajdonságok használata ajánlott olyan alkalmazások esetében, melyek futásidőben határozzák meg ezeket az értékeket. Az SSO-beállítások konfigurálása után az alkalmazásnak a sikeresen hitelesítést követően át kell adnia a felhasználó egyszerű felhasználónevét az IntuneMAMEnrollmentManager RegisterAndEnrollAccount metódusának:

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      Az alkalmazások meghatározhatják a regisztrációs kísérleteke eredményeit az EnrollmentRequestWithStatus metódus az IntuneMAMEnrollmentDelegate egyik alosztályában való alkalmazásával, valamint az IntuneMAMEnrollmentManager Delegate tulajdonságának az osztály egyik példányához való beállításával. 

      Sikeres regisztráció esetén az alkalmazások meghatározhatják a regisztrált fiók egyszerű felhasználónevét a következő tulajdonság lekérdezésével (amennyiben azt addig nem ismerték): 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>Példák az alkalmazásokra
A MAM-funkciókat kiemelő Xamarin. az iOS-alkalmazások a [githubon](https://github.com/msintuneappsdk/sample-intune-xamarin-ios)érhetők el.

> [!NOTE] 
> Az iOS/iPadOS esetében nincs remapper. A Xamarin.Forms-alkalmazásokba való integrálásnak ugyanúgy kell történnie, mint általában a Xamarin.iOS-projektek esetén. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Az Intune alkalmazásvédelmi szabályzatainak engedélyezése Androidos mobilalkalmazásban
1. Adja hozzá Xamarin.Android-projektjéhez a [Microsoft.Intune.MAM.Xamarin.Android NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android).
    1. A Xamarin. Forms alkalmazáshoz adja hozzá a [Microsoft. Intune. Mam. remapper. Tasks NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) a Xamarin. Android projekthez is. 
2. További részletekért tekintse meg az [Intune app SDK](app-sdk-android.md) Android Mobile-alkalmazásba való integrálásához szükséges általános lépéseket.

### <a name="xamarinandroid-integration"></a>Xamarin.Android-integráció

Az Intune app SDK integrálásának teljes áttekintése a [Microsoft Intune app SDK for Android fejlesztői útmutatójában](app-sdk-android.md)található. Az útmutatóban leírtak és az Intune app SDK integrálása a Xamarin alkalmazással az alábbi részekben a Java-ban fejlesztett natív Android-alkalmazás implementációja és a alkalmazásban fejlesztett Xamarin- C#alkalmazások közötti különbségeket érdemes kiemelni. Ezeket a fejezeteket kiegészítőként kell kezelni, és nem helyettesíthetik az útmutató teljes egészében történő beolvasását.

#### <a name="remapper"></a>Remapper
A 1.4428.1-kiadástól kezdve a `Microsoft.Intune.MAM.Remapper` csomag hozzáadható egy Xamarin. Android-alkalmazáshoz, mint a MAM-osztály, a metódus és a rendszerszolgáltatások cseréjének elvégzéséhez használható [Build-eszközként](app-sdk-android.md#build-tooling) . Ha a remappert is tartalmazza, a rendszer automatikusan elvégzi az átnevezett módszerek és a MAM-alkalmazási csoportok MAM-helyettesítési részeit az alkalmazás létrehozásakor.

Ha ki szeretne zárni egy osztályt a MAM-ification a remapper használatával, a következő tulajdonság hozzáadható a projektek `.csproj` fájlhoz.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> A remapper jelenleg megakadályozza a hibakeresést a Xamarin. Android-alkalmazásokban. A manuális integráció ajánlott az alkalmazás hibakereséséhez.

#### <a name="renamed-methods"></a>[Átnevezett metódusok](app-sdk-android.md#renamed-methods)
Sok esetben az androidos osztályban rendelkezésre álló metódus végsőként van megjelölve a helyettesítő MAM-osztályban. Ebben az esetben a helyettesítő MAM-osztály egy hasonlóan elnevezett metódust biztosít (a `MAM` utótaggal), amelyet felül kell írni. Így például a `MAMActivity` származtatásakor az `OnCreate()` felülírása, illetve a `base.OnCreate()` metódus hívása helyett az `Activity` tevékenységnek felül kell írnia az `OnMAMCreate()` metódust, és meg kell hívnia a `base.OnMAMCreate()` metódust.

#### <a name="mam-application"></a>[MAM-alkalmazás](app-sdk-android.md#mamapplication)
Az alkalmazásnak meg kell határoznia egy `Android.App.Application` osztályt. Ha manuálisan integrálja a MAM-t, a `MAMApplication`tól örökölni kell. Ügyeljen rá, hogy az alosztály megfelelően jelölve legyen a `[Application]` attribútummal, és felülbírálja a `(IntPtr, JniHandleOwnership)` konstruktort.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> A MAM Xamarin-kötésekkel kapcsolatos probléma miatt az alkalmazás hibakeresési módban való üzembe helyezésekor összeomlást eredményezhet. Megkerülő megoldásként a `Debuggable=false` attribútumot hozzá kell adni a `Application` osztályhoz, és a `android:debuggable="true"` jelzőt el kell távolítani a jegyzékfájlból, ha az manuálisan be lett állítva.

#### <a name="enable-features-that-require-app-participation"></a>[Alkalmazások részvételét igénylő szolgáltatások engedélyezése](app-sdk-android.md#enable-features-that-require-app-participation)
Példa: annak megállapítása, hogy az alkalmazáshoz szükséges-e PIN-kód

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

Példa: az elsődleges Intune-felhasználó meghatározása

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

Példa: annak megállapítása, hogy engedélyezve van-e az eszközre vagy a felhőbeli tárhelyre való mentés

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdk"></a>[Regisztráció az SDK értesítéseire](app-sdk-android.md#register-for-notifications-from-the-sdk)
Az alkalmazásnak regisztrálnia kell az SDK által küldött értesítésekhez egy `MAMNotificationReceiver` létrehozásával és a `MAMNotificationReceiverRegistry`val való regisztrálásával. Ezt úgy teheti meg, hogy megadja a fogadó és a kívánt értesítés típusát `App.OnMAMCreate`ban, az alábbi példában látható módon:

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-manager"></a>[MAM beléptetési kezelő](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms-integráció

`Xamarin.Forms`-alkalmazások esetén a `Microsoft.Intune.MAM.Remapper`-csomag az `MAM` osztályok a gyakran használt `Xamarin.Forms` osztályok osztály-hierarchiába való beírásával automatikusan végrehajtja a MAM-osztály cseréjét. 

> [!NOTE]
> A Xamarin. Forms integrációt a fentiekben ismertetett Xamarin. Android-integráció mellett kell elvégezni. A remapper a Xamarin. Forms alkalmazások esetében eltérően viselkedik, ezért a kézi MAM-cseréket továbbra is el kell végezni.

Miután hozzáadta az újraleképezést a projekthez, el kell végeznie a MAM-beli egyenértékű visszahelyezést. Például a `FormsAppCompatActivity` és a `FormsApplicationActivity` továbbra is használható az alkalmazásban, ha a felülbírálások `OnCreate` és `OnResume` a MAM-ekvivalens `OnMAMCreate` és `OnMAMResume`.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

Ha a cserék nem történnek, akkor a következő fordítási hibák merülhetnek fel, amíg el nem végzi a cseréket:
* [Fordítói hiba CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Ezt a hibát általában a következő formában tekinti ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Ennek az az oka, hogy ha a remapper módosítja a Xamarin osztályok öröklését, a rendszer bizonyos függvényeket fog `sealed`, és egy új MAM-változatot ad hozzá a felülbíráláshoz.
* [Fordítóprogram-hiba CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Ez a hiba általában a következő formában látható ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Ha a remapper megváltoztatja a Xamarin egyes osztályainak öröklését, a rendszer bizonyos tag-függvényeket `public`re fog módosítani. Ha felülbírálja ezeket a függvényeket, módosítania kell a felülbírálások hozzáférési módosítóit, hogy `public` is legyenek.

> [!NOTE]
> A remapper újra ír egy függőséget, amelyet a Visual Studio az IntelliSense automatikus kiegészítéséhez használ. Ezért előfordulhat, hogy újra kell töltenie és újra létre kell hoznia a projektet, ha a remapper hozzá van adva az IntelliSensehoz a módosítások megfelelő felismeréséhez.

#### <a name="troubleshooting"></a>Hibaelhárítás
* Ha egy üres, fehér képernyő jelenik meg az alkalmazás indításakor, akkor előfordulhat, hogy a fő szálon végre kell hajtania a navigációs hívásokat.
* Az Intune SDK-Xamarin kötései nem támogatják a többplatformos keretrendszert használó alkalmazásokat, például a MvvmCross-et a MvvmCross és az Intune MAM-osztályok közötti ütközések miatt. Előfordulhat, hogy néhány ügyfél sikerrel járt együtt az alkalmazások egyszerű Xamarin. Forms-ra való áthelyezése után, és nem biztosítunk explicit útmutatást vagy beépülő modult az MvvmCross használó alkalmazás-fejlesztőknek.

### <a name="company-portal-app"></a>Vállalati portál alkalmazás
Az Intune SDK-Xamarin kötései a [céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android-alkalmazás jelenlétét használják az eszközön az alkalmazás-védelmi házirendek engedélyezéséhez. A Céges portál az Intune szolgáltatástól kéri le az alkalmazásvédelmi szabályzatokat. Az alkalmazás az inicializáláskor betölti a Céges portálról a szabályzatot és a betartatásához szükséges kódot. A felhasználónak nem kell bejelentkeznie.

> [!NOTE]
> Ha a Céges portál alkalmazás nem az **Android** -eszközön található, az Intune által felügyelt alkalmazás ugyanúgy viselkedik, mint egy normál alkalmazás, amely nem támogatja az Intune app Protection-házirendeket.

Az eszközregisztráció nélküli alkalmazásvédelem esetében a felhasználónak _**nem**_ kell regisztrálnia az eszközt a Céges portál alkalmazással.

### <a name="sample-applications"></a>Példák az alkalmazásokra
A Xamarin. Android-és Xamarin. Forms-alkalmazások MAM-funkcióit kiemelő példák a [githubon](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps)érhetők el.

## <a name="support"></a>Támogatás
Ha a szervezete egy meglévő Intune-ügyfél, forduljon a Microsoft ügyfélszolgálati képviselőjéhez, és nyisson meg egy támogatási jegyet, és hozzon létre egy problémát [a GitHub-problémák oldalon](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). A lehető leghamarabb segíteni fogunk. 
