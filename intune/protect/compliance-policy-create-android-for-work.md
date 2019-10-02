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
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7d38d5c71b06587b593eef46eca46f3d32f1349
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729827"
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

- **Az eszköz a veszélyforrások szintjén vagy alatt történő bekapcsolásának megkövetelése**: Válassza ki a [Mobile Threat Defense szolgáltatás](mobile-threat-defense.md)által kiértékelt, maximálisan engedélyezett veszélyforrások szintjét. Azok az eszközök, amelyek túllépik ezt a veszélyforrást, nem megfelelőként vannak megjelölve. A beállítás használatához válassza ki a megengedett kockázati szintet:

  - **Nincs konfigurálva** (alapértelmezett): Ez a beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Biztonságos**: Ez a lehetőség a legbiztonságosabb, és azt jelenti, hogy az eszközön nem lehetnek fenyegetések. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön lévő fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas**: Ez a legkevésbé biztonságos beállítás, mivel az összes veszélyforrást engedélyezi. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.
  
> [!NOTE] 
> A következő Mobile Threat Defense-(MTD-) szolgáltatók az alkalmazások konfigurációjának használatával támogatják az androidos vállalati eszközök tulajdonosának telepítését:
> - Jobb mobil 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Érdeklődjön az MTD-szolgáltatónál az androidos vállalati eszközök tulajdonosi platformjának az Intune-ban való támogatásához szükséges pontos konfigurációhoz. Ez a lista frissült, mivel az androidos vállalati eszközök tulajdonosi forgatókönyvei támogatják a MTD. 

#### <a name="google-play-protect"></a>Google Play Protect

