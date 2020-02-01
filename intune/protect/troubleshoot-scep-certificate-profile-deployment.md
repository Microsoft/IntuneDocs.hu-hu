---
title: A SCEP-tanúsítványok profiljainak üzembe helyezésével kapcsolatos hibák megoldása Microsoft Intune | Microsoft Docs
description: SCEP-tanúsítvány profiljának az Intune-nal való elküldésének hibája.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3dae74321b6825a1b94551addfd7621450fd8ae4
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913248"
---
# <a name="troubleshoot-deployment-of-a-scep-certificate-profile-to-devices-in-microsoft-intune"></a>SCEP-tanúsítvány profiljának a Microsoft Intune eszközre történő központi telepítésével kapcsolatos hibák megoldása

A következő információk segítséget nyújtanak a Egyszerű tanúsítványigénylési protokoll-(SCEP-) tanúsítvány-profilok Intune-nal való üzembe helyezésének hibakeresésében.

Ez a cikk az [SCEP kommunikációs folyamat áttekintésének](troubleshoot-scep-certificate-profiles.md)1. lépésére hivatkozik.


## <a name="android"></a>Android:

Az Android rendszerhez készült SCEP-profilokat az eszköz SyncML, és a [OMADM-naplóban](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)naplózza.

### <a name="validate-that-the-android-device-was-sent-the-policy"></a>Annak ellenőrzése, hogy az Android-eszköz el lett-e küldve a szabályzatnak

Ha ellenőrizni szeretné, hogy a rendszer elküldte-e a profilt a várt eszközre, a [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431) lépjen a **hibaelhárítás + támogatás** > **Hibaelhárítás**elemre.  A *hibaelhárítási* ablakban állítsa be a **hozzárendeléseket** a **konfigurációs profilokra** , majd ellenőrizze a következő konfigurációkat:

1. Olyan felhasználót kell megadnia, akinek meg kell kapnia a SCEP-tanúsítvány profilját.

2. Tekintse át a felhasználói csoport tagságát, hogy azok a biztonsági csoportban legyenek, amelyet az SCEP-tanúsítvány profiljában használt.

3. Ellenőrizze, hogy az eszköz utoljára be van-e jelölve az Intune-ban.

![A szabályzat ellenőrzése](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-android.png)

### <a name="validate-the-policy-reached-the-android-device"></a>Annak ellenőrzése, hogy a szabályzat elérte az Android-eszközt

