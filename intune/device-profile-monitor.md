---
title: 'Lásd: Eszközprofilok a Microsoft Intune-ban – Azure | Microsoft Docs'
description: Megtekintheti és kezelheti az eszközkonfigurációs profilok adatait a Microsoft Intune-ban, egy grafikus diagramon tekintheti meg a profilokhoz rendelt eszközök számát, és megtekintheti, mely eszközök rendelkeznek hozzárendelt vagy üzembe helyezett profillal. Az ütközést okozó beállításokkal rendelkező profilok hibaelhárítása is elvégezhető.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4b95894e00ce160323a5951b30eb9621585ea85
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "71303461"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Eszközprofilok figyelése a Microsoft Intune-ban

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az Intune egyes Azure Portalbeli funkcióival figyelheti és kezelheti az eszközkonfigurációs profilokat. Például ellenőrizheti egy profil állapotát, megtekintheti a hozzárendelt eszközöket, és frissítheti a profiltulajdonságokat.

## <a name="view-existing-profiles"></a>Meglévő profilok megtekintése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **Eszközkonfiguráció** > **Profilok** lehetőséget.

Itt mindegyik meglévő profil megjelenik olyan adatokkal, mint a platform, és megmutatja a profil eszköz-hozzárendelési állapotát is.

## <a name="view-details-on-a-profile"></a>Egy profil adatainak megtekintése

Az eszközprofil létrehozása után az Intune grafikus diagramokat nyújt. Ezek a diagramok a profilok állapotát jelenik meg, például, hogy hozzá vannak-e rendelve eszközökhöz, vagy tartalmaznak-e ütközéseket.

1. Válasszon ki egy meglévő profilt, például egy macOS-profilt.
2. Lépjen az **Áttekintés** fülre.

    A felső grafikus diagramon megtekintheti az adott eszközprofilhoz rendelt eszközök számát. Ha például az eszközprofil macOS-eszközökre van alkalmazva, akkor a diagram csak a macOS-eszközök számát jeleníti meg.

    Emellett más platformok eszközeinek számát is megjeleníti, ha ezek ugyanahhoz az eszközprofilhoz vannak rendelve. Például megtekintheti a nem macOS-eszközök számát.

    ![Az eszközprofilhoz rendelt eszközök számának megtekintése](./media/device-configuration-profile-graphical-chart.png)

    Az alsó grafikus diagramon megtekintheti az adott eszközprofilhoz rendelt felhasználók számát. Ha például az eszközprofil macOS-felhasználókra van alkalmazva, akkor a diagram a macOS-felhasználók számát jeleníti meg.

3. Kattintson a felső grafikus diagramon látható körre. Ekkor megnyílik az **Eszközállapot** menü.

    Itt láthatja a profilhoz rendelt eszközöket, valamint azt, hogy a profilt sikeresen üzembe helyezték-e. Ne feledje, hogy itt csak a megadott platform eszközei jelennek meg (például macOS).

    Zárja be az **Eszközállapot** adatait.

4. Kattintson az alsó grafikus diagramon látható körre. Ekkor megnyílik a **Felhasználó állapota** menü. 

    Itt láthatja a profilhoz rendelt felhasználókat, valamint azt, hogy a profilt sikeresen üzembe helyezték-e. Ne feledje, hogy itt csak a megadott platform (például macOS) felhasználói jelennek meg.

    Zárja be a **Felhasználó állapota** adatait.

5. Miután visszalépett a **Profilok** listára, válasszon ki egy adott profilt. A meglévő tulajdonságokat is módosíthatja:
    - **Tulajdonságok**: Módosítsa a nevet, vagy frissítse a meglévő beállításokat.
    - **Hozzárendelések**: A házirend hatálya alá tartozó eszközök belefoglalása vagy kizárása. Adott csoportok kiválasztásához válassza a **Kiválasztott csoportok** lehetőséget.
    - **Eszköz állapota**: Itt láthatja a profilhoz rendelt eszközöket, valamint azt, hogy a profilt sikeresen üzembe helyezték-e. Egy adott eszközt kijelölve még több adatot megtekinthet, például a telepített alkalmazásokat.
    - **Felhasználói állapot**: Felsorolja azokat a felhasználóneveket, amelyek hatással vannak a profil által érintett eszközökre, és ha a profil sikeresen telepítve lett. Egy adott felhasználót kijelölve még több adatot megtekinthet.
    - **/Beállítás állapota**: Kiszűri a kimenetet a profilban lévő egyes beállítások megjelenítésével, és megjeleníti, hogy a beállítás alkalmazása sikeres volt-e.

## <a name="view-conflicts"></a>Ütközések megtekintése

Az **Eszközök** > **Minden eszköz** területen megtekintheti az ütközést okozó beállításokat. Ütközés esetén az összes olyan profil is látható, amely ezt a beállítást tartalmazza. A rendszergazdák ezzel a funkcióval hibakeresést végezhetnek, és elháríthatják a profilok hibáit is.

1. Az Intune-ban válassza az **Eszközök** > **Minden eszköz** lehetőséget, majd válasszon ki a listából egy meglévő eszközt. A végfelhasználók a céges portál alkalmazásban nézhetik meg az eszköz nevét.
2. Válassza az **Eszközök konfigurálása** lehetőséget. Az eszközre alkalmazott összes konfigurációs szabályzat megjelenik.
3. Válassza ki a szabályzatot. Megjelenik a szabályzat összes olyan beállítása, amely az eszközre vonatkozik. Ha egy eszköz **Ütközés** állapotban van, válassza ki a vonatkozó sort. Az új ablakban megjelenik az összes olyan profil és profilnév, amely az ütközést kiváltó beállítást tartalmazza.

Miután ismeri az ütközést okozó beállítást, és tudja, hogy mely szabályzatok tartalmazzák ezt a beállítást, az ütközés elhárítása egyszerűbben elvégezhető. 

## <a name="next-steps"></a>További lépések
[Felhasználói és eszközprofilok hozzárendelése](device-profile-assign.md)  
[Eszközprofilokkal kapcsolatos gyakori problémák és azok megoldása](device-profile-troubleshoot.md)
