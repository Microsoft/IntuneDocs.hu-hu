---
title: Alkalmazások telepítésével kapcsolatos problémák elhárítása
titleSuffix: Microsoft Intune
description: A Microsoft Intune hibaelhárítási paneljével elháríthatja az alkalmazások telepítésével kapcsolatos problémákat.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4783d24e3fc25583a61f88c2e7375d4eed673186
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563486"
---
# <a name="troubleshoot-app-installation-issues"></a>Alkalmazások telepítésével kapcsolatos problémák elhárítása

A Microsoft Intune MDM által felügyelt eszközökön néha sikertelenek lehetnek az alkalmazástelepítések. Ilyen esetekben nem könnyű megérteni a hiba okát, illetve elhárítani azt. A Microsoft Intune olyan adatokat szolgáltat az alkalmazástelepítésbeli hibákról, amelyekkel az ügyfélszolgálati operátorok és az Intune-rendszergazdák megtekinthetik az alkalmazásadatokat, és reagálhatnak az ügyfelek kérelmeire. Az Intune hibaelhárítási panelje megjeleníti a hibák adatait, így a felhasználói eszközökön kezelt alkalmazások információit is. Az alkalmazások végpontok közötti életciklusához tartozó adatok a **Felügyelt alkalmazások** panelen, az egyes eszközök alatt tekinthetők meg. Itt megtekintheti a telepítési problémákat, például az alkalmazás létrehozási, módosítási és célzási dátumát, valamint az eszközökre való továbbításának dátumát. 

## <a name="app-troubleshooting-details"></a>Alkalmazás-hibaelhárítás részletei

