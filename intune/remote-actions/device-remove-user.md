---
title: A Microsoft Intune által felügyelt iOS-eszköz felhasználójának eltávolítása
titleSuffix: ''
description: Ismerje meg, hogyan távolíthat el felhasználót egy Intune által felügyelt, megosztott iOS-eszközről.
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
ms.openlocfilehash: 772cdbe203b0489a9b2312a1cc10ea1b3182b35d
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713154"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Felhasználó eltávolítása megosztott iOS-eszközről


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A **Felhasználó eltávolítása** művelettel törölheti a kiválasztott felhasználót az iPad eszköz helyi gyorsítótárából. Az iPad eszközt úgy kell beállítani egy [iOS oktatási profillal](../fundamentals/education-settings-configure-ios.md), hogy kezelje az iOS Osztályterem alkalmazást. 

## <a name="supported-platforms"></a>Támogatott platformok

- Windows – nem támogatott
- Windows Phone – nem támogatott
- iOS – az iOS 9.3-as és újabb verzióiban támogatott (csak megosztott iPad eszközökön)
- macOS – nem támogatott
- Android – nem támogatott

## <a name="remove-a-user"></a>Felhasználó eltávolítása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **Eszközök** > **Minden eszköz** lehetőséget.
3. A felügyelt eszközök listájából válasszon ki egy iOS-eszközt.
4. Az eszköz ablaktábláján válassza a **Felhasználók** lehetőséget.
5. A listán a jobb gombbal kattintson az eltávolítani kívánt felhasználóra, majd kattintson a **Felhasználó eltávolítása** elemre.

## <a name="next-steps"></a>További lépések

- A **Felhasználók eltávolítása** művelet állapotának megtekintéséhez válassza az **Eszközök** > **Eszközműveletek** lehetőséget.
