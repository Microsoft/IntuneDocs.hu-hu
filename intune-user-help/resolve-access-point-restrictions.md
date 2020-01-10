---
title: Az Intune-ban megadott hozzáférésipont-korlátozások feloldása
description: Az Intune hozzáférésipont-korlátozási szabályzatok 3 gyakori üzenetének áttekintése és feloldásuk elsajátítása
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: eeb47c072a4f34098bdebfd8766ab51b941d0bd3
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858098"
---
# <a name="resolve-access-point-restrictions"></a>Hozzáférésipont-korlátozások feloldása

A cégek korlátozhatják azokat a helyeket, ahonnan az eszközök hozzáférhetnek a vállalati adatokhoz.
Ezeknek a *hozzáférésipont-korlátozásoknak* a konfigurálásához engedélyezett hálózati helyeket adnak meg és állítanak be.  

Ha egy fel nem ismert vagy nem engedélyezett hálózathoz próbál kapcsolódni, kaphat egy vagy több üzenetet a következők közül:

* Nincsenek beállítva hozzáférésipont-korlátozások.
* Nem kapcsolódik jóváhagyott hálózathoz.
* Hiba történt, és nem lehetett kényszeríteni a hozzáférésipont-korlátozásokat.

 Az alábbi táblázatokban megtalálható mindegyik üzenet, azok jelentése, és az, hogyan érhetők el ismét a munkahelyi erőforrásokhoz.

## <a name="access-point-restrictions-not-set-up"></a>Nincsenek beállítva hozzáférésipont-korlátozások  
| Üzenet a Céges portálon | Az üzenet jelentése | Tennivalók                                                               
|------------------------|--------------------------|--------------------------|
| **A hozzáférésipont-korlátozások nincsenek beállítva – a hozzáférésipont-korlátozások aktívak, és be kell állítani őket.** | A vállalata hozzáférésipont-korlátozásokat alkalmazott az eszközön. Ez a beállítás megköveteli, hogy a Céges portál alkalmazás ellenőrizzen néhány hálózati beállítást az eszközén. | Koppintson a **Feloldás** elemre. A Céges portál alkalmazás ellenőrzi, hogy az eszköz a vállalat által engedélyezett hálózathoz kapcsolódik-e. |

## <a name="not-connected-to-an-approved-network"></a>Nem kapcsolódik jóváhagyott hálózathoz  

| Üzenet a Céges portálon | Az üzenet jelentése | Tennivalók                                                                   
|------------------------|-----------------------------------|--------------------------|
| **Az eszköz nem kapcsolódik jóváhagyott hálózathoz – Kapcsolódjon egy jóváhagyott vezeték nélküli hálózathoz.** | Egy olyan hálózathoz kapcsolódik, amely nincs munkahelyi hozzáféréshez jóváhagyva. Amíg ehhez a hálózathoz kapcsolódik, nem fogja tudni elérni a munkahelyi e-maileket, alkalmazásokat és más védett vállalati erőforrásokat. | Kapcsolódjon egy, a vállalat által jóváhagyott hálózathoz. Ez után koppintson a **Feloldás** elemre az újbóli próbálkozáshoz. |

## <a name="restrictions-couldnt-be-enforced"></a>Nem lehetett kényszeríteni a korlátozásokat  

| Üzenet a Céges portálon | Az üzenet jelentése | Tennivalók                                                                      
|------------------------|-----------------------------------|--------------------------|
| **Nem lehetett kényszeríteni a hozzáférésipont-korlátozásokat – A Céges portál hibát észlelt.** | Az Intune nem tudja megállapítani, hogy egy jóváhagyott hálózathoz kapcsolódik-e. Ez a hiba lehet gyenge hálózati kapcsolat, alacsony töltöttségű akkumulátor, akkumulátortakarékos üzemmód vagy a Céges portál hibájának következménye. | Ellenőrizze, hogy nagy-e a hálózati térerő. Kapcsolja ki a akkumulátortakarékos üzemmódot, és győződjön meg róla, hogy az akkumulátor töltöttsége legalább 30%-os. Ez után koppintson a **Feloldás** elemre az újbóli próbálkozáshoz. 

További segítségre van szüksége? Javasoljuk, hogy forduljon a cég ügyfélszolgálatához. Az elérhetőségi információt a [Céges portál webhelyén](https://portal.manage.microsoft.com/#HelpDeskDialog) találja.
