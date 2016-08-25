---
title: "Mi történik, ha törli az eszköz regisztrációját az Intune-ból? | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
ms.reviewer: priyar
ms.suite: ems
ms.sourcegitcommit: 1244d931d1bd3db012fbcfe0bd055d1fd4f2d88a
ms.openlocfilehash: f0108b884439aac9661c9f36f85b47d80209d155


---


# Mi történik, ha törli az eszköz regisztrációját az Intune-ból?

Ha többet szeretne megtudni arról, hogy mi történik, kattintson a megfelelő eszközhöz tartozó hivatkozásra a fenti „A cikk tartalma” részben.

- [Windows 10 Mobile, 8.1, Windows 8, Windows 7, Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10, Windows 8.1 vagy Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [Windows 8.1 vagy Windows RT rendszert futtató Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   Az eszköz többé nem jelenik meg a Vállalati portálon, és nem telepíthet alkalmazásokat a Vállalati portálról.

-   Ha telepítette az Intune ügyfélszoftvert, a rendszer eltávolítja a számítógépről.

-   Megtörténik az Intune Endpoint Protection szoftver eltávolítása a számítógépről. Ha a számítógépre másik vírusvédelmi alkalmazás is van telepítve, és az le van tiltva, az Intune Endpoint Protection eltávolítását követően újra engedélyezni lehet ezt az alkalmazást. Javasoljuk, hogy a Vállalati portálról való eltávolítása után ellenőrizze a számítógépet.

    > [!IMPORTANT]
    > [!IMPORTANT] Ha nem történik meg a másik vírusvédelmi szoftver újraengedélyezése, és egyéb vírusvédelmi szoftver sincs telepítve, a számítógép védtelen maradhat a vírusokkal és az egyéb kártevő szoftverekkel szemben.

-   Az eszközön a hozzáadásakor életbe léptetett beállítások (például a kamera letiltása) hatályukat veszítik.

-   A számítógép többé nem kapja meg automatikusan a szoftverfrissítéseket és a vírusdefiníciós frissítéseket az Intune szolgáltatástól. Azonban a számítógép a beállításaitól függően továbbra is kaphat frissítéseket a Windows Server Update Services, a Windows Update vagy a Microsoft Update használatával.

Ezenkívül Windows 8.1 esetén:

-   Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

-   Egyes levelezőalkalmazások (például a Windows Mail) többé nem tudják elérni az eszközön tárolt vállalati e-maileket.

-   Előfordulhat, hogy az eszközről nem tud csatlakozni a vállalati hálózatra Wi-Fi- vagy virtuális magánhálózati (VPN) kapcsolaton keresztül.

-   Előfordulhat, hogy az eszközről többé nem lehet elérni egyes vállalati erőforrásokat, például fájlmegosztásokat és belső webhelyeket.

## Windows 10 Mobile, Windows Phone 8.1 vagy Windows Phone 8

-   A Vállalati portál alkalmazást eltávolítja az eszközről, vagyis az eszköz nem jelenik meg többé a Vállalati portálon, és nem tud telepíteni alkalmazásokat a Vállalati portál alkalmazásból vagy webhelyről.

-   Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

-   Az eszközön a hozzáadásakor életbe léptetett beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat veszítik.

    > [!IMPORTANT]
    > Az egyetlen kivételt a titkosítási házirendek jelentik, amelyek továbbra is érvényben maradnak. Ha a vállalati házirend értelmében titkosítani kellett a Windows Phone rendszerű eszközt, akkor a telefon titkosításának feloldására az egyetlen lehetőség a telefon alaphelyzetbe állítása, amely a Windows Phone **Beállítások** menüjéből végezhető el.

## Windows 8.1 vagy Windows RT rendszert futtató Windows RT

-   A Vállalati portál alkalmazást eltávolítja az eszközről, vagyis az eszköz nem jelenik meg többé a Vállalati portálon, és nem tud telepíteni alkalmazásokat a Vállalati portálról.

-   Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

-   Az eszközön a hozzáadásakor életbe léptetett beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat veszítik.

-   Előfordulhat, hogy az eszközről többé nem tud csatlakozni a vállalati hálózatra Wi-Fi- vagy virtuális magánhálózati (VPN) kapcsolaton keresztül.

-   Előfordulhat, hogy az eszközről többé nem lehet elérni egyes vállalati erőforrásokat, például fájlmegosztásokat és belső webhelyeket.

-   Egyes levelezőalkalmazások (például a Windows Mail) többé nem tudják elérni az eszközön tárolt vállalati e-maileket.

Windows RT-alapú eszköz eltávolításakor a következők történnek:

-   A Vállalati portál alkalmazást eltávolítja az eszközről, vagyis az eszköz nem jelenik meg többé a Vállalati portálon, és nem tud telepíteni alkalmazásokat a Vállalati portálról.

-   Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

-   Az eszközön a hozzáadásakor életbe léptetett beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat veszítik.

Ha kérdése van, lépjen kapcsolatba a rendszergazdával. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).

### További információ
[Windows-eszköz használata az Intune-nal](using-your-windows-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


