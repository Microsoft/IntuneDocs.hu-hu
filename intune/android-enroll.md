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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dcde377dbf3e97e94957ab5c984aa6dfede9136
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71303921"
---
# <a name="enroll-android-devices"></a>Androidos eszközök regisztrálása

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune-rendszergazdaként a következő módokon regisztrálhat Android-eszközöket:
- Android Enterprise (olyan regisztrációs beállításokat kínál, amelyek a legnaprakészebb és biztonságos funkciókat biztosítanak a felhasználóknak):
    - [**Androidos vállalati munkahelyi profil**](android-work-profile-enroll.md): A személyes eszközök számára engedélyezték a vállalati adatelérést. A rendszergazdák kezelhetik a munkahelyi fiókokat, az alkalmazásokat és az adatmennyiséget. Az eszközön tárolt személyes adatok külön maradnak a munkahelyi adatoktól, és a rendszergazdák nem szabályozzák a személyes beállításokat vagy az adatok adatait. 
    - [**Android Enterprise dedikált**](android-kiosk-enroll.md): A vállalat által birtokolt, egyszer használatos eszközök, például a digitális aláírások, a jegyek nyomtatása vagy a leltár kezelése. A rendszergazdák alkalmazások és webes hivatkozások egy adott körére korlátozzák az eszköz használatát. Ez azt is megakadályozza, hogy a felhasználók más alkalmazásokat adjanak az eszközhöz, vagy más műveleteket hajtsanak végre rajta.
    - [**Teljes körűen felügyelt Android Enterprise**](android-fully-managed-enroll.md): A kizárólag munkahelyi és nem személyes használatra szánt, vállalati tulajdonú, egyetlen felhasználói eszközök esetében. A rendszergazdák kezelhetik a teljes eszközt, és a házirend-vezérlők nem érhetők el a munkahelyi profilokhoz. 
- [**Android-eszköz rendszergazdája**](android-enroll-device-administrator.md), beleértve a Samsung Knox standard-eszközöket és a [Zebra-eszközöket](android-zebra-mx-overview.md). 

## <a name="prerequisites"></a>Előfeltételek

A mobileszközök kezelésének előkészítéseként a **Microsoft Intune**-t kell beállítani mobileszköz-kezelő (MDM) szolgáltatóként. Erről [Az MDM-szolgáltató beállítása](mdm-authority-set.md) című cikk nyújt útmutatást. Ezt a beállítást csak egyszer, az Intune-nak a mobileszközök kezelésére való kezdeti beállítása során kell megadni.

A zebra Technologies által gyártott eszközök esetében előfordulhat, hogy az adott eszköz képességeitől függően további engedélyeket kell megadnia a Céges portál. [A zebra-eszközök mobilitási bővítményei](android-zebra-mx-overview.md) további részleteket tartalmaznak.

A Samsung Knox standard-eszközökhöz [további előfeltételek](android-samsung-knox-mobile-enroll.md)tartoznak.

## <a name="next-steps"></a>További lépések

- [Androidos vállalati munkahelyi profil regisztrálásának beállítása](android-work-profile-enroll.md)
- [Androidos vállalati dedikált eszközök regisztrálásának beállítása](android-kiosk-enroll.md)
- [Androidos vállalati teljes körűen felügyelt regisztrációk beállítása](android-fully-managed-enroll.md)
- [Androidos eszközök rendszergazdai regisztrációjának beállítása](android-enroll-device-administrator.md)

