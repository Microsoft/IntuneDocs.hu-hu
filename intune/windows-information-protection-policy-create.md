---
title: Létrehozása és üzembe helyezése a Windows Information Protection (WIP) alkalmazásvédelmi szabályzat |} A Microsoft Intune-ban
description: A Windows Information Protection (WIP) alkalmazásvédelmi szabályzatainak létrehozása és bevezetése a Microsoft Intune használatával
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f91f5b9779c3067a3120864eaf265346efd8a02
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297434"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>A Windows Information Protection (WIP) alkalmazásvédelmi szabályzatainak létrehozása és bevezetése az Intune használatával

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10-es alkalmazások esetén az eszközök regisztrálása nélkül használhatja az alkalmazásvédelmi szabályzatokat.

## <a name="before-you-begin"></a>Előkészületek

A WIP szabályzatainak hozzáadásához célszerű tisztában lenni néhány fogalommal:

### <a name="list-of-allowed-and-exempt-apps"></a>Az engedélyezett és mentesített alkalmazások listája

-   **Védett alkalmazások:** Ezek az alkalmazások be kell tartaniuk az ezt a házirendet.

-   **Kivételt képező alkalmazások:** Ezek az alkalmazások mentesülnek a szabályzat, és hozzáférhet a vállalati adatok korlátozás nélkül.

### <a name="types-of-apps"></a>Alkalmazások típusai

-   **Ajánlott alkalmazások:** Előre összeállított lista (leginkább Microsoft Office-) alkalmazásokat, amelyek egyszerűen házirend importálása.
-   **Store-alkalmazások:** A Windows áruházból bármilyen alkalmazást felvehet a szabályzatba.
-   **Windows asztali alkalmazások:** Bármilyen hagyományos asztali Windows-alkalmazást is hozzáadhat a házirendet (például .exe, .dll stb.)

## <a name="prerequisites"></a>Előfeltételek

A WIP alkalmazásvédelmi szabályzatainak létrehozása előtt be kell állítania a MAM-szolgáltatót. További információk a [MAM-szolgáltató konfigurálásáról az Intune segítségével](app-protection-policies-configure-windows-10.md).  

> [!IMPORTANT]
> A WIP nem támogatja a többszörös identitás használatát, egyidejűleg csak egyetlen felügyelt identitás létezhet.

Emellett rendelkeznie kell a következő licenccel és frissítéssel:

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) licenc
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)





## <a name="to-add-a-wip-app-protection-policy"></a>Alkalmazásvédelmi WIP-szabályzatok hozzáadása

Miután cégénél beállította az Intune-t, létrehozhat WIP-specifikus szabályzatokat.

> [!TIP]  
> Az Intune-ban a WIP-szabályzatok létrehozásával – beleértve az elérhető beállításokkal és a konfigurálásuk módjával – kapcsolatosan a Windows rendszerbiztonsági dokumentáció gyűjteményében, a [Windows Information Protection (WIP) szabályzatainak MAM használatával, a Microsoft Intune Azure Portaljával való létrehozásáról szóló szakaszban](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure) talál további információt. 


1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).
2. Válassza a **Minden szolgáltatás** > **Intune** lehetőséget.
3. A **Microsoft Intune** panelen válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** panelen válassza az **Alkalmazásvédelmi szabályzatok** lehetőséget.
5. Válassza a **Szabályzat hozzáadása** lehetőséget a **Szabályzat hozzáadása** panel megjelenítéséhez.
6. Adja meg a következő értékeket:
    - **név:** Adja meg (kötelező) az új házirend nevét.
    - **Leírás:** (Nem kötelező) Adjon meg egy leírást.
    - **Platform:** Válasszon **Windows 10-es** , az alkalmazásvédelmi szabályzat támogatott platformjának.
    - **Regisztráció állapota:** Válasszon **regisztráció nélkül** , a szabályzat regisztrációs állapotaként.
7.  Válassza a **Létrehozás** lehetőséget. A szabályzat létrejön, és megjelenik az **Alkalmazásvédelmi szabályzatok** panelen található táblázatban.

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>Javasolt alkalmazások hozzáadása a védett alkalmazások listájához

