---
title: iOS-eszközbeállítások a Microsoft Intuneban – Azure | Microsoft Docs
titleSuffix: ''
description: IOS-eszközökön lévő beállítások hozzáadása, konfigurálása vagy létrehozása a funkciók korlátozásához, beleértve a jelszóval kapcsolatos követelmények beállítását, a zárolt képernyő használatát, a beépített alkalmazásokat, a korlátozott vagy jóváhagyott alkalmazások hozzáadását, a Bluetooth-eszközök kezelését, a felhőhöz való kapcsolódást a biztonsági mentéshez és tároláshoz. a kioszk mód engedélyezése, tartományok hozzáadása és annak szabályozása, hogy a felhasználók hogyan használják a Safari böngészőt Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 476817b70f18fdd45a678ef3e12d1d3312c03dd3
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206533"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>iOS-és iPadOS-eszközök beállításai az Intune-t használó funkciók engedélyezéséhez vagy korlátozásához

Ez a cikk az iOS-és iPadOS-eszközökön szabályozható különböző beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, beállíthatja a jelszavas szabályokat, engedélyezheti vagy korlátozhatja az egyes alkalmazásokat, és így tovább.

Ezek a beállítások hozzáadódnak az Intune-ban az eszköz konfigurációs profiljához, majd az iOS-eszközökhöz vannak rendelve vagy telepítve.

> [!TIP]
> Ezek a beállítások az Apple MDM beállításait használják. További információ ezekről a beállításokról: az [Apple mobileszköz-kezelési beállításai](https://support.apple.com/guide/mdm/welcome/web) (az Apple webhelyén nyílik meg).

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz-korlátozási konfigurációs profilt](../device-restrictions-configure.md).

> [!NOTE]
> Ezek a beállítások a különböző regisztrációs típusokra vonatkoznak, és egyes beállítások az összes regisztrációs lehetőségre érvényesek. A különböző regisztrációs típusokkal kapcsolatos további információkért lásd: [iOS-regisztráció](../ios-enroll.md).

## <a name="general"></a>Általános

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Használati adatok megosztása**: a **Letiltás** elem kiválasztásával megakadályozhatja, hogy az eszköz diagnosztikai és használati adatokat küldjön az Apple-nek. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezt az adatküldés.

- **Képernyőfelvétel**: a **Letiltás** elem kiválasztásával megakadályozhatja a képernyőképek vagy képernyőfelvételek készítését az eszközön. Az iOS 9,0-es és újabb verzióiban blokkolja a képernyőfelvételeket is. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy képként vagy videóként rögzítse a képernyő tartalmát.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- Nem **megbízható TLS-tanúsítványok**: a **Letiltás** elem kiválasztásával megakadályozhatja a nem megbízható Transport Layer Security (TLS) tanúsítványait az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a TLS-tanúsítványokat.
- **Nyilvános PKI-frissítések letiltása**: a **Letiltás** megakadályozza, hogy a felhasználók csak akkor fogadják a szoftverfrissítéseket, ha az eszköz csatlakoztatva van a számítógéphez. **Nincs konfigurálva** (alapértelmezett): lehetővé teszi, hogy az eszköz a számítógépekhez való csatlakozás nélkül kapjon szoftverfrissítéseket.
- **Ad-követés korlátozása**: válassza a **korlát** lehetőséget az eszköz hirdetési azonosítójának letiltásához. **Nincs konfigurálva** (az alapértelmezett) megtartja a használatát.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **Diagnosztikai beküldési beállítások módosítása**: a **Letiltás** megakadályozza, hogy a felhasználó a **diagnosztika és a használat** (eszközbeállítások) során megváltoztassa a diagnosztikai beküldést és az alkalmazás-elemzési beállításokat. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára ezen eszközbeállítások módosítását.

  Ha ezt a beállítást szeretné használni, állítsa a **megosztás használati adatok** beállítást a **blokkolás**értékre.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS-9.3.2 és újabb verziók

- A **távoli képernyő megfigyelése az osztályterem alkalmazásban**: válassza a **Letiltás** lehetőséget, hogy megakadályozza, hogy az osztályterem alkalmazás távolról megtekintse a képernyőt az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az Apple tanterem alkalmazás számára a képernyő megtekintését.

  Ha ezt a beállítást szeretné használni, állítsa a **képernyőfelvétel** beállítást a **blokkolás**értékre.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 9,3 és újabb verziók

- Nem megfigyelt képernyő-figyelés az **osztályterembeli alkalmazásban**: Ha a beállítás **engedélyezésre**van állítva, a tanárok a tanulók ismeretei nélkül, az osztályterem alkalmazással csendben láthatják a tanulók számára készült iOS-eszközök képernyőjét. Az osztályterem alkalmazással az osztályban regisztrált tanulói eszközök automatikusan engedélyt adnak a tanfolyam oktatójának. **Nincs konfigurálva** (alapértelmezés) megakadályozza ezt a funkciót.

  Ha ezt a beállítást szeretné használni, állítsa a **képernyőfelvétel** beállítást a **blokkolás**értékre.

- **Nagyvállalati alkalmazás megbízhatósága**: a **Letiltás** elem kiválasztásával távolítsa el a **megbízható vállalati fejlesztő** gombot a beállítások > Általános > profilok & eszközkezelés az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára az alkalmazás-áruházból letöltött alkalmazások megbízhatóságának megválasztását.
- **Fiók módosítása**: Ha a **blokkolás**értékre van állítva, a felhasználó nem tudja frissíteni az eszközre vonatkozó beállításokat az iOS-beállítások alkalmazásból. A felhasználó például nem tud új fiókokat létrehozni, vagy módosítani a felhasználónevet vagy a jelszót. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy megváltoztassák ezeket a beállításokat.

  Ez a funkció az iOS-beállítások alkalmazásból elérhető beállításokra is vonatkozik, például a levelezés, a névjegyek, a naptár, a Twitter stb. Ez a funkció nem vonatkozik azokra az alkalmazásokra, amelyek olyan Fiókbeállítások, amelyek nem konfigurálhatók az iOS-beállítások alkalmazásból, például a Microsoft Outlook alkalmazásból.

- **Képernyő időpontja**: a **Letiltás** gombra kattintva megakadályozhatja, hogy a felhasználók a saját korlátozásokat állítsanak be a képernyőn megadott időben (eszközbeállítások). A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználó az eszközön korlátozásokat (például szülői vezérlőket, tartalmakat és adatvédelmi korlátozásokat) konfiguráljon az eszközön.

  A rendszer átnevezte ezt a beállítást, mert **engedélyezte a korlátozásokat az eszközbeállítások között**. A változás hatása:  
  
  - iOS-11.4.1 és korábbi verziók: a **Letiltás** megakadályozza, hogy a végfelhasználók saját korlátozásokat állítsanak be az eszközbeállítások között. A viselkedés ugyanaz; és nincsenek változások a végfelhasználók számára.
  - iOS 12,0 és újabb verziók: a **Letiltás** megakadályozza, hogy a végfelhasználók saját **képernyős időt** állítsanak be az eszközbeállítások során (beállítások > általános > képernyő idő), beleértve a tartalom-és adatvédelmi korlátozásokat. Az iOS 12,0-re frissített eszközök többé nem látják a korlátozások lapot az eszközbeállítások esetében (Beállítások > Általános > eszközkezelés > felügyeleti profil > korlátozásai). Ezek a beállítások a **képernyőn**jelennek meg.
  
