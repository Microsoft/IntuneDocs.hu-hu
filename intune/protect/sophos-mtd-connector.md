---
title: A Sophos Mobile használata az Intune-nal
titleSuffix: Intune on Azure
description: A Sophos Mobile megoldás használata a Microsoft Intune használatával a mobileszközök hozzáférésének szabályozásához a vállalati erőforrásokhoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 816968d512b73a8592c7a86b39c41057aa99e827
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782053"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>A Sophos Mobile Threat Defense-összekötő az Intune-nal
A mobil eszközök hozzáférését a vállalati erőforrásokhoz feltételes hozzáférés használatával szabályozhatja a Sophos Mobile, a Mobile Threat Defense (MTD) által a Microsoft Intune-nal integrálható megoldás alapján. A rendszer a Sophos Mobile alkalmazást futtató eszközökről gyűjtött telemetria alapján méri a kockázatot.
Az Intune-eszköz megfelelőségi szabályzatai által engedélyezett, a Sophos Mobile Risk Assessment szolgáltatáson alapuló feltételes hozzáférési szabályzatokat konfigurálhatja, amelyekkel engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz az észlelt fenyegetések alapján.

> [!NOTE]
> A Mobile Threat Defense gyártója nem regisztrált eszközök esetén nem támogatott.

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Hogyan segít az Intune és a Sophos Mobile a vállalati erőforrások védelmében?
A Sophos Mobile App for Android és az iOS/iPadOS rögzíti a fájlrendszer, a hálózati verem, az eszköz és az alkalmazás telemetria, ahol elérhető, majd elküldi a telemetria adatokat a Sophos Mobile Cloud Service-nek, hogy felmérje az eszköz kockázatát a mobil fenyegetések ellen.
Az Intune-eszköz megfelelőségi szabályzata tartalmaz egy szabályt a Sophos Mobile Threat Defense számára, amely a Sophos Mobile Risk Assessment alapján történik. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét. Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a felhasználók hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A felhasználók az eszközökön telepített Sophos Mobile alkalmazásból is kaphatnak útmutatást a probléma megoldásához és a vállalati erőforrásokhoz való hozzáférés visszaszerzéséhez.  

## <a name="sample-scenarios"></a>Mintaforgatókönyvek
Néhány gyakori helyzet:  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján
Ha az eszközön rosszindulatú alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbi műveletek:
- Hozzáférés a vállalati e-mailekhez
- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással
- Hozzáférés vállalati alkalmazásokhoz

**A kártékony alkalmazások észlelésének letiltása**:
 
![Kártékony alkalmazások fogalmi képe](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**A hozzáférés szervizelésen keresztüli**engedélyezése:  
![szervizelési](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png) után kiadott fogalmi rendszerkép

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján  
Észlelheti a hálózatra irányuló fenyegetéseket, például a személyes támadásokat, és az eszköz kockázata alapján biztosíthatja a Wi-Fi-hálózatokhoz való hozzáférést.  

**Hálózati hozzáférés letiltása Wi-Fi-n keresztül**:  
![hálózati hozzáférés letiltása Wi-Fi-](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**A hozzáférés szervizelésen keresztüli**engedélyezése:   
a szervizelés](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png) ![hozzáférés engedélyezett  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján  
Észlelheti a hálózatra irányuló fenyegetéseket, például az ember által a középső támadásokat, és megakadályozhatja a vállalati fájlok szinkronizálását az eszköz kockázata alapján.  

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén**:   
a SharePoint Online ![letiltása hálózati fenyegetések észlelésekor](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**A hozzáférés szervizelésen keresztüli**engedélyezése:  
a SharePoint-példa szervizeléséhez ![hozzáférés biztosított](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png)  

## <a name="supported-platforms"></a>Támogatott platformok  
- Android 5,0 és újabb verziók
- iOS 11,0 és újabb verziók

## <a name="prerequisites"></a>Előfeltételek  
- Prémium szintű Azure Active Directory
- Microsoft Intune-előfizetés 
- A Sophos Mobile Threat Defense-előfizetés

További információ: a [Sophos webhelye](https://www.sophos.com/en-us/products/mobile-control.aspx).

## <a name="next-steps"></a>További lépések  
- [A Sophos integrálása az Intune-nal](sophos-mtd-connector-integration.md)
- [A Sophos-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Sophos-eszköz megfelelőségi szabályzatának létrehozása](mtd-device-compliance-policy-create.md)
- [A Sophos MTD-összekötő engedélyezése](mtd-connector-enable.md)
