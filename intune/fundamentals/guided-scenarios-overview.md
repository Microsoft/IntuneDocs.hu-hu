---
title: Az interaktív forgatókönyvek áttekintése
titleSuffix: Microsoft Intune
description: Ismerkedjen meg a Microsoft 365 Eszközkezelő portálon elérhető Intune-beli forgatókönyvekkel.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 460cabead711e6fa4559bcec39e556448cdf2237
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635367"
---
# <a name="intune-guided-scenarios-overview"></a>Az Intune interaktív forgatókönyvei – áttekintés 

Az interaktív forgatókönyvek egy teljes körű használati esethez igazított lépések testreszabott sorozata. A gyakori forgatókönyvek a szervezeten belüli rendszergazda, felhasználó vagy eszköz szerepkörén alapulnak. Ezek a szerepkörök általában gondosan előkészített profilok, beállítások, alkalmazások és biztonsági vezérlők gyűjteményét igénylik, hogy a lehető legjobb felhasználói élményt és biztonságot nyújtsanak.    

Ha nem ismeri az adott Intune-forgatókönyv megvalósításához szükséges összes lépést és erőforrást, akkor a kiindulási pontként az interaktív forgatókönyvek is használhatók. Az irányított forgatókönyv automatikusan összeállítja a szabályzatokat, az alkalmazásokat, a hozzárendeléseket és az egyéb felügyeleti konfigurációkat. Emellett az irányított forgatókönyvek szándékosan kihagyhatnak bizonyos, nem alkalmazható vagy nem gyakori beállításokat az adott forgatókönyv esetében. 

Az interaktív forgatókönyvek nem az Intune normál munkafolyamatainak eltérő felügyeleti területét jelentik. Ezek a munkafolyamatok az Intune meglévő munkafolyamataihoz, profilokhoz, alkalmazásokhoz és házirendekhez való együttes használatra készültek. Az interaktív forgatókönyvek elvégzése során a forgatókönyv jövőbeli kezelésének a szabályzatok, az alkalmazások és a profilok meglévő menüiben kell megvalósulnia. Egy irányított forgatókönyv nem ment "irányított forgatókönyv" típusú erőforrástípust, vagy nyomon követheti az erőforrások jövőbeli változásait. Minden irányított forgatókönyv által létrehozott erőforrás a megfelelő munkaterhelésen fog megjelenni. Az összes lehetőség, még az interaktív forgatókönyvben kihagyott beállítások is elérhetők lesznek a meglévő menükben való szerkesztéshez.  

## <a name="types-of-guided-scenarios"></a>Az interaktív forgatókönyvek típusai 

Az egyszerűség kedvéért minden irányított forgatókönyv kihagyja az összetett hatókörű szolgáltatásokat, például a hatókör címkéit <link>, a kizárási csoportokat és a virtuális csoport hozzárendeléseit <link>. Az interaktív forgatókönyvek által létrehozott összes erőforrás örökli a rendszergazda minden hatókör-címkéjét, amely befejezi a forgatókönyvet. Bizonyos forgatókönyvek a közös beállítások bizonyos szintjének megfelelő testreszabási lehetőségeket biztosítanak a szorosan kapcsolódó forgatókönyvek lefedéséhez. Ezek a forgatókönyvek csak a csak befoglalási csoportokhoz tartozó csoportok hozzárendelését támogatják. Más irányított forgatókönyvek esetén a teljes forgatókönyv egy egységes felhasználói élményt garantál azáltal, hogy nincs testreszabás, és automatikusan új csoportot hoz létre az összes hozzárendelés fogadásához. Miután az interaktív forgatókönyv befejeződik, a kifinomultabb hozzárendeléseket ingyenesen használhatja a meglévő szabályzatok, az alkalmazások és a profilok munkaterhelése révén.  

A következő forgatókönyvek vezérlik: 
- A Microsoft Edge for Mobile üzembe helyezése 
- Felhőalapú felügyelt számítógép kipróbálása
- Biztonságos Microsoft Office mobilhoz 

## <a name="guided-scenario-functionality"></a>Interaktív forgatókönyv funkció 

