---
title: Mobile Threat Defense-alkalmazások hozzáadása a nem regisztrált eszközökhöz
titleSuffix: Microsoft Intune
description: Mobile Threat Defense-alkalmazások hozzáadása a nem regisztrált eszközökhöz az eszköz felhasználói számára.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72795322"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Mobile Threat Defense-alkalmazások hozzáadása a nem regisztrált eszközökhöz

Alapértelmezés szerint, amikor az Intune app Protection-szabályzatokat a Mobile Threat Defense használatával használja, az Intune-nal megtekintheti a végfelhasználót az eszközön, hogy telepíthesse és bejelentkezzen az összes szükséges alkalmazásba, hogy engedélyezze a kapcsolatot a megfelelő szolgáltatásokkal.

A végfelhasználók számára szükséges a Microsoft Authenticator (iOS) az eszköz regisztrálásához, valamint a Mobile Threat Defense (Android és iOS) rendszerű eszközök fogadásához, amikor fenyegetést azonosítanak a mobileszközökön, és útmutatást kapnak a fenyegetések elhárításához.

Igény szerint az Intune-nal is hozzáadhatja és üzembe helyezheti a Microsoft Authenticator és a Mobile Threat Defense (MTD) alkalmazásokat.

> [!NOTE] 
> Ez a cikk az alkalmazás-védelmi házirendeket támogató összes Mobile Threat Defense-partnerre vonatkozik: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).
> 
> A nem regisztrált eszközök esetében **nincs szükség iOS-es alkalmazás-konfigurációs szabályzatra** , amely beállítja az Intune-nal használt iOS-alkalmazás Mobile Threat Defense szolgáltatását. Ez a legfontosabb különbség az Intune-ban regisztrált eszközökhöz képest. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Az iOS-hez készült Microsoft Authenticator konfigurálása az Intune-nal (opcionális)
Ha az Intune app Protection-szabályzatokat a Mobile Threat Defense szolgáltatással használja, az Intune végigvezeti a végfelhasználót az eszköz telepítésének, bejelentkezésének és regisztrálásának Microsoft Authenticator (iOS) használatával.

Ha azonban az alkalmazást a Intune Céges portál keresztül szeretné elérhetővé tenni a végfelhasználók számára, tekintse meg az [iOS-es áruházbeli alkalmazások Microsoft Intunehoz való hozzáadásának](../apps/store-apps-ios.md)utasításait. Használja ezt a [Microsoft Authenticator-iOS App Store-URL-címet](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) az alkalmazásadatok **konfigurálása** szakasz végrehajtásakor. Ne felejtse el az [alkalmazás az Intune-nal való hozzárendelését](../apps/apps-deploy.md) az utolsó lépésként.

> [!NOTE] 
> iOS-eszközök esetén a [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) használatára van szükség, hogy az Azure AD ellenőrizhesse a felhasználók identitását. A Intune Céges portál az Android-eszközökön működő közvetítőként működik, így a felhasználók az Azure AD-ben is megadhatják az identitásuk ellenőrzését.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Mobile Threat Defense-alkalmazások elérhetővé tétele az Intune-on keresztül (opcionális)
Ha az Intune app Protection-szabályzatokat a Mobile Threat Defense használatával használja, az Intune végigvezeti a végfelhasználót a szükséges Mobile Threat Defense-ügyfélalkalmazás telepítéséhez és bejelentkezéséhez. 

Ha azonban az alkalmazást a Intune Céges portál keresztül szeretné elérhetővé tenni a végfelhasználók számára, kövesse az alábbi lépéseket a [Azure Portal](https://portal.azure.com/). Előzőleg ismerkedjen meg a következő eljárásokkal:

- [Alkalmazás felvétele az Intune-ba](../apps/apps-add.md)
- [Alkalmazás hozzárendelése az Intune-hoz](../apps/apps-deploy.md).

### <a name="making-lookout-for-work-available-to-end-users"></a>Lookout for Work elérhetővé tétele a végfelhasználók számára
- **Android--**  
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Használja ezt a [Lookout for Work-Play áruház URL-címet](https://play.google.com/store/apps/details?id=com.lookout.enterprise) az alkalmazásadatok **konfigurálása** szakasz végrehajtásakor.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Használja ezt a [Lookout for Work-iOS App Store-URL-címet](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) az alkalmazásadatok **konfigurálása** szakasz végrehajtásakor.

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>A Zimperium elérhetővé tétele a végfelhasználók számára
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Használja ezt a [Zimperium-áruházi URL-címet](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) az alkalmazásadatok **konfigurálása** szakasz végrehajtásakor.
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>A jobb mobil elérhetővé tétele a végfelhasználók számára 
- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Használja ezt az [aktív pajzs-Play áruház URL-címet](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) az alkalmazásadatok **konfigurálása** szakasz végrehajtásakor.
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>További lépések  

- [A Mobile Threat Defense-összekötő engedélyezése az Intune-ban a nem regisztrált eszközökön](~/protect/mtd-enable-unenrolled-devices.md)

