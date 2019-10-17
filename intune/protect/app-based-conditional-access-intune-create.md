---
title: Alkalmazás-alapú feltételes hozzáférési szabályzat beállítása az Intune-nal
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan hozhat létre alkalmazás-alapú feltételes hozzáférési szabályzatot az Intune-nal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94e9fcc77f8260c4a63150b5d0aef033677c524a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509673"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Alkalmazás-alapú feltételes hozzáférési szabályzatok beállítása az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Alkalmazás-alapú feltételes hozzáférési szabályzatokat állíthat be a jóváhagyott alkalmazások listájának részét képező alkalmazásokhoz. A jóváhagyott alkalmazások listája a Microsoft által tesztelt alkalmazásokból áll.

> [!IMPORTANT]
> Ez a cikk végigvezeti egy alkalmazás-alapú feltételes hozzáférési szabályzat hozzáadásának lépésein. Ugyanezeket a lépéseket használhatja, ha alkalmazásokat ad hozzá, például SharePoint Online, Microsoft Teams és Microsoft Exchange Online, a jóváhagyott alkalmazások listájából.

## <a name="create-app-based-conditional-access-policies"></a>Alkalmazás-alapú feltételes hozzáférési szabályzatok létrehozása
A feltételes hozzáférés az Azure Active Directory (Azure AD) technológiája. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni. Ez azt jelenti, hogy nem kell váltania az Intune és az Azure AD között a házirendek konfigurálásához.

> [!IMPORTANT]
> A feltételes hozzáférési szabályzatok az Intune-portálról történő létrehozásához rendelkeznie kell egy prémium szintű Azure AD licenccel.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Alkalmazás-alapú feltételes hozzáférési szabályzat létrehozása

> [!IMPORTANT]
> Az alkalmazás-alapú feltételes hozzáférési szabályzatok használata előtt az alkalmazásokra alkalmaznia kell az [Intune app Protection-szabályzatokat](../apps/app-protection-policies.md) .

1. Az **Intune irányítópultján**válassza a **feltételes hozzáférés**lehetőséget.

2. Az új alkalmazás-alapú feltételes hozzáférési szabályzat létrehozásához a **házirendek** ablaktáblán válassza az **új** szabályzat lehetőséget.

4. A szabályzatnév megadása, valamint a **Hozzárendelések** szakaszban hozzáférhető beállítások konfigurálása után válassza a **Hozzáférés-szabályozás** szakaszban található **Engedélyezés** elemet.

5. Az új szabályzat mentéséhez válassza a **Jóváhagyott ügyfélalkalmazás megkövetelése**, majd a **Kijelölés**, végül pedig a **Létrehozás** lehetőséget.

## <a name="next-steps"></a>További lépések
[Modern hitelesítés nélküli alkalmazások blokkolása](app-modern-authentication-block.md)

## <a name="see-also"></a>További információ

[Alkalmazásadatok védelme alkalmazásvédelmi szabályzatokkal](../apps/app-protection-policies.md)
[Feltételes hozzáférés az Azure Active Directory-ban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
