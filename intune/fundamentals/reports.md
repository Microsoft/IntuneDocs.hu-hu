---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Az Intune adott típusú jelentéseket biztosít, amelyek konzisztens és kellő időben tárolt nézeteket tartalmaznak.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390934"
---
# <a name="intune-reports"></a>Intune-jelentések
Microsoft Intune a jelentések lehetővé teszik, hogy hatékonyabban és proaktívan figyelje a végpontok állapotát és tevékenységét a szervezeten belül, valamint más jelentéskészítési adatait is biztosítson az Intune-ban. Láthatja például, hogy az eszközök megfelelőségével, az eszköz állapotával és az eszközök trendjeivel kapcsolatos jelentések jelennek meg. Emellett létrehozhat egyéni jelentéseket is, amelyekkel pontosabban megszerezheti az adatokra vonatkozó adatgyűjtést. 

> [!NOTE]
> Az Intune jelentéskészítési módosításai fokozatosan, az új struktúra előkészítéséhez és az ahhoz való alkalmazkodáshoz szükséges idő alatt jelennek meg.

A jelentések típusai a következő fókusz területekre vannak rendezve:
- **Működés** – biztosítja az időben, a célcsoportokra koncentráló és a szükséges lépéseket. A rendszergazdák, a tárgyi szakértők és a helpdesk a leghasznosabb jelentéseket fogják találni.
- **Szervezeti** – átfogó áttekintést nyújt a teljes nézetről, például az eszközkezelés állapotáról. A kezelők és a rendszergazdák a leghasznosabb jelentéseket fogják találni.
- **Előzmények** – mintákat és trendeket biztosít egy adott időszakra vonatkozóan. A kezelők és a rendszergazdák a leghasznosabb jelentéseket fogják találni.
- **Specialist** – lehetővé teszi, hogy a nyers adatait használja saját egyéni jelentéseinek létrehozásához. Ezek a jelentések a rendszergazdák számára nyújtanak segítséget.

A jelentéskészítési keretrendszer egységes és átfogóbb jelentéskészítési élményt biztosít. Az elérhető jelentések a következő funkciókat biztosítják:
- **Keresés és rendezés** – megkeresheti és rendezheti az egyes oszlopokat, függetlenül attól, hogy mekkora az adatkészlet mérete.
- **Adatlapozás** – áttekintheti az adatait a lapozás, az oldal és a lap alapján, vagy egy adott oldalra ugrással.
- **Teljesítmény** – a nagyméretű bérlők által létrehozott jelentések gyorsan létrehozhatók és megtekinthetők.
- **Exportálás** – a nagyméretű bérlők által generált jelentéskészítési adatok gyors exportálása is végezhető.

### <a name="who-can-access-the-data"></a>Ki férhet hozzá az adatokhoz?

A következő engedélyekkel rendelkező felhasználók áttekinthetik a naplókat:

- Globális rendszergazda
- Intune-szolgáltatásadminisztrátor
- **Olvasási** engedélyekkel rendelkező Intune-szerepkörhöz rendelt rendszergazdák

## <a name="non-compliant-devices-report-operational"></a>Nem megfelelő eszközök jelentés (működési)
A nem megfelelő eszközök jelentést készítenek a felületek adatairól jellemzően az ügyfélszolgálat vagy a rendszergazdai szerepkörök használják a problémák azonosításához és a problémák megoldásához. Az ezekben a jelentésekben található adat időben, váratlan viselkedést hív meg, és működésének célja. A jelentés a munkaterhelés mellett érhető el, így a nem megfelelő eszközök nem érhetők el az aktív munkafolyamatokból való böngészés nélkül. Ez a jelentés szűrési, keresési, lapozási és rendezési képességeket biztosít. Azt is megteheti, hogy segít a hibakeresésben.

