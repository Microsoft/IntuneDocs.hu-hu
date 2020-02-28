---
title: Symantec-összekötő a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Megismerheti az Intune szolgáltatás Symantec Endpoint Protection Mobile-lal való integrálását, amellyel vezérelheti a mobileszközök vállalati erőforrásokhoz való hozzáférését.
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
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60bad9299a3751474ef01220a7c18f16be329448
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782081"
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Symantec Endpoint Protection Mobile-összekötő

A vállalati erőforrásokhoz való hozzáférést a Symantec Endpoint Protection Mobile (SEP Mobile), a Microsoft Intune-nal integrálható Mobile Threat Defense-megoldás kockázatértékelésén alapuló feltételes hozzáférés használatával szabályozhatja. A kockázatfelmérés a SEP Mobile által az eszközökről gyűjtött telemetriai adatokon alapul, például:

- Fizikai védelem

- Hálózatvédelem

- Alkalmazásvédelem

- Biztonsági rések elleni védelem

Az Intune-eszközök megfelelőségi házirendjein keresztül engedélyezheti a SEP Mobile Risk Assessment használatát, majd feltételes hozzáférési szabályzatokkal engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz az észlelt fenyegetések alapján.

> [!NOTE]
> A Mobile Threat Defense gyártója nem regisztrált eszközök esetén nem támogatott.

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a SEP Mobile a vállalati erőforrások védelmét?

A SEP Mobile apps for Android vagy iOS/iPadOS rögzíti a fájlrendszer, a hálózati verem, az eszköz és az alkalmazás telemetria, ahol elérhető, majd elküldi a Symantec Cloud Service-nek, hogy felmérje az eszköz kockázatát a mobil fenyegetések ellen.

Az Intune eszközmegfelelőségi szabályzata tartalmaz egy szabályt a SEP Mobile-hoz, amely a SEP Mobile kockázatfelmérésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét.

Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A SEP Mobile alkalmazás segítséget nyújt a letiltott eszközök felhasználóinak a probléma elhárításához és a vállalati erőforrásokhoz való hozzáférés visszaszerzéséhez.

Az Intune kétféleképpen integrálható a SEP Mobile-lal:

- Az **alapszintű beállítás** írásvédett mód, amely révén a SEP Mobile vizsgálhatja az Intune-beli eszközöket.

- A **teljes integráció** lehetővé teszi, hogy a SEP Mobile jelentse az eszközökkel kapcsolatos kockázatokat és a biztonsági incidensek részleteit az Intune-nak.

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Néhány gyakori helyzet:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján

Ha az eszközön kártékony alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbiak:

- Hozzáférés a vállalati e-mailekhez

- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással

- Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![Kártékony alkalmazások fogalmi képe](./media/skycure-mobile-threat-defense-connector/symantec-arch-1.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A kártékony alkalmazások észlelése után szervizelésre megadott hozzáférési rendszerkép](./media/skycure-mobile-threat-defense-connector/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![Wi-Fi-s hálózati elérés letiltása](./media/skycure-mobile-threat-defense-connector/symantec-arch-3.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított](./media/skycure-mobile-threat-defense-connector/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózaton a fenyegetéseket, például a **közbeékelődéses (man-in-the-middle)** támadást, és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![A SharePoint Online letiltása hálózati fenyegetések észlelése esetén](./media/skycure-mobile-threat-defense-connector/symantec-arch-5.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A fenyegetés kiküszöbölését követően a SharePoint-hozzáférés ismét biztosított – példa](./media/skycure-mobile-threat-defense-connector/symantec-arch-6.png)

## <a name="supported-platforms"></a>Támogatott platformok

- **Android 4.1 és újabb verziók**

- **iOS 8 és újabb verziók**

## <a name="pre-requisites"></a>Előfeltételek

- Prémium szintű Azure Active Directory

- Microsoft Intune-előfizetés

- Symantec Endpoint Protection Mobile-előfizetés

További tájékoztatást a [Symantec webhelyén](https://www.skycure.com/skycure-microsoft-integration/) talál.

## <a name="next-steps"></a>További lépések

Az Intune és a SEP Mobile integrálásához szükséges lépések:

- [A SEP Mobile és az Intune közötti integráció beállítása](skycure-mtd-connector-integration.md)

- [A SEP Mobile apps, a Microsoft Authenticator és az iOS/iPadOS alkalmazás-konfigurációs szabályzat hozzáadása és kiosztása](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [A SEP Mobile eszközmegfelelőségi szabályzatának létrehozása az Intune-ban](mtd-device-compliance-policy-create.md)

- [A SEP Mobile MTD-összekötő engedélyezése az Intune-ban](mtd-connector-enable.md)