Az interaktív forgatókönyvek konkrét funkciókat kínálnak. Az alábbi részletekből megtudhatja, mit tehet, és mit nem tehet meg egy irányított forgatókönyv követése közben.

### <a name="launching"></a>Indít  

Az **[Eszközkezelő portálról](https://devicemanagement.microsoft.com)** elérhető minden interaktív forgatókönyv > **hibaelhárítás + támogatás** > **interaktív forgatókönyvek**. 

Az interaktív forgatókönyv a forgatókönyv célját és a telepítés befejezéséhez szükséges előfeltételeket ismerteti. Ekkor a rendszer ellenőrzi a rendszergazdai jogosultságokat annak ellenőrzéséhez, hogy minden szükséges jogosultsággal rendelkezik-e a forgatókönyv végrehajtásához.  

Az összes előfeltétel-ellenőrzés után a forgatókönyv megfelelő beállításokat biztosít a testreszabáshoz. Az interaktív forgatókönyvek célja, hogy csak a minimális számú beállításhoz, a nem gyakori vagy a speciális beállításokhoz, illetve a különleges körülményekhez ne kelljen beírni a szükséges adatokat. Minden olyan interaktív forgatókönyv, amely további részleteket tartalmaz, a dokumentációra hivatkozik. 

Az összes kötelező beállítás megadása után az interaktív forgatókönyv a megadott beállítások összegzését és a forgatókönyv által igényelt erőforrásokat mutatja be. Ezen a ponton semmi nem lett mentve, kivéve, ha explicit módon feljegyezték.

A következő lépés a forgatókönyv üzembe helyezése. A forgatókönyvek üzembe helyezése létrehozza és menti az összes szükséges erőforrást és a kiválasztott beállításokat. A központi telepítés befejezéséhez szükséges idő forgatókönyv szerint változik. Az üzembe helyezés befejezését követően az interaktív forgatókönyv megjeleníti a létrehozott erőforrások listáját, amely az egyes erőforrások felügyeleti nézetére mutató hivatkozásokat, az erőforrás normál számítási feladatait és a dokumentációt tartalmazza. 

> [!IMPORTANT]
> Az interaktív forgatókönyv végén bemutatott lista nem lesz mentve, és csak az interaktív forgatókönyv megnyitásakor látható.  
Ha hiba történt a forgatókönyv telepítésekor, a rendszer minden módosítást visszaállít. 

### <a name="editing"></a>Szerkesztés 

A meglévő erőforrások szerkesztéséhez nem használhatók irányított forgatókönyvek. A létrehozást követően az összes erőforrást, csoportot és hozzárendelést a meglévő munkaterhelések alapján kell szerkeszteni.

### <a name="monitoring"></a>Figyelés 

Az irányított forgatókönyvek nem használhatók a meglévő erőforrások figyelésére a kezdeti létrehozási folyamaton kívül. A létrehozást követően az összes erőforrást, csoportot és hozzárendelést a meglévő munkaterhelések alapján kell figyelni. 

### <a name="retiring"></a>Visszavonult 

Az irányított forgatókönyvek nem használhatók meglévő erőforrások kivonására a kezdeti telepítés során felmerülő hiba miatt. A létrehozást követően az összes erőforrást, csoportot és hozzárendelést ki kell vonni a meglévő munkaterhelések használatával. 

### <a name="updating"></a>Frissítése

A technológia fejlődése során az Intune időről időre frissít egy interaktív forgatókönyvet, hogy javítsa a felhasználói élményt, a biztonságot vagy a forgatókönyv egyéb aspektusait. Ez a frissítés csak az irányított forgatókönyv által végrehajtott új központi telepítéseket érinti. Az Intune nem frissíti az interaktív forgatókönyv által korábban létrehozott meglévő erőforrásokat, hogy azok megfeleljenek az új ajánlott eljárásoknak vagy javaslatoknak.  

## <a name="next-steps"></a>További lépések

A Microsoft Intune gyors futtatásához lépjen az Intune által vezérelt forgatókönyvek között. Ha még nem ismeri az Intune-t, az [ingyenes próbaidőszakot](free-trial-sign-up.md)követve állítsa be az Intune-bérlőt.
