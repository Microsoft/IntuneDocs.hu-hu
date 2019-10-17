---
title: macOS-eszköz funkciójának beállításai a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg a macOS-eszközök AirPrint való konfigurálásának beállításait, és szabja testre a bejelentkezési ablakot a Microsoft Intune lévő főkapcsoló gombok megjelenítéséhez vagy elrejtéséhez. Tekintse meg a AirPrint-kiszolgáló IP-címének, elérési útjának és portbeállítások beszerzésének lépéseit a hálózaton. Ezeket a beállításokat egy eszköz konfigurációs profiljában a macOS-eszközök funkcióinak konfigurálásához használhatja.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17d0baeeb6b193be6acf8d6087c26a66b18642c5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506668"
---
# <a name="macos-device-feature-settings-in-intune"></a>macOS-eszköz funkciójának beállításai az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune tartalmaz néhány beépített beállítást a macOS-eszközök funkcióinak testreszabásához. A rendszergazdák például hozzáadhatnak AirPrint-nyomtatókat, kiválaszthatják, hogy a felhasználók hogyan jelentkeznek be, konfigurálják az energiagazdálkodást, az egyszeri bejelentkezéses hitelesítés használatát és egyebeket.

Ezekkel a szolgáltatásokkal vezérelheti a macOS-eszközöket a mobileszköz-kezelési (MDM) megoldás részeként.

Ez a cikk felsorolja ezeket a beállításokat, és leírja az egyes beállításokat. Emellett felsorolja azokat a lépéseket, amelyekkel lekérheti a AirPrint-nyomtatók IP-címét, elérési útját és portját a Terminal app (Emulator) használatával. Az eszköz funkcióival kapcsolatos további információkért lépjen az [iOS-vagy MacOS-eszköz funkció beállításainak hozzáadása lehetőségre](device-features-configure.md).

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy MacOS-eszköz konfigurációs profilt](device-features-configure.md).

