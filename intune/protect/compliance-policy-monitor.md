---
title: Eszközmegfelelőségi szabályzatok figyelése az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az eszközmegfelelőségi irányítópulttal figyelheti az eszközmegfelelőségeket, jelentéseket tekinthet meg, valamint megtekintheti a szabályzatonkénti és beállításonkénti eszközmegfelelőségeket.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 1/14/2019
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
ms.openlocfilehash: 844e93f3a063ae43342d2967cbd544f3ec425c21
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410160"
---
# <a name="monitor-intune-device-compliance-policies"></a>Intune-eszközmegfelelőségi szabályzatok figyelése

A megfelelőségi jelentések segítenek az eszközmegfelelőség áttekintésében, és a megfelelőséggel kapcsolatos problémák elhárításában a vállalatánál. Ezeknek a jelentéseknek a használatával a következőkről tekinthet meg információkat:

- Az eszközök összesített megfelelőségi állapota
- Az egyes beállítások megfelelőségi állapota
- Az egyes szabályzatok megfelelőségi állapota
- Egy eszköz részletes vizsgálatával megtekintheti az arra vonatkozó beállításokat és szabályzatokat

## <a name="open-the-compliance-dashboard"></a>A megfelelőségi irányítópult megnyitása

Nyissa meg az **Intune Eszközmegfelelőségi irányítópultját**:

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Válassza az **Eszközmegfelelőség** > **Áttekintés** elemet. Megnyílik az **Eszközmegfelelőségi irányítópult**.

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

### <a name="device-compliance-status"></a>Device compliance status

The **Device compliance status** chart shows the compliance states for all Intune enrolled devices. Az eszközmegfelelőségi állapot adatait két külön adatbázis tárolja: az Intune és az Azure Active Directory.

