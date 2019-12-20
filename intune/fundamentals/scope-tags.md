---
title: A szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata az Intune-ban való terjesztéshez | Microsoft Docs
description: Hatókörcímkékkel a konfigurációs profilokat meghatározott szerepkörök szerint szűrheti.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c2ec3ab62c6effd80d6a02d6ae9052b41fed23c
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207322"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>A szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez

A szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használatával ellenőrizheti, hogy a megfelelő rendszergazdák rendelkeznek-e megfelelő hozzáféréssel, és hogy láthatók-e a megfelelő Intune-objektumok. A szerepkörök határozzák meg, hogy mely hozzáférési rendszergazdák rendelkezzenek az objektumokkal. A hatókör-címkék határozzák meg, hogy mely objektumok adminisztrátorai láthatják.

Tegyük fel például, hogy a Seattle regionális iroda rendszergazdája a szabályzat és a profil Manager szerepkörrel rendelkezik. Azt szeretné, hogy ez a rendszergazda csak a Seattle-eszközökre érvényes profilokat és házirendeket tekintse meg és kezelje. A hozzáférés beállításához a következőket kell tennie:

1. Hozzon létre egy Seattle nevű hatókör-címkét.
2. Hozzon létre egy szerepkör-hozzárendelést a házirend és a profil-kezelő szerepkörhöz a következővel: 
    - Tagok (csoportok) = egy Seattle informatikai rendszergazdák nevű biztonsági csoport. Az ebben a csoportban található összes rendszergazda jogosult a házirendek és profilok kezelésére a hatókörben (csoportok) lévő felhasználók és eszközök számára.
    - Hatókör (csoportok) = egy Seattle-felhasználók nevű biztonsági csoport. A csoportban lévő összes felhasználó/eszköz rendelkezhet a tagok (csoportok) rendszergazdái által felügyelt profilokkal és szabályzatokkal. 
    - Hatókör (címkék) = Seattle. A tag (csoportok) rendszergazdái megtekinthetik a Seattle hatókör címkével is rendelkező Intune-objektumokat.
3. Adja hozzá a Seattle-beli hatókör címkét olyan házirendekhez és profilokhoz, amelyekhez a tagok (csoportok) rendszergazdáit szeretné elérni.
4. Adja hozzá a Seattle scope címkét a tagok (csoportok) rendszergazdái számára megjeleníteni kívánt eszközökhöz. 

## <a name="default-scope-tag"></a>Alapértelmezett hatókör címkéje
A rendszer automatikusan hozzáadja az alapértelmezett hatóköri címkét a hatókör címkéit támogató összes címkézetlen objektumhoz.

Az alapértelmezett hatókör címke funkció a System Center Configuration Manager biztonsági hatókörök szolgáltatásához hasonló. 

## <a name="to-create-a-scope-tag"></a>Hatókörcímke létrehozása

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **hatókör (címkék)** > **Létrehozás**lehetőséget.

    ![Képernyőkép a hatókör-címke létrehozásáról.](./media/scope-tags/create-scope-tag.png)

2. Adja meg a **nevet** és a **leírást**(nem kötelező).
3. Ha azt szeretné, hogy az összes eszköz adott csoportokban legyen, válassza **a hatókör címke kiosztása a kijelölt csoportokban lévő összes eszközhöz**lehetőséget.
    1. A **szerepeltetni kívánt csoportok kiválasztása** lapon válassza ki azokat az eszközöket, amelyekhez hozzá szeretné rendelni a hatókör címkéjét.
    2. Válassza a **Kijelölés** elemet.
4. Válassza a **Létrehozás** lehetőséget.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Hatókörcímke hozzárendelése egy szerepkörhöz

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **minden szerepkör** lehetőséget, > válassza ki a szerepkört > **hozzárendelések** > **hozzárendelés**elemet.
2. Adja meg a **hozzárendelés nevét** és **leírását**.
3. Válassza a **Tagok (csoportok)** > **Hozzáadás** > Válassza ki a hozzárendelés részeként használni kívánt csoportokat > válassza a > **OK** **lehetőséget** . A csoport felhasználói jogosultak lesznek a hatókör (csoportok) felhasználói/eszközeinek kezelésére.

    ![Képernyőfelvétel a csoporttag kiválasztásáról.](./media/scope-tags/select-member-groups.png)

