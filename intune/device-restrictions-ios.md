---
title: iOS-eszközbeállítások a Microsoft Intuneban – Azure | Microsoft Docs
titleSuffix: ''
description: IOS-eszközökön lévő beállítások hozzáadása, konfigurálása vagy létrehozása a funkciók korlátozásához, beleértve a jelszóval kapcsolatos követelmények beállítását, a zárolt képernyő használatát, a beépített alkalmazásokat, a korlátozott vagy jóváhagyott alkalmazások hozzáadását, a Bluetooth-eszközök kezelését, a felhőhöz való kapcsolódást a biztonsági mentéshez és tároláshoz. a kioszk mód engedélyezése, tartományok hozzáadása és annak szabályozása, hogy a felhasználók hogyan használják a Safari böngészőt Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/24/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e31fc3b199f6437bbdd7b12e4be8b17ead689c7e
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71302372"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>iOS-és iPadOS-eszközök beállításai az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk az iOS-és iPadOS-eszközökön szabályozható különböző beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, beállíthatja a jelszavas szabályokat, engedélyezheti vagy korlátozhatja az egyes alkalmazásokat, és így tovább.

Ezek a beállítások hozzáadódnak az Intune-ban az eszköz konfigurációs profiljához, majd az iOS-eszközökhöz vannak rendelve vagy telepítve.

> [!TIP]
> Ezek a beállítások az Apple MDM beállításait használják. További információ ezekről a beállításokról: az [Apple mobileszköz-kezelési beállításai](https://support.apple.com/guide/mdm/welcome/web) (az Apple webhelyén nyílik meg).

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz-korlátozási konfigurációs profilt](device-restrictions-configure.md).

> [!NOTE]
> Ezek a beállítások a különböző regisztrációs típusokra vonatkoznak, és egyes beállítások az összes regisztrációs lehetőségre érvényesek. A különböző regisztrációs típusokkal kapcsolatos további információkért lásd: [iOS-regisztráció](ios-enroll.md).

## <a name="general"></a>Általános

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Használati adatok megosztása**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy az eszköz diagnosztikai és használati adatokat küldjön az Apple-nek. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt az adatküldés.

- **Képernyőfelvétel**: A **Letiltás** elemre kattintva megakadályozhatja a képernyőképek vagy képernyőfelvételek készítését az eszközön. Az iOS 9,0-es és újabb verzióiban blokkolja a képernyőfelvételeket is. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy képként vagy videóként rögzítse a képernyő tartalmát.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- Nem **megbízható TLS-tanúsítványok**: A **Letiltás** elem kiválasztásával megakadályozhatja a nem megbízható TRANSPORT Layer Security (TLS) tanúsítványait az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a TLS-tanúsítványokat.
- **A-Air PKI-frissítések engedélyezése**: Az **Engedélyezés** lehetővé teszi, hogy a felhasználók szoftverfrissítéseket kapjanak az eszközök számítógéphez való csatlakoztatása nélkül.
- **Ad-követés korlátozása**: Válassza a **korlát** lehetőséget az eszköz hirdetési azonosítójának letiltásához. **Nincs konfigurálva** (alapértelmezés) továbbra is engedélyezve van.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Diagnosztika-küldési beállítások módosítása**: A **Letiltás** megakadályozza, hogy a felhasználó módosítsa a diagnosztikai és az alkalmazás-elemzési beállításokat a **diagnosztika és használat** (eszközbeállítások) beállításban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa az eszközbeállítások beállításait.

  Ha ezt a beállítást szeretné használni, állítsa a **megosztás használati adatok** beállítást a **blokkolás**értékre.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS-9.3.2 és újabb verziók

- **A távoli képernyő megfigyelése az osztályterem alkalmazásban**: A **Letiltás** elemre kattintva megakadályozhatja, hogy az osztályterem alkalmazás távolról megtekintse a képernyőt az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az Apple tanterem alkalmazás számára a képernyő megtekintését.

  Ha ezt a beállítást szeretné használni, állítsa a **képernyőfelvétel** beállítást a **blokkolás**értékre.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 9,3 és újabb verziók

- Nem megjelenő **képernyő-megfigyelés az osztályterem alkalmazásban**: Ha **engedélyezve**van, a tanárok a tanulók ismeretei nélkül, az osztályterem alkalmazással csendesen megfigyelheti a tanulók számára készült iOS-eszközök képernyőjét. Az osztályterem alkalmazással az osztályban regisztrált tanulói eszközök automatikusan engedélyt adnak a tanfolyam oktatójának. **Nincs konfigurálva** (alapértelmezés) megakadályozza ezt a funkciót.

  Ha ezt a beállítást szeretné használni, állítsa a **képernyőfelvétel** beállítást a **blokkolás**értékre.

- **Vállalati alkalmazás megbízhatósága**: Kattintson a **Letiltás** elemre, ha el szeretné távolítani a **megbízható vállalati fejlesztő** gombot a beállítások > Általános > profilok & eszközkezelés az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy megbízzon az alkalmazás-áruházból letöltött alkalmazások megbízhatóságának megválasztásában.
- **Fiók módosítása**: Ha a **blokkolás**értékre van állítva, a felhasználó nem tudja frissíteni az eszközre vonatkozó beállításokat az iOS-beállítások alkalmazásból. A felhasználó például nem tud új fiókokat létrehozni, vagy módosítani a felhasználónevet vagy a jelszót. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók megváltoztassák ezeket a beállításokat.

  Ez a funkció az iOS-beállítások alkalmazásból elérhető beállításokra is vonatkozik, például a levelezés, a névjegyek, a naptár, a Twitter stb. Ez a funkció nem vonatkozik azokra az alkalmazásokra, amelyek olyan Fiókbeállítások, amelyek nem konfigurálhatók az iOS-beállítások alkalmazásból, például a Microsoft Outlook alkalmazásból.

- **Képernyő időpontja**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók saját korlátozásokat állítsanak be a képernyő időpontjában (eszközbeállítások). A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználó az eszközön korlátozásokat (például szülői vezérlőket, tartalmakat és adatvédelmi korlátozásokat) konfiguráljon az eszközön.

  A rendszer átnevezte ezt a beállítást, mert **engedélyezte a korlátozásokat az eszközbeállítások között**. A változás hatása:  
  
  - iOS-11.4.1 és korábbi verziók: A **Letiltás** megakadályozza, hogy a végfelhasználók saját korlátozásokat állítsanak be az eszközbeállítások számára. A viselkedés ugyanaz; és nincsenek változások a végfelhasználók számára.
  - iOS 12,0 és újabb verziók: A **Letiltás** beállítás megadásával megakadályozható, hogy a végfelhasználók saját **képernyős időt** állítsanak be az eszközbeállítások között (Beállítások > Általános > képernyőn), beleértve a tartalom-és adatvédelmi korlátozásokat is. Az iOS 12,0-re frissített eszközök többé nem látják a korlátozások lapot az eszközbeállítások esetében (Beállítások > Általános > eszközkezelés > felügyeleti profil > korlátozásai). Ezek a beállítások a **képernyőn**jelennek meg.
  
