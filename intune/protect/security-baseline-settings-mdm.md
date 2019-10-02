---
title: Az Intune biztonsági alapkonfigurációinak beállításai a Windows 10 rendszerhez
titleSuffix: Microsoft Intune
description: Tekintse át az Intune-nal felügyelt Windows 10-es eszközök Windows MDM biztonsági alapkonfigurációjában található alapértelmezéseket és elérhető beállításokat.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7bba4617aa756c5f7168a2febf1a3f1ffdd2029
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731959"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>MDM biztonsági alapkonfigurációjának beállításai az Intune-ban  

Tekintse meg a Microsoft Intune által támogatott MDM biztonsági alapbeállításokat a Windows 10 vagy újabb rendszerű eszközökön. Az alapkonfigurációban a beállítások alapértelmezett értékei a megfelelő eszközök ajánlott konfigurációját jelentik, és előfordulhat, hogy nem egyeznek az alapértékekkel más biztonsági alaptervekben.  

A legújabb alapverzió a 2019-as **Mdm biztonsági** alapkonfiguráció.  

Ha többet szeretne megtudni arról, hogy mi változott az alapkonfiguráció legújabb verziójában az előző verzióban, tekintse meg [a mi változott az új sablonban](#whats-changed-in-the-new-template).  

> [!NOTE]  
> Az előzetes verziójú MDM biztonsági alapkonfigurációt a 2019-es számú biztonsági alapkonfiguráció váltotta fel, amely a május 2019 sablonra vonatkozó, általánosan elérhető (nem előzetes verzióban elérhető) *Mdm biztonsági* alaptervet váltott ki. A *május 2019-es Mdm biztonsági* alapkonfigurációjának rendelkezésre állása előtt létrehozott profilok nem frissülnek, hogy TÜKRÖZZÉK a Mdm biztonsági alaptervében a 2019-es verzióra vonatkozó beállításokat és értékeket.  Bár az előnézeti sablon alapján nem hozhatók létre új profilok, szerkesztheti és tovább használhatja a korábban létrehozott profilokat az előnézeti sablon alapján.   
  
A biztonsági alapkonfigurációk Intune-nal történő használatáról további információt a biztonsági alapkonfigurációk [használata](security-baselines.md)című témakörben talál.  


   
## <a name="above-lock"></a>Zárolás felett  
További információ: [Policy CSP-AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) a Windows dokumentációjában.  

- **Bejelentési értesítések megjelenítésének tiltása**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy az alkalmazás értesítései megjelenjenek a zárolási képernyőn. Ha engedélyezi ezt a házirend-beállítást, akkor a zárolási képernyőn nem jelennek meg alkalmazás-értesítések. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználók kiválaszthatják, hogy mely alkalmazások jelenítsék meg az értesítéseket a zárolási képernyőn.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Alapértelmezett**: Igen  

- **Alkalmazások hang aktiválása zárolt képernyőről**  

  **Alapértelmezett**: Letiltva

## <a name="app-runtime"></a>Alkalmazás futtatókörnyezete    
További információ: [Policy CSP-AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) a Windows dokumentációjában.  

- **Microsoft-fiókok választhatók a Windows áruházbeli alkalmazásokhoz**  
  Ezzel a házirend-beállítással szabályozhatja, hogy a Microsoft-fiókok választhatók-e olyan Windows áruházbeli alkalmazásokhoz, amelyekhez fiók szükséges a bejelentkezéshez. Ez a szabályzat csak az azt támogató Windows áruházbeli alkalmazásokat érinti. Ha engedélyezi ezt a házirend-beállítást, a Windows áruházbeli alkalmazások, amelyek általában a bejelentkezéshez Microsoft-fiók igényelnek, lehetővé teszik a felhasználók számára a vállalati fiókkal való bejelentkezést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználóknak Microsoft-fiók kell bejelentkezniük.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Alapértelmezett**: Enabled  

## <a name="application-management"></a>Alkalmazások kezelése   
További információ: [Policy CSP-ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) a Windows dokumentációjában.  

- **Felhasználók felügyeletének tiltása a telepítéseken**  
  Ezzel a házirend-beállítással a felhasználók módosíthatják azokat a telepítési beállításokat, amelyek jellemzően csak rendszergazdák számára érhetők el. Ha engedélyezi ezt a házirend-beállítást, a Windows Installer egyes biztonsági funkcióit a rendszer figyelmen kívül hagyja. Lehetővé teszi a telepítés befejezését, mert a biztonsági szabálysértés miatt leáll. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a Windows Installer biztonsági funkciói megakadályozzák, hogy a felhasználók a rendszergazdák számára fenntartott telepítési beállításokat használják, például megadhatják azt a könyvtárat, amelyre a fájlok telepítve vannak. Ha Windows Installer észleli, hogy egy telepítőcsomag engedélyezte a felhasználó számára egy védett beállítás módosítását, leállítja a telepítést, és megjelenít egy üzenetet. Ezek a biztonsági funkciók csak akkor működnek, ha a telepítőprogram olyan rendszerjogosultságú biztonsági környezetben fut, amelyben hozzáfér a felhasználónak elutasítottak könyvtáraihoz. Ez a házirend-beállítás kevésbé korlátozó környezetekhez készült. A használatával megkerülheti a szoftverek telepítését megakadályozó telepítőprogram hibáit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Alapértelmezett**: Igen

- **MSI-alkalmazások telepítésének letiltása emelt szintű jogosultságokkal**  
  Ezzel a házirend-beállítással a Windows Installer emelt szintű engedélyek használhatók, amikor a rendszerre telepít bármely programot.  
  - *Ha engedélyezi ezt a házirend-beállítást*, a rendszer minden programra kiterjeszti a jogosultságokat. Ezek a jogosultságok általában olyan programok számára vannak fenntartva, amelyek hozzá vannak rendelve a felhasználóhoz (az asztalon elérhető), a számítógéphez (automatikusan telepített) f, vagy elérhetővé válnak a Vezérlőpult Programok telepítése és törlése segédprogramjában. Ez a Profilbeállítások lehetővé teszi, hogy a felhasználók olyan programokat telepítsenek, amelyek hozzáférést igényelnek a címtárakhoz, amelyekhez a felhasználónak nincs engedélye a megtekintésre vagy a módosításra, beleértve a nagymértékben korlátozott számítógépeken lévő
  - *Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást*, akkor a rendszer az aktuális felhasználó engedélyeit alkalmazza, amikor olyan programokat telepít, amelyeket a rendszergazda nem terjeszt el vagy biztosít. Megjegyezés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználói konfigurációs mappákban is megjelenik. Ahhoz, hogy ez a házirend-beállítás érvényes legyen, mindkét mappában engedélyeznie kell azt. Vigyázat A gyakorlott felhasználók kihasználhatják az engedélyek előnyeit ezzel a házirend-beállítással, hogy megváltoztassák a jogosultságokat, és állandó hozzáférést szerezzenek a korlátozott fájlokhoz és mappákhoz. Vegye figyelembe, hogy a házirend-beállítás felhasználói konfigurációs verziója nem garantált, hogy biztonságos legyen.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Alapértelmezett**: Igen

- **Játék DVR blokkolása (csak asztali verzió)**  
  Annak konfigurálása, hogy engedélyezett-e a játékok rögzítése és közvetítése.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Alapértelmezett**: Igen  

## <a name="auto-play"></a>Automatikus lejátszás   
További információ: [Policy CSP-Robotpilota](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) a Windows dokumentációjában.  

- **Automatikus lejátszás alapértelmezett automatikus futtatási viselkedése**  
  Ez a beállítás hatással van az automatikus futtatási parancsok alapértelmezett viselkedésére. Az automatikus futtatási parancsok az Autorun. inf fájlban tárolódnak, és a telepítőprogramokat vagy más rutinokat indíthatnak el. Ha ez a *beállítás engedélyezve van*, a rendszergazdák megváltoztathatják a Windows Vista vagy újabb rendszert futtató eszközök alapértelmezett automatikus futtatási viselkedését. A viselkedés beállítható a következőre: a) teljesen letilthatja az automatikus futtatási parancsokat, vagy b) visszatérhet a Windows Vista előtti működésre, amely automatikusan végrehajtja az Autorun parancs futtatását. Ha a beállítás letiltva vagy *nincs konfigurálva*értékre van állítva, akkor a Windows Vista vagy újabb rendszerű eszközök megkérik a felhasználót, hogy az Autorun parancs fusson.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Alapértelmezett**: Végrehajtás mellőzése  
  
- **Automatikus lejátszási mód**  
  Ez a házirend-beállítás lehetővé teszi az automatikus lejátszás funkció kikapcsolását. Az automatikus lejátszás megkezdi a meghajtóról való beolvasást, amint adathordozót szúr be a meghajtóba. Ennek eredményeképpen a programok telepítési fájlja és a hanganyagokon megjelenő zene azonnal elindul. A Windows XP SP2 előtt az automatikus lejátszási szolgáltatás alapértelmezés szerint le van tiltva a cserélhető meghajtókon, például a hajlékonylemez-meghajtón (de nem a CD-ROM-meghajtón) és a hálózati meghajtókon. A Windows XP SP2 verziótól kezdődően az automatikus lejátszás engedélyezve van a cserélhető meghajtókon, beleértve a zip-meghajtókat és néhány USB háttértár-eszközt is. Ha engedélyezi ezt a házirend-beállítást, az automatikus lejátszási funkció le van tiltva a CD-ROM-és cserélhető adathordozó-meghajtókon, vagy le van tiltva az összes meghajtón. Ezzel a házirend-beállítással a további típusú meghajtókon letiltja az Automatikus lejátszást. Ezzel a beállítással nem engedélyezheti az Automatikus lejátszást azon meghajtókon, amelyeken a szolgáltatás alapértelmezés szerint le van tiltva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az automatikus lejátszás engedélyezve van. Megjegyezés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználói konfigurációs mappákban is megjelenik. Ha a házirend-beállítások ütköznek, a számítógép konfigurációjában a házirend-beállítás elsőbbséget élvez a felhasználói konfiguráció házirend-beállításával szemben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Alapértelmezett**: Letiltva

- **Nem mennyiségi eszközök automatikus lejátszásának letiltása**  
  Ez a házirend-beállítás nem engedélyezi az Automatikus lejátszást az MTP-eszközök, például a kamerák vagy a telefonok számára. Ha engedélyezi ezt a házirend-beállítást, az automatikus lejátszás nem engedélyezett MTP-eszközökhöz, például fényképezőgépekhez vagy telefonokhoz. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az automatikus lejátszás engedélyezve van a nem mennyiségi eszközökhöz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Alapértelmezett**: Enabled  

## <a name="bitlocker"></a>BitLocker    
További információ: [Policy CSP-BitLocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) a Windows dokumentációjában.  

- **Bites zárolás cserélhető meghajtó házirendje**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, konfigurálhat egy titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtók, az operációsrendszer-meghajtók és a cserélhető adatmeghajtók számára egyenként. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067140) 

  A következő beállítással állíthatja be a cserélhető meghajtó cserélhető meghajtójának házirendjét:

  - **Titkosítás megkövetelése írási hozzáféréshez**  
    **Alapértelmezett**: Igen  
  

## <a name="browser"></a>Browser  
További információ: [szabályzat CSP-böngésző](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) a Windows dokumentációjában.  

- **SmartScreen megkövetelése a Microsoft Edge-hez**  
  A Microsoft Edge a Windows Defender SmartScreen (bekapcsolva) használatával védi a felhasználókat a lehetséges adathalászat-csalások és kártevő szoftverek alapértelmezés szerint. Alapértelmezés szerint a felhasználók nem letilthatják (kikapcsolják) a Windows Defender SmartScreen szolgáltatását. A házirend engedélyezése kikapcsolja a Windows Defender SmartScreen szolgáltatást, és megakadályozza, hogy a felhasználók bekapcsolják azt. Ne konfigurálja ezt a házirendet úgy, hogy a felhasználók a Windows Defender SmartScreen be-vagy kikapcsolását választják.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Alapértelmezett**: Igen  
  
- **Rosszindulatú hely elérésének letiltása**  
  Alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Windows Defender SmartScreen figyelmeztetéseit a potenciálisan kártékony webhelyekről, így azok továbbra is a webhelyre léphetnek. Ezzel a házirenddel azonban beállíthatja a Microsoft Edge-t, hogy megakadályozza a felhasználók számára a figyelmeztetések megkerülését, és blokkolja őket a helyről.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Alapértelmezett**: Igen  
  
- **Nem ellenőrzött fájlok letöltésének tiltása**  
  Alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Windows Defender SmartScreen figyelmeztetéseit a potenciálisan kártékony fájlokról, így továbbra is letöltheti a nem ellenőrzött fájlokat. A szabályzat engedélyezése megakadályozza, hogy a felhasználók megkerüljék a figyelmeztetéseket, és blokkolja a nem ellenőrzött fájlok letöltését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Alapértelmezett**: Igen  
  
- **A Password Manager letiltása**  
  Alapértelmezés szerint a Microsoft Edge automatikusan a Password Managert használja, így a felhasználók helyileg is elérhetik a jelszavakat. A szabályzat letiltása korlátozza a Microsoft Edge használatát a Password Manager használatával. Ne konfigurálja ezt a házirendet, ha engedélyezni szeretné a felhasználók számára a jelszavak helyi mentését és kezelését a Password Manager használatával.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Alapértelmezett**: Igen  
  
- **Tanúsítvány-hibák felülbírálásának megakadályozása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó figyelmen kívül hagyja a böngészést megszakító SSL/Transport Layer Security (SSL/TLS) tanúsítványokat (például a "lejárt", a "visszavont" vagy a "név eltérése" hibákat) az Internet Explorerben. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem folytathatja a böngészést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó dönthet úgy, hogy figyelmen kívül hagyja a tanúsítvány hibáit, és folytatja a böngészést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Alapértelmezett**: Igen  

## <a name="connectivity"></a>Kapcsolat  
További információ: [Policy CSP – kapcsolat](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) a Windows dokumentációjában.  

- **Internetes letöltés letiltása a webes közzététel és az online rendezési varázslók számára**  
  Ezzel a házirend-beállítással adható meg, hogy a Windows letöltse-e a szolgáltatók listáját a webes közzétételi és az online rendezési varázslókhoz. Ezek a varázslók lehetővé teszik a felhasználók számára, hogy kiválasszák azon vállalatok listáját, amelyek olyan szolgáltatásokat biztosítanak, mint például az online tárterület és a fényképészeti nyomtatás. Alapértelmezés szerint a Windows a beállításjegyzékben megadott szolgáltatók mellett a Windows-webhelyről letöltött szolgáltatókat jeleníti meg. Ha engedélyezi ezt a házirend-beállítást, a Windows nem tölti le a szolgáltatókat, és csak azok a szolgáltatók jelennek meg, amelyek a helyi beállításjegyzékben vannak gyorsítótárazva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer letölti a szolgáltatók listáját, amikor a felhasználó a webes közzétételi vagy online rendezési varázslót használja. További információ a szolgáltatók beállításjegyzékbeli megadásáról: a webes közzététel és az online rendezés varázsló dokumentációja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Alapértelmezett**: Enabled  

- **Az UNC elérési utak biztonságos elérésének konfigurálása**  
  Ezzel a házirend-beállítással biztonságos hozzáférést konfigurálhat az UNC elérési utakhoz. Ha engedélyezi ezt a házirendet, a Windows a további biztonsági követelmények teljesítése után csak a megadott UNC elérési utak elérését teszi lehetővé.
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067243) 

  **Alapértelmezett**: A Windows beállítása úgy, hogy csak a további biztonsági követelmények teljesítése után engedélyezze a megadott UNC elérési utak elérését
  
  Ha a *Windows úgy van beállítva, hogy csak a további biztonsági követelmények teljesítése után engedélyezze a megadott UNC elérési utak elérését* , beállíthatja az * megerősített UNC elérési út listáját.
  - **Megerősített UNC elérési utak listája**  
    Válassza a **Hozzáadás** lehetőséget a további biztonsági jelzők és a kiszolgáló elérési útjának megadásához.  

- **A nyomtatóillesztők HTTP-n keresztüli letöltésének letiltása**  
  Ezzel a házirend-beállítással megadható, hogy az ügyfél letöltse-e a nyomtatóillesztő-csomagokat HTTP-n keresztül. HTTP-nyomtatás beállításához a nem beérkező illesztőprogramokat HTTP-n keresztül kell letölteni. Megjegyezés: Ez a házirend-beállítás nem akadályozza meg, hogy az ügyfél az intraneten vagy az interneten keresztül HTTP-n keresztül nyomtasson a nyomtatókra. Csak a helyileg telepített illesztőprogramok letöltését tiltja le. Ha engedélyezi ezt a házirend-beállítást, a nyomtatóillesztők nem tölthetők le HTTP-n keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználók HTTP-n keresztül tölthetnek le nyomtatóillesztőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Alapértelmezett**: Enabled  

## <a name="credentials-delegation"></a>Hitelesítő adatok delegálása  
További információ: [Policy CSP-CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) a Windows dokumentációjában.  

- **Nem exportálható hitelesítő adatok távoli gazdagép-delegálása**  
  A távoli gazdagép lehetővé teszi a nem exportálható hitelesítő adatok delegálását. A hitelesítő adatok delegálásakor az eszközök a hitelesítő adatok exportálható verzióját biztosítják a távoli gazdagép számára, amely lehetővé teszi a felhasználók számára a távoli gazdagépen lévő támadók által a hitelesítő adatok ellopásának kockázatát. Ha engedélyezi ezt a házirend-beállítást, a gazdagép támogatja a korlátozott rendszergazdai vagy távoli hitelesítő adatok Guard üzemmódot. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a korlátozott felügyelet és a távoli hitelesítőadat-őr mód nem támogatott. A felhasználónak mindig meg kell adnia a hitelesítő adatait a gazdagépen.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Alapértelmezett**: Enabled  

## <a name="credentials-ui"></a>Hitelesítő adatok felhasználói felülete  
További információ: [Policy CSP-CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) a Windows dokumentációjában.  

- **Rendszergazdák számbavétele** Ezzel a házirend-beállítással szabályozható, hogy a rendszergazdai fiókok megjelenjenek-e, amikor egy felhasználó egy futó alkalmazást próbál meg emelni. Alapértelmezés szerint a rendszergazdai fiókok nem jelennek meg, amikor a felhasználó egy futó alkalmazást próbál meg emelni. Ha engedélyezi ezt a házirend-beállítást, a számítógép összes helyi rendszergazdai fiókja megjelenik, így a felhasználó kiválaszthatja az egyiket, és megadhatja a megfelelő jelszót. Ha letiltja ezt a házirend-beállítást, a felhasználóknak mindig meg kell adnia egy felhasználónevet és egy jelszót a jogosultságszint-emeléshez.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Alapértelmezett**: Letiltva  

## <a name="data-protection"></a>Adatvédelem  
További információ: [Policy CSP-DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) a Windows dokumentációjában.  

- **Közvetlen memória-hozzáférés letiltása**  
  Ezzel a házirend-beállítással letilthatja a közvetlen memória-hozzáférést (DMA) az összes melegen csatlakoztatható PCI-porthoz, amíg a felhasználó be nem jelentkezik a Windowsba. Miután a felhasználó bejelentkezik, a Windows feljegyzi a gazdagéphez csatlakozó PCI-portokhoz csatlakozó PCI-eszközöket. Minden alkalommal, amikor a felhasználó zárolja a gépet, a rendszer letiltja a DMA-t a gyermekek nélküli gyors csatlakozású PCI-portok esetében, amíg a felhasználó újra be nem jelentkezik. A gép zárolásának feloldása után már enumerált eszközök továbbra is működni fognak, amíg le nem húzta a gépet. Ez a házirend-beállítás csak akkor lép érvénybe, ha a BitLocker vagy az eszköz titkosítása engedélyezve van.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Alapértelmezett**: Igen  

## <a name="device-guard"></a>Device Guard  
További információ: [Policy CSP-DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) a Windows dokumentációjában.  

- **Hitelesítőadat-őr**  
  Ezzel a beállítással a felhasználók bekapcsolhatják a hitelesítő adatokat a virtualizálás-alapú biztonsággal a hitelesítő adatok védelme érdekében a következő újraindításkor.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Alapértelmezett**: Engedélyezés UEFI-zárral 

