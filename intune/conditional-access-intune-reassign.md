---
title: Feltételes hozzáférés migrálása Azure Portalra
titleSuffix: Microsoft Intune
description: Rendelje újra az Intune klasszikus portálján korábban létrehozott feltételes hozzáférési szabályzatokat a Azure Portalhoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36e7b8468e4ee9d1f6be71a82d18f066bd7568d4
ms.sourcegitcommit: 9110124a481160039d476cf0374a4fa0464a8509
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256200"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Feltételes hozzáférési szabályzatok ismételt társítása az Intune klasszikus portálján a Azure Portal

Az új Azure Portaltól kezdve a feltételes hozzáférés több szabályzatot is támogat az alkalmazások számára, valamint a testreszabhatóság érdekében. Ha korábban már létrehozott feltételes hozzáférési szabályzatokat a klasszikus Intune-portálon, áttelepítheti azokat a Azure Portalba. 

## <a name="before-you-begin"></a>Előkészületek

Ha készen áll a Azure Portalre való áttérésre, kövesse a jelen témakörben ismertetett lépéseket a korábban a klasszikus Intune-portálon létrehozott feltételes hozzáférési szabályzatok újbóli hozzárendeléséhez:

- Gyűjtse össze a korábban létrehozott feltételes hozzáférési szabályzatokat, hogy tudja, milyen beállításokat kell később újra társítania.

- Az ebben a témakörben leírt lépéseket követve újraalkothatja ezeket a szabályzatokat az Azure Portalon.

- Miután meggyőződött róla, hogy az új szabályzatok a várt módon működnek az Azure Portalon, tiltsa le a feltételes szabályzatokat az Intune klasszikus portálján.
<br /><br />
  - **Mielőtt** letiltotta a feltételes hozzáférési szabályzatokat az Intune klasszikus portálján, tervezze meg, hogyan helyezheti át a felhasználókat az új szabályzatba. Két módszer létezik:
<br /><br />
    - **Használhatja ugyanazt a belefoglaló csoportot az Azure Portalon létrehozott szabályzatok alkalmazására úgy, hogy létrehoz egy új kizárt csoportot az Intune klasszikus portál által alkalmazott szabályzatokhoz**.
      - A felhasználók egy részét fokozatosan helyezze át a klasszikus portálon megadott kizárt csoportba. Ez megakadályozza az Intune klasszikus portálja által meghatározott szabályzatok alkalmazását. Az ugyanazon felhasználói csoporthoz az Azure Portalon létrehozott szabályzatok az Intune klasszikus portálon alkalmazottak mellett érvényesülnek. 
<br /><br />
    - **Hozzon létre egy új csoportot, amely a feltételes hozzáférési házirendeket célozza meg a Azure Portalban**. Ha ezt a módszert választja, akkor a következőket kell tennie:
      - Fokozatosan távolítsa el a felhasználókat azokból a biztonsági csoportokból, amelyek feltételes hozzáférési szabályzatokkal rendelkeznek a klasszikus Intune-portálon.
      - Miután meggyőződött róla, hogy az új szabályzat ezen felhasználók esetében működik, letilthatja a szabályzatot az Intune klasszikus portálján. 
<br /><br />
- Ha a feltételes hozzáférési szabályzat az Exchange ActiveSync (EAS) használatára van konfigurálva az Intune klasszikus portálján, tekintse meg a [jelen témakör utasításait](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) az **EAS feltételes hozzáférési házirend beállításainak újbóli hozzárendeléséhez a Azure Portal**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Az eszközön alapuló feltételes hozzáférési szabályzatok ellenőrzése a klasszikus Intune-portálon

