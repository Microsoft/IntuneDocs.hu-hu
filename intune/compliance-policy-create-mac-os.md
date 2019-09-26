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
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0e3164c84c9a4088068fcf920903c6bb76cd30a
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "71305069"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>macOS-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk a macOS-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal adhatja meg a minimális vagy maximális operációsrendszer-verziót, beállíthatja a jelszavakat, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- macOS

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításnál adja meg a **macOS** értéket.

## <a name="device-health"></a>Eszközállapot

- **Rendszerintegritás-védelem megkövetelése**: A macOS-eszközök [rendszerintegritás-védelemmel való ellátásának](https://support.apple.com/HT204899) **megkövetelése** (Apple webhely megnyitása) engedélyezve. Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

## <a name="device-properties"></a>Eszköztulajdonságok

- **Operációs rendszer minimális verziója**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ez után pedig hozzáférést kap a vállalati erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb verziót használ, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak ekkor az informatikai rendszergazdához kell fordulnia. Az eszköz csak akkor használható a vállalati erőforrások elérésére, ha a szabályt úgy módosítják, hogy engedélyezze az operációs rendszer verzióját.
- **Operációsrendszer-Build minimális verziója**: Amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ez a funkció használatával adja meg a minimális megengedett buildszám az eszközön.
- **Operációsrendszer-Build maximális verziója**: Amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ez a funkció használatával adja meg a maximális megengedett buildszám az eszközön.

## <a name="system-security-settings"></a>A rendszer biztonsági beállításai

### <a name="password"></a>Windows 10

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**: A **felhasználóknak jelszót kell** megadniuk ahhoz, hogy hozzáférjenek az eszközhöz.
- **Egyszerű jelszavak**: A **Letiltás** beállítás megadása esetén a felhasználók nem hozhatnak létre egyszerű jelszavakat, például **1234** vagy **1111**. A **Nincs konfigurálva** beállítással a felhasználók olyan jelszavakat is létrehozhatnak, mint az **1234** vagy az **1111**.
- **Jelszó minimális hossza**: Adja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát.
- **Jelszó típusa**: Válassza ki, hogy a jelszó csak **numerikus** karakterekből álljon-e, vagy számokból és más karakterből (**alfanumerikus**) kell állnia.
- **Nem alfanumerikus karakterek száma a jelszóban**: Adja `&`meg a speciális karakterek `#` `%`minimális számát (például:,,, stb.), amelynek a jelszóban kell lennie. `!`

    Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát.
- **Jelszó érvényessége (napokban)** : Válassza ki, hogy hány nap elteltével járjon le a jelszó, és egy újat kell létrehoznia.
- **Az újrafelhasználást megakadályozó korábbi jelszavak száma**: Adja meg a nem használható korábban használt jelszavak számát.

    > [!IMPORTANT]
    > Ha macOS-eszközön megváltozik a jelszóra vonatkozó követelmény, akkor az csak akkor lép érvénybe, amikor a felhasználó legközelebb megváltoztatja jelszavát. Ha például a jelszó kötelező minimális hosszát 8 számjegyűre állítja át, és a macOS-eszköz jelenlegi jelszava 6 számjegyű, az eszköz egészen addig megfelelőnek minősül, amíg a felhasználó legközelebb meg nem változtatja az eszköz jelszavát.

### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**: Válassza a **szükséges** lehetőséget az adattárolók titkosításához az eszközökön.

### <a name="device-security"></a>Eszközbiztonság

A tűzfal a jogosulatlan hálózati hozzáférés ellen védi az eszközöket. A tűzfal használatával a kapcsolatok alkalmazásonként szabályozhatók. 

- **Tűzfal**: Válassza az **Engedélyezés** lehetőséget az eszközök jogosulatlan hozzáférés elleni védelméhez. A funkció engedélyezése után kezelni tudja a bejövő internetes kapcsolatokat, és használhatja a rejtett üzemmódot. Ha **Nincs konfigurálva** (alapértelmezés), akkor a tűzfal kikapcsolva marad, a hálózati forgalom pedig engedélyezve lesz (nem lesz letiltva).
- **Bejövő kapcsolatok**: **Tiltsa** le az összes bejövő hálózati kapcsolatot, kivéve az alapszintű internetes szolgáltatásokhoz szükséges kapcsolatokat, például a DHCP, a Bonjour és az IPSec protokollt. Ez a beállítás blokkolja az összes megosztó szolgáltatást is, beleértve a képernyő-megosztást, a távelérést, az iTunes Music sharingt és egyebeket. Ha **Nincs konfigurálva** (alapértelmezés), akkor minden bejövő kapcsolat és megosztási szolgáltatás engedélyezve van.
- **Rejtett mód**: A rejtett üzemmód **engedélyezésével** megakadályozhatja, hogy az eszközök válaszolják meg a Szondázási kérelmeket, ami elvégezhető a rosszindulatú felhasználóktól. Engedélyezése esetén az eszköz továbbra is válaszol az engedélyezett alkalmazásoktól érkező kérelmekre. Ha **Nincs konfigurálva** (alapértelmezés), akkor a rejtett üzemmód ki van kapcsolva.

### <a name="gatekeeper"></a>Forgalomirányító

További információ: [a MacOS-es Porting](https://support.apple.com/HT202491) (az Apple webhelyének megnyitása).

**A következő helyekről letöltött alkalmazások engedélyezése**: Lehetővé teszi, hogy a támogatott alkalmazások különböző helyekről legyenek telepítve az eszközökön. Az Ön helybeállításai:

- **Nincs konfigurálva**: Default (Alapértelmezett): A forgalomirányító beállítás nincs hatással a megfelelőségre vagy a meg nem felelés esetén. 
- **Mac App Store**: Csak a Mac App Store-hoz készült alkalmazások telepítése. Nem lehet harmadik felektől és azonosított fejlesztőktől származó alkalmazásokat telepíteni. Ha egy felhasználó azt választja, hogy a forgalomirányító a Mac App Store-on kívüli alkalmazásokat telepítsen, akkor az eszköz nem megfelelőnek fog számítani.
- **Mac App Store és azonosított fejlesztők**: Alkalmazások telepítése a Mac App Store-hoz és az azonosított fejlesztőktől. A macOS ellenőrzi a fejlesztők identitását, és néhány egyéb ellenőrzést is végez az alkalmazás integritásának igazolásához. Ha egy felhasználó azt választja, hogy a forgalomirányító a megadott beállításokon kívüli alkalmazásokat telepítsen, akkor az eszköz nem megfelelőnek fog számítani.
- **Bárhol**: Az alkalmazások bárhonnan és bármely fejlesztőtől telepíthetők. Ez a beállítás a legkevésbé biztonságos.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az iOS-eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-ios.md) .