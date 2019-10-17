---
title: Oktatóanyag – az Apple Business Manager vagy a Készülékregisztrációs program használata iOS-eszközök Intune-beli regisztrálásához
titleSuffix: Microsoft Intune
description: Ebben az oktatóanyagban be fogja állítani az Apple vállalati eszközök regisztrálási funkcióit az ABM-ből az iOS-eszközök Intune-ban való regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83a9467065bb5c1d1cde2035df936541bb804ddc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503082"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>Oktatóanyag: az Apple Business Manager (ABM) vállalati eszközök beléptetési funkcióinak használata az iOS-eszközök Intune-beli regisztrálásához
Az Apple Business Manager eszköz-beléptetési funkciói leegyszerűsítik az eszközök regisztrálását. Az Intune támogatja az Apple régebbi Készülékregisztrációs program (DEP) portálját is, de javasoljuk, hogy az Apple Business Managerrel frissen kezdjen. Az Microsoft Intune és az Apple vállalati eszközök regisztrálásával az eszközök automatikusan biztonságosan lesznek regisztrálva, amikor a felhasználó első alkalommal bekapcsolja az eszközt. Az eszközöket tehát számos felhasználónak is kiszállíthatja anélkül, hogy az egyes eszközöket külön kell beállítania. 

Az oktatóanyag segítségével megtanulhatja a következőket:
> [!div class="checklist"]
> * Apple-eszközök regisztrálási jogkivonatának beszerzése
> * Felügyelt eszközök szinkronizálása az Intune-nal
> * Beléptetési profil létrehozása
> * A beléptetési profil kiosztása az eszközökhöz

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
- Az [Apple Business Managerben](https://business.apple.com) vagy az [Apple Készülékregisztrációs programban](http://deploy.apple.com) megvásárolt eszközök
- A [mobileszköz-kezelő szolgáltató](../fundamentals/mdm-authority-set.md) beállítása
- [Apple Mdm push-tanúsítvány](apple-mdm-push-certificate-get.md) beszerzése

## <a name="get-an-apple-device-enrollment-token"></a>Apple-eszközök regisztrálási jogkivonatának beszerzése
Az iOS-eszközöknek az Apple vállalati beléptetési funkcióival való regisztrálása előtt Apple Device beléptetési jogkivonat-(. PEM) fájlra van szükség. Ez a token lehetővé teszi, hogy az Intune szinkronizálja a vállalat tulajdonában lévő Apple-eszközökre vonatkozó információkat. Azt is engedélyezi, hogy az Intune regisztrációs profilokat töltsön fel az Apple számára, és eszközöket rendeljen ezen profilokhoz.

Az ABM vagy a DEP portál használatával hozzon létre egy eszköz-beléptetési jogkivonatot. A portálok segítségével eszközöket rendelhet hozzá az Intune-hoz a felügyelethez.

1. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > **Hozzáadás** elemet.

2. Engedélyezze a Microsoftnak az **Elfogadom** lehetőség választásával a felhasználó- és eszközadatok Apple-nek való elküldését.

   ![Képernyőkép – A Készülékregisztrációs program tokenje panel az Apple tanúsítványok munkaterületen – nyilvános kulcs letöltése.](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Kattintson a **Nyilvános kulcs letöltése** elemre a titkosításikulcs-fájl (.pem) letöltéséhez és helyi mentéséhez. A. PEM-fájl egy megbízhatósági kapcsolati tanúsítvány igénylésére szolgál az ABM vagy a DEP portálról.

4. A **Token létrehozása az Apple Készülékregisztrációs programjában** elemre kattintva nyissa meg az Apple Központi Telepítési Program portálját, és jelentkezzen be a cége Apple-azonosítójával. A későbbiekben ezt az Apple ID-t használhatja a DEP-token megújításához.

5. Az Apple [Központi Telepítési Program portálján ](https://deploy.apple.com) válassza a**Készülékregisztrációs program** **Első lépések** elemét. Előfordulhat, hogy a folyamat némileg eltér az [Apple Business Manager](https://business.apple.com)következő lépéseivel.

4. A **Kiszolgálók kezelése** lapon válassza az **MDM-kiszolgáló hozzáadása** lehetőséget.

5. A **Mdm-kiszolgáló neve**mezőbe írja be a *TestMDMServer* nevet, majd válassza a **tovább**lehetőséget. A kiszolgálónév Önnek segít a mobileszköz-felügyeleti (MDM-) kiszolgáló azonosításában, Nem a Microsoft Intune-kiszolgáló nevét vagy URL-címét adja meg.

6. Megjelenik a **Hozzáadás:&lt;Kiszolgálónév&gt;** párbeszédablak, és kéri **a nyilvános kulcs feltöltését**. Válassza a **fájl kiválasztása...** lehetőséget. a .pem-fájl feltöltéséhez, majd válassza a **Next** (Tovább) lehetőséget.

6. Lépjen az **üzembe helyezési programok** > **Készülékregisztrációs program** > **eszközök kezelése**.
7. Az **eszközök kiválasztása a**alapján területen válassza a **sorozatszám**elemet. <!--ask Tiffany about this-->

8. A **Választott tevékenység** területen jelölje ki a **Hozzárendelés kiszolgálóhoz** elemet, válassza Microsoft Intune-hoz megadott &lt;Kiszolgálónevet&gt;, majd kattintson az **OK** gombra. Az Apple-portál az Intune-kiszolgálóhoz rendeli a megadott eszközök kezelését, majd megjeleníti a **Hozzárendelés kész** üzenetet.

   Az Apple-portál **Központi telepítési programok** &gt; **Készülékregisztrációs program** &gt; **Hozzárendelési előzmények** menüpontjában jeleníthető meg az eszközök és a hozzájuk tartozó MDM-kiszolgálók listája.

9. A későbbiekben a Azure Portal Intune-ban adja meg a jogkivonat létrehozásához használt Apple ID-t.

    ![Képernyőkép – A DEP-token létrehozásához használt Apple ID megadása és a DEP-token megkeresése.](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. Az **Apple-token** mezőben keresse meg tallózással a tanúsítványfájlt (.pem), és válassza a **Megnyitás**, majd a **Létrehozás** lehetőséget. 

11. Ha hatókör-címkéket kíván alkalmazni, hogy korlátozza, mely rendszergazdák férhetnek hozzá ehhez a jogkivonathoz, válassza a hatókörök lehetőséget.

## <a name="create-an-apple-enrollment-profile"></a>Az Apple-regisztrációs profil létrehozása
Most, hogy telepítette a jogkivonatot, létrehozhat egy regisztrációs profilt a vállalat által birtokolt iOS-eszközökhöz. A regisztrálás során az eszközök csoportjára alkalmazott beállításokat egy készülékregisztrációs profil határozza meg.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** elemet.

2. Válassza ki az imént telepített jogkivonatot, válassza a **profilok** > **profil létrehozása**lehetőséget.

3. A **profil létrehozása**területen adja meg a *TestDEPProfile* **nevet** és *tesztelési DEP-t iOS-eszközökhöz* a **leíráshoz**. Ezeket a felhasználók nem fogják látni.

4. Válassza az **iOS** lehetőséget a **platform**területen.

5. Döntse el, hogy az eszközöket **felhasználói affinitással**vagy anélkül szeretné-e regisztrálni. A felhasználói affinitás olyan eszközökhöz lett tervezve, amelyeket az adott felhasználók használni fognak. Ha a felhasználók a Céges portál szeretnék használni olyan szolgáltatásokhoz, mint például az alkalmazások telepítése, válassza a **regisztráció felhasználói affinitással**lehetőséget. Ha a felhasználóknak nincs szükségük a Céges portálre, vagy sok felhasználó számára szeretné kiépíteni az eszközt, válassza a **regisztráció felhasználói affinitás nélkül**lehetőséget.

6. Ha a felhasználói affinitással való regisztrációt választotta, állapítsa meg, hogy szeretné-e hitelesíteni a Céges portál vagy az Apple beállítási asszisztensét. Ha a Multi-Factor Authenticationt szeretné használni, engedélyezze a felhasználók számára az első bejelentkezéskor a jelszavak módosítását, vagy kérje meg a felhasználókat, hogy a regisztráció során visszaállítsák a lejárt jelszavukat, és válassza az **Igen** lehetőséget **a hitelesítés az céges portál helyett beállításnál Asszisztens**. Ha az Apple beállítási asszisztense révén kényelmes, alapszintű HTTP-hitelesítést használ, válassza a **nem**lehetőséget.

7. Ha a felhasználói affinitással való regisztrációt és a Céges portál hitelesítését választotta, állapítsa meg, hogy szeretné-e telepíteni a Céges portált az Apple Volume Purchase program (VPP) használatával. Ha VPP-tokenrel telepíti a Céges portál, a felhasználónak nem kell megadnia az Apple ID azonosítót és a jelszót, hogy a regisztráció során letöltse a Céges portál az App Store áruházból. Válassza a **token használata:** a **céges portál a VPP** használatával lehetőséget, és válassza ki azt a VPP-tokent, amely ingyenes licenccel rendelkezik a céges portál elérhető. Ha nem szeretné a VPP-t használni a Céges portál üzembe helyezéséhez, válassza a **ne használja** a VPP-t a **VPP céges portál telepítése**alatt. 

8. Ha a felhasználói affinitással való regisztrációt választotta, a hitelesítést a Céges portál használatával végzi el, és a VPP használatával telepíti a Céges portált, döntse el, hogy az Céges portált egyetlen alkalmazás módban szeretné-e futtatni a hitelesítésig. Ezzel a beállítással biztosíthatja, hogy a felhasználó ne férhessen hozzá más alkalmazásokhoz, amíg el nem végezte a vállalati beléptetést. Ha korlátozni szeretné a felhasználót erre a folyamatra, amíg a regisztráció be nem fejeződik, válassza az **Igen** lehetőséget a **Futtatás céges portál alatt egyetlen alkalmazás módban a hitelesítésig**. 

9. Válassza az **eszközkezelés beállítások** lehetőséget, és válassza az **Igen** lehetőséget a **felügyelt**elemnél. A felügyelt eszközök a legtöbb felügyeleti lehetőséget biztosítanak a vállalati iOS-eszközökhöz.

10. A **zárolt regisztráció** területen válassza az **Igen** lehetőséget annak biztosítása érdekében, hogy a felhasználók ne tudják eltávolítani a vállalati eszköz felügyeletét. 

11. Válasszon egy beállítást a **számítógépek szinkronizálása** lehetőséggel annak megállapításához, hogy az iOS-eszközök képesek-e a számítógépekkel való szinkronizálásra.

12. Alapértelmezés szerint az Apple az eszköz típusával (pl. iPad) nevezi az eszközt. Ha másik nevet szeretne megadni, válassza az **Igen** lehetőséget az **eszköznév alkalmazása sablonban**. Adja meg az eszközökre alkalmazni kívánt nevet, ahol a (z) *{{Serial}}* és *{{DeviceType}}* karakterláncok az egyes eszközök sorozatszámát és típusát is helyettesítik. Ellenkező esetben válassza a **nem** lehetőséget az **eszköznév sablon alkalmazása**elemnél.

13. Válassza az **OK** gombot.

14. Válassza a **beállítási asszisztens testreszabása** lehetőséget, és írja be az *oktatóanyag részleg* **nevet a részlegnek**. Ez a karakterlánc azt ismerteti, hogy a felhasználók Mikor koppintanak **a konfigurációra az** eszköz aktiválása során.

15. A **részleg telefonszáma**területen adjon meg egy telefonszámot. Ez a szám akkor jelenik meg, ha a felhasználók az aktiválás során a **segítségre van szükségük** gombra koppintanak.

16. Az eszköz aktiválása során különböző képernyőket jeleníthet meg vagy **rejtheti** **el.** A legzökkenőmentesebb regisztrációs élmény érdekében az összes képernyőt **elrejtve**állítsa be.

17. Válassza az **OK** > **Létrehozás** lehetőségeket.

## <a name="sync-managed-devices-to-intune"></a>Felügyelt eszközök szinkronizálása az Intune-nal

Miután beállította az ABM-, ASM-vagy DEP-portálon a beléptetési program tokenjét, és hozzárendelt eszközöket a MDM-kiszolgálóhoz, megvárhatja, hogy ezek az eszközök szinkronizálva legyenek az Intune szolgáltatással, vagy manuálisan is leküldhetik a szinkronizálást. Manuális szinkronizálás nélkül az eszközök akár 24 órát is igénybe vehetnek, hogy megjelenjenek a Azure Portal.

1. A Azure Portal Intune-ban válassza az eszközök **beléptetése @no__t-** 1**Apple-regisztráció** > **beléptetési program jogkivonatok** elemet > Válassza ki a tokent a listában > **eszközök** > **szinkronizálás**lehetőséget.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Regisztrációs profil kiosztása iOS-eszközökhöz

Ahhoz, hogy egy eszközt regisztrálni lehessen, először hozzá kell rendelni egy regisztrációs programprofilt. Ezek az eszközök az Apple-től szinkronizálva vannak az Intune-nal, és hozzá kell rendelni a megfelelő MDM-kiszolgálói jogkivonathoz az ABM, ASM vagy DEP portálon.

1. Az Intune-ban a Azure Portal válassza az **eszközök**beléptetése  > **Apple-regisztráció** > **beléptetési programbeli tokenek** > Válassza ki a tokent a listában.
2. Válassza az **Eszközök** lehetőséget, válasszon eszközöket a listából, majd válassza a **Profil hozzárendelése** elemet.
3. A **Profil hozzárendelése** területen válasszon egy profilt az eszközökhöz, majd válassza a **Hozzárendelés** lehetőséget.

## <a name="distribute-devices-to-users"></a>Eszközök terjesztése a felhasználóknak

Beállította a felügyeletet és a szinkronizálást az Apple és az Intune között, és hozzárendelt egy profilt, amely lehetővé teszi a DEP-eszközök regisztrálását. Az eszközök ekkor már kioszthatók a felhasználóknak. Felhasználói affinitással rendelkező eszközök esetén minden felhasználóhoz hozzá kell rendelni egy Intune-licencet.

## <a name="next-steps"></a>További lépések

További információ az iOS-eszközök regisztrálásához használható egyéb lehetőségekről.

> [!div class="nextstepaction"]
> [Részletes, iOS-es DEP-regisztrációval foglalkozó cikk](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
