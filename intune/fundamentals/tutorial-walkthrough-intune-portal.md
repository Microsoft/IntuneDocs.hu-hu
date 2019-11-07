---
title: Oktatóanyag – útmutató az Intune-hoz a Azure Portal
titleSuffix: Microsoft Intune
description: Ebben az oktatóanyagban Microsoft Intune a feladatok végrehajtásának jobb megismeréséhez.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9197d4f96eae1041b00b07110ef421a12a4fe338
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712998"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Oktatóanyag: a Microsoft Intune áttekintése a Azure Portal

Az [Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) több mint 100 szolgáltatást tartalmaz, amelyek segítséget nyújtanak a különböző felhőalapú számítástechnikai forgatókönyvekhez és lehetőségekhez. Microsoft Intune az Azure-ban elérhető számos szolgáltatás egyike. Az Intune segítségével biztosíthatja, hogy a vállalat eszközei, alkalmazásai és adatai megfeleljenek a vállalat biztonsági követelményeinek. A vezérlővel beállíthatja, hogy mely követelményeket kell ellenőrizni, és mi történik, ha ezek a követelmények nem teljesülnek. A Microsoft Intune szolgáltatást az [Azure Portalon](https://portal.azure.com) találhatja meg. Az Intune funkcióinak megismerése segít a különböző mobileszköz-kezelési (MDM) és mobileszköz-kezelési (MAM) feladatok megvalósításában.

Ebben az oktatóanyagban a következőket fogja elsajátítani:
> [!div class="checklist"]
> * Bemutató Microsoft Intune
> * A Azure Portal konfigurálása

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
A Microsoft Intune beállítása előtt tekintse át az alábbi követelményeket:

- [Támogatott operációs rendszerek és böngészők](../supported-devices-browsers.md) 
- [A hálózati konfiguráció követelményei és a sávszélesség](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Regisztráció a Microsoft Intune ingyenes próbaverziójára

Az Intune kipróbálása 30 napig ingyenes. Ha már rendelkezik munkahelyi vagy iskolai fiókkal, **jelentkezzen be** vele, és adja hozzá az Intune-t az előfizetéshez. Ellenkező esetben regisztrálhat [az ingyenes próbaverziós fiókra](free-trial-sign-up.md) , hogy az Intune-t használja a szervezete számára.

> [!IMPORTANT]
> Meglévő munkahelyi vagy iskolai fiókok nem vonhatók össze újonnan regisztrált fiókokkal.

## <a name="tour-microsoft-intune"></a>Bemutató Microsoft Intune

Kövesse az alábbi lépéseket az Intune jobb megismeréséhez a Azure Portalban. A turné befejezése után jobban megismerheti az Intune egyes főbb területeit.

1. Nyisson meg egy böngészőt, és jelentkezzen be az [Intune-portálra](https://aka.ms/intuneportal). Ha még nem ismeri az Intune-t, használja az ingyenes próbaverziós előfizetését.

    ![A Microsoft Intune portál képernyőképe](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Amikor megnyitja az Intune-t vagy bármely más szolgáltatást az Azure-ban, a szolgáltatás megjelenik egy panelen. Az Intune-ban használható első munkaterhelések közé tartoznak például az **eszközök**, az **ügyfélalkalmazások**, a **felhasználók**és a **csoportok**. A munkaterhelés egyszerűen egy szolgáltatás alterülete. Amikor kiválasztja a munkaterhelést, az a panel teljes oldalként nyílik meg. Az egyéb ablaktáblák a megnyitáskor a panel jobb oldalán, az előző ablaktábla megjelenítéséhez pedig a Bezárás gombra mutatnak. A panelt egy panelnek is nevezzük. 

    Alapértelmezés szerint az Intune megnyitásakor megjelenik az **Áttekintés** panel. Ez a panel az eszköz-hozzárendelés és a megfelelőségi állapot általános vizuális pillanatképét, valamint az alkalmazások telepítési állapotát jeleníti meg.

2. Az [Intune](https://aka.ms/intuneportal)-ból válassza az **eszközök** regisztrálása lehetőséget a regisztrált eszközök adatainak megjelenítéséhez az Intune-bérlőben. Ha új Intune-bérlőt indít, még nem lesz regisztrált eszköze. 

    ![Képernyőfelvétel az eszközök regisztrálási paneljéről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Az Intune-nal kezelheti a munkaerő eszközeit és alkalmazásait, beleértve a vállalati adataik elérését. A mobileszköz-felügyeleti (MDM) szolgáltatás használatához először regisztrálni kell az eszközöket az Intune-ban. Az eszközök regisztrálásakor azok egy MDM-tanúsítványt kapnak. Ez a tanúsítvány az Intune szolgáltatással való kommunikációra szolgál. 

    Több módszer is van a munkaerő eszközeinek Intune-ba való regisztrálására. Az egyes módszerek az eszköz tulajdonosától (személyes vagy céges), az eszköztípustól (iOS, Windows, Android) és a felügyeleti követelményektől (alaphelyzetbe állítások, affinitás, zárolás) függ. Az eszközök regisztrálásának engedélyezése előtt azonban be kell állítania az Intune-infrastruktúrát. Különösen fontos, hogy az eszközregisztrációhoz szükség van [saját MDM-szolgáltató beállítására](mdm-authority-set.md). Az Intune-környezet (bérlő) készenléti állapotáról további információt az [Intune beállítása](setup-steps.md)című témakörben talál. Ha elkészült az Intune-Bérlővel, regisztrálhat eszközöket. További információt az eszközregisztrációról a [Mi az eszközregisztrálás?](../enrollment/device-enrollment.md) című témakörben találhat

3. Az [Intune-ból válassza](https://aka.ms/intuneportal)az **eszköz megfelelősége** lehetőséget az Intune által felügyelt eszközök megfelelőségi adatainak megjelenítéséhez. A következő képhez hasonló részleteket fog látni.

    ![Képernyőfelvétel az eszköz megfelelőségi paneljéről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    A megfelelőségi követelmények alapvetően szabályok, például az eszköz PIN-kódjának megkövetelése vagy az eszközök titkosításának megkövetelése. Az eszköz megfelelőségi szabályzatai határozzák meg azokat a szabályokat és beállításokat, amelyeket az eszköznek követnie kell a megfelelőség szempontjából. Az eszközök megfelelőségének használatához a következőket kell tennie:
    - Intune és Azure Active Directory (Azure AD) prémium szintű előfizetés
    - Támogatott platformot futtató eszközök
    - Az eszközöket regisztrálni kell az Intune-ban
    - Egy felhasználóhoz vagy elsődleges felhasználóhoz regisztrált eszközök.
    
    További információkért lásd: az [eszközök megfelelőségi szabályzatának első lépései az Intune-ban](../protect/device-compliance-get-started.md).

4. Az [Intune](https://aka.ms/intuneportal)-ból válassza az **eszköz konfigurációja** lehetőséget az eszközbeállítások az Intune-ban való megjelenítéséhez.

    ![Képernyőfelvétel az eszköz konfigurációs paneljéről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Az Intune olyan beállításokat és funkciókat kínál, amelyeket Ön engedélyezhet vagy letilthat a vállalatához tartozó különböző eszközökön. Ezek a beállítások és funkciók hozzáadódnak a "konfigurációs profilokhoz". Létrehozhat profilokat különböző eszközökhöz és különböző platformokhoz, például iOS-, Android-és Windows-rendszerekhez is. Ezt követően az Intune használatával alkalmazhatja a profilt a szervezet eszközeire.   

    Az eszköz konfigurációjával kapcsolatos további információkért lásd: a [szolgáltatások beállításainak alkalmazása az eszközökön a Microsoft Intune eszköz profiljainak használatával](../configuration/device-profiles.md).

5. Az [Intune](https://aka.ms/intuneportal)-ból válassza az **eszközök** lehetőséget az Intune-bérlő regisztrált eszközeinek részleteinek megjelenítéséhez. Ha új Intune-bejegyzést indít, akkor még nem lesz regisztrált eszköze.

    ![Képernyőfelvétel az eszközök regisztrálási paneljéről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)

    Az **eszközök** ablaktábla a bérlő regisztrált eszközeinek részleteit tartalmazza. Az Intune-bérlőhöz tartozó eszközök listájának megjelenítéséhez kattintson a **minden eszköz** lehetőségre.

6. Az [Intune](https://aka.ms/intuneportal)-ból válassza az **ügyfélalkalmazások** lehetőséget az alkalmazások telepítési állapotának megjelenítéséhez.

    ![Képernyőkép az ügyfélalkalmazások panelről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)

    A rendszergazdák a Microsoft Intune használatával kezelhetik a cég által használt ügyfélalkalmazásokat. Ez a funkció az eszközkezelési és adatvédelmi funkciókat egészíti ki. A rendszergazdák egyik elsődleges feladata annak biztosítása, hogy a végfelhasználók hozzáférjenek a munkájukhoz szükséges alkalmazásokhoz. Emellett előfordulhat, hogy az Intune-ban nem regisztrált eszközökön található alkalmazásokat is szeretne hozzárendelni és felügyelni. Az Intune számos szolgáltatást kínál a szükséges alkalmazások kívánt eszközökön való használatához. Az alkalmazások hozzáadásával és hozzárendelésével kapcsolatos további információkért lásd: [Alkalmazások hozzáadása Microsoft Intune](../apps/apps-add.md) és [alkalmazások társítása a csoportokhoz a Microsoft Intune használatával](../apps/apps-deploy.md).

7. Az [Intune](https://aka.ms/intuneportal)-ból válassza a **feltételes hozzáférés** lehetőséget a hozzáférési szabályzatok részleteinek megjelenítéséhez.

    ![A feltételes hozzáférés panel képernyőképe](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    A feltételes hozzáférés arra utal, hogy miként szabályozható az e-mailekhez és a vállalati erőforrásokhoz való kapcsolódásra jogosult eszközök és alkalmazások. Az eszköz-és az alkalmazás-alapú feltételes hozzáférés megismeréséhez és az Intune-nal való feltételes hozzáférés használatának gyakori forgatókönyveit lásd: [Mi a feltételes hozzáférés?](../protect/conditional-access.md)

8. Az [Intune](https://aka.ms/intuneportal)-ból válassza a **felhasználók** lehetőséget az Intune-ban található felhasználók részleteinek megjelenítéséhez. Ezek a felhasználók a vállalat munkaereje.

    ![Képernyőfelvétel a felhasználók panelről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Hozzáadhat felhasználókat közvetlenül az Intune-hoz, vagy szinkronizálhat felhasználókat a helyszíni Active Directoryról. Ha felvették a felhasználókat a szolgáltatásba, regisztrálhatják az eszközeiket, és elérhetik a vállalati erőforrásokat. Emellett további engedélyeket is biztosíthat a felhasználóknak az Intune eléréséhez. További információ: [felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](users-add.md).

9. Az [Intune](https://aka.ms/intuneportal)-ból válassza a **csoportok** lehetőséget az intune-ban található Azure Active Directory-(Azure ad-) csoportok részleteinek megjelenítéséhez. Intune-rendszergazdaként csoportok használatával kezelheti az eszközöket és a felhasználókat.

    ![Képernyőfelvétel a csoportok panelről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    A szervezeti igényeknek megfelelő csoportokat is beállíthat. Létrehozhat csoportokat a felhasználók és eszközök földrajzi hely, részleg vagy hardverjellemzők szerinti rendezéséhez. Használjon csoportokat a feladatok nagy számban való végrehajtásához. Beállíthatja például, hogy a szabályzatok számos felhasználóhoz legyenek beállítva, vagy alkalmazásokat telepítsenek egy adott eszközre. A csoportokkal kapcsolatos további információkért lásd: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](../groups-add.md).

10. Az [Intune](https://aka.ms/intuneportal)-ban kattintson a **Súgó és támogatás** lehetőségre a Súgó kéréséhez. Rendszergazdaként a **Súgó és támogatás** lehetőséget használhatja a megoldások keresésére és megtekintésére, valamint az Intune-hoz kapcsolódó online támogatási jegy beszerzésére. 

    ![A Súgó és támogatás panel képernyőképe](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Támogatási jegy létrehozásához a fiókot rendszergazdai szerepkörként kell hozzárendelni a Azure Active Directory-ben. Rendszergazdai szerepkörök: **Intune-rendszergazda**, **globális rendszergazda**és **szolgáltatás-rendszergazda**. További információkért lásd: [a Microsoft Intune támogatásának beszerzése](../get-support.md).

11. Az [Intune](https://aka.ms/intuneportal)-ból válassza a **bérlő állapota** lehetőséget az Intune-bérlő részleteinek megjelenítéséhez.

    ![Képernyőfelvétel a bérlő állapota panelről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    A bérlői állapot részletei közé tartozik az összekötő állapota, az Intune Service Health és az Intune-hírek. Ha a Bérlővel vagy az Intune-nal kapcsolatban bármilyen probléma merül fel, a részletek a **bérlő állapota** ablaktáblán találhatók. További információ: az [Intune-bérlő állapota](../tenant-status.md).

12. Az [Intune](https://aka.ms/intuneportal)-ból válassza a **Hibaelhárítás** lehetőséget a hibaelhárítási tippek, támogatás kérése vagy az Intune állapotának ellenőrzéséhez. Ezek az információk a kiválasztott Intune-felhasználóra vonatkoznak.

    ![Képernyőkép a hibakeresési panelről](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

További információ az Intune-on belüli hibaelhárításról: [a hibaelhárítási portál használata a felhasználóknak a vállalatnál](../help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>A Azure Portal konfigurálása

Az Azure segítségével testreszabhatja és konfigurálhatja a portál nézetét.

### <a name="change-the-sidebar"></a>Az oldalsáv módosítása

Az Azure Portal bal oldalán található **oldalsáv** megjeleníti az összes rendelkezésre álló Azure-szolgáltatást tartalmazó listát. Ennek az átfogó listának az alapértelmezett nézetét módosíthatja, hogy egy állandó nézetet hozzon létre azokból a szolgáltatásokból, amelyek az Ön számára a legfontosabbak. Az alábbiakban példaszolgáltatásként az Intune-t fogjuk felvenni a lista tetejére.

![Egy felhasználó a Microsoft Intune-t keresi a „További szolgáltatások” listában.](./media/tutorial-walkthrough-intune-portal/azure-add-intune1.png)

1. Válassza a lap bal oldalán lévő oldalsávon a **Minden szolgáltatás** hivatkozást.
2. Keressen az **Intune** kifejezésre a szűrőmezőben.
3. Kattintson a **csillagra**, amivel felveszi az Intune-t a kedvenc szolgáltatásai listájának az aljára.
4. Mutasson az Intune szolgáltatásra. Jelölje ki és húzza át az Intune-t a szolgáltatás nevének jobb oldalán található **három függőleges ponttal**.

### <a name="change-the-dashboard"></a>Az irányítópult módosítása

Az alapértelmezett kezdőlap az **irányítópult**. Ezen a lapon szabhatja személyre a csempéket az Ön számára legfontosabb információk megjelenítéséhez.

![Az általános új irányítópult képe. Az oldalsáv látható az összes szolgáltatással a bal oldalon, a fő irányítópult pedig középen. Az irányítópult módosítógombjai felül vannak, valamint csempék láthatók, amelyekkel elérhető az összes erőforrás, a gyorsútmutatók, a szolgáltatásállapot és az Azure-piactér.](./media/tutorial-walkthrough-intune-portal/azure-default-dashboard.png)

A jelenlegi irányítópult módosításához válassz az **Irányítópult szerkesztése** gombot. Ha nem szeretné módosítani az alapértelmezett irányítópultot, létrehozhat egy **új irányítópultot** is. Új irányítópult létrehozásakor egy üres saját irányítópultot kap **Csempetárral**, amelyen új csempéket vehet fel és átrendezheti a csempéket. Csempéket találhat **általános** kategóriájuk, **típusuk** segítségével, **kereséssel** és **erőforráscsoportjuk** vagy **címkéjük** alapján.

Ezeken kívül felvehet csempéket az irányítópultra bármely **három pont** gombbal, ha a **Rögzítés az irányítópulton** lehetőséget választja.

![A Felhasználók és csoportok > Minden csoport hely közelképe az Intune-ban, amelyen látszik a „Rögzítés az irányítópulton” menüpont a csoport jobb szélén.](./media/tutorial-walkthrough-intune-portal/azure-pin-to-dashboard.png)

Ez a funkció relevánsabb lesz, miután további tartalmakat is hozzáadott az Intune-hoz, például csoportokat és felhasználókat.

## <a name="next-steps"></a>További lépések

A Microsoft Intune gyors futtatásához lépjen az Intune rövid útmutatói között az ingyenes Intune-fiók beállításával.

> [!div class="nextstepaction"]
> [Rövid útmutató: próbálja ki Microsoft Intune ingyen](free-trial-sign-up.md)
