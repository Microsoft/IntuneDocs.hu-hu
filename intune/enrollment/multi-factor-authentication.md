---
title: Többtényezős hitelesítés megkövetelése az Intune-os eszközregisztrációhoz
titleSuffix: Microsoft Intune
description: A többtényezős hitelesítés kötelezővé tétele az Azure AD-ben az Intune-os eszközregisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db04b93deffd2476a97b952fd1c6942fa79e1f05
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955388"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Többtényezős hitelesítés megkövetelése az Intune-os eszközregisztrációhoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune-nal növelheti vállalati erőforrásai biztonságát az Azure Active Directory (AD) többtényezős hitelesítést (MFA) eszközregisztrációkhoz való használatával.

Az MFA az alábbiak közül követeli meg legalább két ellenőrzési mód használatát:

- egy, a felhasználó által ismert információ (általában jelszó vagy PIN-kód)
- egy, a felhasználó birtokában lévő dolog (nehezen másolható, megbízható eszköz, például telefon)
- egy, a felhasználót azonosító dolog (biometrikus adatok, például ujjlenyomat).

Az MFA iOS, Android, Windows 8.1-es vagy újabb, Windows Phone 8.1-es vagy Windows 10 Mobile vagy újabb rendszerű eszközökön támogatott.

Az MFA engedélyezésekor a végfelhasználóknak kétféle hitelesítő adatot kell megadniuk az eszközök regisztrációjához.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Kötelező többtényezős hitelesítés beállítása az eszközök regisztrálásához az Intune-ban

Ha meg szeretné követelni a többtényezős hitelesítést a regisztráció során, tegye a következőket:

>[!Important]
>Ennek a szabályzatnak a használatához a felhasználókhoz rendelt legalább prémium P1 szintű Azure Active Directoryval kell rendelkeznie.

>[!Important]
>Ne konfiguráljon **eszközalapú hozzáférési szabályokat** a Microsoft Intune-regisztrációhoz.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **feltételes hozzáférés**lehetőséget. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.
2. Válassza az **Új szabályzat** lehetőséget.
3. Az **Új** szabályzat mezőbe írjon be egy beszédes nevet a szabályzathoz.
4. A **Hozzárendelések** szakaszban válassza a **Felhasználók és csoportok** lehetőséget. 
5. A **Felhasználók és csoportok** területen válassza a **Felhasználók vagy csoportok kiválasztása** lehetőséget, majd jelölje be a **Felhasználók és csoportok** jelölőnégyzetet. Válassza ki azokat a felhasználókat és csoportokat, amelyek meg fogják kapni ezt a szabályzatot, majd válassza a **Kész** elemet.
6. A **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.
7. A **Felhőalkalmazások** **Intune** lapján válassza az **Alkalmazások kiválasztása** elemet, majd a **Kijelölés** > **Microsoft Intune-regisztráció** lehetőséget, végül a **Kész** gombot. **Microsoft Intune regisztráció**kiválasztásával a feltételes hozzáférési MFA csak az eszköz regisztrálására vonatkozik (egyszeri MFA-kérés).
8. A **Hozzárendelések** szakasz **Feltételek** területén nem kell semmilyen beállítást sem megadnia az MFA-hoz.
9. A **Hozzáférés-vezérlés** területen válassza az **Engedélyezés** elemet.
10. Az **Engedélyezés** szakaszban válassza a **Hozzáférés engedélyezése** lehetőséget, majd válassza a **Többtényezős hitelesítés megkövetelése** elemet. Ne válassza ki az **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget, mert az eszközök megfelelőségét nem lehet ellenőrizni, amíg nincsenek regisztrálva. Válassza a **Kiválasztás** elemet.
11. Az **Új szabályzat** szakaszban válassza a **Szabályzat engedélyezése** > **Be** beállítást, majd a **Létrehozás** gombot.



## <a name="next-steps"></a>További lépések

Miután a végfelhasználók regisztrálták eszközeiket, egy második hitelesítési módot is használniuk kell, például PIN-kódot, telefont vagy biometrikát.
