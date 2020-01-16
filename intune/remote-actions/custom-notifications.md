---
title: Egyéni értesítések küldése a felhasználóknak a Microsoft Intune
titleSuffix: Microsoft Intune
description: Egyéni leküldéses értesítések létrehozása és küldése az Intune-nal az iOS-és Android-eszközök felhasználói számára
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/15/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d42651b11891f3d830c0d90e70a9ecd98ea5bfb7
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036608"
---
# <a name="send-custom-notifications-in-intune"></a>Egyéni értesítések küldése az Intune-ban  

A Microsoft Intune használatával egyéni értesítéseket küldhet a felügyelt iOS-és Android-eszközök felhasználóinak. Ezek az üzenetek szabványos leküldéses értesítésként jelennek meg a Céges portál alkalmazásból és a felhasználó eszközén található Microsoft Intune alkalmazásból, ugyanúgy, mint az eszközön lévő más alkalmazások értesítései. A macOS és a Windows rendszerű eszközök nem támogatják az egyéni Intune-értesítéseket.   

Az egyéni értesítési üzenetek közé tartozik egy rövid cím és egy 500 karakterből álló üzenettörzs. Ezek az üzenetek bármilyen általános kommunikációs célra testreszabhatók.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Egyéni értesítések küldésének gyakori forgatókönyvei  

- Értesítés az összes alkalmazottról az ütemterv változásáról, például a zord időjárási idő miatti bezárások létrehozásáról.
- Értesítés küldése egyetlen eszköz felhasználójának egy sürgős kérelem továbbítására, például az eszköz újraindítására a frissítés telepítésének befejezéséhez. 

## <a name="considerations-for-using-custom-notifications"></a>Az egyéni értesítések használatának szempontjai

**Eszközök konfigurálása** 

- Az eszközökön telepítve kell lennie a Céges portál alkalmazásnak vagy a Microsoft Intune alkalmazásnak, mielőtt a felhasználók egyéni értesítéseket tudnak fogadni. Emellett konfigurált engedélyekkel kell rendelkezniük ahhoz, hogy a Céges portál alkalmazás vagy a Microsoft Intune alkalmazás leküldéses értesítéseket küldjön. Ha szükséges, a Céges portál alkalmazás és a Microsoft Intune alkalmazás kérheti a felhasználókat, hogy engedélyezzenek értesítéseket.  
- Androidon a Google Play-szolgáltatások egy szükséges függőség.  
- Az eszköznek regisztrálva kell lennie a MDM.

**Engedélyek**:
- Ha értesítéseket szeretne küldeni a csoportoknak, a fiókjának a következő RBAC engedéllyel kell rendelkeznie az Intune-ban: *Organization* > **Update**.
- Ha értesítéseket szeretne küldeni egy eszközre, a fiókjának a következő RBAC engedéllyel kell rendelkeznie az Intune-ban: *távoli feladatok* > **Egyéni értesítések küldése**.

