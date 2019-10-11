---
title: Win32-alkalmazások hozzáadása és kiosztása Microsoft Intune
titleSuffix: ''
description: Útmutató Win32-alkalmazások hozzáadásához, hozzárendeléséhez és kezeléséhez Microsoft Intune használatával. E témakör áttekintést nyújt a Win32-alkalmazások telepítési és kezelési lehetőségeiről az Intune-ban, valamint a Win32-alkalmazásokkal kapcsolatos hibák elhárításával kapcsolatban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21192d259de0711ad38fa35b294ea82c7d913292
ms.sourcegitcommit: fca2670142c083d7562c0a36547a6a451863e315
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/08/2019
ms.locfileid: "72036495"
---
# <a name="intune-standalone---win32-app-management"></a>Önálló Intune – Win32-alkalmazások kezelése

Az [Intune standalone](../fundamentals/mdm-authority-set.md) mostantól lehetővé teszi a nagyobb Win32-alkalmazások felügyeleti képességeit. Bár a felhőhöz csatlakozó ügyfelek használhatják a Konfigurációkezelőt a Win32-alkalmazások kezeléséhez, a kizárólag Intune-nal rendelkező ügyfelek számára több lehetőség érhető el az üzletági (LOB) Win32-alkalmazások kezeléséhez. E témakör áttekintést nyújt a Win32-alkalmazások Intune-ban elérhető kezelési funkcióiról, valamint a hibaelhárítással kapcsolatos lehetőségekről.

> [!NOTE]
> Ez az alkalmazás-kezelési funkció a Windows-alkalmazásokhoz egyaránt támogatja a 32 bites és a 64 bites operációsrendszer-architektúrát.

> [!IMPORTANT]
> Win32-alkalmazások telepítésekor érdemes lehet kizárólag az [Intune felügyeleti bővítményt](../apps/intune-management-extension.md) használni, különösen akkor, ha egy többfájlos Win32 alkalmazás telepítője van. Ha az Autopilot-regisztráció során összekeveri a Win32-alkalmazások és az üzletági alkalmazások telepítését, előfordulhat, hogy az alkalmazás telepítése sikertelen lesz.  

## <a name="prerequisites"></a>Előfeltételek

A Win32-alkalmazások felügyeletének használatához győződjön meg arról, hogy megfelel az alábbi feltételeknek:

- Windows 10 1607-es vagy újabb verzió (Enterprise, Pro és Education verziók)
- A Windows 10-ügyfélnek: 
  - Az eszközöknek csatlakozniuk kell az Azure AD-hez, és automatikusan regisztrálni kell őket. Az Intune felügyeleti bővítmény támogatja az Azure AD-hez csatlakoztatott, hibrid tartományhoz csatlakozó, a csoportházirend által beléptetett eszközök használatát. 
  > [!NOTE]
  > A csoportházirend által beléptetett forgatókönyv esetében – a végfelhasználó a helyi felhasználói fiókot használja a Windows 10-es HRE való csatlakozáshoz. A felhasználónak a HRE felhasználói fiókjával kell bejelentkeznie az eszközre, és regisztrálnia kell az Intune-ban. Az Intune telepíti az Intune felügyeleti bővítményét az eszközön, ha egy PowerShell-parancsfájl vagy egy Win32-alkalmazás a felhasználóhoz vagy az eszközhöz van rendelve.
- A Windows-alkalmazások mérete 8 GB-onként van korlátozva.

## <a name="prepare-the-win32-app-content-for-upload"></a>A Win32-alkalmazás tartalmának előkészítése a feltöltéshez

