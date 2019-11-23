---
title: Az Intune biztonsági alapkonfigurációinak beállításai Windows 10 MDM
titleSuffix: Microsoft Intune
description: Tekintse át a Windows MDM ügyfélkörnyezetre alapkonfigurációjának különböző verzióihoz tartozó alapértelmezett és elérhető beállításokat, amelyeket a Microsoft Intune kezelheti.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
zone_pivot_groups: windows-mdm-versions
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0be7627403cc95316a99e841127a137e0279ff1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508984"
---
# <a name="windows-mdm-security-baseline-settings-for-intune"></a>A Windows MDM biztonsági alapkonfigurációjának beállításai az Intune-ban
Tekintse meg a Microsoft Intune által támogatott MDM biztonsági alapbeállításokat a Windows 10 vagy újabb rendszerű eszközökön. Az alapkonfigurációban a beállítások alapértelmezett értékei az ajánlott konfigurációt jelentik a megfelelő eszközökhöz, és előfordulhat, hogy nem egyeznek meg a többi biztonsági alapkonfigurációtól vagy az alapkonfiguráció más verzióitól származó alapértékekkel.

- További információ a biztonsági alapkonfigurációk Intune-nal való használatáról és az alapkonfiguráció verziójának biztonsági alapkonfiguráció-profilokban való frissítéséről: biztonsági alapkonfigurációk [használata](../security-baselines.md).  
- A legújabb alapverzió a 2019-as **Mdm biztonsági** alapkonfiguráció.  
   
Ügyeljen arra, hogy kiválassza a megtekinteni kívánt alapterv verzióját.   

<!-- Cookies might be required to enable some browsers to display the zone options --> 
 

::: zone pivot="mdm-may-2019"  
**MDM biztonsági alapkonfiguráció a május 2019-es verziójához** 
> [!NOTE]  
> Az 2019-es Mdm biztonsági alapkonfigurációt a *május 2019 sablon esetében* általánosan elérhetőként (nem az előzetes verzióban) adták ki. A biztonsági alapterv ezen verziója helyettesíti a prvious alapkonfigurációt, *amely a 2018-es októberi Mdm biztonsági*alapkonfiguráció.  A május 2019 alapkonfigurációjának rendelkezésre állása előtt létrehozott profilok nem frissülnek, hogy tükrözzék a május 2019 verziójában található beállításokat és értékeket.  Bár az előnézeti sablon alapján nem hozhatók létre új profilok, szerkesztheti és tovább használhatja a korábban létrehozott profilokat az előnézeti sablon alapján. 

Ha többet szeretne megtudni arról, hogy mi változott az alapkonfiguráció az előző verzióban megadott verziójában, tekintse meg [az új sablon változásait](#whats-changed-in-the-new-template)ismertető témakört.  
::: zone-end

::: zone pivot="mdm-preview"
**Előzetes verzió – a MDM biztonsági alapterve október 2018**  
> [!NOTE]  
> Ez a MDM biztonsági alapkonfiguráció előzetes verziója, amely 2018 októberében jelent meg. Ezt az előzetes verziójú alapkonfigurációt a 2019-as számú *MDM 2019 biztonsági* alapkonfiguráció kiadásával, amely általánosan elérhető (nem előzetes verzióban). A *május 2019-es Mdm biztonsági* alapkonfigurációjának rendelkezésre állása előtt létrehozott profilok nem frissülnek, hogy TÜKRÖZZÉK a Mdm biztonsági alaptervében a 2019-es verzióra vonatkozó beállításokat és értékeket. Bár az előnézeti sablon alapján nem hozhatók létre új profilok, szerkesztheti és tovább használhatja a korábban létrehozott profilokat az előnézeti sablon alapján. 
::: zone-end

::: zone pivot="mdm-may-2019,mdm-preview"
## <a name="above-lock"></a>Zárolás felett  
További információ: [Policy CSP-AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) a Windows dokumentációjában.  

- **Bejelentési értesítések megjelenítésének tiltása**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy az alkalmazás értesítései megjelenjenek a zárolási képernyőn. Ha engedélyezi ezt a házirend-beállítást, akkor a zárolási képernyőn nem jelennek meg alkalmazás-értesítések. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználók kiválaszthatják, hogy mely alkalmazások jelenítsék meg az értesítéseket a zárolási képernyőn.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Alapértelmezett**: igen  
::: zone-end
::: zone pivot="mdm-may-2019" 
- **Alkalmazások hang aktiválása zárolt képernyőről**  

  **Alapértelmezett**: letiltva
::: zone-end

::: zone pivot="mdm-may-2019,mdm-preview"  
## <a name="app-runtime"></a>Alkalmazás futtatókörnyezete    
További információ: [Policy CSP-AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) a Windows dokumentációjában.  

- **Microsoft-fiókok választhatók a Windows áruházbeli alkalmazásokhoz**  
  Ezzel a házirend-beállítással szabályozhatja, hogy a Microsoft-fiókok választhatók-e olyan Windows áruházbeli alkalmazásokhoz, amelyekhez fiók szükséges a bejelentkezéshez. Ez a szabályzat csak az azt támogató Windows áruházbeli alkalmazásokat érinti. Ha engedélyezi ezt a házirend-beállítást, a Windows áruházbeli alkalmazások, amelyek általában a bejelentkezéshez Microsoft-fiók igényelnek, lehetővé teszik a felhasználók számára a vállalati fiókkal való bejelentkezést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználóknak Microsoft-fiók kell bejelentkezniük.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Alapértelmezett**: engedélyezve  

## <a name="application-management"></a>Alkalmazások kezelése   
További információ: [Policy CSP-ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) a Windows dokumentációjában.  
::: zone-end

::: zone pivot="mdm-may-2019"
- **Felhasználók felügyeletének tiltása a telepítéseken**  
  Ezzel a házirend-beállítással a felhasználók módosíthatják azokat a telepítési beállításokat, amelyek jellemzően csak rendszergazdák számára érhetők el. Ha engedélyezi ezt a házirend-beállítást, a Windows Installer egyes biztonsági funkcióit a rendszer figyelmen kívül hagyja. Lehetővé teszi a telepítés befejezését, mert a biztonsági szabálysértés miatt leáll. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a Windows Installer biztonsági funkciói megakadályozzák, hogy a felhasználók a rendszergazdák számára fenntartott telepítési beállításokat használják, például megadhatják azt a könyvtárat, amelyre a fájlok telepítve vannak. Ha Windows Installer észleli, hogy egy telepítőcsomag engedélyezte a felhasználó számára egy védett beállítás módosítását, leállítja a telepítést, és megjelenít egy üzenetet. Ezek a biztonsági funkciók csak akkor működnek, ha a telepítőprogram olyan rendszerjogosultságú biztonsági környezetben fut, amelyben hozzáfér a felhasználónak elutasítottak könyvtáraihoz. Ez a házirend-beállítás kevésbé korlátozó környezetekhez készült. A használatával megkerülheti a szoftverek telepítését megakadályozó telepítőprogram hibáit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Alapértelmezett**: igen

- **MSI-alkalmazások telepítésének letiltása emelt szintű jogosultságokkal**  
  Ezzel a házirend-beállítással a Windows Installer emelt szintű engedélyek használhatók, amikor a rendszerre telepít bármely programot.  
  - *Ha engedélyezi ezt a házirend-beállítást*, a rendszer minden programra kiterjeszti a jogosultságokat. Ezek a jogosultságok általában olyan programok számára vannak fenntartva, amelyek hozzá vannak rendelve a felhasználóhoz (az asztalon elérhető), a számítógéphez (automatikusan telepített) f, vagy elérhetővé válnak a Vezérlőpult Programok telepítése és törlése segédprogramjában. Ez a Profilbeállítások lehetővé teszi, hogy a felhasználók olyan programokat telepítsenek, amelyek hozzáférést igényelnek a címtárakhoz, amelyekhez a felhasználónak nincs engedélye a megtekintésre vagy a módosításra, beleértve a nagymértékben korlátozott számítógépeken lévő
  - *Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást*, akkor a rendszer az aktuális felhasználó engedélyeit alkalmazza, amikor olyan programokat telepít, amelyeket a rendszergazda nem terjeszt el vagy biztosít. Megjegyzés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználói konfigurációs mappákban is megjelenik. Ahhoz, hogy ez a házirend-beállítás érvényes legyen, mindkét mappában engedélyeznie kell azt. Vigyázat: a gyakorlott felhasználók kihasználhatják az engedélyek előnyeit ezzel a házirend-beállítással, hogy megváltoztassák a jogosultságokat, és állandó hozzáférést szerezzenek a korlátozott fájlokhoz és mappákhoz. Vegye figyelembe, hogy a házirend-beállítás felhasználói konfigurációs verziója nem garantált, hogy biztonságos legyen.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Alapértelmezett**: igen
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"
- **Játék DVR blokkolása (csak asztali verzió)**  
  Annak konfigurálása, hogy engedélyezett-e a játékok rögzítése és közvetítése.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Alapértelmezett**: igen  

## <a name="auto-play"></a>Automatikus lejátszás   
További információ: [Policy CSP-Robotpilota](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) a Windows dokumentációjában.  

- **Automatikus lejátszás alapértelmezett automatikus futtatási viselkedése**  
  Ez a beállítás hatással van az automatikus futtatási parancsok alapértelmezett viselkedésére. Az automatikus futtatási parancsok az Autorun. inf fájlban tárolódnak, és a telepítőprogramokat vagy más rutinokat indíthatnak el. Ha ez a *beállítás engedélyezve van*, a rendszergazdák megváltoztathatják a Windows Vista vagy újabb rendszert futtató eszközök alapértelmezett automatikus futtatási viselkedését. A viselkedés beállítható a következőre: a) teljesen letilthatja az automatikus futtatási parancsokat, vagy b) visszatérhet a Windows Vista előtti működésre, amely automatikusan végrehajtja az Autorun parancs futtatását. Ha a beállítás *Letiltva* vagy *nincs konfigurálva*értékre van állítva, akkor a Windows Vista vagy újabb rendszerű eszközök megkérik a felhasználót, hogy az Autorun parancs fusson.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Alapértelmezett**: nem hajtható végre  
  
- **Automatikus lejátszási mód**  
  Ez a házirend-beállítás lehetővé teszi az automatikus lejátszás funkció kikapcsolását. Az automatikus lejátszás megkezdi a meghajtóról való beolvasást, amint adathordozót szúr be a meghajtóba. Ennek eredményeképpen a programok telepítési fájlja és a hanganyagokon megjelenő zene azonnal elindul. A Windows XP SP2 előtt az automatikus lejátszási szolgáltatás alapértelmezés szerint le van tiltva a cserélhető meghajtókon, például a hajlékonylemez-meghajtón (de nem a CD-ROM-meghajtón) és a hálózati meghajtókon. A Windows XP SP2 verziótól kezdődően az automatikus lejátszás engedélyezve van a cserélhető meghajtókon, beleértve a zip-meghajtókat és néhány USB háttértár-eszközt is. Ha engedélyezi ezt a házirend-beállítást, az automatikus lejátszási funkció le van tiltva a CD-ROM-és cserélhető adathordozó-meghajtókon, vagy le van tiltva az összes meghajtón. Ezzel a házirend-beállítással a további típusú meghajtókon letiltja az Automatikus lejátszást. Ezzel a beállítással nem engedélyezheti az Automatikus lejátszást azon meghajtókon, amelyeken a szolgáltatás alapértelmezés szerint le van tiltva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az automatikus lejátszás engedélyezve van. Megjegyzés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználói konfigurációs mappákban is megjelenik. Ha a házirend-beállítások ütköznek, a számítógép konfigurációjában a házirend-beállítás elsőbbséget élvez a felhasználói konfiguráció házirend-beállításával szemben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Alapértelmezett**: letiltva

- **Nem mennyiségi eszközök automatikus lejátszásának letiltása**  
  Ez a házirend-beállítás nem engedélyezi az Automatikus lejátszást az MTP-eszközök, például a kamerák vagy a telefonok számára. Ha engedélyezi ezt a házirend-beállítást, az automatikus lejátszás nem engedélyezett MTP-eszközökhöz, például fényképezőgépekhez vagy telefonokhoz. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az automatikus lejátszás engedélyezve van a nem mennyiségi eszközökhöz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Alapértelmezett**: engedélyezve  

## <a name="bitlocker"></a>BitLocker    
További információ: [Policy CSP-BitLocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) a Windows dokumentációjában.  

- **Bites zárolás cserélhető meghajtó házirendje**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, konfigurálhat egy titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtók, az operációsrendszer-meghajtók és a cserélhető adatmeghajtók számára egyenként. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067140) 

  A következő beállítással állíthatja be a cserélhető meghajtó cserélhető meghajtójának házirendjét:

  - **Titkosítás megkövetelése írási hozzáféréshez**  
    **Alapértelmezett**: igen  

::: zone-end
::: zone pivot="mdm-preview"

- **Bites zárolás cserélhető meghajtó házirendje**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, konfigurálhat egy titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtók, az operációsrendszer-meghajtók és a cserélhető adatmeghajtók számára egyenként. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067140) 

  A következő beállítással állíthatja be a cserélhető meghajtó cserélhető meghajtójának házirendjét:

  - **Titkosítás megkövetelése írási hozzáféréshez**  
    **Alapértelmezett**: igen  

  - **Titkosítási módszer**  
    **Alapértelmezett**: AES 256bit CBC  

- **Bit Locker rögzített meghajtó szabályzata**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, beállíthatja a titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtókhoz, az operációsrendszer-meghajtókhoz és a cserélhető adatmeghajtókhoz. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  
 
  A bit Locker rögzített meghajtó házirendje beállításnál adja meg a következő beállításokat: 
  - **Titkosítási módszer**
    **alapértelmezett**: AES 256bit XTS  

- **Bites zárolás rendszermeghajtó-házirendje**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, beállíthatja a titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtókhoz, az operációsrendszer-meghajtókhoz és a cserélhető adatmeghajtókhoz. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  

   A következő beállítások megadásával konfigurálhatja a rendszermeghajtó-házirendet:
  - **Titkosítási módszer**  
    **Alapértelmezett**: AES 256bit XTS  
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="browser"></a>Böngésző  
További információ: [szabályzat CSP-böngésző](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) a Windows dokumentációjában.  

- **SmartScreen megkövetelése a Microsoft Edge-hez**  
  A Microsoft Edge a Microsoft Defender SmartScreen (bekapcsolt) használatával védi a felhasználókat a lehetséges adathalászat-csalások és kártevő szoftverek alapértelmezés szerint. Emellett a felhasználók alapértelmezés szerint nem letilthatják (kikapcsolják) a Microsoft Defender SmartScreen szolgáltatását. A házirend engedélyezése kikapcsolja a Microsoft Defender SmartScreen szolgáltatást, és megakadályozza, hogy a felhasználók bekapcsolják azt. Ezt a házirendet ne konfigurálja úgy, hogy a felhasználók a Microsoft Defender SmartScreen szolgáltatást be-vagy kikapcsolják.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Alapértelmezett**: igen  
  
- **Rosszindulatú hely elérésének letiltása**  
  Alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Microsoft Defender SmartScreen-figyelmeztetéseit a potenciálisan kártékony helyekről, így azok továbbra is a webhelyre léphetnek. Ezzel a házirenddel azonban beállíthatja a Microsoft Edge-t, hogy megakadályozza a felhasználók számára a figyelmeztetések megkerülését, és blokkolja őket a helyről.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Alapértelmezett**: igen  
  
- **Nem ellenőrzött fájlok letöltésének tiltása**  
  Alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Microsoft Defender SmartScreen-figyelmeztetéseit a potenciálisan kártékony fájlokról, így továbbra is letöltheti a nem ellenőrzött fájlokat. A szabályzat engedélyezése megakadályozza, hogy a felhasználók megkerüljék a figyelmeztetéseket, és blokkolja a nem ellenőrzött fájlok letöltését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Alapértelmezett**: igen  
  
- **A Password Manager letiltása**  
  Alapértelmezés szerint a Microsoft Edge automatikusan a Password Managert használja, így a felhasználók helyileg is elérhetik a jelszavakat. A szabályzat letiltása korlátozza a Microsoft Edge használatát a Password Manager használatával. Ne konfigurálja ezt a házirendet, ha engedélyezni szeretné a felhasználók számára a jelszavak helyi mentését és kezelését a Password Manager használatával.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Alapértelmezett**: igen  
  
- **Tanúsítvány-hibák felülbírálásának megakadályozása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó figyelmen kívül hagyja a böngészést megszakító SSL/Transport Layer Security (SSL/TLS) tanúsítványokat (például a "lejárt", a "visszavont" vagy a "név eltérése" hibákat) az Internet Explorerben. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem folytathatja a böngészést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó dönthet úgy, hogy figyelmen kívül hagyja a tanúsítvány hibáit, és folytatja a böngészést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Alapértelmezett**: igen  

## <a name="connectivity"></a>Kapcsolat  
További információ: [Policy CSP – kapcsolat](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) a Windows dokumentációjában.  

- **Internetes letöltés letiltása a webes közzététel és az online rendezési varázslók számára**  
  Ezzel a házirend-beállítással adható meg, hogy a Windows letöltse-e a szolgáltatók listáját a webes közzétételi és az online rendezési varázslókhoz. Ezek a varázslók lehetővé teszik a felhasználók számára, hogy kiválasszák azon vállalatok listáját, amelyek olyan szolgáltatásokat biztosítanak, mint például az online tárterület és a fényképészeti nyomtatás. Alapértelmezés szerint a Windows a beállításjegyzékben megadott szolgáltatók mellett a Windows-webhelyről letöltött szolgáltatókat jeleníti meg. Ha engedélyezi ezt a házirend-beállítást, a Windows nem tölti le a szolgáltatókat, és csak azok a szolgáltatók jelennek meg, amelyek a helyi beállításjegyzékben vannak gyorsítótárazva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer letölti a szolgáltatók listáját, amikor a felhasználó a webes közzétételi vagy online rendezési varázslót használja. További információ a szolgáltatók beállításjegyzékbeli megadásáról: a webes közzététel és az online rendezés varázsló dokumentációja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Alapértelmezett**: engedélyezve  

::: zone-end
::: zone pivot="mdm-may-2019"
- **Az UNC elérési utak biztonságos elérésének konfigurálása**  
  Ezzel a házirend-beállítással biztonságos hozzáférést konfigurálhat az UNC elérési utakhoz. Ha engedélyezi ezt a házirendet, a Windows a további biztonsági követelmények teljesítése után csak a megadott UNC elérési utak elérését teszi lehetővé.
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067243) 

  **Alapértelmezett**: a Windows beállítása, hogy csak a további biztonsági követelmények teljesítése után engedélyezze a megadott UNC elérési utak elérését
  
  Ha a *Windows úgy van beállítva, hogy csak a további biztonsági követelmények teljesítése után engedélyezze a megadott UNC elérési utak elérését* , beállíthatja az * megerősített UNC elérési út listáját.
  - **Megerősített UNC elérési utak listája**  
    Válassza a **Hozzáadás** lehetőséget a további biztonsági jelzők és a kiszolgáló elérési útjának megadásához.  

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **A nyomtatóillesztők HTTP-n keresztüli letöltésének letiltása**  
  Ezzel a házirend-beállítással megadható, hogy az ügyfél letöltse-e a nyomtatóillesztő-csomagokat HTTP-n keresztül. HTTP-nyomtatás beállításához a nem beérkező illesztőprogramokat HTTP-n keresztül kell letölteni. Megjegyzés: Ez a házirend-beállítás nem akadályozza meg, hogy az ügyfél az intraneten vagy az interneten keresztül HTTP-n keresztül nyomtasson a nyomtatókra. Csak a helyileg telepített illesztőprogramok letöltését tiltja le. Ha engedélyezi ezt a házirend-beállítást, a nyomtatóillesztők nem tölthetők le HTTP-n keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználók HTTP-n keresztül tölthetnek le nyomtatóillesztőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Alapértelmezett**: engedélyezve  

<!-- here -->
## <a name="credentials-delegation"></a>Hitelesítő adatok delegálása  
További információ: [Policy CSP-CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) a Windows dokumentációjában.  

- **Nem exportálható hitelesítő adatok távoli gazdagép-delegálása**  
  A távoli gazdagép lehetővé teszi a nem exportálható hitelesítő adatok delegálását. A hitelesítő adatok delegálásakor az eszközök a hitelesítő adatok exportálható verzióját biztosítják a távoli gazdagép számára, amely lehetővé teszi a felhasználók számára a távoli gazdagépen lévő támadók által a hitelesítő adatok ellopásának kockázatát. Ha engedélyezi ezt a házirend-beállítást, a gazdagép támogatja a korlátozott rendszergazdai vagy távoli hitelesítő adatok Guard üzemmódot. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a korlátozott felügyelet és a távoli hitelesítőadat-őr mód nem támogatott. A felhasználónak mindig meg kell adnia a hitelesítő adatait a gazdagépen.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Alapértelmezett**: engedélyezve  

## <a name="credentials-ui"></a>Hitelesítő adatok felhasználói felülete  
További információ: [Policy CSP-CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) a Windows dokumentációjában.  

- **Rendszergazdák számbavétele** Ezzel a házirend-beállítással szabályozható, hogy a rendszergazdai fiókok megjelenjenek-e, amikor egy felhasználó egy futó alkalmazást próbál meg emelni. Alapértelmezés szerint a rendszergazdai fiókok nem jelennek meg, amikor a felhasználó egy futó alkalmazást próbál meg emelni. Ha engedélyezi ezt a házirend-beállítást, a számítógép összes helyi rendszergazdai fiókja megjelenik, így a felhasználó kiválaszthatja az egyiket, és megadhatja a megfelelő jelszót. Ha letiltja ezt a házirend-beállítást, a felhasználóknak mindig meg kell adnia egy felhasználónevet és egy jelszót a jogosultságszint-emeléshez.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Alapértelmezett**: letiltva  

