---
title: Rövid útmutató – Automatikus regisztráció beállítása az Intune-ban
description: Rövid útmutató – Windows 10-es eszközök automatikus regisztrációjának beállítása az Intune-ban.
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5cc7cf3661caa2b2640d9370d26402b7702d36b
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541038"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Rövid útmutató: Windows 10-es eszközök automatikus regisztrációjának beállítása

Ezt a rövid útmutatót követve beállíthatja, hogy a Microsoft Intune automatikusan regisztrálja az eszközöket, amikor bizonyos felhasználók bejelentkeznek a Windows 10 rendszerű eszközeikkel.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Microsoft Intune-előfizetés – [regisztráljon egy ingyenes próbafiókkal](../fundamentals/free-trial-sign-up.md).
- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy felhasználót](../fundamentals/quickstart-create-user.md), majd [létre kell hoznia egy csoportot](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Bejelentkezés az Intune-ba a Microsoft Endpoint Managerben

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10-es eszközök automatikus regisztrációjának beállítása

Ebben a példában MDM-regisztrációt fogunk használni, hogy a vállalati és saját tulajdonban lévő eszközök is automatikusan regisztrálhatók legyenek. Egy ingyenes Azure Active Directory Premium-előfizetésre regisztrál.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **minden szolgáltatás** > **M365 Azure Active Directory** > **Azure Active Directory** > **mobilitás (Mdm és MAM)** lehetőséget.
2. Válassza **A szolgáltatás használatához szerezze be az ingyenes Prémium szintű próbaverziót** lehetőséget. Ezt a lehetőséget választva engedélyezi az Azure Active Directory ingyenes Premium-próbaverziójával történő automatikus regisztrációt. 

    ![Az Azure Active Directory ingyenes Premium-próbaverziójának kiválasztása](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

3. Válassza az **Enterprise Mobility + Security E5** ingyenes próbaverzió lehetőséget. 
4. Kattintson az **ingyenes próbaverzió** > **aktiválja** az ingyenes próbaverziót.

    ![Az Enterprise Mobility + Security E5 ingyenes próbaverzió lehetőség kiválasztása](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

    > [!NOTE]
    > Az aktiváláshoz egy percet is igénybe vehet. 

3. Az Intune konfigurálásához válassza a **Microsoft Intune** lehetőséget. 

    ![A Microsoft Intune kiválasztása a listából](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Válassza az **MDM-felhasználói hatókör** területen a **Néhány** lehetőséget a felhasználók Windows-eszközein található vállalati adatok automatikus MDM-regisztrációval való kezeléséhez. Az automatikus MDM-regisztráció az AAD-hez csatlakoztatott eszközök és saját eszközök használatának esetén lesz konfigurálva.

    ![A „Néhány” elem kiválasztása a konfigurációs listából](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Kattintson a **csoportok kiválasztása** > **Contoso-tesztelők** > **válassza ki** a hozzárendelt csoportként lehetőséget.

    ![Válassza ki a regisztrálandó csoportot](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Válassza a **Néhány** lehetőséget az **MDM-felhasználói hatókör** területen az adatok az alkalmazottak eszközein való kezeléséhez.

    ![Válassza ki a regisztrálandó csoportot](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-06.png)

7. Válassza a **Csoportok kijelölése** > **Contoso tesztelők** > **Kiválasztás** lehetőséget a kijelölt csoportként. 
8. A hátralévő konfigurációs értékekhez használja az alapértelmezett értékeket.
9. Válassza a **Mentés** elemet.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Az Intune-beli automatikus regisztráció újrakonfigurálásával kapcsolatban olvassa el a [Windows-eszközök regisztrációjának beállítása](windows-enroll.md) című cikket.

## <a name="next-steps"></a>További lépések

Ebből a rövid útmutatóból megtanulhatta a Windows 10-es eszközök automatikus regisztrációjának beállítását. További információt az eszközregisztrációról a [Mi az eszközregisztrálás?](device-enrollment.md) című témakörben találhat

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Windows 10 rendszerű eszköz regisztrálása](../quickstart-enroll-windows-device.md)
