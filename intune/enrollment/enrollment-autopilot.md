---
title: Eszközök regisztrálása a Windows AutoPilot használatával
titleSuffix: Microsoft Intune
description: Útmutató a Windows 10-eszközök Windows AutoPilot használatával történő regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 499a1fa468193a5be2da05a62568301f4f23aaf4
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260265"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Windows-eszközök regisztrálása az Intune-ban a Windows Autopilot használatával  
A Windows Autopilot egyszerűbbé teszi az eszközök regisztrálását az Intune-ban. A testre szabott operációsrendszer-lemezképek létrehozása és karbantartása sok időt vesz igénybe. Gyakran ezeknek az egyéni operációsrendszer-lemezképeknek az új eszközökre való alkalmazásával is időt kell töltenie, hogy felkészítse az eszközöket a használatra, mielőtt a végfelhasználóknak adná azokat. A Microsoft Intune és az AutoPilot révén új eszközöket adhat hozzá a végfelhasználók számára anélkül, hogy egyéni operációsrendszer-lemezképek létrehozására, kezelésére és az eszközökre való alkalmazására lenne szükség. Az AutoPilot-eszközök Intune-nal való felügyelete során a regisztráció után szabályzatokat, profilokat, alkalmazásokat és sok mást is kezelni tud. A megoldás előnyeinek, használati eseteinek és előfeltételeinek áttekintéséről lásd [a Windows AutoPilot áttekintését](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

A robotpilóta-telepítés négyféle típusú:
- [Saját üzembe helyezési mód](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) kioszkokhoz, digitális aláírásokhoz vagy megosztott eszközhöz
- A [fehér kesztyű](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) lehetővé teszi a partnerek vagy az informatikai munkatársak számára a Windows 10 rendszerű számítógépek előzetes kiépítését, hogy az teljes mértékben konfigurálva legyen, és készen álljon az üzleti használatra
- A [meglévő eszközökhöz készült Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) lehetővé teszi a Windows 10 legújabb verziójának egyszerű telepítését a meglévő eszközökre
- [Felhasználó által vezérelt mód](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) a hagyományos felhasználók számára. 

## <a name="prerequisites"></a>Előfeltételek
- [Intune-előfizetés](../fundamentals/licenses.md)
- [Engedélyezni kell a Windowsos eszközök automatikus regisztrációját](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Előfizetés prémium szintű Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>A CSV-fájl beszerzése az Intune-ban történő importáláshoz

További információt a PowerShell-parancsmag ismertetése című témakörben talál.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Eszközök felvétele

A Windows AutoPilot-eszközök felvételéhez importálhat egy CSV-fájlt az adataikkal.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **Windows** > **Windows-beléptetési** > **eszközök** elemet (a **Windows Autopilot Deployment program** > **Importálás**lehetőséget.

    ![A Windows AutoPilot-eszközök képernyőképe](./media/enrollment-autopilot/autopilot-import-device.png)

2. A **Windows AutoPilot-eszközök hozzáadása** alatt keresse meg a hozzáadni kívánt eszközöket felsoroló CSV-fájlt. A CSV-fájlnak fel kell sorolnia a sorozatszámokat, a Windows-termékazonosítókat, a hardveres kivonatokat, a választható csoportok címkéit és a választható hozzárendelt felhasználót. A listában legfeljebb 500 sor lehet. További információ az eszköz információinak beszerzéséről: [eszközök hozzáadása a Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/add-devices#device-identification)szolgáltatáshoz. Használja az alább látható fejlécet és sort:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![A Windows AutoPilot-eszközök hozzáadásának képernyőképe](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > Ha CSV-feltöltést használ egy felhasználó hozzárendeléséhez, akkor ügyeljen arra, hogy érvényes UPN-ket rendeljen hozzá. Ha érvénytelen UPN-t (helytelen felhasználónevet) rendel hozzá, előfordulhat, hogy az eszköz mindaddig nem érhető el, amíg el nem távolítja az érvénytelen hozzárendelést. A CSV-fájl feltöltésekor a **hozzárendelt felhasználó** oszlopban a csak az érvényesítést hajtjuk végre, hogy a tartománynév érvényes legyen. Nem lehet egyéni UPN-ellenőrzést végrehajtani, hogy egy meglévő vagy megfelelő felhasználót rendeljen hozzá.

3. Válassza az **Importálás** lehetőséget az eszközadatok importálásának elindításához. Az importálás több percig is eltarthat.

4. Az importálás befejezése után válassza az **eszközök** > **Windows** > **windows-beléptetési** > **eszközök** lehetőséget (a **Windows Autopilot Deployment program** > **Sync**elemnél. Egy üzenet jelenik meg, hogy a szinkronizálás folyamatban van. Nagyszámú eszköz szinkronizálása esetén előfordulhat, hogy várnia kell pár percet, amíg a folyamat befejeződik.

5. Frissítse a nézetet az új eszközök megjelenítéséhez.

## <a name="create-an-autopilot-device-group"></a>AutoPilot-eszközcsoport létrehozása

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza a **csoportok** > **új csoport**lehetőséget.
2. A **Csoport** panelen:
    1. A **Csoport típusa** beállításnál válassza a **Biztonsági** lehetőséget.
    2. Gépelje be a **Csoport nevét** és a **Csoport leírását**.
    3. A **Tagság típusa** beállításnál válassza a **Hozzárendelt** vagy a **Dinamikus eszköz** lehetőséget.
3. Ha a **Tagság típusa** beállításnál az előző lépésben a **Hozzárendelt** értéket választotta, akkor válassza a **Csoport** panel **Tagok** elemét, és adjon hozzá AutoPilot-eszközöket a csoporthoz.
    A még nem regisztrált AutoPilot-eszközök olyan eszközök, amelyek neve megegyezik az eszköz sorozatszámával.
4. Ha a **Tagság típusa** alatt a **Dinamikus eszköz** lehetőséget választotta, akkor válassza a **Csoport** panel **Dinamikus eszköz tagok** lehetőségét, és gépelje be az alábbi kódok bármelyikét a **Speciális szabály** mezőbe. Ezek a szabályok csak az Autopilot-eszközöket gyűjtik, mert azok az attribútumok, amelyek csak az Autopilot-eszközök által vannak kiértékelve. A nem robotpilóta-attribútumok alapján létrehozott csoportok nem garantálják, hogy a csoportba tartozó eszközök ténylegesen regisztrálva vannak az Autopilot-ban.
    - Ha olyan csoportot szeretne létrehozni, amely tartalmazza az összes Autopilot-eszközt, írja be a következőt: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Az Intune csoport címkéje mezője az Azure AD-eszközök Rendeléskód attribútumára mutat. Ha olyan csoportot szeretne létrehozni, amely tartalmazza az összes Autopilot-eszközt egy adott csoport címkével (az Azure AD-eszköz Rendeléskód), a következőt kell beírnia: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Ha létre kíván hozni egy csoportot egy adott beszerzési rendelési azonosítóval rendelkező összes Autopilot-eszközből, írja be a következőt: `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
    A **Speciális szabály** kódjának megadása után válassza a **Mentés** lehetőséget.
5. Válassza a **Létrehozás** lehetőséget.  

## <a name="create-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil létrehozása
Az Autopilot-üzembehelyezési profilokkal Autopilot-eszközeit konfigurálhatja. A bérlők számára legfeljebb 350 profilt hozhat létre.
1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **windows** > **windows-regisztráció** > **központi telepítési profilok** > **profil létrehozása**lehetőséget.
2. Az **alapvető beállítások** lapon adja meg a **nevet** és a **leírást**(nem kötelező).

    ![Képernyőkép az alapok lapról](./media/enrollment-autopilot/create-profile-basics.png)

3. Ha azt szeretné, hogy a hozzárendelt csoportokban lévő minden eszköz automatikusan átálljon az AutoPilotra, állítsa a **Minden megcélzott eszköz AutoPilot-eszközzé alakítása** beállítást **Igen** értékre. A hozzárendelt csoportokban a vállalat tulajdonában lévő, nem Autopilot-eszközök regisztrálva lesznek az Autopilot Deployment szolgáltatásban. A személyes tulajdonban lévő eszközök nem lesznek átalakítva az Autopilot szolgáltatásba. Hagyjon 48 órát a regisztráció feldolgozására. Az eszköz regisztrációjának törlése és alaphelyzetbe állítása után az Autopilot regisztrálja az eszközt. Miután ilyen módon regisztrál egy eszközt, a beállítás letiltása vagy a profil-hozzárendelés eltávolítása nem távolítja el az eszközt az Autopilot üzembehelyezési szolgáltatásból. Ehhez [közvetlenül kell törölnie az eszközt](enrollment-autopilot.md#delete-autopilot-devices).
4. Válassza a **Tovább** elemet.
5. Az **üzembe helyezési mód** **(OOBE)** lapon válassza az alábbi két lehetőség egyikét:
    - **Felhasználó-alapú**: Az ilyen profillal rendelkező eszközök az őket regisztráló felhasználóhoz vannak társítva. Az eszköz regisztrálásához felhasználói hitelesítő adatokra van szükség.
    - **Öntelepítés (előzetes verzió)** : (a Windows 10 1809-es vagy újabb verziójára van szükség) ehhez a profilhoz tartozó eszközök nincsenek társítva az eszközt regisztrálni kívánó felhasználóhoz. Az eszköz telepítéséhez nincs szükség felhasználói hitelesítő adatokra. Ha egy eszközhöz nincs felhasználó társítva, a felhasználó-alapú megfelelőségi szabályzatok nem vonatkoznak rá. Öntelepítési mód használatakor a rendszer csak az eszközt célzó megfelelőségi szabályzatokat alkalmazza.

    ![Az OOBE oldalának képernyőképe](./media/enrollment-autopilot/create-profile-outofbox.png)

   > [!NOTE]
   > A halványan vagy árnyékolt színnel megjelenő beállításokat a rendszer jelenleg nem támogatja a kiválasztott központi telepítési módban.

6. A **Csatlakozás az Azure AD-hez mint** mezőben válassza az **Azure AD-hez csatlakoztatott** lehetőséget.
7. Adja meg az alábbi lehetőségeket:
    - **Végfelhasználói licencszerződés (EULA)** : (Windows 10, 1709-es vagy újabb verzió) Eldöntheti, hogy a felhasználók számára megjelenjen-e a végfelhasználói licencszerződés.
    - **Adatvédelmi beállítások**: Eldöntheti, hogy a felhasználók számára megjelenjenek-e az adatvédelmi beállítások.
    >[!IMPORTANT]
    >A diagnosztikai adatbeállítás alapértelmezett értéke a Windows-verziók között változik. A Windows 10 1903-es verzióját futtató eszközök esetében az alapértelmezett érték a teljes beépített élmény. További információ: [Windows diagnosztikai adatok](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - A **fiók beállításainak módosítása (Windows 10, 1809-es vagy újabb verzió szükséges)** : az **Elrejtés** beállítás megadásával megakadályozhatja a Fiókbeállítások megjelenítését a vállalati bejelentkezési és tartományi hibák oldalain. Ez a beállítás megköveteli, hogy [az Azure Active Directoryban konfigurálva legyen a Vállalati védjegyezés](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Felhasználói fiók típusa**: Válassza ki a felhasználói fiók típusát (**Rendszergazda** vagy **Normál**). Lehetővé tesszük, hogy a felhasználó a helyi rendszergazda csoportba való felvételsel a helyi rendszergazdához csatlakozzon az eszközhöz. A felhasználó alapértelmezett rendszergazdaként nem engedélyezhető az eszközön.
    - A **White kesztyűs Oobe engedélyezése** (a Windows 10 1903-es vagy újabb verziójára van szükség; [További fizikai követelmények](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): válassza az **Igen** lehetőséget a fehér kesztyű támogatásának engedélyezéséhez.
    - Az **eszköz nevének sablonjának alkalmazása** (a Windows 10 1809-es vagy újabb verziójára, valamint az Azure ad JOIN típusra van szükség): válassza az **Igen** lehetőséget, ha az eszköznek a regisztráció során való elnevezéséhez használni szeretné a sablont. A nevek legfeljebb 15 karakterből állhatnak, és betűket, számokat és kötőjelet tartalmazhatnak. A nevek nem állhatnak csak számokból. Hardverspecifikus sorozatszám hozzáadásához használja a [%SERIAL% makrót](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp). Egy másik lehetőség a [%RAND:x% makró](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) használata, amellyel véletlenszerű számsort adhat hozzá. Az x a hozzáadni kívánt számjegyek számát jelenti. A [tartományhoz való csatlakozás profiljában](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile)csak a hibrid eszközök előzetes javítását lehet megadni. 
    - **Nyelv (Régió)** \*: Válassza ki az eszközön használandó nyelvet. Ez a lehetőség csak akkor érhető el, ha a **Telepítési mód** beállításnál az **Öntelepítő** lehetőséget választotta.
    - A **billentyűzet automatikus konfigurálása**\*: Ha egy **nyelv (régió)** van kiválasztva, válassza az **Igen** lehetőséget a billentyűzet kijelölési oldalának kihagyásához. Ez a lehetőség csak akkor érhető el, ha a **Telepítési mód** beállításnál az **Öntelepítő** lehetőséget választotta.
8. Válassza a **Tovább** elemet.
9. A **hatókör címkék** lapon adja meg a profilra alkalmazni kívánt hatókör-címkéket. A hatókör-címkékkel kapcsolatos további információkért lásd: [a szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használata a terjesztéshez](../fundamentals/scope-tags.md).
10. Válassza a **Tovább** elemet.
11. A **hozzárendelések** lapon válassza a **kijelölt csoportok** lehetőséget a **hozzárendeléshez**.

    ![Képernyőfelvétel a hozzárendelésekről lap](./media/enrollment-autopilot/create-profile-assignments.png)

12. Válassza ki a **felvenni kívánt csoportokat**, majd válassza ki azokat a csoportokat, amelyeket bele szeretne foglalni ebbe a profilba.
13. Ha ki szeretne zárni egy csoportot, válassza ki a **kizárni kívánt csoportokat**, majd válassza ki a kizárandó csoportokat.
14. Válassza a **Tovább** elemet.
15. A profil létrehozásához a **felülvizsgálat + létrehozás** lapon válassza a **Létrehozás** lehetőséget.

    ![A felülvizsgálati oldal képernyőképe](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Az Intune rendszeresen ellenőrzi az új eszközöket a hozzárendelt csoportokban, majd megkezdi a profilok hozzárendelésének folyamatát az eszközökhöz. A folyamat végrehajtása több percet is igénybe vehet. Az eszköz telepítése előtt győződjön meg arról, hogy a folyamat befejeződött.  Az **eszközök** **területen > a Windows > ** **windows-beléptetési** > **eszközöket** (a **Windows Autopilot Deployment program** alatt, ahol a profil állapota "nincs hozzárendelve" értékről "hozzárendelés", majd végül a "hozzárendelés" elemre változik).

## <a name="edit-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil szerkesztése
Az AutoPilot üzembehelyezési profil létrehozása után módosíthatja az üzembehelyezési profil egyes részeit.   

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **windows** > **Windows-regisztráció** > **telepítési profilok**lehetőséget.
2. Válassza ki a szerkeszteni kívánt profilt.
3. Válassza a bal oldali **Tulajdonságok** lehetőséget a telepítési profil nevének vagy leírásának módosításához. A módosítások elvégzését követően kattintson a **Mentés** gombra.
5. A Kezdőélmény beállításainak módosításához kattintson a **Beállítások** elemre. A módosítások elvégzését követően kattintson a **Mentés** gombra.

> [!NOTE]
> A profil módosításai alkalmazva lesznek a profilhoz társított eszközökön. Azonban a frissített profilt az Intune-ban korábban már regisztrált eszközökre csak azok alaphelyzetbe állítása és megújítása után alkalmazza a rendszer.

## <a name="edit-autopilot-device-attributes"></a>Autopilot-eszköz attribútumainak szerkesztése
Az Autopilot-eszköz feltöltése után szerkesztheti az eszköz bizonyos attribútumait.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **Windows** > **Windows-beléptetési** > **eszközök** elemet (a **Windows Autopilot Deployment program**területen.
2. Válassza ki a szerkeszteni kívánt eszközt.
3. A képernyő jobb oldalán található ablaktáblán szerkesztheti az eszköz nevét, a csoport címkéjét vagy a felhasználóbarát nevet (ha felhasználóhoz rendelt hozzá).
4. Válassza a **Mentés** lehetőséget.

> [!NOTE]
> Az eszközök neve minden eszközhöz konfigurálható, de a hibrid Azure AD-hez csatlakoztatott üzemelő példányok figyelmen kívül lesznek hagyva. Az eszköz neve továbbra is a hibrid Azure AD-eszközök tartományhoz tartozó csatlakozási profiljából származik.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Riasztások a Windows Autopilot nem hozzárendelt eszközeihez  <!-- 163236 -->  

A riasztások jelzik, hogy az AutoPilot programban hány eszközhöz nincs hozzárendelve AutoPilot üzembehelyezési profil. A riasztás adatai alapján a profilok létrehozhatók és a hozzárendelés nélküli eszközökhöz rendelhetők. A riasztásra kattintva megjelenik a Windows AutoPilot-eszközök részletes adatokat is tartalmazó, teljes listája.

A nem hozzárendelt eszközökre vonatkozó riasztások megtekintéséhez a [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **Áttekintés** > **beléptetési riasztások** > a nem **hozzárendelt eszközök**elemet.  

## <a name="autopilot-deployments-report"></a>Autopilot-alapú üzembe helyezési jelentés
A Windows Autopilot szolgáltatásban üzembe helyezett összes eszközről megtekintheti a részleteket.
A jelentés megjelenítéséhez nyissa meg a [Microsoft Endpoint Manager felügyeleti központját](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **monitor** > Autopilot-alapú **telepítések**lehetőséget.
Az Adatfrissítés az üzembe helyezést követő 30 napig elérhető.

Ez a jelentés előzetes verzióban érhető el. Az eszköz központi telepítési rekordjait jelenleg csak új Intune-regisztrációs események indítják el. Ez azt jelenti, hogy a jelentés nem veszi fel az új Intune-regisztrációt kiváltó központi telepítést. Ebbe beletartozik minden olyan alaphelyzetbe állítás, amely megtartja a regisztrációt és a robotpilóta-fehér kesztyű felhasználói részét.

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Felhasználó hozzárendelése egy adott Autopilot-eszközhöz

Felhasználót rendelhet hozzá egy adott Autopilot-eszközhöz. Ez a hozzárendelés előre kitölti a [vállalati védjeggyel ellátott](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) bejelentkezési oldal felhasználói űrlapját az Azure Active Directoryból származó adatokkal a Windows beállítása során. Egyéni üdvözlési megnevezés beállítását is lehetővé teszi. A windowsos bejelentkezési adatokat nem tölti ki előre és nem is módosítja. Ilyen módon csak licenccel rendelkező Intune-felhasználók rendelhetők hozzá.

Előfeltételek: Azure Active Directory Céges portál konfigurálva van, és a Windows 10 1809-es vagy újabb verziójával.

> [!NOTE]
> Ha az ADFS-t használja, a felhasználó egy adott Autopilot-eszközhöz való hozzárendelésével nem működik.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **Windows** > **Windows-beléptetési** > **eszközök** lehetőséget (a **windows Autopilot Deployment program** területen > Válassza ki az eszközt, > a **felhasználó kiosztása**elemet.

    ![Képernyőkép a felhasználó hozzárendeléséről](./media/enrollment-autopilot/assign-user.png)

2. Jelöljön ki egy Intune-licenccel rendelkező Azure-felhasználót, és válassza a **Kiválasztás** lehetőséget.

    ![Képernyőkép a felhasználó kiválasztásáról](./media/enrollment-autopilot/select-user.png)

3. A **Rövid felhasználónév** mezőbe gépeljen be egy rövid nevet, vagy fogadja el az alapértelmezettet. Ez a rövid név jelenik meg, amikor a felhasználó bejelentkezik a Windows telepítése során.

    ![A rövid felhasználónév képernyőképe](./media/enrollment-autopilot/friendly-name.png)

4. Válassza az **OK** gombot.


## <a name="delete-autopilot-devices"></a>AutoPilot-eszközök törlése

Törölheti az Intune-ban nem regisztrált Windows Autopilot-eszközöket:

- Törölje az eszközöket a Windows **Autopilot eszközről > ** **Windows** > **windows-beléptetési** > **eszközön** (a **Windows Autopilot Deployment program**alatt). Válassza ki a törölni kívánt eszközöket, majd válassza a **Törlés**lehetőséget. A Windows Autopilot-eszközök törlése néhány percet igénybe vehet.

Az eszköz bérlőből való teljes eltávolítása az Intune-eszköz, a Azure Active Directory eszköz és a Windows Autopilot-eszköz rekordjainak törlését igényli. Ezt az Intune-ból végezheti el:

1. Ha az eszközök regisztrálva vannak az Intune-ban, először [törölnie kell őket az Intune minden eszköz](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)paneljéről.

2. Azure Active Directory eszközökön **lévő eszközök törlése** az **Azure AD-eszközök** > .

3. Törölje az eszközöket a Windows **Autopilot eszközről > ** **Windows** > **windows-beléptetési** > **eszközökre** (a **Windows Autopilot Deployment program** > alatt. Válassza ki a törölni kívánt eszközöket, majd válassza a **Törlés**lehetőséget. A Windows Autopilot-eszközök törlése néhány percet igénybe vehet.

## <a name="using-autopilot-in-other-portals"></a>Az AutoPilot használata más portálokon
Ha nem kíván a mobileszközök felügyeletével foglalkozni, más portálokon is használhatja az AutoPilotot. Más portálok is használhatók, de javasoljuk, hogy az Intune-t csak AutoPilottal végzett üzembe helyezések felügyeletéhez használja. Az Intune más portálokkal való használatakor az Intune nem tudja végrehajtani a következőket:  

- Megjeleníteni az Intune-ban létrehozott, de egy másik portálon szerkesztett profilok módosításait
- Szinkronizálni egy másik portálon létrehozott profilokat
- Megjeleníteni a profil-hozzárendelések más portálon végzett módosításait
- Szinkronizálni a más portálon végzett profil-hozzárendeléseket
- Megjeleníteni az eszközlista más portálon végzett módosításait

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot meglévő eszközökhöz

Ha a Configuration Manager [meglévő eszközökhöz használható AutoPilot szolgáltatásával](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) regisztrál, egy korrelátorazonosítóval csoportosíthatja a Windows-eszközöket. A korrelátorazonosító az AutoPilot konfigurációs fájljának egyik paramétere. Az [enrollmentProfileName Azure AD-beli eszközattribútum](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) beállítása automatikusan az ezzel megegyező „OfflineAutopilotprofile-\<korrelátorazonosítóra\>” módosul. Így tetszőleges dinamikus Azure AD-csoportok hozhatók létre korrelátorazonosító alapján az enrollmentprofileName attribútum használatával.

>[!WARNING] 
> Mivel a korrelátorazonosító nincs előzetesen megadva az Intune-on, az eszköz tetszés szerint jelenthet be bármilyen korrelátorazonosítót. Ha a felhasználó által létrehozott korrelátorazonosító egyezik egy AutoPilot- vagy Apple DEP-profil nevével, az eszköz hozzá lesz adva az enrollmentProfileName attribútumon alapuló összes dinamikus Azure AD-eszközcsoporthoz. Az ütközés elkerüléséhez:
> - A dinamikus csoportokra vonatkozó szabályokat mindig a *teljes* enrollmentProfileName érték használatával hozza létre.
> - Az Autopilot- és Apple DEP-profilok nevét soha ne kezdje az OfflineAutopilotprofile- előtaggal.

## <a name="next-steps"></a>További lépések
Miután konfigurálta a Windows AutoPilotot a regisztrált Windows 10-eszközökhöz, sajátítsa el, hogyan felügyelheti az eszközöket. További információt [A Microsoft Intune-eszközfelügyelet ismertetése](../remote-actions/device-management.md) című témakörben talál.
