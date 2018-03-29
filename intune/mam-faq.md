---
title: Gyakori kérdések az MAM-ről és az alkalmazásvédelemről
description: Ez a cikk az Intune mobilalkalmazás-kezeléssel (MAM) és az Intune alkalmazásvédelemmel kapcsolatos gyakori kérdésekre adott válaszokat ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0ab616c373482109ccd402199f7b0de69fe27348
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/22/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Gyakori kérdések az MAM-ről és az alkalmazásvédelemről

Ez a cikk az Intune mobilalkalmazás-kezeléssel (MAM) és az Intune alkalmazásvédelemmel kapcsolatos gyakori kérdésekre adott válaszokat ismerteti.

## <a name="mam-basics"></a>Az MAM alapjai


**Mi az MAM?** Az [Intune mobilalkalmazás-kezelés](/intune/app-lifecycle) olyan Intune-beli felügyeleti összetevők csoportja, amelyek lehetővé teszik mobilalkalmazások közzétételét és leküldését a felhasználók részére, valamint azok konfigurálását, védelmét, figyelését és frissítését.

**Milyen előnyöket kínál az MAM-alkalmazásvédelem?** Az MAM védi munkahelye adatait az alkalmazáson belül. A regisztráció nélküli MAM (MAM-WE) segítségével a bizalmas adatokat tartalmazó munkahelyi vagy iskolai alkalmazások szinte bármilyen eszközön felügyelhetők, beleértve a személyes tulajdonú eszközöket is saját eszközök használata (BYOD) esetén. Több irodai alkalmazás felügyelhető az Intune MAM-mel, például a Microsoft Office-alkalmazások. Lásd a nyilvánosan elérhető, [Intune által kezelt alkalmazások](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) hivatalos listáját.

**Milyen eszközkonfigurációkat támogat az MAM?** Az Intune MAM két konfigurációt támogat:
- **Intune MDM és MAM:** A rendszergazda csak az Intune mobileszköz-kezelésben (MDM) regisztrált eszközökön felügyelheti a MAM- és alkalmazásvédelmi szabályzatokat használó alkalmazásokat. Az MDM-et és MAM-ot használó alkalmazások felügyeletéhez a https://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt.

- **MAM eszközregisztráció nélkül:** az eszközregisztráció nélküli MAM (MAM-WE) révén a rendszergazda felügyelheti az Intune MDM-ben nem regisztrált eszközökön található, MAM- és alkalmazásvédelmi szabályzatot használó alkalmazásokat. Ez azt jelenti, hogy az Intune csak külső EMM-szolgáltatóknál regisztrált eszközökön felügyelheti az alkalmazásokat. Az MAM-WE-t használó alkalmazások felügyeletéhez a http://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt. Emellett az Intune-nal felügyelheti az alkalmazásokat olyan eszközökön, amelyek harmadik féltől származó nagyvállalati mobilitási felügyeleti (EMM) rendszerben vannak regisztrálva, illetve nincsenek regisztrálva egyetlen mobileszköz-kezelési rendszerben sem.


## <a name="app-protection-policies"></a>Alkalmazásvédelmi szabályzatok

**Mik azok az alkalmazásvédelmi szabályzatok?** Az alkalmazásvédelmi szabályzatok olyan szabályok, amelyek biztosítják, hogy a céges adatok biztonságban maradnak, és nem kerülnek ki a felügyelt alkalmazásokból. A szabályzat egyfelől lehet olyan szabály, amely olyankor lép életbe, amikor a felhasználó megpróbál hozzáférni „céges” adatokhoz vagy áthelyezni azokat, másfelől azon műveletek csoportja, amelyeket a rendszer tilt vagy figyel, amikor az felhasználó az alkalmazást használja.

**Milyen példák vannak az alkalmazásvédelmi szabályzatok használatára?** Az alkalmazásvédelmi szabályzat egyes beállításairól részletes információt [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban ](app-protection-policy-settings-android.md) és az [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása ](app-protection-policy-settings-ios.md) című cikkekben talál.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Az alkalmazásvédelmi szabályzatokkal felügyelhető alkalmazások

