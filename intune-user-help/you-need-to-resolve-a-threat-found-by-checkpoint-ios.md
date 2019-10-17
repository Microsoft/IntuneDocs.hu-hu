---
title: SandBlast Mobile Protect által észlelt fenyegetések elhárítása iOS-en | Microsoft Docs
description: Útmutató az iOS-hez készült SandBlast Mobile Protect által talált fenyegetések elhárításához.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 5b2a69e7-cc86-4f1b-81d9-35b8b23b937b
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a5c979f19a2761d596cd48cfc7d88e003bfcb99
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72500898"
---
# <a name="resolve-a-threat-found-by-sandblast-mobile-protect"></a>A SandBlast Mobile Protect által észlelt fenyegetés elhárítása

A SandBlast Mobile Protect egy mobilfenyegetés elleni védelmi szolgáltatás, amely lehetséges fenyegetéseket azonosít és értékel ki iOS-eszközein. Ez után a Céges portál alkalmazásban megtekinthető jelentést küld a fenyegetésekről. A fenyegetések megoldatlan nem megfelelőségi problémákként jelennek meg az alkalmazásban. Amíg a fenyegetések jelen vannak, előfordulhat hogy nem lehet végrehajtani a következőket:   

* Hozzáférés a vállalati e-mailekhez
* Hozzáférés a vállalati Wi-Fi-hez
* Hozzáférés a SharePoint Online-hoz
* Vállalati fájlok szinkronizálása a OneDrive-val
* Hozzáférés a vállalati alkalmazásokhoz

Ez a cikk a SandBlast Mobile Protect fenyegetési riasztásainak felismerését, és a fenyegetések elhárításának módját ismerteti.  

## <a name="troubleshoot-virus-or-security-threat"></a>Vírus vagy biztonsági fenyegetés elhárítása  
Vírus vagy biztonsági fenyegetés észlelésekor a SandBlast Mobile Protect alkalmazás vállalata hozzáférési szabályzatainak megfelelően jár el. A hozzáférési szabályzatok megakadályozhatják, hogy hozzáférjen a munkájához szükséges hálózathoz, alkalmazásokhoz és e-mailekhez.  

![Egy SEP Mobile alkalmazás riasztási üzenetének példaképernyőképe.](./media/skycure-list-of-potential-issues-android.png)  
A SandBlast Mobile Protect párbeszédablakban hívja fel a figyelmét a hozzáférés visszaszerzéséhez szükséges teendőkre. Válassza ki a fenyegetést, és kövesse az utasításokat az alkalmazáson belüli a feloldásához.

Mivel az alkalmazás integrálva van a vállalat MDM szolgáltatójával, korlátozott hozzáférésre vonatkozó figyelmeztetés fog megjelenni a Céges portál alkalmazásban. A figyelmeztetésben utasítások találhatók a Sandblast Mobile Protect megnyitására és a vírus vagy a biztonsági fenyegetés elhárítására vonatkozóan.  

  ![A Céges portál eszközoldalának például szolgáló képernyőképe a SandBlast Mobile Protect figyelmeztetésével.](./media/CP-lookout-virus-banner-1808.png)  

## <a name="troubleshoot-an-app-threat"></a>Alkalmazásfenyegetés hibaelhárítása  

Ha egy fenyegetésként észlelt alkalmazást telepít az eszközére, akkor értesítést fog kapni a SandBlast Mobile Protectben. Ha a érintett alkalmazás az eszközén marad, nem fogja tudni elérni a vállalati erőforrásokat.  

A feloldáshoz válassza ki az alkalmazást a fenyegetések listájából a SandBlast Mobile Protectben. Ezután kövesse az alkalmazás eltávolítására vonatkozó utasításokat.  

További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához. A kapcsolatfelvételi adatait megtalálja a [Munkahelyi portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
