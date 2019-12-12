---
title: Mobile Threat Defense a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Az Intune Mobile Threat Defense (MTD) szolgáltatást a mobileszköz-védelmi partnerével együtt használva eszközkockázaton alapuló módon védheti meg a vállalati erőforrásokhoz való hozzáférést.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b67e3b14fd94376fb6dacad88fa58ddc460a6bc5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73057587"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>A Mobile Threat Defense integrációja az Intune-nal

Az Intune a mobileszköz-megfelelőségi szabályzatok és az eszközök feltételes hozzáférési szabályainak információs forrásaként integrálhatja az adatokat a Mobile Threat Defense (MTD) gyártójától. Ezekkel az információkkal megvédheti a vállalati erőforrásokat, például az Exchange-et és a SharePointot azáltal, hogy blokkolja a hozzáférést a feltört mobileszközökön.

Az Intune ezeket az adatforrásokat használhatja a nem regisztrált eszközökhöz az Intune app Protection-szabályzatok használatával. A rendszergazdák ezeket az információkat a [Microsoft Intune védett alkalmazáson](~/apps/apps-supported-intune-apps.md)belüli vállalati adatok védelmére, valamint egy blokk vagy szelektív törlés kibocsátására használhatják fel.

## <a name="protect-corporate-resources"></a>Vállalati erőforrások megóvása

A MTD-szállítók információinak integrálásával megvédheti a vállalati erőforrásokat a mobil platformokat érintő fenyegetésektől.  

A vállalatok általában proaktív módon védik a számítógépeket a biztonsági rések és a támadások ellen, míg a mobileszközök gyakran nem figyelhetők meg és nem védettek. Ahol a mobil platformok beépített védelemmel rendelkeznek, például az alkalmazások elkülönítése és a bevett fogyasztói alkalmazások tárolói, továbbra is sebezhetőek lesznek a kifinomult támadásokkal szemben. Ahogy egyre több alkalmazott használ eszközöket a munkához, és a bizalmas információkhoz is hozzáférnek, a MTD-szállítóktól származó információk segítenek az eszközök és az erőforrások egyre kifinomultabb támadások elleni védelmében.

## <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense-összekötők

Az Intune egy Mobile Threat Defense-összekötő használatával hozza létre az Intune és a kiválasztott MTD-szállító közötti kommunikációs csatornát. Az Intune MTD-partnereink intuitív és könnyen telepíthető alkalmazásokat biztosítanak a mobileszközök számára. Ezek az alkalmazások aktívan megvizsgálják és elemzik az Intune-nal való megosztásra vonatkozó veszélyforrásokat. Az Intune jelentéskészítési és kényszerítési célból is felhasználhatja az adatgyűjtést.

Például: egy csatlakoztatott MTD-alkalmazás jelenti a MTD gyártónak, hogy a hálózaton lévő telefon jelenleg csatlakoztatva van egy olyan hálózathoz, amely sebezhető az ember által a középső támadásokkal szemben. Ez az információ az alacsony, közepes vagy magas megfelelő kockázati szintre van kategorizálva. Ezt a kockázati szintet a rendszer az Intune-ban beállított kockázati szintbeli kedvezmények összehasonlításával hasonlítja össze. Ezen összehasonlítás alapján a kiválasztott erőforrásokhoz való hozzáférés visszavonható, miközben az eszköz biztonsága sérül.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Az Intune által a Mobile Threat Defense-hez gyűjtött adatok

Ha engedélyezve van, az Intune a személyes és a vállalati tulajdonú eszközökről gyűjti az alkalmazásadatok adatait, és elérhetővé teszi azokat a MTD-szolgáltatók számára, mint például a Lookout for Work. Az alkalmazásleltárt iOS operációs rendszerrel rendelkező felhasználóktól gyűjtheti be.

Ez a szolgáltatás nem kötelező, a leltáradatokat pedig nem osztjuk meg alapértelmezés szerint. Az Intune rendszergazdájának engedélyeznie kell az **alkalmazás-szinkronizálást iOS-eszközökön** a Mobile Threat Defense-összekötő beállításaiban, mielőtt bármely alkalmazás leltári információja meg van osztva.

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

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>Példák az eszköz megfelelőségi házirendjeit használó regisztrált eszközökre

Ha a Mobile Threat Defense rendszer fertőzöttnek tekint egy eszközt:

![Kép: A Mobile Threat Defense által fertőzöttnek minősített eszköz](./media/mobile-threat-defense/MTD-image-1.png)

Ha az eszközről elhárul a veszély, a hozzáférés újra engedélyezett:

![Kép: A Mobile Threat Defense megadja a hozzáférést](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Példák a nem regisztrált eszközökre az Intune app Protection-szabályzatok használatával

Ha a Mobile Threat Defense rendszer fertőzöttnek tekint egy eszközt:<br>
a Mobile Threat Defense fertőzött eszközét mutató ![kép](./media/mobile-threat-defense/MTD-image-3.png)

Ha az eszközről elhárul a veszély, a hozzáférés újra engedélyezett:<br>
![kép, amely a Mobile Threat Defense-hozzáférést adta meg](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> Több Mobile Defense-szállítót is használhat egyetlen Intune-Bérlővel. Ha azonban két vagy több gyártó ugyanazon a platformon való használatra van konfigurálva, az adott platformot futtató összes eszköznek telepítenie kell minden MTD alkalmazást, és be kell olvasnia a fenyegetéseket. Nem sikerült beolvasni bármely konfigurált alkalmazás eredményét, mert az eszköz nem megfelelőként van megjelölve. 

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-partnerek

A vállalati erőforrásokhoz való hozzáférés védelme az eszköz-, a hálózati és az alkalmazáskockázat alapján:

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [A Wanda Mobile Threat Defense](wandera-mtd-connector.md)
