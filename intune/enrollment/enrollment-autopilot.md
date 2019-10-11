---
title: Eszközök regisztrálása a Windows Autopilot használatával
titleSuffix: Microsoft Intune
description: Útmutató Windows 10-es eszközök regisztrálásához a Windows Autopilot használatával.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2ebca165c067afbc3d830e5f75ac9f8e29effb2
ms.sourcegitcommit: a50a1ca123ecc2c5ac129f112f73838748f56476
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/10/2019
ms.locfileid: "72237231"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Windows-eszközök regisztrálása az Intune-ban a Windows Autopilot használatával  
A Windows Autopilot leegyszerűsíti az eszközök regisztrálását az Intune-ban. Az egyéni operációsrendszer-lemezképek létrehozása és karbantartása időigényes folyamat. Az egyéni operációsrendszer-lemezképek új eszközökre való alkalmazásával időt is igénybe vehet, mielőtt a végfelhasználóknak adná őket. A Microsoft Intune és az Autopilot lehetővé teszi, hogy új eszközöket hozzon létre a végfelhasználók számára, anélkül, hogy egyéni operációsrendszer-lemezképeket kellene felépíteni, karbantartani és alkalmazni az eszközökre. Ha az Intune-t használja az Autopilot-eszközök kezeléséhez, a szabályzatokat, a profilokat, az alkalmazásokat és a regisztrációt követően is kezelheti. Az előnyök, forgatókönyvek és előfeltételek áttekintését lásd: [a Windows Autopilot áttekintése](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

A robotpilóta-telepítés négyféle típusú:
- [Saját üzembe helyezési mód](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) kioszkokhoz, digitális aláírásokhoz vagy megosztott eszközhöz
- A [fehér kesztyű](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) lehetővé teszi a partnerek vagy az informatikai munkatársak számára, hogy előzetesen kiépítsék a Windows 10 RENDSZERű számítógépeket, hogy teljesen konfigurálva legyenek, és készen álljanak a[meglévő eszközökre](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) , így egyszerűen üzembe helyezheti a Windows 10-es legújabb verzióját a meglévő eszközökön
- [Felhasználó által vezérelt mód](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) a hagyományos felhasználók számára. 


## <a name="prerequisites"></a>Előfeltételek
- [Intune-előfizetés](../fundamentals/licenses.md)
- [Automatikus Windows-regisztráció engedélyezve](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Előfizetés prémium szintű Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>A CSV-fájl beszerzése az Intune-ban történő importáláshoz

További információt a PowerShell-parancsmag ismertetése című témakörben talál.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Eszközök hozzáadása

A Windows Autopilot-eszközöket egy CSV-fájl importálásával adhatja hozzá az adataihoz.

1. Az [Intune-ban a Azure Portal válassza az](https://aka.ms/intuneportal)eszközök **beléptetése** > **Windows-regisztráció** > **eszközök** > **Importálás**lehetőséget.

    ![Képernyőfelvétel a Windows Autopilot-eszközökről](./media/enrollment-autopilot/autopilot-import-device.png)

2. A **Windows Autopilot-eszközök hozzáadása**területen tallózással keresse meg a hozzáadni kívánt eszközöket FELSOROLó CSV-fájlt. A CSV-fájlnak fel kell sorolnia a sorozatszámokat, a Windows-termékazonosítókat, a hardveres kivonatokat, a választható csoportok címkéit és a választható hozzárendelt felhasználót. A listában legfeljebb 500 sor lehet. Használja az alább látható fejlécet és sort:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Képernyőkép a Windows Autopilot-eszközök hozzáadásáról](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > Ha CSV-feltöltést használ egy felhasználó hozzárendeléséhez, akkor ügyeljen arra, hogy érvényes UPN-ket rendeljen hozzá. Ha érvénytelen UPN-t (helytelen felhasználónevet) rendel hozzá, előfordulhat, hogy az eszköz mindaddig nem érhető el, amíg el nem távolítja az érvénytelen hozzárendelést. A CSV-fájl feltöltésekor a **hozzárendelt felhasználó** oszlopban a csak az érvényesítést hajtjuk végre, hogy a tartománynév érvényes legyen. Nem lehet egyéni UPN-ellenőrzést végrehajtani, hogy egy meglévő vagy megfelelő felhasználót rendeljen hozzá.

3. Válassza az **Importálás** lehetőséget az eszköz adatainak importálásának megkezdéséhez. Az importálás több percet is igénybe vehet.

4. Az importálás befejezése után válassza az **eszközök beléptetése** > **windows-regisztráció** > **Windows**Autopilot  > **eszközök** > **szinkronizálás**lehetőséget. Egy üzenet jelenik meg, hogy a szinkronizálás folyamatban van. A folyamat több percig is eltarthat, attól függően, hogy hány eszközt szinkronizál a rendszer.

5. Frissítse a nézetet az új eszközök megjelenítéséhez.

## <a name="create-an-autopilot-device-group"></a>Autopilot-eszközcsoport létrehozása

1. Az [Intune-ban a Azure Portal válassza a](https://aka.ms/intuneportal) **csoportok** > **új csoport**lehetőséget.
2. A **csoport** panelen:
    1. A **csoport típusa**beállításnál válassza a **Biztonság**elemet.
    2. Adja meg a **csoport nevét** és a **csoport leírását**.
    3. A **tagság típusa**beállításnál válassza a **hozzárendelt** vagy a **dinamikus eszköz**lehetőséget.
3. Ha az előző lépésben a **tagsági típushoz** **rendelt** elemet választotta, akkor a **csoport** panelen válassza a **tagok** lehetőséget, és adja hozzá az Autopilot-eszközöket a csoporthoz.
    A még nem regisztrált Autopilot-eszközök olyan eszközök, amelyekben a név megegyezik az eszköz sorozatszámával.
4. Ha a fenti **tagsági típushoz** a **dinamikus eszközöket** választotta, akkor a **csoport** panelen válassza a **dinamikus eszközök tagjai** lehetőséget, és írja be a következő kód valamelyikét a **speciális szabály** mezőbe. Ezek a szabályok csak az Autopilot-eszközöket gyűjtik, mert azok az attribútumok, amelyek csak az Autopilot-eszközök által vannak kiértékelve.
    - Ha olyan csoportot szeretne létrehozni, amely tartalmazza az összes Autopilot-eszközt, írja be a következőt: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Az Intune csoport címkéje mezője az Azure AD-eszközök Rendeléskód attribútumára mutat. Ha olyan csoportot szeretne létrehozni, amely tartalmazza az összes Autopilot-eszközt egy adott csoport címkével (az Azure AD-eszköz Rendeléskód), a következőt kell beírnia: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Ha olyan csoportot szeretne létrehozni, amely tartalmazza az összes Autopilot-eszközt egy adott megrendelés-AZONOSÍTÓval, írja be a következőt: `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    A **speciális szabály** hozzáadása után válassza a **Mentés**lehetőséget.
5. Válassza a **Létrehozás** elemet.  

## <a name="create-an-autopilot-deployment-profile"></a>Autopilot Deployment-profil létrehozása
Az Autopilot-alapú üzembe helyezési profilok az Autopilot-eszközök konfigurálására szolgálnak.
1. Az [Intune-ban a Azure Portal válassza az](https://aka.ms/intuneportal) **eszközök beléptetése** > **Windows-regisztráció** > **telepítési profilok** > **Létrehozás profilt**.
2. Az **alapvető beállítások** lapon adja meg a **nevet** és a **leírást**(nem kötelező).

    ![Képernyőkép az alapok lapról](./media/enrollment-autopilot/create-profile-basics.png)

3. Ha azt szeretné, hogy a hozzárendelt csoportokban lévő összes eszköz automatikusan Autopilot-re legyen konvertálva, állítsa az **összes megrendelt eszköz konvertálása az Autopilot** értékre **Igen**értéket. A hozzárendelt csoportokban a vállalat tulajdonában lévő, nem Autopilot-eszközök regisztrálva lesznek az Autopilot Deployment szolgáltatásban. A személyes tulajdonban lévő eszközök nem lesznek átalakítva az Autopilot szolgáltatásba. 48 óra engedélyezése a regisztráció feldolgozásához. Az eszköz regisztrációjának törlése és alaphelyzetbe állítása után az Autopilot regisztrálja azt. Miután az eszköz regisztrálva lett, tiltsa le ezt a beállítást, vagy a profil hozzárendelésének eltávolításával nem távolítja el az eszközt az Autopilot Deployment szolgáltatásból. Ehelyett [közvetlenül el kell távolítania az eszközt](enrollment-autopilot.md#delete-autopilot-devices).
4. Kattintson a **Tovább** gombra.
5. Az **üzembe helyezési mód** **(OOBE)** lapon válassza az alábbi két lehetőség egyikét:
    - **Felhasználó által vezérelt**: a profillal rendelkező eszközök társítva vannak az eszközt regisztráló felhasználóhoz. Az eszköz regisztrálásához felhasználói hitelesítő adatokra van szükség.
    - **Öntelepítés (előzetes verzió)** : (a Windows 10 1809-es vagy újabb verziójára van szükség) ehhez a profilhoz tartozó eszközök nincsenek társítva az eszközt regisztrálni kívánó felhasználóhoz. A felhasználó hitelesítő adatai nem szükségesek az eszköz regisztrálásához. Ha egy eszközhöz nincs felhasználó társítva, a felhasználó-alapú megfelelőségi szabályzatok nem vonatkoznak rá. Öntelepítési mód használatakor a rendszer csak az eszközt célzó megfelelőségi szabályzatokat alkalmazza.

    ![Az OOBE oldalának képernyőképe](./media/enrollment-autopilot/create-profile-outofbox.png)

6. Az **illesztés az Azure ad** -ba mezőben válassza az **Azure ad-hez csatlakoztatott**lehetőséget.
7. Konfigurálja az alábbi beállításokat:
    - **Végfelhasználói licencszerződés (EULA)** : (Windows 10, 1709-es vagy újabb verzió) válassza ki, hogy meg szeretné-e jeleníteni a VÉGFELHASZNÁLÓi licencszerződést.
    - **Adatvédelmi beállítások**: válassza ki, hogy meg szeretné-e jeleníteni az adatvédelmi beállításokat a felhasználók számára.
    >[!IMPORTANT]
    >A diagnosztikai adatbeállítás alapértelmezett értéke a Windows-verziók között változik. A Windows 10 1903-es verzióját futtató eszközök esetében az alapértelmezett érték a teljes beépített élmény. További információ: [Windows diagnosztikai adatok](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - A **fiók beállításainak módosítása (Windows 10, 1809-es vagy újabb verzió szükséges)** : az **Elrejtés** beállítás megadásával megakadályozhatja a Fiókbeállítások megjelenítését a vállalati bejelentkezési és tartományi hibák oldalain. Ehhez a beállításhoz [a vállalat arculatának konfigurálására van szükség a Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Felhasználói fiók típusa**: válassza ki a felhasználó fiókjának típusát (**rendszergazda** vagy **normál** felhasználó). Lehetővé tesszük, hogy a felhasználó a helyi rendszergazda csoportba való felvételsel a helyi rendszergazdához csatlakozzon az eszközhöz. A felhasználó alapértelmezett rendszergazdaként nem engedélyezhető az eszközön.
    - A **White kesztyűs Oobe engedélyezése** (a Windows 10 1903-es vagy újabb verziójára van szükség; [További fizikai követelmények](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): válassza az **Igen** lehetőséget a fehér kesztyű támogatásának engedélyezéséhez.
    - Az **eszköz nevének sablonjának alkalmazása** (a Windows 10 1809-es vagy újabb verziójára, valamint az Azure ad JOIN típusra van szükség): válassza az **Igen** lehetőséget, ha az eszköznek a regisztráció során való elnevezéséhez használni szeretné a sablont. A névnek 15 karakternél rövidebbnek kell lennie, és betűket, számokat és kötőjeleket tartalmazhat. A nevek nem lehetnek számok. A [(z)% Serial% Macro](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) használatával adjon hozzá egy hardver-specifikus sorozatszámot. Vagy a [(z)% Rand: x% Macro](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) használatával véletlenszerű karakterláncot adhat hozzá, ahol az x egyenlő a hozzáadandó számjegyek számával. A [tartományhoz való csatlakozás profiljában](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile)csak a hibrid eszközök előzetes javítását lehet megadni. 
    - **Nyelv (régió)** \*: válassza ki az eszközhöz használni kívánt nyelvet. Ez a lehetőség csak akkor érhető el, **Ha az** üzembe helyezési **mód**beállítását választotta.
    - **Billentyűzet automatikus konfigurálása**\*: Ha egy **nyelv (régió)** van kiválasztva, válassza az **Igen** lehetőséget a billentyűzet kijelölési oldalának kihagyásához. Ez a lehetőség csak akkor érhető el, **Ha az** üzembe helyezési **mód**beállítását választotta.
8. Kattintson a **Tovább** gombra.
9. A **hatókör címkék** lapon adja meg a profilra alkalmazni kívánt hatókör-címkéket. A hatókör-címkékkel kapcsolatos további információkért lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).
10. Kattintson a **Tovább** gombra.
11. A **hozzárendelések** lapon válassza a **kijelölt csoportok** lehetőséget a **hozzárendeléshez**.

    ![Képernyőfelvétel a hozzárendelésekről lap](./media/enrollment-autopilot/create-profile-assignments.png)

12. Válassza ki a **felvenni kívánt csoportokat**, majd válassza ki azokat a csoportokat, amelyeket bele szeretne foglalni ebbe a profilba.
13. Ha ki szeretne zárni egy csoportot, válassza ki a **kizárni kívánt csoportokat**, majd válassza ki a kizárandó csoportokat.
14. Kattintson a **Tovább** gombra.
15. A profil létrehozásához a **felülvizsgálat + létrehozás** lapon válassza a **Létrehozás** lehetőséget.

    ![A felülvizsgálati oldal képernyőképe](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Az Intune rendszeresen ellenőrzi az új eszközöket a hozzárendelt csoportokban, majd megkezdi a profilok hozzárendelésének folyamatát az eszközökhöz. A folyamat végrehajtása több percet is igénybe vehet. Az eszköz telepítése előtt győződjön meg arról, hogy a folyamat befejeződött.  Az eszközök **beléptetése** > **Windows-regisztráció** > **eszköz** területen ellenőrizze, hogy a profil állapota "nincs hozzárendelve" értékről "hozzárendelés" értékűre, végül pedig a "hozzárendelt" értékre kerül-e.

## <a name="edit-an-autopilot-deployment-profile"></a>Autopilot Deployment-profil szerkesztése
Miután létrehozott egy Autopilot Deployment-profilt, szerkesztheti a telepítési profil egyes részeit.   

1. A [Azure Portal Intune-](https://aka.ms/intuneportal)ban válassza az **eszközök beléptetése**lehetőséget.
2. A **Windows-regisztráció**területen, a **Windows Autopilot** szakaszban válassza a **telepítési profilok**lehetőséget.
3. Válassza ki a szerkeszteni kívánt profilt.
4. Kattintson a bal oldali **Tulajdonságok** elemre a telepítési profil nevének vagy leírásának módosításához. A módosítások elvégzése után kattintson a **Mentés** gombra.
5. A **Beállítások** gombra kattintva módosíthatja az Oobe beállításait. A módosítások elvégzése után kattintson a **Mentés** gombra.

> [!NOTE]
> A profil módosításait a rendszer a profilhoz rendelt eszközökre alkalmazza. A frissített profilt azonban nem alkalmazza olyan eszközre, amely már regisztrálva van az Intune-ban az eszköz alaphelyzetbe állítása és újraregisztrálása után.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Riasztások a Windows Autopilot nem hozzárendelt eszközeihez  <!-- 163236 -->  

A riasztások azt mutatják be, hogy hány Autopilot program-eszközhöz nincs Autopilot-alapú üzembe helyezési profil. A riasztásban található információk segítségével profilok hozhatók létre, és hozzárendelhetők a hozzá nem rendelt eszközökhöz. Ha rákattint a riasztásra, megjelenik a Windows Autopilot-eszközök teljes listája, valamint a rájuk vonatkozó részletes információk.

A nem hozzárendelt eszközökre vonatkozó riasztások megtekintéséhez [a Azure Portal Intune-ban válassza az](https://aka.ms/intuneportal)eszközök **beléptetése**@no__t – 2**Áttekintés**@no__t – 4 nem**hozzárendelt eszközök**elemet.  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Felhasználó kiosztása egy adott Autopilot-eszközhöz

Hozzárendelhet egy felhasználót egy adott Autopilot-eszközhöz. Ez a hozzárendelés előzetesen kitölti a felhasználót a [vállalati védjeggyel](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) ellátott bejelentkezési oldalon Azure Active Directory a Windows telepítőben. Lehetővé teszi egyéni üdvözlési név megadását is. Nem tölti ki előre vagy nem módosítja a Windows-bejelentkezést. Ilyen módon csak az Intune-licenccel rendelkező felhasználók rendelhetők hozzá.

Előfeltételek: Azure Active Directory Céges portál konfigurálva van, és a Windows 10 1809-es vagy újabb verziójával.

1. A [Azure Portal Intune-ban](https://aka.ms/intuneportal)válassza az eszközök **beléptetése** > **Windows-regisztráció** > **eszközök** lehetőséget, > Válassza ki az eszközt > a **felhasználó kiosztása**elemet.

    ![Képernyőfelvétel a felhasználó hozzárendeléséről](./media/enrollment-autopilot/assign-user.png)

2. Válassza ki az Intune használatához licenccel rendelkező Azure-felhasználót, és válassza a **kiválasztás**lehetőséget.

    ![Képernyőfelvétel a felhasználó kiválasztásáról](./media/enrollment-autopilot/select-user.png)

3. A felhasználóbarát **név** mezőbe írjon be egy rövid nevet, vagy fogadja el az alapértelmezett értéket. Ez a karakterlánc a felhasználóbarát név, amely akkor jelenik meg, amikor a felhasználó bejelentkezik a Windows telepítőben.

    ![Képernyőkép – rövid név](./media/enrollment-autopilot/friendly-name.png)

4. Kattintson az **OK** gombra.


## <a name="delete-autopilot-devices"></a>Autopilot-eszközök törlése

Törölheti az Intune-ban nem regisztrált Windows Autopilot-eszközöket:

- Törölje az eszközöket a Windows Autopilot **eszközről az eszközök beléptetése** > **windows-regisztráció** > **eszközön**. Válassza ki a törölni kívánt eszközöket, majd válassza a **Törlés**lehetőséget. A Windows Autopilot-eszközök törlése néhány percet igénybe vehet.

Az eszköz bérlőből való teljes eltávolítása az Intune-eszköz, a Azure Active Directory eszköz és a Windows Autopilot-eszköz rekordjainak törlését igényli. Ezt az Intune-ból végezheti el:

1. Ha az eszközök regisztrálva vannak az Intune-ban, először [törölnie kell őket az Intune minden eszköz](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)paneljéről.

2. Azure Active Directory eszközökön lévő eszközök törlése az **eszközökön @no__t-** 1**Azure ad-eszközökön**.

3. Törölje az eszközöket a Windows Autopilot **eszközről az eszközök beléptetése** > **windows-regisztráció** > **eszközön**. Válassza ki a törölni kívánt eszközöket, majd válassza a **Törlés**lehetőséget. A Windows Autopilot-eszközök törlése néhány percet igénybe vehet.

## <a name="using-autopilot-in-other-portals"></a>Az Autopilot használata más portálokon
Ha nem érdekli a mobileszköz-kezelés, használhatja az Autopilot-t más portálokon. Ha más portálokat használ, javasoljuk, hogy csak az Intune-t használja az Autopilot-telepítések kezeléséhez. Ha az Intune-t és egy másik portált használ, az Intune nem tudja a következőket:  

- Az Intune-ban létrehozott profilok változásainak megjelenítése, de egy másik portálon szerkesztve
- Egy másik portálon létrehozott profilok szinkronizálása
- A profil-hozzárendelések más portálon végzett változásainak megjelenítése
- Profil-hozzárendelések szinkronizálása egy másik portálon
- Egy másik portálon végrehajtott eszközök listájának megjelenítése

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot a meglévő eszközökhöz

A Windows-eszközöket korrelátor-AZONOSÍTÓk szerint csoportosíthatja, ha [az Autopilot használatával regisztrálja a meglévő eszközöket](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) Configuration Manageron keresztül. A korrelátor azonosítója az Autopilot konfigurációs fájljának paramétere. Az [Azure ad Device attribútum enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) automatikusan egyenlő "OfflineAutopilotprofile-\<correlator ID @ no__t-2" értékre van állítva. Ez lehetővé teszi a tetszőleges Azure AD dinamikus csoportok létrehozását a korrelátor-azonosító alapján a enrollmentprofileName attribútum használatával.

>[!WARNING] 
> Mivel a korrelátor-azonosító nem szerepel az Intune-ban, az eszköz jelentést tehet a kívánt korrelátor-AZONOSÍTÓról. Ha a felhasználó létrehoz egy korrelátor-azonosítót, amely az Autopilot vagy az Apple DEP-profil nevét adja meg, az eszköz a enrollmentProfileName attribútum alapján a dinamikus Azure AD-eszközökhöz lesz hozzáadva. Az ütközés elkerüléséhez tegye a következőket:
> - Mindig hozzon létre a *teljes* enrollmentProfileName értékkel egyező dinamikus csoport szabályokat
> - Soha ne nevezze el az Autopilot vagy az Apple DEP-profilokat a "OfflineAutopilotprofile-" kifejezéssel kezdődően.

## <a name="next-steps"></a>Következő lépések
Miután konfigurálta a Windows Autopilot-t a regisztrált Windows 10-es eszközökhöz, Ismerje meg, hogyan kezelheti ezeket az eszközöket. További információ: [Mi az Microsoft Intune-eszközkezelés?](../remote-actions/device-management.md)
