---
title: iOS-eszközök megfelelőségi beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg az iOS-eszközök megfelelőségének beállításakor használható összes beállítást Microsoft Intuneban. E-mail-cím, a feltört eszközök bejelölése, az engedélyezett minimális és maximális operációs rendszer beállítása, a jelszó korlátozásának beállítása, beleértve a jelszó hosszát és az eszköz inaktivitását, az alkalmazások korlátozását stb.
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
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f473e376278b454ca2d173c7c147137226a9fc9
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601512"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>iOS-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és leírja az iOS-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal megkövetelheti, hogy az e-mailek, a feltört (feltört) eszközök nem megfelelőek legyenek, beállíthatja az engedélyezett veszélyforrásokat, beállíthatja a jelszavakat, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- iOS

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításnál adja meg az **iOS** értéket.

## <a name="email"></a>E-mail

- **Felügyelt e-mail-profil megkövetelése a mobileszközök számára**: Ha a beállítás **kötelező**, az Intune által felügyelt e-mail-profillal nem rendelkező eszközök nem minősülnek megfelelőnek. Egy eszköz nem rendelkezhet felügyelt e-mail-profillal, ha nem megfelelően van megcélozva, vagy ha a felhasználó manuálisan állítja be az e-mail-fiókot az eszközön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Az eszköz nem megfelelőnek minősül a következő helyzetekben:

  - Az e-mail-profil egy másik felhasználói csoporthoz van rendelve, mint a megfelelőségi szabályzat által megcélozott felhasználói csoport.
  - A felhasználó már beállított egy olyan e-mail fiókot az eszközön, amely megfelel az eszközre telepített Intune e-mail profilnak. Az Intune nem írhatja felül a felhasználó által konfigurált profilt, és az Intune nem tudja kezelni azt. A megfelelőség érdekében a felhasználónak el kell távolítania a meglévő e-mail-beállításokat. Ezt követően az Intune képes lesz a felügyelt e-mail-profil telepítésére.

- **Válassza ki azt az e-mail-profilt, amelyet az Intune-nak kell kezelnie**: Ha be van jelölve az **e-mail-fiók** felügyelete az Intune-ban beállítás, válassza a **kiválasztás** lehetőséget az Intune e-mail profil megadásához. Az e-mail-profilnak léteznie kell az eszközön.

A levelezési profilokkal kapcsolatos további információkért lásd: a [vállalati levelezéshez való hozzáférés konfigurálása e-mail-profilok használatával az Intune-](../configuration/email-settings-configure.md)nal.

## <a name="device-health"></a>Device health

- Feltört **eszközök**: a **Letiltás** elem kiválasztásával megadhatja a feltört (jailbroken) eszközöket, nem megfelelőként. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Az eszköznek a veszélyforrások szintjén** (iOS 8,0 és újabb) való használatának megkövetelése: ezzel a beállítással a kockázatértékelés feltétele a megfelelőség. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához. A beállítás használatához válassza ki a megengedett kockázati szintet:
  - **Védett**: Ez a legbiztonságosabb beállítás. Annyit jelent, hogy az eszköz esetében semmilyen fenyegetés nem engedélyezett. Ha az eszköz bármilyen szintű fenyegetést észlel, azt a rendszer nem megfelelőként értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszköz vonatkozásában fennálló fenyegetések alacsony vagy közepes szintűek. Ha az eszköz magas szintű fenyegetéseket észlel, azt a rendszer nem megfelelőként határozza meg.
  - **Magas**: Ez a legkevésbé biztonságos, minden fenyegetettségi szintet megengedő beállítás. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

## <a name="device-properties"></a>Eszköztulajdonságok

