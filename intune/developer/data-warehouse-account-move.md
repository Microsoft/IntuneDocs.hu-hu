---
title: Az Intune-adattárház fiókadatainak áthelyezése
titleSuffix: Microsoft Intune
description: Útmutató az Intune-adattárházbeli adatok biztonsági mentéséhez a fiók áthelyezése esetén.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb86b066755c85208e9d9c2b5b823305f6011df9
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730275"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Az Intune-adattárház fiókadatainak áthelyezése 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A fiókáthelyezési kérelem egyben azt is kérelmezi, hogy az adatközpont más helyre kerüljön át. Az áthelyezés után az adattárház alaphelyzetbe áll és az áthelyezés megadott kezdőnapjának alapján megkezdi az adatok rögzítését az új helyen. A fiók áthelyezése **előtt** készítsen biztonsági másolatot az előző adattárház adatairól a következő lépések végrehajtásával. Az adattárház táblái 30 napig őrzik meg az adatokat, így ezeknek a tábláknak a tartalma a fiók áthelyezése után 30 nappal már nem lesz elérhető. Az egyes táblák adatmegőrzési időtartamairól [Az adattárház adatmodellje](reports-ref-data-model.md) című cikk nyújt bővebb információt. 

## <a name="back-up-your-data-warehouse-data"></a>Az adattárház adatinak biztonsági mentése 

Az adattárház adatainak biztonsági mentéséhez egy *.csv*-fájlba kell menteni azokat az adattárház API használatával:  

1. Ha először használja az adattárház API-t, akkor hajtsa végre az [Adatok beolvasása az Intune-adattárház API-ból REST-ügyféllel](reports-proc-data-rest.md) című cikkben ismertetett, egyszeri eljárást.
2. Az [Intune-adattárház elérése a PowerShellel](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell) című PowerShell-minta használatával minden adat CSV-fájlokba tölthető le. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Trenddiagramok biztonsági mentése az Azure Portalon

Az Azure Portal saját nézetében egyes trenddiagramok alaphelyzetbe állnak. Ezekről a diagramokról a **Graph**-ban készíthető biztonsági másolat a következő szkript futtatásával:   

### <a name="terms--conditions-acceptance-reports"></a>Jelentések a használati feltételek elfogadásáról
1. Az Azure Portalon lépjen a **Microsoft Intune** -> **Eszközregisztráció** -> **Használati feltételek** szakaszba.
2. A **Használati feltételek** minden eleméhez válassza az **Elfogadási jelentés** majd az **Exportálás** lehetőséget.
3. Mentse helyben a jelentést.
 
### <a name="app-protection-reports"></a>Alkalmazásvédelmi jelentések  
1. Az Azure Portalon nyissa meg a **Microsoft Intune** -> **Ügyfélalkalmazások** -> **Alkalmazásvédelem állapota** lehetőséget.
2. Az egyes jelentések mentéséhez kattintson a letöltés ( ⤓ ) ikonra.

### <a name="device-configuration-charts"></a>Eszközkonfigurációs diagramok 
1. Az Azure Portalon nyissa meg a **Microsoft Intune** -> **Eszközkonfiguráció** lehetőséget.
2. A diagramok háttéradatai letölthetők a Microsoft [Diagramkezelő](https://developer.microsoft.com/graph/graph-explorer) használatával. 
    - Az [Eszköztelepítés állapota](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content) használatával az összes eszköz valamennyi eszközkonfigurációs profiljának telepítési állapota megtekinthető.

    - A [Felhasználói telepítés állapota](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content) használatával az összes felhasználó valamennyi eszközkonfigurációs profiljának telepítési állapota megtekinthető.

    - A profilok telepítési állapota a [Telepítési állapot megadása](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview) használatával tekinthető meg.
  
    > [!NOTE]
    > Az eszközkonfigurációs és telepítési állapot információi csak érvényes hitelesítő jogkivonat birtokában érhetők el.

## <a name="device-enrollment-charts"></a>Eszközregisztrációs diagramok
1. Az Azure Portalon nyissa meg a **Microsoft Intune** -> **Eszközregisztráció** lehetőséget.
2. A diagramok háttéradatai letölthetők a Microsoft [Diagramkezelő](https://developer.microsoft.com/graph/graph-explorer) használatával.
    - A regisztráció állapota ezt a [regisztrációsállapot-lekérdezést](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content) lemásolva és a [Diagramkezelőbe](https://developer.microsoft.com/graph/graph-explorer) beillesztve kapható meg.
    - A héten meghiúsult regisztrációk toplistája ezt a [regisztrációshiba-lekérdezést](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content) lemásolva és a [Diagramkezelőbe](https://developer.microsoft.com/graph/graph-explorer) beillesztve kapható meg.

    > [!NOTE]
    > Az eszközregisztrációs adatok csak érvényes hitelesítő jogkivonat birtokában érhetők el. 

## <a name="after-a-data-warehouse-account-move"></a>Adattárházfiók áthelyezése után

Az adattárházfiók áthelyezése után az Intune-ban az látható, hogy az adattárház alaphelyzetbe állt és az adatok már az új helyen vannak tárolva. A diagramok és exportálási lehetőségek alaphelyzetbe állnak és megjelenik egy értesítés. Erre kattintva megnyílik egy cikk, amely elmagyarázza a diagramok alaphelyzetbe állásának okát.  

## <a name="data-warehouse-move-example"></a>Példa adattárház áthelyezésére 

X ügyfél 2018. június 1-jén kezdődő fiókáthelyezést kérelmez. A kérelemre válaszul az ügyfél egy hivatkozást kap, amelyen megtekintheti a korábbi adattárház biztonsági másolatának elkészítését lépésenként leíró dokumentációt. 2018. június 1-jén az adattárház és a rá épülő diagramok alaphelyzetbe állnak, és az adatok ettől kezdve az új adatközpontban lesznek tárolva. 

## <a name="next-steps"></a>További lépések

- Heti összesítésben [olvashat az Intune újdonságairól](../fundamentals/whats-new.md). Emellett tájékozódhat a jövőbeni változtatásokról, a szolgáltatással kapcsolatos fontos bejelentésekről és a korábbi verziókról is.
- Tekintse meg [a Microsoft Intune blogját](https://go.microsoft.com/fwlink/?LinkID=273882).
