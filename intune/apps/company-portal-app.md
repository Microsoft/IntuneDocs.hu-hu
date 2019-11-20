---
title: A Céges portál alkalmazás konfigurálása
titleSuffix: Microsoft Intune
description: Learn how you can apply company-specific branding to the Intune Company Portal app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b750c09207b1950aa27a5f2cae1267503537b6e7
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199197"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>A Microsoft Intune Céges portál alkalmazásának konfigurálása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A felhasználók a Microsoft Intune Céges portálon férhetnek hozzá a vállalati adatokhoz, és olyan gyakori feladatokat hajthatnak végre, mint például az eszközök regisztrálása, az alkalmazások telepítése és az informatikai támogatási információk megtekintése. Additionally, the company portal app allows user to securely access company resources. The company portal app provides several different pages, such as Home, Apps, App details, Devices, and Device details. To quickly find apps within the Company Portal, you can filter the apps on the Apps page.

> [!IMPORTANT]
> To support Google’s Firebase Cloud Messaging (FCM), you must update your Android Company Portal app to the latest version.  

> [!Tip]
> A vállalati portál testreszabása a vállalati portál webhelyére és a vállalati portál alkalmazásaira egyaránt hatással van. Note that users must have an Intune license assigned to access the Company Portal website.

By customizing the Company Portal, you will help provide a familiar and helpful experience for your end users. To do this, in the Intune portal, select **Client apps** > **Branding and customization**, and then configure the required settings.

When a user is installing an iOS application from the Company Portal they will receive a prompt. This occurs when the iOS app is linked to the app store, linked to a volume-purchase program (VPP), or linked to a line-of-business (LOB) app. The prompt allows the users to accept the action or allow management of the app. The prompt will display your company name, or when your company name is unavailable, **Company Portal** will be displayed. 

> [!Note]
> Az Azure Government használata esetében a végfelhasználó alkalmazásnaplókkal döntheti el, hogy hogyan végzi a megosztást, amikor segítségkérési folyamatot indít el egy probléma kapcsán. Ha azonban nem az Azure Governmentet használja, akkor a Windows 10 Céges portál közvetlenül a Microsoftnak küldi az alkalmazásnaplókat, amikor egy felhasználó segítségkérési folyamatot indít el egy probléma kapcsán. Az alkalmazásnaplók Microsoftnak való elküldésével könnyebben háríthatók el és oldhatók meg a problémák. 

## <a name="company-information-and-privacy-statement"></a>A vállalat adatai és adatvédelmi nyilatkozata
A vállalat neve a Vállalati portál címeként jelenik meg. Az adatvédelmi nyilatkozat az Adatvédelem hivatkozásra kattintva jeleníthető meg.

| Mező neve | Maximális hossz | További információ |
|---|---|---|
|**Vállalat neve**| 40 | Ez a név a Céges portál címeként jelenik meg, és az Intune használata alatt végig szöveges formában olvasható. |
| **Az adatvédelmi nyilatkozat URL-címe** |     79     | Itt adhatja meg vállalatának adatvédelmi nyilatkozatát, amely akkor jelenik meg, ha a felhasználó a Vállalati portál adatvédelmi hivatkozásaira kattint. Érvényes URL-címet kell megadnia, a következő formátumban: `<https://www.contoso.com>`. |

> [!NOTE]
> Consistent with Microsoft and Apple policy, we do not sell any data collected by our service to any third parties for any reason.

## <a name="support-information"></a>Támogatási információk
Enter your company's support information to provide your employee with a contact for Intune-related questions.