## <a name="data-protection"></a>Adatvédelem  
További információ: [Policy CSP-DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) a Windows dokumentációjában.  

- **Közvetlen memória-hozzáférés letiltása**  
  Ezzel a házirend-beállítással letilthatja a közvetlen memória-hozzáférést (DMA) az összes melegen csatlakoztatható PCI-porthoz, amíg a felhasználó be nem jelentkezik a Windowsba. Miután a felhasználó bejelentkezik, a Windows feljegyzi a gazdagéphez csatlakozó PCI-portokhoz csatlakozó PCI-eszközöket. Minden alkalommal, amikor a felhasználó zárolja a gépet, a rendszer letiltja a DMA-t a gyermekek nélküli gyors csatlakozású PCI-portok esetében, amíg a felhasználó újra be nem jelentkezik. A gép zárolásának feloldása után már enumerált eszközök továbbra is működni fognak, amíg le nem húzta a gépet. Ez a házirend-beállítás csak akkor lép érvénybe, ha a BitLocker vagy az eszköz titkosítása engedélyezve van.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Alapértelmezett**: igen  

## <a name="device-guard"></a>Device Guard  
További információ: [Policy CSP-DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) a Windows dokumentációjában.  

- **Hitelesítőadat-őr**  
  Ezzel a beállítással a felhasználók bekapcsolhatják a hitelesítő adatokat a virtualizálás-alapú biztonsággal a hitelesítő adatok védelme érdekében a következő újraindításkor.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Alapértelmezett**: Engedélyezés UEFI-zárral 
::: zone-end
::: zone pivot="mdm-may-2019"

- **virtualizálás alapú biztonsági** 
  **alapértelmezett**: a vbs engedélyezése biztonságos rendszerindítással
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Virtualizációs alapú biztonság engedélyezése**  
  A virtualizálás-alapú biztonság (VBS) bekapcsolása a következő újraindításkor. A virtualizálás-alapú biztonság a Windows hipervizorral nyújt támogatást biztonsági szolgáltatásokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Alapértelmezett**: igen  

- **Rendszerőr elindítása**    
  **Alapértelmezett**: engedélyezve  

## <a name="device-installation"></a>Eszköz telepítése  
További információ: [Policy CSP-DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) a Windows dokumentációjában.  

- **Hardvereszközök telepítése eszköz-azonosítók alapján**  
  Ezzel a házirend-beállítással megadható azoknak az eszközöknek a Plug and Play-azonosítói és-kompatibilis azonosítói, amelyek nem telepíthetők a Windows rendszerben. Ez a házirend-beállítás elsőbbséget élvez minden más olyan házirend-beállítással szemben, amely lehetővé teszi, hogy a Windows telepítsen egy eszközt. Ha engedélyezi ezt a házirend-beállítást, a Windows megakadályozza, hogy olyan eszközt telepítsen, amelynek hardver-azonosítója vagy kompatibilis azonosítója megjelenik a létrehozott listában. Ha engedélyezi ezt a házirend-beállítást egy távoli asztali kiszolgálón, a házirend-beállítás a megadott eszközök távoli asztali ügyfélről a távoli asztali kiszolgálóra való átirányítását befolyásolja. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az eszközök az engedélyezettnek megfelelően telepíthetik és frissíthetik az eszközöket, és más házirend-beállítások is megtiltják azokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **Alapértelmezett**: hardvereszközök telepítésének letiltása  

  Ha a *hardveres eszköz telepítésének letiltása* lehetőség van kiválasztva, a következő beállítások érhetők el.

  - A **megfelelő hardvereszközök eltávolítása**   
    Ez a beállítás csak akkor érhető el, ha az *eszköz azonosítói alapján* a hardvereszköz telepítése *blokkolja a hardveres eszközök telepítését*.
    
    **Alapértelmezett**: igen

  - **A letiltott hardveres eszközök azonosítói**  
    Ez a beállítás csak akkor érhető el, ha az *eszköz azonosítói alapján* a hardvereszköz telepítése *blokkolja a hardveres eszközök telepítését*.
    
    **Alapértelmezett**: igen  
  
- **Hardvereszközök telepítése telepítési osztályok szerint**  
  Ezzel a házirend-beállítással megadhatja az eszközök telepítési osztályának globálisan egyedi azonosítókat (GUID azonosítókat) tartalmazó listáját azon eszközillesztők számára, amelyeket a Windows megakadályoz a telepítésben. Ez a házirend-beállítás elsőbbséget élvez minden más olyan házirend-beállítással szemben, amely lehetővé teszi, hogy a Windows telepítsen egy eszközt. Ha engedélyezi ezt a házirend-beállítást, a Windows megakadályozza azon eszközillesztők telepítését vagy frissítését, amelyek az eszköz telepítési osztályának GUID azonosítói megjelennek a létrehozott listában. Ha engedélyezi ezt a házirend-beállítást egy távoli asztali kiszolgálón, a házirend-beállítás a megadott eszközök távoli asztali ügyfélről a távoli asztali kiszolgálóra való átirányítását befolyásolja. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a Windows a házirend-beállításoknak megfelelően telepítheti és frissítheti az eszközöket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Alapértelmezett**: hardvereszközök telepítésének letiltása  

  Ha a *hardveres eszköz telepítésének letiltása* lehetőség van kiválasztva, a következő beállítások érhetők el.
  - A **megfelelő hardvereszközök eltávolítása**    
    Ez a beállítás csak akkor érhető el, ha a *telepítési osztályok által telepített hardvereszközök telepítése* *blokkolja a hardvereszközök telepítését*.  

    **Alapértelmezett**: *nincs alapértelmezett konfiguráció*  

  - **A letiltott hardveres eszközök azonosítói**  
    Ez a beállítás csak akkor érhető el, ha a *telepítési osztályok által telepített hardvereszközök telepítése* *blokkolja a hardvereszközök telepítését*.
    
    **Alapértelmezett**: *nincs alapértelmezett konfiguráció*  

## <a name="device-lock"></a>Eszköz zárolása  
További információ: [Policy CSP-DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) a Windows dokumentációjában.  

- **Kamera használatának megakadályozása**  
  Letiltja a zárolási képernyő kamera-kapcsolóját a számítógép beállításaiban, és megakadályozza, hogy a rendszer meghívja a kamerát a zárolási képernyőn. Alapértelmezés szerint a felhasználók a zárolási képernyőn is engedélyezhetik a rendelkezésre álló kamera meghívását. Ha engedélyezi ezt a beállítást, a felhasználók többé nem fogják tudni engedélyezni vagy letiltani a zárolási képernyő kamera-hozzáférését a számítógép beállításaiban, és a kamerát nem lehet meghívni a zárolási képernyőn.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Alapértelmezett**: engedélyezve  

- **Jelszó megkövetelése**  
  Megadja, hogy engedélyezve van-e az eszköz zárolása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Alapértelmezett**: igen  
  
  Ha a *jelszó megkövetelése* *Igen*értékre van állítva, a következő beállítások érhetők el.

  - **Jelszó minimális karakterkészletének száma**  
    Az erős PIN-kódokhoz vagy jelszóhoz szükséges összetett elemek (kis-és nagybetűk, számok és írásjelek) száma. A PIN-kód kikényszeríti a következő viselkedést az asztali és a mobileszközök esetében: 1 – 2 számjegyből és kisbetűkből álló karakterek esetén 3 számjegyű, kisbetűket és nagybetűket kell megadni. Asztali Microsoft-fiókok és tartományi fiókok esetében nem támogatott. 4 számjegyű, kisbetűket, nagybetűket és speciális karaktereket kell megadni. Az asztali verzióban nem támogatott. Az alapértelmezett érték az 1.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **Alapértelmezett**: 3  

  - **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**  
    Az eszköz törlése előtt engedélyezett hitelesítési hibák száma. A 0 érték letiltja az eszköz törlési funkcióját.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **Alapértelmezett**: 10  

  - **Jelszó érvényessége (nap)**  
    A jelszó maximális élettartama házirend-beállítás határozza meg, hogy mennyi ideig használható a jelszó, mielőtt a rendszer megköveteli a felhasználótól, hogy módosítsa azt. Beállíthatja, hogy a jelszavak egy 1 és 999 közötti számú nap elteltével lejárnak, vagy megadhatja, hogy a jelszavak soha ne járjanak le, ha a napok számát 0-ra állítja. Ha a jelszó maximális kora 1 és 999 nap közé esik, a jelszó minimális élettartama nem lehet kisebb, mint a jelszó maximális kora. Ha a jelszó maximális élettartama 0, akkor a jelszó minimális kora 0 és 998 nap közötti érték lehet.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **Alapértelmezett**: 60  

  - **Kötelező jelszótípus**  
    Meghatározza, hogy milyen típusú PIN-kód vagy jelszó szükséges.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **Alapértelmezett**: alfanumerikus  

  - **Jelszó minimális hossza**  
    A jelszó minimális hossza házirend-beállítás határozza meg, hogy hány karakterből állhat egy felhasználói fiók jelszava. Megadhat egy 1 és 14 karakter közötti értéket, vagy megadhatja, hogy nincs szükség jelszóra, ha a karakterek számát 0-ra állítja.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **Alapértelmezett**: 8  

  - **Egyszerű jelszavak letiltása**  
    Megadja, hogy engedélyezett-e a PIN-kód vagy a jelszavak (például "1111" vagy "1234"). Az asztal esetében a képjelszavak használatát is szabályozza.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **Alapértelmezett**: igen  
      *Az Igen beállítás meggátolja az egyszerű jelszavak használatát.* 

  - **Korábbi jelszavak újbóli használatának tiltása**  
    Meghatározza, hogy hány jelszó tárolható a nem használható előzményekben. Az érték tartalmazza a felhasználó aktuális jelszavát. Ha például az *1* értékre kattint, a felhasználó nem tudja újból felhasználni a jelenlegi jelszavát új jelszó kiválasztásakor. Az *5* beállítás azt jelenti, hogy a felhasználók nem állíthatják be az új jelszavukat a jelenlegi jelszavuk vagy az előző négy jelszavuk közül.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Alapértelmezett**: 24  

- **A diavetítés megakadályozása**  
  Letiltja a zárolási képernyő görgetősávjának beállításait a számítógép beállításaiban, és megakadályozza a diavetítés lejátszását a zárolási képernyőn. Alapértelmezés szerint a felhasználók engedélyezheti a diavetítést, amely a gép zárolása után fog futni. Ha engedélyezi ezt a beállítást, a felhasználók nem módosíthatják a számítógép beállításaiban a diavetítés beállításait, és nem indíthatnak el diavetítést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Alapértelmezett**: engedélyezve  
  *Az Engedélyezve beállítás megadásával megakadályozhatja a diavetítés futtatását.* 

- **Jelszó minimális kora (nap)**  
  A jelszó minimális élettartama házirend-beállítás határozza meg azt az időtartamot (nap), ameddig a felhasználónak meg kell változtatnia a jelszót. 1 és 998 nap közötti értéket adhat meg, vagy a jelszó módosításait azonnal engedélyezheti, ha a napok számát 0-ra állítja. A jelszó minimális élettartama nem lehet kisebb, mint a jelszó maximális kora, kivéve, ha a jelszó maximális élettartama 0 értékű, ami azt jelzi, hogy a jelszavak soha nem járnak le. Ha a jelszó maximális élettartama 0, akkor a jelszó minimális kora 0 és 998 közötti értékre állítható be.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Alapértelmezett**: 1  
::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="dma-guard"></a>DMA-őr  
További információ: [Policy CSP-DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) a Windows dokumentációjában.
- **A kernel DMA-védelemmel nem kompatibilis külső eszközök enumerálása**  
  A szabályzat célja, hogy további biztonságot nyújtson a külső DMA-kompatibilis eszközökhöz. Lehetővé teszi a külső DMA-kompatibilis eszközök enumerálásának nagyobb mértékű szabályozását, amely nem kompatibilis a DMA újramegfeleltetésével/az eszköz memóriájának elkülönítésével és a munkavégzéssel. Ez a szabályzat csak akkor lép érvénybe, ha a rendszer belső vezérlőprogramja támogatja a kernel DMA védelmét. A kernel DMA-védelem olyan platform-szolgáltatás, amely nem vezérelhető házirend vagy végfelhasználó által. A rendszernek a gyártáskor támogatottnak kell lennie. Annak vizsgálatához, hogy a rendszeren támogatott-e a kernel DMA-védelem, tekintse meg a kernel DMA-védelem mezőt az MSINFO32. exe összefoglalás lapján.  
  [További információ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Alapértelmezett**: az összes letiltása   
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="event-log-service"></a>Eseménynapló szolgáltatás  
További információ: [Policy CSP-EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) a Windows dokumentációjában.  

- **Biztonsági napló maximális fájlmérete KB-ban**  
  Ezzel a házirend-beállítással adható meg a naplófájl maximális mérete kilobájtban. Ha engedélyezi ezt a házirend-beállítást, a naplófájlok maximális méretét 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) értékre állíthatja kilobájtos növekményekben. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a naplófájl maximális mérete a helyileg konfigurált értékre van állítva. Ezt az értéket a helyi rendszergazda módosíthatja a napló tulajdonságai párbeszédpanelen, és az alapértelmezett érték 20 megabájt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Alapértelmezett**: 196608  

- **Rendszernapló maximális fájlmérete (KB)**  
  Ezzel a házirend-beállítással adható meg a naplófájl maximális mérete kilobájtban. Ha engedélyezi ezt a házirend-beállítást, a naplófájlok maximális méretét 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) értékre állíthatja kilobájtos növekményekben. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a naplófájl maximális mérete a helyileg konfigurált értékre van állítva. Ezt az értéket a helyi rendszergazda módosíthatja a napló tulajdonságai párbeszédpanelen, és az alapértelmezett érték 20 megabájt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Alapértelmezett**: 32768  

- **Alkalmazásnapló maximális fájlmérete KB-ban**  
  Ezzel a házirend-beállítással adható meg a naplófájl maximális mérete kilobájtban. Ha engedélyezi ezt a házirend-beállítást, a naplófájlok maximális méretét 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) értékre állíthatja kilobájtos növekményekben. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a naplófájl maximális mérete a helyileg konfigurált értékre van állítva. Ezt az értéket a helyi rendszergazda módosíthatja a napló tulajdonságai párbeszédpanelen, és az alapértelmezett érték 20 megabájt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Alapértelmezett**: 32768  

## <a name="experience"></a>Élmény  
További információ: [Policy CSP –](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) a Windows dokumentációjában található tapasztalat.  

- **A Windows reflektorfény letiltása**  
  Lehetővé teszi, hogy a rendszergazdák kikapcsolják az összes Windows reflektorfény-funkciót – ablak Reflektorfényben a zárolási képernyőn, a Windows-tippeket, a Microsoft fogyasztói funkcióit és egyéb kapcsolódó funkciókat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Alapértelmezett**: igen  

  Ha a *Windows reflektorfény letiltása* *Igen*értékre van állítva, a következő beállítások érhetők el.
  
  - **Harmadik féltől származó javaslatok letiltása a Windows reflektorfényben**  
    Megadja, hogy engedélyezi-e a harmadik féltől származó szoftvergyártók alkalmazás-és tartalmi javaslatainak használatát a Windows reflektorfényben, például a zárolási képernyő Spotlight, a javasolt alkalmazások a Start menüben és a Windows-tippek. A felhasználók továbbra is láthatják a Microsoft funkcióit, alkalmazásait és szolgáltatásait.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Alapértelmezett**: igen  
  - **A fogyasztói sajátosságok letiltása**  
    Lehetővé teszi a rendszergazdáknak, hogy csak a felhasználók számára, például a Start Suggestions, a tagsági értesítések, az OOBE utáni alkalmazások telepítése és a csempék átirányítása céljából bekapcsolják a felhasználói élményeket.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Alapértelmezett**: igen  

## <a name="exploit-guard"></a>Védelem kiaknázása  
További információ: [Policy CSP-ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) a Windows dokumentációjában.  

- **Védelem XML-kódjának kiaknázása**  
  Lehetővé teszi a rendszergazda számára egy olyan konfiguráció kiküldését, amely a kívánt rendszer-és alkalmazás-kockázatcsökkentő beállításokat jelöli a szervezet összes eszközén. A konfigurációt egy XML-fájl jelképezi. A védelem kiaknázásával megvédheti az eszközöket olyan kártevők ellen, amelyek kihasználják a kiaknázást és a fertőzést. A Windows biztonsági alkalmazás vagy a PowerShell használatával hozhat létre kockázatcsökkentő (más néven konfiguráció) készletet. Ezt követően exportálhatja ezt a konfigurációt XML-fájlként, és megoszthatja azt több, a hálózaton található géppel, hogy mindegyiknek ugyanazokat a kockázatcsökkentő beállításokat adja meg. Egy meglévő EMET konfigurációs XML-fájlt is konvertálhat, és importálhatja a biztonsági rés kiaknázása konfigurációs XML-fájlba.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Alapértelmezett**: *a minta XML-fájlja van megadva* 
 
## <a name="file-explorer"></a>Fájlkezelő  
További információ: [Policy CSP-fájlkezelő](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) a Windows dokumentációjában.  

- **Az adatvégrehajtás-megelőzés letiltása**  
  Az adatvégrehajtás megakadályozása lehetővé teszi bizonyos örökölt beépülőmodul-alkalmazások működésének leállítását az Explorer leállítása nélkül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Alapértelmezett**: letiltva  
   
- **A kupac megszakításának letiltása a Sérüléskor**  
  Ha letiltja a megszakított adatvesztést a sérülés miatt, bizonyos örökölt beépülőmodul-alkalmazások az Intéző azonnali leállítása nélkül is működhetnek, bár a tallózó a későbbiekben is váratlanul leállhat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Alapértelmezett**: letiltva  
    

## <a name="internet-explorer"></a>Internet Explorer  
További információ: [Policy CSP-InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) a Windows dokumentációjában.  

- **Az Internet Explorer korlátozott zónájának frissítései az állapotsorban parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájl engedélyezheti-e a zónán belüli állapotjelző sáv frissítését. 
  - *Ha engedélyezi ezt a házirend-beállítást*, a parancsfájl frissítheti az állapotsort.
  - *Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást*, a parancsfájl nem jogosult az állapotsor frissítésére.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Alapértelmezett**: letiltva
::: zone-end
::: zone pivot="mdm-may-2019"

- **Internet Explorer Internet Zone húz és eldobása, illetve fájlok másolása és beillesztése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók beilleszthetnek-e fájlokat, vagy másolhatnak és beilleszthetnek fájlokat a zónán belüli forrásokból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók áthelyezhetik a fájlokat, vagy automatikusan másolhatják és beilleszthetik a fájlokat a zónából. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat áthúzni vagy másolni. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak fájlokat húzni, vagy fájlokat másolni és beilleszteni a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók áthelyezhetik a fájlokat, vagy a zónából automatikusan másolhatják és beilleszthetik a fájlokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Alapértelmezett**: letiltás

- Az **Internet Explorer korlátozott zóna .net-keretrendszerének függő összetevői**    
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-ban nem aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy aláíratlan felügyelt összetevőket kíván-e végrehajtani. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláíratlan felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláíratlan felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Alapértelmezett**: letiltás


- **Az Internet Explorer helyi számítógép zónája ne futtasson antimalware-t az aktív X vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Alapértelmezett**: letiltva
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Internet Explorer Internet Zone-hozzáférés az adatforrásokhoz**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer hozzáférhet-e egy másik biztonsági zónából származó adatokhoz a Microsoft XML Parser (MSXML) vagy a ActiveX Data Objects (ADO) használatával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók betölthetnek egy olyan lapot a zónába, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a lap betöltését az MSXML vagy az ADO protokollt használó zónában a zóna egy másik helyéről származó adatok eléréséhez. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer korlátozott zónája különböző tartományokból származó tartalmat húzhat a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy az egyik tartományból egy másik tartományba húzza a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer 9 és korábbi verzióiban a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást az Internetbeállítások párbeszédpanelen.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Alapértelmezett**: letiltva
  
- **Az Internet Explorer-tanúsítvány címe nem megfelelő figyelmeztetés**  
  Ezzel a házirend-beállítással a tanúsítvány címe nem egyezik a biztonsági figyelmeztetéssel. Ha ez a házirend-beállítás be van kapcsolva, a rendszer figyelmezteti a felhasználót, amikor olyan biztonságos HTTP-(HTTPS-) webhelyeket látogat meg, amelyek egy másik webhely címeként kiállított tanúsítványokat jelennek meg Ez a figyelmeztetés segít megelőzni a hamisítás elleni támadásokat. Ha engedélyezi ezt a házirend-beállítást, a tanúsítvány címe nem megfelelő figyelmeztetés mindig megjelenik. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a tanúsítvány címe nem megfelelő figyelmeztetés jelenik-e meg (a Speciális lapon az Internet Vezérlőpulton).  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Alapértelmezett**: engedélyezve 
  
