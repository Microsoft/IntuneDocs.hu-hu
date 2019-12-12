---
title: Alkalmazás-alapú feltételes hozzáférési szabályzat beállítása az Intune-nal
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan hozhat létre alkalmazás-alapú feltételes hozzáférési szabályzatot az Intune-nal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712845"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Alkalmazás-alapú feltételes hozzáférési szabályzatok beállítása az Intune-nal

Alkalmazás-alapú feltételes hozzáférési szabályzatokat állíthat be a jóváhagyott alkalmazások listájának részét képező alkalmazásokhoz. A jóváhagyott alkalmazások listája a Microsoft által tesztelt alkalmazásokból áll.

Az alkalmazás-alapú feltételes hozzáférési szabályzatok használata előtt rendelkeznie kell az alkalmazásokra alkalmazott [Intune app Protection-szabályzatokkal](../apps/app-protection-policies.md) .

> [!IMPORTANT]
> Ez a cikk végigvezeti egy alkalmazás-alapú feltételes hozzáférési szabályzat hozzáadásának lépésein. Ugyanezeket a lépéseket használhatja, ha alkalmazásokat ad hozzá, például SharePoint Online, Microsoft Teams és Microsoft Exchange Online, a jóváhagyott alkalmazások listájából.

## <a name="create-app-based-conditional-access-policies"></a>Alkalmazás-alapú feltételes hozzáférési szabályzatok létrehozása

A feltételes hozzáférés az Azure Active Directory (Azure AD) technológiája. Az *Intune* -ból hozzáférő feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure ad*-ből is elérhet. Mivel ugyanaz a csomópont, nem kell váltania az Intune és az Azure AD között a házirendek konfigurálásához.

Mielőtt feltételes hozzáférési szabályzatokat hozna létre a Microsoft Endpoint Manager felügyeleti központból, rendelkeznie kell egy prémium szintű Azure AD licenccel.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Alkalmazás-alapú feltételes hozzáférési szabályzat létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431)

2. Válassza az **Endpoint security** > a **feltételes hozzáférés** > **új szabályzat**lehetőséget.

3. Adja meg a szabályzat **nevét**, majd a *hozzárendelések*területen válassza a **felhasználók és csoportok**lehetőséget. A befoglalási vagy kizárási lehetőségek használatával jelölje ki a szabályzathoz rendelendő csoportokat majd válassza a **Kész** lehetőséget.

4. Válassza a **felhőalapú alkalmazások vagy műveletek**lehetőséget, és válassza ki, hogy mely alkalmazások legyenek védetté. Az **Alkalmazások kijelölése** alatt választhatja például az **Office 365 SharePoint Online** és az **Office 365 Exchange Online** elemeket.

   A módosítások mentéséhez válassza a **Kész** gombot.

5. A **Feltételek** > **Ügyfélalkalmazások** választásával a szabályzat alkalmazásokra és böngészőkre is érvényesíthető. Választhatja például az **Igen**, majd a **Böngésző** és a **Mobilalkalmazások és asztali ügyfelek** lehetőségeket.

   A módosítások mentéséhez válassza a **Kész** gombot.

6. A *hozzáférés-vezérlés*területen válassza az **Engedélyezés** lehetőséget, hogy az eszköz Megfelelőségén alapuló feltételes hozzáférést alkalmazzon. Választhatja például a **Hozzáférés engedélyezése** > **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget.

   A módosítások mentéséhez válassza az **Választ** gombot.

7. A **házirend engedélyezése**beállításnál válassza **a be**lehetőséget, majd válassza a **Létrehozás** lehetőséget a módosítások mentéséhez.





## <a name="next-steps"></a>További lépések
[Modern hitelesítés nélküli alkalmazások blokkolása](app-modern-authentication-block.md)

## <a name="see-also"></a>További információ

[Alkalmazásadatok védelme alkalmazásvédelmi szabályzatokkal](../apps/app-protection-policies.md)
[Feltételes hozzáférés az Azure Active Directory-ban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
