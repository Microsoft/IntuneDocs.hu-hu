---
title: Win32-alkalmazások hozzáadása és kiosztása Microsoft Intune
titleSuffix: ''
description: Útmutató Win32-alkalmazások hozzáadásához, hozzárendeléséhez és kezeléséhez Microsoft Intune használatával. E témakör áttekintést nyújt a Win32-alkalmazások telepítési és kezelési lehetőségeiről az Intune-ban, valamint a Win32-alkalmazásokkal kapcsolatos hibák elhárításával kapcsolatban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbefd797fead7113045ee7e7655b715a0b4961fd
ms.sourcegitcommit: 32391f74241ee3289a76ccd5319fe700b800d427
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2020
ms.locfileid: "77075824"
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

   <img alt="Process flow to create a .intunewin file" src="./media/apps-win32-app-management/prepare-win32-app.svg" width="700">

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Futtassa a Microsoft Win32 Content PREP eszközt

Ha paraméterek nélkül futtatja `IntuneWinAppUtil.exe` a parancssori ablakban, az eszköz végigvezeti a szükséges paraméterek lépésről lépésre történő beírásakor. A paramétereket a következő elérhető parancssori paraméterek alapján adhatja hozzá a parancshoz.

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

*. Intunewin* -fájl létrehozásakor helyezzen el minden olyan fájlt, amelyre szüksége van a telepítési mappa almappájára való hivatkozáshoz. Ezután használjon egy relatív elérési utat a szükséges fájlra való hivatkozáshoz. Például:

**Telepítési forrás mappája:** *c:\testapp\v1.0*<br>
**Licencfájl:** *c:\testapp\v1.0\licenses\license.txt*

Tekintse meg a *License. txt* fájlt a relatív elérési út *licenses\license.txt*használatával.

## <a name="create-assign-and-monitor-a-win32-app"></a>Win32-alkalmazás létrehozása, hozzárendelése és monitorozása

Az üzletági (LOB) alkalmazásokhoz hasonlóan Win32-alkalmazást is hozzáadhat a Microsoft Intune-hoz. Az ilyen alkalmazásokat általában házon belül írják, vagy egy külső féltől származnak. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Folyamat feldolgozása Win32-alkalmazás hozzáadásához az Intune-ban

<img alt="Process flow to add a Win32 app to Intune" src="./media/apps-win32-app-management/add-win32-app.svg" width="500">

### <a name="add-a-win32-app-to-intune"></a>Win32-alkalmazás hozzáadása az Intune-hoz

Az alábbi lépések útmutatást nyújtanak a Windows-alkalmazások Intune-hoz való hozzáadásához.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán a **többi** alkalmazás típusa területen válassza a **Windows-alkalmazás (Win32)** lehetőséget.

    > [!IMPORTANT]
    > Ügyeljen arra, hogy a Microsoft Win32 Content PREP eszköz legújabb verzióját használja. Ha nem a legújabb verziót használja, egy figyelmeztetés jelenik meg, amely jelzi, hogy az alkalmazás a Microsoft Win32 Content PREP Tool egy régebbi verziójával lett csomagolva. 

4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **alkalmazás hozzáadása** lépések.

## <a name="step-1---app-information"></a>1\. lépés – alkalmazás adatai

### <a name="select-the-app-package-file"></a>Válassza ki az alkalmazáscsomag-fájlt

1. Az **alkalmazás hozzáadása** panelen kattintson az **alkalmazáscsomag-fájl kiválasztása**lehetőségre. 
2. Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ezt követően jelölje ki az *.intunewin* kiterjesztésű Windows-telepítőfájlt.
   Ekkor megjelenik az alkalmazás részletei.
3. Ha elkészült, kattintson az **OK gombra** az **alkalmazáscsomag fájl** paneljén.

### <a name="set-app-information"></a>Alkalmazás adatainak megadása

