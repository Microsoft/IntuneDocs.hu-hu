---
title: 'Rövid útmutató: Értesítések küldése a nem megfelelő eszközökre'
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban a Microsoft Intune használatával küld e-mail-értesítéseket a nem megfelelő eszközökre.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74410261"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Rövid útmutató: Értesítések küldése a nem megfelelő eszközökre

Ebben a rövid útmutatóban a Microsoft Intune segítségével küldhet e-mailes értesítést a munkaerőnek nem megfelelő eszközökkel rendelkező tagjainak.

Alapértelmezés szerint az Intune a nem megfelelő eszköz észlelése után azonnal nem megfelelőként jelöli meg azt. Az Azure Active Directory (Azure AD) [feltételes hozzáférése](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) ezt követően blokkolja az eszközt. Ha egy eszköz nem felel meg az előírásoknak, az Intune lehetővé teszi a meg nem felelés esetén végrehajtandó műveletek hozzáadását, ami rugalmasságot biztosít a teendők eldöntéséhez. Például türelmi időszakot adhat az ügyfeleknek a megfelelőséghez mielőtt letiltaná az eszközöket.

Egy művelet, amely akkor végezhető el, ha egy eszköz nem felel meg a megfelelőségnek, hogy e-mailt küldjön az eszközök felhasználójának. Az e-mailes értesítéseket a küldés előtt testre is szabhatja. Így pontosan megadhatja az e-mail címzettjeit és tárgyát, az üzenet szövegét, a céges emblémát és a kapcsolattartási adatokat. Az Intune a nem megfelelő eszközről is tartalmaz adatokat az e-mailes értesítésben.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

