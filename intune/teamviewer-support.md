---
title: Eszközök távoli felügyelete a Microsoft Intune-ban – Azure | Microsoft Docs
description: Áttekintés a TeamViewer használatához szükséges szerepkörökről, és a TeamViewer-összekötő telepítéséről, valamint lépésenkénti útmutató eszközök távoli felügyeletéhez a Microsoft Intune használatával az Azure Portalon
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b39c9f4f875ca458817940819716e1188d36eef
ms.sourcegitcommit: e6edfbfd63dd7c2500ce1123205aa2af9a7e8e2e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/05/2019
ms.locfileid: "68783253"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>A TeamViewer használata Intune-eszközök távoli felügyeletéhez

Az Intune által kezelt eszközök a [TeamViewer](https://www.teamviewer.com) használatával felügyelhetők távolról. A TeamViewer külső szállítótól származó, külön megvásárolható program. Ez a témakör bemutatja, hogyan konfigurálható a TeamViewer az Intune-ban, és hogyan felügyelhető távolról egy eszköz. 

## <a name="prerequisites"></a>Előfeltételek

- Használjon támogatott eszközt. Az Intune által felügyelt Android-eszköz rendszergazdája, androidos munkahelyi profil, Windows, iOS és macOS rendszerű eszközök támogatják a távoli felügyeletet. A TeamViewer nem feltétlenül támogatja a Windows Holographic (HoloLens), Windows Team (Surface Hub), vagy Windows 10 S rendszerű eszközöket. A támogatással kapcsolatban tekintse át a [TeamViewer](https://www.teamviewer.com) frissítéseit.

> [!NOTE]
> Az Android dedikált és teljes körűen felügyelt funkciója nem támogatott.

- Az Azure Portal-beli Intune rendszergazdának a következő [Intune-szerepkörökkel](role-based-access-control.md) kell rendelkeznie:  

  - **Távsegítség frissítése**: Lehetővé teszi a rendszergazdák számára a TeamViewer-összekötő beállításainak módosítását
  - **Távsegítség kérése**: Lehetővé teszi, hogy a rendszergazdák új Távsegítség-munkamenetet indítsanak bármely felhasználó számára. Az ezzel a szerepkörrel rendelkező felhasználókat nem korlátozzák a hatókörön belüli Intune-szerepkörök. A hatókörön belüli Intune-szerepkörhöz rendelt felhasználói vagy eszközcsoportok szintén kérhetnek távsegítséget. 

- Egy [TeamViewer](https://www.teamviewer.com) -fiók a bejelentkezési hitelesítő adatokkal. Csak néhány TeamViewer-licenc támogatja az Intune-nal való integrációt. Adott TeamViewer-igények esetén lásd [: TeamViewer Integration partner: Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/).

A TeamViewer használatával engedélyezi a TeamViewer for Intune összekötőjének TeamViewer-munkamenetek létrehozását, Active Directory-adatok olvasását és a TeamViewer-fiók hozzáférési jogkivonatának mentéset.

## <a name="configure-the-teamviewer-connector"></a>A TeamViewer-összekötő konfigurálása

Ahhoz, hogy távsegítséget nyújthasson eszközökre, az alábbi lépéseket követve konfigurálja az Intune TeamViewer-összekötőt:

1. Az [Azure Portalon](https://portal.azure.com) válassza a **Minden szolgáltatás** lehetőséget, majd keresse meg a **Microsoft Intune** elemet.
2. A **Microsoft Intune** alatt válassza az **Eszközök**, majd a **TeamViewer-összekötő** elemet.
3. Válassza a **Kapcsolódás** lehetőséget, és fogadja el a licencszerződést.
4. Válassza **Az engedélyezéshez jelentkezzen be a TeamViewer szolgáltatásba** lehetőséget.
5. Ekkor megnyílik a TeamViewer webhelyének egyik oldala. A TeamViewer-licenc hitelesítő adatainak megadását követően válassza a **Bejelentkezés** lehetőséget.

## <a name="remotely-administer-a-device"></a>Eszközök távoli felügyelete

Az összekötő konfigurálása után megkezdheti egy eszköz távoli felügyeletét. Hajtsa végre a következő lépéseket: 

1. Az [Azure Portalon](https://portal.azure.com) válassza a **Minden szolgáltatás** lehetőséget, majd keresse meg a **Microsoft Intune** elemet.
2. A **Microsoft Intune** alatt válassza az **Eszközök**, majd a **Minden eszköz** elemet.
3. Jelölje ki a listában a távolról felügyelni kívánt eszközt. Az eszköz tulajdonságainál válassza az **Új távsegítség munkamenet** lehetőséget.
4. Miután az Intune kapcsolódott a TeamViewer szolgáltatáshoz, látni fog némi információt az eszközről. A **Kapcsolódás** lehetőséggel indítsa el a távoli munkamenetet.

![Androidos eszköz távoli felügyelet a TeamViewer használatával – példa](./media/android-teamviewer.png)

Amikor elindít egy távoli munkamenetet, a felhasználók egy értesítési jelzőt látnak az eszközön Céges portál alkalmazás ikonján. Az alkalmazás megnyitásakor is megjelenik egy értesítés. A felhasználók ezután elfogadják a Távsegítség kérését.

> [!NOTE]
> A "felhasználó nélkül" metódusokkal beléptetett Windows-eszközök, mint például a DEM és a WCD, nem jelenítik meg a TeamViewer-értesítést a Céges portál alkalmazásban. Ezekben a forgatókönyvekben ajánlott a TeamViewer portál használatával előállítani a munkamenetet.

A TeamViewerben sokféle művelet, például az eszköz felügyeletének átvétele is végrehajtható az eszközön. Az elvégezhető tevékenységek teljes körű ismertetését a [TeamViewer útmutató](https://www.teamviewer.com/support/documents/) tartalmazza.

Ha végzett, zárja be a TeamViewer ablakot.