**Mely alkalmazásokat lehet alkalmazásvédelmi szabályzatokkal felügyelni?** Az [Intune App SDK](/intune/app-sdk) által integrált vagy az [Intune alkalmazásburkoló eszköz](/intune/apps-prepare-mobile-application-management) által beburkolt, Intune alkalmazásvédelmi szabályzatokat használó alkalmazásokat. Lásd a nyilvánosan elérhető, [Intune által kezelt alkalmazások](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) hivatalos listáját.

**Mik az alkalmazásvédelmi szabályzatok Intune által kezelt alkalmazáson való használatának alapkövetelményei?**
- A végfelhasználónak rendelkeznie kell egy Azure Active Directory- (AAD-) fiókkal. Az Intune-felhasználók Azure Active Directoryban történő létrehozásáról lásd: [Felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](/intune/users-permissions-add).

- A végfelhasználónak rendelkeznie kell az Azure Active Directory-fiókjához rendelt Microsoft Intune-licenccel. További információ a végfelhasználókhoz rendelt Intune-licencekről: [Intune-licencek kezelése](/intune/licenses-assign).

- A végfelhasználónak egy alkalmazásvédelmi szabályzattal társított biztonsági csoporthoz kell tartoznia. Ugyanezen alkalmazásvédelmi szabályzatnak a használt alkalmazással is társítva kell lennie. Alkalmazásvédelmi csoportokat az [Azure-portálon](http://portal.azure.com) található Intune-konzolban lehet létrehozni és telepíteni. Biztonsági csoportot jelenleg az [Office-portálon](http://portal.office.com) lehet létrehozni.

- A végfelhasználónak saját AAD-fiókjával be kell jelentkeznie az alkalmazásba.

**Mik az [Outlook mobilalkalmazás](https://products.office.com/outlook) használatának további feltételei?**

- A végfelhasználónak telepítenie kell az Outlook mobilalkalmazást az eszközére.

- A végfelhasználónak [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) postaládával és az AAD-fiókjához kapcsolt licenccel kell rendelkeznie.

  >[!NOTE]
  > Az Outlook mobilalkalmazás jelenleg csupán a Microsoft Exchange Online-t támogatja, a helyszíni Exchange-t vagy az Office 365 dedikált verzióban található Exchange-t nem.

**Mik a [Word, az Excel és a PowerPoint](https://products.office.com/business/office) alkalmazás használatának további feltételei?**

- A végfelhasználónak rendelkeznie kell az Azure Active Directory-fiókjához rendelt [Office 365 Vállalati vagy Nagyvállalati verzió](https://products.office.com/business/compare-more-office-365-for-business-plans) licencével. Az előfizetésnek tartalmaznia kell a mobileszközökön használt Office-alkalmazásokat, és egy felhőalapú társzolgáltatás-fiókot is tartalmazhat a [OneDrive Vállalati verzióban](https://onedrive.live.com/about/business/). Az Office 365 licenc az [Office-portálon](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc) történő hozzárendeléséhez kövesse [ezeket az utasításokat](http://portal.office.com).

- A végfelhasználónak egy olyan felügyelt hellyel kell rendelkeznie, amelyet a részletes mentés másként funkcióval konfiguráltak „A Mentés másként művelet letiltása” alkalmazásvédelmi szabályzatbeállítás alatt. Ha például a felügyelt hely a OneDrive, a [OneDrive](https://onedrive.live.com/about/) alkalmazást konfigurálni kell a felhasználó Word, Excel és PowerPoint alkalmazásában.

- Ha a felügyelt hely a OneDrive, a végfelhasználóra életbe léptetett alkalmazásvédelmi szabályzatnak társítva kell lennie a OneDrive alkalmazással.

  >[!NOTE]
  > Az Office-mobilalkalmazások jelenleg csak a SharePoint Online verziót támogatják, a helyszíni SharePoint rendszert nem.

**Miért szükséges felügyelt hely (például a OneDrive) az Office-hoz?** Az Intune az alkalmazásban található összes adatot „cégesként” vagy „személyesként” jelöli meg. „Cégesnek” azok az adatok számítanak, amelyek vállalati forrásból származnak. Az Office-alkalmazásokat illetően az Intune a következőket tekinti vállalati forrásnak: e-mailek (Exchange) vagy felhőbeli tárhely (OneDrive alkalmazás Vállalati OneDrive-fiókkal).

**Mik a Skype Vállalati verzió használatának további feltételei?** A licenckövetelményekért lásd: [Skype Vállalati verzió](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > A Skype Vállalati verzió mobilalkalmazás jelenleg csupán a Skype Vállalati online verziót támogatja.

## <a name="app-protection-features"></a>Alkalmazásvédelmi funkciók

**Mit jelent a többszörös identitás támogatása?** A többszörösidentitás-támogatás az Intune App SDK-nak azt a képességét jelenti, hogy csak az alkalmazásba bejelentkezett munkahelyi vagy iskolai fiókra alkalmazza az alkalmazásvédelmi szabályzatokat. Ha egy személyes fiók van bejelentkezve az alkalmazásba, az adatok érintetlenek maradnak.

**Mi a többszörösidentitás-támogatás célja?** A többszörösidentitás-támogatással a „céges” és fogyasztói célközönséggel egyaránt rendelkező alkalmazások (például az Office-alkalmazások) nyilvánossá tételekor a „céges” fiókokhoz beállítható az Intune alkalmazásvédelmi funkciója.

**Mi helyzet az Outlook többszörös identitással való használata esetén?** Mivel az Outlook a személyes és a „céges” e-mailek kombinált nézetét kínálja, az Outlook alkalmazás már az indításkor kéri az Intune PIN-kódját.

**Mire szolgál az Intune az alkalmazáshoz tartozó PIN-kódja?** A személyes azonosítószám (PIN-kód) egy olyan kód, amellyel ellenőrizni lehet, hogy egy alkalmazásban a megfelelő felhasználó fér-e hozzá a céges adatokhoz.

- **Mikor kell a felhasználónak megadni a PIN-kódját?** Az Intune kéri a felhasználó PIN-kódját az alkalmazáshoz, amikor a felhasználó „céges” adatokhoz kísérel meg hozzáférni. A többszörös identitást használó alkalmazások, például a Word/Excel/PowerPoint esetében a felhasználónak akkor kell megadnia a PIN-kódját, mikor „céges” dokumentumot vagy fájlt próbál megnyitni. Az egyszeres identitást kezelő alkalmazások, például az Intune-os alkalmazásburkoló eszköz használatával előkészített üzletági alkalmazások már indításkor kérik a PIN-kódot, ugyanis az Intune App SDK tudja, hogy a felhasználó tevékenysége az alkalmazásban mindig „céges”.

- **Milyen gyakran kell a felhasználónak megadnia az Intune PIN-kódját?**
  A rendszergazda az Intune felügyeleti konzolján beállíthatja az Intune alkalmazásvédelmi szabályzatának „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítását. Ez a beállítás azt határozza meg, hogy mennyi idő után ellenőrzi a rendszer a hozzáférési követelményeket az eszközön, és jelenik meg újból az alkalmazás PIN-kódot bekérő képernyője. Ugyanakkor a PIN-kóddal kapcsolatos alábbi fontos információk is befolyásolják, hogy a rendszer milyen gyakran kér felhasználói bevitelt: 

    - **A használhatóság fokozása érdekében az ugyanattól a gyártótól származó alkalmazások megosztott PIN-kódot használnak:** Az iOS-ben minden **ugyanattól a gyártótól származó** alkalmazás egyetlen közös alkalmazásszintű PIN-kódot használ. Androidon minden alkalmazás egyetlen közös alkalmazásszintű PIN-kódot használ.
    - **A PIN-kódhoz társított számláló gördülő jellege:** amikor megadják a PIN-kódot egy alkalmazás (az A alkalmazás) eléréséhez, és az alkalmazás kikerül az előtérből (a bemenet fő fókuszából) az eszközön, ezen PIN-kód számlálója alaphelyzetbe áll. Egy olyan alkalmazás (B alkalmazás) sem fogja bekérni a PIN-kódot a felhasználótól, amely szintén ezt a PIN-kódot használja, mivel a számláló alaphelyzetbe állt. Az adatkérés akkor jelenik meg újra, amikor a rendszer ismét eléri a „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítás értékét. 

      >[!NOTE] 
      > A felhasználó hozzáférési követelményeinek gyakoribb ellenőrzése (azaz a PIN-kód kérése) érdekében, különösen a gyakran használt alkalmazások esetében javasolt csökkenteni a „Hozzáférési követelmények újbóli ellenőrzése ennyi idő után (perc)” beállítás értéket. 

- **Biztonságos-e a PIN-kód?** A PIN-kód arra szolgál, hogy csak a megfelelő felhasználó férhessen hozzá az alkalmazásban a céges adatokhoz. Így az alkalmazás Intune-beli PIN-kódjának megváltoztatásához a végfelhasználónak be kell jelentkeznie a munkahelyi vagy iskolai fiókjával. Ezt a hitelesítést az Azure Active Directory biztonságos jogkivonatcsere révén kezeli, ami nem transzparens az Intune App SDK számára. A munkahelyi vagy iskolai adatok védelmére biztonsági szemszögből a titkosítás a legjobb módszer. A titkosítás nem függ össze az alkalmazás PIN-kódjával, csak annak saját alkalmazásvédelmi szabályzatával.

- **Hogyan védi a PIN-kódot az Intune a találgatásos támadásoktól?** Az alkalmazás PIN-szabályzatának részeként a rendszergazda beállíthatja, hogy legfeljebb hányszor adhatja meg a felhasználó a PIN-kódját, mielőtt a rendszer zárolná az alkalmazást. Bizonyos számú kísérlet után az Intune App SDK törölheti az összes „céges” adatot az alkalmazásban.
  
- **Miért kell kétszer beállítanom a PIN-kódot az ugyanattól a gyártótól származó alkalmazások esetében?**
  A MAM (az iOS esetében) jelenleg az alfanumerikus, valamint speciális karaktereket is tartalmazó alkalmazásszintű PIN-kódok (ún. hitelesítő kódok) használatát teszi lehetővé, amihez szükséges, hogy az alkalmazások (például a WXP, az Outlook, a Managed Browser és a Yammer) integrálják az iOS-es Intune APP SDK-t. Az integráció hiányában a PIN-jelszóbeállítások nem lesznek megfelelően megkövetelve a megcélzott alkalmazásoknál. Ez a szolgáltatás az iOS-hez készült Intune SDK következő verziójában jelent meg: 7.1.12. <br><br> A szolgáltatás támogatása és az iOS-hez készült Intune SDK előző verzióival való kompatibilitás biztosítása érdekében a 7.1.12-es és újabb verziókban minden PIN-kód (akár numerikus, akár hitelesítő kód) az SDK korábbi verzióinak numerikus PIN-kódjaitól elkülönítve van kezelve. Így ha egy eszközön olyan alkalmazások találhatók, melyek az iOS-hez készült Intune SDK 7.1.12-esnél korábbi ÉS 7.1.12-esnél újabb verziójával rendelkeznek, és ugyanattól a gyártótól származnak, ezekhez két PIN-kódot kell beállítani. <br><br> Ugyanakkor a két PIN-kód között (melyek az egyes alkalmazásokhoz tartoznak) semmilyen kapcsolat nincs, azaz meg kell felelniük az alkalmazásra vonatkozó alkalmazásvédelmi szabályzatnak. Ennek megfelelően a felhasználó *csak* akkor állíthatja be kétszer ugyanazt a PIN-kódot, ha az A és a B alkalmazásra ugyanazok a szabályzatok érvényesek (a PIN-kódokra vonatkozóan). <br><br> Ez a viselkedés kizárólag az Intune mobilalkalmazás-felügyeleti funkciójával engedélyezett iOS-alkalmazások PIN-kódjaira jellemző. Ahogy az idő múlásával az alkalmazások az iOS-hez készült Intune SDK újabb verzióira térnek át, egyre kisebb problémát fog jelenteni, hogy kétszer kell beállítani a PIN-kódot az ugyanazon gyártótól származó alkalmazásokhoz. Erre az alábbi megjegyzésben találhat egy példát.

  >[!NOTE]
  > Ha például az A alkalmazás egy 7.1.12-esnél korábbi verzióval készült, a B alkalmazás pedig a 7.1.12-es vagy annál újabb verzióval készült, és a kettő ugyanazon gyártótól származik, a végfelhasználónak külön kell majd PIN-kódot beállítania az A-hoz és a B-hez, ha mindkettő egy iOS-es eszközre van telepítve. <br><br> Ha az eszközön telepítve van a C alkalmazás, mely az SDK 7.1.9-es verziójával rendelkezik, az ugyanazt a PIN-kódot fogja használni, mint az A alkalmazás. <br><br> Ha a D alkalmazás a 7.1.14-es verzióval készült, az ugyanazt a PIN-kódot fogja használni, mint a B alkalmazás. <br><br> Ha egy eszközön csak az A és a C alkalmazás van telepítve, akkor egy PIN-kódot kell beállítani. Ugyanez arra az esetre is vonatkozik, ha egy eszközön csak a B és a D alkalmazás van telepítve.

**Mi a helyzet a titkosítással?** A rendszergazdák olyan alkalmazásvédelmi szabályzatokat léptethetnek életbe, amelyek előírják az alkalmazásadatok titkosítását. A szabályzat részeként a rendszergazda azt is megadhatja, hogy mikor kell titkosítani a tartalmat.

- **Hogyan titkosítja az adatokat az Intune?** Az alkalmazásvédelmi szabályzat titkosítási beállításáról részletes információt [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md) és az [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása](app-protection-policy-settings-ios.md) című cikkekben talál.

- **Mi kerül titkosításra?** Csak a rendszergazda alkalmazásvédelmi szabályzatának értelmében „cégesként” megjelölt adatok. „Cégesnek” azok az adatok számítanak, amelyek vállalati forrásból származnak. Az Office-alkalmazásokat illetően az Intune a következőket tekinti vállalati forrásnak: e-mailek (Exchange) vagy felhőbeli tárhely (OneDrive alkalmazás Vállalati OneDrive-fiókkal). Az Intune alkalmazásburkoló eszközével kezelt üzletági alkalmazások esetében minden alkalmazásadat „cégesnek” minősül.

**Hogyan törli távolról az adatokat az Intune?** Az Intune három különböző módon törölhet adatokat: teljes törlés az eszközről, MDM szelektív törlés és MAM szelektív törlés. Az MDM-beli távoli törlésről további információt az [Eszközök eltávolítása a gyári beállítások visszaállításával vagy a céges adatok eltávolításával](devices-wipe.md#factory-reset) című témakörben találhat. A MAM segítségével végrehajtott szelektív törlésről a [Céges adatok eltávolítása](devices-wipe.md#remove-company-data) és a [Csak a céges adatok törlése az alkalmazásokból](apps-selective-wipe.md) című témakörben tudhat meg többet.

- **Mit jelent a gyári beállítások visszaállítása?** A [gyári beállítások visszaállítása](devices-wipe.md) törli **az eszközről** az összes adatot és beállítást, visszaállítva az alapértelmezett gyári beállításokat. Az eszközt a rendszer eltávolítja az Intune-ból.
  >[!NOTE]
  > A gyári beállítások visszaállítása csak az Intune mobileszköz-kezelésben regisztrált eszközökön hajtható végre.

- **Mi az MDM szelektív törlés?** A céges adatok eltávolításáról az [Eszközök eltávolítása – Céges adatok eltávolítása](devices-wipe.md#remove-company-data) című témakörben olvashat.

- **Mi az MAM szelektív törlés?** A MAM szelektív törlés egyszerűen eltávolítja a vállalati alkalmazásadatokat egy alkalmazásból. A kérelem az Intune Azure-portál használatával küldhető be. A törlési kérelmek kezdeményezéséről a [Csak a céges adatok törlése az alkalmazásokból](apps-selective-wipe.md) című témakörben tájékozódhat.

- **Milyen gyorsan megy végbe az MAM szelektív törlés?** Ha a felhasználó a szelektív törlés elindítását követően is használja az alkalmazást, az Intune App SDK 30 percenként ellenőrzi, hogy érkezett-e az Intune MAM szolgáltatásból kérés a szelektív törlésre. Akkor is ellenőrzi a szelektív törlést, amikor a felhasználó először indítja el az alkalmazást és lép be a munkahelyi vagy iskolai fiókjába.

**Miért nem működnek a helyszíni szolgáltatások az Intune-nal védett alkalmazásokkal?** Az Intune alkalmazásvédelem megköveteli a felhasználói identitás konzisztenciáját az alkalmazás és az Intune App SDK között. Ez kizárólag modern hitelesítés révén garantálható. Előfordulnak olyan helyzetek, amelyekben az alkalmazások működnek a helyszíni konfigurációval, ám ezek a forgatókönyvek se nem konzisztensek, se nem garantáltak.

**Létezik biztonságos módja a webes hivatkozások megnyitásának a felügyelt alkalmazásokból?** Igen! A rendszergazda életbe léptethet és beállíthat egy alkalmazásvédelmi szabályzatot az [Intune Managed Browser alkalmazáshoz](app-configuration-managed-browser.md), amely egy, a Microsoft Intune által fejlesztett, az Intune használatával egyszerűen felügyelhető webböngésző. A rendszergazda előírhatja, hogy az Intune által kezelt alkalmazásokban található összes webhivatkozást csak a Managed Browser alkalmazással lehessen megnyitni.

## <a name="app-experience-on-android"></a>Az alkalmazás felhasználói felülete Androidon

**Miért szükséges ahhoz a Munkahelyi portál alkalmazás, hogy az Intune alkalmazásvédelem működjön Android-eszközökön?** A legtöbb alkalmazásvédelmi funkció be van építve a Munkahelyi portál alkalmazásba. Annak ellenére, hogy a Munkahelyi portál alkalmazás mindig szükséges, eszközregisztrációra _nincs szükség_. Az MAM-WE-hez a végfelhasználónak telepítenie kell a Céges portál alkalmazást az eszközre.

**Hogyan működnek az egyazon alkalmazás- és felhasználói csoportokra konfigurált többes Intune alkalmazásvédelmi hozzáférési beállítások az Android-eszközökön?** Az Intune alkalmazásvédelmi hozzáférési szabályzatai adott sorrendben lépnek érvénybe a végfelhasználói eszközökön, amikor azok a vállalati környezetből megkísérelnek hozzáférni az alkalmazásokhoz. A letiltásnak általában elsőbbsége van az elvethető figyelmeztetéssel szemben. Például egy javítási frissítésre figyelmeztető minimálisan előírt androidos biztonsági javítás, ha érvényesíthető az adott felhasználóra/alkalmazásra, csak akkor kerül alkalmazásra, ha már életbe lépett a felhasználó hozzáférését letiltó minimálisan előírt androidos biztonsági javítás. Így tehát ha az informatikai rendszergazda a minimálisan előírt androidos biztonsági javítást 2018. március 1-re, és a (csak figyelmeztetési) minimálisan előírt androidos biztonsági javítást 2018. február 1-re állította be, az alkalmazás elérését megkísérlő eszköz pedig a 2018. január 1-i biztonsági javítást használja, a végfelhasználó a szigorúbb minimálisan előírt androidos biztonsági javítás alapján le lesz tiltva, és nem férhet hozzá az alkalmazáshoz. 

Különböző beállítások esetén először a az alkalmazás verziókövetelménye, majd az androidos operációs rendszer verziókövetelménye és végül az androidos biztonsági javítási verzió követelménye kerül sorra. Ezt követi a beállításokra vonatkozó figyelmeztetések végrehajtása ugyanebben a sorrendben.

## <a name="app-experience-on-ios"></a>Az alkalmazás felhasználói felülete iOS-en

**Az iOS megosztási bővítménnyel megnyithatom a munkahelyi vagy az iskolai adatokat a nem felügyelt alkalmazásokban, még akkor is, ha az adatátviteli szabályzat beállítása „csak felügyelt alkalmazások” vagy „nincs alkalmazás”. Nem jár ez adatszivárgással?** Az Intune alkalmazásvédelmi szabályzata nem tudja kezelni az iOS megosztási bővítményt az eszköz felügyelete nélkül. Ezért az _**Intune titkosítja a „céges” adatokat, mielőtt az alkalmazáson kívül megosztaná**_. Ezt úgy ellenőrizheti, hogy megpróbálja megnyitni a „céges” fájlt a felügyelt alkalmazáson kívül. A fájlnak titkosítottnak kell lennie, így a felügyelt alkalmazáson kívül mással nem nyitható meg.

**Hogyan működnek az egyazon alkalmazás- és felhasználói csoportokra konfigurált többes Intune alkalmazásvédelmi hozzáférési beállítások az iOS-eszközökön?** Az Intune alkalmazásvédelmi hozzáférési szabályzatai adott sorrendben lépnek érvénybe a végfelhasználói eszközökön, amikor azok a vállalati környezetből megkísérelnek hozzáférni az alkalmazásokhoz. A törlésnek általában elsőbbsége van, ezt követi a letiltás és az elvethető figyelmeztetés. Például az iOS-verzió frissítésére figyelmeztető minimálisan előírt iOS operációsrendszer-beállítás, ha érvényesíthető az adott felhasználóra/alkalmazásra, csak akkor kerül alkalmazásra, ha már életbe lépett a felhasználó hozzáférését letiltó minimálisan előírt iOS operációsrendszer-beállítás. Így tehát ha az informatikai rendszergazda a minimális iOS operációs rendszert 11.0.0.0-ra, a (csak figyelmeztetési) minimális iOS operációs rendszert 11.1.0.0-ra állította be, az alkalmazás elérését megkísérlő eszköz pedig az iOS 10-et használja, a végfelhasználó a minimális iOS operációsrendszer-verzióra vonatkozó szigorúbb beállítás alapján le lesz tiltva, és nem férhet hozzá az alkalmazáshoz.

Különböző beállítások esetén először a az Intune App SDK verziókövetelménye, majd az alkalmazásverzió követelménye és végül az iOS operációs rendszer verziókövetelménye kerül sorra. Ezt követi a beállításokra vonatkozó figyelmeztetések végrehajtása ugyanebben a sorrendben. Azt javasoljuk, hogy az Intune App SDK verziókövetelményét csak az Intune termékért felelős csoport alapvető letiltási esetekre vonatkozó útmutatása alapján állítsa be.

## <a name="see-also"></a>Lásd még:
- [Az Intune-terv megvalósítása](planning-guide-onboarding.md)
- [Az Intune tesztelése és ellenőrzése](planning-guide-test-validation.md)
- [Az Android mobilalkalmazás-felügyeleti szabályzatának beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md)
- [iOS mobilalkalmazás-felügyeleti szabályzat konfigurálása](app-protection-policy-settings-ios.md)
- [Az alkalmazásvédelmi szabályzatok ellenőrzése](app-protection-policies-validate.md)
- [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül](app-configuration-policies-managed-app.md)
- [Microsoft Intune-támogatás kérése](get-support.md)
