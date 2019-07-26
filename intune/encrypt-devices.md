---
title: Eszközök titkosítása a Microsoft Intune a platformok által támogatott titkosítási módszerek használatával
titleSuffix: Microsoft Intune
description: Olyan beépített titkosítási módszerekkel titkosíthatja az eszközöket, mint például a BitLocker vagy a FileVault, és felügyelheti a titkosított eszközök helyreállítási kulcsait az Intune-portálon belül.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 3f37b9b0bc16572cc86cbf79be616c7f395aa784
ms.sourcegitcommit: 2bce5e43956b6a5244a518caa618f97f93b4f727
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68467473"
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

A FileVault konfigurálásához hozzon létre egy [eszköz konfigurációs profilt](device-profile-create.md) az Endpoint Protection számára a MacOS platformon. A FileVault beállításai a macOS Endpoint Protection számára elérhető beállítások kategóriák egyike.  

Miután létrehozott egy szabályzatot az eszközök FileVault való titkosításához, a szabályzatot két fázisban alkalmazza az eszközökre. Első lépésként az eszköz készen áll arra, hogy az Intune beolvassa és biztonsági másolatot készíteni a helyreállítási kulcsról. Ezt a letéti értéknek nevezzük. A kulcs letétbe helyezése után a lemez titkosítása is elindítható.

![FileVault-beállítások](./media/encrypt-devices/filevault-settings.png)

Az Intune-nal kezelhető FileVault-beállítás részleteiért lásd: [FileVault](endpoint-protection-macos.md#filevault) a MacOS Endpoint Protection-beállításokhoz tartozó Intune-cikkben.  

### <a name="how-to-configure-macos-filevault"></a>MacOS-FileVault konfigurálása 

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és lépjen az **eszköz konfigurációs** > **profilok** > **létrehozási profil létrehozása**pontra.  

2. Adja meg a következő beállításokat:  

   - Platform: macOS  
   - Profil típusa: Endpoint Protection  

3. Válassza a **Beállítások** > **FileVault**lehetőséget.  

4. A *FileVault*területen válassza az **Engedélyezés**lehetőséget.  

5. A *helyreállítási kulcs típusa*csak a **személyes kulcs** használata támogatott.  

   Vegye fontolóra egy üzenet hozzáadását, amely segítséget nyújt a végfelhasználók számára az eszköz helyreállítási kulcsának lekéréséhez. Ezek az információk hasznosak lehetnek a végfelhasználók számára, ha a személyes helyreállítási kulcs elforgatására vonatkozó beállítást használja, amely rendszeres időközönként automatikusan létrehoz egy új helyreállítási kulcsot az eszközhöz.  

   Példa: Elveszett vagy nemrég elforgatott helyreállítási kulcs lekéréséhez jelentkezzen be a Intune Céges portál webhelyére bármely eszközről. A portálon lépjen az *eszközök* elemre, és válassza ki azt az eszközt, amelyen engedélyezve van az FileVault, majd válassza a *helyreállítási kulcs*beolvasása elemet. Megjelenik az aktuális helyreállítási kulcs.  

6. Konfigurálja a fennmaradó [FileVault-beállításokat](endpoint-protection-macos.md#filevault) az üzleti igények kielégítéséhez, majd kattintson **az OK gombra**.  

7. Fejezze be a további beállítások konfigurációját, majd mentse a profilt.  

### <a name="manage-filevault"></a>FileVault kezelése  

Miután az Intune titkosít egy macOS-eszközt a FileVault-mel, megtekintheti és kezelheti a FileVault helyreállítási kulcsait, amikor megtekinti az Intune [titkosítási jelentését](encryption-monitor.md).  

## <a name="bitlocker-encryption-for-windows-10"></a>BitLocker-titkosítás a Windows 10 rendszerhez  

Az Intune-nal konfigurálhatja a Windows 10 rendszert futtató eszközökön BitLocker meghajtótitkosítás. Ezután az Intune titkosítási jelentés használatával tekintheti meg az eszközök titkosítási adatait. A BitLocker fontos információit az eszközökről is elérheti, ahogy azt a Azure Active Directory (Azure AD) is megtalálta.  

A BitLocker a **Windows 10 vagy újabb rendszert**futtató eszközökön érhető el.  

Konfigurálja a BitLockert, ha a Windows 10 vagy újabb rendszerű platformhoz hoz létre az Endpoint Protection [eszköz konfigurációs profilját](device-profile-create.md) . A BitLocker beállításai a Windows 10-es Endpoint Protection Windows titkosítási beállítások kategóriájában találhatók.    

![BitLocker-beállítások](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>A Windows 10 BitLocker konfigurálása  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és nyissa meg az eszköz konfigurációja > profilok > profil létrehozása lehetőséget.  

2. Adja meg a következő beállításokat:  
   - Platform Windows 10 és újabb  
   - Profil típusa: Endpoint Protection  

3. Válassza a **Beállítások** > **Windows-titkosítás**lehetőséget.

4. Konfigurálja a BitLocker beállításait az üzleti igények kielégítéséhez, majd kattintson **az OK gombra**.  

5. Fejezze be a további beállítások konfigurációját, majd mentse a profilt.  

### <a name="manage-bitlocker"></a>BitLocker kezelése  

Miután az Intune titkosít egy Windows 10-es eszközt a BitLocker használatával, megtekintheti és lekérheti a BitLocker helyreállítási kulcsait az Intune [titkosítási jelentés](encryption-monitor.md)megtekintésekor.  

## <a name="next-steps"></a>További lépések  

[Eszköz megfelelőségi](compliance-policy-create-windows.md) szabályzatának létrehozása  

A titkosítási jelentés használatával a következőket kezelheti:  
- [BitLocker helyreállítási kulcsok](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault helyreállítási kulcsok](encryption-monitor.md#filevault-recovery-keys)

Tekintse át az Intune-nal konfigurálható titkosítási beállításokat a következőhöz:  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
