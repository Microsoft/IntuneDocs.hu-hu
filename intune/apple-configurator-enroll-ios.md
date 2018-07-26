---
title: iOS-eszközök regisztrálása – az Apple Configurator és a Beállítási asszisztens
titleSuffix: Microsoft Intune
description: Útmutató a céges iOS-eszközöknek az Apple Configurator és a Beállítási asszisztens használatával való regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b3965c651bb6fcc38d61a55208fc8b199223891
ms.sourcegitcommit: 5251a630fb2c7a2e6f86abd84ab887f8eabc1481
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2018
ms.locfileid: "39212120"
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>iOS-eszközök regisztrálása az Apple Configurator használatával

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az Intune támogatja az iOS-eszközöknek a Mac számítógépen futó [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) segítségével történő regisztrálását. A céges regisztrálás Apple Configuratorral való beállításához az adott iOS-eszközt USB-csatlakozóval kell csatlakoztatni egy Mac számítógéphez. Az Apple Configurator használatával kétféle módon lehet regisztrálni az eszközt az Intune-ban:
- **Regisztráció a Beállítási asszisztenssel** – Visszaállítja a gyári beállításokat az eszközön, és felkészíti azt a Beállítási asszisztenssel történő regisztrálásra.
- **Közvetlen regisztrálás** – Ez a folyamat nem állítja vissza az eszközön a gyári beállításokat, és az iOS-beállításokon keresztül regisztrálja azt. Ez a módszer csak a **felhasználói affinitás nélküli** eszközöket támogatja.

