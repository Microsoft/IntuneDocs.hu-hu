---
title: Az eszközök funkcióinak korlátozása az Microsoft Intune az Azure-ban | Microsoft Docs
description: Az Android-, macOS-, iOS-, iPadOS-, Windows Phone-telefon-és Windows 10-es eszközökön található szolgáltatások korlátozásához vegyen fel egy eszköz-profilt Microsoft Intune
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
ms.openlocfilehash: b7b4597106d1fffb65f112feae750aa7c8feefc0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493985"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Ezközkorlátozásokra vonatkozó beállítások konfigurálása a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune olyan eszköz-korlátozási szabályzatokat tartalmaz, amelyek segítségével a rendszergazdák vezérelhetik az Android, iOS, macOS és Windows rendszerű eszközöket. Ezek a korlátozások lehetővé teszik a beállítások és szolgáltatások széles körének szabályozását a szervezet erőforrásainak megóvása érdekében. A rendszergazdák például a következőket tehetik:

- Az eszköz kamerájának engedélyezése vagy letiltása
- A Google Play, az alkalmazás-áruházak, a dokumentumok megtekintése és a játékok elérésének szabályozása
- Beépített alkalmazások blokkolása vagy a megengedett vagy tiltott alkalmazások listájának létrehozása
- Fájlok Felhőbeli és Storage-fiókba való biztonsági mentésének engedélyezése vagy letiltása
- Adja meg a jelszó minimális hosszát, és tiltsa le az egyszerű jelszavakat

Ezek a funkciók az Intune-ban érhetők el, és a rendszergazda konfigurálható. Az Intune a "konfigurációs profilok" használatával hozza létre és szabja testre ezeket a beállításokat a szervezet igényeinek megfelelően. Miután hozzáadta ezeket a funkciókat egy profilhoz, leküldheti vagy üzembe helyezheti a profilt a szervezet eszközein.

Ez a cikk bemutatja, hogyan hozhat létre egy eszköz-korlátozási profilt. A különböző platformokhoz elérhető összes beállítást is megtekintheti.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. Például egy jó szabályzat neve **iOS: a kamera letiltása az eszközökön**.
    - **Leírás**: adja meg a szabályzat leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza ki az eszközök platformját. A választható lehetőségek:  

        - **Android--**
        - **Vállalati Android**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 és újabb verziók**
        - **Windows 10 és újabb**

    - **Profil típusa**: válassza az **eszközök korlátozásait**.

        A Windows 10-es Team-eszközökhöz, például a Surface Hubhoz tartozó eszköz-korlátozási profil létrehozásához válassza az eszközök **korlátozásai (Windows 10 Team)** lehetőséget.

4. A kiválasztott platformtól függően a konfigurálható beállítások eltérőek. Válassza ki a platformot a részletes beállításokhoz:

    - [Android-beállítások](../device-restrictions-android.md)
    - [Androidos vállalati beállítások](../device-restrictions-android-for-work.md)
    - [iOS-/iPadOS-beállítások](device-restrictions-ios.md)
    - [macOS-beállítások](device-restrictions-macos.md)
    - [Windows Phone 8.1-beállítások](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10-beállítások](device-restrictions-windows-10.md)
    - [Windows 10 Team-beállítások](device-restrictions-windows-10-teams.md)
    - [A Windows Holographic for Business beállításai](device-restrictions-windows-holographic.md)

5. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

Ekkor létrejön a profil, és megjelenik a profilok listán.

## <a name="next-steps"></a>További lépések

A profil létrehozása után készen áll a hozzárendelésre. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
