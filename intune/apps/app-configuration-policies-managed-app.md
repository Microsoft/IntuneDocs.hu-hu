---
title: Alkalmazáskonfigurációs szabályzatok kezelt alkalmazásokhoz eszközregisztráció nélkül
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan konfigurálhat szabályzatokat kezelt alkalmazásokhoz eszközregisztráció nélkül.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68032f47be043e8c49b6ad922392d14549293c35
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564274"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazáskonfigurációs szabályzatokat nem regisztrált eszközökön is használhatja az olyan felügyelt alkalmazásokkal, amelyek támogatják az Intune App SDK-t. 

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza ki az **alkalmazások** > **alkalmazás-konfigurációs szabályzatok** >  > **felügyelt alkalmazások** **hozzáadása** lehetőséget.
3. Adja meg a következő adatokat:
    - **Név**  
      Az Azure Portalon megjelenő profilnév.
    - **Leírás**  
      Az Azure Portalon megjelenő profilleírás.
4. Válassza a **nyilvános alkalmazások kiválasztása** lehetőséget, vagy **válassza az egyéni alkalmazások** lehetőséget a konfigurálni kívánt alkalmazás kiválasztásához. Válassza ki a listából azon alkalmazásokat, amelyeket jóváhagyott az Intune-nal való szinkronizáláshoz.
5. Az alkalmazás által támogatott konfigurációs beállításokhoz írja be a **nevet** és az **értéket**.  
    Egy konfiguráció törléséhez válassza a három pontot ( **...** ), majd a **Törlés** lehetőséget.  
    
Az Intune App SDK-val kompatibilis alkalmazások támogatják a kulcs-érték párokban megadott konfigurációkat. Ha többet szeretne megtudni a támogatott kulcs-érték párokban megadott konfigurációkról, tekintse meg az egyes alkalmazások dokumentációját. Fontos megjegyezni, hogy használhat olyan tokeneket, amelyek dinamikusan töltődnek fel az alkalmazás által generált adatokkal. Az iOS Outlook alkalmazás konfigurációs szabályzatának beállításairól [Az iOS Outlook alkalmazás konfigurációjának kezelése a Microsoft Intune-nal](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx) című témakörben tájékozódhat.

## <a name="configuration-values-for-using-tokens"></a>Konfigurációs értékek jogkivonatok használatához

Az Intune képes bizonyos jogkivonatokat generálni és elküldeni a felügyelt alkalmazásnak. Ha például az alkalmazáskonfiguráció használhat e-mail-beállítást, egy jogkivonattal dinamikus e-mailt adhat hozzá. Írja be az alkalmazás által várt nevet a **Név** mezőbe, majd írja be az **Érték** mezőbe az alábbi értéket: `\{\{mail\}\}`.

Az Intune a következő tokentípusokat támogatja a konfigurációs beállítások között. Más egyéni kulcs-érték párok nincsenek támogatva.

- \{\{userprincipalname\}\} – például: John@contoso.com
- \{\{mail\}\} – például: John@contoso.com
- \{\{partialupn\}\} – például: John
- \{\{accountid\}\} – például: fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\} – például: 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} — például: John Doe
- \{\{PrimarySMTPAddress\}\}– például: testuser@ad.domain.com


> [!Note]  
> A \{\{ és \}\} karaktereket csak a tokentípusok használják, ezek más célokra nem használhatók.

## <a name="next-steps"></a>További lépések

Ezt követően a szokott módon gondoskodhat az alkalmazás valamely csoporthoz történő [hozzárendeléséről](apps-deploy.md) és [figyeléséről](apps-monitor.md).
