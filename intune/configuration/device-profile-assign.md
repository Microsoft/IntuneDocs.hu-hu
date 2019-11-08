---
title: Eszközprofilok hozzárendelése az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az Azure Portal használatával rendelhet hozzá eszközprofilokat és szabályzatokat a felhasználókhoz és eszközökhöz. Megtudhatja, hogyan zárhat ki csoportokat Microsoft Intune-beli profil-hozzárendelésből.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50b91251572e45669f197df7ac4e5ff94caf47a1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755333"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Felhasználói és eszközprofilok hozzárendelése a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Létrehoz egy profilt, és tartalmazza a megadott beállításokat. A következő lépés a profil üzembe helyezése vagy "kiosztása" a Azure Active Directory (Azure AD) felhasználóhoz vagy eszköz csoporthoz. Ha hozzá van rendelve, a felhasználók és az eszközök megkapják a profilt, és a rendszer alkalmazza a megadott beállításokat.

Ebből a cikkből megtudhatja, hogyan rendelhet hozzá egy profilt, és tartalmaz néhány információt a hatókör-címkék használatáról a profilokban.

> [!NOTE]  
> Ha egy házirendet eltávolítanak vagy már nem rendelnek hozzá egy eszközhöz, a beállítás megtarthatja a meglévő értéket. A beállítás nem tér át alapértelmezett értékre. Ha másik értékre szeretné módosítani a beállítást, hozzon létre egy új szabályzatot, és rendelje hozzá.

## <a name="before-you-begin"></a>Előkészületek

Győződjön meg arról, hogy rendelkezik a megfelelő szerepkörrel a házirendek hozzárendeléséhez. További információ: [szerepköralapú hozzáférés-vezérlés (RBAC) Microsoft Intunesal](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Eszközprofil hozzárendelése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok**lehetőséget. Az összes profil megjelenik.
3. Válassza ki a profilt, amelyhez > **hozzárendeléseket**szeretne hozzárendelni.
4. Válassza a csoportok **belefoglalása** vagy a csoportok **kizárása** lehetőséget, majd válassza ki a csoportokat. A csoportok kiválasztásakor egy Azure AD-csoportot is választ. Több csoport kijelöléséhez tartsa lenyomva a **CTRL** billentyűt, és válassza ki a csoportokat.

    ![Képernyőkép profil hozzárendelésekor a csoportok belefoglalásához és kizárásához megadható beállításokról](./media/device-profile-assign/group-include-exclude.png)

5. **Mentse** a változtatásokat.

### <a name="evaluate-how-many-users-are-targeted"></a>Annak kiértékelése, hogy hány felhasználó van megcélozva

Ha hozzárendeli a profilt, azt is **kiértékelheti** , hogy hány felhasználót érint a rendszer. Ez a szolgáltatás kiszámítja a felhasználókat; nem számítja ki az eszközöket.

1. A felügyeleti központban válassza az **eszközök** > **konfigurációs profilok**lehetőséget.
2. Válassza ki a profilt > **hozzárendelések** > **kiértékelését**. Egy üzenet azt mutatja, hogy a profil hány felhasználót céloz meg.

Ha a **kiértékelés** gomb szürkén jelenik meg, ellenőrizze, hogy a profil hozzá van-e rendelve egy vagy több csoporthoz.

## <a name="use-scope-tags-or-applicability-rules"></a>Hatókör-címkék vagy alkalmazhatósági szabályok használata

A profilok létrehozásakor vagy frissítésekor hozzáadhat hatókör-címkéket és alkalmazhatósági szabályokat is a profilhoz.

A **hatókör címkéi** lehetővé teszik a házirendek hozzárendelését és szűrését adott csoportokra, például az emberi erőforrásokra vagy az összes US-NC-alkalmazottakra. [A RBAC és a hatókör címkéi a terjesztéshez](../fundamentals/scope-tags.md) további információkat is használhatnak.

Windows 10-es eszközökön olyan **alkalmazhatósági szabályokat** adhat hozzá, hogy a profil csak egy adott operációsrendszer-verzióra vagy egy adott Windows-kiadásra vonatkozzon. Az [alkalmazhatósági szabályok](device-profile-create.md#applicability-rules) további információval rendelkeznek.

## <a name="exclude-groups-from-a-profile-assignment"></a>Csoportok kizárása profil hozzárendelésekor

Az Intune-eszköz konfigurációs profiljai lehetővé teszik csoportok belefoglalását és kizárását a szabályzat-hozzárendelésből.

Ajánlott eljárásként hozzon létre és rendeljen hozzá házirendeket kifejezetten a felhasználói csoportokhoz. És hozzon létre és rendeljen hozzá különböző szabályzatokat kifejezetten az eszközök csoportjaihoz. A csoportokkal kapcsolatos további információkért lásd: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](../fundamentals/groups-add.md).

A szabályzatok kiosztásakor használja a következő táblázatot a csoportok belefoglalása és kizárása esetén. A pipa azt jelenti, hogy a hozzárendelés támogatott:

![A támogatott beállítások közé tartoznak a profil-hozzárendelésből származó csoportok vagy kizárások](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Tudnivalók

- A kizárás elsőbbséget élvez a következő azonos csoport típusú forgatókönyvek belefoglalásakor:

  - Felhasználói csoportok belefoglalása és felhasználói csoportok kizárása
  - Eszközcsoport-csoportokkal együtt

  Például hozzárendelhet egy eszköz profilt a **minden vállalati felhasználó** felhasználói csoporthoz, de kizárhatja a tagokat a **vezető felügyeleti munkatárs** felhasználói csoportban. Mivel mindkét csoport felhasználói csoport, az **összes vállalati felhasználó** , kivéve a **vezető felügyeleti személyzetet** , megkapja a szabályzatot.

- Az Intune nem értékeli ki a felhasználók és az eszközök közötti csoportok kapcsolatait. Ha vegyes csoportokba rendeli a szabályzatokat, előfordulhat, hogy az eredmények nem a kívánt vagy várt érték.

  Például hozzárendelhet egy eszköz profilt a **minden felhasználó** felhasználói csoporthoz, de kizárja az **összes személyes** eszköz csoportot. Ebben a vegyes csoportházirend-hozzárendelésben **minden felhasználó** megkapja a szabályzatot. A kizárás nem vonatkozik.

  Ennek eredményeképpen a házirendek vegyes csoportokhoz való társítása nem ajánlott.

## <a name="next-steps"></a>További lépések

A profilok figyelésére, valamint a profilokat futtató eszközökre vonatkozó útmutatásért lásd: [eszközök profiljainak figyelése](device-profile-monitor.md) .
