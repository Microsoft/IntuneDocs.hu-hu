---
title: Az Microsoft Intune Certificate Connector és az Event ID-azonosítók hibáinak megoldása | Microsoft Docs
description: Az Microsoft Intune Certificate Connector hibakereséséhez tekintse át az eseményazonosító és a leírások áttekintését, és tekintse át az Intune Connector szolgáltatás diagnosztikai kódjait.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 682d51269798dff181a3bd8384268da862118a70
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167759"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Intune tanúsítvány-összekötő eseményei és diagnosztikai kódok

A 6.1806.x.x verziótól kezdődően az Intune Connector Service naplózza az eseményeket az **Eseménynaplóban** (**Alkalmazás- és szolgáltatásnaplók** > **Microsoft Intune Connector**). Ezek az események segíthetnek elhárítani az Intune Connector konfigurációjával kapcsolatos esetleges problémákat. A naplózott eseményrekordokban megtalálhatja, hogy a művelet sikeres vagy sikertelen volt-e, illetve a rekordok diagnosztikai kódokat és üzeneteket is tartalmaznak, melyek segítenek a rendszergazdának a probléma elhárításában.

> [!TIP]  
> A problémák elhárításához és az Intune-összekötő beállításának ellenőrzéséhez tekintse meg a [hitelesítésszolgáltató parancsfájl mintáit](https://aka.ms/intuneconnectorverificationscript)ismertető témakört.

## <a name="event-ids-and-descriptions"></a>Eseményazonosítók és -leírások

| Eseményazonosító      | Esemény neve    | Esemény leírása | Vonatkozó diagnosztikai kódok |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Az összekötő szolgáltatás elindult | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Az összekötőszolgáltatás leállt | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Az összekötő beléptetési tanúsítványa sikeresen megújult | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Az összekötő beléptetési tanúsítványának megújítása nem sikerült. Telepítse újra az összekötőt. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Nem sikerült beolvasni az összekötő beléptetési tanúsítványát a beállításjegyzékből. Ellenőrizze az eseményhez tartozó tanúsítvány-ujjlenyomatot. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Ellenőrizze az esemény diagnosztikai adatait. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Sikeresen ki lett bocsátva egy PKCS-tanúsítvány. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet, tanúsítványsablon-nevet és tanúsítvány-ujjlenyomatot. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Egy PKCS-tanúsítvány kibocsátása nem sikerült. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet, tanúsítványsablon-nevet és tanúsítvány-ujjlenyomatot. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Sikeresen vissza lett vonva a tanúsítvány. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet és tanúsítvány-sorozatszámot. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Nem sikerült a tanúsítvány visszavonása. Ellenőrizze az eseményhez tartozó eszközazonosítót, felhasználóazonosítót, hitelesítésszolgáltatói nevet és tanúsítvány-sorozatszámot. További információért tekintse át az NDES SVC-naplófájlokat.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Sikeresen fel lett töltve a tanúsítvány kérelme vagy visszavonási adata. A feltöltés részleteit megtalálhatja az esemény adataiban. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Nem sikerült feltölteni a tanúsítvány kérelmét vagy visszavonási adatait. Ellenőrizze az esemény adatai között megtalálható feltöltési állapotot a hiba helyének megállapításához.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Sikeresen le lett töltve egy kérelem egy tanúsítvány aláírására, egy ügyféltanúsítvány letöltésére vagy egy tanúsítvány visszavonására. A letöltés részleteit megtalálhatja az esemény adataiban.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Nem sikerült letölteni egy kérelmet egy tanúsítvány aláírására, egy ügyféltanúsítvány letöltésére vagy egy tanúsítvány visszavonására. A letöltés részleteit megtalálhatja az esemény adataiban. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | A tanúsítványregisztrációs pont sikeresen ellenőrzött egy ügyfélkérdést | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | A tanúsítványregisztrációs pont végzett, de elutasította a kérelmet. További részletekért ellenőrizze a diagnosztikai kódot és üzenetet. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | A tanúsítványregisztrációs pont nem tudott ellenőrizni egy ügyfélkérést. További részletekért ellenőrizze a diagnosztikai kódot és üzenetet. Az eseményüzenet adataiban megtalálhatja a kérdéshez tartozó eszközazonosítót. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | A tanúsítványregisztrációs pont sikeresen befejezte az értesítési folyamatot, és elküldte a tanúsítványt az ügyféleszköznek. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | A tanúsítványregisztrációs pont nem tudta befejezni az értesítési folyamatot. Az eseményüzenet adataiban megtalálhatja a kérelem részleteit. Ellenőrizze az NDES-kiszolgáló és a hitelesítésszolgáltató közötti kapcsolatot. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Diagnosztikai kódok

| Diagnosztikai kód | Diagnosztikai név | Diagnosztikai üzenet |
| -------------   | -------------   | -------------      |
| 0x00000000 | Siker  | Siker |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | A hitelesítésszolgáltató érvénytelen vagy elérhetetlen. Győződjön meg róla, hogy a hitelesítésszolgáltató elérhető, és hogy a kiszolgálója tud kommunikálni vele. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | A Symantec Client Auth tanúsítvány nem található meg a helyi tanúsítványtárban. További információért lásd: [A Symantec regisztrációszolgáltató tanúsítvány telepítése](certificates-digicert-configure.md#install-the-digicert-ra-certificate).  |
| 0x00000402 | RevokeCert_AccessDenied  | A megadott fióknak nincs engedélye hitelesítésszolgáltatói tanúsítvány visszavonására. A kibocsátó hitelesítésszolgáltató nevét megtalálhatja a Hitelesítésszolgáltató neve mezőben.  |
| 0x00000403 | CertThumbprint_NotFound  | Nem található a bemenetnek megfelelő tanúsítvány. Regisztrálja a tanúsítvány-összekötőt, és próbálkozzon ismét. |
| 0x00000404 | Certificate_NotFound  | Nem található a megadott bemenetnek megfelelő tanúsítvány. Regisztrálja ismét a tanúsítvány-összekötőt, és próbálkozzon újra. |
| 0x00000405 | Certificate_Expired  | Egy tanúsítvány lejárt. Regisztrálja ismét a tanúsítvány-összekötőt a tanúsítvány megújításához, majd próbálkozzon újra. |
| 0x00000408 | CRPSCEPCert_NotFound  | Az CRP-titkosítás tanúsítványa nem található. Győződjön meg róla, hogy az NDES és az Intune-összekötő helyesen van beállítva. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Nem sikerült beolvasni az aláíró tanúsítványt. Győződjön meg róla, hogy az Intune Connector Service megfelelően van konfigurálva, és hogy az Intune Connector Service fut. Ellenőrizze emellett azt is, hogy a tanúsítvány letöltési eseményei sikeresen voltak-e. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Nem sikerült az SCEP-kérelem deszerializálása. Győződjön meg róla, hogy az NDES és az Intune-összekötő helyesen van beállítva. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Kérelem megtagadva lejárt tanúsítványkérdés miatt. Az ügyféleszköz megpróbálhatja ismét végrehajtani a műveletet, miután igényelt egy új kérdést a felügyeleti kiszolgálótól. |
| 0x0FFFFFFFF | Unknown_Error  | Nem tudtuk teljesíteni a kérelmét egy kiszolgálóoldali hiba miatt. Kérjük, próbálkozzon újból. |


## <a name="next-steps"></a>További lépések
További segítségért tekintse [meg Microsoft Intune útmutató SCEP-profiljának hibaelhárítása című témakört](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) .