- **Az Internet Explorer korlátozott zónáinak kevésbé privilegizált helyei**  
  Ezzel a házirend-beállítással felügyelheti, hogy a webhelyek kevesebb jogosultsági szintű zónából, például internetes webhelyről is bejelentkezhetnek-e a zónába. Ha engedélyezi ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát. A biztonsági zóna a védelem által a zóna jogosultságszint-emelése biztonsági szolgáltatás által biztosított kiegészítő biztonsági réteg nélkül fog futni. Ha a legördülő listában a kérdés elemre kattint, egy figyelmeztetés jelenik meg a felhasználó számára, aki potenciálisan kockázatos navigálást végez. Ha letiltja ezt a házirend-beállítást, akkor a rendszer valószínűleg ártalmas navigálást végez. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a valószínűleg ártalmas navigálást. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer – korlátozott zóna – automatikus Rákérdezés a fájlok letöltésére**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználókat a nem felhasználó által kezdeményezett fájlok letöltésére Ettől a beállítástól függetlenül a felhasználók a fájl letöltése párbeszédpaneleket kapják meg a felhasználó által kezdeményezett letöltésekhez. Ha engedélyezi ezt a beállítást, a felhasználók egy fájl letöltése párbeszédpanelt kapnak az automatikus letöltési kísérletekhez. Ha letiltja vagy nem konfigurálja ezt a beállítást, a nem felhasználó által kezdeményezett fájlletöltés le van tiltva, és a felhasználók az értesítési sávot a fájl letöltése párbeszédpanel helyett láthatják. A felhasználók ezután rákattintanak az értesítési sávra a fájl letöltésének megadásához.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Alapértelmezett**: letiltva
  
- **Internet Explorer Internet Zone .NET-keretrendszerre vonatkozó függő összetevők**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-ban nem aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy aláíratlan felügyelt összetevőket kíván-e végrehajtani. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláíratlan felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Alapértelmezett**: letiltás 
  
- **Az Internet Explorer internetes zónája csak a jóváhagyott tartományok TDC ActiveX-vezérlők használatát engedélyezi**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználó futtathat-e TDC ActiveX-vezérlőt a webhelyeken. Ha engedélyezi ezt a házirend-beállítást, a TDC ActiveX-vezérlő nem fog futni a zónában lévő webhelyekről. Ha letiltja ezt a házirend-beállítást, a TDC aktív X vezérlő az ebben a zónában lévő összes helyről futni fog.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Alapértelmezett**: engedélyezve 
  
- **Az Internet Explorer korlátozott zónájának parancsfájlja kezdeményezte a Windowst**  
  Ezzel a házirend-beállítással felügyelheti a parancsfájl által kezdeményezett előugró ablakokat és windowsokat, amelyek tartalmazzák a címet és az állapotjelző sávokat. Ha engedélyezi ezt a házirend-beállítást, a Windows-korlátozások biztonsága nem lesz érvényes ebben a zónában. A biztonsági zóna a szolgáltatás által biztosított hozzáadott biztonsági réteg nélkül fut. Ha letiltja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Alapértelmezett**: letiltva 
  
- **Az Internet Explorer internetes zónája helyi elérési utat tartalmaz a fájlok kiszolgálóra való feltöltésekor**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer mikor küldje el a helyi elérési utat, amikor a felhasználó HTML-űrlapon keresztül tölt fel fájlokat. Ha a rendszer elküldje a helyi elérési utat, előfordulhat, hogy a kiszolgáló véletlenül nem tárt fel adatokat. Előfordulhat például, hogy a felhasználó asztaláról eljuttatott fájlok tartalmazzák a felhasználónevet az elérési út részeként. Ha engedélyezi ezt a házirend-beállítást, a rendszer az elérési út adatait akkor továbbítja, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha letiltja ezt a házirend-beállítást, a rendszer eltávolítja az elérésiút-információkat, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a rendszer elküldje-e az elérési utat, amikor feltölt egy fájlt egy HTML-űrlapon keresztül. Alapértelmezés szerint a rendszer az elérésiút-információkat elküldi.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Alapértelmezett**: letiltva 
  
- **Az Internet Explorer fokozottan védett módban tiltja le a folyamatokat**  
  Ez a házirend-beállítás határozza meg, hogy az Internet Explorer 11 a 64 bites folyamatokat (nagyobb biztonság esetén) vagy 32 bites folyamatokat (a nagyobb kompatibilitás érdekében) használja-e a Windows rendszerű, 64 bites verzióin a fokozottan védett módban. Fontos: Előfordulhat, hogy egyes ActiveX-vezérlők és eszköztárak nem érhetők el, ha 64 bites folyamatokat használ. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer 11 64 bites Tab-folyamatokat fog használni, amikor a Windows 64 bites verzióiban fokozottan védett módban fut. Ha letiltja ezt a házirend-beállítást, az Internet Explorer 11 32 bites Tab-folyamatokat fog használni, amikor a Windows 64 bites verzióiban fokozottan védett módban fut. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók az Internet Explorer beállításaival be-vagy kikapcsolhatják ezt a funkciót. Ez a funkció alapértelmezés szerint ki van kapcsolva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Alapértelmezett**: engedélyezve 
  
- **Internet Explorer – tanúsítvány-hibák figyelmen kívül hagyása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó figyelmen kívül hagyja a böngészést megszakító SSL/Transport Layer Security (SSL/TLS) tanúsítványokat (például a "lejárt", a "visszavont" vagy a "név eltérése" hibákat) az Internet Explorerben. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem folytathatja a böngészést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó dönthet úgy, hogy figyelmen kívül hagyja a tanúsítvány hibáit, és folytatja a böngészést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Alapértelmezett**: letiltva 
  
- **Internet Explorer Internet Zone XAML-fájlok betöltése**  
  Ezzel a házirend-beállítással kezelheti Extensible Application Markup Language-(XAML-) fájlok betöltését. A XAML egy XML-alapú deklaratív jelölési nyelv, amely gazdag felhasználói felületek és grafikák létrehozására szolgál, amelyek kihasználják a Windows megjelenítési alaprendszer. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a XAML-fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha a legördülő lista megadását kéri, a rendszer a felhasználótól kéri a XAML-fájlok betöltését. Ha letiltja ezt a házirend-beállítást, a XAML-fájlok nem töltődnek be az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó eldöntheti, hogy XAML-fájlokat kíván-e betölteni az Internet Explorerben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Alapértelmezett**: letiltás  

::: zone-end
::: zone pivot="mdm-may-2019"
- **Internet Explorer Internet Zone automatikus Rákérdezés a fájlok letöltésére**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználókat a nem felhasználó által kezdeményezett fájlok letöltésére Ettől a beállítástól függetlenül a felhasználók a fájl letöltése párbeszédpaneleket kapják meg a felhasználó által kezdeményezett letöltésekhez. Ha engedélyezi ezt a beállítást, a felhasználók egy fájl letöltése párbeszédpanelt kapnak az automatikus letöltési kísérletekhez. Ha letiltja vagy nem konfigurálja ezt a beállítást, a nem felhasználó által kezdeményezett fájlletöltés le van tiltva, és a felhasználók az értesítési sávot a fájl letöltése párbeszédpanel helyett láthatják. A felhasználók ezután rákattintanak az értesítési sávra a fájl letöltésének megadásához.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Alapértelmezett**: letiltva  
  
::: zone-end
::: zone pivot="mdm-preview"
- **Internet Explorer Internet Zone automatikus Rákérdezés a fájlok letöltésére**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználókat a nem felhasználó által kezdeményezett fájlok letöltésére Ettől a beállítástól függetlenül a felhasználók a fájl letöltése párbeszédpaneleket kapják meg a felhasználó által kezdeményezett letöltésekhez. Ha engedélyezi ezt a beállítást, a felhasználók egy fájl letöltése párbeszédpanelt kapnak az automatikus letöltési kísérletekhez. Ha letiltja vagy nem konfigurálja ezt a beállítást, a nem felhasználó által kezdeményezett fájlletöltés le van tiltva, és a felhasználók az értesítési sávot a fájl letöltése párbeszédpanel helyett láthatják. A felhasználók ezután rákattintanak az értesítési sávra a fájl letöltésének megadásához.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Alapértelmezett**: engedélyezve  
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Internet Explorer – korlátozott zóna biztonsági figyelmeztetése potenciálisan nem biztonságos fájlokhoz**  
  Ezzel a házirend-beállítással szabályozható, hogy a "fájl-biztonsági figyelmeztetés megnyitása" üzenet jelenik-e meg, amikor a felhasználó megpróbál megnyitni egy végrehajtható fájlt vagy más potenciálisan nem biztonságos fájlt (például egy intranetes fájlmegosztást a fájlkezelő használatával). Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a rendszer biztonsági figyelmeztetés nélkül nyitja meg a fájlokat. Ha a legördülő lista megadását kéri, a rendszer biztonsági figyelmeztetést jelenít meg a fájlok megnyitása előtt. Ha letiltja ezt a házirend-beállítást, akkor ezek a fájlok nem nyílnak meg. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a számítógép hogyan kezelje ezeket a fájlokat. Alapértelmezés szerint ezek a fájlok le vannak tiltva a korlátozott zónában, amely engedélyezve van az intranetes és a helyi számítógép zónában, és az interneten és a megbízható zónákban való rákérdezésre van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer Internet zóna helyközi parancsfájl-szűrő**  
  Ez a házirend azt szabályozza, hogy a helyek közötti parancsfájlok (XSS) szűrő felismeri-e és megakadályozza-e a helyek közötti parancsfájl-befecskendezést a zónában lévő webhelyeken. Ha engedélyezi ezt a házirend-beállítást, az XSS-szűrő be van kapcsolva a zónában található helyekhez, és az XSS-szűrő megkísérli blokkolni a helyek közötti parancsfájlok befecskendezését. Ha letiltja ezt a házirend-beállítást, az XSS-szűrő ki van kapcsolva az ebben a zónában lévő helyeknél, és az Internet Explorer engedélyezi a helyek közötti parancsfájlok befecskendezését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Alapértelmezett**: engedélyezve 
  
- **Az Internet Explorer tartalék SSL3**  
  Ezzel a házirend-beállítással letilthat egy nem biztonságos tartalékot az SSL 3,0-re. Ha ez a szabályzat engedélyezve van, az Internet Explorer az SSL 3,0-es vagy újabb verziójának használatával próbál csatlakozni a webhelyekhez, ha a TLS 1,0 vagy nagyobb hibát jelez. Azt javasoljuk, hogy ne engedélyezze a nem biztonságos tartalékot, hogy megakadályozza a személyes támadásokat. Ez a házirend nem befolyásolja, hogy mely biztonsági protokollok engedélyezettek. Ha letiltja ezt a házirendet, a rendszer az alapértelmezett értékeket használja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Alapértelmezett**: nincsenek helyek  
::: zone-end
::: zone pivot="mdm-may-2019"

- **Az Internet Explorer titkosításának támogatása**  
  Ezzel a házirend-beállítással kikapcsolhatja a Transport Layer Security (TLS) 1,0, TLS 1,1, TLS 1,2, SSL (SSL) 2,0 vagy SSL 3,0 támogatását a böngészőben. A TLS és az SSL olyan protokollok, amelyek segítenek a böngésző és a célkiszolgáló közötti kommunikáció védelmében. Amikor a böngésző megpróbál beállítani egy védett kommunikációt a célkiszolgálón, a böngésző és a kiszolgáló egyezteti a használandó protokollt és verziót. A böngésző és a kiszolgáló megpróbálta egyeztetni egymással a támogatott protokollok és verziók listáját, és kiválasztja a leginkább előnyben részesített egyezést. Ha engedélyezi ezt a házirend-beállítást, a böngésző egyezteti vagy nem egyeztet egy titkosítási alagutat a legördülő listából kiválasztott titkosítási módszerek használatával. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja a böngésző által támogatott titkosítási módszert.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Alapértelmezett**: 2 elem: TLS v 1.1 és TLS v 1.2  
  *Válassza a lefelé mutató nyilat a beállításhoz választható beállítások megjelenítéséhez.*
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Az Internet Explorer zárolta az Internet zóna intelligens képernyőjét**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyzés: az Internet Explorer 7 böngészőben ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Alapértelmezett**: engedélyezve 
  
- **Internet Explorer korlátozott zóna alkalmazások és fájlok elindítása iFrame-ben**  
  Ezzel a házirend-beállítással felügyelheti, hogy az alkalmazások futtathatók-e, és hogy a fájlok letölthetők-e a zónában lévő lapok HTML-ben lévő IFRAME-hivatkozásból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatják az alkalmazásokat, és fájlokat tölthetnek le a zóna oldalain lévő IFRAME ELEMEKből. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy szeretné-e futtatni az alkalmazásokat, és letölti a fájlokat a zóna lapjain lévő IFRAME elemek közül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak alkalmazásokat futtatni és fájlokat letölteni a zónában lévő lapok IFRAME ELEMEIből. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a felhasználók futtassák az alkalmazásokat, és fájlokat töltsenek le a zónában lévő lapok IFRAME ELEMEIből.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Alapértelmezett**: letiltás 
  
- **Internet Explorer – a nem gyakori fájlokra vonatkozó figyelmeztetések mellőzése az intelligens képernyőn**  
  Ezzel a házirend-beállítással adható meg, hogy a felhasználó megkerülhet-e a SmartScreen szűrőből származó figyelmeztetéseket. A SmartScreen szűrő figyelmezteti a felhasználót olyan végrehajtható fájlokra, amelyeket az Internet Explorer felhasználói általában nem töltenek le az internetről. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő figyelmeztetései letiltják a felhasználót. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó megkerülheti a SmartScreen szűrő figyelmeztetéseit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Alapértelmezett**: letiltva  
  
- **Internet Explorer Internet zóna előugró ablak blokkolása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a nemkívánatos előugró ablakok megjelenjenek-e. Az előugró ablak akkor nyílik meg, amikor a végfelhasználó egy hivatkozásra kattint. Ha engedélyezi ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg. Ha letiltja ezt a házirend-beállítást, a rendszer nem akadályozza meg az előugró ablakok megjelenését. Ha nem konfigurálja ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer az konzisztens MIME-kezelést dolgozza fel**  
  Az Internet Explorer dinamikus bináris viselkedést tartalmaz: olyan összetevők, amelyek adott funkciókat biztosítanak azon HTML-elemek számára, amelyekhez csatolva vannak. Ezzel a házirend-beállítással szabályozható, hogy a bináris viselkedés biztonsági korlátozásának beállítása meggátolható vagy engedélyezve van-e. Ha engedélyezi ezt a házirend-beállítást, a rendszer a Fájlkezelőben és az Internet Explorer folyamataiban nem akadályozza meg a bináris viselkedést. Ha letiltja ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer folyamatainak bináris viselkedése is engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a bináris viselkedést a fájlkezelő és az Internet Explorer folyamataiban.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Internet Explorer – korlátozott zóna – Java-engedélyek**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Alapértelmezett**: a Java letiltása  
    
  
- **Az Internet Explorer aktív X vezérlői védett módban**  
  Ezzel a házirend-beállítással megakadályozható, hogy az ActiveX-vezérlők védett módban fussanak, ha engedélyezve van a fokozottan védett mód. Ha a felhasználó olyan ActiveX-vezérlővel rendelkezik, amely nem kompatibilis a fokozottan védett móddal, és egy webhely megkísérli betölteni a vezérlőt, az Internet Explorer értesíti a felhasználót, és lehetővé teszi a webhely normál védelemmel ellátott módban történő futtatását. Ezzel a házirend-beállítással a rendszer letiltja ezt az értesítést, és az összes webhelyet fokozottan védett módban futtatja. A továbbfejlesztett védett mód további védelmet biztosít a rosszindulatú webhelyekkel szemben, ha 64 bites folyamatokat használ a Windows 64-bites verzióiban. A Windows 8 rendszerű számítógépek esetében a fokozottan védett mód is korlátozza az Internet Explorer által a beállításjegyzékből és a fájlrendszerből beolvasott helyeket. Ha a bővített védett mód engedélyezve van, és a felhasználó egy olyan webhelyre érkezik, amely nem kompatibilis a fokozottan védett móddal, az Internet Explorer értesíti a felhasználót, és lehetővé teszi a fokozottan védett üzemmód letiltását a következőre: adott webhelyre. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem teszi lehetővé a felhasználó számára a fokozottan védett üzemmód letiltását. Az összes védett mód webhelye fokozottan védett módban fog futni. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer értesíti a felhasználókat, és lehetőséget biztosít a nem kompatibilis ActiveX-vezérlőkkel rendelkező webhelyek normál védett módban való futtatására.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer korlátozott zónájának XAML-fájljainak betöltése**  
  Ezzel a házirend-beállítással kezelheti Extensible Application Markup Language-(XAML-) fájlok betöltését. A XAML egy XML-alapú deklaratív jelölési nyelv, amely gazdag felhasználói felületek és grafikák létrehozására szolgál, amelyek kihasználják a Windows megjelenítési alaprendszer. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a XAML-fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha a legördülő lista megadását kéri, a rendszer a felhasználótól kéri a XAML-fájlok betöltését. Ha letiltja ezt a házirend-beállítást, a XAML-fájlok nem töltődnek be az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó eldöntheti, hogy XAML-fájlokat kíván-e betölteni az Internet Explorerben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer parancsfájlokkal ellátható biztonsági korlátozásokat dolgoz fel**  
  Az Internet Explorer lehetővé teszi a parancsfájlok számára a különböző típusú ablakok programozott megnyitását, átméretezését és áthelyezését. Az ablak korlátozásai biztonsági funkció korlátozza a felugró ablakokat, és letiltja azokat a Windows-verziókat, amelyekben a cím és az állapotjelző sávok nem láthatók a felhasználó számára, vagy eltorzítják a többi Windows-címet és állapotjelző sávot. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlba állított Windows minden folyamat esetében korlátozott. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a megírt Windows nem korlátozott.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Alapértelmezett**: engedélyezve   
  
- **Internet Explorer – korlátozott zóna – aktív X vezérlők és beépülő modulok futtatása**  
  Ezzel a házirend-beállítással felügyelheti, hogy az ActiveX-vezérlők és a beépülő modulok futhatnak-e a megadott zónán lévő lapokon. Ha engedélyezi ezt a házirend-beállítást, a vezérlők és a beépülő modulok felhasználói beavatkozás nélkül is futtathatók. Ha a legördülő listában a kérdés lehetőséget választotta, a rendszer felkéri a felhasználókat arra, hogy engedélyezzék a vezérlők vagy a beépülő modul futtatását. Ha letiltja ezt a házirend-beállítást, a vezérlők és beépülő modulok nem futnak. Ha nem konfigurálja ezt a házirend-beállítást, a vezérlők és beépülő modulok nem futnak.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer korlátozott zónájának parancsfájljában aktív X vezérlők biztonságosként vannak megjelölve parancsfájlok futtatásához**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy biztonságosként megjelölt ActiveX-vezérlő képes-e a parancsfájlok kezelésére. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok interakciója automatikusan, felhasználói beavatkozás nélkül is megtörténhet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a parancsfájlok interakcióját. Ha letiltja ezt a házirend-beállítást, a parancsfájlok interakciója nem történik meg. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl-interakció megakadályozása nem történik meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer korlátozott zónájának bejelentkezési beállításai**  
  Ezzel a házirend-beállítással kezelheti a bejelentkezési beállítások beállításait. Ha engedélyezi ezt a házirend-beállítást, a következő bejelentkezési beállítások közül választhat. 
  - *Névtelen* – Névtelen bejelentkezés használata a http-hitelesítés letiltásához és a vendég fiók csak a Common Internet File System (CIFS) protokollhoz való használatához. 
  - A felhasználók felhasználói azonosítóinak és jelszavának lekérdezéséhez *kérje a* Felhasználónév és a jelszó megadását. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. 
  - *Automatikus bejelentkezés csak az intranet zónában* – ezzel a beállítással lekérdezheti a felhasználókat a többi zónában lévő felhasználói azonosítók és jelszavak számára. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. 
  - *Automatikus bejelentkezés a jelenlegi felhasználónévvel és jelszóval*– ezzel a beállítással megpróbálhatja bejelentkezni a Windows NT kérdéses válasz (más néven NTLM-hitelesítés) használatával. Ha a kiszolgáló támogatja a Windows NT kérdéses választ, a bejelentkezés a felhasználó hálózati felhasználónevét és jelszavát használja a bejelentkezéshez. Ha a kiszolgáló nem támogatja a Windows NT kérdéses választ, a rendszer lekérdezi a felhasználót, hogy megadja a felhasználónevet és a jelszót. 

  Ha letiltja ezt a házirend-beállítást, a bejelentkezés *csak az intranet zónában automatikus bejelentkezésre*van beállítva. Ha nem konfigurálja ezt a házirend-beállítást, a bejelentkezés a Felhasználónév és a jelszó *megadására* van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Alapértelmezett**: névtelen  
  
- **Az Internet Explorer megbízható zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer-kiszolgáló tanúsítvány-visszavonásának ellenőrzése**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer ellenőriznie fogja-e a kiszolgálók tanúsítványainak visszavonási állapotát. A rendszer visszavonja a tanúsítványokat, amikor azok sérülnek, vagy már nem érvényesek, és ez a beállítás védi a felhasználókat abban, hogy bizalmas adatokkal elküldjenek egy olyan webhelyre, amely hamis vagy nem biztonságos lehet. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer megtekinti, hogy a kiszolgálói tanúsítványok visszavonva lettek-e. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a kiszolgálói tanúsítványokat, hogy azok visszavonták-e őket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a kiszolgálói tanúsítványokat, hogy azok visszavonták-e őket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Alapértelmezett**: engedélyezve 
  
