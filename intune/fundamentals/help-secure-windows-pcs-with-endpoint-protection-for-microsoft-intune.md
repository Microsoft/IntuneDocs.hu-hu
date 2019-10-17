---
title: Endpoint Protection Windows rendszerű számítógépekhez
titleSuffix: Microsoft Intune
description: Biztonságossá teheti felügyelt számítógépeit az Endpoint Protection használatával, amely valós idejű védelmet biztosít a kártevők ellen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 535ae4dd986940da17d247136b37185cfaa58b57
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510222"
---
# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

A Microsoft Intune Endpoint Protection valós idejű védelmet biztosít a kártevőkkel szemben, naprakészen tartja a kártevő-definíciókat, és automatikusan átvizsgálja a számítógépeket. Segítségével biztonságossá teheti felügyelt számítógépeit. Az Endpoint Protection olyan eszközöket is biztosít, amelyek segítenek kezelni és megfigyelni a kártékony programok támadásait.

Ha még nem telepítette az Intune-ügyfelet a számítógépeken, [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](install-the-windows-pc-client-with-microsoft-intune.md) című témakörben olvashat erről.

Az alábbi szakaszokban található információk segítségével konfigurálhatja, telepítheti és figyelheti az Endpoint Protection szolgáltatást.

## <a name="choose-when-to-use-endpoint-protection"></a>Mikor ajánlott az Endpoint Protection használata?
Rendszergazdaként egyik legfontosabb feladata, hogy biztosítsa, hogy az Ön által felügyelt számítógépek vírusoktól és rosszindulatú szoftverektől mentesek legyenek. Mielőtt telepíti az Intune-t a szervezet Windows rendszerű számítógépeire, az alábbi lehetőségek egyikének kiválasztásával és az ahhoz tartozó házirend-beállítások konfigurálásával meg kell határoznia, hogyan védi meg a számítógépeket:


|                                                                                                                                                                       Válasszon:                                                                                                                                                                        |                                                                                                       Endpoint Protection házirend-beállításai                                                                                                        |                                                                                                                                                  További információ                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                             A Microsoft Intune Endpoint Protection használata csak akkor, ha nincs telepítve külső gyártó végpontvédelmi alkalmazása.<br /><br />A Microsoft Intune Endpoint Protectiont az összes olyan számítógépen használhatja, amelyen nincs telepítve külső gyártó végpontvédelmi alkalmazása.                                              | Endpoint Protection telepítése = <strong>Igen</strong><br /><br />Endpoint Protection engedélyezése = <strong>Igen</strong><br /><br />Az Endpoint Protection telepítése akkor is, ha egy külső gyártó végpontvédelmi alkalmazása telepítve van = <strong>Nem</strong>  |                                                                      Ha a rendszer egy külső gyártótól származó végpontvédelmi alkalmazást észlel, nem telepíti a Microsoft Intune Endpoint Protectiont, illetve eltávolítja, ha már telepítve van.                                                                       |
| A Microsoft Intune Endpoint Protectiont ugyanakkor abban az esetben is használhatja, ha telepítve van külső gyártó végpontvédelmi alkalmazása.<br /><br />Ha ezt a módszert használja, a Microsoft Intune Endpoint Protection és a külső gyártótól származó végpontvédelmi alkalmazás egyidejűleg fog futni. A lehetséges teljesítményproblémák miatt ez a konfiguráció nem ajánlott. | Endpoint Protection telepítése = <strong>Igen</strong><br /><br />Endpoint Protection engedélyezése = <strong>Igen</strong><br /><br />Az Endpoint Protection telepítése akkor is, ha egy külső gyártó végpontvédelmi alkalmazása telepítve van = <strong>Igen</strong> |                        A következő esetekben használja:<br /><br />– Át szeretne térni a Microsoft Intune Endpoint Protection használatára.<br />– Új ügyfelet telepít, amely a Microsoft Intune Endpoint Protectiont fogja használni.<br />– Olyan ügyfelet frissít, amely a Microsoft Intune Endpoint Protectiont fogja használni.                         |
|                                                                                                             Az Intune használata a Microsoft Intune Endpoint Protection nélkül Ehelyett egy külső gyártó végpontvédelmi alkalmazását fogja alkalmazni.                                                                                                             |                                                                                                Endpoint Protection telepítése = <strong>Nem</strong>                                                                                                 | Ha nem használ külső gyártótól származó végpontvédelmi alkalmazást, ez a konfiguráció nem ajánlott, mivel kártevő szoftvereknek vagy más támadásoknak teheti ki a szervezet számítógépeit.<br /><br />A Microsoft Intune Endpoint Protection nincs telepítve, illetve a rendszer eltávolítja, ha korábban már telepítették. |

