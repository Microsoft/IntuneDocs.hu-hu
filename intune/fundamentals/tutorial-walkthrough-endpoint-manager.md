---
title: Oktatóanyag – útmutató az Intune-hoz a Microsoft Endpoint Managerben
titleSuffix: Microsoft Intune
description: Ebben az oktatóanyagban a Microsoft Endpoint Manager felügyeleti központban Microsoft Intune a feladatok végrehajtásának jobb megismeréséhez.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d8950e57c2427c522d337807d315ed5c399c0d5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514081"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Oktatóanyag: útmutató az Intune-hoz a Microsoft Endpoint Managerben

Az [Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) több mint 100 szolgáltatást tartalmaz, amelyek segítséget nyújtanak a különböző felhőalapú számítástechnikai forgatókönyvekhez és lehetőségekhez. Microsoft Intune az Azure-ban elérhető számos szolgáltatás egyike. Az Intune segítségével biztosíthatja, hogy a vállalat eszközei, alkalmazásai és adatai megfeleljenek a vállalat biztonsági követelményeinek. A vezérlővel beállíthatja, hogy mely követelményeket kell ellenőrizni, és mi történik, ha ezek a követelmények nem teljesülnek. A [Microsoft Endpoint Manager felügyeleti központjának](https://go.microsoft.com/fwlink/?linkid=2109431) segítségével megtalálhatja a Microsoft Intune szolgáltatást, valamint az eszközök egyéb kezelésével kapcsolatos beállításokat. Az Intune funkcióinak megismerése segít a különböző mobileszköz-kezelési (MDM) és mobileszköz-kezelési (MAM) feladatok megvalósításában.

> [!NOTE]
> A Microsoft Endpoint Manager egyetlen, integrált végpont-felügyeleti platform az összes végpont kezeléséhez. Ez a Microsoft Endpoint Manager felügyeleti központ integrálja a ConfigMgr és a Microsoft Intune.

Az oktatóanyag során az alábbi lépéseket fogja végrehajtani:
> [!div class="checklist"]
> * Ismerkedés a Microsoft Endpoint Manager felügyeleti központjával
> * A Microsoft Endpoint Manager felügyeleti központ nézetének testreszabása

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
A Microsoft Intune beállítása előtt tekintse át az alábbi követelményeket:

- [Támogatott operációs rendszerek és böngészők](../supported-devices-browsers.md) 
- [A hálózati konfiguráció követelményei és a sávszélesség](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Regisztráció a Microsoft Intune ingyenes próbaverziójára

Az Intune kipróbálása 30 napig ingyenes. Ha már rendelkezik munkahelyi vagy iskolai fiókkal, **jelentkezzen be** vele, és adja hozzá az Intune-t az előfizetéshez. Ellenkező esetben regisztrálhat [az ingyenes próbaverziós fiókra](free-trial-sign-up.md) , hogy az Intune-t használja a szervezete számára.

> [!IMPORTANT]
> Meglévő munkahelyi vagy iskolai fiókok nem vonhatók össze újonnan regisztrált fiókokkal.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Bemutató Microsoft Intune a Microsoft Endpoint Manager felügyeleti központban

Kövesse az alábbi lépéseket az Intune jobb megismeréséhez a Microsoft Endpoint Manager felügyeleti központban. A turné befejezése után jobban megismerheti az Intune egyes főbb területeit.

1. Nyisson meg egy böngészőt, és jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431). Ha még nem ismeri az Intune-t, használja az ingyenes próbaverziós előfizetését.

    ![A Microsoft Endpoint Manager felügyeleti központ képernyőképe – Kezdőlap](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Amikor megnyitja a Microsoft Endpoint Managert vagy bármely más szolgáltatást az Azure-ban, a szolgáltatás megjelenik egy panelen. Az Intune-ban használható első munkaterhelések közé tartoznak például az **eszközök**, az **alkalmazások**, a **felhasználók**és a **csoportok**. A munkaterhelés egyszerűen egy szolgáltatás alterülete. Amikor kiválasztja a munkaterhelést, az a panel teljes oldalként nyílik meg. Az egyéb ablaktáblák a megnyitáskor a panel jobb oldalán, az előző ablaktábla megjelenítéséhez pedig a Bezárás gombra mutatnak. 

    Alapértelmezés szerint a Microsoft Endpoint Manager megnyitásakor megjelenik a **Kezdőlap** ablaktábla. Ez a panel a bérlői állapot és a megfelelőségi állapot általános vizuális pillanatképét, valamint más hasznos hivatkozásokat tartalmaz.

2. A navigációs ablaktáblán válassza az **irányítópult** lehetőséget az Intune-bérlőben található eszközök és ügyfélalkalmazások általános részleteinek megjelenítéséhez. Ha új Intune-bérlőt indít, még nem lesz regisztrált eszköze. 

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – irányítópult](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Az Intune-nal kezelheti a munkaerő eszközeit és alkalmazásait, beleértve a vállalati adataik elérését. A mobileszköz-felügyeleti (MDM) szolgáltatás használatához először regisztrálni kell az eszközöket az Intune-ban. Az eszközök regisztrálásakor azok egy MDM-tanúsítványt kapnak. Ez a tanúsítvány az Intune szolgáltatással való kommunikációra szolgál. 

    Több módszer is van a munkaerő eszközeinek Intune-ba való regisztrálására. Az egyes módszerek az eszköz tulajdonlása (személyes vagy vállalati), az eszköz típusa (iOS/iPadOS, Windows, Android) és a felügyeleti követelmények (alaphelyzetbe állítás, affinitás, zárolás) függnek. Az eszközök regisztrálásának engedélyezése előtt azonban be kell állítania az Intune-infrastruktúrát. Különösen fontos, hogy az eszközregisztrációhoz szükség van [saját MDM-szolgáltató beállítására](mdm-authority-set.md). Az Intune-környezet (bérlő) készenléti állapotáról további információt az [Intune beállítása](setup-steps.md)című témakörben talál. Ha elkészült az Intune-Bérlővel, regisztrálhat eszközöket. További információt az eszközregisztrációról a [Mi az eszközregisztrálás?](../enrollment/device-enrollment.md) című témakörben találhat

3. A navigációs ablaktáblán válassza az **eszközök** lehetőséget a regisztrált eszközök adatainak megjelenítéséhez az Intune-bérlőben. 

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és az **eszközök**kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    Az **eszközök – áttekintés** ablaktáblán több lap található, amelyek lehetővé teszik a következő állapotok és riasztások összegzésének megtekintését:
    - **Regisztrációs állapot** – az Intune-ban regisztrált eszközök részleteinek áttekintése platform és beléptetési hibák alapján.
    - **Beléptetési riasztások** – további információ a nem hozzárendelt eszközökről a platform alapján. 
    - **Megfelelőségi állapot** – tekintse át a megfelelőségi állapotot az eszköz, a házirend, a beállítás, a fenyegetések és a védelem alapján. Ezen a panelen a megfelelőségi szabályzat nélküli eszközök listája is elérhető.
    - **Konfigurációs állapot** – az eszközök profiljainak konfigurációs állapotának áttekintése, valamint a profilok telepítése. 
    - **Szoftverfrissítés állapota** – az összes eszközre és minden felhasználóra vonatkozóan az üzembe helyezési állapot vizualizációja látható.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – eszközök](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. Az **eszközök – áttekintés** panelen válassza a **megfelelőségi szabályzatok** lehetőséget az Intune által felügyelt eszközök megfelelőségi adatainak megjelenítéséhez. A következő képhez hasonló részleteket fog látni.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjában – megfelelőségi szabályzatok](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és az **eszközök megfelelőségének**kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    A megfelelőségi követelmények alapvetően szabályok, például az eszköz PIN-kódjának megkövetelése vagy az eszközök titkosításának megkövetelése. Az eszköz megfelelőségi szabályzatai határozzák meg azokat a szabályokat és beállításokat, amelyeket az eszköznek követnie kell a megfelelőség szempontjából. Az eszközök megfelelőségének használatához a következőket kell tennie:
    - Intune és Azure Active Directory (Azure AD) prémium szintű előfizetés
    - Támogatott platformot futtató eszközök
    - Az eszközöket regisztrálni kell az Intune-ban
    - Egy felhasználóhoz vagy elsődleges felhasználóhoz regisztrált eszközök.
    
    További információkért lásd: az [eszközök megfelelőségi szabályzatának első lépései az Intune-ban](../protect/device-compliance-get-started.md).

5. Az **eszközök – áttekintés** panelen válassza a **feltételes hozzáférés** lehetőséget a hozzáférési házirendek részleteinek megjelenítéséhez.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – feltételes hozzáférés](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel, majd a **feltételes hozzáférés**lehetőség kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    A feltételes hozzáférés arra utal, hogy miként szabályozható az e-mailekhez és a vállalati erőforrásokhoz való kapcsolódásra jogosult eszközök és alkalmazások. Az eszköz-és az alkalmazás-alapú feltételes hozzáférés megismeréséhez és az Intune-nal való feltételes hozzáférés használatának gyakori forgatókönyveit lásd: [Mi a feltételes hozzáférés?](../protect/conditional-access.md)

6. A navigációs ablaktáblán válassza az **eszközök** > **konfigurációs profilok** elemet az Intune-beli eszközbeállítások részleteinek megjelenítéséhez.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – konfigurációs profilok](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel, majd az **eszköz konfigurációjának**kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    Az Intune olyan beállításokat és funkciókat kínál, amelyeket Ön engedélyezhet vagy letilthat a vállalatához tartozó különböző eszközökön. Ezek a beállítások és funkciók hozzáadódnak a "konfigurációs profilokhoz". Létrehozhat profilokat különböző eszközökhöz és különböző platformokhoz, például iOS/iPadOS, Android, macOS és Windows rendszerekhez. Ezt követően az Intune használatával alkalmazhatja a profilt a szervezet eszközeire.   

    Az eszköz konfigurációjával kapcsolatos további információkért lásd: a [szolgáltatások beállításainak alkalmazása az eszközökön a Microsoft Intune eszköz profiljainak használatával](../configuration/device-profiles.md).

7. A navigációs ablaktáblán válassza az **eszközök** > **minden eszköz** lehetőséget az Intune-bérlő regisztrált eszközeivel kapcsolatos részletek megjelenítéséhez. Ha új Intune-bejegyzést indít, akkor még nem lesz regisztrált eszköze.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központról – minden eszköz](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    Az eszközök listája a megfelelőséggel, az operációs rendszer verziójával és az utolsó beadási dátummal kapcsolatos legfontosabb adatokat jeleníti meg.

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és az **eszközök** > **minden eszköz**elem kiválasztásával megtalálta a fenti adatokat a Azure Portalban.
 
8. A navigációs panelen válassza az **alkalmazások** lehetőséget az alkalmazás állapotának áttekintéséhez. Ez az ablaktábla a következő lapokon alapuló alkalmazás-telepítési állapotot nyújtja:

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és az **ügyfélalkalmazások**kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    Az **alkalmazások – áttekintés** ablaktáblán két lap jelenik meg, amelyek lehetővé teszik a következő állapotok összegzésének megtekintését:
    - **Telepítési állapot** – a legfontosabb telepítési hibák megtekintése eszköz szerint, valamint a telepítési hibákkal rendelkező alkalmazások.  
    - Az **alkalmazás védelmi házirendjének állapota** – részletes információkat talál a hozzárendelt felhasználókról az alkalmazás-védelmi szabályzatokhoz és a megjelölt felhasználókhoz.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – alkalmazások](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    A rendszergazdák a Microsoft Intune használatával kezelhetik a cég által használt ügyfélalkalmazásokat. Ez a funkció az eszközkezelési és adatvédelmi funkciókat egészíti ki. A rendszergazdák egyik elsődleges feladata annak biztosítása, hogy a végfelhasználók hozzáférjenek a munkájukhoz szükséges alkalmazásokhoz. Emellett előfordulhat, hogy az Intune-ban nem regisztrált eszközökön található alkalmazásokat is szeretne hozzárendelni és felügyelni. Az Intune számos szolgáltatást kínál a szükséges alkalmazások kívánt eszközökön való használatához. 

    > [!NOTE]
    > Az **alkalmazások – áttekintés** ablaktábla a bérlői állapotot és a fiók részleteit is tartalmazza.

    Az alkalmazások hozzáadásával és hozzárendelésével kapcsolatos további információkért lásd: [Alkalmazások hozzáadása Microsoft Intune](../apps/apps-add.md) és [alkalmazások társítása a csoportokhoz a Microsoft Intune használatával](../apps/apps-deploy.md).

9. Az **alkalmazások – áttekintés** panelen válassza a **minden alkalmazás** lehetőséget az Intune-hoz hozzáadott alkalmazások listájának megtekintéséhez.

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és az **ügyfélalkalmazások** > **alkalmazások**lehetőség kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    Az Intune-platformon alapuló különböző típusú alkalmazások is hozzáadhatók. Miután hozzáadta az alkalmazást, hozzárendelheti a felhasználói csoportokhoz. 

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központról – minden alkalmazás](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    További információt az [Alkalmazások hozzáadása a Microsoft Intune-hoz](~/apps/apps-add.md) című cikkben talál. 

10. A navigációs panelen válassza a **felhasználók** lehetőséget az Intune-ban található felhasználók részletes adatainak megjelenítéséhez. Ezek a felhasználók a vállalat munkaereje.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – felhasználók](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és a **felhasználók**kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    Hozzáadhat felhasználókat közvetlenül az Intune-hoz, vagy szinkronizálhat felhasználókat a helyszíni Active Directoryról. Ha felvették a felhasználókat a szolgáltatásba, regisztrálhatják az eszközeiket, és elérhetik a vállalati erőforrásokat. Emellett további engedélyeket is biztosíthat a felhasználóknak az Intune eléréséhez. További információ: [felhasználók hozzáadása és rendszergazdai engedély biztosítása az Intune-hoz](users-add.md).

11. A navigációs ablaktáblán válassza a **csoportok** lehetőséget az Intune-ban található Azure Active Directory-(Azure ad-) csoportok részleteinek megjelenítéséhez. Intune-rendszergazdaként csoportok használatával kezelheti az eszközöket és a felhasználókat.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központról – csoportok](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és a **csoportok**kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    A szervezeti igényeknek megfelelő csoportokat is beállíthat. Létrehozhat csoportokat a felhasználók és eszközök földrajzi hely, részleg vagy hardverjellemzők szerinti rendezéséhez. Használjon csoportokat a feladatok nagy számban való végrehajtásához. Beállíthatja például, hogy a szabályzatok számos felhasználóhoz legyenek beállítva, vagy alkalmazásokat telepítsenek egy adott eszközre. A csoportokkal kapcsolatos további információkért lásd: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](../groups-add.md).

12. A navigációs ablaktáblán válassza a **bérlői felügyelet** lehetőséget az Intune-bérlő részleteinek megjelenítéséhez.

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és a **bérlői állapot**kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    A **bérlői rendszergazda – bérlő állapota** panel a **bérlői adatok**, az **összekötő állapota**és a **szolgáltatás állapota irányítópult**lapjait tartalmazza. Ha a Bérlővel vagy az Intune-nal kapcsolatban bármilyen probléma merül fel, akkor az ezen a panelen elérhető részleteket fogja megtalálni. 

    ![A Microsoft Endpoint Manager felügyeleti központ – bérlői állapot képernyőképe](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    További információ: az [Intune-bérlő állapota](../tenant-status.md).

13. A navigációs ablaktáblán válassza a **Hibaelhárítás + támogatás** > **Hibaelhárítás** lehetőséget egy adott felhasználó állapotának megtekintéséhez. 

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel és a **hibakeresési**lehetőség választásával megtalálta a fenti adatokat a Azure Portalban.

    A **hozzárendelések** legördülő listából kiválaszthatja, hogy megtekintheti-e az ügyfélalkalmazások, a házirendek, a frissítési gyűrűk és a regisztrációs korlátozások megcélozta hozzárendeléseit. Ezen a panelen az eszköz adatait, az alkalmazások védelmi állapotát és az adott felhasználó regisztrálási hibáit is megtalálhatja.

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – problémamegoldás](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    További információ az Intune-on belüli hibaelhárításról: [a hibaelhárítási portál használata a felhasználóknak a vállalatnál](../help-desk-operators.md).

14. A navigációs ablaktáblán kattintson a **Hibaelhárítás + támogatás** > **Súgó és támogatás** lehetőségre a Súgó kéréséhez. 

    > [!TIP]
    > Ha korábban már használta az Intune-t a Azure Portalban, az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéssel, majd a **Súgó és támogatás**lehetőség kiválasztásával megtalálta a fenti adatokat a Azure Portalban.

    Rendszergazdaként a **Súgó és támogatás** lehetőséget használhatja a megoldások keresésére és megtekintésére, valamint az Intune-hoz kapcsolódó online támogatási jegy beszerzésére. 

    ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – Súgó és támogatás](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Támogatási jegy létrehozásához a fiókot rendszergazdai szerepkörként kell hozzárendelni a Azure Active Directory-ben. Rendszergazdai szerepkörök: **Intune-rendszergazda**, **globális rendszergazda**és **szolgáltatás-rendszergazda**. 

    További információkért lásd: [a Microsoft Intune támogatásának beszerzése](../get-support.md).

15. A navigációs ablaktáblán válassza a **Hibaelhárítás + támogatás** > **interaktív forgatókönyvek** lehetőséget az elérhető Intune interaktív forgatókönyvek megjelenítéséhez. 

    Az interaktív forgatókönyvek egy teljes körű használati esethez igazított lépések testreszabott sorozata. A gyakori forgatókönyvek a szervezeten belüli rendszergazda, felhasználó vagy eszköz szerepkörén alapulnak. Ezek a szerepkörök általában gondosan előkészített profilok, beállítások, alkalmazások és biztonsági vezérlők gyűjteményét igénylik, hogy a lehető legjobb felhasználói élményt és biztonságot nyújtsanak.

    Ha nem ismeri az adott Intune-forgatókönyv megvalósításához szükséges összes lépést és erőforrást, akkor a kiindulási pontként az interaktív forgatókönyvek is használhatók. 

    ![Képernyőkép a Microsoft Endpoint Manager felügyeleti központjáról – interaktív forgatókönyvek](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    További információ az irányított forgatókönyvekről: [irányított forgatókönyvek – áttekintés](~/fundamentals/guided-scenarios-overview.md).

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>A Microsoft Endpoint Manager felügyeleti központ konfigurálása

Az Azure segítségével testreszabhatja és konfigurálhatja a portál nézetét.

### <a name="change-the-dashboard"></a>Az irányítópult módosítása

Az **irányítópulton** megtekintheti az Intune-bérlőben található eszközök és ügyfélalkalmazások általános részleteit. Az irányítópultok lehetővé teszik, hogy a Microsoft Endpoint Manager felügyeleti központban hozzon létre egy koncentrált és szervezett nézetet. Az irányítópultokat munkaterületként használhatja, ahol gyorsan elindíthatja a napi műveletek feladatait, és figyelheti az erőforrásokat. Egyéni irányítópultokat hozhat létre a projektek, feladatok vagy felhasználói szerepkörök alapján, például:. A Microsoft Endpoint Manager felügyeleti központ kiindulási pontként biztosít alapértelmezett irányítópultot. Szerkesztheti az alapértelmezett irányítópultot, létrehozhat és testreszabhat további irányítópultokat, és közzéteheti és megoszthatja az irányítópultokat, hogy azok elérhetők legyenek más felhasználók számára. 

   ![Képernyőfelvétel a Microsoft Endpoint Manager felügyeleti központjáról – irányítópult](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Az aktuális irányítópult módosításához válassza a **Szerkesztés**lehetőséget. Ha nem szeretné módosítani az alapértelmezett irányítópultot, létrehozhat egy **új irányítópultot** is. Új irányítópult létrehozásakor egy üres saját irányítópultot kap **Csempetárral**, amelyen új csempéket vehet fel és átrendezheti a csempéket. A csempék kategória vagy erőforrástípus alapján is megtalálhatók. Kereshet adott csempéket is. Válassza ki **az irányítópultot** a meglévő egyéni irányítópultok kiválasztásához.

### <a name="change-the-portal-settings"></a>A portál beállításainak módosítása

A Microsoft Endpoint Manager felügyeleti központot az alapértelmezett nézet, a téma, a hitelesítő adatok időtúllépési ideje, valamint a nyelvi és területi beállítások lehetőség kiválasztásával szabhatja testre.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>További lépések

A Microsoft Intune gyors futtatásához lépjen az Intune rövid útmutatói között az ingyenes Intune-fiók beállításával.

> [!div class="nextstepaction"]
> [Rövid útmutató: próbálja ki Microsoft Intune ingyen](free-trial-sign-up.md)
