---
title: Create device compliance policies in Microsoft Intune - Azure | Microsoft Docs
description: Create device compliance policies, overview of status and severity levels, using the InGracePeriod status, working with Conditional Access, handling devices without an assigned policy, and the differences in compliance in the Azure portal and classic portal in Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8452f9b56032864380ec703bfd444dc85ef129b
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188265"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Create a compliance policy in Microsoft Intune

Az eszközmegfelelőségi szabályzatok használata kiemelten fontos, ha az Intune-t a vállalat erőforrásainak védelmére kívánja használni. In Intune, you can create rules and settings that devices must meet to be considered compliant, such as a minimum OS version. If the device isn't compliant, you can then block access to data and resources using [Conditional Access](conditional-access.md).

You can also take actions for non-compliance, such as sending a notification email to the user. For an overview of what compliance policies do, and how they're used, see [get started with device compliance](device-compliance-get-started.md).

Ez a cikk:

- Lists the prerequisites and steps to create a compliancy policy.
- Shows you how to assign the policy to your user and device groups.
- Describes additional features, including scope tags to "filter" your policies, and steps you can take on devices that aren't compliant.
- Lists the check-in refresh cycle times when devices receive policy updates.

## <a name="before-you-begin"></a>Előkészületek

To use device compliance policies, be sure you:

