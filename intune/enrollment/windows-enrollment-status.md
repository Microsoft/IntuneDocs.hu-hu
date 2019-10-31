---
title: Regisztráció állapotának beállítása lap
titleSuffix: Microsoft Intune
description: Üdvözlő lap beállítása a Windows 10-es eszközök regisztrálására szolgáló felhasználók számára.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d69bd040929da08d7d23db764c5b01f6aca6a9ea
ms.sourcegitcommit: c38a856725993a4473ada75e669a57f75ab376f8
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73143176"
---
# <a name="set-up-an-enrollment-status-page"></a>Regisztráció állapotának beállítása lap
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
A regisztrációs állapot lap (ESP) megjeleníti a Windows 10-es eszközök telepítési adatait (1803-es és újabb verziók) a kezdeti eszközök regisztrációja során. Példa:
- a [Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/) használatakor 
- a beléptetési állapot lap házirend alkalmazása után a rendszer első alkalommal elindít egy felügyelt eszközt. 

A regisztrációs állapot lap segítségével a felhasználók megismerhetik az eszköz állapotát az eszköz beállítása során. Létrehozhat több regisztrációs állapot lap profilokat, és alkalmazhatja azokat a felhasználókat tartalmazó különböző csoportokba. A profilok a következőkre állíthatók be:
- A telepítési folyamat kijelzése.
- A használat tiltása a telepítés befejezéséig.
- Megadható, hogy mit tehet meg a felhasználó, ha az eszköz telepítése sikertelen.

Az egyes profilok prioritási sorrendjét úgy is beállíthatja, hogy az ütköző profilok hozzárendelései ugyanahhoz a felhasználóhoz legyenek felhasználva.

> [!NOTE]
> A beléptetési állapot lap csak egy hozzárendelt csoporthoz tartozó felhasználónak célozható meg, és a házirend az eszközön az eszközt használó összes felhasználó regisztrációjának időpontjában be van állítva.  

## <a name="available-settings"></a>Elérhető beállítások

 A beléptetési állapot lap viselkedésének testreszabásához a következő beállítások konfigurálhatók:

<table>
<th align="left">Beállítás<th align="left">Igen<th align="left">Nem
<tr><td>Alkalmazás-és profil telepítési folyamatának megjelenítése<td>Megjelenik a regisztráció állapota lap.<td>A regisztráció állapota lap nem jelenik meg.
<tr><td>Az eszköz használatának letiltása, amíg az összes alkalmazás és profil nincs telepítve<td>Az ebben a táblázatban szereplő beállítások elérhetővé válnak a beléptetési állapot lap működésének testreszabásához, hogy a felhasználó foglalkozzon a lehetséges telepítési problémákkal.
<td>A regisztrációs állapot lap a telepítési hibák megoldására szolgáló további beállítások nélkül jelenik meg.
<tr><td>Eszköz alaphelyzetbe állításának engedélyezése a felhasználók számára telepítési hiba esetén<td>Ha telepítési hiba történik, az <b>eszköz alaphelyzetbe állítása</b> gomb jelenik meg.<td>Az <b>eszköz alaphelyzetbe állítása</b> gomb nem jelenik meg, ha telepítési hiba történt.
<tr><td>Eszközök használatának engedélyezése a felhasználók számára telepítési hiba esetén<td>Ha a telepítés sikertelen, A <b>Folytatás továbbra</b> is gomb jelenik meg.<td>A <b>Folytatás egyébként</b> gomb nem jelenik meg, ha telepítési hiba történt.
<tr><td>Időtúllépési hiba megjelenítése, ha a telepítés a megadott számú percnél hosszabb időt vesz igénybe.<td colspan="2">Adja meg, hogy hány percig várjon a telepítés befejezésére. A rendszer 60 perc alapértelmezett értéket ad meg.
<tr><td>Egyéni üzenet megjelenítése hiba bekövetkezésekor<td>Meg kell adni egy szövegmezőt, ahol megadhatja a telepítési hiba esetén megjelenítendő egyéni üzenetet.<td>Az alapértelmezett üzenet jelenik meg: <br><b>telepítés túllépte a szervezet által beállított időkorlátot. Próbálkozzon újra, vagy kérjen segítséget az informatikai támogatási személytől.<b>
<tr><td>Naplók gyűjtésének engedélyezése a felhasználók számára telepítési hibákkal<td>Ha van telepítési hiba, megjelenik a <b>naplók gyűjtése</b> gomb. <br>Ha a felhasználó erre a gombra kattint, a rendszer megkéri, hogy válasszon egy helyet a naplófájl mentéséhez a <b>MDMDiagReport. cab fájlt.</b><td>A <b>naplók gyűjtése</b> gomb nem jelenik meg, ha telepítési hiba történt.
<tr><td>Az eszköz használatának letiltása, amíg ezek a szükséges alkalmazások telepítve vannak a felhasználóhoz vagy eszközhöz<td colspan="2">Válassza <b>az összes</b> <b>kijelölése</b>lehetőséget. <br><br>Ha ki van <b>választva</b> , az <b>alkalmazások kiválasztása</b> gomb jelenik meg, amellyel kiválaszthatja, hogy mely alkalmazásokat kell telepíteni az eszköz engedélyezése előtt.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Az összes felhasználó alapértelmezett regisztrációs állapotának bekapcsolása lap

