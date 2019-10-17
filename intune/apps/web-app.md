---
title: Webalkalmazások hozzáadása az Intune-hoz
titleSuffix: ''
description: További információ a webalkalmazások (ügyfél-kiszolgáló alkalmazások) Microsoft Intune való hozzáadásáról.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 6678b7c3519328623d9c0035c725af3877a36ba8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507053"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Webalkalmazások hozzáadása az Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune számos különböző alkalmazástípust támogat, beleértve a webalkalmazásokat is. A webalkalmazások ügyfél-kiszolgáló alkalmazások. A kiszolgáló szolgáltatja a webalkalmazást, amely tartalmazza a felhasználói felületet, a tartalmat és a funkciókat. A modern webszolgáltatási platformok emellett gyakran kínálnak biztonsági, terheléselosztási és egyéb szolgáltatásokat is. A webalkalmazásokat külön, a weben kezelik. Ehhez az alkalmazástípushoz a Microsoft Intune-t kell használnia. Azt is megszabhatja, hogy mely felhasználói csoportok férhetnek hozzá az alkalmazáshoz. 

Ahhoz, hogy kezelhesse és felhasználókhoz rendelhesse hozzá az alkalmazásokat, hozzá kell adnia őket az Intune-hoz. 

Az Intune létrehozza a webes alkalmazás parancsikonját a felhasználó eszközén. IOS-eszközök esetén a rendszer a webalkalmazás parancsikonját adja hozzá a kezdőképernyő számára. Android-eszközök esetén a webalkalmazásra mutató parancsikon kerül az Intune vállalati portál widgetbe, és a widgetet manuálisan kell rögzíteni a felhasználó által. Windows-eszközök esetén a webalkalmazásra mutató parancsikon kerül a Start menübe.

> [!Note]
> Az androidos munkahelyi profilú eszközökön nem támogatottak a webalkalmazások. A webalkalmazások indításához egy böngészőt kell telepíteni a felhasználó eszközén.

## <a name="add-a-web-app-to-intune"></a>Webalkalmazás hozzáadása az Intune-hoz
A következő módon adhat hozzá egy alkalmazást az Intune-hoz egy alkalmazás webes hivatkozásaként:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** tevékenységprofil panelén a **Kezelés** szakaszban válassza az **Alkalmazások** lehetőséget.
5. Az **Alkalmazások** panelen válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazás felvétele** panelen az **Alkalmazás típusa** legördülő listában válassza a **Webes hivatkozás** típust.
7. Válassza ki a **Konfigurálás** lehetőséget.
8. Az **Alkalmazásadatok** panelen adja meg az alábbi információkat:
    - **Név**: Itt adhatja meg az alkalmazás vállalati portálon megjelenítendő nevét. 

        > [!NOTE]
        > Ha az alkalmazás telepítését követően módosítja annak nevét az Intune Azure Portalon, az alkalmazást nem fogják megtalálni a parancsok.

    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás a céges portálon jelenik meg a felhasználók számára.
    - **Kiadó**: Adja meg az alkalmazás kiadójának nevét.
    - **Alkalmazás URL-címe**: Adja meg annak a webhelynek az URL-címét, amelyen a hozzárendelni kívánt alkalmazás található.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ezzel megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés kiemelt alkalmazásként a Céges portálon:** Ezzel a beállítással hangsúlyosan jelenítheti meg az alkalmazáscsomagot a céges portál főoldalán az alkalmazásokat kereső felhasználók számára.
    - **Felügyelt böngésző használatának megkövetelése a hivatkozás megnyitásához**: Ezzel a lehetőséggel egy olyan webhelyre vagy webalkalmazásra mutató hivatkozást rendelhet a felhasználókhoz, amelyet az Intune által felügyelt böngészőben nyithatnak meg. Ezt a böngészőt telepíteni kell az eszközökön.
    - **Ikon**: Itt töltheti fel az alkalmazáshoz hozzárendelni kívánt ikont. Ez az alkalmazásikon jelenik meg a céges portálon böngésző felhasználók számára.
9. Válassza az **OK** gombot.
10. Az **Alkalmazás hozzáadása** panelen válassza a **Hozzáadás** lehetőséget.

> [!Note]
> Az Android-eszközökhöz rendelt webalkalmazások megjelenítéséhez a felhasználóknak hozzá kell adniuk az Intune widgetet a kezdőképernyőjükhöz.
>
> Az Intune-webalkalmazások iOS-eszközökön való üzembe helyezése jelenleg a felügyeleti profillal van társítva, így manuálisan nem távolíthatók el. Az Intune portálon **Eltávolítás** értékre módosíthatja az üzembehelyezési típust, hogy a webalkalmazás automatikusan eltávolítható legyen. Ha azonban azelőtt távolítja el az üzemelő példányt, hogy az alkalmazás-hozzárendelési szándékot **Eltávolítás** értékre módosítaná, a webalkalmazás végleg az eszközön marad, amíg meg nem szűnik az eszköz regisztrációja az Intune-ban.

## <a name="next-steps"></a>További lépések

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. További segítségért lásd: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md). 
