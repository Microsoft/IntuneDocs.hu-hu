---
title: Rövid útmutató – Felhasználó létrehozása az Intune-ban
description: Rövid útmutató – Felhasználó létrehozása az Intune-ban.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75a875fc3ff11eb1e3befad425c16a710544f781
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509883"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Gyors útmutató: felhasználó létrehozása az Intune-ban és licencek kiosztása

Ebben a rövid útmutatóban létrehoz egy felhasználót, majd hozzárendeli egy Intune-licencet. Ha az Intune-t használja, minden személynek saját felhasználói fiókkal kell rendelkeznie a vállalati adataihoz való hozzáféréshez. Az Intune-rendszergazdák később is konfigurálhatják a felhasználókat a hozzáférés-vezérlés kezeléséhez.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune](https://aka.ms/intuneportal) -ba [globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként](users-add.md#types-of-administrators). Ha létrehozott egy Intune próbaverziós előfizetést, akkor az előfizetést létrehozó fiók a globális rendszergazda.

## <a name="create-a-user"></a>Felhasználó létrehozása

A felhasználóknak felhasználói fiókkal kell rendelkezniük az Intune-eszközkezelés regisztrálásához. Új felhasználó létrehozása:

1. Válassza az Intune-ban a **Felhasználók** > **Minden felhasználó** > **Új felhasználó** lehetőséget.
![Böngésző](./media/quickstart-create-user/create-user.png)
2. A **Név** mezőben adja meg például a *Pataki Tivadar* nevet.
3. A **Felhasználónév** mezőben adjon meg egy felhasználóazonosítót, például Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Ha még nem konfigurálta az ügyfél tartománynevét, használja az Intune-előfizetés létrehozásához használt ellenőrzött tartománynevet (vagy az [ingyenes próbaverziót](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Válassza a **Jelszó megjelenítése** lehetőséget, és jegyezze fel az automatikusan generált jelszót, hogy be tudjon jelentkezni a teszteszközre.
5. Válassza a **Létrehozás** lehetőséget.

## <a name="assign-a-license-to-the-user"></a>Licenc hozzárendelése a felhasználóhoz

Miután létrehozott egy felhasználót, a [Microsoft 365 felügyeleti központot](http://go.microsoft.com/fwlink/p/?LinkId=698854) kell használnia ahhoz, hogy Intune-licencet Rendeljen hozzájuk. Ha nem rendel hozzá licencet a felhasználóhoz, nem fogja tudni regisztrálni az eszközét az Intune-ban. 

Intune-licenc kiosztása egy felhasználóhoz:

1. Jelentkezzen be a [Microsoft 365 felügyeleti központba](http://go.microsoft.com/fwlink/p/?LinkId=698854) ugyanazzal a hitelesítő adatokkal, amelyeket az Intune-ba való bejelentkezéshez használt.
2. Válassza a **felhasználók** > **aktív felhasználók** > lehetőséget, és válassza ki az imént létrehozott felhasználót.
3. Válassza a **Terméklicencek** melletti **Szerkesztés** lehetőséget.
4. A **Hely** listában válassza ki a felhasználó helyét.
5. Kattintson **az** Intune-licenc melletti (vagy egy másik, az Intune-t tartalmazó licenc) elemre. A megjelenített [terméknév](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** lesz szolgáltatáscsomagként használva az Azure-felügyeletben. 

   > [!NOTE]
   > Ezzel a beállítással elhasználja a licencei egyikét ehhez a felhasználóhoz. Ha próbakörnyezetet használ, később újra hozzárendelheti ezt a licencet egy valódi felhasználóhoz, éles környezetben.
6. Válassza a **Mentés** > **Bezárás** lehetőséget.

Az új aktív Intune-felhasználó mostantól azt fogja látni, hogy **Intune** -licencet használ.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha már nincs szüksége erre a felhasználóra, törölheti a felhasználót a [Microsoft 365 felügyeleti központba](http://go.microsoft.com/fwlink/p/?LinkId=698854) , és kiválaszthatja a **felhasználók** > **aktív felhasználók** > *válassza ki a felhasználót a listában* > **Törlés** felhasználó > **Törlés felhasználó** > a **módosítások jóváhagyása** > **Bezárás gombra**.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban létrehozott egy felhasználót, és hozzárendelt egy Intune-licencet. Felhasználók Intune-hoz való hozzáadásáról további információt a [Felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](users-add.md) szakaszban találhat.

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Csoport létrehozása felhasználók kezeléséhez](../quickstart-create-group.md)
