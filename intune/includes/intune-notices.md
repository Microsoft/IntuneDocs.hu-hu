---
title: beágyazott fájl
description: beágyazott fájl
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 4e93cb7f2d503704251b16d1af03924358020d4e
ms.sourcegitcommit: 1aaff35fddb3d06458d739968d28971fed0bb2ba
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/12/2020
ms.locfileid: "77156694"
---
Ezek a hirdetmények olyan fontos információkat tartalmaznak, amelyek segíthetnek a jövőbeli Intune-változások és-funkciók előkészítésében.

### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>Tervezze meg a változást: az androidos vállalati dedikált eszközök Intune-beli regisztrálásakor tapasztalható változás<!--6114580-->
A novemberi kiadásban a SCEP-tanúsítvány üzembe helyezésének támogatása támogatott az Android Enterprise dedikált eszközökön, amelyek lehetővé teszik a Wi-Fi profilok tanúsítványon alapuló elérését. Ez a változás érintette az androidos vállalati dedikált eszközök néhány kisebb beléptetési folyamatának változását. A márciusi vagy a 2003-es frissítéssel kapcsolatban további változtatások szükségesek.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha az androidos vállalati dedikált eszközöket felügyeli az Ön környezetében, akkor az egyes változások márciusban jelennek meg.
- A 2019 november 22. és a 1911 szolgáltatás frissítése előtt beléptetett, meglévő androidos eszközökhöz: ezek az eszközök rendelkeznek a telepített Microsoft Intune alkalmazással. Miután márciusban megtörtént a háttérbeli változások bevezetése az Intune szolgáltatásban március SCEP, az eszközökre telepített és a Wi-Fi profilokhoz társított tanúsítványok alkalmazása megkezdődik.
- A 2019. november 22. és a változás előtt beléptetett eszközök esetében márciusban bekövetkezik: ezekhez az eszközökhöz telepítve van a Microsoft Intune alkalmazás. Az eszközökre központilag telepített és Wi-Fi profilokhoz kapcsolódó SCEP-tanúsítványok továbbra is érvényben maradnak.
- Az új Android Enterprise dedikált eszközök regisztrációja a változás után márciusban: a végfelhasználók a regisztráció során különböző lépéseket fognak látni az eszközökön. A regisztráció továbbra is megkezdi a mai napig (QR, NFC, Zero Touch vagy Device Identifier), de nem lesz kötelező app install lépés. Ehelyett a rendszer automatikusan telepíti az Microsoft Intune alkalmazást az eszközökön. Emellett a végfelhasználóknak nem kell megkoppintani az "Intune-ügynök engedélyezése" lehetőséget a folyamat során. A Wi-Fi profilokhoz társított SCEP-tanúsítványok telepíthetők ezeken az eszközökön.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Frissítheti a végfelhasználói útmutatást, és értesítheti az ügyfélszolgálatot erről a változásról. Frissítjük az Újdonságok oldalát, és értesítjük Önt, ha ez a változás elindul.

