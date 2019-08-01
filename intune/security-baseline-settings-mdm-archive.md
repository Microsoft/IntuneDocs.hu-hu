---
title: Az Intune MDM biztonsági alapkonfigurációi beállításainak archiválása a Windows 10 rendszerhez
titleSuffix: Microsoft Intune
description: A MDM biztonsági alapkonfigurációjának korábbi verzióinak archívuma a Windows 10 Microsoft Intune-vel való kezeléséhez
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7871fa6f8655ff02242135d04385984368d52625
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/31/2019
ms.locfileid: "68680091"
---
<!-- This article contains the exact baseline details for baseline versions that were previously published in security-baseline-settings-mdm.md.  -->

# <a name="archive-of-mdm-security-baseline-settings"></a>A MDM biztonsági alapkonfiguráció-beállításainak archívuma  

Tekintse meg az Intune MDM biztonsági alapkonfigurációjának archivált verzióira vonatkozó adatokat.  

Új MDM biztonsági alapértékek kiadásakor a beállítások előző listája a biztonsági alapkonfiguráció beállításai cikkből az archívumba kerül. Ezek a verziók továbbra is használhatók, és ez az Archívum nyújt segítséget a régebbi alapverziók alapértelmezett beállításainak megismeréséhez.

Ha egy alapkonfiguráció már nem támogatott a használathoz, a rendszer eltávolítja a cikkből.

- Az [aktuális Mdm biztonsági](security-baseline-settings-mdm.md) alaptervben elérhető beállítások megtekintése 
- Ismerje meg a [biztonsági](security-baselines.md)alapkonfigurációkat, valamint azt, hogyan frissítheti az alapkonfigurációt a biztonsági alapkonfigurációk profiljaiban.

## <a name="preview-mdm-security-baseline-for-october-2018"></a>Előnézet MDM biztonsági alapterv október 2018  

*Ezt az alapkonfigurációt a Mdm biztonsági alapkonfiguráció felülírja [a május 2019](security-baseline-settings-mdm.md)*

### <a name="above-lock"></a>Zárolás felett  

További információ: [Policy CSP-AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) a Windows dokumentációjában.  

- **Bejelentési értesítések megjelenítésének tiltása**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy az alkalmazás értesítései megjelenjenek a zárolási képernyőn. Ha engedélyezi ezt a házirend-beállítást, akkor a zárolási képernyőn nem jelennek meg alkalmazás-értesítések. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználók kiválaszthatják, hogy mely alkalmazások jelenítsék meg az értesítéseket a zárolási képernyőn.
  
  **Alapértelmezett**: Igen  

### <a name="app-runtime"></a>Alkalmazás futtatókörnyezete  

További információ: [Policy CSP-AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) a Windows dokumentációjában.  

- **Microsoft-fiókok választhatók a Windows áruházbeli alkalmazásokhoz**  
  Ezzel a házirend-beállítással szabályozhatja, hogy a Microsoft-fiókok választhatók-e olyan Windows áruházbeli alkalmazásokhoz, amelyekhez fiók szükséges a bejelentkezéshez. Ez a szabályzat csak az azt támogató Windows áruházbeli alkalmazásokat érinti. Ha engedélyezi ezt a házirend-beállítást, a Windows áruházbeli alkalmazások, amelyek általában a bejelentkezéshez Microsoft-fiók igényelnek, lehetővé teszik a felhasználók számára a vállalati fiókkal való bejelentkezést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználóknak Microsoft-fiók kell bejelentkezniük.  
  
  **Alapértelmezett**: Enabled  

### <a name="application-management"></a>Alkalmazások kezelése  

További információ: [Policy CSP-ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) a Windows dokumentációjában.  

- **Játék DVR blokkolása (csak asztali verzió)**  
  Annak konfigurálása, hogy engedélyezett-e a játékok rögzítése és közvetítése.
  
  **Alapértelmezett**: Igen  

### <a name="auto-play"></a>Automatikus lejátszás  

További információ: [Policy CSP-Robotpilota](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) a Windows dokumentációjában.  

- **Automatikus lejátszás alapértelmezett automatikus futtatási viselkedése**  
  Ez a beállítás hatással van az automatikus futtatási parancsok alapértelmezett viselkedésére. Az automatikus futtatási parancsok az Autorun. inf fájlban tárolódnak, és a telepítőprogramokat vagy más rutinokat indíthatnak el. Ha ez a *beállítás engedélyezve van*, a rendszergazdák megváltoztathatják a Windows Vista vagy újabb rendszert futtató eszközök alapértelmezett automatikus futtatási viselkedését. A viselkedés beállítható a következőre: a) teljesen letilthatja az automatikus futtatási parancsokat, vagy b) visszatérhet a Windows Vista előtti működésre, amely automatikusan végrehajtja az Autorun parancs futtatását. Ha a beállítás letiltva vagy *nincs konfigurálva*értékre van állítva, akkor a Windows Vista vagy újabb rendszerű eszközök megkérik a felhasználót, hogy az Autorun parancs fusson.
  
  **Alapértelmezett**: Végrehajtás mellőzése  
  
- **Automatikus lejátszási mód**  
  Ez a házirend-beállítás lehetővé teszi az automatikus lejátszás funkció kikapcsolását. Az automatikus lejátszás megkezdi a meghajtóról való beolvasást, amint adathordozót szúr be a meghajtóba. Ennek eredményeképpen a programok telepítési fájlja és a hanganyagokon megjelenő zene azonnal elindul. A Windows XP SP2 előtt az automatikus lejátszási szolgáltatás alapértelmezés szerint le van tiltva a cserélhető meghajtókon, például a hajlékonylemez-meghajtón (de nem a CD-ROM-meghajtón) és a hálózati meghajtókon. A Windows XP SP2 verziótól kezdődően az automatikus lejátszás engedélyezve van a cserélhető meghajtókon, beleértve a zip-meghajtókat és néhány USB háttértár-eszközt is. Ha engedélyezi ezt a házirend-beállítást, az automatikus lejátszási funkció le van tiltva a CD-ROM-és cserélhető adathordozó-meghajtókon, vagy le van tiltva az összes meghajtón. Ezzel a házirend-beállítással a további típusú meghajtókon letiltja az Automatikus lejátszást. Ezzel a beállítással nem engedélyezheti az Automatikus lejátszást azon meghajtókon, amelyeken a szolgáltatás alapértelmezés szerint le van tiltva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az automatikus lejátszás engedélyezve van. Megjegyezés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználói konfigurációs mappákban is megjelenik. Ha a házirend-beállítások ütköznek, a számítógép konfigurációjában a házirend-beállítás elsőbbséget élvez a felhasználói konfiguráció házirend-beállításával szemben.
  
  **Alapértelmezett**: Letiltva

- **Nem mennyiségi eszközök automatikus lejátszásának letiltása**  
  Ez a házirend-beállítás nem engedélyezi az Automatikus lejátszást az MTP-eszközök, például a kamerák vagy a telefonok számára. Ha engedélyezi ezt a házirend-beállítást, az automatikus lejátszás nem engedélyezett MTP-eszközökhöz, például fényképezőgépekhez vagy telefonokhoz. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az automatikus lejátszás engedélyezve van a nem mennyiségi eszközökhöz.
  
  **Alapértelmezett**: Enabled  

### <a name="bitlocker"></a>BitLocker  

További információ: [Policy CSP-BitLocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) a Windows dokumentációjában.  

- **Bites zárolás cserélhető meghajtó házirendje**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, konfigurálhat egy titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtók, az operációsrendszer-meghajtók és a cserélhető adatmeghajtók számára egyenként. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.

  A cserélhető meghajtókra vonatkozó biztonsági szabályzatok esetében konfigurálja a következő beállításokat:

  - **Titkosítás megkövetelése írási hozzáféréshez**  
    **Alapértelmezett**: Igen  

  - **Titkosítási módszer**  
    **Alapértelmezett**: AES 256bit CBC  

- **Bit Locker rögzített meghajtó szabályzata**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, beállíthatja a titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtókhoz, az operációsrendszer-meghajtókhoz és a cserélhető adatmeghajtókhoz. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  
 
  A bit Locker rögzített meghajtó házirendje beállításnál adja meg a következő beállításokat: 
  - **Titkosítási módszer**  
    **Alapértelmezett**: AES 256bit XTS  

- **Bites zárolás rendszermeghajtó-házirendje**  
  Ezzel a házirend-beállítással szabályozható a titkosítási módszer és a titkosítás erőssége. A szabályzat értékei határozzák meg a BitLocker által a titkosításhoz használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, beállíthatja a titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtókhoz, az operációsrendszer-meghajtókhoz és a cserélhető adatmeghajtókhoz. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  

  A következő beállítások megadásával konfigurálhatja a rendszermeghajtó-házirendet:
  - **Titkosítási módszer**  
    **Alapértelmezett**: AES 256bit XTS  

### <a name="browser"></a>Browser  

További információ: [szabályzat CSP-böngésző](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) a Windows dokumentációjában.  

- **SmartScreen megkövetelése a Microsoft Edge-hez**  

  A Microsoft Edge a Windows Defender SmartScreen (bekapcsolva) használatával védi a felhasználókat a lehetséges adathalászat-csalások és kártevő szoftverek alapértelmezés szerint. Alapértelmezés szerint a felhasználók nem letilthatják (kikapcsolják) a Windows Defender SmartScreen szolgáltatását. A házirend engedélyezése kikapcsolja a Windows Defender SmartScreen szolgáltatást, és megakadályozza, hogy a felhasználók bekapcsolják azt. Ne konfigurálja ezt a házirendet úgy, hogy a felhasználók a Windows Defender SmartScreen be-vagy kikapcsolását választják.  
  
  **Alapértelmezett**: Igen  
  
- **Rosszindulatú hely elérésének letiltása**  

  Alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Windows Defender SmartScreen figyelmeztetéseit a potenciálisan kártékony webhelyekről, így azok továbbra is a webhelyre léphetnek. Ezzel a házirenddel azonban beállíthatja a Microsoft Edge-t, hogy megakadályozza a felhasználók számára a figyelmeztetések megkerülését, és blokkolja őket a helyről.
  
  **Alapértelmezett**: Igen  
  
- Nem **ellenőrzött fájlok letöltésének tiltása** Alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Windows Defender SmartScreen figyelmeztetéseit a potenciálisan kártékony fájlokról, így továbbra is letöltheti a nem ellenőrzött fájlokat. A szabályzat engedélyezése megakadályozza, hogy a felhasználók megkerüljék a figyelmeztetéseket, és blokkolja a nem ellenőrzött fájlok letöltését.
  
  **Alapértelmezett**: Igen  
  
- **A Password Manager letiltása**  
  Alapértelmezés szerint a Microsoft Edge automatikusan a Password Managert használja, így a felhasználók helyileg is elérhetik a jelszavakat. A szabályzat letiltása korlátozza a Microsoft Edge használatát a Password Manager használatával. Ne konfigurálja ezt a házirendet, ha engedélyezni szeretné a felhasználók számára a jelszavak helyi mentését és kezelését a Password Manager használatával.
  
  **Alapértelmezett**: Igen  
  
- **Tanúsítvány-hibák felülbírálásának megakadályozása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó figyelmen kívül hagyja a böngészést megszakító SSL/Transport Layer Security (SSL/TLS) tanúsítványokat (például a "lejárt", a "visszavont" vagy a "név eltérése" hibákat) az Internet Explorerben. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem folytathatja a böngészést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó dönthet úgy, hogy figyelmen kívül hagyja a tanúsítvány hibáit, és folytatja a böngészést.
  
  **Alapértelmezett**: Igen  

### <a name="connectivity"></a>Kapcsolat  

További információ: [Policy CSP – kapcsolat](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) a Windows dokumentációjában.  

- **Internetes letöltés letiltása a webes közzététel és az online rendezési varázslók számára**  
  Ezzel a házirend-beállítással adható meg, hogy a Windows letöltse-e a szolgáltatók listáját a webes közzétételi és az online rendezési varázslókhoz. Ezek a varázslók lehetővé teszik a felhasználók számára, hogy kiválasszák azon vállalatok listáját, amelyek olyan szolgáltatásokat biztosítanak, mint például az online tárterület és a fényképészeti nyomtatás. Alapértelmezés szerint a Windows a beállításjegyzékben megadott szolgáltatók mellett a Windows-webhelyről letöltött szolgáltatókat jeleníti meg. Ha engedélyezi ezt a házirend-beállítást, a Windows nem tölti le a szolgáltatókat, és csak azok a szolgáltatók jelennek meg, amelyek a helyi beállításjegyzékben vannak gyorsítótárazva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer letölti a szolgáltatók listáját, amikor a felhasználó a webes közzétételi vagy online rendezési varázslót használja. További információ a szolgáltatók beállításjegyzékbeli megadásáról: a webes közzététel és az online rendezés varázsló dokumentációja.  
  
  **Alapértelmezett**: Enabled  

- **A nyomtatóillesztők HTTP-n keresztüli letöltésének letiltása**  
  Ezzel a házirend-beállítással megadható, hogy az ügyfél letöltse-e a nyomtatóillesztő-csomagokat HTTP-n keresztül. HTTP-nyomtatás beállításához a nem beérkező illesztőprogramokat HTTP-n keresztül kell letölteni. Megjegyezés: Ez a házirend-beállítás nem akadályozza meg, hogy az ügyfél az intraneten vagy az interneten keresztül HTTP-n keresztül nyomtasson a nyomtatókra. Csak a helyileg telepített illesztőprogramok letöltését tiltja le. Ha engedélyezi ezt a házirend-beállítást, a nyomtatóillesztők nem tölthetők le HTTP-n keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználók HTTP-n keresztül tölthetnek le nyomtatóillesztőket.
  
  **Alapértelmezett**: Enabled  

### <a name="credentials-delegation"></a>Hitelesítő adatok delegálása  

További információ: [Policy CSP-CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) a Windows dokumentációjában.  

- **Nem exportálható hitelesítő adatok távoli gazdagép-delegálása**  
  A távoli gazdagép lehetővé teszi a nem exportálható hitelesítő adatok delegálását. A hitelesítő adatok delegálásakor az eszközök a hitelesítő adatok exportálható verzióját biztosítják a távoli gazdagép számára, amely lehetővé teszi a felhasználók számára a távoli gazdagépen lévő támadók által a hitelesítő adatok ellopásának kockázatát. Ha engedélyezi ezt a házirend-beállítást, a gazdagép támogatja a korlátozott rendszergazdai vagy távoli hitelesítő adatok Guard üzemmódot. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a korlátozott felügyelet és a távoli hitelesítőadat-őr mód nem támogatott. A felhasználónak mindig meg kell adnia a hitelesítő adatait a gazdagépen.  

  
  **Alapértelmezett**: Enabled  

### <a name="credentials-ui"></a>Hitelesítő adatok felhasználói felülete  

További információ: [Policy CSP-CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) a Windows dokumentációjában.  

- **Rendszergazdák számbavétele** Ezzel a házirend-beállítással szabályozható, hogy a rendszergazdai fiókok megjelenjenek-e, amikor egy felhasználó egy futó alkalmazást próbál meg emelni. Alapértelmezés szerint a rendszergazdai fiókok nem jelennek meg, amikor a felhasználó egy futó alkalmazást próbál meg emelni. Ha engedélyezi ezt a házirend-beállítást, a számítógép összes helyi rendszergazdai fiókja megjelenik, így a felhasználó kiválaszthatja az egyiket, és megadhatja a megfelelő jelszót. Ha letiltja ezt a házirend-beállítást, a felhasználóknak mindig meg kell adnia egy felhasználónevet és egy jelszót a jogosultságszint-emeléshez.  

  
  **Alapértelmezett**: Letiltva  

### <a name="data-protection"></a>Adatvédelem  

További információ: [Policy CSP-DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) a Windows dokumentációjában.  

- **Közvetlen memória-hozzáférés letiltása**  
  Ezzel a házirend-beállítással letilthatja a közvetlen memória-hozzáférést (DMA) az összes melegen csatlakoztatható PCI-porthoz, amíg a felhasználó be nem jelentkezik a Windowsba. Miután a felhasználó bejelentkezik, a Windows feljegyzi a gazdagéphez csatlakozó PCI-portokhoz csatlakozó PCI-eszközöket. Minden alkalommal, amikor a felhasználó zárolja a gépet, a rendszer letiltja a DMA-t a gyermekek nélküli gyors csatlakozású PCI-portok esetében, amíg a felhasználó újra be nem jelentkezik. A gép zárolásának feloldása után már enumerált eszközök továbbra is működni fognak, amíg le nem húzta a gépet. Ez a házirend-beállítás csak akkor lép érvénybe, ha a BitLocker vagy az eszköz titkosítása engedélyezve van.
  
  
  **Alapértelmezett**: Igen  

### <a name="device-guard"></a>Device Guard  

További információ: [Policy CSP-DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) a Windows dokumentációjában.  

- **Hitelesítőadat-őr**  
  Ezzel a beállítással a felhasználók bekapcsolhatják a hitelesítő adatokat a virtualizálás-alapú biztonsággal a hitelesítő adatok védelme érdekében a következő újraindításkor.
   
  **Alapértelmezett**: Engedélyezés UEFI-zárral 

- **Virtualizációs alapú biztonság engedélyezése**  </br>
  A virtualizálás-alapú biztonság (VBS) bekapcsolása a következő újraindításkor. A virtualizálás-alapú biztonság a Windows hipervizorral nyújt támogatást biztonsági szolgáltatásokhoz.
  
  **Alapértelmezett**: Igen  

- **Rendszerőr elindítása**    
  **Alapértelmezett**: Enabled  

### <a name="device-installation"></a>Eszköz telepítése  

További információ: [Policy CSP-DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) a Windows dokumentációjában.  

- **Hardvereszközök telepítése eszköz-azonosítók alapján**  
  Ezzel a házirend-beállítással megadható azoknak az eszközöknek a Plug and Play-azonosítói és-kompatibilis azonosítói, amelyek nem telepíthetők a Windows rendszerben. Ez a házirend-beállítás elsőbbséget élvez minden más olyan házirend-beállítással szemben, amely lehetővé teszi, hogy a Windows telepítsen egy eszközt. Ha engedélyezi ezt a házirend-beállítást, a Windows megakadályozza, hogy olyan eszközt telepítsen, amelynek hardver-azonosítója vagy kompatibilis azonosítója megjelenik a létrehozott listában. Ha engedélyezi ezt a házirend-beállítást egy távoli asztali kiszolgálón, a házirend-beállítás a megadott eszközök távoli asztali ügyfélről a távoli asztali kiszolgálóra való átirányítását befolyásolja. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az eszközök az engedélyezettnek megfelelően telepíthetik és frissíthetik az eszközöket, és más házirend-beállítások is megtiltják azokat.
  
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
  
  **Alapértelmezett**: Hardvereszköz telepítésének letiltása  

  Ha a *hardveres eszköz telepítésének letiltása* lehetőség van kiválasztva, a következő beállítások érhetők el.
  - **A megfelelő hardvereszközök eltávolítása**    
  Ez a beállítás csak akkor érhető el, ha a *telepítési osztályok által telepített hardvereszközök telepítése* *blokkolja a hardvereszközök telepítését*.  

    **Alapértelmezett**: *Nincs alapértelmezett konfiguráció*  

  - **A letiltott hardveres eszközök azonosítói**  
    Ez a beállítás csak akkor érhető el, ha a *telepítési osztályok által telepített hardvereszközök telepítése* *blokkolja a hardvereszközök telepítését*.
    
    **Alapértelmezett**: *Nincs alapértelmezett konfiguráció*  

### <a name="device-lock"></a>Eszköz zárolása  

További információ: [Policy CSP-DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) a Windows dokumentációjában.  

