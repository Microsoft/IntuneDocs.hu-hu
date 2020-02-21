---
title: Eszközmegfelelőségi szabályzatok figyelése az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az eszközmegfelelőségi irányítópulttal figyelheti az eszközmegfelelőségeket, jelentéseket tekinthet meg, valamint megtekintheti a szabályzatonkénti és beállításonkénti eszközmegfelelőségeket.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 128f615a9551c31e6b0e0de4f1d269083874bf48
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515118"
---
# <a name="monitor-intune-device-compliance-policies"></a>Intune-eszközmegfelelőségi szabályzatok figyelése

A megfelelőségi jelentések segítenek az eszközmegfelelőség áttekintésében, és a megfelelőséggel kapcsolatos problémák elhárításában a vállalatánál. Ezeknek a jelentéseknek a használatával a következőkről tekinthet meg információkat:

- Az eszközök összesített megfelelőségi állapota
- Az egyes beállítások megfelelőségi állapota
- Az egyes szabályzatok megfelelőségi állapota
- Egy eszköz részletes vizsgálatával megtekintheti az arra vonatkozó beállításokat és szabályzatokat

## <a name="open-the-compliance-dashboard"></a>A megfelelőségi irányítópult megnyitása

Nyissa meg az **Intune Eszközmegfelelőségi irányítópultját**:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **Áttekintés** > **megfelelőségi állapot** lapot.

> [!IMPORTANT]
> Az eszközmegfelelőségi szabályzatok csak akkor alkalmazhatók az eszközökre, ha azok regisztrálva vannak az Intune-ban.

## <a name="dashboard-overview"></a>Az irányítópult áttekintése

Az irányítópult megnyitásakor átfogó képet kap az összes megfelelőségi jelentésről. Ezekben a jelentésekben a következőket ellenőrizheti:

- Összesített eszközmegfelelőség
- Szabályzatok szerinti eszközmegfelelőség
- Beállítások szerinti eszközmegfelelőség
- Fenyegetésfigyelő ügynök állapota
- Eszközvédelem állapota

![Irányítópult képe az eszközmegfelelőségi irányítópulttal és a különböző jelentésekkel](./media/compliance-policy-monitor/idc-1.png)

A jelentések részletes vizsgálata során láthatja az adott eszközre vonatkozó megfelelőségi szabályzatokat és beállításokat is, köztük az egyes beállítások megfelelőségi állapotát.

### <a name="device-compliance-status"></a>Eszköz megfelelőségi állapota

Az **eszköz megfelelőségi állapotának** diagramja az összes Intune-ban regisztrált eszköz megfelelőségi állapotát mutatja. Az eszközmegfelelőségi állapot adatait két külön adatbázis tárolja: az Intune és az Azure Active Directory.