- **Internet Explorer Internet Zone less privilegizált helyek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a webhelyek a kevésbé privilegizált zónákból, például a tiltott helyekről is bejelentkezhetnek-e a zónába. Ha engedélyezi ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát. A biztonsági zóna a védelem által a zóna jogosultságszint-emelése biztonsági szolgáltatás által biztosított kiegészítő biztonsági réteg nélkül fog futni. Ha a legördülő listában a kérdés elemre kattint, egy figyelmeztetés jelenik meg a felhasználó számára, aki potenciálisan kockázatos navigálást végez. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza a valószínűleg ártalmas navigálást. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható. Ha nem konfigurálja ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer – korlátozott zóna fájljának letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a fájlok letöltése engedélyezett-e a zónából. Ezt a beállítást az oldal zónája határozza meg, amely a letöltést okozza, nem pedig azt a zónát, amelyről a fájlt leszállítják. Ha engedélyezi ezt a házirend-beállítást, a fájlok a zónából tölthetők le. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza a fájlok letöltését a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a fájlok letöltését a zónából.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer Internet zóna – az Authenticode-aláírással aláírt .NET-keretrendszerre támaszkodó összetevők futtatása**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-val aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláírt felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy végrehajtja-e az aláírt felügyelt összetevőket. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer megakadályozza az aktív X vezérlők felhasználónkénti telepítését**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy az ActiveX-vezérlők telepítése felhasználónkénti alapon történjen. Ha engedélyezi ezt a házirend-beállítást, az ActiveX-vezérlőket nem lehet felhasználónkénti alapon telepíteni. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor az ActiveX-vezérlők felhasználónkénti alapon telepíthetők.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer megakadályozza az intelligens képernyő-szűrő kezelését**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó kezelje a SmartScreen szűrőt, amely figyelmezteti a felhasználót, ha a meglátogatott webhelyről ismert, hogy csalárd kísérletet tesz személyes adatok gyűjtésére az "adathalászat" vagy a kártevő szoftverek üzemeltetése során. Ha engedélyezi ezt a házirend-beállítást, a rendszer nem kéri a felhasználót a SmartScreen szűrő bekapcsolására. A szűrők engedélyezése listán nem szereplő összes webhely címét a rendszer automatikusan elküldi a Microsoftnak a felhasználó értesítése nélkül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer felszólítja a felhasználót, hogy döntse el, hogy bekapcsolja-e a SmartScreen szűrőt az első futtatási élményben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer feldolgozza a MIME-elemzések biztonsági funkcióját**  
  Ezzel a házirend-beállítással megadható, hogy az Internet Explorer MIME-elemzése megakadályozza-e egy típusú fájl egy veszélyesebb fájltípusra való előléptetését. Ha engedélyezi ezt a házirend-beállítást, a MIME-elemzés soha nem fogja előléptetni az egyik típusú fájlt veszélyesebb fájltípusra. Ha letiltja ezt a házirend-beállítást, az Internet Explorer folyamatai lehetővé teszik a MIME-elemzések számára, hogy egy adott típusú fájlt egy veszélyesebb fájltípusra ösztönözzék. Ha nem konfigurálja ezt a házirend-beállítást, a MIME-elemzés soha nem előlépteti az egyik típusú fájlt veszélyesebb fájltípusra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Internet Explorer – korlátozott zóna – aláírt aktív X vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók letölthetik-e az aláírt ActiveX-vezérlőket a zóna egy oldaláról. Ha engedélyezi ezt a házirendet, a felhasználók felhasználói beavatkozás nélkül tölthetik le az aláírt vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a nem megbízható közzétevők által aláírt vezérlőket szeretné-e letölteni. A megbízható közzétevők által aláírt kód csendesen le van töltve. Ha letiltja a házirend-beállítást, az aláírt vezérlők nem tölthetők le. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy letöltötte-e a nem megbízható közzétevők által aláírt vezérlőket. A megbízható közzétevők által aláírt kód csendesen le van töltve.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer automatikus kiegészítése**  
  Ez az automatikus kiegészítési funkció megjegyezheti és javasolhatja a felhasználóneveket és a jelszavakat az űrlapokon. Ha engedélyezi ezt a beállítást, a felhasználó nem változtathatja meg a "felhasználónevek és jelszavak az űrlapokon" vagy "a jelszavak mentése" üzenetet. Az űrlapokon lévő felhasználónevek és jelszavak automatikus teljes funkciója be van kapcsolva. El kell döntenie, hogy kiválasztja-e a "jelszó mentése" üzenetet. Ha letiltja ezt a beállítást, a felhasználó nem változtathatja meg a "felhasználónevek és jelszavak az űrlapokon" vagy a "kérdés a jelszavak mentéséhez" lehetőséget. Az űrlapokon lévő felhasználónevek és jelszavak automatikus teljes funkciója ki van kapcsolva. A felhasználó nem dönthet úgy is, hogy kéri a jelszavak mentését. Ha nem konfigurálja ezt a beállítást, a felhasználónak lehetősége van az automatikus kiegészítés bekapcsolására az űrlapokon a Felhasználónév és a jelszó megadására, és a jelszavak mentésére is lehetőség van. A beállítás megjelenítéséhez a felhasználók megnyitják az Internetbeállítások párbeszédpanelt, kattintson a tartalom fülre, és kattintson a beállítások gombra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer internetes zónája a VBscript futtatásának engedélyezése**  
  Ezzel a házirend-beállítással eldöntheti, hogy a VBScript futtatható-e az adott Internet Explorer-zónákban lévő lapokon. A lehetőségek a következők: 
  - *Engedélyezés* – a VBScript az adott zónákban lévő lapokon, interakció nélkül fut. 
  - *Kérés* – az alkalmazottaknak meg kell adni, hogy engedélyezni kell-e a VBScript futtatását a zónában. 
  - A *disable* -VBScript nem fut a zónában. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a VBScript a megadott zónán belüli interakció nélkül fut.    

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer korlátozott zónája csak jóváhagyott tartományokat engedélyez a TDC aktív X-vezérlők használatához**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználó futtathat-e TDC ActiveX-vezérlőt a webhelyeken. Ha engedélyezi ezt a házirend-beállítást, a TDC ActiveX-vezérlő nem fog futni a zónában lévő webhelyekről. Ha letiltja ezt a házirend-beállítást, a TDC aktív X vezérlő az ebben a zónában lévő összes helyről futni fog.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer megbízható zónája nem futtat antimalware-t az aktív X vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Alapértelmezett**: letiltva 
  
- **Az Internet Explorer helyi számítógép-zónájának Java-engedélyei**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély közepes biztonsági értékre van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Alapértelmezett**: a Java letiltása 
  
- **Az Internet Explorer intranetes zónája nem futtat antimalware-t az aktív X vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Alapértelmezett**: letiltva  

- **Az Internet Explorer korlátozott zónájának Szkriptletek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó futtathat-e Szkriptletek. Ha engedélyezi ezt a házirend-beállítást, akkor a felhasználó futtathat Szkriptletek. Ha letiltja ezt a házirend-beállítást, a felhasználó nem tudja futtatni a Szkriptletek. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer az értesítési sávot dolgozza fel**  
  Ezzel a házirend-beállítással felügyelheti, hogy az értesítési sáv megjelenjen-e az Internet Explorer folyamataihoz, ha a fájl-vagy programkódok telepítése korlátozott. Alapértelmezés szerint az értesítési sáv az Internet Explorer folyamataihoz jelenik meg. Ha engedélyezi ezt a házirend-beállítást, megjelenik az értesítési sáv az Internet Explorer folyamataihoz. Ha letiltja ezt a házirend-beállítást, az értesítési sáv nem jelenik meg az Internet Explorer folyamataihoz. Ha nem konfigurálja ezt a házirend-beállítást, az értesítési sáv nem jelenik meg az Internet Explorer folyamataihoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Internet Explorer Internet Zone – aláírt ActiveX-vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók letölthetik-e az aláírt ActiveX-vezérlőket a zóna egy oldaláról. Ha engedélyezi ezt a házirendet, a felhasználók felhasználói beavatkozás nélkül tölthetik le az aláírt vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a nem megbízható közzétevők által aláírt vezérlőket szeretné-e letölteni. A megbízható közzétevők által aláírt kód csendesen le van töltve. Ha letiltja a házirend-beállítást, az aláírt vezérlők nem tölthetők le. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy letöltötte-e a nem megbízható közzétevők által aláírt vezérlőket. A megbízható közzétevők által aláírt kód csendesen le van töltve.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer korlátozott zónájának intelligens képernyője**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyzés: az Internet Explorer 7 böngészőben ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer az elavult aktív X vezérlőknél az idő futtatása gombjának eltávolítása**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy a felhasználók meglássák a "Futtatás ebben az időben" gombot, és az Internet Explorerben adott elavult ActiveX-vezérlőket futtasson. Ha engedélyezi ezt a házirend-beállítást, a felhasználók nem láthatják a figyelmeztető üzenet "Futtatás ideje" gombját, amely akkor jelenik meg, ha az Internet Explorer elavult ActiveX-vezérlőt blokkol. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználók az elavult ActiveX-vezérlőt blokkoló figyelmeztető üzenetben láthatják a "Futtatás ideje" gombot. Ha erre a gombra kattint, a felhasználó egyszer futtathatja az elavult ActiveX-vezérlőt. További információ: "elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Alapértelmezett**: engedélyezve 
  
- **Internet Explorer Internet Zone alkalmazások és fájlok elindítása iframe-ben**  
  Ezzel a házirend-beállítással felügyelheti, hogy az alkalmazások futtathatók-e, és hogy a fájlok letölthetők-e a zónában lévő lapok HTML-ben lévő IFRAME-hivatkozásból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatják az alkalmazásokat, és fájlokat tölthetnek le a zóna oldalain lévő IFRAME ELEMEKből. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy szeretné-e futtatni az alkalmazásokat, és letölti a fájlokat a zóna lapjain lévő IFRAME elemek közül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak alkalmazásokat futtatni és fájlokat letölteni a zónában lévő lapok IFRAME ELEMEIből. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy futtatják-e az alkalmazásokat, és fájlokat töltenek le a zóna lapjain lévő IFRAME elemek közül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Alapértelmezett**: letiltás 
  
- **Az Internet Explorer korlátozott zónája különböző tartományokban navigáljon a Windows és a keretek között**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer Internet Zone – intelligens képernyő**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyzés: az Internet Explorer 7 böngészőben ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer zárolta a megbízható zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Alapértelmezett**: a Java letiltása 
  
- **Internet Explorer-ellenőrzési aláírások a letöltött programokban**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer ellenőrizze-e a digitális aláírásokat (amely azonosítja az aláírt szoftverek közzétevőjét, és ellenőrzi, hogy nem módosította vagy módosították-e) a felhasználó számítógépeken a végrehajtható programok letöltése előtt. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer megtekinti a végrehajtható programok digitális aláírásait, és megjeleníti azok identitását, mielőtt letölti őket a felhasználói számítógépekre. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a végrehajtható programok digitális aláírásait, vagy a felhasználói számítógépekre való letöltés előtt megjeleníti az identitását. Ha nem konfigurálja ezt a házirendet, az Internet Explorer nem fogja megtekinteni a végrehajtható programok digitális aláírásait, vagy a felhasználói számítógépekre való letöltés előtt megjeleníti az identitását.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer korlátozott zónáinak parancsfájlkezelése webböngésző-vezérlőkkel**  
  Ezzel a házirend-beállítással megadható, hogy egy oldal képes-e a beágyazott WebBrowser vezérlők futtatására parancsfájl használatával. Ha engedélyezi ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés engedélyezett. Ha letiltja ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés nem engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a WebBrowser vezérlőhöz tartozó parancsfájlok elérését. Alapértelmezés szerint a WebBrowser vezérlőhöz való parancsfájl-hozzáférés csak a helyi gépen és az intranet zónában engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer korlátozott zónájának helyközi parancsfájl-szűrője**  
  Ez a házirend azt szabályozza, hogy a helyek közötti parancsfájlok (XSS) szűrő felismeri-e és megakadályozza-e a helyek közötti parancsfájl-befecskendezést a zónában lévő webhelyeken. Ha engedélyezi ezt a házirend-beállítást, az XSS-szűrő be van kapcsolva a zónában található helyekhez, és az XSS-szűrő megkísérli blokkolni a helyek közötti parancsfájlok befecskendezését. Ha letiltja ezt a házirend-beállítást, az XSS-szűrő ki van kapcsolva az ebben a zónában lévő helyeknél, és az Internet Explorer engedélyezi a helyek közötti parancsfájlok befecskendezését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer korlátozott zónájának bináris és parancsfájl-viselkedései**  
  Ezzel a házirend-beállítással kezelheti a dinamikus bináris és parancsfájl-viselkedést: olyan összetevőket, amelyek olyan HTML-elemek speciális funkcióit ágyazzák be, amelyekhez csatolva vannak. Ha engedélyezi ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés is elérhető. Ha a rendszergazda által jóváhagyott lehetőséget választja a legördülő listában, a rendszer csak a bináris viselkedések biztonsági korlátozási szabályzatában szereplő, a rendszergazda által jóváhagyott viselkedések területen felsorolt viselkedéseket jeleníti meg. Ha letiltja ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés nem érhető el, ha az alkalmazások egyéni biztonsági kezelőt implementáltak. Ha nem konfigurálja ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés nem érhető el, ha az alkalmazások egyéni biztonsági kezelőt implementáltak.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer biztonsági beállításainak bejelölése**  
  Ezzel a házirend-beállítással kikapcsolhatja a biztonsági beállítások ellenőrzése funkciót, amely ellenőrzi, hogy az Internet Explorer biztonsági beállításai meghatározzák-e, hogy a beállítások az Internet Explorert veszélyeztetik-e. Ha engedélyezi ezt a házirend-beállítást, a szolgáltatás ki van kapcsolva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a funkció be van kapcsolva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer Internet zóna biztonsági figyelmeztetése potenciálisan nem biztonságos fájlokhoz**  
  Ezzel a házirend-beállítással szabályozható, hogy a "fájl-biztonsági figyelmeztetés megnyitása" üzenet jelenik-e meg, amikor a felhasználó megpróbál megnyitni egy végrehajtható fájlt vagy más potenciálisan nem biztonságos fájlt (például egy intranetes fájlmegosztást a fájlkezelő használatával). Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a rendszer biztonsági figyelmeztetés nélkül nyitja meg a fájlokat. Ha a legördülő lista megadását kéri, a rendszer biztonsági figyelmeztetést jelenít meg a fájlok megnyitása előtt. Ha letiltja ezt a házirend-beállítást, akkor ezek a fájlok nem nyílnak meg. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a számítógép hogyan kezelje ezeket a fájlokat. Alapértelmezés szerint ezek a fájlok le vannak tiltva a korlátozott zónában, amely engedélyezve van az intranetes és a helyi számítógép zónában, és az interneten és a megbízható zónákban való rákérdezésre van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Alapértelmezett**: kérés  
  
- **Az Internet Explorer intranetes zónájának Java-engedélyei**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély közepes biztonsági értékre van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Alapértelmezett**: magas biztonság 
  
- Az **Internet Explorer elavult aktív X vezérlőket blokkol**   
  Ez a házirend-beállítás határozza meg, hogy az Internet Explorer blokkolja-e az elavult ActiveX-vezérlőket. Az intranetes zónában soha nem blokkolja az elavult ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer leállítja az elavult ActiveX-vezérlők blokkolását. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer továbbra is blokkol bizonyos elavult ActiveX-vezérlőket. További információ: "elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Internet Explorer korlátozott zóna felugró ablakának blokkolása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a nemkívánatos előugró ablakok megjelenjenek-e. Az előugró ablak akkor nyílik meg, amikor a végfelhasználó egy hivatkozásra kattint. Ha engedélyezi ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg. Ha letiltja ezt a házirend-beállítást, a rendszer nem akadályozza meg az előugró ablakok megjelenését. Ha nem konfigurálja ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer az MK protokoll biztonsági korlátozását dolgozza fel**  
  Az MK protokoll biztonsági korlátozási házirendjének beállítása csökkenti a támadási felületet az MK protokoll megakadályozásával. Az MK protokollon tárolt erőforrások sikertelenek lesznek. Ha engedélyezi ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer nem fogja tudni letiltani az MK protokollt, és az MK protokollon tárolt erőforrások sikertelenek lesznek. Ha letiltja ezt a házirend-beállítást, az alkalmazások használhatják az MK protokoll API-ját. Az MK protokollon tárolt erőforrások a Fájlkezelőben és az Internet Explorer folyamataiban is működni fognak. Ha nem konfigurálja ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer nem fogja tudni letiltani az MK protokollt, és az MK protokollon tárolt erőforrások sikertelenek lesznek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Alapértelmezett**: engedélyezve  
  
- Az **Internet Explorer megbízható zónájának Java-engedélyei**   
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély alacsony biztonsági értékre van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Alapértelmezett**: magas biztonság  
  
- **Az Internet Explorer korlátozott zónákon keresztüli parancsfájlkezelése Java-kisalkalmazások esetén**  
  Ezzel a házirend-beállítással felügyelheti, hogy a kisalkalmazások elérhetők-e a zónán belüli parancsfájlok számára. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok felhasználói beavatkozás nélkül automatikusan hozzáférhetnek a kisalkalmazásokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a parancsfájlok elérését a kisalkalmazásokhoz. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem férnek hozzá a kisalkalmazásokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok nem férnek hozzá a kisalkalmazásokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Alapértelmezett**: letiltás  
  
- Az **Internet Explorer zárolta a korlátozott zóna Java-engedélyeit**   
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Alapértelmezett**: a Java letiltása 
  
- **Az Internet Explorer internetes zónájában csak a jóváhagyott tartományok használhatják az ActiveX-vezérlőket**   
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer a felhasználótól az ActiveX-vezérlőt telepítő webhelytől eltérő webhelyeken is fusson. Ha engedélyezi ezt a házirend-beállítást, a rendszer arra kéri a felhasználót, hogy az ActiveX-vezérlők futtathatók legyenek a zónában található webhelyekről. A felhasználó dönthet úgy, hogy engedélyezi, hogy a vezérlő az aktuális helyről vagy az összes helyről fusson. Ha letiltja ezt a házirend-beállítást, a felhasználó nem látja a helyhez tartozó ActiveX-parancssort, és az ActiveX-vezérlők a zóna összes webhelyéről futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer minden hálózati elérési utat tartalmaz**  
  Az Internet Explorer minden hálózati elérési utat tartalmaz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Alapértelmezett**: letiltva 
  
- **Internet Explorer Internet zóna által védett üzemmód**  
  Ezzel a házirend-beállítással engedélyezheti a védett üzemmódot. A védett mód segít megvédeni az Internet Explorert a kihasznált biztonsági rések révén, ha csökkenti az Internet Explorer által a beállításjegyzékben és a fájlrendszerben írni kívánt helyeket. Ha engedélyezi ezt a házirend-beállítást, a védett mód be van kapcsolva. A felhasználó nem kapcsolhatja ki a védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a védett mód ki van kapcsolva. A felhasználó nem kapcsolhatja be a védett üzemmódot. Ha nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó be-vagy kikapcsolhatja a védett módot.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Alapértelmezett**: Engedélyezés 
  
- **Az Internet Explorer internetes zónájának inicializálása és a parancsfájlok aktív X vezérlők nem biztonságosakként vannak megjelölve**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Alapértelmezett**: letiltás 
  
- Az **Internet Explorer zárolta a korlátozott zóna intelligens képernyőjét**   
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyzés: az Internet Explorer 7 böngészőben ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer összeomlásának észlelése**  
  Ezzel a házirend-beállítással kezelheti a bővítmények felügyeletének összeomlás-észlelési funkcióját. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer összeomlása a Windows XP Professional Service Pack 1 és korábbi verziókban is megjelenik, nevezetesen a Windows hibajelentés meghívásához. A Windows hibajelentés összes házirend-beállítása továbbra is érvényben marad. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a beépülő modul felügyeletének összeomlás-észlelési funkciója működőképes.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Alapértelmezett**: letiltva  
  
- **Internet Explorer Internet Zone Java-engedélyek**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély magas biztonságra van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Alapértelmezett**: a Java letiltása  
  
- **Internet Explorer – korlátozott zóna – aktív parancsfájlok**  
  Ezzel a házirend-beállítással felügyelheti, hogy a zóna oldalain lévő parancsfájl-kód fut-e. Ha engedélyezi ezt a házirend-beállítást, a rendszer automatikusan futtathatja a zónában lévő lapokon található parancsfájl kódját. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezzék-e a parancsfájlok futtatását a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a zóna lapjain lévő parancsfájl-kód fusson. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a zóna lapjain lévő parancsfájl-kód ne fusson.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer Internet zóna bejelentkezési beállításai**  
  Ezzel a házirend-beállítással kezelheti a bejelentkezési beállítások beállításait. Ha engedélyezi ezt a házirend-beállítást, a következő bejelentkezési beállítások közül választhat. Névtelen bejelentkezés a HTTP-hitelesítés letiltásához és a vendég fiók csak a Common Internet File System (CIFS) protokollhoz való használatához. Kérje meg a felhasználónevet és a jelszót a felhasználók felhasználói azonosítók és jelszavak lekérdezéséhez. A felhasználó lekérdezése után ezeket az értékeket csendesen használhatja a munkamenet hátralévő részében. Automatikus bejelentkezés csak intranet zónában felhasználói azonosítók és jelszavak más zónákban való lekérdezéséhez. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. Automatikus bejelentkezés a jelenlegi felhasználónévvel és jelszóval a Windows NT kérdéses válasz (más néven NTLM-hitelesítés) használatával történő bejelentkezéshez. Ha a kiszolgáló támogatja a Windows NT kérdéses választ, a bejelentkezés a felhasználó hálózati felhasználónevét és jelszavát használja a bejelentkezéshez. Ha a kiszolgáló nem támogatja a Windows NT kérdéses választ, a rendszer lekérdezi a felhasználót, hogy megadja a felhasználónevet és a jelszót. Ha letiltja ezt a házirend-beállítást, a bejelentkezés csak az intranetes zónában automatikus bejelentkezésre van beállítva. Ha nem konfigurálja ezt a házirend-beállítást, akkor a bejelentkezés csak az intranetes zónában automatikus bejelentkezésre van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Alapértelmezett**: kérés  
  
