---
title: A felhasználói entitás idővonala az adattárházban
titleSuffix: Microsoft Intune
description: Ismerje meg, hogy az Microsoft Intune adattárház hogyan jeleníti meg a felhasználókat az idősoron.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f738efd4327a5c13c1f899dee4d6c08f567187b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730127"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>A felhasználói élettartam reprezentációja a Microsoft Intune-adattárházban

Az Intune-adattárházban tárolt adatok pillanatképeinek egy hónapját időalapú trendekre vonatkozó kérdések megválaszolására használhatja fel. Például megtekintheti az egy hónap alatt felvett felhasználók számát. Azt is megtudhatja, hogy hány felhasználót távolítottak el a rendszerből.

Az ilyen típusú elemzések szolgáltatásához az adattárház előzményadatokat tárol. Az adattárház képes követni az entitások élettartamát. Rögzíti, hogy az entitást mikor hozták létre, mikor változik az állapota, és mikor kerül törlésre. A mennyiségi mérések napi pillanatképeivel rögzített előzmények használatával összehasonlíthat egy napot az előzővel, és így tovább.

Az entitások állapotváltozásai megnehezíthetik az entitások élettartamának elemzését. Ez azt jelenti, hogy ha a 30. napon tekinti meg a pillanatképet, a felhasználói rekord talán nem létezik aktív állapotban az adatok között. Lehet, hogy csak a 29-28. napon létezik aktívként, míg a 28. nap előtt egyáltalán nem is létezett a felhasználó.

A könnyebb érthetőség kedvéért az alábbiakban kövesse végig egy entitás élettartamát.

Tegyük fel, hogy egy **Kovács János** nevű felhasználóhoz 2017. június 1-én hozzárendeltek egy licencet. Ekkor a **Felhasználó** táblán a következő bejegyzés jelenik meg: 
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| Kovács János | HAMIS | 06/01/2017 | 12/31/9999 | IGAZ
 
Kovács János 2017. július 25-én visszaadja a licencét. A **Felhasználó** táblán a következő bejegyzések jelennek meg. A meglévő rekordok változásai `marked`. 

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| Kovács János | HAMIS | 06/01/2017 | `07/26/2017` | `FALSE` 
| Kovács János | IGAZ | 07/26/2017 | 12/31/9999 | IGAZ 

Az első sor azt jelzi, hogy Kovács János 2017/06/01-től 2017/07/25-ig létezett az Intune rendszerében. A második rekord azt jelzi, hogy a felhasználót 2017/07/25-én törölték, és már nincs jelen az Intune rendszerében.

Most tegyük fel, hogy Kovács János 2017. augusztus 31-én új licencet kap. Ekkor a Felhasználó táblán a következő bejegyzések olvashatók:
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| Kovács János | HAMIS | 06/01/2017 | 07/26/2017 | HAMIS 
| Kovács János | IGAZ | 07/26/2017 | `08/31/2017` | `FALSE` 
| Kovács János | HAMIS | 08/31/2017 | 12/31/9999 | IGAZ 
 
Ha az összes felhasználó jelenlegi állapotát szeretné látni, olyan szűrőt érdemes alkalmaznia, ahol `IsCurrent = TRUE`. 
 
Ha csak a létező felhasználókat szeretné látni, olyan szűrőt érdemes alkalmaznia, ahol `IsCurrent = TRUE AND IsDeleted = FALSE`.

## <a name="dimension-tables-in-the-entity-lifetime"></a>Dimenziótáblák az entitás élettartamában

Annak érdekében, hogy megőrizhesse az entitások állapotváltozásainak előzményeit, az Intune nem töröl rekordokat. Ehelyett töröltként jelöli meg a rekordot. Ez a lehetőség a helyreállítható törlés. A dimenziótábla számos metaadat-oszlopot használ a rekordok élettartamának nyomon követéséhez. 

A leggyakrabban használt metaadat-oszlopok a következők: 

| Metaadatok tulajdonságneve  | Értékek értelmezése |
|--|--|
| IsDeleted | Jelzi, hogy az entitást törölték-e az Intune rendszeréből. |
| StartDateInclusiveUTC  | Az az egyezményes világidő szerinti időpont, amikor az entitást feltöltötték az Intune-adattárházba. Lehet, hogy az entitást előbb hozták létre, és az Intune-adattárházba csak ezután importálták. |
| DeletedDateUTC  | Az az egyezményes világidő szerinti időpont, amikor az entitást törölték az Intune-ból. |  

A **Row** (Sor) előtaggal ellátott metaadat-oszlopok, mint például a **RowLastModifiedDateTimeUTC** azt mutatják, hogy az Intune-adattárházon belül mikor hoztak létre vagy módosítottak egy rekordot. Az adattárház az Intune alsóbb rétege. Ez az érték nem áll kapcsolatban az entitás Intune-beli időtartamával.  
 
Annak, aki csak a jelenleg létező dimenzióentitásokat szeretné látni, olyan szűrőt érdemes használnia, ahol **IsDeleted = FALSE**.

## <a name="next-steps"></a>További lépések

- A **Jelenlegi felhasználó** entitással kapcsolatos további információkért lásd: [Aktuális felhasználó típusú entitás referenciája](../reports-ref-current-user.md).
- A **Felhasználó** entitással kapcsolatos további információkért lásd: [Felhasználó típusú entitás referenciája](../reports-ref-user.md).
