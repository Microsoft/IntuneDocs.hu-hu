---
title: Hálózati végpontok az Egyesült Államok kormányának üzembe helyezéséhez – Microsoft Intune
titleSuffix: ''
description: Tekintse át az Egyesült államokbeli kormányzati végpontokat az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfa93bb758447c872d172ded7706fd7507a42f11
ms.sourcegitcommit: c7c6be3833d9a63d43f31d598b555b49b33cf5cb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/03/2020
ms.locfileid: "76966283"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Az Egyesült Államok kormányzati végpontja Microsoft Intune

Ezen a lapon az Intune-környezetekben a proxybeállítások számára szükséges Egyesült államokbeli kormányzati végpontok szerepelnek.

A tűzfalak és proxykiszolgálók mögötti eszközök kezeléséhez engedélyeznie kell az Intune-nal való kommunikációt.

- A proxykiszolgálónak támogatnia kell mind a **HTTP (80)** , mind a **HTTPS (443)** protokollt, mert az Intune-ügyfelek mindkét protokollt használják
- Bizonyos feladatokhoz (például a szoftverfrissítések letöltéséhez) az Intune-nak nem hitelesített proxykiszolgáló-hozzáférésre van szüksége a manage.microsoft.com

Az egyes ügyfélszámítógépeken módosíthatja a proxykiszolgáló beállításait. A megadott proxykiszolgáló mögött található ügyfélszámítógépek beállításainak módosításához Csoportházirend beállításokat is használhat.

A felügyelt eszközöket úgy kell beállítani, hogy **Minden felhasználó** hozzáférjen a szolgáltatásokhoz a tűzfalon keresztül.

További információ a Windows 10 automatikus regisztrálásáról és az eszközök regisztrálásáról az USA kormányzati ügyfelei számára: [Windowsos eszközök](../enrollment/windows-enroll.md#windows-10-auto-enrollment-and-device-registration)regisztrációjának beállítása.

A következő táblázat az Intune-ügyfél által elért portokat és szolgáltatásokat tartalmazza:

|**Végpont**|**IP-cím**|
|---------------------|-----------|
|*. manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Az Egyesült Államok kormányzati ügyfelei által kijelölt végpontok:
- Azure Portal: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Intune Céges portál: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>A partneri szolgáltatási végpontok, amelyeket az Intune a következőktől függ:
- AAD-szinkronizáló szolgáltatás: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https:\//login.microsoftonline.us
- Directory-proxy: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- HRE gráf: https:\//directory.microsoftazure.us és https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Windows leküldéses Notification Services
A mobileszköz-kezelés (MDM) használatával kezelt Intune által felügyelt eszközökön a Windows leküldéses Notification Services (WNS) szükséges az eszközök műveleteihez és más azonnali tevékenységekhez. További információ: [vállalati tűzfal és proxy konfigurációk a WNS-forgalom támogatásához](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## <a name="apple-device-network-information"></a>Apple-eszközhálózati információ

|**Használatban**|**Állomásnév (IP-cím/alhálózat)**|**Protokoll**|**Port**|
|------------|-----------|------------|-----------|
|Apple-kiszolgálók tartalmának beolvasása és megjelenítése|itunes.apple.com<br>\*. itunes.apple.com<br>\*. mzstatic.com<br>\*. phobos.apple.com<br>\*. phobos.itunes-apple.com.akadns.net|HTTP|80|
|Kommunikáció a APNS-kiszolgálókkal|#-courier.push.apple.com<br>a "#" a 0 és 50 közötti véletlenszerű szám.|TCP|5223 és 443|
|Különböző függvények, például az Internet, az iTunes Store, a macOS App Store, az iCloud, az üzenetküldés stb.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 vagy 443|

További információkért lásd:

- [Apple-szoftvertermékek által használt TCP-és UDP-portok](https://support.apple.com/HT202944)
- [A macOS, az iOS és az iTunes Server Host Connections és az iTunes háttér-folyamatai](https://support.apple.com/HT201999)
- [Ha a macOS-és iOS-ügyfelek nem kapnak Apple leküldéses értesítéseket](https://support.apple.com/HT203609)

## <a name="next-steps"></a>További lépések
[Microsoft Intune hálózati végpontok](intune-endpoints.md)

