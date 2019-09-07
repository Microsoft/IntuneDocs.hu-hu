---
title: Az iOS-szoftverfrissítési szabályzatok konfigurálása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Konfigurációs szabályzat létrehozása vagy felvétele a Microsoft Intune-ban, amellyel korlátozhatja, mikor kerüljenek automatikusan telepítésre az Intune által felügyelt, vagy ellenőrzött iOS-eszközök szoftverfrissítései. Megadhatja azokat a dátumokat és időpontokat, amelyeknél nem szeretné, hogy települjenek a frissítések. Ezt a szabályzatot csoportokhoz, felhasználókhoz és eszközökhöz is hozzárendelheti, és ellenőrizheti az esetleges telepítési hibákat is vele.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6df42d908169ab591150e88e03f2f419710c9e54
ms.sourcegitcommit: e477e399cba673a2a9e1fa342e8303ed993801eb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739207"
---
# <a name="add-ios-software-update-policies-in-intune"></a>IOS-szoftverfrissítési szabályzatok hozzáadása az Intune-ban

A-frissítési szabályzatokkal kikényszerítheti a legújabb elérhető rendszerfrissítések automatikus telepítését a felügyelt iOS-eszközökön. A szabályzat beállításakor megadhatja azokat a napokat és időpontokat, amikor nem szeretné, hogy az eszközök frissítéseket telepítsenek. 

Ez a funkció az alábbiakra vonatkozik:

- iOS 10,3 és újabb verziók (felügyelt)

Az eszköz körülbelül 8 óránként jelentkezik be az Intune-ba. Ha az eszköz elérhető frissítést talál a megadott korlátozott időszakokon kívül, akkor letölti és telepíti a legújabb rendszerfrissítéseket. Az eszköz frissítéséhez nincs szükség felhasználói beavatkozásra. A szabályzat nem akadályozza meg, hogy a felhasználó manuálisan frissítse az operációs rendszert.

## <a name="configure-the-policy"></a>A szabályzat konfigurálása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **Szoftverfrissítések** > **iOS-frissítési szabályzatok** > **Létrehozás** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a szoftverfrissítési házirend nevét. Például írja be a következőt: `iOS restricted update times`.
    - **Description** (Leírás): Adja meg a szabályzat leírását. A beállítás használata nem kötelező, de ajánlott.

4. Válassza a **beállítások > konfigurálás**lehetőséget. Adja meg a következő beállításokat:

    - **A frissítések telepítésének megakadályozására szolgáló időpontok kiválasztása**: A korlátozott időkeret megadása, ha a frissítések kényszerített telepítése nem történik meg. 
      - Az egynapos blokkok nem támogatottak, és előfordulhat, hogy nem működnek. Tegyük fel például, hogy nem állít be egy szabályzatot 8 PM *kezdő időponttal* , és 6 órakor *befejező* időpontot.
      - Egy olyan szabályzat, amely 12 órakor kezdődik, és 12 ÓRAKOR ér véget, 0 óra, nem pedig 24 óra, ami korlátozás nélkül jár.

      A korlátozott időkeret beállításakor adja meg a következő adatokat:

      - **Napok**: Válassza ki a hét napját, amikor a frissítések nincsenek telepítve. Például a hétfő, a szerda és a péntek beállítás megadásával megakadályozhatja, hogy a frissítések ezekben a napokban legyenek telepítve.
      - **Időzóna**: Válasszon időzónát.
      - **Kezdés időpontja**: Válassza ki a korlátozott időkeret kezdési idejét. Adja meg például az 5, hogy a frissítések ne legyenek telepítve 5 ÓRAKOR.
      - **Befejezés időpontja**: Válassza ki a korlátozott időkeret befejezési időpontját. Adja meg például a következőt: 1, így a frissítések telepíthetők a-től kezdődően.

    - A **szoftverfrissítések láthatóságának késleltetése a végfelhasználók számára az ütemezett frissítések módosítása nélkül (nap)** : 

      \* * Ha a felügyelt iOS-eszközökön bizonyos ideig szeretné megtekinteni a szoftverfrissítések láthatóságát, konfigurálja ezeket a beállításokat az [eszköz korlátozásai](device-restrictions-ios.md#general)között.
     
      > [! Fontos  
      > A *kezdési időt* és a *befejezési időpontot* a 12-es értékre beállított szabályzat 0 óra, nem pedig 24 óra. Ez az eredmény nem korlátozza a korlátozást.  

5. Kattintson a**Létrehozás** **gombra** > a módosítások mentéséhez és a szabályzat létrehozásához.

A szabályzat létrejön, és megjelenik a szabályzatok listájában.

Az Intune támogatási csapatával kapcsolatos útmutatásért lásd az [Intune-ban felügyelt eszközökre vonatkozó szoftverfrissítések láthatóságának késleltetését](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753)ismertető témakört.

> [!NOTE]
> Az Apple mobileszköz-kezelése nem teszi lehetővé, hogy a készülékek számára kikényszerítse a frissítések adott időpontban történő telepítését.

## <a name="change-the-restricted-times-for-the-policy"></a>A korlátozott időtartamok módosítása a szabályzatban

1. A **Szoftverfrissítések** területen válassza **iOS-frissítési szabályzatok** lehetőséget.
2. Válasszon ki egy meglévő szabályzatot > **Tulajdonságok**.
3. Frissítse a korlátozás időpontjait:

    1. Válassza ki a hét napjait
    2. Válassza ki, hogy melyik időzóna szerint kívánja alkalmazni a szabályzatot
    3. Adja meg a feketelistás órák kezdő és záró idejét

    > [!NOTE]
    > Ha a **kezdési** és a **befejezési időpont** is 12am értékre van állítva, akkor az Intune nem korlátozza a frissítések telepítésének idejét. Ez azt jelenti, **hogy a frissítési telepítések** figyelmen kívül hagyása, és a frissítések telepítése bármikor megtörténik, ha az összes konfigurációt meg szeretné akadályozni.  

## <a name="assign-the-policy-to-users"></a>A szabályzat hozzárendelése a felhasználókhoz

A meglévő szabályzatokat csoportokhoz, felhasználókhoz vagy eszközökhöz rendelheti. Hozzárendelés után a szabályzatok alkalmazásra fognak kerülni.

1. A **Szoftverfrissítések** területen válassza **iOS-frissítési szabályzatok** lehetőséget.
2. Válasszon ki egy meglévő szabályzatot > **Hozzárendelések**. 
3. Válassza ki azokat az Azure Active Directory csoportokat, felhasználókat vagy eszközöket, amelyeknél alkalmazni vagy kizárni szeretné a szabályzatot.
4. Válassza a **Mentés** lehetőséget a szabályzat csoportok felé történő telepítéséhez.

A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználók által használt eszközök frissítési megfelelőségét. Ez a szabályzat a felhasználó nélküli eszközöket is támogatja.

## <a name="monitor-device-installation-failures"></a>Eszközök telepítési hibáinak figyelése
<!-- 1352223 -->
**A szoftverfrissítések** **telepítési hibái iOS-eszközökön** megjelenítik a frissítési szabályzat által megcélozott felügyelt iOS-eszközök listáját, frissítést próbáltak meg, és nem lehetett frissíteni. >  Minden eszköz mellett látható egy állapotleírás, amelyből kiderül, hogy az adott eszköz miért nem frissült automatikusan. A kifogástalan, naprakész eszközök nem jelennek meg a listában. A naprakész eszközökön telepítve van az a legújabb frissítés, amelyet az eszköz támogatni képes.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
