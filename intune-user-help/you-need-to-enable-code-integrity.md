---
title: Engedélyeznie kell a Kódintegritást | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 84892bbc-f888-417b-bbeb-978cc7e10028
searchScope:
- User help
ROBOTS: ''
ms.reviewer: scottduf
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: c518e0eeb18f51fa17d15a72735e319aef1d647d
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167478"
---
# <a name="enable-code-integrity"></a>Kód integritásának engedélyezése

A szervezetnek szüksége lehet arra, hogy a SZÁMÍTÓGÉPe engedélyezve legyen a *kód integritása*nevű veszélyforrások elleni védelmi szolgáltatással. A kód integritása ellenőrzi az eszközön lévő illesztőprogramokat és rendszerfájlokat a sérülés vagy a kártevő szoftverek jeleinek ellenőrzéséhez. Ahhoz, hogy a kód integritása működjön az eszközön, a [*biztonságos rendszerindítás*](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process#secure-boot) nevű másik biztonsági funkciót is engedélyezni kell.

Ha a számítógép nem megfelelő, mert a kód integritása le van tiltva, lépjen kapcsolatba a szervezet informatikai támogatási csapatával. Segítenek a biztonságos rendszerindítás engedélyezésében, amely a kód integritását aktiválja az eszköz következő indításakor.

Ha speciális eszköz felhasználóként azonosítja magát, és saját maga szeretné kipróbálni a lépéseket, tekintse meg a [biztonságos rendszerindítás ismételt engedélyezése](https://docs.microsoft.com/windows-hardware/manufacture/desktop/disabling-secure-boot#re-enable-secure-boot)című témakört.

## <a name="additional-resources-for-it-administrators"></a>További erőforrások a rendszergazdák számára

Ha Ön Intune-rendszergazda, és szeretne többet megtudni az Intune Eszközállapot-megfelelőségi beállításairól, tekintse meg az [eszköz megfelelőségi szabályzatának hozzáadása Windows 10-es eszközökhöz az Intune-ban](https://docs.microsoft.com/intune/compliance-policy-create-windows.md)című témakört. Az Intune-ban elvégezhető megfelelőségi műveletek részletes ismertetését az [HEALTHATTESTATION CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp#step-8-take-appropriate-policy-action-based-on-evaluation-results)-vel foglalkozó témakörben tekintheti meg.  

## <a name="next-steps"></a>További lépések

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
