---
title: Office 365-alkalmazások hozzáadása Windows 10-es eszközökhöz Microsoft Intune használatával
titleSuffix: ''
description: Útmutató az Office 365-alkalmazások Windows 10-es eszközökön való telepítéséhez a Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 86d02ae1277ff2fd6dfce9bf206628f5dc1c2a84
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755322"
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

## <a name="select-the-office-365-suite-app-type"></a>Válassza ki az Office 365 Suite-alkalmazás típusát

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktábla **Office 365 Suite** szakaszában válassza a **Windows 10** lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **Office 365 Suite hozzáadása** lépések.


## <a name="step-1---app-suite-information"></a>1\. lépés – App Suite-információk

Ebben a lépésben adhatja meg az alkalmazáscsomag adatait. Ezek alapján azonosíthatja az alkalmazáscsomagot az Intune-ban, és a felhasználók is ezek alapján találhatják meg azt a céges portálon.

1. Az **App Suite-információk** lapon ellenőrizheti vagy módosíthatja az alapértelmezett értékeket:
    - **Csomag neve:** Itt adhatja meg az alkalmazáscsomag céges portálon megjelenő nevét. Ügyeljen arra, hogy minden megadott csomagnév egyedi legyen. Ha ugyanazt a csomagnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Csomag leírása:** Itt adhatja meg az alkalmazáscsomag leírását. Felsorolhatja például a kiválasztott belefoglalt alkalmazásokat.
    - **Közzétevő:** Közzétevőként a Microsoft jelenik meg.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ez a beállítás megkönnyíti a Céges portálon kereső felhasználóknak az alkalmazás megtalálását.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: ezzel a beállítással a vállalati portál főoldalán jelenítheti meg az App Suite-t, amikor a felhasználók megkeresik az alkalmazásokat.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő:** Fejlesztőként a Microsoft jelenik meg.
    - **Tulajdonos:** Tulajdonosként a Microsoft jelenik meg.
    - **Megjegyzések**: Ide írhatja be az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Embléma:** – Amikor a felhasználók a céges portálon keresnek, az alkalmazás mellett megjelenik az Office 365-embléma.
2. Az **App Suite konfigurálása** lap megjelenítéséhez kattintson a **tovább** gombra.

## <a name="step-2---option-1-configure-app-suite-using-the-configuration-designer"></a>2\. lépés – (**1. lehetőség**) az App Suite konfigurálása a Configuration Designer használatával 

A **konfigurációs beállítások formátumának**kiválasztásával kiválaszthatja az Alkalmazásbeállítás konfigurálásának módját. A formázási lehetőségek beállítása a következők:
- Configuration Designer
- XML-adatok megadása

Ha kiválasztja a **Configuration Designer** alkalmazást, az **alkalmazás hozzáadása** panel három további beállítási területre fog váltani:
- App Suite konfigurálása
- App Suite-információk
- Tulajdonságok

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