1. A **Microsoft Intune** panelen válassza az **Ügyfélalkalmazások** lehetőséget.
2. Az **Ügyfélalkalmazások** panelen válassza az **Alkalmazásvédelmi szabályzatok** lehetőséget.
3. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot. Megjelenik az **Intune App Protection** panel.
4. Az **Intune App Protection** panelen válassza a **Védett alkalmazások** lehetőséget. Megnyílik a **Védett alkalmazások** panel, ahol azoknak az alkalmazásoknak a listáját láthatja, amelyekre ez a szabályzat vonatkozik.
5. Válassza a **Alkalmazások hozzáadása** lehetőséget. Az **Alkalmazások hozzáadása** területen megtekintheti a szűrt alkalmazáslistát. A panel tetején található listával módosíthatja a listaszűrőt.
6. Válassza ki azokat az alkalmazásokat, amelyeknek hozzáférést kíván adni a céges adatokhoz.
7. Kattintson az **OK** gombra. A **Védett alkalmazások** panel frissül, és kibővül a kiválasztott alkalmazásokkal.
8. Kattintson a **Save** (Mentés) gombra.

## <a name="add-a-store-app-to-your-protected-apps-list"></a>Áruházbeli alkalmazás hozzáadása a védett alkalmazások listájához

**Áruházbeli alkalmazás hozzáadása**
1. A **Microsoft Intune** panelen válassza az **Ügyfélalkalmazások** lehetőséget.
2. Az **Ügyfélalkalmazások** panelen válassza az **Alkalmazásvédelmi szabályzatok** lehetőséget.
3. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot. Megjelenik az **Intune App Protection** panel.
4. Az **Intune App Protection** panelen válassza a **Védett alkalmazások** lehetőséget. Megnyílik a **Védett alkalmazások** panel, ahol azoknak az alkalmazásoknak a listáját láthatja, amelyekre ez a szabályzat vonatkozik.
5. Válassza a **Alkalmazások hozzáadása** lehetőséget. Az **Alkalmazások hozzáadása** területen megtekintheti a szűrt alkalmazáslistát. A panel tetején található listával módosíthatja a listaszűrőt.
6. Válassza az **Áruházbeli alkalmazások** lehetőséget a listában.
7. Adja meg a **Név**, a **Közzétevő**, a **Terméknév** és a **Művelet** értékét. A **Művelet** értéket **Engedélyezésre** állítsa, így az alkalmazás hozzáférhet a vállalati adatokhoz.
9. Kattintson az **OK** gombra. A **Védett alkalmazások** panel frissül, és kibővül a kiválasztott alkalmazásokkal.
10. Kattintson a **Save** (Mentés) gombra.

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>Asztali alkalmazás hozzáadása az védett alkalmazások listájához

**Asztali alkalmazás hozzáadása**
1. A **Microsoft Intune** panelen válassza az **Ügyfélalkalmazások** lehetőséget.
2. Az **Ügyfélalkalmazások** panelen válassza az **Alkalmazásvédelmi szabályzatok** lehetőséget.
3. Az **Alkalmazásvédelmi szabályzatok** panelen válassza ki a módosítani kívánt szabályzatot. Megjelenik az **Intune App Protection** panel.
4. Az **Intune App Protection** panelen válassza a **Védett alkalmazások** lehetőséget. Megnyílik a **Védett alkalmazások** panel, ahol azoknak az alkalmazásoknak a listáját láthatja, amelyekre ez a szabályzat vonatkozik.
5. Válassza a **Alkalmazások hozzáadása** lehetőséget. Az **Alkalmazások hozzáadása** területen megtekintheti a szűrt alkalmazáslistát. A panel tetején található listával módosíthatja a listaszűrőt.
6. Válassza az **Asztali alkalmazások** lehetőséget a listában.
7. Adja meg a **Név**, a **Közzétevő**, a **Terméknév**, a **Fájl**, a **Legalacsonyabb verzió**, a **Maximális verzió** és a **Művelet** értékét. A **Művelet** értéket **Engedélyezésre** állítsa, így az alkalmazás hozzáférhet a vállalati adatokhoz.
9. Kattintson az **OK** gombra. A **Védett alkalmazások** panel frissül, és kibővül a kiválasztott alkalmazásokkal.
10. Kattintson a **Save** (Mentés) gombra.