A regisztráció állapota lap bekapcsolásához kövesse az alábbi lépéseket.
 
1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Windows-beléptetés** > **regisztráció állapota lapot**.
2. A **Beléptetés állapota oldal** panelen válassza az **Alapértelmezett** > **Beállítások** lehetőséget.
3. A **Show app and profile installation progress** (Alkalmazások és profilok telepítési állapotának megjelenítése) beállításnál válassza a **Yes** (Igen) lehetőséget.
4. Adja meg a többi kívánt beállítást, majd válassza a **Mentés** gombot.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Regisztrációs állapot lap profiljának létrehozása és társítása egy csoporthoz

1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Windows** -beléptetés > **regisztráció állapota lapot** > a **profil létrehozása**lehetőséget.
2. Adjon meg egy **nevet** és egy **leírást**.
3. Válassza a **Létrehozás** lehetőséget.
4. A **Regisztráció állapota oldal** listájában válassza ki az új profilt.
5. Válassza a **Hozzárendelések** > **Csoportok kiválasztása** területet, majd válassza ki a profillal ellátni kívánt csoportokat, végül válassza a **Kiválasztás** > **Mentés** lehetőséget.
6. Válassza a **Beállítások** területet, adja meg az a profilra alkalmazni kívánt beállításokat, majd válassza a **Mentés** lehetőséget.

## <a name="set-the-enrollment-status-page-priority"></a>Regisztrációs állapotlap prioritásának beállítása

A felhasználók számos csoportba tartozhatnak, és számos regisztrációs állapotú lap profilja lehet. Az ilyen ütközések kezeléséhez beállíthatja az egyes profilok prioritásait. Ha a regisztráció során egynél több regisztrációs állapotú oldal profilja van, akkor a rendszer csak a legmagasabb prioritású profilt alkalmazza a beléptetési eszközre.

