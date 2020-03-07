---
title: Eszközprofilok hozzárendelése az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: A Microsoft Endpoint Manager felügyeleti központjának használatával eszközöket és szabályzatokat rendelhet hozzá a felhasználókhoz és az eszközökhöz. Megtudhatja, hogyan zárhat ki csoportokat Microsoft Intune-beli profil-hozzárendelésből.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: c6678c3fbc247ac0595775c0ccc72c7bdb9c55e1
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369407"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Felhasználói és eszközprofilok hozzárendelése a Microsoft Intune-ban

Létrehoz egy profilt, és tartalmazza a megadott beállításokat. A következő lépés a profil üzembe helyezése vagy "kiosztása" a Azure Active Directory (Azure AD) felhasználóhoz vagy eszköz csoporthoz. Ha hozzá van rendelve, a felhasználók és az eszközök megkapják a profilt, és a rendszer alkalmazza a megadott beállításokat.

Ebből a cikkből megtudhatja, hogyan rendelhet hozzá egy profilt, és tartalmaz néhány információt a hatókör-címkék használatáról a profilokban.

> [!NOTE]  
> Ha egy profil el lett távolítva vagy már nincs hozzárendelve egy eszközhöz, a profil beállításaitól függően különböző dolgok is megtörténhetnek. A beállítások a kriptográfiai szolgáltatókon alapulnak, és minden CSP másképp kezeli a profil eltávolítását. Előfordulhat például, hogy egy beállítás megtartja a meglévő értéket, és nem állítja vissza az alapértelmezett értéket. A viselkedést az operációs rendszer minden CSP vezérli. A Windows-kriptográfiai szolgáltatók listáját a következő témakörben tekintheti meg: [Configuration Service Provider (CSP) referenciája](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).
>
> Ha másik értékre szeretné módosítani a beállításokat, hozzon létre egy új profilt, konfigurálja a beállítást a **nincs konfigurálva**értékre, és rendelje hozzá a profilt. Az eszközre való alkalmazása után a felhasználóknak vezérlővel kell megváltoztatniuk a beállítást a kívánt értékre.
>
> A beállítások konfigurálásakor javasoljuk, hogy egy kísérleti csoportba telepítsen. További információk az Intune bevezetéséről: bevezetési [terv létrehozása](../fundamentals/planning-guide-rollout-plan.md).

## <a name="before-you-begin"></a>Előkészületek

Ellenőrizze, hogy rendelkezik-e a megfelelő szerepkörrel a profilok hozzárendeléséhez. További információ: [szerepköralapú hozzáférés-vezérlés (RBAC) Microsoft Intunesal](../fundamentals/role-based-access-control.md).

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

A **hatókör címkéi** lehetővé teszik a profilok adott csoportokra való szűrését, például `US-NC IT Team` vagy `JohnGlenn_ITDepartment`. [A RBAC és a hatókör címkéi a terjesztéshez](../fundamentals/scope-tags.md) további információkat is használhatnak.

