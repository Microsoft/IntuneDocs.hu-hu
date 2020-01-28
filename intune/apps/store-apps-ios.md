---
title: iOS-es áruházbeli alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Útmutató iOS-es áruházbeli alkalmazások a Microsoft Intune-ba való hozzáadásához. Ezzel a módszerrel rendelhet alkalmazásokat, ha az alkalmazások díjmentesek az App Store-ban.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
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
ms.openlocfilehash: 2daa7428cf8677f9e1a2b11db2b3ce65e2df8bc4
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755000"
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

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán az elérhető **áruházbeli alkalmazások** típusai területen válassza az **iOS áruházbeli alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre.<br>
   Megjelenik az **alkalmazás hozzáadása** lépések.
5. Válassza a **Keresés az App Store-ban** lehetőséget.
6. A **Keresés az App Store** -ban panelen válassza ki az App Store ország/régió területi beállítást.
7. Írja be a **Keresés** mezőbe az alkalmazás nevét (vagy a név egy részét).  
    Az Intune ekkor rákeres arra az áruházban, és a kapott eredmények listáját adja vissza.
8. Az eredmények listájában válassza ki a kívánt alkalmazást, majd válassza a **Kiválasztás** lehetőséget.<br>

   Az alkalmazás- **információ** lap megjelenik az **alkalmazás hozzáadása** panelen. Ha lehetséges, az alkalmazás adatai az áruházból kiválasztott alkalmazás alapján lesznek hozzáadva.

9. Az **alkalmazás adatai** lapon adja meg az alkalmazás részleteit. A választott alkalmazástól függően előfordulhat, hogy egyes értékek automatikusan ki vannak töltve a panelen:
    - **Név**: Itt adhatja meg az alkalmazás céges portálon megjelenítendő nevét. Gondoskodjon róla, hogy az alkalmazás neve egyedi legyen. Ha két alkalmazás neve megegyezik, a felhasználók csak az egyik alkalmazást fogják látni a céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás a céges portálon jelenik meg a felhasználók számára.
    - **Kiadó:** Adja meg az alkalmazás kiadójának nevét.
    - **Alkalmazás-áruház URL-címe**: Itt adhatja meg a létrehozni kívánt alkalmazás áruházbeli URL-címét.
    - **Minimális operációsrendszer-verzió**: A listából válassza ki az operációs rendszer legkorábbi olyan verzióját, amelyre az alkalmazás telepíthető. Ha az alkalmazást régebbi operációs rendszerrel rendelkező eszközhöz rendelik hozzá, akkor nem lesz telepítve.
    - **Érvényes eszköztípusok**: A listából válassza ki az alkalmazás által használt eszközöket.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ezzel megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: ezzel a beállítással a vállalati portál főoldalán jelenítheti meg az App Suite-t, amikor a felhasználók megkeresik az alkalmazásokat.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő**: Igény esetén megadhatja az alkalmazás fejlesztőjének nevét. Ez a mező csak a rendszergazdák számára látható, a felhasználók számára nem.
    - **Tulajdonos**: Igény esetén megadhatja az alkalmazás tulajdonosának nevét (például *HR-osztály*). Ez a mező csak a rendszergazdák számára látható, a felhasználók számára nem.
    - **Megjegyzések:** : Ide írhatja be igény szerint az alkalmazáshoz társítani kívánt megjegyzéseket. Ez a mező csak rendszergazdáknak jelenik meg, a végfelhasználók nem láthatják.
    - **Ikon** (nem kötelező): Itt töltheti fel az alkalmazáshoz hozzárendelni kívánt ikont. Ez az alkalmazásikon jelenik meg a céges portálon böngésző felhasználók számára.
10. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.
11. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye a hatókör címkéit az alkalmazáshoz. További információ: [a szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez](~/fundamentals/scope-tags.md).
12. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.
13. Válassza ki az alkalmazás csoportjának hozzárendeléseit. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md). 
14. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat.
15. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

Megjelenik a létrehozott alkalmazás **Áttekintés** panelje.

## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
