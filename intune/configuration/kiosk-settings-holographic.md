---
title: Kioszk-beállítások Windows holografikus for Business rendszerhez a Microsoft Intune-Azure-ban | Microsoft Docs
description: Konfigurálhatja a Windows holografikus for Business-eszközöket Egyalkalmazásos és többalkalmazásos kioszkként, testreszabhatja a Start menüt, alkalmazásokat adhat hozzá, megjelenítheti a tálcán, és konfigurálhat egy webböngészőt Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9318651dabcc93ef194c82b81b43fb25b98fb32
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730583"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Windows holografikus for Business-eszközbeállítások az Intune-ban való futtatáshoz

Windows Holographic for Business rendszerű eszközök egyalkalmazásos vagy többalkalmazásos kioszkmódban való használatra is konfigurálhatók. Bizonyos funkciókat a Windows Holographic for Business nem támogat.

Ez a cikk felsorolja és leírja azokat a beállításokat, amelyeket a Windows holografikus for Business rendszerű eszközökön szabályozhat. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal konfigurálhatja a Windows holografikus for Business-eszközöket kioszk módban történő futtatásra.

Intune-rendszergazdaként ezeket a beállításokat az eszközökhöz is létrehozhatja és hozzárendelheti.

Az Intune Windows kioszk szolgáltatásával kapcsolatos további tudnivalókért tekintse meg a [kioszk beállításainak konfigurálása](kiosk-settings.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Hozza létre a profilt](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Egyetlen teljes képernyős alkalmazásos kioszkok

Egyalkalmazásos kioszk mód választásakor adja meg a következő beállításokat:

- **Felhasználói bejelentkezés típusa**: Válassza a **helyi felhasználói fiók** lehetőséget, ha meg szeretné adni a helyi (eszköz) felhasználói fiókot vagy a kioszk alkalmazáshoz társított Microsoft-FIÓKOT (MSA-fiókot). Az **Automatikus bejelentkezésű** felhasználói fiókokat a Windows Holographic for Business nem támogatja.

- **Alkalmazás típusa**: Válassza az **áruházbeli alkalmazás**lehetőséget.

- Teljes **képernyős módban futtatandó alkalmazás**: Válassza az **áruházbeli alkalmazás hozzáadása**lehetőséget, és válasszon egy alkalmazást a listából.

    Nincsenek alkalmazások a listában? Adjon hozzá néhányat az [Ügyfélalkalmazások](../apps/apps-add.md) rész lépéseinek használatával.

    Válassza ki **OK** a módosítások mentéséhez.

## <a name="multi-app-kiosks"></a>Többalkalmazásos kioszk

Az ebben az üzemmódban lévő alkalmazások elérhetők a Start menüben. A felhasználó kizárólag ezeket az alkalmazásokat tudja megnyitni. Többalkalmazásos kioszk mód választásakor adja meg a következő beállításokat:

- **Windows 10 megcélzása S módú eszközökön**: Válassza a **nem**lehetőséget. Az S mód nem támogatott a Windows holografikus vállalatnál.

- **Felhasználói bejelentkezés típusa**: Vegyen fel legalább egy olyan felhasználói fiókot, amely használhatja a hozzáadott alkalmazásokat. A választható lehetőségek: 

  - **Automatikus bejelentkezés**: A Windows holografikus for Business esetében nem támogatott.
  - **Helyi felhasználói fiókok**: **Adja hozzá** a helyi (eszköz) felhasználói fiókot. A megadott fiókkal történik a bejelentkezés a kioszkba.
  - **Azure ad-felhasználó vagy-csoport (Windows 10, 1803-es és újabb verziók)** : Felhasználói hitelesítő adatok szükségesek az eszközre való bejelentkezéshez. Válassza a **Hozzáadás** lehetőséget Azure AD-felhasználók vagy -csoportok kiválasztására a listából. Több felhasználót és csoportot is kiválaszthat. A módosítások mentéséhez válassza az **Választ** gombot.
  - **HoloLens-látogató**: A látogatói fiók egy olyan vendégfiók, amely nem igényel felhasználói hitelesítő adatokat vagy hitelesítést a [megosztott számítógépes üzemmód fogalmai](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)című témakörben leírtak szerint.

- **Alkalmazások**: Adja hozzá az alkalmazásokat a kioszk eszközön való futtatáshoz. Ne feledje, hogy több alkalmazást is hozzáadhat.

  - **Áruházbeli alkalmazások hozzáadása**: Válasszon ki egy meglévő alkalmazást, amelyet az Intune-ba telepített vagy üzembe [helyezett, például](../apps/apps-add.md)üzletági alkalmazásokat. Ha nem rendelkezik a felsorolt alkalmazásokkal, az Intune számos, az [Intune-ban hozzáadott](../apps/store-apps-windows.md) [típusú alkalmazást](../apps/apps-add.md) támogat.
  - **Win32-alkalmazás hozzáadása**: A Windows holografikus for Business esetében nem támogatott.
  - **Hozzáadás AUMID szerint**: Ezzel a beállítással adhat hozzá beérkezett fájlok Windows-alkalmazásokat. Adja meg a következő tulajdonságokat: 

    - **Alkalmazás neve**: Kötelező. Adjon nevet az alkalmazásnak.
    - **Alkalmazás felhasználói modell azonosítója (AUMID)** : Kötelező. Adja meg a Windows-alkalmazás alkalmazásfelhasználói modellben használt azonosítóját. Az azonosító a [Telepített alkalmazás alkalmazásfelhasználói modellben használt azonosítójának megkeresése](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) című témakörben leírtak alapján kereshető meg.
    - **Csempe mérete**: Kötelező. Válassza a Kicsi, Közepes, Széles és Nagy alkalmazáscsempe-méretek egyikét.

- Teljes **képernyős böngésző beállításai**: A Windows holografikus for Business esetében nem támogatott.

- **Alternatív indítási elrendezés használata**: Válassza az **Igen** lehetőséget egy olyan XML-fájl megadásához, amely leírja, hogyan jelennek meg az alkalmazások a Start menüben, beleértve az alkalmazások sorrendjét is. Használja ezt a beállítást, ha több testreszabási lehetőségre van szüksége a Start menüben. A [Start menü elrendezésének testreszabása és exportálása](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) című cikk nyújt némi útmutatást, és tartalmaz egy kimondottan Windows Holographic for Business rendszerű eszközökhöz készült XML-fájlt.

- **Windows tálca**: A Windows holografikus for Business esetében nem támogatott.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az [Android](device-restrictions-android.md#kiosk), az [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)és a [Windows 10 és újabb rendszerű](kiosk-settings-windows.md) eszközök számára is létrehozhat kioszk-profilokat.
