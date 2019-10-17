---
title: Windows 10 megosztott eszközbeállítások – Microsoft Intune – Azure | Microsoft Docs
description: A Windows 10 hozzáadásával és használatával konfigurálhatja a megosztott vagy Microsoft Intune több felhasználó által használt eszközöket. Tekintse meg az összes beállítás listáját, valamint azt, hogy mit csinálnak az eszközökön, beleértve a Microsoft Surfacet is. A vendég fiókjainak vezérlése, a fiókok kezelése és az inaktív fiókok törlése, a helyi tárterületre való mentés engedélyezése vagy letiltása, energiaellátási és alvó üzemmódok beállítása, a frissítések telepítésének engedélyezése és az eszközök használata az oktatási környezetekben az eszköz konfigurációs profiljában.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
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
ms.openlocfilehash: 588b6d39f1e3dc86f76279ef0446d9d58dc3e1df
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506618"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Windows 10 és újabb beállítások a megosztott eszközök Intune-nal történő kezeléséhez

A Windows 10 és újabb rendszerű eszközök, például a Microsoft Surface számos felhasználó számára is használhatók. A több felhasználóval rendelkező eszközöket megosztott eszközöknek nevezzük, és a mobileszköz-felügyeleti (MDM) megoldások részét képezik.

A Microsoft Intune használatával a végfelhasználók a vendég fiókkal bejelentkezhetnek ezekre a megosztott eszközökre. Ahogy az eszközt használják, csak az Ön által engedélyezett funkciókhoz férhetnek hozzá. Az Intune-rendszergazdaként konfigurálhatja a hozzáférést, kiválaszthatja, hogy a rendszer mikor törölje a fiókokat, szabályozhatja az energiagazdálkodási beállításokat, és így tovább a megosztott Windows 10-es eszközökhöz.

Ez a cikk a Windows 10-es (és újabb) eszköz konfigurációs profiljában használt beállításokat sorolja fel és ismerteti. Ha a profilt az Intune-ban hozza létre, a profilját üzembe helyezheti vagy hozzárendelheti a szervezetben lévő eszközökhöz. Ezt a profilt vegyes típusú és operációsrendszer-verziókkal rendelkező eszközök csoportjaihoz is hozzárendelheti.

Az Intune ezen funkciójával kapcsolatos további információkért lásd: [hozzáférés, fiókok és energiaellátási funkciók szabályozása megosztott számítógépeken vagy többfelhasználós eszközökön](shared-user-device-settings.md). A Windows CSP-vel kapcsolatos további információkért lásd: [SHAREDPC CSP](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp).

## <a name="before-your-begin"></a>Kezdés előtt