Az Apple Configurator regisztrációs módszerei nem használhatók az [eszközregisztráció-kezelővel](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Előfeltételek

- Fizikai hozzáférés iOS-eszközökhöz
- [MDM-szolgáltató beállítása](mdm-authority-set.md)
- [Apple MDM Push-tanúsítvány](apple-mdm-push-certificate-get.md)
- Az eszközök sorozatszámai (csak a Beállítási asszisztenssel történő regisztrálás esetén)
- USB csatlakozókábelek
- [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344) alkalmazást futtató macOS-számítógép

## <a name="create-an-apple-configurator-profile-for-devices"></a>Apple Configurator-profil létrehozása az eszközökhöz

Egy eszközregisztrációs profil meghatározza a regisztrálás során alkalmazott beállításokat. Ezek a beállítások csak egyszer kerülnek alkalmazásra. Az iOS-eszközöknek az Apple Configuratorral történő regisztrációjához használt regisztrációs profil létrehozásához kövesse az alábbi lépéseket.

1. Az [Intune](https://aka.ms/intuneportal) portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Apple Configurator** > **Profilok** > **Létrehozás** lehetőséget.

    ![Apple Configurator-profil létrehozása](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. A **Regisztrációs profil létrehozása** panelen adminisztrációs célból adja meg a profil **Nevét** és **Leírását**. Ezeket a felhasználók nem fogják látni. A Név mező felhasználásával dinamikus csoportot hozhat létre az Azure Active Directoryban. Használja a profilnevet az enrollmentProfileName paraméter meghatározásához, hogy ezt a regisztrációs profilt rendelhesse hozzá az eszközökhöz. További információk az Azure Active Directory-alapú dinamikus csoportokról.

    ![Képernyőkép a profil létrehozásáról, a felhasználói affinitással történő regisztrálás választásával](./media/apple-configurator-profile-create.png)

3. A **Felhasználói affinitást** aszerint állítsa be, hogy a profilhoz tartozó eszközöket hozzárendelt felhasználóval vagy anélkül szükséges-e regisztrálni.

    - **Regisztráció felhasználói affinitással** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek a felhasználók tulajdonában vannak, de egyes szolgáltatásokhoz, például alkalmazások telepítéséhez, a céges portált kívánják használni. Az eszközt a Beállítási asszisztens használatával össze kell kapcsolni egy felhasználóval, hogy elérhesse a céges adatokat és e-maileket. Csak a Beállítási asszisztens segítségével végzett regisztrációhoz támogatott. A felhasználói affinitáshoz [WS-Trust 1.3 Username/Mixed végpont](https://technet.microsoft.com/library/adfs2-help-endpoints) szükséges. [További információ](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

   > [!NOTE]
   > A többtényezős hitelesítés (MFA) nem működik a felhasználói affinitással beállított regisztráció során. A regisztráció végeztével az MFA az elvárásoknak megfelelően működik. Az első bejelentkezéskor az eszközök nem tudják figyelmeztetni a felhasználókat a jelszó módosítására. Továbbá a lejárt jelszóval rendelkező felhasználók sem kapnak felszólítást a jelszó alaphelyzetbe állítására a regisztráció alatt. A felhasználóknak egy másik eszköz használatával kell alaphelyzetbe állítani a jelszavukat.

    - **Regisztráció felhasználói affinitás nélkül** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek nincsenek egy adott felhasználóhoz társítva. Olyan eszközökhöz használja, amelyek a helyi felhasználói adatokhoz való hozzáférés nélkül végeznek feladatokat. A felhasználói kapcsolatot igénylő alkalmazások, az üzletági alkalmazások telepítéséhez használt Munkahelyi portál alkalmazást is beleértve, nem fognak működni. Közvetlen regisztrálás esetén kötelező.

4. A **Regisztráció felhasználói affinitással** lehetőség választásakor engedélyezheti a felhasználóknak, hogy az Apple beállítási asszisztens helyett a Céges portál alkalmazással végezzenek hitelesítést.

6. Válassza a **Létrehozás** elemet a profil mentéséhez.

## <a name="setup-assistant-enrollment"></a>Regisztrálás a Beállítási asszisztenssel

### <a name="add-apple-configurator-serial-numbers"></a>Apple Configurator-sorozatszámok hozzáadása

1. Hozzon létre egy vesszővel elválasztott, kétoszlopos, fejléc nélküli értéklistát (.csv-fájlt). A bal oldali oszlopban tüntesse fel a sorozatszámot, a jobb oldali oszlopban pedig a további adatokat. A lista jelenlegi maximális mérete 5000 sor. Szövegszerkesztőben a .csv-fájl az alábbihoz hasonlóan jelenik meg:

    F7TLWCLBX196,eszköz adatai</br>
    DLXQPCWVGHMJ,eszköz adatai

   Ismerje meg, [hogyan találhatja meg egy iOS-eszköz sorozatszámát](https://support.apple.com/HT204073).
2. Az [Intune](https://aka.ms/intuneportal) portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Apple Configurator** > **Eszközök** > **Hozzáadás** lehetőséget.

5. Válassza ki az importált sorozatszámokhoz hozzáadandó **regisztrációs profilt**. Ha azt szeretné, hogy az új sorozatszámadatok felülírják az esetlegesen már meglévő adatokat, válassza a **Meglévő azonosítók adatainak felülírása** lehetőséget.
6. Az **Eszközök importálása** területen keresse meg a sorozatszámokat tartalmazó .csv-fájlt, és válassza a **Hozzáadás** lehetőséget.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Profil újbóli hozzárendelése eszközök sorozatszámaihoz

Az Apple Configurator-regisztrációhoz szükséges iOS-sorozatszámokhoz azok importálása során hozzárendelhet egy regisztrációs profilt. Emellett az Azure Portalban két helyen is elvégezheti a profilok hozzárendelését:
- **Apple Configurator-eszközök**
- **AC-profilok**

#### <a name="assign-from-apple-configurator-devices"></a>Hozzárendelés az Apple Configurator-eszközök panelről
1. Az [Intune](https://aka.ms/intuneportal) portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Apple Configurator** > **Eszközök** lehetőséget, válassza ki a sorozatszámokat, majd válassza a **Profil hozzárendelése** lehetőséget.
2. A **Profil hozzárendelése** területen válassza az **Új profil**, majd a **Hozzárendelés** lehetőséget.

#### <a name="assign-from-profiles"></a>Hozzárendelés a profilok közül
1. Az [Intune](https://aka.ms/intuneportal) portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Apple Configurator** > **Profilok** lehetőséget, majd válasszon egy profilt.
2. A profilban válassza a **Hozzárendelt eszközök**, majd a **Hozzárendelés** lehetőséget.
3. Keresse meg a profilhoz hozzárendelni kívánt eszközök sorozatszámait a szűrő segítségével, válassza ki az eszközöket, majd válassza a **Hozzárendelés** lehetőséget.

### <a name="export-the-profile"></a>Profil exportálása
Miután létrehozta a profilt és hozzárendelte a sorozatszámokat, egy URL-címként exportálnia kell a profilt az Intune-ból. Ezt követően az eszközökön történő telepítéshez importálja ezt a profilt az Apple Configuratorban egy Mac számítógépen.

1. Az [Intune](https://aka.ms/intuneportal) portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Apple Configurator** > **Profilok** lehetőséget, majd válassza az exportálni kívánt profilt.
2. A profilban válassza a **Profil exportálása** lehetőséget.
3. Másolja a **profil URL-címét** a vágólapra. A címet ezután hozzáadhatja az Apple Configuratorban az iOS-eszközök által használt Intune-profil meghatározásához.

   Ezt követően importálja ezt a profilt az Apple Configuratorban az alábbi eljárással, hogy meghatározza az iOS-eszközök által használt Intune-profilt.

### <a name="enroll-devices-with-setup-assistant"></a>Eszközök regisztrálása a Beállítási asszisztenssel

1. A Mac-számítógépen nyissa meg az **Apple Configurator 2** eszközt. A menüsávban válassza az **Apple Configurator 2**, majd a **Beállítások** elemet.
    > [!WARNING]
    > A regisztrációs folyamat során az eszközök visszaállnak a gyári beállításokra. Az ajánlott eljárás szerint állítsa alaphelyzetbe az eszközt, és kapcsolja be. Az eszközön az **üdvözlőképernyőnek** kell látszania az eszköz csatlakoztatásakor.

2. Válassza a **Beállítások** panelen a **Servers** (Kiszolgálók) elemet, majd az MDM-kiszolgálói varázsló elindításához válassza a „+” szimbólumot. Kattintson a **Tovább** gombra.
3. Írja be a Beállítási asszisztens segítségével a Microsoft Intune-ban történő iOS-eszközregisztrációhoz megadott MDM-kiszolgáló **állomásnevét vagy URL-címét** (Host name or URL) és **regisztrációs URL-címét** (Enrollment URL) a megfelelő mezőkbe. Az Enrollment URL (Regisztrációs URL-cím) mezőnél az Intune-ból exportált regisztrációs profil URL-címét adja meg. Kattintson a **Tovább** gombra.  
    Ha a rendszer figyelmezteti, hogy nincs ellenőrizve a kiszolgáló URL-címe, nyugodtan figyelmen kívül hagyhatja. Kattintson minden megjelenő oldalon a **Next** (Tovább) gombra, amíg be nem fejeződik a varázsló.
4.  Az iOS-mobileszközöket csatlakoztassa a Mac számítógéphez egy USB-adapterrel.
5.  Jelölje ki a kezelni kívánt iOS-eszközöket, majd válassza az **Előkészítés** lehetőséget. A **Prepare iOS Device** (iOS-eszköz előkészítése) panelen válassza a **Manual** (Manuális) elemet, majd a **Next** (Tovább) gombot.
6. Az **Enroll in MDM Server** (Regisztrálás MDM-kiszolgálón) panelen válassza ki a létrehozott kiszolgáló nevét, majd válassza a **Next** (Tovább) gombot.
7. A **Supervise Devices** (Eszközök felügyelete) panelen válassza ki a felügyelet szintjét, majd válassza a **Next** (Tovább) gombot.
8. A **Create an Organization** (Szervezet létrehozása) panelen válassza ki a szervezetet az **Organization** mezőben, vagy hozzon létre új szervezetet, majd válassza a **Next** gombot.
9. A **Configure iOS Setup Assistant** (iOS-es Beállítási asszisztens konfigurálása) panelen válassza ki a felhasználó számára megjelenő lépéseket, majd válassza a **Prepare** (Előkészítés) gombot. Ha a rendszer kéri, végezzen hitelesítést a megbízhatósági beállítások frissítése érdekében.  
10. Az iOS-eszköz előkészítésének befejezésekor válassza le az USB-kábelt.  

### <a name="distribute-devices"></a>Eszközök terjesztése
Az eszközök most már készen állnak a vállalati regisztrációra. Kapcsolja ki az eszközöket, és ossza ki őket a felhasználóknak. Amikor a felhasználók bekapcsolják az eszközüket, elindul a Beállítási asszisztens.

Miután a felhasználók megkapják az eszközeiket, el kell végezniük a Beállítási asszisztens lépéseit. A felhasználói affinitással konfigurált eszközökön telepítheti és futtathatja a Vállalati portál alkalmazást az alkalmazások letöltéséhez és az eszközök kezeléséhez.

## <a name="direct-enrollment"></a>Közvetlen regisztráció
Amikor közvetlenül regisztrál iOS-eszközöket az Apple Configurator használatával, anélkül regisztrálhat egy eszközt, hogy lekérné annak sorozatszámát. Az eszközt el is nevezheti azonosítási célból, mielőtt az Intune rögzítené az eszköz nevét a regisztráció alatt. A Céges portál alkalmazás nem támogatott a közvetlen módon regisztrált eszközökön. A művelethez nincs szükség a gyári beállítások visszaállítására.

Nem telepíthetők a felhasználói kapcsolatot igénylő alkalmazások, többek között az üzletági alkalmazások telepítéséhez használt Céges portál alkalmazás sem.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>A profil exportálása iOS-eszközökre .mobileconfig fájlként

1. Az [Intune](https://aka.ms/intuneportal) portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Apple Configurator** > **Profilok** lehetőséget, válassza ki az exportálni kívánt profilt, majd válassza a **Profil exportálása** lehetőséget.
2. A **Közvetlen regisztrálás** területen válassza a **Profil letöltése** lehetőséget, és mentse a fájlt. A regisztrációs profilok csak két hétig érvényesek, ez után újra létre kell hozni őket.
3. Ha a profilt közvetlenül az iOS-eszközökre szeretné telepíteni felügyeleti profilként, helyezze át a fájlt egy [Apple Configuratort](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) futtató Mac gépre.
4. Készítse elő az eszközt az Apple Configuratorral az alábbi lépések segítségével:
    1. Egy Mac számítógépen nyissa meg az Apple Configurator 2.0 eszközt.
    2. Csatlakoztassa az iOS-eszközt a Mac számítógéphez egy USB-kábellel. Zárja be a Fotók, az iTunes és más alkalmazásokat, amelyek megnyílnak az eszközhöz annak észlelésekor.
    3. Az Apple Configuratorban válassza ki a csatlakoztatott iOS-eszközt, majd kattintson az **Add** (Hozzáadás) gombra. Az eszközhöz adható lehetőségek a legördülő listában jelennek meg. Válassza a **Profilok** lehetőséget.

        ![Képernyőkép a Beállítási asszisztenssel történő regisztrációs folyamat Profil exportálása parancsáról, a profil kiemelt URL-címével](./media/ios-apple-configurator-add-profile.png)

    4. A fájlkiválasztóval válassza ki az Intune-ból exportált .mobileconfig fájlt, majd válassza az **Add** (Hozzáadás) gombot. Ezzel a profil hozzá lesz adva az eszközhöz. Ha az eszköz Felügyeletlen, a telepítést el kell fogadni az eszközön.
5. Az alábbi lépések segítségével telepítse a profilt az iOS-eszközön. Az eszköz elvileg elvégezte a Beállítási asszisztens lépéseit, és készen áll a használatra. Ha a regisztrációba alkalmazástelepítések tartoznak, az eszközhöz be kell állítani egy Apple ID azonosítót, mert az alkalmazástelepítéshez ezzel kell bejelentkezni az Apple Store áruházba.
    1. Oldja fel az iOS-eszköz zárolását.
    2. A **Felügyeleti profil** **Profil telepítése** párbeszédpanelén kattintson a **Telepítés** gombra.
    3. Ha szükséges, adja meg az eszköz PIN-kódját vagy az Apple ID azonosítót.
    4. Fogadja el a **Figyelmeztetést**, és válassza a **Telepítés** gombot.
    5. Fogadja el a **Távoli figyelmeztetést**, és válassza a **Megbízható** gombot.
    6. Amikor a **Profil telepítve** mező megerősíti, hogy a profil Telepítve van, válassza a **Kész** gombot.

6. Az iOS-eszközön nyissa meg a **Beállítások** alkalmazást, majd válassza az **Általános** > **Eszközkezelés** > **Felügyeleti profil** lehetőséget. Ellenőrizze, hogy a profiltelepítés szerepel-e a listán, valamint ellenőrizze az iOS-házirend korlátozásait és a telepített alkalmazásokat. A házirend-korlátozások és alkalmazások megjelenítése az eszközön akár 10 percet is igénybe vehet.

7. Eszközök terjesztése. Az iOS-eszköz most már felügyelt, és regisztrálva van az Intune-ban.





