---
title: A bevezetés és az időkeretek által érintett csoportok meghatározása
titleSuffix: Microsoft Intune
description: Ennek a cikknek a segítségével könnyebben meghatározhatja, mely csoportoknál vezeti be a Microsoft Intune-t, valamint az üzembe helyezések időkeretét.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 777267f10edac5bbdbe23ceb3068d4366a8df7b7
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509947"
---
# <a name="develop-a-rollout-plan"></a>Bevezetési terv kidolgozása

A bevezetési terve azonosítja az Intune bevezetésében érintett céges csoportokat, a bevezetés időkeretét az egyes csoportoknál és a bevezetéshez használt megközelítési módokat.

## <a name="targeted-groups-and-timeframes"></a>Célcsoportok és időkeretek

Először tekintse át az Intune bevezetése által érintett célcsoportokat és azokat, amelyeket a [használati eseteket tartalmazó forgatókönyvekben](planning-guide-scenarios.md) azonosított.

Másodszor határozza meg az egyes célcsoportok időkeretét. Az egyes csoportoknak legmegfelelőbb bevezetési időkeret meghatározásához rendszerint szükség van az Intune üzembe helyezési csapat és a célcsoportok közötti megbeszélésre. Ezeken többek között a következőket szükséges megbeszélni:
* A csoport változtatási szándékát
* A felhasználók és eszközök száma
* Az eszközplatformok típusa
* Követelmények
* Földrajzi hely
* Üzleti kockázat

## <a name="rollout-phases"></a>Bevezetési fázisok
A szervezetek többnyire az informatikai részleg kisebb csoportjára irányuló kezdeti próbaüzemmel kezdik meg az Intune bevezetését. A próbaüzem később kiterjeszthető az informatikai részleg több felhasználójára, valamint más munkahelyi csoportok is bevonhatók.

### <a name="pilot"></a>Próbaüzem
A bevezetés első fázisa próbafelhasználók számára történjen. A próbafelhasználóknak meg kell érteniük, hogy ők egy új megoldás első felhasználói. El kell fogadniuk, hogy visszajelzéseket fognak adni a konfiguráció, dokumentáció és értesítések javításához, és hogy megkönnyítésék a többi felhasználó dolgát a későbbi bevezetési fázisokban. A próbafelhasználók között ne legyenek vezetők vagy VIP-ek.

A próbaüzem jó lehetőség a [kihívások](../planning-guide-deployment-goals.md) tesztelésére és a korábban összegyűjtött [követelmények](../planning-guide-requirements.md) finomítására.

Foglalja bele a [kommunikációs](../planning-guide-communication-plan.md) tervet, a [támogatási](planning-guide-support-plan.md) tervet és a [tesztelést és érvényesítést](planning-guide-test-validation.md), hogy a problémákat még akkor megoldhassa, amikor azok felhasználókra gyakorolt hatása még kicsi.

### <a name="production-rollout"></a>Éles bevezetés
A sikeres próbaüzemet követően készen áll az éles bevezetésre a cég többi csoportjánál. Néhány példa a különböző bevezetési csoportokra és fázisokra:

- **Részlegek** <br/>Bármelyik részleg lehet bevezetési fázis. Egyszerre lehet célcsoport az egész részleg. Ebben a bevezetési típusban a felhasználók minden részlegben általában ugyanolyan módon használják a mobileszközöket, és ugyanazokhoz az alkalmazásokhoz férnek hozzá. A felhasználók valószínűleg ugyanolyan szabályzattípusokkal rendelkeznek.

