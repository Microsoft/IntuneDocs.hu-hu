---
title: Mobile Threat Defense a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Az Intune Mobile Threat Defense (MTD) szolgáltatást a mobileszköz-védelmi partnerével együtt használva eszközkockázaton alapuló módon védheti meg a vállalati erőforrásokhoz való hozzáférést.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97efe5c2445263bba11ee083e89d36fde1986dc1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732395"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Mit jelent a Mobile Threat Defense integrációja az Intune-nal?
Az Intune a mobil veszélyforrások elleni védelem gyártójától származó adatokat a megfelelőségi szabályzatok és a feltételes hozzáférési szabályok információs forrásaként integrálhatja. Ezekkel az információkkal megvédheti a vállalati erőforrásokat, például az Exchange-et és a SharePointot azáltal, hogy blokkolja a hozzáférést a feltört mobileszközökön.  

## <a name="what-problem-does-this-solve"></a>Milyen problémára nyújt ez megoldást?
A Mobile Threat Defense-gyártótól származó információk integrálásával megvédheti a vállalati erőforrásokat a mobil platformokat érintő fenyegetésektől.  

A vállalatok általában proaktív módon védik a számítógépeket a biztonsági rések és a támadások ellen, míg a mobileszközök gyakran nem figyelhetők meg és nem védettek. Ahol a mobil platformok beépített védelemmel rendelkeznek, például az alkalmazások elkülönítése és a bevett fogyasztói alkalmazások tárolói, továbbra is sebezhetőek lesznek a kifinomult támadásokkal szemben. Ahogy egyre több alkalmazott használ eszközöket a munkához és bizalmas információkhoz férhet hozzá, a Mobile Threat Defense-gyártótól származó információk segítenek az eszközök és az erőforrások egyre kifinomultabb támadások elleni védelmében.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Az Intune Mobile Threat Defense-összekötők működése

Az Intune egy Mobile Threat Defense-összekötőt használ az Intune és a kiválasztott Mobile Threat Defense-gyártó közötti kommunikációs csatorna létrehozásához. Az Intune Mobile Threat Defense-partnerek intuitív és könnyen telepíthető alkalmazásokat telepíthetnek a mobileszközök számára. Ezek az alkalmazások aktívan megvizsgálják és elemzik az Intune-nal való megosztásra vonatkozó veszélyforrásokat. Az Intune jelentéskészítési és kényszerítési célból is felhasználhatja az adatgyűjtést.  

Példa: Egy csatlakoztatott Mobile Threat Defense-alkalmazás jelentést küld a Mobile Threat Defense-gyártónak arról, hogy a hálózaton lévő telefon jelenleg csatlakoztatva van egy olyan hálózathoz, amely sebezhető az ember számára a középső támadásokban. Ez az információ az alacsony, közepes vagy magas megfelelő kockázati szintre van kategorizálva. Ezt a kockázati szintet a rendszer az Intune-ban beállított kockázati szintbeli kedvezmények összehasonlításával hasonlítja össze. Ezen összehasonlítás alapján a kiválasztott erőforrásokhoz való hozzáférés visszavonható, miközben az eszköz biztonsága sérül.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Milyen adatokat gyűjt az Intune a Mobile Threat Defense szolgáltatás számára?

Ha engedélyezte ezt a funkciót, az Intune mind a személyes, mind a vállalati tulajdonban lévő eszközökről alkalmazásleltár-adatokat gyűjt, amelyeket elérhetővé tesz a Mobile Threat Defense szolgáltatói, például a Lookout for Work számára. Az alkalmazásleltárt iOS operációs rendszerrel rendelkező felhasználóktól gyűjtheti be.

Ez a szolgáltatás nem kötelező, a leltáradatokat pedig nem osztjuk meg alapértelmezés szerint. Az alkalmazásleltár-adatok megosztása előtt egy Intune-rendszergazdának engedélyeznie kell a szolgáltatásbeállításokban az iOS-eszközök alkalmazásszinkronizációját.

**Alkalmazásleltár**  
Ha engedélyezi az iOS-eszközök alkalmazásszinkronizáicóját, az Intune mind a személyes, mind a vállalati tulajdonban lévő, iOS rendszerű eszközöktől alkalmazásleltár-adatokat küld az Ön MTD-szolgáltatójának. Az alkalmazásleltár adatai az alábbiakat tartalmazzák:

- Alkalmazásazonosító
- Alkalmazásverzió
- Alkalmazás rövid verziója
- Alkalmazásnév
- Alkalmazás csomagjának mérete
- Alkalmazás dinamikus mérete
- Az alkalmazás ellenőrzött állapota
- Az alkalmazás felügyelt állapota

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Ha a Mobile Threat Defense rendszer fertőzöttnek tekint egy eszközt:

![Kép: A Mobile Threat Defense által fertőzöttnek minősített eszköz](./media/mobile-threat-defense/MTD-image-1.png)

Ha az eszközről elhárul a veszély, a hozzáférés újra engedélyezett:

![Kép: A Mobile Threat Defense megadja a hozzáférést](./media/mobile-threat-defense/MTD-image-2.png)

> [!NOTE] 
> Az Intune nem támogatja egyszerre több Mobile Threat Defense-szolgáltató használatát. Egyszerre több MTD-eszköz engedélyezése minden MTD-alkalmazás telepítését váltja ki, és minden elérhető eszközön elvégzik a fenyegetések keresését.

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-partnerek

A vállalati erőforrásokhoz való hozzáférés védelme az eszköz-, a hálózati és az alkalmazáskockázat alapján:

- [A Lookout használatával](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [A Wanda Mobile Threat Defense](wandera-mtd-connector.md)
