---
title: Android rendszerű nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz
titleSuffix: ''
description: Megtudhatja, hogyan adhat hozzá nagyvállalati rendszeralkalmazásokat Microsoft Intunehoz.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6cf1694c22e748fd10bb016607b7ff38963e80b5
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71304160"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Android rendszerű nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mielőtt az alkalmazást hozzárendelné egy eszközhöz vagy felhasználói csoporthoz, az eszközt először hozzá kell adnia a Microsoft Intune-hoz. A rendszeralkalmazások az Android Enterprise rendszerű eszközökön támogatottak. Az [androidos vállalati dedikált eszközökhöz](android-kiosk-enroll.md) vagy [teljes mértékben felügyelt eszközökhöz](android-fully-managed-enroll.md)is engedélyezheti a rendszeralkalmazást. 

## <a name="add-the-app"></a>Az alkalmazás hozzáadása

Az Intune-ban az alábbi módon adhat hozzá egy androidos nagyvállalati rendszeralkalmazást a Azure Portalhoz:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Az **Intune** panelen válassza az **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** elemet.
3. Az **alkalmazás hozzáadása** panelen, a rendelkezésre álló **egyéb** típusok területen válassza az **Android Enterprise System app**elemet.
4. Az alkalmazás adatainak konfigurálásához válassza a **Konfigurálás**lehetőséget, majd adja meg a következő adatokat:
    - **Alkalmazás neve**: Adja meg az alkalmazás nevét.
    - **Közzétevő**: Itt adhatja meg az alkalmazás kiadójának nevét.  
    - **Csomag neve**: Adja meg a csomag nevét. Az Intune ellenőrzi, hogy érvényes-e a csomag neve.
5. Kattintson az **OK** gombra.
6. Válassza a **Hozzáadás** lehetőséget.

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

Az Android Enterprise rendszerbeli alkalmazások lehetővé teszik a platform már részét képező alkalmazások engedélyezését vagy letiltását. Alkalmazás engedélyezéséhez rendelje hozzá a rendszeralkalmazást **szükség**szerint. Az alkalmazások letiltásához rendelje hozzá a rendszeralkalmazást **eltávolításként**. A rendszeralkalmazások nem rendelhetők hozzá elérhetőként a felhasználó számára.

## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
