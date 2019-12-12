---
title: Frissítés a Windows holografikus for Business rendszerre
titleSuffix: Microsoft Intune
description: Tudja meg, hogyan frissítheti a Windows Holographic operációs rendszert futtató eszközöket a Windows Holographic for Business verzióra
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6342ed23f67c37c2f5084e58594294d826a28e40
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506719"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>A Windows Holographic operációs rendszert futtató eszközök frissítése a Windows Holographic for Business verzióra

Microsoft Intune számos olyan beállítást tartalmaz, amelyek segítenek az eszközök kezelésében és védelmében. Ez a cikk felsorolja és ismerteti a Windows holografikus eszközök Windows holografikus for Business rendszerre való frissítésének beállításait. Ezek a beállítások az Intune-ban leküldve vagy az eszközökre telepített frissítési konfigurációs profilban jönnek létre.

A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja a Windows holografikus eszközök frissítéséhez. A Microsoft HoloLens vásárolhatja meg a kereskedelmi csomagot a frissítéshez szükséges licenc beszerzéséhez. További információkért lásd: [Unlock Windows Holographic for Business features](https://docs.microsoft.com/hololens/hololens1-upgrade-enterprise) (A Windows Holographic for Business új funkcióinak elérése).

A szolgáltatással kapcsolatos további információkért lásd: a [Windows 10 kiadások frissítése vagy az S üzemmód engedélyezése](../edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Kiadásfrissítés

- **Frissítés erre a kiadásra**: válassza **a Windows 10 holografikus for Business**lehetőséget.
- **Licencfájl**: tallózással keresse meg és válassza ki a kapott XML-licencfájl számára.

  ![Adja meg annak az XML-fájlnak a nevét, amely tartalmazza a holografikus vállalati licencelési információkat.](./media/holographic-upgrade/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>További lépések

A profil létrehozása megtörtént, de előfordulhat, hogy még nem csinál semmit. Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md), és [Figyelje annak állapotát](../device-profile-monitor.md).

A [Windows 10-es és újabb](edition-upgrade-windows-settings.md) rendszerű eszközökhöz is létrehozhat kiadás-frissítési profilokat.