1. Az **alkalmazás adatai** lapon adja meg az alkalmazás részleteit. A választott alkalmazástól függően előfordulhat, hogy egyes értékek automatikusan ki vannak töltve a panelen.
    - **Név**: Itt adhatja meg az alkalmazás a Céges portálon megjelenő nevét. Ügyeljen arra, hogy a megadott alkalmazásnevek egyediek legyenek. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a Céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás megjelenik a Céges portálon.
    - **Kiadó**: Adja meg az alkalmazás kiadójának nevét.
    - **Kategória**: Választhat egyet vagy többet a beépített kategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. A kategóriákkal megkönnyítheti a felhasználók számára az alkalmazás megkeresését a Céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portál**: az alkalmazás megjelenítése a vállalati portál főoldalán, amikor a felhasználók megkeresik az alkalmazásokat.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Fejlesztő**: Igény esetén megadhatja az alkalmazás fejlesztőjének nevét.
    - **Tulajdonos**: Igény esetén megadhatja az alkalmazás tulajdonosának nevét. Például **HR részleg**.
    - **Megjegyzések**: Ide írhatja be az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Ikon**: Itt töltheti fel az alkalmazáshoz társított ikont. Ez az ikon jelenik meg az alkalmazásnál a Céges portálon böngésző felhasználók számára.
2. A **program** lap megjelenítéséhez kattintson a **tovább** gombra.

## <a name="step-2-program"></a>2\. lépés: program

1. A **program** lapon konfigurálja az alkalmazás telepítési és eltávolítási parancsait:
    - Telepítési **parancs**: adja hozzá a teljes telepítési parancssort az alkalmazás telepítéséhez. 

        Ha például az alkalmazás fájlneve **MyApp123**, adja hozzá a következőt:<br>
        `msiexec /p “MyApp123.msp”`<p>
        Ha pedig az alkalmazás `ApplicationName.exe`, a parancs az alkalmazás neve, amelyet a csomag által támogatott parancs-argumentumok (kapcsolók) követnek. <br>Például:<br>
        `ApplicationName.exe /quiet`<br>
        A fenti parancsban a `ApplicationName.exe` csomag támogatja a `/quiet` Command argumentumot.<p> 
        Az alkalmazáscsomag által támogatott argumentumok esetében forduljon az alkalmazás forgalmazójához.

    - **Eltávolítási parancs**: a teljes eltávolítási parancssor hozzáadásával távolítsa el az alkalmazást az alkalmazás GUID azonosítója alapján. 

        Például: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    - **Telepítési viselkedés**: állítsa be a telepítési viselkedést a **rendszer** vagy a **felhasználó**számára.

        > [!NOTE]
        > Az adott Win32-alkalmazás telepítését a **Felhasználó** vagy a **Rendszer** környezetben konfigurálhatja. A **Felhasználó** környezet csak az adott felhasználóra vonatkozik. A **Rendszer** környezet az adott, Windows 10-es rendszerű eszköz összes felhasználójára vonatkozik.
        >
        > A végfelhasználóknak nem kell bejelentkezniük az eszközön a Win32-alkalmazások telepítéséhez.
        > 
        > A Win32-alkalmazás telepítése és eltávolítása a rendszergazdai jogosultságok alatt történik (alapértelmezés szerint), ha az alkalmazás felhasználói környezetben történő telepítésre van beállítva, és az eszköz végfelhasználója rendszergazdai jogosultságokkal rendelkezik.
    
    - **Eszköz újraindításának viselkedése**: válasszon a következő lehetőségek közül:
        - **Viselkedés meghatározása a visszatérési kódok alapján**: válassza ezt a lehetőséget, ha újra szeretné indítani az eszközt a visszatérési kódok alapján.
        - **Nincs konkrét művelet**: válassza ezt a lehetőséget, ha el szeretné tiltani az eszköz újraindítását az MSI-alapú alkalmazások telepítésekor.
        - Az **alkalmazás telepítése kényszerítheti az eszköz újraindítását**: ezzel a beállítással engedélyezheti, hogy az alkalmazás telepítése az újraindítások mellőzése nélkül befejeződjön.
        - Az **Intune a kötelező eszköz újraindítását kényszeríti**: válassza ezt a lehetőséget, ha az alkalmazás sikeres telepítése után mindig újraindítja az eszközt.

    - **Adja meg a visszatérési kódokat a telepítés utáni viselkedés jelzéséhez**: adja meg az alkalmazás telepítésének újrapróbálkozási viselkedését vagy a telepítés utáni viselkedését megadó visszatérési kódokat. A visszatérési kód bejegyzéseit a rendszer alapértelmezés szerint hozzáadja az alkalmazás létrehozása során. További visszatérési kódokat is megadhat, és a meglévőket is módosíthatja.
        1. A **kód típusa** oszlopban állítsa be a **kód típusát** a következők egyikére:
            - **Sikertelen** – az alkalmazás telepítési hibáját jelző visszatérési érték.
            - **Hardveres újraindítás** – A hardveres újraindítás visszatérési kódja nem engedi meg, hogy a további Win32-alkalmazások újraindítás nélkül legyenek telepíthetők az ügyfélen. 
            - **Szoftveres újraindítás** – A szoftveres újraindítás visszatérési kódja lehetővé teszi, hogy a következő Win32-alkalmazás az ügyfél újraindítása nélkül telepíthető legyen. Az aktuális alkalmazás telepítésének befejezéséhez újraindításra van szükség.
            - **Újrapróbálkozás** – Az újrapróbálkozás visszatérési kód háromszor kísérli meg az alkalmazás telepítését. Az egyes kísérletek közötti 5 percet vár. 
            - **Sikeres** – Ez a visszaadott érték azt jelzi, hogy az alkalmazás telepítése sikeresen megtörtént.
        2. Ha szükséges, kattintson a **Hozzáadás** gombra további visszatérési kódok hozzáadásához vagy a meglévő visszatérési kódok módosításához.