**Értesítések létrehozása**:  
- Üzenet létrehozásához használjon egy Intune-szerepkörhöz rendelt fiókot, amely tartalmazza a **szervezetre**vonatkozó **frissítési** engedélyt. Engedélyek felhasználóhoz rendeléséhez lásd: [szerepkör-hozzárendelések](../fundamentals/role-based-access-control.md#role-assignments)  
- Az egyéni értesítések 50 karakteres címekre és 500 karakteres üzenetekre korlátozódnak.  
- Az Intune nem menti az elküldött üzeneteket. Ha újra el szeretné küldeni az üzenetet, újra létre kell hoznia az üzenetet.  
- Legfeljebb 25 üzenetet küldhet a csoportoknak óránként. Ez a korlátozás a bérlő szintjén van. Ez a korlátozás nem vonatkozik a magánszemélyeknek küldött értesítések küldésére.
- Amikor üzeneteket küld az egyes eszközökre, óránként legfeljebb 10 üzenetet küldhet ugyanarra az eszközre. 
- Az értesítések csoportokba való hozzárendelésével több felhasználónak vagy eszköznek is küldhet értesítéseket. A csoportok használatakor minden értesítés közvetlenül legfeljebb 25 csoportot tud megcélozni. A beágyazott csoportok nem számítanak bele a teljes összegbe.  

  A csoportok tartalmazhatnak felhasználókat vagy eszközöket, de csak a felhasználóknak küldött üzeneteket, valamint minden olyan iOS-vagy Android-eszközt, amelyet a felhasználó regisztrált.  
- Értesítéseket egyetlen eszközre is küldhet. A csoportok használata helyett válasszon ki egy eszközt, majd egy távoli [eszköz művelettel](device-management.md#available-device-actions) küldje el az egyéni értesítést.  

**Kézbesítés**:  
- Az Intune üzeneteket küld a felhasználók Céges portál alkalmazásnak vagy a Microsoft Intune alkalmazásnak, amely ezután létrehozza a leküldéses értesítést. A felhasználóknak nem kell bejelentkezniük az alkalmazásba az értesítés küldéséhez az eszközön.  
- Az Intune, valamint a Céges portál alkalmazás és a Microsoft Intune alkalmazás nem garantálja az egyéni értesítések kézbesítését. Előfordulhat, hogy az egyéni értesítések több órányi késés után is megjelennek, így sürgős üzenetekhez nem használhatók.  
- Az Intune-ból származó egyéni értesítési üzenetek szabványos leküldéses értesítésként jelennek meg az eszközökön. Ha a Céges portál alkalmazás egy iOS-eszközön van megnyitva, amikor megkapja az értesítést, a rendszer leküldéses értesítés helyett az alkalmazásban jeleníti meg az értesítést.  
- Az egyéni értesítések az eszköz beállításaitól függően az iOS-és Android-eszközök zárolási képernyőjén is láthatók.  
- Az Android-eszközökön más alkalmazások is hozzáférhetnek az egyéni értesítések adataihoz. Ne használja őket bizalmas kommunikációra.  
- Azok a felhasználók, akik nemrég lettek regisztrálva, vagy egy csoportból eltávolított felhasználók, továbbra is kaphatnak olyan egyéni értesítést, amelyet később küldenek a csoportnak.  Hasonlóképpen, ha a csoportba egy egyéni értesítés elküldése után ad hozzá egy felhasználót egy csoporthoz, az újonnan felvett használatával megkaphatja a korábban elküldött értesítési üzenetet.  

## <a name="send-a-custom-notification-to-groups"></a>Egyéni értesítés küldése a csoportoknak  

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431) egy olyan fiókkal, amely jogosult értesítések létrehozására és küldésére, valamint a **bérlői felügyelet** > **Egyéni értesítések**elemre.  

2. Az alapvető beállítások lapon adja meg a következőket, majd a folytatáshoz kattintson a **tovább** gombra.  
   - **Title (cím** ) – Itt adhatja meg az értesítés címét. A címek legfeljebb 50 karakterből állhatnak.  
   - **Törzs** – Itt adhatja meg az üzenetet. Az üzenetek legfeljebb 500 karakterből állhatnak.

   ![Egyéni értesítés létrehozása](./media/custom-notifications/custom-notifications.png)  

3. A **hozzárendelések** lapon válassza ki azokat a csoportokat, amelyekhez az egyéni értesítést el szeretné küldeni, majd a folytatáshoz kattintson a Tovább gombra.  

4. A **felülvizsgálat + létrehozás** lapon tekintse át az információkat, és ha készen áll az értesítés elküldésére, válassza a **Létrehozás**lehetőséget.  

Az Intune az azonnal létrehozott üzeneteket dolgozza fel. Az üzenet elküldésének egyetlen megerősítése az az Intune-értesítés, amely megerősíti, hogy az egyéni értesítés el lett küldve.  

![Küldött értesítés megerősítése](./media/custom-notifications/notification-sent.png)  

Az Intune nem követi az Ön által küldött egyéni értesítéseket, és az eszközök nem naplózzák az eszköz értesítési központján kívüli nyugtát.  

## <a name="send-a-custom-notification-to-a-single-device"></a>Egyéni értesítés küldése egyetlen eszközre  

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431) egy olyan fiókkal, amely jogosult értesítések létrehozására és küldésére, majd lépjen az **eszközök** > **minden eszköz**elemre.

2. Kattintson duplán annak a felügyelt eszköznek a nevére, amelyhez értesítést szeretne küldeni, hogy megnyissa az eszközök *Áttekintés* lapját.

3. Az eszközök **áttekintése** lapon az **Egyéni értesítési eszköz küldése** művelettel nyissa meg az *Egyéni értesítés küldése* panelt. Ha ez a beállítás nem érhető el, válassza az oldal jobb felső részén található **...** (ellipszisek) lehetőséget, majd válassza az **Egyéni értesítés küldése**lehetőséget.

4. Az **Egyéni értesítés küldése** panelen a következő üzenet részleteit kell megadnia:  

   - **Title (cím** ) – Itt adhatja meg az értesítés címét. A címek legfeljebb 50 karakterből állhatnak.  
   - **Törzs** – Itt adhatja meg az üzenetet. Az üzenetek legfeljebb 500 karakterből állhatnak.  

5. Válassza a **Küldés** lehetőséget az egyéni értesítés az eszközre való elküldéséhez. A csoportoknak küldött értesítésekkel ellentétben nem konfigurálhat hozzárendelést, vagy nem tekintheti át az üzenetet a küldés előtt.  

Az Intune azonnal feldolgozza az üzenetet. Az üzenet elküldésének egyetlen megerősítése a konzolon megjelenő Intune-értesítés, amely az elküldött üzenet szövegét jeleníti meg.  

## <a name="receive-a-custom-notification"></a>Egyéni értesítés fogadása  

Egy eszközön a felhasználók az Intune által az Céges portál alkalmazásból vagy a Microsoft Intune alkalmazásból küldött szabványos leküldéses értesítésként látják az egyéni értesítési üzeneteket. Ezek az értesítések hasonlóak az eszközön lévő más alkalmazásokból érkező leküldéses értesítések felhasználóinak.  

IOS-eszközökön, ha a Céges portál alkalmazás az értesítés fogadásakor meg van nyitva, az értesítés az alkalmazásban jelenik meg leküldéses értesítés helyett.  

Az értesítés addig marad, amíg a felhasználó el nem utasítja.  

## <a name="next-steps"></a>További lépések  

[Eszközök kezelése](device-management.md)
