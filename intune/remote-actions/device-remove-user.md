---
title: Felhasználó eltávolítása iOS-vagy iPadOS-eszközről Microsoft Intune
titleSuffix: ''
description: Ismerje meg, hogyan távolíthat el felhasználót egy megosztott iOS/iPadOS-eszközről az Intune-nal.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b6b2b3492b9edece6b69e4b302741c0443c0a3e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415566"
---
# <a name="remove-a-user-from-a-shared-iosipados-device"></a>Felhasználó eltávolítása megosztott iOS-/iPadOS-eszközről


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A **Felhasználó eltávolítása** művelettel törölheti a kiválasztott felhasználót az iPad eszköz helyi gyorsítótárából. Az iPad eszközt úgy kell beállítani, hogy az iOS/iPadOS tantermi alkalmazást [iOS/iPadOS oktatási profil](../fundamentals/education-settings-configure-ios.md)használatával kezelhesse. 

## <a name="supported-platforms"></a>Támogatott platformok

- Windows – nem támogatott
- Windows Phone – nem támogatott
- iOS/iPadOS – az iOS/iPadOS 9,3-es és újabb verzióiban támogatott (csak megosztott iPad eszközök esetén)
- macOS – nem támogatott
- Android – nem támogatott

## <a name="remove-a-user"></a>Felhasználó eltávolítása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **Eszközök** > **Minden eszköz** lehetőséget.
3. A felügyelt eszközök listájában válassza ki az iOS/iPadOS eszközt.
4. Az eszköz ablaktábláján válassza a **Felhasználók** lehetőséget.
5. A listán a jobb gombbal kattintson az eltávolítani kívánt felhasználóra, majd kattintson a **Felhasználó eltávolítása** elemre.

## <a name="next-steps"></a>További lépések

- A **Felhasználók eltávolítása** művelet állapotának megtekintéséhez válassza az **Eszközök** > **Eszközműveletek** lehetőséget.
