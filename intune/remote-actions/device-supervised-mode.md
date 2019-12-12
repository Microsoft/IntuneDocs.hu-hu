---
title: iOS-es felügyelt mód a Microsoft Intune-nal
titleSuffix: ''
description: Információ az iOS-es felügyelt mód bekapcsolásáról az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e995dbc89321bf844151accd654a2d17d35afd9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713431"
---
# <a name="turn-on-ios-supervised-mode"></a>iOS-es felügyelt mód bekapcsolása


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Apple iOS-es felügyelt mód több lehetőséget biztosít a rendszergazdáknak Apple-eszközök kezelésénél, ami különösen a nagy méretekben üzembe helyezett vállalati tulajdonban lévő eszközök esetén hasznos. Például korlátozhatja az AirDropot, vagy letilthatja a felhasználók számára az eszköz nevének módosítását. A felügyelt módot megkövetelő beállítások listáját az [iOS-es eszközkorlátozási beállítások az Intune-ban](../configuration/device-restrictions-ios.md) című témakörben találja.

Az Intune az Apple [készülékregisztrációs program (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) keretében biztosít lehetőséget az eszközök felügyelt módú üzemeltetéséhez.

Az Apple [Adattartalom-beállítási referencia](http://help.apple.com/configurator/mac/2.4/#/cad5370d089) című cikkében megtalálja azoknak az Apple-vezérlőknek a listáját, amelyekhez felügyelt mód szükséges.

## <a name="turn-on-supervised-mode-during-enrollment"></a>Felügyelt mód bekapcsolása regisztrálás során

A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)bekapcsolhatja a felügyelt üzemmódot az eszközökön, amikor [létrehoz egy Apple beléptetési profilt a DEP-ben](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Ehhez az **Eszközfelügyeleti beállítások** területen jelölje be a **Felügyelt** jelölőnégyzetet.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Felügyelt mód bekapcsolása regisztrálás után

Ha a regisztráció már megtörtént, az iOS-eszközt össze kell kötni egy Mac számítógéppel, és az [Apple Configuratort használva](../enrollment/apple-configurator-enroll-ios.md) engedélyezni kell rajta a felügyelt módot (ami alaphelyzetbe állítja az eszközt). Regisztráció után az Intune-ban nem lehetséges az eszközt felügyelt módra konfigurálni.

## <a name="identify-a-supervised-device"></a>Felügyelt eszköz azonosítása

Ha azt szeretné ellenőrizni, hogy felügyelt-e egy eszköz, nézze meg a zárolási képernyőt vagy a **Névjegy** oldalt:
- Az eszköz zárolási képernyőjén ez látható: **Ezt az iPhone-t a „Cég neve” felügyeli.**
- Az eszköz **Névjegy** lapján azt fogja mondani, hogy az **iPhone felügyelve van. A cég neve nyomon követheti az internetes forgalmat, és megkeresheti az eszközt.**

## <a name="next-steps"></a>További lépések

További eszközfelügyeleti beállításokért lásd: [A Microsoft Intune-eszközfelügyelet ismertetése](device-management.md).
