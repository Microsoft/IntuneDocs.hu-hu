---
title: A biztonsági alapkonfigurációk sikeres vagy sikertelen állapotának megtekintése a Microsoft Intune-Azure-ban | Microsoft Docs
description: 'A biztonsági alapkonfigurációk a Microsoft Intune MDM lévő felhasználók és eszközök számára történő telepítésekor a hiba, az ütközés és a sikeres állapot ellenőrzése. Lásd: az ügyfél naplófájljaival kapcsolatos hibák és az Intune jelentéskészítési funkcióinak használata.'
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d8ee4ec6a5bcb29a51b68cff7b840823b678636
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569285"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Biztonsági alapkonfiguráció és profilok figyelése Microsoft Intune

Az Intune számos lehetőséget kínál a biztonsági alapkonfigurációk figyelésére. Nyomon követheti a felhasználókra és eszközökre vonatkozó biztonsági alapkonfigurációk profilt. Figyelemmel kísérheti a tényleges alapkonfigurációt, valamint az összes olyan eszközt, amely megfelel az ajánlott értékeknek (vagy nem egyeznek).

Ez a cikk végigvezeti mindkét figyelési lehetőségen.

Az [Intune-beli biztonsági](../security-baselines.md) alapkonfigurációk további részleteket tartalmaznak a Microsoft Intune biztonsági alapkonfigurációk szolgáltatásával kapcsolatban.

## <a name="monitor-the-baseline-and-your-devices"></a>Az alapkonfiguráció és az eszközök figyelése

Az alapkonfiguráció monitorozásakor a Microsoft javaslatai alapján betekintést nyerhet az eszközök biztonsági állapotára. Ezeket az információkat az Intune-konzol biztonsági alapkonfigurációjának áttekintés ablaktábláján tekintheti meg.  Akár 24 órát is igénybe vesz, hogy az egyes alaptervek első kiosztása után megjelenjenek az adathalmazok. A későbbi módosítások akár hat órát is igénybe vesznek.

Az alaptervhez és az eszközökhöz tartozó figyelési adatmegjelenítéshez jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431). Ezután válassza az **Endpoint security** > **biztonsági**alapkonfigurációk lehetőséget, válasszon ki egy alapkonfigurációt, és tekintse meg az **Áttekintés** panelt.

Az **Áttekintés** panel két módszert biztosít az állapot figyelésére:

- **Device View (eszköz nézet** ) – összefoglalás arról, hogy hány eszköz szerepel az alapkonfigurációban az egyes állapotok kategóriájában.
- **Kategóriánként** – egy nézet, amely megjeleníti az alapkonfiguráció egyes kategóriáit, és az egyes alapértékekhez tartozó egyes állapotüzenetek esetében az eszközök százalékos arányát tartalmazza.

Minden eszközt a következő állapotok egyike képvisel (az *eszköz* nézetben és a *kategóriánkénti* nézetekben is használatos):

- Alapértékek – az alapkonfigurációban lévő összes **beállítás megegyezik az** ajánlott beállításokkal.
- **Nem felel** meg az alapkonfigurációnak – az alapterv legalább egy beállítása nem felel meg az ajánlott beállításnak.

  > [!NOTE]
  > Amikor létrehoz vagy szerkeszt egy alapkonfigurációt, az alapértelmezett értékre vagy konfigurációs beállításra végrehajtott módosítások miatt a "nem felel meg az alapterv" állapotnak. Ha segítségre van szükség a módosított beállítások meghatározásához, forduljon a Microsoft ügyfélszolgálatahoz. 

- **Helytelenül konfigurált – legalább** egy beállítás nincs megfelelően konfigurálva. Ez az állapot azt jelenti, hogy a beállítás ütközés, hiba vagy függő állapotban van.
- **Nem alkalmazható** – legalább egy beállítás nem alkalmazható, és nincs alkalmazva.

### <a name="device-view"></a>Eszköz nézet

