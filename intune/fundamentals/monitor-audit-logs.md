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
ms.openlocfilehash: b4be1755a07e6ec304edb7bceba8041d5b58263e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509999"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Naplók használata a Microsoft Intune eseményeinek nyomon követéséhez és figyeléséhez

A naplók a Microsoft Intune változását eredményező tevékenységek rekordját tartalmazzák. Létrehozás, frissítés (Szerkesztés), törlés, hozzárendelés és távoli műveletek minden olyan naplózási esemény létrehozása, amelyet a rendszergazdák a legtöbb Intune-beli számítási feladathoz megtekinthetnek. Alapértelmezés szerint a naplózás minden ügyfél esetében engedélyezve van. Nem lehet letiltani.

> [!NOTE]
> A naplózási események a december 2017-es kiadásban kezdték meg a felvételt. Az előző események nem érhetők el.

## <a name="who-can-access-the-data"></a>Ki férhet hozzá az adatokhoz?

A következő engedélyekkel rendelkező felhasználók tekinthetik meg az auditnaplókat:

- Globális rendszergazda
- Intune-szolgáltatásadminisztrátor
- **Naplózási adatok** - **Olvasási** engedéllyel rendelkező, Intune-szerepkörhöz hozzárendelt rendszergazdák

## <a name="audit-logs-for-intune-workloads"></a>Intune-beli számítási feladatok auditnaplói

A naplókat a figyelés csoportban tekintheti meg az egyes Intune-munkaterhelésekhez:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza ki a munkaterhelést, amelyben át szeretné tekinteni a naplókat. Válassza például az **eszközök**lehetőséget.
3. A **figyelés**területen válassza a **naplók**lehetőséget.

## <a name="route-logs-to-azure-monitor"></a>Naplók átirányítása a Azure Monitorba

A naplók és az operatív naplók is átirányíthatók Azure Monitorba. A **naplók**területen válassza az **adatbeállítások exportálása**lehetőséget:

![A naplófájlok exportálása az Azure monitorba az adatbeállítások exportálása az Intune-ban lehetőség kiválasztásával](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

További információ erről a szolgáltatásról: [naplófájlok küldése a tárolóba, az Event hubokba vagy a log analyticsbe](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Naplózási események áttekintése

![Válassza ki a naplók az Intune-ban lehetőséget, hogy megjelenjenek a műveletek és dátumok, amikor események történtek](./media/monitor-audit-logs/monitor-audit-logs.png "Naplók")

Az auditnaplók alapértelmezett listanézete a következő elemeket jeleníti meg:

- Az előfordulás dátuma és időpontja
- Kezdeményező (szereplő)
- Alkalmazás neve
- Tevékenység
- Cél(ok)
- Category
- Állapot

Ha részletesebb információkat szeretne látni egy eseményről, válasszon egy elemet a listában:

![Konkrétabb információk az Intune-beli naplókról](./media/monitor-audit-logs/monitor-audit-log-detail.png "Napló részletei")

> [!NOTE]
> A **kezdeményező (Actor)** információt tartalmaz arról, hogy ki futtatta a feladatot, és hol futott. Ha például az Intune-ban futtatja a tevékenységet a Azure Portalban, az **alkalmazás** mindig listázza **Microsoft Intune portál bővítményt** , és az **alkalmazás-azonosító** mindig ugyanazt a GUID-t használja.
> 
> A **cél (ok)** szakasz több célt és a módosított tulajdonságokat sorolja fel.  

## <a name="filter-audit-events"></a>A naplózási események áttekintése

Minden számítási feladathoz tartozik egy menüpont, mely előzetesen szűri az adott panelhez társított naplózási események kategóriáját. Egy különálló szűrési lehetőséggel válthat más kategóriákra, illetve az adott kategóriába tartozó eseményműveletek adataira. Az egyszerű felhasználónév alapján kereshet, például a műveletet végrehajtó felhasználó. A dátumtartomány-szűrők 24 órás, 7 napos és 30 napos beállítás használatát teszik lehetővé. Alapértelmezés szerint az utolsó 30 nap a naplózási események láthatók.

## <a name="use-graph-api-to-retrieve-audit-events"></a>A naplózott események beolvasása a Graph API-val

A Graph API-val való használatáról további részleteket a [listázásával listázása](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)című témakörben talál.

## <a name="next-steps"></a>További lépések

[Naplózási adatküldés a Storage, az Event hubok vagy a log Analytics](review-logs-using-azure-monitor.md)szolgáltatásba.

[Tekintse át az ügyfélalkalmazás-védelmi naplókat](../apps/app-protection-policy-settings-log.md).
