---
title: Apple mennyiségi licencszerződés keretében vásárolt alkalmazások kezelése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan szinkronizálhatja az iOS-es és macOS-es alkalmazás-áruházból mennyiségi programban vásárolt alkalmazásokat a Microsoft Intuneba, majd kezelheti és nyomon követheti a használatot.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff9a37a1dd815b6ec9d7522604796310e7f0b5ce
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984106"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>A Apple Volume Purchase Program használatával vásárolt iOS-és macOS-alkalmazások kezelése Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Apple lehetővé teszi, hogy több licencet is vásároljon egy olyan alkalmazáshoz, amelyet a vállalatnál szeretne futtatni iOS-és macOS-eszközökön. Több licenc vásárlásával hatékonyabban kezelhetők a vállalaton belüli alkalmazások.

A Microsoft Intune segítséget nyújt az ilyen program keretében vásárolt alkalmazások több példányának kezelésében a következő módon:

- Licencinformációk jelentése az App Store-ból.
- A felhasznált licencek számának nyilvántartása.
- Annak megakadályozása, hogy több példányt telepítsen az alkalmazásból, mint amennyit vásárolt.

A mennyiségi programban vásárolt alkalmazásokat kétféle módszerrel lehet hozzárendelni:

## <a name="device-licensing"></a>Eszközlicencelés

Ha eszközhöz rendeli az alkalmazást, egyetlen alkalmazáslicenc lesz használatban, továbbra is ahhoz az eszközhöz társítva, amelyhez hozzárendelte.

Ha mennyiségi programban vásárolt alkalmazásokat rendel az eszközhöz, a végfelhasználónak nem kell Apple ID azonosítót megadnia az áruházhoz való hozzáféréshez.

## <a name="user-licensing"></a>Felhasználói licencelés

Ha felhasználóhoz rendeli az alkalmazást, egyetlen alkalmazáslicenc lesz használatban, a felhasználóhoz társítva. Az alkalmazás legfeljebb 5, a felhasználó tulajdonában lévő eszközön futtatható (az eszköz korlátját az Apple vezérli).

Ha mennyiségi programban vásárolt alkalmazásokat rendel felhasználókhoz, minden végfelhasználónak érvényes, egyedi Apple ID azonosítóval kell rendelkeznie az App Store-hoz való hozzáféréshez.

Emellett szinkronizálhatja, kezelheti és hozzárendelheti az Apple Volume Purchase program (VPP) áruházban vásárolt könyveket iOS-eszközökre. További információkat a [Mennyiségi vásárlási program keretében vásárolt iOS-es e-könyvek kezelése](vpp-ebooks-ios.md) című cikkben talál.

## <a name="manage-volume-purchased-apps-for-ios-and-macos-devices"></a>Mennyiségi programban vásárolt alkalmazások felügyelete iOS-és macOS-eszközökhöz

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps"></a>A Apple Volume Purchase Program mennyiségi programban vásárolt alkalmazások támogatása

