---
title: Windows holografikus üzleti megosztott eszköz beállításai – Microsoft Intune – Azure | Microsoft Docs
description: A Windows holografikus for Business hozzáadásával és használatával konfigurálhatja a megosztott vagy Microsoft Intune több felhasználó által használt eszközöket. Tekintse meg a fiók-felügyeleti beállítások listáját, valamint azt, hogy mit csinálnak az eszközökön, beleértve a Microsoft HoloLens is.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9c89712539d4e5bd78cc317af2af396f8ca7006
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492219"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Windows holografikus for Business-beállítások a megosztott eszközök Intune-nal való kezeléséhez

Több felhasználó is használhatja a Windows holografikus for Business-eszközöket, például a Microsoft HoloLens. A több felhasználóval rendelkező eszközöket megosztott eszközöknek nevezzük, és a mobileszköz-felügyeleti (MDM) megoldások részét képezik.

A Microsoft Intune használatával a felhasználók vendég fiókkal jelentkezhetnek be ezekre a megosztott eszközökre. Ahogy az eszközt használják, csak az Ön által engedélyezett funkciókhoz férhetnek hozzá.

Ez a cikk a Windows holografikus for Business eszköz konfigurációs profiljában használt beállításokat sorolja fel és ismerteti. Miután létrehozta a profilt az Intune-ban, üzembe helyezheti vagy hozzárendelheti a profilt a szervezetben lévő eszközökhöz. Ezt a profilt vegyes típusú és operációsrendszer-verziókkal rendelkező eszközcsoport számára is hozzárendelheti.

Az Intune ezen funkciójával kapcsolatos további információkért lásd: [hozzáférés, fiókok és energiaellátási funkciók szabályozása megosztott számítógépeken vagy többfelhasználós eszközökön](shared-user-device-settings.md). A Windows CSP-vel kapcsolatos további információkért lásd: [ACCOUNTMANAGEMENT CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp).

## <a name="before-your-begin"></a>Kezdés előtt

[Hozza létre a profilt](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Megosztott többfelhasználós eszközbeállítások

> [!NOTE]
> A Windows holografikus for Business rendszert futtató eszközök, beleértve a Microsoft HoloLens, csak a **Fiókkezelés** beállításait támogatják. Ha az Intune-ban megjelenő egyéb beállítások bármelyikét konfigurálja, beleértve a **megosztott számítógépes üzemmódot**, az nem érinti ezeket az eszközöket.

- **Fiókkezelés**: az **Engedélyezés** beállítás megadásával automatikusan törölheti a vendégek által létrehozott helyi fiókokat és az AD-és Azure ad-fiókokat. Amikor egy felhasználó kijelentkezik az eszközön, vagy ha a rendszer karbantartását futtatja, ezek a fiókok törlődnek. Ha engedélyezve van, állítsa be a következőket is:
  - **Fiók törlése**: válassza ki, hogy mikor történjen a fiókok törlése: **a tárolóhelyek küszöbértéke**, **a tárolóhelyek küszöbértéke és az inaktív küszöbérték**, vagy közvetlenül a kijelentkezés **után**. Adja meg a következőket is:
    - **Kezdeti törlési küszöb (%)** : adja meg a lemezterület százalékos arányát (0-100). Ha a teljes lemez/tárterület a megadott érték alá csökken, a rendszer törli a gyorsítótárazott fiókokat. Folyamatosan törli a fiókokat a lemezterület felszabadításához. A rendszer először törli a leghosszabb ideig inaktív fiókokat.
    - **Törlési küszöb leállítása (%)** : adja meg a lemezterület százalékos arányát (0-100). Ha a teljes lemez/tárolóhely megfelel a megadott értéknek, a törlés leáll.

  A **Letiltás** beállítás megadásával megtarthatja a vendégek által létrehozott helyi, ad-és Azure ad-fiókokat.

  > [!NOTE]
  > A Microsoft HoloLens-eszközök csak a **Fiókkezelés** beállításait támogatják.

## <a name="next-steps"></a>További lépések

- [Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
- Tekintse meg a [Windows 10 és újabb rendszer](shared-user-device-settings-windows.md)beállításait.