A nem **megfelelő eszközökről** szóló jelentést a következő lépésekkel tekintheti meg:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **eszköz megfelelősége** > nem **megfelelő eszközök**elemet.

    ![Nem megfelelő eszköz jelentés](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>Eszköz megfelelőségi jelentése (szervezeti)
Az eszközök megfelelőségi jelentéseinek célja, hogy széleskörűek legyenek a természetben, és az összesített mérőszámok azonosításához az adatoknak egy hagyományos jelentéskészítési nézetet biztosítanak. Ez a jelentés nagy adatkészletekkel való együttműködésre szolgál, hogy teljes eszköz megfelelőségi képet kapjon. Például az eszköz megfelelőségi jelentésében az eszközök megfelelőségi jelentése látható, hogy az eszközök minden megfelelőségi állapota szélesebb körű képet ad az adatkészletről, függetlenül attól, hogy mekkora az adatkészlet mérete. Ez a jelentés a rekordok teljes részletezését jeleníti meg az összesített metrikák kényelmes vizualizációja mellett. Ez a jelentés szűrők alkalmazásával és a jelentés létrehozása gomb kiválasztásával hozható létre. Ezzel frissíti az adatokat, hogy megjelenjenek a legújabb állapotok, amelyek segítségével megtekintheti az összesített adatokat alkotó egyes rekordokat. Az új keretrendszer jelentéseihez hasonlóan ezek a rekordok is rendezhetők és kereshetők, hogy a szükséges információkra koncentráljon. 

Az eszköz állapotának generált jelentéseinek megtekintéséhez kövesse az alábbi lépéseket:
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **jelentések** lehetőséget a jelentések összegzésének megtekintéséhez.
3. Válassza az **Eszközmegfelelőség** elemet.
4. Válassza ki a **megfelelőségi állapotot**, az **operációs rendszert**és a **tulajdonosi** szűrőket a jelentés pontosításához.
5. Kattintson a **jelentés előállítása** (vagy az **újbóli létrehozás**) elemre az aktuális adatlekérdezéshez.

    ![Eszköz megfelelőségi jelentése](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > Ez az **eszköz megfelelőségi** jelentés időbélyegzőt biztosít a jelentés legutóbbi generálásakor. 

Kapcsolódó információk: a [Microsoft DEFENDER ATP megfelelőségének kikényszerítés feltételes hozzáféréssel az Intune-ban](~/protect/advanced-threat-protection.md).

## <a name="reports-summary"></a>Jelentések összegzése 

Az eszköz megfelelőségi jelentése összegző jelentésként érhető el a **jelentések** munkafolyamatban. Az eszköz megfelelőségi jelentésének megtekintéséhez kövesse az alábbi lépéseket:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **jelentések** lehetőséget a jelentések összegzésének megtekintéséhez.

    ![Az Intune-jelentések összegzése](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>Eszköz megfelelőségi trend jelentés (korábbi)
A rendszergazdák és az építészek az eszköz megfelelőségi trendjeit gyakrabban használják az eszközök megfelelőségének hosszú távú trendjeinek azonosítására. Az összesített adat egy adott időszakon belül jelenik meg, és hasznos lehet a jövőbeli befektetési döntések meghozatalához, a folyamat fejlesztéséhez, illetve a nyomozás bármilyen rendellenességhez való megadásához. A szűrők is alkalmazhatók az adott trendek megjelenítéséhez. A jelentés által megadott adatok a bérlő aktuális állapotának (közel valós idejű) pillanatképét jelentik. 

Az eszközök megfelelőségi trendjeire vonatkozó megfelelőségi jelentés egy adott időszakban az eszköz megfelelőségi állapotának alakulását mutatja be. Azonosíthatja a megfelelőségi csúcsok helyét, és ennek megfelelően összpontosíthatja az időt és a fáradságot.

A **trendek** jelentés a következő lépésekkel tekinthető meg:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **jelentések** > **trendek** lehetőséget, hogy megtekintse az eszköz megfelelőségét egy 60 napos trenden.

    ![Intune trend-jelentés](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Azure Monitor integrációs jelentések (specialista)
Testre szabhatja saját jelentéseit, hogy megkapják a kívánt adatkéréseket. A jelentésekben szereplő adatai a [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) [log Analytics](reports.md#log-analytics) és [Azure monitor munkafüzetek](reports.md#workbooks)használatával is elérhetők. Ezekkel a megoldásokkal egyéni lekérdezéseket hozhat létre, riasztásokat állíthat be, és irányítópultokat készíthet az eszköz megfelelőségi adatainak a kívánt módon történő megjelenítéséhez. Emellett megtarthatja a tevékenység naplóit az Azure Storage-fiókjában, integrálhatja azokat a jelentésekkel a [biztonsági információk és az események kezelése (SIEM) eszközeivel](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration), és korrelálhatja a jelentéseket az Azure ad-tevékenységek naplóival. A Azure Monitor munkafüzetek az egyéni jelentéskészítési igényekhez tartozó irányítópultok importálásán felül is használhatók.

> [!NOTE]
> Az összetett jelentéskészítési funkciókhoz Azure-előfizetés szükséges.

Egy példaként szolgáló speciális jelentés a platform beléptetési corelate egy egyéni jelentésben. Ezt követően ez az egyéni jelentés egy meglévő irányítópulton jelenhet meg a Azure Active Directory-portálon.

Az alábbi lépések végrehajtásával hozhat létre és tekinthet meg egyéni jelentéseket:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **jelentések** > **diagnosztikai beállítások** Hozzáadás [diagnosztikai beállítás](reports.md#diagnostic-settings)lehetőséget.

    ![Az Intune-jelentések összegzése](./media/intune-reports/intune-reports-04.png)

3. A **diagnosztikai beállítások** ablaktábla megjelenítéséhez kattintson a **diagnosztikai beállítás hozzáadása** elemre. 
4. Adja meg a diagnosztikai beállítások **nevét** . 
5. Válassza ki a **küldés log Analytics** és a **DeviceComplianceOrg** beállításait.

    ![Az Intune-jelentések összegzése](./media/intune-reports/intune-reports-04a.png)

6. Kattintson a **Mentés**gombra.
7. Ezután a **log Analytics** elemre kattintva hozzon létre és futtasson új napló-lekérdezést [log Analytics](reports.md#log-analytics)használatával.

   ![Log Analytics – napló lekérdezése](./media/intune-reports/intune-reports-05.png)

8. Válassza a **munkafüzetek** lehetőséget, hogy [Azure monitor munkafüzetek](reports.md#workbooks)használatával hozzon létre vagy nyisson meg egy interaktív jelentést.

   ![Munkafüzetek – interaktív jelentések](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>Diagnosztikai beállítások
Minden Azure-erőforráshoz saját diagnosztikai beállítások szükségesek. A diagnosztikai beállítás határozza meg az erőforrás következő értékét:

- A beállításban meghatározott célhelyekre továbbított naplók és metrikai adatok kategóriái. A rendelkezésre álló kategóriák a különböző erőforrástípusok esetében eltérőek lesznek.
- Egy vagy több célhely a naplók elküldéséhez. Az aktuális célhelyek közé tartozik Log Analytics munkaterület, Event Hubs és az Azure Storage.
- Adatmegőrzési szabályzat az Azure Storage-ban tárolt adatokhoz.

Egyetlen diagnosztikai beállítás is meghatározhatja az egyes célok egyikét. Ha szeretne adatokat küldeni egy adott célhelyhez (például két különböző Log Analytics-munkaterületre), akkor hozzon létre több beállítást. Minden erőforrás legfeljebb 5 diagnosztikai beállítással rendelkezhet.

További információ a diagnosztikai beállításokról: [diagnosztikai beállítás létrehozása a platform-naplók és-metrikák gyűjtéséhez az Azure-ban](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings).

### <a name="log-analytics"></a>Log Analytics
A Log Analytics a Azure Portal elsődleges eszköze a naplók írásához és a lekérdezések eredményeinek interaktív elemzéséhez. Akkor is, ha a naplózási lekérdezést Azure Monitorban máshol használják, általában a Log Analytics használatával fogja írni és tesztelni a lekérdezést. További információ a Log Analytics használatáról és a naplók létrehozásáról: [Azure monitor-lekérdezések áttekintése](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview). 

### <a name="workbooks"></a>Munkafüzetek
A munkafüzetek szöveg-, elemzési és Azure-metrikákat és-paramétereket egyesítenek gazdag interaktív jelentésekben. A munkafüzetek szerkeszthető más csapattagok számára, akik ugyanahhoz az Azure-erőforrásokhoz férnek hozzá. További információ a munkafüzetekről: [Azure monitor munkafüzetek](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks). Emellett a munkafüzet-sablonokkal is dolgozhat és járulhat hozzá. További információ: [Azure monitor munkafüzet-sablonok](https://go.microsoft.com/fwlink/?linkid=867045).

## <a name="next-steps"></a>További lépések

További információ az alábbi technológiákról:
- [Blog – Microsoft Intune jelentési keretrendszer](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [Mi az a Log Analytics?](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [Lekérdezések naplózása](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Ismerkedés a Log Analyticsával Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Munkafüzetek Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [Biztonsági információk és rendezvényszervezés (SIEM) eszközei](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
