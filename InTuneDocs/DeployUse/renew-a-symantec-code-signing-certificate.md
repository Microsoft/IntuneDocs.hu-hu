---
title: "Symantec vállalati kódaláíró tanúsítvány megújítása a Microsoft Intune-nal való használatra | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 566a226c19825990c6a34bffbbd9d1cd6a242ddb


---

# A Windows-eszközökhöz használt Symantec vállalati kódaláíró tanúsítvány megújítása

Az egyes Windows és Windows Phone rendszerű mobileszközök kezelésére szolgáló Symantec-tanúsítványt rendszeres időközönként meg kell újítani. Windows Phone 8.0-s telefonok regisztrálásához aláírt Vállalati portál alkalmazásra és a kódaláíró tanúsítványra van szükség. A Windows Phone újabb verzióit használó eszközökön használható az áruházból letöltött vállalati portál alkalmazás. Az üzletági alkalmazások telepítéséhez is szükség lehet kódaláíró tanúsítványra.

## A Symantec vállalati kódaláíró tanúsítvány megújítása

1.  Keressen a Symantec által küldött, megújításra vonatkozó e-mailt körülbelül két héttel a tanúsítvány lejárta előtt. Ez az e-mail tartalmazza a Symantec a vállalati tanúsítvány megújítására vonatkozó utasításait.

    A Symantec-tanúsítványokkal kapcsolatos további tudnivalókért keresse fel a [www.symantec.com](http://www.symantec.com) webhelyet, vagy hívja az 1-877-438-8776 vagy az 1-650-426-3400 telefonszámot.

2.  Nyissa meg a webhelyet (például: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)), és jelentkezzen be a tanúsítványhoz tartozó Symantec-gyártóazonosítóval és e-mail címmel. Fontos, hogy ugyanazon a számítógépen indítása el a megújítást, amelyen le fogja tölteni a tanúsítványt.

3.  Miután megkapta a jóváhagyást a megújításhoz és kifizette azt, töltse le a tanúsítványt.

## A Windows Phone 8.0 rendszerhez készült frissített tanúsítvány telepítése

1.  A legújabb Windows Phone-os Vállalati portál alkalmazást innen töltheti le, majd írhatja alá: [http://www.microsoft.com/hu-hu/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Nyissa meg az Intune felügyeleti konzolját ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)), majd a **Felügyelet**, **Mobileszköz-kezelés** &gt; **Windows Phone** lapot, és kattintson az **Aláírt alkalmazás feltöltése** elemre.

3.  Töltse fel az imént aláírt Vállalati portál alkalmazást. Az újonnan aláírt SSP.xap fájlra és a Symantectől kapott új .PFX-fájlra, vagy az ezzel az új .PFX-fájllal létrehozott alkalmazásregisztrációs adatblokkra lesz szüksége.

4.  A feltöltés befejeződése után az Intune felügyeleti konzol **Szoftverek** munkaterületén távolítsa el a Vállalati portál régi verzióját.

5.  Újból írja alá az összes vállalati üzletági alkalmazást ugyanezzel a tanúsítvánnyal, majd töltse fel azokat, és cserélje le a meglévő alkalmazásokat.

Jelenleg kizárólag az aláírt SSP.xap fájl biztosításával adható meg a frissített kódaláíró tanúsítvány. Az aláírt üzletági alkalmazások támogatásához alá kell írni, majd fel kell tölteni a Vállalati portál alkalmazást, annak ellenére, hogy a felhasználók az Áruházból fogják telepíteni azt.

## A frissített tanúsítvány telepítése Windows Phone 8.1 és újabb rendszerű eszközökre

1.  A legújabb Windows Phone-os Vállalati portál alkalmazást a letöltőközpontból töltheti le, majd írhatja alá: [http://www.microsoft.com/hu-hu/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Nyissa meg az [Intune felügyeleti konzolját](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com), majd a **Felügyelet** &gt; **Mobileszköz-kezelés** &gt; **Windows Phone** lapot, és kattintson az **Aláírt alkalmazás feltöltése** elemre.

3.  Töltse fel az imént aláírt Vállalati portál alkalmazást. Az újonnan aláírt SSP.xap fájlra és a Symantectől kapott új .PFX-fájlra, vagy az ezzel az új .PFX-fájllal létrehozott alkalmazásregisztrációs adatblokkra lesz szüksége.

4.  A feltöltés befejeződése után távolítsa el a vállalati portál régi verzióját a **Szoftverek**  munkaterületről.

5.  Írja alá az összes új és az esetlegesen frissített üzletági alkalmazásokat az új tanúsítvánnyal. A meglévő alkalmazásokat nem kell újra ellátni aláírással és újratelepíteni.


### További információ
[Windows Phone 8.0 kezelésének beállítása](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[Windows Phone kezelésének beállítása](set-up-windows-phone-management-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


