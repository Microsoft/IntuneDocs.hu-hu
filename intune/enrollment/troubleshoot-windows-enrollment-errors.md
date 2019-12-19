---
title: A Windows-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune
titleSuffix: Microsoft Intune
description: Javaslatok a Windows-eszközök Intune-beli regisztrálásával kapcsolatos leggyakoribb problémák elhárításához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 46012b11cdb458243658e858b53c2dfb1a69dc88
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991804"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>A Windows-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune

Ez a cikk az Intune-rendszergazdáknak segít megérteni és elhárítani a Windows-eszközök Intune-beli regisztrálásakor felmerülő problémákat.

## <a name="prerequisites"></a>Előfeltételek
Mielőtt elkezdené a hibaelhárítást, fontos, hogy gyűjtsön néhány alapvető információt. Ezek az információk segítenek jobban megérteni a problémát, és csökkenthetik a megoldási időt.

Gyűjtse össze a következő információkat a problémával kapcsolatban:
- Érvényes Intune-licenc van hozzárendelve a felhasználóhoz? Ahhoz, hogy a felhasználók regisztrálni tudják eszközeiket, hozzá kell rendelni a szükséges licencet.
- A legújabb frissítés telepítve van a Windows-eszközön? Az Intune egyes funkciói csak a Windows legújabb verziójával működnek. A Windows Updateon keresztül elérhető ismert problémák számos javítást biztosítanak. A legújabb frissítések alkalmazása gyakran javít egy Windows-eszköz regisztrálásával kapcsolatos problémát. 
- Mi a pontos hibaüzenet?
- Hol látja a hibaüzenetet?
- Mikor jelentkezett először a probléma? Valaha is működött a regisztráció? 
- Milyen platformon (Android, iOS, Windows) van probléma?
- Hány felhasználót érint a rendszer? Az összes érintett felhasználó vagy csak néhány?
- Hány eszközt érint a rendszer? Minden eszköz érintett vagy csak néhány?
- Mi a MDM-szolgáltató? Ha System Center Configuration Manager, a Configuration Manager milyen verzióját használja?
- Hogyan történik a beléptetés? A "saját eszközök használata" (BYOD) vagy Apple Készülékregisztrációs program (DEP) beléptetési profilokkal?

## <a name="error-messages"></a>Hibaüzenetek

### <a name="this-user-is-not-authorized-to-enroll"></a>Ez a felhasználó nem rendelkezik jogosultsággal a regisztráláshoz.

Hiba 0x801c003: "Ez a felhasználó nem rendelkezik jogosultsággal a regisztráláshoz. Próbálkozzon újra, vagy forduljon a rendszergazdához a hibakód (0x801c0003) használatával. "
80180003-es hiba: "valami hiba történt. Ez a felhasználó nem rendelkezik jogosultsággal a regisztráláshoz. Próbálkozzon újra, vagy forduljon a rendszergazdához a 80180003-as hibakódgal. "

**OK:** Az alábbi feltételek bármelyike: 

- A felhasználó már regisztrálta az Intune-ban engedélyezett eszközök maximális számát.    
- Az eszköz típusa korlátozásai le vannak tiltva.    
- A számítógép Windows 10 Home rendszert futtat. Azonban az Intune-ban való regisztrálás vagy az Azure AD-hez való csatlakozás csak a Windows 10 Pro és újabb kiadásokban támogatott.

#### <a name="resolution"></a>Megoldás
A probléma több lehetséges megoldást is kínál:

##### <a name="remove-devices-that-were-enrolled"></a>A regisztrált eszközök eltávolítása
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).    
2. Lépjen a **felhasználók** > **az összes felhasználóra**.    
3. Válassza ki az érintett felhasználói fiókot, majd kattintson az **eszközök**elemre.    
4. Válassza ki a fel nem használt vagy nemkívánatos eszközöket, majd kattintson a **Törlés**gombra. 

##### <a name="increase-the-device-enrollment-limit"></a>Az eszközök regisztrálási korlátjának emelése

