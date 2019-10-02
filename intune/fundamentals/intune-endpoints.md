---
title: Microsoft Intune hálózati végpontok
titleSuffix: ''
description: Tekintse át az Intune-végpontokat.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18c5622d9ce2566d5edf6ac5ebdfc931c8638418
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731559"
---
# <a name="network-endpoints-for-microsoft-intune"></a>Microsoft Intune hálózati végpontok  

Ez a lap felsorolja az Intune-környezetekben a proxybeállítások számára szükséges IP-címeket és port-beállításokat.

Csak felhőalapú szolgáltatásként az Intune nem igényel helyszíni infrastruktúrát, például kiszolgálókat vagy átjárókat.

## <a name="access-for-managed-devices"></a>Hozzáférés a felügyelt eszközökhöz  

A tűzfalak és proxykiszolgálók mögötti eszközök kezeléséhez engedélyeznie kell az Intune-nal való kommunikációt.

- A proxykiszolgáló csak a **http (80)** és a **https (443)** protokollt támogatja, mert az Intune-ügyfelek mindkét protokollt használják. A Windows Information Protection a 444-es portot használja.
- Bizonyos feladatokhoz (például a klasszikus PC-ügynökhöz tartozó szoftverfrissítések letöltéséhez) az Intune-nak nem hitelesített proxykiszolgáló-hozzáférésre van szüksége a manage.microsoft.com

Az egyes ügyfélszámítógépeken módosíthatja a proxykiszolgáló beállításait. A megadott proxykiszolgáló mögött található ügyfélszámítógépek beállításainak módosításához Csoportházirend beállításokat is használhat.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

A felügyelt eszközöket úgy kell beállítani, hogy **Minden felhasználó** hozzáférjen a szolgáltatásokhoz a tűzfalon keresztül.

A következő táblázat az Intune-ügyfél által elért portokat és szolgáltatásokat tartalmazza:

