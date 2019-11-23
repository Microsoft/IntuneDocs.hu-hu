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
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409696"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>A Mobile Threat Defense (MTD) eszközmegfelelőségi szabályzatának létrehozása az Intune-nal

Az Intune és az MTD együttes használata segíti a mobileszközökön megjelenő fenyegetések észlelését és a kockázat felmérését. Az Intune eszközmegfelelési szabályzaton belül létrehozhat egy szabályt, amely kockázatfelméréssel állapítja meg az eszköz megfelelőségét. You can then use a [Conditional Access policy](create-conditional-access-intune.md) to block access to services based on device compliance.

> [!NOTE]
> Ezek az információk minden Mobile Threat Defense-partnerre vonatkoznak.

## <a name="before-you-begin"></a>Előkészületek

Az MTD beállítása során az MTD-partnerkonzolon már létrehozott egy szabályzatot, amely a fenyegetéseket magas, közepes és alacsony szintű csoportba sorolja. Most be kell állítania a Mobile Threat Defense szintjét az Intune megfelelőségi szabályzatában.

Az MTD-eszközmegfelelési szabályzat előfeltételei:

- Az MTD és az Intune közötti integráció beállítása

## <a name="to-create-an-mtd-device-compliance-policy"></a>MTD-eszközmegfelelési szabályzat létrehozása

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Device** > **Compliance policies** > **Create policy**.

3. Specify a device compliance policy **Name**, **Description**, select the **Platform**, then select **Configure** under the **Settings** section.

4. A **Megfelelőségi szabályzat** panelen kattintson az **Eszközállapot** lehetőségre.

5. On the **Device Health** pane, choose the Mobile Threat Level from the drop-down list for **Require the device to be at or under the Device Threat Level**.

   - **Védett**: Ez a szint a legbiztonságosabb. Az eszköz csak akkor fér hozzá a céges erőforrásokhoz, ha semmilyen veszélyforrás nincs rajta. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül.

   - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű veszélyforrások állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.

   - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt veszélyforrások alacsony vagy közepes szintűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.

   - **Magas**: Ez a szint a legkevésbé biztonságos. Megadása esetén a rendszer semelyik fenyegetettségi szint mellett nem korlátozza az eszközt, a Mobile Threat Defense szolgáltatást csak jelentéskészítésre használja. Ennek a beállításnak a megadása esetén az eszközökön aktiválni kell az MTD alkalmazást.

6. Select **OK** twice, then select **Create** to create the policy.

> [!IMPORTANT]
> If you create Conditional Access policies for Office 365 or other services, the device compliance evaluation is assessed and noncompliant devices are blocked from accessing corporate resources until the threat is resolved in the device.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>MTD-eszközmegfelelési szabályzat hozzárendelése

To assign a device compliance policy to users:

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Device** > **Compliance policies**.

3. Select the policy you want to assign to users, and then select **Assignments**. Use the available options to *Include* and *Exclude* groups to receive this policy.  

4. Select Save to complete the assignment. When you save the assignment, the policy deploys to your selected users and their devices are evaluated for compliance.

## <a name="next-steps"></a>További lépések

[MTD engedélyezése az Intune-nal](mtd-connector-enable.md)
