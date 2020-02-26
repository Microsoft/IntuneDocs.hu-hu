---
title: beágyazott fájl
description: beágyazott fájl
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 373aeea9ab4fcbd075ac2ab18f205f3ddd191a39
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609298"
---
Ezek a hirdetmények olyan fontos információkat tartalmaznak, amelyek segíthetnek a jövőbeli Intune-változások és-funkciók előkészítésében.

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>A Windows 10 Mobile Microsoft Intune támogatása<!--3544938-->
A Microsoft mainstream támogatása a Windows 10 Mobile-ban 2019 decemberében fejeződött be. A jelen támogatási nyilatkozatban említettek szerint a Windows 10 Mobile-felhasználók többé nem jogosultak új biztonsági frissítések, nem biztonsági gyorsjavítások, ingyenes támogatott támogatási lehetőségek vagy a Microsoft Online technikai jellegű frissítéseinek fogadására. A teljes mobil operációs rendszer támogatásán alapuló Microsoft Intune mostantól a Windows 10 Mobile-alkalmazás és a Windows 10 Mobile operációs rendszer Céges portál is támogatja a 2020-es májusi 11.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha a szervezetében üzembe helyezett Windows 10 Mobile-eszközöket használ, a 2020-as és a május 11. között új eszközöket regisztrálhat, hozzáadhat vagy eltávolíthat szabályzatokat és alkalmazásokat, vagy frissítheti a felügyeleti beállításokat. Május 11. után a rendszer leállítja az új regisztrációkat, és végül eltávolítja a Windows 10 Mobile managementet az Intune felhasználói felületéről. Az eszközök többé nem fogják bejelentkezni az Intune szolgáltatásba, és töröljük az eszköz-és a házirend-adategységeket.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Az Intune-jelentéskészítéssel megtekintheti, hogy mely eszközökre vagy felhasználókra van hatással. Nyissa meg az **eszközök** > **minden eszköz** lehetőséget, és szűrje az operációs rendszer alapján. További oszlopokat is hozzáadhat, amelyekkel azonosítható, hogy a szervezeten belül kik rendelkeznek a Windows 10 Mobile rendszerű eszközökkel. Kérje meg, hogy a végfelhasználók frissítse eszközeiket, vagy szüntessék meg a vállalati hozzáférés eszközeinek használatát.



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

### <a name="decreasing-support-for-android-device-administrator--5857738--"></a>Az Android-eszközök rendszergazdai támogatásának csökkentése<!--5857738-->
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



