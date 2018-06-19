---
title: Használatieset-forgatókönyvek kidolgozása
titlesuffix: Microsoft Intune
description: Ez a cikk segít az Intune használati esetek, valamint alesetek azonosításában a Microsoft Intune felhőalapú implementációja esetében.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ef2030ba36e7a2c5f1a9566a2fcb94ecca465149
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/17/2018
ms.locfileid: "29961595"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>Mobileszköz-kezelési használati esetek azonosítása

A használati esetek azonosítása az Intune sikeres telepítése szempontjából fontos részét képezi a tervezési folyamatnak. A használati esetek azért hasznosak, mert lehetővé teszik a felhasználók kezelhető csoportokba szegmentálását felhasználótípus vagy -szerepkör és a felhasználói eszköz tulajdonosa (például céges vagy személyi tulajdonú) alapján.

Ebben a témakörben néhány példán keresztül segítünk abban, hogy cége könnyedén azonosíthassa az Intune használati eseteit, a cégen belüli csoportokat, valamint az egyes használati esetekhez kapcsolódó mobileszköz-platformokat.

## <a name="device-ownership"></a>Az eszközök tulajdonjoga
Első lépésként tekintse át a cégnél az Intune telepítésével elérni kívánt célokat, így könnyebben azonosíthatja a telepítés fő használati eseteit. Az Intune telepítési tervének hatókörén belül válaszoljon az alábbi kérdésekre:

-   Tervezi a céges tulajdonú eszközök támogatását?

-   Tervezi a magántulajdonban lévő eszközök (BYOD) támogatását?

Ezek nem egymást kizáró lehetőségek. A cég céljainak eléréséhez lehet, hogy az eszköztulajdon mindkét formáját támogatnia kell. Az alárendelt használati esetek segítenek tisztázni, hol kell alkalmazni a különböző eszközkezelési szabályzatokat.

### <a name="user-type-or-device-role"></a>Felhasználó típusa vagy eszköz szerepköre

Határozza meg, hogy az egyes használati esetek tartalmaznak-e alárendelt használati eseteket is. Például a cég megállapíthatja, hogy igény van egy vállalati használati eset támogatására, amely tartalmaz további, felhasználói típuson vagy eszközszerepkörön alapuló, aleseteket, például:

-   Infomunkás

-   Vezető

-   Kioszkmód

Íme néhány példa a használati esetekre és alesetekre:

| **Használati esetek** | **Használati alesetek** |
|:---:|:---:|
| Vállalati | Infomunkás |              
| Vállalati | Vezetők |           
| Vállalati | Kioszkmód |
| BYOD | Infomunkás |           
| BYOD | Vezetők |

[Letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), hogy beírja a cég használati eseteit és aleseteit.

## <a name="organizational-groups-for-your-scenarios"></a>Céges csoportok a használati eseteihez

Ezután azonosítania kell az egyes használati esetekhez és alesetekhez kapcsolódó munkahelyi csoportokat. Például:

| **Használati esetek** | **Használati alesetek** | **Munkahelyi csoportok** |
|:---:|:---:|:---:|
| Vállalati | Infomunkás | HR, Pénzügy |               
| Vállalati | Vezető | HR, Pénzügy |            
| Vállalati | Kioszkmód | Kereskedelem |
| BYOD | Infomunkás | Marketing, értékesítés |            
| BYOD | Vezető | Marketing, értékesítés |


## <a name="mobile-device-platforms-for-your-scenarios"></a>Mobileszköz-platformok a használat esetekhez

A következő lépés az egyes használati esetekhez kapcsolódó mobileszköz-platformok azonosítása. Egynél több is lehet.

A vállalati használati esetei támogathatják például az iOS és az Androidra fejlesztett Samsung Knox eszközplatformokat. A saját eszközhasználati (BYOD) szabályzata tartalmazhat támogatást további mobileszköz-platformokhoz, például Androidhoz (nem Samsung Knox) és Windows 10 Mobile-hoz. Az előző példákból kiindulva mobileszköz-platformokat társítottunk mindegyik használati esethez.

| **Használati esetek** | **Használati alesetek** | **Csoportok** | **Eszközplatformok** |   
|:---:|:---:|:---:|:---:|
| Vállalati | Infomunkás | HR, pénzügy | iOS |                                                           
| Vállalati | Vezetők | HR, Pénzügy | iOS |                                                           
| Vállalati | Kioszkmód | Kereskedelem | Android |
| BYOD | Infomunkás | Marketing, értékesítés | iOS |                                                           
| BYOD | Vezetők | Marketing, értékesítés | iOS |

## <a name="next-steps"></a>További lépések

A következő szakaszban útmutatást talál arra, hogy [hogyan azonosíthatja az egyes használati esetek követelményeit](planning-guide-requirements.md).