2. Kattintson a **tovább** gombra a **követelmények** lap megjelenítéséhez.        

## <a name="step-3-requirements"></a>3\. lépés: követelmények

1. A **követelmények** lapon határozza meg, hogy az eszközöknek milyen követelményeknek kell megfelelniük az alkalmazás telepítése előtt:
    - **Operációs rendszer architektúrája**: Válassza ki az alkalmazás telepítéséhez szükséges architektúrákat.
    - **Minimális operációsrendszer-verzió**: Válassza ki az operációs rendszer verziószámát, amely minimumkövetelményként szükséges az alkalmazás telepítéséhez.
    - **Szükséges lemezterület (MB)** : Opcionálisan megadhatja, hogy a rendszermeghajtón mekkora szabad lemezterületnek kell rendelkezésre állnia az alkalmazás telepítéséhez.
    - **Szükséges fizikai memória (MB)** : Opcionálisan megadhatja, hogy mekkora fizikai memória (RAM) szükséges az alkalmazás telepítéséhez.
    - **Logikai processzorok szükséges minimális száma**: Opcionálisan megadhatja az alkalmazás telepítéséhez szükséges logikai processzorok minimális számát.
    - **Szükséges minimális processzorsebesség (MHz)** : Opcionálisan megadhatja az alkalmazás telepítéséhez szükséges minimális processzorsebességet.
    - **További követelmények szabályainak konfigurálása**: 
        1. A **Hozzáadás** gombra kattintva jelenítse meg az **Add a követelményi szabály** panelt, és konfigurálja a további követelmények szabályait. Válassza ki a **követelmény típusát** annak a szabálynak a kiválasztásához, amelyet a követelmények érvényesítésének meghatározásához fog használni. A követelmények szabályai a fájlrendszer adatai, a beállításjegyzék értékei vagy a PowerShell-parancsfájlok alapján is alapulhatnak. 
            - **Fájl**: Ha a **követelmény típusaként**a **fájl** lehetőséget választja, a követelmény szabálynak egy fájlt vagy mappát, dátumot, verziót vagy méretet kell felderíteni. 
                - **Elérési út** – Az észlelendő fájlt vagy mappát tartalmazó mappa teljes elérési útja.
                - **Fájl vagy mappa** – Az észlelendő fájl vagy mappa.
                - **Tulajdonság** – válassza ki az alkalmazás meglétének ellenőrzéséhez használt szabály típusát.
                - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha 64 bites ügyfeleken a „path” környezeti változókat 32 bites környezetben szeretné kibontani, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer minden „path” változót 64 bites környezetben bontja ki a 64 bites ügyfeleken. A 32 bites ügyfelek mindig a 32 bites környezetet használják.
            - **Beállításjegyzék**: Ha a **beállításjegyzéket** a **követelmény típusaként**választja, a követelmény szabályának az érték, a karakterlánc, az egész szám vagy a verzió alapján kell megállapítania egy beállításjegyzék-beállítást.
                - **Kulcs elérési útja** – Az észlelendő értéket tartalmazó beállításjegyzék-bejegyzés teljes elérési útja.
                - **Érték neve** – Az észlelendő beállításazonosító neve. Ha ez az érték üres, akkor az észlelés a kulcs alapján történik. A rendszer egy kulcs (alapértelmezett) értékét használja észlelési értékként, ha az észlelési módszer nem a fájl vagy a mappa meglétén alapul.
                - **Beállításkulcs követelménye** – válassza ki a beállításkulcs összehasonlításának típusát, amely meghatározza a követelmény szabályának érvényességét.
                - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha a 32 bites beállításjegyzékben szeretne keresni a 64 bites ügyfeleken, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer a 64 bites ügyfeleken a 64 bites beállításjegyzékben fog keresni. A 32 bites ügyfeleknél a keresés mindig a 32 bites beállításjegyzéket érinti.
            - **Parancsfájl**: a **parancsfájlt** a **követelmény típusaként**válassza, ha a fájlon, a beállításjegyzéken vagy az Intune-konzolon elérhető bármely más módszeren alapuló követelmény-szabály nem hozható létre.
                - **Parancsfájl** – a PowerShell parancsfájl-alapú követelményi szabályához (ha létezik kód 0), a rendszer részletesebben felderíti az stdout-ot. Például észlelhető az STDOUT olyan egész számként, amelynek értéke 1.
                - **Parancsfájl futtatása 32 bites folyamatként 64 bites ügyfeleken** – válassza az **Igen** lehetőséget, ha a parancsfájlt 32 bites folyamaton szeretné futtatni 64 bites ügyfeleken. Válassza a **nem** (alapértelmezett) lehetőséget, hogy a parancsfájlt 64 bites folyamaton futtassa a 64 bites ügyfeleken. 32 bites ügyfelek a szkriptet egy 32 bites folyamatban futtatják.
                - **Futtassa ezt a parancsfájlt a bejelentkezett hitelesítő adatok használatával**: válassza az **Igen** lehetőséget a szkript futtatásához a bejelentkezett eszköz hitelesítő adatai * * használatával.
                - **Szkriptaláírás ellenőrzésének kényszerítése** – Az **Igen** lehetőség kiválasztásával ellenőrizheti, hogy a szkriptet egy megbízható gyártó írta-e alá, így a szkript figyelmeztetések és felszólítások megjelenítése nélkül fog futni. A szkript letiltás nélkül fog futni. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a szkript végfelhasználói megerősítéssel, az aláírás ellenőrzése nélkül fut.
                - **Válassza ki a kimeneti adattípust**: válassza ki a követelményi szabály egyezésének meghatározásakor használt adattípust.
        2. Ha végzett a követelmények szabályainak beállításával, kattintson **az OK gombra**.
