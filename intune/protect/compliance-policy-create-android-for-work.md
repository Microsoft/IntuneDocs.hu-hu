---
title: Az androidos nagyvállalati megfelelőségi beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg az androidos vállalati eszközök megfelelőségének beállításakor használható összes beállítást a Microsoft Intuneban. Állítsa be a jelszavakat, válassza ki a minimális vagy maximális operációsrendszer-verziót, korlátozza az egyes alkalmazásokat, megakadályozza a jelszó újrafelhasználását, és így tovább.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/07/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60244bb268f7becadc427c397d7c2d1562bcf6b5
ms.sourcegitcommit: ea81ad5f33f18d9fe43254e27e02de5eaef74a05
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75722606"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Androidos vállalati beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

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

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Biztonságos** – ez a legbiztonságosabb beállítás, ami azt jelenti, hogy az eszközhöz nem tartozhat fenyegetés. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony**: – az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes** – az eszköz abban az esetben minősül megfelelőnek, ha az eszközön lévő fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas** – ez a legkevésbé biztonságos beállítás, mivel az összes veszélyforrást engedélyezi. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.
  
> [!NOTE] 
> A Mobile Threat Defense (MTD) szolgáltatói az alkalmazások konfigurációját használó androidos vállalati eszközök tulajdonosi telepítései esetében támogatottak. Érdeklődjön az MTD-szolgáltatónál az androidos vállalati eszközök tulajdonosi platformjának az Intune-ban való támogatásához szükséges pontos konfigurációhoz.

#### <a name="google-play-protect"></a>Google Play Protect