Az Áttekintés panel egy diagramon alapuló összegzést jelenít meg arról, hogy hány eszköz rendelkezik az alapterv adott állapotával. Biztonsági alaphelyzetek **a hozzárendelt Windows 10-es eszközökhöz**.

![Az eszközök állapotának ellenõrzése](./media/security-baselines-monitor/overview.png)

Ha egy eszköz eltérő állapotú az alapkonfiguráció különböző csoportjaitól, az eszközt egyetlen állapot jelöli. Az eszközt jelképező állapot a következő elsőbbségi sorrendben történik: helytelenül van konfigurálva, nem **felel**meg az **alapkonfigurációnak**, **nem alkalmazható**, az alapértéknek **felel meg.**

Ha például egy eszköz *nem megfelelőként*van besorolva, *és egy* vagy több olyan beállítást tartalmaz, amely nem egyezik az alapkonfigurációval, az *eszköz hibásan van besorolva.*

Kattintson a diagramra a részletezéshez, és tekintse meg a különböző állapotokkal rendelkező eszközök listáját. A listából kiválaszthatja az egyes eszközök adatait, és megtekintheti az egyes eszközök részleteit. Például:

- Válassza ki az **eszköz konfigurációját** > válassza ki a profilt hibás állapottal:

  ![Profil állapotának megtekintése](./media/security-baselines-monitor/device-configuration-profile-list.png)

- Válassza ki a hiba profilt. Megjelenik a profil összes beállításának listája, és az állapotuk látható. Most görgessen a hibát okozó beállítás megkereséséhez:

  ![Tekintse meg a hibát okozó beállítást](./media/security-baselines-monitor/profile-with-error-status.png)

Ezzel a jelentéssel megtekintheti a profilban a problémát okozó beállításokat. Az eszközökön üzembe helyezett szabályzatok és profilok további részleteit is megismerheti.

> [!NOTE]
> Ha egy tulajdonság úgy van beállítva, hogy az alapterv **ne legyen konfigurálva** , a rendszer figyelmen kívül hagyja a beállítást, és nem kényszeríti ki a korlátozásokat. A tulajdonság nem jelenik meg egyetlen jelentésben sem.

### <a name="per-category-view"></a>Kategóriánkénti nézet

Az Áttekintés panel az alapkonfigurációhoz tartozó kategóriánkénti diagramot jeleníti meg. Biztonsági alaphelyzetek **kategória szerint**.  Ez a nézet az alaptervből származó kategóriákat jeleníti meg, és az egyes kategóriákhoz tartozó állapot besorolású eszközök százalékos arányát azonosítja.

![Az állapot kategória szerinti nézete](./media/security-baselines-monitor/monitor-baseline-per-category.png)

Az alapkonfiguráció **állapota nem jelenik** meg, amíg az eszközök 100%-a nem jelenti a kategória állapotát.

A kategóriánkénti nézetet minden oszlop szerint rendezheti az oszlop tetején található felfelé mutató nyíl ikon kiválasztásával.

## <a name="monitor-the-profile"></a>A profil figyelése

A profil figyelése betekintést nyújt az eszközök központi telepítési állapotára, de az alapkövetelmények alapján nem a biztonsági állapotot.

1. Az Intune-ban válassza a **biztonsági** alapkonfigurációk > a **létrehozott**alapkonfiguráció > profilok lehetőséget.

2. Válasszon egy profilt. Az **Áttekintés**területen a rendszerkép azt mutatja, hogy hány eszközt és felhasználót rendelt hozzá ehhez a profilhoz:

   ![Megtekintheti, hogy hány eszköz és felhasználó van hozzárendelve a biztonsági alapkonfigurációk profiljához](./media/security-baselines-monitor/existing-profile-overview.png)

3. A > **Tulajdonságok** **kezelése** területen megjelenik az alapkonfiguráció összes beállításának listája. A következő beállításokat is módosíthatja:

   ![A biztonsági alapkonfigurációk profiljában megtekintheti és frissítheti a beállításokat](./media/security-baselines-monitor/manage-settings.png)

