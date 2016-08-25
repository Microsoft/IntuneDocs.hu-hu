---
title: "Adatok védelme mobilalkalmazás-kezelési házirendekkel a Microsoft Intune segítségével | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: a140a2f634397440b35786e7afb3165dccc7d93e


---

# Configure and deploy mobile application management policies in the Microsoft Intune console
A Microsoft Intune mobilalkalmazás-kezelési szabályzatai lehetővé teszik a telepített alkalmazások funkcióinak módosítását, ezzel segítenek elérni, hogy összhangba kerüljenek vállalata megfelelőségi és biztonsági szabályzataival. Például korlátozhatja a kezelt alkalmazások kivágási, másolási és beillesztési műveleteit, vagy konfigurálhat egy alkalmazást arra, hogy az összes webes hivatkozás egy kezelt böngészőben nyíljon meg.

A mobilalkalmazás-kezelési házirendek a következőket támogatják:

-   Az Android 4-es vagy újabb verzióját futtató eszközök

-   Az iOS 7-es vagy újabb verzióját futtató eszközök

> [!TIP]
> A mobilalkalmazás-kezelési szabályzatok az Intune-ban regisztrált eszközökre alkalmazhatók.
>
> Ha olyan eszközökre vonatkozóan szeretne alkalmazáskezelési szabályzatokat létrehozni, amelyeket nem az Intune felügyel, olvassa el a következő cikket: [Alkalmazásadatok védelme mobilalkalmazás-kezelési szabályzatokkal a Microsoft Intune segítségével](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

Az Intune más szabályzataitól eltérően a mobilalkalmazás-kezelési szabályzatok alkalmazása nem közvetlenül történik, hanem úgy, hogy a házirendet társítja a korlátozni kívánt alkalmazással. Az alkalmazás központi és az eszközökön való telepítése után az Ön által megadott beállítások lépnek életbe.

Ahhoz, hogy korlátozásokat lehessen alkalmazni egy alkalmazásra, az alkalmazásnak tartalmaznia kell a Microsoft Intune App SDK-t. Ilyen típusú alkalmazást az alábbi három módszerrel lehet beszerezni:

-   **Házirend által kezelt alkalmazás használata** – Beépített App SDK-val rendelkezik. Ilyen típusú alkalmazások hozzáadásához meg kell adnia az alkalmazás hivatkozását egy alkalmazás-áruházból, például az iTunes vagy Google Play áruházból. Az ilyen típusú alkalmazáshoz nincs szükség további feldolgozásra. Itt megtekintheti [a Microsoft Intune mobilalkalmazás-kezelési szabályzatokkal használható alkalmazásokat](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

-   **Becsomagolt alkalmazás használata** – Alkalmazások, amelyek abból a célból lettek újracsomagolva a **Microsoft Intune alkalmazásburkoló eszközzel**, hogy tartalmazzák az App SDK-t. Ez az eszköz általában a házon belül létrehozott vállalati alkalmazások feldolgozásához használatos. Nem használható az alkalmazás-áruházból letöltött alkalmazások feldolgozásához. További információ: [iOS-alkalmazások mobilalkalmazás-kezeléshez való előkészítése a Microsoft Intune alkalmazásburkoló eszközével](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) és [Android-alkalmazások előkészítése mobilalkalmazás-felügyelethez a Microsoft Intune alkalmazásburkoló eszközével](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

- **Saját alkalmazás írása, amely tartalmazza az Intune App SDK-t** – Az Intune App SDK lehetővé teszi alkalmazáskezelési funkciók beépítését a készített alkalmazásokba. További információ: [Az Intune App SDK áttekintése](/intune/develop/intune-app-sdk)

Ha segítségre van szüksége az alkalmazásburkoló eszköz és az Intune App SDK közötti választáshoz, olvassa el a következőt: [Annak eldöntése, hogyan készíti elő az alkalmazásokat a mobilalkalmazás-kezeléshez a Microsoft Intune-nal](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

Néhány kezelt alkalmazás, például az iOS és az Android rendszer Outlook alkalmazása támogatja a **többszörös identitást**. Ez azt jelenti, hogy az Intune csak az alkalmazásban lévő vállalati fiókokra vagy adatokra alkalmazza a felügyeleti beállításokat.

Az Outlook alkalmazás használata esetén például:

-   Ha a felhasználó egy vállalati és egy személyes e-mail fiókot konfigurál, az Intune csak a vállalati fiókra alkalmazza a felügyeleti beállításokat, és a személyes fiókot nem felügyeli.

-   Az eszköz kivonása vagy a regisztrációja megszüntetése esetén a rendszer csak a vállalati Outlook-adatokat távolítja el az eszközről.

-   A használt vállalati fióknak egyeznie kell azzal a fiókkal, amelyet az eszköz az Intune-nal végzett regisztrációhoz használt.

> [!TIP]
> Ha a Configuration Managerrel használja az Intune-t, olvassa el az [Alkalmazások vezérlése mobilalkalmazás-felügyeleti szabályzatokkal a Configuration Managerben](https://technet.microsoft.com/library/mt131414.aspx) című témakört.

## Alkalmazás létrehozása és telepítése mobilalkalmazás-kezelési házirenddel

-   **1. lépés:** Hivatkozás beszerzése egy házirend által kezelt alkalmazáshoz, becsomagolt alkalmazás létrehozása, vagy az Intune App SDK használata MAM-kompatibilis alkalmazások írásához.

-   **2. lépés:** Az alkalmazás közzététele a felhőalapú tárhelyén.

-   **3. lépés:** Mobilalkalmazás-kezelési házirend létrehozása.

-   **4. lépés:** Az alkalmazás telepítése úgy, hogy társítja egy mobilalkalmazás-kezelési házirenddel.

-   **5. lépés:** Az alkalmazás telepítésének figyelése.

## **1. lépés:** Hivatkozás beszerzése egy házirend által kezelt alkalmazáshoz, becsomagolt alkalmazás létrehozása, vagy az Intune App SDK használata MAM-kompatibilis alkalmazások írásához.

-   **Egy házirend által kezelt alkalmazás hivatkozásának beszerzése az alkalmazásáruházban** – Az App Store-ban keresse meg és jegyezze fel a telepíteni kívánt, házirend által kezelt alkalmazás URL-címét.

    Az iPad Microsoft Word alkalmazás URL-címe például a következő: **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**


## **2. lépés:** Az alkalmazás közzététele a felhőalapú tárhelyén
Amikor közzétesz egy kezelt alkalmazást, az eljárások különböznek attól függően, hogy a közzétenni kívánt alkalmazás házirend által kezelt-e, vagy olyan alkalmazás, amelynek a feldolgozása a Microsoft Intune App Wrapping Tool for iOS eszközzel történt.

#### Házirend által kezelt alkalmazás közzététele

1.  Ha készen áll rá, hogy feltöltse az alkalmazást a felhőtárhelyre, járjon el a következő cikk utasításai szerint: [Alkalmazások hozzáadása Microsoft Intune-beli mobileszközökhöz](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  iOS-alkalmazások esetén válassza a **Kezelt iOS-alkalmazás az alkalmazás-áruházból**lehetőséget az **Adja meg, hogy hogyan legyen elérhetővé téve a szoftver az eszközöknek**csoportban.

    Android-alkalmazások esetén válassza a **Külső hivatkozás**lehetőséget.

3.  Az **URL-cím megadása**csoportban írja be a házirend által kezelt alkalmazás korábban feljegyzett URL-címét.

Ha befejeződött a feltöltés, a feltöltött alkalmazás **Szoftver tulajdonságai** lapján az **Igen** szó lesz látható az **Alkalmazáskezelési házirendek** beállításnál.

Ha meggyőződött arról, hogy az alkalmazás sikeresen feltöltődött, folytassa a 3. lépéssel.

#### A Microsoft Intune alkalmazásburkoló eszközzel feldolgozott alkalmazás közzététele

1.  Ha készen áll rá, hogy feltöltse az alkalmazást a felhőtárhelyre, járjon el a következő cikk utasításai szerint: [Alkalmazások hozzáadása Microsoft Intune-beli mobileszközökhöz](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Válassza a **Szoftvertelepítő**lehetőséget az **Adja meg, hogy hogyan legyen elérhetővé téve a szoftver az eszközöknek**csoportban.

3.  Válassza a **Csomag hozzáadása iOS-hez (&#42;.ipa-fájl)** lehetőséget a **Szoftvertelepítő fájltípusa** csoportban.

Ha befejeződött a feltöltés, a feltöltött alkalmazás **Szoftver tulajdonságai** lapján az **Igen** szó lesz látható az **Alkalmazáskezelési házirendek** beállításnál.

Ha meggyőződött arról, hogy az alkalmazás sikeresen feltöltődött, folytassa a 3. lépéssel.

## **3. lépés:** Mobilalkalmazás-kezelési házirend létrehozása

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) válassza a **Házirend** &gt; **Áttekintés** &gt; **Házirend hozzáadása** elemet.

2.  Konfigurálja és alkalmazza az alábbi **szoftverházirendek** egyikét attól függően, hogy milyen típusú eszközhöz szeretne alkalmazásokat konfigurálni:

    -   **Mobilalkalmazás-kezelési házirend (Android 4 és újabb)**

    -   **Mobilalkalmazás-kezelési házirend (iOS 7 és újabb)**

    Használhatja az ajánlott beállításokat, vagy testre is szabhatja a beállításokat. További információt [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) című témakörben találhat.

3.  Adja meg saját igényeinek megfelelően a következő beállításokat: A beállítások eltérhetnek attól függően, hogy a házirendet milyen típusú eszközhöz konfigurálja.

|Beállítás neve|Részletek|
    |---------|--------------------|
    |**Név**|Adja meg a házirend nevét.|
    |**Leírás**|Ha szeretne, adjon meg egy leírást a házirendhez.|
    |**A vállalat által kezelt böngészőben megjelenő webtartalom korlátozása**|Ha engedélyezve van ez a beállítás, az alkalmazásban szereplő esetleges hivatkozások a kezelt böngészőben fognak megnyílni. Ahhoz, hogy működjön ez a beállítás, az alkalmazásnak telepítve kell lennie az eszközökön.|
    |**Android-biztonsági mentések tiltása** vagy **iTunes- és iCloud-biztonsági mentések tiltása**|Információk biztonsági mentésének letiltása az alkalmazásból.|
    |**Más alkalmazásokból való adatátvitel engedélyezése az alkalmazásnak**|Megadhatja azokat az alkalmazásokat, amelyekbe ez az alkalmazás adatokat küldhet. Választhat, hogy letiltja, illetve csak más kezelt alkalmazásokba vagy bármely alkalmazásba engedélyezi az adatátvitelt. Ez a beállítás nem szabályozza a mobileszközök **Megnyitás a következőben** funkciójának használatát.<br /><br />Például ha nem engedélyezi az adatátvitelt, azzal megakadályozza az olyan szolgáltatásoknak való adatátvitelt, mint az SMS-üzenetkezelés, képek hozzárendelése a kapcsolatokhoz és a közzététel a Facebook-on vagy a Twitteren.<br /><br />iOS-eszközök esetén a kezelt és nem kezelt alkalmazások közötti dokumentumátvitel letiltásához egy olyan mobileszköz-biztonsági házirendet is konfigurálnia és alkalmaznia kell, amely letiltja a **Kezelt dokumentumok engedélyezése más nem kezelt alkalmazásokban** beállítást. Ha csak más kezelt alkalmazásokba engedélyezi az átvitelt, az Intune PDF- és képmegtekintői (ha telepítve vannak) lesznek használva a megfelelő típusú tartalmak megnyitásához.<br /><br />A **Házirend által felügyelt alkalmazások** vagy a **Nincs** beállítás alkalmazása esetén le lesz tiltva az iOS 9 rendszernek az a funkciója, amely lehetővé teszi, hogy a Spotlight-keresés adatokat keressen az alkalmazásokon belül.|
    |**Más alkalmazásokból való adatfogadás engedélyezése az alkalmazásnak**|Megadhatja azokat az alkalmazásokat, amelyekből ez az alkalmazás adatokat fogadhat. Választhat, hogy teljesen letiltja, vagy csak más kezelt alkalmazásokból, illetve bármely alkalmazásból engedélyezi az adatátvitelt.<br /><br />A többszörös identitást támogató iOS-alkalmazások esetében (ahol az Intune csak vállalati fiókokra vagy adatokra alkalmazza a felügyeleti beállításokat az alkalmazásban), amikor a felhasználók mobilalkalmazás-kezelési házirenddel ellátott regisztrált eszközükről mobilalkalmazás-kezelési házirend által nem felügyelt alkalmazásból érnek el adatokat, azokat a rendszer a házirend által védett vállalati adatokként kezeli.|
    |**A „Mentés másként” művelet letiltása**|Bármely ezt a házirendet alkalmazó alkalmazásban letiltja a **Mentés másként** művelet használatát adatok személyes felhőbeli tárolókba (mint például a személyes OneDrive vagy a Dropbox) való mentéséhez.|
    |**Kivágási, másolási és beillesztési műveletek korlátozása más alkalmazásokkal**|Megadhatja, hogy miként legyen használható a kivágási, a másolási és a beillesztési művelet az alkalmazással. A következő lehetőségek közül választhat:<br /><br />**Letiltva** – A kivágási, másolási és beillesztési műveletek letiltása az alkalmazás és más alkalmazások között.<br /><br />**Házirend által felügyelt alkalmazások** – A kivágási, másolási és beillesztési műveletek engedélyezése csak az alkalmazás és más kezelt alkalmazások között.<br /><br />**Házirend által felügyelt alkalmazások beillesztési lehetőséggel** – Az alkalmazásból kivágott vagy másolt adatok beillesztésének engedélyezése más kezelt alkalmazásokba. Egy tetszőleges alkalmazásból kivágott vagy másolt adatok beillesztésének engedélyezése ebbe az alkalmazásba.<br /><br />**Bármely alkalmazás** – Nincs korlátozás az alkalmazásba vagy alkalmazásból történő kivágási, másolási és beillesztési műveletekre vonatkozóan.<br /><br />Ahhoz, hogy adatokat lehessen másolni és beilleszteni kezelt alkalmazások között, mindkét alkalmazásban a **Házirend által felügyelt alkalmazások** vagy a **Házirend által felügyelt alkalmazások beillesztési lehetőséggel** beállításnak kell konfigurálva lennie.|
    |**Egyszerű PIN-kód szükséges a hozzáféréshez**|A felhasználónak meg kell adnia az alkalmazás használatához megadott PIN-kódot. A felhasználót a rendszer az alkalmazás első futtatásakor kéri a kód beállítására.|
    |**Kísérletek száma a PIN-kód alaphelyzetbe állítása előtt**|Megadhatja, hogy hány alkalommal lehet megkísérelni a PIN-kód megadását, mielőtt a felhasználót a rendszer a PIN-kód alaphelyzetbe állítására kényszerítené.|
    |**Vállalati hitelesítő adatok szükségesek a hozzáféréshez**|A felhasználónak meg kell adnia vállalati bejelentkezési adatait, mielőtt hozzáférhetne az alkalmazáshoz.|
    |**A vállalati házirenddel való eszközkompatibilitás szükséges a hozzáféréshez**|Az alkalmazás használata csak akkor engedélyezett, ha az eszköz nincs feltörve.|
    |**A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)**|Az **Időtúllépés** mezőben adja meg azt az időtartamot, amennyi elteltével szeretné, hogy megtörténjen az alkalmazás hozzáférési követelményeinek ismételt ellenőrzése az alkalmazás elindítása után.|
    |**Offline türelmi időszak**|Ha az eszköz offline állapotban van, itt megadhatja azt az időtartamot, amennyi elteltével szeretné, hogy megtörténjen az alkalmazás hozzáférési követelményeinek ismételt ellenőrzése.|
    |**Alkalmazásadatok titkosítása**|Megadhatja, hogy titkosítva legyenek az alkalmazással társított alkalmazások, beleértve a külsőleg (például SD-kártyán) tárolt adatokat is.<br /><br />**Titkosítás iOS rendszerhez**<br /><br />Az Intune valamely mobilalkalmazás-kezelési házirendjével társított alkalmazások esetén az adatok titkosítása az iOS által biztosított eszközszintű titkosítással történik. Ez az eszköz PIN-házirendjén keresztül engedélyezhető, amelyet be kell állítania a rendszergazdának. Ha szükség van PIN-kódra, az adattitkosítás a mobilalkalmazás-kezelési házirendben megadott beállítások szerint történik. Az Apple dokumentációjában leírtaknak megfelelően [az iOS 7 által használt modulokra érvényes a FIPS 140-2 tanúsítvány](http://support.apple.com/en-us/HT202739).<br /><br />**Titkosítás Android rendszerhez**<br /><br />Az Intune valamely mobilalkalmazás-kezelési házirendjével társított alkalmazások esetén a titkosítást a Microsoft biztosítja. A rendszer szinkron módon titkosítja az adatokat a fájlok írási és olvasási műveletei során.  Az eszköz tárhelyén található tartalom mindig titkosított marad. A titkosítási módszerre nem érvényes a FIPS 140-2 típusú tanúsítvány.|
    |**Képernyőrögzítés letiltása** (csak Android-eszközök esetén)|Megadhatja, hogy az eszköz képernyő-rögzítési lehetőségei le legyenek tiltva az alkalmazás használatakor.|

4.  Ha elkészült, válassza a **Házirend mentése** elemet.

Az új szabályzat a **Házirend** munkaterület **Konfigurációs szabályzatok** csomópontjában jelenik meg.

## **4. lépés:** Az alkalmazás társítása egy mobilalkalmazás-kezelési házirenddel, majd az alkalmazás telepítése
Az alkalmazás telepítésekor gondoskodjon arról, hogy a **Mobilalkalmazás-kezelés** lapon a mobilalkalmazás-kezelési házirend kiválasztásával társítja a házirendet az alkalmazással.

További információt az [Alkalmazások telepítése a Microsoft Intune-ban](deploy-apps.md) című témakörben találhat.

> [!IMPORTANT]
> Az iOS 7.1-es verziójánál korábbi operációs rendszereket futtató eszközök esetén a társított házirendek nem lesznek eltávolítva az alkalmazás eltávolításakor.
>
> Ha az eszközt kiléptetik az Intune-ból, a rendszer nem távolítja el a házirendeket az alkalmazásokból; az alkalmazások, amelyekre házirendeket alkalmaztak, eltávolítás és újratelepítés után is megőrzik a házirend-beállításokat.

### Teendők, ha egy alkalmazás már üzembe van helyezve az eszközökön
Előfordulhat, hogy egy alkalmazás telepítésekor a célcsoportba tartozó felhasználók vagy eszközök egyike már rendelkezik a telepített alkalmazás nem felügyelt verziójával, például telepítette a Microsoft Wordöt az alkalmazás-áruházból.

Ilyenkor meg kell kérnie a felhasználót, hogy manuálisan távolítsa el a nem felügyelt verziót az Ön által konfigurált felügyelt verzió telepítéséhez.

Az iOS 9-es vagy újabb verziójával futó eszközök esetében az Intune automatikusan engedélyt kér a felhasználótól a meglévő alkalmazás felügyeletének átvételére. Ha az engedélyt megadják, az alkalmazás az Intune felügyelete alá kerül, és az összes Ön által hozzárendelt mobilalkalmazás-felügyeleti házirend érvényes lesz rá.

> [!TIP]
> Ha az eszköz felügyelt módban van, az Intune a felhasználó engedélyének kikérése nélkül átveszi a meglévő alkalmazás felügyeletét.

## **5. lépés:** Az alkalmazás telepítésének figyelése.
Miután létrehozott és telepített egy mobilalkalmazás-kezelési házirenddel társított alkalmazást, a következő eljárásokkal figyelheti az alkalmazást, és feloldhatja az esetleges házirendütközéseket.

#### A telepítés állapotának megtekintése

1.  A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) válassza a **Csoportok** &gt; **Áttekintés** lehetőséget.

2.  Hajtsa végre az alábbi lépések egyikét:

    -   Válassza a **Minden felhasználó** elemet, majd kattintson duplán arra a felhasználóra, akinek az eszközét meg szeretné vizsgálni. A **Felhasználó tulajdonságai** lapon válassza az **Eszközök** elemet, majd kattintson duplán arra az eszközre, amelyet meg szeretne vizsgálni.

    -   Válassza a **Minden eszköz** &gt; **Minden mobileszköz** elemet. Az **Eszközcsoport tulajdonságai** lapon válassza az **Eszközök** elemet, majd kattintson duplán arra az eszközre, amelyet meg szeretne vizsgálni.

3.  A **Mobileszköz tulajdonságai** lapon válassza a **Házirend** elemet az eszközre alkalmazott mobilalkalmazás-kezelési házirendek megtekintéséhez.

4.  Jelölje ki azt a mobilalkalmazás-kezelési házirendet, amelynek meg szeretné tekinteni az állapotát. A házirend adatait az alsó ablaktáblában, a beállításait pedig a hozzá tartozó csomópont kibontásával tekintheti meg.

5.  Az egyes mobilalkalmazás-kezelési házirendek **Állapot** oszlopában a **Megfelel**, **Megfelel (függőben)**vagy a **Hiba** szó látható. Ha a kijelölt házirend egy vagy több beállítása ütközik, a mezőben a **Hiba** szó fog megjelenni.

6.  Ha azonosított egy ütközést, ellenőrizheti, hogy az ütköző házirend-beállítások ugyanazt a beállítást használják-e, vagy alkalmazhat csupán egy házirendet az alkalmazásra és a felhasználóra.

### Házirend-ütközések feloldása
Ha a felhasználó vagy eszköz első telepített példányán ütközik egy mobilalkalmazás-kezelési házirend, az ütközésben lévő beállításérték el lesz távolítva az alkalmazásra alkalmazott házirendből, és az alkalmazás egy beépített ütközési értéket fog használni.

Ha az alkalmazás vagy felhasználó későbbi telepített példányain ütközik egy mobilalkalmazás-kezelési házirend, az ütközésben lévő beállításérték nem fog frissülni az alkalmazásra alkalmazott mobilalkalmazás-kezelési házirenden, az alkalmazás pedig a beállítás meglévő értékét fogja használni.

Azokban az esetekben, amikor az eszköz vagy a felhasználó két ütköző házirendet kap, a következő viselkedés tapasztalható:

-   Ha egy házirend már alkalmazva lett az eszközre, a meglévő házirend-beállítások nem íródnak felül.

-   Ha még nem lett alkalmazva házirend az eszközre, és két ütköző beállítás van használatban, az eszközbe épített alapértelmezett beállítás használatos.



<!--HONumber=Jun16_HO4-->