Az aktuálisan használt végpontvédelmi alkalmazásról a Microsoft Intune Endpoint Protection szolgáltatásra való áttéréshez tegye a következőket:

1. Az Intune-ügyfélszoftvernek az ügyfélszámítógépekre való telepítése közben ne állítsa le az aktuálisan használt végpontvédelmi alkalmazást.

2. Győződjön meg arról, hogy a Microsoft Intune Endpoint Protection telepítve lett, és már védi az ügyfélszámítógépeket.

3. Távolítsa el a külső gyártó végpontvédelmi szoftverét a következőképpen:

    - A külső végpontvédelmi alkalmazás gyártója által biztosított szoftvereltávolító eszköz telepítése az Intune szoftverterjesztés funkciójával. További információk: [Alkalmazások központi telepítése a Microsoft Intune-nal](../apps/apps-deploy.md).

    - A külső gyártótól származó végpontvédelmi alkalmazás manuális eltávolításával.

> [!NOTE]
> Az Intune nem végzi el automatikusan a külső gyártótól származó végpontvédelmi alkalmazások eltávolítását.

## <a name="configure-microsoft-intune-endpoint-protection"></a>A Microsoft Intune Endpoint Protection konfigurálása
A Microsoft Intune Endpoint Protection konfigurálásához hajtsa végre a következő lépéseket.

