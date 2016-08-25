---
title: "Szabályzat bevezetése | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 390d5adf-86d2-4e23-ba93-1e61e6b1028b
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 8935fbc42d7b406a5bcdbfc4353209b4447ae413


---

# Szabályzat bevezetése
Ez a témakör konkrét javaslatokkal szolgál a Microsoft Intune szabályzatainak fázisokra bontott bevezetéséhez. Ugyanez a módszer alkalmazható az Intune új központi telepítésében használt első szabályzatokra és a meglévő telepítéshez hozzáadott szabályzatokra is.

A bevezetési fázisokkal kapcsolatos általános információkért olvassa el [A Microsoft Intune üzembe helyezésének bevezetési fázisai](rollout-phases-for-microsoft-intune-deployment.md) című cikket.

### A szabályzat bevezetésének fázisai
A szabályzat bevezetésének fázisai a következők:

-   A projekt hatóköre

-   A koncepció igazolása

-   Próbaüzem

-   Vállalati bevezetés

-   Üzemeltetés és karbantartás

## A projekt hatóköre
Az Intune-szabályzat telepítési hatókörének meghatározása:

-   Új telepítés esetén ehhez meg kell határozni az összes olyan elvárt eszközviselkedést és biztonsági követelményt, amelyet el kíván érni a szabályzatokkal.

-   Döntse el, hogy mely felhasználókra és eszközökre kell foganatosítani ezeket a szabályzatokat.

-   Alakítsa úgy a felhasználói és eszközcsoportokat, hogy megfelelően alkalmazhassa az új szabályzatokat.

-   Határozza meg, hogy vannak-e olyan, az egyes operációs rendszerekhez kapcsolódó korlátozások vagy követelmények, amelyek hatással lehetnek a szabályzat céljaira.

-   Vegye figyelembe a szabályzatok kialakítási részleteit, például a használandó szabályzattípust vagy -sablont.

-   Akár az első szabályzatokat helyezi üzembe, akár a meglévő szabályzatokat bővíti új szabályzatokkal, vegye figyelembe, hogy a különféle szabályzatok hogyan hatnak egymásra, és az eszközöktől milyen viselkedés várható. A szabályzatok kölcsönhatásai és ütközései a Próbaüzem fázis alatt felderíthetők, de a szabályzatok ütközéseinek a korai tervezési szakaszban történő felfedezése egyszerűsíti a Próbaüzem végrehajtását.

## A koncepció igazolása
A koncepció igazolásának fázisában a szabályzat telepítésének tesztelését tesztkörnyezetben, szigorúan csak tesztelési célokra beállított eszközökön és felhasználókon szabad végezni.

-   Célszerű, ha a segélyszolgálat is részt vesz ebben a fázisban, hogy megismerje a próbaüzem és az éles telepítés során esetleg felmerülő problémákat. Hibaelhárítási információk a [Szabályzatokkal kapcsolatos problémák elhárítása a Microsoft Intune-ban](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune) című cikkben találhatók.

-   A folyamatnak ezen a pontján kommunikációs terveket kell kidolgozni a próbaüzem és az éles üzem felhasználóinak számára. A tervnek mindenképp tartalmaznia kell, hogy eszközök milyen működésmódjának és mikor kell megváltoznia, a módosítás üzleti célját, a teendőket arra az esetre, ha a felhasználók vagy az informatikai munkatársak problémákat tapasztalnak, továbbá az önsegítő információkat és a segélyszolgálattal való kapcsolatfelvétel módját.

## Próbaüzem
A próbaüzem során tesztfelhasználók és -eszközök kis csoportja számára telepíti a szabályzatot. A szabályzatok Intune-beli próbaüzeméhez figyelembe kell venni bizonyos dolgokat:

-   A tesztcsoportnak azt a csoportot kell modelleznie, amelyre a szabályzat az éles bevezetésben vonatkozni fog.

-   A szabályzat változásait ismertetni kell a segélyszolgálat munkatársaival, és meg kell győződni arról, hogy felkészültek a tesztcsoport felhasználóinak segítésére.

-   Aktiválja a próbaüzem felhasználói kommunikációs tervét.

-   A próbaüzemet először elkülönített módban kell elvégezni, amelyben az eszközre nem vonatkoznak más szabályzatok, amelyek ütközést és nem kívánt viselkedést okozhatnak.

-   A végső tesztnek figyelembe kell vennie az új szabályzatot, valamint az ugyanarra az eszközre alkalmazandó összes meglévő szabályzatot is.

## Vállalati bevezetés

-   A próbaüzem eredménye alapján végezze el a tervezett szabályzat módosítását, a szabályzatok ütközése és a nem várt viselkedés kijavítása érdekében.

-   Tájékoztassa a segélyszolgálatot a vállalati bevezetés ütemezéséről. Gondoskodjon a segélykérelmek megválaszolásához és a bevezetés szükség szerinti módosításához szükséges mechanizmusok előkészítéséről.

-   Készüljön fel a szabályzat hibáinak problémák felmerülése esetén szükséges elhárítására.

-   Aktiválja az éles üzem felhasználói kommunikációs tervét.

-   A szabályzatokat fokozatosan terjessze ki további csoportokra, az érintett eszközök esetén figyelje a szabályzat állapotát, és kövesse nyomon az új szabályzattal esetleg kapcsolatos segélyszolgálat-kérelmeket.

## Üzemeltetés és karbantartás
**Üzemeltetés:** Figyelje az Intune-konzolon a riasztásokat és a felhasználókkal vagy eszközökkel kapcsolatos problémákat, és ellenőrizze, hogy a szabályzatok a terveinek megfelelően működnek-e.

**Segélyszolgálat:** Győződjön meg arról, hogy a segélyszolgálat ismeri a szabályzatok minden olyan módosítását, amelyek hatással lehetnek a felhasználói élményre, mert ezek támogatási kérelmeket eredményezhetnek.


### További információ
[Felkészülés a mobilalkalmazás-felügyeleti szabályzatok konfigurálására a Microsoft Intune-ban](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Szabályzatokkal kapcsolatos problémák elhárítása a Microsoft Intune-ban](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)



<!--HONumber=Jun16_HO4-->


