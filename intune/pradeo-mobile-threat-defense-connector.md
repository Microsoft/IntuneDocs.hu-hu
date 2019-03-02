---
title: A Pradeo Mobile Threat Defense-összekötő működése az Intune-nal
titleSuffix: Intune on Azure
description: A Pradeo Mobile Threat Defense-összekötő beállítása az Intune-hoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6a511a9fe0316b0db3ffae39b85f85c8b8b5aa00
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229003"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>A Pradeo Mobile Threat Defense-összekötő működése az Intune-nal

A Microsoft Intune-nal integrálható, Pradeo által irányított, veszélyforrások elleni mobileszköz-védelmi (MTD) megoldás kockázatfelmérése alapján feltételes hozzáféréssel korlátozható a vállalati erőforrások mobil elérése. A kockázatfelmérés a Pradeo alkalmazást futtató eszközökről gyűjtött telemetriai adatokon alapul.

Feltételes hozzáférési szabályzatokat konfigurálhat az Intune eszközmegfelelőségi szabályzataira épülő Pradeo-kockázatfelmérés alapján, és ezek révén az észlelt fenyegetések alapján engedélyezheti vagy tilthatja le a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a Pradeo a vállalati erőforrások védelmét?

Az Androidra és iOS-re készült Pradeo alkalmazás rögzíti a fájlrendszer, a hálózati protokollkészlet, valamint az eszközök és az alkalmazások telemetriai adatait, ha elérhetők, és továbbítja őket a Pradeo felhőszolgáltatásnak, amely felméri az eszköz kockázatát a mobil veszélyforrások tekintetében.

Az Intune eszközmegfelelőségi szabályzata tartalmaz egy szabályt a Pradeo Mobile Threat Defense-hez, amely a Pradeo kockázatfelmérésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét. Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a felhasználók hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A mobileszközeikre telepített Pradeo mobilalkalmazás segítséget nyújt a felhasználóknak a probléma elhárításához és a vállalati erőforrásokhoz való hozzáférés visszaszerzéséhez.

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Néhány gyakori helyzet:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján

Ha az eszközön rosszindulatú alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbi műveletek:

-   Hozzáférés a vállalati e-mailekhez

-   A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással

-   Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![Észlelt rosszindulatú alkalmazások fogalmi képe](./media/pradeo_maliciousapps_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A program kártevőt észlelt, hozzáférés megadva](./media/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a **közbeékelődéses (man-in-the-middle)** támadásokat, és az eszközkockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![Wi-Fi-s hálózati elérés letiltása](./media/pradeo_network_wifi_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A fenyegetés kiküszöbölését követően hozzáférés fogalmi képe](./media/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a **közbeékelődéses (man-in-the-middle)** támadásokat és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![A SharePoint Online letiltása hálózati fenyegetések észlelése esetén](./media/pradeo_network_spo_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Megadja a hozzáférést a Sharepoint például a fenyegetés kiküszöbölését fogalmi képe](./media/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Támogatott platformok

-   **Android 4.0.3 és újabb verziók**

-   **iOS 7 és újabb verziók**

## <a name="prerequisites"></a>Előfeltételek

-   Prémium szintű Azure Active Directory

-   Microsoft Intune-előfizetés

-   Pradeo Security for Mobile Threat Defense-előfizetés

    -   További információt a [Pradeo webhelyén](https://www.pradeo.com/en-US/mobile-threat-protection) találhat.

## <a name="next-steps"></a>További lépések

- [A Pradeo integrálása az Intune-nal](pradeo-mtd-connector-integration.md)

- [Pradeo-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Pradeo-eszközmegfelelőségi szabályzat létrehozása](mtd-device-compliance-policy-create.md)

- [A Pradeo MTD-összekötő engedélyezése](mtd-connector-enable.md)
