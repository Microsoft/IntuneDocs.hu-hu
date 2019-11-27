---
title: Hogyan kérhet támogatást az Intune-hoz
titleSuffix: Microsoft Intune
description: A Microsoft Intune fizetős és próbaverziós előfizetéseihez online és telefonos segítséget kérhet.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5aca7dbae7a74af399bcbf21aec1dd9dd2d1e851
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390748"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Hogyan kérhet támogatást az Intune-hoz

A Microsoft Intune-hoz a Microsoft globális műszaki, értékesítés előtti, számlázási és előfizetési támogatást nyújt. A támogatás interneten és telefonon is elérhető mind a fizetős, mind a próbaverziós előfizetésekhez. Az online műszaki támogatás angolul és japánul érhető el. Telefonos és online számlázási támogatás más nyelveken érhetők el.

Intune-rendszergazdaként használhatja a **Súgó és támogatás** lehetőséget az Intune-hoz készült online támogatási jegy a Azure Portalból való beküldéséhez. A támogatási incidensek létrehozásához és kezeléséhez a fióknak rendelkeznie kell egy Azure Active Directory (Azure AD) szerepkörrel, amely tartalmazza a **Microsoft. Office 365. supportTickets** *műveletet* . További információ a támogatási jegy létrehozásához szükséges Azure AD-szerepkörökről és engedélyekről: [rendszergazdai szerepkörök a Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

>[!IMPORTANT]
> Ha olyan külső termékekhez szeretne műszaki támogatást igénybe venni, amelyek együttműködnek az Intune-nal (például a Saaswedo, a Cisco vagy a Lookout), akkor először forduljon ezeknek a termékeknek a szállítójához. Mielőtt megnyitja az Intune-nal kapcsolatos támogatási kérelmet, győződjön meg róla, hogy a másik terméket megfelelően konfigurálta.
>
> A Microsoft Intune hibaelhárítási problémáiról további információt az Intune dokumentációjának [hibaelhárítási szakaszában](help-desk-operators.md) találhat.


## <a name="help-and-support-experience"></a>Súgó és támogatás

Az Intune Súgó-és támogatási felülete a [Microsoft Endpoint Manager felügyeleti központjában](https://go.microsoft.com/fwlink/?linkid=2109431) , valamint az Intune-ban lévő összes (vagy lapokon) található, a Azure Portal.

A *Súgó és támogatás* funkció hasonló a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com/)látható élményhez, és lecseréli az előző *Súgó + támogatást*, amely az Azure egyéb szolgáltatásaira is érvényes marad.

> [!TIP]
> 2019. november 18-án kezdődően egy frissített és egyszerűsített konzolon alapuló felhasználói élményt nyújt a bérlők számára. Ha ez az új felület még nem érhető el, hamarosan elérhető lesz.

### <a name="options-to-access-help-and-support"></a>A Súgó és támogatás elérésének lehetőségei

Ha újonnan létrehozott bérlőt használ az Intune-hoz, lehetséges, hogy a *Súgó és támogatás* nem nyílik meg, és a következő üzenet jelenik meg:

- *Ismeretlen hiba történt. Frissítse a lapot, de ha a probléma továbbra is fennáll, hozzon létre egy esetet a [M365 felügyeleti központban](https://admin.microsoft.com) , és hivatkozzon a megadott munkamenet-azonosítóra.*

A hiba részletei között szerepel egy *munkamenet-azonosító*, egy *bővítmény* részletei és egyebek. 
 
Ez a probléma akkor fordul elő, ha még nem hitelesítette az új bérlői fiókot a **M365 felügyeleti központban** https://admin.microsoft.comvagy az **Office 365-portálon** https://portal.office.comcímen. A probléma megoldásához válassza a *M365 felügyeleti központ* hivatkozását az üzenetben, vagy keresse fel https://portal.office.com, és jelentkezzen be. A hitelesítés a következő helyen, az Intune *súgója és támogatása* elérhetővé válik.


**Súgó és támogatás elérése**:

- **A Azure Portal**

  - Válassza a **Súgó és támogatás** lehetőséget minden Intune-panelen vagy-lapon.

  > [!NOTE]  
  > Ha az Intune-példánya a nyilvános felhőben, más néven a kormányzati felhőben található, mint például a Azure Government, tekintse meg a jelen cikk későbbi, a [privát felhőhöz készült Intune-támogatás](#intune-support-for-private-cloud-for-government)című részét. Az Intune *Súgó és támogatás* felülete a következő év végéig nem érhető el a kormányzati privát felhőben.

- **A Microsoft Endpoint Manager felügyeleti központjában**
  - Miután kiválasztotta az Intune szolgáltatáshoz tartozó szolgáltatási területeket, válassza a **Súgó és támogatás**lehetőséget.
  - A Microsoft Endpoint Manager felügyeleti központ bármely csomópontján jelölje be a **?** ikonra a portál jobb felső sarkában, majd a legördülő listából válassza ki azt a szolgáltatást, amelyhez segítséget szeretne használni. A **?** a Microsoft Endpoint Manager felügyeleti központban található ikon több szolgáltatást is támogat, és ki kell választania azt a szolgáltatást, amelyhez segítséget szeretne adni.  

    ![Válassza ki a szolgáltatást](./media/get-support/select-a-service.png)

    A szolgáltatás kiválasztása után megjelenik a szolgáltatás *Súgó és támogatás* lapja, ahol megadhatja a konkrét problémákra vonatkozó [megoldások megtalálásának](#find-solutions) részleteit.

    Ha a keresés eredményei úgy tűnik, hogy nem felelnek meg a szolgáltatás elvárásainak, ellenőrizze, hogy a helyes szolgáltatást választotta-e ki. A szolgáltatás kiválasztása csak a *Súgó és támogatás*után jelenik meg.  Ha a megfelelő szolgáltatás nem lett kiválasztva, kattintson a *válasszon ki egy szolgáltatást* , hogy visszatérjen a szolgáltatás kiválasztása legördülő listához.

    ![A szolgáltatás megerősítése](./media/get-support/confirm-your-service-selection.png)

###  <a name="the-support-experience"></a>A támogatási élmény

  A Súgó és támogatás megnyitásakor a portálon megjelenik a **segítségre van szüksége?** ablak:

  ![A segítség szükséges ablak megtekintése](./media/get-support/need-help.png)

  A bal felső sarokban három ikon közül választhat, amelyekkel megnyithat különböző ablaktáblákat a *segítségre van szüksége?* ablakban. A megjelenített ablaktáblát az aláhúzás azonosítja.

  A **Premier** vagy **Unified** támogatási szerződéssel rendelkező ügyfelek [további támogatási lehetőségekkel](#premier-and-unified-support-customers) rendelkeznek, és a *segítségre van szüksége* a szalagcímben? ez a következő képhez hasonlít: ![Premier banner](./media/get-support/premier-banner.png)

  *Segítségre van szüksége?* Megnyílik a *megoldások keresése* ablaktáblán. Ha azonban aktív támogatási esettel rendelkezik, megnyílik az ablak a *szolgáltatási kérelmek* ablaktáblán, ahol megtekintheti az aktív és a lezárt támogatási esetek részleteit.

#### <a name="find-solutions"></a>Megoldások keresése

![Válassza a megoldások keresése panelt](./media/get-support/find-solutions.png)

A *megoldások keresése* panelen adja meg a probléma néhány részletét a megadott szövegmezőben. Az adott problémával kapcsolatban megadott szöveg alapján a panel a lehetséges egyezések szerint tölti fel az adatokat. Emellett a javasolt cikkekre mutató hivatkozásokat is talál, amelyek segíthetnek a probléma megoldásában.

Ha az Ön által leírt részletekre erős egyezés található, a hibaelhárítási tippek közvetlenül a *segítség szükséges?* ablakban jelenhetnek meg.

Megadhatja például a **jelszó-szinkronizálási hibákat**. A találatok között közvetlenül a panelen található hibaelhárítási útmutató, valamint a dokumentációs könyvtár ajánlott cikkeire mutató hivatkozások találhatók.

![Hibaelhárítási ismeretek megtekintése](./media/get-support/troubleshooting-insights.png)

#### <a name="contact-support"></a>Forduljon a támogatási szolgálathoz.

![A kapcsolatfelvételi támogatás ablaktábla kiválasztása](./media/get-support/contact-support.png)

A *kapcsolatfelvételi támogatás* ablaktáblán kérhet segítséget. Ez az ablaktábla akkor érhető el, ha néhány alapszintű kulcsszót ad meg a *megoldások keresése* ablaktáblán.

Ha segítségre van szüksége, a lehető legrészletesebben adja meg a probléma leírását.  A telefonos és e-mail-kapcsolattartási adatok megerősítése után válassza ki a kívánt kapcsolatfelvételi módot. Az ablakban az egyes kapcsolattartási módszerek válaszideje látható, amely a kapcsolódáskor várható. A kérelem elküldése előtt csatolja a fájlokat, például a naplókat vagy a képernyőképeket, amelyek segíthetnek a probléma részleteinek kitöltésében.

![Kapcsolatfelvétel a támogatási űrlappal](./media/get-support/contact-support-form.png)

A szükséges információk kitöltése után válassza a **Kapcsolatfelvétel** lehetőséget a kérelem elküldéséhez.

#### <a name="service-requests"></a>Szolgáltatási kérelmek

![A szolgáltatási kérelmek panel kiválasztása](./media/get-support/service-requests.png)

A *szolgáltatási kérelmek* ablaktáblán jelennek meg az esetek előzményei. Az aktív esetek a lista elején találhatók, és a lezárt problémák is elérhetők véleményezésre.

![A szolgáltatási kérelmek listájának megtekintése](./media/get-support/service-requests-pane.png)

Ha aktív támogatási esettel rendelkezik, Itt megadhatja, hogy erre a hibára ugorjon, vagy bármelyik incidenst kiválaszthatja az aktív és a lezárt incidensek listájából, hogy további információkat lehessen megtekinteni.

Ha elkészült egy incidens részleteinek megtekintésével, válassza a három segítségre *szoruló* párbeszédpanel ikonján megjelenő bal oldali nyilat a szolgáltatás kérése ablak tetején. A vissza nyíl visszaadja a megjelenített támogatási incidensek listáját.

#### <a name="premier-and-unified-support-customers"></a>Premier és Unified support-ügyfelek

**Premier** vagy **Unified** támogatási szerződéssel rendelkező ügyfélként megadhatja a probléma súlyosságát, és egy adott időpontra és napra vonatkozó támogatási visszahívást is ütemezhet. Ezek a beállítások akkor érhetők el, ha új problémát nyit meg vagy küld el, és amikor szerkeszt egy aktív támogatási esetet.

**Súlyosság** – a problémák súlyosságát meghatározó beállítások a támogatási szerződéstől függenek:

- *Premier*: az a, B vagy C súlyossága
- *Unified*: kritikus vagy nem kritikus

Az " **a** " súlyossági szintű vagy **kritikus fontosságú** probléma kiválasztásával egy telefonos támogatási esetre korlátozódik, amely lehetővé teszi a leggyorsabb lehetőséget a támogatás megszerzésére.

**Visszahívási ütemterv** – a visszahívást egy adott napon és időpontban kérheti le.

## <a name="azure-help--support-experience"></a>Azure Súgó + támogatási élmény

A továbbiakban nem használhatja az Azure *Súgó + támogatási szolgáltatást* az Intune-nal való segítségnyújtásra, kivéve, ha az előfizetése egy privát felhőben van a kormányzat számára.
Ha az Intune-példány nem fut a kormányzathoz tartozó privát felhőben, az Azure *Súgó + támogatás* szolgáltatáson keresztül történő navigálás a támogatási incidensek létrehozásához és kezeléséhez az Intune *súgóját és támogatási* élményét átirányítja:

Ha a bal oldali navigációs ablaktábla **Súgó + támogatás**elemét használja, vagy használja a **?** lehetőségre kattintva nyissa meg a *Súgó* panelt, majd válassza a **Súgó + támogatás**lehetőséget, majd nyissa meg az Azure *Súgó + támogatás* lapját. 


Ebből az oldalból válassza az **+ új támogatási kérés** elemet a *Súgó + támogatás + új támogatási kérelem* lap *alapok* lapjának megnyitásához.

![Súgó és támogatás](./media/get-support/help-plus-support.png)

Ezen az oldalon:

- A *probléma típusa*beállításnál válassza a **technikai**lehetőséget.
- A *szolgáltatás*mezőben válassza a **Microsoft Intune**lehetőséget.

  Ekkor megjelenik egy hivatkozás, amely átirányítja Önt az [Intune Súgó és támogatás oldalára](https://aka.ms/intunehelpsupport).
  
  ![Új támogatási kérelem](./media/get-support/new-request.png)


## <a name="intune-support-for-private-cloud-for-government"></a>Intune-támogatás a Private Cloud for Government szolgáltatáshoz

Ha az Intune-előfizetést a privát felhőben üzemelteti a Government számára, amely más néven szuverén felhő, mint a Azure Government, még nem fér hozzá az Intune súgójának és támogatásának újabb felhasználói felületéhez.  Ehelyett használja az alábbi információkat az Intune támogatásához.

### <a name="create-an-online-support-ticket"></a>Online támogatási jegy létrehozása

>[!IMPORTANT]
> A támogatási incidensek létrehozásakor a portál olyan támogatási esetet *azonosít, amely* egy olyan új rendszerre mutat be, amely még nem érhető el az állami felhőhöz A 15 számjegyű eset létrehozásakor a rendszer az adott eset tükrözését hozza létre Microsoft ügyfélszolgálata általi használatra. Ez a tükrözési eset egy új támogatási rendszerben jön létre, és a 8 jegyű eset AZONOSÍTÓját használja, és a támogatási szolgáltatások a támogatási incidensek összes munkájának és kommunikációjának nyomon követésére használják. Röviddel a 15 jegyű eset létrehozása után egy e-mailt fog kapni, amely a támogatási szolgáltatások által használt tükrözött támogatási eset 8 számjegyű számát azonosítja.
>
> Támogassa a személyes munkát és a 8 számjegyű támogatási esetet, és csak a 8 számjegyű támogatási esetet használja a kommunikáció naplózásához és az incidensek előrehaladásának nyomon követéséhez. Ezért e-mail-frissítéseket fog kapni ebből a 8 számjegyű támogatási esetről, amely a kis-és nagybetűket tartalmazó rekordként szolgál. A 15 számjegyű támogatási incidens nem naplózza a részleteket. Ha a támogatás kizárult, és a 8 számjegyű támogatási eset bezárul, az állapotot a 15 számjegyű támogatási eset tükrözi, amelyet az Azure Portalon tekinthet meg.  A 15 számjegyű támogatási esethez nem várható más frissítés vagy állapot változása.
>
> Ha a támogatási eszközök közötti átmenetek az év folyamán is befejeződik, a kormányzati felhőben üzemeltetett támogatási élmény a nyilvános felhőben üzemeltetett Intune-előfizetésekhez jelenleg elérhető alapértelmezett *Súgó-és támogatási* élményhez hasonló.

1. Az Intune rendszergazdai hitelesítő adataival jelentkezzen be az Azure Portalra (<https://portal.azure.us>), majd válassza a **?** lehetőséget ikonra a portál jobb felső sarkában, majd a **Súgó + támogatás** lehetőség kiválasztásával lépjen tovább az [Azure Súgó + támogatás](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) oldalra.

   ![A kérdőjel hivatkozás képe a Súgó + támogatás hivatkozás kiemelésével](./media/get-support/azure-get-support.png)

2. Az Azure **Súgó + támogatás** lapon válassza az **új támogatási kérelem**lehetőséget.

   ![Az új támogatási kérelem hivatkozásának képe a Súgó és támogatás oldalon](./media/get-support/azure-support-ticket-link.png)

3. Az **alapismeretek** lapon a legtöbb Intune technikai támogatási probléma megoldásához válassza a következő lehetőségeket:
   - **Problématípus**: **Technikai**
   - **Előfizetés**: <*az előfizetését*>
   - **Szolgáltatás**: **Microsoft Intune**
   - **Probléma típusa**: válassza ki a probléma típusát a legördülő menüből.
   - **Probléma altípusa**: válassza ki a probléma altípust a legördülő menüből.
   - **Tárgy**: röviden írja le azt a problémát, amelyet segíteni szeretne.

   ![A Súgó + támogatás – új támogatási kérelem oldalon található alapismeretek lap képe](./media/get-support/help-new-support-case-basics.png)

   Válassza a **Tovább: megoldások** a folytatáshoz lehetőséget.
4. A **megoldások** lapon tekintse át a javasolt lépéseket, amelyek segíthetnek a probléma megoldásában a jegy bejelentése nélkül. Ha a lépések végrehajtása után is létre szeretne hozni egy támogatási kérést, kattintson a **Tovább gombra: részletek**.

   ![A Súgó + támogatás – új támogatási kérelem lap megoldások lapjának képe](./media/get-support/help-new-support-case-solutions.png)
5. A **részletek** lapon adja meg a probléma részleteit, a támogatási módszert, a kapcsolattartási adatokat, majd kattintson a Tovább gombra **: felülvizsgálat + létrehozás**.

   ![A Súgó + támogatás – új támogatási kérelem lap részletek lapjának képe](./media/get-support/help-new-support-case-details.png)
6. Tekintse át az adatokat, ellenőrizze, hogy helyes-e, majd válassza a **Létrehozás** lehetőséget a támogatási kérelem elküldéséhez.

   ![Az új támogatási kérelem oldalon található felülvizsgálat + Létrehozás lap képe](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>Ha számlázással vagy előfizetéssel kapcsolatos kérdése van, megnyithat egy esetet, hogy támogatást kapjon a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Támogatási kérelmek megtekintése  

A támogatási kéréseket a Azure Portalon belül tekintheti meg. A korlátozott információk azonban rendelkezésre állnak.  Az incidensek megtekintéséhez:

1. Az Intune rendszergazdai hitelesítő adataival jelentkezzen be az Azure-ba (<https://portal.azure.com>), majd válassza a **?** lehetőséget ikonra a portál jobb felső sarkában, majd a **Súgó + támogatás** lehetőség kiválasztásával lépjen tovább az [Azure Súgó + támogatás](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) oldalra.

2. A **Súgó + támogatás** lapon megtekintheti a **legutóbbi támogatási kérelmek**listáját.

   > [!IMPORTANT]  
   > A kormányzati ügyfelek számára a privát felhő csak a 15 számjegyű támogatási eset számát és az incidens állapotát tekintheti meg. A rendszer e-mailben küldi el a munkahelyi vagy riasztási kommunikációt és nyomon követést, valamint az Intune-konzolon megnyitott támogatási eset tükrözésével létrehozott 8 számjegyű támogatási eset számát.

## <a name="additional-resources"></a>További források  

- [Számlázási és előfizetés-kezelési támogatás](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Mennyiségi licencelés](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [A Intune hibáinak elhárítása](help-desk-operators.md)
