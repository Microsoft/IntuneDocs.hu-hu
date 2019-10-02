---
title: A Sophos Mobile-integráció beállítása az Intune-nal
titleSuffix: Intune on Azure
description: A Sophos Mobile megoldás beállítása a Microsoft Intune használatával a mobileszköz-hozzáférés szabályozásához a vállalati erőforrásokhoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec60a618280caf6a5b7ef242c192cc64b5d839de
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731883"
---
# <a name="integrate-sophos-mobile-with-intune"></a>A Sophos Mobile integrálása az Intune-nal  

A Sophos Mobile Threat Defense megoldás az Intune-nal való integrálásához hajtsa végre az alábbi lépéseket.  

## <a name="before-you-begin"></a>Előkészületek  

A Sophos Mobile és az Intune integrálási folyamatának megkezdése előtt győződjön meg arról, hogy rendelkezik a következőkkel:  
- Microsoft Intune-előfizetés  
- Azure Active Directory rendszergazdai hitelesítő adatok a következő engedélyek megadására:  
  - Bejelentkezés és felhasználói profil olvasása  
  - A címtár elérése a bejelentkezett felhasználó nevében  
  - Címtáradatok olvasása  
  - Eszközadatok küldése az Intune-ba  
- Rendszergazdai hitelesítő adatok a Sophos Mobile felügyeleti konzol eléréséhez.  


### <a name="sophos-mobile-app-authorization"></a>A Sophos Mobile App engedélyezése  
  
A Sophos Mobile App engedélyezési folyamata a következő:  
- Annak engedélyezése, hogy a Sophos Mobile szolgáltatás az eszköz állapotával kapcsolatos adatokat az Intune-nal továbbítsa.  
- A Sophos Mobile syncs az Azure AD regisztrációs csoporttagság használatával tölti fel az eszköz adatbázisát.  
- Az Azure AD egyszeri bejelentkezés (SSO) használatának engedélyezése a Sophos Mobile felügyeleti konzoljának.  
- Az Azure AD SSO használatával való bejelentkezés engedélyezése a Sophos Mobile alkalmazásnak.  


## <a name="to-set-up-sophos-mobile-integration"></a>A Sophos Mobile Integration beállítása  

1. Jelentkezzen be a [Azure Portalba]( https://portal.azure.com/), nyissa meg az **Intune** > **eszköz megfelelőség**@no__t – 4**Mobile Threat Defense** >, és válassza a **Hozzáadás**lehetőséget.  
2. Az **összekötő hozzáadása** lapon használja a legördülő menüt, és válassza a **Sophos**lehetőséget. Majd válassza a **Létrehozás**lehetőséget.  
3. Kattintson a hivatkozásra a *Sophos felügyeleti konzol megnyitásához*.  
4. Jelentkezzen be a [Sophos felügyeleti konzolra](https://central.sophos.com/) a Sophos hitelesítő adataival.  
5. Nyissa meg a **Mobile** > **Beállítások** > **Setup** > **Sophos telepítőjét**.  
6. A **Sophos telepítője** lapon válassza az **Intune MTD** lapot.  
   ![Sophos Setup @ no__t-1 
 
7. Válassza a **kötés**lehetőséget, majd válassza az **Igen**lehetőséget. A Sophos csatlakozik az Intune-hoz, és bejelentkezik az Intune-előfizetésbe. 
8. A Microsoft Intune hitelesítés ablakban adja meg az Intune hitelesítő adatait, és **fogadja el** a *Sophos Mobile Thread Defense*engedélyezési kérelmét.  
   @no__t 0Intune-hitelesítés @ no__t-1

9. A **Sophos beállítása** lapon válassza a **Mentés** lehetőséget az Intune konfigurációjának befejezéséhez:  
   ![Save Sophos Setup @ no__t-1  

1. A **sikeres integrációt** jelző ablak megjelenésekor az integráció befejeződött.  
1. Az Intune-konzolon a Sophos már elérhető.  


## <a name="next-steps"></a>További lépések  
[A Sophos-ügyfélalkalmazások konfigurálása](mtd-apps-ios-app-configuration-policy-add-assign.md)
