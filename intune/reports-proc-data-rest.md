---
title: Adatok beolvasása az adattárház API-ból REST-ügyféllel
titleSuffix: Microsoft Intune
description: Ez a témakör azt ismerteti, hogyan kérhet le információkat a Microsoft Intune adattárházból egy REST API használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b449dcc0ba0fc33f66db54c4cfd158aaefa8032e
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69582971"
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>Adatok beolvasása az Intune-adattárház API-ból REST-ügyféllel

Az Intune-adatárház adatmodellje RESTful végpontokon keresztül érhető el. Ahhoz, hogy hozzáférjen az adatokhoz, az ügyfélnek az OAuth 2.0 protokollt használva igazolnia kell, hogy jogosult a Microsoft Azure Active Directory (Azure AD) használatára. A hozzáférés engedélyezéséhez először hozzon létre egy natív alkalmazást az Azure-ban, majd adjon annak engedélyeket a Microsoft Intune API használatára. Amikor a helyi ügyfél megkapja az engedélyt, a natív alkalmazáson keresztül fog tudni kommunikálni az adattárház-végpontokkal.

Egy ügyfél adatok az adattárház API-ból való beolvasására történő beállításához a következőket kell tennie:

1. Ügyfélalkalmazás létrehozása natív alkalmazásként az Azure-ban
3. Hozzáférés biztosítása az ügyfélalkalmazásnak a Microsoft Intune API-hoz
3. Helyi REST-ügyfél létrehozása az adatok beolvasásához

