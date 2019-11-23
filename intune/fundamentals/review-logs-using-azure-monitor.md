---
title: Naplók átirányítása Azure Monitor Microsoft Intune-Azure használatával | Microsoft Docs
description: A diagnosztikai beállításokkal naplókat és műveleti naplókat küldhet Microsoft Intune Azure Storage-fiókba, Event hubokba vagy log analyticsbe. Válassza ki, hogy mennyi ideig szeretné megőrizni az adatmennyiséget, és megtekintheti a különböző méretű bérlők becsült költségeit.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 95191d64-9895-4f2e-8c5b-f0e85be086d8
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66acf4d8b88097c3262f44493ab72b3900781eed
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504961"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Naplózási adatküldés a Storage, az Event hubok vagy a log Analytics számára az Intune-ban (előzetes verzió)

A Microsoft Intune tartalmaz olyan beépített naplókat, amelyek a környezettel kapcsolatos információkat biztosítanak:

- A **naplók** az Intune-ban megjelenő különböző eseményekre vagy feladatokra vonatkozó adatokat jelenítik meg.
- Az **operatív naplók (előzetes verzió)** részletesen ismertetik a regisztrálni kívánt felhasználók és eszközök részleteit, valamint a nem megfelelő eszközök részleteit.
- Az **eszköz megfelelőségi szervezeti naplói (előzetes verzió)** az eszköz megfelelőségének szervezeti jelentését mutatják be az Intune-ban, valamint a nem megfelelő eszközök részleteit.

Ezeket a naplókat Azure Monitor szolgáltatásokhoz is el lehet juttatni, beleértve a Storage-fiókokat, az Event hubokat és a log Analytics szolgáltatást. Pontosabban a következőket teheti:

* Archiválja az Intune-naplókat egy Azure Storage-fiókba, hogy az adatok megmaradjanak vagy archiválásra legyenek beállítva.
* A stream Intune egy Azure Event hub-ba kerül az elemzéshez népszerű biztonsági információk és eseménykezelő (SIEM) eszközök, például a splunk és a QRadar használatával.
* Az Intune-naplókat saját egyéni bejelentkezési megoldásaival integrálhatja az Event hub-ba.
* Az Intune-naplók küldésével Log Analytics, hogy lehetővé tegye a kapcsolódó adatmegjelenítést, monitorozást és riasztást.

Ezek a funkciók az Intune **diagnosztikai beállításainak** részét képezik.

Ez a cikk bemutatja, hogyan lehet **diagnosztikai beállításokkal** elküldeni a naplózási adatait különböző szolgáltatásokra, példákat és becsléseket adni, és választ kaphat a gyakori kérdésekre. Ha engedélyezi ezt a funkciót, a rendszer átirányítja a naplókat a kiválasztott Azure Monitor szolgáltatáshoz.

## <a name="prerequisites"></a>Előfeltételek

A funkció használatához a következőkre lesz szüksége:

