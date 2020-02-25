---
title: Az iOS/iPadOS szoftverfrissítési szabályzatok konfigurálása a Microsoft Intuneban – Azure | Microsoft Docs
description: Microsoft Intuneban hozzon létre vagy adjon hozzá egy konfigurációs szabályzatot, amely korlátozza, hogy a szoftverfrissítések automatikus telepítése az iOS-/iPadOS-eszközökön történjen. Megadhatja azokat a dátumokat és időpontokat, amelyeknél nem szeretné, hogy települjenek a frissítések. Ezt a szabályzatot csoportokhoz, felhasználókhoz és eszközökhöz is hozzárendelheti, és ellenőrizheti az esetleges telepítési hibákat is vele.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576152"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>IOS/iPadOS-szoftverfrissítési szabályzatok hozzáadása az Intune-ban

A szoftverfrissítési házirendek lehetővé teszik a felügyelt iOS-/iPadOS-eszközök kikényszerítését az operációs rendszer frissítéseinek automatikus telepítésére. A felügyelt eszközök az Apple Business Manager vagy az Apple School Manager használatával regisztrálva vannak. A frissítések telepítésére vonatkozó házirend konfigurálásakor a következőket teheti:

- Válassza az elérhető *legújabb frissítés* telepítését, vagy válassza a frissítés verziószámának korábbi frissítését, ha nem szeretné telepíteni a legújabb frissítést. Ha úgy dönt, hogy egy régebbi frissítést telepít, a szoftverfrissítések láthatóságának korlátozásához be kell állítania egy eszköz-konfigurációs házirendet is.
- Adja meg azt az ütemtervet, amely meghatározza, hogy a rendszer mikor telepítse a frissítést. Az ütemtervek olyan egyszerűek, mint a frissítések telepítése, amikor az eszköz bejelentkezik, vagy olyan dátum-és időtartományokat hoz létre, amelyek során a frissítések telepíthetők vagy le vannak tiltva.

Ez a funkció az alábbiakra vonatkozik:

- iOS 10,3 és újabb verziók (felügyelt)

Alapértelmezés szerint az eszközök 8 óránként bejelentkezni az Intune-ba. Ha egy frissítés egy frissítési házirenden keresztül érhető el, az eszköz letölti a frissítést. Az eszköz ezután telepíti a frissítést a következő bejelentkezéskor az ütemezett konfiguráción belül. Bár a frissítési folyamat általában nem tartalmaz felhasználói beavatkozást, ha az eszköz rendelkezik PIN-kóddal, a felhasználónak meg kell adnia azt a szoftverfrissítés elindításához. A profilok nem akadályozzák meg, hogy a felhasználók manuálisan frissítse az operációs rendszert. A felhasználók nem tudják manuálisan frissíteni az operációs rendszert egy eszköz-konfigurációs házirenddel a szoftverfrissítések láthatóságának korlátozására.

## <a name="configure-the-policy"></a>A szabályzat konfigurálása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **frissítési szabályzatok iOS/iPadOS > a** **profil létrehozása**lehetőséget.
3. Az **alapvető beállítások** lapon adja meg a szabályzat nevét, adjon meg egy leírást (nem kötelező), majd kattintson a **tovább**gombra.

   ![Alapbeállítások lap](./media/software-updates-ios/basics-tab.png)

