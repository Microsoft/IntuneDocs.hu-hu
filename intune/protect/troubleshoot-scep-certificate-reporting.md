---
title: A SCEP és a Microsoft Intune használata esetén a sikeres tanúsítvány-telepítésről szóló jelentésekkel kapcsolatos hibák megoldása | Microsoft Docs
description: A NDES és az összekötő által az Intune-hoz való jelentéskészítéssel kapcsolatos hibák megoldása az SCEP-tanúsítvánnyal kiépített tanúsítványok sikeres üzembe helyezésével.
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913240"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>A Microsoft Intune lévő tanúsítványok központi telepítésének NDES kapcsolatos hibák megoldása

Az alábbi információk segítségével ellenőrizheti, hogy a NDES és a Microsoft Intune Tanúsítvány-összekötő sikeresen jelentést kapott-e az Intune-nak arról, hogy a tanúsítványt továbbították az eszközre. Az Intune-hoz való jelentéskészítés az utolsó fázis a Windows-eszközök tanúsítvánnyal való kiépítéséhez a SCEP-tanúsítványok profiljainak használatával.

Ez a cikk a [SCEP kommunikációs munkafolyamat](troubleshoot-scep-certificate-profiles.md)6. lépésére vonatkozik.

## <a name="review-for-signs-of-successful-reporting"></a>A sikeres jelentéskészítés jeleinek áttekintése

Ha a jelentéskészítés sikeres volt, a következő példákhoz hasonló bejegyzéseket talál a NDES-kiszolgálón:

- **IIS-napló**:

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin. log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint. svclog**:

  ![Intune tanúsítvány-összekötő naplója](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector. svclog**:

  ![Intune tanúsítvány-összekötő naplója](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**:

  Nyissa meg a *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus* mappát, ahol a tanúsítványigénylési állapotüzenetek tárolására szolgáló **sikertelen**, **feldolgozott**és **sikeres** mappák láthatók.

  Ha a tanúsítványkérelem feldolgozása sikeres volt, a **sikeres** mappában megjelenik az új fájlok. A *Notepad. exe* segítségével megnyithatja a fájlokat, és megtekintheti az Intune szolgáltatásba feltöltött, az Intune tanúsítvány-összekötő által feltöltött adatfájlokat. A feltöltött adatok olyan adatokat tartalmaznak, mint például a **certificateissuer**, a **userid**, a **DeviceID**és az **ujjlenyomat**.

### <a name="troubleshoot-stuck-files"></a>Beragadt fájlok hibáinak megoldása

Ha nem látja a *sikeres* mappában létrehozott új fájlokat, ellenőrizze, hogy vannak-e olyan fájlok, amelyek a *feldolgozó* mappában vannak beragadva.

Győződjön meg arról, hogy az Intune-összekötő szolgáltatás elindult a NDES-kiszolgálón, és nincsenek hibák a Ndesconnector. svclog.

## <a name="next-steps"></a>További lépések

[Microsoft Intune-támogatás kérése](../fundamentals/get-support.md)
