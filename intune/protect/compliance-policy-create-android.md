---
title: Az Android-eszközök megfelelőségi beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Tekintse meg az Android-eszközök megfelelőségének beállításakor használható beállításokat a Microsoft Intuneban. Állítsa be a jelszavakat, válassza ki a minimális vagy maximális operációsrendszer-verziót, korlátozza az egyes alkalmazásokat, megakadályozza a jelszó újrafelhasználását, és így tovább.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8efb9dcf9129375252b5d9a7d1e6255dce39625c
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801410"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android-beállítások az eszközök megfelelő vagy nem megfelelőként való megjelöléséhez az Intune-nal

Ez a cikk felsorolja és leírja az Android-eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat a feltört (feltört) eszközök nem megfelelőként való megjelölésére, az engedélyezett veszélyforrási szint beállítására, a Google Play Protect engedélyezésére és egyebekre használhatja.

Ez a funkció az alábbiakra vonatkozik:

- Android-eszköz rendszergazdája

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **platform**területen válassza az **Android-eszköz rendszergazdája**lehetőséget.

## <a name="device-health"></a>Eszközállapot

- Feltört **eszközök**:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Blokkolt** feltört (feltört) eszközök nem megfelelőként való megjelölése.

- **Az eszköz a veszélyforrások szintjén vagy alatt történő bekapcsolásának megkövetelése**:

  Ezzel a beállítással végezheti el a kockázatértékelést egy csatlakoztatott Mobile Threat Defense-szolgáltatásból a megfelelőség feltételeként.
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást. 
  - **Biztonságos** – ez a lehetőség a legbiztonságosabb, mert az eszköz nem rendelkezhet fenyegetésekkel. Bármilyen szintű fenyegetés észlelésekor az eszközt a rendszer nem megfelelőként fogja értékeli.
  - **Alacsony** – az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes** – az eszköz abban az esetben minősül megfelelőnek, ha az eszközön fennálló fenyegetések alacsony vagy közepes szintűek. Magas szintű fenyegetés észlelésekor a rendszer nem megfelelőként értékeli az eszközt.
  - **Magas** – ez a legkevésbé biztonságos beállítás, és lehetővé teszi az összes veszélyforrás szintjét. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.

### <a name="google-play-protect"></a>Google Play Protect

- **A Google Play-szolgáltatások konfigurálva vannak**:

  A Google Play-szolgáltatások lehetővé teszik a biztonsági frissítéseket, és számos biztonsági funkció előfeltételei a hitelesített Google-eszközökön.

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.  
  - **Required (kötelező** ) – meg kell követelni, hogy a Google Play Services alkalmazás telepítve és engedélyezve legyen.  

- **Naprakész biztonsági szolgáltató**:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Kötelező** – megköveteli, hogy egy naprakész biztonsági szolgáltató képes legyen az ismert biztonsági rések elleni védelemre.

- **Veszélyforrások vizsgálata az alkalmazásokban**:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Required (kötelező** ): az Android- **alkalmazások ellenőrzése** funkció engedélyezve van.

  > [!NOTE]
  > A régebbi Android platformon ez a szolgáltatás egy megfelelőségi beállítás. Az Intune csak azt tudja ellenőrizni, hogy eszközszinten engedélyezett-e ez a beállítás.

