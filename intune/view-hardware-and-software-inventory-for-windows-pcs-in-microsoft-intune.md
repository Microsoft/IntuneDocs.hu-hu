---
title: Hardver- és szoftverleltár megtekintése Windows rendszerű számítógépeken
titleSuffix: Microsoft Intune
description: Az Intune szoftverügyfél által kezelt Windows-számítógépek hardver- és szoftverinformációinak megtekintése.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b9d17426bf3dde3fd1684c12113adf0c5095d5f
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353301"
---
# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Hardver- és szoftverleltár megtekintése Windows rendszerű számítógépeken

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> A jelen témakörben ismertetett információk csak azokra a PC-ként felügyelt Windows-számítógépekre vonatkoznak, amelyeket az Intune szoftverügyfél segítségével felügyel. Ha szeretné megtekinteni a mobileszközökként regisztrált Windows rendszerű számítógépek leltárát, tekintse meg [az eszköz adatainak megtekintése az Intune-ban](device-inventory.md)című témakört.

Az Intune részletes információkat gyűjt az olyan asztali számítógépekkel kapcsolatos hardverekről és szoftverekről, amelyeket az Intune-ügyfélszoftver használatával felügyel. Az alábbi eljárásokban lévő információkból megtudhatja:

- Hogyan hozhat létre olyan jelentést, amely az Ön által kezelt számítógépek hardvertulajdonságaival kapcsolatos információkat tartalmaz.

- Hogyan hozhat létre olyan jelentést, amely az egyes számítógépekre telepített szoftverek listáját tartalmazza.

- A számítógép leltározásának frissítése, hogy a jelentés adatai naprakészek legyenek.

## <a name="to-display-information-about-pcs-you-manage"></a>Az Ön által kezelt számítógépekkel kapcsolatos információk megjelenítése

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Jelentések** &gt; **Számítógépleltár-jelentések** lehetőséget.

2. Az **Új jelentés létrehozása** lapon fogadja el az alapértelmezett értékeket, vagy állítsa be őket a jelentés által visszaadott eredmények szűrésére. Kiválaszthatja például, hogy csak a Windows 8,1 rendszert futtató számítógépek jelenjenek meg a jelentésben.

3. A **Jelentés megtekintése** elemet választva megnyithatja a **Számítógépleltár-jelentést** egy új ablakban.

    Az egyes oszlopok fejlécét választva a jelentést bármelyik oszlop, például a **Név**, a **Ház típusa** vagy a **Gyártó** szerint rendezheti.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>Az Ön által kezelt számítógépekre telepített szoftverek megjelenítése

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Jelentések** &gt; **Észlelt szoftverek jelentései** elemet.

2. Az **Új jelentés létrehozása** lapon fogadja el az alapértelmezett értékeket, vagy állítsa be őket a jelentés által visszaadott eredmények szűrésére. Kiválaszthatja például, hogy csak a Microsoft által kiadott szoftverek jelenjenek meg a jelentésben.

3. A **Jelentés megtekintése** elemet választva megnyithatja az **Észlelt szoftverek jelentéseit** egy új ablakban.

    Az egyes oszlopok fejlécét választva a jelentést bármelyik oszlop, például a **Név**, a **Kiadó** vagy a **Kategória** alapján rendezheti. A listában lévő frissítések kibontásával, a listaelem mellett lévő, irányt mutató nyílra kattintva részletes információkat jeleníthet meg (például a számítógépeket, amelyeken telepítve van).

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>A számítógépleltár frissítése a naprakész állapot biztosításához

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza azt a számítógépet, amelynek a leltárát frissíteni szeretné).

2. Válasszon ki egy számítógépet, vagy tartsa lenyomva a **Ctrl** billentyűt több számítógép kijelöléséhez.

3. A tálcán válassza a **Távoli feladatok** &gt; **Leltár frissítése** elemet.

4. A feladat állapotának megtekintéséhez válassza a lap jobb alsó sarkában található **Távoli feladatok** elemet.

    A **Feladat állapota** párbeszédpanel megjeleníti az aktuális távoli feladatokat, a feladatok állapotát, az eszköz nevét és minden jelentett hibát, valamint egy hivatkozást kínál a hibaelhárítási információkhoz.

## <a name="see-also"></a>Lásd még:

[A Windows rendszerű számítógépek Intune-szoftverügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
