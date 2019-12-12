---
title: Microsoft Edge hozzáadása macOS-eszközökhöz Microsoft Intune használatával
titleSuffix: ''
description: Tudnivalók a Microsoft Edge macOS-eszközökhöz való hozzáadásáról Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c31dd652022ae0d394ab2229a0c25b362ad8574d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563589"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Microsoft Edge hozzáadása macOS-eszközökhöz Microsoft Intune használatával

Az alkalmazások üzembe helyezése, konfigurálása, monitorozása vagy védelemmel való ellátása előtt hozzá kell adnia őket az Intune-hoz. Az elérhető [alkalmazások](~/apps/apps-add.md#app-types-in-microsoft-intune) egyike a Microsoft Edge *77-es és újabb verziója*. Ha ezt az alkalmazást az Intune-ban kiválasztja, a Microsoft Edge *77-es vagy újabb verzióját* a MacOS-t futtató eszközökhöz rendelheti hozzá és telepítheti. Az alkalmazás típusa megkönnyíti a Microsoft Edge macOS-eszközökhöz való hozzárendelését anélkül, hogy a macOS-alkalmazás burkoló eszközét kellene használnia. Az alkalmazások biztonságosabbá és naprakészen tartása érdekében az alkalmazás a Microsoft AutoUpdate (MAU) szolgáltatáshoz tartozik.

> [!IMPORTANT]
> Az alkalmazás típusa **nyilvános előzetes** verzióban érhető el, és fejlesztői és bétaverziós csatornákat kínál a MacOS rendszerhez. A központi telepítés csak angol (EN) nyelven érhető el, de a végfelhasználók a **beállítások** > **nyelvek**területen módosíthatják a böngésző megjelenítési nyelvét. 

> [!NOTE]
> A Microsoft Edge *77-es és újabb verziója* is elérhető a Windows 10 rendszerhez.

## <a name="prerequisites"></a>Előfeltételek
- A macOS-eszköznek macOS 10,12 vagy újabb rendszert kell futtatnia a Microsoft Edge telepítése előtt.

## <a name="add-microsoft-edge-to-intune"></a>Microsoft Edge hozzáadása az Intune-hoz
A Microsoft Edge 77-es vagy újabb verzióját a következő lépésekkel adhatja hozzá az Intune-hoz:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusa** listában a **Microsoft Edge 77-es és újabb verziójában**válassza a **MacOS**lehetőséget.

## <a name="configure-app-information"></a>Az alkalmazásadatok konfigurálása
Ebben a lépésben az alkalmazás telepítésével kapcsolatos információkat nyújt. Ez az információ segít azonosítani az alkalmazást az Intune-ban, és segít a felhasználóknak megkeresni az alkalmazást a vállalati portálon.

1. Az **alkalmazásadatok ablaktábla** megjelenítéséhez kattintson az **alkalmazás adatai** elemre.
2. Az **alkalmazás adatai** panelen megadhatja az alkalmazás telepítésével kapcsolatos információkat. Ez az információ segít azonosítani az alkalmazást az Intune-ban, és segít a felhasználóknak megkeresni az alkalmazást a vállalati portálon.
    - **Név**: Itt adhatja meg az alkalmazásnak a vállalati portálon megjelenő nevét. Ügyeljen arra, hogy minden név egyedi legyen. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. Megadhatja például, hogy a leírásban megjelenő felhasználók is fel legyenek listázva.
    - **Közzétevő:** Közzétevőként a Microsoft jelenik meg.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ez a beállítás megkönnyíti a felhasználók számára az alkalmazás megkeresését a vállalati portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: válassza ezt a lehetőséget, ha a felhasználók tallózásával szeretné megjeleníteni az alkalmazást a vállalati portál főoldalán.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő:** Fejlesztőként a Microsoft jelenik meg.
    - **Tulajdonos:** Tulajdonosként a Microsoft jelenik meg.
    - **Megjegyzések:** : Ide írhatja be igény szerint az alkalmazáshoz társítani kívánt megjegyzéseket.
3. Válassza az **OK** gombot.

## <a name="configure-microsoft-edge-settings"></a>A Microsoft Edge-beállítások konfigurálása
Ebben a lépésben konfigurálja az alkalmazás telepítési beállításait.

1. Az **alkalmazás hozzáadása** panelen válassza az **Alkalmazásbeállítások**lehetőséget.
2. Az **Alkalmazásbeállítások** ablaktáblán a **bétaverzió** automatikusan ki van választva, és nem módosítható.
    - A **Beta** Channel a legstabilabb Microsoft Edge előzetes verziója, és a legjobb választás a teljes pilóta számára a szervezeten belül. A főbb frissítések 6 hetente.

    > [!NOTE]
    > A Microsoft Edge böngésző emblémája az alkalmazással jelenik meg, amikor a felhasználók megkeresik a vállalati portált.
3.  Válassza az **OK** gombot.

## <a name="select-scope-tags-optional"></a>Hatóköri címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez.
1.  Válassza a **hatókör (címkék)**  > **Hozzáadás**elemet.
2.  A **Select (kijelölés** ) mező használatával keresheti meg a hatókör címkéit.
3.  Jelölje be a jelölőnégyzetet az alkalmazáshoz hozzárendelni kívánt hatókör-címkék mellett.
4.  Kattintson a **kijelölés** > **OK gombra**.

## <a name="add-the-app"></a>Az alkalmazás hozzáadása
Ha végzett a konfigurálással, válassza a **Hozzáadás** lehetőséget az **alkalmazás-alkalmazás** ablaktáblán. 

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

> [!NOTE]
> Jelenleg az Apple nem biztosít módot arra, hogy az Intune eltávolítsa a Microsoft Edge-t macOS-eszközökön.

## <a name="next-steps"></a>További lépések
- A Microsoft Edge macOS-eszközökön való konfigurálásával kapcsolatos további információkért lásd: [a Microsoft Edge beállítása MacOS-eszközökön](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Felhasználói csoportok esetében az alkalmazás-hozzárendelések belefoglalásáról és kizárásáról az [Alkalmazás-hozzárendelések belefoglalása vagy kizárása](~/apps/apps-inc-exl-assignments.md) című témakörben talál további információkat.
- [Alkalmazások hozzárendelése csoportokhoz](~/apps/apps-deploy.md)