## <a name="wip-learning"></a>WIP Learning
A WIP által védeni kívánt alkalmazások hozzáadása után alkalmazni kell azokon az egyik védelmi módot a **WIP Learning** használatával.

### <a name="before-you-begin"></a>Előkészületek

A WIP Learning egy olyan jelentés, amellyel a WIP szolgáltatással együttműködő és a WIP számára ismeretlen alkalmazásokat figyelheti. Ismeretlennek számítanak az olyan alkalmazások, amelyeket nem a munkahelyi IT-részleg helyezett üzembe. Ezeket az alkalmazásokat exportálhatja a jelentésből, és a zavartalan munka érdekében hozzáadhatja őket a WIP-szabályzatokhoz, mielőtt kikényszerítik a WIP „Letiltás” módját.

<!-- 1631908 --> A WIP szolgáltatással együttműködő alkalmazások adatainak megtekintése mellett megtekintheti a webhelyekkel munkahelyi adatokat megosztó eszközök összegzését is. Ezen adatok alapján megállapíthatja, hogy mely webhelyeket kell hozzáadnia a csoportszabályzatokhoz és a WIP-szabályzatokhoz. Az összegzés megmutatja, mely webes URL-címekhez férnek hozzá a WIP szolgáltatással együttműködő alkalmazások.

A WIP szolgáltatással együttműködő és a WIP számára ismeretlen alkalmazások használatakor javasolt, hogy először a **Csendes** vagy a **Felülbírálások engedélyezése** módot válassza, és egy kisebb csoporton ellenőrizze, hogy a megfelelő alkalmazások szerepelnek a védett alkalmazások listájában. Ha ezzel végzett, átválthat a végleges kényszerítési szabályzatra, a **Letiltás** módra.

### <a name="what-are-the-protection-modes"></a>Milyen védelmi módok lehetségesek?

#### <a name="block"></a>Letiltás
A WIP figyeli a nem megfelelő adatmegosztási gyakorlatot, és megakadályozza, hogy a felhasználó elvégezze az adott műveletet. Letiltott műveletnek számíthat, ha nem céges védelem alatt álló alkalmazásokkal osztanak meg információt, vagy ha a szervezeten kívüli személyekkel és eszközökkel osztanak meg céges adatokat.

#### <a name="allow-overrides"></a>Felülbírálások engedélyezése
A WIP figyeli a nem megfelelő adatmegosztásokat, és figyelmezteti a felhasználót az esetlegesen nem biztonságos tevékenységre. Ebben a módban azonban a felhasználónak lehetősége van a szabályzat felülbírálásával megosztani az adatokat, a tevékenység pedig megjelenik a műveleti naplóban.

#### <a name="silent"></a>Csendes
A WIP csendes módban üzemel, és úgy naplózza a nem megfelelő adatmegosztásokat, hogy nem akadályozza meg azokat a tevékenységeket, amelyek esetében a Felülbírálások engedélyezése módban figyelmeztetések jelennének meg a felhasználó számára. A nem engedélyezett műveletek azonban továbbra is tiltva vannak, például hálózati erőforrások vagy WIP-védelem alatt álló adatok nem megfelelő elérése.

#### <a name="off-not-recommended"></a>Kikapcsolva (nem ajánlott)
A WIP ki van kapcsolva, így nem védi és nem naplózza az adatokat.

A WIP kikapcsolása után a rendszer megkísérli visszafejteni a WIP-címkével ellátott fájlokat a csatlakoztatott helyszíni meghajtókon. Vegye figyelembe, hogy a WIP-védelem újbóli bekapcsolásakor a korábbi visszafejtési és szabályzatinformációk nem lesznek automatikusan újra alkalmazva.

### <a name="add-a-protection-mode"></a>Védelmi mód hozzáadása