- **Kamera használatának megakadályozása**  
  Letiltja a zárolási képernyő kamera-kapcsolóját a számítógép beállításaiban, és megakadályozza, hogy a rendszer meghívja a kamerát a zárolási képernyőn. Alapértelmezés szerint a felhasználók a zárolási képernyőn is engedélyezhetik a rendelkezésre álló kamera meghívását. Ha engedélyezi ezt a beállítást, a felhasználók többé nem fogják tudni engedélyezni vagy letiltani a zárolási képernyő kamera-hozzáférését a számítógép beállításaiban, és a kamerát nem lehet meghívni a zárolási képernyőn. 
  
  **Alapértelmezett**: Enabled  

- **Jelszó megkövetelése**  
  Megadja, hogy engedélyezve van-e az eszköz zárolása.
  
  **Alapértelmezett**: Igen  
  
  Ha a *jelszó* megkövetelése *Igen*értékre van állítva, a következő beállítások érhetők el.

  - **Jelszó minimális karakterkészletének száma**  
    Az erős PIN-kódokhoz vagy jelszóhoz szükséges összetett elemek (kis-és nagybetűk, számok és írásjelek) száma. A PIN-kód a következő viselkedést alkalmazza az asztali és a mobileszközök esetében: 1 – csak 2 számjegyből és kisbetűkből álló számjegyek szükségesek 3 számjegyű, kisbetűket és nagybetűket. Asztali Microsoft-fiókok és tartományi fiókok esetében nem támogatott. 4 számjegyű, kisbetűket, nagybetűket és speciális karaktereket kell megadni. Az asztali verzióban nem támogatott. Az alapértelmezett érték az 1. 
    
    **Alapértelmezett**: 3  
  
  - **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**  
    Az eszköz törlése előtt engedélyezett hitelesítési hibák száma. A 0 érték letiltja az eszköz törlési funkcióját.
    
    **Alapértelmezett**: 10  
  
  - **Jelszó lejárata (nap)**  
    A jelszó maximális élettartama házirend-beállítás határozza meg, hogy mennyi ideig használható a jelszó, mielőtt a rendszer megköveteli a felhasználótól, hogy módosítsa azt. Beállíthatja, hogy a jelszavak egy 1 és 999 közötti számú nap elteltével lejárnak, vagy megadhatja, hogy a jelszavak soha ne járjanak le, ha a napok számát 0-ra állítja. Ha a jelszó maximális kora 1 és 999 nap közé esik, a jelszó minimális élettartama nem lehet kisebb, mint a jelszó maximális kora. Ha a jelszó maximális élettartama 0, akkor a jelszó minimális kora 0 és 998 nap közötti érték lehet.
    
    **Alapértelmezett**: 60  
  
  - **Kötelező jelszótípus**  
    Meghatározza, hogy milyen típusú PIN-kód vagy jelszó szükséges.
    
    **Alapértelmezett**: Alfanumerikus  
  
  - **Jelszó minimális hossza**  
    A jelszó minimális hossza házirend-beállítás határozza meg, hogy hány karakterből állhat egy felhasználói fiók jelszava. Megadhat egy 1 és 14 karakter közötti értéket, vagy megadhatja, hogy nincs szükség jelszóra, ha a karakterek számát 0-ra állítja.
    
    **Alapértelmezett**: 8  

  - **Egyszerű jelszavak letiltása**  
    Megadja, hogy engedélyezett-e a PIN-kód vagy a jelszavak (például "1111" vagy "1234"). Az asztal esetében a képjelszavak használatát is szabályozza.
    
    **Alapértelmezett**: Igen  
      *Az Igen beállítás meggátolja az egyszerű jelszavak használatát.* 

  - **Korábbi jelszavak újbóli használatának tiltása**  
    Meghatározza, hogy hány jelszó tárolható a nem használható előzményekben. Az érték tartalmazza a felhasználó aktuális jelszavát. Ha például az *1* értékre kattint, a felhasználó nem tudja újból felhasználni a jelenlegi jelszavát új jelszó kiválasztásakor. Az *5* beállítás azt jelenti, hogy a felhasználók nem állíthatják be az új jelszavukat a jelenlegi jelszavuk vagy az előző négy jelszavuk közül.
    
    **Alapértelmezett**: 24  

- **A diavetítés megakadályozása**  
  Letiltja a zárolási képernyő görgetősávjának beállításait a számítógép beállításaiban, és megakadályozza a diavetítés lejátszását a zárolási képernyőn. Alapértelmezés szerint a felhasználók engedélyezheti a diavetítést, amely a gép zárolása után fog futni. Ha engedélyezi ezt a beállítást, a felhasználók nem módosíthatják a számítógép beállításaiban a diavetítés beállításait, és nem indíthatnak el diavetítést.
  
    **Alapértelmezett**: Enabled  
    *Az Engedélyezve beállítás megadásával megakadályozhatja a diavetítés futtatását.* 

- **Jelszó minimális kora (nap)**  
  A jelszó minimális élettartama házirend-beállítás határozza meg azt az időtartamot (nap), ameddig a felhasználónak meg kell változtatnia a jelszót. 1 és 998 nap közötti értéket adhat meg, vagy a jelszó módosításait azonnal engedélyezheti, ha a napok számát 0-ra állítja. A jelszó minimális élettartama nem lehet kisebb, mint a jelszó maximális kora, kivéve, ha a jelszó maximális élettartama 0 értékű, ami azt jelzi, hogy a jelszavak soha nem járnak le. Ha a jelszó maximális élettartama 0, akkor a jelszó minimális kora 0 és 998 közötti értékre állítható be.
  
    **Alapértelmezett**: 1  

### <a name="event-log-service"></a>Eseménynapló szolgáltatás  

További információ: [Policy CSP-EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) a Windows dokumentációjában.  

- **Biztonsági napló maximális fájlmérete KB-ban**  
  Ezzel a házirend-beállítással adható meg a naplófájl maximális mérete kilobájtban. Ha engedélyezi ezt a házirend-beállítást, a naplófájlok maximális méretét 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) értékre állíthatja kilobájtos növekményekben. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a naplófájl maximális mérete a helyileg konfigurált értékre van állítva. Ezt az értéket a helyi rendszergazda módosíthatja a napló tulajdonságai párbeszédpanelen, és az alapértelmezett érték 20 megabájt.
  
   **Alapértelmezett**: 196608  

- **Rendszernapló maximális fájlmérete (KB)**  
  Ezzel a házirend-beállítással adható meg a naplófájl maximális mérete kilobájtban. Ha engedélyezi ezt a házirend-beállítást, a naplófájlok maximális méretét 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) értékre állíthatja kilobájtos növekményekben. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a naplófájl maximális mérete a helyileg konfigurált értékre van állítva. Ezt az értéket a helyi rendszergazda módosíthatja a napló tulajdonságai párbeszédpanelen, és az alapértelmezett érték 20 megabájt.
  
  **Alapértelmezett**: 32768  

- **Alkalmazásnapló maximális fájlmérete KB-ban**  
  Ezzel a házirend-beállítással adható meg a naplófájl maximális mérete kilobájtban. Ha engedélyezi ezt a házirend-beállítást, a naplófájlok maximális méretét 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) értékre állíthatja kilobájtos növekményekben. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a naplófájl maximális mérete a helyileg konfigurált értékre van állítva. Ezt az értéket a helyi rendszergazda módosíthatja a napló tulajdonságai párbeszédpanelen, és az alapértelmezett érték 20 megabájt.
  
  **Alapértelmezett**: 32768  

### <a name="experience"></a>Élmény  

További információ: [Policy CSP –](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) a Windows dokumentációjában található tapasztalat.  

- **A Windows reflektorfény letiltása**  
  Lehetővé teszi, hogy a rendszergazdák kikapcsolják az összes Windows reflektorfény-funkciót – ablak Reflektorfényben a zárolási képernyőn, a Windows-tippeket, a Microsoft fogyasztói funkcióit és egyéb kapcsolódó funkciókat.
  
  **Alapértelmezett**: Igen  

  Ha a *Windows reflektorfény letiltása* *Igen*értékre van állítva, a következő beállítások érhetők el.
  
  - **Harmadik féltől származó javaslatok letiltása a Windows reflektorfényben**  
    Megadja, hogy engedélyezi-e a harmadik féltől származó szoftvergyártók alkalmazás-és tartalmi javaslatainak használatát a Windows reflektorfényben, például a zárolási képernyő Spotlight, a javasolt alkalmazások a Start menüben és a Windows-tippek. A felhasználók továbbra is láthatják a Microsoft funkcióit, alkalmazásait és szolgáltatásait.
      
    **Alapértelmezett**: Igen  
  - **A fogyasztói sajátosságok letiltása**  
    Lehetővé teszi a rendszergazdáknak, hogy csak a felhasználók számára, például a Start Suggestions, a tagsági értesítések, az OOBE utáni alkalmazások telepítése és a csempék átirányítása céljából bekapcsolják a felhasználói élményeket.
    
    **Alapértelmezett**: Igen  


### <a name="exploit-guard"></a>Védelem kiaknázása  

További információ: [Policy CSP-ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) a Windows dokumentációjában.  

- **Védelem XML-kódjának kiaknázása**  
  Lehetővé teszi a rendszergazda számára egy olyan konfiguráció kiküldését, amely a kívánt rendszer-és alkalmazás-kockázatcsökkentő beállításokat jelöli a szervezet összes eszközén. A konfigurációt egy XML-fájl jelképezi. A védelem kiaknázásával megvédheti az eszközöket olyan kártevők ellen, amelyek kihasználják a kiaknázást és a fertőzést. A Windows biztonsági alkalmazás vagy a PowerShell használatával hozhat létre kockázatcsökkentő (más néven konfiguráció) készletet. Ezt követően exportálhatja ezt a konfigurációt XML-fájlként, és megoszthatja azt több, a hálózaton található géppel, hogy mindegyiknek ugyanazokat a kockázatcsökkentő beállításokat adja meg. Egy meglévő EMET konfigurációs XML-fájlt is konvertálhat, és importálhatja a biztonsági rés kiaknázása konfigurációs XML-fájlba.
  
  **Alapértelmezett**: *A minta XML-fájlja megadva* 
 
### <a name="file-explorer"></a>Fájlkezelő  

További információ: [Policy CSP-fájlkezelő](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) a Windows dokumentációjában.  

- **Az adatvégrehajtás-megelőzés letiltása**  
  Az adatvégrehajtás megakadályozása lehetővé teszi bizonyos örökölt beépülőmodul-alkalmazások működésének leállítását az Explorer leállítása nélkül.
  
  **Alapértelmezett**: Letiltva  
   
- **A kupac megszakításának letiltása a Sérüléskor**  
  Ha letiltja a megszakított adatvesztést a sérülés miatt, bizonyos örökölt beépülőmodul-alkalmazások az Intéző azonnali leállítása nélkül is működhetnek, bár a tallózó a későbbiekben is váratlanul leállhat.
  
  **Alapértelmezett**: Letiltva  
    

### <a name="internet-explorer"></a>Internet Explorer  

További információ: [Policy CSP-InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) a Windows dokumentációjában.  

- **Internet Explorer Internet Zone-hozzáférés az adatforrásokhoz**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer hozzáférhet-e egy másik biztonsági zónából származó adatokhoz a Microsoft XML Parser (MSXML) vagy a ActiveX Data Objects (ADO) használatával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók betölthetnek egy olyan lapot a zónába, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a lap betöltését az MSXML vagy az ADO protokollt használó zónában a zóna egy másik helyéről származó adatok eléréséhez. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónája különböző tartományokból származó tartalmat húzhat a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy az egyik tartományból egy másik tartományba húzza a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer 9 és korábbi verzióiban a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél ugyanabban az ablakban található. A felhasználók nem változtathatják meg ezt a beállítást az Internetbeállítások párbeszédpanelen.
  
  **Alapértelmezett**: Letiltva
  
- **Az Internet Explorer-tanúsítvány címe nem megfelelő figyelmeztetés**  
  Ezzel a házirend-beállítással a tanúsítvány címe nem egyezik a biztonsági figyelmeztetéssel. Ha ez a házirend-beállítás be van kapcsolva, a rendszer figyelmezteti a felhasználót, amikor olyan biztonságos HTTP-(HTTPS-) webhelyeket látogat meg, amelyek egy másik webhely címeként kiállított tanúsítványokat jelennek meg Ez a figyelmeztetés segít megelőzni a hamisítás elleni támadásokat. Ha engedélyezi ezt a házirend-beállítást, a tanúsítvány címe nem megfelelő figyelmeztetés mindig megjelenik. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a tanúsítvány címe nem megfelelő figyelmeztetés jelenik-e meg (a Speciális lapon az Internet Vezérlőpulton).
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer korlátozott zónáinak kevésbé privilegizált helyei**  
  Ezzel a házirend-beállítással felügyelheti, hogy a webhelyek kevesebb jogosultsági szintű zónából, például internetes webhelyről is bejelentkezhetnek-e a zónába. Ha engedélyezi ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát. A biztonsági zóna a védelem által a zóna jogosultságszint-emelése biztonsági szolgáltatás által biztosított kiegészítő biztonsági réteg nélkül fog futni. Ha a legördülő listában a kérdés elemre kattint, egy figyelmeztetés jelenik meg a felhasználó számára, aki potenciálisan kockázatos navigálást végez. Ha letiltja ezt a házirend-beállítást, akkor a rendszer valószínűleg ártalmas navigálást végez. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a valószínűleg ártalmas navigálást. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer – korlátozott zóna – automatikus Rákérdezés a fájlok letöltésére**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználókat a nem felhasználó által kezdeményezett fájlok letöltésére Ettől a beállítástól függetlenül a felhasználók a fájl letöltése párbeszédpaneleket kapják meg a felhasználó által kezdeményezett letöltésekhez. Ha engedélyezi ezt a beállítást, a felhasználók egy fájl letöltése párbeszédpanelt kapnak az automatikus letöltési kísérletekhez. Ha letiltja vagy nem konfigurálja ezt a beállítást, a nem felhasználó által kezdeményezett fájlletöltés le van tiltva, és a felhasználók az értesítési sávot a fájl letöltése párbeszédpanel helyett láthatják. A felhasználók ezután rákattintanak az értesítési sávra a fájl letöltésének megadásához.
  
  **Alapértelmezett**: Letiltva
  
- **Internet Explorer Internet Zone .NET-keretrendszerre vonatkozó függő összetevők**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-ban nem aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy aláíratlan felügyelt összetevőket kíván-e végrehajtani. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláíratlan felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer aláíratlan felügyelt összetevőket fog végrehajtani.
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer internetes zónája csak a jóváhagyott tartományok TDC ActiveX-vezérlők használatát engedélyezi**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználó futtathat-e TDC ActiveX-vezérlőt a webhelyeken. Ha engedélyezi ezt a házirend-beállítást, a TDC ActiveX-vezérlő nem fog futni a zónában lévő webhelyekről. Ha letiltja ezt a házirend-beállítást, a TDC aktív X vezérlő az ebben a zónában lévő összes helyről futni fog.
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer korlátozott zónájának parancsfájlja kezdeményezte a Windowst**  
  Ezzel a házirend-beállítással felügyelheti a parancsfájl által kezdeményezett előugró ablakokat és windowsokat, amelyek tartalmazzák a címet és az állapotjelző sávokat. Ha engedélyezi ezt a házirend-beállítást, a Windows-korlátozások biztonsága nem lesz érvényes ebben a zónában. A biztonsági zóna a szolgáltatás által biztosított hozzáadott biztonsági réteg nélkül fut. Ha letiltja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja.
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer internetes zónája helyi elérési utat tartalmaz a fájlok kiszolgálóra való feltöltésekor**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer mikor küldje el a helyi elérési utat, amikor a felhasználó HTML-űrlapon keresztül tölt fel fájlokat. Ha a rendszer elküldje a helyi elérési utat, előfordulhat, hogy a kiszolgáló véletlenül nem tárt fel adatokat. Előfordulhat például, hogy a felhasználó asztaláról eljuttatott fájlok tartalmazzák a felhasználónevet az elérési út részeként. Ha engedélyezi ezt a házirend-beállítást, a rendszer az elérési út adatait akkor továbbítja, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha letiltja ezt a házirend-beállítást, a rendszer eltávolítja az elérésiút-információkat, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a rendszer elküldje-e az elérési utat, amikor feltölt egy fájlt egy HTML-űrlapon keresztül. Alapértelmezés szerint a rendszer az elérésiút-információkat elküldi.
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer fokozottan védett módban tiltja le a folyamatokat**  
  Ez a házirend-beállítás határozza meg, hogy az Internet Explorer 11 a 64 bites folyamatokat (nagyobb biztonság esetén) vagy 32 bites folyamatokat (a nagyobb kompatibilitás érdekében) használja-e a Windows rendszerű, 64 bites verzióin a fokozottan védett módban. Fontos! Előfordulhat, hogy néhány ActiveX-vezérlő és-eszköztár nem érhető el, ha 64 bites folyamatokat használ. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer 11 64 bites Tab-folyamatokat fog használni, amikor a Windows 64 bites verzióiban fokozottan védett módban fut. Ha letiltja ezt a házirend-beállítást, az Internet Explorer 11 32 bites Tab-folyamatokat fog használni, amikor a Windows 64 bites verzióiban fokozottan védett módban fut. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók az Internet Explorer beállításaival be-vagy kikapcsolhatják ezt a funkciót. Ez a funkció alapértelmezés szerint ki van kapcsolva.
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer – tanúsítvány-hibák figyelmen kívül hagyása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó figyelmen kívül hagyja a böngészést megszakító SSL/Transport Layer Security (SSL/TLS) tanúsítványokat (például a "lejárt", a "visszavont" vagy a "név eltérése" hibákat) az Internet Explorerben. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem folytathatja a böngészést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó dönthet úgy, hogy figyelmen kívül hagyja a tanúsítvány hibáit, és folytatja a böngészést.
  
  **Alapértelmezett**: Letiltva 
  
- **Internet Explorer Internet Zone XAML-fájlok betöltése**  
  Ezzel a házirend-beállítással kezelheti Extensible Application Markup Language-(XAML-) fájlok betöltését. A XAML egy XML-alapú deklaratív jelölési nyelv, amely gazdag felhasználói felületek és grafikák létrehozására szolgál, amelyek kihasználják a Windows megjelenítési alaprendszer. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a XAML-fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha a legördülő lista megadását kéri, a rendszer a felhasználótól kéri a XAML-fájlok betöltését. Ha letiltja ezt a házirend-beállítást, a XAML-fájlok nem töltődnek be az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó eldöntheti, hogy XAML-fájlokat kíván-e betölteni az Internet Explorerben.
  
  **Alapértelmezett**: Letiltás 
  
