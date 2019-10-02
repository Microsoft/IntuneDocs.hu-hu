---
title: A Microsoft eszközkorlátozásai az Intune-ban Windows 10 Team esetén
titleSuffix: ''
description: A Windows 10 Team-eszközökre vonatkozó eszközkorlátozások ismertetése.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35dbc39d01780f23dcc325a203d7a9c33b98e296
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730727"
---
# <a name="microsoft-intune-windows-10-team-device-restriction-settings"></a>A Windows 10 Team eszközkorlátozásokra vonatkozó beállításai a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikk bemutatja a Microsoft Intune olyan eszközkorlátozásokra vonatkozó beállításait, melyek konfigurálhatók Windows 10 Team-eszközökhöz.


## <a name="apps-and-experience"></a>Alkalmazások és felhasználói élmény

- **Képernyő felébresztése, ha valaki a helyiségben tartózkodik** – Lehetővé teszi az eszköz automatikus felébresztését, ha az érzékelők valakit észlelnek a helyiségben.
- **Üdvözlőképernyőn megjelenített értekezletadatok** – Ha engedélyezi ezt a lehetőséget, kiválaszthatja az üdvözlőképernyő Értekezletek csempéjén megjelenő adatokat. A következőket teheti:
  - **Csak szervező és időpont megjelenítése**
  - **Szervező, időpont és tárgy megjelenítése (zártkörű értekezletek esetén a tárgy rejtett)**
- **Üdvözlőképernyő háttérképének URL-címe** – A beállítás engedélyezésével egy egyéni hátteret jeleníthet meg a Windows 10 Team-eszközök **üdvözlőképernyőjén** a megadott URL-címről.<br>A képnek PNG formátumban kell lennie, és az URL-címnek a **https://** karakterlánccal kell kezdődnie.

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights** – A Microsoft Operations Manager csomag részét képező Azure Operational Insights összegyűjti, tárolja és elemzi a Windows 10 Team-eszközök naplófájladatait.
Az Azure-os Operational Insights szolgáltatáshoz végzett csatlakozáshoz meg kell adnia egy **munkaterület-azonosítót** és egy **munkaterületkulcsot**.

## <a name="maintenance"></a>Karbantartás

- **Frissítésre szolgáló karbantartási időszak** – Meghatározza, hogy mely időszakban kerülhet sor frissítésekre az eszközön. Konfigurálhatja az időszak **Kezdési időpontját** és **Időtartamát (óra)** (1 és 5 óra között).

## <a name="wireless-projection"></a>Vezeték nélküli kivetítés

- **Vezeték nélküli kivetítéshez szükséges PIN-kód** – Meghatározza, hogy meg kell-e adni a PIN-kódot az eszköz vezeték nélküli vetítési képességeinek használata előtt.
- **Miracast vezeték nélküli vetítés** – A beállítás engedélyezésével lehetővé teheti a Windows 10 Team-eszköz számára a Miracast-kompatibilis eszközök használatát a vetítéshez.
- **Miracast vezeték nélküli kivetítési csatorna** – Válassza ki a kapcsolat létrehozásához használt Miracast-csatornát.


## <a name="next-steps"></a>További lépések

Olvassa el az [Eszközkorlátozási profilok konfigurálása](../device-restrictions-configure.md) szakaszt a profil mentéséhez, majd hozzárendeléséhez a felhasználók és eszközök számára.
