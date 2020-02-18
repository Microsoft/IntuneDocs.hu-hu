---
title: Alkalmazáskonfigurációs szabályzatok kezelt alkalmazásokhoz eszközregisztráció nélkül
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan konfigurálhat szabályzatokat kezelt alkalmazásokhoz eszközregisztráció nélkül.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 4301afca471d0aa56fa1a0826ad7f88bcdf23de2
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414873"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazáskonfigurációs szabályzatokat nem regisztrált eszközökön is használhatja az olyan felügyelt alkalmazásokkal, amelyek támogatják az Intune App SDK-t. 

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza ki az **alkalmazások** > **alkalmazás-konfigurációs szabályzatok** >  > **felügyelt alkalmazások** **hozzáadása** lehetőséget.
3. Az **alapvető beállítások** lapon adja meg a következő adatokat:
    - **Name (név**): a Azure Portalban megjelenő profil neve.
    - **Description (Leírás**): a profil leírása, amely megjelenik a Azure Portalban.
    - **Eszköz beléptetésének típusa**: kiválasztva a felügyelt alkalmazások.
4. Válassza a **nyilvános alkalmazások kiválasztása** lehetőséget, vagy **válassza az egyéni alkalmazások** lehetőséget a konfigurálni kívánt alkalmazás kiválasztásához. Válassza ki a listából azon alkalmazásokat, amelyeket jóváhagyott az Intune-nal való szinkronizáláshoz.
5. A **Beállítások** lap megjelenítéséhez kattintson a **tovább** gombra.
6. Az alkalmazás által támogatott konfigurációs beállításokhoz írja be a **nevet** és az **értéket**. 

   Az Intune App SDK-val kompatibilis alkalmazások támogatják a kulcs-érték párokban megadott konfigurációkat. Ha többet szeretne megtudni a támogatott kulcs-érték párokban megadott konfigurációkról, tekintse meg az egyes alkalmazások dokumentációját. Fontos megjegyezni, hogy használhat olyan tokeneket, amelyek dinamikusan töltődnek fel az alkalmazás által generált adatokkal. További információ: [konfigurációs értékek a tokenek használatához](~/apps/app-configuration-policies-managed-app.md#configuration-values-for-using-tokens). Az iOS/iPadOS alkalmazás konfigurációs házirendjének beállításaival kapcsolatos információkért lásd: az [Outlook kezelése iOS-/iPadOS-alkalmazás-konfiguráció Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

    Egy konfiguráció törléséhez válassza a három pontot ( **...** ), majd a **Törlés** lehetőséget.  

7. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.
8. Kattintson **a csoportok kiválasztása**elemre.
9. Válasszon ki egy csoportot a **csoportok kiválasztása** ablaktáblán, és kattintson a **kiválasztás**elemre.
10. Kattintson a **Válassza ki a kizárandó csoportokat** lehetőségre a kapcsolódó panel megjelenítéséhez.
11. Válassza ki azokat a csoportokat, amelyeket ki szeretne zárni, majd kattintson a **Kijelölés** lehetőségre.

    >[!NOTE]
    >Csoportok hozzáadásakor, ha bármely más csoport már bele lett foglalva egy adott hozzárendelés-típus esetében, az előre ki van jelölve, és nem módosítható más belefoglalási hozzárendelés-típusok esetében. Ezért az adott csoport használatba lett véve, és így nem használható kizárt csoportként.

12. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez.
13. A **Létrehozás** gombra kattintva adja hozzá az alkalmazás konfigurációs szabályzatát az Intune-hoz.

## <a name="configuration-values-for-using-tokens"></a>Konfigurációs értékek jogkivonatok használatához

Az Intune képes bizonyos jogkivonatokat generálni és elküldeni a felügyelt alkalmazásnak. Ha például az alkalmazáskonfiguráció használhat e-mail-beállítást, egy jogkivonattal dinamikus e-mailt adhat hozzá. Írja be az alkalmazás által várt nevet a **Név** mezőbe, majd írja be az `\{\{mail\}\}`Érték**mezőbe az alábbi értéket:** .

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