- **Internet Explorer Internet Zone automatikus Rákérdezés a fájlok letöltésére**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználókat a nem felhasználó által kezdeményezett fájlok letöltésére Ettől a beállítástól függetlenül a felhasználók a fájl letöltése párbeszédpaneleket kapják meg a felhasználó által kezdeményezett letöltésekhez. Ha engedélyezi ezt a beállítást, a felhasználók egy fájl letöltése párbeszédpanelt kapnak az automatikus letöltési kísérletekhez. Ha letiltja vagy nem konfigurálja ezt a beállítást, a nem felhasználó által kezdeményezett fájlletöltés le van tiltva, és a felhasználók az értesítési sávot a fájl letöltése párbeszédpanel helyett láthatják. A felhasználók ezután rákattintanak az értesítési sávra a fájl letöltésének megadásához.
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer – korlátozott zóna biztonsági figyelmeztetése potenciálisan nem biztonságos fájlokhoz**  
  Ezzel a házirend-beállítással szabályozható, hogy a "fájl-biztonsági figyelmeztetés megnyitása" üzenet jelenik-e meg, amikor a felhasználó megpróbál megnyitni egy végrehajtható fájlt vagy más potenciálisan nem biztonságos fájlt (például egy intranetes fájlmegosztást a fájlkezelő használatával). Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a rendszer biztonsági figyelmeztetés nélkül nyitja meg a fájlokat. Ha a legördülő lista megadását kéri, a rendszer biztonsági figyelmeztetést jelenít meg a fájlok megnyitása előtt. Ha letiltja ezt a házirend-beállítást, akkor ezek a fájlok nem nyílnak meg. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a számítógép hogyan kezelje ezeket a fájlokat. Alapértelmezés szerint ezek a fájlok le vannak tiltva a korlátozott zónában, amely engedélyezve van az intranetes és a helyi számítógép zónában, és az interneten és a megbízható zónákban való rákérdezésre van beállítva.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna helyközi parancsfájl-szűrő**  
  Ez a házirend azt szabályozza, hogy a helyek közötti parancsfájlok (XSS) szűrő felismeri-e és megakadályozza-e a helyek közötti parancsfájl-befecskendezést a zónában lévő webhelyeken. Ha engedélyezi ezt a házirend-beállítást, az XSS-szűrő be van kapcsolva a zónában található helyekhez, és az XSS-szűrő megkísérli blokkolni a helyek közötti parancsfájlok befecskendezését. Ha letiltja ezt a házirend-beállítást, az XSS-szűrő ki van kapcsolva az ebben a zónában lévő helyeknél, és az Internet Explorer engedélyezi a helyek közötti parancsfájlok befecskendezését.
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer tartalék SSL3**  
  Ezzel a házirend-beállítással letilthat egy nem biztonságos tartalékot az SSL 3,0-re. Ha ez a szabályzat engedélyezve van, az Internet Explorer az SSL 3,0-es vagy újabb verziójának használatával próbál csatlakozni a webhelyekhez, ha a TLS 1,0 vagy nagyobb hibát jelez. Azt javasoljuk, hogy ne engedélyezze a nem biztonságos tartalékot, hogy megakadályozza a személyes támadásokat. Ez a házirend nem befolyásolja, hogy mely biztonsági protokollok engedélyezettek. Ha letiltja ezt a házirendet, a rendszer az alapértelmezett értékeket használja.
  
  **Alapértelmezett**: Nincsenek helyek 
  
- **Az Internet Explorer zárolta az Internet zóna intelligens képernyőjét**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer korlátozott zóna alkalmazások és fájlok elindítása iFrame-ben**  
  Ezzel a házirend-beállítással felügyelheti, hogy az alkalmazások futtathatók-e, és hogy a fájlok letölthetők-e a zónában lévő lapok HTML-ben lévő IFRAME-hivatkozásból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatják az alkalmazásokat, és fájlokat tölthetnek le a zóna oldalain lévő IFRAME ELEMEKből. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy szeretné-e futtatni az alkalmazásokat, és letölti a fájlokat a zóna lapjain lévő IFRAME elemek közül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak alkalmazásokat futtatni és fájlokat letölteni a zónában lévő lapok IFRAME ELEMEIből. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a felhasználók futtassák az alkalmazásokat, és fájlokat töltsenek le a zónában lévő lapok IFRAME ELEMEIből.
  
  **Alapértelmezett**: Letiltás 
  
- **Internet Explorer – a nem gyakori fájlokra vonatkozó figyelmeztetések mellőzése az intelligens képernyőn**  
  Ezzel a házirend-beállítással adható meg, hogy a felhasználó megkerülhet-e a SmartScreen szűrőből származó figyelmeztetéseket. A SmartScreen szűrő figyelmezteti a felhasználót olyan végrehajtható fájlokra, amelyeket az Internet Explorer felhasználói általában nem töltenek le az internetről. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő figyelmeztetései letiltják a felhasználót. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó megkerülheti a SmartScreen szűrő figyelmeztetéseit.
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet zóna előugró ablak blokkolása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a nemkívánatos előugró ablakok megjelenjenek-e. Az előugró ablak akkor nyílik meg, amikor a végfelhasználó egy hivatkozásra kattint. Ha engedélyezi ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg. Ha letiltja ezt a házirend-beállítást, a rendszer nem akadályozza meg az előugró ablakok megjelenését. Ha nem konfigurálja ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg.
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer az konzisztens MIME-kezelést dolgozza fel**  
  Az Internet Explorer dinamikus bináris viselkedést tartalmaz: olyan összetevők, amelyek adott funkciókat biztosítanak azon HTML-elemek számára, amelyekhez csatolva vannak. Ezzel a házirend-beállítással szabályozható, hogy a bináris viselkedés biztonsági korlátozásának beállítása meggátolható vagy engedélyezve van-e. Ha engedélyezi ezt a házirend-beállítást, a rendszer a Fájlkezelőben és az Internet Explorer folyamataiban nem akadályozza meg a bináris viselkedést. Ha letiltja ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer folyamatainak bináris viselkedése is engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a bináris viselkedést a fájlkezelő és az Internet Explorer folyamataiban.
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer – korlátozott zóna – Java-engedélyek**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.
  
  **Alapértelmezett**: A Java letiltása  
    
  
- **Az Internet Explorer aktív X vezérlői védett módban**  
  Ezzel a házirend-beállítással megakadályozható, hogy az ActiveX-vezérlők védett módban fussanak, ha engedélyezve van a fokozottan védett mód. Ha a felhasználó olyan ActiveX-vezérlővel rendelkezik, amely nem kompatibilis a fokozottan védett móddal, és egy webhely megkísérli betölteni a vezérlőt, az Internet Explorer értesíti a felhasználót, és lehetővé teszi a webhely normál védelemmel ellátott módban történő futtatását. Ezzel a házirend-beállítással a rendszer letiltja ezt az értesítést, és az összes webhelyet fokozottan védett módban futtatja. A továbbfejlesztett védett mód további védelmet biztosít a rosszindulatú webhelyekkel szemben, ha 64 bites folyamatokat használ a Windows 64-bites verzióiban. A Windows 8 rendszerű számítógépek esetében a fokozottan védett mód is korlátozza az Internet Explorer által a beállításjegyzékből és a fájlrendszerből beolvasott helyeket. Ha a bővített védett mód engedélyezve van, és a felhasználó egy olyan webhelyre érkezik, amely nem kompatibilis a fokozottan védett móddal, az Internet Explorer értesíti a felhasználót, és lehetővé teszi a fokozottan védett üzemmód letiltását a következőre: adott webhelyre. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem teszi lehetővé a felhasználó számára a fokozottan védett üzemmód letiltását. Az összes védett mód webhelye fokozottan védett módban fog futni. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer értesíti a felhasználókat, és lehetőséget biztosít a nem kompatibilis ActiveX-vezérlőkkel rendelkező webhelyek normál védett módban való futtatására.  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának XAML-fájljainak betöltése**  
  Ezzel a házirend-beállítással kezelheti Extensible Application Markup Language-(XAML-) fájlok betöltését. A XAML egy XML-alapú deklaratív jelölési nyelv, amely gazdag felhasználói felületek és grafikák létrehozására szolgál, amelyek kihasználják a Windows megjelenítési alaprendszer. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a XAML-fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha a legördülő lista megadását kéri, a rendszer a felhasználótól kéri a XAML-fájlok betöltését. Ha letiltja ezt a házirend-beállítást, a XAML-fájlok nem töltődnek be az Internet Explorerben. A felhasználó nem változtathatja meg ezt a viselkedést. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó eldöntheti, hogy XAML-fájlokat kíván-e betölteni az Internet Explorerben.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer parancsfájlokkal ellátható biztonsági korlátozásokat dolgoz fel**  
  Az Internet Explorer lehetővé teszi a parancsfájlok számára a különböző típusú ablakok programozott megnyitását, átméretezését és áthelyezését. Az ablak korlátozásai biztonsági funkció korlátozza a felugró ablakokat, és letiltja azokat a Windows-verziókat, amelyekben a cím és az állapotjelző sávok nem láthatók a felhasználó számára, vagy eltorzítják a többi Windows-címet és állapotjelző sávot. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlba állított Windows minden folyamat esetében korlátozott. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a megírt Windows nem korlátozott.
  
  **Alapértelmezett**: Enabled   
  
- **Internet Explorer – korlátozott zóna – aktív X vezérlők és beépülő modulok futtatása**  
  Ezzel a házirend-beállítással felügyelheti, hogy az ActiveX-vezérlők és a beépülő modulok futhatnak-e a megadott zónán lévő lapokon. Ha engedélyezi ezt a házirend-beállítást, a vezérlők és a beépülő modulok felhasználói beavatkozás nélkül is futtathatók. Ha a legördülő listában a kérdés lehetőséget választotta, a rendszer felkéri a felhasználókat arra, hogy engedélyezzék a vezérlők vagy a beépülő modul futtatását. Ha letiltja ezt a házirend-beállítást, a vezérlők és beépülő modulok nem futnak. Ha nem konfigurálja ezt a házirend-beállítást, a vezérlők és beépülő modulok nem futnak.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónájának parancsfájljában aktív X vezérlők biztonságosként vannak megjelölve parancsfájlok futtatásához**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy biztonságosként megjelölt ActiveX-vezérlő képes-e a parancsfájlok kezelésére. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok interakciója automatikusan, felhasználói beavatkozás nélkül is megtörténhet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a parancsfájlok interakcióját. Ha letiltja ezt a házirend-beállítást, a parancsfájlok interakciója nem történik meg. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl-interakció megakadályozása nem történik meg.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónájának bejelentkezési beállításai**  
  Ezzel a házirend-beállítással kezelheti a bejelentkezési beállítások beállításait. Ha engedélyezi ezt a házirend-beállítást, a következő bejelentkezési beállítások közül választhat. 
  - *Névtelen* – Névtelen bejelentkezés használata a http-hitelesítés letiltásához és a vendég fiók csak a Common Internet File System (CIFS) protokollhoz való használatához. 
  - A felhasználók felhasználói azonosítóinak és jelszavának lekérdezéséhez kérje a Felhasználónév és a jelszó megadását. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. 
  - *Automatikus bejelentkezés csak az intranet zónában* – ezzel a beállítással lekérdezheti a felhasználókat a többi zónában lévő felhasználói azonosítók és jelszavak számára. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. 
  - *Automatikus bejelentkezés a jelenlegi felhasználónévvel és jelszóval*– ezzel a beállítással megpróbálhatja bejelentkezni a Windows NT kérdéses válasz (más néven NTLM-hitelesítés) használatával. Ha a kiszolgáló támogatja a Windows NT kérdéses választ, a bejelentkezés a felhasználó hálózati felhasználónevét és jelszavát használja a bejelentkezéshez. Ha a kiszolgáló nem támogatja a Windows NT kérdéses választ, a rendszer lekérdezi a felhasználót, hogy megadja a felhasználónevet és a jelszót. 

  Ha letiltja ezt a házirend-beállítást, a bejelentkezés *csak az intranet zónában automatikus bejelentkezésre*van beállítva. Ha nem konfigurálja ezt a házirend-beállítást, a bejelentkezés a Felhasználónév és a jelszó megadására van beállítva.
  
  **Alapértelmezett**: Névtelen  
  
- **Az Internet Explorer megbízható zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer-kiszolgáló tanúsítvány-visszavonásának ellenőrzése**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer ellenőriznie fogja-e a kiszolgálók tanúsítványainak visszavonási állapotát. A rendszer visszavonja a tanúsítványokat, amikor azok sérülnek, vagy már nem érvényesek, és ez a beállítás védi a felhasználókat abban, hogy bizalmas adatokkal elküldjenek egy olyan webhelyre, amely hamis vagy nem biztonságos lehet. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer megtekinti, hogy a kiszolgálói tanúsítványok visszavonva lettek-e. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a kiszolgálói tanúsítványokat, hogy azok visszavonták-e őket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a kiszolgálói tanúsítványokat, hogy azok visszavonták-e őket.
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer Internet Zone less privilegizált helyek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a webhelyek a kevésbé privilegizált zónákból, például a tiltott helyekről is bejelentkezhetnek-e a zónába. Ha engedélyezi ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát. A biztonsági zóna a védelem által a zóna jogosultságszint-emelése biztonsági szolgáltatás által biztosított kiegészítő biztonsági réteg nélkül fog futni. Ha a legördülő listában a kérdés elemre kattint, egy figyelmeztetés jelenik meg a felhasználó számára, aki potenciálisan kockázatos navigálást végez. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza a valószínűleg ártalmas navigálást. Az Internet Explorer biztonsági funkciója ebben a zónában a zóna jogosultságszint-emelési funkciójának vezérlésével megadható. Ha nem konfigurálja ezt a házirend-beállítást, a kevesebb jogosultsági szintű zónából származó webhelyek megnyithatják az új ablakokat, vagy megkereshetik a zónát.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer – korlátozott zóna fájljának letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a fájlok letöltése engedélyezett-e a zónából. Ezt a beállítást az oldal zónája határozza meg, amely a letöltést okozza, nem pedig azt a zónát, amelyről a fájlt leszállítják. Ha engedélyezi ezt a házirend-beállítást, a fájlok a zónából tölthetők le. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza a fájlok letöltését a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza a fájlok letöltését a zónából.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna – az Authenticode-aláírással aláírt .NET-keretrendszerre támaszkodó összetevők futtatása**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-val aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláírt felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy végrehajtja-e az aláírt felügyelt összetevőket. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer megakadályozza az aktív X vezérlők felhasználónkénti telepítését**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy az ActiveX-vezérlők telepítése felhasználónkénti alapon történjen. Ha engedélyezi ezt a házirend-beállítást, az ActiveX-vezérlőket nem lehet felhasználónkénti alapon telepíteni. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor az ActiveX-vezérlők felhasználónkénti alapon telepíthetők.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megakadályozza az intelligens képernyő-szűrő kezelését**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó kezelje a SmartScreen szűrőt, amely figyelmezteti a felhasználót, ha a meglátogatott webhelyről ismert, hogy csalárd kísérletet tesz személyes adatok gyűjtésére az "adathalászat" vagy a kártevő szoftverek üzemeltetése során. Ha engedélyezi ezt a házirend-beállítást, a rendszer nem kéri a felhasználót a SmartScreen szűrő bekapcsolására. A szűrők engedélyezése listán nem szereplő összes webhely címét a rendszer automatikusan elküldi a Microsoftnak a felhasználó értesítése nélkül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer felszólítja a felhasználót, hogy döntse el, hogy bekapcsolja-e a SmartScreen szűrőt az első futtatási élményben.
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer feldolgozza a MIME-elemzések biztonsági funkcióját**  
  Ezzel a házirend-beállítással megadható, hogy az Internet Explorer MIME-elemzése megakadályozza-e egy típusú fájl egy veszélyesebb fájltípusra való előléptetését. Ha engedélyezi ezt a házirend-beállítást, a MIME-elemzés soha nem fogja előléptetni az egyik típusú fájlt veszélyesebb fájltípusra. Ha letiltja ezt a házirend-beállítást, az Internet Explorer folyamatai lehetővé teszik a MIME-elemzések számára, hogy egy adott típusú fájlt egy veszélyesebb fájltípusra ösztönözzék. Ha nem konfigurálja ezt a házirend-beállítást, a MIME-elemzés soha nem előlépteti az egyik típusú fájlt veszélyesebb fájltípusra.
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer – korlátozott zóna – aláírt aktív X vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók letölthetik-e az aláírt ActiveX-vezérlőket a zóna egy oldaláról. Ha engedélyezi ezt a házirendet, a felhasználók felhasználói beavatkozás nélkül tölthetik le az aláírt vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a nem megbízható közzétevők által aláírt vezérlőket szeretné-e letölteni. A megbízható közzétevők által aláírt kód csendesen le van töltve. Ha letiltja a házirend-beállítást, az aláírt vezérlők nem tölthetők le. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy letöltötte-e a nem megbízható közzétevők által aláírt vezérlőket. A megbízható közzétevők által aláírt kód csendesen le van töltve.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer automatikus kiegészítése**  
  Ez az automatikus kiegészítési funkció megjegyezheti és javasolhatja a felhasználóneveket és a jelszavakat az űrlapokon. Ha engedélyezi ezt a beállítást, a felhasználó nem változtathatja meg a "felhasználónevek és jelszavak az űrlapokon" vagy "a jelszavak mentése" üzenetet. Az űrlapokon lévő felhasználónevek és jelszavak automatikus teljes funkciója be van kapcsolva. El kell döntenie, hogy kiválasztja-e a "jelszó mentése" üzenetet. Ha letiltja ezt a beállítást, a felhasználó nem változtathatja meg a "felhasználónevek és jelszavak az űrlapokon" vagy a "kérdés a jelszavak mentéséhez" lehetőséget. Az űrlapokon lévő felhasználónevek és jelszavak automatikus teljes funkciója ki van kapcsolva. A felhasználó nem dönthet úgy is, hogy kéri a jelszavak mentését. Ha nem konfigurálja ezt a beállítást, a felhasználónak lehetősége van az automatikus kiegészítés bekapcsolására az űrlapokon a Felhasználónév és a jelszó megadására, és a jelszavak mentésére is lehetőség van. A beállítás megjelenítéséhez a felhasználók megnyitják az Internetbeállítások párbeszédpanelt, kattintson a tartalom fülre, és kattintson a beállítások gombra.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zónája a VBscript futtatásának engedélyezése**  
  Ezzel a házirend-beállítással eldöntheti, hogy a VBScript futtatható-e az adott Internet Explorer-zónákban lévő lapokon. A lehetőségek a következők: 
  - *Engedélyezés* – a VBScript az adott zónákban lévő lapokon, interakció nélkül fut. 
  - *Kérés* – az alkalmazottaknak meg kell adni, hogy engedélyezni kell-e a VBScript futtatását a zónában. 
  - A *disable* -VBScript nem fut a zónában. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a VBScript a megadott zónán belüli interakció nélkül fut. 
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónája csak jóváhagyott tartományokat engedélyez a TDC aktív X-vezérlők használatához**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználó futtathat-e TDC ActiveX-vezérlőt a webhelyeken. Ha engedélyezi ezt a házirend-beállítást, a TDC ActiveX-vezérlő nem fog futni a zónában lévő webhelyekről. Ha letiltja ezt a házirend-beállítást, a TDC aktív X vezérlő az ebben a zónában lévő összes helyről futni fog.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megbízható zónája nem futtat antimalware-t az aktív X vezérlőkön**  
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer helyi számítógép-zónájának Java-engedélyei**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély közepes biztonsági értékre van állítva.
  
  **Alapértelmezett**: A Java letiltása 
  
- Az **Internet Explorer intranetes zónája nem futtat antimalware** -t az aktív X vezérlőkön Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.
  
  **Alapértelmezett**: Letiltva  

