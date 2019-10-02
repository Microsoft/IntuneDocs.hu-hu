---
title: Windows 10 frissítési és S módú beállítások a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg az összes beállítás listáját, valamint azt, hogy mit csinálnak egy eszközön futó Windows 10-es kiadás frissítésekor, vagy engedélyezze az S üzemmódot az eszközön a Microsoft Intune eszköz konfigurációs profiljának használatával.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c34f683bfd16362dfb9af9a69c6f7d9b04860c7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730715"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Windows 10 (és újabb) eszközbeállítások a kiadások frissítéséhez vagy az S üzemmód engedélyezéséhez az Intune-ban

Microsoft Intune számos olyan beállítást tartalmaz, amelyek segítenek az eszközök kezelésében és védelmében. Ez a cikk felsorolja és ismerteti a Windows 10-es eszközökön a kiadások frissítésének és engedélyezésének beállításait. Ezek a beállítások az Intune-ban leküldve vagy az eszközökre telepített frissítési konfigurációs profilban jönnek létre.

A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja a Windows 10-es eszközök kiadási és S módú beállításainak vezérléséhez.

A szolgáltatással kapcsolatos további információkért lásd: a [Windows 10 kiadások frissítése vagy az S üzemmód engedélyezése](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Előkészületek

[Hozza létre a profilt](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Kiadásfrissítés

- **Frissítés erre a kiadásra**: Válassza ki azt a Windows 10-es verziót, amelyre frissíteni szeretne. A szabályzat hatókörébe tartozó eszközök ekkor frissülnek a választott kiadásra.
- **Termékkulcs**: Adja meg a Microsofttól kapott termékkulcsot. Miután létrehozta a termékkulcsot tartalmazó szabályzatot, a termékkulcsot nem lehet többé frissíteni, és biztonsági okokból rejtve marad. A termékkulcs módosításához a teljes kulcsot újra meg kell adnia.
- **Licencfájl**: **Windows 10 holografikus for Business** vagy **Windows 10 Mobile kiadás**esetén válassza a **Tallózás** lehetőséget a Microsofttól kapott licencfájl kiválasztásához. Ez a licencfájl tartalmazza azokat a kiadási adatokat, amelyekre az eszközöket frissíti.

## <a name="mode-switch"></a>Üzemmód kapcsoló

- **Nincs konfiguráció**: Az S üzemmódú eszközök az S üzemmódban maradnak. A végfelhasználók válthatnak S módból.
- **Tartsa az S módban**: Letiltja a végfelhasználók számára az eszköz kikapcsolását az S módból.
- **Kapcsoló**: Kikapcsolja az eszközt az S módból.

## <a name="next-steps"></a>További lépések

A profil létrehozása megtörtént, de előfordulhat, hogy még nem csinál semmit. Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md), és [Figyelje annak állapotát](device-profile-monitor.md).

Kiadási frissítési profilokat is létrehozhat a [Windows holografikus for Business](holographic-upgrade.md) -eszközökhöz.
