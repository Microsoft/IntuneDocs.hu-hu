---
title: "A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1bdcfa71aab0918fba1f59bd0782fc63eef6994e
ms.openlocfilehash: 723bef398338946e085e9d04d57a85b433ebc1c8


---

# A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal
Ezzel az útmutatóval beállíthatja a Windows rendszerű számítógépeinek a Microsoft Intune-ügyfélszoftverrel való kezelését.

## Előkészületek
Az Intune-ügyfélszoftver telepítésének megkezdése előtt olvassa el [A GPO- és Microsoft Intune-házirendek ütközéseinek feloldása](resolve-gpo-and-microsoft-intune-policy-conflicts.md) című témakört, melyből megtudhatja, milyen körülményeket kell biztosítani az ügyfél megfelelő telepítéséhez, majd térjen vissza ehhez az útmutatóhoz.

## Az ügyfél telepítése
Az alábbi lépésekkel telepítheti be az ügyfelet:

-   [Az ügyfélszoftver letöltése](#to-download-the-client-software)

Ezután az alábbi módszerek közül egy vagy több alkalmazásával telepítheti az ügyfelet:

-   [Az ügyfélszoftver manuális telepítése](#to-manually-deploy-the-client-software)

-   [Az ügyfélszoftver automatikus telepítése a Csoportházirenddel](#to-automatically-deploy-the-client-software-by-using-group-policy)

-   [Számítógépek önálló regisztrálása a felhasználók által](#how-users-can-self-enroll-their-computers)

-   [A Microsoft Intune-ügyfélszoftver telepítése rendszerkép részeként](#install-the-microsoft-intune-client-software-as-part-of-an-image)

Ha már nincs szüksége egy számítógépnek az Intune szolgáltatással való kezelésére, kivonhatja a számítógépet. Ezzel egyben az ügyfélszoftvert is eltávolítja a számítógépről. További információ: [A Windows rendszerű számítógépek a Microsoft Intune számítógépügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

### Az ügyfélszoftver letöltése

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Felügyelet** &gt; **Ügyfélszoftver letöltése** lehetőségre.

  ![Az Intune-számítógépügyfél letöltése](./media/pc-SA-client-download.png)

2.  Az **Ügyfélszoftver letöltése** lapon kattintson az **Ügyfélszoftver letöltése** lehetőségre, majd mentse a szoftvert tartalmazó **Microsoft_Intune_Setup.zip** csomagot egy biztonságos helyre a hálózaton.

    > [!NOTE]
    > A Intune ügyfélszoftverének telepítőcsomagja tartalmazza a fiókja adatait. Ha jogosulatlan felhasználók férnek hozzá a telepítőcsomaghoz, a beágyazott tanúsítvány által jelölt fiókhoz regisztrálhatnak számítógépeket.

3.  Bontsa ki a telepítőcsomag tartalmát a biztonságos helyre a hálózaton.

    > [!IMPORTANT]
    > Ne nevezze át vagy távolítsa el a kibontott **ACCOUNTCERT** fájlt, különben az ügyfélszoftver telepítése sikertelen lesz.

### Az ügyfélszoftver manuális telepítése

1.  Az adott számítógépen keresse meg az ügyfélszoftver telepítési fájljait tartalmazó mappát, és futtassa a **Microsoft_Intune_Setup.exe** fájlt az ügyfélszoftver telepítéséhez.

    > [!NOTE]
    > A telepítés állapota akkor jelenik meg, ha az ügyfélszámítógép tálcáján megjelenő ikonra mutat.

### Az ügyfélszoftver automatikus telepítése a Csoportházirenddel

1.  A **Microsoft_Intune_Setup.exe** és a **MicrosoftIntune.accountcert** fájlt tartalmazó mappában futtassa a következő parancsot a 32 bites és 64 bites számítógépekhez készült Windows Installer-alapú telepítőprogramok kibontásához:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Másolja a **Microsoft_Intune_x86.msi** fájlt, a **Microsoft_Intune_x64.msi** fájlt és a **MicrosoftIntune.accountcert** fájlt egy olyan hálózati helyre, amely minden olyan számítógép számára elérhető, amelyre telepíteni kívánja az ügyfélszoftvert.

    > [!IMPORTANT]
    > A fájlokat ne válassza szét vagy nevezze át, különben az ügyfélszoftver telepítése sikertelen lesz.

3.  A Csoportházirenddel telepítse a szoftvert a hálózaton lévő számítógépekre.

    A Csoportházirend szoftverek automatikus telepítésére való használatával kapcsolatban a Windows Server dokumentációjában találhat további információkat.

### Számítógépek önálló regisztrálása a felhasználók által
A felhasználók saját maguk is regisztrálhatják számítógépeiket a munkahelyi Intune-portálon. Minden regisztrált számítógép ahhoz a felhasználói fiókhoz lesz kapcsolva, amellyel telepítették az ügyfélszoftvert.

> [!NOTE]
> -   Az ügyfélszoftver telepítéséhez a felhasználónak rendszergazdának kell lennie a számítógépen.
> -   Az önálló regisztráláshoz az Internet Explorer böngészőnek telepítve kell lennie az ügyfélszámítógépen.
> -   Minden alkalommal, amikor a felhasználó önállóan regisztrál egy számítógépet, felhasznál egy Intune-licencet.
> -   A számítógépek önálló regisztrálásához egy munkahelyi vagy iskolai fiókot kell használni. Microsoft-fiókkal nem lehet önállóan regisztrálni számítógépeket.
> -   Ha az ügyfélszoftver már telepítve van a számítógépen, a végfelhasználó egy hibaüzenetet fog kapni.

### Számítógépek önálló regisztrálása (tájékoztatás végfelhasználók számára)

1.  Jelentkezzen be a vállalati portálra a regisztrálni kívánt számítógépről.

2.  Kattintson az **Eszköz hozzáadása**lehetőségre.

3.  Kattintson a **Szoftver letöltése** , majd a **Futtatás**lehetőségre.

4.  A **Tovább** gombra kattintva indítsa el a Microsoft Intune telepítővarázslóját.

5.  A telepítő varázsló befejeződésekor kattintson a **Befejezés**gombra.

### A Microsoft Intune-ügyfélszoftver telepítése rendszerkép részeként
Az Intune ügyfélszoftverét az alábbi példaeljárás alapján egy operációsrendszer-kép részeként is telepítheti a számítógépekre:

1.  Az ügyfél telepítési fájljait, a **Microsoft_Intune_Setup.exe** és a **MicrosoftIntune.accountcert** fájlt másolja a **%Systemdrive%\Temp\Microsoft_Intune_Setup** mappába a referencia-számítógépen.

2.  Hozzon létre egy **WindowsIntuneEnrollPending** nevű bejegyzést a beállításjegyzékben a következő parancs hozzáadásával a **SetupComplete.cmd** parancsfájlhoz:

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  A következő parancs a **setupcomplete.cmd** parancsfájlhoz való hozzáadásával futtassa a regisztrációs csomagot a /PrepareEnroll parancssori argumentummal:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > A **SetupComplete.cmd** parancsfájl lehetővé teszi, hogy a Windows telepítő módosításokat végezzen a rendszeren egy felhasználó bejelentkezése előtt. A **/PrepareEnroll** parancssori argumentum előkészíti a célzott számítógépet a Windows telepítő befejeződése után az Intune-ban való automatikus regisztráláshoz.

4.  Helyezze a **SetupComplete.cmd** fájlt a **%Windir%\Setup\Scripts** mappába a referencia-számítógépen.

5.  Rögzítsen egy rendszerképet a referencia-számítógépről, majd telepítse azt a célként megadott számítógépekre.

Amikor a célszámítógép a Windows telepítő befejezése után újraindul, létrejön a **WindowsIntuneEnrollPending** beállításkulcs. A regisztrálási csomag ellenőrzi, hogy regisztrálva van-e a számítógép. Ha a számítógép regisztrálva van, nem szükséges további művelet. Ha a számítógép nincs regisztrálva, a regisztrálási csomag létrehoz egy automatikus Microsoft Intune-regisztrálási feladatot.

Amikor a következő ütemezett időpontban lefut az automatikus regisztrálási feladat, ellenőrzi, hogy létezik-e a **MicrosoftIntuneEnrollPending** beállításkulcs, és megkísérli regisztrálni a célszámítógépet az Intune szolgáltatásban. Ha a regisztráció bármilyen okból nem sikerül, a rendszer ismét megkísérli a regisztrációt a feladat következő futtatásakor. A próbálkozások egy hónapon keresztül ismétlődnek.

Ha a regisztráció sikeres, vagy ha letelik az egy hónap, törlődik a célszámítógépről az automatikus Intune-regisztrálási feladat, a **WindowsIntuneEnrollPending** beállításkulcs és a fióktanúsítvány.

## A sikeres ügyféltelepítés figyelése és ellenőrzése 
A következő eljárások egyikével figyelheti és ellenőrizheti az ügyfél sikeres telepítését.

### A kliensszoftver telepítésének ellenőrzése a Microsoft Intune felügyeleti konzolon

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Csoportok** &gt; **Minden eszköz** &gt; **Minden számítógép** lehetőségre.

2.  A számítógépek listáját görgetve keresheti meg az Intune szolgáltatással kommunikáló kezelt számítógépeket, vagy a **Keresés az eszközök között** mezőben megadva a számítógép nevét (vagy annak bármely részét) kereshet meg egy adott kezelt számítógépet.

3.  Vizsgálja meg a számítógép állapotát a konzol alsó ablaktábláján, és hárítsa el a hibákat, ha vannak.

### Az összes regisztrált számítógépet megjelenítő számítógépkészlet-jelentés létrehozása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Jelentések** &gt; **Számítógépleltár-jelentések** elemre.

2.  Az **Új jelentés létrehozása** lapon az összes mezőben hagyja meg az alapértelmezett értéket (kivéve ha szűrőket kíván alkalmazni), majd kattintson a **Jelentés megtekintése**lehetőségre.

3.  Ekkor egy új ablakban megjelenik a **Számítógépleltár-jelentés** lap, melyen az összes, az Intune szolgáltatásban sikeresen regisztrált számítógép látható.

    > [!TIP]
    > A jelentés bármely oszlopának fejlécére kattintva a lista az adott oszlop tartalma szerint rendezhető.


### Lásd még:
[Windows rendszerű számítógépek felügyelete a Microsoft Intune-nal](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