- **Az Internet Explorer korlátozott zónájának Szkriptletek**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó futtathat-e Szkriptletek. Ha engedélyezi ezt a házirend-beállítást, akkor a felhasználó futtathat Szkriptletek. Ha letiltja ezt a házirend-beállítást, a felhasználó nem tudja futtatni a Szkriptletek. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer az értesítési sávot dolgozza fel**  
  Ezzel a házirend-beállítással felügyelheti, hogy az értesítési sáv megjelenjen-e az Internet Explorer folyamataihoz, ha a fájl-vagy programkódok telepítése korlátozott. Alapértelmezés szerint az értesítési sáv az Internet Explorer folyamataihoz jelenik meg. Ha engedélyezi ezt a házirend-beállítást, megjelenik az értesítési sáv az Internet Explorer folyamataihoz. Ha letiltja ezt a házirend-beállítást, az értesítési sáv nem jelenik meg az Internet Explorer folyamataihoz. Ha nem konfigurálja ezt a házirend-beállítást, az értesítési sáv nem jelenik meg az Internet Explorer folyamataihoz.
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer Internet Zone – aláírt ActiveX-vezérlők letöltése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók letölthetik-e az aláírt ActiveX-vezérlőket a zóna egy oldaláról. Ha engedélyezi ezt a házirendet, a felhasználók felhasználói beavatkozás nélkül tölthetik le az aláírt vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a nem megbízható közzétevők által aláírt vezérlőket szeretné-e letölteni. A megbízható közzétevők által aláírt kód csendesen le van töltve. Ha letiltja a házirend-beállítást, az aláírt vezérlők nem tölthetők le. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy letöltötte-e a nem megbízható közzétevők által aláírt vezérlőket. A megbízható közzétevők által aláírt kód csendesen le van töltve.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónájának intelligens képernyője**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer az elavult aktív X vezérlőknél az idő futtatása gombjának eltávolítása**  
  Ezzel a házirend-beállítással megakadályozhatja, hogy a felhasználók meglássák a "Futtatás ebben az időben" gombot, és az Internet Explorerben adott elavult ActiveX-vezérlőket futtasson. Ha engedélyezi ezt a házirend-beállítást, a felhasználók nem láthatják a figyelmeztető üzenet "Futtatás ideje" gombját, amely akkor jelenik meg, ha az Internet Explorer elavult ActiveX-vezérlőt blokkol. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználók az elavult ActiveX-vezérlőt blokkoló figyelmeztető üzenetben láthatják a "Futtatás ideje" gombot. Ha erre a gombra kattint, a felhasználó egyszer futtathatja az elavult ActiveX-vezérlőt. További információ: "elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárában.
  
  **Alapértelmezett**: Enabled 
  
- **Internet Explorer Internet Zone alkalmazások és fájlok elindítása iframe-ben**  
  Ezzel a házirend-beállítással felügyelheti, hogy az alkalmazások futtathatók-e, és hogy a fájlok letölthetők-e a zónában lévő lapok HTML-ben lévő IFRAME-hivatkozásból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatják az alkalmazásokat, és fájlokat tölthetnek le a zóna oldalain lévő IFRAME ELEMEKből. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy szeretné-e futtatni az alkalmazásokat, és letölti a fájlokat a zóna lapjain lévő IFRAME elemek közül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak alkalmazásokat futtatni és fájlokat letölteni a zónában lévő lapok IFRAME ELEMEIből. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy futtatják-e az alkalmazásokat, és fájlokat töltenek le a zóna lapjain lévő IFRAME elemek közül.
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer korlátozott zónája különböző tartományokban navigáljon a Windows és a keretek között**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet Zone – intelligens képernyő**  
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer zárolta a megbízható zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.
  
  **Alapértelmezett**: A Java letiltása 
  
- **Internet Explorer-ellenőrzési aláírások a letöltött programokban**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer ellenőrizze-e a digitális aláírásokat (amely azonosítja az aláírt szoftverek közzétevőjét, és ellenőrzi, hogy nem módosította vagy módosították-e) a felhasználó számítógépeken a végrehajtható programok letöltése előtt. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer megtekinti a végrehajtható programok digitális aláírásait, és megjeleníti azok identitását, mielőtt letölti őket a felhasználói számítógépekre. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem fogja megtekinteni a végrehajtható programok digitális aláírásait, vagy a felhasználói számítógépekre való letöltés előtt megjeleníti az identitását. Ha nem konfigurálja ezt a házirendet, az Internet Explorer nem fogja megtekinteni a végrehajtható programok digitális aláírásait, vagy a felhasználói számítógépekre való letöltés előtt megjeleníti az identitását.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónáinak parancsfájlkezelése webböngésző-vezérlőkkel**  
  Ezzel a házirend-beállítással megadható, hogy egy oldal képes-e a beágyazott WebBrowser vezérlők futtatására parancsfájl használatával. Ha engedélyezi ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés engedélyezett. Ha letiltja ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés nem engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a WebBrowser vezérlőhöz tartozó parancsfájlok elérését. Alapértelmezés szerint a WebBrowser vezérlőhöz való parancsfájl-hozzáférés csak a helyi gépen és az intranet zónában engedélyezett.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának helyközi parancsfájl-szűrője**  
  Ez a házirend azt szabályozza, hogy a helyek közötti parancsfájlok (XSS) szűrő felismeri-e és megakadályozza-e a helyek közötti parancsfájl-befecskendezést a zónában lévő webhelyeken. Ha engedélyezi ezt a házirend-beállítást, az XSS-szűrő be van kapcsolva a zónában található helyekhez, és az XSS-szűrő megkísérli blokkolni a helyek közötti parancsfájlok befecskendezését. Ha letiltja ezt a házirend-beállítást, az XSS-szűrő ki van kapcsolva az ebben a zónában lévő helyeknél, és az Internet Explorer engedélyezi a helyek közötti parancsfájlok befecskendezését.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónájának bináris és parancsfájl-viselkedései**  
  Ezzel a házirend-beállítással kezelheti a dinamikus bináris és parancsfájl-viselkedést: olyan összetevőket, amelyek olyan HTML-elemek speciális funkcióit ágyazzák be, amelyekhez csatolva vannak. Ha engedélyezi ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés is elérhető. Ha a rendszergazda által jóváhagyott lehetőséget választja a legördülő listában, a rendszer csak a bináris viselkedések biztonsági korlátozási szabályzatában szereplő, a rendszergazda által jóváhagyott viselkedések területen felsorolt viselkedéseket jeleníti meg. Ha letiltja ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés nem érhető el, ha az alkalmazások egyéni biztonsági kezelőt implementáltak. Ha nem konfigurálja ezt a házirend-beállítást, a bináris és a parancsfájl-viselkedés nem érhető el, ha az alkalmazások egyéni biztonsági kezelőt implementáltak.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer biztonsági beállításainak bejelölése**  
  Ezzel a házirend-beállítással kikapcsolhatja a biztonsági beállítások ellenőrzése funkciót, amely ellenőrzi, hogy az Internet Explorer biztonsági beállításai meghatározzák-e, hogy a beállítások az Internet Explorert veszélyeztetik-e. Ha engedélyezi ezt a házirend-beállítást, a szolgáltatás ki van kapcsolva. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a funkció be van kapcsolva.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer Internet zóna biztonsági figyelmeztetése potenciálisan nem biztonságos fájlokhoz**  
  Ezzel a házirend-beállítással szabályozható, hogy a "fájl-biztonsági figyelmeztetés megnyitása" üzenet jelenik-e meg, amikor a felhasználó megpróbál megnyitni egy végrehajtható fájlt vagy más potenciálisan nem biztonságos fájlt (például egy intranetes fájlmegosztást a fájlkezelő használatával). Ha engedélyezi ezt a házirend-beállítást, és a legördülő listát engedélyezi, a rendszer biztonsági figyelmeztetés nélkül nyitja meg a fájlokat. Ha a legördülő lista megadását kéri, a rendszer biztonsági figyelmeztetést jelenít meg a fájlok megnyitása előtt. Ha letiltja ezt a házirend-beállítást, akkor ezek a fájlok nem nyílnak meg. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a számítógép hogyan kezelje ezeket a fájlokat. Alapértelmezés szerint ezek a fájlok le vannak tiltva a korlátozott zónában, amely engedélyezve van az intranetes és a helyi számítógép zónában, és az interneten és a megbízható zónákban való rákérdezésre van beállítva.
  
  **Alapértelmezett**: Kérdés  
  
- **Az Internet Explorer intranetes zónájának Java-engedélyei**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély közepes biztonsági értékre van állítva.
  
  **Alapértelmezett**: Magas biztonság 
  
- **Az Internet Explorer elavult aktív X vezérlőket blokkol**  </br>
  Ez a házirend-beállítás határozza meg, hogy az Internet Explorer blokkolja-e az elavult ActiveX-vezérlőket. Az intranetes zónában soha nem blokkolja az elavult ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer leállítja az elavult ActiveX-vezérlők blokkolását. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer továbbra is blokkol bizonyos elavult ActiveX-vezérlőket. További információ: "elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárában.
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer korlátozott zóna felugró ablakának blokkolása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a nemkívánatos előugró ablakok megjelenjenek-e. Az előugró ablak akkor nyílik meg, amikor a végfelhasználó egy hivatkozásra kattint. Ha engedélyezi ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg. Ha letiltja ezt a házirend-beállítást, a rendszer nem akadályozza meg az előugró ablakok megjelenését. Ha nem konfigurálja ezt a házirend-beállítást, a legtöbb nemkívánatos előugró ablak nem jelenik meg.
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer az MK protokoll biztonsági korlátozását dolgozza fel**  
  Az MK protokoll biztonsági korlátozási házirendjének beállítása csökkenti a támadási felületet az MK protokoll megakadályozásával. Az MK protokollon tárolt erőforrások sikertelenek lesznek. Ha engedélyezi ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer nem fogja tudni letiltani az MK protokollt, és az MK protokollon tárolt erőforrások sikertelenek lesznek. Ha letiltja ezt a házirend-beállítást, az alkalmazások használhatják az MK protokoll API-ját. Az MK protokollon tárolt erőforrások a Fájlkezelőben és az Internet Explorer folyamataiban is működni fognak. Ha nem konfigurálja ezt a házirend-beállítást, a fájlkezelő és az Internet Explorer nem fogja tudni letiltani az MK protokollt, és az MK protokollon tárolt erőforrások sikertelenek lesznek.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megbízható zónájának Java-engedélyei**  </br>
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély alacsony biztonsági értékre van állítva.
  
  **Alapértelmezett**: Magas biztonság  
  
- **Az Internet Explorer korlátozott zónákon keresztüli parancsfájlkezelése Java-kisalkalmazások esetén**  
  Ezzel a házirend-beállítással felügyelheti, hogy a kisalkalmazások elérhetők-e a zónán belüli parancsfájlok számára. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok felhasználói beavatkozás nélkül automatikusan hozzáférhetnek a kisalkalmazásokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a parancsfájlok elérését a kisalkalmazásokhoz. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem férnek hozzá a kisalkalmazásokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok nem férnek hozzá a kisalkalmazásokhoz.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer letiltotta a korlátozott zóna Java-engedélyeit**  </br>
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.
  
  **Alapértelmezett**: A Java letiltása 
  
- **Az Internet Explorer internetes zónája csak a jóváhagyott tartományok számára engedélyezi az ActiveX-vezérlők használatát**  </br>
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer a felhasználótól az ActiveX-vezérlőt telepítő webhelytől eltérő webhelyeken is fusson. Ha engedélyezi ezt a házirend-beállítást, a rendszer arra kéri a felhasználót, hogy az ActiveX-vezérlők futtathatók legyenek a zónában található webhelyekről. A felhasználó dönthet úgy, hogy engedélyezi, hogy a vezérlő az aktuális helyről vagy az összes helyről fusson. Ha letiltja ezt a házirend-beállítást, a felhasználó nem látja a helyhez tartozó ActiveX-parancssort, és az ActiveX-vezérlők a zóna összes webhelyéről futtathatók.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer minden hálózati elérési utat tartalmaz**  
  Az Internet Explorer minden hálózati elérési utat tartalmaz
  
  **Alapértelmezett**: Letiltva 
  
- **Internet Explorer Internet zóna által védett üzemmód**  
  Ezzel a házirend-beállítással engedélyezheti a védett üzemmódot. A védett mód segít megvédeni az Internet Explorert a kihasznált biztonsági rések révén, ha csökkenti az Internet Explorer által a beállításjegyzékben és a fájlrendszerben írni kívánt helyeket. Ha engedélyezi ezt a házirend-beállítást, a védett mód be van kapcsolva. A felhasználó nem kapcsolhatja ki a védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a védett mód ki van kapcsolva. A felhasználó nem kapcsolhatja be a védett üzemmódot. Ha nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó be-vagy kikapcsolhatja a védett módot.
  
  **Alapértelmezett**: Engedélyezés 
  
- **Az Internet Explorer internetes zónájának inicializálása és a parancsfájlok aktív X vezérlők nem biztonságosakként vannak megjelölve**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer lezárta a korlátozott zóna intelligens képernyőjét**  </br>
  Ezzel a házirend-beállítással szabályozható, hogy a SmartScreen szűrő megvizsgálja-e a zónában található oldalakat a kártékony tartalomhoz. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő kártékony tartalmat keres az ebben a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a SmartScreen szűrő nem vizsgálja meg a zónában lévő lapokat a kártékony tartalomhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó megadhatja, hogy a SmartScreen szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz. Megjegyezés: Az Internet Explorer 7 programban ez a házirend-beállítás határozza meg, hogy az adathalászat-szűrő megvizsgálja-e a zónában lévő lapokat a kártékony tartalomhoz.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer összeomlásának észlelése**  
  Ezzel a házirend-beállítással kezelheti a bővítmények felügyeletének összeomlás-észlelési funkcióját. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer összeomlása a Windows XP Professional Service Pack 1 és korábbi verziókban is megjelenik, nevezetesen a Windows hibajelentés meghívásához. A Windows hibajelentés összes házirend-beállítása továbbra is érvényben marad. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a beépülő modul felügyeletének összeomlás-észlelési funkciója működőképes.
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet Zone Java-engedélyek**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, az engedély magas biztonságra van állítva.
  
  **Alapértelmezett**: A Java letiltása  
  
- **Internet Explorer – korlátozott zóna – aktív parancsfájlok**  
  Ezzel a házirend-beállítással felügyelheti, hogy a zóna oldalain lévő parancsfájl-kód fut-e. Ha engedélyezi ezt a házirend-beállítást, a rendszer automatikusan futtathatja a zónában lévő lapokon található parancsfájl kódját. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezzék-e a parancsfájlok futtatását a zónában lévő lapokon. Ha letiltja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a zóna lapjain lévő parancsfájl-kód fusson. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer megakadályozza, hogy a zóna lapjain lévő parancsfájl-kód ne fusson.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna bejelentkezési beállításai**  
  Ezzel a házirend-beállítással kezelheti a bejelentkezési beállítások beállításait. Ha engedélyezi ezt a házirend-beállítást, a következő bejelentkezési beállítások közül választhat. Névtelen bejelentkezés a HTTP-hitelesítés letiltásához és a vendég fiók csak a Common Internet File System (CIFS) protokollhoz való használatához. Kérje meg a felhasználónevet és a jelszót a felhasználók felhasználói azonosítók és jelszavak lekérdezéséhez. A felhasználó lekérdezése után ezeket az értékeket csendesen használhatja a munkamenet hátralévő részében. Automatikus bejelentkezés csak intranet zónában felhasználói azonosítók és jelszavak más zónákban való lekérdezéséhez. A felhasználó lekérdezése után ezek az értékek csendesen használhatók a munkamenet hátralevő részében. Automatikus bejelentkezés a jelenlegi felhasználónévvel és jelszóval a Windows NT kérdéses válasz (más néven NTLM-hitelesítés) használatával történő bejelentkezéshez. Ha a kiszolgáló támogatja a Windows NT kérdéses választ, a bejelentkezés a felhasználó hálózati felhasználónevét és jelszavát használja a bejelentkezéshez. Ha a kiszolgáló nem támogatja a Windows NT kérdéses választ, a rendszer lekérdezi a felhasználót, hogy megadja a felhasználónevet és a jelszót. Ha letiltja ezt a házirend-beállítást, a bejelentkezés csak az intranetes zónában automatikus bejelentkezésre van beállítva. Ha nem konfigurálja ezt a házirend-beállítást, akkor a bejelentkezés csak az intranetes zónában automatikus bejelentkezésre van beállítva.
  
  **Alapértelmezett**: Kérdés  
  
- **Az Internet Explorer korlátozott zónája lehetővé teszi a VBScript futtatását**  </br>  
  Ezzel a házirend-beállítással felügyelheti, hogy a VBScript futtatható-e az Internet Explorerben megadott zónán lévő lapokon. Ha a legördülő listában az Engedélyezés lehetőséget választotta, a VBScript felhasználói beavatkozás nélkül futtatható. Ha a legördülő listában a kérdés lehetőséget választotta, a felhasználóknak meg kell választaniuk, hogy engedélyezik-e a VBScript futtatását. Ha a legördülő listában a Letiltás lehetőséget választotta, a VBScript nem fut. Ha nem konfigurálja vagy letiltja ezt a házirend-beállítást, a VBScript megakadályozza a futtatását.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zónája különböző tartományokból származó tartalmat húzhat át a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer intranetes zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.
  
  **Alapértelmezett**: Letiltás 
  
