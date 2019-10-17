---
title: Az androidos nagyvállalati megfelelőségi beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg az androidos vállalati eszközök megfelelőségének beállításakor használható összes beállítást a Microsoft Intuneban. Állítsa be a jelszavakat, válassza ki a minimális vagy maximális operációsrendszer-verziót, korlátozza az egyes alkalmazásokat, megakadályozza a jelszó újrafelhasználását, és így tovább.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2704fdcd8072b8049452b0337a22f04b533d0650
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504665"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Androidos vállalati beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és leírja az Android Enterprise-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat a feltört (feltört) eszközök nem megfelelőként való megjelölésére, az engedélyezett veszélyforrási szint beállítására, a Google Play Protect engedélyezésére és egyebekre használhatja.

Ez a funkció az alábbiakra vonatkozik:

- Vállalati Android

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

> [!IMPORTANT]
> A megfelelőségi szabályzatok androidos vállalati dedikált eszközöket is alkalmaznak. Ha a megfelelőségi szabályzatot egy dedikált eszközhöz rendeli hozzá, az eszköz **nem megfelelőként**jelenhet meg. A feltételes hozzáférés és a megfelelőség érvényesítése nem érhető el dedikált eszközökön. Ügyeljen arra, hogy minden feladatot vagy műveletet végrehajtson, hogy a dedikált eszközök megfeleljenek a hozzárendelt szabályzatoknak.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **platform**területen válassza az **Android Enterprise**lehetőséget.

## <a name="device-owner"></a>Az eszköz tulajdonosa

### <a name="device-health"></a>Eszközállapot

- Az eszköznek **az eszköz veszélyforrási szintjére vagy az alá való helyezésének megkövetelése**: válassza ki a [Mobile Threat Defense szolgáltatás](mobile-threat-defense.md)által kiértékelt maximálisan engedélyezett veszélyforrások szintjét. Azok az eszközök, amelyek túllépik ezt a veszélyforrást, nem megfelelőként vannak megjelölve. A beállítás használatához válassza ki a megengedett kockázati szintet:

  - **Nincs konfigurálva** (alapértelmezett): Ez a beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Védett**: Ez a legbiztonságosabb beállítás. Annyit jelent, hogy az eszköz esetében semmilyen fenyegetés nem engedélyezett. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszköz vonatkozásában fennálló fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas**: Ez a legkevésbé biztonságos, minden fenyegetettségi szintet megengedő beállítás. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.
  
> [!NOTE] 
> A következő Mobile Threat Defense-(MTD-) szolgáltatók az alkalmazások konfigurációjának használatával támogatják az androidos vállalati eszközök tulajdonosának telepítését:
> - Jobb mobil 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Érdeklődjön az MTD-szolgáltatónál az androidos vállalati eszközök tulajdonosi platformjának az Intune-ban való támogatásához szükséges pontos konfigurációhoz. Ez a lista frissült, mivel az androidos vállalati eszközök tulajdonosi forgatókönyvei támogatják a MTD. 

#### <a name="google-play-protect"></a>Google Play Protect