- **Földrajzi hely** <br/>Ebben a megközelítésben egy adott földrajzi régió minden felhasználója számára üzembe helyezhető, függetlenül attól, hogy ugyanazt a kontinenst, országot/régiót vagy ugyanazon vállalat felépítése. A több fázisú bevezetésnek ez a típusa lehetővé teszi, hogy a felhasználók meghatározott helye legyen a középpontban. Ez lehetővé teszi [körültekintőbb](#user-assisted-enrollment) megközelítési mód alkalmazását, mert az egyidejűleg üzembe helyezett Intune-helyek száma kevesebb. Mivel esély van arra, hogy különböző részlegek vagy használati esetek ugyanazon a helyen legyenek, ezért a különböző használati esetek egyidejűleg is telepíthetők.

- **Platform** <br/>Ez a típusú telepítés hasonló platformok egyidejű telepítését jelenti. Erre jó példa lehet az, hogy az első hónapban az összes iOS-eszköz, majd az összes Android-, végül az összes Windows-eszköz kerül sorra. A több fázisú üzembe helyezésnek ez a típusa leegyszerűsíti a segélyszolgálati támogatást, mert egyszerre csak egyetlen platformot kell támogatnia.

Itt egy olyan Intune bevezetési tervre található példa, amely magába foglalja a célcsoportokat és az ütemterveket:

| **Bevezetési fázis** | **Július** | **Augusztus** | **Szeptember** | **Október** |
|:---:|:---:|:---:|:---:|:---:|
| Korlátozott próbaüzem | Informatika (50 felhasználó) |  |  |  |                                                         
| Bővített próbaüzem | Informatika (200 felhasználó), informatikai vezetők (10 felhasználó) |  |  |  |                                                         
| Éles bevezetés, 1. fázis |  | Értékesítés és marketing (2000 felhasználó) |  |  |
| Éles bevezetés, 2. fázis |  |  | Kereskedelem (1000 felhasználó) |  |
| Éles bevezetés, 3. fázis |  |  |  | HR (50 felhasználó), Pénzügy (40 felhasználó), vezetők (30 felhasználó) |

[Letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), és beírhatja cégének bevezetési fázisait.
## <a name="match-rollout-groups-to-enrollment-approaches"></a>Bevezetési csoportok és regisztrációs módszerek társítása

Most, hogy meghatározta az Intune bevezetéséhez kapcsolódó célcsoportokat és ütemterveket, a következő lépésként válassza ki minden egyes csoportra vonatkozóan a legmegfelelőbb Intune-beli regisztrálási módszert. Különböző regisztrációs módszereket használhat, többek között ezeket:
* Önkiszolgáló felhasználó
* Felhasználót segítő regisztrálás
* Informatikai vásár

### <a name="user-self-service"></a>Önkiszolgáló felhasználó

Ebben az esetben a felhasználó felelős saját eszközének regisztrálásáért, rendszerint munkahelye informatikai részlegének regisztrálási utasításait követve. Ezt a módszert többnyire cégek alkalmazzák, és jobban skálázható, mint a felhasználót segítő regisztrálás.

### <a name="user-assisted-enrollment"></a>Felhasználót segítő regisztrálás

Ez másként „körültekintő” módszerként is ismert. Az IT-csoport egy tagja személyesen vagy Skype-on segít a felhasználónak a regisztrációs folyamat során. Ez a módszer rendszerint a vezetőkkel vagy olyan csoportokkal alkalmazandó, akiknek több segítségre lehet szüksége bevezetés során.

### <a name="it-tech-fair"></a>Informatikai vásár

Az Intune bevezetésének további lehetősége egy informatikai vásár megtartása. Az informatikai csoport az eseményen felállít egy regisztrálástámogatási standot, ahol a felhasználók információt kaphatnak, kérdéseket tehetnek fel és támogatásban részesülhetnek az Intune-beli regisztrálással kapcsolatban. Ez a lehetőség az informatikai csoportnak és a felhasználónak egyaránt hasznára válhat, kiváltképpen az Intune bevezetésének korai szakaszaiban.

Itt következik a fenti Intune-regisztrációs terv regisztrációs módszerekkel frissített példája:

| **Bevezetési fázis** | **Július** | **Augusztus** | **Szeptember** | **Október** |
|:---:|:---:|:---:|:---:|:---:|
| Korlátozott próbaüzem |  |  |  |  |
| Önkiszolgáló | Informatikai részleg |  |  |  |
| Bővített próbaüzem |  |  |  |  |
| Önkiszolgáló | Informatikai részleg |  |  |  |
| Körültekintő | Informatikai vezetők |  |  |  |
| Éles bevezetés, 1. fázis |  | Értékesítés, Marketing |  |  |
| Önkiszolgáló |  | Értékesítés és marketing |  |  |
| Éles bevezetés, 2. fázis |  |  | Kereskedelem |  |
| Önkiszolgáló |  |  | Kereskedelem |  |
| Éles bevezetés, 3. fázis |  |  |  | Vezetők, HR, pénzügy |
| Önkiszolgáló |  |  |  | HR, pénzügy |
| Körültekintő |  |  |  | Vezetők |

## <a name="next-steps"></a>További lépések

A következő szakaszban az [Intune bevezetési kommunikációs terv összeállításáról](../planning-guide-communication-plan.md) található információ.
