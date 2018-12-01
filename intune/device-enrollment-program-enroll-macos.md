---
title: MacOS-eszközök regisztrálása – Készülékregisztrációs Program vagy az Apple School Manager
titleSuffix: Microsoft Intune
description: Céges tulajdonú macOS-es eszközök regisztrálása az Apple készülékregisztrációs programjával (DEP).
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 12a59165cd9ebe43826f8ec63ed5b045e5f3e991
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728752"
---
# <a name="automatically-enroll-macos-devices-with-the-device-enrollment-program-or-apple-school-manager"></a>A Készülékregisztrációs Program vagy az Apple School Manager macOS-eszközök automatikus regisztrálása

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk segítséget nyújt az Apple keretében vásárolt eszközök macOS-eszközök regisztrálásának beállítása [Készülékregisztrációs Program (DEP)](https://deploy.apple.com) vagy [Apple School Manager](https://school.apple.com/). Is használhatja ezeket a regisztrációk esetében nagy számú eszközt anélkül, hogy kézbe venné őket. A macOS-eszközöket közvetlenül a felhasználóknak küldheti el. Amikor a felhasználó bekapcsolja az eszközt, a Beállítási asszisztens az előre konfigurált beállítások szerint fut, és regisztrálja az eszközt az Intune felügyeleti szolgáltatásban.

Regisztráció beállítása az Intune és az Apple DEP-portált használja. Regisztrációs profilok, Regisztrálás során az eszközre vonatkozó beállításokat tartalmazó hoz létre.

Sem a DEP-regisztrációt, vagy az Apple School Manager dolgozni a [készülékregisztráció-kezelő](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Előfeltételek
- Keretében vásárolt eszközök [Apple School Manager](https://school.apple.com/) vagy [az Apple Készülékregisztrációs Program](http://deploy.apple.com)
- Sorozatszámok listája vagy vásárlási megrendelési szám. 
- [MDM-szolgáltató ](mdm-authority-set.md)
- [Apple MDM Push-tanúsítvány](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Apple DEP-token beszerzése

A DEP vagy az Apple School Manager macOS-eszközök regisztrálása előtt kell egy Apple-től származó DEP-jogkivonatot (.p7m) fájl. Ez a token lehetővé teszi, hogy az Intune szinkronizálja az a szervezet tulajdonában lévő eszközök adatait. A token ezenkívül lehetővé teszi, hogy az Intune feltöltse a regisztrációs profilokat az Apple adatbázisába, és eszközöket rendeljen az egyes profilokhoz.

A token létrehozásához használhatja az Apple portálján. Az Apple portálján az eszközök hozzárendelése kezelés céljából az Intune-hoz is használhatja.

> [!NOTE]
> Ha törli a tokent a klasszikus Intune-portálon az Azure-ba való migrálás előtt, az Intune előfordulhat, hogy visszaállít egy törölt Apple-token. A tokent ismét törölheti az Azure Portalról.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>1. lépés Töltse le a nyilvános kulcsú Intune-tanúsítványt, amelyre szükség van a token létrehozásához.

1. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > **Hozzáadás** elemet.

    ![Szerezzen be egy készülékregisztrációs programbeli tokent.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Engedélyezze a Microsoftnak az **Elfogadom** lehetőség választásával a felhasználó- és eszközadatok Apple-nek való elküldését.

   ![Képernyőkép – A Készülékregisztrációs program tokenje panel az Apple tanúsítványok munkaterületen – nyilvános kulcs letöltése.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Kattintson a **Nyilvános kulcs letöltése** elemre a titkosításikulcs-fájl (.pem) letöltéséhez és helyi mentéséhez. A PEM-fájllal megbízhatósági kapcsolati tanúsítványt kérhet az Apple portálján szolgál.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>2. lépés Töltsön le a kulcsa segítségével egy tokent az Apple-től.

1. Válasszon **token létrehozása az Apple Device Enrollment Program** vagy **hozzon létre egy tokent az Apple School Manager programon keresztül** nyissa meg a megfelelő Apple-portált, és jelentkezzen be vállalati Apple ID azonosítójával. Ezt az Apple ID használatával a jogkivonat megújításához.
2.  A DEP, az Apple portálján válassza **Ismerkedés** a **Device Enrollment Program** > **kiszolgálók kezelése** > **MDM hozzáadása Kiszolgáló**.
3.  Az Apple School kezelése, az Apple portálján válassza a **MDM kiszolgálók** > **MDM-kiszolgáló hozzáadása**.
4. Az **MDM Server Name** (MDM-kiszolgáló neve) mezőben adja meg az MDM-kiszolgáló nevét, majd kattintson a **Next** (Tovább) gombra. A kiszolgálónév Önnek segít a mobileszköz-felügyeleti (MDM-) kiszolgáló azonosításában, nem ez a Microsoft Intune-kiszolgáló URL-címe vagy neve.

5. Megjelenik a **Hozzáadás:&lt;Kiszolgálónév&gt;** párbeszédablak, és kéri **a nyilvános kulcs feltöltését**. Kattintson a **Choose File…** (Fájl kiválasztása…) elemre a .pem-fájl feltöltéséhez, majd válassza a **Next** (Tovább) lehetőséget.

6. Válassza a **Deployment Programs** (Telepítési programok) &gt; **Device Enrollment Program** (Készülékregisztrációs program) &gt; **Manage Devices** (Eszközök kezelése) lehetőséget.
7. Az **Eszközök kiválasztásának szempontja** alatt adja meg az eszközök azonosításának módját:
    - **Sorozatszám**
    - **Sorszám**
    - **CSV-fájl feltöltése**.

   ![Képernyőkép – Eszközök kiválasztásának beállítása: sorozatszám alapján. Választott tevékenység: hozzárendelés kiszolgálóhoz. Kiszolgálónév megadása.](./media/enrollment-program-token-specify-serial.png)

8. A **Választott tevékenység** területen jelölje ki a **Hozzárendelés kiszolgálóhoz** elemet, válassza Microsoft Intune-hoz megadott &lt;Kiszolgálónevet&gt;, majd kattintson az **OK** gombra. Az Apple-portál az Intune-kiszolgálóhoz rendeli a megadott eszközök kezelését, majd megjeleníti a **Hozzárendelés kész** üzenetet.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>3. lépés. Mentse a token létrehozásához használt Apple ID-t.

Az Azure-beli Intune-portálon adja meg az Apple ID azonosítót későbbi felhasználásra.

![Képernyőkép – A DEP-token létrehozásához használt Apple ID megadása és a DEP-token megkeresése.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>4. lépés. Töltse fel a tokent.
Az **Apple-token** mezőben keresse meg tallózással a tanúsítványfájlt (.pem), és válassza a **Megnyitás**, majd a **Létrehozás** lehetőséget. A leküldéses tanúsítvány lehetővé teszi, hogy az Intune regisztrálja és felügyelje a macOS-eszközöket a szabályzatoknak a regisztrált eszközökre való leküldésével. Az Intune automatikusan szinkronizálja az Apple-lel a regisztrációs programfiók adatait.

## <a name="create-an-apple-enrollment-profile"></a>Apple-regisztrációs profil létrehozása

Most, hogy telepítette a jogkivonatot, létrehozhat egy regisztrációs profilt az eszközökhöz. A regisztrálás során az eszközök csoportjára alkalmazott beállításokat egy készülékregisztrációs profil határozza meg.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** elemet.
2. Válasszon egy tokent, és válassza a **Profilok**, majd a **Profil létrehozása** lehetőséget.

    ![Készítsen egy képernyőképet a profilról.](./media/device-enrollment-program-enroll-ios/image04.png)

3. A **Profil létrehozása** panelen adminisztrációs célból adja meg a profil **Nevét** és **Leírását**. Ezeket a felhasználók nem fogják látni. A **Név** mező felhasználásával dinamikus csoportot hozhat létre az Azure Active Directoryban. Használja a profilnevet az enrollmentProfileName paraméter meghatározásához, hogy ezzel a regisztrációs profillal rendelhesse hozzá az eszközöket. További információk az [Azure Active Directory-alapú dinamikus csoportokról](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![A profil neve és leírása.](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. A **Platform** területen válassza az **macOS** lehetőséget.

5. A **Felhasználói affinitást** aszerint állítsa be, hogy a profilhoz tartozó eszközöket hozzárendelt felhasználóval vagy anélkül szükséges-e regisztrálni.
    - **Regisztráció felhasználói affinitással** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek a felhasználók tulajdonában vannak, de egyes szolgáltatásokhoz, például alkalmazások telepítéséhez, a Céges portál alkalmazást kívánják használni. ADFS használata esetén a felhasználói affinitáshoz [WS-Trust 1.3 Username/Mixed végpont](https://technet.microsoft.com/library/adfs2-help-endpoints) szükséges. [További információ](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).A többtényezős hitelesítés nincs támogatva felhasználói affinitást használó macOS DEP-eszközökön.

    - **Regisztráció felhasználói affinitás nélkül** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek nincsenek egy adott felhasználóhoz társítva. Olyan eszközökhöz használja, amelyek a helyi felhasználói adatokhoz való hozzáférés nélkül végeznek feladatokat. Egyes alkalmazások, mint például a Céges portál alkalmazás, nem működnek.

6. Válassza az **Eszközkezelési beállításokat**, és válassza ki, hogy zárolt regisztrációt szeretne-e alkalmazni az ezt a profilt használó eszközökhöz. A **Zárolt regisztráció** letiltja azokat a macOS-beállításokat, amelyek segítségével eltávolítható a felügyeleti profil a **Rendszerbeállítások** menü vagy a **Terminál** használatával. Az eszköz regisztrálása után ez a beállítás nem módosítható az eszköz összes adatának törlése nélkül.

    ![Az Eszközkezelési beállítások képernyőképe.](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. Válassza az **OK** gombot.

8. Válassza a **Beállítási asszisztens beállításai** elemet, és konfigurálja az alábbi profilbeállításokat:  ![A beállítási asszisztens testreszabása.](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)

    | Részlegbeállítások | Leírás |
    |---|---|
    | <strong>Részleg neve</strong> | Akkor jelenik meg, ha a felhasználó az aktiválás során a <strong>Konfiguráció névjegye</strong> elemre koppint. |
    | <strong>Részleg telefonszáma</strong> | Akkor jelenik meg, ha a felhasználó az aktiválás során a <strong>Segítségre van szüksége?</strong> gombra kattint. |

  Választhat, hogy megjelenjenek-e a Beállítási asszisztens különböző képernyői, amikor a felhasználó beállítja az eszközt.
  - Ha az **Elrejtés** lehetőséget választja, az adott képernyő nem fog megjelenni a beállítás során. Az eszköz beállítását követően a felhasználó a **Beállítások** menüben továbbra is beállíthatja az érintett funkciót.
  - Ha a **Megjelenítés** lehetőséget választja, az adott képernyő megjelenik a beállítás során. A felhasználó egyes esetekben átugorhat egy-egy képernyőt anélkül, hogy bármit is tenne. A kihagyott funkciókat később az eszköz **Beállítások** menüjében állíthatja be. 


    | Beállítási asszisztens képernyőinek beállításai | Ha a **Megjelenítés** lehetőséget választja, a telepítés során az eszköz... |
    |------------------------------------------|------------------------------------------|
    | <strong>PIN-kód</strong> | Elkéri a felhasználótól a PIN-kódot. PIN-kód megadására mindig szükség van, kivéve, ha az eszköz biztonságát, illetve elérésének szabályozását valamilyen más módszer biztosítja (például teljes képernyős mód, amely egyetlen alkalmazás futtatására korlátozza az eszközt). |
    | <strong>Helyalapú szolgáltatások</strong> | Elkéri a felhasználó tartózkodási helyét. |
    | <strong>Visszaállítás</strong> | Megjeleníti az **Alkalmazások és adatok** képernyőt. Ezen a képernyőn az eszköz beállításakor a felhasználónak lehetősége van adatok visszaállítására vagy átvitelére az iCloudos biztonsági mentésből. |
    | <strong>iCloud és Apple ID</strong> | Lehetőséget nyújt a felhasználónak arra, hogy bejelentkezzen az **Apple ID**-jével, és használja az **iCloud** szolgáltatást.                         |
    | <strong>Feltételek és kikötések</strong> | Felkéri a felhasználót, hogy fogadja el az Apple használati feltételeit. |
    | <strong>Touch ID</strong> | Lehetőséget nyújt a felhasználónak ujjlenyomat-azonosítás beállítására az eszközön. |
    | <strong>Apple Pay</strong> | Lehetőséget nyújt a felhasználónak az Apple Pay beállítására az eszközön. |
    | <strong>Nagyítás</strong> | Lehetőséget nyújt a felhasználónak a képernyő nagyítására az eszköz beállításakor. |
    | <strong>Siri</strong> | Lehetőséget nyújt a felhasználónak a Siri beállítására. |
    | <strong>Diagnosztikai adatok</strong> | Megjeleníti a **Diagnosztika** képernyőt. Ezen a képernyőn a felhasználó diagnosztikai adatokat küldhet az Apple-nek. |
    | <strong>FileVault</strong> | Lehetőséget nyújt a felhasználónak a FileVault-titkosítás beállítására. |
    | <strong>iCloud-diagnosztika</strong> | Lehetőséget nyújt a felhasználónak arra, hogy iCloud diagnosztikai adatokat küldhessen az Apple-nek. |
    | <strong>Regisztráció</strong>| Kötelezi a felhasználót az eszköz regisztrálására. |

   

10. Válassza az **OK** gombot.

11. Válassz a **Létrehozás** elemet a profil mentéséhez.

## <a name="sync-managed-devices"></a>Felügyelt eszközök szinkronizálása
Miután az Intune engedélyt kapott az eszközei felügyeletére, szinkronizálhatja az Intune-t az Apple-lel, hogy megtekinthesse a felügyelt eszközöket az Azure-beli Intune-portálon.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, válasszon egy tokent a listából, majd válassza az **Eszközök** > **Szinkronizálás** lehetőséget. ![Képernyőkép – A Szinkronizálás hivatkozás választása a Készülékregisztrációs programba felvett eszközök mező kijelölése után.](./media/device-enrollment-program-enroll-ios/image06.png)

   Az Apple elfogadható regisztrációs programforgalomra vonatkozó feltételeinek teljesítése céljából az Intune az alábbi korlátozásokat írja elő:
   - Teljes szinkronizálás legfeljebb hétnaponta futtatható. A teljes szinkronizálás során az Intune beolvassa az Intune-hoz csatlakoztatott Apple MDM-kiszolgálóhoz rendelt sorozatszámok frissített teljes listáját. Miután egy Készülékregisztrációs programbeli eszközt úgy törölnek az Intune portálról, hogy nem szüntetik meg az Apple MDM-kiszolgálóval való társítását a DEP-portálon, csak a teljes szinkronizálás lefuttatása után lesz újraimportálva az Intune-ba.   
   - A szinkronizálás futtatása automatikusan történik 24 óránként. A **Szinkronizálás** gombra kattintva is végezhet szinkronizálást (legfeljebb 15 percenként egyszer). Az összes szinkronizálási kérelemnek 15 percen belül kell befejeződnie. A szinkronizálás befejeződéséig a **Szinkronizálás** gomb letiltott. A szinkronizálás frissíti a meglévő eszközök állapotát, és a importálja az Apple MDM-kiszolgálóhoz rendelt új eszközöket.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Regisztrálási profil eszközökhöz rendelése
Ahhoz, hogy egy eszközt regisztrálni lehessen, először hozzá kell rendelni egy regisztrációs programprofilt.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon egy tokent a listából.
2. Válassza az **Eszközök** lehetőséget, válasszon eszközöket a listából, majd válassza a **Profil hozzárendelése** elemet.
3. A **Profil hozzárendelése** területen válasszon egy profilt az eszközökhöz, majd válassza a **Hozzárendelés** lehetőséget.

### <a name="assign-a-default-profile"></a>Alapértelmezett profil hozzárendelése

Választhat egy alapértelmezett macOS- vagy iOS-profilt, amelyet a rendszer az adott tokennel regisztráló összes eszközre alkalmaz. 

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon egy tokent a listából.
2. Válassza az **Alapértelmezett profil beállítása** lehetőséget, válasszon egy profilt a legördülő listából, majd válassza a **Mentés** lehetőséget. A választott profil alkalmazva lesz az adott tokennel regisztráló összes eszközre.

## <a name="distribute-devices"></a>Eszközök terjesztése
Engedélyezte az eszközfelügyeletet és az Apple és az Intune közötti szinkronizálása rendelkezik, és hozzárendelt egy profilt, hogy az eszközök regisztrálásához. Az eszközök ekkor már kioszthatók a felhasználóknak. Felhasználói affinitással rendelkező eszközök esetén minden felhasználóhoz hozzá kell rendelni egy Intune-licencet. A felhasználói affinitás nélküli eszközökhöz licenc szükséges. Regisztrációs profil csak akkor léptethető érvénybe egy aktivált eszközön, ha előtte törli az eszköz összes adatát.

## <a name="renew-a-dep-token"></a>DEP-token megújítása  
1. Ugrás a deploy.apple.com címre.  
2. A **Manage Servers** (Kiszolgálók kezelése) területen válassza ki a megújítani kívánt token-fájlhoz társított MDM-kiszolgálót.
3. Válassza a **Generate New Token** (Új token létrehozása) lehetőséget.

    ![Képernyőkép új token generálásáról.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Válassza a **Your Server Token** (Saját kiszolgálói token) lehetőséget.  
5. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon ki a tokent.
    ![Képernyőkép a regisztrációs program jogkivonatairól.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Válassza a **Jogkivonat megújítása** lehetőséget, majd adja meg az eredeti jogkivonat létrehozásához használt Apple ID-t.  
    ![Képernyőkép új token generálásáról.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Töltse fel az újonnan letöltött tokent.  
9. Válassza a **Token megújítása** lehetőséget. Látni fogja a token megújításáról szóló megerősítő üzenetet.   
    ![Képernyőkép a megerősítésről.](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>További lépések

A macOS-eszközök regisztrálása után megkezdheti azok [felügyeletét](device-management.md).