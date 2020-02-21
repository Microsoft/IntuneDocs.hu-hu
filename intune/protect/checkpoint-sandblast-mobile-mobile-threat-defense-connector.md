---
title: Check Point SandBlast MTD beállítása
titleSuffix: Microsoft Intune
description: Megismerheti az Intune a Check Point SandBlast Mobile Threat Defense-szel való integrálását, amellyel vezérelheti a mobileszközök a vállalati erőforrásokhoz való hozzáférését.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b740ed1e16f60b15991f1aa450e623cd20b62ea
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515135"
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Check Point SandBlast Mobile Threat Defense-összekötő az Intune-nal

A mobil eszközök hozzáférését a vállalati erőforrásokhoz feltételes hozzáférés használatával szabályozhatja a következő, az Microsoft Intune-nal integrált Mobile Threat Defense-megoldás által végzett kockázatértékelés alapján. A kockázatfelmérés a Check Point SandBlast Mobile alkalmazást futtató eszközökről gyűjtött telemetriai adatokon alapul.

A feltételes hozzáférési szabályzatok az Intune-eszközök megfelelőségi házirendjein keresztül engedélyezhető, a nem megfelelő eszközök hozzáférésének engedélyezéséhez vagy letiltásához használhatók a vállalati erőforrások észlelése alapján fenyegetések.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a Check Point SandBlast Mobile a vállalati erőforrások védelmét?

Jelölje be az Android és az iOS/iPadOS rendszerhez készült Service-alapú mobil alkalmazások rögzítik a fájlrendszer, a hálózati verem, az eszköz és az alkalmazás telemetria, ahol elérhetők, majd a telemetria-adatokat elküldi a pipa a betakarítási felhőbe, hogy felmérje az eszköz kockázatát a mobil fenyegetések ellen.

Az Intune eszközmegfelelőségi szabályzata tartalmaz egy szabályt a Check Point SandBlast Mobile Threat Defense-hez, amely a Check Point SandBlast kockázatfelmérésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét. Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a felhasználók hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A mobileszközeikre telepített Check Point SandBlast mobilalkalmazás segítséget nyújt a felhasználóknak a probléma elhárításához és a vállalati erőforrásokhoz való hozzáférés visszaszerzéséhez.

Néhány gyakori helyzet:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján

Ha az eszközön kártékony alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbiak:

- Hozzáférés a vállalati e-mailekhez

- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással

- Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![Check Point MTD – letiltás kártékony alkalmazás észlelése esetén](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-2.PNG)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Check Point MTD – hozzáférés engedélyezve](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![Check Point MTD – Wi-Fi-s hálózati elérés letiltása](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-4.PNG)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Check Point MTD – Wi-Fi-hozzáférés engedélyezve](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![Check Point MTD – SharePoint Online-hozzáférés letiltása](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-6.PNG)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Check Point MTD – SharePoint Online-hozzáférés engedélyezve](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-7.PNG)

## <a name="supported-platforms"></a>Támogatott platformok

- **Android 4.1 és újabb verziók**

- **iOS 8 és újabb verziók**

## <a name="pre-requisites"></a>Előfeltételek

- Prémium szintű Azure Active Directory

- Microsoft Intune-előfizetés

- Check Point SandBlast Mobile Threat Defense-előfizetés
  - További információt a [CheckPoint SandBlast webhelyén](https://www.checkpoint.com/) találhat.

## <a name="next-steps"></a>További lépések

- [A Check Point SandBlast integrálása az Intune-nal](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Check Point SandBlast Mobile-alkalmazás beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [CheckPoint SandBlast Mobile eszközmegfelelőségi szabályzat létrehozása](mtd-device-compliance-policy-create.md)

- [A CheckPoint SandBlast Mobile MTD-összekötő engedélyezése](mtd-connector-enable.md)