4. Ha egy adott csoportba tartozó felhasználókat vagy eszközöket szeretne felügyelni, válassza a **hatókör (csoportok)** lehetőséget > **kiválasztott csoportok** > **válassza** ki a csoportokat, > válassza ki a csoportokat > válassza a > **OK** **elemet** . A csoport összes felhasználóját/eszközét a tagok (csoport) rendszergazdái fogják kezelni.

    ![Képernyőkép a hatókör-csoportok kiválasztásáról.](./media/scope-tags/select-scope-groups.png)

    Másik lehetőségként kiválaszthatja **az**összes eszközt, **az összes felhasználót**vagy **az összes felhasználót & minden eszközön**.

    ![Képernyőkép a hatókör-csoportok kiválasztásának egyéb lehetőségeiről.](./media/scope-tags/scope-group-other-options.png)
    
5. Válassza a **hatókör (címkék)** > **Hozzáadás** > Válassza ki a szerepkörhöz hozzáadni kívánt címkéket > válassza a > **OK** **lehetőséget** . A tagok (csoportok) felhasználói hozzáférhetnek az olyan Intune-objektumokhoz, amelyek szintén rendelkeznek ugyanazzal a hatóköri címkével.

    ![Képernyőkép a hatóköri címkék kiválasztásáról.](./media/scope-tags/select-scope-tags.png)

6. Válassza az **OK** gombot. 

## <a name="assign-scope-tags-to-other-objects"></a>Hatókör-címkék társítása más objektumokhoz

A hatókör címkéit támogató objektumok esetében a hatókör címkéi általában a **Tulajdonságok**területen jelennek meg. Ha például hatókör-címkét szeretne hozzárendelni egy konfigurációs profilhoz, kövesse az alábbi lépéseket:

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **konfigurációs profilok** lehetőséget, > válasszon egy profilt.

2. Válassza a **tulajdonságok** > **hatókör (címkék)** > **Hozzáadás**elemet.

    ![Képernyőkép a hatókör-címkék hozzáadásáról.](./media/scope-tags/add-scope-tags.png)

3. A **címkék kiválasztása**területen válassza ki azokat a címkéket, amelyeket hozzá szeretne adni a profilhoz.
4. Válassza a **kijelölés** > **OK** > **Mentés**lehetőséget.


## <a name="scope-tag-details"></a>Hatóköri címke részletei
A hatókör-címkék használatakor jegyezze fel ezeket a részleteket: 

- Ha a bérlő az objektum több verzióját is használhatja (például szerepkör-hozzárendeléseket vagy alkalmazásokat), hozzárendelhet hatóköri címkéket az Intune-objektumhoz.
  A következő Intune-objektumok kivételek ehhez a szabályhoz, és jelenleg nem támogatják a hatókör címkéit:
    - Windows ESP-profilok
    - Eszközök kategóriái
    - Regisztrációs korlátozások
    - Corp-eszközök azonosítói
    - Autopilot-eszközök
    - Eszköz megfelelőségi helyei
    - JAMF-eszközök
- A VPP-tokenhez társított VPP-alkalmazások és-e-könyvek öröklik a társított VPP-tokenhez hozzárendelt hatóköri címkéket.
- A DEP-tokenhez társított Készülékregisztrációs program (DEP) eszközök és DEP-profilok öröklik a társított DEP-tokenhez hozzárendelt hatóköri címkéket.
- Amikor egy rendszergazda létrehoz egy objektumot az Intune-ban, a rendszergazda számára hozzárendelt összes hatókör-címke automatikusan hozzá lesz rendelve az új objektumhoz.
- Az Intune-RBAC nem vonatkozik Azure Active Directory szerepkörökre. Így az Intune szolgáltatás-rendszergazdák és a globális rendszergazdák szerepkörök teljes körű rendszergazdai hozzáféréssel rendelkeznek az Intune-hoz, függetlenül attól, hogy milyen hatókörű címkéket használnak.
- Ha egy szerepkör-hozzárendelésnek nincs hatókör-címkéje, a rendszergazda a rendszergazdák engedélyei alapján láthatja az összes objektumot. Azok a rendszergazdák, akik nem rendelkeznek hatóköri címkékkel, lényegében minden hatókör-címkével rendelkeznek.
- Csak a szerepkör-hozzárendelésekben található hatókör-címkét lehet hozzárendelni.
- Csak azok a csoportok jelennek meg, amelyek szerepelnek a szerepkör-hozzárendelés hatókörében (csoportokban).
- Ha a szerepkörhöz hozzárendelt hatókör-címkével rendelkezik, nem törölheti az összes hatókör-címkét egy Intune-objektumon. Legalább egy hatókör-címkét kötelező megadni.

## <a name="next-steps"></a>További lépések

Megtudhatja, hogyan viselkedjenek a hatókör-címkék [több szerepkör-hozzárendelés](role-based-access-control.md#multiple-role-assignments)esetén.
A [szerepkörök](role-based-access-control.md) és a [profilok](../configuration/device-profile-assign.md) kezelése.