1. Az [Intune](https://aka.ms/intuneportal)-ban válassza az **eszközök beléptetése** > **Windows-beléptetés** > **regisztráció állapota lapot**.
2. Vigye a kurzort a listában a profilra.
3. A függőleges három ponttal húzza a profilt a kívánt helyre a listában.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Eszköz hozzáférésének letiltása egy adott alkalmazás telepítése előtt

Megadhatja, hogy mely alkalmazásokat kell telepíteni, mielőtt a felhasználó el tudja érni az asztalt.

1. Az Intune-ban válassza az **eszközök beléptetése** > **Windows-beléptetés** > **regisztráció állapota lapot**.
2. Válassza ki a profil > **beállításait**.
3. Válassza az **Igen** lehetőséget az **alkalmazások és a profilok telepítési folyamatának megjelenítéséhez**.
4. Válassza az **Igen** lehetőséget az **eszköz használatának tiltása lehetőségre, amíg az összes alkalmazás és profil nincs telepítve**.
5. Válassza a **kijelölt** lehetőséget a **Letiltás eszköz használatára, amíg ezek a szükséges alkalmazások nem települnek a felhasználóhoz vagy eszközhöz**.
6. Válassza az **alkalmazások kiválasztása** lehetőséget > Válassza ki az alkalmazásokat > válassza a > **Mentés** **lehetőséget** .

## <a name="enrollment-status-page-tracking-information"></a>Regisztrációs állapot lap követési adatai

Három fázisban szerepel a regisztráció állapota lap a következővel:; eszköz-előkészítés, eszköz beállítása és fiók beállítása.

### <a name="device-preparation"></a>Eszköz előkészítése

Az eszközök előkészítéséhez a regisztráció állapota lapon a következő számok szerepelnek:
- Platformmegbízhatósági modul (TPM) kulcsának igazolása (ha alkalmazható)
- a Azure Active Directoryhoz való csatlakozás előrehaladása
- regisztrálás az Intune-ban
- Intune felügyeleti bővítmények telepítése

### <a name="device-setup"></a>Eszköz beállítása

A regisztráció állapota lap a következő eszközbeállítások elemeit követi nyomon (ha azok hozzá vannak rendelve az összes eszközhöz vagy egy olyan eszköz-csoporthoz, amelyben a beléptetési eszköz tagja):
- Biztonsági házirendek
  - Egy konfigurációs szolgáltató (CSP) az összes beléptetéshez.
  - Az Intune által konfigurált tényleges konfigurációs szolgáltatók nem jelennek meg itt.
- Alkalmazások
  - Gépenkénti üzletági (LoB) MSI-alkalmazások.
  - LoB-áruházbeli alkalmazások, melyek telepítési kontextusa „Device”.
  - Offline áruházbeli és LoB-áruházbeli alkalmazások, melyek telepítési kontextusa „Device”.
  - Win32-alkalmazások (csak Windows 10 1903-es és újabb verziók) 
- Csatlakozási profilok
  - A **Minden eszközhöz** vagy olyan eszközcsoporthoz hozzárendelt VPN- vagy Wi-Fi-profilok, amelyeknek az éppen regisztrált eszköz a tagja, de csak Autopilot-eszközök esetén
- A **Minden eszközhöz**, vagy olyan eszközcsoporthoz hozzárendelt tanúsítványprofilok, amelyeknek az éppen regisztrált eszköz a tagja, de csak Autopilot-eszközök esetén

### <a name="account-setup"></a>Fiók beállítása
A fiók beállításakor a regisztráció állapota lap a következő elemeket követi nyomon, ha azok hozzá vannak rendelve az aktuális bejelentkezett felhasználóhoz:
- Biztonsági házirendek
  - Egy konfigurációs szolgáltató minden beléptetéshez.
  - Az Intune által konfigurált tényleges konfigurációs szolgáltatók nem jelennek meg itt.
- Alkalmazások
  - Felhasználónkénti LoB MSI-alkalmazások, melyek társítása „Minden eszköz”, „Minden felhasználó” vagy egy olyan felhasználói csoport, amelynek az eszközt beléptető felhasználó a tagja.
  - Gépenkénti LoB MSI-alkalmazások, melyek társítása „Minden felhasználó” vagy egy olyan felhasználói csoport, amelynek az eszközt beléptető felhasználó a tagja.
  - Üzletági áruházbeli alkalmazások, online áruházbeli alkalmazások és offline tár alkalmazások, amelyek a következő objektumok bármelyikéhez vannak rendelve:
    - Minden eszköz
    - All Users
    - Egy felhasználói csoport, amelyben az eszköz regisztrálására szolgáló felhasználó tagja, a telepítési környezet felhasználói értékre van állítva.
  - Win32-alkalmazások (csak Windows 10 1903-es és újabb verziók) 
- Csatlakozási profilok
  - VPN- vagy Wi-Fi-profilok, melyek társítása „Minden felhasználó” vagy egy olyan felhasználói csoport, amelynek az eszközt beléptető felhasználó a tagja.
- Tanúsítványok
  - Tanúsítványprofilok, melyek társítása „Minden felhasználó” vagy egy olyan felhasználói csoport, amelynek az eszközt beléptető felhasználó a tagja.

### <a name="troubleshooting"></a>Hibaelhárítás
Hibaelhárítással kapcsolatos leggyakoribb kérdések.

- Miért nem lettek telepítve az alkalmazások a regisztrációs állapotot használó Autopilot-telepítés során az eszközök telepítési fázisában?
  - Annak biztosításához, hogy az alkalmazások a robotpilóta-eszköz telepítési fázisában legyenek telepítve, győződjön meg róla, hogy 
        1. Az alkalmazás úgy van kiválasztva, hogy letiltsa a hozzáférést a kiválasztott alkalmazások listájában.
        2. Az alkalmazásokat ugyanarra az Azure AD-eszköz csoportra célozza, amelyhez az Autopilot-profil hozzá van rendelve. 

- Miért jelenik meg a regisztrációs állapot lap a nem Autopilot-alapú központi telepítések esetén, például amikor egy felhasználó első alkalommal jelentkezik be Configuration Manager közös felügyeletű regisztrált eszközön?  
  - A regisztrációs állapot lap felsorolja az összes regisztrációs módszer telepítési állapotát, beleértve a következőket:
      - Autopilot
      - Közös felügyelet Configuration Manager
      - Ha minden új felhasználó bejelentkezik az eszközre, amely a regisztrációs állapot lap házirendjét először alkalmazza

- Hogyan lehet letiltani a beléptetési állapot lapot, ha az eszközön konfigurálva van?
  - A beléptetési állapot lap házirendje a regisztráció időpontjában van beállítva egy eszközön. A regisztráció állapota lap letiltásához le kell tiltania a felhasználók és eszközök regisztrációjának állapota lap szakaszt. Az egyéni OMA-URI beállítások létrehozásával letilthatja a szakaszt a következő konfigurációkkal.

      A felhasználó regisztrációjának állapota lap letiltása:

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      Az eszközök regisztrációjának állapota lap letiltása:

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- Hogyan gyűjthetem be a naplófájlokat?
  - Kétféle módon regisztrálhatók a regisztrációs állapot lap naplófájljai:
      - Lehetővé teszi a felhasználók számára naplók gyűjtését az ESP-házirendben. Ha a regisztráció állapota lapon időtúllépés történik, a végfelhasználó választhatja a **naplók gyűjtésének**lehetőségét. Egy USB-meghajtó beszúrásával a naplófájlok átmásolhatók a meghajtóra.
      - Nyisson meg egy parancssort a SHIFT-F10 billentyűkombináció megadásával, majd írja be a következő parancssort a naplófájlok létrehozásához: 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>Ismert problémák
Az alábbiakban ismert problémák merültek fel. 
- Az ESP-profil letiltása nem távolítja el az ESP-házirendet az eszközökről, és a felhasználók még mindig ESP-t kapnak, amikor első alkalommal jelentkeznek be az eszközre A házirendet nem távolítja el a rendszer, ha az ESP-profil le van tiltva. Az ESP letiltásához OMA-URI-t kell telepítenie. A fenti útmutatást követve megtudhatja, hogyan tilthatja le az ESP-t az OMA-URI használatával. 
- A függőben lévő újraindítás mindig időtúllépést eredményez. Az időtúllépés oka, hogy az eszközt újra kell indítani. Az újraindítás szükséges ahhoz, hogy a beléptetési állapot lapon nyomon kövessék az elem időpontját. Az újraindítás után a regisztrációs állapot lap kilép, és az újraindítás után az eszköz nem fog megjelenni a fiók beállítása során.  Vegye figyelembe, hogy az alkalmazás telepítése nem igényel újraindítást. 
- Az eszköz telepítése során a rendszer újraindítja a felhasználót, hogy adja meg a hitelesítő adatait, mielőtt átvált a fiók beállítása szakaszra. A felhasználói hitelesítő adatok nem őrződnek meg az újraindítás során. A felhasználónak meg kell adnia a hitelesítő adatait, majd a regisztráció állapota lap továbbra is megadható. 
- A regisztrációs állapot lap mindig időtúllépést mutat a munkahelyi és iskolai fiók beléptetése során a Windows 10 1903-nál kisebb verzióiban. A regisztrációs állapot lap megvárja, amíg az Azure AD-regisztráció befejeződik. A probléma a Windows 10 1903-es és újabb verzióiban van kijavítva.  
- A hibrid Azure AD Autopilot üzembe helyezése ESP-vel hosszabb időt vesz igénybe, mint az ESP-profilban definiált időtúllépési időtartam. A hibrid Azure AD Autopilot-telepítések esetén az ESP 40 percet vesz igénybe, mint az ESP-profilban beállított érték. Ez a késleltetés időt biztosít a helyszíni AD-összekötő számára az új eszköz rekordjának létrehozására az Azure AD-ben. 
- A Windows bejelentkezési oldal nincs előre kitöltve a felhasználónévvel az Autopilot-felhasználó által vezérelt módban. Ha a rendszer újraindítást indít az ESP eszköz telepítési fázisában:
    - a felhasználói hitelesítő adatok nem őrződnek meg
    - a felhasználónak újra meg kell adnia a hitelesítő adatokat, mielőtt továbblép az eszköz telepítési fázisáról a fiók telepítési szakaszába
- Az ESP hosszú ideig beragadt, vagy soha nem fejezi be az "azonosítás" fázist. Az Intune kiszámítja az ESP-házirendeket az azonosítási fázisban. Az eszköz nem végezheti el a számítástechnikai ESP-házirendeket, ha az aktuális felhasználónak nincs hozzárendelt Intune-licenccel.  
- A Windows Defender-alkalmazás vezérlésének konfigurálásakor a rendszer felszólítja az újraindításra az Autopilot során. A Windows Defender alkalmazás (AppLocker CSP) konfigurálása újraindítást igényel. Ha ez a házirend be van állítva, akkor az eszköz újraindítását okozhatja az Autopilot során. Jelenleg nem lehet letiltani vagy elhalasztani az újraindítást.
- Ha a DeviceLock-házirend (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) egy ESP-profil részeként van engedélyezve, az OOBE vagy a felhasználói asztal automatikus bejelentkezés két okból meghiúsulhat a unexpectantly.
  - Ha az eszköz nem lett újraindítva az ESP-eszköz telepítési fázisának bezárása előtt, a rendszer kérni fogja a felhasználótól, hogy adja meg az Azure AD-beli hitelesítő adatait. Ez a kérdés a sikeres automatikus bejelentkezés helyett akkor fordul elő, ha a felhasználó a Windows első bejelentkezési animációját látja.
  - A autologn sikertelen lesz, ha az eszköz újraindul, miután a felhasználó megadta az Azure AD-beli hitelesítő adatait, de az ESP-eszköz telepítési fázisának bezárása előtt. Ez a hiba azért fordul elő, mert az ESP-eszköz beállítási fázisa soha nem fejeződött be. A megkerülő megoldás az eszköz alaphelyzetbe állítása.

## <a name="next-steps"></a>További lépések
Ha végzett a Windows-alapú beléptetési lapok beállításával, ismerje meg, hogyan tudja kezelni a Windows-eszközöket. További információt [A Microsoft Intune-eszközfelügyelet ismertetése](../remote-actions/device-management.md) című témakörben talál.
