---
title: "Korábbi kiadások | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: 3080d23f464e96315ed9e5fd59774ba9f1b2dd86
ms.openlocfilehash: 65d582958d77150091880cce72e079b87308209f


---

# Az Intune korábbi kiadásai
## 2016. május

Mindezek a funkciók hibrid telepítések esetén is támogatottak (Intune-nal integrált Configuration Manager). Az új hibrid funkciókról további információért tekintse meg a [hibrid újdonságok](https://technet.microsoft.com/en-us/library/mt718155.aspx) oldalát.

### Dokumentáció
A [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) előzetes kiadása üdvözli Önt!
Ez a teljesen új, modern tartalomplatform azért jött létre, hogy Ön, ügyfelünk egyszerűbben megismerje és hatékonyabban használhassa az Intune-t.
Ha szeretne tájékozódni az összes új funkcióról, keresse fel az [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (A docs.microsoft.com bemutatása) című weblapot.

### Az Intune szolgáltatás állapota
Az Intune-ra vonatkozó szolgáltatásállapot-adatok átkerültek a központi, a többi Microsoft-szolgáltatásról is információt nyújtó helyre. Ezt az információt mostantól az [Office 365 felügyeleti portál](https://portal.office.com/Admin/Default.aspx) **Szolgáltatás állapota** menüjében találja meg.
További információkat [ebben a blogban](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/) talál.


### Alkalmazáskezelés
- **MAM SDK: PIN-kód hosszának konfigurálása.** A mobilalkalmazás-felügyeleti (MAM-) alkalmazásoknál az eszközök PIN-kódjához hasonlóan meghatározható lesz a PIN-kód hossza. Ebben az esetben a végfelhasználóknak meg kell felelniük a beállított új korlátozásoknak. A felhasználók számára kissé más képernyő jelenik meg a hosszabb PIN-kód beviteléhez. Részletekért lásd: [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban](/intune/deploy-use/android-mam-policy-settings) és [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása](/intune/deploy-use/ios-mam-policy-settings).

- **Skype Vállalati verzió Androidra és iOS-re.** Mostantól a Skype Vállalati verziót is beállíthatja [mobilalkalmazás-felügyeleti (MAM-) célként, regisztrálási szabályzatok nélkül](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). A felhasználók bejelentkezését követően a rendszer érvénybe lépteti a MAM-szabályzatokat.

- **MAM-szabályzatokkal való felügyeletre alkalmas új alkalmazások.** Az androidos Microsoft Word, Excel és PowerPoint alkalmazáshoz mostantól az Intune-ban nem regisztrált eszközökön is MAM-szabályzatok társíthatók. A támogatott alkalmazások teljes listájának megtekintéséhez keresse fel a Microsoft Intune mobilalkalmazás-galériát a [Microsoft Intune alkalmazáspartnerek](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) oldalán.


### A Vállalati portál újdonságai

#### Androidos Munkahelyi portál alkalmazás
- **Végfelhasználói bejelentési értesítések**: a végfelhasználók mostantól bejelentési értesítést kapnak az androidos Vállalati portál alkalmazástól, amikor regisztrálják eszközüket a Vállalati portálon, illetve, amikor eltávolítják eszközüket a portálról.

- **Változások a készülékregisztráció-kezelői fiókokban az androidos Vállalati portál alkalmazásban.** A jobb teljesítmény és méretezhetőség érdekében az Intune mostantól nem jeleníti meg az összes készülékregisztráció-kezelő (DEM-) eszközt az androidos Vállalati portál alkalmazás Saját eszközök panelén. Csak az alkalmazást futtató helyi eszköz fog megjelenni, és csak abban az esetben, ha azt korábban már regisztrálták a Vállalati portálon. A DEM-felhasználó a helyi eszközön elvégezheti a kapcsolódó műveleteket, de a további regisztrált eszközök távoli felügyeleti teendői csak az Intune felügyeleti konzolon hajthatók végre.

#### Munkahelyi portál webhely
- **Vállalati portál webhely: az eszközazonosító sáv több információt nyújt a végfelhasználók számára.** A végfelhasználók mostantól könnyebben azonosíthatják a választott eszközt a Vállalati portál webhelyen. Ha nem jól választottak, a kezdőlapi sávon a **Koppintson ide** hivatkozással kijelölhetik a megfelelő eszközt.

## Mi várható?
- **Az üzenetközpont felhasználói felület bevezetése**. Az Intune-nak az [Office 365 felügyeleti portálra](https://portal.office.com/) való áttelepítése keretében az Office 365 üzenetközpontját fogjuk használni az új funkciókkal kapcsolatos és egyéb típusú értesítések küldéséhez. Emellett az Office 365 Admin felügyeleti társalkalmazás telepítésével mobiltelefonos értesítéseket kaphat, és egyszerűen továbbíthat bármilyen üzenetet a felhasználóknak vagy egy terjesztési célú aliasra.
Az üzenetközpontot a májusi kiadással kezdjük el használni, és a továbbiakban itt értesítjük a felhasználókat a frissítések elkészültéről, valamint az Intune új és továbbfejlesztett funkcióiról. Az üzenetközpont megtekintéséhez jelentkezzen be az [Office 365 felügyeleti portálra](https://portal.office.com/), és a bal oldali navigációs ablakból válassza az ÜZENETKÖZPONT elemet.

- **A készülékregisztráció-kezelő (DEM-) fiókok változásai**. A jobb teljesítmény és méretezhetőség érdekében az Intune mostantól nem jeleníti meg az **összes** készülékregisztráció-kezelő (DEM-) eszközt az iOS-es Vállalati portál alkalmazás **Saját eszközök** panelén. Csak az alkalmazást futtató helyi eszköz fog megjelenni, és csak abban az esetben, ha azt korábban már regisztrálták a Vállalati portálon. A DEM-felhasználó a helyi eszközön elvégezheti a kapcsolódó műveleteket, de a további regisztrált eszközök távoli felügyeleti teendői csak az Intune felügyeleti konzolon hajthatók végre. Emellett az Intune-ból kivezettük a DEM-fiókoknak az Apple Device Enrollment Programmal és az Apple Configurator eszközzel való használatát. Ezek a regisztrálási módszerek alapértelmezés szerint támogatják a megosztott iOS-eszközök felhasználó nélküli regisztrálását. Csak akkor használjon DEM-fiókot, ha a megosztott eszközök felhasználó nélküli regisztrálása nem lehetséges.

### A felhőplatform ütemterve
Maradjon naprakész az Intune jövőbeli fejlesztéseiről a [Cloud Platform ütemterv](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune) használatával.

### Szolgáltatások érvénytelenítése
- **Intune Viewer-alkalmazások** Az új RMS-megosztó alkalmazás megjelenésével 2016 augusztusától kezdve megszüntetjük a következő Intune Viewer-alkalmazásokat:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer Android-eszközökre a Google Play Áruházból

  Az Intune Viewer-alkalmazások használata helyett javasoljuk az új androidos Rights Management alkalmazás (RMS-megosztó alkalmazás) használatát, amelynek segítségével három különálló alkalmazás helyett elég egyetlen alkalmazást telepítenie a vállalati fájlok Android-eszközökön való biztonságos megtekintéséhez. További információk az RMS-megosztó alkalmazásról (a dokumentációra mutató hivatkozással).

- **Az értesítési szabályok egyéni csoportcélzási lehetősége megszűnik.**
Az Intune értesítési szabályai határozzák meg, hogy kinek küld értesítő e-mailt az Intune. Jelenleg úgy is beállíthatja az értesítési szabályokat, hogy a rendszer a létrehozott Intune-eszközcsoportokhoz tartozó eszközök összes felhasználójának elküldje az e-maileket. 2016. június 1-jétől fogva a felhasználó által létrehozott csoportok megcélzása nem lesz megvalósítható.

    Ma a következő lépések szükségesek ahhoz, hogy egy értesítési szabállyal egy Ön által létrehozott csoportot célozzon meg a Microsoft Intune felügyeleti konzoljában:

    A **Felügyelet** munkaterületen kattintson az **Értesítési szabályok** > **Új szabály létrehozása** elemre.

    Az Értesítési szabály létrehozása varázsló második lépésében válassza ki a szabály által megcélzott eszközcsoportokat. Ez az eszközcsoportok kiválasztására szolgáló lépés a jövőben nem lesz elérhető az Intune-konzolon.

    A módosítás előzetes ütemterve a következő:
    - 2016 júniusától az új bérlők számára nem fog megjelenni az Értesítési szabály létrehozása varázsló második lépése. A meglévő bérlőkre ekkor még nem lesz érvényes a változás.
    - 2016 augusztusától kezdve egyes meglévő bérlők számára sem fog megjelenni az eszközcsoportok kiválasztására szolgáló lépés a varázslóban.
    - 2016 októberétől kezdve terveink szerint már egyetlen bérlő számára sem fog megjelenni az eszközcsoportok kiválasztására szolgáló lépés a varázslóban.


- **Az iOS-es Vállalati portál alkalmazás támogatására vonatkozó módosítások**. Néhány hónapon belül meg fog jelenni egy frissítés az iOS-es Microsoft Intune Vállalati portál alkalmazáshoz, amely csak az iOS 8.0-s vagy újabb rendszerű eszközöket fogja támogatni. Az iOS 8.0-s verziójánál régebbi rendszerű új eszközöket ettől kezdve nem lehet majd regisztrálni. Az iOS 8.0-s verziójánál régebbi rendszerű, de korábban már regisztrált eszközök korlátozott ideig még felügyelhetők, és használhatják a Vállalati portál alkalmazást. A Vállalati portál alkalmazás legújabb verzióját azonban csak az iOS 8.0-s vagy újabb rendszerű eszközök fogják tudni elérni. Javasoljuk, hogy értesítse a felhasználókat, hogy az Intune új funkcióinak teljes körű kihasználása érdekében frissítsenek legalább iOS 8.0 rendszerre.  


## 2016. április
Mindezeket a funkciókat a hibrid ügyfelek is támogatják (tehát az Intune-nal integrált Configuration Manager is).
### Alkalmazáskezelés
- **A felhasználók mobilalkalmazás-felügyeleti megfelelősége.**
Már az Azure Active Directory- (AAD-) bérlőben szereplő bármely felhasználónál megtekintheti az alkalmazásfelügyeleti házirendek [állapotát](monitor-mobile-app-management-policies-with-Microsoft-Intune.md). Ez a következő teendőket foglalja magában:
   - Eszközök
   - Alkalmazások az eszközön

   Az állapot a következő értékeket veheti fel:

   **Beadva**: azt jelzi, hogy a házirend telepítve van a felhasználónál, az alkalmazást pedig használták munkahelyi környezetben, és sikeresen megkapta a házirendet.

    **Nincs beadva:** azt jelzi, hogy a házirend telepítve van a felhasználónál, de az alkalmazást egyszer sem használták a munkahelyi környezetben.


- **Az Outlook-névjegyek szinkronizálásának megakadályozása mobilalkalmazás-felügyelettel (Android).**
Új beállítás érhető el a [mobilalkalmazások eszközregisztráció nélküli felügyeletéhez](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md). Ezzel a beállítással megakadályozhatja, hogy az alkalmazás szinkronizálja a névjegyeket a natív címjegyzékbe az Android-eszközökön. Ha a beállítás engedélyezve van, a megcélzott alkalmazások nem menthetnek névjegyeket a natív címjegyzékbe. Ha a beállítás nincs engedélyezve, a megcélzott alkalmazások menthetik a névjegyeket a natív címjegyzékbe. Amikor [távolról törli egy eszköz vagy alkalmazás tartalmát](wipe-managed-company-app-data-with-Microsoft-Intune.md), a natív címjegyzék mentett összes névjegy törlődni fog. Ezt az új beállítást már az Android-eszközökön elérhető Outlook alkalmazás is támogatja.

### Eszközkezelés
- **A céges eszközök telefonszámos azonosítása.** A „Céges” eszközként besorolt telefonokat a rendszer már a teljes telefonszámukkal azonosítja, például amikor jelentést készít a mobileszközkészletről. A BYOD-eszközök telefonszámai továbbra is **** karakterekkel maszkolva, csak az utolsó 4 számjegyükkel jelennek meg.


### A Vállalati portál újdonságai
**Androidos Vállalati portál alkalmazás** Azok a felhasználók, akik nem regisztrálták az eszközüket az Intune-ban, és akiknél nincs telepítve a megfelelő tanúsítvány, nem jelentkezhetnek be az androidos Vállalati portál alkalmazásba. Náluk a következő üzenet jelenik meg: „Nem tud bejelentkezni, mert az eszközön hiányzik egy szükséges tanúsítvány.” Az üzenettel együtt megjelenő „Útmutató a probléma megoldásához” hivatkozással a felhasználó megtekintheti a tanúsítvány telepítési lépéseit. A probléma megoldásának lépéseit [Az eszközhöz hiányzik egy szükséges tanúsítvány](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing) című cikkben találhatja.

**iOS Vállalati portál alkalmazás**A kezdőképernyőn szereplő tartalmak, például a felsorolt alkalmazások, eszközök és az informatikusok elérhetőségi adatai már lefelé húzással is frissíthetők. A lehúzásos frissítési művelet a megfelelőséggel és házirenddel kapcsolatos adatokat nem ellenőrzi – ez az aktuális eszköz csempéjének kijelölésével és a **Szinkronizálás** gombbal végezhető el.

**Windows 10 Mobile és Windows Phone 8.1 Vállalati portál alkalmazás** A végfelhasználó számára az üzleti alkalmazások telepítésekor egy továbbfejlesztett környezet jelenik meg. Ha az alkalmazás telepítése hosszú ideig tart, a felhasználók manuálisan szinkronizálhatják az eszközt a szinkronizálási folyamat kényszerített folytatásához. A végfelhasználói lépések az [Eszköz manuális szinkronizálása a lassú alkalmazástelepítések felgyorsítása érdekében](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually) című cikkben találhatók.

**Vállalati portál webhelye** A Windows 10 Mobile- és a Windows Phone 8.1 -felhasználók az üzleti alkalmazások telepítésekor a következő új állapotokat láthatják, amelyek több részlettel szolgálnak számukra a telepítés előrehaladásáról:

* **Várakozás az eszköz szinkronizálására** – A felhasználó a „Telepítés” gombra kattintott, az eszköz pedig most megpróbál szinkronizálni az Intune-infrastruktúrával. A szinkronizálás szükséges a telepítés folytatásához. A „Várakozás az eszköz szinkronizálására” üzenet egyben hivatkozás is, amellyel a felhasználó megtekinthet egy [útmutatást](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) arról, hogyan szinkronizálhatja manuálisan az eszközét az Intune-nal, ha a szinkronizálási folyamat túl sokáig tart vagy elakad.
* **Letöltés** – A felhasználó letöltési kérelme feldolgozás alatt áll, az eszközön pedig folyamatban van az alkalmazás letöltése és telepítése.

A fenti állapotok megjelenése előtt a felhasználónál zavart okozhatott, ha egy alkalmazás telepítése hosszú ideig tartott, ugyanis csak a „Telepítés” állapotot láthatta, amely akár órákig is a képernyőn maradhatott. Az új állapotok bevezetésével a felhasználó a támogatási szolgálat felkeresése helyett a „Várakozás az eszköz szinkronizálására” hivatkozásra kattinthat, és az útmutatást követve folytatásra kényszerítheti a szinkronizálási folyamatot.


## 2016. március
### Újdonságok 2016. március 29-én
A Windows 10-hez tartozó általános konfigurációs házirend frissítésének kivételével a 2016. március 29-én kiadott összes szolgáltatás a hibrid ügyfelek (Intune-nal integrált Configuration Manager) esetében is támogatott. A Windows 10 általános konfigurációs házirendjének hibrid támogatása hamarosan elérhető lesz. Vegye figyelembe, hogy a felsorolt szolgáltatások némelyikéhez a Configuration Manager legújabb verziójára lehet szükség.

### Alkalmazáskezelés
- **A MAM felügyeletével elkerülhető az Outlook-névjegyek szinkronizálása (iOS).** Új beállítás érhető el az eszközregisztráció nélküli mobilalkalmazás-kezeléshez. Ezzel a beállítással megakadályozhatja, hogy az alkalmazás szinkronizálja a névjegyeket a natív címjegyzékbe az iOS-eszközökön. Ha a beállítás engedélyezve van, az alkalmazás nem tudja menteni a névjegyeket a natív címjegyzékbe. Ha a beállítás nincs engedélyezve, az alkalmazás menteni tudja a névjegyeket a natív címjegyzékbe. Amikor szelektív módon törli egy eszköz tartalmát, a natív címjegyzékbe mentett összes névjegy törlődni fog. Ez az új beállítást az Outlook alkalmazás támogatja az iOS-eszközökön. Az új beállítással és az egyéb beállításokkal kapcsolatban további információt a [Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése](https://technet.microsoft.com/en-us/library/dn292747.aspx) című témakörben találhat.

### Hozzáférés-vezérlés
- **A Skype Vállalati online verzió támogatja a feltételes hozzáférést.** Beállíthat feltételes hozzáférési házirendet a Skype Vállalati online verzióhoz, hogy csak a felügyelt és megfelelő iOS- és Android-eszközök férhessenek hozzá. A Skype Vállalati online verzió mobilalkalmazásba iOS- vagy Android-eszközön bejelentkezni próbáló végfelhasználóktól a bejelentkezés végrehajtása előtt a rendszer kérni fogja a regisztrálást az Intune-nal, valamint a nem megfelelést okozó problémák megszüntetését. Részletes leírás: [A Skype Vállalati online verzióhoz való hozzáférés kezelése](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Eszközkezelés
- **Intune-támogatás az iOS 9.3-as verzióhoz.** Az Apple március 21-én, hétfőn jelentette be az iOS 9.3 megjelenését. Komoly erőfeszítéseket tettünk azért, hogy a Microsoft Intune kompatibilis legyen az Apple mobil operációs rendszerének legújabb verziójával, és [örömmel jelenthetjük be, hogy az Intune már támogatja az iOS 9.3-as verzióval működő eszközöket](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  A jelenleg rendelkezésre álló iOS-eszközökhöz elérhető összes meglévő Intune-szolgáltatás továbbra is problémamentesen fog működni, amikor a felhasználók az iOS 9.3-as verzióra frissítik az eszközeiket. Ezenkívül az iOS 9.3-as verziót már a hibrid ügyfelek (Intune-nal integrált Configuration Manager) is támogatják.

- **A Windows 10 általános konfigurációs házirendje már tartalmazza a Windows Defendernek a Windows 10 rendszerrel működő regisztrált számítógépeken történő kezeléséhez szükséges beállításokat.** Részletes leírás: [A Windows 10 konfigurációs házirendjének beállításai a Microsoft Intune-ban](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Vállalati portál

- **A Windows-alkalmazáscsomagok közvetlenül elérhetők a Vállalati portál webhelyén.** A Windows 8, a Windows 8.1 és a Windows RT rendszerű számítógépek felhasználói most már közvetlenül a Vállalati portál webhelyéről telepíthetik a Windows-alkalmazáscsomagokat (.appx kiterjesztés). Korábban az alkalmazások telepítéséhez Önnek kellett központilag telepítenie, vagy a felhasználóknak az eszközeikre kell telepíteniük a Vállalati portál alkalmazást.

- **A felhasználók a Vállalati portál webhelyén távolról zárolhatják az eszközeiket.** Egy új távoli zárolási beállítás lett elérhető a Vállalati portál webhelyen, amellyel a felhasználók a portálon távolról zárolhatják az eszközeiket azok elvesztése vagy ellopása esetén. Lásd a [végfelhasználóknak szóló utasításokat](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). A következő táblázat a távoli zárolás platformtámogatását sorolja fel a különálló Intune és a Configuration Managerrel együtt használt Intune esetében.

|Platform | Támogatás részletei|
|---------|----------------|
|Android |Támogatott|
|iOS |Támogatott|
|Windows 10 mobil verzió |Csak beállított jelszóval rendelkező telefonok esetén támogatott|
|Windows 10 asztali verzió |Nem támogatott|
|Windows Phone 8.1 |Csak beállított jelszóval rendelkező telefonok esetén támogatott|
|Windows Phone 8.0 |Nem támogatott|
|PC (Windows 8.0 és korábbi verziók) |Nem támogatott|
|PC (Windows 8.1) |Nem támogatott|

### Újdonságok 2016. március 10-én

### Alkalmazáskezelés

- **Éljen az iOS harmadik fél által nyújtott, MDM-megoldásokban regisztrált eszközök „Megnyitás ezzel” típusú kezelésének előnyével** A harmadik felek által nyújtott mobileszköz-kezelési forgalmazójával kihasználhatja az iOS „Megnyitás ezzel” típusú kezelését. Korlátozásokat állíthat be a konfigurációs profil beállításaiban, és az [iOS-alkalmazások közti adatátvitel kezelésével](manage-data-transfer-between-ios-apps-with-microsoft-intune.md) telepítheti az alkalmazást.

     Ez a módszer két fő előnnyel jár:

     1. A felhasználóknak be kell jelentkezniük a munkahelyi fiókjukkal, mielőtt hozzáférhetnének a szervezeti adatokhoz a Cloud Services szolgáltatásokból vagy más alkalmazásokból. Ez biztosítja, hogy mobilalkalmazás-kezelési (MAM-) házirendek legyenek érvényben az adatok elérésekor.

     2. A külső MDM-megoldással telepített felügyelt e-mail-profilok és más felügyelt alkalmazások fájlokat és adatokat oszthatnak meg az Intune MAM-szabályzatokkal rendelkező alkalmazásokkal.

- **A Microsoft Outlook alkalmazás kezelése MAM-szabályzatokkal az Intune-ban nem regisztrált eszközökön** Mostantól az Intune mobilalkalmazás-kezelési szabályzatával kezelheti a Microsoft Outlook alkalmazást az Intune-ban nem regisztrált eszközökön. A frissített Microsoft Outlook alkalmazás a MAM-képességekkel az [iOS-](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) és [Android-](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook)eszközökhöz is elérhető. A [Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése](https://technet.microsoft.com/library/mt627829.aspx) témakörben található utasításokkal hozzon létre egy MAM-házirendet.  


- **A mobilalkalmazások konfigurációs szabályzataival rugalmasabban szabhatja meg az iOS-alkalmazások felhasználói adatait** Megadhat olyan felhasználói beállításokat, amelyekre az iOS-alkalmazásoknak szükségük lehet a megnyitásukkor. Megadhat például egy hálózati portot vagy egy felhasználónevet. Részletes leírás: [iOS-alkalmazások konfigurálása mobilalkalmazás-konfigurációs házirendek segítségével a Microsoft Intune-ban](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Az Adobe Reader for Microsoft Intune telepítése a vállalata Intune-ban kezelt iOS-eszközeire ** Az Adobe Reader iOS-alkalmazás már regisztrált eszközökön is kezelhető az Intune mobilealkalmazás-kezelési házirendjével.

- **A telepített webklipeknek a felügyelt böngészőben való megnyitása** Célzott webklipeket telepíthet, amelyek csak a felügyelt böngészővel nyithatók meg az iOS- és Android-eszközökön. Vállalati erőforrásokra mutató hivatkozásokat telepíthet például a Vállalati portálon keresztül, és amikor a felhasználók megnyitják a hivatkozásokat, azok közvetlenül a felügyelt böngészőben nyílnak meg, ahol a MAM-házirend védi őket. Részletes leírás: [Alkalmazások telepítése](deploy-apps.md).


- **Windows 10-eszközökre készült Vállalati Windows Áruház alkalmazásainak keresése, kezelése és elosztása az Intune rendszergazdai konzolból** Az Intune támogatást nyújt a Vállalati Windows Áruházhoz, így könnyebben kereshet, kezelhet és oszthat el alkalmazásokat a kezelt Windows 10-eszközei között. A Vállalati Windows Áruházzal kezelheti ezen alkalmazások telepítését és megfigyelését az Intune felügyeleti konzoljáról – ugyanarról a konzolról, amellyel a többi alkalmazást is kezeli. A Vállalati Windows Áruház az „online licencelt alkalmazások” tartalmát és licencelését felügyeli. Részletes leírás: [A Vállalati Windows Áruházban vásárolt alkalmazások kezelése](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Eszközkezelés
- **PFX-tanúsítványok elosztása iOS-eszközökön** Az Intune-rendszergazdák iOS PFX-tanúsítványokat hozhatnak létre és telepíthetnek a Wi-Fi-, e-mail- és VPN-hitelesítéshez az iOS-eszközökön. Ez a funkció már elérhető az Android- és Windows 10-es eszközökhöz. Részletes leírás: [Vállalati erőforrások elérésének lehetővé tétele tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md).


- **Alkalmazások és házirendek alkalmazása különböző eszközcsoportokra a felhasználói kategóriák alapján** Az Intune-rendszergazdák mostantól egyéni eszközkategóriákat határozhatnak meg, amelyekből a felhasználók válogathatnak a regisztrálás során. A rendszergazdák például azt kívánhatják, hogy a felhasználóik adják meg, hogy a „Pénztárhoz”, „Szállítójárműhöz” vagy „Leltárhoz” használt eszközt regisztrálnak-e. A kiválasztott kategória miatt az eszköz egy Intune-eszközcsoport tagjává válik, amely különböző alkalmazások és házirendek a regisztrált eszközre való telepítéséhez használható. Részletes leírás: [Eszközök kategorizálása eszközcsoport-leképezéssel](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### A Microsoft Munkahelyi portál szolgáltatásának módosításai és frissítései
Ebben a kiadásban a következő módosításokat vezettük be a Munkahelyi portál szolgáltatásban.

**Androidos Munkahelyi portál alkalmazás**

* Amikor a felhasználók mobilalkalmazás-kezeléssel felügyelt alkalmazást indítanak, egy üzenetet látnak, amely értesíti őket, hogy az alkalmazást a vállalatuk felügyeli. A felhasználók mostantól a „További információk” hivatkozásra koppintva [további információhoz](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) juthatnak arról, mit jelent a „felügyelt alkalmazás”. Vagy ha a „Ne jelenjen meg ismét” lehetőségre koppintanak, az üzenet többé nem jelenik meg az alkalmazás elindításakor.
* Új képernyők vezetik végig a felhasználókat a regisztrálási folyamaton és nyújtanak további információt arról, hogy a felhasználóknak miért érdemes regisztrálniuk, valamint hogy az informatikai rendszergazdák mit láthatnak és mit nem láthatnak a regisztrált eszközökön. A részleteket lásd: [Regisztrációs utasítások](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
* A regisztrációs hibaüzenetek mostantól megjelennek a Munkahelyi portál alkalmazásban. Korábban ezek az üzenetek a Munkahelyi portál webhelyen jelentek meg. Ez a módosítás azt jelenti, hogy mostantól az összes hibaüzenet egy helyen jelenik meg ahelyett, hogy két különböző helyen jelenne meg.


**iOS rendszerű Vállalati portál alkalmazás**
* Amikor a felhasználók mobilalkalmazás-kezeléssel felügyelt alkalmazást indítanak, egy üzenetet látnak, amely értesíti őket, hogy az alkalmazást a vállalatuk felügyeli. A felhasználók mostantól a „További információk” hivatkozásra koppintva [további információhoz](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) juthatnak arról, mit jelent a „felügyelt alkalmazás”. Vagy ha a „Ne jelenjen meg ismét” lehetőségre koppintanak, az üzenet többé nem jelenik meg az alkalmazás elindításakor.
* Új képernyők vezetik végig a felhasználókat a regisztrálási folyamaton és nyújtanak további információt arról, hogy a felhasználóknak miért érdemes regisztrálniuk, valamint hogy az informatikai rendszergazdák mit láthatnak és mit nem láthatnak a regisztrált eszközökön. A részleteket lásd: [Regisztrációs utasítások](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).
* A regisztrációs hibaüzenetek mostantól megjelennek a Munkahelyi portál alkalmazásban. Korábban ezek az üzenetek a Munkahelyi portál webhelyen jelentek meg. Ez a módosítás azt jelenti, hogy mostantól az összes hibaüzenet egy helyen jelenik meg ahelyett, hogy két különböző helyen jelenne meg.




## 2016. február
### A Microsoft Munkahelyi portál szolgáltatásának módosításai és frissítései

Ebben a kiadásban a következő módosításokat vezettük be a Munkahelyi portál szolgáltatásban.

#### Androidos Munkahelyi portál alkalmazás
- Új képernyők vezetik végig a felhasználókat a regisztrálási folyamaton és nyújtanak további információt arról, hogy a felhasználóknak miért érdemes regisztrálniuk, valamint hogy az informatikai rendszergazdák mit láthatnak és mit nem láthatnak a regisztrált eszközökön. A részleteket lásd: [Regisztrációs utasítások](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
- A regisztrációs hibaüzenetek mostantól megjelennek a Munkahelyi portál alkalmazásban. Korábban ezek az üzenetek a Munkahelyi portál webhelyen jelentek meg. Ez a módosítás azt jelenti, hogy mostantól az összes hibaüzenet egy helyen jelenik meg ahelyett, hogy két különböző helyen jelenne meg.

#### iOS rendszerű Vállalati portál alkalmazás
 - Új képernyők vezetik végig a felhasználókat a regisztrálási folyamaton és nyújtanak további információt arról, hogy a felhasználóknak miért érdemes regisztrálniuk, valamint hogy az informatikai rendszergazdák mit láthatnak és mit nem láthatnak a regisztrált eszközökön. A részleteket lásd: [Regisztrációs utasítások](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).

 - A regisztrációs hibaüzenetek mostantól megjelennek a Munkahelyi portál alkalmazásban. Korábban ezek az üzenetek a Munkahelyi portál webhelyen jelentek meg. Ez a módosítás azt jelenti, hogy mostantól az összes hibaüzenet egy helyen jelenik meg ahelyett, hogy két különböző helyen jelenne meg.


## 2016. január

### A Windows 10 szolgáltatásainak kihasználása
* **Feltételes hozzáférés az állapotigazolási szolgáltatással** Az Intune-rendszergazdák mostantól megtekinthetik a Windows 10 eszközállapot-igazolási állapotát az Intune felügyeleti konzoljában. Az eszközállapot-igazolással a rendszergazdák gondoskodhatnak arról, hogy az ügyfélszámítógépek BIOS-, TPM- és rendszerindítószoftver-konfigurációja megbízható legyen. Az eszközállapot-igazolás támogatásához az ügyféleszközökön a Windows 10-nek kell futnia, és engedélyezni kell a TPM 2-t. Az eszközállapot-igazolás megjeleníti az eszközök számát, melyeken engedélyezve vannak az egyes alábbi funkciók:
    * Korai indítás kártevőirtó
    * BitLocker
    * Biztonságos rendszerindítás
    * Kódintegritás

    Az eszközállapot beállításával, az összegyűjtött adatpontokkal és az eszközállapot-jelentéssel kapcsolatos részleteket lásd: [Bevezetés a Microsoft Intune eszközmegfelelőségi házirendjeinek kezelésébe](introduction-to-device-compliance-policies-in-microsoft-intune.md). A [HAS szolgáltatás részletei](https://msdn.microsoft.com/en-us/library/dn934876.aspx) című témakör részletesen leírja a szolgáltatást.

* **Windows 10 Passport for Work házirend- és tanúsítványkezelés** Az Intune lehetővé teszi az [integrációt a Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) nevű Windows 10-es alternatív bejelentkezési módszerrel, amely Active Directoryt vagy egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya helyett. A Passport lehetővé teszi jelszó helyett felhasználói kézmozdulatok használatát a bejelentkezéshez. A felhasználói hitelesítési mód lehet egy egyszerű PIN-kód, biometrikus hitelesítés, mint például a Windows Hello, vagy egy külső eszköz, például egy ujjlenyomat-olvasó.

* **VPN-csatlakozás választott alkalmazásokban** Kiválaszthat olyan alkalmazásokat, amelyek automatikusan csatlakoznak a vállalati hálózathoz VPN-kapcsolaton keresztül. A VPN-profil beállításakor létrehozhatja az alkalmazások listáját a Segítség a felhasználóknak a munkájukhoz való csatlakozásban VPN-profilok használatával a Microsoft Intune-nal című részben leírtak alapján.

* **Windows 10 – teljes törlés támogatása** Mostantól az Intune-nal regisztrált Windows 10-es asztali eszközök teljes távoli törlését is elrendelheti az Intune felügyeleti konzoljáról. A Windows 10 teljes törlési funkciója az eszköz gyári beállításainak visszaállítását végzi el.


### Az Apple Volume Purchase program (VPP) frissítése
Az Intune most segít [az Apple Volume Purchase Program (VPP) for Business programon keresztül vásárolt alkalmazások felügyeletében](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Ebbe beletartozik a licencinformációk az Apple és az Intune közötti szinkronizálása és annak nyomon követése, hogy az egyes alkalmazások hány példánya van telepítve.

### Vállalati tulajdonú eszközök azonosítása IMEI számokkal
[Nemzetközi mobilkészülék-azonosító (IMEI) számokat importálhat](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) IMEI-számokkal rendelkező mobileszköz-platformok esetén, hogy könnyebben azonosítsa a vállalati tulajdonban lévő mobileszközöket. Az Intune-ban történő regisztráció után az importált IMEI-számokkal rendelkező eszközök Vállalati címkével rendelkeznek, amellyel a személyes eszközökre alkalmazott házirendektől eltérő házirendek alkalmazhatók.

### Mostantól több alkalmazás kompatibilis az Intune MAM-házirendekkel
Mostantól a Microsoft partnereinek további alkalmazásai kompatibilisek az Intune mobilalkalmazás-kezelési (MAM-) házirendjeivel (az Intune által felügyelt eszközökhöz):
* Box for EMM (a Box Inc vállalattól) – csak iOS esetén
* Adobe Reader (az Adobe vállalattól) – csak Android esetén
* Foxit PDF Reader (a Foxit Corporation vállalattól) – iOS és Android esetén


### Az IE9 támogatása januárban megszűnik
2016 februárjától többé nem támogatjuk az Internet Explorer 9-et mint a Microsoft Intune Vállalati portál webhelyének, az Intune-fiókportálnak és az Intune felügyeleti konzoljának eléréséhez használható hivatalos böngészőt. Ezért át kell térnie az Internet Explorer 10 vagy a böngésző újabb verziójának használatára.

## 2015. december
### A Microsoft Munkahelyi portál szolgáltatásának módosításai és frissítései
Ebben a kiadásban a következő módosításokat vezettük be a Munkahelyi portál szolgáltatásban.

**Androidos Munkahelyi portál alkalmazás**

A Google új követelményeinek való megfelelés végett elvégeztük a következőkben ismertetett változtatásokat. Az Android 6.0-s és újabb verziójú eszközökön két új üzenet jelenik meg a felhasználók számára:
* Allow Company Portal to make and manage phone calls? (Engedélyezi, hogy a Munkahelyi portál alkalmazás telefonhívásokat indítson és kezeljen?)
* Allow Company Portal to access photos, media, and files on your device? (Engedélyezi a Munkahelyi portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?)

További információt e két üzenetről az alábbi táblázatban talál.



Szöveges üzenet  |Allow Company Portal to make and manage phone calls? (Engedélyezi, hogy a Munkahelyi portál alkalmazás telefonhívásokat indítson és kezeljen?)  
---------|---------
Üzenet jelentése     |  Engedélyezi a felhasználó eszközéhez tartozó telefonszám és IMEI-szám Intune szolgáltatásnak való elküldését, valamint a Hardver lap felügyeleti konzolján való megjelenítésüket.   </br></br>**MEGJEGYZÉS: A Vállalati portál alkalmazás soha nem indít és kezel telefonhívásokat.** Az üzenet szövegét a Google szabja meg, és nem módosítható. </br></br>A **Hardver** lap megnyitásához válassza a **Csoportok** > **Minden mobileszköz** > **Eszközök** lehetőséget. Jelölje ki a felhasználó eszközét, és válassza a **Tulajdonságok megjelenítése** > **Hardver** lehetőséget.    
Hol és mikor jelenik meg az üzenet  | Akkor jelenik meg az üzenet, amikor a felhasználók első alkalommal jelentkeznek be a Munkahelyi portál alkalmazásba, hogy regisztrálják az eszközüket.|         
Mi történik, ha a felhasználók engedélyezik a hozzáférést  |  Az eszköz telefonszáma és IMEI-száma megjelenik a Hardver lap felügyeleti konzolján. |         
Mi történik, ha a felhasználók nem engedélyezik a hozzáférést     | Tovább használhatják a Munkahelyi portál alkalmazást, regisztrálhatják az eszközeiket, de azok telefonszámai és IMEI-számai nem jelennek meg a Hardver lap felügyeleti konzolján.       </br></br> Amikor a felhasználók a hozzáférés megtagadása után másodszor bejelentkeznek a Vállalati portál alkalmazásba, az üzenetben látható egy **Ne jelenjen meg többé** feliratú jelölőnégyzet, amelynek bejelölésével végleg kikapcsolhatják az üzenet megjelenítését.</br></br>Ha a felhasználók engedélyezik a hozzáférést, de később megtagadják azt, az üzenet újból megjelenik majd, amikor a felhasználók a legközelebb bejelentkeznek a Munkahelyi portál alkalmazásba a regisztrálást követően.</br></br>Amennyiben a felhasználók később ismét engedélyezni szeretnék a hozzáférést, a **Beállítások** > **Alkalmazások** > **Vállalati portál** > **Engedélyek** > **Telefon** lapon tehetik ezt meg.
További információ     |  Felhasználóknak: [Bejelentkezés a Munkahelyi portál alkalmazásba](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>Rendszergazdáknak: Az ebben a táblázatban szereplő információk megtalálhatók a [Munkahelyi portál alkalmazás üzeneteinek leírásában](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs) is.   

Szöveges üzenet  |Allow Company Portal to access photos, media, and files on your device? (Engedélyezi a Munkahelyi portál alkalmazásnak, hogy hozzáférjen az eszközén tárolt fényképekhez, médiatartalmakhoz és fájlokhoz?)  
---------|---------
Üzenet jelentése     |  Engedélyezi az eszköznek, hogy adatnaplókat írjon az eszköz SD-kártyájára, így USB-kábelen keresztül áthelyezhetővé válnak a naplók.   </br></br>**MEGJEGYZÉS: A Vállalati portál alkalmazás sohasem próbál hozzáférni a felhasználó fényképeihez, médiatartalmaihoz és fájljaihoz.** Az üzenet szövegét a Google szabja meg, és nem módosítható.     
Hol és mikor jelenik meg az üzenet  | Akkor jelenik meg az üzenet, amikor a felhasználók az **Adatküldés** elemre koppintva elküldik az adatnaplókat a rendszergazdának.|         
Mi történik, ha a felhasználók engedélyezik a hozzáférést  |  A naplók másolással az SD-kártyára kerülnek. |         
Mi történik, ha a felhasználók nem engedélyezik a hozzáférést     | Az adatnaplók elküldése ettől függetlenül továbbra is lehetséges, ám a naplók nem másolhatók az SD-kártyára.       </br></br> Amikor a felhasználók a hozzáférés megtagadása után másodszor bejelentkeznek a Vállalati portál alkalmazásba, az üzenetben látható egy **Ne jelenjen meg többé** feliratú jelölőnégyzet, amelynek bejelölésével végleg kikapcsolhatják az üzenet megjelenítését.</br></br>Ha a felhasználók engedélyezik a hozzáférést, de később megtagadják azt, az üzenet újból megjelenik majd, amikor a felhasználók a legközelebb megpróbálják elküldeni a naplókat.</br></br>Amennyiben a felhasználók később ismét engedélyezni szeretnék a hozzáférést, a **Beállítások** > **Alkalmazások** > **Vállalati portál** > **Engedélyek** > **Tárterület** lapon tehetik ezt meg.
További információ     |  Felhasználóknak: [Diagnosztikai adatok naplófájljainak elküldése e-mailben a rendszergazdának](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>Rendszergazdáknak: Az ebben a táblázatban szereplő információk megtalálhatók a [Munkahelyi portál alkalmazás üzeneteinek leírásában](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs) is.   


**iOS rendszerű Vállalati portál alkalmazás**
* A felhasználók már a Microsoft Outlookkal vagy más levelezőalkalmazásokkal is elküldhetik a rendszergazdának a diagnosztikai naplókat. Korábban ez csak a natív alkalmazással volt lehetséges.
* Javítottuk az Apple készülékregisztrációs programjához (DEP) és a vállalatok által regisztrált eszközökhöz nyújtott támogatást. A részletekért lásd: [A regisztráláskor a rendszer felkéri az eszköz azonosítására](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* A regisztrált eszközök felhasználói listájában ezentúl zöld pipa jelzi a felhasználó által éppen használt eszközt. A pipa hiányában korábban nem lehetett megállapítani, hogy a regisztrált eszközök melyikét használta éppen a felhasználó.

**Windowsos Munkahelyi portál alkalmazás**

A Microsoft termék- és szolgáltatásfejlesztési célból automatikus módszerekkel név nélküli adatokat gyűjt a munkahelyi portál teljesítményéről és használatáról. A végfelhasználók bármikor kikapcsolhatják az adatok gyűjtését eszközük használati adatokra vonatkozó beállításával, rendszergazdák azonban nem szabályozhatják az adatgyűjtést, és nem módosíthatják e beállítás végfelhasználói szakaszát.



## 2015. november
### Alkalmazáskezelés
Az Intune támogatja a mobilalkalmazás-kezelési (MAM) házirendeket, amelyek meggátolják, hogy vállalati adatok szivárogjanak ki a fogyasztói alkalmazásokba vagy szolgáltatásokba. Korábban ezek a házirendek csak olyan eszközökön futó mobilalkalmazásokon voltak kikényszerítve, amelyeket mobileszköz-kezelésre regisztráltak az Intune-ba.

Az ehavi frissítéssel az Intune új eszközosztályokra bővíti ki MAM-képességeit. Az Intune-ban regisztrált eszközök mellett most a következőkön kényszeríthet ki MAM-házirendeket:
* más eszközkezelési megoldások által kezelt eszközök
* eszközkezelési rendszerekben nem regisztrált eszközök, általában saját eszközök

A következő blogbejegyzésekben talál további információt ezen új MAM-képességekről:
* [A felügyelt mobiltermelékenység növelése](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [A Microsoft új nagyvállalati mobilitási képességei](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Ezenkívül itt találhat néhány részletet és további információkat az Intune MAM-szolgáltatásairól:
* A vállalati adatok el vannak különítve az ügyféladatoktól az Intune-hoz felkészített alkalmazásokban, beleértve az Office Mobile alkalmazásokat, az Intune SDK-t alkalmazó külső alkalmazásokat és az Intune által becsomagolt üzletági alkalmazásokat.
* A vállalati adatok megoszthatók (**kivághatók/másolhatók/beilleszthetők**) a vállalati alkalmazások között, mialatt meggátolható a vállalati adatok személyes alkalmazásokba való megosztása. A részletekért lásd: [A MAM-szabályzatok és az alkalmazásadatok védelme](https://technet.microsoft.com/library/mt627825.aspx). Ebben [A Microsoft Word alkalmazás használata munkahelyi és személyes teendők elvégzésére](https://technet.microsoft.com/library/mt627827.aspx) című példa forgatókönyvben láthatja, hogyan gátolja meg a rendszer a vállalati adatok személyes alkalmazásokba való megosztását.
* Kulcsfontosságú adatvesztés-megelőzési házirendek, például alkalmazásonkénti PIN-kód, mentés másként vezérlők és felügyelt adatmegosztás az alkalmazások között. Az összes házirend listájáért lásd: [Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban](https://technet.microsoft.com/library/mt627829.aspx).
* A Word, az Excel, a PowerPoint, az Outlook, a OneNote és a OneDrive Vállalati verzió is rendelkezik ezekkel az új képességekkel és eszközregisztrációval vagy anélkül is felügyelhető. Az adatvesztés-megelőzési képességek natív módon vannak beépítve a szabványos Office-alkalmazásokba az Apple Store vagy a Google Play áruházban, és nem igényelnek alkalmazásburkolást vagy közvetlen telepítést.
* Az első lépésekért lásd: [Ismerkedés a mobilalkalmazás-felügyeleti szabályzatokkal az Azure-portálon](https://technet.microsoft.com/library/mt627830.aspx). A mobilalkalmazás-felügyeleti házirendek konfigurálásával és telepítésével kapcsolatban lásd: [Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban](https://technet.microsoft.com/library/mt627829.aspx).
* Amikor a végfelhasználók a vállalati hitelesítő adataikkal hitelesítést végeznek az alkalmazásban, az adatvesztés-megelőzési képességek automatikusan be vannak állítva. A [Microsoft Intune-alapú mobilalkalmazás-kezelési házirendek hatálya alá tartozó alkalmazásokkal kapcsolatos végfelhasználói folyamatok](https://technet.microsoft.com/library/mt627827.aspx) című témakörben talál néhány példa forgatókönyvet a OneDrive iOS- és Androidos-eszközökön való elérésére.
* iOS- és Android-eszközökön is működik.

[A Microsoft Intune mobilalkalmazás-kezelési házirendekkel használható Microsoft-alkalmazások](https://technet.microsoft.com/library/dn708489.aspx) listája frissült, és megjeleníti a legújabb alkalmazásokat.

### Eszközkezelés
 **Mac OS X eszközkezelés** Az Intune-nal Mac OS X-eszközöket regisztrálhat és kezelhet. A következőket teheti a Mac OS X-eszközökkel:
* Az eszközök regisztrálása az Intune általi kezeléshez. Lásd: [Az iOS kezelésének beállítása a Microsoft Intune-nal](https://technet.microsoft.com/library/dn408185.aspx).
* Eszközbeállítások vezérlése általános konfigurációs házirenddel. Lásd: [A Mac OS X-konfigurációs házirendek beállításai a Microsoft Intune-ban](https://technet.microsoft.com/library/mt627823.aspx).
* Az Apple Configuratorral létrehozott Mac OS X-beállítások alkalmazása. Lásd: [Egyéni Mac OS X-házirendbeállítások a Microsoft Intune-ban](https://technet.microsoft.com/library/mt627820.aspx)-
* Hardver- és szoftverleltár készítése Mac OS X-eszközökről. Lásd: [A regisztrált eszközök áttekintése a Microsoft Intune leltárfunkciójával](https://technet.microsoft.com/library/jj733634.aspx).
* Új jelentések futtatása, amelyek részleteket jelenítenek meg a kezelt Mac OS X-eszközökről. Lásd: [A Microsoft Intune-műveletek értelmezése jelentések segítségével](https://technet.microsoft.com/library/dn646977.aspx).

**ÚJ Edge böngészőbeállítások Windows 10-eszközökre** Új beállítások érhetőek el a Windows 10 általános konfigurációs házirendjéhez, amelyekkel kezelheti a Microsoft Edge böngésző beállításait és szolgáltatásait. Lásd: [A Windows 10 konfigurációs házirendjének beállításai a Microsoft Intune-ban](https://technet.microsoft.com/library/mt404697.aspx).

**E-mail-profilok** Új e-mail-profilokra vonatkozó házirend érhető el a Windows 10-es asztali és Windows 10-es mobileszközökön. Lásd: [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](https://technet.microsoft.com/library/dn646984.aspx).

**Új megfelelőségiszabályzat-beállítások** Az alábbi új biztonsági és rendszerházirend-beállítások lettek hozzáadva a megfelelőségi szabályzatok listájához:
* Ahhoz, hogy a vállalati erőforrásokat elérő Windows 8.1-es vagy újabb verziójú eszközökön telepítve legyenek a legújabb frissítések, használja az **Automatikus frissítések megkövetelése** beállítást. Az automatikusan telepíteni kívánt frissítések típusát is meghatározhatja – vagy az összes fontosként megjelölt telepítendő frissítést, vagy az összes fontosként vagy ajánlottként megjelölt telepítést. A megfelelőségiházirend-beállítások teljes listájáért lásd: [A Microsoft Intune eszközmegfelelőségi házirendjeinek kezelése](https://technet.microsoft.com/library/dn705843.aspx).
* Az új **Jelszó kérése, amikor az eszköz visszatér inaktív állapotból** beállítást a meglévő **Jelszó kérése ennyi perc inaktivitás után** beállítással kombinálva olyan megfelelőségi beállítást hozhat létre, amelyhez a végfelhasználónak jelszót kell beírnia a bizonyos ideig inaktív eszközök használatához.

**Új feltételes hozzáférésiszabályzat-beállítások** **Minden felhasználóra** feltételes hozzáférési szabályzatot alkalmazhat az új vagy meglévő feltételes hozzáférési szabályzatokban. Az Intune és Office 365 programokhoz licenccel rendelkező összes felhasználónak regisztrálnia kell az eszközét, és ha az Intune nem támogatja az eszköz platformját, a hozzáférés le lesz tiltva az [Active Directory-hitelesítésalapú bejelentkezést (modern hitelesítést)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) használó ügyfélalkalmazások esetében.

Azt is megadhatja, hogy a feltételes hozzáférési házirend **minden platformra** érvényes legyen.  Az [Active Directory-hitelesítésalapú bejelentkezést (modern hitelesítést)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) használó összes ügyfélalkalmazásra érvényes a feltételes hozzáférési házirend, és ha a platformot nem támogatja az Intune, akkor le lesz tiltva.

### A Microsoft Munkahelyi portál szolgáltatásának módosításai és frissítései
Ebben a kiadásban a következő módosítások lettek bevezetve a vállalati portál alkalmazásaival kapcsolatban:

* **Android**: Egy új üdvözlőképernyő érhető el az androidos Munkahelyi portál alkalmazásban, amellyel a felhasználók jobban megérthetik a Munkahelyi portál alkalmazás célját. Ez a képernyő csökkenti az azon felhasználók általi letöltések számát, akiknek a vállalata nem Intune-előfizető.

* **iOS**: Az Intune már a Mac OS X rendszerű eszközök regisztrálását is támogatja a [Vállalati portál webhely](https://portal.manage.microsoft.com) használatával. Ehhez a [Mac OS X-eszköz regisztrálása az Intune-ban](https://technet.microsoft.com/library/mt598622.aspx) című rész ad útmutatást.

* **Vállalati portál webhely**: Azok a felhasználók, akik regisztrálták az eszközeiket az Intune-ban, most már közvetlenül a Munkahelyi portál webhelyen tudnak új PIN-kódot készíteni maguknak az **Új PIN-kód** lehetőséget választva. Korábban ez csak a rendszergazdán keresztül volt lehetséges. Windows 8.1-es és Windows RT rendszerű eszközökön nem működik az Új PIN-kód lehetőség. Más rendszerű eszközökön pedig csak akkor jelenik meg, ha az adott eszköz regisztrálva van a mobileszköz-kezelési szolgáltatásban vagy az Exchange ActiveSync mobileszköz-kezelési moduljában. Az [Új PIN-kód készítése](https://technet.microsoft.com/library/mt590895.aspx) című részben útmutatást talál mindehhez.

### Változások a globális rendszergazdai licencelésben
Októberben megosztottuk, hogy a globális rendszergazdák (másnéven a bérlő rendszergazdák) folytathatják a mindennapos adminisztrációs feladataikat különálló Intune- vagy Nagyvállalati mobilitási csomag- (EMS-) licenc nélkül. Ha azonban a globális rendszergazdák a szolgáltatást szeretnék használni, például a saját eszközük vagy vállalati eszköz regisztrálásához vagy a munkahelyi Intune portál használatához, Intune- vagy EMS-licencre van szükségük, mint minden más felhasználónak. Az alábbiakban további részleteket olvashat erről.
* A munkahelyi Intune portálon a végfelhasználók a következőket tehetik:
    * az eszköz regisztrálása;
    * Az eszközök állapotának megtekintése
    * olyan szoftver letöltése, amelyet globális rendszergazda telepített a szervezetbe;
    * a globális rendszergazda által közzétett hivatkozások megkeresése arról, hogyan léphetnek kapcsolatba az informatikai részleggel.

    [További információk a munkahelyi portálról](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) és [a munkahelyi portál testreszabásának módjáról](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* Az Intune vagy az EMS megvásárlásához a szervezet nevében feliratkozó személy automatikusan az első globális rendszergazdává válik a bérlőben. Az ősszel az Intune elkezdett automatikusan hozzárendelni Intune- vagy EMS-licencet az első globális rendszergazdához az [Office 365 portálra](http://portal.office.com/) való átállás és az [Intune fiókportál](http://account.manage.microsoft.com/) megszűnésének részeként. Az összes további hozzáadott globális rendszergazda folytathatja a mindennapos adminisztrációt különálló Intune- vagy EMS-licenc nélkül. Ha végfelhasználói műveleteket végeznek, és regisztrálják a saját (vagy vállalati) eszközüket, vagy szoftvert töltenek le a vállalati portálról, akkor licencre van szükségük, mint bármely más felhasználónak.
* A változást fokozatosan vezetjük be 2016 januárjától.
* A Microsoft partnereit ez a változás nem befolyásolja abban, hogy az ügyfeleik nevében biztosítsák a szolgáltatást. A végfelhasználói feladatokhoz a felhasználóknak Intune- vagy EMS-licencre van szükségük az eszköz regisztrálásához és a szoftver a munkahelyi portálról való eléréséhez és letöltéséhez.

Ha kérdései vannak ezzel a változtatással kapcsolatban, vegye fel a kapcsolatot az Intune támogatási csapatával:
* [A Microsoft Intune támogatási csatornái](https://technet.microsoft.com/library/jj839713.aspx)
* [Közösségi támogatás](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Általános Microsoft Intune-visszajelzés, beleértve a tervátalakítási kérések (DCR-ek) elküldése vagy hibák jelentése érdekében látogasson el az [Intune felhasználói visszajelzési webhelyére](https://microsoftintune.uservoice.com/).


### Újdonságok az Intune-ban – 2015. november
**Új tartalom**
* [A Mac OS X-konfigurációs házirendek beállításai a Microsoft Intune-ban](https://technet.microsoft.com/library/mt627823.aspx): A Mac OS X-eszközök eszközbeállításainak és szolgáltatásainak vezérlése.
* [Egyéni Mac OS X-házirendbeállítások a Microsoft Intune-ban](https://technet.microsoft.com/library/mt627820.aspx): Az Apple Configurator eszközzel létrehozott Mac OS X-eszközbeállítások telepítése.
* [Adatveszteség-megelőzési alkalmazásszabályzatok konfigurálása Microsoft Intune-ban](https://technet.microsoft.com/library/mt627825.aspx): Azon forgatókönyvekről tartalmaz információt, amelyeket a mobilalkalmazás-kezelési házirendek támogatnak, valamint arról, hogyan védi a házirend az adatokat.
* [Ismerkedés a mobilalkalmazás-felügyeleti szabályzatokkal az Azure-portálon](https://technet.microsoft.com/library/mt627830.aspx): A mobilalkalmazás-kezelési házirendek használatának az Azure Betekintő portálon való elkezdéséhez szükséges információk.
* [Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban](https://technet.microsoft.com/library/mt627829.aspx): Részletes útmutató arról, hogyan hozhat létre mobilalkalmazás-kezelési házirendeket az Azure Betekintő portálon.
* [Mobilalkalmazás-felügyeleti szabályzatok figyelése a Microsoft Intune-nal](https://technet.microsoft.com/library/mt627824.aspx): Információ arról, hogyan figyelheti meg a mobilalkalmazás-kezelési házirendeket az Azure Betekintő portálon.
* [A Microsoft Intune mobilalkalmazás-kezelési házirendjei és az iOS megnyitási engedélyei](https://technet.microsoft.com/library/mt627821.aspx): Információ arról, hogyan működnek a mobilalkalmazás-kezelési házirendek az iOS megnyitás a következőben szolgáltatásával.
* [Microsoft Intune-alapú mobilalkalmazás-kezelési szabályzatok hatálya alá tartozó alkalmazásokkal kapcsolatos végfelhasználói folyamatok](https://technet.microsoft.com/library/mt627827.aspx): Milyen a végfelhasználói élmény mobilalkalmazás-kezelési házirenddel társított alkalmazások használatakor.
* [A Microsoft Intune-nal felügyelt vállalati alkalmazások adatainak törlése](https://technet.microsoft.com/library/mt627826.aspx): A vállalati alkalmazásadatok eltávolításának módja.

**Frissített tartalom**
* [A Windows 10 konfigurációs házirendjének beállításai a Microsoft Intune-ban](https://technet.microsoft.com/library/mt404697.aspx): Új Edge-böngészőbeállítások.
* [Az iOS kezelésének beállítása a Microsoft Intune-nal](http://technet.microsoft.com/library/dn408185.aspx): További információk a Mac OS X-eszközök regisztrálásáról.
* [A regisztrált eszközök áttekintése a Microsoft Intune leltárfunkciójával](https://technet.microsoft.com/library/jj733634.aspx): További információk a Mac OS X-eszközökről gyűjtött leltárról. Ezenkívül az összes eszközplatformra vonatkozó legújabb információkkal frissült a témakör.
* [A Microsoft Intune-műveletek értelmezése jelentések segítségével](https://technet.microsoft.com/library/dn646977.aspx): További információk a felügyelt Mac OS X-eszközökkel kapcsolatos információk megjelenítésére használt két új jelentésről.
* [A Microsoft Intune eszközmegfelelőségi házirendjeinek kezelése](https://technet.microsoft.com/library/dn705843.aspx): További információk az automatikus frissítések és jelszó megkövetelésének új megfelelőségi házirendjeiről, amikor egy eszköz inaktív állapotból tér vissza.
* [E-mail hozzáférés kezelése a Microsoft Intune-nal](https://technet.microsoft.com/library/dn705841.aspx): További információ arról, hogy a feltételes hozzáférési házirend hogyan alkalmazható az összes platformra és az összes felhasználóra.
* [A SharePoint Online-hozzáférés kezelése a Microsoft Intune-nal](https://technet.microsoft.com/library/dn705844.aspx): További információ arról, hogy a feltételes hozzáférési házirend hogyan alkalmazható az összes platformra és az összes felhasználóra.

## 2015. október

### Feltételes hozzáférés frissítései helyszíni Exchange esetén
**Most engedélyezheti az Exchange ActiveSync e-mailek elérését az Intune-nal regisztrált, az előírásoknak megfelelő eszközök számára, amikor a globális Exchange-szabály Letiltás vagy Karantén értékű** Eddig a regisztrált vagy az előírásoknak megfelelő eszközökön az e-mail-elérés engedélyezéséhez **Engedélyezés** értékűre kellett állítani az alapértelmezett globális Exchange-szabályt.

Ezzel a szolgáltatásfrissítéssel többé nincs szükség erre a beállításra a feltételes eléréshez. Ha az Exchange-környezet megköveteli, hogy az alapértelmezett globális szabály értéke **Letiltás/Karantén** legyen, jelölje be az Exchange helyszíni feltételes hozzáférési szabályzat lapján az **Alapértelmezett szabály felülbírálása** jelölőnégyzetet. Az [E-mail hozzáférés kezelése a Microsoft Intune-nal](https://technet.microsoft.com/library/dn705841.aspx) témakör további részleteket tartalmaz a szabályokról és az eredményül kapott végfelhasználói értesítésekről.

**Karantén mostantól egy kattintással** Egyszerűsítettük az e-mailek karanténba helyezését az egykattintásos regisztrálás engedélyezése érdekében. Ezzel a szolgáltatásfrissítéssel a végfelhasználók a karanténba helyezett e-mailben egyetlen hivatkozásra kattintva végezhetik el a regisztrációs folyamatot a munkahelyiportál-alkalmazásban.
### Mobileszköz- és alkalmazásfelügyeleti frissítések
**Android** Az Intune összes felügyeleti funkciója mostantól támogatja az Android 6.0 (Marshmallow) rendszert, a következő blogbejegyzésben leírtaknak megfelelően: [Microsoft Intune Provides Day 0 Support for Android Marshmallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)(A Microsoft Intune azonnali támogatást nyújt az Android Marshmallow rendszerhez).

**iOS** Az iOS 7.1-es verziójánál régebbi rendszerű iOS-eszközökhöz már nem készíthetők új alkalmazástelepítések. Az ilyen eszközökhöz készült meglévő alkalmazáspéldányok azonban továbbra is működni fognak az Intune-ban, és a kezelésük is ott történik.

**Windows 10** Az Intune mostantól támogatja az univerzális Windows 10-alkalmazások telepítését a **Windows-alkalmazáscsomag** szoftvertelepítő-típus használatával. A követelményekkel kapcsolatban további információkat [Az alkalmazások telepítésének első lépései a Microsoft Intune-ban](http://technet.microsoft.com/en-US/library/dn646955.aspx) című témakörben talál.


### A Microsoft vállalati portál alkalmazásainak módosításai és frissítései
A következő módosításokat végeztük el a vállalati portál alkalmazások ezen kiadásain: **iOS** Új gombokkal bővült a Vállalati portál alkalmazás, így a felhasználók egyszerűbben tudják elküldeni a diagnosztikai naplókat a rendszergazdáknak:

|Gomb neve|Megjelenési helye|
|------------|---------------|
|Jelentés|Riasztási hibaüzenetek|
|Diagnosztikai jelentés küldése|A Munkahelyi portál alkalmazás Névjegy képernyője|


>[!div class="step-by-step"]

>[&larr; **[!div class="step-by-step"]**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Jul16_HO1-->


