---
title: A Zimperium zIPS által talált fenyegetések elhárítása Android rendszeren
description: Útmutató az Android-eszközén észlelt biztonsági és alkalmazásfenyegetések elhárításához.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 9ffbb656-93cd-4e0b-96c0-c5038cd2cf31
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d1a0583b18d34dbf8b942cf2a31656d3d61c1600
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507775"
---
# <a name="resolve-a-threat-found-by-zimperium-zips"></a>A Zimperium zIPS által azonosított fenyegetések elhárítása

A Zimperium zIPS egy mobilfenyegetés elleni védelmi szolgáltatás, amely lehetséges fenyegetéseket azonosít Android-eszközein. A fenyegetéseket a rendszer jelenti a Céges portál alkalmazásnak, ahol megoldatlan nem megfelelőségi problémákként jelennek meg. Amíg az eszköze nem megfelelőként van azonosítva, előfordulhat hogy nem lesz lehetősége a következőkre:

* Hozzáférés a vállalati e-mailekhez
* Hozzáférés a vállalati Wi-Fi-hez
* Hozzáférés a SharePoint Online-hoz
* Vállalati fájlok szinkronizálása a OneDrive-val
* Hozzáférés a vállalati alkalmazásokhoz

Ez a cikk a Zimperium zIPS fenyegetési riasztásainak felismerését és a fenyegetések elhárításának módját ismerteti. 

## <a name="troubleshoot-virus-or-security-threat"></a>Vírus vagy biztonsági fenyegetés elhárítása  
Vírus vagy biztonsági fenyegetés észlelésekor a Zimperium zIPS vállalata hozzáférési szabályzatainak megfelelő korlátozásokat érvényesít. Vállalati hozzáférési szabályzatai megakadályozhatják, hogy hozzáférjen a munkájához szükséges hálózathoz, alkalmazásokhoz és e-mailekhez az eszközéről.  

A Zimperium zIPS párbeszédablakban hívja fel a figyelmét a hozzáférés visszaszerzéséhez szükséges teendőkre. Válassza ki a fenyegetést, és kövesse az utasításokat az alkalmazáson belüli a feloldásához.

Mivel az alkalmazás integrálva van a vállalat MDM szolgáltatójával, korlátozott hozzáférésre vonatkozó figyelmeztetés fog megjelenni a Céges portál alkalmazásban. A figyelmeztetés felszólítja, hogy a vírus vagy biztonsági fenyegetés elhárításához nyissa meg a Zimperium zIPS-t.  

  ![Példa képernyőkép a Céges portál Eszközök oldaláról, a Zimperium zIPS figyelmeztetésével.](./media/CP-lookout-virus-banner-1808.png)  

Válassza az érintett eszköz alatt megjelenő figyelmeztető szalagcímet. Megnyílik a Zimperium zIPS, és tájékoztatja Önt a fenyegetés elhárításának módjáról.  

## <a name="resolve-an-app-threat"></a>Alkalmazásfenyegetés elhárítása

Az eszközére nézve fenyegetőnek ítélt alkalmazás telepítésekor értesítést kap a Zimperium zIPS-ben. Ha a érintett alkalmazás az eszközén marad, nem fogja tudni elérni a vállalati erőforrásokat.  

A megoldáshoz jelölje ki az alkalmazást a fenyegetéseknek a Zimperium zIPS-ben megjelenő listájában. Ezután kövesse a képernyőn megjelenő utasításokat az alkalmazás eltávolításához.    

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980). 