|Mező neve|Maximális hossz|További információ|
|---|---|---|
|**Kapcsolattartó neve** | 40 | This name is displayed on the **Help and Support** page. |
|**Telefonszám** | 20 | This contact number is displayed on the **Help and Support** page to enable employees to contact you for support. |
|**E-mail cím**| 40 | This contact address is displayed on the **Help and Support** page. Meg kell adnia egy érvényes e-mail-címet a következő formátumban: `alias@domainname.com`. |
|**Webhely neve**| 40 | Ez a név a támogatási webhely URL-címének rövid neveként jelenik meg. If you specify a support website URL and no friendly name, then Go to IT website is displayed on the **Help and Support** page in the Company Portal. |
|**Webhely URL-címe**| 150 | Ha rendelkezik saját felhasználóinak szánt támogatási webhellyel, ide írja be az URL-címét. Az URL-cím formátumának a következőnek kell lennie: `https://www.contoso.com`. If you don't specify a URL, nothing is displayed for the support website on the **Help and Support** page in the Company Portal. |
| **További információ**| 120 | Displayed on the **Help and Support** page. |


## <a name="company-identity-branding-customization"></a>Vállalati identitási arculat testreszabása
A Vállalati portál testre szabható a vállalat emblémájának és nevének, valamint a téma színének és a háttérnek a megadásával.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Témaszín és embléma a Céges portálon
Témaszínt alkalmazhat a Céges portálon. Jelöljön ki egy szabványos színt, vagy adjon meg egy hexadecimális hatjegyű kódot az egyéni színhez.

|Mező neve|További információ|
|---|---|
|**Jelöljön ki egy szabványos színt, vagy adjon meg egy hexadecimális hatjegyű kódot**| Choose **Standard** to visually select a color. Válassza az **Egyéni** lehetőséget egy hexadecimális kódon alapuló meghatározott szín kiválasztásához.|
|**Téma színének kiválasztása**| A Vállalati portálra alkalmazni kívánt témaszín kiválasztása. Választhat a színválasztóból, vagy megadhat egy hexadecimális kódot. |
|**Megjelenítés**| Válassza ki, hogy mit szeretne megjeleníteni: **Cégembléma és -név**, **Csak cégembléma** vagy **Csak cégnév**. |
|**A céges embléma feltöltése**|Feltöltheti a Céges portálon megjeleníteni kívánt vállalati emblémát. Vegye figyelembe, hogy a szöveg színének kiválasztása automatikusan történik a legnagyobb kontraszt eléréséhez. Az optimális megjelenés érdekében töltsön fel egy áttetsző hátterű emblémát.<p><ul><li>Maximális képméret: 400px x 400px</li><li>Maximális fájlméret: 750KB</li><li>Fájltípus: PNG, JPG vagy JPEG</li></ul>|

Miután feltöltötte az emblémát, az előnézeti területen meg fog jelenni az embléma a téma színével. Ha úgy dönt, hogy megjeleníti a cég nevét, az feketén vagy fehéren fog megjelenni a Céges portálon, és a téma színe alapján automatikusan a lehető legnagyobb kontraszttal fog megjelenni. A képernyő előnézeti területén nem fog megjelenni a cég neve. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Fehér vagy világos háttérrel használható embléma
Válasszon olyan emblémát, amely fehér vagy világos háttéren mutat a legjobban.

|Mező neve|További információ|
|---|---|
|**Embléma feltöltése**| Ez a lehetőség akkor érhető el, ha a céges embléma megjelenítése mellett döntött. Az optimális megjelenés érdekében töltsön fel egy áttetsző hátterű emblémát.<p><ul><li>Maximális képméret: 400px x 400px</li><li>Maximális fájlméret: 750KB</li><li>Fájltípus: PNG, JPG vagy JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Márkakép a Céges portálhoz

Márkakép feltöltése, amely tükrözi a vállalati márkát. A módosítások mentése után az Intune-webportálon a panel tetején található **Beállítások előnézetének megtekintése** lehetőséget választva megtekintheti, hogyan fog kinézni a konfigurációja. Vegye figyelembe, hogy a márkakép előnézetét csak egy iOS-eszközön lehet megtekinteni, az Intune webes portálján nem. 

