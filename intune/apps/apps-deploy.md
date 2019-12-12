---
title: Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-ban
titleSuffix: ''
description: Megtudhatja, hogyan rendelhet hozzá egy Intune-alkalmazást felhasználók vagy eszközök csoportjaihoz Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e990cd94c0f8622d07e59b4130566a1dc2953a1c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563997"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Miután [hozzáadott egy alkalmazást](apps-add.md) a Microsoft Intune-hoz, azt felhasználókhoz és eszközökhöz rendelheti hozzá. Vegye figyelembe, hogy az alkalmazást attól függetlenül hozzárendelheti az eszközhöz, hogy az eszközt az Intune felügyeli-e.

> [!NOTE]
> Az elérhető üzembe helyezési szándék nem támogatott az eszközök csoportjai esetében, csak a felhasználói csoportok támogatottak.

Az alábbi táblázat az alkalmazások felhasználókhoz és eszközökhöz való hozzárendelésével kapcsolatos különböző lehetőségeket sorolja fel:

|   | Az Intune-ban regisztrált eszközök | Az Intune-ban nem regisztrált eszközök |
|-------------------------------------------------------------------------------------------|------------------------------|----------------------------------|
| Hozzárendelés felhasználókhoz | Igen | Igen |
| Hozzárendelés eszközökhöz | Igen | Nem |
| Burkolt alkalmazások, vagy azt Intune SDK-t magukba foglaló alkalmazások hozzárendelése (alkalmazásvédelmi szabályzatok esetén) | Igen | Igen |
| Alkalmazások hozzárendelése elérhetőként | Igen | Igen |
| Alkalmazások hozzárendelése szükségesként | Igen | Nem |
| Alkalmazások eltávolítása | Igen | Nem |
| Alkalmazásfrissítések fogadása az Intune-ból | Igen | Nem |
| A végfelhasználók a Céges portál alkalmazásban telepítik az elérhető alkalmazásokat | Igen | Nem |
| A végfelhasználók a webalapú Intune Céges portálon telepítik az elérhető alkalmazásokat | Igen | Igen |

> [!NOTE]
> Jelenleg (mind üzletági, mind pedig áruházbeli) iOS- és Android-alkalmazásokat rendelhet hozzá azokhoz az eszközökhöz, melyek nincsenek regisztrálva az Intune-ban.
>
> Az alkalmazásfrissítések fogadásához az Intune-ban nem regisztrált eszközök felhasználóinak fel kell keresniük saját céges portáljukat, hogy manuálisan telepítsék az alkalmazásfrissítéseket.

