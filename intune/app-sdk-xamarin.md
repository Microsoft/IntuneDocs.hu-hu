---
title: Microsoft Intune App SDK Xamarin Bindings
description: Az Intune App SDK Xamarin Bindings lehetővé teszik az Intune alkalmazásvédelmi szabályzatok használatát a Xamarinnal készített iOS- és Android-alkalmazásokban.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd2a2b73c5dc7b792e5766c3fded152eabc1f53b
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69582910"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin Bindings

> [!NOTE]
> Először célszerű elolvasnia az [Intune App SDK használatának első lépései](app-sdk-get-started.md) című cikket, amely bemutatja az integráció előkészítését a támogatott platformokon.

## <a name="overview"></a>Áttekintés
Az [Intune App SDK Xamarin Bindings](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) lehetővé teszi az [Intune alkalmazásvédelmi szabályzatok](app-protection-policy.md) használatát a Xamarinnal készített iOS- és Android-alkalmazásokban. A kötések lehetővé teszik a fejlesztők számára, hogy Intune alkalmazásvédelmi funkciókat építsenek be a Xamarin-alapú alkalmazásaikba.

A Microsoft Intune App SDK Xamarin Bindings lehetővé teszi, hogy Intune alkalmazásvédelmi szabályzatokat (vagy más néven alkalmazás- vagy MAM-szabályzatokat) építsen be a Xamarinnal fejlesztett alkalmazásokba. A MAM-kompatibilis alkalmazás az, amelyik integrálva van az Intune App SDK-val. Mindez lehetővé teszi a rendszergazdáknak, hogy alkalmazásvédelmi szabályzatokat telepítsenek a mobilalkalmazásra vonatkozóan, ha az Intune aktívan felügyeli az alkalmazást.

## <a name="whats-supported"></a>Támogatott források és műveletek