- **Az Internet Explorer korlátozott zónája lehetővé teszi a VBScript futtatását**   
  Ezzel a házirend-beállítással felügyelheti, hogy a VBScript futtatható-e az Internet Explorerben megadott zónán lévő lapokon. Ha a legördülő listában az Engedélyezés lehetőséget választotta, a VBScript felhasználói beavatkozás nélkül futtatható. Ha a legördülő listában a kérdés lehetőséget választotta, a felhasználóknak meg kell választaniuk, hogy engedélyezik-e a VBScript futtatását. Ha a legördülő listában a Letiltás lehetőséget választotta, a VBScript nem fut. Ha nem konfigurálja vagy letiltja ezt a házirend-beállítást, a VBScript megakadályozza a futtatását.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer internetes zónája különböző tartományokból származó tartalmat húzhat át a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Alapértelmezett**: letiltva 
  
- **Az Internet Explorer intranetes zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Alapértelmezett**: letiltás 
  
- **Internet Explorer-Letöltés – készülékházak**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó betöltse a hírcsatornáról a felhasználó számítógépére. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem állíthatja be a hírcsatorna-szinkronizálási motort úgy, hogy a csatorna tulajdonságlapján keresztül letöltse a bekerítést. A fejlesztők nem változtathatják meg a letöltési beállítást a hírcsatorna API-kon keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a hírcsatorna-szinkronizálási motor letöltse a bekerítést a hírcsatorna tulajdonságlapján. A fejlesztő a hírcsatorna API-jai segítségével módosíthatja a letöltési beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer korlátozott zónájának aláíratlan aktív X vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer internetes zónája a különböző tartományokból származó tartalmakat a Windowson belül húzza**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Alapértelmezett**: letiltva  
  
- Az **Internet Explorer folyamatai korlátozzák az aktív X telepítési**   
  Ezzel a házirend-beállítással engedélyezheti, hogy a webböngésző vezérlőt futtató alkalmazások blokkolják az ActiveX-vezérlő telepítésének automatikus megadását. Ha engedélyezi ezt a házirend-beállítást, a webböngésző vezérlő letiltja az ActiveX-vezérlő telepítésének automatikus megadását minden folyamat esetében. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a webböngésző vezérlő nem blokkolja az ActiveX-vezérlő telepítésének automatikus megadását az összes folyamat esetében.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Internet Explorer Internet Zone Szkriptletek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó futtathat-e Szkriptletek. Ha engedélyezi ezt a házirend-beállítást, akkor a felhasználó futtathat Szkriptletek. Ha letiltja ezt a házirend-beállítást, a felhasználó nem tudja futtatni a Szkriptletek. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer – korlátozott zóna – fájlok húzása vagy másolása és beillesztése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók beilleszthetnek-e fájlokat, vagy másolhatnak és beilleszthetnek fájlokat a zónán belüli forrásokból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók áthelyezhetik a fájlokat, vagy automatikusan másolhatják és beilleszthetik a fájlokat a zónából. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat áthúzni vagy másolni. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak fájlokat húzni, vagy fájlokat másolni és beilleszteni a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat húzni vagy másolni.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Alapértelmezett**: letiltás  
  
- **Internet Explorer szoftver, ha az aláírás érvénytelen**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó telepíthet-e vagy futtathat-e szoftvert, például az ActiveX-vezérlőket és a fájlokat, még akkor is, ha az aláírás érvénytelen. Egy érvénytelen aláírás azt jelezheti, hogy valaki módosította a fájlt. Ha engedélyezi ezt a házirend-beállítást, a rendszer a felhasználókat az érvénytelen aláírással rendelkező fájlok telepítésére és futtatására kéri. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak és nem telepíthetnek érvénytelen aláírással rendelkező fájlokat. Ha nem konfigurálja ezt a házirendet, a felhasználók dönthetnek úgy, hogy érvénytelen aláírással futtatják vagy telepítik a fájlokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer korlátozott zónájának másolása és beillesztése parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájlok végezhetnek-e vágólap-műveletet (például Kivágás, másolás és beillesztés) egy adott régióban. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a vágólapon végez-e műveleteket. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer korlátozott zónája különböző tartományokból származó tartalmat húzhat át a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Alapértelmezett**: letiltva  
  
- **Internet Explorer-felhasználók helyek hozzáadása**  
  Megakadályozza, hogy a felhasználók a biztonsági zónákból származó helyeket adjanak hozzá vagy távolítanak el. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, a biztonsági zónák hely-felügyeleti beállításai le vannak tiltva. (A biztonsági zónák hely-felügyeleti beállításainak megtekintéséhez az Internetbeállítások párbeszédpanelen kattintson a Biztonság fülre, majd kattintson a helyek gombra.) Ha letiltja vagy nem konfigurálja ezt a házirendet, a felhasználók hozzáadhatnak webhelyeket a megbízható helyek és a Tiltott helyek zónából, és módosíthatják a helyi intranet zóna beállításait. Ez a szabályzat megakadályozza, hogy a felhasználók módosítsák a rendszergazda által létesített biztonsági zónák hely-felügyeleti beállításait. Megjegyzés: a "biztonsági oldal letiltása" házirend (a User konfigurációja \ felügyeleti sablonok \ Internet Explorer\Internet vezérlőpultján található), amely eltávolítja a biztonsági lapot a felületről, elsőbbséget élvez a szabályzattal szemben. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Továbbá tekintse meg a "biztonsági zónák: csak számítógép-beállítások használata" házirendet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Alapértelmezett**: letiltva  
  
- **Internet Explorer Internet zóna parancsfájl kezdeményezett Windows**  
  Ezzel a házirend-beállítással felügyelheti a parancsfájl által kezdeményezett előugró ablakokat és windowsokat, amelyek tartalmazzák a címet és az állapotjelző sávokat. Ha engedélyezi ezt a házirend-beállítást, a Windows-korlátozások biztonsága nem lesz érvényes ebben a zónában. A biztonsági zóna a szolgáltatás által biztosított hozzáadott biztonsági réteg nélkül fut. Ha letiltja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer biztonsági zónái csak a gép beállításait használják**  
  A biztonsági zóna információit alkalmazza ugyanazon számítógép minden felhasználója számára. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, a felhasználó által a biztonsági zónában végrehajtott módosítások a számítógép összes felhasználójára érvényesek lesznek. Ha letiltja vagy nem konfigurálja ezt a házirendet, akkor az azonos számítógép felhasználói a saját biztonsági zónákra vonatkozó beállításokat hozhatnak létre. Ezzel a házirenddel biztosíthatja, hogy a biztonsági zónák beállításai egységesen legyenek alkalmazva ugyanarra a számítógépre, és ne változzon a felhasználótól. Továbbá tekintse meg a "biztonsági zónák: ne engedélyezze a felhasználók számára szabályzatok módosítását" házirendet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer zárolta a helyi számítógép zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Alapértelmezett**: a Java letiltása 
  
- Az **Internet Explorer korlátozott zónája nem futtat antimalware-t az aktív X vezérlőkön**   
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer korlátozott zónájának futtatása a .NET-keretrendszerre vonatkozó, Authenticode-val aláírt összetevőkkel**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-val aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláírt felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy végrehajtja-e az aláírt felügyelt összetevőket. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer korlátozott zónáinak hozzáférése az adatforrásokhoz**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer hozzáférhet-e egy másik biztonsági zónából származó adatokhoz a Microsoft XML Parser (MSXML) vagy a ActiveX Data Objects (ADO) használatával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók betölthetnek egy olyan lapot a zónába, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a lap betöltését az MSXML vagy az ADO protokollt használó zónában a zóna egy másik helyéről származó adatok eléréséhez. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Alapértelmezett**: letiltás 
  
- **Az Internet Explorer internetes zónája nem futtat antimalware-t az ActiveX-vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Alapértelmezett**: letiltva  
  
- **Internet Explorer Internet zóna másolás és beillesztés parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájlok végezhetnek-e vágólap-műveletet (például Kivágás, másolás és beillesztés) egy adott régióban. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a vágólapon végez-e műveleteket. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer az aktív X telepítő szolgáltatást használja**  
  Ezzel a házirend-beállítással megadhatja, hogy az ActiveX-vezérlők hogyan legyenek telepítve. Ha engedélyezi ezt a házirend-beállítást, a rendszer csak akkor telepíti az ActiveX-vezérlőket, ha az ActiveX-telepítő szolgáltatás megtalálható, és úgy van konfigurálva, hogy engedélyezze az ActiveX-vezérlők telepítését. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a normál telepítési folyamaton keresztül telepíti az ActiveX-vezérlőket, beleértve a felhasználónkénti vezérlőket is.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer feldolgozza a védelmet a zónák megemelésével**  
  Az Internet Explorer a megnyíló weblapokon korlátozásokat helyez el. A korlátozások a weblap (Internet, intranet, helyi számítógép zóna stb.) helyétől függenek. Például a helyi számítógépen lévő weblapok a legkevesebb biztonsági korlátozással rendelkeznek, és a helyi számítógép zónában találhatók, így a helyi számítógép biztonsági zónája elsődleges cél a rosszindulatú felhasználók számára. Ha engedélyezi ezt a házirend-beállítást, az összes zóna megemelhető minden folyamat esetében. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer vagy a folyamat listában felsorolt folyamatok nem kapnak ilyen védelmet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Internet Explorer Internet Zone aláíratlan ActiveX-vezérlők letöltése**   
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer internetes zónája különböző tartományokban navigáljon a Windows és a keretek között**   
  Ezzel a házirend-beállítással kezelheti a Windows és a keretek megnyitását, valamint az alkalmazások különböző tartományokon belüli elérését. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megnyithatják a Windowst és a képkockákat más tartományokból, és más tartományokból származó alkalmazásokat is elérhet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a Windows és a keretek számára más tartományokból származó alkalmazások elérését. Ha letiltja ezt a házirend-beállítást, a felhasználók nem megnyithatják a Windowst és a képkockákat a különböző tartományokból származó alkalmazások eléréséhez. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók megnyithatja a Windowst és a képkockákat más tartományokból, és más tartományokból is elérheti az alkalmazásokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Alapértelmezett**: letiltás  

- **Internet Explorer Internet zóna frissítései az állapotsoron parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy parancsfájl frissítheti-e a zónán belüli állapotjelző sávot. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok frissíthetik az állapotjelző sávot. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a parancsfájl nem jogosult az állapotsor frissítésére.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Alapértelmezett**: letiltva  
 
- **Az Internet Explorer korlátozott zónája helyi elérési utat tartalmaz a fájlok kiszolgálóra való feltöltésekor**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer mikor küldje el a helyi elérési utat, amikor a felhasználó HTML-űrlapon keresztül tölt fel fájlokat. Ha a rendszer elküldje a helyi elérési utat, előfordulhat, hogy a kiszolgáló véletlenül nem tárt fel adatokat. Előfordulhat például, hogy a felhasználó asztaláról eljuttatott fájlok tartalmazzák a felhasználónevet az elérési út részeként. Ha engedélyezi ezt a házirend-beállítást, a rendszer az elérési út adatait akkor továbbítja, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha letiltja ezt a házirend-beállítást, a rendszer eltávolítja az elérésiút-információkat, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a rendszer elküldje-e az elérési utat, amikor HTML-űrlapon keresztül tölt fel fájlokat. Alapértelmezés szerint a rendszer az elérésiút-információkat elküldi.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Alapértelmezett**: letiltva  
  
- Az **Internet Explorer folyamatai korlátozzák a fájlok letöltését**   
  Ezzel a házirend-beállítással a webböngésző vezérlőt futtató alkalmazások letilthatják a felhasználók által kezdeményezett fájlok letöltésének automatikus megadását. Ha engedélyezi ezt a házirend-beállítást, a webböngésző vezérlő letiltja azon fájlok letöltésének automatikus megadását, amelyek nem minden folyamat esetében kezdeményezték a felhasználót. Ha letiltja ezt a házirend-beállítást, a webböngésző vezérlő nem fogja blokkolni az olyan fájlok letöltésének automatikus megadását, amelyek nem minden folyamat esetében kezdeményezték a felhasználót.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer korlátozott zónája csak jóváhagyott tartományokat engedélyez az aktív X vezérlők használatához**   
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer a felhasználótól az ActiveX-vezérlőt telepítő webhelytől eltérő webhelyeken is fusson. Ha engedélyezi ezt a házirend-beállítást, a rendszer arra kéri a felhasználót, hogy az ActiveX-vezérlők futtathatók legyenek a zónában található webhelyekről. A felhasználó dönthet úgy, hogy engedélyezi, hogy a vezérlő az aktuális helyről vagy az összes helyről fusson. Ha letiltja ezt a házirend-beállítást, a felhasználó nem látja a helyhez tartozó ActiveX-parancssort, és az ActiveX-vezérlők a zóna összes webhelyéről futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer korlátozott zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Alapértelmezett**: letiltás  
  
- **Az Internet Explorer felhasználói házirendeket módosítanak**  
  Megakadályozza, hogy a felhasználók módosíthassák a biztonsági zónák beállításait. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, az Internetbeállítások párbeszédpanel Biztonság lapján az egyéni szint gomb és a biztonsági szint csúszkája le van tiltva. Ha letiltja vagy nem konfigurálja ezt a házirendet, a felhasználók módosíthatják a biztonsági zónák beállításait. Ez a szabályzat megakadályozza, hogy a felhasználók módosítsák a rendszergazda által létesített biztonsági zónák beállításait. Megjegyzés: a "biztonsági oldal letiltása" házirend (a User konfigurációja \ felügyeleti sablonok \ Internet Explorer\Internet vezérlőpultján található), amely eltávolítja az Internet Explorer biztonsági lapját a Vezérlőpulton, elsőbbséget élvez ezt a szabályzatot. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Továbbá tekintse meg a "biztonsági zónák: csak számítógép-beállítások használata" házirendet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Alapértelmezett**: letiltva  
  
- **Internet Explorer korlátozott zóna által védett üzemmód**  
  Ezzel a házirend-beállítással engedélyezheti a védett üzemmódot. A védett mód segít megvédeni az Internet Explorert a kihasznált biztonsági rések révén, ha csökkenti az Internet Explorer által a beállításjegyzékben és a fájlrendszerben írni kívánt helyeket. Ha engedélyezi ezt a házirend-beállítást, a védett mód be van kapcsolva. A felhasználó nem kapcsolhatja ki a védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a védett mód ki van kapcsolva. A felhasználó nem kapcsolhatja be a védett üzemmódot. Ha nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó be-vagy kikapcsolhatja a védett módot.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer Internet Zone felhasználói adatmegőrzés**  
  Ezzel a házirend-beállítással kezelheti az információk megőrzését a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha a felhasználó egy megőrzött lapra tér vissza, akkor a lap állapota visszaállítható, ha a házirend-beállítás megfelelően van konfigurálva. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megőrzik az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók megőrizheti az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban vagy közvetlenül a lemezre mentett weblapon belül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer internetes zónájának parancsfájlkezelése a webböngésző vezérlőinek használatával**  
 
  Ezzel a házirend-beállítással megadható, hogy egy oldal képes-e a beágyazott WebBrowser vezérlők futtatására parancsfájl használatával. Ha engedélyezi ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés engedélyezett. Ha letiltja ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés nem engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a WebBrowser vezérlőhöz tartozó parancsfájlok elérését. Alapértelmezés szerint a WebBrowser vezérlőhöz való parancsfájl-hozzáférés csak a helyi gépen és az intranet zónában engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer korlátozott zónájának felhasználói adatmegőrzése**  
  Ezzel a házirend-beállítással kezelheti az információk megőrzését a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha a felhasználó egy megőrzött lapra tér vissza, akkor a lap állapota visszaállítható, ha a házirend-beállítás megfelelően van konfigurálva. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megőrzik az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül egy, a lemezre mentett weblapon belül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Alapértelmezett**: letiltva  
  
- **Az Internet Explorer lezárta az intranet zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Alapértelmezett**: a Java letiltása  
  
- **Internet Explorer fokozottan védett üzemmód**  
  A továbbfejlesztett védett mód további védelmet biztosít a rosszindulatú webhelyekkel szemben, ha 64 bites folyamatokat használ a Windows 64-bites verzióiban. A Windows 8 rendszerű számítógépek esetében a fokozottan védett mód is korlátozza az Internet Explorer által a beállításjegyzékből és a fájlrendszerből beolvasott helyeket. Ha engedélyezi ezt a házirend-beállítást, a fokozottan védett mód be van kapcsolva. Minden olyan zóna, amelynél engedélyezve van a védett üzemmód, fokozottan védett módot fog használni. A felhasználók nem tudják letiltani a fokozottan védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a fokozottan védett üzemmód ki van kapcsolva. Minden olyan zóna, amelynél engedélyezve van a védett üzemmód, a Windows Vista Internet Explorer 7-es verziójában bemutatott védett mód verzióját fogja használni. Ha nem konfigurálja ezt a házirendet, a felhasználók az Internetbeállítások párbeszédpanel Speciális lapján bekapcsolhatják vagy kikapcsolhatják a fokozottan védett üzemmódot.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Alapértelmezett**: engedélyezve  
  
- **Az Internet Explorer megkerülésének intelligens képernyő figyelmeztetései**  
  Ezzel a házirend-beállítással adható meg, hogy a felhasználó megkerülhet-e a SmartScreen szűrőből származó figyelmeztetéseket. A SmartScreen szűrő figyelmezteti a felhasználót olyan végrehajtható fájlokra, amelyeket az Internet Explorer felhasználói általában nem töltenek le az internetről. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő figyelmeztetései letiltják a felhasználót. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó megkerülheti a SmartScreen szűrő figyelmeztetéseit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Alapértelmezett**: letiltva  
  
- **Internet Explorer – korlátozott zóna – metaadatok frissítése**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy felhasználó böngészője átirányítható-e egy másik weblapra, ha a weblap szerzője a meta refresh (címke) beállítást használja a böngészők másik weblapra való átirányításához. Ha engedélyezi ezt a házirend-beállítást, egy olyan felhasználó böngészőjében, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, átirányítható egy másik weblapra. Ha letiltja ezt a házirend-beállítást, egy olyan felhasználó böngészője, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, nem lehet átirányítani egy másik weblapra. Ha nem konfigurálja ezt a házirend-beállítást, egy olyan felhasználó böngészője, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, nem irányítható át egy másik weblapra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Alapértelmezett**: letiltva  
  
## <a name="local-policies-security-options"></a>Helyi házirendek biztonsági beállításai
További információ: [Policy CSP-LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) a Windows dokumentációjában. 

- **Nevesített csövek és megosztások névtelen elérésének korlátozása**  
  Ha engedélyezve van, ez a biztonsági beállítás korlátozza a megosztásokhoz és csövekhez való névtelen hozzáférést a következő beállításokhoz: (1) Nevesített csövek, amelyekhez névtelenül hozzáférő (2) megosztások érhetők el.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Alapértelmezett**: igen  
  
- **Minimális munkamenet-biztonság az NTLM SSP-alapú kiszolgálók esetében**  
  Ez a biztonsági beállítás lehetővé teszi a kiszolgáló számára, hogy megkövetelje a 128 bites titkosítás és/vagy az NTLMv2 munkamenet-biztonság egyeztetését. Ezek az értékek a LAN Manager hitelesítési szintjének biztonsági beállításának értékétől függenek. A lehetőségek a következők: NTLMv2-munkamenet biztonságának megkövetelése: a kapcsolat sikertelen lesz, ha az üzenet integritása nincs egyeztetve. 128 bites titkosítás megkövetelése. Ha az erős titkosítás (128 bites) nincs egyeztetve, a rendszer nem fogja tudni a kapcsolatokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Alapértelmezett**: NTLM V2 és 128 bites titkosítás szükséges  
  
- **A zárolási képernyő inaktivitásának percben, amíg a képernyőkímélő be nem kapcsol**  
  A Windows észleli a bejelentkezési munkamenetek tétlenségét, és ha a tétlenség ideje túllépi a tétlenségi korlátot, a rendszer futtatja a képernyőkímélőt és lezárja a munkamenetet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Alapértelmezett**: 15
  
- **Az ügyfél minden esetben digitálisan aláírja a kommunikációt** Ez a biztonsági beállítás határozza meg, hogy a tartományi tag által kezdeményezett összes biztonságos csatorna forgalmát alá kell-e írni vagy titkosítani kell-e. Ha egy számítógép tartományhoz csatlakozik, létrejön egy számítógépfiók. Ezt követően a rendszer indításakor a számítógépfiók jelszava használatával hozzon létre egy biztonságos csatornát a tartományához tartozó tartományvezérlővel. Ez a biztonságos csatorna olyan műveletek elvégzésére szolgál, mint például az NTLM-továbbítás hitelesítés, az LSA SID/Name lookup és még sok más. Ez a beállítás határozza meg, hogy a tartomány tagja által kezdeményezett összes biztonságos csatorna-forgalom megfelel-e a minimális biztonsági követelményeknek. Pontosabban meghatározza, hogy a tartományi tag által elindított összes biztonságos csatorna forgalmát alá kell-e írni vagy titkosítani kell-e. Ha ez a szabályzat engedélyezve van, akkor a biztonságos csatorna nem lesz létrehozva, kivéve, ha az összes biztonságos csatorna-forgalom aláírásával vagy titkosításával egyeztetve van. Ha ez a szabályzat le van tiltva, akkor a rendszer az összes biztonságos csatorna forgalom titkosítását és aláírását egyezteti a tartományvezérlővel, amely esetben az aláírás és a titkosítás szintje a tartományvezérlő verziójától és a következő két beállítástól függ. házirendek: tartomány tagja: a biztonságos csatorna adatai digitális titkosítása (ha lehetséges) tartományi tag: a biztonságos csatorna adatai digitális aláírása (ha lehetséges).  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Alapértelmezett**: igen
  