2. Az **észlelési szabályok** lap megjelenítéséhez kattintson a **tovább** gombra.   

## <a name="step-4-detection-rules"></a>4\. lépés: észlelési szabályok

1. Az **észlelési szabályok** lapon konfigurálja a szabályokat az alkalmazás jelenlétének észleléséhez:
    
    **Szabályok formátuma**: válassza ki, hogyan fogja észlelni az alkalmazás jelenlétét. Választhatja az észlelési szabályok manuális konfigurálását, illetve egyéni szkriptet is használhat az alkalmazás meglétének észleléséhez. Legalább egy észlelési szabályt ki kell választani. 

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

2. A szabály (ok) hozzáadása után kattintson a **tovább** gombra a **függőségek** lap megjelenítéséhez.

## <a name="step-5-dependencies"></a>5\. lépés: függőségek

Az alkalmazás-függőségek olyan alkalmazások, amelyeket telepíteni kell a Win32-alkalmazás telepítése előtt. Megkövetelheti, hogy más alkalmazások függőségként legyenek telepítve. Pontosabban, az eszköznek a Win32-alkalmazás telepítése előtt telepítenie kell a függő alkalmazást (ka) t. A rendszer legfeljebb 100 függőséget tartalmaz, amely magában foglalja a benne foglalt függőségek függőségeit, valamint magát az alkalmazást. Win32-alkalmazások függőségei csak a Win32-alkalmazás hozzáadása és az Intune-ba való feltöltése után adhatók hozzá. Miután hozzáadta a Win32-alkalmazást, megjelenik a **függőségek** lehetőség a Win32-alkalmazás ablaktábláján. 

