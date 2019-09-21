---
title: fájl belefoglalása
description: fájl belefoglalása
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 041f37e56e85b0ac26a4dd7a9dbbdb49bc0ebd9e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166330"
---
Ezek a hirdetmények olyan fontos információkat tartalmaznak, amelyek segíthetnek a jövőbeli Intune-változások és-funkciók előkészítésében. 


### <a name="decreasing-support-for-android-device-administrator"></a>Az Android-eszközök rendszergazdai támogatásának csökkentése 
Android-eszköz rendszergazdája (más néven a "régi" Android-kezelés és az Android 2,2 kiadásban megjelent) az androidos eszközök felügyeletének módja. A továbbfejlesztett felügyeleti funkciók azonban mostantól elérhetők az [Android Enterprise](../connect-intune-android-enterprise.md) (Android 5,0) verzióban. A modern, gazdagabb és biztonságosabb eszközkezelés érdekében a Google az új Android-kiadásokban csökkenti az eszköz-rendszergazda támogatását.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A Google által végzett módosítások miatt az Intune-felhasználók a következő módokon lesznek hatással: 
- Az Intune csak az Android 10 vagy újabb rendszerű (más néven Android Q) eszköz-rendszergazda által felügyelt Android-eszközök támogatását teszi lehetővé a 2020-as nyári időszakban. Ezt a dátumot kell megadnia, ha az Android következő fő verziója várhatóan kiadásra kerül.  
- Az Android 10 vagy újabb rendszert futtató, az 2020-as nyári időszakban nem felügyelt eszközökön a továbbiakban nem lesz teljes felügyelet.    
- Az Android 10 alatti Android-verziókban továbbra is az eszköz rendszergazdája által felügyelt Android-eszközök nem lesznek hatással, és továbbra is teljes mértékben kezelhetők az eszköz rendszergazdájával.  
- A Google minden Android 10 és újabb rendszerű eszközön korlátozta az eszköz-rendszergazdai felügyeleti ügynökök, például a Céges portál számára az eszköz-azonosító információk elérését. Ez hatással van az Intune alábbi szolgáltatásaira az Android 10 vagy újabb rendszerű eszközök frissítése után: 
    - A VPN hálózati hozzáférés-vezérlése már nem fog működni.  
    - Az eszközök vállalati tulajdonú IMEI-ként vagy sorozatszámmal való azonosítása nem fogja automatikusan megjelölni az eszközöket vállalati tulajdonban. 
    - Az IMEI-azonosító és a sorozatszám többé nem lesz látható a rendszergazdák számára az Intune-ban. 
        > [!Note]
        > Ez csak az eszköz rendszergazdája által felügyelt Android 10-es és újabb rendszerű eszközökre van hatással, és nem érinti az Android Enterprise-ként kezelt eszközöket. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
A 2020-as nyári időszakban elérhető funkciók csökkenésének elkerüléséhez a következőket javasoljuk:
- Ne helyezze be az új eszközöket az eszköz-rendszergazda felügyeletbe.
- Ha egy eszköznek az Android 10-es verzióra kell frissítenie az eszközt, telepítse azt az eszköz rendszergazdai felügyelete alól az Android Enterprise Management és/vagy az App Protection szabályzatok segítségével.

