---
title: Ellenőrzés Point SandBlast MTD integrálása
titleSuffix: Microsoft Intune
description: A CheckPoint SandBlast Mobile Threat Defense (MTD) beállítása az Intune-ban a mobileszközök a vállalati erőforrásokhoz való hozzáférésének kezeléséhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28c2feb06e27dc87870ba81a180f46687571774e
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292242"
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>A Check Point SandBlast Mobile integrálása az Intune-nal

## <a name="before-you-begin"></a>Előkészületek

> [!NOTE] 
> Az alábbi lépéseket kell elvégezni a [Check Point SandBlast Mobile MTD konzolján](https://intune-4.eu1.locsec.net/).

A Check Point SandBlast Mobile Intune szolgáltatással való integrálásának megkezdése előtt győződjön meg arról, hogy rendelkezik a következőkkel:

-   Microsoft Intune-előfizetés

-   Azure Active Directory rendszergazdai hitelesítő adatok a következő engedélyek megadására:

    -   Bejelentkezés és felhasználói profil olvasása

    -   A címtár elérése a bejelentkezett felhasználó nevében

    -   Címtáradatok olvasása

    -   Eszközadatok küldése az Intune-ba

-   Rendszergazdai hitelesítő adatok a Check Point SandBlast Mobile MTD konzol eléréséhez.

### <a name="check-point-sandblast-app-authorization"></a>Check Point SandBlast alkalmazás engedélyezése

A Check Point SandBlast alkalmazás hitelesítési folyamata a következőkből áll:

-   Az eszközállapot-adatok az Intune-nak való visszaküldésének engedélyezése Check Point SandBlast Mobile szolgáltatás számára.

-   A Check Point SandBlast Mobile szinkronizálása az Azure AD regisztrációs csoporttagsággal az eszköz adatbázisának feltöltéséhez.

-   Az Azure AD egyszeri bejelentkezési (SSO) használatának engedélyezése a Check Point SandBlast felügyeleti konzol számára.

-   Bejelentkezés engedélyezése a Check Point SandBlast Mobile alkalmazás számára az Azure AD egyszeri bejelentkezés használatával.

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>A Check Point SandBlast Mobile-integráció beállítása

1.  Nyissa meg a [Check Point SandBlast Mobile MTD konzolt](https://intune-4.eu1.locsec.net/), és jelentkezzen be a hitelesítő adataival.

2.  Kattintson a **Beállítások** fülre.

3.  Válassza az **Eszközkezelés**, majd a **Beállítások** lehetőséget.

4.  Válassza a **Microsoft Intune** elemet az **MDM szolgáltatás** legördülő listából.

5.  Miután beállította a Microsoft Intune-t mobileszköz-kezelési szolgáltatásként, a megjelenő **Microsoft Intune-konfiguráció** ablakban válassza a **Hozzáadás a saját szervezethez** lehetőséget az egyes eszközplatformokhoz: iOS, Android és Windows a Check Point SandBlast Mobile hitelesítésére az Intune-nal és az Azure AD-vel való kommunikációhoz.

    ![Kép a Check Point MTD Intune-konfigurációjáról](./media/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > A következő lépéssel való folytatáshoz hozzá kell adnia az összes eszközplatformot.

6.  Válassza az **Elfogadás** elemet a Check Point SandBlast mobilalkalmazás engedélyezésére az Intune és az Azure Active Directoryval folytatott kommunikációhoz.

7.  Miután engedélyezte az összes eszközplatformot, meg kell adnia az Azure AD biztonsági csoportot.

8.  Válassza az **Ellenőrzés** elemet, és az Azure AD biztonsági csoport sikeres ellenőrzését követően válassza a **Mentés** elemet.

## <a name="next-steps"></a>További lépések

- [Check Point SandBlast Mobile-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)
