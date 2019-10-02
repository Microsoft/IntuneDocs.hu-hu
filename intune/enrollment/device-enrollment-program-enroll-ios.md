---
title: iOS-eszközök regisztrálása – Készülékregisztrációs program
titleSuffix: Microsoft Intune
description: Céges tulajdonú iOS-es eszközök regisztrálása az Apple készülékregisztrációs programjával (DEP).
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2e9b5eb15cf446b317818a93baa075cdbd33afd2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729991"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>iOS-eszközök automatikus regisztrálása az Apple készülékregisztrációs programjával (DEP)

Beállíthatja az Intune-t az Apple [Készülékregisztrációs programon (DEP)](https://deploy.apple.com)keresztül vásárolt iOS-eszközök regisztrálásához. A DEP lehetővé teszi, hogy nagy számú eszközt regisztráljon anélkül, hogy megérintse őket. Az olyan eszközök, mint az iPhone és az iPad, közvetlenül a felhasználók számára is elhelyezhetők. Amikor a felhasználó bekapcsolja az eszközt, a Beállítási asszisztens az előre konfigurált beállítások szerint fut, és regisztrálja az eszközt a felügyeleti szolgáltatásban.

DEP-regisztráció engedélyezéséhez az Intune- és az Apple DEP-portált is használnia kell. Ahhoz, hogy az eszközök felügyeletét az Intune-hoz rendelhesse, szükség van a sorozatszámok vagy a beszerzési rendelésszámok listájára. Olyan DEP-regisztrációs profilokat hoz létre, amelyek tartalmazzák a regisztráció során az eszközre vonatkozó beállításokat.

A DEP-regisztráció így nem működik az [eszköz beléptetési kezelőjével](device-enrollment-manager-enroll.md).

## <a name="dep-and-the-company-portal"></a>DEP és a Céges portál

A DEP-regisztrációk nem kompatibilisek a Céges portál alkalmazás App Store-verziójával. Hozzáférést biztosíthat a felhasználóknak a Céges portál alkalmazáshoz egy DEP-eszközön. Ha hozzáférést szeretne biztosítani nekik, küldje le az alkalmazást az eszközre a DEP-profilban található VPP (Volume Purchase program) használatával a **céges portál telepítésével** . További információ: iOS- [eszközök automatikus regisztrálása az Apple Készülékregisztrációs program](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

 A Céges portál alkalmazást a DEP szolgáltatással már regisztrált eszközökre is telepítheti. Ehhez telepítse a Céges portál alkalmazást az Intune-nal egy alkalmazott [alkalmazás-konfigurációs házirenddel](../apps/app-configuration-policies-use-ios.md) .

## <a name="what-is-supervised-mode"></a>A felügyelt mód ismertetése

Az Apple az iOS 5-tel vezette be a felügyelt módot. A felügyelt módon futtatott iOS-eszközök (készülékek) működése nagyobb mértékben felügyelhető. Ezért különösen hasznos a vállalati tulajdonú eszközök esetében. Az Intune az Apple készülékregisztrációs program (DEP) keretében biztosít lehetőséget az eszközök felügyelt módú üzemeltetésének beállítására.

A nem felügyelt DEP-eszközök támogatása megszűnt az iOS 11-ben. Az iOS 11-es és újabb verzióiban a DEP-konfigurációval rendelkező eszközöknek mindig felügyeltnek kell lenniük. Egy későbbi iOS-kiadásban a DEP is_supervised jelölőjét nem veszi figyelembe a rendszer.

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Előfeltételek
- [Apple készülékregisztrációs program](http://deploy.apple.com) keretében vásárolt eszközök
- [Mobileszköz-felügyeleti (MDM) szolgáltató](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push-tanúsítvány](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Apple DEP-token beszerzése

Az iOS-eszközök DEP-regisztrációjához először is egy Apple-től származó DEP-tokenre (.p7m) van szükség. Ez a token (jogkivonat) teszi lehetővé az Intune számára a vállalat által birtokolt DEP-eszközök adatainak szinkronizálását. Azt is engedélyezi, hogy az Intune regisztrációs profilokat töltsön fel az Apple számára, és eszközöket rendeljen ezen profilokhoz.

A DEP-tokent az Apple DEP-portálon hozhatja létre. Szintén a DEP-portál használatával rendelheti hozzá az eszközök felügyeletét az Intune-hoz.

> [!NOTE]
> Ha törli a tokent a klasszikus Intune-portálról az Azure-ba történő migrálás előtt, előfordulhat, hogy az Intune visszaállít egy korábban törölt Apple DEP-tokent. Ilyenkor a DEP-tokent ismét törölheti az Azure Portalról.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>1\. lépés Töltse le a nyilvános kulcsú Intune-tanúsítványt, amelyre szükség van a token létrehozásához.

1. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > **Hozzáadás** elemet.

    ![Szerezzen be egy készülékregisztrációs programbeli tokent.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Engedélyezze a Microsoftnak az **Elfogadom** lehetőség választásával a felhasználó- és eszközadatok Apple-nek való elküldését.

   ![Képernyőkép – A Készülékregisztrációs program tokenje panel az Apple tanúsítványok munkaterületen – nyilvános kulcs letöltése.](./media/device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Kattintson a **Nyilvános kulcs letöltése** elemre a titkosításikulcs-fájl (.pem) letöltéséhez és helyi mentéséhez. A .pem fájllal megbízhatósági kapcsolati tanúsítványt kérhet az Apple Device Enrollment Program portálról.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>2\. lépés Töltsön le a kulcsa segítségével egy tokent az Apple-től.

1. A **Token létrehozása az Apple Készülékregisztrációs programjában** elemre kattintva nyissa meg az Apple Központi Telepítési Program portálját, és jelentkezzen be a cége Apple-azonosítójával. A későbbiekben ezt az Apple ID-t használhatja a DEP-token megújításához.
2. Az Apple [Központi Telepítési Program portálján ](https://deploy.apple.com) válassza a**Készülékregisztrációs program** **Első lépések** elemét.

3. A **Kiszolgálók kezelése** lapon válassza az **MDM-kiszolgáló hozzáadása** lehetőséget.
4. Az **MDM Server Name** (MDM-kiszolgáló neve) mezőben adja meg az MDM-kiszolgáló nevét, majd kattintson a **Next** (Tovább) gombra. A kiszolgálónév Önnek segít a mobileszköz-felügyeleti (MDM-) kiszolgáló azonosításában, Nem a Microsoft Intune-kiszolgáló nevét vagy URL-címét adja meg.

5. Megjelenik a **Hozzáadás:&lt;Kiszolgálónév&gt;** párbeszédablak, és kéri **a nyilvános kulcs feltöltését**. Válassza a **fájl kiválasztása...** lehetőséget. a .pem-fájl feltöltéséhez, majd válassza a **Next** (Tovább) lehetőséget.

6. Válassza a **Deployment Programs** (Telepítési programok) &gt; **Device Enrollment Program** (Készülékregisztrációs program) &gt; **Manage Devices** (Eszközök kezelése) lehetőséget.
7. Az **Eszközök kiválasztásának szempontja** alatt adja meg az eszközök azonosításának módját:
    - **Sorozatszám**
    - **Sorszám**
    - **CSV-fájl feltöltése**.

   ![Képernyőkép – Eszközök kiválasztásának beállítása: sorozatszám alapján. Választott tevékenység: hozzárendelés kiszolgálóhoz. Kiszolgálónév megadása.](./media/device-enrollment-program-enroll-ios/enrollment-program-token-specify-serial.png)

8. A **Választott tevékenység** területen jelölje ki a **Hozzárendelés kiszolgálóhoz** elemet, válassza Microsoft Intune-hoz megadott &lt;Kiszolgálónevet&gt;, majd kattintson az **OK** gombra. Az Apple-portál az Intune-kiszolgálóhoz rendeli a megadott eszközök kezelését, majd megjeleníti a **Hozzárendelés kész** üzenetet.

   Az Apple-portál **Központi telepítési programok** &gt; **Készülékregisztrációs program** &gt; **Hozzárendelési előzmények** menüpontjában jeleníthető meg az eszközök és a hozzájuk tartozó MDM-kiszolgálók listája.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>3\. lépés. Mentse a token létrehozásához használt Apple ID-t.

Az Azure-beli Intune-portálon adja meg az Apple ID azonosítót későbbi felhasználásra.

![Képernyőkép – A DEP-token létrehozásához használt Apple ID megadása és a DEP-token megkeresése.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>4\. lépés. Töltse fel a tokent, és válassza a hatókör címkék lehetőséget.

1. Az **Apple-token** mezőben keresse meg a tanúsítvány (. PEM) fájlját, majd válassza a **Megnyitás**lehetőséget.
2. Ha [hatókör-címkéket](../fundamentals/scope-tags.md) kíván alkalmazni erre a DEP-tokenre, válassza a **hatókör (címkék)** lehetőséget, és válassza ki a kívánt hatókör-címkéket. A jogkivonatra alkalmazott hatókör-címkéket a rendszer a tokenhez hozzáadott profilok és eszközök öröklik.
3. Válassza a **Létrehozás** lehetőséget.

A leküldéses tanúsítvány lehetővé teszi, hogy az Intune regisztrálja és felügyelje az iOS-eszközöket a szabályzatoknak a regisztrált mobileszközökre való leküldésével. Az Intune automatikusan szinkronizálja az Apple-lel a regisztrációs programfiók adatait.

## <a name="create-an-apple-enrollment-profile"></a>Apple-regisztrációs profil létrehozása

Most, hogy telepítette a jogkivonatot, létrehozhatja a regisztrációs profilt a DEP-eszközökhöz. A regisztrálás során az eszközök csoportjára alkalmazott beállításokat egy készülékregisztrációs profil határozza meg. DEP-tokenként legfeljebb 100 beléptetési profil adható meg.

> [!NOTE]
> Az eszközök le lesznek tiltva, ha nincs elegendő Céges portál licenc egy VPP-tokenhez, vagy ha a jogkivonat lejárt. Az Intune riasztást jelenít meg, ha a jogkivonat hamarosan lejár, vagy a licencek alacsonyan futnak.
 

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** elemet.
2. Válasszon ki egy jogkivonatot, válassza a **profilok** > **profil** > létrehozása**iOS**lehetőséget.

    ![Készítsen egy képernyőképet a profilról.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Az **alapvető beállítások** lapon adja meg a profil **nevét** és **leírását** felügyeleti célból. A felhasználók nem látják ezeket az adatokat. A **Név** mező felhasználásával dinamikus csoportot hozhat létre az Azure Active Directoryban. Használja a profilnevet az enrollmentProfileName paraméter meghatározásához, hogy ezzel a regisztrációs profillal rendelhesse hozzá az eszközöket. További információk az [Azure Active Directory-alapú dinamikus csoportokról](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![A profil neve és leírása.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Válassza **a Next (tovább) lehetőséget: Eszköz-felügyeleti**beállítások.

5. A **Felhasználói affinitást** aszerint állítsa be, hogy a profilhoz tartozó eszközöket hozzárendelt felhasználóval vagy anélkül szükséges-e regisztrálni.
    - **Regisztráció felhasználói affinitással** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek a felhasználók tulajdonában vannak, de egyes szolgáltatásokhoz, például alkalmazások telepítéséhez, a Céges portált kívánják használni. Ha ADFS van használatban, és a **Hitelesítés a Céges portállal a Beállítási asszisztens helyett** **Nem** értékre van állítva, akkor a [WS-Trust 1.3 Felhasználónév/Vegyes végpont](https://technet.microsoft.com/library/adfs2-help-endpoints) [További információ](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint) szükséges.

    - **Regisztráció felhasználói affinitás nélkül** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek nincsenek egy adott felhasználóhoz társítva. Ezt a lehetőséget olyan eszközök esetén használja, amelyek nem férnek hozzá a helyi felhasználói adatszolgáltatásokhoz. Egyes alkalmazások, mint például a Céges portál alkalmazás, nem működnek.

5. Ha a **felhasználói affinitással való regisztrációt**választotta, a felhasználók a céges portál az Apple beállítási asszisztense helyett engedélyezheti a hitelesítést.

    ![Végezzen hitelesítést a Céges portállal.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Ha az alábbi műveletek bármelyikét szeretné elvégezni, állítsa be, hogy a **felhasználóknak milyen helyen kell hitelesíteniük** **céges portál**.
    >    - Többtényezős hitelesítés használata
    >    - A felhasználók figyelmeztetése a jelszó módosítására az első bejelentkezéskor
    >    - A felhasználók figyelmeztetése a lejárt jelszó helyetti új jelszó kérésére a regisztráció során
    >
    > Ezek nem támogatottak az Apple beállítási asszisztenssel való hitelesítéskor.

6. Ha a **céges portál** lehetőséget választotta, **ahol a felhasználóknak hitelesíteniük kell a HITELESÍTÉST**, a VPP-token használatával automatikusan telepítheti a céges portál az eszközre. Ebben az esetben a felhasználónak nem kell megadnia egy Apple ID azonosítót. A Céges portál VPP-jogkivonattal való telepítéséhez válasszon egy jogkivonatot a **Céges portál telepítése a VPP-vel** résznél. Ehhez a Céges portál már hozzá lett adva a VPP-tokenhez. Ne konfiguráljon olyan házirendet, amely megköveteli az alkalmazás használatát a felhasználók számára, az Intune automatikusan telepíti a Céges portált az ezzel a beléptetési profillal alkalmazott eszközökön. Fontos, hogy a jogkivonat ne járjon le, és hogy elég eszközlicenccel rendelkezzen a Céges portál alkalmazáshoz. Ha a jogkivonat lejár vagy lejár a licencek közül, az Intune telepíti az App Store-Céges portált, és felszólítja az Apple ID azonosítóra. 

    > [!NOTE]
    > Ha **kijelöli, hogy a felhasználóknak hogyan kell céges portál hitelesíteniük** a szolgáltatást, akkor győződjön meg arról, hogy az eszköz beléptetési folyamata a vállalati portál DEP-eszközre való letöltésének első 24 óráján belül történik. Ellenkező esetben előfordulhat, hogy a regisztráció meghiúsul, és a gyári beállítások visszaállítására lesz szükség az eszköz regisztrálásához.
    
    ![Képernyőfelvétel a vállalati portál VPP-vel való telepítéséről.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Ha a **beállítási asszisztens** lehetőséget választotta, **ahol a felhasználóknak hitelesíteniük kell magukat**, de feltételes hozzáférést szeretne használni, vagy a vállalati alkalmazásokat is telepíteni kell az eszközökön, telepítenie kell a céges portál az eszközökön. Ehhez válassza az **Igen** lehetőséget a **céges portál telepítéséhez**.  Ha azt szeretné, hogy a felhasználók az App Store-ban való hitelesítés nélkül kapják meg a Céges portál, válassza a **céges portál VPP** -sel való telepítését, majd válassza ki a VPP-tokent. Győződjön meg arról, hogy a jogkivonat nem jár le, és hogy megfelelő eszköz-licenccel rendelkezik a Céges portál alkalmazás telepítéséhez.

8. Ha a VPP-vel való **céges portál telepítéshez**a tokent választotta, a beállítási asszisztens befejezése után az eszközt egyetlen alkalmazás módban (pontosabban a céges portál alkalmazásban) is zárolhatja. Ennek a lehetőségnek a beállításához válassza az **Igen** értéket a **Céges portál futtatása egyalkalmazásos módban a hitelesítésig** beállításhoz. Az eszköz használatához a felhasználónak először hitelesítenie kell magát a Céges portál használatával.

    A többtényezős hitelesítés nem támogatott egyetlen eszközön, egyetlen alkalmazás módban. Ez a korlátozás azért van, mert az eszköz nem tud másik alkalmazásra váltani, hogy elvégezze a hitelesítés második tényezőjét. Ezért ha a többtényezős hitelesítést egyetlen app Mode-eszközön szeretné használni, a második tényezőnek egy másik eszközön kell lennie.

    Ez a funkció csak akkor támogatott iOS 11.3.1-es és újabb verziók.

   ![Képernyőkép az Egyalkalmazásos módból.](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. Ha azt szeretné, hogy a profilt használó eszközök felügyelve legyenek, válassza az **Igen** lehetőséget a **felügyelt**elemnél.

    ![Az Eszközkezelési beállítások képernyőképe.](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

    A **felügyelt** eszközök esetében több felügyeleti lehetőséget érhet el, és az Aktiválási zár funkció alapértelmezés szerint le van tiltva. A Microsoft a DEP használatát javasolja a felügyelt üzemmód engedélyezéséhez, különösen ha nagy mennyiségű iOS-eszközt helyez üzembe.

    A rendszer kétféle módon is tudatja a felhasználókkal, hogy az eszközük felügyelet alatt áll:

   - A zárolási képernyő a következőket mondja: "Ezt az iPhone-t a contoso felügyeli."
   - A **Beállítások** > általánostudnivalók > a képernyőn: "Ez az iPhone felügyelve van. A Contoso figyelheti az internetes forgalmat és megállapíthatja a készülék helyét.” figyelmeztetés.

     > [!NOTE]
     > A felügyelet nélkül regisztrált eszközöket csak az Apple Configurator segítségével tudja átállítani felügyelt eszközzé. Az eszköz ily módon való átállításához csatlakoztatnia kell az iOS-eszközt egy Mac számítógéphez USB-kábellel. Ezzel kapcsolatban az [Apple Configurator dokumentációjában](http://help.apple.com/configurator/mac/2.3) talál további információkat.

10. Válassza ki, hogy a profilt használó eszközök zárolt regisztrációját kívánja-e használni. A **Zárolt regisztráció** letiltja azokat az iOS-beállításokat a **Beállítások** menüből, amelyek segítségével eltávolítható a felügyeleti profil. Az eszközök regisztrálását követően a beállítás nem módosítható az eszköz törlése nélkül. A zárolt regisztrációjú eszközökön a **Felügyelt** felügyeleti módot az *Igen* értékre kell beállítani. 

11. Válassza ki, hogy szeretné-e, hogy a profilt használó eszközök képesek legyenek **szinkronizálni a számítógépekkel**. Ha az **Apple Configurator engedélyezése tanúsítvány szerint** lehetőséget választja, tanúsítványt kell választania az **Apple Configurator-tanúsítványok** területen.

12. Ha az **Apple Configurator engedélyezése tanúsítvány szerint** lehetőséget választotta az előző lépésben, válasszon egy importálandó Apple Configurator-tanúsítványt.

13. Megadhat egy elnevezési formátumot a regisztráláskor automatikusan alkalmazott eszközökhöz és az egyes egymást követő beléptetésekhez. A névadási sablon létrehozásához válassza az **Igen** lehetőséget az **eszköznév alkalmazása sablonban**. Ezután az **eszköznév sablon** mezőbe írja be a profilt használó nevekhez használni kívánt sablont. Megadhatja az eszköz típusát és sorozatszámát tartalmazó sablon formátumát. 

14. Válassza **a Next (tovább) lehetőséget: A beállítási asszisztens**testreszabása.

15. A **beállítási asszisztens testreszabása** lapon adja meg a következő Profilbeállítások beállításait: ![A beállítási asszisztens testreszabása.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Részlegbeállítások | Leírás |
    |---|---|
    | <strong>Részleg neve</strong> | Akkor jelenik meg, ha a felhasználó az aktiválás során a <strong>Konfiguráció névjegye</strong> elemre koppint. |
    |    <strong>Részleg telefonszáma</strong>     | Akkor jelenik meg, ha a felhasználó az aktiválás során a <strong>Segítségre van szüksége?</strong> gombra kattint. |

    A beállítási asszisztens képernyőit elrejtheti az eszközön a felhasználó beállításakor.
    - Ha az **Elrejtés** lehetőséget választja, az adott képernyő nem fog megjelenni a beállítás során. Az eszköz beállítását követően a felhasználó a **Beállítások** menüben továbbra is beállíthatja az érintett funkciót.
    - Ha a **Megjelenítés** lehetőséget választja, az adott képernyő megjelenik a beállítás során. A felhasználó egyes esetekben átugorhat egy-egy képernyőt anélkül, hogy bármit is tenne. A kihagyott funkciókat később az eszköz **Beállítások** menüjében állíthatja be. 


    | Beállítási asszisztens képernyőinek beállításai | Ha a **Megjelenítés** lehetőséget választja, a telepítés során az eszköz... |
    |------------------------------------------|------------------------------------------|
    | <strong>PIN-kód</strong> | Elkéri a felhasználótól a PIN-kódot. Mindig PIN-kódot kell megadnia a nem biztonságos eszközökhöz, kivéve, ha a hozzáférés valamilyen más módon van szabályozva (például a kioszk mód, amely az eszközt egyetlen alkalmazásra korlátozza). |
    | <strong>Helyalapú szolgáltatások</strong> | Elkéri a felhasználó tartózkodási helyét. |
    | <strong>Visszaállítás</strong> | Megjeleníti az alkalmazások & az adatképernyőt. Ezen a képernyőn az eszköz beállításakor a felhasználónak lehetősége van adatok visszaállítására vagy átvitelére az iCloudos biztonsági mentésből. |
    | <strong>iCloud és Apple ID</strong> | Adja meg a felhasználónak az Apple ID-vel való bejelentkezéshez szükséges beállításokat, és használja az iCloudt.                         |
    | <strong>Feltételek és kikötések</strong> | Felkéri a felhasználót, hogy fogadja el az Apple használati feltételeit. |
    | <strong>Touch ID</strong> | Lehetőséget nyújt a felhasználónak ujjlenyomat-azonosítás beállítására az eszközön. |
    | <strong>Apple Pay</strong> | Lehetőséget nyújt a felhasználónak az Apple Pay beállítására az eszközön. |
    | <strong>Nagyítás</strong> | Lehetőséget nyújt a felhasználónak a képernyő nagyítására az eszköz beállításakor. |
    | <strong>Siri</strong> | Lehetőséget nyújt a felhasználónak a Siri beállítására. |
    | <strong>Diagnosztikai adatok</strong> | Jelenítse meg a diagnosztika képernyőt a felhasználó számára. Ezen a képernyőn a felhasználó diagnosztikai adatokat küldhet az Apple-nek. |
    | <strong>Hangjelzés</strong> | Adja meg a felhasználó számára a megjelenítési hang bekapcsolásának lehetőségét. |
    | <strong>Adatvédelmi</strong> | Jelenítse meg az adatvédelmi képernyőt a felhasználó számára. |
    | <strong>Android-áttelepítés</strong> | Adja meg a felhasználónak a dátum áttelepítését egy Android-eszközről. |
    | <strong>iMessage és FaceTime</strong> | Adja meg a felhasználónak a iMessage és a FaceTime beállítását. |
    | <strong>Bevezetési</strong> | Bevezetési információs képernyők megjelenítése a felhasználói oktatáshoz, mint például a fedőlap és a többfeladatos felügyelet és a vezérlési központ. |
    | <strong>Áttelepítés megtekintése</strong> | A felhasználó számára lehetővé teszi az adatok áttelepítését egy figyelési eszközről. |
    | <strong>Képernyő időpontja</strong> | Jelenítse meg a képernyő időképernyőjét. |
    | <strong>Szoftverfrissítés</strong> | A kötelező szoftverfrissítés képernyő megjelenítése. |
    | <strong>SIM-telepítés</strong> | Adjon lehetőséget a felhasználónak a mobil terv hozzáadására. |
    | <strong>Megjelenés</strong> | Jelenítse meg a megjelenés képernyőt a felhasználó számára. |
    | <strong>Expressz nyelv</strong>| Az expressz nyelvi képernyő megjelenítése a felhasználónak. |
    | <strong>Előnyben részesített nyelv</strong> | Adja meg a felhasználó számára a **kívánt nyelv**kiválasztását. |
    | <strong>Eszközről az eszközre való Migrálás</strong> | Adja meg a felhasználónak a régi eszközről az eszközre történő áttelepítési lehetőséget.|
    

16. A **tovább** gombra kattintva nyissa meg a **felülvizsgálat + létrehozás** lapot.

17. Válassz a **Létrehozás** elemet a profil mentéséhez.

## <a name="sync-managed-devices"></a>Felügyelt eszközök szinkronizálása
Miután az Intune engedélyt kapott az eszközei felügyeletére, szinkronizálhatja az Intune-t az Apple-lel, hogy megtekinthesse a felügyelt eszközöket az Azure-beli Intune-portálon.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, válasszon egy tokent a listából, majd válassza az **Eszközök** > **Szinkronizálás** lehetőséget. ![Képernyőfelvétel a beléptetési program-eszközök csomópontról és a szinkronizálási hivatkozásról.](./media/device-enrollment-program-enroll-ios/image06.png)

   Az Apple a beléptetési program forgalmára vonatkozó feltételeinek követéséhez az Intune a következő korlátozásokat írja elő:
   - Teljes szinkronizálás legfeljebb hétnaponta futtatható. A teljes szinkronizálás során az Intune beolvassa az Intune-hoz csatlakoztatott Apple MDM-kiszolgálóhoz rendelt sorozatszámok frissített teljes listáját. Ha egy DEP-eszközt törölnek az Intune-portálról, azt ki kell osztani az Apple MDM-kiszolgálóról a DEP-portálon. Ha nincs kiosztva, a rendszer nem importálja újra az Intune-ba, amíg a teljes szinkronizálás le nem fut.   
   - A szinkronizálás futtatása automatikusan történik 24 óránként. A **Szinkronizálás** gombra kattintva is végezhet szinkronizálást (legfeljebb 15 percenként egyszer). Az összes szinkronizálási kérelemnek 15 percen belül kell befejeződnie. A szinkronizálás befejeződéséig a **Szinkronizálás** gomb letiltott. A szinkronizálás frissíti a meglévő eszközök állapotát, és a importálja az Apple MDM-kiszolgálóhoz rendelt új eszközöket.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Regisztrálási profil eszközökhöz rendelése
Ahhoz, hogy egy eszközt regisztrálni lehessen, először hozzá kell rendelni egy regisztrációs programprofilt.

>[!NOTE]
>A profilokhoz sorozatszámok is hozzárendelhetők az **Apple-sorozatszámok** panelen.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon egy tokent a listából.
2. Válassza az **Eszközök** lehetőséget, válasszon eszközöket a listából, majd válassza a **Profil hozzárendelése** elemet.
3. A **Profil hozzárendelése** területen válasszon egy profilt az eszközökhöz, majd válassza a **Hozzárendelés** lehetőséget.

### <a name="assign-a-default-profile"></a>Alapértelmezett profil hozzárendelése

Választhat egy alapértelmezett profilt, amelyet a rendszer az adott tokennel regisztráló összes eszközre alkalmaz.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon egy tokent a listából.
2. Válassza az **Alapértelmezett profil beállítása** lehetőséget, válasszon egy profilt a legördülő listából, majd válassza a **Mentés** lehetőséget. A választott profil alkalmazva lesz az adott tokennel regisztráló összes eszközre.

## <a name="distribute-devices"></a>Eszközök terjesztése
Az eddigiekben engedélyezte az eszközfelügyeletet és a szinkronizálást az Apple és az Intune között, valamint a DEP-eszközök regisztrálása céljából hozzárendelt egy profilt. Az eszközök ekkor már kioszthatók a felhasználóknak. Felhasználói affinitással rendelkező eszközök esetén minden felhasználóhoz hozzá kell rendelni egy Intune-licencet. A felhasználói affinitás nélküli eszközökhöz licenc szükséges. Az aktivált eszköz nem tud beléptetési profilt alkalmazni, amíg az eszköz nem törlődik.

Lásd: [iOS-eszköz regisztrálása az Intune-ban a Készülékregisztrációs programmal](/intune-user-help/enroll-your-device-dep-ios).

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
