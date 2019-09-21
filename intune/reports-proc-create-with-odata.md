---
title: Intune-jelentés létrehozása a OData-hírcsatornából Power BI
titleSuffix: Microsoft Intune
description: Fatérkép-diagram létrehozása a Power BI Desktop használatával, az Intune-adattárház API-ból származó interaktív szűrővel.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4494d5f75336f7152668cfa1bb6fa1cd1a94305c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167858"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Intune-jelentés létrehozása a OData-hírcsatornából Power BI

Ez a cikk azt ismerteti, hogyan hozhat létre fatérkép vizualizációt az Intune-adatairól, ha a felhasználók egy interaktív szűrőt Power BI Desktopanak. A pénzügyi vezető például tudni szeretné, hogyan hasonlítják össze az eszközök összesített eloszlását a vállalati tulajdonú eszközök és a személyes eszközök között. A fatérkép-diagram megmutatja az eszköztípusok teljes számát. Látható benne, hogy hány iOS-es, hány androidos és hány windowsos eszköz van vállalati, és hány személyes tulajdonban.

## <a name="overview-of-creating-the-chart"></a>A diagram létrehozásának áttekintése

A diagram létrehozásához az alábbi lépéseket fogja elvégezni:
1. A Power BI Desktop telepítése, ha még nincs telepítve.
2. Csatlakozás az Intune-adattárház adatmodellhez, és a modell aktuális adatainak letöltése.
3. Az adatmodell kapcsolatainak létrehozása és kezelése.
4. Diagram létrehozása az **eszközök** tábla adataiból.
5. Interaktív szűrő létrehozása.
6. Az elkészült diagram megtekintése.

### <a name="a-note-about-tables-and-entities"></a>Megjegyzés a táblákhoz és az entitásokhoz

A Power BI-ban táblákkal kell dolgozni. A táblák adatmezőket tartalmaznak. Minden adatmező adott adattípussal rendelkezik. A mező kizárólag az adott adattípusba tartozó adatokat tartalmazhat. Az adattípus lehet szám, szöveg, dátum és így tovább. Miután betöltötte a modellt, a Power BI táblái feltöltődnek a bérlőből származó friss időbeli adatokkal. Noha a konkrét adat idővel megváltozhat, a táblaszerkezet nem változik, hacsak az alapul szolgáló adatmodellt nem frissítik.

Az *entitás* és a *tábla* kifejezések eleinte zavart okozhatnak. Az adatmodell elérhető egy OData (Open adatprotokoll) adatcsatornán keresztül. Azt a tárolót, amelyet az OData használatánál entitásnak nevezünk, a Power BI használatánál táblának hívjuk. Mindkét kifejezés arra a dologra vonatkozik, amely az adatokat tartalmazza. További információ a OData: a [OData áttekintése](/odata/overview).

## <a name="install-power-bi-desktop"></a>A Power BI Desktop telepítése

Telepítse a Power BI Desktop legújabb verzióját. Power BI Desktop a következő címről tölthető le: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Csatlakozás a bérlőhöz tartozó Intune-adattárház OData-adatcsatornájához