## <a name="assign-an-app"></a>Alkalmazás kiosztása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás**lehetőséget.
3. Az **Alkalmazások** ablaktáblán jelölje ki a hozzárendelni kívánt alkalmazást.
4. A menü **Kezelés** szakaszában válassza a **Hozzárendelések**. elemet.
5. Válassza a **Csoport hozzáadása** lehetőséget az alkalmazáshoz kapcsolódó **Csoport hozzáadása** ablaktábla megnyitásához.
6. Az adott alkalmazáshoz válasszon egy **hozzárendelés-típust**:
   - **Regisztrálva lévő eszközökhöz**: rendelje hozzá az alkalmazást azon felhasználók csoportjaihoz, akik telepíthetik az alkalmazást a céges portál alkalmazásból vagy webhelyről.
   - **Regisztrációval vagy anélkül is elérhető**: Az alkalmazás hozzárendelése olyan felhasználók csoportjaihoz, akik eszközei nincsenek regisztrálva az Intune-ban. A felhasználóknak Intune-licencet kell rendelniük, lásd: [Intune-licencek](../fundamentals/licenses.md).
   - **Szükséges**: A rendszer telepíti az alkalmazást a kiválasztott csoportok eszközeire. Egyes platformok további kérésekkel rendelkezhetnek arról, hogy a végfelhasználó tudomásul veszi az alkalmazás telepítésének megkezdése előtt.
   - **Eltávolítás**: az alkalmazást a kiválasztott csoportok eszközeiből távolítja el, ha az Intune már telepítette az alkalmazást az eszközön a "rendelkezésre álló regisztrált eszközökön" vagy a "kötelező" hozzárendelés használatával ugyanazzal az üzembe helyezéssel. A központi telepítés után nem távolíthatók el a webes hivatkozások.

     > [!NOTE]
     > **Csak iOS-alkalmazások esetén**:
     > - Ha azt szeretné beállítani, hogy mi történik a felügyelt alkalmazásokkal, ha az eszközök már nem kezelhetők, kiválaszthatja a kívánt beállítást az Eltávolítás az **eszköz eltávolításakor**lehetőség alatt. További információ: alkalmazás- [eltávolítási beállítás az iOS által felügyelt alkalmazásokhoz](apps-deploy.md#app-uninstall-setting-for-ios-managed-apps).
     > - Ha létrehozott egy iOS-es VPN-profilt, amely az alkalmazáson belüli VPN-beállításokat tartalmazza, akkor a VPN **-profilt**is kiválaszthatja. Az alkalmazás futtatásakor megnyílik a VPN-kapcsolat. További tudnivalókért lásd: [VPN-beállítások iOS-eszközökön](../vpn-settings-ios.md).
     >
     > **Csak Android-alkalmazások esetén**: Ha az Android **-alkalmazást regisztráció nélkül vagy anélkül**telepíti, a jelentéskészítési állapot csak a regisztrált eszközökön lesz elérhető.
     >
     > A **regisztrált eszközök számára elérhető**: az alkalmazás csak akkor jelenik meg elérhetőként, ha a céges portál bejelentkezett felhasználó az eszközt regisztráló elsődleges felhasználó, és az alkalmazás alkalmazható az eszközre.

7. Az alkalmazás-hozzárendelés által érintett felhasználócsoportok kiválasztásához válassza a **Belefoglalt csoportok** lehetőséget.
8. Miután kiválasztott egy vagy több csoportot a belefoglaláshoz, válassza a **Kiválasztás** lehetőséget.
9. Kattintson a **Hozzárendelés** ablaktáblán az **OK** gombra a belefoglalt csoportok kiválasztásának befejezéséhez.
10. Ha ki szeretne zárni felhasználói csoportokat az alkalmazás-hozzárendelésből, válassza a **Csoportok kizárása** lehetőséget.
11. Ha valamilyen csoport kizárása mellett döntött, válassza a **Csoportok kiválasztása** ablaktáblán a **Kiválasztás** lehetőséget.
12. A **Csoport hozzáadása** panelen kattintson az **OK** gombra.
13. Az alkalmazás **Hozzárendelések** ablaktábláján kattintson a **Mentés** gombra.

Ezzel az alkalmazást hozzárendelte a kiválasztott csoportokhoz. További információt az alkalmazás-hozzárendelések belefoglalásához és kizárásához az [Alkalmazás-hozzárendelések belefoglalása és kizárása](apps-inc-exl-assignments.md) részben talál.

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Alkalmazások hozzárendelési ütközéseinek feloldása

Egyetlen csoportot sem lehet több alkalmazás-hozzárendelési szándéknak megcélozni, azonban ha egy felhasználó vagy egy eszköz több olyan csoport tagja, amely különböző leképezésekkel van társítva, ütközést eredményezhet. Nem ajánlott hozzárendelési ütközéseket létrehozni az alkalmazásokhoz.
Az alábbi táblázatban található információk segítenek megérteni az eredményül kapott szándékot ütközés esetén:

| 1\. csoport hozzárendelési szándéka | 2\. csoport hozzárendelési szándéka | Eredmény |
|-----------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|A felhasználó kötelező|A felhasználó elérhető|Kötelező és elérhető|
|A felhasználó kötelező|Felhasználó eltávolítása|Kötelező|
|A felhasználó elérhető|Felhasználó eltávolítása|Eltávolítás|
|A felhasználó kötelező|Az eszköz kötelező|Mind a két szándék létezik, az Intune Kötelező szándékként kezeli
|A felhasználó kötelező|Eszköz eltávolítása|Mind a két szándék létezik, az Intune a Kötelezőt oldja fel
|A felhasználó elérhető|Az eszköz kötelező|Mind a két szándék létezik, az Intune a Kötelezőt oldja fel (kötelező és elérhető)
|A felhasználó elérhető|Eszköz eltávolítása|Mind a két szándék létezik, az Intune az Elérhetőt oldja fel.<br><br>Az alkalmazás megjelenik az Intune Céges portálon.<br><br>Ha az alkalmazás már telepítve van (korábbi szándékkal kötelezőként) a rendszer eltávolítja az alkalmazást.<br><br>Ha a felhasználó a **Telepítés a céges portálról** lehetőséget választja, az alkalmazás telepítve lesz, és a rendszer az eltávolítás szándékát veti el.|
|Felhasználó eltávolítása|Az eszköz kötelező|Mind a két szándék létezik, az Intune a Kötelezőt oldja fel|
|Felhasználó eltávolítása|Eszköz eltávolítása|Mind a két szándék létezik, az Intune az Eltávolítást oldja fel|
|Az eszköz kötelező|Eszköz eltávolítása|Kötelező|
|A felhasználó kötelező és elérhető|A felhasználó elérhető|Kötelező és elérhető|
|A felhasználó kötelező és elérhető|Felhasználó eltávolítása|Kötelező és elérhető|
|A felhasználó kötelező és elérhető|Az eszköz kötelező|Mind a két szándék, a Kötelező és az Elérhető egyaránt létezik
|A felhasználó kötelező és elérhető|Eszköz eltávolítása|Mind a két szándék létezik, az Intune a Kötelezőt oldja fel (kötelező és elérhető)
|A felhasználó regisztráció nélkül elérhető|A felhasználó kötelező és elérhető|Kötelező és elérhető
|A felhasználó regisztráció nélkül elérhető|A felhasználó kötelező|Kötelező
|A felhasználó regisztráció nélkül elérhető|A felhasználó elérhető|Elérhető|
|A felhasználó regisztráció nélkül elérhető|Az eszköz kötelező|Kötelező és Regisztráció nélkül elérhető|
|A felhasználó regisztráció nélkül elérhető|Eszköz eltávolítása|Eltávolítás és Regisztráció nélkül elérhető.<br><br>Ha a felhasználó nem az Intune Céges portálról telepítette az alkalmazást, akkor a rendszer az eltávolítást veszi figyelembe.<br><br>Ha a felhasználó az Intune Céges portálról telepíti az alkalmazást, akkor a rendszer a telepítést részesíti előnyben az eltávolítással szemben.|

> [!NOTE]
> Csak áruházból származó felügyelt iOS-alkalmazások esetén, ha ezeket az alkalmazásokat a Microsoft Intune-ban **kötelezőként** rendeli hozzá, akkor a **Kötelező** és az **Elérhető** szándék automatikusan egyaránt fog vonatkozni rájuk.<br><br>
> A kötelező hozzárendelési szándékkal célzott (nem iOS VPP) iOS Store-alkalmazások az eszköz bejelentkezésekor kikényszerítetten hozzá lesznek rendelve az eszközhöz, és megjelennek a Céges portál alkalmazásban is.<br><br>
> Ha ütközés lép fel az **eltávolításkor az eszköz eltávolításakor** , az alkalmazás nem lesz eltávolítva az eszközről, ha az eszköz már nem lett felügyelve.

## <a name="managed-google-play-app-deployment-to-unmanaged-devices"></a>Felügyelt Google Play-alkalmazások telepítése nem felügyelt eszközökre
A nem regisztrált app Protection-szabályzatok (APP-WE) üzembe helyezési forgatókönyve nélküli Android-eszközök esetén a felügyelt Google Play használatával telepítheti az áruházbeli alkalmazásokat és üzletági (LOB) alkalmazásokat a felhasználók számára. A **beléptetéssel vagy anélkül elérhető** felügyelt Google Play-alkalmazások a Play áruház alkalmazásban jelennek meg a végfelhasználó eszközén, és nem a céges portál alkalmazásban. A végfelhasználó megkeresi és telepíti az ilyen módon üzembe helyezett alkalmazásokat a Play alkalmazásból. Mivel az alkalmazások a felügyelt Google Play áruházból települnek, a végfelhasználónak nem kell módosítania az eszköz beállításait, hogy az alkalmazás telepítése ismeretlen forrásból történjen, ami azt jelenti, hogy az eszközök biztonságosabbak lesznek. Ha az alkalmazás fejlesztője közzétesz egy alkalmazás egy új verzióját, amelyet a felhasználó eszközére telepített, akkor az alkalmazást a Play automatikusan frissíti. 

A felügyelt Google Play-alkalmazások nem felügyelt eszközökhöz való hozzárendelésének lépései:

1. Az Intune-bérlő összekötése a felügyelt Google Play szolgáltatással. Ha már megtette ezt az androidos vállalati munkahelyi profil, dedikált vagy teljes körűen felügyelt eszközök kezeléséhez, nem kell újra végrehajtania.
2. Alkalmazások hozzáadása a felügyelt Google Play áruházból az Intune-konzolra.
3. A felügyelt Google Play-alkalmazások a kívánt felhasználói csoportba való **regisztrációval vagy anélkül is elérhetők** . A nem regisztrált eszközök esetében nem támogatottak a **kötelező** és az **eltávolítást** célzó alkalmazások.
4. Rendeljen egy alkalmazás-védelmi szabályzatot a felhasználói csoporthoz.
5. Amikor a felhasználó legközelebb megnyitja a Céges portál alkalmazást, megjelenik egy üzenet, amely jelzi, hogy elérhetők-e alkalmazások a Play Áruház alkalmazásban.  A felhasználó az értesítésre koppintva közvetlenül a Play alkalmazásba helyezheti a vállalati alkalmazásokat, vagy a Play Áruház alkalmazást külön is megnyithatja.
6. A végfelhasználó kiterjesztheti a helyi menüt a Play Áruház alkalmazáson belül, és válthat a személyes Google-fiókja (ahol a személyes alkalmazások láthatók) és a munkahelyi fiókjuk között (ahol megtekintheti őket tároló és LOB-alkalmazások). A végfelhasználók a Play Áruház alkalmazásban az install (telepítés) gombra koppintva telepítik az alkalmazásokat.

Ha az Intune-konzolon kiadja az alkalmazás szelektív törlését, a munkahelyi fiók automatikusan el lesz távolítva a Play Áruház alkalmazásból, és a végfelhasználó ettől kezdve nem látja a munkahelyi alkalmazásokat a Play Áruház app Catalogban. Ha a munkahelyi fiókot eltávolítják egy eszközről, az Play Áruház telepített alkalmazások továbbra is telepítve lesznek az eszközön, és nem lesznek eltávolítva. 

## <a name="app-uninstall-setting-for-ios-managed-apps"></a>Az iOS által felügyelt alkalmazások alkalmazás-eltávolítási beállítása
IOS-eszközök esetén kiválaszthatja, hogy mi történik a felügyelt alkalmazásokkal az eszköz Intune-regisztrációjának törlésével vagy a felügyeleti profil eltávolításával az **eszköz eltávolítási** beállításának eltávolításával. Ez a beállítás csak az eszköz regisztrálását követően érvényes az alkalmazásokra, és az alkalmazások felügyelt vannak telepítve. A beállítás nem konfigurálható webalkalmazásokhoz vagy webes hivatkozásokhoz. 

A beállítás alapértelmezett értékei az új hozzárendelésekhez az alábbiak szerint vannak feltöltve:

|iOS-alkalmazás típusa | Alapértelmezett beállítás az Eltávolítás az eszköz eltávolításakor |
|--------------------|----------------|
| Üzletági alkalmazás | Igen |
| Áruházbeli alkalmazás | Nem |
| VPP-alkalmazás | Nem |
| Beépített alkalmazás | Nem |

>[!NOTE]
>**"Elérhető" hozzárendelési típusok:** Ha ezt a beállítást "elérhető regisztrált eszközökhöz" vagy "a regisztráció nélkül vagy anélkül elérhető" csoportok esetében frissíti, akkor a felügyelt alkalmazással már rendelkező felhasználók nem kapják meg a frissített beállítást, amíg nem szinkronizálják az eszközt az Intune-nal, és nem telepítik újra az alkalmazást. 
>
>**Korábban létező hozzárendelések:** A beállítás bevezetését megelőzően létező hozzárendelések nem módosulnak, és az összes felügyelt alkalmazás el lesz távolítva az eszköz eltávolításáról a felügyelet alól.

## <a name="next-steps"></a>További lépések

Alkalmazás-hozzárendelések figyelésével kapcsolatos további tudnivalókért lásd: [Alkalmazások figyelése](apps-monitor.md).
