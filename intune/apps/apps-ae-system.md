---
title: Android rendszerű nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz
titleSuffix: ''
description: Megtudhatja, hogyan adhat hozzá nagyvállalati rendszeralkalmazásokat Microsoft Intunehoz.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: d45455a97f8016527dce49839b5493f16b173d43
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563658"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Android rendszerű nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz

Mielőtt az alkalmazást hozzárendelné egy eszközhöz vagy felhasználói csoporthoz, az eszközt először hozzá kell adnia a Microsoft Intune-hoz. A rendszeralkalmazások az Android Enterprise rendszerű eszközökön támogatottak. Az [androidos vállalati dedikált eszközökhöz](../enrollment/android-kiosk-enroll.md) vagy [teljes mértékben felügyelt eszközökhöz](../enrollment/android-fully-managed-enroll.md)is engedélyezheti a rendszeralkalmazást.

## <a name="add-the-app"></a>Az alkalmazás hozzáadása

Az Intune-ban az alábbi módon adhat hozzá egy androidos nagyvállalati rendszeralkalmazást a Azure Portalhoz:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás hozzáadása** panelen, a rendelkezésre álló **egyéb** típusok területen válassza az **Android Enterprise System app**elemet.
4. Az alkalmazás adatainak konfigurálásához válassza a **Konfigurálás**lehetőséget, majd adja meg a következő adatokat:
    - **Alkalmazás neve**: adja meg az alkalmazás nevét.
    - **Kiadó:** Adja meg az alkalmazás kiadójának nevét.  
    - **Csomag neve**: adja meg a csomag nevét. Az Intune ellenőrzi, hogy érvényes-e a csomag neve.
5. Válassza az **OK** gombot.
6. Válassza a **Hozzáadás** elemet.

> [!NOTE]
> Az eszköz SZÁMÍTÓGÉPGYÁRTÓjának kell működnie, hogy megkeresse az engedélyezni vagy letiltani kívánt alkalmazás csomagjának nevét.

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

Az Android Enterprise rendszerbeli alkalmazások lehetővé teszik a platform már részét képező alkalmazások engedélyezését vagy letiltását. Alkalmazás engedélyezéséhez rendelje hozzá a rendszeralkalmazást **szükség**szerint. Az alkalmazások letiltásához rendelje hozzá a rendszeralkalmazást **eltávolításként**. A rendszeralkalmazások nem rendelhetők hozzá elérhetőként a felhasználó számára.


## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