- **Virtualizációs alapú biztonság engedélyezése**   
  A virtualizálás-alapú biztonság (VBS) bekapcsolása a következő újraindításkor. A virtualizálás-alapú biztonság a Windows hipervizorral nyújt támogatást biztonsági szolgáltatásokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Alapértelmezett**: Igen  


- **Rendszerőr elindítása**    
  **Alapértelmezett**: Enabled  

## <a name="device-installation"></a>Eszköz telepítése  
További információ: [Policy CSP-DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) a Windows dokumentációjában.  

- **Hardvereszközök telepítése eszköz-azonosítók alapján**  
  Ezzel a házirend-beállítással megadható azoknak az eszközöknek a Plug and Play-azonosítói és-kompatibilis azonosítói, amelyek nem telepíthetők a Windows rendszerben. Ez a házirend-beállítás elsőbbséget élvez minden más olyan házirend-beállítással szemben, amely lehetővé teszi, hogy a Windows telepítsen egy eszközt. Ha engedélyezi ezt a házirend-beállítást, a Windows megakadályozza, hogy olyan eszközt telepítsen, amelynek hardver-azonosítója vagy kompatibilis azonosítója megjelenik a létrehozott listában. Ha engedélyezi ezt a házirend-beállítást egy távoli asztali kiszolgálón, a házirend-beállítás a megadott eszközök távoli asztali ügyfélről a távoli asztali kiszolgálóra való átirányítását befolyásolja. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az eszközök az engedélyezettnek megfelelően telepíthetik és frissíthetik az eszközöket, és más házirend-beállítások is megtiltják azokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **Alapértelmezett**: Hardvereszköz telepítésének letiltása  

  Ha a *hardveres eszköz telepítésének letiltása* lehetőség van kiválasztva, a következő beállítások érhetők el.

  - **A megfelelő hardvereszközök eltávolítása**   
    Ez a beállítás csak akkor érhető el, ha az *eszköz azonosítói alapján* a hardvereszköz telepítése *blokkolja a hardveres eszközök telepítését*.
    
    **Alapértelmezett**: Igen

  - **A letiltott hardveres eszközök azonosítói**  
    Ez a beállítás csak akkor érhető el, ha az *eszköz azonosítói alapján* a hardvereszköz telepítése *blokkolja a hardveres eszközök telepítését*.
    
    **Alapértelmezett**: Igen  
  
- **Hardvereszközök telepítése telepítési osztályok szerint**  
  Ezzel a házirend-beállítással megadhatja az eszközök telepítési osztályának globálisan egyedi azonosítókat (GUID azonosítókat) tartalmazó listáját azon eszközillesztők számára, amelyeket a Windows megakadályoz a telepítésben. Ez a házirend-beállítás elsőbbséget élvez minden más olyan házirend-beállítással szemben, amely lehetővé teszi, hogy a Windows telepítsen egy eszközt. Ha engedélyezi ezt a házirend-beállítást, a Windows megakadályozza azon eszközillesztők telepítését vagy frissítését, amelyek az eszköz telepítési osztályának GUID azonosítói megjelennek a létrehozott listában. Ha engedélyezi ezt a házirend-beállítást egy távoli asztali kiszolgálón, a házirend-beállítás a megadott eszközök távoli asztali ügyfélről a távoli asztali kiszolgálóra való átirányítását befolyásolja. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a Windows a házirend-beállításoknak megfelelően telepítheti és frissítheti az eszközöket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Alapértelmezett**: Hardvereszköz telepítésének letiltása  

  Ha a *hardveres eszköz telepítésének letiltása* lehetőség van kiválasztva, a következő beállítások érhetők el.
  - **A megfelelő hardvereszközök eltávolítása**    
    Ez a beállítás csak akkor érhető el, ha a *telepítési osztályok által telepített hardvereszközök telepítése* *blokkolja a hardvereszközök telepítését*.  

    **Alapértelmezett**: *Nincs alapértelmezett konfiguráció*  

  - **A letiltott hardveres eszközök azonosítói**  
    Ez a beállítás csak akkor érhető el, ha a *telepítési osztályok által telepített hardvereszközök telepítése* *blokkolja a hardvereszközök telepítését*.
    
    **Alapértelmezett**: *Nincs alapértelmezett konfiguráció*  

## <a name="device-lock"></a>Eszköz zárolása  
További információ: [Policy CSP-DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) a Windows dokumentációjában.  

- **Kamera használatának megakadályozása**  
  Letiltja a zárolási képernyő kamera-kapcsolóját a számítógép beállításaiban, és megakadályozza, hogy a rendszer meghívja a kamerát a zárolási képernyőn. Alapértelmezés szerint a felhasználók a zárolási képernyőn is engedélyezhetik a rendelkezésre álló kamera meghívását. Ha engedélyezi ezt a beállítást, a felhasználók többé nem fogják tudni engedélyezni vagy letiltani a zárolási képernyő kamera-hozzáférését a számítógép beállításaiban, és a kamerát nem lehet meghívni a zárolási képernyőn.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Alapértelmezett**: Enabled  

- **Jelszó megkövetelése**  
  Megadja, hogy engedélyezve van-e az eszköz zárolása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Alapértelmezett**: Igen  
  
  Ha a *jelszó* megkövetelése *Igen*értékre van állítva, a következő beállítások érhetők el.

  - **Jelszó minimális karakterkészletének száma**  
    Az erős PIN-kódokhoz vagy jelszóhoz szükséges összetett elemek (kis-és nagybetűk, számok és írásjelek) száma. A PIN-kód a következő viselkedést alkalmazza az asztali és a mobileszközök esetében: 1 – csak 2 számjegyből és kisbetűkből álló számjegyek szükségesek 3 számjegyű, kisbetűket és nagybetűket. Asztali Microsoft-fiókok és tartományi fiókok esetében nem támogatott. 4 számjegyű, kisbetűket, nagybetűket és speciális karaktereket kell megadni. Az asztali verzióban nem támogatott. Az alapértelmezett érték az 1.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **Alapértelmezett**: 3  

  - **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**  
    Az eszköz törlése előtt engedélyezett hitelesítési hibák száma. A 0 érték letiltja az eszköz törlési funkcióját.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **Alapértelmezett**: 10  

  - **Jelszó lejárata (nap)**  
    A jelszó maximális élettartama házirend-beállítás határozza meg, hogy mennyi ideig használható a jelszó, mielőtt a rendszer megköveteli a felhasználótól, hogy módosítsa azt. Beállíthatja, hogy a jelszavak egy 1 és 999 közötti számú nap elteltével lejárnak, vagy megadhatja, hogy a jelszavak soha ne járjanak le, ha a napok számát 0-ra állítja. Ha a jelszó maximális kora 1 és 999 nap közé esik, a jelszó minimális élettartama nem lehet kisebb, mint a jelszó maximális kora. Ha a jelszó maximális élettartama 0, akkor a jelszó minimális kora 0 és 998 nap közötti érték lehet.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **Alapértelmezett**: 60  

  - **Kötelező jelszótípus**  
    Meghatározza, hogy milyen típusú PIN-kód vagy jelszó szükséges.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **Alapértelmezett**: Alfanumerikus  

  - **Jelszó minimális hossza**  
    A jelszó minimális hossza házirend-beállítás határozza meg, hogy hány karakterből állhat egy felhasználói fiók jelszava. Megadhat egy 1 és 14 karakter közötti értéket, vagy megadhatja, hogy nincs szükség jelszóra, ha a karakterek számát 0-ra állítja.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **Alapértelmezett**: 8  

  - **Egyszerű jelszavak letiltása**  
    Megadja, hogy engedélyezett-e a PIN-kód vagy a jelszavak (például "1111" vagy "1234"). Az asztal esetében a képjelszavak használatát is szabályozza.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **Alapértelmezett**: Igen  
      *Az Igen beállítás meggátolja az egyszerű jelszavak használatát.* 

  - **Korábbi jelszavak újbóli használatának tiltása**  
    Meghatározza, hogy hány jelszó tárolható a nem használható előzményekben. Az érték tartalmazza a felhasználó aktuális jelszavát. Ha például az *1* értékre kattint, a felhasználó nem tudja újból felhasználni a jelenlegi jelszavát új jelszó kiválasztásakor. Az *5* beállítás azt jelenti, hogy a felhasználók nem állíthatják be az új jelszavukat a jelenlegi jelszavuk vagy az előző négy jelszavuk közül.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Alapértelmezett**: 24  

- **A diavetítés megakadályozása**  
  Letiltja a zárolási képernyő görgetősávjának beállításait a számítógép beállításaiban, és megakadályozza a diavetítés lejátszását a zárolási képernyőn. Alapértelmezés szerint a felhasználók engedélyezheti a diavetítést, amely a gép zárolása után fog futni. Ha engedélyezi ezt a beállítást, a felhasználók nem módosíthatják a számítógép beállításaiban a diavetítés beállításait, és nem indíthatnak el diavetítést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Alapértelmezett**: Enabled  
  *Az Engedélyezve beállítás megadásával megakadályozhatja a diavetítés futtatását.* 

- **Jelszó minimális kora (nap)**  
  A jelszó minimális élettartama házirend-beállítás határozza meg azt az időtartamot (nap), ameddig a felhasználónak meg kell változtatnia a jelszót. 1 és 998 nap közötti értéket adhat meg, vagy a jelszó módosításait azonnal engedélyezheti, ha a napok számát 0-ra állítja. A jelszó minimális élettartama nem lehet kisebb, mint a jelszó maximális kora, kivéve, ha a jelszó maximális élettartama 0 értékű, ami azt jelzi, hogy a jelszavak soha nem járnak le. Ha a jelszó maximális élettartama 0, akkor a jelszó minimális kora 0 és 998 közötti értékre állítható be.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Alapértelmezett**: 1  

