---
title: MacOS-es üzletági alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Útmutató macOS rendszerű üzletági (LOB) alkalmazások Microsoft Intunehoz való hozzáadásához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9802b85a9674535cea62ae28f135153352ef76c
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813263"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>MacOS-es üzletági (LOB) alkalmazások hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikkben található információ segítségével macOS rendszerű üzletági alkalmazásokat adhat hozzá a Microsoft Intune-hoz. Le kell töltenie egy külső eszközt a *.pkg*-fájlok előzetes feldolgozásához, mielőtt feltölthetné üzletági fájlját a Microsoft Intune-ba. A *.pkg*-fájlok előzetes feldolgozását macOS-eszközön kell elvégezni.

> [!NOTE]
> Bár az macOS-eszközök felhasználói eltávolíthatnak néhányat a beépített macOS-alkalmazások közül – például a Részvények vagy a Térképek alkalmazást –, az Intune nem használható ezek újratelepítésére. Amennyiben a végfelhasználó törölte ezeket az alkalmazásokat, manuálisan telepítheti újra őket az App Store áruházból.

## <a name="before-your-start"></a>Előkészületek

Le kell töltenie egy külső eszközt, meg kell jelölnie a letöltött eszközt végrehajtható fájlként, és előre fel kell dolgoznia a *. pkg* -fájlokat az eszközzel, mielőtt feltölti az üzletági fájlt a Microsoft Intuneba. A *.pkg*-fájlok előzetes feldolgozását macOS-eszközön kell elvégezni. Az Intune App Wrapping Tool for Mac eszközzel engedélyezheti a Mac-alkalmazások Microsoft Intune általi felügyeletét.

> [!IMPORTANT]
> A *. pkg* fájlt a "fejlesztői azonosító telepítőjének" tanúsítvány használatával kell aláírni, amely egy Apple Developer-fiókból származik. MacOS LOB-alkalmazások Microsoft Intune-ba való feltöltésére csak *.pkg*-fájlok használhatók. A más formátumokra (például *.dmg* vagy *.pkg*) való konvertálás nincs támogatva.
>

