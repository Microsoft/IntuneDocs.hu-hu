---
title: Csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez
titlesuffix: Microsoft Intune
description: Csoportokat adhat hozzá azzal a céllal, hogy a felhasználókat és az eszközöket földrajzi hely, részleg vagy hardvertulajdonságok alapján rendszerezhesse.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb9ccc2f2a14f554f0f48674efe06b2935242238
ms.sourcegitcommit: fb2ca28ab0cf89202c935da3f9d98adcea20566d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57461311"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez
Az Intune Azure Active Directory- (AD-) csoportokat használ az eszközök és felhasználók kezelésére. Intune-rendszergazdaként csoportokat állíthat be a vállalat igényeinek megfelelően. Létrehozhat csoportokat a felhasználók és eszközök földrajzi hely, részleg vagy hardverjellemzők szerinti rendezéséhez. Használjon csoportokat a feladatok nagy számban való végrehajtásához. Beállíthat például szabályzatokat számos felhasználóhoz, vagy üzembe helyezhet alkalmazásokat eszközök egy csoportján.

A következő típusú csoportokat veheti fel:
- **Hozzárendelt csoportok** – Felhasználók vagy eszközök manuális hozzáadása egy statikus csoporthoz
- **Dinamikus csoportok** – (Az Azure Active Directory Premium használatánál) Lehetővé teszi egyszerű vagy speciális szabályokkal meghatározott felhasználói vagy eszközcsoportok dinamikus felépítését

## <a name="add-a-new-group"></a>Új csoport felvétele

Új csoport létrehozásához használja a következő lépéseket.
1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).
2. Válassza a **Minden szolgáltatás** > **Intune** lehetőséget. Az Intune a **Figyelés + felügyelet** szakaszban található.
3. Az **Intune** panelen válassza a **Csoportok** lehetőséget, majd válassza az **Összes csoport** panelen az **Új csoport** lehetőséget.
   ![Az Azure Portal képernyőképe a kijelölt Új csoport lehetőséggel](./media/groups-add-new.png)
4. A **csoporttípust**, a következő lehetőségek közül választhat:
    - **Biztonsági**: A biztonsági csoportok jól használhatók a felhasználói csoportok feltöltésekor. Mivel a biztonsági csoportok határozzák meg, hogy mely erőforrásokhoz kinek van hozzáférése, azok egyszerűen leképezhetők Intune felhasználói csoportokra. Biztonsági csoportok, amely szinkronizálva lesznek az Active Directoryból az Azure Active Directoryba, illetve amelyeket közvetlenül az Azure Active Directoryban, a Microsoft 365 felügyeleti központban vagy az Azure Portalon hoz létre lesznek elérhetők a felhasználói csoportok létrehozásához az Intune-ban.
    - **Office 365**

5. Adjon meg egy **neve** és **leírás** az új csoport. Ezek a tulajdonságok csak a felügyeleti portálon jelennek meg, és a felhasználók nem láthatják.

6. Válassza a **Tagságtípus**:
   - **Hozzárendelt** lehetőséget manuálisan hozzárendelt tagokkal rendelkező csoport létrehozásához. További tudnivalók az [Azure AD hozzárendelt csoportjairól](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
   - **Dinamikus felhasználó** **Dinamikus lekérdezéssel** meghatározott felhasználói csoport létrehozásához.
   - **Dinamikus eszköz** **Dinamikus lekérdezéssel** meghatározott eszközcsoport létrehozásához.

   ![Az Intune-csoporttulajdonságok képernyőképe](./media/groups-add-properties.png)

   Az Azure AD lehetővé teszi dinamikus csoportok létrehozását a tagságot meghatározó szabályok alapján. Az [attribútumalapú dinamikus csoportok létrehozásának](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal) elsajátítása.

7. Kiválaszthatja az **Engedélyezi az Office-funkciókat** lehetőséget, hogy a felhasználói csoport tagjai elérhessék a megosztott Office 365-alkalmazásokat. További információk az [Office 365-csoportokról](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
8. Az új csoport hozzáadásához válassza a **Létrehozás** lehetőséget.

## <a name="groups-and-policies"></a>Csoportok és házirendek

Csoportok létrehozásakor gondolja át, hogyan szeretné alkalmazni [házirendek](device-compliance-get-started.md). Lehetnek például az eszközök operációs rendszereire szabott, vagy a szervezet különböző szerepköreinek, illetve az Active Directoryban már definiált szervezeti egységeknek megfelelő szabályzatok. Hasznos lehet külön eszközcsoportokat létrehozni az iOS, Android és Windows operációs rendszerekhez rendelt eszközcsoportok számára, valamint külön felhasználói csoportokat az egyes szerepekörök számára a szervezeten belül.

Érdemes létrehozni egy valamennyi csoportra és eszközre vonatkozó alapértelmezett szabályzatot a szervezetre vonatkozó alapvető megfelelőségi követelmények meghatározásához. Ezt követően létrehozhatók részletesebb szabályzatok a felhasználók és eszközök legszélesebb kategóriáira. Létrehozhat például levelezési szabályzatokat az eszközök különböző operációs rendszerei számára.



## <a name="see-also"></a>Lásd még:
- [Az erőforrásokhoz való hozzáférés kezelése Azure Active Directory-csoportokkal](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Klasszikus Intune-csoportok az Azure Portalon](groups-get-started.md)
