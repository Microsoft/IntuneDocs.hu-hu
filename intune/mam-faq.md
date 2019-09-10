---
title: Gyakori kérdések az MAM-ről és az alkalmazásvédelemről
description: Ez a cikk az Intune mobilalkalmazás-kezeléssel (MAM) és az Intune alkalmazásvédelemmel kapcsolatos gyakori kérdésekre adott válaszokat ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28a7838e174d84dd15592c9e4f6d3e40bc679a90
ms.sourcegitcommit: a25cd79a33feb536d9b2fc11aa7d3e3972f1ca5a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/09/2019
ms.locfileid: "70842107"
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Gyakori kérdések az MAM-ről és az alkalmazásvédelemről

Ez a cikk az Intune mobilalkalmazás-kezeléssel (MAM) és az Intune alkalmazásvédelemmel kapcsolatos gyakori kérdésekre adott válaszokat ismerteti.

## <a name="mam-basics"></a>Az MAM alapjai

**Mi az MAM?**<br></br>
Az [Intune mobilalkalmazás-kezelés](/intune/app-lifecycle) olyan Intune-beli felügyeleti összetevők csoportja, amelyek lehetővé teszik mobilalkalmazások közzétételét és leküldését a felhasználók részére, valamint azok konfigurálását, védelmét, figyelését és frissítését.

**Milyen előnyöket kínál az MAM-alkalmazásvédelem?**<br></br>
Az MAM védi munkahelye adatait az alkalmazáson belül. A regisztráció nélküli MAM (MAM-WE) segítségével a bizalmas adatokat tartalmazó munkahelyi vagy iskolai alkalmazások szinte bármilyen eszközön felügyelhetők, beleértve a személyes tulajdonú eszközöket is saját eszközök használata (BYOD) esetén. Több irodai alkalmazás is felügyelhető az Intune MAM-mel, például a Microsoft Office-alkalmazások. Lásd a nyilvánosan elérhető, [Intune által kezelt alkalmazások](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) hivatalos listáját.

**Milyen eszközkonfigurációkat támogat az MAM?**<br></br>
Az Intune MAM két konfigurációt támogat:
- **INTUNE Mdm + MAM**: A rendszergazda csak az Intune mobileszköz-kezelésben (MDM) regisztrált eszközökön felügyelheti az MAM- és alkalmazásvédelmi szabályzatokat használó alkalmazásokat. Az MDM-et és MAM-ot használó alkalmazások felügyeletéhez a https://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt.

- **MAM eszközök regisztrációja nélkül**: A MAM eszközök regisztrációja nélkül, vagy MAM-WE lehetővé teszi a rendszergazdák számára, hogy az Intune MDM-ban nem regisztrált eszközökön a MAM-és az alkalmazás-védelmi szabályzatokat használják az alkalmazások felügyeletére. Ez azt jelenti, hogy az Intune csak külső EMM-szolgáltatóknál regisztrált eszközökön felügyelheti az alkalmazásokat. Az MAM-WE-t használó alkalmazások felügyeletéhez a https://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt. Emellett az Intune-nal felügyelheti az alkalmazásokat olyan eszközökön, amelyek harmadik féltől származó nagyvállalati mobilitási felügyeleti (EMM) rendszerben vannak regisztrálva, illetve nincsenek regisztrálva egyetlen mobileszköz-kezelési rendszerben sem.


## <a name="app-protection-policies"></a>Alkalmazásvédelmi szabályzatok

**Mik azok az alkalmazásvédelmi szabályzatok?**<br></br>
Az alkalmazásvédelmi szabályzatok olyan szabályok, amelyek biztosítják, hogy a céges adatok biztonságban maradnak, és nem kerülnek ki a felügyelt alkalmazásokból. A szabályzat egyfelől lehet olyan szabály, amely olyankor lép életbe, amikor a felhasználó megpróbál hozzáférni „céges” adatokhoz vagy áthelyezni azokat, másfelől azon műveletek csoportja, amelyeket a rendszer tilt vagy figyel, amikor az felhasználó az alkalmazást használja.

**Milyen példák vannak az alkalmazásvédelmi szabályzatok használatára?**<br></br>
Az alkalmazásvédelmi szabályzat egyes beállításairól részletes információt [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban ](app-protection-policy-settings-android.md) és az [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása ](app-protection-policy-settings-ios.md) című cikkekben talál.

**Lehet-e egyszerre a MDM és a MAM-szabályzatokat ugyanarra a felhasználóra alkalmazni, különböző eszközökre? Ha például egy felhasználó hozzáférhet a munkahelyi erőforrásokhoz a saját MAM-kompatibilis gépről, de a munka és az Intune MDM által felügyelt eszköz is használható. Vannak kikötések erre az ötletre?**<br></br>
Ha a MAM-szabályzatot az eszköz állapotának beállítása nélkül alkalmazza a felhasználóra, a felhasználó megkapja a MAM-szabályzatot a BYOD-eszközön és az Intune által felügyelt eszközön is. Egy MAM-szabályzatot a felügyelt állapot alapján is alkalmazhat. Tehát amikor létrehoz egy alkalmazás-védelmi házirendet, a cél elem mellett minden alkalmazás típusa beállításnál válassza a nem lehetőséget. Ezután tegye a következők valamelyikét:
- Alkalmazzon kevésbé szigorú MAM-szabályzatot az Intune által felügyelt eszközökre, és alkalmazzon egy szigorúbb MAM-szabályzatot a nem MDM regisztrált eszközökre.
- MAM-szabályzat alkalmazása csak a nem regisztrált eszközökre.