- Az **összes tartalom és beállítás törlésére szolgáló beállítás használata az eszközön**: válassza a **Letiltás** lehetőséget, hogy a felhasználók ne tudják használni az összes tartalom és beállítás törlése lehetőséget az eszközön. **Nincs konfigurálva** (alapértelmezés) hozzáférést biztosít a felhasználóknak a beállításokhoz.
- **Eszköznév módosítása**: válassza a **Letiltás** lehetőséget, hogy az eszköz neve nem módosítható. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa az eszköz nevét.
- **Értesítési beállítások módosítása**: válassza a **Letiltás** lehetőséget, hogy az értesítési beállítások ne legyenek módosítva. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa az eszköz értesítési beállításait.
- **Háttérkép módosítása**: a **blokk** megakadályozza a háttérkép módosítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa a háttérképet az eszközön.
- **Vállalati alkalmazások megbízhatósági beállításainak módosítása**: a **Letiltás** megakadályozza, hogy a felhasználó módosítsa a vállalati alkalmazás megbízhatósági beállításait a felügyelt eszközökön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára az alkalmazás-áruházból letöltött alkalmazások megmegbízhatóságát.
- **Konfigurációs profil módosítása**: a **blokk** megakadályozza a konfigurációs profil módosítását az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a konfigurációs profilok telepítését.
- **Aktiválási zár**: válassza az **Engedélyezés lehetőséget** aktiválási zár felügyelt iOS-eszközökön való engedélyezéséhez. A Aktiválási zár megnehezíti az elveszett vagy ellopott eszközök újraaktiválását.
- **Alkalmazás eltávolításának tiltása**: válassza a **Letiltás** lehetőséget a felhasználók alkalmazások eltávolításának megakadályozásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az alkalmazások eltávolítását az eszközről.
- **USB-tartozékok engedélyezése, ha az eszköz zárolva van**: az **Engedélyezés** lehetővé teszi, hogy az USB-tartozékok egy órán keresztül zárolt eszközzel legyenek kicserélve. **Nincs konfigurálva** (az alapértelmezett) nem FRISSÍTI az USB-korlátozott üzemmódot az eszközön, és az USB-tartozékok le lesznek tiltva az adatoknak az eszközről történő átvitele esetén, ha egy órán keresztül zárolva van.
- **Automatikus dátum és idő kényszerítése**: a felügyelt eszközök **megkövetelése** a dátum & idő automatikus beállításához. Az eszköz időzónája frissül, amikor az eszköz mobil kapcsolattal rendelkezik, vagy engedélyezve van a Wi-Fi és a Location Services.
- A **tanulóknak engedélyt kell kérniük az osztályteremből való távozásra**: az osztályterem alkalmazással egy nem felügyelt tanfolyamot **kell** bekapcsolni a tanulótól, hogy elhagyják a tanfolyamot. **Nincs konfigurálva** (alapértelmezés) nem kényszeríti a tanulót, hogy kérjen engedélyt.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,3 és újabb verziók

- Alkalmazások **zárolásának engedélyezése az alkalmazáshoz és az eszköz zárolása az értesítés nélkül**: az **Engedélyezés** lehetővé teszi, hogy a tanár zárolja az alkalmazásokat, vagy zárolja az eszközt az osztályterem alkalmazással anélkül, hogy a tanulót kellene kérnie. Az alkalmazások zárolása azt jelenti, hogy az eszköz csak a tanár által megadott alkalmazásokat fér hozzá. **Nincs konfigurálva** (alapértelmezés) megakadályozza, hogy a tanárok az osztályterem alkalmazással zárolják az alkalmazásokat és az eszközöket anélkül, hogy a tanulót kellene kérniük.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

- **Tantermi osztályok automatikus csatlakoztatása rákérdezés nélkül**: az **Engedélyezés** automatikusan lehetővé teszi a tanulók számára az osztályterem alkalmazásban található osztályhoz való csatlakozást a tanár megkérdezése nélkül. **Nincs konfigurálva** (alapértelmezés) arra kéri a tanárt, hogy a tanulók az osztályterem alkalmazásban lévő osztályhoz csatlakozzanak.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

- **VPN-létrehozás letiltása**: a **blokk** megakadályozza, hogy a felhasználók VPN-konfigurációs beállításokat hozzanak létre. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók VPN-eket hozzanak létre az eszközön.
- A **eSIM beállításainak módosítása**: a **Letiltás** megakadályozza, hogy a felhasználók eltávolítsák vagy felvesznek egy mobil csomagot az eszköz eSIM. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy megváltoztassák ezeket a beállításokat.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 12,1 és újabb verziók

- **Szoftverfrissítések késleltetése**: Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a szoftverfrissítések az eszközön jelennek meg, ahogy az Apple felszabadítja őket. Ha például egy iOS-es frissítést az Apple adott időpontban szabadít fel, akkor ez a frissítés természetesen az eszközön jelenik meg a kiadási dátum körül.

  Az **Engedélyezés** beállítás megadásával késleltetheti, hogy a szoftverfrissítések mikor jelenjenek meg az eszközökön, 0-90 nap múlva. Ez a beállítás nem szabályozza, hogy a frissítések Mikor vagy nincsenek telepítve. 

  - **Szoftverfrissítések láthatóságának késleltetése**: adjon meg egy 0-90 napos értéket. Ha a késleltetés lejár, a felhasználók értesítést kapnak, hogy az operációs rendszer legkorábbi verziójára frissítsen a késleltetés elindításakor.

    Ha például az iOS 12. a a **január 1-jén**érhető el, és a **késleltetési láthatóság** értéke **5 nap**, akkor az iOS 12. a nem jelenik meg elérhető frissítésként a végfelhasználói eszközökön. A kiadást követő **hatodik napon** a frissítés elérhető lesz, és a végfelhasználók is telepíthetik azt.

    Ez a beállítás a következőkre vonatkozik:  
    - iOS 11,3 és újabb verziók

## <a name="password"></a>Jelszó

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Password (jelszó**): **megköveteli** a végfelhasználótól, hogy jelszót adjon meg az eszköz eléréséhez. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók jelszó megadása nélkül férhessenek hozzá az eszközhöz.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

> [!IMPORTANT]
> A felhasználó által beléptetett eszközökön a jelszó beállításának beállításakor a rendszer automatikusan **letiltja**az **egyszerű jelszavak** beállításait, és egy 6 számjegyű PIN-kódot kényszerít ki.
>
> Például beállíthatja a **jelszó lejárati** beállítását, és leküldheti a szabályzatot a felhasználó által regisztrált eszközökre. Az eszközökön a következők történnek:
>
> - A **jelszó lejárati** beállítását a rendszer figyelmen kívül hagyja.
> - Az egyszerű jelszavak (például `1111` vagy `1234`) nem engedélyezettek.
> - Egy 6 számjegyű PIN-kód kényszerítve.

- **Egyszerű jelszavak**: a **Letiltás** elem kiválasztásával összetettebb jelszavakat igényelhet. A **nincs konfigurálva** beállítás lehetővé teszi az egyszerű jelszavak használatát, például `0000` és `1234`.

- **Szükséges jelszó típusa**: válassza ki a szervezet által igényelt jelszó típusát. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Numerikus**
  - **Alfanumerikus**
- **Nem alfanumerikus karakterek száma a jelszóban**: Itt adhatja meg, hogy hány karakterből (például `#` vagy `@`) kell szerepelnie a jelszóban.

- **Jelszó minimális hossza**: Itt adhatja meg azt a minimális hosszt, amelyet a felhasználónak meg kell adnia 4 – 14 karakter között. A felhasználó által regisztrált eszközökön adjon meg egy 4 és 6 karakter közötti hosszúságot.
  
  > [!NOTE]
  > A felhasználó által beléptetett eszközök esetében a felhasználók 6 számjegynél nagyobb PIN-kódot állíthatnak be. Azonban az eszközön legfeljebb 6 számjegy kényszeríthető ki. A rendszergazda például a `8`minimális hosszát állítja be. A felhasználó által regisztrált eszközökön a felhasználóknak csak 6 számjegyű PIN-kódot kell megadniuk. Az Intune nem kényszeríti a 6 számjegynél nagyobb PIN-kód megadását a felhasználó által regisztrált eszközökön.