Ha eszköz-megfelelőségi szabályzatok segítségével tiltja le az eszközöket a vállalati erőforrásokból, be kell állítania az Azure AD feltételes hozzáférését. Ha végrehajtotta az [eszköz megfelelőségi szabályzatának létrehozása](quickstart-set-password-length-android.md) című rövid útmutatót, Azure Active Directory használ. Az Azure AD-vel kapcsolatos további információkért tekintse meg [a feltételes hozzáférés Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) és a [feltételes hozzáférés az Intune-nal való használatának gyakori módjai](../protect/conditional-access-intune-common-ways-use.md)című témakört.

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) [globális rendszergazdaként](../fundamentals/users-add.md#types-of-administrators) vagy Intune [szolgáltatás-rendszergazdaként](../fundamentals/users-add.md#types-of-administrators). Ha létrehozott egy Intune próbaverziós előfizetést, akkor az előfizetést létrehozó fiók a globális rendszergazda.

## <a name="create-a-notification-message-template"></a>Értesítési üzenetsablon létrehozása

Ha e-mailt szeretne küldeni a felhasználóknak, hozzon létre egy értesítési üzenetsablont. Ha egy eszköz nem megfelelő, a sablonban megadott adatok a felhasználóknak küldött e-mail tetején jelennek meg.

1. Az Intune-ban válassza az **eszközök** > **megfelelőségi szabályzatok** > **értesítések** **Értesítés létrehozása** > .
2. Adja meg az alábbi adatokat:

   - **Név**: *Contoso rendszergazda*
   - **Tárgy**: *Eszközmegfelelőség*
   - **Üzenet**: *az eszköz jelenleg nem felel meg a szervezet megfelelőségi követelményeinek.*
   - **E-mail fejléce – a cég emblémájának megjelenítése**: **Engedélyezze** a cég emblémájának megjelenítéséhez.
   - **E-mail fejléce – a cég nevének megjelenítése**: **Engedélyezze** a cég nevének megjelenítéséhez.
   - **E-mail lábléce – a kapcsolatfelvételi adatok megjelenítése**: **Engedélyezze** a cég kapcsolatfelvételi adataink megjelenítéséhez.

   ![Megfelelőségről szóló értesítési üzenetminta az Intune-ban](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Kattintson a **Tovább gombra** , és tekintse át az értesítést. Válassza a **Létrehozás** lehetőséget, és az értesítési üzenet sablonja készen áll a használatra.

   > [!NOTE]
   > A korábban létrehozott értesítési sablonokat szerkesztheti is.

A vállalat neve, a vállalati kapcsolattartási adatok és a vállalati embléma beállításával kapcsolatos részletekért tekintse meg a következő cikkeket:

- [Vállalati információk és adatvédelmi nyilatkozat](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Támogatási információk](../apps/company-portal-app.md#support-information)
- A [vállalati identitás arculatának testreszabása](../apps/company-portal-app.md#company-identity-branding-customization).

## <a name="add-a-noncompliance-policy"></a>Nem megfelelőségi szabályzat hozzáadása

Eszközmegfelelőségi szabályzat létrehozásakor az Intune automatikusan létrehoz egy meg nem felelés esetén végrehajtandó műveletet. Az Intune ezután nem megfelelőként jelöli meg az eszközöket, ha nem felelnek meg a megfelelőségi szabályzatnak. Testreszabhatja, hogy az eszköz meddig maradjon nem megfelelőként megjelölve. További műveletet akkor vehet fel, ha megfelelőségi szabályzatot hoz létre, vagy frissít egy meglévő szabályzatot.

A következő lépésekkel létrehozhat egy megfelelőségi szabályzatot Windows 10-eszközökhöz.

1. Az Intune-ban válassza az **eszközök** > **megfelelőségi szabályzatok** > **házirend létrehozása**lehetőséget.

2. Adja meg az alábbi adatokat:

   - **Név**: *Windows 10-megfelelőség*
   - **Leírás**: *A Windows 10-re vonatkozó megfelelőségi szabályzat*
   - **Platform**: Windows 10 és újabb

3. Kattintson a **Beállítások** > **Rendszerbiztonság** elemre a biztonsági beállítások megjelenítéséhez.

4. Adja meg az alábbi lehetőségeket:

   - A **Jelszó szükséges a mobileszközök feloldásához** elemnél válassza a **Kötelező** lehetőséget. Ez a beállítás határozza meg, hogy a felhasználók csak jelszó beírása után férhessenek-e hozzá a mobileszközeiken lévő információkhoz.

   - A **jelszó minimális hosszát** állítsa **6** értékre. Ezzel a beállítással adható meg, hogy legalább hány számjegyből vagy karakterből kell állnia a jelszónak.

   ![Rendszerbiztonsági beállítások új eszközmegfelelőségi szabályzathoz](./media/quickstart-send-notification/system-security-settings-01.png)

5. A megfelelőségi szabályzat létrehozásához kattintson **az OK** gombra >  > **Létrehozás** **gombra** .

6. Válassza a **Tulajdonságok** > **Meg nem felelés esetén végrehajtandó műveletek** > **Hozzáadás**. lehetőséget.

7. A **Művelet** legördülő menüben ellenőrizze, hogy az **E-mail küldése a végfelhasználóknak** lehetőség van kiválasztva.

8. Válassza ki az **üzenőfal**elemet, a cikkben korábban létrehozott sablont, majd **válassza** ki az üzenet sablonját.

9. A módosítások mentéséhez kattintson a **hozzáadás** > ok > **Mentés** **gombra** .

## <a name="assign-the-policy"></a>A szabályzat hozzárendelése

Megfelelőségi szabályzatot adott felhasználói csoportokhoz vagy minden felhasználóhoz hozzárendelhet. Ha az Intune felismeri, hogy az eszköz nem megfelelő, a felhasználó értesítést kap arról, hogy frissítenie kell az eszközét a megfelelőségi szabályzat teljesítéséhez. A szabályzat hozzárendeléséhez kövesse az alábbi lépéseket.

1. Az Intune-ban lépjen az **eszközök** > **megfelelőségi házirendek** elemre, és válassza ki a korábban létrehozott **Windows 10-es megfelelőségi** szabályzatot.

2. Válassza a **Hozzárendelések** lehetőséget.

3. A **Hozzárendelés a következőhöz** legördülő mezőben válassza a **Minden felhasználó** lehetőséget. Ez az összes felhasználót kiválasztja. Minden, **Windows 10 és újabb** verziós eszközt használó felhasználó, aki nem felel meg a megfelelőségi szabályzatnak, értesítést kap.

    > [!NOTE]
    > Belefoglalhat és kizárhat csoportokat a szabályzatok hozzárendelésénél.

4. Kattintson a **Mentés**gombra.

Amikor sikeresen létrehozta és mentette a szabályzatot, az megjelenik a **megfelelőségi szabályzatok**listájában. A lista **Hozzárendelve** eleme **Igen** értékre van állítva.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban az Intune használatával létrehozott és hozzárendelt egy megfelelőségi szabályzatot az alkalmazottak Windows 10-eszközeihez, hogy legalább hat karakter hosszúságú jelszót kelljen hozzájuk megadni. További információ a megfelelőségi szabályzatok Windows-eszközökhöz való létrehozásáról: [Windowsos eszközök megfelelőségi szabályzatainak hozzáadása az Intune-ban](compliance-policy-create-windows.md).

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Ügyfélalkalmazás hozzáadása és hozzárendelése](../apps/quickstart-add-assign-app.md)