> [!IMPORTANT]
> Az Intune az eszköz összes megfelelőségi értékeléséhez az eszköz beadási ütemtervét követi. [További információ az eszköz beadásának ütemtervéről](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

A különböző eszközmegfelelőségi szabályzatállapotok leírása:

- **Megfelelő**: az eszköz megfelel egy vagy több eszközmegfelelőségi szabályzat beállításainak.

- **Türelmi időszak**: Az eszközre egy vagy több eszközmegfelelőségi szabályzat lett beállítva. A felhasználó azonban még nem alkalmazta a szabályzatokat. Ez azt jelenti, hogy az eszköz nem megfelelő, de a rendszergazda által meghatározott türelmi időszakban van.

  - További információ a [nem megfelelő eszközökre alkalmazható műveletekről](actions-for-noncompliance.md).

- **Nem értékelt**: Az újonnan regisztrált eszközök kiinduló állapota. Ezen állapot további lehetséges okai a következők:

  - Azok az eszközök, amelyek nem rendelkeznek megfelelőségi szabályzattal, és nem rendelkeznek a megfelelőség ellenőrzéséhez szükséges triggerrel
  - Azok az eszközök, amelyeket nem ellenőriztek a megfelelőségi szabályzat legutóbbi frissítése óta
  - Egy adott felhasználóhoz nem társított eszközök, például:
    - az Apple Készülékregisztrációs programon (DEP) keresztül vásárolt iOS/iPadOS-eszközök, amelyek nem rendelkeznek felhasználói affinitással
    - Androidos kioszk vagy Android Enterprise dedikált eszközök
  - Eszköz beléptetési kezelőjével (DEM) regisztrált eszközök

- **Nem megfelelő**: Az eszköz nem felel meg egy vagy több eszközmegfelelőségi szabályzat beállításainak. Lehetséges, hogy a felhasználó nem a szabályzatoknak megfelelően járt el.

- **Az eszköz nincs szinkronizálva:** az eszköz nem jelentette az eszközmegfelelőségi szabályzat állapotát az alábbi okok miatt:

  - **Ismeretlen**: az eszköz offline állapotban van, vagy valamilyen más okból nem sikerült kapcsolatba lépnie az Intune-nal vagy az Azure AD-vel.

  - **Hiba**: az eszköznek nem sikerült kapcsolatba lépnie az Intune-nal vagy az Azure AD-vel, és üzenetben megkapta a hiba okát.

> [!IMPORTANT]
> A jelentésben a **Megfelelő** gyűjtőben szerepelnek azok az eszközök, amelyek regisztrálva vannak az Intune-ban, de nem vonatkozik rájuk eszközmegfelelőségi szabályzat.

#### <a name="drill-down-for-more-details"></a>További részletezés

Válasszon egy állapotot az **Eszközmegfelelőségi állapot** diagramon. Válassza például a **Nem megfelelő** állapotot:

![A nem megfelelő állapot kiválasztása](./media/compliance-policy-monitor/select-not-compliant-status.png)

Ez a művelet megnyitja az **eszköz megfelelőségi** ablakát, és megjeleníti az eszközök **állapotát az eszköz állapotsorában** . A diagram az adott állapotban lévő eszközök további részleteit jeleníti meg, beleértve az operációs rendszer platformját, az utolsó beadás dátumát és egyebeket.
![irányítópult-rendszerkép további részleteket jelenít meg az adott állapotban lévő eszközről](./media/compliance-policy-monitor/drill-down-details.png)

Ha egy adott felhasználó tulajdonában lévő összes eszközt látni szeretné, a felhasználó e-mail-címének begépelésével szűrni tudja a diagramot tartalmazó jelentést.

#### <a name="filter-and-columns"></a>Szűrő és oszlopok

![A diagramon ábrázolt eredmények módosítása a Szűrő és az Oszlopok lehetőség választásával](./media/compliance-policy-monitor/filter-columns.png)

A **szűrő** gomb kiválasztásakor a szűrő további beállításokkal nyílik meg, beleértve a **megfelelőségi** állapotot, a **feltört eszközöket és** egyebeket. Az eredmények frissítéséhez válassza a Szűrő panelen az **Alkalmaz** lehetőséget.

A diagram-kimenet oszlopainak hozzáadásához és eltávolításához válassza az **Oszlopok** lehetőséget. Az **Egyszerű felhasználónév** például megmutathatja az eszközön regisztrált e-mail-címet. Az eredmények frissítéséhez válassza az Oszlopok panelen az **Alkalmaz** lehetőséget.

#### <a name="device-details"></a>Eszközadatok

Az **eszköz részletei** diagramon válasszon ki egy adott eszközt, majd válassza az **eszköz megfelelősége**elemet:

![Egy adott eszköz, majd az Eszközmegfelelőség kiválasztása az alkalmazott megfelelőségi szabályzatok megtekintéséhez](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Az Intune az eszköz megfelelőségi szabályzatának beállításaival kapcsolatos további részleteket jeleníti meg. Az adott szabályzat kijelölésével megjelenik a szabályzat összes beállítása.

### <a name="devices-without-compliance"></a>Megfelelőség nélküli eszközök

A *megfelelőségi állapot* lapon, a házirend- *megfelelőségi* diagram mellett kiválaszthatja az **eszközök megfelelőségi szabályzat nélkül** lehetőséget, hogy megtekintse azokat az eszközöket, amelyek nem rendelkeznek hozzárendelt megfelelőségi házirendekkel:

![Megfelelőségi szabályzat nélküli eszközök megtekintése](./media/compliance-policy-monitor/devices-without-policies.png)

Amikor kijelöli a csempét, minden megfelelőségi szabályzat nélküli eszköz megjelenik. Látható az eszköz felhasználója, a szabályzat érvénybe léptetésének állapota és az eszköz típusa is.

#### <a name="what-you-need-to-know"></a>Amit még tudnia kell

- A **Hozzárendelt megfelelőségi szabályzat nélküli eszközök megjelölése mint...** biztonsági beállítás mellett fontos azonosítani a megfelelőségi szabályzat nélküli eszközöket. Ezt követően hozzájuk rendelhet legalább egy megfelelőségi szabályzatot.

  Ez a biztonsági beállítás az Intune portálon konfigurálható. Ahhoz, hogy az **eszközök** > **megfelelőségi szabályzatok** > a **megfelelőségi házirend beállításait**. A **Hozzárendelt megfelelőségi szabályzat nélküli eszközök megjelölése mint...** értékeként **Megfelelő** vagy **Nem megfelelő** állítható be.

  Minderről többet olvashat a [Biztonsági fejlesztések az Intune szolgáltatásban](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/) című cikkben.

- Az olyan felhasználók, akikhez bármilyen megfelelőségi szabályzat van rendelve, nem jelennek meg a jelentésben, tekintet nélkül az eszközplatformra. Így például ha Windows megfelelőségi szabályzat van egy androidos eszközzel rendelkező felhasználóhoz rendelve, akkor az eszköz nem jelenik meg a jelentésben. Az Intune azonban nem megfelelőként kezeli ezt az androidos eszközt. A problémák elkerülése érdekében ajánlott külön szabályzatot létrehozni minden eszközplatformhoz és azokat minden felhasználóra érvényesíteni.

### <a name="per-policy-device-compliance"></a>Szabályzatok szerinti eszközmegfelelőség

A szabályzat- **megfelelőségi** diagram megjeleníti a házirendeket, valamint azt, hogy hány eszköz megfelelő és nem megfelelő.

![A szabályzatok listája és az egyes szabályzatoknak megfelelő és nem megfelelő eszközök száma](./media/compliance-policy-monitor/idc-8.png)

### <a name="setting-compliance"></a>Beállítás-megfelelőség

A **megfelelőségi diagram beállítása** megjeleníti az összes megfelelőségi szabályzat beállításait, a szabályzatok által alkalmazott platformokat és a nem megfelelő eszközök számát.

![A különböző szabályzatok összes beállításának listája](./media/compliance-policy-monitor/idc-10.png)

## <a name="view-compliance-reports"></a>Megfelelőségi jelentések megtekintése

Amellett, hogy a diagramok a *megfelelőségi állapotot*használják, a **jelentések** > **eszköz megfelelősége**lehetőségre léphetnek.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza ki az **eszközök** > **figyelő**elemet, majd a **megfelelőség** alatt válassza ki a megtekinteni kívánt jelentést. Néhány elérhető megfelelőségi jelentés a következőkből áll:

   - Eszközmegfelelőség
   - Nem megfelelő eszközök
   - Megfelelőségi szabályzat nélküli eszközök
   - Beállítás-megfelelőség
   - Szabályzatmegfelelőség
   - Windows Health igazolási jelentés
   - Fenyegetésfigyelő ügynök állapota

További információ a jelentésekről: [Intune-jelentések](../fundamentals/reports.md)

## <a name="view-status-of-device-policies"></a>Eszközszabályzatok állapotának megtekintése

A szabályzatok különböző állapotait platformonként ellenőrizheti. Tegyük fel, hogy van egy macOS-es megfelelőségi szabályzata. Szeretné megtekinteni a szabályzat által érintett eszközöket, és megtudni, hogy vannak-e ütközések vagy hibák.

Ezt a funkciót tartalmazza az eszköz állapotjelentése:

1. Válassza az **eszközök** > **megfelelőségi szabályzatok** > **szabályzatok**lehetőséget. Megjelenik a szabályzatok listája, amely tartalmazza a platformot, hogy hozzá van-e rendelve a szabályzat, és további részleteket.
2. Válasszon ki egy szabályzatot > **Áttekintés**. Ebben a nézetben a szabályzat-hozzárendelés a következő állapotokat tartalmazza:

    - **Sikeres**: a házirend alkalmazása megtörtént
    - **Hiba**: a szabályzatot nem sikerült alkalmazni. Az üzenethez általában egy hibakód is tartozik, amely a hiba ismertetésére hivatkozik.
    - **Ütközés**: a rendszer két beállítást alkalmaz ugyanarra az eszközre, és az Intune nem tudja rendezni az ütközést. Rendszergazdai ellenőrzés szükséges.
    - **Függőben**: az eszköz még nem jelentkezett be az Intune-nal a szabályzat fogadására.
    - **Nem alkalmazható**: az eszköz nem tudja fogadni a szabályzatot. A szabályzat például egy, az iOS 11.1-re vonatkozó beállítást frissít, az eszköz azonban az iOS 10-et használja.

3. A szabályzatot használó eszközökön a részletek megtekintéséhez válassza ki a állapotok egyikét. Válassza például a **Sikeres** elemet. A következő ablakban megjelennek az eszköz adatai, például az eszköz neve és az üzembe helyezési állapot.

## <a name="how-intune-resolves-policy-conflicts"></a>Hogyan oldja fel az Intune az szabályzatütközéseket?

Szabályzatütközésről akkor beszélünk, hogy egy eszközre több Intune-szabályzat vonatkozik. Ha a szabályzatbeállítások közt átfedés van, az Intune a következő szabályok alkalmazásával oldja fel az ütközéseket:

- Ha az ütköző beállítások egy Intune konfigurációs szabályzatból és egy megfelelőségi szabályzatból kerülnek ki, akkor a megfelelőségi szabályzat beállításai érvényesülnek a konfigurációs szabályzatéival szemben. Ez még akkor is így van, ha a konfigurációs szabályzat beállításai biztonságosabbak.

- Ha több megfelelőségi szabályzatot telepített, akkor az Intune a legbiztonságosabbat alkalmazza ezek közül.

## <a name="next-steps"></a>További lépések

[Megfelelőségi szabályzatok áttekintése](device-compliance-get-started.md)