- **Internet Explorer-Letöltés – készülékházak**  
  Ezzel a házirend-beállítással megakadályozható, hogy a felhasználó betöltse a hírcsatornáról a felhasználó számítógépére. Ha engedélyezi ezt a házirend-beállítást, a felhasználó nem állíthatja be a hírcsatorna-szinkronizálási motort úgy, hogy a csatorna tulajdonságlapján keresztül letöltse a bekerítést. A fejlesztők nem változtathatják meg a letöltési beállítást a hírcsatorna API-kon keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a felhasználó beállíthatja, hogy a hírcsatorna-szinkronizálási motor letöltse a bekerítést a hírcsatorna tulajdonságlapján. A fejlesztő a hírcsatorna API-jai segítségével módosíthatja a letöltési beállítást.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának aláíratlan aktív X vezérlők letöltése**  </br>
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zónája a különböző tartományokból származó tartalmakat a Windowson belül húzza**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer folyamatai korlátozzák az aktív X-telepítést**  </br>
  Ezzel a házirend-beállítással engedélyezheti, hogy a webböngésző vezérlőt futtató alkalmazások blokkolják az ActiveX-vezérlő telepítésének automatikus megadását. Ha engedélyezi ezt a házirend-beállítást, a webböngésző vezérlő letiltja az ActiveX-vezérlő telepítésének automatikus megadását minden folyamat esetében. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a webböngésző vezérlő nem blokkolja az ActiveX-vezérlő telepítésének automatikus megadását az összes folyamat esetében.
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer Internet Zone Szkriptletek** Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó futtathat-e Szkriptletek. Ha engedélyezi ezt a házirend-beállítást, akkor a felhasználó futtathat Szkriptletek. Ha letiltja ezt a házirend-beállítást, a felhasználó nem tudja futtatni a Szkriptletek. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer – korlátozott zóna – fájlok húzása vagy másolása és beillesztése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók beilleszthetnek-e fájlokat, vagy másolhatnak és beilleszthetnek fájlokat a zónán belüli forrásokból. Ha engedélyezi ezt a házirend-beállítást, a felhasználók áthelyezhetik a fájlokat, vagy automatikusan másolhatják és beilleszthetik a fájlokat a zónából. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat áthúzni vagy másolni. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudnak fájlokat húzni, vagy fájlokat másolni és beilleszteni a zónából. Ha nem konfigurálja ezt a házirend-beállítást, a rendszer lekérdezi a felhasználókat, hogy eldöntse, hogy a zónából kíván-e fájlokat húzni vagy másolni.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer szoftver, ha az aláírás érvénytelen** </br>
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználó telepíthet-e vagy futtathat-e szoftvert, például az ActiveX-vezérlőket és a fájlokat, még akkor is, ha az aláírás érvénytelen. Egy érvénytelen aláírás azt jelezheti, hogy valaki módosította a fájlt. Ha engedélyezi ezt a házirend-beállítást, a rendszer a felhasználókat az érvénytelen aláírással rendelkező fájlok telepítésére és futtatására kéri. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak és nem telepíthetnek érvénytelen aláírással rendelkező fájlokat. Ha nem konfigurálja ezt a házirendet, a felhasználók dönthetnek úgy, hogy érvénytelen aláírással futtatják vagy telepítik a fájlokat.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának másolása és beillesztése parancsfájl használatával** </br> Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájlok végezhetnek-e vágólap-műveletet (például Kivágás, másolás és beillesztés) egy adott régióban. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a vágólapon végez-e műveleteket. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónája különböző tartományokból származó tartalmat húzhat át a Windowsban**  
  Ezzel a házirend-beállítással beállíthatja, hogy a rendszer hogyan húzza át a tartalmat az egyik tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. Ha engedélyezi ezt a házirend-beállítást, és az Engedélyezés gombra kattint, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és a Letiltás gombra kattint, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél is különböző Windows-környezetben található. A felhasználók nem változtathatják meg ezt a beállítást. Ha az Internet Explorer 10 böngészőben letiltja ezt a házirend-beállítást, vagy nem konfigurálja, a felhasználók nem húzhatja a tartalmat egy tartományból egy másik tartományba, ha a forrás és a cél különböző Windows-környezetben található. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelen. Ha letiltja vagy nem konfigurálja ezt a házirendet az Internet Explorer 9 és a korábbi verzióiban, a felhasználók az egyik tartományból egy másik tartományba húzhatja a tartalmat, ha a forrás és a cél különböző Windows-alapú. A felhasználók nem változtathatják meg ezt a beállítást.  <br><br>
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer-felhasználók helyek hozzáadása**  
  Megakadályozza, hogy a felhasználók a biztonsági zónákból származó helyeket adjanak hozzá vagy távolítanak el. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, a biztonsági zónák hely-felügyeleti beállításai le vannak tiltva. (A biztonsági zónák hely-felügyeleti beállításainak megtekintéséhez az Internetbeállítások párbeszédpanelen kattintson a Biztonság fülre, majd kattintson a helyek gombra.) Ha letiltja vagy nem konfigurálja ezt a házirendet, a felhasználók hozzáadhatnak webhelyeket a megbízható helyek és a Tiltott helyek zónából, és módosíthatják a helyi intranet zóna beállításait. Ez a szabályzat megakadályozza, hogy a felhasználók módosítsák a rendszergazda által létesített biztonsági zónák hely-felügyeleti beállításait. Megjegyezés: A "biztonsági oldal letiltása" házirend (a User konfigurációja \ felügyeleti sablonok \ Internet Explorer\Internet vezérlőpultján található), amely eltávolítja a biztonsági lapot a felületről, elsőbbséget élvez a szabályzattal szemben. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Továbbá tekintse meg a "biztonsági zónák: Csak a számítógép-beállítások házirend használata.
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet zóna parancsfájl kezdeményezett Windows**  
  Ezzel a házirend-beállítással felügyelheti a parancsfájl által kezdeményezett előugró ablakokat és windowsokat, amelyek tartalmazzák a címet és az állapotjelző sávokat. Ha engedélyezi ezt a házirend-beállítást, a Windows-korlátozások biztonsága nem lesz érvényes ebben a zónában. A biztonsági zóna a szolgáltatás által biztosított hozzáadott biztonsági réteg nélkül fut. Ha letiltja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájl által kezdeményezett előugró ablakokban és windowsokban lévő lehetséges ártalmas műveletek nem futtathatók. Az Internet Explorer biztonsági funkciója ebben a zónában található, ahogy azt a Windowsos biztonsági korlátozásokkal kapcsolatos, a folyamathoz tartozó parancsfájl-ellenőrzési beállítás diktálja.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer biztonsági zónái csak a gép beállításait használják**  
  A biztonsági zóna információit alkalmazza ugyanazon számítógép minden felhasználója számára. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, a felhasználó által a biztonsági zónában végrehajtott módosítások a számítógép összes felhasználójára érvényesek lesznek. Ha letiltja vagy nem konfigurálja ezt a házirendet, akkor az azonos számítógép felhasználói a saját biztonsági zónákra vonatkozó beállításokat hozhatnak létre. Ezzel a házirenddel biztosíthatja, hogy a biztonsági zónák beállításai egységesen legyenek alkalmazva ugyanarra a számítógépre, és ne változzon a felhasználótól. Továbbá tekintse meg a "biztonsági zónák: ne engedélyezze a felhasználók számára szabályzatok módosítását" házirendet.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer zárolta a helyi számítógép zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva
  
  **Alapértelmezett**: A Java letiltása 
  
- **Az Internet Explorer korlátozott zónája nem futtat antimalware-t az aktív X vezérlőkön**  </br>
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának futtatása a .NET-keretrendszerre vonatkozó, Authenticode-val aláírt összetevőkkel**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Authenticode-val aláírt .NET-keretrendszer-összetevők az Internet Explorerben futtathatók-e. Ezen összetevők közé tartoznak az Object tag által hivatkozott felügyelt vezérlők, valamint a hivatkozásokból hivatkozott felügyelt végrehajtható fájlok. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer aláírt felügyelt összetevőket fog végrehajtani. Ha a legördülő listában a kérdés gombra kattint, az Internet Explorer megkéri a felhasználót, hogy döntse el, hogy végrehajtja-e az aláírt felügyelt összetevőket. Ha letiltja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer nem hajtja végre az aláírt felügyelt összetevőket.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zónáinak hozzáférése az adatforrásokhoz**  
  Ezzel a házirend-beállítással felügyelheti, hogy az Internet Explorer hozzáférhet-e egy másik biztonsági zónából származó adatokhoz a Microsoft XML Parser (MSXML) vagy a ActiveX Data Objects (ADO) használatával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók betölthetnek egy olyan lapot a zónába, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a lap betöltését az MSXML vagy az ADO protokollt használó zónában a zóna egy másik helyéről származó adatok eléréséhez. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tölthetnek be olyan lapot a zónában, amely az MSXML vagy az ADO használatával fér hozzá a zónában lévő másik helyről származó adatokhoz.
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer internetes zónája nem futtat antimalware-t az ActiveX-vezérlőkön**  </br>
  Ezzel a házirend-beállítással megállapítható, hogy az Internet Explorer antimalware-programokat futtat-e az ActiveX-vezérlőkön, hogy ellenőrizze, biztonságos-e a lapok betöltése. Ha engedélyezi ezt a házirend-beállítást, az Internet Explorer nem ellenőrzi, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha letiltja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi a kártevő szoftverét, hogy biztonságos-e az ActiveX-vezérlő példányának létrehozása. Ha nem konfigurálja ezt a házirend-beállítást, az Internet Explorer mindig ellenőrzi, hogy van-e biztonságos megoldás az ActiveX-vezérlő példányának létrehozására. A felhasználók az Internet Explorer biztonsági beállításainak használatával be-vagy kikapcsolhatják ezt a viselkedést.
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer Internet zóna másolás és beillesztés parancsfájl használatával** </br> Ezzel a házirend-beállítással felügyelheti, hogy a parancsfájlok végezhetnek-e vágólap-műveletet (például Kivágás, másolás és beillesztés) egy adott régióban. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy a vágólapon végez-e műveleteket. Ha letiltja ezt a házirend-beállítást, a parancsfájlok nem hajthatnak végre vágólap-műveletet. Ha nem konfigurálja ezt a házirend-beállítást, a parancsfájlok elvégezhetik a vágólap műveletet.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer az aktív X telepítő szolgáltatást használja**  </br>
  Ezzel a házirend-beállítással megadhatja, hogy az ActiveX-vezérlők hogyan legyenek telepítve. Ha engedélyezi ezt a házirend-beállítást, a rendszer csak akkor telepíti az ActiveX-vezérlőket, ha az ActiveX-telepítő szolgáltatás megtalálható, és úgy van konfigurálva, hogy engedélyezze az ActiveX-vezérlők telepítését. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a normál telepítési folyamaton keresztül telepíti az ActiveX-vezérlőket, beleértve a felhasználónkénti vezérlőket is.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer feldolgozza a védelmet a zónák megemelésével**  
  Az Internet Explorer a megnyíló weblapokon korlátozásokat helyez el. A korlátozások a weblap (Internet, intranet, helyi számítógép zóna stb.) helyétől függenek. Például a helyi számítógépen lévő weblapok a legkevesebb biztonsági korlátozással rendelkeznek, és a helyi számítógép zónában találhatók, így a helyi számítógép biztonsági zónája elsődleges cél a rosszindulatú felhasználók számára. Ha engedélyezi ezt a házirend-beállítást, az összes zóna megemelhető minden folyamat esetében. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, az Internet Explorer vagy a folyamat listában felsorolt folyamatok nem kapnak ilyen védelmet.
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer Internet zóna aláíratlan ActiveX-vezérlők letöltése**  </br>
  Ezzel a házirend-beállítással felügyelheti, hogy a felhasználók le tudják-e tölteni az aláíratlan ActiveX-vezérlőket a zónából. Ez a kód potenciálisan ártalmas, különösen akkor, ha nem megbízható zónából érkeznek. Ha engedélyezi ezt a házirend-beállítást, a felhasználók felhasználói beavatkozás nélkül futtathatnak aláíratlan vezérlőket. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e az aláíratlan vezérlő futtatását. Ha letiltja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet Zone – különböző tartományokban navigáljon a Windows és a keretek között**  </br>
  Ezzel a házirend-beállítással kezelheti a Windows és a keretek megnyitását, valamint az alkalmazások különböző tartományokon belüli elérését. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megnyithatják a Windowst és a képkockákat más tartományokból, és más tartományokból származó alkalmazásokat is elérhet. Ha a legördülő listában a kérdés lehetőséget választja, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a Windows és a keretek számára más tartományokból származó alkalmazások elérését. Ha letiltja ezt a házirend-beállítást, a felhasználók nem megnyithatják a Windowst és a képkockákat a különböző tartományokból származó alkalmazások eléréséhez. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók megnyithatja a Windowst és a képkockákat más tartományokból, és más tartományokból is elérheti az alkalmazásokat.
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer Internet zóna frissítései az állapotsoron parancsfájl használatával**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy parancsfájl frissítheti-e a zónán belüli állapotjelző sávot. Ha engedélyezi ezt a házirend-beállítást, a parancsfájlok frissíthetik az állapotjelző sávot. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a parancsfájl nem jogosult az állapotsor frissítésére.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónája helyi elérési utat tartalmaz a fájlok kiszolgálóra való feltöltésekor**  </br> Ezzel a házirend-beállítással szabályozható, hogy a rendszer mikor küldje el a helyi elérési utat, amikor a felhasználó HTML-űrlapon keresztül tölt fel fájlokat. Ha a rendszer elküldje a helyi elérési utat, előfordulhat, hogy a kiszolgáló véletlenül nem tárt fel adatokat. Előfordulhat például, hogy a felhasználó asztaláról eljuttatott fájlok tartalmazzák a felhasználónevet az elérési út részeként. Ha engedélyezi ezt a házirend-beállítást, a rendszer az elérési út adatait akkor továbbítja, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha letiltja ezt a házirend-beállítást, a rendszer eltávolítja az elérésiút-információkat, amikor a felhasználó HTML-űrlapon keresztül tölt fel egy fájlt. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó kiválaszthatja, hogy a rendszer elküldje-e az elérési utat, amikor HTML-űrlapon keresztül tölt fel fájlokat. Alapértelmezés szerint a rendszer az elérésiút-információkat elküldi.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer folyamatai korlátozzák a fájlok letöltését**  </br> Ezzel a házirend-beállítással a webböngésző vezérlőt futtató alkalmazások letilthatják a felhasználók által kezdeményezett fájlok letöltésének automatikus megadását. Ha engedélyezi ezt a házirend-beállítást, a webböngésző vezérlő letiltja azon fájlok letöltésének automatikus megadását, amelyek nem minden folyamat esetében kezdeményezték a felhasználót. Ha letiltja ezt a házirend-beállítást, a webböngésző vezérlő nem fogja blokkolni az olyan fájlok letöltésének automatikus megadását, amelyek nem minden folyamat esetében kezdeményezték a felhasználót.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónája csak jóváhagyott tartományokat engedélyez az aktív X vezérlők használatához**  </br>
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer a felhasználótól az ActiveX-vezérlőt telepítő webhelytől eltérő webhelyeken is fusson. Ha engedélyezi ezt a házirend-beállítást, a rendszer arra kéri a felhasználót, hogy az ActiveX-vezérlők futtathatók legyenek a zónában található webhelyekről. A felhasználó dönthet úgy, hogy engedélyezi, hogy a vezérlő az aktuális helyről vagy az összes helyről fusson. Ha letiltja ezt a házirend-beállítást, a felhasználó nem látja a helyhez tartozó ActiveX-parancssort, és az ActiveX-vezérlők a zóna összes webhelyéről futtathatók.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zónájának inicializálása és a parancsfájlok nem biztonságosként megjelölt aktív X-vezérlők**  
  Ezzel a házirend-beállítással kezelheti a nem biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, a rendszer futtatja az ActiveX-vezérlőket, betölti azokat paraméterekkel, és parancsfájlt helyez el anélkül, hogy a nem megbízható adatokra vagy parancsfájlokra vonatkozó biztonsági beállításokat Ez a beállítás nem ajánlott, a biztonságos és felügyelt zónák kivételével. Ez a beállítás azt eredményezi, hogy a nem biztonságos és a biztonságos vezérlők inicializálása és parancsfájlba való helyezése megtörtént, figyelmen kívül hagyva a parancsfájlok számára biztonságosként megjelölt ActiveX-vezérlőket. Ha engedélyezi ezt a házirend-beállítást, és a legördülő listában a kérdés elemre kattint, a rendszer lekérdezi a felhasználókat, hogy engedélyezi-e a vezérlőnek a paramétereket vagy parancsfájlokkal való betöltését. Ha letiltja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal. Ha nem konfigurálja ezt a házirend-beállítást, a nem biztonságos ActiveX-vezérlők nem tölthetők be paraméterekkel vagy parancsfájlokkal.
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer felhasználói házirendeket módosítanak**  
    Megakadályozza, hogy a felhasználók módosíthassák a biztonsági zónák beállításait. A biztonsági zónák ugyanazon biztonsági szinttel rendelkező webhelyek csoportjai. Ha engedélyezi ezt a házirendet, az Internetbeállítások párbeszédpanel Biztonság lapján az egyéni szint gomb és a biztonsági szint csúszkája le van tiltva. Ha letiltja vagy nem konfigurálja ezt a házirendet, a felhasználók módosíthatják a biztonsági zónák beállításait. Ez a szabályzat megakadályozza, hogy a felhasználók módosítsák a rendszergazda által létesített biztonsági zónák beállításait. Megjegyezés: A "biztonsági oldal letiltása" házirend (a User konfigurációja \ felügyeleti sablonok \ Internet Explorer\Internet vezérlőpultján található), amely eltávolítja az Internet Explorer biztonság lapját a Vezérlőpulton, elsőbbséget élvez Ez a szabályzat. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Továbbá tekintse meg a "biztonsági zónák: Csak a számítógép-beállítások házirend használata.
    
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer korlátozott zóna által védett üzemmód**  
  Ezzel a házirend-beállítással engedélyezheti a védett üzemmódot. A védett mód segít megvédeni az Internet Explorert a kihasznált biztonsági rések révén, ha csökkenti az Internet Explorer által a beállításjegyzékben és a fájlrendszerben írni kívánt helyeket. Ha engedélyezi ezt a házirend-beállítást, a védett mód be van kapcsolva. A felhasználó nem kapcsolhatja ki a védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a védett mód ki van kapcsolva. A felhasználó nem kapcsolhatja be a védett üzemmódot. Ha nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó be-vagy kikapcsolhatja a védett módot.
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer Internet Zone felhasználói adatmegőrzés**  
  Ezzel a házirend-beállítással kezelheti az információk megőrzését a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha a felhasználó egy megőrzött lapra tér vissza, akkor a lap állapota visszaállítható, ha a házirend-beállítás megfelelően van konfigurálva. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megőrzik az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók megőrizheti az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban vagy közvetlenül a lemezre mentett weblapon belül.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zónájának parancsfájlkezelése a webböngésző vezérlőinek használatával**  
 
  Ezzel a házirend-beállítással megadható, hogy egy oldal képes-e a beágyazott WebBrowser vezérlők futtatására parancsfájl használatával. Ha engedélyezi ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés engedélyezett. Ha letiltja ezt a házirend-beállítást, a WebBrowser vezérlőhöz való parancsfájl-hozzáférés nem engedélyezett. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználó engedélyezheti vagy letilthatja a WebBrowser vezérlőhöz tartozó parancsfájlok elérését. Alapértelmezés szerint a WebBrowser vezérlőhöz való parancsfájl-hozzáférés csak a helyi gépen és az intranet zónában engedélyezett.
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zónájának felhasználói adatmegőrzése**  
    Ezzel a házirend-beállítással kezelheti az információk megőrzését a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha a felhasználó egy megőrzött lapra tér vissza, akkor a lap állapota visszaállítható, ha a házirend-beállítás megfelelően van konfigurálva. Ha engedélyezi ezt a házirend-beállítást, a felhasználók megőrzik az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha letiltja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül a lemezre mentett weblapon belül. Ha nem konfigurálja ezt a házirend-beállítást, a felhasználók nem tudják megőrizni az információkat a böngésző előzményeiben, a Kedvencek között, egy XML-tárolóban, vagy közvetlenül egy, a lemezre mentett weblapon belül.  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer lezárta az intranet zóna Java-engedélyeit**  
  Ezzel a házirend-beállítással kezelheti a Java-kisalkalmazások engedélyeit. Ha engedélyezi ezt a házirend-beállítást, a legördülő listából választhatja ki a kívánt beállításokat. Egyéni, az engedélyek beállításainak külön történő vezérléséhez. Az alacsony biztonság lehetővé teszi a kisalkalmazások számára az összes művelet elvégzését. A közepes biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak (egy olyan terület a memóriában, amelyen kívül a program nem tud hívásokat kezdeményezni), valamint olyan funkciókkal, mint például a kaparós terület (biztonságos és biztonságos tárterület az ügyfélszámítógépen) és a felhasználó által vezérelt fájl I/O. A magas biztonság lehetővé teszi, hogy a kisalkalmazások a homokozóban fussanak. A Java letiltásával megakadályozhatja, hogy bármely kisalkalmazás fusson. Ha letiltja ezt a házirend-beállítást, a Java-kisalkalmazások nem futtathatók. Ha nem konfigurálja ezt a házirend-beállítást, a Java-kisalkalmazások le vannak tiltva.
  
  **Alapértelmezett**: A Java letiltása  
  
- **Internet Explorer fokozottan védett üzemmód**  
  A továbbfejlesztett védett mód további védelmet biztosít a rosszindulatú webhelyekkel szemben, ha 64 bites folyamatokat használ a Windows 64-bites verzióiban. A Windows 8 rendszerű számítógépek esetében a fokozottan védett mód is korlátozza az Internet Explorer által a beállításjegyzékből és a fájlrendszerből beolvasott helyeket. Ha engedélyezi ezt a házirend-beállítást, a fokozottan védett mód be van kapcsolva. Minden olyan zóna, amelynél engedélyezve van a védett üzemmód, fokozottan védett módot fog használni. A felhasználók nem tudják letiltani a fokozottan védett üzemmódot. Ha letiltja ezt a házirend-beállítást, a fokozottan védett üzemmód ki van kapcsolva. Minden olyan zóna, amelynél engedélyezve van a védett üzemmód, a Windows Vista Internet Explorer 7-es verziójában bemutatott védett mód verzióját fogja használni. Ha nem konfigurálja ezt a házirendet, a felhasználók az Internetbeállítások párbeszédpanel Speciális lapján bekapcsolhatják vagy kikapcsolhatják a fokozottan védett üzemmódot.
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megkerülésének intelligens képernyő figyelmeztetései**  
  Ezzel a házirend-beállítással adható meg, hogy a felhasználó megkerülhet-e a SmartScreen szűrőből származó figyelmeztetéseket. A SmartScreen szűrő figyelmezteti a felhasználót olyan végrehajtható fájlokra, amelyeket az Internet Explorer felhasználói általában nem töltenek le az internetről. Ha engedélyezi ezt a házirend-beállítást, a SmartScreen szűrő figyelmeztetései letiltják a felhasználót. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, akkor a felhasználó megkerülheti a SmartScreen szűrő figyelmeztetéseit.
  
  **Alapértelmezett**: Letiltva  
  
