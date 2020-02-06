---
title: SCEP-tanúsítvány-profilok használata a tanúsítványok kiépítéséhez Microsoft Intune használatával | Microsoft Docs
description: A SCEP eszközök által az Intune-nal való használatra vonatkozó tanúsítványok igénylése, beleértve a NDES, a NDES és a hitelesítésszolgáltatók közötti kommunikációt, valamint az Intune tanúsítvány-összekötőt az Intune szolgáltatásba.
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
ms.openlocfilehash: 38bc86b1b9ba85eb7885a0e00673e551821063c1
ms.sourcegitcommit: 459b0ee01eb6e69cc0ce66d4c4b81d73f510f96d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034243"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Az SCEP-tanúsítványok profiljainak hibaelhárítása Microsoft Intune

A Egyszerű tanúsítványigénylési protokoll-(SCEP-) tanúsítvány-profilok használata kihívást jelenthet az Intune-ban való hibakereséshez. Ez a cikk áttekintést nyújt a problémák megoldásához:

- A SCEP folyamat architektúrájának és kommunikációs forgalmának ismertetése
- A kommunikációs folyamat során felmerülő problémák szűkítéséhez való leszűkítés elősegítése
- A következő cikkekben hivatkozott naplófájlok azonosítása a tanúsítvány-profilok hibaelhárításához

Az ebben és a kapcsolódó SCEP-tanúsítvány hibaelhárítási cikkeiben található információk az Android, iOS/iPad és Windows rendszerű eszközökön futó SCEP-tanúsítvány-profilok használatára vonatkoznak. A macOS-hez hasonló információk jelenleg nem érhetők el.

A hálózati eszközök tanúsítványigénylési szolgáltatásának (NDES) hibakereséséhez tekintse meg a következő cikkeket a support.microsoft.com:

