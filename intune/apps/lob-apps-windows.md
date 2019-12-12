---
title: Üzletági Windows-alkalmazás hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Megtudhatja, hogyan adhat hozzá egy Windows rendszerű üzletági (LOB) alkalmazást Microsoft Intune használatával.
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
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f4c7b5e3cca06a3ec10ea1b3dfc5e45546c841f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563902"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Üzletági Windows-alkalmazás hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az üzletági (LOB) alkalmazásokat egy alkalmazástelepítő fájlból adja hozzá. Az ilyen alkalmazásokat általában házon belül írják. Az alábbi lépések nyújtanak útmutatást az üzletági Windows-alkalmazások a Microsoft Intune-hoz való hozzáadásához.

> [!IMPORTANT]
> Ha Win32-alkalmazásokat telepít az *. msi* kiterjesztésű telepítési fájllal, vegye fontolóra az [Intune felügyeleti bővítmény](../apps/intune-management-extension.md)használatát. Ha az Autopilot-regisztráció során összekeveri a Win32-alkalmazások és az üzletági alkalmazások telepítését, előfordulhat, hogy az alkalmazás telepítése sikertelen lesz.  

## <a name="step-1-specify-the-software-setup-file"></a>1\. lépés: A szoftvertelepítő fájl megadása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás hozzáadása** panelen válassza az **üzletági alkalmazás** lehetőséget az **alkalmazás típusaként**.

## <a name="step-2-configure-the-app-package-file"></a>2\. lépés: Az alkalmazáscsomag-fájl konfigurálása

1. Az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazáscsomag-fájl** lehetőséget.
2. Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ez után jelölje ki az **.msi**, **.appx** vagy **.appxbundle** kiterjesztésű telepítőfájlt.

    > [!NOTE]
    > A windowsos alkalmazások fájlnévkiterjesztései közé tartozik az **.msi**, az **.appx**, az **.appxbundle**, az **.msix** és az **.msixbundle** is.  

1. Amikor végzett, válassza az **OK** gombot.


## <a name="step-3-configure-app-information"></a>3\. lépés: Az alkalmazás adatainak konfigurálása

1. Az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazásadatok** lehetőséget.
2. Az **Alkalmazás adatai** panelen konfigurálja az alábbi információkat. Lehetséges, hogy ezen a panelen néhány érték automatikusan ki lesz töltve.
    - **Név**: Itt adhatja meg az alkalmazás a Céges portálon megjelenő nevét. Ügyeljen arra, hogy a megadott alkalmazásnevek egyediek legyenek. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a Céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás megjelenik a Céges portálon.
    - **Kiadó:** Adja meg az alkalmazás kiadójának nevét.
    - **Alkalmazásverzió figyelmen kívül hagyása**: Állítsa **Igen** értékre, ha az alkalmazást automatikusan frissíti annak fejlesztője. Ez a beállítás csak mobil .msi alkalmazásokra vonatkozik.
    - **Kategória**: Választhat egyet vagy többet a beépített kategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. A kategóriákkal megkönnyítheti a felhasználók számára az alkalmazás megkeresését a Céges portálon való böngészés során.
    - **Megjelenítés kiemelt alkalmazásként a Céges portálon**: Ezzel a beállítással hangsúlyosan jelenítheti meg az alkalmazást a Céges portál főoldalán alkalmazásokat kereső felhasználók számára.
    - **Információs URL-cím**: Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe**: Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Az URL-cím megjelenik a Céges portálon.
    - **Parancssori argumentumok**: Szükség esetén az .msi-fájl futtatásakor alkalmazandó parancssori argumentumokat adhat meg.  Például: **/q**. Ne foglalja bele az msiexec parancsot vagy argumentumokat, például a **/i** vagy az **/x**függvényt, mivel azok automatikusan használatban vannak. További információ: [parancssori kapcsolók](https://docs.microsoft.com/windows/desktop/Msi/command-line-options). Ha a. Az MSI-fájlhoz további parancssori kapcsolók szükségesek a [Win32-alkalmazások kezeléséhez](app-management.md).
    - **Fejlesztő**: Igény esetén megadhatja az alkalmazás fejlesztőjének nevét.
    - **Tulajdonos**: Igény esetén megadhatja az alkalmazás tulajdonosának nevét. Például **HR részleg**.
    - **Megjegyzések**: Ide írhatja be az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Ikon**: Itt töltheti fel az alkalmazáshoz társított ikont. Ez az ikon jelenik meg az alkalmazásnál a Céges portálon böngésző felhasználók számára.
3. Amikor végzett, válassza az **OK** gombot.

## <a name="step-4-finish-up"></a>4\. lépés: befejezés

1. Az **Alkalmazás hozzáadása** panelen ellenőrizze, hogy helyesen konfigurálta-e az alkalmazásadatokat.
2. Az alkalmazást a **Hozzáadás** elem kiválasztásával töltheti fel az Intune-ba.

## <a name="step-5-update-a-line-of-business-app"></a>5\. lépés: Üzletági alkalmazás frissítése

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Ahhoz, hogy az Intune szolgáltatás sikeresen üzembe helyezzen egy új APPX-fájlt az eszközön, növelnie kell a `Version` karakterláncot a APPX-csomagban található AppxManifest. xml fájlban.

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Önfrissítő MSI-mobilalkalmazások konfigurálása a verzióellenőrzési folyamat figyelmen kívül hagyására

Az ismert önfrissítő MSI-mobilalkalmazásokat konfigurálhatja úgy, hogy figyelmen kívül hagyják a verzióellenőrzési folyamatot.

Néhány MSI telepítő-alapú alkalmazást automatikusan frissít az alkalmazás fejlesztője vagy egy másik frissítési módszer. Az ilyen automatikusan frissített MSI-alkalmazások esetében konfigurálhatja az **Alkalmazásverzió figyelmen kívül hagyása** beállítást az **Alkalmazásadatok** panelen. Ha ezt a beállítást átállítja az **Igen** értékre, a Microsoft Intune nem kényszeríti a Windows-ügyfélen telepített alkalmazásverzió használatát.

Ez a funkció akkor hasznos, ha nem szeretne versenyhelyzetbe kerülni. Konfliktus alakulhat ki például akkor, amikor az alkalmazást automatikusan frissíti annak fejlesztője, ugyanakkor az Intune is frissíti. Mindkettő megpróbálhatja kikényszeríteni az alkalmazás egy verziójának használatát a Windows-ügyfélen, ami ütközést eredményezhet.

## <a name="next-steps"></a>További lépések

- A létrehozott alkalmazás megjelenik az alkalmazások listájában. Mostantól hozzárendelheti az Ön által választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

- További tájékoztató az alkalmazás jellemzőinek és hozzárendelési állapotának figyeléséről. Lásd: [Alkalmazásadatok és -hozzárendelések figyelése](apps-monitor.md).

- További tudnivalók az Intune-beli alkalmazás környezetéről. Lásd: [az alkalmazások életciklusának áttekintése Microsoft Intuneban](app-lifecycle.md).
