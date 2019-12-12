---
title: 'Lásd: Eszközprofilok a Microsoft Intune-ban – Azure | Microsoft Docs'
description: Megtekintheti és kezelheti az eszközkonfigurációs profilok adatait a Microsoft Intune-ban, egy grafikus diagramon tekintheti meg a profilokhoz rendelt eszközök számát, és megtekintheti, mely eszközök rendelkeznek hozzárendelt vagy üzembe helyezett profillal. Az ütközést okozó beállításokkal rendelkező profilok hibaelhárítása is elvégezhető.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85ba34cfec8ebe78d2574034967bd7ed76f3304e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059549"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Eszközprofilok figyelése a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune néhány funkciót is tartalmaz, amelyek segítségével figyelheti és kezelheti az eszköz konfigurációs profiljait. Például ellenőrizheti egy profil állapotát, megtekintheti a hozzárendelt eszközöket, és frissítheti a profiltulajdonságokat.

## <a name="view-existing-profiles"></a>Meglévő profilok megtekintése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok**lehetőséget.

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

## <a name="device-firmware-configuration-interface-profile-reporting"></a>Eszköz belső vezérlőprogram konfigurációs felületi profiljának jelentése

> [!WARNING]
> Folyamatban van a DFCI-profilok figyelése. Habár a DFCI nyilvános előzetes verzióban érhető el, előfordulhat, hogy a figyelési adatvesztés vagy hiányos.

A DFCI-profilokat egy beállítás alapján kell jelenteni, ugyanúgy, mint az egyéb eszköz-konfigurációs profilokhoz. A gyártó DFCI függően előfordulhat, hogy egyes beállítások nem érvényesek.

A DFCI-profil beállításaival a következő állapotok jelenhetnek meg:

- **Megfelelő**: ez az állapot akkor jelenik meg, ha a profilban beállított érték megegyezik az eszköz beállításával. Ez az állapot a következő esetekben fordulhat elő:

  - A DFCI-profil sikeresen konfigurálta a beállítást a profilban.
  - Az eszköz nem rendelkezik a beállítás által vezérelt hardver-szolgáltatással, és a profil beállítása **le van tiltva**.
  - Az UEFI nem engedélyezi a DFCI számára a funkció letiltását, és a profil beállítása **engedélyezve**van.
  - Az eszköz nem rendelkezik a funkció letiltásához szükséges hardverrel, és a profil beállítása **engedélyezve**van.

- **Nem alkalmazható**: ez az állapot akkor jelenik meg, ha a profilban a beállítás értéke **engedélyezve**van, és az eszközön nem található a megfelelő beállítás. Ez az állapot akkor fordulhat elő, ha az eszköz hardvere nem rendelkezik a szolgáltatással.

- Nem **megfelelő**: ez az állapot akkor jelenik meg, ha a profilban beállított érték nem egyezik meg az eszköz beállításával. Ez az állapot a következő esetekben fordulhat elő:

  - Az UEFI nem engedélyezi a DFCI számára a beállítások letiltását, és a profil beállítása **le van tiltva**.
  - Az eszköz nem rendelkezik a funkció letiltásához szükséges hardverrel, és a profil beállítása **le van tiltva**.
  - Az eszközön nincs a legújabb DFCI belső vezérlőprogram-verziója.
  - A DFCI le lett tiltva az Intune-ban a helyi "letiltási" vezérlő használatával az UEFI menüjében.
  - Az eszköz regisztrálva van az Intune-ban az Autopilot-regisztráción kívül.
  - Az eszköz nincs regisztrálva egy Microsoft CSP-nek, vagy közvetlenül az OEM által regisztrálva.

## <a name="next-steps"></a>További lépések

[Az eszközök profiljaival kapcsolatos gyakori kérdések, problémák és megoldások](device-profile-troubleshoot.md)  
[Szabályzatok és profilok és az Intune hibáinak megoldása](troubleshoot-policies-in-microsoft-intune.md)
