---
title: A Céges portál alkalmazás konfigurálása
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan alkalmazhatja a vállalatra jellemző arculatot a Intune Céges portál alkalmazásra.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b750c09207b1950aa27a5f2cae1267503537b6e7
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199197"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>A Microsoft Intune Céges portál alkalmazásának konfigurálása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A felhasználók a Microsoft Intune Céges portálon férhetnek hozzá a vállalati adatokhoz, és olyan gyakori feladatokat hajthatnak végre, mint például az eszközök regisztrálása, az alkalmazások telepítése és az informatikai támogatási információk megtekintése. Emellett a vállalati portál alkalmazás lehetővé teszi a felhasználó számára a vállalati erőforrások biztonságos elérését. A vállalati portál alkalmazás több különböző oldalt is biztosít, például a kezdőlapot, az alkalmazásokat, az alkalmazás részleteit, az eszközöket és az eszközök részleteit. A Céges portálon belüli alkalmazások gyors megtalálásához az alkalmazások lapon szűrheti az alkalmazásokat.

> [!IMPORTANT]
> A Google Firebase Cloud Messaging (FCM) támogatásához frissítenie kell az Android Céges portál alkalmazást a legújabb verzióra.  

> [!Tip]
> A vállalati portál testreszabása a vállalati portál webhelyére és a vállalati portál alkalmazásaira egyaránt hatással van. Vegye figyelembe, hogy a felhasználóknak Intune-licenccel kell rendelkezniük a Céges portál webhely eléréséhez.

A Céges portál személyre szabásával segítséget nyújt a végfelhasználók számára ismerős és hasznos felhasználói élményben. Ehhez az Intune-portálon válassza az **ügyfélalkalmazások** > a **branding és a Testreszabás**lehetőséget, majd konfigurálja a szükséges beállításokat.

Amikor egy felhasználó egy iOS-alkalmazást telepít a Céges portál, a rendszer kérni fogja a kérést. Ez akkor fordul elő, ha az iOS-alkalmazás az alkalmazás-áruházhoz van csatolva, egy mennyiségi vásárlási programhoz (VPP) vagy egy üzletági (LOB) alkalmazáshoz csatolva. A prompt lehetővé teszi, hogy a felhasználók elfogadják a műveletet, vagy engedélyezzék az alkalmazás felügyeletét. A prompt megjeleníti a vállalat nevét, vagy ha a cég neve nem érhető el, **céges portál** jelenik meg. 

> [!Note]
> Az Azure Government használata esetében a végfelhasználó alkalmazásnaplókkal döntheti el, hogy hogyan végzi a megosztást, amikor segítségkérési folyamatot indít el egy probléma kapcsán. Ha azonban nem az Azure Governmentet használja, akkor a Windows 10 Céges portál közvetlenül a Microsoftnak küldi az alkalmazásnaplókat, amikor egy felhasználó segítségkérési folyamatot indít el egy probléma kapcsán. Az alkalmazásnaplók Microsoftnak való elküldésével könnyebben háríthatók el és oldhatók meg a problémák. 

## <a name="company-information-and-privacy-statement"></a>A vállalat adatai és adatvédelmi nyilatkozata
A vállalat neve a Vállalati portál címeként jelenik meg. Az adatvédelmi nyilatkozat az Adatvédelem hivatkozásra kattintva jeleníthető meg.

| Mező neve | Maximális hossz | További információ |
|---|---|---|
|**Vállalat neve**| 40 | Ez a név a Céges portál címeként jelenik meg, és az Intune használata alatt végig szöveges formában olvasható. |
| **Az adatvédelmi nyilatkozat URL-címe** |     79     | Itt adhatja meg vállalatának adatvédelmi nyilatkozatát, amely akkor jelenik meg, ha a felhasználó a Vállalati portál adatvédelmi hivatkozásaira kattint. Érvényes URL-címet kell megadnia, a következő formátumban: `<https://www.contoso.com>`. |

> [!NOTE]
> A Microsoft és az Apple-szabályzattal összhangban a szolgáltatás által gyűjtött adatokat semmilyen okból nem adjuk át semmilyen harmadik félnek.