Az Intune az adott felhasználók eszközein telepített alkalmazások alapján szolgáltat hibaelhárítási információkat.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza a **hibakeresés + támogatás**lehetőséget.
4. A felhasználó kiválasztásához kattintson a **Felhasználó kijelölése** lehetőségre. Ekkor megjelenik a **Felhasználók kijelölése** panel.
5. Jelöljön ki egy felhasználót a megfelelő név vagy e-mail cím beírásával. Kattintson a **Kijelölés** gombra a lap alján. A felhasználóval kapcsolatos hibaelhárítási információ a **Hibaelhárítás** panelen jelenik meg. 
6. Az **Eszközök** listában jelölje ki azt az eszközt, amelyen hibaelhárítást szeretne végezni.
    ![Az Intune Hibaelhárítás panelje.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. A kijelölt eszköz paneljén válassza a **Felügyelt alkalmazások** lehetőséget. Megjelenik a felügyelt alkalmazások listája.
    ![Az Intune által kezelt eszköz adatai.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Válassza ki azt az alkalmazást, amelynél hibát jelez a **Telepítés állapota**.
    ![A kiválasztott alkalmazás, amelynél megjelennek a telepítési hiba adatai.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > Ugyanazt az alkalmazást eltérő alkalmazásműveleti szándékkal rendelhetik hozzá különböző csoportokhoz. Egy alkalmazás feloldott szándéka például **Kizárva** értéket jelez, ha az alkalmazás ki van zárva egy felhasználó számára az alkalmazás-hozzárendelés során. További információ: [Alkalmazások hozzárendelési ütközéseinek feloldása](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Ha egy szükséges alkalmazás telepítése sikertelen, akkor Ön vagy a segélyszolgálat szinkronizálhatja az eszközt, és újra megkísérelheti az alkalmazás telepítését.

Az alkalmazástelepítési hiba információi ismertetik a problémát. Ezen adatok segítségével meghatározhatja a probléma feloldásához szükséges műveletet. Az alkalmazások telepítési problémáinak elhárításával kapcsolatos további információkért lásd az [alkalmazások telepítési hibáit](troubleshoot-app-install.md#app-installation-errors)ismertető témakört.

> [!Note]  
> A **Hibaelhárítás** panel a böngészőben a [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) címen is elérhető.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>A felhasználói csoport megcélzó alkalmazásának telepítése nem érhető el az eszközön
Az alkalmazások telepítésekor a következő műveleteket kell figyelembe venni:
- Ha az alkalmazás nem jelenik meg a Céges portálban, győződjön meg arról, hogy az alkalmazás **elérhető** szándékkal van telepítve, és hogy a felhasználó a céges portálhoz fér hozzá az alkalmazás által támogatott típusú eszközhöz.
- A Windows BYOD eszközökhöz a felhasználónak munkahelyi fiókot kell hozzáadnia az eszközhöz.
- Ellenőrizze, hogy a felhasználó meghaladja-e a HRE-eszköz korlátját:
  1. Navigáljon [Azure Active Directory eszköz beállításaihoz](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Jegyezze fel a **maximális eszközök felhasználónként**való beállításának értékét.
  3. Navigáljon [Azure Active Directory felhasználóhoz](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Válassza ki az érintett felhasználót, és kattintson az **eszközök**elemre.
  5. Ha a felhasználó túllépi a beállított korlátot, törölje azokat az elavult rekordokat, amelyekre már nincs szükség.
- IOS DEP-eszközök esetén győződjön meg arról, hogy a felhasználó **regisztrálva van a felhasználó által** az Intune-eszköz áttekintés paneljén. Ha a NA-t jeleníti meg, akkor telepítsen egy konfigurációs házirendet a Intune Céges portálhoz. További információ: [a céges portál alkalmazás konfigurálása](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Win32-alkalmazás telepítésének hibaelhárítása

Válassza ki az Intune felügyeleti bővítmény használatával üzembe helyezett Win32-alkalmazást. Ha a Win32-alkalmazás telepítése sikertelen, a **naplók összegyűjtése** lehetőség kiválasztásával végezhető el. 

> [!IMPORTANT]
> A **naplók összegyűjtése** beállítás nem lesz engedélyezve, ha a Win32-alkalmazás sikeresen telepítve van az eszközön.<p>A Win32-alkalmazások naplózási adatainak összegyűjtéséhez az Intune felügyeleti bővítményét telepíteni kell a Windows-ügyfélre. Az Intune felügyeleti bővítmény akkor települ, ha PowerShell-parancsfájlt vagy Win32-alkalmazást telepít egy felhasználói vagy eszköz biztonsági csoportba. További információ: [Intune felügyeleti bővítmény – előfeltételek](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Naplófájl gyűjtése

A Win32-alkalmazás telepítési naplóinak összegyűjtéséhez kövesse az [alkalmazás hibaelhárítási részletei](troubleshoot-app-install.md#app-troubleshooting-details)című szakasz lépéseit. Ezután folytassa a következő lépésekkel:

1. Kattintson a **naplók összegyűjtése** lehetőségre a **telepítés részletei** ablaktáblán.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. A naplófájlok gyűjtési folyamatának megkezdéséhez adja meg a fájl elérési útját, és kattintson **az OK**gombra.

    > [!NOTE]
    > A naplózási gyűjtemény kevesebb mint két órát vesz igénybe. Támogatott fájltípusok: *. log,. txt,. dmp,. cab,. zip,. XML,. evtx és. evtl*. Legfeljebb 25 fájlelérési út engedélyezett.

3. A naplófájlok gyűjtése után kiválaszthatja a **naplók** hivatkozást a naplófájlok letöltéséhez.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Ekkor megjelenik egy értesítés, amely az alkalmazás naplójának sikeres sikerességét jelzi.

#### <a name="win32-log-collection-requirements"></a>A Win32-naplók gyűjtésének követelményei

A naplófájlok összegyűjtéséhez konkrét követelményekre van szükség:

- Meg kell adnia a naplófájl teljes elérési útját. 
- Megadhatja a naplózási gyűjtemény környezeti változóit, például a következőket:<br>
  *% PROGRAMFILES%,% PROGRAMDATA%% NYILVÁNOS%,% WINDIR%,% TEMP%,% TMP%*
- Csak a pontos fájlkiterjesztések engedélyezettek, például:<br>
  *. log,. txt,. dmp,. cab,. zip,. XML*
- A feltölteni kívánt maximális naplófájl 60 MB vagy 25 fájl, amelyik előbb megtörténik. 
- A Win32-alkalmazás telepítési naplójának gyűjteménye engedélyezve van azon alkalmazások esetében, amelyek megfelelnek a szükséges, elérhető és eltávolított alkalmazás-hozzárendelési szándéknak.
- A tárolt naplók titkosítva vannak a naplókban tárolt személyes azonosításra alkalmas adatok védelemmel.
- A Win32-alkalmazások támogatási jegyének megnyitása közben csatolja a kapcsolódó hibák naplóit a fenti lépésekkel.

## <a name="app-installation-errors"></a>Alkalmazástelepítési hibák

Az alábbi hibaüzenetek és leírások az Androidos és iOS-es telepítési hibák részleteit mutatják be. 

### <a name="android-errors"></a>Android hibák

Ez a szakasz az eszköz rendszergazdája (DA) és a Samsung Knox-regisztrációt is említi. További információ: Android-eszközök [rendszergazdai regisztrációja](../enrollment/android-enroll-device-administrator.md) és [automatikus regisztrálása Android-eszközökön a Samsung Knox Mobile-regisztráció használatával](../enrollment/android-samsung-knox-mobile-enroll.md). 

| Hibaüzenet/kód | Description |
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Az alkalmazás telepítése nem sikerült. (0xC7D14FB5) | Ez a hibaüzenet akkor jelenik meg, ha az Intune nem tudja megállapítani az Android-alkalmazás telepítési hibájának okát. A hiba során az Android nem adott semmilyen információt. Ezt a hibát akkor adja vissza a rendszer, amikor az APK letöltése sikeres volt, de az alkalmazás telepítése nem sikerült. Ez a hiba gyakrabban fordulhat elő, mert egy helytelen APK-fájl nem telepíthető az eszközre. Lehetséges ok lehet, ha a Google Play Protect blokkolja az alkalmazás telepítését biztonsági problémák miatt. A hiba másik lehetséges oka az, ha egy eszköz nem támogatja az alkalmazást. Ha például az alkalmazásnak a 21-es és az API-nak kell lennie, és az eszköz jelenleg a 19-ös verziójú. Az Intune a DA és KNOX rendszerű eszközökön ezt a hibát adja vissza, de előfordulhat, hogy a felhasználók az újrapróbálkozásra kattintanak. Ha az alkalmazás egy elérhető alkalmazás, akkor az értesítés elhagyható. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el. |
| Az alkalmazás telepítése megszakadt, mert a telepítési (APK) fájl törlődött a letöltés után, de még a telepítés előtt. (0xC7D14FBA) | Az APK letöltése sikeres volt, de mielőtt a felhasználó telepítette az alkalmazást, a fájl el lett távolítva az eszközről. Ez akkor fordulhat elő, ha a letöltés és a telepítés között nagy eltérés történt. A felhasználó például megszakította az eredeti telepítést, megvárta, majd rákattintott az értesítésre az újbóli próbálkozáshoz. Ezt a hibaüzenetet a rendszer csak a DA forgatókönyvek esetében adja vissza. KNOX-forgatókönyvek csendesen is elvégezhető. Bemutatunk egy értesítést az újrapróbálkozáshoz, hogy a felhasználó el tudja fogadni a megszakítás helyett. Ha az alkalmazás egy elérhető alkalmazás, akkor az értesítés elhagyható. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el. |
| Az alkalmazás telepítése megszakadt, mert a folyamat újra lett indítva a telepítés során. (0xC7D14FBB) | Az eszköz újraindult az APK telepítési folyamata során, ami egy megszakított telepítést eredményezett. Ez a hibaüzenet a DA és KNOX rendszerű eszközökre is visszaadja. Az Intune értesítést küld arról, hogy a felhasználók rákattintanak az újrapróbálkozásra. Ha az alkalmazás egy elérhető alkalmazás, akkor az értesítés elhagyható. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el. |
| A telepítés sikeres befejezése után az alkalmazás nem észlelhető. (0x87D1041C) | A felhasználó explicit módon eltávolította az alkalmazást. Ezt a hibát a rendszer nem adja vissza az ügyféltől. Ez egy hiba, amely akkor jön létre, amikor az alkalmazást egy ponton telepítették, de a felhasználó eltávolította. Ez a hiba csak a szükséges alkalmazások esetében fordul elő. A nem szükséges alkalmazásokat a felhasználó eltávolíthatja. Ez a hiba csak a DA-ban fordulhat elő. A KNOX nem engedélyezi a felügyelt alkalmazások eltávolítását. A következő szinkronizálás újraküldi az értesítéseket az eszközön, amelyet a felhasználónak telepítenie kell. A felhasználó figyelmen kívül hagyhatja az értesítést. Ezt a hibát a rendszer addig fogja jelenteni, amíg a felhasználó nem telepíti az alkalmazást. |
| A Letöltés ismeretlen hiba miatt nem sikerült. (0xC7D14FB2) | Ez a hiba akkor fordul elő, ha a letöltés sikertelen. Ez a hiba általában Wi-Fi-problémák vagy lassú kapcsolatok miatt fordulhat elő. Ezt a hibát a rendszer csak a DA forgatókönyvek esetében adja vissza. KNOX-forgatókönyvek esetén a rendszer nem kéri a felhasználót a telepítésre, ezt csendesen teheti meg. Az Intune értesítést küld arról, hogy a felhasználók rákattintanak az újrapróbálkozásra. Ha az alkalmazás egy elérhető alkalmazás, akkor az értesítés elhagyható. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el. |
| A Letöltés ismeretlen hiba miatt nem sikerült. A rendszer az eszköz következő szinkronizálásakor újra megpróbálja végrehajtani a szabályzatot. (0xC7D15078) | Ez a hiba akkor fordul elő, ha a letöltés sikertelen. Ez a hiba általában Wi-Fi-problémák vagy lassú kapcsolatok miatt fordulhat elő. Ezt a hibát a rendszer csak a DA forgatókönyvek esetében adja vissza. KNOX-forgatókönyvek esetén a rendszer nem kéri a felhasználót a telepítésre, ezt csendesen teheti meg. |
| A végfelhasználó megszakította az alkalmazás telepítését. (0xC7D14FB1) | A felhasználó explicit módon eltávolította az alkalmazást. Ezt a hibát akkor adja vissza a rendszer, amikor a felhasználó megszakította az Android operációsrendszer-telepítési tevékenységet. A felhasználó leállította a Mégse gombot, amikor az operációs rendszer telepítési kérése be lett állítva, vagy a parancssorból kattintott. Ezt a hibát a rendszer csak a DA forgatókönyvek esetében adja vissza. KNOX-forgatókönyvek esetén a rendszer nem kéri a felhasználót a telepítésre, ezt csendesen teheti meg. Az Intune értesítést küld arról, hogy a felhasználók rákattintanak az újrapróbálkozásra. Ha az alkalmazás egy elérhető alkalmazás, akkor az értesítés elhagyható. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el. Kérje meg a felhasználót, hogy ne szakítsa meg a telepítést. |
| A fájl letöltési folyamata váratlanul leállt. (0xC7D15015) | Az operációs rendszer leállította a letöltési folyamatot a befejezés előtt. Ez a hiba akkor fordulhat elő, ha az eszközön kevés az akkumulátor, vagy a letöltés túl sokáig tart. Ezt a hibát a rendszer csak a DA forgatókönyvek esetében adja vissza. KNOX-forgatókönyvek esetén a rendszer nem kéri a felhasználót a telepítésre, ezt csendesen teheti meg. Az Intune értesítést küld arról, hogy a felhasználók rákattintanak az újrapróbálkozásra. Ha az alkalmazás egy elérhető alkalmazás, akkor az értesítés elhagyható. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el. Győződjön meg arról, hogy az eszköz megbízható hálózati kapcsolatban áll.  |
| A fájl letöltése szolgáltatás váratlanul leállt. A rendszer az eszköz következő szinkronizálásakor újra megpróbálja végrehajtani a szabályzatot. (0xC7D1507C) | Az operációs rendszer befejeződött a letöltési folyamat befejezése előtt. Ez a hiba akkor fordulhat elő, ha az eszközön kevés az akkumulátor, vagy a letöltés túl sokáig tart. Ezt a hibát a rendszer csak a DA forgatókönyvek esetében adja vissza. KNOX-forgatókönyvek esetén a rendszer nem kéri a felhasználót a telepítésre, ezt csendesen teheti meg. Manuálisan szinkronizálja az eszközt, vagy várjon 24 órát, és keresse meg az állapotot. |
| Nem sikerült eltávolítani az alkalmazást. (0xc7d14fb8) | Ez a hiba általános eltávolítási hiba. Az operációs rendszer nem adta meg, hogy miért nem sikerült eltávolítani az alkalmazást. Egyes rendszergazdai alkalmazások nem távolíthatók el egyszerűen. Győződjön meg arról, hogy az alkalmazás manuálisan is eltávolítható, és Gyűjtse össze a Céges portál naplókat, ha az Eltávolítás sikertelen. |
| A frissítéshez használt alkalmazás-telepítési APK-fájl nem felel meg az eszközön található aktuális alkalmazás aláírásának. (0xc7d14fb7) | Az Android operációs rendszernek meg kell egyeznie azzal a korlátozással, hogy a frissítési verzióhoz tartozó aláíró tanúsítvány pontosan ugyanaz legyen, mint a meglévő verzió aláírásához használt tanúsítvány. Ha a fejlesztő nem használhatja ugyanazt a tanúsítványt az új verzió aláírásához, el kell távolítania a meglévő alkalmazást, és újra kell telepítenie az új alkalmazást, és nem kell frissítenie a meglévő alkalmazást. |
| A végfelhasználó megszakította az alkalmazás telepítését. (0xc7d14fb9) | Tájékoztassa a felhasználót, hogy fogadja el az Intune-ban üzembe helyezett alkalmazást, és amikor a rendszer kéri, telepítse az alkalmazást. |
| Az alkalmazás eltávolítása megszakadt, mert a folyamat újra lett indítva a telepítés során. (0xc7d14fbc) | Az alkalmazás telepítési folyamatát az operációs rendszer megszakította, vagy az eszköz újraindult. Próbálja megismételni a telepítést, és gyűjtsön Céges portál naplókat, ha ez a hiba újra bekövetkezik. |
| Az alkalmazás-telepítési APK-fájl nem telepíthető, mert nem volt aláírva. (0xc7d14fb6) | Alapértelmezés szerint az Android operációs rendszer megköveteli, hogy az alkalmazások aláírva legyenek. Győződjön meg arról, hogy az alkalmazás aláírása az üzembe helyezés előtt megtörténik. |

### <a name="ios-errors"></a>iOS hibák

| Hibaüzenet/kód | Leírás/hibaelhárítási tippek |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Az Apple MDM-ügynök visszaadotta, hogy a telepítési parancs sikertelen volt. |
| (0x87D1313C) | A hálózati kapcsolat megszakadt a frissített letöltési szolgáltatás URL-címének az eszközre való küldése során. Pontosabban nem található a megadott állomásnévvel rendelkező kiszolgáló. |
| az iOS-eszköz jelenleg foglalt. (0x87D11388) | Az iOS-eszköz foglalt, ami hibát eredményezett. Az eszköz zárolva van. A felhasználónak fel kell oldania az eszköz zárolását az alkalmazás telepítéséhez. |
| Az alkalmazás telepítése nem sikerült. (0x87D13B64) | Alkalmazás-telepítési hiba történt. a hiba megoldásához iOS-konzol naplói szükségesek. |
| Az alkalmazás felügyelt, de a felhasználó lejárt vagy el lett távolítva. (0x87D13B66) | Vagy a felhasználó explicit módon eltávolította az alkalmazást, vagy az alkalmazás lejárt, de nem tölthető le, vagy az alkalmazás észlelése nem felel meg az eszköz válaszának. Emellett a hibát az iOS 9.2.2 platform egyik hibája is okozhatja. |
| Az alkalmazás telepítésre van ütemezve, de a tranzakció elvégzéséhez szükség van egy beváltási kódra. (0x87D13B60) | Ez a hiba általában olyan iOS-es áruházbeli alkalmazásokban fordul elő, amelyek fizetős alkalmazások. |
| A telepítés sikeres befejezése után az alkalmazás nem észlelhető. (0x87D1041C) | Az alkalmazás észlelési folyamata nem felelt meg az eszköz válaszának. |
| A felhasználó elutasította az alkalmazás telepítésére vonatkozó ajánlatot. (0x87D13B62) | Az alkalmazás kezdeti telepítésekor a felhasználó a Mégse gombra kattintott. Kérje meg a felhasználót, hogy fogadja el a telepítési kérelmet a következő alkalommal. |
| A felhasználó elutasította az alkalmazás frissítésére vonatkozó ajánlatot. (0x87D13B63) | A végfelhasználó rákattint a Mégse gombra a frissítési folyamat során. Szükség szerint telepítse az üzembe helyezést, vagy oktatja a felhasználót, hogy fogadja el a frissítési kérést. |
| Ismeretlen hiba (0x87D103E8) | Ismeretlen alkalmazás-telepítési hiba történt. Ez a hiba akkor következik be, ha más hibák nem történtek meg. |
| A VPP-alkalmazásokat csak megosztott iPadre lehet telepíteni (-2016330861). | Az alkalmazásokat a Apple Volume Purchase Program használatával kell beszerezni egy megosztott iPaden való telepítéshez. |
| Nem lehet alkalmazásokat telepíteni, ha az App Store le van tiltva (-2016330860). | Az App Store-nak engedélyezve kell lennie ahhoz, hogy a felhasználó telepítse az alkalmazást. |
| Nem található a VPP-licenc az alkalmazáshoz (-2016330859). | Próbálja meg visszavonni és újból hozzárendelni az alkalmazás licencét. |
| A rendszeralkalmazások nem telepíthetők a MDM-szolgáltatóval (-2016330858). | Az iOS operációs rendszer által előre telepített alkalmazások telepítése nem támogatott. |
| Nem lehet alkalmazásokat telepíteni, ha az eszköz elveszett módban van (-2016330857). | Az eszköz minden használata elveszett módban van letiltva. Az elveszett üzemmód letiltása az alkalmazások telepítéséhez. |
| Az alkalmazások nem telepíthetők, ha az eszköz kioszk módban van (-2016330856). | Próbálja meg hozzáadni az eszközt egy kizárási csoporthoz a kioszk mód konfigurációs házirendjéhez az alkalmazások telepítéséhez. |
| Az 32-bites alkalmazások nem telepíthetők erre az eszközre (-2016330852). | Az eszköz nem támogatja a 32 bites alkalmazások telepítését. Próbálja meg telepíteni az alkalmazás 64 bites verzióját. |
| A felhasználónak be kell jelentkeznie az App Store-ba (-2016330855). | Az alkalmazás telepítésének megkezdése előtt a felhasználónak be kell jelentkeznie az alkalmazás-áruházba. |
| Ismeretlen probléma. Próbálkozzon újra (-2016330854). | Az alkalmazás telepítése ismeretlen ok miatt meghiúsult. Próbálkozzon újra később. |
| Az alkalmazás telepítése nem sikerült. Az Intune újra próbálkozik az eszköz következő szinkronizálásakor (-2016330853). | Az alkalmazás telepítése eszköz hibába ütközött. Az eszköz szinkronizálásával próbálja megismételni az alkalmazás telepítését. |
| A licenc-hozzárendelés nem sikerült – Apple Error "No VPP-licencek megmaradt" (0x87d13b7e) | Ezt a működésmód szándékos. Ennek megoldásához vásároljon további VPP-licenceket, vagy igényeljen licenceket a felhasználóktól már nem megcélozva. |
| Az alkalmazás telepítési hibája 12024: ismeretlen ok. (0x87d13b6e) | Az Apple nem adott nekünk elegendő információt a telepítés okának meghatározásához. Nincs jelentés. |
| A szükséges alkalmazás-konfigurációs házirend nem található, győződjön meg arról, hogy a házirend ugyanahhoz a csoporthoz van rendelve. (0x87d13b7f) | Az alkalmazáshoz az alkalmazás konfigurációja szükséges, de nincs megcélozva az alkalmazás konfigurációja. A rendszergazdának meg kell győződnie arról, hogy az alkalmazáshoz tartozó csoportokat is megcélozta a csoportok számára szükséges alkalmazás-konfiguráció. |
| Az eszköz VPP-licencelése csak az iOS 9.0 + rendszerű eszközökön használható. (0x87d13b69) | Az érintett iOS-eszközök frissítése az iOS 9.0 + verzióra. |
| Az alkalmazás telepítve van az eszközön, de nem felügyelt. (0x87d13b8f) | Ez a hiba csak LOB-alkalmazásokban fordul elő. Az alkalmazás az Intune-on kívül lett telepítve. A hiba megoldásához távolítsa el az alkalmazást az eszközről. Amikor legközelebb megtörténik az eszköz szinkronizálása, az eszköznek telepítenie kell az alkalmazást az Intune-ból. |
| Felhasználó által elutasított app Management (0x87d13b68) | Kérje meg a felhasználót, hogy fogadja el az alkalmazások felügyeletét. |
| Ismeretlen hiba. (0x87d1279d) | Ez a hiba az iOS áruházbeli alkalmazások esetében fordul elő, de a hiba forgatókönyve ismeretlen. |
| Az alkalmazás legújabb verziója nem tudott frissíteni egy korábbi verzióról. (0x87D13B9D) | Ez a hibaüzenet akkor jelenik meg, ha az alkalmazás telepítve van és felügyelt, de a helytelen verziója van az eszközön. Ez a helyzet akkor is vonatkozik, amikor egy eszköz megkapta az alkalmazás frissítésére szolgáló parancsot, de az új verzió még nincs telepítve és nem jelentett vissza. A rendszer ezt a hibát fogja jelenteni az eszköz első beadásához a frissítés telepítése után, és akkor következik be, amikor az eszköz nem jelenti az új verzió telepítését, vagy egy másik hiba miatt meghiúsul.  |


### <a name="other-installation-errors"></a>Egyéb telepítési hibák

|  Hibaüzenet/kód  |  Description  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (ügyfél-hiba)  |  Az alkalmazás telepítéséhez közvetlen telepítést lehetővé tevő rendszerrel kell rendelkeznie. Győződjön meg arról, hogy az alkalmazáscsomag megbízható aláírással van aláírva, és telepítve van egy tartományhoz csatlakoztatott eszközön, amelyen engedélyezve van a **AllowAllTrustedApps** házirend, vagy egy olyan eszköz, amelyen engedélyezve van a **AllowAllTrustedApps** szabályzat, és amely rendelkezik Windows közvetlen telepítési-licenccel. További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).   |
|  0x80073CF0  |  A csomag nem nyitható meg. Lehetséges okok:<ul><li> A csomag nincs aláírva.</li><li> A közzétevő neve nem egyezik meg az aláíró tanúsítvány tulajdonosával.</li></ul> További információért olvassa el az **appxpackagingom eseménynaplóban talál** -eseménynaplót. További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CF3  |  A csomag nem tudta frissíteni, függőséget vagy ütközést érvényesíteni. Lehetséges okok:<ul><li> A bejövő csomag ütközik egy telepített csomaggal.</li><li> Nem található a megadott csomagfüggőség.</li><li> A csomag nem támogatja a megfelelő processzorarchitektúrát.</li></ul> További információért olvassa el a **AppXDeployment-Server** eseménynaplóját. További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CFB  |  A megadott csomag már telepítve van, és a csomag újratelepítése le van tiltva. Ez a hiba akkor jelenhet meg, ha olyan csomagot telepít, amely nem azonos a már telepített csomaggal. Ellenőrizze, hogy a csomag tartalmaz-e digitális aláírást. Ha újraépít vagy újra aláír egy csomagot, a csomag nem lesz bitenként azonos az előzőleg telepített csomaggal. Ez a hiba kétféleképpen javítható ki:<ul><li> Növelje az alkalmazás verziószámát, majd építse és írja alá újra a csomagot.</li><li> Az új csomag telepítése előtt távolítsa el a régi csomagot a rendszer minden felhasználója esetében.</li></ul> További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x87D1041C  |  Az alkalmazás telepítése sikeres volt, de a rendszer nem ismeri fel az alkalmazást. Az alkalmazást az Intune sikeresen telepítette, majd ezt követően eltávolította. Az alkalmazás eltávolításának okai a következők:<ul><li> A végfelhasználó eltávolította az alkalmazást.</li><li> A csomagban lévő azonosító adatok nem egyeznek meg a hibás alkalmazásokhoz tartozó eszközök jelentéseivel.</li><li>Az önfrissítő rendszercsomagok a termék verziója nem felel meg az alkalmazásnak az Intune-on kívüli frissítés utáni információjának.</li></ul> Kérje meg a felhasználót, hogy telepítse újra az alkalmazást a vállalati portálról. Vegye figyelembe, hogy a szükséges alkalmazások újratelepítése automatikusan megtörténik, amikor az eszköz következő bejelentkezik.  |
|  0x8000FFFF  |  Váratlan hiba történt a telepítés során. További információért olvassa el a telepítési naplókat.  |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>A Microsoft Áruházból származó alkalmazások hibáinak elhárítása

A [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (A Microsoft Áruházbeli alkalmazások csomagolási, telepítési és lekérdezési hibáinak elhárítása) című cikkben foglaltak segítenek elhárítani az alkalmazásoknak a Microsoft Áruházból akár Intune-nal, akár más módon történő telepítésekor tapasztalt gyakori problémákat.

## <a name="app-troubleshooting-resources"></a>Alkalmazás-hibaelhárítási erőforrások
- [A Visio és a Project üzembe helyezése az Office Pro Plus üzembe helyezésének részeként](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Végezze el az Intune-telepítéssel telepített MSfB alkalmazások Windows 10 1903 rendszeren való telepítését.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [MSI-alkalmazások központi telepítésének hibaelhárítása Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Ajánlott eljárások a szoftverek terjesztéséhez a klasszikus Intune-ban Windows PC-ügynök](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>További lépések

- További információt az Intune hibaelhárításáról a [Segítségnyújtás a céges felhasználóknak a hibaelhárítási portál használatával](../fundamentals/help-desk-operators.md) című témakörben talál. 
- Ismertető a Microsoft Intune esetleges ismert problémáiról. További információ: az [Intune-ügyfél sikeressége](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md).
