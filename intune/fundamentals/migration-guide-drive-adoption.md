---
title: Végfelhasználói elfogadás a feltételes hozzáféréssel
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan használható a feltételes hozzáférés a regisztrációhoz a Microsoft Intuneban.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 115313816542fd642e6a0c67900abd48b7146e42
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510060"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>A végfelhasználói bevezetés bevezetése feltételes hozzáféréssel Microsoft Intune

A feltételes hozzáférési funkciók Intune-nal való engedélyezése, például a nem regisztrált eszközökre vonatkozó e-mailek letiltása, a regisztrációt és a megfelelőséget is lehetővé teszi, de nem szükséges, hogy az áttelepítés sikeres legyen. ezt inkább az áttérési célértékek és a biztonsági követelmények alapján lehet megítélni.

## <a name="migration-campaign-with-conditional-access"></a>Áttelepítési kampány feltételes hozzáféréssel

Az alábbi tipikus módszer a feltételes hozzáféréssel rendelkező migrációs kampány fejlesztéséhez:

1. Állítsa be a feltételes hozzáférési szabályokat az összes felhasználóra vonatkozóan, de kifejezetten zárja ki a régi MDM-szolgáltatótól áttelepíteni kívánt felhasználókat. Létrehozhat egy Azure AD-felhasználói csoportot az összes feltételes hozzáférés kizárt felhasználóval.

2. A felhasználók áttelepítésekor távolítsa el őket a feltételes hozzáférés kizárási csoportjából.

3. Az áttelepítés befejezése után az összes feltételes hozzáférési szabályzatot állítsa be úgy, hogy alapértelmezés szerint blokkoljon, kivéve, ha az Intune engedélyezi a hozzáférést.

### <a name="advantages"></a>Előnyök

- Hozzáférés-vezérlést biztosít az új, illetve a korábbi megoldással nem felügyelt felhasználói fiókoknak is.

- Türelmi időszakot kínál az előző megoldás felhasználóinak a migrációra.

- Minimálisra szorítja a produktivitás csökkenését.

### <a name="disadvantages"></a>Hátrányok

- Az előző megoldás felhasználói a nem felügyelt eszközök használatával férhetnek hozzá az erőforrásokhoz, amíg a feltételes hozzáférés engedélyezve van a felhasználók számára.


Ez csak egy megközelítés a sok közül: Kiválaszthat egy egyszerűbb folyamatot, amely az összes feltételes hozzáférést elhalasztja mindaddig, amíg az összes szakaszt be nem utasította a regisztrálásra, vagy egy szigorúbb folyamat, amely a feltételes hozzáférést a kezdetektől kényszeríti, és teljes megfelelőséget követel meg az összes hozzáféréshez.

- További tudnivalók [a feltételes hozzáférésről](../protect/conditional-access.md)

## <a name="task-list-for-conditional-access"></a>Feladatlista feltételes hozzáféréshez

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>1\. feladat: döntse el, hogyan fogja megvalósítani a feltételes hozzáférést

[A feltételes hozzáférés használatának gyakori módjai](../protect/conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>2\. feladat: az Intune feltételes hozzáférésének beállítása

Válasszon egyet az alábbi lehetőségek közül:

- [Feltételes hozzáférés konfigurálása Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [A helyszíni Exchange-összekötő telepítése az Intune-nal](../protect/exchange-connector-install.md)

- [Alkalmazás-alapú feltételes hozzáférési házirendek beállítása az Exchange Online-hoz](../protect/app-based-conditional-access-intune-create.md)

- [Alkalmazás-alapú feltételes hozzáférési szabályzatok beállítása a SharePoint Online-hoz](../protect/app-based-conditional-access-intune-create.md)

- [Modern hitelesítés nélküli alkalmazások blokkolása (ADAL)](../protect/app-modern-authentication-block.md)

## <a name="next-steps"></a>További lépések

További tudnivalókat a [szokásos migrálási ciklus](../migration-guide-cycle.md) ismertetőjében talál.