> [!IMPORTANT]
> Intune follows the device check-in schedule for all compliance evaluations on the device. [Learn more about the device check-in schedule](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

A különböző eszközmegfelelőségi szabályzatállapotok leírása:

- **Megfelelő**: az eszköz megfelel egy vagy több eszközmegfelelőségi szabályzat beállításainak.

- **Türelmi időszak**: Az eszközre egy vagy több eszközmegfelelőségi szabályzat lett beállítva. A felhasználó azonban még nem alkalmazta a szabályzatokat. Ez azt jelenti, hogy az eszköz nem megfelelő, de a rendszergazda által meghatározott türelmi időszakban van.

  - További információ a [nem megfelelő eszközökre alkalmazható műveletekről](actions-for-noncompliance.md).

- **Nem értékelt**: Az újonnan regisztrált eszközök kiinduló állapota. Other possible reasons for this state include:

  - Devices that aren't assigned a compliance policy and don't have a trigger to check for compliance
  - Devices that haven't checked in since the compliance policy was last updated
  - Devices not associated to a specific user, such as:
    - iOS devices purchased through Apple's Device Enrollment Program (DEP) that don't have user affinity
    - Android kiosk or Android Enterprise dedicated devices
  - Devices enrolled with a device enrollment manager (DEM) account

- **Nem megfelelő**: Az eszköz nem felel meg egy vagy több eszközmegfelelőségi szabályzat beállításainak. Lehetséges, hogy a felhasználó nem a szabályzatoknak megfelelően járt el.

- **Az eszköz nincs szinkronizálva:** az eszköz nem jelentette az eszközmegfelelőségi szabályzat állapotát az alábbi okok miatt:

  - **Ismeretlen**: az eszköz offline állapotban van, vagy valamilyen más okból nem sikerült kapcsolatba lépnie az Intune-nal vagy az Azure AD-vel.

  - **Hiba**: az eszköznek nem sikerült kapcsolatba lépnie az Intune-nal vagy az Azure AD-vel, és üzenetben megkapta a hiba okát.

> [!IMPORTANT]
> A jelentésben a **Megfelelő** gyűjtőben szerepelnek azok az eszközök, amelyek regisztrálva vannak az Intune-ban, de nem vonatkozik rájuk eszközmegfelelőségi szabályzat.

#### <a name="drill-down-for-more-details"></a>További részletezés

Válasszon egy állapotot az **Eszközmegfelelőségi állapot** diagramon. Válassza például a **Nem megfelelő** állapotot:

![A nem megfelelő állapot kiválasztása](./media/compliance-policy-monitor/select-not-compliant-status.png)

That action opens the **Device compliance** window, and displays devices in a **Device status** chart. The chart shows you more details on the devices in that state, including operating system platform, last check-in date, and more. 

![Irányítópult képe az adott állapotú eszközöz további részleteivel](./media/compliance-policy-monitor/drill-down-details.png)

Ha egy adott felhasználó tulajdonában lévő összes eszközt látni szeretné, a felhasználó e-mail-címének begépelésével szűrni tudja a diagramot tartalmazó jelentést.

#### <a name="filter-and-columns"></a>Szűrő és oszlopok

![A diagramon ábrázolt eredmények módosítása a Szűrő és az Oszlopok lehetőség választásával](./media/compliance-policy-monitor/filter-columns.png)

When you select the **Filter** button, the filter fly-out opens with more options, including the **Compliance** state, **Jailbroken** devices, and more. Az eredmények frissítéséhez válassza a Szűrő panelen az **Alkalmaz** lehetőséget.

A diagram-kimenet oszlopainak hozzáadásához és eltávolításához válassza az **Oszlopok** lehetőséget. Az **Egyszerű felhasználónév** például megmutathatja az eszközön regisztrált e-mail-címet. Az eredmények frissítéséhez válassza az Oszlopok panelen az **Alkalmaz** lehetőséget.

#### <a name="device-details"></a>Eszközadatok

In the **Device details** chart, select a specific device, and then select **Device compliance**:

![Egy adott eszköz, majd az Eszközmegfelelőség kiválasztása az alkalmazott megfelelőségi szabályzatok megtekintéséhez](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Intune displays more details on the device compliance policy settings applied on that device. Az adott szabályzat kijelölésével megjelenik a szabályzat összes beállítása.

### <a name="devices-without-compliance"></a>Devices without compliance

On the *Compliance status* page, next to the *Policy compliance* chart, you can select the **Devices without compliance policy** tile to view information about devices that don't have any compliance policies assigned:

![Megfelelőségi szabályzat nélküli eszközök megtekintése](./media/compliance-policy-monitor/devices-without-policies.png)

Amikor kijelöli a csempét, minden megfelelőségi szabályzat nélküli eszköz megjelenik. Látható az eszköz felhasználója, a szabályzat érvénybe léptetésének állapota és az eszköz típusa is.

#### <a name="what-you-need-to-know"></a>Amit még tudnia kell

- A **Hozzárendelt megfelelőségi szabályzat nélküli eszközök megjelölése mint...** biztonsági beállítás mellett fontos azonosítani a megfelelőségi szabályzat nélküli eszközöket. Ezt követően hozzájuk rendelhet legalább egy megfelelőségi szabályzatot.

  Ez a biztonsági beállítás az Intune portálon konfigurálható. To to **Devices** > **Compliance policies** > **Compliance policy settings**. A **Hozzárendelt megfelelőségi szabályzat nélküli eszközök megjelölése mint...** értékeként **Megfelelő** vagy **Nem megfelelő** állítható be. 

  Minderről többet olvashat a [Biztonsági fejlesztések az Intune szolgáltatásban](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/) című cikkben.

- Az olyan felhasználók, akikhez bármilyen megfelelőségi szabályzat van rendelve, nem jelennek meg a jelentésben, tekintet nélkül az eszközplatformra. Így például ha Windows megfelelőségi szabályzat van egy androidos eszközzel rendelkező felhasználóhoz rendelve, akkor az eszköz nem jelenik meg a jelentésben. Az Intune azonban nem megfelelőként kezeli ezt az androidos eszközt. A problémák elkerülése érdekében ajánlott külön szabályzatot létrehozni minden eszközplatformhoz és azokat minden felhasználóra érvényesíteni.

### <a name="per-policy-device-compliance"></a>Szabályzatok szerinti eszközmegfelelőség

The **Policy compliance** chart shows you the policies, and how many devices are compliant and noncompliant. 

![A szabályzatok listája és az egyes szabályzatoknak megfelelő és nem megfelelő eszközök száma](./media/compliance-policy-monitor/idc-8.png)

### <a name="setting-compliance"></a>Beállítás-megfelelőség

The **Setting compliance** chart shows you all device compliance policy settings from all compliance policies, the platforms the policy settings are applied, and the number of noncompliant devices.

![A különböző szabályzatok összes beállításának listája](./media/compliance-policy-monitor/idc-10.png)

> [!NOTE]
> A policy can be assigned to a device, and a user on that same device. In some scenarios, a device may sync before the user signs in, such as when the device reboots. Compliance may evaluate this user, and show the device as non compliant. This behavior may also show the System Account as a non-compliant user.
>
> This is a known issue with multi-user Windows 10 devices. Any changes or updates on this behavior are announced in [in development](../fundamentals/in-development.md) and/or [what's new](../fundamentals/whats-new.md).

## <a name="view-compliance-reports"></a>View compliance reports

In addition to using the charts on *Compliance status*, you can view compliance reports from the *Monitor* page of the Admin Center.

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Monitor**, and then from below **Compliance** select the report you want to view. Some of the available compliance reports include:

   - Eszközmegfelelőség
   - Noncompliant devices
   - Megfelelőségi szabályzat nélküli eszközök
   - Beállítás-megfelelőség
   - Policy compliance
   - Windows health attestation report
   - Fenyegetésfigyelő ügynök állapota

For more information about reports, see [Intune reports](../fundamentals/reports.md)

## <a name="view-status-of-device-policies"></a>Eszközszabályzatok állapotának megtekintése

A szabályzatok különböző állapotait platformonként ellenőrizheti. Tegyük fel, hogy van egy macOS-es megfelelőségi szabályzata. Szeretné megtekinteni a szabályzat által érintett eszközöket, és megtudni, hogy vannak-e ütközések vagy hibák.

Ezt a funkciót tartalmazza az eszköz állapotjelentése:

1. Select **Devices** > **Compliance policies** > **Policies**. Megjelenik a szabályzatok listája, amely tartalmazza a platformot, hogy hozzá van-e rendelve a szabályzat, és további részleteket.
2. Válasszon ki egy szabályzatot > **Áttekintés**. Ebben a nézetben a szabályzat-hozzárendelés a következő állapotokat tartalmazza:

    - **Succeeded**: Policy is applied
    - **Error**: The policy failed to apply. Az üzenethez általában egy hibakód is tartozik, amely a hiba ismertetésére hivatkozik. 
    - **Conflict**: Two settings are applied to the same device, and Intune can't sort out the conflict. Rendszergazdai ellenőrzés szükséges.
    - **Pending**: The device hasn’t checked in with Intune to receive the policy yet. 
    - **Not applicable**: The device can't receive the policy. A szabályzat például egy, az iOS 11.1-re vonatkozó beállítást frissít, az eszköz azonban az iOS 10-et használja. 

3. A szabályzatot használó eszközökön a részletek megtekintéséhez válassza ki a állapotok egyikét. Válassza például a **Sikeres** elemet. A következő ablakban megjelennek az eszköz adatai, például az eszköz neve és az üzembe helyezési állapot.

## <a name="how-intune-resolves-policy-conflicts"></a>Hogyan oldja fel az Intune az szabályzatütközéseket?
Szabályzatütközésről akkor beszélünk, hogy egy eszközre több Intune-szabályzat vonatkozik. Ha a szabályzatbeállítások közt átfedés van, az Intune a következő szabályok alkalmazásával oldja fel az ütközéseket:

- Ha az ütköző beállítások egy Intune konfigurációs szabályzatból és egy megfelelőségi szabályzatból kerülnek ki, akkor a megfelelőségi szabályzat beállításai érvényesülnek a konfigurációs szabályzatéival szemben. Ez még akkor is így van, ha a konfigurációs szabályzat beállításai biztonságosabbak.

- Ha több megfelelőségi szabályzatot telepített, akkor az Intune a legbiztonságosabbat alkalmazza ezek közül.
