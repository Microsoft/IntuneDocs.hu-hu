---
title: Úgy tűnik, hogy az androidos eszköze titkosított | Microsoft Docs
description: Titkosítási állapot feloldása Céges portál és Microsoft Intune alkalmazásban
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: af1c7d1f9d8236fd95413317acefbe8887d90f47
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507664"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>Az eszköz titkosítva van, de az alkalmazások másként

Ha Céges portál vagy a Microsoft Intune alkalmazás azt mondja, hogy az eszköz nincs titkosítva, de biztos benne, hogy az, próbálja meg a cikkben ismertetett lépéseket.  

## <a name="add-a-startup-pin"></a>Indítási PIN-kód hozzáadása

Egyes Android-eszközök indítási PIN-kód létrehozását teszik kötelezővé az eszköz biztonsága érdekében. A beállítás helye az eszköz **Settings (beállítások** ) alkalmazásában lesz. A beállítás neve és helye eltérő lehet. A Samsung Galaxy S7 esetében például a beállítást **biztonságos indításnak**nevezzük. A beállítás engedélyezéséhez és a PIN-kód létrehozásához lépjen a **beállítások** > **zárolási képernyő és biztonság** > **biztonságos indítás**elemre.  

## <a name="encrypt-the-entire-device"></a>A teljes eszköz titkosítása

Ez a szakasz csak a Céges portál alkalmazásra vonatkozik. Egyes eszközök esetében választható a teljes eszköz titkosítása vagy csak a használatban lévő tárterület titkosítása. Válassza a teljes eszköz titkosítása lehetőséget. Ha a csak a felhasznált terület titkosítását választotta:

1. [Távolítsa el az eszközt a céges portálból](unenroll-your-device-from-intune-android.md).
2. A felhasznált terület visszafejtése.  
3. A teljes eszköz titkosítása.  
4. Regisztrálja újra az eszközt.  

## <a name="downgrade-your-version-of-android"></a>Az Android alacsonyabb verzióra való visszaléptetése

Ez a szakasz csak a Céges portál alkalmazásra vonatkozik. Ha az eszköz felajánlja az Android 6,0-es vagy újabb verzióra való visszalépés lehetőségét, akkor tegye a következőt:. Ha megpróbálja visszaminősíteni az eszközt, fennáll az adatvesztés kockázata. Ellenkező esetben javasoljuk, hogy a probléma megoldásához lépjen kapcsolatba a cég informatikai támogató szolgálatával. Kérje meg a cég informatikai támogatási szolgálatának elérhetőségét a [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="specific-manufacturer-issues"></a>Gyártóspecifikus problémák

Néhány androidos eszköz a 7,0-es és újabb verzióiban olyan módon titkosítja az adattitkosítást, amely nem konzisztens bizonyos Android-platformokra vonatkozó szabványokkal. Ezek a titkosítási módszerek veszélyeztetik az eszközök adatait. Ennek eredményeképpen ezek az eszközök nem támogatottak.

A támogatott androidos eszközök nem teljes listájáért tekintse meg az Intune- [ban támogatott operációs rendszereket és böngészőket](https://docs.microsoft.com/intune/fundamentals/supported-devices-browsers#supported-samsung-knox-standard-devices)ismertető cikket. Ha az eszköz nem szerepel a listáján, tekintse meg az eszköz gyártóját, vagy forduljon a támogatási személyhez.

> [!Note]
> A Microsoft együttműködik a gyártókkal a tesztelés vagy a felhasználók által jelentett problémák megoldásához. Ezt a cikket folyamatosan frissítjük, ha új információk állnak rendelkezésünkre.

## <a name="update-devices"></a>Eszközök frissítése

Ha még nem frissítette az eszközt az Android legújabb verziójára, nyissa meg az eszköz **Beállítások** alkalmazását, és válassza a **frissítés**lehetőséget.  

## <a name="next-steps"></a>További lépések

További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához (a kapcsolattartási adatokat a [Céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja), vagy írjon a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-csapatának</a>.  
