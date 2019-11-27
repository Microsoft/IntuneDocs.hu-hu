---
title: Eszközök titkosítása támogatott titkosítási módszerrel
titleSuffix: Microsoft Intune
description: Olyan beépített titkosítási módszerekkel titkosíthatja az eszközöket, mint például a BitLocker vagy a FileVault, és felügyelheti a titkosított eszközök helyreállítási kulcsait az Intune-portálon belül.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 13d6a2b9cdc8596c7f5cf81218377754e9412be1
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390346"
---
# <a name="use-device-encryption-with-intune"></a>Az eszközök titkosításának használata az Intune-nal

Az Intune használatával az eszközökön tárolt eszközök védelme érdekében beépített lemezeket vagy meghajtó-titkosítást kezelhet.

Konfigurálja a lemez titkosítását az Endpoint Protection eszköz konfigurációs profiljának részeként. Az Intune az alábbi platformokat és titkosítási technológiákat támogatja:

- macOS: FileVault
- Windows 10 és újabb verziók: BitLocker

Az Intune egy beépített [titkosítási jelentést](encryption-monitor.md) is biztosít, amely az eszközök titkosítási állapotának részletes adatait jeleníti meg az összes felügyelt eszközön.

## <a name="filevault-encryption-for-macos"></a>FileVault-titkosítás macOS rendszerhez

Az Intune-nal konfigurálhatja a FileVault a macOS-t futtató eszközökön. Ezután az Intune titkosítási jelentésével megtekintheti az eszközök titkosítási adatait, valamint felügyelheti a FileVault titkosított eszközök helyreállítási kulcsait.

A FileVault egy teljes lemezes titkosítási program, amely a macOS rendszer részét képezi. Az Intune-nal a **macOS 10,13-es vagy újabb verzióját**futtató eszközökön is konfigurálhatja a FileVault.

A FileVault konfigurálásához hozzon létre egy [eszköz konfigurációs profilt](../configuration/device-profile-create.md) az Endpoint Protection számára a MacOS platformon. A FileVault beállításai a macOS Endpoint Protection számára elérhető beállítások kategóriák egyike.

Miután létrehozott egy szabályzatot az eszközök FileVault való titkosításához, a szabályzatot két fázisban alkalmazza az eszközökre. Első lépésként az eszköz készen áll arra, hogy az Intune beolvassa és biztonsági másolatot készíteni a helyreállítási kulcsról. Ezt a letéti értéknek nevezzük. A kulcs letétbe helyezése után a lemez titkosítása is elindítható.

![FileVault-beállítások](./media/encrypt-devices/filevault-settings.png)