- **Internet Explorer – korlátozott zóna – metaadatok frissítése**  
  Ezzel a házirend-beállítással felügyelheti, hogy egy felhasználó böngészője átirányítható-e egy másik weblapra, ha a weblap szerzője a meta refresh (címke) beállítást használja a böngészők másik weblapra való átirányításához. Ha engedélyezi ezt a házirend-beállítást, egy olyan felhasználó böngészőjében, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, átirányítható egy másik weblapra. Ha letiltja ezt a házirend-beállítást, egy olyan felhasználó böngészője, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, nem lehet átirányítani egy másik weblapra. Ha nem konfigurálja ezt a házirend-beállítást, egy olyan felhasználó böngészője, amely egy aktív meta frissítési beállítást tartalmazó oldalt tölt be, nem irányítható át egy másik weblapra.
  
  **Alapértelmezett**: Letiltva  
  
### <a name="local-policies-security-options"></a>Helyi házirendek biztonsági beállításai
További információ: [Policy CSP-LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) a Windows dokumentációjában. 

- **Nevesített csövek és megosztások névtelen elérésének korlátozása**  
  Ha engedélyezve van, ez a biztonsági beállítás korlátozza a megosztásokhoz és csövekhez való névtelen hozzáférést a következő beállításokra: (1) névvel ellátott, névtelenül elérhető (2) megosztású csövek
  
  **Alapértelmezett**: Igen  
  
- **Minimális munkamenet-biztonság az NTLM SSP-alapú kiszolgálók esetében**  
  Ez a biztonsági beállítás lehetővé teszi a kiszolgáló számára, hogy megkövetelje a 128 bites titkosítás és/vagy az NTLMv2 munkamenet-biztonság egyeztetését. Ezek az értékek a LAN Manager hitelesítési szintjének biztonsági beállításának értékétől függenek. Az alábbi lehetőségek állnak rendelkezésére: NTLMv2-munkamenet biztonságának megkövetelése: Ha az üzenet integritása nincs egyeztetve, a rendszer sikertelen lesz. 128 bites titkosítás megkövetelése. Ha az erős titkosítás (128 bites) nincs egyeztetve, a rendszer nem fogja tudni a kapcsolatokat.
  
  **Alapértelmezett**: NTLM v2 és 128 bites titkosítás megkövetelése  
  
- **A zárolási képernyő inaktivitásának percben, amíg a képernyőkímélő be nem kapcsol**  
  A Windows észleli a bejelentkezési munkamenetek tétlenségét, és ha a tétlenség ideje túllépi a tétlenségi korlátot, a rendszer futtatja a képernyőkímélőt és lezárja a munkamenetet.
  
  **Alapértelmezett**: 15
  
- **Az ügyfél minden esetben digitálisan aláírja a kommunikációt** Ez a biztonsági beállítás határozza meg, hogy a tartományi tag által kezdeményezett összes biztonságos csatorna forgalmát alá kell-e írni vagy titkosítani kell-e. Ha egy számítógép tartományhoz csatlakozik, létrejön egy számítógépfiók. Ezt követően a rendszer indításakor a számítógépfiók jelszava használatával hozzon létre egy biztonságos csatornát a tartományához tartozó tartományvezérlővel. Ez a biztonságos csatorna olyan műveletek elvégzésére szolgál, mint például az NTLM-továbbítás hitelesítés, az LSA SID/Name lookup és még sok más. Ez a beállítás határozza meg, hogy a tartomány tagja által kezdeményezett összes biztonságos csatorna-forgalom megfelel-e a minimális biztonsági követelményeknek. Pontosabban meghatározza, hogy a tartományi tag által elindított összes biztonságos csatorna forgalmát alá kell-e írni vagy titkosítani kell-e. Ha ez a szabályzat engedélyezve van, akkor a biztonságos csatorna nem lesz létrehozva, kivéve, ha az összes biztonságos csatorna-forgalom aláírásával vagy titkosításával egyeztetve van. Ha ez a szabályzat le van tiltva, akkor a rendszer az összes biztonságos csatorna forgalom titkosítását és aláírását egyezteti a tartományvezérlővel, amely esetben az aláírás és a titkosítás szintje a tartományvezérlő verziójától és a következő két beállítástól függ. szabályzatok Tartományi tag: Biztonságos csatorna adatai digitális titkosítása (ha lehetséges) tartományi tag: Biztonságos csatornák digitális aláírása (ha lehetséges)
  
  **Alapértelmezett**: Igen
  
- **Hitelesítési szint**  
  Ez a biztonsági beállítás határozza meg, hogy melyik kérdés-válasz hitelesítési protokollt használja a rendszer a hálózati bejelentkezésekhez. Ez a választás hatással van az ügyfelek által használt hitelesítési protokoll szintjére, a munkamenet-biztonság megtárgyalásának szintjére, valamint a kiszolgálók által a következőképpen elfogadott hitelesítés szintjére:  
  - *LM-és NTLM-válaszok küldése*: Az ügyfelek az LM és az NTLM hitelesítést használják, és soha nem használják az NTLMv2 munkamenet-biztonságot; a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Az LM és az NTLM-NTLMv2 küldése, ha egyeztetve*van: Az ügyfelek az LM és az NTLM hitelesítést használják, és az NTLMv2 munkamenet-biztonságot használják, ha a kiszolgáló támogatja azt; a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLM-válasz küldése*: Az ügyfelek csak az NTLM-hitelesítést használják, és ha a kiszolgáló támogatja, az NTLMv2 munkamenet-biztonságot használják. a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLMv2-válasz küldése*: Az ügyfelek csak az NTLMv2-hitelesítést használják, és az NTLMv2 munkamenet-biztonságot használják, ha a kiszolgáló támogatja azt; a tartományvezérlők elfogadják az LM-, NTLM-és NTLMv2-hitelesítést. 
  - *Csak NTLMv2-válasz küldése. LM*elutasítása: Az ügyfelek csak az NTLMv2-hitelesítést használják, és az NTLMv2 munkamenet-biztonságot használják, ha a kiszolgáló támogatja azt; a tartományvezérlők elutasították az LM-t (csak NTLM és NTLMv2 hitelesítést fogadnak el). 
  - *Csak NTLMv2-válasz küldése. Az LM és az NTLM*elutasítása: Az ügyfelek csak az NTLMv2-hitelesítést használják, és az NTLMv2 munkamenet-biztonságot használják, ha a kiszolgáló támogatja azt; a tartományvezérlők megtagadják az LM és az NTLM használatát (csak az NTLMv2-hitelesítést fogadják el). 
    
  **Alapértelmezett**: Csak NTLMv2-válasz küldése. Az LM és az NTLM elutasítása
  
- **Titkosítatlan jelszavak küldésének megakadályozása az ügyfelektől harmadik féltől származó SMB-kiszolgálókra**  
  Ha ez a biztonsági beállítás engedélyezve van, a kiszolgálói üzenetblokk (SMB) átirányító képes szöveges jelszavakat küldeni a nem Microsoft SMB-kiszolgálókra, amelyek nem támogatják a jelszó-titkosítást a hitelesítés során. A Titkosítatlan jelszavak küldése biztonsági kockázat.
  
  **Alapértelmezett**: Igen
  
- **A kiszolgáló digitális aláírási kommunikációjának letiltása mindig**  
  Ez a biztonsági beállítás határozza meg, hogy az SMB-ügyfél megkísérelje-e az SMB-csomagok aláírásának egyeztetését. A Server Message Block (SMB) protokoll a Microsoft fájl-és nyomtatómegosztás, valamint számos egyéb hálózati művelet, például a távoli Windows-felügyelet alapját képezi. Ha meg szeretné akadályozni, hogy az SMB-csomagokat az átvitel során módosító, nem a közepes támadásokkal szemben, az SMB protokoll támogatja az SMB-csomagok digitális aláírását. Ezzel a házirend-beállítással megadható, hogy az SMB-ügyfél-összetevő megkísérelje-e az SMB-csomagok aláírását az SMB-kiszolgálóhoz való csatlakozáskor. Ha ez a beállítás engedélyezve van, a Microsoft hálózati ügyfél arra kéri a kiszolgálót, hogy az SMB-csomagok aláírását végrehajtsa a munkamenet beállításakor. Ha a csomagaláírás engedélyezve van a kiszolgálón, a csomagaláírás egyeztetése megkezdődik. Ha a szabályzat le van tiltva, az SMB-ügyfél soha nem fogja egyeztetni az SMB-csomagok aláírását.
  
  **Alapértelmezett**: Igen
  
- **Rendszergazdai jogosultságszint-emelési kérések viselkedése**  
  Ezzel a házirend-beállítással szabályozható a rendszergazdák jogosultságszint-emelési kérésének viselkedése. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Jogosultságszint-emelés kérés nélkül*: Lehetővé teszi, hogy a Kiemelt fiókok olyan műveletet végezzenek, amely jogosultságszint-emelést követel meg a jogosultság vagy a hitelesítő adatok megadása nélkül. Megjegyezés: Ezt a lehetőséget csak a legszigorúbban korlátozott környezetekben használhatja. 
  - *Hitelesítő adatok kérése a biztonságos asztalon*: Ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer felszólítja a felhasználót a biztonságos asztalra, hogy adjon meg egy kiemelt felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ír be, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  - *Beleegyezés kérése a biztonságos asztalon*: Ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a felhasználónak meg kell adnia a biztonságos asztalt az engedélyezés vagy a Megtagadás lehetőség kiválasztásához. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik. 
  - *Hitelesítő adatok kérése*: Ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer kéri a felhasználótól, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Beleegyezés kérése*: Ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a felhasználónak meg kell adnia az engedélyt vagy a Megtagadás lehetőséget. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik.  
  - *Beleegyezés kérése nem Windows rendszerű bináris*fájlokhoz: Ha egy nem a Microsofttól származó alkalmazás működéséhez jogosultságszint-emelésre van szükség, a felhasználónak meg kell adnia a felhasználót a biztonságos asztalon az engedélyezés vagy a Megtagadás lehetőség kiválasztásához. Ha a felhasználó az Engedélyezés lehetőséget választja, a művelet a felhasználó legmagasabb rendelkezésre állási jogosultságával folytatódik.   
  
  **Alapértelmezett**: Beleegyezés kérése a biztonságos asztalon
  
- **Minimális munkamenet-biztonság az NTLM SSP-alapú ügyfelek számára**  
  Ez a biztonsági beállítás lehetővé teszi az ügyfél számára, hogy megkövetelje a 128 bites titkosítás és/vagy az NTLMv2 munkamenet-biztonság egyeztetését. Ezek az értékek a LAN Manager hitelesítési szintjének biztonsági beállításának értékétől függenek. Az alábbi lehetőségek állnak rendelkezésére:
  - NTLMv2-munkamenet biztonságának megkövetelése: A kapcsolat sikertelen lesz, ha az NTLMv2 protokoll nincs egyeztetve. 
  - *128 bites titkosítás*megkövetelése: Ha az erős titkosítás (128 bites) nincs egyeztetve, a rendszer nem fogja tudni a kapcsolatokat.
  - *NTLMv2 és 128 bites titkosítás*megkövetelése. 

  **Alapértelmezett**: NTLM v2 128 titkosítás megkövetelése
  
- **Intelligens kártya eltávolításának viselkedése**  
  Ez a biztonsági beállítás határozza meg, hogy mi történjen, ha a bejelentkezett felhasználó intelligens kártyáját eltávolítja az intelligenskártya-olvasóból. Az alábbi lehetőségek állnak rendelkezésére:
  - *Nincs művelet*. 
  - *Munkaállomás zárolása* – a munkaállomás az intelligens kártya eltávolításakor zárolva van, így a felhasználók elhagyhatják a területeket, saját intelligens kártyájuk is megtarthatják őket, és továbbra is fenntartják a védett munkamenetet.
  - *Kijelentkezés kényszerítése* – a rendszer automatikusan kijelentkezik a felhasználót az intelligens kártya eltávolításakor.
  - *Távoli asztal kapcsolat bontása* – az intelligens kártya eltávolítása leválasztja a munkamenetet anélkül, hogy a felhasználót be kellene jelentkeznie. Ez lehetővé teszi a felhasználó számára, hogy beszúrja az intelligens kártyát, és később, vagy egy másik intelligenskártya-olvasóval felszerelt számítógépen folytassa a bejelentkezést anélkül, hogy újra be kellene jelentkeznie. Helyi munkamenet esetén ez a szabályzat pontosan úgy működik, mint a Munkaállomás zárolása.  <br><br>

  **Alapértelmezett**: Munkaállomás zárolása
  
- **SAM-fiókok és-megosztások névtelen enumerálásának letiltása**  
  Ez a biztonsági beállítás határozza meg, hogy engedélyezi-e a SAM-fiókok és-megosztások névtelen enumerálását. A Windows lehetővé teszi a névtelen felhasználók számára bizonyos tevékenységek végrehajtását, például a tartományi fiókok és hálózati megosztások nevének számbavételét. Ez akkor lehet hasznos, ha egy rendszergazda olyan megbízható tartományban kíván hozzáférést biztosítani a felhasználóknak, amely nem tart fenn kölcsönös bizalmi kapcsolatot. Ha nem szeretné engedélyezni a SAM-fiókok és-megosztások névtelen enumerálását, állítsa ezt a házirendet *Igen*értékre.
  
  **Alapértelmezett**: Igen
  
- **Üres jelszóval rendelkező távoli bejelentkezés letiltása**  
  Ez a biztonsági beállítás határozza meg, hogy a jelszóval védett helyi fiókok a fizikai számítógép konzolján kívül más helyekről is bejelentkezhetnek-e. Ha engedélyezve van, a jelszóval védett helyi fiókoknak a számítógép billentyűzetén kell használniuk a bejelentkezést. 

  *Figyelmeztetés*: Azok a számítógépek, amelyek nem a fizikailag biztonságos helyen találhatók, mindig erős jelszavas házirendeket kényszerítenek az összes helyi felhasználói fiókhoz. Ellenkező esetben a számítógéphez való fizikai hozzáféréssel rendelkező bárki bejelentkezhet egy olyan felhasználói fiókkal, amely nem rendelkezik jelszóval. Ez különösen fontos a hordozható számítógépekhez. 

  Ha ezt a biztonsági házirendet a Mindenki csoportra alkalmazza, a Távoli asztali szolgáltatások nem tud bejelentkezni. Ez a beállítás nem érinti a tartományi fiókokat használó bejelentkezéseket. Távoli interaktív bejelentkezéseket használó alkalmazások esetén a beállítás megkerülése lehetséges.
  
  **Alapértelmezett**: Igen
  
- **Normál felhasználói jogosultságszint-emelési kérések viselkedése**  
  Ezzel a házirend-beállítással szabályozható az általános jogú felhasználók jogosultságszint-emelési kérésének viselkedése. 
  - *Jogosultságszint-emelési kérések automatikus*megtagadása: Ha egy művelethez Jogosultságszint-emelés szükséges, a rendszer konfigurálható hozzáférés-megtagadási hibaüzenetet jelenít meg. Az asztali gépeket futtató vállalatok az általános jogú felhasználók ezt a beállítást választva csökkenthetik az ügyfélszolgálati hívásokat. 
  - *Hitelesítő adatok kérése a biztonságos asztalon*: Ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a felhasználónak a biztonságos asztalon kell megadnia egy másik felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - *Hitelesítő adatok kérése*: Ha egy művelethez jogosultságszint-emelési jogosultságra van szükség, a rendszer kéri a felhasználótól, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal.  
  
  **Alapértelmezett**: Jogosultságszint-emelési kérések automatikus megtagadása
  
- **Rendszergazdai engedélyezési mód szükséges a rendszergazdák számára**  
  Ezzel a házirend-beállítással szabályozható a számítógépen a felhasználói fiókok felügyelete (UAC) összes házirend-beállításának viselkedése. Ha módosítja ezt a házirend-beállítást, újra kell indítania a számítógépet. Az alábbi lehetőségek állnak rendelkezésére:   
  - *Nincs konfigurálva*: A rendszergazdai engedélyezési mód és az összes kapcsolódó UAC házirend-beállítás le van tiltva. Megjegyezés: Ha a házirend-beállítás le van tiltva, a Security Center értesíti arról, hogy az operációs rendszer általános biztonsága csökkent. 
  - *Igen*: A rendszergazdai jóváhagyási mód engedélyezve van. Ezt a házirendet engedélyezni kell, és a kapcsolódó UAC-házirend beállításait megfelelően be kell állítani ahhoz, hogy a beépített rendszergazdai fiók és az összes többi olyan felhasználó, aki tagja a rendszergazdák csoportnak, rendszergazdai engedélyezéses módban fusson.  
  
  **Alapértelmezett**: Igen
  
- **SAM-fiókok névtelen számbavételének megakadályozása**  
  Ez a biztonsági beállítás határozza meg, hogy a rendszer milyen további engedélyeket kap a névtelen kapcsolatok számára a számítógéphez. A Windows lehetővé teszi a névtelen felhasználók számára bizonyos tevékenységek végrehajtását, például a tartományi fiókok és hálózati megosztások nevének számbavételét. Ez akkor lehet hasznos, ha egy rendszergazda olyan megbízható tartományban kíván hozzáférést biztosítani a felhasználóknak, amely nem tart fenn kölcsönös bizalmi kapcsolatot. Ez a biztonsági beállítás lehetővé teszi, hogy további korlátozások kerüljenek a névtelen kapcsolatokra a következőképpen: 
  - *Igen*: Ne engedélyezze a SAM-fiókok enumerálását. Ez a beállítás a hitelesített felhasználókkal rendelkező mindenkit lecseréli az erőforrásokra vonatkozó biztonsági engedélyekben.
  - *Nincs konfigurálva*: Nincs további korlátozás. Használja az alapértelmezett engedélyeket.  
  
  **Alapértelmezett**: Igen
  
