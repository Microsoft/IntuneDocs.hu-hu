---
title: Az Android-eszközök megfelelőségi beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg az Android-eszközök megfelelőségének beállításakor használható beállításokat a Microsoft Intuneban. Állítsa be a jelszavakat, válassza ki a minimális vagy maximális operációsrendszer-verziót, korlátozza az egyes alkalmazásokat, megakadályozza a jelszó újrafelhasználását, és így tovább.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4237b54b3ea89fcf75ce5a21f08012f384eed95c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502514"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és leírja az Android-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat a feltört (feltört) eszközök nem megfelelőként való megjelölésére, az engedélyezett veszélyforrási szint beállítására, a Google Play Protect engedélyezésére és egyebekre használhatja.

Ez a funkció az alábbiakra vonatkozik:

- Android:

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításban válassza az **Android** lehetőséget.

## <a name="device-health"></a>Device health

- **Rootolt eszközök**: Válassza a **Letiltás** lehetőséget a rootolt (jailbreakelt) eszközök nem megfelelőként való megjelöléséhez. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- Az eszköznek **az eszköz veszélyforrási szintjén való használatának megkövetelése**: ezzel a beállítással a kockázatértékelés feltétele a megfelelőségi feladatnak. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához. A beállítás használatához válassza ki a megengedett kockázati szintet:
  - **Védett**: Ez a legbiztonságosabb beállítás, mivel az eszköz esetében semmilyen fenyegetés nem engedélyezett. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas**: Ez a legkevésbé biztonságos, minden fenyegetettségi szintet megengedő beállítás. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

### <a name="google-play-protect"></a>Google Play Protect

- **A Google Play-szolgáltatások be van állítva**: **Kötelező** a Google Play-szolgáltatások alkalmazás telepítése és engedélyezése. A Google Play-szolgáltatások lehetővé teszik a biztonsági frissítéseket, és számos biztonsági funkció előfeltételei a hitelesített Google-eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Naprakész biztonsági szolgáltató**: **Kötelező** egy naprakész biztonsági szolgáltatóval védeni az eszközöket az ismert biztonsági kockázatokkal szemben. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Alkalmazások fenyegetettségvizsgálata**: **Kötelező** az androidos **Alkalmazások ellenőrzése** szolgáltatás engedélyezése. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  > [!NOTE]
  > A régebbi Android platformon ez a szolgáltatás egy megfelelőségi beállítás. Az Intune csak azt tudja ellenőrizni, hogy eszközszinten engedélyezett-e ez a beállítás.

