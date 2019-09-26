---
title: A Google által az Intune-nak küldött adatok
titleSuffix: Microsoft Intune
description: A Google által az Intune-nak küldött adatok listája.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9163e449737973309410aa5dca87b759d38586ee
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/23/2019
ms.locfileid: "71303936"
---
# <a name="data-google-sends-to-intune"></a>A Google által az Intune-nak küldött adatok

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ha az Android Enterprise eszközkezelése engedélyezve van egy eszközön, a Microsoft Intune kapcsolatot létesít az Google-lel, és felhasználói és eszközadatok lesznek megosztva az Intune és a Google között. Ahhoz, hogy a Microsoft Intune létrehozhassa a kapcsolatot, Önnek létre kell hoznia egy Google-fiókot.

Az alábbi táblázat felsorolja az adatokat, amelyeket az eszközkezelés engedélyezése esetén a Google küld az Intune-nak:


| A Google által az Intune-nak küldött adatok | Részletek | Használatban | Példa |
|:---:|:---:|:---:|:---:|
| Vállalati adatok | Az ügyfél Google-beli vállalati azonosítói. | Összekapcsolja az ügyféladatokat az Intune és a Google között. | **enterpriseId** példa: LC04eik8a6.<br>**Név**. A rendszergazdának az Android Enterprise konfigurálásakor megadott neve. Példa: Joe Smith.<br>**Rendszergazda e-mail címe**. Az Android Enterprise konfigurálásakor használt YourAdmin@gmail.com. |
| Alkalmazásadatok | Felügyelt Play Áruház-alkalmazások adatai. | Az alkalmazás felhasználókhoz vagy eszközökhöz rendelése elérhetőként vagy kötelezőként. | **Alkalmazás neve** példa: Contoso Warehouse-leltár alkalmazás.<br>**Az alkalmazás egyedi azonosítója** példa: app:com.Contoso.Warehouse.InventoryTracking |
| Szolgáltatásfiók | Adott ügyfélhívásokkal használandó egyedi belső Google-szolgáltatásfiók. | Az ügyfél nevében a Google-be irányuló hívásokhoz lesz használva (alkalmazások vagy eszközök megtekintésére és más célokra) | **Név** példa: InternalAccount@InternalService.com.<br>**Kulcsok** például: ServiceAccountPassword |


Ha nem szeretné használni az Android Enterprise eszközkezelést az Intune-nal, és törölni szeretné az adatokat, le kell tiltania a Microsoft Intune Android Enterprise eszközkezelést, és törölnie kell a Google-fiókját. A fiókkezelésről a Google-fiókban tudhat meg többet.