A Win32-alkalmazások függőségének is Win32-alkalmazásnak kell lennie. Más típusú alkalmazásoktól, például egyetlen MSI LOB-alkalmazástól vagy áruházbeli alkalmazástól függően nem támogatott.

Alkalmazás-függőség hozzáadásakor az alkalmazás neve és közzétevője alapján kereshet. Emellett az alkalmazás neve és a közzétevője alapján is rendezheti a hozzáadott függőségeket. A korábban hozzáadott alkalmazás-függőségek nem választhatók ki a hozzáadott alkalmazás-függőségek listájában. 

Megadhatja, hogy az egyes függő alkalmazások automatikusan települnek-e. Alapértelmezés szerint az **Automatikus telepítés** beállítás minden függőség esetében az **Igen** értékre van állítva. Ha egy függő alkalmazást automatikusan telepít, még akkor is, ha a függő alkalmazás nem a felhasználóra vagy eszközre irányul, az Intune a Win32-alkalmazás telepítése előtt telepíti az alkalmazást az eszközön. Fontos megjegyezni, hogy a függőség rekurzív alfüggőségekkel is rendelkezhet, és az egyes alrendszerek a fő függőség telepítése előtt lesznek telepítve. Emellett a függőségek telepítése nem követi a telepítési sorrendet egy adott függőségi szinten.

### <a name="select-the-dependencies"></a>A függőségek kiválasztása

A **függőségek** lapon válassza ki azokat az alkalmazásokat, amelyeket telepíteni kell a Win32-alkalmazás telepítése előtt:
1. Kattintson a **Hozzáadás** gombra a **függőség hozzáadása** ablaktábla megjelenítéséhez.
3. Miután hozzáadta a függő alkalmazást (ka) t, kattintson a **kiválasztás**elemre.
4. Válassza ki, hogy szeretné-e automatikusan telepíteni a függő alkalmazást az **Automatikus telepítés** oszlopban az **Igen** vagy a **nem** lehetőség kiválasztásával.
5. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.

### <a name="understand-additional-dependency-details"></a>További függőség részleteinek megismerése

A végfelhasználó láthatja, hogy a függő alkalmazások letöltése és telepítése a Win32-alkalmazás telepítési folyamatának részeként történik. Emellett, ha egy függő alkalmazás nincs telepítve, a végfelhasználó általában az alábbi értesítések egyikét fogja látni:
- 1 vagy több függő alkalmazás telepítése nem sikerült
- 1 vagy több függő alkalmazásra vonatkozó követelmény nem teljesül
- 1 vagy több függő alkalmazás is függőben van egy eszköz újraindításakor

Ha úgy dönt, hogy nem **telepít automatikusan** egy függőséget, a rendszer nem kísérli meg a Win32-alkalmazás telepítését. Az alkalmazás-jelentéskészítés emellett azt is megmutatja, hogy a függőség `failed`ként van megjelölve, és a hiba okát is megadja. A függőség telepítési hibáját úgy tekintheti meg, ha a Win 32 alkalmazás [telepítésének részletei](troubleshoot-app-install.md#win32-app-installation-troubleshooting)között a hiba (vagy figyelmeztetés) elemre kattint. 

Minden függőség betartja az Intune Win32-alkalmazás újrapróbálkozási logikáját (próbálja meg 5 perc után 3 alkalommal telepíteni) és a globális újraértékelési ütemtervet. Emellett a függőségek csak a Win32-alkalmazásnak az eszközön való telepítésekor érvényesek. A függőségek nem alkalmazhatók Win32-alkalmazások eltávolítására. A függőségek törléséhez a függőségi lista sorainak végén található függő alkalmazástól balra lévő három pontra kell kattintania. 

## <a name="step-6---select-scope-tags-optional"></a>6\. lépés – hatókör-címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).

1. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye a hatókör címkéit az alkalmazáshoz. 
2. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.

## <a name="step-7---assignments"></a>7\. lépés – hozzárendelések

Kiválaszthatja a **szükséges**, a **regisztrált eszközök számára elérhető**, illetve az alkalmazáshoz tartozó hozzárendelések **eltávolítását** is. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md) , valamint [alkalmazások társítása a csoportokhoz Microsoft Intune](apps-deploy.md)használatával.