> [!NOTE]
> Ezek a beállítások a különböző regisztrációs típusokra vonatkoznak, és egyes beállítások az összes regisztrációs lehetőségre érvényesek. A különböző regisztrációs típusokkal kapcsolatos további információkért lásd: [MacOS-regisztráció](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment"></a>Beállítások a következőkre vonatkoznak: eszköz beléptetése

- **IP-cím**: adja meg a nyomtató IPv4-vagy IPv6-címét. Ha állomásneveket használ a nyomtatók azonosítására, akkor az IP-címet a nyomtatónak a terminál alkalmazásban történő pingelésével érheti el. [Az IP-cím és az elérési út](#get-the-ip-address-and-path) (ebben a cikkben) beszerzése további részleteket tartalmaz.
- **Elérési út**: adja meg a nyomtató elérési útját. Az elérési út általában `ipp/print` a hálózatban lévő nyomtatókhoz. [Az IP-cím és az elérési út](#get-the-ip-address-and-path) (ebben a cikkben) beszerzése további részleteket tartalmaz.
- **Port** (iOS 11,0 és újabb): adja meg a AirPrint célhelyének figyelési portját. Ha üresen hagyja ezt a tulajdonságot, a AirPrint az alapértelmezett portot használja.
- **TLS** (iOS 11,0 és újabb): válassza az **Engedélyezés** lehetőséget a AirPrint-kapcsolatok Transport Layer Security (TLS) használatával történő biztonságossá tételéhez.

- **Hozzáadás** A AirPrint-kiszolgáló. Több AirPrint-kiszolgálót is hozzáadhat.

**Importálhat** egy vesszővel tagolt (. csv) fájlt is, amely tartalmazza a AirPrint-nyomtatók listáját. Emellett a AirPrint-nyomtatók Intune-ban való hozzáadása után **exportálhatja** a listát.

### <a name="get-the-ip-address-and-path"></a>Az IP-cím és az elérési út lekérése

AirPrinter-kiszolgálók hozzáadásához szüksége lesz a nyomtató IP-címére, az erőforrás elérési útjára és a portra. Az alábbi lépések bemutatják, hogyan kérheti le ezeket az információkat.

1. Olyan Mac gépen, amely ugyanahhoz a helyi hálózathoz (alhálózat) csatlakozik, mint a AirPrint-nyomtatók, nyissa meg a **terminált** (a **/Applications/Utilities alatt**).
2. A Terminal alkalmazásban írja be a `ippfind` értéket, majd kattintson az ENTER gombra.

    Jegyezze fel a nyomtató adatait. Előfordulhat például, hogy a `ipp://myprinter.local.:631/ipp/port1` értékhez hasonló értéket ad vissza. Az első rész a nyomtató neve. Az utolsó rész (`ipp/port1`) az erőforrás elérési útja.

3. A terminálban írja be a `ping myprinter.local` értéket, majd kattintson az ENTER gombra.

   Jegyezze fel az IP-címet. Előfordulhat például, hogy a `PING myprinter.local (10.50.25.21)` értékhez hasonló értéket ad vissza.

4. Használja az IP-cím és az erőforrás elérési útjának értékét. Ebben a példában az IP-cím `10.50.25.21`, az erőforrás elérési útja pedig `/ipp/port1`.

## <a name="login-items"></a>Bejelentkezési elemek

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Fájlok, mappák és egyéni alkalmazások**: **adja** meg a megnyitni kívánt fájl, mappa, egyéni alkalmazás vagy rendszeralkalmazás elérési útját, amikor egy felhasználó bejelentkezik az eszközre. A szervezete számára létrehozott vagy testre szabott rendszeralkalmazások vagy alkalmazások jellemzően a `Applications` mappában találhatók, és a `/Applications/AppName.app`-hez hasonló elérési úttal rendelkeznek. 

  Számos fájlt, mappát és alkalmazást adhat hozzá. Írja be például a következőt:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Ha bármilyen alkalmazást, mappát vagy fájlt ad hozzá, ügyeljen arra, hogy a helyes elérési utat adja meg. Nem minden elem szerepel a `Applications` mappában. Ha a felhasználó egy elemet helyez át egyik helyről a másikra, az elérési út megváltozik. Ez az áthelyezett tétel nem nyílik meg, amikor a felhasználó bejelentkezik.

## <a name="login-window"></a>Bejelentkezési ablak

### <a name="settings-apply-to-device-enrollment"></a>Beállítások a következőkre vonatkoznak: eszköz beléptetése

#### <a name="window-layout"></a>Ablak elrendezése

- **További információk megjelenítése a menüsávban**: Ha a menüsorban az időpont van kiválasztva, az **Engedélyezés** megjeleníti az állomásnév és a MacOS verzióját. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg ezt az információt a menüsávon.
- **Banner**: adjon meg egy üzenetet, amely megjelenik az eszköz bejelentkezési képernyőjén. Adja meg például a szervezeti adatokat, egy üdvözlő üzenetet, az elveszett és a talált információkat, és így tovább.
- **Válassza a bejelentkezési formátum elemet**: válassza ki, hogy a felhasználók hogyan jelentkezzenek be az eszközre. A választható lehetőségek:
  - **Felhasználónév és jelszó kérése** (alapértelmezett): a felhasználóknak felhasználónevet és jelszót kell megadniuk.
  - Az **összes felhasználó listázása, jelszó kérése**: a felhasználóknak a felhasználónevet a felhasználói listából kell kiválasztaniuk, majd meg kell adniuk a jelszavukat. Konfigurálja a következőket is:

    - **Helyi felhasználók**: az **Elrejtés** nem jeleníti meg a felhasználói listán szereplő helyi felhasználói fiókokat, amelyek magukban foglalhatják a standard és a rendszergazdai fiókokat. Csak a hálózat és a rendszer felhasználói fiókjai jelennek meg. **Nincs konfigurálva** (alapértelmezés) a felhasználók listájában a helyi felhasználói fiókokat jeleníti meg.
    - **Mobileszközök**: az **Elrejtés** nem jeleníti meg a felhasználói listán szereplő Mobile-fiókokat. **Nincs konfigurálva** (alapértelmezés) a felhasználók listájában látható Mobile-fiókokat jeleníti meg. Egyes Mobile-fiókok hálózati felhasználóként jelenhetnek meg.
    - **Hálózati felhasználók**: válassza a **Megjelenítés** lehetőséget a felhasználók listájában szereplő hálózati felhasználók listázásához. **Nincs konfigurálva** (az alapértelmezett) nem jeleníti meg a hálózati felhasználói fiókokat a felhasználók listájában.
    - Rendszergazda **felhasználók**: az **Elrejtés** nem jeleníti meg a rendszergazdai felhasználói fiókokat a felhasználók listájában. **Nincs konfigurálva** (alapértelmezés) a felhasználók listájában a rendszergazdai felhasználói fiókokat jeleníti meg.
    - **Egyéb felhasználók**: válassza a **Megjelenítés** lehetőséget a felhasználók listájában szereplő **egyéb...** felhasználók listázásához. **Nincs konfigurálva** (az alapértelmezett) nem jeleníti meg a többi felhasználói fiókot a felhasználók listájában.

#### <a name="login-screen-power-settings"></a>Bejelentkezési képernyő energiagazdálkodási beállításai

- **Leállítás gomb**: az **Elrejtés** nem jelenik meg a bejelentkezési képernyőn a Leállítás gomb. **Nincs konfigurálva** (alapértelmezés) a Leállítás gombot jeleníti meg.
- **Újraindítás gomb**: az **Elrejtés** gomb nem jeleníti meg az újraindítás gombot a bejelentkezési képernyőn. **Nincs konfigurálva** (alapértelmezés) az újraindítás gombot jeleníti meg.
- **Alvó állapot gomb**: az **Elrejtés** nem jelenik meg a bejelentkezési képernyő alvó állapot gombján. **Nincs konfigurálva** (alapértelmezés) az alvó gomb megjelenítése.

#### <a name="other"></a>Más

- **Felhasználói bejelentkezés letiltása a konzolról**: **letiltja** a bejelentkezéshez használt MacOS-parancssor elrejtése. A tipikus felhasználók esetében **Tiltsa le** ezt a beállítást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a speciális felhasználók számára a bejelentkezést a MacOS parancssor használatával. A konzol üzemmódjának megadásához a felhasználók a username (Felhasználónév) mezőbe `>console` értéket kell megadniuk, és hitelesíteniük kell magukat a konzol ablakban.

#### <a name="apple-menu"></a>Apple menü

Miután a felhasználók bejelentkeznek az eszközökre, a következő beállítások befolyásolhatják, hogy milyen műveleteket végezhetnek el.

- **Leállítás letiltása**: a **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a **Leállítás** lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az eszköz **Leállítás** menüpontjának kiválasztását.
- **Újraindítás letiltása**: a **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók a felhasználó bejelentkezése után kiválasszanak az **Újraindítás** lehetőséget. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az **Újraindítási** menüelem kiválasztását az eszközön.
- Kikapcsolás **letiltása**: a **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók **bejelentkeznek** a kikapcsolás lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy kiválasszanak a **kikapcsolt menüelemet** az eszközön.
- Kijelentkezés **letiltása** (MacOS 10,13 és újabb): a **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók **bejelentkeznek a kijelentkezés** lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a **kijelentkezés** menüpont kiválasztását az eszközön.
- **Zárolási képernyő letiltása** (MacOS 10,13 és újabb): a **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a **zárolási képernyő** lehetőségre. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy kiválassza a **zárolási képernyő** menüelemét az eszközön.

## <a name="single-sign-on-app-extension"></a>Egyszeri bejelentkezési alkalmazás bővítménye

Ez a funkció az alábbiakra vonatkozik:

- macOS 10,15 és újabb verziók

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus 

- **Egyszeri bejelentkezéses alkalmazás bővítményének típusa**: válassza ki a hitelesítő adatok egyszeri bejelentkezéses alkalmazás-bővítményének típusát. Az SSO app Extension-profil mentésekor nem módosítható az egyszeri bejelentkezéses alkalmazás bővítményének típusa. A választható lehetőségek:

  - **Nincs konfigurálva**: az alkalmazás-bővítmények nem használatosak. Az egyszeri bejelentkezéses alkalmazások kiterjesztésének letiltásához állítsa át az egyszeri bejelentkezéses alkalmazás kiterjesztésének típusát a **Kerberos** vagy a **hitelesítő adatok** közül a **nincs konfigurálva**értékre
  - **Hitelesítő adatok**: általános, testreszabható hitelesítőadat-alkalmazási bővítmény használata az egyszeri bejelentkezés használatához. Győződjön meg róla, hogy ismeri a szervezete SSO-alkalmazásának bővítmény-AZONOSÍTÓját és a csoport AZONOSÍTÓját.  
  - **Kerberos**: az Apple beépített Kerberos-bővítményét használja, amely megtalálható a macOS Catalina 10,15-es és újabb verzióiban. Ez a beállítás a **hitelesítőadat** -alkalmazás kiterjesztésének Kerberos-specifikus verziója.

  > [!TIP]
  > A **hitelesítő adatok** típusával adja hozzá a saját konfigurációs értékeit, hogy áthaladjon a bővítményen. Ehelyett érdemes lehet az Apple által biztosított beépített konfigurációs beállításokat használni a **Kerberos** -típusban.

- **BŐVÍTMÉNY azonosítója** (csak hitelesítő adatok): adja meg az SSO-alkalmazás kiterjesztését azonosító köteg-azonosítót, például `com.apple.ssoexample`.
- **Csoport azonosítója** (csak hitelesítő adatok): adja meg az egyszeri bejelentkezéses alkalmazás-bővítmény csoportjának azonosítóját. A csapat azonosítója az Apple által generált 10 karakteres alfanumerikus (számok és betűk) karakterlánc, például `ABCDE12345`. 

  [Keresse meg a csoport azonosítóját (az](https://help.apple.com/developer-account/#/dev55c3c710c) Apple webhelyének megnyitása), amely további információkat tartalmaz.

- **Tartomány**: írja be a Kerberos-tartomány nevét. A tartománynevet tőkésíteni kell, például `CONTOSO.COM`. A tartománynév általában megegyezik a DNS-tartománynévvel, de minden nagybetűvel.
- **Tartományok**: Itt adhatja meg az SSO-n keresztül hitelesíthető helyek tartomány-vagy állomásnevek nevét. Ha például a webhely `mysite.contoso.com`, akkor `mysite` az állomásnév, és a `contoso.com` a tartománynév. Ha a felhasználók bármelyik webhelyhez csatlakoznak, az alkalmazás-bővítmény kezeli a hitelesítési kihívást. Ez a hitelesítés lehetővé teszi a felhasználók számára a bejelentkezéshez a Face ID, a Touch ID vagy az Apple pincode/PIN-kód használatát.

  - Az egyszeri bejelentkezési alkalmazás bővítményének Intune-profiljainak minden tartományának egyedinek kell lennie. A tartományokat nem lehet megismételni a Bejelentkezési alkalmazás bővítményeinek egyik profiljában sem, még akkor is, ha különböző típusú egyszeri bejelentkezéses alkalmazás-bővítményeket használ.
  - Ezek a tartományok nem megkülönböztetik a kis-és nagybetűket

- **További konfiguráció** (csak hitelesítő adatok): adja meg az egyszeri bejelentkezéshez szükséges további adatokat, amelyeket át kell adni az SSO-alkalmazás kiterjesztésének:
  - **Konfigurációs kulcs**: adja meg a hozzáadni kívánt elem nevét, például `user name`.
  - **Value Type (értéktípus**): adja meg az adattípust. A választható lehetőségek:

    - Sztring
    - Boolean: a **konfigurációs érték**mezőben adja meg a `True` vagy a `False` értéket.
    - Egész szám: a **konfigurációs érték**mezőbe írjon be egy számot.
    
  - **Konfigurációs érték**: adja meg az adathalmazt.
  
  - **Hozzáadás**: válassza ki a konfigurációs kulcsok hozzáadásához.

- **Kulcstartó használata** (csak Kerberos): válassza a **Letiltás** lehetőséget, hogy megakadályozza a jelszavak mentését és tárolását a kulcstartóban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszavak mentését és tárolását a kulcstartóban.  
- **Face ID, Touch ID vagy PIN kód** (csak Kerberos): **megköveteli** , hogy a felhasználók belépjenek a saját Face ID, Touch ID vagy Apple PIN-kóddal a hozzáadott tartományba való bejelentkezéshez. **Nincs konfigurálva** (alapértelmezés) nem igényli, hogy a felhasználók biometrikus vagy PIN-kódot használjanak a bejelentkezéshez.
- **Alapértelmezett tartomány** (csak Kerberos): válassza az **Engedélyezés** lehetőséget az alapértelmezett tartományként megadott **tartomány** értékének megadásához. **Nincs konfigurálva** (alapértelmezés) nem állítja be az alapértelmezett tartományt.

  > [!TIP]
  > - Akkor **engedélyezze** ezt a beállítást, ha több Kerberos SSO-alkalmazás-bővítményt konfigurál a szervezetében.
  > - Ha több birodalmat használ, **engedélyezze** ezt a beállítást. Az alapértelmezett tartományként megadott **tartományi** értéket állítja be.
  > - Ha csak egy tartománya van, hagyja meg, hogy **nincs konfigurálva** (alapértelmezett).

- Automatikus **észlelés** (csak Kerberos esetén): Ha a **blokkolás**értékre van állítva, a Kerberos-bővítmény nem használja automatikusan az LDAP és a DNS szolgáltatást a Active Directory hely nevének meghatározásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a bővítmény automatikusan megkeresse a Active Directory hely nevét.
- **Jelszó módosítása** (csak Kerberos esetén): a **Letiltás** megakadályozza, hogy a felhasználók megváltoztassák a megadott tartományba való bejelentkezéshez használt jelszavakat. **Nincs konfigurálva** (alapértelmezés) a jelszó módosítását teszi lehetővé.  
- **Jelszó-szinkronizálás** (csak Kerberos): válassza az **Engedélyezés** lehetőséget a felhasználók helyi jelszavainak Azure ad-hez való szinkronizálásához. **Nincs konfigurálva** (az alapértelmezett) letiltja a jelszó-szinkronizálást az Azure ad-be. Ezt a beállítást Alternatív megoldásként vagy az SSO-ként történő biztonsági mentésként használhatja. Ez a beállítás nem működik, ha a felhasználók Apple Mobile-fiókkal jelentkeznek be.
- **Windows Server Active Directory jelszó bonyolultsága** (csak Kerberos): válassza a **kötelező** lehetőséget a felhasználói jelszavak kényszerítéséhez Active Directory jelszavának bonyolultságára vonatkozó követelmények teljesítéséhez. További információkért lásd: a [jelszónak meg kell felelnie a bonyolultsági feltételeknek](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **Nincs konfigurálva** (alapértelmezés) nem igényli, hogy a felhasználók megfeleljenek Active Directory jelszavára vonatkozó követelménynek.
- **Jelszó minimális hossza** (csak Kerberos): Itt adhatja meg, hogy hány karakterből állhatnak a felhasználók jelszava. **Nincs konfigurálva** (alapértelmezés) nem kényszeríti ki a jelszó minimális hosszát a felhasználóknál.
- **Jelszó újrafelhasználásának korlátja** (csak Kerberos): adja meg, hogy hány új jelszót kell használni a 1-24-től, amelyet csak akkor használhat, ha a tartományon újra fel nem használ egy korábbi jelszót. **Nincs konfigurálva** (az alapértelmezett) nem érvényesíti a jelszó-újrahasznosítási korlátot.
- **Jelszó minimális kora** (csak Kerberos): Itt adhatja meg, hogy hány nap elteltével kell használni a jelszót a tartományon, mielőtt a felhasználó módosíthatja azt. **Nincs konfigurálva** (az alapértelmezett érték) nem kényszeríti ki a minimális korhatárt a jelszó megváltozása előtt.
- **Jelszó lejáratáról szóló értesítés** (csak Kerberos): adja meg, hogy hány nap elteltével járjon le a jelszó, hogy a felhasználók értesítést kapjanak a jelszavuk lejáratáról. **Nincs konfigurálva** (alapértelmezés) `15` napot használ.
- **Jelszó lejárata** (csak Kerberos esetén): adja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát. **Nincs konfigurálva** (alapértelmezett): a felhasználói jelszavak soha nem járnak le.
- **Egyszerű név** (csak Kerberos): adja meg a Kerberos-tag felhasználónevét. Nem kell belefoglalni a tartománynevet. Például `user@contoso.com`, `user` az egyszerű név, és a `contoso.com` a tartománynév.
- **Active Directory Helykód** (csak Kerberos): adja meg annak a Active Directory helynek a nevét, amelyet a Kerberos-bővítménynek használnia kell. Előfordulhat, hogy nem kell módosítania ezt az értéket, mivel a Kerberos-bővítmény automatikusan megkeresi a Active Directory hely kódját.
- **Gyorsítótár neve** (csak Kerberos): adja meg a Kerberos-gyorsítótár általános biztonsági szolgáltatásainak (GSS) nevét. Valószínűleg nem kell beállítania ezt az értéket.  
- **Jelszóra vonatkozó követelmények üzenet** (csak Kerberos): adja meg a szervezete jelszavának a felhasználók számára megjelenített szöveges verzióját. Az üzenet akkor jelenik meg, ha nincs szükség Active Directory jelszavával kapcsolatos bonyolultsági követelményekre, vagy ne adja meg a jelszó minimális hosszát.  
- Alkalmazáscsomag- **azonosítók** (csak Kerberos): **adja hozzá** az App Bundle-azonosítókat, amelyeknek egyszeri bejelentkezést kell használniuk az eszközökön. Ezek az alkalmazások hozzáférést kapnak a Kerberos-jegy biztosításához, a hitelesítési jegyet, és hitelesítik a felhasználókat a hozzáférésre jogosult szolgáltatásokhoz.
- **Tartományi tartomány leképezése** (csak Kerberos): **adja** meg a tartományhoz HOZZÁRENDELNI kívánt tartományi DNS-utótagokat. Akkor használja ezt a beállítást, ha a gazdagépek DNS-nevei nem egyeznek a tartománynév nevével. Valószínűleg nem kell létrehoznia ezt az egyéni tartomány – tartomány társítást.

## <a name="associated-domains"></a>Társított tartományok

Az Intune-ban a következőket teheti:

- Számos alkalmazás-tartomány társítást vehet fel.
- Számos tartományt társíthat ugyanahhoz az alkalmazáshoz.

Ez a funkció az alábbiakra vonatkozik:

- macOS 10,15 és újabb verziók

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőre vonatkoznak: minden regisztrációs típus

- **Alkalmazás azonosítója**: adja meg az alkalmazásnak a webhelyhez társítandó alkalmazás-azonosítóját. Az alkalmazás azonosítója tartalmazza a csoport AZONOSÍTÓját és a köteg AZONOSÍTÓját: `TeamID.BundleID`.

  A csoport azonosítója az Apple által az alkalmazások fejlesztői számára generált, 10 karakterből álló alfanumerikus (betűk és számok) karakterlánc, például `ABCDE12345`. [Keresse meg a csoport azonosítóját](https://help.apple.com/developer-account/#/dev55c3c710c)  (az Apple webhelyének megnyitása), amely további információkat tartalmaz.

  A Bundle-azonosító egyedileg azonosítja az alkalmazást, és általában fordított tartománynév-jelöléssel van formázva. A Finder csomag azonosítója például `com.apple.finder`. A csomag AZONOSÍTÓjának megkereséséhez használja az AppleScript-t a terminálban:

  `osascript -e 'id of app "ExampleApp"'`

- **Tartomány**: adja meg az alkalmazáshoz társítandó webhely tartományát. A tartomány tartalmaz egy szolgáltatástípus és egy teljes tartománynevet, például `webcredentials:www.contoso.com`.

  A társított tartomány összes altartományával egyeztetheti `*.` (egy csillag helyettesítő karakter és egy pont) megadásával a tartomány elejéig. Az időszakot kötelező megadni. A pontos tartományok magasabb prioritással rendelkeznek, mint a helyettesítő tartományok. Így a fölérendelt tartományokból származó minták egyeztetése akkor történik meg, *Ha* nem található egyezés a teljes altartományban.

  A szolgáltatás típusa a következő lehet:

  - **authsrv**: egyszeri bejelentkezéses alkalmazás bővítmény
  - **applink**: univerzális hivatkozás
  - **webhitelesítő adatok**: jelszó automatikus kitöltése

- **Hozzáadás**: válassza ki az alkalmazások és a társított tartományok hozzáadásához.

> [!TIP]
> A hibakereséshez a macOS-eszközön nyissa meg a **System Preferences** > **profilok**elemet. Erősítse meg, hogy a létrehozott profil az eszköz profiljai listán található. Ha szerepel a felsorolásban, győződjön meg arról, hogy a **társított tartományok konfigurációja** szerepel a profilban, és tartalmazza a megfelelő alkalmazás-azonosítót és-tartományokat.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az eszközök funkcióit az [iOS](ios-device-features-settings.md)rendszeren is megadhatja.
