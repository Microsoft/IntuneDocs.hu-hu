---
title: Az Android vállalati eszközbeállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Az Android Enterprise vagy Android for Work-eszközökön korlátozza az eszköz beállításait, beleértve a másolást és beillesztést, az értesítések megjelenítését, az alkalmazás engedélyeinek megadását, az adatmegosztást, a jelszó hosszát, a bejelentkezési hibákat, az ujjlenyomat feloldását, a jelszavak újrafelhasználását és a Bluetooth használatát munkahelyi névjegyek megosztása. Az eszközöket dedikált eszközként konfigurálhatja egy alkalmazás vagy több alkalmazás futtatásához.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d1d83a77d8823a05accaf1c88b57f6e380636469
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585384"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Az androidos vállalati eszközbeállítások az Intune-t használó szolgáltatások engedélyezéséhez vagy korlátozásához

Ez a cikk felsorolja és leírja az androidos vállalati eszközökön szabályozható különböző beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja a funkciók engedélyezéséhez vagy letiltásához, a dedikált eszközökön futó alkalmazások futtatásához, valamint a biztonság szabályozásához.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Csak az eszköz tulajdonosa

### <a name="general-settings"></a>Általános beállítások

- **Képernyőfelvétel**: a **Letiltás** elem kiválasztásával megakadályozhatja a képernyőképek vagy képernyőfelvételek készítését az eszközön. Ezen kívül megakadályozza a tartalom megjelenítését a biztonságos videokimenettel nem rendelkező megjelenítő eszközökön. **Nincs konfigurálva** , lehetővé teszi a felhasználó számára, hogy képként rögzítse a képernyő tartalmát.
- **Kamera**: válassza a **Letiltás** lehetőséget a kamera elérésének megakadályozásához az eszközön. A **nem kötelezően** engedélyezi az eszköz kamerájának elérését.
- **Alapértelmezett engedélyezési szabályzat**: Ez a beállítás adja meg a futásidejű engedélykérésekre vonatkozó alapértelmezett engedélyezési szabályzatot. Lehetséges értékei többek között a következők:
  - **Eszköz alapértelmezése**: Az eszköz alapértelmezett beállításának használata.
  - **Rákérdezés**: A rendszer felszólítja a felhasználót az engedély jóváhagyására.
  - **Automatikus engedélyezés**: Az engedélyek automatikusan meg lesznek adva.
  - **Automatikus elutasítás**: Az engedélyek automatikusan meg lesznek tagadva.
- **Dátum-és időváltozások**: a **Letiltás** gombra kattintva megakadályozhatja, hogy a felhasználók manuálisan állítsa be a dátumot és az időt. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára az eszközön beállított dátumot és időt.
- **Hangerő-módosítás**: A **Tiltás** lehetőség választásával megakadályozza a felhasználókat az eszköz hangerejének módosításában. A **nincs konfigurálva** beállítás lehetővé teszi a kötet beállításainak használatát az eszközön.
- **Gyári beállítások visszaállítása**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók a gyári beállítások visszaállítása lehetőséget használják az eszköz beállításaiban. A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználók ezt a beállítást használják az eszközön.
- **Csökkentett üzemmódú indítás**: A **Tiltás** lehetőség választásával megakadályozza a felhasználókat az eszköz csökkentett módban való újraindításában. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára, hogy csökkentett módban újraindítsák az eszközt.
- **Állapotsor**: a **Letiltás** elemre kattintva megakadályozhatja az állapotsor elérését, beleértve az értesítéseket és a gyors beállításokat is. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára az állapotsor elérését.
- **Barangoló adatszolgáltatások**: a **Letiltás** elem kiválasztásával megakadályozhatja az adatroamingot a mobil hálózaton. A **nincs konfigurálva** beállítás lehetővé teszi az adatroaming használatát, ha az eszköz mobil hálózaton van.
- **Wi-Fi-beállítások módosításai**: a **Letiltás** beállítás megadásával megakadályozhatja, hogy a felhasználók az eszköz tulajdonosával létrehozott Wi-Fi-beállításokat módosíthassák. A felhasználók saját Wi-Fi-konfigurációkat hozhatnak létre. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára az eszköz Wi-Fi-beállításainak módosítását.
- **Wi-Fi hozzáférési pont konfigurálása**: a **Letiltás** gombra kattintva megakadályozhatja, hogy a felhasználók bármilyen Wi-Fi-konfigurációt hozzanak létre vagy módosítsanak. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára az eszköz Wi-Fi-beállításainak módosítását.
- **Bluetooth-konfiguráció**: a **Letiltás** elem kiválasztásával megakadályozhatja a felhasználók számára a Bluetooth konfigurálását az eszközön. A **nincs konfigurálva** beállítás engedélyezi a Bluetooth használatát az eszközön.
- **Lekötés és hozzáférés a**hozzáférési pontokhoz: válassza a **Letiltás** lehetőséget, hogy megakadályozza a lekötést és a hordozható hozzáférési pontokhoz való hozzáférést. A **nincs konfigurálva** beállítás lehetővé teszi a hordozható hozzáférési pontokhoz való lekötést és hozzáférést.
- **USB-tároló**: válassza az **Engedélyezés lehetőséget** az USB-tároló eléréséhez az eszközön. A **nincs konfigurálva beállítás** MEGAKADÁLYOZZA az USB-tároló elérését.
- USB-fájlátvitel: a **Letiltás** beállítás **megadásával**MEGAKADÁLYOZhatja a fájlok USB-kapcsolaton keresztüli átvitelét. A **nincs konfigurálva** lehetővé teszi a fájlok átvitelét.
- **Külső média**: válassza a **Letiltás** lehetőséget az eszközön található külső adathordozók használatának vagy csatlakoztatásának megakadályozásához. **Nincs konfigurálva** a külső adathordozó az eszközön.
- **Adatok továbbítása az NFC használatával**: válassza a **Letiltás** lehetőséget, hogy ne használja a kis hatótávolságú kommunikáció (NFC) technológiát az adatok az alkalmazásokból való kisugárzásához. **Nincs konfigurálva** , lehetővé teszi az NFC használatát az eszközök közötti adatmegosztáshoz.
- **Hibakeresési funkciók**: válassza az **Engedélyezés lehetőséget** , hogy a felhasználók a hibakeresési funkciókat használják az eszközön. A **nincs konfigurálva beállítás** megakadályozza, hogy a felhasználók a hibakeresési funkciókat használják az eszközön.
- **Mikrofon beállítása**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók visszakapcsolják a mikrofont, és beállítsa a mikrofon kötetét. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználó számára az eszközön található mikrofon kötetének beállítását és módosítását.
- **Gyári beállítások visszaállítása a védelmi e-mailekre**: válassza a **Google-fiók e-mail-címe**lehetőséget. Adja meg azoknak az eszköz-rendszergazdáknak az e-mail-címeit, amelyek a törlés után feloldják az eszköz zárolását. Ügyeljen arra, hogy az e-mail-címeket pontosvesszővel válassza el, például `admin1@gmail.com;admin2@gmail.com`. Ha nem ad meg e-mailt, bárki feloldja az eszköz zárolását a gyári beállításokra való visszaállítás után. Ezek az e-mailek csak akkor érvényesek, ha nem a felhasználó gyári alaphelyzetbe állítását futtatják, például a gyári beállítások visszaállítását a helyreállítási menü használatával.
- **Hálózati Escape-sraffozás**: válassza az **Engedélyezés** lehetőséget, hogy a felhasználók bekapcsolják a hálózati Escape-sraffozás funkciót. Ha nem történik hálózati kapcsolat az eszköz indításakor, akkor a menekülési sraffozás arra kéri, hogy ideiglenesen kapcsolódjon egy hálózathoz, és frissítse az eszköz házirendjét. A szabályzat alkalmazása után a rendszer elfelejti az átmeneti hálózatot, és az eszköz folytatja a rendszerindítást. Ez a funkció csatlakoztatja az eszközöket egy hálózathoz, ha:
  - Nincs megfelelő hálózat az utolsó szabályzatban.
  - Az eszköz zárolási feladat módban elindul egy alkalmazásba.
  - A felhasználó nem tudja elérni az eszközbeállítások beállításait.

  A **nincs konfigurálva beállítás** megakadályozza, hogy a felhasználók bekapcsolják a hálózati Escape-sraffozás funkciót az eszközön.

