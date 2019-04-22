---
title: Rövid útmutató – Ügyfélalkalmazás hozzáadása és hozzárendelése
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban egy ügyfélalkalmazást ad és rendel hozzá a Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/25/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4a1c81b1b2f54b15397e9e1d7451ee7ed911848
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59898513"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Gyors útmutató: Egy ügyfél alkalmazások felvételét és hozzárendelését

Ebben a rövid útmutatóban egy ügyfélalkalmazást ad és rendel hozzá a cége alkalmazottaihoz az Intune használatával. A rendszergazdák egyik elsődleges feladata annak biztosítása, hogy a végfelhasználók hozzáférjenek a munkájukhoz szükséges alkalmazásokhoz. 

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon egy ingyenes próbafiókkal](free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy felhasználót](quickstart-create-user.md), [létre kell hoznia egy csoportot](quickstart-create-group.md), majd [regisztálnia kell egy eszközt](quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be a [Intune](https://aka.ms/intuneportal) , egy [globális rendszergazda vagy egy Intune-szolgáltatásadminisztrátor](users-add.md#types-of-administrators). Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="add-the-client-app-to-intune"></a>Az ügyfélalkalmazás hozzáadása az Intune-hoz

Az alkalmazás belefoglalásával az Intune kezelheti annak részleteit. 

A következő lépéseket követve adjon hozzá egy alkalmazást az Intune-hoz:

1. Az [Intune-ban](https://aka.ms/intuneportal) válassza az **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** elemet. 
2. Válassza a **Windows 10** lehetőséget az **Alkalmazástípus** legördülő mező **Office 365 csomag** szakaszában.
3. A hozzárendelni kívánt Office-alkalmazások kiválasztásához válassza az **Alkalmazáscsomag konfigurálása** lehetőséget.
4. Az alapértelmezett alkalmazások elfogadásához kattintson az **OK** gombra.
5. Válassza az **Alkalmazáscsomag adatai** lehetőséget.
6. Adja meg a **Microsoft Office 365 alkalmazáscsomag** kifejezést a **csomag neveként**.
7. Adja meg a **Microsoft Office 365 alkalmazáscsomag** kifejezést. a **csomag leírásaként**.
8. A **Megjelenítés kiemelt alkalmazásként a Céges portálon** lehetőségnél kattintson az **Igen** gombra.
9. Kattintson az **OK** gombra.

    ![Képernyőkép az alkalmazás adatainak hozzáadásáról](media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

8. Válassza az **Alkalmazáscsomag beállításai** lehetőséget.
9. A **Frissítési csatorna** legördülő mezőben válassza a **Havonta** elemet.
10. Kattintson az **OK** > **Hozzáadás** lehetőségre.

## <a name="assign-the-app-to-a-group"></a>Az alkalmazás csoporthoz rendelése

Miután hozzáadott egy alkalmazást a Microsoft Intune-hoz, azt felhasználói csoportokhoz és eszközökhöz rendelheti hozzá.

> [!NOTE]
> Ez a rövid útmutató-sorozat előző útmutatóink épül. Részletekért tekintse meg az útmutató [előfeltételeit](quickstart-add-assign-app.md#prerequisites).

Egy alkalmazás egy csoporthoz rendeléséhez használja a következő lépéseket:
1. Az [Intune-ban](https://aka.ms/intuneportal) válassza az **Ügyfélalkalmazások** > **Alkalmazások** elemet. 
2. Válassza ki a hozzárendelni kívánt alkalmazást.   
3. Kattintson a **Hozzárendelések** > **Csoport hozzáadása** lehetőségre a **Csoport hozzáadása** panel megjelenítéséhez.
4. Válassza a **Regisztrált eszközökhöz elérhető** lehetőséget a **Hozzárendelés típusa** legördülő menüben. 
5. Kattintson a **Tartalmazott csoportok** > **Befoglalandó csoportok kijelölése** > **Contoso tesztelők** lehetőséget.
6. Kattintson a **Kiválasztás** > **OK** > **OK** > **Mentés** lehetőségre a csoporthoz való hozzárendeléshez.

Így hozzárendelte az alkalmazást a **Contoso tesztelők** csoporthoz.

## <a name="install-the-app-on-the-enrolled-device"></a>Az alkalmazás telepítése egy regisztrált eszközre

Az Intune-on keresztül elérhető **Contoso To-Do** alkalmazás telepítéséhez telepítenie kell a Céges portál alkalmazást. A következő lépésekkel ellenőrizze, hogy az alkalmazás elérhető a regisztrált eszköz felhasználója számára.

1. Jelentkezzen be a regisztrált Windows 10 asztali eszközén.

    > [!IMPORTANT]
    > Az eszköznek [az Intune-ban](quickstart-enroll-windows-device.md) regisztráltnak kell lennie. Ezenkívül be kell jelentkeznie az eszközön egy olyan fiókkal, amely az alkalmazáshoz hozzárendelt csoport része.

2. A **Start** menüben nyissa meg a **Microsoft Store áruházat**. Keresse meg és telepítse a **Céges portál** alkalmazást.
3. Nyissa meg a **Céges portál alkalmazást**.
4. Kattintson az Intune-nal hozzáadott alkalmazásra. Ebben a rövid útmutatóban hozzáadta a **Microsoft Office 365 alkalmazáscsomag** alkalmazást.

    > [!NOTE]
    > Ha Ön nem sikerült társít alkalmazások az Intune-felhasználó, a következő üzenet jelenik meg: *A rendszergazda nem hajtott végre bármely alkalmazás érhető el Önnek.*

5. Kattintson az **Install** (Telepítés) gombra.

Ha a cég megköveteli a Céges portál alkalmazottakhoz való hozzárendelését, a Windows 10-es Céges portál alkalmazás hozzárendelése manuálisan is elvégezhető közvetlenül az Intune-ból. További információ: [A Windows 10-es Céges portál alkalmazás manuális hozzáadása a Microsoft Intune-nal](store-apps-company-portal-app.md).

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban hozzáadott alkalmazásokat az Intune-hoz, ezeket egy csoporthoz rendelte, majd telepítette őket a regisztrált Windows 10-es asztali eszközön. További információ az alkalmazások Intune-beli kezeléséről: [A Microsoft Intune-alkalmazásfelügyelet ismertetése](app-management.md)

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Gyors útmutató: Létrehozása és hozzárendelése az alkalmazásvédelmi szabályzatokhoz](quickstart-create-assign-app-policy.md)