> [!NOTE]
> Ez a módszer növeli az eszközök regisztrálási korlátját az összes felhasználó számára, nem csak az érintett felhasználót.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **a regisztrációs korlátozások** > az **alapértelmezett** (az eszközök **korlátja**alatt) > **tulajdonságok** > **Szerkesztés** (az **eszköz korlátja**) > növelje az **eszköz korlátját** (legfeljebb 15) > **felülvizsgálat + mentés**lehetőséget.    
 

##### <a name="check-device-type-restrictions"></a>Az eszközök típusára vonatkozó korlátozások keresése
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431) globális rendszergazdai fiókkal.
2. Lépjen az **eszközök** > a **regisztrációs korlátozások**elemre, majd válassza ki az **alapértelmezett** korlátozást az **eszközök típusának korlátozása**területen.    
3. Válassza a **platformok**lehetőséget, majd válassza a **Windows engedélyezése (Mdm)** lehetőséget.

    > [!IMPORTANT]
    > Ha az aktuális beállítás már **engedélyezve**van, módosítsa a **blokkolás**értékre, mentse a beállítást, majd állítsa vissza, hogy **engedélyezze** , majd mentse újra a beállítást. Ezzel alaphelyzetbe állítja a beléptetési beállítást.

4. Várjon körülbelül 15 percet, majd regisztrálja újra az érintett eszközt.    

##### <a name="upgrade-windows-10-home"></a>A Windows 10 Home frissítése
[Frissítse a Windows 10 Home rendszert a Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) vagy újabb verzióra. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Ez a felhasználó regisztrációja nem engedélyezett.

Hiba 0x801c0003: "Ez a felhasználó nem regisztrálható. Próbálkozzon újra, vagy forduljon a rendszergazdához a hibakód 801c0003. "

**OK:** Előfordulhat, hogy a **felhasználók az Azure ad-be való csatlakozáshoz** a **none**értékre vannak beállítva. Ez megakadályozza, hogy az új felhasználók az eszközeiket az Azure AD-be csatlakozzanak. Ezért az Intune-regisztráció meghiúsul.

