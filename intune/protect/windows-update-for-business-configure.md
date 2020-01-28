---
title: A Windows Update Vállalatoknak konfigurálása a Microsoft Intune-ban – Azure | Microsoft Docs
description: Windows 10 rendszerű szoftverfrissítések kezelése frissítési körök és szolgáltatás-frissítési szabályzat használatával. A megfelelőséget áttekintheti, és a frissítés telepítését a Windows Update for Business beállításaival szüneteltetheti Microsoft Intune használatával.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: beafee4eb22d641748ca41f8f4c01c48ead87741
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754337"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>Windows 10 rendszerű szoftverfrissítések kezelése az Intune-ban

Az Intune használatával kezelheti a Windows 10 rendszerű szoftverfrissítések telepítését a Windows Update for Business rendszerből.

A Windows Update Vállalatoknak használatával leegyszerűsítheti a frissítéskezelést. Nem kell jóváhagynia az eszközcsoportok egyes frissítéseit. A környezetek kockázatkezelését egy frissítéskibocsátási stratégia konfigurálásával intézheti. Az Intune lehetővé teszi a [frissítési beállítások konfigurálását](windows-update-settings.md) az eszközökön, és lehetővé teszi a frissítések telepítésének késleltetését. Azt is megakadályozhatja, hogy az eszközök új Windows-verziókat telepítsenek, hogy azok stabilak maradjanak, miközben az eszközök továbbra is telepíthetik a minőségi és biztonsági frissítéseket.

Az Intune csak a frissítési szabályzat-hozzárendeléseket tárolja, a frissítéseket nem. Az eszközök közvetlenül a Microsoft Update-hez fordulnak a frissítésekért.

Az Intune a következő házirend-típusokat biztosítja a frissítések kezeléséhez:

- **Windows 10 frissítési kör**: Ez a házirend olyan beállítások gyűjteménye, amelyek a Windows 10 frissítéseinek telepítésekor konfigurálhatók.

- **Windows 10 szolgáltatások frissítései (nyilvános előzetes verzió)** : Ez a szabályzat a megadott Windows-verzióra helyezi át az eszközöket, és az eszközökön beállított szolgáltatások lefagynak, amíg nem frissíti őket egy későbbi Windows-verzióra.  Habár a szolgáltatás verziója statikus marad, az eszközök továbbra is telepíthetik a szolgáltatás verziójához elérhető minőségi és biztonsági frissítéseket.

A Windows 10-es frissítési gyűrűkhöz és a Windows 10 rendszerhez készült szolgáltatásokhoz szabályzatokat rendelhet hozzá az eszközök csoportjaihoz. A Windows 10-es eszközök frissítéseinek kezeléséhez és az üzleti igényeknek megfelelő frissítési stratégia létrehozásához mindkét házirend-típust használhatja ugyanabban az Intune-környezetben.

