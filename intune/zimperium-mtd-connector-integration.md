---
title: A Zimperium MTD integrálása a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: A Zimperium Mobile Threat Defense (MTD) beállítása a Microsoft Intune-ban a mobileszközök a vállalati erőforrásokhoz való hozzáférésének kezeléséhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3eb18c45f81e427f1d14ce77086e0d7684994e82
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884162"
---
# <a name="integrate-zimperium-with-intune"></a>A Zimperium integrálása az Intune-nal

A Zimperium mobilfenyegetések elleni megoldás Intune-beli integrálásához kövesse az alábbi lépéseket.

## <a name="before-you-begin"></a>Előkészületek

> [!NOTE]
> Az alábbi lépéseket a [Zimperium MTD konzolon](https://www.zimperium.com/platform) kell végrehajtania.

Mielőtt elkezdené a Zimperium integrálását az Intune-nal, ellenőrizze, hogy rendelkezik-e az alábbi előfizetéssel és hitelesítő adatokkal:

- Microsoft Intune-előfizetés

- Azure Active Directory a globális rendszergazda rendszergazdai hitelesítő adatait a következő engedélyek megadásához:

  - Bejelentkezés és felhasználói profil olvasása

  - A címtár elérése a bejelentkezett felhasználó nevében

  - Címtáradatok olvasása

  - Eszközadatok küldése az Intune-ba

- Rendszergazdai hitelesítő adatok a Zimperium MTD konzol eléréséhez.

### <a name="zimperium-app-authorization"></a>A Zimperium alkalmazás engedélyezése

A Zimperium alkalmazás engedélyezési folyamata a következő:

- Adja meg a Zimperium szolgáltatás engedélyeit az eszköz állapotával kapcsolatos információk az Intune-nal való visszaadásához. Ezen engedélyek megadásához globális rendszergazdai hitelesítő adatokat kell használnia. Az engedélyek megadása egyszeri művelet. Az engedélyek megadása után a globális rendszergazdai hitelesítő adatok nem szükségesek a napi művelethez.

- A Zimperium szinkronizálást végez az Azure Active Directory (AD) regisztrációs csoporttagsággal az eszköz adatbázisának feltöltéséhez.

- Engedélyezze a Zimperium felügyeleti konzolja számára az Azure AD-alapú egyszeri bejelentkezést (SSO-t).

- Engedélyezze a Zimperium alkalmazás számára az Azure AD SSO használatát a bejelentkezéshez.

A beleegyező és Azure Active Directory alkalmazásokkal kapcsolatos további információkért lásd: [az engedélyek kérése egy címtár](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) -rendszergazdától a *Azure Active Directory v 2.0-végpont engedélyei és beleegyezik*a Azure Active Directory című cikkben.


## <a name="to-set-up-zimperium-integration"></a>A Zimperium-integráció beállítása

1. Nyissa meg a [Zimperium MTD konzolt](https://www.zimperium.com/platform), és jelentkezzen be a hitelesítő adataival. A Zimperium-integráció telepítési folyamatának végrehajtásához be kell jelentkeznie egy olyan Azure Active Directory felhasználóval, aki globális rendszergazdai szerepkörrel rendelkezik. Ez az egyszeri telepítési művelet a globális rendszergazdai jogosultságokat használja a szervezeten belüli engedélyek megadására a Zimperium-alkalmazások számára az Intune-nal való kommunikációhoz. 

2. Válassza a bal oldali menü **Felügyelet** pontját.

3. Válassza az **MDM-beállítások** panelt.

4. Válassza az **MDM hozzáadása** elemet, majd az **MDM-szolgáltatók** listájából válassza ki a **Microsoft Intune** elemet.

5. Miután beállította a Microsoft Intunet a MDM szolgáltatásként, megjelenik a **Microsoft Intune konfigurációs** ablak, válassza ki a **Azure Active Directory hozzáadása** lehetőséget az egyes beállításokhoz: **Zimperium zConsole**, **cipzáras iOS-és Android-alkalmazások** , amelyek engedélyezik a Zimperium számára az Intune-nal és az Azure ad-vel való kommunikációt az Azure ad egyszeri bejelentkezéssel.

    > [!IMPORTANT]  
    > Az Intune-nal való integrációs folyamat befejezéséhez hozzá kell adnia a Zimperium zConsole, a zip iOS és Android rendszerű alkalmazásokat.

6. Válassza az **Elfogadás** elemet. Ezzel engedélyezi, hogy a Zimperium kommunikáljon az Intune-nal és az Azure Active Directoryval.

7. Miután hozzáadta a **Zimperium zConsole** és a **zip-iOS-és Android-** alkalmazásokat az Azure ad-hez, adja hozzá az Azure ad biztonsági csoportjait. A hozzáadás lehetővé teszi, hogy a Zimperium szinkronizálja a szolgáltatással az Azure AD biztonsági csoportját.

8. A **Befejezés** elem kiválasztásával menti a konfigurációt, és elindítja az Azure AD biztonsági csoport első szinkronizálását.

9. Jelentkezzen ki a Zimperium MTD-konzolról.

## <a name="next-steps"></a>További lépések

- [Zimperium-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)