#### <a name="additional-information"></a>További információ
[SCEP-tanúsítványok támogatása androidos vállalati dedikált eszközökön](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Frissítettük az "Adobe Acrobat Reader for Intune" Mobile App támogatási utasítását<!--5746776-->
A MC188653 augusztus végén megosztjuk az Adobe Acrobat Reader for Intune Mobile App-t, amely a 2019. december 1-én ért véget, az Adobe pedig az Intune app Protection-házirendjeinek támogatását tervezte a fő Acrobat Reader-alkalmazásban. Azóta megkaptuk a vásárlói visszajelzéseket, hogy több időt kellene biztosítani a rendszergazdák számára a cél eléréséhez, és a végfelhasználók számára az Adobe Acrobat Reader for Intune használatának megkezdéséhez. Az Adobe Acrobat Reader az Intune-nal való magas kihasználtsága miatt a végfelhasználói eszközökön, valamint a nagyvállalati forgatókönyvek szempontjából fontos, hogy minden tapasztalat megfelel a szervezete által biztosított alkalmazások védelmének. 

Noha továbbra is ajánlott az általános Acrobat Reader Mobile alkalmazás megcélzása a szabályzatokban, mivel az Acrobat Reader Mobile alkalmazás támogatja az alkalmazás-védelmi házirendeket, és integrálta az Intune SDK-t, az Adobe Acrobat Reader for Intune alkalmazás továbbra is támogatott lesz. 2020. március 31-ig. 

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Azért kapta ezt az üzenetet, mert a jelentés egy vagy több olyan házirendet jelez a szervezetben, amely az Intune-hoz készült Adobe Acrobat Reader alkalmazást és/vagy a korábbi EOL-kommunikációt is megkapta. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Tájékoztassa a végfelhasználókat és a helpdesket erről a változásról. Az Intune-nal kapcsolatos kérdésekért a [céges portál támogatási információ funkcióját](../apps/company-portal-app.md#support-information) használhatja.

#### <a name="additional-information"></a>További információ
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Windows Phone-telefon 8,1-es végpont-támogatás<!--3544909-->
A Microsoft mainstream Windows Phone-telefon 8,1-es verziójának támogatása 2017 júliusában fejeződött be, és a meghosszabbított támogatás az 2019-as év végén fejeződött be. A Windows Phone-telefon 8,1-es Céges portál alkalmazás a 2017 októbere óta tart fenn fenntartási módban. A Microsoft Intune mostantól a Windows Phone-telefon 8,1 2020. február 20-án megszűnik a támogatás.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Február 2020 20. után ezek az eszközök nem kapják meg a biztonsági frissítéseket, és nem regisztrálhat új eszközöket. A meglévő Windows Phone-telefon 8,1 rendszerű eszközök regisztrálva maradnak (házirend, alkalmazások, jelentéskészítés), de Megjegyzés: a meglévő regisztrációk hibaelhárítása ezen dátum után nem támogatott, mivel számos összetevő, például a harmadik féltől származó tanúsítványok már befejezték a támogatását platform. Az Intune leállítja a kompatibilitási tesztelést az Intune-nal és a Windows Phone-telefon 8,1-mel.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Az Intune-jelentéskészítéssel megtekintheti, hogy mely eszközökre vagy felhasználókra van hatással. Lépjen az Eszközök > Minden eszköz menüpontra, és szűrje a találatokat operációs rendszer alapján. További oszlopokat is hozzáadhat, amelyekkel azonosítható, hogy a szervezeten belül kik rendelkeznek a Windows Phone-telefon 8,1 rendszerű eszközökkel. Kérje meg, hogy a végfelhasználók a támogatott operációsrendszer-verzióra frissítse eszközeit.


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Művelet: a Microsoft Edge használata a védett Intune-böngésző felhasználói felületén<!--5728447-->
Ahogy az elmúlt évben osztozunk, a Microsoft Edge Mobile ugyanazokat a felügyeleti funkciókat támogatja, mint a Managed Browser, miközben sokkal fejlettebb felhasználói élményt biztosít. A Microsoft Edge által biztosított robusztus élmény érdekében a Intune Managed Browser kivonására kerül sor. A 2020. januártól kezdődően az Intune már nem fogja támogatni a Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem? 
A 2020. február 1-től kezdődően a Intune Managed Browser többé nem lesz elérhető a Google Play Áruházban vagy az iOS App Store-ban. Ezen a ponton továbbra is megcélozhatja az új alkalmazás-védelmi szabályzatokat a Intune Managed Browserra, bár az új felhasználók nem tudják letölteni a Intune Managed Browser alkalmazást. Emellett az iOS-en a MDM által beléptetett új webklipek is a Microsoft Edge-ben nyílnak meg a Intune Managed Browser helyett.  

Március 31 2020-én a Intune Managed Browser el lesz távolítva az Azure-konzolról. Ez azt jelenti, hogy többé nem fog tudni új szabályzatokat létrehozni a Intune Managed Browser számára. Ha meglévő Intune Managed Browser szabályzatok vannak érvényben, nem lesznek hatással rájuk. A Intune Managed Browser ikon nélkül fog megjelenni a konzolon, és a meglévő szabályzatok még mindig az alkalmazásnak megfelelően jelennek meg. Ezen a ponton eltávolítjuk a webes tartalom átirányításának lehetőségét is a Intune Managed Browser az adatvédelmi szabályzatok adatvédelem szakaszán belül.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra? 
A Intune Managed Browserról a Microsoft Edge-re való zökkenőmentes áttérés érdekében javasoljuk, hogy proaktív módon végezze el a következő lépéseket: 

1. Célozza meg a Microsoft Edge-t iOS-re és Androidra az App Protection-szabályzattal (más néven MAM) és az alkalmazás konfigurációs beállításaival. A Microsoft Edge-hez készült Intune Managed Browser szabályzatait a meglévő szabályzatok Microsoft Edge-re való célzásával is felhasználhatja.  
2. Győződjön meg arról, hogy az Ön környezetében található összes MAM-védelemmel ellátott alkalmazás rendelkezik "a webes tartalmak átvitelének korlátozása más alkalmazásokkal" beállítással "szabályzat által felügyelt böngészők" értékre. 
3. A "com. microsoft. Intune. useEdge" nevű felügyelt alkalmazás-konfigurációs beállítással megcélzott összes MAM-védelemmel ellátott érték értéke TRUE (igaz). A következő hónapban a 1911-es kiadással megkezdheti a 2. és a 3. lépést a "webtartalom átvitelének korlátozása más alkalmazásokkal" beállítással, hogy a "Microsoft Edge" legyen kiválasztva az alkalmazás-védelmi szabályzatok adatvédelem szakaszában. . 

Az iOS-és Android-alapú webklipek támogatása hamarosan elérhető lesz. Ha ez a támogatás megjelent, újra meg kell céloznia a meglévő webklipeket, hogy azok a Managed Browser helyett a Microsoft Edge-ben legyenek megnyitva. 

#### <a name="additional-information"></a>További információ
További információért látogasson el a [Microsoft Edge és az alkalmazás-védelmi szabályzatok használatával](../apps/manage-microsoft-edge.md) foglalkozó dokumentumokra, vagy tekintse meg a [támogatási blogbejegyzését](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="end-of-support-for-legacy-pc-management"></a>A régi számítógép-felügyelet támogatásának vége

Az örökölt számítógépek felügyelete 2020. október 15-én megszűnik. Frissítse az eszközöket a Windows 10-es verzióra, és regisztrálja őket mobileszköz-felügyeleti (MDM) eszközként, hogy az Intune kezelje őket.

[További információ](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Az Android-eszközök rendszergazdai támogatásának csökkentése 
Android-eszköz rendszergazdája (más néven a "régi" Android-kezelés és az Android 2,2 kiadásban megjelent) az androidos eszközök felügyeletének módja. A továbbfejlesztett felügyeleti funkciók azonban mostantól elérhetők az [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (Android 5,0) verzióban. A modern, gazdagabb és biztonságosabb eszközkezelés érdekében a Google az új Android-kiadásokban csökkenti az eszköz-rendszergazda támogatását.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A Google által végzett módosítások miatt az Intune-felhasználók a következő módokon lesznek hatással:  
- Az Intune csak az Android 10 vagy újabb rendszerű, a Q2 CY2020-t futtató Android-eszközök teljes támogatását teszi lehetővé. Az Android 10 vagy újabb rendszerű eszközökön futó rendszergazda által felügyelt eszközök nem lesznek teljesen felügyelve. Különösen az érintett eszközök nem kapják meg az új jelszóra vonatkozó követelményeket.
    - Ebben az időkeretben nem kerül sor a Samsung Knox-eszközökre, mert az Intune a Knox platformmal való integrációja révén kiterjesztett támogatást biztosít. Ez több időt biztosít az eszköz rendszergazdai felügyeletének megtervezésére.    
- Az Android 10 alatti Android-verziókban továbbra is az eszköz rendszergazdája által felügyelt Android-eszközöket nem érinti a rendszer, és továbbra is teljes körűen felügyelhető az eszköz rendszergazdájával.    
- Az Android 10 vagy újabb rendszerű eszközökön a Google az eszköz-rendszergazdai felügyeleti ügynökök (például Céges portál) számára korlátozta az eszköz-azonosító információk elérését. Ez a korlátozás a következő Intune-funkciókra van hatással, miután egy eszköz frissítve lett az Android 10-es vagy újabb verzióra:  
    - A VPN hálózati hozzáférés-vezérlése már nem fog működni.   
    - Az eszközök vállalati tulajdonú IMEI-vagy sorozatszámmal való azonosítása nem fogja automatikusan megjelölni az eszközöket vállalati tulajdonban.  
    - Az IMEI-azonosító és a sorozatszám többé nem lesz látható a rendszergazdák számára az Intune-ban. 
        > [!NOTE]
        > Ez csak az eszköz rendszergazdája által felügyelt Android 10 és újabb rendszerű eszközökre vonatkozik, és nem érinti az Android Enterprise-ként kezelt eszközöket. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Ha el szeretné kerülni a Q3-CY2020 érkező funkciók csökkentését, javasoljuk a következőket:
- Ne helyezze be az új eszközöket az eszköz-rendszergazda felügyeletbe.
- Ha egy eszköznek az Android 10-es verzióra kell frissítenie az eszközt, telepítse azt az eszköz rendszergazdai felügyelete alól az Android Enterprise Management és/vagy az App Protection szabályzatok segítségével.

#### <a name="additional-information"></a>További információ
- [A Google útmutatója az eszköz-rendszergazdától az Android Enterprise rendszerre való áttelepítéshez](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [A Google dokumentációja az eszköz rendszergazdai API-jával való érvénytelenítésének tervéről](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Tervezze meg a változást: az Intune app SDK és az alkalmazás-védelmi szabályzatok Android rendszerre való áttérés az Android 5,0 és újabb verzióinak támogatásához egy közelgő kiadásban <!--4911065 -->
Az Intune egy közelgő kiadásban az Android 5. x (nyalóka) és újabb verzióinak támogatására lesz áthelyezve. Frissítheti az összes burkolt alkalmazást a legújabb Intune app SDK-val, és frissítheti az eszközeit.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha nem használja az SDK-t vagy az alkalmazást az Androidhoz, akkor ez a változás nem érinti Önt. Ha az Intune app SDK-t használja, frissítsen a legújabb verzióra, és frissítse az eszközeit az Android 5. x vagy újabb verziójára. Ha nem frissíti, az alkalmazások nem kapják meg a frissítéseket, és a tapasztalatok minősége idővel csökken.

Az alábbi listában megtalálhatja az Intune-ban regisztrált általános eszközök listáját, amelyek az Android 4. x verzióját futtatják. Ha rendelkezik ezekkel az eszközökkel, hajtsa végre a megfelelő lépéseket annak biztosításához, hogy az eszköz támogassa az Android 5,0-es vagy újabb verzióját, vagy hogy a rendszer az Android 5,0-es vagy újabb verzióját támogató eszközre cserélje. Ez a lista nem minden olyan eszköz teljes, amelyet ki kell értékelni:

- Samsung SM – T561  
- Samsung SM – T365
- Samsung GT – I9195
- Samsung SM – G800F
- Samsung SM – G357FZ
- Motorola XT1080
- Samsung GT – I9305
- Samsung SM – T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Alkalmazások becsomagolása a legújabb Intune app SDK-val. Az "a minimális operációsrendszer-verzió megkövetelése (csak figyelmeztetés)" beállítást is beállíthatja úgy, hogy a végfelhasználók tájékoztassák a felhasználókat a személyes eszközökről a frissítéshez.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Intune-terv a változáshoz: a Windows 7 támogatásának megszűnése<!-- 3042987 -->
Ahogy a MC148476-ben, az utolsó szeptember 2018-án, a MC176794-ben pedig a 2019-as időszakban ismét megjelent, a Windows 7 a 2020-as január 14-én elérte a kiterjesztett támogatás végét. Ebben az esetben az Intune kivonja a Windows 7 rendszerű eszközök támogatását, így az újabb technológiákat támogató beruházásokra koncentrálhat, és nagyszerű, új végfelhasználói élményt biztosíthat. Ezen dátum után a Windows 7 rendszerű számítógépek védelméhez segítséget nyújtó technikai segítségnyújtás és automatikus frissítések többé nem lesznek elérhetők az Intune-on keresztül. A Microsoft határozottan azt javasolja, hogy a Windows 10 rendszerre való áttérés előtt a 2020-es számú olyan esetet ne telepítsen, ahol a szolgáltatásra vagy támogatásra már nem lesz elérhető. További információk a Windows támogatási életciklusáról [itt](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)olvashat.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Azért kapta ezt az üzenetet, mert jelenleg a Windows 7 rendszerű számítógépeket kezeli az örökölt Intune PC-s szoftveres ügynök használatával. Mivel a Windows 7 meghosszabbított támogatásának vége előtt kevesebb mint egy éve marad, nyomatékosan javasoljuk, hogy a lehető leghamarabb megkezdhesse a Windows 10-es verzióra való frissítést.  

A számítógép-felügyeleti funkciók közvetlenül a Windows 10-es operációs rendszerbe vannak építve, és már nem kell telepítenie az ügyfél-ügynököt, például a Windows 7 rendszerhez készült Intune-ügyfélszoftvert. A Windows 8,1-től kezdve a Microsoft a mobileszköz-kezelési (MDM) architektúrát használja a Windows rendszerű számítógépek kiépítéséhez, konfigurálásához, frissítéséhez és felügyeletéhez. Miután beállította az Intune-t, a Windows 10 rendszerű [számítógépek Intune-ba való regisztrálásával](..\windows-enroll.md) egyszerűsítheti a Windows-regisztrációt a Mdm-csatornán keresztül. Javasoljuk, hogy a Windows 10 rendszerű számítógépek kezeléséhez használja ezt az "ügynök nélküli" MDM-kezelési megoldást.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Javasoljuk, hogy a szervezet azonnal vegye fontolóra ezt a műveleti tervet:

- Tervezze meg és frissítse a Windows 7 flottáját a Windows 10-es verzióra 2020. január 14. előtt.
- Ismerkedjen meg a [Windows 10-es üzembe helyezési támogatással](https://docs.microsoft.com/windows/deployment/) , és tudjon meg többet arról, hogyan frissítheti meglévő Windows 7 rendszerű számítógépeit a Windows 10-es verzióra.
- Tekintse át az [asztali alkalmazást](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) az FastTrack-on keresztül, amely segítséget nyújt a Microsoft-alkalmazások kompatibilitási ígéretéhez.
- Meglévő örökölt Intune szoftveres ügyfél által felügyelt eszközök átváltása a Microsoft által ajánlott megoldásra a Windows 10 felügyeletéhez a MDM-kezelés használatával. Regisztrálja az összes új Windows 10-es számítógépet az Intune-hoz készült MDM-felügyelettel a Azure Portal.

További információt a [blogbejegyzésben](https://aka.ms/Windows7_Intune)talál.