- **SafetyNet eszközigazolás**: Megadható a [SafetyNet igazolás](https://developer.android.com/training/safetynet/attestation.html) elvárt szintje. A választható lehetőségek:
  - **Nincs konfigurálva** (*alapértelmezett*) – a beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

### <a name="device-properties"></a>Eszköztulajdonságok

#### <a name="operating-system-version"></a>Operációs rendszer verziója

- **Minimális operációsrendszer-verzió**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, majd hozzáférhet a szervezeti erőforrásokhoz.

  *Alapértelmezés szerint nincs konfigurálva a verzió*.

- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a szervezeti erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a szervezeti erőforrásokhoz.

  *Alapértelmezés szerint nincs konfigurálva a verzió*.

- **Minimális biztonsági javítási szint**: válassza ki a legrégebbi biztonsági javítási szintet, amelyet az eszköz tartalmazhat. Az ennél régebbi javítási verzióval rendelkező eszközök nem megfelelőek. A dátumot éééé-hh-nn formátumban kell megadni.

  *Alapértelmezés szerint nincs beállítva dátum*.


### <a name="system-security"></a>Rendszerbiztonság

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Kötelező** – a felhasználóknak jelszót kell megadniuk ahhoz, hogy hozzáférjenek az eszközhöz. 

  Ez a beállítás az eszköz szintjén érvényes. Ha csak a munkahelyi profil szintjén kell jelszót megkövetelni, használja a konfigurációs szabályzatot. Lásd: [androidos vállalati eszköz konfigurációs beállításai](../configuration/device-restrictions-android-for-work.md).

  - **Jelszó megkövetelt típusa**: Megadható, hogy a jelszó csak számjegyeket, vagy számokat és más karaktereket vegyesen tartalmazzon. A választható lehetőségek:
    - **Alapértelmezett eszköz** – a jelszó-megfelelőség kiértékelése érdekében ügyeljen arra, hogy az **eszköz alapértelmezett értékén**kívül más jelszót válasszon.  
    - **Jelszó szükséges, nincs korlátozás**
    - **Gyenge biometrikus** - [erős és gyenge biometria](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (az Android webhelyének megnyitása)
    - **Numerikus** (*alapértelmezett*): a jelszó csak számok, például `123456789`lehet. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Komplex numerikus** – ismétlődő vagy egymást követő számok, például "1111" vagy "1234", nem engedélyezettek. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - Az **ábécében** szereplő betűket kötelező megadni. A számok és szimbólumok nem szükségesek. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Alfanumerikus** – nagybetűket, kisbetűket és numerikus karaktereket is tartalmaz. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Alfanumerikus** karakterek és szimbólumok – nagybetűket, kisbetűket, numerikus karaktereket, írásjeleket és szimbólumokat tartalmaz. Ezt is adja meg:
    
    A választott *jelszó* típusától függően a következő beállítások érhetők el:  
    - **Jelszó minimális hossza**: Itt adhatja meg a jelszó minimális hosszát 4 és 16 karakter között.  

    - **Szükséges karakterek száma**: Itt adhatja meg, hogy hány karakterből kell állnia a jelszónak 0 és 16 karakter között.

    - **Szükséges kisbetűs karakterek száma**: adja meg, hogy hány kisbetűs karakterből kell állnia a jelszónak 0 és 16 karakter között kell lennie.

    - **Szükséges nagybetűk száma**: Itt adhatja meg, hogy hány nagybetűt kell tartalmaznia a jelszónak 0 és 16 karakter között.

    - **Nem szükséges karakterek száma**: Itt adhatja meg, hogy a jelszónak hány karakterből kell állnia (az ábécében szereplő betűk kivételével), 0 és 16 karakter között kell lennie.

    - **Megkövetelt numerikus karakterek száma**: megadhatja, hogy a jelszónak 0 és 16 karakter közöttinek kell lennie (`1`, `2`, `3`stb.).
    
    - **Szükséges karakterek száma**: Itt adhatja meg, hogy hány szimbólumot kell megadni (`&`, `#`, `%`stb.) a jelszónak 0 és 16 karakter közöttinek kell lennie.
 
- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát. A beállítások közé tartozik a *nem konfigurált*alapértelmezett érték, valamint *1 perc* és *8 óra*között.

- A **jelszó lejárati idejét jelző napok száma**: adja meg a napok számát 1-365 között, amíg meg nem változtatja az eszköz jelszavát. Ha például a 60 nap után szeretné módosítani a jelszót, írja be `60`. A jelszó lejáratakor a rendszer a felhasználókat új jelszó létrehozására kéri.

   *Alapértelmezés szerint nincs beállítva érték*.

- A jelszó megadásához **szükséges jelszavak száma**: adja meg, hogy hány legutóbbi jelszó ne legyen újra felhasználható, 1-24 között. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.  

    *Alapértelmezés szerint nincs konfigurálva a verzió*.

#### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - Az adattároló titkosításának **megkövetelése** az eszközökön.  

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök kikényszerítik a titkosítást.

## <a name="work-profile"></a>Munkahelyi profil

### <a name="device-health"></a>Eszközállapot

- Feltört **eszközök**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Blokkolt** feltört (feltört) eszközök nem megfelelőként való megjelölése.  

- Az eszköznek **az eszköz veszélyforrási szintjére vagy az alá való helyezésének megkövetelése**: válassza ki a [Mobile Threat Defense szolgáltatás](mobile-threat-defense.md)által kiértékelt maximálisan engedélyezett veszélyforrások szintjét. Azok az eszközök, amelyek túllépik ezt a veszélyforrást, nem megfelelőként vannak megjelölve. A beállítás használatához válassza ki a megengedett kockázati szintet:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Biztonságos** – ez a legbiztonságosabb beállítás, ami azt jelenti, hogy az eszközhöz nem tartozhat fenyegetés. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony** – az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes** – az eszköz abban az esetben minősül megfelelőnek, ha az eszközön lévő fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas** – ez a legkevésbé biztonságos beállítás, mivel az összes veszélyforrást engedélyezi. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

#### <a name="google-play-protect"></a>Google Play Protect

- **A Google Play-szolgáltatások konfigurálva vannak**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Required (kötelező** ) – meg kell követelni, hogy a Google Play Services alkalmazás telepítve és engedélyezve legyen. A Google Play-szolgáltatások lehetővé teszik a biztonsági frissítéseket, és számos biztonsági funkció előfeltételei a hitelesített Google-eszközökön. 
  
- **Naprakész biztonsági szolgáltató**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Kötelező** – megköveteli, hogy egy naprakész biztonsági szolgáltató képes legyen az ismert biztonsági rések elleni védelemre. 
  
- **SafetyNet eszközigazolás**: Megadható a [SafetyNet igazolás](https://developer.android.com/training/safetynet/attestation.html) elvárt szintje. A választható lehetőségek:
  - **Nincs konfigurálva** (*alapértelmezett*) – a beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

> [!NOTE]
> Az Android Enterprise rendszerű eszközökön az **alkalmazások veszélyforrások vizsgálata** az eszköz konfigurációs szabályzata. Konfigurációs házirend használatával a rendszergazdák engedélyezhetik a beállítást az eszközön. Lásd: [Eszközkorlátozásokra vonatkozó beállítások Android Enterprise esetén](../configuration/device-restrictions-android-for-work.md)

### <a name="device-properties"></a>Eszköztulajdonságok

#### <a name="operating-system-version"></a>Operációs rendszer verziója

- **Minimális operációsrendszer-verzió**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, majd hozzáférhet a szervezeti erőforrásokhoz.

  *Alapértelmezés szerint nincs konfigurálva a verzió*.

- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb operációs rendszer van használatban, a szervezeti erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a szervezeti erőforrásokhoz.

  *Alapértelmezés szerint nincs konfigurálva a verzió*.

### <a name="system-security"></a>Rendszerbiztonság

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást. 
  - **Kötelező** – a felhasználóknak jelszót kell megadniuk ahhoz, hogy hozzáférjenek az eszközhöz.  

  Ez a beállítás az eszköz szintjén érvényes. Ha csak a munkahelyi profil szintjén kell jelszót megkövetelni, használja a konfigurációs szabályzatot. Lásd: [androidos vállalati eszköz konfigurációs beállításai](../configuration/device-restrictions-android-for-work.md).

- **Jelszó megkövetelt típusa**: Megadható, hogy a jelszó csak számjegyeket, vagy számokat és más karaktereket vegyesen tartalmazzon. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Legalább numerikus** (*alapértelmezett*): adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Komplex numerikus**: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább betűk**: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább alfanumerikus**: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább alfanumerikus**karakterek: adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.

  A választott *jelszó* típusától függően a következő beállítások érhetők el:  
  - **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát. A beállítások közé tartozik a *nem konfigurált*alapértelmezett érték, valamint *1 perc* és *8 óra*között.

  - A **jelszó lejárati idejét jelző napok száma**: adja meg a napok számát 1-365 között, amíg meg nem változtatja az eszköz jelszavát. Ha például a 60 nap után szeretné módosítani a jelszót, írja be `60`. A jelszó lejáratakor a rendszer a felhasználókat új jelszó létrehozására kéri.

  - **Jelszó minimális hossza**: Itt adhatja meg a jelszó minimális hosszát 4 és 16 karakter között. 
  
  - **Újból nem használható jelszavak száma**: Megadhatja, hogy hány legutóbbi jelszó ne legyen újra felhasználható. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.

#### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - Az adattároló titkosításának **megkövetelése** az eszközökön.  

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök kikényszerítik a titkosítást.

#### <a name="device-security"></a>Eszközbiztonság

- **Ismeretlen forrásból származó alkalmazások letiltása**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Blokkolja** a **biztonsági** > **ismeretlen forrásokkal** rendelkező eszközök használatát (az Android 4,0-es*verziójában támogatott források (Android 7. x). Android 8,0 és újabb rendszereken nem támogatott*).  

  Alkalmazások közvetlen telepítéséhez az ismeretlen forrásokat engedélyezni kell. Ha nem telepít közvetlenül Android-alkalmazásokat, akkor a megfelelőségi szabályzat engedélyezéséhez adja meg a **Letiltás** beállítást ehhez a funkcióhoz.

  > [!IMPORTANT]
  > Az alkalmazások közvetlen telepítéséhez engedélyezni kell az **Ismeretlen forrásból származó alkalmazások letiltása** beállítást. Csak akkor szükséges ennek a megfelelőségi szabályzatnak a kényszerítése, ha nem telepít közvetlenül Android-alkalmazásokat az eszközökön.

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök mindig korlátozzák az ismeretlen forrásból történő telepítést.

- **Vállalati portál alkalmazás futtatókörnyezetének integritása**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Require (kötelező** ) – válassza a *kötelező* lehetőséget annak megerősítéséhez, hogy a céges portál alkalmazás megfelel az alábbi követelményeknek:
    - Telepítve van hozzá az alapértelmezett futtatókörnyezet
    - Megfelelően alá van írva
    - Nincs hibakeresési módban
    - Ismert forrásból telepítették

- **USB-hibakeresés letiltása az eszközön**: 
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Letiltás** – megakadályozza, hogy az eszközök az USB-hibakeresés funkciót használják.  

  Ezt a beállítást nem kell konfigurálnia, mert az USB-hibakeresés már le van tiltva az androidos vállalati eszközökön.

- **Minimális biztonsági javítási szint**: válassza ki a legrégebbi biztonsági javítási szintet, amelyet az eszköz tartalmazhat. Az ennél régebbi javítási verzióval rendelkező eszközök nem megfelelőek. A dátumot éééé-hh-nn formátumban kell megadni.

  *Alapértelmezés szerint nincs beállítva dátum*.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az androidos eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-android.md) .
