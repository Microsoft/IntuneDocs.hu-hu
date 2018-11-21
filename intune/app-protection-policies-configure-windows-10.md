---
title: Felkészülés az alkalmazásvédelmi szabályzatok Windows 10 rendszereken történő konfigurálására
titleSuffix: Microsoft Intune
description: Mobilalkalmazás-kezelési (MAM) szolgáltató beállítása az Azure AD-ban.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5953038f3627f98f0e034aeba4c2c92ea3dca2d6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184386"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Felkészülés az alkalmazásvédelmi szabályzatok Windows 10 rendszereken történő konfigurálására 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10-es rendszerhez mobilalkalmazás-kezelést (MAM) úgy engedélyezhet, hogy beállítja a MAM-szolgáltatót az Azure AD-ban. A MAM-szolgáltató Azure AD-n belüli beállításával meghatározhatja a regisztráció állapotát, amikor az Intune-ban új Windows Information Protection- (WIP-) szabályzatot hoz létre. A regisztráció állapota lehet MAM vagy mobileszköz-kezelés (MDM).

## <a name="to-configure-the-mam-provider"></a>MAM-szolgáltató konfigurálása

1. Jelentkezzen be az Azure Portalon, majd válassza az **Azure Active Directory** elemet.

2. A **Kezelés** csoportban válassza a **Mobilitás (MDM és MAM)** elemet.

3. Kattintson a **Microsoft Intune** elemre.

4. A **Konfigurálás** panel **Alapértelmezett MAM URL-címek** csoportjában végezze el a konfigurációs beállításokat.

   **MAM-felhasználói hatókör**  
   Az automatikus MAM-regisztrációval a felhasználók Windows-eszközein található vállalati adatok kezelhetők. Az automatikus MAM-regisztráció a saját eszközök használatának esetén lesz konfigurálva.<ul><li>**Nincsenek**<br>Ezt akkor válassza, ha egy felhasználó sem regisztrálható a MAM-ban.</li><li>**Néhány**<br>Kiválaszthatja azokat az Azure AD-csoportokat, amelyekbe a MAM-ban regisztrálandó felhasználók tartoznak.</li><li>**Összes**<br>Ezt akkor válassza, ha minden felhasználó regisztrálható a MAM-ban.</li></ul>

   **A MAM használati feltételeinek URL-címe**  
   A MAM használati feltételei URL-címének használata a Microsoft Intune-ban nem támogatott. A beviteli mezőt a védelmi szabályzatok alkalmazásához üresen kell hagyni.

   **MDM-felderítési URL-cím**  
   A MAM-szolgáltatás regisztrálásra mutató URL-címe. A regisztrálási cím az eszközök MAM-szolgáltatásban történő regisztrálásához használatos.

   **A MAM megfelelőségi URL-címe**  
   A MAM megfelelőségi URL-címének használata a Microsoft Intune-ban nem támogatott. A beviteli mezőt a védelmi szabályzatok alkalmazásához üresen kell hagyni. 

5.  Kattintson a **Mentés**gombra.

## <a name="next-steps"></a>További lépések

[Alkalmazásvédelmi WIP-szabályzatok létrehozása](windows-information-protection-policy-create.md)