Több licencet vásárolhat az iOS-és macOS-alkalmazásokhoz az [üzleti Apple Volume Purchase program](https://www.apple.com/business/vpp/) vagy az [oktatási Apple Volume Purchase program](https://volume.itunes.apple.com/us/store). Ez az eljárás magában fogalja Apple VPP-fiók beállítását az Apple webhelyén, és az Apple VPP-token feltöltését az Intune-ba.  Ezután szinkronizálhatja a mennyiségi vásárlás adatait az Intune-nal, és nyomon követheti a mennyiségi programban vásárolt alkalmazás használatát.

### <a name="supports-business-to-business-volume-purchased-apps"></a>A vállalatok közötti mennyiségi programban vásárolt alkalmazások támogatása

Emellett a harmadik féltől származó fejlesztők is magánjellegű módon terjeszthetik az alkalmazásokat az App Store-ban meghatározott, az alkalmazásokhoz tartozó, jóváhagyott mennyiségi vásárlási programba. Ezek a VPP for Business-tagok be tudnak jelentkezni a Volume Purchase Program App Store áruházba, és ott meg tudják venni azokat az alkalmazásokat, amelyekre szükségük van. A végfelhasználók által a VPP for Business keretében megvásárolt alkalmazások Intune-bérlőikkel szinkronizálják magukat.

## <a name="before-you-start"></a>Előkészületek
Mielőtt hozzálát, be kell szereznie a VPP-tokent az Apple-től, és fel kell töltenie azt az Intune-fiókjába. Ezenkívül tisztában kell lennie a következő feltételekkel:

* Intune-fiókjához több VPP-tokent is társíthat.
* Ha korábban VPP-tokent használt egy másik termékkel, egy újat kell létrehoznia az Intune használatához.
* A tokenek egy évig érvényesek.
* Alapértelmezés szerint az Intune naponta kétszer szinkronizál az Apple VPP szolgáltatással. Manuális szinkronizálás bármikor kezdeményezhető.
* Mielőtt az Apple VPP-t az Intune-nal kezdené használni, távolítsa el a más mobileszköz-felügyeleti (MDM) megoldás használatával létrehozott összes meglévő VPP-felhasználói fiókot. Az Intune biztonsági okokból nem szinkronizálja ezeket a felhasználói fiókokat az Intune-ba. Az Intune csak az Intune által létrehozott adatokat szinkronizálja az Apple VPP szolgáltatásból.
* Az Apple készülékregisztrációs profil (DEP) program automatizálja a mobileszközök felügyeleti célú regisztrációját (MDM regisztrációját). A készülékregisztrációs profilt használva a vállalati eszközöket kézbevétel nélkül is be tudja állítani. A DEP programba ugyanazzal a programügynök-fiókkal tud regisztrálni, mint amit az Apple VPP-hez használt. Az [Apple Központi Telepítési Program](https://deploy.apple.com) oldalon felsorolt valamennyi program egyedi azonosítóval rendelkezik, amellyel nem lehet bejelentkezni az olyan Apple-szolgáltatásokba, mint amilyen például az iTunes áruház.
* Ha felhasználólicencelési modellel rendel hozzá VPP-alkalmazásokat a felhasználókhoz vagy eszközökhöz (felhasználói affinitással), minden egyes Intune-felhasználót társítani kell egy egyedi Apple ID-vel vagy egy e-mail-címmel, amikor az eszközükön elfogadják az Apple használati feltételeit.
* Amikor beállít egy eszközt egy új Intune-felhasználó számára, konfigurálja azt a felhasználó egyedi Apple ID-jével vagy e-mail-címével. Az Apple ID vagy e-mail-cím és az Intune-felhasználó egyedi párt alkot, amely akár öt eszközön használható.
* A VPP-token használata egyszerre csak egy Intune-fiókban támogatott. Nem használja újra ugyanazt a VPP-tokent több Intune-bérlőhöz.

>[!IMPORTANT]
>Miután a VPP-tokent az Intune-ba importálta, ne importálja ugyanezt a tokent egy másik eszközfelügyeleti megoldásba. Ez a licenc-hozzárendelések és a felhasználói rekordok elvesztését eredményezheti.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP-token beszerzése és feltöltése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **ügyfélalkalmazások** > **Apple VPP-tokenek** elemet a **beállítás**alatt.
4. A VPP-tokenek panel listájában válassza a **Létrehozás** elemet.
5. Az **VPP-token Létrehozása** panelen adja meg az alábbi adatokat:
    - **VPP-jogkivonatfájl** – Ha még nem tette meg, iratkozzon fel a vállalati Volume Purchase Programra vagy az oktatási programra. A regisztrációt követően töltse le a fiókjához tartozó Apple VPP-tokent, és itt jelölje ki.
    - **Apple ID** – Adja meg a mennyiségi vásárlási programhoz kapcsolódó fiók Apple ID-ját.
    - A **token vezérlése egy másik Mdm** – ez a beállítás **Igen** értékre állítja a token hozzárendelését az Intune-hoz egy másik Mdm.
    - **Jogkivonat neve** – a jogkivonat nevének beállítására szolgáló felügyeleti mező.    
    - **Ország/régió** – válassza ki a VPP ország/régió tárolót.  Az Intune az adott VPP ország/régió tárolóban lévő összes területi beállításhoz a VPP-alkalmazásokat szinkronizálja.
        > [!WARNING]  
        > Az ország/régió módosítása frissíti az alkalmazások metaadatait és az áruházbeli URL-címet a következő szinkronizáláskor a tokenrel létrehozott alkalmazások Apple szolgáltatásával. Az alkalmazás nem frissül, ha nem létezik az új ország/régió tárolóban.

    - **VPP-fiók típusa** –A következő lehetőségek közül választhat: **Üzlet** és **Oktatás**.
    - **Alkalmazások automatikus frissítése** – Az automatikus frissítés engedélyezéséhez válasszon a **Be** és **Ki** érték közül. Engedélyezés esetén az Intune észleli, ha az alkalmazás-áruházban az adott VPP-alkalmazáshoz frissítés érhető el, és az eszköz legközelebbi bejelentkezésekor automatikusan leküldi a frissítéseket az eszközre. Az Apple VPP automatikus alkalmazásfrissítései csak a **Kötelező** telepítési szándékkal üzembe helyezett alkalmazásokat frissítik automatikusan. Az **elérhető** telepítési szándéktal telepített alkalmazások esetében az automatikus frissítés állapotjelző üzenetet hoz létre a rendszergazda számára, amely tájékoztatja, hogy az alkalmazás új verziója érhető el. Az állapotjelző üzenet az alkalmazás kiválasztásával, az eszköz telepítési állapotának kiválasztásával és az állapot részleteinek ellenőrzésével tekinthető meg. Emellett a felhasználó a Céges portálon nem telepítettként látja az alkalmazást, annak ellenére, hogy annak régebbi verziója telepítve van. Ebben az esetben a felhasználó újratelepítheti az alkalmazást, ha az alkalmazás újabb verzióját szeretné telepíteni a Céges portál alkalmazás részletek képernyőjén a **telepítés** gombra kattintva.

        > [!NOTE]
        > Az alkalmazások automatikus frissítései mind az eszköz, mind a felhasználó által licencelt, iOS 11,0-es, illetve macOS 10,12-es és újabb verziójú alkalmazások esetében működnek.

    - **Engedélyezem a Microsoft számára, hogy a felhasználók és az eszközök adatait is el lehessen küldeni az Apple-nek.** – **Válassza az Elfogadom** lehetőséget a folytatáshoz. Az Apple-nek küldött Microisoft áttekintését lásd: az [Intune által az Apple](~/protect/data-intune-sends-to-apple.md)-nek küldött adatokat.

6. Amikor elkészült, válassza a **Létrehozás** gombot.

A token a jogkivonatok panel listájában jelenik meg.

Az Apple által tárolt adatok bármikor szinkronizálhatók az Intune-nal a **Szinkronizálás** lehetőség kiválasztásával.

## <a name="to-assign-a-volume-purchased-app"></a>Mennyiségi programban vásárolt alkalmazás hozzárendelése

1. Az **Intune** ablaktáblán válassza az **Eszközalkalmazások** > **Alkalmazások** elemet a **Kezelés** lehetőség alatt.
2. Az alkalmazáslista paneljén válassza ki a hozzárendelni kívánt alkalmazást, és válassza a **Hozzárendelés** lehetőséget.
3. Az ***Alkalmazás neve*** - **Hozzárendelések** panelen kattintson a **Csoport hozzáadása** elemre, majd a **Csoport hozzáadása** panelen válasszon egy **hozzárendelés-típust** és azokat az Azure AD-beli felhasználói vagy eszközcsoportokat, amelyekhez hozzá kívánja rendelni az alkalmazást.
5. Minden kijelölt csoporthoz válassza ki az alábbi beállításokat:
    - **Típus** – Határozza meg, hogy az alkalmazás **Elérhető**, azaz a végfelhasználók telepíthetik a Céges portálról, vagy **Kötelező**, azaz a végfelhasználók automatikusan megkapják az telepített alkalmazást.
    - **Licenc típusa** – Válassza a **Felhasználói licencelés** vagy az **Eszközlicencelés** lehetőséget.
6. Ha elkészült, válassza a **Mentés** elemet.


>[!NOTE]
>Az elérhető üzembe helyezési szándék nem támogatott az eszközök csoportjai esetében, csak a felhasználói csoportok támogatottak. A megjelenített alkalmazások listája egy tokenhez van társítva. Ha van egy olyan alkalmazása, amely több VPP-tokenhez is társítva van, akkor ugyanaz az alkalmazás többször is megjelenik; minden tokenhez egyszer.

## <a name="end-user-prompts-for-vpp"></a>VPP-figyelmeztetés a végfelhasználónak

A végfelhasználó különféle helyzetekben figyelmeztetést fog kapni VPP-alkalmazások telepítésére. A különféle feltételek az alábbi táblázatban láthatók:

| # | Forgatókönyv                                | Meghívás az Apple VPP-programba                              | Figyelmeztetés alkalmazástelepítésre | Apple ID bekérése |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – licenccel rendelkező felhasználó                             | Y                                                                                               | Y                                           | Y                                 |
| 2 | Corp (Vállalat) – licenccel rendelkező felhasználó (nem felügyelt eszköz)     | Y                                                                                               | Y                                           | Y                                 |
| 3 | Corp (Vállalat) – licenccel rendelkező felhasználó (felügyelt eszköz)         | Y                                                                                               | N                                           | Y                                 |
| 4 | BYOD – licenccel rendelkező eszköz                           | N                                                                                               | Y                                           | N                                 |
| 5 | CORP (Vállalat) – licenccel rendelkező eszköz (nem felügyelt eszköz)                           | N                                                                                               | Y                                           | N                                 |
| 6 | CORP (Vállalat) – licenccel rendelkező eszköz (felügyelt eszköz)                           | N                                                                                               | N                                           | N                                 |
| 7 | Teljes képernyős mód (felügyelt eszköz) – licenccel rendelkező eszköz | N                                                                                               | N                                           | N                                 |
| 8 | Teljes képernyős mód (felügyelt eszköz) – licenccel rendelkező felhasználó   | --- | ---                                          | ---                                |

> [!Note]  
> VPP-alkalmazásokat nem ajánlott teljes képernyős eszközökhöz rendelni VPP-felhasználói licenceléssel.

## <a name="revoking-app-licenses"></a>Alkalmazás-licencek visszavonása

Egy adott eszköz, felhasználó vagy alkalmazás alapján visszavonhatja az összes kapcsolódó iOS-vagy macOS-alkalmazás licencét.  Az iOS-és macOS-platformok között azonban van néhány különbség. 

### <a name="revoking-app-licenses-on-ios"></a>Alkalmazás-licencek visszavonása iOS rendszeren
A felhasználókat értesítheti, amikor megszűnik az alkalmazás hozzájuk rendelése. Egy alkalmazás licencének visszavonása azonban nem fogja eltávolítani a kapcsolódó VPP-alkalmazást az eszközről. A VPP-alkalmazás eltávolításához és a felhasználóhoz vagy eszközhöz társított alkalmazáslicenc visszaszerzéséhez a hozzárendelési műveletet meg kell változtatnia **Eltávolítás** műveletre. Ha egy felhasználóhoz hozzárendelt alkalmazást eltávolít, az Intune visszaigényli a felhasználó vagy az eszköz licencét, és eltávolítja az alkalmazást az eszközről. A visszavont licencek száma látható lesz az Intune **Alkalmazások** tevékenységcsoportján belüli **Licencelt alkalmazások** csomóponton. Miután eltávolította a VPP-alkalmazást, és az alkalmazás licencét visszaigényelték, dönthet úgy, hogy hozzárendeli az alkalmazás licencét egy másik felhasználóhoz vagy eszközhöz.


### <a name="revoking-app-licenses-on-macos"></a>Alkalmazás-licencek visszavonása macOS rendszeren
Az alkalmazás licencének visszavonása nem távolítja el a VPP-alkalmazást az eszközről. Ha visszavon egy felhasználóhoz rendelt alkalmazás-licencet, az Intune visszaállítja a felhasználó vagy az eszköz licencét. A visszavont licenccel rendelkező macOS-alkalmazás továbbra is használható az eszközön, de nem frissíthető, amíg a licencet nem rendeli hozzá a felhasználóhoz vagy eszközhöz. Az Apple szerint az ilyen alkalmazásokat egy 30 napos türelmi időszak után távolítja el a rendszer. Az Apple azonban nem biztosít olyan eszközt, amellyel az Intune eltávolíthatja az alkalmazást az **eltávolítási** hozzárendelés művelettel. Azonban dönthet úgy is, hogy hozzárendeli a visszaigényelt alkalmazás licencét egy másik felhasználóhoz vagy eszközhöz.

>[!NOTE]
>Az Intune az iOS-és macOS-felhasználók licencelt VPP-alkalmazási licenceit is lekéri, ha egy alkalmazott elhagyja a vállalatot, és már nem része a HRE csoportnak.

## <a name="deleting-vpp-tokens"></a>VPP-tokenek törlése
<!-- 820879 -->  
Az Apple Volume beszerzési program (VPP) tokenjét a-konzol használatával törölheti. Ez akkor lehet szükséges, ha egy VPP-token több példányban van meg. A token törlésével a kapcsolódó alkalmazásokat és hozzárendelést is törli. A token törlésével azonban nem vonja vissza az alkalmazáslicenceket, és nem töröl alkalmazásokat. 

>[!NOTE]
>Az Intune a token törlése után már nem tudja visszavonni az alkalmazáslicenceket. 

<!-- 820870 -->  
Ha egy VPP-token összes VPP-alkalmazásának licenceit törölni szeretné, először vissza kell vonnia a tokenhez társított összes alkalmazáslicencet, majd törölnie kell a tokent.

## <a name="renewing-app-licenses"></a>Alkalmazáslicencek megújítása

Az Apple VPP-jogkivonat megújításához töltsön le egy új jogkivonatot az Apple mennyiségi vásárlási programjának portáljáról, és frissítse az Intune-ban a meglévő jogkivonatot.

## <a name="deleting-a-vpp-app"></a>VPP-alkalmazás törlése

Jelenleg az iOS VPP-alkalmazások nem törölhetők a Microsoft Intune-ból.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Egyéni szerepkör-engedélyek kiosztása VPP-hez

Az Apple VPP-tokenekhez és VPP-alkalmazásokhoz való hozzáférés az Intune-ban egyéni rendszergazdai szerepkörökhöz hozzárendelt engedélyektől függetlenül is szabályozható.

* Ha engedélyezni szeretné, hogy az Intune egyéni szerepköre kezelhesse az Apple VPP-tokeneket az **ügyfélalkalmazások** > **Apple VPP-tokenek**alatt, rendeljen engedélyeket a **felügyelt alkalmazásokhoz**.
* Ha engedélyezni szeretné az Intune egyéni szerepkörét az iOS VPP-tokenekkel vásárolt alkalmazások kezeléséhez az **ügyfélalkalmazások** > **alkalmazásokban**, rendeljen engedélyeket a **Mobile apps**szolgáltatáshoz. 

## <a name="additional-information"></a>További információ

Amikor egy jogosult eszközzel rendelkező felhasználó először próbál VPP-alkalmazást telepíteni egy eszközön, a rendszer megkéri, hogy csatlakozzon az Apple Volume Purchase Programhoz. Még az alkalmazás telepítésének folytatása előtt csatlakozniuk kell. Az Apple Volume Purchase programhoz való csatlakozás meghívása megköveteli, hogy a felhasználó használhassa az App Store alkalmazást az iOS-vagy macOS-eszközön. Ha beállított egy szabályzatot az App Store-alkalmazás letiltásához, a VPP-alkalmazások felhasználói alapú licencelése nem működik. A megoldás az, hogy engedélyezi az App Store-alkalmazás számára a szabályzat eltávolítását vagy az eszközökön alapuló licencelés használatát.

Az Apple közvetlen segítséget biztosít a VPP-tokenek létrehozásához és megújításához. További információkért lásd a [Tartalomterjesztés a felhasználók felé a Mennyiségi vásárlási program (VPP) segítségével](https://go.microsoft.com/fwlink/?linkid=2014661) című részt az Apple dokumentációjában. 

Ha az Intune portálján a **Külső MDM-hez rendelve** beállítás látható, a VPP-token Intune-beli használata előtt a rendszergazdának el kell távolítania a VPP-tokent a harmadik félhez tartozó MDM-ről.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Mennyi ideig tart, mire a portál frissíti a licencszámot egy alkalmazás telepítése vagy az eszközről való eltávolítása után?
A licenc néhány órával az alkalmazások telepítése vagy eltávolítása után frissül. Megjegyzés: Ha a végfelhasználó eltávolítja az alkalmazást, a licenc továbbra is a felhasználóhoz vagy az eszközhöz lesz rendelve.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Túlléphető egy alkalmazáselőfizetés? Ha igen, milyen körülmények között?
Igen. Az Intune rendszergazdája túllépheti az alkalmazáselőfizetéseket. Ha például a rendszergazda 100 licencet vásárol XYZ alkalmazáshoz, majd egy 500 tagú csoporthoz rendeli azt. Az első 100 tag (felhasználó vagy eszköz) megkapja a licencet, a többi taghoz azonban nem lesz hozzárendelve licenc.

### <a name="how-frequently-does-intune-sync-vpp-tokens-with-apple"></a>Milyen gyakran szinkronizálja az Intune a VPP-tokeneket az Apple-szel?
Az Intune naponta kétszer szinkronizálja a VPP-tokeneket és-licenceket az Apple-szel. Az Intune-rendszergazda az **ügyfélalkalmazások** > **Apple VPP-tokenek**alatt manuális szinkronizálást indíthat.

## <a name="next-steps"></a>További lépések

Lásd [az alkalmazások figyelésével](apps-monitor.md) foglalkozó útmutatót, amely az alkalmazás-hozzárendelések figyeléséhez nyújt segítséget.