* Azure-előfizetés: Ha nem rendelkezik Azure-előfizetéssel, [regisztrálhat egy ingyenes próbaverzióra](https://azure.microsoft.com/free/).
* Microsoft Intune-környezet (bérlő) az Azure-ban
* Olyan felhasználó, aki **globális rendszergazda** vagy **Intune-szolgáltatás rendszergazdája** az Intune-bérlőhöz.

Attól függően, hogy hová szeretné átirányítani a naplózási naplót, a következő szolgáltatások egyikére lesz szüksége:

* Egy [Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-account-overview) -fiók *listkeys műveletének beolvasása* -engedélyekkel. Javasoljuk, hogy használjon általános Storage-fiókot, és ne blob Storage-fiókot. A tárolási díjszabással kapcsolatos információkért tekintse meg az [Azure Storage díjszabási számológépét](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* Egy [Azure Event hub-névtér](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) , amely integrálható a harmadik féltől származó megoldásokkal.
* Egy [Azure log Analytics-munkaterületet](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) , amely naplókat küld log Analyticsba.

## <a name="send-logs-to-azure-monitor"></a>Naplók küldése az Azure monitornak

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. A **figyelés**területen válassza a **diagnosztikai beállítások**elemet. Amikor először nyitja meg, kapcsolja be. Ellenkező esetben adjon hozzá egy beállítást.

    ![A diagnosztikai beállítások bekapcsolása az Intune-ban a naplók Azure Monitorba való küldéséhez](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. Adja meg a következő tulajdonságokat:

    - **Név**: adja meg a diagnosztikai beállítások nevét. Ez a beállítás tartalmazza a beírt összes tulajdonságot. Például írja be a következőt: `Route audit logs to storage account`.
    - **Archiválás a Storage-fiókba**: a naplóba mentett adatok mentése egy Azure Storage-fiókba. Akkor használja ezt a lehetőséget, ha menteni vagy archiválni szeretné az adatfájlokat.

        1. Válassza ezt a beállítást > a **configure (Konfigurálás**) lehetőséget. 
        2. Válasszon egy meglévő Storage-fiókot a listából > **OK gombra**.

    - **Stream az Event hub**-ba: a naplókat egy Azure Event hub-ba továbbítja. Ha azt szeretné, hogy a naplózási adatait SIEM-eszközök, például a splunk és a QRadar használja, válassza ezt a lehetőséget.

        1. Válassza ezt a beállítást > a **configure (Konfigurálás**) lehetőséget. 
        2. Válasszon ki egy meglévő Event hub-névteret és-szabályzatot a listáról > **OK gombra**.

    - **Küldés log Analyticsba**: az adatokat az Azure log Analytics szolgáltatásba küldi. Ha vizualizációkat, figyelést és riasztásokat szeretne használni a naplókhoz, válassza ezt a lehetőséget.

        1. Válassza ezt a beállítást > a **configure (Konfigurálás**) lehetőséget. 
        2. Hozzon létre egy új munkaterületet, és adja meg a munkaterület részleteit. Vagy válasszon ki egy meglévő munkaterületet a listáról > **OK gombra**.

            Az [Azure log Analytics-munkaterület](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) további részleteket tartalmaz ezekről a beállításokról.

    - **LOG** > **AuditLogs**: válassza ezt a lehetőséget, ha el szeretné küldeni az [Intune-naplókat](../monitor-audit-logs.md) a Storage-fiókba, az Event hub-ba vagy a log analyticsbe. A naplók az Intune-ban változást okozó feladatok előzményeit jelenítik meg, beleértve azt is, hogy ki és mikor.

      Ha a Storage-fiók használata mellett dönt, adja meg, hogy hány napig szeretné megőrizni az adatok megőrzésének idejét. Az adatok örökre megtartásához állítsa a **megőrzés (nap)** értéket `0` (nulla) értékre.

    - **LOG** > **OperationalLogs**: a működési naplók (előzetes verzió) az Intune-ban regisztrált felhasználók és eszközök sikerességét vagy hibáit, valamint a nem megfelelő eszközök részleteit mutatják be. Válassza ezt a lehetőséget, ha a beléptetési naplókat el szeretné küldeni a Storage-fiókba, az Event Hubbe vagy a log analyticsbe.

      Ha a Storage-fiók használata mellett dönt, adja meg, hogy hány napig szeretné megőrizni az adatok megőrzésének idejét. Az adatok örökre megtartásához állítsa a **megőrzés (nap)** értéket `0` (nulla) értékre.

      > [!NOTE]
      > Az operatív naplók előzetes verzióban érhetők el. A visszajelzések megadásához, beleértve az operatív naplókban található információkat is, ugorjon a [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    - **LOG** > **DeviceComplianceOrg**: az eszköz megfelelőségi szervezeti naplói (előzetes verzió) az eszköz megfelelőségének szervezeti jelentését mutatják be az Intune-ban, valamint a nem megfelelő eszközök részleteit. Válassza ezt a lehetőséget, ha el szeretné küldeni a megfelelőségi naplókat a Storage-fiókba, az Event hub-ba vagy a log analyticsbe.

      Ha a Storage-fiók használata mellett dönt, adja meg, hogy hány napig szeretné megőrizni az adatok megőrzésének idejét. Az adatok örökre megtartásához állítsa a **megőrzés (nap)** értéket `0` (nulla) értékre.
 
      > [!NOTE]
      > Az eszközök megfelelőségi szervezeti naplói előzetes verzióban érhetők el. Ha visszajelzést szeretne küldeni, beleértve a jelentésben szereplő információkat is, ugorjon a [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    Ha elkészült, a beállítások a következő beállításokhoz hasonlóan néznek ki: 

    ![Az Intune-naplókat egy Azure Storage-fiókba küldő minta képe](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. **Mentse** a változtatásokat. A beállítás megjelenik a listában. A létrehozást követően módosíthatja a beállításokat, ha a beállítások **szerkesztése** > **Mentés**lehetőségre kattint.

## <a name="use-audit-logs-throughout-intune"></a>Naplófájlok használata az Intune-ban

A naplókat az Intune más részeiben is exportálhatja, beleértve a regisztrációt, a megfelelőséget, a konfigurációt, az eszközöket, az ügyfélalkalmazások és egyebeket.

Például a naplók exportálásához az eszköz megfelelőségének használatakor:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **eszköz megfelelősége** > **figyelő** > **naplózási naplók**elemet:

    ![Naplók kiválasztása az Intune-beli adatAzure Monitor Storage, Events hubok vagy Analytics szolgáltatásba való átirányításához](./media/review-logs-using-azure-monitor/audit-logs-under-monitor-in-compliance.png)

3. Válassza **az adatbeállítások exportálása**lehetőséget. Ha nincs engedélyezve, bekapcsolhatja a **diagnosztikai beállításokat**. Azt is megadhatja, hogy hová szeretné elküldeni a naplókat a [naplók küldése az Azure monitorba](#send-logs-to-azure-monitor) című cikkben leírtak szerint (ez a cikk).

## <a name="cost-considerations"></a>Költségekkel kapcsolatos szempontok

Ha már rendelkezik Microsoft Intune licenccel, a Storage-fiók és az Event hub beállításához Azure-előfizetésre van szükség. Az Azure-előfizetés általában ingyenes. Azonban az Azure-erőforrások használatáért kell fizetnie, beleértve az archiváláshoz használt Storage-fiókot és a streaming Event hub-t. Az adatmennyiség és a költségek a bérlő méretétől függően változnak.

### <a name="storage-size-for-activity-logs"></a>A tevékenységi naplók tárolási mérete

Minden naplózási esemény körülbelül 2 KB tárterületet használ. Az 100 000-felhasználókkal rendelkező bérlők napi körülbelül 1 500 000 eseményt igényelhetnek. Naponta 3 GB tárterületre lehet szükség. Mivel az írások jellemzően öt perces kötegekben történnek, havonta körülbelül 9 000 írási művelet várható.

A következő táblázatok a bérlő méretétől függően a költségbecslést mutatják. Emellett egy általános célú v2-es Storage-fiókot is tartalmaz az USA nyugati régiójában legalább egy évig az adatmegőrzéshez. A naplókhoz várt adatmennyiség becsült értékének megszerzéséhez használja az [Azure Storage díjszabási számológépét](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Naplózás 100 000-felhasználókkal**

| | |
|---|---|
|Esemény/nap| 1 500 000|
|Becsült adatmennyiség havonta| 90 GB|
|Becsült díj havonta (USD)| $1,93|
|Becsült díj évente (USD)| $23,12|

**Naplózás 1 000-felhasználókkal**

| | |
|---|---|
|Esemény/nap| 15,000|
|Becsült adatmennyiség havonta| 900 MB|
|Becsült díj havonta (USD)| $0,02|
|Becsült díj évente (USD)| $0,24|

### <a name="event-hub-messages-for-activity-logs"></a>Event hub-üzenetek a tevékenység naplóihoz

Az eseményeket általában öt percenként kell kötegelt beszámítani, és egyetlen üzenetként kell elküldeni az adott időkereten belüli összes eseményre. Az Event hub-ban lévő üzenet maximális mérete 256 KB. Ha az adott időkereten belül az összes üzenet teljes mérete meghaladja ezt a kötetet, akkor több üzenet is el lesz küldve.

Például körülbelül 18 esemény/másodperc általában a több mint 100 000 felhasználó nagy bérlője esetében fordul elő. Ez 5 percenként 5 400 eseményt tesz elérhetővé (300 másodperc x 18 esemény). A naplófájlok körülbelül 2 KB/eseményre vonatkoznak. Ez 10,8 MB-nyi adattal egyenlő. Így a 43-es üzeneteket az Event hub továbbítja az adott öt perces intervallumban.

Az alábbi táblázat az USA nyugati régiójában található alapszintű Event hub becsült költségét tartalmazza, az események mennyiségétől függően. A naplókhoz várt adatmennyiség becsléséhez használja a [Event Hubs árképzési számológépet](https://azure.microsoft.com/pricing/details/event-hubs/).

**Naplózás 100 000-felhasználókkal**

| | |
|---|---|
|Események másodpercenként| 18|
|Események száma öt percenként| 5 400|
|Kötet/időköz| 10,8 MB|
|Üzenetek/időköz| 43|
|Üzenet/hó| 371 520|
|Becsült díj havonta (USD)| $10,83|

**Naplózás 1 000-felhasználókkal**

| | |
|---|---|
|Események másodpercenként|0,1 |
|Események száma öt percenként| 52|
|Kötet/időköz|104 KB |
|Üzenetek/időköz|1 |
|Üzenet/hó|8 640 |
|Becsült díj havonta (USD)|$10,80 |

### <a name="log-analytics-cost-considerations"></a>Log Analytics a költséghatékonysággal kapcsolatos megfontolások

Az Log Analytics munkaterület kezelésével kapcsolatos költségek áttekintését lásd: a [költségek kezelése az adatmennyiség szabályozásával és a megőrzéssel log Analyticsban](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Gyakori kérdések

Válaszoljon a gyakori kérdésekre, és olvassa el a Azure Monitor Intune-naplókkal kapcsolatos ismert problémákat.

### <a name="which-logs-are-included"></a>Mely naplók tartoznak ide?

A naplózási naplók és a működési (előzetes) naplók egyaránt elérhetők útválasztáshoz a funkció használatával.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>A művelet után Mikor jelenik meg a megfelelő naplók az Event hub-ban?

A naplók általában a művelet végrehajtása után néhány percen belül megjelennek az Event hub-ban. [Mi az Azure Event Hubs?](https://docs.microsoft.com/azure/event-hubs/) További információkat tartalmaz.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>A művelet után Mikor jelenik meg a megfelelő naplók a Storage-fiókban?

Az Azure Storage-fiókok esetében a késés a művelet futtatása után 5 – 15 percen belül megtörténik.

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>Mi történik, ha egy rendszergazda megváltoztatja a diagnosztikai beállítások megőrzési időtartamát?

Az új adatmegőrzési szabályt a változás után gyűjtött naplókra alkalmazza a rendszer. A szabályzat módosítása előtt gyűjtött naplók nem érintettek.

### <a name="how-much-does-it-cost-to-store-my-data"></a>Mennyibe kerül az adataim tárolása?

A tárolási költségek a naplók méretétől és a kiválasztott megőrzési időszaktól függenek. A bérlők becsült költségeinek listáját, amely a generált naplózási mennyiségtől függ, tekintse meg a [tevékenységi naplók tárolási méretét](#storage-size-for-activity-logs) (ebben a cikkben).

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Mennyibe kerül az adataim egy Event hubhoz való továbbítása?

A folyamatos átviteli költségek a percenként fogadott üzenetek számától függnek. A költségek kiszámításának és az üzenetek számán alapuló költségek becslésének részleteiért lásd a jelen cikk [Event hub-üzenetek a tevékenység naplóihoz](#event-hub-messages-for-activity-logs) című részét.

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Hogyan integrálja az Intune-naplókat az SIEM-rendszerrel?

Azure Monitor és Event Hubs használatával továbbíthatja a naplókat az SIEM-rendszerébe. Először [továbbítsa a naplókat egy Event hubhoz](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). Ezután [állítsa be a Siem eszközt](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) a konfigurált Event hub-val. 

### <a name="what-siem-tools-are-currently-supported"></a>Jelenleg milyen SIEM-eszközök támogatottak?

Jelenleg a [splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), a QRadar és a [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) támogatja a Azure monitort (megnyílik egy új webhely). További információ az összekötők működéséről: az [Azure monitoring-adatok átvitele egy Event hub-ba külső eszköz általi felhasználás](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs)céljából.

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>Az Event hub adatait külső SIEM-eszköz használata nélkül is elérheti?

Igen. Az egyéni alkalmazás naplóihoz való hozzáféréshez használhatja a [Event HUBS API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph)-t.

### <a name="what-data-is-stored"></a>Milyen adattárolók vannak tárolva?

Az Intune nem tárolja a folyamaton keresztül továbbított összes adathalmazt. Az Intune átirányítja az adatátvitelt a Azure Monitor folyamatba a bérlő hatósága számára. További információ: [Azure monitor Overview (áttekintés](https://docs.microsoft.com/azure/azure-monitor/overview)).

## <a name="next-steps"></a>További lépések

* [Archiválási tevékenység naplófájljai egy Storage-fiókba](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Tevékenységek naplóinak irányítása egy Event hubhoz](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Tevékenységek naplóinak integrálása Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
