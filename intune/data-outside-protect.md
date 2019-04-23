---
title: A céges adatokhoz való illetéktelen hozzáférés megakadályozása
titleSuffix: Microsoft Intune
description: A vállalat hálózatán kívül megosztott vállalati adatokhoz való illetéktelen hozzáférés megakadályozása a Microsoft Intune-nal.
keywords: Office 365 O365 Azure Information Protection hálózaton kívüli adatok védelme céges adatok
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6a88573a-aa60-455c-858c-74562798246b
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0882fb19d3ce74c837b83973ec07f391bc2875fa
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61506406"
---
# <a name="prevent-unauthorized-access-to-company-data-using-microsoft-intune"></a>A céges adatokhoz való illetéktelen hozzáférés megakadályozása a Microsoft Intune-nal

Az Office 365 dokumentumait és e-mailjeit besorolással és címkézéssel védheti, így csak a jogosultsággal rendelkező felhasználók férhetnek hozzá az adatokhoz. Miután a rendszergazda vagy a felhasználók létrehozták a szabályokat és feltételeket, a beállítások kezelése automatikusan történik. A rendszergazdák emellett ajánlott beállításokat is megadhatnak a felhasználók számára. A rendszergazdák és a felhasználók azt követően is visszavonhatják a hozzáférési engedélyeket, miután az adatokat megosztották másokkal, és ehhez nincs szükség szolgáltatói segítségre. Ennek eredményeképp még akkor is szabályozható, hogy ki nyithat meg vagy módosíthat adatokat, amikor az adatok már a céges hálózaton kívülre kerültek. 

## <a name="before-you-begin"></a>Előkészületek

A lentebb ismertetett cselekvési terv az alábbi feltételek teljesülése esetén használható:
* A vállalat készen áll a felhőre való biztonságos áttérésre.
* A vállalat Office 365 Exchange Online-t, SharePoint Online-t, OneDrive vállalati verziót vagy Yammert használ.
* A vállalat rendelkezik licenccel a Microsoft 365, az Enterprise Mobility + Security (EMS) vagy az Azure Information Protection egyikéhez.
* A vállalat Windows 7 1. szervizcsomag vagy újabb verziót futtató eszközöket használ.
* A vállalat Office 365 ProPlus 2016-os vagy 2013-as alkalmazásokat, Office Professional Plus 2016, az Office Professional Plus 2013 a Service Pack 1 csomaggal, vagy az Office Professional Plus 2010 alkalmazásokat használ.

## <a name="action-plan"></a>Műveletterv

Tanulmányozza az [Azure Information Protection – gyors üzembe helyezési útmutatót](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial).  

## <a name="what-to-tell-employees-and-students"></a>Miről kell tájékoztatni az alkalmazottakat és a tanulókat?

Tudassa velük, hogy [mikor és hogyan kell védelemmel ellátni a bizalmas információkat tartalmazó dokumentumokat és e-maileket](https://docs.microsoft.com/information-protection/deploy-use/help-users).

## <a name="next-steps"></a>További lépések

A következő lépések részeként további információhoz juthat azokról az egyéb módszerekről, melyekkel növelhető a céges adatok védelme, beleértve a következőket: 

* Ismerje meg, hogyan használható [Azure Information Protection iOS és Android rendszerű eszközökön](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).
* Windows Phone-telefonok és Mac-gépek esetén ismerkedjen meg a [Microsoft Rights Management Sharing alkalmazással](https://technet.microsoft.com/dn451248).
