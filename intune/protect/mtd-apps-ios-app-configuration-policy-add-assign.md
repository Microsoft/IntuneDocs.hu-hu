---
title: MTD-alkalmazások hozzáadása és hozzárendelése a Microsoft Intune-hoz
titleSuffix: Microsoft Intune
description: Az Intune-nal Mobile Threat Defense-alkalmazásokat, a Microsoft Authenticator alkalmazást és iOS-es konfigurációs szabályzatokat adhat hozzá az Azure Portalon.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04a18befe73ce63f5619c3efc6def4189db9c8df
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188487"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Mobile Threat Defense- (MTD) alkalmazások felvétele és hozzárendelése az Intune-nal

You can use Intune to add and deploy Mobile Threat Defense (MTD) apps so that end users can receive notifications when a threat is identified in their mobile devices, and to receive guidance to remediate the threats.

> [!NOTE]
> This article applies to all Mobile Threat Defense partners.

## <a name="before-you-begin"></a>Előkészületek

Complete the following steps in Intune. Előzőleg ismerkedjen meg a következő eljárásokkal:

- [Alkalmazás felvétele az Intune-ba](../apps/apps-add.md)
- [iOS-es alkalmazáskonfigurációs szabályzat felvétele az Intune-ba](../apps/app-configuration-policies-use-ios.md)
- [Alkalmazás hozzárendelése az Intune-hoz](../apps/apps-deploy.md).

> [!TIP]
> The Intune Company Portal works as the broker on Android devices so users can have their identities checked by Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Az iOS-hez készült Microsoft Authenticator alkalmazás konfigurálása

iOS-eszközök esetén a [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) használatára van szükség, hogy az Azure AD ellenőrizhesse a felhasználók identitását. Additionally, you need an iOS app configuration policy that sets the MTD iOS app you use with Intune.

Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [Microsoft Authenticator app store URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) when you configure **App information**.

## <a name="configure-mtd-applications"></a>MTD-alkalmazások konfigurálása

Válassza ki az MTD-szolgáltatójának megfelelő szakaszt:

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Lookout for Work-alkalmazások konfigurálása

- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [Lookout for work Google app store URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) for the **Appstore URL**.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [Lookout for Work iOS app store URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) for the **Appstore URL**.

- **Lookout for Work alkalmazás az Apple áruházon kívül**
  - You must re-sign the Lookout for Work iOS app. A Lookout az iOS App Store-on kívül terjeszti a Lookout for Work alkalmazását. Az alkalmazás terjesztése előtt újra alá kell írnia az alkalmazást az iOS vállalati fejlesztői tanúsítványával.  
  - A részletes leírást a Lookout for Work iOS-alkalmazás újbóli aláírásáról lásd: [Lookout for Work iOS-alkalmazás újbóli aláírásának folyamata](https://personal.support.lookout.com/hc/articles/114094038714) a Lookout oldalán.

  - **Azure AD-hitelesítés engedélyezése a Lookout for Work iOS-alkalmazás felhasználói számára**

    1. Lépjen az [Azure Portalra](https://portal.azure.com), jelentkezzen be a hitelesítő adataival, majd nyissa meg az alkalmazás lapot.

    2. Adja hozzá a **Lookout for Work iOS alkalmazást natív ügyfélalkalmazásként**.

    3. Cserélje le a **com.lookout.enterprise.yourcompanyname** sort az IPA aláírásakor választott ügyfélcsomag-azonosítóval.

    4. Adja hozzá ezt az átirányítási URI-t: **&lt;companyportal://code/>** , valamint az eredeti átirányítási URI-ja URL-kódolású verzióját.

    5. Adjon hozzá **Delegált engedélyeket** az alkalmazásához.

    > [!NOTE]
    > További részletekért lásd:[Natív ügyfélalkalmazás konfigurálása az Azure AD-val](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

  - **Adja hozzá a Lookout for Work ipa-fájlt.**

    - Upload the re-signed .ipa file as described in the [Add iOS LOB apps with Intune](../apps/lob-apps-ios.md) article. Ezenkívül a minimum OS-verziót iOS 8.0-ra vagy újabbra kell állítania.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>A Symantec Endpoint Protection Mobile-alkalmazások konfigurálása

- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure) for the **Appstore URL**.  **Minimális operációs rendszerként** jelölje be az **Android 4.0 (Ice Cream Sandwich)** rendszert.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [SEP Mobile app store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) for the **Appstore URL**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Check Point SandBlast Mobile-alkalmazások konfigurálása

- **Android--**  
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile app store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) for the **Appstore URL**.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile app store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) for the **Appstore URL**.  

