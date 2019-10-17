---
title: Hálózati végpontok az Egyesült Államok kormányának üzembe helyezéséhez – Microsoft Intune
titleSuffix: ''
description: Tekintse át az Egyesült államokbeli kormányzati végpontokat az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5e52d1967ff6f5cf97334c099bc2b5b854ae87c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502681"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Az Egyesült Államok kormányzati végpontja Microsoft Intune

Ezen a lapon az Intune-környezetekben a proxybeállítások számára szükséges Egyesült államokbeli kormányzati végpontok szerepelnek.

A tűzfalak és proxykiszolgálók mögötti eszközök kezeléséhez engedélyeznie kell az Intune-nal való kommunikációt.

- A proxykiszolgálónak támogatnia kell mind a **HTTP (80)** , mind a **HTTPS (443)** protokollt, mert az Intune-ügyfelek mindkét protokollt használják
- Bizonyos feladatokhoz (például a szoftverfrissítések letöltéséhez) az Intune-nak nem hitelesített proxykiszolgáló-hozzáférésre van szüksége a manage.microsoft.com

Az egyes ügyfélszámítógépeken módosíthatja a proxykiszolgáló beállításait. A megadott proxykiszolgáló mögött található ügyfélszámítógépek beállításainak módosításához Csoportházirend beállításokat is használhat.

A felügyelt eszközöket úgy kell beállítani, hogy **Minden felhasználó** hozzáférjen a szolgáltatásokhoz a tűzfalon keresztül.

A következő táblázat az Intune-ügyfél által elért portokat és szolgáltatásokat tartalmazza:

|**Végpont**|**IP-cím**|
|---------------------|-----------|
|*. manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Az Egyesült Államok kormányzati ügyfelei által kijelölt végpontok:
- Azure Portal: https: \//Portal. Azure. us/ 
- Office 365: https: \//Portal. Office 365. us/ 
- Intune Céges portál: https: \//Portal. Manage. microsoft. USA/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>A partneri szolgáltatási végpontok, amelyeket az Intune a következőktől függ:
- AAD-szinkronizáló szolgáltatás: https: \//syncservice. gov. us. microsoftonline. com/DirectoryService. SVC
- Evo STS: https: \//login. microsoftonline. us
- Directory proxy: https: \//directoryproxy. microsoftazure. us/DirectoryProxy. SVC
- HRE gráf: https: \//Directory. microsoftazure. us és https: \//Graph. microsoftazure. us
- MS gráf: https: \//Graph. microsoft. us
- ADRS: https: \//enterpriseregistration. microsoftonline. us
