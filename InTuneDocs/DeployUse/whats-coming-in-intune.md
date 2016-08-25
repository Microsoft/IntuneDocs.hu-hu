---
title: "Várható újdonságok | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: b203f51171d38f2b0fc2b46e556679322701d29b
ms.openlocfilehash: 77d2e74dcb032ff52808998c56de7d6b8847ebbe


---

# Várható újdonságok a Microsoft Intune-ban
Ezekre az információkra igen szigorú titoktartási szerződés vonatkozik. Az információk változhatnak. Fennáll a kockázata, hogy az itt felsorolt funkciók nem készülnek el a kitűzött határidőig, és csak egy későbbi kiadásban lesznek elérhetők. Más funkciók próbaüzemben működnek (fokozatos bevezetéssel), hogy meggyőződjünk arról, hogy készen állnak a használatra. Esetleges kérdéseivel és észrevételeivel kérjük, forduljon Intune/PM-partneréhez.

A lap tartalmát rendszeresen frissítjük. A várható újdonságokkal kapcsolatban friss hírekért látogasson vissza.

A következő változtatások vannak fejlesztés alatt az Intune-hoz. Mindezeket a funkciókat a hibrid ügyfélkörnyezetek is támogatni fogják (tehát az Intune-nal integrált Configuration Manager is). Az új hibrid funkciókról további információért tekintse meg a [hibrid újdonságok oldalát](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Alkalmazáskezelés
- **Továbbfejlesztett konfigurációs felület a Windows 10 vállalati adatkezelési házirendjéhez.** Továbbfejlesztettük a Win 10 vállalati adatkezelési házirendjének konfigurációs felületét az alkalmazásszabályok létrehozása, a hálózathatár-definíciók megadása és más vállalati adatvédelmi beállítások tekintetében.
<!---TFS 1303011--->

- **Feltételes hozzáférés böngészőhöz.** Lehetősége nyílik majd, hogy feltételes hozzáférési házirendet állítson be az Exchange Online-hoz és a SharePoint Online-hoz, így azokat csak a felügyelt és a szabályozásoknak megfelelő iOS- és Android-eszközök érhetik majd el. Az Outlook Web Accessbe (OWA) és a SharePoint-webhelyekre iOS- vagy Android-eszközön bejelentkezni próbáló végfelhasználóktól a rendszer a bejelentkezés előtt kérni fogja az eszköz Intune-beli regisztrálását, valamint az esetleges szabályozási hiányosságok elhárítását.
<!---TFS 1175844--->

- **A Dynamics CRM Online támogatja a feltételes hozzáférést.** Az ügyfelek feltételes hozzáférési házirendet állíthatnak be a Dynamics CRM Online-hoz, hogy csak a felügyelt és a szabályozásnak megfelelő iOS- és Android-eszközök érhessék el. A Dynamics CRM mobilalkalmazásba iOS- vagy Android-eszközön bejelentkezni próbáló végfelhasználóktól a bejelentkezés végrehajtása előtt a rendszer kérni fogja a regisztrálást az Intune-ba, valamint a meg nem felelést okozó problémák megszüntetését.
<!---TFS1295358--->

### Xamarin-támogatás
A Microsoft Intune App SDK a következő használati helyzetekben fogja támogatni a Xamarin-alkalmazásokat:

- Új alkalmazások írása vagy a meglévő üzleti alkalmazások kódjának módosítása az Intune SDK-val. A bővítmény a [Microsoft Intune Github-oldalról](https://github.com/msintuneappsdk) lesz letölthető.
- A mobilalkalmazás-felügyelet támogatásának kiterjesztése a meglévő üzleti alkalmazásokra az Intune alkalmazásburkoló eszközével.

Ha segítségre van szüksége a megfelelő módszer kiválasztásához, lásd: [Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->

## Eszközkezelés
- **Windows Defender-házirendbeállítása a vélhetően nemkívánatos alkalmazások elleni védelem biztosításához.** A Windows Defender egy új, **Potentially Unwanted Application Detection** (Vélhetően nemkívánatos alkalmazás észlelése) nevű beállításával bővült a Windows 10 asztali és mobil verziójának általános konfigurációs házirendje. Ezzel a beállítással biztosíthatja a regisztrált Windows rendszerű asztali számítógépek védelmét a Windows Defender által a vélhetően nemkívánatos osztályba sorolt szoftverek futtatása ellen. Biztosíthatja a védelmet ezen alkalmazások futtatása ellen, vagy a vizsgálati üzemmóddal jelentést készíthet a vélhetően nemkívánatos alkalmazások telepítéséről.
<!---TFS 1244478--->

## Feltételes hozzáférés
**Cisco ISE-hálózati hozzáférés-vezérlési szabályzat az Intune-hoz.**  Azok az ügyfelek, akik a Cisco Identity Service Engine (ISE) 2.1 szolgáltatást, illetve a Microsoft Intune-t is használják, a hálózati hozzáférés-vezérlési szabályzatot beállíthatják az ISE szolgáltatásban.

Ezen szabályzat használatakor azoknak az eszközöknek, melyeknek Wi-Fi vagy VPN használatával kell kapcsolódniuk a hálózathoz, meg kell felelniük a következő feltételeknek a hozzáférésük engedélyezéséhez:

* Az Intune által felügyeltnek kell lenniük
* Meg kell felelniük az Intune összes telepített megfelelőségi szabályzatának

A nem megfelelő eszközökkel rendelkező végfelhasználókat kérni fogja a rendszer, hogy regisztráljanak, és hárítsák el a megfelelőségi problémákat, hogy hozzáférést kapjanak.
<!---TFS 1299144--->

## Vállalati portál
**Változások a készülékregisztráció-kezelői fiókokban az iOS-es Vállalati portál alkalmazásban.** A jobb teljesítmény és méretezés érdekében az Intune a jövőben nem fogja megjeleníteni az összes készülékregisztráció-kezelő (DEM-) eszközt az iOS rendszerhez készült Vállalati portál alkalmazás Saját eszközök panelén. Csak az alkalmazást futtató helyi eszköz jelenik meg, és az is csak abban az esetben, ha korábban már regisztrálták a Vállalati portálon. A DEM-felhasználó a helyi eszközön elvégezheti a kapcsolódó műveleteket, de a további regisztrált eszközök távoli felügyeleti teendői csak az Intune felügyeleti konzolon lesznek majd végrehajthatók.  Emellett az Intune-ból kivezettük a DEM-fiókoknak az Apple Device Enrollment Programmal és az Apple Configurator eszközzel való használatát. Ezek a regisztrálási módszerek alapértelmezés szerint támogatják a megosztott iOS-eszközök felhasználó nélküli regisztrálását. Csak akkor használjon DEM-fiókot, ha a megosztott eszközök felhasználó nélküli regisztrálása nem lehetséges.
<!---TFS 1233681--->

## Szolgáltatások érvénytelenítése
**A Windows 8 és a Windows Phone 8 vállalati portál alkalmazásai 2016. szeptembertől elavulttá válnak.** 2016. szeptembertől a Microsoft Intune már nem fogja támogatni a Microsoft Intune vállalati portál alkalmazásait Windows Phone 8 és Windows 8 platformokon. Frissítése az eszközöket a Windows 8.1 és a Windows Phone 8.1 rendszerekre, és használja a megfelelő Windows 8.1 és Windows Phone 8.1 vállalati portál alkalmazásokat az alkalmazásoknak ezekre az eszközökre történő további terjesztésére.
<!---TFS 1255391--->

**Az értesítési szabályok egyéni csoportcélzási lehetősége megszűnik.**
Az Intune értesítési szabályai határozzák meg, hogy kinek küld értesítő e-mailt az Intune. Jelenleg úgy is beállíthatja az értesítési szabályokat, hogy a rendszer a létrehozott Intune-eszközcsoportokhoz tartozó eszközök összes felhasználójának elküldje az e-maileket. 2016. június 1-jétől fogva a felhasználó által létrehozott csoportok megcélzása nem lesz megvalósítható.

A módosítás előzetes ütemterve a következő:
- 2016 augusztusától az új bérlők számára nem fog megjelenni az Értesítési szabály létrehozása varázsló második lépése. A meglévő bérlőkre ekkor még nem lesz érvényes a változás.
- 2016 szeptemberétől kezdve egyes meglévő bérlők számára sem fog megjelenni az eszközcsoportok kiválasztására szolgáló lépés a varázslóban.
- 2016 novemberétől kezdve terveink szerint már egyetlen bérlő számára sem fog megjelenni az eszközcsoportok kiválasztására szolgáló lépés a varázslóban.
<!---   TFS 1278864--->

**Az iOS rendszerű vállalati portál alkalmazás támogatására vonatkozó módosítások.**
Júliustól az iOS rendszerhez készült Microsoft Intune vállalati portál alkalmazás minden felhasználójának az alkalmazás legújabb verzióját kell majd használnia. Az új felhasználók csak a legújabb verziót fogják tudni letölteni, a jelenlegi felhasználóknak pedig frissíteniük kell erre a verzióra. A vállalati portál legújabb verziójához iOS 8.0-s vagy újabb operációs rendszer szükséges, ezért a régebbi iOS-verziót futtató eszközök felhasználói nem fogják tudni használni a vállalati portált, sem pedig regisztrálni, amíg nem frissítik az eszközt iOS 8.0-s vagy újabb verzióra, majd ezt követően a vállalati portál alkalmazást is a legújabb verzióra. Az iOS 8.0-s verziójánál régebbi verziót futtató regisztrált eszközök továbbra is láthatóak és felügyelhetőek lesznek az Intune felügyeleti konzolján.  

**Intune Viewer-alkalmazások.** Az új RMS-megosztó alkalmazás megjelenésével 2016 augusztusától kezdve megszüntetjük a következő Intune Viewer-alkalmazásokat:
- Intune AV Viewer
- Intune PDF Viewer
- Intune Image Viewer Android-eszközökre a Google Play Áruházból

Az Intune Viewer-alkalmazások használata helyett javasoljuk az új androidos Rights Management alkalmazás (RMS-megosztó alkalmazás) használatát, amelynek segítségével három különálló alkalmazás helyett elég egyetlen alkalmazást telepítenie a vállalati fájlok Android-eszközökön való biztonságos megtekintéséhez. További információk az RMS-megosztó alkalmazásról (a dokumentációra mutató hivatkozással).


### További információ
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new-in-microsoft-intune.md).



<!--HONumber=Jul16_HO1-->


