---
title: Alkalmazáskonfigurációs szabályzatok kezelt alkalmazásokhoz eszközregisztráció nélkül
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan konfigurálhat szabályzatokat kezelt alkalmazásokhoz eszközregisztráció nélkül.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
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
ms.openlocfilehash: 3a31a4777537db6f656dbf9eaf0b30a6e95412a8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499767"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazáskonfigurációs szabályzatokat nem regisztrált eszközökön is használhatja az olyan felügyelt alkalmazásokkal, amelyek támogatják az Intune App SDK-t. 

> [!NOTE]
> Alkalmazás-konfigurációs szabályzatok fogadásához az alkalmazásoknak Intune App Protection szabályzattal kell rendelkezniük. További információ az Intune App Protection szabályzatainak létrehozásáról: [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md)

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **Ügyfélalkalmazások** területet.
4. Válassza az **Alkalmazáskonfigurációs szabályzatok** lehetőséget a **Felügyelet** csoportban, majd a **Hozzáadás** lehetőséget.
5. Adja meg a következő adatokat:
    - **Név**  
      Az Azure Portalon megjelenő profilnév.
    - **Leírás**  
      Az Azure Portalon megjelenő profilleírás.
    - **Eszközbeléptetés típusa**  
      Válassza az **Alkalmazások kezelése** lehetőséget.
6. A konfigurálni kívánt alkalmazás kiválasztásához válassza a **Társított alkalmazás** lehetőséget. Válassza ki a listából azon alkalmazásokat, amelyeket jóváhagyott az Intune-nal való szinkronizáláshoz.
7. Az alkalmazás által támogatott konfigurációs beállítások mindegyikéhez írja be a **Nevet** és az **Értéket**, majd válassza a három pontot ( **…** ).  
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
