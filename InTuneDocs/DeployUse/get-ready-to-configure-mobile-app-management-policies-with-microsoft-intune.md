---
# required metadata

title: Felkészülés a mobilalkalmazás-felügyeleti szabályzatok konfigurálására | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Felkészülés a mobilalkalmazás-felügyeleti szabályzatok konfigurálására a Microsoft Intune-ban
Ez a témakör leírja, milyen műveleteket kell elvégeznie ahhoz, hogy mobilalkalmazás-felügyeleti szabályzatokat (MAM) hozhasson létre az Azure-portálon.
Ha jelenleg az **Intune felügyeleti konzolt** használja eszközei kezelésére, az [Intune felügyeleti konzol](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) segítségével létrehozhat egy olyan MAM-szabályzatot, amely támogatja az Intune-ban regisztrált eszközökön futó alkalmazásokat..
>[!IMPORTANT]
> Előfordulhat, hogy az Intune felügyeleti konzolon nem lát minden MAM-szabályzatbeállítást. A mobilalkalmazás-felügyeleti szabályzatok létrehozására szolgáló új felügyeleti konzol az Azure-portál.

##  Támogatott platformok
- iOS 8.1-es vagy újabb verzió

- Android 4 vagy újabb verzió

##  Támogatott alkalmazások
A támogatott alkalmazások teljes listájának megtekintéséhez keresse fel a [Microsoft Intune mobilalkalmazás-galériát](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) a Microsoft Intune alkalmazáspartnerek oldalán.
Ha meg szeretné tekinteni a támogatott forgatókönyveket, platformokat, illetve azt, hogy az alkalmazás támogatja-e a többszörös identitást, kattintson az adott alkalmazásra.

MAM-szabályzatok **konfigurálásához** a következőkre lesz szüksége:

