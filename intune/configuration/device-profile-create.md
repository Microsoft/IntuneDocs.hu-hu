---
title: Eszközprofilok létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Add or configure a device configuration profile in Microsoft Intune. Select the platform type, configure the settings, add a scope tag.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c4c995322234a4a2486d8e6c5e9efd88f78dd63
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390874"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Eszközprofil létrehozása a Microsoft Intune-ban

Devices profiles allow you to add and configure settings, and then push these settings to devices in your organization. [Apply features and settings on your devices using device profiles](device-profiles.md) goes into more detail, including what you can do.

Ez a cikk:

- Lists the steps to create a profile.
- Shows you how to add a scope tag to "filter" the profile.
- Describes applicability rules on Windows 10 devices, and shows you how to create a rule.
- Lists the check-in refresh cycle times when devices receive profiles and any profile updates.

## <a name="create-the-profile"></a>A profil létrehozása

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Configuration profiles**. You have the following options:

    - **Overview**: Lists the status of your profiles, and provides additional details on the profiles you assigned to users and devices.
    - **Manage**: Create device profiles, upload custom [PowerShell scripts](../apps/intune-management-extension.md) to run within the profile, and add data plans to devices using [eSIM](esim-device-configuration.md).
    - **Monitor**: Check the status of a profile for success or failure, and also view logs on your profiles.
    - **Setup**: Add a SCEP or PFX certificate authority, or enable [Telecom Expense Management](telecom-expenses-monitor.md) in the profile.

3. Select **Create profile**. Adja meg a következő tulajdonságokat:

   - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **WP email profile for entire company**.
   - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
   - **Platform**: Choose the platform of your devices. A választható lehetőségek:  

       - **Android--**
       - **Vállalati Android**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 és újabb verziók**
       - **Windows 10 és újabb**

   - **Profile type**: Select the type of settings you want to create. The list shown depends on the **platform** you choose.
   - **Settings**: The following articles describe the settings for each profile type:

       - [Administrative templates](administrative-templates-windows.md)
       - [Egyéni](../custom-settings-configure.md)
       - [Delivery optimization](../delivery-optimization-windows.md)
       - [Eszközfunkciók](../device-features-configure.md)
       - [Eszközkorlátozások](device-restrictions-configure.md)
       - [Edition upgrade and mode switch](edition-upgrade-configure-windows-10.md)
       - [Education](education-settings-configure.md)
       - [Email](email-settings-configure.md)
       - [Endpoint Protection](../protect/endpoint-protection-configure.md)
       - [Identity protection](../protect/identity-protection-configure.md)  
       - [Kioszkmód](kiosk-settings.md)
       - [PKCS certificate](../protect/certficates-pfx-configure.md)
       - [PKCS imported certificate](../protect/certificates-imported-pfx-configure.md)
       - [Preference file](preference-file-settings-macos.md)
       - [SCEP certificate](../protect/certificates-scep-configure.md)
       - [Trusted certificate](../protect/certificates-configure.md)
       - [Update policies](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Információvédelem](../protect/windows-information-protection-configure.md)

     For example, if you select **iOS/iPadOS** for the platform, your profile type options look similar to the following profile:

     ![Create iOS profile in Intune](./media/device-profile-create/create-device-profile.png)

4. When finished, select **OK** > **Create** to save your changes. The profile is created, and shown in the list.

## <a name="scope-tags"></a>Hatókörcímkék

After you add the settings, you can also add a scope tag to the profile. Scope tags assign and filter policies to specific groups, such as HR or All US-NC employees.