Az Intune-nal kezelhető FileVault-beállítás részleteiért lásd: [FileVault](endpoint-protection-macos.md#filevault) a MacOS Endpoint Protection-beállításokhoz tartozó Intune-cikkben.

### <a name="how-to-configure-macos-filevault"></a>MacOS-FileVault konfigurálása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

3. Adja meg a következő beállításokat:

   - Platform: macOS
   - Profil típusa: Endpoint Protection

4. Válassza a **beállítások** > **FileVault**lehetőséget.

5. A *FileVault*területen válassza az **Engedélyezés**lehetőséget.

6. A *helyreállítási kulcs típusa*csak a **személyes kulcs** használata támogatott.

   Vegye fontolóra egy üzenet hozzáadását, amely segítséget nyújt a végfelhasználók számára az eszköz helyreállítási kulcsának lekéréséhez. Ezek az információk hasznosak lehetnek a végfelhasználók számára, ha a személyes helyreállítási kulcs elforgatására vonatkozó beállítást használja, amely rendszeres időközönként automatikusan létrehoz egy új helyreállítási kulcsot az eszközhöz.

   Például: egy elveszett vagy nemrég elforgatott helyreállítási kulcs lekéréséhez jelentkezzen be a Intune Céges portál webhelyre bármilyen eszközről. A portálon lépjen az *eszközök* elemre, és válassza ki azt az eszközt, amelyen engedélyezve van az FileVault, majd válassza a *helyreállítási kulcs beolvasása*elemet. Megjelenik az aktuális helyreállítási kulcs.

7. Konfigurálja a fennmaradó [FileVault-beállításokat](endpoint-protection-macos.md#filevault) az üzleti igények kielégítéséhez, majd kattintson **az OK gombra**.

   > [!IMPORTANT]
   > Ismert hiba történt, ha a Letiltás beállítás a **kijelentkezéskor** beállítás *engedélyezve*értékre van állítva. Ha az *Engedélyezés*beállítást adja meg, a **megkerülő időpontok számának** meg kell adni egy értéket, és nem állítható be *nem konfiguráltként*. Ha a *nincs konfigurálva*értékre van állítva, a profil meghiúsul az eszközön. Ebben az esetben az eszköz a **profil állapotának összegzése** **hibát** jelez, további részletek nélkül.
   >
   > Ha a **kijelentkezéskor a Letiltás** beállítás nincs *konfigurálva*értékre van állítva, a **megkerülő időpontok száma** *nem konfigurálható* , és nem rendelkezhet értékkel.
   >
   > Ezt a problémát egy jövőbeli frissítés fogja megoldani.

8. Fejezze be a további beállítások konfigurációját, majd mentse a profilt.  

### <a name="manage-filevault"></a>FileVault kezelése

Miután az Intune titkosít egy macOS-eszközt a FileVault-mel, megtekintheti és kezelheti a FileVault helyreállítási kulcsait, amikor megtekinti az Intune [titkosítási jelentését](encryption-monitor.md).

Miután az Intune titkosít egy macOS-eszközt a FileVault-mel, megtekintheti az eszköz személyes helyreállítási kulcsát a webes Céges portál bármely eszközön. Egyszer a webes Céges portál válassza ki a titkosított macOS-eszközt, majd válassza a "helyreállítási kulcs beolvasása" lehetőséget távoli eszköz műveletként.

## <a name="bitlocker-encryption-for-windows-10"></a>BitLocker-titkosítás a Windows 10 rendszerhez

Az Intune-nal konfigurálhatja a Windows 10 rendszert futtató eszközökön BitLocker meghajtótitkosítás. Ezután az Intune titkosítási jelentés használatával tekintheti meg az eszközök titkosítási adatait. A BitLocker fontos információit az eszközökről is elérheti, ahogy azt a Azure Active Directory (Azure AD) is megtalálta.

A BitLocker a **Windows 10 vagy újabb rendszert**futtató eszközökön érhető el.

Konfigurálja a BitLockert, ha a Windows 10 vagy újabb rendszerű platformhoz hoz létre az Endpoint Protection [eszköz konfigurációs profilját](../configuration/device-profile-create.md) . A BitLocker beállításai a Windows 10-es Endpoint Protection Windows titkosítási beállítások kategóriájában találhatók.

![BitLocker-beállítások](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>A Windows 10 BitLocker konfigurálása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

3. Adja meg a következő beállításokat:

   - Platform: Windows 10 és újabb verziók
   - Profil típusa: Endpoint Protection

4. Válassza a **beállítások** > **Windows-titkosítás**lehetőséget.

5. Konfigurálja a BitLocker beállításait az üzleti igények kielégítéséhez, majd kattintson **az OK gombra**.

6. Fejezze be a további beállítások konfigurációját, majd mentse a profilt.

### <a name="manage-bitlocker"></a>BitLocker kezelése

Miután az Intune titkosít egy Windows 10-es eszközt a BitLocker használatával, megtekintheti és lekérheti a BitLocker helyreállítási kulcsait az Intune [titkosítási jelentés](encryption-monitor.md)megtekintésekor.

### <a name="rotate-bitlocker-recovery-keys"></a>BitLocker helyreállítási kulcsok elforgatása

Az Intune-eszköz művelettel távolról elforgathatja a Windows 10 1909-es vagy újabb verzióját futtató eszközök BitLocker helyreállítási kulcsát.

#### <a name="prerequisites"></a>Előfeltételek

Az eszközöknek meg kell felelniük a következő előfeltételeknek a BitLocker helyreállítási kulcs rotációjának támogatásához:

- Az eszközöknek a Windows 10 1909-es vagy újabb verzióját kell futtatniuk

- Az Azure AD-hez csatlakoztatott és a hibrid csatlakozású eszközöknek támogatnia kell a kulcs-rotációs szolgáltatást:

  - **Ügyfél által vezérelt helyreállítási jelszó elforgatása**

  Ez a beállítás a Windows 10 Endpoint Protection eszköz-konfigurációs szabályzatának részeként a *Windows-titkosítás* területen található.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>A BitLocker helyreállítási kulcsának elforgatása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **Eszközök** > **Minden eszköz** lehetőséget.

3. A felügyelt eszközök listájában válasszon ki egy eszközt, válassza a **továbbiak**lehetőséget, majd válassza ki a **BitLocker Key rotációs** eszköz távoli műveletét.

## <a name="next-steps"></a>További lépések

Hozzon létre [egy eszköz megfelelőségi](compliance-policy-create-windows.md) szabályzatát.

A titkosítási jelentés használatával a következőket kezelheti:

- [BitLocker helyreállítási kulcsok](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault helyreállítási kulcsok](encryption-monitor.md#filevault-recovery-keys)

Tekintse át az Intune-nal konfigurálható titkosítási beállításokat a következőhöz:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