## <a name="support-information"></a>Támogatási információk
Adja meg a vállalat támogatási információit, hogy az alkalmazottak számára az Intune-nal kapcsolatos kérdésekre vonatkozó kapcsolatfelvételt nyújtson.

|Mező neve|Maximális hossz|További információ|
|---|---|---|
|**Kapcsolattartó neve** | 40 | Ez a név jelenik meg a **Súgó és támogatás** lapon. |
|**Telefonszám** | 20 | Ez a telefonszám jelenik meg a **Súgó és támogatás** lapon, hogy az alkalmazottak kapcsolatba lépjenek Önnel a támogatási szolgálattal. |
|**E-mail cím**| 40 | Ez a kapcsolattartási e-mail a **Súgó és támogatás** oldalon jelenik meg. Meg kell adnia egy érvényes e-mail-címet a következő formátumban: `alias@domainname.com`. |
|**Webhely neve**| 40 | Ez a név a támogatási webhely URL-címének rövid neveként jelenik meg. Ha a támogatási webhely URL-címét és a név nélküli nevet adja meg, akkor az IT-webhely a Céges portál **Súgó és támogatás** lapján jelenik meg. |
|**Webhely URL-címe**| 150 | Ha rendelkezik saját felhasználóinak szánt támogatási webhellyel, ide írja be az URL-címét. Az URL-cím formátumának a következőnek kell lennie: `https://www.contoso.com`. Ha nem ad meg URL-címet, semmi nem jelenik meg a támogatási webhelyhez a Céges portál **Súgó és támogatás** lapján. |
| **További információ**| 120 | Megjelenik a **Súgó és támogatás** oldalon. |


## <a name="company-identity-branding-customization"></a>Vállalati identitási arculat testreszabása
A Vállalati portál testre szabható a vállalat emblémájának és nevének, valamint a téma színének és a háttérnek a megadásával.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Témaszín és embléma a Céges portálon
Témaszínt alkalmazhat a Céges portálon. Jelöljön ki egy szabványos színt, vagy adjon meg egy hexadecimális hatjegyű kódot az egyéni színhez.

|Mező neve|További információ|
|---|---|
|**Jelöljön ki egy szabványos színt, vagy adjon meg egy hexadecimális hatjegyű kódot**| Válassza a **standard** elemet a szín kiválasztásához. Válassza az **Egyéni** lehetőséget egy hexadecimális kódon alapuló meghatározott szín kiválasztásához.|
|**Téma színének kiválasztása**| A Vállalati portálra alkalmazni kívánt témaszín kiválasztása. Választhat a színválasztóból, vagy megadhat egy hexadecimális kódot. |
|**Megjelenítés**| Válassza ki, hogy mit szeretne megjeleníteni: **Cégembléma és -név**, **Csak cégembléma** vagy **Csak cégnév**. |
|**A céges embléma feltöltése**|Feltöltheti a Céges portálon megjeleníteni kívánt vállalati emblémát. Vegye figyelembe, hogy a szöveg színének kiválasztása automatikusan történik a legnagyobb kontraszt eléréséhez. Az optimális megjelenés érdekében töltsön fel egy áttetsző hátterű emblémát.<p><ul><li>Maximális képméret: 400px x 400px</li><li>Maximális fájlméret: 750KB</li><li>Fájltípus: PNG, JPG vagy JPEG</li></ul>|

Miután feltöltötte az emblémát, az előnézeti területen meg fog jelenni az embléma a téma színével. Ha úgy dönt, hogy megjeleníti a cég nevét, az feketén vagy fehéren fog megjelenni a Céges portálon, és a téma színe alapján automatikusan a lehető legnagyobb kontraszttal fog megjelenni. A képernyő előnézeti területén nem fog megjelenni a cég neve. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Fehér vagy világos háttérrel használható embléma
Válasszon olyan emblémát, amely fehér vagy világos háttéren mutat a legjobban.

