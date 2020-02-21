---
title: Az alkalmazás-védelmi szabályzatok konfigurálása az áttelepítés során
titleSuffix: Microsoft Intune
description: Ez a cikk az alkalmazásvédelmi szabályzatok Microsoft Intune-migráció során történő beállításához szükséges lépéseket ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183a1dc7083aa9b427df225297fb7c393939220f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515050"
---
# <a name="configure-app-protection-policies-optional"></a>Alkalmazásvédelmi szabályzatok konfigurálása (nem kötelező)


Az alkalmazásvédelmi szabályzatokkal az alábbi műveleteket végezheti el:
* Alkalmazások titkosítása
* A PIN-kód meghatározása az alkalmazás eléréséhez
* Egyes alkalmazások futtatásának letiltása feltört eszközökön, valamint számos más védelmi intézkedés.

Ha a felhasználó telefonját ellopják vagy elvész, távolról is törölhetők róla szelektíven a vállalati adatok, miközben a személyes adatok érintetlenül maradnak.

Az alkalmazásvédelmi szabályzatok alkalmazásszinten működnek, így nem igényelnek eszközregisztrációt, egyaránt használhatók az Intune-ba regisztrált és nem regisztrált eszközökkel, sőt, akár külső MDM-szolgáltatónál regisztrált eszközökkel is.

## <a name="app-protection-policies-with-lob-apps"></a>Alkalmazásvédelmi szabályzatok üzletági alkalmazásokkal

A Mobile App Protection-szabályzatokat az üzletági (LOB) alkalmazásokra is kiterjesztheti az iOS/iPadOS és az Android platformhoz készült [Microsoft Intune app SDK](../developer/app-sdk-get-started.md) vagy a Microsoft Intune alkalmazás-burkoló eszköz használatával. További információ: [iOS-hez készült alkalmazásburkoló eszköz](../developer/app-wrapper-prepare-ios.md) és [Androidhoz készült alkalmazásburkoló eszköz](./../developer/app-wrapper-prepare-android.md). Lásd még: [Üzletági alkalmazások előkészítése alkalmazásvédelemre](../developer/apps-prepare-mobile-application-management.md).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Hogyan segítenek a migráció során az alkalmazásvédelmi szabályzatok?

A migráció során az eszközöket el kell távolítani a korábbi MDM-szolgáltatóból, és regisztrálni kell őket az Intune-ba. Ezt előre célszerű megszervezni: kérje meg a felhasználókat, hogy lépjenek ki a régi MDM-szolgáltatótól, és rögtön regisztráljanak is az Intune-ba. Előfordulhatnak azonban olyan felhasználók a migráció során, akik késlekednek a regisztrációval, így eszközeiket egyik MDM-szolgáltató sem felügyeli.

Ebben az időszakban a szervezet jobban ki van téve az eszközlopás és a vállalati adatvesztés veszélyének, ha a céges adatokhoz való hozzáférés továbbra is engedélyezve van, illetve a felhasználói produktivitás csökkenésének, ha a céges adatokhoz való hozzáférés le van tiltva.

Az Intune a migráció során is képes vállalati adatvédelmi intézkedésekre, így a céges adatok az eszközszintű felügyelet hiányában sem maradnak teljesen védtelenek.

A régi MDM-szolgáltatóban a feltételes hozzáférés letiltásával a felhasználók továbbra is hatékonyan dolgozhatnak az Intune-ban.

## <a name="task-list-for-app-protection-policies"></a>Feladatlista az alkalmazásvédelmi szabályzatokhoz

- [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](~/apps/app-protection-policies.md)

## <a name="next-steps"></a>További lépések

[Speciális áttelepítési megfontolások](migration-guide-considerations.md)
