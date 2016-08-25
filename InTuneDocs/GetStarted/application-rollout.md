---
title: "Alkalmazás bevezetése | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 4a237942b4bc1e411cf55bc34c7b86d2249c526e


---

# Alkalmazás bevezetése
Ez a témakör konkrét javaslatokkal szolgál az alkalmazásoknak a Microsoft Intune-ban, fázisokra bontva történő bevezetéséhez. A bevezetési fázisokkal kapcsolatos általános információkért olvassa el [A Microsoft Intune üzembe helyezésének bevezetési fázisai](rollout-phases-for-microsoft-intune-deployment.md) című cikket.

### Az alkalmazás telepítésének fázisai
Az alkalmazás telepítésének fázisai a következők:

-   A projekt hatóköre

-   A koncepció igazolása

-   Próbaüzem

-   Vállalati bevezetés

-   Üzemeltetés és karbantartás

## A projekt hatóköre
Ügyeljen a következőkre:

-   A felhasználói feladat, amelynek feltételeit az alkalmazás megteremti.

-   Az alkalmazás megfelelősége a felhasználók és az eszközeik számára (minden várhatóan használt operációs rendszer esetén).

-   Ellenőrizze, hogy a kiválasztott alkalmazás telepítőjét támogatja-e az Intune-alkalmazásterjesztés, az [Alkalmazások hozzáadása Microsoft Intune-nal](/intune/deploy-use/add-apps) című cikkben leírtak szerint.

-   Győződjön meg arról, hogy telepítve vannak-e az alkalmazásterjesztési előfeltételek. <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md--->).

-   Állapítsa meg, hogy az alkalmazástípust támogatja-e az Intune.

-   Ellenőrizze, hogy van-e elegendő szabad terület a felhőalapú tárhelyen az alkalmazás feltöltéséhez. A további tárterület megvásárlásával kapcsolatos útmutató az [Alkalmazások hozzáadása Microsoft Intune-nal](/intune/deploy-use/add-apps) című cikkben található.

> [!NOTE]           
> A bevezetési folyamathoz segítségképpen letöltheti ezt a [mobilalkalmazásokhoz készült tervezősablont](https://gallery.technet.microsoft.com/Mobile-app-planning-18689d59).

## A koncepció igazolása
A koncepció igazolására szolgáló fázisban az alkalmazás telepítésének tesztelését tesztkörnyezetben, szigorúan csak tesztelési célokra beállított eszközökön és felhasználókon szabad végezni.

-   Célszerű, ha a segélyszolgálat is részt vesz ebben a fázisban, hogy megismerje a próbaüzem és az éles telepítés során esetleg felmerülő problémákat. Hibaelhárítási információk az [Alkalmazás telepítésével kapcsolatos problémák elhárítása a Microsoft Intune-ban](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune) című cikkben találhatók.

-   A folyamatnak ezen a pontján kommunikációs terveket kell kidolgozni a próbaüzem és az éles üzem felhasználóinak számára. A tervnek mindenképp tartalmaznia kell a telepítendő alkalmazás leírását, a felhasználókhoz való eljuttatásának módját és idejét, a telepítés üzleti célját, a teendőket arra az esetre, ha a felhasználók problémákat tapasztalnak, továbbá az önsegítő információkat és a segélyszolgálattal való kapcsolatfelvétel módját.

## Próbaüzem
A próbaüzem során tesztfelhasználók és -eszközök kis csoportja számára fogja telepíteni az alkalmazást. Ügyeljen a következőkre:

-   A tesztcsoportnak azokat a felhasználókat és eszközöket kell modelleznie, akik és amelyek az üzemi bevezetést követően az alkalmazást használni fogják.

-   Az alkalmazás telepítését ismertetni kell a segélyszolgálat munkatársaival, és meg kell győződni arról, hogy felkészültek a tesztcsoport felhasználóinak segítésére.

-   Válassza ki azokat a tesztfelhasználókat, akik az alkalmazást jellemző napi használatba fogják venni, és megbízhatóan jelenteni fogják a problémákat a próbaüzem rendszergazdái számára.

-   Aktiválja a próbaüzem felhasználói kommunikációs tervét.

## Vállalati bevezetés

-   A próbaüzem eredményeinek felhasználásával módosítsa a vállalati bevezetést.

-   Tájékoztassa a segélyszolgálatot az alkalmazás bevezetésének ütemezéséről. Gondoskodjon a segélykérelmek megválaszolásához és a bevezetés szükség szerinti módosításához szükséges mechanizmusok előkészítéséről.

-   Készüljön fel a telepítés hibáinak problémák felmerülése esetén szükséges elhárítására.

-   Aktiválja az éles üzem felhasználói kommunikációs tervét.

-   Az alkalmazás telepítéséhez használjon fázisokra bontott megközelítést, a bevezetés zökkenőmentes haladásának biztosítása érdekében fokozatosan adja hozzá a csoportokat.

## Üzemeltetés és karbantartás
**Üzemeltetés:** Figyelje az Intune-konzolon a riasztásokat és a felhasználókkal vagy eszközökkel kapcsolatos problémákat, az alkalmazás tervek szerint történő terjesztésének biztosítása érdekében.

**Segélyszolgálat:** Gondoskodjon arról, hogy a segélyszolgálat tudjon az alkalmazás elérhetőségének minden olyan módosításáról, amely támogatási kérelmeket eredményezhet.

### További információ
[Alkalmazások telepítése](/intune/deploy-use/deploy-apps)

[Alkalmazástelepítéssel kapcsolatos problémák elhárítása a Microsoft Intune-ban](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)



<!--HONumber=Jun16_HO4-->