#### <a name="resolution"></a>Megoldás
1. Jelentkezzen be rendszergazdaként a [Azure Portalba](https://portal.azure.com/) .    
2. Lépjen **Azure Active Directory** > **eszközök** > **eszközbeállítások menüpontra**.    
3. A felhasználók beállíthatja, **hogy az**eszközök az **Azure ad** -hez csatlakozzanak.    
4. Regisztrálja újra az eszközt.   

### <a name="the-device-is-already-enrolled"></a>Az eszköz már regisztrálva van.

Hiba 8018000a: "hiba történt. Az eszköz már regisztrálva van.  Forduljon a rendszergazdához a hibakód 8018000a. "

**OK:** A következő feltételek egyike igaz:
- Egy másik felhasználó már regisztrálta az eszközt az Intune-ban, vagy csatlakoztatta az eszközt az Azure AD-hez. Annak megállapításához, hogy ez a helyzet-e, lépjen a **beállítások** > **fiókok** > **munkahelyi hozzáférés elemre**. Keresse meg az alábbihoz hasonló üzenetet: "egy másik felhasználó már csatlakoztatva van egy munkahelyi vagy iskolai hálózathoz. Távolítsa el a munkahelyi vagy iskolai kapcsolatokat, és próbálkozzon újra. "    
- A Configuration Manager ügyfél ügynöke telepítve van a számítógépen.    

#### <a name="resolution"></a>Megoldás

A probléma megoldásához használja az alábbi módszerek egyikét:

##### <a name="remove-the-other-work-or-school-account"></a>A másik munkahelyi vagy iskolai fiók eltávolítása
1. Jelentkezzen ki a Windowsból, majd jelentkezzen be a másik fiókkal, amely regisztrált vagy csatlakozott az eszközhöz.    
2. Lépjen a **beállítások** > **fiókok** > **munkahelyi hozzáférés**elemre, majd távolítsa el a munkahelyi vagy iskolai fiókot.
3. Jelentkezzen ki a Windowsból, majd jelentkezzen be a fiókjával.    
4. Regisztrálja az eszközt az Intune-ban, vagy csatlakoztassa az eszközt az Azure AD-hez. 

##### <a name="remove-the-configuration-manager-client"></a>Az Configuration Manager-ügyfél eltávolítása
Távolítsa el a Configuration Manager ügyfelet, majd regisztrálja újra az eszközt.



### <a name="this-account-is-not-allowed-on-this-phone"></a>Ez a fiók nem engedélyezett ezen a telefonon.

Hiba: "Ez a fiók nem engedélyezett ezen a telefonon. Győződjön meg arról, hogy a megadott adatok helyesek, majd próbálkozzon újra, vagy kérjen támogatást a vállalattól. "

**OK:** Az eszközt regisztrálni próbáló felhasználónak nincs érvényes Intune-licence.

#### <a name="resolution"></a>Megoldás
Rendeljen érvényes Intune-licencet a felhasználóhoz, majd regisztrálja az eszközt.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Úgy tűnik, hogy a MDM használati feltételeinek végpontja helytelenül van konfigurálva.

**OK:** A következő feltételek egyike igaz: 
 - Az Office 365-hez és az Intune-hoz készült mobileszköz-kezelést (MDM) is használhatja a bérlőn, és az eszköz regisztrálását végző felhasználó nem rendelkezik érvényes Intune-licenccel vagy Office 365-licenccel.     
- Az Azure AD MDM használati feltételei üresek, vagy nem tartalmazzák a megfelelő URL-címet.    

#### <a name="resolution"></a>Megoldás

A probléma megoldásához használja az alábbi módszerek egyikét: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Érvényes licencet rendeljen a felhasználóhoz
Lépjen a [Microsoft 365 felügyeleti központba](https://portal.office.com/adminportal/home), majd rendeljen hozzá egy Intune-t vagy egy Office 365-licencet a felhasználóhoz.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Javítsa ki a MDM használati feltételeinek URL-címét
  1. Jelentkezzen be a [Azure Portalba](https://portal.azure.com/), majd válassza a **Azure Active Directory**lehetőséget.    
  2. Válassza a **mobilitás (Mdm és MAM)** lehetőséget, majd kattintson a **Microsoft Intune**elemre.    
  3. Válassza az **alapértelmezett Mdm-URL-címek visszaállítása**lehetőséget, és győződjön meg arról, hogy a **Mdm URL-címének** beállítása **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Válassza a **Mentés** elemet.    


### <a name="something-went-wrong"></a>Hiba történt.

80180026-es hiba: "valami hiba történt. Ellenőrizze, hogy a megfelelő bejelentkezési adatokat használja-e, és hogy a szervezet használja-e ezt a funkciót. Próbálkozzon újra, vagy forduljon a rendszergazdához a 80180026-es hibakód használatával. "

**OK:** Ez a hiba akkor fordulhat elő, ha Windows 10 rendszerű számítógépet próbál csatlakoztatni az Azure AD-hez, és az alábbi feltételek mindegyike teljesül: 
- A MDM automatikus regisztrációja engedélyezve van az Azure-ban.    
- Az Intune PC-ügyfél (Intune PC Agent) vagy a Configuration Manager ügyfél ügynöke telepítve van a Windows 10 rendszerű számítógépre.

#### <a name="resolution"></a>Megoldás
A probléma megoldásához használja az alábbi módszerek egyikét:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Tiltsa le a MDM automatikus regisztrációját az Azure-ban.
1. Jelentkezzen be az [Azure portálra](https://portal.azure.com/).    
2. Nyissa meg a **Azure Active Directory** > **Mobility (Mdm és MAM)**  > **Microsoft Intune**.    
3. Állítsa a **Mdm felhasználói hatókörét** **none**értékre, majd kattintson a **Mentés**gombra.    
     
##### <a name="uninstall"></a>Eltávolítás
Távolítsa el az Intune PC-ügyfelet vagy Configuration Manager-ügynököt a számítógépről.    

### <a name="the-software-cannot-be-installed"></a>A szoftver nem telepíthető.

Hiba: "a szoftver nem telepíthető, 0x80cf4017."

**OK:** Az ügyfélszoftver elavult.

#### <a name="resolution"></a>Megoldás
1. Jelentkezzen be itt: [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Nyissa meg a **felügyeleti** > **ügyfélszoftver letöltése**lehetőséget, majd kattintson az **ügyfélszoftver letöltése**elemre.    
3. Mentse a telepítőcsomagot, majd telepítse az ügyfélszoftvert. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>A fiók tanúsítványa nem érvényes, és lehet, hogy lejárt.

Hiba: "a fiók tanúsítványa nem érvényes, és lehet, hogy lejárt, 0x80cf4017."

**OK:** Az ügyfélszoftver elavult.

#### <a name="resolution"></a>Megoldás
1. Jelentkezzen be itt: [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Nyissa meg a **felügyeleti** > **ügyfélszoftver letöltése**lehetőséget, majd kattintson az **ügyfélszoftver letöltése**elemre.    
3. Mentse a telepítőcsomagot, majd telepítse az ügyfélszoftvert.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>A szervezet nem támogatja a Windows ezen verzióját. 

Hiba: "probléma történt. A szervezet nem támogatja a Windows ezen verzióját.  (0x80180014) "

**OK:** A Windows MDM regisztrációja le van tiltva az Intune-bérlőben.

#### <a name="resolution"></a>Megoldás
A probléma önálló Intune-környezetben való kijavításához kövesse az alábbi lépéseket: 
 
1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > a **regisztrációs korlátozásokat** > válasszon egy eszköz típusú korlátozást.    
2. Válassza a **tulajdonságok** > **Szerkesztés** (a **platform beállításai**mellett) > a **Windows (Mdm)** **engedélyezése lehetőséget** .    
3. Kattintson a **felülvizsgálat + mentés**gombra.    
 
A probléma megoldásához az Intune-nal és a Configuration Managertel rendelkező hibrid MDM hajtsa végre az alábbi lépéseket: 
1. Nyissa meg a Configuration Manager-konzolt.    
2. Válassza az **Adminisztráció**, majd a **Cloud Services**lehetőséget.    
3. Kattintson a jobb gombbal **Microsoft Intune előfizetésre**, majd válassza a **platformok konfigurálása > Windows**lehetőséget.    
4. Jelölje be a **Windows-regisztráció engedélyezése** > **ok** > **gombra**.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Telepítési hiba történt a csoportos regisztráció során.

**OK:** A megfelelő kiépítési csomaghoz tartozó fiók csomagjában (Package_GUID) lévő Azure AD felhasználói fiókjai nem jogosultak eszközök csatlakoztatására az Azure AD-hez. Ezek az Azure AD-fiókok automatikusan létrejönnek a Windows Configuration Designerrel (WCD) rendelkező kiépítési csomag vagy az iskolai PC-alkalmazás beállítása során, és ezeket a fiókokat az eszközök Azure AD-hez való csatlakoztatására használják.

#### <a name="resolution"></a>Megoldás
1. Jelentkezzen be rendszergazdaként a [Azure Portalba](https://portal.azure.com/) .    
2. Lépjen **Azure Active Directory > eszközök > eszközbeállítások menüpontra**.    
3. Beállíthatja, hogy a felhasználók az Azure AD-be vagy az **összes** **kiválasztott** **eszközhöz csatlakozzanak** .

   Ha a **kijelölt**lehetőséget választja, kattintson a **kijelölt**elemre, majd kattintson a **Tagok hozzáadása** lehetőségre az összes olyan felhasználó hozzáadásához, akik csatlakozhatnak az eszközéhez az Azure ad-ben. Győződjön meg arról, hogy a kiépítési csomaghoz tartozó összes Azure AD-fiók hozzá van adva.
 
További információ a kiépítési csomag létrehozásáról a Windows Configuration Designerben: létesítési [csomag létrehozása a Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)rendszerhez.

További információ az iskolai számítógépek alkalmazásának beállításáról: [az iskolai számítógépek alkalmazásának beállítása](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Automatikus MDM-regisztráció: sikertelen 

Ha Csoportházirend használatával próbál automatikusan regisztrálni egy Windows 10-es eszközt, a következő problémákat tapasztalhatja: 
- A Feladatütemezőben, a **Microsoft** > **Windows** > **EnterpriseMgmt**alatt a **beléptetési ügyfél által a HRE feladatba való automatikus regisztráláshoz létrehozott ütemezés** utolsó futtatásának eredménye a következő: **Event 76 Auto Mdm regisztrációja: failed (ismeretlen Win32 hibakód: 0x8018002b)**       
- Eseménynapló a következő eseményt naplózza az **Applications and Services logs/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/admin**területen:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**OK:** A következő feltételek egyike igaz: 
- Az UPN nem ellenőrzött vagy nem irányítható tartományt tartalmaz, például:. local (például joe@contoso.local).    
- A **Mdm felhasználói hatóköre** **none**értékre van állítva. 

#### <a name="resolution"></a>Megoldás
Ha az UPN nem ellenőrzött vagy nem irányítható tartományt tartalmaz, kövesse az alábbi lépéseket: 

1. Azon a kiszolgálón, amelyen a Active Directory tartományi szolgáltatások (AD DS) fut, nyissa meg **Active Directory felhasználókat és számítógépeket** . Ehhez írja be a **DSA. msc** parancsot a **Futtatás** párbeszédpanelen, majd kattintson **az OK**gombra.    
2. Kattintson a tartomány alatt lévő **felhasználók** elemre, majd tegye a következőket:  
    - Ha csak egy érintett felhasználó van, kattintson a jobb gombbal a felhasználóra, majd kattintson a **Tulajdonságok**elemre. A **fiók** lap UPN-utótag legördülő listájában a **felhasználói bejelentkezési név**területen válasszon egy érvényes UPN-utótagot, például contoso.com, majd kattintson **az OK**gombra.    
    - Ha több érintett felhasználó van, válassza ki a felhasználókat, a **művelet** menüben kattintson a **Tulajdonságok**elemre. A **fiók** lapon jelölje be az **UPN-utótag** jelölőnégyzetet, válasszon ki egy érvényes UPN-utótagot, például contoso.com a legördülő listából, majd kattintson **az OK**gombra.
3. Várjon a következő szinkronizálásra, vagy kényszerítse a különbözeti szinkronizálást a szinkronizációs kiszolgálóról a következő parancsok futtatásával egy rendszergazda jogú PowerShell-parancssorban:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Ha a **Mdm felhasználói hatóköre** **none**értékre van állítva, kövesse az alábbi lépéseket: 
 
1. Jelentkezzen be a [Azure Portalba](https://portal.azure.com/), majd válassza a **Azure Active Directory**lehetőséget.
2. Válassza a **mobilitás (Mdm és MAM)** lehetőséget, majd válassza a **Microsoft Intune**lehetőséget.    
3. A **Mdm felhasználói hatókörének** beállítása az **összes**értékre. Vagy állítsa be a **Mdm felhasználói hatókörét** **néhány**értékre, és válassza ki azokat a csoportokat, amelyek automatikusan regisztrálhatják Windows 10-es eszközeiket.    
4. A **MAM felhasználói hatókör** beállítása **none**értékre.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Hiba történt az Autopilot-profil létrehozásakor.

**OK:** Az eszköznév sablonjának megadott elnevezési formátuma nem felel meg a követelményeknek. Használhat például kisbetűs értéket a soros makróhoz, például% Serial%-ot a (z)% SERIAL% helyett.

#### <a name="resolution"></a>Megoldás

Győződjön meg arról, hogy az elnevezési formátum megfelel a következő követelményeknek:

- Hozzon létre egy egyedi nevet az eszközök számára. A névnek legalább 15 karakterből kell állnia, és tartalmazhat betűket (a-z, A-Z), számokat (0-9) és kötőjeleket ().
- A nevek nem állhatnak csak számokból.
- A nevek nem tartalmazhatnak üres helyet.
- A (z)% SERIAL% Macro használatával adjon hozzá egy hardver-specifikus sorozatszámot. Vagy használja a (z)% RAND: < # számjegyeket >% Macro használatával véletlenszerű karakterláncok hozzáadásához, a karakterlánc a számjegyek számának > <ét tartalmazza. Például a MYPC-% RAND: 6% olyan nevet hoz létre, mint például a MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Hiba történt. OOBEIDPS.

**OK:** Ez a probléma akkor fordul elő, ha van proxy, tűzfal vagy más olyan hálózati eszköz, amely blokkolja az identitás-szolgáltató (identitásszolgáltató) elérését.

#### <a name="resolution"></a>Megoldás
Győződjön meg arról, hogy az Autopilot Internet alapú szolgáltatásaihoz szükséges hozzáférés nincs letiltva. További információ: a [Windows Autopilot hálózati követelményei](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Az eszköz regisztrálása a Mobile Management szolgáltatásban (sikertelen: 3, 0x801C03EA).

**OK:** Az eszközön van olyan TPM-lapka, amely támogatja az 2,0-es verziót, de még nem frissítették a 2,0-es verzióra.

#### <a name="resolution"></a>Megoldás
Frissítse a TPM-lapka-t a 2,0-es verzióra.

Ha a probléma továbbra is fennáll, ellenőrizze, hogy ugyanaz az eszköz két hozzárendelt csoportban van-e, és hogy az egyes csoportok egy másik Autopilot-profilt rendelnek hozzá. Ha két csoportban van, állapítsa meg, hogy melyik Autopilot-profilt kell alkalmazni az eszközön, majd távolítsa el a másik profil hozzárendelését.

További információ arról, hogyan telepíthet egy Windows-eszközt kioszk módban az Autopilot [használatával: kioszk üzembe helyezése a Windows Autopilot használatával](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>A hardver biztonságossá tétele (sikertelen: 0x800705b4).

800705B4 hiba: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**OK:** A célként megadott Windows-eszköz nem felel meg az alábbi követelmények egyikének:

- Az eszköznek rendelkeznie kell fizikai TPM 2,0-csiptel. A virtuális TPM (például Hyper-V virtuális gépek) vagy a TPM 1,2-es chipek nem működnek öntelepítési módban.
- Az eszköznek a Windows következő verziói egyikét kell futtatnia:
    - Windows 10 Build 1703 vagy újabb verzió.
    - Ha hibrid Azure AD-csatlakozást használ, a Windows 10 1809-es vagy újabb verzióját használja.


#### <a name="resolution"></a>Megoldás
Győződjön meg arról, hogy a célként megadott eszköz megfelel az **OK** szakaszban ismertetett követelményeknek.

További információ arról, hogyan telepíthet egy Windows-eszközt kioszk módban az Autopilot [használatával: kioszk üzembe helyezése a Windows Autopilot használatával](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Hiba történt. Hibakód: 80070774.

Hiba 0x80070774: hiba történt. Ellenőrizze, hogy a megfelelő bejelentkezési adatokat használja-e, és hogy a szervezet használja-e ezt a funkciót. Próbálkozzon újra, vagy forduljon a rendszergazdához a 80070774 hibakódgal.

Ez a probléma általában akkor fordul elő, ha az eszköz újraindul egy hibrid Azure AD Autopilot-forgatókönyvben, amikor az eszköz időtúllépést okoz a kezdeti bejelentkezési képernyőn. Ez azt jelenti, hogy a tartományvezérlő nem található vagy nem érhető el sikeresen a kapcsolódási problémák miatt. Vagy azt, hogy az eszköz olyan állapotba lépett, amely nem tud csatlakozni a tartományhoz.

**OK:** A leggyakoribb ok az, hogy a hibrid Azure AD-csatlakozás használatban van, és a felhasználó kiosztása funkció az Autopilot-profilban van konfigurálva. A felhasználó kiosztása funkcióval Azure AD-csatlakozást hajt végre az eszközön a kezdeti bejelentkezési képernyőn, amely olyan állapotba helyezi az eszközt, amelyben nem tud csatlakozni a helyszíni tartományhoz. Ezért a felhasználó kiosztása funkció csak a standard Azure AD JOIN Autopilot-forgatókönyvekben használható.  A szolgáltatás nem használható hibrid Azure AD JOIN-forgatókönyvekben.

#### <a name="resolution"></a>Megoldás

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza > **eszközök** > **Windows** > Windows- **eszközök**elemet.
2. Válassza ki a problémát észlelő eszközt > kattintson a három pontra (...) a jobb oldali oldalon.
3. Válassza a **felhasználó hozzárendelésének** megszüntetése lehetőséget, és várjon, amíg a folyamat befejeződik.
4. Ellenőrizze, hogy a hibrid Azure AD Autopilot-profil hozzá van-e rendelve az OOBE ismételt megkísérlése előtt.

#### <a name="second-resolution"></a>Második megoldás
Ha a probléma továbbra is fennáll, a kapcsolat nélküli tartományhoz csatlakozás Intune-összekötőt futtató kiszolgálón ellenőrizze, hogy a 30312-es azonosítójú esemény be van-e jelentkezve a ODJ-összekötő szolgáltatási naplójába. Az 30312-as esemény a következőhöz hasonló:

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

Ezt a problémát általában a Windows Autopilot-eszközöket létrehozó szervezeti egység engedélyeinek helytelen delegálása okozza. További információ: [a számítógépfiók korlátjának megemelése a szervezeti egységben](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Nyissa meg **Active Directory felhasználókat és számítógépeket (DSA. msc)** .
2. Kattintson a jobb gombbal arra a szervezeti egységre, amelyet hibrid Azure AD-hez csatlakoztatott számítógépek létrehozásához fog használni, > **delegálja a vezérlést**.
3. A **vezérlés delegálása** varázslóban válassza a **következő** >  > **objektumtípus** **hozzáadása** elemet.
4. Az **Objektumtípusok** ablaktáblán jelölje be a **számítógépek** jelölőnégyzetet, > **az OK gombra**.
5. A **felhasználók**, **számítógépek**vagy **csoportok** kiválasztása panelen az **adja meg a kijelölendő objektumok nevét** mezőbe írja be annak a számítógépnek a nevét, amelyen az összekötő telepítve van.
6. Jelölje be a Névellenőrzés **jelölőnégyzetet** a bejegyzés ellenőrzéséhez > OK > a **tovább** **gombra** .
7. Válassza az **Egyéni feladat létrehozása** lehetőséget > **következő**delegálásához.
8. Jelölje be a **csak a következő objektumokat a mappában** jelölőnégyzetből, majd jelölje ki a **számítógép-objektumokat**, **hozzon létre a kijelölt objektumokat**ebben a mappában, és **törölje a kijelölt objektumokat a mappában** jelölőnégyzetből.
9. Válassza a **Tovább** elemet.
10. Az **engedélyek**területen jelölje be a **teljes hozzáférés** jelölőnégyzetet. Ez a művelet kijelöli az összes többi beállítást.
11. Válassza a **Tovább** > **Befejezés** lehetőséget.

## <a name="next-steps"></a>További lépések

- [Eszközök regisztrálásával kapcsolatos problémák elhárítása az Intune-ban](../troubleshoot-device-enrollment-in-intune.md)
- [Kérdés feltevése az Intune-fórumon](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [A Microsoft Intune támogatási csapatának blogja](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [A Microsoft nagyvállalati mobilitási és biztonsági blogjának beolvasása](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Támogatás kérése Microsoft Intune](../fundamentals/get-support.md)
- [Közös felügyelettel kapcsolatos regisztrálási hibák keresése](https://docs.microsoft.com/sccm/comanage/how-to-monitor#enrollment-errors)