|Mező neve|További információ|
|---|---|
|**Márkakép feltöltése**| This option allows you to display a brand image. On the iOS Company Portal, it shows as a background image on the user's profile page.<p><ul><li>Recommended image width: Greater than 1125px (required to be at least 650 px)</li><li>Maximális képméret: 1,3 MB</li><li>Fájltípus: PNG, JPG vagy JPEG</li></ul>|

A megfelelő márkakép javíthatja a felhasználó Céges portálba vetett bizalmát a cég márkájának hangsúlyozásával. Íme néhány tipp, amelyet érdemes figyelembe venni a kép Céges portálhoz történő beszerzésekor, kiválasztásakor és optimalizálásakor. 

- Vegye fel a kapcsolatot az értékesítési vagy művészeti osztállyal. They may already have an approved set of brand images. Előfordulhat, hogy a képek igény szerinti optimalizálásában is tudnak segíteni. 

- Fontolja meg a fekvő és az álló tájolású kompozíciókat is. A képnek megfelelő háttérrel kell rendelkeznie, amely körülveszi a fókuszpontot. The image may be cropped differently based on device size, orientation, and platform. 

- Kerülje az általános, készletben elérhető képek használatát. A képnek tükröznie kell a vállalati márkát, és ismerősnek kell tűnnie a felhasználóknak. Ha még nem rendelkezik ilyen képpel, jobb ha nem használ semmilyet, mint sem hogy olyan általános képet adjon meg, ami semmit nem jelent a felhasználóknak. 

- Szükségtelen metaadatok eltávolítása. A képfájl tartalmazhat metaadatokat, például kameraprofilt, földrajzi helyet, címet, feliratot stb. Használjon képoptimalizáló eszközt ezeknek az adatoknak az eltávolításához a minőség fájlméretkorlátok betartásával történő megőrzéséhez. 

After a brand image is added or changed in Intune, the end user may not see the change on iOS devices until the Company Portal has recognized the change on start up, and then has been restarted to display the brand image. 

### <a name="brand-image-examples"></a>Brand image examples

The following image shows an example iPad branding image:

![Screenshot of example iPhone branding image](./media/company-portal-app/company-portal-app-03.png)

The following image shows an example iPhone branding image:

