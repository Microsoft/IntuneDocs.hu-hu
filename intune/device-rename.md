---
title: Eszköz átnevezése Microsoft Intune-Azure-val | Microsoft Docs
description: Az eszköz átnevezése Microsoft Intune használatával.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d109529e2c5dafdf8d5b4e0d73191d1715ecd8c
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71304657"
---
# <a name="rename-a-device-in-intune"></a>Eszköz átnevezése az Intune-ban


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az **eszköz átnevezése** művelettel átnevezheti az Intune-ban regisztrált eszközöket. Az eszköz neve módosítva van az Intune-ban és az eszközön.

A következő típusú eszközöket nevezheti át:
- vállalat által birtokolt Windows 
- felügyelt iOS
- vállalat által birtokolt MacOS 10

Ez a funkció jelenleg nem támogatja a hibrid Azure AD Windows-eszközök átnevezését.

## <a name="rename-a-device"></a>Eszköz átnevezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **eszközök** > **minden eszköz** lehetőséget > válasszon ki egy eszközt > **további** > **Átnevezés eszköz**.
4. Az **eszköz átnevezése** panelen írja be az új nevet a szövegmezőbe. Betűket, számokat és kötőjeleket is használhat. A névnek legalább egy betűt vagy kötőjelet tartalmaznia kell.
5. Ha az Átnevezés után újra szeretné indítani az eszközt, az újraindítás után az **Igen** gombra kattintva **indítsa újra**a rendszert.
6. Válassza az **Átnevezés**lehetőséget.



## <a name="next-steps"></a>További lépések

Az eszköz **átnevezése** művelet állapotának megtekintéséhez tekintse meg az eszköz **Áttekintés** lapját.
