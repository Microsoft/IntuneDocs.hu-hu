---
title: Egyéni alkalmazásonkénti Androidos VPN-profil
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan hozhat létre alkalmazásonkénti VPN-profilt a Microsoft Intune-nal felügyelt Android-eszközökhöz.
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
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62f418e396c5030a47ea0bcb31914cd4e1069c40
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319844"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Alkalmazásonkénti VPN-profil létrehozása androidos eszközökhöz egyéni Microsoft Intune-profillal

Az Intune által felügyelt Android 5.0-s és újabb rendszerű eszközökhöz alkalmazásonkénti VPN-profilt hozhat létre. Először hozzon létre egy olyan VPN-profit, amely a Pulse Secure vagy a Citrix kapcsolattípust használja. Ezután hozzon létre egy olyan egyéni szabályzatot, amely a VPN-profilt meghatározott alkalmazásokkal társítja.

> [!NOTE]
> To use per-app VPN on Android Enterprise devices, you can also use these steps. But, it's recommended to use an [app configuration policy](../apps/app-configuration-policies-use-android.md) for your VPN client app.

Miután hozzárendeli a szabályzatot az Android rendszerű eszközhöz vagy felhasználócsoportokhoz, a felhasználóknak el kell indítaniuk a PulseSecure vagy a Citrix VPN-ügyfelet. A VPN-ügyfél ezután csak a megadott alkalmazások adatforgalma számára engedélyezi a nyitott VPN-kapcsolat használatát.

> [!NOTE]
>
> Ez a profil csak a Pulse Secure és a Citrix kapcsolattípust támogatja.

## <a name="step-1-create-a-vpn-profile"></a>1\. lépés: VPN-profil létrehozása

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
3. Adja meg a következő tulajdonságokat:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Android per-app VPN profile for entire company**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Select **Android**.
    - **Profile type**: Select **VPN**.

4. Válassza a **Beállítások** > **Konfigurálás** lehetőséget. Then, configure the VPN profile. For more information, see [How to configure VPN settings](vpn-settings-configure.md) and [Intune VPN settings for Android devices](vpn-settings-android.md).

Jegyezze le a VPN-profil létrehozásakor megadott **Kapcsolat neve** értéket. Erre szükség lesz a következő lépésben. Például: **AlkVpnProfil**.

## <a name="step-2-create-a-custom-configuration-policy"></a>2\. lépés: Egyéni konfigurációs szabályzat létrehozása

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
3. Adja meg a következő tulajdonságokat:

    - **Name**: Enter a descriptive name for the custom profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Custom OMA-URI Android VPN profile for entire company**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Select **Android**.
    - **Profile type**: Select **Custom**.

4. Válassza a **Beállítások** > **Konfigurálás** lehetőséget.
5. Az **Egyéni OMA-URI beállítások** panelen válassza a **Hozzáadás** lehetőséget.
    - **Name**: Enter a name for your setting.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **OMA-URI**: Enter `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, where *Name* is the connection name you noted in Step 1. In this example, the string is `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Data type**: Enter **String**.
    - **Value**: Enter a semicolon-separated list of packages to associate with the profile. For example, if you want Excel and the Google Chrome browser to use the VPN connection, enter `com.microsoft.office.excel;com.android.chrome`.

![Példa Android rendszerű, alkalmazásonkénti VPN-hez létrehozott egyéni szabályzatra](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Az alkalmazáslista Blacklist (Letiltott) vagy Whitelist (Engedélyezett) értékre állítása (nem kötelező)

Use the **BLACKLIST** value to enter a list of apps that *cannot* use the VPN connection. Minden más alkalmazás VPN-kapcsolaton keresztül fog csatlakozni az internethez. Or, use the **WHITELIST** value to enter a list of apps that *can* use the VPN connection. Apps that aren't on the list don't connect through the VPN.

1. Az **Egyéni OMA-URI beállítások** panelen válassza a **Hozzáadás** lehetőséget.
2. Adja meg a beállítás nevét.
3. In **OMA-URI**, enter `./Vendor/MSFT/VPN/Profile/*Name*/Mode`, where *Name* is the VPN profile name you noted in Step 1. In our example, the string is `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. In **Data type**, enter **String**.
5. Az **Érték** mezőbe írja be a **BLACKLIST** (LETILTOTT) vagy a **WHITELIST** (ENGEDÉLYEZETT) értéket.

## <a name="step-3-assign-both-policies"></a>3\. lépés: Mindkét szabályzat hozzárendelése

[Assign both device profiles](device-profile-assign.md) to the required users or devices.
