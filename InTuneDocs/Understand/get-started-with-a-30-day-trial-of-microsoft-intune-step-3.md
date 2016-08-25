---
# required metadata

title: Csoportok létrehozása a próba-előfizetés felhasználóinak és eszközeinek rendszerezésére | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Csoportok létrehozása a próba-előfizetés felhasználóinak és eszközeinek rendszerezésére
Az Intune csoportjai az eszközök és felhasználók rendkívül rugalmas kezelését teszik lehetővé. A szervezet saját igényeinek megfelelően csoportokat is létrehozhat (például földrajzi hely, részleg vagy hardverjellemzők alapján), amelyekkel számos felügyeleti feladatot elvégezhet, a felhasználói csoportok számára beállított házirendektől az alkalmazások eszközcsoportokra való telepítéséig.

## Eszközcsoport létrehozása
Az eszközcsoportok használatával szoftvereket és frissítéseket telepíthet, valamint konfigurálhatja „A Microsoft Intune-ügynök beállításai” és a „Windows tűzfal beállításai” házirendet. Állítsa be például a „Próbaverziós eszközök” csoportot az alábbi lépéseket követve:

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Áttekintés** &gt; **Csoport létrehozása** elemet..

2.  A **Csoportnév** mezőbe írja be a „Próbaverziós eszközök” kifejezést, válassza a szülőcsoportok listájának **Minden eszköz** elemét, majd válassza a **Tovább** gombot..

3.  A **Tagság feltételeinek meghatározása** lapon a **Minden eszköz** lehetőséget kiválasztva jelezze, hogy a csoport mobileszközöket és számítógépeket is tartalmaz.

4.  A **Közvetlen tagság meghatározása** lapon válassza a **Tovább** gombot. Ha előzőleg olyan csoportot hozott létre, amely nem tartalmazza az összes eszközt, és konkrét eszközöket szeretne hozzáadni az új csoporthoz, azt itt teheti meg.

5.  Az **Összefoglalás** lapon tekintse át a végrehajtandó műveleteket, majd válassza a **Befejezés** gombot..

Az újonnan létrehozott csoportot megtalálhatja a **Csoportok** munkaterület **Csoportok** listájának **Minden eszköz**lapján. Itt szerkesztheti és törölheti is a csoportot.

## Felhasználói csoport létrehozása
A felhasználói csoportokat szoftverek és eszköz- házirendek telepítésére használhatja. Állítsa be például a „Próbaverziós felhasználók” csoportot az alábbi lépéseket követve:

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Áttekintés** &gt; **Csoport létrehozása** elemet..

2.  A **Csoport neve** mezőbe írja be a „Próbaverziós felhasználók” kifejezést, válassza a szülőcsoportok listájának **Minden felhasználó** elemét, majd válassza a **Tovább** gombot..

3.  A **Tagság feltételeinek meghatározása** lap **Csoporttagság kezdése a következővel** beállítását állítsa **A szülőcsoport összes felhasználója** értékre..

4.  Kattintson a **Tagok kizárása ezekből a biztonsági csoportokból** lehetőség melletti **Tallózás** gombra, és válassza a **Vállalati rendszergazda** lehetőséget. E kizárás révén anélkül kezelheti a Próbaverziós felhasználók csoportot, hogy az hatással lenne a vállalati rendszergazda (más néven bérlői rendszergazda) fiókjára.

5.  A **Közvetlen tagság meghatározása** lapon válassza a **Tovább** gombot. Itt semmit nem kell tennie, mivel a vállalati rendszergazdán kívül minden felhasználónak bele kell tartoznia a Próbafelhasználók csoportba.

6.  Az **Összefoglalás** lapon tekintse át a végrehajtandó műveleteket, majd válassza a **Befejezés** gombot..

Az újonnan létrehozott csoportot megtalálhatja a **Csoportok** munkaterület **Csoportok** listájának **Minden felhasználó**lapján. Itt szerkesztheti és törölheti is a csoportot.

A csoportok használatával kapcsolatos további tájékoztatás a [Csoportok használata felhasználók és eszközök kezelésére a Microsoft Intune-nal](/Intune/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune) című témakörben olvasható..

### További lépések
Gratulálunk! Befejezte a *Microsoft Intune próbaverzió* útmutatójának 3. lépését.

>[!div class="step-by-step"]

>[&larr; **Felhasználók hozzáadása**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)     [**Házirendek létrehozása** &larr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  


<!--HONumber=May16_HO1-->


