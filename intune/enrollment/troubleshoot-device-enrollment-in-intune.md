---
title: Eszközök regisztrálásával kapcsolatos problémák elhárítása
titleSuffix: Microsoft Intune
description: Javaslatok az eszközök regisztrálásával kapcsolatos problémák elhárításához Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cb323dc6f8110d77343fb11c9e0a1c40f9e3cd8
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415278"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Az eszközök regisztrálásának hibája Microsoft Intune

Ez a cikk az [eszközök regisztrálásával](device-enrollment.md) kapcsolatos problémák elhárítására vonatkozó javaslatokat tartalmaz. Ha ezekkel az információkkal nem tudja megoldani a problémát, a [Hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md) című témakörben talál további részleteket a segítségkéréshez.


## <a name="initial-troubleshooting-steps"></a>Első hibaelhárítási lépések

A hibaelhárítás megkezdése előtt ellenőrizze, hogy az Intune megfelelően van-e konfigurálva a regisztráláshoz. Ezekről a konfigurációs követelményekről itt olvashat:

- [Felkészülés az eszközök regisztrálására a Microsoft Intune-ban](../fundamentals/setup-steps.md)
- [IOS-/iPadOS-és Mac-eszközök felügyeletének beállítása](../ios-enroll.md)
- [Windowsos eszközök kezelésének beállítása](windows-enroll.md)
- [Android-eszközök kezelésének beállítása](android-enroll.md) – nincs szükség további lépésekre

Azt is biztosíthatja, hogy a felhasználó eszközén megfelelően legyen beállítva a dátum és az idő:

1. Indítsa újra az eszközt.
2. Győződjön meg arról, hogy a dátum és az idő a végfelhasználó időzónájához képest a GMT-szabványokhoz közeli (+ vagy - 12 óra) értékre van beállítva.
3. Távolítsa el, majd telepítse újra az Intune Céges portált (ha ez alkalmazható).

A felügyelt eszközök felhasználói össze tudják gyűjteni a regisztrációs és diagnosztikai naplókat, hogy átnézhesse őket. A naplók felhasználók általi gyűjtésére vonatkozó utasítások itt találhatók:

