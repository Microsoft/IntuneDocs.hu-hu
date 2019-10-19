---
title: A Microsoft Edge for Windows 10 hozzáadása a Microsoft Intunehoz
titleSuffix: ''
description: Ismerje meg, hogyan adhat hozzá Microsoft Edge for Windows-t a Microsoft Intunehoz.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2019
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
ms.openlocfilehash: 492feb3f2ef5f5bbbc1537d4c60ac12d5fd6bdcd
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585860"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>A Microsoft Edge for Windows 10 hozzáadása a Microsoft Intunehoz

Az alkalmazások üzembe helyezése, konfigurálása, monitorozása vagy védelemmel való ellátása előtt hozzá kell adnia őket az Intune-hoz. Az elérhető [alkalmazások](~/apps/apps-add.md#app-types-in-microsoft-intune) egyike a Microsoft Edge *77-es és újabb verziója*. Ha ezt az alkalmazást az Intune-ban kiválasztja, a Microsoft Edge *77-es vagy újabb verzióját* a Windows 10 rendszert futtató eszközökhöz rendelheti hozzá és telepítheti.

> [!IMPORTANT]
> Az alkalmazás típusa **nyilvános előzetes** verzióban érhető el, és fejlesztői és bétaverziós csatornákat kínál a Windows 10 rendszerhez. A központi telepítés csak angol (EN) nyelven érhető el, de a végfelhasználók a **beállítások**  > **nyelvek**területen módosíthatják a böngésző megjelenítési nyelvét. A Microsoft Edge egy, a rendszerkörnyezetben és hasonló architektúrákban telepített Win32-alkalmazás (x86-OS és x64-es OS-es x64-es alkalmazás). Emellett az Edge automatikus frissítései alapértelmezés szerint **be vannak kapcsolva** , és az Edge nem távolítható el.

> [!NOTE]
> A Microsoft Edge *77-es és újabb* verziói a MacOS-re is elérhetők.
> 
> A munkahelyi csatlakoztatási számítógépeken a Microsoft Edge beépített alkalmazás-telepítése nem használható. A beépített alkalmazás üzembe helyezéséhez az Intune felügyeleti bővítmény szükséges, amely csak a HRE-hez csatlakoztatott eszközökhöz létezik. Továbbra is telepítheti a Microsoft Edge *77-es vagy újabb verzióját* az **ügyfélalkalmazások**számára feltöltött *. msi* használatával: [Windowsos üzletági alkalmazások hozzáadása a Microsoft Intunehoz](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Előfeltételek
- A Windows 10 RS2 és újabb verziójának megadása kötelező.
- A Microsoft Edge *77-es és újabb verziójának* előre telepített verzióit a felhasználói környezetben a **fejlesztői** és a **bétaverziós** csatornák esetében a rendszer felülírja a rendszerkörnyezetben telepített Edge-vel.

## <a name="configure-the-app-in-intune"></a>Az alkalmazás konfigurálása az Intune-ban
A Microsoft Edge 77-es vagy újabb verzióját a következő lépésekkel adhatja hozzá az Intune-hoz:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Az **Intune** panelen válassza az **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** elemet.
3. Az **alkalmazás típusa** listában a **Microsoft Edge 77-es és újabb verziójában**válassza a **Windows 10**lehetőséget.

## <a name="configure-app-information"></a>Az alkalmazásadatok konfigurálása
Ebben a lépésben az alkalmazás telepítésével kapcsolatos információkat nyújt. Ez az információ segít azonosítani az alkalmazást az Intune-ban, és segít a felhasználóknak megkeresni az alkalmazást a vállalati portálon.

1. **Az alkalmazásadatok** panel megjelenítéséhez kattintson az **alkalmazás adatai** elemre.
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
2. Az **Alkalmazásbeállítások** panelen válassza a **csatorna** listából a **Beta** vagy a **dev** lehetőséget annak meghatározásához, hogy melyik peremhálózati csatornát fogja telepíteni az alkalmazásból.
    - **Bétaverzió** A Channel a Microsoft Edge legstabilabb előzetes verziója, és a legjobb választás a teljes pilóta számára a szervezeten belül. A főbb frissítések 6 hetente minden kiadásban a fejlesztői csatorna megismeréseit és fejlesztéseit is magában foglalja.
    - **Fejlesztői** A Channel készen áll a vállalati visszajelzésekre Windows, Windows Server és macOS rendszereken. Minden héten frissül, és tartalmazza a legújabb javításokat és javításokat.

    > [!NOTE]
    > A Microsoft Edge böngésző emblémája az alkalmazással jelenik meg, amikor a felhasználók megkeresik a vállalati portált.

3.  Válassza az **OK** gombot.

## <a name="select-scope-tags-optional"></a>Hatóköri címkék kiválasztása (nem kötelező)
A hatókör-címkék használatával meghatározhatja, hogy ki láthatja az ügyfélalkalmazások adatait az Intune-ban. A hatókör-címkék részletes ismertetését lásd: a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez.
1.  Válassza a **hatókör (címkék)**  > **Hozzáadás**elemet.
2.  A **Select (kijelölés** ) mező használatával keresheti meg a hatókör címkéit.
3.  Jelölje be a jelölőnégyzetet az alkalmazáshoz hozzárendelni kívánt hatókör-címkék mellett.
4.  Kattintson a **kijelölés**  > **OK gombra**.

## <a name="add-the-app"></a>Az alkalmazás hozzáadása
Ha befejezte az alkalmazás konfigurálását, válassza a **Hozzáadás** lehetőséget az **alkalmazás-alkalmazás** paneljén. 

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

> [!NOTE]
> Ha törli a Microsoft Edge központi telepítésének hozzárendelését, az az eszközön marad.

## <a name="troubleshooting"></a>Hibaelhárítás
**A Microsoft Edge 77-es és újabb verziói a Windows 10 rendszerhez:**<br>
Az Intune az Intune felügyeleti bővítmény használatával tölti le és telepíti a Microsoft Edge telepítőjét a Windows 10-es eszközökhöz, majd a Microsoft Edge-böngésző letöltésével és telepítésével továbbítja a központi telepítési beállításokat a Microsoft Edge telepítőjének. közvetlenül a CDN-ből. Az [Intune felügyeleti bővítmény előfeltételei](~/apps/intune-management-extension.md#prerequisites), valamint az Azure Update szolgáltatás és a CDN elérése című cikkben ismertetett ajánlott eljárások, amelyek biztosítják, hogy a hálózati konfiguráció lehetővé tegye, hogy a Windows 10-es eszközök hozzáférjenek ezekhez a helyekhez.

## <a name="next-steps"></a>További lépések
- [Alkalmazások hozzárendelése csoportokhoz](~/apps/apps-deploy.md)
