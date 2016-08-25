---
title: "Eszközök kivonása | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: c06f1fc1168b0dde515eaa82d15095ec4d73d1cf


---

# Eszközök kivonása az Intune felügyelete alól

Akár vállalati, akár saját eszközökről van szó, eljön a pillanat, amikor egy kezelt eszközt ki kell vonni az Intune felügyelete alól. Az eszközkivonás viszonylag egyszerű folyamat; végezhet szelektív vagy teljes törlést is.
## Adatok és alkalmazások törlése az eszközökről
Mind a szelektív, mind a teljes törlés eltávolítja az eszközt az Intune-ból a szabályzat és a Vállalati portál törlésével, vagyis az eszköz a továbbiakban nem fog rendelkezni a vállalati erőforrásokba, például a Microsoft SharePoint vagy az Office 365 szolgáltatásba, illetve a levelezőrendszerbe való bejelentkezéshez szükséges hitelesítő adatokkal.

A [szelektív törlés](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) művelet olyan alkalmazottak esetében ajánlott, akik a saját eszközüket regisztrálták az Intune-ban, mert az eszközön lévő személyes adatokra nincs hatással. Csak a vállalati adatok törlődnek.

A vállalat által birtokolt eszközök esetében a [teljes törlés](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) funkciót is használhatja, amely visszaállítja az eszköz gyári beállításait.

## A vállalati hálózati hozzáférés megvonása
Ha egy eszközt azért von ki a használatból, mert a munkavállaló kilép a vállalattól, és elmulasztja visszaadni a vállalati hardvert, [távolról is zárolhatja](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) az eszközt. Ezzel a vállalati információkkal és a vállalati hardverrel való visszaélés is elkerülhető, bár előfordulhat, hogy az eszközt le kell írni veszteségként.

Az alkalmazott Intune-felhasználói fiókjának licencét is érdemes visszavonni. Ezzel felszabadul a licenc, és hozzá lehet rendelni egy új felhasználói fiókhoz.

## Hardver kivonása
Egyes esetekben maga az eszköz éri el életciklusának végét. Ilyen esetekben egy teljes törléssel [a gyári beállítások visszaállíthatók](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md), az összes adat eltávolítható, és az eszköz el is távolítható az Intune-ból. Ezután a vállalati házirendnek megfelelően le lehet selejtezni a hardvereket.

### További információ
[Adatok védelme teljes vagy szelektív törléssel](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