- **Biztonság-eszköz igazolása**:

  Adja meg a [biztonság-igazolás](https://developer.android.com/training/safetynet/attestation.html) azon szintjét, amelynek teljesülnie kell. A választható lehetőségek:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Alapvető integritás ellenőrzése**
  - **Alapvető integritás ellenőrzés és tanúsított eszközök**

> [!NOTE]
> Ha a Google Play Protect-beállításokat az alkalmazás-védelmi házirendek használatával szeretné konfigurálni, tekintse meg az [Intune app Protection házirend-beállítások](../apps/app-protection-policy-settings-android.md#conditional-launch) Android rendszeren című témakört

## <a name="device-properties"></a>Eszköztulajdonságok

### <a name="operating-system-version"></a>Operációs rendszer verziója 

- **Operációs rendszer minimális verziója**:

  Ha egy eszköz nem teljesíti az operációs rendszer szükséges minimális verziójára vonatkozó követelményt, nem megfelelőként jelenik meg. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó frissítheti az eszközt, ez után pedig hozzáférést kap a vállalati erőforrásokhoz.

  *Alapértelmezés szerint nincs konfigurálva a verzió*.

- **Maximális operációsrendszer-verzió**:

  Ha egy eszközön a szabályban megadott operációsrendszer-verziónál újabb verziót használ, a vállalati erőforrásokhoz való hozzáférés le lesz tiltva. A felhasználónak kapcsolatba kell lépnie a rendszergazdával. Amíg egy szabály nem módosul az operációs rendszer verziójának engedélyezésére, az eszköz nem fér hozzá a vállalati erőforrásokhoz.

  *Alapértelmezés szerint nincs konfigurálva a verzió*.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Jelszó

<!-- Removed
- **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.   


- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password. When you choose **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.

- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

-->

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Kötelező** – a felhasználóknak jelszót kell megadniuk ahhoz, hogy hozzáférjenek az eszközhöz.

- **Szükséges jelszó típusa**:

  Válassza ki, hogy a jelszó csak numerikus karaktereket tartalmazzon-e, illetve számok és más karakterek kombinációját. A választható lehetőségek:

  - **Alapértelmezett eszköz** – a jelszó-megfelelőség kiértékelése érdekében ügyeljen arra, hogy az **eszköz alapértelmezett értékén**kívül más jelszót válasszon.
  - **Alacsony biztonságú biometrikus**
  - **Legalább számok**
  - **Komplex numerikus** – ismétlődő vagy egymást követő számok, például `1111` vagy `1234`, nem engedélyezettek.
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**

### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**:  
  *Android 4,0 vagy újabb, vagy KNOX 4,0 és újabb rendszereken támogatott.*

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - Az adattároló titkosításának **megkövetelése** az eszközökön. Az eszközök **A mobileszközök zárolásának feloldásához jelszó szükséges** beállítás használatával titkosíthatók.

### <a name="device-security"></a>Eszközbiztonság

- **Ismeretlen forrásból származó alkalmazások letiltása**:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Blokkolja** a **biztonsági > ismeretlen forrásokkal** rendelkező eszközök használatát (az Android 4,0-es*verziójában támogatott források (Android 7. x). Android 8,0 és újabb rendszereken nem támogatott.* )

  Alkalmazások közvetlen telepítéséhez az ismeretlen forrásokat engedélyezni kell. Ha nem telepít közvetlenül Android-alkalmazásokat, akkor a megfelelőségi szabályzat engedélyezéséhez adja meg a **Letiltás** beállítást ehhez a funkcióhoz.

  > [!IMPORTANT]
  > Az alkalmazások közvetlen telepítéséhez engedélyezni kell az **Ismeretlen forrásból származó alkalmazások letiltása** beállítást. Csak akkor szükséges ennek a megfelelőségi szabályzatnak a kényszerítése, ha nem telepít közvetlenül Android-alkalmazásokat az eszközökön.

- **Vállalati portál alkalmazás futtatókörnyezetének integritása**:

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Require (kötelező** ) – válassza a *kötelező* lehetőséget annak megerősítéséhez, hogy a céges portál alkalmazás megfelel az alábbi követelményeknek:

    - Telepítve van hozzá az alapértelmezett futtatókörnyezet
    - Megfelelően alá van írva
    - Nincs hibakeresési módban
    - Ismert forrásból telepítették

- **USB-hibakeresés letiltása az eszközön** *(Android 4,2 vagy újabb)* :

  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Letiltás** – megakadályozza, hogy az eszközök az USB-hibakeresés funkciót használják.

- **Minimális biztonsági javítási szint** *(Android 6,0 vagy újabb)* :

  Válassza ki a legrégebbi biztonsági javítási szintet, amelyet az eszköz tartalmazhat. Az ennél régebbi javítási verzióval rendelkező eszközök nem megfelelőek. A dátumot `YYYY-MM-DD` formátumban kell megadni.

  *Alapértelmezés szerint nincs beállítva dátum*.

- **Korlátozott alkalmazások**:

  Adja meg az **alkalmazás nevét** és az alkalmazáscsomag **azonosítóját** a korlátozni kívánt alkalmazások számára, majd válassza a **Hozzáadás**lehetőséget. A legalább egy telepített korlátozott alkalmazással rendelkező eszközök megjelölése nem megfelelő.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg az androidos vállalati eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-android-for-work.md) .
