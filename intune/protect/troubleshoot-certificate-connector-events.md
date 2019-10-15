---
title: Az Microsoft Intune Certificate Connector és az Event ID-azonosítók hibáinak megoldása | Microsoft Docs
titleSuffix: Microsoft Intune
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
ms.openlocfilehash: 2d798f22ee4e0f11f46626eec01ad3b739d61467
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306722"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Intune tanúsítvány-összekötő eseményei és diagnosztikai kódok

A 6.1806. x. x verziótól kezdődően az Intune-összekötő szolgáltatás a **eseménynaplóban** naplózza az eseményeket (az**alkalmazások és szolgáltatások naplói**@no__t – 2**Microsoft Intune összekötő**). Ezeknek az eseményeknek a segítségével elháríthatja az Intune-összekötő konfigurációjában rejlő lehetséges problémákat. Ezek az események a művelet sikerességét és hibáit naplózzák, valamint olyan diagnosztikai kódokat is tartalmaznak, amelyekkel a rendszergazdák a rendszergazda által végzett hibakeresést segítik.

> [!TIP]  
> A problémák elhárításához és az Intune-összekötő beállításának ellenőrzéséhez tekintse meg a [hitelesítésszolgáltató parancsfájl mintáit](https://aka.ms/intuneconnectorverificationscript)ismertető témakört.

## <a name="event-ids-and-descriptions"></a>Események azonosítói és leírása

| Eseményazonosító      | Esemény neve    | Esemény leírása | Kapcsolódó diagnosztikai kódok |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Az összekötő szolgáltatás elindult | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Az összekötő szolgáltatás leállt | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Az összekötő beléptetési tanúsítványának megújítása sikerült | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Az összekötő-beléptetési tanúsítvány megújítása nem sikerült. Telepítse újra az összekötőt. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Nem sikerült beolvasni az összekötő beléptetési tanúsítványát a beállításjegyzékből. Tekintse át az eseményhez kapcsolódó tanúsítvány ujjlenyomatának részleteit. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Diagnosztikai információk keresése az esemény részleteiben. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | A PKCS-tanúsítvány kiállítása sikeresen megtörtént. Tekintse át az eseményhez tartozó azonosító, a felhasználói azonosító, a HITELESÍTÉSSZOLGÁLTATÓ neve, a tanúsítványsablon neve és a tanúsítvány ujjlenyomatának részleteit. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Nem sikerült kiadni a PKCS-tanúsítványt. Tekintse át az eseményhez tartozó azonosító, a felhasználói azonosító, a HITELESÍTÉSSZOLGÁLTATÓ neve, a tanúsítványsablon neve és a tanúsítvány ujjlenyomatának részleteit. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | A tanúsítvány visszavonása sikerült. Tekintse át az eseményre vonatkozó azonosító, a felhasználói azonosító, a HITELESÍTÉSSZOLGÁLTATÓ neve és a tanúsítvány sorozatszámának részleteit. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Nem sikerült visszavonni a tanúsítványt. Tekintse át az eseményre vonatkozó azonosító, a felhasználói azonosító, a HITELESÍTÉSSZOLGÁLTATÓ neve és a tanúsítvány sorozatszámának részleteit. További információ: NDES SVC-naplók.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | A tanúsítvány kérésének vagy visszavonási idejének feltöltése sikerült. Tekintse át az esemény részleteit a feltöltés részleteinek megtekintéséhez. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Nem sikerült feltölteni a tanúsítvány kérését vagy az adatok visszavonását. A hiba okának megállapításához tekintse át az esemény részleteit > feltöltési állapotot.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | A tanúsítvány aláírására, az ügyféltanúsítvány letöltésére vagy a tanúsítvány visszavonására vonatkozó kérelem letöltése sikeresen megtörtént. Tekintse át az esemény részleteit a letöltés részleteinek megtekintéséhez.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Nem sikerült letölteni a tanúsítvány aláírására, az ügyféltanúsítvány letöltésére vagy a tanúsítvány visszavonására vonatkozó kérést. Tekintse át az esemény részleteit a letöltés részleteinek megtekintéséhez. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | A tanúsítvány regisztrációs pontja sikeresen ellenőrizte az ügyfél kérdését | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | A tanúsítvány regisztrációs pontja befejeződött, de elutasította a kérést. További részletekért tekintse meg a diagnosztikai kódot és az üzenetet. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | A tanúsítvány regisztrációs pontja nem tudta ellenőrizni az ügyfélre vonatkozó kihívásokat. További részletekért tekintse meg a diagnosztikai kódot és az üzenetet. Tekintse meg a kérdéshez tartozó eszköz AZONOSÍTÓjának az eseményazonosító részleteit. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | A tanúsítvány regisztrációs pontja sikeresen befejezte a értesítési folyamatot, és elküldte a tanúsítványt az eszköznek. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | A tanúsítvány regisztrációs pontja nem tudta befejezni az értesítési folyamatot. A kérelemmel kapcsolatos információkért tekintse meg az eseményekre vonatkozó adatokat. Ellenőrizze a kapcsolatot a NDES-kiszolgáló és a HITELESÍTÉSSZOLGÁLTATÓ között. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Diagnosztikai kódok

| Diagnosztikai kód | Diagnosztikai név | Diagnosztikai üzenet |
| -------------   | -------------   | -------------      |
| 0x00000000 | Sikeres  | Sikeres |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | A hitelesítésszolgáltató érvénytelen, vagy nem érhető el. Ellenőrizze, hogy a hitelesítésszolgáltató elérhető-e, és hogy a kiszolgáló tud-e kommunikálni vele. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | A Symantec-ügyfél hitelesítési tanúsítványa nem található a helyi tanúsítvány-tárolóban. További információkért tekintse meg a [Symantec regisztrációs engedélyezési tanúsítványának telepítése](certificates-digicert-configure.md#install-the-digicert-ra-certificate) című cikket.  |
| 0x00000402 | RevokeCert_AccessDenied  | A megadott fióknak nincs engedélye a tanúsítvány visszavonására a HITELESÍTÉSSZOLGÁLTATÓTÓL. A kiállító HITELESÍTÉSSZOLGÁLTATÓ meghatározásához tekintse meg a HITELESÍTÉSSZOLGÁLTATÓ neve mezőt az esemény-üzenet részletei között.  |
| 0x00000403 | CertThumbprint_NotFound  | Nem található a bemenetnek megfelelő tanúsítvány. Regisztrálja a tanúsítvány-összekötőt, és próbálkozzon újra. |
| 0x00000404 | Certificate_NotFound  | Nem található a megadott bemenetnek megfelelő tanúsítvány. Regisztrálja újra a tanúsítvány-összekötőt, és próbálkozzon újra. |
| 0x00000405 | Certificate_Expired  | A tanúsítvány lejárt. Regisztrálja újra a tanúsítvány-összekötőt a tanúsítvány megújításához, majd próbálkozzon újra. |
| 0x00000408 | CRPSCEPCert_NotFound  | A CRP titkosítási tanúsítványa nem található. Ellenőrizze, hogy a NDES és az Intune-összekötő helyesen van-e beállítva. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Nem sikerült beolvasni az aláíró tanúsítványt. Ellenőrizze, hogy az Intune-összekötő szolgáltatás megfelelően van-e konfigurálva, és fut-e az Intune-összekötő szolgáltatás. Ellenőrizze azt is, hogy a tanúsítvány letöltési eseményei sikeresek voltak-e. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Nem sikerült deszerializálni a SCEP-kérdés kérését. Ellenőrizze, hogy a NDES és az Intune-összekötő megfelelően van-e beállítva. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Lejárt tanúsítvány miatt megtagadva a kérelem. Az ügyféleszközök újra próbálkoznak a felügyeleti kiszolgáló új kihívásának beszerzése után. |
| 0x0FFFFFFFF | Unknown_Error  | A kérés nem hajtható végre, mert kiszolgálóoldali hiba történt. Kérjük, próbálkozzon újból. |


## <a name="next-steps"></a>Következő lépések
További segítségért tekintse [meg Microsoft Intune útmutató SCEP-profiljának hibaelhárítása című témakört](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) .
