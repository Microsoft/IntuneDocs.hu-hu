---
title: Üzletági Windows-alkalmazás hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Megtudhatja, hogyan adhat hozzá egy Windows rendszerű üzletági (LOB) alkalmazást Microsoft Intune használatával.
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
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3deb9f3c96a4c2c2de72b7016aca855f679bbd7
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755127"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Üzletági Windows-alkalmazás hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az üzletági (LOB) alkalmazásokat egy alkalmazástelepítő fájlból adja hozzá. Az ilyen alkalmazásokat általában házon belül írják. Az alábbi lépések nyújtanak útmutatást az üzletági Windows-alkalmazások a Microsoft Intune-hoz való hozzáadásához.

> [!IMPORTANT]
> Ha Win32-alkalmazásokat telepít az *. msi* kiterjesztésű telepítési fájllal, vegye fontolóra az [Intune felügyeleti bővítmény](../apps/intune-management-extension.md)használatát. Ha az Autopilot-regisztráció során összekeveri a Win32-alkalmazások és az üzletági alkalmazások telepítését, előfordulhat, hogy az alkalmazás telepítése sikertelen lesz.  

## <a name="select-the-app-type"></a>Válassza ki az alkalmazás típusát

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán, a **többi** alkalmazás típusa területen válassza az **üzletági alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **alkalmazás hozzáadása** lépések.

## <a name="step-1---app-information"></a>1\. lépés – alkalmazás adatai

### <a name="select-the-app-package-file"></a>Válassza ki az alkalmazáscsomag-fájlt

1. Az **alkalmazás hozzáadása** panelen kattintson az **alkalmazáscsomag-fájl kiválasztása**lehetőségre. 
2. Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ezután válasszon ki egy,. **MSI**, **. Appx**vagy **. appxbundle**kiterjesztésű Windows-telepítési fájlt.
   Ekkor megjelenik az alkalmazás részletei.

    > [!NOTE]
    > A windowsos alkalmazások fájlnévkiterjesztései közé tartozik az **.msi**, az **.appx**, az **.appxbundle**, az **.msix** és az **.msixbundle** is.  

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

A létrehozott alkalmazás ekkor megjelenik az alkalmazások listájában. A listából hozzárendelheti az alkalmazást a választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

## <a name="update-a-line-of-business-app"></a>Üzletági alkalmazás frissítése

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

- További információ a Win32-alkalmazásokról. Lásd: [Win32-alkalmazások kezelése](~/apps/apps-win32-app-management.md).