- Sikertelen **bejelentkezések száma az eszköz törlése előtt**: Itt adhatja meg, hogy hány sikertelen bejelentkezés után kerüljön sor az eszköz törlésére (4-11).
  
  az iOS beépített biztonságot tartalmaz, amely hatással lehet erre a beállításra. Előfordulhat például, hogy az iOS késlelteti a szabályzat aktiválását a bejelentkezési hibák számától függően. Azt is fontolóra veheti, hogy ismételten ugyanazzal a PIN-kóddal adja meg ugyanazt a jelszót, mint egy kísérletet. Az Apple [IOS-alapú biztonsági útmutatója](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (az Apple webhelyének megnyitása) jó erőforrás, és pontosabb részleteket biztosít a PIN-kódokról.
  
- A **Képernyő zárolása előtt legfeljebb perccel a jelszó megadása kötelező**<sup>1</sup>: adja meg, hogy az eszköz mennyi ideig maradjon üresjáratban, mielőtt a felhasználónak újra meg kell adnia a jelszavát. Ha a megadott idő hosszabb az eszközön jelenleg beállított értéknél, akkor az eszköz figyelmen kívül hagyja a beírt időt. IOS 8,0 és újabb rendszerű eszközökön támogatott.

- **Legfeljebb ennyi perc inaktivitás után (képernyő zárolása**<sup>1)</sup>: Itt adhatja meg, hogy legfeljebb hány perc inaktivitás engedélyezett az eszközön a képernyő zárolása előtt.

  **iOS-beállítások**:  

  - **Nincs konfigurálva** (alapértelmezett): az Intune nem érinti ezt a beállítást.
  - **Azonnal**: a képernyő zárolása 30 másodperc inaktivitás után történik.
  - **1**: a képernyőfelvételek 1 perc inaktivitás után zárolva vannak.
  - **2**: a képernyő 2 perc inaktivitás után zárolható.
  - **3**: a képernyő zárolása 3 perc inaktivitás után történik.
  - **4**: a képernyő zárolása 4 perc inaktivitás után történik.
  - **5**: a képernyő 5 perc inaktivitás után zárolja.
    
  **iPadOS beállítások**:  

  - **Nincs konfigurálva** (alapértelmezett): az Intune nem érinti ezt a beállítást.
  - **Azonnal**: 2 perc inaktivitás után zárolja a képernyőket.
  - **2**: a képernyő 2 perc inaktivitás után zárolható.
  - **5**: a képernyő 5 perc inaktivitás után zárolja.
  - **10**: a képernyő zárolása 10 perc inaktivitás után történik.
  - **15**: a képernyőfelvételek 15 perc inaktivitás után zárolva vannak.

  Ha egy érték nem vonatkozik az iOS-re vagy a iPadOS, az Apple a legközelebbi *legalacsonyabb* értéket használja. Ha például `4` percet ad meg, a iPadOS-eszközök `2` percet használnak. Ha `10` percet ad meg, az iOS-eszközök `5` percet használnak. Ez egy Apple-korlátozás.
  
  > [!NOTE]
  > A beállítás Intune KEZELŐFELÜLETe nem választja el az iOS-és a iPadOS által támogatott értékeket. Előfordulhat, hogy a felhasználói felület egy későbbi kiadásban frissül.

- **Jelszó érvényessége (napokban)**: adja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát.
- **Korábbi jelszavak újbóli használatának tiltása**: Itt adhatja meg, hogy hány új jelszót kell használni, amíg egy régit nem lehet újra felhasználni.
- **Touch ID és Face ID feloldása**: válassza a **Letiltás** lehetőséget, nehogy ujjlenyomatot vagy arcot használjon az eszköz zárolásának feloldásához. A **nincs konfigurálva** beállítás lehetővé teszi, hogy a felhasználó ezeket a módszereket használja fel az eszköz zárolásának feloldásához.

  A beállítás letiltása azt is megakadályozza, hogy a FaceID hitelesítést használja az eszköz zárolásának feloldásához.

  A Face ID a következőkre vonatkozik:  
  - iOS 11,0 és újabb verziók

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **PIN-kód módosítása**: válassza a **Letiltás** lehetőséget a PIN-kód módosításának, hozzáadásának vagy eltávolításának leállításához. A PIN-kódokra vonatkozó korlátozások módosításait a rendszer figyelmen kívül hagyja a felügyelt eszközökön a funkció letiltása után. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a PIN-kódok hozzáadását, módosítását vagy eltávolítását.

  - **Touch ID és Face ID módosítása**: a **blokk** leállítja a felhasználót a Touch ID ujjlenyomatok és a Face ID módosításának, hozzáadásának vagy eltávolításának megváltoztatásával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó frissítse a Touch ID ujjlenyomatait és a Face ID-t az eszközön.

    Ha letiltja ezt a beállítást, a felhasználó FaceID-hitelesítés módosítását, hozzáadását vagy eltávolítását is megakadályozza.

    A Face ID a következőkre vonatkozik:  
    - iOS 11,0 és újabb verziók

- **Jelszó automatikus**kitöltésének tiltása: válassza a **Letiltás** lehetőséget, hogy ne használja az automatikus kitöltés jelszava funkciót iOS rendszeren. A **blokk** kiválasztása a következő hatással is van:

  - A felhasználók nem kérik a mentett jelszavak használatát a Safariban vagy bármely alkalmazásban.
  - Az automatikus erős jelszavak le vannak tiltva, és az erős jelszavakat nem javasoljuk a felhasználók számára.

  **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a funkciókat.

- **Jelszó-közelségi kérelmek letiltása**: válassza a **Letiltás** lehetőséget, hogy a felhasználó eszköze ne kérjen jelszavakat a közeli eszközökről. **Nincs konfigurálva** (alapértelmezés) engedélyezi ezeket a jelszavakat.
- **Jelszó-megosztás letiltása**: a **blokk** megakadályozza a jelszavak megosztását az eszközök között a AirDrop használatával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszavak megosztását.
- **A jelszó-vagy hitelkártya-adatok automatikus kitöltéséhez érintse meg a Touch ID-t vagy a Face ID hitelesítést**: Ha a beállítás **kötelező**, a felhasználóknak a Touch ID vagy a FaceID használatával kell hitelesíteniük magukat, mielőtt a jelszavak vagy a hitelkártya-információk automatikusan kitölthetők a Safari és más alkalmazások **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a funkció vezérlését az eszközbeállítások között.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók
  
<sup>1</sup> Ha a képernyő zárolása ennyi **perc inaktivitás** után és a **Képernyő zárolása után legfeljebb perccel a jelszó megadása után beállítás van** beállítva, akkor azokat a rendszer sorrend szerint alkalmazza. Ha például mindkét beállítás értékét **5** percre állítja be, a képernyő öt perc elteltével automatikusan kikapcsol, és az eszköz további öt perc múlva zárolva lesz. Ha azonban a felhasználó manuálisan kapcsolja ki a képernyőt, azonnal a második beállítás lesz alkalmazva. Ugyanebben a példában azt követően, hogy a felhasználó kikapcsolta a képernyőt, öt perccel később zárolja az eszközt.

## <a name="locked-screen-experience"></a>Zárolási képernyő felülete

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Vezérlési központ hozzáférése az eszköz zárolt állapotában**: válassza a **Letiltás** lehetőséget a vezérlési központ alkalmazás elérésének megakadályozásához az eszköz zárolt állapotában. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználók hozzáférjenek a Control Center alkalmazáshoz, amikor az eszköz zárolva van.
- **Értesítések az eszköz zárolt állapotában**: a **blokk** megakadályozza az értesítések elérését az eszköz zárolt állapotában. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára az értesítések elérését az eszköz zárolásának feloldása nélkül.
- **Ma nézet az eszköz zárolt állapotában**: a **blokk** megakadályozza a ma nézethez való hozzáférést, ha az eszköz zárolva van. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy megtekintse a mai nézetet, amikor az eszköz zárolva van.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Mobiltárca-értesítések az eszköz zárolt állapotában**: a **blokk** megakadályozza a hozzáférését a mobiltárca alkalmazáshoz, ha az eszköz zárolva van. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó hozzáférjen a mobiltárca alkalmazáshoz, amíg az eszköz zárolva van.

## <a name="app-store-doc-viewing-gaming"></a>Alkalmazás-áruház, dokumentumok megtekintése, játékok

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Vállalati dokumentumok megtekintése a nem felügyelt alkalmazásokban**: a **blokk** megakadályozza a vállalati dokumentumok megtekintését a nem felügyelt alkalmazásokban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a vállalati dokumentumok megtekintését bármely alkalmazásban. Tegyük fel például, hogy meg szeretné akadályozni, hogy a felhasználók fájlokat mentsenek a OneDrive alkalmazásból a Dropboxba. Állítsa be ezt a beállítást **blokkként**. Miután az eszköz megkapja a házirendet (például újraindítás után), az már nem teszi lehetővé a mentést.


  > [!NOTE]
  > Ha ez a beállítás le van tiltva, az alkalmazás-áruházból telepített külső gyártótól származó billentyűzetek is le vannak tiltva.

  - Nem **felügyelt alkalmazások beolvasásának engedélyezése a felügyelt névjegyek fiókjaiból**: Ha **engedélyezi**, a nem felügyelt alkalmazások, például a beépített iOS-névjegyek alkalmazás, a felügyelt alkalmazásokból származó kapcsolattartási adatokat, például az Outlook Mobile alkalmazást is beolvashatja és elérheti. **Nincs konfigurálva** (alapértelmezés) megakadályozza az olvasást, beleértve az ismétlődések eltávolítását is az eszköz beépített névjegyek alkalmazásában.  
  
    Ez a beállítás engedélyezi vagy megakadályozza a kapcsolattartási adatok olvasását. Nem szabályozza a kapcsolatok szinkronizálását az alkalmazások között.
  
    Ha ezt a beállítást szeretné használni, állítsa be a **vállalati dokumentumok megtekintése a nem felügyelt alkalmazásokban** beállítást a **blokkoláshoz**.

  További információ erről a két beállításról, valamint azok hatása az Outlook for iOS-kapcsolat exportálási szinkronizálására [: támogatási Tipp: az egyéni Intune-profil beállításainak használata az iOS Native Contacts alkalmazással](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **AirDrop kezelése nem felügyelt célként**: a kényszerített AirDrop nem felügyelt eldobási **célként kell tekinteni** . Leállítja a felügyelt alkalmazások számára az adatok küldését a AirDrop használatával. 
- **Nem vállalati dokumentumok megtekintése a vállalati alkalmazásokban: a** **blokk** megakadályozza a nem vállalati dokumentumok megtekintését a vállalati alkalmazásokban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a dokumentumok megtekinthetők legyenek a vállalat által felügyelt alkalmazásokban.

  A **Letiltás** beállítás meggátolja a kapcsolatfelvételt az iOS-ben az Outlookban. További információ [: támogatási Tipp: az Outlook iOS Contact Sync engedélyezése a IOS12 Mdm-vezérlőkkel](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **ITunes Store-jelszó megkövetelése az összes vásárláshoz**: a felhasználónak meg kell **adnia az Apple** ID jelszót az egyes alkalmazásokhoz vagy az iTunes-vásárlásokhoz. **Nincs konfigurálva** (az alapértelmezett) lehetővé teszi a vásárlásokat anélkül, hogy minden alkalommal jelszót kellene kérnie.
- **Alkalmazáson belüli vásárlások**: a **Letiltás** elem kiválasztásával megakadályozhatja az alkalmazáson belüli vásárlásokat az áruházból. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az áruházban való vásárlást egy futó alkalmazáson belül.
- A **"Erotika" címkével megjelölt tartalmak letöltése az iBooks áruházból**: a **Letiltás** beállítás megtiltásával megakadályozhatja, hogy a felhasználók ne töltsenek le olyan adathordozókat az iBooks áruházból, amely az erotika. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a könyvek letöltését az "Erotika" kategóriával.
- A **felügyelt alkalmazások számára lehetővé teszi a névjegyek írását a nem felügyelt névjegyalbumba**: Ha az **Engedélyezés**, a felügyelt alkalmazások, például az Outlook Mobile alkalmazás, a beépített iOS Contacts alkalmazásba mentheti vagy szinkronizálhatja a kapcsolattartási adatokat, beleértve az üzleti és vállalati kapcsolatokat is. Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a felügyelt alkalmazások nem tudják menteni vagy szinkronizálni a kapcsolattartási adatokat az eszköz beépített iOS Contacts alkalmazásával.
  
  Ha ezt a beállítást szeretné használni, állítsa be a **vállalati dokumentumok megtekintése a nem felügyelt alkalmazásokban** beállítást a **blokkoláshoz**.

- **Minősítési régió**: válassza ki az engedélyezett letöltésekhez használni kívánt minősítési régiót. Majd válassza ki a **filmek**, **tévéműsorok**és **alkalmazások**engedélyezett minősítéseit.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **App Store**: **letiltja** az alkalmazás-áruházhoz való hozzáférést a felügyelt eszközökön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

  - **Alkalmazások telepítése az App Store-ból**: válassza a **Letiltás** lehetőséget az alkalmazás-áruház az eszköz kezdőlapjára való blokkolásához. A végfelhasználók továbbra is használhatják az iTunest vagy az Apple Configurator eszközt alkalmazások telepítésére. **Nincs konfigurálva** (alapértelmezés) engedélyezi az App Store-t a kezdőképernyőn.
  - Alkalmazások **automatikus**letöltése: válassza a **Letiltás** lehetőséget, hogy megakadályozza a más eszközökön vásárolt alkalmazások automatikus letöltését. Nem érinti a meglévő alkalmazások frissítéseit. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi más iOS-eszközökön vásárolt alkalmazások letöltését az eszközön.

- **Kifejezetten iTunes zene, podcast vagy Hírek tartalma**: a **Letiltás** elemre kattintva megakadályozhatja az iTunes-zene, podcast vagy Hírek tartalmát. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz hozzáférjen az áruházból származó felnőttként használt tartalomhoz. az iOS 13 és újabb verziókhoz csak felügyelt eszközökre lehet szükség. 

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Game Center ismerősök hozzáadása**: a **Letiltás** megakadályozza, hogy a felhasználók Game Center barátokat adjanak hozzá. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a barátok hozzáadását Game Center.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Game Center**: a Game Center alkalmazás használatának **tiltása** . **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Game Center alkalmazás használatát az eszközön.
- **Többrésztvevős játék**: válassza a **Letiltás** lehetőséget a többrésztvevős játékok elkerüléséhez. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy többrésztvevős játékokat játsszon az eszközön.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Hozzáférés hálózati meghajtóhoz a Files alkalmazásban**: a kiszolgálói üzenetblokk (SMB) protokoll használatával az eszközök hozzáférhetnek a hálózati kiszolgálón található fájlokhoz vagy egyéb erőforrásokhoz. A **Letiltás** beállítás meggátolja a hálózati SMB-meghajtón lévő fájlok elérését. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hozzáférést.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS és iPadOS 13,0 és újabb verziók

## <a name="built-in-apps"></a>Beépített alkalmazások

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Siri**: a **blokk** megakadályozza a hozzáférést a sirihoz. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az eszközön a Siri Voice Assistant használatát.
  - Siri, ha az **eszköz zárolva van**: válassza a **Letiltás** lehetőséget a Siri elérésének megakadályozásához, ha az eszköz zárolva van. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az eszközön a Siri Voice Assistant használatát, ha zárolva van.

- A **Safari csalások elleni figyelmeztetések**: az eszközön található webböngészőben megjelenő csalási figyelmeztetések **megkövetelése** . A **Nincs konfigurálva** (alapértelmezett) érték letiltja a funkciót.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Spotlight-keresés az internetről származó eredmények visszaadásához**: a leállítási **funkció** nem tér vissza az internetes keresés eredményeiből. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Spotlight-keresés kapcsolódását az internethez a keresési eredmények biztosítása érdekében.

- **Safari cookie-k**: válassza ki, hogyan történjen a cookie-k kezelése az eszközön. A választható lehetőségek:
  - Lehetővé
  - Az összes cookie letiltása
  - Cookie-k engedélyezése a felkeresett webhelyekről
  - Cookie-k engedélyezése a jelenlegi webhelyről

- **Safari JavaScript**: a **blokk** megakadályozza a Java-parancsfájlok futtatását a böngészőben az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a Java-parancsfájlokat.

- **Safari előugró ablakok**: **letiltja** az előugró ablakok blokkoló funkcióját a böngészőben. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az előugró ablak blokkolását.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **Kamera**: válassza a **Letiltás** lehetőséget a kamera elérésének megakadályozásához az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi az eszköz kamerájának elérését.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

  - **FaceTime**: **blokkolás** a FaceTime-alkalmazáshoz való hozzáférés megakadályozása érdekében. **Nincs konfigurálva** (alapértelmezés) engedélyezi a FaceTime alkalmazás elérését az eszközön.

    Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Siri káromkodás szűrő**: **megkövetelő** , hogy a Siri ne diktáljon vagy beszélje meg a káromkodás nyelvét.

  Ha ezt a beállítást szeretné használni, állítsa a **Siri** beállítást a **Letiltás**értékre.

- **A felhasználó által létrehozott tartalom lekérése az internetről**: **Block** megakadályozza, hogy a Siri hozzáférjen a webhelyekhez a kérdések megválaszolásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Siri számára a felhasználó által létrehozott tartalmak elérését az internetről.

  Ha ezt a beállítást szeretné használni, állítsa a **Siri** beállítást a **Letiltás**értékre.

- **Apple News**: válassza a **letiltás** lehetőséget a Apple News alkalmazás elérésének megakadályozásához az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Apple News alkalmazás használatát.
- **iBooks Store**: a **blokk** megakadályozza az iBooks tároló elérését. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az iBooks áruházból származó könyvek tallózását és megvásárlását.
- **Üzenetek alkalmazás az eszközön**: a **Letiltás** megakadályozza, hogy a felhasználók a iMessage üzenetek alkalmazást használják. Ha az eszköz támogatja a szöveges üzenetküldést, akkor a felhasználó SMS-sel továbbra is küldhet és fogadhat szöveges üzeneteket. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az üzenetek alkalmazás számára az üzenetek küldését és olvasását az interneten keresztül.
- **Podcasts**: a **blokk** megakadályozza, hogy a felhasználók a Podcasts alkalmazást használják. **Nincs konfigurálva** (alapértelmezett) a Podcasts alkalmazás használatát teszi lehetővé.
- **Music szolgáltatás**: a **Block** a Music alkalmazást klasszikus módra vált, és letiltja a Music szolgáltatást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Apple Music alkalmazás használatát.
- **iTunes Radio szolgáltatás**: a **Letiltás** megakadályozza, hogy a felhasználók az iTunes Radio alkalmazást használják. **Nincs konfigurálva** (alapértelmezett) az iTunes Radio alkalmazás használatát teszi lehetővé.
- **iTunes Store**: **nincs konfigurálva** (alapértelmezett) engedélyezi az iTunes használatát az eszközökön. A **Letiltás** megakadályozza, hogy a felhasználók az iTunes-ot használják az eszközön. 

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 4,0 és újabb verziók

- Az **iPhone**: **nincs konfigurálva** (alapértelmezett) funkció lehetővé teszi, hogy a Find My app (az alkalmazás megkeresése) funkciót használja az eszköz hozzávetőleges helyének lekéréséhez. A **Letiltás** megakadályozza a funkció megkeresését a saját alkalmazásban. 

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és iPadOS 13,0 és újabb

- **Ismerősök megkeresése**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az alkalmazás megkeresése funkcióval megkeresse a családot és a barátokat egy Apple-eszközről vagy iCloud.com. A **Letiltás** megakadályozza a funkció megkeresését a saját alkalmazásban.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és iPadOS 13,0 és újabb

- **A barátok keresése alkalmazás beállításainak módosítása**: a **Letiltás** megakadályozza a barátok alkalmazás beállításainak módosítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a barátok keresése alkalmazás beállításainak módosítását.

- **Spotlight-keresés az internetről származó eredmények visszaadásához**: a leállítási **funkció** nem tér vissza az internetes keresés eredményeiből. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a Spotlight-keresés kapcsolódását az internethez a keresési eredmények biztosítása érdekében.

- **Rendszeralkalmazások eszközről való eltávolításának tiltása**: a **Letiltás** beállítás megadásával letiltható a rendszeralkalmazások eltávolítása az eszközről. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a rendszeralkalmazások eltávolítását.

- **Safari**: **Letiltás** a Safari böngésző használatával az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a Safari böngésző használatát.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **Safari automatikus kitöltés**: a **Letiltás** letiltja az eszközön található Safari automatikus kitöltés szolgáltatását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a webböngésző automatikus kiegészítési beállításainak módosítását.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

## <a name="restricted-apps"></a>Korlátozott alkalmazások

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **A korlátozott alkalmazások listájának típusa**: hozza létre azon alkalmazások listáját, amelyeket a felhasználók nem telepíthetnek és nem használhatnak. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): nincsenek korlátozások az Intune-ban. A felhasználók hozzáférhetnek a hozzárendelt alkalmazásokhoz és a beépített alkalmazásokhoz.
  - **Tiltott alkalmazások**: az Intune által nem felügyelt alkalmazások, amelyeket nem kíván telepíteni az eszközre. A felhasználók nem akadályozzák meg a tiltott alkalmazások telepítését. Ha azonban a felhasználó a listából telepít egy alkalmazást, az az Intune-ban szerepel.
  - **Jóváhagyott alkalmazások**: azok az alkalmazások, amelyeket a felhasználók telepíthetnek. A felhasználók nem telepíthetnek olyan alkalmazásokat, amelyek nem szerepelnek a felsorolásban. Az Intune által kezelt alkalmazások automatikusan engedélyezettek. A felhasználók nem akadályozzák meg a jóváhagyott listán nem szereplő alkalmazások telepítését. De ha igen, az Intune-ban jelentett jelentés.

Ha alkalmazásokat szeretne hozzáadni a listához, a következőket teheti:

- **Adja hozzá** a kívánt alkalmazás iTunes App Store áruházbeli URL-címét. A Microsoft munkahelyi mappák alkalmazás hozzáadásához például adja meg `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` vagy `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Az alkalmazás URL-címének megkereséséhez nyissa meg az iTunes App Store áruházat, és keresse meg az alkalmazást. Keressen például `Microsoft Remote Desktop` vagy `Microsoft Word`. Válassza ki az alkalmazást, és másolja az URL-címet.

  Az iTunes használatával is megkeresheti az alkalmazást, majd a **hivatkozás másolása** feladat használatával beolvashatja az alkalmazás URL-címét.

- **Importáljon** egy CSV-fájlt az alkalmazás részleteivel, beleértve az URL-címet is. Használja a következő formátumot: `<app url>, <app name>, <app publisher>`. Vagy **exportáljon** egy meglévő listát, amely tartalmazza a korlátozott alkalmazások listáját ugyanabban a formátumban.

> [!IMPORTANT]
> A korlátozott alkalmazás-beállításokat használó eszközöket felhasználói csoportokhoz kell rendelni.

## <a name="show-or-hide-apps"></a>Alkalmazások megjelenítése vagy elrejtése

Az iOS 9,3-es vagy újabb verzióját futtató eszközökre vonatkozik.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **Az alkalmazások típusa lista**: hozza létre a megjelenítendő vagy elrejteni kívánt alkalmazások listáját. Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094). A választható lehetőségek:

  - **Rejtett alkalmazások**: megadhatja a felhasználók elől rejtett alkalmazások listáját. A felhasználók nem tekinthetik meg és nem nyitják meg ezeket az alkalmazásokat.
  
    Az Apple megakadályozza egyes natív alkalmazások elrejtését. Nem rejtheti el például a **beállításokat** vagy a **mobiltárca** -alkalmazásokat az eszközön. A [beépített Apple-alkalmazások törlésével](https://support.apple.com/HT208094) megtekintheti azokat az alkalmazásokat, amelyek rejtve vannak.
  
  - **Látható alkalmazások**: megadhatja a felhasználók által megtekinthető és elindítható alkalmazások listáját. Ezeken kívül a felhasználók más alkalmazásokat nem látnak és nem indíthatnak el.

- **Alkalmazás URL-címe**: adja meg a megjeleníteni vagy elrejteni kívánt alkalmazás áruházbeli alkalmazásának URL-címét. Példa:

  - A Microsoft munkahelyi mappák alkalmazás hozzáadásához írja be `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` vagy `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - A Microsoft Word alkalmazás hozzáadásához írja be `https://itunes.apple.com/de/app/microsoft-word/id586447913` vagy `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Az alkalmazás URL-címének megkereséséhez nyissa meg az iTunes App Store áruházat, és keresse meg az alkalmazást. Keressen például `Microsoft Remote Desktop` vagy `Microsoft Word`. Válassza ki az alkalmazást, és másolja az URL-címet.

  Az iTunes használatával is megkeresheti az alkalmazást, majd a **hivatkozás másolása** feladat használatával beolvashatja az alkalmazás URL-címét.
  
  A csomagok AZONOSÍTÓjának megkeresésével kapcsolatos további információkért lásd: [az iOS-alkalmazások csomag-azonosítójának megkeresése](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- Alkalmazáscsomag- **azonosító**: adja meg a kívánt alkalmazás ALKALMAZÁSCSOMAG- [azonosítóját](bundle-ids-built-in-ios-apps.md) . Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Alkalmazás neve**: adja meg a kívánt alkalmazás nevét. Megjelenítheti vagy elrejtheti a beépített alkalmazásokat és üzletági alkalmazásokat. Az Apple webhelye tartalmazza a [beépített Apple apps-alkalmazásokat](https://support.apple.com/HT208094).
- **Kiadó**: adja meg a kívánt alkalmazás közzétevőjét.

Alkalmazások hozzáadásához a következőket teheti:

- **Hozzáadás**: válassza a lehetőséget az alkalmazások listájának létrehozásához.
- **Importáljon** egy CSV-fájlt az alkalmazás részleteivel, beleértve az URL-címet is. Használja a következő formátumot: `<app url>, <app name>, <app publisher>`. Vagy az **Exportálás** gombra kattintva hozzon létre egy listát a hozzáadott korlátozott alkalmazások listájáról, ugyanebben a formátumban.

## <a name="wireless"></a>Vezeték nélküli

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

Vegye figyelembe, hogy az adatroaminghoz szükséges (tipp vagy fontos megjegyzés): Ez a beállítás nem jelenik meg a célként megadott eszköz felügyeleti profilján. Ennek oka, hogy ez a beállítás távoli eszköz műveletként van kezelve, és minden alkalommal, amikor megváltoznak az adatroaming állapota az eszközön, az Intune szolgáltatás újra letiltja. Annak ellenére, hogy nem szerepel a felügyeleti profilban, akkor is működik, ha a felügyeleti konzolon a jelentéskészítés sikerességét mutatja. 
- **Adatroaming**: a **Letiltás** elemre kattintva megakadályozhatja az adatbarangolást a mobilhálózat felett. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi az adatroaming használatát, ha az eszköz mobil hálózaton van.

  > [!IMPORTANT]
  > Ezt a beállítást távoli eszköz műveletként kezeli a rendszer. Így ez a beállítás nem jelenik meg az eszköz felügyeleti profiljában. Minden alkalommal, amikor az adatroaming állapota megváltozik az eszközön, az Intune szolgáltatás letiltja az **adatroamingot** . Az Intune-ban, ha a jelentéskészítési állapot sikert mutat, akkor tudja, hogy működik, még akkor is, ha a beállítás nem jelenik meg az eszköz felügyeleti profiljában.

- **Globális háttérbeli beolvasás barangolás közben**: a **Letiltás** megakadályozza a globális háttér-beolvasási funkció használatát a mobil hálózaton való barangolás közben. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz beolvassa az adatfájlokat, például az e-maileket, amikor a barangoló a mobil hálózaton van.
- **Hangtárcsázás**: válassza a **Letiltás** lehetőséget, hogy a felhasználók ne használják a hangtárcsázás funkciót az eszközön. **Nincs konfigurálva** (alapértelmezés) engedélyezi a hangtárcsázást az eszközön.
- **Hangroaming**: válassza a **Letiltás** lehetőséget a mobiltelefonon a hangroaming elkerüléséhez. **Nincs konfigurálva** (alapértelmezés) a hangroaming használatát teszi lehetővé, ha az eszköz mobil hálózaton van.
- **Személyes**elérési pont: a **blokk** minden eszköz szinkronizálásával kikapcsolja a felhasználó eszközén lévő személyes hozzáférési pontokat. Előfordulhat, hogy ez a beállítás nem kompatibilis bizonyos szolgáltatókkal. **Nincs konfigurálva** (alapértelmezés) megtartja a személyes hozzáférési pont konfigurációját a felhasználó alapértelmezett beállításaként.

  > [!IMPORTANT]
  > Ezt a beállítást távoli eszköz műveletként kezeli a rendszer. Így ez a beállítás nem jelenik meg az eszköz felügyeleti profiljában. Minden alkalommal, amikor a személyes hozzáférési pont állapota megváltozik az eszközön, az Intune szolgáltatás letiltja a **személyes hozzáférési pontokat** . Az Intune-ban, ha a jelentéskészítési állapot sikert mutat, akkor tudja, hogy működik, még akkor is, ha a beállítás nem jelenik meg az eszköz felügyeleti profiljában.

- **Mobil használati szabályok (csak felügyelt alkalmazások esetén)**: adja meg azokat az adattípusokat, amelyeket a felügyelt alkalmazások használhatnak a mobil hálózatokon. A választható lehetőségek:
  - **A mobil adatmennyiség használatának tiltása**: az **összes felügyelt** alkalmazáshoz tartozó mobil adatmennyiség letiltása, vagy **adott alkalmazások kiválasztása**.
  - **A mobil adatátviteli funkció használatának letiltása barangolás közben**: az **összes felügyelt alkalmazáshoz** való barangolás vagy **adott alkalmazások kiválasztása**esetén tiltsa le a mobil adatátvitelt.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- Az **alkalmazás mobil adatfelhasználási beállításainak módosítása**: válassza a **Letiltás** lehetőséget az alkalmazás mobil adatfelhasználási beállításainak módosításainak elkerüléséhez. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy szabályozza, mely alkalmazások használhatják a mobil-adatszolgáltatásokat.
- A **mobil csomag beállításainak módosítása**: a **Letiltás** megakadályozza, hogy a felhasználók módosíthassák a mobil csomag beállításait. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a módosítások elvégzését.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

- **Személyes elérési pont felhasználói módosítása**: Ha **blokkolásra**van beállítva, a felhasználó nem módosíthatja a személyes hozzáférési pont beállítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a végfelhasználók számára, hogy engedélyezzék vagy letiltsák a személyes hozzáférési pontját.

  Ha letiltja ezt a beállítást, és letiltja a **személyes hozzáférési** pont beállítását, a személyes elérési pont ki van kapcsolva.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 12,2 és újabb verziók

- **Csak a konfigurációs profilokat használó Wi-Fi-hálózatok csatlakoztatása**: **megköveteli** , hogy az eszköz csak az Intune konfigurációs profiljain keresztül beállított Wi-Fi-hálózatokat használja. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz más Wi-Fi-hálózatokat használjon.
- **Wi-Fi mindig be van kapcsolva**: Ha a beállítás **kötelező**, a Wi-Fi a beállítások alkalmazásban marad. A beállításokban vagy a vezérlési központban nem kapcsolható ki, még akkor is, ha az eszköz Airplane módban van. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a Wi-Fi bekapcsolásának vagy kikapcsolásának szabályozását.

  A beállítás konfigurálása nem akadályozza meg, hogy a felhasználók kiválasszák a Wi-Fi hálózatot.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS és iPadOS 13,0 és újabb verziók

## <a name="connected-devices"></a>Csatlakoztatott eszközök

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Párosított Apple Watch – csukló-észlelés**: a párosított Apple Watch használatának **megkövetelése** a csukló észleléséhez. Ha szükséges, az Apple Watch nem jelenít meg értesítéseket, amikor nem kopott. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- Lejátszást **kérő kimenő kérelmek párosítása jelszavának**megkövetelése: párosítási jelszó **megkövetelése** , ha a felhasználó a közvetített tartalmat más Apple-eszközökre továbbítja. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára, hogy jelszó megadása nélkül közvetítse a tartalmat a lejátszási lista használatával.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **AirDrop**: **letiltja** a AirDrop használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirDrop funkció használatát a tartalmak a közeli eszközökkel való cseréjéhez.
- **Apple Watch-párosítás**: a **blokk** megakadályozza az Apple Watch párosítását. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz párosítva legyen egy Apple Watch használatával.
- **Bluetooth-módosítás**: a **Letiltás** leállítja a végfelhasználók számára a Bluetooth-beállítások módosítását az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a felhasználó módosítsa ezeket a beállításokat.
- **Az IOS-eszköz által párosítható eszközök vezérlése**a következővel: **nincs konfigurálva** (alapértelmezés) – a gazdagép párosítása lehetővé teszi a rendszergazda számára, hogy az IOS-eszköz által párosítható eszközöket biztosítson a rendszergazdának. A **blokk** megakadályozza a gazdagép párosítását.
- **AirPrint letiltása**: a **Letiltás** lehetőség kiválasztásával megakadályozhatja a AirPrint funkció használatát az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a AirPrint használatát.
  - **AirPrint hitelesítő adatok tárolásának letiltása a kulcstartóban**: a **blokkolás** megakadályozza a kulcstartó tárolását a Felhasználónév és a jelszó használatával az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirPrint-Felhasználónév és-jelszó tárolását a kulcstartó alkalmazásban.
  - **Megbízható TLS-tanúsítvány megkövetelése a AirPrint**: **megköveteli** , hogy az eszköz megbízható tanúsítványokat használjon a TLS-nyomtatással való kommunikációhoz.
  - **A AirPrint-nyomtatók iBeacon-felderítésének letiltása**: a **blokk** megakadályozza a rosszindulatú AirPrint Bluetooth-figyelőket a hálózati forgalom számára. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a AirPrint-nyomtatók reklámozását az eszközön.
- **Új közeli eszközök beállításának letiltása**: a **Letiltás** letiltja a megjelenő új eszközök beállítását. **Nincs konfigurálva** (az alapértelmezett beállítás) a felhasználók számára a többi közeli Apple-eszközhöz való kapcsolódásra vonatkozó kéréseket tesz lehetővé.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 11,0 és újabb verziók

- **Hozzáférés a fájlokhoz USB-meghajtón**: az eszközök csatlakozhatnak és megnyithatnak egy USB-meghajtón található fájlokat. A **Letiltás** beállítás megadásával megakadályozható, hogy az eszköz HOZZÁFÉRJEN az USB-meghajtóhoz a fájlok alkalmazásban, ha az USB-kapcsolat az eszközhöz csatlakozik. A funkció letiltása azt is megakadályozza, hogy a végfelhasználók fájlokat vigyenek át egy iPadhez csatlakoztatott USB-meghajtóra. **Nincs konfigurálva** (az alapértelmezett érték) a fájlok alkalmazásban található USB-meghajtó elérését teszi lehetővé.

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS és iPadOS 13,0 és újabb verziók

## <a name="keyboard-and-dictionary"></a>Billentyűzet és szótár

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **Word-definíciók keresése**: a **Letiltás** megakadályozza, hogy a felhasználó kiemelje a szót, majd megkeresse a definícióját az eszközön. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a hozzáférését a definíciós keresési szolgáltatáshoz.
- **Prediktív billentyűzetek**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi a prediktív billentyűzetek használatát arra, hogy a felhasználó által kívánt szavakat javasolják. A **Letiltás** megakadályozza ezt a funkciót.
- **Automatikus javítás**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az eszköz automatikusan kijavítsa a hibásan írt szavakat. A **tiltás** megakadályozza az automatikus javítást.
- **Billentyűzet helyesírás-ellenőrzés**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi a helyesírás-ellenőrző használatát az eszközön. A **Letiltás** lehetővé teszi a helyesírás-ellenőrzőt.
- **Billentyűparancsok**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi billentyűparancsok használatát az eszközön. A **Letiltás** megakadályozza, hogy a felhasználó billentyűparancsokat használjon.
- **Diktálás**: a **Letiltás** megakadályozza, hogy a felhasználó hangbevitelt használjon szöveg megadásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára a diktálási bevitel használatát.
- **QuickPath**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a QuickPath használatát, amely lehetővé teszi a folyamatos bevitelt az eszköz billentyűzetén. A felhasználók a kulcsok szövegének megírásával írhatják be a szavakat. A **Letiltás** megakadályozza, hogy a felhasználók a QuickPath használják. 

  Ez a funkció az alábbiakra vonatkozik:  
  - iOS 13,0 és iPadOS 13,0 és újabb

## <a name="cloud-and-storage"></a>Felhő és tárolás

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Titkosított biztonsági mentés**: az eszközök biztonsági mentéseit titkosítva **kell megadni.**
- **Felügyelt alkalmazások szinkronizálása a felhővel**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy az Intune-ban az alkalmazások szinkronizálják az adatait a felhasználó iCloud-fiókjával. A **blokk** megakadályozza az adatszinkronizálást az icloudba.
- **Vállalati könyv biztonsági mentésének letiltása**: a **Letiltás** gombra kattintva megakadályozhatja, hogy a felhasználók biztonsági mentést készítsenek a vállalati könyvekből. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak a könyvek biztonsági mentését.
- A **vállalati könyv metaadatainak szinkronizálásának letiltása (megjegyzések és csúcsfények)**: a **blokk** megakadályozza a jegyzetek és a kiemelések szinkronizálását a nagyvállalati könyvekben. **Nincs konfigurálva** (alapértelmezés) engedélyezi a szinkronizálást.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **A Photo Stream szinkronizálása iCloud**-ba: **nincs konfigurálva** (alapértelmezett) lehetővé teszi a felhasználók számára, hogy az eszközön lévő **Photo streamet** szinkronizálják az icloudba, és az összes felhasználó eszközén elérhetővé tegyék a fényképeket. A **blokk** megakadályozza, hogy a Photo Stream szinkronizáljon az icloudba. A funkció blokkolása adatvesztést eredményezhet. 
- **iCloud Photo Library**: a **Letiltás** beállítás megadásával letilthatja a fényképek és videók felhőben való tárolását az iCloud Photo Library használatával. A rendszer eltávolít minden olyan fényképet, amely nincs teljesen letöltve az iCloud Photo Library-ből az eszközre. **Nincs konfigurálva** (az alapértelmezett beállítás) az iCloud Photo Library használatát teszi lehetővé.
- **Megosztott Photo Stream**: válassza a **Letiltás** lehetőséget az **iCloud Photo Sharing** eszközön való letiltásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a megosztott fényképek folyamatos átvitelét.
- **Handoff**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy megkezdsék a munkát egy IOS-eszközön, majd folytatják az elindított munkát egy másik iOS-vagy MacOS-eszközön. A **blokk** megakadályozza ezt a handoff.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **Biztonsági mentés az icloudba**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználó számára az eszköz icloudba történő biztonsági mentését. A **Letiltás** leállítja a felhasználótól, hogy biztonsági másolatot készít az eszközről az icloudba.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **ICloud-dokumentum szinkronizálásának letiltása**: **nincs konfigurálva** (alapértelmezés) lehetővé teszi a dokumentumok és a kulcs-érték szinkronizálását az iCloud tárhelyére. A **blokk** megakadályozza, hogy az iCloud szinkronizálja a dokumentumokat és az adatokkal.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

- **ICloud-kulcstartó szinkronizálásának**letiltása: válassza a **Letiltás** lehetőséget a kulcstartóban tárolt hitelesítő adatok icloudba való szinkronizálásának letiltásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy szinkronizálják ezeket a hitelesítő adatokat.

  Az iOS 13,0-es verziótól kezdve a beállításhoz felügyelt eszközök szükségesek.

## <a name="autonomous-single-app-mode"></a>Autonóm Egyalkalmazásos mód

Ezekkel a beállításokkal konfigurálhatja az iOS-es eszközöket adott alkalmazások autonóm Egyalkalmazásos módban való futtatására. Ha ez a mód be van állítva, és az alkalmazás fut, az eszköz zárolva van. Csak ezt az alkalmazást futtathatja. Például hozzáadhat egy olyan alkalmazást, amely lehetővé teszi a felhasználók számára, hogy tesztelje az eszközt. Az alkalmazás használatának befejezésekor vagy a szabályzat eltávolításakor az eszköz visszatér a szokásos állapotába.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **Alkalmazás neve**: írja be a kívánt alkalmazás nevét.
- Alkalmazáscsomag- **azonosító**: adja meg a kívánt alkalmazás [köteg-azonosítóját](bundle-ids-built-in-ios-apps.md) .
- **Hozzáadás**: válassza a lehetőséget az alkalmazások listájának létrehozásához.

Egy CSV-fájlt is **importálhat** az alkalmazások neveinek és a Kötegük azonosítóinak listájával. Vagy **exportáljon** egy meglévő listát, amely tartalmazza az alkalmazásokat.

## <a name="kiosk"></a>Kioszkmód

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- Teljes **képernyős módban futtatandó alkalmazás**: válassza ki a kioszk módban futtatni kívánt alkalmazások típusát. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): a teljes képernyős beállítások nincsenek alkalmazva. Az eszköz nem fut kioszk módban.
  - **Áruházbeli alkalmazás**: adja meg egy alkalmazás URL-címét az iTunes App Store áruházban.
  - **Felügyelt alkalmazás**: válassza ki az Intune-ba felvett alkalmazást.
  - **Beépített alkalmazás**: Itt adhatja meg a beépített alkalmazás [köteg-azonosítóját](bundle-ids-built-in-ios-apps.md) .

- **Kisegítő érintés**: a kisegítő érintés kisegítő lehetőségének **megkövetelése** az eszközön. Ez a funkció segíti a felhasználók számára, hogy a képernyőn megjelenő kézmozdulatokat nehéz lehet megállapítani. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Színek invertálása**: a színek megfordításának **megkövetelése** beállítás megadásával a vizualizációt használó felhasználók módosíthatják a megjelenítési képernyőt. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Monó hang**: a MONO hang kisegítő lehetőségének **megkövetelése** az eszközön. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Hangvezérlés**: a **megkövetelése** lehetővé teszi a hangvezérlést az eszközön, és lehetővé teszi a felhasználóknak az operációs rendszer teljes körű vezérlését a Siri parancsokkal. A **nincs konfigurálva beállítás** letiltja a hangvezérlést az eszközön.

  Ez a beállítás a következőkre vonatkozik:  
  - iOS 13,0 és újabb verziók
  - iPadOS 13,0 és újabb verziók
  
  > [!TIP]
  > Ha a szervezete számára elérhető LOB-alkalmazások állnak rendelkezésre, és az iOS 13,0-as verzióban nem állnak készen a **Hangvezérlésre** , akkor azt javasoljuk, hogy **ne konfigurálja**ezt a beállítást.

- **Kommentár**: a kommentár kisegítő lehetőségének **megkövetelése** az eszközön, hogy a képernyőn hangosan lehessen olvasni a szöveget. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Nagyítás**: a nagyítás beállításának **megkövetelése** az eszközön, hogy a felhasználók érintsen a nagyításhoz a képernyőn. **Nincs konfigurálva** , vagy nem engedélyezi a szolgáltatást kioszk módban.
- **Automatikus zárolás**: a **blokk** megakadályozza az eszköz automatikus zárolását. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Csengés kapcsolója**: a **blokk** letiltja a csengetési (Mute) kapcsolót az eszközön. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Képernyő-elforgatás**: a **blokk** megakadályozza a képernyő tájolásának módosítását, amikor a felhasználó elforgatja az eszközt. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Alvó állapot gombja**: válassza a **Letiltás** lehetőséget a képernyő alvó állapotának letiltásához az eszközön. A **nincs konfigurálva** beállítás engedélyezi ezt a funkciót.
- **Érintés**: a **Letiltás** letiltja az érintőképernyőt az eszközön. A **nincs konfigurálva** beállítás lehetővé teszi a felhasználó számára az érintőképernyő használatát.
- **Hangerő gombok**: a **Letiltás** megakadályozza az eszközön a hangerő-szabályozó gombok használatát. A **nincs konfigurálva** beállítás engedélyezi a hangerő-szabályozó gombok használatát.
- **Kisegítő érintéses vezérlés**: **lehetővé teszi, hogy** a felhasználók a kisegítő érintés funkciót használják. A **nincs konfigurálva beállítás** letiltja ezt a funkciót.
- **Színinvertálás vezérlő**: **lehetővé teszi** a színek megfordítását, így a felhasználók módosíthatják a színek invertálása funkciót. A **nincs konfigurálva beállítás** letiltja ezt a funkciót.
- **Beszéljen a kijelölt szövegről**: engedélyezze a kisegítő lehetőségek **használatát** az eszközön. Ez a funkció olyan szöveget olvas be, amelyet a felhasználó hangosan választ ki. A **nincs konfigurálva beállítás** letiltja ezt a funkciót.
- **Hangvezérlés módosítása**: **lehetővé teszi** a felhasználók számára, hogy megváltoztassák a hangvezérelt vezérlés állapotát az eszközökön. A **nincs konfigurálva beállítás** megakadályozza, hogy a felhasználók megváltoztassák a hangvezérlés állapotát az eszközökön.

  Ez a beállítás a következőkre vonatkozik:  
  - iOS 13,0 és újabb verziók
  - iPadOS 13,0 és újabb verziók

- A kommentárok **szabályozása**: a kommentárok módosításának **engedélyezése lehetővé teszi** a felhasználóknak a kommentár-funkció frissítését, például hogy a képernyőn megjelenő szöveg milyen gyorsan legyen hangosan kiolvasva. A **nincs konfigurálva beállítás** megakadályozza a kommentárok módosítását.
- **Nagyítás-vezérlés**: a felhasználó által végrehajtott nagyítási módosítások **engedélyezése** . A **nincs konfigurálva beállítás** megakadályozza a nagyítás módosítását.

> [!NOTE]
> Az iOS-eszközök Kioszk módra való konfigurálása előtt felügyelt módba kell állítania az eszközt az Apple Configurator eszközzel vagy az Apple Device Enrollment Program készülékregisztráció-kezelővel. Tekintse meg az Apple konfiguráló eszközének használatát ismertető témakört.
> Ha a megadott iOS-alkalmazás a profil hozzárendelését követően települ, az eszköz mindaddig nem lép kioszk módba, amíg az eszköz újra nem indul.

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: eszközök beléptetése, automatikus eszközök beléptetése (felügyelt)

- **Jelöletlen e-mail-tartományok** > **e-mail-tartomány URL-címe**: adjon hozzá egy vagy több URL-címet a listához. Ha a végfelhasználók a megadott tartománytól eltérő tartományból kapnak e-mailt, az iOS-es mail alkalmazásban az e-mail nem megbízhatóként van megjelölve.

- **Felügyelt webtartományok** > **webes tartomány URL-címe**; Adjon hozzá egy vagy több URL-címet a listához. Ha a rendszer letölti a dokumentumokat a megadott tartományokból, felügyelt tekintendők. Ez a beállítás csak a Safari böngészővel letöltött dokumentumokra vonatkozik.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>A beállítások a következőkre vonatkoznak: automatikus eszközök beléptetése (felügyelt)

- **Safari-jelszó automatikus kitöltés tartomány** > **tartomány URL-címe**: adjon hozzá egy vagy több URL-címet a listához. A felhasználók csak a listában szereplő URL-címekhez tartozó webes jelszavakat menthetnek. Ez a beállítás csak a Safari böngészőre és a felügyelt módban lévő eszközökre vonatkozik. Ha nem ad meg URL-címet, a jelszavakat az összes webhelyről mentheti.

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

[Rendelje hozzá a profilt](../device-profile-assign.md), és [kövesse nyomon az állapotát](../device-profile-monitor.md).

A [MacOS](device-restrictions-macos.md) -eszközökön is korlátozhatja az eszközök funkcióit és beállításait.
