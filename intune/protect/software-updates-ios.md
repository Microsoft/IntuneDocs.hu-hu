---
title: Az iOS-szoftverfrissítési szabályzatok konfigurálása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: A Microsoft Intune-ben hozzon létre vagy adjon hozzá egy konfigurációs házirendet, amely korlátozza, hogy a szoftverfrissítések automatikusan telepítsenek iOS-eszközökre. Megadhatja azokat a dátumokat és időpontokat, amelyeknél nem szeretné, hogy települjenek a frissítések. Ezt a szabályzatot csoportokhoz, felhasználókhoz és eszközökhöz is hozzárendelheti, és ellenőrizheti az esetleges telepítési hibákat is vele.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f9750603d19d9b19697c7d2660351c4586432f6
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73984198"
---
# <a name="add-ios-software-update-policies-in-intune"></a>IOS-szoftverfrissítési szabályzatok hozzáadása az Intune-ban

A-frissítési szabályzatokkal kikényszerítheti a legújabb elérhető rendszerfrissítések automatikus telepítését a felügyelt iOS-eszközökön. A szabályzat beállításakor megadhatja azokat a napokat és időpontokat, amikor nem szeretné, hogy az eszközök frissítéseket telepítsenek.

Ez a funkció az alábbiakra vonatkozik:

- iOS 10,3 és újabb verziók (felügyelt)

Az eszköz körülbelül 8 óránként jelentkezik be az Intune-ba. Ha van elérhető frissítés, az eszköz letölti és telepíti, kivéve a korlátozott időpontokban. Bár a frissítési folyamat általában nem tartalmaz felhasználói beavatkozást, ha az eszköz rendelkezik PIN-kóddal, a felhasználónak meg kell adnia azt a szoftverfrissítés elindításához. Ez az iOS 10,3-es és újabb verzióira vonatkozik. A szabályzat nem akadályozza meg, hogy a felhasználó manuálisan frissítse az operációs rendszert.

## <a name="configure-the-policy"></a>A szabályzat konfigurálása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza a **Szoftverfrissítések** > **iOS-frissítési szabályzatok** > **Létrehozás** lehetőséget.
3. Az **alapvető beállítások** lapon adja meg a szabályzat nevét, adjon meg egy leírást (nem kötelező), majd kattintson a **tovább**gombra.

   ![Alapbeállítások lap](./media/software-updates-ios/basics-tab.png) 

