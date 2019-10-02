---
title: Lookout MTD-összekötő a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Megismerheti az Intune a Lookout Mobile Threat Defense-szel való integrálását, amellyel vezérelheti a mobileszközök a vállalati erőforrásokhoz való hozzáférését.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e16907f39fe8c6ea5e9a12f1e2b25026a5db225
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729247"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>A Mobile Endpoint Security-összekötő kilátója az Intune-nal

A Microsoft Intune-nal integrálható, Lookout nevű, veszélyforrások elleni mobileszköz-védelmi megoldás kockázatfelmérése alapján korlátozható a vállalati erőforrások mobil elérése. A kockázatfelmérés a Lookout által az eszközökről gyűjtött telemetriai adatokon alapul, például:
- Az operációs rendszer biztonsági rései
- Telepített kártékony alkalmazások
- Kártékony hálózati profilok

A feltételes hozzáférési szabályzatok az Intune megfelelőségi szabályzatai által engedélyezett kockázatértékelés alapján állíthatók be. A beállítások lehetővé teszik a nem megfelelő eszközök engedélyezését vagy letiltását az észlelt fenyegetések alapján.

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>Hogyan segít a vállalati erőforrások védelme az Intune-ban és a mobil Endpoint Security szolgáltatásban?
A Lookout mobilalkalmazása, a **Lookout for Work** telepítve van és fut a mobileszközökön. Az alkalmazás rögzíti a fájlrendszer, a hálózati protokollkészlet, valamint az eszközök és az alkalmazások telemetriai adatait, ha elérhetők, és továbbítja őket a Lookout veszélyforrások elleni eszközvédelmi felhőszolgáltatásnak, amely kiszámítja az eszköz kockázatát a mobil veszélyforrások tekintetében. A Lookout konzolon igény szerint módosítható a fenyegetések kockázatiszint-besorolása.  

Az Intune megfelelőségi szabályzata tartalmaz egy szabályt a Lookout Mobile Threat Defense-hez, amely a Lookout kockázatértékelésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét.

Ha az eszköz nem megfelelőnek minősül, akkor letiltható a hozzáférés az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A letiltott eszközök felhasználói a probléma megoldásához és a hozzáférés visszaszerzéséhez szükséges lépéseket kapják meg. Az útmutatót a Lookout for Work alkalmazás szolgáltatja.

## <a name="supported-platforms"></a>Támogatott platformok  
A Lookout az alábbi Intune-ban regisztrált platformokat támogatja:
* **Android 4.1 és újabb verziók**  
* **iOS 8 és újabb verziók**  

A platformmal és a nyelvi támogatással kapcsolatos további információkért látogasson el a [kilátó webhelyére](https://personal.support.lookout.com/hc/articles/114094140253).  

## <a name="prerequisites"></a>Előfeltételek
* Vállalati előfizetés a Lookout Mobile EndPoint Securityhez  
* Microsoft Intune-előfizetés
* Prémium szintű Azure Active Directory
* Nagyvállalati mobilitás és biztonság (EMS) E3 vagy E5, felhasználókhoz hozzárendelt licencekkel.  

További információ: [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Az alábbiakban a Mobile Endpoint Security és az Intune együttes használatának gyakori forgatókönyvei láthatók.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján
Ha az eszközön rosszindulatú alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbiak:
* Hozzáférés a vállalati e-mailekhez
* A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással
* Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![A szabályzat fogalmi képe blokkolja a hozzáférést rosszindulatú alkalmazások miatt](./media/lookout-mobile-threat-defense-connector/malicious-apps-blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A szervizelést követően az eszközök hozzáférését bemutató fogalmi kép](./media/lookout-mobile-threat-defense-connector/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján
Észleli a hálózat elleni támadásokat, például a közbeékelődéses (man-in-the-middle) támadásokat, és az eszközkockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![A hálózati fenyegetések alapján a WiFi-hozzáférés blokkolását bemutató kép](./media/lookout-mobile-threat-defense-connector/network-wifi-blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A feltételes hozzáférés fogalmi képe, amely lehetővé teszi a hozzáférést a szervizelés után](./media/lookout-mobile-threat-defense-connector/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a közbeékelődéses (man-in-the-middle) támadást és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![A SharePoint Online-hoz való hozzáférés blokkolásának fogalmi képe](./media/lookout-mobile-threat-defense-connector/network-spo-blocked.png)


**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A hálózati fenyegetés szervizelése után a hozzáférés engedélyezésének fogalmi képe](./media/lookout-mobile-threat-defense-connector/network-spo-unblocked.png)

## <a name="next-steps"></a>További lépések
A legfontosabb lépések a megoldás megvalósítása érdekében:
1. [A Lookout-integráció beállítása](lookout-mtd-connector-integration.md)
2. [A mobil végpontok biztonságának engedélyezése az Intune-ban](mtd-connector-enable.md)
3. [A Lookout for Work felvétele és hozzárendelése](mtd-apps-ios-app-configuration-policy-add-assign.md)
4. [A Lookout eszközmegfelelőségi szabályzatának konfigurálása](mtd-device-compliance-policy-create.md)
