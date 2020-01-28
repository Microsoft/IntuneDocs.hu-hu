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
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754490"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>Gyors útmutató: felhasználó létrehozása az Intune-ban és a felhasználó licencének kiosztása

Ebben a rövid útmutatóban létrehoz egy felhasználót, majd hozzárendeli a felhasználót az Intune-licenchez. Ha az Intune-t használja, minden személynek saját felhasználói fiókkal kell rendelkeznie ahhoz, hogy hozzáférjen a vállalati adatszolgáltatáshoz. Az Intune-rendszergazdák később is konfigurálhatják a felhasználókat a hozzáférés-vezérlés kezeléséhez.

## <a name="prerequisites"></a>Előfeltételek

- Microsoft Intune előfizetés. [Regisztráljon az ingyenes próbaverziós fiókra](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>Bejelentkezés az Intune-ba a Microsoft Endpoint Managerben

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) [globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként](users-add.md#types-of-administrators). Ha létrehozott egy Intune próbaverziós előfizetést, akkor az előfizetést létrehozó fiók a globális rendszergazda.

## <a name="create-a-user"></a>Felhasználó létrehozása

A felhasználónak felhasználói fiókkal kell rendelkeznie az Intune-eszközkezelés regisztrálásához. Új felhasználó létrehozása:

1. A Microsoft Endpoint Managerben válassza a **felhasználók** > **minden felhasználó** > **új felhasználó**: ![a Microsoft Endpoint Managerben válassza az új felhasználó lehetőséget](./media/quickstart-create-user/create-user.png)
2. A **név** mezőbe írjon be egy nevet, például a *Dewey Kellum*: ![felhasználói adatok hozzáadása](./media/quickstart-create-user/create-user-02.png)
3. A **Felhasználónév** mezőbe írja be a felhasználói azonosítót, például Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Ha még nem konfigurálta az ügyfél tartománynevét, használja az Intune-előfizetés létrehozásához használt ellenőrzött tartománynevet (vagy az [ingyenes próbaverziót](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Válassza a **jelszó megjelenítése** lehetőséget, és ügyeljen arra, hogy az automatikusan generált jelszót jegyezze fel, hogy bejelentkezzen egy tesztelési eszközre.
5. Válassza a **Létrehozás** lehetőséget.

## <a name="assign-a-license-to-the-user"></a>Licenc hozzárendelése a felhasználóhoz

Miután létrehozott egy felhasználót, a [Microsoft 365 felügyeleti központban](https://go.microsoft.com/fwlink/p/?LinkId=698854) kell hozzárendelnie egy Intune-licencet a felhasználóhoz. Ha nem rendel hozzá licencet a felhasználóhoz, nem fogja tudni regisztrálni az eszközét az Intune-ban.

Intune-licenc kiosztása egy felhasználóhoz:

1. Jelentkezzen be a [Microsoft 365 felügyeleti központba](https://go.microsoft.com/fwlink/p/?LinkId=698854) ugyanazzal a hitelesítő adatokkal, amelyeket az Intune-ba való bejelentkezéshez használt.
2. Válassza a **felhasználók** > az **aktív felhasználók**lehetőséget, majd válassza ki az imént létrehozott felhasználót.
3. Válassza a **licencek és alkalmazások** fület.
4. A **hely kiválasztása**területen válassza ki a felhasználó helyét, ha még nincs beállítva.
2. Jelölje be az **Intune** jelölőnégyzetet a **licencek** szakaszban. Ha egy másik licenc tartalmazza az Intune-t, akkor kiválaszthatja a licencet. A megjelenített [terméknév](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) az Azure Management szolgáltatási csomagjaként használható.

    ![A hely és az Intune-licenc kiválasztása](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > Ez a beállítás a felhasználó egyik licencét használja. Ha próbaverziós környezetet használ, később újra hozzá fogja rendelni a licencet egy valós felhasználóhoz élő környezetben.

6. Válassza a **módosítások mentése**lehetőséget.

Az új aktív Intune-felhasználó mostantól azt fogja látni, hogy **Intune** -licencet használ.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha már nincs szüksége erre a felhasználóra, törölheti a felhasználót a [Microsoft 365 felügyeleti központba](https://go.microsoft.com/fwlink/p/?LinkId=698854) , és kiválaszthatja a **felhasználók** > *a* felhasználó > *a felhasználó törlése ikon* > **Törlés felhasználó** > **Bezárás**lehetőséget.

   ![A törlés ikon kijelölése](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban létrehozott egy felhasználót, és hozzárendelt egy Intune-licencet az adott felhasználóhoz. Felhasználók Intune-hoz való hozzáadásáról további információt a [Felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](users-add.md) szakaszban találhat.

Az Intune rövid útmutatóinak folytatásához lépjen a következő rövid útmutatóra:

> [!div class="nextstepaction"]
> [Rövid útmutató: Csoport létrehozása felhasználók kezeléséhez](../quickstart-create-group.md)
