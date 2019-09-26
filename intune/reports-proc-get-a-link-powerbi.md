---
title: Kapcsolódás az adattárházhoz a Power BI használatával
titleSuffix: Microsoft Intune
description: A Microsoft Power BI-hoz letölthető egy fájl, amellyel a Microsoft Intune-bérlőhöz kapcsolódó interaktív, dinamikusan létrehozott jelentéseket hozhat létre.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7bc3247399341a59533e87fc5e21a44c061acddd
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/14/2019
ms.locfileid: "71303189"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Kapcsolódás az adattárházhoz a Power BI használatával

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az Power BI megfelelőségi alkalmazással az Intune-bérlőhöz kapcsolódó interaktív, dinamikusan generált jelentéseket tölthet be. Emellett a bérlői adatait Power BI a OData hivatkozás használatával is betöltheti. Az Intune kapcsolati beállításokat biztosít a bérlőhöz, így megtekintheti a következőkhöz kapcsolódó példákat és diagramokat:  

- Eszközök
- Beléptetés
- Alkalmazásvédelmi szabályzat
- Megfelelőségi szabályzat
- Eszközkonfigurációs profilok
- Szoftverfrissítések
- Eszközleltár-naplók

A jelentésekben szerepelnek továbbá a regisztrálásokra, a megfelelőségre, az eszközkonfigurációs profilokra és a szoftverfrissítésekre vonatkozó adatok és trendek. A mintadiagramok és a jelentések könnyen használható szűrőket alkalmaznak a megjelenítésnél. A Power BI Desktop **Szűrők** paneljének használatával speciális szűrőket is alkalmazhat.

Az alábbiakban bemutatjuk, hogyan töltheti le a Power BI-fájl, és hogyan használhatja az OData-hivatkozást a Power BI-vel.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>A Power BI telepítése

Telepítse a [Power bi Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi)legújabb verzióját. További információ: [Power bi Desktop](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>Az Power BI Intune megfelelőségi adattárház-alkalmazás használatával töltse be az adataikat és a jelentéseket

A Power BI [Intune megfelelőségi (adattárház-)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) alkalmazás a bérlőre vonatkozó információkat, valamint az adatraktár adatmodelljén alapuló előre elkészített jelentéseket tartalmaz.

1. A telepítési folyamat megkezdéséhez navigáljon az [Intune megfelelőségi (adatraktár-)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) alkalmazás **AppSource** lapjára.
2. Kattintson a **Letöltés most** gombra, majd a **Folytatás**gombra.
3. Amikor a rendszer a Power BI alkalmazás telepítésére kéri, kattintson a **telepítés**gombra.
4. A telepítés befejezése után kattintson az **Intune megfelelőségi (adattárház-)** alkalmazás csempére.
5. Kattintson a **kapcsolat** gombra. Megjelenik a **Kapcsolódás az Intune-hoz – megfelelőség (adattárház)** párbeszédpanel.
6. Kattintson a **Bejelentkezés** gombra.
7. Jelentkezzen be egy olyan felhasználói fiókkal, amely hozzáfér a megtekinteni kívánt jelentéseket tartalmazó bérlő Intune-adattárházához.
8. A befoglalt irányítópult megtekintéséhez kattintson az **irányítópultok** lapra, majd kattintson a **megfelelőség áttekintésére** szolgáló irányítópultra.
9. Az összes elérhető jelentés megtekintéséhez kattintson a **jelentések** lapra, majd a **megfelelőségi 1.0** -jelentésre. Böngésszen a jelentés oldalain, és kattintson a lenti lapokra.
10. Ha később szeretné megtekinteni ezeket a jelentéseket, kattintson a **megfelelőségi v 1.0** -jelentés melletti csillagra. Ezzel hozzáadja a jelentést a Power BI kedvencekhez.

Azt is megteheti, hogy az Intune-portálról telepítheti az alkalmazást:

1. Jelentkezzen be az Azure Portalra, és válassza a **Monitoring + Management (Figyelés és kezelés)**  > **Intune** elemet. Az Intune-ban is kereshet erőforrásokat.
2. Nyissa meg az **Intune-adattárház beállítása** panelt.
3. Válassza a **Beolvasás Power bi alkalmazás** lehetőséget a bérlőhöz tartozó előre létrehozott Power bi-jelentések eléréséhez és megosztásához a böngészőben.
4. Kövesse a fenti 2-10. lépést.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Adatok betöltése a Power BI-be az OData-hivatkozás használatával

Ha az ügyfél hitelesítve van az Azure AD-ben, az OData-URL kapcsolódni tud az adattárház-API RESTful-végpontjához, és így a jelentéskészítő ügyfél hozzáfér az adatmodellhez. Az alábbi lépéseket követve a Power BI Desktop használatával végezheti el a kapcsolódást, és létrehozhatja saját jelentéseit. Az OData-URL alkalmazásánál a Power BI-n kívül más elemzőeszközöket is használhat, amennyiben az ügyfél OAUTH2.0-hitelesítést, valamint az OData-szabvány 4.0-ás verzióját használja.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Az Áttekintés panel jobb oldalán található **egyéb feladatok** szakaszban kattintson az **Intune-adattárház beállítása** elemre. Ekkor megjelenik az **Intune-adattárház** panel.
3. Az egyéni hírcsatorna URL-címének beolvasása a jelentéskészítési panelről, például:`https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. Nyissa meg a **Power BI Desktopot**.
5. Válassza a **Kezdőlap** > **Adatforrás lekérése** elemet. Válassza az **OData-betöltés** lehetőséget.
6. Válassza a **Basic** (Egyszerű) lehetőséget.
7. Írja be vagy másolja be az **OData-URL-t** az URL mezőbe.
8. Kattintson az **OK** gombra.
9. Ha a Power BI Desktop-ügyfélben nem adta meg az Azure AD-s hitelesítő adatait, most adja meg azokat. Ahhoz, hogy hozzáférjen az adatokhoz, az OAuth 2.0 protokollt használva igazolnia kell, hogy jogosult az Azure Active Directory (Azure AD) használatára.  
    1. Válassza a **Szervezeti fiók** lehetőséget.  
    2. Adja meg felhasználónevét és jelszavát.  
    3. Válassza a **Bejelentkezés** lehetőséget.  
    4. Kattintson a **Csatlakozás** gombra.  
10. Válassza a **Betöltés** lehetőséget.

## <a name="next-steps"></a>További lépések

A fenti módszerrel olyan információkat kaphat a környezetről, mint például a regisztrált eszközök száma az elmúlt egy hétben napi bontásban. Betekintést nyerhet az Intune-bérlőbe és az ügyfél-populációba az Intune-adattárház Power BI az Azure-ban lekért jelentések segítségével. Ezen kívül azonban az Intune számos további lehetőséget is kínál az adatok bővítésére vagy újbóli felhasználására. A Power BI és az Intune-adattárház API további funkciókat biztosít, például:

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- A bérlő adatai olyan módon vannak felépítve, hogy azokból egyszerűen lehessen információhoz jutni. Az adatok felépítéséről az [Adattárház adatmodellje](reports-ref-data-model.md) című témakörben tájékozódhat.
- Egy RESTful interfészről is elérheti az adatokat, és belefoglalhatja azokat a saját alkalmazásába. További információért lásd [Adatok beolvasása az adattárház API-ból REST-ügyféllel](reports-proc-data-rest.md).
