---
title: Eszközprofilok hozzárendelése az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az Azure Portal használatával rendelhet hozzá eszközprofilokat és szabályzatokat a felhasználókhoz és eszközökhöz. Megtudhatja, hogyan zárhat ki csoportokat Microsoft Intune-beli profil-hozzárendelésből.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344ffdfefd8b354c9d2ab31f2d08c2a25456f970
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730803"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Felhasználói és eszközprofilok hozzárendelése a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Létrehoz egy profilt, és tartalmazza a megadott beállításokat. A következő lépés a profil üzembe helyezése vagy "kiosztása" a Azure Active Directory (Azure AD) felhasználóhoz vagy eszköz csoporthoz. Ha hozzá van rendelve, a felhasználók és az eszközök megkapják a profilt, és a rendszer alkalmazza a megadott beállításokat.

Ebből a cikkből megtudhatja, hogyan rendelhet hozzá egy profilt, és tartalmaz néhány információt a hatókör-címkék használatáról a profilokban.

## <a name="assign-a-device-profile"></a>Eszközprofil hozzárendelése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** lehetőséget. Az összes profil megjelenik.
3. Válassza ki a profilt, amelyhez > **hozzárendeléseket**szeretne hozzárendelni.
4. Válassza a csoportok **belefoglalása** vagy a csoportok **kizárása** lehetőséget, majd válassza ki a csoportokat. A csoportok kiválasztásakor egy Azure AD-csoportot is választ. Több csoport kijelöléséhez tartsa lenyomva a **CTRL** billentyűt, és válassza ki a csoportokat.

    ![Képernyőkép profil hozzárendelésekor a csoportok belefoglalásához és kizárásához megadható beállításokról](./media/device-profile-assign/group-include-exclude.png)

5. **Mentse** a változtatásokat.

### <a name="evaluate-how-many-users-are-targeted"></a>Annak kiértékelése, hogy hány felhasználó van megcélozva

Ha hozzárendeli a profilt, azt is **kiértékelheti** , hogy hány felhasználót érint a rendszer. Ez a szolgáltatás kiszámítja a felhasználókat; nem számítja ki az eszközöket.

1. Az Intune-ban válassza az **eszköz konfigurációs** > **profilok**lehetőséget.
2. Válassza ki a profilt > **hozzárendelések** > **kiértékelése**. Egy üzenet azt mutatja, hogy a profil hány felhasználót céloz meg.

Ha a **kiértékelés** gomb szürkén jelenik meg, ellenőrizze, hogy a profil hozzá van-e rendelve egy vagy több csoporthoz.

## <a name="use-scope-tags-or-applicability-rules"></a>Hatókör-címkék vagy alkalmazhatósági szabályok használata

A profilok létrehozásakor vagy frissítésekor hozzáadhat hatókör-címkéket és alkalmazhatósági szabályokat is a profilhoz.

A **hatókör címkéi** lehetővé teszik a házirendek hozzárendelését és szűrését adott csoportokra, például az emberi erőforrásokra vagy az összes US-NC-alkalmazottakra. [A RBAC és a hatókör címkéi a terjesztéshez](../fundamentals/scope-tags.md) további információkat is használhatnak.

Windows 10-es eszközökön olyan **alkalmazhatósági szabályokat** adhat hozzá, hogy a profil csak egy adott operációsrendszer-verzióra vagy egy adott Windows-kiadásra vonatkozzon. Az [alkalmazhatósági szabályok](device-profile-create.md#applicability-rules) további információval rendelkeznek.

## <a name="exclude-groups-from-a-profile-assignment"></a>Csoportok kizárása profil hozzárendelésekor

Az Intune-beli eszközkonfigurációs profilok lehetővé teszik csoportok kizárását a szabályzat-hozzárendelésből.

Az Intune nem tekinti meg a felhasználók és az eszközök közötti csoportok kapcsolatait. A felhasználói csoportok és az erőforráscsoportok kizárása esetén előfordulhat, hogy nem kapja meg a várt eredményeket. A felhasználói csoport – felhasználó csoport és az eszközök csoport-eszköz csoportjának forgatókönyvei esetében a kizárás elsőbbséget élvez a felvételsel szemben.

Például hozzárendelhet egy eszköz profilt a **minden vállalati felhasználó** felhasználói csoporthoz, de kizárhatja a tagokat a **vezető felügyeleti munkatárs** felhasználói csoportban. Mivel mindkét csoport felhasználói csoport, a **vezető felügyeleti munkatárs** összes tagja ki van zárva a szabályzatból, még akkor is, ha az **összes vállalati felhasználó** tagja a csoportnak.

A Belefoglalás elsőbbséget élvez az olyan vegyes csoportok használatakor, mint például a felhasználói csoport – eszköz csoport vagy az eszközök csoport – felhasználó csoport.

Tegyük fel például, hogy az eszköz profilját hozzá szeretné rendelni a szervezet összes felhasználója számára, kivéve a kioszkos eszközöket. Belefoglalja a **Minden felhasználó** csoportot, de kizárja a **Minden eszköz** csoportot. Ebben az esetben az összes felhasználó és eszköze megkapja a szabályzatot, még akkor is, ha a felhasználó eszköze a **minden eszköz** csoportban van.

A kizárás csak a csoport közvetlen tagjait vizsgálja. Nem tartalmazza a felhasználóhoz társított eszközöket. A felhasználóval nem rendelkező eszközök azonban nem kapják meg a szabályzatot. Ez a viselkedés azért fordul elő, mert a felhasználók nélküli eszközök nem rendelkeznek kapcsolattal a **minden felhasználó** csoporttal.

A **Minden eszköz** csoport belefoglalása és a **Minden felhasználó** csoport kizárása esetén minden eszköz megkapja a szabályzatot. A cél ezúttal azoknak az eszközöknek a kizárása, amelyekhez a szabályzat szerint felhasználó van társítva. Ez azonban zárja ki az eszközöket, hiszen a kizárás funkció csak a közvetlen csoporttagokat hasonlítja össze.

## <a name="next-steps"></a>További lépések

A profilok figyelésére, valamint a profilokat futtató eszközökre vonatkozó útmutatásért lásd: [eszközök profiljainak figyelése](device-profile-monitor.md) .
