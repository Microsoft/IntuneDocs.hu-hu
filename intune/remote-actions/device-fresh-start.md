---
title: Windows 10 rendszerű eszközök visszaállítása a Microsoft Intune-nal – Azure | Microsoft Docs
description: A Microsoft Intune Újrakezdés funkciójával eltávolíthat alkalmazásokat Windows 10 rendszerű számítógépekről.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01ecfda5b173b2fc9dcef893789614bfbcc7c90b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732519"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Intune-t futtató Windows 10 rendszerű eszközök alaphelyzetbe állítása az Újrakezdéssel


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az **Újratelepítés** eszközművelet eltávolít minden alkalmazást, amely telepítve van egy Windows 10 rendszerű (1703-as vagy újabb verzió) számítógépen. Ezzel a művelettel eltávolíthatja az olyan előre telepített (OEM) alkalmazásokat, amelyek általában telepítve vannak egy új számítógépen. 

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com), majd lépjen a **Microsoft Intune** > **Eszközök** > **Minden eszköz** elemre.
2. A felügyelt eszközök listájából válasszon ki egy Windows 10-es asztali eszközt.
3. Kattintson az **Újratelepítés** lehetőségre. 
4. **Az eszközön található felhasználói adatok megőrzése** beállításnál válassza ki a következőket:
   * Az eszköz Azure AD-csatlakozásának megtartása
   * Ha egy Azure Active Directory engedélyező felhasználó bejelentkezik az eszközre, a rendszer ismét regisztrálja az eszközt a mobileszköz-felügyeletbe.
   * Az eszköz felhasználójához tartozó kezdőmappa tartalmának megtartása, az alkalmazások és beállítások eltávolítása

  > [!IMPORTANT]
 > Ha nem őrzi meg a felhasználói adatmennyiséget, az eszköz visszaáll az alapértelmezett OOBE (beépített élmény) állapotba, és megtartja a beépített rendszergazdai fiókot.
 > A BYOD-eszközök regisztrálása az Azure AD-ben és a mobileszköz-kezelésben történik.
 > Az Azure AD-hez csatlakoztatott eszközök újra regisztrálva lesznek a mobileszköz-felügyeletben, amikor egy Azure Active Directory engedélyező felhasználó bejelentkezik az eszközre.
 
5. Kattintson az **OK** gombra.   
6. A művelet állapotának megtekintéséhez lépjen vissza az **Eszközök** szintjére, majd kattintson az **Eszközműveletek** elemre.  
7. Az eszköz vissza lesz állítva a kezdeti bejelentkezési képernyőre.
