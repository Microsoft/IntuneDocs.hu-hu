---
title: Az alkalmazásvédelmi szabályzatok figyelése
titleSuffix: Microsoft Intune
description: Ez a témakör az alkalmazás-védelmi szabályzatok Intune-ban történő figyelését ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d2902c876fab12c1ba1e45783327f1ea08ab4d8
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414659"
---
# <a name="how-to-monitor-app-protection-policies"></a>Az alkalmazásvédelmi szabályzatok figyelése
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A [Azure Portal](https://portal.azure.com)Intune app Protection paneljén a felhasználókra alkalmazott alkalmazás-védelmi szabályzatok állapotát figyelheti. Emellett információkat találhat az alkalmazás-védelmi szabályzatok által érintett felhasználókról, a szabályzatok megfelelőségi állapotáról, valamint a felhasználók által esetlegesen tapasztalt problémákról.

Az alkalmazás-védelmi házirendek három különböző helyen figyelhetők:
- Összesített nézet
- Részletes nézet
- Jelentéskészítés nézet

Az App Protection-adatok megőrzési időtartama 90 nap. Minden olyan alkalmazás-példány, amely az Intune szolgáltatásba bejelentkezett az elmúlt 90 napon belül, az alkalmazás védelmi állapota jelentés részét képezi. Az *alkalmazás-példány* egy egyedi felhasználó + alkalmazás + eszköz. 

> [!NOTE]
> További információt az [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](app-protection-policies.md) című cikkben talál.

## <a name="summary-view"></a>Összesített nézet

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza az **alkalmazások** > **monitor** > **app Protection állapota**lehetőséget.

   ![Képernyőkép az Intune Mobile Application Management panel összefoglalás csempéje](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Hozzárendelt felhasználók**: a vállalat olyan hozzárendelt felhasználóinak teljes száma, akik olyan alkalmazást használnak, amely egy munkahelyi környezetben található házirendhez van társítva, és amely védett és licenccel rendelkezik, valamint a nem védett és a licenccel nem rendelkező hozzárendelt felhasználók számára.
- **Megjelölt felhasználók**: az eszközeivel kapcsolatos problémákat tapasztaló felhasználók száma. A rendszer a feltört (iOS) és a feltört (androidos) eszközöket a **megjelölt felhasználók**alatt jelenti. Ezen kívül a Google biztonság-eszköz igazolási ellenőrzésével megjelölt eszközökkel (ha a rendszergazda bekapcsolja azt) a felhasználók itt jelennek meg. 
- **Potenciálisan ártalmas alkalmazásokkal rendelkező felhasználók**: azon felhasználók száma, akik kártékony alkalmazással rendelkezhetnek a Google Play Protect által észlelt Android-eszközön. 
- **Felhasználói állapot az iOS** -hez és a **felhasználói állapothoz Android**rendszeren: azon felhasználók száma, akik az adott alkalmazáshoz hozzárendelt szabályzattal rendelkeznek a kapcsolódó platformhoz tartozó munkakörnyezetben. Ez az információ a szabályzat által kezelt felhasználók számát, valamint azon felhasználók számát jeleníti meg, akik olyan alkalmazást használnak, amelyet nem a munkahelyi környezetben lévő szabályzat céloz meg. Érdemes megfontolni ezen felhasználók bevonását a szabályzat hatálya alá.
- **Legnépszerűbb védett iOS-/iPadOS-alkalmazások** és **legnépszerűbb védett Android-alkalmazások**: a leggyakrabban használt iOS-/iPadOS-és Android-alkalmazások alapján ez az információ a védett és a nem védett alkalmazások platformon alapuló számát jeleníti meg.
- **Top-konfigurált iOS-/iPadOS-alkalmazások** regisztráció nélkül, és a **legfelső szintű konfigurált Android-alkalmazások regisztráció nélkül**: a nem regisztrált eszközökön a leggyakrabban használt iOS-/iPadOS-és Android-alkalmazások esetében ez az információ a konfigurált alkalmazások számát mutatja platform (például az alkalmazás-konfigurációs házirend használatával).

    > [!NOTE]
    > Platformonként több szabályzat esetén a felhasználó akkor minősül szabályzat által kezeltnek, ha legalább egy szabályzat hozzá van rendelve.

## <a name="detailed-view"></a>Részletes nézet
Az összefoglalás részletes nézetét kiválasztva megtekintheti a **megjelölt felhasználók** csempét, valamint az **esetlegesen ártalmas alkalmazások csempét használó felhasználókat** .

### <a name="flagged-users"></a>Megjelölt felhasználók
A részletes nézetben látható a hibaüzenet, annak az alkalmazásnak a neve, amelynek a használata közben fellépett a hiba, az eszközök érintett operációsrendszer-platformja, valamint egy időbélyeg. A hiba általában a jailbroken (iOS) vagy a feltört (androidos) eszközökön van. Az "biztonság Device igazolás" feltételes indítási ellenőrzés által megjelölt eszközökkel rendelkező felhasználók itt is a Google által jelentett oknál fogva jelennek meg. Ahhoz, hogy egy felhasználó el legyen távolítva a jelentésből, meg kell változtatnia az eszköz állapotát, ami a következő legfelső szintű észlelési ellenőrzés (vagy a jailbreak-ellenőrzés/biztonság-ellenőrzés) után történik, amelyeknek pozitív eredményt kell jelenteniük. Ha az eszköz valóban szervizelve van, a megjelölt felhasználók jelentésének frissítése a panel újrabetöltésekor fog történni.

### <a name="users-with-potentially-harmful-apps"></a>Potenciálisan ártalmas alkalmazásokat használó felhasználók
Az alkalmazások feltételes indítási ellenőrzésének megkövetelése az eszközökön a **veszélyforrások vizsgálatát megkövetelő** eszközökkel a Google által jelentett veszélyforrások kategóriáját kell jelenteni. Ha az Intune-on keresztül üzembe helyezett alkalmazások vannak felsorolva, lépjen kapcsolatba az alkalmazás fejlesztővel, vagy távolítsa el az alkalmazást a felhasználókhoz való hozzárendeléshez. A részletes nézet a következőket jeleníti meg:

- **Felhasználó**: a felhasználó neve.
- **ALKALMAZÁSCSOMAG azonosítója**: az Android operációs rendszer egyedi módon határozza meg az alkalmazást.
- **Ha az alkalmazás MAM-kompatibilis**: függetlenül attól, hogy az alkalmazás üzembe helyezése Microsoft Intuneon keresztül történik-e. 
- A **fenyegetés kategóriája**: az alkalmazáshoz tartozó Google által meghatározott veszélyforrások kategóriája. 
- **E-mail**: a felhasználó e-mail-címe.
- **Eszköznév**: a felhasználói fiókhoz társított összes eszköz neve.
- **Egy**időbélyegző: ez az utolsó szinkronizálás dátuma, amelyet a Google Microsoft Intune a potenciálisan ártalmas alkalmazásokkal kapcsolatban.

## <a name="reporting-view"></a>Jelentéskészítés nézet

Ugyanezeket a jelentéseket az **app Protection állapota** ablaktábla tetején tekintheti meg. A jelentések megtekintéséhez válassza az **alkalmazások** > az **App Protection állapota** > a **jelentések**elemet. A **jelentések** ablaktábla számos jelentést biztosít a felhasználók és az alkalmazások alapján, beleértve a következőket:

### <a name="user-report"></a>Felhasználói jelentés
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
> Az **utolsó szinkronizálási** oszlop ugyanazt az értéket jelöli, mint a konzolon belüli felhasználói állapot jelentés és az alkalmazás-védelmi házirend [exportálható. csv-jelentése](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities). A különbség a két jelentés értéke közötti szinkronizálás kis késleltetése. 
>
> A legutóbbi szinkronizálásban hivatkozott idő az, amikor az Intune utoljára látta az alkalmazás példányát. Amikor egy felhasználó egy alkalmazást indít el, az a legutóbbi bejelentkezéstől függően értesíti a Intune App Protection szolgáltatást. Tekintse [meg az alkalmazás-védelmi házirend beadásának újrapróbálkozási időpontját](~/apps/app-protection-policy-delivery.md). Ha egy felhasználó nem használta az adott alkalmazást az utolsó beadási időközben (amely általában 30 perc az aktív használat esetén), és elindítja az alkalmazást, akkor:
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

### <a name="app-report"></a>Alkalmazás-jelentés
Kereshet a platform és az alkalmazás között, és ez a jelentés két különböző app Protection-állapotot biztosít, amelyeket a jelentés létrehozása előtt kijelölhet. Az állapotok **védhetők** **vagy nem védettek**.

  - Felügyelt MAM-tevékenységekre vonatkozó felhasználói állapot (**védett**): Ez a jelentés felhasználónkénti alapon ismerteti az egyes felügyelt MAM-alkalmazások tevékenységeit. A MAM-szabályzatok által megcélozott összes alkalmazást megjeleníti az egyes felhasználókra vonatkozóan, valamint az egyes alkalmazások állapotát a MAM-szabályzatokkal bejelentkezve. A jelentés a MAM-szabályzattal megcélozott alkalmazások állapotát is tartalmazza, de soha nem volt bejelölve.
  - Nem felügyelt MAM-tevékenységekre vonatkozó felhasználói állapot (nem**védett**): Ez a jelentés a jelenleg nem felügyelt MAM-kompatibilis alkalmazások tevékenységeit ismerteti, felhasználónkénti alapon. Ez az alábbiak miatt fordulhat elő:
    - Ezeket az alkalmazásokat egy olyan felhasználó vagy alkalmazás használja, amelyet jelenleg nem a MAM-szabályzat céloz meg.
    - Minden alkalmazás érvényesítve lett, de nincsenek rájuk vonatkozó MAM-szabályzatok.

    ![Képernyőfelvétel a felhasználó alkalmazás-jelentési paneljéről, három alkalmazás részleteivel](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**Felhasználói konfigurációs jelentés**
A kiválasztott felhasználó alapján ez a jelentés részletesen ismerteti a felhasználó által fogadott alkalmazások konfigurációit.

### <a name="app-configuration-report"></a>**Alkalmazás-konfigurációs jelentés**
A kiválasztott platform és alkalmazás alapján ez a jelentés részletesen ismerteti, hogy mely felhasználók kaptak konfigurációkat a kiválasztott alkalmazáshoz.

### <a name="app-learning-report-for-windows-information-protection"></a>Alkalmazás-tanulási jelentés Windows Information Protection
Ez a jelentés azt jeleníti meg, hogy mely alkalmazások próbálnak meg határokon átívelő házirendeket használni.

### <a name="website-learning-for-windows-information-protection"></a>A Windows Information Protection webhelyének megismerése
Ez a jelentés azt jeleníti meg, hogy mely webhelyek próbálnak meg határokon átívelő házirendeket használni.

## <a name="export-app-protection-activities"></a>Alkalmazás-védelmi tevékenységek exportálása
Az alkalmazásvédelmi szabályzatokkal kapcsolatos összes tevékenységet egyetlen .csv-fájlba exportálhatja. Ez hasznos lehet az összes, a felhasználók felől jelentett alkalmazásvédelmi állapot elemzésében. Az **app Protection. csv fájl a következőket jeleníti**meg:
- **Felhasználó**: a felhasználó neve.
- **E-mail**: a felhasználó e-mail-címe.
- **Alkalmazás**: az alkalmazás neve.
- **Alkalmazás verziója**: az alkalmazás verziója.
- **Eszköznév**: a felhasználói fiókhoz társított összes eszköz neve.
- **Eszköz gyártója**: az eszköz gyártóját sorolja fel (csak Android esetén). 
- **Eszköz modellje**: ez felsorolja az eszköz gyártóját (csak Android esetén). 
- **Android-javítás verziója**: az utolsó Android biztonsági javítás dátuma.
- **HRE-eszköz azonosítója**: ez az oszlop feltöltve lesz, ha az eszköz HRE van csatlakoztatva.
- **Mdm-eszköz azonosítója**: ez az oszlop feltöltve lesz, ha az eszköz regisztrálva van Microsoft Intune Mdm.
- **Platform**: az operációs rendszer.
- **Platform verziója**: az operációs rendszer verziója.
- **Felügyeleti típus**: a felügyelet típusa az eszközön. Például: Android Enterprise, nem felügyelt vagy MDM.  
- **Alkalmazás védelmi állapota**: nem védett vagy védett.
- **Házirend**: az alkalmazáshoz társított alkalmazás-védelmi szabályzatok.
- **Utolsó szinkronizálás**: az alkalmazás Microsoft Intunesal való legutóbbi szinkronizálásakor. 
- **Megfelelőségi állapot**: azt határozza meg, hogy a felhasználó eszközén lévő alkalmazás megfelel-e az alkalmazás-alapú feltételes hozzáférési szabályzatoknak.  

Kövesse az alábbi lépéseket az App Protection. csv fájl vagy az App Configuration. csv fájl létrehozásához:

1. Az Intune-os mobilalkalmazás-kezelés paneljén válassza az **Alkalmazásvédelmi jelentés** lehetőséget.

    ![Képernyőkép az App Protection letöltési hivatkozásáról](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Válassza az **Igen** lehetőséget a jelentés mentéséhez, majd válassza a **Mentés másként**lehetőséget. Válassza ki azt a mappát, amelybe menteni szeretné a jelentést.

    ![Képernyőkép a Jelentés mentése jóváhagyó mezőről](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> Az Intune további eszköz-jelentési mezőket biztosít, beleértve az alkalmazás regisztrációs AZONOSÍTÓját, az Android-gyártót, a modellt és a biztonsági javítás verzióját, valamint az iOS-modellt is. Az Intune-ban ezeket a mezőket az **alkalmazások** > **app protection-állapot** > **app Protection-jelentés: iOS/iPadOS, Android**. Emellett ezek a paraméterek segítséget nyújtanak az eszköz gyártójának (Android) **engedélyezési** listájának, az eszköz modell **engedélyezési** listájának (Android és iOS) és az **androidos biztonsági javítás minimális verziójának** beállításának konfigurálásában.   
 
## <a name="see-also"></a>További információ
- [Az iOS/iPadOS alkalmazások közötti adatátvitel kezelése](data-transfer-between-apps-manage-ios.md)
- [Milyen hatással vannak az androidos alkalmazásokra az alkalmazásvédelmi szabályzatok?](../fundamentals/end-user-mam-apps-android.md)
- [Mi várható, ha az iOS/iPadOS alkalmazást az alkalmazás-védelmi szabályzatok kezelik](../fundamentals/end-user-mam-apps-ios.md)
