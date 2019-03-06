---
title: Eszközök zárolása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: A Microsoft Intune-ban elérhető Távoli zárolás művelettel zárolhatja a PIN-kóddal vagy jelszóval védett eszközöket.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4d0443b100a4a973161ddcbf5e445c4b6136e6f
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57394233"
---
# <a name="remotely-lock-devices-with-intune"></a>Eszközök távoli zárolása az Intune-nal

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A **Távoli zárolás** eszközművelet zárolja az eszközt. A zárolás feloldásához az eszköz tulajdonosának be kell írnia a PIN-kódját. Csak olyan eszköz zárolható távolról, amelyhez PIN-kód vagy jelszó van megadva. A PIN-kód vagy jelszó nélküli eszközöket nem lehet távolról zárolni.

## <a name="supported-platforms"></a>Támogatott platformok

A **távoli zárolás** az alábbi platformokon támogatott:

- Android
- Vállalati androidos kioszkeszközök
- Vállalati androidos kioszkeszközök
- iOS
- macOS
- Windows 10 mobil verzió
- Windows Phone 8.1 és újabb verziók

A **távoli zárolás** nem támogatott:
- Windows 10 asztali verzió

> [!NOTE]
> MacOS eszközökhöz egy hatjegyű helyreállítási PIN-kódot kell megadnia. Ha az eszköz zárolva van, az **Eszközáttekintés** panelen látható marad a PIN-kód mindaddig, amíg az eszköznek nem kell egy másik műveletet végrehajtania.

## <a name="remote-lock-a-device"></a>Egy eszköz távoli zárolása

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).
2. Válassza a **Minden szolgáltatás** lehetőséget, szűrjön az **Intune**-ra, és válassza a **Microsoft Intune** elemet.
3. Válassza az **Eszközök** > **Minden eszköz** lehetőséget.
4. Válasszon egy eszközt az eszközlistáról, majd válassza a **Távoli zárolás** műveletet.

## <a name="next-steps"></a>További lépések

- A művelet állapotának megtekintéséhez válassza a **Microsoft Intune** > **Eszközök** > **Eszközműveletek** lehetőséget. 
- Az eszközök kezeléséhez rendelkezésre álló további műveletekről a [Rendelkezésre álló műveletek](device-management.md) témakörben tájékozódhat.
