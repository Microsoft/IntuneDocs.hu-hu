---
title: Gyors útmutató – jelszó-megfelelőségi szabályzat Android-eszközökhöz
titleSuffix: Microsoft Intune
description: Ebben a rövid útmutatóban a Microsoft Intune-t fogja használni az Android-eszközöknél megkövetelt jelszóhosszúság beállításához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30c4d5976b7f743a12a9691878e2b7031e373b1d
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001835"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>QuickStart Jelszó-megfelelőségi szabályzat létrehozása Android-eszközökhöz

Ebben a rövid útmutatóban a Microsoft Intune-t használjuk annak beállítására, hogy a rendszer az Android-eszközöket használó munkatársaktól adott hosszúságú jelszót kérjen el, mielőtt engedélyezné az eszközökön található információkhoz való hozzáférést. 

Az Intune-eszközmegfelelőségi szabályzatokkal megszabhatja az eszközök megfelelőségéhez kötelezően szükséges szabályokat és beállításokat. A megfelelőségi szabályzatokat feltételes hozzáféréssel használhatja a vállalati erőforrásokhoz való hozzáférés engedélyezéséhez vagy letiltásához. Emellett lekérhet eszközjelentéseket, és különböző műveleteket hajthat végre meg nem felelés esetén.

> [!IMPORTANT]
> Az alkalmazottak tartalmainak védelme érdekében a jelszóbeállítások mellett egyéb rendszerbiztonsági beállításokat használatát is érdemes fontolóra venni. További információkért tekintse meg a [rendszerbiztonsági beállításokat](compliance-policy-create-android-for-work.md) ismertető cikket.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon egy ingyenes próbafiókkal](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune-ba](https://aka.ms/intuneportal) globális rendszergazdaként vagy Intune-szolgáltatásadminisztrátorként. 

## <a name="create-a-device-compliance-policy"></a>Eszközmegfelelőségi szabályzat létrehozása

Ebben a rövid útmutatóban a Intune-t használja majd annak beállítására, hogy a rendszer az Android-eszközöket használó munkatársaktól adott hosszúságú jelszót kérjen el, mielőtt engedélyezné az eszközökön található információkhoz való hozzáférést.

1. Az Intune-ban válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
2. A **Név** mezőben adja meg az **Android compliance** (Android-megfelelőség) nevet. Egy **leírást** is adjon meg.
3. A **Platform** beállításban válassza az **Android** lehetőséget. 
4. Kattintson a **Beállítások** > **Rendszerbiztonság** elemre az Android **Rendszerbiztonság** paneljének megjelenítéséhez.
5. Kattintson a **Kötelező** elemre a **Jelszó szükséges a mobileszközök feloldásához** mellett.
6. Válasszon ki **legalább egy numerikus** **értéket a kötelező jelszó típusa**mellett.
7. Adja meg a **6** értéket a **Jelszó minimális hossza** mellett. 

    ![Képernyőkép egy csoport létrehozásáról a Microsoft Intune-ban](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. Ha elkészült, a szabályzat létrehozásához kattintson az **OK** > **OK** > **Létrehozás** gombra.

Ha sikeresen létrehozta a szabályzatot, az megjelenik az eszközmegfelelőségi szabályzatok listájában. 

## <a name="clean-up-resources"></a>Az erőforrások eltávolítása

Ha többé nincs szükség a szabályzatra, törölje. Ehhez jelölje ki a megfelelőségi szabályzatot, és kattintson a **Törlés** gombra.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban az Intune használatával létrehozott egy megfelelőségi szabályzatot az alkalmazottak Android-eszközeihez, hogy legalább hat karakter hosszúságú jelszót kelljen hozzájuk megadni. További információk a megfelelőségi szabályzatok létrehozásáról: [Az Intune eszközmegfelelőségi szabályzatai – első lépések](device-compliance-get-started.md).

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [QuickStart Értesítések küldése a nem megfelelő eszközökre](quickstart-send-notification.md)
