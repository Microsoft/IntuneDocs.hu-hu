---
title: Csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez
titleSuffix: Microsoft Intune
description: Csoportokat adhat hozzá azzal a céllal, hogy a felhasználókat és az eszközöket földrajzi hely, részleg vagy hardvertulajdonságok alapján rendszerezhesse.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e3219e32ef9bea838f0c19258d0b22a99083a12
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74261565"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez

Az Intune Azure Active Directory (Azure AD) csoportokat használ az eszközök és a felhasználók felügyeletéhez. Intune-rendszergazdaként csoportokat állíthat be a vállalat igényeinek megfelelően. Létrehozhat csoportokat a felhasználók és eszközök földrajzi hely, részleg vagy hardverjellemzők szerinti rendezéséhez. Használjon csoportokat a feladatok nagy számban való végrehajtásához. Beállíthatja például, hogy a szabályzatok számos felhasználóhoz legyenek beállítva, vagy alkalmazásokat telepítsenek egy adott eszközre.

A következő típusú csoportokat veheti fel:

- **Hozzárendelt csoportok** – felhasználók vagy eszközök manuális hozzáadása egy statikus csoporthoz. 
- **Dinamikus csoportok** (prémium szintű Azure ad) – a létrehozott kifejezés alapján automatikusan hozzáadhat felhasználókat és eszközöket a felhasználói csoportokhoz vagy az eszközökhöz.

  Ha például egy felhasználót ad hozzá a felettes címéhez, a rendszer automatikusan hozzáadja a felhasználót a **minden kezelő** felhasználói csoporthoz. Vagy ha egy eszközön az iOS-eszköz operációs rendszerének típusa van, a rendszer automatikusan hozzáadja az eszközt az **összes iOS** -eszköz eszközök csoportjához.

## <a name="add-a-new-group"></a>Új csoport felvétele

Új csoport létrehozásához használja a következő lépéseket.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. **Csoportok** kiválasztása > **új csoport**:

   ![Képernyőfelvétel a Azure Portal új csoport kiválasztásával](./media/groups-add/groups-add-new.png)

3. A **csoport típusa**területen válasszon a következő lehetőségek közül:

    - **Biztonság**: a biztonsági csoportok határozzák meg, hogy kik férhetnek hozzá az erőforrásokhoz, és az Intune-beli csoportok számára ajánlott. Létrehozhat például csoportokat a felhasználók számára, például a **Charlotte alkalmazottai** vagy a **contoso összes nő**számára. Vagy létrehozhat csoportokat eszközökhöz, például az **összes iOS-eszközhöz** vagy **az összes Windows 10 tanuló eszközhöz**.

        > [!TIP]
        > A létrehozott felhasználók és csoportok is megtekinthetők a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com), Azure Active Directory felügyeleti központban és [a Azure Portal Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973). A szervezet bérlője minden területen létrehozhatja és kezelheti a csoportokat.
        >
        > Ha az elsődleges szerepköre az eszközkezelés, javasoljuk, hogy használja a [Microsoft Endpoint Manager felügyeleti központot](https://go.microsoft.com/fwlink/?linkid=2109431).

    - **Office 365**: ezek a csoportok úgy vannak kialakítva, hogy szabályozzák az Office 365-erőforrások elérését és megosztását. Létrehozhat például egy Office 365-csoportot az Outlook beérkezett fájlok vagy a naptár megosztásához. További információ: az [Office 365-csoportok megismerése](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Adja meg a **csoport nevét** és a **csoport leírását** az új csoport számára. Egyedinek kell lennie, és meg kell adni az adatokat, hogy mások tudják, mi a csoport.

    Adja meg például az **összes Windows 10-es tanuló eszköz** a csoport nevét, valamint az **összes Windows 10-es eszközt, amelyet a diákok a Contoso High School 9-12-es** verziójában használnak a csoport leírásához.

5. Adja meg a **tagság típusát**. A választható lehetőségek:

    - **Hozzárendelt**: a rendszergazdák manuálisan rendelhetnek hozzá felhasználókat vagy eszközöket a csoporthoz, és manuálisan eltávolíthatják a felhasználókat vagy az eszközöket.
    - **Dinamikus felhasználó**: a rendszergazdák tagsági szabályokat hoznak létre a tagok automatikus hozzáadásához és eltávolításához.
    - **Dinamikus eszköz**: a rendszergazdák dinamikus csoportokra vonatkozó szabályokat hoznak létre az eszközök automatikus hozzáadásához és eltávolításához.

        ![Az Intune-csoporttulajdonságok képernyőképe](./media/groups-add/groups-add-properties.png)

    További információt ezekről a tagsági típusokról és dinamikus kifejezések létrehozásáról a következő témakörben talál:

    - [Alapszintű csoport létrehozása és Tagok hozzáadása az Azure AD-vel](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Dinamikus tagsági szabályok a csoportok számára az Azure AD-ben](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > Ebben a felügyeleti központban a felhasználók vagy csoportok létrehozásakor előfordulhat, hogy nem jelenik meg a **Azure Active Directory** arculata. Azonban ezt használja.

6. Az új csoport hozzáadásához válassza a **Létrehozás** lehetőséget. A csoport megjelenik a listában.

> [!TIP]
> Vegye figyelembe a további létrehozott dinamikus felhasználói és eszközcsoport-csoportokat is, például:
>
> - A contoso Gimnázium összes tanulója
> - Minden Android Enterprise-eszköz
> - Minden iOS 11 és régebbi eszköz
> - Marketing
> - Emberi erőforrások
> - Az összes Charlotte-alkalmazott
> - Minden WA-alkalmazott

## <a name="groups-and-policies"></a>Csoportok és házirendek

A szervezet erőforrásaihoz való hozzáférést a létrehozott felhasználók és csoportok vezérlik.

A csoportok létrehozásakor gondolja át, hogyan alkalmazza a [megfelelőségi szabályzatokat](../protect/device-compliance-get-started.md) és a [konfigurációs profilokat](../configuration/device-profiles.md). Előfordulhat például, hogy:

- Az eszköz operációs rendszerére vonatkozó szabályzatok.
- A szervezet különböző szerepköreire jellemző szabályzatok.
- A Active Directoryban meghatározott szervezeti egységekre vonatkozó szabályzatok.

A szervezet alapvető megfelelőségi követelményeinek létrehozásához létrehozhat egy alapértelmezett szabályzatot, amely az összes csoportra és eszközre vonatkozik. Ezután hozzon létre konkrétabb házirendeket a felhasználók és eszközök legszélesebb kategóriáira. Létrehozhat például levelezési szabályzatokat az eszközök különböző operációs rendszerei számára.

A konfigurációs profilokkal kapcsolatos ajánlások és útmutatás: [házirendek társítása felhasználói csoportokhoz vagy](../configuration/device-profile-assign.md#user-groups-vs-device-groups) eszközcsoport- [javaslatokhoz](../configuration/device-profile-create.md#recommendations).

## <a name="see-also"></a>További információ

- [Szerepköralapú hozzáférés-vezérlés (RBAC) Microsoft Intune](role-based-access-control.md)
- [Az erőforrásokhoz való hozzáférés kezelése az Azure AD-csoportokkal](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
