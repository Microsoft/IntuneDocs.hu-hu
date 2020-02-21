---
title: Zimperium MTD-összekötő az Intune-nal
titleSuffix: Intune on Azure
description: Megismerheti az Intune a Zimperium Mobile Threat Defense-szel való integrálását, amellyel vezérelheti a mobileszközök a vállalati erőforrásokhoz való hozzáférését.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d0fe5634e5af6ef4c6f19e067131f151733c0b5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515237"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Zimperium Mobile Threat Defense-összekötő az Intune-nal

A mobileszköz-hozzáférés a vállalati erőforrásokhoz a feltételes hozzáférés használatával szabályozható a Zimperium által végzett, a Microsoft Intune-nal integrálható Mobile Threat Defense (MTD) megoldás kockázatértékelése alapján. A kockázatfelmérés a Zimperium alkalmazást futtató eszközökről gyűjtött telemetriai adatokon alapul.

A feltételes hozzáférési szabályzatok az Intune-eszköz megfelelőségi szabályzatai által engedélyezett Zimperium kockázatértékelés alapján konfigurálhatók. A kockázatértékelési házirend engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz az észlelt fenyegetések alapján.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a Zimperium a vállalati erőforrások védelmét?

Az Android és az iOS/iPadOS Zimperium alkalmazás rögzíti a fájlrendszer, a hálózati verem, az eszköz és az alkalmazás telemetria, ahol elérhető, majd a telemetria adatokat elküldi a Zimperium Cloud Service-nek, hogy felmérje az eszköz kockázatát a mobil fenyegetések ellen.

Az Intune eszközmegfelelőségi szabályzata tartalmaz egy szabályt a Zimperium mobilfenyegetések elleni védelméhez, amely a Zimperium kockázatfelmérésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét. Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a felhasználók hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A mobileszközeikre telepített Zimperium mobilalkalmazás segítséget nyújt a felhasználóknak a probléma elhárításához és a vállalati erőforrásokhoz való hozzáférés visszaszerzéséhez.

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Az alábbi forgatókönyvek a Zimperium Intune-nal való integrációjához használhatók:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján

Ha az eszközön kártékony alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbiak:

- Hozzáférés a vállalati e-mailekhez

- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással

- Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![Kártékony alkalmazások fogalmi képe](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A szervizelés után a hozzáférés fogalmi képe](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![Wi-Fi-s hálózati elérés letiltása](./media/zimperium-mobile-threat-defense-connector/network_wifi_blocked_Zimperium.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított](./media/zimperium-mobile-threat-defense-connector/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![A SharePoint Online letiltása hálózati fenyegetések észlelése esetén](./media/zimperium-mobile-threat-defense-connector/network_spo_blocked_Zimperium.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A fenyegetés kiküszöbölését követően a SharePoint-hozzáférés ismét biztosított – példa](./media/zimperium-mobile-threat-defense-connector/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Támogatott platformok

- **Android 4.1 és újabb verziók**

- **iOS 8 és újabb verziók**

## <a name="prerequisites"></a>Előfeltételek

- Prémium szintű Azure Active Directory

- Microsoft Intune-előfizetés

- Zimperium Mobile Threat Defense-előfizetés

  - További információ: [Zimperium webhelye](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>További lépések

- [A Zimperium integrálása az Intune-nal](zimperium-mtd-connector-integration.md)

- [Zimperium-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Zimperiummal használható eszközmegfelelőségi szabályzat létrehozása](mtd-device-compliance-policy-create.md)

- [Zimperium MTD-összekötő engedélyezése](mtd-connector-enable.md)
