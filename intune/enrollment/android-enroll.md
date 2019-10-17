---
title: Androidos eszközök regisztrálása az Intune-ban
titleSuffix: Microsoft Intune
description: Útmutató az Android-eszközök Intune-ban való regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff005ddded4178801e7e334f604280ef4408aaff
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505661"
---
# <a name="enroll-android-devices"></a>Androidos eszközök regisztrálása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune-rendszergazdaként a következő módokon regisztrálhat Android-eszközöket:
- Android Enterprise (olyan regisztrációs beállításokat kínál, amelyek a legnaprakészebb és biztonságos funkciókat biztosítanak a felhasználóknak):
    - [**Androidos vállalati munkahelyi profil**](android-work-profile-enroll.md): a személyes eszközök számára engedélyezték a vállalati adatelérést. A rendszergazdák kezelhetik a munkahelyi fiókokat, az alkalmazásokat és az adatmennyiséget. Az eszközön tárolt személyes adatok külön maradnak a munkahelyi adatoktól, és a rendszergazdák nem szabályozzák a személyes beállításokat vagy az adatok adatait. 
    - [**Android Enterprise dedikált**](android-kiosk-enroll.md): vállalati tulajdonú, egyfelhasználós eszközök, például digitális aláírások, jegyek nyomtatása vagy leltár-kezelés. A rendszergazdák alkalmazások és webes hivatkozások egy adott körére korlátozzák az eszköz használatát. Ez azt is megakadályozza, hogy a felhasználók más alkalmazásokat adjanak az eszközhöz, vagy más műveleteket hajtsanak végre rajta.
    - [**Teljes körűen felügyelt Android Enterprise**](android-fully-managed-enroll.md): vállalati tulajdonú, egyetlen felhasználói eszköz, amely kizárólag munkahelyi és nem személyes használatra szolgál. A rendszergazdák kezelhetik a teljes eszközt, és a házirend-vezérlők nem érhetők el a munkahelyi profilokhoz. 
- [**Android-eszköz rendszergazdája**](android-enroll-device-administrator.md), beleértve a Samsung Knox standard-eszközöket és a [Zebra-eszközöket](../configuration/android-zebra-mx-overview.md). 

## <a name="prerequisites"></a>Előfeltételek

A mobileszközök kezelésének előkészítéseként a **Microsoft Intune**-t kell beállítani mobileszköz-kezelő (MDM) szolgáltatóként. Erről [Az MDM-szolgáltató beállítása](../fundamentals/mdm-authority-set.md) című cikk nyújt útmutatást. Ezt a beállítást csak egyszer, az Intune-nak a mobileszközök kezelésére való kezdeti beállítása során kell megadni.

A zebra Technologies által gyártott eszközök esetében előfordulhat, hogy az adott eszköz képességeitől függően további engedélyeket kell megadnia a Céges portál. [A zebra-eszközök mobilitási bővítményei](../configuration/android-zebra-mx-overview.md) további részleteket tartalmaznak.

A Samsung Knox standard-eszközökhöz [további előfeltételek](android-samsung-knox-mobile-enroll.md)tartoznak.

## <a name="next-steps"></a>További lépések

- [Androidos vállalati munkahelyi profil regisztrálásának beállítása](android-work-profile-enroll.md)
- [Androidos vállalati dedikált eszközök regisztrálásának beállítása](android-kiosk-enroll.md)
- [Androidos vállalati teljes körűen felügyelt regisztrációk beállítása](android-fully-managed-enroll.md)
- [Androidos eszközök rendszergazdai regisztrációjának beállítása](android-enroll-device-administrator.md)