- **Rendszerfrissítés**: válassza ki azt a lehetőséget, amely meghatározza, hogy az eszköz hogyan kezelje a csatornákon belüli frissítéseket:
  - **Eszköz alapértelmezése**: Az eszköz alapértelmezett beállításának használata.
  - **Automatikus**: A rendszer automatikusan, felhasználói beavatkozás nélkül telepíti a frissítéseket. Ennek a szabályzatnak a beállításakor minden függőben lévő frissítés azonnal települ.
  - **Elhalasztva**: A frissítések 30 nappal el lesznek halasztva. A 30 nap végén az Android kéri a felhasználót, hogy telepítse a frissítést. Az eszközgyártók vagy a szolgáltatók megakadályozhatják (kivételként) a fontos biztonsági frissítések elhalasztását. A kivételként kezelt frissítések rendszerértesítést jelenítenek meg a felhasználó számára az eszközön.
  - **Karbantartási időszak**: Automatikusan telepíti a frissítéseket az Ön által az Intune-ban beállított napi karbantartási időszakban. A telepítés 30 napig naponta próbálkozik, és sikertelen lehet, ha nincs elég hely vagy akkumulátor. 30 nap elteltével az Android felszólítja a felhasználót a telepítésre. Ez az időszak szolgál a Play-alkalmazások frissítéseinek telepítésére is. Ezt a lehetőséget olyan dedikált eszközökhöz használhatja, mint például a kioszkok, az Egyalkalmazásos dedikált eszköz előtérben lévő alkalmazások is frissíthetők.

- **Értesítési ablakok**: Ha **letiltja**a beállítást, a rendszer nem jeleníti meg az eszközön az ablakokra vonatkozó értesítéseket, például a pirítóst, a bejövő hívásokat, a kimenő hívásokat, a rendszerriasztásokat és a rendszerhibákat. Ha a **nincs konfigurálva**értékre van állítva, a rendszer az operációs rendszer alapértelmezett beállításait használja, ami lehet, hogy az értesítéseket jeleníti meg.
- **Első használati útmutatók kihagyása**: válassza az **Engedélyezés** lehetőséget az alkalmazások javaslatainak megjelenítéséhez vagy kihagyásához, vagy olvassa el a bevezető tippeket az alkalmazás indításakor. Ha a **nincs konfigurálva**értékre van állítva, a rendszer az operációs rendszer alapértelmezett beállításait használja, amely az alkalmazás indításakor a javaslatok megjelenítéséhez vezethet.

### <a name="system-security-settings"></a>A rendszer biztonsági beállításai

- **Veszélyforrások vizsgálata az alkalmazásokban**: **kötelező** (alapértelmezett) lehetővé teszi, hogy a Google Play Protect alkalmazás a telepítés előtt és után ellenőrizze az alkalmazásokat. Ha fenyegetést észlel, figyelmeztetheti a felhasználót, hogy távolítsa el az alkalmazást az eszközről. A **nincs konfigurálva beállítás** nem engedélyezi vagy nem futtatja a Google Play Protect alkalmazást az alkalmazások vizsgálatához.

### <a name="dedicated-device-settings"></a>Dedikált eszközbeállítások

Ezekkel a beállításokkal konfigurálhatja a dedikált eszközökön a kioszk stílusú élményt. Beállíthat egy eszközt egy alkalmazás futtatásához vagy számos alkalmazás futtatásához. Ha egy eszköz kioszk módban van beállítva, csak a hozzáadott alkalmazások érhetők el. Ezek a beállítások az Android Enterprise dedikált eszközökre vonatkoznak. Nem vonatkoznak az Android Enterprise teljes körűen felügyelt eszközeire.

Teljes **képernyős mód**: válassza ki, hogy az eszköz futtat-e egy alkalmazást, vagy több alkalmazást futtat.

