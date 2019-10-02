---
title: macOS-eszköz funkciójának beállításai a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg a macOS-eszközök AirPrint való konfigurálásának beállításait, és szabja testre a bejelentkezési ablakot a Microsoft Intune lévő főkapcsoló gombok megjelenítéséhez vagy elrejtéséhez. Tekintse meg a AirPrint-kiszolgáló IP-címének, elérési útjának és portbeállítások beszerzésének lépéseit a hálózaton. Ezeket a beállításokat egy eszköz konfigurációs profiljában a macOS-eszközök funkcióinak konfigurálásához használhatja.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3e270fc3efcc92a138fe97cbe599f7bd2bf1e55
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730567"
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

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

- **IP-cím**: Adja meg a nyomtató IPv4-vagy IPv6-címeit. Ha állomásneveket használ a nyomtatók azonosítására, akkor az IP-címet a nyomtatónak a terminál alkalmazásban történő pingelésével érheti el. [Az IP-cím és az elérési út lekérése](#get-the-ip-address-and-path) (ebben a cikkben) további részleteket tartalmaz.
- **Elérési út**: Adja meg a nyomtató elérési útját. Az elérési út `ipp/print` általában a hálózatban lévő nyomtatókhoz van. [Az IP-cím és az elérési út lekérése](#get-the-ip-address-and-path) (ebben a cikkben) további részleteket tartalmaz.
- **Port** (iOS 11,0 és újabb verziók): Adja meg a AirPrint célhelyének figyelési portját. Ha üresen hagyja ezt a tulajdonságot, a AirPrint az alapértelmezett portot használja.
- **TLS** (iOS 11,0 és újabb verziók): Válassza az **Engedélyezés** lehetőséget a AirPrint-kapcsolatok TRANSPORT Layer Security (TLS) használatával történő biztonságossá tételéhez.

- **Hozzáadás** A AirPrint-kiszolgáló. Több AirPrint-kiszolgálót is hozzáadhat.

**Importálhat** egy vesszővel tagolt (. csv) fájlt is, amely tartalmazza a AirPrint-nyomtatók listáját. Emellett a AirPrint-nyomtatók Intune-ban való hozzáadása után **exportálhatja** a listát.

### <a name="get-the-ip-address-and-path"></a>Az IP-cím és az elérési út lekérése

AirPrinter-kiszolgálók hozzáadásához szüksége lesz a nyomtató IP-címére, az erőforrás elérési útjára és a portra. Az alábbi lépések bemutatják, hogyan kérheti le ezeket az információkat.

1. Olyan Mac gépen, amely ugyanahhoz a helyi hálózathoz (alhálózat) csatlakozik, mint a AirPrint-nyomtatók, nyissa meg a terminált (a **/Applications/Utilities alatt**).
2. A terminál alkalmazásban írja be `ippfind`a parancsot, majd kattintson az ENTER (bevitel) gombra.

    Jegyezze fel a nyomtató adatait. Előfordulhat például, hogy a `ipp://myprinter.local.:631/ipp/port1`következőhöz hasonló értéket ad vissza:. Az első rész a nyomtató neve. Az utolsó rész (`ipp/port1`) az erőforrás elérési útja.

3. A terminálon írja be `ping myprinter.local`a parancsot, majd kattintson az ENTER (bevitel) gombra.

   Jegyezze fel az IP-címet. Előfordulhat például, hogy a `PING myprinter.local (10.50.25.21)`következőhöz hasonló értéket ad vissza:.

4. Használja az IP-cím és az erőforrás elérési útjának értékét. Ebben a példában az IP-cím `10.50.25.21`, az erőforrás elérési útja pedig. `/ipp/port1`

## <a name="login-items"></a>Bejelentkezési elemek

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Fájlok, mappák és egyéni alkalmazások**: **Adja** meg a megnyitni kívánt fájl, mappa, egyéni alkalmazás vagy rendszeralkalmazás elérési útját, amikor egy felhasználó bejelentkezik az eszközre. A szervezete számára létrehozott vagy testre szabott rendszeralkalmazások vagy alkalmazások általában a `Applications` mappában találhatók, a következőhöz `/Applications/AppName.app`hasonló elérési úttal. 

  Számos fájlt, mappát és alkalmazást adhat hozzá. Írja be például a következőt:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Ha bármilyen alkalmazást, mappát vagy fájlt ad hozzá, ügyeljen arra, hogy a helyes elérési utat adja meg. Nem minden elem szerepel a `Applications` mappában. Ha a felhasználó egy elemet helyez át egyik helyről a másikra, az elérési út megváltozik. Ez az áthelyezett tétel nem nyílik meg, amikor a felhasználó bejelentkezik.

## <a name="login-window"></a>Bejelentkezési ablak

### <a name="settings-apply-to-device-enrollment"></a>A beállítások a következőkre vonatkoznak: Eszközök beléptetése

#### <a name="window-layout"></a>Ablak elrendezése

- **További információk megjelenítése a menüsorban**: Ha a menüsorban az időszak van kiválasztva, az **Engedélyezés** megjeleníti az állomásnév és a MacOS verzióját. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg ezeket az információkat a menüsávon.
- **Szalagcím**: Adja meg az eszköz bejelentkezési képernyőjén látható üzenetet. Adja meg például a szervezeti adatokat, egy üdvözlő üzenetet, az elveszett és a talált információkat, és így tovább.
- **Adja meg a bejelentkezési formátumot**: Válassza ki, hogyan jelentkeznek be a felhasználók az eszközre. A választható lehetőségek:
  - **Felhasználónév és jelszó kérése** (alapértelmezett): Felhasználónevet és jelszót kell megadnia a felhasználóknak.
  - **Az összes felhasználó listázása, jelszó kérése**: A felhasználóknak a felhasználónevet a felhasználói listából kell kiválasztaniuk, majd meg kell adniuk a jelszavukat. Konfigurálja a következőket is:

    - **Helyi felhasználók**: Az **Elrejtés** nem jeleníti meg a felhasználók listájában a helyi felhasználói fiókokat, amelyek magukban foglalhatják a standard és a rendszergazdai fiókokat. Csak a hálózat és a rendszer felhasználói fiókjai jelennek meg. **Nincs konfigurálva** (alapértelmezés) megjeleníti a helyi felhasználói fiókokat a felhasználók listájában.
    - **Mobile-fiókok**: Az **Elrejtés** nem jeleníti meg a mobil fiókokat a felhasználók listájában. **Nincs konfigurálva** (alapértelmezés) megjeleníti a felhasználói listán szereplő mobil fiókokat. Egyes Mobile-fiókok hálózati felhasználóként jelenhetnek meg.
    - **Hálózati felhasználók**: Válassza a **Megjelenítés** lehetőséget a felhasználók listájában szereplő hálózati felhasználók listázásához. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a hálózati felhasználói fiókokat a felhasználók listájában.
    - **Rendszergazda felhasználók**: Az **Elrejtés** nem jeleníti meg a rendszergazdai felhasználói fiókokat a felhasználók listájában. **Nincs konfigurálva** (alapértelmezés) a felhasználók listájában a rendszergazdai felhasználói fiókokat jeleníti meg.
    - **Egyéb felhasználók**: Válassza a **Megjelenítés** elemet a felhasználók listájának **más...** felhasználóinak listázásához. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a többi felhasználói fiókot a felhasználók listájában.

#### <a name="login-screen-power-settings"></a>Bejelentkezési képernyő energiagazdálkodási beállításai

- **Leállítás gomb**: Az **Elrejtés** gomb nem jelenik meg a bejelentkezési képernyő leállítás gombjával. **Nincs konfigurálva** (alapértelmezés) megjeleníti a Leállítás gombot.
- **Újraindítás gomb**: Az **Elrejtés** gomb nem jeleníti meg az újraindítás gombot a bejelentkezési képernyőn. **Nincs konfigurálva** (alapértelmezés) az újraindítás gombot jeleníti meg.
- **Alvó gomb**: Az **Elrejtés** gomb nem jeleníti meg az alvó gombot a bejelentkezési képernyőn. **Nincs konfigurálva** (alapértelmezés) az alvó gomb megjelenítése.

#### <a name="other"></a>Egyéb

- **Felhasználói bejelentkezés letiltása a konzolról**: A **Letiltás letiltja** a bejelentkezéshez használt MacOS-parancssort. A tipikus felhasználók esetében **Tiltsa le** ezt a beállítást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a haladó felhasználók a macOS parancssor használatával jelentkezzenek be. A konzol mód megadásához a `>console` felhasználók a Felhasználónév mezőbe lépnek be, és a konzol ablakban kell hitelesíteniük magukat.

#### <a name="apple-menu"></a>Apple menü

Miután a felhasználók bejelentkeznek az eszközökre, a következő beállítások befolyásolhatják, hogy milyen műveleteket végezhetnek el.

- **Leállítás letiltása**: A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a **Leállítás** lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak az eszköz **Leállítás** menüpontjának kiválasztását.
- **Újraindítás letiltása**: A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek az **Újraindítási** lehetőség választásával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az **Újraindítási** menüelem kiválasztását az eszközön.
- Kikapcsolás **letiltása**: A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók **bejelentkeznek** a kikapcsolás lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé **teszi a felhasználók** számára, hogy kiválassza a kikapcsolt menüelemet az eszközön.
- Kijelentkezés **letiltása** (macOS 10,13 és újabb verziók): A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók **bejelentkeznek a kijelentkezés** lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a **kijelentkezés** menüpont kiválasztását az eszközön.
- **Zárolási képernyő letiltása** (macOS 10,13 és újabb verziók): A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a **zárolási képernyő** lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy kiválassza a **zárolási képernyő** menüelemét az eszközön.

## <a name="single-sign-on-app-extension"></a>Egyszeri bejelentkezési alkalmazás bővítménye

Ez a funkció az alábbiakra vonatkozik:

- macOS 10,15 és újabb verziók

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus 

- **Egyszeri bejelentkezéses alkalmazás bővítményének típusa**: Válassza ki a hitelesítő adatok SSO-alkalmazásának típusát. A választható lehetőségek:

  - **Nincs konfigurálva**: Nem használják az alkalmazás-bővítményeket. Az egyszeri bejelentkezéses alkalmazások kiterjesztésének letiltásához állítsa át az egyszeri bejelentkezéses alkalmazás kiterjesztésének típusát a **Kerberos** vagy a **hitelesítő adatok** közül a **nincs konfigurálva**értékre
  - **Hitelesítő adat**: Használjon egy általános, testreszabható hitelesítőadat-alkalmazás-bővítményt az egyszeri bejelentkezés használatához. Győződjön meg róla, hogy ismeri a szervezete SSO-alkalmazásának bővítmény-AZONOSÍTÓját és a csoport AZONOSÍTÓját.  
  - **Kerberos**: Használja az Apple beépített Kerberos-bővítményét, amely a macOS Catalina 10,15-es és újabb verzióiban található. Ez a beállítás a **hitelesítőadat** -alkalmazás kiterjesztésének Kerberos-specifikus verziója.

  > [!TIP]
  > A **hitelesítő adatok** típusával adja hozzá a saját konfigurációs értékeit, hogy áthaladjon a bővítményen. Ehelyett érdemes lehet az Apple által biztosított beépített konfigurációs beállításokat használni a **Kerberos** -típusban.

- **BŐVÍTMÉNY azonosítója** (Csak hitelesítő adatok): Adja meg az SSO-alkalmazás kiterjesztését azonosító köteg-azonosítót, `com.apple.ssoexample`például:.
- **Csoport azonosítója** (Csak hitelesítő adatok): Adja meg az egyszeri bejelentkezéses alkalmazás bővítményének csapat-azonosítóját. A csapat azonosítója az Apple által generált, 10 karakterből álló alfanumerikus (számok és betűk) karakterlánc, például `ABCDE12345`:. 

  [A csoport azonosítójának megkeresése](https://help.apple.com/developer-account/#/dev55c3c710c) (az Apple webhelyének megnyitása) további információkat tartalmaz.

- **Tartomány**: Adja meg a Kerberos-tartomány nevét. A tartománynevet tőkésíteni kell, például `CONTOSO.COM`:. A tartománynév általában megegyezik a DNS-tartománynévvel, de minden nagybetűvel.
- **Tartományok**: Adja meg az egyszeri bejelentkezéssel hitelesíthető helyek tartomány-vagy állomásnevek nevét. Ha például a webhelye `mysite.contoso.com`, akkor `mysite` az az állomásnév, `contoso.com` a pedig a tartománynév. Ha a felhasználók bármelyik webhelyhez csatlakoznak, az alkalmazás-bővítmény kezeli a hitelesítési kihívást. Ez a hitelesítés lehetővé teszi a felhasználók számára a bejelentkezéshez a Face ID, a Touch ID vagy az Apple pincode/PIN-kód használatát.

  - Az egyszeri bejelentkezési alkalmazás bővítményének Intune-profiljainak minden tartományának egyedinek kell lennie. A tartományokat nem lehet megismételni a Bejelentkezési alkalmazás bővítményeinek egyik profiljában sem, még akkor is, ha különböző típusú egyszeri bejelentkezéses alkalmazás-bővítményeket használ.
  - Ezek a tartományok nem megkülönböztetik a kis-és nagybetűket

- **További konfiguráció** (Csak hitelesítő adatok): Adja meg az egyszeri bejelentkezéses alkalmazás kiterjesztésére vonatkozó további, bővítményekre vonatkozó adatbevitelt:
  - **Konfigurációs kulcs**: Adja meg a hozzáadni kívánt elem nevét, például `user name`:.
  - **Érték típusa**: Adja meg az adattípust. A választható lehetőségek:

    - Sztring
    - Logikai A **konfigurációs érték**mezőben adja `True` meg `False`a vagy a értéket.
    - Egész A **konfigurációs érték**mezőbe írjon be egy számot.
    
  - **Konfigurációs érték**: Adja meg az adatbevitelt.
  
  - **Hozzáadás**: A konfigurációs kulcsok hozzáadásához válassza a lehetőséget.

- **Kulcstartó használata** (Csak Kerberos esetén): A **blokkolás** gombra kattintva megakadályozhatja a jelszavak mentését és tárolását a kulcstartóban. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszavak mentését és tárolását a kulcstartóban.  
- **Face ID, Touch ID vagy PIN kód** (Csak Kerberos esetén): **Megkövetelheti** a felhasználóktól, hogy a hozzáadott tartományba való bejelentkezéshez megadják a Face ID, a Touch ID vagy az Apple PIN-kódot. **Nincs konfigurálva** (alapértelmezés) nem igényli, hogy a felhasználók a bejelentkezéshez biometria vagy PIN-kódot használjanak.
- **Alapértelmezett tartomány** (Csak Kerberos esetén): Válassza az **Engedélyezés** lehetőséget az alapértelmezett tartományként megadott **tartomány** értékének beállításához. **Nincs konfigurálva** (alapértelmezés) nem állítja be az alapértelmezett tartományt.

  > [!TIP]
  > - Akkor **engedélyezze** ezt a beállítást, ha több Kerberos SSO-alkalmazás-bővítményt konfigurál a szervezetében.
  > - Ha több birodalmat használ, **engedélyezze** ezt a beállítást. Az alapértelmezett tartományként megadott **tartományi** értéket állítja be.
  > - Ha csak egy tartománya van, hagyja meg, hogy **nincs konfigurálva** (alapértelmezett).

- **Automatikus észlelés** (Csak Kerberos esetén): Ha a **blokkolás**értékre van állítva, a Kerberos-bővítmény nem használja automatikusan az LDAP és a DNS szolgáltatást a Active Directory hely nevének meghatározásához. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a bővítmény automatikusan megkeresse a Active Directory hely nevét.
- **Jelszó módosítása** (Csak Kerberos esetén): A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók megváltoztassák a beírt tartományba való bejelentkezéshez használt jelszavakat. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a jelszó módosítását.  
- **Jelszó-szinkronizálás** (Csak Kerberos esetén): Az **Engedélyezés** gombra kattintva szinkronizálhatja a felhasználók helyi jelszavait az Azure ad-vel. **Nincs konfigurálva** (alapértelmezés) letiltja a jelszó-szinkronizálást az Azure AD-be. Ezt a beállítást Alternatív megoldásként vagy az SSO-ként történő biztonsági mentésként használhatja. Ez a beállítás nem működik, ha a felhasználók Apple Mobile-fiókkal jelentkeznek be.
- **Windows Server Active Directory jelszó bonyolultsága** (Csak Kerberos esetén): A **kötelező** beállítás megadásával kényszerítheti a felhasználói jelszavakat, hogy megfeleljenek Active Directory jelszavának összetettségi követelményeinek. További információkért lásd: a [jelszónak meg kell felelnie a bonyolultsági feltételeknek](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **Nincs konfigurálva** (alapértelmezés) nem igényli, hogy a felhasználók megfeleljenek Active Directory jelszavára vonatkozó követelménynek.
- **Jelszó minimális hossza** (Csak Kerberos esetén): Adja meg a felhasználó jelszavának kihasználható karakterek minimális számát. **Nincs konfigurálva** (alapértelmezés) nem kényszeríti ki a jelszó minimális hosszát a felhasználóknál.
- **Jelszó újrafelhasználásának korlátja** (Csak Kerberos esetén): Adja meg a 1-24-ból származó új jelszavak számát, amelyeket addig kell használni, amíg egy korábbi jelszót újra fel nem használ a tartományon. **Nincs konfigurálva** (alapértelmezés) nem érvényesíti a jelszó-újrahasznosítási korlátot.
- **Jelszó minimális kora** (Csak Kerberos esetén): Adja meg, hogy hány nap elteltével kell használni a jelszót a tartományon, mielőtt a felhasználó módosíthatja azt. **Nincs konfigurálva** (az alapértelmezett érték) nem kényszeríti ki a minimális korhatárt a jelszó megváltozása előtt.
- **Jelszó lejáratáról szóló értesítés** (Csak Kerberos esetén): Adja meg, hogy hány nap elteltével járjon le a jelszó, ha a felhasználók értesítést kapnak arról, hogy a jelszavuk lejár. **Nincs konfigurálva** (alapértelmezés) napokat használ `15` .
- **Jelszó lejárata** (Csak Kerberos esetén): Adja meg, hogy hány nap elteltével kell megváltoztatni az eszköz jelszavát. **Nincs konfigurálva** (alapértelmezett): a felhasználói jelszavak soha nem járnak le.
- **Egyszerű név** (Csak Kerberos esetén): Adja meg a Kerberos-tag felhasználónevét. Nem kell belefoglalni a tartománynevet. Például a-ben `user@contoso.com` `user` a az egyszerű név, a pedigatartományneve.`contoso.com`
- **Active Directory Helykód** (Csak Kerberos esetén): Adja meg annak a Active Directory helynek a nevét, amelyet a Kerberos-bővítménynek használnia kell. Előfordulhat, hogy nem kell módosítania ezt az értéket, mivel a Kerberos-bővítmény automatikusan megkeresi a Active Directory hely kódját.
- **Gyorsítótár neve** (Csak Kerberos esetén): Adja meg a Kerberos-gyorsítótár általános biztonsági szolgáltatásainak (GSS) nevét. Valószínűleg nem kell beállítania ezt az értéket.  
- A **jelszóra vonatkozó követelmények üzenete** (Csak Kerberos esetén): Adja meg a szervezete jelszavának a felhasználók számára megjelenített szöveges verzióját. Az üzenet akkor jelenik meg, ha nincs szükség Active Directory jelszavával kapcsolatos bonyolultsági követelményekre, vagy ne adja meg a jelszó minimális hosszát.  
- Alkalmazáscsomag- **azonosítók** (Csak Kerberos esetén): **Adja hozzá** azokat az alkalmazáscsomag-azonosítókat, amelyeken egyszeri bejelentkezést kell használnia az eszközökön. Ezek az alkalmazások hozzáférést kapnak a Kerberos-jegy biztosításához, a hitelesítési jegyet, és hitelesítik a felhasználókat a hozzáférésre jogosult szolgáltatásokhoz.
- **Tartományi tartomány leképezése** (Csak Kerberos esetén): **Adja hozzá** a tartományhoz hozzárendelni kívánt tartományi DNS-utótagokat. Akkor használja ezt a beállítást, ha a gazdagépek DNS-nevei nem egyeznek a tartománynév nevével. Valószínűleg nem kell létrehoznia ezt az egyéni tartomány – tartomány társítást.

## <a name="associated-domains"></a>Társított tartományok

Az Intune-ban a következőket teheti:

- Számos alkalmazás-tartomány társítást vehet fel.
- Számos tartományt társíthat ugyanahhoz az alkalmazáshoz.

Ez a funkció az alábbiakra vonatkozik:

- macOS 10,15 és újabb verziók

### <a name="settings-apply-to-all-enrollment-types"></a>A beállítások a következőkre vonatkoznak: Minden regisztrációs típus

- **Alkalmazás azonosítója**: Adja meg annak az alkalmazásnak az azonosítóját, amelyet a webhelyhez szeretne rendelni. Az alkalmazás azonosítója tartalmazza a csoport AZONOSÍTÓját és a köteg AZONOSÍTÓját: `TeamID.BundleID`.

  A csoport azonosítója az Apple által az alkalmazások fejlesztői számára generált, 10 karakterből álló alfanumerikus (betűk és számok) karakterlánc, például `ABCDE12345`:. [Keresse meg a csoport azonosítóját](https://help.apple.com/developer-account/#/dev55c3c710c) (az Apple webhelyének megnyitása) további információkat.

  A Bundle-azonosító egyedileg azonosítja az alkalmazást, és általában fordított tartománynév-jelöléssel van formázva. A Finder `com.apple.finder`csomag azonosítója például a következő:. A csomag AZONOSÍTÓjának megkereséséhez használja az AppleScript-t a terminálban:

  `osascript -e 'id of app "ExampleApp"'`

- **Tartomány**: Adja meg az alkalmazáshoz társítandó webhely-tartományt. A tartomány tartalmaz egy szolgáltatástípus és egy teljes tartománynevet, például `webcredentials:www.contoso.com`a következőt:.

  A szolgáltatás típusa a következő lehet:

  - **authsrv**: Egyszeri bejelentkezési alkalmazás bővítménye
  - **applink**: Univerzális hivatkozás
  - **webhitelesítő adatok**: Jelszó automatikus kitöltése

- **Hozzáadás**: Az alkalmazások és a társított tartományok hozzáadásához válassza a lehetőséget.

> [!TIP]
> A hibakereséshez a MacOS-eszközön nyissa meg a **Rendszerbeállítások** > **profiljait**. Erősítse meg, hogy a létrehozott profil az eszköz profiljai listán található. Ha szerepel a felsorolásban, győződjön meg arról, hogy a **társított tartományok konfigurációja** szerepel a profilban, és tartalmazza a megfelelő alkalmazás-azonosítót és-tartományokat.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az eszközök funkcióit az [iOS](ios-device-features-settings.md)rendszeren is megadhatja.
