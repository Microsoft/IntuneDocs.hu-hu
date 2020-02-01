---
title: Felügyelt eszköz NDES való kommunikációjának hibakeresése Microsoft Intuneban | Microsoft Docs
description: A felügyelt eszköz NDES a kiszolgálói kommunikációhoz, amikor SCEP-tanúsítványokat használ a tanúsítványok Intune-nal való üzembe helyezéséhez.
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
ms.openlocfilehash: 8c81fa9b521b0d950fb69c29f7625981e709863d
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913268"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Az eszköz NDES-kiszolgálóval való kommunikációjának megoldása a Microsoft Intune SCEP-tanúsítvány profiljaihoz

Az alábbi információk alapján megállapíthatja, hogy egy Intune Egyszerű tanúsítványigénylési protokoll (SCEP) tanúsítvány-profilt fogadó és feldolgozó eszköz sikeresen tud-e kapcsolatba lépni a hálózati eszközök tanúsítványigénylési szolgáltatásával (NDES). Az eszközön létrejön egy titkos kulcs, és a tanúsítvány-aláírási kérelem (CSR) és a Challenge az eszközről a NDES-kiszolgálóra lesz átadva. A NDES-kiszolgálóval való kapcsolatfelvételhez az eszköz az SCEP-tanúsítvány profiljának URI azonosítóját használja.

Ez a cikk a [SCEP kommunikációs folyamat áttekintésének](troubleshoot-scep-certificate-profiles.md)2. lépésére hivatkozik.

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>Az eszközön létesített kapcsolatok IIS-naplóinak áttekintése

Az IIS-naplók azonos típusú bejegyzéseket tartalmaznak az összes platformhoz.


1. A NDES-kiszolgálón nyissa meg a legutóbbi IIS-naplófájlt, amely a következő mappában található: *%SYSTEMDRIVE%\inetpub\logs\logfiles\w3svc1*

