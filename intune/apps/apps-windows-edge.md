---
title: A Microsoft Edge for Windows 10 hozzáadása a Microsoft Intunehoz
titleSuffix: ''
description: Ismerje meg, hogyan adhat hozzá Microsoft Edge for Windows-t a Microsoft Intunehoz.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/03/2020
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
ms.openlocfilehash: 8d5082376c42ff3b92e3979a53b6deac3e59c88e
ms.sourcegitcommit: 32391f74241ee3289a76ccd5319fe700b800d427
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2020
ms.locfileid: "77075807"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>A Microsoft Edge for Windows 10 hozzáadása a Microsoft Intunehoz

Az alkalmazások üzembe helyezése, konfigurálása, monitorozása vagy védelemmel való ellátása előtt hozzá kell adnia őket az Intune-hoz. Az elérhető [alkalmazások](~/apps/apps-add.md#app-types-in-microsoft-intune) egyike a Microsoft Edge *77-es és újabb verziója*. Ha ezt az alkalmazást az Intune-ban kiválasztja, a Microsoft Edge *77-es vagy újabb verzióját* a Windows 10 rendszert futtató eszközökhöz rendelheti hozzá és telepítheti.

> [!IMPORTANT]
> Az alkalmazás típusa **nyilvános előzetes** verzióban érhető el, és stabil, bétaverziós és fejlesztői csatornákat kínál a Windows 10 rendszerhez. A központi telepítés csak angol (EN) nyelven érhető el, de a végfelhasználók a **beállítások** > **nyelvek**területen módosíthatják a böngésző megjelenítési nyelvét. A Microsoft Edge egy, a rendszerkörnyezetben és hasonló architektúrákban telepített Win32-alkalmazás (x86-OS és x64-es OS-es x64-es alkalmazás). Az Intune észlelni fogja a Microsoft Edge összes meglévő telepítését. Ha a felhasználói környezetben van telepítve, a rendszer telepítése felülírja azt. Ha a rendszerkörnyezetbe van telepítve, a rendszer a telepítés sikerességét jelenti. Emellett a Microsoft Edge automatikus frissítései alapértelmezés szerint **be vannak kapcsolva** .

> [!NOTE]
> A Microsoft Edge *77-es és újabb* verziói a MacOS-re is elérhetők.
> 
> A munkahelyi csatlakoztatási számítógépeken a Microsoft Edge beépített alkalmazás-telepítése nem használható. A beépített alkalmazás üzembe helyezéséhez az Intune felügyeleti bővítmény szükséges, amely csak a HRE-hez csatlakoztatott eszközökhöz létezik. Továbbra is telepítheti a Microsoft Edge *77-es vagy újabb verzióját* az **alkalmazásba**feltöltött *. msi* használatával: [Windowsos üzletági alkalmazások hozzáadása a Microsoft Intunehoz](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Előfeltételek
- A Windows 10 RS2 és újabb verziójának megadása kötelező.
- A Microsoft Edge *77-es és újabb verziójának* összes előre telepített verziója a felhasználói környezetben lévő összes csatornára felülírva lesz a rendszerkörnyezetben telepített peremhálózati állapottal.

## <a name="configure-the-app-in-intune"></a>Az alkalmazás konfigurálása az Intune-ban
A Microsoft Edge 77-es vagy újabb verzióját a következő lépésekkel adhatja hozzá az Intune-hoz:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusa** listában a **Microsoft Edge 77-es és újabb verziójában**válassza a **Windows 10**lehetőséget.

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

## <a name="configure-app-settings"></a>Alkalmazásbeállítások konfigurálása
Ebben a lépésben konfigurálja az alkalmazás telepítési beállításait.

1. Az **alkalmazás hozzáadása** panelen válassza az **Alkalmazásbeállítások**lehetőséget.
2. Az **Alkalmazásbeállítások** ablaktáblán válassza a **STABLE**, a **Beta** vagy a **dev** lehetőséget a **Channel (csatorna** ) listából annak meghatározásához, hogy melyik peremhálózati csatornát fogja telepíteni az alkalmazásból.
    - A **stabil** csatorna az ajánlott csatorna, amellyel széles körben üzembe helyezhetők a nagyvállalati környezetek. Hat hetente frissül, és minden kiadás a Beta Channel szolgáltatással kapcsolatos fejlesztési funkciókat tartalmaz.
    - A Beta Channel a legstabilabb Microsoft Edge előzetes **verziója** , és a legjobb választás a teljes pilóta számára a szervezeten belül. A főbb frissítések 6 hetente minden kiadásban a fejlesztői csatorna megismeréseit és fejlesztéseit is magában foglalja.
    - A **fejlesztői** csatorna készen áll a vállalati visszajelzésekre Windows, Windows Server és MacOS rendszereken. Minden héten frissül, és tartalmazza a legújabb javításokat és javításokat.

    > [!NOTE]
    > A Microsoft Edge böngésző emblémája az alkalmazással jelenik meg, amikor a felhasználók megkeresik a vállalati portált.

3.  Válassza az **OK** gombot.

## <a name="select-scope-tags-optional"></a>Hatóköri címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez.
1.  Válassza a **hatókör (címkék)**  > **Hozzáadás**elemet.
2.  A **Select (kijelölés** ) mező használatával keresheti meg a hatókör címkéit.
3.  Jelölje be a jelölőnégyzetet az alkalmazáshoz hozzárendelni kívánt hatókör-címkék mellett.
4.  Kattintson a **kijelölés** > **OK gombra**.

## <a name="add-the-app"></a>Az alkalmazás felvétele
Ha befejezte az alkalmazás konfigurálását, válassza a **Hozzáadás** lehetőséget az **alkalmazás-alkalmazás** ablaktáblán. 

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

> [!NOTE]
> Ha törli a Microsoft Edge központi telepítésének hozzárendelését, az az eszközön marad.

## <a name="uninstall-the-app"></a>Az alkalmazás eltávolítása

Ha el kell távolítania a Microsoft Edge-t a felhasználó eszközeiről, kövesse az alábbi lépéseket.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** lehetőséget, > a *Microsoft Edge* alkalmazás > **hozzárendelések** > **Csoport hozzáadása**elemet.
3. A **Csoport hozzáadása** panelen válassza az **Eltávolítás**lehetőséget.

    > [!NOTE]
    > Az alkalmazást a kiválasztott csoportok eszközeiből távolítja el, ha az Intune már telepítette az alkalmazást az eszközre a **regisztrált eszközökön** vagy a **szükséges** hozzárendelésen keresztül ugyanazzal az üzembe helyezéssel.
4. Válassza ki a **belefoglalt csoportok** lehetőséget az alkalmazás-hozzárendelés által érintett felhasználók csoportjai kiválasztásához.
5. Válassza ki azokat a csoportokat, amelyekre alkalmazni szeretné az eltávolítási hozzárendelést.
6. A **csoportok kiválasztása** panelen kattintson a **kiválasztás** elemre.
7. A hozzárendelés megadásához kattintson az **OK gombra** a **hozzárendelés ablaktáblán** .
8. Ha ki szeretne zárni felhasználói csoportokat az alkalmazás-hozzárendelésből, válassza a **Csoportok kizárása** lehetőséget.
9. Ha valamilyen csoport kizárása mellett döntött, válassza a **Csoportok kiválasztása** ablaktáblán a **Kiválasztás** lehetőséget.
10. A **Csoport hozzáadása** panelen kattintson **az OK gombra** .
11. Válassza a **Mentés** lehetőséget az alkalmazás- **hozzárendelések** ablaktáblán.

> [!IMPORTANT]
> Az alkalmazás sikeres eltávolításához távolítsa el a telepítéshez a tagokat vagy a csoport-hozzárendelést, mielőtt a hozzárendelést el szeretné távolítani. Ha egy csoport egy alkalmazás telepítéséhez és egy alkalmazás eltávolításához is hozzá van rendelve, az alkalmazás továbbra is megmarad, és nem távolítható el.

## <a name="troubleshooting"></a>Hibaelhárítás
**A Microsoft Edge 77-es és újabb verziói a Windows 10 rendszerhez:**<br>
Az Intune az Intune felügyeleti bővítmény használatával tölti le és telepíti a Microsoft Edge telepítőjét a Windows 10-es eszközökhöz, majd a Microsoft Edge-böngésző letöltésével és telepítésével továbbítja a központi telepítési beállításokat a Microsoft Edge telepítőjének. közvetlenül a CDN-ből. Az [Intune felügyeleti bővítmény előfeltételei](~/apps/intune-management-extension.md#prerequisites), valamint az Azure Update szolgáltatás és a CDN elérése című cikkben ismertetett ajánlott eljárások, amelyek biztosítják, hogy a hálózati konfiguráció lehetővé tegye, hogy a Windows 10-es eszközök hozzáférjenek ezekhez a helyekhez. Továbbá, ha engedélyezni szeretné a CDN-ből származó telepítési fájlok elérését a böngésző telepítéséhez, engedélyezni kell Windows Update végpontokhoz való hozzáférést. További információ: a [Windows 10 1809-es verziójának – Windows Update](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update) és [a Microsoft Intune hálózati végpontjának](~/fundamentals/intune-endpoints.md)– a csatlakoztatási végpontok kezelése.

## <a name="next-steps"></a>További lépések
- [Alkalmazások hozzárendelése csoportokhoz](~/apps/apps-deploy.md)
