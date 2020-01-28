---
title: MacOS-es üzletági alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Útmutató macOS rendszerű üzletági (LOB) alkalmazások Microsoft Intunehoz való hozzáadásához.
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
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755170"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>MacOS-es üzletági (LOB) alkalmazások hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikkben található információ segítségével macOS rendszerű üzletági alkalmazásokat adhat hozzá a Microsoft Intune-hoz. Le kell töltenie egy külső eszközt a *.pkg*-fájlok előzetes feldolgozásához, mielőtt feltölthetné üzletági fájlját a Microsoft Intune-ba. A *.pkg*-fájlok előzetes feldolgozását macOS-eszközön kell elvégezni.

> [!NOTE]
> A macOS Catalina 10,15 kiadásával kezdődően az alkalmazások Intune-nal való hozzáadása előtt ellenőrizze, hogy a macOS LOB-alkalmazások hitelesítettek-e. Ha a LOB-alkalmazások fejlesztői nem notarize az alkalmazásaikat, az alkalmazások nem fognak futni a felhasználók macOS-eszközein. Ha további információt szeretne arról, hogyan ellenőrizhető, hogy egy alkalmazás hitelesített-e, látogasson el [a MacOS-alkalmazások Notarize a MacOS catalinare való felkészüléshez](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579).

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
    > [!IMPORTANT]
    > Győződjön meg arról, hogy a `<source_file>` argumentum nem tartalmaz szóközt a `IntuneAppUtil` parancsok futtatása előtt.

    - `IntuneAppUtil -h`<br>
    Ez a parancs megjeleníti az eszköz használatára vonatkozó információkat.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Ez a parancs *.pkg* kiterjesztésű üzletági alkalmazásfájlt burkol *.intunemac*-fájlba.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Ez a parancs kibontja a felderített paramétereket és verziót a létrehozott *.intunemac*-fájlhoz.

## <a name="select-the-app-type"></a>Válassza ki az alkalmazás típusát

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán, a **többi** alkalmazás típusa területen válassza az **üzletági alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **alkalmazás hozzáadása** lépések.

## <a name="step-1---app-information"></a>1\. lépés – alkalmazás adatai

### <a name="select-the-app-package-file"></a>Válassza ki az alkalmazáscsomag-fájlt

1. Az **alkalmazás hozzáadása** panelen kattintson az **alkalmazáscsomag-fájl kiválasztása**lehetőségre. 
2. Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ezután válasszon ki egy, a *. intunemac*kiterjesztésű MacOS-telepítőfájlt.
   Ekkor megjelenik az alkalmazás részletei.
3. Ha elkészült, kattintson az **OK gombra** az **alkalmazáscsomag fájl** paneljén az alkalmazás hozzáadásához.

### <a name="set-app-information"></a>Alkalmazás adatainak megadása

1. Az **alkalmazás adatai** lapon adja meg az alkalmazás részleteit. A választott alkalmazástól függően előfordulhat, hogy egyes értékek automatikusan ki vannak töltve a panelen.
    - **Név**: Itt adhatja meg az alkalmazás a Céges portálon megjelenő nevét. Ügyeljen arra, hogy a megadott alkalmazásnevek egyediek legyenek. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a Céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás megjelenik a Céges portálon.
    - **Kiadó:** Adja meg az alkalmazás kiadójának nevét.
    - **Minimális operációsrendszer-verzió**: A listából kiválaszthatja az operációs rendszer legkorábbi olyan verzióját, amelyre az alkalmazás telepíthető. Ha az alkalmazást régebbi operációs rendszerrel rendelkező eszközhöz rendelik hozzá, akkor nem lesz telepítve.
    - **Kategória**: Választhat egyet vagy többet a beépített kategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. A kategóriákkal megkönnyítheti a felhasználók számára az alkalmazás megkeresését a Céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portál**: az alkalmazás megjelenítése a vállalati portál főoldalán, amikor a felhasználók megkeresik az alkalmazásokat.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Fejlesztő**: Igény esetén megadhatja az alkalmazás fejlesztőjének nevét.
    - **Tulajdonos**: Igény esetén megadhatja az alkalmazás tulajdonosának nevét. Például **HR részleg**.
    - **Megjegyzések**: Ide írhatja be az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Ikon**: Itt töltheti fel az alkalmazáshoz társított ikont. Ez az ikon jelenik meg az alkalmazásnál a Céges portálon böngésző felhasználók számára.
2. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.

## <a name="step-2---select-scope-tags-optional"></a>2\. lépés – hatókör-címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).

1. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye a hatókör címkéit az alkalmazáshoz. 
2. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.

## <a name="step-3---assignments"></a>3\. lépés – hozzárendelések

1. Válassza ki a **szükséges**, a **regisztrált eszközök számára elérhető**lehetőséget, vagy **távolítsa el** a csoport hozzárendeléseit az alkalmazáshoz. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md) , valamint [alkalmazások társítása a csoportokhoz Microsoft Intune](apps-deploy.md)használatával.
2. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez. 

## <a name="step-4---review--create"></a>4\. lépés – felülvizsgálat + létrehozás

1. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat.
2. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

    Megjelenik az üzletági alkalmazás **Áttekintés** panelje.

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kívánt csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

> [!NOTE]
> Ha a *.pkg*-fájl több alkalmazást vagy alkalmazástelepítőt is tartalmaz, a Microsoft Intune csak akkor jelenti, hogy az *alkalmazás* telepítése sikerült, ha felderítette az összes telepített alkalmazást az eszközön.

## <a name="update-a-line-of-business-app"></a>Üzletági alkalmazás frissítése

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Ahhoz, hogy az Intune szolgáltatás sikeresen üzembe tudja helyezni az új *.pkg*-fájlt az eszközön, a *.pkg* kiterjesztésű csomagban található *packageinfo* fájlban meg kell növelni a csomag `version` és `CFBundleVersion` sztringjének értékét.

## <a name="next-steps"></a>További lépések

- A létrehozott alkalmazás megjelenik az alkalmazáslistában. Mostantól hozzárendelheti az Ön által választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

- További tájékoztató az alkalmazás jellemzőinek és hozzárendelési állapotának figyeléséről. További információt az [Alkalmazásinformációk és -hozzárendelések figyelése](apps-monitor.md) című témakörben talál.

- További tudnivalók az Intune-beli alkalmazás környezetéről. További információt az [Eszközök és alkalmazások életciklusa](../fundamentals/device-lifecycle.md) című témakörben talál.