|Mező neve|További információ|
|---|---|
|**Embléma feltöltése**| Ez a lehetőség akkor érhető el, ha a céges embléma megjelenítése mellett döntött. Az optimális megjelenés érdekében töltsön fel egy áttetsző hátterű emblémát.<p><ul><li>Maximális képméret: 400px x 400px</li><li>Maximális fájlméret: 750KB</li><li>Fájltípus: PNG, JPG vagy JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Márkakép a Céges portálhoz

Márkakép feltöltése, amely tükrözi a vállalati márkát. A módosítások mentése után az Intune-webportálon a panel tetején található **Beállítások előnézetének megtekintése** lehetőséget választva megtekintheti, hogyan fog kinézni a konfigurációja. Vegye figyelembe, hogy a márkakép előnézetét csak egy iOS-eszközön lehet megtekinteni, az Intune webes portálján nem. 

|Mező neve|További információ|
|---|---|
|**Márkakép feltöltése**| Ez a beállítás lehetővé teszi a márka képének megjelenítését. Az iOS Céges portál háttérképként jelenik meg a felhasználó profiljának oldalán.<p><ul><li>Ajánlott képszélesség: nagyobb mint 1125px (legalább 650 px szükséges)</li><li>Maximális képméret: 1,3 MB</li><li>Fájltípus: PNG, JPG vagy JPEG</li></ul>|

A megfelelő márkakép javíthatja a felhasználó Céges portálba vetett bizalmát a cég márkájának hangsúlyozásával. Íme néhány tipp, amelyet érdemes figyelembe venni a kép Céges portálhoz történő beszerzésekor, kiválasztásakor és optimalizálásakor. 

- Vegye fel a kapcsolatot az értékesítési vagy művészeti osztállyal. Lehetséges, hogy már rendelkezik egy jóváhagyott márkás készlettel. Előfordulhat, hogy a képek igény szerinti optimalizálásában is tudnak segíteni. 

- Fontolja meg a fekvő és az álló tájolású kompozíciókat is. A képnek megfelelő háttérrel kell rendelkeznie, amely körülveszi a fókuszpontot. Az eszköz mérete, tájolása és platformja alapján a rendszerképet különbözőképpen lehet megtakarítani. 

- Kerülje az általános, készletben elérhető képek használatát. A képnek tükröznie kell a vállalati márkát, és ismerősnek kell tűnnie a felhasználóknak. Ha még nem rendelkezik ilyen képpel, jobb ha nem használ semmilyet, mint sem hogy olyan általános képet adjon meg, ami semmit nem jelent a felhasználóknak. 

- Szükségtelen metaadatok eltávolítása. A képfájl tartalmazhat metaadatokat, például kameraprofilt, földrajzi helyet, címet, feliratot stb. Használjon képoptimalizáló eszközt ezeknek az adatoknak az eltávolításához a minőség fájlméretkorlátok betartásával történő megőrzéséhez. 

Miután hozzáadta vagy megváltoztatta a rendszerképét az Intune-ban, előfordulhat, hogy a végfelhasználó nem látja az iOS-eszközök változását, amíg a Céges portál felismerte a rendszerindítási módosítást, majd újraindult a márka rendszerképének megjelenítéséhez. 

### <a name="brand-image-examples"></a>Példa a Brand-képekre

Az alábbi képen egy példa iPad arculatot ábrázoló rendszerkép látható:

![Képernyőkép – példa az iPhone arculati képére](./media/company-portal-app/company-portal-app-03.png)

Az alábbi képen az iPhone arculatát bemutató példa látható:

