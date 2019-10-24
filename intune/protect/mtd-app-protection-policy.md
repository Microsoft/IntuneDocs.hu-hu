---
title: Mobile Threat Defense (MTD) alkalmazás-védelmi szabályzat létrehozása az Intune-nal
titleSuffix: Microsoft Intune
description: Hozzon létre egy Mobile Threat Defense-(MTD-) alkalmazás-védelmi szabályzatot Microsoft Intuneokkal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72795310"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Mobile Threat Defense-alkalmazás védelmi szabályzatának létrehozása az Intune-nal

> [!NOTE] 
> Ez a cikk az alkalmazás-védelmi házirendeket támogató összes Mobile Threat Defense-(MTD-) partnerre vonatkozik: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

Az Intune és az MTD együttes használata segíti a mobileszközökön megjelenő fenyegetések észlelését és a kockázat felmérését. Létrehozhat egy Intune app Protection-szabályzatot, amely felméri a kockázatot annak megállapítására, hogy az eszköz hozzáférhet-e a vállalati adatszolgáltatáshoz. 

## <a name="before-you-begin"></a>Előkészületek

Az MTD beállítása során az MTD-partnerkonzolon már létrehozott egy szabályzatot, amely a fenyegetéseket magas, közepes és alacsony szintű csoportba sorolja. Most be kell állítania a Mobile Threat Defense szintjét az Intune app Protection-szabályzatban.

Az alkalmazás-védelmi szabályzat MTD való használatának előfeltételei:

- MTD-integráció beállítása az Intune-nal. Ezen integráció nélkül a MTD-alkalmazás védelmi szabályzata nem lesz hatással.

## <a name="to-create-an-mtd-app-protection-policy"></a>MTD-szabályzat létrehozása

1. Az [Azure Portalon](https://portal.azure.com/) jelentkezzen be az Intune-os hitelesítő adataival.

2. Az **Azure-irányítópulton** válassza a bal oldali menü **Minden szolgáltatás** pontját, majd írja be a szűrő szövegmezőbe az **Intune** nevet.

3. Ha az **Intune** elemre kattint, megnyílik az **Intune irányítópultja**.

4. Az **Intune irányítópultján**válassza az **ügyfélalkalmazások**lehetőséget, majd a **kezelés** szakaszban válassza az **alkalmazás-védelmi házirendek** elemet.

5. Válassza a **házirend létrehozása**lehetőséget, adja meg a **nevet**, a **leírást**, majd válassza ki a **platformot**. 

6. A **feltételes indítás** ablaktáblán, az **eszköz feltételei** táblázatban válassza ki a Mobile Threat (mobil veszélyforrás) szintet a **maximálisan engedélyezett veszélyforrások szintjének**legördülő listából.

    a.  **Védett**: Ez a szint a legbiztonságosabb. Az eszköz csak akkor fér hozzá a céges erőforrásokhoz, ha semmilyen veszélyforrás nincs rajta. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül.

    b.  **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű veszélyforrások állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.

    c.  **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt veszélyforrások alacsony vagy közepes szintűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.

    d.  **Magas**: Ez a szint a legkevésbé biztonságos. Megadása esetén a rendszer semelyik fenyegetettségi szint mellett nem korlátozza az eszközt, a Mobile Threat Defense szolgáltatást csak jelentéskészítésre használja. Ennek a beállításnak a megadása esetén az eszközökön aktiválni kell az MTD alkalmazást.

7. Kattintson kétszer a **Mentés** gombra, majd válassza a **Létrehozás**lehetőséget.

## <a name="to-assign-an-mtd-app-protection-policy"></a>MTD-szabályzatok kiosztása

Ha a felhasználókhoz eszközmegfelelőségi szabályzatot kíván rendelni, olyan szabályzatot válasszon, amelyet előzőleg már konfigurált. A meglévő szabályzatokat az **Eszközmegfelelőségi szabályzatok** panelen tekintheti meg.

1. Válassza ki a felhasználókhoz hozzárendelni kívánt szabályzatot, és válassza a **Hozzárendelések** lehetőséget. Ez a művelet megnyitja a panelt, amelyen kiválaszthatja **Azure Active Directory biztonsági csoportokat** , és hozzárendelheti azokat a szabályzathoz.

2. Válassza ki azokat a **csoportokat** , amelyeket fel szeretne venni az Azure ad biztonsági csoportjait megjelenítő ablaktábla megnyitásához. A **Select** (kiválasztás) gombra kattintva telepítheti a szabályzatot a felhasználók számára.

> [!NOTE] 
> Ezzel érvénybe léptette a szabályzatot a felhasználók számára. A szabályzat által megcélozott felhasználók által használt eszközök az Intune app Protection használatával kiértékelésre kerülnek a vállalati adathozzáféréshez a megcélozott alkalmazásokban.

## <a name="next-steps"></a>További lépések  

- További tudnivalók a [Mobile Threat Defense](~/protect/mobile-threat-defense.md) szolgáltatásról Microsoft Intune.
