---
title: IOS-eszköz eltávolítása az Intune-ból | Microsoft Docs
description: Egy iOS-eszköz az Intune-ból való eltávolítását ismerteti
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: bd5384945158f3d0ef3035eaf9bc2f8375d8b153
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859015"
---
# <a name="remove-your-ios-device-from-intune"></a>IOS-eszköz eltávolítása az Intune-ból

Amikor eltávolít egy iOS-eszközt az Intune-ból, az nem fog tudni többé hozzáférni a vállalati erőforrásokhoz, és kikerül az Intune felügyelete alól.


## <a name="removing-the-device-from-my-devices"></a>Az eszköz eltávolítása az Eszközeim területről

Ha az eszközt el szeretné távolítani az Intune-ból, kövesse az alábbi lépéseket, vagy tekintse meg ezt a videót:


1. A Céges portál alkalmazásban koppintson az **Eszközök** elemre, majd válassza ki azt az eszközt, amelynek regisztrációját törölni szeretné. Ha csak egy eszközzel rendelkezik, az **Eszközök** elemre koppintáskor követlenül az eszközadatok képernyőjére lép.

2. Az **ÁTNEVEZÉS** lehetőség mellet kattintson a három pontra, majd az **Eszköz eltávolítása** > **Eltávolítás** lehetőségre.  

    |![Képernyőkép a Céges portál alkalmazás Eszközök képernyőjéről, az Eltávolítás gombra kattintás után megjelenő lehetőségekkel. Megjelenített gombok: „Eszköz eltávolítása”, „Gyári beállítások visszaállítása”, valamint „Mégse”.](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![Képernyőkép a Céges portál alkalmazás Eszközök képernyőjéről, az Eszköz eltávolítása gombra kattintás után megjelenő lehetőségekkel. Megjelenített gombok: pirosan kiemelt „Eltávolítás” gomb, valamint kékkel kiemelt „További információ” és „Mégse” gomb.](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


    Az eszköz regisztrációjának Intune-ból való törlésekor a következők történnek:

    - Az eszköz többé nem jelenik meg a vállalati portálon.

    - Többé nem telepíthet alkalmazásokat a vállalati portálról.

    - Az eszközön annak regisztrálásakor módosult beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat vesztik.

    - Előfordulhat, hogy az eszközről többé nem lehet elérni egyes vállalati erőforrásokat, például fájlmegosztásokat és belső webhelyeket.

    - Az eszközön többé nem használhatók a vállalati alkalmazások és adatok.

    - Előfordulhat, hogy Wi-Fi- vagy virtuális magánhálózati (VPN-) kapcsolaton keresztül nem tud többé a vállalati hálózathoz csatlakozni.

    - A rendszer eltávolítja a vállalati e-mail profilokat az eszközről.

    - A csak levelezéshez konfigurált eszközök nem fognak megjelenni a Vállalati portál alkalmazásban és a vállalati portál webhelyén.

    - Törlődnek az alkalmazások. Törlődnek a vállalati alkalmazásadatok.

## <a name="removing-data-collected-by-the-company-portal-app"></a>A Céges portál alkalmazás által gyűjtött adatok eltávolítása

A Céges portál az eszközön három helyen tárolja a helyi adatokat.

- **Információs naplók**: a Microsoft által gyűjtött szabványos alkalmazástevékenység-adatok, például az alkalmazás megnyitási időtartama vagy az összeomlási adatok automatikusan törlődnek az eszköz a Céges portálból való eltávolításakor.

- **Apple-elemzések**: az Apple által gyűjtött szabványos alkalmazás-összeomlási adatok. Ezek az adatok csak az eszköz gyári alaphelyzetbe való visszaállításával távolíthatók el. Ez a művelet minden személyes adatot töröl az eszközről. Ehhez válassza a **Beállítások** > **Általános** > **Alaphelyzetbe állítás** > **Összes tartalom, beállítás törlése** lehetőséget.

- **Kulcskarika**: az eszköz a kulcskarikán tárolja a jelszavakat és egyéb bejelentkezéshez szükséges adatokat. A Microsoft-alkalmazások megosztják az eszközön található más Microsoft-alkalmazásokkal a bejelentkezési adatait, így például a Microsoft Outlookkal és a Microsoft Authenticatorrel. Az Apple-elemzésekhez hasonlóan ezeket az adatokat csak az eszköz gyári alaphelyzetbe való visszaállításával távolíthatja el. Ez a művelet minden személyes adatot töröl az eszközről. Ehhez válassza a **Beállítások** > **Általános** > **Alaphelyzetbe állítás** > **Összes tartalom, beállítás törlése** lehetőséget.


További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
