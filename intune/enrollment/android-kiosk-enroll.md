---
title: Setup Intune enrollment for Android Enterprise dedicated devices
titleSuffix: Microsoft Intune
description: Learn how to enroll Android Enterprise dedicated devices in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d4ff9126fec182d1e0d2f3eb75297ede8a632e2e
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390720"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Set up Intune enrollment of Android Enterprise dedicated devices

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Android Enterprise supports corporate-owned, single-use, kiosk-style devices with its dedicated devices solution set. Az ilyen eszközöknek egyetlen rendeltetése van, például digitális aláírás, jegynyomtatás vagy leltárkezelés, hogy csak néhányat említsünk. A rendszergazdák alkalmazások és webes hivatkozások egy adott körére korlátozzák az eszköz használatát. Ez azt is megakadályozza, hogy a felhasználók más alkalmazásokat adjanak az eszközhöz, vagy más műveleteket hajtsanak végre rajta.

Intune helps you deploy apps and settings to Android Enterprise dedicated devices. For specific details about Android Enterprise, see [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Az ezen a módon felügyelt eszközök felhasználói fiók nélkül vannak regisztrálva az Intune-ban, és egyetlen végfelhasználóhoz sincsenek hozzárendelve. Nem rendeltetésük olyan személyes használatra szánt, vagy sok felhasználóspecifikus adatot igénylő alkalmazások futtatása, mint az Outlook vagy a Gmail.

## <a name="device-requirements"></a>Device requirements

Devices must meet these requirements to be managed as an Android Enterprise dedicated device:

- Android 5.1 vagy újabb operációs rendszer.
- Az eszközökön olyan Android-disztribúciónak kell futnia, amely kapcsolódni tud a Google Mobile Services (GMS) szolgáltatáshoz. Az eszközöknek el kell érniük a GMS-t, és képesnek kell lenniük a GMS-hez való kapcsolódásra.

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Set up Android Enterprise dedicated device management

To set up Android Enterprise dedicated device management, follow these steps:

1. A mobileszközök kezelésének előkészítését a [**Microsoft Intune** mint mobileszköz-felügyeleti (MDM) szolgáltató megadása](../fundamentals/mdm-authority-set.md) című témakör ismerteti. Ezt elég egyszer beállítani, amikor először állítja be az Intune-t a mobileszközök felügyeletére.
2. [Connect your Intune tenant account to your Managed Google Play account](connect-intune-android-enterprise.md).
3. [Regisztrációs profil létrehozása](#create-an-enrollment-profile).
4. [Eszközcsoport létrehozása](#create-a-device-group).
5. [Enroll the dedicated devices](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Create an enrollment profile

> [!NOTE]
> If a token has expired, the profile associated with it will not be displayed in **Device enrollment** > **Android enrollment** > **Corporate-owned dedicated devices**. To see all profiles associated with both active and inactive tokens, click on **Filter** and check the boxes for both "Active" and "Inactive" policy states. 

You must create an enrollment profile so that you can enroll your dedicated devices. A profil a létrehozásakor ad egy regisztrációs jogkivonatot (véletlenszerű sztring) és egy QR-kódot. Depending on the Android OS and version of the device, you can use either the token or QR code to [enroll the dedicated device](#enroll-the-dedicated-devices).

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) and choose **Device enrollment** > **Android enrollment** > **Corporate-owned dedicated devices**.
2. Válassza a **Létrehozás** lehetőséget, és töltse ki a kötelező mezőket.
    - **Név**: Adjon meg egy nevet, amelyet akkor fog használni, amikor a profilt a dinamikus eszközcsoporthoz rendeli.
    - **Jogkivonat lejárati dátuma**: Az a dátum, amikor a jogkivonat lejár. A Google legfeljebb 90 napos érvényességi időszakot engedélyez.
3. Válassza a **Létrehozás** elemet a profil mentéséhez.

### <a name="create-a-device-group"></a>Eszközcsoport létrehozása

A cél lehet alkalmazás, és hozzárendelt vagy dinamikus eszközcsoportokra vonatkozó szabályzat is. A dinamikus AAD-eszközcsoportokat a következő lépesekkel konfigurálhatja úgy, hogy automatikusan felvegyék a megadott regisztrációs profillal regisztrált eszközöket:

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) and choose **Groups** > **All groups** > **New group**.
2. A **Csoport** panelen töltse ki a kötelező mezőket az alábbiak szerint:
    - **Csoporttípus**: Biztonsági (Security)
    - **Csoport neve**: Adjon meg egy beszédes nevet (például 1. üzem eszközei)
    - **Tagság típusa**: Dinamikus eszköz (Dynamic device)
3. Válassza a **Dinamikus lekérdezés hozzáadása** lehetőséget.
4. A **Dinamikus tagsági szabályok** panelen töltse ki a mezőket az alábbiak szerint:
    - **Dinamikus tagsági szabály hozzáadása**: Egyszerű szabály (Simple rule)
    - **Eszközök hozzáadásának helye**: enrollmentProfileName
    - In the middle box, choose **Equals**.
    - Az utolsó mezőben adja meg a korábban létrehozott regisztrációs profilt.
    A dinamikus tagságra vonatkozó szabályokról bővebben lásd [az AAD-csoportok dinamikus tagsági szabályait](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership) ismertető témakört. 
5. Válassza a **Lekérdezés hozzáadása** > **Létrehozás** lehetőséget.

### <a name="replace-or-remove-tokens"></a>Jogkivonatok cseréje vagy eltávolítása

- **Jogkivonat cseréje**: A Jogkivonat cseréje lehetőséggel új jogkivonatot/QR-kódot generálhat a hamarosan lejáró helyett.
- **Jogkivonat visszavonása**: Azonnal lejárttá minősítheti a jogkivonatot/QR-kódot. Ettől kezdve a jogkivonat/QR-kód többé nem használható. Ez a lehetőség a következő esetekben lehet hasznos:
  - a jogkivonat/QR-kód véletlenül meg lett osztva egy jogosulatlan féllel
  - minden regisztráció befejeződött, és a jogkivonatra/QR-kódra többé nincs szükség

Egy jogkivonat/QR-kód cseréje vagy visszavonása a már regisztrált eszközöket nem érinti.

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) and choose **Device enrollment** > **Android enrollment** > **Coporate-owned dedicated devices**.
2. Válassza ki a profilt, amellyel dolgozni kíván.
3. Válassza a **Jogkivonat** lehetőséget.
4. A jogkivonat cseréjéhez válassza a **Jogkivonat cseréje** lehetőséget.
5. A jogkivonat visszavonásához válassza a **Jogkivonat visszavonása** lehetőséget.

## <a name="enroll-the-dedicated-devices"></a>Enroll the dedicated devices

You can now [enroll your dedicated devices](android-dedicated-devices-fully-managed-enroll.md).

> [!NOTE]
> The **Microsoft Intune** app will be automatically installed during enrollment of a dedicated device.  This app is required for enrollment and cannot be uninstalled. 

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Managing apps on Android Enterprise dedicated devices

Only apps that have Assignment type [set to Required](../apps/apps-deploy.md#assign-an-app) can be installed on Android Enterprise dedicated devices. Apps are installed from the Managed Google Play store in the same manner as Android Enterprise work profile devices.

Az alkalmazások automatikusan frissítve lesznek a felügyelt eszközökön, amikor az alkalmazás fejlesztője frissítést tesz közzé a Google Playben.

To remove an app from Android Enterprise dedicated devices, you can do either of the following:
- Törölje az alkalmazástelepítés Kötelező értékét.
- Hozzon létre központi eltávolítást az alkalmazáshoz.

## <a name="next-steps"></a>További lépések
- [Deploy Android apps](../apps/apps-deploy.md)
- [Add Android configuration policies](../configuration/device-profiles.md)