> [!Note]  
> Az Intune-beli **Jelentések** eléréséhez hozzáférési engedélyre van szükség. További információt az [Engedélyezés](reports-api-url.md) témakörben talál.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Nyissa meg az **Intune** -adattárház panelt az adatraktár hivatkozásának kiválasztásával az **Microsoft Intune – áttekintés** panel jobb oldalán található **egyéb feladatok** területen.
3. Másolja az egyéni URL-címet. Például:`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Nyissa meg a Power BI Desktop alkalmazást.
5. A menüsávon válassza a **fájl** >  > **adatok beolvasása** **OData-hírcsatorna**lehetőséget.
6. Illessze be az egyéni hírcsatorna URL-címét, amelyet a korábbi lépésből másolt be a OData- **hírcsatorna** ablakának URL mezőjébe.
7. Válassza az **Alapszintű** lehetőséget.

    ![OData-hírcsatorna a bérlőhöz tartozó Intune-adattárházhoz](media/reports-create-01-odatafeed.png)

8. Kattintson az **OK** gombra.
9. Válassza a **Szervezeti fiók** lehetőséget, és jelentkezzen be az Intune-hoz tartozó hitelesítő adataival.

    ![Szervezeti fiók hitelesítő adatai](media/reports-create-02-org-account.png)

10. Kattintson a **Csatlakozás** gombra. Ekkor megnyílik a Navigátor, és megjelenik rajta az Intune-adattárházban található táblák listája.

    ![Képernyőfelvétel a Navigátorról – az adatraktár tábláinak listája](media/reports-create-02-loadentities.png)

11. Válassza ki a **devices** (eszközök) és az **ownerTypes** (tulajdonostípusok) táblákat.  Válassza a **Betöltés** lehetőséget. A Power BI betölti az adatokat a modellbe.

## <a name="create-a-relationship"></a>Kapcsolat létrehozása

Nem csak egyetlen tábla adatait, de több táblát is importálhat, és így egyszerre több tábla összekapcsolt adatait is elemezheti. Power BI tartalmaz egy **automatikus észlelési** funkciót, amely megpróbálja megkeresni és létrehozni a kapcsolatokat. Az adattárház táblái úgy lettek felépítve, hogy működjenek a Power BI automatikus észlelés funkciójával. Ha azonban Power BI nem találja meg automatikusan a kapcsolatokat, továbbra is kezelheti a kapcsolatokat.

![Kapcsolódó adatkapcsolatok kezelése táblák között](media/reports-create-03-managerelationships.png)

1. Válassza a **Kapcsolatok kezelése** lehetőséget.
2. Válassza az **automatikus észlelés lehetőséget...** ha a Power bi még nem észlelte a kapcsolatokat.

A kapcsolatokat egy From (forrás) és egy To (cél) oszlopban láthatja. Ebben a példában az **eszközök** tábla **ownerTypeKey** adatmezőjéből indul kapcsolat az **ownerTypes** tábla **ownerTypeKey** mezőjébe. A kapcsolat használatával megkeresheti az eszköz típus kódjának egyszerű nevét az **eszközök** táblában.

## <a name="create-a-treemap-visualization"></a>Fatérkép-diagram létrehozása

A fatérkép diagramon a hierarchikus adatmezők a mezőkön belül találhatók. A hierarchia minden ága egy négyzet, amely alágakat reprezentáló kisebb négyzeteket tartalmaz. A Power BI Desktop használatával létrehozhat egy fatérkép az Intune-bérlői adataihoz, amely az eszköz gyártójának relatív mennyiségét mutatja.

![Power BI fatérkép vizualizációk](media/reports-create-03-treemap.png)

1. A **vizualizációk** ablaktáblán keresse meg és válassza ki a **fatérkép**. A **fatérkép** diagramot a rendszer hozzáadja a jelentés vászonhoz.
2. A **mezők** ablaktáblán keresse meg a `devices` táblázatot.
3. Bontsa `devices` ki a táblázatot, `manufacturer` és válassza ki az adatmezőt.
4. Húzza az `manufacturer` adatmezőt a jelentés vászonra, és dobja el a **fatérkép** diagramon.
5. Húzza az `deviceKey` adatmezőt a `devices` táblázatból a **vizualizációk** panelre, és az **értékek** szakaszban adja meg az **adatmezők hozzáadása mezőt**.  

Ezzel elkészített egy olyan vizualizációt, amely megmutatja, hogy milyen a szervezetben az eszközök gyártók szerinti eloszlása.

![Fatérkép az adatmennyiséggel – az eszközök gyártóinak eloszlása](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Szűrő hozzáadása

A fatérkép-diagramhoz szűrőt is hozzáadhat, hogy az további kérdésekre is választ tudjon adni az alkalmazással.

1. Szűrő hozzáadásához jelölje ki a jelentés vászonját, majd válassza a **szeletelő ikont** (![fatérkép adatmodellel és támogatott kapcsolatokkal](media/reports-create-slicer.png)) a **vizualizációk**alatt. Ekkor megjelenik az üres **szeletelő** vizualizációja a vásznon.
2. A **mezők** ablaktáblán keresse meg a `ownerTypes` táblázatot.
3. Bontsa `ownerTypes` ki a táblázatot, `ownerTypeName` és válassza ki az adatmezőt.
4. Húzza az `onwerTypeName` adatmezőt a `ownerTypes` táblázatból a **szűrők** panelre, és a **szűrők ezen az oldalon** szakaszban az **adatmezők hozzáadása**feliratú mezőbe.  

   A `OwnerTypes` táblázat alatt található egy nevű `OwnerTypeKey`adatmező, amely az adott eszköz vállalati tulajdonú vagy személyes adatát tartalmazza. Mivel ebben a szűrőben szeretné megjeleníteni a felhasználóbarát neveket, keresse meg a `ownerTypes` táblázatot, és húzza a **ownerTypeName** a szeletelőbe. Ebből a példából láthatja, hogyan támogatja az adatmodell a táblák közötti kapcsolatokat.

![Fatérkép szűrővel – a táblák közötti kapcsolatok támogatása](media/reports-create-08_ownertype.png)

Ezzel létrehozott egy olyan interaktív szűrőt, amelyben egyszerű váltással megtekinthetők a vállalati és a személyes tulajdonú eszközök. Ezzel a szűrővel megtekintheti az eloszlás változásait.

1. A szeletelőben válassza a **vállalat** lehetőséget, hogy megtekintse a vállalat tulajdonában lévő eszközök eloszlását.
2. A **személyes** tulajdonban lévő eszközök megjelenítéséhez válassza a Personal (személyes) lehetőséget a szeletelőn belül.

## <a name="next-steps"></a>További lépések

- Olvassa el a Power BI dokumentációjában, hogyan [hozhatók létre és hogyan kezelhetők kapcsolatok](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) a Power BI Desktopban.
- Ismerkedjen meg az [Intune-adattárház modelljével](reports-ref-data-model.md).