## <a name="dma-guard"></a>DMA-őr  
További információ: [Policy CSP-DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) a Windows dokumentációjában.
- **A kernel DMA-védelemmel nem kompatibilis külső eszközök enumerálása**  
  A szabályzat célja, hogy további biztonságot nyújtson a külső DMA-kompatibilis eszközökhöz. Lehetővé teszi a külső DMA-kompatibilis eszközök enumerálásának nagyobb mértékű szabályozását, amely nem kompatibilis a DMA újramegfeleltetésével/az eszköz memóriájának elkülönítésével és a munkavégzéssel. Ez a szabályzat csak akkor lép érvénybe, ha a rendszer belső vezérlőprogramja támogatja a kernel DMA védelmét. A kernel DMA-védelem olyan platform-szolgáltatás, amely nem vezérelhető házirend vagy végfelhasználó által. A rendszernek a gyártáskor támogatottnak kell lennie. Annak vizsgálatához, hogy a rendszeren támogatott-e a kernel DMA-védelem, tekintse meg a kernel DMA-védelem mezőt az MSINFO32. exe összefoglalás lapján.  
  [További információ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Alapértelmezett**: Az összes letiltása   

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
  
  **Alapértelmezett**: Igen  

  Ha a *Windows reflektorfény letiltása* *Igen*értékre van állítva, a következő beállítások érhetők el.
  
  - **Harmadik féltől származó javaslatok letiltása a Windows reflektorfényben**  
    Megadja, hogy engedélyezi-e a harmadik féltől származó szoftvergyártók alkalmazás-és tartalmi javaslatainak használatát a Windows reflektorfényben, például a zárolási képernyő Spotlight, a javasolt alkalmazások a Start menüben és a Windows-tippek. A felhasználók továbbra is láthatják a Microsoft funkcióit, alkalmazásait és szolgáltatásait.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Alapértelmezett**: Igen  
  - **A fogyasztói sajátosságok letiltása**  
    Lehetővé teszi a rendszergazdáknak, hogy csak a felhasználók számára, például a Start Suggestions, a tagsági értesítések, az OOBE utáni alkalmazások telepítése és a csempék átirányítása céljából bekapcsolják a felhasználói élményeket.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Alapértelmezett**: Igen  

## <a name="exploit-guard"></a>Védelem kiaknázása  
További információ: [Policy CSP-ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) a Windows dokumentációjában.  

- **Védelem XML-kódjának kiaknázása**  
  Lehetővé teszi a rendszergazda számára egy olyan konfiguráció kiküldését, amely a kívánt rendszer-és alkalmazás-kockázatcsökkentő beállításokat jelöli a szervezet összes eszközén. A konfigurációt egy XML-fájl jelképezi. A védelem kiaknázásával megvédheti az eszközöket olyan kártevők ellen, amelyek kihasználják a kiaknázást és a fertőzést. A Windows biztonsági alkalmazás vagy a PowerShell használatával hozhat létre kockázatcsökkentő (más néven konfiguráció) készletet. Ezt követően exportálhatja ezt a konfigurációt XML-fájlként, és megoszthatja azt több, a hálózaton található géppel, hogy mindegyiknek ugyanazokat a kockázatcsökkentő beállításokat adja meg. Egy meglévő EMET konfigurációs XML-fájlt is konvertálhat, és importálhatja a biztonsági rés kiaknázása konfigurációs XML-fájlba.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Alapértelmezett**: *A minta XML-fájlja megadva* 
 
## <a name="file-explorer"></a>Fájlkezelő  
További információ: [Policy CSP-fájlkezelő](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) a Windows dokumentációjában.  

- **Az adatvégrehajtás-megelőzés letiltása**  
  Az adatvégrehajtás megakadályozása lehetővé teszi bizonyos örökölt beépülőmodul-alkalmazások működésének leállítását az Explorer leállítása nélkül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Alapértelmezett**: Letiltva  
   
- **A kupac megszakításának letiltása a Sérüléskor**  
  Ha letiltja a megszakított adatvesztést a sérülés miatt, bizonyos örökölt beépülőmodul-alkalmazások az Intéző azonnali leállítása nélkül is működhetnek, bár a tallózó a későbbiekben is váratlanul leállhat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Alapértelmezett**: Letiltva  
    

## <a name="internet-explorer"></a>Internet Explorer  
További információ: [Policy CSP-InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) a Windows dokumentációjában.  

- **Az Internet Explorer korlátozott zónájának frissítései az állapotsorban parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájl engedélyezheti-e a zónán belüli állapotjelző sáv frissítését. 
  - *Ha engedélyezi ezt a házirend-beállítást*, a parancsfájl frissítheti az állapotsort.
  - *Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást*, a parancsfájl nem jogosult az állapotsor frissítésére.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Alapértelmezett**: Letiltva

- **Internet Explorer Internet Zone húz és eldobása, illetve fájlok másolása és beillesztése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók beilleszthetnek-e fájlokat, vagy másolhatnak és beilleszthetnek fájlokat a zónán belüli forrásokból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók áthelyezhetik a fájlokat, vagy automatikusan másolhatják és beilleszthetik a fájlokat a zónából. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat áthúzni vagy másolni. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak fájlokat húzni, vagy fájlokat másolni és beilleszteni a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók áthelyezhetik a fájlokat, vagy a zónából automatikusan másolhatják és beilleszthetik a fájlokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Alapértelmezett**: Letiltás

- **Az Internet Explorer korlátozott zóna .NET-keretrendszerének függő összetevői**    
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-ban nem aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy aláíratlan felügyelt összetevőket kíván-e végrehajtani. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláíratlan felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláíratlan felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Alapértelmezett**: Letiltás


- **Az Internet Explorer helyi számítógép zónája ne futtasson antimalware-t az aktív X vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Alapértelmezett**: Letiltva

- **Internet Explorer Internet Zone-hozzáférés az adatforrásokhoz**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer hozzáférhet-e egy másik biztonsági zónából származó adatokhoz a Microsoft XML Parser (MSXML) vagy a ActiveX Data Objects (ADO) használatával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók betölthetnek egy olyan lapot a zónába, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a lap betöltését az MSXML vagy az ADO protokollt használó zónában a zóna egy másik helyéről származó adatok eléréséhez. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónája különböző tartományokból származó tartalmat húzhat a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy az egyik tartományból egy másik tartományba húzza a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer 9 és korábbi verzióiban a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást az Internetbeállítások párbeszédpanelen.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Alapértelmezett**: Letiltva
  
- **Az Internet Explorer-tanúsítvány címe nem megfelelő figyelmeztetés**  
  Ezzel a házirend-beállítással a tanúsítvány címe nem egyezik a biztonsági figyelmeztetéssel. Ha ez a házirend-beállítás be van kapcsolva, a rendszer figyelmezteti a felhasználót, amikor olyan biztonságos HTTP-(HTTPS-) webhelyeket látogat meg, amelyek egy másik webhely címeként kiállított tanúsítványokat jelennek meg Ez a figyelmeztetés segít megelőzni a hamisítás elleni támadásokat. Ha engedélyezi ezt a házirend-beállítást, a tanúsítvány címe nem megfelelő figyelmeztetés mindig megjelenik. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a tanúsítvány címe nem megfelelő figyelmeztetés jelenik-e meg (a Speciális lapon az Internet Vezérlőpulton).  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer korlátozott zónáinak kevésbé privilegizált helyei**  
  Ezzel a házirend-beállítással felügyelheti, hogy a webhelyek kevesebb jogosultsági szintű zónából, például internetes webhelyről is bejelentkezhetnek-e a zónába. Ha engedélyezi ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát. A biztonsági zóna a védelem által a zóna jogosultságszint-emelése biztonsági szolgáltatás által biztosított kiegészítő biztonsági réteg nélkül fog futni. Ha a legördülő listában a kérdés elemre kattint, egy figyelmeztetés jelenik meg a felhasználó számára, aki potenciálisan kockázatos navigálást végez. Ha letiltja ezt a házirend-beállítást, akkor a rendszer valószínűleg ártalmas navigálást végez. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a valószínűleg ártalmas navigálást. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer – korlátozott zóna – automatikus Rákérdezés a fájlok letöltésére**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználókat a nem felhasználó által kezdeményezett fájlok letöltésére Ettől a beállítástól függetlenül a felhasználók a fájl letöltése párbeszédpaneleket kapják meg a felhasználó által kezdeményezett letöltésekhez. Ha engedélyezi ezt a beállítást, a felhasználók egy fájl letöltése párbeszédpanelt kapnak az automatikus letöltési kísérletekhez. Ha letiltja vagy nem konfigurálja ezt a beállítást, a nem felhasználó által kezdeményezett fájlletöltés le van tiltva, és a felhasználók az értesítési sávot a fájl letöltése párbeszédpanel helyett láthatják. A felhasználók ezután rákattintanak az értesítési sávra a fájl letöltésének megadásához.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Alapértelmezett**: Letiltva
  
- **Internet Explorer Internet Zone .NET-keretrendszerre vonatkozó függő összetevők**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-ban nem aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy aláíratlan felügyelt összetevőket kíván-e végrehajtani. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláíratlan felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer internetes zónája csak a jóváhagyott tartományok TDC ActiveX-vezérlők használatát engedélyezi**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználó futtathat-e TDC ActiveX-vezérlőt a webhelyeken. Ha engedélyezi ezt a házirend-beállítást, a TDC ActiveX-vezérlő nem fog futni a zónában lévő webhelyekről. Ha letiltja ezt a házirend-beállítást, a TDC aktív X vezérlő az ebben a zónában lévő összes helyről futni fog.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer korlátozott zónájának parancsfájlja kezdeményezte a Windowst**  
  Ezzel a házirend-beállítással felügyelheti a parancsfájl által kezdeményezett előugró ablakokat és windowsokat, amelyek tartalmazzák a címet és az állapotjelző sávokat. Ha engedélyezi ezt a házirend-beállítást, a Windows-korlátozások biztonsága nem lesz érvényes ebben a zónában. A biztonsági zóna a szolgáltatás által biztosított hozzáadott biztonsági réteg nélkül fut. Ha letiltja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer internetes zónája helyi elérési utat tartalmaz a fájlok kiszolgálóra való feltöltésekor**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer mikor küldje el a helyi elérési utat, amikor a felhasználó HTML-űrlapon keresztül tölt fel fájlokat. Ha a rendszer elküldje a helyi elérési utat, előfordulhat, hogy a kiszolgáló véletlenül nem tárt fel adatokat. Előfordulhat például, hogy a felhasználó asztaláról eljuttatott fájlok tartalmazzák a felhasználónevet az elérési út részeként. Ha engedélyezi ezt a házirend-beállítást, a rendszer az elérési út adatait akkor továbbítja, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha letiltja ezt a házirend-beállítást, a rendszer eltávolítja az elérésiút-információkat, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a rendszer elküldje-e az elérési utat, amikor feltölt egy fájlt egy HTML-űrlapon keresztül. Alapértelmezés szerint a rendszer az elérésiút-információkat elküldi.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer fokozottan védett módban tiltja le a folyamatokat**  
  Ez a házirend-beállítás határozza meg, hogy az Internet Explorer 11 a 64 bites folyamatokat (nagyobb biztonság esetén) vagy 32 bites folyamatokat (a nagyobb kompatibilitás érdekében) használja-e a Windows rendszerű, 64 bites verzióin a fokozottan védett módban. Fontos! Előfordulhat, hogy néhány ActiveX-vezérlő és-eszköztár nem érhető el, ha 64 bites folyamatokat használ. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer 11 64 bites Tab-folyamatokat fog használni, amikor a Windows 64 bites verzióiban fokozottan védett módban fut. Ha letiltja ezt a házirend-beállítást, az Internet Explorer 11 32 bites Tab-folyamatokat fog használni, amikor a Windows 64 bites verzióiban fokozottan védett módban fut. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók az Internet Explorer beállításaival be-vagy kikapcsolhatják ezt a funkciót. Ez a funkció alapértelmezés szerint ki van kapcsolva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer – tanúsítvány-hibák figyelmen kívül hagyása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó figyelmen kívül hagyja a böngészést megszakító SSL/Transport Layer Security (SSL/TLS) tanúsítványokat (például a "lejárt", a "visszavont" vagy a "név eltérése" hibákat) az Internet Explorerben. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem folytathatja a böngészést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó dönthet úgy, hogy figyelmen kívül hagyja a tanúsítvány hibáit, és folytatja a böngészést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Alapértelmezett**: Letiltva 
  
- **Internet Explorer Internet Zone XAML-fájlok betöltése**  
  Ezzel a házirend-beállítással kezelheti Extensible Application Markup Language-(XAML-) fájlok betöltését. A XAML egy XML-alapú deklaratív jelölési nyelv, amely gazdag felhasználói felületek és grafikák létrehozására szolgál, amelyek kihasználják a Windows megjelenítési alaprendszer. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a XAML-fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha a legördülő lista megadását kéri, a rendszer a felhasználótól kéri a XAML-fájlok betöltését. Ha letiltja ezt a házirend-beállítást, a XAML-fájlok nem töltődnek be az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó eldöntheti, hogy XAML-fájlokat kíván-e betölteni az Internet Explorerben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Alapértelmezett**: Letiltás 
  
- **Internet Explorer Internet Zone automatikus Rákérdezés a fájlok letöltésére**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználókat a nem felhasználó által kezdeményezett fájlok letöltésére Ettől a beállítástól függetlenül a felhasználók a fájl letöltése párbeszédpaneleket kapják meg a felhasználó által kezdeményezett letöltésekhez. Ha engedélyezi ezt a beállítást, a felhasználók egy fájl letöltése párbeszédpanelt kapnak az automatikus letöltési kísérletekhez. Ha letiltja vagy nem konfigurálja ezt a beállítást, a nem felhasználó által kezdeményezett fájlletöltés le van tiltva, és a felhasználók az értesítési sávot a fájl letöltése párbeszédpanel helyett láthatják. A felhasználók ezután rákattintanak az értesítési sávra a fájl letöltésének megadásához.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer – korlátozott zóna biztonsági figyelmeztetése potenciálisan nem biztonságos fájlokhoz**  
  Ezzel a házirend-beállítással szabályozható, hogy a "fájl-biztonsági figyelmeztetés megnyitása" üzenet jelenik-e meg, amikor a felhasználó megpróbál megnyitni egy végrehajtható fájlt vagy más potenciálisan nem biztonságos fájlt (például egy intranetes fájlmegosztást a fájlkezelő használatával). Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a rendszer biztonsági figyelmeztetés nélkül nyitja meg a fájlokat. Ha a legördülő lista megadását kéri, a rendszer biztonsági figyelmeztetést jelenít meg a fájlok megnyitása előtt. Ha letiltja ezt a házirend-beállítást, akkor ezek a fájlok nem nyílnak meg. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a számítógép hogyan kezelje ezeket a fájlokat. Alapértelmezés szerint ezek a fájlok le vannak tiltva a korlátozott zónában, amely engedélyezve van az intranetes és a helyi számítógép zónában, és az interneten és a megbízható zónákban való rákérdezésre van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna helyközi parancsfájl-szűrő**  
  Ez a házirend azt szabályozza, hogy a helyek közötti parancsfájlok (XSS) szűrő felismeri-e és megakadályozza-e a helyek közötti parancsfájl-befecskendezést a zónában lévő webhelyeken. Ha engedélyezi ezt a házirend-beállítást, az XSS-szűrő be van kapcsolva a zónában található helyekhez, és az XSS-szűrő megkísérli blokkolni a helyek közötti parancsfájlok befecskendezését. Ha letiltja ezt a házirend-beállítást, az XSS-szűrő ki van kapcsolva az ebben a zónában lévő helyeknél, és az Internet Explorer engedélyezi a helyek közötti parancsfájlok befecskendezését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer tartalék SSL3**  
  Ezzel a házirend-beállítással letilthat egy nem biztonságos tartalékot az SSL 3,0-re. Ha ez a szabályzat engedélyezve van, az Internet Explorer az SSL 3,0-es vagy újabb verziójának használatával próbál csatlakozni a webhelyekhez, ha a TLS 1,0 vagy nagyobb hibát jelez. Azt javasoljuk, hogy ne engedélyezze a nem biztonságos tartalékot, hogy megakadályozza a személyes támadásokat. Ez a házirend nem befolyásolja, hogy mely biztonsági protokollok engedélyezettek. Ha letiltja ezt a házirendet, a rendszer az alapértelmezett értékeket használja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Alapértelmezett**: Nincsenek helyek  

- **Az Internet Explorer titkosításának támogatása**  
  Ezzel a házirend-beállítással kikapcsolhatja a Transport Layer Security (TLS) 1,0, TLS 1,1, TLS 1,2, SSL (SSL) 2,0 vagy SSL 3,0 támogatását a böngészőben. A TLS és az SSL olyan protokollok, amelyek segítenek a böngésző és a célkiszolgáló közötti kommunikáció védelmében. Amikor a böngésző megpróbál beállítani egy védett kommunikációt a célkiszolgálón, a böngésző és a kiszolgáló egyezteti a használandó protokollt és verziót. A böngésző és a kiszolgáló megpróbálta egyeztetni egymással a támogatott protokollok és verziók listáját, és kiválasztja a leginkább előnyben részesített egyezést. Ha engedélyezi ezt a házirend-beállítást, a böngésző egyezteti vagy nem egyeztet egy titkosítási alagutat a legördülő listából kiválasztott titkosítási módszerek használatával. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja a böngésző által támogatott titkosítási módszert.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Alapértelmezett**: 2 elem:  TLS v 1.1 és TLS 2.0  
  *Válassza a lefelé mutató nyilat a beállításhoz választható beállítások megjelenítéséhez.*
  
- **Az Internet Explorer zárolta az Internet zóna intelligens képernyőjét**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer korlátozott zóna alkalmazások és fájlok elindítása iFrame-ben**  
  Ezzel a házirend-beállítással felügyelheti, hogy az alkalmazások futtathatók-e, és hogy a fájlok letölthetők-e a zónában lévő lapok HTML-ben lévő IFRAME-hivatkozásból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatják az alkalmazásokat, és fájlokat tölthetnek le a zóna oldalain lévő IFRAME ELEMEKből. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy szeretné-e futtatni az alkalmazásokat, és letölti a fájlokat a zóna lapjain lévő IFRAME elemek közül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak alkalmazásokat futtatni és fájlokat letölteni a zónában lévő lapok IFRAME ELEMEIből. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a felhasználók futtassák az alkalmazásokat, és fájlokat töltsenek le a zónában lévő lapok IFRAME ELEMEIből.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Alapértelmezett**: Letiltás 
  
- **Internet Explorer – a nem gyakori fájlokra vonatkozó figyelmeztetések mellőzése az intelligens képernyőn**  
  Ezzel a házirend-beállítással adható meg, hogy a felhasználó megkerülhet-e a SmartScreen szűrőből származó figyelmeztetéseket. A SmartScreen szűrő figyelmezteti a felhasználót olyan végrehajtható fájlokra, amelyeket az Internet Explorer felhasználói általában nem töltenek le az internetről. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő figyelmeztetései letiltják a felhasználót. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó megkerülheti a SmartScreen szűrő figyelmeztetéseit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet zóna előugró ablak blokkolása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a nemkívánatos előugró ablakok megjelenjenek-e. Az előugró ablak akkor nyílik meg, amikor a végfelhasználó egy hivatkozásra kattint. Ha engedélyezi ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg. Ha letiltja ezt a házirend-beállítást, a rendszer nem akadályozza meg az előugró ablakok megjelenését. Ha nem konfigurálja ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer az konzisztens MIME-kezelést dolgozza fel**  
  Az Internet Explorer dinamikus bináris viselkedést tartalmaz: olyan összetevők, amelyek adott funkciókat biztosítanak azon HTML-elemek számára, amelyekhez csatolva vannak. Ezzel a házirend-beállítással szabályozható, hogy a bináris viselkedés biztonsági korlátozásának beállítása meggátolható vagy engedélyezve van-e. Ha engedélyezi ezt a házirend-beállítást, a rendszer a Fájlkezelőben és az Internet Explorer folyamataiban nem akadályozza meg a bináris viselkedést. Ha letiltja ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer folyamatainak bináris viselkedése is engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a bináris viselkedést a fájlkezelő és az Internet Explorer folyamataiban.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer – korlátozott zóna – Java-engedélyek**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Alapértelmezett**: A Java letiltása  
    
  
- **Az Internet Explorer aktív X vezérlői védett módban**  
  Ezzel a házirend-beállítással megakadályozható, hogy az ActiveX-vezérlők védett módban fussanak, ha engedélyezve van a fokozottan védett mód. Ha a felhasználó olyan ActiveX-vezérlővel rendelkezik, amely nem kompatibilis a fokozottan védett móddal, és egy webhely megkísérli betölteni a vezérlőt, az Internet Explorer értesíti a felhasználót, és lehetővé teszi a webhely normál védelemmel ellátott módban történő futtatását. Ezzel a házirend-beállítással a rendszer letiltja ezt az értesítést, és az összes webhelyet fokozottan védett módban futtatja. A továbbfejlesztett védett mód további védelmet biztosít a rosszindulatú webhelyekkel szemben, ha 64 bites folyamatokat használ a Windows 64-bites verzióiban. A Windows 8 rendszerű számítógépek esetében a fokozottan védett mód is korlátozza az Internet Explorer által a beállításjegyzékből és a fájlrendszerből beolvasott helyeket. Ha a bővített védett mód engedélyezve van, és a felhasználó egy olyan webhelyre érkezik, amely nem kompatibilis a fokozottan védett móddal, az Internet Explorer értesíti a felhasználót, és lehetővé teszi a fokozottan védett üzemmód letiltását a következőre: adott webhelyre. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem teszi lehetővé a felhasználó számára a fokozottan védett üzemmód letiltását. Az összes védett mód webhelye fokozottan védett módban fog futni. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer értesíti a felhasználókat, és lehetőséget biztosít a nem kompatibilis ActiveX-vezérlőkkel rendelkező webhelyek normál védett módban való futtatására.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának XAML-fájljainak betöltése**  
  Ezzel a házirend-beállítással kezelheti Extensible Application Markup Language-(XAML-) fájlok betöltését. A XAML egy XML-alapú deklaratív jelölési nyelv, amely gazdag felhasználói felületek és grafikák létrehozására szolgál, amelyek kihasználják a Windows megjelenítési alaprendszer. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a XAML-fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha a legördülő lista megadását kéri, a rendszer a felhasználótól kéri a XAML-fájlok betöltését. Ha letiltja ezt a házirend-beállítást, a XAML-fájlok nem töltődnek be az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó eldöntheti, hogy XAML-fájlokat kíván-e betölteni az Internet Explorerben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer parancsfájlokkal ellátható biztonsági korlátozásokat dolgoz fel**  
  Az Internet Explorer lehetővé teszi a parancsfájlok számára a különböző típusú ablakok programozott megnyitását, átméretezését és áthelyezését. Az ablak korlátozásai biztonsági funkció korlátozza a felugró ablakokat, és letiltja azokat a Windows-verziókat, amelyekben a cím és az állapotjelző sávok nem láthatók a felhasználó számára, vagy eltorzítják a többi Windows-címet és állapotjelző sávot. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlba állított Windows minden folyamat esetében korlátozott. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a megírt Windows nem korlátozott.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Alapértelmezett**: Enabled   
  
- **Internet Explorer – korlátozott zóna – aktív X vezérlők és beépülő modulok futtatása**  
  Ezzel a házirend-beállítással felügyelheti, hogy az ActiveX-vezérlők és a beépülő modulok futhatnak-e a megadott zónán lévő lapokon. Ha engedélyezi ezt a házirend-beállítást, a vezérlők és a beépülő modulok felhasználói beavatkozás nélkül is futtathatók. Ha a legördülő listában a kérdés lehetőséget választotta, a rendszer felkéri a felhasználókat arra, hogy engedélyezzék a vezérlők vagy a beépülő modul futtatását. Ha letiltja ezt a házirend-beállítást, a vezérlők és beépülő modulok nem futnak. Ha nem konfigurálja ezt a házirend-beállítást, a vezérlők és beépülő modulok nem futnak.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónájának parancsfájljában aktív X vezérlők biztonságosként vannak megjelölve parancsfájlok futtatásához**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy biztonságosként megjelölt ActiveX-vezérlő képes-e a parancsfájlok kezelésére. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok interakciója automatikusan, felhasználói beavatkozás nélkül is megtörténhet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a parancsfájlok interakcióját. Ha letiltja ezt a házirend-beállítást, a parancsfájlok interakciója nem történik meg. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl-interakció megakadályozása nem történik meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónájának bejelentkezési beállításai**  
  Ezzel a házirend-beállítással kezelheti a bejelentkezési beállítások beállításait. Ha engedélyezi ezt a házirend-beállítást, a következő bejelentkezési beállítások közül választhat. 
  - *Névtelen* – Névtelen bejelentkezés használata a http-hitelesítés letiltásához és a vendég fiók csak a Common Internet File System (CIFS) protokollhoz való használatához. 
  - A felhasználók felhasználói azonosítóinak és jelszavának lekérdezéséhez kérje a Felhasználónév és a jelszó megadását. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. 
  - *Automatikus bejelentkezés csak az intranet zónában* – ezzel a beállítással lekérdezheti a felhasználókat a többi zónában lévő felhasználói azonosítók és jelszavak számára. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. 
  - *Automatikus bejelentkezés a jelenlegi felhasználónévvel és jelszóval*– ezzel a beállítással megpróbálhatja bejelentkezni a Windows NT kérdéses válasz (más néven NTLM-hitelesítés) használatával. Ha a kiszolgáló támogatja a Windows NT kérdéses választ, a bejelentkezés a felhasználó hálózati felhasználónevét és jelszavát használja a bejelentkezéshez. Ha a kiszolgáló nem támogatja a Windows NT kérdéses választ, a rendszer lekérdezi a felhasználót, hogy megadja a felhasználónevet és a jelszót. 

  Ha letiltja ezt a házirend-beállítást, a bejelentkezés *csak az intranet zónában automatikus bejelentkezésre*van beállítva. Ha nem konfigurálja ezt a házirend-beállítást, a bejelentkezés a Felhasználónév és a jelszó megadására van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Alapértelmezett**: Névtelen  
  
- **Az Internet Explorer megbízható zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer-kiszolgáló tanúsítvány-visszavonásának ellenőrzése**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer ellenőriznie fogja-e a kiszolgálók tanúsítványainak visszavonási állapotát. A rendszer visszavonja a tanúsítványokat, amikor azok sérülnek, vagy már nem érvényesek, és ez a beállítás védi a felhasználókat abban, hogy bizalmas adatokkal elküldjenek egy olyan webhelyre, amely hamis vagy nem biztonságos lehet. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer megtekinti, hogy a kiszolgálói tanúsítványok visszavonva lettek-e. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a kiszolgálói tanúsítványokat, hogy azok visszavonták-e őket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a kiszolgálói tanúsítványokat, hogy azok visszavonták-e őket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer Internet Zone less privilegizált helyek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a webhelyek a kevésbé privilegizált zónákból, például a tiltott helyekről is bejelentkezhetnek-e a zónába. Ha engedélyezi ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát. A biztonsági zóna a védelem által a zóna jogosultságszint-emelése biztonsági szolgáltatás által biztosított kiegészítő biztonsági réteg nélkül fog futni. Ha a legördülő listában a kérdés elemre kattint, egy figyelmeztetés jelenik meg a felhasználó számára, aki potenciálisan kockázatos navigálást végez. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza a valószínűleg ártalmas navigálást. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható. Ha nem konfigurálja ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer – korlátozott zóna fájljának letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a fájlok letöltése engedélyezett-e a zónából. Ezt a beállítást az oldal zónája határozza meg, amely a letöltést okozza, nem pedig azt a zónát, amelyről a fájlt leszállítják. Ha engedélyezi ezt a házirend-beállítást, a fájlok a zónából tölthetők le. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza a fájlok letöltését a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a fájlok letöltését a zónából.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna – az Authenticode-aláírással aláírt .NET-keretrendszerre támaszkodó összetevők futtatása**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-val aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláírt felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy végrehajtja-e az aláírt felügyelt összetevőket. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer megakadályozza az aktív X vezérlők felhasználónkénti telepítését**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy az ActiveX-vezérlők telepítése felhasználónkénti alapon történjen. Ha engedélyezi ezt a házirend-beállítást, az ActiveX-vezérlőket nem lehet felhasználónkénti alapon telepíteni. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor az ActiveX-vezérlők felhasználónkénti alapon telepíthetők.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megakadályozza az intelligens képernyő-szűrő kezelését**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó kezelje a SmartScreen szűrőt, amely figyelmezteti a felhasználót, ha a meglátogatott webhelyről ismert, hogy csalárd kísérletet tesz személyes adatok gyűjtésére az "adathalászat" vagy a kártevő szoftverek üzemeltetése során. Ha engedélyezi ezt a házirend-beállítást, a rendszer nem kéri a felhasználót a SmartScreen szűrő bekapcsolására. A szűrők engedélyezése listán nem szereplő összes webhely címét a rendszer automatikusan elküldi a Microsoftnak a felhasználó értesítése nélkül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer felszólítja a felhasználót, hogy döntse el, hogy bekapcsolja-e a SmartScreen szűrőt az első futtatási élményben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer feldolgozza a MIME-elemzések biztonsági funkcióját**  
  Ezzel a házirend-beállítással megadható, hogy az Internet Explorer MIME-elemzése megakadályozza-e egy típusú fájl egy veszélyesebb fájltípusra való előléptetését. Ha engedélyezi ezt a házirend-beállítást, a MIME-elemzés soha nem fogja előléptetni az egyik típusú fájlt veszélyesebb fájltípusra. Ha letiltja ezt a házirend-beállítást, az Internet Explorer folyamatai lehetővé teszik a MIME-elemzések számára, hogy egy adott típusú fájlt egy veszélyesebb fájltípusra ösztönözzék. Ha nem konfigurálja ezt a házirend-beállítást, a MIME-elemzés soha nem előlépteti az egyik típusú fájlt veszélyesebb fájltípusra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer – korlátozott zóna – aláírt aktív X vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók letölthetik-e az aláírt ActiveX-vezérlőket a zóna egy oldaláról. Ha engedélyezi ezt a házirendet, a felhasználók felhasználói beavatkozás nélkül tölthetik le az aláírt vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a nem megbízható közzétevők által aláírt vezérlőket szeretné-e letölteni. A megbízható közzétevők által aláírt kód csendesen le van töltve. Ha letiltja a házirend-beállítást, az aláírt vezérlők nem tölthetők le. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy letöltötte-e a nem megbízható közzétevők által aláírt vezérlőket. A megbízható közzétevők által aláírt kód csendesen le van töltve.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer automatikus kiegészítése**  
  Ez az automatikus kiegészítési funkció megjegyezheti és javasolhatja a felhasználóneveket és a jelszavakat az űrlapokon. Ha engedélyezi ezt a beállítást, a felhasználó nem változtathatja meg a "felhasználónevek és jelszavak az űrlapokon" vagy "a jelszavak mentése" üzenetet. Az űrlapokon lévő felhasználónevek és jelszavak automatikus teljes funkciója be van kapcsolva. El kell döntenie, hogy kiválasztja-e a "jelszó mentése" üzenetet. Ha letiltja ezt a beállítást, a felhasználó nem változtathatja meg a "felhasználónevek és jelszavak az űrlapokon" vagy a "kérdés a jelszavak mentéséhez" lehetőséget. Az űrlapokon lévő felhasználónevek és jelszavak automatikus teljes funkciója ki van kapcsolva. A felhasználó nem dönthet úgy is, hogy kéri a jelszavak mentését. Ha nem konfigurálja ezt a beállítást, a felhasználónak lehetősége van az automatikus kiegészítés bekapcsolására az űrlapokon a Felhasználónév és a jelszó megadására, és a jelszavak mentésére is lehetőség van. A beállítás megjelenítéséhez a felhasználók megnyitják az Internetbeállítások párbeszédpanelt, kattintson a tartalom fülre, és kattintson a beállítások gombra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zónája a VBscript futtatásának engedélyezése**  
  Ezzel a házirend-beállítással eldöntheti, hogy a VBScript futtatható-e az adott Internet Explorer-zónákban lévő lapokon. A lehetőségek a következők: 
  - *Engedélyezés* – a VBScript az adott zónákban lévő lapokon, interakció nélkül fut. 
  - *Kérés* – az alkalmazottaknak meg kell adni, hogy engedélyezni kell-e a VBScript futtatását a zónában. 
  - A *disable* -VBScript nem fut a zónában. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a VBScript a megadott zónán belüli interakció nélkül fut.    

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónája csak jóváhagyott tartományokat engedélyez a TDC aktív X-vezérlők használatához**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználó futtathat-e TDC ActiveX-vezérlőt a webhelyeken. Ha engedélyezi ezt a házirend-beállítást, a TDC ActiveX-vezérlő nem fog futni a zónában lévő webhelyekről. Ha letiltja ezt a házirend-beállítást, a TDC aktív X vezérlő az ebben a zónában lévő összes helyről futni fog.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megbízható zónája nem futtat antimalware-t az aktív X vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer helyi számítógép-zónájának Java-engedélyei**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély közepes biztonsági értékre van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Alapértelmezett**: A Java letiltása 
  
- **Az Internet Explorer intranetes zónája nem futtat antimalware-t az aktív X vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Alapértelmezett**: Letiltva  

- **Az Internet Explorer korlátozott zónájának Szkriptletek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó futtathat-e Szkriptletek. Ha engedélyezi ezt a házirend-beállítást, akkor a felhasználó futtathat Szkriptletek. Ha letiltja ezt a házirend-beállítást, a felhasználó nem tudja futtatni a Szkriptletek. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer az értesítési sávot dolgozza fel**  
  Ezzel a házirend-beállítással felügyelheti, hogy az értesítési sáv megjelenjen-e az Internet Explorer folyamataihoz, ha a fájl-vagy programkódok telepítése korlátozott. Alapértelmezés szerint az értesítési sáv az Internet Explorer folyamataihoz jelenik meg. Ha engedélyezi ezt a házirend-beállítást, megjelenik az értesítési sáv az Internet Explorer folyamataihoz. Ha letiltja ezt a házirend-beállítást, az értesítési sáv nem jelenik meg az Internet Explorer folyamataihoz. Ha nem konfigurálja ezt a házirend-beállítást, az értesítési sáv nem jelenik meg az Internet Explorer folyamataihoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer Internet Zone – aláírt ActiveX-vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók letölthetik-e az aláírt ActiveX-vezérlőket a zóna egy oldaláról. Ha engedélyezi ezt a házirendet, a felhasználók felhasználói beavatkozás nélkül tölthetik le az aláírt vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a nem megbízható közzétevők által aláírt vezérlőket szeretné-e letölteni. A megbízható közzétevők által aláírt kód csendesen le van töltve. Ha letiltja a házirend-beállítást, az aláírt vezérlők nem tölthetők le. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy letöltötte-e a nem megbízható közzétevők által aláírt vezérlőket. A megbízható közzétevők által aláírt kód csendesen le van töltve.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónájának intelligens képernyője**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer az elavult aktív X vezérlőknél az idő futtatása gombjának eltávolítása**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy a felhasználók meglássák a "Futtatás ebben az időben" gombot, és az Internet Explorerben adott elavult ActiveX-vezérlőket futtasson. Ha engedélyezi ezt a házirend-beállítást, a felhasználók nem láthatják a figyelmeztető üzenet "Futtatás ideje" gombját, amely akkor jelenik meg, ha az Internet Explorer elavult ActiveX-vezérlőt blokkol. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználók az elavult ActiveX-vezérlőt blokkoló figyelmeztető üzenetben láthatják a "Futtatás ideje" gombot. Ha erre a gombra kattint, a felhasználó egyszer futtathatja az elavult ActiveX-vezérlőt. További információ: "elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer Internet Zone alkalmazások és fájlok elindítása iframe-ben**  
  Ezzel a házirend-beállítással felügyelheti, hogy az alkalmazások futtathatók-e, és hogy a fájlok letölthetők-e a zónában lévő lapok HTML-ben lévő IFRAME-hivatkozásból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatják az alkalmazásokat, és fájlokat tölthetnek le a zóna oldalain lévő IFRAME ELEMEKből. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy szeretné-e futtatni az alkalmazásokat, és letölti a fájlokat a zóna lapjain lévő IFRAME elemek közül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak alkalmazásokat futtatni és fájlokat letölteni a zónában lévő lapok IFRAME ELEMEIből. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy futtatják-e az alkalmazásokat, és fájlokat töltenek le a zóna lapjain lévő IFRAME elemek közül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer korlátozott zónája különböző tartományokban navigáljon a Windows és a keretek között**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet Zone – intelligens képernyő**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer zárolta a megbízható zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Alapértelmezett**: A Java letiltása 
  
- **Internet Explorer-ellenőrzési aláírások a letöltött programokban**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer ellenőrizze-e a digitális aláírásokat (amely azonosítja az aláírt szoftverek közzétevőjét, és ellenőrzi, hogy nem módosította vagy módosították-e) a felhasználó számítógépeken a végrehajtható programok letöltése előtt. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer megtekinti a végrehajtható programok digitális aláírásait, és megjeleníti azok identitását, mielőtt letölti őket a felhasználói számítógépekre. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a végrehajtható programok digitális aláírásait, vagy a felhasználói számítógépekre való letöltés előtt megjeleníti az identitását. Ha nem konfigurálja ezt a házirendet, az Internet Explorer nem fogja megtekinteni a végrehajtható programok digitális aláírásait, vagy a felhasználói számítógépekre való letöltés előtt megjeleníti az identitását.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónáinak parancsfájlkezelése webböngésző-vezérlőkkel**  
  Ezzel a házirend-beállítással megadható, hogy egy oldal képes-e a beágyazott WebBrowser vezérlők futtatására parancsfájl használatával. Ha engedélyezi ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés engedélyezett. Ha letiltja ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés nem engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a WebBrowser vezérlőhöz tartozó parancsfájlok elérését. Alapértelmezés szerint a WebBrowser vezérlőhöz való parancsfájl-hozzáférés csak a helyi gépen és az intranet zónában engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának helyközi parancsfájl-szűrője**  
  Ez a házirend azt szabályozza, hogy a helyek közötti parancsfájlok (XSS) szűrő felismeri-e és megakadályozza-e a helyek közötti parancsfájl-befecskendezést a zónában lévő webhelyeken. Ha engedélyezi ezt a házirend-beállítást, az XSS-szűrő be van kapcsolva a zónában található helyekhez, és az XSS-szűrő megkísérli blokkolni a helyek közötti parancsfájlok befecskendezését. Ha letiltja ezt a házirend-beállítást, az XSS-szűrő ki van kapcsolva az ebben a zónában lévő helyeknél, és az Internet Explorer engedélyezi a helyek közötti parancsfájlok befecskendezését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónájának bináris és parancsfájl-viselkedései**  
  Ezzel a házirend-beállítással kezelheti a dinamikus bináris és parancsfájl-viselkedést: olyan összetevőket, amelyek olyan HTML-elemek speciális funkcióit ágyazzák be, amelyekhez csatolva vannak. Ha engedélyezi ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés is elérhető. Ha a rendszergazda által jóváhagyott lehetőséget választja a legördülő listában, a rendszer csak a bináris viselkedések biztonsági korlátozási szabályzatában szereplő, a rendszergazda által jóváhagyott viselkedések területen felsorolt viselkedéseket jeleníti meg. Ha letiltja ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés nem érhető el, ha az alkalmazások egyéni biztonsági kezelőt implementáltak. Ha nem konfigurálja ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés nem érhető el, ha az alkalmazások egyéni biztonsági kezelőt implementáltak.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer biztonsági beállításainak bejelölése**  
  Ezzel a házirend-beállítással kikapcsolhatja a biztonsági beállítások ellenőrzése funkciót, amely ellenőrzi, hogy az Internet Explorer biztonsági beállításai meghatározzák-e, hogy a beállítások az Internet Explorert veszélyeztetik-e. Ha engedélyezi ezt a házirend-beállítást, a szolgáltatás ki van kapcsolva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a funkció be van kapcsolva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer Internet zóna biztonsági figyelmeztetése potenciálisan nem biztonságos fájlokhoz**  
  Ezzel a házirend-beállítással szabályozható, hogy a "fájl-biztonsági figyelmeztetés megnyitása" üzenet jelenik-e meg, amikor a felhasználó megpróbál megnyitni egy végrehajtható fájlt vagy más potenciálisan nem biztonságos fájlt (például egy intranetes fájlmegosztást a fájlkezelő használatával). Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a rendszer biztonsági figyelmeztetés nélkül nyitja meg a fájlokat. Ha a legördülő lista megadását kéri, a rendszer biztonsági figyelmeztetést jelenít meg a fájlok megnyitása előtt. Ha letiltja ezt a házirend-beállítást, akkor ezek a fájlok nem nyílnak meg. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a számítógép hogyan kezelje ezeket a fájlokat. Alapértelmezés szerint ezek a fájlok le vannak tiltva a korlátozott zónában, amely engedélyezve van az intranetes és a helyi számítógép zónában, és az interneten és a megbízható zónákban való rákérdezésre van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Alapértelmezett**: Kérdés  
  
- **Az Internet Explorer intranetes zónájának Java-engedélyei**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély közepes biztonsági értékre van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Alapértelmezett**: Magas biztonság 
  
- **Az Internet Explorer elavult aktív X vezérlőket blokkol**   
  Ez a házirend-beállítás határozza meg, hogy az Internet Explorer blokkolja-e az elavult ActiveX-vezérlőket. Az intranetes zónában soha nem blokkolja az elavult ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer leállítja az elavult ActiveX-vezérlők blokkolását. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer továbbra is blokkol bizonyos elavult ActiveX-vezérlőket. További információ: "elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer korlátozott zóna felugró ablakának blokkolása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a nemkívánatos előugró ablakok megjelenjenek-e. Az előugró ablak akkor nyílik meg, amikor a végfelhasználó egy hivatkozásra kattint. Ha engedélyezi ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg. Ha letiltja ezt a házirend-beállítást, a rendszer nem akadályozza meg az előugró ablakok megjelenését. Ha nem konfigurálja ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer az MK protokoll biztonsági korlátozását dolgozza fel**  
  Az MK protokoll biztonsági korlátozási házirendjének beállítása csökkenti a támadási felületet az MK protokoll megakadályozásával. Az MK protokollon tárolt erőforrások sikertelenek lesznek. Ha engedélyezi ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer nem fogja tudni letiltani az MK protokollt, és az MK protokollon tárolt erőforrások sikertelenek lesznek. Ha letiltja ezt a házirend-beállítást, az alkalmazások használhatják az MK protokoll API-ját. Az MK protokollon tárolt erőforrások a Fájlkezelőben és az Internet Explorer folyamataiban is működni fognak. Ha nem konfigurálja ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer nem fogja tudni letiltani az MK protokollt, és az MK protokollon tárolt erőforrások sikertelenek lesznek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megbízható zónájának Java-engedélyei**   
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély alacsony biztonsági értékre van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Alapértelmezett**: Magas biztonság  
  
- **Az Internet Explorer korlátozott zónákon keresztüli parancsfájlkezelése Java-kisalkalmazások esetén**  
  Ezzel a házirend-beállítással felügyelheti, hogy a kisalkalmazások elérhetők-e a zónán belüli parancsfájlok számára. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok felhasználói beavatkozás nélkül automatikusan hozzáférhetnek a kisalkalmazásokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a parancsfájlok elérését a kisalkalmazásokhoz. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem férnek hozzá a kisalkalmazásokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok nem férnek hozzá a kisalkalmazásokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer letiltotta a korlátozott zóna Java-engedélyeit**   
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Alapértelmezett**: A Java letiltása 
  
- **Az Internet Explorer internetes zónája csak a jóváhagyott tartományok számára engedélyezi az ActiveX-vezérlők használatát**   
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer a felhasználótól az ActiveX-vezérlőt telepítő webhelytől eltérő webhelyeken is fusson. Ha engedélyezi ezt a házirend-beállítást, a rendszer arra kéri a felhasználót, hogy az ActiveX-vezérlők futtathatók legyenek a zónában található webhelyekről. A felhasználó dönthet úgy, hogy engedélyezi, hogy a vezérlő az aktuális helyről vagy az összes helyről fusson. Ha letiltja ezt a házirend-beállítást, a felhasználó nem látja a helyhez tartozó ActiveX-parancssort, és az ActiveX-vezérlők a zóna összes webhelyéről futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer minden hálózati elérési utat tartalmaz**  
  Az Internet Explorer minden hálózati elérési utat tartalmaz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Alapértelmezett**: Letiltva 
  
- **Internet Explorer Internet zóna által védett üzemmód**  
  Ezzel a házirend-beállítással engedélyezheti a védett üzemmódot. A védett mód segít megvédeni az Internet Explorert a kihasznált biztonsági rések révén, ha csökkenti az Internet Explorer által a beállításjegyzékben és a fájlrendszerben írni kívánt helyeket. Ha engedélyezi ezt a házirend-beállítást, a védett mód be van kapcsolva. A felhasználó nem kapcsolhatja ki a védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a védett mód ki van kapcsolva. A felhasználó nem kapcsolhatja be a védett üzemmódot. Ha nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó be-vagy kikapcsolhatja a védett módot.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Alapértelmezett**: Engedélyezés 
  
- **Az Internet Explorer internetes zónájának inicializálása és a parancsfájlok aktív X vezérlők nem biztonságosakként vannak megjelölve**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer lezárta a korlátozott zóna intelligens képernyőjét**   
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer összeomlásának észlelése**  
  Ezzel a házirend-beállítással kezelheti a bővítmények felügyeletének összeomlás-észlelési funkcióját. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer összeomlása a Windows XP Professional Service Pack 1 és korábbi verziókban is megjelenik, nevezetesen a Windows hibajelentés meghívásához. A Windows hibajelentés összes házirend-beállítása továbbra is érvényben marad. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a beépülő modul felügyeletének összeomlás-észlelési funkciója működőképes.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet Zone Java-engedélyek**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély magas biztonságra van állítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Alapértelmezett**: A Java letiltása  
  
- **Internet Explorer – korlátozott zóna – aktív parancsfájlok**  
  Ezzel a házirend-beállítással felügyelheti, hogy a zóna oldalain lévő parancsfájl-kód fut-e. Ha engedélyezi ezt a házirend-beállítást, a rendszer automatikusan futtathatja a zónában lévő lapokon található parancsfájl kódját. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezzék-e a parancsfájlok futtatását a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a zóna lapjain lévő parancsfájl-kód fusson. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a zóna lapjain lévő parancsfájl-kód ne fusson.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna bejelentkezési beállításai**  
  Ezzel a házirend-beállítással kezelheti a bejelentkezési beállítások beállításait. Ha engedélyezi ezt a házirend-beállítást, a következő bejelentkezési beállítások közül választhat. Névtelen bejelentkezés a HTTP-hitelesítés letiltásához és a vendég fiók csak a Common Internet File System (CIFS) protokollhoz való használatához. Kérje meg a felhasználónevet és a jelszót a felhasználók felhasználói azonosítók és jelszavak lekérdezéséhez. A felhasználó lekérdezése után ezeket az értékeket csendesen használhatja a munkamenet hátralévő részében. Automatikus bejelentkezés csak intranet zónában felhasználói azonosítók és jelszavak más zónákban való lekérdezéséhez. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. Automatikus bejelentkezés a jelenlegi felhasználónévvel és jelszóval a Windows NT kérdéses válasz (más néven NTLM-hitelesítés) használatával történő bejelentkezéshez. Ha a kiszolgáló támogatja a Windows NT kérdéses választ, a bejelentkezés a felhasználó hálózati felhasználónevét és jelszavát használja a bejelentkezéshez. Ha a kiszolgáló nem támogatja a Windows NT kérdéses választ, a rendszer lekérdezi a felhasználót, hogy megadja a felhasználónevet és a jelszót. Ha letiltja ezt a házirend-beállítást, a bejelentkezés csak az intranetes zónában automatikus bejelentkezésre van beállítva. Ha nem konfigurálja ezt a házirend-beállítást, akkor a bejelentkezés csak az intranetes zónában automatikus bejelentkezésre van beállítva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Alapértelmezett**: Kérdés  
  
- **Az Internet Explorer korlátozott zónája lehetővé teszi a VBScript futtatását**   
  Ezzel a házirend-beállítással felügyelheti, hogy a VBScript futtatható-e az Internet Explorerben megadott zónán lévő lapokon. Ha a legördülő listában az Engedélyezés lehetőséget választotta, a VBScript felhasználói beavatkozás nélkül futtatható. Ha a legördülő listában a kérdés lehetőséget választotta, a felhasználóknak meg kell választaniuk, hogy engedélyezik-e a VBScript futtatását. Ha a legördülő listában a Letiltás lehetőséget választotta, a VBScript nem fut. Ha nem konfigurálja vagy letiltja ezt a házirend-beállítást, a VBScript megakadályozza a futtatását.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zónája különböző tartományokból származó tartalmat húzhat át a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer intranetes zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Alapértelmezett**: Letiltás 
  
- **Internet Explorer-Letöltés – készülékházak**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó betöltse a hírcsatornáról a felhasználó számítógépére. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem állíthatja be a hírcsatorna-szinkronizálási motort úgy, hogy a csatorna tulajdonságlapján keresztül letöltse a bekerítést. A fejlesztők nem változtathatják meg a letöltési beállítást a hírcsatorna API-kon keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a hírcsatorna-szinkronizálási motor letöltse a bekerítést a hírcsatorna tulajdonságlapján. A fejlesztő a hírcsatorna API-jai segítségével módosíthatja a letöltési beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának aláíratlan aktív X vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zónája a különböző tartományokból származó tartalmakat a Windowson belül húzza**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer folyamatai korlátozzák az aktív X-telepítést**   
  Ezzel a házirend-beállítással engedélyezheti, hogy a webböngésző vezérlőt futtató alkalmazások blokkolják az ActiveX-vezérlő telepítésének automatikus megadását. Ha engedélyezi ezt a házirend-beállítást, a webböngésző vezérlő letiltja az ActiveX-vezérlő telepítésének automatikus megadását minden folyamat esetében. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a webböngésző vezérlő nem blokkolja az ActiveX-vezérlő telepítésének automatikus megadását az összes folyamat esetében.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer Internet Zone Szkriptletek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó futtathat-e Szkriptletek. Ha engedélyezi ezt a házirend-beállítást, akkor a felhasználó futtathat Szkriptletek. Ha letiltja ezt a házirend-beállítást, a felhasználó nem tudja futtatni a Szkriptletek. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer – korlátozott zóna – fájlok húzása vagy másolása és beillesztése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók beilleszthetnek-e fájlokat, vagy másolhatnak és beilleszthetnek fájlokat a zónán belüli forrásokból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók áthelyezhetik a fájlokat, vagy automatikusan másolhatják és beilleszthetik a fájlokat a zónából. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat áthúzni vagy másolni. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak fájlokat húzni, vagy fájlokat másolni és beilleszteni a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat húzni vagy másolni.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer szoftver, ha az aláírás érvénytelen**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó telepíthet-e vagy futtathat-e szoftvert, például az ActiveX-vezérlőket és a fájlokat, még akkor is, ha az aláírás érvénytelen. Egy érvénytelen aláírás azt jelezheti, hogy valaki módosította a fájlt. Ha engedélyezi ezt a házirend-beállítást, a rendszer a felhasználókat az érvénytelen aláírással rendelkező fájlok telepítésére és futtatására kéri. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak és nem telepíthetnek érvénytelen aláírással rendelkező fájlokat. Ha nem konfigurálja ezt a házirendet, a felhasználók dönthetnek úgy, hogy érvénytelen aláírással futtatják vagy telepítik a fájlokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának másolása és beillesztése parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájlok végezhetnek-e vágólap-műveletet (például Kivágás, másolás és beillesztés) egy adott régióban. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a vágólapon végez-e műveleteket. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónája különböző tartományokból származó tartalmat húzhat át a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer-felhasználók helyek hozzáadása**  
  Megakadályozza, hogy a felhasználók a biztonsági zónákból származó helyeket adjanak hozzá vagy távolítanak el. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, a biztonsági zónák hely-felügyeleti beállításai le vannak tiltva. (A biztonsági zónák hely-felügyeleti beállításainak megtekintéséhez az Internetbeállítások párbeszédpanelen kattintson a Biztonság fülre, majd kattintson a helyek gombra.) Ha letiltja vagy nem konfigurálja ezt a házirendet, a felhasználók hozzáadhatnak webhelyeket a megbízható helyek és a Tiltott helyek zónából, és módosíthatják a helyi intranet zóna beállításait. Ez a szabályzat megakadályozza, hogy a felhasználók módosítsák a rendszergazda által létesített biztonsági zónák hely-felügyeleti beállításait. Megjegyezés: A "biztonsági oldal letiltása" házirend (a User konfigurációja \ felügyeleti sablonok \ Internet Explorer\Internet vezérlőpultján található), amely eltávolítja a biztonsági lapot a felületről, elsőbbséget élvez a szabályzattal szemben. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Továbbá tekintse meg a "biztonsági zónák: Csak a számítógép-beállítások házirend használata.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet zóna parancsfájl kezdeményezett Windows**  
  Ezzel a házirend-beállítással felügyelheti a parancsfájl által kezdeményezett előugró ablakokat és windowsokat, amelyek tartalmazzák a címet és az állapotjelző sávokat. Ha engedélyezi ezt a házirend-beállítást, a Windows-korlátozások biztonsága nem lesz érvényes ebben a zónában. A biztonsági zóna a szolgáltatás által biztosított hozzáadott biztonsági réteg nélkül fut. Ha letiltja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer biztonsági zónái csak a gép beállításait használják**  
  A biztonsági zóna információit alkalmazza ugyanazon számítógép minden felhasználója számára. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, a felhasználó által a biztonsági zónában végrehajtott módosítások a számítógép összes felhasználójára érvényesek lesznek. Ha letiltja vagy nem konfigurálja ezt a házirendet, akkor az azonos számítógép felhasználói a saját biztonsági zónákra vonatkozó beállításokat hozhatnak létre. Ezzel a házirenddel biztosíthatja, hogy a biztonsági zónák beállításai egységesen legyenek alkalmazva ugyanarra a számítógépre, és ne változzon a felhasználótól. Továbbá tekintse meg a "biztonsági zónák: ne engedélyezze a felhasználók számára szabályzatok módosítását" házirendet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer zárolta a helyi számítógép zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Alapértelmezett**: A Java letiltása 
  
- **Az Internet Explorer korlátozott zónája nem futtat antimalware-t az aktív X vezérlőkön**   
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának futtatása a .NET-keretrendszerre vonatkozó, Authenticode-val aláírt összetevőkkel**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-val aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláírt felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy végrehajtja-e az aláírt felügyelt összetevőket. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónáinak hozzáférése az adatforrásokhoz**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer hozzáférhet-e egy másik biztonsági zónából származó adatokhoz a Microsoft XML Parser (MSXML) vagy a ActiveX Data Objects (ADO) használatával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók betölthetnek egy olyan lapot a zónába, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a lap betöltését az MSXML vagy az ADO protokollt használó zónában a zóna egy másik helyéről származó adatok eléréséhez. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer internetes zónája nem futtat antimalware-t az ActiveX-vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet zóna másolás és beillesztés parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájlok végezhetnek-e vágólap-műveletet (például Kivágás, másolás és beillesztés) egy adott régióban. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a vágólapon végez-e műveleteket. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer az aktív X telepítő szolgáltatást használja**  
  Ezzel a házirend-beállítással megadhatja, hogy az ActiveX-vezérlők hogyan legyenek telepítve. Ha engedélyezi ezt a házirend-beállítást, a rendszer csak akkor telepíti az ActiveX-vezérlőket, ha az ActiveX-telepítő szolgáltatás megtalálható, és úgy van konfigurálva, hogy engedélyezze az ActiveX-vezérlők telepítését. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a normál telepítési folyamaton keresztül telepíti az ActiveX-vezérlőket, beleértve a felhasználónkénti vezérlőket is.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer feldolgozza a védelmet a zónák megemelésével**  
  Az Internet Explorer a megnyíló weblapokon korlátozásokat helyez el. A korlátozások a weblap (Internet, intranet, helyi számítógép zóna stb.) helyétől függenek. Például a helyi számítógépen lévő weblapok a legkevesebb biztonsági korlátozással rendelkeznek, és a helyi számítógép zónában találhatók, így a helyi számítógép biztonsági zónája elsődleges cél a rosszindulatú felhasználók számára. Ha engedélyezi ezt a házirend-beállítást, az összes zóna megemelhető minden folyamat esetében. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer vagy a folyamat listában felsorolt folyamatok nem kapnak ilyen védelmet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer Internet zóna aláíratlan ActiveX-vezérlők letöltése**   
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet Zone – különböző tartományokban navigáljon a Windows és a keretek között**   
  Ezzel a házirend-beállítással kezelheti a Windows és a keretek megnyitását, valamint az alkalmazások különböző tartományokon belüli elérését. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megnyithatják a Windowst és a képkockákat más tartományokból, és más tartományokból származó alkalmazásokat is elérhet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a Windows és a keretek számára más tartományokból származó alkalmazások elérését. Ha letiltja ezt a házirend-beállítást, a felhasználók nem megnyithatják a Windowst és a képkockákat a különböző tartományokból származó alkalmazások eléréséhez. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók megnyithatja a Windowst és a képkockákat más tartományokból, és más tartományokból is elérheti az alkalmazásokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna frissítései az állapotsoron parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy parancsfájl frissítheti-e a zónán belüli állapotjelző sávot. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok frissíthetik az állapotjelző sávot. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a parancsfájl nem jogosult az állapotsor frissítésére.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónája helyi elérési utat tartalmaz a fájlok kiszolgálóra való feltöltésekor**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer mikor küldje el a helyi elérési utat, amikor a felhasználó HTML-űrlapon keresztül tölt fel fájlokat. Ha a rendszer elküldje a helyi elérési utat, előfordulhat, hogy a kiszolgáló véletlenül nem tárt fel adatokat. Előfordulhat például, hogy a felhasználó asztaláról eljuttatott fájlok tartalmazzák a felhasználónevet az elérési út részeként. Ha engedélyezi ezt a házirend-beállítást, a rendszer az elérési út adatait akkor továbbítja, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha letiltja ezt a házirend-beállítást, a rendszer eltávolítja az elérésiút-információkat, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a rendszer elküldje-e az elérési utat, amikor HTML-űrlapon keresztül tölt fel fájlokat. Alapértelmezés szerint a rendszer az elérésiút-információkat elküldi.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer folyamatai korlátozzák a fájlok letöltését**   
  Ezzel a házirend-beállítással a webböngésző vezérlőt futtató alkalmazások letilthatják a felhasználók által kezdeményezett fájlok letöltésének automatikus megadását. Ha engedélyezi ezt a házirend-beállítást, a webböngésző vezérlő letiltja azon fájlok letöltésének automatikus megadását, amelyek nem minden folyamat esetében kezdeményezték a felhasználót. Ha letiltja ezt a házirend-beállítást, a webböngésző vezérlő nem fogja blokkolni az olyan fájlok letöltésének automatikus megadását, amelyek nem minden folyamat esetében kezdeményezték a felhasználót.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónája csak jóváhagyott tartományokat engedélyez az aktív X vezérlők használatához**   
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer a felhasználótól az ActiveX-vezérlőt telepítő webhelytől eltérő webhelyeken is fusson. Ha engedélyezi ezt a házirend-beállítást, a rendszer arra kéri a felhasználót, hogy az ActiveX-vezérlők futtathatók legyenek a zónában található webhelyekről. A felhasználó dönthet úgy, hogy engedélyezi, hogy a vezérlő az aktuális helyről vagy az összes helyről fusson. Ha letiltja ezt a házirend-beállítást, a felhasználó nem látja a helyhez tartozó ActiveX-parancssort, és az ActiveX-vezérlők a zóna összes webhelyéről futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer felhasználói házirendeket módosítanak**  
  Megakadályozza, hogy a felhasználók módosíthassák a biztonsági zónák beállításait. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, az Internetbeállítások párbeszédpanel Biztonság lapján az egyéni szint gomb és a biztonsági szint csúszkája le van tiltva. Ha letiltja vagy nem konfigurálja ezt a házirendet, a felhasználók módosíthatják a biztonsági zónák beállításait. Ez a szabályzat megakadályozza, hogy a felhasználók módosítsák a rendszergazda által létesített biztonsági zónák beállításait. Megjegyezés: A "biztonsági oldal letiltása" házirend (a User konfigurációja \ felügyeleti sablonok \ Internet Explorer\Internet vezérlőpultján található), amely eltávolítja az Internet Explorer biztonság lapját a Vezérlőpulton, elsőbbséget élvez Ez a szabályzat. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Továbbá tekintse meg a "biztonsági zónák: Csak a számítógép-beállítások házirend használata.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer korlátozott zóna által védett üzemmód**  
  Ezzel a házirend-beállítással engedélyezheti a védett üzemmódot. A védett mód segít megvédeni az Internet Explorert a kihasznált biztonsági rések révén, ha csökkenti az Internet Explorer által a beállításjegyzékben és a fájlrendszerben írni kívánt helyeket. Ha engedélyezi ezt a házirend-beállítást, a védett mód be van kapcsolva. A felhasználó nem kapcsolhatja ki a védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a védett mód ki van kapcsolva. A felhasználó nem kapcsolhatja be a védett üzemmódot. Ha nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó be-vagy kikapcsolhatja a védett módot.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer Internet Zone felhasználói adatmegőrzés**  
  Ezzel a házirend-beállítással kezelheti az információk megőrzését a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha a felhasználó egy megőrzött lapra tér vissza, akkor a lap állapota visszaállítható, ha a házirend-beállítás megfelelően van konfigurálva. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megőrzik az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók megőrizheti az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban vagy közvetlenül a lemezre mentett weblapon belül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zónájának parancsfájlkezelése a webböngésző vezérlőinek használatával**  
 
  Ezzel a házirend-beállítással megadható, hogy egy oldal képes-e a beágyazott WebBrowser vezérlők futtatására parancsfájl használatával. Ha engedélyezi ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés engedélyezett. Ha letiltja ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés nem engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a WebBrowser vezérlőhöz tartozó parancsfájlok elérését. Alapértelmezés szerint a WebBrowser vezérlőhöz való parancsfájl-hozzáférés csak a helyi gépen és az intranet zónában engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának felhasználói adatmegőrzése**  
  Ezzel a házirend-beállítással kezelheti az információk megőrzését a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha a felhasználó egy megőrzött lapra tér vissza, akkor a lap állapota visszaállítható, ha a házirend-beállítás megfelelően van konfigurálva. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megőrzik az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül egy, a lemezre mentett weblapon belül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer lezárta az intranet zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Alapértelmezett**: A Java letiltása  
  
- **Internet Explorer fokozottan védett üzemmód**  
  A továbbfejlesztett védett mód további védelmet biztosít a rosszindulatú webhelyekkel szemben, ha 64 bites folyamatokat használ a Windows 64-bites verzióiban. A Windows 8 rendszerű számítógépek esetében a fokozottan védett mód is korlátozza az Internet Explorer által a beállításjegyzékből és a fájlrendszerből beolvasott helyeket. Ha engedélyezi ezt a házirend-beállítást, a fokozottan védett mód be van kapcsolva. Minden olyan zóna, amelynél engedélyezve van a védett üzemmód, fokozottan védett módot fog használni. A felhasználók nem tudják letiltani a fokozottan védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a fokozottan védett üzemmód ki van kapcsolva. Minden olyan zóna, amelynél engedélyezve van a védett üzemmód, a Windows Vista Internet Explorer 7-es verziójában bemutatott védett mód verzióját fogja használni. Ha nem konfigurálja ezt a házirendet, a felhasználók az Internetbeállítások párbeszédpanel Speciális lapján bekapcsolhatják vagy kikapcsolhatják a fokozottan védett üzemmódot.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megkerülésének intelligens képernyő figyelmeztetései**  
  Ezzel a házirend-beállítással adható meg, hogy a felhasználó megkerülhet-e a SmartScreen szűrőből származó figyelmeztetéseket. A SmartScreen szűrő figyelmezteti a felhasználót olyan végrehajtható fájlokra, amelyeket az Internet Explorer felhasználói általában nem töltenek le az internetről. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő figyelmeztetései letiltják a felhasználót. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó megkerülheti a SmartScreen szűrő figyelmeztetéseit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer – korlátozott zóna – metaadatok frissítése**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy felhasználó böngészője átirányítható-e egy másik weblapra, ha a weblap szerzője a meta refresh (címke) beállítást használja a böngészők másik weblapra való átirányításához. Ha engedélyezi ezt a házirend-beállítást, egy olyan felhasználó böngészőjében, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, átirányítható egy másik weblapra. Ha letiltja ezt a házirend-beállítást, egy olyan felhasználó böngészője, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, nem lehet átirányítani egy másik weblapra. Ha nem konfigurálja ezt a házirend-beállítást, egy olyan felhasználó böngészője, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, nem irányítható át egy másik weblapra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Alapértelmezett**: Letiltva  
  
## <a name="local-policies-security-options"></a>Helyi házirendek biztonsági beállításai
További információ: [Policy CSP-LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) a Windows dokumentációjában. 

- **Nevesített csövek és megosztások névtelen elérésének korlátozása**  
  Ha engedélyezve van, ez a biztonsági beállítás korlátozza a megosztásokhoz és csövekhez való névtelen hozzáférést a következő beállításokra: (1) Nevesített csövek, amelyekhez névtelenül (2) hozzáférő, névtelenül elérhető megosztások érhetők el.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Alapértelmezett**: Igen  
  
- **Minimális munkamenet-biztonság az NTLM SSP-alapú kiszolgálók esetében**  
  Ez a biztonsági beállítás lehetővé teszi a kiszolgáló számára, hogy megkövetelje a 128 bites titkosítás és/vagy az NTLMv2 munkamenet-biztonság egyeztetését. Ezek az értékek a LAN Manager hitelesítési szintjének biztonsági beállításának értékétől függenek. Az alábbi lehetőségek állnak rendelkezésére: NTLMv2-munkamenet biztonságának megkövetelése: Ha az üzenet integritása nincs egyeztetve, a rendszer sikertelen lesz. 128 bites titkosítás megkövetelése. Ha az erős titkosítás (128 bites) nincs egyeztetve, a rendszer nem fogja tudni a kapcsolatokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Alapértelmezett**: NTLM v2 és 128 bites titkosítás megkövetelése  
  
- **A zárolási képernyő inaktivitásának percben, amíg a képernyőkímélő be nem kapcsol**  
  A Windows észleli a bejelentkezési munkamenetek tétlenségét, és ha a tétlenség ideje túllépi a tétlenségi korlátot, a rendszer futtatja a képernyőkímélőt és lezárja a munkamenetet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Alapértelmezett**: 15
  
- **Az ügyfél minden esetben digitálisan aláírja a kommunikációt** Ez a biztonsági beállítás határozza meg, hogy a tartományi tag által kezdeményezett összes biztonságos csatorna forgalmát alá kell-e írni vagy titkosítani kell-e. Ha egy számítógép tartományhoz csatlakozik, létrejön egy számítógépfiók. Ezt követően a rendszer indításakor a számítógépfiók jelszava használatával hozzon létre egy biztonságos csatornát a tartományához tartozó tartományvezérlővel. Ez a biztonságos csatorna olyan műveletek elvégzésére szolgál, mint például az NTLM-továbbítás hitelesítés, az LSA SID/Name lookup és még sok más. Ez a beállítás határozza meg, hogy a tartomány tagja által kezdeményezett összes biztonságos csatorna-forgalom megfelel-e a minimális biztonsági követelményeknek. Pontosabban meghatározza, hogy a tartományi tag által elindított összes biztonságos csatorna forgalmát alá kell-e írni vagy titkosítani kell-e. Ha ez a szabályzat engedélyezve van, akkor a biztonságos csatorna nem lesz létrehozva, kivéve, ha az összes biztonságos csatorna-forgalom aláírásával vagy titkosításával egyeztetve van. Ha ez a szabályzat le van tiltva, akkor a rendszer az összes biztonságos csatorna forgalom titkosítását és aláírását egyezteti a tartományvezérlővel, amely esetben az aláírás és a titkosítás szintje a tartományvezérlő verziójától és a következő két beállítástól függ. szabályzatok Tartományi tag: Biztonságos csatorna adatai digitális titkosítása (ha lehetséges) tartományi tag: Biztonságos csatornák digitális aláírása (ha lehetséges).  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Alapértelmezett**: Igen
  
- **Hitelesítési szint**  
  Ez a biztonsági beállítás határozza meg, hogy melyik kérdés-válasz hitelesítési protokollt használja a rendszer a hálózati bejelentkezésekhez. Ez a választás hatással van az ügyfelek által használt hitelesítési protokoll szintjére, a munkamenet-biztonság megtárgyalásának szintjére, valamint a kiszolgálók által a következőképpen elfogadott hitelesítés szintjére:  
  - *LM-és NTLM-válaszok küldése* – az ügyfelek az LM és az NTLM hitelesítést használják, és soha nem használják az NTLMv2 munkamenet-biztonságot; a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *LM és NTLM-NTLMv2 küldése, ha egyeztetve* van – az ügyfelek az LM és az NTLM hitelesítést használják, és ha a kiszolgáló támogatja az NTLMv2-munkamenetek biztonságát, a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLM-válasz küldése* – az ügyfelek csak az NTLM-hitelesítést használják, és ha a kiszolgáló támogatja azt, akkor az NTLMv2-munkamenetek biztonságát használják. a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLMv2-válaszok küldése* – az ügyfelek csak az NTLMv2-hitelesítést használják, és ha a kiszolgáló támogatja, az NTLMv2-munkamenetek biztonságát használják. a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLMv2-válasz küldése. LM* -azonosítók elutasítása – az ügyfelek csak az NTLMv2-hitelesítést használják, és ha a kiszolgáló támogatja azt, akkor a tartományvezérlők megtagadják az LM-t (csak NTLM és NTLMv2 hitelesítést fogadnak el). 
  - *Csak NTLMv2-válasz küldése. Az LM és az NTLM* -ügyfelek elutasítása csak az NTLMv2-hitelesítést használja, és ha a kiszolgáló támogatja azt, akkor a tartományvezérlők visszautasítja az LM és az NTLM protokollt (csak NTLMv2-hitelesítést fogad el).  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Alapértelmezett**: Csak NTLMv2-válasz küldése. Az LM és az NTLM elutasítása
  
- **Titkosítatlan jelszavak küldésének megakadályozása az ügyfelektől harmadik féltől származó SMB-kiszolgálókra**  
  Ha ez a biztonsági beállítás engedélyezve van, a kiszolgálói üzenetblokk (SMB) átirányító képes szöveges jelszavakat küldeni a nem Microsoft SMB-kiszolgálókra, amelyek nem támogatják a jelszó-titkosítást a hitelesítés során. A Titkosítatlan jelszavak küldése biztonsági kockázat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Alapértelmezett**: Igen
  
- **A kiszolgáló digitális aláírásával való kommunikáció megkövetelése mindig**  
  Ez a biztonsági beállítás határozza meg, hogy az SMB-ügyfél megkísérelje-e az SMB-csomagok aláírásának egyeztetését. A Server Message Block (SMB) protokoll a Microsoft fájl-és nyomtatómegosztás, valamint számos egyéb hálózati művelet, például a távoli Windows-felügyelet alapját képezi. Ha meg szeretné akadályozni, hogy az SMB-csomagokat az átvitel során módosító, nem a közepes támadásokkal szemben, az SMB protokoll támogatja az SMB-csomagok digitális aláírását. Ezzel a házirend-beállítással megadható, hogy az SMB-ügyfél-összetevő megkísérelje-e az SMB-csomagok aláírását az SMB-kiszolgálóhoz való csatlakozáskor. Ha ez a beállítás engedélyezve van, a Microsoft hálózati ügyfél arra kéri a kiszolgálót, hogy az SMB-csomagok aláírását végrehajtsa a munkamenet beállításakor. Ha a csomagaláírás engedélyezve van a kiszolgálón, a csomagaláírás egyeztetése megkezdődik. Ha a szabályzat le van tiltva, az SMB-ügyfél soha nem fogja egyeztetni az SMB-csomagok aláírását.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Alapértelmezett**: Igen
  
- **Rendszergazdai jogosultságszint-emelési kérések viselkedése**  
  Ezzel a házirend-beállítással szabályozható a rendszergazdák jogosultságszint-emelési kérésének viselkedése. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Jogosultságszint-emelés kérés nélkül* – lehetővé teszi az emelt szintű fiókok számára a jogosultságszint-emelést a beleegyezés vagy a hitelesítő adatok megkövetelése nélkül. Megjegyezés: Ezt a lehetőséget csak a legszigorúbban korlátozott környezetekben használhatja. 
  - *Hitelesítő adatok kérése a biztonságos asztalon* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer felszólítja a felhasználót a biztonságos asztalra, hogy adjon meg egy kiemelt felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ír be, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  - *Beleegyezés kérése a biztonságos asztalon* – ha egy művelethez jogosultságszint-emelésre van szükség, a felhasználónak meg kell adnia a biztonságos asztalt az engedélyezés vagy a Megtagadás lehetőség kiválasztásához. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  - *Hitelesítő adatok kérése* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer kéri a felhasználótól, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Beleegyezés kérése* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer a felhasználónak engedélyt vagy megtagadást kell választania. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik.  
  - A *nem Windows rendszerű bináris fájlok jóváhagyásának kérése* – ha egy nem Microsoft-alkalmazásra vonatkozó művelethez jogosultságszint-emelésre van szükség, a felhasználónak meg kell adnia a biztonságos asztalt az engedélyezés vagy a Megtagadás lehetőség kiválasztásához. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Alapértelmezett**: Beleegyezés kérése a biztonságos asztalon
  
- **Minimális munkamenet-biztonság az NTLM SSP-alapú ügyfelek számára**  
  Ez a biztonsági beállítás lehetővé teszi az ügyfél számára, hogy megkövetelje a 128 bites titkosítás és/vagy az NTLMv2 munkamenet-biztonság egyeztetését. Ezek az értékek a LAN Manager hitelesítési szintjének biztonsági beállításának értékétől függenek. Az alábbi lehetőségek állnak rendelkezésére:
  - *NTLMv2-munkamenet biztonságának* megkövetelése – a kapcsolat sikertelen lesz, ha az NTLMv2 protokoll nincs egyeztetve. 
  - *128 bites titkosítás* megkövetelése – ha erős titkosítás (128 bites) nincs egyeztetve, a rendszer nem fogja tudni a kapcsolatokat.
  - *NTLMv2 és 128 bites titkosítás*megkövetelése.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Alapértelmezett**: NTLM v2 128 titkosítás megkövetelése
  
- **Intelligens kártya eltávolításának viselkedése**  
  Ez a biztonsági beállítás határozza meg, hogy mi történjen, ha a bejelentkezett felhasználó intelligens kártyáját eltávolítja az intelligenskártya-olvasóból. Az alábbi lehetőségek állnak rendelkezésére:
  - *Nincs művelet*. 
  - *Munkaállomás zárolása* – a munkaállomás az intelligens kártya eltávolításakor zárolva van, így a felhasználók elhagyhatják a területeket, saját intelligens kártyájuk is megtarthatják őket, és továbbra is fenntartják a védett munkamenetet.
  - *Kijelentkezés kényszerítése* – a rendszer automatikusan kijelentkezik a felhasználót az intelligens kártya eltávolításakor.
  - *Távoli asztal kapcsolat bontása* – az intelligens kártya eltávolítása leválasztja a munkamenetet anélkül, hogy a felhasználót be kellene jelentkeznie. Ez lehetővé teszi a felhasználó számára, hogy beszúrja az intelligens kártyát, és később, vagy egy másik intelligenskártya-olvasóval felszerelt számítógépen folytassa a bejelentkezést anélkül, hogy újra be kellene jelentkeznie. Helyi munkamenet esetén ez a szabályzat pontosan úgy működik, mint a Munkaállomás zárolása.
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Alapértelmezett**: Munkaállomás zárolása
  
- **SAM-fiókok és-megosztások névtelen enumerálásának letiltása**  
  Ez a biztonsági beállítás határozza meg, hogy engedélyezi-e a SAM-fiókok és-megosztások névtelen enumerálását. A Windows lehetővé teszi a névtelen felhasználók számára bizonyos tevékenységek végrehajtását, például a tartományi fiókok és hálózati megosztások nevének számbavételét. Ez akkor lehet hasznos, ha egy rendszergazda olyan megbízható tartományban kíván hozzáférést biztosítani a felhasználóknak, amely nem tart fenn kölcsönös bizalmi kapcsolatot. Ha nem szeretné engedélyezni a SAM-fiókok és-megosztások névtelen enumerálását, állítsa ezt a házirendet *Igen*értékre.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Alapértelmezett**: Igen
  
- **Üres jelszóval rendelkező távoli bejelentkezés letiltása**  
  Ez a biztonsági beállítás határozza meg, hogy a jelszóval védett helyi fiókok a fizikai számítógép konzolján kívül más helyekről is bejelentkezhetnek-e. Ha engedélyezve van, a jelszóval védett helyi fiókoknak a számítógép billentyűzetén kell használniuk a bejelentkezést. 

  *Figyelmeztetés*: Azok a számítógépek, amelyek nem a fizikailag biztonságos helyen találhatók, mindig erős jelszavas házirendeket kényszerítenek az összes helyi felhasználói fiókhoz. Ellenkező esetben a számítógéphez való fizikai hozzáféréssel rendelkező bárki bejelentkezhet egy olyan felhasználói fiókkal, amely nem rendelkezik jelszóval. Ez különösen fontos a hordozható számítógépekhez. 

  Ha ezt a biztonsági házirendet a Mindenki csoportra alkalmazza, a Távoli asztali szolgáltatások nem tud bejelentkezni. Ez a beállítás nem érinti a tartományi fiókokat használó bejelentkezéseket. Távoli interaktív bejelentkezéseket használó alkalmazások esetén a beállítás megkerülése lehetséges.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Alapértelmezett**: Igen
  
- **Normál felhasználói jogosultságszint-emelési kérések viselkedése**  
  Ezzel a házirend-beállítással szabályozható az általános jogú felhasználók jogosultságszint-emelési kérésének viselkedése. 
  - *Jogosultságszint* -emelési kérések automatikus megtagadása – ha egy művelethez emelt szintű jogosultságra van szükség, egy konfigurálható hozzáférés-megtagadási hibaüzenet jelenik meg. Az asztali gépeket futtató vállalatok az általános jogú felhasználók ezt a beállítást választva csökkenthetik az ügyfélszolgálati hívásokat. 
  - *Hitelesítő adatok kérése a biztonságos asztalon* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a felhasználónak a biztonságos asztalon kell megadnia egy másik felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Hitelesítő adatok kérése* – ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer kéri a felhasználótól, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Alapértelmezett**: Jogosultságszint-emelési kérések automatikus megtagadása
  
- **Rendszergazdai engedélyezési mód szükséges a rendszergazdák számára**  
  Ezzel a házirend-beállítással szabályozható a számítógépen a felhasználói fiókok felügyelete (UAC) összes házirend-beállításának viselkedése. Ha módosítja ezt a házirend-beállítást, újra kell indítania a számítógépet. Az alábbi lehetőségek állnak rendelkezésére:   
  - *Nincs konfigurálva* – a rendszergazdai engedélyezési mód és az összes kapcsolódó UAC-házirend-beállítás le van tiltva. Megjegyezés: Ha a házirend-beállítás le van tiltva, a Security Center értesíti arról, hogy az operációs rendszer általános biztonsága csökkent. 
  - *Igen* – a rendszergazdai jóváhagyási mód engedélyezve van. Ezt a házirendet engedélyezni kell, és a kapcsolódó UAC-házirend beállításait megfelelően be kell állítani ahhoz, hogy a beépített rendszergazdai fiók és az összes többi olyan felhasználó, aki tagja a rendszergazdák csoportnak, rendszergazdai engedélyezéses módban fusson.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Alapértelmezett**: Igen
  
- **SAM-fiókok névtelen számbavételének megakadályozása**  
  Ez a biztonsági beállítás határozza meg, hogy a rendszer milyen további engedélyeket kap a névtelen kapcsolatok számára a számítógéphez. A Windows lehetővé teszi a névtelen felhasználók számára bizonyos tevékenységek végrehajtását, például a tartományi fiókok és hálózati megosztások nevének számbavételét. Ez akkor lehet hasznos, ha egy rendszergazda olyan megbízható tartományban kíván hozzáférést biztosítani a felhasználóknak, amely nem tart fenn kölcsönös bizalmi kapcsolatot. Ez a biztonsági beállítás lehetővé teszi, hogy további korlátozások kerüljenek a névtelen kapcsolatokra a következőképpen: 
  - *Igen* – nem engedélyezi a SAM-fiókok enumerálását. Ez a beállítás a hitelesített felhasználókkal rendelkező mindenkit lecseréli az erőforrásokra vonatkozó biztonsági engedélyekben.
  - *Nincs konfigurálva* – nincs további korlátozás. Használja az alapértelmezett engedélyeket.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Alapértelmezett**: Igen
  
- **Távoli hívások engedélyezése a biztonsági fiókok kezelőjének**  
  Ezzel a házirend-beállítással korlátozhatja a távoli RPC-kapcsolatokat a SAM-ra. Ha nincs bejelölve, a rendszer az alapértelmezett biztonsági leírót használja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Alapértelmezett**: *O:BAG: HELYTELEN: (A;; RC;;; BA*

- **Rendszergazdai jóváhagyási mód használata**  
  Ezzel a házirend-beállítással szabályozható a rendszergazdai engedélyezési mód működése a beépített rendszergazda fiókhoz. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Igen* – a beépített rendszergazdai fiók rendszergazdai jóváhagyási módot használ. Alapértelmezés szerint a jogosultságszint-emelést igénylő műveletek megkérik a felhasználót, hogy hagyja jóvá a műveletet. 
  - *Nincs konfigurálva* – a beépített rendszergazdai fiók minden olyan alkalmazást futtat, amely teljes körű rendszergazdai jogosultságokkal rendelkezik. 

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Alapértelmezett**: Igen
  
- **Felhasználói felületi hozzáférési alkalmazások engedélyezése biztonságos helyszíneken**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználói felület kisegítő lehetőségei (UIAccess vagy UIA) automatikusan le tudják-e tiltani a biztonságos asztalt az általános jogú felhasználók általi jogosultságszint-emelési kérésekhez. 
  - *Igen* – a UIA programok, például a Windows Távsegítség, automatikusan letiltják a jogosultságszint-emelési kérések biztonságos asztalát. Ha nem tiltja le a "felhasználói fiókok felügyelete: A jogosultságszint-emelésre való rákérdezéskor váltson a biztonságos asztalra, és a kérések a biztonságos asztal helyett az interaktív felhasználó asztalán jelennek meg. 
  - *Nincs konfigurálva*: – a biztonságos asztalt csak az interaktív asztal felhasználója tilthatja le, vagy letilthatja a felhasználói fiókok felügyeletét: Jogosultságszint-emelési kérés esetén váltson a biztonságos asztalra.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Alapértelmezett**: Igen

- **Alkalmazások telepítésének észlelése és Jogosultságszint-emelés kérése**  
  Ezzel a házirend-beállítással szabályozható a számítógép alkalmazás-telepítési észlelésének viselkedése. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Engedélyezve* – ha olyan alkalmazás-telepítési csomagot észlel, amely jogosultságszint-emelést igényel, a rendszer megkéri a felhasználót, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Letiltott* – az alkalmazás telepítési csomagjai nem észlelhetők, és a rendszer kéri a jogosultságszint-emelést. Az általános jogú felhasználói asztalokat futtató és a delegált telepítési technológiákat (például Csoportházirend-alapú szoftvertelepítés vagy System Management Server (SMS)) használó vállalatoknak le kell tiltaniuk ezt a házirend-beállítást. Ebben az esetben a telepítő észlelése szükségtelen.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Alapértelmezett**: Igen
  
- **A LAN Manager kivonatoló értékének a következő jelszó módosításakor való tárolásának megakadályozása**  
  Ez a biztonsági beállítás határozza meg, hogy a következő jelszó megváltozásakor az új jelszóhoz tartozó LAN Manager (LM) kivonatoló értéket tárolja-e a rendszer. Az LM-kivonat viszonylag gyenge és hajlamos a támadásokra, mint a kriptográfiailag erősebb Windows NT-kivonathoz képest. Mivel az LM-kivonat a biztonsági adatbázisban a helyi számítógépen van tárolva, a rendszer a jelszavakat a biztonsági adatbázis megtámadása esetén is veszélyeztetheti.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Alapértelmezett**: Igen

- **A fájl-és beállításjegyzék-írási hibák virtualizálása felhasználónkénti helyen**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer az alkalmazások írási hibáit átirányítsa-e a megadott beállításjegyzék-és fájlrendszerbeli helyeire Ezzel a házirend-beállítással csökkenthetők a rendszergazdaként futtatott alkalmazások és a futásidejű alkalmazásadatok írása a következőre: *% ProgramFiles%* , *% windir%* , *%windir%\System32*vagy *HKLM\Software*.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Alapértelmezett**: Igen

## <a name="ms-security-guide"></a>MS biztonsági útmutató  
További információ: [Policy CSP-MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) a Windows dokumentációjában.  

- **UAC-korlátozások alkalmazása helyi fiókokra hálózati bejelentkezéskor**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Alapértelmezett**: Enabled
  
- **SMB v1 – ügyfél-illesztőprogram indítási konfigurációja**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Alapértelmezett**: Letiltott illesztőprogram
  
- **SMB v1-kiszolgáló**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Alapértelmezett**: Letiltva
  
- **Kivonatoló hitelesítés**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Alapértelmezett**: Letiltva
  
- **Strukturált kivétel kezelésére vonatkozó felülírási védelem**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Alapértelmezett**: Enabled
  
## <a name="mss-legacy"></a>MSS örökölt  
További információ: [Policy CSP-MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) a Windows dokumentációjában.  

- **Hálózati IP-forrás útválasztási védelmi szintje**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Alapértelmezett**: Legmagasabb szintű védelem  
  
- **A hálózat figyelmen kívül hagyja a NetBIOS-névfeloldási kérelmeket a WINS-kiszolgálók kivételével**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Alapértelmezett**: Enabled
  
- **Hálózati IPv6-forrás útválasztási védelmi szintje**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Alapértelmezett**: Legmagasabb szintű védelem

- **Hálózati ICMP-átirányítás felülbírálja az OSPF által generált**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Alapértelmezett**: Letiltva
  
## <a name="power"></a>Power  
További információ: [házirend CSP-Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) a Windows dokumentációjában.  

- **Jelszó megkövetelése ébresztéskor a csatlakoztatáskor**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználótól a jelszót, amikor a rendszer visszatér az alvó állapotból. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a felhasználónak jelszót kér, amikor az alvó állapotból folytatódik. Ha letiltja ezt a házirend-beállítást, a felhasználó nem kér jelszót, amikor a rendszer visszatér az alvó állapotból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Alapértelmezett**: Enabled
  
- **Készenléti állapot, ha akkumulátorról alszik**  
  Ez a házirend-beállítás azt szabályozza, hogy a Windows használhat-e készenléti állapotokat a számítógép alvó állapotba helyezésekor. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a Windows készenléti állapotot használ a számítógép alvó állapotba helyezéséhez. Ha letiltja ezt a házirend-beállítást, a készenléti állapotok (S1-S3) nem engedélyezettek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Alapértelmezett**: Letiltva
  
- **Készenléti állapotok a csatlakoztatáskor**  
  Ez a házirend-beállítás azt szabályozza, hogy a Windows használhat-e készenléti állapotokat a számítógép alvó állapotba helyezésekor. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a Windows készenléti állapotot használ a számítógép alvó állapotba helyezéséhez. Ha letiltja ezt a házirend-beállítást, a készenléti állapotok (S1-S3) nem engedélyezettek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Alapértelmezett**: Letiltva
  
- **Jelszó megkövetelése ébresztéskor az akkumulátoron**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználótól a jelszót, amikor a rendszer visszatér az alvó állapotból. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a felhasználónak jelszót kér, amikor az alvó állapotból folytatódik. Ha letiltja ezt a házirend-beállítást, a felhasználó nem kér jelszót, amikor a rendszer visszatér az alvó állapotból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Alapértelmezett**: Enabled

## <a name="remote-assistance"></a>Távsegítség
- **Távsegítség kérése**  
  Ezzel a házirend-beállítással engedélyezheti vagy kikapcsolhatja a Távsegítség kérését a számítógépen. 
  - *Ha engedélyezi ezt a házirend-beállítást*, akkor a számítógépen lévő felhasználók e-mailben vagy fájlátvitel használatával kérhetnek segítséget. Emellett a felhasználók csevegési programokat is használhatnak a számítógéphez való csatlakozás engedélyezéséhez, és további Távsegítség-beállításokat is konfigurálhat. 
  - *Ha letiltja ezt a házirend-beállítást*, a számítógépen lévő felhasználók nem használhatnak e-mailt vagy fájlátvitelt, hogy kérjen segítséget. Emellett a felhasználók nem használhatják az azonnali üzenetküldési programokat, hogy engedélyezzék a kapcsolódást a számítógéphez. 
  - *Ha nem konfigurálja ezt a házirend-beállítást*, a felhasználók bekapcsolhatják vagy kikapcsolhatják a (z) Távsegítség szolgáltatást a Vezérlőpult Rendszer tulajdonságai párbeszédpanelén. A felhasználók a Távsegítség beállításait is megadhatják. 

  Ha engedélyezi ezt a házirend-beállítást, kétféleképpen engedélyezheti a segítőket a Távsegítség biztosításához: "A segítők csak a számítógép megtekintésére" vagy "a segítők a számítógép távvezérlésének engedélyezése". A "maximális jegy ideje" házirend-beállítás azt a korlátot állítja be, ameddig a Távsegítség e-mailben vagy fájlátvitel útján létrehozott meghívása nyitva maradhat. Az "e-mail-meghívások küldésére szolgáló módszer kiválasztása" beállítás megadja, hogy melyik e-mail-szabványt kell használni a Távsegítség meghívásához. Az e-mail-programtól függően használhatja a mailto standard (a meghívót egy internetes kapcsolaton keresztül) vagy a SMAPI (egyszerű MAPI) szabványt (a meghívót az e-mail-üzenethez csatolva). Ez a házirend-beállítás nem érhető el a Windows Vista rendszerben, mert a SMAPI az egyetlen támogatott módszer. Ha engedélyezi ezt a házirend-beállítást, akkor a megfelelő tűzfal-kivételeket is engedélyeznie kell a Távsegítség kommunikációjának engedélyezéséhez.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Alapértelmezett**: Távsegítség letiltása

  Ha a *Távsegítség engedélyezésére*van beállítva, konfigurálja a következő további beállításokat:  
  - **Távsegítség által kért engedély**  
    **Alapértelmezett**: Nézet  

  - **Jegy maximális élettartama**  
    **Alapértelmezett**: *Nincs konfigurálva*  

  - **Jegyek maximális időtartama**  
    **Alapértelmezett**: perc    

  - **E-Mail Meghívási módszere**  
    **Alapértelmezett**: Egyszerű MAPI

  
## <a name="remote-desktop-services"></a>Távoli asztali szolgáltatások  
További információ: [Policy CSP-RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) a Windows dokumentációjában.  

- **Jelszó mentésének tiltása**  
  Meghatározza, hogy a jelszavak menthetők-e a számítógépen Távoli asztali kapcsolatról. Ha engedélyezi ezt a beállítást, a Távoli asztali kapcsolat letiltotta a jelszó-mentés jelölőnégyzetet, és a felhasználók nem tudják menteni a jelszavakat. Amikor egy felhasználó megnyit egy RDP-fájlt a Távoli asztali kapcsolat használatával, és menti a beállításokat, az RDP-fájlban korábban létezett jelszavak törlődnek. Ha letiltja ezt a beállítást, vagy hagyja meg, hogy nincs konfigurálva, a felhasználó Távoli asztali kapcsolat használatával mentheti a jelszavakat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Alapértelmezett**: Enabled
  
- **Biztonságos RPC-kommunikáció**  
  Meghatározza, hogy egy Távoli asztal munkamenet-kiszolgáló biztonságos RPC-kommunikációt igényel-e az összes ügyféllel, vagy engedélyezi a nem biztonságos kommunikációt. Ezzel a beállítással megerősítheti az ügyfelekkel folytatott RPC-kommunikáció biztonságát úgy, hogy csak a hitelesített és titkosított kérelmeket engedélyezi. Ha az állapot engedélyezve értékre van állítva, Távoli asztali szolgáltatások fogadja a biztonságos kéréseket támogató RPC-ügyfelektől érkező kérelmeket, és nem engedélyezi a nem biztonságos kommunikációt a nem megbízható ügyfelekkel. Ha az állapot letiltva értékre van állítva, Távoli asztali szolgáltatások mindig minden RPC-forgalomhoz kér biztonságot. A nem biztonságos kommunikáció azonban olyan RPC-ügyfelek számára engedélyezett, amelyek nem válaszolnak a kérelemre. Ha az állapot nincs konfigurálva értékre van állítva, akkor a nem biztonságos kommunikáció engedélyezett. Megjegyezés: Az RPC interfész Távoli asztali szolgáltatások felügyeletére és konfigurálására szolgál.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Alapértelmezett**: Enabled
  
- **Meghajtó átirányításának tiltása**  
  Ezzel a házirend-beállítással megadható, hogy meg kell-e akadályozni az ügyfélmeghajtók hozzárendelését egy Távoli asztali szolgáltatások-munkamenetben (meghajtó-átirányítás). Alapértelmezés szerint a távoli asztali munkamenetgazda-kiszolgáló automatikusan leképezi az ügyféloldali meghajtókat a kapcsolaton keresztül. A csatlakoztatott meghajtók a Fájlkezelőben vagy a számítógépen a következő formátumban  *\<* jelennek meg: meghajtóbetűjel > a  *\<számítógépnév >* . Ezt a házirend-beállítást használhatja a viselkedés felülbírálásához. Ha engedélyezi ezt a házirend-beállítást, az ügyfélmeghajtók átirányítása Távoli asztali szolgáltatások munkamenetekben nem engedélyezett, és a vágólap-fájlmásolás átirányítása nem engedélyezett a Windows Server 2003, Windows 8 és Windows XP rendszerű számítógépeken. Ha letiltja ezt a házirend-beállítást, a rendszer mindig engedélyezi az ügyfél-meghajtó átirányítását. A vágólap-másolási átirányítás is mindig engedélyezett, ha a vágólap átirányítása engedélyezve van. Ha nem konfigurálja ezt a házirend-beállítást, az ügyfél-meghajtó átirányítása és a vágólap-fájlmásolás átirányítása nincs megadva a Csoportházirend szinten.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Alapértelmezett**: Enabled
  
- **Jelszó kérése a csatlakozáskor**  
  Ezzel a házirend-beállítással megadható, hogy a Távoli asztali szolgáltatások mindig kéri-e az ügyfelet a jelszó kérésére a csatlakozáskor. Ezzel a beállítással megadhatja, hogy a felhasználók milyen jelszóval jelentkezzenek be Távoli asztali szolgáltatásokba, még akkor is, ha már megadták a jelszót a Távoli asztali kapcsolat-ügyfélben. Alapértelmezés szerint a Távoli asztali szolgáltatások lehetővé teszi, hogy a felhasználók automatikusan bejelentkeznek a Távoli asztali kapcsolat-ügyfélben lévő jelszó megadásával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók nem tudnak automatikusan bejelentkezni a Távoli asztali szolgáltatásokba, ha a Távoli asztali kapcsolat-ügyfélben megadják a jelszavukat. a rendszer jelszót kér a bejelentkezéshez. Ha letiltja ezt a házirend-beállítást, a felhasználók bármikor bejelentkezhetnek a Távoli asztali szolgáltatások automatikusan, ha megadják a jelszavukat a Távoli asztali kapcsolat ügyfélen. Ha nem konfigurálja ezt a házirend-beállítást, az automatikus bejelentkezés nincs megadva a Csoportházirend szinten.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Alapértelmezett**: Enabled
  
- **Távoli asztali szolgáltatások ügyfélkapcsolatának titkosítási szintje**  
  Meghatározza, hogy szükség van-e egy adott titkosítási szint használatára az ügyfélszámítógépek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikáció biztonságossá tételéhez RDP protokoll (RDP) kapcsolatok során. Ez a szabályzat csak akkor érvényes, ha natív RDP-titkosítást használ. Azonban a natív RDP-titkosítás (az SSL-titkosítás helyett) nem ajánlott. Ez a szabályzat nem vonatkozik az SSL-titkosításra. Ha engedélyezi ezt a házirend-beállítást, a távoli kapcsolatok során az ügyfelek és a távoli asztali munkamenetgazda-kiszolgálók közötti összes kommunikációnak az ebben a beállításban megadott titkosítási módszert kell használnia. Alapértelmezés szerint a titkosítási szint magas értékre van állítva. A következő titkosítási módszerek érhetők el:  
  - *Magas* – a magas beállítás a-ügyfélről a kiszolgálóra és a kiszolgálóról az ügyfélre érkező, erős 128 bites titkosítást használó adatok titkosítását végzi. Használja ezt a titkosítási szintet olyan környezetekben, amelyek csak 128 bites ügyfeleket tartalmaznak (például Távoli asztali kapcsolatt futtató ügyfeleket). Azok az ügyfelek, amelyek nem támogatják ezt a titkosítási szintet, nem csatlakozhatnak a távoli asztali munkamenetgazda-kiszolgálókhoz.  
  - *Ügyfél-kompatibilis* – az ügyfél-kompatibilis beállítás titkosítja az ügyfél és a kiszolgáló között továbbított, az ügyfél által támogatott maximális kulcs erősségét. Használja ezt a titkosítási szintet olyan környezetekben, amelyek olyan ügyfeleket tartalmaznak, amelyek nem támogatják a 128 bites titkosítást.  
  - *Alacsony* – az alacsony beállítás a 56 bites titkosítás használatával csak az ügyfélről a kiszolgálóra továbbított adatok titkosítását végzi.  
  
  Ha letiltja vagy nem konfigurálja ezt a beállítást, a távoli kapcsolatokhoz használni kívánt titkosítási szint nem kényszeríthető Csoportházirendon keresztül. A fontos FIPS-megfelelőség a rendszerkriptográfiai szolgáltatáson keresztül konfigurálható. A FIPS szabványnak megfelelő algoritmusok használata titkosításhoz, kivonatoláshoz és aláírási beállításokhoz Csoportházirendban (a számítógép konfigurációja \ Windows beállításai \ helyi házirend \ házirend beállítások menüpontban) A FIPS-kompatibilis beállítás titkosítja és visszafejti az ügyfél és a kiszolgáló között továbbított adatokat a kiszolgálóról az ügyfélre, a Federal Information Processing standard (FIPS) 140 titkosítási algoritmusokkal a Microsoft titkosítási moduljainak használatával. Akkor használja ezt a titkosítási szintet, ha az ügyfelek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikációhoz a legmagasabb szintű titkosítás szükséges.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Alapértelmezett**: Magas
  
## <a name="remote-management"></a>Távfelügyelet  
További információ: [Policy CSP-RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) a Windows dokumentációjában.  

- **Futtató hitelesítő adatok tárolásának tiltása**  
  Ügyfél alapszintű hitelesítése.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Alapértelmezett**: Enabled
  
- **Alapszintű hitelesítés**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) szolgáltatás fogadja-e az egyszerű hitelesítést egy távoli ügyfélről. Ha engedélyezi ezt a házirend-beállítást, a WinRM szolgáltatás fogadja az egyszerű hitelesítést egy távoli ügyfélről. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM szolgáltatás nem fogadja el az egyszerű hitelesítést egy távoli ügyféltől.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél-kivonatoló hitelesítés letiltása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfele kivonatoló hitelesítést használ-e. Ha engedélyezi ezt a házirend-beállítást, a WinRM-ügyfél nem használ kivonatoló hitelesítést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél kivonatoló hitelesítést használ.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Alapértelmezett**: Enabled
  
- **Titkosítatlan forgalom**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) szolgáltatás küld-e és fogad-e titkosítatlan üzeneteket a hálózaton keresztül. Ha engedélyezi ezt a házirend-beállítást, a Rendszerfelügyeleti webszolgáltatások ügyfele titkosítatlan üzeneteket küld és fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél csak a titkosított üzeneteket küldi vagy fogadja a hálózaton keresztül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél titkosítatlan forgalma**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfél küld-e és fogad-e titkosítatlan üzeneteket a hálózaton keresztül. Ha engedélyezi ezt a házirend-beállítást, a Rendszerfelügyeleti webszolgáltatások ügyfele titkosítatlan üzeneteket küld és fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél csak a titkosított üzeneteket küldi vagy fogadja a hálózaton keresztül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél alapszintű hitelesítése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfél alapszintű hitelesítést használ-e. Ha engedélyezi ezt a házirend-beállítást, a WinRM-ügyfél alapszintű hitelesítést használ. Ha a WinRM a HTTP-átvitel használatára van konfigurálva, a Felhasználónév és a jelszó küldése a hálózaton keresztül egyszerű szövegként történik. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél nem használ alapszintű hitelesítést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Alapértelmezett**: Letiltva
  
