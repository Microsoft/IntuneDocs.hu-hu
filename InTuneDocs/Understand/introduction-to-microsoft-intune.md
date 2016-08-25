---
title: "A Microsoft Intune bemutatása | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1bdcfa71aab0918fba1f59bd0782fc63eef6994e
ms.openlocfilehash: da9db0b3961cbbd53fc2b7aa7704fa31c8c78718


---

# Az Intune bemutatása
A Microsoft Intune a Microsoft Nagyvállalati mobilitási csomag (Enterprise Mobility Suite, EMS) „felügyeleti szerve”. A nagyvállalati mobilitás kulcsa, hogy az alkalmazottak minden eszközükön képesek legyenek hatékonyan dolgozni, miközben a szervezeti adatok védelmet élveznek.  

Az EMS a nagyvállalati mobilitás teljes, integrált csomagja, amelynek részét alkotják az irodai alkalmazások, az identitáskezelés, a hozzáférés-vezérlés, a felügyelet és az adatvédelem. Az EMS a lehető legjobb módszert kínálja a mobilitási megoldásoknak a szervezeten belüli telepítésére és felügyeletére.  

![A nagyvállalati mobilitást átfogóan bemutató kép](..\media\em-vision.png)

Az Intune lehetőséget nyújt mobileszközök és mobilalkalmazások felügyeletére. Az Intune szorosan integrálva van az Azure Active Directoryval (AD) az identitás- és hozzáférés-vezérlés érdekében, valamint az Azure Rights Managementtel (RMS) az adatvédelem érdekében.  

Néhány gyakori üzleti probléma, amelyek megoldásában segít az Intune:

* A meglévő helyszíni e-mail- és együttműködési infrastruktúra védelmének biztosítása úgy, hogy a rendszer az interneten keresztül elérhető legyen a mobileszközök és az alkalmazások számára
* A meglévő Office 365-infrastruktúra védelmének biztosítása úgy, hogy a rendszer az interneten keresztül elérhető legyen a mobileszközök és az alkalmazások számára
* Annak lehetővé tétele, hogy a szervezet mobiltelefonokkal láthassa el az alkalmazottait
* Annak lehetővé tétele, hogy a szervezet korlátozottan alkalmazható „megosztott eszközöket” biztosíthasson az adminisztratív munkatársak számára
* Annak lehetővé tétele, hogy a szervezet biztonságos stratégiát vezessen be a „saját eszközök használatára” (BYOD) a személyes eszközökre vonatkozóan
* Annak lehetővé tétele, hogy a szervezet megteremtse az alkalmazottak számára az Office 365 olyan eszközökkel és alkalmazásokkal történő elérésének feltételeit, amelyek nem állnak a vállalat ellenőrzése alatt, például egy szakvásár előcsarnokában elhelyezett kioszkkal

Néhány példa az Intune legfontosabb eszközeire:
* **Mobileszköz-felügyeleti (MDM)**: lehetőség az eszközöknek az Intune-ban történő regisztrálására, így az adott eszközök kiépíthetők, konfigurálhatók, megfigyelhetők, illetve műveletek is végezhetők rajtuk, például törölhető a tartalmuk.
* **Mobilalkalmazás-kezelés (MAM)**: lehetőség a felhasználók mobilalkalmazásainak közzétételére, leküldésére, konfigurálására, védelmére, figyelésére és frissítésére.
* **Mobilalkalmazás-biztonság**: a mobilalkalmazások felügyeletének részeként az Intune a személyes adatoknak a vállalati adatokról történő leválasztásának és a vállalati adatok szelektív törlésének lehetőségével támogatja a mobiladatok védelmét.

A fenti gyakori helyzetek ezeknek az eszközöknek a különböző kombinációkban történő használatával kezelhetők. Például a megosztott eszközzel kapcsolatos helyzetek erősen támaszkodnak az MDM használatára. A BYOD-helyzetek általában a MAM használatára támaszkodnak. A vállalati telefonos helyzetek pedig mindkettőre építenek. Szinte minden helyzet támaszkodik a mobilalkalmazás-biztonságra.

Ebben a dokumentációban elmagyarázzuk, hogy az Intune által biztosított eszközök hogyan használhatók az üzleti helyzetek feltételeinek megteremtésére.  Azt is ismertetjük, hogy ezek az eszközök hogyan használhatók az Office 365-tel, az Azure AD-vel, az Azure RMS-sel és a Microsoft mobilitási csomag többi részével. Ez segít a technológia gyakori használati módszereinek és a környezet számára előnyös hatásainak, valamint az alkalmazásukhoz szükséges eljárásoknak az átfogó megismerésében. A technológia maga igen rugalmas, és az itt leírtakon túlmutató összes helyzethez hozzáigazítható.

### További lépések
* Tájékozódjon az [Intune gyakori használati módjairól](common-ways-to-use-intune.md).
* Ismerkedjen meg a termékkel egy [30 napos Intune-próbaverzió](get-started-with-a-30-day-trial-of-microsoft-intune.md) révén.
* Mélyedjen el az Intune [műszaki követelményeiben és képességeiben](/intune/get-started/what-to-know-before-you-start-microsoft-intune).



<!--HONumber=Jun16_HO4-->


