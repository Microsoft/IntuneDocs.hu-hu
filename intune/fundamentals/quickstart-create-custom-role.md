---
title: Rövid útmutató – Egyéni szerepkör létrehozása és hozzárendelése az Intune-ban
description: Rövid útmutató – Egyéni szerepkör létrehozása és hozzárendelése távoli eszközkezelőhöz.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.assetid: 0b3ac749-4a61-4717-bf08-e0e6a15c3b0a
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c61449e17b96151d2717365e5193fd6c4bdaae3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509893"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>Rövid útmutató: Egyéni szerepkör létrehozása és hozzárendelése

Ezt a rövid Intune-útmutatót követve létrehozhat egy meghatározott engedélyeket biztosító egyéni szerepkört egy biztonsági üzemeltetési részleg számára. Ez után a szerepkört hozzárendelheti az ezen a területen dolgozók egy csoportjához. Több azonnal használható alapértelmezett szerepkör is létezik. Az ehhez hasonló egyéni szerepkörök létrehozásával azonban mobileszköz-kezelési rendszere minden részletét precízen szabályozhatja.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy csoportot](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune-ba](https://aka.ms/intuneportal) globális rendszergazdaként vagy Intune-beli szolgáltatásadminisztrátorként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="create-a-custom-role"></a>Egyéni szerepkör létrehozása

Egyéni szerepkör létrehozásakor a műveletek széles köréhez állíthat be engedélyeket. A biztonsági műveletek szerepköréhez beállítunk néhány olvasási jogosultságot, hogy a munkatársak áttekinthessék egy eszköz konfigurációit és a rá vonatkozó szabályzatokat.

1. Az Intune-ban válassza a **Szerepkörök** > **Minden szerepkör** > **Hozzáadás** lehetőséget.
![Böngésző](./media/quickstart-create-custom-role/add-custom-role.png)
2. Az **Egyéni szerepkör hozzáadása** alatti **Név** mezőbe írja be a *Biztonsági üzemeltetés* szöveget.
3. A **Leírás** mezőbe írja be a következőt: *Ez a szerepkör biztonsági munkatársak számára teszi lehetővé eszközök konfigurációs és megfelelőségi információinak figyelését.*
4. Válassza a **Konfigurálás** > **Vállalati eszközazonosítók** > **Olvasás** beállításnál az **Igen** > **OK** elemet.
![Böngésző](./media/quickstart-create-custom-role/corp-device-id-read.png)
5. Válassza az **Eszközmegfelelőségi szabályzatok** > **Olvasás** beállításnál az **Igen** > **OK** elemet.
6. Válassza az **Eszközkonfigurációk** >  **Olvasás** beállításnál az **Igen** > **OK** elemet.
7. Válassza a **Vállalat** > **Olvasás** beállításnál az **Igen** > **OK** elemet.
8. Válassza az **OK** > **Létrehozás** lehetőségeket.

## <a name="assign-the-role-to-a-group"></a>A szerepkör csoporthoz rendelése

Ahhoz, hogy egy biztonsági munkatárs használhassa az új engedélyeket, a szerepkört hozzá kell rendelnie egy csoporthoz, amely tartalmazza a biztonsági felhasználót.

1. Az Intune-ban válassza a **Szerepkörök** > **Minden szerepkör** > **Biztonsági műveletek** lehetőséget.
2. Az **Intune-szerepkörök** alatt válassza a **Hozzárendelések** > **Hozzárendelés** lehetőséget.
3. A **Hozzárendelés neve** mezőbe írja be a *Bizt. üz.* nevet.
4. Válassza a **Tag (Csoportok)**  > **Hozzáadás** lehetőséget.
5. Jelölje ki a **Contoso tesztelők** csoportot.
6. Válassza a **Kiválasztás** > **OK** lehetőséget.
7. Válassza a **Hatókör (Csoportok)**  > **Befoglalandó csoportok kijelölése** > **Contoso tesztelők** lehetőséget.
8. Válassza a **Kiválasztás** > **OK** > **OK** lehetőséget.

A csoportban már mindenki tagja a *Biztonsági üzemeltetés* szerepkörnek, és megtekintheti az eszközzel kapcsolatos következő információkat: vállalati eszközazonosítók, eszközmegfelelőségi szabályzatok, eszközkonfigurációk és vállalati információk.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha nem kívánja többé használni az új egyéni szerepkört, törölheti. Válassza a **Szerepkörök** > **Minden szerepkör** > a szerepkör melletti három pont > **Törlés** lehetőséget.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban létrehozta az egyéni Biztonsági üzemeltetés szerepkört, és hozzárendelte egy csoporthoz. További információ az Intune szerepköreiről: [Szerepköralapú hozzáférés-vezérlés (RBAC) a Microsoft Intune-nal](role-based-access-control.md)

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: E-mail-eszközprofil létrehozása iOS-hez](../configuration/quickstart-email-profile.md)
