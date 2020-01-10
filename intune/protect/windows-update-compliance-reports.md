---
title: Update Compliance-jelentések használata Windows-frissítésekhez a Microsoft Intune
titleSuffix: Microsoft Intune
description: A OMS Update Compliance használatával megtekintheti az Intune-nal üzembe helyezett Windows-frissítések jelentési szolgáltatásait.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1e493e0d2d562c0f69454d1999e82b528c724a2
ms.sourcegitcommit: e4602481a25a5e12379f673dfe801c611f51c35b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731279"
---
# <a name="intune-compliance-reports-for-updates"></a>Intune-megfelelőségi jelentések a frissítésekhez

Ha az Intune-nal telepíti a Windows Update szolgáltatást a Windows 10-es eszközökre, tekintse meg a frissítés megfelelőségének részleteit az Intune használatával vagy egy *Update Compliance*nevű ingyenes megoldással, amely a Microsoft Operations Management Suite részét képezi (OMS).

## <a name="use-intune"></a>Az Intune használata

A konfigurált Windows 10-es frissítési körök telepítési állapotára vonatkozó házirend-jelentés áttekintése:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **Áttekintés** > a **szoftverfrissítés állapota**lehetőséget. Itt általános információkat találhat minden hozzárendelt frissítési kör állapotáról.

3. További részletek megtekintéséhez válassza a **figyelő**lehetőséget. Ezután a **szoftverfrissítések**alatt válassza a **frissítési kör központi telepítési állapota** lehetőséget, és válassza ki az üzembe helyezési kört az áttekintéshez.

   Az adott frissítési kör adatainak megtekintéséhez a **Figyelés** szakaszban válasszon az alábbi jelentések közül:

   - **Eszközállapot**– megjeleníti az eszköz konfigurációjának állapotát, a részletekért lásd: [deviceConfigurationDeviceStatus frissítése]( https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-update?view=graph-rest-1.0).

   - **Felhasználói állapot**– a rendszer megjeleníti a Felhasználónév, az állapot és az utolsó jelentés dátumát, a részletekért lásd: [deviceConfigurationUserStatuses listázása](https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationuserstatus-list?view=graph-rest-1.0).

   - **Végfelhasználói frissítés állapota**– ez a beállítás a Windows-eszköz frissítési állapotát jeleníti meg, részletekért lásd: [windowsUpdateState](https://docs.microsoft.com/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta).

## <a name="use-update-compliance"></a>Update Compliance használata

A Windows 10-es frissítések bevezetését a Windows Analytics megoldás [Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)használatával figyelheti. Update Compliance a Azure Portal keresztül érhető el, és az [előfeltételeknek](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites)megfelelő eszközök számára ingyenesen elérhető.  

Ha ezt a megoldást használja, egy kereskedelmi azonosítót kell központilag telepítenie az Intune által kezelt Windows 10 rendszerű eszközökre, amelyekről jelentést szeretne készíteni a frissítés megfelelőségéről.  

Az Intune-ban az egyéni szabályzat OMA-URI beállításait használhatja a kereskedelmi azonosító konfigurálásához. Lásd: [Egyéni beállítások használata Windows 10-es eszközökhöz az Intune-ban](../configuration/custom-settings-windows-10.md).

A kereskedelmi azonosító konfigurálására szolgáló OMA-URI (kis-és nagybetűket megkülönböztető) útvonal a következő: *./VENDOR/MSFT/DMCLIENT/Provider/MS DM Server/CommercialID*  

Az **OMA-URI beállítások hozzáadása vagy módosítása** alatt például a következő beállítások használhatók:

- **Beállítás neve**: Windows Analytics kereskedelmi azonosító
- **Beállítás leírása**: Kereskedelmi azonosító konfigurálása Windows Analytics megoldásokhoz
- **OMA-URI** (megkülönbözteti a kis-és nagybetűket): *./vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Adattípus:** Sztring
- **Érték**: \<használja a OMS munkaterület Windows telemetria lapján látható GUID azonosítót >

> [!NOTE]
> További információ az MS DM-kiszolgálóról: [DMClient konfigurációs szolgáltató (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>További lépések

[Szoftverfrissítések kezelése az Intune-ban](windows-update-for-business-configure.md)
