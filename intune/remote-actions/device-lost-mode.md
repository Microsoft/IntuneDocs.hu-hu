---
title: Az iOS Elveszett eszköz módjának aktiválása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az Elveszett eszköz mód bekapcsolásakor megadhat egy egyéni üzenetet a Microsoft Intune-nal, mely megjelenik az elveszett vagy ellopott iOS-eszköz zárolási képernyőjén. Emellett az Elveszett eszköz mód használatakor biztonsági és adatvédelmi információkat is kaphat.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac83160e6604b7a679e03bb244e1dd5081a5fc5
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732647"
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Az Elveszett eszköz mód bekapcsolása egy iOS-eszközön az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az **Elveszett eszköz mód** eszközművelet segítségével engedélyezheti az elveszett eszköz módot elveszett vagy ellopott iOS-es eszközökön. Ebben a módban megadható egy üzenet és egy telefonszám, amely megjelenik az eszköz zárolási képernyőjén. Az Elveszett eszköz mód csak felügyelt módban lévő, vállalati tulajdonú iOS-eszközök esetén használható.

## <a name="supported-platforms"></a>Támogatott platformok

- iOS 9.3 és újabb verziók

Ez a funkció nem támogatott a következő rendszereken: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Az Elveszett mód engedélyezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **Eszközök**, majd a **Minden eszköz** lehetőséget.
4. A felügyelt eszközök listájából válasszon ki egy iOS-eszközt, és válassza a **...További** lehetőséget. Majd válassza az **Elveszett eszköz** távoli műveletet.
5. Az **Elveszett eszköz** területen aktiválja a funkciót. Ezután írja be a megjelenítendő üzenetet, és adjon meg egy kapcsolatfelvételi telefonszámot.
6. Válassza ki **OK** a módosítások mentéséhez.

Az Elveszett eszköz mód engedélye teljesen letiltja az eszköz használatát. A végfelhasználó az Elveszett eszköz mód kikapcsolásáig nem tud hozzáférni az eszközhöz. Ha az Elveszett eszköz mód engedélyezve van, az [Eszköz megkeresése](device-locate.md) művelettel meghatározhatja az eszköz földrajzi helyét.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Az Elveszett eszköz módhoz és az eszközkeresési műveletekhez tartozó biztonsági és adatvédelmi tudnivalók
- A művelet elindításáig a rendszer semmilyen információt nem küld az Intune-nak az eszköz helyéről.
- Az eszközkeresési művelet használatakor a rendszer az eszköz szélességi és hosszúsági koordinátáit elküldi az Intune-nak, és ezeket az adatokat megjeleníti az Azure Portalon.
- A rendszer 24 óráig tárolja az adatokat, majd törli azokat. A helyadatokat manuálisan nem lehet eltávolítani.
- A helyadatok tároláskor és továbbításkor egyaránt titkosítva vannak.
- A zárolási képernyőn megjelenítendő üzenet megadásakor mindenképp jelezze, hogy miként lehet visszaszolgáltatni az elveszett eszközt.

## <a name="next-steps"></a>További lépések

Az Elveszett eszköz mód aktiválásának állapotát az **Eszközök** > **Eszközműveletek** lehetőség választásával tekintheti meg.
