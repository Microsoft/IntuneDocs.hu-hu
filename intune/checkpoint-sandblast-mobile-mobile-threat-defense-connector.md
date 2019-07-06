---
title: Check Point SandBlast MTD beállítása
titleSuffix: Microsoft Intune
description: Megismerheti az Intune a Check Point SandBlast Mobile Threat Defense-szel való integrálását, amellyel vezérelheti a mobileszközök a vállalati erőforrásokhoz való hozzáférését.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9438c3c566dc62acfa7567428ebe3a6a6be4777
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572568"
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Check Point SandBlast Mobile Threat Defense-összekötő az Intune-nal

Szabályozhatja, hogy a Check Point SandBlast Mobile, a Microsoft Intune-nal integrálható mobil veszélyforrások elleni védelmi megoldás kockázatfelmérése alapján feltételes hozzáféréssel a vállalati erőforrások mobil elérése. A kockázatfelmérés a Check Point SandBlast Mobile alkalmazást futtató eszközökről gyűjtött telemetriai adatokon alapul.

Engedélyezve van az Intune eszközmegfelelőségi szabályzatai által, amely segítségével engedélyezése vagy letiltása nem megfelelő eszközök hozzáférését a vállalati erőforrások észlelt Check Point SandBlast Mobile-kockázatfelmérés alapján történő feltételes hozzáférési szabályzatok konfigurálhatók az fenyegetések.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a Check Point SandBlast Mobile a vállalati erőforrások védelmét?

Az Androidra és iOS-re készült Check Point SandBlast Mobile alkalmazás rögzíti a fájlrendszer, a hálózati protokollkészlet, valamint az eszközök és az alkalmazások telemetriai adatait, ha elérhetők, és továbbítja őket a Check Point SandBlast felhőszolgáltatásnak, amely felméri az eszköz kockázatát a mobil veszélyforrások tekintetében.

Az Intune eszközmegfelelőségi szabályzata tartalmaz egy szabályt a Check Point SandBlast Mobile Threat Defense-hez, amely a Check Point SandBlast kockázatfelmérésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét. Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a felhasználók hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A mobileszközeikre telepített Check Point SandBlast mobilalkalmazás segítséget nyújt a felhasználóknak a probléma elhárításához és a vállalati erőforrásokhoz való hozzáférés visszaszerzéséhez.

<!-- ## Sample scenarios 
closing syntax for comment above is missing. Please insert closing syntax at intended location. -->

Néhány gyakori helyzet:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján

Ha az eszközön kártékony alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbiak:

- Hozzáférés a vállalati e-mailekhez

- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással

- Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![Check Point MTD – letiltás kártékony alkalmazás észlelése esetén](./media/checkpoint-MTD-2.PNG)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Check Point MTD – hozzáférés engedélyezve](./media/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![Check Point MTD – Wi-Fi-s hálózati elérés letiltása](./media/checkpoint-MTD-4.PNG)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Check Point MTD – Wi-Fi-hozzáférés engedélyezve](./media/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![Check Point MTD – SharePoint Online-hozzáférés letiltása](./media/checkpoint-MTD-6.PNG)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![Check Point MTD – SharePoint Online-hozzáférés engedélyezve](./media/checkpoint-MTD-7.PNG)

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
