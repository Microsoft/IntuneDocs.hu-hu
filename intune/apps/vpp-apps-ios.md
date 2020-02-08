---
title: Apple mennyiségi licencszerződés keretében vásárolt alkalmazások kezelése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan szinkronizálhatja az iOS-es és macOS-es alkalmazás-áruházból mennyiségi programban vásárolt alkalmazásokat a Microsoft Intuneba, majd kezelheti és nyomon követheti a használatot.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
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
ms.openlocfilehash: d965ac35719d809ab922d28f76dec1754e9a4c6b
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051626"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>A Apple Volume Purchase Program használatával vásárolt iOS-és macOS-alkalmazások kezelése Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Apple segítségével több licencet vásárolhat egy olyan alkalmazáshoz, amelyet az [Apple Business Manager](https://business.apple.com/) vagy az [Apple School Manager](https://school.apple.com/)használatával iOS-és MacOS-eszközökön kíván használni a szervezetben. Ezután szinkronizálhatja a mennyiségi vásárlás adatait az Intune-nal, és nyomon követheti a mennyiségi programban vásárolt alkalmazás használatát. Az alkalmazás-licencek megvásárlásával hatékonyan kezelheti a vállalaton belüli alkalmazásokat, és megőrizheti a megvásárolt alkalmazások tulajdonjogát és felügyeletét. 

A Microsoft Intune a program keretében vásárolt alkalmazások kezelésében nyújt segítséget:

- Az Apple Business Managerből letöltött hely tokenek szinkronizálása.
- Nyomon követheti, hogy hány licenc áll rendelkezésre, és hogyan lettek használva a megvásárolt alkalmazásokhoz.
- Az alkalmazások telepítésének segítése a saját licencek számától függetlenül.

Emellett szinkronizálhatja, kezelheti és hozzárendelheti az Apple Business Managerben vásárolt könyveket az Intune-ból iOS-eszközökre. További információkat a [Mennyiségi vásárlási program keretében vásárolt iOS-es e-könyvek kezelése](vpp-ebooks-ios.md) című cikkben talál.

## <a name="what-are-location-tokens"></a>Mik azok a helyek jogkivonatai?
A hely jogkivonatait Volume Purchase program-(VPP-) tokeneknek is nevezzük. Ezek a tokenek az Apple Business Manager használatával megvásárolt licencek hozzárendelésére és kezelésére szolgálnak. A tartalomkezelők a licenceket olyan tartózkodási jogkivonatokkal vásárolhatják meg és társítják, amelyekhez engedélyük van az Apple Business Managerben. A rendszer ezután letölti az Apple Business Managerből a hely jogkivonatait, és feltölti Microsoft Intune. Microsoft Intune támogatja a több helyre vonatkozó tokenek feltöltését a bérlőn. A tokenek egy évig érvényesek.

## <a name="how-are-purchased-apps-licensed"></a>Hogyan történik a megvásárolt alkalmazások licencelése?
A megvásárolt alkalmazások az Apple által az iOS-és macOS-eszközökhöz kínált két típusú licenccel rendelkező csoportokhoz rendelhetők.

