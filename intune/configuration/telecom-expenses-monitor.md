---
title: Távközlési költségek kezelésére szolgáló szolgáltatás beállítása Microsoft Intune-Azure-ban | Microsoft Docs
titleSuffix: ''
description: A Microsoft Intune integrálása a Saaswedo Telecom költségelszámolás szolgáltatásával az adatok használatának monitorozásához, valamint a küszöbértékek és korlátok beállításához Android és iOS rendszerű eszközökön.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 340659adfa3bbd40f98ccec9d8d44e952f7ec9b9
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059932"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Távközlésiköltség-kezelő szolgáltatás beállítása az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune-nal kezelheti a távközlési költségeket a szervezet tulajdonában lévő mobileszközök adatfelhasználásával kapcsolatban. Az Intune integrálható a Saaswedo [Datalert telekommunikációs költségeinek kezelésével](http://datalert.biz/get-started). A Datalert egy valós idejű, távközlési költségek kezelésére szolgáló megoldás, amely a távközlési adatok használatát kezeli. Segít elkerülni az Intune által felügyelt eszközök költséges és váratlan adatátviteli és barangolási díját.

A Datalert-integráció a barangolási és a belső adathasználati korlátokat is beállíthatja, figyelheti és kényszerítheti. Ha a korlátok meghaladják a meghatározott küszöbértékeket, a rendszer automatikusan elindítja a riasztásokat. A szolgáltatást úgy is beállíthatja, hogy különböző műveleteket alkalmazzon, például letiltsa a barangolást, vagy meghaladja a küszöbértéket magánszemélyek vagy csoportok számára. A Datalert felügyeleti konzol olyan jelentéseket tartalmaz, amelyek az adatfelhasználást és a figyelési információkat tartalmazzák.

