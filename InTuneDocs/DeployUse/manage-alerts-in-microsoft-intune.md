---
# required metadata

title: Riasztások kezelése | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 74dc4ce4-21da-4f40-a07f-3eea34561eee

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Riasztások kezelése a Microsoft Intune-ban
Az Intune felügyeleti konzol **Riasztások** munkaterületével felmérheti a szervezetben lévő eszközök általános állapotát, és azonosíthatja a problémákat.

#### Aktív riasztások megtekintése

1.  Az Intune felügyeleti konzolon tegye a következők valamelyikét:

    -   **A riasztások általános információinak megjelenítéséhez**, a három legfőbb riasztást és az aktív riasztások számát is beleértve, kattintson a **Rendszer – áttekintés** lehetőségre. A riasztásokban lévő hivatkozásokra kattintva részletesebb információkat kaphat.

    -   **A riasztások összefoglaló adatainak megjelenítéséhez** kattintson a **Riasztások &gt; áttekintés** lehetőségre. A **Riasztások – áttekintés** lapon a **Riasztások típus szerint** terület tartalmazza a riasztások összefoglaló adatait. A kritikus riasztások jelennek meg legfelül. A riasztásokban lévő hivatkozásokra kattintva részletesebb információkat kaphat.

        > [!NOTE]
        > Bizonyos esetekben egy riasztási típus egynél többször is megjelenhet a **Riasztások típus szerint** listában.
        > 
        > Például a Logikai lemez – Szabad terület riasztási típusból a következő példányok jelenhetnek meg a listában egyszerre:
        > 
        > -   3 Logikai lemez – Szabad terület
        > -   2 Logikai lemez – Szabad terület
        > 
        > Ez akkor fordul elő, ha különböző operációs rendszert futtató eszközökhöz generál a rendszer ugyanolyan típusú riasztást. A példában a Logikai lemez – Szabad terület riasztási típus első példányát („3 Logikai lemez – Szabad terület”) lehet, hogy Windows® 7 rendszert futtató számítógépek generálták. A Logikai lemez – Szabad terület riasztási típus második példánya pedig lehet, hogy Windows Vista® rendszert futtató számítógépek generálták.

    -   **Az összes aktív riasztás megjelenítéséhez** kattintson a **Riasztások &gt; Minden riasztás** lehetőségre. A **Riasztások** lap a következő oszlopokkal jeleníti meg az összes aktív riasztás listáját:

        1.  **Név** – Annak a riasztástípusnak a neve, amely a riasztást előidézte.

        2.  **Forrás** – Hivatkozás a riasztás forrására. Ha a riasztási típus megjelenítési küszöbértéke az **Összes megjelenítése** értékre van állítva, akkor ez a hivatkozás egyetlen eszközt jelenít meg. Ha a riasztási típus megjelenítési küszöbértéke egy adott értékre van állítva, akkor a hivatkozás a riasztásban érintett összes eszköz listáját megjeleníti.

        3.  **Utolsó frissítés** – A riasztás legutóbbi módosításának időpontja. Ha egy riasztás le van zárva, akkor a lezárás időpontja jelenik meg.

        4.  **Súlyosság** – A riasztás súlyosságát jelzi.

## Hirdetőtábla-riasztások megtekintése
A hirdetőtábla-riasztások fontos szolgáltatási közleményeket nyújtanak, például hamarosan lezajló szolgáltatásfrissítésről, karbantartásról vagy szolgáltatáskimaradásról tájékoztatnak. Az alábbi utasításokat követve áttekintheti és kezelheti a hirdetőtábla-riasztásokat.

#### Hirdetőtábla-riasztások megtekintése és kezelése

1.  Az Intune felügyeleti konzolon kattintson a **Rendszer – áttekintés** lehetőségre..

2.  Ha vannak fontos szolgáltatási közlemények, akkor azok az **Üzenőfal** területen láthatók.

