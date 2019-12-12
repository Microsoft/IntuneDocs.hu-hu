---
title: A használati feltételek beállítása a Microsoft Intune-ban
titleSuffix: ''
description: A felhasználók által az Intune Céges portálon látható használati feltételek beállítása.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fb5818609763753878fec7a84fd8c19eb154f88
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955439"
---
# <a name="terms-and-conditions-for-user-access"></a>Felhasználói hozzáférés használati feltételei

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune rendszergazdájaként megkövetelheti a felhasználóktól a cég feltételeinek elfogadását, mielőtt a Céges portált az alábbiakra használnák:
- eszközök regisztrálása,
- erőforrások, például a vállalati alkalmazások és az e-mailek elérése.

A használati feltételek konfigurálása nem kötelező.

Több használati feltételt hozhat létre, és azokat különböző csoportokhoz rendelheti hozzá, így például eltérő nyelveket támogathat.

A céges használati feltételeket kétféleképpen hozhatja létre:
- Az Intune-nal az ebben a cikkben leírtak szerint.
- a Azure Active Directory használati [feltételek funkciójának](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou) használatával

Ha szeretné megtudni, hogy melyik módszer a legmegfelelőbb, tekintse meg a [szervezet blogbejegyzésének megfelelő feltételek kiválasztását](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409)ismertető témakört. 

## <a name="create-terms-and-conditions"></a>Használati feltételek létrehozása
Az alábbi lépések végrehajtásával hozhat létre használati feltételeket. A megjelenítendő név és leírás adminisztrációs célt szolgál, míg a feltételek tulajdonságait a felhasználók láthatják a Céges portálon.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza a **bérlői felügyelet** > **használati**feltételek elemet.
2. Válassza a **Létrehozás** lehetőséget.
3. Az **alapok** lapon a következő információkat kell megadni:

   - **Name (név**): a Azure Portalban szereplő feltételek neve. A felhasználók nem látják ezt a nevet.
   - **Leírás**: További részletek, amelyek alapján könnyebben felismerhető az adott feltételkészlet az Azure Portalon.

    ![A feltételek és kikötések alapismeretek lapját bemutató Azure Portal képernyőképe](./media/terms-and-conditions-create/terms-basics-page.png)

4. A **tovább** gombra kattintva lépjen a **feltételek** lapra, és adja meg a következő információkat:

   - **Cím**: a felhasználóknak ez jelenik meg a Céges portálon az **Összegzés** fölött.
   - **Használati feltételek**: Azok a használati feltételek, amelyeket a felhasználók látnak, és amelyek elfogadása vagy elutasítása kötelező.
   - **Feltételek összefoglalása**: Ez a szöveg ismerteti, hogy mi történik, ha a felhasználók elfogadják a feltételeket. Például: „Az eszköz regisztrálásával Ön elfogadja a Contoso által meghatározott használati feltételeket. Folytatás előtt figyelmesen olvassa el a feltételeket.”

5. A **tovább** gombra kattintva nyissa meg a **hatókör címkék** lapot.

6. Válassza a **hatókör címkék kiválasztása**lehetőséget, válassza ki a feltételeket és kikötéseket hozzárendelni kívánt hatóköri címkéket, majd válassza a **kiválasztás**lehetőséget. 

7. A **tovább** gombra kattintva lépjen a **hozzárendelések** lapra, és válassza az alábbi lehetőségek egyikét a **hozzárendeléshez**:
    - **Minden felhasználó**: válassza ezt a lehetőséget a feltételek és kikötések minden felhasználóhoz való hozzárendeléséhez.
    - **Csoportok kiválasztása**: válassza ezt a lehetőséget, ha a feltételeket és kikötéseket az Ön által azonosított csoportokban mindenki számára szeretné hozzárendelni, **válassza a csoportok kiválasztása lehetőséget**.

8. Válassza a **következő** > **Létrehozás**elemet.

## <a name="see-how-terms-are-displayed-to-your-users"></a>A felhasználóknak megjelenő feltételek megtekintése
Az alábbi példában látható, hogyan jelenik meg a **Cím** és a **Feltételek összefoglalása** a felügyeleti konzolon és a Céges portálon.

![Képernyőkép: a Cím és a Feltételek összefoglalása a felügyeleti konzolon és a Céges portálon.](./media/terms-and-conditions-create/terms-summary-terms.png)

Az alábbi példában látható, hogyan jelennek meg a használati feltételek a felügyeleti konzolon és a Céges portálon.

![Képernyőkép: a használati feltételek a felügyeleti konzolon és a Céges portálon.](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>A használati feltételek figyelése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza a **bérlői felügyelet** > **használati**feltételek elemet.
2. A használati feltételek listájában válassza ki azokat a feltételeket, amelyeknél meg szeretné tekinteni az elfogadást, majd válassza az **Elfogadási jelentés** lehetőséget.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>A használati feltételek több változatának használata
Szerkesztheti a használati feltételeket, és felügyelheti verzióikat. Minden alkalommal, amikor lényeges módosításokat végez a használati feltételekben, el kell végeznie az alábbiakat:
- az alkalmazás verziószámának növelése
- az új feltételek és kikötések elfogadásának megkövetelése a felhasználóktól

Tartsa meg az aktuális verziószámot, ha például az elírásokat javítja vagy megváltoztatja a formázást.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza a **bérlői felügyelet** > **használati** feltételek > Válassza ki azokat a feltételeket és kikötéseket, amelyeket módosítani kíván > **tulajdonságai**között.

2. A **Tulajdonságok** panelen válassza a **Feltételek és kikötések** lehetőséget, majd szükség szerint módosítsa a **Cím**, a **Feltételek összefoglalása** és a **Feltételek és kikötések** szövegét. Ha a módosítások miatt a felhasználóknak újra el kell fogadniuk a feltételeket, válassza a **Kérje a felhasználóktól az újbóli elfogadást, és növelje a verziószámot a következőre** lehetőséget.

3. Válassza az **OK** > **Mentés** gombokat.

A használati feltételeket csak egyszer kell elfogadni, a több eszközzel bíró felhasználóknak tehát nem kell ezt megtenniük minden eszközön.
