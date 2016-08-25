---
title: "Az iOS-eszközök védelme az aktiválásizár-megkerüléssel | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 496679a196dc3e84c6b16ad0d3b830c81f12631b
ms.openlocfilehash: 7bbd761b13f110297959a036ec15cafe1396377e


---

# Az iOS-eszközök védelme a Microsoft Intune-hoz készült aktiválásizár-megkerüléssel
A Microsoft Intune szolgáltatással kezelhető az iOS aktiválási zára, amely az iOS 7.1 és újabb rendszerű eszközök Find My iPhone alkalmazásának egyik funkciója. Ha a Find My iPhone alkalmazást használják egy eszközön, az aktiválási zár automatikusan engedélyezve lesz. Az engedélyezése után meg kell adni a felhasználó Apple ID azonosítóját és jelszavát ahhoz, hogy el lehessen végezni a következők bármelyikét:

-   A Find My iPhone alkalmazás kikapcsolása

-   Az eszköz alaphelyzetbe állítása

-   Az eszköz újraaktiválása

## Az aktiválási zár hatásai
Az aktiválási zár segít biztosítani az iOS-eszközök biztonságát, és növeli a megtalálásuk esélyét azok elvesztésekor vagy ellopásakor, ugyanakkor ez a funkció számos kihívást is jelenthet Ön, mint rendszergazda számára. Példa:

-   Egy felhasználó beállítja az aktiválási zárat egy eszközön. A felhasználó később elhagyja a céget és visszaszolgáltatja az eszközt. A felhasználó Apple ID azonosítója és jelszava nélkül semmilyen módon nem lehet újraaktiválni az eszközt.

-   Szüksége van egy jelentésre az összes eszközről, amelyen engedélyezve van az aktiválási zár.

-   A szervezetben egy eszközfrissítés során néhány eszközt másik részleghez szeretne rendelni. Csak azokat az eszközöket lehet újból hozzárendelni, amelyeken nincs engedélyezve az aktiválási zár.

Az Apple az ilyen problémák megoldására vezette be az aktiválási zár megkerülését az iOS 7.1-ben. Ez lehetővé teszi az aktiválási zár a felhasználó Apple ID azonosítója és jelszava nélkül való eltávolítását a felügyelt eszközökről. A felügyelt eszközök létre tudnak hozni egy eszközspecifikus aktiválásizár-áthidaló kódot, mely az Apple aktiválási kiszolgálóján van tárolva.

> [!TIP]
> Az iOS-eszközök felügyelt módja lehetővé teszi az eszközök az Apple Configurator eszközzel való zárolását, így meghatározott üzleti célokra korlátozva annak funkcióit. A felügyelt mód általánosságban csak céges eszközökhöz használható.

## Az aktiválási zár kezelése az Intune-nal
Az Intune a felügyelt és a felügyeletlen iOS 7.1 vagy újabb rendszerű eszközök aktiválási zárának állapotát is le tudja kérdezni. Kizárólag a felügyelt eszközök esetében az Intune képes lekérdezni az aktiválásizár-áthidaló kódot, és közvetlenül kiadni azt az eszköznek. Ha törölték az eszköz adatait, a kódot felhasználónévként használva és üres jelszóval közvetlenül hozzáférhet az eszközhöz.

**Ennek a következők az üzleti előnyei**:

-   A felhasználó élvezheti a Find My iPhone alkalmazás biztonsági előnyeit.

-   Lehetővé teheti, hogy a felhasználó annak tudatában végezhesse a munkáját, hogy ha más rendeltetéssel kell felruházni az eszközt, akkor ki lehet vonni, illetve fel lehet oldani a zárolását.

## Az aktiválási zár megkerülésének használata az Intune felügyeleti konzolon
> [!IMPORTANT]
> Az aktiválási zár megkerülése után az eszköz a Find My iPhone alkalmazás megnyitásakor automatikusan egy újabb aktiválási zárat fog alkalmazni. Ezért **csak akkor kövesse ezt az eljárást, ha az eszköz a birtokában van**.

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) válassza a **Csoportok** &gt; **Minden eszköz** &gt; **Minden céges eszköz** elemet.

2.  Válassza ki azt az eszközt, amelynek aktiválási zárját meg szeretné kerülni. Válassza az **Aktiválási zár megkerülése** lehetőséget.

3.  Olvassa el a figyelmeztető üzenetet. A folytatáshoz válassza az **Igen** lehetőséget.

A zárolásfeloldási kérés állapotát az eszköz részleteit megjelenítő oldalon ellenőrizheti.

## Az aktiválási zárat használó eszközök megtekintése
Az alábbi két módon tekintheti meg az aktiválási zárat használó eszközöket:

-   Futtassa a **Mobileszközkészlet-jelentéseket**. Ebben a jelentésben az **Aktiválási zár állapota** és a **Felügyelt** oszlop mutatja az eszközök állapotát. A **Felügyelt** oszlopban **Igen** vagy **Nem**érték jelenik meg, az **Aktiválási zár állapota** oszlop értékei pedig a következők:

    -   Engedélyezve áthidaló kóddal

    -   Engedélyezve áthidaló kód nélkül (az eszköz nem felügyelt)

    -   Engedélyezve áthidaló kód nélkül (az eszköz nem érhető el)

    -   Nincs engedélyezve

    Az **Aktiválási zár állapota** mező a nem iOS 7.1 vagy újabb rendszerű eszközök esetén üres.

-   Ha egy Csoportok nézetben jelöl ki egy eszközt, az aktiválási zár állapota az eszköz részletező ablaktábláján jelenik meg.

    Ha a **Minden céges eszköz** csomópontban jelöl ki egy eszközt, és az aktiválási zár engedélyezve van az eszközön, megtekintheti az áthidaló kódot is. Ezzel a kóddal manuálisan végezhető el az aktiválási zár megkerülése.

### További információ
[Eszközök kivonása](retire-devices-from-microsoft-intune-management.md)
[Az adatok védelme távoli zárolással és jelszó alaphelyzetbe állításával](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


