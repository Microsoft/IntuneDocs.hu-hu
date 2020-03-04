---
title: Eszközök kezelése a Microsoft Intune-ban – Azure | Microsoft Docs
description: Áttekintheti a Microsoft Intune-nal kezelt eszközöket, beleértve az eszközlisták csv formátumban való exportálását, megtekintheti az Azure Active Directoryhoz csatlakoztatott eszközöket, áttekintheti az eszköz műveleteinek változásnaplóját, a TeamViewer-összekötővel engedélyezheti a rendszergazdáknak az Android-eszközök távoli hibaelhárítását, és megtekintheti az eszközökön futtatható összes műveletet.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f5d11cade1e22ca5d306dd1896e8136f9e7c1ed
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256390"
---
# <a name="what-is-microsoft-intune-device-management"></a>A Microsoft Intune-eszközfelügyelet ismertetése

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Rendszergazdaként meg kell győződnie arról, hogy a felügyelt eszközök a felhasználók munkájához szükséges erőforrásokat nyújtják, és megvédik az adatokat.

Az **Eszközök** munkafolyamat áttekintést nyújt a felügyelt eszközökről, és lehetővé teszi, hogy távolról hajtson végre műveleteket rajtuk.

## <a name="get-to-your-devices"></a>Az eszközök elérése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza az **Eszközök** lehetőséget. Ez a nézet részletes információkat jelenít meg az egyes eszközökről, illetve megjeleníti a velük elvégezhető műveleteket, például:

   - Az **Áttekintés** megjeleníti a beléptetett eszközök vizualizációs pillanatképét, valamint azt is, hogy hány eszköz használja a különböző platformokat, például Android, iOS/iPadOS stb.
   - A **Minden eszköz** az Ön által kezelt regisztrált eszközöket jeleníti meg.

     Az **Exportálás** funkcióval az összes eszközön létrehozhat egy. zip-listát az 10 000-es (Internet Explorer) vagy 30 000 (Microsoft Edge, Chrome) növekményekben.

     Válassza ki bármelyik eszközt az [eszköz további részleteinek megtekintéséhez](device-inventory.md), beleértve a hardver részleteit, a telepített alkalmazásokat, a megfelelőségi szabályzat állapotát és egyebeket.

   - Az **Azure AD-eszközök** – az Azure Active Directory (AD) szolgáltatásban regisztrált vagy azzal összekapcsolt eszközöket jeleníti meg. További tudnivalók az [Azure AD eszközkezeléséről](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - Az **Eszközműveletek** az eszközökön végrehajtott távoli műveletek előzményei, amelyek tartalmazzák a műveletet, az állapotot, a műveletet kezdeményező felhasználót és az időt.

     ![Képernyőkép az eszközműveletek figyeléséről](./media/device-management/monitor-device-actions.png)

   - Az **auditnaplókban** az Intune-ban változást előidéző tevékenységek jegyzéke érhető el. Az [auditnaplók](../fundamentals/monitor-audit-logs.md) további részletekkel szolgálnak.
   - A **TeamViewer-összekötő** szolgáltatással az Intune-ban kezelt Android-eszközök használói távsegítséget kérhetnek a rendszergazdájuktól. További információ a [TeamViewerről](teamviewer-support.md).
   - A **Súgó és támogatás** hibaelhárítási tippekhez, támogatás kéréséhez és az Intune állapotának ellenőrzéséhez nyújt hivatkozást.

## <a name="available-device-actions"></a>Elérhető eszközműveletek
Az egyes műveletek az eszköz platformjának és konfigurációjának függvényében érhetők el.

- [Az eszközleltár megtekintése](device-inventory.md)
- A távoli eszközműveletek futtatása:
  - [Kivonás](devices-wipe.md#retire)
  - [Törlés](devices-wipe.md#wipe)
  - [Távoli zárolás](device-remote-lock.md)
  - [Új PIN-kód](device-passcode-reset.md)
  - [Aktiválási zár letiltása](device-activation-lock-disable.md) (csak iOS esetén)
  - [Újrakezdés](device-fresh-start.md) (kizárólag Windowson)
  - [Elveszett eszköz mód](device-lost-mode.md) (kizárólag iOS esetében)
  - [Eszköz megkeresése](device-locate.md) (kizárólag iOS esetében)
  - [Újraindítás](device-restart.md) (kizárólag Windowson)
  - [Windows 10-es PIN-kód alaphelyzetbe állítása](device-windows-pin-reset.md)
  - [Távirányítás Androidhoz](teamviewer-support.md)
  - [Eszköz szinkronizálása](device-sync.md)
  - [Eszköz átnevezése](device-rename.md)
  - [Egyéni értesítés küldése](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android, iOS/iPadOS)
  - [BitLocker-kulcs elforgatása](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) (csak Windows)

## <a name="next-steps"></a>További lépések

- A **Minden eszköz** területen válasszon ki egy eszközt további részletek megtekintéséhez.
- Válassza az **Eszközműveletek** lehetőséget az Ön által kezelt eszközökön végzett műveletek állapotának megtekintéséhez.
