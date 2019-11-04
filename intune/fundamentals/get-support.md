---
title: Hogyan kérhet támogatást az Intune-hoz
titleSuffix: Microsoft Intune
description: A Microsoft Intune fizetős és próbaverziós előfizetéseihez online és telefonos segítséget kérhet.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1049bfeaf3840e1e6a711fd4df10b0a29a88b6b8
ms.sourcegitcommit: 85c894cb4df34a5ff558e3b45e28a8b91054d9e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432544"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Hogyan kérhet támogatást az Intune-hoz  
  
A Microsoft Intune-hoz a Microsoft globális műszaki, értékesítés előtti, számlázási és előfizetési támogatást nyújt. A támogatás interneten és telefonon is elérhető mind a fizetős, mind a próbaverziós előfizetésekhez. Az online műszaki támogatás angolul és japánul érhető el. Telefonos támogatás és online számlázási támogatás más nyelveken is elérhető.

Intune-rendszergazdaként használhatja a **Súgó és támogatás** lehetőséget az Intune-hoz készült online támogatási jegy a Azure Portalból való beküldéséhez. A támogatási incidensek létrehozásához és kezeléséhez a fióknak rendelkeznie kell egy Azure Active Directory (Azure AD) szerepkörrel, amely tartalmazza a **Microsoft. Office 365. supportTickets** *műveletet* . További információ a támogatási jegy létrehozásához szükséges Azure AD-szerepkörökről és engedélyekről: [rendszergazdai szerepkörök a Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).  

>[!IMPORTANT]  
> Ha olyan külső termékekhez szeretne műszaki támogatást igénybe venni, amelyek együttműködnek az Intune-nal (például a Saaswedo, a Cisco vagy a Lookout), akkor először forduljon ezeknek a termékeknek a szállítójához. Mielőtt megnyitja az Intune-nal kapcsolatos támogatási kérelmet, győződjön meg róla, hogy a másik terméket megfelelően konfigurálta.
>
> A Microsoft Intune hibaelhárítási problémáiról további információt az Intune dokumentációjának [hibaelhárítási szakaszában](help-desk-operators.md) találhat.

## <a name="known-issues-for-creating-support-incidents"></a>Támogatási incidensek létrehozásával kapcsolatos ismert problémák

Ha a fiókja rendelkezik a szükséges engedélyekkel, de nem tud sikeresen hozzáférni a súgóhoz és támogatáshoz, vagy támogatási incidenst szeretne létrehozni vagy kezelni, tekintse át a következő ismert problémákat és megoldásokat:

- A fiók elavult felhasználói jogkivonata. A probléma megoldásához jelentkezzen ki az összes aktív konzol-munkamenetből, jelentkezzen be újra, majd próbálkozzon egy támogatási incidens létrehozásával vagy kezelésével.
- Több aktív munkamenet. Ha egynél több felhasználóval vagy munkamenettel jelentkezett be, jelentkezzen ki az összes, de egyetlen konzolon. Ezt követően egyetlen aktív munkamenettel próbálkozhat a támogatási incidensek létrehozásával vagy kezelésével.

A hozzáférési problémák megoldásához szükséges további műveletek:

- Törölje az összes cookie-t az aktív böngésző-munkamenethez, majd próbálkozzon újra a támogatási incidens létrehozásával vagy kezelésével.
- InPrivate-böngészési munkamenet használatával jelentkezzen be az Intune-ba, és próbálkozzon egy támogatási incidens létrehozásával vagy kezelésével.

