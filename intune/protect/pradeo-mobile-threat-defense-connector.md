---
title: A Pradeo Mobile Threat Defense-összekötő működése az Intune-nal
titleSuffix: Intune on Azure
description: Ismerje meg, hogyan integrálhatja az Intune-t a Pradeo Mobile Threat Defense-összekötővel a mobileszközök hozzáférésének szabályozásához a vállalati erőforrásokhoz.
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
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 262d36817e86c8087c6ef4b642d1bd53b1511104
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782109"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>A Pradeo Mobile Threat Defense-összekötő működése az Intune-nal

A mobileszköz-hozzáférés a vállalati erőforrásokhoz a feltételes hozzáférés használatával szabályozható a Pradeo által végzett, a Microsoft Intune-nal integrálható Mobile Threat Defense (MTD) megoldás kockázatértékelése alapján. A kockázatfelmérés a Pradeo alkalmazást futtató eszközökről gyűjtött telemetriai adatokon alapul.

A feltételes hozzáférési szabályzatokat az Intune-eszköz megfelelőségi szabályzatai által engedélyezett Pradeo kockázatértékelés alapján konfigurálhatja, amellyel engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz az észlelt fenyegetések alapján.

> [!NOTE]
> A Mobile Threat Defense gyártója nem regisztrált eszközök esetén nem támogatott.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a Pradeo a vállalati erőforrások védelmét?

Az Android és az iOS/iPadOS Pradeo alkalmazás rögzíti a fájlrendszer, a hálózati verem, az eszköz és az alkalmazás telemetria, ahol elérhető, majd a telemetria adatokat elküldi a Pradeo Cloud Service-nek, hogy felmérje az eszköz kockázatát a mobil fenyegetések ellen.

Az Intune eszközmegfelelőségi szabályzata tartalmaz egy szabályt a Pradeo Mobile Threat Defense-hez, amely a Pradeo kockázatfelmérésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét. Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a felhasználók hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A mobileszközeikre telepített Pradeo mobilalkalmazás segítséget nyújt a felhasználóknak a probléma elhárításához és a vállalati erőforrásokhoz való hozzáférés visszaszerzéséhez.

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Néhány gyakori helyzet:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján

Ha az eszközön rosszindulatú alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbi műveletek:

- Hozzáférés a vállalati e-mailekhez

- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással

- Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![Kártékony alkalmazások fogalmi képe](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A program kártevőt észlelt, hozzáférés megadva](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a **közbeékelődéses (man-in-the-middle)** támadásokat, és az eszközkockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![Wi-Fi-s hálózati elérés letiltása](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Szervizeléssel biztosított hozzáférés fogalmi képe](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a **közbeékelődéses (man-in-the-middle)** támadásokat és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![A SharePoint Online letiltása hálózati fenyegetések észlelése esetén](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A SharePoint-példa szervizeléséhez biztosított hozzáférés fogalmi képe](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Támogatott platformok

- **Android 4.0.3 és újabb verziók**

- **iOS 7 és újabb verziók**

## <a name="prerequisites"></a>Előfeltételek

- Prémium szintű Azure Active Directory

- Microsoft Intune-előfizetés

- Pradeo Security for Mobile Threat Defense-előfizetés

  - További információt a [Pradeo webhelyén](https://www.pradeo.com/en-US/mobile-threat-protection) találhat.

## <a name="next-steps"></a>További lépések

- [A Pradeo integrálása az Intune-nal](pradeo-mtd-connector-integration.md)

- [Pradeo-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Pradeo-eszközmegfelelőségi szabályzat létrehozása](mtd-device-compliance-policy-create.md)

- [A Pradeo MTD-összekötő engedélyezése](mtd-connector-enable.md)
