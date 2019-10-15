---
title: iOS-eszközök beléptetése – Apple konfigurátor – beállítási asszisztens
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan regisztrálhat az Apple konfigurátorral a vállalat által birtokolt iOS-eszközöket a beállítási asszisztens segítségével.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1c2acc2ebe5528e30c344a31c9551ac64bdf3ca
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306784"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>IOS-eszközök regisztrálásának beállítása az Apple konfigurátorral

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune támogatja az iOS-eszközök regisztrálását a Mac számítógépen futó [Apple konfigurátor](https://itunes.apple.com/app/apple-configurator-2/id1037126344) használatával. Az Apple konfigurátor beléptetéséhez az szükséges, hogy az egyes iOS-eszközöket a vállalati regisztráció beállítása érdekében USB-kapcsolattal csatlakoztasson egy Mac számítógéphez. Az Apple konfigurátorral kétféleképpen regisztrálhat eszközöket az Intune-ba:
- A **beállítási asszisztens beléptetése** – törli az eszközt, és előkészíti a regisztrálást a beállítási asszisztens során.
- **Közvetlen regisztráció** – nem törli az eszközt, és az iOS-beállításokon keresztül regisztrálja az eszközt. Ez a metódus csak a **felhasználói affinitás nélküli**eszközöket támogatja.

Az Apple konfigurátor regisztrációs módszerei nem használhatók az [eszköz beléptetési kezelőjével](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Előfeltételek

- Fizikai hozzáférés iOS-eszközökhöz
- [MDM-szolgáltató beállítása](../fundamentals/mdm-authority-set.md)
- [Apple MDM push-tanúsítvány](apple-mdm-push-certificate-get.md)
- Eszköz sorozatszáma (csak a beállítási asszisztens regisztrációja)
- USB-kapcsolati kábelek
- [Apple konfigurátor 2,0](https://itunes.apple.com/app/apple-configurator-2/id1037126344) rendszert futtató MacOS rendszerű számítógép

## <a name="create-an-apple-configurator-profile-for-devices"></a>Apple konfigurátor-profil létrehozása az eszközökhöz

Egy eszköz beléptetési profil határozza meg a regisztráció során alkalmazott beállításokat. Ezeket a beállításokat csak egyszer alkalmazza a rendszer. Az alábbi lépéseket követve létrehozhat egy regisztrációs profilt az iOS-eszközök Apple konfigurátorral való regisztrálásához.

1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Apple-regisztráció** > **Apple konfigurátor** > **profilok** > **létrehozását**.

    ![Profil létrehozása az Apple konfigurátorhoz](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. A **beléptetési profil létrehozása**területen adja meg a profil **nevét** és **leírását** felügyeleti célból. A felhasználók nem látják ezeket az adatokat. A név mező használatával dinamikus csoportot hozhat létre Azure Active Directory. A profilnév használatával adja meg a enrollmentProfileName paramétert az ehhez a beléptetési profilhoz tartozó eszközök hozzárendeléséhez. További információ Azure Active Directory dinamikus csoportokról.

    ![A profil létrehozása képernyő képernyőképe a regisztráció felhasználói affinitással beállítással](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. A **felhasználói affinitás**beállításnál adja meg, hogy a profilt használó eszközök hozzárendelt felhasználóval vagy anélkül legyenek-e regisztrálva.

    - **Regisztrálás felhasználói affinitással** – válassza ezt a lehetőséget olyan eszközökhöz, amelyek felhasználókhoz tartoznak, és amelyek a vállalati portált szeretnék használni, például az alkalmazások telepítését. Az eszközt a beállítási asszisztenssel rendelkező felhasználóval kell összekapcsolni, és ezután hozzáférhet a vállalati adatszolgáltatásokhoz és e-mailekhez. Csak a beállítási asszisztens regisztrációja esetén támogatott. A felhasználói affinitáshoz a [ws-Trust 1,3 username/Mixed végpont](https://technet.microsoft.com/library/adfs2-help-endpoints)szükséges. [További információk](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Regisztráció felhasználói affinitás nélkül** – válassza ezt a lehetőséget olyan eszközök esetében, amelyek nem kapcsolódnak egyetlen felhasználóhoz. Használja ezt olyan eszközök esetében, amelyek a helyi felhasználói adatokhoz való hozzáférés nélkül végeznek feladatokat. A felhasználói kapcsolatot igénylő alkalmazások (beleértve az üzletági alkalmazások telepítéséhez használt Céges portál alkalmazást) nem fognak működni. A közvetlen regisztrációhoz szükséges.

     > [!NOTE]
     > Ha a **regisztráció felhasználói affinitással** beállítás be van jelölve, akkor győződjön meg arról, hogy az eszköz a regisztrált eszköz első 24 órájában egy, a beállítási asszisztenssel rendelkező felhasználóhoz kapcsolódik. Ellenkező esetben előfordulhat, hogy a regisztráció meghiúsul, és a gyári beállítások visszaállítására lesz szükség az eszköz regisztrálásához.

4. Ha a **regisztráció felhasználói affinitással**lehetőséget választotta, lehetősége van arra, hogy a felhasználók az Apple beállítási asszisztens helyett a céges portál hitelesítsék magukat.

    > [!NOTE]
    > Ha a következők valamelyikét szeretné elvégezni, állítsa be a **hitelesítést a céges portál az Apple beállítási asszisztens helyett** az **Igen**értékre.
    >    - többtényezős hitelesítés használata
    >    - azok a felhasználók, akiknek az első bejelentkezéskor módosítaniuk kell a jelszavukat
    >    - kérje meg a felhasználókat, hogy a regisztráció során visszaállítsák a lejárt jelszavukat
    >
    > Ezek nem támogatottak az Apple beállítási asszisztenssel való hitelesítéskor.


6. A profil mentéséhez válassza a **Létrehozás** lehetőséget.

## <a name="setup-assistant-enrollment"></a>A beállítási asszisztens regisztrációja

### <a name="add-apple-configurator-serial-numbers"></a>Apple konfigurátor sorozatszámok hozzáadása

1. Hozzon létre egy két oszlopból álló, vesszővel tagolt (. csv) listát fejléc nélkül. Adja hozzá a sorozatszámot a bal oldali oszlopban, valamint a jobb oldali oszlopban található részleteket. A lista jelenlegi maximális értéke 5 000 sor. Egy szövegszerkesztőben a. csv-lista így néz ki:

    F7TLWCLBX196, eszköz adatai</br>
    DLXQPCWVGHMJ, eszköz adatai

   Útmutató [az iOS-eszközök sorozatszámának megkereséséhez](https://support.apple.com/HT204073).
2. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Apple-regisztráció** > **Apple konfigurátor** > **eszközök** > **Hozzáadás**lehetőséget.

5. Válassza ki az importálandó sorozatszámokra alkalmazni kívánt **regisztrációs profilt** . Ha azt szeretné, hogy az új sorozatszám részletei felülírják a meglévő adatokat, válassza a **meglévő azonosítók adatainak felülírása**lehetőséget.
6. Az **eszközök importálása**területen keresse meg a sorozatszámok CSV-fájlját, és válassza a **Hozzáadás**lehetőséget.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Profil ismételt társítása az eszköz sorozatszámához

Ha iOS-sorozatszámokat importál az Apple konfigurátor-regisztrációhoz, hozzárendelhet egy regisztrációs profilt. A Azure Portal két helyről is hozzárendelhet profilokat:
- **Apple konfigurátor-eszközök**
- **AC-profilok**

#### <a name="assign-from-apple-configurator-devices"></a>Hozzárendelés Apple konfigurátor-eszközökről
1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Apple-regisztráció** > **Apple konfigurátor** > **eszközök** lehetőséget, > Válassza ki a sorozatszámokat > a **profil hozzárendelését**.
2. A **profil társítása**területen válassza ki a hozzárendelni kívánt **új profilt** , majd válassza a **hozzárendelés**lehetőséget.

#### <a name="assign-from-profiles"></a>Hozzárendelés profilokból
1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Apple-regisztráció** > **Apple konfigurátor** > **profilok** lehetőséget, > válasszon egy profilt.
2. A profilban válassza a **hozzárendelt eszközök**elemet, majd válassza a **hozzárendelés**lehetőséget.
3. A profilhoz hozzárendelni kívánt eszközök sorozatszámának megkereséséhez válassza ki az eszközöket, majd válassza a **hozzárendelés**lehetőséget.

### <a name="export-the-profile"></a>A profil exportálása
Miután létrehozta a profilt, és hozzárendelte a sorozatszámokat, URL-címként kell exportálnia a profilt az Intune-ból. Ezután importálhatja az Apple konfigurátorba egy Mac gépen az eszközökre való üzembe helyezéshez.

1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Apple-regisztráció** > **Apple konfigurátor** > **profilok** lehetőséget, > Válassza ki az exportálandó profilt.
2. A profilban válassza a **profil exportálása**lehetőséget.
3. Másolja a **profil URL-címét**. Ezután hozzáadhatja az Apple konfigurátorban az iOS-eszközök által használt Intune-profil meghatározásához.

   Ezután importálja ezt a profilt az Apple konfigurátorba az alábbi eljárással az iOS-eszközök által használt Intune-profil meghatározásához.

### <a name="enroll-devices-with-setup-assistant"></a>Eszközök regisztrálása a beállítási asszisztenssel

1. A Mac számítógépen nyissa meg az **Apple konfigurátor 2**eszközt. A menüsávban válassza az **Apple konfigurátor 2**elemet, majd válassza a **Beállítások**lehetőséget.
    > [!WARNING]
    > A beléptetési folyamat során az eszközök visszaállnak a gyári beállításokra. Az ajánlott eljárás szerint állítsa alaphelyzetbe az eszközt, és kapcsolja be. Az eszközöknek a **Hello** képernyőn kell lenniük az eszköz csatlakoztatásakor.
    > Ha az eszköz már regisztrálva van az Apple ID-fiókkal, az eszközt törölni kell az Apple iCloudból a beléptetési folyamat megkezdése előtt. A kérdéses hiba "nem sikerült aktiválni [eszköznév]" üzenet jelenik meg.

2. A **Beállítások** ablaktáblán válassza a **kiszolgálók** elemet, majd a Mdm-kiszolgáló varázsló elindításához válassza a plusz (+) szimbólumot. Kattintson a **Tovább** gombra.
3. Adja meg a MDM-kiszolgáló **állomásnevét vagy URL** -címét, valamint a **regisztrációs URL-címet** az iOS-eszközökhöz a Microsoft Intune használatával. A beléptetési URL-cím mezőbe írja be az Intune-ból exportált regisztrációs profil URL-címét. Kattintson a **Tovább** gombra.  
    Nyugodtan figyelmen kívül hagyhatja a "kiszolgáló URL-címének ellenőrzése" üzenetet. A folytatáshoz kattintson a **tovább** gombra, amíg a varázsló be nem fejeződik.
4. Az iOS rendszerű mobileszközök csatlakoztatása a Mac számítógéphez egy USB-adapterrel.
5. Válassza ki a kezelni kívánt iOS-eszközöket, majd válassza az **előkészítés**lehetőséget. Az **IOS-eszköz előkészítése** panelen válassza a **manuális**lehetőséget, majd kattintson a **tovább**gombra.
6. A **Mdm-kiszolgáló regisztrálása** ablaktáblán válassza ki a létrehozott kiszolgálónevet, majd válassza a **tovább**lehetőséget.
7. Az **eszközök felügyelete** ablaktáblán válassza ki a felügyelet szintjét, majd válassza a **tovább**lehetőséget.
8. A **szervezet létrehozása** panelen válassza ki a **szervezetet** , vagy hozzon létre egy új szervezetet, majd válassza a **tovább**lehetőséget.
9. Az **iOS beállítási asszisztens konfigurálása** panelen válassza ki a felhasználó számára megjeleníteni kívánt lépéseket, majd válassza az **előkészítés**lehetőséget. Ha a rendszer kéri, végezzen hitelesítést a megbízhatósági beállítások frissítéséhez.  
10. Az iOS-eszköz előkészítésének befejezésekor válassza le az USB-kábelt.  

### <a name="distribute-devices"></a>Eszközök terjesztése
Az eszközök most már készen állnak a vállalati regisztrációra. Kapcsolja ki az eszközöket, és terjessze azokat a felhasználók számára. Amikor a felhasználók bekapcsolják az eszközeiket, elindul a beállítási asszisztens.

Miután a felhasználók megkapják az eszközeiket, el kell végezniük a beállítási asszisztenst. A felhasználói affinitással konfigurált eszközökön telepítheti és futtathatja a Céges portál alkalmazást az alkalmazások letöltéséhez és az eszközök kezeléséhez.

## <a name="direct-enrollment"></a>Közvetlen regisztráció
Ha közvetlenül regisztrálja az iOS-eszközöket az Apple konfigurátorral, az eszköz sorozatszámának beszerzése nélkül regisztrálhat egy eszközt. Az eszközt az azonosításhoz is elnevezheti, mielőtt az Intune rögzíti az eszköz nevét a regisztráció során. A Céges portál alkalmazás nem támogatott a közvetlenül regisztrált eszközökön. Ez a metódus nem törli az eszközt.

A felhasználói kapcsolatot igénylő alkalmazások, beleértve az üzletági alkalmazások telepítéséhez használt Céges portál alkalmazást is, nem telepíthetők.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>A profil exportálása a. mobileconfig-ből iOS-eszközökre

1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Apple-regisztráció** > **Apple konfigurátor** > **profilok** lehetőséget, > válassza ki a profilt, amelybe exportálni szeretné > **exportálási profilt**.
2. A **közvetlen regisztráció**területen válassza a **profil letöltése**lehetőséget, és mentse a fájlt. A beléptetési profil fájlja csak két hétig érvényes, amikor újra létre kell hoznia.
3. Vigye át a fájlt egy [Apple konfigurátort](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) futtató Mac számítógépre, és közvetlenül felügyeleti profilként leküldheti az iOS-eszközökre.
4. Készítse elő az eszközt az Apple konfigurátorral az alábbi lépések segítségével:
    1. A Mac számítógépen nyissa meg az Apple konfigurátor 2,0 eszközt.
    2. Az iOS-eszköz csatlakoztatása a Mac számítógéphez USB-kábellel. A képek, az iTunes és más alkalmazások bezárásával megnyithatja az eszközt az eszköz észlelésekor.
    3. Az Apple konfigurátorban válassza ki a csatlakoztatott iOS-eszközt, majd kattintson a **Hozzáadás** gombra. Az eszközhöz adható beállítások a legördülő listában jelennek meg. Válassza a **profilok**lehetőséget.

        ![Képernyőkép-exportálási profil a beállítási asszisztens beléptetéséhez a profil URL-címének kiemelésével](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. A file Picker használatával válassza ki az Intune-ból exportált. mobileconfig fájlt, majd válassza a **Hozzáadás**lehetőséget. A profil hozzá lett adva az eszközhöz. Ha az eszköz nem felügyelt, akkor a telepítéshez el kell fogadniuk az eszközt.
5. A következő lépésekkel telepítheti a profilt az iOS-eszközön. Az eszköznek már el kell végeznie a beállítási Segédet, és használatra készen kell állnia. Ha a regisztráció az alkalmazás központi telepítését vonja maga után, az eszköznek rendelkeznie kell egy Apple ID azonosítóval, mert az alkalmazás központi telepítése megköveteli, hogy rendelkezzen egy Apple ID-vel, amely be van jelentkezve az App Store-ba.
    1. Az iOS-eszköz zárolásának feloldása.
    2. A **felügyeleti profil** **profil telepítése** párbeszédpanelén válassza a **telepítés**lehetőséget.
    3. Szükség esetén adja meg az eszköz PIN-kódját vagy az Apple ID azonosítót.
    4. Fogadja el a **figyelmeztetést**, és válassza a **telepítés**lehetőséget.
    5. Fogadja el a **távoli figyelmeztetést**, és válassza a **megbízhatóság**lehetőséget.
    6. Ha a **profil telepítve** mező megerősíti, hogy a profil telepítve van, válassza a **kész**lehetőséget.

6. Az iOS-eszközön nyissa meg a **Beállítások menüpontot** , és válassza az **általános** > **eszközkezelés** > **felügyeleti profilt**. Győződjön meg arról, hogy a profil telepítése fel van sorolva, és ellenőrizze az iOS-házirend korlátozásait és a telepített alkalmazásokat. A házirend-korlátozások és alkalmazások akár 10 percet is igénybe vehetnek az eszközön.

7. Eszközök terjesztése. Az iOS-eszköz most már regisztrálva van az Intune-ban és felügyelve.





