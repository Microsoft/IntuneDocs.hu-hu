---
title: Üzembe helyezési célok, célkitűzések és kihívások meghatározása
titleSuffix: Microsoft Intune
description: Ez a cikk segítséget nyújt a Microsoft Intune csak felhőalapú megvalósításához kapcsolódó telepítési célok, célkitűzések és kihívások meghatározásában.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ea88396c9637b0eaf8fa6886f33164fafe25b09
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509968"
---
# <a name="determine-deployment-goals-objectives-and-challenges"></a>Üzembe helyezési célok, célkitűzések és kihívások meghatározása

A jó telepítési tervhez legelőször is meg kell határozni munkahelye telepítési céljait, célkitűzéseit, valamint a lehetséges kihívásokat. Az alábbiakban mindegyik kérdést részletesen is megtárgyaljuk.

## <a name="deployment-goals"></a>Üzembe helyezés céljai

Az üzembe helyezési célok azok a hosszútávú eredmények, amelyeket az Intune vállalatnál történő üzembe helyezésével el szeretne érni. Az alábbi felsorolásban ezekre a célokra találhatók példák a leírásukkal és az üzleti értékükkel együtt.

- **Integráció az Office 365-tel és az Office-mobilalkalmazások támogatása**

  - **Leírás:** Szoros integráció biztosítása az Office 365-tel, valamint az Office-mobilalkalmazások alkalmazásvédelemmel történő használata.

  - **Üzleti érték:** Biztonságos és fokozott felhasználói élmény azáltal, hogy a felhasználók az számukra ismerős és kedvelt alkalmazásokat használhatnak.

- **Belső céges szolgáltatásokhoz való hozzáférés engedélyezése mobileszközökön**

  - **Leírás:** Az alkalmazottak termelékenyen dolgozhatnak, bárhol is kell végezniük a munkát és bármely eszközzel, ami számukra a legelőnyösebb. Ez magába foglalja a mobileszközökről végzett hatékony munkát, valamint a céges adatokhoz való biztonságos hozzáférést.

  - **Üzleti érték:** Ha a munkavállalók agilisak lehetnek és bárhonnan tudnak dolgozni, a vállalkozás versenyképesebbé, a munkakörnyezet pedig jobbá válik.

- **Adatvédelem biztosítása a mobileszközökön**

  - **Leírás:** Ahol az adatokat mobileszközökön tárolják, ott meg kell védeni azokat a rosszindulatú vagy véletlenszerű elvesztésektől vagy megosztásoktól.

  - **Üzleti érték:** Az adatvédelem életbevágóan fontos, hogy versenyképesek maradjunk, valamint hogy saját és ügyfeleink adatait a lehető legkörültekintőbben kezeljük.

- **Költségcsökkentés**

  - **Leírás:** A projekt lehetőség szerint csökkenti a telepítési és működtetési költségeket.

  - **Üzleti érték:** Az erőforrások hatékony felhasználásával a vállalkozás más területeken is befektethet, hatékonyabban versenyezhet, valamint jobb szolgáltatásokat nyújthat ügyfeleinek.

## <a name="deployment-objectives"></a>Üzembe helyezés feladatai

Az üzembe helyezés feladatai olyan műveletek, amelyekkel az adott munkahely elérheti az Intune üzembe helyezési céljait. Az alábbiakban néhány példa következik az üzembe helyezési feladatokra, valamint azok megvalósítására.

- **Az eszközkezelési megoldások számának csökkentése**

  - **Megvalósítás:** Alkalmazásai és eszközei vállalati védelméhez szorítkozzon egyetlen mobileszköz-felügyeleti megoldásra, mégpedig a Microsoft Intune-ra.

- **Biztosítson az Exchange-hez és a SharePoint Online-hoz biztonságos hozzáférést**

  - **Implementáció:** Feltételes hozzáférés alkalmazása az Exchange-hez és a SharePoint Online-hoz.

- **Ne engedje, hogy a céges adatok a mobileszköz nem céges szolgáltatásain kerüljenek tárolásra vagy továbbításra**

  - **Megvalósítás:** Intune alkalmazásvédelmi szabályok alkalmazása a Microsoft Office-ra és az üzletági alkalmazásokra.

- **Biztosítsa a céges adatok törlésének képességét az eszközről**

  - **Megvalósítás** Eszközök regisztrálása az Intune-ban. Ez lehetővé teszi a vállalati adatok és erőforrások törlését a távolból, ha szükséges.

## <a name="deployment-challenges"></a>Üzembe helyezés kihívásai

Az üzembe helyezés kihívásai kiemelt fontossággal bírnak a cégek életében, és előfordulhat, hogy negatív hatást gyakorolhatnak magára a telepítésre. Olykor ezek régi projekteknél fellépő múltbéli problémákkal kapcsolatosak, amelyeket szeretne elkerülni, vagy pedig a jelenlegi üzembe helyezéskor felmerülő újakkal. Az alábbi listában néhány példa található az Intune üzembe helyezési kihívásaira és lehetséges kezelésükre.

- A kezdeti projekt nem terjed ki a támogatásra és a végfelhasználói élményre. Ez gyenge végfelhasználói adaptációhoz és a támogatás szervezésében jelentkező kihívásokhoz vezet.

  - **Megoldás:** Támogatási képzések beiktatása. A végfelhasználói tapasztalat érvényesítése az üzembe helyezési terv sikerességi metrikáival.

- A világosan meghatározott célok és sikerkritériumok metrikáinak hiánya miatt nincsenek kézzelfogható eredmények. Emiatt problémák jelentkezésekor a cég reaktív üzemmódba válthat.

  - **Megoldás:** A célokat és a siker kritériumait már a projekthatókör meghatározásának korai szakaszában definiálja, és ezeket az adatokat vegye alapul a bevezetés további fázisainak tervezéséhez. Győződjön meg róla, hogy SMART céljai vannak (Specific, Measurable, Attainable, Realistic, and Timely – meghatározottak, mérhetőek, elérhetőek, reálisok és időbeliek). Tervezze meg céljai mérését minden fázisban, hogy bevezetési projektjei biztosan a megfelelő irányba haladjanak.

- Elmulasztotta a cég értékeivel összhangban álló, világos értékjavaslat létrehozását, érvényesítését és agresszív megosztását. Ez gyakran korlátozott adaptációhoz és befektetésmegtérüléshez (ROI) vezet.

  - **Megoldás:** Bár bizonyára izgatottan várja, hogy belevágjon a projektbe, gondoskodjon arról, hogy pontosan meghatározza a céljait és törekvéseit. Ezeket foglalja bele valamennyi tájékoztatási és képzési tevékenységbe, hogy a felhasználók tisztában legyenek azzal, miért választotta a szervezet az Intune-t.

## <a name="next-steps"></a>További lépések

Most, hogy már meghatározta a telepítési célokat, célkitűzéseket és a lehetséges kihívásokat, áttérhet a következő szakaszra: [Tipikus használatieset-forgatókönyvek](planning-guide-scenarios.md).