- [A helyszíni NDES-konfiguráció ellenőrzése a SCEP-tanúsítványok számára az Intune-ban](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [NDES-konfiguráció hibaelhárítása Microsoft Intune-tanúsítvány profiljaival való használathoz]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

A folytatás előtt győződjön meg arról, hogy megfelel a [SCEP-tanúsítványok használatának előfeltételeinek](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates), beleértve a főtanúsítvány megbízható tanúsítvány-profilon keresztül történő telepítését is.

## <a name="scep-communication-flow-overview"></a>SCEP kommunikációs folyamat – áttekintés

Az alábbi ábra az Intune SCEP kommunikációs folyamatának alapszintű áttekintését mutatja be.

![SCEP-folyamat](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [SCEP-tanúsítvány profiljának üzembe helyezése](troubleshoot-scep-certificate-profile-deployment.md). Az Intune egy olyan Challenge karakterláncot hoz létre, amelyhez egy adott felhasználó, tanúsítvány célja és tanúsítvány típusa szükséges.

2. [Az eszköz NDES-kiszolgáló kommunikációja](troubleshoot-scep-certificate-device-to-ndes.md). Az eszköz a NDES tartozó URI-t használja a profilból, hogy kapcsolatba lépjen a NDES-kiszolgálóval, hogy az képes legyen a probléma kimutatása.

3. [NDES a házirend modul kommunikációjának](troubleshoot-scep-certificate-ndes-policy-module.md). A NDES továbbítja a kihívást az Intune tanúsítvány-összekötő házirend moduljának a kiszolgálón, amely érvényesíti a kérelmet.

4. [NDES a hitelesítésszolgáltatóhoz](troubleshoot-scep-certificate-ndes-policy-module.md). A NDES érvényes kérelmeket továbbít a tanúsítvány kiállításához a hitelesítésszolgáltatónak (CA).

5. [Tanúsítvány kézbesítése az eszközre](troubleshoot-scep-certificate-delivery.md). A tanúsítvány az eszközre lesz továbbítva.

6. [Az Intune-ba történő központi telepítés jelentése](troubleshoot-scep-certificate-reporting.md). Az Intune tanúsítvány-összekötő a tanúsítvány-kiállítási eseményt az Intune-nak jelenti.

## <a name="log-files"></a>Naplófájlok

A kommunikációs és a tanúsítvány-létesítési munkafolyamattal kapcsolatos problémák azonosításához tekintse át a naplófájlokat a kiszolgálói infrastruktúrából és az eszközökről. A SCEP-profilok hibaelhárításának későbbi szakaszai az ebben a részben hivatkozott naplófájlokra vonatkoznak.

- [Infrastruktúra-és kiszolgálói naplók](#logs-for-on-premises-infrastructure)

Az eszközök naplói az eszköz platformtól függenek:  

- [iOS-és iPadOS](#logs-for-ios-and-ipados-devices)
- [Android--](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>A helyszíni infrastruktúrához tartozó naplók
  
A tanúsítvány-telepítésekhez SCEP-tanúsítvány-profilok használatát támogató helyszíni infrastruktúra magában foglalja a Microsoft Intune Tanúsítvány-összekötő, a Windows Serveren futó NDES és a hitelesítésszolgáltatót is.

Ezekhez a szerepkörökhöz a naplófájlok közé tartoznak a Windows Eseménynapló, a Tanúsítványsablonok és az Intune tanúsítvány-összekötőhöz, a NDES, valamint a helyszíni infrastruktúra részét képező egyéb szerepkörökhöz és műveletekhez tartozó különböző naplófájlok.

Az alábbi lista azokat a naplókat és konzolokat tartalmazza, amelyeket a következő SCEP hibaelhárítási cikkei hivatkoznak. 

- **NDESConnector_date_time. svclog**:

  Ez a napló a Microsoft Intune Tanúsítvány-összekötőről az Intune Cloud Service-be irányuló kommunikációt jeleníti meg. A naplófájl megtekintéséhez használhatja a [Service Trace Viewer eszközt](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) .

  Kapcsolódó beállításkulcs: *HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  Hely: azon a kiszolgálón, amelyen a NDES fut, *% PROGRAM_FILES% \ Microsoft intune\ndesconnectorsvc\logs\logs*

- **CertificateRegistrationPoint_date_time. svclog**:

  Ez a napló a tanúsítványkérelmek fogadására és ellenőrzésére szolgáló NDES házirend-modult jeleníti meg. A naplófájl megtekintéséhez használhatja a [Service Trace Viewer eszközt](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) .

  Hely: azon a kiszolgálón, amelyen a NDES fut, *% PROGRAM_FILES% \ Microsoft intune\ndesconnectorsvc\logs\logs*

- **NDESPlugin. log**:

  Ez a napló a tanúsítványkérelmek átadását mutatja be a tanúsítvány regisztrációs pontjára, valamint a kérelmekből eredő ellenőrzéseket.

  Hely: azon a kiszolgálón, amelyen a NDES fut, *% PROGRAM_FILES% \ Microsoft Intune\NDESPolicyModule\logs*

- **IIS-naplók**:

  Az IIS-naplók megjelenítik a mobileszközök által a NDES beérkező tanúsítványkérelmek.

  Hely: azon a kiszolgálón, amely a NDES-t a *c:\inetpub\logs\LogFiles\W3SVC1* -on üzemelteti

- **Windows-alkalmazás naplója**:

  Ez a napló az IIS-problémák, például a SCEP-alkalmazáskészlet kivizsgálása során hasznos.

  Hely: a NDES-t futtató kiszolgálón: futtassa a **eventvwr. msc parancsot** a Windows Eseménynapló megnyitásához




### <a name="logs-for-android-devices"></a>Naplók Android-eszközökhöz

Android rendszerű eszközök esetén használja az **android céges portál** alkalmazás naplófájlját, az **OMADM. log**fájlt. A naplók összegyűjtése és áttekintése előtt engedélyezze a [részletes naplózás](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) engedélyezése beállítást, majd reprodukálja a problémát.

A OMADM. logs eszközről való összegyűjtéséhez tekintse meg a [feltöltési és e-mail-naplók USB-kábellel való használatát](/intune-user-help/send-logs-to-your-it-admin-using-cable-android)ismertető témakört.

Emellett [feltölthet és e-mail-naplókat](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app) is a támogatáshoz.

### <a name="logs-for-ios-and-ipados-devices"></a>IOS-és iPadOS-eszközök naplófájljai

Az iOS-t vagy iPadOS-t futtató eszközökön olyan hibakeresési naplókat és **Xcode** használ, amelyek Mac számítógépen futnak:

1. Az iOS-eszköz csatlakoztatása Mac számítógéphez, majd az **alkalmazások** > **segédprogramok** elemre kattintva nyissa meg a konzol alkalmazást. 

2. A **művelet**területen jelölje be az **információs üzenetek belefoglalása** és a **hibakeresési üzenetek belefoglalása**jelölőnégyzetet.

   ![A naplózási beállítások kiválasztása](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. Reprodukálja a problémát, majd mentse a naplófájlokat szövegfájlba:
   1. Válassza a **szerkesztés** > az **összes kijelölése** lehetőséget az összes üzenet kiválasztásához az aktuális képernyőn, majd válassza a > **Másolás** **szerkesztése** lehetőséget az üzenetek vágólapra másolásához. 
   2. Nyissa meg a TextEdit alkalmazást, illessze be a másolt naplókat egy új szövegfájlba, majd mentse a fájlt.


Az iOS-és iPadOS-eszközök Céges portál naplója nem tartalmaz információkat az SCEP-tanúsítvány profiljairól.

### <a name="logs-for-windows-devices"></a>Windows-eszközök naplófájljai

A Windows rendszerű eszközökön a Windows-eseménynaplók segítségével diagnosztizálhatja az Intune-nal felügyelt eszközök regisztrációját és az eszközök kezelésével kapcsolatos problémákat.

Az eszközön nyissa meg **Eseménynapló** > **alkalmazások és szolgáltatások naplói** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider**

![Windows-eseménynaplók](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>További lépések

[A SCEP-tanúsítványok profiljainak üzembe helyezésének](troubleshoot-scep-certificate-profile-deployment.md) áttekintése 