- Az **összes tartalom és beállítás törlésére szolgáló beállítás használata az eszközön**: Válassza a **Letiltás** lehetőséget, hogy a felhasználók ne tudják használni az összes tartalom és beállítás törlése beállítást az eszközön. **Nincs konfigurálva** (alapértelmezés) hozzáférést biztosít a felhasználóknak ezekhez a beállításokhoz.
- **Eszköz nevének módosítása**: Válassza a **Letiltás** lehetőséget, hogy az eszköz neve nem módosítható. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa az eszköz nevét.
- **Értesítési beállítások módosítása**: Válassza a **Letiltás** lehetőséget, hogy az értesítési beállítások ne legyenek módosítva. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa az eszköz értesítési beállításait.
- **Háttérkép módosítása**: A **blokk** megakadályozza a háttérkép módosítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa az eszköz háttérképét.
- **Vállalati alkalmazások megbízhatósági beállításainak módosítása**: A **Letiltás** megakadályozza, hogy a felhasználó módosítsa a vállalati alkalmazás megbízhatósági beállításait a felügyelt eszközökön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára az alkalmazás-áruházból letöltött alkalmazások megmegbízhatóságát.
- **Konfigurációs profil módosítása**: A **blokk** megakadályozza a konfigurációs profil módosítását az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a konfigurációs profilok telepítését.
- **Aktiválási zár**: Válassza az **Engedélyezés lehetőséget** az aktiválási zár felügyelt iOS-eszközökön való engedélyezéséhez. A Aktiválási zár megnehezíti az elveszett vagy ellopott eszközök újraaktiválását.
- **Alkalmazás eltávolításának tiltása**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók eltávolítsanak alkalmazásokat. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók eltávolítsanak alkalmazásokat az eszközről.
- **Blokkolja az USB-korlátozásos üzemmódot**: Válassza a **Letiltás** lehetőséget a felügyelt eszközökön lévő USB-korlátozott mód letiltásához. Az USB-Korlátozásos mód megakadályozza, hogy az USB-kiegészítők az adatok cseréjét egy órán át zárolt eszközre korlátozzák. **Nincs konfigurálva** (alapértelmezés) engedélyezi az USB-korlátozott üzemmódot.
- **Automatikus dátum és idő kényszerítése**: Kényszerített felügyelt eszközök **megkövetelése** a dátum & idő automatikus beállításához. Az eszköz időzónája frissül, amikor az eszköz mobil kapcsolattal rendelkezik, vagy engedélyezve van a Wi-Fi és a Location Services.
- A **tanulóknak engedélyt kell kérniük az osztályterem tanfolyam elhagyására**: **Megkövetelheti** , hogy a tanulók az osztályterem alkalmazással egy nem felügyelt tanfolyamon regisztrálják a tanfolyamot, hogy engedélyt kérjenek a tanártól a kurzus elhagyása érdekében. **Nincs konfigurálva** (alapértelmezés) nem kényszeríti a tanulót, hogy kérjen engedélyt.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,3 és újabb verziók

- **Az osztályterem zárolásának engedélyezése az alkalmazáshoz és az eszköz zárolása az értesítés nélkül**: Az **Engedélyezés** lehetővé teszi, hogy a tanár zárolja az alkalmazásokat, vagy zárolja az eszközt az osztályterem alkalmazással anélkül, hogy a tanulót kéri. Az alkalmazások zárolása azt jelenti, hogy az eszköz csak a tanár által megadott alkalmazásokat fér hozzá. **Nincs konfigurálva** (alapértelmezés) megakadályozza, hogy a tanárok az osztályterem alkalmazással zárolják az alkalmazásokat vagy eszközöket a tanulók értesítése nélkül. 

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

- **Tantermi osztályok automatikus csatlakoztatása rákérdezés nélkül**: Az **engedélyezése** automatikusan lehetővé teszi a tanulók számára, hogy az osztályterem alkalmazásban található osztályhoz csatlakozzanak a tanár megkérdezése nélkül. **Nincs konfigurálva** (alapértelmezés) arra kéri a tanárt, hogy a tanulók az osztályterem alkalmazásban lévő osztályhoz csatlakozzanak.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

- **VPN-létrehozás tiltása**: A **Letiltás** megakadályozza, hogy a felhasználók VPN-konfigurációs beállításokat hozzanak létre. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók VPN-eket hozzanak létre az eszközön.
- **ESIM beállításainak módosítása**: A **Letiltás** megakadályozza, hogy a felhasználók egy mobil csomagot távolítanak el vagy adjanak hozzá az eszköz eSIM. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók megváltoztassák ezeket a beállításokat.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 12,1 és újabb verziók

- **Szoftverfrissítések késleltetése**: Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a szoftverfrissítések az eszközön jelennek meg, ahogy az Apple kiadják őket. Ha például egy iOS-es frissítést az Apple adott időpontban szabadít fel, akkor ez a frissítés természetesen az eszközön jelenik meg a kiadási dátum körül.

  Az **Engedélyezés** beállítás megadásával késleltetheti, hogy a szoftverfrissítések mikor jelenjenek meg az eszközökön, 0-90 nap múlva. Ez a beállítás nem szabályozza, hogy a frissítések Mikor vagy nincsenek telepítve. 

  - **Szoftverfrissítések láthatóságának késleltetése**: 0-90 napos értéket adjon meg. Ha a késleltetés lejár, a felhasználók értesítést kapnak, hogy az operációs rendszer legkorábbi verziójára frissítsen a késleltetés elindításakor.

    Ha például az iOS 12. a a **január 1-jén**érhető el, és a **késleltetési láthatóság** értéke **5 nap**, akkor az iOS 12. a nem jelenik meg elérhető frissítésként a végfelhasználói eszközökön. A kiadást követő **hatodik napon** a frissítés elérhető lesz, és a végfelhasználók is telepíthetik azt.

    Ez a beállítás a következőkre vonatkozik:  
    - iOS 11,3 és újabb verziók

