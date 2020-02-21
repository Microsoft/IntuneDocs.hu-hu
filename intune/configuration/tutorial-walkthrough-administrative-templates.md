---
title: Útmutató – felügyeleti sablon létrehozása a Microsoft Intuneban – Azure | Microsoft Docs
description: Ez az oktatóanyag vagy útmutató a Microsoft Intune segítségével konfigurálja az Office, a Windows és a Microsoft Edge ADMX-sablonokat Windows 10 és újabb rendszerű eszközökön.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a96f291203e1513ab89196b26a7802856f90e048
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511233"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>Oktatóanyag: a Windows 10 rendszerű eszközökön a felhő használatával konfigurálja a csoportházirendet az ADMX-sablonokkal és Microsoft Intune

> [!NOTE]
> Ez az oktatóanyag a Microsoft Ignite technikai workshopján lett létrehozva. Több előfeltételt is tartalmaz, mint a szokásos oktatóanyagok, mivel összehasonlítja az ADMX-szabályzatokat az Intune-ban és a helyszínen.

Csoportházirend felügyeleti sablonok, más néven ADMX-sablonok, a Windows 10-es eszközökön, beleértve a számítógépeket is konfigurálható beállításokat tartalmaznak. Az ADMX-sablon beállításait különböző szolgáltatások érhetik el. Ezeket a beállításokat a mobileszköz-felügyeleti (MDM) szolgáltatók használják, beleértve a Microsoft Intune. Bekapcsolhatja például a PowerPointban megjelenő tervezési ötleteket, megadhat egy kezdőlapot a Microsoft Edge-ben, letilthatja az ActiveX-vezérlőket az Internet Explorerben.

Az ADMX-sablonok a következő szolgáltatásokhoz érhetők el:

