---
title: Szerepköralapú hozzáférés-vezérlés (RBAC) Microsoft Intune
description: Megtudhatja, hogyan szabályozhatja, hogy kik hajthatnak végre műveleteket, és hogyan végezhet módosításokat a Microsoft Intuneban a RBAC használatával.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a03366037f9b0eced70f0375b3f4b39401e3141
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509807"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Szerepköralapú hozzáférés-vezérlés (RBAC) Microsoft Intune

A szerepköralapú hozzáférés-vezérlés (RBAC) segítségével felügyelheti, hogy ki férhet hozzá a szervezet erőforrásaihoz, és hogy mit tehetnek ezekkel az erőforrásokkal.  Ha [szerepköröket rendel](assign-role.md) az Intune-felhasználókhoz, korlátozhatja, hogy mit láthatnak és módosíthatnak. Minden szerepkör rendelkezik olyan engedélyekkel, amelyek meghatározzák, hogy az adott szerepkörrel rendelkező felhasználók hogyan férhetnek hozzá és módosíthatók a szervezeten belül.

A szerepkörök létrehozásához, szerkesztéséhez vagy hozzárendeléséhez a fióknak rendelkeznie kell a következő jogosultságok egyikével az Azure AD-ben:
- **Globális rendszergazda**
- **Intune szolgáltatás-rendszergazda** (más néven **Intune-rendszergazda**)