## <a name="password"></a>Windows 10

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Jelszó**: **Kérje** meg a végfelhasználót, hogy adjon meg egy jelszót az eszköz eléréséhez. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók jelszó megadása nélkül férhessenek hozzá az eszközhöz.
  - **Egyszerű jelszavak**: A **Letiltás** elemre kattintva összetettebb jelszavakat igényelhet. A **nincs konfigurálva** beállítás lehetővé teszi az egyszerű `0000` jelszavak `1234`használatát, például a és a.
  - **Szükséges jelszó típusa**: Válassza ki a szervezet által igényelt jelszó típusát. A választható lehetőségek:
    - **Eszköz alapértelmezése**
    - **Numerikus**
    - **Alphanumeric**
  - **Nem alfanumerikus karakterek száma a jelszóban**: Adja meg a szimbólum karaktereinek `#` számát (például vagy `@`), amelynek szerepelnie kell a jelszóban.
  - **Jelszó minimális hossza**: Adja meg a minimális hosszt, amelyet a felhasználónak 4 és 14 karakter között kell megadnia. A felhasználó által regisztrált eszközökön adjon meg egy 4 és 6 karakter közötti hosszúságot.
  
    > [!NOTE]
    > A felhasználó által beléptetett eszközök esetében:
    >  - Ha egy meglévő PIN-kód 6 karakternél nagyobb, akkor a rendszer csak az első 6 karaktert használja. Ha például a PIN `12345678`-kód, a PIN-kód lerövidítve. `123456`
    >  - Ha a felhasználók 6 karakternél hosszabb új PIN-kódot ad meg, akkor csak az első 6 karaktert használja a rendszer. Ha például PIN-kódot ad `12345678` meg, a PIN-kód lerövidítve `123456`lesz.

  - **Sikertelen bejelentkezések száma az eszköz törlése előtt**: Adja meg az eszköz törlése előtt engedélyezni kívánt sikertelen bejelentkezések számát (4-11).
  
    az iOS beépített biztonságot tartalmaz, amely hatással lehet erre a beállításra. Előfordulhat például, hogy az iOS késlelteti a szabályzat aktiválását a bejelentkezési hibák számától függően. Azt is fontolóra veheti, hogy ismételten ugyanazzal a PIN-kóddal adja meg ugyanazt a jelszót, mint egy kísérletet. Az Apple [IOS-alapú biztonsági útmutatója](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (az Apple webhelyének megnyitása) jó erőforrás, és pontosabb részleteket biztosít a PIN-kódokról.
  
  - **A képernyő zárolása utáni maximális percek a jelszó megadása előtt** <sup>1</sup>: Adja meg, hogy az eszköz mennyi ideig maradjon üresjáratban, mielőtt a felhasználónak újra meg kell adnia a jelszavát. Ha a megadott idő hosszabb az eszközön jelenleg beállított értéknél, akkor az eszköz figyelmen kívül hagyja a beírt időt. IOS 8,0 és újabb rendszerű eszközökön támogatott.
  - **A képernyő zárolása legfeljebb ennyi perc inaktivitás** után <sup>1</sup>: Adja meg az eszközön a képernyő zárolása előtt legfeljebb ennyi perc inaktivitás engedélyezett számát. Ha a megadott idő hosszabb az eszközön jelenleg beállított értéknél, akkor az eszköz figyelmen kívül hagyja a beírt időt. Ha a érték **azonnal**be van állítva, a képernyő zárolása az eszköz minimális ideje alapján történik. IPhone-on 30 másodperc. IPaden ez két perc.
  - **Jelszó érvényessége (napokban)** : Adja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát.
  - **Korábbi jelszavak újbóli használatának tiltása**: Adja meg, hogy hány új jelszót kell használni, amíg egy régit újra fel nem használ.
  - **Touch ID és Face ID feloldása**: Az eszköz zárolásának feloldásához válassza a **Letiltás** lehetőséget, hogy ne használjon ujjlenyomatot vagy arcot. A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználó ezeket a módszereket használja fel az eszköz zárolásának feloldásához.

    A beállítás letiltása azt is megakadályozza, hogy a FaceID hitelesítést használja az eszköz zárolásának feloldásához.

    A Face ID a következőkre vonatkozik:  
    - iOS 11,0 és újabb verziók

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **PIN-kód módosítása**: Válassza a **Letiltás** lehetőséget a jelszó módosításának, hozzáadásának vagy eltávolításának leállításához. A PIN-kódokra vonatkozó korlátozások módosításait a rendszer figyelmen kívül hagyja a felügyelt eszközökön a funkció letiltása után. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a PIN-kódok hozzáadását, módosítását vagy eltávolítását.

  - **Touch ID és Face ID módosítása**: A **Letiltás** leállítja a felhasználótól a Touch ID ujjlenyomatok és a Face ID módosítását, hozzáadását vagy eltávolítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó frissítse a Touch ID ujjlenyomatait és a Face ID-t az eszközön.

    Ha letiltja ezt a beállítást, a felhasználó FaceID-hitelesítés módosítását, hozzáadását vagy eltávolítását is megakadályozza.

    A Face ID a következőkre vonatkozik:  
    - iOS 11,0 és újabb verziók

- **Jelszó automatikus**kitöltésének tiltása: A **Letiltás** lehetőség kiválasztásával megakadályozhatja az automatikus kitöltés jelszava funkció használatát iOS rendszeren. A **blokk** kiválasztása a következő hatással is van:

  - A felhasználók nem kérik a mentett jelszavak használatát a Safariban vagy bármely alkalmazásban.
  - Az automatikus erős jelszavak le vannak tiltva, és az erős jelszavakat nem javasoljuk a felhasználók számára.

  **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a funkciókat.

- **Jelszó-közelségi kérelmek letiltása**: Válassza a **Letiltás** lehetőséget, hogy a felhasználó eszköze ne kérjen jelszavakat a közeli eszközökről. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a jelszavakra vonatkozó kérelmeket.
- **Jelszó megosztásának letiltása**: A **Letiltás** megakadályozza a jelszavak megosztását az eszközök között a AirDrop használatával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszavak megosztását.
- **A jelszó-vagy hitelkártya-adatok automatikus kitöltésének megkövetelése a Touch ID vagy a Face ID hitelesítéshez**: A **kötelező**beállításhoz a felhasználóknak a Touch ID vagy a FaceID használatával kell hitelesíteniük magukat, mielőtt a jelszavak vagy a hitelkártya adatai automatikusan kitölthetők a Safariban és más alkalmazásokban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a funkció vezérlését az eszközbeállítások között.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók
  
<sup>1</sup> Ha a képernyő zárolása ennyi **perc inaktivitás** után és a **Képernyő zárolása után legfeljebb perccel a jelszó megadása után beállítás van** beállítva, akkor azokat a rendszer sorrend szerint alkalmazza. Ha például mindkét beállítás értékét **5** percre állítja be, a képernyő öt perc elteltével automatikusan kikapcsol, és az eszköz további öt perc múlva zárolva lesz. Ha azonban a felhasználó manuálisan kapcsolja ki a képernyőt, azonnal a második beállítás lesz alkalmazva. Ugyanebben a példában azt követően, hogy a felhasználó kikapcsolta a képernyőt, öt perccel később zárolja az eszközt.

## <a name="locked-screen-experience"></a>Zárolási képernyő felülete

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Vezérlési központ hozzáférése az eszköz zárolt állapotában**: A **Letiltás** elemre kattintva megakadályozhatja a hozzáférését a Control Center alkalmazáshoz, amíg az eszköz zárolva van. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók hozzáférjenek a vezérlési központ alkalmazáshoz, amikor az eszköz zárolva van.
- **Értesítések az eszköz zárolt állapotában**: A **blokk** megakadályozza az értesítések elérését az eszköz zárolt állapotában. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó az eszköz zárolásának feloldása nélkül hozzáférjen az értesítésekhez.
- **Ma nézet, ha az eszköz zárolva**van: A **blokk** megakadályozza a ma nézethez való hozzáférést, ha az eszköz zárolva van. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy megtekintse a mai nézetet, amikor az eszköz zárolva van.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Mobiltárca-értesítések az eszköz zárolt állapotában**: A **blokk** megakadályozza, hogy a rendszer zárolja az eszközt a mobiltárca alkalmazáshoz. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó hozzáférjen a mobiltárca alkalmazáshoz, amíg az eszköz zárolva van.

## <a name="app-store-doc-viewing-gaming"></a>Alkalmazás-áruház, dokumentumok megtekintése, játékok

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Vállalati dokumentumok megtekintése a nem felügyelt alkalmazásokban**: A **blokk** megakadályozza a vállalati dokumentumok megtekintését a nem felügyelt alkalmazásokban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a vállalati dokumentumok bármely alkalmazásban való megtekintését. Tegyük fel például, hogy meg szeretné akadályozni, hogy a felhasználók fájlokat mentsenek a OneDrive alkalmazásból a Dropboxba. Állítsa be ezt a beállítást **blokkként**. Miután az eszköz megkapja a házirendet (például újraindítás után), az már nem teszi lehetővé a mentést.

  - Nem **felügyelt alkalmazások olvasásának engedélyezése a felügyelt névjegyek fiókjaiból**: Ha **engedélyezve**van, a nem felügyelt alkalmazások, például a beépített iOS-névjegyek alkalmazás, a felügyelt alkalmazásokból származó kapcsolattartási adatokat, például az Outlook Mobile alkalmazást is beolvashatja és elérheti. **Nincs konfigurálva** (alapértelmezés) megakadályozza az olvasást, beleértve az ismétlődések eltávolítását is az eszköz beépített névjegyek alkalmazásában.  
  
    Ez a beállítás engedélyezi vagy megakadályozza a kapcsolattartási adatok olvasását. Nem szabályozza a kapcsolatok szinkronizálását az alkalmazások között.
  
    Ha ezt a beállítást szeretné használni, állítsa be a **vállalati dokumentumok megtekintése a nem felügyelt alkalmazásokban** beállítást a **blokkoláshoz**.

  További információ erről a két beállításról, valamint az iOS-kapcsolat exportálásának [az Outlookban való hatásáról: támogatási Tipp: Az egyéni Intune-profil beállításait az iOS Native Contacts](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453)alkalmazással használhatja.

- **AirDrop kezelése nem felügyelt célhelyként**: A **kényszerített** AirDrop nem felügyelt eldobási célpontnak tekintendők. Leállítja a felügyelt alkalmazások számára az adatok küldését a AirDrop használatával. 
- **Nem vállalati dokumentumok megtekintése a vállalati alkalmazásokban**: A **blokk** megakadályozza a nem vállalati dokumentumok megtekintését a vállalati alkalmazásokban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a dokumentumok megtekinthetők legyenek a vállalat által felügyelt alkalmazásokban.

  A **Letiltás** beállítás meggátolja a kapcsolatfelvételt az iOS-ben az Outlookban. További információkért lásd [a támogatási tippet: Az Outlook iOS-kapcsolat szinkronizálásának engedélyezése a](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453)IOS12 Mdm-vezérlőkkel.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **ITunes Store-jelszó megkövetelése az összes vásárláshoz**: **A felhasználónak** meg kell adnia az Apple ID jelszót minden alkalmazásbeli vagy iTunes-vásárláshoz. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a vásárlásokat anélkül, hogy minden alkalommal jelszót kellene megkérnie.
- **Alkalmazáson belüli vásárlások**: A **blokk** gombra kattintva megakadályozhatja az alkalmazáson belüli vásárlásokat az áruházból. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy egy futó alkalmazás tárolja az áruházbeli vásárlásokat.
- **Tartalom letöltése az iBooks áruházból "Erotika" jelöléssel**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók a "Erotika" címkével ellátott adathordozóról töltsenek le médiatartalmakat. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó könyveket töltsön le az "Erotika" kategóriával.
- **Névjegyek írásának engedélyezése a felügyelt alkalmazásoknak a nem felügyelt névjegyek fiókjai**számára: Ha **engedélyezve**van, a felügyelt alkalmazások, például az Outlook Mobile alkalmazás, a beépített iOS Contacts alkalmazásba menthetik vagy szinkronizálhatják a kapcsolattartási adatokat, beleértve az üzleti és vállalati kapcsolatokat is. Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a felügyelt alkalmazások nem tudják menteni vagy szinkronizálni a kapcsolattartási adatokat az eszköz beépített iOS Contacts alkalmazásával.
  
  Ha ezt a beállítást szeretné használni, állítsa be a **vállalati dokumentumok megtekintése a nem felügyelt alkalmazásokban** beállítást a **blokkoláshoz**.

- **Minősítési régió**: Válassza ki az engedélyezett letöltésekhez használni kívánt minősítési régiót. Majd válassza ki a **filmek**, **tévéműsorok**és **alkalmazások**engedélyezett minősítéseit.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **App Store**: A **blokk** megakadályozza a felügyelt eszközökön az alkalmazás-áruház elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

  - **Alkalmazások telepítése az App Store-ból**: A **Letiltás** elemre kattintva blokkolhatja az App Store-t az eszköz kezdőképernyő képernyőjéről. A végfelhasználók továbbra is használhatják az iTunest vagy az Apple Configurator eszközt alkalmazások telepítésére. **Nincs konfigurálva** (alapértelmezés) engedélyezi az App Store-t a kezdőképernyőn.
  - **Alkalmazások automatikus letöltése**: A **blokkolás** gombra kattintva megakadályozhatja a más eszközökön vásárolt alkalmazások automatikus letöltését. Nem érinti a meglévő alkalmazások frissítéseit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi más iOS-eszközökön vásárolt alkalmazások letöltését az eszközön.

- **Kifejezetten iTunes zene, podcast vagy Hírek tartalma**: A **Letiltás** elem kiválasztásával megakadályozhatja az iTunes zene-, podcast-vagy hírforrás-tartalmait. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az eszköz számára, hogy az áruházból származó felnőttként értékelje a tartalmat. az iOS 13 és újabb verziókhoz csak felügyelt eszközökre lehet szükség. 

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Game Center ismerősök hozzáadása**: A **Letiltás** megakadályozza, hogy a felhasználók Game Center barátokat adjanak hozzá. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a barátok hozzáadását Game Center.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Game Center**: A Game Center alkalmazás használatának **tiltása** . **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Game Center alkalmazás használatát az eszközön.
- **Többrésztvevős játékok**: A többrésztvevős játékok elkerüléséhez válassza a **Letiltás** lehetőséget. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó többrésztvevős játékokat játsszon az eszközön.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

## <a name="built-in-apps"></a>Beépített alkalmazások

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Siri**: A **Letiltás** megakadályozza a Siri elérését. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az eszközön a Siri Voice Assistant használatát.
  - **Siri, ha az eszköz zárolva van**: Válassza a **Letiltás** lehetőséget a Siri elérésének megakadályozásához, ha az eszköz zárolva van. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az eszközön a Siri Voice Assistant használatát, ha zárolva van.

- A **Safari csalások elleni figyelmeztetései**: Csalással kapcsolatos figyelmeztetések megjelenítésének **megkövetelése** az eszköz böngészőjében. A **Nincs konfigurálva** (alapértelmezett) érték letiltja a funkciót.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Spotlight-keresés az internetről származó eredmények visszaküldéséhez**: A **Letiltás** megszakítja a reflektorfényben az internetes keresésből származó eredmények visszaadását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Spotlight-keresés kapcsolódását az internethez a keresési eredmények biztosítása érdekében.

- **Safari cookie-k**: Válassza ki, hogy a cookie-k hogyan legyenek kezelve az eszközön. A választható lehetőségek:
  - Allow
  - Az összes cookie letiltása
  - Cookie-k engedélyezése a felkeresett webhelyekről
  - Cookie-k engedélyezése a jelenlegi webhelyről

- **Safari JavaScript**: A **Letiltás** megakadályozza, hogy a böngészőben futó Java-parancsfájlok fussanak az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a Java-parancsfájlokat.

- **Safari előugró ablakok**: **Blokkolja** az előugró ablakok blokkolását a böngészőben. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az előugró ablak blokkolását.

- **Kiszolgálóoldali naplózás a Siri-parancsokhoz**: Ha a **Letiltás**értékre van állítva, a kiszolgálóoldali Siri-naplózás ki van kapcsolva. Emellett megakadályozhatja a felhasználói kérések naplózását a Siri-kiszolgálókon. **Nincs konfigurálva** (alapértelmezés) naplózza a-kiszolgálón található Siri-parancsokat. Ez a beállítás nem függ attól, hogy a Siri-beállítás le van tiltva vagy nincs konfigurálva.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 12,2 és újabb verziók

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Kamera**: Válassza a **Letiltás** lehetőséget a kamera elérésének megakadályozásához az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi az eszköz kamerájának elérését.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

  - **FaceTime**: **Blokkolja** a FaceTime-alkalmazáshoz való hozzáférés megakadályozását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a FaceTime alkalmazás elérését az eszközön.

    Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Siri-káromkodás szűrője**: Meg **kell** akadályozni, hogy a Siri megdiktálja vagy megbeszélje a káromkodás nyelvét.

  Ha ezt a beállítást szeretné használni, állítsa a **Siri** beállítást a **Letiltás**értékre.

- **A felhasználó által létrehozott tartalom lekérdezése az internetről**: A **Letiltás** megakadályozza, hogy a Siri hozzáférjen a webhelyekhez a kérdések megválaszolásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a Siri hozzáférjen a felhasználó által létrehozott tartalomhoz az internetről.

  Ha ezt a beállítást szeretné használni, állítsa a **Siri** beállítást a **Letiltás**értékre.

- **Apple News**: Válassza a **Letiltás** lehetőséget a Apple News alkalmazás elérésének megakadályozásához az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az Apple News alkalmazás használatát.
- **iBooks Store**: A **blokk** megakadályozza az iBooks tároló elérését. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak az iBooks áruházból származó könyvek tallózását és megvásárlását.
- **Üzenetek alkalmazás az eszközön**: A **Letiltás** megakadályozza, hogy a felhasználók a iMessage üzenetek alkalmazást használják. Ha az eszköz támogatja a szöveges üzenetküldést, akkor a felhasználó SMS-sel továbbra is küldhet és fogadhat szöveges üzeneteket. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az üzenetek alkalmazás számára az üzenetek küldését és olvasását az interneten keresztül.
- **Podcastok**: A **blokk** megakadályozza, hogy a felhasználók a Podcasts alkalmazást használják. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a podcastok alkalmazás használatát.
- **Music szolgáltatás**: A **Block** a Music alkalmazást klasszikus módra vált, és letiltja a Music szolgáltatást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az Apple Music alkalmazás használatát.
- **iTunes Radio szolgáltatás**: A **Letiltás** megakadályozza, hogy a felhasználók az iTunes Radio alkalmazást használják. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az iTunes Radio alkalmazás használatát.
- **iTunes Store**: **Nincs konfigurálva** (alapértelmezés) engedélyezi az iTunes használatát az eszközökön. A **Letiltás** megakadályozza, hogy a felhasználók az iTunes-ot használják az eszközön. 

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 4,0 és újabb verziók

- **Az iPhone megkeresése**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az alkalmazás megkeresése funkció használatával beolvassa az eszköz hozzávetőleges helyét. A **Letiltás** megakadályozza a funkció megkeresését a saját alkalmazásban. 

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és iPadOS 13,0 és újabb

- **Ismerősök megkeresése**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az alkalmazás megkeresése funkció használatával megkeresse a családot és a barátokat egy Apple-eszközről vagy iCloud.com. A **Letiltás** megakadályozza a funkció megkeresését a saját alkalmazásban.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és iPadOS 13,0 és újabb

- **Barátok keresése alkalmazás beállításainak módosítása**: A **blokk** megakadályozza a barátok alkalmazás beállításainak módosítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a barátok keresése alkalmazás beállításainak módosítását.

- **Spotlight-keresés az internetről származó eredmények visszaküldéséhez**: A **Letiltás** megszakítja a reflektorfényben az internetes keresésből származó eredmények visszaadását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Spotlight-keresés kapcsolódását az internethez a keresési eredmények biztosítása érdekében.

- **Rendszeralkalmazások eszközről való eltávolításának tiltása**: A **Letiltás** lehetőség kiválasztásával letilthatja a rendszeralkalmazások eltávolítását az eszközről. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a rendszeralkalmazások eltávolítását.

- **Safari**: A Safari böngésző használatának **letiltása** az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók a Safari böngészőt használják.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Safari automatikus kitöltés**: A **Letiltás** letiltja az eszközön a Safari automatikus kitöltés szolgáltatását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a webböngésző automatikus kiegészítési beállításainak módosítását.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

## <a name="restricted-apps"></a>Korlátozott alkalmazások

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **A korlátozott alkalmazások listájának típusa**: Hozza létre azon alkalmazások listáját, amelyeket a felhasználók nem telepíthetnek és nem használhatnak. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): Az Intune-ban nincsenek korlátozások. A felhasználók hozzáférhetnek a hozzárendelt alkalmazásokhoz és a beépített alkalmazásokhoz.
  - **Tiltott alkalmazások**: Az Intune által nem felügyelt alkalmazásokat, amelyeket nem szeretne telepíteni az eszközre. A felhasználók nem akadályozzák meg a tiltott alkalmazások telepítését. Ha azonban a felhasználó a listából telepít egy alkalmazást, az az Intune-ban szerepel.
  - **Jóváhagyott alkalmazások**: Azok az alkalmazások, amelyeket a felhasználók telepíthetnek. A felhasználók nem telepíthetnek olyan alkalmazásokat, amelyek nem szerepelnek a felsorolásban. Az Intune által kezelt alkalmazások automatikusan engedélyezettek. A felhasználók nem akadályozzák meg a jóváhagyott listán nem szereplő alkalmazások telepítését. De ha igen, az Intune-ban jelentett jelentés.