- **Hitelesítési szint**  
  Ez a biztonsági beállítás határozza meg, hogy melyik kérdés-válasz hitelesítési protokollt használja a rendszer a hálózati bejelentkezésekhez. Ez a választás hatással van az ügyfelek által használt hitelesítési protokoll szintjére, a munkamenet-biztonság megtárgyalásának szintjére, valamint a kiszolgálók által a következőképpen elfogadott hitelesítés szintjére:  
  - *LM-és NTLM-válaszok küldése* – az ügyfelek az LM és az NTLM hitelesítést használják, és soha nem használják az NTLMv2 munkamenet-biztonságot; a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *LM és NTLM-NTLMv2 küldése, ha egyeztetve* van – az ügyfelek az LM és az NTLM hitelesítést használják, és ha a kiszolgáló támogatja az NTLMv2-munkamenetek biztonságát, a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLM-válasz küldése* – az ügyfelek csak az NTLM-hitelesítést használják, és ha a kiszolgáló támogatja azt, akkor az NTLMv2-munkamenetek biztonságát használják. a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLMv2-válaszok küldése* – az ügyfelek csak az NTLMv2-hitelesítést használják, és ha a kiszolgáló támogatja, az NTLMv2-munkamenetek biztonságát használják. a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLMv2-válasz küldése. LM-azonosítók elutasítása* – az ügyfelek csak az NTLMv2-hitelesítést használják, és ha a kiszolgáló támogatja, akkor az NTLMv2-munkamenetek biztonsága a tartományvezérlők elutasították az LM-t (csak NTLM és NTLMv2 hitelesítést fogadnak el). 
  - *Csak NTLMv2-válasz küldése. Az LM és az NTLM megtagadása* – az ügyfelek csak az NTLMv2-hitelesítést használják, és ha a kiszolgáló támogatja, az NTLMv2-munkamenetek biztonságát használják. a tartományvezérlők megtagadják az LM és az NTLM használatát (csak az NTLMv2-hitelesítést fogadják el).  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Alapértelmezett**: csak NTLMv2-válaszok küldése. Az LM és az NTLM elutasítása
  
- **Titkosítatlan jelszavak küldésének megakadályozása az ügyfelektől harmadik féltől származó SMB-kiszolgálókra**  
  Ha ez a biztonsági beállítás engedélyezve van, a kiszolgálói üzenetblokk (SMB) átirányító képes szöveges jelszavakat küldeni a nem Microsoft SMB-kiszolgálókra, amelyek nem támogatják a jelszó-titkosítást a hitelesítés során. A Titkosítatlan jelszavak küldése biztonsági kockázat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Alapértelmezett**: igen
  
- **A kiszolgáló digitális aláírásával való kommunikáció megkövetelése mindig**  
  Ez a biztonsági beállítás határozza meg, hogy az SMB-ügyfél megkísérelje-e az SMB-csomagok aláírásának egyeztetését. A Server Message Block (SMB) protokoll a Microsoft fájl-és nyomtatómegosztás, valamint számos egyéb hálózati művelet, például a távoli Windows-felügyelet alapját képezi. Ha meg szeretné akadályozni, hogy az SMB-csomagokat az átvitel során módosító, nem a közepes támadásokkal szemben, az SMB protokoll támogatja az SMB-csomagok digitális aláírását. Ezzel a házirend-beállítással megadható, hogy az SMB-ügyfél-összetevő megkísérelje-e az SMB-csomagok aláírását az SMB-kiszolgálóhoz való csatlakozáskor. Ha ez a beállítás engedélyezve van, a Microsoft hálózati ügyfél arra kéri a kiszolgálót, hogy az SMB-csomagok aláírását végrehajtsa a munkamenet beállításakor. Ha a csomagaláírás engedélyezve van a kiszolgálón, a csomagaláírás egyeztetése megkezdődik. Ha a szabályzat le van tiltva, az SMB-ügyfél soha nem fogja egyeztetni az SMB-csomagok aláírását.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Alapértelmezett**: igen
  
- **Rendszergazdai jogosultságszint-emelési kérések viselkedése**  
  Ezzel a házirend-beállítással szabályozható a rendszergazdák jogosultságszint-emelési kérésének viselkedése. A választható beállítások: 
  - *Jogosultságszint-emelés kérés nélkül* – lehetővé teszi az emelt szintű fiókok számára a jogosultságszint-emelést a beleegyezés vagy a hitelesítő adatok megkövetelése nélkül. Megjegyzés: ezt a beállítást csak a legszigorúbban korlátozott környezetekben használhatja. 
  - *Hitelesítő adatok kérése a biztonságos asztalon* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer felszólítja a felhasználót a biztonságos asztalra, hogy adjon meg egy kiemelt felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ír be, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  - *Beleegyezés kérése a biztonságos asztalon* – ha egy művelethez jogosultságszint-emelésre van szükség, a felhasználónak meg kell adnia a biztonságos asztalt az engedélyezés vagy a Megtagadás lehetőség kiválasztásához. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  - *Hitelesítő adatok kérése* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer kéri a felhasználótól, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Beleegyezés kérése* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer a felhasználónak engedélyt vagy megtagadást kell választania. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik.  
  - A *nem Windows rendszerű bináris fájlok jóváhagyásának kérése* – ha egy nem Microsoft-alkalmazásra vonatkozó művelethez jogosultságszint-emelésre van szükség, a felhasználónak meg kell adnia a biztonságos asztalt az engedélyezés vagy a Megtagadás lehetőség kiválasztásához. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Alapértelmezett**: beleegyezés kérése a biztonságos asztalon
  
- **Minimális munkamenet-biztonság az NTLM SSP-alapú ügyfelek számára**  
  Ez a biztonsági beállítás lehetővé teszi az ügyfél számára, hogy megkövetelje a 128 bites titkosítás és/vagy az NTLMv2 munkamenet-biztonság egyeztetését. Ezek az értékek a LAN Manager hitelesítési szintjének biztonsági beállításának értékétől függenek. A választható beállítások:
  - *NTLMv2-munkamenet biztonságának megkövetelése* – a kapcsolat sikertelen lesz, ha az NTLMv2 protokoll nincs egyeztetve. 
  - *128 bites titkosítás megkövetelése* – ha erős titkosítás (128 bites) nincs egyeztetve, a rendszer nem fogja tudni a kapcsolatokat.
  - *NTLMv2 és 128 bites titkosítás megkövetelése*.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Alapértelmezett**: NTLM v2 128 titkosítás szükséges
  
- **Intelligens kártya eltávolításának viselkedése**  
  Ez a biztonsági beállítás határozza meg, hogy mi történjen, ha a bejelentkezett felhasználó intelligens kártyáját eltávolítja az intelligenskártya-olvasóból. A választható beállítások:
  - *Nincs művelet*. 
  - *Munkaállomás zárolása* – a munkaállomás az intelligens kártya eltávolításakor zárolva van, így a felhasználók elhagyhatják a területeket, saját intelligens kártyájuk is megtarthatják őket, és továbbra is fenntartják a védett munkamenetet.
  - *Kijelentkezés kényszerítése* – a rendszer automatikusan kijelentkezik a felhasználót az intelligens kártya eltávolításakor.
  - *Távoli asztal kapcsolat bontása* – az intelligens kártya eltávolítása leválasztja a munkamenetet anélkül, hogy a felhasználót be kellene jelentkeznie. Ez lehetővé teszi a felhasználó számára, hogy beszúrja az intelligens kártyát, és később, vagy egy másik intelligenskártya-olvasóval felszerelt számítógépen folytassa a bejelentkezést anélkül, hogy újra be kellene jelentkeznie. Helyi munkamenet esetén ez a szabályzat pontosan úgy működik, mint a Munkaállomás zárolása.
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Alapértelmezett**: munkaállomás zárolása
  
- **SAM-fiókok és-megosztások névtelen enumerálásának letiltása**  
  Ez a biztonsági beállítás határozza meg, hogy engedélyezi-e a SAM-fiókok és-megosztások névtelen enumerálását. A Windows lehetővé teszi a névtelen felhasználók számára bizonyos tevékenységek végrehajtását, például a tartományi fiókok és hálózati megosztások nevének számbavételét. Ez akkor lehet hasznos, ha egy rendszergazda olyan megbízható tartományban kíván hozzáférést biztosítani a felhasználóknak, amely nem tart fenn kölcsönös bizalmi kapcsolatot. Ha nem szeretné engedélyezni a SAM-fiókok és-megosztások névtelen enumerálását, állítsa ezt a házirendet *Igen*értékre.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Alapértelmezett**: igen
  
- **Üres jelszóval rendelkező távoli bejelentkezés letiltása**  
  Ez a biztonsági beállítás határozza meg, hogy a jelszóval védett helyi fiókok a fizikai számítógép konzolján kívül más helyekről is bejelentkezhetnek-e. Ha engedélyezve van, a jelszóval védett helyi fiókoknak a számítógép billentyűzetén kell használniuk a bejelentkezést. 

  *Figyelmeztetés*: a nem fizikailag biztonságos helyen lévő számítógépeknek mindig erős jelszóházirend-szabályzatot kell kikényszeríteni az összes helyi felhasználói fiókhoz. Ellenkező esetben a számítógéphez való fizikai hozzáféréssel rendelkező bárki bejelentkezhet egy olyan felhasználói fiókkal, amely nem rendelkezik jelszóval. Ez különösen fontos a hordozható számítógépekhez. 

  Ha ezt a biztonsági házirendet a Mindenki csoportra alkalmazza, a Távoli asztali szolgáltatások nem tud bejelentkezni. Ez a beállítás nem érinti a tartományi fiókokat használó bejelentkezéseket. Távoli interaktív bejelentkezéseket használó alkalmazások esetén a beállítás megkerülése lehetséges.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Alapértelmezett**: igen
  
- **Normál felhasználói jogosultságszint-emelési kérések viselkedése**  
  Ezzel a házirend-beállítással szabályozható az általános jogú felhasználók jogosultságszint-emelési kérésének viselkedése. 
  - Jogosultságszint-emelési *kérések automatikus megtagadása* – ha egy művelethez emelt szintű jogosultságra van szükség, egy konfigurálható hozzáférés-megtagadási hibaüzenet jelenik meg. Az asztali gépeket futtató vállalatok az általános jogú felhasználók ezt a beállítást választva csökkenthetik az ügyfélszolgálati hívásokat. 
  - *Hitelesítő adatok kérése a biztonságos asztalon* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a felhasználónak a biztonságos asztalon kell megadnia egy másik felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Hitelesítő adatok kérése* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer kéri a felhasználótól, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Alapértelmezett**: jogosultságszint-emelési kérések automatikus megtagadása
  
- **Rendszergazdai engedélyezési mód szükséges a rendszergazdák számára**  
  Ezzel a házirend-beállítással szabályozható a számítógépen a felhasználói fiókok felügyelete (UAC) összes házirend-beállításának viselkedése. Ha módosítja ezt a házirend-beállítást, újra kell indítania a számítógépet. A választható beállítások:   
  - *Nincs konfigurálva* – a rendszergazdai engedélyezési mód és az összes kapcsolódó UAC-házirend-beállítás le van tiltva. Megjegyzés: Ha ez a házirend-beállítás le van tiltva, a Security Center értesíti arról, hogy az operációs rendszer általános biztonsága csökkent. 
  - *Igen* – a rendszergazdai jóváhagyási mód engedélyezve van. Ezt a házirendet engedélyezni kell, és a kapcsolódó UAC-házirend beállításait megfelelően be kell állítani ahhoz, hogy a beépített rendszergazdai fiók és az összes többi olyan felhasználó, aki tagja a rendszergazdák csoportnak, rendszergazdai engedélyezéses módban fusson.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Alapértelmezett**: igen
  
- **SAM-fiókok névtelen számbavételének megakadályozása**  
  Ez a biztonsági beállítás határozza meg, hogy a rendszer milyen további engedélyeket kap a névtelen kapcsolatok számára a számítógéphez. A Windows lehetővé teszi a névtelen felhasználók számára bizonyos tevékenységek végrehajtását, például a tartományi fiókok és hálózati megosztások nevének számbavételét. Ez akkor lehet hasznos, ha egy rendszergazda olyan megbízható tartományban kíván hozzáférést biztosítani a felhasználóknak, amely nem tart fenn kölcsönös bizalmi kapcsolatot. Ez a biztonsági beállítás lehetővé teszi, hogy további korlátozások kerüljenek a névtelen kapcsolatokra a következőképpen: 
  - *Igen* – nem engedélyezi a SAM-fiókok enumerálását. Ez a beállítás a hitelesített felhasználókkal rendelkező mindenkit lecseréli az erőforrásokra vonatkozó biztonsági engedélyekben.
  - *Nincs konfigurálva* – nincs további korlátozás. Használja az alapértelmezett engedélyeket.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Alapértelmezett**: igen
  
- **Távoli hívások engedélyezése a biztonsági fiókok kezelőjének**  
  Ezzel a házirend-beállítással korlátozhatja a távoli RPC-kapcsolatokat a SAM-ra. Ha nincs bejelölve, a rendszer az alapértelmezett biztonsági leírót használja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Alapértelmezett**: *O:Bag: rossz: (A;; RC;;; BA)*

- **Rendszergazdai jóváhagyási mód használata**  
  Ezzel a házirend-beállítással szabályozható a rendszergazdai engedélyezési mód működése a beépített rendszergazda fiókhoz. A választható beállítások: 
  - *Igen* – a beépített rendszergazdai fiók rendszergazdai jóváhagyási módot használ. Alapértelmezés szerint a jogosultságszint-emelést igénylő műveletek megkérik a felhasználót, hogy hagyja jóvá a műveletet. 
  - *Nincs konfigurálva* – a beépített rendszergazdai fiók minden olyan alkalmazást futtat, amely teljes körű rendszergazdai jogosultságokkal rendelkezik. 

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Alapértelmezett**: igen
  
- **Felhasználói felületi hozzáférési alkalmazások engedélyezése biztonságos helyszíneken**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználói felület kisegítő lehetőségei (UIAccess vagy UIA) automatikusan le tudják-e tiltani a biztonságos asztalt az általános jogú felhasználók általi jogosultságszint-emelési kérésekhez. 
  - *Igen* – a UIA programok, például a Windows Távsegítség, automatikusan letiltják a jogosultságszint-emelési kérések biztonságos asztalát. Ha nem tiltja le a "felhasználói fiókok felügyelete: váltás a biztonságos asztalra a jogosultságszint-emelési kéréskor" házirend-beállítást, a kérések az interaktív felhasználó asztalán jelennek meg a biztonságos asztal helyett. 
  - *Nincs konfigurálva*: – a biztonságos asztalt csak az interaktív asztal felhasználója tilthatja le, vagy letilthatja a "felhasználói fiókok felügyelete: váltás a biztonságos asztalra a jogosultságszint-emelési kéréskor" házirend-beállítás letiltásával.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Alapértelmezett**: igen

- **Alkalmazások telepítésének észlelése és Jogosultságszint-emelés kérése**  
  Ezzel a házirend-beállítással szabályozható a számítógép alkalmazás-telepítési észlelésének viselkedése. A választható beállítások: 
  - *Engedélyezve* – ha olyan alkalmazás-telepítési csomagot észlel, amely jogosultságszint-emelést igényel, a rendszer megkéri a felhasználót, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Letiltott* – az alkalmazás telepítési csomagjai nem észlelhetők, és a rendszer kéri a jogosultságszint-emelést. Az általános jogú felhasználói asztalokat futtató és a delegált telepítési technológiákat (például Csoportházirend-alapú szoftvertelepítés vagy System Management Server (SMS)) használó vállalatoknak le kell tiltaniuk ezt a házirend-beállítást. Ebben az esetben a telepítő észlelése szükségtelen.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Alapértelmezett**: igen
  
- **A LAN Manager kivonatoló értékének a következő jelszó módosításakor való tárolásának megakadályozása**  
  Ez a biztonsági beállítás határozza meg, hogy a következő jelszó megváltozásakor az új jelszóhoz tartozó LAN Manager (LM) kivonatoló értéket tárolja-e a rendszer. Az LM-kivonat viszonylag gyenge és hajlamos a támadásokra, mint a kriptográfiailag erősebb Windows NT-kivonathoz képest. Mivel az LM-kivonat a biztonsági adatbázisban a helyi számítógépen van tárolva, a rendszer a jelszavakat a biztonsági adatbázis megtámadása esetén is veszélyeztetheti.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Alapértelmezett**: igen

- **A fájl-és beállításjegyzék-írási hibák virtualizálása felhasználónkénti helyen**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer az alkalmazások írási hibáit átirányítsa-e a megadott beállításjegyzék-és fájlrendszerbeli helyeire Ezzel a házirend-beállítással csökkenthetők a rendszergazdaként futtatott alkalmazások és a futásidejű alkalmazásadatok írása a következőre: *% ProgramFiles%* , *% windir%* , *%windir%\System32*vagy *HKLM\Software*.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Alapértelmezett**: igen

## <a name="ms-security-guide"></a>MS biztonsági útmutató  
További információ: [Policy CSP-MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) a Windows dokumentációjában.  

- **UAC-korlátozások alkalmazása helyi fiókokra hálózati bejelentkezéskor**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Alapértelmezett**: engedélyezve
  
- **SMB v1 – ügyfél-illesztőprogram indítási konfigurációja**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Alapértelmezett**: letiltott illesztőprogram
  
- **SMB v1-kiszolgáló**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Alapértelmezett**: letiltva
  
- **Kivonatoló hitelesítés**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Alapértelmezett**: letiltva
  
- **Strukturált kivétel kezelésére vonatkozó felülírási védelem**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Alapértelmezett**: engedélyezve
  
## <a name="mss-legacy"></a>MSS örökölt  
További információ: [Policy CSP-MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) a Windows dokumentációjában.  

- **Hálózati IP-forrás útválasztási védelmi szintje**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Alapértelmezett**: legmagasabb szintű védelem  
  
- **A hálózat figyelmen kívül hagyja a NetBIOS-névfeloldási kérelmeket a WINS-kiszolgálók kivételével**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Alapértelmezett**: engedélyezve
  
- **Hálózati IPv6-forrás útválasztási védelmi szintje**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Alapértelmezett**: legmagasabb szintű védelem

- **Hálózati ICMP-átirányítás felülbírálja az OSPF által generált**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Alapértelmezett**: letiltva
  
## <a name="power"></a>Power  
További információ: [házirend CSP-Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) a Windows dokumentációjában.  

- **Jelszó megkövetelése ébresztéskor a csatlakoztatáskor**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználótól a jelszót, amikor a rendszer visszatér az alvó állapotból. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a felhasználónak jelszót kér, amikor az alvó állapotból folytatódik. Ha letiltja ezt a házirend-beállítást, a felhasználó nem kér jelszót, amikor a rendszer visszatér az alvó állapotból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Alapértelmezett**: engedélyezve
  
- **Készenléti állapot, ha akkumulátorról alszik**  
  Ez a házirend-beállítás azt szabályozza, hogy a Windows használhat-e készenléti állapotokat a számítógép alvó állapotba helyezésekor. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a Windows készenléti állapotot használ a számítógép alvó állapotba helyezéséhez. Ha letiltja ezt a házirend-beállítást, a készenléti állapotok (S1-S3) nem engedélyezettek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Alapértelmezett**: letiltva
  
- **Készenléti állapotok a csatlakoztatáskor**  
  Ez a házirend-beállítás azt szabályozza, hogy a Windows használhat-e készenléti állapotokat a számítógép alvó állapotba helyezésekor. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a Windows készenléti állapotot használ a számítógép alvó állapotba helyezéséhez. Ha letiltja ezt a házirend-beállítást, a készenléti állapotok (S1-S3) nem engedélyezettek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Alapértelmezett**: letiltva
  