-   **Microsoft Intune-előfizetés**.    A végfelhasználók csak [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenccel szerezhetnek be MAM-szabályzatot használó alkalmazásokat.

-   **Mobileszköz-kezelő szolgáltatóként** az **Intune-t** vagy a **Configuration Managert** kell megadni, attól függően, hogy csak az Intune-t használja, vagy az Intune-nal integrált Configuration Managert is használja az eszközök kezelésére. Ha az O365 beépített mobileszköz-kezelését használja, Intune-előfizetést kell vásárolnia, és [az Intune-t kell beállítania mobileszköz-kezelő szolgáltatóként](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)..
-   A következőkhöz **Office 365**-előfizetés (O365-előfizetés) is szükséges:
  - MAM-szabályzatok alkalmazása többszörös identitást támogató alkalmazásokra.
  - SharePoint Online- és Exchange Online munkahelyi fiókok létrehozása. A helyi Exchange-et és a helyi SharePointot nem támogatjuk.


- **Microsoft Azure Active Directory (Azure AD)** a felhasználók létrehozásához. Az Azure AD akkor hitelesíti a felhasználót, amikor az végfelhasználóként elindítja az alkalmazást, és megadja a munkahelyi hitelesítő adatokat.

    > [!NOTE]
    > Ha az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konzolon végzi a felhasználók beállítását, vegye figyelembe, hogy a rendszer az Azure-portálra továbbítja a MAM-szabályzat konfigurációját, e portál használatához pedig Azure AD felhasználói csoportokat kell létrehoznia az Office 365-portál használatával.


## Felhasználók létrehozása és Microsoft Intune-licencek kiosztása

1. Intune-előfizetés szükséges: ha jelenleg az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] segítségével felügyeli az eszközeit, az azt jelenti, hogy rendelkezik [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-előfizetéssel.  Akkor is rendelkezik [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-előfizetéssel, ha korábban már vásárolt EMS-licencet. Ha a mobilalkalmazás-felügyeleti funkciók miatt próbálná ki az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-t, [itt](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/) létrehozhat egy próbafiókot..

    Az Office-portál Számlázás lapján ellenőrizheti, hogy van-e [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-előfizetése.  Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-nak az **Aktív** előfizetéseknél kell megjelennie.

2.  Jelentkezzen be az   [Office portálra](http://portal.office.com) a rendszergazdai hitelesítő adataival.

3.  Válassza az **Aktív felhasználók** lapot felhasználók hozzáadásához és az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licencek hozzárendeléséhez.

    ![Az Office-portál felhasználók hozzáadására szolgáló oldala](../media/AppManagement/OfficePortal_AddUsers.png)

4.  A felhasználók számára a **Globális rendszergazdai szerepkör** hozzárendelésével biztosíthat hozzáférést az Office-, az Azure AD- és az Azure-portálhoz.

    ![Az Office-portál Aktív felhasználók oldalát bemutató képernyőkép ](../media/AppManagement/OfficePortal_AddRoletoUser.png)

5.  A MAM-szabályzatok az Azure Active Directorybeli felhasználói csoportokra vonatkoznak. MAM-szabályzatokat használó felhasználói csoportok létrehozásához válassza a **Csoportok** lapot az **Office-portálon**, majd kattintson a **+** ikonra új biztonsági csoport létrehozásához.  Írja be a csoport nevét és leírását, majd kattintson a **Létrehozás**elemre. Ezt követően a **Tagok szerkesztése** elemre kattintva vehet fel felhasználókat az újonnan létrehozott biztonsági csoportba. A biztonsági csoport az Azure Active Directoryban jön létre.

    ![A Felhasználói szerepkörök módosítása oldalon a Globális rendszergazda szerepkör kiválasztását mutató képernyőkép](../media/AppManagement/OfficePortal_CreateGroups.png)

Az alábbi táblázat a rendszergazdai jogosultságú felhasználókhoz rendelhető szerepköröket és engedélyeket sorolja fel.

|||
|--|----|
|**Szerepkör**|**Engedélyek**|
|Globális rendszergazda (O365-portál)|Hozzáférés az O365-portálhoz és az Azure AD-portálhoz<br /><br />Hozzáférés az Azure-portálhoz (mobilalkalmazás- és szerepkör-felügyeleti feladatokat is végrehajthat).|
|Tulajdonosi szerepkör (Azure-portál)|Hozzáférés az Azure-portálhoz (mobilalkalmazás- és szerepkör-felügyeleti feladatokat is végrehajthat).|
|Közreműködői szerepkör (Azure-portál)|Hozzáférés az Azure-portálhoz (csak mobilalkalmazás-felügyeleti feladatokat hajthat végre).|

## A közreműködői szerepkör hozzárendelése felhasználóhoz

A**globális rendszergazdák** hozzáférhetnek az Azure-portálhoz.  Ha más rendszergazdai felhasználók számára is engedélyezni szeretné a szabályzatok konfigurálását és egyéb mobilalkalmazás-felügyeleti feladatokat, rendelje hozzá a felhasználóhoz a **közreműködői szerepkört** az alábbi lépéseket követve:


1.  A **Beállítások** panel **Erőforrás-kezelés** szakaszában kattintson a **Felhasználók** elemre..

    ![Az Azure-portál Felhasználók paneljét bemutató képernyőkép](../media/AppManagement/AzurePortal_MAM_AddUsers.png)

2.  Kattintson a **Hozzáadás** elemre a **Hozzáférés hozzáadása** panel megnyitásához.

3.  Kattintson a **Szerepkörválasztás**, majd a **Közreműködő** elemre..

    ![Az Azure-portál Szerepkörválasztás paneljét bemutató képernyőkép](../media/AppManagement/AzurePortal_MAM_AddRole.png)

4.  Miután kiválasztotta a szerepkört, kattintson a **Felhasználók hozzáadása**elemre, és keresse meg a kívánt felhasználót a felhasználónév vagy e-mail cím alapján. A listán az első 1000 felhasználó látható, akiket korábban az Office-portál használatával hozott létre az Azure AD-ban. Kattintson az **Ok** gombra a **Hozzáférés hozzáadása** panelen a mentéshez és a szerepkör hozzárendeléséhez a felhasználóhoz.

    ![Az Azure-portál Felhasználók hozzáadása paneljét bemutató képernyőkép](../media/AppManagement/AzurePortal_MAM_AddusertoRole.png)

    > [!IMPORTANT]
    > Ha [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenccel nem rendelkező felhasználót választ ki, a felhasználó nem fogja tudni elérni a portált.

## További lépések
[Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->