Ha alkalmazásokat szeretne hozzáadni a listához, a következőket teheti:

- **Adja hozzá** a kívánt alkalmazás iTunes App Store áruházbeli URL-címét. Például a Microsoft munkahelyi mappák alkalmazás hozzáadásához írja be `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` a következőt: vagy. `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

  Az alkalmazás URL-címének megkereséséhez nyissa meg az iTunes App Store áruházat, és keresse meg az alkalmazást. Keressen például a `Microsoft Remote Desktop` vagy `Microsoft Word`a kifejezésre. Válassza ki az alkalmazást, és másolja az URL-címet.

  Az iTunes használatával is megkeresheti az alkalmazást, majd a **hivatkozás másolása** feladat használatával beolvashatja az alkalmazás URL-címét.

- **Importáljon** egy CSV-fájlt az alkalmazás részleteivel, beleértve az URL-címet is. Használja a következő formátumot: `<app url>, <app name>, <app publisher>`. Vagy **exportáljon** egy meglévő listát, amely tartalmazza a korlátozott alkalmazások listáját ugyanabban a formátumban.

> [!IMPORTANT]
> A korlátozott alkalmazás-beállításokat használó eszközöket felhasználói csoportokhoz kell rendelni.

## <a name="show-or-hide-apps"></a>Alkalmazások megjelenítése vagy elrejtése

Az iOS 9,3-es vagy újabb verzióját futtató eszközökre vonatkozik.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Alkalmazások típusa**: A megjelenítendő vagy elrejteni kívánt alkalmazások listájának létrehozása. A választható lehetőségek:

  - **Rejtett alkalmazások**: Adja meg azoknak az alkalmazásoknak a listáját, amelyek rejtve vannak a felhasználók elől. A felhasználók nem tekinthetik meg és nem nyitják meg ezeket az alkalmazásokat.
  - **Látható alkalmazások**: Adja meg a felhasználók által megtekinthető és elindítható alkalmazások listáját. Ezeken kívül a felhasználók más alkalmazásokat nem látnak és nem indíthatnak el.

- **Alkalmazás URL-címe**: Adja meg a megjeleníteni vagy elrejteni kívánt alkalmazás áruházbeli alkalmazásának URL-címét. Példa:

  - A Microsoft munkahelyi mappák alkalmazás hozzáadásához írja be `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` a `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`következőt: vagy. 

  - A Microsoft Word alkalmazás hozzáadásához írja be `https://itunes.apple.com/de/app/microsoft-word/id586447913` a `https://apps.apple.com/de/app/microsoft-word/id586447913`következőt: vagy.

  Az alkalmazás URL-címének megkereséséhez nyissa meg az iTunes App Store áruházat, és keresse meg az alkalmazást. Keressen például a `Microsoft Remote Desktop` vagy `Microsoft Word`a kifejezésre. Válassza ki az alkalmazást, és másolja az URL-címet.

  Az iTunes használatával is megkeresheti az alkalmazást, majd a **hivatkozás másolása** feladat használatával beolvashatja az alkalmazás URL-címét.
  
  A csomagok AZONOSÍTÓjának megkeresésével kapcsolatos további információkért lásd: [az iOS-alkalmazások csomag-azonosítójának megkeresése](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- Alkalmazáscsomag **azonosítója**: Adja meg a kívánt alkalmazás alkalmazáscsomag- [azonosítóját](bundle-ids-built-in-ios-apps.md) . Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Alkalmazás neve**: Adja meg a kívánt alkalmazás nevét. Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Közzétevő**: Adja meg a kívánt alkalmazás közzétevőjét.

Alkalmazások hozzáadásához a következőket teheti:

- **Hozzáadás**: Válassza a lehetőséget az alkalmazások listájának létrehozásához.
- **Importáljon** egy CSV-fájlt az alkalmazás részleteivel, beleértve az URL-címet is. Használja a következő formátumot: `<app url>, <app name>, <app publisher>`. Vagy az **Exportálás** gombra kattintva hozzon létre egy listát a hozzáadott korlátozott alkalmazások listájáról, ugyanebben a formátumban.

## <a name="wireless"></a>Vezeték nélküli

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Adatroaming**: A **Letiltás** elemre kattintva megakadályozhatja az adatroamingot a mobil hálózaton. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az adatroaming használatát, ha az eszköz mobil hálózaton van.
- **Globális háttérbeli beolvasás barangolás közben**: A **Letiltás** megakadályozza a globális háttér-beolvasási funkció használatát a mobil hálózaton való barangolás közben. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz beolvassa az adatfájlokat, például az e-maileket, ha mobil hálózaton barangol.
- **Hangtárcsázás**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja, hogy a felhasználók a hangtárcsázás funkciót használják az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hangtárcsázást az eszközön.
- **Hangroaming**: A **Letiltás** elemre kattintva megakadályozhatja a hangroaming használatát a mobil hálózaton. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hangroaming használatát, ha az eszköz mobil hálózaton van.
- **Személyes hozzáférési**pont: A **Letiltás funkció** minden eszköz szinkronizálásával kikapcsolja a felhasználó eszközén lévő személyes hozzáférési pontokat. Előfordulhat, hogy egyes hálózatüzemeltető szolgáltatók esetében ez a beállítás nem érvényesül. **Nincs konfigurálva** (alapértelmezés) megtartja a személyes hozzáférési pont konfigurációját a felhasználó alapértelmezett beállításaként.
- **Mobil használati szabályok (csak felügyelt alkalmazások esetén)** : Adja meg azokat az adattípusokat, amelyeket a felügyelt alkalmazások használhatnak a mobil hálózatokon. A választható lehetőségek:
  - **A mobil adatmennyiség használatának letiltása**: Letilthatja az **összes felügyelt alkalmazás** cellájának használatát, vagy **választhat adott alkalmazásokat**.
  - **A mobil adatátviteli funkció használatának letiltása barangolás közben**: Letilthatja a mobil adatátvitelt az **összes felügyelt alkalmazás** barangolásakor, vagy **adott alkalmazások kiválasztását**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Az alkalmazás mobil adatfelhasználási beállításainak módosítása**: A **Letiltás** elemre kattintva megakadályozhatja az alkalmazás mobil adatfelhasználási beállításainak módosítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy szabályozza, hogy mely alkalmazások használhatják a mobil-adatszolgáltatásokat.
- **A mobil csomag beállításainak módosításai**: A **Letiltás** megakadályozza, hogy a felhasználók módosítsák a mobil csomag beállításait. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a módosítások elvégzését.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

- **Személyes hozzáférési pont felhasználói módosítása**: Ha a **blokkolás**értékre van állítva, a felhasználó nem módosíthatja a személyes hozzáférési pont beállítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a végfelhasználók számára, hogy engedélyezzék vagy letiltsák a személyes hozzáférési pontokat.

  Ha letiltja ezt a beállítást, és letiltja a **személyes hozzáférési** pont beállítását, a személyes elérési pont ki van kapcsolva.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 12,2 és újabb verziók

- **Csak a konfigurációs profilokat használó Wi-Fi-hálózatok csatlakoztatása**: **Megköveteli** , hogy az eszköz csak az Intune konfigurációs profiljain keresztül beállított Wi-Fi-hálózatokat használja. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz más Wi-Fi-hálózatokat használjon.
- **Wi-Fi állapot módosítása**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók bekapcsolják vagy kikapcsolhatják a Wi-Fi-t az eszközön. A **blokk** megakadályozza a Wi-Fi be-és kikapcsolását.

## <a name="connected-devices"></a>Csatlakoztatott eszközök

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Párosított Apple Watch – csukló-észlelés**: **Megkövetelheti** a párosított Apple Watch használatának kényszerítését a csukló észleléséhez. Ha szükséges, az Apple Watch nem jelenít meg értesítéseket, amikor nem kopott. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- A hanglejátszás **megkövetelése kimenő kérelmek párosítási jelszava**: Párosítási jelszó **megkövetelése** , ha a felhasználó a közvetített tartalmak más Apple-eszközökre való továbbítását is használja. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a tartalom továbbítását a rádió használatával a jelszó beírása nélkül.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **AirDrop**: A **blokk** megakadályozza a AirDrop használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirDrop funkció használatát a tartalmak a közeli eszközökhöz való cseréjéhez.
- **Apple Watch-párosítás**: A **blokk** megakadályozza az Apple Watch párosítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz párosítva legyen egy Apple Watch használatával.
- **Bluetooth-módosítás**: A **Letiltás** leállítja a végfelhasználók számára a Bluetooth-beállítások módosítását az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa ezeket a beállításokat.
- **A gazdagép párosítása az IOS-eszköz által párosítható eszközök vezérléséhez**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a gazdagép párosítását, hogy a rendszergazda vezérelje, hogy az iOS-eszközök mely eszközökhöz tudnak párosítani. A **blokk** megakadályozza a gazdagép párosítását.
- **AirPrint letiltása**: A **Letiltás** lehetőség kiválasztásával megakadályozhatja a AirPrint funkció használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a AirPrint használatát.
  - **AirPrint hitelesítő adatok tárolásának letiltása a kulcstartóban**: A **blokk** megakadályozza a kulcstartó tárolását a Felhasználónév és a jelszó használatával az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirPrint-Felhasználónév és-jelszó tárolását a kulcstartó alkalmazásban.
  - **Megbízható TLS-tanúsítvány megkövetelése a AirPrint**: **Megköveteli** , hogy az eszköz megbízható tanúsítványokat használjon a TLS-nyomtatással való kommunikációhoz.
  - **AirPrint-nyomtatók iBeacon-felderítésének letiltása**: A **Letiltás** megakadályozza, hogy a rosszindulatú AirPrint Bluetooth-figyelőket észlelje a hálózati forgalom számára. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirPrint-nyomtatók reklámozását az eszközön.
- **Új közeli eszközök beállításának letiltása**: A **Letiltás** letiltja a megjelenő új eszközök beállítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy csatlakozzanak más közeli Apple-eszközökhöz.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

## <a name="keyboard-and-dictionary"></a>Billentyűzet és szótár

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Szó definíciójának keresése**: A **Letiltás** megakadályozza, hogy a felhasználó kiemelje a szót, majd megkeresse a definícióját az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hozzáférést a definíciós keresési szolgáltatáshoz.
- **Prediktív billentyűzetek**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a prediktív billentyűzetek használatát arra, hogy a felhasználók számára érdemes szavakat javasolni. A **Letiltás** megakadályozza ezt a funkciót.
- **Automatikus javítás**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz automatikusan javítsa a hibásan írt szavakat. A **tiltás** megakadályozza az automatikus javítást.
- **Billentyűzet helyesírás-ellenőrzés**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a helyesírás-használatot az eszközön. A **Letiltás** lehetővé teszi a helyesírás-ellenőrzőt.
- **Billentyűparancsok**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a billentyűparancsok használatát az eszközön. A **Letiltás** megakadályozza, hogy a felhasználó billentyűparancsokat használjon.
- **Diktálás**: A **Letiltás** leállítja a felhasználótól a hangbemenet használatát szöveg megadásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a diktálási bevitel használatát.
- **QuickPath**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a QuickPath használatát, amely lehetővé teszi a folyamatos bevitelt az eszköz billentyűzetén. A felhasználók a kulcsok szövegének megírásával írhatják be a szavakat. A **Letiltás** megakadályozza, hogy a felhasználók a QuickPath használják. 

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és iPadOS 13,0 és újabb

## <a name="cloud-and-storage"></a>Felhő és tárolás

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Titkosított biztonsági mentés**: Annak **megkövetelése** , hogy az eszközök biztonsági mentését titkosítani kell.
- **Felügyelt alkalmazások szinkronizálása a felhővel**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az Intune számára, hogy az alkalmazásokat szinkronizálja a felhasználó iCloud-fiókjával. A **blokk** megakadályozza az adatszinkronizálást az icloudba.
- **Vállalati könyv biztonsági mentésének letiltása**: A **Letiltás** elem kiválasztásával megakadályozhatja, hogy a felhasználók biztonsági mentést készíthetnek a vállalati könyvekből. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak a könyvek biztonsági mentését.
- **A vállalati könyv metaadatainak szinkronizálásának letiltása (megjegyzések és csúcsfények)** : A **blokk** megakadályozza a jegyzetek és a Kiemelt események szinkronizálását a nagyvállalati könyvekben. **Nincs konfigurálva** (alapértelmezés) engedélyezi a szinkronizálást.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Photo Stream szinkronizálása az icloudba**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy az eszközön lévő **Photo streamet** szinkronizálják az icloudba, és hogy a felhasználó összes eszközén elérhetők legyenek fényképek. A **blokk** megakadályozza, hogy a Photo Stream szinkronizáljon az icloudba. A funkció blokkolása adatvesztést eredményezhet. 
- **ICloud Photo Library**: A **Letiltás** beállítás megadásával letilthatja az iCloud Photo Library használatát a fényképek és videók felhőben való tárolásához. A rendszer eltávolít minden olyan fényképet, amely nincs teljesen letöltve az iCloud Photo Library-ből az eszközre. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az iCloud Photo Library használatát.
- **Megosztott Photo Stream**: Kattintson a **Letiltás** elemre az **iCloud Photo Sharing** eszközön való letiltásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a megosztott fényképek folyamatos átvitelét.
- **Handoff**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy megkezdjék a munkát egy iOS-eszközön, majd folytassa az elindított munkát egy másik iOS-vagy macOS-eszközön. A **blokk** megakadályozza ezt a handoff.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Biztonsági mentés az icloudba**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy biztonsági másolatot készít az eszközről az iCloudba. A **Letiltás** leállítja a felhasználótól, hogy biztonsági másolatot készít az eszközről az icloudba.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **ICloud-dokumentumok szinkronizálásának letiltása**: **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a dokumentumok és a kulcs-érték szinkronizálását az iCloud tárhelyére. A **blokk** megakadályozza, hogy az iCloud szinkronizálja a dokumentumokat és az adatokkal.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **ICloud-kulcstartó szinkronizálásának letiltása**: Válassza a **Letiltás** lehetőséget, ha le szeretné tiltani a kulcstartóban tárolt hitelesítő adatok icloudba való szinkronizálását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy szinkronizálják ezeket a hitelesítő adatokat.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

## <a name="autonomous-single-app-mode"></a>Autonóm Egyalkalmazásos mód

Ezekkel a beállításokkal konfigurálhatja az iOS-es eszközöket adott alkalmazások autonóm Egyalkalmazásos módban való futtatására. Ha ez a mód be van állítva, és az alkalmazás fut, az eszköz zárolva van. Csak ezt az alkalmazást futtathatja. Például hozzáadhat egy olyan alkalmazást, amely lehetővé teszi a felhasználók számára, hogy tesztelje az eszközt. Az alkalmazás használatának befejezésekor vagy a szabályzat eltávolításakor az eszköz visszatér a szokásos állapotába.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Alkalmazás neve**: Adja meg a kívánt alkalmazás nevét.
- Alkalmazáscsomag **azonosítója**: Adja meg a kívánt alkalmazás [köteg-azonosítóját](bundle-ids-built-in-ios-apps.md) .
- **Hozzáadás**: Válassza a lehetőséget az alkalmazások listájának létrehozásához.

Egy CSV-fájlt is **importálhat** az alkalmazások neveinek és a Kötegük azonosítóinak listájával. Vagy **exportáljon** egy meglévő listát, amely tartalmazza az alkalmazásokat.

## <a name="kiosk"></a>Kioszkmód

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- Teljes **képernyős módban futtatandó alkalmazás**: Válassza ki a kioszk módban futtatni kívánt alkalmazások típusát. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A kioszk beállításai nincsenek alkalmazva. Az eszköz nem fut kioszk módban.
  - **Áruházbeli alkalmazás**: Adja meg egy alkalmazás URL-címét az iTunes App Store-ban.
  - **Felügyelt alkalmazás**: Válassza ki az Intune-ba felvett alkalmazást.
  - **Beépített alkalmazás**: Adja meg a beépített alkalmazás [köteg-azonosítóját](bundle-ids-built-in-ios-apps.md) .

- **Kisegítő érintés**: A kisegítő érintés kisegítő beállításának **megkövetelése** az eszközön. Ez a funkció segíti a felhasználók számára, hogy a képernyőn megjelenő kézmozdulatokat nehéz lehet megállapítani. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Színek invertálása**: A színinvertálás kisegítő beállításának **megkövetelése** , hogy a vizualizációt használó felhasználók módosíthatják a megjelenítési képernyőt. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Monó hang**: A Monó hang kisegítő lehetőségének **megkövetelése** az eszközön. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- Hangvezérelt **vezérlés**: A **kötelező** hangvezérlést tesz lehetővé az eszközön, és lehetővé teszi a felhasználók számára az operációs rendszer teljes körű vezérlését a Siri-parancsok használatával. A **nincs konfigurálva beállítás** letiltja a hangvezérlést az eszközön.

  Ez a beállítás a következőkre vonatkozik:  
  - iOS 13,0 és újabb verziók
  - iPadOS 13,0 és újabb verziók
  
  > [!TIP]
  > Ha a szervezete számára elérhető LOB-alkalmazások állnak rendelkezésre, és az iOS 13,0-as verzióban nem állnak készen a **Hangvezérlésre** , akkor azt javasoljuk, hogy **ne konfigurálja**ezt a beállítást.

- **Kommentár**: A kommentár kisegítő beállításának **megkövetelése** az eszközön, hogy hangosan beolvassa a szöveget a képernyőn. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Nagyítás**: A nagyítás beállításának **megkövetelése** az eszközön, hogy a felhasználók érintsenek a nagyításhoz a képernyőn. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Automatikus zárolás**: A **blokk** megakadályozza az eszköz automatikus zárolását. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Csengés kapcsolója**: A **Letiltás** letiltja a csengetési (Mute) kapcsolót az eszközön. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Képernyő elforgatása**: A **blokk** megakadályozza a képernyő tájolásának módosítását, amikor a felhasználó elforgatja az eszközt. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Képernyő alvó gombja**: Kattintson a **Letiltás** gombra a képernyő alvó állapotának letiltásához az eszközön. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Érintés**: A **Letiltás** letiltja az érintőképernyőt az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználó számára az érintőképernyő használatát.
- **Hangerő gombok**: A **Letiltás** megakadályozza a hangerő-szabályozó gombok használatát az eszközön. A **nincs konfigurálva** beállítás engedélyezi a hangerő-szabályozó gombok használatát.
- **Kisegítő érintéses vezérlés**: **Lehetővé teszi** a felhasználók számára a kisegítő érintés funkció használatát. A **nincs konfigurálva beállítás** letiltja ezt a funkciót.
- **Színek invertálása vezérlő**: A színinvertálás módosításának **engedélyezése** a felhasználók számára a színek invertálása funkció beállításához. A **nincs konfigurálva beállítás** letiltja ezt a funkciót.
- **Beszéd a kijelölt szövegen**: A kisegítő lehetőségek kiválasztásának **engedélyezése** az eszközön. Ez a funkció olyan szöveget olvas be, amelyet a felhasználó hangosan választ ki. A **nincs konfigurálva beállítás** letiltja ezt a funkciót.
- **Hangvezérelt módosítás**: Annak **engedélyezése** , hogy a felhasználók megváltoztassák a hangvezérelt vezérlés állapotát az eszközökön. A **nincs konfigurálva beállítás** megakadályozza, hogy a felhasználók megváltoztassák a hangvezérlés állapotát az eszközökön.

  Ez a beállítás a következőkre vonatkozik:  
  - iOS 13,0 és újabb verziók
  - iPadOS 13,0 és újabb verziók

- **Kommentár-vezérlés**: A kommentár módosításának **engedélyezése** a felhasználók számára a kommentár funkció frissítéséhez, például a képernyőn megjelenő szöveg gyors beolvasása. A **nincs konfigurálva beállítás** megakadályozza a kommentárok módosítását.
- **Nagyítási vezérlő**: A felhasználó nagyítási módosításainak **engedélyezése** . A **nincs konfigurálva beállítás** megakadályozza a nagyítás módosítását.

> [!NOTE]
> Az iOS-eszközök Kioszk módra való konfigurálása előtt felügyelt módba kell állítania az eszközt az Apple Configurator eszközzel vagy az Apple Device Enrollment Program készülékregisztráció-kezelővel. Tekintse meg az Apple konfiguráló eszközének használatát ismertető témakört.
> Ha a megadott iOS-alkalmazás a profil hozzárendelését követően települ, az eszköz mindaddig nem lép kioszk módba, amíg az eszköz újra nem indul.

## <a name="domains"></a>Tartományok

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Jelöletlen e-mail-tartományok** > **e-mail tartományának URL-címe**: Adjon hozzá egy vagy több URL-címet a listához. Ha a végfelhasználók a megadott tartománytól eltérő tartományból kapnak e-mailt, az iOS-es mail alkalmazásban az e-mail nem megbízhatóként van megjelölve.

- **Felügyelt webtartományok** > **webes tartományának URL-címe**; Adjon hozzá egy vagy több URL-címet a listához. Ha a rendszer letölti a dokumentumokat a megadott tartományokból, felügyelt tekintendők. Ez a beállítás csak a Safari böngészővel letöltött dokumentumokra vonatkozik.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: Automatikus eszközök beléptetése (felügyelt)

- **Safari-jelszó automatikus** > kitöltési tartományának**URL-címe**: Adjon hozzá egy vagy több URL-címet a listához. A felhasználók csak a listában szereplő URL-címekhez tartozó webes jelszavakat menthetnek. Ez a beállítás csak a Safari böngészőre és a felügyelt módban lévő eszközökre vonatkozik. Ha nem ad meg URL-címet, a jelszavakat az összes webhelyről mentheti.

  Ez a beállítás a következőkre vonatkozik:  
  - iOS 9,3 és újabb verziók

## <a name="settings-that-require-supervised-mode"></a>Felügyelt üzemmódot igénylő beállítások

Az iOS Supervised (Felügyelt) módja csak a kezdeti eszközbeállítás során, az Apple Készülékregisztrációs programján keresztül vagy az Apple Configuratorral engedélyezhető. A Supervised (Felügyelt) mód engedélyezése után az Intune az alábbi funkciókkal konfigurálhatja az eszközöket:

- App Lock (Egyetlen alkalmazás mód) 
- Globális HTTP-Proxy 
- Aktiválási zár megkerülése 
- Önálló egyetlen alkalmazás mód 
- Webtartalomszűrő 
- Háttér és zárolási képernyő beállítása 
- Felhasználói beavatkozás nélküli alkalmazástelepítés 
- Mindig bekapcsolt VPN 
- Kizárólag felügyelt alkalmazások telepítésének engedélyezése 
- iBookstore 
- iMessages 
- Game Center 
- Airdrop 
- AirPlay 
- Párosítás gazdagéppel 
- Felhőalapú szinkronizálás 
- Spotlight-keresés 
- Handoff 
- Eszköz törlése 
- Korlátozások felhasználói felülete 
- Konfigurációs profilok telepítése a felhasználói felület használatával 
- Hírek 
- Billentyűparancsok 
- PIN-kód módosítása 
- Eszköznév módosítása 
- Alkalmazások automatikus letöltése 
- Vállalati alkalmazások megbízhatóságának módosítása 
- Apple Music 
- Mail Drop 
- Párosítás Apple Watch órával 

> [!NOTE]
> Az Apple megerősítette, hogy bizonyos beállítások csak a 2019-ben kerülnek felügyelet alá. Javasoljuk, hogy ezt a beállítások használatakor vegye figyelembe, ahelyett, hogy az Apple-t csak felügyelt eszközökre telepítse át:
>
> - Végfelhasználók által végzett alkalmazástelepítés
> - Alkalmazás eltávolítása
> - FaceTime
> - Safari
> - iTunes
> - Durva tartalom
> - iCloud dokumentumok és adatok
> - Többrésztvevős játékok
> - Game Center ismerősök hozzáadása
> - Siri

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

A [MacOS](device-restrictions-macos.md) -eszközökön is korlátozhatja az eszközök funkcióit és beállításait.
