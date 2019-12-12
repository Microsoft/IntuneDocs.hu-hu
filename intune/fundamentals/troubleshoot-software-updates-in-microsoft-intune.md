---
title: Szoftverfrissítések Microsoft Intune-Azure-beli frissítéseinek hibáinak megoldása | Microsoft Docs
description: A Microsoft Intune szoftverfrissítéseivel kapcsolatban felmerülő problémák megoldása.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7da927754971fb66a5d8442d0cdf18e0ebfbcd4a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059080"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>A Microsoft Intune szoftverfrissítéseinek hibaelhárítása

Segítsen a Microsoft Intune a szoftverfrissítési problémák megoldásában. A hibakódok és leírások listájának megtekintéséhez keresse fel a [szoftverfrissítési ügynök hibakódait Microsoft Intune](../protect/software-update-agent-error-codes.md).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>A sok felváltott frissítéssel rendelkező Windows 7 rendszerű eszközök leállítja az Intune-nak való jelentéskészítést

Microsoft Intune ügyfelek a következő tünetek közül egyet vagy többet tapasztalhatnak:

- Az eszközök hirtelen leállítják az Intune-ban való jelentéskészítést  
- Az eszközök magas CPU-kihasználtságot tapasztalnak.
- Az alkalmazások lassan települnek az Intune-on keresztül.
- A Microsoft Intune Center a következő hibaüzenetet jeleníti meg: `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- Az Intune felügyeleti konzolján > csoportok > minden eszköz > állapota a következőket mutatja: `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Ez a probléma akkor fordulhat elő, ha a felülírt frissítéseket (a frissítéseket egy másik frissítés váltja fel) nem utasította el egy hosszabb ideig. Bizonyos folyamatok, például az alkalmazások telepítése során a Windows az összes felülírt frissítést a sorban ellenőrzi, hogy a frissítések és azok utódai megfelelően legyenek leképezve. Ha a felülírt frissítések listája túl nagyra vált, az ellenőrzési feladat magas CPU-kihasználtságot okozhat a feldolgozási terhelés és a szükséges idő miatt. Ez a probléma elsősorban a Windows 7 rendszerű eszközöket érinti, mivel a Windows 7 rendszerhez elérhető nagy mennyiségű felülírt frissítés van. Előfordulhat, hogy az újabb operációs rendszerek nem rendelkeznek annyi rendelkezésre álló felváltott frissítéssel, és nem hajlamosak erre a hibára.

**Felbontás**

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **szoftverfrissítések**lehetőséget.
3. Az érintett ügyfelekre telepített összes felülírt frissítés elutasítása a Windows 7 vagy alkalmazásokra, például a Microsoft Officeekre.
4. Indítsa újra az érintett ügyfeleket.

Ha Windows 7 rendszert használ, győződjön meg arról, hogy a következő frissítés telepítve van:[3050265 Windows Update ügyfél Windows 7 rendszerhez: június 2015](https://support.microsoft.com/kb/3050265).

## <a name="next-steps"></a>További lépések

Kérjen [támogatási segítséget a Microsofttól](get-support.md), vagy használja a [közösségi fórumokat](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).