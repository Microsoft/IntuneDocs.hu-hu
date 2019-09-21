---
title: MTD-alkalmazások hozzáadása és hozzárendelése a Microsoft Intune-hoz
titleSuffix: Microsoft Intune
description: Az Intune-nal Mobile Threat Defense-alkalmazásokat, a Microsoft Authenticator alkalmazást és iOS-es konfigurációs szabályzatokat adhat hozzá az Azure Portalon.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55132570683742bd3e8dcec1c20726b9eb2c4b16
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166826"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Mobile Threat Defense- (MTD) alkalmazások felvétele és hozzárendelése az Intune-nal  

> [!NOTE] 
> Ez a cikk az összes Mobile Threat Defense-partnerre vonatkozik.

A Mobile Threat Defense-(MTD-) alkalmazások hozzáadásához és üzembe helyezéséhez használhatja az Intune-t, hogy a végfelhasználók értesítéseket kapjanak a mobileszközök által észlelt fenyegetésekről, és útmutatást kapjanak a fenyegetések elhárításához.

## <a name="before-you-begin"></a>Előkészületek    
Az [Azure Portalon](https://portal.azure.com/) végre kell hajtani az alábbi lépéseket. Előzőleg ismerkedjen meg a következő eljárásokkal:

- [Alkalmazás felvétele az Intune-ba](apps-add.md)
- [iOS-es alkalmazáskonfigurációs szabályzat felvétele az Intune-ba](app-configuration-policies-use-ios.md)
- [Alkalmazás hozzárendelése az Intune-hoz](apps-deploy.md).

> [!TIP]
> A Intune Céges portál az Android-eszközökön működő közvetítőként működik, így a felhasználók az Azure AD-ben is megadhatják az identitásuk ellenőrzését.

## <a name="configure-microsoft-authenticator-for-ios"></a>Az iOS-hez készült Microsoft Authenticator alkalmazás konfigurálása  
iOS-eszközök esetén a [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) használatára van szükség, hogy az Azure AD ellenőrizhesse a felhasználók identitását. Emellett szüksége lesz egy iOS-alkalmazás konfigurációs szabályzatára is, amely az Intune-nal használt MTD iOS-alkalmazást állítja be.

Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Az **Alkalmazásadatok konfigurálása** szakasz **12. lépésében** használja a [ Microsoft Authenticator alkalmazás-áruházbeli URL-címét](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8).

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
- **Android**  
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). A **7. lépésben** használja a [ Lookout for Work Google alkalmazás-áruházbeli URL-címét](https://play.google.com/store/apps/details?id=com.lookout.enterprise).

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Ezt a [Lookout for Work iOS App Store-URL-címet](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) használhatja az **AppStore URL-** címének **11** . lépésében.

- **Lookout for Work alkalmazás az Apple áruházon kívül**  
  - A Lookout for Work iOS-alkalmazást újra alá kell írnia. A Lookout az iOS App Store-on kívül terjeszti a Lookout for Work alkalmazását. Az alkalmazás terjesztése előtt újra alá kell írnia az alkalmazást az iOS vállalati fejlesztői tanúsítványával.  
  - A részletes leírást a Lookout for Work iOS-alkalmazás újbóli aláírásáról lásd: [Lookout for Work iOS-alkalmazás újbóli aláírásának folyamata](https://personal.support.lookout.com/hc/articles/114094038714) a Lookout oldalán.

  - **Azure AD-hitelesítés engedélyezése a Lookout for Work iOS-alkalmazás felhasználói számára**

    1. Lépjen az [Azure Portalra](https://portal.azure.com), jelentkezzen be a hitelesítő adataival, majd nyissa meg az alkalmazás lapot.

    2. Adja hozzá a **Lookout for Work iOS alkalmazást** **natív ügyfélalkalmazásként**.

    3. Cserélje le a **com.lookout.enterprise.yourcompanyname** sort az IPA aláírásakor választott ügyfélcsomag-azonosítóval.

    4. Adja hozzá ezt az átirányítási URI-t: **&lt;companyportal://code/>** , valamint az eredeti átirányítási URI-ja URL-kódolású verzióját.

    5. Adjon hozzá **Delegált engedélyeket** az alkalmazásához.

    > [!NOTE] 
    > További részletekért lásd:[Natív ügyfélalkalmazás konfigurálása az Azure AD-val](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

  - **Adja hozzá a Lookout for Work ipa-fájlt.**

    - Töltse fel az újra aláírt. ipa-fájlt az [iOS LOB-alkalmazások hozzáadása az Intune](lob-apps-ios.md) -nal című cikkben leírtak szerint. Ezenkívül a minimum OS-verziót iOS 8.0-ra vagy újabbra kell állítania.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>A Symantec Endpoint Protection Mobile-alkalmazások konfigurálása  
- **Android**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). A **7. lépésben** használja ezt a [SEP Mobile alkalmazás-áruházbeli URL-címet](https://play.google.com/store/apps/details?id=com.skycure.skycure).  **Minimális operációs rendszerként** jelölje be az **Android 4.0 (Ice Cream Sandwich)** rendszert.

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Használja ezt a [Sep Mobile App Store-beli URL-címet](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) az **AppStore URL-** címének **11** . lépésében.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Check Point SandBlast Mobile-alkalmazások konfigurálása  
- **Android**  
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). Adja meg ezt a [Check Point SandBlast Mobile alkalmazás-áruházbeli URL-címet](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) a  **7. lépésben**.

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Használja ezt a pipát a kihelyezett [mobil alkalmazás áruházbeli URL-címére](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) az **AppStore URL-címének** **11** . lépésében.  

### <a name="configure-zimperium-apps"></a>Zimperium-alkalmazások konfigurálása  
- **Android**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). A **7. lépésben** használja a [ Zimperium alkalmazás-áruházbeli URL-címét](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en).

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Használja ezt a [Zimperium alkalmazás-áruházbeli URL-címet](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) az **AppStore URL-címének** **11** . lépésében.  
 
### <a name="configure-pradeo-apps"></a>Pradeo-alkalmazások konfigurálása  
- **Android**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). A **7. lépésben** használja a [Pradeo alkalmazás-áruházbeli URL-címet](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US).

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Használja ezt a [Pradeo alkalmazás-áruházbeli URL-címet](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) az **AppStore URL-címének** **11** . lépésében.

### <a name="configure-better-mobile-apps"></a>Better Mobile-alkalmazások konfigurálása  
- **Android**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). Használja az [Active Shield ezen alkalmazás-áruházbeli URL-címét](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) a **7. lépésben**.

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Használja ezt a [ActiveShield alkalmazás-áruházbeli URL-címet](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) az **AppStore URL-címének** **11** . lépésében.

