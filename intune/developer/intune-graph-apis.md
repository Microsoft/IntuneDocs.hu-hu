---
title: Az Azure AD használata az Intune API-k elérésére a Microsoft Graphban
titleSuffix: Microsoft Intune
description: A cikk azokat a lépéseket írja le, amelyekkel az alkalmazások elérhetik az Intune API-kat a Microsoft Graphban az Azure AD-n keresztül.
keywords: intune graphapi c# powershell engedély szerepkörök
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a5381d139247424d976b6b510d62681f623203a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490507"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Az Azure AD használata az Intune API-k elérésére a Microsoft Graphban

A [Microsoft Graph API](https://developer.microsoft.com/graph/) mostantól megfelelő API-kkal és engedélyezési szerepkörökkel támogatja a Microsoft Intune szolgáltatást.  A Microsoft Graph API az Azure Active Directoryt (Azure AD) használja a hitelesítéshez és a hozzáférés-vezérléshez.  
Az Intune API-k a Microsoft Graphban való eléréséhez a következők szükségesek:

- Alkalmazásazonosító, amely tartalmazza:

  - az Azure AD és a Microsoft Graph API-k hívásához szükséges engedélyt,
  - az adott alkalmazásfeladatokhoz kapcsolódó engedélyhatóköröket.

- Felhasználói hitelesítő adatok, amelyek tartalmazzák:

  - a hozzáférési engedélyt az alkalmazáshoz társított Azure AD-bérlőhöz,
  - az alkalmazás-engedélyhatókörök támogatásához szükséges szerepkörengedélyeket.

- Végfelhasználó, aki engedélyezi az alkalmazásnak az Azure-bérlőhöz kapcsolódó alkalmazásfeladatokat.

Ez a cikk:

- Bemutatja, hogy kell regisztrálni egy Microsoft Graph API-hozzáféréssel és a kapcsolódó engedélyezési szerepkörökkel rendelkező alkalmazást.

- Leírja az Intune API engedélyezési szerepköreit.

- Példákat ad az Intune API hitelesítésére C# és PowerShell környezetben.

- Leírja, hogyan állítható be több bérlő támogatása.

További tudnivalókért lásd:

- [Hozzáférés engedélyezése webes alkalmazásokhoz az OAuth 2.0 és az Azure Active Directory használatával](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Azure AD-hitelesítés – első lépések](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Alkalmazások integrálása az Azure Active Directoryval](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [Az OAuth 2.0 ismertetése](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Alkalmazások regisztrálása a Microsoft Graph API használatához

Ha alkalmazásokat szeretne regisztrálni a Microsoft Graph API használatához:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba rendszergazdai hitelesítő adatok használatával.

    Igény szerint az alábbiak közül bármelyiket használhatja:
    - A bérlői rendszergazdafiókot.
    - Olyan bérlői felhasználói fiókot, amelyen engedélyezve van **A felhasználók regisztrálhatnak alkalmazásokat** beállítás.

2. A menüben válassza az **Azure Active Directory** &gt; **Alkalmazásregisztrációk** elemet.

    <img src="../media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3. Hozzon létre új alkalmazást az **Új alkalmazás regisztrálása** elemre kattintva, vagy válasszon egy meglévő alkalmazást.  (Ha meglévő alkalmazást választott, hagyja ki a következő lépést.)

4. A **Létrehozás** panelen adja meg a következőket:

    1. A **Név** mezőben adja meg az alkalmazás nevét (amely megjelenik a felhasználók bejelentkezésekor).

    2. Az **Alkalmazás típusa** és az **Átirányítási URI** mező értékét.

        Ezek az igényektől függően változhatnak. Például ha Azure AD-alapú [hitelesítési tárat](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) használ, az **Alkalmazás típusa** legyen `Native` az **Átirányítási URI** pedig legyen `urn:ietf:wg:oauth:2.0:oob`.

        <img src="../media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        További tudnivalókért lásd: [Hitelesítési forgatókönyvek az Azure AD-ban](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

5. Az alkalmazás paneljén:

    1. Jegyezze fel az **Alkalmazás azonosítója** mező értékét.

    2. Válassza a **Beállítások** &gt; **API-hozzáférés** &gt; **Szükséges engedélyek** lehetőséget.

    <img src="../media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6. A **Szükséges engedélyek** panelen válassza a **Hozzáadás** &gt; **API-hozzáférés hozzáadása** &gt; **API kiválasztása** lehetőséget.

    <img src="../media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7. Az **API kiválasztása** panelen válassza a **Microsoft Graph** &gt; **Kiválasztás** lehetőséget.  Ekkor megnyílik a **Hozzáférés engedélyezése** panel, amelyen látható az alkalmazás számára elérhető engedélyhatókörök listája.

    <img src="../media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    Helyezzen pipát az alkalmazás számára szükséges szerepkörök nevétől balra.  Az adott Intune-engedélyhatókörök megismeréséhez lásd: [Intune-engedélyhatókörök](#intune-permission-scopes).  Egyéb Graph API-engedélyhatókörök megismeréséhez lásd a [Microsoft Graph-engedélyekkel kapcsolatos segédanyagot](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

    A legjobb eredményt akkor éri el, ha az alkalmazás implementálásához szükséges lehető legkevesebb szerepkört választja.

    Ha elkészült, kattintson a **Kiválasztás**, majd a **Kész** elemre a változások mentéséhez.

Ezen a ponton lehetősége van:

- Engedélyt adhat minden bérlői fióknak, hogy hitelesítő adatok megadása nélkül használja az alkalmazást.  

    Ehhez válassza az **Engedélyek megadása** lehetőséget, és fogadja el a megerősítési kérést.

    Amikor először futtatja az alkalmazást, a rendszer kérni fogja, hogy adja meg az engedélyt az alkalmazásnak a kiválasztott szerepkörök végrehajtásához.

    <img src="../media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- Elérhetővé teheti az alkalmazást a bérlőn kívüli felhasználók számára.  (Ez általában csak olyan partnerek esetén szükséges, akik több bérlőt, illetve céget támogatnak.)  

    Ehhez tegye a következőket:

  1. Az alkalmazás paneljén kattintson a **Jegyzékfájl** elemre, amely megnyitja a **Jegyzékfájl szerkesztése** panelt.

     <img src="../media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. Módosítsa az `availableToOtherTenants` beállítást `true` értékűre.

  3. Mentse a változtatásokat.

## <a name="intune-permission-scopes"></a>Intune-engedélyhatókörök

Az Azure AD és a Microsoft Graph engedélyhatókörök segítségével szabályozza a céges erőforrásokhoz való hozzáférést.  

Az engedélyhatókörök (más néven _OAuth-hatókörök_) az adott Intune-entitásokhoz és tulajdonságaikhoz való hozzáférést szabályozzák. Ez a szakasz az Intune API-funkciók engedélyhatóköreit foglalja össze.

További tudnivalók:
- [Azure AD-hitelesítés](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Alkalmazás-engedélyhatókörök](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

A Microsoft Graph engedélyezésekor az alábbi táblázatban összefoglalt Intune API-engedélyhatóköröket adhatja meg az Intune-funkciókhoz való hozzáférés szabályozásához.  Az első oszlop a funkció nevét tünteti fel abban a formában, ahogy az Azure Portalon megjelenik, a második oszlopban az engedélyhatókör neve látható.

_Hozzáférés engedélyezése_ beállítás | Hatókör neve
:--|:--
__Felhasználót érintő távoli műveletek végzése Microsoft Intune-eszközökön__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Microsoft Intune-eszközök olvasása és írás rájuk__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Microsoft Intune-eszközök olvasása__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Microsoft Intune RBAC beállításainak olvasása és írása__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Microsoft Intune RBAC beállításainak olvasása__ | DeviceManagementRBAC. Read. All
__Microsoft Intune-alkalmazások olvasása és írás rájuk__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Microsoft Intune-alkalmazások olvasása__ | [DeviceManagementApps.Read.All](#app-ro)
__Microsoft Intune-beli eszközkonfiguráció és szabályzatok olvasása és írása__ | DeviceManagementConfiguration. ReadWrite. All
__Microsoft Intune-beli eszközkonfiguráció és szabályzatok olvasása__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Microsoft Intune-konfiguráció olvasása és írása__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Microsoft Intune-konfiguráció olvasása__ | DeviceManagementServiceConfig. Read. All

A táblázat az Azure Portalon látható sorrendben listázza a beállításokat. Az alábbi szakaszokban a hatókörök betűrendes listája és a hozzájuk tartozó leírás olvasható.

Jelenleg minden Intune-engedélyhatókörhöz rendszergazdai hozzáférés szükséges.  Ez azt jelenti, hogy az Intune API-erőforrásokhoz hozzáférő alkalmazások vagy szkriptek futtatásához rendelkeznie kell a megfelelő hitelesítő adatokkal.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune-alkalmazások olvasása__

- Olvasási hozzáférést biztosít a következő entitástulajdonságokhoz és -állapotokhoz:
  - Ügyfélalkalmazások
  - Mobilalkalmazás-kategóriák
  - Alkalmazásvédelmi szabályzatok
  - Alkalmazáskonfigurációs szabályzatok

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- **Hozzáférés engedélyezés** beállítás: __Microsoft Intune-alkalmazások olvasása és írása__

- Lehetővé teszi ugyanazokat a műveleteket, mint a __DeviceManagementApps.Read.All__

- Ezenkívül lehetővé teszi az alábbi entitások módosítását is:

  - Ügyfélalkalmazások
  - Mobilalkalmazás-kategóriák
  - Alkalmazásvédelmi szabályzatok
  - Alkalmazáskonfigurációs szabályzatok

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune-eszközkonfiguráció és -szabályzatok olvasása__

- Olvasási hozzáférést biztosít a következő entitástulajdonságokhoz és -állapotokhoz:
  - Eszközkonfiguráció
  - Eszköz-megfelelőségi szabályzat
  - Értesítési üzenetek

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune-eszközkonfiguráció és -szabályzatok olvasása és írása__

- Lehetővé teszi ugyanazokat a műveleteket, mint a __DeviceManagementConfiguration.Read.All__

- Ezenkívül az alkalmazások létrehozhatják, hozzárendelhetik, törölhetik és módosíthatják a következő entitásokat:
  - Eszközkonfiguráció
  - Eszköz-megfelelőségi szabályzat
  - Értesítési üzenetek

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- **Hozzáférés engedélyezése** beállítás: __Felhasználókat érintő távoli műveletek végrehajtása Microsoft Intune-eszközökön__

- Lehetővé teszi a következő távoli műveletek felügyelt eszközön való végrehajtását:
  - Kivonás
  - Törlés
  - PIN-kód alaphelyzetbe állítása/helyreállítása
  - Távoli zárolás
  - Elveszett eszköz mód engedélyezése/letiltása
  - Számítógép megtisztítása
  - Újraindítás
  - Felhasználó törlése megosztott eszközről

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune-eszközök olvasása__

- Olvasási hozzáférést biztosít a következő entitástulajdonságokhoz és -állapotokhoz:
  - Felügyelt eszköz
  - Eszközkategória
  - Észlelt alkalmazás
  - Távoli műveletek
  - Kártevőkre vonatkozó információ

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune-eszközök olvasása és írása__

- Lehetővé teszi ugyanazokat a műveleteket,mint a __DeviceManagementManagedDevices.Read.All__

- Ezenkívül az alkalmazások létrehozhatják, törölhetik és módosíthatják a következő entitásokat:
  - Felügyelt eszköz
  - Eszközkategória

- A következő távoli műveletek szintén engedélyezettek:
  - Eszközök megkeresése
  - Aktiválási zár megkerülése
  - Távsegítség kérése

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune RBAC-beállítások olvasása__

- Olvasási hozzáférést biztosít a következő entitástulajdonságokhoz és -állapotokhoz:
  - Szerepkör-hozzárendelések
  - Szerepkör-definíciók
  - Erőforrás-műveletek

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune RBAC-beállítások olvasása és írása__

- Lehetővé teszi ugyanazokat a műveleteket,mint a __DeviceManagementRBAC.Read.All__

- Ezenkívül az alkalmazások létrehozhatják, hozzárendelhetik, törölhetik és módosíthatják a következő entitásokat:
  - Szerepkör-hozzárendelések
  - Szerepkör-definíciók

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune-konfiguráció olvasása__

- Olvasási hozzáférést biztosít a következő entitástulajdonságokhoz és -állapotokhoz:
  - Eszközök beléptetése
  - Apple Push Notification-tanúsítvány
  - Apple Készülékregisztrációs program
  - Apple Volume Purchase Program
  - Exchange-összekötő
  - Feltételek és kikötések
  - Távközlési költségek kezelése
  - Felhőalapú PKI
  - Védjegyezés
  - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- **Hozzáférés engedélyezése** beállítás: __Microsoft Intune-konfiguráció olvasása és írása__

- Lehetővé teszi ugyanazokat a műveleteket, mint a DeviceManagementServiceConfig.Read.All_

- Ezenkívül az alkalmazások a következő Intune-funkciókat is konfigurálhatják:
  - Eszközök beléptetése
  - Apple Push Notification-tanúsítvány
  - Apple Készülékregisztrációs program
  - Apple Volume Purchase Program
  - Exchange-összekötő
  - Feltételek és kikötések
  - Távközlési költségek kezelése
  - Felhőalapú PKI
  - Védjegyezés
  - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Példák az Azure AD-hitelesítésre

Ez a szakasz azt mutatja be, hogy miként építheti be az Azure AD-t C#- és PowerShell-alapú projektekbe.

Minden példánál szükség lesz egy olyan alkalmazásazonosító megadására, amely legalább a `DeviceManagementManagedDevices.Read.All` engedélyhatókört tartalmazza (a fent leírtak szerint).

Bármely példa tesztelésénél előfordulhat, hogy a rendszer az alábbihoz hasonló 403-as (Tiltott) HTTP-állapothibát jelez:

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

Ilyenkor ellenőrizze a következőket:

- Az alkalmazásazonosítót olyanra módosította, amely jogosult a Microsoft Graph API és a `DeviceManagementManagedDevices.Read.All` engedélyhatókör használatára.

- A bérlői hitelesítő adatok támogatják a felügyeleti funkciókat.

- A kód hasonlít az itt bemutatott példákhoz.


### <a name="authenticate-azure-ad-in-c"></a>Az Azure AD hitelesítése C\#-környezetben

Az alábbi példa az Intune-fiókhoz társított eszközök C#-kód használatával való beolvasását mutatja be.

1. Indítsa el a Visual Studiót, majd hozzon létre egy új Visual C#-alapú konzolalkalmazás-projektet (.NET-keretrendszer).

2. Adja meg a projekt nevét, és igény szerint a további adatokat.

    <img src="../media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3. Adja hozzá a projekthez a Microsoft ADAL NuGet-csomagot a Megoldáskezelő segítségével.

    1. Kattintson a jobb gombbal a Megoldáskezelőre.
    2. Válassza a **Manage NuGet-Packages…** (NuGet-csomagok kezelése) &gt; **Browse** (Tallózás) lehetőséget.
    3. Válassza ki a `Microsoft.IdentityModel.Clients.ActiveDirectory` elemet, majd kattintson az **Install** (Telepítés) elemre.

    <img src="../media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4. A **Program.cs** fájl elejére illessze be a következő utasításokat:

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5. Adjon meg egy metódust az engedélyezési fejléc létrehozásához:

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    Ne felejtse el módosítani az `application_ID` értékét úgy, hogy a korábban leírtaknak megfelelően legalább a `DeviceManagementManagedDevices.Read.All` engedélyhatókörrel rendelkező alkalmazásnak feleljen meg.

6. Adjon meg egy metódust az eszközök listájának beolvasásához:

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7. Módosítsa a **Main** elemet úgy, hogy meghívja **GetMyManagedDevices** metódust:

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8. Fordítsa és futtassa a programot.  

A program első futtatásánál két kérést kell kapnia.  Az első a hitelesítő adatokat kéri, a másodikkal pedig megadhatja az engedélyeket a `managedDevices` kérelemre.  

Referenciaként itt látható a kész program:

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Az Azure AD hitelesítése a PowerShell használatával

A következő PowerShell-szkript az Azure AD PowerShell modulját használja a hitelesítéshez.  További tudnivalók az [Azure Active Directory PowerShell – 2-es verzió](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) és az [Intune-os PowerShell-minták](https://github.com/microsoftgraph/powershell-intune-samples) cikkben olvasható.

Ebben a példában a `$clientID` értékét frissítse olyan értékre, amely megfelel egy érvényes alkalmazásazonosítónak.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>Több bérlő és partner támogatása

Ha a cége saját Azure AD-bérlővel rendelkező cégeket támogat, igény szerint engedélyezheti az ügyfeleknek, hogy a saját bérlőjükön keresztül használják az alkalmazást.

Ehhez tegye a következőket:

1. Ellenőrizze, hogy az ügyfélfiók létezik az céloldali Azure AD-bérlőn.

2. Gondoskodjon róla, hogy az ügyfélfiók engedélyezze a felhasználóknak az alkalmazásregisztrációt (lásd: **Felhasználói beállítások**).

3. Létesítsen kapcsolatot az egyes bérlők között.  

    Ehhez tegye a következők egyikét:

    a. A [Microsoft Partnerközpont](https://partnercenter.microsoft.com/) segítségével definiáljon kapcsolatot az ügyfelekkel és az e-mail-címükkel.

    b. Hívja meg a felhasználókat a bérlőre vendégként.

Így vehet fel vendégfelhasználót a bérlőre:

1. A **Gyors feladatok** panelen válassza a **Vendégfelhasználó felvétele** lehetőséget.

    <img src="../media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2. Adja meg az ügyfél e-mail-címét, és (igény szerint) írja be a személyes meghívó szövegét.

    <img src="../media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3. Kattintson a **Meghívás** elemre.

Ezzel elküldi a meghívót a felhasználónak.

   <img src="../media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   A meghívó elfogadásához a felhasználónak a **Get Started** (Kezdés) hivatkozásra kell kattintania.

Miután létrejött a kapcsolat (vagy elfogadták a meghívót), adja hozzá a felhasználói fiókot a **címtárszerepkörhöz**.

Ne felejtse el hozzáadni a felhasználót igény szerint a többi szerepkörhöz is. Ahhoz például, hogy a felhasználó engedélyt kapjon az Intune-beállítások kezelésére, **globális rendszergazdának** vagy **Intune-beli szolgáltatás-rendszergazdának** kell lennie.

Ezenkívül:

- A(z) https://admin.microsoft.com segítségével rendeljen hozzá egy Intune-licencet az felhasználói fiókhoz.

- Módosítsa úgy az alkalmazás kódját, hogy a sajátja helyett inkább az ügyfél Azure AD-bérlői tartományán hitelesítsen.

    Ha például a saját bérlői tartománya `contosopartner.onmicrosoft.com` az ügyfél bérlői tartománya pedig `northwind.onmicrosoft.com`, a kódot úgy kell módosítania, hogy az ügyfél bérlőjén hitelesítsen.

    Ha ezt az előző példában látható C#-alkalmazásban kívánja megtenni, az `authority` változó értékét így kell módosítania:

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    Módosított sor:

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
