---
title: Common Endpoint Protection-üzenetek a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg az Endpoint Protection és a Microsoft Defender Microsoft Intune-ben történő használatakor és hibaelhárításakor a gyakori üzeneteket és a lehetséges megoldást.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 819586a923f5c0f3a81a6d59c4a3895898182f6b
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059161"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Endpoint Protection-problémák és lehetséges megoldások a Microsoft Intune

Ez a cikk a hibák és figyelmeztetések lehetséges okait és megoldásait sorolja fel és ismerteti. Az Endpoint Protection használata során felmerülő problémák megoldása érdekében használja az információkat.

## <a name="microsoft-defender-error-codes"></a>Microsoft Defender-hibakódok

Tekintse át az eseménynaplókat és a hibakódokat a [Microsoft DEFENDER AV-vel kapcsolatos hibák elhárításához](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Gyakori Intune-hibák és lehetséges megoldások

### <a name="endpoint-protection-engine-unavailable"></a>Az Endpoint Protection-motor nem érhető el

**Lehetséges ok**: az Intune Endpoint Protection-motor sérült vagy törölték.

**Lehetséges megoldások**:

- Ha az Endpoint Protection sérült vagy nem frissül, akkor frissítse vagy telepítse újra a programot.
- Azonnali frissítés kényszerítése. Az Endpoint Protection-ügyfélprogramban (valószínűleg a tálcán) válassza a **frissítés**lehetőséget.
- A Vezérlőpulton > programok területen válassza az **Microsoft Intune Endpoint Protection ügynök**lehetőséget. Távolítsa el az alkalmazást.
- A következő frissítési szinkronizálás során a Microsoft Online Management frissítéskezelője észleli a hiányzó programot, és az ütemezés szerinti telepítési időpontban újratelepíti.

### <a name="features-are-disabled"></a>A funkciók le vannak tiltva

Előfordulhat, hogy bizonyos funkciók le vannak tiltva. Ezek az üzenetek akkor fordulnak elő, ha a rendszergazda letiltotta az Intune Endpoint Protection vagy a Microsoft Defender használatát egy konfigurációs profillal. Vagy a végfelhasználó letiltotta az eszközön. Lehetséges üzenetek:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Lehetséges megoldások**: engedélyezze ezeket a funkciókat. Útmutatásért lásd:

- [Endpoint Protection-beállítások hozzáadása](../protect/endpoint-protection-configure.md)
- [Microsoft Defender víruskereső](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [Végfelhasználók: a valós idejű védelem bekapcsolása a vállalati erőforrások eléréséhez](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>A kártevő-definíciók elavultak

Ez az állapot akkor jelenik meg, ha az eszközön a kártevő-definíciók elavultak (14 nap). Előfordulhat például, hogy az üzenet megmutathatja, hogy az eszköz le van választva az internetről, vagy elavultak a kártevő-definíciók.

**Lehetséges megoldások**: Ha a kártevő-definíciók elavultak, frissítse a definíciókat a [Microsoft Defender Antivirus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)használatával.

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>A teljes ellenőrzés elmaradt, vagy a gyors ellenőrzés késésben

A teljes vizsgálat vagy a gyors vizsgálat 14 napig nem fejeződött be. Ez a forgatókönyv akkor fordulhat elő, ha az eszköz egy teljes vizsgálat során újraindul.

**Lehetséges megoldások**: Ha egy vizsgálat késésben van, futtathat egy egyszeri vizsgálatot, vagy ismétlődő vizsgálatokat is ütemezhet. Lásd: [Microsoft Defender Antivirus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="another-endpoint-protection-application-running"></a>Egy másik végpontvédelmi alkalmazás fut

Egy másik Endpoint Protection-alkalmazás fut, és az eszköz kifogástalan állapotú.

**Lehetséges megoldások**: Ha egy másik Endpoint Protection-alkalmazás telepítve van, és az Intune észleli ezt az alkalmazást, akkor az eszköz instabillá válhat.

## <a name="next-steps"></a>További lépések

Kérjen [támogatási segítséget a Microsofttól](get-support.md), vagy használja a [közösségi fórumokat](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