4. A **figyelőben**megtekintheti a profil telepítési állapotát az egyes eszközökön, az egyes felhasználók állapotát, valamint az alapkonfiguráció minden beállításának állapotát:

   ![Tekintse meg a biztonsági alapkonfigurációk profiljának különböző figyelési lehetőségeit.](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="view-endpoint-security-configurations-per-device"></a>Végpont biztonsági konfigurációinak megtekintése eszközönként

Megtekintheti az egyes eszközökre vonatkozó biztonsági konfigurációk részleteit, amelyek segítségével elkülönítheti a helytelenül konfigurált beállításokat.

1. Jelentkezzen be a bejelentkezés a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Lépjen az **eszközök** > **minden eszköz** elemre, és válassza ki a megtekinteni kívánt eszközt.

3. A *figyelő* kategóriában válassza a **végpont biztonsági konfiguráció** elemet az adott eszközre érvényes biztonsági konfigurációk listájának megtekintéséhez.

4. Kiválaszthat egy végponti biztonsági konfigurációt a részletezéshez, és megtekintheti a biztonsági konfiguráció értékelésével kapcsolatos további részleteket az eszközön.

## <a name="troubleshoot-using-per-setting-status"></a>Hibakeresési állapot használata – problémamegoldás

Központilag telepített egy biztonsági alapkonfigurációt, de a telepítés állapota hibát jelez. A következő lépések útmutatást nyújtanak a hiba elhárításához.

1. Az Intune-ban válassza a **biztonsági** alapkonfigurációk > a **létrehozott**alapkonfiguráció > profilok lehetőséget.

2. Válasszon egy profilt > a **figyelés** > a **beállítás állapota**területen.

3. A tábla megjeleníti az összes beállítást, valamint az egyes beállítások állapotát. Válassza ki a **hiba** oszlopot vagy az **ütközés** oszlopot a hibát okozó beállítás megtekintéséhez.

### <a name="mdm-diagnostic-information"></a>Diagnosztikai információk MDM

Most már ismeri a problémás beállítást. A következő lépés annak megállapítása, hogy a beállítás Miért okoz hibát vagy ütközést.

Windows 10-es eszközökön létezik egy beépített MDM diagnosztikai információs jelentés. Ez a jelentés tartalmazza az alapértelmezett értékeket, a jelenlegi értékeket, felsorolja a szabályzatot, és megjeleníti, hogy az eszközre vagy a felhasználóra van-e telepítve, és így tovább. A jelentés segítségével meghatározhatja, hogy a beállítás miért ütközik vagy hibát okoz.

1. Az eszközön lépjen a **beállítások** > **fiókok** > **hozzáférés munkahelyi vagy iskolai**rendszerhez elemre.

2. Válassza ki a fiókot > **Info** > **speciális diagnosztikai jelentés** > **jelentés létrehozása**elemre.

3. Válassza az **Exportálás**lehetőséget, majd nyissa meg a létrehozott fájlt.

4. A jelentésben keresse meg a hiba vagy az ütközés beállítást a jelentés különböző részeiben.

  Tekintse meg például a **regisztrált konfigurációs források és a célként megadott erőforrások** szakaszt, illetve a nem **felügyelt házirendek** szakaszt. Azt is megteheti, hogy miért okoz hibát vagy ütközést.

A [Mdm hibák diagnosztizálása a Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) rendszerben további információt nyújt erről a beépített jelentésről.

> [!TIP]
>
> - Egyes beállítások a GUID azonosítót is felsorolják. Ezt a globálisan egyedi azonosítót a beállított értékekhez tartozó helyi beállításjegyzékben (Regedit) is megkeresheti.
> - A Eseménynapló naplók tartalmazhatnak bizonyos hibákat a problémás beállításról (**eseménynapló** > **alkalmazások és szolgáltatások naplói** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**).

## <a name="next-steps"></a>További lépések

[Figyelje az eszközök profiljait](../configuration/device-profile-monitor.md) , és [tekintse meg a gyakori problémákat és a megoldásokat](../configuration/device-profile-troubleshoot.md).