Ha az előző megkerülő megoldások nem segítenek, lépjen [Microsoft 365 felügyeleti központba](https://admin.microsoft.com) , és hozzon létre egy támogatási jegyet. Jelenleg olyan javításon dolgozunk, amely a nyár végén lesz elérhető.

## <a name="help-and-support-experience"></a>Súgó és támogatás  

Az Intune Súgó és támogatás szolgáltatását a [Microsoft 365 Eszközkezelő portálról](https://devicemanagement.microsoft.com) , valamint az Intune-ban található összes panelről (vagy lapokról) elérhető a Azure Portal. 

![Intune-lapok](./media/get-support/intune-blades.png)


A *Súgó és támogatás* funkció hasonló a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com/)látható élményhez, és lecseréli az előző *Súgó + támogatást*, amely az Azure egyéb szolgáltatásaira is érvényes marad. 

A Súgó és támogatás eléréséhez használja a következő lehetőségeket:  
- **Eszközkezelés irányítópultja:**
  - Miután kiválasztotta az Intune szolgáltatáshoz tartozó szolgáltatási területeket, válassza a **Súgó és támogatás**lehetőséget.
  - Az Eszközkezelő portál bármelyik csomópontján jelölje be a **?** ikonra a portál jobb felső sarkában, majd a legördülő listából válassza ki azt a szolgáltatást, amelyhez segítséget szeretne használni. A **?** az Eszközkezelő portál ikonja több szolgáltatást is támogat, és ki kell választania azt a szolgáltatást, amelyhez segítségre van szüksége.  

    ![Válassza ki a szolgáltatást](./media/get-support/select-a-service.png)

    A szolgáltatás kiválasztása után megjelenik a szolgáltatás *Súgó és támogatás* lapja, ahol [megadhatja](#specify-details-about-an-issue) a súgóhoz segítséget nyújtó konkrét probléma részleteit.  

    Ha a keresés eredményei úgy tűnik, hogy nem felelnek meg a szolgáltatás elvárásainak, ellenőrizze, hogy a helyes szolgáltatást választotta-e ki. A szolgáltatás kiválasztása csak a *Súgó és támogatás*után jelenik meg.  Ha a megfelelő szolgáltatás nem lett kiválasztva, kattintson a *válasszon ki egy szolgáltatást* , hogy visszatérjen a szolgáltatás kiválasztása legördülő listához.   

    ![A szolgáltatás megerősítése](./media/get-support/confirm-your-service-selection.png) 


- **A Azure Portalban:**
  - A **Súgó és támogatás** lehetőség kiválasztása bármely Intune-panelen vagy-lapon

  Ha a Azure Portal kiválasztja a **?** ikon a jobb felső sarokban, vagy a bal oldali navigációs ablaktáblán a **Súgó + támogatás** lehetőségre kattintva megnyithatja az Azure *Súgó + támogatás* szolgáltatását. Az Azure *Súgó és támogatás*szolgáltatásból nem nyithat meg közvetlenül Intune-támogatási incidenst, de az Intune *Súgó és támogatás* lapján az alábbi műveletek végrehajtásával érheti el: 
  1. Válassza az új támogatási kérelem lehetőséget.
  2. A probléma típusa mezőben adja meg a technikai értéket.
  3. A szolgáltatás mezőben válassza a Microsoft Intune.
  4. Válassza az Intune Súgó és támogatás lapját.

> [!NOTE]  
> Ha az Intune-példánya a nyilvános felhőben, más néven a kormányzati felhőben található, mint például a Azure Government, tekintse meg a jelen cikk későbbi, a [privát felhőhöz készült Intune-támogatás](#intune-support-for-private-cloud-for-government)című részét. Az Intune *Súgó és támogatás* felülete a következő év végéig nem érhető el a kormányzati privát felhőben. 


A *Súgó és támogatás*megnyitásakor a portálon egy olyan nézet jelenik meg, amely attól függ, hogy aktív támogatási incidensekkel rendelkezik-e, és ha van Premier szintű támogatás, néhány további elem és lehetőség is van:
- **Nincsenek aktív támogatási incidensek**: a **segítségre van szüksége?** oldalon láthatja, ahogy az Eszközkezelő irányítópultján az alábbi képen is látható.  
- **Aktív támogatási incidensek**: a [támogatási jegyek](#view-support-cases) oldal jelenik meg, amely az aktív incidensek listáját jeleníti meg.  
- **Premier szintű támogatási szerződés**: a felhasználói élmény ugyanaz, mint az első két lehetőség, de az alábbi további elemek is megjelennek a segítségre van szüksége? oldalala 
  - Ha a lap címe **segítségre van szüksége?** , megjelenik a Premier szintű támogatás banner:  
    ![Premier support banner](./media/get-support/premier-banner.png)
  - A lap **támogatásának beolvasása** részén megadhatja a kezdeti **súlyossági** szintet, ha telefonon keresztül hoz létre szolgáltatási kérést.


![Az eszközkezelés irányítópultja és a segítségre van szüksége? oldalala](./media/get-support/help-support-dashboard.png)

Ebben a nézetben a következő műveleteket végezheti el:

1. [Részletezheti](#specify-details-about-an-issue) az adott problémát, amellyel kapcsolatban segítségre szorul  
2. [Megtekintheti a környezetfüggő súgót](#view-context-sensitive-help) és azon kapcsolódó megoldásokat, amelyek az Ön által megadott részleteken alapulnak  
3. [Támogatást kérhet](#get-support) e-mailen vagy telefonon keresztül  
4. [Olyan támogatási eseteket tekinthet meg](#view-support-cases), amelyeket Ön nyitott korábban ezen új munkafolyam segítségével  

### <a name="specify-details-about-an-issue"></a>Adott probléma részletezése 

Ha a Súgó és támogatás szolgáltatást az új felület által támogatott helyről nyitja meg, akkor a segítségre **van szüksége?** lap nyílik meg. Ezen az oldalon részletesen kifejtheti az adott problémát. Amikor elkezdi beírni a részleteket, a konzol olyan általános témákat dob fel, amelyek az Ön által használt kulcsszavakon alapulnak. Válasszon ki egy kínált lehetőséget, vagy fejezze be a saját probléma leírását. Ha az Önt érintő problémát írja be, akkor kérdését a **Támogatás kérése** lehetőséget választva küldheti el. A lekérdezés elküldése után a konzol olyan környezetfüggő adatokat ad vissza, amelyek segíthetnek a probléma megoldásában.

A következőkben példákat láthat a beküldhető kérdésekre:
  
- *Nem lehet visszaállítani az iOS eszközt*  
- *Nem hozható létre feltételes hozzáférési szabályzat*  

![Probléma kifejtése a Segítségre szorul? oldalon](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Környezetfüggő súgó megtekintése 

Miután kiválasztotta a felkínált lehetőségek egyikét, vagy elküldte a saját kérését, a **Megoldások megtekintése** részben környezetfüggő találatok jelennek meg. Ezek a találatok tartalmazzák az Intune-hoz kapcsolódó önsegítő útmutatást, és az internetes keresés után megjelenített, a lekérdezési kritériumokon alapuló további találatokat is.  
![Találatok megtekintése](./media/get-support/view-results.png)

### <a name="get-support"></a>Támogatás igénylése 

Ha az önsegítő vagy webalapú útmutató nem segít a probléma megoldásában, a konzol használatával nyisson meg egy e-mail-vagy telefonos támogatási problémát.  
A **Segítségre szorul?** oldalon válassza ki a használni kívánt lehetőséget.  

  > [!NOTE] 
  > A támogatási e-mail-kérések nem érhetők el az összes bérlő számára.  

- E-mailes kérés esetén adja meg e-mail-címét, és tetszőlegesen csatolmányokat is küldhet levelében. A kérés megnyitásához válassza a **Küldés** elemet. 

  ![E-mailes kérés](./media/get-support/email-support.png)
  
- Telefonos kéréshez adja meg telefonszámát. Esetlegesen megadhatja e-mail-címét is, és csatolmányokat fűzhet a levélhez. A kérés küldéséhez válassza a Visszahívás elemet.  



   ![Telefonos kérés](./media/get-support/phone-support.png)

**Premier szintű támogatás**:  
Premier szintű támogatási szerződéssel a telefonos támogatási incidensek is létrehozhatók. Megadhatja a támogatási visszahívás **súlyosságát** is, és választhatja a támogatási jegy létrehozását a feladat kritikus szerződése alapján.  

![Premier szintű támogatási lehetőségek](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>Támogatási esetek megtekintése  

Az Előzmények gombra kattintva megtekintheti az Ön által létrehozott támogatási eseteket.  

![Támogatási esetek megtekintése](./media/get-support/view-support-tickets.png)

- Kizárólag az új munkafolyam használatával megnyitott támogatási esetek jeleníthetők meg e munkafolyamon belül. A megtekintéshez használja a Súgó és támogatás nézetet az Eszközkezelő konzolon vagy a Azure Portal Intune paneljén. Ezeket az eseteket nyolcjegyű számok jelölik. A Microsoft 365 felügyeleti központjában is megtekinthetők az esetek.  

- Az Intune Súgó és támogatás felületének használatakor megnyíló esetek nem változnak. A megtekintéshez olyan Súgó és támogatás nézetet kell használnia, amely nem része az Intune-élménynek vagy az eszközkezelés irányítópultjának. Ezek az esetek **117**-tel vagy **118**-cal kezdődő, 15 jegyű számokkal vannak ellátva. Megtekintheti őket:

    1. Az Intune rendszergazdai hitelesítő adataival jelentkezzen be az Azure-ba (<https://portal.azure.com>), majd válassza a *?* lehetőséget ikonra a portál jobb felső sarkában, majd a *Súgó + támogatás* lehetőség kiválasztásával lépjen tovább az [Azure Súgó + támogatás](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) oldalra.

    2. A **Súgó és támogatás** lapon megtekintheti a **legutóbbi támogatási kérelmek** listáját, és az egyes elemeket kijelölve további információt kaphat róluk.
 

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
> Ha a támogatási eszközök közötti váltás az év későbbi részében fejeződik be, a kormányzati felhőben üzemeltetett támogatási élmény az Intune-előfizetésekhez jelenleg elérhető alapértelmezett *Súgó-és támogatási* élményhez hasonló lesz. nyilvános felhő.  


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
   > A kormányzati számítási felhő ügyfelei csak a 15 számjegyű támogatási eset számát és az incidens állapotát tekinthetik meg. A rendszer e-mailben küldi el a munkahelyi vagy riasztási kommunikációt és nyomon követést, valamint az Intune-konzolon megnyitott támogatási eset tükrözésével létrehozott 8 számjegyű támogatási eset számát.   

## <a name="additional-resources"></a>További háttéranyagok  

- [Számlázási és előfizetés-kezelési támogatás](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Mennyiségi licencelés](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [A Intune hibáinak elhárítása](help-desk-operators.md)
