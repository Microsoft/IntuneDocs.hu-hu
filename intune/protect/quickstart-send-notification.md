---
title: 'Rövid útmutató: Értesítések küldése a nem megfelelő eszközökre'
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban a e-mailes értesítéseket küldhet a nem megfelelő eszközökre a Microsoft Intune-nal.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f8de97178beedf7e5017330bae106824c329b32
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504219"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Rövid útmutató: Értesítések küldése a nem megfelelő eszközökre

Ebben a rövid útmutatóban a e-mailes értesítéseket küldhet az alkalmazottai nem megfelelő eszközeire a Microsoft Intune-nal.

Alapértelmezés szerint az Intune a nem megfelelő eszköz észlelése után azonnal nem megfelelőként jelöli meg azt. A Azure Active Directory (HRE) [feltételes hozzáférés](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) letiltja az eszközt. Az Intune meg nem felelés esetén végrehajtandó műveleteivel rugalmas döntésekre is lehetőséget ad, ha egy eszköz nem megfelelő. Például türelmi időszakot adhat az ügyfeleknek a megfelelőséghez mielőtt letiltaná az eszközöket.

A nem megfelelőség esetén e-mailt küldet az adott végfelhasználóknak. Az értesítő e-mailt testreszabhatja, mielőtt elküldené a végfelhasználónak. Így pontosan megadhatja az e-mail címzettjeit és tárgyát, az üzenet szövegét, a céges emblémát és a kapcsolattartási adatokat. Az Intune a nem megfelelő eszköz adatait is szerepelteti az értesítésben.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
- Ha eszköz-megfelelőségi szabályzatok segítségével tiltja le az eszközöket a vállalati erőforrásokból, be kell állítania a feltételes hozzáférést a HRE. Ha elvégezte az [Eszközmegfelelőségi szabályzat létrehozása](quickstart-set-password-length-android.md) című útmutatót, az Azure Active Directoryt használja. További információ a HRE: [feltételes hozzáférés Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) és az Intune-nal való [feltételes hozzáférés gyakori módjai](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune](https://aka.ms/intuneportal) portáljára [globális rendszergazdaként](../fundamentals/users-add.md#types-of-administrators) vagy [Intune-szolgáltatásadminisztrátorként](../fundamentals/users-add.md#types-of-administrators). Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="create-a-notification-message-template"></a>Értesítési üzenetsablon létrehozása

Ha e-mailt szeretne küldeni a felhasználóknak, hozzon létre egy értesítési üzenetsablont. Ha egy eszköz nem megfelelő, a sablonban megadott adatok a felhasználóknak küldött e-mail tetején jelennek meg.

1. Az Intune-ban válassza az **Eszközmegfelelőség** > **Értesítéses** > **Értesítés létrehozása** lehetőséget. 
2. Adja meg az alábbi adatokat:

   - **Név**: *Contoso rendszergazda*
   - **Tárgy**: *Eszközmegfelelőség*
   - **Üzenet**: *az eszköz jelenleg nem felel meg a szervezet megfelelőségi követelményeinek.*
   - **E-mail fejléce – a cég emblémájának megjelenítése**: **Engedélyezze** a cég emblémájának megjelenítéséhez.
   - **E-mail fejléce – a cég nevének megjelenítése**: **Engedélyezze** a cég nevének megjelenítéséhez.
   - **E-mail lábléce – a kapcsolatfelvételi adatok megjelenítése**: **Engedélyezze** a cég kapcsolatfelvételi adataink megjelenítéséhez.

   ![Megfelelőségről szóló értesítési üzenetminta az Intune-ban](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Ha megadta a szükséges információkat, válassza a **Létrehozás** elemet. Az értesítési üzenet sablonja mostantól használható.

    > [!NOTE]
    > A korábban létrehozott értesítési sablonokat szerkesztheti is.

A cég nevének, kapcsolattartási adatainak és emblémájának beállításáról további információt [A vállalat adatai és adatvédelmi nyilatkozata](../apps/company-portal-app.md#company-information-and-privacy-statement), a [Támogatási információk](../apps/company-portal-app.md#support-information) és a [Vállalati identitási arculat testreszabása](../apps/company-portal-app.md#company-identity-branding-customization) című témakörökben találhat. 

## <a name="add-a-noncompliance-policy"></a>Nem megfelelőségi szabályzat hozzáadása

Eszközmegfelelőségi szabályzat létrehozásakor az Intune automatikusan létrehoz egy meg nem felelés esetén végrehajtandó műveletet. Ha egy eszköz nem teljesíti a megfelelőségi szabályzat követelményeit, az Intune automatikusan nem megfelelőként jelöli meg az eszközt. Testreszabhatja, hogy az eszköz meddig maradjon nem megfelelőként megjelölve. További műveletet akkor vehet fel, ha megfelelőségi szabályzatot hoz létre, vagy frissít egy meglévő szabályzatot. 

A következő lépésekkel létrehozhat egy megfelelőségi szabályzatot Windows 10-eszközökhöz.

1. Az Intune-ban válassza az **Eszközmegfelelőség** lehetőséget.
2. Válassza a **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
3. Adja meg az alábbi adatokat:

   - **Név**: *Windows 10-megfelelőség*
   - **Leírás**: *A Windows 10-re vonatkozó megfelelőségi szabályzat*
   - **Platform**: Windows 10 és újabb

4. Kattintson a **Beállítások** > **Rendszerbiztonság** elemre a biztonsági beállítások megjelenítéséhez.
5. A **Jelszó szükséges a mobileszközök feloldásához** elemnél válassza a **Kötelező** lehetőséget. Ez a beállítás határozza meg, hogy a felhasználók csak jelszó beírása után férhessenek-e hozzá a mobileszközeiken lévő információkhoz. 
6. A **jelszó minimális hosszát** állítsa **6** értékre. Ezzel a beállítással adható meg, hogy legalább hány számjegyből vagy karakterből kell állnia a jelszónak.

    <img alt="System Security settings for a new compliance policy" src="./media/quickstart-send-notification/quickstart-send-notification-01.png" width="600">

7. A megfelelőségi szabályzat létrehozásához válassza az **ok** > **OK** > **Létrehozás** lehetőséget.
8. Válassza a **Tulajdonságok** > **Meg nem felelés esetén végrehajtandó műveletek** > **Hozzáadás**. lehetőséget.
9. A **Művelet** legördülő menüben ellenőrizze, hogy az **E-mail küldése a végfelhasználóknak** lehetőség van kiválasztva.
10. Válassza az **Üzenetsablon** > **Contoso rendszergazda** > **Kiválasztás** lehetőséget a korábban létrehozott üzenetsablon kiválasztásához.
11. Válassza a **hozzáadás**@no__t – 1**OK**@no__t – 3**Mentés** lehetőséget a módosítások mentéséhez.

## <a name="assign-the-policy"></a>A szabályzat hozzárendelése

Megfelelőségi szabályzatot adott felhasználói csoportokhoz vagy minden felhasználóhoz hozzárendelhet. Ha az Intune észleli, hogy egy eszköz nem megfelelő, a felhasználó értesítést kap, hogy frissítenie kell az eszközt a megfelelőségi szabályzatok szerint. A következő lépésekkel hozzárendelheti a szabályzatot.

1. Válassza ki a korábban létrehozott **Windows 10-re vonatkozó megfelelőségi** szabályzatot.
2. Válassza a **Hozzárendelések** lehetőséget.
3. A **Hozzárendelés a következőhöz** legördülő mezőben válassza a **Minden felhasználó** lehetőséget. Ez az összes felhasználót kiválasztja. Minden, **Windows 10 és újabb** verziós eszközt használó felhasználó, aki nem felel meg a megfelelőségi szabályzatnak, értesítést kap.

    > [!NOTE]
    > Belefoglalhat és kizárhat csoportokat a szabályzatok hozzárendelésénél.

4. Kattintson a **Mentés**gombra.

Ha sikeresen létrehozta és mentette a szabályzatot, az megjelenik az **Eszközmegfelelőség – Szabályzatok** listájában. A lista **Hozzárendelve** eleme **Igen** értékre van állítva.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban az Intune használatával létrehozott és hozzárendelt egy megfelelőségi szabályzatot az alkalmazottak Windows 10-eszközeihez, hogy legalább hat karakter hosszúságú jelszót kelljen hozzájuk megadni. További információ a megfelelőségi szabályzatok Windows-eszközökhöz való létrehozásáról: [Windowsos eszközök megfelelőségi szabályzatainak hozzáadása az Intune-ban](compliance-policy-create-windows.md).

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Ügyfélalkalmazás hozzáadása és hozzárendelése](../apps/quickstart-add-assign-app.md)
