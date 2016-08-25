---
title: "Vállalati tulajdonban lévő eszközök megadása IMEI-számokkal | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 398d93d4e2317d00a2f9d5f89966aaec3b942504
ms.openlocfilehash: af4b87eb8082ee5ff11cd2d42b788ad17b334bcb


---

# Vállalati tulajdonban lévő eszközök megadása IMEI-számokkal
A Microsoft Intune lehetővé teszi, hogy a rendszergazdák nemzetközi mobilkészülék-azonosító (IMEI-) számokat importáljanak IMEI-számokkal rendelkező mobileszköz-platformok esetén, hogy könnyebben azonosítsák a vállalati tulajdonban lévő mobileszközöket. Ha regisztrálta őket az Intune-ban, az importált IMEI-számmal rendelkező eszközök a **Csoportok** > **Áttekintés** > **Minden eszköz** > **Előre regisztrált vállalati eszközök** > **IMEI-szám szerint (minden platform)** menüpontban tekinthetők meg.

1. A [Microsoft Intune felügyeleti konzoljában](http://manage.microsoft.com) lépjen a **Csoportok** &gt; **Minden eszköz** &gt; **Előre regisztrált vállalati eszközök** &gt; **IMEI-szám szerint (minden platform)** területre, majd válassza az **Eszközök felvétele** lehetőséget. Két módon adhat hozzá eszközöket:

    -   **Sorozatszámokat tartalmazó CSV-fájl feltöltése** – Hozzon létre egy vesszővel elválasztott, kétoszlopos, fejléc nélküli értéklistát (.csv), amelyben maximum 5000 eszköz szerepel. A csv-fájl mérete nem haladja meg az 5 MB-ot.

        |||
        |-|-|
        |&lt;1. IMEI azonosító&gt;|&lt;1. eszköz részletei&gt;|
        |&lt;2. IMEI azonosító&gt;|&lt;2. eszköz részletei&gt;|
        Ez a .csv- fájl egy szövegszerkesztőben megtekintve így jelenik meg:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Eszközadatok kézi megadása** – Adja meg legfeljebb öt eszköz sorozatszámát és eszközrészleteit

   A *Részletek* adminisztrációs célokat szolgál, az eszközökkel társított IMEI-számok beazonosítása érdekében. Ezek az információk nem kerülnek át az eszközre, csak az Intune konzoljában jelennek meg.

2.   Kattintson a **Tovább** gombra.
3.  Az **Eszközök felülvizsgálata** panelen ellenőrizheti, hogy melyik IMEI-eszközszámok lettek importálva. Eldöntheti azt is, hogy felülírja-e az újraimportált IMEI-számok **Részleteit**. A **Felülírás** jelölőnégyzet jelölését törölve megőrizheti az aktuális részleteket. Válassza a **Befejezés** lehetőséget az IMEI-számok importálásához.
4.  A hozzáadott IMEI-számok és leírások az **IMEI szerint (minden platform)** listába kerülnek.

Amikor az adott IMEI-számmal rendelkező eszközt regisztrálják – általában akkor, amikor egy felhasználó telepíti a Vállalati portál alkalmazást, és elvégzi a regisztrációs folyamatot –, az eszköz Vállalati címkével fog rendelkezni, és regisztráltként jelenik meg az **IMEI-eszközök** csoportban.



<!--HONumber=Jul16_HO1-->


