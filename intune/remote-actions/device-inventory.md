---
title: Eszköz részletes adatainak megtekintése az Azure-beli Microsoft Intune-nal | Microsoft Docs
description: Megtekintheti az eszközei adatait, például az operációs rendszereket, a tárhelyet, a gyártót és a modelladatokat. Az Azure-beli Microsoft Intune-nal lekérheti a telepített alkalmazások listáját, ellenőrizheti a megfelelőségi szabályzatokat, és beállíthatja a TeamViewert. Ez hasonlít a kezelt eszközök leltárának áttekintéséhez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
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
ms.openlocfilehash: df814abf9cdff3eb4d9fbac8183618461b590adb
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781917"
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
      - [Törlés](devices-wipe.md#delete-devices-from-the-intune-portal)
      - [Távoli zárolás](device-remote-lock.md)
      - [Szinkronizálási](device-sync.md)
      - [Új PIN-kód](device-passcode-reset.md)
      - [Újraindítás](device-restart.md) (kizárólag Windowson)
      - [Újrakezdés](device-fresh-start.md) (kizárólag Windowson)
      - [Autopilot alaphelyzetbe állítása]() (csak Windows)
      - [Gyors vizsgálat](../configuration/device-restrictions-windows-10.md) (csak Windows 10 esetén)
      - [Teljes vizsgálat](../configuration/device-restrictions-windows-10.md) (csak Windows 10 esetén)
       - [Eszköz átnevezése](device-rename.md)
      - Távsegítség-munkamenet indítása
   - **Saját létrehozású eszközkategória** hozzárendelésére és az eszköz tulajdonosának (saját eszköz vagy vállalati eszköz) átállítására használja a [Tulajdonságok](../enrollment/device-group-mapping.md) lehetőséget.
   - A **hardver** számos információt tartalmaz az eszközről, például az eszköz azonosítóját, az operációs rendszert és a verziót, a tárolóhelyet és további részleteket.
   - Az **Észlelt alkalmazások** verziójukkal együtt sorolja fel azon telepített alkalmazásokat, amelyet az Intune talált az eszközön. További információ: az [Intune által felderített alkalmazások](../apps/app-discovered-apps.md).
   - Az **Eszközmegfelelőség** a hozzárendelt megfelelőségi szabályzatok listája mellett azt is tartalmazza, hogy az eszköz megfelelő vagy nem.
   - Az **Eszközkonfiguráció** az eszközhöz rendelt összes eszközkonfigurációs szabályzat listáját mutatja meg, és hogy a szabályzat alkalmazása sikeres vagy sikertelen.

## <a name="hardware-device-details"></a>Hardvereszköz részletes adatai
Az eszközök által használt szolgáltatótól függően az összes adat gyűjtése nem lehetséges

> [!Note]  
> A hardver-és a szoftveres leltár 7 naponta frissül az Intune szolgáltatásban.

|Adat|Leírás|Platform| 
|--------------|----------------------|----|  
|Név|Az eszköz neve.|Windows, iOS|
|Felügyeleti név|A csak a konzolon használt eszköznév. Ennek a névnek a módosítása nem változtatja meg a nevet az eszközön.|Windows, iOS|
|UDID|Az eszköz egyedi eszközazonosítója.|Windows, iOS|
|Intune-eszközazonosító|Az eszközt egyedileg azonosító GUID.|Windows, iOS|
|Sorozatszám|Az eszköz gyártótól származó sorozatszáma.|Windows, iOS|
|Megosztott eszköz|Ha **Igen**, akkor az eszköz több felhasználó között van megosztva.|Windows, iOS|
|Felhasználó által jóváhagyott regisztráció|Ha **Igen**, akkor az eszköz felhasználó által jóváhagyott regisztrációja lehetővé teszi, hogy a rendszergazdák bizonyos biztonsági beállításokat kezelhesse az eszközön.|Windows, iOS|
|Operációs rendszer|Az eszközön futó operációs rendszer.|Windows, iOS|
|Operációs rendszer verziója|Az eszköz operációs rendszerének verziója.|Windows, iOS|
|Operációs rendszer nyelve|Az eszközön futó operációs rendszerhez beállított nyelv.|Windows, iOS|
|Buildszám|Az operációs rendszer összeállításának száma.|Android:|
|Biztonsági javítási szint|Az eszköz biztonsági javítási szintje.|Android:|
|Teljes tárterület|Az eszközön lévő teljes tárterület (gigabájtban).|Windows, iOS|
|Szabad tárterület|Az eszközön lévő felhasználatlan tárterület (gigabájtban).|Windows, iOS|
|IMEI|Az eszköz Nemzetközi mobilkészülék-azonosító (IMEI) száma.|Windows, iOS/iPadOS, Android|
|MEID|Az eszköz mobilkészülék-azonosító száma.|Windows, iOS/iPadOS, Android|
|Gyártó|Az eszköz gyártója.|Windows, iOS/iPadOS, Android|
|Modell|Az eszköz típusa.|Windows, iOS/iPadOS, Android|
|Telefonszám|Az eszközhöz rendelt telefonszám.|Windows, iOS/iPadOS, Android *|
|Előfizetés-szolgáltató|Az eszköz vezeték nélküli szolgáltatója.|Windows, iOS/iPadOS, Android|
|Mobiltechnológia|Az eszköz által használt rádiórendszer.|Windows, iOS/iPadOS, Android|
|Wi-Fi MAC|Az eszköz MAC-címe.|Windows, iOS/iPadOS, Android|
|ICCID|Az integrált áramköri kártya (ICC) azonosítója, amely a SIM-kártya egyedi azonosítószáma.|Windows, iOS/iPadOS, Android|
|Regisztrálás dátuma|Az eszköz Intune-ban történt regisztrálásának dátuma és időpontja.|Windows, iOS/iPadOS, Android|
|Utolsó kapcsolat|Az eszköz Intune-hoz való utolsó kapcsolódásának dátuma és időpontja.|Windows, iOS/iPadOS, Android|
|Kód az aktiválási zár megkerüléséhez|Az aktiválási zár letiltására alkalmas kód.|iOS|
|Az Azure AD-ban regisztrálva|Ha **Igen**, akkor az eszköz regisztrálva van az Azure Active Directoryban.|Windows, iOS/iPadOS, Android|
|Intune regisztrálva|Ha **Igen**, az eszköz regisztrálva van az Intune-ban|Windows, iOS/iPadOS, Android|
|Megfelelőség|Az eszköz megfelelőségi állapota.|Windows, iOS/iPadOS, Android|
|EAS aktiválva|Ha **Igen**, akkor az eszköz szinkronizálva van egy Exchange-postafiókkal.|Windows, iOS/iPadOS, Android|
|EAS-aktiválási azonosító|Az eszköz Exchange ActiveSync-azonosítója.|Windows, iOS/iPadOS, Android|
|Felügyelt|Ha **Igen**, akkor a rendszergazdák fokozott felügyelettel rendelkeznek az eszköz felett.|Windows, iOS/iPadOS, Android|
|Titkosítva|Ha **Igen**, akkor az eszközön tárolt adatok titkosítva vannak.|Windows, iOS/iPadOS, Android|

> [!Note]  
> A telefonszám nem leltározott az Android Enterprise dedikált vagy teljes mértékben felügyelt eszközökön.

## <a name="next-steps"></a>További lépések
Ismerje meg az Intune-beli [eszközkezelés](device-management.md) további funkcióit.