- **Microsoft Edge**: Letöltés a [Microsoft Edge Policy-fájlban](https://www.microsoftedgeinsider.com/en-us/enterprise).
- **Office**: Letöltés az [Office 365 ProPlus, Office 2019 és Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).
- **Windows**: beépített a Windows 10 operációs rendszerre.

Az ADMX-házirendekkel kapcsolatos további információkért lásd: az [ADMX-alapú szabályzatok ismertetése](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies).

Microsoft Intune ezek a sablonok az Intune szolgáltatásba épülnek, és **Felügyeleti sablonok** profiljaiként érhetők el. Ebben a profilban konfigurálhatja a felvenni kívánt beállításokat, majd "hozzárendelheti" ezt a profilt az eszközökhöz.

Az oktatóanyag során az alábbi lépéseket fogja végrehajtani:

> [!div class="checklist"]
> * Ismerkedjen meg a [Microsoft Endpoint Manager felügyeleti központjával](https://go.microsoft.com/fwlink/?linkid=2109431).
> * Hozzon létre felhasználói csoportokat, és hozzon létre eszközöket.
> * Hasonlítsa össze az Intune beállításait a helyszíni ADMX-beállításokkal.
> * Hozzon létre különböző felügyeleti sablonokat, és konfigurálja azokat a beállításokat, amelyek a különböző csoportokat célozzák meg.

A labor végére elsajátíthatja az Intune és a Microsoft 365 használatának első lépéseit a felhasználók felügyeletéhez és a felügyeleti sablonok üzembe helyezéséhez.

Ez a funkció az alábbiakra vonatkozik:

- Windows 10 1703-es és újabb verzió

## <a name="prerequisites"></a>Előfeltételek

- Egy Microsoft 365 E3 vagy E5 előfizetés, amely tartalmazza az Intune és a Azure Active Directory (AD) Premiumot. Ha nem rendelkezik E3 vagy E5 előfizetéssel, [próbálja ki ingyenesen](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide).

  A különböző Microsoft 365-licencekkel kapcsolatos további információkért lásd: [a vállalat átalakítása Microsoft 365sal](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).

- A Microsoft Intune **INTUNE Mdm-szolgáltatóként**van konfigurálva. További információt [a mobileszköz-kezelő szolgáltató beállítása](../fundamentals/mdm-authority-set.md)című témakörben talál.

  > [!div class="mx-imgBorder"]
  > ![a MDM-szolgáltatót úgy állítsa be, hogy Microsoft Intune a bérlői állapotában](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- Helyszíni Active Directory tartományvezérlőn (DC):

  1. Másolja a következő Office-és Microsoft Edge-sablonokat a [központi tárolóba (SYSVOL mappába)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra):

      - [Office felügyeleti sablonok](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Microsoft Edge felügyeleti sablonok > házirend fájl](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. Hozzon létre egy csoportházirendet a sablonok egy Windows 10 Enterprise Administrator rendszerű számítógépre való leküldéséhez a tartományvezérlővel megegyező tartományban. Ebben az oktatóanyagban:

      - Az ezekkel a sablonokkal létrehozott csoportházirend neve **OfficeandEdge**. Ezt a nevet fogja látni a lemezképekben.
      - Az általunk használt Windows 10 Enterprise Administrator-számítógépet a **rendszergazda számítógépnek**nevezzük.

      Egyes szervezeteknél a tartományi rendszergazdáknak két fiókja van – egy tipikus tartományi munkahelyi fiókkal és egy másik tartományi rendszergazdai fiókkal, amely csak tartományi rendszergazdai feladatokhoz, például csoportházirendekhez használható.

      Ennek a **felügyeleti számítógépnek** a célja, hogy a rendszergazdák a tartományi rendszergazdai fiókjával jelentkezzenek be, és a csoportházirend kezelésére tervezett hozzáférési eszközöket használják.

- Ezen a **rendszergazdai számítógépen**:

  - Jelentkezzen be egy tartományi rendszergazdai fiókkal.

  - Telepítse az **RSAT: csoportházirend felügyeleti eszközöket**:

    1. Nyissa meg a **Settings** App > **apps** > **választható funkciók** > **Hozzáadás funkciót**.
    2. Válassza az **RSAT: csoportházirend felügyeleti eszközök** > **telepítés**lehetőséget.

        Várjon, amíg a Windows telepíti a szolgáltatást. Ha elkészült, a rendszer végül a **Windows felügyeleti eszközök** alkalmazásban jeleníti meg.

        > [!div class="mx-imgBorder"]
        > ![a Windows felügyeleti eszközök alkalmazásait, beleértve a Csoportházirend Management alkalmazást](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - Győződjön meg arról, hogy van internet-hozzáférése és rendszergazdai jogosultsága a Microsoft 365-előfizetéshez, amely tartalmazza a Endpoint Manager felügyeleti központot.

## <a name="open-the-endpoint-manager-admin-center"></a>A Endpoint Manager felügyeleti központ megnyitása

1. Nyisson meg egy Chromium webböngészőt, például a Microsoft Edge 77-es vagy újabb verzióját.
2. Nyissa meg a [Microsoft Endpoint Manager felügyeleti központját](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com). Jelentkezzen be a következő fiókkal:

    **Felhasználó**: adja meg a Microsoft 365 bérlői előfizetés rendszergazdai fiókját.  
    **Password (jelszó**): adja meg a jelszavát.

Ez a felügyeleti központ az eszközök felügyeletére koncentrál, és tartalmazza az Azure-szolgáltatásokat, például az Azure AD-t és az Intune-t. Előfordulhat, hogy nem látja a **Azure Active Directory** és az **Intune** arculatát, de ezeket használja.

A Endpoint Manager felügyeleti központot a [Microsoft 365 felügyeleti központból](https://admin.microsoft.com)is megnyithatja:

1. Lépjen [https://admin.microsoft.com](https://admin.microsoft.com).
2. Jelentkezzen be a Microsoft 365 bérlői előfizetés rendszergazdai fiókjával.
3. A **felügyeleti központok**területen válassza **az összes felügyeleti központ** > **Endpoint Management**lehetőséget. Megnyílik a Endpoint Manager felügyeleti központ.

    > [!div class="mx-imgBorder"]
    > ![tekintse meg az összes felügyeleti központot a Microsoft 365 felügyeleti központban](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>Csoportok létrehozása és felhasználók hozzáadása

A helyszíni házirendek a LSDOU sorrend-helyi, hely, tartomány és szervezeti egység (OU) szerint lesznek alkalmazva. Ebben a hierarchiában a szervezeti házirendek felülírják a helyi házirendeket, a tartományi házirendeket felülírják a hely házirendjeit és így tovább.

Az Intune-ban a szabályzatok az Ön által létrehozott felhasználókra és csoportokra vonatkoznak. Nincs hierarchia. Ha két házirend ugyanazt a beállítást frissíti, akkor a beállítás ütközésként jelenik meg. Ha két megfelelőségi szabályzat ütközik, akkor a legszigorúbb szabályzat érvényes. Ha két konfigurációs profil ütközik, akkor a beállítás nincs alkalmazva. További információ: [általános kérdések, problémák és megoldások az eszközök házirendjeivel és profiljaival](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied).

A következő lépésekben hozzon létre biztonsági csoportokat, és vegyen fel felhasználókat a csoportokhoz. Több csoporthoz is hozzáadhat felhasználókat. Előfordulhat például, hogy egy felhasználó több eszközt is tartalmaz, például a Surface Pro for Work szolgáltatást és egy androidos mobileszköz-eszközt a személyes használatra. Emellett az is normális, hogy egy személy több eszközről is hozzáférhessen a szervezeti erőforrásokhoz.

1. A Endpoint Manager felügyeleti központban válassza a **csoportok** > **új csoport**lehetőséget.

2. Adja meg a következő beállításokat:

    - **Csoport típusa**: válassza a **Biztonság**elemet.
    - **Csoport neve**: adja meg **az összes Windows 10 tanuló eszközét**.
    - **Tagság típusa**: válassza a **hozzárendelés**lehetőséget.

3. Válasszon ki **tagokat**, és adjon hozzá néhány eszközt.

    Az eszközök hozzáadása nem kötelező. A cél a csoportok létrehozásának gyakorlata, és az eszközök hozzáadásának ismerete. Ha éles környezetben használja ezt az oktatóanyagot, vegye figyelembe, hogy mit csinál.

4. A módosítások mentéséhez válassza a > **Létrehozás** **lehetőséget** .

    Nem látja a csoportot? Válassza a **frissítés**lehetőséget.

5. Válassza az **új csoport**lehetőséget, és adja meg a következő beállításokat:

    - **Csoport típusa**: válassza a **Biztonság**elemet.
    - **Csoport neve**: adja meg **az összes Windows-eszközt**.
    - **Tagság típusa**: válassza a **dinamikus eszköz**lehetőséget.
    - **Dinamikus eszközök tagjai**: konfigurálja a lekérdezést:

        - **Tulajdonság**: válassza a **deviceOSType**lehetőséget.
        - **Operátor**: válassza az **egyenlő**lehetőséget.
        - **Érték**: adja meg a **Windowst**.

        1. Válassza a **kifejezés hozzáadása**elemet. A kifejezés a **szabály szintaxisában**látható:

            > [!div class="mx-imgBorder"]
            > ![hozzon létre egy dinamikus lekérdezést, és adjon hozzá kifejezést a Microsoft Intune felügyeleti sablonban](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            Ha a felhasználók vagy az eszközök megfelelnek az Ön által megadott feltételeknek, a rendszer automatikusan hozzáadja őket a dinamikus csoportokhoz. Ebben a példában az eszközök automatikusan hozzáadódnak ehhez a csoporthoz, amikor az operációs rendszer Windows. Ha éles környezetben használja ezt az oktatóanyagot, körültekintően járjon el. A cél a dinamikus csoportok létrehozásának gyakorlata.

        2. **Mentse** > a **Létrehozás** gombra a módosítások mentéséhez.

6. Hozza létre a **minden tanár** csoportot a következő beállításokkal:

    - **Csoport típusa**: válassza a **Biztonság**elemet.
    - **Csoport neve**: adja meg **az összes tanárt**.
    - **Tagság típusa**: válassza a **dinamikus felhasználó**lehetőséget.
    - **Dinamikus felhasználói tagok**: a lekérdezés konfigurálása:

      - **Tulajdonság**: **részleg**kiválasztása.
      - **Operátor**: válassza az **egyenlő**lehetőséget.
      - **Érték**: adja meg a **tanárokat**.

        1. Válassza a **kifejezés hozzáadása**elemet. A kifejezés a **szabály szintaxisában**látható.

            Ha a felhasználók vagy az eszközök megfelelnek az Ön által megadott feltételeknek, a rendszer automatikusan hozzáadja őket a dinamikus csoportokhoz. Ebben a példában a felhasználók automatikusan hozzáadódnak ehhez a csoporthoz, amikor a tanszékük oktatók. Megadhatja az osztályt és a többi tulajdonságot, amikor a felhasználók bekerülnek a szervezetbe. Ha éles környezetben használja ezt az oktatóanyagot, körültekintően járjon el. A cél a dinamikus csoportok létrehozásának gyakorlata.

        2. **Mentse** > a **Létrehozás** gombra a módosítások mentéséhez.

### <a name="talking-points"></a>Beszélő pontok

- A dinamikus csoportok a prémium szintű Azure AD egyik funkciója. Ha nem rendelkezik prémium szintű Azure ADval, a licenccel csak a hozzárendelt csoportok hozhatók létre. A dinamikus csoportokról további információt a következő témakörben talál:

  - [Dinamikus csoporttagság a Azure Active Directoryban (1. rész)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Dinamikus csoporttagság a Azure Active Directoryban (2. rész)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- A prémium szintű Azure AD az alkalmazások és az eszközök kezelésekor általában használt egyéb szolgáltatásokat, például a [többtényezős hitelesítést (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) és a [feltételes hozzáférést](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)is magában foglalja.

- Sok rendszergazda megkérdezi, hogy mikor kell felhasználói csoportokat használni, és mikor kell használni az eszközök csoportjait. Bizonyos útmutatásért lásd: [felhasználói csoportok és eszközök csoportjai](device-profile-assign.md#user-groups-vs-device-groups).

- Ne feledje, hogy egy felhasználó több csoporthoz is tartozhat. Vegye figyelembe a további létrehozott dinamikus felhasználói és eszközcsoport-csoportokat is, például:

  - Minden tanuló
  - Minden Android-eszköz
  - Minden iOS-/iPadOS-eszköz
  - Marketing
  - Emberi erőforrások
  - Az összes Charlotte-alkalmazott
  - Összes Redmond-alkalmazott
  - A West Coast IT-rendszergazdák
  - A keleti parti informatikai rendszergazdák

A létrehozott felhasználókat és csoportokat a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com), az Azure ad-ben is láthatja a Azure Portal, és [a Azure Portal Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973). A bérlői előfizetéshez tartozó összes területen létrehozhat és kezelhet csoportokat. **Ha a cél az eszközkezelés, használja a [Microsoft Endpoint Manager felügyeleti központot](https://go.microsoft.com/fwlink/?linkid=2109431)** .

### <a name="review-group-membership"></a>Csoporttagság áttekintése

1. A Endpoint Manager felügyeleti központban válassza ki a **felhasználók** > a meglévő felhasználók nevét.

    > [!div class="mx-imgBorder"]
    > ![a Endpoint Manager felügyeleti központban válassza a felhasználók lehetőséget](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. Tekintse át a felvehető vagy módosítható információkat. Tekintse meg például a konfigurálható tulajdonságokat, például a beosztás, az részleg, a város, az iroda helye és még sok más. Dinamikus csoportok létrehozásakor ezeket a tulajdonságokat a dinamikus lekérdezésekben is használhatja.
3. Válassza ki a **csoportokat** a felhasználó tagságának megtekintéséhez. A felhasználót eltávolíthatja egy csoportból is.
4. A többi lehetőség kiválasztásával további információkat tekinthet meg, és megteheti. Tekintse meg például a hozzárendelt licencet, a felhasználó eszközeit és egyebeket.

### <a name="what-did-i-just-do"></a>Mit csináltam?

A Endpoint Manager felügyeleti központban új biztonsági csoportokat hozott létre, és hozzáadta a meglévő felhasználókat és eszközöket ezekhez a csoportokhoz. Ezeket a csoportokat az oktatóanyag későbbi lépéseiben fogjuk használni.

## <a name="create-a-template-in-intune"></a>Sablon létrehozása az Intune-ban

Ebben a szakaszban hozzunk létre egy felügyeleti sablont az Intune-ban, tekintse meg a **Csoportházirend felügyeletének**egyes beállításait, és hasonlítsa össze ugyanezt a beállítást az Intune-ban. A cél egy beállítás megjelenítése a csoportházirendben, és ugyanaz a beállítás jelenik meg az Intune-ban.

1. A Endpoint Manager felügyeleti központban válassza az **eszközök** > **konfigurációs profilok** lehetőséget, > **hozzon létre profilt**.
2. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Írja be például a következőt: **felügyeleti sablon – Windows 10 tanulói eszközök**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: válassza a **Felügyeleti sablonok**lehetőséget.

3. Válassza a **Létrehozás** lehetőséget. A **válasszon kategóriát** legördülő listából válassza a **minden termék**elemet. Minden beállítás megjelenik. A beállításokban figyelje meg a következő tulajdonságokat:

    - A szabályzat **elérési útja** ugyanaz, mint csoportházirend felügyelet vagy a gpedit.
    - A beállítás a felhasználókra vagy az eszközökre vonatkozik.

### <a name="open-group-policy-management"></a>Csoportházirend felügyelet megnyitása

Ebben a szakaszban egy szabályzatot mutatunk be az Intune-ban, és az ahhoz tartozó szabályzatot Csoportházirend-felügyeleti szerkesztő.

#### <a name="compare-a-device-policy"></a>Eszköz házirendjének összehasonlítása

1. Nyissa meg a **felügyeleti számítógépen**a **csoportházirend felügyeleti** alkalmazást.

    Ez az alkalmazás az **RSAT: csoportházirend felügyeleti eszközökkel**lesz telepítve, amely a Windows rendszeren telepített választható szolgáltatás. Az [Előfeltételek](#prerequisites) (ebben a cikkben) a telepítésének lépéseit sorolja fel.

2. Bontsa ki a **tartományok** csomópontot > Válassza ki a tartományt. Válassza például a **contoso.net**lehetőséget.
3. Kattintson a jobb gombbal a **OfficeandEdge** házirendre > a **Szerkesztés**gombra. Ekkor megnyílik a Csoportházirend-felügyeleti szerkesztő alkalmazás.

    > [!div class="mx-imgBorder"]
    > ![kattintson a jobb gombbal az Office-és peremhálózati ADMX-Csoportházirendre, majd válassza a szerkesztés lehetőséget](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    A **OfficeandEdge** olyan csoportházirend, amely tartalmazza az Office és a Microsoft Edge ADMX-sablonokat. Ezt a szabályzatot az [Előfeltételek](#prerequisites) (ebben a cikkben) ismertetjük.

4. Bontsa ki a **Számítógép konfigurációja** > **házirendek** > **Felügyeleti sablonok** > Vezérlőpult > **személyre szabás** **elemet** . Figyelje meg a rendelkezésre álló beállításokat.

    > [!div class="mx-imgBorder"]
    > ![bontsa ki a számítógép-konfigurációt a Csoportházirend-felügyeleti szerkesztőban, és lépjen a személyre szabás](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    Kattintson duplán a **zárolási képernyő kamerájának engedélyezése**lehetőségre, és tekintse meg a rendelkezésre álló beállításokat:

    > [!div class="mx-imgBorder"]
    > ![tekintse meg a csoportházirend](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png) a számítógép konfigurációja beállítás beállításait.

5. Az Eszközkezelő felügyeleti központban lépjen a **felügyeleti sablon – Windows 10 Student-eszközök** sablonra.
6. Válassza a **minden termék** elemet a legördülő listából, és keresse meg a **személyre szabás**kifejezést:

    > [!div class="mx-imgBorder"]
    > ![személyre szabás keresése a felügyeleti sablonban Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    Figyelje meg a rendelkezésre álló beállításokat.

    A beállítás típusa **eszköz**, az elérési út pedig **\Control Panel\Personalization**. Ez az elérési út hasonló ahhoz, amit csak láttál Csoportházirend-felügyeleti szerkesztőban. Ha megnyitja a beállítást, a Csoportházirend-felügyeleti szerkesztőban megjelenő **nem konfigurált**, **engedélyezett**és **letiltott** beállítások láthatók.

#### <a name="compare-a-user-policy"></a>Felhasználói házirend összehasonlítása

1. A felügyeleti sablonban keressen az **InPrivate-böngészés**kifejezésre. Figyelje meg az elérési utat, és a beállítás a felhasználókra és az eszközökre is vonatkozik.

2. A **csoportházirend-felügyeleti szerkesztőban**keresse meg a megfelelő felhasználói és eszközbeállítások beállításait:

    - Eszköz: bontsa ki a **Számítógép konfigurációja** > **házirendek** > **Felügyeleti sablonok** > **Windows-összetevők** > **Internet Explorer** > **adatvédelmi** > **kapcsolja ki a InPrivate-böngészést**.
    - Felhasználó: bontsa ki a **felhasználói konfiguráció** > **házirendek** > **Felügyeleti sablonok** > **Windows-összetevők** > **Internet Explorer** > **adatvédelmi** > **kapcsolja ki a InPrivate-böngészést**.

    > [!div class="mx-imgBorder"]
    > ![az Internet Explorerben kapcsolja ki az InPrivate-böngészést az ADMX-sablon használatával](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> A beépített Windows-szabályzatok megjelenítéséhez a GPEdit (Csoportházirend-alkalmazás**szerkesztése** ) is használható.

#### <a name="compare-an-edge-policy"></a>Peremhálózati házirend összehasonlítása

1. Az Eszközkezelő felügyeleti központban lépjen a **felügyeleti sablon – Windows 10 Student-eszközök** sablonra.
2. Válassza ki a **Edge 77-es vagy újabb verzióját** a legördülő listából.
3. Keresés az **indításhoz**. Figyelje meg a rendelkezésre álló beállításokat.
4. A Csoportházirend-felügyeleti szerkesztőban keresse meg az alábbi beállításokat:

    - Eszköz: bontsa ki a **Számítógép konfigurációja** > **szabályzatok** > **Felügyeleti sablonok** > a **Microsoft Edge** > **Startup, a Kezdőlap és az új lap**lapot.
    - Felhasználó: bontsa ki a **felhasználói konfiguráció** > **szabályzatok** > **Felügyeleti sablonok** > a **Microsoft Edge** > **Startup, a Kezdőlap és az új lap** lapot

### <a name="what-did-i-just-do"></a>Mit csináltam?

Létrehozott egy felügyeleti sablont az Intune-ban. Ebben a sablonban néhány ADMX-beállítást vizsgáltunk meg, és megvizsgáltuk az ADMX-beállításokat Csoportházirend-felügyeletben.

## <a name="add-settings-to-the-students-admin-template"></a>Beállítások hozzáadása a tanulók felügyeleti sablonhoz

Ebben a sablonban néhány Internet Explorer-beállítást konfigurálunk a több tanuló által megosztott eszközök zárolásához.

1. A **felügyeleti sablonban – Windows 10 tanulói eszközök**területen keressen rá az **InPrivate-böngészés kikapcsolása**lehetőségre, és válassza ki az eszköz házirendjét:

    > [!div class="mx-imgBorder"]
    > ![az InPrivate-böngészési eszköz házirendjének kikapcsolása a felügyeleti sablonban a Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. Ebben az ablakban láthatja a megadható leírást és értékeket. Ezek a beállítások a csoportházirendben láthatóhoz hasonlóak.
3. A módosítások mentéséhez kattintson az **engedélyezve** > **az OK gombra** .
4. Konfigurálja az Internet Explorer következő beállításait is. Ügyeljen rá, hogy a módosítások mentéséhez kattintson **az OK gombra** .

    - **Fájlok húzásának vagy másolásának és beillesztésének engedélyezése**
      - **Típus**: eszköz
      - **Elérési út**: \Windows Internet Explorer\Internet Control Panel\Security Page\Internet Zone
      - **Érték**: letiltva

    - **A tanúsítvány hibáinak figyelmen kívül hagyása**
      - **Típus**: eszköz
      - **Elérési út**: \Windows Internet Explorer\Internet Control Panel
      - **Érték**: engedélyezve

    - **Kezdőlap beállításainak módosításának letiltása**
      - **Típus**: felhasználó
      - **Elérési út**: \Windows Internet Explorer
      - **Érték**: engedélyezve
      - **Kezdőlap**: adjon meg egy URL-címet, például `contoso.com`.

5. Törölje a keresési szűrőt. Figyelje meg, hogy a konfigurált beállítások felül vannak sorolva:

    > [!div class="mx-imgBorder"]
    > ![konfigurált beállítások a Microsoft Intune tetején jelennek meg](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>Sablon kiosztása

1. A sablonban válassza a **hozzárendelések**lehetőséget. Előfordulhat, hogy be kell jelölnie a sablont, majd ki kell választania az **eszközök – konfigurációs profilok** listából:

    > [!div class="mx-imgBorder"]
    > ![válassza ki a felügyeleti sablon profilját a Microsoft Intune eszköz konfigurációs profilok listájából](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. Válassza ki **a felvenni kívánt csoportokat**. Megjelenik a meglévő felhasználók és csoportok listája.
3. Válassza ki a korábban létrehozott **összes Windows 10 Student Devices** csoportot > **válassza a lehetőséget**.

    Ha éles környezetben használja ezt az oktatóanyagot, vegye fontolóra az üres csoportok hozzáadását. A cél a sablon hozzárendelésének gyakorlása.

4. **Mentse** a változtatásokat.

Amint a profil mentése megtörtént, a rendszer az eszközre alkalmazza az Intune-ba való bejelentkezéskor. Ha az eszközök csatlakoznak az internethez, akkor azonnal megtörténhet. A házirend-frissítési időpontokkal kapcsolatos további információkért tekintse meg, [mennyi ideig tart a szabályzatok, a profilok vagy az alkalmazások hozzárendelése az eszközökhöz](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Szigorú vagy korlátozó szabályzatok és profilok kiosztásakor ne zárja ki magát. Érdemes lehet olyan csoportot létrehozni, amely ki van zárva a szabályzatokból és a profilokból. Az ötlet a hibákhoz való hozzáférés. A csoport figyelése annak megerősítéséhez, hogy a rendszer a kívánt módon használja.

### <a name="what-did-i-just-do"></a>Mit csináltam?

A Endpoint Manager felügyeleti központban létrehozott egy felügyeleti sablon-eszköz konfigurációs profilt, és hozzárendelte a profilt egy létrehozott csoporthoz.

## <a name="create-a-onedrive-template"></a>OneDrive-sablon létrehozása

Ebben a szakaszban egy OneDrive-rendszergazdai sablont hoz létre az Intune-ban egyes beállítások szabályozásához. Ezek a beállítások úgy vannak kiválasztva, hogy a szervezetek gyakran használják őket.

1. Hozzon létre egy másik profilt (**eszközök** > **konfigurációs profilok** > **create Profile**).

2. Adja meg a következő tulajdonságokat:

    - **Név**: írja be **a felügyeleti sablon-OneDrive szabályzatokat, amelyek az összes Windows 10 felhasználóra érvényesek**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: válassza a **Felügyeleti sablonok**lehetőséget.

3. Válassza a **Létrehozás** lehetőséget.
4. Válassza az **Office** lehetőséget a legördülő listából.
5. **Engedélyezze** a következő beállításokat. Ügyeljen rá, hogy a módosítások mentéséhez kattintson **az OK gombra** .

    - **Felhasználók beavatkozás nélküli beadása a OneDrive szinkronizálási ügyfeléhez Windows-beli hitelesítő adataikkal**
    - **Igény szerinti OneDrive-fájlok használata**
    - **Személyes OneDrive-fiókok szinkronizálásának tiltása a felhasználók számára**

A beállítások a következő beállításokhoz hasonlóan néznek ki:

> [!div class="mx-imgBorder"]
> ![OneDrive felügyeleti sablon létrehozása Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

Az OneDrive kapcsolatos további információkért lásd: [a OneDrive-szinkronizálási ügyfélbeállítások szabályozása Csoportházirend használata](https://docs.microsoft.com/onedrive/use-group-policy).

### <a name="assign-your-template"></a>Sablon kiosztása

1. A sablonban válassza a **hozzárendelések**lehetőséget.
2. Válassza ki **a felvenni kívánt csoportokat**. Megjelenik a meglévő felhasználók és csoportok listája.
3. Válassza ki a korábban létrehozott **összes Windows-eszköz** csoportot > **válassza a lehetőséget**.

    Ha éles környezetben használja ezt az oktatóanyagot, vegye fontolóra az üres csoportok hozzáadását. A cél a sablon hozzárendelésének gyakorlása.

4. **Mentse** a változtatásokat.

Ezen a ponton létrehozott néhány felügyeleti sablont, és hozzárendelte őket a létrehozott csoportokhoz. A következő lépés egy felügyeleti sablon létrehozása a Windows PowerShell használatával és az Intune-hoz készült Microsoft Graph API-val.

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>Nem kötelező: szabályzat létrehozása a PowerShell és a Graph API használatával

Ez a szakasz a következő erőforrásokat használja. Ezeket az erőforrásokat ebben a szakaszban fogjuk telepíteni.

- [Intune PowerShell SDK](https://github.com/microsoft/Intune-PowerShell-SDK)
- [Microsoft Graph API az Intune-hoz](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. A **felügyeleti számítógépen**nyissa meg a **Windows PowerShellt** rendszergazdaként:

    1. A keresősáv mezőbe írja be a **PowerShell**kifejezést.
    2. Kattintson a jobb gombbal a **Windows PowerShell** > **Futtatás rendszergazdaként**lehetőségre.

    > [!div class="mx-imgBorder"]
    > ![futtassa a Windows PowerShellt rendszergazdaként](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. A végrehajtási házirend beolvasása és beállítása.

    1. Adja meg a következőket: `get-ExecutionPolicy`

        Jegyezze fel, hogy mit kell beállítani, ami **korlátozható**. Ha elkészült az Oktatóanyaggal, állítsa vissza az eredeti értékre.

    2. Adja meg a következőket: `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. A módosításhoz adja meg `Y`.

    A PowerShell végrehajtási házirendje segít megelőzni a kártékony parancsfájlok futtatását. További információ: [a végrehajtási szabályzatok](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).

3. Adja meg a következőket: `Install-Module -Name Microsoft.Graph.Intune`

    Adja meg a `Y`, ha:

    - A NuGet-szolgáltató telepítésének megválaszolása
    - A modulok nem megbízható tárházból való telepítésének megválaszolása

    A művelet végrehajtása több percet is igénybe vehet. Ha elkészült, a következőhöz hasonló üzenet jelenik meg:

    > [!div class="mx-imgBorder"]
    > ![a Windows PowerShell-parancssort a modul telepítése után](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. A böngészőben nyissa meg a [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases), és válassza ki az **Intune-PowerShell-SDK_v6.1907.00921.0001. zip** fájlt.

    1. Válassza a **Mentés másként**lehetőséget, és válasszon egy mappát, amelyről emlékezni fog. `c:\psscripts` jó választás.
    2. Nyissa meg a mappát, kattintson a jobb gombbal a. zip fájlra > **bontsa** ki az összes > - **kivonatot**. A mappa szerkezete a következő mappához hasonlóan néz ki:

        > [!div class="mx-imgBorder"]
        > az Intune PowerShell SDK-mappa szerkezete ![kibontása után](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. A **nézet** lapon tekintse **át**a fájlnévkiterjesztések:

    > [!div class="mx-imgBorder"]
    > ![az Explorer nézet lapján válassza ki a fájlnévkiterjesztések elemet](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. A mappában, és lépjen a `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`elemre. Kattintson a jobb gombbal minden. dll > **Tulajdonságok** elemre > **feloldásához**.

    > [!div class="mx-imgBorder"]
    > ![a DLL-fájlok blokkolásának feloldása](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. A **Windows PowerShell** alkalmazásban írja be a következőket:

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    Adja meg `R` ha a rendszer kéri, hogy a nem megbízható közzétevőtől futtassa a parancsot.

8. Az Intune felügyeleti sablonjai a Graph béta verzióját használják:

    1. Adja meg a következőket: `Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. Adja meg a következőket: `Connect-MSGraph -AdminConsent`

    3. Ha a rendszer kéri, jelentkezzen be ugyanazzal a Microsoft 365 rendszergazdai fiókkal. Ezek a parancsmagok létrehozzák a szabályzatot a bérlői szervezetben.

        **Felhasználó**: adja meg a Microsoft 365 bérlői előfizetés rendszergazdai fiókját.  
        **Password (jelszó**): adja meg a jelszavát.

    4. Válassza az **elfogadás**lehetőséget.

9. Hozza létre a **teszt konfigurációs** konfigurációs profilt. Adja meg a következőt:

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    Ha ezek a parancsmagok sikeresek, a rendszer létrehozza a profilt. A megerősítéshez nyissa meg a Endpoint Manager felügyeleti központot > **konfigurációs profilokat**. A **teszt konfigurációs** profiljának szerepelnie kell a listáján.

10. Az összes SettingDefinitions beolvasása. Adja meg a következőt:

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. Keresse meg a definíció AZONOSÍTÓját a megjelenítendő név beállítás használatával. Adja meg a következőt:

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. Konfiguráljon egy beállítást. Adja meg a következőt:

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>Tekintse meg a szabályzatot

1. A Endpoint Manager felügyeleti központban > **konfigurációs profilok** > **frissítés**.
2. Válassza ki a **teszt konfigurációs** profiljának > **beállításait**.
3. A legördülő listában válassza a **minden termék**elemet.

A **felhasználói beavatkozás nélküli bejelentkezés a OneDrive-szinkronizálási ügyfélen a Windows hitelesítő adataival** beállítás be van állítva.

## <a name="policy-best-practices"></a>Házirend – ajánlott eljárások

Ha szabályzatokat és profilokat hoz létre az Intune-ban, néhány javaslatot és ajánlott eljárást érdemes figyelembe venni. További információ: [szabályzatok és profilok – ajánlott eljárások](device-profile-create.md#recommendations).

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha már nincs rá szükség, a következőket teheti:

- Törölje a létrehozott csoportokat:

  - **Minden Windows 10 Student-eszköz**
  - **Minden Windows-eszköz**
  - **Minden tanár**

- Törölje a létrehozott felügyeleti sablonokat:

  - **Felügyeleti sablon – Windows 10 tanulói eszközök**
  - **Felügyeleti sablon – az összes Windows 10 felhasználóra vonatkozó OneDrive szabályzatok**
  - **Konfiguráció tesztelése**

- Állítsa vissza a Windows PowerShell végrehajtási házirendjét az eredeti értékre. A következő példa a végrehajtási házirendet korlátozza:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>További lépések

Ebben az oktatóanyagban jobban megismerte a [Microsoft Endpoint Manager felügyeleti központját](https://go.microsoft.com/fwlink/?linkid=2109431), és a lekérdezés-szerkesztővel dinamikus csoportokat hozott létre, és létrehozott felügyeleti sablonokat az Intune-ban az [ADMX-beállítások](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)konfigurálásához. A helyszíni és a Felhőbeli ADMX-sablonok használatával is összehasonlíthatja az Intune-nal. Bónuszként a PowerShell-parancsmagok használatával hozzon létre egy felügyeleti sablont.

Az Intune felügyeleti sablonjaival kapcsolatos további információkért lásd:

> [!div class="nextstepaction"]
> [A csoportházirend-beállítások konfigurálása az Intune-ban Windows 10-es sablonok használatával](administrative-templates-windows.md)