4. A **házirend-beállítások frissítése** lapon konfigurálja a következőket:

   1. **Válassza ki a telepítendő verziót**. A következő lehetőségek közül választhat:

      - *Legújabb frissítés*: telepíti az iOS/iPadOS legutóbb kiadott frissítését.
      - A legördülő listából elérhető bármely korábbi verzió. Ha egy korábbi verziót választ, a szoftverfrissítések láthatóságának késleltetéséhez telepítenie kell egy eszköz-konfigurációs házirendet is.

   2. **Ütemterv típusa**: konfigurálja a szabályzat ütemtervét:

      - *Frissítés a következő bejelentkezéskor*: a frissítés telepítése az eszközön, amikor legközelebb bejelentkezik az Intune-ba. Ez a legegyszerűbb lehetőség, és nincsenek további konfigurációk.
      - *Frissítés az ütemezett idő alatt*: beállíthatja, hogy a rendszer mikor telepítse a frissítést a bejelentkezés után.
      - *Frissítés az ütemezett időkereten kívül*: egy vagy több olyan időszakot konfigurálhat, amely alatt a frissítések nem települnek a bejelentkezés után.

   3. **Heti ütemterv**: Ha a *következő bejelentkezéskor a frissítéstől*eltérő típusú ütemtervet választ, konfigurálja a következő beállításokat:

      ![Példa az ütemezett időpontra való frissítés kiválasztására](./media/software-updates-ios/scheduled-time.png)

      - **Időzóna**: válasszon időzónát.
      - **Időablak**: adjon meg egy vagy több olyan időblokkot, amely korlátozza a frissítések telepítésének idejét. A következő beállítások hatása a kiválasztott ütemtervtől függ. A kezdő és a záró nap használatával az egynapos blokkok támogatottak. A lehetőségek a következők:

        - **Kezdés napja**: válassza ki azt a napot, amelyen az ütemezett időszak elindul.
        - **Kezdési idő**: válassza ki az időpontot, amikor az ütemezett időszak megkezdődik. Ha például kijelöli az 5 és az ütemezési típust az *ütemezett idő alatt*, a frissítések megkezdésének ideje 5 lesz. Ha az ütemezési típust az *ütemezett időkereten kívül*választotta, akkor a frissítések nem telepíthetők egy adott időszak elején.
        - **Befejezés napja**: válassza ki az időpontot, amikor az ütemezett időszak véget ér.
        - **Befejezés időpontja**: válassza ki azt az időpontot, amikor a Schedule ablak leáll. Ha például a (1) lehetőséget választja, és a frissítés ütemezési típusa *ütemezett idő alatt*van, akkor a frissítések már nem telepíthetők. Ha az ütemezési típust az *ütemezett időkereten kívüli*időpontra választotta, akkor a frissítések telepítésének időszaka 1 lesz.

       Ha nem állítja be az indítási vagy befejezési időpontot, a konfiguráció nem korlátozza a módosításokat, és a frissítések bármikor telepíthetők.  

       > [!NOTE]
       > A felügyelt iOS-/iPadOS-eszközökön a szoftverfrissítések láthatóságának késleltetéséhez konfigurálja ezeket a beállításokat az [eszköz korlátozásai](../configuration/device-restrictions-ios.md#general)között. A szoftverfrissítési házirendek felülbírálják az eszközre vonatkozó korlátozásokat. Ha a szoftverfrissítések láthatóságának késleltetése érdekében a szoftverfrissítési házirendet és a korlátozást is beállítja, az eszköz a szabályzat által megadott szoftverfrissítéseket kényszeríti. A korlátozás arra az esetre vonatkozik, hogy a felhasználók nem látják saját maguknak az eszköz frissítését, és a frissítés az iOS-frissítési szabályzat által meghatározott módon van leküldve.

   A *frissítési szabályzat beállításainak*konfigurálása után kattintson a **Tovább gombra**.

5. A **hatókör címkék** lapon válassza a **hatókör címkék** kiválasztása lehetőséget a *címkék kiválasztása* ablaktábla megnyitásához, ha alkalmazni szeretné őket a frissítési házirendre.

   - A **címkék kiválasztása** panelen válasszon ki egy vagy több címkét, majd kattintson a **kiválasztás** elemre, és adja hozzá őket a Szabályzathoz, és térjen vissza a *hatókör címkék* panelre.

   Ha elkészült, kattintson a **tovább** gombra a *hozzárendelések*folytatásához.

6. A **hozzárendelések** lapon válassza a **+ csoportok kiválasztása lehetőséget** , majd rendelje hozzá a frissítési szabályzatot egy vagy több csoporthoz. **Válassza a + csoportok kiválasztása lehetőséget** a hozzárendelés finomhangolásához. Ha elkészült **, kattintson a Tovább gombra** a folytatáshoz.

   A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználók által használt eszközök frissítési megfelelőségét. Ez a szabályzat a felhasználó nélküli eszközöket is támogatja.

7. A **felülvizsgálat + létrehozás** lapon tekintse át a beállításokat, majd válassza a **Létrehozás** lehetőséget, amikor készen áll az iOS/iPadOS frissítési szabályzat mentéséhez. Az új szabályzat az iOS/iPadOS frissítési szabályzatok listájában jelenik meg.

Az Intune támogatási csapatával kapcsolatos útmutatásért lásd az [Intune-ban felügyelt eszközökre vonatkozó szoftverfrissítések láthatóságának késleltetését](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753)ismertető témakört.

> [!NOTE]
> Az Apple mobileszköz-kezelése nem teszi lehetővé, hogy a készülékek számára kikényszerítse a frissítések adott időpontban történő telepítését. Az Intune szoftverfrissítési házirendjei nem használhatók az operációs rendszer verziójának az eszközön való visszaminősítésére.

## <a name="edit-a-policy"></a>Szabályzat szerkesztése

Szerkeszthet egy meglévő szabályzatot, beleértve a korlátozott időpontok módosítását is:

1. Válassza az **eszközök** > **frissítési szabályzatok iOS rendszerhez**lehetőséget. Válassza ki a szerkeszteni kívánt szabályzatot.

2. A szabályzatok **tulajdonságainak**megtekintése közben válassza a **Szerkesztés** lehetőséget a módosítani kívánt szabályzat oldalhoz.

   ![Szabályzat szerkesztése](./media/software-updates-ios/edit-policy.png)

3. A módosítás bevezetése után válassza az **Áttekintés + mentés** > **Mentés** lehetőséget a módosítások mentéséhez, és térjen vissza a házirendek *tulajdonságaihoz*.

> [!NOTE]
> Ha a **kezdési** és a **befejezési időpont** is 12 értékre van állítva, akkor az Intune nem keres korlátozásokat a frissítések telepítésének idejére. Ez azt jelenti, **hogy a frissítési telepítések** figyelmen kívül hagyása, és a frissítések telepítése bármikor megtörténik, ha az összes konfigurációt meg szeretné akadályozni.

## <a name="monitor-device-installation-failures"></a>Eszközök telepítési hibáinak figyelése

<!-- 1352223 -->
A **szoftverfrissítések** > az **iOS-eszközök telepítési hibái** megjelenítik a frissítési szabályzat által megcélozott felügyelt iOS-/iPadOS-eszközök listáját, a frissítés kísérletét, és nem sikerült frissíteni. Minden eszköz mellett látható egy állapotleírás, amelyből kiderül, hogy az adott eszköz miért nem frissült automatikusan. A kifogástalan, naprakész eszközök nem jelennek meg a listában. A naprakész eszközökön telepítve van az a legújabb frissítés, amelyet az eszköz támogatni képes.

## <a name="next-steps"></a>További lépések

[Az állapot figyelése](../configuration/device-profile-monitor.md).
