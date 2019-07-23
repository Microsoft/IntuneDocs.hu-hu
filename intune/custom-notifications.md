---
title: Egyéni értesítések küldése a felhasználóknak a Microsoft Intune
titleSuffix: ''
description: Egyéni leküldéses értesítések létrehozása és küldése az Intune-nal az iOS-és Android-eszközök felhasználói számára
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 7/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1caff820daf2e278c50d154873f569163b264315
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2019
ms.locfileid: "68377085"
---
# <a name="send-custom-notifications-in-intune"></a>Egyéni értesítések küldése az Intune-ban  

A Microsoft Intune használatával egyéni értesítéseket küldhet a felügyelt iOS-és Android-eszközök felhasználóinak. Ezek az üzenetek szabványos leküldéses értesítésként jelennek meg a felhasználó eszközén lévő Céges portál alkalmazásból, ahogy az eszközön lévő más alkalmazások értesítései is megjelennek. A Windows-eszközök nem támogatják az egyéni Intune-értesítéseket.   

Az egyéni értesítési üzenetek közé tartozik egy rövid cím és egy 500 karakterből álló üzenettörzs. Ezek az üzenetek bármilyen általános kommunikációs célra testreszabhatók.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Egyéni értesítések küldésének gyakori forgatókönyvei  

- Egyéni értesítések használata adott felhasználók riasztására egy új, a Céges portál elérhető alkalmazásról.  
- Értesítés az összes alkalmazottról az ütemterv változásáról, például a zord időjárás miatti bezárások létrehozásáról.  

## <a name="considerations-for-using-custom-notifications"></a>Az egyéni értesítések használatának szempontjai  

**Eszköz konfigurációja**:  
- Az eszközökön telepítve kell lennie a Céges portál alkalmazásnak, mielőtt a felhasználók egyéni értesítéseket tudnak fogadni. Emellett konfigurált engedélyekkel kell rendelkezniük ahhoz, hogy az Céges portál alkalmazás leküldéses értesítéseket küldjön. A Céges portál kérni fogja a felhasználókat, hogy engedélyezzenek értesítéseket.  
- Androidon a Google Play-szolgáltatások egy szükséges függőség.  

**Értesítések létrehozása**:  
- Üzenet létrehozásához használjon egy Intune-szerepkörhöz rendelt fiókot, amely tartalmazza a szervezetre vonatkozó **frissítési** engedélyt . Engedélyek felhasználóhoz rendeléséhez lásd: [szerepkör](role-based-access-control.md#role-assignments) -hozzárendelések  
- Az egyéni értesítések 50 karakteres címekre és 500 karakteres üzenetekre korlátozódnak.  
- Az Intune nem menti az elküldött üzeneteket. Ha újra el szeretné küldeni az üzenetet, újra létre kell hoznia az üzenetet.  
- Óránként legfeljebb 25 üzenet küldhető el. Ez a korlátozás a bérlő szintjén van.  
- Minden értesítés közvetlenül legfeljebb 25 csoportot tud megcélozni. A beágyazott csoportok nem számítanak bele a teljes összegbe.  
- A csoportok tartalmazhatnak felhasználókat vagy eszközöket, de az üzeneteket csak a felhasználók kapják meg, és a rendszer minden olyan iOS-vagy Android-eszközre elküldi, amelyet a felhasználó regisztrált.  

**Kézbesítés**:  
- Az Intune egy értesítés elküldése után legfeljebb egy óráig próbálkozik a kézbesítéssel.  
- Az Intune üzeneteket küld a felhasználók Céges portál alkalmazásnak, amely ezután létrehozza a leküldéses értesítést. A felhasználóknak nem kell bejelentkezniük az alkalmazásba az értesítés küldéséhez az eszközön.  
- Az Intune és a Céges portál alkalmazás nem tudja garantálni az egyéni értesítések kézbesítését. Előfordulhat, hogy az egyéni értesítések több órányi késés után is megjelennek, így sürgős üzenetekhez nem használhatók.  
- Az Intune-ból származó egyéni értesítési üzenetek szabványos leküldéses értesítésként jelennek meg az eszközökön. Ha a Céges portál alkalmazás egy iOS-eszközön van megnyitva, amikor megkapja az értesítést, a rendszer leküldéses értesítés helyett az alkalmazásban jeleníti meg az értesítést.  
- Az egyéni értesítések az eszköz beállításaitól függően az iOS-és Android-eszközök zárolási képernyőjén is láthatók.  
- Az Android-eszközökön más alkalmazások is hozzáférhetnek az egyéni értesítések adataihoz. Ne használja őket bizalmas kommunikációra.  
- Azok a felhasználók, akik nemrég lettek regisztrálva, vagy egy csoportból eltávolított felhasználók, továbbra is kaphatnak olyan egyéni értesítést, amelyet később a csoportnak küldenek.  Hasonlóképpen, ha a csoportba egy egyéni értesítés elküldése után ad hozzá egy felhasználót egy csoporthoz, akkor az újonnan felvett használatával megkaphatja a korábban elküldött értesítési üzenetet.  

## <a name="send-a-custom-notification"></a>Egyéni értesítés küldése  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba egy olyan fiókkal, amely rendelkezik értesítések létrehozásához és küldéséhez szükséges engedélyekkel, majd lépjen az **eszközök** > **Egyéni értesítések küldése**elemre.  

2. Az alapvető beállítások lapon adja meg a következőket, majd a folytatáshoz kattintson a **tovább** gombra.  
   - **Title (cím** ) – Itt adhatja meg az értesítés címét. A címek legfeljebb 50 karakterből állhatnak.  
   - **Törzs** – Itt adhatja meg az üzenetet. Az üzenetek 500 karakterre korlátozódnak

   ![Egyéni értesítés létrehozása](./media/custom-notifications/custom-notifications.png)  

3. A **hozzárendelések** lapon válassza ki azokat a csoportokat, amelyekhez az egyéni értesítést el szeretné küldeni, majd a folytatáshoz kattintson a Tovább gombra.  

4. A **felülvizsgálat + létrehozás** lapon tekintse át az információkat, és ha készen áll az értesítés elküldésére, válassza a **Létrehozás**lehetőséget.  

Az Intune az azonnal létrehozott üzeneteket dolgozza fel. Az üzenet elküldésének egyetlen megerősítése az az Intune-értesítés, amely megerősíti, hogy az egyéni értesítés el lett küldve.  

![Küldött értesítés megerősítése](./media/custom-notifications/notification-sent.png)  

Az Intune nem követi az Ön által küldött egyéni értesítéseket, és az eszközök nem naplózzák az eszköz értesítési központján kívüli nyugtát.  

## <a name="receive-a-custom-notification"></a>Egyéni értesítés fogadása  

Egy eszközön a felhasználók az Intune által az Céges portál alkalmazástól szokásos leküldéses értesítésként küldött egyéni értesítési üzeneteket látják. Ezek az értesítések hasonlóak az eszközön lévő más alkalmazásokból érkező leküldéses értesítések felhasználóinak.  

IOS-eszközökön, ha a Céges portál alkalmazás az értesítés fogadásakor meg van nyitva, az értesítés az alkalmazásban jelenik meg leküldéses értesítés helyett.  

Az értesítés addig marad, amíg a felhasználó el nem utasítja.  

## <a name="next-steps"></a>További lépések  
[Eszközök kezelése](device-management.md)
