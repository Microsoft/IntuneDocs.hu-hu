---
title: Adatbiztonság és-megosztás az Intune-ban
titleSuffix: Microsoft Intune
description: Ismerje meg, hogy a személyes adatai hogyan biztonságosak és megoszthatók az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53480b7a2e008af46f4f8929cc6321e10b042b33
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306748"
---
# <a name="data-security-and-sharing-in-intune"></a>Adatbiztonság és-megosztás az Intune-ban


## <a name="data-security"></a>Adatbiztonság

A Microsoft Intune a Microsoft nagyvállalati mobilitási és biztonsági csomagjának Cloud Service-ajánlatának kulcsfontosságú összetevője. Az [adatirányítási stratégia](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx)támogatásához minden Microsoft Cloud Services-szolgáltatást a [Microsoft adatvédelmi](https://www.microsoft.com/en-us/trustcenter/privacy) és a [Microsoft biztonsági](https://www.microsoft.com/en-us/trustcenter/security/) módszereivel dolgozunk ki.  

Microsoft Intune ugyanazokat a technikai és szervezeti mértékeket követi, mint amelyeket az Microsoft Azure Service-csapatok az adatmegsértési folyamatokkal szembeni védelemre szánnak.

További információ: [szolgáltatás megbízhatósági portálja](https://www.microsoft.com/en-us/TrustCenter/stp).

Az Intune az adatminimalizálás módszereit használja, például:

- Összesítési
- nem kötelező adatgyűjtés egyes funkciókhoz
- kevésbé pontos vagy bizalmas adatok

Az Intune a támogatási incidensek esetében olyan technikákat is alkalmaz, mint például a RBAC és a JiT Security, hogy alapértelmezés szerint biztosítsa az adatvédelem védelmét. 

### <a name="data-breach-reporting"></a>Adatmegsértési jelentéskészítés

A felhasználó által jelentett biztonsági incidens (CRSI) azonosítása esetén az ügyfelek értesítést kapnak. Ez a folyamat a Microsoft O365 csapatával folytatott kommunikációt is magában foglalja a Microsoft O365 ügyfeleinek az Intune-nal való megsértéséről.

## <a name="data-sharing"></a>Adatmegosztás

Ha a bérlői rendszergazdák bizonyos funkciókat bekapcsolnak (például az Apple Készülékregisztrációs program), a Microsoft Intune a megfelelő harmadik felekkel megoszthatja az adatmegosztáshoz szükséges rendszergazdai engedélyt. Ilyen esetekben az Intune a következőket oszthatja meg személyes adatként:

- A Microsoft ügynökökként működő harmadik felek.
- Harmadik felek nem a Microsoft ügynökei, hanem csak akkor, ha a bérlői rendszergazdák explicit módon engedélyezik az Intune-engedélyt.

Az [online szolgáltatások alvállalkozói listájában](https://aka.ms/Online_Serv_Subcontractor_List)minden Microsoft-ügynökként működő harmadik fél szerepel.

Az ilyen entitásokkal rendelkező adatok megosztása az ügyfelek és a technikai támogatás, a szolgáltatások karbantartása és egyéb műveletek támogatása érdekében történik.

A bérlő a harmadik féllel kötött szerződése szabályozza a harmadik fél szolgáltatásában tárolt Intune személyes adatvédelmet. Emellett engedélyezi az Intune számára, hogy adatokat továbbítson a harmadik féltől származó szolgáltatásnak.  

Az egyes harmadik felekkel megosztott adatokkal kapcsolatos információkért tekintse meg a következő cikkeket:
- [Az Intune által az Apple-nek küldött adatokat](data-intune-sends-to-apple.md)
- [Az Intune által a Google-nek küldött adatokat](data-intune-sends-to-google.md)
- [Az Apple által az Intune-nak küldött adatokat](data-apple-sends-to-intune.md)
- [A Google által az Intune-nak küldött adatokat](data-google-sends-to-intune.md)
- [A JAMF Pro által küldött adatokat az Intune-nak küldi](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>Adatmegosztás System Center Configuration Manager

A Microsoft Intune nem oszt meg semmilyen adatSystem Center Configuration Managert. System Center Configuration Manager az ügyfél által közvetlenül üzembe helyezett, felügyelt és üzemeltetett helyszíni termék. A Configuration Manager által összegyűjtött diagnosztikai és használati adatok csak a telepítési élmény, a minőség és a jövőbeli kiadások biztonságának javításához szükségesek.

További információ: [diagnosztikai és használati adatok a SCCM](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). 


## <a name="next-steps"></a>Következő lépések

Ismerje meg, hogyan [tekintheti meg és javítsa](privacy-data-view-correct.md) ki a személyes adatok az Intune-ban.