Tekintse át az [eszközök OMADM naplóját](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Keresse meg az alábbihoz hasonló bejegyzéseket, amelyeket a rendszer naplóz, amikor az eszköz megkapja a profilt az Intune-ból:

```
Time    VERB    Event     com.microsoft.omadm.syncml.SyncmlSession     9595        9    <?xml version="1.0" encoding="utf-8"?><SyncML xmlns="SYNCML:SYNCML1.2"><SyncHdr><VerDTD>1.2</VerDTD><VerProto>DM/1.2</VerProto><SessionID>1</SessionID><MsgID>6</MsgID><Target><LocURI>urn:uuid:UUID</LocURI></Target><Source><LocURI>https://a.manage.microsoft.com/devicegatewayproxy/AndroidHandler.ashx</LocURI></Source><Meta><MaxMsgSize xmlns="syncml:metinf">524288</MaxMsgSize></Meta></SyncHdr><SyncBody><Status><CmdID>1</CmdID><MsgRef>6</MsgRef><CmdRef>0</CmdRef><Cmd>SyncHdr</Cmd><Data>200</Data></Status><Replace><CmdID>2</CmdID><Item><Target><LocURI>./Vendor/MSFT/Scheduler/IntervalDurationSeconds</LocURI></Target><Meta><Format xmlns="syncml:metinf">int</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>28800</Data></Item></Replace><Replace><CmdID>3</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseIDs</LocURI></Target><Data>contoso.onmicrosoft.com</Data></Item></Replace><Exec><CmdID>4</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseApps/ClearNotifications</LocURI></Target></Item></Exec><Add><CmdID>5</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Root/{GUID}/EncodedCertificate</LocURI></Target><Data>Data</Data></Item></Add><Add><CmdID>6</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Enroll/ModelName=AC_51…%2FLogicalName_39907…%3BHash=-1518303401/Install</LocURI></Target><Meta><Format xmlns="syncml:metinf">xml</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>&lt;CertificateRequest&gt;&lt;ConfigurationParametersDocument&gt;&amp;lt;ConfigurationParameters xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2012/03/07/CertificateEnrollment/ConfigurationParameters"&amp;gt;&amp;lt;ExpirationThreshold&amp;gt;20&amp;lt;/ExpirationThreshold&amp;gt;&amp;lt;RetryCount&amp;gt;3&amp;lt;/RetryCount&amp;gt;&amp;lt;RetryDelay&amp;gt;1&amp;lt;/RetryDelay&amp;gt;&amp;lt;TemplateName /&amp;gt;&amp;lt;SubjectNameFormat&amp;gt;{ID}&amp;lt;/SubjectNameFormat&amp;gt;&amp;lt;SubjectAlternativeNameFormat&amp;gt;{ID}&amp;lt;/SubjectAlternativeNameFormat&amp;gt;&amp;lt;KeyStorageProviderSetting&amp;gt;0&amp;lt;/KeyStorageProviderSetting&amp;gt;&amp;lt;KeyUsage&amp;gt;32&amp;lt;/KeyUsage&amp;gt;&amp;lt;KeyLength&amp;gt;2048&amp;lt;/KeyLength&amp;gt;&amp;lt;HashAlgorithms&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-1&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-2&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;/HashAlgorithms&amp;gt;&amp;lt;NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls&amp;gt;&amp;lt;CAThumbprint&amp;gt;{GUID}&amp;lt;/CAThumbprint&amp;gt;&amp;lt;ValidityPeriod&amp;gt;2&amp;lt;/ValidityPeriod&amp;gt;&amp;lt;ValidityPeriodUnit&amp;gt;Years&amp;lt;/ValidityPeriodUnit&amp;gt;&amp;lt;EKUMapping&amp;gt;&amp;lt;EKUMap&amp;gt;&amp;lt;EKUName&amp;gt;Client Authentication&amp;lt;/EKUName&amp;gt;&amp;lt;EKUOID&amp;gt;1.3.6.1.5.5.7.3.2&amp;lt;/EKUOID&amp;gt;&amp;lt;/EKUMap&amp;gt;&amp;lt;/EKUMapping&amp;gt;&amp;lt;/ConfigurationParameters&amp;gt;&lt;/ConfigurationParametersDocument&gt;&lt;RequestParameters&gt;&lt;CertificateRequestToken&gt;PENlcnRFbn... Hash: 1,010,143,298&lt;/CertificateRequestToken&gt;&lt;SubjectName&gt;CN=name&lt;/SubjectName&gt;&lt;Issuers&gt;CN=FourthCoffee CA; DC=fourthcoffee; DC=local&lt;/Issuers&gt;&lt;SubjectAlternativeName&gt;&lt;SANs&gt;&lt;SAN NameFormat="ID" AltNameType="2" OID="{OID}"&gt;&lt;/SAN&gt;&lt;SAN NameFormat="ID" AltNameType="11" OID="{OID}"&gt;john@contoso.onmicrosoft.com&lt;/SAN&gt;&lt;/SANs&gt;&lt;/SubjectAlternativeName&gt;&lt;NDESUrl&gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&lt;/NDESUrl&gt;&lt;/RequestParameters&gt;&lt;/CertificateRequest&gt;</Data></Item></Add><Get><CmdID>7</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/SCEP</LocURI></Target></Item></Get><Add><CmdID>8</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Add><Replace><CmdID>9</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Replace><Get><CmdID>10</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr</LocURI></Target></Item></Get><Get><CmdID>11</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/CacheVersion</LocURI></Target></Item></Get><Get><CmdID>12</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/ChangedNodes</LocURI></Target></Item></Get><Get><CmdID>13</CmdID><Item><Target><LocURI>./DevDetail/Ext/Microsoft/LocalTime</LocURI></Target></Item></Get><Get><CmdID>14</CmdID><Item><Target><LocURI>./Vendor/MSFT/DeviceLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Get><CmdID>15</CmdID><Item><Target><LocURI>./Vendor/MSFT/WorkProfileLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Final /></SyncBody></SyncML>
```

Példák a legfontosabb bejegyzésekre:

- `ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c%3BHash=-1518303401`
- `NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls`

## <a name="ios-and-ipados"></a>iOS-és iPadOS

### <a name="validate-that-the-ios-or-ipados-device-was-sent-the-policy"></a>Annak ellenőrzése, hogy az iOS-vagy iPadOS-eszköz el lett-e küldve a szabályzatnak

Ha ellenőrizni szeretné, hogy a rendszer elküldte-e a profilt a várt eszközre, a [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431) lépjen a **hibaelhárítás + támogatás** > **Hibaelhárítás**elemre.  A *hibaelhárítási* ablakban állítsa be a **hozzárendeléseket** a **konfigurációs profilokra** , majd ellenőrizze a következő konfigurációkat:

1. Olyan felhasználót kell megadnia, akinek meg kell kapnia a SCEP-tanúsítvány profilját.

2. Tekintse át a felhasználói csoport tagságát, hogy azok a biztonsági csoportban legyenek, amelyet az SCEP-tanúsítvány profiljában használt.

3. Ellenőrizze, hogy az eszköz utoljára be van-e jelölve az Intune-ban.

![A szabályzat ellenőrzése](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-ios.png)

### <a name="validate-the-policy-reached-the-ios-or-ipados-device"></a>Ellenőrzi, hogy a szabályzat elérte-e az iOS-vagy iPadOS-eszközt

Tekintse át az [eszközök hibakeresési naplóját](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Keresse meg az alábbihoz hasonló bejegyzéseket, amelyeket a rendszer naplóz, amikor az eszköz megkapja a profilt az Intune-ból:

```
debug    18:30:54.638009 -0500    profiled    Adding dependent ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 to parent 636572740000000000000012 in domain PayloadDependencyDomainCertificate to system\
```

Példák a legfontosabb bejegyzésekre:

- `ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295`
- `PayloadDependencyDomainCertificate`

## <a name="windows"></a>Windows

### <a name="validate-that-the-windows-device-was-sent-the-policy"></a>Annak ellenőrzése, hogy a Windows-eszköz el lett-e küldve a szabályzatnak

Ha ellenőrizni szeretné, hogy a rendszer elküldte-e a profilt a várt eszközre, a [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431), a[Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431) lépjen a **Hibaelhárítás + támogatás** > **Hibaelhárítás**elemre.  A *hibaelhárítási* ablakban állítsa be a **hozzárendeléseket** a **konfigurációs profilokra** , majd ellenőrizze a következő konfigurációkat:

1. Olyan felhasználót kell megadnia, akinek meg kell kapnia a SCEP-tanúsítvány profilját.

2. Tekintse át a felhasználói csoport tagságát, hogy azok a biztonsági csoportban legyenek, amelyet az SCEP-tanúsítvány profiljában használt.

3. Ellenőrizze, hogy az eszköz utoljára be van-e jelölve az Intune-ban.

![A szabályzat ellenőrzése](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-windows.png)

### <a name="validate-the-policy-reached-the-windows-device"></a>Annak ellenőrzése, hogy a házirend elérte-e a Windows-eszközt

A profil szabályzatának megérkezését a rendszer a Windows *-eszközök DeviceManagement-Enterprise-Diagnostics-Provider* > **rendszergazdai** naplójában naplózza, **306**-es azonosítójú eseménysel. 

A napló megnyitása:

1. Az eszközön futtassa a **eventvwr. msc parancsot** a Windows Eseménynapló megnyitásához.

2. Bontsa ki **az alkalmazások és szolgáltatások naplók** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**elemet.

3. Keresse meg a **306**-es eseményt, amely a következő példához hasonló:

   ```
   Event ID:      306
   Task Category: None
   Level:         Information
   User:          SYSTEM
   Computer:      <Computer Name>
   Description:
   SCEP: CspExecute for UniqueId : (ModelName_<ModelName>_LogicalName_<LogicalName>_Hash_<Hash>) InstallUserSid : (<UserSid>) InstallLocation : (user) NodePath : (clientinstall)  KeyProtection: (0x2) Result : (Unknown Win32 Error code: 0x2ab0003).
   ```

   A **0x2ab0003** hibakód a következőre van lefordítva: **DM_S_ACCEPTED_FOR_PROCESSING**.

   A nem sikeres hibakódok jelezhetik a mögöttes problémát.

## <a name="next-steps"></a>További lépések

Ha a profil eléri az eszközt, a következő lépés az [eszköz NDES-kiszolgálóval való kommunikációjának](troubleshoot-scep-certificate-device-to-ndes.md)áttekintése.
