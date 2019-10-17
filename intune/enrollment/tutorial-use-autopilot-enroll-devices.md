---
title: Oktatóanyag – Eszközök regisztrálása az Intune-ban az AutoPilot használatával
titleSuffix: Microsoft Intune
description: Ebben az oktatóanyagban a Windows Autopilotot állítja be az eszközök Intune-ban való regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39ea8b3859d3d2525433c4cafdf566e7a2c8d2ab
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509197"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Oktatóanyag – Windows-eszközök regisztrálása az Intune-ban az AutoPilot használatával

A Windows Autopilot leegyszerűsíti az eszközök regisztrálását. A Microsoft Intune és az AutoPilot használatával új eszközöket adhat a végfelhasználóknak anélkül, hogy egyéni operációsrendszer-lemezképek létrehozására, fenntartására és alkalmazására lenne szükség.

Az oktatóanyag segítségével megtanulhatja a következőket:
> [!div class="checklist"]
> * Eszközök hozzáadása az Intune-hoz
> * AutoPilot-eszközcsoport létrehozása
> * AutoPilot üzembehelyezési profil létrehozása
> * Az AutoPilot üzembehelyezési profil hozzárendelése az eszközcsoporthoz
> * Windows rendszerű eszközök kiosztása a felhasználóknak

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

Az AutoPilot előnyeinek, használati eseteinek és előfeltételeinek áttekintéséhez lásd [a Windows AutoPilot áttekintését](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Előfeltételek
- [Windowsos eszközök automatikus regisztrációjának beállítása](../quickstart-setup-auto-enrollment.md)
- [Előfizetés prémium szintű Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Eszközök felvétele

A Windows Autopilot beállításának első lépéseként hozzá kell adnia az Intune-hoz a Windows rendszerű eszközöket. Csak létre kell hoznia egy CSV-fájlt, és importálnia kell az Intune-ba.

1. Egy szövegszerkesztőben hozza létre a Windows rendszerű eszközöket azonosító, vesszővel elválasztott értékeket (CSV) tartalmazó listát. Használja az alábbi formátumot:
    
    *sorozatszám*, *Windows-termék-azonosító*, *hardver-kivonat*, *opcionális-Group-tag*
    
    Az első három elem megadása kötelező, de a csoport címkéje (korábbi nevén "Order ID") nem kötelező.

2. Mentse a CSV-fájlt.

3. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Windows-regisztráció** > **Eszközök** > **Importálás** elemet.

    ![A Windows AutoPilot-eszközök képernyőképe](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device.png)

4. A **Windows AutoPilot-eszközök hozzáadása** területen keresse meg a mentett CSV-fájlt.

    ![A Windows AutoPilot-eszközök hozzáadásának képernyőképe](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device2.png)

5. Válassza az **Importálás** lehetőséget az eszközadatok importálásának elindításához. Az importálás több percig is eltarthat.

4. Az importálás befejezése után válassza az **eszközök beléptetése** > **windows-regisztráció** > **Windows**Autopilot  > **eszközök** > **szinkronizálás**lehetőséget. Egy üzenet jelenik meg, hogy a szinkronizálás folyamatban van. Nagyszámú eszköz szinkronizálása esetén előfordulhat, hogy várnia kell pár percet, amíg a folyamat befejeződik.

5. Frissítse a nézetet az új eszközök megjelenítéséhez.

## <a name="create-an-autopilot-device-group"></a>AutoPilot-eszközcsoport létrehozása

Ezután létrehoz egy eszközcsoportot, és belehelyezi az előbb betöltött AutoPilot-eszközöket.

1. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza a **Csoportok** > **Új csoport** elemet.
2. A **Csoport** panelen:
    1. A **Csoport típusa** beállításnál válassza a **Biztonsági** lehetőséget.
    2. A **Csoport neve** mezőbe írja be az *AutoPilot-csoport* nevet. A **Csoport leírása** mezőbe írja be az *AutoPilot-eszközök tesztcsoportja* leírást.
    3. A **Tagság típusa** beállításnál válassza a **Hozzárendelt** lehetőséget.
3. A **Csoport** panelen válassza a **Tagok** elemet, és adja hozzá az AutoPilot-eszközöket a csoporthoz. A még nem regisztrált AutoPilot-eszközök olyan eszközök, amelyek neve megegyezik az eszköz sorozatszámával.
4. Válassza a **Létrehozás** lehetőséget.  

## <a name="create-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil létrehozása

Egy eszközcsoport létrehozása után létre kell hoznia egy Deployment-profilt az AutoPilot-eszközök konfigurálásához.

1. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Windows-regisztráció** > **Telepítési profilok** > **Profil létrehozása** elemet.
2. Az **alapbeállítások** lapon a Tor **neve**mezőbe írja be az *Autopilot-profilt*. A **Leírás** mezőbe írja be az *AutoPilot-eszközök tesztprofilja* leírást.
3. Állítsa a **Minden megcélzott eszköz átalakítása az Autopilotra** beállítást **Igen** értékre. Ez a beállítás biztosítja, hogy a listában lévő összes eszköz regisztrálva legyen az Autopilot üzembehelyezési szolgáltatásban. A regisztráció feldolgozása 48 órát is igénybe vehet.
4. Válassza a **Tovább** elemet.
5. A beépített felhasználói **élmény (OOBE)** lapon a **központi telepítési mód**beállításnál válassza a **felhasználó által vezérelt**elemet. Az ilyen profillal rendelkező eszközök az őket regisztráló felhasználóhoz vannak társítva. Az eszköz regisztrálásához felhasználói hitelesítő adatokra van szükség.
6. A **Csatlakozás az Azure AD-hez mint** mezőben válassza az **Azure AD-hez csatlakoztatott** lehetőséget.
7. Konfigurálja az alábbi beállításokat, és hagyja, hogy a többi beállítás az alapértelmezett értékre legyen állítva:
    - **Végfelhasználói licencszerződés (EULA)** : **Elrejtés**
    - **Adatvédelmi beállítások**: **Megjelenítés**
    - **Felhasználói fiók típusa**: **Standard**
8. Válassza a **Tovább** elemet.
9. A **hozzárendelések** lapon válassza a **kijelölt csoportok** lehetőséget a **hozzárendeléshez**.
10. Válassza ki **a felvenni kívánt csoportok kiválasztása**lehetőséget, majd válassza az **Autopilot-csoport**lehetőséget.
11. Válassza a **Tovább** elemet.
12. A profil létrehozásához a **felülvizsgálat + létrehozás** lapon válassza a **Létrehozás** lehetőséget.

## <a name="distribute-devices-to-users"></a>Eszközök terjesztése a felhasználóknak

A Windows rendszerű eszközök ekkor már kioszthatók a felhasználóknak. Az AutoPilot rendszer az első bejelentkezéskor automatikusan regisztrálja és konfigurálja az eszközöket. 

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha már nem szeretne Autopilot-eszközöket használni, törölheti őket.

1. Ha az eszközök regisztrálva vannak az Intune-ban, akkor először [törölnie kell azokat az Azure Active Directory portálról](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Windows-regisztráció** > **Eszközök** lehetőséget.

3. A **Windows AutoPilot-eszközök** területen jelölje ki a törölni kívánt eszközöket, majd válassza a **Törlés** elemet.

4. Hagyja jóvá a törlést az **Igen** választásával. A törlés eltarthat néhány percig.

## <a name="next-steps"></a>További lépések

További információt találhat a Windows Autopilothoz elérhető többi beállításról.

> [!div class="nextstepaction"]
> [Az Autopilot-regisztrációt részletesen ismertető cikk](enrollment-autopilot.md)