Az Intune RBAC kapcsolatos tanácsokért és javaslatokért tekintse meg az alábbi öt videót, amelyek példákat és bemutatókat mutatnak be: [1](https://www.youtube.com/watch?v=5deXLMLcnKY), [2](https://www.youtube.com/watch?v=38dnMBLuxbQ), [3](https://www.youtube.com/watch?v=6vqg9cAkMbY), [4](https://www.youtube.com/watch?v=5yOLajFFMHE), [5](https://www.youtube.com/watch?v=P5DDvsSF4Wk).

## <a name="roles"></a>Szerepkörök
A szerepkörök határozzák meg az adott szerepkörhöz rendelt felhasználók számára biztosított engedélyek készletét.
Használhatja a beépített és az egyéni szerepköröket is. A beépített szerepkörök néhány gyakori Intune-forgatókönyvet érintenek. [Saját egyéni szerepköröket is létrehozhat](create-custom-role.md) a szükséges engedélyek pontos készletével. Számos Azure Active Directory szerepkör rendelkezik engedéllyel az Intune-hoz.
Ha meg szeretne tekinteni egy szerepkört, válassza az **Intune** > **szerepkörök** > **minden szerepkör** lehetőséget, > válasszon egy szerepkört. A következő lapokat fogja látni:

- **Tulajdonságok**: a szerepkör neve, leírása, típusa, hozzárendelései és hatókör-címkéi. 
- **Engedélyek**: a nagy mennyiségű váltással határozza meg, hogy a szerepkör milyen engedélyekkel rendelkezik.
- **Hozzárendelések**: azon [szerepkör-hozzárendelések]( assign-role.md) listája, amelyek meghatározzák, hogy mely felhasználók férhetnek hozzá a felhasználókhoz vagy eszközökhöz. Egy szerepkör több hozzárendeléssel is rendelkezhet, és a felhasználók több hozzárendelésben is szerepelhetnek.

### <a name="built-in-roles"></a>Beépített szerepkörök
A csoportok számára további konfigurálás nélkül is hozzárendelhet beépített szerepköröket. Nem törölheti vagy szerkesztheti a beépített szerepkör nevét, leírását, típusát vagy engedélyeit.

- **Ügyfélszolgálat**: Távoli feladatokat hajt végre felhasználókon és eszközökön, valamint alkalmazásokat és szabályzatokat rendelhet hozzájuk.
- **Házirend-és profil-kezelő**: a megfelelőségi szabályzatot, a konfigurációs profilokat, az Apple-regisztrációt, a vállalati eszközök azonosítóit és a biztonsági alapterveket kezeli.
- **Csak olvasási jogosultságú operátor**: Megtekintheti a felhasználókra, regisztrációra, konfigurációra és alkalmazásokra vonatkozó információkat. Nem lehet módosítani az Intune-t.
- **Alkalmazáskezelő**: Kezeli a mobil- és felügyelt alkalmazásokat, olvashatja az eszközadatokat, és megtekintheti az eszközkonfigurációs profilokat.
- **Intune szerepkör-rendszergazda**: az egyéni Intune-szerepkörök kezelése és hozzárendelések hozzárendelése a beépített Intune-szerepkörökhöz. Ez az egyetlen Intune-szerepkör, amely engedélyeket rendelhet a rendszergazdákhoz.
- **Iskolai rendszergazda**: a Windows 10-es eszközök kezelése a [Intune for Educationban](../introduction-intune-education.md).

### <a name="custom-roles"></a>Egyéni szerepkörök
Egyéni engedélyekkel saját szerepköröket is létrehozhat. További információ az egyéni szerepkörökről: [Egyéni szerepkör létrehozása](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Intune-hozzáféréssel rendelkező szerepkörök Azure Active Directory
| Azure Active Directory szerepkör | Az összes Intune-érték | Intune-beli naplózási adatgyűjtés |
| --- | :---: | :---: |
| Globális rendszergazda | Olvasás/írás | Olvasás/írás |
| Intune-szolgáltatásadminisztrátor | Olvasás/írás | Olvasás/írás |
| Feltételes hozzáférésű rendszergazda | Nincsenek | Nincsenek |
| Biztonsági rendszergazda | Csak olvasható | Csak olvasható |
| Biztonsági operátor | Csak olvasható | Csak olvasható |
| Biztonsági olvasó | Csak olvasható | Csak olvasható |
| Megfelelőségi rendszergazda | Nincsenek | Csak olvasható |
| Megfelelőségi adatkezelő | Nincsenek | Csak olvasható |
| Globális olvasó | Csak olvasható | Csak olvasható |

> [!TIP]
> Az Intune három Azure AD-bővítményt is megjelenít: **felhasználók**, **csoportok**és **feltételes hozzáférés**, amelyek az Azure ad RBAC vannak szabályozva. A **Felhasználóifiók-adminisztrátori** szerepkör csak az Azure AD-felhasználói vagy -csoporttevékenységek végrehajtására jogosít fel, és nem biztosít teljes körű engedélyt az összes Intune-beli tevékenységhez. További információ: [RBAC az Azure ad-vel](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Klasszikus Intune-portálon létrehozott szerepkörök
Csak a „Teljes körű” engedéllyel rendelkező Intune-beli **szolgáltatás-rendszergazdákat** migrálja a rendszer a klasszikus Intune-portálról az Azure Portalbeli Intune-ba. Újra hozzá kell rendelnie az Intune **szolgáltatás-rendszergazdák** felhasználóit "csak olvasási" vagy "segélyszolgálat" hozzáféréssel a Azure Portal Intune-szerepkörökhöz, és el kell távolítani őket a klasszikus portálról.
> [!IMPORTANT]
> Előfordulhat, hogy meg kell őriznie az Intune szolgáltatás rendszergazdai hozzáférését a klasszikus portálon, ha a rendszergazdáknak még hozzá kell férniük a számítógépek Intune-nal való kezeléséhez.

## <a name="role-assignments"></a>Szerepkör-hozzárendelések
A szerepkör-hozzárendelések A következőket határozzák meg:

- a szerepkörhöz hozzárendelt felhasználók
- milyen erőforrásokat láthatnak
- milyen erőforrásokat módosíthatnak.

Egyéni és beépített szerepköröket is hozzárendelhet a felhasználókhoz. Intune-szerepkör hozzárendeléséhez a felhasználónak Intune-licenccel kell rendelkeznie.
A szerepkör-hozzárendelés megjelenítéséhez válassza az **Intune** > **szerepkörök**@no__t – 3**minden szerepkör** lehetőséget, > válasszon egy szerepkört > válasszon ki egy hozzárendelést. A következő lapokat fogja látni:

- **Tulajdonságok**: a hozzárendelés neve, leírása, szerepköre, tagjai, hatóköre és címkéje.
- **Tagok**: a felsorolt Azure-beli biztonsági csoportok minden felhasználója jogosult a hatókörben (csoportok) felsorolt felhasználók vagy eszközök kezelésére.
- **Hatókör (csoportok)** : ezekben az Azure biztonsági csoportokban lévő összes felhasználó/eszköz felügyelhető a tagok felhasználóinak.
- **[Hatókör (címkék)](scope-tags.md)** : a tagok felhasználói láthatják azokat az erőforrásokat, amelyeknek ugyanazok a hatóköri címkéi.

### <a name="multiple-role-assignments"></a>Több szerepkör-hozzárendelés
Ha egy felhasználó több szerepkör-hozzárendeléssel, engedélyekkel és hatókör-címkékkel rendelkezik, a szerepkör-hozzárendelések a következőképpen bővülnek a különböző objektumokra:

- Az engedélyek és a hatókör-címkék hozzárendelése csak az adott szerepkör hozzárendelési hatókörében (csoportok) lévő objektumokra (például szabályzatokra vagy alkalmazásokra) vonatkozik. Az engedélyek és a hatókör-címkék hozzárendelése nem vonatkozik más szerepkör-hozzárendelések objektumaira, kivéve, ha a másik hozzárendelés kifejezetten megadja őket.
- Más engedélyek (például a létrehozás, olvasás, frissítés, törlés) és a hatókör-címkék minden olyan objektumra érvényesek, amely azonos típusú (például az összes szabályzatot vagy az összes alkalmazást) érinti a felhasználó hozzárendeléseiben.
- A különböző típusú (például szabályzatok vagy alkalmazások) objektumok engedélyei és hatóköri címkéi nem vonatkoznak egymásra. Egy házirendhez tartozó olvasási engedély például nem ad olvasási engedélyt a felhasználó hozzárendeléseiben lévő alkalmazásokhoz.

## <a name="next-steps"></a>További lépések
- [Szerepkör társítása felhasználóhoz](assign-role.md)
- [Egyéni szerepkör létrehozása](create-custom-role.md)
