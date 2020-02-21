---
title: Szabályzat-készletek
titleSuffix: Microsoft Intune
description: A házirend-készletek használatával csoportosíthatja a felügyeleti objektumok gyűjteményeit Microsoft Intuneban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48bfe727615f5165fc70ed2e08f98f01203dc895
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514829"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Csoportházirend-készletek használata a felügyeleti objektumok gyűjteményének csoportosításához

A házirend-készletek lehetővé teszik, hogy a már meglévő felügyeleti entitásokra mutató hivatkozásokat hozzon létre, amelyeket egyetlen fogalmi egységként kell azonosítani, megcélozni és figyelni. A házirend-készlet az alkalmazások, házirendek és egyéb létrehozott felügyeleti objektumok hozzárendelhető gyűjteménye. Egy házirend-készlet létrehozása lehetővé teszi, hogy egyszerre több különböző objektumot jelöljön ki, és azokat egyetlen helyről rendelje hozzá. A szervezet megváltozásakor újra felkeresheti az objektumokat és a hozzárendeléseket, vagy eltávolíthatja azokat. Egy házirend-készletet használhat meglévő objektumok, például alkalmazások, házirendek és virtuális magánhálózatok társítására és hozzárendelésére egyetlen csomagban. 

> [!IMPORTANT]
> A házirend-készletekkel kapcsolatos ismert problémák listáját a [szabályzatok ismert problémákkal határozzák](~/fundamentals/policy-sets.md#policy-sets-known-issues)meg.

A házirend-készletek nem helyettesítik a meglévő fogalmakat vagy objektumokat. Továbbra is hozzárendelhet egyedi objektumokat, és egy házirend-készlet részeként is hivatkozhat egyes objektumokra. Ezért az egyes objektumok módosításai a házirend-készletben is megjelennek. 

A következő házirend-készleteket használhatja:

- Az egymáshoz hozzárendelni kívánt objektumok csoportosítása
- A szervezet minimális konfigurációs követelményeinek kiosztása az összes felügyelt eszközön
- Gyakran használt vagy kapcsolódó alkalmazások társítása az összes felhasználóhoz

A következő felügyeleti objektumokat veheti fel egy házirend-készletbe:
- Apps
- Alkalmazáskonfigurációs szabályzatok
- Alkalmazásvédelmi szabályzatok
- Eszközkonfigurációs profilok
- Eszközmegfelelőségi szabályzatok
- Eszköz típusának korlátozásai
- Windows Autopilot Deployment-profilok
- Beléptetés állapota oldal

Házirend-készlet létrehozásakor a hozzárendelések egyetlen egységét kell létrehoznia, és kezelni kell a különböző objektumok közötti társításokat. Egy házirend-készlet a külső objektumokra mutató hivatkozás lesz. A befoglalt objektumok módosításai is hatással lesznek a házirend-készletre. Miután létrehozta a szabályzatot, többször is megtekintheti és szerkesztheti az objektumait és hozzárendeléseit. 

> [!NOTE]
> A házirend-készletek támogatják a Windows, az Android, a macOS és az iOS/iPadOS beállításait, és több platformot is hozzá lehet rendelni.

## <a name="how-to-create-a-policy-set"></a>Házirend-készlet létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **házirend-készletek** > **szabályzatok** > **Létrehozás**lehetőséget.
3. Az **alapvető beállítások** lapon adja hozzá a következő értékeket:
    - **Házirend-készlet neve** – adja meg a házirend-készlet nevét.
    - **Leírás** – nem kötelezően megadhatja a házirend-készlet leírását.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Kattintson a **Tovább gombra: az alkalmazás kezelése**lehetőségre.<br>
   Az **alkalmazás-kezelés** lapon opcionálisan [hozzáadhat alkalmazásokat](~/apps/apps-add.md), alkalmazás- [konfigurációs házirendeket](~/apps/app-configuration-policies-overview.md)és alkalmazás- [védelmi házirendeket](~/apps/app-protection-policy.md) a házirend-készlethez. További információ az alkalmazások kezeléséről: [Mi az Microsoft Intune app Management?](~/apps/app-management.md). 
5. Kattintson a **Tovább gombra: eszközkezelés**.<br>
   Az **eszközkezelés** lapon felügyeleti objektumokat adhat hozzá a házirend-készlethez, például az [eszköz konfigurációs profiljaihoz](~/configuration/device-profiles.md) és az [eszköz megfelelőségi házirendjeihez](~/protect/device-compliance-get-started.md). Ügyeljen arra, hogy az összes társított objektumot, például az egyéb szabályzatokat, tanúsítványokat és biztonsági alapprofilokat is tartalmazza.
6. Kattintson a **Tovább gombra: eszközök beléptetése**.<br>
   Az **eszközök beléptetése** lapon hozzáadhat eszközök beléptetési objektumokat a házirend-készlethez, például az [eszközök típusának korlátozásait](~/enrollment/enrollment-restrictions-set.md), a [Windows Autopilot üzembe helyezési profilokat](~/enrollment/enrollment-autopilot.md)és a [regisztrációs állapot lap profilokat](~/enrollment/windows-enrollment-status.md).
7. Kattintson a **Tovább: hozzárendelések**elemre.<br>
   A **hozzárendelések** lapon beállíthatja a szabályzatot a felhasználókhoz és az eszközökhöz. Fontos megjegyezni, hogy hozzárendelhet egy házirendet egy eszközhöz, függetlenül attól, hogy az eszközt az Intune felügyeli-e.
8. Kattintson a **Tovább gombra: felülvizsgálat + létrehozás** elemre, és tekintse át a profilhoz megadott értékeket.
9. Ha elkészült, kattintson a **Létrehozás** gombra a szabályzat az Intune-ban való létrehozásához. 

## <a name="policy-sets-known-issues"></a>A szabályzatok ismert problémákat állítanak be

A házirendek új, 1910-as számú házirend-készlete a következő ismert problémákkal rendelkezik.

- Házirend-készlet létrehozásakor, ha egy hatókörrel rendelkező rendszergazda egy hatóköri címke nélkül próbál létrehozni egy házirend-készletet, a **felülvizsgálat + létrehozás** lap elérésekor az érvényesítés sikertelen lesz, és hibaüzenet jelenik meg az állapotsoron. A rendszergazdának a folyamat egy másik lapjára kell váltania, majd vissza kell térnie a **felülvizsgálat + létrehozás** lapra. Ez engedélyezi a **létrehozási** beállítást.  
 
- A házirend-készletek jelenleg a következő típusú alkalmazásokat támogatják:
    - iOS/iPadOS áruházbeli alkalmazás
    - iOS/iPadOS üzletági alkalmazás
    - Felügyelt iOS/iPadOS üzletági alkalmazás
    - Android store app
    - Üzletági Android-alkalmazás
    - Felügyelt androidos üzletági alkalmazás
    - Office 365 ProPlus csomag (Windows 10)
    - Webes hivatkozás
    - Beépített iOS-/iPadOS-alkalmazás
    - Beépített Android-alkalmazás

- Nem támogatott, hogy az **összes felhasználóra** vonatkozó szabályzat-hozzárendelést az **Autopilot-profilhoz** lehessen beállítani.

- A házirend-készletek a következő regisztrációs korlátozásokkal és a regisztrációs állapot oldalával (ESP) kapcsolatos problémákkal rendelkeznek:
    - A korlátozások és az ESP nem támogatja a virtuális csoportok hozzárendeléseit.
    - A korlátozások és az ESP nem támogatja szigorúan a kizárási csoport hozzárendeléseit. 
    - A korlátozások és az ESP a Priority-alapú ütközések feloldását használja. Előfordulhat, hogy a korlátozásokat és az ESP-t nem lehet ugyanazokra a felhasználókra alkalmazni, mint a házirend-készlet többi hasznos adatát, ha a korlátozásokat és az ESP-t egy magasabb prioritású korlátozás és ESP is célozza.
    - Az alapértelmezett korlátozások és az ESP nem vehető fel egy házirend-készletbe.

- A szabályzatokat támogató MAM-szabályzatok típusai a következők: 
    - MAM-beli BEFEJEZő (Windows) MDM megcélzó felügyelt alkalmazások védelme 
    - MAM iiOS/iPadOSOS megcélzó felügyelt alkalmazások védelme
    - MAM Android megcélozott felügyelt alkalmazások védelme
    - MAM iOS/iPadOS megcélozt felügyelt alkalmazás konfigurációja
    - MAM Android megcélozott felügyelt alkalmazás konfigurációja

- A szabályzatot nem támogató MAM-szabályzatok a következők: 
    - MAM-beli folyamatban lévő (Windows) felügyelt alkalmazások védelme

- A MAM dolgozza fel a hozzárendeléseket a következő típusú házirendek közvetlen hozzárendeléseiként:
    - MAM iOS/iPadOS megcélzó felügyelt alkalmazások védelme
    - MAM Android megcélozott felügyelt alkalmazások védelme
    - MAM iOS/iPadOS megcélozt felügyelt alkalmazás konfigurációja
    - MAM Android megcélozott felügyelt alkalmazás konfigurációja

    Ha egy házirendet egy csoportba központilag telepített házirendhez ad hozzá, akkor a csoport a munkaterhelésben közvetlenül hozzárendelt értékként jelenik meg, nem pedig a "házirend-készleten keresztül" hozzárendeléssel. Ennek eredményeképpen a MAM nem dolgozza fel a házirend-készletekből érkező csoport-hozzárendelési törléseket.

- A MAM nem támogatja az **összes felhasználó** és **minden eszköz** virtuális csoport üzembe helyezését bármely házirend-típus esetében.

## <a name="next-steps"></a>További lépések

- [Eszközök regisztrálása a Microsoft Intuneban](~/enrollment/index.yml).