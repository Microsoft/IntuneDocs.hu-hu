---
title: Eszközök regisztrálása a Windows AutoPilot használatával
titleSuffix: Microsoft Intune
description: Útmutató a Windows 10-eszközök Windows AutoPilot használatával történő regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5066afdaf303a1cef20f80d3134f2382f718d86b
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390739"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Enroll Windows devices in Intune by using the Windows Autopilot  
The Windows Autopilot simplifies enrolling devices in Intune. A testre szabott operációsrendszer-lemezképek létrehozása és karbantartása sok időt vesz igénybe. Gyakran ezeknek az egyéni operációsrendszer-lemezképeknek az új eszközökre való alkalmazásával is időt kell töltenie, hogy felkészítse az eszközöket a használatra, mielőtt a végfelhasználóknak adná azokat. A Microsoft Intune és az AutoPilot révén új eszközöket adhat hozzá a végfelhasználók számára anélkül, hogy egyéni operációsrendszer-lemezképek létrehozására, kezelésére és az eszközökre való alkalmazására lenne szükség. Az AutoPilot-eszközök Intune-nal való felügyelete során a regisztráció után szabályzatokat, profilokat, alkalmazásokat és sok mást is kezelni tud. A megoldás előnyeinek, használati eseteinek és előfeltételeinek áttekintéséről lásd [a Windows AutoPilot áttekintését](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

There are four types of Autopilot deployment:
- [Self Deploying Mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) for kiosks, digital signage, or a shared device
- [White Glove](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) enables partners or IT staff to pre-provision a Windows 10 PC so that it's fully configured and business-ready -[Autopilot for existing devices](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) enables you to easily deploy the latest version of Windows 10 to your existing devices
- [User Driven Mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) for traditional users. 


## <a name="prerequisites"></a>Előfeltételek
- [Intune subscription](../fundamentals/licenses.md)
- [Engedélyezni kell a Windowsos eszközök automatikus regisztrációját](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium subscription](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>How to get the CSV for Import in Intune

For more information, see the understanding powershell cmdlet.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Eszközök felvétele

A Windows AutoPilot-eszközök felvételéhez importálhat egy CSV-fájlt az adataikkal.

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment** > **Windows enrollment** > **Devices** > **Import**.

    ![A Windows AutoPilot-eszközök képernyőképe](./media/enrollment-autopilot/autopilot-import-device.png)

2. A **Windows AutoPilot-eszközök hozzáadása** alatt keresse meg a hozzáadni kívánt eszközöket felsoroló CSV-fájlt. The CSV file should list the serial numbers, Windows product IDs, hardware hashes, optional group tags, and optional assigned user. You can have up to 500 rows in the list. Use the header and line format shown below:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![A Windows AutoPilot-eszközök hozzáadásának képernyőképe](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > When you use CSV upload to assign a user, make sure that you assign valid UPNs. If you assign an invalid UPN (incorrect username), your device may be inaccessible until you remove the invalid assignment. During CSV upload the only validation we perform on the **Assigned User** column is to check that the domain name is valid. We're unable to perform individual UPN validation to ensure that you're assigning an existing or correct user.

3. Válassza az **Importálás** lehetőséget az eszközadatok importálásának elindításához. Az importálás több percig is eltarthat.

4. After import is complete, choose **Device enrollment** > **Windows enrollment** > **Windows Autopilot** > **Devices** > **Sync**. A message displays that the synchronization is in progress. Nagyszámú eszköz szinkronizálása esetén előfordulhat, hogy várnia kell pár percet, amíg a folyamat befejeződik.

5. Frissítse a nézetet az új eszközök megjelenítéséhez.

## <a name="create-an-autopilot-device-group"></a>AutoPilot-eszközcsoport létrehozása

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Groups** > **New group**.
2. A **Csoport** panelen:
    1. A **Csoport típusa** beállításnál válassza a **Biztonsági** lehetőséget.
    2. Gépelje be a **Csoport nevét** és a **Csoport leírását**.
    3. A **Tagság típusa** beállításnál válassza a **Hozzárendelt** vagy a **Dinamikus eszköz** lehetőséget.
3. Ha a **Tagság típusa** beállításnál az előző lépésben a **Hozzárendelt** értéket választotta, akkor válassza a **Csoport** panel **Tagok** elemét, és adjon hozzá AutoPilot-eszközöket a csoporthoz.
    A még nem regisztrált AutoPilot-eszközök olyan eszközök, amelyek neve megegyezik az eszköz sorozatszámával.
4. Ha a **Tagság típusa** alatt a **Dinamikus eszköz** lehetőséget választotta, akkor válassza a **Csoport** panel **Dinamikus eszköz tagok** lehetőségét, és gépelje be az alábbi kódok bármelyikét a **Speciális szabály** mezőbe. Only Autopilot devices are gathered by these rules, because they target attributes that are only possessed by Autopilot devices. Creating a group based off non-autopilot attributes won't guarantee that devices included in the group are actually registered to Autopilot.
    - If you want to create a group that includes all of your Autopilot devices, type: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Intune's group tag field maps to the OrderID attribute on Azure AD devices. If you want to create a group that includes all of your Autopilot devices with a specific group tag (the Azure AD device OrderID), you must type: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Ha létre kíván hozni egy csoportot, amely az egy adott beszerzési rendelési azonosítóval rendelkező összes Autopilot-eszközét tartalmazza, írja be a következőt: `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    A **Speciális szabály** kódjának megadása után válassza a **Mentés** lehetőséget.
5. Válassza a **Létrehozás** lehetőséget.  

## <a name="create-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil létrehozása
Az Autopilot-üzembehelyezési profilokkal Autopilot-eszközeit konfigurálhatja. You can create up to 350 profiles per tenant.
1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment** > **Windows enrollment** > **Deployment Profiles** > **Create Profile**.
2. On the **Basics** page, type a **Name** and optional **Description**.

    ![Screenshot of Basics page](./media/enrollment-autopilot/create-profile-basics.png)

3. Ha azt szeretné, hogy a hozzárendelt csoportokban lévő minden eszköz automatikusan átálljon az AutoPilotra, állítsa a **Minden megcélzott eszköz AutoPilot-eszközzé alakítása** beállítást **Igen** értékre. All corporate owned, non-Autopilot devices in assigned groups will register with the Autopilot deployment service. Personally owned devices will not be converted to Autopilot. A regisztráció feldolgozása 48 órát is igénybe vehet. Az eszköz regisztrációjának törlése és alaphelyzetbe állítása után az Autopilot regisztrálja az eszközt. Miután ilyen módon regisztrál egy eszközt, a beállítás letiltása vagy a profil-hozzárendelés eltávolítása nem távolítja el az eszközt az Autopilot üzembehelyezési szolgáltatásból. Ehhez [közvetlenül kell törölnie az eszközt](enrollment-autopilot.md#delete-autopilot-devices).
4. Válassza a **Tovább** elemet.
5. On the **Out-of-box experience (OOBE)** page, for **Deployment mode**, choose one of these two options:
    - **Felhasználó-alapú**: Az ilyen profillal rendelkező eszközök az őket regisztráló felhasználóhoz vannak társítva. Az eszköz regisztrálásához felhasználói hitelesítő adatokra van szükség.
    - **Self-deploying (preview)** : (requires Windows 10, version 1809 or later) Devices with this profile aren't associated with the user enrolling the device. Az eszköz telepítéséhez nincs szükség felhasználói hitelesítő adatokra. When a device has no user associated with it, user-based compliance policies don't apply to it. When using self-deploying mode, only compliance policies targeting the device will be applied.

    ![Screenshot of OOBE page](./media/enrollment-autopilot/create-profile-outofbox.png)

6. A **Csatlakozás az Azure AD-hez mint** mezőben válassza az **Azure AD-hez csatlakoztatott** lehetőséget.
7. Configure the following options:
    - **Végfelhasználói licencszerződés (EULA)** : (Windows 10, 1709-es vagy újabb verzió) Eldöntheti, hogy a felhasználók számára megjelenjen-e a végfelhasználói licencszerződés.
    - **Adatvédelmi beállítások**: Eldöntheti, hogy a felhasználók számára megjelenjenek-e az adatvédelmi beállítások.
    >[!IMPORTANT]
    >The default value for the Diagnostic Data setting varies between Windows versions. For devices running Windows 10, version 1903, the default value is set to Full during the out-of-box experience. For more information, see [Windows Diagnostics Data](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Hide change account options (requires Windows 10, version 1809 or later)** : Choose **Hide** to prevent change account options from displaying on the company sign-in and domain error pages. Ez a beállítás megköveteli, hogy [az Azure Active Directoryban konfigurálva legyen a Vállalati védjegyezés](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Felhasználói fiók típusa**: Válassza ki a felhasználói fiók típusát (**Rendszergazda** vagy **Normál**). We allow the user joining the device to be a local Administrator by adding them to the local Admin group. We don't enable the user as the default administrator on the device.
    - **Allow White Glove OOBE** (requires Windows 10, version 1903 or later; [additional physical requirements](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): Choose **Yes** to allow white glove support.
    - **Apply device name template** (requires Windows 10, version 1809 or later, and Azure AD join type): Choose **Yes** to create a template to use when naming a device during enrollment. A nevek legfeljebb 15 karakterből állhatnak, és betűket, számokat és kötőjelet tartalmazhatnak. A nevek nem állhatnak csak számokból. Hardverspecifikus sorozatszám hozzáadásához használja a [%SERIAL% makrót](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp). Egy másik lehetőség a [%RAND:x% makró](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) használata, amellyel véletlenszerű számsort adhat hozzá. Az x a hozzáadni kívánt számjegyek számát jelenti. You can only provide a pre-fix for hybrid devices in a [domain join profile](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile). 
    - **Nyelv (Régió)** \*: Válassza ki az eszközön használandó nyelvet. Ez a lehetőség csak akkor érhető el, ha a **Telepítési mód** beállításnál az **Öntelepítő** lehetőséget választotta.
    - **Automatically configure keyboard**\*: If a **Language (Region)** is selected, choose **Yes** to skip the keyboard selection page. Ez a lehetőség csak akkor érhető el, ha a **Telepítési mód** beállításnál az **Öntelepítő** lehetőséget választotta.
8. Válassza a **Tovább** elemet.
9. On the **Scope tags** page, optionally add the scope tags you want to apply to this profile. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md).
10. Válassza a **Tovább** elemet.
11. On the **Assignments** page, choose **Selected groups** for **Assign to**.

    ![Screenshot of Assignments page](./media/enrollment-autopilot/create-profile-assignments.png)

12. Choose **Select groups to include**, and choose the groups you want to include in this profile.
13. If you want to exclude any groups, choose **Select groups to exclude**, and choose the groups you want to exclude.
14. Válassza a **Tovább** elemet.
15. On the **Review + Create** page, choose **Create** to create the profile.

    ![Screenshot of Review page](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune will periodically check for new devices in the assigned groups, and then begin the process of assigning profiles to those devices. This process can take several minutes to complete. Before deploying a device, ensure that this process has completed.  You can check under **Device enrollment** > **Windows enrollment** > **Devices** where you should see the profile status change from "Unassigned" to "Assigning" and finally to "Assigned."

## <a name="edit-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil szerkesztése
Az AutoPilot üzembehelyezési profil létrehozása után módosíthatja az üzembehelyezési profil egyes részeit.   

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment**.
2. A **Windows-regisztráció** terület **Windows AutoPilot** szakaszában válassza az **Üzembehelyezési profilok** lehetőséget.
3. Válassza ki a szerkeszteni kívánt profilt.
4. A telepítési profil nevének vagy leírásának módosításához kattintson a bal oldali **Tulajdonságok** elemre. A módosítások elvégzését követően kattintson a **Mentés** gombra.
5. A Kezdőélmény beállításainak módosításához kattintson a **Beállítások** elemre. A módosítások elvégzését követően kattintson a **Mentés** gombra.

> [!NOTE]
> A profil módosításai alkalmazva lesznek a profilhoz társított eszközökön. Azonban a frissített profilt az Intune-ban korábban már regisztrált eszközökre csak azok alaphelyzetbe állítása és megújítása után alkalmazza a rendszer.

## <a name="edit-autopilot-device-attributes"></a>Edit Autopilot device attributes
After you've uploaded an Autopilot device, you can edit certain attributes of the device.

1. In Intune in the Azure portal, choose **Device enrollment**.
2. Under **Windows enrollment**, in the **Windows Autopilot** section, choose **Devices**.
3. Select the device you want to edit.
4. In the pane on the right of the screen, you can edit the device name, group tag, or User Friendly Name (if you've assigned a user).
5. Válassza a **Mentés** lehetőséget.

> [!NOTE]
> Device names can be configured for all devices, but are ignored in Hybrid Azure AD joined deployments. Device name still comes from the domain join profile for Hybrid Azure AD devices.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alerts for Windows Autopilot unassigned devices  <!-- 163236 -->  

A riasztások jelzik, hogy az AutoPilot programban hány eszközhöz nincs hozzárendelve AutoPilot üzembehelyezési profil. A riasztás adatai alapján a profilok létrehozhatók és a hozzárendelés nélküli eszközökhöz rendelhetők. A riasztásra kattintva megjelenik a Windows AutoPilot-eszközök részletes adatokat is tartalmazó, teljes listája.

A nem társított eszközökre vonatkozó riasztások megtekintéséhez az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Áttekintés** > **Nem társított eszközök** lehetőséget.  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Felhasználó hozzárendelése egy adott Autopilot-eszközhöz

Felhasználót rendelhet hozzá egy adott Autopilot-eszközhöz. Ez a hozzárendelés előre kitölti a [vállalati védjeggyel ellátott](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) bejelentkezési oldal felhasználói űrlapját az Azure Active Directoryból származó adatokkal a Windows beállítása során. Egyéni üdvözlési megnevezés beállítását is lehetővé teszi. A windowsos bejelentkezési adatokat nem tölti ki előre és nem is módosítja. Ilyen módon csak licenccel rendelkező Intune-felhasználók rendelhetők hozzá.

Prerequisites: Azure Active Directory Company Portal has been configured and Windows 10, version 1809 or later.

1. In the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment** > **Windows enrollment** > **Devices** > choose the device > **Assign user**.

    ![Képernyőkép a felhasználó hozzárendeléséről](./media/enrollment-autopilot/assign-user.png)

2. Jelöljön ki egy Intune-licenccel rendelkező Azure-felhasználót, és válassza a **Kiválasztás** lehetőséget.

    ![Képernyőkép a felhasználó kiválasztásáról](./media/enrollment-autopilot/select-user.png)

3. A **Rövid felhasználónév** mezőbe gépeljen be egy rövid nevet, vagy fogadja el az alapértelmezettet. Ez a rövid név jelenik meg, amikor a felhasználó bejelentkezik a Windows telepítése során.

    ![A rövid felhasználónév képernyőképe](./media/enrollment-autopilot/friendly-name.png)

4. Válassza az **OK** gombot.

## <a name="autopilot-deployments-report"></a>Autopilot deployments report
You can see details on each device deployed through Windows Autopilot.
To see the report, go to **Intune** and, under **Monitor**, choose **Autopilot deployments**.
The data is available for 30 days after deployment.


## <a name="delete-autopilot-devices"></a>AutoPilot-eszközök törlése

You can delete Windows Autopilot devices that aren't enrolled into Intune:

- Delete the devices from Windows Autopilot at **Device enrollment** > **Windows enrollment** > **Devices**. Choose the devices you want to delete, then choose **Delete**. Windows Autopilot device deletion can take a few minutes to complete.

Completely removing a device from your tenant requires you to delete the Intune device, the Azure Active Directory device, and the Windows Autopilot device records. This can all be done from Intune:

1. If the devices are enrolled in Intune, you must first [delete them from the Intune All devices blade](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Delete the devices in Azure Active Directory devices at **Devices** > **Azure AD devices**.

3. Delete the devices from Windows Autopilot at **Device enrollment** > **Windows enrollment** > **Devices**. Choose the devices you want to delete, then choose **Delete**. Windows Autopilot device deletion can take a few minutes to complete.

## <a name="using-autopilot-in-other-portals"></a>Az AutoPilot használata más portálokon
Ha nem kíván a mobileszközök felügyeletével foglalkozni, más portálokon is használhatja az AutoPilotot. Más portálok is használhatók, de javasoljuk, hogy az Intune-t csak AutoPilottal végzett üzembe helyezések felügyeletéhez használja. Az Intune más portálokkal való használatakor az Intune nem tudja végrehajtani a következőket:  

- Megjeleníteni az Intune-ban létrehozott, de egy másik portálon szerkesztett profilok módosításait
- Szinkronizálni egy másik portálon létrehozott profilokat
- Megjeleníteni a profil-hozzárendelések más portálon végzett módosításait
- Szinkronizálni a más portálon végzett profil-hozzárendeléseket
- Megjeleníteni az eszközlista más portálon végzett módosításait

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot meglévő eszközökhöz

Ha a Configuration Manager [meglévő eszközökhöz használható AutoPilot szolgáltatásával](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) regisztrál, egy korrelátorazonosítóval csoportosíthatja a Windows-eszközöket. A korrelátorazonosító az Autopilot konfigurációs fájljának egyik paramétere. Az [enrollmentProfileName Azure AD-beli eszközattribútum](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) beállítása automatikusan az ezzel megegyező „OfflineAutopilotprofile-\<korrelátorazonosítóra\>” módosul. Így tetszőleges dinamikus Azure AD-csoportok hozhatók létre korrelátorazonosító alapján az enrollmentprofileName attribútum használatával.

>[!WARNING] 
> Mivel a korrelátorazonosító nincs előzetesen megadva az Intune-on, az eszköz tetszés szerint jelenthet be bármilyen korrelátorazonosítót. Ha a felhasználó által létrehozott korrelátorazonosító egyezik egy AutoPilot- vagy Apple DEP-profil nevével, az eszköz hozzá lesz adva az enrollmentProfileName attribútumon alapuló összes dinamikus Azure AD-eszközcsoporthoz. Az ütközés elkerüléséhez:
> - A dinamikus csoportokra vonatkozó szabályokat mindig a *teljes* enrollmentProfileName érték használatával hozza létre.
> - Az Autopilot- és Apple DEP-profilok nevét soha ne kezdje az OfflineAutopilotprofile- előtaggal.

## <a name="next-steps"></a>További lépések
Miután konfigurálta a Windows AutoPilotot a regisztrált Windows 10-eszközökhöz, sajátítsa el, hogyan felügyelheti az eszközöket. További információt [A Microsoft Intune-eszközfelügyelet ismertetése](../remote-actions/device-management.md) című témakörben talál.