- **Jelszó megkövetelése ébresztéskor az akkumulátoron**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználótól a jelszót, amikor a rendszer visszatér az alvó állapotból. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a felhasználónak jelszót kér, amikor az alvó állapotból folytatódik. Ha letiltja ezt a házirend-beállítást, a felhasználó nem kér jelszót, amikor a rendszer visszatér az alvó állapotból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Alapértelmezett**: engedélyezve
::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="remote-assistance"></a>Távsegítség   
További információ: [Policy CSP-RemoteAssistance](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteassistance#remoteassistance-solicitedremoteassistance) a Windows dokumentációjában.  

- **Távsegítség kérése**  
  Ezzel a házirend-beállítással engedélyezheti vagy kikapcsolhatja a Távsegítség kérését a számítógépen. 
  - *Ha engedélyezi ezt a házirend-beállítást*, akkor a számítógépen lévő felhasználók e-mailben vagy fájlátvitel használatával kérhetnek segítséget. Emellett a felhasználók csevegési programokat is használhatnak a számítógéphez való csatlakozás engedélyezéséhez, és további Távsegítség-beállításokat is konfigurálhat. 
  - *Ha letiltja ezt a házirend-beállítást*, a számítógépen lévő felhasználók nem használhatnak e-mailt vagy fájlátvitelt, hogy kérjen segítséget. Emellett a felhasználók nem használhatják az azonnali üzenetküldési programokat, hogy engedélyezzék a kapcsolódást a számítógéphez. 
  - *Ha nem konfigurálja ezt a házirend-beállítást*, a felhasználók bekapcsolhatják vagy kikapcsolhatják a (z) Távsegítség szolgáltatást a Vezérlőpult Rendszer tulajdonságai párbeszédpanelén. A felhasználók a Távsegítség beállításait is megadhatják. 

  Ha engedélyezi ezt a házirend-beállítást, kétféleképpen engedélyezheti a segítőket a Távsegítség biztosításához: "a segítők csak a számítógépet tekinthetik meg" vagy "a segítők távolról vezérelhetik a számítógépet". A "maximális jegy ideje" házirend-beállítás azt a korlátot állítja be, ameddig a Távsegítség e-mailben vagy fájlátvitel útján létrehozott meghívása nyitva maradhat. Az "e-mail-meghívások küldésére szolgáló módszer kiválasztása" beállítás megadja, hogy melyik e-mail-szabványt kell használni a Távsegítség meghívásához. Az e-mail-programtól függően használhatja a mailto standard (a meghívót egy internetes kapcsolaton keresztül) vagy a SMAPI (egyszerű MAPI) szabványt (a meghívót az e-mail-üzenethez csatolva). Ez a házirend-beállítás nem érhető el a Windows Vista rendszerben, mert a SMAPI az egyetlen támogatott módszer. Ha engedélyezi ezt a házirend-beállítást, akkor a megfelelő tűzfal-kivételeket is engedélyeznie kell a Távsegítség kommunikációjának engedélyezéséhez.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Alapértelmezett**: Távsegítség letiltása

  Ha a *Távsegítség engedélyezésére*van beállítva, konfigurálja a következő további beállításokat:  
  - **Távsegítség által kért engedély**  
    **Alapértelmezett**: nézet  

  - **Jegy maximális élettartama**  
    **Alapértelmezett**: *nincs konfigurálva*  

  - **Jegyek maximális időtartama**  
    **Alapértelmezett**: perc    

  - **E-Mail Meghívási módszere**  
    **Alapértelmezett**: egyszerű MAPI
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"
  
## <a name="remote-desktop-services"></a>Távoli asztali szolgáltatások  
További információ: [Policy CSP-RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) a Windows dokumentációjában.  

- **Jelszó mentésének tiltása**  
  Meghatározza, hogy a jelszavak menthetők-e a számítógépen Távoli asztali kapcsolatról. Ha engedélyezi ezt a beállítást, a Távoli asztali kapcsolat letiltotta a jelszó-mentés jelölőnégyzetet, és a felhasználók nem tudják menteni a jelszavakat. Amikor egy felhasználó megnyit egy RDP-fájlt a Távoli asztali kapcsolat használatával, és menti a beállításokat, az RDP-fájlban korábban létezett jelszavak törlődnek. Ha letiltja ezt a beállítást, vagy hagyja meg, hogy nincs konfigurálva, a felhasználó Távoli asztali kapcsolat használatával mentheti a jelszavakat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Alapértelmezett**: engedélyezve
  
- **Biztonságos RPC-kommunikáció**  
  Meghatározza, hogy egy Távoli asztal munkamenet-kiszolgáló biztonságos RPC-kommunikációt igényel-e az összes ügyféllel, vagy engedélyezi a nem biztonságos kommunikációt. Ezzel a beállítással megerősítheti az ügyfelekkel folytatott RPC-kommunikáció biztonságát úgy, hogy csak a hitelesített és titkosított kérelmeket engedélyezi. Ha az állapot engedélyezve értékre van állítva, Távoli asztali szolgáltatások fogadja a biztonságos kéréseket támogató RPC-ügyfelektől érkező kérelmeket, és nem engedélyezi a nem biztonságos kommunikációt a nem megbízható ügyfelekkel. Ha az állapot letiltva értékre van állítva, Távoli asztali szolgáltatások mindig minden RPC-forgalomhoz kér biztonságot. A nem biztonságos kommunikáció azonban olyan RPC-ügyfelek számára engedélyezett, amelyek nem válaszolnak a kérelemre. Ha az állapot nincs konfigurálva értékre van állítva, akkor a nem biztonságos kommunikáció engedélyezett. Megjegyzés: az RPC interfész Távoli asztali szolgáltatások felügyeletére és konfigurálására szolgál.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Alapértelmezett**: engedélyezve
  
- **Meghajtó átirányításának tiltása**  
  Ezzel a házirend-beállítással megadható, hogy meg kell-e akadályozni az ügyfélmeghajtók hozzárendelését egy Távoli asztali szolgáltatások-munkamenetben (meghajtó-átirányítás). Alapértelmezés szerint a távoli asztali munkamenetgazda-kiszolgáló automatikusan leképezi az ügyféloldali meghajtókat a kapcsolaton keresztül. A csatlakoztatott meghajtók a Fájlkezelőben vagy a számítógépen *\<meghajtóbetűjel >* *\<számítógépnév >* formátumban jelennek meg. Ezt a házirend-beállítást használhatja a viselkedés felülbírálásához. Ha engedélyezi ezt a házirend-beállítást, az ügyfélmeghajtók átirányítása Távoli asztali szolgáltatások munkamenetekben nem engedélyezett, és a vágólap-fájlmásolás átirányítása nem engedélyezett a Windows Server 2003, Windows 8 és Windows XP rendszerű számítógépeken. Ha letiltja ezt a házirend-beállítást, a rendszer mindig engedélyezi az ügyfél-meghajtó átirányítását. A vágólap-másolási átirányítás is mindig engedélyezett, ha a vágólap átirányítása engedélyezve van. Ha nem konfigurálja ezt a házirend-beállítást, az ügyfél-meghajtó átirányítása és a vágólap-fájlmásolás átirányítása nincs megadva a Csoportházirend szinten.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Alapértelmezett**: engedélyezve
  
- **Jelszó kérése a csatlakozáskor**  
  Ezzel a házirend-beállítással megadható, hogy a Távoli asztali szolgáltatások mindig kéri-e az ügyfelet a jelszó kérésére a csatlakozáskor. Ezzel a beállítással megadhatja, hogy a felhasználók milyen jelszóval jelentkezzenek be Távoli asztali szolgáltatásokba, még akkor is, ha már megadták a jelszót a Távoli asztali kapcsolat-ügyfélben. Alapértelmezés szerint a Távoli asztali szolgáltatások lehetővé teszi, hogy a felhasználók automatikusan bejelentkeznek a Távoli asztali kapcsolat-ügyfélben lévő jelszó megadásával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók nem tudnak automatikusan bejelentkezni a Távoli asztali szolgáltatásokba, ha a Távoli asztali kapcsolat-ügyfélben megadják a jelszavukat. a rendszer jelszót kér a bejelentkezéshez. Ha letiltja ezt a házirend-beállítást, a felhasználók bármikor bejelentkezhetnek a Távoli asztali szolgáltatások automatikusan, ha megadják a jelszavukat a Távoli asztali kapcsolat ügyfélen. Ha nem konfigurálja ezt a házirend-beállítást, az automatikus bejelentkezés nincs megadva a Csoportházirend szinten.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Alapértelmezett**: engedélyezve
  
- **Távoli asztali szolgáltatások ügyfélkapcsolatának titkosítási szintje**  
  Meghatározza, hogy szükség van-e egy adott titkosítási szint használatára az ügyfélszámítógépek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikáció biztonságossá tételéhez RDP protokoll (RDP) kapcsolatok során. Ez a szabályzat csak akkor érvényes, ha natív RDP-titkosítást használ. Azonban a natív RDP-titkosítás (az SSL-titkosítás helyett) nem ajánlott. Ez a szabályzat nem vonatkozik az SSL-titkosításra. Ha engedélyezi ezt a házirend-beállítást, a távoli kapcsolatok során az ügyfelek és a távoli asztali munkamenetgazda-kiszolgálók közötti összes kommunikációnak az ebben a beállításban megadott titkosítási módszert kell használnia. Alapértelmezés szerint a titkosítási szint magas értékre van állítva. A következő titkosítási módszerek érhetők el:  
  - *Magas* – a magas beállítás a-ügyfélről a kiszolgálóra és a kiszolgálóról az ügyfélre érkező, erős 128 bites titkosítást használó adatok titkosítását végzi. Használja ezt a titkosítási szintet olyan környezetekben, amelyek csak 128 bites ügyfeleket tartalmaznak (például Távoli asztali kapcsolatt futtató ügyfeleket). Azok az ügyfelek, amelyek nem támogatják ezt a titkosítási szintet, nem csatlakozhatnak a távoli asztali munkamenetgazda-kiszolgálókhoz.  
  - *Ügyfél-kompatibilis* – az ügyfél-kompatibilis beállítás titkosítja az ügyfél és a kiszolgáló között továbbított, az ügyfél által támogatott maximális kulcs erősségét. Használja ezt a titkosítási szintet olyan környezetekben, amelyek olyan ügyfeleket tartalmaznak, amelyek nem támogatják a 128 bites titkosítást.  
  - *Alacsony* – az alacsony beállítás a 56 bites titkosítás használatával csak az ügyfélről a kiszolgálóra továbbított adatok titkosítását végzi.  
  
  Ha letiltja vagy nem konfigurálja ezt a beállítást, a távoli kapcsolatokhoz használni kívánt titkosítási szint nem kényszeríthető Csoportházirendon keresztül. A fontos FIPS-megfelelőség a rendszerkriptográfiai szolgáltatáson keresztül konfigurálható. A FIPS szabványnak megfelelő algoritmusok használata titkosításhoz, kivonatoláshoz és aláírási beállításokhoz Csoportházirendban (a számítógép konfigurációja \ Windows beállításai \ helyi házirend \ házirend beállítások menüpontban) A FIPS-kompatibilis beállítás titkosítja és visszafejti az ügyfél és a kiszolgáló között továbbított adatokat a kiszolgálóról az ügyfélre, a Federal Information Processing standard (FIPS) 140 titkosítási algoritmusokkal a Microsoft titkosítási moduljainak használatával. Akkor használja ezt a titkosítási szintet, ha az ügyfelek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikációhoz a legmagasabb szintű titkosítás szükséges.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Alapértelmezett**: magas
  
## <a name="remote-management"></a>Távfelügyelet  
További információ: [Policy CSP-RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) a Windows dokumentációjában.  

- **Futtató hitelesítő adatok tárolásának tiltása**  
  Ügyfél alapszintű hitelesítése.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Alapértelmezett**: engedélyezve
  
- **Alapszintű hitelesítés**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) szolgáltatás fogadja-e az egyszerű hitelesítést egy távoli ügyfélről. Ha engedélyezi ezt a házirend-beállítást, a WinRM szolgáltatás fogadja az egyszerű hitelesítést egy távoli ügyfélről. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM szolgáltatás nem fogadja el az egyszerű hitelesítést egy távoli ügyféltől.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Alapértelmezett**: letiltva
  
- **Ügyfél-kivonatoló hitelesítés letiltása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfele kivonatoló hitelesítést használ-e. Ha engedélyezi ezt a házirend-beállítást, a WinRM-ügyfél nem használ kivonatoló hitelesítést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél kivonatoló hitelesítést használ.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Alapértelmezett**: engedélyezve
  
- **Titkosítatlan forgalom**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) szolgáltatás küld-e és fogad-e titkosítatlan üzeneteket a hálózaton keresztül. Ha engedélyezi ezt a házirend-beállítást, a Rendszerfelügyeleti webszolgáltatások ügyfele titkosítatlan üzeneteket küld és fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél csak a titkosított üzeneteket küldi vagy fogadja a hálózaton keresztül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Alapértelmezett**: letiltva
  
- **Ügyfél titkosítatlan forgalma**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfél küld-e és fogad-e titkosítatlan üzeneteket a hálózaton keresztül. Ha engedélyezi ezt a házirend-beállítást, a Rendszerfelügyeleti webszolgáltatások ügyfele titkosítatlan üzeneteket küld és fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél csak a titkosított üzeneteket küldi vagy fogadja a hálózaton keresztül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Alapértelmezett**: letiltva
  
- **Ügyfél alapszintű hitelesítése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfél alapszintű hitelesítést használ-e. Ha engedélyezi ezt a házirend-beállítást, a WinRM-ügyfél alapszintű hitelesítést használ. Ha a WinRM a HTTP-átvitel használatára van konfigurálva, a Felhasználónév és a jelszó küldése a hálózaton keresztül egyszerű szövegként történik. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél nem használ alapszintű hitelesítést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Alapértelmezett**: letiltva
  
## <a name="remote-procedure-call"></a>Távoli eljárás hívása  
További információ: [Policy CSP-RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) a Windows dokumentációjában.  

- **Nem hitelesített RPC-ügyfél beállításai**  
  Ezzel a házirend-beállítással szabályozható, hogy az RPC-kiszolgáló futtatókörnyezete hogyan kezelje az RPC-kiszolgálókhoz csatlakozó nem hitelesített RPC-ügyfeleket Ezzel a házirend-beállítással az összes RPC-alkalmazás hatással van. Tartományi környezetben ezt a házirend-beállítást körültekintően kell használni, mivel ez a funkció számos funkciót érint, beleértve a csoportházirend feldolgozását is. A házirend-beállítás módosításának visszaállításához manuális beavatkozásra van szükség az egyes érintett gépeken. Ez a házirend-beállítás soha nem alkalmazható tartományvezérlőre. Ha letiltja ezt a házirend-beállítást, az RPC-kiszolgáló futtatókörnyezete a "hitelesített" értéket használja a Windows-ügyfélen, és a "None" értéket a Windows Server azon verzióiban, amelyek támogatják ezt a házirend-beállítást. Ha nem konfigurálja ezt a házirend-beállítást, az továbbra is le lesz tiltva. Az RPC-kiszolgáló futtatókörnyezete úgy viselkedik, mintha engedélyezve volt a Windows-ügyfélhez használt "hitelesített" értékkel, valamint a "nincs" értékkel, amelyet ez a házirend-beállítás támogat. Ha engedélyezi ezt a házirend-beállítást, a rendszer az RPC-kiszolgáló futtatókörnyezetét arra utasítja, hogy korlátozza a gépen futó RPC-kiszolgálókhoz csatlakozó nem hitelesített RPC-ügyfeleket. Az ügyfél akkor tekinthető hitelesített ügyfélnek, ha nevesített csövet használ a kiszolgálóval való kommunikációhoz, vagy ha RPC-biztonságot használ. A nem hitelesített ügyfelek által elérhetővé tett RPC-felületek mentesülnek ettől a korlátozástól attól függően, hogy a házirend-beállítás kiválasztott értéke milyen.  
  - A *none* értékkel az összes RPC-ügyfél csatlakozhat a házirend-beállítást alkalmazó számítógépen futó RPC-kiszolgálókhoz. 
  - A *hitelesítéssel* csak a hitelesített RPC-ügyfelek (a fenti definíció alapján) csatlakozhatnak azon a számítógépen futó RPC-kiszolgálókhoz, amelyen a házirend-beállítás alkalmazva van. A rendszer kivételeket biztosít azokhoz az interfészekhez, amelyek kérték azokat. 
  - A *kivételek nélküli hitelesítés* lehetővé teszi, hogy csak a fenti definíción alapuló hitelesített RPC-ügyfelek csatlakozzanak a házirend-beállítást alkalmazó számítógépen futó RPC-kiszolgálókhoz. A kivételek nem engedélyezettek. Megjegyzés: Ez a házirend-beállítás csak a rendszer újraindítása után lesz alkalmazva.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Alapértelmezett**: hitelesített

## <a name="search"></a>Keresés 
További információ: [házirend-CSP – keresés](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) a Windows dokumentációjában.  

