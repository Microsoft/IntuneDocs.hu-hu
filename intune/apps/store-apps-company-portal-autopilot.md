---
title: A Windows 10 Céges portál alkalmazás hozzáadása és kiosztása az Autopilot-kiépített eszközökhöz
titleSuffix: Microsoft Intune
description: Adja hozzá és rendelje hozzá a Windows 10 Céges portál alkalmazást az Intune-hoz az Autopilot kiépített eszközeihez.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579768"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>A Windows 10 Céges portál alkalmazás hozzáadása és kiosztása az Autopilot-kiépített eszközökhöz

Az eszközök kezeléséhez és az alkalmazások telepítéséhez a felhasználók használhatják a Céges portál alkalmazást. A Windows 10-es Céges portál alkalmazást közvetlenül az Intune-ból is hozzárendelheti. 

## <a name="prerequisites"></a>Előfeltételek

A Windows 10 Autopilot-beli kiépített eszközök esetében javasoljuk, hogy az Intune-nal társítsa a Microsoft Store vállalati fiókhoz. További információ: a [mennyiségi programban vásárolt alkalmazások felügyelete a Microsoft Store for Business és a Microsoft Intune használatával](~/apps/windows-store-for-business.md).

Az alábbi lépésekkel a Céges portál (offline) telepítésére van kiválasztva. A Céges portál alkalmazás az Autopilot-csoporthoz való hozzárendeléskor lesz telepítve az eszköz környezetében, és a felhasználó bejelentkezése előtt telepíteni kell az eszközre. 

## <a name="configure-settings-to-show-offline-apps"></a>A beállítások konfigurálása offline alkalmazások megjelenítéséhez
1. Jelentkezzen be a [Microsoft Store Vállalatoknak](https://www.microsoft.com/business-store) szolgáltatásba a rendszergazdai fiókjával.
2. Válassza a **Felügyelet** lapot az ablak tetején.
3. A bal oldali ablaktáblán válassza a **Beállítások** elemet.
4. A **Vásárlási élmény** terület **Offline alkalmazások megjelenítése** beállítását állítsa **Bekapcsolva** értékre.  
    Megjelennek az offline licencelt alkalmazások.

## <a name="get-the-offline-company-portal-app"></a>Offline Céges portál alkalmazás beolvasása
1. Keresse meg és válassza ki a **Céges portál** alkalmazást.
2. Állítsa a **licenc típusát****offline-ra**.
3. Válassza **Az alkalmazás letöltése** lehetőséget az offline Céges portál letöltéséhez és a leltárba való felvételéhez.

## <a name="assign-the-company-portal-app"></a>A Céges portál alkalmazás kiosztása
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) a rendszergazdai fiókjával. 
2. Válassza az **alkalmazások** fület a jobb oldali ablaktáblán. 
3. A **platform**alatt válassza a **Windows**lehetőséget. 
4. Válassza a **céges portál (offline)** lehetőséget.   
5. Várjon, amíg a szinkronizálási ütemterv befejeződik, vagy hajtson végre manuális szinkronizálást a Microsoft Endpoint Manager felügyeleti központjából.
6. Rendelje hozzá a Céges portál alkalmazást kötelező alkalmazásként a kiválasztott Autopilot-eszközök csoportjaihoz.

## <a name="next-steps"></a>További lépések

- Az alkalmazások hozzárendelésével kapcsolatos további tudnivalókért tekintse meg az [alkalmazások csoportok számára való hozzárendelését](apps-deploy.md)ismertető témakört.