További információ: [az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Az alkalmazásvédelmi szabályzatokkal felügyelhető alkalmazások

**Mely alkalmazásokat lehet alkalmazásvédelmi szabályzatokkal felügyelni?**<br></br>
Az [Intune App SDK](/intune/app-sdk) által integrált vagy az [Intune alkalmazásburkoló eszköz](/intune/apps-prepare-mobile-application-management) által beburkolt, Intune alkalmazásvédelmi szabályzatokat használó alkalmazásokat. Lásd a nyilvánosan elérhető, [Intune által kezelt alkalmazások](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) hivatalos listáját.

**Mik az alkalmazásvédelmi szabályzatok Intune által kezelt alkalmazáson való használatának alapkövetelményei?**

- A végfelhasználónak rendelkeznie kell egy Azure Active Directory- (AAD-) fiókkal. Az Intune-felhasználók Azure Active Directoryban történő létrehozásáról lásd: [Felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](/intune/users-permissions-add).

- A végfelhasználónak rendelkeznie kell az Azure Active Directory-fiókjához rendelt Microsoft Intune-licenccel. További információ a végfelhasználókhoz rendelt Intune-licencekről: [Intune-licencek kezelése](/intune/licenses-assign).

- A végfelhasználónak egy alkalmazásvédelmi szabályzattal társított biztonsági csoporthoz kell tartoznia. Ugyanezen alkalmazásvédelmi szabályzatnak a használt alkalmazással is társítva kell lennie. Alkalmazásvédelmi csoportokat az [Azure-portálon](https://portal.azure.com) található Intune-konzolban lehet létrehozni és telepíteni. A biztonsági csoportok létrehozása jelenleg a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com)lehetséges.

- A végfelhasználónak saját AAD-fiókjával be kell jelentkeznie az alkalmazásba.

**Mi a teendő, ha egy alkalmazást szeretnék engedélyezni Intune App Protection de nem támogatott alkalmazás-fejlesztési platformot használ?** 

Az Intune SDK Fejlesztői csapata aktívan teszteli és karbantartja a natív Android, iOS (obj-C, Swift), a Xamarin, a Xamarin. Forms és a Cordova platformmal létrehozott alkalmazásokat. Míg egyes ügyfelek sikerrel jártak az Intune SDK-val más platformokkal, például a natív és a NativeScript reagálva, a támogatott platformoktól eltérő módon nem biztosítunk explicit útmutatást vagy beépülő modult az alkalmazás-fejlesztőknek.

**Az Intune APP SDK támogatja a Microsoft Authentication Libraryt (MSAL), vagy a közösségi fiókokat?**<br></br>
Az Intune APP SDK fejlett ADAL-funkciókat használ az SDK saját és külső verzióihoz is. Az MSAL így nem működik jól együtt számos alapvető forgatókönyvvel, például az Intune App Protection szolgáltatásban való hitelesítéssel és a feltételes indítással. Mivel a Microsoft Identity csapatának általános útmutatója, hogy az összes Microsoft Office-alkalmazásra váltson a MSAL-re, az Intune SDK-nak végül támogatnia kell, de még nincsenek csomagok.

**Mik az [Outlook mobilalkalmazás](https://products.office.com/outlook) használatának további feltételei?**

- A végfelhasználónak telepítenie kell az Outlook mobilalkalmazást az eszközére.

- A végfelhasználónak [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) postaládával és az AAD-fiókjához kapcsolt licenccel kell rendelkeznie.

  >[!NOTE]
  > Az Outlook mobilalkalmazás az Intune App Protection szolgáltatást jelenleg csak a Microsoft Exchange Online és a [hibrid, modern hitelesítésű Exchange Server kiszolgálók](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) esetében támogatja, az Office 365 dedikált verzióban futó Exchange esetében nem.

**Mik a [Word, az Excel és a PowerPoint](https://products.office.com/business/office) alkalmazás használatának további feltételei?**

- A végfelhasználónak rendelkeznie kell az Azure Active Directory-fiókjához rendelt [Office 365 Vállalati vagy Nagyvállalati verzió](https://products.office.com/business/compare-more-office-365-for-business-plans) licencével. Az előfizetésnek tartalmaznia kell a mobileszközökön használt Office-alkalmazásokat, és egy felhőalapú társzolgáltatás-fiókot is tartalmazhat a [OneDrive Vállalati verzióban](https://onedrive.live.com/about/business/). Az Office 365-licenceket a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com) lehet hozzárendelni, ezeket az [utasításokat](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)követve.

- A végfelhasználónak egy olyan felügyelt hellyel kell rendelkeznie, amelyet a részletes mentés másként funkcióval konfiguráltak „A Mentés másként művelet letiltása” alkalmazásvédelmi szabályzatbeállítás alatt. Ha például a felügyelt hely a OneDrive, a [OneDrive](https://onedrive.live.com/about/) alkalmazást konfigurálni kell a felhasználó Word, Excel és PowerPoint alkalmazásában.

- Ha a felügyelt hely a OneDrive, a végfelhasználóra életbe léptetett alkalmazásvédelmi szabályzatnak társítva kell lennie a OneDrive alkalmazással.

  >[!NOTE]
  > Az Office-mobilalkalmazások jelenleg csak a SharePoint Online verziót támogatják, a helyszíni SharePoint rendszert nem.

**Miért szükséges felügyelt hely (például a OneDrive) az Office-hoz?**<br></br>
Az Intune az alkalmazásban található összes adatot „cégesként” vagy „személyesként” jelöli meg. „Cégesnek” azok az adatok számítanak, amelyek vállalati forrásból származnak. Az Office-alkalmazásokat illetően az Intune a következőket tekinti vállalati forrásnak: e-mailek (Exchange) vagy felhőbeli tárhely (OneDrive alkalmazás Vállalati OneDrive-fiókkal).

**Mik a Skype Vállalati verzió használatának további feltételei?**<br></br>
A licenckövetelményekért lásd: [Skype Vállalati verzió](https://products.office.com/skype-for-business/it-pros). A Skype Vállalati verzió (SfB) helyszíni és hibrid konfigurációival kapcsolatban lásd: [Az SfB és Exchange hibrid modern hitelesítése általánosan elérhető](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756), illetve [Modern hitelesítés az AAD-vel az SfB-hez](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910).

## <a name="app-protection-features"></a>Alkalmazásvédelmi funkciók

**Mit jelent a többszörös identitás támogatása?**<br></br>
A többszörösidentitás-támogatás az Intune App SDK-nak azt a képességét jelenti, hogy csak az alkalmazásba bejelentkezett munkahelyi vagy iskolai fiókra alkalmazza az alkalmazásvédelmi szabályzatokat. Ha egy személyes fiók van bejelentkezve az alkalmazásba, az adatok érintetlenek maradnak.

**Mi a többszörösidentitás-támogatás célja?**<br></br>
A többszörösidentitás-támogatással a „céges” és fogyasztói célközönséggel egyaránt rendelkező alkalmazások (például az Office-alkalmazások) nyilvánossá tételekor a „céges” fiókokhoz beállítható az Intune alkalmazásvédelmi funkciója.

**Mi helyzet az Outlook többszörös identitással való használata esetén?**<br></br>
Mivel az Outlook a személyes és a „céges” e-mailek kombinált nézetét kínálja, az Outlook alkalmazás már az indításkor kéri az Intune PIN-kódját.

**Mire szolgál az Intune az alkalmazáshoz tartozó PIN-kódja?**<br></br>
A személyes azonosítószám (PIN-kód) egy olyan kód, amellyel ellenőrizni lehet, hogy egy alkalmazásban a megfelelő felhasználó fér-e hozzá a céges adatokhoz.

- **Mikor kell a felhasználónak megadni a PIN-kódját?**<br></br> Az Intune kéri a felhasználó PIN-kódját az alkalmazáshoz, amikor a felhasználó „céges” adatokhoz kísérel meg hozzáférni. A többszörös identitást használó alkalmazások, például a Word/Excel/PowerPoint esetében a felhasználónak akkor kell megadnia a PIN-kódját, mikor „céges” dokumentumot vagy fájlt próbál megnyitni. Az egyszeres identitást kezelő alkalmazások, például az Intune-os alkalmazásburkoló eszköz használatával előkészített üzletági alkalmazások már indításkor kérik a PIN-kódot, ugyanis az Intune App SDK tudja, hogy a felhasználó tevékenysége az alkalmazásban mindig „céges”.

- **Milyen gyakran kell a felhasználónak megadnia az Intune PIN-kódját?**<br></br> A rendszergazda az Intune felügyeleti konzolján beállíthatja az Intune alkalmazásvédelmi szabályzatának „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítását. Ez a beállítás azt határozza meg, hogy mennyi idő után ellenőrzi a rendszer a hozzáférési követelményeket az eszközön, és jelenik meg újból az alkalmazás PIN-kódot bekérő képernyője. Ugyanakkor a PIN-kóddal kapcsolatos alábbi fontos információk is befolyásolják, hogy a rendszer milyen gyakran kér felhasználói bevitelt: 

  - **A PIN-kód azonos közzétevő alkalmazásai között van megosztva a használhatóság javítása érdekében:** IOS rendszeren egyetlen alkalmazás-PIN-kód van megosztva **az azonos alkalmazás-közzétevőhöz**tartozó alkalmazások között. Androidon minden alkalmazás egyetlen közös alkalmazásszintű PIN-kódot használ.
  - **Az eszköz újraindítása után a "hozzáférési követelmények újravizsgálása ennyi idő után (perc)" viselkedés után:** A "PIN-kód időzítő" érték azt jelzi, hogy hány perc inaktivitás után kell megállapítani, hogy mikor jelenjen meg az Intune-alkalmazás PIN-kódja. iOS rendszeren a PIN-kód-számlálót nem érinti az eszköz-újraindítás. Az eszközök újraindítása így nincs hatással arra, hogy a felhasználó hány percig inaktív egy Intune-os PIN-kód-szabályzattal ellátott iOS-alkalmazásban. Android rendszeren a PIN-kód-számláló újraindul az eszköz újraindításakor. Ennek köszönhetően az Intune-os PIN-kód-szabályzattal ellátott Android-alkalmazások **az eszköz újra indítása után** valószínűleg kérni fogják az alkalmazás PIN-kódját „A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)” beállítás értékének függetlenül.  
  - **A PIN-kóddal társított időzítő működés közbeni jellege:** Miután megadta a PIN-kódot egy alkalmazás eléréséhez (A alkalmazáshoz), és az alkalmazás elhagyja az előtért (a fő bemeneti fókuszt) az eszközön, a PIN-kód időzítője visszaáll az adott PIN-kódra. Egy olyan alkalmazás (B alkalmazás) sem fogja bekérni a PIN-kódot a felhasználótól, amely szintén ezt a PIN-kódot használja, mivel a számláló alaphelyzetbe állt. Az adatkérés akkor jelenik meg újra, amikor a rendszer ismét eléri a „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítás értékét.

iOS-eszközökön, ha a bemenet fő fókuszán kívüli alkalmazás ismét eléri **A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)** értéket, az adatkérés akkor is újra megjelenik, ha a PIN-kód különböző közzétevőktől származó alkalmazások között van megosztva. Így ha a felhasználó rendelkezik például egy _A_ alkalmazással az _X_ közzétevőtől, és egy _B_ alkalmazással az _Y_ közzétevőtől, akkor ez a két alkalmazás ugyanazon a PIN-kódon osztozik. A felhasználó fókuszában (előtér) az _A_ alkalmazás áll, a _B_ alkalmazás pedig kis méretűre van állítva. **A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)** érték elérése után a felhasználónak szüksége van PIN-kódra, hogy átváltson a _B_ alkalmazásra.

  >[!NOTE] 
  > A felhasználó hozzáférési követelményeinek gyakoribb ellenőrzése (azaz a PIN-kód kérése) érdekében, különösen a gyakran használt alkalmazások esetében javasolt csökkenteni a „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítás értéket. 
      
- **Hogyan működik az Intune PIN-kód az Outlook és a OneDrive beépített PIN-kódjaival?**<br></br>
Az Intune PIN-kód egy inaktivitásalapú számláló alapján (azaz „A hozzáférési követelmények ismételt ellenőrzése ennyi idő után (perc)” értéke alapján) működik. Az Intune PIN-kód kérései így az alkalmazások beépített PIN-kódjaitól (amelyek gyakran alapértelmezés szerint az alkalmazásindításhoz vannak kötve) függetlenül jelennek meg az Outlookban és a OneDrive-ban. Ha a felhasználó mindkét PIN-kód-kérelmet egyszerre kapja meg, várhatóan az Intune PIN-kódnak kell elsőbbséget élveznie. 

- **Biztonságos-e a PIN-kód?**<br></br> A PIN-kód arra szolgál, hogy csak a megfelelő felhasználó férhessen hozzá az alkalmazásban a céges adatokhoz. Így az alkalmazás Intune-beli PIN-kódjának megváltoztatásához a végfelhasználónak be kell jelentkeznie a munkahelyi vagy iskolai fiókjával. Ezt a hitelesítést az Azure Active Directory biztonságos jogkivonatcsere révén kezeli, ami nem transzparens az Intune App SDK számára. A munkahelyi vagy iskolai adatok védelmére biztonsági szemszögből a titkosítás a legjobb módszer. A titkosítás nem függ össze az alkalmazás PIN-kódjával, csak annak saját alkalmazásvédelmi szabályzatával.

- **Hogyan védi a PIN-kódot az Intune a találgatásos támadásoktól?**<br></br> Az alkalmazás PIN-szabályzatának részeként a rendszergazda beállíthatja, hogy legfeljebb hányszor adhatja meg a felhasználó a PIN-kódját, mielőtt a rendszer zárolná az alkalmazást. Bizonyos számú kísérlet után az Intune App SDK törölheti az összes „céges” adatot az alkalmazásban.
  
- **Miért kell kétszer beállítanom a PIN-kódot az ugyanattól a gyártótól származó alkalmazások esetében?**<br></br> A MAM (az iOS esetében) jelenleg az alfanumerikus, valamint speciális karaktereket is tartalmazó alkalmazásszintű PIN-kódok (ún. hitelesítő kódok) használatát teszi lehetővé, amihez szükséges, hogy az alkalmazások (például a WXP, az Outlook, a Managed Browser és a Yammer) integrálják az iOS-es Intune APP SDK-t. Az integráció hiányában a PIN-jelszóbeállítások nem lesznek megfelelően megkövetelve a megcélzott alkalmazásoknál. Ez a szolgáltatás az iOS-hez készült Intune SDK következő verziójában jelent meg: 7.1.12. <br><br> A szolgáltatás támogatása és az iOS-hez készült Intune SDK előző verzióival való kompatibilitás biztosítása érdekében a 7.1.12-es és újabb verziókban minden PIN-kód (akár numerikus, akár hitelesítő kód) az SDK korábbi verzióinak numerikus PIN-kódjaitól elkülönítve van kezelve. Így ha egy eszközön olyan alkalmazások találhatók, melyek az iOS-hez készült Intune SDK 7.1.12-esnél korábbi ÉS 7.1.12-esnél újabb verziójával rendelkeznek, és ugyanattól a gyártótól származnak, ezekhez két PIN-kódot kell beállítani. <br><br> Ugyanakkor a két PIN-kód között (melyek az egyes alkalmazásokhoz tartoznak) semmilyen kapcsolat nincs, azaz meg kell felelniük az alkalmazásra vonatkozó alkalmazásvédelmi szabályzatnak. Ennek megfelelően a felhasználó *csak* akkor állíthatja be kétszer ugyanazt a PIN-kódot, ha az A és a B alkalmazásra ugyanazok a szabályzatok érvényesek (a PIN-kódokra vonatkozóan). <br><br> Ez a viselkedés kizárólag az Intune mobilalkalmazás-felügyeleti funkciójával engedélyezett iOS-alkalmazások PIN-kódjaira jellemző. Ahogy az idő múlásával az alkalmazások az iOS-hez készült Intune SDK újabb verzióira térnek át, egyre kisebb problémát fog jelenteni, hogy kétszer kell beállítani a PIN-kódot az ugyanazon gyártótól származó alkalmazásokhoz. Erre az alábbi megjegyzésben találhat egy példát.

  >[!NOTE]
  > Ha például az A alkalmazás egy 7.1.12-esnél korábbi verzióval készült, a B alkalmazás pedig a 7.1.12-es vagy annál újabb verzióval készült, és a kettő ugyanazon gyártótól származik, a végfelhasználónak külön kell majd PIN-kódot beállítania az A-hoz és a B-hez, ha mindkettő egy iOS-es eszközre van telepítve. <br><br> Ha az eszközön telepítve van a C alkalmazás, mely az SDK 7.1.9-es verziójával rendelkezik, az ugyanazt a PIN-kódot fogja használni, mint az A alkalmazás. <br><br> Ha a D alkalmazás a 7.1.14-es verzióval készült, az ugyanazt a PIN-kódot fogja használni, mint a B alkalmazás. <br><br> Ha egy eszközön csak az A és a C alkalmazás van telepítve, akkor egy PIN-kódot kell beállítani. Ugyanez arra az esetre is vonatkozik, ha egy eszközön csak a B és a D alkalmazás van telepítve.

**Mi a helyzet a titkosítással?**<br></br>
A rendszergazdák olyan alkalmazásvédelmi szabályzatokat léptethetnek életbe, amelyek előírják az alkalmazásadatok titkosítását. A szabályzat részeként a rendszergazda azt is megadhatja, hogy mikor kell titkosítani a tartalmat.

- **Hogyan titkosítja az adatokat az Intune?**<br></br> Az alkalmazásvédelmi szabályzat titkosítási beállításáról részletes információt [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md) és az [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása](app-protection-policy-settings-ios.md) című cikkekben talál.

- **Mi kerül titkosításra?**<br></br> Csak a rendszergazda alkalmazásvédelmi szabályzatának értelmében „cégesként” megjelölt adatok. „Cégesnek” azok az adatok számítanak, amelyek vállalati forrásból származnak. Az Office-alkalmazásokat illetően az Intune a következőket tekinti vállalati forrásnak: e-mailek (Exchange) vagy felhőbeli tárhely (OneDrive alkalmazás Vállalati OneDrive-fiókkal). Az Intune alkalmazásburkoló eszközével kezelt üzletági alkalmazások esetében minden alkalmazásadat „cégesnek” minősül.

**Hogyan törli távolról az adatokat az Intune?**<br></br>
Az Intune három különböző módon törölhet adatokat: teljes törlés az eszközről, MDM szelektív törlés és MAM szelektív törlés. Az MDM-beli távoli törlésről az [eszközök az összes adat törlésével vagy használatból való kivonással történő eltávolítását](devices-wipe.md) ismertető témakörben találhat további információt. A MAM segítségével végrehajtott szelektív törlésről [A kivonás művelete](devices-wipe.md#retire) és a [Csak a céges adatok törlése az alkalmazásokból](apps-selective-wipe.md) című témakörben tudhat meg többet.

- **Mit jelent az összes adat törlése?**<br></br> Az [összes adat törlése](devices-wipe.md) törli **az eszközről** az összes adatot és beállítást, visszaállítva az alapértelmezett gyári beállításokat. Az eszközt a rendszer eltávolítja az Intune-ból.
  >[!NOTE]
  > Az összes adat törlése csak az Intune mobileszköz-kezelésben regisztrált eszközökön hajtható végre.

- **Mi az MDM szelektív törlés?**<br></br> A céges adatok eltávolításáról az [Eszközök eltávolítása – Kivonás](devices-wipe.md#retire) című témakörben olvashat.

- **Mi az MAM szelektív törlés?**<br></br> A MAM szelektív törlés egyszerűen eltávolítja a vállalati alkalmazásadatokat egy alkalmazásból. A kérelem az Intune Azure-portál használatával küldhető be. A törlési kérelmek kezdeményezéséről a [Csak a céges adatok törlése az alkalmazásokból](apps-selective-wipe.md) című témakörben tájékozódhat.

- **Milyen gyorsan megy végbe az MAM szelektív törlés?**<br></br> Ha a felhasználó a szelektív törlés elindítását követően is használja az alkalmazást, az Intune App SDK 30 percenként ellenőrzi, hogy érkezett-e az Intune MAM szolgáltatásból kérés a szelektív törlésre. Akkor is ellenőrzi a szelektív törlést, amikor a felhasználó először indítja el az alkalmazást és lép be a munkahelyi vagy iskolai fiókjába.

**Miért nem működnek a helyszíni szolgáltatások az Intune-nal védett alkalmazásokkal?**<br></br>
Az Intune alkalmazásvédelem megköveteli a felhasználói identitás konzisztenciáját az alkalmazás és az Intune App SDK között. Ez kizárólag modern hitelesítés révén garantálható. Előfordulnak olyan helyzetek, amelyekben az alkalmazások működnek a helyszíni konfigurációval, ám ezek a forgatókönyvek se nem konzisztensek, se nem garantáltak.

**Létezik biztonságos módja a webes hivatkozások megnyitásának a felügyelt alkalmazásokból?**<br></br>
Igen! A rendszergazda életbe léptethet és beállíthat egy alkalmazásvédelmi szabályzatot az [Intune Managed Browser alkalmazáshoz](app-configuration-managed-browser.md), amely egy, a Microsoft Intune által fejlesztett, az Intune használatával egyszerűen felügyelhető webböngésző. A rendszergazda előírhatja, hogy az Intune által kezelt alkalmazásokban található összes webhivatkozást csak a Managed Browser alkalmazással lehessen megnyitni.



## <a name="app-experience-on-android"></a>Az alkalmazás felhasználói felülete Androidon

**Miért szükséges ahhoz a Munkahelyi portál alkalmazás, hogy az Intune alkalmazásvédelem működjön Android-eszközökön?**<br></br>
A legtöbb alkalmazásvédelmi funkció be van építve a Munkahelyi portál alkalmazásba. Annak ellenére, hogy a Munkahelyi portál alkalmazás mindig szükséges, eszközregisztrációra _nincs szükség_. Az MAM-WE-hez a végfelhasználónak telepítenie kell a Céges portál alkalmazást az eszközre.

**Hogyan működnek az egyazon alkalmazás- és felhasználói csoportokra konfigurált többes Intune alkalmazásvédelmi hozzáférési beállítások az Android-eszközökön?**<br></br>
Az Intune alkalmazásvédelmi hozzáférési szabályzatai adott sorrendben lépnek érvénybe a végfelhasználói eszközökön, amikor azok a vállalati környezetből megkísérelnek hozzáférni az alkalmazásokhoz. A letiltásnak általában elsőbbsége van a bezárható figyelmeztetéssel szemben. Például egy javítási frissítésre figyelmeztető minimálisan előírt androidos biztonsági javítás, ha érvényesíthető az adott felhasználóra/alkalmazásra, csak akkor kerül alkalmazásra, ha már életbe lépett a felhasználó hozzáférését letiltó minimálisan előírt androidos biztonsági javítás. Így tehát ha az informatikai rendszergazda a minimálisan előírt androidos biztonsági javítást 2018. március 1-re, és a (csak figyelmeztetési) minimálisan előírt androidos biztonsági javítást 2018. február 1-re állította be, az alkalmazás elérését megkísérlő eszköz pedig a 2018. január 1-i biztonsági javítást használja, a végfelhasználó a szigorúbb minimálisan előírt androidos biztonsági javítás alapján le lesz tiltva, és nem férhet hozzá az alkalmazáshoz. 

Különböző beállítások esetén először a az alkalmazás verziókövetelménye, majd az androidos operációs rendszer verziókövetelménye és végül az androidos biztonsági javítási verzió követelménye kerül sorra. Ezt követi a beállításokra vonatkozó figyelmeztetések végrehajtása ugyanebben a sorrendben.

**A Intune App Protection házirendek lehetővé teszik a rendszergazdák számára, hogy a végfelhasználói eszközöket a Google biztonság-igazolásának átadásához adják át Android-eszközökre. Milyen gyakran érkezik új biztonság igazolási eredmény a szolgáltatásnak?** <br><br> A Google Play szolgáltatás új meghatározása az Intune szolgáltatás által meghatározott időközönként jelentést küld a rendszergazdának. A szolgáltatás hívásának gyakorisága a terhelés miatt szabályozva van, ezért ez az érték belsőleg marad, és nem konfigurálható. A Google biztonság igazolási beállításához a rendszergazda által konfigurált rendszergazdai műveletek a feltételes indításkor az Intune szolgáltatás utolsó jelentett eredményei alapján lesznek elvégezve. Ha nincs adat, a hozzáférés más feltételes indítási ellenőrzéstől függően nem lehetséges, és a Google Play szolgáltatás "oda" helyezése az igazolási eredmények meghatározásához a háttérbe kerül, és aszinkron módon kéri a felhasználót, ha az eszköz meghibásodik. Elavult adatmennyiség esetén a rendszer letiltja vagy engedélyezi a hozzáférést az utolsó jelentett eredménytől függően, és Hasonlóképpen az igazolási eredmények meghatározásához a Google Play szolgáltatás "oda" helyezése is megkezdődik, és aszinkron módon kéri a felhasználót, ha az eszköz sikertelen volt.

**A Intune App Protection szabályzatok lehetővé teszik a rendszergazdák számára, hogy a végfelhasználói eszközökön jeleket küldjenek az Android-eszközökön a Google ellenőrzése alkalmazások API-n keresztül. Hogyan kapcsolhatja be a végfelhasználó az alkalmazás vizsgálatát, hogy azok ne legyenek letiltva a hozzáférés miatt?**<br><br> Az ehhez szükséges útmutatást az eszköz kissé eltérőnek kell lennie. Az általános folyamat magában foglalja a Google Play Áruház, majd a **saját alkalmazások & játékok**elemre kattint, és az utolsó alkalmazás vizsgálatának eredményére kattint, amely a lejátszás elleni védelem menübe kerül. Ellenőrizze, hogy be van-e kapcsolva a **biztonsági fenyegetések keresése az eszközön** .

**Mit jelent a Google biztonság igazolási API-je az Android-eszközökön? Mi a különbség az "alapszintű integritás ellenőrzése" és az "alapszintű integritás ellenőrzése & tanúsított eszközök" között?** <br><br>
Az Intune kihasználja a Google Play Protect biztonság API-kat a nem regisztrált eszközökhöz való meglévő gyökérszintű észlelési ellenőrzésekhez való hozzáadáshoz. A Google fejleszti és karbantartja ezt az API-készletet az Android-alkalmazások számára, ha nem szeretné, hogy az alkalmazások feltört eszközökön fussanak. Az Android Pay-alkalmazás beépítette ezt, például:. Noha a Google nem osztja meg nyilvánosan a legfelső szintű észlelési ellenőrzéseket, az API-k elvárják, hogy észlelje az eszközeit feltört felhasználókat. Ezek a felhasználók ezt követően le lehet tiltani a hozzáférését, vagy a vállalati fiókjaikat a szabályzattal kompatibilis alkalmazásokból törölve. Az "alapszintű integritás ellenőrzése" című rész az eszköz általános integritását mutatja be. A feltört eszközök, emulátorok, virtuális eszközök és eszközök, amelyekkel a rendszer nem módosítja az alapszintű integritást. "Az alapszintű integritás & minősítésű eszközök ellenőrzése" című rész az eszköznek a Google szolgáltatásaival való kompatibilitását mutatja be. Csak a Google által hitelesített, nem módosított eszközök adhatják át ezt az ellenőrzést. A meghiúsuló eszközök közé tartoznak a következők:
* Alapvető integritást nem teljesítő eszközök
* Zárolt rendszertöltő eszközzel rendelkező eszközök
* Egyéni rendszerkép/ROM-lemezzel rendelkező eszközök
* Eszközök, amelyekhez a gyártó nem kérelmezte a Google minősítést 
* Közvetlenül az Android nyílt forráskódú program forrásfájljait tartalmazó rendszerképpel rendelkező eszközök
* A Beta/Developer Preview rendszerképpel rendelkező eszközök

A technikai részletekért tekintse meg [a Google dokumentációját a biztonság igazolásával](https://developer.android.com/training/safetynet/attestation) kapcsolatban.

**Két hasonló ellenőrzés szerepel a feltételes indítás szakaszban, amikor Intune App Protection szabályzatot hoz létre Android-eszközökhöz. Szükség van-e az "biztonság-eszköz igazolása" beállításra vagy a "feltört/feltört eszközök" beállításra?** <br><br>
A Google Play Protect biztonság API-ellenőrzései megkövetelik, hogy a végfelhasználó online állapotba kerüljön, amely az igazolási eredmények meghatározásához szükséges idő időtartamára vonatkozik. Ha a végfelhasználó offline állapotban van, a rendszergazda továbbra is várhatja, hogy az eredmény kényszerítve legyen a "feltört eszközök" beállításra. Ennek ellenére, ha a végfelhasználó offline állapotban van, az "offline türelmi időszak" érték lejátszásra kerül, és a munkahelyi vagy iskolai adataihoz való összes hozzáférés le lesz tiltva az időzítő értékének elérésekor, amíg a hálózati hozzáférés elérhetővé nem válik. Mindkét beállítás bekapcsolása lehetővé teszi, hogy egy rétegzett megközelítés legyen a végfelhasználói eszközökön, ami akkor fontos, ha a végfelhasználók a mobilon férnek hozzá munkahelyi vagy iskolai információhoz. 

**A Google Play Protect API-kat használó app Protection-házirend beállításai megkövetelik a Google Play-szolgáltatások működését. Mi a teendő, ha a Google Play-szolgáltatások nem engedélyezettek abban a helyen, ahol a végfelhasználó lehet?**<br><br>
A "biztonság-eszköz igazolása" és a "veszélyforrások vizsgálata az alkalmazásokban" beállításhoz a Google Play-szolgáltatások meghatározott verziójának megfelelő működésre van szükség. Mivel ezek olyan beállítások, amelyek a biztonság területéhez tartoznak, a végfelhasználó le lesz tiltva, ha ezeket a beállításokat megcélozták, és nem felelnek meg a Google Play-szolgáltatások megfelelő verziójának, vagy nincs hozzáférésük a Google Play-szolgáltatásokhoz. 

## <a name="app-experience-on-ios"></a>Az alkalmazás felhasználói felülete iOS-en
**Mi történik, ha hozzáadok vagy eltávolítok egy ujjlenyomatot vagy arcot a saját eszközről?**<br></br>
Az Intune alkalmazásvédelmi szabályzatai csak az Intune licencelt felhasználójának teszik lehetővé az alkalmazás elérésének szabályozását. Az alkalmazáshoz való hozzáférés szabályozásának egyik módja az Apple Touch ID vagy a Face ID megkövetelése a támogatott eszközökön. Az Intune olyan viselkedést vezet be, ahol az eszköz biometrikus adatbázisának bármilyen változása esetén az Intune PIN-kódot kér a felhasználótól a következő inaktivitási időkorlát elérése esetén. A biometrikus adatok módosításai tartalmazzák az arc vagy ujjlenyomat hozzáadását és eltávolítását. Ha az Intune-felhasználóhoz nincs beállítva PIN-kód, a rendszer felszólítja az Intune PIN-kód beállítására.
 
Ennek célja az alkalmazáson belüli céges adatok védelmének biztosítása az alkalmazás szintjén. Ez a funkció csak az iOS-ben érhető el, és a működéséhez szükséges az alkalmazások integrálása az Intune APP SDK for iOS 9.0.1-es vagy újabb verziójával. Az SDK-integráció szükséges a viselkedés kényszeríthetőségéhez a megcélzott alkalmazásoknál. Ez az integráció fokozatosan történik, és az egyes alkalmazáscsapatoktól függ. Néhány alkalmazás, amely ezek között szerepelhet: WXP, Outlook, Managed Browser és Yammer. 
  
**Az iOS megosztási bővítménnyel megnyithatom a munkahelyi vagy az iskolai adatokat a nem felügyelt alkalmazásokban, még akkor is, ha az adatátviteli szabályzat beállítása „csak felügyelt alkalmazások” vagy „nincs alkalmazás”. Nem jár ez adatszivárgással?**<br></br>
Az Intune alkalmazásvédelmi szabályzata nem tudja kezelni az iOS megosztási bővítményt az eszköz felügyelete nélkül. Ezért az _**Intune titkosítja a „céges” adatokat, mielőtt az alkalmazáson kívül megosztaná**_ . Ezt úgy ellenőrizheti, hogy megpróbálja megnyitni a „céges” fájlt a felügyelt alkalmazáson kívül. A fájlnak titkosítottnak kell lennie, így a felügyelt alkalmazáson kívül mással nem nyitható meg.

**Hogyan működnek az egyazon alkalmazás- és felhasználói csoportokra konfigurált többes Intune alkalmazásvédelmi hozzáférési beállítások az iOS-eszközökön?**<br></br>
Az Intune alkalmazásvédelmi hozzáférési szabályzatai adott sorrendben lépnek érvénybe a végfelhasználói eszközökön, amikor azok a vállalati környezetből megkísérelnek hozzáférni az alkalmazásokhoz. A törlésnek általában elsőbbsége van, ezt követi a letiltás és a bezárható figyelmeztetés. Például az iOS-verzió frissítésére figyelmeztető minimálisan előírt iOS operációsrendszer-beállítás, ha érvényesíthető az adott felhasználóra/alkalmazásra, csak akkor kerül alkalmazásra, ha már életbe lépett a felhasználó hozzáférését letiltó minimálisan előírt iOS operációsrendszer-beállítás. Így tehát ha az informatikai rendszergazda a minimális iOS operációs rendszert 11.0.0.0-ra, a (csak figyelmeztetési) minimális iOS operációs rendszert 11.1.0.0-ra állította be, az alkalmazás elérését megkísérlő eszköz pedig az iOS 10-et használja, a végfelhasználó a minimális iOS operációsrendszer-verzióra vonatkozó szigorúbb beállítás alapján le lesz tiltva, és nem férhet hozzá az alkalmazáshoz.

Különböző beállítások esetén először a az Intune App SDK verziókövetelménye, majd az alkalmazásverzió követelménye és végül az iOS operációs rendszer verziókövetelménye kerül sorra. Ezt követi a beállításokra vonatkozó figyelmeztetések végrehajtása ugyanebben a sorrendben. Azt javasoljuk, hogy az Intune App SDK verziókövetelményét csak az Intune termékért felelős csoport alapvető letiltási esetekre vonatkozó útmutatása alapján állítsa be.


## <a name="see-also"></a>Lásd még:
- [Az Intune-terv megvalósítása](planning-guide-onboarding.md)
- [Az Intune tesztelése és ellenőrzése](planning-guide-test-validation.md)
- [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md)
- [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása](app-protection-policy-settings-ios.md)
- [Alkalmazás-védelmi szabályzatok házirend frissítése](app-protection-policy-delivery.md)
- [Az alkalmazásvédelmi szabályzatok ellenőrzése](app-protection-policy-delivery.md)
- [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül](app-configuration-policies-managed-app.md)
- [Microsoft Intune-támogatás kérése](get-support.md)
