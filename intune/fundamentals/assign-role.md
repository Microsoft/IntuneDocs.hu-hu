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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 780a248f16a8a5028875c9c2401921ea23d0af24
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540928"
---
# <a name="assign-a-role-to-an-intune-user"></a>Szerepkör kiosztása Intune-felhasználóhoz

Létrehozhat egy [beépített](role-based-access-control.md#built-in-roles) vagy [Egyéni](create-custom-role.md) szerepkört egy Intune-felhasználóhoz.

A szerepkörök létrehozásához, szerkesztéséhez vagy hozzárendeléséhez a fióknak rendelkeznie kell a következő jogosultságok egyikével az Azure AD-ben:
- **Globális rendszergazda**
- **Intune-beli szolgáltatás-rendszergazda**

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **minden szerepkör**lehetőséget.

2. Az **Intune-szerepkörök – minden szerepkör** panelen válassza ki a hozzárendelni kívánt beépített szerepkört.

3. A <*szerepkör neve*> – **Áttekintés** panelen válassza a **kezelés** > **hozzárendelések**lehetőséget.

4. Kattintson a **Hozzárendelés** elemre az Egyéni szerepkör panelen.

5. A **szerepkör-hozzárendelések** panelen adja meg a hozzárendelés **nevét** és választható **hozzárendelésének leírását** .

6. A **Tagok (csoportok)** területen válasszon ki egy csoportot, amely tartalmazza azt a felhasználót, akinek engedélyeket kíván adni.

7. **Hatókör (csoportok)** esetében válassza ki azt a csoportot, amely a fenti tag által felügyelni kívánt felhasználókat vagy eszközöket tartalmazza.

8. A **hatókör (címkék)** területen válassza a címkék lehetőséget, ahol ez a szerepkör-hozzárendelés lesz alkalmazva.

9. Ha elkészült, válassza az **OK** gombot. Az új hozzárendelés megjelenik a hozzárendelések listájában.


## <a name="next-steps"></a>További lépések
- [További információ az Intune-beli szerepköralapú hozzáférés-vezérlésről](role-based-access-control.md)
- [Egyéni szerepkör létrehozása](create-custom-role.md)