- **Titkosított elemek indexelésének letiltása**  
  Engedélyezi vagy tiltja az elemek indexelését. Ez a kapcsoló a Windows Search indexelő szolgáltatáshoz használható, amely azt szabályozza, hogy a rendszer indexeli-e a titkosított elemeket (például a Windows Information Protection (folyamatban lévő) védett fájlokat. A szabályzat engedélyezésekor a WIP által védett elemek indexelve lesznek, a velük kapcsolatos metaadatok pedig titkosítatlan helyen lesznek tárolva. A metaadatok között szerepel egyebek között a fájl elérési útja és módosításának dátuma. Ha a házirend le van tiltva, a rendszer nem indexeli a nem indexelt, és nem jeleníti meg az eredményeket a Cortana vagy a fájlkezelőben. A Fényképek és a Groove alkalmazás teljesítménye csökkenhet, ha nagy mennyiségű WIP-védelemmel ellátott médiafájl található az eszközön.  
  [További információ]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Alapértelmezett**: igen
  
## <a name="smart-screen"></a>Intelligens képernyő  
További információ: [Policy CSP-SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) a Windows dokumentációjában.  

- **Nem ellenőrzött fájlok végrehajtásának letiltása**  
  Nem ellenőrzött fájlok futtatásának letiltása a felhasználó számára. 
  - *Nincs konfigurálva* – az alkalmazottak figyelmen kívül hagyhatják a SmartScreen-figyelmeztetéseket, és kártékony fájlokat futtathatnak. 
  - *Igen* – az alkalmazottak nem hagyhatják figyelmen kívül a SmartScreen-figyelmeztetéseket, és nem futtathatnak rosszindulatú fájlokat.

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Alapértelmezett**: igen

- **SmartScreen megkövetelése alkalmazások és fájlok esetén**  
  Lehetővé teszi a rendszergazdáknak a SmartScreen konfigurálását Windows rendszeren.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Alapértelmezett**: igen
  
## <a name="system"></a>Rendszer  
További információ: [Policy CSP – rendszer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) a Windows dokumentációjában.  

- **Rendszerindítási indítási illesztőprogram inicializálása**  
  Ezzel a házirend-beállítással megadhatja, hogy mely rendszerindítási illesztőprogramok legyenek inicializálva egy korai indítási antimalware rendszerindítási illesztőprogram által meghatározott besorolás alapján. A korai indítású antimalware rendszerindítási illesztőprogram a következő besorolásokat adhatja vissza minden rendszerindítási illesztőprogramhoz: 
  - *Jó* – az illesztőprogram aláírása megtörtént, és a nem lett illetéktelenül módosítva.  
  - *Rossz* – az illesztőprogram kártevőként lett azonosítva. Azt javasoljuk, hogy ne engedélyezze az ismert hibás illesztőprogramok inicializálását. 
  - *Rossz, de szükséges a rendszerindításhoz* – az illesztőprogram kártevőként van azonosítva, de a számítógép nem tud sikeresen elindulni az illesztőprogram betöltése nélkül. 
  - *Ismeretlen* – ezt az illesztőprogramot a kártevő-észlelési alkalmazás nem tanúsította, és a korai indítású antimalware rendszerindítási illesztőprogram nem sorolta be.  

  Ha engedélyezi ezt a házirend-beállítást, kiválaszthatja, hogy mely rendszerindítási illesztőprogramokat szeretné inicializálni a számítógép következő indításakor. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszerindítási illesztőprogramok helyesnek, ismeretlennek vagy hibásnak, de a rendszerindítási kritikusnak megfelelően vannak inicializálva, és a helytelenül meghatározott illesztőprogramok inicializálását a rendszer kihagyja. Ha a kártevő-észlelési alkalmazás nem tartalmaz korai indítású antimalware rendszerindítási illesztőprogramot, vagy ha a korai indítású kártevő-indítási illesztőprogram le van tiltva, akkor ez a beállítás nem lép érvénybe, és az összes rendszerindítási illesztőprogram inicializálva van.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Alapértelmezett**: jó ismeretlen és rossz kritikus


## <a name="wi-fi"></a>Wi-Fi  
További információ: [Policy CSP-WiFi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) a Windows-dokumentációban.  

- **Internetes megosztás letiltása**  
  Megadja, hogy lehetséges-e az internetes megosztás az eszközön.   
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Alapértelmezett**: igen  

- **A Wi-Fi elérési pontokhoz való automatikus csatlakozás letiltása**  
  A Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése vagy letiltása az eszközön.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Alapértelmezett**: igen  
  
## <a name="windows-connection-manager"></a>Windows Csatlakozáskezelő  
További információ: [Policy CSP-WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) a Windows dokumentációjában.  

- **Nem tartományi hálózatokhoz való kapcsolódás letiltása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a számítógépek egyszerre egy tartományalapú hálózathoz és egy nem tartományon alapuló hálózathoz csatlakozzanak. Ha ez a házirend-beállítás engedélyezve van, a számítógép a következő esetekben válaszol az automatikus és a manuális hálózati csatlakozási kísérletekre: 
  - Ha a számítógép már csatlakozik egy tartományalapú hálózathoz, az automatikus kapcsolódási kísérleteket a rendszer letiltja a nem tartományi hálózatokra irányuló összes automatikus kapcsolódási kísérletet. Ha a számítógép már csatlakozik egy nem tartomány alapú hálózathoz, a rendszer letiltja a tartományalapú hálózatokra irányuló automatikus kapcsolódási kísérleteket. 
  - A manuális kapcsolódási kísérlet akkor fordul elő, ha a számítógép már csatlakoztatva van egy nem tartomány alapú hálózathoz vagy egy, az Etherneten kívüli, más adathordozón található tartományalapú hálózathoz, és egy felhasználó egy további, a szabályzat megsértése miatti hálózathoz való csatlakozást kísérel meg létrehozni. beállítás, a meglévő hálózati kapcsolat megszakad, és a manuális kapcsolat engedélyezett. Ha a számítógép már csatlakoztatva van egy nem tartomány alapú hálózathoz vagy egy tartományalapú hálózathoz Ethernet-kapcsolaton keresztül, és egy felhasználó egy további, a házirend-beállítás megsértése miatti hálózatra irányuló manuális kapcsolatot próbál létrehozni, a meglévő Ethernet-kapcsolat karbantartva, és a manuális kapcsolódási kísérlet le van tiltva.  

  Ha a házirend-beállítás nincs konfigurálva vagy le van tiltva, a számítógépek egyszerre csatlakozhatnak a tartományhoz és a tartományhoz nem tartozó hálózatokhoz is.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Alapértelmezett**: engedélyezve
  
## <a name="microsoft-defender"></a>Microsoft Defender  
További információ: [Policy CSP-Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) a Windows dokumentációjában.  

- **Bejövő üzenetek ellenőrzése**  
  Engedélyezi vagy engedélyezi az e-mailek vizsgálatát.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Alapértelmezett**: igen  

- **Az Office-alkalmazások alárendelt folyamatának indítása**  
  Az Office-alkalmazások nem hozhatnak létre alárendelt folyamatokat. Ide tartozik a Word, az Excel, a PowerPoint, a OneNote és a hozzáférés. Ez egy tipikus kártevő-viselkedés, különösen olyan makró-alapú támadások esetében, amelyek az Office-alkalmazások használatával próbálnak meg rosszindulatú végrehajtható fájlokat elindítani vagy letölteni.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Alapértelmezett**: letiltás
  
- **Defender-minta küldésének beleegyező típusa**  
  A Microsoft Defender felhasználói beleegyezési szintjének ellenőrzése az adatküldéshez. Ha a szükséges engedély már meg lett adva, a Microsoft Defender beküldi őket. Ha nem, (és ha a felhasználónak soha nem kell megadnia a kérdést), a felhasználói felület megadását kéri (ha a Defender/AllowCloudProtection engedélyezett) az adatok elküldése előtt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Alapértelmezett**: biztonságos minták automatikus küldése 
  
- **Aláírás-frissítési időköz (óra)**  
  Defender-aláírás frissítési időköze (óra)
  
  **Alapértelmezett**: 4
  
- **Parancsfájl letöltött adattartalom-végrehajtási típusa**  
  Defender-parancsfájl letöltött adattartalom-végrehajtási típusa
  
  **Alapértelmezett**: letiltás
  
- **Hitelesítő adatok ellopási típusának tiltása**  
  A Microsoft Defender hitelesítőadat-őr virtualizálás-alapú biztonságot használ a titkok elkülönítésére, így csak a rendszerjogosultságú rendszerszoftverek férhetnek hozzájuk. A titkos kódokhoz való illetéktelen hozzáférés a hitelesítési adatok ellopását okozó (például pass-the-hash vagy pass-the-ticket típusú) támadásokhoz vezethetnek. A Microsoft Defender hitelesítőadat-őr megakadályozza ezeket a támadásokat az NTLM jelszó-kivonatok, a Kerberos-jegyek és az alkalmazások tartományi hitelesítő adatokként tárolt hitelesítő adatainak védelmével.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Alapértelmezett**: Engedélyezés

- **E-mail tartalom végrehajtásának típusa**  
  Ez a szabály blokkolja a következő fájltípusokat, amelyek a Microsoft Outlook vagy webmail (például Gmail.com vagy Outlook.com) által látott e-mailből futtathatók vagy indíthatók: végrehajtható fájlok (például. exe,. dll vagy. scr) parancsfájlok (például PowerShell. ps, VisualBasic. vbs, vagy a JavaScript. js fájl) parancsfájl-archiválási fájlok.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **Alapértelmezett**: letiltás
::: zone-end
::: zone pivot="mdm-may-2019"

- **Adobe Reader indítása alárendelt folyamatban**  

  **Alapértelmezett**: Engedélyezés
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Hálózati védelem**  
  Ez a szabályzat lehetővé teszi a hálózati védelem (Letiltás/naplózás) bekapcsolását a Microsoft Defender Exploit Guard-ben. A hálózatvédelem a Microsoft Defender kiaknázási őr szolgáltatása, amely megvédi az alkalmazottakat az adathalászat-csalások, a biztonsági rések és a rosszindulatú tartalmak interneten való elérésének bármely alkalmazásával. Ez magában foglalja a harmadik féltől származó böngészőknek a veszélyes helyekhez való csatlakozásának megakadályozását. Az érték típusa egész szám. Ha engedélyezi ezt a beállítást, a hálózati védelem be van kapcsolva, és az alkalmazottak nem kapcsolhatják ki. A viselkedését a következő beállítások szabályozzák: letiltás és naplózás. Ha engedélyezi ezt a házirendet a "letiltás" beállítással, a felhasználók és az alkalmazások le vannak tiltva a veszélyes tartományokhoz való csatlakozáskor. Ezt a tevékenységet a Microsoft Defender Security Centerban tekintheti meg. Ha engedélyezi ezt a házirendet a "naplózás" beállítással, a felhasználók/alkalmazások nem lesznek letiltva a veszélyes tartományokhoz való csatlakozáskor. Ezt a tevékenységet azonban továbbra is megtekintheti a Microsoft Defender Security Centerban. Ha letiltja ezt a házirendet, a felhasználók/alkalmazások nem lesznek letiltva a veszélyes tartományokhoz való csatlakozáskor. A Microsoft Defender Security Centerban semmilyen hálózati tevékenység nem jelenik meg. Ha nem konfigurálja ezt a házirendet, a hálózati blokkolás alapértelmezés szerint le van tiltva.  
  [További információ](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)  
  
  **Alapértelmezett**: Engedélyezés
  
- **Defender-ütemterv vizsgálatának napja**  
  Defender-ütemterv vizsgálatának napja.
  
  **Alapértelmezett**: mindennapi
  
- **Felhőbe szállított védelem**  
  A számítógép legjobb védelméhez a Microsoft Defender adatokat küld a Microsoftnak a talált problémákról. A Microsoft elemezni fogja ezeket az információkat, többet tudhat meg az Ön és más ügyfelek problémáit érintő problémákról, és továbbfejlesztett megoldásokat kínál.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Alapértelmezett**: igen  

- **A Defender vélhetően nemkívánatos alkalmazásának művelete**  
  A Microsoft Defender Antivirus vélhetően nemkívánatos alkalmazás-(PUA-) védelmi funkciója képes azonosítani és letiltani a PUAs a hálózaton lévő végpontokon való letöltés és telepítés során. Ezek az alkalmazások nem tekintendők vírusok, kártevők vagy más típusú fenyegetéseknek, de olyan végpontokon is végezhetnek műveleteket, amelyek hátrányosan befolyásolják a teljesítményüket vagy a használatukat. A PUA olyan alkalmazásokra is hivatkozhat, amelyeknek a megítélése szerint rossz hírnevük van. A tipikus PUA-viselkedés többek között az alábbiakat tartalmazza: különböző típusú szoftver-árukapcsolás ad-befecskendezés a böngészők és a beállításjegyzék-optimalizálók számára, amelyek a hibákat észlelik, a hibák kijavításához, de a végponton maradva nem módosítanak vagy optimalizálást (más néven " Rogue Antivirus "programok". Ezek az alkalmazások növelhetik a kártevő szoftverrel fertőzött hálózat kockázatát, így a rosszindulatú fertőzések nehezebben azonosíthatók, és az informatikai erőforrások az alkalmazások tisztításával is felhasználhatók.  
  [További információ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Alapértelmezett**: letiltás  

- **Parancsfájl által eltorzított kód típusa**  
  A kártevők és egyéb fenyegetések megpróbálják eltorzítani vagy elrejteni a kártékony kódokat bizonyos parancsfájlokban. Ez a szabály akadályozza meg, hogy a rendszer ne futtasson olyan parancsfájlokat, amelyek nem futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Alapértelmezett**: letiltás
  
- **Cserélhető meghajtók vizsgálata teljes vizsgálat során**  
  Lehetővé teszi a Microsoft Defender számára, hogy a teljes vizsgálat során kártékony és nemkívánatos szoftvereket keressen a cserélhető meghajtókon (például flash-meghajtókon). A Microsoft Defender víruskereső a végrehajtás előtt megkeresi az USB-eszközökön lévő összes fájlt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Alapértelmezett**: igen  
  
- **Archív fájlok ellenőrzése**  
  Defender-vizsgálat archív fájljai.
  
  **Alapértelmezett**: igen
  
- **Viselkedés figyelése**  
  Engedélyezi vagy engedélyezi a Microsoft Defender viselkedésének figyelését. A Windows 10 rendszerbe ágyazott érzékelők begyűjtik és feldolgozzák az operációs rendszer viselkedési jeleit, és elküldik az érzékelő adatait a Microsoft Defender ATP privát, elkülönített, Felhőbeli példányának.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Alapértelmezett**: igen

- **Hálózati mappákból megnyitott fájlok vizsgálata**  
  Ha a fájlok csak olvashatók, a felhasználó nem tudja eltávolítani az észlelt kártevőket.
  
  **Alapértelmezett**: igen

- **Nem megbízható USB-folyamat típusa**  
  Ezzel a szabállyal a rendszergazdák megakadályozhatják az aláíratlan vagy nem megbízható végrehajtható fájlok futtatását USB cserélhető meghajtókról, beleértve az SD-kártyákat is.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Alapértelmezett**: letiltás
  
- **Office-alkalmazások egyéb folyamat-injektálási típusa**  
  Az Office-alkalmazások, például a Word, az Excel, a PowerPoint és a OneNote, nem tudnak kódot beszúrni más folyamatokra. Ezt általában a kártevők használják rosszindulatú kód futtatására arra az kísérletre, hogy el lehessen rejteni a tevékenységet a víruskereső keresőmotorokból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Alapértelmezett**: letiltás
  
- **Office-makróvédelmi kód engedélyezése Win32 importálási típus**  
  A kártevők a Win32 DLL-fájlok importálásához és betöltéséhez használhatnak makróvírus-kódot az Office-fájlokban, amelyek ezután API-hívások készítésére használhatók a rendszeren belüli további fertőzés engedélyezéséhez. Ez a szabály megkísérli letiltani a Win32 DLL-ek importálására képes makrót tartalmazó Office-fájlokat. Ide tartozik a Word, az Excel, a PowerPoint és a OneNote.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Alapértelmezett**: letiltás  
  
- **Defender Cloud Block-szint**  
  A Defender Cloud Block szintje.
  
  **Alapértelmezett**: nincs konfigurálva

- **Valós idejű figyelés**  
  A Defender valós idejű figyelést igényel.
  
  **Alapértelmezett**: igen
 
::: zone-end
::: zone pivot="mdm-may-2019"
- **Office kommunikációs alkalmazások indítása alárendelt folyamatban**  

  **Alapértelmezett**: Engedélyezés
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Office-alkalmazások végrehajtható tartalom létrehozási vagy indítási típusa**  
  Ez a szabály a végrehajtható fájlokat létrehozó vagy indító gyanús és kártékony bővítmények és parancsfájlok (bővítmények) által használt jellemző viselkedéseket célozza meg. Ez egy tipikus kártevő-módszer. Az Office-alkalmazások nem használják a bővítményeket. Ezek a bővítmények általában a Windows Scripting Host (. wsh fájlok) használatával futtatnak bizonyos feladatokat automatizáló vagy felhasználó által létrehozott kiegészítő funkciókat biztosító parancsfájlokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Alapértelmezett**: letiltás

::: zone-end
::: zone pivot="mdm-may-2019"
## <a name="microsoft-defender-firewall"></a>Microsoft Defender-tűzfal  
További információ: [2.2.2 FW_PROFILE_TYPE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) a Windows-protokollok dokumentációjában.  

- **Tűzfal-profil tartománya**  
  Meghatározza azokat a profilokat, amelyekhez a szabály tartozik: tartomány, privát, nyilvános. Ez az érték a tartományokhoz csatlakozó hálózatok profilját jelöli.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: igen

  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: igen 

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezés**: engedélyezett

- **Nyilvános tűzfal-profil**  
  Meghatározza azokat a profilokat, amelyekhez a szabály tartozik: tartomány, privát, nyilvános. Ez az érték a nyilvános hálózatok profilját jelöli. Ezek a hálózatok a kiszolgáló gazdagépének rendszergazdái. A besorolás akkor történik meg, amikor a gazdagép először csatlakozik a hálózathoz. Ezek a hálózatok általában olyan repülőtereken, kávézókban és más nyilvános helyeken találhatók, ahol a hálózatban vagy a hálózati rendszergazdában található társai nem megbízhatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: igen

  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: igen 

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezés**: engedélyezett

  - **Nincs egyesítve a csoportházirendből származó kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: igen

  - **A csoportházirend házirend-szabályai nem lettek egyesítve**  
    **Alapértelmezett**: igen

- **Saját tűzfal-profil**  
  Meghatározza azokat a profilokat, amelyekhez a szabály tartozik: tartomány, privát, nyilvános. Ez az érték a magánhálózatok profilját jelöli.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: igen

  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: igen 

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezés**: engedélyezett

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello  
- **Fokozott hamisítás szükséges, ha elérhető**  
  Ha igen, akkor az eszközök fokozott hamisítást alkalmaznak, ha elérhető. Ha nem, a rendszer letiltja a hamisítás elleni hamisítást. Nincs konfigurálva, az ügyfélen végzett konfigurációk tiszteletben tartása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Alapértelmezett**: igen

- **Vállalati Windows Hello** -  konfigurálása  
    A vállalati Windows Hello egy alternatív módszer a Windowsba való bejelentkezéshez jelszavak, intelligens kártyák és virtuális intelligens kártyák helyett.  

  - Ha az *Igen*értékre van állítva, akkor engedélyezi ezt a házirendet, és az eszköz kiépíti a vállalati Windows Hello-t.  
  - Ha a *nincs konfigurálva*értékre van állítva, az alapterv nem befolyásolja az eszköz házirend-beállítását. Ez azt jelenti, hogy ha a vállalati Windows Hello le van tiltva egy eszközön, az továbbra is le lesz tiltva. Ha engedélyezve van, az továbbra is engedélyezett marad. 

  A vállalati Windows Hello nem tiltható le ezen alapterven keresztül. A Windows Hello for Business letiltható a [Windows-regisztráció](windows-hello.md)konfigurálásakor, vagy az [Identity Protection](identity-protection-configure.md)eszköz konfigurációs profiljának részeként.  

  **Alapértelmezett**: igen

- **Kisbetűk megkövetelése a PIN-kódban**  
  Ha szükséges, a felhasználói PIN-kódnak tartalmaznia kell legalább egy kisbetűt.

  **Alapértelmezés**: engedélyezett

- **Speciális karakterek megkövetelése a PIN-kódban**  
  Ha szükséges, a felhasználói PIN-kódnak tartalmaznia kell legalább egy speciális karaktert.

  **Alapértelmezés**: engedélyezett

- **PIN-kód minimális hossza**  
  A PIN-kód minimális hosszának 4 és 127 között kell lennie.

  **Alapértelmezett**: 6

- **Nagybetűk megkövetelése a PIN-kódban**  
  Ha szükséges, a felhasználó PIN-kódjának legalább egy nagybetűt tartalmaznia kell.

  **Alapértelmezés**: engedélyezett
::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="windows-ink-workspace"></a>Windows Ink-munkaterület  
További információ: [Policy CSP-WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) a Windows dokumentációjában.  

- **Szabadkézi munkaterület**  
  Megadja, hogy engedélyezi-e a felhasználó számára a szabadkézi munkaterület elérését. 
  - *Letiltva* – a szabadkézi munkaterület hozzáférése le van tiltva. A szolgáltatás ki van kapcsolva.
  - *Engedélyezve* – a tinta munkaterület funkció be van kapcsolva, de a felhasználó nem férhet hozzá a zárolási képernyő felett.
  - *Nincs konfigurálva* – a tinta munkaterület funkció be van kapcsolva, és a felhasználó a zárolási képernyő felett is használhatja.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Alapértelmezett**: engedélyezve
 
## <a name="windows-powershell"></a>Windows PowerShell  
További információ: [Policy CSP-WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) a Windows dokumentációjában.  

- **Rendszerhéj-rendszerhéj parancsfájl-blokkolási naplózása**  
  Ezzel a házirend-beállítással engedélyezhető a PowerShell-parancsfájl összes bemenetének naplózása a Microsoft-Windows-PowerShell/operatív eseménynaplóba. Ha engedélyezi ezt a házirend-beállítást, a Windows PowerShell naplózza a parancsok, parancsfájl-blokkok, függvények és parancsfájlok feldolgozását – akár interaktív módon, akár automatizálás útján. Ha letiltja ezt a házirend-beállítást, a PowerShell-parancsfájl bemenetének naplózása le van tiltva. Ha engedélyezi a parancsfájl-blokkoló naplózását, a PowerShell emellett naplózza az eseményeket, amikor egy parancs, parancsfájl-blokk, függvény vagy parancsfájl meghívása elindul vagy leáll. A meghívásos naplózás engedélyezése nagy mennyiségű eseménynaplót generál. Megjegyzés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználó konfigurációja területen található a Csoportházirend szerkesztőben. A számítógép-konfigurációs házirend beállítása elsőbbséget élvez a felhasználói konfigurációs házirend beállításával szemben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Alapértelmezett**: engedélyezve

::: zone-end
::: zone pivot="mdm-may-2019"  
## <a name="whats-changed-in-the-new-template"></a>Az új sablon módosítása
A *május 2019 sablon Mdm biztonsági alapterve* a következő változásokkal rendelkezik az *előnézeti* sablonban.

### <a name="changes-to-the-baseline-settings"></a>Az alapkonfiguráció beállításainak módosításai
A következő beállítások egyike:
- *Új* az alapkonfiguráció ezen legújabb verziójában.
- A rendszer *eltávolítja* a legújabb alapverzióról, de az előző verzióban szerepelt.
- A beállítások a korábbi verziókban való megjelenésének valamilyen módon *módosultak* . 

*[Új]* a [**zárolás felett**](#above-lock):
- **Alkalmazások hang aktiválása zárolt képernyőről**    

*[Új]* [**alkalmazás-kezelés**](#application-management): 
- **Felhasználók felügyeletének tiltása a telepítéseken**  
- **MSI-alkalmazások telepítésének letiltása emelt szintű jogosultságokkal**  

*[Eltávolítva]* [**BitLocker**](#bitlocker):  
- Bites zárolás cserélhető meghajtó házirendje > **titkosítási módszer**
- **Bit Locker rögzített meghajtó házirendje** *(minden beállítás)*
- **Bit Locker rendszermeghajtó házirendje** *(minden beállítás)*

*[Új]* [**kapcsolat**](#connectivity):
- **Az UNC elérési utak biztonságos elérésének konfigurálása**

*[Új]* [**Device Guard**](#device-guard):
- **Virtualizálás-alapú biztonság**


*[Új]* [**DMA-őr**](#dma-guard):
- **A kernel DMA-védelemmel nem kompatibilis külső eszközök enumerálása**  

*[Új]* [**Internet Explorer**](#internet-explorer):
- **Internet Explorer Internet zóna frissítései az állapotsoron parancsfájl használatával**
- **Internet Explorer Internet Zone húz és eldobása, illetve fájlok másolása és beillesztése**  
- **Az Internet Explorer korlátozott zóna .NET-keretrendszerének függő összetevői**  
- **Az Internet Explorer helyi számítógép zónája ne futtasson antimalware-t az aktív X vezérlőkön**
- **Az Internet Explorer titkosításának támogatása**  

*[Felülvizsgált]* [**Internet Explorer**](#internet-explorer):
- **Internet Explorer Internet Zone automatikus Rákérdezés a fájlok letöltésére** > az alapértelmezett érték most **le van tiltva**. Az előzetes verzióban ez engedélyezve értékre van állítva.

*[Új]* [**Távsegítség**](#remote-assistance):  
- **Távsegítség kérése** 
  - **Távsegítség által kért engedély**
  - **Jegy maximális élettartama**  
  - **Jegyek maximális időtartama**  
  - **E-Mail Meghívási módszere**


*[Új]* [**Microsoft Defender**](#microsoft-defender):
- **Adobe Reader indítása alárendelt folyamatban**  
- **Office kommunikációs alkalmazások indítása alárendelt folyamatban** 

*[Új]* [ **Microsoft Defender-tűzfal**](#microsoft-defender-firewall)
- **Tűzfal-profil tartománya**  
  - **Bejövő kapcsolatok blokkolva**  
  - **Kimenő kapcsolatok szükségesek**  
  - **Bejövő értesítések blokkolva**  
  - **Tűzfal engedélyezve**  
- **Nyilvános tűzfal-profil**  
  - **Bejövő kapcsolatok blokkolva**  
  - **Kimenő kapcsolatok szükségesek**  
  - **Bejövő értesítések blokkolva**  
  - **Tűzfal engedélyezve** 
  - **Nincs egyesítve a csoportházirendből származó kapcsolatbiztonsági szabályok**   
  - **A csoportházirend házirend-szabályai nem lettek egyesítve**  
- **Saját tűzfal-profil**  
  - **Bejövő kapcsolatok blokkolva**  
  - **Kimenő kapcsolatok szükségesek**  
  - **Bejövő értesítések blokkolva**  
  - **Tűzfal engedélyezve**  

*[Új]* [**vállalati Windows Hello**](#windows-hello-for-business):  
- **Fokozott hamisítás szükséges, ha elérhető**  
- **A vállalati Windows Hello konfigurálása**  
- **Kisbetűk megkövetelése a PIN-kódban** 
- **Speciális karakterek megkövetelése a PIN-kódban** 
- **PIN-kód minimális hossza**  
- **Nagybetűk megkövetelése a PIN-kódban** 
::: zone-end




 