---
title: 'Lásd: Eszközprofilok a Microsoft Intune-ban – Azure | Microsoft Docs'
description: Megtekintheti és kezelheti az eszközkonfigurációs profilok adatait a Microsoft Intune-ban, egy grafikus diagramon tekintheti meg a profilokhoz rendelt eszközök számát, és megtekintheti, mely eszközök rendelkeznek hozzárendelt vagy üzembe helyezett profillal. Az ütközést okozó beállításokkal rendelkező profilok hibaelhárítása is elvégezhető.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/14/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17057100f9bc762de8c679880145014cf5806432
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584862"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Eszközprofilok figyelése a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune néhány funkciót is tartalmaz, amelyek segítségével figyelheti és kezelheti az eszköz konfigurációs profiljait. Például ellenőrizheti egy profil állapotát, megtekintheti a hozzárendelt eszközöket, és frissítheti a profiltulajdonságokat.

## <a name="view-existing-profiles"></a>Meglévő profilok megtekintése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** lehetőséget.

Itt mindegyik meglévő profil megjelenik olyan adatokkal, mint a platform, és megmutatja a profil eszköz-hozzárendelési állapotát is.

## <a name="view-details-on-a-profile"></a>Egy profil adatainak megtekintése

Az eszközprofil létrehozása után az Intune grafikus diagramokat nyújt. Ezek a diagramok a profilok állapotát jelenik meg, például, hogy hozzá vannak-e rendelve eszközökhöz, vagy tartalmaznak-e ütközéseket.

1. Válasszon ki egy meglévő profilt, például egy macOS-profilt.
2. Lépjen az **Áttekintés** fülre.

    A felső grafikus diagram az eszköz profiljához rendelt eszközök számát jeleníti meg. Ha például az eszközprofil macOS-eszközökre van alkalmazva, akkor a diagram csak a macOS-eszközök számát jeleníti meg.

    Emellett más platformok eszközeinek számát is megjeleníti, ha ezek ugyanahhoz az eszközprofilhoz vannak rendelve. Például megtekintheti a nem macOS-eszközök számát.

    ![Az eszközprofilhoz rendelt eszközök számának megtekintése](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    Az alsó grafikus diagram az eszköz profiljához rendelt felhasználók számát jeleníti meg. Ha például az eszközprofil macOS-felhasználókra van alkalmazva, akkor a diagram a macOS-felhasználók számát jeleníti meg.

3. Kattintson a felső grafikus diagramon látható körre. Ekkor megnyílik az **Eszközállapot** menü.

    Itt láthatja a profilhoz rendelt eszközöket, valamint azt, hogy a profilt sikeresen üzembe helyezték-e. Ne feledje, hogy itt csak a megadott platform eszközei jelennek meg (például macOS).

    Zárja be az **Eszközállapot** adatait.

4. Kattintson az alsó grafikus diagramon látható körre. Ekkor megnyílik a **Felhasználó állapota** menü. 

    Itt láthatja a profilhoz rendelt felhasználókat, valamint azt, hogy a profilt sikeresen üzembe helyezték-e. Ne feledje, hogy itt csak a megadott platform (például macOS) felhasználói jelennek meg.

    Zárja be a **Felhasználó állapota** adatait.

5. Miután visszalépett a **Profilok** listára, válasszon ki egy adott profilt. A meglévő tulajdonságokat is módosíthatja:
    - **Tulajdonságok**: Módosíthatja a nevet, vagy frissítheti a meglévő beállításokat.
    - **Hozzárendelések**: Belefoglalhat vagy kizárhat a szabályzat hatálya alá tartozó eszközöket. Adott csoportok kiválasztásához válassza a **Kiválasztott csoportok** lehetőséget.
    - **Eszközállapot**: Itt láthatja a profilhoz rendelt eszközöket, valamint azt, hogy a profilt sikeresen üzembe helyezték-e. Egy adott eszközt kijelölve még több adatot megtekinthet, például a telepített alkalmazásokat.
    - **Felhasználói állapot**: felsorolja a profil által érintett eszközökkel rendelkező felhasználóneveket, valamint a profil sikeres üzembe helyezését. Egy adott felhasználót kijelölve még több adatot megtekinthet.
    - **Állapot beállításonként**: A kimenetet szűri a profil egyes beállításait megjelenítve, valamint megmutatja, hogy a beállítást sikeresen alkalmazták-e.

## <a name="view-conflicts"></a>Ütközések megtekintése

Az **Eszközök** > **Minden eszköz** területen megtekintheti az ütközést okozó beállításokat. Ütközés esetén a beállítást tartalmazó összes konfigurációs profil is megjelenik. A rendszergazdák ezzel a funkcióval hibakeresést végezhetnek, és elháríthatják a profilok hibáit is.

1. Az Intune-ban válassza az **Eszközök** > **Minden eszköz** lehetőséget, majd válasszon ki a listából egy meglévő eszközt. A végfelhasználók a céges portál alkalmazásban nézhetik meg az eszköz nevét.
2. Válassza az **Eszközök konfigurálása** lehetőséget. Az eszközre alkalmazott összes konfigurációs szabályzat megjelenik.
3. Válassza ki a szabályzatot. Megjelenik a szabályzat összes olyan beállítása, amely az eszközre vonatkozik. Ha egy eszköz **Ütközés** állapotban van, válassza ki a vonatkozó sort. Az új ablakban megjelenik az összes olyan profil és profilnév, amely az ütközést kiváltó beállítást tartalmazza.

Miután ismeri az ütközést okozó beállítást, és tudja, hogy mely szabályzatok tartalmazzák ezt a beállítást, az ütközés elhárítása egyszerűbben elvégezhető. 

## <a name="next-steps"></a>További lépések

[Az eszközök profiljaival kapcsolatos gyakori kérdések, problémák és megoldások](device-profile-troubleshoot.md)  
[Szabályzatok és profilok és az Intune hibáinak megoldása](troubleshoot-policies-in-microsoft-intune.md)