- Használja az alábbi előfizetéseket:

  - Intune
  - If you use Conditional Access, then you need Azure Active Directory (AD) Premium edition. [Azure Active Directory pricing](https://azure.microsoft.com/pricing/details/active-directory/) lists what you get with the different editions. Intune compliance doesn't require Azure AD.

- Használjon támogatott platformot:

  - Android device administrator
  - Vállalati Android
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - WVPN-profilokdows Phone 8.1

- Enroll devices in Intune (required to see the compliance status)

- Enroll devices to one user, or enroll without a primary user. Devices enrolled to multiple users aren't supported.

## <a name="create-the-policy"></a>Create the policy

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Compliance policies** > **Create Policy**.

3. Specify the following properties:

   - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **Mark iOS jailbroken devices as not compliant**.

   - **Description**: Enter a description for the policy. A beállítás használata nem kötelező, de ajánlott.

   - **Platform**: Choose the platform of your devices. A választható lehetőségek:
     - **Android device administrator**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 és újabb verziók**
     - **Windows 10 és újabb**

     For *Android Enterprise*, you must then select a **Profile type**:
     - **Device owner**
     - **Work Profile**

   - **Settings**: The following articles list and describe the settings for each platform:
     - [Android device administrator](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 and later](compliance-policy-create-windows-8-1.md)
     - [Windows 10 és újabb](compliance-policy-create-windows.md)  

   - **Locations** *(Android device administrator)* : In your policy, you can force compliance by the location of the device. Choose from existing locations. Még nem rendelkezik hellyel? [Use Locations (network fence)](use-network-locations.md) in Intune provides some guidance.  

   - **Actions for noncompliance**: For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. Módosíthatja az eszköz nem megfelelőként való megjelölésének ütemezését, megadhatja például, hogy egy nap elteltével jelölje a rendszer nem megfelelőnek az eszközt. Hozzáadhat egy második műveletet is, amely e-mailt küld a felhasználónak, ha az eszköz nem megfelelő.

     A [Műveletek hozzáadása nem megfelelő eszközökhöz](actions-for-noncompliance.md) további információval szolgál, többek között arról, hogyan hozhat létre értesítési e-mailt a felhasználók számára.

     Például, a Helyek funkciót használja, és hozzáad egy helyet egy megfelelőségi szabályzatban. Az alapértelmezett meg nem felelési művelet alkalmazandó, ha kiválaszt legalább egy helyet. Ha az eszköz nem csatlakozik a megadott helyekhez, akkor azonnal nem megfelelőnek számít. Biztosíthat a felhasználóknak egy türelmi időszakot, például egy napot.

   - **Scope (Tags)** : Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.

4. When finished, select **OK** > **Create** to save your changes. The policy is created, and shown in the list. Next, assign the policy to your groups.

## <a name="assign-the-policy"></a>A szabályzat hozzárendelése

Once a policy is created, the next step is to assign the policy to your groups:

1. Choose a policy you created. Existing policies are in **Devices** > **Compliance policies** > **Policies**.

2. Select the *policy* > **Assignments**. Belefoglalhat vagy kizárhat Azure Active Directory (AD) biztonsági csoportokat.

3. Azure AD-biztonsági csoportjait a **Kijelölt csoportok** lehetőséget választva tekintheti meg. Select the groups you want this policy to apply > Choose **Save** to deploy the policy.

The users or devices targeted by your policy are evaluated for compliance when they check-in with Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Evaluate how many users are targeted

When you assign the policy, you can also **Evaluate** how many users are affected. This feature calculates users; it doesn't calculate devices.

1. In Intune, select **Devices** > **Compliance policies** > **Policies**.

2. Select a *policy* > **Assignments** > **Evaluate**. A message shows you how many users are targeted by this policy.

If the **Evaluate** button is grayed out, make sure the policy is assigned to one or more groups.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Refresh cycle times

Intune uses different refresh cycles to check for updates to compliance policies. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lists the estimated refresh times.

At any time, users can open the Company Portal app, and sync the device to immediately check for policy updates.

### <a name="assign-an-ingraceperiod-status"></a>Türelmi időszakban állapot hozzárendelése

A megfelelőségi szabályzatok Türelmi időszakban állapota egy érték. Ezt az értéket a rendszer az adott eszköz türelmi időszaka és az eszközre érvényes megfelelőségi szabályzat tényleges állapota alapján határozza meg.

Konkrétan, ha egy eszköz Nem megfelelő állapotú egy hozzárendelt megfelelőségi szabályzatra vonatkozóan, illetve:

- The device has no grace period assigned to it, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's expired, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's in the future, then the assigned value for the compliance policy is InGracePeriod

Az alábbi táblázat összefoglalja ezt részletesen:

|Aktuális megfelelőségi állapot|A hozzárendelt türelmi időszak értéke|Tényleges megfelelőségi állapot|
|---------|---------|---------|
|Nem megfelelő |Nincs hozzárendelve türelmi időszak |Nem megfelelő |
|Nem megfelelő |Tegnapi dátum|Nem megfelelő|
|Nem megfelelő |Holnapi dátum|Türelmi időszakban|

Az eszközmegfelelőségi szabályzatok figyelésével kapcsolatos további információkért lásd: [Intune-eszközmegfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Megfelelőségi szabályzat eredményül kapott állapotának hozzárendelése

Ha egy eszközhöz több megfelelőségi szabályzat tartozik, és az eszköz megfelelőségi állapota két vagy több hozzárendelt megfelelőségi szabályzat esetében eltérő, akkor egyetlen eredményül kapott megfelelőségi állapot lesz hozzárendelve. A hozzárendelés az egyes megfelelőségi állapotokhoz hozzárendelt fogalmi szintű súlyossági szinten alapul. Az egyes megfelelőségi állapotok a következő súlyossági szinttel rendelkeznek:

|Állapot  |Severity  |
|---------|---------|
|Ismeretlen     |1|
|Nem alkalmazható     |2|
|Compliant (Megfelelő)|3|
|Türelmi időszakban|4|
|Nem megfelelő|5|
|Hiba|6|

Ha egy eszköz több megfelelőségi szabályzattal rendelkezik, akkor az eszközhöz hozzárendelt összes szabályzaté közül a legmagasabb súlyossági szintet rendeli hozzá a rendszer az eszközhöz.

For example, a device has three compliance policies assigned to it: one Unknown status (severity = 1), one Compliant status (severity = 3), and one InGracePeriod status (severity = 4). The InGracePeriod status has the highest severity level. So, all three policies have the InGracePeriod compliance status.

## <a name="next-steps"></a>További lépések

[Monitor your policies](compliance-policy-monitor.md).
