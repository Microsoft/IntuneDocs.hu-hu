---
title: IOS-es üzletági alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Útmutató az iOS-es üzletági (LOB) alkalmazások Microsoft Intunehoz való hozzáadásához.
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
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b7c0a7dfa4337983c12ada2d0f415c771bd0548
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755187"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>IOS-es üzletági alkalmazások hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikkben található információ segítségével iOS rendszerű üzletági alkalmazást adhat hozzá a Microsoft Intune-hoz. Az üzletági (LOB) alkalmazások olyan alkalmazások, amelyeket az Intune-ban egy IPA-alkalmazás telepítési fájljában adhat hozzá. Az ilyen alkalmazásokat általában házon belül írják. Először csatlakoznia kell az iOS Developer Enterprise programhoz. Ennek módjáról további információt az [Apple webhelyén](https://developer.apple.com/programs/ios/enterprise/)talál.

>[!NOTE]
>Az iOS-eszközök felhasználói eltávolíthatnak néhányat a beépített iOS-alkalmazások közül, például a Részvények vagy a Térképek alkalmazást. Az Intune nem használható ezek újratelepítésére. Amennyiben a felhasználó törölte ezeket az alkalmazásokat, manuálisan telepítheti újra őket az App Store áruházból.
>
>az iOS LOB-alkalmazások esetében az alkalmazás legfeljebb 4 GB méretű lehet.

## <a name="select-the-app-type"></a>Válassza ki az alkalmazás típusát

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán, a **többi** alkalmazás típusa területen válassza az **üzletági alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **alkalmazás hozzáadása** lépések.

## <a name="step-1---app-information"></a>1\. lépés – alkalmazás adatai

### <a name="select-the-app-package-file"></a>Válassza ki az alkalmazáscsomag-fájlt

1. Az **alkalmazás hozzáadása** panelen kattintson az **alkalmazáscsomag-fájl kiválasztása**lehetőségre. 
2. Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ezután válasszon ki egy **. ipa**kiterjesztésű iOS-es telepítőfájlt.
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

A létrehozott alkalmazás ekkor megjelenik az alkalmazások listájában. A listából hozzárendelheti az alkalmazást a választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

> [!NOTE]
> Az iOS üzletági (LOB) alkalmazások üzembehelyezési profiljai 30 nappal a lejáratuk előtt értesítést küldenek.

## <a name="step-5-update-a-line-of-business-app"></a>5\. lépés: Üzletági alkalmazás frissítése

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

A rendszer automatikusan telepíti az üzletági alkalmazás frissítését.

> [!NOTE]
> Ahhoz, hogy az Intune szolgáltatás sikeresen üzembe tudja helyezni az új IPA-fájlt az eszközön, az IPA-csomagban található Info.plist fájlban meg kell növelni a `CFBundleVersion` sztring értékét.

## <a name="next-steps"></a>További lépések

- A létrehozott alkalmazás megjelenik az alkalmazások listájában. Mostantól hozzárendelheti az Ön által választott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).

- További tájékoztató az alkalmazás jellemzőinek és hozzárendelési állapotának figyeléséről. Lásd: [Alkalmazásadatok és -hozzárendelések figyelése](apps-monitor.md).

- További tudnivalók az Intune-beli alkalmazás környezetéről. Lásd: [Az eszközök és alkalmazások életciklusának áttekintése](../fundamentals/device-lifecycle.md).
