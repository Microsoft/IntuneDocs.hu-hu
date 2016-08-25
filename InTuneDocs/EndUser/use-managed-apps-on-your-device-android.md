---
title: "Felügyelt alkalmazások használata az eszközön | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed10a62c-b026-4ad3-ac41-641933522df2
ms.reviewer: maxles
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0bb435b87c937ea118a0794c8332b9a8f268d36e
ms.openlocfilehash: 5a25d845113ef6a3cb402923ef451fab63138979


---


# Felügyelt alkalmazások használata az eszközön

A felügyelt alkalmazások olyan alkalmazások, amelyeket a rendszergazda konfigurálhat a rajtuk keresztül elérhető vállalati adatok védelme érdekében. Amikor androidos eszközön felügyelt alkalmazásban fér hozzá vállalati adatokhoz, észreveheti, hogy az alkalmazás a várttól kissé eltérően működik. Előfordulhat például, hogy nem tudja másolni és beilleszteni a védett vállalati adatokat, vagy nem tudja menteni az adatokat bizonyos helyekre.

A különböző felügyelt alkalmazások együtt is működhetnek az eszközön annak érdekében, hogy el tudja végezni mindennapos feladatait, miközben a vállalati adatok védelméről is gondoskodnak. Ha például megnyit egy vállalati fájlt egy felügyelt alkalmazásban, és egy másik alkalmazásra van szükség a fájl megtekintéséhez, a szükséges alkalmazás automatikusan megnyílik. Ha egy szükséges alkalmazás nem érhető el, akkor előfordulhat, hogy bizonyos műveletek, például a dokumentumok vagy a felügyelt dokumentumokban található webes hivatkozások megnyitása nem végezhetők el.

Amikor felügyelt alkalmazásban fér hozzá vállalati adatokhoz, az alábbihoz hasonló üzenet jelenik meg, amely tudatja, hogy egy felügyelt alkalmazást nyitott meg.

![open-managed-apps-message](./media/managed-apps-message.png)

## Hogyan szerezhetők be a felügyelt alkalmazások?
Különböző módokon szerezhet be felügyelt alkalmazásokat:

-   Ha az eszköze regisztrálva van a Microsoft Intune-nal, akkor telepítheti az alkalmazást a Vállalati portál alkalmazásból vagy a Vállalati portál webhelyről, illetve a rendszergazda is telepítheti azt az eszközére. A regisztrációval kapcsolatos információkért lásd: [Eszköz regisztrálása az Intune-ban](enroll-your-device-in-Intune-android.md).

-   Alkalmazást telepíthet a Play Áruházból is, majd bejelentkezhet az Intune által felügyelt vállalati felhasználói fiókjával.

## Mit felügyelhet a rendszergazda az alkalmazásokban?
Itt talál néhány példát arra, hogy melyek lehetnek azok a rendszergazda által az alkalmazásokban felügyelt elemek, amelyek hatással lehetnek a vállalati adatok használatára az eszközön:

-   Adott webhelyek hozzáférése

-   Adatátvitel alkalmazások között

-   Fájlok mentése

-   Másolási és beillesztési műveletek

-   PIN-hozzáférési követelmények

-   Vállalati hitelesítő adatokkal végzett bejelentkezés

-   Biztonsági mentés létrehozásának lehetősége a felhőben

-   Képernyőfelvételek készítésének lehetősége

-   Adattitkosítási követelmények

A következők olyan általános alkalmazások, amelyeket az informatikai részlege felügyelhet:

-   Intune Managed Browser

-   Intune Image Viewer

-   Intune PDF Viewer

-   Intune AV Viewer

-   Microsoft Word, Excel, PowerPoint

Az eszközén lévő felügyelt alkalmazásokról további információért lépjen kapcsolatba az informatikai rendszergazdájával. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).


### További információ
[Android-eszköz használata az Intune-nal](using-your-android-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


