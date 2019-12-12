---
title: Oktatási beállítások hozzáadása vagy konfigurálása a Microsoft Intuneban – Azure | Microsoft Docs
description: A Windows 10-es és újabb rendszerű eszközökön a teszt alkalmazása eszköz konfigurációs profiljában a Microsoft Intune. Hozzon létre egy konfigurációs profilt az oktatási beállítások segítségével, és írja be a teszt alkalmazás URL-címét, válassza ki a felhasználók bejelentkezésének módját, figyelje a képernyőt a teszt során, és engedélyezze vagy tiltsa le a szöveges javaslatokat a teszt során.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be6cc64c3a65af72fd74bc58ed7c06a214797510
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059469"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>A teszt alkalmazás használata Windows 10-es eszközökön Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune-beli oktatási profilokat tanulók számára tervezték, hogy tesztet vagy vizsgát tegyenek az eszközökön. Ez a funkció magában foglalja a teszt-URL-cím hozzáadására szolgáló **tesztelési** alkalmazást és beállításokat, valamint azt, hogy a végfelhasználó Hogyan jelentkezzen be a tesztbe, és így tovább. Ez a funkció a következő platformot támogatja:

- Windows 10 és újabb

Amikor a felhasználó bejelentkezik, a teszt alkalmazás automatikusan megnyílik a megadott teszttel. Az eszközön semmilyen más alkalmazás nem futtatható, amíg a teszt folyamatban van. A [Windows 10 tesztelési](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) szolgáltatásával további részleteket tudhat meg a próbaverzió alkalmazásról.

Ez a cikk a Microsoft Intune eszköz konfigurációs profiljának létrehozásának lépéseit sorolja fel. Emellett információkat is tartalmaz a Windows 10-es eszközökhöz elérhető oktatási beállítások olvasásához és megismeréséhez.

## <a name="create-a-device-profile"></a>Eszközprofil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adja meg az új profil leíró nevét.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza a **Windows 10-es vagy újabb verzió** lehetőséget.
    - **Profil**: válassza az **oktatási profil**lehetőséget.

4. Adja meg a konfigurálni kívánt beállításokat:

    - [Windows 10 és újabb](education-settings-windows.md)

5. A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

A beállítások megadása és a profil létrehozása után a profil megjelenik a profilok listájában. A következő lépés a [profil hozzárendelése egyes csoportokhoz](device-profile-assign.md).

## <a name="next-steps"></a>További lépések

Tekintse meg a [Windows 10-es oktatási beállítások](education-settings-windows.md) listáját és azok leírását.

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