### <a name="configure-zimperium-apps"></a>Zimperium-alkalmazások konfigurálása

- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [Zimperium app store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) for the **Appstore URL**.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [Zimperium app store URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) for the **Appstore URL**.  
 
### <a name="configure-pradeo-apps"></a>Pradeo-alkalmazások konfigurálása

- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [Pradeo app store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) for the **Appstore URL**.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [Pradeo app store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) for the **Appstore URL**.

### <a name="configure-better-mobile-apps"></a>Better Mobile-alkalmazások konfigurálása

- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [Active Shield app store URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) for the **Appstore URL**.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [ActiveShield app store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) for the **Appstore URL**.

### <a name="configure-sophos-apps"></a>Configure Sophos apps

- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [Sophos app store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) for the **Appstore URL**.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [ActiveShield app store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) for the **Appstore URL**.

### <a name="configure-wandera-apps"></a>Configure Wandera apps

- **Android--**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-android.md). Use this [Wandera Mobile app store URL](https://play.google.com/store/apps/details?id=com.wandera.android) for the **Appstore URL**. For **Minimum operating system**, select **Android 5.0**.

- **iOS--**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](../apps/store-apps-ios.md). Use this [Wandera Mobile app store URL](https://itunes.apple.com/app/wandera/id605469330) for the **Appstore URL**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>MTD-alkalmazások konfigurálása egy iOS-es alkalmazáskonfigurációs szabályzattal

### <a name="lookout-for-work-app-configuration-policy"></a>Konfigurációs szabályzat az Lookout for Workhöz

Create the iOS app configuration policy as described in the [using iOS app configuration policy](../apps/app-configuration-policies-use-ios.md) article.

### <a name="sep-mobile-app-configuration-policy"></a>SEP Mobile-alkalmazások konfigurációs szabályzata

Use the same Azure AD account previously configured in the [Symantec Endpoint Protection Management console](https://aad.skycure.com), which should be the same account used to sign in to the Intune.

- **Download** the iOS app configuration policy file:
  - Lépjen a [Symantec Endpoint Protection Management konzolra](https://aad.skycure.com), és jelentkezzen be rendszergazdai azonosító adataival.

  - Lépjen a **Settings** (Beállítások) lapra, majd az **Integrations** (Integrációk) alatt válassza az **Intune** lehetőséget. Válassza az **EMM Integration Selection** (EMM-integráció kiválasztása) lehetőséget. Válassza a **Microsoft** lehetőséget, majd mentse a kijelölés.

  - Kattintson az **Integration setup files** (Integráció-telepítőfájlok) hivatkozásra, és mentse a létrejövő \*.zip fájlt. A .zip-fájlban található a * **.plist**-fájl, amellyel létrehozható az iOS-es alkalmazáskonfigurációs szabályzat az Intune-ban.

  - A SEP Mobile iOS-es alkalmazáskonfigurációs szabályzat felvételéhez lásd a következő útmutatót:[A Microsoft Intune alkalmazáskonfigurációs szabályzatának használata iOS-hez](../apps/app-configuration-policies-use-ios.md).

    - For **Configuration settings format**, select **Enter XML data**, copy the content from the * **.plist** file, and paste its content into the configuration policy body.

> [!NOTE]
> Ha nem sikerült beolvasni a fájlokat, lépjen kapcsolatba a [Symantec Endpoint Protection Mobile nagyvállalati támogatási szolgálatával](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Check Point SandBlast Mobile-alkalmazások konfigurációs szabályzata

A Check Point SandBlast Mobile iOS-es alkalmazáskonfigurációs szabályzat felvételéhez tekintse át a következő útmutatót: [A Microsoft Intune alkalmazáskonfigurációs szabályzatának használata iOS-hez](../apps/app-configuration-policies-use-ios.md).

- For **Configuration settings format**, select **Enter XML data**, copy the following content and paste it into the configuration policy body.

  `<dict><key>MDM</key><string>INTUNE</string></dict>`


### <a name="zimperium-app-configuration-policy"></a>Zimperium-alkalmazások konfigurációs szabályzata

A Zimperium iOS-es alkalmazáskonfigurációs szabályzat felvételéhez kövesse [A Microsoft Intune alkalmazáskonfigurációs szabályzatának használata iOS-hez](../apps/app-configuration-policies-use-ios.md) című útmutatót.

- For **Configuration settings format**, select **Enter XML data**, copy the following content and paste it into the configuration policy body.

   ```
   <dict>
   <key>provider</key><string>Intune</string>
   <key>userprincipalname</key><string>{{userprincipalname}}</string>
   <key>deviceid</key>
   <string>{{deviceid}}</string>
   <key>serialnumber</key>
   <string>{{serialnumber}}</string>
   <key>udidlast4digits</key>
   <string>{{udidlast4digits}}</string>
   </dict>
   ```

### <a name="pradeo-app-configuration-policy"></a>Pradeo app configuration policy

Pradeo doesn't support application configuration policy on iOS.  Instead, to get a configured app, work with Pradeo to implement custom IPA or APK files that are preconfigured with the settings you want.

### <a name="better-mobile-app-configuration-policy"></a>Better Mobile-alkalmazások konfigurációs szabályzata

A Better Mobile iOS-es alkalmazáskonfigurációs szabályzat megadásához lásd [a Microsoft Intune alkalmazáskonfigurációs szabályzatainak iOS-hez történő használatával](../apps/app-configuration-policies-use-ios.md) foglalkozó útmutatót.

- For **Configuration settings format**, select **Enter XML data**, copy the following content and paste it into the configuration policy body. Cserélje le a `https://client.bmobi.net` URL-címet a konzol URL-címére.

   ```
    <dict>
   <key>better_server_url</key>
   <string>https://client.bmobi.net</string>
   <key>better_udid</key>
   <string>{{aaddeviceid}}</string>
   <key>better_user</key>
   <string>{{userprincipalname}}</string>
   </dict>
   ```

### <a name="sophos-mobile-app-configuration-policy"></a>Sophos Mobile app configuration policy

Create the iOS app configuration policy as described in the [using iOS app configuration policy](../apps/app-configuration-policies-use-ios.md) article.

### <a name="wandera-app-configuration-policy"></a>Wandera app configuration policy

See the instructions for [using Microsoft Intune app configuration policies for iOS](../apps/app-configuration-policies-use-ios.md) to add the Wandera iOS app configuration policy.

- For **Configuration settings format**, select **Enter XML data**.

Sign in to your RADAR Wandera portal and browse to **Settings** > **EMM Integration** > **App Push**. Select **Intune**, and then copy the content below and paste it into the configuration policy body.  

  ```
  <dict><key>secretKey</key>
  <string>SeeRADAR</string>
  <key>apiKey</key>
  <string> SeeRADAR </string>
  <key>customerId</key>
  <string> SeeRADAR </string>
  <key>email</key>
  <string>{{mail}}</string>
  <key>firstName</key>
  <string>{{username}}</string>
  <key>lastName</key>
  <string></string>
  <key>activationType</key>
  <string>PROVISION_THEN_AWP</string></dict>
  ```

## <a name="assign-apps-to-groups"></a>Alkalmazások hozzárendelése csoportokhoz

Ez a lépés minden MTD-partnerre vonatkozik. Lásd a következő útmutatót: [Alkalmazások csoportokhoz rendelése az Intune-nal](../apps/apps-deploy.md).

## <a name="next-steps"></a>További lépések

- [Az MTD eszközmegfelelőségi szabályzatának konfigurálása](mtd-device-compliance-policy-create.md)