## <a name="remote-procedure-call"></a>Távoli eljárás hívása  
További információ: [Policy CSP-RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) a Windows dokumentációjában.  

- **Nem hitelesített RPC-ügyfél beállításai**  
  Ezzel a házirend-beállítással szabályozható, hogy az RPC-kiszolgáló futtatókörnyezete hogyan kezelje az RPC-kiszolgálókhoz csatlakozó nem hitelesített RPC-ügyfeleket Ezzel a házirend-beállítással az összes RPC-alkalmazás hatással van. Tartományi környezetben ezt a házirend-beállítást körültekintően kell használni, mivel ez a funkció számos funkciót érint, beleértve a csoportházirend feldolgozását is. A házirend-beállítás módosításának visszaállításához manuális beavatkozásra van szükség az egyes érintett gépeken. Ez a házirend-beállítás soha nem alkalmazható tartományvezérlőre. Ha letiltja ezt a házirend-beállítást, az RPC-kiszolgáló futtatókörnyezete a "hitelesített" értéket használja a Windows-ügyfélen, és a "None" értéket a Windows Server azon verzióiban, amelyek támogatják ezt a házirend-beállítást. Ha nem konfigurálja ezt a házirend-beállítást, az továbbra is le lesz tiltva. Az RPC-kiszolgáló futtatókörnyezete úgy viselkedik, mintha engedélyezve volt a Windows-ügyfélhez használt "hitelesített" értékkel, valamint a "nincs" értékkel, amelyet ez a házirend-beállítás támogat. Ha engedélyezi ezt a házirend-beállítást, a rendszer az RPC-kiszolgáló futtatókörnyezetét arra utasítja, hogy korlátozza a gépen futó RPC-kiszolgálókhoz csatlakozó nem hitelesített RPC-ügyfeleket. Az ügyfél akkor tekinthető hitelesített ügyfélnek, ha nevesített csövet használ a kiszolgálóval való kommunikációhoz, vagy ha RPC-biztonságot használ. A nem hitelesített ügyfelek által elérhetővé tett RPC-felületek mentesülnek ettől a korlátozástól attól függően, hogy a házirend-beállítás kiválasztott értéke milyen.  
  - A *none* értékkel az összes RPC-ügyfél csatlakozhat a házirend-beállítást alkalmazó számítógépen futó RPC-kiszolgálókhoz. 
  - A hitelesítéssel csak a hitelesített RPC-ügyfelek (a fenti definíció alapján) csatlakozhatnak azon a számítógépen futó RPC-kiszolgálókhoz, amelyen a házirend-beállítás alkalmazva van. A rendszer kivételeket biztosít azokhoz az interfészekhez, amelyek kérték azokat. 
  - A *kivételek nélküli hitelesítés* lehetővé teszi, hogy csak a fenti definíción alapuló hitelesített RPC-ügyfelek csatlakozzanak a házirend-beállítást alkalmazó számítógépen futó RPC-kiszolgálókhoz. A kivételek nem engedélyezettek. Megjegyezés: Ez a házirend-beállítás csak a rendszer újraindítása után lesz alkalmazva.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Alapértelmezett**: Hitelesített

