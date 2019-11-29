---
title: Office 365-alkalmazások hozzáadása Windows 10-es eszközökhöz Microsoft Intune használatával
titleSuffix: ''
description: Útmutató az Office 365-alkalmazások Windows 10-es eszközökön való telepítéséhez a Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73848ee8301362f14fe2866a57329425d5e5cfbe
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563665"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Office 365-alkalmazások hozzáadása a Windows 10-es eszközökhöz Microsoft Intune

Az alkalmazások hozzárendelése, figyelése, konfigurálása és védelme előtt hozzá kell adnia őket az Intune-hoz. Az elérhető [alkalmazások](apps-add.md#app-types-in-microsoft-intune) egyike az Office 365 alkalmazások Windows 10-es eszközökhöz. Ha ezt az alkalmazást az Intune-ban kiválasztja, az Office 365-alkalmazásokat hozzárendelheti és telepítheti a Windows 10 rendszert futtató eszközökre. Az alkalmazásokat a Microsoft Project online asztali ügyfeléhez és a Microsoft Visio online 2. csomaghoz is hozzárendelheti és telepítheti, ha Ön rendelkezik saját licencekkel. Az elérhető Office 365-alkalmazások egyetlen bejegyzésként jelennek meg az Azure-beli Intune-konzolon az alkalmazások listájában.

> [!NOTE]
> Office 365 ProPlus-licencekkel kell aktiválnia a Microsoft Intune-on keresztül üzembe helyezett Office 365 ProPlus-alkalmazásokat. Jelenleg az Intune nem támogatja az Office 365 Business Edition kiadását.

## <a name="before-you-start"></a>Előkészületek

> [!IMPORTANT]
> Ha a végfelhasználói eszközön .msi Office-alkalmazások találhatók, azokat az **MSI eltávolítása** szolgáltatással biztonságosan el kell távolítani. Ellenkező esetben az Intune által biztosított Office 365-alkalmazások telepítése sikertelen lesz.

- Azokon az eszközökön, melyekre telepíti az alkalmazásokat, a Windows 10 alkotói frissítésének vagy újabb verziójának kell futnia.
- Az Intune csak az Office 365 csomagból származó Office-alkalmazások hozzáadását támogatja.
- Ha bármely Office-alkalmazás meg van nyitva, amikor az Intune telepíti az alkalmazáscsomagot, előfordulhat, hogy a telepítés sikertelen lesz, és elvesznek a végfelhasználók adatai a nem mentett fájlokból.
- Ez a telepítési módszer nem támogatott Windows Home, Windows Team, Windows holografikus vagy Windows holografikus for Business rendszerű eszközökön.
- Az Intune nem támogatja az asztali Office 365-programok (más néven az Office Centennial-alkalmazások) Microsoft Áruházból történő telepítését olyan eszközök esetében, amelyekre korábban már telepítettek valamilyen Office 365-alkalmazást az Intune segítségével. Ha ezt a konfigurációt telepíti, az adatvesztést vagy adatsérülést okozhat.
- Több kötelező vagy elérhető alkalmazás-hozzárendelés nem adódik össze. A későbbi alkalmazás-hozzárendelés felülírja a már meglévő alkalmazás-hozzárendeléseket. Ha például az első Office-alkalmazáscsomag tartalmazta a Wordöt, de az újabb már nem, akkor a Word el lesz távolítva. Ez a feltétel a Visio- és Project-alkalmazásokra nem vonatkozik.
- Több Office 365 üzemelő példány jelenleg nem támogatott. Csak egy központi telepítés lesz továbbítva az eszközre
- **Office-verzió**: - Itt választhatja ki, hogy az Office 32 bites vagy 64 bites verzióját szeretné hozzárendelni. A 32 bites verziót 32 bites és 64 bites eszközökön is, a 64 bites verziót viszont csak 64 bites eszközökön telepítheti.
- **MSI eltávolítása a végfelhasználói eszközökről** – Itt választhatja ki, hogy eltávolítja-e a már meglévő Office .MSI-alkalmazásokat a végfelhasználói eszközökről. A telepítés nem lesz sikeres, ha a végfelhasználói eszközökön már meglévő .MSI-alkalmazások vannak. Az eltávolítás nem korlátozódik az **Alkalmazáscsomag konfigurálásánál** telepítésre kiválasztott alkalmazásokra, mert minden Office (MSI) alkalmazást eltávolít a végfelhasználói eszközről. További információkért lásd: [Az Office már meglévő MSI-verzióinak eltávolítása az Office 365 ProPlusra való frissítés esetén](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Amikor az Intune újratelepíti a végfelhasználói gépekre az Office-t, a végfelhasználók automatikusan ugyanazokat a nyelvi csomagokat kapják meg, mint az előző .MSI-alapú Office-telepítésnél.

## <a name="get-started"></a>Első lépések

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **Alkalmazások hozzáadása** ablaktáblán, az **Alkalmazástípus** listában, az **Office 365 csomag** alatt válassza a **Windows 10** lehetőséget.

## <a name="select-settings-format"></a>Beállítások formátumának kiválasztása

Kiválaszthat egy módszert az Alkalmazásbeállítások konfigurálásához a **Beállítások formátumának**kiválasztásával. A formázási lehetőségek beállítása a következők:
- Configuration Designer
- XML-adatok megadása

Ha kiválasztja a **Configuration Designer** alkalmazást, az **alkalmazás hozzáadása** panel két további beállítási lehetőséget is kínál:
- App Suite konfigurálása
- App Suite-beállítások

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Ha az **XML-adatértékek megadása** lehetőséget választja, az **alkalmazás hozzáadása** panelen JELENÍTSE meg az **XML-adatbevitel** beállítást. Válassza ezt a **konfigurációs fájl** ablaktábla megjelenítéséhez. 

![Office 365 Configuration Designer hozzáadása](./media/apps-add-office365/apps-add-office365-01.png)
    
Az **XML-adatok megadása** beállítással kapcsolatos további információkért lásd: az alábbi [XML-adatok megadása](apps-add-office365.md#enter-xml-format) .

## <a name="configure-app-suite-information"></a>App Suite-információk konfigurálása

Ebben a lépésben adhatja meg az alkalmazáscsomag adatait. Ezek alapján azonosíthatja az alkalmazáscsomagot az Intune-ban, és a felhasználók is ezek alapján találhatják meg azt a céges portálon.

1. Az **Alkalmazás hozzáadása** ablaktáblán válassza az **Alkalmazáscsomag adatai** lehetőséget.
2. Az **Alkalmazáscsomag adatai** ablaktáblán tegye a következőket:
    - **Csomag neve:** Itt adhatja meg az alkalmazáscsomag céges portálon megjelenő nevét. Ügyeljen arra, hogy minden megadott csomagnév egyedi legyen. Ha ugyanazt a csomagnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Csomag leírása:** Itt adhatja meg az alkalmazáscsomag leírását. Felsorolhatja például a kiválasztott belefoglalt alkalmazásokat.
    - **Közzétevő:** Közzétevőként a Microsoft jelenik meg.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ez a beállítás megkönnyíti a Céges portálon kereső felhasználóknak az alkalmazás megtalálását.
    - **Megjelenítés kiemelt alkalmazásként a Céges portálon:** Ezzel a beállítással hangsúlyosan jelenítheti meg az alkalmazáscsomagot a céges portál főoldalán az alkalmazásokat kereső felhasználók számára.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő:** Fejlesztőként a Microsoft jelenik meg.
    - **Tulajdonos:** Tulajdonosként a Microsoft jelenik meg.
    - **Megjegyzések**: Ide írhatja be az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Embléma:** – Amikor a felhasználók a céges portálon keresnek, az alkalmazás mellett megjelenik az Office 365-embléma.
3. Válassza az **OK** gombot.

## <a name="configure-app-suite"></a>App Suite konfigurálása

Ha a **konfigurációs tervező** lehetőséget választotta a Formátum legördülő lista **beállítása** alatt, az alkalmazás **hozzáadása** panelen megjelenik az **alkalmazáscsomag konfigurálása** lehetőség. Válassza ki azokat az Office-alkalmazásokat, melyeket szeretne eszközökhöz hozzárendelni.

1. Az **Alkalmazás felvétele** ablaktáblán válassza az **Alkalmazáscsomag konfigurálása** lehetőséget.
2. Az **Alkalmazáscsomag konfigurálása** ablaktáblán válassza ki a szokásos Office-alkalmazásokat, melyeket szeretne eszközökhöz hozzárendelni.  
    Emellett telepíthet alkalmazásokat a Microsoft Project online asztali ügyfeléhez és a Microsoft Visio online 2. csomagjához is, ha saját licencekkel rendelkezik.
3. Válassza az **OK** gombot.

## <a name="configure-app-suite-settings"></a>App Suite-beállítások konfigurálása

Ha a **konfigurációs tervező** lehetőséget választotta a Formátum legördülő lista **beállítása** alatt, az alkalmazás **hozzáadása** panelen megjelenik az **alkalmazáscsomag beállításai** lehetőség. Ebben a lépésben az alkalmazáscsomag telepítési beállításait konfigurálhatja. A beállítások minden, a csomaghoz hozzáadott alkalmazásra vonatkoznak.

1. Az **Alkalmazás hozzáadása** ablaktáblán válassza az **Alkalmazáscsomag beállításai** lehetőséget.
2. Az **Alkalmazáscsomag beállításai** ablaktáblán tegye a következőket:
    - **Office-verzió**: Itt választhatja ki, hogy az Office 32 bites vagy 64 bites verzióját szeretné hozzárendelni. A 32 bites verziót 32 bites és 64 bites eszközökön is, a 64 bites verziót viszont csak 64 bites eszközökön telepítheti.
    - **Frissítési csatorna**: Itt választhatja ki, hogyan történjen az Office frissítése az eszközökön. A különböző frissítési csatornákkal kapcsolatban az [Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) című témakörben találhat további információt. A következő lehetőségek közül választhat:
        - **Havonta**
        - **Havonta (megcélzott)**
        - **Semi-Annual**
        - **Féléves (megcélzott)**

        A csatorna kiválasztása után igény szerint kattinthat az **Adott** elemre az Office adott verziójának telepítéséhez a végfelhasználói eszközök kiválasztott csatornáján. Ekkor kiválaszthatja az Office **adott verzióját** a használathoz.
        
        Az elérhető verziók idővel változni fognak. Ezért egy új központi telepítés létrehozásakor újabb verziók válhatnak elérhetővé, és előfordulhat, hogy egyes régebbi verziók már nem érhetők el. A jelenleg üzemelő példányok továbbra is a régebbi verziót telepítik, de a verziólista csatornánként folyamatosan frissül.
        
        A rögzített verziót (vagy bármely tulajdonságot) frissítő és lehetőség szerint üzembe helyezett eszközök esetén, ha azokon az előző verziót telepítették, az állapotjelentés az eszköz bejelentkezéséig a Telepítve állapotot mutatja. Amikor az eszköz bejelentkezik, az állapot ideiglenesen Ismeretlenre vált, de ez a felhasználó számára nem látható. Amikor a felhasználó kezdeményezi az újabb elérhető verzió telepítését, látni fogja, hogy az állapot Telepítettre változott.
        
        További információkért lásd: [Az Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **MSI eltávolítása a végfelhasználói eszközökről** – Itt választhatja ki, hogy eltávolítja-e a már meglévő Office .MSI-alkalmazásokat a végfelhasználói eszközökről. A telepítés nem lesz sikeres, ha a végfelhasználói eszközökön már meglévő .MSI-alkalmazások vannak. Az eltávolítás nem korlátozódik az **Alkalmazáscsomag konfigurálásánál** telepítésre kiválasztott alkalmazásokra, mert minden Office (MSI) alkalmazást eltávolít a végfelhasználói eszközről. További információkért lásd: [Az Office már meglévő MSI-verzióinak eltávolítása az Office 365 ProPlusra való frissítés esetén](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Amikor az Intune újratelepíti a végfelhasználói gépekre az Office-t, a végfelhasználók automatikusan ugyanazokat a nyelvi csomagokat kapják meg, mint az előző .MSI-alapú Office-telepítésnél. 
    - **Alkalmazás végfelhasználói licencszerződésének automatikus elfogadása**: Ezt a beállítást akkor jelölje be, ha nem követeli meg a végfelhasználóktól, hogy elfogadják a licencszerződést. Ebben az esetben az Intune automatikusan elfogadja a szerződést.
    - **Megosztott aktiválás használata**: A megosztott aktiválás akkor használatos, amikor több felhasználó használja ugyanazt a számítógépet. További információ: [Az Office 365 megosztott aktiválásának áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Nyelvek**: Az Office automatikusan telepít minden olyan támogatott nyelvet, amely telepítve van a Windowsban a végfelhasználói eszközön. Ezt a beállítást akkor jelölje be, ha az alkalmazáscsomaghoz további nyelveket szeretne telepíteni. <p></p>
    További nyelveket helyezhet üzembe az Intune által felügyelt Office 365 Pro Plus-alkalmazások számára. Az elérhető nyelvek listája tartalmazza a nyelvi csomag **Típusát** (alap, részleges vagy nyelvi ellenőrzési) is. A Azure Portal válassza a **Microsoft Intune** > az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget. Az **alkalmazás hozzáadása** panel **alkalmazás típusa** listájában válassza a **Windows 10** az **Office 365 Suite**elemet. Válassza a **nyelvek** lehetőséget az **App Suite beállítások** ablaktábláján. További információkért lásd [a nyelvek az Office 365 ProPlusban történő üzembe helyezésének áttekintését](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Hatóköri címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).

1. Válassza a **hatókör (címkék)**  > **Hozzáadás**elemet.
2. A **Select (kijelölés** ) mező használatával keresheti meg a hatókör címkéit.
3. Jelölje be a jelölőnégyzetet az alkalmazáshoz hozzárendelni kívánt hatókör-címkék mellett.
4. Válassza a **Kiválasztás** > **OK** lehetőséget.

## <a name="enter-xml-format"></a>XML-formátum megadása

Ha az **XML-adatértékek megadása** lehetőséget választotta a **Formátum** legördülő listában, az **alkalmazás hozzáadása** panelen megjelenik az **XML-formátum megadása** lehetőség. További információ: [konfigurációs beállítások az Office-telepítő eszközhöz](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Befejezés

Amikor elkészült, válassza az **Alkalmazás hozzáadása** ablaktáblán a **Hozzáadás** lehetőséget. A létrehozott alkalmazás megjelenik az alkalmazáslistában. A következő lépés az alkalmazások társítása a kiválasztott csoportokhoz. További információ: [Alkalmazások hozzárendelése csoportokhoz](~/apps/apps-deploy.md).

## <a name="deployment-details"></a>Központi telepítés részletei

Ha az Intune-ból származó központi telepítési szabályzatot az Office- [konfigurációs szolgáltató (CSP)](https://docs.microsoft.com/windows/client-management/mdm/office-csp)segítségével rendeli hozzá a cél gépekhez, a befejező eszköz automatikusan letölti a telepítőcsomagot a *officecdn.microsoft.com* helyéről. A *Program Files* könyvtárában két könyvtár jelenik meg:

![Office-telepítési csomagok a program files könyvtárában](./media/apps-add-office365/office-folder.png)

A *Microsoft Office* könyvtár alatt létrejön egy új mappa, ahol a telepítési fájlok tárolódnak:

![Új létrehozott mappa Microsoft Office könyvtár alatt](./media/apps-add-office365/created-folder.png)

A *Microsoft Office 15* könyvtár alatt az Office Kattintásra futtatható telepítési indító fájljai vannak tárolva. A telepítés automatikusan elindul, ha a hozzárendelés típusa kötelező:

![Kattintson ide a telepítési indító fájlok futtatásához](./media/apps-add-office365/clicktorun-files.png)

A telepítés csendes módban lesz, ha a O365 csomag hozzárendelése kötelezőként van konfigurálva. Ha a telepítés sikeres volt, a letöltött telepítőfájlokat a rendszer törli. Ha a hozzárendelés **elérhetőként**van konfigurálva, az Office-alkalmazások a céges portál alkalmazásban jelennek meg, így a végfelhasználók manuálisan indíthatják el a telepítést.

## <a name="troubleshooting"></a>Hibaelhárítás
Az Intune az Office 365 ProPlus az Office [365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)használatával tölti le és helyezi üzembe az Office- [eszközökön](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) . Az [Office 365-végpontok kezelése](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) című útmutatóban ismertetett ajánlott eljárások alapján biztosíthatja, hogy a hálózati konfiguráció lehetővé tegye az ügyfelek számára a CDN közvetlen elérését a CDN-forgalom központi proxyn keresztüli átirányítása helyett, hogy elkerülje a szükségtelen késést.

Futtassa a [Microsoft ügyfélszolgálata és a helyreállítási asszisztenst az Office 365-hez](https://diagnostics.office.com) egy megcélzó eszközön, ha telepítési vagy futásidejű problémákba ütközik.

### <a name="additional-troubleshooting-details"></a>További hibaelhárítási részletek

Ha nem tudja telepíteni a O365-alkalmazásokat egy eszközre, meg kell határoznia, hogy a probléma az Intune-nal kapcsolatos-e, vagy az operációs rendszer/iroda kapcsolatos-e. Ha megtekintheti a két mappát *Microsoft Office* és *Microsoft Office 15* , amely megjelenik az eszköz *programfájlok* könyvtárában, ellenőrizheti, hogy az Intune sikeresen kezdeményezte-e az üzembe helyezést. Ha nem látja a *programfájlok*alatt megjelenő két mappát, ellenőrizze az alábbi eseteket:

- Az eszköz megfelelően van regisztrálva a Microsoft Intuneba. 
- Aktív hálózati kapcsolatok találhatók az eszközön. Ha az eszköz repülőgép üzemmódban van, ki van kapcsolva, vagy olyan helyen van, amely nem rendelkezik szolgáltatással, akkor a rendszer nem alkalmazza a házirendet, amíg a hálózati kapcsolat létrejött.
- Az Intune és az Office 365 hálózati követelményei teljesülnek, és a kapcsolódó IP-címtartományok a következő cikkek alapján érhetők el:

  - [Az Intune hálózati konfigurációs követelményei és sávszélessége](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Office 365 URL-címek és IP-címtartományok](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- A megfelelő csoportok hozzá lettek rendelve a O365 App Suite-hoz. 

Emellett figyelje a *C:\Program Files\Microsoft Office\Updates\Download*könyvtár méretét. Az Intune-felhőből letöltött telepítőcsomag ezen a helyen lesz tárolva. Ha a méret nem növekszik vagy csak nagyon lassan nő, javasoljuk, hogy ellenőrizze a hálózati kapcsolatot és a sávszélességet.

Ha azt állapítja meg, hogy az Intune és a hálózati infrastruktúra is a várt módon működik, akkor a problémát továbbra is az operációs rendszer perspektívájában kell elemezni. Vegye figyelembe a következő feltételeket:

- A célként megadott eszköznek Windows 10 alkotói frissítéssel vagy újabb verzióval kell futnia.
- Nem nyílik meg meglévő Office-alkalmazás, amíg az Intune üzembe helyezi az alkalmazásokat.
- Az Office meglévő MSI-verziói megfelelően el lettek távolítva az eszközről. Az Intune az Office MSI-vel nem kompatibilis Office-kattintások futtatását használja. A jelen dokumentumban a következő viselkedést kell megemlíteni:<br>
  [Az Office Kattintásra futtatva és Windows Installer ugyanazon a számítógépen nem támogatott](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- A bejelentkezési felhasználónak engedéllyel kell rendelkeznie az alkalmazások telepítéséhez az eszközön.
- Ellenőrizze, hogy nincsenek-e problémák a Windows Eseménynapló log **Windows-naplók** -> **alkalmazásokban**.
- Az Office telepítési részletes naplóinak rögzítése a telepítés során. Ehhez kövesse az alábbi lépéseket:<br>
    1. Aktiválja a részletes naplózást az Office telepítéséhez a célszámítógépen. Ehhez futtassa a következő parancsot a beállításjegyzék módosításához:<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Telepítse újra az Office 365-csomagot a megcélzott eszközökre.<br>
    3. Várjon körülbelül 15 – 20 percet, és nyissa meg a **% temp%** mappát és a **%windir%\Temp** mappát, a rendezés **dátum szerint módosítva**lehetőséget, válassza ki a (z) *{Machine Name} – {timestamp}. naplófájlokat* , amelyeket a Reprodukálási idő szerint módosított.<br>
    4. Futtassa a következő parancsot a részletes napló letiltásához:<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        A részletes naplók részletesebb információkat biztosítanak a telepítési folyamatról.

## <a name="errors-during-installation-of-the-app-suite"></a>Hiba történt az alkalmazáscsomag telepítésekor

A részletes telepítési naplók megtekintésével kapcsolatos információkért lásd: [az Office 365 ProPlus ULS-naplózásának engedélyezése](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) .

Az alábbi táblázatban az esetlegesen megjelenő gyakori hibakódok és azok jelentése található.

### <a name="status-for-office-csp"></a>Az Office felhőszolgáltatójának állapota

| Állapot | Fázis | Description |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Letöltés | Nem sikerült letölteni az Office-telepítő eszközt |
| 13 (ERROR_INVALID_DATA) | - | Nem sikerült ellenőrizni a letöltött Office-telepítő eszköz aláírását |
| A CertVerifyCertificateChainPolicy függvény által visszaadott hibakód | - | Nem sikerült a letöltött Office-telepítő eszköz hitelesítési ellenőrzése |
| 997 | WIP | Telepítés |
| 0 | Telepítés után | A telepítés sikeres volt |
| 1603 (ERROR_INSTALL_FAILURE) | - | Nem sikerült végrehajtani az előfeltételek ellenőrzését, például: SxS (a rendszer a 2016 MSI telepítését követően megpróbálta telepíteni) a mismatchOthers verzióban |
| 0x8000ffff (E_UNEXPECTED) | - | Kísérlet történt az eltávolításra, miközben a számítógépen nem található meg az Office Kattintásra szolgáltatás |
| 17002 | - | Nem sikerült befejezni a forgatókönyv végrehajtását (telepítés). Lehetséges okok: a telepítést a userInstallation megszakította egy másik installationOut, a installationUnknown nyelvi azonosítója során. |
| 17004 | - | Ismeretlen termékváltozatok |


### <a name="office-deployment-tool-error-codes"></a>Az Office-telepítő eszköz hibakódjai

| Forgatókönyv | Visszatérési kód | Felhasználói felület | Megjegyzés |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Kísérlet történt az eltávolításra, miközben nincs aktív Kattintásra-telepítés | -2147418113, 0x8000ffff vagy 2147549183 | Hibakód: 30088-1008Error kód: 30125-1011 (404) | Office-telepítő eszköz |
| Telepítés, miközben telepítve van az MSI-verzió | 1603 | - | Office-telepítő eszköz |
| A felhasználó vagy egy másik telepítés megszakította a telepítést | 17002 | - | Kattintásra |
| Kísérlet a 64 bites verzió telepítésére egy olyan eszközön, amelyen telepítve van a 32 bites verzió. | 1603 | - | Az Office-telepítő eszköz visszatérési kódja |
| Kísérlet egy ismeretlen termékváltozat telepítésére (az Office-felhőszolgáltató esetében ez nem valós használati eset, mivel csak érvényes termékváltozatokat lehet beküldeni) | 17004 | - | Kattintásra |
| Nincs elegendő szabad terület | 17002 | - | Kattintásra |
| Nem sikerült elindítani a Kattintásra-ügyfelet (váratlan) | 17000 | - | Kattintásra |
| A Kattintásra-ügyfélnek nem sikerült várólistára helyeznie a forgatókönyvet (váratlan) | 17001 | - | Kattintásra |

## <a name="next-steps"></a>További lépések

- Az alkalmazásoknak a választott csoportokhoz való hozzárendeléséhez tekintse meg az [Alkalmazások hozzárendelése csoportokhoz](/intune-azure/manage-apps/deploy-apps) című cikket.