4. A **házirend-beállítások frissítése** lapon meghatározhatja a korlátozott időkeretet, ha a frissítések nincsenek kényszerítve telepítve.  
   - Az egynapos blokkok nem támogatottak, és előfordulhat, hogy nem működnek. Tegyük fel például, hogy nem állít be egy szabályzatot 8 PM *kezdő időponttal* , és 6 órakor *befejező* időpontot.
   - Egy olyan szabályzat, amely 12 órakor kezdődik, és 12 ÓRAKOR ér véget, a kiértékelés 0 óra, nem 24 óra. Ez a konfiguráció nem eredményez korlátozást.

   A korlátozott időkeret beállításakor adja meg a következő adatokat:

   - **Nap**: válassza ki a hét azon napját, amikor a frissítések nincsenek telepítve. Például a hétfő, a szerda és a péntek beállítás megadásával megakadályozhatja, hogy a frissítések ezekben a napokban legyenek telepítve.
   - **Időzóna**: válasszon időzónát.
   - **Kezdési idő**: válassza ki a korlátozott időtartam kezdő időpontját. Adja meg például az 5, hogy a frissítések ne legyenek telepítve 5 ÓRAKOR.
   - **Befejezés időpontja**: válassza ki a korlátozott időkeret befejezési időpontját. Adja meg például a következőt: 1, így a frissítések telepíthetők a-től kezdődően.
  
   > [!IMPORTANT]  
   > A *kezdési időt* és a *befejezési időpontot* a 12-es értékre beállított szabályzat 0 óra, nem pedig 24 óra. Ez az eredmény nem korlátozza a korlátozást.  
    
   A felügyelt iOS-eszközökön megadott idő elteltével a szoftverfrissítések láthatóságának késleltetéséhez konfigurálja ezeket a beállításokat az [eszközök korlátozásai](../configuration/device-restrictions-ios.md#general)között. A szoftverfrissítési házirendek felülbírálják az eszközre vonatkozó korlátozásokat. Ha a szoftverfrissítések láthatóságának késleltetése érdekében a szoftverfrissítési házirendet és a korlátozást is beállítja, az eszköz a szabályzat által megadott szoftverfrissítéseket kényszeríti. A korlátozás arra az esetre vonatkozik, ha a felhasználók nem látják saját maguknak az eszköz frissítését, és a frissítést az iOS-frissítési szabályzat által meghatározott első alkalommal küldi el a rendszer.

   A *frissítési szabályzat beállításainak*konfigurálása után kattintson a **Tovább gombra**. 

5. A **hatókör címkék** lapon válassza a **hatókör címkék** kiválasztása lehetőséget a *címkék kiválasztása* ablaktábla megnyitásához, ha alkalmazni szeretné őket a frissítési házirendre.
   
   - A **címkék kiválasztása** panelen válasszon ki egy vagy több címkét, majd kattintson a **kiválasztás** elemre, és adja hozzá őket a Szabályzathoz, és térjen vissza a *hatókör címkék* panelre.  

   Ha elkészült, kattintson a **tovább** gombra a *hozzárendelések*folytatásához.

6. A **hozzárendelések** lapon válassza a **+ csoportok kiválasztása lehetőséget** , majd rendelje hozzá a frissítési szabályzatot egy vagy több csoporthoz. **Válassza a + csoportok kiválasztása lehetőséget** a hozzárendelés finomhangolásához. Ha elkészült **, kattintson a Tovább gombra** a folytatáshoz. 

   A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználók által használt eszközök frissítési megfelelőségét. Ez a szabályzat a felhasználó nélküli eszközöket is támogatja.

7. A **felülvizsgálat + létrehozás** lapon tekintse át a beállításokat, majd válassza a **Létrehozás** lehetőséget, amikor készen áll az iOS-frissítési szabályzat mentéséhez. Az új szabályzat az iOS-es frissítési szabályzatok listájában jelenik meg.


Az Intune támogatási csapatával kapcsolatos útmutatásért lásd az [Intune-ban felügyelt eszközökre vonatkozó szoftverfrissítések láthatóságának késleltetését](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753)ismertető témakört.

> [!NOTE]
> Az Apple mobileszköz-kezelése nem teszi lehetővé, hogy a készülékek számára kikényszerítse a frissítések adott időpontban történő telepítését.

## <a name="edit-a-policy"></a>Szabályzat szerkesztése
Szerkeszthet egy meglévő szabályzatot, beleértve a korlátozott időpontok módosítását is:

1. A **szoftverfrissítések**területen válassza az **iOS-re vonatkozó szabályzatok frissítése** lehetőséget, majd válassza ki a szerkeszteni kívánt szabályzatot.

2. A szabályzatok **tulajdonságainak**megtekintése közben válassza a **Szerkesztés** lehetőséget a módosítani kívánt szabályzat oldalhoz.  
   ![a rendőri](./media/software-updates-ios/edit-policy.png)   

3. A módosítás bevezetése után válassza az **Áttekintés + mentés** > **Mentés** lehetőséget a módosítások mentéséhez, és térjen vissza a házirendek *tulajdonságaihoz*.  
 
> [!NOTE]
> Ha a **kezdési** és a **befejezési időpont** is 12 értékre van állítva, akkor az Intune nem keres korlátozásokat a frissítések telepítésének idejére. Ez azt jelenti, **hogy a frissítési telepítések** figyelmen kívül hagyása, és a frissítések telepítése bármikor megtörténik, ha az összes konfigurációt meg szeretné akadályozni.  


## <a name="monitor-device-installation-failures"></a>Eszközök telepítési hibáinak figyelése
<!-- 1352223 -->
A **szoftverfrissítések** > az **iOS-eszközök telepítési hibái** megjelenítik a frissítési szabályzat által megcélozott felügyelt iOS-eszközök listáját, frissítést próbáltak meg, és nem lehetett frissíteni. Minden eszköz mellett látható egy állapotleírás, amelyből kiderül, hogy az adott eszköz miért nem frissült automatikusan. A kifogástalan, naprakész eszközök nem jelennek meg a listában. A naprakész eszközökön telepítve van az a legújabb frissítés, amelyet az eszköz támogatni képes.

## <a name="next-steps"></a>További lépések

[Az állapot figyelése](../configuration/device-profile-monitor.md).
