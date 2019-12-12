---
title: Eszköz részletes adatainak megtekintése az Azure-beli Microsoft Intune-nal | Microsoft Docs
description: Megtekintheti az eszközei adatait, például az operációs rendszereket, a tárhelyet, a gyártót és a modelladatokat. Az Azure-beli Microsoft Intune-nal lekérheti a telepített alkalmazások listáját, ellenőrizheti a megfelelőségi szabályzatokat, és beállíthatja a TeamViewert. Ez hasonlít a kezelt eszközök leltárának áttekintéséhez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94c38aaf28440511720280a3c5a1ebda5b9f2ab1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74819780"
---
# <a name="see-device-details-in-intune"></a>Eszközadatok megtekintése az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az **Eszközök** funkció további részletekkel szolgál a kezelt eszközökkel kapcsolatban, például hardveradatokkal és a telepített alkalmazások listájával.

Ez a cikk bemutatja, hogyan tekintheti meg az összes eszközét és azok tulajdonságait az Azure Portalon.

## <a name="view-the-device-details"></a>Eszköz részletes adatainak megtekintése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza az **Eszközök** > **Minden eszköz** lehetőséget, majd jelölje ki a listában szereplő eszközök egyikét, hogy megnyissa annak részletes adatait:

   - Az **Áttekintés** megjeleníti az eszköz nevét, és felsorolja az eszköz néhány kulcsfontosságú tulajdonságát, például azt, hogy egy saját eszköz (BYOD) eszköz-e, és hogy van-e. A következő műveleteket végezheti el az eszközön:
      - [Kivonás](devices-wipe.md#retire)
      - [Törlés](devices-wipe.md#wipe)
      - [Távoli zárolás](device-remote-lock.md)
      - [Eszköz szinkronizálása](device-sync.md)
      - [Új PIN-kód](device-passcode-reset.md)
      - [Újraindítás](device-restart.md) (kizárólag Windowson)
      - [Újrakezdés](device-fresh-start.md) (kizárólag Windowson)
      - Távsegítség-munkamenet indítása
   - [Saját létrehozású eszközkategória](../enrollment/device-group-mapping.md) hozzárendelésére és az eszköz tulajdonosának (saját eszköz vagy vállalati eszköz) átállítására használja a **Tulajdonságok** lehetőséget.
   - A **hardver** számos információt tartalmaz az eszközről, például az eszköz azonosítóját, az operációs rendszert és a verziót, a tárolóhelyet és további részleteket.
   - Az **Észlelt alkalmazások** verziójukkal együtt sorolja fel azon telepített alkalmazásokat, amelyet az Intune talált az eszközön. További információ: az [Intune által felderített alkalmazások](../apps/app-discovered-apps.md).
   - Az **Eszközmegfelelőség** a hozzárendelt megfelelőségi szabályzatok listája mellett azt is tartalmazza, hogy az eszköz megfelelő vagy nem.
   - Az **Eszközkonfiguráció** az eszközhöz rendelt összes eszközkonfigurációs szabályzat listáját mutatja meg, és hogy a szabályzat alkalmazása sikeres vagy sikertelen.

## <a name="hardware-device-details"></a>Hardvereszköz részletes adatai
Az eszközök által használt szolgáltatótól függően az összes adat gyűjtése nem lehetséges

> [!Note]  
> A hardver-és a szoftveres leltár 7 naponta frissül az Intune szolgáltatásban.

|Adat|Description|Platfésm| 
|--------------|----------------------|----|  
|Név|Az eszköz neve.|Windows, iOS|
|Felügyeleti név|A csak a konzolon használt eszköznév. Ennek a névnek a módosítása nem változtatja meg a nevet az eszközön.|Windows, iOS|
|UDID|Az eszköz egyedi eszközazonosítója.|Windows, iOS|
|Intune-eszközazonosító|Az eszközt egyedileg azonosító GUID.|Windows, iOS|
|Sorozatszám|Az eszköz gyártótól származó sorozatszáma.|Windows, iOS|
|Megosztott eszköz|Ha **Igen**, akkor az eszköz több felhasználó között van megosztva.|Windows, iOS|
|Felhasználó által jóváhagyott regisztráció|Ha **Igen**, akkor az eszköz felhasználó által jóváhagyott regisztrációja lehetővé teszi, hogy a rendszergazdák bizonyos biztonsági beállításokat kezelhesse az eszközön.|Windows, iOS|
|Operációs rendszer|Az eszközön futó operációs rendszer.|Windows, iOS|
|Operációs rendszer verziója|Az eszközön futó operációs rendszer verziója.|Windows, iOS|
|Operációs rendszer nyelve|Az eszközön futó operációs rendszerhez beállított nyelv.|Windows, iOS|
|Buildszám|Az operációs rendszer összeállításának száma.|Android:|
|Biztonsági javítási szint|Az eszköz biztonsági javítási szintje.|Android:|
|Teljes tárterület|Az eszközön lévő teljes tárterület (gigabájtban).|Windows, iOS|
|Szabad tárterület|Az eszközön lévő felhasználatlan tárterület (gigabájtban).|Windows, iOS|
|IMEI|Az eszköz Nemzetközi mobilkészülék-azonosító (IMEI) száma.|Windows, iOS, Android|
|MEID|Az eszköz mobilkészülék-azonosító száma.|Windows, iOS, Android|
|Gyártó|Az eszköz gyártója.|Windows, iOS, Android|
|Modell|Az eszköz típusa.|Windows, iOS, Android|
|Telefonszám|Az eszközhöz rendelt telefonszám.|Windows, iOS, Android *|
|Előfizetés-szolgáltató|Az eszköz vezeték nélküli szolgáltatója.|Windows, iOS, Android|
|Mobiltechnológia|Az eszköz által használt rádiórendszer.|Windows, iOS, Android|
|Wi-Fi MAC|Az eszköz MAC-címe.|Windows, iOS, Android|
|ICCID|Az integrált áramköri kártya (ICC) azonosítója, amely a SIM-kártya egyedi azonosítószáma.|Windows, iOS, Android|
|Regisztrálás dátuma|Az eszköz Intune-ban történt regisztrálásának dátuma és időpontja.|Windows, iOS, Android|
|Utolsó kapcsolat|Az eszköz Intune-hoz való utolsó kapcsolódásának dátuma és időpontja.|Windows, iOS, Android|
|Kód az aktiválási zár megkerüléséhez|Az aktiválási zár megkerüléséhez használható kód.|iOS|
|Az Azure AD-ban regisztrálva|Ha **Igen**, akkor az eszköz regisztrálva van az Azure Active Directoryban.|Windows, iOS, Android|
|Intune regisztrálva|Ha **Igen**, az eszköz regisztrálva van az Intune-ban|Windows, iOS, Android|
|Megfelelőség|Az eszköz megfelelőségi állapota.|Windows, iOS, Android|
|EAS aktiválva|Ha **Igen**, akkor az eszköz szinkronizálva van egy Exchange-postafiókkal.|Windows, iOS, Android|
|EAS-aktiválási azonosító|Az eszköz Exchange ActiveSync-azonosítója.|Windows, iOS, Android|
|Felügyelt|Ha **Igen**, akkor a rendszergazdák fokozott felügyelettel rendelkeznek az eszköz felett.|Windows, iOS, Android|
|Titkosítva|Ha **Igen**, akkor az eszközön tárolt adatok titkosítva vannak.|Windows, iOS, Android|

a \* nem érhető el az Androidban a Google Policy Managerrel, például a teljes körűen felügyelt és a dedikált eszközökkel

## <a name="next-steps"></a>További lépések
Ismerje meg az Intune-beli [eszközkezelés](device-management.md) további funkcióit.
