---
title: iOS-es áruházbeli alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Útmutató iOS-es áruházbeli alkalmazások a Microsoft Intune-ba való hozzáadásához. Ezzel a módszerrel rendelhet alkalmazásokat, ha az alkalmazások díjmentesek az App Store-ban.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c53166b6e6dc6ab3f780ccdfd4f11eb4c6a9d730
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497558"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>iOS-es áruházbeli alkalmazások hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A témakörben található információ segítségével iOS-es áruházbeli alkalmazásokat adhat hozzá a Microsoft Intune-hoz. Az iOS-es áruházbeli alkalmazásokat az Intune telepíti a felhasználói eszközökön. A felhasználók a cég munkatársai. Az iOS-es alkalmazásbeli alkalmazások automatikusan frissülnek.

>[!NOTE]
>Bár az iOS-eszközök felhasználói eltávolíthatnak néhányat a beépített iOS-alkalmazások közül – például a Részvények vagy a Térképek alkalmazást –, az Intune nem használható ezek újratelepítésére. Amennyiben a felhasználó törölte ezeket az alkalmazásokat, manuálisan telepítheti újra őket az App Store áruházból.

## <a name="before-you-start"></a>Előkészületek

Ezzel az eljárással csak az áruházban ingyenesen elérhető alkalmazások hozzárendelése lehetséges. Ha fizetős alkalmazást szeretne az Intune segítségével hozzárendelni, fontolja meg az [iOS mennyiségi vásárlási program](vpp-apps-ios.md) használatát.

>[!NOTE]
>A Microsoft Intune használatához javasoljuk, hogy a Microsoft Edge vagy a Google Chrome böngészőt használja.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** tevékenységprofil panelén a **Kezelés** szakaszban válassza az **Alkalmazások** lehetőséget.
5. Az **Alkalmazások** panelen válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazás típusa** lista **Áruházbeli alkalmazás** területén válassza az **iOS** lehetőséget.
7. Válassza a **Keresés az App Store-ban** lehetőséget.
8. A **Keresés az App Store** -ban panelen válassza ki az App Store ország/régió területi beállítást.
9. Írja be a **Keresés** mezőbe az alkalmazás nevét (vagy a név egy részét).  
    Az Intune ekkor rákeres arra az áruházban, és a kapott eredmények listáját adja vissza.
10. Az eredmények listájában válassza ki a kívánt alkalmazást, majd válassza a **Kiválasztás** lehetőséget.
11. Az alkalmazás konfigurálásához az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazás adatai** elemet.
12. Az **Alkalmazásadatok** panelen adja meg az alkalmazás adatait. A választott alkalmazástól függően előfordulhat, hogy egyes értékek automatikusan ki vannak töltve a panelen:
    - **Név**: Itt adhatja meg az alkalmazás céges portálon megjelenítendő nevét. Gondoskodjon róla, hogy az alkalmazás neve egyedi legyen. Ha két alkalmazás neve megegyezik, a felhasználók csak az egyik alkalmazást fogják látni a céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás a céges portálon jelenik meg a felhasználók számára.
    - **Kiadó:** Adja meg az alkalmazás kiadójának nevét.
    - **Alkalmazás-áruház URL-címe**: Itt adhatja meg a létrehozni kívánt alkalmazás áruházbeli URL-címét.
    - **Minimális operációsrendszer-verzió**: A listából válassza ki az operációs rendszer legkorábbi olyan verzióját, amelyre az alkalmazás telepíthető. Ha az alkalmazást régebbi operációs rendszerrel rendelkező eszközhöz rendelik hozzá, akkor nem lesz telepítve.
    - **Érvényes eszköztípusok**: A listából válassza ki az alkalmazás által használt eszközöket.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ezzel megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés kiemelt alkalmazásként a Céges portálon:** Ezzel a beállítással hangsúlyosan jelenítheti meg az alkalmazáscsomagot a céges portál főoldalán az alkalmazásokat kereső felhasználók számára.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő**: Igény esetén megadhatja az alkalmazás fejlesztőjének nevét. Ez a mező csak a rendszergazdák számára látható, a felhasználók számára nem.
    - **Tulajdonos**: Igény esetén megadhatja az alkalmazás tulajdonosának nevét (például *HR-osztály*). Ez a mező csak a rendszergazdák számára látható, a felhasználók számára nem.
    - **Megjegyzések:** : Ide írhatja be igény szerint az alkalmazáshoz társítani kívánt megjegyzéseket. Ez a mező csak rendszergazdáknak jelenik meg, a végfelhasználók nem láthatják.
    - **Ikon** (nem kötelező): Itt töltheti fel az alkalmazáshoz hozzárendelni kívánt ikont. Ez az alkalmazásikon jelenik meg a céges portálon böngésző felhasználók számára.
13. Válassza az **OK** gombot.
14. Válassza a **Hozzáadás** elemet.

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz.

## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
