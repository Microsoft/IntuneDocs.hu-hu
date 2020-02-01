---
title: A Microsoft Intune Tanúsítvány-összekötő Policy modul hibáinak megoldása | Microsoft Docs
description: A NDES házirend modul működésének hibája, amikor a modul feldolgozza a tanúsítványkérelmet, amikor SCEP-tanúsítványokat használ a tanúsítványok Intune-beli telepítéséhez.
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913184"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>A Microsoft Intune NDES-házirend moduljának hibáinak megoldása

A cikkben található információk segítséget nyújtanak a hálózati eszközök tanúsítványigénylési szolgáltatásának (NDES) házirend-moduljának működésének ellenőrzésében, amely a Microsoft Intune Tanúsítvány-összekötő-vel települ. Ha a NDES egy tanúsítványra vonatkozó kérelmet kap, akkor továbbítja a kérést a házirend-modulnak, amely érvényesként érvényesíti a kérelmet az eszköz számára. Az ellenőrzés után a NDES kapcsolatba lép a hitelesítésszolgáltatóval (CA), hogy kérje a tanúsítványt az eszköz nevében.

Ez a cikk a [SCEP kommunikációs munkafolyamat](troubleshoot-scep-certificate-profiles.md)3. és 4. lépésére is vonatkozik.

## <a name="ndes-communication-to-the-policy-module"></a>NDES kommunikáció az irányelvmodul használatával

Miután megkapta a tanúsítványkérelmet egy eszközről, a NDES ellenőrzi, hogy a kérelem az Intune-nal van-e a Microsoft Intune Tanúsítvány-összekötő-t telepítő irányelvmodul használatával. Ezek a bejegyzések a *tanúsítvány regisztrációs pontját*jelentik.

**A sikerességet jelző**naplóbejegyzések:

Ha ellenőrizni szeretné, hogy a rendszer elküldte-e az érvényesítési kérést a modulnak, keressen egy olyan bejegyzést, amely a következő példához hasonlít a NDES-kiszolgálón lévő naplókban:

- **IIS-naplók**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **NDESPlugin napló**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  Az alábbi példa az eszközök Challenge-kérelem sikeres érvényesítését jelzi, és a NDES most már kapcsolatba léphet a HITELESÍTÉSSZOLGÁLTATÓval:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint. svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**Ha a sikerességi mutatók nem jelennek**meg:

Ha nem találja ezeket a bejegyzéseket, először tekintse [át az eszköz NDES-kiszolgáló kommunikációjának](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors)hibaelhárítási útmutatóját.

Ha a cikkben szereplő információk nem segítenek a probléma megoldásában, a következő további bejegyzések is jelezhetik a problémákat.

### <a name="ndespluginlog-contains-an-error-12175"></a>A NDESPlugin. log 12175-es hibát tartalmaz

Ha a napló a következőhöz hasonló 12175-es hibát tartalmaz, az SSL-tanúsítvánnyal kapcsolatos probléma merülhet fel:

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

A modern böngészők és böngészők a mobileszközök esetében figyelmen kívül hagyják a *köznapi nevet* az SSL-tanúsítványon, ha a *tulajdonos alternatív nevei* jelen vannak.

**Megoldás**: a WEBkiszolgáló SSL-tanúsítványának kiadása a *köznapi név* és a *tulajdonos alternatív neve*számára a következő attribútumokkal, majd az IIS 443-es portjának kötése:

  - **Tulajdonos neve**  
    CN = külső kiszolgáló neve
  - **Tulajdonos alternatív neve**  
     Név = külső kiszolgáló neve  
     DNS-név = belső kiszolgáló neve

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>A NDESPlugin. log egy 403-es hibát tartalmaz – tiltott: a hozzáférés megtagadva.

Ha a következő naplók a következőhöz hasonló 403-es hibát tartalmaznak, előfordulhat, hogy az ügyféltanúsítvány nem megbízható vagy érvénytelen:

**NDESPlugin. log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**IIS-napló**:

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

Ez a probléma akkor fordul elő, ha közbenső HITELESÍTÉSSZOLGÁLTATÓI tanúsítványok vannak a NDES-kiszolgáló megbízható legfelső szintű hitelesítésszolgáltatók tanúsítványtárolójába.

Ha egy tanúsítvány rendelkezik *a és az* értékek *alapján* kiadott tanúsítvánnyal, akkor ez egy főtanúsítvány. Ellenkező esetben ez egy közbenső tanúsítvány.

**Megoldás**: a probléma megoldásához azonosítsa és távolítsa el a közbenső hitelesítésszolgáltatói tanúsítványokat a megbízható legfelső szintű hitelesítésszolgáltatók tanúsítványtárolóból.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>A NDESPlugin. log azt jelzi, hogy a kihívás hamis értéket ad vissza.

Ha a kihívás eredménye **hamis**értéket ad vissza, akkor a *CertificateRegistrationPoint. svclog* hibákat kell megadnia. Előfordulhat például, hogy egy "aláíró tanúsítvány nem olvasható be" hibaüzenet jelenik meg, amely a következő bejegyzéshez hasonló:

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**Megoldás**: azon a kiszolgálón, amelyen az összekötő telepítve van, nyissa meg a Beállításszerkesztőt, keresse meg a `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` beállításkulcsot, majd győződjön meg arról, hogy a SigningCertificate érték létezik-e.

Ha ez az érték nem létezik, indítsa újra az Intune Connector szolgáltatást a Services. msc fájlból, majd ellenőrizze, hogy az érték megjelenik-e a beállításjegyzékben. Ha az érték továbbra is hiányzik, gyakran a NDES és az Intune szolgáltatást használó kiszolgáló közötti hálózati kapcsolati problémák miatt.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>A NDES továbbítja a tanúsítványt kiállító kérést

A tanúsítvány regisztrációs pontja (a házirend modul) sikeres érvényesítése után a NDES továbbítja a tanúsítványkérelmet a HITELESÍTÉSSZOLGÁLTATÓnak az eszköz nevében.

**A sikerességet jelző**naplóbejegyzések:

- **NDESPlugin napló**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **IIS-naplók**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint. svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**Ha a sikerességi mutatók nem jelennek**meg:

Ha nem látja a sikert jelző bejegyzéseket, kövesse az alábbi lépéseket:

1. Keresse meg a *CertificateRegistrationPoint. svclog* naplózott problémákat, amikor a tanúsítvány regisztrációs pontja ellenőrzi a problémát. Keresse meg a bejegyzéseket a következő sorok között:

   - VerifyRequest elindítva.
   - VerifyRequest befejezve, hamis állapottal

2. Nyissa meg a hitelesítésszolgáltató MMC konzolt a HITELESÍTÉSSZOLGÁLTATÓN, és válassza a **Sikertelen kérelmek** lehetőséget a probléma azonosítását megkönnyítő hibák kereséséhez. A következő képen egy példa látható:

   ![Sikertelen kérelem – példa](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. A hibákért tekintse át az alkalmazás eseménynaplóját a HITELESÍTÉSSZOLGÁLTATÓN. Általában láthatja, hogy az előző lépésben a **sikertelen kérelmekben** látható hibák megegyeznek. A következő képen egy példa látható:

   ![Az alkalmazás naplójának áttekintése](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>További lépések

Ha a NDES-házirend modul érvényesíti a kérelmet, és a kérést továbbítja a hitelesítésszolgáltatónak, a következő lépés az [eszközre történő tanúsítvány-kézbesítés](troubleshoot-scep-certificate-delivery.md)áttekintése.
