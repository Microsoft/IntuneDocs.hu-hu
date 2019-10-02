---
title: Alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Információ arról, hogyan lehet a Microsoft Intune-hoz alkalmazásokat hozzáadni, majd az alkalmazásokat felhasználókhoz és eszközökhöz rendelni. Az Intune sokféle alkalmazástípust támogat.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40bb96000513bb1de09ec8f8865735d70bddcd43
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731267"
---
# <a name="add-apps-to-microsoft-intune"></a>Alkalmazások hozzáadása a Microsoft Intune-hoz 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazások hozzárendelése, figyelése, konfigurálása és védelme előtt hozzá kell adnia őket a Microsoft Intune-hoz.

Az alkalmazások és eszközök céges felhasználói (a munkaerő) több alkalmazáskövetelménnyel rendelkezhetnek. Mielőtt alkalmazásokat adna hozzá az Intune-hoz, ezzel elérhetővé téve azokat a munkaerő számára, célszerű felmérnie és megértenie néhány alkalmazásokkal kapcsolatos alapvetést. Ismernie kell az Intune-ban elérhető különböző alkalmazástípusokat. Fel kell mérnie az alkalmazáskövetelményeket, így a munkaerő számára szükséges platformokat és funkciókat. Meg kell határoznia, hogy az Intune-nal kezeli-e az eszközöket (és azok alkalmazásait), vagy az Intune-nal kezeli az alkalmazásokat, az eszközöket azonban nem. Végül meg kell határoznia a munkaerő által igényelt alkalmazásokat és funkciókat és azt, hogy ezekre kiknek van szükségük. Ez a cikk segíthet az első lépések megtételében.

## <a name="app-types-in-microsoft-intune"></a>Alkalmazástípusok a Microsoft Intune-ban

Az Intune sokféle alkalmazástípust támogat. Az elérhető beállítások minden alkalmazástípus esetében eltérőek. Az Intune a következő típusú alkalmazások hozzáadását és hozzárendelését teszi lehetővé:

| Alkalmazástípusok | Telepítés | Frissítések |
|---|---|---|
| Áruházbeli alkalmazások | Az Intune telepíti az alkalmazást az eszközön.  | Az alkalmazások frissítése automatikus. |
| Belső fejlesztésű (üzletági) alkalmazások | Az Intune telepíti az alkalmazást az eszközön (a telepítőfájlt Önnek kell letöltenie). | Az alkalmazást Önnek kell frissítenie. |
| Beépített alkalmazások | Az Intune telepíti az alkalmazást az eszközön.  | Az alkalmazások frissítése automatikus. |
| Alkalmazások a weben (webes hivatkozás) | Az Intune létrehoz egy parancsikont a webalkalmazáshoz az eszköz kezdőképernyőjén. | Az alkalmazások frissítése automatikus. |

### <a name="specific-app-type-details"></a>Alkalmazástípusok konkrét részletei
 
A következő táblázatban megtekintheti a konkrét alkalmazástípusokat és azok hozzáadásának módját az Intune **Alkalmazás hozzáadása** panelén:

| **Alkalmazásspecifikus típus** | **Általános típus** | **Alkalmazásspecifikus eljárások** |
| --- | --- | --- |
| Androidos áruházbeli alkalmazások  | Áruházbeli alkalmazás  | Válassza az **Android** lehetőséget az **alkalmazás típusa** területen, majd adja meg a Google Play áruház alkalmazáshoz tartozó URL-címét. |
| Androidos vállalati alkalmazások  | Áruházbeli alkalmazás  | Válassza az **Android** lehetőséget az **alkalmazás típusa**területen, majd adja meg az alkalmazás felügyelt Google Play áruházbeli URL-címét. <sup>1</sup> |
| iOS-es áruházbeli alkalmazások  | Áruházbeli alkalmazás  | Válassza az **iOS** lehetőséget az **alkalmazás típusa** területen, keresse meg az alkalmazást majd jelölje ki az Intune-ban. |
| Windows Phone 8.1-es áruházbeli alkalmazások  | Áruházbeli alkalmazás  | Válassza a **Windows Phone 8.1** lehetőséget az **alkalmazás típusa** területen, majd adja meg a Microsoft Store alkalmazáshoz tartozó URL-címét. |
| Microsoft Store-beli alkalmazások  | Áruházbeli alkalmazás  | Válassza a **Windows** lehetőséget az **alkalmazás típusa** területen, majd adja meg a Microsoft Store alkalmazáshoz tartozó URL-címét. |
| Felügyelt Google Play-alkalmazások | Áruházbeli alkalmazás  | Válassza a **felügyelt Google Play** lehetőséget az **alkalmazás típusa**területen, keresse meg az alkalmazást, és válassza ki az alkalmazást az Intune-ban. |
| Windows 10-es Office 365-alkalmazások  | Áruházbeli alkalmazás (Office 365) | Válassza a **Windows 10** lehetőséget az **Office 365 csomag** területen, az **alkalmazás típusa** részen, majd válassza ki a telepíteni kívánt Office 365-alkalmazást.  |
| macOS-es Office 365-alkalmazások | Áruházbeli alkalmazás (Office 365) | Válassza a **macOS** lehetőséget az **Office 365 csomag** területen, az **alkalmazás típusa** részen, majd válassza ki az Office 365 csomagot. |
| Androidos üzletági (LOB) alkalmazások | Üzletági (LOB) alkalmazás | Válassza az **Üzletági alkalmazás** lehetőséget az **alkalmazás típusa** területen, válassza az **Alkalmazáscsomag-fájl** elemet, majd adjon meg egy **.apk** kiterjesztésű Androidos telepítőfájlt.  |
| iOS-es üzletági alkalmazások | Üzletági (LOB) alkalmazás | Válassza az **Üzletági alkalmazás** lehetőséget az **alkalmazás típusa** területen, válassza az **Alkalmazáscsomag-fájl** elemet, majd adjon meg egy **.ipa** kiterjesztésű iOS-es telepítőfájlt.  |
| Windows Phone LOB-alkalmazások | Üzletági (LOB) alkalmazás | Válassza az **Üzletági alkalmazás** lehetőséget az **alkalmazás típusa** területen, válassza az **Alkalmazáscsomag-fájl** elemet, majd adjon meg egy **.xap** kiterjesztésű Windows Phone-telepítőfájlt.  |
| Windows LOB apps | Üzletági (LOB) alkalmazás | Válassza az **Üzletági alkalmazás** lehetőséget az alkalmazás típusa területen, válassza az **Alkalmazáscsomag-fájl** elemet, majd adjon meg egy **.msi**, **.appx**, **.appxbundle**, **.msix** vagy **.msixbundle** kiterjesztésű Windows-telepítőfájlt. |
| Beépített iOS-alkalmazás  | Beépített alkalmazás | Válassza a **Beépített alkalmazás** lehetőséget az **alkalmazás típusa** területen, majd jelöljön ki egy beépített alkalmazást az elérhető alkalmazások listáján.  |
| Beépített Android-alkalmazás  | Beépített alkalmazás | Válassza a **Beépített alkalmazás** lehetőséget az **alkalmazás típusa** területen, majd jelöljön ki egy beépített alkalmazást az elérhető alkalmazások listáján.  |
| Webalkalmazások  | Web app  | Válassza a **Webes hivatkozás** lehetőséget az **alkalmazás típusa** területen, majd adjon meg egy érvényes, a webalkalmazásra mutató URL-címet.  |
| A Vállalati Android rendszeralkalmazásai  | Áruházbeli alkalmazás  | Válassza az **Android Enterprise System app** elemet az **alkalmazás típusa**területen, majd adja meg az alkalmazás nevét, közzétevőjét és csomagfájl.  |
| Windows-alkalmazás (Win32)  | Üzletági (LOB) alkalmazás  | Válassza a **Windows-alkalmazás (Win32)** lehetőséget az **alkalmazás típusa** területen, válassza az **Alkalmazáscsomag-fájl** elemet, majd válasszon egy **.intunewin** kiterjesztésű telepítőfájlt.  |
| macOS-es üzletági alkalmazások | Üzletági (LOB) alkalmazás  | Válassza az **üzletági** lehetőséget az **alkalmazás típusa**területen, válassza ki az **alkalmazáscsomag-fájlt**, majd válassza ki a **. intunemac**kiterjesztésű telepítési fájlt.  |


