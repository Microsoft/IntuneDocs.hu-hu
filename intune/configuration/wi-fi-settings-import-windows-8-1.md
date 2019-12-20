---
title: Wi-Fi-beállítások importálása Windows 10-es eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Windows-eszközök Wi-Fi-beállításainak exportálása XML-fájlba a netsh wlan használatával. Ezután a fájl Intune-ba történő importálásával létrehozhat egy Wi-Fi-profilt a Windows 8.1, Windows 10 és Windows Holographic for Business rendszerű eszközökhöz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207009"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Windows-eszközök Wi-Fi-beállításainak importálása az Intune-ba

A Windows rendszert futtató eszközökre importálhatja az előzőleg fájlba exportált Wi-Fi konfigurációs profilt. **Windows 10 és újabb rendszerű eszközökhöz közvetlenül az Intune-ban is [létrehozhat Wi-Fi-profilt](wi-fi-settings-windows.md)**.

A következőkre vonatkozik:  
- Windows 8.1 és újabb
- Windows 10 és újabb
- A Windows 10 asztali vagy mobilverziója
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Wi-Fi beállítások exportálása windowsos eszközről

A Windows rendszerben a `netsh wlan` használatával az Intune által is olvasható XML-fájlba exportálhat egy meglévő Wi-Fi-profilt. A kulcsot egyszerű szöveges formátumban kell exportálnia a profil sikeres használatához.

A szükséges Wi-Fi-profillal már rendelkező Windows-számítógépen kövesse az alábbi lépéseket:

1. Hozzon létre egy helyi mappát az exportált Wi-Fi profilok, például a **c:\WiFi**számára.
2. Nyisson meg egy parancssort rendszergazdaként.
3. Futtassa az `netsh wlan show profiles` parancsot. Jegyezze fel az exportálni kívánt profil nevét. Ebben a példában a profil neve: **WiFiName**.
4. Futtassa az `netsh wlan export profile name="ProfileName" folder=c:\Wifi` parancsot. Ezzel létrehozza a **Wi-Fi-WiFiName.xml** nevű Wi-Fi-profilfájlt a célmappában.

## <a name="import-the-wi-fi-settings-into-intune"></a>Wi-Fi-beállítások importálása az Intune-ba

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. A névnek **meg kell egyeznie** a Wi-Fi-profil XML-fájljában található névattribútummal. Ellenkező esetben sikertelen lesz a művelet.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **Platform**: válassza **a Windows 8,1 és újabb**lehetőséget.
    - **Profil típusa**: válassza a **Wi-Fi importálás**lehetőséget.

    > [!IMPORTANT]
    > - Ha előmegosztott kulcsot tartalmazó Wi-Fi-profilt exportál, akkor **mindenképp** hozzá kell adnia a `key=clear` kapcsolót a parancshoz. Például írja be a következőt: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`.
    > - Ha egy előmegosztott kulcsot használ a Windows 10 rendszerben, szervizelési hiba jelenik meg az Intune-ban. E hiba megjelenésekor a Wi-Fi-profilt a rendszer megfelelően hozzárendeli az eszközhöz, és a profil a várt módon fog működni.
    > - Az előmegosztott kulcsot tartalmazó Wi-Fi-profilok exportálásakor gondoskodjon a fájlok védelméről. A kulcs egyszerű szövegként szerepel, ezért az Ön felelőssége a kulcs védelme.

4. Adja meg a következő beállításokat:

    - **Kapcsolat neve**: Adja meg a Wi-Fi-kapcsolat nevét. Ez a név jelenik meg a felhasználók számára az elérhető Wi-Fi-hálózatok tallózásával.
    - **Profil XML-** fájlja: válassza a Tallózás gombot, és válassza ki azt az XML-fájlt, amely az importálni kívánt Wi-Fi profil beállításait tartalmazza.
    - **Fájl tartalma**: Megjeleníti a kiválasztott konfigurációs profil XML-kódját.

5. A módosítások mentéséhez válassza az **OK** gombot.
6. Ha elkészült, válassza az **OK** > **Létrehozás** lehetőséget az Intune-profil létrehozásához. Ha elkészült, a profil megjelenik az **eszközök – konfigurációs profilok** listában.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Tekintse meg a [Wi-Fi beállítások áttekintését](wi-fi-settings-configure.md), beleértve a többi elérhető platformot is.
