---
title: Mobile Threat Defense (MTD) alkalmazás-védelmi szabályzat létrehozása az Intune-nal
titleSuffix: Microsoft Intune
description: Hozzon létre egy Mobile Threat Defense-(MTD-) alkalmazás-védelmi szabályzatot Microsoft Intuneokkal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 900858d9c437f2d2662260ca62534a987446d2b2
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782119"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Mobile Threat Defense-alkalmazás védelmi szabályzatának létrehozása az Intune-nal

Az Intune és a Mobile Threat Defense (MTD) segít a fenyegetések észlelésében és a mobileszközök kockázatának felmérésében. Létrehozhat egy Intune app Protection-szabályzatot, amely felméri a kockázatot annak megállapítására, hogy az eszköz hozzáférhet-e a vállalati adatszolgáltatásokhoz.

> [!NOTE]
> Ez a cikk az alkalmazás-védelmi házirendeket támogató összes Mobile Threat Defense-partnerre vonatkozik:
>
> - Jobb mobil (Android, iOS/iPadOS)
> - Zimperium (Android, iOS/iPadOS)
> - Lookout for Work (Android, iOS/iPadOS).

## <a name="before-you-begin"></a>Előkészületek

Az MTD beállítása során az MTD-partnerkonzolon már létrehozott egy szabályzatot, amely a fenyegetéseket magas, közepes és alacsony szintű csoportba sorolja. Most be kell állítania a Mobile Threat Defense szintjét az Intune app Protection-szabályzatban.

Az alkalmazás-védelmi szabályzat MTD való használatának előfeltételei:

- MTD-integráció beállítása az Intune-nal. Ezen integráció nélkül a MTD-alkalmazás védelmi szabályzata nem lesz hatással.

## <a name="to-create-an-mtd-app-protection-policy"></a>MTD-szabályzat létrehozása

Az [iOS/iPadOS vagy Android rendszerhez készült alkalmazás-védelmi szabályzat létrehozásához](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps)kövesse az alábbi információkat, valamint az *alkalmazások*, a *feltételes indítás*és a *hozzárendelés* lapokon:

- **Alkalmazások**: válassza ki azokat az alkalmazásokat, amelyeket az alkalmazás-védelmi szabályzatok alapján szeretne megcélozni. A szolgáltatáskészlet esetében ezek az alkalmazások le vannak tiltva, vagy szelektíven törlődnek a kiválasztott Mobile Threat Defense-gyártótól származó eszköz kockázati értékelése alapján.
- **Feltételes indítás**: az *eszköz feltételei*alatt válassza a legördülő listát a **maximálisan engedélyezett veszélyforrások szintjének**kiválasztásához.

  A veszélyforrások szintjének **értékének**beállításai:

  - **Védett**: Ez a szint a legbiztonságosabb. Az eszköz nem tud hozzáférni a vállalati erőforrásokhoz, és így továbbra is elérhető. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű veszélyforrások állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt veszélyforrások alacsony vagy közepes szintűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.
  - **Magas**: Ez a szint a legkevésbé biztonságos, és lehetővé teszi az összes veszélyforrást a Mobile Threat Defense használatával jelentéskészítési célokra. Ennek a beállításnak a megadása esetén az eszközökön aktiválni kell az MTD alkalmazást.

  A **művelet**lehetőségei:

  - **Fájlhozzáférés**
  - **Adatok törlése**

- **Hozzárendelések**: rendelje hozzá a szabályzatot a felhasználók csoportjaihoz.  A csoport tagjai által használt eszközök az Intune app Protection használatával értékelik a vállalati adatelérést a megcélozott alkalmazásokban.

## <a name="next-steps"></a>További lépések

- További tudnivalók a [Mobile Threat Defense](~/protect/mobile-threat-defense.md) szolgáltatásról Microsoft Intune.
