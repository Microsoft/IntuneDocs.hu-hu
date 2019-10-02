---
title: A Windows és a holografikus eszközök kioszk-beállításai a Microsoft Intune-Azure-ban | Microsoft Docs
description: Konfigurálhatja a Windows 10 (és újabb) és a Windows holografikus for Business eszközöket egyetlen alkalmazásként és többalkalmazásos kioszkként, testreszabhatja a Start menüt, alkalmazásokat adhat hozzá, megjelenítheti a tálcán, és konfigurálhat egy webböngészőt a Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19641a36cf429773a8c0e06a90ee279d2baa06f7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730575"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Windows 10 és Windows holografikus for Business eszközök beállításai dedikált kioszkként való futtatáshoz az Intune használatával

Windows 10 rendszerű eszközökön az Intune-nal kioszkként futtathat eszközöket, más néven dedikált eszközként. Az eszköz teljes képernyős módban futtathat egy alkalmazást, vagy futtathat számos alkalmazást. Megtekintheti és testreszabhatja a Start menüt, különböző alkalmazásokat adhat hozzá, beleértve a Win32 alkalmazásokat, hozzáadhat egy adott kezdőlapot egy webböngészőhöz, és így tovább. 

Ez a funkció a következő rendszert futtató eszközökre vonatkozik:

- Windows 10 és újabb
- Windows Holographic for Business

Az Intune eszközönként egy kioszkprofilt támogat. Ha egy adott eszközön több kioszkprofilra van szüksége, használhat egy [egyéni OMA-URI](custom-settings-windows-10.md)-t.

Az Intune a "konfigurációs profilok" használatával hozza létre és szabja testre ezeket a beállításokat a szervezet igényeinek megfelelően. Miután hozzáadta ezeket a szolgáltatásokat egy profilhoz, leküldheti vagy telepítheti ezeket a beállításokat a szervezeten belüli csoportokra.

Ez a cikk bemutatja, hogyan hozhat létre egy eszköz-konfigurációs profilt. Az összes beállítás listáját és azok leírását a [Windows 10 kioszk beállításai](kiosk-settings-windows.md) és [a Windows holografikus vállalati kioszk beállításai](kiosk-settings-holographic.md)című témakörben tekintheti meg.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

   - **Név**: Adjon meg egy leíró nevet az új profilhoz.
   - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
   - **Platform**: Válassza **a Windows 10 és újabb** lehetőséget.
   - **Profil típusa**: **Kioszk** kiválasztása

4. A **Beállítások**területen válasszon ki egy teljes **képernyős módot**. A **Kioszkmód** azonosítja a szabályzat által támogatott teljes képernyős mód típusát. A lehetőségek a következők:

    - **Nincs konfigurálva** (alapértelmezett): A házirend nem engedélyezi a kioszk üzemmódot.
    - **Egyetlen alkalmazás, teljes képernyős kioszk**: Az eszköz egyetlen felhasználói fiókként fut, és egyetlen áruházbeli alkalmazásba zárolja. Ezért, amikor a felhasználó bejelentkezik, elindul az adott alkalmazás. Ez a mód emellett meggátolja a felhasználót abban, hogy új alkalmazásokat nyisson meg vagy másik futó alkalmazásra váltson.
    - **Több alkalmazás kioszkja**: Az eszköz több áruházbeli alkalmazást, Win32 alkalmazást vagy beérkezett Windows-alkalmazást futtat az alkalmazás felhasználói modell azonosítója (AUMID) használatával. Az eszközön csak a hozzáadott alkalmazások lesznek elérhetők.

        A többalkalmazásos kioszk (vagy fix célú eszköz) előnye az, hogy egy olyan, könnyen érthető környezetet nyújt a felhasználóknak, amelyben csak a szükséges alkalmazások érhetőek el. A szükségtelen alkalmazásokat pedig elrejti.

    Az összes beállítás listáját és a teendőket lásd:
      - [A Windows 10-es kioszk beállításai](kiosk-settings-windows.md)
      - [Windows holografikus vállalati kioszk beállításai](kiosk-settings-holographic.md)

5. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. 

Ekkor létrejön a profil, és megjelenik a profilok listájában. Ezután [rendelje hozzá](device-profile-assign.md) a profilt.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

A következő platformokat futtató eszközökhöz kioszk-profilokat hozhat létre:
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 és újabb](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
