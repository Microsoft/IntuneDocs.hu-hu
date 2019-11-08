---
title: Előmegosztott kulccsal rendelkező WiFi-profil létrehozása az Azure Microsoft Intune-ban | Microsoft Docs
description: Egyéni profil segítségével létrehozhat egy előmegosztott kulcsú Wi-Fi-profilt. A cikkben találhat XML-mintakódot Android-, Windows- és EAP-alapú Wi-Fi-profilok Microsoft Intune-ban való létrehozásához.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7f888a5a384503393c086a27d1c2ce6410357fd
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755026"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Előmegosztott kulccsal rendelkező Wi-Fi-profil létrehozása egyéni eszköz-profil használatával az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az előmegosztott kulcsokat (PSK) általában a WiFi-hálózatok vagy vezeték nélküli helyi hálózatok felhasználóinak hitelesítésére használják. Az Intune-nal hozhat létre egy előmegosztott kulccsal ellátott WiFi-profilt. A profil létrehozásához először készítenie kell egy **egyéni eszközkonfigurációs profilt** az Intune-ban. A cikk emellett tartalmaz néhány példát az EAP-alapú Wi-Fi-profilok létrehozásához is.

Ez a funkció a következőket támogatja:

- Android:
- Windows
- EAP-alapú Wi-Fi

> [!IMPORTANT]
> - Ha egy előmegosztott kulcsot használ a Windows 10 rendszerben, szervizelési hiba jelenik meg az Intune-ban. E hiba megjelenésekor a Wi-Fi-profilt a rendszer megfelelően hozzárendeli az eszközhöz, és a profil a várt módon fog működni.
> - Az előmegosztott kulcsot tartalmazó Wi-Fi-profilok exportálásakor gondoskodjon a fájlok védelméről. A kulcs egyszerű szövegként szerepel, ezért az Ön felelőssége a kulcs védelme.

## <a name="before-you-begin"></a>Előkészületek

- Egyszerűbb lehet, ha a kódot egy, az adott hálózathoz már csatlakozó számítógépről másolja. Ennek leírását a cikk későbbi részében megtalálhatja.
- További OMA-URI-beállítások megadásával több hálózatot és kulcsot is hozzáadhat.
- iOS-rendszereken a profil létrehozásához használja az Apple Configurator programot egy Mac munkaállomáson.
- Az előmegosztott kulcsokhoz egy 64 hexadecimális számból álló sztringet vagy egy 8–63 nyomtatható ASCII-karakterből álló jelszót kell megadnia. Bizonyos karakterek, például a csillag (*) nem támogatottak.

