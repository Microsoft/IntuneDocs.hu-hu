---
title: Az Intune használata a Microsoft Defender ATP-Azure által észlelt biztonsági rések javításához | Microsoft Docs
description: Tekintse meg, hogyan kezelheti a biztonsági feladatokat a és a veszélyforrások elleni & sebezhetőségek kezelése, a Microsoft Defender komplex veszélyforrások elleni védelem (ATP) részeként az Intune-konzolon.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69f214b4fd3f3b7767e719c0f68f19e178a8e29c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167250"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Az Intune használata a Microsoft Defender ATP által azonosított sebezhetőségek javítására  

Ha integrálja az Intune-t a Microsoft Defender komplex veszélyforrások elleni védelemmel (ATP), kihasználhatja a ATPs veszélyforrások elleni & sebezhetőségek felügyeletét (TVM), és az Intune használatával javíthatja a TVM által azonosított végponti gyengeséget. Ez az integráció kockázati alapú megközelítést biztosít a biztonsági rések felderítése és rangsorolása terén, amely javíthatja a Szervizelési válaszidőt a környezetében.  

A veszélyforrások elleni [& biztonsági rések kezelése](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt) a [Microsoft Defender komplex veszélyforrások elleni védelem](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)részét képezi.  

## <a name="how-integration-works"></a>Az integráció működése  

Az Intune és a Microsoft Defender komplex veszélyforrások elleni védelemhez való csatlakoztatása után az ATP a felügyelt eszközökről fenyegetést és sebezhetőségi adatokat kap.  

A Microsoft Defender Security Center konzolon az ATP biztonsági rendszergazdák áttekintik a végponti biztonsági rések adatait. A rendszergazdák ezt követően egyetlen kattintással létrehozhatják azokat a biztonsági feladatokat, amelyek megjelölik a sebezhető eszközöket a szervizeléshez. A biztonsági feladatokat azonnal átadja az Intune-konzolnak, ahol az Intune-rendszergazdák megtekinthetik azokat. A biztonsági feladat azonosítja a sebezhetőség típusát, prioritását, állapotát, valamint a biztonsági rés megoldásához szükséges lépéseket. Az Intune-rendszergazda úgy dönt, hogy elfogadja vagy elutasítja a feladatot.  

Ha egy feladat el van fogadva, az Intune rendszergazdája ezt követően elhárítja a biztonsági rést, ha az Intune-t használja a biztonsági feladat részeként biztosított útmutatás alapján.  

A szervizeléssel kapcsolatos gyakori műveletek a következők:  

- Alkalmazás futtatásának **letiltása**  
- Operációs rendszer frissítésének **központi telepítése** a biztonsági rés enyhítése érdekében.  
- **Módosítsa** a beállításazonosító értékét.  
- **Tiltsa le** vagy **engedélyezze** a biztonsági rést befolyásoló konfigurációt.  
- **Ügyeljen** arra, hogy a rendszergazda a fenyegetés hiányában ne kapjon megfelelő javaslatot.  

Példa munkafolyamat:

- A Microsoft Defender ATP szolgáltatáson belül a contoso Media Player v4 nevű alkalmazás biztonsági rése észlelhető, és egy rendszergazda biztonsági feladatot hoz létre az alkalmazás frissítéséhez. A contoso Media Player egy nem felügyelt alkalmazás, amelyet az Intune-nal telepítettek.  

  Ez a biztonsági feladat az Intune-konzolon függőben lévő állapottal jelenik meg:  
  ![A biztonsági feladatok listájának megtekintése az Intune-konzolon](./media/atp-manage-vulnerabilities/temp-security-tasks.png)
 
- Az Intune-rendszergazda kiválasztja a biztonsági feladatot a feladat részleteinek megtekintéséhez.  A rendszergazda ezután kiválasztja az **elfogadás**lehetőséget, amely frissíti az állapotát az Intune-ban, és *elfogadja*az ATP-t.  
  ![Biztonsági feladat elfogadása vagy elutasítása](./media/atp-manage-vulnerabilities/temp-accept-task.png) 
 