Az alábbi lépésekből megtudhatja, hogyan engedélyezheti és érheti el az API-t REST-ügyféllel. Először áttekintheti az általános REST-ügyfelek a Postman alkalmazással való használatát. A Postman alkalmazást gyakran használják API-kat használó REST-ügyfelek fejlesztésére és hibaelhárítására. A Postmannel kapcsolatban a [Postman](https://www.getpostman.com) webhelyén találhat további információkat. Ezután tanulmányozhat egy C#-kódmintát. A példa azt mutatja be, hogyan lehet engedélyezni egy ügyfélprogramot, és beolvasni adatokat az API-ból.

## <a name="create-a-client-app-as-a-native-app-in-azure"></a>Ügyfélalkalmazás létrehozása natív alkalmazásként az Azure-ban

Hozzon létre egy natív alkalmazást az Azure-ben. Ez a natív alkalmazás az ügyfélalkalmazás. A helyi számítógépen futó ügyfélalkalmazás az Intune adattárház API-ra hivatkozik, amikor a helyi ügyfél bekéri a hitelesítési adatokat.

1. Jelentkezzen be a bérlőhöz tartozó Azure Portalra. Válassza az **Azure Active Directory** > **Alkalmazásregisztrációk** lehetőséget az **Alkalmazásregisztrációk** panel megnyitásához.
2. Válassza az **Új alkalmazásregisztráció** lehetőséget.
3. Gépelje be az alkalmazás adatait.
    1. A **Név** mezőben adjon meg egy felhasználóbarát nevet, például azt, hogy „Intune-adattárházügyfél”.
    2. Az **Alkalmazástípus** mezőben válassza a **Natív** lehetőséget.
    3. Írjon be egy URL-címet a **Bejelentkezési URL-cím** mezőbe. A bejelentkezési URL-cím az adott forgatókönyvtől is függ, azonban ha a Postman alkalmazást tervezi használni, a következő címet írja be: `https://www.getpostman.com/oauth2/callback`. A visszahívásra az ügyfél-hitelesítési lépésben lesz szükség a Microsoft Azure AD-beli hitelesítéshez.
4. Kattintson a **Létrehozás** gombra.

     ![Intune-adattárház-ügyfélalkalmazás](./media/reports-get_rest_data_client_overview.png)

5. Jegyezze fel az alkalmazás **Alkalmazásazonosítóját**. Az azonosítóra szükség lesz a következő szakaszban.

## <a name="grant-the-client-app-access-to-the-microsoft-intune-api"></a>Hozzáférés biztosítása az ügyfélalkalmazásnak a Microsoft Intune API-hoz

Most már rendelkezik egy Azure-ban definiált alkalmazással. Gondoskodjon arról, hogy a natív alkalmazásból hozzá lehessen férni a Microsoft Intune API-hoz.

1. Válassza ki a natív alkalmazást. Az alkalmazásnak Ön az **Intune-adattárházügyfél**, vagy ehhez hasonló nevet adott.
2. A **Beállítások** panelen válassza a **Szükséges engedélyek** lehetőséget
3. A **Szükséges engedélyek** panelen válassza a **Hozzáadás** lehetőséget.
4. Válassza az **API kiválasztása** lehetőséget.
5. Keressen rá a webalkalmazás nevére. Az alkalmazás neve **Microsoft Intune API**.
6. Jelölje ki az alkalmazást a listában.
7. Válassza a **Kiválasztás** lehetőséget.
8. Jelölje be a **Delegált engedélyek** jelölőnégyzetet a **Get data warehouse information from Microsoft Intune** (Adattárház-információk beolvasása a Microsoft Intune-ból) lehetőség felvételéhez.

    ![Hozzáférés engedélyezése – Microsoft Intune API](./media/reports-get_rest_data_client_access.png)

9. Válassza a **Kiválasztás** lehetőséget.
10. Válassza a **Done** (Kész) lehetőséget.
11. A Szükséges engedélyek panelen választhatja az **Engedélyek megadása** lehetőséget. Így az aktuális címtár minden fiókjának adható hozzáférés. Ezáltal elkerülhető, hogy a hozzájárulási párbeszédpanel a bérlő összes felhasználójánál megjelenjen. További információt az [Integrating applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) (Alkalmazások integrációja az Azure Active Directory-val) című témakörben találhat.
12. Válassza az **Igen** lehetőséget.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Adatok beolvasása a Microsoft Intune API-ból a Postman alkalmazással

Az Intune-adattárház API-t használhatja olyan általános REST ügyfelekkel, mint például a Postman. A Postman információkat tud biztosítani az API szolgáltatásairól, a mögöttes OData-adatmodellről, és el tudja hárítani az API-erőforrásokkal létesített kapcsolatok hibáit. Ez a szakasz bemutatja, hogyan hozhat létre egy Auth2.0-jogkivonatot a helyi ügyfél számára. Az ügyfélnek az Azure AD-ben való hitelesítéshez és az API-erőforrásokhoz való hozzáféréshez lesz szüksége a jogkivonatra.

### <a name="information-you-will-need-to-make-the-call"></a>A híváshoz szükséges információk

A következők szükségesek REST-hívások a Postman alkalmazásból való végrehajtásához:

| Attribútum        | Leírás                                                                                                                                                                          | Példa                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Visszahívási URL     | Az alábbi címet adja meg az alkalmazás Beállítások oldalán visszahívási URL-címként.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| Jogkivonat neve       | A sztring, amellyel az ügyfél átadja a hitelesítő adatokat az Azure-alkalmazásnak. A folyamat során egy jogkivonat jön létre, mellyel az adattárház API-t hívhatja.                          | Tulajdonos                                                                                        |
| Hitelesítési URL-cím         | A hitelesítéshez használt URL-cím. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/ |
| Hozzáférési jogkivonat URL-címe | A jogkivonat megadásához használt URL-cím.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| Ügyfél-azonosító        | Az Azure-beli natív alkalmazás létrehozásakor hozta létre és jegyezte fel.                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| Hatókör (nem kötelező) | Üres                                                                                                                                                                               | Ezt a mezőt üresen hagyhatja.                                                                     |
| Engedélyezési típus       | A jogkivonat egy engedélyezési kód.                                                                                                                                                  | Engedélyezési kód                                                                            |

### <a name="odata-endpoint"></a>OData-végpont

A végpont is szükséges. Az adattárház-végpont beszerzéséhez szükséges az egyedi hírcsatorna URL-címe. Az OData-végpont az Adattárház panelen érhető el.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Nyissa meg az **Intune** -adattárház panelt az adatraktár hivatkozásának kiválasztásával az **Microsoft Intune – áttekintés** panel jobb oldalán található **egyéb feladatok** területen.
4. Másolja be az egyedi hírcsatorna URL-címét a **Külső gyártótól származó jelentéskészítési szolgáltatások használata** szakaszba. Az eredménynek a következőhöz hasonlónak kell lennie: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0`

A végpont a következő formátumot követi:`https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity}?api-version={verson-number}`

A **dates** entitás megjelenése például a következő: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`

