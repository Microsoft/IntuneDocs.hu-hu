---
title: MTD-eszközmegfelelőségi szabályzat létrehozása a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Létrehozhat egy olyan Intune-beli eszközmegfelelőségi szabályzatot, amely az MTD-partner fenyegetettségi szintjeivel határozza meg, hogy egy mobileszköz hozzáférhet-e a céges erőforrásokhoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74409696"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>A Mobile Threat Defense (MTD) eszközmegfelelőségi szabályzatának létrehozása az Intune-nal

Az Intune és az MTD együttes használata segíti a mobileszközökön megjelenő fenyegetések észlelését és a kockázat felmérését. Az Intune eszközmegfelelési szabályzaton belül létrehozhat egy szabályt, amely kockázatfelméréssel állapítja meg az eszköz megfelelőségét. Ezután [feltételes hozzáférési szabályzattal](create-conditional-access-intune.md) blokkolhatja a szolgáltatásokhoz való hozzáférést az eszköz megfelelősége alapján.

> [!NOTE]
> Ezek az információk minden Mobile Threat Defense-partnerre vonatkoznak.

## <a name="before-you-begin"></a>Előkészületek

Az MTD beállítása során az MTD-partnerkonzolon már létrehozott egy szabályzatot, amely a fenyegetéseket magas, közepes és alacsony szintű csoportba sorolja. Most be kell állítania a Mobile Threat Defense szintjét az Intune megfelelőségi szabályzatában.

Az MTD-eszközmegfelelési szabályzat előfeltételei:

- Az MTD és az Intune közötti integráció beállítása

## <a name="to-create-an-mtd-device-compliance-policy"></a>MTD-eszközmegfelelési szabályzat létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszköz** > **megfelelőségi szabályzatok** > **házirend létrehozása**lehetőséget.

3. Adja meg az eszköz megfelelőségi szabályzatának **nevét**, **leírását**, válassza ki a **platformot**, majd válassza a **Konfigurálás** lehetőséget a **Beállítások** szakaszban.

4. A **Megfelelőségi szabályzat** panelen kattintson az **Eszközállapot** lehetőségre.

5. A **Eszközállapot** ablaktáblán válassza ki a Mobile Threat (mobil veszélyforrás) szintet a legördülő listából, hogy **az eszköz a veszélyforrások szintjén legyen**.

   - **Védett**: Ez a szint a legbiztonságosabb. Az eszköz csak akkor fér hozzá a céges erőforrásokhoz, ha semmilyen veszélyforrás nincs rajta. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül.

   - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű veszélyforrások állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.

   - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt veszélyforrások alacsony vagy közepes szintűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.

   - **Magas**: Ez a szint a legkevésbé biztonságos. Megadása esetén a rendszer semelyik fenyegetettségi szint mellett nem korlátozza az eszközt, a Mobile Threat Defense szolgáltatást csak jelentéskészítésre használja. Ennek a beállításnak a megadása esetén az eszközökön aktiválni kell az MTD alkalmazást.

6. Kattintson kétszer **az OK** , majd a **Létrehozás** elemre a szabályzat létrehozásához.

> [!IMPORTANT]
> Ha feltételes hozzáférési szabályzatokat hoz létre az Office 365-hez vagy más szolgáltatásokhoz, az eszköz megfelelőségének kiértékelését a rendszer kiértékeli, és a nem megfelelő eszközök nem férnek hozzá a vállalati erőforrásokhoz, amíg a fenyegetés fel nem oldódik az eszközön.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>MTD-eszközmegfelelési szabályzat hozzárendelése

Eszköz megfelelőségi szabályzatának kiosztása a felhasználók számára:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszköz** > **megfelelőségi szabályzatok**lehetőséget.

3. Válassza ki a felhasználókhoz hozzárendelni kívánt szabályzatot, majd válassza a **hozzárendelések**lehetőséget. Az elérhető beállításokkal csoportok *belefoglalásához* és *kizárásához* használhatja a szabályzatot.  

4. A hozzárendelés befejezéséhez válassza a mentés lehetőséget. A hozzárendelés mentésekor a szabályzatot a rendszer a kiválasztott felhasználókra telepíti, és az eszköz megfelelőségét kiértékeli.

## <a name="next-steps"></a>További lépések

[MTD engedélyezése az Intune-nal](mtd-connector-enable.md)
