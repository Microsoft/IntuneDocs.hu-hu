---
title: Rövid útmutató – Felhasználó létrehozása az Intune-ban
description: Rövid útmutató – Felhasználó létrehozása az Intune-ban.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 161a18f56256f4a056f32d677759bdb6efe4cd8b
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540837"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Gyors útmutató: felhasználó létrehozása az Intune-ban és licencek kiosztása

Ebben a rövid útmutatóban létrehoz egy felhasználót, majd hozzárendeli egy Intune-licencet. Ha az Intune-t használja, minden személynek saját felhasználói fiókkal kell rendelkeznie a vállalati adataihoz való hozzáféréshez. Az Intune-rendszergazdák később is konfigurálhatják a felhasználókat a hozzáférés-vezérlés kezeléséhez.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Microsoft Intune-előfizetés – [regisztráljon egy ingyenes próbafiókkal](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Bejelentkezés az Intune-ba a Microsoft Endpoint Managerben

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) [globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként](users-add.md#types-of-administrators). Ha létrehozott egy Intune próbaverziós előfizetést, akkor az előfizetést létrehozó fiók a globális rendszergazda.

## <a name="create-a-user"></a>Felhasználó létrehozása

A felhasználóknak felhasználói fiókkal kell rendelkezniük az Intune-eszközkezelés regisztrálásához. Új felhasználó létrehozása:

1. A Microsoft Endpoint Managerben válassza a **felhasználók** > **minden felhasználó** > **új felhasználó**lehetőséget.
    ![a Microsoft Endpoint Managerben válassza az új felhasználó hozzáadása lehetőséget](./media/quickstart-create-user/create-user.png)
2. A **Név** mezőben adja meg például a *Pataki Tivadar* nevet.
    ![felhasználói adatok hozzáadása](./media/quickstart-create-user/create-user-02.png)
3. A **Felhasználónév** mezőben adjon meg egy felhasználóazonosítót, például Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Ha még nem konfigurálta az ügyfél tartománynevét, használja az Intune-előfizetés létrehozásához használt ellenőrzött tartománynevet (vagy az [ingyenes próbaverziót](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Kattintson a **jelszó megjelenítése** lehetőségre, és jegyezze fel az automatikusan generált jelszót, hogy be tudjon jelentkezni egy teszt eszközre.
5. Kattintson a **Létrehozás**gombra.

## <a name="assign-a-license-to-the-user"></a>Licenc hozzárendelése a felhasználóhoz

Miután létrehozott egy felhasználót, a [Microsoft 365 felügyeleti központot](https://go.microsoft.com/fwlink/p/?LinkId=698854) kell használnia ahhoz, hogy Intune-licencet Rendeljen hozzájuk. Ha nem rendel hozzá licencet a felhasználóhoz, nem fogja tudni regisztrálni az eszközét az Intune-ban. 

Intune-licenc kiosztása egy felhasználóhoz:

1. Jelentkezzen be a [Microsoft 365 felügyeleti központba](https://go.microsoft.com/fwlink/p/?LinkId=698854) ugyanazzal a hitelesítő adatokkal, amelyeket az Intune-ba való bejelentkezéshez használt.
2. Válassza a **felhasználók** > **aktív felhasználók** > lehetőséget, és válassza ki az imént létrehozott felhasználót.
3. Kattintson a **licencek és alkalmazások** fülre.
4. A **hely kiválasztása**területen válassza ki a felhasználó helyét, ha még nincs beállítva.
2. Jelölje be az **Intune** jelölőnégyzetet a licencek szakaszban. Ha egy másik licenc tartalmazza az Intune-t, akkor kiválaszthatja a licencet. A megjelenített [terméknév](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)* * az Azure-felügyeletben szolgáltatási csomagként van használatban.

    ![A hely és az Intune-licenc kiválasztása](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > Ezzel a beállítással elhasználja a licencei egyikét ehhez a felhasználóhoz. Ha próbakörnyezetet használ, később újra hozzárendelheti ezt a licencet egy valódi felhasználóhoz, éles környezetben.

6. Válassza a **módosítások mentése**elemet.

Az új aktív Intune-felhasználó mostantól azt fogja látni, hogy **Intune** -licencet használ.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha már nincs szüksége erre a felhasználóra, törölheti a felhasználót a [Microsoft 365 felügyeleti központba](https://go.microsoft.com/fwlink/p/?LinkId=698854) , és a **felhasználók** kiválasztásával > *kiválaszthatja* a felhasználót a listából > *válassza a felhasználó törlése ikont* > **Törlés felhasználói** > **Bezárás**lehetőséget.

   ![A törlés ikon kijelölése](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban létrehozott egy felhasználót, és hozzárendelt egy Intune-licencet. Felhasználók Intune-hoz való hozzáadásáról további információt a [Felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](users-add.md) szakaszban találhat.

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Csoport létrehozása felhasználók kezeléséhez](../quickstart-create-group.md)
