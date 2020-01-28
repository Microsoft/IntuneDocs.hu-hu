---
title: Android rendszerű nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz
titleSuffix: ''
description: Megtudhatja, hogyan adhat hozzá nagyvállalati rendszeralkalmazásokat Microsoft Intunehoz.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755255"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Android rendszerű nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz

Mielőtt az alkalmazást hozzárendelné egy eszközhöz vagy felhasználói csoporthoz, az eszközt először hozzá kell adnia a Microsoft Intune-hoz. A rendszeralkalmazások az Android Enterprise rendszerű eszközökön támogatottak. Az [androidos vállalati dedikált eszközökhöz](../enrollment/android-kiosk-enroll.md) vagy [teljes mértékben felügyelt eszközökhöz](../enrollment/android-fully-managed-enroll.md)is engedélyezheti a rendszeralkalmazást.

## <a name="add-the-app"></a>Az alkalmazás hozzáadása

Az Intune-ban az alábbi módon adhat hozzá egy androidos nagyvállalati rendszeralkalmazást a Azure Portalhoz:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán az elérhető **egyéb** típusok területen válassza az **Android Enterprise System app**elemet.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **alkalmazás hozzáadása** lépések.
Az **alkalmazás adatai** lapon adja meg az alkalmazás részleteit:
    - **Alkalmazás neve**: adja meg az alkalmazás nevét.
    - **Kiadó:** Adja meg az alkalmazás kiadójának nevét.  
    - **Csomag neve**: adja meg a csomag nevét. Az Intune ellenőrzi, hogy érvényes-e a csomag neve.
5. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.
8. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye a hatókör címkéit az alkalmazáshoz. További információ: [a szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez](~/fundamentals/scope-tags.md).
9. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.
10. Válassza ki az alkalmazás csoportjának hozzárendeléseit. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md). 
11. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat.
12. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

Megjelenik a létrehozott alkalmazás **Áttekintés** panelje.

> [!NOTE]
> Az eszköz SZÁMÍTÓGÉPGYÁRTÓjának kell működnie, hogy megkeresse az engedélyezni vagy letiltani kívánt alkalmazás csomagjának nevét.

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

Az Android Enterprise rendszerbeli alkalmazások lehetővé teszik a platform már részét képező alkalmazások engedélyezését vagy letiltását. Alkalmazás engedélyezéséhez rendelje hozzá a rendszeralkalmazást **szükség**szerint. Az alkalmazások letiltásához rendelje hozzá a rendszeralkalmazást **eltávolításként**. A rendszeralkalmazások nem rendelhetők hozzá elérhetőként a felhasználó számára.


## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
