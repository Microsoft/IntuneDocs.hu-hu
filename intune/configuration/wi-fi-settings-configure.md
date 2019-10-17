---
title: Wi-Fi-profil létrehozása az eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Itt láthatja a Wi-Fi eszközkonfigurációs profilok Microsoft Intune-ban való létrehozásának lépéseit. Profilok létrehozása Android, Android Enterprise, Android kioszk, iOS, macOS, Windows 10 és újabb rendszerekhez, valamint Windows holografikus for Business. Ezekkel a profilokkal Wi-Fi-kapcsolatot hozhat létre tanúsítványok használatához, EAP-típus és hitelesítési módszer kiválasztásához, proxy engedélyezéséhez és egyebekhez.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a794d724fe162ad7d464760661fecb45bd874431
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506452"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Wi-Fi-beállítások hozzáadása és használata az eszközökön a Microsoft Intune-ban

A Wi-Fi olyan vezeték nélküli hálózat, amelyet számos mobileszköz használ a hálózati hozzáféréshez. A Microsoft Intune beépített Wi-Fi-beállításokat tartalmaz, amelyek a szervezet felhasználóira és eszközeire telepíthetők. A beállítások ezt a csoportját "profilnak" nevezzük, és különböző felhasználókhoz és csoportokhoz rendelhetők. A hozzárendelést követően a felhasználók anélkül férhetnek hozzá a szervezet Wi-Fi hálózatához, hogy azt maguknak kellene konfigurálniuk.

Tegyük fel például, hogy egy új, Contoso Wi-Fi nevű vezeték nélküli hálózatot helyez üzembe. Ekkor szeretné beállítani, hogy az összes iOS-eszköz kapcsolódjon ehhez a hálózathoz. Ennek folyamata a következő:

1. Hozzon létre egy Wi-Fi profilt, amely tartalmazza a contoso Wi-Fi vezeték nélküli hálózathoz csatlakozó beállításokat.
2. Rendelje hozzá a profilt egy olyan csoporthoz, amely az iOS-eszközök összes felhasználóját tartalmazza.
3. A felhasználók az eszközükön a vezeték nélküli hálózatok listájában találják az új Contoso Wi-Fi-hálózatot. Ezután az Ön által kiválasztott hitelesítési módszerrel csatlakozhatnak a hálózathoz.

Ez a cikk a Wi-Fi-profil létrehozásának lépéseit sorolja fel. Emellett olyan hivatkozásokat is tartalmaz, amelyek leírják az egyes platformok különböző beállításait.

## <a name="supported-device-platforms"></a>Támogatott eszközplatformok

A Wi-Fi-profilok a következő eszközplatformokat támogatják:

- Android 4 és újabb verziók
- Android Enterprise és kioszk
- iOS 8.0 és újabb verziók
- macOS X 10,11 és újabb verziók
- Windows 10 vagy újabb, Windows 10 Mobile és Windows Holographic for Business

> [!NOTE]
> A Windows 8.1-et futtató eszközökön importálhatja egy másik eszköz korábban exportált Wi-Fi-konfigurációját.

## <a name="create-a-device-profile"></a>Eszközprofil létrehozása

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ban válassza az **eszköz konfigurációja** > **profilok** > **profil létrehozása**lehetőséget.
2. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profilnév például a **teljes vállalat Wi-Fi profilja**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza ki az eszközök platformját. A választható lehetőségek:

      - **Android--**
      - **Android Enterprise**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows 8.1 és újabb verziók**
      - **Windows 10 és újabb**

    - **Profil típusa**: válassza a **Wi-Fi**lehetőséget.

      > [!TIP]
      >
      > - A dedikált eszközként (kioszk) futó **androidos vállalati** eszközök esetén válassza az **eszköz tulajdonosa csak** > **Wi-Fi**lehetőséget.
      > - A **Windows 8.1 és újabb** rendszereken a **Wi-Fi-importálás** lehetőséget választhatja. Ez lehetővé teszi, hogy XML-fájlként importálhasson egy másik eszközről korábban exportált Wi-Fi-beállításokat.

3. Egyes Wi-Fi-beállítások minden platformon eltérnek. Egy adott platform beállításainak megtekintéséhez válassza ki a platformot:

    - [Android--](wi-fi-settings-android.md)
    - [Android Enterprise](wi-fi-settings-android-enterprise.md), beleértve a dedikált eszközöket
    - [iOS/iPadOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 és újabb](wi-fi-settings-windows.md)
    - [Windows 8.1 és újabb](wi-fi-settings-import-windows-8-1.md) (beleértve a Windows Holographic for Businesst is)

4. Ha elkészült, válassza a **create profile** > **Létrehozás**elemet.

Ekkor létrejön a profil, és megjelenik a profilok listában (az**eszköz konfigurációja** > **profilok**).

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. Ezután [rendelje hozzá ezt a profilt](device-profile-assign.md) , és [Figyelje annak állapotát.](device-profile-monitor.md)