További információt az [Intune-adattárház API-végpontja](reports-api-url.md) című témakörben találhat.

### <a name="make-the-rest-call"></a>A REST-hívás végrehajtása

Ahhoz, hogy beszerezzen egy új hozzáférési jogkivonatot a Postman számára, meg kell adnia az Azure AD engedélyezési URL-címet, az ügyfél-azonosítót és a titkos ügyfélkódot. A Postman betölti az engedélyezési oldalt, melyen meg kell adnia a hitelesítő adatait.

#### <a name="add-the-information-used-to-request-the-token"></a>A jogkivonat kéréséhez szükséges információk

1. Ha még nincs telepítve, töltse le a Postman alkalmazást. A Postman alkalmazást a [www.getpostman](https://www.getpostman.com) címről töltheti le.
2. Nyissa meg a Postmant. Válassza ki a **GET** HTTP-műveletet.
3. Illessze be a végpont URL-címét a címbe. Valahogy így kell kinéznie:  

    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. Válassza az **Authorization** (Engedélyezés) lapot, és a **Type** (Típus) listában válassza ki az **OAuth 2.0** lehetőséget.
5. Válassza az **Get New Access Token** (Új hozzáférési jogkivonat beszerzése) lehetőséget.
6. Ellenőrizze, hogy hozzáadta-e már a visszahívási URL-címet (Callback URL) az Azure-beli alkalmazáshoz. A Callback URL (Visszahívási URL-cím) a következő: `https://www.getpostman.com/oauth2/callback`.
7. A **Token Name** (Jogkivonat neve) mezőbe írja be a Bearer értéket.
8. Adja meg az **Auth URL** (Hitelesítési URL-cím) értékét. Valahogy így kell kinéznie:  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/`
9. Adja meg az **Access Token URL** (Hozzáférési jogkivonat URL-címe) értékét. Valahogy így kell kinéznie:  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Adja meg a **Client ID** (Ügyfél-azonosító) értékét az Azure-ben létrehozott, `Intune Data Warehouse Client` nevű alkalmazásból. Valahogy így kell kinéznie:  

     `88C8527B-59CB-4679-A9C8-324941748BB4`

11. Válassza az **Authorization Code** (Engedélyezési kód) lehetőséget, és jelölje be a Request access code locally (Hozzáférési jogkivonat kérése helyileg) jelölőnégyzetet.

12. Válassza a **Request Token** (Jogkivonat kérése) lehetőséget.

    ![A hozzáférési jogkivonat adatai](./media/reports-postman_getnewtoken.png)

13. Adja meg a hitelesítő adatait az Active AD engedélyezési oldalán. A Postmanben most már szerepelni fog a `Bearer` nevű jogkivonat a jogkivonatok listáján.
14. Válassza a **Use Token** (Jogkivonat használata) lehetőséget. A fejlécek listája tartalmazza az új engedélyezési kulcsértéket és a `Bearer <your-authorization-token>` értéket.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Küldje el a hívást a végpontra a Postman alkalmazással.

1. Kattintson a **Küldés** gombra.
2. A visszaadott adatok a Postman-válasz törzsében jelennek meg.

    ![A Poster-ügyfél állapota 200 OK](./media/reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>REST-ügyfél (C#) létrehozása az Intune-adattárház adatainak beolvasásához

Az alábbi minta egy egyszerű REST-ügyfelet tartalmaz. A kód a .Net-kódtár **httpClient** osztályát használja. Amikor az ügyfél Azure AD-beli hitelesítő adatokat kap, létrehoz egy GET REST hívást a dates entitás az adattárház API-ból való beolvasásához.

> [!Note]  
> Az alábbi kódminta elérhető a [GitHubon](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs). A kód legutóbbi változtatásai és frissítései a GitHub-tárházban érhetők el.

1. Indítsa el a **Microsoft Visual Studiót**.
2. Válassza a **Fájl** > **Új projekt** lehetőséget. Bontsa ki a **Visual C#** lehetőséget, és válassza a **Console App (.Net Framework)** (Konzolalkalmazás (.Net-keretrendszer)) lehetőséget.
3. A projektnek adja az `IntuneDataWarehouseSamples` nevet, és tallózással válassza ki, hova szeretné azt menteni, majd kattintson az **OK** gombra.
4. Kattintson a jobb gombbal a megoldás nevére a Megoldáskezelőben, majd válassza a **Manage NuGet Packages for Solution** (Megoldás NuGet-csomagjainak kezelése) lehetőséget. Válassza a **Tallózás** elemet, majd írja a `Microsoft.IdentityModel.Clients.ActiveDirectory` szöveget a keresőmezőbe.
5. Válassza ki a csomagot, jelölje ki a **IntuneDataWarehouseSamples** projektet a Manage Packages for Your Solution (Megoldás csomagjainak kezelése) szakaszban, majd válassza a **Telepítés** lehetőséget.
6. Az **Elfogadom** elemet választva fogadja el a NuGet-csomag licencfeltételeit.
7. Nyissa meg a `Program.cs` fájlt a Megoldáskezelőben.

    ![Program.cs és Megoldáskezelő a Visual Studióban](./media/reports-get_rest_data_in.png)

8. Cserélje le a *program.cs* található kódot a következő kódra:  

   ```csharp
   namespace IntuneDataWarehouseSamples
   {
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;
   using Microsoft.IdentityModel.Clients.ActiveDirectory;

   class Program
   {
    static void Main(string[] args)
   {
   /**
   * TODO: Replace the below values with your own.
   * emailAddress - The email address of the user that you will authenticate as.
   *
   * password  - The password for the above email address.
   *    This is inline only for simplicity in this sample. We do not
   *    recommend storing passwords in plaintext.
   *
   * applicationId - The application ID of the native app that was created in AAD.
   *
   * warehouseUrl   - The data warehouse URL for your tenant. This can be found in
   *      the Azure portal.
   *
   * collectionName - The name of the warehouse entity collection you would like to
   *      access.
   */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
   resource: "https://api.manage.microsoft.com/",
   clientId: applicationId,
   userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
   }
   }
   ```

9. Frissítse a mintakódban található `TODO` elemeket.
10. A **Ctrl + F5** billentyűkombinációval állítsa össze és futtassa az Intune.DataWarehouseAPIClient ügyfelet hibakeresési módban.

    ![JSON formátumban beolvasott dátumentitás.](./media/reports-get_rest_data_output.png)

11. Tekintse meg a kimenetet a konzolon. A kimenet JSON formátumban tartalmazza az Intune-bérlő **dates** entitásából kinyert adatokat.

## <a name="next-steps"></a>További lépések

Az engedélyezéssel, az API URL-címek szerkezetével és az OData-végpontokkal kapcsolatban az [Intune-adattárház API-végpontja](reports-api-url.md) című témakörben találhat további információkat.

Az API-ban megtalálható adatentitásokkal kapcsolatban az Intune-adattárház adatmodelljében is tájékozódhat. További információ: [Az adattárház adatmodellje](reports-ref-data-model.md).