|   | Eszköz licencelése | Felhasználói licencelés |
|-----|------------------|----------------|
| **App Store-bejelentkezés** | Nem kötelező. | Minden végfelhasználónak egyedi Apple ID azonosítót kell használnia, amikor a rendszer kéri, hogy jelentkezzen be az App Store-ba. |
| **Az eszköz konfigurációja blokkolja az App Store-hoz való hozzáférést** | Az alkalmazások Céges portál használatával telepíthetők és frissíthetők. | Az Apple VPP-hez való csatlakozás meghívásához hozzáféréssel kell rendelkeznie az App Store-hoz. Ha az App Store letiltására vonatkozó szabályzatot állított be, a VPP-alkalmazások felhasználói licencelése nem fog működni. |
| **Alkalmazás automatikus frissítése** | Ahogy az Intune-rendszergazda konfigurálja az Apple VPP-token beállításaiban, ahol az alkalmazás **hozzárendelési típusa** **szükséges**. <br> <br> Ha a **hozzárendelés típusa** **regisztrált eszközökhöz érhető el**, az elérhető alkalmazások frissítései a céges portálból telepíthetők. | A végfelhasználó által a személyes App Store-ban konfigurált beállítások szerint. Ezt nem lehet az Intune-rendszergazda felügyelni. |
| **Felhasználó beléptetése** | Nem támogatott. | Felügyelt Apple-azonosítók használatával támogatott. |
| **Könyvek** | Nem támogatott. | Támogatott. |
| **Használatban lévő licencek** | 1 licenc eszközönként. A licenc társítva van az eszközhöz. | 1 licenc legfeljebb 5 eszközhöz ugyanazzal a személyes Apple ID azonosítóval. A licenc a felhasználóhoz van társítva. <br> <br> A személyes Apple ID azonosítóval és az Intune-ban felügyelt Apple ID-vel társított végfelhasználók 2 alkalmazás-licencet használnak.|
| **Licenc áttelepítése** | Az alkalmazások csendesen telepíthetik a felhasználót az eszközre. | Az alkalmazások nem telepíthetők át az eszközről a felhasználói licencekre. |

> [!NOTE]  
> A Céges portál nem jeleníti meg az eszközök licencelt alkalmazásait a felhasználói beléptetési eszközökön, mert csak a felhasználó által licencelt alkalmazások telepíthetők a felhasználói beléptetési eszközökre.