Windows 10-es eszközökön olyan **alkalmazhatósági szabályokat** adhat hozzá, hogy a profil csak egy adott operációsrendszer-verzióra vagy egy adott Windows-kiadásra vonatkozzon. Az [alkalmazhatósági szabályok](device-profile-create.md#applicability-rules) további információval rendelkeznek.

## <a name="user-groups-vs-device-groups"></a>Felhasználói csoportok és eszközök csoportjai

Sok felhasználó kérdezi, hogy mikor kell felhasználói csoportokat használni, és mikor kell használni az eszközök csoportjait. A válasz a céltól függ. Íme néhány útmutató az első lépésekhez.

### <a name="device-groups"></a>Eszközcsoportok

Ha egy eszközön szeretné alkalmazni a beállításokat, függetlenül attól, hogy ki jelentkezett be, majd rendelje hozzá a profilokat az eszközök csoportjához. Az eszközök csoportjaira alkalmazott beállítások mindig az eszközön mennek, nem a felhasználó.

Például:

- Az eszközcsoport olyan eszközök felügyeletéhez hasznos, amelyek nem rendelkeznek dedikált felhasználóval. Például vannak olyan eszközök, amelyek a jegyek, a beolvasási leltár, a kihelyezett munkavégzők megosztva vannak, egy adott raktárhoz vannak rendelve, és így tovább. Helyezze ezeket az eszközöket egy eszköz csoportba, és rendelje hozzá a profilokat az eszközök csoportjához.

- Létre kell hoznia egy [eszköz belső vezérlőprogram-konfigurációs felületének (DFCI) Intune-profilját](device-firmware-configuration-interface-windows.md) , amely frissíti a beállításokat a BIOS-ban. Ezt a profilt például úgy állíthatja be, hogy letiltsa az eszköz kameráját, vagy zárolja a rendszerindítási beállításokat annak megakadályozása érdekében, hogy a felhasználók egy másik operációs rendszert indítsanak. Ez a profil jó példa az eszközök csoportjához való hozzárendelésre.

- Bizonyos Windows-eszközökön mindig a Microsoft Edge bizonyos beállításait szeretné vezérelni, függetlenül attól, hogy ki használja az eszközt. Például letilthatja az összes letöltést, korlátozhatja az összes cookie-t az aktuális böngészési munkamenetre, és törölheti a böngészési előzményeket. Ebben a forgatókönyvben ezeket az adott Windows-eszközöket egy eszközök csoportba helyezi. Ezután hozzon létre egy [felügyeleti sablont az Intune-ban](administrative-templates-windows.md), adja hozzá ezeket az eszközbeállítások, majd rendelje hozzá ezt a profilt az eszközök csoporthoz.

Ha szeretne összefoglalni, akkor használja az erőforráscsoportok használatát, ha nem érdekli, hogy ki jelentkezett be az eszközön, vagy ha valaki bejelentkezett. Azt szeretné, hogy a beállítások mindig az eszközön legyenek.

### <a name="user-groups"></a>Felhasználói csoportok

A felhasználói csoportokra alkalmazott Profilbeállítások mindig a felhasználóval mennek át, és a felhasználó a sok eszközre való bejelentkezéskor. Normális, hogy a felhasználóknak sok eszközük van, például a Surface Pro for Work és egy személyes iOS/iPadOS-eszköz. Emellett normális, hogy valaki hozzáfér az e-mailekhez és más szervezeti erőforrásokhoz az eszközökről.

Például:

- Egy ügyfélszolgálati ikont szeretne elhelyezni az összes felhasználó számára az összes eszközön. Ebben a forgatókönyvben ezeket a felhasználókat egy felhasználói csoportba helyezheti, és az ügyfélszolgálat ikonjának profilját hozzárendelheti ehhez a felhasználói csoporthoz.
- A felhasználók új szervezet által birtokolt eszközt kapnak. A felhasználó tartományi fiókkal jelentkezik be az eszközre. Az eszköz automatikusan regisztrálva van az Azure AD-ben, és automatikusan az Intune kezeli. Ez a profil jó példa a felhasználók csoportjához való hozzárendelésre.
- Amikor egy felhasználó bejelentkezik egy eszközre, az alkalmazások, például a OneDrive vagy az Office funkcióit szeretné vezérelni. Ebben a forgatókönyvben rendelje hozzá a OneDrive vagy az Office-profil beállításait egy felhasználói csoporthoz.

  Például letilthatja a nem megbízható ActiveX-vezérlőket az Office-alkalmazásokban. Létrehozhat egy [felügyeleti sablont az Intune-ban](administrative-templates-windows.md), megadhatja ezt a beállítást, majd hozzárendelheti a profilt egy felhasználói csoporthoz.

Az összegzéshez használjon felhasználói csoportokat, ha azt szeretné, hogy a beállítások és szabályok mindig a felhasználóval lépjenek fel, függetlenül attól, hogy melyik eszközt használják.

## <a name="exclude-groups-from-a-profile-assignment"></a>Csoportok kizárása profil hozzárendelésekor

Az Intune-eszköz konfigurációs profiljai lehetővé teszik csoportok hozzáadását és kizárását a profil-hozzárendelésből.

Ajánlott eljárásként hozzon létre és rendeljen hozzá profilokat kifejezetten a felhasználói csoportokhoz. És hozzon létre és rendeljen hozzá különböző profilokat kifejezetten az eszközök csoportjaihoz. A csoportokkal kapcsolatos további információkért lásd: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](../fundamentals/groups-add.md).

A profilok kiosztásakor használja a következő táblázatot a csoportok belefoglalása és kizárása esetén. A pipa azt jelenti, hogy a hozzárendelés támogatott:

![A támogatott beállítások közé tartoznak a profil-hozzárendelésből származó csoportok vagy kizárások](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Alapismeretek

- A kizárás elsőbbséget élvez a következő azonos csoport típusú forgatókönyvek belefoglalásakor:

  - Felhasználói csoportok belefoglalása és felhasználói csoportok kizárása
  - Eszközcsoport-csoportokkal együtt

  Például hozzárendelhet egy eszköz profilt a **minden vállalati felhasználó** felhasználói csoporthoz, de kizárhatja a tagokat a **vezető felügyeleti munkatárs** felhasználói csoportban. Mivel mindkét csoport felhasználói csoport, az **összes vállalati felhasználó** , kivéve a **vezető felügyeleti személyzetet** , megkapja a profilt.

- Az Intune nem értékeli ki a felhasználók és az eszközök közötti csoportok kapcsolatait. Ha vegyes csoportokba rendeli a profilokat, előfordulhat, hogy az eredmények nem a kívánt vagy várt érték.

  Például hozzárendelhet egy eszköz profilt a **minden felhasználó** felhasználói csoporthoz, de kizárja az **összes személyes** eszköz csoportot. Ebben a vegyes csoportbeli profil-hozzárendelésben **minden felhasználó** megkapja a profilt. A kizárás nem vonatkozik.

  Ennek eredményeképpen a profilok vegyes csoportokba való társítása nem ajánlott.

## <a name="next-steps"></a>További lépések

A profilok figyelésére, valamint a profilokat futtató eszközökre vonatkozó útmutatásért lásd: [eszközök profiljainak figyelése](device-profile-monitor.md) .