[Hozza létre a profilt](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Megosztott többfelhasználós eszközbeállítások

- **Megosztott számítógép üzemmód**: válassza az **Engedélyezés** lehetőséget a megosztott számítógép üzemmód bekapcsolásához. Ebben a módban egyszerre csak egy felhasználó jelentkezik be az eszközre. Egy másik felhasználó nem tud bejelentkezni, amíg az első felhasználó kijelentkezik. **Nincs konfigurálva** (alapértelmezés) nem az Intune által felügyelt beállítást hagyja, és nem küld semmilyen szabályzatot az eszközön a beállítás szabályozására.
- **Vendég fiók**: válasszon egy vendég lehetőséget a bejelentkezési képernyőn. A vendég fiókoknak nincs szükségük felhasználói hitelesítő adatokra vagy hitelesítésre. Ez a beállítás minden használatkor új helyi fiókot hoz létre. A választható lehetőségek:
  - **Vendég**: a vendég fiókot helyileg hozza létre az eszközön.
  - **Tartomány**: vendég fiókot hoz létre Azure Active Directory (ad).
  - **Vendég és tartomány**: helyi fiók létrehozása az eszközön, valamint Azure Active Directory (ad).
- **Fiókkezelés**: az **Engedélyezés** beállítás megadásával automatikusan törölheti a vendégek által létrehozott helyi fiókokat és az AD-és Azure ad-fiókokat. Amikor egy felhasználó kijelentkezik az eszközön, vagy ha a rendszer karbantartását futtatja, ezek a fiókok törlődnek. Ha engedélyezve van, állítsa be a következőket is:
  - **Fiók törlése**: válassza ki, hogy mikor történjen a fiókok törlése: **a tárolóhelyek küszöbértéke**, **a tárolóhelyek küszöbértéke és az inaktív küszöbérték**, vagy közvetlenül a kijelentkezés **után**. Adja meg a következőket is:
    - **Kezdeti törlési küszöb (%)** : adja meg a lemezterület százalékos arányát (0-100). Ha a teljes lemez/tárterület a megadott érték alá csökken, a rendszer törli a gyorsítótárazott fiókokat. Folyamatosan törli a fiókokat a lemezterület felszabadításához. A rendszer először törli a leghosszabb ideig inaktív fiókokat.
    - **Törlési küszöb leállítása (%)** : adja meg a lemezterület százalékos arányát (0-100). Ha a teljes lemez/tárolóhely megfelel a megadott értéknek, a törlés leáll.

  A **Letiltás** beállítás megadásával megtarthatja a vendégek által létrehozott helyi, ad-és Azure ad-fiókokat.

- **Helyi tárterület**: válassza az **engedélyezve** lehetőséget, hogy megakadályozza a felhasználók számára a fájlok mentését és megtekintését az eszköz merevlemezén. Válassza a **Letiltva** lehetőséget, hogy a felhasználók a fájlkezelő használatával helyileg lássák és mentsenják a fájlokat. **Nincs konfigurálva** (alapértelmezés) nem az Intune által felügyelt beállítást hagyja, és nem küld semmilyen szabályzatot az eszközön a beállítás szabályozására.
- **Energiagazdálkodási házirendek**: Ha az **engedélyezve**értékre van állítva, a felhasználók nem kapcsolhatják ki a hibernált állapotot, az összes alvó műveletet nem lehet felülbírálni (például a fedél bezárása), és nem változtathatják meg az energiaellátási beállításokat. Ha a beállítás **Letiltva**értékre van állítva, a felhasználók hibernálják az eszközt, lezárhatók a fedelet az eszköz alvó állapotában, és módosíthatják az energiaellátási beállításokat. **Nincs konfigurálva** (alapértelmezés) nem az Intune által felügyelt beállítást hagyja, és nem küld semmilyen szabályzatot az eszközön a beállítás szabályozására.
- **Alvó állapot időtúllépése (másodperc)** : adja meg az inaktív másodpercek számát (0-100), mielőtt az eszköz alvó üzemmódba kerül. Ha nem állít be időpontot, az eszköz 60 perc elteltével alvó állapotba kerül.
- **Bejelentkezés a számítógép ébresztése esetén**: beállítás **engedélyezve** értékre állításával a felhasználóknak jelszóval kell bejelentkezniük, ha az eszköz alvó üzemmódból származik. Válassza a **Letiltva** lehetőséget, hogy a felhasználóknak ne kelljen megadniuk felhasználónevét és jelszavát. **Nincs konfigurálva** (alapértelmezés) nem az Intune által felügyelt beállítást hagyja, és nem küld semmilyen szabályzatot az eszközön a beállítás szabályozására.
- **Karbantartási kezdési idő (percben éjféltől)** : adja meg az időt percben (0-1440) az automatikus karbantartási feladatok, például a Windows Update futtatása esetén. Az alapértelmezett indítási idő éjfél vagy nulla (@no__t – 0) perc. A kezdés időpontjának megváltoztatásához adjon meg egy kezdő időpontot percben éjféltől. Ha például azt szeretné, hogy a karbantartás 2 ÓRAKOR kezdődjön, írja be a következőt: `120`. Ha azt szeretné, hogy a karbantartás 8 ÓRAKOR kezdődjön, írja be a következőt: `1200`.
- **Oktatási szabályzatok**: válassza az **engedélyezve** lehetőséget az iskolákban használt eszközök ajánlott beállításainak használatához, amelyek szigorúbbak. Válassza a **Letiltva** lehetőséget, hogy az alapértelmezett és az ajánlott oktatási házirendek ne legyenek használatban. **Nincs konfigurálva** (alapértelmezés) nem az Intune által felügyelt beállítást hagyja, és nem küld semmilyen szabályzatot az eszközön a beállítás szabályozására.

  Az oktatási szabályzatok végrehajtásával kapcsolatos további információkért lásd: [Windows 10 konfigurációs javaslatok oktatási ügyfelek számára](https://docs.microsoft.com/education/windows/configure-windows-for-education).

> [!TIP]
> [Megosztott vagy vendég számítógép beállítása](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc) (egy másik docs webhelyének megnyitása) Ez a Windows 10 szolgáltatás kiváló forrása, beleértve a közös módban beállítható fogalmakat és csoportházirendeket is.

## <a name="next-steps"></a>További lépések

- [Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
- Tekintse meg a [Windows holografikus for Business](shared-user-device-settings-windows-holographic.md)beállításait.
