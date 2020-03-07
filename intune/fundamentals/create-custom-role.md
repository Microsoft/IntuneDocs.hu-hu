---
title: Egyéni szerepkör létrehozása az Intune-ban
description: Ismerje meg, hogyan hozhat létre egyéni szerepkört a Microsoft Intuneban.
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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369805"
---
# <a name="create-a-custom-role-in-intune"></a>Egyéni szerepkör létrehozása az Intune-ban

Létrehozhat egy egyéni Intune-szerepkört, amely tartalmazza az adott feladat függvényéhez szükséges engedélyeket is. Például ha egy IT-részleg alkalmazásokat, szabályzatokat, és konfigurációs profilokat kezel, mindezeket az engedélyeket együtt adhatja meg egy egyéni szerepkör segítségével. Egyéni szerepkör létrehozása után [hozzárendelheti](assign-role.md) azt bármely olyan felhasználóhoz, akinek szüksége van rájuk.

A szerepkörök létrehozásához, szerkesztéséhez vagy hozzárendeléséhez a fióknak rendelkeznie kell a következő jogosultságok egyikével az Azure AD-ben:
- **Globális rendszergazda**
- **Intune-beli szolgáltatás-rendszergazda**

## <a name="to-create-a-custom-role"></a>Egyéni szerepkör létrehozása

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **minden szerepkör** > **Létrehozás**lehetőséget.

2. Az **alapvető beállítások** lapon adja meg az új szerepkör nevét és leírását, majd válassza a **tovább**lehetőséget.

3. Az **engedélyek** lapon válassza ki a szerepkörhöz használni kívánt engedélyeket.

4. A **hatókör (címkék)** lapon válassza ki a szerepkörhöz tartozó címkéket. Ez a szerepkör hozzáférhet a címkével ellátható erőforrásokhoz is. Kattintson a **Tovább** gombra.

5. Ha elkészült a **felülvizsgálat + létrehozás** oldalon, válassza a **Létrehozás**lehetőséget. Az új szerepkör megjelenik az **Intune-szerepkörök – minden szerepkör** panel listájában.

## <a name="copy-a-role"></a>Szerepkör másolása

Egy meglévő szerepkört is másolhat.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **minden szerepkör** lehetőséget, > jelölje be a listában szereplő egyik szerepkör jelölőnégyzetét > **duplikált**elemnél.

2. Az **alapvető beállítások** lapon adjon meg egy nevet. Ügyeljen arra, hogy egyedi nevet használjon.

3. Az eredeti szerepkör összes engedélye és hatókör-címkéje már ki lesz választva. Ezt követően módosíthatja az ismétlődő szerepkör **nevét**, **leírását**, **engedélyeit**és **hatókörét (címkéket)** .

4. Miután elvégezte az összes szükséges módosítást, kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap beszerzéséhez. Válassza a **Létrehozás** lehetőséget. 

## <a name="next-steps"></a>További lépések
- [Szerepkör társítása felhasználóhoz](assign-role.md)
- [További információ az Intune-beli szerepköralapú hozzáférés-vezérlésről](role-based-access-control.md)


