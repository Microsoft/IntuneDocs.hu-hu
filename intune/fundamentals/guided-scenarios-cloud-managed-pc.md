---
title: Interaktív forgatókönyv – felhőben felügyelt modern asztal
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan állíthat be és konfigurálhat egy alapszintű modern asztalt a Microsoft 365 Eszközkezelő portálról.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3372fc83e467b08b479490b3707f2be03409156
ms.sourcegitcommit: c2e62f1ebdf75599c8e544287123c602f0f15f2b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72749332"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Interaktív forgatókönyv – felhőben felügyelt modern asztal

A modern asztali környezet a legkorszerűbb hatékonyságnövelő platform, amely az Information Worker számára készült. Az Office 365 ProPlus és a Windows 10 a modern asztal alapvető összetevői, valamint a Windows 10 és a Windows Defender komplex veszélyforrások elleni védelem legújabb biztonsági alapkonfigurációi. 

A modern asztal felhőből való kezelése az internetes szintű távoli műveletek előnyeit élvezheti. A Cloud Management a beépített Windows mobileszköz-kezelési házirendeket használja, és eltávolítja a függőségeket a helyi Active Directory csoportházirenden. 

Ha szeretné kiértékelni a felhőben felügyelt modern asztalt a saját szervezetében, ez az irányított forgatókönyv előre definiálja az alapszintű telepítéshez szükséges összes konfigurációt. Ebben az interaktív forgatókönyvben egy biztonságos környezetet hoz létre, ahol kipróbálhatja az Intune-eszközkezelés képességeit. 

## <a name="prerequisites"></a>Előfeltételek
- [Az Mdm-szolgáltató beállítása az Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) -ra – a mobileszköz-kezelési (Mdm) szolgáltatói beállítás határozza meg az eszközök felügyeletének módját. Ahhoz, hogy a felhasználók felügyeletre tudják regisztrálni eszközeiket, a rendszergazdának be kell állítania egy MDM-szolgáltatót.
- M356 E3 minimum (vagy M365 E5 a legjobb biztonság érdekében)
- Windows 10 1903 rendszerű eszköz (a Windows Autopilot szolgáltatásban regisztrált legjobb végfelhasználói élmény)
- Az interaktív forgatókönyv végrehajtásához szükséges Intune rendszergazdai engedélyek:
  - Eszköz konfigurációja olvasás, létrehozás, törlés, hozzárendelés és frissítés
  - Beléptetési programok olvasási eszköz, profil olvasása, profil létrehozása, profil társítása, profil törlése
  - Mobile apps olvasás, létrehozás, törlés, hozzárendelés és frissítés
  - Szervezet olvasása és frissítése
  - Biztonsági alaptervek olvasás, létrehozás, törlés, hozzárendelés és frissítés
  - Az olvasási, létrehozási, törlési, hozzárendelési és frissítési szabályzatok beállítása

## <a name="step-1---introduction"></a>1\. lépés – bevezetés

Ennek az interaktív forgatókönyvnek a használatával egy tesztelési felhasználót kell beállítania, egy eszköz regisztrálása az Intune-ban, és az eszköz üzembe helyezése az Intune által ajánlott beállításokkal, valamint a Windows 10 és az Office ProPlus. Az eszköz a Microsoft Defender komplex veszélyforrások elleni védelemhez is be lesz állítva, ha [engedélyezi ezt a védelmet az Intune-ban](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune). Az Ön által beállított felhasználó és a regisztrált eszköz új biztonsági csoportokhoz lesz hozzáadva, és a biztonság és a termelékenység ajánlott beállításaival lesz konfigurálva. 

### <a name="what-you-will-need-to-continue"></a>A folytatáshoz szükséges művelet

