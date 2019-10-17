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
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9fbf555f204e54a65e11c4b14f0a461213b61746
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509362"
---
# <a name="rename-a-device-in-intune"></a>Eszköz átnevezése az Intune-ban


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az **eszköz átnevezése** művelettel átnevezheti az Intune-ban regisztrált eszközöket. Az eszköz neve módosítva van az Intune-ban és az eszközön.

A következő típusú eszközöket nevezheti át:
- vállalat által birtokolt Windows 
- felügyelt iOS
- vállalat által birtokolt MacOS 10

Ez a funkció jelenleg nem támogatja a hibrid Azure AD Windows-eszközök átnevezését.

## <a name="rename-a-device"></a>Eszköz átnevezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **eszközök**@no__t – 1**minden** eszköz lehetőséget, > válasszon egy eszközt, > **több** > **eszköz átnevezése**.
4. Az **eszköz átnevezése** panelen írja be az új nevet a szövegmezőbe. Betűket, számokat és kötőjeleket is használhat. A névnek legalább egy betűt vagy kötőjelet tartalmaznia kell.
5. Ha az Átnevezés után újra szeretné indítani az eszközt, az újraindítás után az **Igen** gombra kattintva **indítsa újra**a rendszert.
6. Válassza az **Átnevezés**lehetőséget.



## <a name="next-steps"></a>További lépések

Az eszköz **átnevezése** művelet állapotának megtekintéséhez tekintse meg az eszköz **Áttekintés** lapját.
