---
title: Rövid útmutató – Alkalmazásvédelmi szabályzat létrehozása és hozzárendelése
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban a Microsoft Intune használatával létrehoz és hozzárendel egy alkalmazásvédelmi szabályzatot.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bcda312274e78d327a3a515eb6c95454e38c96f1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507126"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>Rövid útmutató: Alkalmazásvédelmi szabályzat létrehozása és hozzárendelése

Ebben a rövid útmutatóban az Intune-nal létrehoz és hozzárendel egy alkalmazásvédelmi szabályzatot egy ügyfélalkalmazáshoz a végfelhasználó eszközén. Az Intune alkalmazásvédelmi szabályzatokkal ellenőrzi, hogy az alkalmazások megfelelnek-e a szervezet adatvédelmi követelményeinek.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy felhasználót](../fundamentals/quickstart-create-user.md), [létre kell hoznia egy csoportot](../fundamentals/quickstart-create-group.md), [regisztrálnia kell egy eszközt](../quickstart-setup-auto-enrollment.md), valamint [hozzá kell adnia és rendelnie egy alkalmazást](../quickstart-add-assign-app.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune-ba](https://aka.ms/intuneportal) [globális rendszergazdaként vagy Intune-szolgáltatásadminisztrátorként](../fundamentals/users-add.md#types-of-administrators). Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="create-an-app-protection-policy"></a>Alkalmazásvédelmi szabályzat létrehozása

Az alábbi lépések végrehajtásával hozhat létre egy alkalmazás-védelmi szabályzatot:

1. Az [Intune-ban](https://aka.ms/intuneportal) válassza az **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok** > **Szabályzat létrehozása** lehetőséget. 
2. Adja meg a következő adatokat: 

    - **Név**: *Windows 10 tartalomvédelem*
    - **Leírás**: *A szabályzathoz társított felhasználók nem vághatnak ki, másolhatnak vagy illeszthetnek be tartalmakat a társított alkalmazás és az eszköz egyéb, nem felügyelt alkalmazásai között.*
    - **Platform**: *Windows 10*
    - **Regisztráció állapota**: *Regisztrálva*

3. Válassza a **Védett alkalmazások** lehetőséget a szabályzatnak megfeleltetni kívánt alkalmazások kiválasztásához.
4. Kattintson az **Alkalmazások hozzáadása** lehetőségre.
5. Az **Ajánlott alkalmazások** területen válassza a **Word Mobile** lehetőséget.
5. Kattintson az **OK** > **OK** elemre. 
6. Az alkalmazás konfigurálásához válassza a **Szükséges beállítások** lehetőséget.
7. A Windows Information Protection-üzemmód beállításához kattintson a **Felülbírálások engedélyezése** elemre. Ezzel a beállítással letiltja a vállalati adatok az alkalmazáson kívülre való küldését.
8. Kattintson az **OK** > **Létrehozás** gombra.

Ekkor megjelenik az alkalmazásvédelmi szabályzat az Intune-ban.

### <a name="assign-the-app-protection-policy"></a>Az alkalmazásvédelmi szabályzat hozzárendelése

Miután létrehozott egy alkalmazásvédelmi szabályzatot az Intune-ban, azt hozzárendelheti csoportokhoz. 

Alkalmazásvédelmi szabályzat hozzárendeléséhez kövesse az alábbi lépéseket:

1. Az [Intune-ban](https://aka.ms/intuneportal) válassza az **Intune** > **Ügyfélalkalmazások** > **Alkalmazásvédelmi szabályzatok**. 
2. Jelölje ki a korábban létrehozott alkalmazásvédelmi szabályzatot. Ebben a rövid útmutatóban a szabályzat a **Windows 10 tartalomvédelem**.
3. Válassza a **Hozzárendelések** lehetőséget.
4. A **Befoglalás** lapon válassza a **Belefoglalandó csoportok kijelölése** lehetőséget.
5. Válassza a **Contoso tesztelők** elemet a belefoglalandó csoportként.
6. Kattintson a **kijelölés**@no__t – 1**Mentés**gombra. 

Ezzel hozzárendelte az alkalmazásvédelmi szabályzatot.

> [!NOTE]
> Az alkalmazásvédelmi szabályzatok csak olyan csoportokra alkalmazhatók, amelyek felhasználókat és nem eszközöket tartalmaznak.

## <a name="next-steps"></a>További lépések

Ebbe a rövid útmutatóban létrehozott és hozzárendelt egy alkalmazásvédelmi szabályzatot. A szabályzathoz társított, az alkalmazást használó felhasználók nem vághatnak ki, másolhatnak vagy illeszthetnek be tartalmakat a társított alkalmazás és az eszköz egyéb, nem felügyelt alkalmazásai között. Ez a védelmi típus segít megvédeni a szervezet adatait. További információ az Intune alkalmazásvédelmi szabályzatairól: [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md)

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Egyéni szerepkör létrehozása és hozzárendelése](../fundamentals/create-custom-role.md)