- **SafetyNet eszközigazolás**: Megadható a [SafetyNet igazolás](https://developer.android.com/training/safetynet/attestation.html) elvárt szintje. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A rendszer nem értékeli a beállítást a megfelelőség vagy meg nem felelőség megállapításához.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

> [!NOTE]
> Ha a Google Play Protect-beállításokat az alkalmazás-védelmi házirendek használatával szeretné konfigurálni, tekintse meg az [Intune app Protection házirend-beállítások](../apps/app-protection-policy-settings-android.md#conditional-launch) Android rendszeren című témakört

## <a name="device-property-settings"></a>Eszköztulajdonság-beállítások

- **Minimális operációsrendszer-verzió**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként fog szerepelni. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ez után pedig hozzáférést kap a vállalati erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb fut, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a vállalati erőforrásokhoz.

## <a name="system-security-settings"></a>A rendszer biztonsági beállításai

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához**: A felhasználók **kötelesek** jelszót megadni az eszköz eléréséhez. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Jelszó minimális hossza**: Meghatározhatja a felhasználó jelszavában szereplő számjegyek vagy karakterek minimális számát.
- **Jelszó megkövetelt típusa**: Megadható, hogy a jelszó csak számjegyeket, vagy számokat és más karaktereket vegyesen tartalmazzon. A választható lehetőségek:
  - **Eszköz alapértelmezése**: a jelszó megfelelőségének kiértékeléséhez ügyeljen arra, hogy az **alapértelmezettnél**ne válasszon jelszót.
  - **Alacsony biztonságú biometrikus**
  - **Legalább számok** (alapértelmezett)
  - **Komplex numerikus**: Nem lehet ismétlődő vagy egymást követő számokat megadni (például `1111` vagy `1234`).
  - **Legalább betűk** 
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Jelszó érvényessége (napokban)** : Válassza ki, hány nap elteltével járjon le a jelszó, ami után a felhasználónak újat kell létrehoznia.
- **Újból nem használható jelszavak száma**: Megadhatja, hogy hány legutóbbi jelszó ne legyen újra felhasználható. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.

### <a name="encryption"></a>Encryption

- **Adattároló titkosítása az eszközön** (Android 4.0 és újabb, vagy KNOX 4.0 és újabb): A **Kötelező** lehetőséget választva az adattárolók titkosítva lesznek az eszközökön. Az eszközök **A mobileszközök zárolásának feloldásához jelszó szükséges** beállítás használatával titkosíthatók. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

### <a name="device-security"></a>Eszközbiztonság

- **Ismeretlen forrásból származó alkalmazások letiltása**: Választásával **letilthatók** a „Biztonság > Ismeretlen források” alatti forrásokat engedélyező eszközök (támogatott az Android 4.0 – Android 7.x. rendszereken, és nem támogatott az Android 8.0-s és újabb rendszereken). Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Alkalmazások közvetlen telepítéséhez az ismeretlen forrásokat engedélyezni kell. Ha nem telepít közvetlenül Android-alkalmazásokat, akkor a megfelelőségi szabályzat engedélyezéséhez adja meg a **Letiltás** beállítást ehhez a funkcióhoz. 

  > [!IMPORTANT]
  > Az alkalmazások közvetlen telepítéséhez engedélyezni kell az **Ismeretlen forrásból származó alkalmazások letiltása** beállítást. Csak akkor szükséges ennek a megfelelőségi szabályzatnak a kényszerítése, ha nem telepít közvetlenül Android-alkalmazásokat az eszközökön.

- **A Céges portál alkalmazás futtatókörnyezetének integritása**: Válassza a **Kötelező** lehetőséget annak megerősítéséhez, hogy a Céges portál alkalmazás megfelel az összes alábbi követelménynek:

  - Telepítve van hozzá az alapértelmezett futtatókörnyezet
  - Megfelelően alá van írva
  - Nincs hibakeresési módban
  - Ismert forrásból telepítették

  Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

- **USB-hibakeresés letiltása az eszközön** (Android 4.2 vagy újabb): a **Letiltás** választásával megakadályozható az eszközön az USB-hibakeresés funkció használata. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Minimális biztonsági javítási szint** (Android 6.0 vagy újabb): Megadható a legrégebbi biztonsági javítás, amellyel az eszköz rendelkezhet. Az ennél régebbi javítási verzióval rendelkező eszközök nem megfelelőek. A dátumot `YYYY-MM-DD` formátumban kell megadni.
- **Korlátozott alkalmazások**: Adja meg az **Alkalmazás neve** és az **Alkalmazásköteg-azonosító** adatot a korlátozni kívánt alkalmazásokhoz. Válassza a **Hozzáadás** lehetőséget. A legalább egy telepített korlátozott alkalmazással rendelkező eszközök megjelölése nem megfelelő.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="locations"></a>Helyek

A házirendben az eszköz helye alapján kényszerítheti a megfelelőséget. Válasszon a meglévő helyekről. Még nem rendelkezik hellyel? Az Intune-ban a [webhelyek (hálózati kerítés) használatával](use-network-locations.md) biztosítunk útmutatást.

1. Válasszon **helyszíneket @no__t-** 1**válasszon helyet**.
2. A listában jelölje ki a helyet > **válassza a lehetőséget**.
3. **Mentse** a szabályzatot.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az androidos vállalati eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-android-for-work.md) .
