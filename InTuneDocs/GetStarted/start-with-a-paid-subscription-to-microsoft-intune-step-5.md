---
# required metadata

title: Csoportok létrehozása a felhasználók és eszközök rendszerezéséhez | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Csoportok létrehozása a felhasználók és eszközök rendszerezéséhez
Az Intune csoportjai az eszközök és felhasználók rendkívül rugalmas kezelését teszik lehetővé. Különböző, a szervezet igényeinek megfelelő csoportokat állíthat be (például földrajzi hely, részleg vagy hardverjellemzők alapján), melyekkel számos felügyeleti feladatot elvégezhet, a házirendek felhasználók csoportjai számára történő telepítésétől az alkalmazások eszközök csoportjaira való telepítéséig.

Az eszközcsoportok és felhasználói csoportok létrehozása egyaránt az Intune felügyeleti konzol CSOPORTOK munkaterületén történik.

![A felügyeleti konzol Csoportok munkaterülete](./media/groups.png)


> [!TIP]
> A csoportok használatával kapcsolatos további tájékoztatás a [Csoportok használata felhasználók és eszközök kezelésére a Microsoft Intune-nal](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune) című témakörben olvasható..


## Eszközcsoport létrehozása
Az eszközcsoportokat alkalmazások és frissítések telepítésére, valamint egyéb funkciók konfigurálására használhatja. Például állítsa be az „Eszközök” csoportot a következő lépések alapján:

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Csoportok** > **Áttekintés** > **Csoport létrehozása** elemet..

2.  A **Csoport neve** mezőbe írja be az „Eszközök” értéket, a szülőcsoportok listájából válassza ki a **Minden eszköz** lehetőséget, majd válassza a **Tovább** gombot..

3.  A **Tagság feltételeinek meghatározása** lapon a **Minden eszköz** lehetőséget kiválasztva jelezze, hogy a csoport mobileszközöket és számítógépeket is tartalmaz.

4.  A **Közvetlen tagság meghatározása** lapon válassza a **Tovább** gombot. Ha előzőleg olyan csoportot hozott létre, amely nem tartalmazza az összes eszközt, és konkrét eszközöket szeretne hozzáadni az új csoporthoz, azt itt teheti meg.

5.  Az **Összefoglalás** lapon tekintse át a végrehajtandó műveleteket, majd válassza a **Befejezés** gombot..

Az újonnan létrehozott csoportot megtalálhatja a **Csoportok** munkaterület **Csoportok** listájának **Minden eszköz** lapján. Itt szerkesztheti és törölheti is a csoportot.

## Felhasználói csoport létrehozása
A felhasználói csoportokat szoftverek és eszköz- házirendek telepítésére használhatja. Például állítsa be az „Intune-felhasználók” csoportot a következő lépések alapján:

1.  Az [Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Csoportok** > **Áttekintés** > **Csoport létrehozása** elemet..

2.  A **Csoport neve** mezőbe írja be az „Intune-felhasználók” értéket, a szülőcsoportok listájából válassza ki a **Minden felhasználó** lehetőséget, majd válassza a **Tovább** gombot..

3.  A **Tagság feltételeinek meghatározása** lap **Csoporttagság kezdése a következővel** beállítását állítsa **A szülőcsoport összes felhasználója** értékre..

4.  Kattintson a **Tagok kizárása ezekből a biztonsági csoportokból** lehetőség melletti **Tallózás** gombra, és válassza a **Vállalati rendszergazda** lehetőséget. Ez a kizárás lehetővé teszi, hogy az Intune-felhasználók csoportot a vállalati rendszergazda fiók (más néven a bérlői rendszergazda) érintése nélkül kezelhesse.

5.  A **Közvetlen tagság meghatározása** lapon válassza a **Tovább** gombot. Itt semmit nem kell tennie, mivel a vállalati rendszergazdán kívül minden felhasználónak bele kell tartoznia az Intune-felhasználók csoportba.

6.  Az **Összefoglalás** lapon tekintse át a végrehajtandó műveleteket, majd válassza a **Befejezés** gombot..

Az újonnan létrehozott csoportot megtalálhatja a **Csoportok** munkaterület **Csoportok** listájának **Minden felhasználó** lapján. Itt szerkesztheti és törölheti is a csoportot.



### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések útmutatójának* 5. lépését..

>[!div class="step-by-step"]

>[&larr; **Az Intune-licencek kezelése**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**Szabályzatok és alkalmazások létrehozása** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  


<!--HONumber=May16_HO1-->