1. A **Configuration App Suite** lapon válassza a **Configuration Designer**elemet.
   - **Office-alkalmazások kiválasztása**: válassza ki az eszközökhöz hozzárendelni kívánt szabványos Office-alkalmazásokat a legördülő listában szereplő alkalmazások közül.
   - **Más Office-alkalmazások kijelölése (licenc szükséges)** : válassza ki az eszközökhöz hozzárendelni kívánt további Office-alkalmazásokat, valamint a legördülő listában szereplő alkalmazások kiválasztásával. Ezek közé tartoznak a licencelt alkalmazások, például a Microsoft Project online asztali ügyfélprogram és a Microsoft Visio online 2. csomag.
   - **Architektúra**: válassza ki, hogy az Office ProPlus **32 bites** vagy **64 bites** verzióját szeretné-e hozzárendelni. A 32 bites verziót 32 bites és 64 bites eszközökön is, a 64 bites verziót viszont csak 64 bites eszközökön telepítheti.
    - **Frissítési csatorna**: Itt választhatja ki, hogyan történjen az Office frissítése az eszközökön. A különböző frissítési csatornákkal kapcsolatban az [Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) című témakörben találhat további információt. A következő lehetőségek közül választhat:
        - **Havonta**
        - **Havonta (megcélzott)**
        - **Semi-Annual**
        - **Féléves (megcélzott)**

        A csatorna kiválasztása után kiválaszthatja a következőket:
        - **Más verziók eltávolítása**: válassza az **Igen** lehetőséget az Office (MSI) más verzióinak felhasználói eszközökről való eltávolításához. Akkor válassza ezt a lehetőséget, ha el szeretné távolítani a meglévő Office-t. A végfelhasználói eszközökről származó MSI-alkalmazások. A telepítés nem lesz sikeres, ha a végfelhasználói eszközökön már meglévő .MSI-alkalmazások vannak. Az eltávolítás nem korlátozódik az **Alkalmazáscsomag konfigurálásánál** telepítésre kiválasztott alkalmazásokra, mert minden Office (MSI) alkalmazást eltávolít a végfelhasználói eszközről. További információkért lásd: [Az Office már meglévő MSI-verzióinak eltávolítása az Office 365 ProPlusra való frissítés esetén](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Amikor az Intune újratelepíti a végfelhasználói gépekre az Office-t, a végfelhasználók automatikusan ugyanazokat a nyelvi csomagokat kapják meg, mint az előző .MSI-alapú Office-telepítésnél. 
        - **Telepítendő verzió**: válassza ki a telepíteni kívánt Office-verziót.
        - **Megadott verzió**: Ha a fenti beállításban **megadott** **verziót** választotta, akkor kiválaszthatja, hogy az Office adott verzióját a végfelhasználói eszközökön a kiválasztott csatornára telepítse. 
            
            Az elérhető verziók idővel változni fognak. Ezért egy új központi telepítés létrehozásakor újabb verziók válhatnak elérhetővé, és előfordulhat, hogy egyes régebbi verziók már nem érhetők el. A jelenleg üzemelő példányok továbbra is a régebbi verziót telepítik, de a verziólista csatornánként folyamatosan frissül.
            
            A rögzített verziót (vagy bármely tulajdonságot) frissítő és lehetőség szerint üzembe helyezett eszközök esetén, ha azokon az előző verziót telepítették, az állapotjelentés az eszköz bejelentkezéséig a Telepítve állapotot mutatja. Amikor az eszköz bejelentkezik, az állapot ideiglenesen Ismeretlenre vált, de ez a felhasználó számára nem látható. Amikor a felhasználó kezdeményezi az újabb elérhető verzió telepítését, látni fogja, hogy az állapot Telepítettre változott.
            
            További információkért lásd: [Az Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).
    - **Megosztott aktiválás használata**: A megosztott aktiválás akkor használatos, amikor több felhasználó használja ugyanazt a számítógépet. További információ: [Az Office 365 megosztott aktiválásának áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Alkalmazás végfelhasználói licencszerződésének automatikus elfogadása**: Ezt a beállítást akkor jelölje be, ha nem követeli meg a végfelhasználóktól, hogy elfogadják a licencszerződést. Ebben az esetben az Intune automatikusan elfogadja a szerződést.
    - **Nyelvek**: Az Office automatikusan telepít minden olyan támogatott nyelvet, amely telepítve van a Windowsban a végfelhasználói eszközön. Ezt a beállítást akkor jelölje be, ha az alkalmazáscsomaghoz további nyelveket szeretne telepíteni. <p></p>
        További nyelveket helyezhet üzembe az Intune által felügyelt Office 365 Pro Plus-alkalmazások számára. Az elérhető nyelvek listája tartalmazza a nyelvi csomag **Típusát** (alap, részleges vagy nyelvi ellenőrzési) is. A Azure Portal válassza a **Microsoft Intune** > az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget. Az **alkalmazás hozzáadása** panel **alkalmazás típusa** listájában válassza a **Windows 10** az **Office 365 Suite**elemet. Válassza a **nyelvek** lehetőséget az **App Suite beállítások** ablaktábláján. További információkért lásd [a nyelvek az Office 365 ProPlusban történő üzembe helyezésének áttekintését](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).
2. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.

## <a name="step-2---option-2-configure-app-suite-using-xml-data"></a>2\. lépés – (**2. lehetőség**) az App Suite konfigurálása XML-adatok használatával 

Ha az **App Suite konfigurálása** **lapon az** **XML-adatok megadása** lehetőséget választotta, az Office App Suite-t egyéni konfigurációs fájllal is konfigurálhatja.

![Office 365 Configuration Designer hozzáadása](./media/apps-add-office365/apps-add-office365-01.png)

1. A konfigurációs XML-fájl hozzáadva.
2. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.

Az XML-adatok beírásával kapcsolatos további információkért lásd: [az Office üzembehelyezési eszköz konfigurációs beállításai](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="step-3---select-scope-tags-optional"></a>3\. lépés – hatókör-címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).

1. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye az alkalmazáscsomag hatókör-címkéit. 
2. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.

## <a name="step-4---assignments"></a>4\. lépés – hozzárendelések

1. Válassza ki a **szükséges**, a **regisztrált eszközök számára elérhető**lehetőséget, vagy **távolítsa el** a csoport hozzárendeléseit az alkalmazáscsomag számára. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md) , valamint [alkalmazások társítása a csoportokhoz Microsoft Intune](apps-deploy.md)használatával.
2. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez. 

## <a name="step-5---review--create"></a>5\. lépés – felülvizsgálat + létrehozás

1. Tekintse át az alkalmazáscsomag által megadott értékeket és beállításokat.
2. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

    Megjelenik a létrehozott Office 365 ablak 10 alkalmazáscsomag **áttekintő** panelje.

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

A részletes telepítési naplók megtekintésével kapcsolatos információkért lásd: [az Office 365 ProPlus ULS-naplózásának engedélyezése](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging) .

Az alábbi táblázatban az esetlegesen megjelenő gyakori hibakódok és azok jelentése található.

### <a name="status-for-office-csp"></a>Az Office felhőszolgáltatójának állapota

| Állapot | Fázis | Description |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Letöltések | Nem sikerült letölteni az Office-telepítő eszközt |
| 13 (ERROR_INVALID_DATA) | - | Nem sikerült ellenőrizni a letöltött Office-telepítő eszköz aláírását |
| A CertVerifyCertificateChainPolicy függvény által visszaadott hibakód | - | Nem sikerült a letöltött Office-telepítő eszköz hitelesítési ellenőrzése |
| 997 | WIP | A |
| 0 | Telepítés után | A telepítés sikeres volt |
| 1603 (ERROR_INSTALL_FAILURE) | - | Nem sikerült végrehajtani az előfeltételek ellenőrzését, például: SxS (a rendszer a 2016 MSI telepítését követően megpróbálta telepíteni) a mismatchOthers verzióban |
| 0x8000ffff (E_UNEXPECTED) | - | Kísérlet történt az eltávolításra, miközben a számítógépen nem található meg az Office Kattintásra szolgáltatás |
| 17002 | - | Nem sikerült befejezni a forgatókönyv végrehajtását (telepítés). Lehetséges okok: a telepítést a userInstallation megszakította egy másik installationOut, a installationUnknown nyelvi azonosítója során. |
| 17004 | - | Ismeretlen termékváltozatok |


### <a name="office-deployment-tool-error-codes"></a>Az Office-telepítő eszköz hibakódjai

| Forgatókönyv | Visszatérési kód | UI | Megjegyzés |
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

- Az alkalmazáscsomag további csoportokhoz rendeléséhez lásd: [alkalmazások társítása csoportokhoz](/intune-azure/manage-apps/deploy-apps).