- A rendszergazda ezután a megadott útmutatás alapján szervizeli a feladatot.  Az útmutató a szükséges szervizelés típusától függően változik. Ha elérhető, a Szervizelési útmutató olyan hivatkozásokat tartalmaz, amelyek a megfelelő ablaktáblákat nyitják meg a konfigurációkhoz az Intune-ban. 

  Mivel az ebben a példában szereplő Media Player nem felügyelt alkalmazás, az Intune csak szöveges utasításokat tud megadni. Ha az alkalmazást felügyelték, az Intune utasításokat adhat a frissített verzió letöltéséhez, és megadhat egy hivatkozást az alkalmazás központi telepítésének megnyitásához, hogy a frissített fájlok hozzá legyenek adva a központi telepítéshez. 

- A szervizelés befejezése után az Intune rendszergazdája megnyitja a biztonsági feladatot, és kiválasztja a **feladat befejezése**lehetőséget.  A Szervizelési állapot frissült az Intune-ban és az ATP-ben, ahol a biztonsági rendszergazdák megerősítik a biztonsági rés felülvizsgált állapotát.  

## <a name="prerequisites"></a>Előfeltételek  

Előfizetések:  

- Microsoft Intune  
- Microsoft Defender komplex veszélyforrások elleni védelem ([regisztráljon az ingyenes próbaverzióra](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink).)  

**Az ATP**-beli Intune-konfigurációk:  

- Szolgáltatás konfigurálása a Microsoft Defender ATP szolgáltatással való kapcsolódásra.  
- Helyezzen üzembe egy eszköz megfelelőségi szabályzatot a **Microsoft DEFENDER ATP (Windows 10 asztali verzió)** profiljával olyan eszközökre, amelyek az ATP által értékelt kockázattal rendelkeznek.

  További információ arról, hogyan állíthatja be az Intune-t az ATP szolgáltatással való együttműködéshez: a [Microsoft DEFENDER ATP megfelelőségének kikényszerítés feltételes hozzáféréssel az Intune-ban](advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune).  

## <a name="work-with-security-tasks"></a>Biztonsági feladatok használata  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és nyissa meg az **eszköz biztonsági** > feladatait.  
2. Válasszon ki egy feladatot a listából egy olyan erőforrás-ablak megnyitásához, amely megjeleníti a biztonsági feladat további részleteit.  
3. A biztonsági feladat erőforrás-ablakának megtekintése közben további hivatkozásokat is választhat:  
   - FELÜGYELt alkalmazások – megtekintheti a sebezhető alkalmazást. Ha a biztonsági rés több alkalmazásra is vonatkozik, az alkalmazások szűrt listája jelenik meg.  
   - ESZKÖZÖK – megtekintheti a *sebezhető eszközök*listáját, amelyről egy olyan bejegyzéshez kapcsolódhat, amely az adott eszköz biztonsági résének további részleteit tartalmazza.  
   - KÉRELMEZŐ – a hivatkozás használatával küldhet e-mailt a biztonsági feladatot elküldő rendszergazdának.  
   - Megjegyzések – a kérelmező által a biztonsági feladat megnyitásakor küldött egyéni üzenetek olvasása.  
4. Válassza az **elfogadás** vagy az **elutasítás** lehetőséget, ha értesítést szeretne küldeni az ATP számára a tervezett művelethez. Ha elfogadja vagy elutasítja a feladatot, elküldheti az ATP szolgáltatásnak küldött megjegyzéseket.  

5. A feladat elfogadása után nyissa meg újra a biztonsági feladatot (ha be van zárva), és a biztonsági rés javításához kövesse a szervizelés részleteit.  Az ATP által a biztonsági feladat részleteiben megadott utasítások az érintett sebezhetőségtől függően változhatnak.  

   Ha ez lehetséges, a Szervizelési utasítások olyan hivatkozásokat tartalmaznak, amelyek megnyitják a megfelelő konfigurációs objektumokat az Intune-konzolon.  

6. A Szervizelési lépések elvégzése után nyissa meg a biztonsági feladatot, és válassza a **feladat befejezése**lehetőséget.  Ez a művelet frissíti a biztonsági feladat állapotát az Intune-ban és az ATP-ben is.  

A szervizelés sikeres befejezését követően az ATP kockázati expozíciós pontszáma eldobásra kerül a szervizelt eszközökről származó új információk alapján. 

## <a name="next-steps"></a>További lépések
További információ az Intune-ról és a [Microsoft DEFENDER ATP](advanced-threat-protection.md) -ről  
Az Intune [Mobile Threat Defense](mobile-threat-defense.md) áttekintése  
Tekintse át a veszélyforrások elleni [& biztonsági rések kezelése irányítópultot](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights) a Microsoft Defender ATP-ben