### <a name="developer-machines"></a>Fejlesztői gépek
* Windows (Visual Studio version 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>Mobilalkalmazás-platformok
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune mobilalkalmazás-kezelési helyzetek

* Intune APP-WE (eszközregisztráció nélkül)
* Intune MDM által regisztrált eszközök
* Külső EMM által regisztrált eszközök

Az Intune App SDK Xamarin Bindingsszal létrehozott Xamarin-alkalmazásokra mostantól alkalmazhatók az Intune alkalmazásvédelmi szabályzatai az Intune mobileszköz-felügyeletében (MDM) regisztrált eszközökön és a nem regisztrált eszközökön is.

## <a name="prerequisites"></a>Előfeltételek

A [licencfeltételek](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf) áttekintése. Nyomtassa ki és őrizze meg a licencfeltételeket. Az Intune App SDK Xamarin Bindings letöltésével és használatával elfogadja licencfeltételeket. Amennyiben a feltételeket nem fogadja el, ne használja a szoftvert.

Az SDK a [hitelesítési](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) és feltételes indítási forgatókönyvek [Active Directory-hitelesítési tárra (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) támaszkodik, amelyeknek az alkalmazásoknak a [Azure Active Directoryval](https://azure.microsoft.com/documentation/articles/active-directory-whatis/)való konfigurálására van szükségük. 

Ha az alkalmazás már konfigurálva van a ADAL vagy a MSAL használatára, és rendelkezik a saját egyéni ügyfél-azonosítójával a hitelesítéshez a Azure Active Directory használatával, győződjön meg arról, hogy a Xamarin-alkalmazás engedélyeit az Intune Mobile Application Management (MAM) szolgáltatáshoz adja meg majd. Az útmutató az Intune app Protection szolgáltatáshoz című szakaszában található útmutatást követve megtudhatja, [Hogyan](app-sdk-get-started.md)érheti el az[alkalmazást az Intune-hoz](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional).

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Az Intune alkalmazásvédelmi szabályzatainak engedélyezése az iOS-mobilalkalmazásban
1. Adja hozzá Xamarin.iOS-projektjéhez a [Microsoft.Intune.MAM.Xamarin.iOS NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS).
2. Kövesse az Intune App SDK iOS-mobilalkalmazásokba való integrálásához szükséges általános lépéseket. Kezdhet az [iOS-hez készült Intune App SDK – fejlesztői útmutató](app-sdk-ios.md#build-the-sdk-into-your-mobile-app) című témakör integrálási útmutatásának 3. lépésével. Az IntuneMAMConfigurator futtatásáról szóló szakasz utolsó lépését átugorhatja, mivel az eszköz része a Microsoft.Intune.MAM.Xamarin.iOS csomagnak, és a build időpontjában automatikusan futtatva lesz.
    **Fontos**: Egy alkalmazás kulcstartó-megosztásának engedélyezése némileg eltér a Visual Studióban a Xcode. Nyissa meg az alkalmazás jogosultságokat tartalmazó plist-fájlját, és győződjön meg arról, hogy az „Enable Keychain” („Kulcslánc engedélyezése”) lehetőség engedélyezve van, és hogy ebben a szakaszban a megfelelő kulcslánc-megosztási csoportok szerepelnek. Ezután győződjön meg arról, hogy a projekt „iOS Bundle Signing” („iOS-kötegaláírási”) beállításai között a konfigurációk és platformok összes megfelelő kombinációjához meg van adva a jogosultságokat tartalmazó plist-fájl a „Custom Entitlements” („Egyéni jogosultságok”) mezőben.
3. Miután hozzáadta a kötéseket, és megfelelően konfigurálta az alkalmazást, az alkalmazás megkezdheti az Intune SDK API-jának használatát. Ehhez a következő névteret kell hozzáadnia:

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. Az alkalmazásvédelmi szabályzatok fogadásának megkezdéséhez az alkalmazást regisztrálni kell az Intune MAM szolgáltatásban. Ha az alkalmazás nem az [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) vagy a [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) tárral hitelesíti a felhasználókat, Ön pedig ezt az Intune SDK-val szeretné kezelni, az alkalmazásnak át kell adnia a felhasználó egyszerű felhasználónevét az IntuneMAMEnrollmentManager LoginAndEnrollAccount metódusának:

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      Az alkalmazások üres értékűek is lehetnek, ha a felhasználó egyszerű felhasználóneve ismeretlen a hívás idején. Ebben az esetben a rendszer az e-mail-címet és a jelszót kéri a felhasználóktól.
      
      Ha az alkalmazás már az ADA vagy az MSAL segítségével hitelesíti a felhasználókat, egyszeri bejelentkezést (SSO) konfigurálhat az alkalmazás és az Intune SDK között. Elsőként konfigurálnia kell az ADAL/MSAL szolgáltatást a tokenek az iOS-es Intune Xamarin-kötések által is használt ugyanazon kulcslánc-hozzáférési csoport használatára (com.microsoft.adalcache). A ADAL ezt a [AuthenticationContext iOSKeychainSecurityGroup tulajdonságának beállításával](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/iOS-Keychain-Access)teheti meg. A MSAL esetében [be kell állítania a PublicClientApplication iOSKeychainSecurityGroup tulajdonságát](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-iOS-specifics#enable-keychain-access). Ezután felül kell bírálnia az Intune SDK alapértelmezett AAD-beállításait az alkalmazáséival. Ezt az alkalmazás Info.plist fájljában található IntuneMAMSettings szótárban teheti meg az [iOS-hez készült Intune App SDK – fejlesztői útmutató](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) című témakörben leírtaknak megfelelően, vagy használhatja az IntuneMAMPolicyManager-példány AAD-felülbírálási tulajdonságait. Az Info.plist fájlt alkalmazó módszer használata ajánlott az olyan alkalmazások esetében, melyek ADAL-beállításai statikusak, míg a felülbírálási tulajdonságok használata ajánlott olyan alkalmazások esetében, melyek futásidőben határozzák meg ezeket az értékeket. Az SSO-beállítások konfigurálása után az alkalmazásnak a sikeresen hitelesítést követően át kell adnia a felhasználó egyszerű felhasználónevét az IntuneMAMEnrollmentManager RegisterAndEnrollAccount metódusának:

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      Az alkalmazások meghatározhatják a regisztrációs kísérleteke eredményeit az EnrollmentRequestWithStatus metódus az IntuneMAMEnrollmentDelegate egyik alosztályában való alkalmazásával, valamint az IntuneMAMEnrollmentManager Delegate tulajdonságának az osztály egyik példányához való beállításával. Erről példát a [Xamarin.iOS-mintaalkalmazásban](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) találhat.

      Sikeres regisztráció esetén az alkalmazások meghatározhatják a regisztrált fiók egyszerű felhasználónevét a következő tulajdonság lekérdezésével (amennyiben azt addig nem ismerték): 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      

> [!NOTE] 
> iOS rendszerre nincs remapper. A Xamarin.Forms-alkalmazásokba való integrálásnak ugyanúgy kell történnie, mint általában a Xamarin.iOS-projektek esetén. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Az Intune alkalmazásvédelmi szabályzatainak engedélyezése Androidos mobilalkalmazásban
1. Adja hozzá Xamarin.Android-projektjéhez a [Microsoft.Intune.MAM.Xamarin.Android NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android).
    1. A Xamarin. Forms alkalmazáshoz adja hozzá a [Microsoft. Intune. Mam. remapper. Tasks NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) a Xamarin. Android projekthez is. 
2. További részletekért tekintse meg az [Intune app SDK](app-sdk-android.md) Android Mobile-alkalmazásba való integrálásához szükséges általános lépéseket.

### <a name="xamarinandroid-integration"></a>Xamarin.Android-integráció

Az Intune app SDK integrálásának teljes áttekintése a [Microsoft Intune app SDK for Android fejlesztői útmutatójában](app-sdk-android.md)található. Az útmutatóban leírtak és az Intune app SDK integrálása a Xamarin alkalmazással az alábbi részekben a Java-ban fejlesztett natív Android-alkalmazás implementációja és a alkalmazásban fejlesztett Xamarin- C#alkalmazások közötti különbségeket érdemes kiemelni. Ezeket a fejezeteket kiegészítőként kell kezelni, és nem helyettesíthetik az útmutató teljes egészében történő beolvasását.

#### <a name="remapper"></a>Remapper
A 1.4428.1-kiadástól kezdve a `Microsoft.Intune.MAM.Remapper` csomag hozzáadható egy Xamarin. Android-alkalmazáshoz, amely a MAM-osztály, a metódus és a System Services-szolgáltatások kihelyezésére szolgáló [Build](app-sdk-android.md#build-tooling) -eszközként használható. Ha a remappert is tartalmazza, a rendszer automatikusan elvégzi az átnevezett módszerek és a MAM-alkalmazási csoportok MAM-helyettesítési részeit az alkalmazás létrehozásakor.

Ha ki szeretne zárni egy osztályt a MAM-ification a remapper használatával, a következő tulajdonság adható hozzá `.csproj` a projects-fájlhoz.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> Jelenleg a remapper hibája megakadályozza a hibakeresést a Xamarin. Android-alkalmazásokban. A manuális integráció ajánlott az alkalmazás hibakereséséhez, amíg a probléma nem oldódik meg.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Átnevezett metódusok](app-sdk-android.md#renamed-methods)
Sok esetben az androidos osztályban rendelkezésre álló metódus végsőként van megjelölve a helyettesítő MAM-osztályban. Ebben az esetben a helyettesítő MAM-osztály egy hasonlóan elnevezett metódust biztosít (a `MAM` utótaggal), amelyet felül kell írni. Így például a `MAMActivity` származtatásakor az `OnCreate()` felülírása, illetve a `base.OnCreate()` metódus hívása helyett az `Activity` tevékenységnek felül kell írnia az `OnMAMCreate()` metódust, és meg kell hívnia a `base.OnMAMCreate()` metódust.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM-alkalmazás](app-sdk-android.md#mamapplication)
Az alkalmazásnak meg kell `Android.App.Application` határoznia egy osztályt. Ha manuálisan integrálja a MAM-t, a `MAMApplication`-től örökölni kell. Ügyeljen rá, hogy az alosztály megfelelően jelölve legyen a `[Application]` attribútummal, és felülbírálja a `(IntPtr, JniHandleOwnership)` konstruktort.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> A MAM Xamarin-kötésekkel kapcsolatos probléma miatt az alkalmazás hibakeresési módban való üzembe helyezésekor összeomlást eredményezhet. Megkerülő megoldásként `Debuggable=false` az attribútumot hozzá kell adni `Application` az osztályhoz `android:debuggable="true"` , és a jelzőt el kell távolítani a jegyzékfájlból, ha az manuálisan be lett állítva.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Alkalmazások részvételét igénylő szolgáltatások engedélyezése](app-sdk-android.md#enable-features-that-require-app-participation)
Példa: Annak megállapítása, hogy szükséges-e PIN-kód az alkalmazáshoz

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

Példa: Az elsődleges Intune-felhasználó meghatározása

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

Példa: Annak megállapítása, hogy engedélyezett-e a Mentés eszközre vagy Felhőbeli tárhelyre

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Regisztráció az SDK értesítéseire](app-sdk-android.md#register-for-notifications-from-the-sdk)
Az alkalmazásnak regisztrálnia kell az SDK által küldött értesítésekhez `MAMNotificationReceiver` egy létrehozásával, és `MAMNotificationReceiverRegistry`regisztrálnia kell az-nal. Ez a fogadó és a kívánt `App.OnMAMCreate`értesítés típusának megadásával történik, az alábbi példában látható módon:

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

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[MAM beléptetési kezelő](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms-integráció

Az `Xamarin.Forms` alkalmazások esetében `Microsoft.Intune.MAM.Remapper` a csomag automatikusan `MAM` kicseréli a MAM-osztályokat, ha osztályokat szúr be `Xamarin.Forms` a gyakran használt osztályok osztály-hierarchiába. 

> [!NOTE]
> A Xamarin. Forms integrációt a fentiekben ismertetett Xamarin. Android-integráció mellett kell elvégezni. A remapper másként viselkedik a Xamarin. Forms-alkalmazásoknál, így a kézi MAM-cserék továbbra is szükségesek.

Miután hozzáadta az újraleképezést a projekthez, el kell végeznie a MAM-beli egyenértékű visszahelyezést. `FormsAppCompatActivity` Például a és `OnMAMResume` `OnCreate` `OnMAMCreate` `OnResume` a továbbra is használható az alkalmazásban, és a rendszer felülbírálja a következőt:. `FormsApplicationActivity`

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
* [Fordítói hiba CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Ez a hiba általában ebben az űrlapban ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``látható.
Ennek az az oka, hogy ha a remapper módosítja a Xamarin-osztályok öröklését, bizonyos függvények is `sealed` létrejönnek, és a rendszer új MAM-változatot ad hozzá a felülbíráláshoz.
* [Fordítói hiba CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Ez a hiba általában ebben az űrlapban ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``látható. Ha a remapper megváltoztatja a Xamarin egyes osztályainak öröklését, a rendszer bizonyos tag- `public`függvényeket fog módosítani. Ha felülbírálja ezen függvények bármelyikét, módosítania kell a felülbírálások hozzáférés-módosítóit `public` is.

> [!NOTE]
> A remapper újra ír egy függőséget, amelyet a Visual Studio az IntelliSense automatikus kiegészítéséhez használ. Ezért előfordulhat, hogy újra kell töltenie és újra létre kell hoznia a projektet, ha a remapper hozzá van adva az IntelliSensehoz a módosítások megfelelő felismeréséhez.

#### <a name="troubleshooting"></a>Hibaelhárítás
* Ha üres, fehér képernyőt tapasztal az alkalmazás indításakor, akkor előfordulhat, hogy a fő szálon végre kell hajtania a navigációs hívásokat.

### <a name="company-portal-app"></a>Vállalati portál alkalmazás
Az Intune SDK-Xamarin kötései a [céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android-alkalmazás jelenlétét használják az eszközön az alkalmazás-védelmi házirendek engedélyezéséhez. A Céges portál az Intune szolgáltatástól kéri le az alkalmazásvédelmi szabályzatokat. Az alkalmazás az inicializáláskor betölti a Céges portálról a szabályzatot és a betartatásához szükséges kódot. A felhasználónak nem kell bejelentkeznie.

> [!NOTE]
> Ha a Céges portál alkalmazás nem az **Android** -eszközön található, az Intune által felügyelt alkalmazás ugyanúgy viselkedik, mint egy normál alkalmazás, amely nem támogatja az Intune app Protection-házirendeket.

Az eszközregisztráció nélküli alkalmazásvédelem esetében a felhasználónak _**nem**_ kell regisztrálnia az eszközt a Céges portál alkalmazással.

### <a name="sample-applications"></a>Példák az alkalmazásokra
A MAM-funkciókat kiemelő Xamarin. Android és Xamarin Forms alkalmazások a [githubon](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps)érhetők el.

## <a name="support"></a>Támogatás
Ha a szervezete egy meglévő Intune-ügyfél, akkor a Microsoft ügyfélszolgálati képviselőjével együttműködve nyisson meg egy támogatási jegyet, és hozzon létre egy problémát a [GitHub-problémák oldalon](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) , és segítünk a lehető leghamarabb. 
