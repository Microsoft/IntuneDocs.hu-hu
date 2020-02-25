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
ms.openlocfilehash: 19fff092f7eccfc6de2a027c7834c52698176cbf
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569166"
---
# <a name="assign-a-role-to-an-intune-user"></a>Szerepkör kiosztása Intune-felhasználóhoz

Létrehozhat egy [beépített](role-based-access-control.md#built-in-roles) vagy [Egyéni](create-custom-role.md) szerepkört egy Intune-felhasználóhoz.

A szerepkörök létrehozásához, szerkesztéséhez vagy hozzárendeléséhez a fióknak rendelkeznie kell a következő jogosultságok egyikével az Azure AD-ben:
- **Globális rendszergazda**
- **Intune-beli szolgáltatás-rendszergazda**

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **minden szerepkör**lehetőséget.

2. Az **Intune-szerepkörök – minden szerepkör** panelen válassza ki azt a beépített szerepkört, **amelyet hozzá szeretne**rendelni > **hozzárendelésekhez** > hozzárendeléshez.

5. Az **alapvető beállítások** lapon adja meg a **hozzárendelés nevét** és az opcionális **hozzárendelés leírását**, majd válassza a **tovább**lehetőséget.

6. A **felügyeleti csoportok** lapon válassza ki azt a csoportot, amely tartalmazza azt a felhasználót, akinek engedélyeket kíván adni. Kattintson a **Tovább** gombra.

7. A **hatókör (csoportok)** lapon válassza ki azt a csoportot, amely a fenti tag által felügyelni kívánt felhasználókat vagy eszközöket tartalmazza. Kattintson a **Tovább** gombra.

8. A **hatókör (címkék)** lapon válassza a címkék elemet, ahol ez a szerepkör-hozzárendelés lesz alkalmazva. Kattintson a **Tovább** gombra.

9. Ha elkészült a **felülvizsgálat + létrehozás** oldalon, válassza a **Létrehozás**lehetőséget. Az új hozzárendelés megjelenik a hozzárendelések listájában.

## <a name="next-steps"></a>További lépések
- [További információ az Intune-beli szerepköralapú hozzáférés-vezérlésről](role-based-access-control.md)
- [Egyéni szerepkör létrehozása](create-custom-role.md)