## <a name="what-app-types-are-supported"></a>Milyen típusú alkalmazások támogatottak?
Az Apple Business Manager használatával nyilvános és privát alkalmazásokat is vásárolhat és terjeszthet.
- **Áruházbeli alkalmazások:** Az Apple Business Manager használatával a Content managerek az App Store áruházban elérhető ingyenes és fizetős alkalmazásokat is vásárolhatnak.
- **Egyéni alkalmazások:** Az Apple Business Manager használatával a Content managerek a szervezete számára elérhetővé tett egyéni alkalmazásokat is vásárolhatnak. Ezek az alkalmazások a szervezet konkrét igényeinek megfelelően vannak kialakítva olyan fejlesztők számára, akikkel közvetlenül dolgozik. További információ az [egyéni alkalmazások terjesztéséről](https://developer.apple.com/business/custom-apps/).

## <a name="prerequisites"></a>Előfeltételek
- Egy [Apple Business Manager](https://business.apple.com/) -vagy [Apple School Manager](https://school.apple.com/) -fiók a szervezet számára. 
- Egy vagy több hely jogkivonatához hozzárendelt alkalmazás-licencek megvásárlása. 
- Letöltött hely tokenek. 

> [!IMPORTANT]
> - A hely tokenje egyszerre csak egy eszközkezelés megoldással használható. Mielőtt elkezdi használni a megvásárolt alkalmazásokat az Intune-nal, vonja vissza és távolítsa el a más mobileszköz-felügyeleti (MDM) szolgáltató által használt meglévő hely jogkivonatokat. 
> - A hely jogkivonata csak egy Intune-bérlőn használható egyszerre. Ne használja ugyanazt a tokent több Intune-bérlőhöz.
> - Alapértelmezés szerint az Intune naponta kétszer szinkronizálja a hely jogkivonatait az Apple-szel. Az Intune-ból bármikor kezdeményezheti a manuális szinkronizálást.
> - Miután importálta a Location tokent az Intune-ba, ne importálja ugyanazt a jogkivonatot más eszközkezelés megoldásba. Ez a licenc-hozzárendelések és a felhasználói rekordok elvesztését eredményezheti.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Migrálás mennyiségi vásárlási programból (VPP) alkalmazások és könyvek számára
Ha a szervezete még nem lett migrálva az Apple Business Manager vagy az Apple School Manager alkalmazásba, tekintse át az [Apple útmutatását az alkalmazások és a könyvek áttelepítéséhez](https://support.apple.com/HT208257) , mielőtt továbblépne a beszerzett alkalmazások felügyeletére az Intune-ban.

> [!IMPORTANT]
> - A legjobb áttelepítési élmény érdekében helyenként csak egy VPP-vásárlót telepítsen át. Ha minden vásárló egy egyedi helyre kerül át, az összes licenc – hozzárendelt és hozzá nem rendelt – az alkalmazásokra és a könyvekre fog áttérni.
> - Ne törölje a meglévő örökölt VPP-tokent az Intune-ban, illetve a meglévő örökölt VPP-tokenhez társított alkalmazásokat és hozzárendeléseket. Ezeknek a műveleteknek minden alkalmazás-hozzárendelést újra létre kell hoznia az Intune-ban.

A meglévő megvásárolt VPP-tartalmak és-tokenek áttelepíthetők az Apple Business Managerben vagy az Apple School Managerben lévő alkalmazásokba és könyvekbe az alábbi módon:

1. Hívja meg a VPP-beszerzőket a szervezethez való csatlakozáshoz, és az egyes felhasználók számára, hogy egyedi helyet válasszon ki. 
2. A folytatás előtt győződjön meg arról, hogy a szervezeten belül minden VPP-vásárló befejezte az 1. lépést.
3. Győződjön meg arról, hogy az összes megvásárolt alkalmazás és licenc át lett telepítve az alkalmazások és könyvek számára az Apple Business Managerben vagy az Apple School Managerben.
4. Töltse le az új Location tokent az **Apple Business (vagy School) Manager** > **Beállítások** > **alkalmazások és könyvek** > **a saját kiszolgálói jogkivonatok**elemre.
5. Frissítse a Location tokent a Microsoft Endpoint Manager felügyeleti központban a **bérlői felügyelet** > **Összekötők és tokenek** > **Apple VPP-tokenek** és a token szinkronizálása érdekében.

## <a name="upload-an-apple-vpp-or-location-token"></a>Apple VPP-vagy Location token feltöltése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza a **bérlői felügyelet** > **Összekötők és tokenek** > **Apple VPP-tokenek**elemet.
4. A VPP-tokenek panel listájában válassza a **Létrehozás** elemet.
5. Az **VPP-token Létrehozása** panelen adja meg az alábbi adatokat:
    - **VPP-jogkivonat fájlja** – ha még nem tette meg, regisztráljon az Apple Business Managerre vagy az Apple School Managerre. A regisztrációt követően töltse le a fiókjához tartozó Apple VPP-tokent, és itt jelölje ki.
    - **Apple ID** – adja meg a feltöltött tokenhez társított fiók felügyelt Apple ID azonosítóját.
    - A **jogkivonat vezérlése egy másik Mdm** – ez a beállítás **Igen** értékre állítja a token hozzárendelését az Intune-hoz egy másik Mdm-megoldásból.
    - **Jogkivonat neve** – a jogkivonat nevének beállítására szolgáló felügyeleti mező.    
    - **Ország/régió** – válassza ki a VPP ország/régió tárolót.  Az Intune az adott VPP ország/régió tárolóban lévő összes területi beállításhoz a VPP-alkalmazásokat szinkronizálja.
        > [!WARNING]  
        > Az ország/régió módosítása frissíti az alkalmazások metaadatait és az App Store-beli URL-címet a következő szinkronizáláskor a tokenrel létrehozott alkalmazások Apple szolgáltatásával. Az alkalmazás nem frissül, ha nem létezik az új ország/régió tárolóban.

    - **VPP-fiók típusa** –A következő lehetőségek közül választhat: **Üzlet** és **Oktatás**.
    - **Alkalmazások automatikus frissítése** – Az automatikus frissítés engedélyezéséhez válasszon a **Be** és **Ki** érték közül. Engedélyezés esetén az Intune észleli, ha az alkalmazás-áruházban az adott VPP-alkalmazáshoz frissítés érhető el, és az eszköz legközelebbi bejelentkezésekor automatikusan leküldi a frissítéseket az eszközre. 
        
        > [!NOTE] 
        > Az Apple VPP automatikus alkalmazásfrissítései csak a **Kötelező** telepítési szándékkal üzembe helyezett alkalmazásokat frissítik automatikusan. Az **elérhető** telepítési szándéktal telepített alkalmazások esetében az automatikus frissítés állapotjelző üzenetet hoz létre a rendszergazda számára, amely tájékoztatja, hogy az alkalmazás új verziója érhető el. Az állapotjelző üzenet az alkalmazás kiválasztásával, az eszköz telepítési állapotának kiválasztásával és az állapot részleteinek ellenőrzésével tekinthető meg.  

    - **Engedélyezem a Microsoft számára, hogy a felhasználók és az eszközök adatait is el lehessen küldeni az Apple-nek.** – **Válassza az Elfogadom** lehetőséget a folytatáshoz. A Microsoft által az Apple-nek küldött adatokat az [Intune által az Apple](~/protect/data-intune-sends-to-apple.md)-nek küldött adatokat áttekintve tekintheti meg.

6. Amikor elkészült, válassza a **Létrehozás** gombot. A token a jogkivonatok panel listájában jelenik meg.

## <a name="synchronize-a-vpp-token"></a>VPP-token szinkronizálása
Az Intune-ban megvásárolt alkalmazások nevét, metaadatait és licencelési információit szinkronizálhatja a kiválasztott token **szinkronizálásának** kiválasztásával.

## <a name="assign-a-volume-purchased-app"></a>Mennyiségi programban vásárolt alkalmazás kiosztása

1. Válassza az **alkalmazások** > **minden alkalmazás**lehetőséget.
2. Az alkalmazáslista paneljén válassza ki a hozzárendelni kívánt alkalmazást, és válassza a **Hozzárendelés** lehetőséget.
3. Az **Alkalmazás neve** - **Hozzárendelések** panelen kattintson a **Csoport hozzáadása** elemre, majd a **Csoport hozzáadása** panelen válasszon egy **hozzárendelés-típust** és azokat az Azure AD-beli felhasználói vagy eszközcsoportokat, amelyekhez hozzá kívánja rendelni az alkalmazást.
5. Minden kijelölt csoporthoz válassza ki az alábbi beállításokat:
    - **Típus** – Határozza meg, hogy az alkalmazás **Elérhető**, azaz a végfelhasználók telepíthetik a Céges portálról, vagy **Kötelező**, azaz a végfelhasználók automatikusan megkapják az telepített alkalmazást.
    - **Licenc típusa** – Válassza a **Felhasználói licencelés** vagy az **Eszközlicencelés** lehetőséget.
6. Ha elkészült, válassza a **Mentés** elemet.


>[!NOTE]
>Az elérhető üzembe helyezési szándék nem támogatott az eszközök csoportjai esetében, csak a felhasználói csoportok támogatottak. A megjelenített alkalmazások listája egy tokenhez van társítva. Ha van egy olyan alkalmazása, amely több VPP-tokenhez is társítva van, akkor ugyanaz az alkalmazás többször is megjelenik; minden tokenhez egyszer.

> [!NOTE]  
> Az Intune (vagy bármely más MDM) valójában nem telepíti a VPP-alkalmazásokat. Ehelyett az Intune csatlakozik a VPP-fiókjához, és megadja az Apple-nek, hogy mely alkalmazás-licenceket rendelje hozzá az eszközökhöz. Innentől kezdve az összes tényleges telepítést az Apple és az eszköz között kezeljük.
> 
> [Apple MDM protokoll referenciája, 135-es oldal](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf)

## <a name="end-user-prompts-for-vpp"></a>VPP-figyelmeztetés a végfelhasználónak

A végfelhasználó különféle helyzetekben figyelmeztetést fog kapni VPP-alkalmazások telepítésére. A különféle feltételek az alábbi táblázatban láthatók:

| # | Forgatókönyv                                | Meghívás az Apple VPP-programba                              | Figyelmeztetés alkalmazástelepítésre | Apple ID bekérése |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – felhasználó által licencelt (nem felhasználó-beléptetési eszköz)                             | I                                                                                               | I                                           | I                                 |
| 2 | Corp (Vállalat) – licenccel rendelkező felhasználó (nem felügyelt eszköz)     | I                                                                                               | I                                           | I                                 |
| 3 | Corp (Vállalat) – licenccel rendelkező felhasználó (felügyelt eszköz)         | I                                                                                               | N                                           | I                                 |
| 4 | BYOD – licenccel rendelkező eszköz                           | N                                                                                               | I                                           | N                                 |
| 5 | CORP (Vállalat) – licenccel rendelkező eszköz (nem felügyelt eszköz)                           | N                                                                                               | I                                           | N                                 |
| 6 | CORP (Vállalat) – licenccel rendelkező eszköz (felügyelt eszköz)                           | N                                                                                               | N                                           | N                                 |
| 7 | Teljes képernyős mód (felügyelt eszköz) – licenccel rendelkező eszköz | N                                                                                               | N                                           | N                                 |
| 8 | Teljes képernyős mód (felügyelt eszköz) – licenccel rendelkező felhasználó   | --- | ---                                          | ---                                |

> [!Note]  
> Nem ajánlott a VPP-alkalmazásokat felhasználói licencelést használó kioszk módú eszközökhöz rendelni.

## <a name="revoking-app-licenses"></a>Alkalmazás-licencek visszavonása

Egy adott eszköz, felhasználó vagy alkalmazás alapján visszavonhatja az összes kapcsolódó iOS-vagy macOS-alkalmazás licencét.  Az iOS-és macOS-platformok között azonban van néhány különbség. 

|   | iOS | macOS |
|-----|------------------|----------------|
| **Alkalmazás-hozzárendelés eltávolítása** | Ha egy felhasználóhoz hozzárendelt alkalmazást eltávolít, az Intune visszaigényli a felhasználó vagy az eszköz licencét, és eltávolítja az alkalmazást az eszközről. | Ha eltávolít egy felhasználóhoz hozzárendelt alkalmazást, az Intune visszaállítja a felhasználó vagy az eszköz licencét. Az alkalmazás nem lesz eltávolítva az eszközről. |
| **Alkalmazás licencének visszavonása** | Az alkalmazás licencének visszavonása visszaállítja az alkalmazás licencét a felhasználótól vagy az eszköztől. Az alkalmazás az eszközről való eltávolításához módosítania kell a hozzárendelést az **Eltávolítás** elemre. | Az alkalmazás licencének visszavonása visszaállítja az alkalmazás licencét a felhasználótól vagy az eszköztől. A visszavont licenccel rendelkező macOS-alkalmazás továbbra is használható az eszközön, de nem frissíthető, amíg a licencet nem rendeli hozzá a felhasználóhoz vagy eszközhöz. Az Apple szerint az ilyen alkalmazásokat egy 30 napos türelmi időszak után távolítja el a rendszer. Az Apple azonban nem biztosít olyan eszközt, amellyel az Intune eltávolíthatja az alkalmazást az eltávolítási hozzárendelés művelettel.

>[!NOTE]
> - Az Intune visszaállítja az alkalmazás licenceit, amikor egy alkalmazott elhagyja a vállalatot, és már nem része a HRE csoportnak.
> - Ha a megvásárolt alkalmazást **eltávolítási** szándékkal rendeli hozzá, az Intune mind visszaállítja a licencet, és eltávolítja az alkalmazást.
> - Az alkalmazás-licenceket a rendszer nem állítja vissza, amikor eltávolítanak egy eszközt az Intune-felügyeletből. 

## <a name="deleting-vpp-tokens"></a>VPP-tokenek törlése
<!-- 820879 -->  
Az Apple Volume beszerzési program (VPP) tokenjét a-konzol használatával törölheti. Ez akkor lehet szükséges, ha egy VPP-token több példányban van meg. A token törlésével a kapcsolódó alkalmazásokat és hozzárendelést is törli. A token törlésével azonban nem vonja vissza az alkalmazáslicenceket, és nem töröl alkalmazásokat. 

>[!NOTE]
>Az Intune a token törlése után már nem tudja visszavonni az alkalmazáslicenceket. 

<!-- 820870 -->  
Ha egy VPP-token összes VPP-alkalmazásának licenceit törölni szeretné, először vissza kell vonnia a tokenhez társított összes alkalmazáslicencet, majd törölnie kell a tokent.

## <a name="renewing-app-licenses"></a>Alkalmazáslicencek megújítása

Az Apple VPP-token megújításához töltse le az Apple Business Manager vagy az Apple School Manager új jogkivonatát, és frissítse a meglévő tokent az Intune-ban.

## <a name="deleting-a-vpp-app"></a>VPP-alkalmazás törlése

Jelenleg az iOS VPP-alkalmazások nem törölhetők a Microsoft Intune-ból.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Egyéni szerepkör-engedélyek kiosztása VPP-hez

Az Apple VPP-tokenekhez és VPP-alkalmazásokhoz való hozzáférés az Intune-ban egyéni rendszergazdai szerepkörökhöz hozzárendelt engedélyektől függetlenül is szabályozható.

* Ha engedélyezni szeretné az Intune egyéni szerepkörének az Apple VPP-tokenek kezelését az **alkalmazások** > **Apple VPP-tokenek**területen, rendeljen engedélyeket a **felügyelt alkalmazásokhoz**.
* Ha engedélyezni szeretné az Intune egyéni szerepkörét az iOS VPP-tokenekkel vásárolt alkalmazások kezeléséhez az **alkalmazások** > az **összes alkalmazás**területen, rendeljen engedélyeket a **Mobile apps**szolgáltatáshoz. 

## <a name="additional-information"></a>További információ

Az Apple közvetlen segítséget biztosít a VPP-tokenek létrehozásához és megújításához. További információkért lásd a [Tartalomterjesztés a felhasználók felé a Mennyiségi vásárlási program (VPP) segítségével](https://go.microsoft.com/fwlink/?linkid=2014661) című részt az Apple dokumentációjában. 

Ha az Intune portálján a **Külső MDM-hez rendelve** beállítás látható, a VPP-token Intune-beli használata előtt a rendszergazdának el kell távolítania a VPP-tokent a harmadik félhez tartozó MDM-ről.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

### <a name="how-many-tokens-can-i-upload"></a>Hány jogkivonatot tölthetek fel?
Az Intune-ban akár 3 000 tokent is feltölthet.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Mennyi ideig tart, mire a portál frissíti a licencszámot egy alkalmazás telepítése vagy az eszközről való eltávolítása után?
A licenc néhány órával az alkalmazások telepítése vagy eltávolítása után frissül. Megjegyzés: Ha a végfelhasználó eltávolítja az alkalmazást, a licenc továbbra is a felhasználóhoz vagy az eszközhöz lesz rendelve.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Túlléphető egy alkalmazáselőfizetés? Ha igen, milyen körülmények között?
Igen. Az Intune rendszergazdája túllépheti az alkalmazáselőfizetéseket. Ha például a rendszergazda 100 licencet vásárol XYZ alkalmazáshoz, majd egy 500 tagú csoporthoz rendeli azt. Az első 100 tag (felhasználó vagy eszköz) megkapja a licencet, a többi taghoz azonban nem lesz hozzárendelve licenc.


## <a name="next-steps"></a>További lépések

Az alkalmazás-hozzárendelések figyeléséhez a [How to monitor apps](apps-monitor.md) (Alkalmazások figyelése) című témakörben találhat segítséget.

Az alkalmazással kapcsolatos problémák elhárításával kapcsolatos információkért lásd: [alkalmazások hibaelhárítása](~/apps/troubleshoot-app-install.md) .