1.  Az **Alkalmazásszabályzat** panelen válassza ki a kívánt szabályzat nevét, majd válassza a **Kötelező beállítások** lehetőséget.

    ![A tanulási mód panel képernyőképe](./media/learning-mode-sc1.png)

1.  Válasszon egy beállítást, majd a **Mentés** lehetőséget.

### <a name="use-wip-learning"></a>A WIP Learning használata

1. Nyissa meg az [Azure Portalt](https://portal.azure.com). Válassza a **Minden szolgáltatás** lehetőséget. A szövegmezőbe írja be az **Intune** szót.

3. Válassza az **Intune** > **Ügyfélalkalmazások** lehetőséget.

4. Válassza az **Alkalmazásvédelem állapota** > **Jelentések** > **Windows Information Protection Learning** elemet.  

    A WIP Learning naplójelentésében szereplő alkalmazásokat ezután exportálhatja az alkalmazásvédelmi szabályzatokba.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Titkosított elemek keresésének engedélyezése a Windows Search szolgáltatás indexelőprogramjában
Engedélyezi vagy tiltja az elemek indexelését. Ez a Windows Search szolgáltatás indexelőprogramjára vonatkozó kapcsoló határozza meg, hogy indexelendők-e a titkosított, például a Windows Információvédelem (WIP) által védett fájlok.

Ez az alkalmazásvédelmi szabályzat a Windows Információvédelem szabályzatának **Speciális beállításai** között található. Az alkalmazásvédelmi szabályzatot a *Windows 10* platformhoz kell beállítani, az alkalmazásszabályzat **Regisztrációs állapot** értékeként pedig a **Regisztrációval** értéket kell megadni.

A szabályzat engedélyezésekor a WIP által védett elemek indexelve lesznek, a velük kapcsolatos metaadatok pedig titkosítatlan helyen lesznek tárolva. A metaadatok között szerepel egyebek között a fájl elérési útja és módosításának dátuma.

A szabályzat tiltásakor a WIP által védett elemek nem lesznek indexelve és nem jelennek meg a Cortana vagy a fájlkezelő eredményei között. A Fényképek és a Groove alkalmazás teljesítménye csökkenhet, ha nagy mennyiségű WIP-védelemmel ellátott médiafájl található az eszközön.

## <a name="add-encrypted-file-extensions"></a>Titkosított fájlok kiterjesztéseinek megadása

A **Titkosított elemek keresésének engedélyezése a Windows Search szolgáltatás indexelőprogramjában** beállítás mellett egy fájlkiterjesztésekből álló lista is megadható. Az ilyen kiterjesztésű fájlok titkosítva lesznek, ha Server Message Block (SMB) megosztásról másolják őket a vállalatnak a hálózati helyek listája alapján meghatározott területén belül. Ha ez a szabályzat nincs beállítva, akkor a meglévő automatikus titkosítás lesz alkalmazva. Ha ez a szabályzat be van állítva, akkor csak a listában szereplő kiterjesztésű fájlok lesznek titkosítva.

## <a name="deploy-your-wip-app-protection-policy"></a>WIP alkalmazásvédelmi szabályzat bevezetése

> [!IMPORTANT]
> Az alábbi információk az WIP eszközregisztráció nélküli használatára vonatkoznak.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

A WIP alkalmazásvédelmi szabályzat létrehozása után a MAM használatával kell bevezetnie azt a cégnél.

1.  Az **Alkalmazásszabályzat** panelen válassza ki az újonnan létrehozott alkalmazásvédelmi szabályzatot, majd válassza a **Felhasználói csoportok** > **Felhasználói csoport hozzáadása** elemet.

    A **Felhasználói csoport hozzáadása** panelen megjelenik az Azure Active Directoryban elérhető összes felhasználói csoport listája.

2.  Válassza ki azt a csoportot, amelyre alkalmazni szeretné a szabályzatot, majd válassza a **Kiválasztás** lehetőséget a szabályzat üzembe helyezéséhez.

## <a name="next-steps"></a>További lépések

További információk a Windows információvédelemről: [Vállalati adatok védelme a Windows információvédelemmel (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
