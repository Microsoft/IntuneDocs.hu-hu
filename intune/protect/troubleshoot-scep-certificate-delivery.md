---
title: A tanúsítványok eszközökre történő kézbesítésének hibája a SCEP és a Microsoft Intune használatával Microsoft Docs
description: A tanúsítványnak az eszközre történő kézbesítésének hibája a HITELESÍTÉSSZOLGÁLTATÓTÓL a SCEP és az Intune használatával a tanúsítványok telepítéséhez.
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
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913196"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>A SCEP által a Microsoft Intune eszközökre kiosztott tanúsítványok kézbesítésének hibáinak megoldása

A cikkben található információk segítségével megvizsgálhatja a tanúsítványok eszközökre való kézbesítését, amikor Egyszerű tanúsítványigénylési protokoll (SCEP) használatával hoz létre tanúsítványokat az Intune-ban. Ha a hálózati eszközök tanúsítványigénylési szolgáltatásának (NDES) kiszolgálója megkapja a kért tanúsítványt egy eszközhöz a hitelesítésszolgáltatótól (CA), akkor a tanúsítványt visszaadja az eszköznek.

Ez a cikk a [SCEP kommunikációs munkafolyamat](troubleshoot-scep-certificate-profiles.md)5. lépésére vonatkozik; a tanúsítvány kézbesítése arra az eszközre, amely elküldte a tanúsítványkérelmet.

## <a name="review-the-certification-authority"></a>A hitelesítésszolgáltató áttekintése

Ha a HITELESÍTÉSSZOLGÁLTATÓ kiállította a tanúsítványt, az alábbi példához hasonló bejegyzés jelenik meg a HITELESÍTÉSSZOLGÁLTATÓN:

![Kiállított tanúsítványok – példa](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>Az eszköz áttekintése

### <a name="android"></a>Android:

Az eszköz rendszergazdája által beléptetett eszközök esetében az alábbi képhez hasonló értesítés jelenik meg, amely felszólítja a tanúsítvány telepítésére:

![Android-értesítés](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

Android Enterprise vagy Samsung Knox esetén a tanúsítvány telepítése automatikus és csendes.

Ha egy telepített tanúsítványt szeretne megtekinteni az Androidon, használjon egy külső gyártótól származó tanúsítvány-megtekintő alkalmazást.

Tekintse át az [eszközök OMADM naplóját](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)is. Keresse meg az alábbihoz hasonló bejegyzéseket, amelyek naplózása a tanúsítványok telepítésekor történik:

**Főtanúsítvány**:

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**SCEP használatával kiépített tanúsítvány**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS-és iPadOS

Az iOS-vagy iPadOS-eszközön megtekintheti az Eszközkezelő profil alatt található tanúsítványt. Részletezés – a telepített tanúsítványok részleteinek megtekintéséhez.

![iOS-tanúsítvány](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

A következőhöz hasonló bejegyzéseket is megtalálhatja az [iOS hibakeresési naplójában](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices):

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

A Windows-eszközön ellenőrizze a tanúsítvány kézbesítését:

- Futtassa a **eventvwr. msc parancsot** a Eseménynapló megnyitásához. Nyissa meg az **alkalmazások és szolgáltatások naplókat** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **rendszergazdát** , és keresse meg a 39-es **eseményt**. Az eseménynek a következő általános leírásával kell rendelkeznie: **SCEP: a tanúsítvány telepítése sikerült.**

   ![39-es esemény a Windows-alkalmazás naplójában](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

Az eszközön található tanúsítvány megtekintéséhez futtassa a **certmgr. msc parancsot** a tanúsítványok MMC megnyitásához, és ellenőrizze, hogy a gyökér-és SCEP-tanúsítványok megfelelően vannak-e telepítve az eszközön a személyes tárolóban:

   1. Nyissa meg a **tanúsítványok (helyi számítógép)**  > **megbízható legfelső szintű hitelesítésszolgáltatók** > **tanúsítványokat**, és ellenőrizze, hogy a hitelesítésszolgáltató főtanúsítványa megtalálható-e. A által kiállított *és* *kiadott* értékek azonosak lesznek.
   2. A tanúsítványok MMC konzolon válassza a **tanúsítványok – aktuális felhasználó** > **személyes** > **tanúsítványok**lehetőséget, és ellenőrizze, hogy a kért tanúsítvány megtalálható-e *, és hogy* a hitelesítésszolgáltató neve megegyezik-e.

## <a name="troubleshoot-failures"></a>Hibák elhárítása

### <a name="android"></a>Android:

Ennek a lépésnek a hibaelhárításához tekintse át az OMA DM-naplóban naplózott hibákat.

### <a name="ios-and-ipados"></a>iOS-és iPadOS

Ennek a lépésnek a hibaelhárításához tekintse át az eszközök hibakeresési naplójában naplózott hibákat.

### <a name="windows"></a>Windows

Az eszközön nem telepített tanúsítványokkal kapcsolatos problémák elhárításához tekintse meg a Windows eseménynaplójában a problémákat sugalló hibákat:

- Az eszközön futtassa a **eventvwr. msc** parancsot a Eseménynapló megnyitásához, majd lépjen az **alkalmazások és szolgáltatások naplóiba** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**.

A tanúsítványnak az eszközre történő kézbesítésével és telepítésével kapcsolatos hibák jellemzően a Windows-műveletekhez kapcsolódnak, és nem az Intune-hoz.

## <a name="next-steps"></a>További lépések

Ha a tanúsítvány sikeresen üzembe lett helyezve az eszközön, de az Intune nem jelent sikeres jelentést, tekintse meg a jelentéskészítési hibákkal kapcsolatos [NDES az Intune](troubleshoot-scep-certificate-reporting.md) -hoz című témakört
