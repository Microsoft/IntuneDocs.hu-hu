---
title: beágyazott fájl
description: beágyazott fájl
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 0aa78ec17aba5deb0c914c3698676219f203b856
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415077"
---
Ezek a hirdetmények olyan fontos információkat tartalmaznak, amelyek segíthetnek a jövőbeli Intune-változások és-funkciók előkészítésében.

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>Tervezze meg a változást: a "kiszolgálóoldali naplózás a Siri-parancsokhoz" beállítás el lesz távolítva az Intune-konzolról <!-- 5468501-->

Azt tervezzük, hogy a "kiszolgálóoldali naplózás a Siri-parancsokhoz" beállítást az Intune-konzolon az Intune szolgáltatás novemberi frissítésével távolítjuk el. Ez a módosítás úgy igazodik az Apple-hez, hogy már eltávolította a beállítást a saját oldalán.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha a novemberi frissítés vagy a 1911 november közepétől kikerül, láthatja, hogy ez a beállítás el lett távolítva az iOS-es konfigurációs profilokhoz tartozó eszközök korlátozási menüjéből (beépített alkalmazások) az Intune-konzolon. Ez megjelenhet a szabályzatokban és a célként megadott eszköz felügyeleti profiljában, de a beállítás nincs hatással az eszközre. A funkcionalitást nem vesszük számításba, mivel jelenleg nem működik az eszközökön, még akkor is, ha azt a felügyeleti profilban látja.

A két útvonal egyikét választhatja:
- Ha törölni szeretné ezt a beállítást a szabályzatokból, lépjen a beállítással rendelkező profilra, végezze el a másodlagos szerkesztést, és mentse a szabályzatot. A házirend újraszámítja a háttérbeli beállításokat, és a rendszer törli a beállítást a szabályzatból.
- Ha úgy dönt, hogy nem kívánja végrehajtani ezt a műveletet, a végfelhasználók ezt a beállítást fogják látni az eszköz felügyeleti profiljában, de a beállítás nem lesz hatással.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
A fenti szakasz vagy a szabályzat megtartása szerint is végrehajthat műveleteket. A változás kidobásakor az Újdonságok oldalát és dokumentációját fogjuk frissíteni.

### <a name="end-of-support-for-legacy-pc-management"></a>A régi számítógép-felügyelet támogatásának vége

Az örökölt számítógépek felügyelete 2020. október 15-én megszűnik. Frissítse az eszközöket a Windows 10-es verzióra, és regisztrálja újra őket MDM-eszközként, hogy az Intune kezelje őket.

