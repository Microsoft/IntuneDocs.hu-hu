---
title: PC-s ügyfélszoftver telepítése
description: Ezzel az útmutatóval beállíthatja a Windows rendszerű számítógépeinek a Microsoft Intune-ügyfélszoftverrel való kezelését.
keywords: ''
author: ErikjeMS
ms.author: erikje
ms.date: 07/13/2017
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 99dcf916-d80f-42c5-863b-a4595e1ec67a
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1484aa2cf9ab665796b6c02e060d2d7c4cb4fcd1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502786"
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Az Intune-szoftverügyfél telepítése Windows rendszerű számítógépekre

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> A Microsoft Intune-ban kezelheti a Windows-számítógépeket [mobileszközként a mobileszköz-kezelés (MDM),](../enrollment/windows-enroll.md) vagy számítógépként az Intune szoftverügyfél használatával, a lent ismertetett módon. A Microsoft azonban azt javasolja, hogy az ügyfelek [lehetőség szerint az MDM-megoldást válasszák](../enrollment/windows-enroll.md) a felügyelethez. További információ: a [Windows rendszerű számítógépek számítógépként vagy mobileszközökként való kezelésének összehasonlítása](pc-management-comparison.md) 


A Windows rendszerű számítógépek az Intune-ügyfélszoftver telepítésével regisztrálhatók. Az Intune-ügyfélszoftver a következő módszerekkel telepíthető:

- A rendszergazda által az alábbi három módszer egyikével: manuális telepítés, Csoportházirenddel vagy lemezkép részeként történő telepítéssel

- A végfelhasználók által, az ügyfélszoftver manuális telepítésével

Az Intune-ügyfélszoftver tartalmazza azt a szoftvert, amely ahhoz szükséges, hogy a számítógépet regisztrálja az Intune-felügyeletben. A számítógép regisztrálása után az Intune-ügyfélszoftver letölti a számítógép felügyeletéhez szükséges teljes ügyfélszoftvert.

Az egymást követő letöltések csökkentik a hálózati sávszélességre gyakorolt hatást és minimálisra csökkentik a számítógép Intune-ban való kezdeti regisztrálásához szükséges időt. Emellett azt is biztosítja, hogy a második letöltést követően az ügyfél a legfrissebb szoftverrel rendelkezzen.

Egy Intune-licenc legfeljebb öt számítógépen teszi lehetővé az Intune-ügyfélszoftver telepítését.

## <a name="download-the-intune-client-software"></a>Az Intune-ügyfélszoftver letöltése

Az összes módszer, kivéve azokat, amelyekben maguk a felhasználók telepítik az Intune-ügyfélszoftvert, megköveteli a szoftver letöltését, hogy ezután központilag lehessen telepíteni azt a végfelhasználók számára.

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Felügyelet** &gt; **Ügyfélszoftver letöltése** lehetőségre.

   ![Az Intune-számítógépügyfél letöltése](./media/install-the-windows-pc-client-with-microsoft-intune/pc-sa-client-download.png)

2. Az **Ügyfélszoftver letöltése** oldalon kattintson az **Ügyfélszoftver letöltése** elemre. Ezt követően mentse a szoftvert tartalmazó **Microsoft_Intune_Setup.zip** csomagot a hálózat egy biztonságos helyére.

   Az Intune-ügyfélszoftver telepítési csomagja egyedi és specifikus információt tartalmaz, amely egy beágyazott tanúsítványon keresztül érhető el, és az Ön fiókjára vonatkozik. Ha jogosulatlan felhasználók férnek hozzá a telepítőcsomaghoz, a beágyazott tanúsítvány által jelölt fiókhoz számítógépeket regisztrálhatnak, és hozzáférhetnek a vállalat erőforrásaihoz.

3. Bontsa ki a telepítőcsomag tartalmát a biztonságos helyre a hálózaton.

    > [!IMPORTANT]
    > Ne nevezze át és ne távolítsa el a kibontott **ACCOUNTCERT** fájlt, különben az ügyfélszoftver telepítése sikertelen lesz.

## <a name="deploy-the-client-software-manually"></a>Ügyfélszoftver manuális telepítése

Ugorjon az ügyfélszoftver telepítési fájljait tartalmazó mappára azon számítógép(ek)en, amely(ek)re az ügyfélszoftvert telepíteni fogja. Futtassa a **Microsoft_Intune_Setup.exe** fájlt az ügyfélszoftver telepítéséhez.

> [!NOTE]
> A telepítés állapota akkor jelenik meg, ha az ügyfélszámítógép tálcáján megjelenő ikonra mutat.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Az ügyfélszoftver telepítése Csoportházirenddel

