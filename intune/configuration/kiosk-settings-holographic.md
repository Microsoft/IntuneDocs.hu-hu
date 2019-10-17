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
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e555c62030cede57e98e34034367831c298c0ced
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492398"
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

- **Felhasználói bejelentkezés típusa**: Válassza a **Helyi felhasználói fiók** lehetőséget, és adja meg a kioszkalkalmazáshoz társított helyi (eszközön létező) felhasználói fiókot vagy Microsoft Account (MSA) fiókot. Az **Automatikus bejelentkezésű** felhasználói fiókokat a Windows Holographic for Business nem támogatja.

- **Alkalmazástípus**: Válassza az **Áruházbeli alkalmazás** lehetőséget.

- **Kioszkmódban futtatni kívánt alkalmazás**: Válassza az **Áruházbeli alkalmazás hozzáadása** lehetőséget, és válasszon alkalmazást a listából.

    Nincsenek alkalmazások a listában? Adjon hozzá néhányat az [Ügyfélalkalmazások](../apps/apps-add.md) rész lépéseinek használatával.

    A módosítások mentéséhez válassza az **OK** gombot.

## <a name="multi-app-kiosks"></a>Többalkalmazásos kioszk

Az ebben az üzemmódban lévő alkalmazások elérhetők a Start menüben. A felhasználó kizárólag ezeket az alkalmazásokat tudja megnyitni. Többalkalmazásos kioszk mód választásakor adja meg a következő beállításokat:

- **S módú Windows 10-es eszközök megcélzása**: válassza a **Nem** lehetőséget. Az S mód nem támogatott a Windows holografikus vállalatnál.

- **Felhasználói bejelentkezés típusa**: Adjon meg egy vagy több olyan felhasználói fiókot, amely jogosult a társított alkalmazások használatára. A választható lehetőségek: 

  - **Automatikus bejelentkezés**: A Windows Holographic for Business nem támogatja.
  - **Helyi felhasználói fiókok**: **Adja hozzá** a helyi (az eszközön létező) felhasználói fiókot. A megadott fiókkal történik a bejelentkezés a kioszkba.
  - **Azure AD-felhasználó vagy csoport (Windows 10, 1803-as vagy újabb verzió)** : Felhasználói hitelesítő adatok szükségesek az eszközre való bejelentkezéshez. Válassza a **Hozzáadás** lehetőséget Azure AD-felhasználók vagy -csoportok kiválasztására a listából. Több felhasználót és csoportot is kiválaszthat. A módosítások mentéséhez válassza az **Választ** gombot.
  - **HoloLens vendég**: Ehhez a vendégfiókhoz [A megosztott számítógép üzemmód alapelvei](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts) című szakaszban ismertetettek alapján nem szükségesek hitelesítő adatok.

- **Alkalmazások**: Adja hozzá a kioszkmódú eszközön futtatandó alkalmazásokat. Ne feledje, hogy több alkalmazást is hozzáadhat.

  - **Áruházbeli alkalmazások hozzáadása**: válasszon ki egy meglévő alkalmazást, amelyet az Intune-ba [, az üzletági alkalmazásokat is](../apps/apps-add.md)beleértve. Ha nem rendelkezik a felsorolt alkalmazásokkal, az Intune számos, az [Intune-ban hozzáadott](../apps/store-apps-windows.md) [típusú alkalmazást](../apps/apps-add.md) támogat.
  - **Win32-alkalmazás hozzáadása**: a Windows Holographic for Business nem támogatja.
  - **Hozzáadás AUMID alapján**: használja ezt a beállítást a postaláda Windows-alkalmazások hozzáadásához. Adja meg a következő tulajdonságokat: 

    - **Alkalmazás neve**: Kötelező. Adjon nevet az alkalmazásnak.
    - **Alkalmazás alkalmazásfelhasználói modellben használt azonosítója (AUMID)** : Kötelező. Adja meg a Windows-alkalmazás alkalmazásfelhasználói modellben használt azonosítóját. Az azonosító a [Telepített alkalmazás alkalmazásfelhasználói modellben használt azonosítójának megkeresése](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) című témakörben leírtak alapján kereshető meg.
    - **Csempeméret**: Kötelező. Válassza a Kicsi, Közepes, Széles és Nagy alkalmazáscsempe-méretek egyikét.

- **Teljes képernyős böngésző beállításai**: a Windows Holographic for Business nem támogatja.

- **Start menü alternatív elrendezésének használata**: Válassza az **Igen** lehetőséget egy XML-fájl megadásához, amely meghatározza, hogyan jelenjenek meg az alkalmazások a Start menüben, beleértve azok sorrendjét. Használja ezt a beállítást, ha több testreszabási lehetőségre van szüksége a Start menüben. A [Start menü elrendezésének testreszabása és exportálása](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) című cikk nyújt némi útmutatást, és tartalmaz egy kimondottan Windows Holographic for Business rendszerű eszközökhöz készült XML-fájlt.

- **Windows Tálca**: a Windows Holographic for Business nem támogatja.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az [Android](device-restrictions-android.md#kiosk), az [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)és a [Windows 10 és újabb rendszerű](kiosk-settings-windows.md) eszközök számára is létrehozhat kioszk-profilokat.
