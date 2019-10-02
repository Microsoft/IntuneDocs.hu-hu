---
title: fájl belefoglalása
description: fájl belefoglalása
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fa251a0edd943d566849b138af5cbab0be248a53
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731759"
---
Ezek a hirdetmények olyan fontos információkat tartalmaznak, amelyek segíthetnek a jövőbeli Intune-változások és-funkciók előkészítésében. 


### <a name="decreasing-support-for-android-device-administrator"></a>Az Android-eszközök rendszergazdai támogatásának csökkentése 
Android-eszköz rendszergazdája (más néven a "régi" Android-kezelés és az Android 2,2 kiadásban megjelent) az androidos eszközök felügyeletének módja. A továbbfejlesztett felügyeleti funkciók azonban mostantól elérhetők az [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (Android 5,0) verzióban. A modern, gazdagabb és biztonságosabb eszközkezelés érdekében a Google az új Android-kiadásokban csökkenti az eszköz-rendszergazda támogatását.

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Intune-terv a változáshoz: a Windows 7 támogatásának megszűnése <!-- 3042987 -->
Ahogy azt a MC148476-ben közzétettük, az elmúlt szeptember 2018-ben, majd a MC176794-ben ismét visszatért a 2019-es verzióra, a Windows 7 a 2020-as januári meghosszabbított támogatás végére ér. Ebben az esetben az Intune kivonja a Windows 7 rendszerű eszközök támogatását, így az új technológiákat támogató beruházásokra koncentrálhat, és nagyszerű új végfelhasználói élményt biztosíthat. Ezen dátum után a Windows 7 rendszerű számítógépek védelméhez segítséget nyújtó technikai segítségnyújtás és automatikus frissítések többé nem lesznek elérhetők az Intune-on keresztül. A Microsoft határozottan azt ajánlja, hogy a Windows 10-es rendszerre való áttérés előtt 2020 január, hogy elkerülje azt a helyzetet, amikor olyan szolgáltatásra vagy támogatásra van szüksége, amely már nem érhető el. További információk a Windows támogatási életciklusáról [itt](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)olvashat.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Azért kapta ezt az üzenetet, mert jelenleg a Windows 7 rendszerű SZÁMÍTÓGÉPeket a régi Intune PC szoftver ügynökével kezeli. Ha kevesebb mint egy évig marad a Windows 7 kiterjesztett támogatása, javasoljuk, hogy a lehető leghamarabb indítsa el a szervezetet a Windows 10-es verzióra való frissítéshez. A számítógép-felügyeleti funkciók közvetlenül a Windows 10-es operációs rendszerbe vannak építve, és már nem kell telepítenie az ügyfél-ügynököt, például a Windows 7 rendszerhez készült Intune-ügyfélszoftvert. A Windows 8,1-től kezdve a Microsoft a mobileszköz-kezelési (MDM) architektúrát használja a Windows rendszerű számítógépek kiépítéséhez, konfigurálásához, frissítéséhez és felügyeletéhez. Miután beállította az Intune-t, a Windows 10 rendszerű [számítógépek Intune-ba való regisztrálásával](..\windows-enroll.md) egyszerűsítheti a Windows-regisztrációt a Mdm-csatornán keresztül. Javasoljuk, hogy a Windows 10 rendszerű számítógépek kezeléséhez használja ezt az "ügynök nélküli" MDM-kezelési megoldást.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Javasoljuk, hogy a szervezet azonnal vegye fontolóra ezt a műveleti tervet:

- Tervezze meg és frissítse a Windows 7 flottáját a Windows 10-es verzióra 2020. január 14. előtt.
- Ismerkedjen meg a [Windows 10-es üzembe helyezési támogatással](https://docs.microsoft.com/windows/deployment/) , és tudjon meg többet arról, hogyan frissítheti a Windows 7 rendszerű számítógépek meglévő flottáját a Windows 10 rendszerre.
- Tekintse át az [asztali alkalmazást](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) , és nyújtson segítséget a Microsoft alkalmazás-kompatibilitási ígéretének gyors nyomon követésében.
- Meglévő korábbi Intune szoftveres ügyfelek által felügyelt eszközök átváltása a Microsoft által ajánlott megoldásra a Windows 10 felügyeletéhez a MDM-kezelés használatával. Az összes új Windows 10 rendszerű számítógép regisztrálása az Intune-hoz készült MDM-felügyelettel a Azure Portalban.
- További információért tekintse meg az [itt közzétett blogot](https://aka.ms/Windows7_Intune) .
