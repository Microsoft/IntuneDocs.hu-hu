---
title: Office 365-alkalmazások kiosztása Windows 10-es eszközökhöz Microsoft Intune használatával
titleSuffix: ''
description: Útmutató az Office 365-alkalmazások Windows 10-es eszközökön való telepítéséhez a Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: eff9f965649587a929e45d0f9d59305194ffe68b
ms.sourcegitcommit: b1ddc7f4a3d520b7d6755c7a423a46d1e2548592
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69651149"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Office 365-alkalmazások hozzárendelése Windows 10-es eszközökhöz a Microsoft Intune-nal

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
- A mutiple Office 365 üzemelő példányok jelenleg nem támogatottak. Csak egy központi telepítés lesz továbbítva az eszközre
- **Office-verzió**: - Itt választhatja ki, hogy az Office 32 bites vagy 64 bites verzióját szeretné hozzárendelni. A 32 bites verziót 32 bites és 64 bites eszközökön is, a 64 bites verziót viszont csak 64 bites eszközökön telepítheti.
- **MSI eltávolítása a végfelhasználói eszközökről** – Itt választhatja ki, hogy eltávolítja-e a már meglévő Office .MSI-alkalmazásokat a végfelhasználói eszközökről. A telepítés nem lesz sikeres, ha a végfelhasználói eszközökön már meglévő .MSI-alkalmazások vannak. Az eltávolítás nem korlátozódik az **Alkalmazáscsomag konfigurálásánál** telepítésre kiválasztott alkalmazásokra, mert minden Office (MSI) alkalmazást eltávolít a végfelhasználói eszközről. További információkért lásd: [Az Office már meglévő MSI-verzióinak eltávolítása az Office 365 ProPlusra való frissítés esetén](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Amikor az Intune újratelepíti a végfelhasználói gépekre az Office-t, a végfelhasználók automatikusan ugyanazokat a nyelvi csomagokat kapják meg, mint az előző .MSI-alapú Office-telepítésnél.

## <a name="get-started"></a>Bevezetés

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** tevékenységprofil panelén a **Kezelés** szakaszban válassza az **Alkalmazások** lehetőséget.
5. Válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazások hozzáadása** ablaktáblán, az **Alkalmazástípus** listában, az **Office 365 csomag** alatt válassza a **Windows 10** lehetőséget.

## <a name="select-settings-format"></a>Beállítások formátumának kiválasztása

Kiválaszthat egy módszert az Alkalmazásbeállítások konfigurálásához a **Beállítások formátumának**kiválasztásával. A formázási lehetőségek beállítása a következők:
- Configuration Designer
- XML-adatok megadása

Ha a **Configuration Designer** lehetőséget választja, az **alkalmazás hozzáadása** panel két további beállítási lehetőség közül választhat:
- App Suite konfigurálása
- App Suite-beállítások

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Ha az XML-adatértékek **megadása** lehetőséget választja, az **alkalmazás hozzáadása** panelen JELENÍTSE meg az **XML-adatbevitel** beállítást. Válassza ki ezt a **konfigurációs fájl** panel megjelenítéséhez. 

![Office 365 Configuration Designer hozzáadása](./media/apps-add-office365/apps-add-office365-01.png)
    
Az **XML-adatok megadása** beállítással kapcsolatos további információkért lásd: az alábbi [XML-adatok megadása](apps-add-office365.md#enter-xml-format) .

## <a name="configure-app-suite-information"></a>App Suite-információk konfigurálása

Ebben a lépésben adhatja meg az alkalmazáscsomag adatait. Ezek alapján azonosíthatja az alkalmazáscsomagot az Intune-ban, és a felhasználók is ezek alapján találhatják meg azt a céges portálon.

1. Az **Alkalmazás hozzáadása** ablaktáblán válassza az **Alkalmazáscsomag adatai** lehetőséget.
2. Az **Alkalmazáscsomag adatai** ablaktáblán tegye a következőket:
    - **Csomag neve**: Adja meg a vállalati portálon megjelenő alkalmazáscsomag nevét. Ügyeljen arra, hogy minden megadott csomagnév egyedi legyen. Ha ugyanazt a csomagnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Csomag leírása**: Adja meg az alkalmazáscsomag leírását. Felsorolhatja például a kiválasztott belefoglalt alkalmazásokat.
    - **Közzétevő**: A Microsoft közzétevőként jelenik meg.
    - **Kategória**: Szükség esetén kiválaszthat egy vagy több beépített alkalmazás-kategóriát vagy egy Ön által létrehozott kategóriát is. Ez a beállítás megkönnyíti a Céges portálon kereső felhasználóknak az alkalmazás megtalálását.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: Ezzel a beállítással Kiemelt módon jelenítheti meg az App Suite-t a vállalati portál főoldalán, amikor a felhasználók megkeresik az alkalmazásokat.
    - **Információs URL-cím**: Nem kötelező: megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi URL-cím**: Nem kötelező: megadhatja az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő**: A Microsoft a fejlesztőként jelenik meg.
    - **Tulajdonos**: A Microsoft tulajdonosként jelenik meg.
    - **Megjegyzések**: Adja meg az alkalmazáshoz hozzárendelni kívánt megjegyzéseket.
    - **Embléma**: Az Office 365 embléma az alkalmazással jelenik meg, amikor a felhasználók megkeresik a vállalati portált.
3. Kattintson az **OK** gombra.

## <a name="configure-app-suite"></a>App Suite konfigurálása

Ha a **konfigurációs tervező** lehetőséget választotta a Formátum legördülő lista **beállítása** alatt, az alkalmazás **hozzáadása** panelen megjelenik az **alkalmazáscsomag konfigurálása** lehetőség. Válassza ki azokat az Office-alkalmazásokat, melyeket szeretne eszközökhöz hozzárendelni.

1. Az **Alkalmazás felvétele** ablaktáblán válassza az **Alkalmazáscsomag konfigurálása** lehetőséget.
2. Az **Alkalmazáscsomag konfigurálása** ablaktáblán válassza ki a szokásos Office-alkalmazásokat, melyeket szeretne eszközökhöz hozzárendelni.  
    Emellett telepíthet alkalmazásokat a Microsoft Project online asztali ügyfeléhez és a Microsoft Visio online 2. csomagjához is, ha saját licencekkel rendelkezik.
3. Kattintson az **OK** gombra.

## <a name="configure-app-suite-settings"></a>App Suite-beállítások konfigurálása

Ha a **konfigurációs tervező** lehetőséget választotta a Formátum legördülő lista **beállítása** alatt, az alkalmazás **hozzáadása** panelen megjelenik az **alkalmazáscsomag beállításai** lehetőség. Ebben a lépésben az alkalmazáscsomag telepítési beállításait konfigurálhatja. A beállítások minden, a csomaghoz hozzáadott alkalmazásra vonatkoznak.

1. Az **Alkalmazás hozzáadása** ablaktáblán válassza az **Alkalmazáscsomag beállításai** lehetőséget.
2. Az **Alkalmazáscsomag beállításai** ablaktáblán tegye a következőket:
    - **Office-verzió**: Válassza ki, hogy az Office 32 bites vagy 64 bites verzióját szeretné-e hozzárendelni. A 32 bites verziót 32 bites és 64 bites eszközökön is, a 64 bites verziót viszont csak 64 bites eszközökön telepítheti.
    - **Frissítési csatorna**: Válassza ki az Office frissítését az eszközökön. A különböző frissítési csatornákkal kapcsolatban az [Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) című témakörben találhat további információt. A következő lehetőségek közül választhat:
        - **Havonta**
        - **Havonta (megcélzott)**
        - **Semi-Annual**
        - **Féléves (megcélzott)**

        A csatorna kiválasztása után igény szerint kattinthat az **Adott** elemre az Office adott verziójának telepítéséhez a végfelhasználói eszközök kiválasztott csatornáján. Ekkor kiválaszthatja az Office **adott verzióját** a használathoz.
        
        Az elérhető verziók idővel változni fognak. Ezért egy új központi telepítés létrehozásakor újabb verziók válhatnak elérhetővé, és előfordulhat, hogy egyes régebbi verziók már nem érhetők el. A jelenleg üzemelő példányok továbbra is a régebbi verziót telepítik, de a verziólista csatornánként folyamatosan frissül.
        
        A rögzített verziót (vagy bármely tulajdonságot) frissítő és lehetőség szerint üzembe helyezett eszközök esetén, ha azokon az előző verziót telepítették, az állapotjelentés az eszköz bejelentkezéséig a Telepítve állapotot mutatja. Amikor az eszköz bejelentkezik, az állapot ideiglenesen Ismeretlenre vált, de ez a felhasználó számára nem látható. Amikor a felhasználó kezdeményezi az újabb elérhető verzió telepítését, látni fogja, hogy az állapot Telepítettre változott.
        
        További információkért lásd: [Az Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **MSI eltávolítása a végfelhasználói eszközökről** – Itt választhatja ki, hogy eltávolítja-e a már meglévő Office .MSI-alkalmazásokat a végfelhasználói eszközökről. A telepítés nem lesz sikeres, ha a végfelhasználói eszközökön már meglévő .MSI-alkalmazások vannak. Az eltávolítás nem korlátozódik az **Alkalmazáscsomag konfigurálásánál** telepítésre kiválasztott alkalmazásokra, mert minden Office (MSI) alkalmazást eltávolít a végfelhasználói eszközről. További információkért lásd: [Az Office már meglévő MSI-verzióinak eltávolítása az Office 365 ProPlusra való frissítés esetén](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Amikor az Intune újratelepíti a végfelhasználói gépekre az Office-t, a végfelhasználók automatikusan ugyanazokat a nyelvi csomagokat kapják meg, mint az előző .MSI-alapú Office-telepítésnél. 
    - **Az alkalmazás végfelhasználói licencszerződésének automatikus elfogadása**: Válassza ezt a lehetőséget, ha nem kívánja, hogy a végfelhasználók elfogadják a licencszerződést. Ebben az esetben az Intune automatikusan elfogadja a szerződést.
    - **Megosztott számítógép aktiválásának használata**: Akkor válassza ezt a lehetőséget, ha több felhasználó osztozik egy számítógépen. További információ: [Az Office 365 megosztott aktiválásának áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Nyelvek**: Az Office-t a rendszer a végfelhasználó eszközén a Windows rendszerrel telepített támogatott nyelveken telepíti automatikusan. Ezt a beállítást akkor jelölje be, ha az alkalmazáscsomaghoz további nyelveket szeretne telepíteni. <p></p>
    További nyelveket helyezhet üzembe az Intune által felügyelt Office 365 Pro Plus-alkalmazások számára. Az elérhető nyelvek listája tartalmazza a nyelvi csomag **Típusát** (alap, részleges vagy nyelvi ellenőrzési) is. Az Azure Portalon válassza a **Microsoft Intune** > **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** lehetőséget. Az **Alkalmazás hozzáadása** panelen, az **Alkalmazástípusok** listáján, válassza az **Office 365 csomag** alatti **Windows 10** lehetőséget. Az **Alkalmazáscsomag beállításai** panelen válassza a **Nyelvek** lehetőséget. További információkért lásd [a nyelvek az Office 365 ProPlusban történő üzembe helyezésének áttekintését](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Hatóköri címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](scope-tags.md).

1. Válassza a **hatókör (címkék)**  > **Hozzáadás**elemet.
2. A **Select (kijelölés** ) mező használatával keresheti meg a hatókör címkéit.
3. Jelölje be a jelölőnégyzetet az alkalmazáshoz hozzárendelni kívánt hatókör-címkék mellett.
4. Válassza a **Kiválasztás** > **OK** lehetőséget.

## <a name="enter-xml-format"></a>XML-formátum megadása

Ha az **XML-adatértékek megadása** lehetőséget választotta **a formátum** legördülő listában, az **alkalmazás hozzáadása** panelen megjelenik az **XML-formátum megadása** lehetőség. További információ: [konfigurációs beállítások az Office-telepítő eszközhöz](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Befejezés

Amikor elkészült, válassza az **Alkalmazás hozzáadása** ablaktáblán a **Hozzáadás** lehetőséget. A létrehozott alkalmazás megjelenik az alkalmazáslistában.

## <a name="troubleshooting"></a>Hibaelhárítás
Az Intune az [](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) Office 365 ProPlus az Office [365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)használatával tölti le és helyezi üzembe az Office-eszközökön. Az [Office 365-végpontok kezelése](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) című útmutatóban ismertetett ajánlott eljárások alapján biztosíthatja, hogy a hálózati konfiguráció lehetővé tegye az ügyfelek számára a CDN közvetlen elérését a CDN-forgalom központi proxyn keresztüli átirányítása helyett, hogy elkerülje a szükségtelen késleltetés.

Futtassa a [Microsoft ügyfélszolgálata és a helyreállítási asszisztenst az Office 365-hez](https://diagnostics.office.com) egy megcélzó eszközön, ha telepítési vagy futásidejű problémákba ütközik.

## <a name="errors-during-installation-of-the-app-suite"></a>Hiba történt az alkalmazáscsomag telepítésekor

A részletes telepítési naplók megtekintésével kapcsolatos információkért lásd: [az Office 365 ProPlus ULS-naplózásának engedélyezése](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) .

Az alábbi táblázatban az esetlegesen megjelenő gyakori hibakódok és azok jelentése található.

### <a name="status-for-office-csp"></a>Az Office felhőszolgáltatójának állapota

| State | Fázis | Leírás |
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
| Kísérlet történt az eltávolításra, miközben nincs aktív Kattintásra-telepítés | -2147418113, 0x8000ffff vagy 2147549183 | Hibakód: 30088 – 1008Error kód: 30125-1011 (404) | Office-telepítő eszköz |
| Telepítés, miközben telepítve van az MSI-verzió | 1603 | - | Office-telepítő eszköz |
| A felhasználó vagy egy másik telepítés megszakította a telepítést | 17002 | - | Kattintásra |
| Kísérlet a 64 bites verzió telepítésére egy olyan eszközön, amelyen telepítve van a 32 bites verzió. | 1603 | - | Az Office-telepítő eszköz visszatérési kódja |
| Kísérlet egy ismeretlen termékváltozat telepítésére (az Office-felhőszolgáltató esetében ez nem valós használati eset, mivel csak érvényes termékváltozatokat lehet beküldeni) | 17004 | - | Kattintásra |
| Nincs elegendő szabad terület | 17002 | - | Kattintásra |
| Nem sikerült elindítani a Kattintásra-ügyfelet (váratlan) | 17000 | - | Kattintásra |
| A Kattintásra-ügyfélnek nem sikerült várólistára helyeznie a forgatókönyvet (váratlan) | 17001 | - | Kattintásra |

## <a name="next-steps"></a>További lépések

- Az alkalmazásoknak a választott csoportokhoz való hozzárendeléséhez tekintse meg az [Alkalmazások hozzárendelése csoportokhoz](/intune-azure/manage-apps/deploy-apps) című cikket.
