---
title: Eszközök PIN-kódjának visszaállítása a Microsoft Intune-nal – Azure | Microsoft Docs
description: A PIN-kód eltávolítása művelettel eltávolíthatja vagy visszaállíthatja a PIN-kódot az Intune-nal kezelt vagy figyelt eszközökön.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2a5629e6a318836e23c6a2f7fceb59363a0ed72
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812494"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Eszközök PIN-kódjának visszaállítása vagy eltávolítása az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a dokumentum a PIN-kód alaphelyzetbe állítása és a munkahelyi profil PIN-kód alaphelyzetbe állítását ismerteti az Android Enterprise (korábbi nevén Android for Work vagy AfW) eszközökön. Fontos megjegyezni, hogy ez a különbség a követelmények szerint változhat. Az eszközszintű PIN-kód alaphelyzetbe állítása az egész eszközön átállítja a PIN-kódot. A munkahelyi profil PIN-kódjának alaphelyzetbe állítása csak a felhasználó munkahelyi profiljára vonatkozó PIN-kódot állítja át a vállalati Android rendszerű eszközökön.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Az eszközszintű PIN-kód alaphelyzetbe állításának támogatott platformjai

| Platfésm | Támogatott? |
| ---- | ---- |
| 6\.x vagy régebbi verziójú Android-eszközök | Igen |
| Eszköz tulajdonosként regisztrált androidos vállalati eszközök | Igen |
| iOS-eszközök | Igen |
| Felhasználói regisztrációval regisztrált iOS-eszközök | Nem |
| Munkahelyi profillal regisztrált Android-eszközök | Nem |
| 7\.0-ás vagy újabb verziójú Android-eszközök | Nem |
| macOS | Nem |
| Windows | Nem |

Android-eszközök esetén ez azt jelenti, hogy az eszköz szintű PIN-kód alaphelyzetbe állítása csak a 6. x vagy korábbi rendszerű eszközökön, illetve a kioszk módban futó androidos vállalati eszközökön támogatott. Ennek az az oka, hogy a Google többé nem támogatja az Android 7 rendszerű eszközökön a PIN-kód/jelszó alaphelyzetbe állítását eszközrendszergazda által jóváhagyott alkalmazásokból, minden MDM-szállítóra vonatkozóan.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Azok a platformok, amelyeken alaphelyzetbe állítható a vállalati Android munkahelyi profil PIN-kódja

| Platfésm | Támogatott? |
| ---- | ---- |
| Munkahelyi profillal regisztrált, 8.0-s vagy újabb verziójú vállalati Android-eszközök | Igen |
| Munkahelyi profillal regisztrált, 7.x vagy korábbi verziójú vállalati Android-eszközök | Nem |
| 7\.x vagy korábbi verziójú Android-eszközök | Nem |

A munkahelyi profilokhoz a PIN-kód alaphelyzetbe állítása művelettel hozhat létre új PIN-kódot. Ez a művelet elindítja a PIN-kód alaphelyzetbe állítását, és új, ideiglenes PIN-kódot hoz létre, kizárólag a munkahelyi profilhoz. 

## <a name="reset-a-passcode"></a>Új PIN-kód kérése


1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431) a következő szerepkörök bármelyikével: Azure Active Directory globális rendszergazda, Azure Active Directory Intune szolgáltatás-rendszergazda, segélyszolgálat-kezelő vagy szerepkör-rendszergazda.
2. Válassza az **Eszközök**, majd a **Minden eszköz** lehetőséget.
3. Az Ön által kezel eszközök listájáról válasszon ki egy eszközt, majd válassza a **...További** lehetőséget. Majd válassza a **PIN-kód eltávolítása** távoli eszközműveletet.

## <a name="reset-android-work-profile-passcodes"></a>Androidos munkahelyi profilok PIN-kódjának alaphelyzetbe állítása

A támogatott, androidos munkahelyi profillal regisztrált vállalati eszközök végfelhasználói új feloldó jelszót vagy biztonsági kérdést kapnak a felügyelt profilhoz.

A 8.x vagy újabb verziójú, munkahelyi profillal regisztrált vállalati Android-eszközök végfelhasználói a regisztráció befejezése után azonnal értesítést kapnak arról, hogy aktiválniuk kell az új PIN-kódot. Az értesítés akkor jelenik meg, ha a munkahelyi profilban kötelező jelszót megadni, és be is van állítva jelszó. A PIN-kód megadása után az értesítés eltűnik.


## <a name="remove-ios-passcodes"></a>iOS-beli PIN-kódok eltávolítása

A PIN-kódok alaphelyzetbe állítás helyett törlődnek az iOS-eszközökről. Ha PIN-kódokra vonatkozó megfelelőségi szabályzat van érvényben, az eszköz megkéri a felhasználót, hogy állítson be egy új jelszót a Beállítások területen.

## <a name="next-steps"></a>További lépések

A kezdeményezett művelet állapotát az **Eszközök** panel **Eszközműveletek** szakaszában tekintheti meg.
