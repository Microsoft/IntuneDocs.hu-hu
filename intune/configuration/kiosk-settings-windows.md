---
title: Kioszkbeállítások a Windows 10 rendszerhez az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Konfigurálhatja a Windows 10 (és újabb) rendszerű eszközöket Egyalkalmazásos és többalkalmazásos kioszkként, testreszabhatja a Start menüt, alkalmazásokat adhat hozzá, megjelenítheti a tálcán, és konfigurálhat egy webböngészőt Microsoft Intuneban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2a94253934454bc9e176db8de0eec2454ddfee0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730579"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Windows 10 és újabb eszközbeállítások az Intune-ban való futtatáshoz

Windows 10 és újabb rendszerű eszközökön ezeket az eszközöket Egyalkalmazásos kioszk módban, vagy többalkalmazásos kioszk módban is futtathatja.

Ez a cikk a Windows 10 és újabb rendszerű eszközökön szabályozható különböző beállításokat sorolja fel és ismerteti. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja a Windows 10 és újabb rendszerű eszközök kioszk módban történő futtatásához.

Intune-rendszergazdaként ezeket a beállításokat az eszközökhöz is létrehozhatja és hozzárendelheti.

Az Intune Windows kioszk szolgáltatásával kapcsolatos további tudnivalókért tekintse meg a [kioszk beállításainak konfigurálása](../kiosk-settings.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

- [Hozza létre a profilt](kiosk-settings.md#create-the-profile).

- Ez a kioszk-profil közvetlenül kapcsolódik a [Microsoft Edge kioszk beállításainak](device-restrictions-windows-10.md#microsoft-edge-browser)használatával létrehozott eszköz-korlátozási profilhoz. Összefoglalás:

  1. Hozza létre ezt a kioszk-profilt az eszköz kioszk módban való futtatásához.
  2. Hozza létre az [eszköz korlátozási profilját](device-restrictions-windows-10.md#microsoft-edge-browser), és konfigurálja a Microsoft Edge-ben engedélyezett egyes szolgáltatásokat és beállításokat.

> [!IMPORTANT]
> Ügyeljen arra, hogy ezt a kioszk-profilt ugyanahhoz az eszközökhöz rendelje, mint a [Microsoft Edge-profilja](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>Egyetlen teljes képernyős alkalmazásos kioszkok

Csak egy alkalmazást futtat az eszközön.

- **Válasszon ki egy kioszk üzemmódot**: Válasszon **egy alkalmazást, teljes képernyős kioszkot**.

- **Felhasználói bejelentkezés típusa**: A felvenni kívánt alkalmazások a megadott felhasználói fiókkal futnak. A választható lehetőségek:

  - **Automatikus bejelentkezés (Windows 10 1803-es és újabb verziók)** : Olyan nyilvános környezetekben használható kioszkokon, amelyek nem igénylik a felhasználótól a bejelentkezést, a vendég fiókhoz hasonlóan. Ez a beállítás az [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)-t használja.
  - **Helyi felhasználói fiók**: Adja meg a helyi (eszköz) felhasználói fiókot. A megadott fiók bejelentkezik a kioszkba.

- **Alkalmazás típusa**: Válassza ki az alkalmazás típusát. A választható lehetőségek:

  - **Microsoft Edge böngésző hozzáadása**: Válassza ki a **Microsoft Edge böngészőt**, és válassza ki az **Edge kioszk mód típusát**:

    - **Digitális/interaktív aláírások**: Megnyit egy teljes URL-címet, és csak az adott webhelyen lévő tartalmat jeleníti meg. A [digitális jelek beállítása](https://docs.microsoft.com/windows/configuration/setup-digital-signage) a szolgáltatással kapcsolatos további információkat tartalmaz.
    - **Nyilvános böngészés (InPrivate)** : A Microsoft Edge korlátozott többoldalas verzióját futtatja. A felhasználók megkereshetik nyilvánosan vagy letölthetik a böngészési munkamenetet.

    További információ ezekről a lehetőségekről: a [Microsoft Edge kioszk mód üzembe helyezése](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Ezzel a beállítással engedélyezheti a Microsoft Edge böngészőt az eszközön. A Microsoft Edge-specifikus beállításainak konfigurálásához hozzon létre egy eszköz konfigurációs profilt (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **Windows 10** platformra > **eszköz korlátozásai**  >  **Microsoft Edge böngésző**). A [Microsoft Edge böngésző](device-restrictions-windows-10.md#microsoft-edge-browser) felsorolja és ismerteti a rendelkezésre álló beállításokat.

  - **Kioszk böngésző hozzáadása**: Válassza ki a **kioszk böngésző beállításait**. Ezek a beállítások vezérlik a böngészőalkalmazást kioszkmódban. Győződjön meg arról, hogy az áruházból beolvassa a [kioszk böngésző alkalmazást](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) , és adja hozzá az Intune-hoz [ügyfélalkalmazásként](../apps/apps-add.md). Ezután rendelje hozzá az alkalmazást a kioszk-eszközökhöz.

    Adja meg a következő beállításokat:

    - **Alapértelmezett Kezdőlap URL-címe**: Adja meg a kioszk böngésző megnyitásakor vagy a böngésző újraindításakor megjelenő alapértelmezett URL-címet. Például írja be a következőt: `http://bing.com` vagy `http://www.contoso.com`.

    - **Kezdőlap gomb**: A kioszk böngésző Kezdőlap gombjának **megjelenítése** vagy **elrejtése** . Alapértelmezés szerint a gomb nem jelenik meg.

    - **Navigációs gombok**: A továbbítási és a vissza gomb **megjelenítése** vagy **elrejtése** A navigációs gombok alapértelmezés szerint nem jelennek meg.

    - **Munkamenet befejezése gomb**: A befejezési munkamenet gomb **megjelenítése** vagy **elrejtése** Ha a gomb látható, és a felhasználó kiválasztja, akkor az alkalmazás megerősítést kér a munkamenet befejezéséhez. Megerősítés után a böngésző minden böngészési adatot (cookie-k, gyorsítótár stb.) töröl, majd megnyitja az alapértelmezett URL-címet. Alapértelmezés szerint a gomb nem jelenik meg.

    - **Böngésző frissítése üresjárati idő után**: Adja meg az üresjárati idő mennyiségét (1-1440 perc), amíg a kioszk böngésző nem indul újra friss állapotban. Az üresjárati idő az utolsó felhasználói beavatkozás óta eltelt percek száma. Alapértelmezés szerint az érték üres, ami azt jelenti, hogy a nincs üresjárati időkorlát.

    - **Engedélyezett webhelyek**: Ezzel a beállítással engedélyezheti a meghatározott webhelyek megnyitását. Más szóval, ezzel a beállítással korlátozhatja vagy megakadályozhatja a webhelyek megjelenítését az eszközön. Például engedélyezheti a `http://contoso.com*` összes webhelyének megnyitását. Alapértelmezés szerint az összes webhely engedélyezett.

      Adott webhelyek engedélyezéséhez töltse fel az engedélyezett webhelyek listáját különböző sorokban tartalmazó fájlt. Ha nem ad hozzá fájlt, az összes webhely használata engedélyezve lesz. Az Intune helyettesítő karakterként támogatja a `*` (csillag) karaktert.

      Az mintafájlnak a következő listához hasonlóan kell kinéznie:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`

    > [!NOTE]
    > A Microsoft kioszk böngészővel engedélyezett automatikus bejelentkezéssel rendelkező Windows 10-es Kioszkoknak offline licencet kell használniuk a vállalati Microsoft Store. Ennek a követelménynek az az oka, hogy az automatikus bejelentkezés Azure Active Directory (AD) hitelesítő adatokkal nem rendelkező helyi felhasználói fiókot használ. Így az online licenceket nem lehet kiértékelni. További információ: [Offline alkalmazások terjesztése](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Áruházbeli alkalmazás hozzáadása**: Válassza az **áruházbeli alkalmazás hozzáadása**lehetőséget, és válasszon egy alkalmazást a listából.

    Nincsenek alkalmazások a listában? Adjon hozzá néhányat az [Ügyfélalkalmazások](../apps/apps-add.md) rész lépéseinek használatával.
    
 - **Karbantartási időszak megadása az alkalmazások újraindításához**: Az alapértelmezett érték "nincs konfigurálva", a "require" (kötelező) beállítás megadásával a telepítés befejezéséhez újraindítás szükséges.
 
     Ha a kioszk böngésző vagy más Microsoft Store for Business alkalmazást használ, döntse el, hogy az alkalmazás telepítésének befejezéséhez milyen gyakran kell az újraindítást igénylő alkalmazás-frissítéseket megkeresni. Ha nincs konfigurálva, a Microsoft Store for Business alkalmazások az alkalmazás frissítését követően 3 nappal nem ütemezett időpontban lesznek újraindítva.
     
     - **Karbantartási időszak kezdő időpontja**: Válassza ki a nap dátumát és időpontját, hogy megkezdje az ügyfelek ellenőrzését az újraindítást igénylő alkalmazások frissítéseinek ellenőrzéséhez. Az alapértelmezett indítási idő éjfél vagy nulla perc.
     
     - **Karbantartási időszak ismétlődése**: Az alapértelmezett érték naponta.
         Állítsa be, hogy a karbantartási időszakok milyen gyakran történjenek az alkalmazások frissítései számára. A javaslat napi rendszerességgel elkerülheti a nem ütemezett alkalmazások újraindítását.

  [ApplicationManagement/ScheduleForceRestartForUpdateFailures CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)

## <a name="multi-app-kiosks"></a>Többalkalmazásos kioszk

Az ebben az üzemmódban lévő alkalmazások elérhetők a Start menüben. A felhasználó kizárólag ezeket az alkalmazásokat tudja megnyitni. Ha egy alkalmazás egy másik alkalmazástól függ, mindkettőnek szerepelnie kell az engedélyezett alkalmazások listájában. Például az Internet Explorer 64-bites verziójának függősége van az Internet Explorer 32-bites verzióján, ezért engedélyeznie kell a "C:\Program Files\internet explorer\iexplore.exe" és a "C:\Program Files (x86) \Internet Explorer\iexplore.exe" szolgáltatást. 

- **Válasszon ki egy kioszk üzemmódot**: Válassza a **többalkalmazásos kioszk**lehetőséget.

- **Windows 10 megcélzása S módú eszközökön**:
  - **Igen**: Lehetővé teszi az áruházbeli alkalmazások és AUMID alkalmazások (Win32-alkalmazások kizárása) használatát a kioszk profilban.
  - **Nem**: Az áruházbeli alkalmazások, Win32-alkalmazások és AUMID alkalmazások tárolásának engedélyezése a kioszk profilban. Ez a kioszk-profil nincs telepítve az S módú eszközökön.

- **Felhasználói bejelentkezés típusa**: A felvenni kívánt alkalmazások a megadott felhasználói fiókkal futnak. A választható lehetőségek:

  - **Automatikus bejelentkezés (Windows 10 1803-es és újabb verziók)** : Olyan nyilvános környezetekben használható kioszkokon, amelyek nem igénylik a felhasználótól a bejelentkezést, a vendég fiókhoz hasonlóan. Ez a beállítás az [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)-t használja.
  - **Helyi felhasználói fiók**: **Adja hozzá** a helyi (eszköz) felhasználói fiókot. A megadott fiók bejelentkezik a kioszkba.
  - **Azure ad-felhasználó vagy-csoport (Windows 10 1803-es és újabb verziók)** : Válassza a **Hozzáadás**lehetőséget, majd válassza ki az Azure ad-felhasználók vagy-csoportok elemet a listából. Több felhasználót és csoportot is kiválaszthat. A módosítások mentéséhez válassza az **Választ** gombot.
  - **HoloLens-látogató**: A látogatói fiók egy olyan vendégfiók, amely nem igényel felhasználói hitelesítő adatokat vagy hitelesítést a [megosztott számítógépes üzemmód fogalmai](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)című témakörben leírtak szerint.

- **Böngésző és alkalmazások**: Adja hozzá az alkalmazásokat a kioszk eszközön való futtatáshoz. Ne feledje, hogy több alkalmazást is hozzáadhat.

  - **Böngészők**

    - **Microsoft Edge hozzáadása**: A Microsoft Edge bekerül az alkalmazás rácsára, és minden alkalmazás futtatható ezen a kioszkon. Válassza ki a **Microsoft Edge kioszk mód típusát**:

      - **Normál mód (a Microsoft Edge teljes verziója)** : A Microsoft Edge teljes verzióját futtatja minden böngészési funkcióval. A rendszer menti a felhasználói és az állapotot a munkamenetek között.
      - **Nyilvános böngészés (InPrivate)** : A Microsoft Edge többoldalas verzióját futtatja a teljes képernyős módban futó kioszkok testreszabott felületével.

      További információ ezekről a lehetőségekről: a [Microsoft Edge kioszk mód üzembe helyezése](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Ezzel a beállítással engedélyezheti a Microsoft Edge böngészőt az eszközön. A Microsoft Edge-specifikus beállításainak konfigurálásához hozzon létre egy eszköz konfigurációs profilt (**eszköz konfigurációja** > **profilok** > **profil létrehozása** > **Windows 10** platformra > **eszköz korlátozásai**  >  **Microsoft Edge böngésző**). A [Microsoft Edge böngésző](device-restrictions-windows-10.md#microsoft-edge-browser) felsorolja és ismerteti a rendelkezésre álló beállításokat.

    - **Kioszk böngésző hozzáadása**: Ezek a beállítások vezérlik a böngészőalkalmazást kioszkmódban. Böngészőalkalmazást a kioszkmódban lévő eszközökön az [ügyfélalkalmazások](../apps/apps-add.md) használatával kell üzembe helyeznie.

      Adja meg a következő beállításokat:

      - **Alapértelmezett Kezdőlap URL-címe**: Adja meg a kioszk böngésző megnyitásakor vagy a böngésző újraindításakor megjelenő alapértelmezett URL-címet. Például írja be a következőt: `http://bing.com` vagy `http://www.contoso.com`.

      - **Kezdőlap gomb**: A kioszk böngésző Kezdőlap gombjának **megjelenítése** vagy **elrejtése** . Alapértelmezés szerint a gomb nem jelenik meg.

      - **Navigációs gombok**: A továbbítási és a vissza gomb **megjelenítése** vagy **elrejtése** A navigációs gombok alapértelmezés szerint nem jelennek meg.

      - **Munkamenet befejezése gomb**: A befejezési munkamenet gomb **megjelenítése** vagy **elrejtése** Ha a gomb látható, és a felhasználó kiválasztja, akkor az alkalmazás megerősítést kér a munkamenet befejezéséhez. Megerősítés után a böngésző minden böngészési adatot (cookie-k, gyorsítótár stb.) töröl, majd megnyitja az alapértelmezett URL-címet. Alapértelmezés szerint a gomb nem jelenik meg.

      - **Böngésző frissítése üresjárati idő után**: Adja meg az üresjárati idő mennyiségét (1-1440 perc), amíg a kioszk böngésző nem indul újra friss állapotban. Az üresjárati idő az utolsó felhasználói beavatkozás óta eltelt percek száma. Alapértelmezés szerint az érték üres, ami azt jelenti, hogy a nincs üresjárati időkorlát.

      - **Engedélyezett webhelyek**: Ezzel a beállítással engedélyezheti a meghatározott webhelyek megnyitását. Más szóval, ezzel a beállítással korlátozhatja vagy megakadályozhatja a webhelyek megjelenítését az eszközön. Például engedélyezheti a `contoso.com*` összes webhelyének megnyitását. Alapértelmezés szerint az összes webhely engedélyezett.

        Adott webhelyek engedélyezéséhez töltse fel az engedélyezett webhelyek listáját tartalmazó .csv-fájlt. Ha nem ad hozzá .csv-fájlt, az összes webhely használata engedélyezve lesz.

      > [!NOTE]
      > A Microsoft kioszk böngészővel engedélyezett automatikus bejelentkezéssel rendelkező Windows 10-es Kioszkoknak offline licencet kell használniuk a vállalati Microsoft Store. Ennek a követelménynek az az oka, hogy az automatikus bejelentkezés Azure Active Directory (AD) hitelesítő adatokkal nem rendelkező helyi felhasználói fiókot használ. Így az online licenceket nem lehet kiértékelni. További információ: [Offline alkalmazások terjesztése](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Alkalmazások**

    - **Áruházbeli alkalmazás hozzáadása**: Vegyen fel egy alkalmazást a vállalati Microsoft Storeból. Ha nem találhatók alkalmazások a listában, akkor beszerezheti az alkalmazásokat, és [hozzáadhatja őket az Intune-hoz](../apps/store-apps-windows.md). Például a teljes képernyős böngészőt, az Excelt, a OneNote-ot és egyéb alkalmazásokat is hozzáadhat.

    - **Win32-alkalmazás hozzáadása**: A Win32-alkalmazások hagyományos asztali alkalmazások, például a Visual Studio Code vagy a Google Chrome. Adja meg a következő tulajdonságokat:

      - **Alkalmazás neve**: Kötelező. Adjon nevet az alkalmazásnak.
      - **Helyi elérési út**: Kötelező. Adja meg a végrehajtható fájl elérési útját, például `C:\Program Files (x86)\Microsoft VS Code\Code.exe` vagy `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **Alkalmazás felhasználói modell azonosítója (AUMID)** : Adja meg a Win32-alkalmazás alkalmazásfelhasználói modellben használt azonosítóját. Ez a beállítás meghatározza a csempe kezdő elrendezését az asztalon. Ennek az AZONOSÍTÓnak a beszerzéséhez lásd: [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

    - **Hozzáadás AUMID szerint**: Ezzel a beállítással adhat hozzá beérkezett fájlok Windows-alkalmazásokat, például a Jegyzettömböt vagy a számológépet. Adja meg a következő tulajdonságokat:

      - **Alkalmazás neve**: Kötelező. Adjon nevet az alkalmazásnak.
      - **Alkalmazás felhasználói modell azonosítója (AUMID)** : Kötelező. Adja meg a Windows-alkalmazás alkalmazásfelhasználói modellben használt azonosítóját. Az azonosító a [Telepített alkalmazás alkalmazásfelhasználói modellben használt azonosítójának megkeresése](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) című témakörben leírtak alapján kereshető meg.

    - **Autolaunch**: Nem kötelező. A felhasználó bejelentkezésekor válassza ki az újraindításhoz használandó alkalmazást. Csak egyetlen alkalmazás indítható el.
    - **Csempe mérete**: Kötelező. Válassza a Kicsi, Közepes, Széles és Nagy alkalmazáscsempe-méretek egyikét.

  > [!TIP]
  > Miután hozzáadta az összes alkalmazást, kattintással és húzással módosíthatja a megjelenítés sorrendjét az alkalmazások listájában.  

- **Alternatív indítási elrendezés használata**: Válassza az **Igen** lehetőséget egy olyan XML-fájl megadásához, amely leírja, hogyan jelennek meg az alkalmazások a Start menüben, beleértve az alkalmazások sorrendjét is. Használja ezt a beállítást, ha több testreszabási lehetőségre van szüksége a Start menüben. A [Start menü elrendezésének testreszabása és exportálása](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) című cikkben találhat útmutatást és XML-mintát.

- **Windows tálca**: Válassza a tálca **megjelenítését** vagy **elrejtését** . Alapértelmezés szerint a tálca nem jelenik meg. Az ikonok (például a Wi-Fi ikon) láthatók, de a végfelhasználók nem módosíthatják a beállításokat.

- **Letöltések mappa elérésének engedélyezése**: Válassza az **Igen** lehetőséget, hogy a felhasználók hozzáférhessenek a Windows Intéző letöltések mappájához. Alapértelmezés szerint a letöltések mappához való hozzáférés le van tiltva. Ez a funkció általában a böngészőből letöltött elemek elérésére használatos a végfelhasználók számára.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az [Android](device-restrictions-android.md#kiosk), az [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)és [a Windows holografikus for Business](kiosk-settings-holographic.md) rendszerű eszközökhöz is létrehozhat kioszk profilokat.
