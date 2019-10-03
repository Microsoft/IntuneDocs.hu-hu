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
ms.openlocfilehash: 0b4ab3369f241c9f33d4e0bddfd0dcf98c8ab915
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830597"
---
# <a name="how-to-monitor-app-protection-policies"></a>Az alkalmazásvédelmi szabályzatok figyelése
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A [Azure Portal](https://portal.azure.com)Intune app Protection paneljén a felhasználókra alkalmazott Mobile App Management-(MAM-) szabályzatok megfelelőségi állapotát figyelheti. Emellett információkat találhat a MAM-szabályzatok által érintett felhasználókról, a MAM-szabályzatok megfelelőségi állapotáról, valamint a felhasználók által esetlegesen tapasztalt problémákról.

Az alkalmazás-védelmi házirendek három különböző helyen figyelhetők:
- Összefoglalás megtekintése
- Részletes nézet
- Jelentéskészítés nézet

> [!NOTE]
> Az alkalmazásvédelmi szabályzatok létrehozásával kapcsolatban további információt az [alkalmazásvédelmi szabályzatok létrehozásával és hozzárendelésével](app-protection-policies.md) foglalkozó cikkben talál.

Az App Protection-adatok megőrzési időtartama 90 nap. A MAM-szolgáltatásba az elmúlt 90 napban bejelentkezett összes alkalmazás-példány szerepelni fog az alkalmazás-védelmi állapot jelentésében. Az alkalmazás-példány egy egyedi felhasználó + alkalmazás + eszköz. 

## <a name="summary-view"></a>Összefoglalás megtekintése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **ügyféloldali alkalmazások** munkafolyamatban válassza az **alkalmazás-védelmi állapot** lehetőséget a **figyelő** szakaszban az összegző nézet megtekintéséhez:

![Az Intune mobilalkalmazás-kezelés panel Összefoglalás csempéje](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Hozzárendelt felhasználók**: A vállalat olyan hozzárendelt felhasználóinak teljes száma, akik egy munkahelyi környezetben egy házirendhez társított alkalmazást használnak, és amelyek védettek és licenccel rendelkeznek, valamint a nem védett és a licenccel nem rendelkező hozzárendelt felhasználók.
- **Megjelölt felhasználók**: A problémákat tapasztaló felhasználók száma. A rendszer a feltört (iOS) és a feltört (androidos) eszközöket a **megjelölt felhasználók**alatt jelenti. Itt jelennek meg azok a felhasználók, akik rendelkeznek a Google biztonság-eszköz igazolási ellenőrzésével (ha a rendszergazda bekapcsolva) megjelölt eszközökkel. 
- **Potenciálisan ártalmas alkalmazásokkal rendelkező felhasználók**: Azon felhasználók száma, akik kártékony alkalmazással rendelkezhetnek a Google Play Protect által észlelt Android-eszközön. 
- **Felhasználói állapot iOS** -hez és **felhasználói állapot az Androidhoz**: Azon felhasználók száma, akik egy olyan alkalmazást használnak, amely a kapcsolódó platform munkahelyi környezetében hozzárendelt szabályzattal rendelkezik. Ez az információ a szabályzat által kezelt felhasználók számát, valamint azon felhasználók számát jeleníti meg, akik olyan alkalmazást használnak, amelyet nem a munkahelyi környezetben lévő szabályzat céloz meg. Érdemes megfontolni ezen felhasználók bevonását a szabályzat hatálya alá.
- **Legnépszerűbb védett iOS-alkalmazások**: A leggyakrabban használt iOS-alkalmazások alapján ez az információ a védett és a nem védett iOS-alkalmazások számát jeleníti meg.
- **Legnépszerűbb védett Android-alkalmazások**: A leggyakrabban használt Android-alkalmazások alapján ez az információ a védett és a nem védett Android-alkalmazások számát jeleníti meg.
- **Leggyakrabban konfigurált iOS-alkalmazások regisztráció nélkül**: A nem regisztrált eszközökhöz leggyakrabban használt iOS-alkalmazások alapján ez az információ a konfigurált iOS-alkalmazások számát mutatja.
- **Legfelső szintű konfigurált Android-alkalmazások regisztráció nélkül**: A nem regisztrált eszközök leggyakrabban használt Android-alkalmazásai alapján ez az információ a konfigurált Android-alkalmazások számát mutatja.

    > [!NOTE]
    > Ha platformon több szabályzatot is tartalmaz, akkor a felhasználókat a házirend felügyeli, ha legalább egy házirend hozzá van rendelve.

## <a name="detailed-view"></a>Részletes nézet
Az összefoglalás részletes nézetét a **felhasználói állapot** csempére (az eszköz operációsrendszer-platformja alapján), a **potenciálisan ártalmas alkalmazásokkal rendelkező felhasználókra** és a **megjelölt felhasználók** csempére kattintva érheti el.

### <a name="user-status"></a>Felhasználó állapota
Itt megkeresheti az adott felhasználókat, és ellenőrizheti a megfelelési állapotukat. Az **Alkalmazásjelentések** panelen a következő információk tekinthetők meg a kiválasztott felhasználóról:
- **Ikon**: Megjeleníti, hogy az alkalmazás állapota naprakész-e.
- **Alkalmazás neve**: Az alkalmazás neve.
- **Eszköz neve**: A felhasználói fiókhoz társított eszközök.
- **Eszköz típusa**: Az eszköz által futtatott eszköz vagy operációs rendszer típusa.
- **Szabályzatok**: Az alkalmazáshoz társított szabályzatok.
- **Állapot**:
  - **Bejelölve**: A házirend a felhasználó számára lett telepítve, és az alkalmazást legalább egyszer használták a munkahelyi környezetben.
  - **Nincs bejelölve**: A házirend a felhasználó számára lett telepítve, de az alkalmazást azóta nem használták a munkahelyi környezetben.
- **Utolsó szinkronizálás**: Az alkalmazás az Intune-nal való legutóbbi szinkronizálása után. 

>[!NOTE]
> A "Last Sync" oszlop ugyanazt az értéket jelöli a konzolon belüli felhasználói állapot jelentésben és az alkalmazás-védelmi házirend [exportálható. csv-jelentésében](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities-to-csv)is. A különbség a két jelentés értéke közötti szinkronizálás kis késleltetése. 
>
> Az "utolsó szinkronizálás" során hivatkozott idő az, amikor az Intune utoljára látta az "app instance" kifejezést. Az alkalmazás-példány az App + User + eszköz egyedi kombinációja. Amikor egy végfelhasználó elindít egy alkalmazást, előfordulhat, hogy az utolsó beadástól függően nem kommunikál a Intune App Protection szolgáltatással az adott indítási időpontban. Ez a dokumentáció segít tisztázni [az App Protection-házirend beadásának újrapróbálkozási időpontját](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Tehát ha egy végfelhasználó nem használta az adott alkalmazást az utolsó beadási intervallumban (amely általában 30 perc az aktív használat esetén), és elindítja az alkalmazást, akkor:
>
> - Az alkalmazás védelmi szabályzata exportálható. a CSV-jelentés a legmodernebb időt 1 percen belül (szokásos; minimum) – 30 percre (az Intune-jelentéskészítés által használt SQL-összesítés által ténylegesen megadott maximális SLA-ra vonatkozik).
> - A felhasználó állapota jelentés a legújabb időpontban azonnal elérhető lesz.
>
> Tegyük fel például, hogy egy megcélozt és egy licenccel rendelkező végfelhasználót, amely 12:00 ÓRAKOR indít el egy védett alkalmazást:
> - Ha első alkalommal jelentkezik be, az azt jelenti, hogy a végfelhasználó kijelentkezett (nem aktív használat), ami azt jelenti, hogy az Intune-ban nem voltak alkalmazás-példányok regisztrálása. Ha bejelentkeznek, egy új alkalmazás-példány regisztrációt kapnak, és azonnal be kell jelentkezniük, amíg nincs kapcsolati probléma; a későbbi bejelentkezések során a fent felsorolt késések is megegyeznek. Így az utolsó szinkronizálás ideje 12:00 PM-ként jelent jelentést a felhasználói állapot jelentésében, és 12:01 PM (vagy 12:30 PM legrosszabb esetben) alkalmazás-védelmi házirend jelentést. 
> - Ha csak elindítják az alkalmazást, a jelentett utolsó szinkronizálási idő attól függ, hogy mikor utoljára bejelentkeznek.


A felhasználóhoz tartozó jelentések megtekintéséhez kövesse az alábbi lépéseket:

1. Felhasználó kiválasztásához válassza a **felhasználói állapot** összegzése csempét.

    ![Képernyőkép az Intune Mobile Application Management összefoglaló csempéről](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. A megjelenő **Alkalmazásjelentések** panelen válassza a **Felhasználó kijelölése** lehetőséget, és keresse meg a kívánt Azure Active Directory-felhasználót.

    ![Képernyőkép a felhasználó kiválasztása lehetőségről az alkalmazás jelentéskészítési paneljén](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Válassza ki a listából a felhasználót. Megjelennek a felhasználó megfelelési állapotára vonatkozó információk.

>[!NOTE]
> Ha a keresett felhasználók nem rendelkeznek telepített MAM-szabályzattal, egy üzenet jelenik meg, amely arról tájékoztatja, hogy a felhasználóra nem vonatkozik egyetlen MAM-szabályzat sem.Ha a keresett felhasználók nem rendelkeznek telepített MAM-szabályzattal, egy üzenet jelenik meg, amely arról tájékoztatja, hogy a felhasználóra nem vonatkozik egyetlen MAM-szabályzat sem.

### <a name="flagged-users"></a>Megjelölt felhasználók
A részletes nézetben látható a hibaüzenet, annak az alkalmazásnak a neve, amelynek a használata közben fellépett a hiba, az eszközök érintett operációsrendszer-platformja, valamint egy időbélyeg. A "biztonság-eszköz igazolása" feltételes indítási ellenőrzés által megjelölt eszközökkel rendelkező felhasználók itt jelennek meg a Google által jelentett okból.

### <a name="users-with-potentially-harmful-apps"></a>Potenciálisan ártalmas alkalmazásokat használó felhasználók
A részletes nézetben látható a felhasználó, az alkalmazáscsomag azonosítója, ha az alkalmazás MAM engedélyezve van, a veszélyforrások kategóriája, az e-mail, az eszköz neve és az időbélyegző. A "veszélyforrások vizsgálatának megkövetelése az alkalmazásokban" feltételes indítási ellenőrzésre megjelölt eszközökkel rendelkező felhasználók itt jelennek meg a veszélyforrások kategóriájában, amelyet a Google jelentett. Ha az Intune-on keresztül üzembe helyezett alkalmazások vannak felsorolva, lépjen kapcsolatba az alkalmazás fejlesztővel, és/vagy távolítsa el az alkalmazást a végfelhasználók számára. 

## <a name="reporting-view"></a>Jelentéskészítés nézet

Ugyanezeket a jelentéseket az **app Protection állapota** panel tetején tekintheti meg.

> [!NOTE]
> Az Intune további eszköz-jelentési mezőket biztosít, beleértve az alkalmazás regisztrációs azonosítóját, az Android-gyártót, a modellt és a biztonsági javítás verzióját, valamint az iOS-modellt is. Az Intune-ban ezek a mezők az **ügyfélalkalmazások** > **app Protection állapotának** kiválasztásával és az App Protection-jelentés kiválasztásával érhetők el **: iOS, Android**. Emellett ezek a paraméterek segítségével konfigurálja a **engedélyezése** lista az eszköz gyártója (Android), a **engedélyezése** lista az eszköz modellje (Android és iOS) és a minimális Android biztonsági javítási szintnek verzió beállítását. 

További jelentések érhetők el a MAM-szabályzat megfelelőségi állapotának elősegítése érdekében. A jelentések megtekintéséhez válassza az **ügyfélalkalmazások** > **app Protection-állapotjelentések** > **elemet.** 

A **jelentések** panel számos jelentést biztosít a felhasználók és az alkalmazások alapján, beleértve a következőket:


- **Felhasználói jelentés**: Ez a jelentés a fenti [Részletes nézet](app-protection-policies-monitor.md#detailed-view) szakaszban található **felhasználói állapot** jelentésében megjelenő információkat ismerteti.

- **Alkalmazás jelentése**: A platform és az alkalmazás kiválasztása mellett ez a jelentés két különböző app Protection-állapotot biztosít, amelyeket a jelentés létrehozása előtt választhat ki. Az állapotok **védhetők** **vagy nem védettek**.

  - Felügyelt MAM-tevékenységekre vonatkozó felhasználói állapot (**védett**): Ez a jelentés az egyes felügyelt MAM-alkalmazások tevékenységeit ismerteti felhasználónkénti alapon. Megjelenik benne minden olyan alkalmazás az egyes felhasználókra vonatkozóan, melyekre MAM-szabályzatok lettek érvényesítve, illetve az egyes alkalmazások állapotának felbontása aszerint, hogy az adott alkalmazásra lettek-e érvényesítve MAM-szabályzatok, vagy vonatkozik rá egy MAM-szabályzat, de az nem lett érvényesítve az alkalmazásra.
  - Nem felügyelt MAM-tevékenységekre vonatkozó felhasználói állapot (nem**védett**): Ez a jelentés a jelenleg nem felügyelt MAM-kompatibilis alkalmazások tevékenységeit ismerteti, felhasználónkénti alapon. Ez a következő okokból fordulhat elő:
    - Ezeket az alkalmazásokat egy olyan felhasználó vagy alkalmazás használja, akire vagy amelyre jelenleg nem vonatkozik MAM-szabályzat.
    - Minden alkalmazás érvényesítve lett, de nincsenek rájuk vonatkozó MAM-szabályzatok.

    ![Képernyőkép egy felhasználó alkalmazás-jelentési paneljéről 3 alkalmazás részleteivel](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Felhasználói konfigurációs jelentés**: A kiválasztott felhasználó alapján ez a jelentés részletesen ismerteti a felhasználó által fogadott alkalmazások konfigurációit.
- **Alkalmazás-konfigurációs jelentés**: A kiválasztott platformon és alkalmazáson alapuló alap a jelentés részletesen ismerteti, hogy mely felhasználók kapott konfigurációkat a kiválasztott alkalmazáshoz.
- **Alkalmazás-tanulási jelentés Windows Information Protectionhoz**: Ez a jelentés azt jeleníti meg, hogy mely alkalmazások próbálnak meg határokon átívelő házirendeket használni.
- **A Windows Information Protection webhelyének megismerése**: Ez a jelentés azt jeleníti meg, hogy mely webhelyek próbálnak meg határokon átívelő házirendeket használni.

## <a name="table-grouping"></a>Táblacsoportosítás

Miután megjelenik az **app Protection felhasználói jelentéseinek** adatainak megjelenítése, a következők szerint összesítheti az adatokat:

- **Érvényesítési eredmény:** Az alkalmazás az App Protection állapota szerint csoportosítva jeleníti meg az adathalmazt, ami sikertelen, figyelmeztetés vagy sikeres lehet.
- **Alkalmazás neve:** Az adatok az alkalmazások (a tényleges alkalmazás neve) szerint csoportosított adatokat jelenítenek meg, a hiba, a figyelmeztetés vagy a siker alapján.

## <a name="export-app-protection-activities-to-csv"></a>Az alkalmazásvédelmi tevékenységek exportálása CSV-fájlba

Az összes alkalmazás-védelmi házirend tevékenységét egyetlen *. csv* fájlba exportálhatja. Ez hasznos lehet az összes, a felhasználók felől jelentett alkalmazásvédelmi állapot elemzésében.

Az alkalmazásvédelmi jelentés létrehozásához kövesse az alábbi lépéseket:

1. Az Intune-os mobilalkalmazás-kezelés paneljén válassza az **Alkalmazásvédelmi jelentés** lehetőséget.

    ![Képernyőkép az App Protection letöltési hivatkozásáról](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Válassza az **Igen** lehetőséget a jelentés mentéséhez, majd válassza a **Mentés másként** lehetőséget, és válassza ki azt a mappát, amelybe menteni szeretné a jelentést.

    ![Képernyőkép a Jelentés mentése jóváhagyó mezőről](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Lásd még:
- [iOS-alkalmazások közti adatátvitel kezelése](data-transfer-between-apps-manage-ios.md)
- [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-android.md)
- [Milyen hatással vannak az iOS-es alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-ios.md)
