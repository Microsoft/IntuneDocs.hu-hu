---
title: "Eszközök kategorizálása eszközcsoport-leképezéssel | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
ms.sourcegitcommit: bb30b8e61a768b15e2f09993f4dceae8f4e1bd8a
ms.openlocfilehash: 55f811153bf37048a4fcdfc6da301a5f181700c3


---

# Eszközök kategorizálása eszközcsoport-leképezéssel a Microsoft Intune-ban
A Microsoft Intune **eszközcsoport-leképezés** funkciója segítségével különböző Ön által meghatározott kategóriákba csoportosíthatja az eszközöket, megkönnyítve ezzel a felügyeletüket. 

Az eszközcsoport-leképezés funkció a következő munkafolyamatot használja:
1. Ön létrehozza a használni kívánt kategóriákhoz tartozó Intune-eszközcsoportokat.
2. Beállítja az eszközcsoport-leképezési szabályokat, amelyek segítségével a rendszer összepárosítja a kiválasztott kategóriákat a létrehozott eszközcsoportokkal.
3. Amikor a végfelhasználók regisztrálják eszközüket, csak az Ön által meghatározott kategóriák közül választhatnak. A kategória kiválasztását követően a rendszer automatikusan az Ön által létrehozott megfelelő eszközcsoporthoz adja a kérdéses eszközt.
4. Ezt követően az eszközcsoportok használatával leegyszerűsítheti a szabályzatok és az alkalmazások központi telepítését.

Kategóriák lehetnek például:
* Személyes eszközök
* Pénztári eszközök
* Bemutatóeszközök
* Értékesítés
* Könyvelés
* Manager

A kategóriákat tetszőlegesen választhatja meg.

## Az eszközcsoport-leképezések konfigurálása
1. Minden használni kívánt eszközcsoporthoz hozzon létre egy Intune-eszközcsoportot. A csoportok létrehozásával kapcsolatban további információt a [Csoportok használata felhasználók és eszközök kezelésére a Microsoft Intune-nal](use-groups-to-manage-users-and-devices-with-microsoft-intune.md) című témakörben találhat.
2. A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com) válassza a **Felügyelet** elemet.
3. A **Felügyelet** munkaterületen bontsa ki a **Mobileszköz-kezelés** csomópontot, majd válassza az **Eszközcsoport-leképezés** elemet.
4. Az **Eszközcsoport-leképezés** oldalon engedélyezze az eszközcsoport-leképezés funkciót.
5. Új leképezési szabály felvételéhez válassza a **Hozzáadás** elemet.
6. Az **Eszközcsoport-leképezési szabály hozzáadása** párbeszédpanelen adja meg a létrehozni kívánt kategória nevét, majd a legördülő listából válassza ki azt az eszközgyűjteményt, amelyhez párosítani szeretné ezt a kategóriát. Ha elkészült, válassza a **Hozzáadás** gombot.
7. Ha befejezte a kategóriák és a csoportok hozzáadását, válassza a **Mentés** gombot.

Ezt követően amikor a felhasználók regisztrálják eszközüket, meg fog jelenni számukra az Ön által beállított kategóriák listája. A kategória kiválasztását és a regisztráció befejezését követően a rendszer a kiválasztott kategóriának megfelelő eszközcsoporthoz adja az eszközüket.

### További információ
[Csoportok használata felhasználók és eszközök kezelésére a Microsoft Intune-nal](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=Jul16_HO2-->