- [Az Android regisztrálási hibáinak elküldése a rendszergazdának](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [IOS/iPadOS-hibák elküldése a rendszergazdának](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Eszközök regisztrálásával kapcsolatos általános problémák
Ezek a problémák az összes eszközplatformon előfordulhatnak.

### <a name="device-cap-reached"></a>Eszközök maximális száma elérve
**Probléma:** A felhasználó a regisztráció során hibát kap (például **céges portál átmenetileg nem érhető el**).

**Megoldás:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>A regisztrált és engedélyezett eszközök számának ellenőrzése

Ellenőrizze az alábbi lépések követésével, hogy a felhasználóhoz nincs-e hozzárendelve több eszköz a legfeljebb megengedettnél:

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > a **regisztrálási korlátozások** > az eszközök korlátozására **vonatkozó korlátozásokat**. Jegyezze fel az **Eszközszámkorlát** oszlopban látható értéket.

2. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **felhasználók** > **minden felhasználó** lehetőséget, > válassza ki a felhasználói > **eszközöket**. Jegyezze fel a regisztrált eszközök számát.

3. Ha a felhasználó regisztrált eszközeinek száma már megegyezik az eszközszámkorlát értékével, további eszközöket csak akkor regisztrálhat, ha:
    - [eltávolít meglévő eszközöket](../remote-actions/devices-wipe.md), vagy
    - növeli az eszközszámkorlátot az [eszközkorlátozások beállításával](enrollment-restrictions-set.md).

Az eszközszámkorlát elérésének elkerüléséhez mindig távolítsa el a már nem használt eszközök rekordjait.

> [!NOTE]
> 
> Az eszközregisztráció-kezelői fiók használatával elkerülheti a maximális szám elérését az eszközregisztráció során. Lásd: [Vállalati tulajdonban lévő eszközök regisztrálása az Eszközregisztráció-kezelővel a Microsoft Intune-ban](device-enrollment-manager-enroll.md).
> 
> Az eszközregisztráció-kezelői fiókba felvett felhasználói fiók nem tud regisztrálást végrehajtani, ha az adott felhasználói bejelentkezéshez a Feltételes hozzáférés szabályzat van érvényben.

### <a name="company-portal-temporarily-unavailable"></a>A Vállalati portál átmenetileg nem érhető el
**Probléma:** Az eszközön **A Vállalati portál átmenetileg nem érhető el** hibaüzenet jelenik meg.

**Megoldás:**

1. Távolítsa el az eszközről az Intune Vállalati portál alkalmazást.

2. Nyissa meg a böngészőt az eszközön, keresse meg a [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) oldalt, és tegyen kísérletet egy felhasználói bejelentkezésre.

3. Ha a felhasználó nem tud bejelentkezni, egy másik hálózattal kell próbálkoznia.

4. Ha nem sikerül, ellenőrizze, hogy a felhasználói hitelesítő adatokat megfelelően szinkronizálta-e a rendszer az Azure Active Directoryval.

5. Ha a felhasználó sikeresen bejelentkezik, az iOS/iPadOS eszköz kérni fogja, hogy telepítse a Intune Céges portál alkalmazást, és regisztrálja. Az Android-eszközökön manuálisan kell telepítenie az Intune Vállalati portál alkalmazást, amelyet követően újból megpróbálkozhat a regisztrációval.

### <a name="mdm-authority-not-defined"></a>Nincs megadva mobileszköz-kezelési szolgáltató
**Hiba:** Megjelenik egy **Nincs megadva mobileszköz-kezelési szolgáltató** hibaüzenet.

**Megoldás:**

1. Győződjön meg arról, hogy a Mobileszköz-felügyeleti szolgáltató [megfelelően be van állítva](../fundamentals/mdm-authority-set.md).
    
2. Ellenőrizze, hogy a felhasználói hitelesítő adatokat megfelelően szinkronizálta-e a rendszer az Azure Active Directoryval. A Microsoft 365 felügyeleti központban ellenőrizheti, hogy a felhasználó UPN-je megfelel-e a Active Directory információinak.
    Ha a felhasználónév nem egyezik meg az Active Directory adataival:

    1. Kapcsolja ki a DirSync eszközt a helyi kiszolgálón.

    2. Törölje a nem egyező felhasználót az **Intune-fiókportál** felhasználói listáról.

    3. Várjon körülbelül egy óráig, amíg az Azure szolgáltatás eltávolítja a helytelen adatokat.

    4. Kapcsolja be újból a DirSync eszközt, és ellenőrizze, hogy most már megfelelően van-e szinkronizálva a felhasználó.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Nem lehet szabályzatot létrehozni vagy eszközöket regisztrálni, ha a vállalat neve speciális karaktereket tartalmaz.
**Hiba:** Nem lehet szabályzatot létrehozni vagy eszközöket regisztrálni.

**Megoldás:** A [Microsoft 365 felügyeleti központban](https://admin.microsoft.com/)távolítsa el a speciális karaktereket a vállalat nevéből, és mentse a vállalati adatokat.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Nem lehet bejelentkezni vagy eszközöket regisztrálni több ellenőrzött tartomány esetén
**Probléma:** Ez a probléma akkor merülhet fel, amikor egy második ellenőrzött tartományt ad hozzá az ADFS-hez. A második tartomány egyszerű felhasználóneves (UPN) utótagjával rendelkező felhasználók nem tudnak bejelentkezni a portálokra vagy nem tudnak eszközöket regisztrálni.


<strong>Megoldás:</strong> A Microsoft Office 365-ügyfeleknek az AD FS 2.0 Összevonási szolgáltatás egy külön példányát kell üzembe helyezniük minden utótaghoz az alábbi esetekben:
- ha az AD FS 2.0-n keresztül egyszeri bejelentkezést (SSO-t) használnak
- ha több felső szintű tartomány tartozik a szervezet egyszerű felhasználóneveinek utótagjaihoz (például @contoso.com vagy @fabrikam.com).


Az [AD FS 2.0 összegzése](https://support.microsoft.com/kb/2607496) a <strong>SupportMultipleDomain</strong> kapcsolóval együtt használható, hogy az AD FS-kiszolgáló támogassa az ilyen helyzetet anélkül, hogy további AD FS 2.0 kiszolgálókra lenne szükség. További információt [ebben a blogban](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/) talál.


## <a name="android-issues"></a>Android-problémák

### <a name="android-enrollment-errors"></a>Android-eszközök regisztrálásának hibái

A következő táblázat azon hibákat tartalmazza, melyeket Android-eszközök az Intune-ban való regisztrálásakor tapasztalhatnak a végfelhasználók.

|Hibaüzenet|Probléma|Megoldás|
|---|---|---|
|**A rendszergazdának hozzáférési licencet kell hozzárendelnie**<br>A rendszergazda nem adott hozzáférést az alkalmazás használatához. Kérjen segítséget a rendszergazdától, vagy próbálkozzon újra később.|Az eszközt nem lehet regisztrálni, mert a felhasználó fiókja nem rendelkezik a szükséges licenccel.|Ahhoz, hogy a felhasználók regisztrálhassák az eszközeiket, hozzájuk kell rendelni a szükséges licencet. Ez az üzenet azt jelenti, hogy nem rendelkeznek a megfelelő licenctípussal a mobileszköz-kezelő szolgáltatóhoz. Például ez a hiba jelenik meg, ha az alábbi állítások közül mindkettő igaz:<ol><li>Az Intune van beállítva mobileszköz-kezelési szolgáltatóként</li><li>Egy System Center 2012 R2 Configuration Manager-licencet használnak.</li></ol>További információ: [Intune-licencek felhasználói fiókokhoz való hozzárendelése](/intune/licenses-assign).|
|**A rendszergazdának be kell állítania a mobileszköz-felügyeleti szolgáltatót**<br>Úgy tűnik, hogy a rendszergazda még nem állította be a mobileszköz-kezelő szolgáltatót. Kérjen segítséget a rendszergazdától, vagy próbálkozzon újra később.|A mobileszköz-kezelő szolgáltató még nincs megadva.|A mobileszköz-kezelő szolgáltató még nincs megadva az Intune-ban. További információ [a mobileszköz-felügyeleti szolgáltató beállításáról](/intune/mdm-authority-set).|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Az eszközök nem tudnak lejelentkezni az Intune szolgáltatásnál, és az Intune felügyeleti konzolján „Nem megfelelő” állapotúként jelennek meg
**Probléma:** Egyes, az Android 4.4.x és 5.x verzióját futtató Samsung-eszközök esetében előfordulhat, hogy egy idő után nem jelentkeznek le újra az Intune szolgáltatásnál. Ha nem jelentkeznek le az eszközök:

- Nem kaphatják meg a szabályzatot, az alkalmazásokat és a távoli parancsokat az Intune szolgáltatástól.
- A felügyeleti konzolon **Nem megfelelő** felügyeleti állapotúnak látszanak.
- A feltételes hozzáférési szabályzatok által védett felhasználók elveszíthetik a vállalati erőforrásokhoz való hozzáférést.

Az egyes Samsung-eszközökre előtelepített Samsung Smart Manager szoftver inaktiválhatja az Intune Céges portált és összetevőit. Ha a Céges portál inaktív állapotú, nem futhat a háttérben, ezért nem tud kapcsolatot létesíteni az Intune szolgáltatással.

**1. megoldás:**

Kérje meg a felhasználókat, hogy manuálisan indítsák el a Munkahelyi portál alkalmazást. Az alkalmazás az újraindítása után lejelentkezik az Intune szolgáltatásnál.

> [!IMPORTANT]
> A Munkahelyi portál manuális megnyitása átmeneti megoldás, mert a Samsung Smart Manager ismét inaktiválhatja a Munkahelyi portál alkalmazást.

**2. megoldás:**

Kérje meg a felhasználókat, hogy próbáljanak meg frissíteni az Android 6.0-s verziójára. Az Android 6.0 rendszerű eszközökön nem jelentkezik az inaktiválás problémája. A **Beállítások** > **Eszköz névjegye** > **Frissítések manuális letöltése** területen ellenőrizheti, hogy elérhető-e frissítés. A frissítést a megjelenő útmutatás szerint végezheti el.

**3. megoldás:**

Ha a 2. megoldás nem működik, kérje a felhasználókat a következő lépések elvégzésére, hogy a Smart Manager ne felügyelje a Munkahelyi portál alkalmazást:

1. Indítsa el az eszközön a Smart Manager alkalmazást.

   ![A Smart Manager ikon kiválasztása az eszközön](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. Válassza a **Battery** (Akkumulátor) csempét.

   ![A Battery (Akkumulátor) csempe kiválasztása](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. Válassza az **App power saving** (Alkalmazás energiatakarékossága) vagy **App optimization** (Alkalmazás optimalizálása) terület **Detail** (Részletek) elemét.

   ![Az App power saving (Alkalmazás energiatakarékossága) vagy App optimization (Alkalmazás optimalizálása) terület Detail (Részletek) elemének kiválasztása](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. Koppintson a **Munkahelyi portál** elemre az alkalmazáslistában.

   ![A Munkahelyi portál kiválasztása az alkalmazáslistából](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. Válassza a **Turned off** (Kikapcsolva) beállítást.

   ![A Turned off (Kikapcsolva) beállítás kiválasztása az App optimization (Alkalmazás optimalizálása) párbeszédpanelen](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. Győződjön meg róla az **App power saving** (Alkalmazás energiatakarékossága) vagy az **App optimization** (Alkalmazás optimalizálása) területen, hogy a Munkahelyi portál ki van kapcsolva.

   ![Annak ellenőrzése, hogy a Munkahelyi portál ki van-e kapcsolva](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Profiltelepítési hiba
**Hiba:** **Profiltelepítési hiba** üzenet jelenik meg egy Android-eszközön.

**Megoldás:**

1. Ellenőrizze, hogy az Ön által használt Intune szolgáltatás verziójának megfelelő licenc van-e hozzárendelve a felhasználóhoz.

2. Ellenőrizze, hogy az eszköz nincs-e egy másik mobileszköz-kezelő szolgáltatónál regisztrálva.

3. Ellenőrizze, hogy az eszköz nem rendelkezik-e már egy kezelési profillal.

4. Ellenőrizze, hogy az Androidhoz készült Chrome az alapértelmezett böngésző-e, és a cookie-k engedélyezettek-e.

### <a name="android-certificate-issues"></a>Android-tanúsítványokkal kapcsolatos problémák

**Probléma:** A felhasználók eszközén a következő üzenet jelenik meg: *Nem tud bejelentkezni, mert az eszközön hiányzik egy szükséges tanúsítvány.*

**1. megoldás**:

Előfordulhat, hogy a felhasználó [Az eszközhöz hiányzik egy szükséges tanúsítvány](/intune-user-help/your-device-is-missing-a-required-certificate-android) című témakörben leírt útmutatás alapján be tudja szerezni a hiányzó tanúsítványt. Ha a hiba továbbra is fennáll, próbálkozzon a 2. megoldással.

**2. megoldás**:

A felhasználók a vállalati hitelesítő adatok megadását és az összevont bejelentkezési oldalra való átirányítást követően is a hiányzó tanúsítványra utaló hibát láthatják. Ebben az esetben a hiba azt jelentheti, hogy hiányzik egy közbenső tanúsítvány az Active Directory Összevonási szolgáltatások (AD FS) kiszolgálójáról

A tanúsítványhiba azért fordul elő, mert az androidos eszközöknek közbenső tanúsítványokra van szükségük ahhoz, hogy szerepelhessenek az [SSL-kiszolgáló hello üzeneteiben](https://technet.microsoft.com/library/cc783349.aspx). Jelenleg az AD FS-kiszolgáló vagy a WAP és az AD FS közötti proxykiszolgáló alapértelmezett példányai csak az AD FS szolgáltatás SSL-tanúsítványát küldik el az SSL-kiszolgáló SSL-ügyfelek hello kérelmére adott hello válaszában.

A probléma megoldásához importálja a tanúsítványt az AD FS-kiszolgálón vagy a proxykon található személyes számítógép-tanúsítványok tárába a következő módon:

1. Az ADFS és proxykiszolgálók szakaszban kattintson a jobb gombbal a **Start** > **Futtatás** > **certlm.msc** elemre a Helyi gép tanúsítványkezelő konzoljának indításához.
2. Bontsa ki a **Személyes** elemet, majd válassza a **Tanúsítványok** lehetőséget.
3. Keresse meg az AD FS szolgáltatással való kommunikációhoz szükséges tanúsítványt (ez egy nyilvános aláírású tanúsítvány), és kattintson rá duplán a tulajdonságok megjelenítéséhez.
4. Válassza a **Tanúsítványlánc** lapot a tanúsítvány szülőtanúsítványának vagy -tanúsítványainak megjelenítéséhez.
5. Az összes szülőtanúsítványnál válassza a **Tanúsítvány megtekintése** lehetőséget.
6. Válassza a **Részletek** > **Másolás fájlba...**  lehetőséget.
7. A varázsló utasításait követve exportálja vagy mentse a szülőtanúsítvány nyilvános kulcsát a fájl kívánt helyére.
8. Kattintson a jobb gombbal a **Tanúsítványok** > **Minden feladat** > **Importálás** lehetőségre.
9. A varázsló utasításait követve importálja a szülőtanúsítvány(oka)t a **Helyi számítógép\Személyes\Tanúsítványok** helyre.
10. Indítsa újra az AD FS-kiszolgálókat.
11. Ismételje meg a fenti lépéseket az összes AD FS- és proxykiszolgálón.

A [https://www.digicert.com/help/](https://www.digicert.com/help/) címen elérhető diagnosztikai eszközzel ellenőrizheti, hogy a tanúsítvány megfelelően lett-e telepítve. A **Kiszolgáló címe** mezőbe írja be az AD FS-kiszolgáló teljes tartománynevét (példa: sts.contso.com), majd kattintson a **Kiszolgáló vizsgálata** lehetőségre.

**A tanúsítványok megfelelő telepítésének ellenőrzése**:

A következő lépésekben csupán a tanúsítvány megfelelő telepítésének ellenőrzésére rendelkezésre álló számos módszer és eszköz egyikét mutatjuk be.

1. Nyissa meg az [ingyenes Digicert eszközt](ttps://www.digicert.com/help/).
2. Adja meg az AD FS-kiszolgáló teljes tartománynevét (például sts.contoso.com), majd válassza a **CHECK SERVER** (Kiszolgáló ellenőrzése) lehetőséget.

Ha a kiszolgálótanúsítványt megfelelően telepítette, az eredményeknél csak pipák jelennek meg. Ha a fenti probléma továbbra sem szűnt meg, piros X jelenik meg a jelentés „Certificate Name Matches” (Tanúsítványnév-egyezések) és „SSL Certificate is correctly Installed” (Az SSL-tanúsítvány megfelelő telepítése) részében.


## <a name="iosipados-issues"></a>iOS/iPadOS problémák

### <a name="iosipados-enrollment-errors"></a>iOS-/iPadOS-regisztrálási hibák
A következő táblázat felsorolja azokat a hibákat, amelyeket a végfelhasználók láthatnak az iOS/iPadOS-eszközök Intune-beli regisztrálásakor.

|Hibaüzenet|Probléma|Megoldás|
|-------------|-----|----------|
|NoEnrollmentPolicy|Nem található eszközregisztrációs szabályzat|Győződjön meg arról, hogy az összes regisztrációs előfeltétel, például a Apple Push Notification Service (APNs) tanúsítvány be van állítva, és hogy az "iOS/iPadOS as a platform" engedélyezve van. Útmutatásért lásd: [iOS-/iPadOS-és Mac-eszközök kezelésének beállítása](../ios-enroll.md).|
|DeviceCapReached|A már regisztrált mobileszközök száma túl magas.|A felhasználónak el kell távolítania az aktuálisan regisztrált mobileszközeit a Céges portálról, mielőtt másikat regisztrálhatna. Tekintse meg az Ön által használt eszköz típusára vonatkozó utasításokat: [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS/iPadOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Probléma merült fel azzal a tanúsítvánnyal kapcsolatban, amely lehetővé teszi a mobileszköz és a céges hálózat közötti kommunikációt.<br /><br />|A Apple Push Notification Service (APNs) biztosítja a regisztrált iOS/iPadOS-eszközökhöz való kapcsolódáshoz szükséges csatornát. A következő esetekben a regisztráció meghiúsul és ez az üzenet jelenik meg:<ul><li>Az APNs-tanúsítvány beszerzésének lépéseit nem végezték el, vagy</li><li>Az APNs-tanúsítvány lejárt.</li></ul>A felhasználók konfigurálásához olvassa el [Az Active Directory szinkronizálása és felhasználók hozzáadása az Intune szolgáltatáshoz](../fundamentals/users-add.md) című szakaszt, valamint a [felhasználók és eszközök rendszerezésével](../fundamentals/groups-add.md) kapcsolatos tudnivalókat.|
|AccountNotOnboarded|Probléma merült fel azzal a tanúsítvánnyal kapcsolatban, amely lehetővé teszi a mobileszköz és a céges hálózat közötti kommunikációt.<br /><br />|A Apple Push Notification Service (APNs) biztosítja a regisztrált iOS/iPadOS-eszközökhöz való kapcsolódáshoz szükséges csatornát. A következő esetekben a regisztráció meghiúsul és ez az üzenet jelenik meg:<ul><li>Az APNs-tanúsítvány beszerzésének lépéseit nem végezték el, vagy</li><li>Az APNs-tanúsítvány lejárt.</li></ul>További információkért tekintse át [az iOS/iPadOS és a Mac Management beállítása a Microsoft Intunekal](../ios-enroll.md)című témakört.|
|DeviceTypeNotSupported|Lehet, hogy a felhasználó nem iOS-eszközzel próbált meg regisztrálni. A regisztrálni próbált mobileszköz típusa nem támogatott.<br /><br />Győződjön meg arról, hogy az eszközön a 8,0-es vagy újabb iOS-/iPadOS-verzió fut.<br /><br />|Győződjön meg arról, hogy a felhasználó eszközén a 8,0-es vagy újabb iOS-/iPadOS-verzió fut.|
|UserLicenseTypeInvalid|A mobileszköz nem regisztrálható, mert a felhasználói fiók még nem tagja egy szükséges felhasználói csoportnak.<br /><br />|Ahhoz, hogy a felhasználók regisztrálhassák eszközeiket, a megfelelő felhasználói csoport tagjának kell lenniük. Ez az üzenet azt jelenti, hogy nem rendelkeznek a megfelelő licenctípussal a mobileszköz-kezelő szolgáltatóhoz. Például ez a hiba jelenik meg, ha az alábbi állítások közül mindkettő igaz:<ol><li>Az Intune van beállítva mobileszköz-kezelési szolgáltatóként</li><li>Egy System Center 2012 R2 Configuration Manager-licencet használnak.</li></ol>További információért tekintse át az alábbi cikkeket:<br /><br />Tekintse át az [iOS-/iPadOS-és Mac-kezelés beállítása a Microsoft Intune](../ios-enroll.md) és a [szinkronizálási Active Directory](../fundamentals/users-add.md) felhasználók beállításával és a felhasználók [és eszközök rendszerezésével](../fundamentals/groups-add.md)kapcsolatos tudnivalókat ismertető témakört.|
|MdmAuthorityNotDefined|A mobileszköz-kezelő szolgáltató még nincs megadva.<br /><br />|A mobileszköz-kezelő szolgáltató még nincs megadva az Intune-ban.<br /><br />Tekintse meg az 1. elemet [Az első lépések a Microsoft Intune 30 napos próbaverziójában](../fundamentals/free-trial-sign-up.md) „6. lépés: Mobileszközök regisztrálása és alkalmazások telepítése” szakaszában.|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>Az eszközök inaktívak, vagy a felügyeleti konzol nem tud kommunikálni velük
**Probléma:** az iOS/iPadOS-eszközök nem ellenőrzik az Intune szolgáltatást. Az eszközök csak a szolgáltatásba való rendszeres bejelentkezéssel őrizhetik meg a vállalati erőforrásokhoz való hozzáférési jogosultságukat. Ha az eszközök rendszeres bejelentkezése nem történik meg:

- Nem kaphatják meg a szabályzatot, az alkalmazásokat és a távoli parancsokat az Intune szolgáltatástól.
- A felügyeleti konzolon **Nem megfelelő** felügyeleti állapotúnak látszanak.
- A feltételes hozzáférési szabályzatok által védett felhasználók elveszíthetik a vállalati erőforrásokhoz való hozzáférést.

**Megoldás:** Az alábbi megoldások megosztásával segíthet a végfelhasználóknak visszaszerezni a vállalati erőforrásokhoz való hozzáférési jogosultságukat.

Ha a felhasználók elindítják az iOS/iPadOS Céges portál alkalmazást, megtudhatja, hogy az eszközük elvesztette-e az Intune-nal való kapcsolatfelvételt. Ha az alkalmazás azt észleli, hogy nincs kapcsolat, automatikusan megpróbál szinkronizálni az Intune-nal az újrakapcsolódáshoz, és a felhasználók a következő értesítést fogják látni: **A szinkronizálási kísérlet folyamatban van...** .

  ![A szinkronizálási kísérlet folyamatban van – értesítés](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

Ha a szinkronizálás sikeres, a **szinkronizálás sikeres** beágyazott értesítés jelenik meg az iOS/iPadOS céges portál alkalmazásban, ami azt jelzi, hogy az eszköz kifogástalan állapotban van.

  ![Sikeres szinkronizálás – értesítés](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

Ha a szinkronizálás sikertelen, a felhasználók **nem tudják szinkronizálni** a beágyazott értesítéseket az iOS/iPadOS céges portál alkalmazásban.

  ![Nem lehet szinkronizálni – értesítés](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

A probléma elhárításához a felhasználóknak a **Nem lehet szinkronizálni** értesítés jobb oldalán lévő **Beállítás** gombot kell használniuk. A Beállítás gomb használatával a felhasználók a Vállalati hozzáférés beállítása folyamatképernyőre kerülnek, ahol a képernyőn megjelenő utasítások követésével regisztrálhatják az eszközüket.

  ![A Vállalati hozzáférés beállítása képernyő](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

Regisztráció után az eszközök ismét kifogástalan állapotba kerülnek, és visszakapják a vállalati erőforrásokhoz való hozzáférési jogosultságukat.

### <a name="verify-ws-trust-13-is-enabled"></a>Ellenőrizze, hogy a WS-Trust 1.3 engedélyezve van-e
**Probléma** Készülékregisztrációs program (DEP) iOS/iPadOS-eszközök nem regisztrálhatók

A felhasználói affinitással rendelkező DEP-eszközök regisztrálása esetében a felhasználói jogkivonat kérelmezéséhez engedélyezni kell a WS-Trust 1.3 Username/Mixed végpontot. Az Active Directory alapértelmezés szerint engedélyezi ezt a végpontot. A Get-AdfsEndpoint PowerShell-parancsmagot futtatva, majd a trust/13/UsernameMixed végpontot megkeresve láthatja az engedélyezett végpontok listáját. Például:

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

További információt a [Get-AdfsEndpoint dokumentációjában](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint) talál.

További információt az [Ajánlott eljárások az Active Directory összevonási szolgáltatások biztonságossá tételéhez](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs) című cikkben talál. Ha segítséget szeretne kérni a WS-Trust 1.3 Username/Mixed identitás-összevonási szolgáltatóbeli engedélyezési állapotának megállapításához, tegye a következőket:
- forduljon a Microsoft ügyfélszolgálatához, ha az ADFS-t használja
- forduljon a külső szállítóhoz.


### <a name="profile-installation-failed"></a>Profiltelepítési hiba
**Probléma:** Egy felhasználó egy iOS-/iPadOS-eszközön **sikertelenül** kapott egy profilt.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Sikertelen profiltelepítés hibaelhárításának lépései

1. Ellenőrizze, hogy az Ön által használt Intune szolgáltatás verziójának megfelelő licenc van-e hozzárendelve a felhasználóhoz.

2. Ellenőrizze, hogy az eszköz nincs-e egy másik mobileszköz-kezelő szolgáltatónál regisztrálva.

3. Ellenőrizze, hogy az eszköz nem rendelkezik-e már egy kezelési profillal.

4. Navigáljon a [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) oldalra, és telepítse a profilt a rendszer kérésekor.

5. Ellenőrizze, hogy az iOS/iPadOS Safari az alapértelmezett böngésző-e, és hogy a cookie-k engedélyezve vannak-e.

### <a name="users-iosipados-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>A felhasználó iOS-/iPadOS-eszköze több mint 10 percen belül beragadt a beléptetési képernyőn

**Probléma**: Egy regisztrálandó eszköz elakadhat az alábbi két képernyő egyikén:
- A végső Microsoft-konfigurációra való várakozás során
- Nem érhető el a Guided Access alkalmazás. Forduljon a rendszergazdához.

A probléma a következő esetekben jelentkezhet:
- átmeneti szolgáltatáskimaradás tapasztalható az Apple szolgáltatásaiban, vagy
- az iOS-/iPadOS-regisztráció VPP-tokenek használatára van beállítva, ahogy az a táblázatban látható, de a VPP-tokennél valami nem stimmel.

| Regisztrációs beállítások | Érték |
| ---- | ---- |
| Platform | iOS/iPadOS |
| Felhasználói affinitás | Felhasználói affinitással rendelkező eszközök regisztrálása |
|Hitelesítés a Céges portállal az Apple Beállítási asszisztense helyett | Igen |
| A Céges portál telepítése a VPP-vel | Token használata: token címe |
| A Céges portál futtatása egyalkalmazásos módban a hitelesítésig | Igen |

**Megoldás**: A probléma megoldásához a következőket kell tennie:
1. Határozza meg, hogy hibás-e a VPP-token, és ha igen, javítsa ki.
2. Azonosítsa, mely eszközök vannak letiltva.
3. Törölje az érintett eszközök összes adatát.
4. Kérje meg a felhasználót, hogy kezdje újra a regisztrációs folyamatot.

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>Annak meghatározása, hogy hibás-e a VPP-token
1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > a **beléptetési program jogkivonatok** > token neve > **profilok** > profil neve > > **Tulajdonságok** **kezelése** lehetőséget.
2. Tekintse át a tulajdonságokat, és ellenőrizze, hogy találhatók-e a következőhöz hasonló hibák:
    - A token lejárt.
    - A token a Céges portál licenceinek hatókörén kívülre esik.
    - A tokent egy másik szolgáltatás használja.
    - A tokent egy másik bérlő használja.
    - A tokent törölték.
3. Hárítsa el a token problémáit.

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>A VPP-token által letiltott eszközök azonosítása
1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **iOS**k > **iOS-regisztráció** > a **beléptetési program jogkivonatok** > token neve > **eszközök**elemet.
2. Szűrje a **Profil állapota** oszlopot **Letiltva** állapot szerint.
3. Jegyezze fel a **letiltott** eszközök sorozatszámait.

#### <a name="remotely-wipe-the-blocked-devices"></a>A letiltott eszközök adatainak távoli törlése
Miután kijavította a VPP-token problémáit, törölnie kell a letiltott eszközök adatait.
1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **minden eszköz** > **oszlopok** > **sorozatszám** > **alkalmaz**lehetőséget. 
2. A letiltott eszközök esetén válassza ki őket a **Minden eszköz** listában, majd válassza a **Törlés** > **Igen** lehetőséget.

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>A felhasználók megkérése a regisztrációs folyamat újrakezdésére
A letiltott eszközök törlését követően megkérheti a felhasználókat, hogy kezdjék újra a regisztrációs folyamatot.

## <a name="macos-issues"></a>macOS-problémák

### <a name="macos-enrollment-errors"></a>macOS-regisztrálási hibák
**1. hibaüzenet:** úgy *tűnik, mintha egy virtuális gépet használ. Győződjön meg arról, hogy teljesen konfigurálta a virtuális gépet, beleértve a sorozatszámot és a hardveres modellt is. Ha ez nem egy virtuális gép, forduljon az ügyfélszolgálathoz.*  

**2. hibaüzenet:** *probléma merült fel az eszköz felügyeletének beolvasásakor. Ezt a problémát az okozhatja, ha virtuális gépet használ, korlátozott sorozatszámmal rendelkezik, vagy ha az eszköz már hozzá van rendelve valaki másnak. Megtudhatja, hogyan oldja meg ezeket a problémákat, vagy forduljon a cég informatikai támogatási szolgálatához.*

**Probléma:** Ez az üzenet lehet az alábbi okok bármelyikének a következménye:  
- Egy macOS rendszerű virtuális gép (VM) nincs megfelelően konfigurálva  
- Olyan eszközkorlátozásokat engedélyezett, amelyek megkövetelik, hogy az eszköz vállalati tulajdonú legyen, vagy regisztrált eszközsorozatszámmal rendelkezzen az Intune-ban  
- Az eszköz már regisztrálva van, és még hozzá van rendelve valaki máshoz az Intune-ban  

**Megoldás:** Először ellenőrizze a felhasználónál, hogy melyik probléma áll fenn az eszközén. Ez után alkalmazza a következő megoldások közül a legrelevánsabbat:

- Ha a felhasználó tesztelési célból regisztrál virtuális gépet, győződjön meg róla, hogy az teljesen konfigurálva van, hogy az Intune felismerhesse a sorozatszámát és a hardvermodellt. További információ a [virtuális gépek beállításáról](macos-enroll.md#enroll-virtual-macos-machines-for-testing) az Intune-ban.
- Ha a szervezet olyan regisztrációs korlátozásokat vezetett be, amelyek letiltják a személyes macOS-eszközöket, akkor manuálisan kell [hozzáadnia a személyes eszköz sorozatszámát](corporate-identifiers-add.md#manually-enter-corporate-identifiers) az Intune-hoz.  
- Ha az eszköz még hozzá van rendelve egy másik felhasználóhoz az Intune-ban, akkor a korábbi tulajdonosa nem használta a Céges portál alkalmazást az eltávolításához vagy alaphelyzetbe állításához. A elavult eszközrekord törlése az Intune-ból:  

    1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)jelentkezzen be rendszergazdai hitelesítő adataival.
    2. Válassza az **eszközök** > **minden eszköz**lehetőséget.  
    3. Keresse meg a regisztrációs problémával rendelkező eszközt. Az eredmények szűkítéséhez keressen az eszköz neve vagy a MAC-/hardvercím alapján.
    4. Válassza ki az eszközt > **Törlés**. Törölje az eszközhöz társított összes többi bejegyzést.  

## <a name="pc-issues"></a>PC-kkel kapcsolatos problémák

|Hibaüzenet|Probléma|Megoldás|
|---|---|---|
|**A rendszergazdának hozzáférési licencet kell hozzárendelnie**<br>A rendszergazda nem adott hozzáférést az alkalmazás használatához. Kérjen segítséget a rendszergazdától, vagy próbálkozzon újra később.|Az eszközt nem lehet regisztrálni, mert a felhasználó fiókja nem rendelkezik a szükséges licenccel.|Ahhoz, hogy a felhasználók regisztrálhassák az eszközeiket, hozzájuk kell rendelni a szükséges licencet. Ez az üzenet azt jelenti, hogy nem rendelkeznek a megfelelő licenctípussal a mobileszköz-kezelő szolgáltatóhoz. Például ez a hiba jelenik meg, ha az alábbi állítások közül mindkettő igaz: <ol><li>Az Intune van beállítva mobileszköz-kezelési szolgáltatóként</li><li>Egy System Center 2012 R2 Configuration Manager-licencet használnak.</li></ol>További információ [az Intune-licencek felhasználói fiókokhoz való hozzárendelésével](../fundamentals/licenses-assign.md) kapcsolatban.|

### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>A gép már regisztrálva van – hibakód: hr 0x8007064c

**Hiba:** A regisztrálás sikertelen **A gép már regisztrálva van** hibaüzenettel. A regisztrálási napló a **hr 0x8007064c** hibakódot tartalmazza.

Ez a hiba akkor fordulhat elő, ha a számítógépet:

- korábban már regisztrálták, vagy
- egy már regisztrált számítógép klónozott lemezképével rendelkezik.
Az előző fiók fióktanúsítványa továbbra is megtalálható a számítógépen.

**Megoldás:**

1. A **Start** menüben használja a **Futtatás** -> **MMC** parancsot.
1. Válassza a **Fájl** > **Beépülő modulok hozzáadása/eltávolítása** parancsot.
1. Kattintson duplán a **Tanúsítványok** elemre, válassza a **Számítógépfiók** >  lehetőséget, kattintson a **Tovább** gombra, végül válassza a **Helyi számítógép** lehetőséget.
1. Kattintson duplán a **Tanúsítványok (Helyi számítógép)** elemre, majd válassza a **Személyes/Tanúsítványok** lehetőséget.
1. Keresse meg az Sc_Online_Issuing által kiadott Intune-tanúsítványt, és ha létezik, törölje.
1. Ha létezik, törölje a következő beállításkulcsot és az összes alkulcsát: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey**.
1. Kísérelje meg újból a regisztrációt.
1. Ha a számítógépet továbbra sem lehet regisztrálni, keresse meg a következő beállításkulcsot, és ha létezik, törölje: **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Kísérelje meg újból a regisztrációt.

    > [!IMPORTANT]
    > Ez a szakasz, módszer vagy feladat olyan lépéseket tartalmaz, amelyekkel módosítja a beállításjegyzéket. A beállításjegyzék nem megfelelő módosítása azonban súlyos hibákat okozhat. Ezért ügyeljen arra, hogy pontosan kövesse a leírtakat. További biztonsági intézkedésként a módosítások végrehajtása előtt készítsen biztonsági másolatot a beállításjegyzékről. Így probléma esetén helyreállíthatja a beállításjegyzéket.
    > Ha további tájékoztatásra van szüksége a beállításjegyzék biztonsági mentéséről és visszaállításáról, olvassa el a [How to back up and restore the registry in Windows](https://support.microsoft.com/kb/322756) (A beállításjegyzék biztonsági mentése és visszaállítása a Windows rendszerben) című témakört.

## <a name="general-enrollment-error-codes"></a>Általános beléptetési hibakódok

|Hibakód|Lehetséges probléma|Javasolt megoldás|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |Az ügyfélszámítógép órája nem a helyes időre van beállítva.|Győződjön meg róla, hogy az ügyfélszámítógép órája és időzónája a helyes értékre van beállítva.|
|0x80240438, 0x80CF0438, 0x80CF402C|Nem lehet kapcsolódni az Intune szolgáltatáshoz. Ellenőrizze az ügyfél proxybeállításait.|Győződjön meg arról, hogy az Intune támogatja az ügyfélszámítógép proxykonfigurációját. Ellenőrizze, hogy az ügyfélszámítógép rendelkezik-e internetkapcsolattal.|
|0x80240438, 0x80CF0438|Az Internet Explorer és a helyi rendszer proxybeállításai nincsenek konfigurálva.|Nem lehet kapcsolódni az Intune szolgáltatáshoz. Ellenőrizze az ügyfél proxybeállításait. Győződjön meg arról, hogy az Intune támogatja az ügyfélszámítógép proxykonfigurációját. Ellenőrizze, hogy az ügyfélszámítógép rendelkezik-e internetkapcsolattal.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|A beléptetési csomag elavult.|Töltse le és telepítse az aktuális ügyfélszoftvercsomagot a Felügyelet munkaterületen.|
|0x80043002, 0x80CF3002|A fiók karbantartási módban van.|Nem tud új ügyfélszámítógépeket regisztrálni, ha a fiók karbantartási módban van. A fiókbeállítások megtekintéséhez jelentkezzen be a fiókba.|
|0x80043003, 0x80CF3003|A fiókot törölték.|Ellenőrizze, hogy az Intune-fiókja és -előfizetése aktív-e. A fiókbeállítások megtekintéséhez jelentkezzen be a fiókba.|
|0x80043005, 0x80CF3005|Az ügyfélszámítógépet eltávolították.|Várjon néhány órát, távolítsa el az ügyfélszoftver minden régebbi verzióját a számítógépről, majd próbálja meg újból telepíteni az ügyfélszoftvert.|
|0x80043006, 0x80CF3006|Elérte a fiók számára engedélyezett maximális munkaállomásszámot.|A szervezetnek további munkaállomásokat kell vásárolnia, mielőtt további ügyfélszámítógépeket léptethet be a szolgáltatásba.|
|0x80043007, 0x80CF3007|A tanúsítványfájl nem található abban a mappában, amelyben a telepítőprogram van.|A telepítés kezdete előtt az összes fájlt csomagolja ki. Ne nevezze át és ne helyezze át a kicsomagolt fájlokat: az összes fájlnak ugyanabban a mappában kell lennie, különben a telepítés sikertelen lesz.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|A szoftvert nem lehet telepíteni, mert függőben van az ügyfélszámítógép újraindítása.|Indítsa újra a számítógépet, majd próbálja meg újból az ügyfélszoftver telepítését.|
|0x80070032|Az ügyfélszámítógép nem felel meg az ügyfélszoftver telepítéséhez szükséges egy vagy több előfeltételnek.|Gondoskodjon róla, hogy minden szükséges frissítés telepítve legyen az ügyfélszámítógépen, majd próbálja meg újból az ügyfélszoftver telepítését.|
|0x80043008, 0x80CF3008|Nem sikerült elindítani a Microsoft Online Management Updates szolgáltatást.|Lépjen kapcsolatba a Microsoft ügyfélszolgálatával a [Hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md) című szakaszban leírtak szerint.|
|0x80043009, 0x80CF3009|Az ügyfélszámítógép már be van léptetve a szolgáltatásba.|Az ügyfélszámítógépet el kell távolítania, mielőtt újból beléptetheti a szolgáltatásba.|
|0x8004300B, 0x80CF300B|Az ügyfélszoftver telepítési csomagja nem futtatható, mert az ügyfélen futó Windows-verzió nem támogatott.|Az Intune nem támogatja az ügyfélszámítógépen futó Windows-verziót.|
|0xAB2|A Windows Installer nem tud hozzáférni a VBScript futtatókörnyezethez egy egyéni művelet végrehajtásához.|A hibát egy egyéni művelet okozza, amely dinamikus kötésű kódtárakon (DLL-eken) alapul. Előfordulhat, hogy a DLL hibáinak elhárításához a következő témakörben ismertetett eszközöket kell használnia: [Microsoft Support KB198038: Useful Tools for Package and Deployment Issues](https://support.microsoft.com/kb/198038) (Hasznos eszközök csomag- és telepítési problémák esetére).|
|0x80cf0440|Megszakadt a kapcsolat a szolgáltatásvégponttal.|A próbafiók vagy a díjköteles fiók fel van függesztve. Hozzon létre egy új próbafiókot vagy díjköteles fiókot, és végezze el újból a regisztrálást.|

## <a name="next-steps"></a>További lépések

Ha ezek a hibaelhárítási információk nem oldották meg a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](../fundamentals/get-support.md) című témakörben leírtak szerint.