1. Jelentkezzen be hitelesítő adataival az [Intune klasszikus portálon](https://manage.microsoft.com).

2. Válassza a bal oldali menü **Szabályzat** pontját.

3. Válassza a **feltételes hozzáférés**lehetőséget, majd válassza ki a Microsoft Cloud Service-t (például Exchange Online vagy SharePoint Online), amelyhez feltételes hozzáférési szabályzatot hozott létre.

4. Jegyezze fel a feltételes hozzáférési beállításokat, és ezeket a feltételes hozzáférési szabályzatokat a Azure Portalban való létrehozásakor tekintse át.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Az alkalmazás és az eszközön alapuló feltételes hozzáférési szabályzatok együtt működnek

Az Azure Portal **Intune App Protection** paneljén a rendszergazdák alkalmazásalapú feltételes szabályokat állíthatnak be, így csak az Intune alkalmazásvédelmi szabályzatait támogató alkalmazások férhetnek hozzá a vállalati erőforrásokhoz. Megadhatja, hogy az alkalmazás-alapú feltételes hozzáférési szabályzatok átfedésben legyenek az eszközökön alapuló feltételes hozzáférési szabályzatok használatával. Az eszközalapú és alkalmazásalapú feltételes szabályzatokat kombinálhatja (logikai ÉS) vagy választási lehetőséget kínálhat fel (logikai VAGY). Ha a feltételes hozzáférési szabályzat követelményei a következők:

- Követelmény a megfelelő eszköz **ÉS** az engedélyezett alkalmazás használata.
  - A feltételes hozzáférési szabályzatot a [Azure Active Directory feltételes hozzáférés](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) panel és a [Intune app Protection](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)panel használatával kell beállítania.
<br /><br />
- Követelmény a megfelelő eszköz **VAGY** az engedélyezett alkalmazás használata.
  - A feltételes hozzáférési szabályzatot a [klasszikus Intune-portál](https://manage.microsoft.com) és a [Intune app Protection](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)panel használatával kell beállítania.

> [!TIP] 
> Ezt a témakört az Intune klasszikus portál és az Azure Portal felhasználói felületét összehasonlító képernyőképek illusztrálják.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Intune-alapú feltételes hozzáférési szabályzatok ismételt társítása

1. Lépjen a [Azure Portal feltételes hozzáférés](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)elemre, és jelentkezzen be a hitelesítő adataival.

2. Válassza az **Új szabályzat** lehetőséget.

3. Adja meg a szabályzat nevét.

4. A **hozzárendelések szakaszban**válassza a **felhasználók és csoportok** lehetőséget az új feltételes hozzáférési szabályzat megcélzásához.

    ![Az Intune és az Azure portálok közötti felhasználói csoportok felhasználói FELÜLETét összehasonlító rendszerkép](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > Az Azure Portalon és a klasszikus portálon végzett kiválasztásnak meg kell egyeznie. Például ha a Minden felhasználó lehetőséget jelölte meg az Intune klasszikus portálján, akkor az Azure Portalon is a **Minden felhasználó** lehetőséget válassza. Ezen kívül, ha használta a **Kivételt képző csoportok** lehetőséget az Intune klasszikus portálon, akkor az ott kijelölt csoportokat ki kell zárnia az Azure Portalon is.

5. A csoport kijelölése után kattintson a **Kiválaszt**, majd a **Kész** gombra.

6. A **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.

7. A **Felhőalkalmazások** panelen válassza az **Alkalmazások kijelölése** lehetőséget.

8. Válassza ki azt az alkalmazást, amelyre alkalmazni kívánja az új feltételes hozzáférési szabályzatot, majd kattintson a **kiválasztás**elemre.

9. Kattintson a **Done** (Kész) gombra.

    ![A Felhőbeli alkalmazások KEZELŐFELÜLETének összehasonlítása az Intune és az Azure Portalon](./media/reassign-ca-3.png)

    > [!TIP] 
    > Ha több alkalmazásra ugyanaz a szabályzat vonatkozik, akkor érdemes lehet egyetlen szabályzatba összevonni őket az Azure Portalon.

10. A **Hozzárendelések** szakaszban válassza a **Feltételek** lehetőséget.

11. A **Feltételek** panelen az **Eszközplatformok** alatt válassza ki az alkalmazható eszközplatformokat.

12. Ha végzett az eszközplatformok kijelölésével, kattintson kétszer a **Kész** gombra.

    ![Az eszköz platformjának felhasználói felületét az Intune-ból és az Azure portálról összehasonlító rendszerkép](./media/reassign-ca-4.png)

    > [!TIP] 
    > Ha egyedi platformokat jelölt ki az Intune klasszikus portálon, akkor az Azure Portalon is válassza ki az egyes platformokat.

    > [!NOTE] 
    > A tartományhoz való csatlakozás és a Windows megfelelőség beállításait később is megadhatja.

13. A **Hozzárendelések** szakaszban válassza a **Feltételek** lehetőséget.

14. A **Feltételek** panelen az **Ügyfélalkalmazások** alatt válassza ki a megfelelő ügyfélalkalmazást.

15. Ha végzett az ügyfélalkalmazás kijelölésével, kattintson kétszer a **Kész** gombra.

    ![Az Intune és az Azure portálok közötti ügyfélalkalmazások felhasználói felületét összehasonlító rendszerkép](./media/reassign-ca-6.png)

16. Ha kijelölte a böngészőbeállításokat az Intune klasszikus portálon, akkor az Azure Portalon jelölje ki a **Böngésző** és a **Mobilalkalmazások és asztali ügyfelek** lehetőséget is. Ha nem jelölte ki a böngészőbeállításokat az Intune klasszikus portálon, akkor csak a **Mobilalkalmazások és asztali ügyfelek** lehetőséget jelölje meg. 

17. A **Hozzáférés-vezérlés** területen válassza az **Engedélyezés** elemet.

18. A **Hozzáférési engedély feltételei** alatt jelölje ki a **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget, majd kattintson a **Kiválaszt** gombra.

19. Ha van tartományba léptetett Windows-eszközöket megkövetelő szabályzata, és engedélyezi az Intune-ban regisztrált és megfelelő Windows-eszközöket is, akkor válassza a **Tartományba léptetett eszköz megkövetelése** és a **Megfelelőként megjelölt eszköz megkövetelése** feltételt, valamint **A kijelölt feltételek egyikének megkövetelése** lehetőséget.

20. Ha nem engedélyezi az Intune-ban regisztrált és megfelelő Windows-eszközöket, zárja ki a Windows-szabályzatot a jelenlegiből. Ezután hozzon létre külön szabályzatot az **Eszközplatform** értékét **Windows**ra állítva, belefoglalva a fentiek szerint beállított többi feltételt, és válassza a **Tartományba léptetett eszköz megkövetelése** feltételt a **Hozzáférési engedély feltételei** alatt.

21. Az **új** feltételes hozzáférési szabályzat panelen kapcsolja be a **szabályzat engedélyezése** kapcsolót, majd kattintson a **Létrehozás**gombra.

    ![Feltételes hozzáférési szabályzat engedélyezése felhasználói felületének összehasonlítása az Intune és az Azure között](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Intune-eszközökön alapuló feltételes hozzáférési szabályzatok ismételt társítása EAS-ügyfelek számára

Ha a klasszikus Intune-portálon az Exchange Online-szabályzat részeként konfigurálta az Exchange ActiveSync-beállításokat, létre kell hoznia egy második feltételes hozzáférési szabályzatot a Azure Portal.

1. Lépjen a [Azure Portal feltételes hozzáférés](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)elemre, és jelentkezzen be a hitelesítő adataival.

2. Válassza az **Új szabályzat** lehetőséget.

3. Adja meg a szabályzat nevét.

4. A **hozzárendelések** szakaszban válassza a **felhasználók és csoportok** lehetőséget az új feltételes hozzáférési szabályzat megcélzásához.

    ![Az Azure-és az Intune-portálok felhasználói csoport felhasználói felületének összehasonlítását bemutató kép](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Az Azure Portalon és az Intune-portálon végzett kiválasztásnak meg kell egyeznie. Például ha a Minden felhasználó lehetőséget jelölte meg az Intune klasszikus portálján, akkor az Azure Portalon is a **Minden felhasználó** lehetőséget válassza. Ezen kívül, ha használta a **Kivételt képző csoportok** lehetőséget az Intune klasszikus portálon, akkor az ott kijelölt csoportokat ki kell zárnia az Azure Portalon is.

5. A csoport kijelölése után kattintson a **Kiválaszt**, majd a **Kész** gombra.

6. A **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.

7. A **Felhőalkalmazások** panelen kattintson a **Kijelölt alkalmazások**, majd az **Exchange Online** elemre. Kattintson a **Kiválaszt**, majd a **Kész** gombra.

    ![Felhőbeli alkalmazások KEZELŐFELÜLETének összehasonlítása az Intune és az Azure Portalon](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > Az EAS-ügyfelek feltételes hozzáférési szabályzatai nem vonatkozhatnak másik felhőalkalmazásra.

8. A **Feltételek** panelen az **Ügyfélalkalmazások** alatt válassza ki a megfelelő ügyfélalkalmazást. Ha az Intune által nem támogatott ügyfelek kitiltása mellett döntött, akkor válassza a **Szabályzat alkalmazása csak a támogatott platformokon** lehetőséget.

    ![Az Azure-és az Intune-portálon az ügyfélalkalmazások KEZELŐFELÜLETének összehasonlítását bemutató kép](./media/reassign-ca-15.png)

9. Ha végzett az ügyfélalkalmazás kijelölésével, kattintson kétszer a **Kész** gombra.

10. A **Hozzáférés-vezérlés** területen válassza az **Engedélyezés** elemet.

11. A **Hozzáférési engedély feltételei** alatt jelölje ki a **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget, majd kattintson a **Kiválaszt** gombra.

    ![Az Intune és az Azure portálok közötti hozzáférési felhasználói felületet összehasonlító rendszerkép](./media/reassign-ca-16.png)

12. Az **új** feltételes hozzáférési szabályzat panelen kapcsolja be a **szabályzat engedélyezése** kapcsolót, majd kattintson a **Létrehozás**gombra.

    ![Feltételes hozzáférési szabályzat engedélyezése felhasználói felületének összehasonlítása az Intune és az Azure között](./media/reassign-ca-17.png)

> [!NOTE]
> Ha konfigurálja az **Eszközplatformokat**, a szabályzat mentése sikertelen lesz, és a „Szabályzat konfigurálása nem támogatott” üzenetet kapja. Az Exchange ActiveSync nem tudja azonosítani a csatlakozó eszköz által használt platformot. Az egyes eszközplatformok konfigurálása ezért nem támogatott az Exchange ActiveSync-eszközök szabályzatainak létrehozásakor.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Feltételes hozzáférési szabályzatok letiltása a klasszikus Intune-portálon

Miután hozzárendelte a feltételes hozzáférési szabályzatokat a Azure Portal, fontos, hogy fokozatosan tiltsa le a korábban a klasszikus Intune-portálon létrehozott feltételes hozzáférési szabályzatokat. Emellett előfordulhat, hogy ugyanazt a biztonsági csoportot kell használnia a Azure Portalban létrehozott feltételes hozzáférési szabályzatok alkalmazásához.

> [!NOTE]
> Mielőtt letiltotta a feltételes hozzáférési szabályzatokat a klasszikus Intune-portálon, tekintse meg a jelen témakör elején, a [Kezdés előtt](#before-you-begin) című szakaszt.

### <a name="to-disable-the-conditional-access-policies"></a>A feltételes hozzáférési szabályzatok letiltása

Mivel a MDM el lett távolítva a klasszikus Intune-portálról, a következő hivatkozás található a klasszikus szabályzatok megtekintéséhez/letiltásához:

https://portal.azure.com/?microsoft_aad_iam_classicPolicyDontHide=true#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/ClassicPolicies

## <a name="see-also"></a>Lásd még:

- [A feltételes hozzáférés használatának gyakori módjai az Intune-nal](conditional-access-intune-common-ways-use.md)
- [alkalmazás-alapú feltételes hozzáférés az Intune-nal](app-based-conditional-access-intune.md)
- [Feltételes hozzáférés az Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
