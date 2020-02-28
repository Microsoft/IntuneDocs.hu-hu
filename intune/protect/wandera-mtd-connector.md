---
title: A Wander Mobile Security beállítása az Intune-nal
titleSuffix: Intune on Azure
description: A Wanda Mobile Security beállítása a Microsoft Intune használatával a mobileszköz-hozzáférés szabályozásához a vállalati erőforrásokhoz.
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
ms.openlocfilehash: f82a64cdb66528e3e1d3a81fd6119c4a99dff504
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782262"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>A Wanda Mobile Threat Defense-összekötő az Intune-nal  

A mobil eszközök hozzáférésének szabályozása a vállalati erőforrásokhoz feltételes hozzáférés használatával a Wanda által végzett kockázatértékelés alapján. A Wanda egy Mobile Threat Defense-(MTD-) megoldás, amely integrálható Microsoft Intuneokkal.  A kockázat megállapítása az eszközökről a Wanda szolgáltatás által gyűjtött telemetria alapján történik, beleértve a következőket:
- Az operációs rendszer biztonsági rései
- Telepített kártékony alkalmazások
- Kártékony hálózati profilok
- Cryptojacking

A Wander kockázatértékelésén alapuló *feltételes hozzáférési* szabályzatok konfigurálhatók az Intune-eszköz megfelelőségi szabályzatai által engedélyezett módon. A kockázatértékelési házirend engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz az észlelt fenyegetések alapján.  

> [!NOTE]
> A Mobile Threat Defense gyártója nem regisztrált eszközök esetén nem támogatott.

## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a Wanderer Mobile Threat Defense a vállalati erőforrások védelmét?  

A Wanda Mobile App zökkenőmentesen telepíthető Microsoft Intune használatával. Ez az alkalmazás rögzíti a fájlrendszer, a hálózati verem, valamint az eszköz-és alkalmazás-telemetria (ahol elérhető). Ez az információ szinkronizálja a Wanda Cloud Service-t, hogy felmérje az eszköz kockázatát a mobil fenyegetések ellen. Ezek a kockázati szintű besorolások úgy konfigurálhatók, hogy megfeleljenek az igényeinek a Wanda konzolon, a RADARon.

A megfelelőségi szabályzat az Intune-ban a MTD alapuló szabályt tartalmaz a Wander kockázatértékelése alapján. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét.

A nem megfelelő eszközökhöz, például az Office 365-hez hasonló erőforrásokhoz való hozzáférés le lehet tiltani. A letiltott eszközökön lévő felhasználók útmutatást kapnak a Wanda alkalmazástól a probléma megoldásához és a hozzáférés visszaszerzéséhez.

## <a name="supported-platforms"></a>Támogatott platformok  

Az Intune-ban való regisztráláskor a következő platformok támogatottak:

- Android 5,0 és újabb verziók  
- iOS 10,2 és újabb verziók  

További információ a platformról és az eszközről: a [Wanda webhelyén](https://www.wandera.com/mobile-threat-defense/).

## <a name="prerequisites"></a>Előfeltételek  

- Microsoft Intune-előfizetés  
- Azure Active Directory  
- A Wanderer Mobile Threat Defense (korábban Wanda biztonságos)  

További információ: a [Wanda Mobile Security](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Az alábbiakban a Wanda MTD az Intune-nal való használatának gyakori forgatókönyvei láthatók.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján  

Ha kártékony alkalmazásokat, például kártevőket észlel az eszközökön, letilthatja az eszközöket a közös eszközökről, amíg el nem oldja a fenyegetést. Gyakori blokkok a következők:  
- Hozzáférés a vállalati e-mailekhez  
- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással  
- Hozzáférés vállalati alkalmazásokhoz  

**A kártékony alkalmazások észlelésének letiltása**:

![Kártékony alkalmazások fogalmi képe](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**A hozzáférés szervizelésen keresztüli**engedélyezése: 

![A szervizelés után a hozzáférés fogalmi képe](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján  

Észlelheti a hálózati fenyegetéseket, például a személyes támadásokat és a Wi-Fi-hálózatokhoz való hozzáférést az eszköz kockázata alapján.  

**Hálózati hozzáférés letiltása Wi-Fi-n keresztül**:  

![Wi-Fi-s hálózati elérés letiltása](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**A hozzáférés szervizelésen keresztüli**engedélyezése:  

![A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a közbeékelődéses ({1}man-in-the-middle{2}) támadást és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén**:  

![A SharePoint Online letiltása hálózati fenyegetések észlelése esetén](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**A hozzáférés szervizelésen keresztüli**engedélyezése:  

![A SharePoint-példa szervizelésének engedélyezése](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>További lépések

- [A Wander integrálása az Intune-nal](wandera-mtd-connector-integration.md)
- [A vándor alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [A bolyongó eszköz megfelelőségi szabályzatának létrehozása](mtd-device-compliance-policy-create.md)
- [A Wanda MTD-összekötő engedélyezése](mtd-connector-enable.md)
