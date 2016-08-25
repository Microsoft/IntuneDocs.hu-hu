---
title: "Újdonságok | Microsoft Intune"
description: "Ismerkedjen meg a Microsoft Intune e havi és korábbi verzióinak újdonságaival"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 65e53ad6a74fbf0e9249c367f517ab52ea0efa80


---

# Újdonságok a Microsoft Intune-ban
Ismerkedjen meg a Microsoft Intune új verziójának újdonságaival. Emellett tájékozódhat a jövőbeni változtatásokról és a korábbi verziókról, és felkészülhet a következő kiadásra.

Az alábbiakban ismertetjük az új verzió újdonságait. A Windows Defender házirendbeállításainak frissítését kivéve mindegyik funkciót támogatják a hibrid ügyféltelepítések (Configuration Manager az Intune-nal). Az új hibrid funkciókról további információért tekintse meg a [hibrid újdonságok oldalát](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## 2016. június
### Az Intune szolgáltatás állapota
Az Intune-ra vonatkozó szolgáltatásállapot-adatok átkerültek a központi, a többi Microsoft-szolgáltatásról is információt nyújtó helyre. Ezt az információt mostantól az Office 365 felügyeleti portál Szolgáltatás állapota menüjében találja meg. További információkat [ebben a blogban](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/) talál.

## Alkalmazáskezelés
- **Továbbfejlesztett konfigurációs felület a Windows 10 vállalati adatkezelési házirendjéhez.** Továbbfejlesztettük a Windows 10 vállalati adatkezelési házirendjének konfigurációs felületét az alkalmazásszabályok létrehozása, a hálózathatár-definíciók megadása és más vállalati adatvédelmi beállítások tekintetében. További tudnivalók: [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) (Enterprise Data Protection-házirend létrehozása a Microsoft Intune-nal).


## Eszközkezelés
- **Windows Defender-házirendbeállítása a vélhetően nemkívánatos alkalmazások elleni védelem biztosításához.** A Windows Defender egy új, **Potentially Unwanted Application Detection** (Vélhetően nemkívánatos alkalmazás észlelése) nevű beállításával bővült a Windows 10 asztali és mobil verziójának általános konfigurációs házirendje. Ezzel a beállítással biztosíthatja a regisztrált Windows rendszerű asztali számítógépek védelmét a Windows Defender által a vélhetően nemkívánatos osztályba sorolt szoftverek futtatása ellen. Biztosíthatja a védelmet ezen alkalmazások futtatása ellen, vagy a vizsgálati üzemmóddal jelentést készíthet a vélhetően nemkívánatos alkalmazások telepítéséről. További információ: [Windows 10 policy settings in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune) (A Windows 10 házirendbeállításai a Microsoft Intune-ban).
<!---TFS 1244478--->

## Feltételes hozzáférés
- **Cisco ISE-hálózati hozzáférés-vezérlési szabályzat az Intune-hoz.**  Azok az ügyfelek, akik a Cisco Identity Service Engine (ISE) 2.1 szolgáltatást, illetve a Microsoft Intune-t is használják, a hálózati hozzáférés-vezérlési szabályzatot beállíthatják az ISE szolgáltatásban.

    Ezen szabályzat használatakor azoknak az eszközöknek, melyeknek Wi-Fi vagy VPN használatával kell kapcsolódniuk a hálózathoz, meg kell felelniük a következő feltételeknek a hozzáférésük engedélyezéséhez:

    * Az Intune által felügyeltnek kell lenniük
    * Meg kell felelniük az Intune összes telepített megfelelőségi szabályzatának

 A nem megfelelő eszközökkel rendelkező végfelhasználókat kérni fogja a rendszer, hogy regisztráljanak, és hárítsák el a megfelelőségi problémákat, hogy hozzáférést kapjanak.
- **Feltételes hozzáférés böngészőhöz.** Feltételes hozzáférési házirendet állíthat be az [Exchange Online-hoz](restrict-access-to-exchange-online-with-microsoft-intune.md) és a [SharePoint Online-hoz](restrict-access-to-sharepoint-online-with-microsoft-intune.md), így azok csak a felügyelt és a szabályozásoknak megfelelő iOS- és Android-eszközök támogatott webböngészőiről érhetők majd el. Az Outlook Web Accessbe (OWA) és a SharePoint-webhelyekre iOS- vagy Android-eszközön bejelentkezni próbáló végfelhasználóktól a rendszer a bejelentkezés előtt kérni fogja az eszköz Intune-beli regisztrálását, valamint az esetleges szabályozási hiányosságok elhárítását.
<!---TFS 1175844--->

- **A Dynamics CRM Online támogatja a feltételes hozzáférést.** Feltételes hozzáférési házirendet állíthat be a [Dynamics CRM Online-hoz](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md), hogy csak a felügyelt és a szabályozásnak megfelelő iOS- és Android-eszközök érhessék el. A Dynamics CRM mobilalkalmazásba iOS- vagy Android-eszközön bejelentkezni próbáló végfelhasználóktól a bejelentkezés végrehajtása előtt a rendszer kérni fogja a regisztrálást az Intune-ba, valamint a meg nem felelést okozó problémák megszüntetését.
<!---TFS1295358--->

## A Vállalati portál újdonságai

### Androidos Munkahelyi portál alkalmazás

- Ha a rendszergazdák az új „Az eszközök tiltsák le az ismeretlen forrásból származó alkalmazások telepítését (Android 4.0+)” házirendet alkalmazzák, az Android 4.0-val és későbbi verziókkal rendelkező végfelhasználók számára „Az ismeretlen forrásokból származó alkalmazások telepítését le kell tiltani” üzenet jelenik meg. A felhasználóknak ekkor a **Beállítások** > **Biztonság** menüben ki kell kapcsolniuk az **Ismeretlen források** lehetőséget. A megfelelőségi üzenet tartalmaz egy hivatkozást, amely további [tájékoztatást](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) ad a felhasználóknak az üzenetről és a beállítás kikapcsolásának okáról.

- Ha a rendszergazdák az új „A Biztonsági fenyegetések keresése az eszközön beállítás engedélyezésének megkövetelése az eszközökön (Android 4.0+)” házirendet alkalmazzák, az Android 4.0-val és későbbi verziókkal rendelkező végfelhasználók számára „Futtasson biztonsági fenyegetés elleni keresést az eszközön” üzenet jelenik meg. A felhasználóknak ekkor a **Beállítások** > **Google** > **Biztonság** menüben be kell kapcsolniuk a **Biztonsági fenyegetések keresése az eszközön** beállítást. A megfelelőségi üzenet tartalmaz egy hivatkozást, amely további [tájékoztatást](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) ad a felhasználóknak az üzenetről és a beállítás bekapcsolásának okáról.

- Ha a rendszergazdák az új „Az USB-hibakeresés letiltásának megkövetelése (Android 4.2+)” házirendet alkalmazzák, az Android 4.2-vel és későbbi verziókkal rendelkező végfelhasználók számára „Az USB-hibakeresést le kell tiltani” üzenet jelenik meg. A felhasználóknak ekkor a **Beállítások** > **Fejlesztői beállítások** menüben ki kell kapcsolniuk az **USB-hibakeresést**. A megfelelőségi üzenet tartalmaz egy hivatkozást, amely további [tájékoztatást](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) ad a felhasználóknak az üzenetről és a beállítás kikapcsolásának okáról.

- Ha a rendszergazdák az új „Az Android minimálisan előírt biztonsági javítási szintje (Android 6.0+)” házirendet alkalmazzák, az Android 6.0-val és későbbi verziókkal rendelkező végfelhasználók számára „Az eszköz nem éri el a minimális Android biztonsági javítási szintet” üzenet jelenik meg. A felhasználóknak ekkor telepíteniük kell a szükséges biztonsági javítási szintet. A megfelelőségi üzenet tartalmaz egy hivatkozást, amely további [tájékoztatást](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) ad a felhasználóknak a biztonsági javítás telepítéséről és arról, hogy jelenleg melyik biztonsági javítási verzióval rendelkeznek.

### iOS rendszerű Vállalati portál alkalmazás

- A végfelhasználó számára az üzleti alkalmazások telepítésekor egy továbbfejlesztett környezet jelenik meg. Ha az alkalmazás telepítése hosszú ideig tart, a felhasználók manuálisan szinkronizálhatják az eszközt a szinkronizálási folyamat kényszerített folytatásához. A végfelhasználói lépéseket [Sync your iOS device manually](/Intune/EndUser/sync-your-device-manually-ios) (Az iOS-eszköz manuális szinkronizálása) című szakaszban tekintheti meg.

- Az iOS rendszerhez készült Microsoft Intune Vállalati portál alkalmazás frissült, így már támogatja az iOS 8.0-s és újabb verzióit. A frissítés eredményeként a végfelhasználók csak akkor tudják telepíteni a Vállalati portál alkalmazást, és regisztrálni új eszközöket az Intune-ban, ha az eszközön az iOS 8.0-s vagy újabb verziója fut. Az iOS nem támogatott verzióját futtató eszközöket korábban regisztrált felhasználók továbbra is használhatják az eszközükön lévő Vállalati portál alkalmazást.


## Mi várható?

### A felhőplatform ütemterve
Maradjon naprakész az Intune jövőbeli fejlesztéseiről a [Cloud Platform ütemterv](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune) használatával.

### Szolgáltatások érvénytelenítése
- **Intune Viewer-alkalmazások** Az új RMS-megosztó alkalmazás megjelenésével 2016 augusztusától kezdve megszüntetjük a következő Intune Viewer-alkalmazásokat:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer Android-eszközökre a Google Play Áruházból

  Az Intune Viewer-alkalmazások használata helyett javasoljuk az új androidos Rights Management alkalmazás (RMS-megosztó alkalmazás) használatát, amelynek segítségével három különálló alkalmazás helyett elég egyetlen alkalmazást telepítenie a vállalati fájlok Android-eszközökön való biztonságos megtekintéséhez.

- **Az értesítési szabályok egyéni csoportcélzási lehetősége megszűnik.**
Az Intune értesítési szabályai határozzák meg, hogy kinek küld értesítő e-mailt az Intune. Jelenleg úgy is beállíthatja az értesítési szabályokat, hogy a rendszer a létrehozott Intune-eszközcsoportokhoz tartozó eszközök összes felhasználójának elküldje az e-maileket. 2016. június 1-jétől fogva a felhasználó által létrehozott csoportok megcélzása nem lesz megvalósítható.

    Ma a következő lépések szükségesek ahhoz, hogy egy értesítési szabállyal egy Ön által létrehozott csoportot célozzon meg a Microsoft Intune felügyeleti konzoljában:

    A **Felügyelet** munkaterületen kattintson az **Értesítési szabályok** > **Új szabály létrehozása** elemre.

    Az Értesítési szabály létrehozása varázsló második lépésében válassza ki a szabály által megcélzott eszközcsoportokat. Ez az eszközcsoportok kiválasztására szolgáló lépés a jövőben nem lesz elérhető az Intune-konzolon.

    A módosítás előzetes ütemterve a következő:
    - 2016 augusztusától az új bérlők számára nem fog megjelenni az Értesítési szabály létrehozása varázsló második lépése. A meglévő bérlőkre ekkor még nem lesz érvényes a változás.
    - 2016 szeptemberétől kezdve egyes meglévő bérlők számára sem fog megjelenni az eszközcsoportok kiválasztására szolgáló lépés a varázslóban.
    - 2016 novemberétől kezdve terveink szerint már egyetlen bérlő számára sem fog megjelenni az eszközcsoportok kiválasztására szolgáló lépés a varázslóban.


- **Az iOS-es Vállalati portál alkalmazás támogatására vonatkozó módosítások**. Júliustól az iOS rendszerhez készült Microsoft Intune vállalati portál alkalmazás minden felhasználójának az alkalmazás legújabb verzióját kell majd használnia. Az új felhasználók csak a legújabb verziót fogják tudni letölteni, a jelenlegi felhasználóknak pedig frissíteniük kell erre a verzióra. A vállalati portál legújabb verziójához iOS 8.0-s vagy újabb operációs rendszer szükséges, ezért a régebbi iOS-verziót futtató eszközök felhasználói nem fogják tudni használni a vállalati portált, sem pedig regisztrálni, amíg nem frissítik az eszközt iOS 8.0-s vagy újabb verzióra, majd ezt követően a vállalati portál alkalmazást is a legújabb verzióra. Az iOS 8.0-s verziójánál régebbi verziót futtató regisztrált eszközök továbbra is láthatóak és felügyelhetőek lesznek az Intune felügyeleti konzolján.





## Az Intune korábbi kiadásai
Az Intune-ban az elmúlt hat hónapban bevezetett újdonságok listája [Az Intune korábbi kiadásai](previous-intune-releases.md) című cikkben olvasható.



### További információ
* [A Microsoft Intune blogja](http://go.microsoft.com/fwlink/?LinkID=273882)
* [A felhőplatform ütemterve](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Jul16_HO1-->


