---
title: "E-mail profilok hibaelhárítása | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c22ddd554928b394e14742b8ba7d583d390d1c44
ms.openlocfilehash: 766c5d5f8e512ea1c36c73936b0ffb95977395ae


---

# E-mail profilok hibaelhárítása a Microsoft Intune-ban
Az alábbiakban néhány, az e-mail profilokkal kapcsolatos problémát ismertetünk, az elhárításukkal és a megoldásukkal együtt.

Ha ezekkel az információkkal nem tudja megoldani a problémát, a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben talál további részleteket a segítségkéréshez.


## Nem sikerül képeket küldeni az e-mail fiókból
Az automatikusan konfigurált e-mail fiókkal rendelkező felhasználók nem tudnak képeket küldeni az eszközeikről.
Ez akkor fordul elő, ha a **Harmadik felek alkalmazásaiból is engedélyezett az e-mailek küldése** beállítás nincs engedélyezve.

### Intune-megoldás

1.  Nyissa meg a Microsoft Intune felügyeleti konzolját, és válassza a **Házirend** &gt; **Konfigurációs szabályzat** lehetőséget.

2.  Válassza ki a kívánt e-mail-profilt, majd válassza a **Szerkesztés** lehetőséget.

3.  Válassza ki a **Harmadik felek alkalmazásaiból is engedélyezett az e-mailek küldése** beállítást.

### Intune-megoldással integrált Configuration Manager

1.  Nyissa meg a Configuration Manager-konzol &gt; **Eszközök és megfelelőség** elemét.

2.  Bontsa ki az **Áttekintés** -&gt; **Megfelelőségi beállítások** -&gt; **Hozzáférés a vállalati erőforrásokhoz** elemeket, és válassza az **E-mail profilok** lehetőséget.

3.  Kattintson a jobb gombbal az e-mail-profilra, és nyissa meg a **Tulajdonságok** menüt.

4.  A **Szinkronizációs beállítások** lapon válassza a **Harmadik felek alkalmazásaiból is engedélyezett az e-mailek küldése** lehetőséget.

## További lépések
Ha ezek a hibaelhárítási információk nem oldották meg a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben leírtak szerint.



<!--HONumber=Jun16_HO4-->


