---
title: Mi történik, ha törli a Windows-eszköz regisztrációját? | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6e3f61fc84458525ae2ff62887d64baea9542
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505959"
---
# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>Mi történik, ha törli a Windows-eszköz regisztrációját az Intune-ból?

Használja a lap jobb oldalán a **Cikk tartalma** szakaszban lévő hivatkozásokat, és keresse meg a használt eszköz típusára vonatkozó információkat.


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista

- Az eszköz többé nem jelenik meg a Vállalati portálon, és nem telepíthet alkalmazásokat a Vállalati portálról.

- Ha telepítette az Intune ügyfélszoftvert, a rendszer eltávolítja a számítógépről.

- Megtörténik az Intune Endpoint Protection szoftver eltávolítása a számítógépről. Ha a számítógépre másik vírusvédelmi alkalmazás is telepítve van, és az le van tiltva, az Intune Endpoint Protection eltávolítását követően lehet újra engedélyezni ezt az alkalmazást. A Vállalati portálról való eltávolítása után ellenőrizze a számítógépet.

    > [!IMPORTANT]
    > Ha nem történik meg a másik vírusvédelmi szoftver újraengedélyezése, és egyéb vírusvédelmi szoftver sincs telepítve, akkor a számítógép védtelen maradhat a vírusokkal és az egyéb kártevő szoftverekkel szemben.

- Az eszközön annak regisztrálásakor módosult beállítások (például a kamera letiltása) hatályukat veszítik.

- A számítógép többé nem kapja meg automatikusan a szoftverfrissítéseket és a vírusdefiníciós frissítéseket az Intune szolgáltatástól. Azonban a számítógép a beállításaitól függően továbbra is kaphat frissítéseket a Windows Server Update Services, a Windows Update vagy a Microsoft Update használatával.

Ezenkívül Windows 8.1 esetén:

- Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

- Egyes levelezőalkalmazások (például a Windows Mail) többé nem tudják elérni az eszközön tárolt vállalati e-maileket.

- Előfordulhat, hogy az eszközről nem tud csatlakozni a vállalati hálózatra Wi-Fi- vagy virtuális magánhálózati (VPN) kapcsolaton keresztül.

- Előfordulhat, hogy az eszközről többé nem lehet elérni egyes vállalati erőforrásokat, például fájlmegosztásokat és belső webhelyeket.

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 Mobile és Windows Phone 8.1

- A rendszer eltávolítja a Vállalati portál alkalmazást az eszközről. Ez azt jelenti, hogy az eszköz többé nem jelenik meg a Vállalati portálon, és nem telepíthet alkalmazásokat a Vállalati portál alkalmazásból vagy a Vállalati portál webhelyről.

- Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

- Az eszközön annak regisztrálásakor módosult beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat vesztik.

    > [!IMPORTANT]
    > Az egyetlen kivételt a titkosítási házirendek jelentik, amelyek továbbra is érvényben maradnak. Ha a vállalati házirend értelmében titkosítani kellett a Windows Phone rendszerű eszközt, akkor a telefon titkosításának feloldására az egyetlen lehetőség a telefon alaphelyzetbe állítása, amely a **Beállítások** menüben végezhető el.

## <a name="windows-rt-running-windows-81"></a>Windows 8.1 rendszert futtató Windows RT

- A rendszer eltávolítja a Vállalati portál alkalmazást az eszközről. Ez azt jelenti, hogy az eszköz többé nem jelenik meg a Vállalati portálon, és nem telepíthet alkalmazásokat a Vállalati portálról.

- Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

- Az eszközön annak regisztrálásakor módosult beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat vesztik.

- Előfordulhat, hogy az eszközről többé nem tud csatlakozni a vállalati hálózatra Wi-Fi- vagy virtuális magánhálózati (VPN) kapcsolaton keresztül.

- Előfordulhat, hogy az eszközről többé nem lehet elérni egyes vállalati erőforrásokat, például fájlmegosztásokat és belső webhelyeket.

- Egyes levelezőalkalmazások (például a Windows Mail) többé nem tudják elérni az eszközön tárolt vállalati e-maileket.

Windows RT-alapú eszköz eltávolításakor a következők történnek:

- A rendszer eltávolítja a Vállalati portál alkalmazást az eszközről. Ez azt jelenti, hogy az eszköz többé nem jelenik meg a Vállalati portálon, és nem telepíthet alkalmazásokat a Vállalati portálról.

- Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

- Az eszközön annak regisztrálásakor módosult beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat vesztik.

Ha kérdése van, lépjen kapcsolatba a cég informatikai támogatási szolgálatával. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