## <a name="search"></a>Keresés 
További információ: [házirend-CSP – keresés](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) a Windows dokumentációjában.  

- **Titkosított elemek indexelésének letiltása**  
  Engedélyezi vagy tiltja az elemek indexelését. Ez a kapcsoló a Windows Search indexelő szolgáltatáshoz használható, amely azt szabályozza, hogy a rendszer indexeli-e a titkosított elemeket (például a Windows Information Protection (folyamatban lévő) védett fájlokat. A szabályzat engedélyezésekor a WIP által védett elemek indexelve lesznek, a velük kapcsolatos metaadatok pedig titkosítatlan helyen lesznek tárolva. A metaadatok között szerepel egyebek között a fájl elérési útja és módosításának dátuma. Ha a házirend le van tiltva, a rendszer nem indexeli a nem indexelt, és nem jeleníti meg az eredményeket a Cortana vagy a fájlkezelőben. A Fényképek és a Groove alkalmazás teljesítménye csökkenhet, ha nagy mennyiségű WIP-védelemmel ellátott médiafájl található az eszközön.  
  [További információ]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Alapértelmezett**: Igen
  
## <a name="smart-screen"></a>Intelligens képernyő  
További információ: [Policy CSP-SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) a Windows dokumentációjában.  

- **Nem ellenőrzött fájlok végrehajtásának letiltása**  
  Nem ellenőrzött fájlok futtatásának letiltása a felhasználó számára. 
  - *Nincs konfigurálva* – az alkalmazottak figyelmen kívül hagyhatják a SmartScreen-figyelmeztetéseket, és kártékony fájlokat futtathatnak. 
  - *Igen* – az alkalmazottak nem hagyhatják figyelmen kívül a SmartScreen-figyelmeztetéseket, és nem futtathatnak rosszindulatú fájlokat.

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Alapértelmezett**: Igen

- **SmartScreen megkövetelése alkalmazások és fájlok esetén**  
  Lehetővé teszi a rendszergazdáknak a SmartScreen konfigurálását Windows rendszeren.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Alapértelmezett**: Igen
  
## <a name="system"></a>Rendszer  
További információ: [Policy CSP – rendszer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) a Windows dokumentációjában.  

- **Rendszerindítási indítási illesztőprogram inicializálása**  
  Ezzel a házirend-beállítással megadhatja, hogy mely rendszerindítási illesztőprogramok legyenek inicializálva egy korai indítási antimalware rendszerindítási illesztőprogram által meghatározott besorolás alapján. A korai indítású antimalware rendszerindítási illesztőprogram a következő besorolásokat adhatja vissza minden rendszerindítási illesztőprogramhoz: 
  - *Jó* – az illesztőprogram aláírása megtörtént, és a nem lett illetéktelenül módosítva.  
  - *Rossz* – az illesztőprogram kártevőként lett azonosítva. Azt javasoljuk, hogy ne engedélyezze az ismert hibás illesztőprogramok inicializálását. 
  - *Rossz, de szükséges a* rendszerindításhoz – az illesztőprogram kártevőként van azonosítva, de a számítógép nem tud sikeresen elindulni az illesztőprogram betöltése nélkül. 
  - *Ismeretlen* – ezt az illesztőprogramot a kártevő-észlelési alkalmazás nem tanúsította, és a korai indítású antimalware rendszerindítási illesztőprogram nem sorolta be.  

  Ha engedélyezi ezt a házirend-beállítást, kiválaszthatja, hogy mely rendszerindítási illesztőprogramokat szeretné inicializálni a számítógép következő indításakor. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszerindítási illesztőprogramok helyesnek, ismeretlennek vagy hibásnak, de a rendszerindítási kritikusnak megfelelően vannak inicializálva, és a helytelenül meghatározott illesztőprogramok inicializálását a rendszer kihagyja. Ha a kártevő-észlelési alkalmazás nem tartalmaz korai indítású antimalware rendszerindítási illesztőprogramot, vagy ha a korai indítású kártevő-indítási illesztőprogram le van tiltva, akkor ez a beállítás nem lép érvénybe, és az összes rendszerindítási illesztőprogram inicializálva van.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Alapértelmezett**: Jól ismert és rossz kritikus


## <a name="wi-fi"></a>Wi-Fi  
További információ: [Policy CSP-WiFi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) a Windows-dokumentációban.  

- **Internetes megosztás letiltása**  
  Megadja, hogy lehetséges-e az internetes megosztás az eszközön.   
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Alapértelmezett**: Igen  

- **A Wi-Fi elérési pontokhoz való automatikus csatlakozás letiltása**  
  A Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése vagy letiltása az eszközön.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Alapértelmezett**: Igen  
  
## <a name="windows-connection-manager"></a>Windows Csatlakozáskezelő  
További információ: [Policy CSP-WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) a Windows dokumentációjában.  

- **Nem tartományi hálózatokhoz való kapcsolódás letiltása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a számítógépek egyszerre egy tartományalapú hálózathoz és egy nem tartományon alapuló hálózathoz csatlakozzanak. Ha ez a házirend-beállítás engedélyezve van, a számítógép a következő esetekben válaszol az automatikus és a manuális hálózati csatlakozási kísérletekre: 
  - Ha a számítógép már csatlakozik egy tartományalapú hálózathoz, az automatikus kapcsolódási kísérleteket a rendszer letiltja a nem tartományi hálózatokra irányuló összes automatikus kapcsolódási kísérletet. Ha a számítógép már csatlakozik egy nem tartomány alapú hálózathoz, a rendszer letiltja a tartományalapú hálózatokra irányuló automatikus kapcsolódási kísérleteket. 
  - A manuális kapcsolódási kísérlet akkor fordul elő, ha a számítógép már csatlakoztatva van egy nem tartomány alapú hálózathoz vagy egy, az Etherneten kívüli, más adathordozón található tartományalapú hálózathoz, és egy felhasználó egy további, a szabályzat megsértése miatti hálózathoz való csatlakozást kísérel meg létrehozni. beállítás, a meglévő hálózati kapcsolat megszakad, és a manuális kapcsolat engedélyezett. Ha a számítógép már csatlakoztatva van egy nem tartomány alapú hálózathoz vagy egy tartományalapú hálózathoz Ethernet-kapcsolaton keresztül, és egy felhasználó egy további, a házirend-beállítás megsértése miatti hálózatra irányuló manuális kapcsolatot próbál létrehozni, a meglévő Ethernet-kapcsolat karbantartva, és a manuális kapcsolódási kísérlet le van tiltva.  

  Ha a házirend-beállítás nincs konfigurálva vagy le van tiltva, a számítógépek egyszerre csatlakozhatnak a tartományhoz és a tartományhoz nem tartozó hálózatokhoz is.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Alapértelmezett**: Enabled
  
## <a name="windows-defender"></a>Windows Defender  
További információ: [Policy CSP-Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) a Windows dokumentációjában.  

- **Bejövő üzenetek ellenőrzése**  
  Engedélyezi vagy engedélyezi az e-mailek vizsgálatát.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Alapértelmezett**: Igen  

- **Az Office-alkalmazások alárendelt folyamatának indítása**  
  Az Office-alkalmazások nem hozhatnak létre alárendelt folyamatokat. Ide tartozik a Word, az Excel, a PowerPoint, a OneNote és a hozzáférés. Ez egy tipikus kártevő-viselkedés, különösen olyan makró-alapú támadások esetében, amelyek az Office-alkalmazások használatával próbálnak meg rosszindulatú végrehajtható fájlokat elindítani vagy letölteni.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Alapértelmezett**: Letiltás
  
- **Defender-minta küldésének beleegyező típusa**  
  A Windows Defender felhasználói beleegyezési szintjét ellenőrzi az adatküldés során. Ha a szükséges engedély már meg lett adva, a Windows Defender elküldi azokat. Ha nem, (és ha a felhasználónak soha nem kell megadnia a kérdést), a felhasználói felület megadását kéri (ha a Defender/AllowCloudProtection engedélyezett) az adatok elküldése előtt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Alapértelmezett**: Biztonságos minták automatikus küldése 
  
- **Aláírás-frissítési időköz (óra)**  
  Defender-aláírás frissítési időköze (óra)
  
  **Alapértelmezett**: 4
  
- **Parancsfájl letöltött adattartalom-végrehajtási típusa**  
  Defender-parancsfájl letöltött adattartalom-végrehajtási típusa
  
  **Alapértelmezett**: Letiltás
  
- **Hitelesítő adatok ellopási típusának tiltása**  
  A Windows Defender hitelesítőadat-őr virtualizálás-alapú biztonságot használ a titkok elkülönítésére, így csak a rendszerjogosultságú rendszerszoftverek férhetnek hozzájuk. A titkos kódokhoz való illetéktelen hozzáférés a hitelesítési adatok ellopását okozó (például pass-the-hash vagy pass-the-ticket típusú) támadásokhoz vezethetnek. A Windows Defender hitelesítőadat-őr megakadályozza ezeket a támadásokat az NTLM jelszó-kivonatok, a Kerberos-jegyek és az alkalmazások tartományi hitelesítő adatokként tárolt hitelesítő adatainak védelmével.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Alapértelmezett**: Engedélyezés

- **E-mail tartalom végrehajtásának típusa**  
  Ez a szabály blokkolja a következő fájltípusokat a Futtatás vagy a Microsoft Outlook vagy webmail szolgáltatásban (például Gmail.com vagy Outlook.com) látott e-mailből való indításkor: Végrehajtható fájlok (például. exe,. dll vagy. scr) parancsfájlok (például PowerShell. ps, VisualBasic. vbs vagy JavaScript. js fájl).  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **Alapértelmezett**: Letiltás

- **Adobe Reader indítása alárendelt folyamatban**  

  **Alapértelmezett**: Engedélyezés

- **Hálózati védelem típusa**  
  Ez a szabályzat lehetővé teszi a hálózati védelem (Letiltás/naplózás) bekapcsolását a Windows Defender Exploit Guardben. A hálózatvédelem a Windows Defender Exploit Guard egyik funkciója, amely megvédi az alkalmazottakat az adathalászat-csalások, a biztonsági rések és az interneten található kártékony tartalmak elérésére alkalmas bármely alkalmazás használatával. Ez magában foglalja a harmadik féltől származó böngészőknek a veszélyes helyekhez való csatlakozásának megakadályozását. Az érték típusa egész szám. Ha engedélyezi ezt a beállítást, a hálózati védelem be van kapcsolva, és az alkalmazottak nem kapcsolhatják ki. A viselkedését a következő beállítások szabályozzák: Blokkolás és naplózás. Ha engedélyezi ezt a házirendet a "letiltás" beállítással, a felhasználók és az alkalmazások le vannak tiltva a veszélyes tartományokhoz való csatlakozáskor. Ezt a tevékenységet a Windows Defender Security Centerban tekintheti meg. Ha engedélyezi ezt a házirendet a "naplózás" beállítással, a felhasználók/alkalmazások nem lesznek letiltva a veszélyes tartományokhoz való csatlakozáskor. Ezt a tevékenységet azonban továbbra is láthatja a Windows Defender Security Centerban. Ha letiltja ezt a házirendet, a felhasználók/alkalmazások nem lesznek letiltva a veszélyes tartományokhoz való csatlakozáskor. A Windows Defender Security Centerban semmilyen hálózati tevékenység nem jelenik meg. Ha nem konfigurálja ezt a házirendet, a hálózati blokkolás alapértelmezés szerint le van tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067102)  
  
  **Alapértelmezett**: Engedélyezés
  
