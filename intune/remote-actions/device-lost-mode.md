---
title: IOS/iPadOS elveszett mód aktiválása az Microsoft Intune-Azure-val | Microsoft Docs
description: Az elveszett mód bekapcsolásával vagy elindításával testreszabhatja az elveszett vagy ellopott iOS/iPadOS eszközök zárolási képernyőjén megjelenő üzeneteket Microsoft Intune használatával. Emellett az Elveszett eszköz mód használatakor biztonsági és adatvédelmi információkat is kaphat.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a4103c819c0d4bd377b9c6ab2359cb7465cdd9c
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415599"
---
# <a name="enable-lost-mode-on-iosipados-devices-with-intune"></a>Elveszett mód engedélyezése iOS-vagy iPadOS-eszközökön az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az **elveszett eszköz mód** művelettel engedélyezheti az elveszett üzemmódot az elveszett vagy ellopott iOS/iPadOS eszközökön. Ebben a módban megadható egy üzenet és egy telefonszám, amely megjelenik az eszköz zárolási képernyőjén. Az elveszett mód használatához az eszköznek felügyelt módban lévő, vállalati tulajdonú iOS-/iPadOS-eszköznek kell lennie.

## <a name="supported-platforms"></a>Támogatott platformok

- iOS/iPadOS 9,3 és újabb verziók

Ez a funkció nem támogatott a következő rendszereken: 
- Windows
- Windows Phone
- macOS
- Android:

## <a name="enable-lost-mode"></a>Az Elveszett mód engedélyezése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Kattintson az **Eszközök**, majd a **Minden eszköz** elemre.
4. A felügyelt eszközök listájából válassza ki az iOS/iPadOS eszközt, majd válassza az **elveszett módot (csak felügyelt**eszköz esetén).
5. Az **elveszett mód**területen válassza az **Engedélyezés**lehetőséget.
6. A **zárolási képernyőn megjelenítendő üzenetben**írja be az eszköz zárolási képernyőjén megjelenítendő üzenetet.
7. Szükség esetén megadhat egy telefonszámot a **megjelenítendő** telefonszám mezőben.
6. A módosítások mentéséhez kattintson az **OK** gombra.

Az Elveszett eszköz mód engedélye teljesen letiltja az eszköz használatát. A végfelhasználó az Elveszett eszköz mód kikapcsolásáig nem tud hozzáférni az eszközhöz. Ha az Elveszett eszköz mód engedélyezve van, az [Eszköz megkeresése](device-locate.md) művelettel meghatározhatja az eszköz földrajzi helyét.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Az Elveszett eszköz módhoz és az eszközkeresési műveletekhez tartozó biztonsági és adatvédelmi tudnivalók
- A művelet elindításáig a rendszer semmilyen információt nem küld az Intune-nak az eszköz helyéről.
- Az eszközkeresési művelet használatakor a rendszer az eszköz szélességi és hosszúsági koordinátáit elküldi az Intune-nak, és ezeket az adatokat megjeleníti az Azure Portalon.
- A rendszer 24 óráig tárolja az adatokat, majd törli azokat. A helyadatokat manuálisan nem lehet eltávolítani.
- A helyadatok tároláskor és továbbításkor egyaránt titkosítva vannak.
- A zárolási képernyőn megjelenítendő üzenet megadásakor mindenképp jelezze, hogy miként lehet visszaszolgáltatni az elveszett eszközt.

## <a name="next-steps"></a>További lépések

Az Elveszett eszköz mód aktiválásának állapotát az **Eszközök** > **Eszközműveletek** lehetőség választásával tekintheti meg.
