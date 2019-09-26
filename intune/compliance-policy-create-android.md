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
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7c6cec515bfda95fed922785705b0e0b5339983
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/25/2019
ms.locfileid: "71305083"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk felsorolja és leírja az Android-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat a feltört (feltört) eszközök nem megfelelőként való megjelölésére, az engedélyezett veszélyforrási szint beállítására, a Google Play Protect engedélyezésére és egyebekre használhatja.

Ez a funkció az alábbiakra vonatkozik:

- Android

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításban válassza az **Android** lehetőséget.

## <a name="device-health"></a>Device health

- Feltört **eszközök**: Válassza a **Letiltás** elemet a feltört (feltört) eszközök nem megfelelőként való megjelöléséhez. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Az eszköz a veszélyforrások szintjén vagy alatt történő bekapcsolásának megkövetelése**: Ezzel a beállítással elvégezheti a kockázatértékelést, amely a megtekintő mobil végpont biztonsági megoldásának a megfelelőségi feltétele. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához. A beállítás használatához válassza ki a megengedett kockázati szintet:
  - **Biztonságos**: Ez a lehetőség a legbiztonságosabb, mert az eszköz nem rendelkezhet fenyegetésekkel. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön fennálló fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas**: Ez a beállítás a legkevésbé biztonságos, és lehetővé teszi az összes veszélyforrás szintjét. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

### <a name="google-play-protect"></a>Google Play Protect

- **A Google Play-szolgáltatások konfigurálva vannak**: **Megkövetelheti** , hogy a Google Play-szolgáltatások alkalmazás telepítve és engedélyezve legyen. A Google Play-szolgáltatások lehetővé teszik a biztonsági frissítéseket, és számos biztonsági funkció előfeltételei a hitelesített Google-eszközökön. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Naprakész biztonsági szolgáltató**: **Megkövetelheti** , hogy egy naprakész biztonsági szolgáltató képes legyen az ismert biztonsági rések elleni védelemre. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Veszélyforrások vizsgálata az alkalmazásokban**: Az Android- **alkalmazások ellenőrzése** funkció engedélyezése **kötelező** . Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  > [!NOTE]
  > A régebbi Android platformon ez a szolgáltatás egy megfelelőségi beállítás. Az Intune csak azt tudja ellenőrizni, hogy eszközszinten engedélyezett-e ez a beállítás.

