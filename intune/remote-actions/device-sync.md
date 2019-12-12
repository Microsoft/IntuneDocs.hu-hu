---
title: Eszközök szinkronizálása a Microsoft Intuneokkal – Azure | Microsoft Docs
description: A Microsoft Intune-ban regisztrált vagy az általa kezelt eszközök szinkronizálásával az eszközök beolvashatják a legfrissebb szabályzatokat és műveleteket. Az Azure Portallal való szinkronizálás lépései és az újrapróbálható hibakódok.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1001a7a3fde9c203fdad3d146ace57736ae7128d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713450"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Az eszközök szinkronizálása az Intune-nal a legfrissebb szabályzatok és műveletek beolvasásához


A **Szinkronizálás** eszközművelet kikényszeríti a választott eszköz azonnali bejelentkezését az Intune-nál. Bejelentkezéskor az eszköz azonnal fogadja az összes hozzárendelt, függőben lévő műveletet vagy szabályzatot. Ez a funkció segíthet a vonatkozó szabályzatok azonnali ellenőrzésében és a hibák elhárításában anélkül, hogy ki kellene várni a következő ütemezett bejelentkezést.

## <a name="supported-platforms"></a>Támogatott platformok

- Windows
- Windows Phone
- iOS
- macOS
- Android:

## <a name="sync-a-device"></a>Eszköz szinkronizálása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431). 
3. Válassza az **Eszközök** > **Minden eszköz** lehetőséget.
4. A felügyelt eszközök listájában válasszon ki egy eszközt az *Áttekintés* panel megnyitásához, majd válassza a **szinkronizálás**lehetőséget.
5. Válassza az **Igen** lehetőséget a megerősítéshez.

A szinkronizálási művelet állapotának megtekintéséhez válassza az **Eszközök** > **Eszközműveletek** lehetőséget.

A [frissítési ciklus idején](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)a standard Intune házirend-beadási gyakorisága is megtalálható.

## <a name="retryable-error-codes"></a>Újrapróbálható hibakódok

Ha a rendszergazda a **Szinkronizálás** eszközműveletet futtatja, a sikertelen iOS- és Android-alkalmazásokhoz használható újrapróbálható hibakód továbbra is elérhető. Ha azonban az alkalmazás nem újrapróbálható hibakódot generált, akkor az hét napig nem lesz elérhető az eszköz számára.


| Hibakód  | Javasolt leírás | Újrapróbálható |
|---|---|---|
| 2016330898 | Ismeretlen hiba történt. | Nem |
| 2016330897 | Az Intune-nal létesített kapcsolódás időkorlátja lejárt. A kapcsolatok alaphelyzetbe állítása. | Igen |
| 2016330896 | Megszakadt az internetkapcsolat. Kapcsolat alaphelyzetbe állítása. | Igen |
| 2016330895 | Megszakadt az internetkapcsolat. Kapcsolat alaphelyzetbe állítása. | Igen |
| 2016330894 | Megszakadt az internetkapcsolat. Kapcsolat alaphelyzetbe állítása. | Igen |
| 2016330893 | Megszakadt az internetkapcsolat. Kapcsolat alaphelyzetbe állítása. | Igen|
| 2016330892 | A nemzetközi roaming le van tiltva. | Nem|
| 2016330891 | Az eszköz mobil adatkapcsolata nem érhető el Telefonhívás közben. Várjon a hívás befejezéséig. | Igen|
| 2016330890 | Az eszköz mobilhálózata. Ezek az eszközök jelenleg nem használhatók. | Nem|
| 2016330889 | A biztonságos kapcsolat sikertelen. Kapcsolat alaphelyzetbe állítása. | Igen|
| 2016330888 | A kiszolgáló megbízhatósági értékelése sikertelen. | Nem|

## <a name="next-steps"></a>További lépések

[Megtekintheti az eszköz részleteit](device-inventory.md).
 
