---
title: Wi-Fi-beállítások importálása Windows 10-es eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Windows-eszközök Wi-Fi-beállításainak exportálása XML-fájlba a netsh wlan használatával. Ezután a fájl Intune-ba történő importálásával létrehozhat egy Wi-Fi-profilt a Windows 8.1, Windows 10 és Windows Holographic for Business rendszerű eszközökhöz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 841be002cf9ed99142ce95a1f9cafda761d1b856
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730355"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Windows-eszközök Wi-Fi-beállításainak importálása az Intune-ba

A Windows rendszert futtató eszközökre importálhatja az előzőleg fájlba exportált Wi-Fi konfigurációs profilt. **Windows 10 és újabb rendszerű eszközökhöz közvetlenül az Intune-ban is [létrehozhat Wi-Fi-profilt](wi-fi-settings-windows.md)** .

Érintett kiadások:  
- Windows 8.1 és újabb
- Windows 10 és újabb
- A Windows 10 asztali vagy mobilverziója
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Wi-Fi beállítások exportálása windowsos eszközről

A Windows rendszerben a `netsh wlan` használatával az Intune által is olvasható XML-fájlba exportálhat egy meglévő Wi-Fi-profilt. A kulcsot egyszerű szöveges formátumban kell exportálnia a profil sikeres használatához.

A szükséges Wi-Fi-profillal már rendelkező Windows-számítógépen kövesse az alábbi lépéseket:

1. Hozzon létre egy helyi mappát az exportált W-Fi-profilokhoz, például a **c:\WiFi** mappát.
2. Nyisson meg egy parancssort rendszergazdaként.
3. Futtassa a `netsh wlan show profiles` parancsot, és jegyezze fel az exportálni kívánt profil nevét. Ebben a példában a profil neve: **WiFiName**.
4. Futtassa a `netsh wlan export profile name="ProfileName" folder=c:\Wifi` parancsot. Ezzel létrehozza a **Wi-Fi-WiFiName.xml** nevű Wi-Fi-profilfájlt a célmappában.

## <a name="import-the-wi-fi-settings-into-intune"></a>Wi-Fi-beállítások importálása az Intune-ba

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg az eszközkorlátozási profil nevét és leírását a **Név** és a **Leírás** mezőben.

    > [!IMPORTANT]
    > - A névnek **meg kell egyeznie** a Wi-Fi-profil XML-fájljában található névattribútummal. Ellenkező esetben sikertelen lesz a művelet.
    > - Ha előmegosztott kulcsot tartalmazó Wi-Fi-profilt exportál, akkor **mindenképp** hozzá kell adnia a `key=clear` kapcsolót a parancshoz. Például írja be a következőt: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`.
    > - Az előmegosztott kulcsok Windows 10 rendszerben való használata szervizelési hiba megjelenéséhez vezet az Intune-ban. E hiba megjelenésekor a Wi-Fi-profilt a rendszer megfelelően hozzárendeli az eszközhöz, és a profil a várt módon fog működni.
    > - Az előmegosztott kulcsot tartalmazó Wi-Fi-profilok exportálásakor gondoskodjon a fájlok védelméről. A kulcs egyszerű szövegként szerepel, ezért az Ön felelőssége a kulcs védelme.

4. A **Platform** beállításnál válassza a **Windows 8.1 és újabb** lehetőséget.
5. A **Profil típusa** beállításnál válassza a **Wi-Fi importálás** lehetőséget.
6. Adja meg a következő beállításokat:
    - **Kapcsolatok neve**: Adja meg a Wi-Fi kapcsolat nevét. Ez a név jelenik meg a végfelhasználók számára elérhető Wi-Fi-hálózatok böngészése közben.
    - **Profil XML-fájlja**: Válassza a Tallózás gombot, és válassza ki azt az XML-fájlt, amely az importálni kívánt Wi-Fi profil beállításait tartalmazza.
    - **Fájl tartalma**: Megjeleníti a kiválasztott konfigurációs profil XML-kódját.
7. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. A következő lépés a [profil hozzárendelése](device-profile-assign.md).

## <a name="more-resources"></a>További források

[Wi-Fi-beállítások áttekintése](wi-fi-settings-configure.md), beleértve a többi rendelkezésre álló platformot is.