- **SafetyNet eszközigazolás**: Megadható a [SafetyNet igazolás](https://developer.android.com/training/safetynet/attestation.html) elvárt szintje. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A rendszer nem értékeli a beállítást a megfelelőség vagy meg nem felelőség megállapításához.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

### <a name="device-properties"></a>Eszköztulajdonságok

- **Minimális operációsrendszer-verzió**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, majd hozzáférhet a szervezeti erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a szervezeti erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a szervezeti erőforrásokhoz.

### <a name="system-security"></a>Rendszerbiztonság

- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához**: A felhasználók **kötelesek** jelszót megadni az eszköz eléréséhez. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Ez a beállítás az eszköz szintjén lesz alkalmazva. Ha csak a munkahelyi profil szintjén kell jelszót megkövetelni, használja a konfigurációs szabályzatot. Lásd: [androidos vállalati eszköz konfigurációs beállításai](../configuration/device-restrictions-android-for-work.md).

  - **Jelszó megkövetelt típusa**: Megadható, hogy a jelszó csak számjegyeket, vagy számokat és más karaktereket vegyesen tartalmazzon. A választható lehetőségek:
    - **Eszköz alapértelmezése**: a jelszó megfelelőségének kiértékeléséhez ügyeljen arra, hogy az **alapértelmezettnél**ne válasszon jelszót.  
    - **Jelszó szükséges, nincs korlátozás**
    - **Gyenge biometrikus**: [erős és gyenge biometria](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (az Android webhely megnyitása)
    - **Numerikus** (alapértelmezett): a jelszó csak számokat, például `123456789` értéket adhat meg. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Komplex numerikus**: ismétlődő vagy egymást követő számok, például "1111" vagy "1234", nem engedélyezettek. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **ABC**: az ábécében szereplő betűket kötelező megadni. A számok és szimbólumok nem szükségesek. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Alfanumerikus**: nagybetűket, kisbetűket és numerikus karaktereket tartalmaz. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Alfanumerikus**karakterek és szimbólumok: nagybetűket, kisbetűket, numerikus karaktereket, írásjeleket és szimbólumokat tartalmaz. Ezt is adja meg:

      - **Jelszó minimális hossza**: Itt adhatja meg a jelszó minimális hosszát 4 és 16 karakter között.
      - **Szükséges karakterek száma**: Itt adhatja meg, hogy hány karakterből kell állnia a jelszónak 0 és 16 karakter között.
      - **Szükséges kisbetűs karakterek száma**: adja meg, hogy hány kisbetűs karakterből kell állnia a jelszónak 0 és 16 karakter között kell lennie.
      - **Szükséges nagybetűk száma**: Itt adhatja meg, hogy hány nagybetűt kell tartalmaznia a jelszónak 0 és 16 karakter között.
      - **Nem szükséges karakterek száma**: Itt adhatja meg, hogy a jelszónak hány karakterből kell állnia (az ábécében szereplő betűk kivételével), 0 és 16 karakter között kell lennie.
      - **Szükséges numerikus karakterek száma**: adja meg a numerikus karakterek számát (`1`, `2`, `3` stb.) a jelszónak 0 és 16 karakter közöttinek kell lennie.
      - **Szükséges karakterek száma**: adja meg a szimbólum karaktereinek számát (`&`, `#`, `%` stb.) a jelszónak 0 és 16 karakter közöttinek kell lennie.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- A **jelszó lejárati idejét jelző napok száma**: adja meg a napok számát 1-365 között, amíg meg nem változtatja az eszköz jelszavát. Ha például a 60 nap után szeretné módosítani a jelszót, írja be `60` értéket. A jelszó lejáratakor a rendszer a felhasználókat új jelszó létrehozására kéri.
- A jelszó megadásához **szükséges jelszavak száma**: adja meg, hogy hány legutóbbi jelszó ne legyen újra felhasználható, 1-24 között. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.

- **Adattároló titkosítása az eszközön**: A **Kötelező** lehetőséget választva az adattárolók titkosítva lesznek az eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök kikényszerítik a titkosítást.

## <a name="work-profile"></a>Munkahelyi profil

### <a name="device-health"></a>Device health

- **Rootolt eszközök**: Válassza a **Letiltás** lehetőséget a rootolt (jailbreakelt) eszközök nem megfelelőként való megjelöléséhez. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- Az eszköznek **az eszköz veszélyforrási szintjére vagy az alá való helyezésének megkövetelése**: válassza ki a [Mobile Threat Defense szolgáltatás](mobile-threat-defense.md)által kiértékelt maximálisan engedélyezett veszélyforrások szintjét. Azok az eszközök, amelyek túllépik ezt a veszélyforrást, nem megfelelőként vannak megjelölve. A beállítás használatához válassza ki a megengedett kockázati szintet:

  - **Nincs konfigurálva** (alapértelmezett): Ez a beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Védett**: Ez a legbiztonságosabb beállítás. Annyit jelent, hogy az eszköz esetében semmilyen fenyegetés nem engedélyezett. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszköz vonatkozásában fennálló fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas**: Ez a legkevésbé biztonságos, minden fenyegetettségi szintet megengedő beállítás. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

#### <a name="google-play-protect"></a>Google Play Protect

- **A Google Play-szolgáltatások be van állítva**: **Kötelező** a Google Play-szolgáltatások alkalmazás telepítése és engedélyezése. A Google Play-szolgáltatások lehetővé teszik a biztonsági frissítéseket, és számos biztonsági funkció előfeltételei a hitelesített Google-eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Naprakész biztonsági szolgáltató**: **Kötelező** egy naprakész biztonsági szolgáltatóval védeni az eszközöket az ismert biztonsági kockázatokkal szemben. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **SafetyNet eszközigazolás**: Megadható a [SafetyNet igazolás](https://developer.android.com/training/safetynet/attestation.html) elvárt szintje. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A rendszer nem értékeli a beállítást a megfelelőség vagy meg nem felelőség megállapításához.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

> [!NOTE]
> Az Android Enterprise rendszerű eszközökön az **alkalmazások veszélyforrások vizsgálata** az eszköz konfigurációs szabályzata. Konfigurációs házirend használatával a rendszergazdák engedélyezhetik a beállítást az eszközön. Lásd: [Eszközkorlátozásokra vonatkozó beállítások Android Enterprise esetén](../configuration/device-restrictions-android-for-work.md)

### <a name="device-properties"></a>Eszköztulajdonságok

- **Minimális operációsrendszer-verzió**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, majd hozzáférhet a szervezeti erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a szervezeti erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a szervezeti erőforrásokhoz.

### <a name="system-security"></a>Rendszerbiztonság

- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához**: A felhasználók **kötelesek** jelszót megadni az eszköz eléréséhez. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához. Ez a beállítás az eszköz szintjén lesz alkalmazva. Ha csak a munkahelyi profil szintjén kell jelszót megkövetelni, használja a konfigurációs szabályzatot. Lásd: [androidos vállalati eszköz konfigurációs beállításai](../configuration/device-restrictions-android-for-work.md).
- **Jelszó megkövetelt típusa**: Megadható, hogy a jelszó csak számjegyeket, vagy számokat és más karaktereket vegyesen tartalmazzon. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Legalább numerikus** (alapértelmezett): adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Komplex numerikus**: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább betűk**: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább alfanumerikus**: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább alfanumerikus**karakterek: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- A **jelszó elévülési ideje (nap**): válassza ki, hogy hány nap elteltével járjon le a jelszó, és a felhasználónak új jelszót kell létrehoznia.
- **Újból nem használható jelszavak száma**: Megadhatja, hogy hány legutóbbi jelszó ne legyen újra felhasználható. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.

#### <a name="encryption"></a>Encryption

- **Adattároló titkosítása az eszközön**: A **Kötelező** lehetőséget választva az adattárolók titkosítva lesznek az eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához. 

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök kikényszerítik a titkosítást.

#### <a name="device-security"></a>Eszközbiztonság

- **Ismeretlen forrásból származó alkalmazások letiltása**: dönthet úgy, hogy **letiltja** az eszközök **biztonsági** > **ismeretlen forrással** rendelkező forrását (ez az Android 4,0 – Android 7. x; Android 8,0 és újabb verziók esetében támogatott). Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Alkalmazások közvetlen telepítéséhez az ismeretlen forrásokat engedélyezni kell. Ha nem telepít közvetlenül Android-alkalmazásokat, akkor a megfelelőségi szabályzat engedélyezéséhez adja meg a **Letiltás** beállítást ehhez a funkcióhoz.

  > [!IMPORTANT]
  > Az alkalmazások közvetlen telepítéséhez engedélyezni kell az **Ismeretlen forrásból származó alkalmazások letiltása** beállítást. Csak akkor szükséges ennek a megfelelőségi szabályzatnak a kényszerítése, ha nem telepít közvetlenül Android-alkalmazásokat az eszközökön.

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök mindig korlátozzák az ismeretlen forrásból történő telepítést.

- **A Céges portál alkalmazás futtatókörnyezetének integritása**: Válassza a **Kötelező** lehetőséget annak megerősítéséhez, hogy a Céges portál alkalmazás megfelel az összes alábbi követelménynek:

  - Telepítve van hozzá az alapértelmezett futtatókörnyezet
  - Megfelelően alá van írva
  - Nincs hibakeresési módban
  - Ismert forrásból telepítették

  Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

- **USB-hibakeresés letiltása az eszközön**: A **Letiltás** választásával megakadályozható az USB-hibakeresési funkció használata az eszközön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Ezt a beállítást nem kell konfigurálnia, mert az USB-hibakeresés már le van tiltva az androidos vállalati eszközökön.

- **Minimális biztonsági javítási szint**: Megadható a legrégebbi biztonsági javítás, amellyel az eszköz rendelkezhet. Az ennél régebbi javítási verzióval rendelkező eszközök nem megfelelőek. Az adatokat a következő formátumban kell megadni: *ÉÉÉÉ-HH-NN*.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az androidos eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-android.md) .
