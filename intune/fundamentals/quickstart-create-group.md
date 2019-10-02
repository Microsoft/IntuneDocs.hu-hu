---
title: Rövid útmutató – Csoport létrehozása felhasználók kezeléséhez
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban a Microsoft Intune használatával fog csoportot létrehozni meglévő felhasználók alapján.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ccf0f06993ef0edf06ca60ba4de7973ed878441a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732099"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>QuickStart Csoport létrehozása a felhasználók kezeléséhez

Ebben a rövid útmutatóban az Intune használatával fog csoportot létrehozni egy meglévő felhasználó alapján. Csoportokkal kezelheti a felhasználókat, és ellenőrzés alatt tarthatja, hogy a felhasználók milyen céges erőforrásokat érhetnek el. Ezek lehetnek a vállalati intranet részei, vagy olyan külső erőforrások, mint a SharePoint-webhelyek, SaaS-alkalmazások vagy webalkalmazások.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon egy ingyenes próbafiókkal](free-trial-sign-up.md).

>[!NOTE]
>Az Intune biztosítja az előre létrehozott **Minden felhasználó** és **Minden eszköz** csoportok beépített optimalizálását a felhasználók kényelme érdekében a konzolon.

## <a name="prerequisites"></a>Előfeltételek

- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy felhasználót](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune-portálra](https://aka.ms/intuneportal) [globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként](users-add.md#types-of-administrators). Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="create-a-group"></a>Csoport létrehozása

Létre fog hozni egy csoportot, amelyet a későbbiekben fog használni ebben a rövid útmutatóban. Csoport létrehozása:

1. Miután megnyitotta a **Microsoft Intune** panelt, válassza a **Csoportok** > **Új csoport** lehetőséget.
2. A **Csoporttípus** legördülő listában válassza a **Biztonság** elemet.
3. A **csoport neve** mezőbe írja be az új csoport nevét (például **contoso-tesztelők**).
4. Adja meg a csoport **leírását** .
5. Adja meg a **Tagság típusa** elemhez a **Hozzárendelt** beállítást. 
6. Kattintson a **tagok** elemre, és válassza ki a csoport egy vagy több tagját a listából.

    ![Képernyőkép egy csoport létrehozásáról a Microsoft Intune-ban](./media/quickstart-create-group/quickstart-use-groups-01.png)

7. Kattintson a **Kiválasztás** > **Létrehozás** elemre.

Miután sikeresen létrehozta a csoportot, az megjelenik az **Összes csoport** listájában. 

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban az Intune használatával hozott létre csoportot egy meglévő felhasználó alapján. Csoportok Intune-hoz való hozzáadásáról további információ a [Csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](../groups-add.md) szakaszban olvasható.

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [QuickStart Automatikus regisztráció beállítása a Windows 10-es eszközökhöz @ no__t-0
