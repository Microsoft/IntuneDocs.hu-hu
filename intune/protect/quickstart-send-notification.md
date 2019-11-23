---
title: 'Rövid útmutató: Értesítések küldése a nem megfelelő eszközökre'
titleSuffix: Microsoft Intune
description: In this quickstart, you use Microsoft Intune to send email notifications to noncompliant devices.
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
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410261"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Rövid útmutató: Értesítések küldése a nem megfelelő eszközökre

In this quickstart, you'll use Microsoft Intune to send an email notification to the members of your workforce that have noncompliant devices.

Alapértelmezés szerint az Intune a nem megfelelő eszköz észlelése után azonnal nem megfelelőként jelöli meg azt. Azure Active Directory (Azure AD) [Conditional Access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) then blocks the device. When a device isn't compliant, Intune allows you to add actions for noncompliance, which gives you flexibility to decide what to do. Például türelmi időszakot adhat az ügyfeleknek a megfelelőséghez mielőtt letiltaná az eszközöket.

One action to take when a device doesn't meet compliance is to send email to the devices user. You can also customize an email notification before sending it. Így pontosan megadhatja az e-mail címzettjeit és tárgyát, az üzenet szövegét, a céges emblémát és a kapcsolattartási adatokat. Intune also includes details about the noncompliant device in the email notification.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

When using device compliance policies to block devices from corporate resources, Azure AD Conditional Access must be set up. If you've completed the [Create a device compliance policy](quickstart-set-password-length-android.md) quickstart, you're using Azure Active Directory. For more information about Azure AD, see [Conditional Access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) and [common ways to use Conditional Access with Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) as a [Global administrator](../fundamentals/users-add.md#types-of-administrators) or an Intune [Service administrator](../fundamentals/users-add.md#types-of-administrators). If you've created an Intune Trial subscription, the account you created the subscription with is the Global administrator.

## <a name="create-a-notification-message-template"></a>Értesítési üzenetsablon létrehozása

Ha e-mailt szeretne küldeni a felhasználóknak, hozzon létre egy értesítési üzenetsablont. Ha egy eszköz nem megfelelő, a sablonban megadott adatok a felhasználóknak küldött e-mail tetején jelennek meg.

1. In Intune, select **Devices** > **Compliance policies** > **Notifications** > **Create notification**.
2. Adja meg az alábbi adatokat:

   - **Név**: *Contoso rendszergazda*
   - **Tárgy**: *Eszközmegfelelőség*
   - **Message**: *Your device is currently not meeting our organization's compliance requirements.*
   - **E-mail fejléce – a cég emblémájának megjelenítése**: **Engedélyezze** a cég emblémájának megjelenítéséhez.
   - **E-mail fejléce – a cég nevének megjelenítése**: **Engedélyezze** a cég nevének megjelenítéséhez.
   - **E-mail lábléce – a kapcsolatfelvételi adatok megjelenítése**: **Engedélyezze** a cég kapcsolatfelvételi adataink megjelenítéséhez.

   ![Megfelelőségről szóló értesítési üzenetminta az Intune-ban](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Select **Next** and review your notification. Select **Create** and the notification message template is ready to use.

   > [!NOTE]
   > A korábban létrehozott értesítési sablonokat szerkesztheti is.

For details about setting your company name, company contact information, and company logo, see the following articles:

- [Company information and privacy statement](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Support information](../apps/company-portal-app.md#support-information)
- [Company identity branding customization](../apps/company-portal-app.md#company-identity-branding-customization).

## <a name="add-a-noncompliance-policy"></a>Nem megfelelőségi szabályzat hozzáadása

Eszközmegfelelőségi szabályzat létrehozásakor az Intune automatikusan létrehoz egy meg nem felelés esetén végrehajtandó műveletet. Intune then marks devices as noncompliant when they fail to meet your compliance policy. Testreszabhatja, hogy az eszköz meddig maradjon nem megfelelőként megjelölve. További műveletet akkor vehet fel, ha megfelelőségi szabályzatot hoz létre, vagy frissít egy meglévő szabályzatot.

A következő lépésekkel létrehozhat egy megfelelőségi szabályzatot Windows 10-eszközökhöz.

1. In Intune, select **Devices** > **Compliance Policies** > **Create Policy**.

2. Adja meg az alábbi adatokat:

   - **Név**: *Windows 10-megfelelőség*
   - **Leírás**: *A Windows 10-re vonatkozó megfelelőségi szabályzat*
   - **Platform**: Windows 10 és újabb

3. Kattintson a **Beállítások** > **Rendszerbiztonság** elemre a biztonsági beállítások megjelenítéséhez.

4. Configure the following options:

   - A **Jelszó szükséges a mobileszközök feloldásához** elemnél válassza a **Kötelező** lehetőséget. Ez a beállítás határozza meg, hogy a felhasználók csak jelszó beírása után férhessenek-e hozzá a mobileszközeiken lévő információkhoz.

   - A **jelszó minimális hosszát** állítsa **6** értékre. Ezzel a beállítással adható meg, hogy legalább hány számjegyből vagy karakterből kell állnia a jelszónak.

   ![Rendszerbiztonsági beállítások új eszközmegfelelőségi szabályzathoz](./media/quickstart-send-notification/system-security-settings-01.png)

5. Select **OK** > **OK** > **Create** to create your compliance policy.

6. Válassza a **Tulajdonságok** > **Meg nem felelés esetén végrehajtandó műveletek** > **Hozzáadás**. lehetőséget.

7. A **Művelet** legördülő menüben ellenőrizze, hogy az **E-mail küldése a végfelhasználóknak** lehetőség van kiválasztva.

8. Select **Message template**,  the template you created earlier in this article, and then **Select** to select the message template.

9. Select **ADD** > **OK** > **Save** to save your changes.

## <a name="assign-the-policy"></a>A szabályzat hozzárendelése

Megfelelőségi szabályzatot adott felhasználói csoportokhoz vagy minden felhasználóhoz hozzárendelhet. When Intune recognizes that a device is noncompliant, the user is notified that they must update their device to meet the compliance policy. Use the following steps to assign the policy.

1. In Intune go to **Devices** > **Compliance Policies** and select the **Windows 10 compliance** policy that you created earlier.

2. Válassza a **Hozzárendelések** lehetőséget.

3. A **Hozzárendelés a következőhöz** legördülő mezőben válassza a **Minden felhasználó** lehetőséget. Ez az összes felhasználót kiválasztja. Minden, **Windows 10 és újabb** verziós eszközt használó felhasználó, aki nem felel meg a megfelelőségi szabályzatnak, értesítést kap.

    > [!NOTE]
    > Belefoglalhat és kizárhat csoportokat a szabályzatok hozzárendelésénél.

4. Kattintson a **Mentés**gombra.

When you've successfully created and saved the policy, it will appear in the list of **Compliance policies - Policies**. A lista **Hozzárendelve** eleme **Igen** értékre van állítva.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban az Intune használatával létrehozott és hozzárendelt egy megfelelőségi szabályzatot az alkalmazottak Windows 10-eszközeihez, hogy legalább hat karakter hosszúságú jelszót kelljen hozzájuk megadni. További információ a megfelelőségi szabályzatok Windows-eszközökhöz való létrehozásáról: [Windowsos eszközök megfelelőségi szabályzatainak hozzáadása az Intune-ban](compliance-policy-create-windows.md).

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Ügyfélalkalmazás hozzáadása és hozzárendelése](../apps/quickstart-add-assign-app.md)