3.  Ha egy üzenőfal-riasztást szeretne CSV- vagy HTML-fájlba exportálni, az Intune felügyeleti konzolon kattintson a **Riasztások &gt; Minden riasztás &gt; Megjegyzések** lehetőségre. Jelöljön ki egy értesítést, kattintson az exportálás ikonjára, és kövesse az utasításokat.

## Intune-szolgáltatások állapotának áttekintése
A **Rendszer – áttekintés** munkaterületen áttekintheti az Endpoint Protection, a frissítések, az ügynökök, a házirendek és a szoftverek állapotadatait. Ezekkel az információkkal felmérheti a problémákat, és priorizálhatja azokat, amelyek azonnali figyelmet igényelnek. Egy, a **Szolgáltatás állapota** összesítőlapra mutató hivatkozás is látható a hibaüzenetekben a rendszer üzemkimaradása esetén. A **Szolgáltatás állapota** összesítés részletesebb információt nyújt az egyes helyeken fellépő problémákról, és mindig megjeleníti az utolsó frissítés időpontját.

#### Az előfizetés állapotának megtekintése

1.  Az Intune felügyeleti konzolon kattintson a **Rendszer – áttekintés** lehetőségre..

2.  A **Rendszer állapota** területen láthatja a Microsoft Intune különféle összetevőinek állapotát. Sok elem hivatkozásokat is tartalmaz, melyekre kattintva további információkat kaphat. Például az **Endpoint Protection** alatt a példányok számára kattintva megjelenítheti az **Endpoint Protection** munkaterületet, rajta az észlelt kártevők listájával. Az eszközök számára kattintva pedig megjelenítheti a **Csoportok** munkaterületet, rajta azoknak az eszközöknek a listájával, amelyeken kártevőt észlelt a rendszer.

## Riasztások bezárása és újraaktiválása
Az Intune-riasztások addig maradnak aktívak, amíg az alábbiak egyike meg nem történik:

-   A riasztást generáló probléma megoldódik.

-   A riasztást valaki manuálisan lezárja.

-   5 nap eltelik a riasztás generálása után. A riasztás 45 nap után lejár, és automatikusan lezáródik.

A lezártnak jelölt riasztásokat a rendszer 90 nap után véglegesen törli.

#### Riasztás lezárása manuálisan

1.  Az Intune felügyeleti konzolon tegye a következők valamelyikét:

    1.  **Egy riasztásnak a Riasztások listából való lezárásához** kattintson a **Riasztások &gt; Minden riasztás** elemre. Jelölje ki a kívánt riasztást, és kattintson a **Riasztás bezárása** lehetőségre..

    2.  **Egy adott eszközhöz tartozó riasztás lezárásához** kattintson a **Csoportok &gt; Minden eszköz** lehetőségre. Jelöljön ki egy eszközt, és kattintson a **Tulajdonságok megjelenítése** lehetőségre. Ezután a **Riasztások** lapon jelölje ki a kívánt riasztást, és kattintson a **Riasztás bezárása** lehetőségre..

    3.  **Üzenőfal-riasztás lezárásához** kattintson a **Rendszer – áttekintés** lehetőségre. Kattintson az üzenőfal-riasztás melletti **X** gombra.

#### Lezárt riasztások megtekintése és újraaktiválása

1.  Az Intune felügyeleti konzolon kattintson a **Riasztások &gt; Minden riasztás** lehetőségre..

2.  A **Szűrők** listában válassza a **Lezárva** lehetőséget..

    Ekkor megjelennek a riasztások adatai a felügyeleti lista ablaktábláján. A kijelölt riasztás részletes adatait az előnézeti ablaktáblában láthatja.

3.  A kijelölt riasztás újraaktiválásához kattintson a **Riasztás újraaktiválása** lehetőségre..

### További információ
[Értesítések a Microsoft Intune riasztásaival](get-notified-by-microsoft-intune-alerts.md)



<!--HONumber=May16_HO1-->


