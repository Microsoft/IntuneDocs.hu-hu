---
title: Android-felhasználói alkalmazások letöltése
description: Módszerek az Android-alkalmazások elérhetővé tételére végfelhasználók számára
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 960c440372613fed2c92ce00c604d97e1f122e8f
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71239820"
---
# <a name="how-your-android-users-get-their-apps"></a>Android-felhasználói alkalmazások letöltése

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Ebből a cikkből megtudhatja, hogyan és hol érheti el az Android-végfelhasználók a Microsoft Intune által terjesztett alkalmazásokat. Az ebben foglalt információk a különböző típusú eszközök (androidos natív vagy Samsung Knox Standard-eszközök) esetén eltérőek lehetnek.

## <a name="native-non-samsung-knox-standard-android-devices"></a>Natív (Samsung Knox Standard) androidos eszközök

| Alkalmazás típusa | Üzletági (LOB) alkalmazások | Play Áruház-alkalmazások  |
| ------------- |-------------| -----|
| Nem kötelező alkalmazások      | A felhasználók a **telepítés** elemre koppintanak a Vállalati portálon. Megjelenik egy értesítés, amelyre koppintva a felhasználók elindítják a telepítést. A telepítés befejezését követően megjelenik az értesítés. | A felhasználók koppintanak az alkalmazásra a Céges portál, és a Play Áruház egy alkalmazás lapjára kerülnek. Itt kezdődik a telepítés.|
| Required apps      | A felhasználók értesítéseket jelenítenek meg, amelyeket nem lehet elvetni, ami azt jelzi, hogy telepíteniük kell egy alkalmazást. A felhasználók az értesítésre koppintva elindíthatják a telepítést. A telepítés befejezését követően megjelenik az értesítés.    | A felhasználók értesítéseket jelenítenek meg, amelyeket nem lehet elvetni, ami azt jelzi, hogy telepíteniük kell egy alkalmazást. A felhasználók koppintanak az értesítésre, és a Play Áruház egy alkalmazás lapjára kerülnek. Itt kezdődik a telepítés. A telepítés befejezését követően megjelenik az értesítés. |

A végfelhasználók számára engedélyezni kell az ismeretlen forrásból történő telepítést [LOB-alkalmazások](lob-apps-android.md)telepítéséhez. Ez a beállítás általában két különböző helyen található:

* **Android 7.1.2 és alacsonyabb**: **Beállítások** > biztonságiismeretlen > **források**
* **Android 8,0 és újabb**verziók: **Beállítások** >  >  > alkalmazások & értesítések speciális alkalmazás-hozzáférés az ismeretlen alkalmazások telepítésecégesportál > engedélyezés ebből a forrásból > 

Ebben az esetben a Céges portál értesíti a felhasználót, és közvetlenül végigvezeti a megfelelő beállítás megadásán. 

## <a name="samsung-knox-standard-android-devices"></a>Androidos Samsung Knox Standard-eszközök

| Alkalmazás típusa | Üzletági (LOB) alkalmazások | Play Áruház-alkalmazások  |
| ------------- |-------------| -----|
| Nem kötelező alkalmazások      | A felhasználók a **telepítés** elemre koppintanak a Vállalati portálon. Az alkalmazás további felhasználói beavatkozás nélkül telepítve lesz. | A felhasználók koppintanak az alkalmazásra a Céges portál, és a Play Áruház egy alkalmazás lapjára kerülnek. Itt kezdődik a telepítés.|
| Required apps      | Az alkalmazás felhasználói beavatkozás nélkül telepítve lesz.    | A felhasználók értesítéseket jelenítenek meg, amelyeket nem lehet elvetni, ami azt jelzi, hogy telepíteniük kell egy alkalmazást. A felhasználók koppintanak az értesítésre, és a Play Áruház egy alkalmazás lapjára kerülnek. Itt kezdődik a telepítés. A telepítés befejezését követően megjelenik az értesítés. |

Az alkalmazások az alább leírtak szerint kezelhetők vagy nem kezelhetők. Az alkalmazások kezeltként való beállítása minden típusú androidos eszközön azonos.

**Felügyelt alkalmazások** – ezek az alkalmazások szabályzatokkal kezelhetők. Ezeket az Intune "becsomagolta" vagy az Intune app SDK-val készítettük. Ezek az alkalmazások az Intune-nal kezelhetők, és alkalmazás-házirendekkel felügyelhetők.

Nem **felügyelt alkalmazások** – ezek az alkalmazások nem kezelhetők a szabályzatok segítségével. Ezeket nem az Intune csomagolta be, vagy nem tartalmazzák az Intune app SDK-t. Az alkalmazás-házirendek nem alkalmazhatók ezekre az alkalmazásokra.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Zebra-eszközök a zebra Mobility Extensions bővítménnyel

Az Intune a zebra Mobility Extensions (MX) eszközkészlet használatával csendesen telepíti az alkalmazásokat az eszköz rendszergazdája által kezelt Zebra-eszközökön. Ez a funkció lehetővé teszi, hogy felhasználói beavatkozás nélkül telepítsen és frissítsen alkalmazásokat a zebra-eszközökön. Ha az eszközön található MX-verzió 4,2-es vagy régebbi, akkor az alkalmazások csendesen nincsenek telepítve. További információ: a [teljes MX szolgáltatás mátrixa](http://techdocs.zebra.com/mx/compatibility/) a zebra webhelyén.

A zebra-eszközökre telepített ÜZLETÁGI alkalmazásokat az eszköz nyilvános mappájából kell telepíteni. Előfordulhat, hogy az. apk alkalmazáscsomag elérhetővé válik más alkalmazások és szolgáltatások számára is, amelyek hozzáférhetnek a nyilvános tárhelyhez az eszközön. Ez a hozzáférés általában egy kis ablak az alkalmazás letöltésének befejezése és a telepítés elején. Ez az ablak engedélyezheti az időzítési támadást. Egy. apk-csomag például megváltoztatható ebben az ablakban. Az Intune minimálisra csökkentheti azt az időtartamot, ameddig az. apk a nyilvános tárolóban költ, és nem engedélyezi az aláíratlan alkalmazások telepítését. A biztonsági kockázat minimalizálásához győződjön meg arról, hogy a feltöltött. apk fájlok nem tartalmaznak bizalmas adatokat.

## <a name="see-also"></a>Lásd még:

[Alkalmazások hozzáadása a Microsoft Intune-nal](apps-add.md)

[iOS-felhasználói alkalmazások letöltése](end-user-apps-ios.md)

[Windows-felhasználói alkalmazások letöltése](end-user-apps-windows.md)
