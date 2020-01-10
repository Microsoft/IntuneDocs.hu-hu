---
title: A Windows Defender bekapcsolása | Microsoft Docs
description: Útmutató a Windows Defender a vállalati erőforrásokhoz való hozzáférés érdekében történő bekapcsolásához.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 63d5ebc00182c8edaea6956612ecd047a1778dec
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859032"
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>A Windows Defender bekapcsolása a vállalati erőforrásokhoz való hozzáférés érdekében

A munkahely vagy az iskola biztosítani szeretné, hogy az erőforrásaihoz hozzáférő eszközök biztonságosak legyenek. A [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx), a Windows beépített kártevő szoftverek elleni védelme többféleképpen is használható.

Előfordulhat, hogy a Windows Defender néhány beállítását meg kell változtatnia az esetleges hozzáférési problémák megoldásához. Lehetséges, hogy a lépések végrehajtásához több helyet is meg kell nyitnia a számítógépen.

## <a name="turn-on-windows-defender"></a>A Windows Defender bekapcsolása

1. A **Start** menüben nyissa meg a **Vezérlőpultot**.
2. Válassza a **Felügyeleti eszközök** > **Csoportházirend szerkesztése** lehetőséget. Ezzel megnyitja a **Helyicsoportházirend-szerkesztőt** egy új ablakban.
3. Válassza a **Számítógép konfigurációja** > **Felügyeleti sablonok** > **Windows-összetevők** > **Windows Defender víruskereső** lehetőséget. **A Windows Defender víruskereső kikapcsolása** beállítás a többi beállítás mappái alatt található. 
4. Nyissa meg **A Windows Defender víruskereső kikapcsolása** elemet, és győződjön meg róla, hogy az a **Letiltva** vagy a **Nincs konfigurálva** értékre van beállítva.

## <a name="turn-on-real-time-protection"></a>Valós idejű védelem bekapcsolása

Győződjön meg arról, hogy a valós idejű védelem be van kapcsolva. Ehhez nyissa meg a **Start** menüt, és keressen rá a **Windows Defender biztonsági központ** kifejezésre. Válassza a **Vírusok és veszélyforrások elleni védelem beállításai** lehetőséget, és győződjön meg róla, hogy a **Valós idejű védelem** és a **Felhőalapú védelem** is **Be** van kapcsolva. Ha ezek a lehetőségek nem jelennek meg, akkor a következő lépésekkel engedélyezheti őket:

1. A **Start** menüben nyissa meg a **Vezérlőpultot**.
2. Válassza a **Felügyeleti eszközök** > **Csoportházirend szerkesztése** lehetőséget. Ezzel megnyitja a **Helyicsoportházirend-szerkesztőt** egy új ablakban.
3. Kattintson a **Számítógép konfigurációja** > **Felügyeleti sablonok** > **Windows-összetevők** > **Windows Defender biztonsági központ** > **Vírusok és veszélyforrások elleni védelem** pontra.
4. Nyissa meg a **Vírusok és veszélyforrások elleni védelem terület** beállítást, és állítsa **Letiltva** értékre.

## <a name="update-your-antivirus-definitions"></a>Víruskeresési definíciók frissítése

Győződjön meg arról, hogy a víruskeresési definíciók naprakészek. Ehhez nyissa meg a **Start** menüt, és keressen rá a **Windows Defender biztonsági központ** kifejezésre. A **Védelmi frissítések** és a **Frissítések keresése** lehetőséggel ellenőrizze, hogy az eszköze naprakész védelemmel rendelkezik-e vírusok ellen. Ha ez a lehetőség nem jelenik meg, akkor kövesse a [Valós idejű védelem bekapcsolása](turn-on-defender-windows.md#turn-on-real-time-protection) című szakaszban szereplő lépéseket.

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