- **Távoli hívások engedélyezése a biztonsági fiókok kezelőjének**  
  Ezzel a házirend-beállítással korlátozhatja a távoli RPC-kapcsolatokat a SAM-ra. Ha nincs bejelölve, a rendszer az alapértelmezett biztonsági leírót használja.
  
  **Alapértelmezett**: *O:BAG: HELYTELEN: (A;; RC;;; BA*

- **Rendszergazdai jóváhagyási mód használata**  
  Ezzel a házirend-beállítással szabályozható a rendszergazdai engedélyezési mód működése a beépített rendszergazda fiókhoz. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Igen*: A beépített rendszergazdai fiók rendszergazdai jóváhagyási módot használ. Alapértelmezés szerint a jogosultságszint-emelést igénylő műveletek megkérik a felhasználót, hogy hagyja jóvá a műveletet. 
  - *Nincs konfigurálva*: A beépített rendszergazdai fiók minden olyan alkalmazást futtat, amely teljes körű rendszergazdai jogosultságokkal rendelkezik.  

  **Alapértelmezett**: Igen
  
- **Felhasználói felületi hozzáférési alkalmazások engedélyezése biztonságos helyszíneken**  
  Ezzel a házirend-beállítással szabályozható, hogy a felhasználói felület kisegítő lehetőségei (UIAccess vagy UIA) automatikusan le tudják-e tiltani a biztonságos asztalt az általános jogú felhasználók általi jogosultságszint-emelési kérésekhez. 
  - *Igen*: A UIA programok, például a Windows Távsegítség, automatikusan letiltják a jogosultságszint-emelési kérések biztonságos asztalát. Ha nem tiltja le a "felhasználói fiókok felügyelete: A jogosultságszint-emelésre való rákérdezéskor váltson a biztonságos asztalra, és a kérések a biztonságos asztal helyett az interaktív felhasználó asztalán jelennek meg. 
  - *Nincs konfigurálva*: A biztonságos asztalt csak az interaktív asztal felhasználója tilthatja le, vagy letilthatja a felhasználói fiókok felügyeletét: Jogosultságszint-emelési kérés esetén váltson a biztonságos asztalra.  

  **Alapértelmezett**: Igen

- **Alkalmazások telepítésének észlelése és Jogosultságszint-emelés kérése**  
  Ezzel a házirend-beállítással szabályozható a számítógép alkalmazás-telepítési észlelésének viselkedése. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Engedélyezve*: A jogosultságszint-emelést igénylő alkalmazás-telepítési csomag észlelésekor a rendszer megkéri a felhasználót, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó érvényes hitelesítő adatokat ad meg, a művelet folytatódik a megfelelő jogosultsággal. 
  - Letiltva: Az alkalmazás telepítési csomagjai nem észlelhetők, és a rendszer kéri a jogosultságszint-emelést. Az általános jogú felhasználói asztalokat futtató és a delegált telepítési technológiákat (például Csoportházirend-alapú szoftvertelepítés vagy System Management Server (SMS)) használó vállalatoknak le kell tiltaniuk ezt a házirend-beállítást. Ebben az esetben a telepítő észlelése szükségtelen.  
  
  **Alapértelmezett**: Igen
  
- **A LAN Manager kivonatoló értékének a következő jelszó módosításakor való tárolásának megakadályozása**  
  Ez a biztonsági beállítás határozza meg, hogy a következő jelszó megváltozásakor az új jelszóhoz tartozó LAN Manager (LM) kivonatoló értéket tárolja-e a rendszer. Az LM-kivonat viszonylag gyenge és hajlamos a támadásokra, mint a kriptográfiailag erősebb Windows NT-kivonathoz képest. Mivel az LM-kivonat a biztonsági adatbázisban a helyi számítógépen van tárolva, a rendszer a jelszavakat a biztonsági adatbázis megtámadása esetén is veszélyeztetheti.
  
  **Alapértelmezett**: Igen

- **A fájl-és beállításjegyzék-írási hibák virtualizálása felhasználónkénti helyen**  
  Ezzel a házirend-beállítással szabályozható, hogy a rendszer az alkalmazások írási hibáit átirányítsa-e a megadott beállításjegyzék-és fájlrendszerbeli helyeire Ezzel a házirend-beállítással csökkenthetők a rendszergazdaként futtatott alkalmazások és a futásidejű alkalmazásadatok írása a következőre: *% ProgramFiles%* , *% windir%* , *%windir%\System32*vagy *HKLM\Software*.
  
  **Alapértelmezett**: Igen

### <a name="ms-security-guide"></a>MS biztonsági útmutató  

További információ: [Policy CSP-MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) a Windows dokumentációjában.  

- **UAC-korlátozások alkalmazása helyi fiókokra hálózati bejelentkezéskor**  
  **Alapértelmezett**: Enabled
  
- **SMB v1 – ügyfél-illesztőprogram indítási konfigurációja**  
  **Alapértelmezett**: Letiltott illesztőprogram
  
- **SMB v1-kiszolgáló**  
  **Alapértelmezett**: Letiltva
  
- **Kivonatoló hitelesítés**  
  **Alapértelmezett**: Letiltva
  
- **Strukturált kivétel kezelésére vonatkozó felülírási védelem**  
  **Alapértelmezett**: Enabled
  
### <a name="mss-legacy"></a>MSS örökölt  

További információ: [Policy CSP-MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) a Windows dokumentációjában.  

- **Hálózati IP-forrás útválasztási védelmi szintje**  
  **Alapértelmezett**: Legmagasabb szintű védelem  
  
- **A hálózat figyelmen kívül hagyja a NetBIOS-névfeloldási kérelmeket a WINS-kiszolgálók kivételével**  
  **Alapértelmezett**: Enabled
  
- **Hálózati IPv6-forrás útválasztási védelmi szintje**  
  **Alapértelmezett**: Legmagasabb szintű védelem

- **Hálózati ICMP-átirányítás felülbírálja az OSPF által generált**  
  **Alapértelmezett**: Letiltva
  
### <a name="power"></a>Power  

További információ: [házirend CSP-Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) a Windows dokumentációjában.  

- **Jelszó megkövetelése ébresztéskor a csatlakoztatáskor**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználótól a jelszót, amikor a rendszer visszatér az alvó állapotból. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a felhasználónak jelszót kér, amikor az alvó állapotból folytatódik. Ha letiltja ezt a házirend-beállítást, a felhasználó nem kér jelszót, amikor a rendszer visszatér az alvó állapotból.
  
  **Alapértelmezett**: Enabled
  
- **Készenléti állapot, ha akkumulátorról alszik**  
  Ez a házirend-beállítás azt szabályozza, hogy a Windows használhat-e készenléti állapotokat a számítógép alvó állapotba helyezésekor. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a Windows készenléti állapotot használ a számítógép alvó állapotba helyezéséhez. Ha letiltja ezt a házirend-beállítást, a készenléti állapotok (S1-S3) nem engedélyezettek.
  
  **Alapértelmezett**: Letiltva
  
- **Készenléti állapotok a csatlakoztatáskor**  
  Ez a házirend-beállítás azt szabályozza, hogy a Windows használhat-e készenléti állapotokat a számítógép alvó állapotba helyezésekor. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a Windows készenléti állapotot használ a számítógép alvó állapotba helyezéséhez. Ha letiltja ezt a házirend-beállítást, a készenléti állapotok (S1-S3) nem engedélyezettek.
  
  **Alapértelmezett**: Letiltva
  
- **Jelszó megkövetelése ébresztéskor az akkumulátoron**  
  Ezzel a házirend-beállítással adható meg, hogy a rendszer kéri-e a felhasználótól a jelszót, amikor a rendszer visszatér az alvó állapotból. Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, a rendszer a felhasználónak jelszót kér, amikor az alvó állapotból folytatódik. Ha letiltja ezt a házirend-beállítást, a felhasználó nem kér jelszót, amikor a rendszer visszatér az alvó állapotból.
  
  **Alapértelmezett**: Enabled
  
### <a name="remote-desktop-services"></a>Távoli asztali szolgáltatások  

További információ: [Policy CSP-RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) a Windows dokumentációjában.  

- **Jelszó mentésének tiltása**  
  Meghatározza, hogy a jelszavak menthetők-e a számítógépen Távoli asztali kapcsolatról. Ha engedélyezi ezt a beállítást, a Távoli asztali kapcsolat letiltotta a jelszó-mentés jelölőnégyzetet, és a felhasználók nem tudják menteni a jelszavakat. Amikor egy felhasználó megnyit egy RDP-fájlt a Távoli asztali kapcsolat használatával, és menti a beállításokat, az RDP-fájlban korábban létezett jelszavak törlődnek. Ha letiltja ezt a beállítást, vagy hagyja meg, hogy nincs konfigurálva, a felhasználó Távoli asztali kapcsolat használatával mentheti a jelszavakat.
  
   **Alapértelmezett**: Enabled
  
- **Biztonságos RPC-kommunikáció**  
  Meghatározza, hogy egy Távoli asztal munkamenet-kiszolgáló biztonságos RPC-kommunikációt igényel-e az összes ügyféllel, vagy engedélyezi a nem biztonságos kommunikációt. Ezzel a beállítással megerősítheti az ügyfelekkel folytatott RPC-kommunikáció biztonságát úgy, hogy csak a hitelesített és titkosított kérelmeket engedélyezi. Ha az állapot engedélyezve értékre van állítva, Távoli asztali szolgáltatások fogadja a biztonságos kéréseket támogató RPC-ügyfelektől érkező kérelmeket, és nem engedélyezi a nem biztonságos kommunikációt a nem megbízható ügyfelekkel. Ha az állapot letiltva értékre van állítva, Távoli asztali szolgáltatások mindig minden RPC-forgalomhoz kér biztonságot. A nem biztonságos kommunikáció azonban olyan RPC-ügyfelek számára engedélyezett, amelyek nem válaszolnak a kérelemre. Ha az állapot nincs konfigurálva értékre van állítva, akkor a nem biztonságos kommunikáció engedélyezett. Megjegyezés: Az RPC interfész Távoli asztali szolgáltatások felügyeletére és konfigurálására szolgál.
  
  **Alapértelmezett**: Enabled
  
- **Meghajtó átirányításának tiltása**  
  Ezzel a házirend-beállítással megadható, hogy meg kell-e akadályozni az ügyfélmeghajtók hozzárendelését egy Távoli asztali szolgáltatások-munkamenetben (meghajtó-átirányítás). Alapértelmezés szerint a távoli asztali munkamenetgazda-kiszolgáló automatikusan leképezi az ügyféloldali meghajtókat a kapcsolaton keresztül. A csatlakoztatott meghajtók a Fájlkezelőben vagy a számítógépen a következő formátumban  *\<* jelennek meg: meghajtóbetűjel > a  *\<számítógépnév >* . Ezt a házirend-beállítást használhatja a viselkedés felülbírálásához. Ha engedélyezi ezt a házirend-beállítást, az ügyfélmeghajtók átirányítása Távoli asztali szolgáltatások munkamenetekben nem engedélyezett, és a vágólap-fájlmásolás átirányítása nem engedélyezett a Windows Server 2003, Windows 8 és Windows XP rendszerű számítógépeken. Ha letiltja ezt a házirend-beállítást, a rendszer mindig engedélyezi az ügyfél-meghajtó átirányítását. A vágólap-másolási átirányítás is mindig engedélyezett, ha a vágólap átirányítása engedélyezve van. Ha nem konfigurálja ezt a házirend-beállítást, az ügyfél-meghajtó átirányítása és a vágólap-fájlmásolás átirányítása nincs megadva a Csoportházirend szinten.
  
  **Alapértelmezett**: Enabled
  
- **Jelszó kérése a csatlakozáskor**  
  Ezzel a házirend-beállítással megadható, hogy a Távoli asztali szolgáltatások mindig kéri-e az ügyfelet a jelszó kérésére a csatlakozáskor. Ezzel a beállítással megadhatja, hogy a felhasználók milyen jelszóval jelentkezzenek be Távoli asztali szolgáltatásokba, még akkor is, ha már megadták a jelszót a Távoli asztali kapcsolat-ügyfélben. Alapértelmezés szerint a Távoli asztali szolgáltatások lehetővé teszi, hogy a felhasználók automatikusan bejelentkeznek a Távoli asztali kapcsolat-ügyfélben lévő jelszó megadásával. Ha engedélyezi ezt a házirend-beállítást, a felhasználók nem tudnak automatikusan bejelentkezni a Távoli asztali szolgáltatásokba, ha a Távoli asztali kapcsolat-ügyfélben megadják a jelszavukat. a rendszer jelszót kér a bejelentkezéshez. Ha letiltja ezt a házirend-beállítást, a felhasználók bármikor bejelentkezhetnek a Távoli asztali szolgáltatások automatikusan, ha megadják a jelszavukat a Távoli asztali kapcsolat ügyfélen. Ha nem konfigurálja ezt a házirend-beállítást, az automatikus bejelentkezés nincs megadva a Csoportházirend szinten. 
  
  **Alapértelmezett**: Enabled
  
- **Távoli asztali szolgáltatások ügyfélkapcsolatának titkosítási szintje**  
  Meghatározza, hogy szükség van-e egy adott titkosítási szint használatára az ügyfélszámítógépek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikáció biztonságossá tételéhez RDP protokoll (RDP) kapcsolatok során. Ez a szabályzat csak akkor érvényes, ha natív RDP-titkosítást használ. Azonban a natív RDP-titkosítás (az SSL-titkosítás helyett) nem ajánlott. Ez a szabályzat nem vonatkozik az SSL-titkosításra. Ha engedélyezi ezt a házirend-beállítást, a távoli kapcsolatok során az ügyfelek és a távoli asztali munkamenetgazda-kiszolgálók közötti összes kommunikációnak az ebben a beállításban megadott titkosítási módszert kell használnia. Alapértelmezés szerint a titkosítási szint magas értékre van állítva. A következő titkosítási módszerek érhetők el:  
  - *Magas*: A magas beállítás a-ügyfélről a kiszolgálóra és a kiszolgálóról az ügyfélre érkező, erős 128 bites titkosítást használó adatok titkosítására szolgál. Használja ezt a titkosítási szintet olyan környezetekben, amelyek csak 128 bites ügyfeleket tartalmaznak (például Távoli asztali kapcsolatt futtató ügyfeleket). Azok az ügyfelek, amelyek nem támogatják ezt a titkosítási szintet, nem csatlakozhatnak a távoli asztali munkamenetgazda-kiszolgálókhoz.  
  - *Ügyfél-kompatibilis*: Az ügyfél-kompatibilis beállítás titkosítja az ügyfél és a kiszolgáló között továbbított, az ügyfél által támogatott maximális kulcs erősségét. Használja ezt a titkosítási szintet olyan környezetekben, amelyek olyan ügyfeleket tartalmaznak, amelyek nem támogatják a 128 bites titkosítást.  
  - *Alacsony*: Az alacsony beállítás a 56 bites titkosítás használatával csak az ügyfélről a kiszolgálóra továbbított adatok titkosítását végzi.  
  
  Ha letiltja vagy nem konfigurálja ezt a beállítást, a távoli kapcsolatokhoz használni kívánt titkosítási szint nem kényszeríthető Csoportházirendon keresztül. A fontos FIPS-megfelelőség a rendszerkriptográfiai szolgáltatáson keresztül konfigurálható. A FIPS szabványnak megfelelő algoritmusok használata titkosításhoz, kivonatoláshoz és aláírási beállításokhoz Csoportházirendban (a számítógép konfigurációja \ Windows beállításai \ helyi házirend \ házirend beállítások menüpontban) A FIPS-kompatibilis beállítás titkosítja és visszafejti az ügyfél és a kiszolgáló között továbbított adatokat a kiszolgálóról az ügyfélre, a Federal Information Processing standard (FIPS) 140 titkosítási algoritmusokkal a Microsoft titkosítási moduljainak használatával. Akkor használja ezt a titkosítási szintet, ha az ügyfelek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikációhoz a legmagasabb szintű titkosítás szükséges.
  
  **Alapértelmezett**: Magas
  
### <a name="remote-management"></a>Távfelügyelet  

További információ: [Policy CSP-RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) a Windows dokumentációjában.  

- **Futtató hitelesítő adatok tárolásának tiltása**  
  Ügyfél alapszintű hitelesítése
  
  **Alapértelmezett**: Enabled
  
- **Alapszintű hitelesítés**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) szolgáltatás fogadja-e az egyszerű hitelesítést egy távoli ügyfélről. Ha engedélyezi ezt a házirend-beállítást, a WinRM szolgáltatás fogadja az egyszerű hitelesítést egy távoli ügyfélről. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM szolgáltatás nem fogadja el az egyszerű hitelesítést egy távoli ügyféltől.
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél-kivonatoló hitelesítés letiltása**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfele kivonatoló hitelesítést használ-e. Ha engedélyezi ezt a házirend-beállítást, a WinRM-ügyfél nem használ kivonatoló hitelesítést. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél kivonatoló hitelesítést használ.
  
  **Alapértelmezett**: Enabled
  
- **Titkosítatlan forgalom**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) szolgáltatás küld-e és fogad-e titkosítatlan üzeneteket a hálózaton keresztül. Ha engedélyezi ezt a házirend-beállítást, a Rendszerfelügyeleti webszolgáltatások ügyfele titkosítatlan üzeneteket küld és fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél csak a titkosított üzeneteket küldi vagy fogadja a hálózaton keresztül.  
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél titkosítatlan forgalma**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfél küld-e és fogad-e titkosítatlan üzeneteket a hálózaton keresztül. Ha engedélyezi ezt a házirend-beállítást, a Rendszerfelügyeleti webszolgáltatások ügyfele titkosítatlan üzeneteket küld és fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél csak a titkosított üzeneteket küldi vagy fogadja a hálózaton keresztül.
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél alapszintű hitelesítése**  
  Ezzel a házirend-beállítással felügyelheti, hogy a Rendszerfelügyeleti webszolgáltatások (WinRM) ügyfél alapszintű hitelesítést használ-e. Ha engedélyezi ezt a házirend-beállítást, a WinRM-ügyfél alapszintű hitelesítést használ. Ha a WinRM a HTTP-átvitel használatára van konfigurálva, a Felhasználónév és a jelszó küldése a hálózaton keresztül egyszerű szövegként történik. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a WinRM-ügyfél nem használ alapszintű hitelesítést.
  
  **Alapértelmezett**: Letiltva
  

### <a name="remote-procedure-call"></a>Távoli eljárás hívása  

További információ: [Policy CSP-RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) a Windows dokumentációjában.  

- **Nem hitelesített RPC-ügyfél beállításai**  
  Ezzel a házirend-beállítással szabályozható, hogy az RPC-kiszolgáló futtatókörnyezete hogyan kezelje az RPC-kiszolgálókhoz csatlakozó nem hitelesített RPC-ügyfeleket Ezzel a házirend-beállítással az összes RPC-alkalmazás hatással van. Tartományi környezetben ezt a házirend-beállítást körültekintően kell használni, mivel ez a funkció számos funkciót érint, beleértve a csoportházirend feldolgozását is. A házirend-beállítás módosításának visszaállításához manuális beavatkozásra van szükség az egyes érintett gépeken. Ez a házirend-beállítás soha nem alkalmazható tartományvezérlőre. Ha letiltja ezt a házirend-beállítást, az RPC-kiszolgáló futtatókörnyezete a "hitelesített" értéket használja a Windows-ügyfélen, és a "None" értéket a Windows Server azon verzióiban, amelyek támogatják ezt a házirend-beállítást. Ha nem konfigurálja ezt a házirend-beállítást, az továbbra is le lesz tiltva. Az RPC-kiszolgáló futtatókörnyezete úgy viselkedik, mintha engedélyezve volt a Windows-ügyfélhez használt "hitelesített" értékkel, valamint a "nincs" értékkel, amelyet ez a házirend-beállítás támogat. Ha engedélyezi ezt a házirend-beállítást, a rendszer az RPC-kiszolgáló futtatókörnyezetét arra utasítja, hogy korlátozza a gépen futó RPC-kiszolgálókhoz csatlakozó nem hitelesített RPC-ügyfeleket. Az ügyfél akkor tekinthető hitelesített ügyfélnek, ha nevesített csövet használ a kiszolgálóval való kommunikációhoz, vagy ha RPC-biztonságot használ. A nem hitelesített ügyfelek által elérhetővé tett RPC-felületek mentesülnek ettől a korlátozástól attól függően, hogy a házirend-beállítás kiválasztott értéke milyen.  
  - A *none* értékkel az összes RPC-ügyfél csatlakozhat a házirend-beállítást alkalmazó számítógépen futó RPC-kiszolgálókhoz. 
  - A hitelesítéssel csak a hitelesített RPC-ügyfelek (a fenti definíció alapján) csatlakozhatnak azon a számítógépen futó RPC-kiszolgálókhoz, amelyen a házirend-beállítás alkalmazva van. A rendszer kivételeket biztosít azokhoz az interfészekhez, amelyek kérték azokat. 
  - A *kivételek nélküli hitelesítés* lehetővé teszi, hogy csak a fenti definíción alapuló hitelesített RPC-ügyfelek csatlakozzanak a házirend-beállítást alkalmazó számítógépen futó RPC-kiszolgálókhoz. A kivételek nem engedélyezettek. Megjegyezés: Ez a házirend-beállítás csak a rendszer újraindítása után lesz alkalmazva.  

  **Alapértelmezett**: Hitelesített

