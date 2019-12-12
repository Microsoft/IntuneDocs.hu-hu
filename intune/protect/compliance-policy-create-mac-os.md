---
title: macOS-eszközök megfelelőségi beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg a macOS-eszközök megfelelőségének beállításakor használható beállítások listáját Microsoft Intuneban. Az Apple rendszerintegritás-védelem megkövetelése, jelszó-korlátozás beállítása, tűzfal megkövetelése, forgalomirányító engedélyezése és még sok más.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813500"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>macOS-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

Ez a cikk a macOS-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal adhatja meg a minimális vagy maximális operációsrendszer-verziót, beállíthatja a jelszavakat, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- macOS

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításnál adja meg a **macOS** értéket.

## <a name="device-health"></a>Eszközállapot

- **Rendszerintegritás-védelem megkövetelése**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Szükséges** – a MacOS rendszerű eszközökön engedélyezni kell a [rendszerintegritás-védelmet](https://support.apple.com/HT204899) (az Apple webhelyének megnyitása).  

## <a name="device-properties"></a>Eszköztulajdonságok

- Az **operációs rendszer minimuma szükséges**:  
  Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. Az eszköz a felhasználó dönthet úgy, hogy frissíti az eszközt. Ezután hozzáférhetnek a szervezeti erőforrásokhoz.

- **Maximálisan engedélyezett operációsrendszer-verzió**:  
  Ha egy eszköz a szabályban megadott operációsrendszer-verziónál újabb verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. Az eszköz felhasználójának kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg egy szabály nem változik, hogy az operációs rendszer verziója engedélyezve legyen.

- **Operációsrendszer-Build minimális verziója**:  
  Amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ezzel a szolgáltatással megadhatja az eszközön a minimálisan megengedett Build-számot.

- **Operációsrendszer-Build maximális verziója**:  
  Amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ezzel a szolgáltatással adhatja meg az eszközön a maximálisan megengedett Build-számot.

## <a name="system-security-settings"></a>A rendszer biztonsági beállításai

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**:  
  - **Nincs konfigurálva** (*alapértelmezett*)
  - **Szükséges** A felhasználóknak jelszót kell megadniuk ahhoz, hogy hozzáférjenek az eszközhöz.

- **Egyszerű jelszavak**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a felhasználók olyan egyszerű jelszavakat hozhatnak létre, mint például a **1234** vagy a **1111**.
  - **Letiltás** – a felhasználók nem hozhatnak létre egyszerű jelszavakat, például **1234** vagy **1111**.

- **Jelszó minimális hossza**:  
  Adja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát.

- **Jelszó típusa**: Megadható, hogy a jelszó csak **számjegy** karaktereket vagy számjegy és más (**Alfanumerikus**) karaktereket vegyesen tartalmazzon.

- **Nem alfanumerikus karakterek száma a jelszóban**:  
  Adja meg a speciális karakterek minimális számát (például `&`, `#`, `%`, `!`stb.), amelynek a jelszónak kell lennie.

  Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**:  
  Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát.

- **Jelszó érvényessége (napokban)** :  
  Válassza ki, hogy hány nap elteltével járjon le a jelszó, és egy újat kell létrehoznia.

- **Az újrafelhasználást megakadályozó korábbi jelszavak száma**:  
  Adja meg a nem használható korábban használt jelszavak számát.
> [!IMPORTANT]
> Ha macOS-eszközön megváltozik a jelszóra vonatkozó követelmény, akkor az csak akkor lép érvénybe, amikor a felhasználó legközelebb megváltoztatja jelszavát. Ha például a jelszó kötelező minimális hosszát 8 számjegyűre állítja át, és a macOS-eszköz jelenlegi jelszava 6 számjegyű, az eszköz egészen addig megfelelőnek minősül, amíg a felhasználó legközelebb meg nem változtatja az eszköz jelszavát.

### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**:  
  - **Nincs konfigurálva** (*alapértelmezett*)
  - **Kötelező** – az adattárolást az eszközökön *titkosítani kell.*

### <a name="device-security"></a>Eszközbiztonság

A tűzfal a jogosulatlan hálózati hozzáférés ellen védi az eszközöket. A tűzfal használatával a kapcsolatok alkalmazásonként szabályozhatók. 

- **Tűzfal**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – Ez a beállítás elhagyja a tűzfalat, és a hálózati forgalom engedélyezett (nincs letiltva).
  - **Engedélyezés** – a használata *lehetővé teszi* az eszközök jogosulatlan hozzáférés elleni védelmének elősegítését. A funkció engedélyezése után kezelni tudja a bejövő internetes kapcsolatokat, és használhatja a rejtett üzemmódot. 

- **Bejövő kapcsolatok**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – engedélyezi a bejövő kapcsolatokat és a megosztási szolgáltatásokat.
  - **Tiltsa** le az összes bejövő hálózati kapcsolatot, kivéve az alapszintű internetes szolgáltatásokhoz szükséges kapcsolatokat, például a DHCP-t, a Bonjour-t és az IPSec-t. Ez a beállítás blokkolja az összes megosztó szolgáltatást is, beleértve a képernyő-megosztást, a távelérést, az iTunes Music sharingt és egyebeket.  

- **Rejtett mód**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – ezzel a beállítással a rejtett mód ki van kapcsolva.
  - **Engedélyezze** a rejtett üzemmód bekapcsolását, hogy megakadályozza, hogy az eszközök válaszolják a Szondázási kérelmeket, ami elvégezhető a rosszindulatú felhasználóktól. Engedélyezése esetén az eszköz továbbra is válaszol az engedélyezett alkalmazásoktól érkező kérelmekre.  

### <a name="gatekeeper"></a>Forgalomirányító

További információ: [a MacOS-es Porting](https://support.apple.com/HT202491) (az Apple webhelyének megnyitása).

**Alkalmazások ezen helyekről való letöltésének engedélyezése**: Engedélyezi a különböző helyekről származó támogatott alkalmazások telepítését az eszközre. Az Ön helybeállításai:

- **Nincs konfigurálva** (*alapértelmezett*) – a forgalomirányító beállítás nincs hatással a megfelelőségre vagy a nem megfelelőségre.  
- **Mac App Store** – csak a Mac App Store áruházbeli alkalmazások telepítése. Nem lehet harmadik felektől és azonosított fejlesztőktől származó alkalmazásokat telepíteni. Ha egy felhasználó azt választja, hogy a forgalomirányító a Mac App Store-on kívüli alkalmazásokat telepítsen, akkor az eszköz nem megfelelőnek fog számítani.
- **Mac App Store és azonosított fejlesztők** – alkalmazások telepítése a Mac App Store-hoz és az azonosított fejlesztőktől. A macOS ellenőrzi a fejlesztők identitását, és néhány egyéb ellenőrzést is végez az alkalmazás integritásának igazolásához. Ha egy felhasználó azt választja, hogy a forgalomirányító a megadott beállításokon kívüli alkalmazásokat telepítsen, akkor az eszköz nem megfelelőnek fog számítani.
- **Bárhol** – az alkalmazások bárhonnan és bármely fejlesztőtől telepíthetők. Ez a beállítás a legkevésbé biztonságos.
 

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az iOS-eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-ios.md) .