<sup>1</sup> az Android Enterprise és Android rendszerű munkahelyi profilokkal kapcsolatos további információkért lásd az alábbi [licencelt alkalmazások ismertetése](apps-add.md#understanding-licensed-apps) című témakört.

Az alkalmazásokat az **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** lehetőséggel adhatja hozzá a Microsoft Intune-hoz. Megjelenik az **Alkalmazás hozzáadása** panel, ahol kiválaszthatja az **alkalmazás típusát**. 

>[!TIP]
> Az üzletági (LOB) alkalmazásokat egy alkalmazástelepítő fájlból adja hozzá. Egy iOS LOB-alkalmazás telepítéséhez például az **Alkalmazás hozzáadása** panel **Alkalmazás típusa** részén az **Üzletági alkalmazás** beállítás megadásával adhatja hozzá az alkalmazást. Ezután válassza ki az alkalmazáscsomag (.ipa kiterjesztésű) fájlját. Az ilyen típusú alkalmazások általában belső fejlesztésűek.

## <a name="assess-app-requirements"></a>Alkalmazáskövetelmények értékelése
Rendszergazdaként nem csak azt kell meghatároznia, hogy mely alkalmazásokra lesz szüksége a csapatának, hanem azt is, hogy az egyes csoportoknak és alcsoportoknak milyen funkciókra lesz szükségük. Minden alkalmazáshoz meg kell határoznia a szükséges platformokat, az alkalmazásra igényt tartó felhasználói csoportokat, a csoportokra alkalmazandó konfigurációs szabályzatokat és az alkalmazandó védelmi szabályzatokat.  

Emellett meg kell határoznia, hogy szükséges-e a mobileszköz-kezeléssel (MDM) foglalkoznia, vagy elegendő a mobilalkalmazás-kezelés (MAM). 

Az Intune-nal történő eszközkezelés (MDM) a következő esetekben hasznos:
- A felhasználóknak vállalati Wi-Fi- vagy VPN-csatlakozási profilra van szükségük a produktív munkához.
- A felhasználóknak egy, az eszközükre leküldött alkalmazáscsomagra van szükségük.
- A szervezetének meg kell felelnie azoknak a szabályozási és más szabályzatoknak, amelyek konkrét mobileszköz-kezelési előírások, például biztonságra vagy titkosításra vonatkozó előírások betartását követelik meg.

Az Intune-nal történő alkalmazáskezelés (MAM) az eszköz kezelése nélkül a következő esetekben hasznos:
- A felhasználók használhatják a saját eszközeiket (BYOD).
- A folyamatos eszközszintű értesítések helyett egy egyszeri felugró üzenettel szeretné tudatni a felhasználókkal, hogy életbe lépett a MAM-védelem.
- Olyan szabályzatoknak kell megfelelnie, amelyek alacsonyabb fokú felügyeleti képességeket írnak elő a személyes eszközökhöz. Például az alkalmazások céges adatait szeretné kezelni, nem az eszközön található minden céges adatot.

További információ: [Az MDM és az MAM összehasonlítása](../fundamentals/byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Az alkalmazás használóinak meghatározása

A munkaerő számára szükséges alkalmazások meghatározása során vegye figyelembe a különböző felhasználói csoportokat és az általuk használt alkalmazásokat. A csoportok ismerete az alkalmazások hozzáadása után is hasznos. Miután hozzáadta az alkalmazást, hozzárendelhet egy felhasználói csoportot, akik használhatják azt. 

Elsőként az alkalmazás adatainak bizalmassági szintje alapján meg kell határoznia, hogy ki tartozzon az alkalmazáshoz hozzáférők csoportjába. Előfordulhat, hogy bizonyos szerepköröket ki kell zárnia a hozzáférésből. Például előfordulhat, hogy az értékesítési csoportnak csak bizonyos LOB-alkalmazásokra van szüksége, míg a mérnöki, a pénzügyi, a HR vagy a jogi osztálynak nincs szüksége ezekre. Emellett előfordulhat, hogy az értékesítési csoportnak további adatvédelemre, valamint a belső vállalati szolgáltatások elérésére van szüksége a mobileszközein. Önnek kell meghatároznia, hogy hogyan csatlakozhat az adott csoport az erőforrásokhoz az alkalmazás használatával. Az alkalmazással elért adatok a felhőben vagy a helyszínen legyenek tárolva? Hogyan csatlakozhatnak a felhasználók az erőforrásokhoz az alkalmazással? 

Az Intune támogatja az olyan ügyfélalkalmazások hozzáférésének biztosítását is, amelyek biztonságos hozzáférést igényelnek a helyszíni adatokhoz, mint például az üzleti alkalmazások kiszolgálói. Ez a hozzáféréstípus általában a hozzáférés [Intune által kezelt tanúsítványokkal](../protect/certificates-configure.md) történő szabályozásával, valamint a szegélyhálózatban található szabványos VPN-átjáróval vagy proxyval, például a Azure Active Directory-alkalmazásproxyval oldható meg. Az Intune [alkalmazásburkoló eszközével és az App SDK-val](../developer/apps-prepare-mobile-application-management.md) az elért adatok az üzleti alkalmazáson belül tarthatók, hogy az alkalmazás ne tudja átadni a vállalati adatokat a fogyasztói alkalmazásoknak vagy szolgáltatásoknak.

Az [Intune az üzembe helyezésének tervezésével, kialakításával és kivitelezésével](../fundamentals/planning-guide.md) meghatározhatja, hogy hogyan azonosíthatja az egyes alkalmazáshasználati esetekhez és alesetekhez tartozó szervezeti csoportokat. További információ az alkalmazások csoportokhoz rendeléséről: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](apps-deploy.md).

### <a name="determine-the-type-of-app-for-your-solution"></a>A saját megoldáshoz tartozó alkalmazás meghatározása

Az alábbi alkalmazástípusok közül választhat:
- **Az áruházból származó alkalmazások**: A Microsoft áruházba, az iOS-tárolóba vagy az Android áruházba feltöltött alkalmazások áruházbeli alkalmazások. Az áruházbeli alkalmazásokat a szolgáltatójuk tartja karban és frissíti. Az áruház listájából Ön választja ki az alkalmazást, és teszi elérhetővé a felhasználói számára az Intune segítségével.
- **Házon belül írt alkalmazások (üzletági)** : A házon belül létrehozott alkalmazások üzletági (LOB) alkalmazások. Az ilyen típusú alkalmazások funkciói az Intune által támogatott platformok (például Windows, iOS, macOS vagy Android) egyikére lettek létrehozva. A cége egy külön fájlként hozza létre és teszi elérhetővé Ön számára a frissítéseket. Az alkalmazás frissítéseit a felhasználók számára az Intune-nal teheti elérhetővé.
- **Webes alkalmazások**: A webalkalmazások ügyfél-kiszolgáló alkalmazások. A kiszolgáló szolgáltatja a webalkalmazást, amely tartalmazza a felhasználói felületet, a tartalmat és a funkciókat. A modern webszolgáltatási platformok emellett gyakran kínálnak biztonsági, terheléselosztási és egyéb szolgáltatásokat. Az ilyen típusú alkalmazásokat külön, a weben kezelik. Ehhez az alkalmazástípushoz az Intune-t kell használnia. Azt is Ön dönti el, hogy mely felhasználói csoportok férhetnek hozzá ezekhez az alkalmazásokhoz. Vegye figyelembe, hogy az Android nem támogatja a webalkalmazásokat.

A szervezet alkalmazásigényének felmérésekor vegye figyelembe, hogy ezek az alkalmazások hogyan integrálhatók felhőszolgáltatásokkal, milyen adatokhoz férhetnek hozzá, elérhetők-e BYOD-felhasználók számára, valamint szükség van-e hozzájuk internet-hozzáférésre.

A cégnél használni kívánt alkalmazástípusokról a [Terv létrehozása](../fundamentals/planning-guide-design.md#feature-requirements) terület „Funkciókövetelmények” szakaszának „Alkalmazások” részén találhat bővebb információt.

### <a name="understanding-app-management-and-protection-policies"></a>Az alkalmazáskezelési és -védelmi szabályzatok megértése
Az Intune-nal módosíthatja a telepített alkalmazások funkcióit, hogy azok összhangban legyenek a vállalat megfelelőségi és biztonsági szabályzataival. Ennek köszönhetően megadhatja, hogyan legyenek védve a céges adatok. Az Intune által kezelt alkalmazások széles körű mobilalkalmazás-védelmi szabályzatokkal rendelkeznek, például:

- A másolás és beillesztés, valamint a mentés másként funkció korlátozása.
- A webes hivatkozások konfigurálása, hogy azok az Intune Managed Browser alkalmazásban nyíljanak meg.
- A többszörös identitás használatának és az alkalmazás szintű feltételes hozzáférésének engedélyezése.

Az Intune által kezelt alkalmazások regisztráció nélkül nyújtanak alkalmazásvédelmet, így Ön a felhasználói eszköz kezelése nélkül alkalmazhat adatveszteség-megelőzési szabályzatokat. Emellett az Intune alkalmazás szoftverfejlesztői készletével (SDK) és alkalmazásburkoló eszközével beépítheti a mobilalkalmazás-kezelést az üzletági és mobilalkalmazásaiba. További információ ezekről az eszközökről: [Az Intune App SDK áttekintése](../developer/app-sdk.md).

### <a name="understanding-licensed-apps"></a>A licencelt alkalmazások megértése
A webes, az áruházbeli és az üzletági alkalmazásokon kívül érdemes tisztában lennie a Volume Purchase Program alkalmazásainak és a licencelt alkalmazások sajátosságaival, például: 
- **Apple Volume vásárlási program for Business (iOS)** : Az iOS App Store áruház lehetővé teszi, hogy több licencet vásároljon a vállalatnál futtatni kívánt alkalmazásokhoz. Több licenc vásárlásával hatékonyabban kezelhetők a vállalaton belüli alkalmazások. További információ: [Mennyiségi programban vásárolt iOS-alkalmazások felügyelete](vpp-apps-ios.md).
- **Androidos munkahelyi profil**: Az alkalmazások androidos munkahelyi profilos eszközökhöz való hozzárendelése eltér a hagyományos androidos eszközökhöz való hozzárendeléstől. Minden olyan alkalmazás, amelyet az androidos munkahelyi profil részeként telepít a felügyelt Google Play áruházból szerezhető be. Az Intune használatával megkeresheti a kívánt alkalmazásokat, és jóváhagyhatja azokat. Az alkalmazás megjelenik az Azure Portal **Licencelt alkalmazások** lapján, és a hozzárendelése ugyanúgy kezelhető, mint bármely más alkalmazásé.
- **Üzleti Microsoft Store (Windows 10)** : A Microsoft Store for Business lehetővé teszi, hogy megkeresse és megvásárolja a szervezete alkalmazásait egyénileg vagy köteten. Az áruházat a Microsoft Intune-nal összekapcsolva a mennyiségi programban vásárolt alkalmazásokat az Azure Portalon kezelheti. További információ: [A Microsoft Store Vállalatoknak áruházban vásárolt alkalmazások felügyelete](windows-store-for-business.md).

    > [!NOTE]
    > A windowsos alkalmazások fájlnévkiterjesztései közé tartozik az **.msi**, **.appx**, **.appxbundle**, **.msix** és **.msixbundle** is.  

## <a name="before-you-add-apps"></a>Mielőtt hozzáadna alkalmazásokat
Mielőtt elkezdené az alkalmazások hozzáadását és hozzárendelését, vegye figyelembe a következőket:

- Ha áruházból végzi az alkalmazások felvételét és hozzárendelését, a felhasználók csak akkor tudják telepíteni az alkalmazásokat, ha rendelkeznek fiókkal az adott áruházban.
- Előfordulhat, hogy egyes hozzárendelendő alkalmazások beépített iOS-alkalmazásoktól függenek. Ha például egy könyv iOS-es áruházból való hozzárendelését végzi, az eszközön elérhetőnek kell lennie az iBooks alkalmazásnak. Ha eltávolította a beépített iBooks alkalmazást, azt az Intune használatával nem tudja újratelepíteni.

> [!IMPORTANT]
> Ha az alkalmazás telepítését követően módosítja annak nevét az Intune Azure Portalon, az alkalmazást nem fogják megtalálni a parancsok.

## <a name="cloud-storage-space"></a>Felhőtárhely
A szoftvertelepítő típusú telepítéssel létrehozott összes alkalmazást (például az üzletági alkalmazásokat) a rendszer becsomagolja és feltölti az Intune felhőtárhelyére. Az Intune próba-előfizetése 2 gigabájtnyi (GB) felhőtárhelyet biztosít a felügyelt alkalmazások és frissítések tárolásához. A teljes előfizetések nem korlátozzák a tárhely maximális mennyiségét.

A felhőtárhelyre vonatkozó követelmények az alábbiak:

- Az összes alkalmazás telepítési fájljainak ugyanabban a mappában kell lenniük.
- A feltöltött fájlok legfeljebb 8 GB méretűek lehetnek.

  > [!NOTE]
  > A Windows rendszerű üzletági (LOB) alkalmazások esetében az alkalmazás legfeljebb 8 GB méretű lehet. az iOS LOB-alkalmazások esetében az alkalmazás legfeljebb 4 GB méretű lehet.

## <a name="create-and-edit-categories-for-apps"></a>Alkalmazáskategóriák létrehozása és szerkesztése

Az alkalmazáskategóriák segítségével úgy rendezheti az alkalmazásokat, hogy a felhasználók könnyebben találják meg őket a céges portálon. Egy alkalmazáshoz több kategóriát is hozzárendelhet (például *Fejlesztői alkalmazások* és *Kommunikációs alkalmazások*).

Amikor hozzáad egy alkalmazást az Intune-hoz, kiválaszthatja a kívánt kategóriát. Az alkalmazások felvételéről és a kategóriák hozzárendeléséről az egyes platformokra vonatkozó témakörökből tájékozódhat. Saját kategóriáit a következő eljárással hozhatja létre és szerkesztheti:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** területen a **Beállítások** alatt válassza az **Alkalmazáskategóriák** lehetőséget.  
    Az **Alkalmazáskategóriák** panel megjeleníti az aktuális kategóriák listáját. 
5. A következő lehetőségek közül választhat:
    - Új kategória megadásához válassza a **Kategória létrehozása** panel **Hozzáadás** elemét, majd adja meg a kategória nevét.  
    A neveket csak egy nyelven lehet megadni, és az Intune nem fordítja le őket.
    - Kategória szerkesztéséhez válassza a kategória melletti három pontot ( **...** ) majd a **Rögzítés irányítópulton** vagy **Törlés** lehetőséget.
6. Kattintson a **Létrehozás** gombra.

## <a name="apps-that-are-added-automatically-by-intune"></a>Az Intune által automatikusan hozzáadott alkalmazások

Korábban az Intune számos beépített alkalmazást tartalmazott, melyeket hamar hozzá lehetett rendelni egy kategóriához. Ezt a listát az Intune-ügyfelek visszajelzései alapján eltávolítottuk, és a beépített alkalmazások többé nem jelennek meg. A korábban már hozzárendelt beépített alkalmazások azonban továbbra is megjelennek az alkalmazások listájában. Az alkalmazások szükség szerint továbbra is hozzárendelhetők.

> [!NOTE]
> Kötelező nem üzletági alkalmazás telepítéséhez az Intune telepítési parancsot küld az eszköz bejelentkezésekor, feltéve hogy az alkalmazás nem észlelhető és az alkalmazás telepítési állapota nem *Telepítés függőben*.

## <a name="installing-updating-or-removing-required-apps"></a>Kötelező alkalmazások telepítése, frissítése, vagy eltávolítása

A kötelező alkalmazásokat az Intune a 7 napos újraértékelési ciklus kivárása helyett 24 órán belül automatikusan újratelepíti, frissíti, vagy eltávolítja.

Az Intune a kötelező alkalmazásokat a következő feltételek alapján telepíti újra, frissíti, vagy távolítja el automatikusan:
- Ha a végfelhasználó eltávolít egy olyan alkalmazást, amelyet az eszközre kötelezően telepített alkalmazásnak jelöltek, akkor az Intune az ütemezett időpontban automatikusan újratelepíti az adott alkalmazást.
- Ha a kötelező alkalmazás telepítése sikertelen, vagy valamiért az alkalmazás nincs jelen az eszközön, az Intune ellenőrzi a megfelelőséget, és az ütemezett időpontban újratelepíti az alkalmazást.  
- Az egyik rendszergazda elérhetővé tesz egy alkalmazást egy felhasználói csoport számára, és a felhasználó telepíti ezt az alkalmazást az eszközre a céges portál használatával. Később a rendszergazda frissíti az alkalmazást v1-es verzióról v2-re. Amennyiben az alkalmazás korábbi verziója jelen van az eszközön, az Intune az ütemezett időpontban frissíteni fogja az alkalmazást.
- Ha a rendszergazda az alkalmazást törlésre jelöli ki, és az alkalmazás továbbra is jelen van a készüléken és eltávolítása sikertelen volt, az Intune ellenőrzi a megfelelőséget, és eltávolítja az alkalmazást az ütemezett időpontban.   

## <a name="app-installation-errors"></a>Alkalmazástelepítési hibák

Az Intune alkalmazástelepítési hibáival kapcsolatos további információkért lásd: [Alkalmazástelepítési hibák](troubleshoot-app-install.md#app-installation-errors).

## <a name="next-steps"></a>További lépések

Az alkalmazások Intune-hoz adásáról a különböző platformokon az alábbi cikkek adnak útmutatást:

- [Androidos áruházbeli alkalmazások](store-apps-android.md)
- [Androidos üzletági alkalmazások](lob-apps-android.md)
- [iOS rendszerhez készült áruházbeli alkalmazások](store-apps-ios.md)
- [iOS-es üzletági alkalmazások](lob-apps-ios.md)
- [macOS LOB-alkalmazások](lob-apps-macos.md)
- [Webalkalmazások (az összes platformra)](web-app.md)
- [Windows Phone 8.1-es áruházbeli alkalmazások](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB-alkalmazások](lob-apps-windows-phone.md)
- [Microsoft Áruházbeli alkalmazások](store-apps-windows.md)
- [Windows LOB-alkalmazás](lob-apps-windows.md)
- [Windows 10-es Office 365-alkalmazások](apps-add-office365.md)
- [macOS-es Office 365-alkalmazások](apps-add-office365-macos.md)
- [Beépített alkalmazások](apps-add-built-in.md)
- [Android Enterprise System-alkalmazás](apps-ae-system.md)
- [Win32-alkalmazások](app-management.md)
