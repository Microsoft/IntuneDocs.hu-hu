---
title: Endpoint Protection-beállítások konfigurálása a Microsoft Intune-ban – Azure | Microsoft Docs
description: macOS- vagy Windows 10-eszközprofil az Intune-ban való létrehozásakor létrehozhat Endpoint Protection-beállításokat is.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: f8923f3c4e1610be2501dccbd3ac551b9c994c24
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729307"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Endpoint Protection-beállítások hozzáadása az Intune-ban  

Az Intune-nal az eszköz konfigurációs profiljaival kezelheti az Endpoint Protection általános biztonsági funkcióit az eszközökön, beleértve a következőket:  
- Tűzfal   
- BitLocker  
- Alkalmazások engedélyezése és letiltása  
- Windows Defender és titkosítás  

Létrehozhat például egy olyan Endpoint Protection-profilt, amely csak a Maces App Store áruházból származó alkalmazásokat engedélyezi telepíteni a macOS felhasználók számára. Vagy engedélyezheti a Windows SmartScreent a Windows 10-eszközök alkalmazásain.  

A profil létrehozása előtt tekintse át a következő cikkeket, amelyek részletesen ismertetik az Intune által a támogatott platformokon felügyelhető Endpoint Protection-beállításokat:  
   - [macOS-beállítások](endpoint-protection-macos.md)  
   - [Windows 10-beállítások](endpoint-protection-windows-10.md)  

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Endpoint Protection-beállításokat tartalmazó eszközprofil létrehozása  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.  
3. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.  
4. Adja meg az Endpoint Protection-profil **nevét** és **leírását**.  
5. A **Platform** legördülő listából válassza ki azt az eszközplatformot, amelyre egyéni beállításokat szeretne alkalmazni. Jelenleg az alábbi platformokra vonatkozóan lehet eszközkorlátozási beállításokat megadni:  
   - **macOS**  
   - **Windows 10 és újabb**  
6. A **Profil típusa** legördülő listából válassza az **Endpoint Protection** lehetőséget.  
7. A kiválasztott platformtól függően a konfigurálható beállítások eltérőek. Lásd:  
   - [macOS-beállítások](endpoint-protection-macos.md)  
   - [Windows 10-beállítások](endpoint-protection-windows-10.md)  

8. A megfelelő beállítások konfigurálása után válassza a **Létrehozás** elemet a **profil létrehozása** lapon.  

   Ekkor létrejön a profil, és megjelenik a profilok listáját tartalmazó lapon. Ha csoportokhoz szeretné hozzárendelni a profilt, tekintse meg az [eszközprofilok hozzárendelését](../configuration/device-profile-assign.md) ismertető cikket.  

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Egyéni tűzfalszabályok hozzáadása Windows 10-es eszközökhöz  

Ha a Windows Defender-tűzfalat olyan profil részeként konfigurálja, amely a Windows 10 Endpoint Protection-szabályait tartalmazza, a tűzfalakra vonatkozó egyéni szabályokat is konfigurálhat. Az egyéni szabályok lehetővé teszik a Windows 10 által támogatott tűzfalszabályok előre definiált készletének kibontását.  

Ha egyéni tűzfalszabályok alapján tervez profilt, vegye figyelembe a következő információkat, amelyek befolyásolhatják a tűzfalszabályok csoportosítási módját a profilokban:  
- Az egyes profilok legfeljebb 150 tűzfalszabályok használatát támogatják. Ha több mint 150 szabályt használ, hozzon létre további profilokat, amelyek mindegyike 150 szabályra korlátozódik.  
- Minden profil esetében, ha egyetlen szabályt nem sikerül alkalmazni, a profilban szereplő összes szabály sikertelen lesz, és a rendszer egyetlen szabályt sem alkalmaz az eszközre.  
- Ha egy szabályt nem sikerül alkalmazni, a profilban szereplő összes szabályt nem sikerült jelenteni. Az Intune nem tudja azonosítani, hogy melyik egyedi szabály nem sikerült.  

Az Intune által kezelhető tűzfalszabályok részletesen szerepelnek a Windows [tűzfal konfigurációs]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) szolgáltatójában (CSP). Az Intune által támogatott Windows 10-es eszközök egyéni tűzfalbeállítások listájának áttekintéséhez tekintse meg az [Egyéni tűzfalszabályok](endpoint-protection-windows-10.md#firewall-rules)című témakört.  

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Egyéni tűzfalszabályok hozzáadása Endpoint Protection-profilhoz  

1. Az Intune-ban válassza az **eszköz konfigurációs** > **profilok** > **Létrehozás profil létrehozása**lehetőséget.  

2. A *platform*területen válassza a **Windows 10 és újabb**lehetőséget, majd a *Profil típusa* beállításnál válassza az **Endpoint Protection**lehetőséget.  

3. Válassza a **Windows Defender-tűzfal** lehetőséget a konfiguráció lap megnyitásához, majd a *Tűzfalszabályok* kiválasztásához kattintson a **Hozzáadás** elemre a **szabály létrehozása** lap megnyitásához.  

4. Adja meg a tűzfalszabály beállításait, majd kattintson **az OK gombra** a mentéshez. A dokumentációban elérhető egyéni tűzfalszabályok beállításainak áttekintését lásd: [Egyéni tűzfalszabályok](endpoint-protection-windows-10.md#firewall-rules).  

5. A szabály mentése után az megjelenik a *Windows Defender-tűzfal* lapon a szabályok listájában.  

6. Egy szabály módosításához válassza ki a szabályt a listából, és nyissa meg a **szabály szerkesztése** lapot.  

7. Ha törölni szeretne egy szabályt egy profilból, válassza a szabályhoz tartozó három pontot **(...)** , majd válassza a **Törlés**lehetőséget.  

8. Ha módosítani szeretné a szabályok megjelenítési sorrendjét, kattintson a *felfelé mutató nyíl* ikonra a szabálygyűjtemény tetején.  


## <a name="next-steps"></a>További lépések  

Ha csoportokhoz szeretne hozzárendelni egy profilt, tekintse meg az [eszközprofilok hozzárendelését](../configuration/device-profile-assign.md) ismertető cikket.  
