---
title: Gyors útmutató – jelszó-megfelelőségi szabályzat Android-eszközökhöz
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban az Android-eszközökhöz szükséges jelszó hosszának beállításához Microsoft Intune fog használni.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74409789"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Rövid útmutató: Jelszó-megfelelőségi szabályzat létrehozása Android rendszerű eszközökhöz

Ebben a rövid útmutatóban a Microsoft Intune segítségével megkövetelheti a munkaerő Android-felhasználóinak, hogy egy adott hosszúságú jelszót adjanak meg, mielőtt az Android-eszközökön lévő információkhoz hozzáférjenek.

Az Intune-eszközmegfelelőségi szabályzatokkal megszabhatja az eszközök megfelelőségéhez kötelezően szükséges szabályokat és beállításokat. A megfelelőségi szabályzatokat feltételes hozzáféréssel használhatja a vállalati erőforrásokhoz való hozzáférés engedélyezéséhez vagy letiltásához. Emellett lekérhet eszközjelentéseket, és különböző műveleteket hajthat végre meg nem felelés esetén.

> [!IMPORTANT]
> Az alkalmazottak tartalmainak védelme érdekében a jelszóbeállítások mellett egyéb rendszerbiztonsági beállításokat használatát is érdemes fontolóra venni. További információkért tekintse meg a [rendszerbiztonsági beállításokat](compliance-policy-create-android-for-work.md) ismertető cikket.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) [globális rendszergazdaként](../fundamentals/users-add.md#types-of-administrators) vagy Intune [szolgáltatás-rendszergazdaként](../fundamentals/users-add.md#types-of-administrators).

## <a name="create-a-device-compliance-policy"></a>Eszközmegfelelőségi szabályzat létrehozása

Hozzon létre egy eszköz-megfelelőségi szabályzatot, amely megköveteli, hogy a munkaerő Android-felhasználói egy adott hosszúságú jelszót adjanak meg, mielőtt az Android-eszközökön lévő információkhoz hozzáférjenek.

1. Az Intune-ban válassza az **eszközök** > **megfelelőségi szabályzatok** > **házirend létrehozása**lehetőséget.

2. A **Név** mezőben adja meg az **Android compliance** (Android-megfelelőség) nevet. Egy **leírást** is adjon meg.

3. A **platform**területen válassza az **Android Enterprise**lehetőséget.

4. A **Profil típusa**beállításnál válassza a **munkahelyi profil**lehetőséget.

5. Kattintson a **Beállítások** > **Rendszerbiztonság** elemre az Android **Rendszerbiztonság** paneljének megjelenítéséhez.

6. A **Jelszó szükséges a mobileszközök feloldásához** elemnél válassza a **Kötelező** lehetőséget.

7. A **kötelező jelszó típusa**mezőben válasszon ki **legalább numerikus**értéket.

8. A **jelszó minimális hosszához**írja be a **6**értéket.

    ![Képernyőkép csoport létrehozásáról a Microsoft Intune-ban](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. Ha elkészült, kattintson az **OK gombra** >  > **Létrehozás** **gombra** a szabályzat létrehozásához.

Ha sikeresen létrehozta a szabályzatot, az megjelenik az eszköz Complice szabályzatok listájában.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha többé nincs szükség a szabályzatra, törölje. Ehhez jelölje ki a megfelelőségi szabályzatot, és kattintson a **Törlés** gombra.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban az Intune használatával létrehozott egy megfelelőségi szabályzatot az alkalmazottak Android-eszközeihez, hogy legalább hat karakter hosszúságú jelszót kelljen hozzájuk megadni. További információk a megfelelőségi szabályzatok létrehozásáról: [Az Intune eszközmegfelelőségi szabályzatai – első lépések](device-compliance-get-started.md).

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató: Értesítések küldése a nem megfelelő eszközökre](../quickstart-send-notification.md)
