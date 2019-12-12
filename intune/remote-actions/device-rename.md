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
ms.openlocfilehash: 0f5ee9a0fe27c3cf9de758fd7155dbd127fb1e5e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712221"
---
# <a name="rename-a-device-in-intune"></a>Eszköz átnevezése az Intune-ban

Az **eszköz átnevezése** művelettel átnevezheti az Intune-ban regisztrált eszközöket. Az eszköz neve módosítva van az Intune-ban és az eszközön.

A következő típusú eszközöket nevezheti át:
- vállalat által birtokolt Windows 
- felügyelt iOS
- vállalat által birtokolt MacOS 10

Ez a funkció jelenleg nem támogatja a hibrid Azure AD Windows-eszközök átnevezését.

## <a name="rename-a-device"></a>Eszköz átnevezése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza az **eszközök** > **minden eszköz** lehetőséget > válasszon ki egy eszközt > **további** > **átnevezése eszköz**.
4. Az **eszköz átnevezése** panelen írja be az új nevet a szövegmezőbe. Betűket, számokat és kötőjeleket is használhat. A névnek legalább egy betűt vagy kötőjelet tartalmaznia kell.
5. Ha az Átnevezés után újra szeretné indítani az eszközt, az újraindítás után az **Igen** gombra kattintva **indítsa újra**a rendszert.
6. Válassza az **Átnevezés**lehetőséget.

## <a name="windows-device-rename-rules"></a>Windows-eszköz átnevezési szabályai
Windows-eszköz átnevezése esetén az új névnek a következő szabályoknak kell megfelelnie:
- legfeljebb 15 karakter (63 bájtnál kisebbnek vagy azzal egyenlőnek kell lennie, a záró NULL értékkel nem együtt)
- Nem null vagy üres karakterlánc
- Engedélyezett ASCII: betűk (a-z, A-Z), számok (0-9) és kötőjelek
- Engedélyezett Unicode: karakter > = 0x80, érvényes UTF8-nak kell lennie, az IDN-leképezhető (azaz a RtlIdnToNameprepUnicode sikeresek, lásd: RFC 3492)
- A nevek nem tartalmazhatnak csak számokat
- Nincs szóköz a névben
- Nem engedélyezett karakterek: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>További lépések

Az eszköz **átnevezése** művelet állapotának megtekintéséhez tekintse meg az eszköz **Áttekintés** lapját.
