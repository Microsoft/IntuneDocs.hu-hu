---
title: Egy iOS/iPadOS-eszköz felhasználójának kijelentkezése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan jelentkezhet be egy iOS/iPadOS-eszköz aktuális felhasználója az Intune-nal. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e23f95d169a95244abc8669eb9a19150cff8138
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413694"
---
# <a name="logout-the-current-user-on-intune-managed-iosipados-devices"></a>Az aktuális felhasználó kijelentkezése az Intune által felügyelt iOS-/iPadOS-eszközökön


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az **Aktuális felhasználó kijelentkeztetése** művelet kijelentkezteti egy megosztott iPad aktuális felhasználóját. 

## <a name="supported-platforms"></a>Támogatott platformok

- Windows – nem támogatott
- Windows Phone – nem támogatott
- iOS/iPadOS – az iOS/iPadOS 9,3-es és újabb verzióiban támogatott (csak megosztott iPad eszközök esetén)
- macOS – nem támogatott
- Android – nem támogatott

## <a name="how-to-log-out-the-current-user"></a>Aktuális felhasználó kijelentkeztetése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431) , és válassza az **eszközök**lehetőséget.
4. Az **Eszközök és csoportok** panelen válassza a **Minden eszköz** lehetőséget.
5. A felügyelt eszközök listájából válassza ki az iOS/iPadOS eszközt, majd válassza az aktuális felhasználói eszköz távoli műveletének **kijelentkezése** lehetőséget.

## <a name="next-steps"></a>További lépések

A kezdeményezett művelet állapotát az **Eszközök és csoportok** panel **Eszközműveletek** szakaszában tekintheti meg.
