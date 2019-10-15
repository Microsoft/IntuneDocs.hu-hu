---
title: Frissítés a Windows holografikus for Business rendszerre
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan melyekben a Windows holografikus rendszert futtató eszközöket az ablakos holografikus vállalatoknak
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d569d34da1568d0e412d689d98d4a22b00e6545
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314518"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Windows holografikus rendszert futtató eszközök frissítése a Windows holografikus for Business rendszerre

Microsoft Intune számos olyan beállítást tartalmaz, amelyek segítenek az eszközök kezelésében és védelmében. Ez a cikk felsorolja és ismerteti a Windows holografikus eszközök Windows holografikus for Business rendszerre való frissítésének beállításait. Ezek a beállítások az Intune-ban leküldve vagy az eszközökre telepített frissítési konfigurációs profilban jönnek létre.

A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja a Windows holografikus eszközök frissítéséhez. A Microsoft HoloLens vásárolhatja meg a kereskedelmi csomagot a frissítéshez szükséges licenc beszerzéséhez. További információ: [a Windows holografikus for Business funkcióinak feloldása](https://docs.microsoft.com/hololens/hololens1-upgrade-enterprise).

A szolgáltatással kapcsolatos további információkért lásd: a [Windows 10 kiadások frissítése vagy az S üzemmód engedélyezése](../edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Előzetes teendők

[Hozzon létre egy eszköz konfigurációs profilt](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Kiadás frissítése

- **Frissítés erre a kiadásra**: válassza **a Windows 10 holografikus for Business**lehetőséget.
- **Licencfájl**: tallózással keresse meg és válassza ki a kapott XML-licencfájl számára.

  ![Adja meg annak az XML-fájlnak a nevét, amely tartalmazza a holografikus vállalati licencelési információkat.](./media/holographic-upgrade/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>Következő lépések

A profil létrehozása megtörtént, de előfordulhat, hogy még nem csinál semmit. Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md), és [Figyelje annak állapotát](../device-profile-monitor.md).

A [Windows 10-es és újabb](edition-upgrade-windows-settings.md) rendszerű eszközökhöz is létrehozhat kiadás-frissítési profilokat.