További információ: [Frissítések kezelése a Vállalati Windows Update használatával](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="prerequisites"></a>Előfeltételek

A Windows 10 rendszerű eszközök Intune-ban való használatához a következő előfeltételeknek kell teljesülniük.

- A Windows 10 rendszerű számítógépeknek a következő Windows 10-es verziókat kell futtatniuk:
  - **Windows 10 frissítési gyűrűk**: 1607-es vagy újabb verzió
  - **Windows 10 szolgáltatás frissítései**: 1703-es vagy újabb verzió

- Windows Update a következő Windows 10 kiadásokat támogatja:
  - Windows 10
  - Windows 10 Team – Surface Hub eszközökhöz (nem támogatja a *Windows 10-es szolgáltatások frissítéseit*)
  - Windows Holographic for Business

    A Windows holografikus for Business támogatja a Windows-frissítések egy részhalmazát, beleértve a következőket:
    - **Az automatikus frissítés viselkedése**
    - **Microsoft-termékek frissítései**
    - **Karbantartási csatorna**: támogatja a **féléves csatornát** és a **féléves Channel (Targeted)** lehetőségeket. További információ: a [Windows holografikus kezelése](../fundamentals/windows-holographic-for-business.md).

  > [!NOTE]
  > Nem **támogatott verziók és kiadások**:
  > - Windows 10 mobil verzió  
  > - Windows 10 Enterprise LTSC. A Windows Update for Business (WUfB) jelenleg nem támogatja a *hosszú távú szolgáltatási csatornák* kiadásait. Alternatív javítási módszerek, például a WSUS vagy a Configuration Manager használatának megtervezése.

- Windows-eszközökön a **visszajelzések & a diagnosztika** > a **diagnosztikai és használati adatokat** **alapszintű**, **bővített**vagy **teljes**értékre kell beállítani.

  A Windows 10-es eszközök *diagnosztikai és használati adatokra* vonatkozó beállítását manuálisan is konfigurálhatja, vagy a Windows 10 és újabb rendszerekhez készült Intune-eszközök korlátozási profilját használhatja. Ha eszköz-korlátozási profilt használ, állítsa be a **használati adatok megosztására** szolgáló [eszköz korlátozási beállítását](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) legalább **alapszintű**értékre. Ez a beállítás a Windows 10 vagy újabb rendszerű eszközök korlátozási szabályzatának konfigurálásakor a **jelentéskészítés és a telemetria** kategóriában található.

  Az eszközprofilokról további információt nyújt az [Eszközkorlátozási beállítások konfigurálása](../configuration/device-restrictions-configure.md) című témakör.

## <a name="windows-10-update-rings"></a>Windows 10 frissítési gyűrűk

Olyan frissítési köröket hozhat létre, amelyek meghatározzák, hogy a Windows mint szolgáltatás hogyan frissíti a Windows 10-es eszközöket a funkció-és minőségi frissítésekkel. A Windows 10-ben az új funkció- és minőségi frissítések magukban foglalják valamennyi korábbi frissítés tartalmát. Ha a legújabb frissítést telepítette, akkor tudja, hogy a Windows 10 rendszerű eszközök naprakészek. A Windows korábbi verzióitól eltérően a frissítés egy része helyett már a teljes frissítést telepíteni kell.

A Windows 10-es frissítési gyűrűk támogatják a [hatókör címkéit](../fundamentals/scope-tags.md). A frissítési körökkel rendelkező hatókör-címkék segítségével szűrheti és kezelheti a használt konfigurációk készleteit.

### <a name="create-and-assign-update-rings"></a>Frissítési körök létrehozása és hozzárendelése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába]( https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **Windows** > **Windows 10 frissítési** körök > **Létrehozás**lehetőséget.

3. Az *alapvető beállítások*területen adjon meg egy nevet, egy leírást (nem kötelező), majd kattintson a **tovább**gombra.
  ![frissítési kör létrehozása]( ./media/windows-update-for-business-configure/basics-tab.png)
  
4. A **frissítési kör beállításai**területen konfigurálja az üzleti igényeknek megfelelő beállításokat. Az elérhető beállításokkal kapcsolatos további információkért lásd: a Windows Update beállításai. A *frissítési és felhasználói élmény* beállításainak konfigurálása után kattintson a **Tovább gombra**.

5. A **hatókör címkék**területen válassza a **+ hatókör címkék lehetőséget** a *címkék kiválasztása* ablaktábla megnyitásához, ha alkalmazni szeretné őket a frissítési gyűrűre. Válasszon ki egy vagy több címkét, majd kattintson a **kiválasztás** elemre, és adja hozzá őket a frissítési gyűrűhöz, és térjen vissza a *hatókör címke*s oldalára.

   Ha elkészült, kattintson a **tovább** gombra a *hozzárendelések*folytatásához.

6. A **hozzárendelések**alatt válassza a **+ csoportok kiválasztása lehetőséget** , majd a frissítési kört egy vagy több csoporthoz rendelje. **Válassza a + csoportok kiválasztása lehetőséget** a hozzárendelés finomhangolásához. A folytatáshoz kattintson a **tovább** gombra.

7. A**felülvizsgálat + létrehozás**területen tekintse át a beállításokat, majd válassza a **Létrehozás** lehetőséget, amikor készen áll a Windows 10-es frissítési kör mentéséhez. Az új frissítési kör megjelenik a frissítési körök listájában.

### <a name="manage-your-windows-10-update-rings"></a>Windows 10-es frissítési gyűrűk kezelése

A portálon navigáljon az **eszközök** > **Windows** > **Windows 10 Update-gyűrűk** elemre, és válassza ki a kezelni kívánt házirendet.  A szabályzat megnyílik az **Áttekintés** oldalára.

Ezen a lapon megtekintheti a gyűrűk hozzárendelési állapotát, és az Áttekintés ablaktábla felső részén található alábbi műveletek közül választhatja ki a frissítési kör kezelését:

- [Törlés](#delete)
- [Szünet](#pause)
- [Folytatása](#resume)
- [Kiterjesztése](#extend)
- [Eltávolítása](#uninstall)

![Elérhető műveletek](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>Törlés

A kiválasztott Windows 10-es frissítési kör beállításainak kényszerítéséhez válassza a **Törlés** lehetőséget. A gyűrű törlése eltávolítja annak konfigurációját az Intune-ból, így az Intune már nem érvényes, és nem kényszeríti ki ezeket a beállításokat.

A gyűrűnek az Intune-ból való törlése nem módosítja a frissítési gyűrűhöz rendelt eszközök beállításait.  Ehelyett az eszköz megtartja a jelenlegi beállításait. Az eszközök nem tartanak fenn korábbi rekordot a korábban megtartott beállításokról. Az eszközök további frissítési köröktől származó beállításokat is fogadhatnak, amelyek aktívak maradnak.

##### <a name="to-delete-a-ring"></a>Gyűrű törlése

1. Egy frissítési kör Áttekintés lapjának megtekintésekor válassza a **Törlés**lehetőséget.
2. Válassza az **OK** gombot.

#### <a name="pause"></a>Szünet

A **pause (szüneteltetés** ) lehetőség kiválasztásával megakadályozhatja, hogy a hozzárendelt eszközök a szolgáltatáshoz tartozó frissítéseket és a minőségi frissítéseket a gyűrű szüneteltetése után akár 35 napig is megkapják. A megadott időtartam után a felfüggesztés automatikusan megszűnik, és az eszköz keresni kezdi az alkalmazható Windows-frissítéseket. A keresés után a frissítések ismét felfüggeszthetők.
Ha folytatja a szüneteltetett frissítési kör folytatását, majd újra szünetelteti a gyűrűt, a szüneteltetési időszak 35 napra visszaállítható.

##### <a name="to-pause-a-ring"></a>Gyűrű szüneteltetése

1. Egy frissítési kör Áttekintés lapjának megtekintésekor válassza a **szüneteltetés**lehetőséget.
2. Válassza a **funkció** vagy a **minőség** lehetőséget a frissítés szüneteltetéséhez, majd kattintson **az OK gombra**.
3. Egy frissítési típus felfüggesztése után a másik frissítési típus szüneteltetéséhez válassza a Szüneteltetés újra lehetőséget.

Ha a frissítési típus szüneteltetve van, az adott gyűrű áttekintő panelje azt jeleníti meg, hogy hány nap van hátra a frissítési típus folytatása előtt.

> [!IMPORTANT]
> A szüneteltetési parancs kiadása után az eszközök akkor kapják meg ezt a parancsot, amikor legközelebb bejelentkeznek a szolgáltatásba. Megtörténhet, hogy mielőtt bejelentkeznek, még telepítenek egy ütemezett frissítést. Ha az adott eszköz ki van kapcsolva a felfüggesztési parancs kiadásakor, akkor a bekapcsolása után esetleg letölthet és telepíthet ütemezett frissítéseket, mielőtt bejelentkezik az Intune-ba.

#### <a name="resume"></a>Folytatása

Amíg a frissítési kör szünetel, a **Folytatás** gombra kattintva visszaállíthatja a szolgáltatás és a minőségi frissítéseket az adott gyűrű aktív működéséhez. A frissítési kör folytatása után újra szüneteltetheti a gyűrűt.

##### <a name="to-resume-a-ring"></a>Gyűrű folytatása

1. Ha megtekinti a szüneteltetett frissítési kör áttekintés lapját, válassza a **Folytatás**lehetőséget.
2. Válassza ki az elérhető lehetőségek közül a **funkció** vagy a **minőségi** frissítések folytatásához, majd kattintson **az OK gombra**.
3. Egy frissítési típus folytatása után a másik frissítés folytatásához válassza a folytatás újra lehetőséget.

#### <a name="extend"></a>Kiterjesztése  

Amíg a frissítési kör szünetel, a **kiterjesztés** lehetőség kiválasztásával alaphelyzetbe állíthatja a szüneteltetési időszakot a szolgáltatás és a minőségi frissítések esetében az adott frissítési kör 35 napra.

##### <a name="to-extend-the-pause-period-for-a-ring"></a>A szünet időtartamának meghosszabbítása egy adott gyűrűn

1. Ha megtekinti a szüneteltetett frissítési kör áttekintés lapját, válassza a **kiterjesztés**lehetőséget.
2. Válassza ki az elérhető lehetőségek közül a **funkció** vagy a **minőségi** frissítések folytatásához, majd kattintson **az OK gombra**.
3. Miután kiterjesztte az egyik frissítési típus szüneteltetését, kiválaszthatja az újbóli bővítés lehetőséget a másik frissítési típus kiterjesztéséhez.

#### <a name="uninstall"></a>Eltávolítás  

Az Intune-rendszergazdák az **Eltávolítás** használatával eltávolíthatják (visszaállítják) a legújabb *szolgáltatás* frissítését, vagy egy aktív vagy szüneteltetett frissítési kör legújabb *minőségi* frissítését. Egy típus eltávolítását követően eltávolíthatja a másik típust. Az Intune nem támogatja vagy nem felügyeli, hogy a felhasználók nem tudják eltávolítani a frissítéseket.  

> [!IMPORTANT]
> Az *eltávolítási* lehetőség használatakor az Intune azonnal átadja az eltávolítási kérést az eszközöknek.
>
> - A Windows-eszközök azonnal megkezdik a frissítések eltávolítását, amint megkapják az Intune-szabályzat módosításait. A frissítés eltávolítása nem korlátozódik a karbantartási ütemtervekre, még akkor is, ha azok a frissítési kör részeként vannak konfigurálva.
> - Ha a frissítés eltávolításához az eszköz újraindítása szükséges, az eszköz újraindul, anélkül, hogy az eszköz felhasználóinak késleltetést kellene felajánlani.

Az Eltávolítás sikerességéhez:

- Az eszköznek a Windows 10 április 2018 frissítést (1803-es verzió) vagy újabb verzióját kell futtatnia.

Az eszköznek telepítenie kell a legújabb frissítést. Mivel a frissítések összegző jellegűek, a legújabb frissítést telepítő eszközök a legújabb szolgáltatás-és minőségi frissítést fogják tartalmazni. Ha ezt a lehetőséget választja, akkor az utolsó frissítés visszavonása előtt érdemes felderíteni a problémát a Windows 10-es gépeken.

Az Eltávolítás használatakor vegye figyelembe a következőket:

- A funkciófrissítések és minőségi frissítések eltávolításának lehetősége csak ahhoz a karbantartási csatornához érhető el, amelyhez az eszköz tartozik.

- Ha a szolgáltatás vagy a minőségi frissítések eltávolítását használja, a a Windows 10-es gépek korábbi frissítésének visszaállítására szolgáló szabályzatot indít el.

- Egy Windows 10-es eszközön a minőségi frissítés sikeres visszavonása után az eszköz felhasználói továbbra is megtekinthetik a **Windows beállításai** > **frissítések** > **frissítési előzmények**című témakörben felsorolt frissítést.

- A szolgáltatások frissítéseinek kimondottan a frissítés eltávolításának ideje 2-60 nap. Ezt az időszakot a frissítési körök frissítési beállításának **beállítása a szolgáltatás frissítésének eltávolítási időtartama (2 – 60 nap)** . Az eszközre telepített szolgáltatás frissítése nem állítható vissza, ha a frissítés a beállított eltávolítási időtartamnál hosszabb ideig lett telepítve.

  Tegyük fel például, hogy egy frissítési gyűrű egy 20 napos szolgáltatás-frissítési eltávolítási időszakmal rendelkezik. 25 nap elteltével állítsa vissza a legújabb funkció frissítését, és használja az Eltávolítás lehetőséget.  Azok az eszközök, amelyek több mint 20 nappal ezelőtt telepítették a szolgáltatást, nem tudják eltávolítani, mert a karbantartási folyamat részeként eltávolítottak a szükséges biteket. Azonban azok az eszközök, amelyek csak a 19 napos frissítést telepítették, eltávolíthatják a frissítést, ha sikeresen bejelentkeznek az eltávolítási parancs fogadására, mielőtt meghaladják a 20 napos eltávolítási időszakot.

Windows Update házirendekkel kapcsolatos további információkért lásd: a [CSP frissítése](https://docs.microsoft.com/windows/client-management/mdm/update-csp) a Windows ügyfél-felügyeleti dokumentációjában.

##### <a name="to-uninstall-the-latest-windows-10-update"></a>A Windows 10 legújabb frissítésének eltávolítása

1. Ha megtekinti a szüneteltetett frissítési kör áttekintés lapját, válassza az **Eltávolítás**lehetőséget.
2. Válasszon az elérhető lehetőségek közül a **szolgáltatás** vagy a **minőségi** frissítések eltávolításához, majd kattintson **az OK gombra**.
3. Miután elindította az eltávolítást egy frissítési típusra, az Eltávolítás lehetőség kiválasztásával távolítsa el a fennmaradó frissítési típust.

## <a name="windows-10-feature-updates"></a>Windows 10 szolgáltatás frissítései

*Ez a funkció nyilvános előzetes verzióban érhető el.*

A *Windows 10 szolgáltatásainak*használatával kiválaszthatja a Windows-szolgáltatás azon verzióját, amelyre az eszközöket szeretné használni, például a windows 10 1803-es vagy 1809-es verzióját. 1803-es vagy újabb szolgáltatási szintet is beállíthat.

Ha egy eszköz megkapja a Windows 10-es szolgáltatáshoz tartozó frissítési szabályzatot:

- Az eszköz frissíti a házirendben megadott Windows-verzióra. Egy eszköz, amely már futtatja a Windows újabb verzióját, a jelenlegi verzióban marad. A verzió befagyasztásával az eszközök funkció a szabályzat időtartama alatt stabil marad.

- Habár a Windows telepített verziója továbbra is be van állítva, az eszközök továbbra is kaphatnak és telepíthetnek minőségi és biztonsági frissítéseket a Windows-verziójuk számára az adott verzió támogatásának időtartamára, ami segít az eszközök aktuális és biztonságos megőrzésében.

- A *pause* és egy frissítési gyűrű használatával ellentétben, amely 35 nap után lejár, a Windows 10-es szolgáltatások frissítési szabályzata érvényben marad. Az eszközök nem telepítik az új Windows-verziót, amíg nem módosítja vagy nem távolítja el a Windows 10 szolgáltatás frissítési szabályzatát. Ha szerkeszti a házirendet egy újabb verzió megadásához, az eszközök ezt a Windows-verziót telepíthetik a szolgáltatásból.

### <a name="prerequisites-for-windows-10-feature-updates"></a>A Windows 10-es szolgáltatások frissítéseinek előfeltételei

Az Intune-ban a Windows 10-es funkcióinak használatához a következő előfeltételeknek kell teljesülniük.

- Az eszközöket regisztrálni kell az Intune MDM és az Azure AD-hez csatlakoztatott vagy az Azure AD-ben regisztrált eszközökön.
- Ha az Intune-nal szeretné használni a szolgáltatás-frissítési szabályzatot, az eszközökön be kell kapcsolni az telemetria-t, az [*alapszintű*](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry)minimális beállítással. A telemetria a *jelentéskészítés és a telemetria* alatt van konfigurálva az [eszköz korlátozási szabályzatának](../configuration/device-restrictions-configure.md)részeként.
  
  Azok az eszközök, amelyek szolgáltatás-frissítési házirendet kapnak, és amelyek Telemetria beállítása *nincs konfigurálva*, ami azt jelenti, hogy ki van kapcsolva, a Windows újabb verzióját telepítheti, mint a szolgáltatás frissítési házirendjében meghatározottak szerint. A telemetria megkövetelésének előfeltétele felülvizsgálat alatt áll, mivel ez a funkció az általános elérhetőség irányába mozdul.

### <a name="limitations-for-windows-10-feature-updates"></a>A Windows 10-es szolgáltatások frissítéseinek korlátai

- Ha egy *Windows 10* rendszerre vonatkozó frissítési szabályzatot egy olyan eszközre telepít, amely a *Windows 10-es frissítési kör* házirendjét is megkapja, tekintse át a frissítési kört a következő konfigurációk esetén:
  - A **frissítési késleltetési időszak (nap)** értékének **0**értékűnek kell lennie.
  - A frissítési gyűrű szolgáltatás frissítéseinek *futniuk*kell. Nem szabad szüneteltetni őket.

- A Windows 10 szolgáltatás frissítési házirendjei nem alkalmazhatók az Autopilot-ből a Box Experience (OOBE) alkalmazásban, és csak az első Windows Update vizsgálatra érvényesek, miután egy eszköz befejezte az üzembe helyezést (ez általában egy nap).

### <a name="create-and-assign-windows-10-feature-updates"></a>Windows 10 rendszerű szolgáltatások frissítéseinek létrehozása és kiosztása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > a **Windows** > **Windows 10-es szolgáltatások** > **Létrehozás**lehetőséget.

3. Az **alapvető beállítások**területen adja meg a kívánt szolgáltatást, a leírását (nem kötelező) és a **szolgáltatások frissítését**, és válassza ki a Windows-verziót, amelyhez a kívánt szolgáltatáskészlet tartozik, majd válassza a **tovább**lehetőséget.

4. A **hozzárendelések**alatt válassza a **+ csoportok kiválasztása** lehetőséget, majd rendelje hozzá a szolgáltatás frissítésének központi telepítését egy vagy több csoporthoz. A folytatáshoz kattintson a **tovább** gombra.

5. A **felülvizsgálat + létrehozás**területen tekintse át a beállításokat, majd válassza a **Létrehozás** lehetőséget, amikor készen áll a Windows 10-es szolgáltatás frissítési házirendjének mentéséhez.  

### <a name="manage-windows-10-feature-updates"></a>A Windows 10-es szolgáltatások frissítéseinek kezelése

A felügyeleti központban lépjen az **eszközök** > **Windows** > **Windows 10 funkció frissítése** elemre, és válassza ki a kezelni kívánt házirendet. Megnyílik a házirend az **Áttekintés** ablaktábláján.

Ebből a panelből a következőket teheti:

- A **Törlés** lehetőség kiválasztásával törölheti a szabályzatot az Intune-ból, és eltávolíthatja az eszközökről.
- A központi telepítés módosításához válassza a **Tulajdonságok** lehetőséget.  A *Tulajdonságok* ablaktáblán válassza a **Szerkesztés** lehetőséget a *központi telepítési beállítások vagy hozzárendelések*megnyitásához, ahol módosíthatja a központi telepítést.
- A szabályzattal kapcsolatos információk megtekintéséhez válassza a **végfelhasználói frissítés állapota** lehetőséget.

## <a name="next-steps"></a>További lépések

[Az Intune által támogatott Windows Update-beállítások](../windows-update-settings.md)

[Intune-megfelelőségi jelentések a frissítésekhez](../windows-update-compliance-reports.md)

[A Windows 10 frissítési gyűrűk hibaelhárítása](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)