---
title: A JAMF Pro által küldött adatokat az Intune-nak küldi
titleSuffix: Microsoft Intune
description: Tekintse át azokat az adatokat, amelyeket a JAMF Pro küld Microsoft Intunenek, amikor a JAMF Pro-t integrálja a Mac-et az Intune-nal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4bf6df44335f3375d58d3c2c11da7cb3f982b3e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502416"
---
# <a name="data-jamf-pro-sends-to-intune"></a>A Jamf Pro által az Intune-ba küldött adatok

Ha a [JAMF Pro](https://www.jamf.com) használatával felügyeli a végfelhasználók Mac számítógépét az Intune-nal, a JAMF Pro rögzíti a felügyelt MacOS-eszközök leltározási adatait. 

## <a name="data"></a>Adat  
Az Intune-nal JAMF Pro-megosztással rendelkező adatok listájáért lásd a függelék: a JAMF Pro technikai dokumentációjában [Microsoft Intune megosztott leltári információk](https://docs.jamf.com/technical-papers/jamf-pro/microsoft-intune/10.9.0/Appendix__Inventory_Information_Shared_with_Microsoft_Intune.html) című szakaszt. 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>További lépések
A [JAMF által felügyelt eszközök JAMF Pro docs-beli eltávolításával](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)kapcsolatos információk. További segítségért a támogatási jegyet is [JAMF-támogatással](https://www.jamf.com/support/) teheti meg. 

