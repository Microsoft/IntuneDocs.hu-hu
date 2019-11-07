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
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78620818bfd13f0292e159c6a3670b5e3af53dab
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709494"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Rövid útmutató: Windows 10-es eszközök automatikus regisztrációjának beállítása

Ezt a rövid útmutatót követve beállíthatja, hogy a Microsoft Intune automatikusan regisztrálja az eszközöket, amikor bizonyos felhasználók bejelentkeznek a Windows 10 rendszerű eszközeikkel.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Microsoft Intune-előfizetés – [regisztráljon egy ingyenes próbafiókkal](../fundamentals/free-trial-sign-up.md).
- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy felhasználót](../fundamentals/quickstart-create-user.md), majd [létre kell hoznia egy csoportot](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10-es eszközök automatikus regisztrációjának beállítása

Ebben a példában MDM-regisztrációt fogunk használni, hogy a vállalati és saját tulajdonban lévő eszközök is automatikusan regisztrálhatók legyenek. Egy ingyenes Azure Active Directory Premium-előfizetésre regisztrál.

1. Az Azure-ban válassza az **Azure Active Directory** > **Mobilitás (MDM és MAM)** lehetőséget.
2. Válassza **A szolgáltatás használatához szerezze be az ingyenes Prémium szintű próbaverziót** lehetőséget. Ezt a lehetőséget választva engedélyezi az Azure Active Directory ingyenes Premium-próbaverziójával történő automatikus regisztrációt. 

    ![Az Azure Active Directory ingyenes Premium-próbaverziójának kiválasztása](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    Válassza az **Enterprise Mobility + Security E5** ingyenes próbaverzió lehetőséget. Emellett **aktiválnia** kell az ingyenes próbaverziót.

    ![Az Enterprise Mobility + Security E5 ingyenes próbaverzió lehetőség kiválasztása](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. Válassza a **Microsoft Intune** elemet. 

    ![A Microsoft Intune kiválasztása a listából](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Válassza az **MDM-felhasználói hatókör** területen a **Néhány** lehetőséget a felhasználók Windows-eszközein található vállalati adatok automatikus MDM-regisztrációval való kezeléséhez. Az automatikus MDM-regisztráció az AAD-hez csatlakoztatott eszközök és saját eszközök használatának esetén lesz konfigurálva.

    ![A „Néhány” elem kiválasztása a konfigurációs listából](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Válassza a **Csoportok kijelölése** > **Contoso tesztelők** > **Kiválasztás** lehetőséget a kijelölt csoportként.

    ![Válassza ki a regisztrálandó csoportot](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Válassza a **Néhány** lehetőséget az **MDM-felhasználói hatókör** területen az adatok az alkalmazottak eszközein való kezeléséhez.
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
