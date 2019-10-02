---
title: Telepítési célok, célkitűzések és kihívások meghatározása
titleSuffix: Microsoft Intune
description: Ez a cikk segítséget nyújt a Microsoft Intune csak felhőalapú megvalósításához kapcsolódó telepítési célok, célkitűzések és kihívások meghatározásában.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8cc4a109aac22617f2785a74de701e4d1d7bdf09
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732223"
---
# <a name="determine-deployment-goals-objectives-and-challenges"></a>Üzembe helyezési célok, célkitűzések és kihívások meghatározása

A jó telepítési tervhez legelőször is meg kell határozni munkahelye telepítési céljait, célkitűzéseit, valamint a lehetséges kihívásokat. Az alábbiakban mindegyik kérdést részletesen is megtárgyaljuk.

## <a name="deployment-goals"></a>Üzembe helyezés céljai

Az üzembe helyezési célok azok a hosszútávú eredmények, amelyeket az Intune vállalatnál történő üzembe helyezésével el szeretne érni. Az alábbi felsorolásban ezekre a célokra találhatók példák a leírásukkal és az üzleti értékükkel együtt.

- **Integráció az Office 365-tel és az Office-mobilalkalmazások támogatása**

  - **Leírás:** Az Office 365 szoros integrációja és az Office Mobile apps használata az App Protection szolgáltatással.

  - **Üzleti érték:** Biztonságos és továbbfejlesztett felhasználói élmény azáltal, hogy lehetővé teszi a felhasználók számára, hogy a megszokott és kedvelt alkalmazásokat használják.

- **Belső céges szolgáltatásokhoz való hozzáférés engedélyezése mobileszközökön**

  - **Leírás:** Lehetővé teheti az alkalmazottak számára, hogy a munkahelyen való munkához szükségesek legyenek, és melyik eszköz a legmegfelelőbb számukra. Ez magába foglalja a mobileszközökről végzett hatékony munkát, valamint a céges adatokhoz való biztonságos hozzáférést.

  - **Üzleti érték:** Az alkalmazottak számára lehetővé teszi, hogy agilisak legyenek, és olyan helyről, ahol szükségük van rá, hogy a vállalat versenyképesebbé váljék, és nagyobb haszonú munkakörnyezetet biztosítson.

- **Adatvédelem biztosítása a mobileszközökön**

  - **Leírás:** Ha az adatok mobileszközön vannak tárolva, akkor azt védeni kell a rosszindulatú vagy véletlen adatvesztéstől vagy megosztástól.

  - **Üzleti érték:** Az adatvédelem létfontosságú annak biztosításához, hogy versenyképes maradjon, és hogy az ügyfeleket és az azokban lévő adatkezelést a lehető legnagyobb gondossággal kezeljék.

- **Költségcsökkentés**

  - **Leírás:** Ha lehetséges, a projekt csökkenti az üzembe helyezést és a működési költségeket.

  - **Üzleti érték:** Az erőforrások hatékony használata lehetővé teszi, hogy a vállalat más területeken fektessen be, hatékonyabban versenyezzen, és jobb szolgáltatást nyújtson az ügyfeleknek.

## <a name="deployment-objectives"></a>Üzembe helyezés feladatai

Az üzembe helyezés feladatai olyan műveletek, amelyekkel az adott munkahely elérheti az Intune üzembe helyezési céljait. Az alábbiakban néhány példa következik az üzembe helyezési feladatokra, valamint azok megvalósítására.

- **Az eszközkezelési megoldások számának csökkentése**

  - **Végrehajtása** Konszolidáció egyetlen mobileszköz-felügyeleti megoldásba: Microsoft Intune az alkalmazások és eszközök vállalati szintű védelméhez.

- **Biztosítson az Exchange-hez és a SharePoint Online-hoz biztonságos hozzáférést**

  - **Végrehajtása** Feltételes hozzáférés alkalmazása az Exchange-hez és a SharePoint Online-hoz.

- **Ne engedje, hogy a céges adatok a mobileszköz nem céges szolgáltatásain kerüljenek tárolásra vagy továbbításra**

  - **Végrehajtása** Az Intune app Protection-szabályzatok alkalmazása a Microsoft Office és az üzletági alkalmazásokhoz.

- **Biztosítsa a céges adatok törlésének képességét az eszközről**

  - **Végrehajtása** Eszközök regisztrálása az Intune-ban. Ez lehetővé teszi a vállalati adatok és erőforrások törlését a távolból, ha szükséges.

## <a name="deployment-challenges"></a>Üzembe helyezés kihívásai

Az üzembe helyezés kihívásai kiemelt fontossággal bírnak a cégek életében, és előfordulhat, hogy negatív hatást gyakorolhatnak magára a telepítésre. Olykor ezek régi projekteknél fellépő múltbéli problémákkal kapcsolatosak, amelyeket szeretne elkerülni, vagy pedig a jelenlegi üzembe helyezéskor felmerülő újakkal. Az alábbi listában néhány példa található az Intune üzembe helyezési kihívásaira és lehetséges kezelésükre.

- A kezdeti projekt nem terjed ki a támogatásra és a végfelhasználói élményre. Ez gyenge végfelhasználói adaptációhoz és a támogatás szervezésében jelentkező kihívásokhoz vezet.

  - **Kockázatcsökkentő** A támogatási képzés beépítése. A végfelhasználói tapasztalat érvényesítése az üzembe helyezési terv sikerességi metrikáival.

- A világosan meghatározott célok és sikerkritériumok metrikáinak hiánya miatt nincsenek kézzelfogható eredmények. Emiatt problémák jelentkezésekor a cég reaktív üzemmódba válthat.

  - **Kockázatcsökkentő** A célkitűzéseket és a sikerességi mérőszámokat a projekt hatókörében már korán definiálhatja, és ezeket az adatpontokat használhatja a többi bevezetési fázis kiépítéséhez. Győződjön meg róla, hogy SMART céljai vannak (Specific, Measurable, Attainable, Realistic, and Timely – meghatározottak, mérhetőek, elérhetőek, reálisok és időbeliek). Tervezze meg céljai mérését minden fázisban, hogy bevezetési projektjei biztosan a megfelelő irányba haladjanak.

- Elmulasztotta a cég értékeivel összhangban álló, világos értékjavaslat létrehozását, érvényesítését és agresszív megosztását. Ez gyakran korlátozott adaptációhoz és befektetésmegtérüléshez (ROI) vezet.

  - **Kockázatcsökkentő** Habár érdemes lehet beugrani a projektbe, győződjön meg róla, hogy világosan definiálta a céljait és célkitűzéseit. Ezeket foglalja bele valamennyi tájékoztatási és képzési tevékenységbe, hogy a felhasználók tisztában legyenek azzal, miért választotta a szervezet az Intune-t.

## <a name="next-steps"></a>További lépések

Most, hogy azonosította a telepítési célokat, a célkitűzéseket és a lehetséges kihívásokat, térjen át a következő szakaszra: A [használati esetek meghatározása](planning-guide-scenarios.md).
