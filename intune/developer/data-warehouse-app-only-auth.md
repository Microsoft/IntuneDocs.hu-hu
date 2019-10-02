---
title: Alkalmazásalapú hitelesítés az Intune-adattárházban
titleSuffix: Microsoft Intune
description: Ez a témakör a Microsoft Intune adatraktár-alkalmazásra vonatkozó hitelesítést ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f70ca7d8d85853c38e2e8e88d06bae966431989
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730279"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Alkalmazásalapú hitelesítés az Intune-adattárházban

Beállíthat alkalmazásokat az Azure Active Directory (Azure AD) segítségével úgy, hogy hitelesítsék magukat az Intune-adattárházban. Ez a folyamat olyan webhelyeknél, alkalmazásoknál és háttérfolyamatoknál lehet hasznos, amelyek esetében az alkalmazásnak nem szabad felhasználói hitelesítő adatokkal rendelkeznie. Az alábbi lépésekkel hitelesítheti az alkalmazást az Azure AD-val az OAuth 2.0 protokoll használatával.

## <a name="authorization"></a>Authorization

Az Azure Active Directory (Azure AD) az OAuth 2.0 használatával teszi lehetővé a webalkalmazásokhoz és webes API-khez való hozzáférés engedélyezését az Azure AD-bérlőben. Ebből az útmutatóból megtudhatja, hogy hogyan hitelesítheti az alkalmazását a C# programnyelv használatával. Az OAuth 2.0 engedélyezési kódjának folyamatáról bővebben az OAuth 2.0 ismertetőjének 4.1-es szakaszában olvashat. További információt az [Hozzáférés engedélyezése webes alkalmazásokhoz az OAuth 2.0 és az Azure Active Directory használatával](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code) című témakörben talál.


## <a name="azure-keyvault"></a>Azure KeyVault

Az alábbi eljárás egy privát metódus segítségével dolgoz fel és konvertál egy alkalmazáskulcsot. Ez a privát metódus a SecureString nevet kapta. Másik lehetőségként az Azure KeyVaultban is tárolhatja az alkalmazáskulcsot. További információ: [Key Vault](https://azure.microsoft.com/services/key-vault/).

## <a name="create-a-web-app"></a>Webalkalmazás létrehozása

Ebben a szakaszban az Intune-ra irányítani kívánt webalkalmazás adatait fogja megadni. A webalkalmazások ügyfél-kiszolgáló alkalmazások. A kiszolgáló szolgáltatja a webalkalmazást, amely tartalmazza a felhasználói felületet, a tartalmat és a funkciókat. Az ilyen típusú alkalmazásokat külön, a weben kezelik. Az Intune segítségével tud hozzáférést adni a webalkalmazásnak az Intune-hoz. Az adatforgalmat a webalkalmazás kezdeményezi. 

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).
2. Az Azure Portal tetején lévő **Erőforrások, szolgáltatások és dokumentumok** mezőben keressen az **Azure Active Directory** kifejezésre.
3. A legördülő listában válassza a **Szolgáltatások** csoportban látható **Azure Active Directory** lehetőséget.
4. Válassza az **Alkalmazásregisztrációk** lehetőséget.
5. Kattintson az **Új alkalmazás regisztrálása** elemre a **Létrehozás** panel megnyitásához.
6. A **Létrehozás** panelen adja meg az alkalmazás adatait:

    - Az alkalmazás nevét (például *Alkalmazásalapú hitelesítés az Intune-ban*).
    - Az **Alkalmazástípust**. Válassza a **Webalkalmazás / API** lehetőséget egy olyan alkalmazás hozzáadásához, amely egy webalkalmazásnak, egy webes API-nak vagy ezek kombinációjának felel meg.
    - Az alkalmazás **Bejelentkezési URL-címét**. Ez az a hely, ahová az alkalmazás automatikusan átirányítja a felhasználókat a hitelesítési folyamat során. A felhasználóknak itt igazolniuk kell az identitásukat. További információt a [Mi az az alkalmazás-hozzáférés és egyszeri bejelentkezés az Azure Active Directoryban?](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis) című témakörben találhat.

7. Kattintson a **Létrehozás** gombra a **Létrehozás** panel alján.

    >[!NOTE] 
    > Másolja a vágólapra az **Alkalmazásazonosító** értéket a **Regisztrált alkalmazás** panelről későbbi használat céljából.

## <a name="create-a-key"></a>Kulcs létrehozása

Ebben a szakaszban létre fog hozni egy kulcsértéket az alkalmazáshoz az Azure AD segítségével.