[További információ](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Az Android-eszközök rendszergazdai támogatásának csökkentése 
Android-eszköz rendszergazdája (más néven a "régi" Android-kezelés és az Android 2,2 kiadásban megjelent) az androidos eszközök felügyeletének módja. A továbbfejlesztett felügyeleti funkciók azonban mostantól elérhetők az [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (Android 5,0) verzióban. A modern, gazdagabb és biztonságosabb eszközkezelés érdekében a Google az új Android-kiadásokban csökkenti az eszköz-rendszergazda támogatását.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A Google által végzett módosítások miatt az Intune-felhasználók a következő módokon lesznek hatással:  
- Az Intune csak az Android 10 vagy újabb rendszerű Android-eszközök (más néven Android Q) futtatásával támogatja az eszköz rendszergazdája által felügyelt Android-eszközöket a 2020-as nyaran. Ez a dátum akkor jelenik meg, ha az Android következő fő verziója várhatóan fel lesz szabadítva.   
- Az Android 10 vagy újabb rendszerű, 2020-es nyarat futtató eszközök rendszergazdája által felügyelt eszközök többé nem lesznek teljes mértékben felügyelve.       
- Az Android 10 alatti Android-verziókban továbbra is az eszköz rendszergazdája által felügyelt Android-eszközök nem lesznek hatással, és továbbra is teljes mértékben kezelhetők az eszköz rendszergazdájával.    
- Az Android 10 vagy újabb rendszerű eszközökön a Google az eszköz-rendszergazdai felügyeleti ügynökök (például Céges portál) számára korlátozta az eszköz-azonosító információk elérését. Ez hatással van az Intune alábbi szolgáltatásaira az Android 10 vagy újabb rendszerű eszközök frissítése után:  
    - A VPN hálózati hozzáférés-vezérlése már nem fog működni.   
    - Az eszközök vállalati tulajdonú IMEI-vagy sorozatszámmal való azonosítása nem fogja automatikusan megjelölni az eszközöket vállalati tulajdonban.  
    - Az IMEI-azonosító és a sorozatszám többé nem lesz látható a rendszergazdák számára az Intune-ban. 
        > [!NOTE]
        > Ez csak az eszköz rendszergazdája által felügyelt Android 10 és újabb rendszerű eszközökre vonatkozik, és nem érinti az Android Enterprise-ként kezelt eszközöket. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
A 2020 nyarán elérhető funkciók csökkenésének elkerüléséhez a következőket javasoljuk:
- Ne helyezze be az új eszközöket az eszköz-rendszergazda felügyeletbe.
- Ha egy eszköznek az Android 10-es verzióra kell frissítenie az eszközt, telepítse azt az eszköz rendszergazdai felügyelete alól az Android Enterprise Management és/vagy az App Protection szabályzatok segítségével.

#### <a name="additional-information"></a>További információ
- [A Google útmutatója az eszköz-rendszergazdától az Android Enterprise rendszerre való áttelepítéshez](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [A Google dokumentációja az eszköz rendszergazdai API-jával való érvénytelenítésének tervéről](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android Céges portál-alkalmazás frissítése a legújabb verzióra <!--4536963-->
Az Intune rendszeres időközönként frissítéseket szabadít fel az Android Céges portál alkalmazásban. November 2018-én közzétettünk egy vállalati portál frissítést, amely tartalmaz egy back-end kapcsolót, amely felkészíti a Google-t a meglévő értesítési platformról a Google Firebase Cloud Messaging (FCM) szolgáltatásba való váltásra. Ha a Google kihasználja a meglévő értesítési platformot, és áthelyezi az FCM-re, a végfelhasználóknak frissíteniük kell Céges portál alkalmazást legalább a november 2018-as kiadásra, hogy továbbra is kommunikáljanak a Google Play áruházral.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A telemetria azt jelzi, hogy a 5.0.4269.0-nál korábbi Céges portál verzióval rendelkező eszközök vannak. Ha a Céges portál alkalmazás ezen vagy újabb verziója nincs telepítve, akkor a rendszer az általa támogatott, az eszköz által kezdeményezett műveleteket, például a törlést, a jelszó alaphelyzetbe állítását, az elérhető és a szükséges alkalmazások telepítését, és a tanúsítványigénylés nem a várt módon működik. Ha az eszközök regisztrálva vannak az Intune-ban, akkor a Céges portál-verziók és a felhasználók az ügyfélalkalmazások által felderített alkalmazások MDM jelennek meg. A Céges portál alkalmazás korábbi verzióinak kiválasztásával megtekintheti, hogy mely végfelhasználók rendelkeznek olyan eszközökkel, amelyek nem frissítették a Céges portál alkalmazást.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Kérje meg az Android-eszközök végfelhasználóit, amelyek nem frissültek a Céges portál alkalmazás frissítéséhez a Google Play használatával. Értesítse az ügyfélszolgálatot arra az esetre, ha egy felhasználó nem tartotta meg automatikusan a Céges portál alkalmazás automatikus frissítését. További információ a Google FCM platformról és a változásról: további *információk* a hivatkozáson.

#### <a name="additional-information"></a>További információ
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Új teljes képernyős élmény az Intune-hoz <!--4593669-->
Folyamatban van a felhasználói felületi tapasztalatok létrehozása és szerkesztése az Intune-ban a Azure Portal. Ez az új felhasználói élmény leegyszerűsíti a meglévő munkafolyamatokat egy olyan varázsló stílusú formátum használatával, amely egy panelen van tömörítve. Ez a frissítés elvégezhető a "panel terjeszkedésével", vagy olyan létrehozási és szerkesztési folyamatokkal, amelyekkel részletesen lehatolhat a Deep Blade-útvonalak. A munkafolyamatok létrehozása is frissül, hogy tartalmazza a hozzárendeléseket (kivéve az alkalmazás-hozzárendelést).

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A teljes képernyős élmény a következő néhány hónapban a portal.azure.com és a devicemanagement.microsoft.com szolgáltatásban is elérhető az Intune-ban. A felhasználói felület ezen frissítése nem befolyásolja a meglévő szabályzatok és profilok funkcióit, de egy kissé módosított munkafolyamatot fog látni. Új szabályzatok létrehozásakor például beállíthatja, hogy a folyamat részeként bizonyos hozzárendeléseket a szabályzat létrehozása után is be lehessen állítani. Tekintse meg a blogbejegyzés *további információit* , amelyekkel az új felhasználói élmény a-konzolon fog kinézni.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Semmilyen műveletet nem kell végrehajtania, de szükség esetén érdemes lehet frissíteni az IT-Pro-útmutatást. Frissítjük a dokumentációt, mivel ez a folyamat a Azure Portalban az Intune-ban lévő különböző lapokra mutat.

#### <a name="additional-information"></a>További információ 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Tervezze meg a változást: az Intune app SDK és az alkalmazás-védelmi szabályzatok Android rendszerre való áttérés az Android 5,0 és újabb verzióinak támogatásához egy közelgő kiadásban <!--4911065 -->
Az Intune egy közelgő kiadásban az Android 5. x (nyalóka) és újabb verzióinak támogatására lesz áthelyezve. Frissítheti az összes burkolt alkalmazást a legújabb Intune app SDK-val, és frissítheti az eszközeit.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha nem használja az SDK-t vagy az alkalmazást az Androidhoz, akkor ez a változás nem érinti Önt. Ha az Intune app SDK-t használja, frissítsen a legújabb verzióra, és frissítse az eszközeit az Android 5. x vagy újabb verziójára. Ha nem frissíti, az alkalmazások nem kapják meg a frissítéseket, és a tapasztalatok minősége idővel csökken.

Az alábbi listában megtalálhatja az Intune-ban regisztrált általános eszközök listáját, amelyek az Android 4. x verzióját futtatják. Ha rendelkezik ezekkel az eszközökkel, hajtsa végre a megfelelő lépéseket annak biztosításához, hogy az eszköz támogassa az Android 5,0-es vagy újabb verzióját, vagy hogy a rendszer az Android 5,0-es vagy újabb verzióját támogató eszközre cserélje. Ez a lista nem teljes körű a kiértékeléshez szükséges összes eszközről:

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

További információért tekintse meg a [blogbejegyzésben](https://aka.ms/Windows7_Intune) .
