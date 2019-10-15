---
title: Személyes adatok megtekintése és javítása
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan tekintheti meg és javítsa ki a személyes adatokkal.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1ba77bc7-505e-4eca-a49e-dcdaa75d0043
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b6ca291f55511be9e88b0ff898d9383691542bf
ms.sourcegitcommit: a2654f3642b43b29ab0e1cbb2dfa2b56aae18d0e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72310901"
---
# <a name="view-and-correct-personal-data"></a>Személyes adatok megtekintése és javítása

Az Intune-rendszergazdák a hozzáférési engedélyeik alapján megtekinthetik a személyes adategységeket, de csak a végfelhasználók módosíthatják az eszköz személyes adatfájljait.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-dsr-and-stp-note.md)]


## <a name="view-personal-data"></a>Személyes adattárolás megtekintése

A rendszergazdák az Intune felhasználói felületén különböző lapokon láthatják a végfelhasználók személyes adatait. A következő cikkek elmagyarázzák, hogy a rendszergazdák mit tesznek és miért nem férnek hozzá a szolgáltatáshoz:
- Az [eszköz adatainak megtekintése](../remote-actions/device-inventory.md) az Intune-ban című cikk azt ismerteti, hogyan tekintheti át a végfelhasználó eszközének részleteit.
- Az alkalmazásadatok [és-hozzárendelések figyelése](../apps/apps-monitor.md) című cikk azt ismerteti, hogyan tekintheti meg a végfelhasználói eszközre telepített alkalmazások részleteit.
- [Milyen információkat láthatok a vállalatom az eszköz regisztrálása során? cikk](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) a végfelhasználók számára a vállalat által megjelenített és nem látható adatok listáját adja meg. Érdemes egyértelműen megállapítani a felhasználókat, hogy milyen típusú adatok gyűjtése történik, és miért gyűjti azt. Ez a cikk az átláthatóság első lépése lehet.

### <a name="who-can-view-the-data"></a>Kik tekinthetik meg az adatvédelmet?

A Microsoft szigorú szabályozással szabályozza az ügyféladatok elérését, biztosítva a legfontosabb feladatok végrehajtásához és a hozzáférés visszavonásához szükséges legalacsonyabb szintű hozzáférést, ha már nincs rá szükség. 

Szerepköralapú adminisztrációs vezérlő (RBAC) használatával biztonságossá teheti és szabályozhatja a végfelhasználók személyes adataihoz való hozzáférést. További információ: [RBAC with Microsoft Intune](../fundamentals/role-based-access-control.md).

A Microsoft adatkezelési gyakorlatával kapcsolatos további információkért olvassa el az online szolgáltatások használati feltételeit és a [Microsoft Online Services adatvédelmi nyilatkozatát](https://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409). 

## <a name="correct-end-user-personal-data"></a>A végfelhasználói személyes adatok helyes javítása

A rendszergazdák nem frissíthetik az eszközre vagy az alkalmazásra vonatkozó információkat. Ha egy végfelhasználó szeretné kijavítani a személyes adatok (például az eszköz nevét), azt közvetlenül az eszközén kell megtennie. Ezek a változások szinkronizálva lesznek a következő alkalommal, amikor csatlakoznak az Intune-hoz.


## <a name="next-steps"></a>Következő lépések

Megtudhatja [, hogyan naplózhatja, exportálhatja vagy törölheti](privacy-data-audit-export-delete.md) a személyes adatvédelmet az Intune-ban.