#### <a name="additional-information"></a>További információ
- [A Google útmutatója az eszköz-rendszergazdától az Android Enterprise rendszerre való áttelepítéshez](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [A Google dokumentációja az eszköz rendszergazdai API-jával való érvénytelenítésének tervéről](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android Céges portál-alkalmazás frissítése a legújabb verzióra <!--4536963-->
Az Intune rendszeres időközönként frissítéseket szabadít fel az Android Céges portál alkalmazásban. November 2018-én közzétettünk egy vállalati portál frissítést, amely tartalmaz egy back-end kapcsolót, amely felkészíti a Google-t a meglévő értesítési platformról a Google Firebase Cloud Messaging (FCM) szolgáltatásba való váltásra. Ha a Google kihasználja a meglévő értesítési platformot, és áthelyezi az FCM-re, a végfelhasználóknak legalább november 2018 kiadásban frissíteniük kell a vállalati portál alkalmazást, hogy továbbra is kommunikáljanak a Google Play áruházral.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A telemetria azt jelzi, hogy a 5.0.4269.0-nál korábbi Céges portál verzióval rendelkező eszközök vannak. Ha a vállalati portál alkalmazás ezen vagy későbbi verziója nincs telepítve, az informatikai részleg olyan műveleteket kezdeményezett, mint például a törlés, a jelszó alaphelyzetbe állítása, az elérhető és a szükséges alkalmazások telepítése, és előfordulhat, hogy a tanúsítványigénylés nem a várt módon működik. Ha az eszközök MDM regisztrálva vannak az Intune-ban, akkor a vállalati portál verzióit és a felhasználókat a Client apps – észlelt alkalmazások oldalon tekintheti meg. Ha kijelöli a Céges portál korábbi verzióit, megtekintheti, hogy a végfelhasználók milyen eszközökkel rendelkeznek a vállalati portál frissítésével.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Kérje meg az Android-eszközök végfelhasználóit, amelyek nem frissültek a vállalati portál Google Play használatával történő frissítéséhez. Értesítse az ügyfélszolgálatot abban az esetben, ha egy felhasználó nem tartotta meg a vállalati portál alkalmazás automatikus frissítését. További információ a Google FCM platformról és a változásról: további információk a hivatkozáson.

#### <a name="additional-information"></a>További információ
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Új teljes képernyős élmény az Intune-hoz <!--4593669-->
Folyamatban van a felhasználói felületi tapasztalatok létrehozása és szerkesztése az Intune-ban a Azure Portal. Ez az új felhasználói élmény leegyszerűsíti a meglévő munkafolyamatokat egy olyan varázsló-stílusú formátum használatával, amely egy panelen van tömörítve. Ez a frissítés elvégezhető a "panel terjeszkedésével", vagy olyan létrehozási és szerkesztési folyamatokkal, amelyekkel részletesen lehatolhat a Deep Blade-útvonalak. A munkafolyamatok létrehozása is frissül, hogy tartalmazza a hozzárendeléseket (kivéve az alkalmazás-hozzárendelést).

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A teljes képernyős élmény a következő néhány hónapban a portal.azure.com és a devicemanagement.microsoft.com szolgáltatásban is elérhető az Intune-ban. A felhasználói felület ezen frissítése nem befolyásolja a meglévő szabályzatok és profilok funkcióit, de egy kissé módosított munkafolyamatot fog látni. Új szabályzatok létrehozásakor például beállíthatja, hogy a folyamat részeként bizonyos hozzárendeléseket a szabályzat létrehozása után is be lehessen állítani. Tekintse meg a blogbejegyzés további információit, amelyekkel az új felhasználói élmény a-konzolon fog kinézni.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Semmilyen műveletet nem kell elvégeznie, de szükség esetén érdemes lehet az IT Pro-útmutatást is frissíteni. Frissítjük a dokumentációt, mivel ez a folyamat a Azure Portal-beli Intune-ban található különféle pengéket összesíti.

#### <a name="additional-information"></a>További információ 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665324--"></a>Tervezze meg a változást: Az Intune az iOS 11 és újabb verzióinak támogatására való áttérés szeptemberben <!-- 4665324-->
Szeptemberben azt várjuk, hogy az iOS 13 az Apple számára legyen felszabadítva. Az Intune-regisztráció, a Céges portál és a Managed Browser az iOS 11 kiadása után nem sokkal magasabban támogatja az iOS 11-es verzióját.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha a O365 Mobile apps iOS 11,0-es és újabb verziókban is támogatott, akkor ez nem érinti Önt; valószínűleg már frissítette az operációs rendszert vagy az eszközöket. Ha azonban rendelkezik az alább felsorolt eszközök bármelyikével, vagy dönthet úgy, hogy az alább felsorolt eszközök bármelyikét regisztrálja, akkor tudja, hogy az alábbi eszközök nem támogatják az iOS 10 rendszernél nagyobb operációs rendszert. Ezeket az eszközöket frissíteni kell egy olyan eszközre, amely támogatja az iOS 11 vagy újabb verzióját:

- iPhone 5
- iPhone 5c
- iPad (4. generáció)

Ha alkalmazás-védelmi házirendeket (alkalmazást) használ, a "minimális iOS operációs rendszer megkövetelése (csak figyelmeztetés)" hozzáférési beállítást is beállíthatja.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Tekintse meg az Intune-jelentéskészítést, hogy megtekintse, milyen eszközökre vagy felhasználókra lehet hatással. Válassza az **eszközök** > **minden eszköz** lehetőséget, és szűrje az operációs rendszer alapján. További oszlopokat is hozzáadhat, amelyekkel azonosítható, hogy a szervezeten belül kik rendelkeznek iOS 10 rendszerű eszközökkel. Kérje meg, hogy a végfelhasználók szeptember előtt frissítsenek eszközeiket egy támogatott operációsrendszer-verzióra.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Tervezze meg a változást: Az iOS-hez készült Intune app SDK 8.1.1 és újabb verziójának támogatása <!-- 3586942-->
Az Intune 2019-től kezdve az iOS-alkalmazások támogatásához az Intune app SDK 8.1.1 és újabb verzióit fogja támogatni. A 8.1.1-nál kisebb SDK-verziókkal létrehozott alkalmazások már nem támogatottak. Ez a változás az Apple iOS 13 kiadásával lép érvénybe, amely várhatóan szeptembertől kezdődően, illetve a MC181399-ben is jelent meg.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Az Intune app SDK-val vagy az alkalmazások csomagolásának integrálásával az adatok titkosításával biztosíthatja a nem jóváhagyott alkalmazásokból és felhasználóktól származó vállalati adatok védelmet. Az iOS-hez készült Intune app SDK a 256 bites titkosítási kulcsokat alapértelmezés szerint a Intune App Protection szabályzatok (alkalmazás) általi titkosítás engedélyezésekor fogja használni. Ennek a változásnak a megkezdése után minden, a 128 bites titkosítási kulcsokat használó SDK-verzióhoz tartozó iOS-alkalmazás a továbbiakban nem fogja tudni megosztani az SDK-8.1.1 integrált és a 256 bites kulcsokat használó alkalmazásokkal rendelkező 8.1.1. A védett adatmegosztás engedélyezéséhez minden iOS-alkalmazáshoz 8.1.1 vagy újabb SDK-verzió szükséges.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Keresse meg a Microsoft, harmadik féltől származó és üzletági (LOB) alkalmazásokat. Győződjön meg arról, hogy az Intune-ALKALMAZÁSsal védett összes alkalmazás az SDK 8.1.1 vagy újabb verzióját használja.

- LOB-alkalmazások esetén: Előfordulhat, hogy újra kell közzétennie az SDK-8.1.1 vagy újabb verzióval integrált alkalmazásokat. A legújabb SDK-verziót ajánljuk. Az ÜZLETÁGI alkalmazások alkalmazás-védelmi házirendekkel való előkészítésével kapcsolatos információkért lásd: üzletági [alkalmazások előkészítése az App Protection-szabályzatokhoz](../apps-prepare-mobile-application-management.md).
- Microsoft/harmadik féltől származó alkalmazások esetén: Győződjön meg arról, hogy az alkalmazások legújabb verzióját telepíti a felhasználók számára.

A dokumentációt és a fejlesztői útmutatót is frissítenie kell, ha ez a módosítás az SDK támogatásában is szerepel.

#### <a name="additional-information"></a>További információ
[Üzletági alkalmazások előkészítése az alkalmazás-védelmi szabályzatokhoz](../apps-prepare-mobile-application-management.md)

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Tervezze meg a változást: Új Windows Update-beállítások az Intune-ban <!-- 4464404 -->
Az Intune szolgáltatás vagy a 1908 új "határidő-beállítások" részének megadásával kezdődően a "felhasználó újraindításának engedélyezése (lefoglalt újraindításkor)" beállítások helyett a következő beállításokat vesszük igénybe. Azt tervezzük, hogy letiltjuk a bekapcsolt újraindítási beállításokat a felhasználói felületen a 1909-as vagy a szeptemberi frissítés után, majd a konzolról teljesen el kell távolítani őket a konzolról október végére. 

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha Windows 10-es eszközöket kezel a környezetben: 
- Az Intune frissítésével vagy 1908-as verziójában az új határidő-beállítások jelennek meg a konzolon a régi, lefolytatott újraindítási beállítások mellett.
- Ha a régi és az új beállítások is konfigurálva vannak, a határidő-beállítási értékek felülbírálják a befoglalt újraindítási beállítások értékeit.
- A határidő beállításai lecserélik a "felhasználó újraindításának engedélyezése (a művelet újraindítása)" beállítást a konzolon a 1910-es frissítésben.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Az 1908-as határidő-beállítások használatával kezdje meg a kívánt értékeket beállítani. Ha ezt megtörtént, beállíthatja, hogy a kapcsolódó újraindítási beállítás "nincs konfigurálva" értékűre készüljön, hogy előkészítse ezeket a beállításokat a konzolról októberben.

Szükség esetén frissítse a dokumentációt és az Automation-parancsfájlokat. 

Folyamatosan frissítjük, és egy emlékeztetőt teszünk közzé az üzenetközpont előtt, mielőtt eltávolítjuk a befoglalt újraindítási beállításokat.

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Tervezze meg a változást: Az Android 5,0-es és újabb verzióinak támogatásához az Intune app SDK és az alkalmazás-védelmi szabályzatok október <!--4911065 -->
Az Intune az Android 5. x (nyalóka) és újabb verzióinak támogatására lesz áthelyezve. Frissítheti az összes burkolt alkalmazást a legújabb Intune app SDK-val, és frissítheti az eszközeit.

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
Alkalmazások becsomagolása a legújabb Intune app SDK-val. Az "a minimális operációsrendszer-verzió megkövetelése (csak figyelmeztetés)" beállítást is beállíthatja a feltételes indítási beállítással, hogy a végfelhasználók tájékoztassák a felhasználókat a személyes eszközökről.
