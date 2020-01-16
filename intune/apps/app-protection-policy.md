---
title: Alkalmazásvédelmi szabályzatok áttekintése
titleSuffix: Microsoft Intune
description: Hogyan segítik a Microsoft Intune alkalmazásvédelmi szabályzatai a céges adatok védelmét és az adatvesztés megelőzését.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c340ffaacad303c4ff395c84d92e3907e42a521
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036651"
---
# <a name="app-protection-policies-overview"></a>Alkalmazásvédelmi szabályzatok áttekintése

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazás-védelmi szabályzatok (alkalmazás) olyan szabályok, amelyek biztosítják, hogy a szervezet adatbiztonsága biztonságos maradjon, vagy egy felügyelt alkalmazásban legyen. A szabályzat egyfelől lehet olyan szabály, amely olyankor lép életbe, amikor a felhasználó megpróbál hozzáférni „céges” adatokhoz vagy áthelyezni azokat, másfelől azon műveletek csoportja, amelyeket a rendszer tilt vagy figyel, amikor az felhasználó az alkalmazást használja. A felügyelt alkalmazásra alkalmazásvédelmi szabályzatok vonatkoznak, és az Intune-nal felügyelhető.

A Mobile Application Management (MAM) alkalmazás-védelmi szabályzatok lehetővé teszik a szervezet adatainak kezelését és védelmét egy alkalmazáson belül. Ha a **MAM regisztráció nélkül** (MAM-We) dolgozik, a bizalmas adatokat tartalmazó munkahelyi vagy iskolai alkalmazások szinte bármilyen [eszközön](app-management.md#app-management-capabilities-by-platform)kezelhetők, beleértve a **saját** eszközökön (BYOD) lévő személyes eszközöket is. Több irodai alkalmazás is felügyelhető az Intune MAM-mel, például a Microsoft Office-alkalmazások. Tekintse meg a nyilvános használatra elérhető [Microsoft Intune védett alkalmazások](apps-supported-intune-apps.md) hivatalos listáját.

## <a name="how-you-can-protect-app-data"></a>Az alkalmazásadatok védelme
Az alkalmazottak mobileszközöket használnak a személyes és munkahelyi feladatokhoz. A produktív munkavégzést elősegítő környezet megteremtése mellett a véletlen vagy szándékos adatveszteség megelőzése is fontos szempont egy vállalatban. Azoknak a vállalati adatoknak a védelme is fontos, amelyeket nem az Ön felügyelete alatt álló eszközökről érnek el.

Az Intune alkalmazásvédelmi szabályzatai **a mobileszköz-felügyeleti (MDM) megoldásoktól függetlenül** használhatók. Ennek köszönhetően a vállalati adatokat attól függetlenül védheti, hogy regisztrálta-e az eszközöket egy eszközfelügyeleti megoldásba. Az **alkalmazásszintű házirendek** érvénybe léptetésével korlátozhatja a vállalati erőforrásokhoz való hozzáférést, és az informatikai részleg adatainak is nagyobb védelmet nyújthat.

### <a name="app-protection-policies-on-devices"></a>Alkalmazás-védelmi szabályzatok az eszközökön

Az alkalmazásvédelmi szabályzatok olyan eszközökön futó alkalmazásokhoz konfigurálhatók, amelyek:

- **Regisztrálva vannak a Microsoft Intune-ban:** Ezek általában vállalati tulajdonú eszközök.

- **Regisztrálva vannak egy harmadik fél mobileszköz-felügyeleti (MDM) megoldásában:** Ezek általában vállalati tulajdonú eszközök.

  > [!NOTE]
  > A mobilalkalmazás-felügyeleti szabályzatokat nem ajánlott külső mobileszköz-felügyeleti biztonságos tárolómegoldásokkal együtt használni.

- **Nincs regisztrálva mobileszköz-kezelési megoldásban:** Ezek az eszközök jellemzően olyan alkalmazottak tulajdonában lévő eszközök, amelyek nincsenek felügyelve vagy regisztrálva az Intune-ban vagy más MDM-megoldásokban.

> [!IMPORTANT]
> Mobilalkalmazás-kezelési házirendeket hozhat létre az Office 365-szolgáltatásokhoz kapcsolódó Office-mobilalkalmazások számára. Emellett a helyszíni Exchange-postafiókok hozzáférését is védheti, az iOS és Android rendszerű Outlookhoz készült Intune alkalmazásvédelmi szabályzatok létrehozásával és a hibrid modern hitelesítés engedélyezésével. A funkció használata előtt győződjön meg arról, hogy megfelel az [iOS-es és Androidos Outlook követelményeinek](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Az alkalmazásvédelmi szabályzatok a helyszíni Exchange-hez vagy a SharePoint-szolgáltatásokhoz kapcsolódó egyéb alkalmazások esetében nem támogatottak.

## <a name="benefits-of-using-app-protection-policies"></a>Az alkalmazás-védelmi szabályzatok használatának előnyei

Az alkalmazás-védelmi szabályzatok használatának fontos előnyei a következők:

- **A vállalati adatok védelme az alkalmazás szintjén.** Mivel a mobilalkalmazás-felügyelet nem igényel eszközkezelést, a felügyelt és a nem felügyelt eszközökön is biztosíthatja a vállalati adatok védelmét. A felügyelet a felhasználói azonosítón alapul, így nincs szükség az eszközkezelőre.

- **Nem érinti a végfelhasználói hatékonyságot, és a szabályzatok nem érvényesek, ha személyes környezetben használják az alkalmazást.** A szabályzatok kizárólag munkahelyi környezetben vannak alkalmazva, így a vállalati adatok védelmét a személyes adatok érintése nélkül biztosíthatja.

- **Az alkalmazás-védelmi szabályzatok gondoskodnak arról, hogy az alkalmazás-réteg védelme érvényben legyen.** Lehetőség van például a következőkre:
  - PIN-kódot kérhet egy alkalmazás vállalati környezetben való megnyitásához 
  - Szabályozhatja az adatok megosztását az alkalmazások között 
  - Megakadályozhatja az alkalmazásadatok személyes tárhelyre való mentését

- A **MAM mellett a Mdm is gondoskodik róla, hogy az eszköz védve**legyen. Segítségével például PIN-kódot kérhet az eszköz eléréséhez, vagy felügyelt alkalmazásokat telepíthet az eszközre. Az MDM-megoldáson keresztül is telepíthet alkalmazásokat, így jobban szabályozhatja az alkalmazáskezelést.

Az MDM-megoldások és alkalmazásvédelmi szabályzatok együttes használata további előnyökkel is jár, és a vállalatoknál az alkalmazásvédelmi szabályzatok MDM-megoldásokkal és azok nélkül is használhatók. Vegyünk például egy alkalmazottat, aki egy munkahelyi telefont és egy saját táblagépet használ. A munkahelyi telefon regisztrálva van az MDM-ben, és érvényesek rá az alkalmazásvédelmi szabályzatok, míg a személyes eszközt csak az alkalmazásvédelmi szabályzatok védik.

Ha a MAM-szabályzatot az eszköz állapotának beállítása nélkül alkalmazza a felhasználóra, a felhasználó megkapja a MAM-szabályzatot a BYOD-eszközön és az Intune által felügyelt eszközön is. Egy MAM-szabályzatot a felügyelt állapot alapján is alkalmazhat. Tehát amikor létrehoz egy alkalmazás-védelmi házirendet, a **cél elem mellett minden alkalmazás típusa**beállításnál válassza a **nem**lehetőséget. Ezután tegye a következők valamelyikét:
- Alkalmazzon kevésbé szigorú MAM-szabályzatot az Intune által felügyelt eszközökre, és alkalmazzon egy szigorúbb MAM-szabályzatot a nem MDM regisztrált eszközökre.
- MAM-szabályzat alkalmazása csak a nem regisztrált eszközökre.

## <a name="supported-platforms-for-app-protection-policies"></a>Az alkalmazásvédelmi szabályzatok által támogatott platformok

Az Intune számos szolgáltatással segít a szükséges alkalmazások üzembe helyezésében azokon az eszközökön, amelyeken futtatni kívánják azokat. További információ: alkalmazás- [felügyeleti képességek platform alapján](app-management.md#app-management-capabilities-by-platform).

Az Intune app Protection-házirendek platform támogatja az Office Mobile Application Platform-támogatást az Android-és iOS-eszközökhöz. További információt az [Office rendszerkövetelményeit](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg) ismertető témakör **mobilalkalmazásokkal** foglalkozó szakaszában talál.

> [!IMPORTANT]
> A Intune Céges portál az eszközön kell megadnia az alkalmazás-védelmi szabályzatok Android rendszeren való fogadásához. További információ: [Intune céges portál Access apps-követelmények](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Az alkalmazásvédelmi szabályzatok és az alkalmazásadatok védelme

### <a name="apps-without-app-protection-policies"></a>Alkalmazásvédelmi szabályzat nélküli alkalmazások

A korlátozások nélkül használt alkalmazások miatt összekeveredhetnek a vállalati és személyes adatok. Adatvesztéssel járhat, ha a vállalati adatok személyes tárolókra vagy az Ön hatáskörén kívüli alkalmazásokba kerülnek. A következő ábrán látható nyilak a vállalati és a személyes alkalmazások, valamint a tárolási helyek közötti korlátlan adatáthelyezést mutatják.

![Az alkalmazások közötti adatáthelyezésre szolgáló elméleti rendszerkép a szabályzatok nélkül](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Adatvédelem az App Protection-szabályzatokkal (alkalmazás)

Az alkalmazás-védelmi házirendek használatával megakadályozhatja a vállalati adatok mentését az eszköz helyi tárolójába (lásd az alábbi ábrát). Emellett korlátozható a más, alkalmazásvédelmi szabályzatokkal nem védett alkalmazásokba irányuló adattovábbítás. Íme néhány az alkalmazásvédelmi szabályzatok beállításai közül:
- Adatáthelyezési szabályzatok, például **a szervezeti adatpéldányok mentése**, valamint a **Kivágás, másolás és beillesztés korlátozása**.
- A hozzáférési szabályzat beállításai, például **Egyszerű PIN-kód megkövetelése a hozzáféréshez** és **A felügyelt alkalmazások futásának letiltása a függetlenített vagy feltört eszközökön**.

![A szabályzatok által védett vállalati adatok megjelenítését bemutató fogalmi rendszerkép](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Adatvédelem az ALKALMAZÁSsal az MDM-megoldás által felügyelt eszközökön

Az alábbi ábrán a MDM és az alkalmazás-védelmi szabályzatok által kínált védelmi rétegek láthatók.

![Az alkalmazásvédelmi szabályzatok BYOD-eszközökön való működését bemutató kép](./media/app-protection-policy/app-protection-policies-with-mdm.png)

A MDM-megoldás a következőket biztosítja az érték hozzáadásával:

- Regisztrálja az eszközt
- Telepíti az alkalmazásokat az eszközön
- Folyamatosan ellenőrzi az eszköz megfelelőségét és felügyeletét

Az alkalmazás-védelmi házirendek értéket adnak hozzá az alábbiak biztosításával:

- A vállalati adatok védelme a fogyasztói alkalmazásokba és szolgáltatásokba való szivárgás révén
- Korlátozások alkalmazása, például *Mentés másként*, *vágólap*vagy *PIN-kód*az ügyfélalkalmazások számára
- A vállalati adatok törlése az alkalmazásokból az eszközről való eltávolítása nélkül

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Adatvédelem az ALKALMAZÁSsal a regisztráció nélküli eszközökhöz

Az alábbi ábra azt szemlélteti, hogyan működnek az adatvédelmi szabályzatok az alkalmazás szintjén MDM nélkül.

![Az a rendszerkép, amely bemutatja, hogyan működnek az adatvédelmi szabályzatok az eszközökön regisztráció nélkül (nem felügyelt eszközök)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

Mivel az MDM-megoldás nem regisztrálja a BYOD-eszközöket, az alkalmazásvédelmi szabályzatok segítségével alkalmazásszinten biztosíthatja a vállalati adatok védelmét.
Van azonban néhány korlátozás, például:

- Nem telepíthet alkalmazásokat az eszközre. A végfelhasználónak az áruházból kell letölteniük az alkalmazásokat.
- Az ilyen eszközökön nem építhetők ki tanúsítványprofilok.
- Az eszközön nem használhatók a Wi-Fi- és VPN-beállítások.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Az alkalmazásvédelmi szabályzatokkal felügyelhető alkalmazások

Az Intune [SDK](../developer/app-sdk.md) -val integrált vagy az [Intune app burkoló eszköz](../developer/apps-prepare-mobile-application-management.md) által becsomagolt alkalmazások kezelhetők az Intune app Protection-szabályzatok használatával. Tekintse meg az ezen eszközök használatával létrehozott, [Microsoft Intune védett alkalmazások](apps-supported-intune-apps.md) hivatalos listáját, amelyek nyilvános használatra elérhetők.

Az Intune SDK Fejlesztői csapata aktívan teszteli és karbantartja a natív Android, iOS (obj-C, Swift), a Xamarin, a Xamarin. Forms és a Cordova platformmal létrehozott alkalmazásokat. Míg egyes ügyfelek sikerrel jártak az Intune SDK-val más platformokkal, például a natív és a NativeScript reagálva, a támogatott platformoktól eltérő módon nem biztosítunk explicit útmutatást vagy beépülő modult az alkalmazás-fejlesztőknek.

Az [INTUNE SDK](../developer/app-sdk.md) néhány fejlett modern hitelesítési funkciót használ a[Azure Active Directory Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) szolgáltatásban mind az 1. fél, mind az SDK harmadik féltől származó verzióihoz. Így a [Microsoft Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) nem működik megfelelően számos alapvető forgatókönyvvel, például a hitelesítéssel a Intune app Protection szolgáltatásban és a feltételes indításban. Mivel a Microsoft Identity csapatának általános útmutatója, hogy az összes Microsoft Office-alkalmazásra váltson a MSAL-re, az [INTUNE SDK](../developer/app-sdk.md) -nak végül támogatnia kell, de még nincsenek csomagok.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>A végfelhasználói követelmények az alkalmazás-védelmi házirendek használatához

Az alábbi lista a végfelhasználói követelményeket ismerteti az alkalmazás-védelmi szabályzatok Intune által felügyelt alkalmazásokban való használatához:

- A végfelhasználónak rendelkeznie kell egy Azure Active Directory- (AAD-) fiókkal. Az Intune-felhasználók Azure Active Directoryban történő létrehozásáról lásd: [Felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](../fundamentals/users-add.md).

- A végfelhasználónak rendelkeznie kell az Azure Active Directory-fiókjához rendelt Microsoft Intune-licenccel. További információ a végfelhasználókhoz rendelt Intune-licencekről: [Intune-licencek kezelése](../fundamentals/licenses-assign.md).

- A végfelhasználónak egy alkalmazásvédelmi szabályzattal társított biztonsági csoporthoz kell tartoznia. Ugyanezen alkalmazásvédelmi szabályzatnak a használt alkalmazással is társítva kell lennie. Alkalmazásvédelmi csoportokat az [Azure-portálon](https://portal.azure.com) található Intune-konzolban lehet létrehozni és telepíteni. A biztonsági csoportok létrehozása jelenleg a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com)lehetséges.

- A végfelhasználónak saját AAD-fiókjával be kell jelentkeznie az alkalmazásba.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Alkalmazás-védelmi szabályzatok Microsoft Office alkalmazásokhoz

Néhány további követelményt figyelembe kell vennie, ha Microsoft Office alkalmazásokkal rendelkező alkalmazás-védelmi szabályzatokat kíván használni.

### <a name="outlook-mobile-app"></a>Outlook Mobile alkalmazás
Az [Outlook Mobile alkalmazás](https://products.office.com/outlook) használatának további követelményei a következők:

- A végfelhasználónak telepítenie kell az Outlook mobilalkalmazást az eszközére.
- A végfelhasználónak [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) postaládával és az AAD-fiókjához kapcsolt licenccel kell rendelkeznie.

  >[!NOTE]
  > Az Outlook mobilalkalmazás az Intune App Protection szolgáltatást jelenleg csak a Microsoft Exchange Online és a [hibrid, modern hitelesítésű Exchange Server kiszolgálók](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) esetében támogatja, az Office 365 dedikált verzióban futó Exchange esetében nem.

### <a name="word-excel-and-powerpoint"></a>Word, Excel és PowerPoint
A [Word, Excel és PowerPoint](https://products.office.com/business/office) alkalmazások használatának további követelményei a következők:

- A végfelhasználónak rendelkeznie kell az Azure Active Directory-fiókjához rendelt [Office 365 Vállalati vagy Nagyvállalati verzió](https://products.office.com/business/compare-more-office-365-for-business-plans) licencével. Az előfizetésnek tartalmaznia kell a mobileszközökön használt Office-alkalmazásokat, és egy felhőalapú társzolgáltatás-fiókot is tartalmazhat a [OneDrive Vállalati verzióban](https://onedrive.live.com/about/business/). Az Office 365-licenceket a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com) lehet hozzárendelni, ezeket az [utasításokat](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)követve.

- A végfelhasználónak rendelkeznie kell egy felügyelt hellyel, amely a részletes Mentés másként funkció használatával van konfigurálva a "szervezet adatai másolatának mentése" alkalmazás-védelmi házirend-beállításban. Ha például a felügyelt hely a OneDrive, a [OneDrive](https://onedrive.live.com/about/) alkalmazást konfigurálni kell a felhasználó Word, Excel és PowerPoint alkalmazásában.

- Ha a felügyelt hely a OneDrive, a végfelhasználóra életbe léptetett alkalmazásvédelmi szabályzatnak társítva kell lennie a OneDrive alkalmazással.

  >[!NOTE]
  > Az Office-mobilalkalmazások jelenleg csak a SharePoint Online verziót támogatják, a helyszíni SharePoint rendszert nem.

### <a name="managed-location-needed-for-office"></a>Az Office-hoz szükséges felügyelt hely
Felügyelt hely (például OneDrive) szükséges az Office-hoz. Az Intune az alkalmazásban lévő összes olyan adattípust megjelöli, mint a "céges" vagy a "személyes". „Cégesnek” azok az adatok számítanak, amelyek vállalati forrásból származnak. Az Office-alkalmazásokat illetően az Intune a következőket tekinti vállalati forrásnak: e-mailek (Exchange) vagy felhőbeli tárhely (OneDrive alkalmazás Vállalati OneDrive-fiókkal).

### <a name="skype-for-business"></a>Skype Vállalati verzió
A Skype vállalati verziójának használatára további követelmények vonatkoznak. A licenckövetelményekért lásd: [Skype Vállalati verzió](https://products.office.com/skype-for-business/it-pros). A Skype Vállalati verzió (SfB) helyszíni és hibrid konfigurációival kapcsolatban lásd: [Az SfB és Exchange hibrid modern hitelesítése általánosan elérhető](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756), illetve [Modern hitelesítés az AAD-vel az SfB-hez](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910).

## <a name="app-protection-global-policy"></a>Alkalmazásvédelmi globális szabályzat

Ha a OneDrive rendszergazdája megkeresi a **admin.onedrive.com** , és kiválasztja az **eszközök hozzáférését**, beállíthatja a **mobileszköz-kezelési** vezérlőket a OneDrive és a SharePoint-ügyfélalkalmazások számára. 

A OneDrive felügyeleti konzolján elérhető beállításokkal konfigurálható a **Globális** szabályzat nevű speciális Intune alkalmazásvédelmi szabályzat. Ez a globális szabályzat a bérlőn belül az összes felhasználóra vonatkozik, és nincs lehetőség a szabályzat célzására. 

A szabályzat az engedélyezése után alapértelmezés szerint a választott beállításoknak megfelelően védi az iOS és Android rendszerre készült OneDrive és SharePoint alkalmazást. Az informatikai szakemberek az Intune-konzolon szerkeszthetik ezt a szabályzatot, ahol további célalkalmazásokat adhatnak hozzá, és bármely beállítását módosíthatják. 

Alapértelmezés szerint bérlőnként csak egy **Globális** szabályzat létezhet. Az [Intune Graph API-k](../developer/intune-graph-apis.md) használatával további globális szabályzatok is létrehozhatók bérlőnként, azonban ezt nem javasoljuk. A további globális szabályzatok létrehozása azért nem ajánlott, mert az ilyen szabályzatok megvalósításának hibaelhárítása igen bonyolult lehet.

A **Globális** szabályzat a bérlőn belül az összes felhasználóra vonatkozik, azonban ezeket a beállításokat bármely normál Intune alkalmazásvédelmi szabályzat felülbírálja.

## <a name="app-protection-features"></a>Alkalmazásvédelmi funkciók

### <a name="multi-identity"></a>Többszörös identitás

A többszörös identitás támogatása lehetővé teszi, hogy az alkalmazások több célközönséget támogassanak. Ezek a célközönségek a "vállalati" felhasználók és a "személyes" felhasználók is. A munkahelyi és iskolai fiókokat a "céges" célközönségek használják, míg a személyes fiókokat a fogyasztói célközönségek, például Microsoft Office felhasználók számára használják. A többszörös identitást támogató alkalmazások nyilvánosan is közzétehetők, ahol az alkalmazás csak akkor érvényes, ha az alkalmazást a munkahelyi és iskolai ("vállalati") környezetben használják. A többszörös identitás támogatása az [INTUNE SDK](../developer/app-sdk.md) -t használja, hogy csak az alkalmazásba bejelentkezett munkahelyi vagy iskolai fiókra alkalmazza az alkalmazás-védelmi szabályzatokat. Ha egy személyes fiók van bejelentkezve az alkalmazásba, az adatok érintetlenek maradnak.

A "személyes" kontextusra példaként vegye fontolóra azt a felhasználót, aki új dokumentumot indít el a Wordben, ez a személyes környezetnek minősül, így Intune App Protection szabályzatok nem lesznek alkalmazva. Ha a dokumentumot a "céges" OneDrive-fiókba menti, akkor a rendszer a "vállalati" kontextust fogja alkalmazni, és Intune App Protection szabályzatokat alkalmaz.

A munkahelyi és a "vállalati" környezetre például vegye fontolóra azt a felhasználót, aki a OneDrive alkalmazást indítja el a munkahelyi fiókjával. A felhasználó ebben a vállalati környezetben nem tudja áthelyezni a fájlokat a személyes tárolóhelyére. Ha később a személyes fiókjával használja a OneDrive-ot, akkor korlátozás nélkül másolhat és helyezhet át adatokat a személyes OneDrive-jából.

Az Outlook a "személyes" és a "vállalati" e-mailek együttes e-mail-nézetét tartalmazza. Ebben az esetben az Outlook alkalmazás az Intune PIN-kódját kéri az indításkor.

További információ a többszörös identitásról az Intune-ban: [MAM és multi-Identity](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>Intune-alkalmazás PIN-kódja

A személyes azonosítószám (PIN-kód) egy olyan kód, amellyel ellenőrizni lehet, hogy egy alkalmazásban a megfelelő felhasználó fér-e hozzá a céges adatokhoz.

**PIN-kód kérése**<br>
Az Intune kéri a felhasználó PIN-kódját az alkalmazáshoz, amikor a felhasználó „céges” adatokhoz kísérel meg hozzáférni. A többszörös identitású alkalmazásokban (például Word, Excel vagy PowerPoint) a rendszer a felhasználót a PIN-kód megadására kéri, amikor megpróbál megnyitni egy "céges" dokumentumot vagy fájlt. Az egyidentitású alkalmazások, például az [Intune app wrapper Tool](../developer/apps-prepare-mobile-application-management.md)használatával felügyelt üzletági alkalmazások esetén a PIN-kód megadását kéri a rendszer, mivel az [Intune SDK](../developer/app-sdk.md) tudja, hogy a felhasználó az alkalmazásban mindig a "céges" élményét használja.

**PIN-kód kérése vagy vállalati hitelesítő adatok kérése, gyakoriság**<br>
A rendszergazda megadhatja az Intune app Protection házirend-beállítást az Intune felügyeleti konzolján **(perc)** . Ez a beállítás határozza meg, hogy mennyi idő elteltével jelenjen meg a hozzáférési követelmények ellenőrzése az eszközön, és az alkalmazás PIN-kódjának képernyője vagy a vállalati hitelesítő adatok kérése megtörténjen. Ugyanakkor a PIN-kóddal kapcsolatos alábbi fontos információk is befolyásolják, hogy a rendszer milyen gyakran kér felhasználói bevitelt:

- **A PIN-kód azonos közzétevő alkalmazásai között van megosztva a használhatóság javítása érdekében:**<br> IOS rendszeren egyetlen alkalmazás-PIN-kód van megosztva **az azonos alkalmazás-közzétevőhöz**tartozó alkalmazások között. Az összes Microsoft-alkalmazás például ugyanazt a PIN-kódot használja. Androidon minden alkalmazás egyetlen közös alkalmazásszintű PIN-kódot használ.
- **Az eszköz újraindítása utáni *(perc) viselkedés utáni újraellenőrzési követelmények* :**<br> Az időzítő nyomon követi, hogy a rendszer hány perc inaktivitás után jelenítse meg az Intune-alkalmazás PIN-kódját, vagy a vállalati hitelesítő adatok megadását. IOS rendszeren az eszköz újraindítása nem érinti az időzítőt. Így az eszköz újraindítása nem befolyásolja azon percek számát, ameddig a felhasználó inaktív volt egy olyan iOS-alkalmazásból, amely az Intune PIN-kódját (vagy a vállalati hitelesítő adatokkal) megcélozta. Androidon az időzítő visszaáll az eszköz újraindítására. Ilyenkor az Intune PIN-kódját (vagy vállalati hitelesítő adatokkal) tartalmazó Android-alkalmazások valószínűleg rákérdeznek az alkalmazás PIN-kódjára vagy a vállalati hitelesítő adatokra, függetlenül attól, hogy az **eszköz újraindítása után**megtörtént-e a hozzáférési követelmények ismételt ellenőrzésének (perc) beállítása.  
- **A PIN-kóddal társított időzítő működés közbeni jellege:**<br> Miután megadta a PIN-kódot egy alkalmazás eléréséhez (A alkalmazáshoz), és az alkalmazás elhagyja az előtért (a fő bemeneti fókuszt) az eszközön, az időzítő a PIN-kód alaphelyzetbe állításával lesz visszaállítva. Egy olyan alkalmazás (B alkalmazás) sem fogja bekérni a PIN-kódot a felhasználótól, amely szintén ezt a PIN-kódot használja, mivel a számláló alaphelyzetbe állt. Az adatkérés akkor jelenik meg újra, amikor a rendszer ismét eléri a „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítás értékét.

iOS-eszközökön, ha a bemenet fő fókuszán kívüli alkalmazás ismét eléri **A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)** értéket, az adatkérés akkor is újra megjelenik, ha a PIN-kód különböző közzétevőktől származó alkalmazások között van megosztva. Így ha a felhasználó rendelkezik például egy _A_ alkalmazással az _X_ közzétevőtől, és egy _B_ alkalmazással az _Y_ közzétevőtől, akkor ez a két alkalmazás ugyanazon a PIN-kódon osztozik. A felhasználó fókuszában (előtér) az _A_ alkalmazás áll, a _B_ alkalmazás pedig kis méretűre van állítva. **A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)** érték elérése után a felhasználónak szüksége van PIN-kódra, hogy átváltson a _B_ alkalmazásra.

  >[!NOTE]
  > A felhasználó hozzáférési követelményeinek gyakoribb ellenőrzése (azaz a PIN-kód kérése) érdekében, különösen a gyakran használt alkalmazások esetében javasolt csökkenteni a „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítás értéket.

**Beépített alkalmazás-PIN-kód az Outlookhoz és a OneDrive**<br>
Az Intune-PIN-kód egy inaktivitáson alapuló időzítő alapján működik (a **hozzáférési követelmények ismételt ellenőrzési értéke (perc)** ). Az Intune PIN-kód kérései így az alkalmazások beépített PIN-kódjaitól (amelyek gyakran alapértelmezés szerint az alkalmazásindításhoz vannak kötve) függetlenül jelennek meg az Outlookban és a OneDrive-ban. Ha a felhasználó mindkét PIN-kód-kérelmet egyszerre kapja meg, várhatóan az Intune PIN-kódnak kell elsőbbséget élveznie.

**Intune PIN-kód biztonsága**<br>
A PIN-kód arra szolgál, hogy csak a megfelelő felhasználó férhessen hozzá az alkalmazásban a céges adatokhoz. Így az alkalmazás Intune-beli PIN-kódjának megváltoztatásához a végfelhasználónak be kell jelentkeznie a munkahelyi vagy iskolai fiókjával. Ezt a hitelesítést a Azure Active Directory a biztonságos jogkivonat-Exchange használatával kezeli, és nem átlátható az [INTUNE SDK](../developer/app-sdk.md)-val. A munkahelyi vagy iskolai adatok védelmére biztonsági szemszögből a titkosítás a legjobb módszer. A titkosítás nem függ össze az alkalmazás PIN-kódjával, csak annak saját alkalmazásvédelmi szabályzatával.

**A találgatásos támadásokkal és az Intune-PIN-kóddal szembeni védelem**<br>
Az alkalmazás PIN-szabályzatának részeként a rendszergazda beállíthatja, hogy legfeljebb hányszor adhatja meg a felhasználó a PIN-kódját, mielőtt a rendszer zárolná az alkalmazást. A kísérletek számának teljesülése után az [INTUNE SDK](../developer/app-sdk.md) törölheti az alkalmazás "vállalati" adatait.

**Intune-PIN-kód és szelektív törlés**<br>
IOS rendszeren az alkalmazás szintű PIN-kód adatait a kulcstartó tárolja, amely azonos közzétevővel, például az összes Microsoft-alkalmazással közösen van. A PIN-kód adatai egy végfelhasználói fiókhoz is kötődnek. Egy alkalmazás szelektív törlése nem érintheti a másik alkalmazást. 

Például egy, a bejelentkezett felhasználóhoz tartozó Outlookhoz beállított PIN-kód egy megosztott kulcstartóban tárolódik. Amikor a felhasználó bejelentkezik a OneDrive (amelyet a Microsoft is közzétett), ugyanazt a PIN-kódot fogja látni, mint az Outlook, mivel ugyanazt a megosztott kulcstartót használja. Ha kijelentkezik az Outlookból, vagy törli a felhasználói adatok az Outlookban, az Intune SDK nem törli a kulcstartót, mert a OneDrive továbbra is használhatja ezt a PIN-kódot. Emiatt a szelektív törlések nem törlik a megosztott kulcstartót, beleértve a PIN-kódot is. Ez a viselkedés akkor is ugyanaz marad, ha az eszközön már csak egy alkalmazás található. 

Mivel a PIN-kód ugyanazokkal a közzétevővel van megosztva az alkalmazások között, ha a törlés egyetlen alkalmazásba kerül, az Intune SDK nem tudja, hogy van-e más alkalmazás az eszközön ugyanazzal a közzétevővel. Így az Intune SDK nem törli a PIN-kódot, mivel az más alkalmazásokhoz is használható. A várt érték az, hogy az alkalmazás PIN-kódját törölni kell, ha az adott közzétevőtől származó legutóbbi alkalmazás el lesz távolítva egy bizonyos operációs rendszer tisztításának részeként.
 
Ha betartja a PIN-kódot néhány eszközön, a következők történnek: mivel a PIN-kód egy identitáshoz van kötve, ha a felhasználó egy másik fiókkal jelentkezett be a törlés után, a rendszer kérni fogja az új PIN-kód megadását. Ha azonban korábban már meglévő fiókkal jelentkezik be, a kulcstartóban tárolt PIN-kód már használható a bejelentkezéshez.

**Kétszer állítja be a PIN-kódot ugyanazon közzétevő alkalmazásaiban?**<br>
A MAM (iOS rendszeren) jelenleg lehetővé teszi, hogy az alkalmazás szintű PIN-kód alfanumerikus és speciális karaktereket használjon (úgynevezett PIN-kód), amelyhez alkalmazások (pl. WXP, Outlook, Managed Browser, Yammer) részvételére van szükség az [iOS-hez készült INTUNE SDK](../developer/app-sdk-ios.md)integrálásához. Az integráció hiányában a PIN-jelszóbeállítások nem lesznek megfelelően megkövetelve a megcélzott alkalmazásoknál. Ez a szolgáltatás az iOS-hez készült Intune SDK következő verziójában jelent meg: 7.1.12.

A szolgáltatás támogatása és az iOS-hez készült Intune SDK előző verzióival való kompatibilitás biztosítása érdekében a 7.1.12-es és újabb verziókban minden PIN-kód (akár numerikus, akár hitelesítő kód) az SDK korábbi verzióinak numerikus PIN-kódjaitól elkülönítve van kezelve. Így ha egy eszközön olyan alkalmazások találhatók, melyek az iOS-hez készült Intune SDK 7.1.12-esnél korábbi ÉS 7.1.12-esnél újabb verziójával rendelkeznek, és ugyanattól a gyártótól származnak, ezekhez két PIN-kódot kell beállítani. A két PIN-kód (az egyes alkalmazásokhoz) nem kapcsolódik semmilyen módon (azaz be kell tartania az alkalmazásra alkalmazott adatvédelmi szabályzatot). Így *csak* abban az esetben, ha az a és a B alkalmazáshoz ugyanazok a szabályzatok érvényesek (a PIN-kód tekintetében), a felhasználó kétszer is beállíthatja ugyanazt a PIN-kódot. 

Ez a viselkedés kizárólag az Intune mobilalkalmazás-felügyeleti funkciójával engedélyezett iOS-alkalmazások PIN-kódjaira jellemző. Ahogy az idő múlásával az alkalmazások az iOS-hez készült Intune SDK újabb verzióira térnek át, egyre kisebb problémát fog jelenteni, hogy kétszer kell beállítani a PIN-kódot az ugyanazon gyártótól származó alkalmazásokhoz. Erre az alábbi megjegyzésben találhat egy példát.

  >[!NOTE]
  > Ha például az A alkalmazás egy 7.1.12-esnél korábbi verzióval készült, a B alkalmazás pedig a 7.1.12-es vagy annál újabb verzióval készült, és a kettő ugyanazon gyártótól származik, a végfelhasználónak külön kell majd PIN-kódot beállítania az A-hoz és a B-hez, ha mindkettő egy iOS-es eszközre van telepítve.
  > Ha a 7.1.9 SDK-verziót tartalmazó C-alkalmazás telepítve van az eszközön, akkor ugyanazt a PIN-kódot fogja megosztani az A alkalmazással. A D-vel készített 7.1.14-alkalmazás ugyanazt a PIN-kódot fogja megosztani a B alkalmazásban.  
  > Ha egy eszközön csak az A és a C alkalmazás van telepítve, akkor egy PIN-kódot kell beállítani. Ugyanez arra az esetre is vonatkozik, ha egy eszközön csak a B és a D alkalmazás van telepítve.

### <a name="app-data-encryption"></a>Az alkalmazás adattitkosítása
A rendszergazdák olyan alkalmazásvédelmi szabályzatokat léptethetnek életbe, amelyek előírják az alkalmazásadatok titkosítását. A szabályzat részeként a rendszergazda azt is megadhatja, hogy mikor kell titkosítani a tartalmat.

**Hogyan működik az Intune-adattitkosítási folyamat**<br> Az alkalmazásvédelmi szabályzat titkosítási beállításáról részletes információt [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md) és az [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása](app-protection-policy-settings-ios.md) című cikkekben talál.

**Titkosított adatforgalom**<br>
Csak a rendszergazda alkalmazásvédelmi szabályzatának értelmében „cégesként” megjelölt adatok. „Cégesnek” azok az adatok számítanak, amelyek vállalati forrásból származnak. Az Office-alkalmazások esetében az Intune a következőket látja el üzleti helyként:

- E-mail (Exchange) 
- Felhőalapú tárolás (OneDrive-alkalmazás OneDrive for Business-fiókkal)

Az [Intune alkalmazás-burkoló eszköz](../developer/apps-prepare-mobile-application-management.md)által kezelt üzletági alkalmazások esetében az összes alkalmazásadatok a "céges" minősül.

### <a name="selective-wipe"></a>Szelektív törlés

**Adatok távoli törlése**<br>
Az Intune három különböző módon törölheti az alkalmazásadatok: 
- Teljes eszköz törlése
- Szelektív törlés a MDM 
- MAM szelektív törlés

Az MDM-beli távoli törlésről az [eszközök az összes adat törlésével vagy használatból való kivonással történő eltávolítását](../remote-actions/devices-wipe.md) ismertető témakörben találhat további információt. A MAM segítségével végrehajtott szelektív törlésről [A kivonás művelete](../remote-actions/devices-wipe.md#retire) és a [Csak a céges adatok törlése az alkalmazásokból](apps-selective-wipe.md) című témakörben tudhat meg többet.

Az eszköz [teljes törlése](../remote-actions/devices-wipe.md) eltávolítja az összes felhasználói adatát és beállítását **az** eszköz gyári beállításainak visszaállításával. Az eszközt a rendszer eltávolítja az Intune-ból.

  >[!NOTE]
  > Az eszköz teljes törlése és a szelektív törlés a MDM esetében csak az Intune mobileszköz-kezelési (MDM) szolgáltatásban regisztrált eszközökön érhető el.

**Szelektív törlés a MDM**<br>
A céges adatok eltávolításáról az [Eszközök eltávolítása – Kivonás](../remote-actions/devices-wipe.md#retire) című témakörben olvashat.

**Szelektív törlés MAM-hoz**<br>
A MAM szelektív törlés egyszerűen eltávolítja a vállalati alkalmazásadatokat egy alkalmazásból. A kérelem az Intune Azure-portál használatával küldhető be. A törlési kérelmek kezdeményezéséről a [Csak a céges adatok törlése az alkalmazásokból](apps-selective-wipe.md) című témakörben tájékozódhat.

Ha a felhasználó az alkalmazást szelektív törlés kezdeményezése során használja, az [INTUNE SDK](../developer/app-sdk.md) 30 percenként ellenőrzi, hogy az Intune MAM szolgáltatástól érkező szelektív törlési kérést végez-e. Akkor is ellenőrzi a szelektív törlést, amikor a felhasználó először indítja el az alkalmazást és lép be a munkahelyi vagy iskolai fiókjába.

**Ha a helyszíni (helyszíni) szolgáltatások nem működnek az Intune által védett alkalmazásokkal**<br>
Az Intune app Protection az alkalmazás és az [INTUNE SDK](../developer/app-sdk.md)közötti konzisztens felhasználó identitásának függvénye. Ez kizárólag modern hitelesítés révén garantálható. Előfordulnak olyan helyzetek, amelyekben az alkalmazások működnek a helyszíni konfigurációval, ám ezek a forgatókönyvek se nem konzisztensek, se nem garantáltak.

**Webhivatkozások megnyitása biztonságos módon a felügyelt alkalmazásokból**<br>
A rendszergazda életbe léptethet és beállíthat egy alkalmazásvédelmi szabályzatot az [Intune Managed Browser alkalmazáshoz](app-configuration-managed-browser.md), amely egy, a Microsoft Intune által fejlesztett, az Intune használatával egyszerűen felügyelhető webböngésző. A rendszergazda előírhatja, hogy az Intune által kezelt alkalmazásokban található összes webhivatkozást csak a Managed Browser alkalmazással lehessen megnyitni.

## <a name="app-protection-experience-for-ios-devices"></a>App Protection-élmény iOS-eszközökhöz

### <a name="device-fingerprint-or-face-ids"></a>Eszköz ujjlenyomata vagy arc-azonosítói 
Az Intune alkalmazásvédelmi szabályzatai csak az Intune licencelt felhasználójának teszik lehetővé az alkalmazás elérésének szabályozását. Az alkalmazáshoz való hozzáférés szabályozásának egyik módja az Apple Touch ID vagy a Face ID megkövetelése a támogatott eszközökön. Az Intune olyan viselkedést vezet be, ahol az eszköz biometrikus adatbázisának bármilyen változása esetén az Intune PIN-kódot kér a felhasználótól a következő inaktivitási időkorlát elérése esetén. A biometrikus adatok módosításai tartalmazzák az arc vagy ujjlenyomat hozzáadását és eltávolítását. Ha az Intune-felhasználóhoz nincs beállítva PIN-kód, a rendszer felszólítja az Intune PIN-kód beállítására.
 
Ennek a folyamatnak a célja, hogy az alkalmazás szintjén biztonságosan és védelemmel lássa el a szervezet adatait az alkalmazáson belül. Ez a funkció csak az iOS rendszerhez érhető el, és olyan alkalmazások részvételét igényli, amelyek integrálják az iOS-es, 9.0.1-es vagy újabb verziójú Intune SDK-t. Az SDK-integráció szükséges a viselkedés kényszeríthetőségéhez a megcélzott alkalmazásoknál. Ez az integráció fokozatosan történik, és az egyes alkalmazáscsapatoktól függ. Néhány alkalmazás, amely ezek között szerepelhet: WXP, Outlook, Managed Browser és Yammer.
  
### <a name="ios-share-extension"></a>iOS-megosztási bővítmény
Az iOS-megosztási bővítmény használatával megnyithatja a nem felügyelt alkalmazások munkahelyi vagy iskolai szolgáltatásait, még akkor is, ha az adatátviteli szabályzat **csak a felügyelt alkalmazásokra** van beállítva, vagy **nem rendelkezik alkalmazásokkal**. Az Intune alkalmazásvédelmi szabályzata nem tudja kezelni az iOS megosztási bővítményt az eszköz felügyelete nélkül. Ezért az _**Intune titkosítja a „céges” adatokat, mielőtt az alkalmazáson kívül megosztaná**_ . Ezt a titkosítási viselkedést a felügyelt alkalmazáson kívüli "céges" fájl megnyitására tett kísérlettel ellenőrizheti. A fájlnak titkosítottnak kell lennie, így a felügyelt alkalmazáson kívül mással nem nyitható meg.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Több Intune app Protection-hozzáférési beállítás ugyanazon alkalmazások és felhasználók számára
Az Intune app Protection-szabályzatok a hozzáféréshez meghatározott sorrendben lesznek alkalmazva a végfelhasználói eszközökön, amikor egy célzott alkalmazást próbálnak elérni a vállalati fiókból. A törlésnek általában elsőbbsége van, ezt követi a letiltás és a bezárható figyelmeztetés. Például az iOS-verzió frissítésére figyelmeztető minimálisan előírt iOS operációsrendszer-beállítás, ha érvényesíthető az adott felhasználóra/alkalmazásra, csak akkor kerül alkalmazásra, ha már életbe lépett a felhasználó hozzáférését letiltó minimálisan előírt iOS operációsrendszer-beállítás. Így tehát ha az informatikai rendszergazda a minimális iOS operációs rendszert 11.0.0.0-ra, a (csak figyelmeztetési) minimális iOS operációs rendszert 11.1.0.0-ra állította be, az alkalmazás elérését megkísérlő eszköz pedig az iOS 10-et használja, a végfelhasználó a minimális iOS operációsrendszer-verzióra vonatkozó szigorúbb beállítás alapján le lesz tiltva, és nem férhet hozzá az alkalmazáshoz.

A különböző típusú beállításokkal kapcsolatban az Intune SDK-verzióra vonatkozó követelmény elsőbbséget élvez, majd az alkalmazás verziójának követelményét, majd az iOS operációsrendszer-verzió követelményét. Ezt követi a beállításokra vonatkozó figyelmeztetések végrehajtása ugyanebben a sorrendben. Javasoljuk, hogy az Intune SDK-verziójának követelményét csak az Intune-termék csapata által az alapvető blokkolási forgatókönyvekre vonatkozó útmutatás alapján konfigurálja.

## <a name="app-protection-experience-for-android-devices"></a>Alkalmazás-védelmi élmény Android-eszközökhöz

### <a name="company-portal-app-and-intune-app-protection"></a>Az alkalmazás és az Intune app Protection Céges portál
A legtöbb alkalmazásvédelmi funkció be van építve a Munkahelyi portál alkalmazásba. Annak ellenére, hogy a Munkahelyi portál alkalmazás mindig szükséges, eszközregisztrációra _nincs szükség_. A regisztráció nélküli mobileszköz-felügyelethez (MAM-WE) a végfelhasználónak csak az eszközön kell telepítenie az Céges portál alkalmazást.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Több Intune app Protection-hozzáférési beállítás ugyanazon alkalmazások és felhasználók számára
Az Intune app Protection-szabályzatok a hozzáféréshez meghatározott sorrendben lesznek alkalmazva a végfelhasználói eszközökön, amikor egy célzott alkalmazást próbálnak elérni a vállalati fiókból. A letiltásnak általában elsőbbsége van a bezárható figyelmeztetéssel szemben. Például egy javítási frissítésre figyelmeztető minimálisan előírt androidos biztonsági javítás, ha érvényesíthető az adott felhasználóra/alkalmazásra, csak akkor kerül alkalmazásra, ha már életbe lépett a felhasználó hozzáférését letiltó minimálisan előírt androidos biztonsági javítás. Így tehát ha az informatikai rendszergazda a minimálisan előírt androidos biztonsági javítást 2018. március 1-re, és a (csak figyelmeztetési) minimálisan előírt androidos biztonsági javítást 2018. február 1-re állította be, az alkalmazás elérését megkísérlő eszköz pedig a 2018. január 1-i biztonsági javítást használja, a végfelhasználó a szigorúbb minimálisan előírt androidos biztonsági javítás alapján le lesz tiltva, és nem férhet hozzá az alkalmazáshoz. 

Különböző beállítások esetén először a az alkalmazás verziókövetelménye, majd az androidos operációs rendszer verziókövetelménye és végül az androidos biztonsági javítási verzió követelménye kerül sorra. Ezt követi a beállításokra vonatkozó figyelmeztetések végrehajtása ugyanebben a sorrendben.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Intune app Protection-szabályzatok és a Google biztonság igazolása Android-eszközökhöz 
Az Intune app Protection-szabályzatok lehetővé teszik a rendszergazdák számára, hogy végfelhasználói eszközöket adjanak át a Google biztonság-igazolásának az Android-eszközökhöz. A Google Play szolgáltatás új meghatározása az Intune szolgáltatás által meghatározott időközönként jelentést küld a rendszergazdának. A szolgáltatás hívásának gyakorisága a terhelés miatt szabályozva van, ezért ez az érték belsőleg marad, és nem konfigurálható. A Google biztonság igazolási beállításához a rendszergazda által konfigurált rendszergazdai műveletek a feltételes indításkor az Intune szolgáltatás utolsó jelentett eredményei alapján lesznek elvégezve. Ha nincs adat, a hozzáférés más feltételes indítási ellenőrzéstől függően nem lehetséges, és a Google Play szolgáltatás "oda" helyezése az igazolási eredmények meghatározásához a háttérbe kerül, és aszinkron módon kéri a felhasználót, ha az eszköz meghibásodik. Elavult adatmennyiség esetén a rendszer letiltja vagy engedélyezi a hozzáférést az utolsó jelentett eredménytől függően, és Hasonlóképpen az igazolási eredmények meghatározásához a Google Play szolgáltatás "oda" helyezése is megkezdődik, és aszinkron módon kéri a felhasználót, ha az eszköz sikertelen volt.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Intune app Protection-szabályzatok és a Google alkalmazások ellenőrzése API Android-eszközökhöz
A Intune App Protection házirendek lehetővé teszik a rendszergazdák számára, hogy a végfelhasználói eszközökön jeleket küldjenek az Android-eszközökön a Google ellenőrzése alkalmazások API-n keresztül. Az ehhez szükséges útmutatást az eszköz kissé eltérőnek kell lennie. Az általános folyamat magában foglalja a Google Play Áruház, majd a **saját alkalmazások & játékok**elemre kattint, és az utolsó alkalmazás vizsgálatának eredményére kattint, amely a lejátszás elleni védelem menübe kerül. Ellenőrizze, hogy be van-e kapcsolva a **biztonsági fenyegetések keresése az eszközön** .

### <a name="googles-safetynet-attestation-api"></a>Google biztonság igazolási API 
Az Intune kihasználja a Google Play Protect biztonság API-kat a nem regisztrált eszközökhöz való meglévő gyökérszintű észlelési ellenőrzésekhez való hozzáadáshoz. A Google fejleszti és karbantartja ezt az API-készletet az Android-alkalmazások számára, ha nem szeretné, hogy az alkalmazások feltört eszközökön fussanak. Az Android Pay-alkalmazás beépítette ezt, például:. Noha a Google nem osztja meg nyilvánosan a legfelső szintű észlelési ellenőrzéseket, az API-k elvárják, hogy észlelje az eszközeit feltört felhasználókat. Ezek a felhasználók ezt követően le lehet tiltani a hozzáférését, vagy a vállalati fiókjaikat a szabályzattal kompatibilis alkalmazásokból törölve. Az **alapvető integritás ellenőrzése** az eszköz általános integritását mutatja be. A feltört eszközök, emulátorok, virtuális eszközök és eszközök, amelyekkel a rendszer nem módosítja az alapszintű integritást. Győződjön meg arról, hogy az **alapszintű integritás & a hitelesített eszközök** közlik az eszköz kompatibilitását a Google szolgáltatásaival. Csak a Google által hitelesített, nem módosított eszközök adhatják át ezt az ellenőrzést. A meghiúsuló eszközök közé tartoznak a következők:

- Alapvető integritást nem teljesítő eszközök
- Zárolt rendszertöltő eszközzel rendelkező eszközök
- Egyéni rendszerkép/ROM-lemezzel rendelkező eszközök
- Eszközök, amelyekhez a gyártó nem kérelmezte a Google minősítést
- Közvetlenül az Android nyílt forráskódú program forrásfájljait tartalmazó rendszerképpel rendelkező eszközök
- A Beta/Developer Preview rendszerképpel rendelkező eszközök

A technikai részletekért tekintse meg [a Google dokumentációját a biztonság igazolásával](https://developer.android.com/training/safetynet/attestation) kapcsolatban.

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>A biztonság-eszköz igazolási beállítása és a "feltört eszközök" beállítása
A Google Play Protect biztonság API-ellenőrzései megkövetelik, hogy a végfelhasználó online állapotba kerüljön, amely az igazolási eredmények meghatározásához szükséges idő időtartamára vonatkozik. Ha a végfelhasználó offline állapotban van, a rendszergazda továbbra is számíthat arra, hogy kikényszeríthető legyen a feltört/feltört **eszközök** beállításától. Ennek ellenére, ha a végfelhasználó offline állapotban van, az **Offline türelmi időszak** értéke lejátszásra kerül, és a munkahelyi vagy iskolai adataihoz való összes hozzáférés le lesz tiltva az időzítő értékének elérésekor, amíg a hálózati hozzáférés elérhetővé nem válik. Mindkét beállítás bekapcsolása lehetővé teszi, hogy egy rétegzett megközelítés legyen a végfelhasználói eszközökön, ami akkor fontos, ha a végfelhasználók a mobilon férnek hozzá munkahelyi vagy iskolai információhoz.

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play Protect API-k és Google Play-szolgáltatások
A Google Play Protect API-kat használó app Protection-házirend beállításai megkövetelik a Google Play-szolgáltatások működését. A **Biztonság-eszköz igazolása**és a **veszélyforrások vizsgálata az alkalmazások** beállításainál a Google Play-szolgáltatások meghatározott verziójának megfelelő működéséhez szükséges. Mivel ezek olyan beállítások, amelyek a biztonság területéhez tartoznak, a végfelhasználó le lesz tiltva, ha ezeket a beállításokat megcélozták, és nem felelnek meg a Google Play-szolgáltatások megfelelő verziójának, vagy nincs hozzáférésük a Google Play-szolgáltatásokhoz.

## <a name="next-steps"></a>További lépések

[Alkalmazásvédelmi szabályzatok létrehozása és telepítése Microsoft Intune-ban](app-protection-policies.md)

[Az Android-alkalmazások elérhető védelmi házirendjének beállításai a Microsoft Intune](app-protection-policy-settings-android.md)

[IOS-alkalmazásokhoz elérhető védelmi házirend-beállítások Microsoft Intune](app-protection-policy-settings-ios.md)

## <a name="see-also"></a>További információ
A harmadik féltől származó alkalmazások, például a Salesforce mobilalkalmazás, speciális módon működnek együtt az Intune-nal a vállalati adatok védelme érdekében. Ha szeretne többet megtudni arról, hogy a Salesforce alkalmazás konkrétan hogyan működik együtt az Intune-nal (az MDM alkalmazáskonfigurációs beállításait is beleértve), olvassa el [A Salesforce alkalmazás és a Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) című témakört.
