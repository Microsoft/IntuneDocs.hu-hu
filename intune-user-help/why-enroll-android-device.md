---
title: Miért regisztrálja androidos eszközét
description: Ismerje meg, hogy miért fontos az eszköz regisztrálása az Intune-ban
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08b20ba59c0dabc680e0f5760ee4de892506b7e3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72501600"
---
# <a name="why-enroll-your-android-device"></a>Miért regisztrálja androidos eszközét  

Az iskolák és a munkaadók gondoskodnak arról, hogy biztonságos, megbízható eszközt használjanak a belső erőforrások eléréséhez. A Céges portál és a Microsoft Intune alkalmazások gondoskodnak az Android-eszköz és az adatok biztonságáról, miközben hozzáférnek ezekhez az erőforrásokhoz. Gondoskodnak arról, hogy biztonságos hozzáférést biztosítson az erőforrásokhoz, függetlenül attól, hogy hol vagy milyen eszközt használ. 

Ha a szervezete megköveteli az alkalmazások egyikének telepítését és regisztrálását, ezt csak akkor kell megtennie, ha az eszközről hozzáfér a vállalati erőforrásokhoz. Ez a cikk az eszközök ezen alkalmazásokkal való regisztrálásának célját és előnyeit ismerteti.  

## <a name="gets-your-device-managed"></a>Eszköz felügyelet alá vonása  
 Céges portál és a Microsoft Intune alkalmazás regisztrálja az eszközt az Intune-ban.  Az Intune egy mobileszköz-kezelő szolgáltató, amely segítséget nyújt a szervezetnek a mobileszközök és alkalmazások felügyeletéhez a biztonsági és eszköz-házirendek segítségével. 

Az alkalmazások végigvezetik a regisztráció lépésein, és úgy konfigurálja az eszközbeállítások beállításait, hogy megfeleljenek a szervezet házirendjének. Emellett riasztást küld a vállalati hozzáférés megkezdése előtt feloldható problémákról vagy beállításokról.  

Példák a szervezet által igényelt házirendekre:  
* Jelszó vagy PIN-kód beállítása
* Hozzáférés korlátozása adott számú bejelentkezési kísérlet után
* Jailbreakelt vagy rootolt eszköz használatának kizárása
* A munkahelyen kötelező alkalmazások telepítése  

## <a name="gives-you-access-to-work-and-school-apps-work-files-and-email"></a>Hozzáférést nyújt munkahelyi és iskolai alkalmazásaihoz, fájljaihoz és levelezéséhez  
A beléptetés során a Céges portál és a Microsoft Intune alkalmazásnak csatlakoznia kell a munkahelyi vagy iskolai fiókjához.  Miután megtörtént a hitelesítés, és miután konfigurálta az eszközbeállítások beállításait a szervezet házirendjeinek megfelelően, hozzáférhet a szervezete e-mail-fiókjához, hálózatához, fájljaihoz és alkalmazásaihoz.  

Egyes szervezetek munkahelyi vagy biztonsági alkalmazások – például a Microsoft Office vagy a Mobile Threat Defense – telepítését követelhetik meg. Ha ezek az alkalmazások szükségesek vagy elérhetőek lesznek az Ön számára, Céges portál vagy a Microsoft Intune alkalmazásban is megtalálhatja őket.

## <a name="lets-you-remotely-reset-a-lost-or-stolen-device-if-device-supports-it"></a>Távolról alaphelyzetbe állíthatja elveszett vagy ellopott eszközét (ha az eszköz ezt támogatja)
Ha az eszköz elveszett vagy ellopták, a Céges portál alkalmazásba vagy annak webhelyére egy másik eszközről bejelentkezve visszaállíthatja a telefont a gyári beállításokra. Ez a funkció jól jöhet, ha az eszköz olyan jogvédett munkahelyi adatokat tartalmaz, amelyeket nem szeretne mások számára elérhetővé tenni. Mivel az eszköz regisztrálva van felügyeletre, a céges ügyfélszolgálat vagy rendszergazda is segíthet alaphelyzetbe állítani.  

Az Alaphelyzetbe állítás funkció nem érhető el a Microsoft Intune alkalmazásban.  

## <a name="notifies-you-of-policy-updates-and-requirements"></a>Értesítést küld a szabályzatfrissítésekről és a követelményekről
A Céges portál vagy Microsoft Intune alkalmazás 8 óránként automatikusan bekerül az Intune-ba, vagy szinkronizálja őket. Ha Céges portál használ, és gyakrabban szeretne bejelentkezni, Ön vagy a cég informatikai támogatási szolgálata manuális szinkronizálást indíthat. A bejelentkezés során az alkalmazások a következőket teszik:  

* A cég informatikai támogatási szolgálata által elérhetővé tett szabályzatok és alkalmazásfrissítések letöltése.  
* A hardverleltár változásainak elküldése. Ezek a frissítések nem tartalmaznak személyes adatokat.  
* A vállalati alkalmazások leltárában bekövetkezett változások elküldése. Ezek a frissítések nem tartalmaznak személyes adatokat.  

Ha az eszköz szinkronban van, vagy már nem felel meg a követelményeknek, az állapota *nem megfelelőként*jelenik meg. Amíg az eszköz nem felel meg újra a követelményeknek, megvonható az Ön munkahelyi vagy iskolai erőforrásokhoz való hozzáférése. A Céges portál alkalmazás értesíti Önt ezekről a problémákról, és a kijavításához szükséges lépésekről.  


## <a name="permits-company-support-access-to-your-device"></a>Lehetővé teszi a céges ügyfélszolgálat hozzáférését az eszközhöz
Az eszköz regisztrálása esetén a cég informatikai támogatási szolgálata vagy a rendszergazda korlátozott és ésszerű okokból hozzáférést kap az eszközhöz. Ezek a következők:  

* Az eszköz visszaállítása a gyári beállításokra. A fent említetteknek megfelelően Ön is alaphelyzetbe állíthatja az eszközt. Azonban ha nem fér hozzá a Céges portál alkalmazáshoz, ezt a cége is megteheti.  

* Az összes céges adat eltávolítása. A szervezete eltávolíthat céges adatokat az eszközről, ha Ön elhagyja a céget vagy az eszköz kezelése megszűnik. A személyes adatait és beállításait nem távolítja el a rendszer, és az eszközön marad.  

* Követelményeket határozhat meg az eszközön, például a jelszó vagy PIN-kód használatát. Ebben az esetben olyan alkalmazás-értesítéseket kap, amelyek nem felelnek meg az eszköznek. A cég támogatási szolgálata korlátozhatja, hogy hányszor lehet helytelen jelszót megadni az eszközön. Túl sok sikertelen kísérlet után az eszközt lezárhatják.  

* Ehhez el kell fogadnia a használati feltételeket.  

* A kamera letiltása. A szabályzat célja, hogy meggátolja a jogvédett adatok fotózását, valamint kevesebb figyelemelterelő funkciót nyújtson iskolai környezetekben. Az iskolák letilthatják a kamerákat a tantermi eszközökön, a tanulók így nem oszthatnak meg egymással vizsgaanyagokat.  

* Az eszközön található adatok titkosításának megkövetelése. Ez a szabályzat hozzájárul az adatok védelméhez az eszköz elvesztésekor és ellopásakor. Emellett az eszközökkel vagy alkalmazásokkal megosztott adatok számára is védelmet nyújt. 

## <a name="next-steps"></a>További lépések  

Segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához (a kapcsolattartási adatokat a [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja), vagy írjon a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble installing the Company Portal app on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-csapatának</a>.
