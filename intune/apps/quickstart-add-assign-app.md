---
title: Rövid útmutató – Ügyfélalkalmazás hozzáadása és hozzárendelése
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban egy ügyfélalkalmazást ad és rendel hozzá a Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d09857c4e5b63947a6e3b3140f673f0887f7f920
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563407"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Rövid útmutató: Ügyfélalkalmazás hozzáadása és hozzárendelése

Ebben a rövid útmutatóban egy ügyfélalkalmazást ad és rendel hozzá a cége alkalmazottaihoz az Intune használatával. A rendszergazdák egyik elsődleges feladata annak biztosítása, hogy a végfelhasználók hozzáférjenek a munkájukhoz szükséges alkalmazásokhoz. 

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy felhasználót](../fundamentals/quickstart-create-user.md), [létre kell hoznia egy csoportot](../fundamentals/quickstart-create-group.md), majd [regisztálnia kell egy eszközt](../quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune](https://aka.ms/intuneportal) -ba [globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként](../fundamentals/users-add.md#types-of-administrators). Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="add-the-client-app-to-intune"></a>Az ügyfélalkalmazás hozzáadása az Intune-hoz

Az alkalmazás belefoglalásával az Intune kezelheti annak részleteit. 

A következő lépéseket követve adjon hozzá egy alkalmazást az Intune-hoz:
1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget. 
2. Válassza a **Windows 10** lehetőséget az **Alkalmazástípus** legördülő mező **Office 365 csomag** szakaszában.
3. A hozzárendelni kívánt Office-alkalmazások kiválasztásához válassza az **Alkalmazáscsomag konfigurálása** lehetőséget.
4. Az alapértelmezett alkalmazások elfogadásához kattintson az **OK** gombra.
5. Válassza az **Alkalmazáscsomag adatai** lehetőséget.
6. Adja meg a **Microsoft Office 365 alkalmazáscsomag** kifejezést a **csomag neveként**.
7. A **csomag leírásaként**adja meg **a Microsoft Office 365 App Suite** -t.
8. A **Megjelenítés kiemelt alkalmazásként a Céges portálon** lehetőségnél kattintson az **Igen** gombra.
9. Kattintson az **OK**gombra.

    ![Képernyőkép az alkalmazás adatainak hozzáadásáról](./media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

10. Válassza az **Alkalmazáscsomag beállításai** lehetőséget.
11. A **Frissítési csatorna** legördülő mezőben válassza a **Havonta** elemet.
12. Kattintson az **OK** > **Hozzáadás** lehetőségre.

## <a name="assign-the-app-to-a-group"></a>Az alkalmazás csoporthoz rendelése

Miután hozzáadott egy alkalmazást a Microsoft Intune-hoz, azt felhasználói csoportokhoz és eszközökhöz rendelheti hozzá.

> [!NOTE]
> Ez a rövid útmutató a sorozat előző rövid útmutatókra épül. Részletekért tekintse meg az útmutató [előfeltételeit](quickstart-add-assign-app.md#prerequisites).

Egy alkalmazás egy csoporthoz rendeléséhez használja a következő lépéseket:
1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **alkalmazások** > **minden alkalmazás**lehetőséget. 
2. Válassza ki a hozzárendelni kívánt alkalmazást.
3. Kattintson a **hozzárendelések** > **Csoport hozzáadása** elemre a **Csoport hozzáadása** panel megjelenítéséhez.
4. Válassza a **Regisztrált eszközökhöz elérhető** lehetőséget a **Hozzárendelés típusa** legördülő menüben. 
5. Kattintson a **Tartalmazott csoportok** > **Befoglalandó csoportok kijelölése** > **Contoso tesztelők** lehetőséget.
6. Kattintson a **Kiválasztás** > **OK** > **OK** > **Mentés** lehetőségre a csoporthoz való hozzárendeléshez.

Így hozzárendelte az alkalmazást a **Contoso tesztelők** csoporthoz.

## <a name="install-the-app-on-the-enrolled-device"></a>Az alkalmazás telepítése egy regisztrált eszközre

Az Intune-on keresztül elérhető **Contoso To-Do** alkalmazás telepítéséhez telepítenie kell a Céges portál alkalmazást. A következő lépésekkel ellenőrizze, hogy az alkalmazás elérhető a regisztrált eszköz felhasználója számára.

1. Jelentkezzen be a regisztrált Windows 10 asztali eszközén.

    > [!IMPORTANT]
    > Az eszköznek [az Intune-ban](../quickstart-enroll-windows-device.md) regisztráltnak kell lennie. Ezenkívül be kell jelentkeznie az eszközön egy olyan fiókkal, amely az alkalmazáshoz hozzárendelt csoport része.

2. A **Start** menüben nyissa meg a **Microsoft Store áruházat**. Keresse meg és telepítse a **Céges portál** alkalmazást.
3. Nyissa meg a **Céges portál alkalmazást**.
4. Kattintson az Intune-nal hozzáadott alkalmazásra. Ebben a rövid útmutatóban hozzáadta a **Microsoft Office 365 alkalmazáscsomag** alkalmazást.

    > [!NOTE]
    > Ha nem sikerült alkalmazásokat hozzárendelni az Intune-felhasználóhoz, a következő üzenet jelenik meg: *A rendszergazda nem tetten elérhetővé ezeket az alkalmazásokat.*

5. Kattintson az **Install** (Telepítés) gombra.

Ha a cég megköveteli a Céges portál alkalmazottakhoz való hozzárendelését, a Windows 10-es Céges portál alkalmazás hozzárendelése manuálisan is elvégezhető közvetlenül az Intune-ból. További információ: [A Windows 10-es Céges portál alkalmazás manuális hozzáadása a Microsoft Intune-nal](../company-portal-app.md).

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban hozzáadott alkalmazásokat az Intune-hoz, ezeket egy csoporthoz rendelte, majd telepítette őket a regisztrált Windows 10-es asztali eszközön. További információ az alkalmazások Intune-beli kezeléséről: [A Microsoft Intune-alkalmazásfelügyelet ismertetése](app-management.md)

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Alkalmazásvédelmi szabályzat létrehozása és hozzárendelése](quickstart-create-assign-app-policy.md)