Ebben az interaktív helyzetben meg kell adnia a tesztelési eszközt, és tesztelni kell a felhasználót. Győződjön meg arról, hogy a következő feladatokat hajtja végre:
- Tesztelési felhasználói fiók beállítása Azure Active Directoryban.
- Hozzon létre egy, a Windows 10 1903-es vagy újabb verzióját futtató tesztelési eszközt.
- Választható [Regisztrálja a tesztelő eszközt a Windows Autopilot szolgáltatásban](~/enrollment/enrollment-autopilot.md#add-devices).
- Választható A saját [szervezet Azure Active Directory bejelentkezési oldalának](https://go.microsoft.com/fwlink/?linkid=2102455)engedélyezése.

## <a name="step-2---user"></a>2\. lépés – felhasználó

Válassza ki az eszközön beállítani kívánt felhasználót. Ez a személy lesz az eszköz elsődleges felhasználója.

Ha további felhasználókat vagy eszközöket szeretne hozzáadni ehhez a konfigurációhoz, egyszerűen adja hozzá a felhasználókat és az eszközöket a varázsló által generált HRE biztonsági csoportokhoz. A többi irányított forgatókönyvtől eltérően a varázslót nem kell többször futtatnia, mert a konfiguráció nem testreszabható. Csak adjon hozzá több felhasználót és eszközt a létrehozott HRE-csoportokhoz. A varázsló befejezése után megtekintheti az üzembe helyezett ajánlott házirendek által létrehozott csoportot. 

## <a name="step-3---device"></a>3\. lépés – eszköz

Győződjön meg arról, hogy az eszközön a Windows 10 1903-es vagy újabb verziója fut.  Az elsődleges felhasználónak be kell állítania az eszközt, amikor megkapja. A felhasználó két beállítási lehetőség közül választhat. 

### <a name="option-a--windows-autopilot"></a>A. lehetőség – Windows Autopilot
A Windows Autopilot automatizálja az új eszközök konfigurációját, így a felhasználók nem tudnak az IT-támogatás nélkül beállítani őket. Ha az eszköz már regisztrálva van a Windows Autopilot szolgáltatásban, válassza ki a sorozatszám alapján. További információ a Windows Autopilot használatáról: [eszköz regisztrálása a Windows automatikus próbaverziójában (nem kötelező)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional).

### <a name="option-b--manual-device-enrollment"></a>B. lehetőség – manuális eszközök beléptetése
A felhasználók manuálisan fogják beállítani és regisztrálni az új eszközöket a mobileszköz-felügyeletben. A forgatókönyv elvégzése után állítsa alaphelyzetbe az eszközt, és adja meg az elsődleges felhasználónak a Windows-eszközök regisztrálására vonatkozó utasításokat. További információ: [Windows 10-es eszköz csatlakoztatása az Azure ad-hez az első futtatási élményben](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>4\. lépés – felülvizsgálat + létrehozás

Az utolsó lépés lehetővé teszi a konfigurált beállítások összefoglalásának áttekintését. Miután áttekintette a beállításokat, kattintson a **telepítés** elemre az interaktív forgatókönyv befejezéséhez. Miután az interaktív forgatókönyv elkészült, megjelenik egy táblázat az erőforrások között. Ezeket az erőforrásokat később is szerkesztheti, azonban ha elhagyja az összegző nézetet, a rendszer nem menti a táblát.

> [!IMPORTANT]
> Az interaktív forgatókönyv befejezését követően megjelenik egy Összegzés. Az összegzésben felsorolt erőforrásokat módosíthatja, azonban a osztályalapú megjelenítő tábla nem lesz mentve.

### <a name="verification"></a>Ellenőrzés
1. Annak ellenőrzése, hogy a kijelölt MDM-felhasználói hatókör van-e hozzárendelve
    - Győződjön meg arról, hogy a [Mdm felhasználói hatóköre](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) :
        - **A** **Microsoft Intune** alkalmazáshoz, vagy
        - **Néhány**értékre állítva. Adja hozzá az interaktív forgatókönyv által létrehozott felhasználói csoportot is.
2. Ellenőrizze, hogy a kiválasztott felhasználó tud-e csatlakozni az eszközökhöz Azure Active Directoryhoz.
    - Győződjön meg arról, hogy a HRE illesztés:
        - Az **összes** vagy a értékre állítva
        - **Néhány**értékre állítva. Adja hozzá az interaktív forgatókönyv által létrehozott felhasználói csoportot is.
3. Kövesse az eszközön a megfelelő lépéseket az Azure AD-hez való csatlakozáshoz a következők alapján:
    - Az Autopilot-vel. További információ: [Windows Autopilot felhasználó által vezérelt üzemmód](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Autopilot nélkül: további tudnivalókért tekintse meg [a Windows 10-es eszközök csatlakoztatása az Azure ad-hez című részt az első futtatási élményben](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>Mi történik, ha az üzembe helyezés gombra kattintok?
A rendszer hozzáadja a felhasználót és az eszközt az új biztonsági csoportokhoz. Emellett az Intune által ajánlott beállításokkal is konfigurálhatók a biztonság és a hatékonyság érdekében a munkahelyi vagy iskolai környezetben. Miután a felhasználó csatlakoztatta az eszközt az Azure AD-hez, további alkalmazások és beállítások lesznek hozzáadva az eszközhöz. További információt ezekről a további konfigurációkról a gyors üzembe helyezési útmutató [: Windows 10-es eszköz regisztrálása](~/enrollment/quickstart-enroll-windows-device.md)című témakörben talál.

## <a name="additional-information"></a>További információ

### <a name="register-device-with-windows-autopilot-optional"></a>Eszköz regisztrálása a Windows Autopilot szolgáltatásban (nem kötelező)

Választhatóan egy regisztrált Autopilot-eszközt is használhat. Az Autopilot esetében ez az irányított forgatókönyv egy Autopilot Deployment-profilt és egy regisztrációs állapot oldal-profilt fog rendelni. Az Autopilot Deployment-profil a következőképpen lesz konfigurálva:
- Felhasználó által vezérelt mód – azaz a felhasználónak a Felhasználónév és a jelszó megadását kell megadnia a Windows telepítője során.
- Azure AD-csatlakozás.
- A Windows telepítő testreszabása:
  - A Microsoft szoftverlicencelési feltételei képernyő elrejtése
  - Adatvédelmi beállítások elrejtése 
  - Helyi rendszergazdai jogosultságok nélkül hozza létre a felhasználó helyi profilját
  - A fiók módosítása beállításainak elrejtése a vállalati bejelentkezési oldalon

A beléptetési állapot lap csak az Autopilot-eszközök esetében lesz engedélyezve, és nem blokkolja az összes alkalmazás telepítésére való várakozást.

Az interaktív forgatókönyv a felhasználót a kiválasztott Autopilot-eszközhöz is hozzárendeli egy személyre szabott telepítési élményhez.

#### <a name="post-requisites"></a>Utólagos követelmények
Miután a felhasználó csatlakoztatta az eszközt a Azure Active Directoryhoz, a következő konfigurációk lesznek alkalmazva az eszközön:
1. Az Office 365 ProPlus telepítése automatikusan megtörténik a felhőben felügyelt SZÁMÍTÓGÉPeken. Magában foglalja az Ön által ismert alkalmazásokat, például a hozzáférés, az Excel, a OneNote, az Outlook, a PowerPoint, a Publisher, a Skype vállalati verzió és a Word. Ezeket az alkalmazásokat használhatja az Office 365-szolgáltatásokhoz, például a SharePoint Online-hoz, az Exchange Online-hoz és a Skype vállalati online verzióhoz való kapcsolódáshoz. Az Office 365 ProPlus rendszeresen frissül új funkciókkal, az Office nem előfizetéses verzióival ellentétben. Az új szolgáltatások listáját az Office 365 újdonságai című témakörben tekintheti meg.
2. A Windows biztonsági alapkonfigurációk a felhőben felügyelt SZÁMÍTÓGÉPeken lesznek telepítve. Ha a Microsoft Defender komplex veszélyforrások elleni védelem beállítását választotta, az interaktív forgatókönyv a Defender alapkonfigurációjának beállításait is konfigurálja. A Defender komplex veszélyforrások elleni védelem új védelmi réteget biztosít a Windows 10 biztonsági verem számára. A Windows 10-es és a robusztus felhőalapú szolgáltatások kombinációja révén a rendszer segít észlelni a fenyegetéseket, amelyeken korábban más védekezés történt. 

## <a name="next-steps"></a>További lépések

- Ha a Windows Defender komplex veszélyforrások észlelését használja, hozzon létre egy [Intune-megfelelőségi szabályzatot](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy) , amely megköveteli a Defender-fenyegetések elemzését a megfelelőség teljesítése érdekében.
- Hozzon létre egy [eszközön alapuló feltételes hozzáférési szabályzatot](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy) , amely letiltja a hozzáférést, ha az eszköz nem felel meg az Intune megfelelőségi követelményeinek.
