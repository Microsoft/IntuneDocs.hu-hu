---
title: A Windows 10-es alkalmazásvédelmi szabályzatok konfigurálása
titleSuffix: Microsoft Intune
description: Ez a témakör a Windows 10-es eszközökhöz készült alkalmazás-védelmi szabályzatok (APP) konfigurálását ismerteti.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66cf454290903705d8500c2b1f9a07c9097351bf
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781756"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Felkészülés az alkalmazásvédelmi szabályzatok Windows 10 rendszereken történő konfigurálására 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Windows 10-es rendszerhez mobilalkalmazás-kezelést (MAM) úgy engedélyezhet, hogy beállítja a MAM-szolgáltatót az Azure AD-ban. A MAM-szolgáltató Azure AD-n belüli beállításával meghatározhatja a regisztráció állapotát, amikor az Intune-ban új Windows Information Protection- (WIP-) szabályzatot hoz létre. A regisztráció állapota lehet MAM vagy mobileszköz-kezelés (MDM).

## <a name="to-configure-the-mam-provider"></a>MAM-szolgáltató konfigurálása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza a **minden szolgáltatás** lehetőséget, és válassza az **M365 Azure Active Directory** lehetőséget az irányítópultok váltásához.
3. Válassza a **Azure Active Directory**lehetőséget.
4. A **Kezelés** csoportban válassza a **Mobilitás (MDM és MAM)** elemet.
5. Kattintson a **Microsoft Intune** elemre.
6. Konfigurálja a beállításokat az **alapértelmezett MAM URL-címek visszaállítása** csoportban a **Konfigurálás** ablaktáblán.

   **MAM-felhasználói hatókör**  
   Az automatikus MAM-regisztrációval a felhasználók Windows-eszközein található vállalati adatok kezelhetők. Az automatikus MAM-regisztráció a saját eszközök használatának esetén lesz konfigurálva.<ul><li>**Egyik sem**<br>Ezt akkor válassza, ha egy felhasználó sem regisztrálható a MAM-ban.</li><li>**Néhány**<br>Kiválaszthatja azokat az Azure AD-csoportokat, amelyekbe a MAM-ban regisztrálandó felhasználók tartoznak.</li><li>**Összes**<br>Ezt akkor válassza, ha minden felhasználó regisztrálható a MAM-ban.</li></ul>

   **A MAM használati feltételeinek URL-címe**  
   A MAM használati feltételei URL-címének használata a Microsoft Intune-ban nem támogatott. A beviteli mezőt a védelmi szabályzatok alkalmazásához üresen kell hagyni.

   **MDM-felderítési URL-cím**  
   A MAM-szolgáltatás regisztrálásra mutató URL-címe. A regisztrálási cím az eszközök MAM-szolgáltatásban történő regisztrálásához használatos.

   **A MAM megfelelőségi URL-címe**  
   A MAM megfelelőségi URL-címének használata a Microsoft Intune-ban nem támogatott. A beviteli mezőt a védelmi szabályzatok alkalmazásához üresen kell hagyni. 

7. Kattintson a **Mentés**gombra.

## <a name="next-steps"></a>További lépések

[Alkalmazásvédelmi WIP-szabályzatok létrehozása](windows-information-protection-policy-create.md)
