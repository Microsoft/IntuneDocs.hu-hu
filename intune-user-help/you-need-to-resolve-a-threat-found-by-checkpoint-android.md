---
title: A SandBlast Mobile Protect Androidhoz által észlelt fenyegetések elhárítása | Microsoft Docs
description: Útmutató a SandBlast Mobile Protect Androidhoz által talált fenyegetések elhárításához.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 449c34ec-2d94-4c7f-8691-a5200efee3cb
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.openlocfilehash: be3f728a4f2764a0c2494686c943cdfb43b32bd2
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/29/2018
ms.locfileid: "43147555"
---
# <a name="resolve-a-threat-found-by-sandblast-mobile-protect"></a>A SandBlast Mobile Protect által észlelt fenyegetés elhárítása

A SandBlast Mobile Protect egy mobilfenyegetés elleni védelmi szolgáltatás, amely lehetséges fenyegetéseket azonosít az Android-eszközein. Jelentést készít a fenyegetésekről, amelyeket megtekinthet a Céges portál alkalmazásban. A fenyegetések megoldatlan nem megfelelőségi problémákként jelennek meg az alkalmazásban. Amíg a fenyegetések jelen vannak, előfordulhat hogy nem lehet végrehajtani a következőket:   

* Hozzáférés a vállalati e-mailekhez
* Hozzáférés a vállalati Wi-Fi-hez
* Hozzáférés a SharePoint Online-hoz
* Vállalati fájlok szinkronizálása a OneDrive-val
* Hozzáférés a vállalati alkalmazásokhoz

Ez a cikk a SandBlast Mobile Protect fenyegetési riasztásainak felismerését, és a fenyegetések elhárításának módját ismerteti.  

## <a name="troubleshoot-virus-or-security-threat"></a>Vírus vagy biztonsági fenyegetés elhárítása  
Vírus vagy biztonsági fenyegetés észlelésekor a SandBlast Mobile Protect alkalmazás vállalata hozzáférési szabályzatainak megfelelően jár el. A vállalat hozzáférési szabályzatai megakadályozhatják, hogy hozzáférjen a munkájához szükséges hálózathoz, alkalmazásokhoz és e-mailekhez.  

![Egy SEP Mobile alkalmazás riasztási üzenetének példaképernyőképe.](./media/skycure-list-of-potential-issues-android.png)  

Azonban a SandBlast Mobile Protect egy párbeszédablakban a hozzáférés visszaszerzéséhez szükséges teendőkre is felhívja a figyelmét. Válassza ki a fenyegetést, és kövesse az utasításokat az alkalmazáson belüli a feloldásához.

Mivel az alkalmazás integrálva van a vállalat MDM szolgáltatójával, korlátozott hozzáférésre vonatkozó figyelmeztetés fog megjelenni a Céges portál alkalmazásban. A figyelmeztetésben utasítások találhatók a Sandblast Mobile Protect megnyitására és a vírus vagy a biztonsági fenyegetés elhárítására vonatkozóan.

  ![A Céges portál példaképernyőképe a SandBlast Mobile Protect figyelmeztetésével.](./media/CP-lookout-virus-banner-1808.png)  

## <a name="troubleshoot-an-app-threat"></a>Alkalmazásfenyegetés hibaelhárítása  

Ha egy fenyegetésként észlelt alkalmazást telepít az eszközére, akkor értesítést fog kapni a SandBlast Mobile Protectben. Ha a érintett alkalmazás az eszközén marad, nem fogja tudni elérni a vállalati erőforrásokat.  

A feloldáshoz válassza ki az alkalmazást a fenyegetések listájából a SandBlast Mobile Protectben. Ez után kövesse az utasításokat az alkalmazás eltávolításához.     

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
