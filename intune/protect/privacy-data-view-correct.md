---
title: Személyes adatok megtekintése és javítása
titleSuffix: Microsoft Intune
description: Ismertető a személyes adatok megtekintéséhez és javításához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1ba77bc7-505e-4eca-a49e-dcdaa75d0043
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 913bf3103254abdd73913e0efc81da3a38ca991b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504249"
---
# <a name="view-and-correct-personal-data"></a>Személyes adatok megtekintése és javítása

Az Intune-rendszergazdák hozzáférési engedélyeiktől függően megtekinthetnek bizonyos személyes adatokat, de az eszköz személyes adatait csak a végfelhasználók módosíthatják.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-dsr-and-stp-note.md)]


## <a name="view-personal-data"></a>Személyes adatok megtekintése

Az Intune kezelőfelületének különböző paneljein a rendszergazdák számára láthatók a végfelhasználók személyes adatai. A következő cikkek a rendszergazdák számára hozzáférhető és nem hozzáférhető információk körét ismertetik:
- Az [eszköz adatainak megtekintése](../remote-actions/device-inventory.md) az Intune-ban leírja, hogyan tekinthetők át egy végfelhasználó eszközének adatai.
- Az [Alkalmazásadatok és -hozzárendelések figyelése](../apps/apps-monitor.md) azt ismerteti, hogy hogyan tekinthetők meg az egy végfelhasználó eszközére telepített alkalmazások adatai.
- A [Milyen adatok láthatók a cég számára, ha regisztrálom az eszközömet?](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) című cikk felsorolja a végfelhasználók számára a vállalatuk által látható és nem látható adatokat. Célszerű egyértelműen tudatni a felhasználókkal, hogy milyen adatokat gyűjt, és miért. Ez a cikk lehet az első lépés az átláthatóság felé.

### <a name="who-can-view-the-data"></a>Ki tekintheti meg az adatokat?

A Microsoft szigorú korlátozásokkal szabályozza az ügyfelek adataihoz való hozzáférést, csak a lényeges feladatok elvégzéséhez szükséges legalacsonyabb szintű hozzáférést megadva, és a hozzáférés visszavonásával, amikor arra már nincs szükség. 

A végfelhasználói adatokhoz való hozzáférés szerepköralapú hozzáférés-vezérlés (RBAC) használatával tehető biztonságossá és szabályozhatóvá. További információ: [Szerepköralapú hozzáférés-vezérlés (RBAC) a Microsoft Intune-nal](../fundamentals/role-based-access-control.md).

A Microsoft adatkezelési gyakorlatáról az Online Services feltételeiből és a [Microsoft Online Services Adatvédelmi nyilatkozatából](https://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409) tájékozódhat bővebben. 

## <a name="correct-end-user-personal-data"></a>Végfelhasználók személyes adatainak javítása

A rendszergazdák nem frissíthetik az eszköz- vagy alkalmazásspecifikus információkat. Ha egy végfelhasználó ki szeretne javítani egy személyes adatot (például az eszköz nevét), akkor ezt közvetlenül az eszközön kell megtennie. Az ilyen módosítások az Intune-hoz való legközelebbi kapcsolódáskor lesznek szinkronizálva.


## <a name="next-steps"></a>További lépések

Ismertető személyes adatok Intune-beli [naplózásáról, exportálásáról vagy törléséről](privacy-data-audit-export-delete.md).
