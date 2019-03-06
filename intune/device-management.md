---
title: Eszközök kezelése a Microsoft Intune-ban – Azure | Microsoft Docs
description: Áttekintheti a Microsoft Intune-nal kezelt eszközöket, beleértve az eszközlisták csv formátumban való exportálását, megtekintheti az Azure Active Directoryhoz csatlakoztatott eszközöket, áttekintheti az eszköz műveleteinek változásnaplóját, a TeamViewer-összekötővel engedélyezheti a rendszergazdáknak az Android-eszközök távoli hibaelhárítását, és megtekintheti az eszközökön futtatható összes műveletet.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbed5ee5ca31a85f1ab227916619b0750a1b84e5
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57393997"
---
# <a name="what-is-microsoft-intune-device-management"></a>A Microsoft Intune-eszközfelügyelet ismertetése

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Rendszergazdaként meg kell győződnie arról, hogy a felügyelt eszközök a felhasználók munkájához szükséges erőforrásokat nyújtják, és megvédik az adatokat.

Az **Eszközök** munkafolyamat áttekintést nyújt a felügyelt eszközökről, és lehetővé teszi, hogy távolról hajtson végre műveleteket rajtuk.

## <a name="get-to-your-devices"></a>Az eszközök elérése

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).
2. Kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
3. Válassza az **Eszközök** lehetőséget. Ez a nézet részletes információkat jelenít meg az egyes eszközökről, illetve megjeleníti a velük elvégezhető műveleteket, például:

   - Az **Áttekintés** a regisztrált eszközök pillanatképét jeleníti meg, valamint azt, hogy hány eszköz használja a különböző platformokat (Android, iOS és egyebek).
   - A **Minden eszköz** az Ön által kezelt regisztrált eszközöket jeleníti meg.

     Az **Exportálás** funkcióval létrehozhat egy .csv formátumú listát minden eszközről, egyenként 10000 (Internet Explorer), iletve 30000 (Microsoft Edge, Chrome) eszközzel.

     Egy eszköz kijelölésével [további részleteket tekinthet meg róla](device-inventory.md), így a hardveradatokat, a telepített alkalmazásokat, a megfelelőségi állapotot és egyéb adatokat.

   - Az **Azure AD-eszközök** – az Azure Active Directory (AD) szolgáltatásban regisztrált vagy azzal összekapcsolt eszközöket jeleníti meg. További tudnivalók az [Azure AD eszközkezeléséről](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - Az **Eszközműveletek** az eszközökön végrehajtott távoli műveletek előzményei, amelyek tartalmazzák a műveletet, az állapotot, a műveletet kezdeményező felhasználót és az időt.

     ![Képernyőkép az eszközműveletek figyeléséről](./media/monitor-device-actions.png)

   - Az **auditnaplókban** az Intune-ban változást előidéző tevékenységek jegyzéke érhető el. Az [auditnaplók](monitor-audit-logs.md) további részletekkel szolgálnak.
   - A **TeamViewer-összekötő** szolgáltatással az Intune-ban kezelt Android-eszközök használói távsegítséget kérhetnek a rendszergazdájuktól. További információ a [TeamViewerről](device-profile-android-teamviewer.md).
   - A **Súgó és támogatás** hibaelhárítási tippekhez, támogatás kéréséhez és az Intune állapotának ellenőrzéséhez nyújt hivatkozást.

## <a name="available-device-actions"></a>Elérhető eszközműveletek
Az egyes műveletek az eszköz platformjának és konfigurációjának függvényében érhetők el.

- [Az eszközleltár megtekintése](device-inventory.md)
- A távoli eszközműveletek futtatása:
    - [Kivonás](devices-wipe.md#retire)
    - [Törlés](devices-wipe.md#wipe)
    - [Távoli zárolás](device-remote-lock.md)
    - [Új PIN-kód](device-passcode-reset.md)
    - [Az aktiválási zár megkerülése](device-activation-lock-bypass.md) (kizárólag iOS esetében)
    - [Újrakezdés](device-fresh-start.md) (kizárólag Windowson)
    - [Elveszett eszköz mód](device-lost-mode.md) (kizárólag iOS esetében)
    - [Eszköz megkeresése](device-locate.md) (kizárólag iOS esetében)
    - [Újraindítás](device-restart.md) (kizárólag Windowson)
    - [Windows 10-es PIN-kód alaphelyzetbe állítása](device-windows-pin-reset.md)
    - [Távirányítás Androidhoz](device-profile-android-teamviewer.md)
    - [Eszköz szinkronizálása](device-sync.md)

## <a name="next-steps"></a>További lépések

- A **Minden eszköz** területen válasszon ki egy eszközt további részletek megtekintéséhez.
- Válassza az **Eszközműveletek** lehetőséget az Ön által kezelt eszközökön végzett műveletek állapotának megtekintéséhez.