- **Biztonság-eszköz igazolása**: Adja meg a [biztonság-igazolás](https://developer.android.com/training/safetynet/attestation.html) azon szintjét, amelynek teljesülnie kell. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A beállítás nincs kiértékelve megfelelőségi vagy meg nem felelés esetén.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

> [!NOTE]
> Ha a Google Play Protect-beállításokat az alkalmazás-védelmi házirendek használatával szeretné konfigurálni, tekintse meg az [Intune app Protection házirend-beállítások](app-protection-policy-settings-android.md#conditional-launch) Android rendszeren című témakört

## <a name="device-property-settings"></a>Eszköztulajdonság-beállítások

- **Operációs rendszer minimális verziója**: Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ez után pedig hozzáférést kap a vállalati erőforrásokhoz.
- **Maximális operációsrendszer-verzió**: Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb verziót használ, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak ekkor az informatikai rendszergazdához kell fordulnia. Az eszköz csak akkor használható a vállalati erőforrások elérésére, ha a szabályt úgy módosítják, hogy engedélyezze az eszköz operációs rendszerének verzióját is.

## <a name="system-security-settings"></a>A rendszer biztonsági beállításai

### <a name="password"></a>Windows 10

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**: A **felhasználóknak jelszót kell** megadniuk ahhoz, hogy hozzáférjenek az eszközhöz. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Jelszó minimális hossza**: Adja meg a felhasználók jelszavában szereplő számjegyek vagy karakterek minimális számát.
- **Szükséges jelszó típusa**: Válassza ki, hogy a jelszó csak numerikus karaktereket tartalmazzon-e, illetve számok és más karakterek kombinációját. A választható lehetőségek:
  - **Eszköz alapértelmezett értéke**: A jelszó-megfelelőség kiértékeléséhez ügyeljen arra, hogy az **alapértelmezettnél**más jelszót válasszon.
  - **Alacsony biztonságú biometrikus**
  - **Legalább számok** (alapértelmezett)
  - **Komplex numerikus**: Ismétlődő vagy egymást követő számok (például `1111` vagy `1234`) nem engedélyezettek.
  - **Legalább betűk** 
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Jelszó érvényessége (napokban)** : Válassza ki, hogy hány nap elteltével járjon le a jelszó, és a felhasználónak új jelszót kell létrehoznia.
- **Az újrafelhasználást megakadályozó korábbi jelszavak száma**: Adja meg a legutóbbi olyan jelszavak számát, amelyeket nem lehet újra felhasználni. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.

### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása** (Android 4,0 és újabb verziók, vagy KNOX 4,0 és újabb verziók): Válassza a **szükséges** lehetőséget az adattárolók titkosításához az eszközökön. Az eszközök **A mobileszközök zárolásának feloldásához jelszó szükséges** beállítás használatával titkosíthatók. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

### <a name="device-security"></a>Eszközbiztonság

- **Ismeretlen forrásból származó alkalmazások letiltása**: A "biztonsági > ismeretlen források" engedélyezett források **letiltását** lehetővé teszi az Android 4,0 – Android 7. x rendszeren, az Android 8,0 és újabb verziók nem támogatják. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

  Alkalmazások közvetlen telepítéséhez az ismeretlen forrásokat engedélyezni kell. Ha nem telepít közvetlenül Android-alkalmazásokat, akkor a megfelelőségi szabályzat engedélyezéséhez adja meg a **Letiltás** beállítást ehhez a funkcióhoz. 

  > [!IMPORTANT]
  > Az alkalmazások közvetlen telepítéséhez engedélyezni kell az **Ismeretlen forrásból származó alkalmazások letiltása** beállítást. Csak akkor szükséges ennek a megfelelőségi szabályzatnak a kényszerítése, ha nem telepít közvetlenül Android-alkalmazásokat az eszközökön.

- **Vállalati portál alkalmazás futtatókörnyezetének integritása**: A **kötelező** gombra kattintva erősítse meg, hogy a céges portál alkalmazás megfelel az alábbi követelményeknek:

  - Telepítve van hozzá az alapértelmezett futtatókörnyezet
  - Megfelelően alá van írva
  - Nincs hibakeresési módban
  - Ismert forrásból telepítették

  Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.

- **USB-hibakeresés letiltása az eszközön** (Android 4,2 vagy újabb): A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy az eszközök az USB-hibakeresés funkciót használják. Ha a **Nincs konfigurálva** (alapértelmezett) lehetőséget választja, a rendszer ezt a beállítást nem veszi figyelembe a megfelelőség, vagy meg nem felelőség megállapításához.
- **Minimális biztonsági javítási szint** (Android 6,0 vagy újabb): Válassza ki a legrégebbi biztonsági javítási szintet, amelyet az eszköz tartalmazhat. Az ennél régebbi javítási verzióval rendelkező eszközök nem megfelelőek. A dátumot `YYYY-MM-DD` formátumban kell megadni.
- **Korlátozott alkalmazások**: Adja meg az **alkalmazás nevét** és az alkalmazáscsomag **azonosítóját** a korlátozni kívánt alkalmazásokhoz. Válassza a **Hozzáadás** lehetőséget. A legalább egy telepített korlátozott alkalmazással rendelkező eszközök megjelölése nem megfelelő.

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="locations"></a>Helyek

A házirendben az eszköz helye alapján kényszerítheti a megfelelőséget. Válasszon a meglévő helyekről. Még nem rendelkezik hellyel? Az Intune-ban a [webhelyek (hálózati kerítés) használatával](use-network-locations.md) biztosítunk útmutatást.

1. Válassza a **helyszínek** > **lehetőséget**.
2. A listában jelölje ki a helyet > **válassza a lehetőséget**.
3. **Mentse** a szabályzatot.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az androidos vállalati eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-android-for-work.md) .