1. Az adott alkalmazáshoz válasszon egy hozzárendelési típust:
    - **Szükséges**: A rendszer telepíti az alkalmazást a kiválasztott csoportok eszközeire.
    - **Regisztrált eszközök esetében elérhető**: A felhasználók a Céges portál alkalmazásban vagy a Céges portál webhelyen telepítik az alkalmazást.
    - **Eltávolítás**: A rendszer eltávolítja az alkalmazást a kiválasztott csoportok eszközeiről.
2. Kattintson a **Csoport hozzáadása** elemre, és rendelje hozzá az alkalmazást használó csoportokat.
3. A **csoportok kiválasztása** panelen válassza ki a hozzárendelést felhasználók vagy eszközök alapján. 
4. A csoportok kiválasztása után megadhatja a **végfelhasználói értesítéseket**, a **rendelkezésre állást**és a **telepítési határidőt**is. További információ: [Win32-alkalmazás rendelkezésre állásának és értesítéseinek beállítása](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).
5. Ha ki szeretné zárni az alkalmazás-hozzárendelés által érintett felhasználói csoportokat, válassza a a **Mode (mód** ) oszlopban **található** elemet. Ekkor megjelenik a **hozzárendelés szerkesztése** ablaktábla. Beállíthatja, hogy a **mód** ne **szerepeljen** a **kizárásban**. A **hozzárendelés szerkesztése** ablaktábla bezárásához kattintson **az OK** gombra.
6. Miután befejezte az alkalmazások hozzárendeléseinek beállítását, kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez.

## <a name="step-8---review--create"></a>8\. lépés – felülvizsgálat + létrehozás

1. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat. Ellenőrizze, hogy helyesen konfigurálta-e az alkalmazás adatait.
2. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

    Megjelenik az üzletági alkalmazás **Áttekintés** panelje.

Ekkor elvégezte a Win32-alkalmazások Intune-hoz való hozzáadásának lépéseit. Az alkalmazás-hozzárendeléssel és monitorozással kapcsolatos további információ: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](apps-deploy.md) és [Alkalmazásadatok és -hozzárendelések figyelése a Microsoft Intune-ban](apps-monitor.md).

## <a name="delivery-optimization"></a>Kézbesítési optimalizálás