### <a name="configure-sophos-apps"></a>A Sophos-alkalmazások konfigurálása  
- **Android**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). Használja ezt a [Sophos App Store-beli URL-címet](https://play.google.com/store/apps/details?id=com.sophos.smsec) a **7. lépésben**.

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Használja ezt a [ActiveShield alkalmazás-áruházbeli URL-címet](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) az **AppStore URL-címének** **11** . lépésében.

### <a name="configure-wandera-apps"></a>A Wander-alkalmazások konfigurálása  
 
- **Android**
  - Lásd a következő útmutatót: [Android Áruházbeli alkalmazás felvétele a Microsoft Intune-ba](store-apps-android.md). Használja a [Wanda Mobile App Store-beli URL-címét](https://play.google.com/store/apps/details?id=com.wandera.android) a **7. lépésben**. A **minimális operációs rendszer**beállításnál válassza az **Android 5,0**lehetőséget.

- **iOS**
  - Lásd a következő útmutatót: [iOS Store-alkalmazás felvétele a Microsoft Intune-ba](store-apps-ios.md). Használja a [Wanda Mobile App Store-beli URL-címét](https://itunes.apple.com/app/wandera/id605469330) az **AppStore URL-** címének **11** . lépésében.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>MTD-alkalmazások konfigurálása egy iOS-es alkalmazáskonfigurációs szabályzattal  

### <a name="lookout-for-work-app-configuration-policy"></a>Konfigurációs szabályzat az Lookout for Workhöz  
- Hozza létre az iOS-alkalmazás konfigurációs szabályzatát az [iOS-alkalmazás konfigurációs házirendjének használata](app-configuration-policies-use-ios.md) című cikkben leírtak szerint.

### <a name="sep-mobile-app-configuration-policy"></a>SEP Mobile-alkalmazások konfigurációs szabályzata  
- Használja ugyanazt az Azure AD-fiókot, amelyet korábban a [Symantec Endpoint Protection felügyeleti konzolján](https://aad.skycure.com)konfigurált, és amely a klasszikus Intune-portálra való bejelentkezéshez használt fióknak kell lennie.

- **Töltse le** az iOS-alkalmazás konfigurációs szabályzatának fájlját: 
  - Lépjen a [Symantec Endpoint Protection Management konzolra](https://aad.skycure.com), és jelentkezzen be rendszergazdai azonosító adataival.

  - Lépjen a **Settings** (Beállítások) lapra, majd az **Integrations** (Integrációk) alatt válassza az **Intune** lehetőséget. Válassza az **EMM Integration Selection** (EMM-integráció kiválasztása) lehetőséget. Válassza a **Microsoft** lehetőséget, majd mentse a kijelölés.

  - Kattintson az **Integration setup files** (Integráció-telepítőfájlok) hivatkozásra, és mentse a létrejövő \*.zip fájlt. A .zip-fájlban található a * **.plist**-fájl, amellyel létrehozható az iOS-es alkalmazáskonfigurációs szabályzat az Intune-ban.

  - A SEP Mobile iOS-es alkalmazáskonfigurációs szabályzat felvételéhez lásd a következő útmutatót:[A Microsoft Intune alkalmazáskonfigurációs szabályzatának használata iOS-hez](app-configuration-policies-use-ios.md).

  - A **8. lépésnél** válassza az **XML adatok megadása** lehetőséget, majd másolja be a * **.plist**-fájl tartalmát a konfigurációs szabályzat törzsébe.

> [!NOTE]  
> Ha nem sikerült beolvasni a fájlokat, lépjen kapcsolatba a [Symantec Endpoint Protection Mobile nagyvállalati támogatási szolgálatával](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Check Point SandBlast Mobile-alkalmazások konfigurációs szabályzata  
- A Check Point SandBlast Mobile iOS-es alkalmazáskonfigurációs szabályzat felvételéhez tekintse át a következő útmutatót: [A Microsoft Intune alkalmazáskonfigurációs szabályzatának használata iOS-hez](app-configuration-policies-use-ios.md).
  - A**8. lépésnél** válassza az **XML adatok megadása** lehetőséget, majd másolja be az alábbi tartalmat a konfigurációs szabályzat törzsébe.

        <dict><key>MDM</key><string>INTUNE</string></dict>


### <a name="zimperium-app-configuration-policy"></a>Zimperium-alkalmazások konfigurációs szabályzata  
- A Zimperium iOS-es alkalmazáskonfigurációs szabályzat felvételéhez kövesse [A Microsoft Intune alkalmazáskonfigurációs szabályzatának használata iOS-hez](app-configuration-policies-use-ios.md) című útmutatót.
  - A**8. lépésnél** válassza az **XML adatok megadása** lehetőséget, majd másolja be az alábbi tartalmat a konfigurációs szabályzat törzsébe.
 
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

### <a name="pradeo-app-configuration-policy"></a>Pradeo-alkalmazás konfigurációs szabályzata  
A Pradeo nem támogatja az alkalmazás-konfigurációs szabályzatot iOS rendszeren.  Ehelyett egy konfigurált alkalmazás beszerzéséhez a Pradeo együtt kell működnie a kívánt beállításokkal előre konfigurált egyéni IPA-vagy APK-fájlok megvalósításához.

### <a name="better-mobile-app-configuration-policy"></a>Better Mobile-alkalmazások konfigurációs szabályzata  
- A Better Mobile iOS-es alkalmazáskonfigurációs szabályzat megadásához lásd [a Microsoft Intune alkalmazáskonfigurációs szabályzatainak iOS-hez történő használatával](app-configuration-policies-use-ios.md) foglalkozó útmutatót.
  - A**8. lépésnél** válassza az **XML adatok megadása** lehetőséget, majd másolja be az alábbi tartalmat a konfigurációs szabályzat törzsébe. Cserélje le a `https://client.bmobi.net` URL-címet a konzol URL-címére.

        <dict>
        <key>better_server_url</key>
        <string>https://client.bmobi.net</string>
        <key>better_udid</key>
        <string>{{aaddeviceid}}</string>
        <key>better_user</key>
        <string>{{userprincipalname}}</string>
        </dict>


### <a name="sophos-mobile-app-configuration-policy"></a>A Sophos Mobile App konfigurációs szabályzata  
Hozza létre az iOS-alkalmazás konfigurációs szabályzatát az [iOS-alkalmazás konfigurációs házirendjének használata](app-configuration-policies-use-ios.md) című cikkben leírtak szerint.

### <a name="wandera-app-configuration-policy"></a>A Wanda alkalmazás konfigurációs házirendje  
Tekintse meg az [iOS rendszerhez készült Microsoft Intune alkalmazás-konfigurációs szabályzatok használatának](app-configuration-policies-use-ios.md) utasításait a Wanda iOS-alkalmazás konfigurációs házirendjének hozzáadásához.
- A **8**. lépésnél használja az **XML-adatbevitel**lehetőséget. Jelentkezzen be a radar Wanda-portálra, > és keresse meg a Settings, a következőt: az alkalmazásnév**Integration** > **app push** Válassza az **Intune**lehetőséget, majd másolja az alábbi tartalmat, és illessze be a konfigurációs szabályzat törzsébe.  

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

## <a name="assign-apps-to-groups"></a>Alkalmazások hozzárendelése csoportokhoz  
- Ez a lépés minden MTD-partnerre vonatkozik. Lásd a következő útmutatót: [Alkalmazások csoportokhoz rendelése az Intune-nal](apps-deploy.md).

## <a name="next-steps"></a>További lépések  
- [Az MTD eszközmegfelelőségi szabályzatának konfigurálása](mtd-device-compliance-policy-create.md)
