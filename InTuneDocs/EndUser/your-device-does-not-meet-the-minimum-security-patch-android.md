---
title: "Az eszköz nem felel meg a minimális biztonsági javítási szintnek | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b3e5994c-d215-4c72-8915-349bd0b2504d
ms.sourcegitcommit: b76c04545b9b26a0e2470b95a3f5ac0a81b07817
ms.openlocfilehash: a4788340b36c7d04ff1a62844aea7dba06079a2b


---

# Az eszköz nem felel meg a minimális biztonsági javítási szintnek

Ha megjelenik „A minimális Android biztonsági javítási szint nincs konfigurálva” üzenet, akkor telepítenie kell a minimális biztonsági javítást, vagy annak egy későbbi verzióját. A rendszergazdának fontos, hogy ez telepítve legyen az Android-eszközökön a vállalati adatok védelme érdekében.

A jelenlegi biztonsági javítási szint helye eltérő lehet attól függően, hogy milyen típusú Android-eszközt használ. Állapítsa meg, hogy Samsung Knox-eszközzel, vagy más típusú Android-eszközzel rendelkezik. A **Beállítások** > **Az eszköz névjegye** területen megállapíthatja, hogy Samsung Knox eszközzel rendelkezik-e. Ha nem jelenik meg a „Knox” szó, akkor nem Samsung Knox-eszközzel rendelkezik.

**A szoftververzió megállapítása:**

- Nem Samsung Knox-eszközön: Nyissa meg a **Beállítások** > **A telefonról** > **Szoftver adatok** > **Egyebek** menüt, majd az **Android biztonsági javítási szintje** lehetőséget. A menük nevei és helyei eltérhetnek a különböző Android-eszközökön.

- Samsung Knox-eszközön: Koppintson a **Beállítások** > **A telefonról** > **A biztonsági szoftver verziója** elemre.

**A kötelező biztonsági javítás telepítése:**

- Nem Samsung Knox-eszközön: Koppintson a **Beállítások** > **A telefonról** > **Szoftverfrissítés** lehetőségre. 

- Samsung Knox-eszközön: Koppintson a **Beállítások** > **Rendszerfrissítések** > **Rendszerfrissítés keresése** lehetőségre.

További segítségre van szüksége? Forduljon a rendszergazdához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).

### További információ
[Android-eszköz használata az Intune-nal](using-your-android-device-with-intune.md)



<!--HONumber=Jun16_HO3-->


