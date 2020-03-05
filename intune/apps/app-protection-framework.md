---
title: Adatvédelmi szabályzatok az alkalmazás-védelmi házirendek használatával
titleSuffix: Microsoft Intune
description: Ismerje meg, hogy az alkalmazás-védelmi szabályzatok (alkalmazás) miként gondoskodnak arról, hogy a szervezet adatbiztonsága biztonságos vagy egy felügyelt alkalmazásban legyen, függetlenül attól, hogy az eszköz regisztrálva van-e.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: smithre4
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc2843073d11e5c9dae989a60f357dcfeb16a5d2
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290808"
---
# <a name="data-protection-framework-using-app-protection-policies"></a>Adatvédelmi szabályzatok az alkalmazás-védelmi házirendek használatával 

Ahogy egyre több szervezet valósít meg mobileszköz-stratégiákat a munkahelyi vagy iskolai adatok eléréséhez, az adatszivárgás elleni védelem a legfontosabb. Az Intune Mobile Application Management megoldás az adatszivárgás elleni védelemhez az alkalmazás-védelmi szabályzatok (alkalmazás). Az alkalmazás olyan szabályok, amelyek biztosítják, hogy a szervezet által tárolt adatmennyiség biztonságban maradjon, vagy egy felügyelt alkalmazásban legyenek, függetlenül attól, hogy az eszköz regisztrálva van-e. További információ: az [app Protection-házirendek áttekintése](~/apps/app-protection-policy.md). 