![Screenshot of example iPad branding image](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Privacy statement customization

You can customize the privacy statement that appears for your organization on managed iOS devices. This message lists the items that your organization can't see or do on managed iOS devices.

Under **Company Portal customization** > **Device management and privacy message**, you can:

- Accept the **Default** to use the list as shown, or
- Choose **Custom** to customize the the list of items that your organization can’t see or do on managed iOS devices. You can use [markdown](https://daringfireball.net/projects/markdown/) to add bullets, bolding, italics, and links.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Company Portal derived credentials for iOS devices
Intune supports Personal Identity Verification (PIV) and Common Access Card (CAC) Derived Credentials in partnership with credential providers DISA Purebred, Entrust Datacard, and Intercede. End users will go through additional steps post-enrollment of their iOS device to verify their identity in the Company Portal application. Derived Credentials will be enabled for users by first setting up a credential provider for your tenant, then targeting a profile that uses Derived Credentials to users or devices.

> [!NOTE]
> The user will see instructions about derived credentials based on the link that you have specified via Intune.

For more information about derived credentials for iOS devices, see [Use derived credentials in Microsoft Intune](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Dark Mode for iOS Company Portal

Dark Mode is available for the iOS Company Portal. Users can download company apps, manage their devices, and get IT support in the color scheme of their choice based on device settings. The iOS Company Portal will automatically match the end user's device settings for dark or light mode. 

## <a name="windows-company-portal-keyboard-shortcuts"></a>A Windows Céges portálon használható billentyűparancsok

End users can trigger navigation, app, and device actions in the Windows Company Portal using keyboard shortcuts (accelerators).

A következő billentyűparancsok érhetők el a Windows Céges portál alkalmazásban.

| Terület | Description | Keyboard shortcut |
|:------------------:|:--------------:|:-----------------:|
| Navigációs menü | Navigation | Alt+M |
|  | Otthoni | Alt+H |
|  | Minden alkalmazás | Alt+A |
|  | Telepített alkalmazások | Alt+I |
|  | Visszajelzés küldése | Alt+F |
|  | Saját profil | Alt+U |
|  | Beállítások | Alt+T |
| Kezdőlap – Eszköz csempe | Átnevezés | F2 |
|  | Eltávolítás | Ctrl+D vagy Delete |
|  | Hozzáférés ellenőrzése | Ctrl+M vagy F9 |
| Eszközadatok | Átnevezés | F2 |
|  | Eltávolítás | Ctrl+D vagy Delete |
|  | Hozzáférés ellenőrzése | Ctrl+M vagy F9 |
| Alkalmazás részletei | Telepítés | Ctrl+I |
| Eszközök | Elérhető | Ctrl+D |

End users will also be able to see the available shortcuts in the Windows Company Portal app.

![Screenshot of the available shortcuts in the Windows Company Portal](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>User self-service device actions from the Company Portal

Users can perform actions on their local or remote devices via the Company Portal app or Website. The actions that a user can perform varies based on device platform and configuration. In all cases, the remote device actions can only be performed by device’s Primary User.
- **Retire** – Removes the device from Intune Management. In the company portal app and website, this shows as **Remove**.
- **Wipe** – This action initiates a device reset. In the company portal website this is shown as **Reset**, or **Factory Reset** in the iOS Company Portal App.
- **Rename** – This action changes the device name that the user can see in the Company Portal. It does not change the local device name, only the listing in the Company Portal.
- **Sync** – This action initiates a device check-in with the Intune service. This shows as **Check Status** in the Company Portal.
- **Remote Lock** – This locks the device, requiring a PIN to unlock it.
- **Reset Passcode** – This action is used to reset device passcode. On iOS devices the passcode will be removed and the end user will be required to enter a new code in settings. On supported Android devices, a new passcode is generated by Intune and temporarily displayed in the Company Portal.
- **Key Recovery** – This action is used to recover a personal recovery key for encrypted macOS devices from the Company Portal website. 

### <a name="self-service-actions"></a>Self Service Actions

Some platforms and configurations do not allow self-service device actions. This table below provides further details about self service actions:

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Kivonás | Available<sup>(1)</sup> | Elérhető | Elérhető | Available<sup>(7)</sup> |
| Törlés | Elérhető | Available<sup>(5)</sup> | NA | Available<sup>(7)</sup> |
| Rename<sup>(4)</sup> | Elérhető | Elérhető | Elérhető | Elérhető |
| Sync | Elérhető | Elérhető | Elérhető | Elérhető |
| Távoli zárolás | Windows Phone only | Elérhető | Elérhető | Elérhető |
| Reset Passcode | Windows Phone only | Available<sup>(8)</sup> | NA | Available<sup>(6)</sup> |
| Key Recovery | NA | NA | Available<sup>(2)</sup> | NA |

<sup>(1)</sup> **Retire** is always blocked on Azure AD Joined Windows devices.<br>
<sup>(2)</sup> **Key Recovery** for MacOS is only available via the Web Portal.<br>
<sup>(3)</sup> All remote actions are disabled if using a Device Enrollment Manager enrollment.<br>
<sup>(4)</sup> **Rename** only changes the device name in the Company Portal app or Web Portal, not on the device.<br>
<sup>(5)</sup> **Wipe** is not available on User Enrolled iOS devices.<br>
<sup>(6)</sup> **Reset Passcode** is not supported on some Android and Android Enterprise configurations. For more information, see [Reset or remove a device passcode in Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> **Retire** and **Wipe** are not available on Android Enterprise Device Owner scenarios (COPE, COBO, COSU).<br> 
<sup>(8)</sup> **Reset Passcode** is not supported on User Enrolled iOS devices.

## <a name="next-steps"></a>További lépések

- [A Windows 10-es céges portál alkalmazás manuális hozzáadása a Microsoft Intune-nal](company-portal-app.md)