### <a name="search"></a>Keresés  

További információ: [házirend-CSP – keresés](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) a Windows dokumentációjában.  

- **Titkosított elemek indexelésének letiltása**  
  Engedélyezi vagy tiltja az elemek indexelését. Ez a kapcsoló a Windows Search indexelő szolgáltatáshoz használható, amely azt szabályozza, hogy a rendszer indexeli-e a titkosított elemeket (például a Windows Information Protection (folyamatban lévő) védett fájlokat. A szabályzat engedélyezésekor a WIP által védett elemek indexelve lesznek, a velük kapcsolatos metaadatok pedig titkosítatlan helyen lesznek tárolva. A metaadatok között szerepel egyebek között a fájl elérési útja és módosításának dátuma. Ha a házirend le van tiltva, a rendszer nem indexeli a nem indexelt, és nem jeleníti meg az eredményeket a Cortana vagy a fájlkezelőben. A Fényképek és a Groove alkalmazás teljesítménye csökkenhet, ha nagy mennyiségű WIP-védelemmel ellátott médiafájl található az eszközön.
  
**Alapértelmezett**: Igen
  
### <a name="smart-screen"></a>Intelligens képernyő  

További információ: [Policy CSP-SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) a Windows dokumentációjában.  

- **Nem ellenőrzött fájlok végrehajtásának letiltása**  
  Nem ellenőrzött fájlok futtatásának letiltása a felhasználó számára. 
  - *Nincs konfigurálva* – az alkalmazottak figyelmen kívül hagyhatják a SmartScreen-figyelmeztetéseket, és kártékony fájlokat futtathatnak. 
  - *Igen* – az alkalmazottak nem hagyhatják figyelmen kívül a SmartScreen-figyelmeztetéseket, és nem futtathatnak rosszindulatú fájlokat.

  **Alapértelmezett**: Igen

<!-- Not currently available? - **Block unverified file download**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes
 --> 
- **SmartScreen megkövetelése alkalmazások és fájlok esetén**  
  Lehetővé teszi a rendszergazdáknak a SmartScreen konfigurálását Windows rendszeren.

  **Alapértelmezett**: Igen
  
### <a name="system"></a>Rendszer  

További információ: [Policy CSP – rendszer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) a Windows dokumentációjában.  

- **Rendszerindítási indítási illesztőprogram inicializálása**  
  Ezzel a házirend-beállítással megadhatja, hogy mely rendszerindítási illesztőprogramok legyenek inicializálva egy korai indítási antimalware rendszerindítási illesztőprogram által meghatározott besorolás alapján. A korai indítású antimalware rendszerindítási illesztőprogram a következő besorolásokat adhatja vissza minden rendszerindítási illesztőprogramhoz: 
  - *Jó*: Az illesztőprogram aláírása megtörtént, és a nem lett illetéktelenül módosítva.  
  - *Rossz* – az illesztőprogram kártevőként lett azonosítva. Azt javasoljuk, hogy ne engedélyezze az ismert hibás illesztőprogramok inicializálását. 
  - *Rossz, de szükséges a*rendszerindításhoz: Az illesztőprogram kártevőként lett azonosítva, de a számítógép nem indítható el sikeresen az illesztőprogram betöltése nélkül. 
  - *Ismeretlen* – ezt az illesztőprogramot a kártevő-észlelési alkalmazás nem tanúsította, és a korai indítású antimalware rendszerindítási illesztőprogram nem sorolta be.  

  Ha engedélyezi ezt a házirend-beállítást, kiválaszthatja, hogy mely rendszerindítási illesztőprogramokat szeretné inicializálni a számítógép következő indításakor. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást, a rendszerindítási illesztőprogramok helyesnek, ismeretlennek vagy hibásnak, de a rendszerindítási kritikusnak megfelelően vannak inicializálva, és a helytelenül meghatározott illesztőprogramok inicializálását a rendszer kihagyja. Ha a kártevő-észlelési alkalmazás nem tartalmaz korai indítású antimalware rendszerindítási illesztőprogramot, vagy ha a korai indítású kártevő-indítási illesztőprogram le van tiltva, akkor ez a beállítás nem lép érvénybe, és az összes rendszerindítási illesztőprogram inicializálva van.  
  
  **Alapértelmezett**: Jól ismert és rossz kritikus


### <a name="wi-fi"></a>Wi-Fi  

További információ: [Policy CSP-WiFi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) a Windows-dokumentációban.  

- **Internetes megosztás letiltása**  
  Megadja, hogy lehetséges-e az internetes megosztás az eszközön.  

  **Alapértelmezett**: Igen  

- **A Wi-Fi elérési pontokhoz való automatikus csatlakozás letiltása**  
  A Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése vagy letiltása az eszközön.  

  **Alapértelmezett**: Igen  
  
### <a name="windows-connection-manager"></a>Windows Csatlakozáskezelő  

További információ: [Policy CSP-WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) a Windows dokumentációjában.  

- **Nem tartományi hálózatokhoz való kapcsolódás letiltása**  
  Ezzel a házirend-beállítással megakadályozható, hogy a számítógépek egyszerre egy tartományalapú hálózathoz és egy nem tartományon alapuló hálózathoz csatlakozzanak. Ha ez a házirend-beállítás engedélyezve van, a számítógép a következő esetekben válaszol az automatikus és a manuális hálózati csatlakozási kísérletekre: 
  - Ha a számítógép már csatlakozik egy tartományalapú hálózathoz, az automatikus kapcsolódási kísérleteket a rendszer letiltja a nem tartományi hálózatokra irányuló összes automatikus kapcsolódási kísérletet. Ha a számítógép már csatlakozik egy nem tartomány alapú hálózathoz, a rendszer letiltja a tartományalapú hálózatokra irányuló automatikus kapcsolódási kísérleteket. 
  - A manuális kapcsolódási kísérlet akkor fordul elő, ha a számítógép már csatlakoztatva van egy nem tartomány alapú hálózathoz vagy egy, az Etherneten kívüli, más adathordozón található tartományalapú hálózathoz, és egy felhasználó egy további, a szabályzat megsértése miatti hálózathoz való csatlakozást kísérel meg létrehozni. beállítás, a meglévő hálózati kapcsolat megszakad, és a manuális kapcsolat engedélyezett. Ha a számítógép már csatlakoztatva van egy nem tartomány alapú hálózathoz vagy egy tartományalapú hálózathoz Ethernet-kapcsolaton keresztül, és egy felhasználó egy további, a házirend-beállítás megsértése miatti hálózatra irányuló manuális kapcsolatot próbál létrehozni, a meglévő Ethernet-kapcsolat karbantartva, és a manuális kapcsolódási kísérlet le van tiltva.  

  Ha a házirend-beállítás nincs konfigurálva vagy le van tiltva, a számítógépek egyszerre csatlakozhatnak a tartományhoz és a tartományhoz nem tartozó hálózatokhoz is.  

  **Alapértelmezett**: Enabled
  
### <a name="windows-defender"></a>Windows Defender  

További információ: [Policy CSP-Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) a Windows dokumentációjában.  

- **Bejövő üzenetek ellenőrzése**  
  Engedélyezi vagy engedélyezi az e-mailek vizsgálatát.
  
  **Alapértelmezett**: Igen  

- **Az Office-alkalmazások alárendelt folyamatának indítása**  
  Az Office-alkalmazások nem hozhatnak létre alárendelt folyamatokat. Ide tartozik a Word, az Excel, a PowerPoint, a OneNote és a hozzáférés. Ez egy tipikus kártevő-viselkedés, különösen olyan makró-alapú támadások esetében, amelyek az Office-alkalmazások használatával próbálnak meg rosszindulatú végrehajtható fájlokat elindítani vagy letölteni.
  
  **Alapértelmezett**: Letiltás
  
- **Defender-minta küldésének beleegyező típusa**  
  A Windows Defender felhasználói beleegyezési szintjét ellenőrzi az adatküldés során. Ha a szükséges engedély már meg lett adva, a Windows Defender elküldi azokat. Ha nem, (és ha a felhasználónak soha nem kell megadnia a kérdést), a felhasználói felület megadását kéri (ha a Defender/AllowCloudProtection engedélyezett) az adatok elküldése előtt.
  
  **Alapértelmezett**: Biztonságos minták automatikus küldése 
  
- **Aláírás-frissítési időköz (óra)**  
  Defender-aláírás frissítési időköze (óra)
  
  **Alapértelmezett**: 4
  
- **Parancsfájl letöltött adattartalom-végrehajtási típusa**  
  Defender-parancsfájl letöltött adattartalom-végrehajtási típusa
  
  **Alapértelmezett**: Letiltás
  
- **Hitelesítő adatok ellopási típusának tiltása**  
  A Windows Defender hitelesítőadat-őr virtualizálás-alapú biztonságot használ a titkok elkülönítésére, így csak a rendszerjogosultságú rendszerszoftverek férhetnek hozzájuk. A titkos kódokhoz való illetéktelen hozzáférés a hitelesítési adatok ellopását okozó (például pass-the-hash vagy pass-the-ticket típusú) támadásokhoz vezethetnek. A Windows Defender hitelesítőadat-őr megakadályozza ezeket a támadásokat az NTLM jelszó-kivonatok, a Kerberos-jegyek és az alkalmazások tartományi hitelesítő adatokként tárolt hitelesítő adatainak védelmével.
  
  **Alapértelmezett**: Engedélyezés

- **E-mail tartalom végrehajtásának típusa**  
  Ez a szabály blokkolja a következő fájltípusokat a Futtatás vagy a Microsoft Outlook vagy webmail szolgáltatásban (például Gmail.com vagy Outlook.com) látott e-mailből való indításkor: Végrehajtható fájlok (például. exe,. dll vagy. scr) parancsfájlok (például PowerShell. ps, VisualBasic. vbs vagy JavaScript. js fájl).
  
  **Alapértelmezett**: Letiltás
  
- **Hálózati védelem típusa**  
  Ez a szabályzat lehetővé teszi a hálózati védelem (Letiltás/naplózás) bekapcsolását a Windows Defender Exploit Guardben. A hálózatvédelem a Windows Defender Exploit Guard egyik funkciója, amely megvédi az alkalmazottakat az adathalászat-csalások, a biztonsági rések és az interneten található kártékony tartalmak elérésére alkalmas bármely alkalmazás használatával. Ez magában foglalja a harmadik féltől származó böngészőknek a veszélyes helyekhez való csatlakozásának megakadályozását. Az érték típusa egész szám. Ha engedélyezi ezt a beállítást, a hálózati védelem be van kapcsolva, és az alkalmazottak nem kapcsolhatják ki. A viselkedését a következő beállítások szabályozzák: Blokkolás és naplózás. Ha engedélyezi ezt a házirendet a "letiltás" beállítással, a felhasználók és az alkalmazások le vannak tiltva a veszélyes tartományokhoz való csatlakozáskor. Ezt a tevékenységet a Windows Defender Security Centerban tekintheti meg. Ha engedélyezi ezt a házirendet a "naplózás" beállítással, a felhasználók/alkalmazások nem lesznek letiltva a veszélyes tartományokhoz való csatlakozáskor. Ezt a tevékenységet azonban továbbra is láthatja a Windows Defender Security Centerban. Ha letiltja ezt a házirendet, a felhasználók/alkalmazások nem lesznek letiltva a veszélyes tartományokhoz való csatlakozáskor. A Windows Defender Security Centerban semmilyen hálózati tevékenység nem jelenik meg. Ha nem konfigurálja ezt a házirendet, a hálózati blokkolás alapértelmezés szerint le van tiltva.
  
  **Alapértelmezett**: Engedélyezés
  
- **Defender-ütemterv vizsgálatának napja**  
  Defender-ütemterv vizsgálatának napja.
  
  **Alapértelmezett**: Mindennap
  
- **Felhőbe szállított védelem**  
  A számítógép legjobb védelméhez a Windows Defender adatokat küld a Microsoftnak a talált problémákról. A Microsoft elemezni fogja ezeket az információkat, többet tudhat meg az Ön és más ügyfelek problémáit érintő problémákról, és továbbfejlesztett megoldásokat kínál.
  
  **Alapértelmezett**:  Igen  

- **A Defender vélhetően nemkívánatos alkalmazásának művelete**  
  A Windows Defender víruskereső vélhetően nemkívánatos alkalmazás-(PUA-) védelmi funkciója képes azonosítani és letiltani a PUAs a hálózaton lévő végpontokon való letöltés és telepítés során. Ezek az alkalmazások nem tekintendők vírusok, kártevők vagy más típusú fenyegetéseknek, de olyan végpontokon is végezhetnek műveleteket, amelyek hátrányosan befolyásolják a teljesítményüket vagy a használatukat. A PUA olyan alkalmazásokra is hivatkozhat, amelyeknek a megítélése szerint rossz hírnevük van. A tipikus PUA-viselkedés a következőket tartalmazza: Különböző típusú szoftver-árukapcsolás ad-befecskendezés a webböngészőkbe és a beállításjegyzék-optimalizálók a problémák észlelésére, a hibák kijavítására, de továbbra is a végponton maradnak, és nem tesznek módosítást vagy optimalizálást (más néven "gazember víruskereső" programokat). Ezek az alkalmazások növelhetik a kártevő szoftverrel fertőzött hálózat kockázatát, így a rosszindulatú fertőzések nehezebben azonosíthatók, és az informatikai erőforrások az alkalmazások tisztításával is felhasználhatók.  
  
  **Alapértelmezett**: Letiltás  

- **Parancsfájl által eltorzított kód típusa**  
  A kártevők és egyéb fenyegetések megpróbálják eltorzítani vagy elrejteni a kártékony kódokat bizonyos parancsfájlokban. Ez a szabály akadályozza meg, hogy a rendszer ne futtasson olyan parancsfájlokat, amelyek nem futtathatók.
  
  **Alapértelmezett**: Letiltás
  
- **Cserélhető meghajtók vizsgálata teljes vizsgálat során**  
  Lehetővé teszi a Windows Defender számára a kártékony és nemkívánatos szoftverek keresését a cserélhető meghajtókon (például flash meghajtókon) a teljes vizsgálat során. A Windows Defender víruskereső a végrehajtás előtt megkeresi az USB-eszközökön található összes fájlt.
  
  **Alapértelmezett**: Igen  
  
- **Archív fájlok ellenőrzése**  
  Defender-vizsgálat archív fájljai.
  
  **Alapértelmezett**: Igen
  
- **Viselkedés figyelése**  
  Engedélyezi vagy engedélyezi a Windows Defender viselkedésének figyelését. A Windows 10 rendszerbe ágyazott érzékelők begyűjtik és feldolgozzák az operációs rendszer viselkedési jeleit, és elküldik az érzékelő adatait a Microsoft Defender ATP privát, elkülönített, Felhőbeli példányának.
  
  **Alapértelmezett**: Igen

- **Hálózati mappákból megnyitott fájlok vizsgálata**  
  Ha a fájlok csak olvashatók, a felhasználó nem tudja eltávolítani az észlelt kártevőket.
  
  **Alapértelmezett**: Igen

- **Nem megbízható USB-folyamat típusa**  
  Ezzel a szabállyal a rendszergazdák megakadályozhatják az aláíratlan vagy nem megbízható végrehajtható fájlok futtatását USB cserélhető meghajtókról, beleértve az SD-kártyákat is.
  
  **Alapértelmezett**: Letiltás
  
- **Office-alkalmazások egyéb folyamat-injektálási típusa**  
  Az Office-alkalmazások, például a Word, az Excel, a PowerPoint és a OneNote, nem tudnak kódot beszúrni más folyamatokra. Ezt általában a kártevők használják rosszindulatú kód futtatására arra az kísérletre, hogy el lehessen rejteni a tevékenységet a víruskereső keresőmotorokból.
  
  **Alapértelmezett**:  Letiltás
  
- **Office-makróvédelmi kód engedélyezése Win32 importálási típus**  
  A kártevők a Win32 DLL-fájlok importálásához és betöltéséhez használhatnak makróvírus-kódot az Office-fájlokban, amelyek ezután API-hívások készítésére használhatók a rendszeren belüli további fertőzés engedélyezéséhez. Ez a szabály megkísérli letiltani a Win32 DLL-ek importálására képes makrót tartalmazó Office-fájlokat. Ide tartozik a Word, az Excel, a PowerPoint és a OneNote.
  
  **Alapértelmezett**: Letiltás  
  
- **Defender Cloud Block-szint**  
  A Defender Cloud Block szintje.
  
  **Alapértelmezett**: Nincs konfigurálva

- **Valós idejű figyelés**  
  A Defender valós idejű figyelést igényel.
  
  **Alapértelmezett**: Igen
  
- **Office-alkalmazások végrehajtható tartalom létrehozási vagy indítási típusa**  
  Ez a szabály a végrehajtható fájlokat létrehozó vagy indító gyanús és kártékony bővítmények és parancsfájlok (bővítmények) által használt jellemző viselkedéseket célozza meg. Ez egy tipikus kártevő-módszer. Az Office-alkalmazások nem használják a bővítményeket. Ezek a bővítmények általában a Windows Scripting Host (. wsh fájlok) használatával futtatnak bizonyos feladatokat automatizáló vagy felhasználó által létrehozott kiegészítő funkciókat biztosító parancsfájlokat.
  
  **Alapértelmezett**: Letiltás

### <a name="windows-ink-workspace"></a>Windows Ink-munkaterület  

További információ: [Policy CSP-WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) a Windows dokumentációjában.  

- **Szabadkézi munkaterület**  
  Megadja, hogy engedélyezi-e a felhasználó számára a szabadkézi munkaterület elérését. 
  - Letiltva – a szabadkézi munkaterület hozzáférése le van tiltva. A szolgáltatás ki van kapcsolva.
  - *Engedélyezve* – a tinta munkaterület funkció be van kapcsolva, de a felhasználó nem férhet hozzá a zárolási képernyő felett.
  - *Nincs konfigurálva* – a tinta munkaterület funkció be van kapcsolva, és a felhasználó a zárolási képernyő felett is használhatja.  

  **Alapértelmezett**: Enabled
 
### <a name="windows-powershell"></a>Windows PowerShell  

További információ: [Policy CSP-WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) a Windows dokumentációjában.  

- **Rendszerhéj-rendszerhéj parancsfájl-blokkolási naplózása**  
  Ezzel a házirend-beállítással engedélyezhető a PowerShell-parancsfájl összes bemenetének naplózása a Microsoft-Windows-PowerShell/operatív eseménynaplóba. Ha engedélyezi ezt a házirend-beállítást, a Windows PowerShell naplózza a parancsok, parancsfájl-blokkok, függvények és parancsfájlok feldolgozását – akár interaktív módon, akár automatizálás útján. Ha letiltja ezt a házirend-beállítást, a PowerShell-parancsfájl bemenetének naplózása le van tiltva. Ha engedélyezi a parancsfájl-blokkoló naplózását, a PowerShell emellett naplózza az eseményeket, amikor egy parancs, parancsfájl-blokk, függvény vagy parancsfájl meghívása elindul vagy leáll. A meghívásos naplózás engedélyezése nagy mennyiségű eseménynaplót generál. Megjegyezés: Ez a házirend-beállítás a számítógép konfigurációja és a felhasználó konfigurációja területen található a Csoportházirend szerkesztőben. A számítógép-konfigurációs házirend beállítása elsőbbséget élvez a felhasználói konfigurációs házirend beállításával szemben.
  
  **Alapértelmezett**: Enabled
 
## <a name="next-steps"></a>További lépések  

[Az aktuális alapverzió megtekintése](security-baseline-settings-mdm.md)  
[Profilok frissítése új alapverzió használatára](security-baselines.md#change-the-baseline-instance-for-a-profile)