2. Keresse meg az alábbi példákhoz hasonló bejegyzéseket a naplóban. Mindkét példa a **200**állapotot tartalmazza, amely a vége közelében jelenik meg:

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   És

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. Amikor az eszköz kapcsolatba lép az IIS-vel, a rendszer naplózza a MSCEP. dll HTTP GET kérelmét.

   Tekintse át az állapotkódot a kérelem vége közelében:
   - **200**-es állapotkód: ez az állapot azt jelzi, hogy a NDES-kiszolgálóval létesített kapcsolatok sikeresek.
   - **500**-es állapotkód: a IIS_IURS csoport nem rendelkezik megfelelő engedélyekkel. Tekintse meg a cikk későbbi, 500-as [állapotkódot](#status-code-500).
   - Ha az állapotkód nem 200 vagy 500:

     - A konfiguráció érvényesítéséhez tekintse meg [a SCEP-kiszolgáló URL-címének tesztelése](#test-the-scep-server-url) című cikket a cikk későbbi részében.

     - A kevésbé gyakori hibakódokkal kapcsolatos információkért tekintse [meg az IIS 7-es és újabb verzióiban elérhető http-állapotkódot](https://support.microsoft.com/help/943891) .

   Ha a kapcsolati kérelem egyáltalán nincs naplózva, előfordulhat, hogy az eszközről az eszköz és a NDES-kiszolgáló közötti kapcsolat le van tiltva a hálózaton.

## <a name="review-device-logs-for-connections-to-ndes"></a>Az NDES létesített kapcsolatok eszköz-naplófájljainak áttekintése

### <a name="android-devices"></a>Androidos eszközök

Tekintse át az [eszközök OMADM naplóját](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Keresse meg az alábbihoz hasonló bejegyzéseket, amelyeket a rendszer naplóz, amikor az eszköz csatlakozik a NDES-hez:

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

A kulcsok bejegyzései a következő szöveges karakterláncokat tartalmazzák:

- 1 kérelem van
- "200 OK" érkezett, amikor GetCACaps (CA) küld a https://\<Server >. msappproxy. net/certsrv/MSCEP/MSCEP. dll? Operation = GetCACaps & üzenet = CA
- PkiMessage aláírása a következőhöz tartozó kulccsal: [DN = CN =\<username >; Serial = 1]


A NDES-kiszolgáló%SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ mappájába az IIS is naplózza a kapcsolatokat. Például:

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="ios-and-ipados-devices"></a>iOS-és iPadOS-eszközök

Tekintse át az [eszközök hibakeresési naplóját](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Keresse meg az alábbihoz hasonló bejegyzéseket, amelyeket a rendszer naplóz, amikor az eszköz csatlakozik a NDES-hez:

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

A kulcsok bejegyzései a következő szöveges karakterláncokat tartalmazzák:

- művelet = GetCACert
- Kísérlet a kiállított tanúsítvány beolvasására
- CSR küldése a GET használatával
- művelet = PKIOperation

### <a name="windows-devices"></a>Windows-eszközök

A NDES-hez csatlakozó Windows-eszközökön megtekintheti az eszközök Windows Eseménynapló, és megkeresheti a sikeres kapcsolatok jelzéseit. A kapcsolatok naplózása **36** -as azonosítójú eseményként történik a következő eszközökön: *DeviceManagement-Enterprise-Diagnostics –*  > **rendszergazdai** napló megadása.

A napló megnyitása:

1. Az eszközön futtassa a **eventvwr. msc parancsot** a Windows Eseménynapló megnyitásához.

2. Bontsa ki **az alkalmazások és szolgáltatások naplók** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**elemet.

3. Keresse meg a **36**-es eseményt, amely az alábbi példához hasonló: a SCEP kulcsának **kérése sikeresen létrejött**:

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>Gyakori hibák elhárítása

A következő fejezetek az összes NDES közös kapcsolódási problémáit segítik.

### <a name="status-code-500"></a>500-as állapotkód

Az alábbi példához hasonló, 500-as állapotkódot használó kapcsolatok azt jelzik, hogy az *Ügyfél megszemélyesítése a hitelesítés* felhasználói jogosultsága után nincs hozzárendelve a NDES-kiszolgálón lévő IIS_IURS csoporthoz. A **500** állapot értéke a végén jelenik meg:

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**A probléma megoldásához**:

1. A NDES-kiszolgálón futtassa a **secpol. msc parancsot** a helyi biztonsági házirend megnyitásához.

2. Bontsa ki a **helyi házirendek**csomópontot, majd kattintson a **felhasználói jogok kiosztása**elemre.

3. A jobb oldali ablaktáblán kattintson duplán az **Ügyfél megszemélyesítése hitelesítés után** elemre.

4. Kattintson a **felhasználó vagy csoport hozzáadása...** elemre, írja be **IIS_IURS** az **adja meg a kijelölendő objektumok nevét mezőbe**, majd kattintson **az OK**gombra.

5. Kattintson az **OK**gombra.

6. Indítsa újra a számítógépet, majd próbálja megismételni a csatlakoztatást az eszközről.

### <a name="test-the-scep-server-url"></a>A SCEP-kiszolgáló URL-címének tesztelése

A következő lépések végrehajtásával tesztelheti a SCEP-tanúsítvány profiljában megadott URL-címet.

1. Az Intune-ban szerkessze a SCEP-tanúsítvány profilját, és másolja a kiszolgáló URL-címét. Az URL-címnek a *https://contoso.com/certsrv/mscep/msecp.dll hoz* kell hasonlítani.

2. Nyisson meg egy webböngészőt, majd keresse meg a SCEP-kiszolgáló URL-címét. Az eredménynek a következőnek kell lennie: **HTTP 403,0 – tiltott**. Ez az eredmény azt jelzi, hogy az URL-cím megfelelően működik.

   Ha nem kapja meg ezt a hibát, válassza ki a hibához hasonló hivatkozást, amely a probléma-specifikus útmutató megtekintéséhez szükséges:
   - [Általános hálózati eszközök tanúsítványigénylési szolgáltatásának üzenete](#general-ndes-message)
   - ["HTTP-hiba 503. A szolgáltatás nem érhető el. "](#http-error-503)
   - ["GatewayTimeout" hibaüzenet jelenik meg](#gatewaytimeout)
   - ["HTTP 414 Request-URI túl hosszú" értéket kapok](#http-414-request-uri-too-long)
   - ["A lap nem jeleníthető meg" üzenet jelenik meg](#this-page-cant-be-displayed)
   - ["500 – belső kiszolgálóhiba" hibaüzenet jelenik meg](#internal-server-error)

#### <a name="general-ndes-message"></a>Általános NDES üzenet

Amikor megkeresi a SCEP-kiszolgáló URL-címét, a következő hálózati eszközök tanúsítványigénylési szolgáltatására vonatkozó üzenet jelenik meg:

![SCEP-kiszolgáló URL-címe](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **OK**: Ez a probléma általában az Microsoft Intune-összekötő telepítésével kapcsolatos probléma.

  A MSCEP. dll egy ISAPI-bővítmény, amely elfogja a bejövő kérelmeket, és a HTTP 403 hibát jeleníti meg, ha az megfelelően van telepítve.
  
  **Megoldás**: vizsgálja meg a *SetupMsi. log* fájlt annak megállapításához, hogy Microsoft Intune-összekötő telepítése sikeres volt-e. A következő példában a *telepítés sikeresen befejeződött* , a *telepítés sikeressége vagy a hiba állapota: 0* a sikeres telepítést jelzi:

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  Ha a telepítés sikertelen, távolítsa el a Microsoft Intune-összekötőt, majd telepítse újra.

#### <a name="http-error-503"></a>HTTP-hiba 503

Amikor megkeresi a SCEP-kiszolgáló URL-címét, a következő hibaüzenet jelenik meg:

![503-es HTTP-hiba. A szolgáltatás nem érhető el](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

Ezt a problémát általában az okozza, hogy az IIS **SCEP** -alkalmazáskészlete nincs elindítva. Az NDES-kiszolgálón nyissa meg az **IIS-kezelőt** , és lépjen az **alkalmazáskészletek**elemre. Keresse meg a **SCEP** alkalmazáskészletet, és ellenőrizze, hogy elindult-e.

Ha a SCEP-alkalmazáskészlet nincs elindítva, ellenőrizze az alkalmazás eseménynaplóját a kiszolgálón:

1. Az eszközön futtassa a **eventvwr. msc** parancsot a **Eseménynapló** megnyitásához, majd lépjen a **Windows-naplók** > **alkalmazáshoz**.

2. Keresse meg az alábbi példához hasonló eseményt, ami azt jelenti, hogy az alkalmazáskészlet összeomlik a kérelem fogadásakor:

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

Az **alkalmazáskészlet összeomlásának gyakori okai**:

- **1. ok**: a NDES-kiszolgáló megbízható legfelső szintű hitelesítésszolgáltatóinak tanúsítványtárolójában közbenső hitelesítésszolgáltatói tanúsítványok (nem önaláírtak) találhatók.

  **Megoldás**: távolítsa el a köztes tanúsítványokat a megbízható legfelső szintű hitelesítésszolgáltatók tanúsítványtárolóból, majd indítsa újra a NDES-kiszolgálót.
  
  A megbízható legfelső szintű hitelesítésszolgáltatók tanúsítványtárolóban található összes köztes tanúsítvány azonosításához futtassa a következő PowerShell-parancsmagot: `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  Egy olyan tanúsítvány, **amely azonos értékű** **és értékkel** rendelkezik, egy főtanúsítvány. Ellenkező esetben ez egy közbenső tanúsítvány.

  A tanúsítványok eltávolítása és a kiszolgáló újraindítása után a PowerShell-parancsmag újbóli futtatásával erősítse meg, hogy nincsenek köztes tanúsítványok. Ha vannak, ellenőrizze, hogy a Csoportházirend leküldi-e a közbenső tanúsítványokat a NDES-kiszolgálónak. Ha igen, zárja ki a NDES-kiszolgálót a Csoportházirendból, és távolítsa el újra a köztes tanúsítványokat.

- **2. ok**: a tanúsítvány-visszavonási lista (CRL) URL-címei le vannak tiltva, vagy nem érhetők el az Intune tanúsítvány-összekötő által használt tanúsítványokhoz.

  **Megoldás**: engedélyezze a további naplózást további információk gyűjtéséhez:
  1. Nyissa meg Eseménynapló, kattintson a **Megtekintés**gombra, ellenőrizze, hogy be van-e jelölve az **elemzési és hibakeresési naplók megjelenítése** beállítás.
  2. Lépjen az **alkalmazások és szolgáltatások naplóiba** > **Microsoft** > **Windows** > **CAPI2** > **működéséhez**, kattintson a jobb gombbal a **működés**elemre, majd kattintson a **napló engedélyezése**lehetőségre.
  3. A CAPI2-naplózás engedélyezése után reprodukálja a problémát, és vizsgálja meg az eseménynaplót a probléma elhárítása érdekében.

- **3. ok**: a **melynek neve certificateregistrationsvc** IIS-engedélye engedélyezve van a **Windows-hitelesítés** .

  **Megoldás**: engedélyezze a **névtelen hitelesítést** , tiltsa le a **Windows-hitelesítést**, majd indítsa újra a NDES-kiszolgálót.

  ![IIS-engedélyek](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

Amikor megkeresi a SCEP-kiszolgáló URL-címét, a következő hibaüzenet jelenik meg:

![Gatewaytimeout hiba](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **OK**: a **Microsoft HRE Application proxy Connector** szolgáltatás nincs elindítva.

  **Megoldás**: futtassa a **Services. msc parancsot**, és győződjön meg arról, hogy a **Microsoft HRE Application proxy Connector** szolgáltatás fut, és az **indítási típus** **automatikus**.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 kérelem – URI túl hosszú

Amikor megkeresi a SCEP-kiszolgáló URL-címét, a következő hibaüzenet jelenik meg: `HTTP 414 Request-URI Too Long`

- **OK**: az IIS-kérelmek szűrése nincs KONFIGURÁLVA a NDES szolgáltatás által fogadott hosszú URL-címek (lekérdezések) támogatására. Ez a támogatás akkor van konfigurálva, amikor [konfigurálja a NDES szolgáltatást](certificates-scep-configure.md#configure-the-ndes-service) a SCEP-infrastruktúrával való használatra.

- **Megoldás**: a hosszú URL-címek támogatásának konfigurálása.

  1. A NDES-kiszolgálón nyissa meg az IIS-kezelőt, válassza az **alapértelmezett** webhely > a **kérelmek szűrése** > a **szolgáltatás szerkesztése** lehetőséget a **kérelem-szűrési beállítások szerkesztése** lap megnyitásához.

  2. Adja meg a következő beállításokat:
     - **URL-cím maximális hossza (bájt)** = 65534
     - **Lekérdezési karakterlánc maximális száma (bájt)** = 65534

  3. A konfiguráció mentéséhez és az IIS-kezelő bezárásához kattintson **az OK gombra** .

  4. Ellenőrizze ezt a konfigurációt a következő beállításkulcs megkeresésével annak ellenőrzéséhez, hogy a megadott értékek szerepelnek-e:

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     A következő értékek DWORD-bejegyzésként vannak beállítva:
     - Név: **MaxFieldLength**, decimális **65534**
     - Név: **MaxRequestBytes**, decimális **65534**

  5. Indítsa újra a NDES-kiszolgálót.

#### <a name="this-page-cant-be-displayed"></a>Ez a lap nem jeleníthető meg

Az Azure AD Application Proxy konfigurálva van. Amikor megkeresi a SCEP-kiszolgáló URL-címét, a következő hibaüzenet jelenik meg:

`This page can't be displayed`

- **OK**: Ez a probléma akkor fordul elő, ha a SCEP külső URL-címe helytelen az alkalmazásproxy konfigurációjában. Erre az URL-címre https://contoso.com/certsrv/mscep/mscep.dll példa.

  **Megoldás**: használja az *yourtenant.msappproxy.net* alapértelmezett tartományát az SCEP külső URL-címéhez az alkalmazásproxy konfigurációjában.

#### <a name="internal-server-error"></a>500 – belső kiszolgálóhiba

Amikor megkeresi a SCEP-kiszolgáló URL-címét, a következő hibaüzenet jelenik meg:

![500 – belső kiszolgálóhiba](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **1. ok**: a NDES szolgáltatás fiókja zárolva van, vagy lejárt a jelszava.

  **Megoldás**: a fiók zárolásának feloldása vagy a jelszó alaphelyzetbe állítása.

- **2. ok**: a MSCEP-ra tanúsítványok lejártak.

  **Megoldás**: Ha a MSCEP-ra tanúsítványai lejárnak, telepítse újra a NDES szerepkört, vagy kérjen új Cep titkosítási és Exchange beléptetési ügynök (offline kérelem) tanúsítványokat.

  Új tanúsítványok igényléséhez kövesse az alábbi lépéseket:

  1. A hitelesítésszolgáltató (CA) vagy a kiállító HITELESÍTÉSSZOLGÁLTATÓ területen nyissa meg a Tanúsítványsablonok MMC-t. Győződjön meg arról, hogy a bejelentkezett felhasználó és a **NDES-kiszolgáló** **olvasási** és beléptetési engedéllyel rendelkezik a Cep titkosítási és Exchange-regisztrációs ügynök (offline kérelem) tanúsítványsablonok számára.

  2. Győződjön meg arról, hogy a NDES-kiszolgálón lejárt tanúsítványok vannak, és másolja a **tulajdonos** adatait a tanúsítványból.

  3. Nyissa meg a tanúsítványok MMC-t a **számítógépfiók**számára.

  4. Bontsa ki a **személyes**csomópontot, kattintson a jobb gombbal a **tanúsítványok**elemre, majd válassza **az összes feladat** > **új tanúsítvány kérése**lehetőséget

  5. A **tanúsítvány kérése** lapon válassza a **Cep titkosítás**lehetőséget, majd kattintson a **tanúsítvány igényléséhez több információ szükséges. Kattintson ide a beállítások konfigurálásához**.

     ![CEP titkosítás kiválasztása](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. A **tanúsítvány tulajdonságai**között kattintson a **tulajdonos** lapra, töltse ki a **tulajdonos nevét** a 2. lépésben összegyűjtött adatokkal, kattintson a **Hozzáadás**, majd **az OK**gombra.

  7. Fejezze be a tanúsítványigénylést.

  8. Nyissa meg a **saját felhasználói fiókhoz**tartozó MMC-tanúsítványokat.

     Ha regisztrálja az Exchange beléptetési ügynök (kapcsolat nélküli kérelem) tanúsítványát, azt a felhasználói környezetben kell végrehajtania. Mivel a tanúsítványsablon **tulajdonos típusa** a **felhasználó**értékre van állítva.

  9. Bontsa ki a **személyes**csomópontot, kattintson a jobb gombbal a **tanúsítványok**elemre, majd válassza **az összes feladat** > **új tanúsítvány kérése**lehetőséget

  10. A **tanúsítvány kérése** lapon válassza az **Exchange beléptetési ügynök (offline kérelem)** lehetőséget, majd kattintson a **tanúsítvány igényléséhez több információ szükséges. Kattintson ide a beállítások konfigurálásához**.

      ![Exchange beléptetési ügynök kiválasztása](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. A **tanúsítvány tulajdonságai**között kattintson a **Tárgy** lapra, töltse ki a **tulajdonos nevét** a 2. lépésben összegyűjtött adatokkal, majd kattintson a **Hozzáadás**gombra.

      ![Tanúsítvány tulajdonságai](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      Válassza a **titkos kulcs** lapot, jelölje be a **titkos kulcs exportálása**lehetőséget, majd kattintson **az OK**gombra.

      ![Titkos kulcs](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. Fejezze be a tanúsítványigénylést.

  13. Exportálja az Exchange beléptetési ügynök (kapcsolat nélküli kérelem) tanúsítványát az aktuális felhasználói tanúsítványtárolóból. A tanúsítvány exportálása varázslóban válassza **az Igen lehetőséget, majd exportálja a titkos kulcsot**.

  14. Importálja a tanúsítványt a helyi számítógép tanúsítványtárolójába.

  15. A tanúsítványok MMC konzolon végezze el az alábbi műveleteket az egyes új tanúsítványokhoz:

      Kattintson a jobb gombbal a tanúsítványra, kattintson a **minden feladat** > **titkos kulcsok kezelése**lehetőségre, és adjon hozzá **olvasási** engedélyt a NDES-szolgáltatásfiók számára.

  16. Futtassa az **IISReset** parancsot az IIS újraindításához.

## <a name="next-steps"></a>További lépések

Ha az eszköz sikeresen elérte a NDES-kiszolgálót a tanúsítványkérelem bemutatására, a következő lépés az [Intune tanúsítvány-összekötők házirend moduljának](troubleshoot-scep-certificate-ndes-policy-module.md)áttekintése.
