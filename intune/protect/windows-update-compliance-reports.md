---
title: Update Compliance-jelentések használata Windows-frissítésekhez a Microsoft Intune
titleSuffix: Microsoft Intune
description: A OMS Update Compliance használatával megtekintheti az Intune-nal üzembe helyezett Windows-frissítések jelentési szolgáltatásait.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09f3cafc16d8a08885731aa244a089367c6c0933
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732471"
---
# <a name="intune-compliance-reports-for-updates"></a>Intune-megfelelőségi jelentések a frissítésekhez
Ha az Intune-nal telepíti a Windows Update szolgáltatást a Windows 10-es eszközökre, tekintse meg a frissítés megfelelőségének részleteit az Intune használatával vagy egy *Update Compliance*nevű ingyenes megoldással, amely a Microsoft Operations Management Suite részét képezi (OMS).

## <a name="use-intune"></a>Az Intune használata
A konfigurált Windows 10-es frissítési körök telepítési állapotára vonatkozó házirend-jelentés áttekintése: 
1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com/).
2. Kattintson a **Minden szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza a **Microsoft Intune** elemet.
3. Válassza a **Szoftverfrissítések** > **Áttekintés** lehetőséget. Itt általános információkat találhat minden hozzárendelt frissítési kör állapotáról.
4. Nyissa meg az alábbi jelentések valamelyikét:  

   **Minden frissítési körhöz**:
   1. A **Szoftverfrissítések** > **Windows 10-es frissítési körök** területen
   2. A **Figyelés** szakaszban válassza a **Frissítési körönkénti telepítési állapot** lehetőséget.  

   **Meghatározott frissítési körökhöz**:  

   1. A **Szoftverfrissítések** > **Windows 10-es frissítési körök** területen válassza ki az áttekinteni kívánt frissítési kört.  
   2. Az adott frissítési kör adatainak megtekintéséhez a **Figyelés** szakaszban válasszon az alábbi jelentések közül:  
      - **Eszközállapot**  
      - **Felhasználó állapota**  

## <a name="use-update-compliance"></a>Update Compliance használata
A Windows 10-es frissítések bevezetését a Windows Analytics megoldás [Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)használatával figyelheti. Update Compliance a Azure Portal keresztül érhető el, és az megfelelő eszközök számára [előfeltételeknek](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites)ingyenesen elérhető.  

Ha ezt a megoldást használja, egy kereskedelmi azonosítót kell központilag telepítenie az Intune által kezelt Windows 10 rendszerű eszközökre, amelyekről jelentést szeretne készíteni a frissítés megfelelőségéről.  

Az Intune-konzolon egy egyéni házirend OMA-URI beállításait használhatja a kereskedelmi azonosító konfigurálásához. További információ: [A Microsoft Intune-ban regisztrált Windows 10-eszközökre vonatkozó Intune-szabályzatbeállítások](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

A kereskedelmi azonosító konfigurálására szolgáló OMA-URI (kis-és nagybetűket megkülönböztető) útvonal a következő: *./VENDOR/MSFT/DMCLIENT/Provider/MS DM Server/CommercialID*  

Az **OMA-URI beállítások hozzáadása vagy módosítása** alatt például a következő beállítások használhatók:
- **Beállítás neve**: Windows Analytics kereskedelmi azonosító
- **Beállítás leírása**: Kereskedelmi azonosító konfigurálása Windows Analytics-megoldásokhoz
- **OMA-URI** (megkülönbözteti a kis-és nagybetűket): *./vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Adattípus**: Sztring
- **Érték**: @no__t – a OMS-munkaterület Windows telemetria lapján megjelenő GUID 0Use >
 
> [!NOTE]  
> További információ az MS DM-kiszolgálóról: [DMClient konfigurációs szolgáltató (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>További lépések
[Szoftverfrissítések kezelése az Intune-ban](windows-update-for-business-configure.md)

