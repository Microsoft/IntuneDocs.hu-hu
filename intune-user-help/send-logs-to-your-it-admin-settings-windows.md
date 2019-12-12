---
title: Windows 10-eszközök naplóinak küldése a cég informatikai támogatási szolgálatának | Microsoft Docs
description: Windows 10 1511 rendszerű eszköz regisztrálása az Intune-ban
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e88fa55391ace4f8a86416412489ca055083503
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502051"
---
# <a name="send-logs-to-your-company-support-from-the-settings-app-for-windows-10"></a>Naplók küldése a cég informatikai támogatási szolgálatának a Windows 10 Gépház alkalmazásából

A Settings (beállítások) alkalmazással a Windows 10 Céges portál kapcsolatos hibák orvosolhatók. Ha az alkalmazás Windows 10-es eszközön való használata során probléma lép fel, akkor segítségért küldje el e-mailben a támogatási csapatot. A Céges portál alkalmazásban előforduló eseményeket és hibákat a rendszer a _diagnosztikai napló_nevű speciális dokumentumban menti az eszközön. További információkat is tartalmazhatnak a hibáról, és az exportáláskor hasznosak lehetnek a csapatok támogatásához.

1. A **Beállítások** alkalmazás megnyitásához nyissa meg a **Start** menü > **beállításait**. A keresési sávban is megkeresheti a *beállításokat* .
2. Lépjen a **Fiókok** > **Hozzáférés munkahelyi vagy iskolai rendszerhez** pontra.
3. Válassza **a felügyeleti naplófájlok exportálása**lehetőséget.

   ![A „Hozzáférés munkahelyi vagy iskolai rendszerhez” képernyő, amelyen elérhető az Exportálás a „Kapcsolódó beállítások” fejléc alatt.](./media/w10-export-logs.png)

4. A naplókat a rendszer a **C:\Users\Public\Public Documents\MDMDiagnostics** könyvtárba menti. Két fájl jön létre: az egyik maga a napló, a másik egy speciális dokumentum, amely lehetővé teszi a rendszergazda számára, hogy a naplót különféle programokban tekinthesse meg, például a Microsoft Excelben. Csatolja mindkét fájlt egy e-mailhez, és küldje el az e-mailt a rendszergazdának. Ha ezt többször is megteszi, egyszerűen válassza ki a naplófájlok létrehozási napját. 

Szükség lehet [naplók küldésére a céges portál alkalmazásból](send-logs-to-your-it-admin-cp-windows.md) is, amivel segítséget nyújthat a cég informatikai támogatási szolgálatának az esetleges problémák megoldásához. 

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