## <a name="create-a-custom-profile"></a>Egyéni profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a szabályzatnak. Nevezze el a szabályzatokat, hogy később könnyebben azonosítható legyen. A helyes szabályzat neve például **Egyéni OMA-URI Wi-Fi-profil beállításai Android-eszközökhöz**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza ki a platformot.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. A **Beállítások**területen válassza a **Hozzáadás**lehetőséget. Adja meg az új OMA-URI beállítást a következő tulajdonságokkal:

    1. **Név**: adja meg az OMA-URI beállítás nevét.
    2. **Leírás**: adja meg az OMA-URI beállítás leírását. A beállítás használata nem kötelező, de ajánlott.
    3. **OMA-URI**: adja meg a következő lehetőségek egyikét:

        - **Android esetén**: `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **Windows esetén**: `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > Ne hagyja ki a karaktersor elején található pontot.

        Az SSID az az SSID, amelyhez létrehozza a házirendet. Ha például a Wi-Fi neve `Hotspot-1`, írja be a következőt: `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

    4. **Adattípus**: válassza a **karakterlánc**lehetőséget.

    5. **Érték**: illessze be az XML-kódot. Tekintse meg a cikkben szereplő [példákat](#android-or-windows-wi-fi-profile-example) . Módosítsa az értékeket a saját hálózati beállításainak megfelelően. A kódban található megjegyzések további információt nyújtanak.

5. Ha elkészült, a módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

A profil megjelenik a profilok listájában. Ezután [rendelje hozzá ezt a profilt](../device-profile-assign.md) a felhasználói csoportokhoz. Ez a szabályzat kizárólag felhasználói csoportokhoz rendelhető.

Amikor az egyes eszközök legközelebb bejelentkeznek, a rendszer telepíti a szabályzatot, és létrehozza a Wi-Fi-profilt az eszközökön. Az eszköz így képes lesz automatikusan kapcsolódni a hálózathoz.

## <a name="android-or-windows-wi-fi-profile-example"></a>Android vagy Windows rendszerhez készült példa Wi-Fi-profil

Az alábbi példában megtalálhatja az Android vagy Windows rendszerhez készült Wi-Fi-profilhoz használható XML-kódot. A példa a megfelelő formátumot mutatja be, valamint részletesebb információkkal is szolgál. Ez azonban csak egy példa, és nem az Ön környezetéhez ajánlott konfiguráció.

### <a name="what-you-need-to-know"></a>Amit még tudnia kell

- A `<protected>false</protected>` tulajdonságot **false** (hamis) értékre kell állítania. Ha **true** (igaz) értékre állítja, előfordulhat, hogy az eszköz titkosított jelszót vár, és a kapott jelszót megpróbálja visszafejteni, melynek következtében a kapcsolódás meghiúsulhat.

- A `<hex>53534944</hex>` helyére a `<name><SSID of wifi profile></name>` paraméter hexadecimális értékét kell beírni. Előfordulhat, hogy a Windows 10-es eszközök hamis `x87D1FDE8 Remediation failed` hibát adnak vissza, de az eszköz továbbra is tartalmazza a profilt.

- Az XML speciális karaktereket tartalmaz, például a `&` (jel) karaktert. A speciális karakterek használata megakadályozhatja, hogy az XML a várt módon működjön. 

### <a name="example"></a>Példa

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>EAP-alapú példa Wi-Fi-profil
Az alábbi példa egy EAP-alapú Wi-Fi-profil XML-kódját tartalmazza: A példa a megfelelő formátumot mutatja be, valamint részletesebb információkkal is szolgál. Ez azonban csak egy példa, és nem az Ön környezetéhez ajánlott konfiguráció.


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>XML-fájl létrehozása meglévő Wi-Fi kapcsolat alapján

Meglévő Wi-Fi-kapcsolatból is létrehozhat egy XML-fájlt. Windows rendszerű számítógépen hajtsa végre a következő lépéseket:

1. Hozzon létre egy helyi mappát az exportált W-Fi-profilokhoz, például c:\WiFi.
2. Nyisson meg egy parancssort rendszergazdaként (kattintson a jobb gombbal a `cmd` > **Futtatás rendszergazdaként**) elemre.
3. Futtassa a `netsh wlan show profiles` parancsot. A rendszer felsorolja az összes profil nevét.
4. Futtassa a `netsh wlan export profile name="YourProfileName" folder=c:\Wifi` parancsot. Ez a parancs létrehoz egy `Wi-Fi-YourProfileName.xml` nevű fájlt a c:\Wifi.

    - Ha előmegosztott kulcsot tartalmazó Wi-Fi-profilt exportál, adja hozzá a `key=clear` parancsot a következő parancshoz:
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` egyszerű szövegként exportálja a kulcsot, amely a profil sikeres használatához szükséges.

Az XML-fájl létrehozása után másolja és illessze be az XML-szintaxist az OMA-URI beállítások > **adattípusba**. [Hozzon létre egy egyéni profilt](#create-a-custom-profile) (ebben a cikkben) a lépéseket.

> [!TIP]
> a `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` az összes, XML formátumú profilt is tartalmazza.

## <a name="best-practices"></a>Ajánlott eljárások

- A Wi-Fi-profil PSK használatával való üzembe helyezése előtt győződjön meg róla, hogy az eszköz tud közvetlenül kapcsolódni a végponthoz.

- A kulcsok (jelszavak vagy hozzáférési kódok) elforgatásakor a rendszer leállást vár, és megtervezi az üzemelő példányokat. A Wi-Fi-profilok leküldését ajánlatos munkaidőn kívülre időzíteni. Továbbá figyelmeztesse a felhasználókat, hogy a kapcsolat befolyásolhatja a kapcsolatot.

- A zökkenőmentes átállás érdekében győződjön meg arról, hogy a végfelhasználó eszköze rendelkezik egy másik internetkapcsolattal. A végfelhasználó például visszaválthat a vendég Wi-Fi-ra (vagy más Wi-Fi hálózatra), vagy mobil kapcsolattal kommunikálhat az Intune-nal. E további kapcsolat révén a felhasználó továbbra is megkaphatja a szabályzatfrissítéseket, amíg a vállalati Wi-Fi-hálózat frissül az eszközön.

## <a name="next-steps"></a>További lépések

Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md), és [Figyelje](device-profile-monitor.md) annak állapotát.