- **Defender-ütemterv vizsgálatának napja**  
  Defender-ütemterv vizsgálatának napja.
  
  **Alapértelmezett**: Mindennap
  
- **Felhőbe szállított védelem**  
  A számítógép legjobb védelméhez a Windows Defender adatokat küld a Microsoftnak a talált problémákról. A Microsoft elemezni fogja ezeket az információkat, többet tudhat meg az Ön és más ügyfelek problémáit érintő problémákról, és továbbfejlesztett megoldásokat kínál.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Alapértelmezett**:  Igen  

- **A Defender vélhetően nemkívánatos alkalmazásának művelete**  
  A Windows Defender víruskereső vélhetően nemkívánatos alkalmazás-(PUA-) védelmi funkciója képes azonosítani és letiltani a PUAs a hálózaton lévő végpontokon való letöltés és telepítés során. Ezek az alkalmazások nem tekintendők vírusok, kártevők vagy más típusú fenyegetéseknek, de olyan végpontokon is végezhetnek műveleteket, amelyek hátrányosan befolyásolják a teljesítményüket vagy a használatukat. A PUA olyan alkalmazásokra is hivatkozhat, amelyeknek a megítélése szerint rossz hírnevük van. A tipikus PUA-viselkedés a következőket tartalmazza: Különböző típusú szoftver-árukapcsolás ad-befecskendezés a webböngészőkbe és a beállításjegyzék-optimalizálók a problémák észlelésére, a hibák kijavítására, de továbbra is a végponton maradnak, és nem tesznek módosítást vagy optimalizálást (más néven "gazember víruskereső" programokat). Ezek az alkalmazások növelhetik a kártevő szoftverrel fertőzött hálózat kockázatát, így a rosszindulatú fertőzések nehezebben azonosíthatók, és az informatikai erőforrások az alkalmazások tisztításával is felhasználhatók.  
  [További információ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Alapértelmezett**: Letiltás  

- **Parancsfájl által eltorzított kód típusa**  
  A kártevők és egyéb fenyegetések megpróbálják eltorzítani vagy elrejteni a kártékony kódokat bizonyos parancsfájlokban. Ez a szabály akadályozza meg, hogy a rendszer ne futtasson olyan parancsfájlokat, amelyek nem futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Alapértelmezett**: Letiltás
  
- **Cserélhető meghajtók vizsgálata teljes vizsgálat során**  
  Lehetővé teszi a Windows Defender számára a kártékony és nemkívánatos szoftverek keresését a cserélhető meghajtókon (például flash meghajtókon) a teljes vizsgálat során. A Windows Defender víruskereső a végrehajtás előtt megkeresi az USB-eszközökön található összes fájlt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Alapértelmezett**: Igen  
  
- **Archív fájlok ellenőrzése**  
  Defender-vizsgálat archív fájljai.
  
  **Alapértelmezett**: Igen
  
- **Viselkedés figyelése**  
  Engedélyezi vagy engedélyezi a Windows Defender viselkedésének figyelését. A Windows 10 rendszerbe ágyazott érzékelők begyűjtik és feldolgozzák az operációs rendszer viselkedési jeleit, és elküldik az érzékelő adatait a Microsoft Defender ATP privát, elkülönített, Felhőbeli példányának.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Alapértelmezett**: Igen

- **Hálózati mappákból megnyitott fájlok vizsgálata**  
  Ha a fájlok csak olvashatók, a felhasználó nem tudja eltávolítani az észlelt kártevőket.
  
  **Alapértelmezett**: Igen

- **Nem megbízható USB-folyamat típusa**  
  Ezzel a szabállyal a rendszergazdák megakadályozhatják az aláíratlan vagy nem megbízható végrehajtható fájlok futtatását USB cserélhető meghajtókról, beleértve az SD-kártyákat is.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Alapértelmezett**: Letiltás
  
- **Office-alkalmazások egyéb folyamat-injektálási típusa**  
  Az Office-alkalmazások, például a Word, az Excel, a PowerPoint és a OneNote, nem tudnak kódot beszúrni más folyamatokra. Ezt általában a kártevők használják rosszindulatú kód futtatására arra az kísérletre, hogy el lehessen rejteni a tevékenységet a víruskereső keresőmotorokból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Alapértelmezett**:  Letiltás
  
- **Office-makróvédelmi kód engedélyezése Win32 importálási típus**  
  A kártevők a Win32 DLL-fájlok importálásához és betöltéséhez használhatnak makróvírus-kódot az Office-fájlokban, amelyek ezután API-hívások készítésére használhatók a rendszeren belüli további fertőzés engedélyezéséhez. Ez a szabály megkísérli letiltani a Win32 DLL-ek importálására képes makrót tartalmazó Office-fájlokat. Ide tartozik a Word, az Excel, a PowerPoint és a OneNote.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Alapértelmezett**: Letiltás  
  
- **Defender Cloud Block-szint**  
  A Defender Cloud Block szintje.
  
  **Alapértelmezett**: Nincs konfigurálva

- **Valós idejű figyelés**  
  A Defender valós idejű figyelést igényel.
  
  **Alapértelmezett**: Igen
 
- **Office kommunikációs alkalmazások indítása alárendelt folyamatban**  

  **Alapértelmezett**:  Engedélyezés

- **Office-alkalmazások végrehajtható tartalom létrehozási vagy indítási típusa**  
  Ez a szabály a végrehajtható fájlokat létrehozó vagy indító gyanús és kártékony bővítmények és parancsfájlok (bővítmények) által használt jellemző viselkedéseket célozza meg. Ez egy tipikus kártevő-módszer. Az Office-alkalmazások nem használják a bővítményeket. Ezek a bővítmények általában a Windows Scripting Host (. wsh fájlok) használatával futtatnak bizonyos feladatokat automatizáló vagy felhasználó által létrehozott kiegészítő funkciókat biztosító parancsfájlokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Alapértelmezett**: Letiltás

## <a name="windows-defender-firewall"></a>Windows Defender-tűzfal  
További információ: [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) a Windows-protokollok dokumentációjában.  

- **Tűzfal-profil tartománya**  
  Meghatározza azokat a profilokat, amelyekre a szabály tartozik: Tartomány, magán, nyilvános. Ez az érték a tartományokhoz csatlakozó hálózatok profilját jelöli.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: Igen

  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: Igen 

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezett**: Engedélyezett

- **Nyilvános tűzfal-profil**  
  Meghatározza azokat a profilokat, amelyekre a szabály tartozik: Tartomány, magán, nyilvános. Ez az érték a nyilvános hálózatok profilját jelöli. Ezek a hálózatok a kiszolgáló gazdagépének rendszergazdái. A besorolás akkor történik meg, amikor a gazdagép először csatlakozik a hálózathoz. Ezek a hálózatok általában olyan repülőtereken, kávézókban és más nyilvános helyeken találhatók, ahol a hálózatban vagy a hálózati rendszergazdában található társai nem megbízhatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: Igen

  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: Igen 

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezett**: Engedélyezett

  - **Nincs egyesítve a csoportházirendből származó kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen

  - **A csoportházirend házirend-szabályai nem lettek egyesítve**  
    **Alapértelmezett**: Igen

- **Saját tűzfal-profil**  
  Meghatározza azokat a profilokat, amelyekre a szabály tartozik: Tartomány, magán, nyilvános. Ez az érték a magánhálózatok profilját jelöli.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: Igen

  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: Igen 

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezett**: Engedélyezett

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello  
- **Fokozott hamisítás szükséges, ha elérhető**  
  Ha igen, akkor az eszközök fokozott hamisítást alkalmaznak, ha elérhető. Ha nem, a rendszer letiltja a hamisítás elleni hamisítást. Nincs konfigurálva, az ügyfélen végzett konfigurációk tiszteletben tartása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Alapértelmezett**: Igen

- **A vállalati Windows Hello konfigurálása**   
    A vállalati Windows Hello egy alternatív módszer a Windowsba való bejelentkezéshez jelszavak, intelligens kártyák és virtuális intelligens kártyák helyett.  

  - Ha az *Igen*értékre van állítva, akkor engedélyezi ezt a házirendet, és az eszköz kiépíti a vállalati Windows Hello-t.  
  - Ha a *nincs konfigurálva*értékre van állítva, az alapterv nem befolyásolja az eszköz házirend-beállítását. Ez azt jelenti, hogy ha a vállalati Windows Hello le van tiltva egy eszközön, az továbbra is le lesz tiltva. Ha engedélyezve van, az továbbra is engedélyezett marad. 

  A vállalati Windows Hello nem tiltható le ezen alapterven keresztül. A Windows Hello for Business letiltható a [Windows-regisztráció](windows-hello.md)konfigurálásakor, vagy az [Identity Protection](identity-protection-configure.md)eszköz konfigurációs profiljának részeként.  

  **Alapértelmezett**: Igen

- **Kisbetűk megkövetelése a PIN-kódban**  
  Ha szükséges, a felhasználói PIN-kódnak tartalmaznia kell legalább egy kisbetűt.

  **Alapértelmezett**: Engedélyezett

- **Speciális karakterek megkövetelése a PIN-kódban**  
  Ha szükséges, a felhasználói PIN-kódnak tartalmaznia kell legalább egy speciális karaktert.

  **Alapértelmezett**: Engedélyezett

- **PIN-kód minimális hossza**  
  A PIN-kód minimális hosszának 4 és 127 között kell lennie.

  **Alapértelmezett**: 6

- **Nagybetűk megkövetelése a PIN-kódban**  
  Ha szükséges, a felhasználó PIN-kódjának legalább egy nagybetűt tartalmaznia kell.

  **Alapértelmezett**: Engedélyezett

## <a name="windows-ink-workspace"></a>Windows Ink-munkaterület  
További információ: [Policy CSP-WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) a Windows dokumentációjában.  

- **Szabadkézi munkaterület**  
  Megadja, hogy engedélyezi-e a felhasználó számára a szabadkézi munkaterület elérését. 
  - Letiltva – a szabadkézi munkaterület hozzáférése le van tiltva. A szolgáltatás ki van kapcsolva.
  - *Engedélyezve* – a tinta munkaterület funkció be van kapcsolva, de a felhasználó nem férhet hozzá a zárolási képernyő felett.
  - *Nincs konfigurálva* – a tinta munkaterület funkció be van kapcsolva, és a felhasználó a zárolási képernyő felett is használhatja.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Alapértelmezett**: Enabled
 
## <a name="windows-powershell"></a>Windows PowerShell  
További információ: [Policy CSP-WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) a Windows dokumentációjában.  

- **Rendszerhéj-rendszerhéj parancsfájl-blokkolási naplózása**  
  Ezzel a házirend-beállítással engedélyezhető a PowerShell-parancsfájl összes bemenetének naplózása a Microsoft-Windows-PowerShell/operatív eseménynaplóba. Ha engedélyezi ezt a házirend-beállítást, a Windows PowerShell naplózza a parancsok, parancsfájl-blokkok, függvények és parancsfájlok feldolgozását – akár interaktív módon, akár automatizálás útján. Ha letiltja ezt a házirend-beállítást, a PowerShell-parancsfájl bemenetének naplózása le van tiltva. Ha engedélyezi a parancsfájl-blokkoló naplózását, a PowerShell emellett naplózza az eseményeket, amikor egy parancs, parancsfájl-blokk, függvény vagy parancsfájl meghívása elindul vagy leáll. A meghívásos naplózás engedélyezése nagy mennyiségű eseménynaplót generál. Megjegyezés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználó konfigurációja területen található a Csoportházirend szerkesztőben. A számítógép-konfigurációs házirend beállítása elsőbbséget élvez a felhasználói konfigurációs házirend beállításával szemben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Alapértelmezett**: Enabled

## <a name="whats-changed-in-the-new-template"></a>Az új sablon módosítása
A *május 2019 sablon Mdm biztonsági alapterve* a következő változásokkal rendelkezik az *előnézeti* sablonban.

### <a name="changes-to-the-baseline-settings"></a>Az alapkonfiguráció beállításainak módosításai
A következő beállítások egyike:
- *Új* az alapkonfiguráció ezen legújabb verziójában.
- A rendszer *eltávolítja* a legújabb alapverzióról, de az előző verzióban szerepelt.
- A beállítások a korábbi verziókban való megjelenésének valamilyen módon módosultak. 

*[Új]* a [**zárolás felett**](#above-lock):
- **Alkalmazások hang aktiválása zárolt képernyőről**    

*[Új]* [**alkalmazás-kezelés**](#application-management): 
- **Felhasználók felügyeletének tiltása a telepítéseken**  
- **MSI-alkalmazások telepítésének letiltása emelt szintű jogosultságokkal**  

*[Eltávolítva]* [**BitLocker**](#bitlocker):  
- Bites zárolás cserélhető meghajtó házirendje > **titkosítási módszer**
- **Bit Locker rögzített meghajtó szabályzata** *(minden beállítás)*
- **Bites zárolás rendszermeghajtó** -házirendje *(minden beállítás)*

*[Új]* [**kapcsolat**](#connectivity):
- **Az UNC elérési utak biztonságos elérésének konfigurálása**

*[Új]* [**Device Guard**](#device-guard):
- **Virtualizálás-alapú biztonság**


*[Új]* [**DMA-őr**](#dma-guard):
- **A kernel DMA-védelemmel nem kompatibilis külső eszközök enumerálása**  

*[Új]* [**Internet Explorer**](#internet-explorer):
- **Explorer Internet zóna frissítései az állapotsoron parancsfájl használatával**
- **Internet Explorer Internet Zone húz és eldobása, illetve fájlok másolása és beillesztése**  
- **Az Internet Explorer korlátozott zóna .NET-keretrendszerének függő összetevői**  
- **Az Internet Explorer helyi számítógép zónája ne futtasson antimalware-t az aktív X vezérlőkön**
- **Az Internet Explorer titkosításának támogatása**  

*[Felülvizsgált]* [**Internet Explorer**](#internet-explorer):
- **Internet Explorer Internet Zone automatikus** Rákérdezés a fájlok letöltésére > az alapértelmezett érték most **le van tiltva**. Az előzetes verzióban ez engedélyezve értékre van állítva.

*[Új]* [**Távsegítség**](#remote-assistance):  
- **Távsegítség kérése** 
  - **Távsegítség által kért engedély**
  - **Jegy maximális élettartama**  
  - **Jegyek maximális időtartama**  
  - **E-Mail Meghívási módszere**


*[Új]* [**WIndows Defender**](#windows-defender):
- **Adobe Reader indítása alárendelt folyamatban**  
- **Office kommunikációs alkalmazások indítása alárendelt folyamatban** 

*[Új]* [ **Windows Defender-tűzfal**](#windows-defender-firewall)
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



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Windows Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Windows Defender SmartScreen. Enabling this policy turns off Windows Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Windows defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Windows Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Windows Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Windows Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Windows Defender Exploit Guard. Network protection is a feature of Windows Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Windows Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Windows Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Windows Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Windows Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Windows Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Windows Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Windows Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->