Az alkalmazás-védelmi szabályzatok konfigurálásakor a különböző beállítások és beállítások száma lehetővé teszi a szervezetek számára, hogy a védelmet az adott igényeknek megfelelően testre szabják. A rugalmasság miatt előfordulhat, hogy nem nyilvánvaló, hogy a teljes forgatókönyv megvalósításához szükség van a házirend-beállításokra. Annak érdekében, hogy a szervezetek a megerősítő törekvéseket rangsorolják, a Microsoft új besorolást vezetett be a [biztonsági konfigurációkhoz a Windows 10](https://aka.ms/secconframework)rendszerben, az Intune pedig kihasználja ezt a besorolást az alkalmazás-adatvédelmi keretrendszerhez a Mobile App Management szolgáltatásban.  

Az alkalmazás adatvédelmi konfigurációs keretrendszere három különböző konfigurációs forgatókönyvbe van rendezve: 

- 1\. szint vállalati alapszintű adatvédelem – a Microsoft javasolja ezt a konfigurációt egy vállalati eszköz minimális adatvédelmi konfigurációjának megfelelően. 

- 2\. szint nagyvállalati adatok védelme – a Microsoft javasolja ezt a konfigurációt olyan eszközöknél, amelyekben a felhasználók bizalmas vagy bizalmas információkat férnek hozzá. Ez a konfiguráció a munkahelyi vagy iskolai adatokhoz hozzáférő legtöbb mobil felhasználóra érvényes. Egyes vezérlők befolyásolhatják a felhasználói élményt. 

- 3\. szint nagyvállalati szintű adatvédelem – a Microsoft javasolja ezt a konfigurációt egy nagyobb vagy összetettebb biztonsági csapattal rendelkező szervezet által működtetett eszközökhöz, vagy adott felhasználók vagy csoportok számára, amelyek egyedi módon nagy kockázattal rendelkeznek (például egy szervezet azonosított felhasználók, akik a lopás által közvetlenül és jelentős mértékben befolyásolhatják a készlet árát. A szervezetnek valószínűleg a jól finanszírozott és a kifinomult ellenfeleknek kell megcéloznia ezt a konfigurációt. 

## <a name="app-data-protection-framework-deployment-methodology"></a>Az alkalmazások adatvédelmi keretrendszerének üzembe helyezési módszertana 

Csakúgy, mint az új szoftverek, funkciók vagy beállítások bármely üzembe helyezéséhez, a Microsoft javasolja, hogy az alkalmazás adatvédelmi keretrendszerének üzembe helyezése előtt tesztelje az érvényesítési teszteket. Az üzembe helyezési körök meghatározása általában egyszeri esemény (vagy legalábbis ritka), de újra fel kell vennie ezeket a csoportokat annak érdekében, hogy az előkészítés még helyes legyen. 

A Microsoft a következő üzembe helyezési kör megközelítését javasolja az alkalmazás adatvédelmi keretrendszere számára: 

| Üzembe helyezési kör  | Bérlő  | Értékelő csapatok  | Kimenet  | Idővonal  |
|--------------------|------------------------|-------------------------------------------------------------------|----------------------------------------------------------|----------------------------------------|
| Minőségbiztosítás  | Üzem előtti bérlő  | Mobil képesség tulajdonosai, biztonság, kockázatértékelés, adatvédelem, UX  | Funkcionális forgatókönyvek ellenőrzése, vázlat dokumentációja  | 0-30 nap  |
| Előzetes  | Üzemi bérlő  | Mobil képesség tulajdonosai, UX  | Végfelhasználói forgatókönyv érvényesítése, felhasználó felé irányuló dokumentáció  | 7-14 nap, utólagos minőségi garancia  |
| Éles  | Üzemi bérlő  | Mobil képesség tulajdonosai, informatikai ügyfélszolgálat  | –  | 7 nap több hétre, post Preview  |

A fenti táblázat azt jelzi, hogy az alkalmazás-védelmi szabályzatok összes módosítását először üzem előtti környezetben kell végrehajtani, hogy tisztában legyen a házirend-beállítás következményeivel. A tesztelés befejezése után a változtatások behelyezhetők a termelési környezetbe, és alkalmazhatók az éles felhasználók egy részhalmazára, általában az IT-részlegre és az egyéb kapcsolódó csoportokra. Végül pedig a bevezetést elvégezheti a mobil felhasználói Közösség többi részén is. Az éles környezetbe való bevezetés hosszabb időt is igénybe vehet, attól függően, hogy milyen hatással van a változásra. Ha nincs felhasználói befolyás, a változásnak gyorsan el kell indulnia, míg ha a változás a felhasználó által kifejtett hatást eredményez, előfordulhat, hogy a bevezetésnek lassabbnak kell lennie, mivel a felhasználók populációjának módosításait kell kommunikálni. 

Ha egy alkalmazás módosításait teszteli, vegye figyelembe a [kézbesítés időzítését](~/apps/app-protection-policy-delivery.md). Egy adott felhasználóhoz tartozó alkalmazás-kézbesítés állapota figyelhető. További információ: [az alkalmazás-védelmi szabályzatok figyelése](~/apps/app-protection-policies-monitor.md). 

Az egyes alkalmazásokra vonatkozó egyéni Alkalmazásbeállítások az Edge-t használó eszközökön és a következő URL-címen ellenőrizhetők *: Intunehelp*. További információ: az [ügyfélalkalmazás-védelmi naplók áttekintése](~/apps/app-protection-policy-settings-log.md) és a [webes elérés kezelése a Microsoft Edge és a Microsoft Intune használatával](~/apps/manage-microsoft-edge.md#use-microsoft-edge-on-ios-to-access-managed-app-logs). 

## <a name="app-data-protection-framework-settings"></a>Az alkalmazás adatvédelmi keretrendszerének beállításai 

A következő alkalmazás-védelmi házirend-beállításokat engedélyezni kell a megfelelő alkalmazásokhoz, és az összes mobil felhasználóhoz hozzá kell rendelni őket. Az egyes házirend-beállításokkal kapcsolatos további információkért lásd az [iOS-alkalmazások védelmére vonatkozó házirend-beállítások](~/apps/app-protection-policy-settings-ios.md) és az [Android-alkalmazások védelmi házirendjének beállításai](~/apps/app-protection-policy-settings-android.md)című témakört. 

A Microsoft javaslatot tesz a használati forgatókönyvek áttekintésére és kategorizálására, majd a felhasználók konfigurálására az adott szinthez tartozó előírásos útmutatás alapján. A bármely keretrendszerhez hasonlóan előfordulhat, hogy a megfelelő szinten lévő beállításokat a szervezet igényeinek megfelelően módosítani kell, mivel az adatvédelem a fenyegetések környezetét, a kockázatkezelést és a használhatóságot befolyásolja.  

### <a name="apps-to-include-in-the-app-protection-policies"></a>Az alkalmazás-védelmi szabályzatokban szerepeltetni kívánt alkalmazások  

Az egyes alkalmazás-védelmi szabályzatok esetében a következő alapvető Microsoft-alkalmazásokat kell figyelembe venni: 

- Edge 
- Excel 
- Iroda 
- OneDrive 
- OneNote 
- Outlook 
- PowerPoint 
- Microsoft Teams 
- Microsoft To-Do
- Word 
- Microsoft SharePoint 

A szabályzatoknak más, üzleti igényeknek megfelelő Microsoft-alkalmazásokat kell tartalmazniuk, a szervezeten belül használt Intune SDK-t, valamint az Intune SDK-t integráló üzletági alkalmazásokat, valamint az [Intune SDK](~/developer/app-sdk.md) -t (vagy már burkolta). 

### <a name="level-1-enterprise-basic-data-protection"></a>1\. szintű vállalati alapszintű adatvédelem 

Az 1. szint a vállalati mobileszköz minimális adatvédelmi konfigurációja. Ez a konfiguráció a munkahelyi vagy iskolai adatokhoz való hozzáféréshez, a munkahelyi vagy iskolai fiókadatok titkosításához, valamint az iskolai vagy munkahelyi adatok szelektív törléséhez szükséges PIN-kód beírásával lecseréli az alapvető Exchange online eszköz-hozzáférési házirendeket. Az Exchange online eszköz-hozzáférési házirendektől eltérően azonban a házirendben kiválasztott összes alkalmazásra érvényesek az alkalmazás védelmi házirendjének beállításai, így biztosítva, hogy az adatokhoz való hozzáférés a mobil üzenetkezelési helyzetekben is védve legyen. 

Az 1. szintű szabályzatok ésszerű adathozzáférési szintet tesznek elérhetővé, miközben minimálisra csökkentik a felhasználókra gyakorolt hatást, és az adatvédelmi szabályzatok Microsoft Endpoint Managerben való létrehozásakor az alapértelmezett adatvédelmi és hozzáférési követelményekre vonatkozó beállításokat tükrözik.  

#### <a name="data-protection"></a>Adatvédelem 

| Beállítás | Beállítás leírása |             Érték  |             Platfvagym        |
|-----------------|--------------------------------------------------------|-----------------------|----------------------------------------|
| Adatátvitel |             Szervezeti adatbázis biztonsági mentése...  |             Engedélyezett  |             iOS/iPadOS, Android        |
| Adatátvitel |       Szervezeti adatküldés más alkalmazásokba  |             Minden alkalmazás  |             iOS/iPadOS, Android        |
| Adatátvitel |       Adatok fogadása más alkalmazásokból  |             Minden alkalmazás  |             iOS/iPadOS, Android        |
| Adatátvitel |       Kivágási, másolási és beillesztési műveletek korlátozása az alkalmazások között  |             Bármely alkalmazás  |             iOS/iPadOS, Android        |
| Adatátvitel |       Harmadik féltől származó billentyűzetek  |             Engedélyezett  |             iOS/iPadOS        |
| Adatátvitel |       Jóváhagyott billentyűzetek  |             Nem kötelező  |             Android:        |
| Adatátvitel |       Képernyőfelvétel és Google Assistant  |             Engedélyezett  |             Android:        |
| Encryption |             Szervezeti adataik titkosítása  |             Kötelező  |             iOS/iPadOS, Android        |
| Encryption |       Szervezeti adataik titkosítása a regisztrált eszközökön  |             Kötelező  |             Android:        |
| Funkció  |             Alkalmazás szinkronizálása a natív névjegyek alkalmazással  |             Engedélyezett  |             iOS/iPadOS, Android        |
| Funkció  |       Szervezeti adattárolók nyomtatása  |             Engedélyezett  |             iOS/iPadOS, Android        |
| Funkció  |       Webes tartalmak átvitelének korlátozása más alkalmazásokkal  |             Bármely alkalmazás  |             iOS/iPadOS, Android        |
| Funkció  |       Szervezeti adatértesítések  |             Engedélyezett  |             iOS/iPadOS, Android        |

#### <a name="access-requirements"></a>Hozzáférési követelmények 

| Beállítás  | Érték  | Platfvagym  | Megjegyzések  |
|----------------------------------------------------------------|---------------|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Hozzáférési PIN-kód  | Kötelező  | iOS/iPadOS, Android  |   |
| PIN-kód típusa  | Numerikus  | iOS/iPadOS, Android  |   |
| Egyszerű PIN-kód  | Engedélyezett  | iOS/iPadOS, Android  |   |
| PIN-kód minimális hosszának kiválasztása  | 4  | iOS/iPadOS, Android  |   |
| Biometrikus adat PIN-kód helyett hozzáféréshez  | Engedélyezett  | iOS/iPadOS, Android  |   |
| A biometrikus felülbírálása PIN-kód helyett hozzáféréshez  | Kötelező  | iOS/iPadOS, Android  |   |
| Időkorlát (a tevékenység percben)  | 720  | iOS/iPadOS, Android  |   |
| Face ID PIN-kód helyett a hozzáféréshez  | Engedélyezett  | iOS/iPadOS  |   |
| PIN-kód alaphelyzetbe állítása napok száma után  | Nem  | iOS/iPadOS, Android  |   |
| Alkalmazás PIN-kódja az eszköz PIN-kódjának beállításakor  | Kötelező  | iOS/iPadOS, Android  | Ha az eszköz regisztrálva van az Intune-ban, a rendszergazdák megtekinthetik a "nem kötelező" beállítást, ha az eszköz megfelelőségi szabályzatán keresztül erős eszköz PIN-kódot kényszerítenek ki.  |
| Munkahelyi vagy iskolai fiók hitelesítő adatai a hozzáféréshez  | Nem kötelező  | iOS/iPadOS, Android  |   |
| A hozzáférési követelmények ismételt ellenőrzési művelete (perc inaktivitás után)  | 30  | iOS/iPadOS, Android  |   |

#### <a name="conditional-launch"></a>Feltételes indítás 

| Beállítás | Beállítás leírása |          Érték/művelet  |          Platfvagym        | Megjegyzések |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Alkalmazási feltételek |       PIN-kód maximális száma  |          5/alaphelyzetbe állítás PIN-kód  |          iOS/iPadOS, Android  |                  |
| Alkalmazási feltételek |       Offline türelmi időszak  |          720/hozzáférés letiltása (perc)  |          iOS/iPadOS, Android  |                  |
| Alkalmazási feltételek |       Offline türelmi időszak  |          90/adatok törlése (nap)  |          iOS/iPadOS, Android  |                  |
| Eszköz feltételei  |       Feltört eszközök  |        Hozzáférés letiltása  |          iOS/iPadOS, Android  |                  |
| Eszköz feltételei  |       Biztonság-eszköz igazolása  |          Alapszintű integritás és tanúsított eszközök/hozzáférés tiltása  |          Android:  |          <p>Ez a beállítás a Google biztonság igazolását konfigurálja a végfelhasználói eszközökön. Az alapszintű integritás érvényesíti az eszköz integritását. A feltört eszközök, emulátorok, virtuális eszközök és eszközök, amelyekkel a rendszer nem módosítja az alapszintű integritást. </p><p> Az alapszintű integritás és a tanúsított eszközök ellenőrzi az eszköz kompatibilitását a Google szolgáltatásaival. Csak a Google által hitelesített, nem módosított eszközök adhatják át ezt az ellenőrzést.</p>  |
| Eszköz feltételei  |       Veszélyforrások vizsgálatának megkövetelése az alkalmazásokban  |        Hozzáférés letiltása  |          Android:  |          Ezzel a beállítással biztosíthatja, hogy a Google ellenőrzési alkalmazások vizsgálata be legyen kapcsolva a végfelhasználói eszközökön. Ha be van állítva, a végfelhasználó le lesz tiltva, amíg be nem kapcsolják a Google alkalmazásnak az Android-eszközön való vizsgálatát.        |

#### <a name="level-2-enterprise-enhanced-data-protection"></a>2\. szint nagyvállalati szintű adatvédelem 

A 2. szint az adatvédelmi konfiguráció ajánlott szabványként olyan eszközök esetében, amelyekben a felhasználók bizalmas adatokat férnek hozzá. Ezek az eszközök a vállalatok természetes célpontja. Ezek a javaslatok nem feltételezik a magasan képzett biztonsági szakemberek nagy létszámát, ezért a legtöbb vállalati szervezet számára elérhetőnek kell lenniük. Ez a konfiguráció az 1. szint konfigurációját az adatátviteli forgatókönyvek korlátozásával, valamint az operációs rendszer minimális verziójának megkövetelésével bővíti. 

A 2. szinten kikényszerített házirend-beállítások közé tartozik az 1. szinthez ajánlott összes házirend-beállítás, és csak az 1. szintű vezérlők és kifinomultabb konfiguráció megvalósításához szükséges, illetve az alábbi házirend-beállítások hozzáadása vagy frissítése. Habár ezek a beállítások valamivel nagyobb hatással lehetnek a felhasználókra vagy az alkalmazásokra, az adatvédelem szintjének nagyobb mértékben vannak kikényszerítve, hogy a felhasználók bizalmas információkhoz hozzáférjenek a mobileszközökön. 

#### <a name="data-protection"></a>Adatvédelem 

| Beállítás | Beállítás leírása |             Érték  |             Platfvagym        | Megjegyzések |
|---------------|----------------------------------------------------------|-----------------------------------------------|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Adatátvitel |       Szervezeti adatbázis biztonsági mentése...  |          Letiltás  |          iOS/iPadOS, Android  |                  |
| Adatátvitel |       Szervezeti adatküldés más alkalmazásokba  |          Szabályzattal felügyelt alkalmazások  |          iOS/iPadOS, Android  |          <p>Az iOS/iPadOS segítségével a rendszergazdák úgy konfigurálhatják ezt az értéket, hogy "házirend által felügyelt alkalmazások", "házirend által felügyelt alkalmazások az operációs rendszer megosztásával", vagy "házirend által felügyelt alkalmazások megnyitási/megosztási szűréssel". </p><p>A házirend által felügyelt alkalmazások az operációs rendszer megosztásával is elérhetők, ha az eszköz regisztrálva van az Intune-ban. Ez a beállítás lehetővé teszi az adatátvitelt más házirend által felügyelt alkalmazásokra, valamint az Intune által felügyelt más alkalmazásokba való fájlátvitelt. </p><p>A házirend által felügyelt alkalmazások megnyitási/megosztási szűréssel az operációs rendszer megnyitási/megosztási párbeszédpaneljein csak a szabályzat által felügyelt alkalmazások jelennek meg. </p><p> További információ: iOS- [alkalmazás védelmi szabályzatának beállításai](~/apps/app-protection-policy-settings-ios.md).</p> |
| Adatátvitel |       Szervezeti adatmásolatok mentése  |          Letiltás  |          iOS/iPadOS, Android  |                  |
| Adatátvitel |       Másolatok mentésének engedélyezése a felhasználók számára a kiválasztott szolgáltatásokban  |          OneDrive for Business, SharePoint Online |          iOS/iPadOS, Android  |                  |
| Adatátvitel |       Kivágási, másolási és beillesztési műveletek korlátozása az alkalmazások között  |          Szabályzattal felügyelt alkalmazások beillesztési lehetőséggel  |          iOS/iPadOS, Android  |                  |
| Adatátvitel |       Képernyőfelvétel és Google Assistant  |          Letiltás  |          Android:  |                  |
| Funkció |       Webes tartalmak átvitelének korlátozása más alkalmazásokkal  |          Microsoft Edge  |          iOS/iPadOS, Android  |                  |
| Funkció |       Szervezeti adatértesítések  |          Szervezeti adattárolók letiltása  |          iOS/iPadOS, Android  |          Az ezt a beállítást támogató alkalmazások listáját az [iOS-alkalmazások védelmére vonatkozó házirend-beállítások](~/apps/app-protection-policy-settings-ios.md) és az Android- [alkalmazások védelmi szabályzatának beállításai](~/apps/app-protection-policy-settings-android.md)című témakörben tekintheti meg.       |


#### <a name="conditional-launch"></a>Feltételes indítás

| Beállítás | Beállítás leírása |          Érték/művelet  |          Platfvagym        | Megjegyzések |
|--------------------|----------------------------|-----------------------------------------------------------|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Eszköz feltételei  |       Minimális operációsrendszer-verzió  |          *Formátum: főverzió. alverzió. Build <br>példa: 12.4.4* /letiltás hozzáférés |          iOS/iPadOS        | A Microsoft azt javasolja, hogy a Microsoft-alkalmazások támogatott iOS-verzióinak megfelelően konfigurálja az iOS főverziójának minimális verzióját.   A Microsoft-alkalmazások egy N-1 módszert támogatnak, ahol N a jelenlegi iOS-es főverzió verziója. A kisebb és a Build verzió értékeihez a Microsoft azt javasolja, hogy az eszközök naprakészek legyenek a megfelelő biztonsági frissítésekkel. Az Apple legújabb javaslataira vonatkozó [Apple biztonsági frissítések](https://support.apple.com/en-us/HT201222) megtekintése |
| Eszköz feltételei  |       Minimális operációsrendszer-verzió  |          *Formátum: főverzió. alverzió<br> példa: 8,0* /hozzáférés tiltása   |          Android:        | A Microsoft javasolja a minimális androidos verzió konfigurálását, hogy az megfeleljen a Microsoft apps által támogatott Android-verzióknak. Az Android Enterprise által ajánlott követelményeknek megfelelő számítógépgyártóknak és eszközöknek támogatnia kell az aktuális szállítási kiadást + egy betűs frissítést.   Az Android jelenleg az Android 8,0-es és újabb verzióit javasolja az ismeretek feldolgozói számára.   Tekintse meg az androidos [nagyvállalatok számára ajánlott követelményeket](https://www.android.com/enterprise/recommended/requirements/) az Android legújabb javaslataihoz |
| Eszköz feltételei  |       Javítás minimális verziója  |          *Formátum: éééé-hh-nn <br> példa: 2020-01-01* /hozzáférés letiltása  |          Android:        | Az Android-eszközök havi biztonsági javításokat kaphatnak, de a kiadás a számítógépgyártóktól és/vagy a szállítóktól függ. A szervezeteknek biztosítaniuk kell, hogy a telepített Android-eszközök biztonsági frissítéseket kapjanak a beállítás megvalósítása előtt. Tekintse meg az [androidos biztonsági közleményeket](https://source.android.com/security/bulletin/) a legújabb javítási kiadásokhoz.  |

#### <a name="level-3-enterprise-high-data-protection"></a>3\. szint nagyvállalati szintű adatvédelem 

A 3. szint a nagy és kifinomult biztonsági szervezetekkel rendelkező szervezetek számára ajánlott adatvédelmi konfiguráció, vagy adott felhasználók és csoportok számára, akiket az ellenfelek egyedileg céloznak meg. Ezeket a szervezeteket általában jól finanszírozott és kifinomult ellenfelek célozzák meg, és így érdemes a további megkötéseket és vezérlőket is kipróbálni. Ez a konfiguráció a 2. szintű konfigurációra támaszkodik a további adatátviteli forgatókönyvek korlátozásával, a PIN-kód konfigurációjának összetettségének növelésével és a mobil veszélyforrások észlelésének hozzáadásával.  

A 3. szinten kikényszerített házirend-beállítások közé tartozik a 2. és az 1. szinthez ajánlott összes házirend-beállítás, és csak az alábbi házirend-beállítások hozzáadása vagy frissítése szükséges a szigorú adatvédelmi konfiguráció és vezérlők megvalósításához. Ezek a házirend-beállítások potenciálisan jelentős hatással lehetnek a felhasználókra vagy az alkalmazásokra, és a megcélzó fenyegetésekkel arányos biztonsági szintet kényszerítenek.  

#### <a name="data-protection"></a>Adatvédelem

| Beállítás | Beállítás leírása |             Érték  |             Platfvagym        | Megjegyzések |
|---------------|---------------------------------------|----------------------------------------|--------------------------------------|---------------------------------------------------------------------------------------------------------|
| Adatátvitel |       Adatok fogadása más alkalmazásokból  |          Szabályzattal felügyelt alkalmazások  |          iOS/iPadOS, Android         |  |
| Adatátvitel |       Harmadik féltől származó billentyűzetek  |          Letiltás  |          iOS/iPadOS        | Az iOS-ben ez letiltja az összes külső gyártótól származó billentyűzet működését az alkalmazáson belül.  |
| Adatátvitel |       Jóváhagyott billentyűzetek  |          Kötelező  |          Android:        | Android esetén a billentyűzeteket ki kell választani ahhoz, hogy használni lehessen az üzembe helyezett Android-eszközök alapján.  |
| Adatátvitel |       Válassza ki a jóváhagyni kívánt billentyűzeteket  |          *Válassza ki a kívánt billentyűzeteket*  |          Android:        | Android esetén a billentyűzeteket ki kell választani ahhoz, hogy használni lehessen az üzembe helyezett Android-eszközök alapján.  |

#### <a name="access-requirements"></a>Hozzáférési követelmények

|       Beállítás  |          Érték  |          Platfvagym  |
|-----------------------------------------------------------|--------------------|---------------------------------|
|       Egyszerű PIN-kód  |          Letiltás  |          iOS/iPadOS, Android  |
|       PIN-kód minimális hosszának kiválasztása  |          6  |          iOS/iPadOS, Android  |
|       PIN-kód alaphelyzetbe állítása napok száma után  |          Igen  |          iOS/iPadOS, Android  |
|       Napok száma  |          365  |          iOS/iPadOS, Android  |
|       Válassza ki a megtartani kívánt korábbi PIN-értékek számát  |          5  |          Android:  |

#### <a name="conditional-launch"></a>Feltételes indítás

| Beállítás | Beállítás leírása |          Érték/művelet  |          Platfvagym        | Megjegyzések |
|----------------------------|--------------------------------------|-------------------|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       Eszköz feltételei  |          Függetlenített/feltört eszközök  |        Adatok törlése  |          iOS/iPadOS, Android        |  |
|       Eszköz feltételei  |          Maximálisan megengedett fenyegetési szint  |          Biztonságos/letiltási hozzáférés  |          iOS/iPadOS, Android        | <p>A nem regisztrált eszközöket a Mobile Threat Defense használatával lehet megvizsgálni a fenyegetések ellen. További információ: [Mobile Threat Defense a nem regisztrált eszközökhöz](https://aka.ms/mtdmamdocs).      </p><p>     Ha az eszköz regisztrálva van, ez a beállítás kihagyható a Mobile Threat Defense a regisztrált eszközökön való üzembe helyezése mellett. További információ: [Mobile Threat Defense a regisztrált eszközökhöz](~/protect/mtd-device-compliance-policy-create.md).</p> |

## <a name="next-steps"></a>További lépések

- [Alkalmazásvédelmi szabályzatok létrehozása és telepítése Microsoft Intune-ban](app-protection-policies.md)
- [Az Android-alkalmazások elérhető védelmi házirendjének beállításai a Microsoft Intune](app-protection-policy-settings-android.md)
- [Az iOS/iPadOS app Protection házirend-beállításai a Microsoft Intune](app-protection-policy-settings-ios.md)

## <a name="see-also"></a>További információ

- A harmadik féltől származó alkalmazások, például a Salesforce mobilalkalmazás, speciális módon működnek együtt az Intune-nal a vállalati adatok védelme érdekében. Ha szeretne többet megtudni arról, hogy a Salesforce alkalmazás konkrétan hogyan működik együtt az Intune-nal (az MDM alkalmazáskonfigurációs beállításait is beleértve), olvassa el [A Salesforce alkalmazás és a Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) című témakört.