![Képernyőkép – példa iPad arculati rendszerkép](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Adatvédelmi nyilatkozat testreszabása

Testreszabhatja a szervezete számára a felügyelt iOS-eszközökön megjelenő adatvédelmi nyilatkozatot. Ez az üzenet felsorolja azokat az elemeket, amelyeket a szervezet nem láthat vagy végezhet a felügyelt iOS-eszközökön.

A **céges portál testreszabás** > **eszközkezelés és adatvédelmi üzenet**területen a következőket teheti:

- Fogadja el az **alapértelmezett értéket** a lista használatára a következő módon, vagy
- Az **Egyéni** elem kiválasztásával testreszabhatja azon elemek listáját, amelyeket a szervezet nem láthat vagy végezhet a felügyelt iOS-eszközökön. A [Markdown](https://daringfireball.net/projects/markdown/) használatával felsorolásjeleket, félkövéreket, dőlteket és hivatkozásokat adhat hozzá.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Céges portál származtatott hitelesítő adatok iOS-eszközökhöz
Az Intune támogatja a személyes személyazonosság-ellenőrzés (PIV) és a Common Access Card (CAC) származtatott hitelesítő adatait a DISA fajtiszta, a Entrust Datacard és a közbenjáró hitelesítő adatokkal. A végfelhasználók az iOS-eszköz regisztrálását követően további lépéseket hajtanak végre az identitásuk ellenőrzéséhez a Céges portál alkalmazásban. A származtatott hitelesítő adatok lehetővé teszik a felhasználók számára, hogy először állítanak be egy hitelesítő adatot a bérlő számára, majd egy olyan profilt céloznak meg, amely származtatott hitelesítő adatokat használ a felhasználóknak vagy az eszközöknek.

> [!NOTE]
> A felhasználó az Intune-on keresztül megadott hivatkozás alapján a származtatott hitelesítő adatokra vonatkozó utasításokat fogja látni.

Az iOS-eszközök származtatott hitelesítő adataival kapcsolatos további információkért lásd: [származtatott hitelesítő adatok használata Microsoft Intuneban](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Sötét mód iOS-Céges portál

A sötét mód elérhető az iOS-Céges portál számára. A felhasználók letölthetik a vállalati alkalmazásokat, kezelhetik az eszközeiket, és az eszköz beállításai alapján választhatják ki a kívánt színsémát. Az iOS-Céges portál automatikusan meg fogja egyezni a végfelhasználói eszközbeállítások sötét vagy világos módban. 

## <a name="windows-company-portal-keyboard-shortcuts"></a>A Windows Céges portálon használható billentyűparancsok

A végfelhasználók a billentyűparancsok (gyorssegédek) használatával indíthatnak navigációs, alkalmazás-és eszköz-műveleteket a Windows Céges portálban.

A következő billentyűparancsok érhetők el a Windows Céges portál alkalmazásban.

| Terület | Leírás | Billentyűparancs |
|:------------------:|:--------------:|:-----------------:|
| Navigációs menü | Navigációs | Alt+M |
|  | Otthoni | Alt+H |
|  | Minden alkalmazás | Alt+A |
|  | Telepített alkalmazások | Alt+I |
|  | Visszajelzés küldése | Alt+F |
|  | Saját profil | Alt+U |
|  | Beállítások | Alt+T |
| Kezdőlap – Eszköz csempe | Átnevezés | F2 |
|  | Eltávolítás | Ctrl+D vagy Delete |
|  | Hozzáférés ellenőrzése | Ctrl+M vagy F9 |
| Eszközadatok | Átnevezés | F2 |
|  | Eltávolítás | Ctrl+D vagy Delete |
|  | Hozzáférés ellenőrzése | Ctrl+M vagy F9 |
| Alkalmazás részletei | Telepítés | Ctrl+I |
| Eszközök | Elérhető | CTRL + D |

A végfelhasználók az elérhető parancsikonokat is láthatják a Windows Céges portál alkalmazásban.

![Képernyőkép a Windows Céges portál elérhető parancsikonjairól](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>A felhasználó önkiszolgáló eszközének műveletei a Céges portál

A felhasználók a helyi vagy távoli eszközökön végezhetnek műveleteket a Céges portál alkalmazás vagy webhely használatával. A felhasználók által elvégezhető műveletek az eszköz platformján és konfigurációjától függően változhatnak. A távoli eszközök műveleteit minden esetben csak az eszköz elsődleges felhasználója hajthatja végre.
- **Kivonás – eltávolítja** az eszközt az Intune-felügyeletből. A céges portál alkalmazásban és webhelyen az **Eltávolítás**elem jelenik meg.
- **Törlés** – ez a művelet elindítja az eszköz alaphelyzetbe állítását. A céges portál webhelyen ez a beállítás **alaphelyzetbe állításként**jelenik meg, vagy a **gyári beállítások visszaállítása** az iOS céges portál alkalmazásban.
- **Átnevezés** – ez a művelet megváltoztatja azt az eszköznév, amelyet a felhasználó láthat a céges portálban. Nem módosítja a helyi eszköznév nevét, csak a Céges portál lévő listaelemet.
- **Sync (szinkronizálás** ) – Ez a művelet az Intune szolgáltatással kezdeményezi az eszköz beadását. Ez a Céges portál **ellenőrzési állapotaként** jelenik meg.
- **Távoli zárolás** – ezzel zárolja az eszközt, és PIN-kódot igényel a zárolás feloldásához.
- Jelszó **alaphelyzetbe állítása** – ezzel a művelettel alaphelyzetbe állíthatja az eszköz PIN-kódját. IOS-eszközökön a PIN-kód el lesz távolítva, és a végfelhasználónak új kódot kell megadnia a beállításokban. A támogatott androidos eszközökön új PIN-kódot hoz létre az Intune, és ideiglenesen megjelenik a Céges portál.
- **Kulcs helyreállítása** – ezzel a művelettel helyreállíthatja a titkosított MacOS-eszközök személyes helyreállítási kulcsát a céges portál webhelyről. 

### <a name="self-service-actions"></a>Önkiszolgáló műveletek

Egyes platformok és konfigurációk nem engedélyezik az önkiszolgáló eszközök műveleteit. Az alábbi táblázat további részleteket tartalmaz az önkiszolgáló műveletekről:

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Kivonás | Elérhető<sup>(1)</sup> | Elérhető | Elérhető | Elérhető<sup>(7)</sup> |
| Törlés | Elérhető | Elérhető<sup>(5)</sup> | NA | Elérhető<sup>(7)</sup> |
| Átnevezés<sup>(4)</sup> | Elérhető | Elérhető | Elérhető | Elérhető |
| Sync | Elérhető | Elérhető | Elérhető | Elérhető |
| Távoli zárolás | Csak Windows Phone-telefon | Elérhető | Elérhető | Elérhető |
| Jelszó alaphelyzetbe állítása | Csak Windows Phone-telefon | Elérhető<sup>(8)</sup> | NA | Elérhető<sup>(6)</sup> |
| Kulcshelyreállítás | NA | NA | Elérhető<sup>(2)</sup> | NA |

<sup>(1)</sup> a kivonás mindig **le van tiltva az Azure** ad-hez csatlakoztatott Windows-eszközökön.<br>
<sup>(2)</sup> a MacOS rendszerhez készült **kulcs-helyreállítás** csak a webes portálon keresztül érhető el.<br>
<sup>(3)</sup> az összes távoli művelet le van tiltva, ha egy eszköz beléptetési kezelőt használ.<br>
<sup>(4)</sup> az **Átnevezés** csak az eszköz nevét módosítja a céges portál alkalmazásban vagy a webes portálon, nem az eszközön.<br>
<sup>(5)</sup> a **Törlés** nem érhető el a felhasználó által regisztrált iOS-eszközökön.<br>
<sup>(6)</sup> a **PIN-kód alaphelyzetbe állítása** néhány Android-és androidos vállalati konfiguráció esetében nem támogatott. További információkért lásd: [eszköz PIN-kód alaphelyzetbe állítása vagy eltávolítása az Intune-ban](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> a kivonás **és a** **Törlés** nem érhető el az androidos vállalati eszközök tulajdonosi forgatókönyvei esetében (Cope, COBO, COSU).<br>a <sup>(z)  
(8)</sup> jelszó **alaphelyzetbe állítása** nem támogatott a felhasználó által regisztrált iOS-eszközökön.

## <a name="next-steps"></a>További lépések

- [A Windows 10-es céges portál alkalmazás manuális hozzáadása a Microsoft Intune-nal](company-portal-app.md)