1. Az **Alkalmazásregisztrációk** panelen válassza az újonnan létrehozott alkalmazást az alkalmazás paneljének megjelenítéséhez.
2. Válassza a panel tetejénél lévő **Beállítások** lehetőséget a **Beállítások** panel megjelenítéséhez.
3. A **Beállítások** panelen válassza a **Kulcsok** lehetőséget.
4. Adja meg a kulcs **Leírását**, **Lejárat** időtartamát és **Értékét**.
5. Kattintson a **Mentés** gombra az alkalmazás kulcsainak mentéséhez és frissítéséhez.
6. Fontos, hogy másolja a vágólapra a generált (Base64 kódolású) kulcsértéket.

    >[!NOTE] 
    > A kulcsérték eltűnik a **Kulcsok** panel elhagyása után, és a kulcs nem lesz többé elérhető ezen a panelen. Másolja a vágólapra későbbi használat céljából.

## <a name="grant-application-permissions"></a>Alkalmazásengedélyek megadása

Ebben a szakaszban az alkalmazás engedélyeit fogja megadni.

1. Válassza a **Szükséges engedélyek** lehetőséget a **Beállítások** panelen.
2. Kattintson a **Hozzáadás**lehetőségre.
3. Válassza az **API hozzáadása** lehetőséget az **API kiválasztása** panel megjelenítéséhez.
4. Válassza a **Microsoft Intune API (MicrosoftIntuneAPI)** lehetőséget, majd a **Kiválasztás** lehetőséget az **API kiválasztása** panelen. Ekkor az **Engedélyek kiválasztása** lépés lesz kijelölve, és megjelenik a **Hozzáférés engedélyezése** panel.
5. Válassza a **Get data warehouse information from Microsoft Intune** (Adattárház-információk beolvasása a Microsoft Intune-ból) lehetőséget az **Alkalmazásengedélyek** szakaszban.
6. Válassza a **Kiválasztás** lehetőséget a **Hozzáférés engedélyezése** panelen.
7. Válassza a **Kész** lehetőséget az **API-hozzáférés hozzáadása** panelen.
8. Válassza az **Engedélyek megadása** lehetőséget a **Szükséges engedélyek** panelen, majd válassza az **Igen** lehetőséget, amikor a rendszer az alkalmazás meglévő engedélyeinek frissítését kéri.

## <a name="generate-token"></a>Token létrehozása

Hozzon létre a Visual Studióban egy .NET-keretrendszerre épülő, C# nyelvű „Console App (.NET Framework)” típusú projektet.

1. Válassza a **File (Fájl)**  > **New (Új)**  > **Project (Projekt)** lehetőséget a **New Project** (Új projekt) párbeszédpanel megjelenítéséhez.
2. A bal oldali listában válassza a **Visual C#** lehetőséget a .NET-keretrendszerre épülő összes projekttípus megjelenítéséhez.
3. Válassza a **Console App (.NET Framework)** lehetőséget, adja meg az alkalmazás nevét, majd kattintson az **OK** gombra az alkalmazás létrehozásához.
4. A **Solution Explorer** (Megoldáskezelő) panelen válassza a **Program.cs** fájlt a kód megjelenítéséhez.
5. Megoldáskezelő adjon hozzá egy hivatkozást a szerelvényhez `System.Configuration`.
6. Válassza a helyi menüben az **Add (Hozzáadás)**  > **New item (Új elem)** lehetőséget. Ekkor megjelenik az **Add New Item** (Új elem hozzáadása) párbeszédpanel.
7. Válassza a bal oldali listában a **Visual C#** > **Code** (Kód) lehetőséget.
8. Válassza a **Class** (Osztály) lehetőséget, módosítsa az osztály nevét az *IntuneDataWarehouseClass.cs* névre, és kattintson az **Add** (Hozzáadás) gombra.
9. Adja hozzá az alábbi kódot a <code>Main</code> metódushoz:

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

10. Adjon hozzá további névtereket úgy, hogy beszúrja az alábbi kódot a fájl tetejére:

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

11. A <code>Main</code> metódus alá szúrja be az alábbi, alkalmazáskulcs feldolgozását és átalakítását végző privát metódust:

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

12. Kattintson a jobb gombbal a **Solution Explorer** (Megoldáskezelő) panelen a **References** (Hivatkozások) elemre, majd válassza a **Manage NuGet Packages** (NuGet-csomagok kezelése) lehetőséget.
13. Keressen rá a *Microsoft.IdentityModel.Clients.ActiveDirectory* csomagra, és telepítse a vonatkozó Microsoft NuGet-csomagot.
14. Válassza a **Solution Explorer** (Megoldáskezelő) panelen az *App.config* fájlt annak megnyitásához.
15. Adja hozzá az <code>appSettings</code> szakaszt, hogy az XML-kód az alábbihoz hasonlóan nézzen ki:

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

16. Frissítse az <code>appId</code>, az <code>appKey</code> és a <code>tenantDomain</code> elem értékét a saját alkalmazása egyedi értékeinek megfelelően.
17. Hozza létre az alkalmazást a Build lehetőséggel.

    >[!NOTE] 
    > További implementációs kódot az [Intune-Data-Warehouse kódpéldában](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp ) találhat.

## <a name="next-steps"></a>További lépések
Az Azure Key Vaultról további információt a [Mi az Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis) című témakörben találhat.

