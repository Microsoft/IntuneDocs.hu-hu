---
title: macOS-eszközök megfelelőségi beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg a macOS-eszközök megfelelőségének beállításakor használható beállítások listáját Microsoft Intuneban. Az Apple rendszerintegritás-védelem megkövetelése, jelszó-korlátozás beállítása, tűzfal megkövetelése, forgalomirányító engedélyezése és még sok más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cada774003f73f487f87ed8051115dfcaaae6a20
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502489"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>macOS-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk a macOS-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal adhatja meg a minimális vagy maximális operációsrendszer-verziót, beállíthatja a jelszavakat, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- macOS

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításnál adja meg a **macOS** értéket.

## <a name="device-health"></a>Eszközállapot

- **Rendszerintegritás-védelem megkövetelése** **: a** MacOS-eszközökön engedélyezve kell lennie a [rendszerintegritás-védelemnek](https://support.apple.com/HT204899) (az Apple webhely megnyitásakor). Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

## <a name="device-properties"></a>Eszköztulajdonságok

- **Minimális operációsrendszer-verzió**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként fog szerepelni. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ez után pedig hozzáférést kap a vállalati erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb fut, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz nem fér hozzá a céges erőforrásokhoz, amíg nincs olyan szabály, amely engedélyezi az operációs rendszer verzióját.
- **Operációsrendszer-Build minimális verziója**: Ha az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ezzel a szolgáltatással megadhatja az eszközön a minimálisan megengedett Build-számot.
- **Maximális operációsrendszer-build verziója**: Ha az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti az összeállítási számot, nem pedig az operációs rendszer verzióját. Ezzel a szolgáltatással adhatja meg az eszközön a maximálisan megengedett Build-számot.

## <a name="system-security-settings"></a>A rendszer biztonsági beállításai

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához**: A felhasználók **kötelesek** jelszót megadni az eszköz eléréséhez.
- **Egyszerű jelszavak**: Ha nem szeretné engedélyezni, hogy a felhasználók olyan egyszerű jelszavakat használhassanak, mint az **1234** vagy az **1111**, válassza a **Tiltás** lehetőséget. A **Nincs konfigurálva** beállítással a felhasználók olyan jelszavakat is létrehozhatnak, mint az **1234** vagy az **1111**.
- **Jelszó minimális hossza**: Meghatározhatja a jelszóban szereplő számjegyek vagy karakterek minimális számát.
- **Jelszó típusa**: Megadható, hogy a jelszó csak **számjegy** karaktereket vagy számjegy és más (**Alfanumerikus**) karaktereket vegyesen tartalmazzon.
- **Nem alfanumerikus karakterek száma a jelszóban**: Itt adhatja meg a speciális karakterek minimális számát (például `&`, `#`, `%`, `!` stb.), amelynek a jelszónak kell lennie.

    Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát.
- **Jelszó érvényessége (napokban)** : Válassza ki, hány nap elteltével járjon le a jelszó, ami után újat kell létrehoznia.
- Az **újrafelhasználást megakadályozó korábbi jelszavak száma**: megadhatja, hogy hány korábban használt jelszót ne lehessen használni.

    > [!IMPORTANT]
    > Ha macOS-eszközön megváltozik a jelszóra vonatkozó követelmény, akkor az csak akkor lép érvénybe, amikor a felhasználó legközelebb megváltoztatja jelszavát. Ha például a jelszó kötelező minimális hosszát 8 számjegyűre állítja át, és a macOS-eszköz jelenlegi jelszava 6 számjegyű, az eszköz egészen addig megfelelőnek minősül, amíg a felhasználó legközelebb meg nem változtatja az eszköz jelszavát.

### <a name="encryption"></a>Encryption

- **Adattároló titkosítása az eszközön**: A **Kötelező** lehetőséget választva az adattárolók titkosítva lesznek az eszközökön.

### <a name="device-security"></a>Eszközbiztonság

A tűzfal a jogosulatlan hálózati hozzáférés ellen védi az eszközöket. A tűzfal használatával a kapcsolatok alkalmazásonként szabályozhatók. 

- **Tűzfal**: válassza az **Engedélyezés** lehetőséget az eszközök jogosulatlan hozzáférés elleni védelméhez. A funkció engedélyezése után kezelni tudja a bejövő internetes kapcsolatokat, és használhatja a rejtett üzemmódot. Ha **Nincs konfigurálva** (alapértelmezés), akkor a tűzfal kikapcsolva marad, a hálózati forgalom pedig engedélyezve lesz (nem lesz letiltva).
- **Bejövő kapcsolatok**: **blokkolja** az összes bejövő hálózati kapcsolatot, kivéve az alapszintű internetes szolgáltatásokhoz szükséges kapcsolatokat, például a DHCP-t, a Bonjour-t és az IPSec-t. Ez a beállítás blokkolja az összes megosztó szolgáltatást is, beleértve a képernyő-megosztást, a távelérést, az iTunes Music sharingt és egyebeket. Ha **Nincs konfigurálva** (alapértelmezés), akkor minden bejövő kapcsolat és megosztási szolgáltatás engedélyezve van.
- **Rejtett mód**: a rejtett üzemmód **engedélyezése** megakadályozza, hogy az eszközök válaszolják a Szondázási kérelmeket, ami elvégezhető a rosszindulatú felhasználóktól. Engedélyezése esetén az eszköz továbbra is válaszol az engedélyezett alkalmazásoktól érkező kérelmekre. Ha **Nincs konfigurálva** (alapértelmezés), akkor a rejtett üzemmód ki van kapcsolva.

### <a name="gatekeeper"></a>Forgalomirányító

További információ: [a MacOS-es Porting](https://support.apple.com/HT202491) (az Apple webhelyének megnyitása).

**Alkalmazások ezen helyekről való letöltésének engedélyezése**: Engedélyezi a különböző helyekről származó támogatott alkalmazások telepítését az eszközre. Az Ön helybeállításai:

- **Nincs konfigurálva**: alapértelmezett. A forgalomirányító beállítás nincs hatással a megfelelőségre vagy a meg nem felelés esetén. 
- **Mac App Store**: Alkalmazások telepítése csak a Mac App Store-ból. Nem lehet harmadik felektől és azonosított fejlesztőktől származó alkalmazásokat telepíteni. Ha egy felhasználó azt választja, hogy a forgalomirányító a Mac App Store-on kívüli alkalmazásokat telepítsen, akkor az eszköz nem megfelelőnek fog számítani.
- **Mac App Store- és azonosított fejlesztők**: A Mac App Store és az azonosított fejlesztők alkalmazásainak telepítése. A macOS ellenőrzi a fejlesztők identitását, és néhány egyéb ellenőrzést is végez az alkalmazás integritásának igazolásához. Ha egy felhasználó azt választja, hogy a forgalomirányító a megadott beállításokon kívüli alkalmazásokat telepítsen, akkor az eszköz nem megfelelőnek fog számítani.
- **Bárhol**: Bárhonnan és bármely fejlesztő által telepíthetőek alkalmazások. Ez a beállítás a legkevésbé biztonságos.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az iOS-eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-ios.md) .