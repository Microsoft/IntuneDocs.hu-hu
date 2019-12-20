---
title: macOS kernel-bővítmény beállításai a Microsoft Intune-Azure-ban | Microsoft Docs
titleSuffix: ''
description: A macOS-eszközökhöz hozzáadhat, konfigurálhat vagy hozhat létre beállításokat a kernel-bővítmények használatához. Azt is lehetővé teszi, hogy a felhasználók felülbírálják a jóváhagyott bővítményeket, engedélyezik az összes bővítményt a csoport azonosítójában, vagy engedélyezik az egyes bővítményeket vagy alkalmazásokat a Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 89f54111258b5e628d9f83c381fde146bf996216
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206329"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>macOS-eszközbeállítások a kernel-bővítmények konfigurálásához és használatához az Intune-ban



Ez a cikk a macOS-eszközökön vezérelhető különböző kernel-bővítményi beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja kernel-bővítmények hozzáadásához és kezeléséhez az eszközökön.

További információ az Intune-beli kernel-bővítményekről és az előfeltételekről: [MacOS kernel-bővítmények hozzáadása](../kernel-extensions-overview-macos.md).

Ezek a beállítások hozzáadódnak az Intune-ban lévő eszköz konfigurációs profiljához, majd a macOS-eszközökhöz vannak rendelve vagy telepítve.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz kernel-bővítmények konfigurációs profilt](../kernel-extensions-overview-macos.md).

> [!NOTE]
> Ezek a beállítások a különböző regisztrációs típusokra vonatkoznak. A különböző regisztrációs típusokkal kapcsolatos további információkért lásd: [MacOS-regisztráció](../macos-enroll.md).

## <a name="kernel-extensions"></a>Kernel-bővítmények

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>A beállítások a következőkre vonatkoznak: felhasználó által jóváhagyott, automatikus eszköz beléptetése

- **Felhasználói felülbírálások engedélyezése**: lehetővé teszi, **hogy** a felhasználók jóváhagyják a konfigurációs profilban nem szereplő kernel-bővítményeket. **Nincs konfigurálva** (alapértelmezett) megakadályozza, hogy a felhasználók a konfigurációs profilban nem szereplő bővítményeket engedélyezzenek. Ez azt jelenti, hogy csak a konfigurációs profilban szereplő bővítmények engedélyezettek.

  A szolgáltatással kapcsolatos további információkért tekintse meg a [felhasználó által jóváhagyott kernel-bővítmény betöltését](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) (az Apple webhelyének megnyitása).

- **Engedélyezett csoport azonosítói**: ezzel a beállítással engedélyezheti egy vagy több csoport azonosítójának használatát. Az Ön által megadott csoport-azonosítókkal aláírt kernel-bővítmények engedélyezettek és megbízhatók. Más szóval, ezzel a beállítással engedélyezheti az összes kernel-bővítményt ugyanazon a csapat-AZONOSÍTÓn belül, amely lehet egy adott fejlesztő vagy partner.

  **Adja** meg a betölteni kívánt érvényes és aláírt kernel-bővítmények csoportjának azonosítóját. Több csoport azonosítóját is hozzáadhatja. A csoport azonosítójának alfanumerikusnak (betűket és számokat) kell tartalmaznia, és 10 karakterből kell állnia. Például írja be a következőt: `ABCDE12345`.

  A csoport azonosítójának hozzáadása után az is törölhető.

  [Keresse meg a csoport azonosítóját (az](https://help.apple.com/developer-account/#/dev55c3c710c) Apple webhelyének megnyitása) további információkat.

- **Engedélyezett kernel-bővítmények**: ezzel a beállítással engedélyezheti a megadott kernel-bővítményeket. Csak a megadott kernel-bővítmények engedélyezettek vagy megbízhatók. 

  **Adja hozzá** a betölteni kívánt kernel-bővítmény köteg-azonosítóját és csoportjának azonosítóját. Aláíratlan örökölt kernel-bővítmények esetén használjon üres csapat-azonosítót. Több kernel-bővítményt is hozzáadhat. A csoport azonosítójának alfanumerikusnak (betűket és számokat) kell tartalmaznia, és 10 karakterből kell állnia. Adja meg például a **csomag azonosítójának**`com.contoso.appname.macos`ét, és `ABCDE12345` a **csoport azonosítóját**.

  > [!TIP]
  > Ha egy macOS-eszközön szeretné lekérni a kernel-bővítmény (kext) köteg-AZONOSÍTÓját, a következőket teheti:
  >
  > 1. A terminálon futtassa `kextstat | grep -v com.apple`parancsot, és jegyezze fel a kimenetet. Telepítse a kívánt szoftvert vagy kext. Futtassa újra `kextstat | grep -v com.apple`, és keresse meg a módosításokat.
  >
  >    A terminálban `kextstat` az operációs rendszer összes kernel-bővítményét listázza. 
  >
  > 2. Az eszközön nyissa meg a kext információs tulajdonságának listáját (info. plist). Megjelenik a köteg azonosítója. Minden kext tartalmaz egy info. plist fájlt, amely belül tárolva van. 

> [!NOTE]
> Nem kell felvennie a csoport azonosítóit és a kernel-bővítményeket. Az egyiket vagy a másikat is konfigurálhatja.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](../device-profile-monitor.md).