A [Microsoft Win32 Content PREP eszköz](https://go.microsoft.com/fwlink/?linkid=2065730) használatával a klasszikus Windows-(Win32-) alkalmazásokat előre feldolgozhatja. Az eszköz *. intunewin* formátumban alakítja át az alkalmazás telepítési fájljait. Az eszköz az Intune által az alkalmazás telepítési állapotának meghatározásához szükséges néhány attribútumot is észleli. Ha ezt az eszközt az App Installer mappában használja, akkor létrehozhat egy Win32-alkalmazást az Intune-konzolon.

> [!IMPORTANT]
> A [Microsoft Win32 Content PREP Tool](https://go.microsoft.com/fwlink/?linkid=2065730) a *. intunewin* fájl létrehozásakor kihelyezi az összes fájlt és almappát. Ügyeljen arra, hogy a Microsoft Win32 Content PREP eszköz elkülönítse a telepítő fájljait és mappáit, hogy ne tartalmazza az eszközt vagy más szükségtelen fájlokat és mappákat a *. intunewin* fájlban.

A [Microsoft Win32 Content PREP eszközt](https://go.microsoft.com/fwlink/?linkid=2065730) zip-fájlként töltheti le a githubról. A tömörített fájl egy **Microsoft-Win32-Content-PREP-Tool-Master**nevű mappát tartalmaz. A mappa tartalmazza a PREP eszközt, a licencet, a readme és a kibocsátási megjegyzéseket. 

### <a name="process-flow-to-create-intunewin-file"></a>Folyamat folyamata. intunewin-fájl létrehozása

   ![Folyamat feldolgozása. intunewin-fájl létrehozásához](./media/apps-win32-app-management/prepare-win32-app.svg)

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Futtassa a Microsoft Win32 Content PREP eszközt

Ha paraméterek nélkül futtatja a parancssori ablakban a `IntuneWinAppUtil.exe` parancsot, az eszköz végigvezeti a szükséges paraméterek lépésről lépésre történő beírásakor. A paramétereket a következő elérhető parancssori paraméterek alapján adhatja hozzá a parancshoz.

### <a name="available-command-line-parameters"></a>Elérhető parancssori paraméterek 

|    **Parancssori paraméter**    |    **Leírás**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Súgó    |
|    `-c <setup_folder>`     |    Az összes telepítési fájl mappája. A mappában lévő összes fájl tömörítve lesz a *. intunewin* fájlba.    |
|    `-s <setup_file>`     |    Telepítőfájl (például *setup.exe* vagy *setup.msi*).    |
|    `-o <output_folder>`     |    Kimeneti mappa a létrehozott *.intunewin* fájl számára.    |
|    `-q`       |    Csendes mód    |

### <a name="example-commands"></a>Példaparancsok

|    **Példaparancs**    |    **Leírás**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Ez a parancs megjeleníti az eszköz használatára vonatkozó információkat.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    Ez a parancs létrehozza az `.intunewin` fájlt a megadott forrásmappa és telepítőfájl alapján. Az MSI-telepítőfájlhoz az eszköz lekéri az Intune-hoz szükséges adatokat. Ha a `-q` van megadva, a parancs csendes módban fog futni, és ha a kimeneti fájl már létezik, felül fogja írni. Ha a kimeneti mappa még nem létezik, akkor automatikusan létrejön.    |

*. Intunewin* -fájl létrehozásakor helyezzen el minden olyan fájlt, amelyre szüksége van a telepítési mappa almappájára való hivatkozáshoz. Ezután használjon egy relatív elérési utat a szükséges fájlra való hivatkozáshoz. Példa:

**Telepítési forrás mappája:** *c:\testapp\v1.0*<br>
**Licencfájl:** *c:\testapp\v1.0\licenses\license.txt*

Tekintse meg a *License. txt* fájlt a relatív elérési út *licenses\license.txt*használatával.

## <a name="create-assign-and-monitor-a-win32-app"></a>Win32-alkalmazás létrehozása, hozzárendelése és monitorozása

Az üzletági (LOB) alkalmazásokhoz hasonlóan Win32-alkalmazást is hozzáadhat a Microsoft Intune-hoz. Az ilyen alkalmazásokat általában házon belül írják, vagy egy külső féltől származnak. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Folyamat feldolgozása Win32-alkalmazás hozzáadásához az Intune-ban

<img alt="Process flow to add a Win32 app to Intune" src="./media/apps-win32-app-management/add-win32-app.svg" width="500">

### <a name="add-a-win32-app-to-intune"></a>Win32-alkalmazás hozzáadása az Intune-hoz

Az alábbi lépések útmutatást nyújtanak a Windows-alkalmazások Intune-hoz való hozzáadásához.

### <a name="step-1-specify-the-software-setup-file"></a>1\. lépés: A szoftvertelepítési fájl beállítása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** elemet.
4. Az alkalmazás **hozzáadása** panelen válassza a **Windows-alkalmazás (Win32)** lehetőséget a megadott legördülő listából.

    ![Képernyőkép az alkalmazás hozzáadása panelről – típus hozzáadása legördülő lista](./media/apps-win32-app-management/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>2\. lépés: Az alkalmazáscsomag fájljának feltöltése

1. Az **Alkalmazás felvétele** panelen válassza az **Alkalmazáscsomag-fájl** lehetőséget egy fájl kiválasztásához. Megjelenik az Alkalmazáscsomag-fájl panel.

    ![Képernyőkép az alkalmazáscsomag-fájl panelről](./media/apps-win32-app-management/apps-win32-app-02.png)

2. Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ezt követően jelölje ki az *.intunewin* kiterjesztésű Windows-telepítőfájlt.

    > [!IMPORTANT]
    > Ügyeljen arra, hogy a Microsoft Win32 Content PREP eszköz legújabb verzióját használja. Ha nem a legújabb verziót használja, egy figyelmeztetés jelenik meg, amely jelzi, hogy az alkalmazás a Microsoft Win32 Content PREP Tool egy régebbi verziójával lett csomagolva. 

3. Amikor végzett, válassza az **OK** gombot.

### <a name="step-3-configure-app-information"></a>3\. lépés: Az alkalmazásadatok konfigurálása

1. Az alkalmazás konfigurálásához az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazás adatai** elemet.
2. Az **Alkalmazás adatai** panelen konfigurálja az alábbi információkat. Lehetséges, hogy ezen a panelen néhány érték automatikusan ki lesz töltve.
    - **Név**: Adja meg az alkalmazásnak a vállalati portálon megjelenő nevét. Ha ugyanazt az alkalmazásnevet kétszer adja meg, mindkét alkalmazás meg fog jelenni a céges portálon.
    - **Description** (Leírás): Adja meg az alkalmazás leírását. A leírás megjelenik a Céges portálon.
    - Az r **közzététele**: Itt adhatja meg az alkalmazás kiadójának nevét.
    - **Kategória**: Válasszon ki egy vagy több beépített alkalmazás-kategóriát, vagy válasszon ki egy Ön által létrehozott kategóriát. A kategóriákkal megkönnyítheti a felhasználók számára az alkalmazás megkeresését a Céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: Az alkalmazás jól észrevehető módon való megjelenítése a vállalati portál fő lapján, amikor a felhasználók tallózással alkalmazásokat keresnek.
    - **Információs URL-cím**: Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Adatvédelmi URL-cím**: Igény szerint megadhatja az alkalmazás adatvédelmi információit tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Fejlesztő**: Igény szerint megadhatja az alkalmazás-fejlesztő nevét.
    - **Tulajdonos**: Igény szerint megadhatja az alkalmazás tulajdonosának nevét. Például **HR részleg**.
    - **Megjegyzések**: Adja meg az alkalmazáshoz hozzárendelni kívánt megjegyzéseket.
    - **Embléma**: Töltse fel az alkalmazáshoz társított ikont. Ez az ikon jelenik meg az alkalmazásnál a Céges portálon böngésző felhasználók számára.
3. Amikor végzett, válassza az **OK** gombot.

### <a name="step-4-configure-app-installation-details"></a>4\. lépés: Az alkalmazás telepítésére vonatkozó részletek konfigurálása
1. Az alkalmazás telepítési és eltávolítási parancsának konfigurálásához az **Alkalmazás felvétele** panelen válassza a **Program** elemet.
2. Adja meg az alkalmazás telepítéséhez szükséges teljes telepítési parancssort. 

    Ha például az alkalmazás fájlneve **MyApp123**, adja hozzá a következőt:<br>
    `msiexec /p “MyApp123.msp”`<p>
    Ha pedig az alkalmazás `ApplicationName.exe`, a parancs az alkalmazás neve, amelyet a csomag által támogatott parancs-argumentumok (kapcsolók) követnek. <br>Példa:<br>
    `ApplicationName.exe /quiet`<br>
    A fenti parancsban a `ApplicationName.exe` csomag támogatja a `/quiet` parancs argumentumot.<p> 
    Az alkalmazáscsomag által támogatott argumentumok esetében forduljon az alkalmazás forgalmazójához.

3. Adja meg az alkalmazás eltávolításához szükséges teljes eltávolítási parancssort az alkalmazás GUID-értékei alapján. 

    Példa: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Az adott Win32-alkalmazás telepítését a **Felhasználó** vagy a **Rendszer** környezetben konfigurálhatja. A **Felhasználó** környezet csak az adott felhasználóra vonatkozik. A **Rendszer** környezet az adott, Windows 10-es rendszerű eszköz összes felhasználójára vonatkozik.
    >
    > A végfelhasználóknak nem kell bejelentkezniük az eszközön a Win32-alkalmazások telepítéséhez.
    > 
    > A Win32-alkalmazás telepítése és eltávolítása a rendszergazdai jogosultságok alatt történik (alapértelmezés szerint), ha az alkalmazás felhasználói környezetben történő telepítésre van beállítva, és az eszköz végfelhasználója rendszergazdai jogosultságokkal rendelkezik.

4. Amikor végzett, válassza az **OK** gombot.

### <a name="step-5-configure-app-requirements"></a>5\. lépés: Alkalmazásokra vonatkozó követelmények konfigurálása

1. Az alkalmazás telepítéséhez szükséges rendszerkövetelmények beállításához az **Alkalmazás felvétele** panelen válassza a **Követelmények** elemet.
2. A **követelmény-szabály hozzáadása** panelen konfigurálja a következő információkat. Lehetséges, hogy ezen a panelen néhány érték automatikusan ki lesz töltve.
    - **Operációs rendszer architektúrája**: Válassza ki, hogy milyen architektúrára van szükség az alkalmazás telepítéséhez.
    - **Minimális operációs rendszer**: Válassza ki az alkalmazás telepítéséhez szükséges minimális operációs rendszert.
    - **Lemezterület szükséges (MB)** : Szükség esetén adja hozzá a rendszermeghajtón a szükséges szabad lemezterületet az alkalmazás telepítéséhez.
    - **Fizikai memória szükséges (MB)** : Szükség esetén adja hozzá az alkalmazás telepítéséhez szükséges fizikai memóriát (RAM).
    - **A szükséges logikai processzorok minimális száma**: Szükség esetén adja meg az alkalmazás telepítéséhez szükséges logikai processzorok minimális számát.
    - **Minimális CPU-sebesség szükséges (MHz)** : Szükség esetén adja meg az alkalmazás telepítéséhez szükséges minimális CPU-sebességet.

3. A **Hozzáadás** gombra kattintva jelenítse meg a **követelmény hozzáadása szabályt** , és konfigurálja a további követelmények szabályait. Válassza ki a **követelmény típusát** annak a szabálynak a kiválasztásához, amelyet a követelmények érvényesítésének meghatározásához fog használni. A követelmények szabályai a fájlrendszer adatai, a beállításjegyzék értékei vagy a PowerShell-parancsfájlok alapján is alapulhatnak. 
    - **Fájl**: Ha a **követelmény típusaként**a **fájl** lehetőséget választja, a követelményi szabálynak meg kell állapítania egy fájlt vagy mappát, dátumot, verziót vagy méretet. 
        - **Elérési út** – Az észlelendő fájlt vagy mappát tartalmazó mappa teljes elérési útja.
        - **Fájl vagy mappa** – Az észlelendő fájl vagy mappa.
        - **Tulajdonság** – válassza ki az alkalmazás meglétének ellenőrzéséhez használt szabály típusát.
        - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha 64 bites ügyfeleken a „path” környezeti változókat 32 bites környezetben szeretné kibontani, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer minden „path” változót 64 bites környezetben bontja ki a 64 bites ügyfeleken. A 32 bites ügyfelek mindig a 32 bites környezetet használják.
    - **Beállításjegyzék**: Ha a **követelmény típusaként**a **beállításjegyzéket** választja, a követelményi szabálynak az érték, a karakterlánc, az egész szám vagy a verzió alapján kell megállapítania egy beállításjegyzék-beállítást.
        - **Kulcs elérési útja** – Az észlelendő értéket tartalmazó beállításjegyzék-bejegyzés teljes elérési útja.
        - **Érték neve** – Az észlelendő beállításazonosító neve. Ha ez az érték üres, akkor az észlelés a kulcs alapján történik. A rendszer egy kulcs (alapértelmezett) értékét használja észlelési értékként, ha az észlelési módszer nem a fájl vagy a mappa meglétén alapul.
        - **Beállításkulcs követelménye** – válassza ki a beállításkulcs összehasonlításának típusát, amely meghatározza a követelmény szabályának érvényességét.
        - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha a 32 bites beállításjegyzékben szeretne keresni a 64 bites ügyfeleken, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer a 64 bites ügyfeleken a 64 bites beállításjegyzékben fog keresni. A 32 bites ügyfeleknél a keresés mindig a 32 bites beállításjegyzéket érinti.
    - **Parancsfájl**: A **követelmény típusaként**válassza a **parancsfájlt** , ha a fájl, a beállításjegyzék vagy bármely más, az Intune-konzolon elérhető módszer alapján nem hozható létre követelmény-szabály.
        - **Parancsfájl** – a PowerShell parancsfájl-alapú követelményi szabályához (ha létezik kód 0), a rendszer részletesebben felderíti az stdout-ot. Például észlelhető az STDOUT olyan egész számként, amelynek értéke 1.
        - **Parancsfájl futtatása 32 bites folyamatként 64 bites ügyfeleken** – válassza az **Igen** lehetőséget, ha a parancsfájlt 32 bites folyamaton szeretné futtatni 64 bites ügyfeleken. Válassza a **nem** (alapértelmezett) lehetőséget, hogy a parancsfájlt 64 bites folyamaton futtassa a 64 bites ügyfeleken. 32 bites ügyfelek a szkriptet egy 32 bites folyamatban futtatják.
        - **Futtassa ezt a parancsfájlt a bejelentkezett hitelesítő adatok használatával**: Válassza az **Igen** lehetőséget a szkript futtatásához a bejelentkezett eszköz hitelesítő adatai * * használatával.
        - **Szkriptaláírás ellenőrzésének kényszerítése** – Az **Igen** lehetőség kiválasztásával ellenőrizheti, hogy a szkriptet egy megbízható gyártó írta-e alá, így a szkript figyelmeztetések és felszólítások megjelenítése nélkül fog futni. A szkript letiltás nélkül fog futni. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a szkript végfelhasználói megerősítéssel, az aláírás ellenőrzése nélkül fut.
        - **Válassza ki a kimeneti adattípust**: Válassza ki a követelmény szabályának meghatározásakor használt adattípust.
4. Amikor végzett, válassza az **OK** gombot.

### <a name="step-6-configure-app-detection-rules"></a>6\. lépés: Alkalmazás-észlelési szabályok konfigurálása

1. Az alkalmazás meglétének észleléséhez szükséges szabályok konfigurálásához az **Alkalmazás felvétele** panelen válassza az **Észlelési szabályok** elemet.
2. A **Szabályok formátuma** mezőben adja meg, hogyan fogja észlelni a rendszer az alkalmazás meglétét. Választhatja az észlelési szabályok manuális konfigurálását, illetve egyéni szkriptet is használhat az alkalmazás meglétének észleléséhez. Legalább egy észlelési szabályt ki kell választani. 

    > [!NOTE]
    > Az **Észlelési szabályok** panelen, ha szeretne, több szabályt is hozzáadhat. Az alkalmazás észleléséhez az **összes** szabály feltételeinek teljesülnie kell.
    >
    > Ha az Intune észleli, hogy az alkalmazás nem található az eszközön, akkor az Intune 24 óra elteltével ismét felajánlja az alkalmazást. Ez csak a kötelező szándékot megcélzó alkalmazások esetében fordul elő.

    - **Észlelési szabályok manuális konfigurálása** – A következő szabálytípusok egyikét választhatja ki:
        1. **MSI** – Jóváhagyás MSI-verzióellenőrzés alapján. Ezt a lehetőséget csak egyszer lehet hozzáadni. Ha ezt a szabálytípust választja, kétféle beállítás áll a rendelkezésére:
            - **MSI-termékkód** – Adjon meg egy érvényes MSI-termékkódot az alkalmazáshoz.
            - **MSI-termékverzió ellenőrzése** – Az **Igen** lehetőség kiválasztásával a rendszer az MSI-termékkód mellett az MSI-termékverziót is ellenőrzi.
        2. **Fájl** – Ellenőrzés a fájl vagy mappa észlelése, dátuma, verziója vagy mérete alapján.
            - **Elérési út** – Az észlelendő fájlt vagy mappát tartalmazó mappa teljes elérési útja.
            - **Fájl vagy mappa** – Az észlelendő fájl vagy mappa.
            - **Észlelési módszer** – Válassza ki az alkalmazás meglétének ellenőrzéséhez használt észlelési módszer típusát.
            - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha 64 bites ügyfeleken a „path” környezeti változókat 32 bites környezetben szeretné kibontani, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer minden „path” változót 64 bites környezetben bontja ki a 64 bites ügyfeleken. A 32 bites ügyfelek mindig a 32 bites környezetet használják.
            
            **Példák a fájlalapú észlelésre**
            1. Fájl meglétének ellenőrzése.
         
                ![Képernyőkép az észlelési szabály paneljéről – a fájl megléte](./media/apps-win32-app-management/apps-win32-app-03.png)
        
            2. Mappa meglétének ellenőrzése.
         
                ![Képernyőkép az észlelési szabály paneljéről – a mappa megléte](./media/apps-win32-app-management/apps-win32-app-04.png)
        
        3. **Beállításjegyzék** – Ellenőrzés érték, sztring, egész szám vagy verzió alapján.
            - **Kulcs elérési útja** – Az észlelendő értéket tartalmazó beállításjegyzék-bejegyzés teljes elérési útja.
            - **Érték neve** – Az észlelendő beállításazonosító neve. Ha ez az érték üres, akkor az észlelés a kulcs alapján történik. A rendszer egy kulcs (alapértelmezett) értékét használja észlelési értékként, ha az észlelési módszer nem a fájl vagy a mappa meglétén alapul.
            - **Észlelési módszer** – Válassza ki az alkalmazás meglétének ellenőrzéséhez használt észlelési módszer típusát.
            - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha a 32 bites beállításjegyzékben szeretne keresni a 64 bites ügyfeleken, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer a 64 bites ügyfeleken a 64 bites beállításjegyzékben fog keresni. A 32 bites ügyfeleknél a keresés mindig a 32 bites beállításjegyzéket érinti.
            
            **Példák a beállításjegyzéken alapuló észlelésre**
            1. A beállításkulcs meglétének ellenőrzése.
            
                ![Képernyőkép az észlelési szabály paneljéről – van beállításkulcs](./media/apps-win32-app-management/apps-win32-app-05.png)    
            
            2. Ellenőrizze, hogy létezik-e a beállításjegyzék-érték.
        
                ![Képernyőkép az észlelési szabály paneljéről – van beállításazonosító](./media/apps-win32-app-management/apps-win32-app-06.png)    
        
            3. A beállításazonosító sztring egyenlőségének ellenőrzése.
        
                ![Képernyőkép az észlelési szabály paneljéről – a beállításazonosító sztring egyenlő](./media/apps-win32-app-management/apps-win32-app-07.png)    
     
    - **Egyéni észlelési szkript alkalmazása** – Adja meg az alkalmazás észleléséhez használandó PowerShell-szkriptet. 
    
        1. **Szkriptfájl** – Válasszon egy PowerShell-szkriptet, amely észleli majd az alkalmazás jelenlétét az ügyfélen. Az alkalmazást a rendszer akkor észleli, ha a szkript egy 0 értékű kilépési kódot ad vissza, és sztringértéket ír az STDOUT elembe.

        2. **Parancsfájl futtatása 32 bites folyamatként 64 bites ügyfeleken** – válassza az **Igen** lehetőséget, ha a parancsfájlt 32 bites folyamaton szeretné futtatni 64 bites ügyfeleken. Válassza a **nem** (alapértelmezett) lehetőséget, hogy a parancsfájlt 64 bites folyamaton futtassa a 64 bites ügyfeleken. 32 bites ügyfelek a szkriptet egy 32 bites folyamatban futtatják.

        3. **Szkriptaláírás ellenőrzésének kényszerítése** – Az **Igen** lehetőség kiválasztásával ellenőrizheti, hogy a szkriptet egy megbízható gyártó írta-e alá, így a szkript figyelmeztetések és felszólítások megjelenítése nélkül fog futni. A szkript letiltás nélkül fog futni. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a szkript végfelhasználói megerősítéssel, az aláírás ellenőrzése nélkül fut.
    
            Az Intune-ügynök ellenőrzi az eredményeket a parancsfájlból. Beolvassa a szkript által a standard kimeneti (STDOUT) streambe írt értékeket, a standard hibastreamet (STDERR) és a kilépési kódot. Ha a szkript egyik értéke nem nulla, akkor a szkript futtatása meghiúsul, és az alkalmazásészlelési állapot nem települ. Ha a kilépési kód nulla, és az STDOUT elemben vannak adatok, akkor az alkalmazásészlelési állapot Telepítve lesz. 

            > [!NOTE]
            > A Microsoft azt javasolja, hogy UTF-8 kódolással kódolja a parancsfájlt. Ha a szkript értéke 0, a végrehajtása sikeres volt. A második kimeneti csatorna alkalmazás észlelését jelzi – az STDOUT-adatok azt jelzik, hogy az alkalmazás megtalálható az ügyfélen. Most nem egy adott sztringet keresünk az STDOUT-ból.

        4. Miután hozzáadta a szabály(ok)at, válassza ki a **Hozzáadás** > **OK** lehetőséget.

### <a name="step-7-configure-app-return-codes"></a>7\. lépés: Alkalmazás-visszatérési kódok konfigurálása

1. Az **Alkalmazás felvétele** panelen válassza a **Visszatérési kódok** lehetőséget az alkalmazástelepítés újrapróbálkozási viselkedését vagy a telepítés utáni viselkedést meghatározó visszatérési kódok hozzáadásához. A visszatérési kód bejegyzéseit a rendszer alapértelmezés szerint hozzáadja az alkalmazás létrehozása során. További visszatérési kódokat is megadhat, és a meglévőket is módosíthatja. 
2. A **Visszatérési kódok** panelen adjon hozzá további visszatérési kódokat, vagy módosítsa a meglévőket.
    - **Sikertelen** – az alkalmazás telepítési hibáját jelző visszatérési érték.
    - **Hardveres újraindítás** – A hardveres újraindítás visszatérési kódja nem engedi meg, hogy a további Win32-alkalmazások újraindítás nélkül legyenek telepíthetők az ügyfélen. 
    - **Szoftveres újraindítás** – A szoftveres újraindítás visszatérési kódja lehetővé teszi, hogy a következő Win32-alkalmazás az ügyfél újraindítása nélkül telepíthető legyen. Az aktuális alkalmazás telepítésének befejezéséhez újraindításra van szükség.
    - **Újrapróbálkozás** – Az újrapróbálkozás visszatérési kód háromszor kísérli meg az alkalmazás telepítését. Az egyes kísérletek közötti 5 percet vár. 
    - **Sikeres** – Ez a visszaadott érték azt jelzi, hogy az alkalmazás telepítése sikeresen megtörtént.
3. Válassza ki az **OK** lehetőséget, miután bővítette vagy módosította a visszatérési kódok listáját.

### <a name="step-8-add-the-app"></a>8\. lépés: Az alkalmazás hozzáadása

1. Az **Alkalmazás hozzáadása** panelen ellenőrizze, hogy helyesen konfigurálta-e az alkalmazásadatokat.
2. Az alkalmazást a **Hozzáadás** elem kiválasztásával töltheti fel az Intune-ba.

### <a name="step-9-assign-the-app"></a>9\. lépés: Az alkalmazás kiosztása

1. Az alkalmazás panelen válassza a **Hozzárendelések** elemet.
2. Válassza a **Csoport hozzáadása** lehetőséget az alkalmazáshoz kapcsolódó **Csoport hozzáadása** ablaktábla megnyitásához.
3. Az adott alkalmazáshoz válasszon egy **hozzárendelés-típust**:
    - **Regisztrálva lévő eszközökhöz érhető el**: A felhasználók a Céges portál alkalmazásból vagy Céges portál webhelyről telepítik az alkalmazást.
    - **Kötelező**: Az alkalmazás a kiválasztott csoportokban található eszközökre van telepítve.
    - **Eltávolítás**: A rendszer eltávolítja az alkalmazást a kiválasztott csoportokból származó eszközökről.
4. Válassza ki a **Tartalmazott csoportok** elemet, és rendelje hozzá a csoportokat, amelyek az alkalmazást fogják használni.
5. Kattintson a **Hozzárendelés** ablaktáblán az **OK** gombra a belefoglalt csoportok kiválasztásának befejezéséhez.
6. Ha ki szeretne zárni felhasználói csoportokat az alkalmazás-hozzárendelésből, válassza a **Csoportok kizárása** lehetőséget.
7. A **Csoport hozzáadása** panelen kattintson az **OK** gombra.
8. Az alkalmazás **Hozzárendelések** ablaktábláján kattintson a **Mentés** gombra.

Ekkor elvégezte a Win32-alkalmazások Intune-hoz való hozzáadásának lépéseit. Az alkalmazás-hozzárendeléssel és monitorozással kapcsolatos további információ: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](apps-deploy.md) és [Alkalmazásadatok és -hozzárendelések figyelése a Microsoft Intune-ban](apps-monitor.md).

## <a name="app-dependencies"></a>Alkalmazás függőségei

Az alkalmazás-függőségek olyan alkalmazások, amelyeket telepíteni kell a Win32-alkalmazás telepítése előtt. Megkövetelheti, hogy más alkalmazások függőségként legyenek telepítve. Pontosabban, az eszköznek a Win32-alkalmazás telepítése előtt telepítenie kell a függő alkalmazást (ka) t. A rendszer legfeljebb 100 függőséget tartalmaz, amely magában foglalja a benne foglalt függőségek függőségeit, valamint magát az alkalmazást. Win32-alkalmazások függőségei csak a Win32-alkalmazás hozzáadása és az Intune-ba való feltöltése után adhatók hozzá. A Win32-alkalmazás hozzáadása után megjelenik a **függőségek** lehetőség a Win32-alkalmazás paneljén. 

A Win32-alkalmazások függőségének is Win32-alkalmazásnak kell lennie. Más típusú alkalmazásoktól, például egyetlen MSI LOB-alkalmazástól vagy áruházbeli alkalmazástól függően nem támogatott.

Alkalmazás-függőség hozzáadásakor az alkalmazás neve és közzétevője alapján kereshet. Emellett az alkalmazás neve és a közzétevője alapján is rendezheti a hozzáadott függőségeket. A korábban hozzáadott alkalmazás-függőségek nem választhatók ki a hozzáadott alkalmazás-függőségek listájában. 

Megadhatja, hogy az egyes függő alkalmazások automatikusan települnek-e. Alapértelmezés szerint az **Automatikus telepítés** beállítás minden függőség esetében az **Igen** értékre van állítva. Ha egy függő alkalmazást automatikusan telepít, még akkor is, ha a függő alkalmazás nem a felhasználóra vagy eszközre irányul, az Intune a Win32-alkalmazás telepítése előtt telepíti az alkalmazást az eszközön. Fontos megjegyezni, hogy a függőség rekurzív alfüggőségekkel is rendelkezhet, és az egyes alrendszerek a fő függőség telepítése előtt lesznek telepítve. Emellett a függőségek telepítése nem követi a telepítési sorrendet egy adott függőségi szinten.

Ha egy alkalmazás-függőséget szeretne hozzáadni a Win32-alkalmazáshoz, kövesse az alábbi lépéseket:

1. Az Intune-ban válassza a **Client apps** > **alkalmazások** lehetőséget a hozzáadott ügyfélalkalmazások listájának megtekintéséhez. 
2. Válassza ki a hozzáadott **Windows-alkalmazás (Win32)** alkalmazást. 
3. A **függőségek** lehetőség kiválasztásával adja hozzá azokat a függő alkalmazás (oka) t, amelyeket a Win32-alkalmazás telepítése előtt telepíteni kell. 
4. Kattintson a **Hozzáadás** gombra az alkalmazás-függőség hozzáadásához.
5. Miután hozzáadta a függő alkalmazást (ka) t, kattintson a **kiválasztás**elemre.
6. Válassza ki, hogy automatikusan szeretné-e telepíteni a függő alkalmazást az **Automatikus telepítés**lehetőségnél az **Igen** vagy a **nem** lehetőség kiválasztásával.
7. Kattintson a **Save** (Mentés) gombra.

A végfelhasználó láthatja, hogy a függő alkalmazások letöltése és telepítése a Win32-alkalmazás telepítési folyamatának részeként történik. Emellett, ha egy függő alkalmazás nincs telepítve, a végfelhasználó általában az alábbi értesítések egyikét fogja látni:
- 1 vagy több függő alkalmazás telepítése nem sikerült
- 1 vagy több függő alkalmazásra vonatkozó követelmény nem teljesül
- 1 vagy több függő alkalmazás is függőben van egy eszköz újraindításakor

Ha úgy dönt, hogy nem **telepít automatikusan** egy függőséget, a rendszer nem kísérli meg a Win32-alkalmazás telepítését. Az alkalmazás-jelentéskészítés emellett azt is megmutatja, hogy a függőség `failed` értékkel lett megjelölve, és a hiba okát is megadja. A függőség telepítési hibáját úgy tekintheti meg, ha a Win 32 alkalmazás [telepítésének részletei](troubleshoot-app-install.md#win32-app-installation-troubleshooting)között a hiba (vagy figyelmeztetés) elemre kattint. 

Minden függőség betartja az Intune Win32-alkalmazás újrapróbálkozási logikáját (próbálja meg 5 perc után 3 alkalommal telepíteni) és a globális újraértékelési ütemtervet. Emellett a függőségek csak a Win32-alkalmazásnak az eszközön való telepítésekor érvényesek. A függőségek nem alkalmazhatók Win32-alkalmazások eltávolítására. A függőségek törléséhez a függőségi lista sorainak végén található függő alkalmazástól balra lévő három pontra kell kattintania. 

## <a name="delivery-optimization"></a>Kézbesítési optimalizálás

A Windows 10 1709 és újabb rendszerű ügyfelek letöltik az Intune Win32-alkalmazás tartalmát egy kézbesítési optimalizálási összetevő használatával a Windows 10-ügyfélen. A kézbesítési optimalizálás a társ-társ funkciókat biztosítja, amelyet alapértelmezés szerint be kell kapcsolni. A kézbesítési optimalizálást a csoportházirend és az Intune-eszköz konfigurációja is konfigurálhatja. További információ: [a Windows 10 kézbesítési optimalizálása](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Kötelező és elérhető alkalmazások telepítése az eszközökön

A végfelhasználó megtekinti a Windows pirítóssal kapcsolatos értesítéseket a szükséges és elérhető alkalmazás-telepítésekhez. Az alábbi képen a bejelentési értesítések egy példája látható, amely szerint az alkalmazás telepítésének befejezéséhez újra kell indítani az eszközt. 

![Képernyőkép az alkalmazás telepítésével kapcsolatos Windows Toast-értesítésekről](./media/apps-win32-app-management/apps-win32-app-08.png)    

A következő rendszerkép értesíti a felhasználót, hogy az alkalmazás megváltoztatja az eszközön végrehajtott módosításokat.

![Képernyőfelvétel a felhasználót arról, hogy az alkalmazás módosításai történnek](./media/apps-win32-app-management/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Bejelentési értesítések a Win32-alkalmazásokhoz 
Ha szükséges, letilthatja az alkalmazás-hozzárendelések végfelhasználói bejelentési értesítéseinek megjelenítését. Az Intune-ból válassza az **ügyfélalkalmazások** > **alkalmazások** lehetőséget > válassza ki az alkalmazást > **hozzárendelések** > **csoportok belefoglalása**. 

> [!NOTE]
> Az Intune felügyeleti bővítmény telepített Win32-alkalmazásai nem lesznek eltávolítva a nem regisztrált eszközökön. A rendszergazdák kihasználhatják a hozzárendelések kizárását, hogy a Win32-alkalmazások ne BYOD eszközöket.

## <a name="troubleshoot-win32-app-issues"></a>A Win32-alkalmazások hibáinak elhárítása
Az ügynöknaplók általában a következő helyen érhetők el az ügyfélgépen: `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. A `CMTrace.exe` segítségével megtekintheti ezeket a naplófájlokat. A *CMTrace. exe* letölthető [Configuration Manager ügyféleszközök](https://docs.microsoft.com/sccm/core/support/tools)közül. 

![Képernyőkép az ügynök naplóiról az ügyfélszámítógépen](./media/apps-win32-app-management/apps-win32-app-10.png)    

> [!IMPORTANT]
> A LOB Win32-alkalmazások megfelelő telepítésének és végrehajtásának engedélyezéséhez a kártevők elleni beállításoknak ki kell zárnia a következő könyvtárakat a vizsgálatból:<p>
> **X64-es ügyfélszámítógépeken**:<br>
> *C:\Program Files (x86) \Microsoft Intune felügyeleti Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **X86-os ügyfélszámítógépeken**:<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>A Win32-alkalmazás fájljának verziója a PowerShell használatával

Ha nehezen észleli a Win32-alkalmazás fájljának verzióját, érdemes lehet a következő PowerShell-parancsot használni vagy módosítani:

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}
```

A fenti PowerShell-parancsban cserélje le a `<path to binary file>` karakterláncot a Win32-alkalmazás elérési útjára. Egy példa elérési útja a következőhöz hasonló lesz:<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

Továbbá cserélje le a `<file version of successfully detected file>` karakterláncot az észleléshez szükséges fájl verziószámára. Egy példa fájlverzió-karakterlánc a következőhöz hasonló:<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Ha le kell kérnie a Win32-alkalmazás verziószámát, a következő PowerShell-parancsot használhatja:

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

A fenti PowerShell-parancsban cserélje le a `<path to binary file>` értéket a fájl elérési útjára.

### <a name="additional-troubleshooting-areas-to-consider"></a>További megfontolandó hibaelhárítási területek
- Ellenőrizze a célcsoportkezelést, és győződjön meg arról, hogy az ügynök telepítve van az eszközön – egy olyan Win32-alkalmazás vagy PowerShell-szkript, amelynek csoport a célzottja, ügynöktelepítési szabályzatot hoz létre a biztonsági csoporthoz.
- Ellenőrizze az operációs rendszer verzióját – 1607-es vagy annál újabb Windows 10-re van szükség.  
- Ellenőrizze a Windows 10 termékváltozatát – a Windows 10 S és az S módban futó Windows-verziók nem támogatják az MSI-telepítést.

A Win32-alkalmazások hibaelhárításával kapcsolatos további információkért lásd: [Win32-alkalmazás telepítésének hibaelhárítása](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>További lépések

- További információk az alkalmazások Intune-hoz való hozzáadásáról: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md).