1. A [Microsoft Intune felügyeleti konzoljában](https://manage.microsoft.com/) válassza a **Házirend** > **Házirend hozzáadása** lehetőséget.

2. Bontsa ki a **Számítógép-kezelés** elemet, és válassza ki **A Microsoft Intune-ügynök beállításai** elemet. Válassza az **Egyéni házirend létrehozása és központi telepítése** lehetőséget az Endpoint Protection-beállítások házirendjének megadásához. Ezután kattintson a **Házirend létrehozása** gombra.

Használhatja az ajánlott beállításokat, vagy testre is szabhatja azokat. Ha szeretne többet megtudni a házirendek létrehozásával és alkalmazásával kapcsolatban, olvassa el [A Windows rendszerű számítógépek a Microsoft Intune számítógépügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) című témakört.

  ![Endpoint Protection-beállítások](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-pc-endpoint-policy.png)

Az alkalmazott Endpoint Protection-házirendet a **Házirend** munkaterület **Minden házirend** lapján tekintheti meg.

## <a name="specify-endpoint-protection-service-settings"></a>Az Endpoint Protection szolgáltatás beállításainak megadása

|                                                 Házirend-beállítás                                                  |                                                                                                                                                                                                                                                                                                                                                                                                             Details                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                  <strong>Az Endpoint Protection telepítése</strong>                                   | Állítsa az <strong>Igen</strong> értékre, ha telepíteni szeretné az Endpoint Protectiont a kezelt számítógépekre. Ha a telepítés során a rendszer egy külső gyártótól származó végpontvédelmi alkalmazást észlel, az Endpoint Protection nem települ, kivéve, ha <strong>Az Endpoint Protection telepítése akkor is, ha már van telepítve más gyártótól származó végpontvédelmi alkalmazás</strong> beállítás értéke <strong>Igen</strong>. <strong>Megjegyzés:</strong> A rendszer alapértelmezés szerint telepíti az Intune Endpoint Protection szolgáltatást a felügyelt számítógépekre. Ha nem szeretné a felügyelt számítógépeken telepíteni az Endpoint Protection szolgáltatást, akkor ezt a házirend-beállítást mindenképpen <strong>Nem</strong> értékre kell állítania. Ha az Endpoint Protection korábban telepítve lett, és a házirendet a <strong>Nem</strong> értékre módosítja, akkor a rendszer eltávolítja az Endpoint Protection szolgáltatást.<br />Javasolt érték: <strong>Igen</strong> |
| <strong>Az Endpoint Protection telepítése akkor is, ha egy külső gyártó végpontvédelmi alkalmazása telepítve van</strong> |                                                                                                                                                                                                                                                                                                                Válassza az <strong>Igen</strong> értéket, ha a Microsoft Intune Endpoint Protection szolgáltatást akkor is telepíteni szeretné, ha a rendszer külső gyártó végpontvédelmi alkalmazását észleli.<br /><br />Javasolt érték: <strong>Igen</strong>                                                                                                                                                                                                                                                                                                                |
|                                   <strong>Az Endpoint Protection engedélyezése</strong>                                   |                                                                                                                                                                                                            Állítsa <strong>Igen</strong> értékre a Microsoft Intune Endpoint Protection engedélyezéséhez az Endpoint Protection-ügyféllel rendelkező számítógépeken.<br /><br />Ha a <strong>Nem</strong> értékre van állítva, és a Microsoft Intune Endpoint Protection telepítve van, az Endpoint Protection-ügyfél felhasználói felülete nem jelenik meg a felhasználók számára, és az összes védelmi szolgáltatás inaktív lesz.<br /><br />Javasolt érték: <strong>Igen</strong>                                                                                                                                                                                                             |
|                                       <strong>Ügyfél felhasználói felületének letiltása</strong>                                        |                                                                                                                                                                                                                                                                                                      Állítsa az <strong>Igen</strong> értékre a Microsoft Intune Endpoint Protection-ügyfél felhasználói felületének a felhasználók elől való elrejtéséhez (az érvénybe lépéséhez az ügyfélszámítógép újraindítása szükséges).<br /><br />Javasolt érték: <strong>Nem</strong>                                                                                                                                                                                                                                                                                                       |
| <strong>Az Endpoint Protection telepítése akkor is, ha egy külső gyártó végpontvédelmi alkalmazása telepítve van</strong> |                                                                                                                                                                                                                                                                                                       Válassza az <strong>Igen</strong> értéket, ha kényszeríteni szeretné a Microsoft Intune Endpoint Protection szolgáltatás telepítését akkor is, ha a rendszer külső gyártó végpontvédelmi alkalmazását észleli.<br /><br />Javasolt érték: <strong>Nem</strong>                                                                                                                                                                                                                                                                                                       |
|                    <strong>Rendszer-visszaállítási pont létrehozása a kártevő szoftverek eltávolítása előtt</strong>                    |                                                                                                                                                                                                                                                                                                                                 Állítsa az <strong>Igen</strong> értékre, ha bármely kártevő szoftver eltávolításának megkezdése előtt létre szeretne hozni egy Windows rendszer-visszaállítási pontot.<br /><br />Javasolt érték: <strong>Igen</strong>                                                                                                                                                                                                                                                                                                                                  |
|                                 <strong>Ártalmatlanított kártevő szoftverek követése (nap)</strong>                                  |                                                                                                                                                                                                                                                                                      A beállítás lehetővé teszi, hogy az Endpoint Protection meghatározott ideig nyomon kövesse az ártalmatlanított kártevő szoftvereket, és így manuálisan lehessen ellenőrizni a korábban fertőzött számítógépeket.<br /><br />0 érték 30 nap közötti értéket adhat meg.<br /><br />Javasolt érték: <strong>7 nap</strong>                                                                                                                                                                                                                                                                                       |

Ha az **Endpoint Protection telepítése** és az **Endpoint Protection engedélyezése** házirendértékeket **Igen**értékre állította, és **Az Endpoint Protection telepítése, akkor is, ha már van telepítve más gyártótól származó végpontvédelmi alkalmazás** házirendérték beállítása **Nem**, akkor a Microsoft Intune Endpoint Protection észleli a telepített végpontvédelmi alkalmazást. Ebben az esetben az Endpoint Protection nem települ, illetve a rendszer eltávolítja, ha már telepítették. Ugyanakkor a Microsoft Intune Endpoint Protection jelenti a másik végpontvédelmi alkalmazás állapotát az Intune-ban.

  A valós idejű védelem jóvoltából a Microsoft Security Essentials riasztást küld, ha potenciális fenyegetések, például vírusok és kémprogramok kísérlik meg telepíteni vagy futtatni magukat. Mihelyst ilyen esemény történik, megjelenik egy üzenet az értesítési területen, a tálca jobb szélén.

### <a name="specify-real-time-protection-settings"></a>Valós idejű védelem beállításainak megadása

|Házirend-beállítás|Details|
|------------------|--------------------|
|**Valós idejű védelem engedélyezése**|Engedélyezi az összes olyan fájl és alkalmazás figyelését és vizsgálatát, melyekhez hozzáférnek. Emellett minden rosszindulatú fájlt és alkalmazást is blokkol, mielőtt azok lefutnának a számítógépeken.<br /><br />Javasolt érték: **Igen**|
|**Minden letöltés ellenőrzése**|Engedélyezi az összes az internetről a számítógépekre letöltött fájl és melléklet vizsgálatát.<br /><br />Javasolt érték: **Igen**|
|**A fájl- és programtevékenység figyelése a számítógépen**|Engedélyezi a bejövő és a kimenő fájlok és a programok tevékenységének figyelését a számítógépeken. Ezzel a beállítással az Endpoint Protection szolgáltatás figyeli az egyes fájlok és programok futásának elindulását, és értesítést küld az általuk vagy rajtuk elvégzett műveletekről.<br /><br />Javasolt érték: **Igen**|
|**Megfigyelt fájlok**|Kiválaszthatja, hogy a szolgáltatás csak a bejövő, csak a kimenő fájlokat, vagy az összes fájlt figyelje.<br /><br />Javasolt érték: **Minden fájl figyelése**|
|**Viselkedésfigyelés engedélyezése**|Engedélyezi, hogy a Microsoft Intune Endpoint Protection gyanús tevékenységekre utaló mintákat keressen az ügyfélszámítógépeken.<br /><br />Javasolt érték: **Igen**|
|**Hálózatvizsgáló rendszer engedélyezése**|A Hálózatfelügyeleti rendszer (NIS) engedélyezése az ügyfélszámítógépeken. A NIS a [Microsoft kártevőkezelési központban](https://go.microsoft.com/fwlink/?LinkId=234249) található ismert sebezhető pontok mintázatai alapján észleli és blokkolja a rosszindulatú hálózati forgalmat.<br /><br />Javasolt érték: **Igen**|

  ![Az Endpoint Protection szolgáltatás valós idejű beállításai](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>A vizsgálatütemezési beállítások megadása

|Házirend-beállítás|További információ|
|------------------|--------------------|
|**Napi gyorsvizsgálat ütemezése**|Egy, a számítógépeken lévő gyakran használt fájlokra, illetve fontos rendszerfájlokra vonatkozó napi gyors vizsgálat ütemezése. Ez a gyors vizsgálat minimális hatással van a teljesítményre.<br /><br />Javasolt érték: **Igen**|
|**Gyorsellenőrzés végrehajtása, ha egymást követően két gyorsellenőrzés is kimaradt**|Az Endpoint Protection szolgáltatás konfigurálása úgy, hogy automatikusan gyors vizsgálatot futtasson azokon a számítógépeken, amelyeken elmaradt két egymást követő gyors vizsgálat.<br /><br />Javasolt érték: **Igen**|
|**Teljes ellenőrzés ütemezése**|A helyi számítógépek merevlemezein található összes fájlra és erőforrásra vonatkozó teljes vizsgálat beállítása. Ez a vizsgálat hosszabb ideig is eltarthat, és hatással lehet a számítógépek teljesítményére (a vizsgálat időtartama a vizsgált fájlok és erőforrások számától függ).<br /><br />Javasolt érték: **Nem**|
|**Teljes ellenőrzés végrehajtása, ha egymást követően két teljes ellenőrzés is kimaradt**|Az Endpoint Protection szolgáltatás beállítása úgy, hogy automatikusan gyors vizsgálatot futtasson azokon a számítógépeken, amelyeken elmaradt két egymást követő, gyors vizsgálat.<br /><br />Javasolt érték: Nincs konfigurálva|

### <a name="specify-scan-options-settings"></a>Vizsgálati beállítások megadása

|Házirend-beállítás|Details|
|------------------|--------------------|
|**Teljes ellenőrzés végrehajtása az Endpoint Protection telepítése után**|**Igen** érték esetén az Endpoint Protection szolgáltatás automatikusan teljes rendszervizsgálatot futtat miután telepítették a számítógépeken. A felhasználók termelékenységére gyakorolt hatás minimalizálása érdekében ez a vizsgálat csak akkor fut, amikor a számítógépek üresjáratban vannak.<br /><br />Javasolt érték: **Igen**|
|**Kártevő szoftver eltávolítása után teljes ellenőrzés automatikus végrehajtása, amennyiben szükséges**|Ha az **Igen** értékre állítja, az Endpoint Protection automatikusan teljes rendszervizsgálatot fog futtatni a számítógépeken a kártevő szoftverek eltávolítása után annak megerősítésére, hogy más fájlok nem érintettek.<br /><br />Javasolt érték: **Igen**|
|**Ütemezett vizsgálat indítása csak akkor, ha a számítógép üresjáratban van**|A beállítást **Igen** értékre állítva akadályozhatja meg, hogy az ütemezett vizsgálatok elinduljanak, amikor a számítógépek használatban vannak, így megelőzve a felhasználói termelékenység csökkenését.<br /><br />Javasolt érték: **Igen**|
|**A legújabb kártevőszoftver-definíciók lekérdezése az ellenőrzések megkezdése előtt**|Ha a beállítást az **Igen** értékre állítja, az Endpoint Protection automatikusan megkeresi a legújabb kártevő-definíciókat a számítógépek vizsgálatának megkezdése előtt.<br /><br />Javasolt érték: **Igen**|
|**Archív fájlok ellenőrzése**|Az **Igen** értékre állítva konfigurálhatja az Endpoint Protection szolgáltatást arra, hogy archív fájlokban (például .zip- vagy .cab-fájlokban) is keressen kártevő szoftvereket a számítógépeken.<br /><br />Javasolt érték: **Nem**|
|**E-mailek ellenőrzése**|Az **Igen** értékre állítva konfigurálhatja az Endpoint Protection szolgáltatást a bejövő e-mailek vizsgálatára a számítógépekre való érkezésükkor.<br /><br />Javasolt érték: **Igen**|
|**A megosztott hálózati mappákból megnyitott fájlok ellenőrzése**|Az **Igen** értékre állítva konfigurálhatja az Endpoint Protection szolgáltatást a hálózaton található megosztott mappákból megnyitott fájlok vizsgálatára. Ezek jellemzően olyan fájlok, amelyek UNC (univerzális elnevezési konvenció) elérési úttal érhetők el. A funkció engedélyezése a csak olvasási hozzáféréssel rendelkező felhasználók számára problémákat okozhat, mert ők nem tudják eltávolítani a kártevő szoftvereket.<br /><br />Javasolt érték: **Nem**|
|**Csatlakoztatott hálózati meghajtók ellenőrzése**|Az **Igen** értékre állítva konfigurálhatja az Endpoint Protection szolgáltatást a csatlakoztatott hálózati meghajtókon lévő fájlok vizsgálatára. A funkció engedélyezése a csak olvasási hozzáféréssel rendelkező felhasználók számára problémákat okozhat, mert ők nem tudják eltávolítani a kártevő szoftvereket.<br /><br />Javasolt érték: **Nem**|
|**Cserélhető adathordozók ellenőrzése**|Az **Igen** értékre állítva konfigurálhatja az Endpoint Protection szolgáltatást a kártevő szoftverek és nemkívánatos szoftverek keresésére a cserélhető adathordozókon, például az USB flash meghajtókon a számítógépek teljes vizsgálatának futtatásakor.<br /><br />Javasolt érték: **Igen**|
|**Processzorhasználat korlátozása az ellenőrzések során**|A számítógépek ütemezett vizsgálatai során engedélyezett maximális CPU-használat százalékértékének beállítása. Ez az érték 1 és 100 százalék között állítható be.<br /><br />Javasolt érték: **50%**|

### <a name="choose-default-actions-settings"></a>Az alapértelmezett műveleti beállítások kiválasztása

Az **Adja meg, hogy az Endpoint Protection hogyan kezelje az alábbi riasztási szintekhez tartozó kártevő szoftvereket** beállítás határozza meg az alapértelmezett műveletet, amelyet az Endpoint Protection végrehajt a különböző riasztási szintű kártevő szoftverek észlelése esetén. Minden riasztási szinten eltávolíthatja a kártevő szoftvereket, karanténba zárhatja azokat, vagy végrehajthatja a Microsoft által javasolt műveletet.

Javasolt érték: **Javasolt művelet**, amely lehetővé teszi, hogy az Endpoint Protection tegyen javaslatot a műveletre.   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>Döntse el, hogy kiválasztja-e a kizárt fájlok és kizárt mappák beállításait

**A valós idejű védelem által és a teljes ellenőrzések végrehajtásakor figyelmen kívül hagyott fájlok és mappák** beállítással kizárhat meghatározott fájlokat és mappákat, amikor vizsgálatot futtat vagy valós idejű védelmet használ a számítógépeken.

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>Döntse el, hogy kiválasztja-e a kizárt folyamatok beállításait

**A valós idejű védelem által és a teljes ellenőrzések végrehajtásakor figyelmen kívül hagyott folyamatok** beállítással kizárhat meghatározott folyamatokat, amikor vizsgálatot futtat vagy valós idejű védelmet használ a számítógépeken. Csak a következő kiterjesztésű fájlokat lehet kizárni: **.exe**, **.com** vagy **.scr**.

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>Döntse el, hogy kiválasztja-e a kizárt fájltípusok beállításait

**A valós idejű védelem által és a teljes ellenőrzések végrehajtásakor figyelmen kívül hagyott fájltípusok** beállítással kizárhat meghatározott fájlnév-kiterjesztéseket, amikor vizsgálatot futtat vagy valós idejű védelmet használ a számítógépeken.

### <a name="specify-microsoft-active-protection-service-settings"></a>A Microsoft Active Protection Service beállításainak megadása
A Microsoft Active Protection Service egy online közösség, amely segít eldönteni, hogyan reagáljon a lehetséges veszélyforrásokra. A Közösség emellett az új kártevőszoftver-fertőzések terjedésének megállítását is segíti. A **Kapcsolódás a Microsoft Active Protection Service szolgáltatáshoz** beállítást **Igen** értékűre állíthatja, majd megadhatja a **Tagsági szint** értékét:
- **Alapszintű** – alapvető adatok küldése a Microsoftnak az észlelt kártevőkkel kapcsolatban. Ez magában foglalja a szoftver származási helyét, az alkalmazott, illetve az Endpoint Protection által automatikusan alkalmazott műveleteket, valamint azt, hogy sikeresek voltak-e a műveletek.
- **Speciális** – több adat küldése a Microsoftnak a kártevőkkel, kémprogramokkal és vélhetően nemkívánatos szoftverekkel kapcsolatban. Ebbe beletartoznak a szoftverek helyével, a fájlnevekkel, és az azzal kapcsolatos információk, hogy a szoftverek hogyan működnek és milyen hatással voltak a számítógépre.

Ezenkívül bekapcsolhatja a **Microsoft Active Protection Service-jelentéseken alapuló dinamikus definíciók fogadása** beállítást is.

## <a name="choose-management-tasks-for-endpoint-protection"></a>Az Endpoint Protection szolgáltatás felügyeleti feladatainak kiválasztása
A következő műveletekkel különböző kezelési feladatokat hajthat végre az Endpoint Protection szolgáltatást futtató kezelt számítógépeken.
- Kártevő-definíciók frissítése
  - Intune konzol – A **Csoportok** munkaterületen jelölje ki a frissíteni kívánt számítógépeket. Válassza a **Távoli feladatok** &gt; **Kártevőszoftver-leírások frissítése** elemet.
  - Felügyelt számítógép – Indítsa el a végpontvédelmi ügyfélszoftvert a Windows értesítési területéről. Válassza a **Frissítés** lapot, majd a **Frissítés**parancsot.
- Kártevő-ellenőrzés futtatása
  - Intune konzol – A **Csoportok** munkaterületen jelölje ki az ellenőrizni kívánt számítógépeket. Válassza a **Teljes kártevő-ellenőrzés futtatása** vagy a **Gyors kártevő-ellenőrzés futtatása** lehetőséget.
  - Felügyelt számítógép – Indítsa el a végpontvédelmi ügyfélszoftvert a Windows értesítési területéről. Válassza a **Gyors**, a **Teljes**, vagy az **Egyéni**lehetőséget, majd kattintson a **Vizsgálat most** elemre.

Az Intune-konzol jobb alsó sarkában található **Távoli feladatok** hivatkozásra kattintva megtekintheti a távoli feladatok állapotát. A **Távoli feladat állapota** párbeszédpanelen áttekintheti az aktuális távoli feladatokat, a feladatok állapotát, az eszköz nevét és a jelentett hibákat. Ugyanitt talál a hibaelhárítási információkra mutató hivatkozást, ha vannak ilyenek.

## <a name="monitor-endpoint-protection"></a>Az Endpoint Protection figyelése
A [Microsoft Intune felügyeleti konzol](https://manage.microsoft.com/) **Védelem**munkaterületén figyelheti a számítógépeken lévő kártevő szoftverek állapotát. A munkaterület két lapból áll:
- **Védelem áttekintése** – A fontos problémákat jeleníti meg hivatkozások formájában, amelyekre rákattintva további információkat érhet el. Többek között az alábbi problémák jelenhetnek meg:
  - **Követő műveletet igénylő kártevőszoftver-példányok** – a hivatkozásra kattintva megtekintheti a kártevőkkel kapcsolatos problémák listáját, beleértve a problémák elhárítása érdekében végrehajtandó utólagos műveleteket. A lista tovább részletezhető annak megtekintéséhez, hogy mely számítógépek érintettek.
  - **Számítógépek követő műveletet igénylő kártevő szoftverrel** – a hivatkozásra kattintva megtekintheti az összes, megoldatlan kártevőproblémával rendelkező számítógépet és a problémák elhárításához szükséges utólagos műveleteket.
  - **Védtelen eszközök** – a hivatkozásra kattintva megtekintheti azokat a számítógépeket, amelyek semmilyen végpontvédelmi szoftverrel nincsenek védve, mert nincs rajtuk telepítve szoftver, vagy mert hiba történt. Egy számítógépet kijelölve megtekintheti annak további részleteit.
  - **Más végpontvédelmi alkalmazást futtató eszközök** – a hivatkozásra kattintva megtekintheti a külső gyártótól származó végpontvédelmi alkalmazást futtató számítógépeket.
- **Minden kártevő** – a számítógépeken talált összes aktív kártevő listáját jeleníti meg. A lista tovább részletezhető valamely adott kártevő szoftver által érintett összes számítógép listájának megtekintéséhez, vagy választhat az alábbi műveletek közül:
  - **Tulajdonságok megtekintése** – a kijelölt kártevő további adatait tartalmazó oldal megnyitása.
  - **További tudnivalók erről a kártevő szoftverről** – a Microsoft kártevőkezelési központ a kártevővel kapcsolatos további információkat tartalmazó témakörének megnyitása.

> [!IMPORTANT]
> A **Védelem** munkaterület addig nem jelenik meg a felügyeleti konzolon, amíg nem telepíti az ügyfelet legalább egy számítógépen, és nem kezdi meg annak felügyeletét.

  ![Az Endpoint Protection figyelése](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>A kártevők legutóbbi észlelési útvonalainak megtekintése számítógépen
Az Intune az eszközökön észlelt 10 legutóbbi kártevőpéldány elérési útvonalát tudja megjeleníteni. A **Legutóbbi észlelési útvonal** alapértelmezés szerint le van tiltva. A nézet engedélyezése:

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Csoportok** > **Minden eszköz** > **Minden számítógép** lehetőséget.
2. Kattintson jobb gombbal arra a számítógépre, amelynek szeretné megnézni a legutóbbi észlelési útvonalát, és válassza a **Tulajdonságok** elemet.
3. A lap felső részén található lapfülek közül válassza a **Kártevők** elemet.

   ![Válassza ki a Kártevők lapfület, majd jelölje be a Legutóbbi észlelési útvonalak jelölőnégyzetet](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/malware-path-column.png)
4. Kattintson jobb gombbal az oszlopfejlécre. Megjelenik az elérhető oszlopok listája. Jelölje be a lista **Legutóbbi észlelési útvonalak** jelölőnégyzetét. Megjelenik a **Legutóbbi észlelési útvonalak** oszlop és megjeleníti az eszközön észlelt legfeljebb 10 legutóbbi kártevőpéldányt.

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>Kártevő-ellenőrzés futtatása vagy a számítógép kártevőszoftver-leírásainak frissítése
Az Intune az Endpoint Protection vagy a Windows Defender használatával teljes vagy gyors kártevő-ellenőrzést is képes futtatni azokon a távoli felügyelt számítógépeken, amelyeken az Intune-ügyfél telepítve van.

1. A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com/) lépjen a **Csoportok** > **Áttekintés** > **Minden eszköz** > **Minden számítógép** elemre, és jelölje ki a célozni kívánt számítógépet.

2. Kattintson a **Távoli feladatok** legördülő listára, és válassza ki a távoli számítógépen futtatni kívánt feladatot.

## <a name="need-more-help"></a>További segítségre van szüksége?
További segítség és támogatás: [Az Endpoint Protection hibáinak elhárítása a Microsoft Intune-ban](troubleshoot-endpoint-protection-in-microsoft-intune.md).

## <a name="see-also"></a>További információ
[Szabályzatok a Windows rendszerű számítógépek védelméhez](policies-to-protect-windows-pcs-in-microsoft-intune.md)
