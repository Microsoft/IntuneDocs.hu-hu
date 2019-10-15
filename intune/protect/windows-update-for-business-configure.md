---
title: Vállalati Windows Update konfigurálása a Microsoft Intuneban – Azure | Microsoft Docs
description: Frissítse a profil szoftverfrissítési beállításait egy frissítési kör létrehozásához, a megfelelőség ellenőrzéséhez és a frissítések szüneteltetéséhez Windows Update üzleti beállításokhoz Microsoft Intune használatával Windows 10-es eszközökön.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa8cc396c05150006799c1e9b86ecb63351cdb36
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314714"
---
# <a name="manage-software-updates-in-intune"></a>Szoftverfrissítések kezelése az Intune-ban

Az Intune segítségével definiálhatja a frissítési köröket, amelyek meghatározzák, hogy a Windows mint szolgáltatás hogyan frissíti a Windows 10-es eszközöket. A frissítési körök az eszközök csoportjaihoz hozzárendelt szabályzatok. Az Update Rings használatával olyan frissítési stratégiát hozhat létre, amely az üzleti igényeket tükrözi. További információ: [frissítések kezelése a Windows Update for Business használatával](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

A Windows 10 rendszerben az új szolgáltatás-és minőségi frissítések tartalmazzák az összes korábbi frissítés tartalmát. Ha a legújabb frissítést telepítette, akkor tudja, hogy a Windows 10 rendszerű eszközök naprakészek. A Windows korábbi verzióitól eltérően mostantól a frissítés része helyett a teljes frissítést kell telepítenie.


A Windows Update for Business használatával egyszerűbbé válik az Update Management-élmény. Az eszközök csoportjaihoz nem kell jóváhagynia az egyes frissítéseket. A környezetek kockázatait a frissítés bevezetési stratégiájának konfigurálásával kezelheti. Az Intune lehetővé teszi a [frissítési beállítások konfigurálását](../windows-update-settings.md) az eszközökön, és lehetővé teszi a frissítések telepítésének késleltetését. Az Intune nem tárolja a frissítéseket, de csak a frissítési szabályzat-hozzárendelést. Az eszközök közvetlenül a frissítésekhez Windows Update férnek hozzá. Azon beállítások gyűjteménye, amelyek a Windows 10 frissítéseinek telepítése során konfigurálhatók, *Windows 10-es frissítési gyűrűnek*nevezzük.

A Windows 10-es frissítési gyűrűk támogatják a [hatókör címkéit](../fundamentals/scope-tags.md). A frissítési körökkel rendelkező hatókör-címkék segítségével szűrheti és kezelheti a használt konfigurációk készleteit.

## <a name="prerequisites"></a>Előfeltételek  

A Windows 10 rendszerű eszközök Intune-ban való használatához a következő előfeltételeknek kell teljesülniük.  

- A Windows 10 rendszerű számítógépeken legalább Windows 10 Pro rendszernek kell futnia a Windows évfordulós frissítéssel vagy újabb verzióval (1607-es vagy újabb verzió)
- Windows Update a következő Windows 10 kiadásokat támogatja:
  - Windows 10
  - Windows 10 Team (Surface Hub eszközökhöz)
  - Windows holografikus vállalatoknak  

    A Windows holografikus for Business támogatja a Windows-frissítések egy részhalmazát, beleértve a következőket:
    - **Automatikus frissítési viselkedés**
    - **Microsoft-termékek frissítései**
    - **Karbantartási csatorna**: támogatja a **féléves csatornát** és a **féléves Channel (Targeted)** lehetőségeket. További információ: a [Windows holografikus kezelése](../fundamentals/windows-holographic-for-business.md).  

    > [!NOTE]  
    > Nem **támogatott verziók és kiadások**:
    > - Windows 10 Mobile  
    > - Windows 10 Enterprise LTSC. A Windows Update for Business (WUfB) jelenleg nem támogatja a *hosszú távú szolgáltatási csatornák* kiadásait. Alternatív javítási módszerek, például a WSUS vagy a Configuration Manager használatának megtervezése.  

- Windows-eszközökön a **visszajelzések & a diagnosztika** >  a**diagnosztikai és használati adatokat** **alapszintű**, **bővített**vagy **teljes**értékre kell beállítani.  

  A Windows 10-es eszközök *diagnosztikai és használati adatokra* vonatkozó beállítását manuálisan is konfigurálhatja, vagy a Windows 10 és újabb rendszerekhez készült Intune-eszközök korlátozási profilját használhatja. Ha eszköz-korlátozási profilt használ, állítsa be a **használati adatok megosztására** szolgáló [eszköz korlátozási beállítását](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) legalább **alapszintű**értékre. Ez a beállítás a Windows 10 vagy újabb rendszerű eszközök korlátozási szabályzatának konfigurálásakor a **jelentéskészítés és a telemetria** kategóriában található.

  További információ az eszközök profiljairól: az [eszközök korlátozási beállításainak konfigurálása](../configuration/device-restrictions-configure.md).  

- Ha a klasszikus Azure portált használja, a [beállításokat áttelepítheti a Azure Portalra](#migrate-update-settings-to-the-azure-portal).  


## <a name="create-and-assign-update-rings"></a>Frissítési körök létrehozása és kiosztása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza a **szoftverfrissítések** > **Windows 10 frissítési**körök  > **Létrehozás**elemet.
4. Adjon meg egy nevet, egy leírást (nem kötelező), majd válassza a **Konfigurálás**lehetőséget.
5. A **Beállítások**területen konfigurálja az üzleti igényeknek megfelelő beállításokat. Az elérhető beállításokkal kapcsolatos további információkért lásd: a [Windows Update beállításai](../windows-update-settings.md).  
6. Ha elkészült, kattintson az **OK** gombra. A **Frissítési kör létrehozása** területen kattintson a **Létrehozás** elemre. Az új frissítési kör a frissítési körök listájában jelenik meg.
7. A gyűrű hozzárendeléséhez válassza ki a kívánt gyűrűt a frissítési körök listájában, majd a \<ring neve > lapon válassza a **hozzárendelések**lehetőséget.
8. A **Belefoglalás** és **kizárás** lapok használatával meghatározhatja, hogy mely csoportokhoz legyen hozzárendelve a gyűrű, majd válassza a **Mentés** lehetőséget a hozzárendelés befejezéséhez.

## <a name="manage-your-windows-10-update-rings"></a>Windows 10-es frissítési gyűrűk kezelése
A portálon kiválaszthatja a Windows 10 frissítési gyűrűjét az **Áttekintés** panel megnyitásához. Ebből a panelből megtekintheti a gyűrűk hozzárendelési állapotát, és további műveleteket hajthat végre a gyűrű kezeléséhez. 
### <a name="to-view-an-updates-rings-overview-pane"></a>A frissítési körök áttekintése panel megtekintése: 
1. Jelentkezzen be az Azure portálra.
2. Navigáljon az **Intune** > **szoftverfrissítések** > **Windows 10 frissítési**körök elemre.
3. Válassza ki a megtekinteni vagy kezelni kívánt frissítési kört.  

A hozzárendelési állapot megtekintése mellett a következő műveleteket is kiválaszthatja az Áttekintés ablaktábla tetején a frissítési kör kezeléséhez:  
- [Törlés](#delete)  
- [Szünet](#pause)  
- [Folytatása](#resume)  
- [Kiterjesztése](#extend)  
- [Eltávolítás](#uninstall)  

![Elérhető műveletek](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Törlés  
A kiválasztott Windows 10-es frissítési kör beállításainak kényszerítéséhez válassza a **Törlés** lehetőséget. A gyűrű törlése eltávolítja annak konfigurációját az Intune-ból, így az Intune már nem érvényes, és nem kényszeríti ki ezeket a beállításokat.  

A gyűrűnek az Intune-ból való törlése nem módosítja a frissítési gyűrűhöz rendelt eszközök beállításait.  Ehelyett az eszköz megtartja a jelenlegi beállításait. Az eszközök nem tartanak fenn korábbi rekordot a korábban megtartott beállításokról. Az eszközök további frissítési köröktől származó beállításokat is fogadhatnak, amelyek aktívak maradnak.  

#### <a name="to-delete-a-ring"></a>Gyűrű törlése  
1. Egy frissítési kör Áttekintés lapjának megtekintésekor válassza a **Törlés**lehetőséget.  
2. Kattintson az **OK** gombra.  

### <a name="pause"></a>Szünet  
A **pause (szüneteltetés** ) lehetőség kiválasztásával megakadályozhatja, hogy a hozzárendelt eszközök a szolgáltatáshoz tartozó frissítéseket és a minőségi frissítéseket a gyűrű szüneteltetése után akár 35 napig is megkapják. A maximális napok lejárta után a Szüneteltetés funkció automatikusan lejár, és az eszköz megvizsgálja a Windows-frissítéseket a megfelelő frissítésekhez. A vizsgálat után újra szüneteltetheti a frissítéseket. Ha folytatja a szüneteltetett frissítési kör folytatását, majd újra szünetelteti a gyűrűt, a szüneteltetési időszak 35 napra visszaállítható.  

#### <a name="to-pause-a-ring"></a>Gyűrű szüneteltetése  
1. Egy frissítési kör Áttekintés lapjának megtekintésekor válassza a **szüneteltetés**lehetőséget.  
2. Válassza a **funkció** vagy a **minőség** lehetőséget a frissítés szüneteltetéséhez, majd kattintson **az OK gombra**.  
3. Egy frissítési típus felfüggesztése után a másik frissítési típus szüneteltetéséhez válassza a Szüneteltetés újra lehetőséget.  

Ha a frissítési típus szüneteltetve van, az adott gyűrű áttekintő panelje azt jeleníti meg, hogy hány nap van hátra a frissítési típus folytatása előtt.

> [!IMPORTANT]  
> A szüneteltetési parancs kiadása után az eszközök akkor kapják meg ezt a parancsot, amikor legközelebb bejelentkeznek a szolgáltatásba. Előfordulhat, hogy a bejelentkezés előtt telepítenek egy ütemezett frissítést. Emellett, ha egy megtekintett eszköz ki van kapcsolva a szüneteltetési parancs kiadásakor, a bekapcsolásakor előfordulhat, hogy az Intune-ba való bejelentkezés előtt letölti és telepíti az ütemezett frissítéseket.

### <a name="resume"></a>Folytatás  
Amíg a frissítési kör szünetel, a **Folytatás** gombra kattintva visszaállíthatja a szolgáltatás és a minőségi frissítéseket az adott gyűrű aktív működéséhez. A frissítési kör folytatása után újra szüneteltetheti a gyűrűt.  

#### <a name="to-resume-a-ring"></a>Gyűrű folytatása  
1. Ha megtekinti a szüneteltetett frissítési kör áttekintés lapját, válassza a **Folytatás**lehetőséget.  
2. Válassza ki az elérhető lehetőségek közül a **funkció** vagy a **minőségi** frissítések folytatásához, majd kattintson **az OK gombra**.  
3. Egy frissítési típus folytatása után a másik frissítés folytatásához válassza a folytatás újra lehetőséget.  

### <a name="extend"></a>Bővíthető  
Amíg a frissítési kör szünetel, a **kiterjesztés** lehetőség kiválasztásával alaphelyzetbe állíthatja a szüneteltetési időszakot a szolgáltatás és a minőségi frissítések esetében az adott frissítési kör 35 napra.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>A szünet időtartamának meghosszabbítása egy adott gyűrűn  
1. Ha megtekinti a szüneteltetett frissítési kör áttekintés lapját, válassza a **kiterjesztés**lehetőséget. 
2. Válassza ki az elérhető lehetőségek közül a **funkció** vagy a **minőségi** frissítések folytatásához, majd kattintson **az OK gombra**.  
3. Miután kiterjesztte az egyik frissítési típus szüneteltetését, kiválaszthatja az újbóli bővítés lehetőséget a másik frissítési típus kiterjesztéséhez.  

### <a name="uninstall"></a>Eltávolítás  
Az Intune-rendszergazdák az **Eltávolítás** használatával eltávolíthatják (visszaállítják) a legújabb *szolgáltatás* frissítését, vagy egy aktív vagy szüneteltetett frissítési kör legújabb *minőségi* frissítését. Egy típus eltávolítását követően eltávolíthatja a másik típust. Az Intune nem támogatja vagy nem felügyeli, hogy a felhasználók nem tudják eltávolítani a frissítéseket.  

> [!IMPORTANT] 
> Az *eltávolítási* lehetőség használatakor az Intune azonnal átadja az eltávolítási kérést az eszközöknek. 
> - A Windows-eszközök azonnal megkezdik a frissítések eltávolítását, amint megkapják az Intune-szabályzat módosításait. A frissítés eltávolítása nem korlátozódik a karbantartási ütemtervekre, még akkor is, ha azok a frissítési kör részeként vannak konfigurálva. 
> - Ha a frissítés eltávolításához az eszköz újraindítása szükséges, az eszköz újraindul, anélkül, hogy az eszköz felhasználóinak késleltetést kellene felajánlani.


Az Eltávolítás sikerességéhez:  
- Az eszköznek a Windows 10 április 2018 frissítést (1803-es verzió) vagy újabb verzióját kell futtatnia.  

Az eszköznek telepítenie kell a legújabb frissítést. Mivel a frissítések összegző jellegűek, a legújabb frissítést telepítő eszközök a legújabb szolgáltatás-és minőségi frissítést fogják tartalmazni. Ha ezt a lehetőséget választja, akkor az utolsó frissítés visszavonása előtt érdemes felderíteni a problémát a Windows 10-es gépeken.  

Az Eltávolítás használatakor vegye figyelembe a következőket:  
- A szolgáltatás-vagy minőségi frissítés eltávolítása csak az eszközön lévő karbantartási csatornához érhető el.  

- Ha a szolgáltatás vagy a minőségi frissítések eltávolítását használja, a a Windows 10-es gépek korábbi frissítésének visszaállítására szolgáló szabályzatot indít el.  

- Egy Windows 10-es eszközön a minőségi frissítés sikeres visszaállítását követően a végfelhasználók továbbra is megtekinthetik a **Windows beállításai** > **frissítések** > **frissítési előzmények**című témakörben felsorolt frissítést.  

- A szolgáltatások frissítéseinek kimondottan a szolgáltatás frissítésének elindításához szükséges idő 2-60 nap, a frissítési körök frissítési beállításának beállítása a **szolgáltatás frissítésének eltávolítási időtartama (2 – 60 nap)** . Az eszközre telepített szolgáltatás frissítése nem állítható vissza, ha a szolgáltatás frissítése a beállított eltávolítási időtartamnál hosszabb ideig van telepítve.  

  Tegyük fel például, hogy egy frissítési gyűrű egy 20 napos szolgáltatás-frissítési eltávolítási időszakmal rendelkezik. 25 nap elteltével állítsa vissza a legújabb funkció frissítését, és használja az Eltávolítás lehetőséget.  Azok az eszközök, amelyek több mint 20 nappal ezelőtt telepítették a szolgáltatást, nem tudják eltávolítani, mert a karbantartásuk részeként eltávolítottak a szükséges biteket. Azonban azok az eszközök, amelyek csak a 19 nappal ezelőtt telepítették a szolgáltatást, eltávolíthatják a frissítést, ha sikeresen bejelentkeznek az eltávolítási parancs fogadására a 20 napos eltávolítási időszak meghaladása előtt.  

Windows Update házirendekkel kapcsolatos további információkért lásd: a [CSP frissítése](https://docs.microsoft.com/windows/client-management/mdm/update-csp) a Windows ügyfél-felügyeleti dokumentációjában.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>A Windows 10 legújabb frissítésének eltávolítása  
1. Ha megtekinti a szüneteltetett frissítési kör áttekintés lapját, válassza az **Eltávolítás**lehetőséget.  
2. Válasszon az elérhető lehetőségek közül a **szolgáltatás** vagy a **minőségi** frissítések eltávolításához, majd kattintson **az OK gombra**.  
3. Miután elindította az eltávolítást egy frissítési típusra, az Eltávolítás lehetőség kiválasztásával távolítsa el a fennmaradó frissítési típust.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Frissítési beállítások áttelepítése a Azure Portalre  
A klasszikus Azure portálon korlátozott számú egyéb Windows 10 frissítési beállítás is található az eszköz konfigurációs profiljában. Ha ezen beállítások bármelyike konfigurálva van a Azure Portalra való áttelepítéskor, javasoljuk, hogy végezze el a következő műveleteket:  

1. A szükséges beállításokkal hozzon létre Windows 10-es frissítési köröket a Azure Portal. Az **előzetes verziójú szolgáltatások engedélyezése** beállítás nem támogatott a Azure Portalban, mert már nem alkalmazható a legújabb Windows 10-es buildekre. A frissítési körök létrehozásakor beállíthatja a másik három beállítást, valamint a Windows 10 frissítéseinek egyéb beállításait is.  

   > [!NOTE]  
   > A klasszikus portálon létrehozott Windows 10 frissítési beállítások nem jelennek meg az Azure Portal az áttelepítés után. Ezeket a beállításokat azonban alkalmazza a rendszer. Ha ezeket a beállításokat telepíti át, és az áttelepített szabályzatot a Azure Portal módosítja, akkor ezek a beállítások törlődnek a szabályzatból.  

2. Törölje a frissítési beállításokat a klasszikus portálon. Miután áttelepítette a Azure Portalra, és ugyanazokat a beállításokat adja hozzá egy frissítési gyűrűhöz, törölnie kell a beállításokat a klasszikus portálon, hogy elkerülje a lehetséges házirend-ütközéseket. Ha például ugyanaz a beállítás eltérő értékekkel van konfigurálva, ütközés van. Nem könnyű tudni, mert a klasszikus portálon konfigurált beállítás nem jelenik meg a Azure Portal.  

## <a name="next-steps"></a>Következő lépések
[Az Intune által támogatott Windows Update-beállítások](../windows-update-settings.md)  

[Intune-megfelelőségi jelentések a frissítésekhez](../windows-update-compliance-reports.md)

[A Windows 10 frissítési gyűrűk hibaelhárítása](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

