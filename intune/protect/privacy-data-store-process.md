---
title: Adattárolás és feldolgozás az Intune-ban
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan tárolja és dolgozza fel a személyes információkat az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c9a8bd5888ab0977d1ca553d059c1e96cccda75
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306885"
---
# <a name="data-storage-and-processing-in-intune"></a>Adattárolás és feldolgozás az Intune-ban

Miután [az Intune az](privacy-data-collect.md)adatok gyűjtését, tárolását és feldolgozását az alábbiakban részletezett módon folytatja.

## <a name="storing-personal-data"></a>Személyes adattárolók tárolása

A rendszer az összes összegyűjtött nem telemetria-adatgyűjtést az Intune szolgáltatáson keresztül dolgozza fel, és a következő tárolóhelyek egy vagy több helyén tárolja: 

- Rendszerkarbantartás 
- Megbízható gyűjtemények (Service Fabric)  
- Azure Storage 

A telemetria (a szolgáltatási naplók, a Teljesítménynaplók, a hibák stb.), amelyek kulcsfontosságúak a figyeléshez és a stabil szolgáltatás megadásához, a rendszer elküldi a Microsoft telemetria-adattárait.

### <a name="storage-locations"></a>Tárolási helyszínek

A Microsoft világszerte számos régióban kínál és működtet Intune-szolgáltatásokat. Az Intune tiszteletben tartja a rendszergazda által az ügyféladatok számára megadott tárolási helyeket.

További információ: [Hol találhatók az adatok?](https://www.microsoft.com/trust-center/privacy/data-location)

### <a name="personal-data-retention"></a>Személyes adatok megőrzése

A személyes adatok általában a felhasználó Intune-felügyeletből való eltávolítása után 30 nappal maradnak meg az Intune-ban.

Az Intune-használat részeként gyűjtött telemetria-adatok maximális száma 30 nap.

A naplókat legfeljebb egy évig őrzi meg a rendszer.

## <a name="processing-personal-data"></a>Személyes adatainak feldolgozása

Az Intune ISO minősítésű rendszerekkel dolgozza fel a személyes adatbázisokat. További információ: [szolgáltatás megbízhatósági portálja](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Profilkészítés és marketing

Microsoft Intune nem használ a szolgáltatás profilkészítési vagy marketing célú biztosításának részeként gyűjtött személyes adatokat. 

### <a name="restrict-processing-of-personal-data"></a>Személyes adatainak feldolgozásának korlátozása

Ha korlátozni szeretné a felhasználó személyes adatainak feldolgozását, a következő lépésekkel törölheti a felhasználói fiókot:
1. A felhasználó személyes adatmásolatának exportálása, beleértve a következőket is
    - fiókok
    - szolgáltatás-adatértékek
    - társított naplók
2. A felhasználó fiókjának és a hozzájuk kapcsolódó adatoknak a törlése az Intune-ból.

## <a name="next-steps"></a>Következő lépések

Tudjon meg többet arról, hogy az Intune hogyan [védi és osztja](privacy-data-secure-share.md) meg a személyes adatait. 