- **Biztonság-eszköz igazolása**: Adja meg a [biztonság-igazolás](https://developer.android.com/training/safetynet/attestation.html) azon szintjét, amelynek teljesülnie kell. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

### <a name="device-properties"></a>Eszköztulajdonságok

- **Operációs rendszer minimális verziója**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, majd hozzáférhet a szervezeti erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a szervezeti erőforrásokhoz.

### <a name="system-security"></a>Rendszerbiztonság

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**: A **felhasználóknak jelszót kell** megadniuk ahhoz, hogy hozzáférjenek az eszközhöz. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Ez a beállítás az eszköz szintjén lesz alkalmazva. Ha csak a munkahelyi profil szintjén kell jelszót megkövetelni, használja a konfigurációs szabályzatot. Lásd: [androidos vállalati eszköz konfigurációs beállításai](../configuration/device-restrictions-android-for-work.md).

  - **Szükséges jelszó típusa**: Válassza ki, hogy a jelszó csak numerikus karaktereket tartalmazzon-e, illetve számok és más karakterek kombinációját. A választható lehetőségek:
    - **Eszköz alapértelmezett értéke**: A jelszó-megfelelőség kiértékeléséhez ügyeljen arra, hogy az **alapértelmezettnél**más jelszót válasszon.  
    - **Jelszó szükséges, nincs korlátozás**
    - **Gyenge biometrikus**: [Erős vagy gyenge biometria](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (az Android webhely megnyitása)
    - **Numerikus** érték (alapértelmezett): A `123456789`jelszó csak számok, például:. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Komplex numerikus**: Ismétlődő vagy egymást követő számok (például "1111" vagy "1234") nem engedélyezettek. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **ABC**: Az ábécében szereplő betűket kötelező megadni. A számok és szimbólumok nem szükségesek. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Alfanumerikus karakterek**: Nagybetűket, kisbetűket és numerikus karaktereket tartalmaz. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
    - **Alfanumerikus karakterek és szimbólumok**: Nagybetűket, kisbetűket, numerikus karaktereket, írásjeleket és szimbólumokat tartalmaz. Ezt is adja meg:

      - **Jelszó minimális hossza**: Adja meg azt a minimális hosszúságot, ameddig a jelszónak 4 és 16 karakter közöttinek kell lennie.
      - **Szükséges karakterek száma**: Adja meg, hogy hány karakterből kell állnia a jelszónak 0 és 16 karakter között.
      - **Szükséges kisbetűs karakterek száma**: Adja meg azt a kisbetűs karaktert, amelyet a jelszónak 0 és 16 karakter közötti értékkel kell rendelkeznie.
      - **Szükséges nagybetűk száma**: Adja meg a jelszóban szereplő nagybetűs karakterek számát 0 és 16 karakter között.
      - **A nem Letter karakterek kötelező száma**: Adja meg a nem betűk számát (az ábécében szereplő betűk kivételével), a jelszónak 0 és 16 karakter közöttinek kell lennie.
      - **Szükséges numerikus karakterek száma**: Adja meg a numerikus karakterek számát (`1`, `2`, `3`stb.) a jelszónak 0 és 16 karakter közöttinek kell lennie.
      - **A szimbólumok karaktereinek száma kötelező**: Adja meg a szimbólum karaktereinek számát (`&`, `#`, `%`stb.) a jelszónak 0 és 16 karakter közöttinek kell lennie.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **A jelszó lejárati ideje (nap**): Adja meg a napok számát 1-365 között, amíg meg nem változtatja az eszköz jelszavát. Ha például a 60 nap után szeretné módosítani a jelszót, írja `60`be a következőt:. A jelszó lejáratakor a rendszer a felhasználókat új jelszó létrehozására kéri.
- A **jelszó használatának megkezdése előtt a felhasználó által kért jelszavak száma**: Adja meg a legutóbbi olyan jelszavak számát, amelyeket nem lehet újra felhasználni 1-24 között. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.

- **Az eszközön lévő adattárolás titkosítása**: Válassza a **szükséges** lehetőséget az adattárolók titkosításához az eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök kikényszerítik a titkosítást.

## <a name="work-profile"></a>Munkahelyi profil

### <a name="device-health"></a>Device health

- Feltört **eszközök**: Válassza a **Letiltás** elemet a feltört (feltört) eszközök nem megfelelőként való megjelöléséhez. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Az eszköz a veszélyforrások szintjén vagy alatt történő bekapcsolásának megkövetelése**: Válassza ki a [Mobile Threat Defense szolgáltatás](mobile-threat-defense.md)által kiértékelt, maximálisan engedélyezett veszélyforrások szintjét. Azok az eszközök, amelyek túllépik ezt a veszélyforrást, nem megfelelőként vannak megjelölve. A beállítás használatához válassza ki a megengedett kockázati szintet:

  - **Nincs konfigurálva** (alapértelmezett): Ez a beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Biztonságos**: Ez a lehetőség a legbiztonságosabb, és azt jelenti, hogy az eszközön nem lehetnek fenyegetések. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön lévő fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas**: Ez a legkevésbé biztonságos beállítás, mivel az összes veszélyforrást engedélyezi. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

#### <a name="google-play-protect"></a>Google Play Protect

- **A Google Play-szolgáltatások konfigurálva vannak**: **Megkövetelheti** , hogy a Google Play-szolgáltatások alkalmazás telepítve és engedélyezve legyen. A Google Play-szolgáltatások lehetővé teszik a biztonsági frissítéseket, és számos biztonsági funkció előfeltételei a hitelesített Google-eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Naprakész biztonsági szolgáltató**: **Megkövetelheti** , hogy egy naprakész biztonsági szolgáltató képes legyen az ismert biztonsági rések elleni védelemre. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Biztonság-eszköz igazolása**: Adja meg a [biztonság-igazolás](https://developer.android.com/training/safetynet/attestation.html) azon szintjét, amelynek teljesülnie kell. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

> [!NOTE]
> Az Android Enterprise rendszerű eszközökön az **alkalmazások veszélyforrások vizsgálata** az eszköz konfigurációs szabályzata. Konfigurációs házirend használatával a rendszergazdák engedélyezhetik a beállítást az eszközön. Lásd: [Eszközkorlátozásokra vonatkozó beállítások Android Enterprise esetén](../configuration/device-restrictions-android-for-work.md)

### <a name="device-properties"></a>Eszköztulajdonságok

- **Operációs rendszer minimális verziója**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, majd hozzáférhet a szervezeti erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a szervezeti erőforrásokhoz.

### <a name="system-security"></a>Rendszerbiztonság

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**: A **felhasználóknak jelszót kell** megadniuk ahhoz, hogy hozzáférjenek az eszközhöz. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához. Ez a beállítás az eszköz szintjén lesz alkalmazva. Ha csak a munkahelyi profil szintjén kell jelszót megkövetelni, használja a konfigurációs szabályzatot. Lásd: [androidos vállalati eszköz konfigurációs beállításai](../configuration/device-restrictions-android-for-work.md).
- **Szükséges jelszó típusa**: Válassza ki, hogy a jelszó csak numerikus karaktereket tartalmazzon-e, illetve számok és más karakterek kombinációját. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Legalább numerikus** (alapértelmezett): Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Komplex numerikus**: Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább betűk**: Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább alfanumerikus karakterek**: Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
  - **Legalább alfanumerikus karakterek a következő szimbólumokkal**: Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **A jelszó lejárati ideje (nap**): Válassza ki, hogy hány nap elteltével járjon le a jelszó, és a felhasználónak új jelszót kell létrehoznia.
- **Az újrafelhasználást megakadályozó korábbi jelszavak száma**: Adja meg a legutóbbi olyan jelszavak számát, amelyeket nem lehet újra felhasználni. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.

#### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**: Válassza a **szükséges** lehetőséget az adattárolók titkosításához az eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához. 

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök kikényszerítik a titkosítást.

#### <a name="device-security"></a>Eszközbiztonság

- **Ismeretlen forrásból származó alkalmazások letiltása**: Az**ismeretlen forrásokkal** rendelkező **, az Android** > 4,0 8,0-es és újabb verzióiban támogatott forrásokkal rendelkező eszközök **letiltását** is lehetővé teszi. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Alkalmazások közvetlen telepítéséhez az ismeretlen forrásokat engedélyezni kell. Ha nem telepít közvetlenül Android-alkalmazásokat, akkor a megfelelőségi szabályzat engedélyezéséhez adja meg a **Letiltás** beállítást ehhez a funkcióhoz.

  > [!IMPORTANT]
  > Az alkalmazások közvetlen telepítéséhez engedélyezni kell az **Ismeretlen forrásból származó alkalmazások letiltása** beállítást. Csak akkor szükséges ennek a megfelelőségi szabályzatnak a kényszerítése, ha nem telepít közvetlenül Android-alkalmazásokat az eszközökön.

  Ezt a beállítást nem kell konfigurálnia, mert az Android Enterprise-eszközök mindig korlátozzák az ismeretlen forrásból történő telepítést.

- **Vállalati portál alkalmazás futtatókörnyezetének integritása**: A **kötelező** gombra kattintva erősítse meg, hogy a céges portál alkalmazás megfelel az alábbi követelményeknek:

  - Telepítve van hozzá az alapértelmezett futtatókörnyezet
  - Megfelelően alá van írva
  - Nincs hibakeresési módban
  - Ismert forrásból telepítették

  Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

- **USB-hibakeresés letiltása az eszközön**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy az eszközök az USB-hibakeresés funkciót használják. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Ezt a beállítást nem kell konfigurálnia, mert az USB-hibakeresés már le van tiltva az androidos vállalati eszközökön.

- **Minimális biztonsági javítási szint**: Válassza ki a legrégebbi biztonsági javítási szintet, amelyet az eszköz tartalmazhat. Az ennél régebbi javítási verzióval rendelkező eszközök nem megfelelőek. Az adatokat a következő formátumban kell megadni: *ÉÉÉÉ-HH-NN*.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az androidos eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-android.md) .
