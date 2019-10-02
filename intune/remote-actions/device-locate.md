---
title: Elveszett iOS-eszközök megkeresése az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Keresse meg az elveszett vagy ellopott iOS eszközöket a Microsoft Intune eszközkeresési funkciójával. Az eszközkeresési művelet használatakor biztonsági és adatvédelmi információkat is kaphat.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e3ab83c282c1e97e80a783f569410253bdf7d42
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732419"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Elveszett vagy ellopott iOS-eszközök megkeresése az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az **Eszköz megkeresése** művelettel megjelenítheti térképen az elveszett vagy ellopott iOS-eszközök helyét. Az eszköznek felügyelt módban kell lennie. A művelet használata előtt győződjön meg róla, hogy az eszközt [Elveszett módba](device-lost-mode.md) állította.

## <a name="supported-platforms"></a>Támogatott platformok

- iOS 9.3 és újabb verziók

Ez a funkció nem támogatott a következő rendszereken: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Elveszett vagy ellopott eszköz megkeresése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **Eszközök**, majd a **Minden eszköz** lehetőséget.
4. A felügyelt eszközök listájából válasszon ki egy iOS-eszközt, és válassza a **...További** lehetőséget. Majd válassza az **Eszköz megkeresése** távoli műveletet.
5. Miután a rendszer megtalálta az eszközt, megjeleníti annak helyét az **Eszköz megkeresése** panelen.
    ![Egy eszköz Azure-beli Intune-nal való megkeresésének képernyőképe](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Az Elveszett üzemmód hangos riasztásának engedélyezése iOS-eszközön

Ha valaki elveszt az iOS 9.3-as vagy újabb rendszerű eszközét, azon távolról aktiválható egy riasztási hang, amely segít megtalálni. Az eszköznek ehhez [Elveszett üzemmódban](device-lost-mode.md) kell lennie.

Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal), válassza az **Eszközök** > **Minden eszköz** > kívánt iOS-eszköz > **Áttekintés** > **További** > **Elveszett üzemmódhoz tartozó hang lejátszása (csak felügyelettel)** lehetőséget.

A hang lejátszása egészen addig folytatódik, amíg a felhasználó le nem tiltja a hangot az eszközön, vagy az eszköz ki nem lép az Elveszett üzemmódból.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Az Elveszett eszköz módhoz és az eszközkeresési műveletekhez kapcsolódó biztonsági és adatvédelmi információk
- A művelet elindításáig a rendszer semmilyen információt nem küld az Intune-nak az eszköz helyéről.
- Az eszközkeresési művelet használatakor az eszköz szélességi és hosszúsági koordinátái a Graph API használatával kérhetők le.
- A rendszer 24 óráig tárolja az adatokat, majd törli azokat. A helyadatokat manuálisan nem lehet eltávolítani.
- A helyadatok tároláskor és továbbításkor egyaránt titkosítva vannak.
- Az Elveszett eszköz mód konfigurálásakor megadhat egy egyéni üzenetet, mely megjelenik az eszköz zárolási képernyőjén. Ebben az üzenetben mindenképp célszerű pontosan jeleznie, hogy az eszközt megtaláló személy miként tudja visszaszolgáltatni az eszközt a cégének.

## <a name="next-steps"></a>További lépések

Az Eszköz megkeresése művelet állapotát az **Eszközök** > **Eszközműveletek** lehetőség választásával tekintheti meg.
