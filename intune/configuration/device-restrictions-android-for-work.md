---
title: Android Enterprise device settings in Microsoft Intune - Azure | Microsoft Docs
description: On Android Enterprise or Android for Work devices, restrict settings on the device, including copy and paste, show notifications, app permissions, data sharing, password length, sign-in failures, use fingerprint to unlock, reuse passwords, and enable bluetooth sharing of work contacts. Configure devices as a dedicated device kiosk to run one app, or multiple apps.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25af87f2bd4eaf5371a1e1a1237298a6808f4f5e
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188180"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Android Enterprise device settings to allow or restrict features using Intune

This article lists and describes the different settings you can control on Android Enterprise devices. As part of your mobile device management (MDM) solution, use these settings to allow or disable features, run apps on dedicated devices, control security, and more.

## <a name="before-you-begin"></a>Előkészületek

[Create a device configuration profile](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Device owner only

### <a name="general-settings"></a>Általános beállítások

- **Screen capture**: Choose **Block** to prevent screenshots or screen captures on the device. Ezen kívül megakadályozza a tartalom megjelenítését a biztonságos videokimenettel nem rendelkező megjelenítő eszközökön. **Not configured** lets the user capture the screen contents as an image.
- **Camera**: Choose **Block** to prevent access to the camera on the device. **Not required** allows access to the device's camera.
- **Alapértelmezett engedélyezési szabályzat**: Ez a beállítás adja meg a futásidejű engedélykérésekre vonatkozó alapértelmezett engedélyezési szabályzatot. Lehetséges értékei többek között a következők:
  - **Eszköz alapértelmezése**: Az eszköz alapértelmezett beállításának használata.
  - **Rákérdezés**: A rendszer felszólítja a felhasználót az engedély jóváhagyására.
  - **Automatikus engedélyezés**: Az engedélyek automatikusan meg lesznek adva.
  - **Automatikus elutasítás**: Az engedélyek automatikusan meg lesznek tagadva.
- **Date and Time changes**: Choose **Block** to prevent users from manually setting the date and time. **Not configured** allows users to the set date and time on the device.
- **Volume changes**: **Block** prevents users from changing the device's volume, and also mutes the master volume. **Not configured** allows using the volume settings on the device.
- **Factory reset**: Choose **Block** to prevent users from using the factory reset option in the device's settings. **Not configured** allows users to use this setting on the device.
- **Csökkentett üzemmódú indítás**: A **Tiltás** lehetőség választásával megakadályozza a felhasználókat az eszköz csökkentett módban való újraindításában. **Not configured** allows users to reboot the device in safe mode.
- **Status bar**: Choose **Block** to prevent access to the status bar, including notifications and quick settings. **Not configured** allows users access to the status bar.
- **Roaming data services**: Choose **Block** to prevent data roaming over the cellular network. **Not configured** allows data roaming when the device is on a cellular network.
- **Wi-Fi setting changes**: Choose **Block** to prevent users from changing Wi-Fi settings created by the device owner. Users can create their own Wi-Fi configurations. **Not configured** allows users to change the Wi-Fi settings on the device.
- **Wi-Fi access point configuration**: Choose **Block** to prevent users from creating or changing any Wi-Fi configurations. **Not configured** allows users to change the Wi-Fi settings on the device.
- **Bluetooth configuration**: Choose **Block** to prevent users from configuring Bluetooth on the device. **Not configured** allows using Bluetooth on the device.
- **Tethering and access to hotspots**: Choose **Block** to prevent tethering and access to portable hotspots. **Not configured** allows tethering and access to portable hotspots.
- **USB storage**: Choose **Allow** to access USB storage on the device. **Not configured** prevents access to USB storage.
- **USB file transfer**: Choose **Block** to prevent transferring files over USB. **Not configured** allows transferring files.
- **External media**: Choose **Block** to prevent using or connecting any external media on the device. **Not configured** allows external media on the device.
- **Beam data using NFC**: Choose **Block** to prevent using the Near Field Communication (NFC) technology to beam data from apps. **Not configured** allows using NFC to share data between devices.
- **Debugging features**: Choose **Allow** to let users use debugging features on the device. **Not configured** prevents users from using the debugging features on the device.
- **Microphone adjustment**: Choose **Block** to prevent users from unmuting the microphone and adjusting the microphone volume. **Not configured** allows the user to use and adjust the volume of the microphone on the device.
- **Factory reset protection emails**: Choose **Google account email addresses**. Enter the email addresses of device administrators that can unlock the device after it's wiped. Be sure to separate the email addresses with a semi-colon, such as `admin1@gmail.com;admin2@gmail.com`. If an email isn't entered, anyone can unlock the device after it's restored to the factory settings. These emails only apply when a non-user factory reset is ran, such as running a factory reset using the recovery menu.
- **Network escape hatch**: Choose **Enable** to allow users to turn on the network escape hatch feature. If a network connection isn't made when the device boots, then the escape hatch asks to temporarily connect to a network and refresh the device policy. A szabályzat alkalmazása után a rendszer elfelejti az átmeneti hálózatot, és az eszköz folytatja a rendszerindítást. This feature connects devices to a network if:
  - There isn't a suitable network in the last policy.
  - The device boots into an app in lock task mode.
  - The user is unable to reach the device settings.

  **Not configured** prevents users from turning on the network escape hatch feature on the device.

- **System update**: Choose an option to define how the device handles over-the-air updates:
  - **Eszköz alapértelmezése**: Az eszköz alapértelmezett beállításának használata.
  - **Automatikus**: A rendszer automatikusan, felhasználói beavatkozás nélkül telepíti a frissítéseket. Ennek a szabályzatnak a beállításakor minden függőben lévő frissítés azonnal települ.
  - **Elhalasztva**: A frissítések 30 nappal el lesznek halasztva. At the end of the 30 days, Android prompts the user to install the update. Az eszközgyártók vagy a szolgáltatók megakadályozhatják (kivételként) a fontos biztonsági frissítések elhalasztását. A kivételként kezelt frissítések rendszerértesítést jelenítenek meg a felhasználó számára az eszközön.
  - **Karbantartási időszak**: Automatikusan telepíti a frissítéseket az Ön által az Intune-ban beállított napi karbantartási időszakban. Installation tries daily for 30 days, and can fail if there's insufficient space or battery levels. After 30 days, Android prompts the user to install. Ez az időszak szolgál a Play-alkalmazások frissítéseinek telepítésére is. Use this option for dedicated devices, such as kiosks, as single-app dedicated device foreground apps can be updated.

- **Notification windows**: When set to **Disable**, window notifications, including toasts, incoming calls, outgoing calls, system alerts, and system errors are not shown on the device. When set to **Not configured**, the operating system default is used, which may be to show notifications.
- **Skip first use hints**: Choose **Enable** to hide or skip suggestions from apps to step through tutorials or read any introductory hints when the app starts. When set to **Not configured**, the operating system default is used, which may be to show these suggestions when the app starts.

### <a name="system-security-settings"></a>A rendszer biztonsági beállításai

- **Threat scan on apps**: **Require** (default) enables Google Play Protect to scan apps before and after they’re installed. If it detects a threat, it may warn the user to remove the app from the device. **Not configured** doesn't enable or run Google Play Protect to scan apps.

### <a name="dedicated-device-settings"></a>Dedicated device settings

Use these settings to configure a kiosk-style experience on your dedicated devices. You can configure a device to run one app, or run many apps. When a device is set with kiosk mode, only the apps you add are available. These settings apply to Android Enterprise dedicated devices. They don't apply to Android Enterprise fully managed devices.

**Kiosk mode**: Choose if the device runs one app or runs multiple apps.

- **Single app**: Users can only access a single app on the device. When the device starts, only the specific app starts. A felhasználók nem nyithatnak meg új alkalmazásokat, és nem módosíthatják a futó alkalmazást.

  - **Select a managed app**: Select the managed Google Play app from the list.

    If you don't have any apps listed, then [add some Android apps](../apps/apps-add-android-for-work.md) to the device. Be sure to [assign the app to the device group created for your dedicated devices](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > When using single-app kiosk mode, dialer/phone apps may not function properly. 
  
- **Multi-app**: Users can access a limited set of apps on the device. When the device starts, only the apps you add start. You can also add some web links that users can open. When the policy is applied, users see icons for the allowed apps on the home screen.

  > [!IMPORTANT]
  > For multi-app dedicated devices, the [Managed Home Screen app](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) from Google Play **must be**:
  >   - [Added as a client app](../apps/apps-add-android-for-work.md) in Intune
  >   - [Assigned to the device group](../apps/apps-deploy.md) created for your dedicated devices
  >
  > The **Managed Home Screen** app isn't required to be in the configuration profile, but it is required to be added as a client app. When the **Managed Home Screen** app is added as a client app, any other apps you add in the configuration profile are shown as icons on the **Managed Home Screen** app.
  >
  > When using multi-app kiosk mode, dialer/phone apps may not function properly. 

  - **Add**: Select your apps from the list.

    If the **Managed Home Screen** app isn't listed, then [add it from Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Be sure to [assign the app](../apps/apps-deploy.md) to the device group created for your dedicated devices.

    You can also add other [Android apps](../apps/apps-add-android-for-work.md) and [web apps](../apps/web-app.md) created by your organization to the device. Be sure to [assign the app to the device group created for your dedicated devices](../apps/apps-deploy.md).

  - **Virtual home button**: A soft-key button that returns users to the Managed Home Screen so users can switch between apps. A választható lehetőségek:

    - **Not configured** (default): A home button isn't shown. Users must use the back button to switch between apps.
    - **Swipe up**: A home button shows when a user swipes up on the device.
    - **Floating**: Shows a persistent, floating home button on the device.

  - **Leave kiosk mode**: Choose **Enable** to allow Administrators to temporarily pause kiosk mode to update the device. To use this feature, the administrator:
  
    1. Continues to select the back button until the **Exit kiosk** button is shown. 
    2. Selects the **Exit kiosk** button, and enters the **Leave kiosk mode code** PIN.
    3. When finished, select the **Managed Home Screen** app. This step relocks the device into multi-app kiosk mode.

      When set to **Not configured**, administrators can't pause kiosk mode. If the administrator continues to select the back button, and selects the **Exit kiosk** button, then a message states that a passcode is required.

    - **Leave kiosk mode code**: Enter a 4-6 digit numeric PIN. The administrator uses this PIN to temporarily pause kiosk mode.

  - **Set custom URL background**: Enter a URL to customize the background screen on the dedicated device.

    > [!NOTE]
    > For most cases, we recommend starting with images of at least the following sizes:
    >
    > - Phone: 1080x1920 px
    > - Tablet: 1920x1080 px
    >
    > For the best experience and crisp details, it’s suggested that per device image assets be created to the display specifications.
    >
    > Modern displays have higher pixel densities and can display equivalent 2K/4K definition images.

  - **Wi-Fi configuration**: **Enable** shows the Wi-Fi control on the Managed Home Screen, and allows end users to connect the device to different WiFi networks. Enabling this feature also turns on device location. **Not configured** (default) doesn't show the Wi-Fi control on the Managed Home Screen. It prevents users from connecting to Wi-Fi networks while using the Managed Home Screen.

  - **Bluetooth configuration**: **Enable** shows the Bluetooth control on the Managed Home Screen, and allows end users to pair devices over Bluetooth. Enabling this feature also turns on device location. **Not configured** (default) doesn't show the Bluetooth control on the Managed Home Screen. It prevents users from configuring Bluetooth and pairing devices while using the Managed Home Screen.

  - **Flashlight access**: **Enable** shows the flashlight control on the Managed Home Screen, and allows end users to turn the flashlight on or off. **Not configured** (default) doesn't show the flashlight control on Managed Home Screen. It prevents users from using the flashlight while using the Managed Home Screen.

  - **Media volume control**: **Enable** shows the media volume control on the Managed Home Screen, and allows end users to adjust the device's media volume using a slider. **Not configured** (default) doesn't show the media volume control on Managed Home Screen. It prevents users from adjusting the device's media volume while using the Managed Home Screen, unless their hardware buttons support it. 

  - **Screen saver mode**: **Enable** shows a screensaver on the Managed Home Screen when the device is locked or times out. **Not configured** (default) doesn't show a screensaver on the Managed Home Screen.

    When enabled, also configure:

    - **Set custom screen saver image**: Enter the URL to a custom PNG, JPG, JPEG, GIF, BMP, WebP, or ICOimage. For example, enter:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.webp`

      If you don't enter a URL, then the device's default image is used, if there is a default image.
      
      > [!TIP]
      > Any file resource URL that can be turned into a bitmap is supported.

    - **Number of seconds the device shows screen saver before turning off screen**: Choose how long the device shows the screensaver. Enter a value between 0-9999999 seconds. Default is `0` seconds. When left blank, or set to zero (`0`), the screen saver is active until a user interacts with the device.
    - **Number of seconds the device is inactive before showing screen saver**: Choose how long the device is idle before showing the screensaver. Enter a value between 1-9999999 seconds. Default is `30` seconds. You must enter a number greater than zero (`0`).
    - **Detect media before starting screen saver**: **Enable** (default) doesn't show the screen saver if audio or video is playing on the device. **Not configured** shows the screen saver, even if audio or video is playing.

### <a name="device-password-settings"></a>Eszköz jelszóbeállításai

- **Disable lock screen**: Choose **Disable** to prevent users from using Keyguard lock screen feature on the device. **Not configured** allows the user to use the Keyguard features.
- **Disabled lock screen features**: When keyguard is enabled on the device, choose which features to disable. For example, when **Secure camera** is checked, the camera feature is disabled on the device. Any features not checked are enabled on the device.

  These features are available to users when the device is locked. Users won't see or access features that are checked.

- **Megkövetelt jelszótípus**: Adja meg az eszközön megkövetelt jelszótípust. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Password required, no restrictions**
  - **Weak biometric**: [Strong vs. weak biometrics](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (opens Android's web site)
  - **Numeric**: Password must only be numbers, such as `123456789`. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Numeric complex**: Repeated or consecutive numbers, such as "1111" or "1234", aren't allowed. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Alphabetic**: Letters in the alphabet are required. Numbers and symbols aren't required. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Alphanumeric**: Includes uppercase letters, lowercase letters, and numeric characters. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Alphanumeric with symbols**: Includes uppercase letters, lowercase letters, numeric characters, punctuation marks, and symbols. Ezt is adja meg:

    - **Minimum password length**: Enter the minimum length the password must have, between 4 and 16 characters.
    - **Number of characters required**: Enter the number of characters the password must have, between 0 and 16 characters.
    - **Number of lowercase characters required**: Enter the number of lowercase characters the password must have, between 0 and 16 characters.
    - **Number of uppercase characters required**: Enter the number of uppercase characters the password must have, between 0 and 16 characters.
    - **Number of non-letter characters required**: Enter the number of non-letters (anything other than letters in the alphabet) the password must have, between 0 and 16 characters.
    - **Number of numeric characters required**: Enter the number of numeric characters (`1`, `2`, `3`, and so on) the password must have, between 0 and 16 characters.
    - **Number of symbol characters required**: Enter the number of symbol characters (`&`, `#`, `%`, and so on) the password must have, between 0 and 16 characters.

- **Number of days until password expires**: Enter the number of days, between 1-365, until the device password must be changed. For example, to change the password after 60 days, enter `60`. When the password expires, users are prompted to create a new password.
- **Number of passwords required before user can resuse a password**: Enter the number of recent passwords that can't be reused, between 1-24. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.
- **Number of sign-in failures before wiping device**: Enter the number, between 4-11, of failed sign-ins to allow before the device is wiped.

### <a name="power-settings"></a>Energiaellátási beállítások

- **Time to lock screen**: Enter the maximum time a user can set until the device locks. For example, if you set this setting to **10 minutes**, then users can set the time from 15 seconds up to 10 minutes. When set to **Not configured** (default), Intune doesn't change or control this setting.

- **Bekapcsolt képernyő, amikor az eszköz áramforráshoz van csatlakoztatva**: Válassza ki, mely áramforrások csatlakoztatásakor maradjon bekapcsolva az eszköz képernyője.

### <a name="users-and-accounts-settings"></a>Felhasználói és fiókbeállítások

- **Új felhasználók hozzáadása**: Válassza a **Tiltás** lehetőséget, hogy megakadályozza a felhasználókat új felhasználók hozzáadásában. Each user has a personal space on the device for custom Home screens, accounts, apps, and settings. **Not configured** allows users to add other users to the device.
- **Felhasználó eltávolítása**: Válassza a **Tiltás** lehetőséget, hogy megakadályozza a felhasználókat felhasználók eltávolításában. **Not configured** allows users to remove other users from the device.
- **Fiókmódosítások**: Válassza a **Tiltás** lehetőséget, hogy megakadályozza a felhasználókat a fiókok módosításában. **Not configured** allows users to update user accounts on the device.

  > [!NOTE]
  > This setting isn't honored on device owner (fully managed) devices. If you configure this setting, then the setting is ignored, and has no impact.

### <a name="applications"></a>Alkalmazások

- **Allow installation from unknown sources**: Choose **Allow** so users can turn on **Unknown sources**. This setting allows apps to install from unknown sources, including sources other than the Google Play Store. **Not configured** prevents users from turning on **Unknown sources**.
- **Allow access to all apps in Google Play store**: When set to **Allow**, users get access to all apps in Google Play store. They don't get access to the apps the administrator blocks in [Client Apps](../apps/apps-add-android-for-work.md). **Not configured** forces users to only access the apps the administrator makes available Google Play store, or apps required in [Client Apps](../apps/apps-add-android-for-work.md).
- **App auto-updates**: Choose when automatic updates are installed. A választható lehetőségek:
  - **Nincs konfigurálva**
  - **User choice**
  - **Never**
  - **Wi-Fi only**
  - **Always**

### <a name="connectivity"></a>Connectivity

- **Mindig bekapcsolt VPN**: Az **Engedélyezés** beállítással a VPN-ügyfél automatikusan csatlakozik és újracsatlakozik a VPN-hez. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal elindítható, ha a felhasználó zárolja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. 

  A mindig bekapcsolt VPN beállítás az összes VPN-ügyfél számára való letiltásához válassza a **Nincs konfigurálva** lehetőséget.

  > [!IMPORTANT]
  > Egy eszközön egyszerre csak egy mindig bekapcsolt VPN-szabályzatot helyezzen üzembe. Több ilyen szabályzat üzembe helyezése egyetlen eszközön nem támogatott.

- **VPN-ügyfél**: Válasszon egy Mindig bekapcsolt állapotot támogató VPN-ügyfelet. A választható lehetőségek:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Hálózatok GlobalProtect
  - Pulse Secure
  - Egyéni
    - **Csomagazonosító**: Adja meg az alkalmazás csomagazonosítóját a Google Play Áruházban. Ha például az áruházban levő alkalmazás URL-címe `https://play.google.com/store/details?id=com.contosovpn.android.prod`, a csomagazonosító `com.contosovpn.android.prod` lesz.

  > [!IMPORTANT]
  > - A kiválasztott VPN-ügyfelet az eszközön kell telepíteni, és támogatnia kell az alkalmazásonkénti VPN-t a munkahelyi profilokban. Ellenkező esetben hiba történik. 
  > - A VPN-ügyfélalkalmazást jóvá kell hagynia a **felügyelt Google Play Áruházban**, szinkronizálnia kell az alkalmazást az Intune-nal, majd üzembe helyeznie az eszközön. Ezt követően az alkalmazás telepítve lesz a felhasználó munkahelyi profiljában.
  > - There may be known issues when using per-app VPN with F5 Access for Android 3.0.4. See [F5's release notes for F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) for more information.

- **Lockdown mode**: Choose **Enable** to force all network traffic to use the VPN tunnel. Ha a VPN-kapcsolat nincs kiépítve, az eszköznek nem lesz hálózati hozzáférése.

  A **Nincs konfigurálva** beállítással a forgalom a VPN-alagúton vagy a mobilhálózaton is áthaladhat.

- **Recommended global proxy**: Choose **Enable** to add a global proxy to the devices. When enabled, HTTP and HTTPS traffic, including some apps on the device, use the proxy you enter. This proxy is only a recommendation. It's possible some apps won't use the proxy. **Not configured** (default) doesn't add a recommended global proxy.

  For more information on this feature, see [setRecommendedGlobalProxy](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setRecommendedGlobalProxy(android.content.ComponentName,%20android.net.ProxyInfo)) (opens an Android site).

  When enabled, also enter the **Type** of proxy. A választható lehetőségek:

  - **Direct**: Choose this option to manually enter the proxy server details, including:
    - **Host**: Enter the hostname or IP address of your proxy server. Például írja be a következőt: `proxy.contoso.com` vagy `127.0.0.1`.
    - **Port number**: Enter the TCP port number used by the proxy server. Például írja be a következőt: `8080`.
    - **Excluded hosts**: Enter a list of host names or IP addresses that won't use the proxy. This list can include an asterisk (`*`) wildcard and multiple hosts separated by semicolons (`;`) with no spaces. Például írja be a következőt: `127.0.0.1;web.contoso.com;*.microsoft.com`.

  - **Proxy Auto-Config**: Enter the **PAC URL** to a proxy auto-configuration script. Például írja be a következőt: `https://proxy.contoso.com/proxy.pac`.

    For more information on PAC files, see [Proxy Auto-Configuration (PAC) file](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (opens a non-Microsoft site).

## <a name="work-profile-only"></a>Csak munkahelyi profil

### <a name="work-profile-settings"></a>Munkahelyi profil beállításai

#### <a name="general"></a>Általános

- **Copy and paste between work and personal profiles**: Choose **Block** to prevent copy-and-paste between work and personal apps. **Not configured** allows users to share data using copy-and-paste with apps in the personal profile 
- **Data sharing between work and personal profiles**: Choose if apps in the work profile can share with apps in the personal profile. For example, you can control sharing actions within applications, such as the **Share…** lehetőséget a Chrome böngészőalkalmazásban). Ez a beállítás nem vonatkozik a másolás/beillesztés vágólapi viselkedésre. Your sharing options:
  - **Device default**: The default sharing behavior of the device, which varies depending on the Android version. Alapértelmezés szerint a személyes profilból lehet a munkahelyi profilba adatokat megosztani, a munkahelyiből a személyesbe viszont nem. A beállítás célja a munkahelyi profilból a személyesbe irányuló adatmegosztás megelőzése. A Google a 6.0-snál újabb verziójú eszközökön nem nyújt lehetőséget a személyesből a munkahelyi profilba irányuló adatmegosztás blokkolására.
  - **A munkahelyi profilban lévő alkalmazások kezelhetik a személyes profilból érkező megosztási kérelmeket**: Engedélyezi a személyesből a munkahelyi profilba irányuló adatmegosztásra szolgáló beépített Android-funkciót. Engedélyezéskor a személyes profil alkalmazásaiból származó megosztási kérések kezdeményezhetnek adatmegosztást a munkahelyi profil alkalmazásaival. A 6.0-snál korábbi verziójú androidos eszközökön ez az alapértelmezett beállítás.
  - **Prevent any sharing across boundaries**: Prevents sharing between work and personal profiles.
  - **No restrictions on sharing**: Enables sharing across the work profile boundary in both directions. Ilyenkor a munkahelyi profilban szereplő alkalmazások megoszthatnak adatokat a személyes profi jelöletlen alkalmazásaival. A beállítással lehetővé teszi a munkahelyi profil alkalmazásainak az adatmegosztást az eszköz nem felügyelt részével. Így körültekintően használja ezt a lehetőséget.

- **Work profile notifications while device locked**: Controls whether apps in the work profile can show data in notifications when the device is locked. **Block** doesn't show the data. **Not configured** shows the data.
- **Alapértelmezett alkalmazásengedélyek**: Itt adhatja meg a munkahelyi profilban található összes alkalmazásra vonatkozó alapértelmezett engedélyszabályzatot. Az Android 6-os verziójától kezdve a rendszer alkalmazásindításkor felszólítja a felhasználót az alkalmazás által megkövetelt, konkrét engedélyek megadására. Ezzel a szabályzatbeállítással döntheti el, hogy a felhasználók megadhatják-e a munkahelyi profilban szereplő összes alkalmazás engedélyeit. Hozzárendelhet például egy olyan alkalmazást a munkahelyi profilhoz, amely helyadatokhoz kér hozzáférést. Általában az alkalmazás kéri a felhasználót a helyadatokhoz való hozzáférés megadására vagy elutasítására. Ezzel a szabályzattal kérdés nélkül automatikusan engedélyezhet vagy letilthat minden hozzáférést, vagy átadhatja a döntés jogát a felhasználónak. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Rákérdezés**
  - **Automatikus engedélyezés**
  - **Automatikus elutasítás**

  Alkalmazáskonfigurációs szabályzatokkal is engedélyeket adhat egyes alkalmazásoknak (**Ügyfélalkalmazások** > **Alkalmazáskonfigurációs szabályzatok**).

- **Add and remove accounts**: Choose **Block** to prevent end users from manually adding or removing accounts in the work profile. Ha például a Gmail alkalmazást androidos munkahelyi profilban telepíti, megakadályozhatja, hogy a végfelhasználók fiókokat adjanak hozzá vagy távolítsanak el ebben a munkaprofilban. **Not configured** allows adding accounts in the work profile.  

- **Névjegyek megosztása Bluetooth-kapcsolattal**: Engedélyezi egy másik Bluetooth-eszköz (például egy autó) a munkahelyi névjegyekhez való hozzáférését. Alapértelmezés szerint ez a beállítás nincs konfigurálva, a munkahelyi névjegyek pedig nem jelennek meg. A megosztás engedélyezéséhez és a munkahelyi profil névjegyeinek megjelenítéséhez válassza az **Engedélyezés** lehetőséget. Ez a beállítás az Android munkahelyi profilos, Android v6.0 és újabb operációs rendszerekkel rendelkező eszközökre vonatkozik. A beállítás engedélyezésével megengedheti bizonyos Bluetooth-eszközöknek, hogy az első kapcsolat alkalmával gyorsítótárazzák a munkahelyi kapcsolatokat. Ennek a szabályzatnak az eredeti párosítás/szinkronizálás utáni letiltása nem feltétlenül távolítja el a munkahelyi kapcsolatokat a Bluetooth-eszközről.

- **Screen capture**: Choose **Block** to prevent screenshots or screen captures on the device in the work profile. Ezen kívül megakadályozza a tartalom megjelenítését a biztonságos videokimenettel nem rendelkező megjelenítő eszközökön. **Not configured** allows getting screenshots.

- **Display work contact caller-id in personal profile**: When enabled (**Not configured**), the work contact caller details are displayed in the personal profile. When set to **Block**, the work contact caller number isn't displayed in the personal profile. Az Android operációs rendszer 6.0-ás és újabb verzióira vonatkozik.

- **Search work contacts from personal profile**: Choose **Block** to prevent users from searching for work contacts in apps in the personal profile. **Not required** allows searching for work contacts in the personal profile.

- **Camera**: Choose **Block** to prevent access to the camera on the device in the work profile. A beállítás nincs hatással a fényképezőkép személyes profilban való használatára. **Not required** allows access to the camera in the work profile.

- **Allow widgets from work profile apps**: **Enable** allows end users to put widgets exposed by apps on the home screen. A **Nincs konfigurálva** (alapértelmezett) érték letiltja a funkciót.

  For example, Outlook is installed on your users' work profiles. When set to **Enable**, users can put the agenda widget on the device home screen.

#### <a name="work-profile-password"></a>Work Profile Password

- **Munkahelyi profilhoz tartozó jelszó megkövetelése**: Az engedélyezett munkahelyi profillal rendelkező Android 7.0-s és újabb verziójú eszközökre vonatkozik. Choose **Require** to enter a passcode policy that applies only to the apps in the work profile. Alapértelmezés szerint a végfelhasználónak lehetősége van két külön-külön definiált PIN-kód használatára, vagy a felhasználók dönthetnek úgy, hogy a két meghatározott PIN-kód összevonásával csak az erősebbet használják. **Not configured** allows the user to use work apps, without entering a password.
- **Jelszó minimális hossza**: Itt adhatja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát (**4**-**16**).
- **A munkahelyi profil zárolása legfeljebb ennyi perc inaktivitás után**: Itt adhatja meg, hogy mennyi idő után zárolódjon a munkahelyi profil. A felhasználónak ezután meg kell adnia a hitelesítő adatait a hozzáférés visszanyeréséhez.
- **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**: Itt adhatja meg, hogy hányszor lehet helytelen jelszót megadni, mielőtt a rendszer törölné az eszközről a munkahelyi profil összes adatát.
- **Jelszó érvényessége (nap)** : Itt adhatja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát (**1**-**255**).
- **Kötelező jelszótípus**: Itt adhatja meg az eszközön beállítandó jelszó típusát. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Kötelező**
  - **Legalább számok**
  - **Komplex numerikus**: Nem lehet ismétlődő vagy egymást követő számokat megadni, például az „1111-et” vagy az „1234-et”
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Itt adhatja meg, hogy hány új jelszót kell beállítani, mielőtt egy korábbit újból használhatna (**1**-**24**).
- **Fingerprint unlock**: Choose **Block** to prevent end users from using the device fingerprint scanner to unlock the device. **Not configured** allows users to unlock devices with a fingerprint in the work profile.
- **Smart Lock and other trust agents**: Choose **Block** to prevent Smart Lock or other trust agents from adjusting lock screen settings on compatible devices. This feature, sometimes known as a trust agent, lets you disable or bypass the device lock screen password if the device is in a trusted location. Így például megkerülheti a munkahelyi profil jelszavát abban az esetben, ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címke közelében van. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.

### <a name="device-password"></a>Eszköz jelszava

These password settings apply to personal profiles on devices that use a work profile.

- **Jelszó minimális hossza**: Itt adhatja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát (**4**-**14**).
- **Képernyőzárolás legfeljebb ennyi perc inaktivitás után**: Itt adhatja meg, hogy mennyi idő után zárolódjanak a tétlen eszközök
- **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**: Itt adhatja meg, hogy hányszor lehet helytelen jelszót megadni, mielőtt a rendszer törölné az eszközről az adatokat
- **Jelszó érvényessége (nap)** : Itt adhatja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát (**1**-**255**)
- **Kötelező jelszótípus**: Itt adhatja meg az eszközön beállítandó jelszó típusát. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Kötelező**
  - **Legalább számok**
  - **Komplex numerikus**: Nem lehet ismétlődő vagy egymást követő számokat megadni, például az „1111”-et vagy az „1234”-et
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Itt adhatja meg, hogy hány új jelszót kell beállítani, mielőtt egy korábbit újból használhatna (**1**-**24**).
- **Fingerprint unlock**: Choose **Block** to prevent end user from using the device fingerprint scanner to unlock the device. **Not configured** allows the user to unlock the device using a fingerprint.
- **Smart Lock and other trust agents**: Choose **Block** to prevent Smart Lock or other trust agents from adjusting lock screen settings on compatible devices. This feature, sometimes known as a trust agent, lets you disable or bypass the device lock screen password if the device is in a trusted location. Így például megkerülheti a munkahelyi profil jelszavát abban az esetben, ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címke közelében van. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.

### <a name="system-security"></a>System security

- **Threat scan on apps**: **Require** enforces that the **Verify Apps** setting is enabled for work and personal profiles.

   > [!Note]
   > This setting only works for devices that are Android 8 (Oreo) and above.

- **Prevent app installations from unknown sources in the personal profile**: By design, Android Enterprise work profile devices can't install apps from sources other than the Play Store. By nature, work profile devices are intended to be dual-profile:

  - A work profile managed using MDM.
  - A personal profile that's isolated from MDM management.

  This setting allows administrators more control of app installations from unknown sources. **Not configured** (default) allows app installations from unknown sources in the personal profile. **Block** prevents app installations from sources other than the Play Store in the personal profile.

### <a name="connectivity"></a>Connectivity

- **Mindig bekapcsolt VPN**: Az **Engedélyezés** beállítással a VPN-ügyfél automatikusan csatlakozik és újracsatlakozik a VPN-hez. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal elindítható, ha a felhasználó zárolja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. 

  A mindig bekapcsolt VPN beállítás az összes VPN-ügyfél számára való letiltásához válassza a **Nincs konfigurálva** lehetőséget.

  > [!IMPORTANT]
  > Egy eszközön egyszerre csak egy mindig bekapcsolt VPN-szabályzatot helyezzen üzembe. Több ilyen szabályzat üzembe helyezése egyetlen eszközön nem támogatott.

- **VPN-ügyfél**: Válasszon egy Mindig bekapcsolt állapotot támogató VPN-ügyfelet. A választható lehetőségek:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Hálózatok GlobalProtect
  - Pulse Secure
  - Egyéni
    - **Csomagazonosító**: Adja meg az alkalmazás csomagazonosítóját a Google Play Áruházban. Ha például az áruházban levő alkalmazás URL-címe `https://play.google.com/store/details?id=com.contosovpn.android.prod`, a csomagazonosító `com.contosovpn.android.prod` lesz.

  > [!IMPORTANT]
  > - A kiválasztott VPN-ügyfelet az eszközön kell telepíteni, és támogatnia kell az alkalmazásonkénti VPN-t a munkahelyi profilokban. Ellenkező esetben hiba történik. 
  > - A VPN-ügyfélalkalmazást jóvá kell hagynia a **felügyelt Google Play Áruházban**, szinkronizálnia kell az alkalmazást az Intune-nal, majd üzembe helyeznie az eszközön. Ezt követően az alkalmazás telepítve lesz a felhasználó munkahelyi profiljában.
  > - There may be known issues when using per-app VPN with F5 Access for Android 3.0.4. See [F5's release notes for F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) for more information.

- **Lockdown mode**: Choose **Enable** to force all network traffic to use the VPN tunnel. Ha a VPN-kapcsolat nincs kiépítve, az eszköznek nem lesz hálózati hozzáférése.

  A **Nincs konfigurálva** beállítással a forgalom a VPN-alagúton vagy a mobilhálózaton is áthaladhat.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

You can also create dedicated device kiosk profiles for [Android](device-restrictions-android.md#kiosk) and [Windows 10](kiosk-settings.md) devices.

## <a name="see-also"></a>További információ

[Configuring and troubleshooting Android enterprise devices in Microsoft Intune](https://support.microsoft.com/help/4476974)