|Tartományok    |IP-cím      |
|-----------|----------------|
|login.microsoftonline.com <br> *. officeconfig.msocdn.com <br> config.office.com <br> graph.windows.net| További információ: [Office 365-ös URL-címek és IP-címtartományok](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 <br>13.72.226.202<br>52.189.220.232|
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84<br>13.73.112.122<br>52.237.192.112|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com |40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212<br>52.147.8.239<br>40.115.69.185|
|portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com<br>portal.fei.amsub0502.manage.microsoft.com<br>m.fei.amsub0502.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|portal.fei.amsud0101.manage.microsoft.com<br>m.fei.amsud0101.manage.microsoft.com|13.72.226.202|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|fef.amsua0102.manage.microsoft.com|52.242.211.0|
|fef.amsua0702.manage.microsoft.com|52.232.225.75|
|fef.amsub0502.manage.microsoft.com|40.67.219.144|
|fef.msud01.manage.microsoft.com|20.40.178.139|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57<br>52.187.196.98<br>52.237.196.51|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180<br>52.187.196.173<br>52.156.162.48|
|*.manage.microsoft.com|40.82.248.224/28<br>20.189.105.0/24<br>20.37.153.0/24<br>20.37.192.128/25<br>20.38.81.0/24<br>20.41.1.0/24<br>20.42.1.0/24<br>20.42.130.0/24<br>20.42.224.128/25<br>20.43.129.0/24<br>40.119.8.128/25<br>40.74.25.0/24<br>40.82.249.128/25<br>40.80.184.128/25<br>52.150.137.0/25|


## <a name="network-requirements-for-powershell-scripts-and-win32-apps"></a>A PowerShell-parancsfájlok és a Win32-alkalmazások hálózati követelményei  

Ha az Intune-t használja PowerShell-parancsfájlok vagy Win32-alkalmazások üzembe helyezéséhez, hozzáférést kell biztosítania azokhoz a végpontokhoz is, amelyekben a bérlő jelenleg található.

|ASU | Tároló neve | Tartalomkézbesítési hálózat (CDN) |
| --- | --- |--- |
| AMSUA0601 | prodmsua06data | https:\//prodmsua06data.azureedge.net |
| AMSUA0602 | prodamsua0602data | https:\//prodamsua0602data.azureedge.net |
| AMSUA0101 | prodmsua01data | https:\//prodmsua01data.azureedge.net |
| AMSUA0201 | prodmsua02data | https:\//prodmsua02data.azureedge.net |
| AMSUA0202 | Prodmsua0202rcdata | https:\//prodamsua0202data.azureedge.net/ |
| AMSUA0401 | prodmsua04data | https:\//prodmsua04data.azureedge.net |
| AMSUA0402 | Prodmsua0402rcdata | https:\//prodamsua0402data.azureedge.net/ |
| AMSUA0501 | prodmsua05data | https:\//prodmsua05data.azureedge.net |
| AMSUA0502 | prodmsua0502data | https:\//prodmsua0502data.azureedge.net |
| AMSUB0101 | prodmsub01data | https:\//prodmsub01data.azureedge.net |
| AMSUB0102 | prodamsub0102data | https:\//prodamsub0102data.azureedge.net |
| AMSUB0201 | prodmsub02data | https:\//prodmsub02data.azureedge.net |
| AMSUB0202 | Prodmsub0202rcdata | https:\//prodamsub0202data.azureedge.net |
| AMSUB0301 | Prodmsub03data2 | https:\//prodmsub03data2.azureedge.net |
| AMSUB0302 | Prodmsub0302rcdata | https:\//prodamsub0302data.azureedge.net |
| AMSUB0501 | prodmsub05data | https:\//prodmsub05data.azureedge.net |
| AMSUC0101 | prodmsuc01data | https:\//prodmsuc01data.azureedge.net |
| AMSUC0201 | prodmsuc02data | https:\//prodmsuc02data.azureedge.net |
| AMSUC0301 | prodmsuc03data | https:\//prodmsuc03data.azureedge.net |
| AMSUC0501 | prodmsuc05data | https:\//prodmsuc05data.azureedge.net |
| AMSUA0701 | pemsua07rcdata | https:\//pemsua07data.azureedge.net |

## <a name="windows-push-notification-services-wns"></a>Windows leküldéses Notification Services (WNS)  

A mobileszköz-kezelés (MDM) használatával felügyelt Intune által felügyelt Windows-eszközök esetén az eszközök műveletei és egyéb azonnali tevékenységei a Windows leküldéses Notification Services (WNS) használatát igénylik. További információ: a [Windows értesítési forgalmának engedélyezése vállalati tűzfalakon keresztül](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config).  

## <a name="delivery-optimization-port-requirements"></a>Kézbesítési optimalizálási portra vonatkozó követelmények  

### <a name="port-requirements"></a>Portra vonatkozó követelmények  

A társközi forgalom esetében a kézbesítési optimalizálás a 7680-es TCP/IP-vagy 3544-alapú NAT-bejárást használja (opcionális Teredo). Az ügyfél és a szolgáltatás közötti kommunikációhoz HTTP vagy HTTPS protokollt használ a 80/443-as porton keresztül.

### <a name="proxy-requirements"></a>Proxyra vonatkozó követelmények  

A kézbesítési optimalizálás használatához engedélyeznie kell a byte Range kérelmeket. További információ: [Windows Update proxyra vonatkozó követelményei](https://docs.microsoft.com/windows/deployment/update/windows-update-troubleshooting).

### <a name="firewall-requirements"></a>A tűzfalra vonatkozó követelmények  

Engedélyezze a következő állomásnevek használatát a tűzfalon a kézbesítés optimalizálásának támogatásához.
Az ügyfelek és a kézbesítési optimalizálási felhő szolgáltatás közötti kommunikációhoz:
- \*. do.dsp.mp.microsoft.com

Kézbesítési optimalizálási metaadatok:
- \*. dl.delivery.mp.microsoft.com
- \*. emdl.ws.microsoft.com

## <a name="apple-device-network-information"></a>Apple-eszközhálózati információ  

|Használatban|Hostname (IP address/subnet)|Protocol|Port|
|-----|--------|------|-------|
|Apple-kiszolgálók tartalmának beolvasása és megjelenítése|itunes.apple.com<br>\*. itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Kommunikáció a APNS-kiszolgálókkal|#-courier.push.apple.com<br>a "#" a 0 és 50 közötti véletlenszerű szám.|    TCP     |  5223 és 443  |
|Különböző funkciók, többek között a World Wide Web, az iTunes Store, a macOS App Store, az iCloud, az üzenetküldés stb. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 vagy 443   |

További információkért lásd az Apple [szoftvertermékek által használt Apple TCP-és UDP](https://support.apple.com/en-us/HT202944)-portokat, [a MacOS-, iOS-és iTunes Server Host-kapcsolatokat](https://support.apple.com/en-us/HT201999), valamint az iTunes-alapú háttér-folyamatokat, és [Ha a MacOS-és iOS-ügyfelek nem kapnak Apple push-t értesítések](https://support.apple.com/en-us/HT203609).  