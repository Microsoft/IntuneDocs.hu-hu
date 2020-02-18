---
title: iOS/iPadOS-eszközök beléptetése – Apple konfigurátor – beállítási asszisztens
titleSuffix: Microsoft Intune
description: Ismerje meg, hogy az Apple konfigurátor használatával hogyan regisztrálhat a vállalat által birtokolt iOS/iPadOS eszközöket a beállítási asszisztenssel.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ccd41b6ebc9bdf62c1603e508cb881a1be62ee7
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415403"
---
# <a name="set-up-iosipados-device-enrollment-with-apple-configurator"></a>IOS-/iPadOS-eszközök regisztrációjának beállítása az Apple konfigurátorral

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune támogatja az iOS/iPadOS-eszközök regisztrálását a Mac számítógépeken futó [Apple konfigurátor](https://itunes.apple.com/app/apple-configurator-2/id1037126344) használatával. Az Apple konfigurátorban való regisztráláshoz az szükséges, hogy a vállalati regisztráció beállításához USB-csatlakozást csatlakoztasson minden iOS/iPadOS-eszközhöz egy Mac számítógéphez. Az Apple Configurator használatával kétféle módon lehet regisztrálni az eszközt az Intune-ban:
- **Regisztráció a Beállítási asszisztenssel** – Törli az eszköz összes adatát, és felkészíti azt a Beállítási asszisztenssel történő regisztrálásra.
- **Közvetlen regisztráció** – nem törli az eszközt, és az iOS/iPadOS beállításokon keresztül regisztrálja az eszközt. Ez a módszer csak a **felhasználói affinitás nélküli** eszközöket támogatja.

Az Apple Configurator regisztrációs módszerei nem használhatók az [eszközregisztráció-kezelővel](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Előfeltételek

- Fizikai hozzáférés iOS-/iPadOS-eszközökhöz
- [MDM-szolgáltató beállítása](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push-tanúsítvány](apple-mdm-push-certificate-get.md)
- Az eszközök sorozatszámai (csak a Beállítási asszisztenssel történő regisztrálás esetén)
- USB csatlakozókábelek
- [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344) alkalmazást futtató macOS-számítógép

## <a name="create-an-apple-configurator-profile-for-devices"></a>Apple Configurator-profil létrehozása az eszközökhöz

Egy eszközregisztrációs profil meghatározza a regisztrálás során alkalmazott beállításokat. Ezek a beállítások csak egyszer kerülnek alkalmazásra. Az alábbi lépéseket követve létrehozhat egy regisztrációs profilt az iOS/iPadOS-eszközök Apple konfigurátorral való regisztrálásához.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **Apple konfigurátor** > **profilok** > **Létrehozás**lehetőséget.

    ![Apple Configurator-profil létrehozása](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. A **Regisztrációs profil létrehozása** panelen adminisztrációs célból adja meg a profil **Nevét** és **Leírását**. Ezeket a felhasználók nem fogják látni. A Név mező felhasználásával dinamikus csoportot hozhat létre az Azure Active Directoryban. Használja a profilnevet az enrollmentProfileName paraméter meghatározásához, hogy ezt a regisztrációs profilt rendelhesse hozzá az eszközökhöz. További információk az Azure Active Directory-alapú dinamikus csoportokról.

    ![Képernyőkép a profil létrehozásáról, a felhasználói affinitással történő regisztrálás választásával](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. A **Felhasználói affinitást** aszerint állítsa be, hogy a profilhoz tartozó eszközöket hozzárendelt felhasználóval vagy anélkül szükséges-e regisztrálni.

    - **Regisztráció felhasználói affinitással** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek a felhasználók tulajdonában vannak, de egyes szolgáltatásokhoz, például alkalmazások telepítéséhez, a céges portált kívánják használni. Az eszközt a Beállítási asszisztens használatával össze kell kapcsolni egy felhasználóval, hogy elérhesse a céges adatokat és e-maileket. Csak a Beállítási asszisztens segítségével végzett regisztrációhoz támogatott. A felhasználói affinitáshoz [WS-Trust 1.3 Username/Mixed végpont](https://technet.microsoft.com/library/adfs2-help-endpoints) szükséges. [További információk](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Regisztráció felhasználói affinitás nélkül** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek nincsenek egy adott felhasználóhoz társítva. Olyan eszközökhöz használja, amelyek a helyi felhasználói adatokhoz való hozzáférés nélkül végeznek feladatokat. A felhasználói kapcsolatot igénylő alkalmazások, az üzletági alkalmazások telepítéséhez használt Munkahelyi portál alkalmazást is beleértve, nem fognak működni. Közvetlen regisztrálás esetén kötelező.

     > [!NOTE]
     > Ha a **regisztráció felhasználói affinitással** beállítás be van jelölve, akkor győződjön meg arról, hogy az eszköz a regisztrált eszköz első 24 órájában egy, a beállítási asszisztenssel rendelkező felhasználóhoz kapcsolódik. Ellenkező esetben előfordulhat, hogy a regisztráció meghiúsul, és a gyári beállítások visszaállítására lesz szükség az eszköz regisztrálásához.

4. A **Regisztráció felhasználói affinitással** lehetőség választásakor engedélyezheti a felhasználóknak, hogy az Apple beállítási asszisztens helyett a Céges portál alkalmazással végezzenek hitelesítést.

    > [!NOTE]
    > Ha az alábbiak valamelyikét szeretné elvégezni, állítsa a **Hitelesítés a Céges portállal a Beállítási asszisztens helyett** értékét az **Igen** lehetőségre.
    >    - Többtényezős hitelesítés használata
    >    - A felhasználók figyelmeztetése a jelszó módosítására az első bejelentkezéskor
    >    - A felhasználók figyelmeztetése a lejárt jelszó helyetti új jelszó kérésére a regisztráció során
    >
    > Ezek az Apple Beállítási asszisztenssel végzett hitelesítéskor nem támogatottak.


6. Válassza a **Létrehozás** elemet a profil mentéséhez.

## <a name="setup-assistant-enrollment"></a>Regisztrálás a Beállítási asszisztenssel

### <a name="add-apple-configurator-serial-numbers"></a>Apple Configurator-sorozatszámok hozzáadása

1. Hozzon létre egy vesszővel elválasztott, kétoszlopos, fejléc nélküli értéklistát (.csv-fájlt). A bal oldali oszlopban tüntesse fel a sorozatszámot, a jobb oldali oszlopban pedig a további adatokat. A lista jelenlegi maximális mérete 5000 sor. Szövegszerkesztőben a .csv-fájl az alábbihoz hasonlóan jelenik meg:

    F7TLWCLBX196,eszköz adatai</br>
    DLXQPCWVGHMJ,eszköz adatai

   Megtudhatja [, hogyan találhatja meg az iOS/iPadOS eszköz sorozatszámát](https://support.apple.com/HT204073).
2. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **Apple konfigurátor** > **eszközök** > **Hozzáadás**lehetőséget.

5. Válassza ki az importált sorozatszámokhoz hozzáadandó **regisztrációs profilt**. Ha azt szeretné, hogy az új sorozatszámadatok felülírják az esetlegesen már meglévő adatokat, válassza a **Meglévő azonosítók adatainak felülírása** lehetőséget.
6. Az **Eszközök importálása** területen keresse meg a sorozatszámokat tartalmazó .csv-fájlt, és válassza a **Hozzáadás** lehetőséget.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Profil újbóli hozzárendelése eszközök sorozatszámaihoz

Ha iOS/iPadOS-sorozatszámokat importál az Apple konfigurátor-regisztrációhoz, akkor hozzárendelhet egy regisztrációs profilt. Emellett az Azure Portalban két helyen is elvégezheti a profilok hozzárendelését:
- **Apple Configurator-eszközök**
- **AC-profilok**

#### <a name="assign-from-apple-configurator-devices"></a>Hozzárendelés az Apple Configurator-eszközök panelről
1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **Apple konfigurátor** > **eszközök** > Válassza ki a sorozatszámokat > a **profil hozzárendelését**.
2. A **Profil hozzárendelése** területen válassza az **Új profil**, majd a **Hozzárendelés** lehetőséget.

#### <a name="assign-from-profiles"></a>Hozzárendelés a profilok közül
1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **Apple konfigurátor** > - **profilok** lehetőséget, > válasszon egy profilt.
2. A profilban válassza a **Hozzárendelt eszközök**, majd a **Hozzárendelés** lehetőséget.
3. Keresse meg a profilhoz hozzárendelni kívánt eszközök sorozatszámait a szűrő segítségével, válassza ki az eszközöket, majd válassza a **Hozzárendelés** lehetőséget.

### <a name="export-the-profile"></a>Profil exportálása
Miután létrehozta a profilt és hozzárendelte a sorozatszámokat, egy URL-címként exportálnia kell a profilt az Intune-ból. Ezt követően az eszközökön történő telepítéshez importálja ezt a profilt az Apple Configuratorban egy Mac számítógépen.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **Apple konfigurátor** > - **profilok** lehetőséget, > Válassza ki az exportálandó profilt.
2. A profilban válassza a **Profil exportálása** lehetőséget.
3. Másolja a **profil URL-címét** a vágólapra. Ezután hozzáadhatja az Apple konfigurátorban az iOS/iPadOS-eszközök által használt Intune-profil meghatározásához.

   Ezután importálja ezt a profilt az Apple konfigurátorba az alábbi eljárással az iOS/iPadOS-eszközök által használt Intune-profil meghatározásához.

### <a name="enroll-devices-with-setup-assistant"></a>Eszközök regisztrálása a Beállítási asszisztenssel

1. A Mac-számítógépen nyissa meg az **Apple Configurator 2** eszközt. A menüsávban válassza az **Apple Configurator 2**, majd a **Beállítások** elemet.
    > [!WARNING]
    > A regisztrációs folyamat során az eszközök visszaállnak a gyári beállításokra. Az ajánlott eljárás szerint állítsa alaphelyzetbe az eszközt, és kapcsolja be. Az eszközön az **üdvözlőképernyőnek** kell látszania az eszköz csatlakoztatásakor.
    > Ha az eszköz már regisztrálva van az Apple ID-fiókkal, az eszközt törölni kell az Apple iCloudból a beléptetési folyamat megkezdése előtt. A kérdéses hiba "nem sikerült aktiválni [eszköznév]" üzenet jelenik meg.

2. Válassza a **Beállítások** panelen a **Servers** (Kiszolgálók) elemet, majd az MDM-kiszolgálói varázsló elindításához válassza a „+” szimbólumot. Kattintson a **Tovább** gombra.
3. Adja meg a MDM-kiszolgáló **állomásnevét vagy URL** -címét, valamint a **BEléptetési URL-címet** az iOS-vagy iPadOS-eszközökhöz a Microsoft Intune használatával. Az Enrollment URL (Regisztrációs URL-cím) mezőnél az Intune-ból exportált regisztrációs profil URL-címét adja meg. Kattintson a **Tovább** gombra.  
    Ha a rendszer figyelmezteti, hogy nincs ellenőrizve a kiszolgáló URL-címe, nyugodtan figyelmen kívül hagyhatja. Kattintson minden megjelenő oldalon a **Next** (Tovább) gombra, amíg be nem fejeződik a varázsló.
4. Az iOS-/iPadOS-mobileszközök csatlakoztatása a Mac számítógéphez USB-adapterrel.
5. Válassza ki a kezelni kívánt iOS-/iPadOS-eszközöket, majd válassza az **előkészítés**lehetőséget. Az **iOS/iPadOS-eszköz előkészítése** panelen válassza a **manuális**lehetőséget, majd kattintson a **tovább**gombra.
6. Az **Enroll in MDM Server** (Regisztrálás MDM-kiszolgálón) panelen válassza ki a létrehozott kiszolgáló nevét, majd válassza a **Next** (Tovább) gombot.
7. A **Supervise Devices** (Eszközök felügyelete) panelen válassza ki a felügyelet szintjét, majd válassza a **Next** (Tovább) gombot.
8. A **Create an Organization** (Szervezet létrehozása) panelen válassza ki a szervezetet az **Organization** mezőben, vagy hozzon létre új szervezetet, majd válassza a **Next** gombot.
9. Az **iOS/iPadOS beállítása segéd** panelen válassza ki a felhasználó számára megjeleníteni kívánt lépéseket, majd válassza az **előkészítés**lehetőséget. Ha a rendszer kéri, végezzen hitelesítést a megbízhatósági beállítások frissítése érdekében.  
10. Amikor az iOS/iPadOS-eszköz befejezi az előkészítést, válassza le az USB-kábelt.  

### <a name="distribute-devices"></a>Eszközök terjesztése
Az eszközök most már készen állnak a vállalati regisztrációra. Kapcsolja ki az eszközöket, és ossza ki őket a felhasználóknak. Amikor a felhasználók bekapcsolják az eszközüket, elindul a Beállítási asszisztens.

Miután a felhasználók megkapják az eszközeiket, el kell végezniük a Beállítási asszisztens lépéseit. A felhasználói affinitással konfigurált eszközökön telepítheti és futtathatja a Vállalati portál alkalmazást az alkalmazások letöltéséhez és az eszközök kezeléséhez.

## <a name="direct-enrollment"></a>Közvetlen regisztráció
Ha közvetlenül regisztrálja az iOS/iPadOS-eszközöket az Apple konfigurátorral, az eszköz sorozatszámának beszerzése nélkül regisztrálhat egy eszközt. Az eszközt el is nevezheti azonosítási célból, mielőtt az Intune rögzítené az eszköz nevét a regisztráció alatt. A Céges portál alkalmazás nem támogatott a közvetlen módon regisztrált eszközökön. Ez a módszer nem törli az eszköz összes adatát.

Nem telepíthetők a felhasználói kapcsolatot igénylő alkalmazások, többek között az üzletági alkalmazások telepítéséhez használt Céges portál alkalmazás sem.

### <a name="export-the-profile-as-mobileconfig-to-iosipados-devices"></a>A profil exportálása a. mobileconfig-ből iOS-/iPadOS-eszközökre

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **Apple konfigurátor** > **profilok** lehetőséget, > Válassza ki a profilt > **exportálási profil**exportálásához.
2. A **Közvetlen regisztrálás** területen válassza a **Profil letöltése** lehetőséget, és mentse a fájlt. A regisztrációs profilok csak két hétig érvényesek, ez után újra létre kell hozni őket.
3. Vigye át a fájlt egy [Apple konfigurátort](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) futtató Mac számítógépre, és közvetlenül felügyeleti profilként leküldheti az iOS/iPadOS-eszközökre.
4. Készítse elő az eszközt az Apple Configuratorral az alábbi lépések segítségével:
    1. Egy Mac számítógépen nyissa meg az Apple Configurator 2.0 eszközt.
    2. Az iOS/iPadOS eszköz csatlakoztatása a Mac számítógéphez USB-kábellel. Zárja be a Fotók, az iTunes és más alkalmazásokat, amelyek megnyílnak az eszközhöz annak észlelésekor.
    3. Az Apple konfigurátorban válassza ki a csatlakoztatott iOS/iPadOS eszközt, majd kattintson a **Hozzáadás** gombra. Az eszközhöz adható lehetőségek a legördülő listában jelennek meg. Válassza a **Profilok** lehetőséget.

        ![Képernyőkép a Beállítási asszisztenssel történő regisztrációs folyamat Profil exportálása parancsáról, a profil kiemelt URL-címével](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. A fájlkiválasztóval válassza ki az Intune-ból exportált .mobileconfig fájlt, majd válassza az **Add** (Hozzáadás) gombot. Ezzel a profil hozzá lesz adva az eszközhöz. Ha az eszköz Felügyeletlen, a telepítést el kell fogadni az eszközön.
5. A következő lépésekkel telepítheti a profilt az iOS/iPadOS eszközön. Az eszköz elvileg elvégezte a Beállítási asszisztens lépéseit, és készen áll a használatra. Ha a regisztrációba alkalmazástelepítések tartoznak, az eszközhöz be kell állítani egy Apple ID azonosítót, mert az alkalmazástelepítéshez ezzel kell bejelentkezni az Apple Store áruházba.
    1. Az iOS-/iPadOS-eszköz zárolásának feloldása.
    2. A **Felügyeleti profil** **Profil telepítése** párbeszédpanelén kattintson a **Telepítés** gombra.
    3. Ha szükséges, adja meg az eszköz PIN-kódját vagy az Apple ID azonosítót.
    4. Fogadja el a **Figyelmeztetést**, és válassza a **Telepítés** gombot.
    5. Fogadja el a **Távoli figyelmeztetést**, és válassza a **Megbízható** gombot.
    6. Amikor a **Profil telepítve** mező megerősíti, hogy a profil Telepítve van, válassza a **Kész** gombot.

6. Az iOS/iPadOS eszközön nyissa meg a **beállításokat** , és lépjen az **általános** > **eszközkezelés** > **felügyeleti profil**elemre. Győződjön meg arról, hogy a profil telepítése fel van sorolva, és ellenőrizze az iOS/iPadOS házirend korlátozásait és a telepített alkalmazásokat. A házirend-korlátozások és alkalmazások megjelenítése az eszközön akár 10 percet is igénybe vehet.

7. Eszközök terjesztése. Az iOS-/iPadOS-eszköz most már regisztrálva van az Intune-ban és felügyelve.





