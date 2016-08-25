---
title: "A Windows kiadásfrissítési házirendjének beállításai | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8e911193075d2a621ef94f2917b2126501ea2100
ms.openlocfilehash: e468ff102b45bf0c23fd76d8d15c44978861ae8a


---

# A Windows kiadásfrissítési házirendjének beállításai a Microsoft Intune-ban
A Microsoft Intune **kiadásfrissítési házirendje** lehetővé teszi az alábbi Windows 10-verziók valamelyikét futtató eszközök újabb verzióra történő automatikus frissítését:
* Windows 10 asztali verzió
* Windows 10 Holographic

## Előkészületek
Az eszközök legújabb verzióra történő frissítésének megkezdése előtt szüksége lesz a következők valamelyikére:
* Termékkulcsra, amely érvényes a Windows új verziójának a házirend céljaként meghatározott összes eszközre történő telepítésére (a Windows 10 asztali verziója esetén).
* A Microsoft által kiadott licencfájlra, amely tartalmazza azokat a licencelési adatokat, amelyek szükségesek a Windows új verziójának a házirend céljaként meghatározott összes eszközre történő telepítéséhez (a Windows 10 Mobile és a Windows 10 Holographic verzió esetén).
* A célként meghatározott Windows 10 rendszerű eszközöknek regisztrálva kell lenniük a Microsoft Intune-ban.

## Kiadásfrissítési házirend beállításai

|Beállítás neve|Részletek|
|-|-|
|**Név**|Adja meg a kiadásfrissítési házirend nevét.|
|**Leírás**|Megadhatja a házirend leírását, hogy könnyebb legyen azonosítani az Intune-konzolon (nem kötelező).
|**Frissítés erre a kiadásra**|A legördülő listából válassza ki a Windows 10 asztali verziónak, a Windows 10 Holographic vagy a Windows 10 Mobile rendszernek azt a verzióját, amelyre a megcélzott eszközöket frissíteni szeretné.
|**Termékkulcs**|Adja meg a Microsofttól kapott, minden megcélzott Windows 10 asztali eszköz frissítéséhez használható termékkulcsot.<br>Miután létrehozta a termékkulcsot tartalmazó házirendet, a termékkulcsot már nem szerkesztheti. Ennek oka a kulcs biztonsági okokból történő elrejtése. Ha módosítani szeretné a termékkulcsot, a teljes kulcsot újra meg kell adnia.
|**Licencfájl**|Kattintson a **Tallózás** elemre, és válassza ki a Microsofttól kapott, a Windows Holographic vagy Windows 10 Mobile azon kiadásának licencadatait tartalmazó licencfájlt, amelyre a célzott eszközöket frissíteni szeretné.

### További információ
[Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


<!--HONumber=Jun16_HO4-->