For more information about scope tags, and what you can do, see [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Add a scope tag

1. Select **Scope (Tags)** .
2. Select **Add** to create a new scope tag. Or, select an existing scope tag from the list.
3. A módosítások mentéséhez válassza az **OK** gombot.

## <a name="applicability-rules"></a>Applicability rules

Applies to:

- Windows 10 és újabb

Applicability rules allow administrators to target devices in a group that meet specific criteria. For example, you create a device restrictions profile that applies to the **All Windows 10 devices** group. And, you only want the profile assigned to devices running Windows 10 Enterprise.

To do this task, create an **applicability rule**. These rules are great for the following scenarios:

- You use Windows 10 Education (EDU). At Bellows College, you want to target all Windows 10 EDU devices between RS3 and RS4.
- You want to target all users in Human Resources at Contoso, but only want Windows 10 Professional or Enterprise devices.

To approach these scenarios, you:

- Create a devices group that includes all devices at Bellows College. In the profile, add an applicability rule so it applies if the OS minimum version is `16299` and the maximum version is `17134`. Assign this profile to the Bellows College devices group.

  When it's assigned, the profile applies to devices between the minimum and maximum versions you enter. For devices that aren't between the minimum and maximum versions you enter, their status shows as **Not applicable**.

- Create a users group that includes all users in Human Resources (HR) at Contoso. In the profile, add an applicability rule so it applies to devices running Windows 10 Professional or Enterprise. Assign this profile to the HR users group.

  When it's assigned, the profile applies to devices running Windows 10 Professional or Enterprise. For devices that aren't running these editions, their status shows as **Not applicable**.

- If there are two profiles with the exact same settings, then the profile without an applicability rule is applied. 

  For example, ProfileA targets the Windows 10 devices group, enables BitLocker, and doesn’t have an applicability rule. ProfileB targets the same Windows 10 devices group, enables BitLocker, and has an applicability rule to only apply the profile to Windows 10 Enterprise.

  When both profiles are assigned, ProfileA is applied because it doesn’t have an applicability rule. 

When you assign the profile to the groups, the applicability rules act as a filter, and only target the devices that meet your criteria.

### <a name="add-a-rule"></a>Add a rule

1. Select **Applicability Rules**. You can choose the **Rule**, **Property**, and **OS edition**:

    ![Add an applicability rule to a device configuration profile in Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. In **Rule**, choose if you want to include or exclude users or groups. A választható lehetőségek:

    - **Assign profile if**: Includes users or groups that meet the criteria you enter.
    - **Don't assign profile if**: Excludes users or groups that meet the criteria you enter.

3. In **Property**, choose your filter. A választható lehetőségek: 

    - **OS edition**: In the list, check the Windows 10 editions you want to include (or exclude) in your rule.
    - **OS version**: Enter the **min** and **max** Windows 10 version numbers of you want to include (or exclude) in your rule. Both values are required.

      For example, you can enter `10.0.16299.0` (RS3 or 1709) for minimum version and `10.0.17134.0` (RS4 or 1803) for maximum version. Or, you can be more granular and enter `10.0.16299.001` for minimum version and `10.0.17134.319` for maximum version.

4. Select **Add** to save your changes.

## <a name="refresh-cycle-times"></a>Refresh cycle times

Intune uses different refresh cycles to check for updates to configuration profiles. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lists the estimated refresh times.

At any time, users can open the Company Portal app, and sync the device to immediately check for profile updates.

## <a name="recommendations"></a>Javaslatok

When creating profiles, consider the following recommendations:

- Name your policies so you know what they are, and what they do. All [compliance policies](../protect/create-compliance-policy.md) and [configuration profiles](../configuration/device-profile-create.md) have an optional **Description** property. In **Description**, be specific and include information so others know what the policy does.

  Some configuration profile examples include:

  **Profile name**: Admin template - OneDrive configuration profile for all Windows 10 users  
  **Profile description**: OneDrive admin template profile that includes the minimum and base settings for all Windows 10 users. Created by user@contoso.com to prevent users from sharing organizational data to personal OneDrive accounts.

  **Profile name**: VPN profile for all iOS users  
  **Profile description**: VPN profile that includes the minimum and base settings for all iOS users to connect to Contoso VPN. Created by user@contoso.com so users automatically authenticate to VPN, instead of prompting users for their username and password.

- Create your profile by its task, such as configure Microsoft Edge settings, enable Microsoft Defender anti-virus settings, block iOS jailbroken devices, and so on.

- Create profiles that apply to specific groups, such as Marketing, Sales, IT Administrators, or by location or school system.

- Separate user policies from device policies.

  For example, [Administrative Templates in Intune](administrative-templates-windows.md) have hundreds of ADMX settings. These template shows if a settings applies to users or devices. When creating admin templates, assign your users settings to a users group, and assign your device settings to a devices group.

  The following image shows an example of a setting that can apply to users and/or apply to devices:

  ![Intune admin template that applies to user and devices](./media/device-profile-create/setting-applies-to-user-and-device.png)

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