1. A **Microsoft_Intune_Setup.exe** és a **MicrosoftIntune.accountcert** fájlt tartalmazó mappában futtassa a következő parancsot a 32 bites és 64 bites számítógépekhez készült Windows Installer-alapú telepítőprogramok kibontásához:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2. Másolja a **Microsoft_Intune_x86.msi** fájlt, a **Microsoft_Intune_x64.msi** fájlt és a **MicrosoftIntune.accountcert** fájlt egy olyan hálózati helyre, amely minden olyan számítógép számára elérhető, amelyre telepíteni kívánja az ügyfélszoftvert.

    > [!IMPORTANT]
    > A fájlokat ne válassza szét vagy nevezze át, különben az ügyfélszoftver telepítése sikertelen lesz.

3. A Csoportházirenddel telepítse a szoftvert a hálózaton lévő számítógépekre.

    A szoftverek Csoportházirenddel történő automatikus telepítésével kapcsolatban a [Group Policy for Beginners](https://technet.microsoft.com/library/hh147307.aspx) (Csoportházirend kezdőknek) című angol nyelvű anyagban találhat további információkat.

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Egy lemezkép részeként telepítse az ügyfélszoftvert
Az Intune ügyfélszoftverét az alábbi eljárás alapján egy operációsrendszer-kép részeként is telepítheti a számítógépekre:

1. Az ügyfél telepítési fájljait, a **Microsoft_Intune_Setup.exe** és a **MicrosoftIntune.accountcert** fájlt másolja a **%Systemdrive%\Temp\Microsoft_Intune_Setup** mappába a referencia-számítógépen.

2. Hozzon létre egy **WindowsIntuneEnrollPending** nevű bejegyzést a beállításjegyzékben a következő parancs hozzáadásával a **SetupComplete.cmd** parancsfájlhoz:

    ```cmd
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3. A következő parancs a **setupcomplete.cmd** parancsfájlhoz való hozzáadásával futtassa a regisztrációs csomagot a /PrepareEnroll parancssori argumentummal:

    ```cmd
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```

    > [!TIP]
    > A **SetupComplete.cmd** parancsfájl lehetővé teszi, hogy a Windows telepítő módosításokat végezzen a rendszeren egy felhasználó bejelentkezése előtt. A **/PrepareEnroll** parancssori argumentum előkészíti a célzott számítógépet a Windows telepítő befejeződése után az Intune-ban való automatikus regisztráláshoz.

4. Helyezze a **SetupComplete.cmd** fájlt a **%Windir%\Setup\Scripts** mappába a referencia-számítógépen.

5. Rögzítsen egy rendszerképet a referencia-számítógépről, majd telepítse azt a célként megadott számítógépekre.

    Amikor a célszámítógép a Windows telepítő befejezése után újraindul, létrejön a **WindowsIntuneEnrollPending** beállításkulcs. A regisztrálási csomag ellenőrzi, hogy regisztrálva van-e a számítógép. Ha a számítógép regisztrálva van, nem szükséges további művelet. Ha a számítógép nincs regisztrálva, a regisztrálási csomag létrehoz egy automatikus Microsoft Intune-regisztrálási feladatot.

    Amikor a következő ütemezett időpontban lefut az automatikus regisztrálási feladat, ellenőrzi, hogy létezik-e a **MicrosoftIntuneEnrollPending** beállításkulcs, és megkísérli regisztrálni a célszámítógépet az Intune szolgáltatásban. Ha a regisztráció bármilyen okból nem sikerül, a rendszer ismét megkísérli a regisztrációt a feladat következő futtatásakor. A próbálkozások egy hónapon keresztül ismétlődnek.

    Ha a regisztráció sikeres, vagy ha letelik az egy hónap (amelyik előbb megtörténik), törlődik a célszámítógépről az automatikus Intune-regisztrálási feladat, a **WindowsIntuneEnrollPending** beállításkulcs és a fióktanúsítvány.

## <a name="instruct-users-to-self-enroll"></a>A felhasználók felkérése önálló regisztrálásra

Az Intune-ügyfélszoftver a [Céges portál webhelyen](https://portal.manage.microsoft.com) telepíthető. A felhasználók számára a webes portálon megjelenített pontos információ a fiók MDM-szolgáltatójától, illetve a felhasználó számítógépének operációsrendszer-platformjától és verziójától függően változik.

Ha a felhasználókhoz még nem rendeltek Intune-licencet, vagy ha a szervezet MDM-szolgáltatóját még nem állították be az Intune-ra, a felhasználóknak nem jelenik meg regisztrálási lehetőség.

Ha a felhasználókhoz hozzárendeltek Intune-licencet, és a szervezet MDM-szolgáltatóját beállították az Intune-ra:

- A Windows 7 és Windows 8 rendszereket használó felhasználóknak CSAK az a regisztrációs lehetőség jelenik meg, amelyben szervezetükre szabott egyedi ügyfélszoftvert kell letölteniük és telepíteniük.

- A Windows 10 és Windows 8.1 rendszereken két regisztrálási lehetőség jelenik meg:

  - **A számítógép regisztrálása mobileszközként**: A felhasználó a **Regisztráció menetének ismertetése** gombra kattintás után útmutatót olvashat a számítógép mobileszközként való regisztrálásáról. Ez a gomb kiemelt módon jelenik meg, mert az MDM-regisztráció az alapbeállítás és a javasolt regisztrációs módszer. Az MDM-regisztráció azonban nem része ennek a témakörnek, mert itt csak az ügyfélszoftver telepítését ismertetjük.
  - **Számítógép regisztrálása az Intune-ügyfélszoftver használatával**: Javasolt a felhasználókat tájékoztatni, hogy kattintsanak a **Letöltés ide kattintva** hivatkozásra, amely végigvezeti őket az ügyfélszoftver telepítésén.

Az alábbi táblázat a különböző lehetőségeket foglalja össze.

  ![Alapértelmezés szerinti regisztrálási lehetőségek platform szerint](./media/install-the-windows-pc-client-with-microsoft-intune/default-enrollment-options-table.png)

Az alábbi képernyőkép azt mutatja, amit a felhasználók láthatnak az ügyfélszoftver használatával történő eszközregisztrálás során.

A rendszer először felkéri a felhasználót, hogy azonosítsa vagy regisztrálja az eszközt.

  ![eszköz azonosítása vagy regisztrálása](./media/install-the-windows-pc-client-with-microsoft-intune/identify-device-or-enroll.png)

A PC-s ügyfélszoftver telepítésének érdekében érdemes a felhasználókat felkérni, hogy válasszák a **Letöltés ide kattintva** hivatkozást, amely lehetővé teszi a PC-s ügyfélszoftver letöltését, és végigvezeti a felhasználót a telepítési folyamaton. A **Regisztráció menetének ismertetése** gomb az MDM-regisztráció folyamatát ismertető dokumentációhoz vezet, amely azonban nem releváns az ügyfélszoftverrel kapcsolatos útmutatóhoz.

  ![válassza a Letöltés ide kattintva hivatkozást](./media/install-the-windows-pc-client-with-microsoft-intune/enroll-your-windows-device.png)

A hivatkozásra kattintva egy **Szoftver letöltése** gomb jelenik meg, amelynek kiválasztásával elindítható a PC-s ügyfélszoftver telepítése.

  ![válassza a Szoftver letöltése gombot](./media/install-the-windows-pc-client-with-microsoft-intune/download-pc-client-software.png)

Ezt követően a felhasználóknak be kell jelentkezniük a vállalati hitelesítő adataikkal.

  ![Bejelentkezés hitelesítő adatokkal](./media/install-the-windows-pc-client-with-microsoft-intune/sign-in-to-intune.png)

A felhasználó a telepítési folyamat Üdvözlő oldalára kerül.

  ![A PC-s ügyfél telepítésének Üdvözlő oldala](./media/install-the-windows-pc-client-with-microsoft-intune/welcome-to-pc-agent-install-wizard.png)

A **Következő** gomb kiválasztásával elindul a telepítés.

  ![A PC-s ügyfél telepítésének Üdvözlő oldala](./media/install-the-windows-pc-client-with-microsoft-intune/welcome-to-pc-agent-install-wizard.png)

A telepítés befejeztével a felhasználó a **Befejezés** gombot választja.

  ![A PC-s ügyfél telepítésének befejezése](./media/install-the-windows-pc-client-with-microsoft-intune/completed-the-setup-wizard.png)

Ha a felhasználó úgy próbálja mobileszközként regisztrálni a számítógépet, hogy az már korábban regisztrálva lett a PC-s Intune-ügyfélszoftverrel, akkor az alább látható hibaüzenetet kapja.

  ![A megjelenő képernyő, ha a számítógép már regisztrálva van](./media/install-the-windows-pc-client-with-microsoft-intune/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>A sikeres ügyféltelepítés figyelése és ellenőrzése
A következő eljárások egyikével figyelheti és ellenőrizheti az ügyfél sikeres telepítését.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>A kliensszoftver telepítésének ellenőrzése a Microsoft Intune felügyeleti konzolon

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Csoportok** &gt; **Minden eszköz** &gt; **Minden számítógép** lehetőségre.

2. A listában keresse meg az Intune szolgáltatással kommunikáló számítógépeket, vagy a **Keresés az eszközök között** mezőben megadva a számítógép nevét (vagy annak bármely részét) kereshet meg egy adott kezelt számítógépet.

3. Vizsgálja meg a számítógép állapotát a konzol alsó ablaktábláján. Hárítsa el az esetleges hibákat.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>Az összes regisztrált számítógépet megjelenítő számítógépkészlet-jelentés létrehozása

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Jelentések** &gt; **Számítógépleltár-jelentések** elemre.

2. Az **Új jelentés létrehozása** lapon az összes mezőben hagyja meg az alapértelmezett értéket (kivéve ha szűrőket kíván alkalmazni), majd kattintson a **Jelentés megtekintése**lehetőségre.

3. Ekkor egy új ablakban megjelenik a **Számítógépleltár-jelentés** lap, melyen az összes, az Intune szolgáltatásban sikeresen regisztrált számítógép látható.

    > [!TIP]
    > A jelentés bármely oszlopának fejlécére kattintva a lista az adott oszlop tartalma szerint rendezhető.

## <a name="uninstall-the-windows-client-software"></a>A Windows rendszerű ügyfélszoftver eltávolítása

Kétféle módon lehet törölni a Windows rendszerű ügyfélszoftver regisztrációját:

- Az Intune felügyeleti konzoljával (ajánlott módszer)
- Az ügyfélen parancssorral

### <a name="unenroll-by-using-the-intune-admin-console"></a>A regisztráció törlése az Intune felügyeleti konzoljával

Ha az ügyfélszoftver regisztrációjának törlését az Intune felügyeleti konzoljával végzi, válassza a **Csoportok** > **Minden számítógép** > **Eszközök** elemet. Kattintson a jobb gombbal az ügyfélre, és válassza a **Kivonás/törlés** elemet.

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>A regisztráció törlése az ügyfélen parancssorral

Rendszergazdai jogú parancssorból futtassa az alábbi parancsok egyikét.

**1. módszer:**

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**2. módszer** Lényeges, hogy minden ilyen ügynök telepítve van a Windows összes termékváltozatán:

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall
    wmic product where name="Microsoft Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall
    wmic product where name="Microsoft Policy Platform" call uninstall
    wmic product where name="Microsoft Security Client" call uninstall
    wmic product where name="Microsoft Online Management Client" call uninstall
    wmic product where name="Microsoft Online Management Client Service" call uninstall
    wmic product where name="Microsoft Easy Assist v2" call uninstall
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Microsoft Intune Center" call uninstall
    wmic product where name="Microsoft Online Management Update Manager" call uninstall
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall
    wmic product where name="Microsoft Intune" call uninstall
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall
    wmic product where name="Windows Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Windows Online Management Policy Agent" call uninstall
    wmic product where name="Windows Policy Platform" call uninstall
    wmic product where name="Windows Security Client" call uninstall
    wmic product where name="Windows Online Management Client" call uninstall
    wmic product where name="Windows Online Management Client Service" call uninstall
    wmic product where name="Windows Easy Assist v2" call uninstall
    wmic product where name="Windows Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Windows Intune Center" call uninstall
    wmic product where name="Windows Online Management Update Manager" call uninstall
    wmic product where name="Windows Online Management Agent Installer" call uninstall
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> Az ügyfél regisztrációjának törlése elavult kiszolgálóoldali rekordot hagy hátra az érintett ügyfélen. A regisztráció törlése aszinkron folyamat, és kilenc ügynök eltávolítására van szükség, így a művelet befejezése akár 30 percet is igénybe vehet.

### <a name="check-the-unenrollment-status"></a>A regisztráció törlési állapotának ellenőrzése

Ellenőrizze a %ProgramFiles%\Microsoft\OnlineManagement mappát, és győződjön meg arról, hogy csak az alábbi könyvtárak láthatóak a bal oldalon:

- Ügynöktelepítő
- Naplók
- Updates
- Közös

### <a name="remove-the-onlinemanagement-folder"></a>Az OnlineManagement nevű mappa eltávolítása

A regisztrációtörlési folyamat nem távolítja el az OnlineManagement nevű mappát. Várjon 30 percet az eltávolítás után, majd futtassa ezt a parancsot. Ha túl hamar futtatja, az eltávolítás ismeretlen állapotú maradhat. A mappa eltávolításához nyisson meg egy rendszergazdai jogú parancssort, majd futtassa a következő parancsot:

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

## <a name="next-steps"></a>További lépések
[A Windows rendszerű számítógépek Intune-szoftverügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