- Az **operációs rendszer szükséges minimális** verziója (iOS 8,0 és újabb): Ha egy eszköz nem teljesíti az operációs rendszer minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. Ezután hozzáférhetnek a szervezeti erőforrásokhoz.
- **Maximálisan engedélyezett operációsrendszer-verzió** (iOS 8,0 és újabb): Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer szerepel, a szervezeti erőforrásokhoz való hozzáférés le lesz tiltva. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg egy szabály nem változik, hogy az operációs rendszer verziója engedélyezve legyen.
- Az **operációsrendszer-Build minimális verziója** (iOS 8,0 és újabb): amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ezzel a szolgáltatással megadhatja az eszközön a minimálisan megengedett Build-számot.
- **Maximális operációsrendszer-összeállítás verziója** (iOS 8,0 és újabb): amikor az Apple közzéteszi a biztonsági frissítéseket, a rendszer általában frissíti a Build számát, nem pedig az operációs rendszer verzióját. Ezzel a szolgáltatással adhatja meg az eszközön a maximálisan megengedett Build-számot.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Jelszó

> [!NOTE]
> Miután megfelelőségi vagy konfigurációs szabályzatot alkalmazott egy iOS-eszközre, a felhasználóktól 15 percenként egy PIN-kódot kér a rendszer. A kérések mindaddig megjelennek, amíg a felhasználó meg nem ad egy PIN-kódot. Ha az iOS-eszközhöz PIN-kód van beállítva, a titkosítási folyamat automatikusan elindul. Az eszköz mindaddig titkosítva marad, amíg le nem tiltja a PIN-kódot.

- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához**: A felhasználók **kötelesek** jelszót megadni az eszköz eléréséhez. A jelszót használó iOS-eszközöket titkosítja a rendszer.
- **Egyszerű jelszavak**: Ha nem szeretné engedélyezni, hogy a felhasználók olyan egyszerű jelszavakat használhassanak, mint az **1234** vagy az **1111**, válassza a **Tiltás** lehetőséget. A **Nincs konfigurálva** beállítással a felhasználók olyan jelszavakat is létrehozhatnak, mint az **1234** vagy az **1111**.
- **Jelszó minimális hossza**: Meghatározhatja a jelszóban szereplő számjegyek vagy karakterek minimális számát.
- **Jelszó megkövetelt típusa**: Megadható, hogy a jelszó csak **számjegy** karaktereket vagy számjegy és más (**alfanumerikus**) karaktereket vegyesen tartalmazzon.
- **Nem alfanumerikus karakterek száma a jelszóban**: megadhatja a speciális karakterek minimális számát (például `&`, `#`, `%`, `!` stb.), amelyeknek a jelszóban kell szerepelniük.

    Ha nagyobb értékre állítja, a felhasználóknak összetettebb jelszót kell létrehozniuk.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát.
- **Jelszó érvényessége (napokban)** : Válassza ki, hány nap elteltével járjon le a jelszó, ami után újat kell létrehoznia.
- Az **újrafelhasználást megakadályozó korábbi jelszavak száma**: megadhatja, hogy hány korábban használt jelszót ne lehessen használni.

### <a name="device-security"></a>Eszköz biztonsága

- **Korlátozott alkalmazások**: Az alkalmazásokat úgy korlátozhatja, hogy a kötegazonosítójukat hozzáadja a szabályzathoz. Ha egy eszközön telepítve van az alkalmazás, az eszköz nem megfelelőként van megjelölve.

  - **Alkalmazásnév**: Adjon meg egy felhasználóbarát nevet, mely alapján a kötegazonosító könnyebben azonosítható.
  - **Alkalmazás kötegazonosítója**: Adja meg az alkalmazás szolgáltatója által hozzárendelt egyedi kötegazonosítót. A csomag AZONOSÍTÓjának megkereséséhez lásd: [az iOS-alkalmazáshoz tartozó csomag azonosítójának megkeresése](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (egy másik Microsoft-webhely megnyitása).  

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Lásd: [MacOS-eszközök megfelelőségi szabályzatának beállításai](compliance-policy-create-mac-os.md) .
