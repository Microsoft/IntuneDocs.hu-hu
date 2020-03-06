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
ms.openlocfilehash: dfb9ec9d28b00e454884bbf0bf296cd72cba4b6f
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369804"
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

A hatókör alapértelmezett címkéje funkció a Microsoft Endpoint Configuration Manager biztonsági hatókörök funkciójának hasonló. 

## <a name="to-create-a-scope-tag"></a>Hatókörcímke létrehozása

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **hatókör (címkék)**  > **Létrehozás**lehetőséget.
2. Az **alapok** lapon adja meg a **nevet** és a **leírást**(nem kötelező). Kattintson a **Tovább** gombra.
3. A **hozzárendelések** lapon válassza ki azokat a csoportokat, amelyek az ehhez a hatókörhöz hozzárendelni kívánt eszközöket tartalmazzák. Kattintson a **Tovább** gombra.
4. A **felülvizsgálat + létrehozás** lapon válassza a **Létrehozás**lehetőséget.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Hatókörcímke hozzárendelése egy szerepkörhöz

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **szerepkörök** > **minden szerepkör** lehetőséget, > válassza ki a szerepkört > **hozzárendelések** > **hozzárendelés**elemet.
2. Az **alapvető beállítások** lapon adja meg a **hozzárendelés nevét** és **leírását**. Kattintson a **Tovább** gombra.
3. A **felügyeleti csoportok** lapon válassza ki a **felvenni kívánt csoportokat**, majd válassza ki azokat a csoportokat, amelyeket a hozzárendelés részeként szeretne használni. A csoport felhasználói jogosultak lesznek a hatókör (csoportok) felhasználói/eszközeinek kezelésére. Kattintson a **Tovább** gombra.

    ![Képernyőfelvétel a csoporttag kiválasztásáról.](./media/scope-tags/select-member-groups.png)

4. A **hatóköri csoportok** lapon válassza ki a következő lehetőségek egyikét a **hozzárendeléshez** :
    - **Kiválasztott csoportok**: válassza ki azokat a csoportokat, amelyek a kezelni kívánt felhasználókat/deivces tartalmazzák. A kiválasztott csoportokban lévő összes felhasználó/eszköz felügyeletét a rendszergazda csoportok felhasználói fogják kezelni.
    - **Minden felhasználó**: az összes felhasználót a rendszergazda csoportok felhasználói kezelhetik.
    - **Minden eszköz**: az összes eszközt a rendszergazda csoportok felhasználói kezelhetik.
    - **Minden felhasználó és minden eszköz**: minden felhasználó és eszköz felügyelhető a rendszergazda csoportok felhasználóinak használatával.

5. Kattintson a **Tovább** gombra.
6. A **hatókör címkék** lapon válassza ki a szerepkörhöz hozzáadni kívánt címkéket. A rendszergazda csoportok felhasználói hozzáférhetnek az olyan Intune-objektumokhoz, amelyek szintén rendelkeznek ugyanazzal a hatóköri címkével.
7. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot, majd válassza a **Létrehozás**lehetőséget.

## <a name="assign-scope-tags-to-other-objects"></a>Hatókör-címkék társítása más objektumokhoz

A hatókör címkéit támogató objektumok esetében a hatókör címkéi általában a **Tulajdonságok**területen jelennek meg. Ha például hatókör-címkét szeretne hozzárendelni egy konfigurációs profilhoz, kövesse az alábbi lépéseket:

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **konfigurációs profilok** lehetőséget, > válasszon egy profilt.

2. Válassza a **tulajdonságok** > **hatókör (címkék)**  > **Szerkesztés** > **válassza a hatókör címkék elemet** > Válassza ki a profilhoz hozzáadni kívánt címkéket.
4. Válassza a kijelölés > **felülvizsgálat + mentés** **lehetőséget** .

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