- **Egyetlen alkalmazás**: a felhasználók csak egyetlen alkalmazást tudnak elérni az eszközön. Az eszköz indításakor csak az adott alkalmazás indul el. A felhasználók nem nyithatnak meg új alkalmazásokat, és nem módosíthatják a futó alkalmazást.

  - **Felügyelt alkalmazás kiválasztása**: válassza ki a felügyelt Google Play alkalmazást a listából.

    Ha nem rendelkezik a felsorolt alkalmazásokkal, [vegyen fel néhány Android-alkalmazást](../apps/apps-add-android-for-work.md) az eszközre. Ügyeljen arra, hogy [az alkalmazást a dedikált eszközökhöz létrehozott eszközcsoport számára társítsa](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > Egyalkalmazásos kioszk mód használata esetén előfordulhat, hogy a tárcsázó/telefonos alkalmazások nem működnek megfelelően. 
  
- **Több alkalmazás**: a felhasználók korlátozott számú alkalmazást férhetnek hozzá az eszközhöz. Az eszköz indításakor csak a hozzáadott alkalmazások indulnak el. Hozzáadhat olyan webes hivatkozásokat is, amelyeket a felhasználók megnyithatnak. A házirend alkalmazása esetén a felhasználók az engedélyezett alkalmazások ikonjait látják a kezdőképernyőn.

  > [!IMPORTANT]
  > A többalkalmazásos dedikált eszközök esetében a Google Play által [kezelt kezdőképernyő alkalmazásnak](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) a következőknek **kell lennie**:
  >   - [Ügyfél-alkalmazásként hozzáadva](../apps/apps-add-android-for-work.md) az Intune-ban
  >   - [Hozzárendelve a](../apps/apps-deploy.md) dedikált eszközökhöz létrehozott eszközcsoport számára
  >
  > A **felügyelt kezdőképernyő** alkalmazásnak nem szükséges a konfigurációs profilban lennie, de az ügyfél-alkalmazásként való hozzáadásra van szükség. Ha a **felügyelt kezdőképernyő** alkalmazást ügyfél-alkalmazásként adja hozzá, a konfigurációs profilban hozzáadott más alkalmazások ikonként jelennek meg a **felügyelt kezdőképernyő** alkalmazásban.
  >
  > Többalkalmazásos kioszk mód használata esetén előfordulhat, hogy a tárcsázó/telefonos alkalmazások nem működnek megfelelően. 

  - **Hozzáadás**: válassza ki az alkalmazásokat a listából.

    Ha a **felügyelt kezdőképernyő** alkalmazás nem szerepel a listáján, [vegye fel azt a Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise)áruházból. Ügyeljen arra, hogy az alkalmazást a dedikált eszközökhöz létrehozott eszközcsoport számára [társítsa](../apps/apps-deploy.md) .

    A szervezet által létrehozott egyéb [Android-alkalmazásokat](../apps/apps-add-android-for-work.md) és [webalkalmazásokat](../apps/web-app.md) is hozzáadhat az eszközhöz. Ügyeljen arra, hogy [az alkalmazást a dedikált eszközökhöz létrehozott eszközcsoport számára társítsa](../apps/apps-deploy.md).

  - **Virtual Home gomb**: egy Soft-Key gomb, amely visszaadja a felhasználókat a felügyelt kezdőképernyő számára, hogy a felhasználók váltani tudják az alkalmazások között. A választható lehetőségek:

    - **Nincs konfigurálva** (alapértelmezett): A Kezdőlap gomb nem jelenik meg. Az alkalmazások közötti váltáshoz a felhasználóknak a vissza gombot kell használniuk.
    - **Felugró**: a Kezdőlap gomb azt jelzi, hogy a felhasználó mikor kerül be az eszközre.
    - **Úszó**: az eszközön állandó, lebegő Kezdőlap gombot jelenít meg.

  - **Kilépés a kioszk módból**: válassza az **Engedélyezés** lehetőséget, hogy a rendszergazdák ideiglenesen szüneteltetik a kioszk üzemmódot az eszköz frissítéséhez. A szolgáltatás használatához a rendszergazda:
  
    1. Továbbra is kijelöli a vissza gombot, amíg meg nem jelenik a **kilépési kioszk** gomb. 
    2. Kiválasztja a **kilépési kioszk** gombot, és belép a teljes **képernyős mód kód PIN-kódjába** .
    3. Ha elkészült, válassza a **felügyelt kezdőképernyő** alkalmazást. Ez a lépés a többalkalmazásos kioszk módba helyezi az eszközt.

      Ha a **nincs konfigurálva**értékre van állítva, a rendszergazdák nem tudják szüneteltetni a kioszk üzemmódot. Ha a rendszergazda továbbra is kiválasztja a vissza gombot, és kiválasztja a **kilépési kioszk** gombot, akkor egy üzenet jelzi, hogy PIN-kódot kell megadnia.

    - **Hagyja ki a kioszk mód kódját**: adjon meg egy 4-6 számjegyű PIN-kódot. A rendszergazda ezt a PIN-kódot használja a kioszk mód ideiglenes szüneteltetéséhez.

  - **Egyéni URL-cím beállítása**: adjon meg egy URL-címet, amely testreszabja a háttérben lévő képernyőt a dedikált eszközön.

    > [!NOTE]
    > A legtöbb esetben azt javasoljuk, hogy legalább a következő méretű képekkel kezdjen el:
    >
    > - Telefonszám: 1080x1920 px
    > - Tablet: 1920 × 1080 px
    >
    > A legjobb élmény és a ropogós részletek tekintetében azt javasoljuk, hogy eszközönként a megjelenítési specifikációk alapján hozzon létre egy eszközön rendszerkép-eszközöket.
    >
    > A modern kijelzők nagyobb képpontokkal rendelkeznek, és megfelelő 2K/4K definíciós képeket tudnak megjeleníteni.

  - **Wi-Fi-konfiguráció**: az **Engedélyezés** megjeleníti a Wi-Fi vezérlőelemet a felügyelt kezdőképernyőn, és lehetővé teszi a végfelhasználók számára az eszköz csatlakoztatását a különböző WiFi-hálózatokhoz. A funkció engedélyezése az eszköz helyét is bekapcsolja. **Nincs konfigurálva** (az alapértelmezett) nem jeleníti meg a Wi-Fi vezérlőelemet a felügyelt kezdőképernyő képernyőjén. Megakadályozza, hogy a felhasználók a felügyelt kezdőképernyő használatával csatlakozzanak a Wi-Fi-hálózatokhoz.

  - **Bluetooth-konfiguráció**: az **Engedélyezés** megjeleníti a Bluetooth-vezérlést a felügyelt kezdőképernyőn, és lehetővé teszi a végfelhasználók számára az eszközök párosítását a Bluetooth-on keresztül. A funkció engedélyezése az eszköz helyét is bekapcsolja. **Nincs konfigurálva** (az alapértelmezett) nem jeleníti meg a Bluetooth-vezérlést a felügyelt kezdőképernyő képernyőjén. Megakadályozza, hogy a felhasználók a felügyelt kezdőképernyő használata közben a Bluetooth és a párosítási eszközöket konfigurálja.

  - **Zseblámpa-hozzáférés**: az **Engedélyezés** megjeleníti a zseblámpa vezérlőelemet a felügyelt kezdőképernyőn, és lehetővé teszi a végfelhasználók számára a zseblámpa be-és kikapcsolását. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a zseblámpa vezérlőelemet a felügyelt kezdőképernyő képernyőn. Ez megakadályozza a felhasználók számára a zseblámpa használatát a felügyelt kezdőképernyő használata közben.

  - **Adathordozó hangerő-szabályozása**: az **Engedélyezés** megjeleníti a Media Volume Controlt a felügyelt kezdőlapon, és lehetővé teszi a végfelhasználók számára, hogy a csúszka használatával módosítsák az eszköz adathordozó-kötetét. **Nincs konfigurálva** (az alapértelmezett) nem jeleníti meg a Media Volume Controlt a felügyelt kezdőképernyőn. Ez megakadályozza, hogy a felhasználók a felügyelt kezdőképernyő használata közben módosítsák az eszköz adathordozó-kötetét, kivéve, ha a hardveres gombok támogatják azt. 

  - **Képernyőkímélő mód**: az **Engedélyezés** megjeleníti a képernyővédőt a felügyelt kezdőképernyőn, ha az eszköz zárolva van vagy időtúllépés miatt. **Nincs konfigurálva** (alapértelmezés) nem mutat képernyővédőt a felügyelt kezdőképernyőn.

    Ha engedélyezve van, konfigurálja a következőket is:

    - **Egyéni képernyőkímélő-rendszerkép beállítása**: adja meg az egyéni rendszerkép URL-címét. Írja be például a következőt:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.html`

      Ha nem ad meg URL-címet, a rendszer az eszköz alapértelmezett képét használja, ha van alapértelmezett rendszerkép.

    - Azon **másodpercek száma, ameddig az eszköz képernyőkímélőt jelenít meg a képernyő kikapcsolása előtt**: válassza ki, hogy az eszköz mennyi ideig jelenítse meg a képernyővédőt. 0-9999999 másodperc közötti értéket adjon meg. Az alapértelmezett érték `0` másodperc. Ha üresen hagyja, vagy nulla (`0`) értékre van állítva, a képernyőkímélő aktív, amíg a felhasználó nem kommunikál az eszközzel.
    - Azon **másodpercek száma, ameddig az eszköz inaktív a képernyőkímélő megjelenítése előtt**: válassza ki, hogy az eszköz mennyi ideig tétlen a képernyővédő megjelenítése előtt. 1-9999999 másodperc közötti értéket adjon meg. Az alapértelmezett érték `30` másodperc. Nullánál nagyobb számot kell megadnia (`0`).
    - **Adathordozó észlelése a képernyőkímélő elindítása előtt**: az **Engedélyezés** (alapértelmezett) nem jeleníti meg a képernyővédőt, ha a hang vagy a videó lejátszása az eszközön történik. A **nincs konfigurálva beállítás** megjeleníti a képernyőkímélőt, még akkor is, ha a hang vagy a videó lejátszása megtörténik.

### <a name="device-password-settings"></a>Eszköz jelszóbeállításai

- **Zárolási képernyő letiltása**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók a billentyűzár-zárolási képernyő szolgáltatást használják az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználó számára a billentyûzár funkcióinak használatát.
- A **zárolási képernyő funkcióinak letiltása**: Ha a billentyűzár engedélyezve van az eszközön, válassza ki a letiltani kívánt szolgáltatásokat. Ha például a **biztonságos kamera** be van jelölve, a kamera funkció le van tiltva az eszközön. A nem ellenőrzött funkciók engedélyezve vannak az eszközön.

  Ezek a funkciók a felhasználók számára érhetők el, ha az eszköz zárolva van. A felhasználók nem látják és nem férnek hozzá a bejelölt szolgáltatásokhoz.

- **Megkövetelt jelszótípus**: Adja meg az eszközön megkövetelt jelszótípust. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Jelszó szükséges, nincs korlátozás**
  - **Gyenge biometrikus**: [erős és gyenge biometria](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (az Android webhely megnyitása)
  - **Numerikus**: a jelszó csak számok, például `123456789` lehet. Adja meg a **jelszó minimális hosszát** , amelyet a felhasználónak 4 és 16 karakter között kell megadnia.
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
    - **Szükséges karakterek száma**: Itt adhatja meg, hogy hány szimbólumot kell megadni (`&`, `#`, `%` stb.) a jelszónak 0 és 16 karakter közöttinek kell lennie.

- A **jelszó lejárati idejét jelző napok száma**: adja meg a napok számát 1-365 között, amíg meg nem változtatja az eszköz jelszavát. Ha például a 60 nap után szeretné módosítani a jelszót, írja be `60` értéket. A jelszó lejáratakor a rendszer a felhasználókat új jelszó létrehozására kéri.
- A jelszó megadásához **szükséges jelszavak száma**: adja meg, hogy hány legutóbbi jelszó ne legyen újra felhasználható, 1-24 között. Ezzel a beállítással korlátozhatja, hogy a felhasználó korábban használt jelszavakat hozzon létre.
- Sikertelen **bejelentkezések száma az eszköz törlése előtt**: Itt adhatja meg, hogy a rendszer hány%-ot adjon meg az eszköz törlése előtt a sikertelen bejelentkezések 4-11 között.

### <a name="power-settings"></a>Energiaellátási beállítások

- **A képernyő zárolásáig eltelt idő**: Adja meg, mennyi tétlenség után legyen az eszköz zárolva.
- **Bekapcsolt képernyő, amikor az eszköz áramforráshoz van csatlakoztatva**: Válassza ki, mely áramforrások csatlakoztatásakor maradjon bekapcsolva az eszköz képernyője.

### <a name="users-and-accounts-settings"></a>Felhasználói és fiókbeállítások

- **Új felhasználók hozzáadása**: Válassza a **Tiltás** lehetőséget, hogy megakadályozza a felhasználókat új felhasználók hozzáadásában. Minden felhasználónak van személyes területe az eszközön az egyéni kezdőképernyő, a fiókok, az alkalmazások és a beállítások számára. A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználók más felhasználókat adjanak hozzá az eszközhöz.
- **Felhasználó eltávolítása**: Válassza a **Tiltás** lehetőséget, hogy megakadályozza a felhasználókat felhasználók eltávolításában. A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználók eltávolítsanak más felhasználókat az eszközről.
- **Fiókmódosítások**: Válassza a **Tiltás** lehetőséget, hogy megakadályozza a felhasználókat a fiókok módosításában. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára a felhasználói fiókok frissítését az eszközön.

  > [!NOTE]
  > Ez a beállítás nem felel meg az eszköz tulajdonosának (teljes mértékben felügyelt) eszközeinek. Ha ezt a beállítást konfigurálja, a rendszer figyelmen kívül hagyja a beállítást, és nincs hatással.

### <a name="applications"></a>Alkalmazások

- **Ismeretlen forrásból történő telepítés engedélyezése**: válassza az **Engedélyezés lehetőséget** , hogy a felhasználók bekapcsolják az **ismeretlen forrásokat**. Ez a beállítás lehetővé teszi, hogy az alkalmazások ismeretlen forrásokból telepítsenek, beleértve a Google Play Áruházon kívüli forrásokat is. A **nincs konfigurálva beállítás** megakadályozza, hogy a felhasználók **ismeretlen forrásokat**kapcsoljanak be.
- **Hozzáférés engedélyezése a Google Play áruházban lévő összes alkalmazáshoz**: Ha a beállítás **engedélyezésre**van állítva, a felhasználók hozzáférhetnek a Google Play áruházban lévő összes alkalmazáshoz. Nem férhetnek hozzá az alkalmazásokhoz az [ügyfélalkalmazások](../apps/apps-add-android-for-work.md)rendszergazdai blokkja. **Nincs konfigurálva** , hogy a felhasználók csak az alkalmazásokhoz férhessenek hozzá, a rendszergazda elérhetővé teszi a Google Play áruházat vagy az [ügyfélalkalmazások](../apps/apps-add-android-for-work.md)számára szükséges alkalmazásokat.
- **Alkalmazás automatikus frissítései**: válassza ki, hogy mikor történjen az automatikus frissítések telepítése. A választható lehetőségek:
  - **Nincs konfigurálva**
  - **Felhasználó választása**
  - **Soha nem**
  - **Csak Wi-Fi**
  - **Mindig**

### <a name="connectivity"></a>Connectivity

- **Mindig bekapcsolt VPN**: Az **Engedélyezés** beállítással a VPN-ügyfél automatikusan csatlakozik és újracsatlakozik a VPN-hez. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal elindítható, ha a felhasználó zárolja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. 

  A mindig bekapcsolt VPN beállítás az összes VPN-ügyfél számára való letiltásához válassza a **Nincs konfigurálva** lehetőséget.

  > [!IMPORTANT]
  > Egy eszközön egyszerre csak egy mindig bekapcsolt VPN-szabályzatot helyezzen üzembe. Több ilyen szabályzat üzembe helyezése egyetlen eszközön nem támogatott.

- **VPN-ügyfél**: Válasszon egy Mindig bekapcsolt állapotot támogató VPN-ügyfelet. A választható lehetőségek:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Hálózatok GlobalProtect
  - Pulse Secure
  - Egyéni
    - **Csomagazonosító**: Adja meg az alkalmazás csomagazonosítóját a Google Play Áruházban. Ha például az áruházban levő alkalmazás URL-címe `https://play.google.com/store/details?id=com.contosovpn.android.prod`, a csomagazonosító `com.contosovpn.android.prod` lesz.

  > [!IMPORTANT]
  > - A kiválasztott VPN-ügyfelet az eszközön kell telepíteni, és támogatnia kell az alkalmazásonkénti VPN-t a munkahelyi profilokban. Ellenkező esetben hiba történik. 
  > - A VPN-ügyfélalkalmazást jóvá kell hagynia a **felügyelt Google Play Áruházban**, szinkronizálnia kell az alkalmazást az Intune-nal, majd üzembe helyeznie az eszközön. Ezt követően az alkalmazás telepítve lesz a felhasználó munkahelyi profiljában.
  > - Ismert problémák merülhetnek fel az alkalmazáson belüli VPN és az F5 Access for Android 3.0.4 használatával. További információért lásd a [F5's kibocsátási megjegyzéseit az F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) számára című témakört.

- **Zárolási mód**: válassza az **Engedélyezés** lehetőséget az összes hálózati forgalom kényszerítéséhez a VPN-alagút használatára. Ha a VPN-kapcsolat nincs kiépítve, az eszköznek nem lesz hálózati hozzáférése.

  A **Nincs konfigurálva** beállítással a forgalom a VPN-alagúton vagy a mobilhálózaton is áthaladhat.

- **Ajánlott globális proxy**: válassza az **Engedélyezés** lehetőséget a globális proxy eszközökhöz való hozzáadásához. Ha engedélyezve van, a HTTP-és HTTPS-forgalom, beleértve az eszközön lévő alkalmazásokat is, használja a megadott proxyt. Ez a proxy csak javaslat. Lehetséges, hogy néhány alkalmazás nem fogja használni a proxyt. **Nincs konfigurálva** (alapértelmezés) nem ad hozzá javasolt globális proxyt.

  A szolgáltatással kapcsolatos további információkért lásd: [setRecommendedGlobalProxy](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setRecommendedGlobalProxy(android.content.ComponentName,%20android.net.ProxyInfo)) (Android-webhely megnyitása).

  Ha engedélyezve van, adja meg a proxy **típusát** is. A választható lehetőségek:

  - **Közvetlen**: válassza ezt a lehetőséget a proxykiszolgáló adatainak manuális megadásához, beleértve a következőket:
    - **Gazdagép**: adja meg a proxykiszolgáló állomásnevét vagy IP-címét. Például írja be a következőt: `proxy.contoso.com` vagy `127.0.0.1`.
    - **Portszám**: adja meg a proxykiszolgáló által használt TCP-portszámot. Például írja be a következőt: `8080`.
    - **Kizárt gazdagépek**: adja meg a proxyt nem használó állomásnevek vagy IP-címek listáját. Ez a lista tartalmazhatja a csillag (`*`) helyettesítő karaktert, valamint több gazdagépet pontosvesszővel (`;`) elválasztva szóközök nélkül. Például írja be a következőt: `127.0.0.1;web.contoso.com;*.microsoft.com`.

  - **Proxy automatikus**konfiguráció: adja meg a **PAC URL-címét** egy proxy automatikus konfigurációs parancsfájlhoz. Például írja be a következőt: `https://proxy.contoso.com/proxy.pac`.

    A PAC-fájlokkal kapcsolatos további információkért lásd: [proxy automatikus konfigurációs (PAC) fájlja](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (egy nem Microsoft-webhely megnyitása).

## <a name="work-profile-only"></a>Csak munkahelyi profil

### <a name="work-profile-settings"></a>Munkahelyi profil beállításai

#### <a name="general"></a>Általános

- **Másolás és beillesztés a munkahelyi és a személyes profilok között**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja a munkahelyi és a személyes alkalmazások közötti másolást és beillesztést. **Nincs konfigurálva** , amely lehetővé teszi a felhasználók számára az adatmegosztást a személyes profilban lévő alkalmazásokkal való másolás és beillesztés használatával 
- **Munkahelyi és személyes profilok közötti adatmegosztás**: válassza ki, hogy a munkahelyi profilban szereplő alkalmazások megoszthatnak-e a személyes profilban lévő alkalmazásokkal. Például megadhatja az alkalmazásokon belüli megosztási műveleteket, például a **megosztást..** . lehetőséget a Chrome böngészőalkalmazásban). Ez a beállítás nem vonatkozik a másolás/beillesztés vágólapi viselkedésre. A megosztási lehetőségek:
  - **Eszköz alapértelmezése**: az eszköz alapértelmezett megosztási viselkedése, amely az Android-verziótól függően változhat. Alapértelmezés szerint a személyes profilból lehet a munkahelyi profilba adatokat megosztani, a munkahelyiből a személyesbe viszont nem. A beállítás célja a munkahelyi profilból a személyesbe irányuló adatmegosztás megelőzése. A Google a 6.0-snál újabb verziójú eszközökön nem nyújt lehetőséget a személyesből a munkahelyi profilba irányuló adatmegosztás blokkolására.
  - **A munkahelyi profilban lévő alkalmazások kezelhetik a személyes profilból érkező megosztási kérelmeket**: Engedélyezi a személyesből a munkahelyi profilba irányuló adatmegosztásra szolgáló beépített Android-funkciót. Engedélyezéskor a személyes profil alkalmazásaiból származó megosztási kérések kezdeményezhetnek adatmegosztást a munkahelyi profil alkalmazásaival. A 6.0-snál korábbi verziójú androidos eszközökön ez az alapértelmezett beállítás.
  - **A határokon átívelő megosztás megakadályozása**: meggátolja a munkahelyi és a személyes profilok közötti megosztást.
  - **Nincs korlátozás a megosztáshoz**: lehetővé teszi a munkahelyi profil határán belüli megosztást mindkét irányban. Ilyenkor a munkahelyi profilban szereplő alkalmazások megoszthatnak adatokat a személyes profi jelöletlen alkalmazásaival. A beállítással lehetővé teszi a munkahelyi profil alkalmazásainak az adatmegosztást az eszköz nem felügyelt részével. Így körültekintően használja ezt a lehetőséget.

- **Munkahelyi profil értesítései az eszköz zárolt állapotában**: azt határozza meg, hogy a munkahelyi profilban szereplő alkalmazások megjeleníthetnek-e értesítéseket az eszköz zárolt állapotában. A **blokk** nem jeleníti meg az adathalmazt. A **nincs konfigurálva** érték jelenik meg.
- **Alapértelmezett alkalmazásengedélyek**: Itt adhatja meg a munkahelyi profilban található összes alkalmazásra vonatkozó alapértelmezett engedélyszabályzatot. Az Android 6-os verziójától kezdve a rendszer alkalmazásindításkor felszólítja a felhasználót az alkalmazás által megkövetelt, konkrét engedélyek megadására. Ezzel a szabályzatbeállítással döntheti el, hogy a felhasználók megadhatják-e a munkahelyi profilban szereplő összes alkalmazás engedélyeit. Hozzárendelhet például egy olyan alkalmazást a munkahelyi profilhoz, amely helyadatokhoz kér hozzáférést. Általában az alkalmazás kéri a felhasználót a helyadatokhoz való hozzáférés megadására vagy elutasítására. Ezzel a szabályzattal kérdés nélkül automatikusan engedélyezhet vagy letilthat minden hozzáférést, vagy átadhatja a döntés jogát a felhasználónak. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Rákérdezés**
  - **Automatikus engedélyezés**
  - **Automatikus elutasítás**

  Alkalmazáskonfigurációs szabályzatokkal is engedélyeket adhat egyes alkalmazásoknak (**Ügyfélalkalmazások** > **Alkalmazáskonfigurációs szabályzatok**).

- **Fiókok hozzáadása és eltávolítása**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a végfelhasználók fiókokat adjanak hozzá vagy távolítanak el a munkahelyi profilban. Ha például a Gmail alkalmazást androidos munkahelyi profilban telepíti, megakadályozhatja, hogy a végfelhasználók fiókokat adjanak hozzá vagy távolítsanak el ebben a munkaprofilban. A **nincs konfigurálva** beállítás lehetővé teszi a munkahelyi profilban lévő fiókok hozzáadását.  

- **Névjegyek megosztása Bluetooth-kapcsolattal**: Engedélyezi egy másik Bluetooth-eszköz (például egy autó) a munkahelyi névjegyekhez való hozzáférését. Alapértelmezés szerint ez a beállítás nincs konfigurálva, a munkahelyi névjegyek pedig nem jelennek meg. A megosztás engedélyezéséhez és a munkahelyi profil névjegyeinek megjelenítéséhez válassza az **Engedélyezés** lehetőséget. Ez a beállítás az Android munkahelyi profilos, Android v6.0 és újabb operációs rendszerekkel rendelkező eszközökre vonatkozik. A beállítás engedélyezésével megengedheti bizonyos Bluetooth-eszközöknek, hogy az első kapcsolat alkalmával gyorsítótárazzák a munkahelyi kapcsolatokat. Ennek a szabályzatnak az eredeti párosítás/szinkronizálás utáni letiltása nem feltétlenül távolítja el a munkahelyi kapcsolatokat a Bluetooth-eszközről.

- **Képernyőfelvétel**: a **Letiltás** elem kiválasztásával megakadályozhatja a képernyőképek vagy képernyőfelvételek készítését az eszközön a munkahelyi profilban. Ezen kívül megakadályozza a tartalom megjelenítését a biztonságos videokimenettel nem rendelkező megjelenítő eszközökön. A **nincs konfigurálva** beállítás lehetővé teszi a képernyőképek lekérését.

- **Munkahelyi kapcsolattartási hívó azonosítójának megjelenítése a személyes profilban**: Ha engedélyezve van (**nincs konfigurálva**), a munkahelyi kapcsolattartási hívó adatai megjelennek a személyes profilban. Ha a **blokkolás**értékre van állítva, a munkahelyi partneri hívó száma nem jelenik meg a személyes profilban. Az Android operációs rendszer 6.0-ás és újabb verzióira vonatkozik.

- **Munkahelyi Névjegyek keresése a személyes profilból**: válassza a **Letiltás** lehetőséget, hogy a felhasználók a személyes profilban lévő alkalmazásokban keressenek munkahelyi névjegyeket. A **nem kötelező** beállítás lehetővé teszi a munkahelyi névjegyek keresését a személyes profilban.

- **Kamera**: válassza a **Letiltás** lehetőséget a munkahelyi profilban található eszköz kamerához való hozzáférésének megakadályozásához. A beállítás nincs hatással a fényképezőkép személyes profilban való használatára. **Nincs szükség** a munkahelyi profilban található kamerához való hozzáférésre.

- **Widgetek használatának engedélyezése a munkahelyi profil alkalmazásaiból**: az **Engedélyezés** lehetővé teszi a végfelhasználók számára, hogy a kezdőképernyő alkalmazásai által elérhetővé tegyék a widgeteket. A **Nincs konfigurálva** (alapértelmezett) érték letiltja a funkciót.

  Az Outlook például a felhasználók munkahelyi profiljaira van telepítve. Az **Engedélyezés**beállítás megadása esetén a felhasználók az eszköz kezdőlapjára helyezhetik el a napirend widgetet.

#### <a name="work-profile-password"></a>Munkahelyi profil jelszava

- **Munkahelyi profilhoz tartozó jelszó megkövetelése**: Az engedélyezett munkahelyi profillal rendelkező Android 7.0-s és újabb verziójú eszközökre vonatkozik. Válassza a **kötelező** lehetőséget egy olyan PIN-kód megadásához, amely csak a munkahelyi profil alkalmazásaira vonatkozik. Alapértelmezés szerint a végfelhasználónak lehetősége van két külön-külön definiált PIN-kód használatára, vagy a felhasználók dönthetnek úgy, hogy a két meghatározott PIN-kód összevonásával csak az erősebbet használják. A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználó jelszó megadása nélkül használja a munkahelyi alkalmazásokat.
- **Jelszó minimális hossza**: Itt adhatja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát (**4**-**16**).
- **A munkahelyi profil zárolása legfeljebb ennyi perc inaktivitás után**: Itt adhatja meg, hogy mennyi idő után zárolódjon a munkahelyi profil. A felhasználónak ezután meg kell adnia a hitelesítő adatait a hozzáférés visszanyeréséhez.
- **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**: Itt adhatja meg, hogy hányszor lehet helytelen jelszót megadni, mielőtt a rendszer törölné az eszközről a munkahelyi profil összes adatát.
- **Jelszó érvényessége (nap)** : Itt adhatja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát (**1**-**255**).
- **Kötelező jelszótípus**: Itt adhatja meg az eszközön beállítandó jelszó típusát. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Kötelező**
  - **Legalább számok**
  - **Komplex numerikus**: Nem lehet ismétlődő vagy egymást követő számokat megadni, például az „1111-et” vagy az „1234-et”
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Itt adhatja meg, hogy hány új jelszót kell beállítani, mielőtt egy korábbit újból használhatna (**1**-**24**).
- **Ujjlenyomat-feloldás**: válassza a **Letiltás** lehetőséget, hogy a végfelhasználók ne használják az eszköz ujjlenyomat-olvasóját az eszköz zárolásának feloldásához. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználók számára, hogy az ujjlenyomattal rendelkező eszközöket a munkahelyi profilban oldják fel.
- **Smart Lock és egyéb megbízhatósági ügynökök**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy Smart lock vagy más megbízhatósági ügynökök a kompatibilis eszközökön módosítsák a zárolási képernyő beállításait. Ez a szolgáltatás, más néven megbízhatósági ügynök, lehetővé teszi az eszköz zárolási képernyőjének jelszavának letiltását vagy megkerülését, ha az eszköz megbízható helyen van. Így például megkerülheti a munkahelyi profil jelszavát abban az esetben, ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címke közelében van. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.

### <a name="device-password"></a>Eszköz jelszava

Ezek a jelszó-beállítások a munkahelyi profilt használó eszközök személyes profiljaira érvényesek.

- **Jelszó minimális hossza**: Itt adhatja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát (**4**-**14**).
- **Képernyőzárolás legfeljebb ennyi perc inaktivitás után**: Itt adhatja meg, hogy mennyi idő után zárolódjanak a tétlen eszközök
- **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**: Itt adhatja meg, hogy hányszor lehet helytelen jelszót megadni, mielőtt a rendszer törölné az eszközről az adatokat
- **Jelszó érvényessége (nap)** : Itt adhatja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát (**1**-**255**)
- **Kötelező jelszótípus**: Itt adhatja meg az eszközön beállítandó jelszó típusát. A következő lehetőségek közül választhat:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Kötelező**
  - **Legalább számok**
  - **Komplex numerikus**: Nem lehet ismétlődő vagy egymást követő számokat megadni, például az „1111”-et vagy az „1234”-et
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Itt adhatja meg, hogy hány új jelszót kell beállítani, mielőtt egy korábbit újból használhatna (**1**-**24**).
- **Ujjlenyomat-feloldás**: válassza a **Letiltás** lehetőséget, hogy a végfelhasználó ne használja az eszköz ujjlenyomat-olvasóját az eszköz zárolásának feloldásához. **Nincs konfigurálva** , lehetővé teszi a felhasználó számára az eszköz zárolásának feloldását ujjlenyomat használatával.
- **Smart Lock és egyéb megbízhatósági ügynökök**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy Smart lock vagy más megbízhatósági ügynökök a kompatibilis eszközökön módosítsák a zárolási képernyő beállításait. Ez a szolgáltatás, más néven megbízhatósági ügynök, lehetővé teszi az eszköz zárolási képernyőjének jelszavának letiltását vagy megkerülését, ha az eszköz megbízható helyen van. Így például megkerülheti a munkahelyi profil jelszavát abban az esetben, ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címke közelében van. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.

### <a name="system-security"></a>Rendszerbiztonság

- **Veszélyforrások vizsgálata az alkalmazásokban**: **megkövetelheti** , hogy az **alkalmazások ellenőrzése** beállítás engedélyezve legyen a munkahelyi és a személyes profilokhoz.

   > [!Note]
   > Ez a beállítás csak Android O vagy újabb rendszerű eszközök esetén érvényesül.

- **A személyes profilban szereplő ismeretlen forrásokból származó alkalmazások telepítésének megakadályozása**: az Android Enterprise Work profiling-eszközök nem telepíthetnek alkalmazásokat a Play áruháztól eltérő forrásokból. Természeténél fogva a munkahelyi profil eszközei a következők:

  - A MDM használatával kezelt munkahelyi profil.
  - A MDM-felügyelettől elkülönített személyes profil.

  Ez a beállítás lehetővé teszi a rendszergazdák számára, hogy az ismeretlen forrásokból származó alkalmazások telepítését jobban szabályozzák. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az alkalmazások telepítése ismeretlen forrásból történjen a személyes profilban. A **Letiltás** megakadályozza az alkalmazások telepítését a személyes profil Play áruháztól eltérő forrásokból.

### <a name="connectivity"></a>Connectivity

- **Mindig bekapcsolt VPN**: Az **Engedélyezés** beállítással a VPN-ügyfél automatikusan csatlakozik és újracsatlakozik a VPN-hez. A mindig bekapcsolt VPN-kapcsolatokkal a kapcsolat folyamatosan fenntartható vagy azonnal elindítható, ha a felhasználó zárolja az eszközét, ha az eszköz újraindul, vagy ha a vezeték nélküli hálózat megváltozik. 

  A mindig bekapcsolt VPN beállítás az összes VPN-ügyfél számára való letiltásához válassza a **Nincs konfigurálva** lehetőséget.

  > [!IMPORTANT]
  > Egy eszközön egyszerre csak egy mindig bekapcsolt VPN-szabályzatot helyezzen üzembe. Több ilyen szabályzat üzembe helyezése egyetlen eszközön nem támogatott.

- **VPN-ügyfél**: Válasszon egy Mindig bekapcsolt állapotot támogató VPN-ügyfelet. A választható lehetőségek:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Hálózatok GlobalProtect
  - Pulse Secure
  - Egyéni
    - **Csomagazonosító**: Adja meg az alkalmazás csomagazonosítóját a Google Play Áruházban. Ha például az áruházban levő alkalmazás URL-címe `https://play.google.com/store/details?id=com.contosovpn.android.prod`, a csomagazonosító `com.contosovpn.android.prod` lesz.

  > [!IMPORTANT]
  > - A kiválasztott VPN-ügyfelet az eszközön kell telepíteni, és támogatnia kell az alkalmazásonkénti VPN-t a munkahelyi profilokban. Ellenkező esetben hiba történik. 
  > - A VPN-ügyfélalkalmazást jóvá kell hagynia a **felügyelt Google Play Áruházban**, szinkronizálnia kell az alkalmazást az Intune-nal, majd üzembe helyeznie az eszközön. Ezt követően az alkalmazás telepítve lesz a felhasználó munkahelyi profiljában.
  > - Ismert problémák merülhetnek fel az alkalmazáson belüli VPN és az F5 Access for Android 3.0.4 használatával. További információért lásd a [F5's kibocsátási megjegyzéseit az F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) számára című témakört.

- **Zárolási mód**: válassza az **Engedélyezés** lehetőséget az összes hálózati forgalom kényszerítéséhez a VPN-alagút használatára. Ha a VPN-kapcsolat nincs kiépítve, az eszköznek nem lesz hálózati hozzáférése.

  A **Nincs konfigurálva** beállítással a forgalom a VPN-alagúton vagy a mobilhálózaton is áthaladhat.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az [Android](device-restrictions-android.md#kiosk) és a [Windows 10 rendszerű](kiosk-settings.md) eszközökhöz is létrehozhat dedikált eszközök kioszk-profilokat.

## <a name="see-also"></a>További információ

[Androidos vállalati eszközök konfigurálása és hibaelhárítása Microsoft Intune](https://support.microsoft.com/help/4476974)
