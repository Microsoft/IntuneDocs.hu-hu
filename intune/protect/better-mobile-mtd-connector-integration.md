---
title: A Better Mobile és az Intune integrációjának beállítása
titleSuffix: Intune on Azure
description: A Better Mobile-összekötő és az Intune integrálása
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0528ec962165f358b35afce98f58c8b9b4efe93c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810326"
---
# <a name="integrate-better-mobile-with-intune"></a>A Better Mobile és az Intune integrálása

A Better Mobile Threat Defense megoldás és az Intune integrálásához kövesse az alábbi lépéseket.

## <a name="before-you-begin"></a>Előkészületek

A következő lépéseket a [jobb Mobile felügyeleti konzolon](https://aad.bmobi.net) kell végrehajtani, és lehetővé válik a jobb mobil szolgáltatáshoz való kapcsolódás az Intune-ban regisztrált eszközökön (az eszközök megfelelőségének használata) és a nem regisztrált eszközökön (az alkalmazás-védelmi házirendek használatával).

Mielőtt elkezdené a Better Mobile és az Intune integrálását, ellenőrizze, hogy rendelkezik-e az alábbiakkal:

- Microsoft Intune-előfizetés

- Azure Active Directory rendszergazdai hitelesítő adatok a következő engedélyek megadására:

  - Bejelentkezés és felhasználói profil olvasása

  - A címtár elérése a bejelentkezett felhasználó nevében

  - Címtáradatok olvasása

  - Eszközadatok küldése az Intune-ba

- Rendszergazdai azonosító adatok a Better Mobile rendszergazdai konzoljának hozzáféréséhez

### <a name="better-mobile-app-authorization"></a>A Better Mobile alkalmazás hitelesítése

A Better Mobile alkalmazás hitelesítésének folyamata a következő:

- Engedélyezze a Better Mobile szolgáltatásnak, hogy az eszközállapottal kapcsolatos információt küldhessen az Intune-ba.

- A Better Mobile szinkronizálja magát az Azure AD regisztrációs csoport tagjaival az eszköz adatbázisának adatokkal való feltöltéséhez.

- Engedélyezze a Better Mobile rendszergazdai konzoljának az Azure AD egyszeri bejelentkezés (Single Sign On, SSO) használatát.

- Engedélyezze a Better Mobile alkalmazásnak az Azure AD SSO-val való bejelentkezést.

## <a name="to-set-up-better-mobile-integration"></a>A Better Mobile-integráció beállítása

1. Lépjen a [Better Mobile rendszergazdai konzoljához](https://aad.bmobi.net), és jelentkezzen be a hitelesítő adataival.
2. Válassza az **Integration** > **EMM/MDM** > **ADD ACCOUNT** (Integráció, EMM/MDM, FIÓK HOZZÁADÁSA) lehetőséget.

     ![A jobb Mobile felügyeleti konzol képe](./media/better-mobile-mtd-connector-integration/better_mobile_console.png)
 
3. Válassza az **Intune** lehetőséget.
4. Az **ACCOUNT NAME** (FIÓKNÉV) elemnél adjon meg egy leírót. 
5. A **Microsoft bejelentkezési** ablakában adja meg az Intune-ban használt hitelesítő adatokat.
6. A **Permissions requested** (Kért engedélyek) ablakban válassza az **Accept** (Elfogadás) lehetőséget.
7. Keresse meg azokat az Azure AD biztonsági csoportokat, amelyekből a Better Mobile-nak szinkronizálnia kell az eszközöket, és válassza ki a csoportokat a listából. Ezután válassza a **Continue** (Folytatás) gombot.
8. Válassza a **Kész** lehetőséget.
9. Újra megjelenik a **fiókhozzáadási** oldal. Zárja be az oldalt. 

## <a name="next-steps"></a>További lépések

- [Jobb Mobile apps beállítása a regisztrált eszközökhöz](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Jobb Mobile apps beállítása a nem regisztrált eszközökhöz](~/protect/mtd-add-apps-unenrolled-devices.md)