Az alábbi képen látható, hogyan integrálható az Intune a Datalert:

  ![Az Intune és a Datalert integrációját bemutató ábra](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

A Datalert szolgáltatás Intune-nal való használatához bizonyos konfigurációs beállítások vannak a Datalert és az Intune-ban. Ez a cikk a következőkhöz nyújt útmutatást:

- Konfigurálja a beállításokat a Datalert-konzolon a Datalert szolgáltatás Intune-hoz való összekapcsolásához.
- Erősítse meg, hogy ez a hálózat aktív, és engedélyezve van az Intune-ban.
- Az Intune használatával adja hozzá a Datalert alkalmazást az eszközökhöz.
- Kapcsolja ki a Datalert szolgáltatást és az Intune-t (opcionális).

## <a name="supported-platforms"></a>Támogatott platformok

- Android 4,4 és újabb, Knox-kompatibilis eszközök (Samsung)

  A Knox-t [támogató Android-verziók](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (a Samsung webhelyén nyílik meg) a Knox által támogatott verziókat listázza.

- iOS 8.0 és újabb verziók

## <a name="prerequisites"></a>Előfeltételek

- Előfizetés Microsoft Intunera és hozzáférés a [Microsoft Endpoint Manager felügyeleti központjához](https://go.microsoft.com/fwlink/?linkid=2109431)
- [Datalert](http://www.datalert.biz/) -előfizetés (megnyílik a Datalert webhely)

## <a name="telecom-expense-management-providers"></a>Távközlési költségek kezelése szolgáltatók

Az Intune a következő telekommunikációs felügyeleti szolgáltatóval integrálódik:

- [Saaswedo Datalert Telecom-költségek kezelése szolgáltatás](http://www.datalert.biz/) (megnyitja a Datalert webhelyét)

## <a name="deploy-the-intune-and-datalert-solution"></a>Az Intune és a Datalert megoldás üzembe helyezése

### <a name="step-1-connect-the-datalert-service-to-intune"></a>1\. lépés: a Datalert szolgáltatás összekötése az Intune-nal

1. Jelentkezzen be a Datalert felügyeleti konzolba rendszergazdai hitelesítő adatokkal.

2. A konzolon lépjen a **Beállítások** lapra > **Mdm konfigurációjában**.

3. Válassza a **Letiltás feloldása**lehetőséget. A **tiltás feloldásával** módosíthatja vagy frissítheti a lapon lévő beállításokat.

4. Az **Intune/Datalert-kapcsolatok** > **kiszolgáló Mdm**területen válassza a **Microsoft Intune**lehetőséget.

5. **Azure ad-tartomány**esetén adja meg az Azure-beli BÉRLŐi azonosítóját. Válassza a **kapcsolatok**lehetőséget.

    Ha a **Csatlakozás**lehetőséget választja, a Datalert szolgáltatás ellenőrzi az Intune-ban. Ellenőrzi, hogy nincsenek-e meglévő Datalert-kapcsolatok. Néhány pillanat elteltével megjelenik egy Microsoft bejelentkezési oldal, amelyet a Datalert Azure-hitelesítés követ.

6. A Microsoft hitelesítési oldalán válassza az **Elfogadás** lehetőséget.

    A rendszer átirányítja **egy Datalert,** amely néhány pillanat múlva bezárul. A Datalert ellenőrzi a kapcsolódást, és az érvényesített elemek mellett zöld pipa jeleket jelenít meg. Ha az érvényesítés sikertelen, piros színnel jelenik meg. Segítségért forduljon a Datalert támogatási szolgálatához.

    A következő képen a zöld pipa jelzi, amikor a kapcsolódás sikeres:

      ![A Datalert sikeres csatlakozást jelző lapja](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. A **Datalert-alkalmazás/ADAL-beleegyezett**beállításnál állítsa be a kapcsolót **a**következőre:. A Microsoft hitelesítési oldalán válassza az **Elfogadás** lehetőséget.

    A rendszer átirányítja **egy Datalert,** amely néhány pillanat múlva bezárul. A Datalert ellenőrzi a kapcsolódást, és az érvényesített elemek mellett zöld pipa jeleket jelenít meg. Ha az érvényesítés sikertelen, piros színnel jelenik meg. Segítségért forduljon a Datalert támogatási szolgálatához.

    A következő képen a zöld pipa jelzi, amikor a kapcsolódás sikeres:

      ![A Datalert sikeres csatlakozást jelző lapja](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. A **Mdm-profilok kezelése (nem kötelező)** beállításnál állítsa be a kapcsolót **a**következőre:. Ez a beállítás lehetővé teszi, hogy a Datalert beolvassa a rendelkezésre álló profilokat az Intune-ban a házirendek beállításának elősegítése érdekében. 

    A Microsoft hitelesítési oldalán válassza az **Elfogadás** lehetőséget.

    A rendszer átirányítja **egy Datalert,** amely néhány pillanat múlva bezárul. A Datalert ellenőrzi a kapcsolódást, és az érvényesített elemek mellett zöld pipa jeleket jelenít meg. Ha az érvényesítés sikertelen, piros színnel jelenik meg. Segítségért forduljon a Datalert támogatási szolgálatához.

    A következő képen a zöld pipa jelzi, amikor a kapcsolódás sikeres:

   ![A Datalert sikeres csatlakozást jelző lapja](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>2\. lépés: a távközlési költségek kezelésének megerősítése aktív az Intune-ban

Az 1. lépés elvégzése után a rendszer automatikusan engedélyezi a hozzáférést. Az Intune-ban a kapcsolatok állapota **aktív**. A következő lépések végrehajtásával ellenőrizheti, hogy az állapot aktív-e:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** > **távközlési költségek kezelése**lehetőséget. Az **aktív** kapcsolatok állapotának megkeresése:

   ![Az Intune oldala, rajta az Aktív állapotú Datalert-kapcsolattal](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>3\. lépés: a Datalert alkalmazás üzembe helyezése az eszközökön

Annak ellenőrzéséhez, hogy a csak a szervezet által birtokolt sorokból származó adatfelhasználást gyűjti-e be, ügyeljen arra, hogy:

- Eszközök kategóriáinak létrehozása az Intune-ban.
- Célozza meg a Datalert alkalmazást csak szervezeti telefonokra.

Ez a szakasz ezeket a lépéseket sorolja fel.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>A kategóriákhoz hozzárendelt eszközök és csoportok létrehozása

A szervezeti igényektől függően hozzon létre legalább két eszközcsoport-kategóriát, például a vállalati és a személyes eszközöket. Ezután hozzon létre dinamikus eszközcsoportokat minden kategóriához. Szükség esetén több kategóriát is létrehozhat a szervezet számára.

Ha eszközöket szeretne létrehozni az Intune-ban, tekintse meg az [eszközök hozzárendelése csoportokhoz](../enrollment/device-group-mapping.md)című témakört.

Ezek a kategóriák a felhasználók számára jelennek meg a regisztráció során ([Android-eszközök regisztrálása](../enrollment/android-enroll.md)). Attól függően, hogy a felhasználók milyen kategóriába tartoznak, a regisztrált eszköz átkerül a megfelelő eszköz csoportba.

  ![Képernyőkép a Szabályzat hozzáadása panelről](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>A Datalert alkalmazás hozzáadása az Intune-hoz

A következő lépésekkel adja hozzá a Datalert alkalmazást. Példaként használja az iOS-t. [Alkalmazások hozzáadása](../apps/apps-add.md) és a [hatókör-címkék használata](../fundamentals/scope-tags.md) részletesebb információkat tartalmaz ezekről a lépésekről.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.

2. Válassza ki az **alkalmazás típusát**. IOS esetében például válassza az **áruházbeli alkalmazás-iOS**lehetőséget.

3. A **Keresés az App Store**-ban írja be a **Datalert** kifejezést a Datalert alkalmazás megkereséséhez.

4. Válassza ki a **Datalert** alkalmazást > **válassza ki**:

   ![A datalert alkalmazás hozzáadása az App Store áruházból az Intune-ügyfélalkalmazásokba](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Adja meg a további tulajdonságokat, például az alkalmazás adatait és a hatókör címkéit:

   ![Adja meg az alkalmazás tulajdonságait, beleértve a nevet, a leírást, az operációs rendszer és az Intune további beállításait.](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. A módosítások mentéséhez kattintson **az OK** > **Hozzáadás** gombra. A Datalert alkalmazás megjelenik a listában.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>A Datalert alkalmazás hozzárendelése a vállalati eszközök csoportjához

1. Az **alkalmazások** > **minden alkalmazás**területen válassza ki az előző lépésben hozzáadott Datalert alkalmazást.

2. Válassza a **hozzárendelések** > **Csoport hozzáadása**lehetőséget. Válassza ki az alkalmazás hozzárendelésének módját. Az [alkalmazásoknak az Intune-beli csoportokhoz való hozzárendelésével](../apps/apps-deploy.md) kapcsolatos további részletek a beállításokról.

    Ezekben a lépésekben az alkalmazás telepítésének megkezdéséhez vagy a csoport számára kötelezővé tételéhez kell választania. Az alábbi példa a szükséges telepítést mutatja be. Ha szükséges, a felhasználóknak telepíteniük kell a Datalert alkalmazást az eszköz regisztrálása után.

   ![Képernyőkép a Szabályzat hozzáadása panelről](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>4\. lépés: szervezeti telefonos sorok hozzáadása a Datalert-konzolhoz

Az Intune és a Datalert Services mostantól az egymással való kommunikációra van konfigurálva. Ezután adja hozzá a szervezete fizetős telefonvonalait a Datalert-konzolhoz. Továbbá adja meg a küszöbértékeket és műveleteket a mobil-vagy barangolásos használati szabálysértések esetében. Manuálisan is hozzáadhat vállalati fizetős telefonvonalat a Datalert-konzolhoz, vagy automatikusan hozzáadhatja őket az Intune-ban regisztrált eszköz után.

Az elemek beállításához nyissa meg a [Datalert-telepítőt Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (megnyílik a Datalert webhely). A **Beállítások** lapon kövesse a telepítési varázsló lépéseit.

  ![Képernyőkép a Szabályzat hozzáadása panelről](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

A Datalert szolgáltatás most aktív. Megkezdi az adathasználat figyelését, és letiltja a mobil-és barangoló adatokat olyan eszközökön, amelyek túllépik a beállított használati korlátot.

## <a name="end-user-enrollment"></a>Végfelhasználói regisztráció

A végfelhasználói élmény érdekében a következő cikkek segíthetnek:

- [iOS-eszköz regisztrálása a távközlésiköltség-kezelőben](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Android-eszköz regisztrálása a távközlésiköltség-kezelőben](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>A Datalert szolgáltatás kikapcsolása

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **bérlői felügyelet** > **összekötők és tokenek** > **távközlési költségek kezelése**lehetőséget.
2. Állítsa be **a távközlési költségek kezelése lehetőséget, és tiltsa le a mobil-vagy barangolási adatokat olyan eszközökön, amelyek túllépik** a **letiltani**kívánt használati kvótákat.
3. **Mentse** a változtatásokat.

> [!IMPORTANT]
> Ha letiltja a Datalert szolgáltatást az Intune-ban:
>
> - Az eszközökre alkalmazott összes művelet a használati korlátok múltbeli megsértése miatt nem vonható vissza.
> - A felhasználók számára ettől kezdve nincs letiltva az adathozzáférés és a roaming.
> - Az Intune továbbra is megkapja a szolgáltatástól érkező jeleket, de az Intune figyelmen kívül hagyja a jeleket.

## <a name="next-steps"></a>További lépések

Az adatfelhasználási jelentéskészítés a Saaswedo Datalert felügyeleti konzolján érhető el.