1. Töltse le a [Mac Intune alkalmazás-burkoló eszközét](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > Az **Intune App Wrapping Tool for Mac** eszközt macOS-gépen kell futtatni. 

2. A letöltött eszköz megjelölése végrehajtható fájlként:
   - Indítsa el a terminál alkalmazást.
   - Módosítsa a könyvtárat arra a helyre, ahol a `IntuneAppUtil` található.
   - Futtassa az alábbi parancsot az eszköz végrehajtható fájljának elvégzéséhez:<br> 
       `chmod +x IntuneAppUtil`

3. Használja az `IntuneAppUtil` parancsot az **Intune App Wrapping Tool for Mac** eszközben *.pkg* kiterjesztésű LOB-alkalmazásfájlok *.intunemac*-fájlból való burkolásához.<br>

    Példaparancsok a Microsoft Intune App Wrapping Tool for macOS eszközhöz:
    
    - `IntuneAppUtil -h`<br>
    Ez a parancs megjeleníti az eszköz használatára vonatkozó információkat.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Ez a parancs *.pkg* kiterjesztésű üzletági alkalmazásfájlt burkol *.intunemac*-fájlba.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Ez a parancs kibontja a felderített paramétereket és verziót a létrehozott *.intunemac*-fájlhoz.

## <a name="step-1---specify-the-software-setup-file"></a>1\. lépés – A szoftvertelepítő fájl megadása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** munkaterületen válassza a **Kezelés** > **Alkalmazások** elemet.
5. Az alkalmazások listája fölött válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazás hozzáadása** panelen válassza az **Üzletági alkalmazás** lehetőséget.

## <a name="step-2---configure-the-app-package-file"></a>2\. lépés – az alkalmazáscsomag-fájl konfigurálása

1. Az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazáscsomag** fájlt.
2. Az **Alkalmazáscsomag**-fájl ablaktáblán válassza a tallózás gombot, majd válasszon egy *.intunemac* kiterjesztésű macOS-es telepítési fájlt.
3. Ha elkészült, válassza az **OK** elemet.


## <a name="step-3---configure-app-information"></a>3\. lépés – Az alkalmazás adatainak konfigurálása

1. Az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazásadatok** lehetőséget.
2. Az **Alkalmazás adatai** panelen adja meg az alkalmazásadatokat. A választott alkalmazástól függően előfordulhat, hogy egyes értékek automatikusan ki vannak töltve a panelen:
    - **Név** – Itt adhatja meg az alkalmazás céges portálon megjelenő nevét. Ügyeljen arra, hogy a megadott alkalmazásnevek egyediek legyenek. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a vállalati portálon.
    - **Leírás** – Adja meg az alkalmazás leírását, amelyet a felhasználók is láthatnak majd a céges portálon.
    - **Kiadó** – Adja meg az alkalmazás kiadójának nevét.
    - **Minimális operációsrendszer-verzió** – A listából kiválaszthatja az operációs rendszer legrégebbi olyan verzióját, amelyre az alkalmazás telepíthető. Ha az alkalmazást régebbi operációs rendszerrel rendelkező eszközhöz rendelik hozzá, akkor nem lesz telepítve.
    - **Kategória** – Választhat egyet vagy többet a beépített kategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Így megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés kiemelt alkalmazásként a Céges portálon** – Ezzel a beállítással hangsúlyosan jelenítheti meg az alkalmazást a Céges portál főoldalán alkalmazásokat kereső felhasználók számára.
    - **Információs URL-cím** – Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe** – Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő** – Igény esetén megadhatja az alkalmazás fejlesztőjének nevét.
    - **Tulajdonos** – Igény esetén megadhatja az alkalmazás tulajdonosának nevét (például **HR-osztály**).
    - **Megjegyzések** – Ide írhatja be az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Ikon** – Itt töltheti fel az alkalmazáshoz hozzárendelni kívánt ikont. Ez az alkalmazásikon jelenik meg a vállalati portálon böngésző felhasználók számára.
3. Ha elkészült, válassza az **OK** elemet.

## <a name="step-4---finish-up"></a>4\. lépés – befejezés

1. Az **Alkalmazás hozzáadása** panelen ellenőrizze, hogy helyesek-e a megadott információk.
2. Az alkalmazást a **Hozzáadás** elem kiválasztásával töltheti fel az Intune-ba.

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kívánt csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

> [!NOTE]
> Ha a *.pkg*-fájl több alkalmazást vagy alkalmazástelepítőt is tartalmaz, a Microsoft Intune csak akkor jelenti, hogy az *alkalmazás* telepítése sikerült, ha felderítette az összes telepített alkalmazást az eszközön.

## <a name="step-5---update-a-line-of-business-app"></a>5\. lépés – üzletági alkalmazás frissítése

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Ahhoz, hogy az Intune szolgáltatás sikeresen üzembe tudja helyezni az új *.pkg*-fájlt az eszközön, a *.pkg* kiterjesztésű csomagban található *packageinfo* fájlban meg kell növelni a csomag `version` és `CFBundleVersion` sztringjének értékét.

## <a name="next-steps"></a>További lépések

- A létrehozott alkalmazás megjelenik az alkalmazáslistában. Mostantól hozzárendelheti az Ön által választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

- További tájékoztató az alkalmazás jellemzőinek és hozzárendelési állapotának figyeléséről. További információt az [Alkalmazásinformációk és -hozzárendelések figyelése](apps-monitor.md) című témakörben talál.

- További tudnivalók az Intune-beli alkalmazás környezetéről. További információt az [Eszközök és alkalmazások életciklusa](../fundamentals/device-lifecycle.md) című témakörben talál.
