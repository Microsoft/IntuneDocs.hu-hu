---
title: Az alkalmazásvédelmi szabályzatok figyelése
titleSuffix: Microsoft Intune
description: Ez a témakör az alkalmazás-védelmi szabályzatok Intune-ban történő figyelését ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 805a1b1145c6b177c83de17de5a2df3efb7380da
ms.sourcegitcommit: 60ed93682a21860e9d99ba1592ede120477f2b4d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72379776"
---
# <a name="how-to-monitor-app-protection-policies"></a>Az alkalmazásvédelmi szabályzatok figyelése
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A [Azure Portal](https://portal.azure.com)Intune app Protection paneljén a felhasználókra alkalmazott Mobile App Management-(MAM-) szabályzatok megfelelőségi állapotát figyelheti. Emellett információkat találhat a MAM-szabályzatok által érintett felhasználókról, a MAM-szabályzatok megfelelőségi állapotáról, valamint a felhasználók által esetlegesen tapasztalt problémákról.

Az alkalmazás-védelmi házirendek három különböző helyen figyelhetők:
- Összesített nézet
- Részletes nézet
- Jelentéskészítés nézet

> [!NOTE]
> További információt az [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](app-protection-policies.md) című cikkben talál.

Az App Protection-adatok megőrzési időtartama 90 nap. Minden olyan alkalmazás-példány, amely az elmúlt 90 napban be van jelölve a MAM-szolgáltatásba, az alkalmazás védelmi állapota jelentés részét képezi. Az *alkalmazás-példány* egy egyedi felhasználó + alkalmazás + eszköz. 

## <a name="summary-view"></a>Összesített nézet

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az összesítő nézet megtekintéséhez az **ügyfélalkalmazások** munkaterhelése területen válassza az alkalmazás **-** **védelmi állapot**lehetőséget.

   ![Képernyőkép az Intune Mobile Application Management panel összefoglalás csempéje](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Hozzárendelt felhasználók**: a vállalat olyan hozzárendelt felhasználóinak teljes száma, akik olyan alkalmazást használnak, amely egy munkahelyi környezetben található házirendhez van társítva, és amely védett és licenccel rendelkezik, valamint a nem védett és a licenccel nem rendelkező hozzárendelt felhasználók számára.
- **Megjelölt felhasználók**: az eszközeivel kapcsolatos problémákat tapasztaló felhasználók száma. A rendszer a feltört (iOS) és a feltört (androidos) eszközöket a **megjelölt felhasználók**alatt jelenti. Ezen kívül a Google biztonság-eszköz igazolási ellenőrzésével megjelölt eszközökkel (ha a rendszergazda bekapcsolja azt) a felhasználók itt jelennek meg. 
- **Potenciálisan ártalmas alkalmazásokkal rendelkező felhasználók**: azon felhasználók száma, akik kártékony alkalmazással rendelkezhetnek a Google Play Protect által észlelt Android-eszközön. 
- **Felhasználói állapot az iOS** -hez és a **felhasználói állapothoz Android**rendszeren: azon felhasználók száma, akik az adott alkalmazáshoz hozzárendelt szabályzattal rendelkeznek a kapcsolódó platformhoz tartozó munkakörnyezetben. Ez az információ a szabályzat által kezelt felhasználók számát, valamint azon felhasználók számát jeleníti meg, akik olyan alkalmazást használnak, amelyet nem a munkahelyi környezetben lévő szabályzat céloz meg. Érdemes megfontolni ezen felhasználók bevonását a szabályzat hatálya alá.
- **Legnépszerűbb védett iOS-alkalmazások**: a leggyakrabban használt iOS-alkalmazások alapján ez az információ a védett és a nem védett iOS-alkalmazások számát jeleníti meg.
- **Legnépszerűbb védett Android-alkalmazások**: a leggyakrabban használt Android-alkalmazások alapján ez az információ a védett és a nem védett Android-alkalmazások számát jeleníti meg.
- **Legfelső szintű konfigurált iOS-alkalmazások regisztráció nélkül**: a nem regisztrált eszközökhöz leggyakrabban használt iOS-alkalmazások alapján ez az információ a konfigurált iOS-alkalmazások számát mutatja.
- **Legfelső szintű konfigurált Android-alkalmazások regisztráció nélkül**: a nem regisztrált eszközök leggyakrabban használt Android-alkalmazásai alapján ez az információ a konfigurált Android-alkalmazások számát mutatja.

    > [!NOTE]
    > Platformonként több szabályzat esetén a felhasználó akkor minősül szabályzat által kezeltnek, ha legalább egy szabályzat hozzá van rendelve.

## <a name="detailed-view"></a>Részletes nézet
Az összefoglalás részletes nézetét a **felhasználói állapot** csempére (az eszköz operációsrendszer-platformja alapján), a **potenciálisan ártalmas alkalmazások** csempére és a **megjelölt felhasználók** csempére kattintva érheti el.

### <a name="user-status"></a>Felhasználó állapota
Itt megkeresheti az adott felhasználókat, és ellenőrizheti a megfelelési állapotukat. Az **Alkalmazásjelentések** panelen a következő információk tekinthetők meg a kiválasztott felhasználóról:
- **Ikon**: megjeleníti, hogy az alkalmazás állapota naprakész-e.
- **Alkalmazás neve**: az alkalmazás neve.
- **Eszköz neve**: a felhasználói fiókhoz társított eszközök.
- **Eszköz típusa**: az eszköz által futtatott eszköz vagy operációs rendszer típusa.
- **Szabályzatok**: az alkalmazáshoz társított szabályzatok.
- **Állapot**:
  - **Beadva:** a szabályzat települt a felhasználónál, és az alkalmazást legalább egyszer már használták a munkahelyi környezetben.
  - **Nincs beadva**: a házirend a felhasználó számára lett telepítve, de az alkalmazást azóta nem használták a munkahelyi környezetben.
- **Utolsó szinkronizálás**: az alkalmazás Intune-nal való legutóbbi szinkronizálásakor. 

>[!NOTE]
> Az **utolsó szinkronizálási** oszlop ugyanazt az értéket jelöli, mint a konzolon belüli felhasználói állapot jelentés és az alkalmazás-védelmi házirend [exportálható. csv-jelentése](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities-to-csv). A különbség a két jelentés értéke közötti szinkronizálás kis késleltetése. 
>
> A legutóbbi szinkronizálásban hivatkozott idő az, amikor az Intune utoljára látta az alkalmazás példányát. Amikor egy felhasználó egy alkalmazást indít el, az a legutóbbi bejelentkezéstől függően értesíti a Intune App Protection szolgáltatást. Tekintse [meg az alkalmazás-védelmi házirend beadásának újrapróbálkozási időpontját](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Ha egy felhasználó nem használta az adott alkalmazást az utolsó beadási időközben (amely általában 30 perc az aktív használat esetén), és elindítja az alkalmazást, akkor:
>
> - Az alkalmazás védelmi szabályzata exportálható. a CSV-jelentés a legújabb időpontban, 1 percen (minimum) és 30 percen belül (maximum) érhető el.
> - A felhasználó állapotáról szóló jelentés a legújabb időpontban azonnal elérhető.
>
> Tegyük fel például, hogy egy megcélozt és licencelt felhasználó, aki 12:00 ÓRAKOR indít el egy védett alkalmazást:
> - Ha első alkalommal jelentkezik be, az azt jelenti, hogy a felhasználó korábban már ki lett jelentkezve, és nem rendelkezik az Intune-beli alkalmazás-példányok regisztrálásával. Miután a felhasználó bejelentkezett, a felhasználó új alkalmazás-példány regisztrációt kap, és azonnal bejelentkezhet (a későbbi bejelentkezések során a korábban felsorolt késésekkel). Így az utolsó szinkronizálási idő 12:00 PM a felhasználói állapot jelentésben, és 12:01 PM (vagy 12:30 PM) az alkalmazás-védelmi házirend jelentésében. 
> - Ha a felhasználó éppen csak elindítja az alkalmazást, a jelentett Legutóbbi szinkronizálási idő attól függ, hogy a felhasználó utoljára be van-e jelölve.


A felhasználóhoz tartozó jelentések megtekintéséhez kövesse az alábbi lépéseket:

1. Felhasználó kiválasztásához válassza a **felhasználói állapot** összegzése csempét.

    ![Képernyőkép az Intune Mobile Application Management összefoglaló csempéről](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. Az **alkalmazás-jelentési** panelen válassza a **felhasználó kiválasztása** lehetőséget Azure Active Directory felhasználó kereséséhez.

    ![Képernyőkép a felhasználó kiválasztása lehetőségről az alkalmazás jelentéskészítési paneljén](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Válassza ki a listából a felhasználót. Megjelennek a felhasználó megfelelési állapotára vonatkozó információk.

>[!NOTE]
> Ha a keresett felhasználók nem rendelkeznek telepített MAM-szabályzattal, egy üzenet jelenik meg, amely arról tájékoztatja, hogy a felhasználóra nem vonatkozik egyetlen MAM-szabályzat sem.Ha a keresett felhasználók nem rendelkeznek telepített MAM-szabályzattal, egy üzenet jelenik meg, amely arról tájékoztatja, hogy a felhasználóra nem vonatkozik egyetlen MAM-szabályzat sem.

### <a name="flagged-users"></a>Megjelölt felhasználók
A részletes nézetben látható a hibaüzenet, annak az alkalmazásnak a neve, amelynek a használata közben fellépett a hiba, az eszközök érintett operációsrendszer-platformja, valamint egy időbélyeg. A hiba általában a jailbroken (iOS) vagy a feltört (androidos) eszközökön van. Az "biztonság Device igazolás" feltételes indítási ellenőrzés által megjelölt eszközökkel rendelkező felhasználók itt is a Google által jelentett oknál fogva jelennek meg. Ahhoz, hogy egy felhasználó el legyen távolítva a jelentésből, meg kell változtatnia az eszköz állapotát, ami a következő legfelső szintű észlelési ellenőrzés (vagy a jailbreak-ellenőrzés/biztonság-ellenőrzés) után történik, amelyeknek pozitív eredményt kell jelenteniük. Ha az eszköz valóban szervizelésre kerül, a panel újratöltése után a megjelölt felhasználók jelentésének frissítése is megtörténik.

### <a name="users-with-potentially-harmful-apps"></a>Potenciálisan ártalmas alkalmazásokat használó felhasználók
A részletes nézet a következőket jeleníti meg:

- A felhasználó.
- Az alkalmazáscsomag azonosítója.
- Ha az alkalmazás MAM-kompatibilis.
- A fenyegetés kategóriája.
- Az e-mailt.
- Az eszköz neve.
- Egy időbélyegző.

Az alkalmazások feltételes indítási ellenőrzésének megkövetelése az eszközökön a **veszélyforrások vizsgálatát megkövetelő** eszközökkel a Google által jelentett veszélyforrások kategóriáját kell jelenteni. Ha az Intune-on keresztül üzembe helyezett alkalmazások vannak felsorolva, lépjen kapcsolatba az alkalmazás fejlesztővel, vagy távolítsa el az alkalmazást a felhasználókhoz való hozzárendeléshez. 

## <a name="reporting-view"></a>Jelentéskészítés nézet

Ugyanezeket a jelentéseket az **app Protection állapota** panel tetején tekintheti meg.

> [!NOTE]
> Az Intune további eszköz-jelentési mezőket biztosít, beleértve az alkalmazás regisztrációs AZONOSÍTÓját, az Android-gyártót, a modellt és a biztonsági javítás verzióját, valamint az iOS-modellt is. Az Intune-ban az **ügyfélalkalmazások**kiválasztásával érheti el ezeket a mezőket  > **app protection-állapot** > **app Protection-jelentés: iOS, Android**. Emellett ezek a paraméterek segítséget nyújtanak az eszköz gyártójának (Android) **engedélyezési** listájának, az eszköz modell **engedélyezési** listájának (Android és iOS) és az androidos biztonsági javítás minimális verziójának beállításának konfigurálásában. 

További jelentések érhetők el a MAM-szabályzat megfelelőségi állapotának elősegítése érdekében. A jelentések megtekintéséhez válassza az **ügyfélalkalmazások** > **App Protection status** > **jelentések**elemet. 

A **jelentések** panel számos jelentést biztosít a felhasználók és az alkalmazások alapján, beleértve a következőket:

- **Felhasználói jelentés**: Ez a jelentés a fenti [Részletes nézet](app-protection-policies-monitor.md#detailed-view) szakaszban található **felhasználói állapot** jelentésében megjelenő információkat ismerteti.

- **Alkalmazás-jelentés**: a platform és az alkalmazás kiválasztása mellett ez a jelentés két különböző alkalmazás-védelmi állapotot biztosít, amelyeket a jelentés létrehozása előtt választhat ki. Az állapotok **védhetők** **vagy nem védettek**.

  - Felügyelt MAM-tevékenységekre vonatkozó felhasználói állapot (**védett**): Ez a jelentés felhasználónkénti alapon ismerteti az egyes felügyelt MAM-alkalmazások tevékenységeit. A MAM-szabályzatok által megcélozott összes alkalmazást megjeleníti az egyes felhasználókra vonatkozóan, valamint az egyes alkalmazások állapotát a MAM-szabályzatokkal bejelentkezve. A jelentés a MAM-szabályzattal megcélozott alkalmazások állapotát is tartalmazza, de soha nem volt bejelölve.
  - Nem felügyelt MAM-tevékenységekre vonatkozó felhasználói állapot (nem**védett**): Ez a jelentés a jelenleg nem felügyelt MAM-kompatibilis alkalmazások tevékenységeit ismerteti, felhasználónkénti alapon. Ez az alábbiak miatt fordulhat elő:
    - Ezeket az alkalmazásokat egy olyan felhasználó vagy alkalmazás használja, amelyet jelenleg nem a MAM-szabályzat céloz meg.
    - Minden alkalmazás érvényesítve lett, de nincsenek rájuk vonatkozó MAM-szabályzatok.

    ![Képernyőfelvétel egy felhasználó alkalmazás-jelentési paneljéről három alkalmazás részleteivel](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Felhasználói konfigurációs jelentés**: a kiválasztott felhasználó alapján ez a jelentés a felhasználó által fogadott alkalmazás-konfigurációk részleteit tartalmazza.
- **Alkalmazás-konfigurációs jelentés**: a kiválasztott platformon és alkalmazáson alapuló alap, ez a jelentés részletesen ismerteti, hogy mely felhasználók kapott konfigurációkat a kiválasztott alkalmazáshoz.
- **Alkalmazás-tanulási jelentés Windows Information Protectionhoz**: Ez a jelentés azt jeleníti meg, hogy mely alkalmazások próbálnak meg határokon átívelő házirendeket használni.
- A **Windows Information Protection webhelyének megismerése**: Ez a jelentés azt jeleníti meg, hogy mely webhelyek próbálnak meg határokon átívelő házirendeket használni.

## <a name="table-grouping"></a>Táblacsoportosítás

Az **app Protection felhasználói jelentés** adatainak megjelenítése után az alábbi módon összesítheti az adatokat:

- **Érvényesítési eredmény**: az alkalmazások az alkalmazás védelmi állapota szerint vannak csoportosítva, ami "hiba", "figyelmeztetés" vagy "sikeres" lehet.
- **Alkalmazás neve**: az adatok a tényleges alkalmazás neve szerint vannak csoportosítva. Az állapot "sikertelen", "figyelmeztetés" vagy "sikeres" lehet.

## <a name="export-app-protection-activities"></a>Alkalmazás-védelmi tevékenységek exportálása

Az alkalmazásvédelmi szabályzatokkal kapcsolatos összes tevékenységet egyetlen .csv-fájlba exportálhatja. Ez hasznos lehet az összes, a felhasználók felől jelentett alkalmazásvédelmi állapot elemzésében.

Az App Protection-jelentés létrehozásához kövesse az alábbi lépéseket:

1. Az Intune-os mobilalkalmazás-kezelés paneljén válassza az **Alkalmazásvédelmi jelentés** lehetőséget.

    ![Képernyőkép az App Protection letöltési hivatkozásáról](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Válassza az **Igen** lehetőséget a jelentés mentéséhez, majd válassza a **Mentés másként**lehetőséget. Válassza ki azt a mappát, amelybe menteni szeretné a jelentést.

    ![Képernyőkép a Jelentés mentése jóváhagyó mezőről](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>További információ
- [iOS-alkalmazások közti adatátvitel kezelése](data-transfer-between-apps-manage-ios.md)
- [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-android.md)
- [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-ios.md)
