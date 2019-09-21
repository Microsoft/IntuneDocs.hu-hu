---
title: Android Enterprise eszközbeállítások a Microsoft Intune – Azure |} A Microsoft Docs
description: Android Enterprise vagy az Android for Work-eszközök korlátozása az eszköz beállításai, többek között másolás és beillesztés, show, értesítések, az Alkalmazásengedélyek, az adatok megosztásához, a jelszó hosszát, a bejelentkezési hibák használata ujjlenyomat a zárolás feloldásához újbóli jelszavak, és a bluetooth engedélyezése a munkahelyi névjegyek megosztása. Az eszközöket dedikált eszközként konfigurálhatja egy alkalmazás vagy több alkalmazás futtatásához.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53a9c3e8b80f611bc9e293ba7e07c1aece0cfc58
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163040"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Android Enterprise eszközbeállítások engedélyezett vagy korlátozott funkciók az Intune-nal

Ez a cikk és az Android Enterprise eszközökön szabályozhatja a különböző beállításokat ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja a funkciók engedélyezéséhez vagy letiltásához, a dedikált eszközökön futó alkalmazások futtatásához, valamint a biztonság szabályozásához.

## <a name="before-you-begin"></a>Előkészületek

[Eszközkonfigurációs profil létrehozása](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Csak az eszköz tulajdonosa

### <a name="general-settings"></a>Általános beállítások

- **Képernyőfelvétel**: A **Letiltás** elemre kattintva megakadályozhatja a képernyőképek vagy képernyőfelvételek készítését az eszközön. Ezen kívül megakadályozza a tartalom megjelenítését a biztonságos videokimenettel nem rendelkező megjelenítő eszközökön. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó képként rögzítse a képernyőn látható tartalmat.
- **Kamera**: Válassza a **Letiltás** lehetőséget a kamera elérésének megakadályozásához az eszközön. **Nem szükséges** engedélyezi a hozzáférést az eszköz kamerájának használatát.
- **Alapértelmezett Engedélyházirend**: Ez a beállítás határozza meg a futásidejű engedélyekre vonatkozó kérelmek alapértelmezett engedélyezési házirendjét. Lehetséges értékei többek között a következők:
  - **Eszköz alapértelmezett értéke**: Használja az eszköz alapértelmezett beállítását.
  - Rákérdezés: A rendszer megkéri a felhasználót, hogy hagyja jóvá az engedélyt.
  - **Automatikus engedélyezés**: Az engedélyek megadása automatikusan megtörténik.
  - **Automatikus megtagadás**: Az engedélyek automatikusan megtagadva.
- **Dátum-és**időváltozások: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók manuálisan állítsa be a dátumot és az időt. **Nincs konfigurálva** lehetővé teszi a felhasználóknak az beállított dátumot és időt az eszközön.
- **Kötet módosításai**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók módosíthassák az eszköz kötetét. **Nincs konfigurálva** lehetővé teszi, hogy a kötet beállításokat az eszközön.
- **Gyári beállítások visszaállítása**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók a gyári beállítások visszaállítása lehetőséget használják az eszköz beállításaiban. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználók számára ez a beállítás használatát az eszközön.
- **Biztonságos rendszerindítás**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók biztonságos módba indítsanak az eszközt. **Nincs konfigurálva** lehetővé teszi a felhasználóknak indítsa újra az eszközt a csökkentett módban.
- **Állapotsor**: A **Letiltás** elemre kattintva megakadályozhatja az állapotsor elérését, beleértve az értesítéseket és a gyors beállításokat is. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználók az állapotsor való hozzáférést.
- **Barangoló**adatszolgáltatások: A **Letiltás** elemre kattintva megakadályozhatja az adatroamingot a mobil hálózaton. **Nincs konfigurálva** engedélyezi az adatroaming használatát, ha az eszköz mobilhálózati.
- **Wi-Fi-beállítások módosításai**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók módosítsák az eszköz tulajdonosa által létrehozott Wi-Fi-beállításokat. Felhasználók saját Wi-Fi-beállításokat hozhat létre. **Nincs konfigurálva** lehetővé teszi a felhasználóknak, hogy a Wi-Fi-beállításokat az eszközön.
- **Wi-Fi hozzáférési pont konfigurációja**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók bármilyen Wi-Fi konfigurációt hozzanak létre vagy módosítsanak. **Nincs konfigurálva** lehetővé teszi a felhasználóknak, hogy a Wi-Fi-beállításokat az eszközön.
- **Bluetooth-konfiguráció**: A **Letiltás** elem kiválasztásával megakadályozhatja a felhasználók számára a Bluetooth konfigurálását az eszközön. **Nincs konfigurálva** lehetővé teszi, hogy az eszköz Bluetooth használatával.
- **Lekötés és hozzáférés a hozzáférési**pontokhoz: A **Letiltás** elemre kattintva megakadályozhatja a lekötést és a hordozható hozzáférési pontokhoz való hozzáférést. **Nincs konfigurálva** -alapú internetmegosztás és hordozható elérési pontokhoz való hozzáférést.
- **USB-tároló**: Válassza az **Engedélyezés lehetőséget** az USB-tároló eléréséhez az eszközön. **Nincs konfigurálva** megakadályozza a USB-tároló.
- **USB-fájlátvitel**: A **Letiltás** elemre kattintva megakadályozhatja a fájlok USB-kapcsolaton keresztüli átvitelét. **Nincs konfigurálva** lehetővé teszi a fájlok átviteléhez.
- **Külső adathordozó**: A **Letiltás** elemre kattintva megakadályozhatja, hogy külső adathordozót használjon vagy csatlakoztasson az eszközön. **Nincs konfigurálva** külső adathordozó engedélyezi az eszközön.
- **Adatsugár az NFC használatával**: A **blokkolás** gombra kattintva megakadályozhatja, hogy a kis hatótávolságú kommunikáció (NFC) technológia használatával az adatok az alkalmazásokból legyenek elválasztva. **Nincs konfigurálva** lehetővé teszi, hogy az NFC segítségével végzett eszközök között adatokat megosztani.
- **Hibakeresési funkciók**: Az **Engedélyezés** lehetőség kiválasztásával engedélyezheti a felhasználóknak a hibakeresési funkciók használatát az eszközön. **Nincs konfigurálva** megakadályozza, hogy a felhasználók a hibakeresési funkciók használata az eszközön.
- **Mikrofon beállítása**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók visszakapcsolják a mikrofont, és beállítsa a mikrofon kötetét. **Nincs konfigurálva** lehetővé teszi a felhasználó használhatja, és állítsa be a mikrofon az eszközön.
- **Gyári beállítások visszaállítása a védelmi e-mailekre**: Válassza ki a **Google-fiók e-mail-címeit**. Adja meg, amely oldhatja fel az eszköz tartalma törlődik, miután eszközadminisztrátorok e-mail címét. Ügyeljen arra, hogy az e-mail-címeket egymástól pontosvesszővel, mint például `admin1@gmail.com;admin2@gmail.com`. Ha egy e-mailt nem adott meg, bárki is az eszköz feloldásához, a gyári beállítások visszaállítása után. Ezek az e-mailek csak akkor érvényesek, ha nem a felhasználó gyári alaphelyzetbe állítását futtatják, például a gyári beállítások visszaállítását a helyreállítási menü használatával.
- **Hálózati Escape-sraffozás**: Az **Engedélyezés** lehetőség kiválasztásával engedélyezheti a felhasználóknak a hálózati Escape-sraffozás funkció bekapcsolását. Ha a hálózati kapcsolat az eszköz nem végzett, majd a vészkijárat kéri ideiglenesen csatlakozzon egy hálózathoz, és frissítenie kell az szabályzat. A szabályzat alkalmazása után a rendszer elfelejti az átmeneti hálózatot, és az eszköz folytatja a rendszerindítást. Ez a funkció eszköz csatlakozik a hálózathoz, ha:
  - Nincs megfelelő hálózati a legutóbbi házirendben.
  - Az eszköz zárolási feladat üzemmódban alkalmazás indul.
  - A felhasználó nem tudja elérni az Eszközbeállítások között.

  **Nincs konfigurálva** megakadályozza, hogy a felhasználók ne tudják bekapcsolni a a hálózat escape csíkozási funkciót az eszközön.

- **Rendszerfrissítés**: Válassza ki azt a lehetőséget, amely meghatározza, hogy az eszköz hogyan kezelje a csatornákon kívüli frissítéseket:
  - **Eszköz alapértelmezett értéke**: Használja az eszköz alapértelmezett beállítását.
  - **Automatikus**: A frissítések felhasználói beavatkozás nélkül automatikusan települnek. Ennek a szabályzatnak a beállításakor minden függőben lévő frissítés azonnal települ.
  - **Elhalasztva**: A frissítések 30 napig Elhalasztva vannak. A 30 nap végén Android kéri a felhasználót, hogy a frissítés telepítéséhez. Az eszközgyártók vagy a szolgáltatók megakadályozhatják (kivételként) a fontos biztonsági frissítések elhalasztását. A kivételként kezelt frissítések rendszerértesítést jelenítenek meg a felhasználó számára az eszközön. 
  - **Karbantartási**időszak: Automatikusan telepíti a frissítéseket az Intune-ban beállított napi karbantartási időszak során. Telepítés megkísérli naponta 30 napig, és meghiúsulhat, ha nincs elegendő terület vagy akkumulátor szintjét. A 30 nap elteltével Android kéri a felhasználót, hogy telepítse. Ez az időszak szolgál a Play-alkalmazások frissítéseinek telepítésére is. Ezt a lehetőséget olyan dedikált eszközökhöz használhatja, mint például a kioszkok, az Egyalkalmazásos dedikált eszköz előtérben lévő alkalmazások is frissíthetők.

- **Értesítési ablakok**: Ha a **Letiltás**értékre van állítva, a rendszer nem jeleníti meg az eszközön az ablakos értesítéseket, például a pirítóst, a bejövő hívásokat, a kimenő hívásokat, a rendszerriasztásokat és a rendszerhibák Ha a **nincs konfigurálva**értékre van állítva, a rendszer az operációs rendszer alapértelmezett beállításait használja, ami lehet, hogy az értesítéseket jeleníti meg.
- **Első használati útmutatók**kihagyása: Az **enable (Engedélyezés** ) gombra kattintva elrejtheti vagy kihagyhatja az alkalmazások javaslatait, és megtekintheti az oktatóanyagokat, illetve bevezető javaslatokat olvashat az alkalmazás indításakor. Ha a **nincs konfigurálva**értékre van állítva, a rendszer az operációs rendszer alapértelmezett beállításait használja, amely az alkalmazás indításakor a javaslatok megjelenítéséhez vezethet.

### <a name="system-security-settings"></a>A rendszer biztonsági beállításai

- **Veszélyforrások vizsgálata az alkalmazásokban**: **Szükséges** (alapértelmezés) lehetővé teszi, hogy a Google Play Protect alkalmazás a telepítés előtt és után ellenőrizze az alkalmazásokat. Ha fenyegetést észlel, figyelmeztetheti a felhasználót, hogy távolítsa el az alkalmazást az eszközről. A **nincs konfigurálva beállítás** nem engedélyezi vagy nem futtatja a Google Play Protect alkalmazást az alkalmazások vizsgálatához.

### <a name="dedicated-device-settings"></a>Dedikált eszközbeállítások

Ezekkel a beállításokkal konfigurálhatja a dedikált eszközökön a kioszk stílusú élményt. Beállíthat egy eszközt egy alkalmazás futtatásához vagy számos alkalmazás futtatásához. Ha egy eszköz kioszk módban van beállítva, csak a hozzáadott alkalmazások érhetők el. Ezek a beállítások az Android Enterprise dedikált eszközökre vonatkoznak. Nem vonatkoznak az Android Enterprise teljes körűen felügyelt eszközeire.

Teljes **képernyős mód**: Válassza ki, hogy az eszköz futtat-e egy alkalmazást, vagy több alkalmazást futtat.

- **Egyetlen alkalmazás**: A felhasználók csak egyetlen alkalmazást tudnak elérni az eszközön. Amikor az eszköz elindul, csak az adott alkalmazás elindul. A felhasználók nem nyithatnak meg új alkalmazásokat, és nem módosíthatják a futó alkalmazást.

  - **Felügyelt alkalmazás kiválasztása**: Válassza ki a felügyelt Google Play alkalmazást a listából.

    Ha nem rendelkezik az összes alkalmazás szerepel a listában, majd [bizonyos Android-alkalmazások hozzáadása](apps-add-android-for-work.md) az eszközön. Ügyeljen arra, hogy [az alkalmazást a dedikált eszközökhöz létrehozott eszközcsoport](apps-deploy.md)számára társítsa.

  > [!IMPORTANT]
  > Egyalkalmazásos kioszk mód használata esetén előfordulhat, hogy a tárcsázó/telefonos alkalmazások nem működnek megfelelően. 
  
- **Több alkalmazás**: A felhasználók korlátozott számú alkalmazást tudnak elérni az eszközön. Amikor az eszköz elindul, csak a hozzáadott alkalmazások indítsa el. Bizonyos webes hivatkozások, amelyek a felhasználó meg tudja nyitni is hozzáadhat. A házirend van érvényben, amikor megjelenik a felhasználók számára az engedélyezett alkalmazások ikonjai a kezdőképernyőn.

  > [!IMPORTANT]
  > A többalkalmazásos dedikált eszközök esetében a Google Play által [kezelt kezdőképernyő alkalmazásnak](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) a következőknek **kell lennie**:
  >   - [Egy ügyfélalkalmazás hozzáadott](apps-add-android-for-work.md) az Intune-ban
  >   - [Hozzárendelve a](apps-deploy.md) dedikált eszközökhöz létrehozott eszközcsoport számára
  > 
  > A **kezdőlap képernyő felügyelt** alkalmazás nem található a konfigurációs profil feltétlenül szükséges, de ügyfélalkalmazásként hozzá kell adni. Ha a **felügyelt kezdőképernyő** alkalmazást ügyfél-alkalmazásként adja hozzá, a konfigurációs profilban hozzáadott más alkalmazások ikonként jelennek meg a felügyelt **kezdőképernyő** alkalmazásban. 
  >
  > Többalkalmazásos kioszk mód használata esetén előfordulhat, hogy a tárcsázó/telefonos alkalmazások nem működnek megfelelően. 

  - **Hozzáadás**: Válassza ki az alkalmazásokat a listából.

    Ha a **kezdőlap képernyő felügyelt** alkalmazás nem szerepel a listán, majd [adja hozzá a Google Play áruházból](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Ügyeljen arra, hogy [az alkalmazást](apps-deploy.md) a dedikált eszközökhöz létrehozott eszközcsoport számára társítsa.

    Is hozzáadhat más [Android-alkalmazások](apps-add-android-for-work.md) és [webes alkalmazások](web-app.md) hozta létre a szervezet az eszköz számára. Ügyeljen arra, hogy [az alkalmazást a dedikált eszközökhöz létrehozott eszközcsoport](apps-deploy.md)számára társítsa.

  - **Virtuális otthoni gomb**: Egy Soft-Key gomb, amely a felhasználókat a felügyelt kezdőképernyő számára adja vissza, így a felhasználók válthatnak az alkalmazások között. A választható lehetőségek:

    - **Nincs konfigurálva** (alapértelmezett): A Kezdőlap gomb nem jelenik meg. Az alkalmazások közötti váltáshoz a felhasználóknak a vissza gombot kell használniuk.
    - **Elcsúsztatás**: A Kezdőlap gomb azt jeleníti meg, hogy a felhasználó mikor kerül be az eszközre.
    - **Lebegő**: Egy állandó, lebegő Kezdőlap gomb megjelenítése az eszközön.

  - A **kioszk mód**kihagyása: Az **Engedélyezés** lehetőség kiválasztásával engedélyezheti, hogy a rendszergazdák ideiglenesen szüneteltetik a kioszk módot az eszköz frissítéséhez. A szolgáltatás használatához a rendszergazda:
  
    1. Továbbra is kijelöli a vissza gombot, amíg meg nem jelenik a **kilépési kioszk** gomb. 
    2. Kiválasztja a **kilépési kioszk** gombot, és belép a teljes **képernyős mód kód PIN-kódjába** .
    3. Ha elkészült, válassza a **felügyelt kezdőképernyő** alkalmazást. Ez a lépés az eszköz relocks többalkalmazásos kioszk módba.

      Ha a **nincs konfigurálva**értékre van állítva, a rendszergazdák nem tudják szüneteltetni a kioszk üzemmódot. Ha a rendszergazda továbbra is kiválasztja a vissza gombot, és kiválasztja a **kilépési kioszk** gombot, akkor egy üzenet jelzi, hogy PIN-kódot kell megadnia.

    - A **kioszk mód kódjának**kihagyása: Adjon meg egy 4-6 számjegyű numerikus PIN-kódot. A rendszergazda ideiglenesen letilthatja a teljes képernyős mód a PIN-kódot használja.

  - **Egyéni URL-cím beállításának beállítása**: Adjon meg egy URL-címet, amely testreszabja a háttér képernyőt a dedikált eszközön.

    > [!NOTE]
    > A legtöbb esetben azt javasoljuk, hogy legalább a következő méretű képekkel kezdjen el:
    >
    > - Phone 1080x1920 px
    > - Tabletta 1920 × 1080 px
    >
    > A legjobb élmény és a ropogós részletek tekintetében azt javasoljuk, hogy eszközönként a megjelenítési specifikációk alapján hozzon létre egy eszközön rendszerkép-eszközöket.
    >
    > A modern kijelzők nagyobb képpontokkal rendelkeznek, és megfelelő 2K/4K definíciós képeket tudnak megjeleníteni.

  - **Wi-Fi-konfiguráció**: Az **Engedélyezés** megjeleníti a Wi-Fi vezérlőelemet a felügyelt kezdőképernyőn, és lehetővé teszi a végfelhasználók számára az eszköz csatlakoztatását a különböző WiFi-hálózatokhoz. A funkció engedélyezése az eszköz helyét is bekapcsolja. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a Wi-Fi vezérlőelemet a felügyelt kezdőképernyő képernyőjén. Megakadályozza, hogy a felhasználók a felügyelt kezdőképernyő használatával csatlakozzanak a Wi-Fi-hálózatokhoz.

  - **Bluetooth-konfiguráció**: Az **Engedélyezés** megjeleníti a felügyelt kezdőképernyő Bluetooth-vezérlését, és lehetővé teszi a végfelhasználók számára az eszközök párosítását a Bluetooth-on keresztül. A funkció engedélyezése az eszköz helyét is bekapcsolja. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a Bluetooth-vezérlést a felügyelt kezdőképernyő képernyőjén. Megakadályozza, hogy a felhasználók a felügyelt kezdőképernyő használata közben a Bluetooth és a párosítási eszközöket konfigurálja.

  - **Zseblámpa-hozzáférés**: Az **Engedélyezés** megjeleníti a zseblámpa vezérlőelemet a felügyelt kezdőképernyőn, és lehetővé teszi a végfelhasználók számára a zseblámpa be-vagy kikapcsolását. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a zseblámpa vezérlőelemet a felügyelt kezdőképernyő képernyőjén. Ez megakadályozza a felhasználók számára a zseblámpa használatát a felügyelt kezdőképernyő használata közben.

  - **Adathordozó-kötet vezérlőelem**: Az **Engedélyezés** beállítás megjeleníti a Media Volume Control eszközt a felügyelt kezdőlapon, és lehetővé teszi a végfelhasználók számára, hogy a csúszka segítségével módosítsák az eszköz adathordozó-kötetét. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a Media Volume Control szolgáltatást a felügyelt kezdőképernyőn. Ez megakadályozza, hogy a felhasználók a felügyelt kezdőképernyő használata közben módosítsák az eszköz adathordozó-kötetét, kivéve, ha a hardveres gombok támogatják azt. 

  - **Képernyővédő mód**: Az **Engedélyezés** megjeleníti a képernyővédőt a felügyelt kezdőképernyőn, ha az eszköz zárolva van vagy időtúllépés miatt megtörténik. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a képernyővédőt a felügyelt kezdőképernyőn.

    Ha engedélyezve van, konfigurálja a következőket is:

    - **Egyéni képernyőkímélő rendszerképének beállítása**: Adja meg az egyéni rendszerkép URL-címét. Írja be például a következőt:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.html`

      Ha nem ad meg URL-címet, a rendszer az eszköz alapértelmezett képét használja, ha van alapértelmezett rendszerkép.

    - **Azon másodpercek száma, ameddig az eszköz képernyőkímélőt mutat a képernyő kikapcsolása előtt**: Válassza ki, hogy az eszköz mennyi ideig jelenítse meg a képernyővédőt. 0-9999999 másodperc közötti értéket adjon meg. Az `0` alapértelmezett érték másodperc. Ha üresen hagyja, vagy nulla (`0`) értékre van állítva, a képernyőkímélő aktív, amíg a felhasználó nem kommunikál az eszközzel.
    - **Azon másodpercek száma, ameddig az eszköz inaktív a képernyőkímélő megjelenítése előtt**: Válassza ki, hogy az eszköz mennyi ideig tétlen a képernyővédő megjelenítése előtt. 1-9999999 másodperc közötti értéket adjon meg. Az `30` alapértelmezett érték másodperc. Nullánál (`0`) nagyobb számot kell megadnia.
    - **Adathordozó észlelése a képernyőkímélő elindítása előtt**: **Engedélyezés** (alapértelmezés) nem jeleníti meg a képernyőkímélőt, ha a hang vagy a videó lejátszása az eszközön történik. A **nincs konfigurálva beállítás** megjeleníti a képernyőkímélőt, még akkor is, ha a hang vagy a videó lejátszása megtörténik.

### <a name="device-password-settings"></a>Eszköz jelszóbeállításai

- **Zárolási képernyő letiltása**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók a billentyûzár zárolási képernyőjének funkcióját használják az eszközön. **Nincs konfigurálva** lehetővé teszi a felhasználó Keyguard funkcióinak használatát.
- A **zárolási képernyő funkcióinak letiltása**: Ha a billentyűzár engedélyezve van az eszközön, válassza ki a letiltani kívánt szolgáltatásokat. Ha például a **biztonságos kamera** be van jelölve, a kamera funkció le van tiltva az eszközön. A nem ellenőrzött funkciók engedélyezve vannak az eszközön.

  Ezek a funkciók a felhasználók számára érhetők el, ha az eszköz zárolva van. A felhasználók nem látják és nem férnek hozzá a bejelölt szolgáltatásokhoz.

- **Szükséges jelszó típusa**: Az eszközhöz szükséges jelszó típusának megadása. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Jelszó szükséges, nincs korlátozás**
  - **Gyenge biometrikus**: [Erős vagy gyenge biometria](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (az Android webhely megnyitása)
  - **Numerikus**: A `123456789`jelszó csak számok, például:. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
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

- **A jelszó lejárati ideje (nap**): Adja meg a napok számát 1-365 között, amíg meg nem változtatja az eszköz jelszavát. Ha például a 60 nap után szeretné módosítani a jelszót, írja `60`be a következőt:. A jelszó lejáratakor a rendszer a felhasználókat új jelszó létrehozására kéri.
- **Jelszó megadásához szükséges jelszavak száma**: Adja meg a legutóbbi olyan jelszavak számát, amelyeket nem lehet újra felhasználni 1-24 között. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.
- **Sikertelen bejelentkezések száma az eszköz törlése előtt**: Adja meg a sikertelen bejelentkezések 4-11 közötti számát az eszköz törlésének engedélyezése előtt.

### <a name="power-settings"></a>Energiaellátási beállítások

- **Zárolási idő**: Állítsa be az eszköz zárolása előtti üresjárati idő mennyiségét.
- **Képernyő az eszköz csatlakoztatása közben**: Válassza ki, hogy mely áramforrások okozzák az eszköz képernyőjét a csatlakoztatásakor.

### <a name="users-and-accounts-settings"></a>Felhasználói és fiókbeállítások

- **Új felhasználók hozzáadása**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók új felhasználókat adjanak hozzá. Minden felhasználó rendelkezik személyes munkaterülettel az eszközön az egyéni kezdőlap képernyők, fiókok, alkalmazások és beállítások. **Nincs konfigurálva** lehetővé teszi a felhasználóknak más felhasználók felvétele az eszközre.
- **Felhasználó eltávolítása**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók eltávolítsanak felhasználókat. **Nincs konfigurálva** lehetővé teszi a felhasználóknak más felhasználók eltávolítása az eszközről.
- **Fiók módosításai**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók módosíthassák a fiókokat. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználók frissíthetik a felhasználói fiókokat az eszközön.

  > [!NOTE]
  > Ez a beállítás nem felel meg az eszköz tulajdonosának (teljes mértékben felügyelt) eszközeinek. Ha ezt a beállítást konfigurálja, a rendszer figyelmen kívül hagyja a beállítást, és nincs hatással.

### <a name="applications"></a>Alkalmazások

- **Ismeretlen forrásból történő telepítés engedélyezése**: Válassza az **Engedélyezés lehetőséget** , hogy a felhasználók be tudják kapcsolni az **ismeretlen forrásokat**. Ez a beállítás lehetővé teszi, hogy az alkalmazások ismeretlen forrásokból telepítsenek, beleértve a Google Play Áruházon kívüli forrásokat is. **Nincs konfigurálva** megakadályozza, hogy a felhasználók ne tudják bekapcsolni a **ismeretlen források**.
- **Hozzáférés engedélyezése a Google Play áruházban lévő összes alkalmazáshoz**: Az **Engedélyezés**beállítás megadása esetén a felhasználók hozzáférhetnek a Google Play áruházban lévő összes alkalmazáshoz. Nem férhetnek hozzá az alkalmazásokhoz az [ügyfélalkalmazások](apps-add-android-for-work.md)rendszergazdai blokkja. **Nincs konfigurálva** , hogy a felhasználók csak az alkalmazásokhoz férhessenek hozzá, a rendszergazda elérhetővé teszi a Google Play áruházat vagy az [ügyfélalkalmazások](apps-add-android-for-work.md)számára szükséges alkalmazásokat.
- **Alkalmazás automatikus frissítései**: Válassza ki az automatikus frissítések telepítését. A választható lehetőségek:
  - **Nincs konfigurálva**
  - **Felhasználói választási lehetőség**
  - **Soha nem**
  - **Wi-Fi csak**
  - **Mindig**

### <a name="connectivity"></a>Kapcsolat

- **Always-On VPN**: Az **Engedélyezés** beállítás megadásával beállíthatja, hogy a VPN-ügyfél automatikusan kapcsolódjon a VPN-hez, és kapcsolódjon újra. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal elindítható, ha a felhasználó zárolja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. 

  A mindig bekapcsolt VPN beállítás az összes VPN-ügyfél számára való letiltásához válassza a **Nincs konfigurálva** lehetőséget.

  > [!IMPORTANT]
  > Egy eszközön egyszerre csak egy mindig bekapcsolt VPN-szabályzatot helyezzen üzembe. Több ilyen szabályzat üzembe helyezése egyetlen eszközön nem támogatott.

- **VPN-ügyfél**: Válassza ki az Always on szolgáltatást támogató VPN-ügyfelet. A választható lehetőségek:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Hálózatok GlobalProtect
  - Pulse Secure
  - Egyéni
    - **Csomag azonosítója**: Adja meg az alkalmazás csomag-AZONOSÍTÓját a Google Play áruházban. Ha például az áruházban levő alkalmazás URL-címe `https://play.google.com/store/details?id=com.contosovpn.android.prod`, a csomagazonosító `com.contosovpn.android.prod` lesz.

  > [!IMPORTANT]
  > - A kiválasztott VPN-ügyfelet az eszközön kell telepíteni, és támogatnia kell az alkalmazásonkénti VPN-t a munkahelyi profilokban. Ellenkező esetben hiba történik. 
  > - A VPN-ügyfélalkalmazást jóvá kell hagynia a **felügyelt Google Play Áruházban**, szinkronizálnia kell az alkalmazást az Intune-nal, majd üzembe helyeznie az eszközön. Ezt követően az alkalmazás telepítve lesz a felhasználó munkahelyi profiljában.
  > - Van Előfordulhat, hogy ismert problémák alkalmazásonkénti VPN az Android 3.0.4 F5 hozzáféréssel rendelkező használatakor. Lásd: [F5 kibocsátási megjegyzések az F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) további információt.

- **Zárolási mód**: Válassza az **Engedélyezés** lehetőséget az összes hálózati forgalom kényszerítéséhez a VPN-alagút használatára. Ha a VPN-kapcsolat nincs kiépítve, az eszköznek nem lesz hálózati hozzáférése.

  A **Nincs konfigurálva** beállítással a forgalom a VPN-alagúton vagy a mobilhálózaton is áthaladhat.

## <a name="work-profile-only"></a>Csak munkahelyi profil 

### <a name="work-profile-settings"></a>Munkahelyi profil beállításai

#### <a name="general"></a>Általános

- **Másolás és beillesztés a munkahelyi és a személyes profilok között**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja a munkahelyi és a személyes alkalmazások közötti másolást és beillesztést. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználók megoszthassák az adatokat a személyes profilban szereplő alkalmazások használata a másolás és beillesztés 
- **A munkahelyi és a személyes profilok közötti adatmegosztás**: Válassza ki, hogy a munkahelyi profilban szereplő alkalmazások megoszthatnak-e az alkalmazásokkal a személyes profilban. Például szabályozhatja megosztási műveletek alkalmazásokban, mint például a **megosztás...** lehetőséget a Chrome böngészőalkalmazásban). Ez a beállítás nem vonatkozik a másolás/beillesztés vágólapi viselkedésre. A megosztási beállítások:
  - **Alapértelmezett megosztási korlátozások**: Az eszköz alapértelmezett megosztási viselkedése, amely az Android-verziótól függően változhat. Alapértelmezés szerint a személyes profilból lehet a munkahelyi profilba adatokat megosztani, a munkahelyiből a személyesbe viszont nem. A beállítás célja a munkahelyi profilból a személyesbe irányuló adatmegosztás megelőzése. A Google a 6.0-snál újabb verziójú eszközökön nem nyújt lehetőséget a személyesből a munkahelyi profilba irányuló adatmegosztás blokkolására.
  - **A munkahelyi profilban lévő alkalmazások kezelhetik a személyes profilból érkező megosztási kéréseket**: Engedélyezi a beépített Android-funkciót, amely lehetővé teszi a személyes és a munkahelyi profil közötti megosztást. Engedélyezéskor a személyes profil alkalmazásaiból származó megosztási kérések kezdeményezhetnek adatmegosztást a munkahelyi profil alkalmazásaival. A 6.0-snál korábbi verziójú androidos eszközökön ez az alapértelmezett beállítás.
  - **Határokon keresztüli megosztás engedélyezése**: Lehetővé teszi a munkahelyi profil határán belüli megosztást mindkét irányban. Ilyenkor a munkahelyi profilban szereplő alkalmazások megoszthatnak adatokat a személyes profi jelöletlen alkalmazásaival. A beállítással lehetővé teszi a munkahelyi profil alkalmazásainak az adatmegosztást az eszköz nem felügyelt részével. Így körültekintően használja ezt a lehetőséget.

- **Munkahelyi profil értesítései az eszköz zárolt állapotában**: Azt szabályozza, hogy a munkahelyi profilban szereplő alkalmazások megjeleníthetnek-e értesítéseket az eszköz zárolt állapotában. **Blokk** nem jelenik meg az adatokat. **Nincs konfigurálva** adatokat mutatja.
- **Alapértelmezett alkalmazás engedélyei**: Meghatározza a munkahelyi profilban található összes alkalmazásra vonatkozó alapértelmezett szabályzatot. Az Android 6-os verziójától kezdve a rendszer alkalmazásindításkor felszólítja a felhasználót az alkalmazás által megkövetelt, konkrét engedélyek megadására. Ezzel a szabályzatbeállítással döntheti el, hogy a felhasználók megadhatják-e a munkahelyi profilban szereplő összes alkalmazás engedélyeit. Hozzárendelhet például egy olyan alkalmazást a munkahelyi profilhoz, amely helyadatokhoz kér hozzáférést. Általában az alkalmazás kéri a felhasználót a helyadatokhoz való hozzáférés megadására vagy elutasítására. Ezzel a szabályzattal kérdés nélkül automatikusan engedélyezhet vagy letilthat minden hozzáférést, vagy átadhatja a döntés jogát a felhasználónak. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Rákérdezés**
  - **Automatikus engedélyezés**
  - **Automatikus elutasítás**

  Alkalmazáskonfigurációs szabályzatokkal is engedélyeket adhat egyes alkalmazásoknak (**Ügyfélalkalmazások** > **Alkalmazáskonfigurációs szabályzatok**).

- **Fiókok hozzáadása és eltávolítása**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a végfelhasználók manuálisan adjanak hozzá vagy távolítanak el fiókokat a munkahelyi profilban. Ha például a Gmail alkalmazást androidos munkahelyi profilban telepíti, megakadályozhatja, hogy a végfelhasználók fiókokat adjanak hozzá vagy távolítsanak el ebben a munkaprofilban. **Nincs konfigurálva** lehetővé teszi, hogy a munkahelyi profilban található fiókok hozzáadásának.  

- **Névjegyek megosztása Bluetooth-kapcsolaton keresztül**: Lehetővé teszi a munkahelyi kapcsolatok elérését egy másik eszközről, például egy, Bluetooth-kapcsolattal rendelkező eszközről. Alapértelmezés szerint ez a beállítás nincs konfigurálva, a munkahelyi névjegyek pedig nem jelennek meg. A megosztás engedélyezéséhez és a munkahelyi profil névjegyeinek megjelenítéséhez válassza az **Engedélyezés** lehetőséget. Ez a beállítás az Android munkahelyi profilos, Android v6.0 és újabb operációs rendszerekkel rendelkező eszközökre vonatkozik. A beállítás engedélyezésével megengedheti bizonyos Bluetooth-eszközöknek, hogy az első kapcsolat alkalmával gyorsítótárazzák a munkahelyi kapcsolatokat. Ennek a szabályzatnak az eredeti párosítás/szinkronizálás utáni letiltása nem feltétlenül távolítja el a munkahelyi kapcsolatokat a Bluetooth-eszközről.

- **Képernyőfelvétel**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a képernyőképek vagy képernyőfelvételek az eszközön legyenek a munkahelyi profilban. Ezen kívül megakadályozza a tartalom megjelenítését a biztonságos videokimenettel nem rendelkező megjelenítő eszközökön. **Nincs konfigurálva** lehetővé teszi, hogy a képernyőképek beolvasása.

- **Munkahelyi kapcsolattartási hívó azonosítójának megjelenítése a személyes profilban**: Ha engedélyezve van (**nincs konfigurálva**), a munkahelyi kapcsolat hívójának adatai megjelennek a személyes profilban. Ha a beállítása **blokk**, a munkahelyi hívó nem jelenik meg a személyes profilban. Az Android operációs rendszer 6.0-ás és újabb verzióira vonatkozik.

- **Munkahelyi Névjegyek keresése a személyes profilból**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók munkahelyi névjegyeket keressenek a személyes profilban található alkalmazásokban. **Nem szükséges** lehetővé teszi, hogy a személyes profilban munkahelyi névjegyek keresése.

- **Kamera**: A **blokkolás** gombra kattintva megakadályozhatja, hogy a munkahelyi profilban lévő eszközön hozzáférhessen a kamerához. A beállítás nincs hatással a fényképezőkép személyes profilban való használatára. **Nem szükséges** a kamerához való hozzáférés lehetővé teszi a munkahelyi profil.

- **Widgetek munkahelyi profilbeli alkalmazásokból való engedélyezése**: Az **Engedélyezés** beállítás lehetővé teszi a végfelhasználók számára, hogy a kezdőképernyő alkalmazásai által elérhetővé tegyék a widgeteket. A **Nincs konfigurálva** (alapértelmezett) érték letiltja a funkciót.

  Az Outlook például a felhasználók munkahelyi profiljaira van telepítve. Az **Engedélyezés**beállítás megadása esetén a felhasználók az eszköz kezdőlapjára helyezhetik el a napirend widgetet.

#### <a name="work-profile-password"></a>Munkahelyi profilhoz tartozó jelszó

- **Munkahelyi profil jelszavának**megkövetelése: Az Android 7,0-es vagy újabb verziójára vonatkozik a munkahelyi profillal engedélyezve. Válasszon **megkövetelése** megadnia a PIN-kód-szabályzatot, amely csak a munkahelyi profilban szereplő alkalmazások vonatkozik. Alapértelmezés szerint a végfelhasználónak lehetősége van két külön-külön definiált PIN-kód használatára, vagy a felhasználók dönthetnek úgy, hogy a két meghatározott PIN-kód összevonásával csak az erősebbet használják. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó használja a munkahelyi alkalmazásokat, anélkül, hogy jelszót írna be.
- **Jelszó minimális hossza**: Adja meg a felhasználók jelszavában szereplő karakterek minimális számát ( **4**-**16**).
- **A munkahelyi profil zárolása legfeljebb ennyi perc inaktivitás**után: Válassza ki azt az időtartamot, ameddig a munkahelyi profil zárolva van. A felhasználónak ezután meg kell adnia a hitelesítő adatait a hozzáférés visszanyeréséhez.
- **Sikertelen bejelentkezések száma az eszköz törlése előtt**: Adja meg, hogy hányszor lehet helytelen jelszót beírni, mielőtt a rendszer törli a munkahelyi profilt az eszközről.
- **Jelszó érvényessége (napokban)** : Adja meg, hogy hány nap elteltével kell módosítani a végfelhasználó jelszavát ( **1**-**255**).
- **Szükséges jelszó típusa**: Válassza ki a jelszó típusát, amelyet be kell állítani az eszközön. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Kötelező**
  - **Legalább számok**
  - **Komplex numerikus**: Ismétlődő vagy egymást követő számok, például "1111" vagy "1234" nem engedélyezettek
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Adja meg, hogy hány új jelszót kell használni a régi jelszó újbóli felhasználása előtt ( **1**-**24**).
- **Ujjlenyomat feloldása**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a végfelhasználók az eszköz ujjlenyomat-olvasóját használják a zárolás feloldásához. **Nincs konfigurálva** lehetővé teszi a felhasználók a munkahelyi profilban szereplő ujjlenyomat a zárolás feloldásához.
- **Smart Lock és más megbízhatósági ügynökök**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy Smart lock vagy más megbízhatósági ügynökök a kompatibilis eszközökön módosítsák a zárolási képernyő beállításait. Ez a funkció, más néven bizalmi ügynök lehetővé teszi, hogy letiltását vagy megkerülését az eszköz zárolási képernyője jelszavának, ha az eszköz megbízható helyen van. Így például megkerülheti a munkahelyi profil jelszavát abban az esetben, ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címke közelében van. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.

### <a name="device-password"></a>Eszköz jelszava

A jelszó-beállításokat alkalmazni a munkahelyi profilt használó eszközök személyes profilok.

- **Jelszó minimális hossza**: Adja meg a felhasználók jelszavában szereplő karakterek minimális számát ( **4**-**14**).
- **A képernyőfelvételek legfeljebb ennyi perc inaktivitás**után: Válassza ki azt az időtartamot, ameddig egy inaktív eszköz automatikusan zárolja
- **Sikertelen bejelentkezések száma az eszköz törlése előtt**: Adja meg, hogy hányszor lehet helytelen jelszót beírni, mielőtt az összes adat törlődik az eszközről.
- **Jelszó érvényessége (napokban)** : Adja meg, hogy hány nap elteltével kell módosítani a végfelhasználói jelszót ( **1**-**255**)
- **Szükséges jelszó típusa**: Válassza ki a jelszó típusát, amelyet be kell állítani az eszközön. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Kötelező**
  - **Legalább számok**
  - **Komplex numerikus**: Ismétlődő vagy egymást követő számok, például "1111" vagy "1234" nem engedélyezettek
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Adja meg, hogy hány új jelszót kell használni a régi jelszó újbóli felhasználása előtt ( **1**-**24**).
- **Ujjlenyomat feloldása**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a végfelhasználó az eszköz ujjlenyomat-olvasójának használatával feloldja az eszközt. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó számára az eszközzárolás ujjlenyomattal történő használatával.
- **Smart Lock és más megbízhatósági ügynökök**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy Smart lock vagy más megbízhatósági ügynökök a kompatibilis eszközökön módosítsák a zárolási képernyő beállításait. Ez a funkció, más néven bizalmi ügynök lehetővé teszi, hogy letiltását vagy megkerülését az eszköz zárolási képernyője jelszavának, ha az eszköz megbízható helyen van. Így például megkerülheti a munkahelyi profil jelszavát abban az esetben, ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címke közelében van. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.

### <a name="system-security"></a>Rendszerbiztonság

- **Veszélyforrások vizsgálata az alkalmazásokban**: **Kötelezővé teszi** , hogy az **alkalmazások ellenőrzése** beállítás engedélyezve legyen a munkahelyi és a személyes profilokhoz.

   > [!Note]
   > Ez a beállítás csak Android O vagy újabb rendszerű eszközök esetén érvényesül.

### <a name="connectivity"></a>Kapcsolat

- **Always-On VPN**: Az **Engedélyezés** beállítás megadásával beállíthatja, hogy a VPN-ügyfél automatikusan kapcsolódjon a VPN-hez, és kapcsolódjon újra. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal elindítható, ha a felhasználó zárolja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. 

  A mindig bekapcsolt VPN beállítás az összes VPN-ügyfél számára való letiltásához válassza a **Nincs konfigurálva** lehetőséget.

  > [!IMPORTANT]
  > Egy eszközön egyszerre csak egy mindig bekapcsolt VPN-szabályzatot helyezzen üzembe. Több ilyen szabályzat üzembe helyezése egyetlen eszközön nem támogatott.

- **VPN-ügyfél**: Válassza ki az Always on szolgáltatást támogató VPN-ügyfelet. A választható lehetőségek:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Hálózatok GlobalProtect
  - Pulse Secure
  - Egyéni
    - **Csomag azonosítója**: Adja meg az alkalmazás csomag-AZONOSÍTÓját a Google Play áruházban. Ha például az áruházban levő alkalmazás URL-címe `https://play.google.com/store/details?id=com.contosovpn.android.prod`, a csomagazonosító `com.contosovpn.android.prod` lesz.

  > [!IMPORTANT]
  > - A kiválasztott VPN-ügyfelet az eszközön kell telepíteni, és támogatnia kell az alkalmazásonkénti VPN-t a munkahelyi profilokban. Ellenkező esetben hiba történik. 
  > - A VPN-ügyfélalkalmazást jóvá kell hagynia a **felügyelt Google Play Áruházban**, szinkronizálnia kell az alkalmazást az Intune-nal, majd üzembe helyeznie az eszközön. Ezt követően az alkalmazás telepítve lesz a felhasználó munkahelyi profiljában.
  > - Van Előfordulhat, hogy ismert problémák alkalmazásonkénti VPN az Android 3.0.4 F5 hozzáféréssel rendelkező használatakor. Lásd: [F5 kibocsátási megjegyzések az F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) további információt.

- **Zárolási mód**: Válassza az **Engedélyezés** lehetőséget az összes hálózati forgalom kényszerítéséhez a VPN-alagút használatára. Ha a VPN-kapcsolat nincs kiépítve, az eszköznek nem lesz hálózati hozzáférése.

  A **Nincs konfigurálva** beállítással a forgalom a VPN-alagúton vagy a mobilhálózaton is áthaladhat.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az [Android](device-restrictions-android.md#kiosk) és a [Windows 10 rendszerű](kiosk-settings.md) eszközökhöz is létrehozhat dedikált eszközök kioszk-profilokat.

## <a name="see-also"></a>Lásd még:

[Androidos vállalati eszközök konfigurálása és hibaelhárítása Microsoft Intune](https://support.microsoft.com/help/4476974)
