---
title: "Riasztások által biztosított értesítések | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 396ea714-0433-4bd5-a934-8d0b477f28e4
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e929a95d95b71e22d46e124f1a423af7046b0539
ms.openlocfilehash: f1dd166b7b1278003ac8785b8be07c29396dfe8c


---

# Értesítések a Microsoft Intune riasztásaival
A riasztásokkal nyomon követheti, mi történik a Microsoft Intune-ban.

A riasztások többek között a következő eseményekről kaphat értesítést:

-   Az Exchange Connectorral kapcsolatos problémákról, amelyek a mobileszköz-felügyeletet is érintik

-   Arról, ha a rendszer kártevőt talál egy számítógépen

-   Arról, ha a rendszer ütközést észlel két Intune-házirend között


## A riasztások működése
A riasztások generálása a **riasztástípusok** alapján (az Intune beépített, előre konfigurált szabályai alapján) történik. Például **A felhőbeli szabad tárkapacitás 10% vagy kevesebb** típusú riasztás akkor figyelmeztet, ha hamarosan elfogy az alkalmazások tárolására szolgáló terület a felhőben. Az egyes riasztástípusok engedélyezhetők, letilthatók, és konfigurálhatók a hozzájuk kapcsolódó tulajdonságok. A fenti riasztástípusnál például a következőket konfigurálhatja:

-   **Állapot:** megadja, hogy a riasztástípus engedélyezve van-e, vagy le van tiltva.

-   **Súlyosság:** megadja, hogy mennyire súlyos a riasztás.


|Severity|Részletek|
|--------|-------|
    |![Kritikus riasztás](../media/Critical-Alert.jpg)|Olyan súlyos problémát jelöl, amelyet mielőbb ki kell vizsgálni – például ha a rendszer kártevőt észlel valamelyik számítógépen.|
    |![Figyelmeztető riasztás](../media/Warning-Alert.jpg)|Olyan problémát jelöl, amely egyelőre még nem súlyos, de súlyossá válhat, ha nem foglalkozik vele – ilyenek például a telepítésre váró biztonsági frissítések.|
    |![Információs riasztás](../media/Informational-Alert.jpg)|Olyan információt jelez, amely az üzemeltetés szempontjából nem kritikus – ilyen például, ha elérhető válik az Exchange Connector újabb verziója.|

Más riasztástípusok ettől eltérő konfigurációs elemeket is tartalmazhatnak, például hogy az eszközök hány százalékát kell érintenie a problémának ahhoz, hogy a riasztás létrejöjjön.

**Ha egy riasztástípus megadott feltétele teljesül, a rendszer létrehozza és megjeleníti a riasztást az Intune felügyeleti konzolon.**

Emellett az is beállítható, hogy az Intune e-mailben értesítse arról, ha riasztás jön létre.

## Riasztások konfigurálása
A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com) kattintson a **Felügyelet** &gt; **Riasztások és értesítések** elemre, majd válasszon a következő konfigurációs feladatok közül:

|Feladat|Leírás|
|--------|---------------|
|**Riasztástípusok**|Válassza ki a konfigurálni kívánt riasztástípust, majd tegye a következők valamelyikét:<br /><br />Válassza a **Konfigurálás** elemet. A **Riasztástípus beállítása** párbeszédpanelen adja meg a kívánt beállításokat, majd kattintson az **OK** gombra.<br /><br />**Engedélyezze** vagy **tiltsa le** a riasztást.<br /><br />Bontsa ki a **Riasztástípusok** csomópontot, majd válassza ki azt a kategóriát, amelynek a riasztástípusait meg szeretné tekinteni.|
|**Címzettek**|Kattintson a **Hozzáadás** gombra, majd adja meg az új e-mail-címet, amelyen e-mail értesítéseket szeretne fogadni.<br /><br />A meglévő címzetteket **szerkesztheti** és **törölheti** is.<br /><br />Ha értesítést szeretne kapni, a kívánt e-mail címet az **Értesítési szabályok** területen is fel kell vennie címzettként.|
|**Értesítési szabályok**|Az e-mail riasztások címzettjeit meghatározó szabályok konfigurálására szolgál. A következő lehetőségek közül választhat:<br /><br />**Meglévő szabály választása** – Válasszon egy szabályt, majd kattintson a **Címzettek kiválasztása** elemre. Ezután kiválaszthatja az összes címzettet, aki e-mailt kap, ha létrejön egy riasztás, amely megfelel ennek a szabálynak.<br /><br />**Új szabály létrehozása** – adja meg a szabály nevét, válassza ki a szabályokra érvényes riasztási kategóriákat és riasztási súlyosságot, válassza ki azon eszközcsoportokat, amelyekre a szabály érvényes, és válassza ki azon felhasználókat, akik e-mailt kapnak riasztás esetén.<br /><br />A meglévő szabályokat **engedélyezheti**, **letilthatja**, **szerkesztheti**és **törölheti** is.|

## A riasztások kezelése
A következő beállításokkal kezelheti a riasztásokat az Intune felügyeleti konzolról.

|Beállítás|Leírás|
|----------|---------------|
|**Aktív riasztások megtekintése**|Válasszon a következő lehetőségek közül:<br /><br />**A riasztás összefoglalásának megtekintése** – Az **Irányítópult** munkaterületen a legfontosabb hibák a Riasztások panelen jelennek meg. További részletes információk megjelenítéséhez kattintson az ablaktáblára.<br /><br />Emellett az egyes riasztások összefoglalását a **Riasztások** munkaterület **Áttekintés** lapján tekintheti meg.<br /><br />**Az összes riasztás megtekintése** – A **Riasztások** munkaterületen kattintson a **Minden riasztás** elemre.|
|**Megjegyzések megtekintése**|Válasszon a következő lehetőségek közül:<br /><br />Az **Irányítópult** munkaterületen kattintson a **Megjegyzések** elemre.<br /><br />A **Riasztások** munkaterületen válassza a **Minden riasztás** &gt; **Értesítések** elemet.|
|**Riasztás bezárása**|A riasztások listájában válassza ki a bezárni kívánt riasztást, majd kattintson a **Riasztás bezárása** elemre.<br /><br />A bezárt riasztások 90 nap után véglegesen törlődnek.|
|**Bezárt riasztás újraaktiválása**|A riasztáslistában válassza a **Szűrők** legördülő lista **Bezárt** elemét.<br /><br />A bezárt riasztások listájában jelölje ki az újraaktiválni kívánt riasztást, majd kattintson a **Riasztás újraaktiválása** elemre.|
Az Intune riasztásainak aktív állapota a következők esetén szűnik meg:

-   Ha a riasztást generáló probléma megoldódik.

-   Ha a riasztást manuálisan lezárja.

-   Ha 45 nap eltelt a riasztás generálása óta.

> [!TIP]
> Ha ugyanazt a riasztást különböző operációs rendszerű eszközök is kiváltják, elképzelhető, hogy több verzió jelenik meg ugyanabból a riasztásból a riasztáslistában.

### További információ
[Figyelés és jelentéskészítés a Microsoft Intune-ban](monitoring-and-reports-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


