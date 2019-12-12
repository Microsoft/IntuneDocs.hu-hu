---
title: Változások és események naplózása a Microsoft Intuneban – Azure | Microsoft Docs
description: Útmutató a Microsoft Intune-tevékenységeket rögzítő auditnaplók áttekintéséhez.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991989"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Naplók használata a Microsoft Intune eseményeinek nyomon követéséhez és figyeléséhez

A naplók a Microsoft Intune változását eredményező tevékenységek rekordját tartalmazzák. Létrehozás, frissítés (Szerkesztés), törlés, hozzárendelés és távoli műveletek minden olyan naplózási esemény létrehozása, amelyet a rendszergazdák a legtöbb Intune-beli számítási feladathoz megtekinthetnek. Alapértelmezés szerint a naplózás minden ügyfél esetében engedélyezve van. A folyamat nem tiltható le.

> [!NOTE]
> A naplózási események a december 2017-es kiadásban kezdték meg a felvételt. Az előző események nem érhetők el.

## <a name="who-can-access-the-data"></a>Ki férhet hozzá az adatokhoz?

A következő engedélyekkel rendelkező felhasználók tekinthetik meg az auditnaplókat:

- Globális rendszergazda
- Intune-szolgáltatásadminisztrátor
- **Naplózási adatok** - **Olvasási** engedéllyel rendelkező, Intune-szerepkörhöz hozzárendelt rendszergazdák

## <a name="audit-logs-for-intune-workloads"></a>Intune-beli számítási feladatok auditnaplói

A naplókat a figyelés csoportban tekintheti meg az egyes Intune-munkaterhelésekhez:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza a **bérlői felügyelet** > a **naplók**lehetőséget.
3. Az eredmények szűréséhez válassza a **szűrés** lehetőséget, és pontosítsa az eredményeket a következő beállítások használatával.
    - **Kategória**: **megfelelőség**, **eszköz**és **szerepkör**.
    - **Tevékenység**: az itt felsorolt beállításokat a **Kategória**mezőben kiválasztott lehetőség korlátozza.
    - **Dátumtartomány**: az előző hónap, hét vagy nap naplóinak kiválasztására van lehetőség.
4. Válassza az **Alkalmaz** lehetőséget.
4. Válasszon ki egy elemet a listában a tevékenység részleteinek megtekintéséhez.

## <a name="route-logs-to-azure-monitor"></a>Naplók átirányítása a Azure Monitorba

A naplók és az operatív naplók is átirányíthatók Azure Monitorba. A **naplók**területen válassza az **adatbeállítások exportálása**lehetőséget:

![A naplófájlok exportálása az Azure monitorba az adatbeállítások exportálása az Intune-ban lehetőség kiválasztásával](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> További információ erről a szolgáltatásról és az előfeltételek használatáról: [naplózási adatok küldése a Storage-ba, az Event hubokba vagy a log analyticsbe](review-logs-using-azure-monitor.md).

> [!NOTE]
> A **kezdeményező (Actor)** információt tartalmaz arról, hogy ki futtatta a feladatot, és hol futott. Ha például az Intune-ban futtatja a tevékenységet a Azure Portalban, az **alkalmazás** mindig listázza **Microsoft Intune portál bővítményt** , és az **alkalmazás-azonosító** mindig ugyanazt a GUID-t használja.
>
> A **cél (ok)** szakasz több célt és a módosított tulajdonságokat sorolja fel.  

## <a name="use-graph-api-to-retrieve-audit-events"></a>A naplózott események beolvasása a Graph API-val

A Graph API-val való használatáról további részleteket a [listázásával listázása](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)című témakörben talál.

## <a name="next-steps"></a>További lépések

[Naplózási adatküldés a Storage, az Event hubok vagy a log Analytics](review-logs-using-azure-monitor.md)szolgáltatásba.

[Tekintse át az ügyfélalkalmazás-védelmi naplókat](../apps/app-protection-policy-settings-log.md).
