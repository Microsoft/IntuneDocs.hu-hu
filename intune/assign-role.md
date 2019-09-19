---
title: Szerepkör kiosztása Intune-felhasználóhoz
description: Megtudhatja, hogyan rendelhet hozzá beépített vagy egyéni szerepkört egy felhasználóhoz Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83e321e932fa2214612836ec994a9a0aa8174dd7
ms.sourcegitcommit: 49f25efb9bc0f16f587f27878cf45de5e4e6a27f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/18/2019
ms.locfileid: "71094682"
---
# <a name="assign-a-role-to-an-intune-user"></a>Szerepkör kiosztása Intune-felhasználóhoz

Létrehozhat egy [beépített](role-based-access-control.md#built-in-roles) vagy [Egyéni](create-custom-role.md) szerepkört egy Intune-felhasználóhoz.

A szerepkörök létrehozásához, szerkesztéséhez vagy hozzárendeléséhez a fióknak rendelkeznie kell a következő jogosultságok egyikével az Azure AD-ben:
- **Globális rendszergazda**
- **Intune-beli szolgáltatás-rendszergazda**

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).

2. Válassza a **Minden szolgáltatás** > **Intune** lehetőséget. Az Intune a **Figyelés + felügyelet** szakaszban található.

3. Az **Intune** panelen válassza a **szerepkörök** > **minden szerepkör**lehetőséget.

4. Az **Intune-szerepkörök – minden szerepkör** panelen válassza ki a hozzárendelni kívánt beépített szerepkört.

5. A <*szerepkör neve*> – **Áttekintés** panelen válassza a **kezelés** > **hozzárendelések**lehetőséget.

6. Kattintson a **Hozzárendelés** elemre az Egyéni szerepkör panelen.

7. A **szerepkör-hozzárendelések** panelen adja meg a hozzárendelés **nevét** és választható **hozzárendelésének leírását** .

8. A **Tagok (csoportok)** területen válasszon ki egy csoportot, amely tartalmazza azt a felhasználót, akinek engedélyeket kíván adni.

9. **Hatókör (csoportok)** esetében válassza ki azt a csoportot, amely a fenti tag által felügyelni kívánt felhasználókat vagy eszközöket tartalmazza.

10. A **hatókör (címkék)** területen válassza a címkék lehetőséget, ahol ez a szerepkör-hozzárendelés lesz alkalmazva.

11. Ha elkészült, válassza az **OK** gombot. Az új hozzárendelés megjelenik a hozzárendelések listájában.


## <a name="next-steps"></a>További lépések
- [További információ az Intune-beli szerepköralapú hozzáférés-vezérlésről](role-based-access-control.md)
- [Egyéni szerepkör létrehozása](create-custom-role.md)