A Windows 10 1709 és újabb rendszerű ügyfelek letöltik az Intune Win32-alkalmazás tartalmát egy kézbesítési optimalizálási összetevő használatával a Windows 10-ügyfélen. A kézbesítési optimalizálás a társ-társ funkciókat biztosítja, amelyet alapértelmezés szerint be kell kapcsolni. A kézbesítési optimalizálást a csoportházirend és az Intune-eszköz konfigurációja is konfigurálhatja. További információ: [a Windows 10 kézbesítési optimalizálása](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

> [!NOTE]
> A Microsoft csatlakoztatott gyorsítótár-kiszolgálót a Configuration Manager terjesztési pontokon is telepítheti az Intune Win32-alkalmazás tartalmának gyorsítótárazásához. További információ: a [Microsoft csatlakoztatott gyorsítótára Configuration Manager – az Intune Win32-alkalmazások támogatása](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

## <a name="install-required-and-available-apps-on-devices"></a>Kötelező és elérhető alkalmazások telepítése az eszközökön

A végfelhasználó megtekinti a Windows pirítóssal kapcsolatos értesítéseket a szükséges és elérhető alkalmazás-telepítésekhez. Az alábbi képen a bejelentési értesítések egy példája látható, amely szerint az alkalmazás telepítésének befejezéséhez újra kell indítani az eszközt. 

![Képernyőkép az alkalmazás telepítésével kapcsolatos Windows Toast-értesítésekről](./media/apps-win32-app-management/apps-win32-app-08.png)    

A következő rendszerkép értesíti a felhasználót, hogy az alkalmazás megváltoztatja az eszközön végrehajtott módosításokat.

![Képernyőfelvétel a felhasználót arról, hogy az alkalmazás módosításai történnek](./media/apps-win32-app-management/apps-win32-app-09.png)    

## <a name="set-win32-app-availability-and-notifications"></a>Win32-alkalmazás rendelkezésre állásának és értesítéseinek beállítása
Beállíthatja a Win32-alkalmazás kezdési idejét és határidejét. A kezdési időpontban az Intune felügyeleti bővítmény elindítja az alkalmazás tartalmának letöltését, és gyorsítótárazza azt a szükséges szándék érdekében. Az alkalmazás a határidő lejártakor lesz telepítve. Az elérhető alkalmazások esetében a kezdési idő akkor fog megjelenni, ha az alkalmazás megjelenik a Céges portálban, és a tartalom le lesz töltve, amikor a végfelhasználó a Céges portáltól kéri az alkalmazást. Emellett engedélyezheti az újraindítási türelmi időszakot is. 

Az alkalmazás rendelkezésre állását a szükséges alkalmazások dátum és idő alapján, a következő lépésekkel állíthatja be:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás**lehetőséget.
3. Válasszon ki egy meglévő **Windows-alkalmazást (Win32)** a listából. 
4. Az alkalmazás ablaktáblán válassza a **tulajdonságok** > **Szerkesztés** elemet a **hozzárendelések** szakasz mellett > **adja hozzá a csoportot** a **szükséges** hozzárendelési típus alatt. 
   Vegye figyelembe, hogy az alkalmazás rendelkezésre állása a hozzárendelés típusa alapján állítható be. A **hozzárendelés típusa** **kötelező**, **regisztrált eszközökhöz**vagy **eltávolításhoz**érhető el.
5. Válasszon ki egy csoportot a **csoport kiválasztása** ablaktáblán annak megadásához, hogy az alkalmazás melyik felhasználói csoporthoz lesz hozzárendelve. 

    > [!NOTE]
    > A **hozzárendelési típus** beállításai a következőket foglalják magukban:<br>
    > - **Kötelező**: megadhatja, hogy **az alkalmazás minden felhasználó számára kötelező legyen** , és/vagy **minden eszközön kötelezővé tegye az alkalmazást**.<br>
    > - **Regisztrálva lévő eszközökhöz elérhető**: megadhatja, hogy **az alkalmazás elérhető legyen az összes regisztrált eszközzel rendelkező felhasználó**számára.<br>
    > - **Eltávolítás**: kiválaszthatja, hogy az**alkalmazást eltávolítja-e az összes felhasználó** számára, és/vagy **távolítsa el az alkalmazást minden eszközön**.

6. Ha módosítani szeretné a **végfelhasználói értesítési** beállításokat, válassza az összes bejelentési **értesítés megjelenítése**lehetőséget.
7. A **hozzárendelés szerkesztése** panelen állítsa be a **Ender felhasználói értesítéseket** az **összes bejelentési értesítés megjelenítéséhez**. Vegye figyelembe, hogy az összes bejelentési **értesítés**megjelenítéséhez beállíthatja a **végfelhasználói értesítéseket** , megtekintheti **a számítógép újraindítására és a** **bejelentések összes értesítését**.
8. Állítsa be az **alkalmazás rendelkezésre állását** **egy adott dátumra és** időpontra, és válassza ki a dátumot és az időt. Ez a dátum és idő határozza meg, hogy az alkalmazás Mikor töltődik le a végfelhasználói eszközre. 
9. Állítsa be az **alkalmazás telepítési határidejét** **egy adott dátumra és időpontra** , és válassza ki a dátumot és az időt. Ez a dátum és idő határozza meg, hogy az alkalmazás Mikor van telepítve a végfelhasználói eszközön. Ha ugyanahhoz a felhasználóhoz vagy eszközhöz több hozzárendelés is készül, az alkalmazás telepítési határideje a lehető legkorábbi időpont alapján lesz kiválasztva.

10. Az **Újraindítási türelmi időszak**mellett kattintson az **engedélyezve** lehetőségre. Az újraindítási türelmi időszak akkor indul el, amikor az alkalmazás telepítése befejeződött az eszközön. Ha le van tiltva, az eszköz figyelmeztetés nélkül indítható újra. <br>A következő beállításokat szabhatja testre:
    - **Eszköz újraindításának türelmi időszaka (perc)** : az alapértelmezett érték 1440 perc (24 óra). Ez az érték legfeljebb 2 hétig lehet.
    - **Válassza ki, hogy mikor jelenjen meg az újraindítási visszaszámlálás párbeszédpanel az újraindítás megkezdése előtt (perc)** : az alapértelmezett érték 15 perc.
    - **Az újraindítási értesítés késleltetésének engedélyezése a felhasználó számára: az** **Igen** vagy a **nem**lehetőséget is választhatja.
        - **Válassza ki a késleltetés időtartamát (perc)** : az alapértelmezett érték 240 perc (4 óra). A késleltetési érték nem lehet nagyobb, mint az újraindítási türelmi időszak.

11. Kattintson a **felülvizsgálat + mentés**gombra.

## <a name="toast-notifications-for-win32-apps"></a>Bejelentési értesítések a Win32-alkalmazásokhoz 
Ha szükséges, letilthatja az alkalmazás-hozzárendelések végfelhasználói bejelentési értesítéseinek megjelenítését. Az Intune-ból válassza az **alkalmazások** > **minden alkalmazás** lehetőséget, > válassza ki az alkalmazás > **hozzárendelések** > **csoportok**lehetőséget. 

> [!NOTE]
> Az Intune felügyeleti bővítmény telepített Win32-alkalmazásai nem lesznek eltávolítva a nem regisztrált eszközökön. A rendszergazdák kihasználhatják a hozzárendelések kizárását, hogy a Win32-alkalmazások ne BYOD eszközöket.

## <a name="troubleshoot-win32-app-issues"></a>A Win32-alkalmazások hibáinak elhárítása
Az ügynöknaplók általában a következő helyen érhetők el az ügyfélgépen: `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. A `CMTrace.exe` segítségével megtekintheti ezeket a naplófájlokat. További információ: [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace).

![Képernyőkép az ügynök naplóiról az ügyfélszámítógépen](./media/apps-win32-app-management/apps-win32-app-10.png)    

> [!IMPORTANT]
> A LOB Win32-alkalmazások megfelelő telepítésének és végrehajtásának engedélyezéséhez a kártevők elleni beállításoknak ki kell zárnia a következő könyvtárakat a vizsgálatból:<p>
> **X64-es ügyfélszámítógépeken**:<br>
> *C:\Program Files (x86) \Microsoft Intune felügyeleti Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **X86-os ügyfélszámítógépeken**:<br>
> *C:\Program Files\Microsoft Intune felügyeleti Extension\Content*<br>
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

A fenti PowerShell-parancsban cserélje le a `<path to binary file>`t a fájl elérési útjára.

### <a name="additional-troubleshooting-areas-to-consider"></a>További megfontolandó hibaelhárítási területek
- Ellenőrizze a célcsoportkezelést, és győződjön meg arról, hogy az ügynök telepítve van az eszközön – egy olyan Win32-alkalmazás vagy PowerShell-szkript, amelynek csoport a célzottja, ügynöktelepítési szabályzatot hoz létre a biztonsági csoporthoz.
- Ellenőrizze az operációs rendszer verzióját – 1607-es vagy annál újabb Windows 10-re van szükség.  
- Ellenőrizze a Windows 10 termékváltozatát – a Windows 10 S és az S módban futó Windows-verziók nem támogatják az MSI-telepítést.

A Win32-alkalmazások hibaelhárításával kapcsolatos további információkért lásd: [Win32-alkalmazás telepítésének hibaelhárítása](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>További lépések

- További információk az alkalmazások Intune-hoz való hozzáadásáról: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md).
