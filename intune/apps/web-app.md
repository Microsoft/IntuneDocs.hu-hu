---
title: Webalkalmazások hozzáadása az Intune-hoz
titleSuffix: ''
description: További információ a webalkalmazások (ügyfél-kiszolgáló alkalmazások) Microsoft Intune való hozzáadásáról.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e018fb9888db19995556a6671d93a1db5fa78c2a
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415446"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Webalkalmazások hozzáadása az Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune számos különböző alkalmazástípust támogat, beleértve a webalkalmazásokat is. A webalkalmazások ügyfél-kiszolgáló alkalmazások. A kiszolgáló szolgáltatja a webalkalmazást, amely tartalmazza a felhasználói felületet, a tartalmat és a funkciókat. A modern webszolgáltatási platformok emellett gyakran kínálnak biztonsági, terheléselosztási és egyéb szolgáltatásokat is. A webalkalmazásokat külön, a weben kezelik. Ehhez az alkalmazástípushoz a Microsoft Intune-t kell használnia. Azt is megszabhatja, hogy mely felhasználói csoportok férhetnek hozzá az alkalmazáshoz. 

Ahhoz, hogy kezelhesse és felhasználókhoz rendelhesse hozzá az alkalmazásokat, hozzá kell adnia őket az Intune-hoz. 

Az Intune létrehozza a webes alkalmazás parancsikonját a felhasználó eszközén. IOS/iPadOS-eszközök esetén a rendszer a webalkalmazás parancsikonját adja hozzá a kezdőképernyőn. Androidos eszközök rendszergazdai eszközei esetén a webalkalmazásra mutató parancsikon kerül az Intune vállalati portál widgetbe, és a widgetet manuálisan kell rögzíteni a felhasználó által. Windows-eszközök esetén a webalkalmazásra mutató parancsikon kerül a Start menübe.

> [!Note]
> A webalkalmazások indításához egy böngészőt kell telepíteni a felhasználó eszközén. 

> [!Note]
> Android rendszerű vállalati eszközök esetén lásd: [felügyelt Google Play web Links](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>Webalkalmazás hozzáadása az Intune-hoz
A következő módon adhat hozzá egy alkalmazást az Intune-hoz egy alkalmazás webes hivatkozásaként:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán a rendelkezésre álló **egyéb** típusok területen válassza a **webes hivatkozás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **alkalmazás hozzáadása** lépések.
5. Az **alkalmazás adatai** lapon adja meg a következő adatokat:
    - **Név**: Itt adhatja meg az alkalmazás vállalati portálon megjelenítendő nevét. 

        > [!NOTE]
        > Ha az alkalmazás telepítését követően módosítja annak nevét az Intune Azure Portalon, az alkalmazást nem fogják megtalálni a parancsok.

    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás a céges portálon jelenik meg a felhasználók számára.
    - **Kiadó**: Adja meg az alkalmazás kiadójának nevét.
    - **Alkalmazás URL-címe**: Adja meg annak a webhelynek az URL-címét, amelyen a hozzárendelni kívánt alkalmazás található.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ezzel megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: ezzel a beállítással a vállalati portál főoldalán jelenítheti meg az App Suite-t, amikor a felhasználók megkeresik az alkalmazásokat.
    - **Felügyelt böngésző használatának megkövetelése a hivatkozás megnyitásához**: Ezzel a lehetőséggel egy olyan webhelyre vagy webalkalmazásra mutató hivatkozást rendelhet a felhasználókhoz, amelyet az Intune által felügyelt böngészőben nyithatnak meg. Ezt a böngészőt telepíteni kell az eszközökön.
    - **Ikon**: Itt töltheti fel az alkalmazáshoz hozzárendelni kívánt ikont. Ez az alkalmazásikon jelenik meg a céges portálon böngésző felhasználók számára.
6. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.
7. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye a hatókör címkéit az alkalmazáshoz. További információ: [a szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez](~/fundamentals/scope-tags.md).
8. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.
9. Válassza ki az alkalmazás csoportjának hozzárendeléseit. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md). 
10. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat.
11. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

    Megjelenik a létrehozott alkalmazás **Áttekintés** panelje.

> [!Note]
> Jelenleg az Intune-webalkalmazások iOS/iPadOS-eszközökre való telepítése a felügyeleti profilhoz van társítva, és nem távolítható el manuálisan. Az Intune portálon **Eltávolítás** értékre módosíthatja az üzembehelyezési típust, hogy a webalkalmazás automatikusan eltávolítható legyen. Ha azonban azelőtt távolítja el az üzemelő példányt, hogy az alkalmazás-hozzárendelési szándékot **Eltávolítás** értékre módosítaná, a webalkalmazás végleg az eszközön marad, amíg meg nem szűnik az eszköz regisztrációja az Intune-ban.

A végfelhasználók közvetlenül a Windows Céges portál alkalmazásból indíthatnak webalkalmazásokat a webalkalmazás kiválasztásával, majd a **Megnyitás böngészőben**lehetőség kiválasztásával. A közzétett webes URL-cím közvetlenül a böngészőben nyílik meg. 

## <a name="next-steps"></a>További lépések

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md). 
