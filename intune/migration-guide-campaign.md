---
title: Intune-migrációs kampány indítása
titlesuffix: Microsoft Intune
description: Ez a cikk egy Microsoft Intune-beli migrációs kampány indításához ad útmutatást.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8cfba95bdb25dcfa47e277d895f1fc4fbcc4a3a4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57398529"
---
# <a name="phase-2-migration-campaign"></a>2. fázis: Áttelepítési kampány

Válassza ki a cége igényeiknek leginkább megfelelő migrációs megközelítést, és igazítsa az adott követelményekhez a bevezetési taktikát. A jelen útmutató fennmaradó részében ismertetjük azon eszközöket, amelyekre szüksége lesz a felhasználók eszközeinek az Intune-ban való sikeres regisztrálásához.

## <a name="keys-to-a-successful-migration"></a>A migrálás sikerességének ellenőrzése

A külső MDM-szolgáltatóktól az Intune-ba való migrálás sikerességéhez kulcsfontosságúak a következők:

-   Folytasson érthető és segítőkész kommunikációt, minimálisra csökkentve a végfelhasználói üzemszünetet és elégedetlenséget.

-   Győződjön meg róla, hogy rendelkezik az adott helyzetre vonatkozó és konkrét migrálási utasításokkal.

-   Az összes felügyelt eszköz regisztrációjának megszüntetése a meglévő MDM-szolgáltatónál annak Intune-ban való regisztrálása előtt.

-   Útmutatás kérése a meglévő MDM-szolgáltatótól a végfelhasználók számára arra vonatkozóan, hogy miként szüntethetik meg eszközeik regisztrációját.

-   Alkalmazzon fázisos megközelítést. Kezdje a próbafelhasználók kis csoportjával, és növekményesen vegye fel a felhasználók további csoportjait, amíg el nem éri a teljes körű bevezetést.

-   Figyelje az ügyfélszolgálat terhelését és a regisztráció sikerességét az egyes ciklusokban. Hagyjon időt a sikerességi feltételek értékelésére az egyes csoportok esetében a következő csoport migrálása előtt. A próbabevezetés során ellenőrizni kell a következőket:

    -   A sikeres és sikertelen regisztrációk aránya az elvárásokon belül van-e.

    -   A felhasználók termelékenységét:

        -   A vállalati erőforrások, például a VPN, a Wi-Fi, a levelezés és a tanúsítványok működését.

        -   A telepített alkalmazások elérhetőségét.

    -   Az adatbiztonságot:

        -   A megfelelőségi jelentések készítését.

        -   A mobilalkalmazás-védelmi funkciók betartatását.

Ha elégedett a migrálás első fázisával, ismételje meg a [migrációs ciklust](migration-guide-cycle.md) a következő fázis esetében.

-   Ismételje a fázisos ciklusokat mindaddig, amíg az összes felhasználót migrálta az Intune-ba.

-   Győződjön meg arról, hogy az ügyfélszolgálat készen áll a végfelhasználók támogatására a teljes migrációs kampány során. Végezzen önkéntes migrálást, amíg meg tudja becsülni a támogatási hívások jelentette munkaterhelést.

-   Ne szabjon meg a regisztrációra vonatkozó határidőket, amíg az ügyfélszolgálata nem tudja kezelni a fennmaradó felhasználómennyiséget

> [!IMPORTANT]
> Ne állítsa be az Intune-ban és a meglévő külső MDM-megoldásban egyaránt a hozzáférés-vezérlés alkalmazását az erőforrásokhoz, például az Exchange-hez vagy a SharePoint online-hoz. Emellett az eszközök egyszerre csak az egyik megoldásban regisztrálhatók.

## <a name="next-steps"></a>További lépések

Hozzon létre egy [kommunikációs tervet](migration-guide-communication-plan.md).
