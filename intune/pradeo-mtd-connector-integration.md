---
title: A Pradeo Intune-integrációjának beállítása
titleSuffix: Intune on Azure
description: A Pradeo-összekötő integrálása az Intune-nal
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b76549ad4be80d510638e3f79111d700a80f73ca
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838529"
---
# <a name="integrate-pradeo-with-intune"></a>A Pradeo integrálása az Intune-nal

A Pradeo Mobile Threat Defense megoldás Intune-beli integrálásához kövesse az alábbi lépéseket.

## <a name="before-you-begin"></a>Előkészületek

> [!NOTE]
> Az alábbi lépéseket a [Pradeo biztonsági konzolon](https://www.apps-security.com) kell végrehajtania.

Mielőtt elkezdené a Pradeo integrálását az Intune-nal, ellenőrizze, hogy rendelkezik-e az alábbiakkal:

-   Microsoft Intune-előfizetés

-   Azure Active Directory rendszergazdai hitelesítő adatok a következő engedélyek megadására:

    -   Bejelentkezés és felhasználói profil olvasása

    -   A címtár elérése a bejelentkezett felhasználó nevében

    -   Címtáradatok olvasása

    -   Eszközadatok küldése az Intune-ba

-   Rendszergazdai hitelesítő adatok a Pradeo bztonsági konzol eléréséhez.

### <a name="pradeo-app-authorization"></a>A Pradeo alkalmazás engedélyezése

A Pradeo alkalmazás engedélyezési folyamata a következő:

-   Engedélyezze a Pradeo szolgáltatásnak, hogy az eszközállapottal kapcsolatos információt küldhessen az Intune-ba.

-   A Pradeo szinkronizálást végez az Azure AD regisztrációs csoporttagsággal az eszköz adatbázisának feltöltéséhez.

-   Engedélyezze a Pradeo felügyeleti konzolja számára az Azure AD-alapú egyszeri bejelentkezést (SSO-t).

-   Engedélyezze a Pradeo alkalmazás számára az Azure AD SSO használatát a bejelentkezéshez.

## <a name="to-set-up-pradeo-integration"></a>A Pradeo-integráció beállítása

1.  Nyissa meg a [Pradeo biztonsági konzolt](https://www.apps-security.com), és jelentkezzen be a hitelesítő adataival.

2.  Válassza az **Administration - Enterprise Mobility Management** (Felügyelet – Nagyvállalati mobileszköz-felügyelet) lehetőséget a menüben.

3.  Kattintson az **Intune emblémára**.

4.  Az **EMM (Enterprise mobility management - Intune** ablak **1. lépésében** kattintson a **Pradeo-összekötő** gombra. 

    ![Az Intune-ban EMM Pradeo ablak képernyőképe](./media/pradeo_setup.png)

5. A Microsoft Intune kapcsolati ablakában adja meg az Intune-hoz használt hitelesítő adatait.

5.  Ekkor megnyílik a Pradeo weboldala. A **2. lépésben** kattintson a **Pradeo Device Health** (Pradeo-eszközállapot) gombra.

7. A Pradeo–Intune-összekötő ablakban válassza az **Elfogadás** lehetőséget. 

8. A Pradeo eszköz-API összekötőjének ablakában válassza az **Elfogadás** lehetőséget.

9. Ekkor megnyílik a Pradeo weboldala. A **3. lépésben** kattintson a **Csatlakozás a Microsofthoz** gombra. 

10. A Microsoft Intune hitelesítő ablakában adja meg az Intune-hoz használt hitelesítő adatait.

11. A **sikeres integrációt** jelző ablak megjelenésekor az integráció befejeződött.

## <a name="next-steps"></a>További lépések

-   [Pradeo-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)
