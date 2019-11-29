---
title: Az alkalmazásvédelmi szabályzatok konfigurációjának ellenőrzése
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan tesztelheti, hogy az App Protection-házirend be van-e állítva, és megfelelően működik-e a Microsoft Intuneban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9c3e775773ab08721cb3a65858f3d8c8402104f
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563736"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Az alkalmazás-védelmi szabályzat beállításának érvényesítése Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Annak ellenőrzése, hogy az alkalmazásvédelmi szabályzat megfelelően be van-e állítva és működik-e. Az útmutató az Azure Portal webhelyen található alkalmazásvédelmi szabályzatokra vonatkozik.

## <a name="checking-for-symptoms"></a>Hibajelenségek keresése
Mivel az alkalmazásvédelem egy adatvédelmi eszköz, nem valószínű, hogy a felhasználók jeleznek problémákat. Ha probléma merül fel az App Protection-konfigurációval kapcsolatban, a felhasználónak korlátlan hozzáférése lesz, ahogy az alkalmazás védelme nélkül lenne, és nem tudja, hogy van probléma. Ezért javasoljuk, hogy az alkalmazás-védelmi szabályzatokat olyan felhasználók kis csoportjának kipróbálásával érvényesítse, akik szándékosan tesztelik az alkalmazás védelmi korlátozásait.

## <a name="what-to-check"></a>Mit kell ellenőrizni?

Ha a tesztelés azt mutatja, hogy az alkalmazás védelmi házirendje nem a várt módon működik, ellenőrizze az alábbi elemeket:

- A felhasználók rendelkeznek alkalmazásvédelmi licenccel?
- A felhasználók rendelkeznek O365-licenccel?
- A felhasználók app Protection-alkalmazásainak állapota az elvárt módon. Az alkalmazások lehetséges állapotai: **Bejelentkezett** és **Nem bejelentkezett**.

### <a name="user-app-protection-status"></a>A felhasználók alkalmazásvédelmi állapota
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza az **alkalmazások** >  az **app Protection állapota**lehetőséget, majd válassza a **hozzárendelt felhasználók** csempét. 
4. Az **alkalmazás-jelentéskészítés** lapon válassza a **felhasználó kiválasztása** lehetőséget a felhasználók és csoportok listájának létrehozásához. 
5. Keresse meg és válassza ki a kívánt felhasználót a listából, majd válassza a **felhasználó kiválasztása**lehetőséget. Az **alkalmazás-jelentési** panel felső részén láthatja, hogy a felhasználó rendelkezik-e licenccel az alkalmazás védelméhez. Azt is megtudhatja, hogy a felhasználó rendelkezik-e licenccel a O365 és az alkalmazás állapotáról az összes felhasználó eszközén.

## <a name="what-to-do"></a>Mi a teendő
A felhasználói állapotnak megfelelően az alábbi műveleteket hajthatja végre:

- Ha a felhasználó nem rendelkezik az App Protection licenccel, rendeljen hozzá egy [Intune-licencet](../fundamentals/licenses.md) a felhasználóhoz.
- Ha a felhasználó nem rendelkezik licenccel a O365, szerezze be a felhasználóhoz tartozó [licencet](../fundamentals/licenses.md) .
- Ha a felhasználó alkalmazás **nem bejelentkezettként**van felsorolva, ellenőrizze, hogy helyesen konfigurálta-e az alkalmazásra vonatkozó [adatvédelmi szabályzatot](app-protection-policies-validate.md) .
- Győződjön meg arról, hogy ezek a feltételek minden olyan felhasználóra érvényesek, amelyre alkalmazni szeretné az [alkalmazás-védelmi szabályzatokat](app-protection-policies-monitor.md) .

## <a name="see-also"></a>További információ

- [Mi az Intune alkalmazásvédelmi szabályzata?](app-protection-policies.md)
- [Az Intune-t tartalmazó licencek](../fundamentals/licenses.md)
- [Licencek kiosztása a felhasználók számára, hogy regisztrálni tudják az eszközöket az Intune-ban](../fundamentals/licenses-assign.md)
- [Az alkalmazás-védelmi szabályzat beállításának ellenőrzése](app-protection-policies-validate.md)
- [Az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md)

