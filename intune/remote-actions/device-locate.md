---
title: Elveszett iOS/iPadOS-eszközök megkeresése az Microsoft Intune-Azure-ban | Microsoft Docs
description: Az elveszett vagy ellopott iOS-/iPadOS-eszközök megkereséséhez használja a Microsoft Intune eszközének megkeresése funkcióját. Az eszközkeresési művelet használatakor biztonsági és adatvédelmi információkat is kaphat.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc276a6235fb4951c83b62e3c488145062814728
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415581"
---
# <a name="locate-lost-or-stolen-iosipados-devices-with-intune"></a>Elveszett vagy ellopott iOS-/iPadOS-eszközök megkeresése az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az elveszett vagy ellopott iOS/iPadOS eszköz helyének lekéréséhez használja az **eszköz megkeresése** műveletet. Az eszköznek felügyelt módban kell lennie. A művelet használata előtt győződjön meg róla, hogy az eszközt [Elveszett módba](device-lost-mode.md) állította.

## <a name="supported-platforms"></a>Támogatott platformok

- iOS/iPadOS 9,3 és újabb verziók

Ez a funkció nem támogatott a következő rendszereken: 
- Windows
- Windows Phone
- macOS
- Android:

## <a name="locate-a-lost-or-stolen-device"></a>Elveszett vagy ellopott eszköz megkeresése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Kattintson az **Eszközök**, majd a **Minden eszköz** elemre.
4. A felügyelt eszközök listájából válassza ki az iOS/iPadOS eszközt, és válassza a **... Továbbiak**. Majd válassza az **Eszköz megkeresése** távoli műveletet.
5. Miután a rendszer megtalálta az eszközt, megjeleníti annak helyét az **Eszköz megkeresése** panelen.
    ![Egy eszköz Azure-beli Intune-nal való megkeresésének képernyőképe](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Az Elveszett üzemmód hangos riasztásának engedélyezése iOS-eszközön

Ha valaki elvesztette az iOS/iPadOS 9,3-es vagy újabb eszközét, távolról is aktiválhatja az eszközt riasztási hang lejátszásához, hogy a felhasználó megtalálja. Az eszköznek ehhez [Elveszett üzemmódban](device-lost-mode.md) kell lennie.

A [Azure Portal Intune-ban](https://aka.ms/intuneportal)válassza az **eszközök** > **minden eszköz** lehetőséget > válasszon ki egy IOS/IPadOS-eszközt > **Áttekintés** > **további** > az **elveszett üzemmódú hang lejátszása (csak felügyelet esetén)** .

A hang lejátszása egészen addig folytatódik, amíg a felhasználó le nem tiltja a hangot az eszközön, vagy az eszköz ki nem lép az Elveszett üzemmódból.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Az Elveszett eszköz módhoz és az eszközkeresési műveletekhez kapcsolódó biztonsági és adatvédelmi információk
- A művelet elindításáig a rendszer semmilyen információt nem küld az Intune-nak az eszköz helyéről.
- Az eszközkeresési művelet használatakor az eszköz szélességi és hosszúsági koordinátái a Graph API használatával kérhetők le.
- A rendszer 24 óráig tárolja az adatokat, majd törli azokat. A helyadatokat manuálisan nem lehet eltávolítani.
- A helyadatok tároláskor és továbbításkor egyaránt titkosítva vannak.
- Az Elveszett eszköz mód konfigurálásakor megadhat egy egyéni üzenetet, mely megjelenik az eszköz zárolási képernyőjén. Ebben az üzenetben mindenképp célszerű pontosan jeleznie, hogy az eszközt megtaláló személy miként tudja visszaszolgáltatni az eszközt a cégének.

## <a name="next-steps"></a>További lépések

Az Eszköz megkeresése művelet állapotát az **Eszközök** > **Eszközműveletek** lehetőség választásával tekintheti meg.
