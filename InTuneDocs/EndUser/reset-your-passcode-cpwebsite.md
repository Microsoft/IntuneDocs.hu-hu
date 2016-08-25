---
title: "Az eszköz alaphelyzetbe állítása a Vállalati portál webhelyéről | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fd74fcdb26827b94d894b28d9d7f48e62420b14a
ms.openlocfilehash: 8f7b33a7e3cf73caee62eaa696fed8b7f65f28dc


---


# Az eszköz alaphelyzetbe állítása a Vállalati portál webhelyéről

Ha elveszíti egy Intune-ban regisztrált eszköz PIN-kódját vagy jelszavát, az eszköz alaphelyzetbe állításához a [Vállalati portál webhelyét](http://portal.manage.microsoft.com) használhatja. A Vállalati portál webhelye egy olyan weboldal, amelyet az Intune-ban regisztrált számítógépek és eszközök felügyeletére, illetve a legtöbb, a Vállalati portál alkalmazásban elvégezhető feladat végrehajtására is használhat.

> [!NOTE]
> Attól függően, hogy a rendszergazda hogyan konfigurálta az Intune-t, előfordulhat, hogy a Vállalati portál webhelyén nem jelenik meg a Jelszó alaphelyzetbe állítása gomb. A jelszó alaphelyzetbe állítása nem támogatott a Windows 8.1 és Windows RT rendszerű eszközökön.

A jelszó alaphelyzetbe állítása:

1.  Nyissa meg a [Vállalati portál webhelyét](http://portal.manage.microsoft.com), és koppintson arra az eszközre, amelynek a jelszavát alaphelyzetbe kívánja állítani.

2.  Koppintson a **Jelszó alaphelyzetbe állítása** gombra.

    ![resetp-passcode-option-on-company-portal-website](./media/iwp-screen-with-all-options.png)

3.  Koppintson a **Bejelentkezés** elemre, és jelentkezzen be újra a munkahelyi vagy iskolai hitelesítő adataival. Az újbóli bejelentkezésnek öt percen belül meg kell történnie.

    ![sign-out-sign-back-in](./media/iwp-2-sign-out.png)

4.  Koppintson a **Jelszó alaphelyzetbe állítása** gombra.

    ![tap-reset-passcode](./media/iwp-3-tap-reset-passcode-after-signin.png)

    Az alábbi táblázatban ellenőrizheti, hogyan működik eszközén a Jelszó alaphelyzetbe állítása funkció.

    |Platform|Support|
    |------------|-----------|
    |Android|Létrehoz egy új, ideiglenes, alfanumerikus jelszót.|
    |iOS|Eltávolítja a jelszót az eszközről, és nem hoz létre új, ideiglenes jelszót. Touch ID használata esetén újra be kell állítania azt az eszközön, mert a jelszó alaphelyzetbe állításakor ez az azonosító is törlődik.|
    |Windows 10 (csak mobileszközök esetén)|Létrehoz egy új, ideiglenes, alfanumerikus jelszót. A Windows Hello támogatott.|
    |Windows Phone 8.1|Létrehoz egy új, ideiglenes, numerikus jelszót.|
    Miután feloldotta az eszköz zárolását, az új jelszót az eszköz **Beállítások** menüjében állíthatja be.

5.  Oldja fel az eszköz zárolását, majd adjon meg egy új jelszót, vagy módosítsa az ideiglenes jelszót az eszköz **Beállítások** menüjében.

    Ha szeretne egy megerősítő értesítést megjeleníteni arról, hogy a jelszó átállítása sikeresen megtörtént, kattintson a Vállalati portál webhelyének felső sarkában található értesítésjelzőre.

További segítségre van szüksége? Forduljon a rendszergazdához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).

### További információ
[Az Intune vállalati portál webhelyének használata](using-the-intune-company-portal-website.md)



<!--HONumber=Aug16_HO3-->


