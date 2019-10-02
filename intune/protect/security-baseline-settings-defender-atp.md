---
title: Az Intune biztonsági alapkonfigurációinak beállításai a Microsoft Defender komplex veszélyforrások elleni védelemhez
titleSuffix: Microsoft Intune
description: Az Intune által támogatott biztonsági alapbeállítások a Microsoft Defender komplex veszélyforrások elleni védelem kezeléséhez
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eee3d4187dd513cd3945e86aff478fe96b341660
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729503"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>A Microsoft Defender komplex veszélyforrások elleni védelem alapkonfigurációjának beállításai az Intune-ban

Tekintse meg a Microsoft Defender komplex veszélyforrások elleni védelmet (korábban a Windows Defender komplex veszélyforrások elleni védelem) a Microsoft Intune által támogatott alapkonfiguráció-beállításokat. A komplex veszélyforrások elleni védelem (ATP) alapértékek az ATP ajánlott konfigurációját jelentik, és előfordulhat, hogy más biztonsági alapkonfigurációk esetében nem egyeznek az alapértékekkel.  

A Microsoft Defender komplex veszélyforrások elleni védelem alapterve akkor érhető el, ha a környezet megfelel a [Microsoft Defender komplex veszélyforrások elleni védelem](advanced-threat-protection.md#prerequisites)használatának előfeltételeinek. 

Ez az alapkonfiguráció fizikai eszközökre van optimalizálva, és jelenleg nem ajánlott virtuális gépeken (VM) vagy VDI-végpontokon használni. Bizonyos alapbeállítások befolyásolhatják a távoli interaktív munkameneteket a virtualizált környezetekben. További információ: a [Microsoft DEFENDER ATP biztonsági](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) alapkonfigurációjának nagyobb megfelelősége a Windows dokumentációjában.


> [!NOTE]  
> Az ATP alapkonfigurációjának beállításai **előzetes**verzióban érhetők el. Az előzetes verzióban a rendelkezésre álló beállítások listája és a tartalom megjelenítési sorrendje nem egyezik meg a portálon elérhetővel.  
>
> Ha az alapkonfiguráció beállításai nem előzetes verziójúak, ez a tartalom frissülni fog az Intune által támogatott biztonsági alapkonfigurációk aktuális listájának megjelenítéséhez.

## <a name="application-guard"></a>Application Guard  
További információ: [WINDOWSDEFENDERAPPLICATIONGUARD CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) a Windows dokumentációjában.  

A Microsoft Edge használata közben a Microsoft Defender Application Guard védi a környezetet a szervezete által nem megbízható helyekről. Ha a felhasználók olyan helyeket látogatnak meg, amelyek nem szerepelnek az elszigetelt hálózati határon, a helyek egy Hyper-V virtuális böngészési munkamenetben nyílnak meg. A megbízható helyeket a hálózat határa határozza meg.  

- **Application Guard** - *Settings/AllowWindowsDefenderApplicationGuard*  
  Válassza az *Igen* lehetőséget a funkció bekapcsolásához, amely nem megbízható helyeket nyit meg egy Hyper-V virtualizált tallózási tárolóban. Ha a *nincs konfigurálva*értékre van állítva, a rendszer minden helyet (megbízható és nem megbízható) nyit meg az eszközön, és nem virtualizált tárolóban.  

  **Alapértelmezett**: Igen
 
  - **Külső tartalom a vállalati webhelyek** - *beállításai/BlockNonEnterpriseContent*  
    Válassza az *Igen* lehetőséget a nem jóváhagyott webhelyekről származó tartalom betöltésének letiltásához. Ha a *nincs konfigurálva*értékre van állítva, a nem vállalati webhelyek megnyithatók az eszközön. 
 
    **Alapértelmezett**: Igen

  - **Vágólap viselkedési** - *beállításai/ClipboardSettings*  
    Válassza ki, hogy mely másolási és beillesztési műveletek engedélyezettek a helyi számítógép és az Application Guard virtuális böngésző között.  A lehetőségek a következők:
    - *Nincs konfigurálva*  
    - A *both* -adatok nem vihetők át a számítógép és a virtuális böngésző között.  
    - *Gazdagép tárolóba való letiltása* – az adatok nem vihetők át a számítógépről a virtuális böngészőbe.
    - *Tároló* tárolásának letiltása – az adatok nem vihetők át a virtuális böngészőből a gazdagép számítógépére.
    - *Nincs* – nincs blokkolás a tartalomhoz.  

    **Alapértelmezett**: Mindkettő letiltása  

- **Windows hálózati elkülönítési házirend – vállalati hálózati tartománynevek**  
  További információ: [Policy CSP-NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) a Windows dokumentációjában.
  
  A felhőben üzemeltetett vállalati erőforrások (tartomány, IP-címtartományok és hálózati határok) listájának megadása, amelyet az Application Guard vállalati helyként kezel.  

  **Alapértelmezett**: SecurityCenter.Windows.com

## <a name="application-reputation"></a>Alkalmazás hírneve  

További információ: [Policy CSP-SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) a Windows dokumentációjában.

- **Nem ellenőrzött fájlok végrehajtásának letiltása**  
    Nem ellenőrzött fájlok futtatásának letiltása a felhasználó számára. Ha a *nincs konfigurálva*értékre van állítva, az alkalmazottak figyelmen kívül hagyhatják a SmartScreen figyelmeztetéseit, és kártékony fájlokat futtathatnak. Állítsa *Igen* értékre, így az alkalmazottak nem hagyhatják figyelmen kívül a SmartScreen figyelmeztetéseit, és nem futtathatnak rosszindulatú fájlokat.  
  
    **Alapértelmezett**: Igen

- **SmartScreen megkövetelése alkalmazások és fájlok esetén**  
  Állítsa az *Igen* értékre a SmartScreen Windows rendszerhez való engedélyezéséhez.  

  **Alapértelmezett**: Igen

## <a name="attack-surface-reduction"></a>Támadási felület csökkentése  

- **Az Office-alkalmazások alárendelt folyamatának indítása**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) –ha blokkolásra van beállítva, az Office-alkalmazások nem hozhatnak létre alárendelt folyamatokat. Az Office-alkalmazások közé tartozik a Word, az Excel, a PowerPoint, a OneNote és a hozzáférés. Egy alárendelt folyamat létrehozása tipikus kártevő-viselkedés, különösen olyan makró-alapú támadások esetén, amelyek az Office-alkalmazások használatával kísérlik meg a rosszindulatú végrehajtható fájlok indítását vagy letöltését.  

  **Alapértelmezett**: Letiltás

- **Parancsfájl letöltött adattartalom-végrehajtási típusa**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – megadhatja az észlelési szintet a letöltött vagy a telepíteni próbált, vélhetően nemkívánatos alkalmazások számára.  

  **Alapértelmezett**: Letiltás 

- **Hitelesítő adatok ellopási típusának tiltása**  
  Állítsa az *Engedélyezés* elemre a származtatott tartományi hitelesítő adatoknak [a hitelesítő adatokkal](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard)való ellátásához. A Windows Defender hitelesítőadat-őr virtualizálás-alapú biztonságot használ a titkok elkülönítésére, így csak a rendszerjogosultságú rendszerszoftverek férhetnek hozzájuk. A titkos kódokhoz való illetéktelen hozzáférés a hitelesítési adatok ellopását okozó (például pass-the-hash vagy pass-the-ticket típusú) támadásokhoz vezethetnek. A Windows Defender hitelesítőadat-őr megakadályozza ezeket a támadásokat az NTLM jelszó-kivonatok, a Kerberos-jegyek és az alkalmazások tartományi hitelesítő adatokként tárolt hitelesítő adatainak védelmével.  

  **Alapértelmezett**: Engedélyezés

- **E-mail tartalom végrehajtásának típusa**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – ha a *blokkolás*értékre van állítva, ez a szabály blokkolja a következő fájltípusokat a Microsoft Outlookban vagy webmailben (például gmail.com vagy Outlook.com) látott e-mailből:  

  - Végrehajtható fájlok (például. exe,. dll vagy. scr)  
  - Parancsfájlok (például PowerShell. ps, VisualBasic. vbs vagy JavaScript. js fájl)  
  - Parancsfájl-archiválási fájlok  

  **Alapértelmezett**: Letiltás

- **Adobe Reader indítása alárendelt folyamatban**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – ennek a szabálynak az *engedélyezésével* letilthatja az Adobe Reader számára az alárendelt folyamat létrehozását. A közösségi mérnöki vagy biztonsági rések révén a kártevők további hasznos adatokat tölthetnek le és indíthatnak el, és kitörhetnek az Adobe Readerből.  

  **Alapértelmezett**: Engedélyezés

- **Parancsfájl által eltorzított kód típusa**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – a kártevők és egyéb fenyegetések megpróbálják eltorzítani vagy elrejteni a kártékony kódokat bizonyos parancsfájlokban. Ez a szabály akadályozza meg, hogy a rendszer ne futtasson olyan parancsfájlokat, amelyek nem futtathatók.  
    
  **Alapértelmezett**: Letiltás

- **Nem megbízható USB-folyamat típusa**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) –ha a blokkolt, aláíratlan vagy nem megbízható végrehajtható fájlokat USB cserélhető meghajtókról és SD-kártyákból állítja be, nem futtatható.

  A végrehajtható fájlok a következők:
  - Végrehajtható fájlok (például. exe,. dll vagy. scr)
  - Parancsfájlok (például PowerShell. ps, VisualBasic. vbs vagy JavaScript. js fájl)  

  **Alapértelmezett**: Letiltás

- **Office-alkalmazások egyéb folyamat-injektálási típusa**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) –ha blokkolásra van beállítva, az Office-alkalmazások, például a Word, az Excel, a PowerPoint és a OneNote, nem adhatnak hozzá kódot más folyamatokhoz. A programkódot általában a kártevők használják arra, hogy rosszindulatú kódot futtassanak a tevékenységek víruskeresőből való elrejtésére tett kísérlet során.  

  **Alapértelmezett**: Letiltás

- **Office-makróvédelmi kód engedélyezése Win32 importálási típus**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – ha a *blokkolás*értékre van állítva, akkor ez a szabály megkísérli letiltani a Win32 DLL-eket importáló makrókat tartalmazó Office-fájlokat. Az Office-fájlok a következők: Word, Excel, PowerPoint és OneNote. A kártevők az Office-fájlokban lévő makróvírus használatával importálhatók és betölthetők a Win32 DLL-fájlok, amelyek ezután API-hívásokkal teszik lehetővé a további fertőzéseket a rendszeren.  

  **Alapértelmezett**: Letiltás

- **Office kommunikációs alkalmazások indítása alárendelt folyamatban**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – ha az *Engedélyezés*beállítás értéke, ez a szabály megakadályozza, hogy az Outlook alárendelt folyamatokat hozzon létre. Ha letiltja egy alárendelt folyamat létrehozását, ez a szabály védelmet biztosít a közösségi mérnöki támadásokkal szemben, és megakadályozza, hogy a programkód felhasználja a biztonsági rést az Outlookban.  

  **Alapértelmezett**: Engedélyezés

- **Office-alkalmazások végrehajtható tartalom létrehozási vagy indítási típusa**  
  [Támadási felület csökkentési szabálya](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) –ha blokkolásra van beállítva, az Office-alkalmazások nem hozhatnak létre végrehajtható tartalmat. Az Office-alkalmazások közé tartozik a Word, az Excel, a PowerPoint, a OneNote és a hozzáférés.  

  Ez a szabály a végrehajtható fájlokat létrehozó vagy indító gyanús és kártékony bővítmények és parancsfájlok (bővítmények) által használt jellemző viselkedéseket célozza meg. Ez egy tipikus kártevő-módszer. Az Office-alkalmazások nem használják a bővítményeket. Ezek a bővítmények általában a Windows Scripting Host (. wsh fájlok) használatával futtatnak bizonyos feladatokat automatizáló vagy felhasználó által létrehozott kiegészítő funkciókat biztosító parancsfájlokat.

  **Alapértelmezett**: Letiltás

## <a name="bitlocker"></a>BitLocker  

További információ a [BitLocker csoportházirend beállítások](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) a Windows dokumentációjában.  

- **Eszközök titkosítása**  
  Válassza az *Igen* lehetőséget a BitLocker-eszközök titkosításának engedélyezéséhez. Az eszköz hardverének és Windows-verziójától függően előfordulhat, hogy az eszköz felhasználóinak meg kell győződnie arról, hogy az eszközön nincs harmadik féltől származó titkosítás. A Windows-titkosítás bekapcsolása, miközben a harmadik féltől származó titkosítás aktív, a rendszer instabillá teszi az eszközt.  

   **Alapértelmezett**: Igen

- **Bites zárolás cserélhető meghajtó házirendje**  
  A szabályzat értékei határozzák meg a BitLocker által a cserélhető meghajtók titkosításához használt rejtjel erősségét. A vállalatok a fokozott biztonság titkosítási szintjét vezérlik (az AES-256 erősebb, mint az AES-128). Ha az *Igen* lehetőséget választja a beállítás engedélyezéséhez, beállíthatja a titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtókhoz, az operációsrendszer-meghajtókhoz és a cserélhető adatmeghajtókhoz. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást. 

  A cserélhető meghajtókra vonatkozó biztonsági szabályzatok esetében konfigurálja a következő beállításokat:

  - **Titkosítás megkövetelése írási hozzáféréshez**  
    **Alapértelmezett**: Igen

  - **Titkosítási módszer**  
    **Alapértelmezett**: AES 128bit CBC

- **Bit Locker rögzített meghajtó szabályzata**  
  A szabályzat értékei határozzák meg a BitLocker által a rögzített meghajtók titkosításához használt rejtjel erősségét. A vállalatok vezérelhetik a fokozott biztonság titkosítási szintjét (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, beállíthatja a titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtókhoz, az operációsrendszer-meghajtókhoz és a cserélhető adatmeghajtókhoz. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.

  A bit Locker rögzített meghajtó házirendje beállításnál adja meg a következő beállításokat:

  - **Titkosítás megkövetelése írási hozzáféréshez**  
    **Alapértelmezett**: Igen

  - **Titkosítási módszer**  
    **Alapértelmezett**: AES-128bit XTS

- **Bites zárolás rendszermeghajtó-házirendje**  
  A szabályzat értékei határozzák meg a BitLocker által a rendszermeghajtó titkosításához használt rejtjel erősségét. A vállalatok a fokozott biztonság érdekében érdemes szabályozni a titkosítási szintet (az AES-256 erősebb, mint az AES-128). Ha engedélyezi ezt a beállítást, beállíthatja a titkosítási algoritmust és a kulcs titkosítási erősségét a rögzített adatmeghajtókhoz, az operációsrendszer-meghajtókhoz és a cserélhető adatmeghajtókhoz. A rögzített és az operációsrendszer-meghajtók esetében javasoljuk, hogy használja a XTS-AES algoritmust. A cserélhető meghajtók esetében az AES-CBC 128-bit vagy az AES-CBC 256-bit használatát kell használnia, ha a meghajtót olyan más eszközök használják, amelyeken nem fut a Windows 10, a 1511-es vagy újabb verzió. A titkosítási módszer módosítása nincs hatással, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ezekben az esetekben a rendszer figyelmen kívül hagyja ezt a házirend-beállítást.  

  A következő beállítások megadásával konfigurálhatja a rendszermeghajtó-házirendet:  

  - **Titkosítási módszer**  
    **Alapértelmezett**: AES-128bit XTS

## <a name="device-control"></a>Eszköz vezérlése  

- **Cserélhető meghajtók vizsgálata teljes vizsgálat során**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) – ha az *Igen*értékre van állítva, a Defender megkeresi a kártékony és nemkívánatos szoftvereket a cserélhető meghajtókon, például a flash meghajtókat a teljes vizsgálat során. A Defender víruskereső az USB-eszközökön lévő összes fájlt megvizsgálja az USB-eszközön lévő fájlok futtatása előtt.

  Kapcsolódó beállítás a listában: *Defender/AllowFullScanOnMappedNetworkDrives*  

  **Alapértelmezett**: Igen

- **A kernel DMA-védelemmel nem kompatibilis külső eszközök enumerálása**  
   Lásd: *DmaGuard/DeviceEnumerationPolicy* a [szabályzat CSP-DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  Ez a szabályzat további biztonságot nyújt a külső DMA-kompatibilis eszközökön. Ez lehetővé teszi a külső DMA-kompatibilis eszközök enumerálásának nagyobb mértékű szabályozását, amely nem kompatibilis a DMA-eszköz memóriájának elkülönítésével és a munkaelkülönítéssel.

  Ez a szabályzat csak akkor lép érvénybe, ha a rendszer belső vezérlőprogramja támogatja a kernel DMA védelmét. A kernel DMA-védelem olyan platform-szolgáltatás, amely nem vezérelhető házirend vagy egy eszköz felhasználója számára. A rendszernek a gyártáskor támogatottnak kell lennie. 

  Annak ellenőrzéséhez, hogy a rendszer támogatja-e a kernel DMA-védelmet, futtassa az MSINFO32. exe fájlt a rendszeren, és tekintse át a *kernel DMA Protection* mezőt az összefoglalás lapon.  

  A lehetőségek a következők: 
  - *Alapértelmezett eszköz* – a bejelentkezés vagy a képernyő zárolásának feloldása után az eszközök a DMA újramegfeleltetésével kompatibilis illesztőprogramokat bármikor fel lehet sorolni. A nem kompatibilis illesztőprogramok DMA-újramegfeleltetésével rendelkező eszközök enumerálása csak azt követően történik meg, hogy a felhasználó feloldja a képernyőt.
  - Minden, az összes külső DMA-kompatibilis PCIe eszköz enumerálása bármikor megtörténik
  - A DMA-újramegfeleltetéssel kompatibilis illesztőprogramokat tartalmazó *összes* eszköz letiltását bármikor megadhatja. A nem kompatibilis illesztőprogramokat a DMA-újramegfeleltetéssel rendelkező eszközök soha nem fogják tudni elindítani és végrehajtani a DMA-t bármikor.

  **Alapértelmezett**: Eszköz alapértelmezése

- **Hardvereszközök telepítése eszköz-azonosítók alapján**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) – ezzel a szabályzattal megadhatja Plug and Play hardver-azonosítók és kompatibilis azonosítók listáját azon eszközök esetében, amelyeket a Windows megakadályoz a telepítésben. Ez a házirend-beállítás elsőbbséget élvez minden más olyan házirend-beállítással szemben, amely lehetővé teszi, hogy a Windows telepítsen egy eszközt. Ha engedélyezi ezt a házirend-beállítást (a *hardveres eszközök telepítésének*letiltására van beállítva), a Windows megakadályozza, hogy olyan eszközt telepítsen, amelynek hardver-azonosítója vagy kompatibilis azonosítója megjelenik a létrehozott listában. Ha engedélyezi ezt a házirend-beállítást egy távoli asztali kiszolgálón, a házirend a megadott eszközök távoli asztali ügyfélről a távoli asztali kiszolgálóra való átirányítását befolyásolja. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást (a *hardveres eszközök telepítésének engedélyezésére*van beállítva), az eszközök az engedélyezett módon telepíthetik és frissíthetik a beállításokat, vagy más házirend-beállítások is megtiltják azokat.  

  **Alapértelmezett**: Hardvereszköz telepítésének letiltása  

  Ha a *hardveres eszköz telepítésének letiltása* lehetőség van kiválasztva, a következő beállítások érhetők el.
  - **A megfelelő hardvereszközök eltávolítása**  
    Ez a beállítás csak akkor érhető el, ha az *eszköz azonosítói alapján* a hardvereszköz telepítése *blokkolja a hardveres eszközök telepítését*.  

    **Alapértelmezett**: *Nincs alapértelmezett konfiguráció*

  - **A letiltott hardveres eszközök azonosítói**  
    Ez a beállítás csak akkor érhető el, ha az *eszköz azonosítói alapján* a hardvereszköz telepítése *blokkolja a hardveres eszközök telepítését*. A beállítás megadásához bontsa ki a beállítást, válassza a **+ Hozzáadás**lehetőséget, majd adja meg a letiltani kívánt hardvereszköz-azonosítót.  

    **Alapértelmezett**: *Nincsenek blokkolt eszközök*  

- **Közvetlen memória-hozzáférés letiltása**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) – ezzel a házirend-beállítással letilthatja a közvetlen memória-hozzáférést (DMA) az eszközön lévő összes melegen csatlakoztatható PCI-porthoz, amíg a felhasználó be nem jelentkezik a Windowsba. Miután a felhasználó bejelentkezik, a Windows feljegyzi a gazdagéphez csatlakozó PCI-portokhoz csatlakozó PCI-eszközöket. Minden alkalommal, amikor a felhasználó zárolja a gépet, a rendszer letiltja a DMA-t a gyermekek nélküli gyors csatlakozású PCI-portok esetében, amíg a felhasználó újra be nem jelentkezik. A gép zárolásának feloldása után már enumerált eszközök továbbra is működni fognak, amíg le nem húzta a gépet. 

  Ez a házirend-beállítás csak akkor lép érvénybe, ha a BitLocker vagy az eszköz titkosítása engedélyezve van.  

  **Alapértelmezett**: Igen


- **Hardvereszközök telepítése telepítési osztályok szerint**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) – ezzel a szabályzattal megadhatja az eszközök telepítési osztályának globálisan egyedi azonosítókat (GUID azonosítókat) tartalmazó listáját, amely megakadályozza a Windows telepítését. Ez a házirend-beállítás elsőbbséget élvez minden más olyan házirend-beállítással szemben, amely lehetővé teszi, hogy a Windows telepítsen egy eszközt. Ha engedélyezi ezt a házirend-beállítást (a *hardveres eszközök telepítésének*letiltására van beállítva), a Windows nem tudja telepíteni vagy frissíteni azokat az eszközillesztőket, amelyek az eszköz telepítési OSZTÁLYÁNAK GUID azonosítói megjelennek a létrehozott listában. Ha engedélyezi ezt a házirend-beállítást egy távoli asztali kiszolgálón, a házirend-beállítás a megadott eszközök távoli asztali ügyfélről a távoli asztali kiszolgálóra való átirányítását befolyásolja. Ha letiltja vagy nem konfigurálja ezt a házirend-beállítást (a *hardveres eszközök telepítésének engedélyezésére*van beállítva), a Windows telepítheti és frissítheti az eszközöket az engedélyezett módon, illetve megakadályozhatja más házirend-beállítások alapján.  

  **Alapértelmezett**: Hardvereszköz telepítésének letiltása

  Ha a *hardveres eszköz telepítésének letiltása* lehetőség van kiválasztva, a következő beállítások érhetők el.  

  - **A megfelelő hardvereszközök eltávolítása**  
    Ez a beállítás csak akkor érhető el, ha a *telepítési osztályok által telepített hardvereszközök telepítése* *blokkolja a hardvereszközök telepítését*.  
 
    **Alapértelmezett**: *Nincs alapértelmezett konfiguráció*  

  - **A letiltott hardveres eszközök azonosítói**  
    Ez a beállítás csak akkor érhető el, ha a telepítési osztályok által telepített hardvereszközök telepítése blokkolja a hardvereszközök telepítését. A beállítás megadásához bontsa ki a beállítást, válassza a **+ Hozzáadás**lehetőséget, majd adja meg a letiltani kívánt hardvereszköz-azonosítót.  
 
    **Alapértelmezett**: *Nincsenek blokkolt eszközök*

## <a name="endpoint-detection-and-response"></a>Végpontok észlelése és válasza  
További információ: [WINDOWSADVANCEDTHREATPROTECTION CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) a Windows dokumentációjában.  

- **Telemetria jelentéskészítés gyakoriságának** - *konfigurálása/TelemetryReportingFrequency*  

  A Microsoft Defender komplex veszélyforrások elleni védelem telemetria jelentéskészítési gyakoriságának gyorsítása.  

  **Alapértelmezett**: Igen

- **Minta megosztása minden fájl** - *konfiguráció/SampleSharing*  

  Visszaadja vagy beállítja a Microsoft Defender komplex veszélyforrások elleni védelem minta-megosztási konfigurációs paraméterét.  

  **Alapértelmezett**: Igen

## <a name="exploit-protection"></a>Védelem kiaknázása  

- **Védelem XML-kódjának kiaknázása**  
  További információkért lásd: a Windows dokumentációjának biztonsági réseket kihasználó [védelmi konfigurációk importálása, exportálása és üzembe helyezése](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml) .  

  Lehetővé teszi a rendszergazda számára egy olyan konfiguráció kiküldését, amely a kívánt rendszer-és alkalmazás-kockázatcsökkentő beállításokat jelképezi a szervezet összes eszközén. A konfigurációt egy XML-fájl jelképezi. 

  A védelem kiaknázása alkalmazásával megvédheti az eszközöket olyan kártevők ellen, amelyek kihasználják a támadásokat és megfertőzik azokat. A Windows biztonsági alkalmazás vagy a PowerShell használatával hozhat létre kockázatcsökkentő (más néven konfiguráció) készletet. Ezt követően exportálhatja ezt a konfigurációt XML-fájlként, és megoszthatja azt több, a hálózaton található géppel, hogy mindegyiknek ugyanazokat a kockázatcsökkentő beállításokat adja meg.
 
  Egy meglévő EMET konfigurációs XML-fájlt is konvertálhat, és importálhatja a biztonsági rés kiaknázása konfigurációs XML-fájlba.

- **Biztonsági rés kiaknázásának felülbírálásának letiltása**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – az *Igen* érték megadásával megakadályozhatja, hogy a felhasználók módosítsák a Windows Defender Security Center a védelmi beállítások kiaknázása területén. Ha letiltja vagy nem konfigurálja ezt a beállítást, a helyi felhasználók módosításokat végezhetnek a védelmi beállítások kiaknázása területen.  
  **Alapértelmezett**: Igen  

- **Vezérelt mappák elérése**  
  Lásd: [Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications) és [Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) 
  
   Fájlok és mappák védelme a nemkívánatos alkalmazások által végrehajtott, jogosulatlan módosítások ellen.

  **Alapértelmezett**: Vizsgálati mód

## <a name="web--network-protection"></a>Web & hálózati védelem  

- **Hálózati védelem típusa**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) – ez a szabályzat lehetővé teszi a hálózati védelem be-és kikapcsolását a Windows Defender Exploit Guard-ben. A hálózatvédelem a Windows Defender Exploit Guard egyik funkciója, amely megvédi az alkalmazottakat az adathalászat-csalások, a biztonsági rések és az interneten található kártékony tartalmak elérésére alkalmas bármely alkalmazás használatával. Ez magában foglalja a harmadik féltől származó böngészőknek a veszélyes helyekhez való csatlakozásának megakadályozását.  

  Ha az *Engedélyezés* vagy a *naplózás mód*értékre van állítva, a felhasználók nem kapcsolhatják ki a hálózati védelmet, és a Windows Defender Security Center segítségével megtekinthetik a kapcsolódási kísérletekkel kapcsolatos információkat.  
 
  - Az *Engedélyezés* funkció letiltja a felhasználókat és az alkalmazásokat a veszélyes tartományokhoz való csatlakozáshoz.  
  - A *vizsgálati mód* nem blokkolja a felhasználókat és az alkalmazásokat a veszélyes tartományokhoz való csatlakozáshoz.  

  Ha a *felhasználó által definiált*értékre van állítva, a felhasználók és az alkalmazások nem blokkolják a veszélyes tartományokhoz való kapcsolódást, és a kapcsolatok információi nem érhetők el a Windows Defender Security Centerban.  

  **Alapértelmezett**: Vizsgálati mód

- **SmartScreen megkövetelése a Microsoft Edge-hez**  
  [Böngésző/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) – a Microsoft Edge a Windows Defender SmartScreen (bekapcsolt) használatával védi a felhasználókat a lehetséges adathalászat-csalások és kártevő szoftverek alapértelmezés szerint. Alapértelmezés szerint ez a házirend engedélyezve van (az *Igen*értékre van állítva), és ha engedélyezve van, megakadályozza, hogy a felhasználók kikapcsolják a Windows Defender SmartScreen szolgáltatást.  Ha az eszközre vonatkozó érvényes házirend nincs konfigurálva, a felhasználók kikapcsolhatják a Windows Defender SmartScreen szolgáltatását, amely nem gondoskodik az eszköz védelem nélküli állapotáról.  

  **Alapértelmezett**: Igen
  
- **Rosszindulatú hely elérésének letiltása**  
  [Böngésző/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) – alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Windows Defender SmartScreen figyelmeztetéseit az esetlegesen kártékony helyekről, így a felhasználók továbbra is elérhetik a webhelyet. Ha ez a szabályzat engedélyezve van (az *Igen*értékre van állítva), a Microsoft Edge megakadályozza, hogy a felhasználók megkerüljék a figyelmeztetéseket, és blokkolja azokat a helyről.  

  **Alapértelmezett**: Igen

- **Nem ellenőrzött fájlok letöltésének tiltása**  
  [Böngésző/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) – alapértelmezés szerint a Microsoft Edge lehetővé teszi, hogy a felhasználók megkerüljék (figyelmen kívül hagyják) a Windows Defender SmartScreen figyelmeztetéseit az esetlegesen kártékony fájlokról, így továbbra is letöltheti a nem ellenőrzött fájlokat. Ha ez a szabályzat engedélyezve van (az *Igen*értékre van állítva), a felhasználók nem hagyhatják figyelmen kívül a figyelmeztetéseket, és nem tölthetik le a nem ellenőrzött fájlokat.  

  **Alapértelmezett**: Igen

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>Windows Defender Anti-Virus [beállítások áttekintése a szakaszra függőben]

További információ: [Policy CSP-Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) a Windows dokumentációjában.

- **A Microsoft webböngészőkben betöltött parancsfájlok vizsgálata**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – állítsa *Igen* értékre a Windows Defender parancsfájl-ellenőrzési funkciójának engedélyezéséhez.  

  **Alapértelmezett**: Igen

- **Bejövő üzenetek ellenőrzése**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – állítsa *Igen* értékre, ha engedélyezni szeretné a Windows Defender számára az e-mailek vizsgálatát.  

  **Alapértelmezett**: Igen

- **Defender-minta küldésének beleegyező típusa**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) – a Windows Defender felhasználói beleegyezési szintjét ellenőrzi az adatküldés során. Ha a szükséges engedély már meg lett adva, a Windows Defender elküldi azokat. Ha nem (és ha a felhasználónak soha nem kell megadnia a kérést), a felhasználói felület megadását kéri (ha a *felhőbe szállított védelem* az *Igen*értékre van állítva) az adatok elküldése előtt.  

  **Alapértelmezett**: Biztonságos minták automatikus küldése

- **Hálózatvizsgáló rendszer (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) – blokkolja a HÁLÓZATVIZSGÁLÓ rendszer (NIS) aláírásával észlelt kártékony forgalmat.  
 
  **Alapértelmezett**: Igen

- **Aláírás-frissítési időköz (óra)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – Itt adhatja meg órákban, hogy az eszköz milyen gyakran keressen új Defender-aláírási frissítéseket.  
 
  **Alapértelmezett**: 4

- **Alacsony CPU-prioritás konfigurálása az ütemezett vizsgálatoknál**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – ha az *Igen*értékre van állítva, a vizsgálatok CPU-prioritása alacsony értékre van állítva. Ha *nincs konfigurálva*, az ütemezett vizsgálatok esetében nem történik változás a CPU-prioritásban.  

    **Alapértelmezett**: Igen

- **Defender-letiltás hozzáférés-védelemhez**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – ha az *Igen*értékre van állítva, a Windows Defender on hozzáférés-védelem engedélyezve van.  

  **Alapértelmezett**: Igen

- **A végrehajtandó rendszervizsgálat típusa**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) – Defender-vizsgálat típusa  

  **Alapértelmezett**: Gyors vizsgálat

- **Minden letöltés ellenőrzése**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) – ha az *Igen*értékre van állítva, a Defender a letöltött fájlokat és mellékleteket vizsgálja.  

  **Alapértelmezett**: Igen

- **Karanténba helyezett kártevők törlése előtti napok**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) – azt határozza meg, hogy a rendszer hány napig tart a karanténba helyezési elemek automatikus törlése előtt. Ha nulla értékre van állítva, a karanténba helyezett elemek soha nem törlődnek automatikusan.  

  **Alapértelmezett**: 0

- **Ütemezett vizsgálat kezdési ideje**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – a Defender által az eszközök vizsgálatára szolgáló napszakot ütemezhet. 
  
  Kapcsolódó beállítás a listában: *Defender/ScheduleScanDay*   

  **Alapértelmezett**: 2

- **Felhőbe szállított védelem**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – ha az *Igen*értékre van állítva, a Windows Defender adatokat küld a Microsoftnak az általa talált problémákról. A Microsoft elemezni fogja ezeket az információkat, többet tudhat meg az Ön és más ügyfelek problémáit érintő problémákról, és továbbfejlesztett megoldásokat kínál.

  Ha ezt a házirendet az *Igen*értékre állítja, akkor a *Defender-minta küldésének beleegyező típusával* adhatja meg, hogy a felhasználók vezérelhetik-e az eszközről küldött adatokat.  

  **Alapértelmezett**: Igen

- **A Defender vélhetően nemkívánatos alkalmazásának művelete**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – a Windows Defender víruskereső képes azonosítani és letiltani a *vélhetően nemkívánatos alkalmazások* (PUAs) letöltését és telepítését a hálózatban lévő végpontokon. 
 
  - Ha a *blokk*értékre van állítva, a Windows Defender blokkolja a PUAs, és felsorolja azokat az előzményekben más fenyegetésekkel együtt.
  - Ha naplózásravan beállítva, a Windows Defender észleli a PUAs, de nem blokkolja őket. A Windows Defender alkalmazással kapcsolatos információk megtalálhatók a Windows Defender által a Eseménynaplóban létrehozott események keresésekor.  
  - Ha az *eszköz alapértelmezett*értékre van állítva, a Pua-védelem ki van kapcsolva.  
 
  **Alapértelmezett**: Letiltás

- **A Defender Cloud Extended időtúllépése**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) – Itt adhatja meg azt a maximális időtartamot, ameddig a Windows Defender víruskeresőnek le kell tiltania egy fájlt a felhőből érkező eredményre való várakozás közben. A Windows Defender-várakozások alapszintű mérete 10 másodperc. Az itt megadott további időt (legfeljebb 50 másodperc) adja hozzá a 10 másodperchez. A legtöbb esetben a vizsgálat a maximálisnál kevesebb időt vesz igénybe. Az idő növelésével azonban elegendő időt biztosíthat ahhoz, hogy a felhő alaposan megvizsgálja a gyanús fájlokat.  

  Alapértelmezés szerint a kibontott idő értéke 0 (letiltva). Az Intune javasolja, hogy engedélyezze ezt a beállítást, és legalább 20 másodpercet határozzon meg.  
 
  **Alapértelmezett**: 0

- **Archív fájlok ellenőrzése**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – állítsa *Igen* értékre, hogy a Windows Defender megvizsgálja az archív fájlokat.  

  **Alapértelmezett**: Igen

- **Defender rendszervizsgálati ütemterve**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) – az a nap, amikor a Defender megvizsgálja az eszközöket. 
 
  Kapcsolódó beállítás a listában: *Defender/ScheduleScanTime*

  **Alapértelmezett**: Felhasználó által definiált

- **Viselkedés figyelése**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – állítsa *Igen* értékre a Windows Defender viselkedés-figyelési funkciójának bekapcsolásához. A Windows 10 rendszerbe ágyazott Windows Defender viselkedés-figyelési érzékelők összegyűjtik és feldolgozzák az operációs rendszer viselkedési jeleit, és elküldik az érzékelő adatait a Microsoft Defender ATP privát, elkülönített, Felhőbeli példányának.  

  **Alapértelmezett**: Igen

- **Hálózati mappákból megnyitott fájlok vizsgálata**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – állítsa *Igen* értékre, hogy a Windows Defender beolvassa a fájlokat a hálózaton. A felhasználó nem tudja eltávolítani az észlelt kártevőket a csak olvasható fájlokból.  

  **Alapértelmezett**: Igen

- **Defender Cloud Block-szint**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – ezzel a házirenddel határozható meg, hogy az agresszív Windows Defender víruskereső Hogyan blokkolja és vizsgálja a gyanús fájlokat. A lehetőségek a következők:

  - Agresszíven blokkolt ismeretlen fájlok az ügyfél teljesítményének optimalizálása közben (a hamis pozitívok nagyobb eséllyel)
  - Nagy plusz – agresszíven blokkolhatja az ismeretlen fájlokat, és további védelmi intézkedéseket alkalmazhat (az ügyfél teljesítményére is hatással lehet)
  - Zéró tolerancia – az összes ismeretlen végrehajtható fájl letiltása

  **Alapértelmezett**: Nincs konfigurálva

- **Valós idejű figyelés**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – állítsa *Igen* értékre a Windows Defender valós idejű figyelésének engedélyezéséhez.  

  **Alapértelmezett**: Igen

- **CPU-használati korlát a vizsgálat során**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – Itt adhatja meg a Windows Defender által a vizsgálat során használható maximális átlagos CPU-használatot.  

  **Alapértelmezett**: 50

- **Csatlakoztatott hálózati meghajtók vizsgálata teljes vizsgálat során**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) – állítsa *Igen* értékre, hogy a Windows Defender beolvassa a fájlokat a hálózaton. A felhasználó nem távolíthatja el az észlelt kártevő szoftvereket a csak olvasható fájlokból,

  Kapcsolódó beállítás a listában: *Defender/AllowScanningNetworkFiles*

  **Alapértelmezett**: Igen

- **A Defender végfelhasználói hozzáférésének tiltása**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – állítsa *Igen* értékre, hogy letiltsa a végfelhasználók számára a Windows Defender felhasználói felületének elérését az eszközön.  

  **Alapértelmezett**: Igen

- **Gyors vizsgálat kezdési ideje**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) – a Defender egy rövid időpontját ütemezze a gyors vizsgálat futtatásához.  

  **Alapértelmezett**: 2

## <a name="windows-defender-firewall"></a>Windows Defender-tűzfal
További információ: [TŰZFAL CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) a Windows dokumentációjában.

- **Biztonsági társítás tétlenségi ideje a törlés** - előtt*MdmStore/globális/SaIdleTime*   
  A biztonsági társítások akkor törlődnek, ha a hálózati forgalom nem látható az adott számú másodpercnél.  
  **Alapértelmezett**: 300

- FileTransferProtocol - *MdmStore/Global/DisableStatefulFtp*   
  Állapot-nyilvántartó File Transfer Protocol (FTP) blokkolása.  
  **Alapértelmezett**: Igen

- **Packet queuing** - *MdmStore/Global/EnablePacketQueue*    
  Itt adhatja meg, hogy a fogadási oldalon lévő szoftver skálázása engedélyezve legyen-e az IPsec Tunnel Gateway-forgatókönyvhöz továbbított titkosított fogadás és tiszta szöveg esetében. Ez biztosítja, hogy a rendszer megőrzi a csomagok sorrendjét.  
  **Alapértelmezett**: Eszköz alapértelmezése

- **Tűzfal-profil tartomány** - *FirewallRules/FirewallRuleName/profilok*  
  Meghatározza azokat a profilokat, amelyekre a szabály tartozik: Tartomány, magán, nyilvános. Ez az érték a tartományokhoz csatlakozó hálózatok profilját jelöli.  

  Elérhető beállítások:  
  - **Egyedi küldéses válaszok küldése csoportos küldésű szórásra**  
    **Alapértelmezett**: Igen

  - **A csoportházirend által beolvadt, jóváhagyott alkalmazási szabályok**  
    **Alapértelmezett**: Igen

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: Igen

  - **Globális portszabályok a csoportházirendből egyesítve**  
    **Alapértelmezett**: Igen

  - **Rejtett mód blokkolva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezett**: Engedélyezett

  - **Nincs egyesítve a csoportházirendből származó kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen

  - **A csoportházirend házirend-szabályai nem lettek egyesítve**  
    **Alapértelmezett**: Igen

- **Tűzfal-profil nyilvános** - *FirewallRules/FirewallRuleName/profilok*  
  Meghatározza azokat a profilokat, amelyekre a szabály tartozik: Tartomány, magán, nyilvános. Ez az érték a nyilvános hálózatok profilját jelöli. Ezek a hálózatok a kiszolgáló gazdagépének rendszergazdái. A besorolás akkor történik meg, amikor a gazdagép először csatlakozik a hálózathoz. Ezek a hálózatok általában olyan repülőtereken, kávézókban és más nyilvános helyeken találhatók, ahol a hálózat vagy a hálózat rendszergazdája nem megbízható.  

  Elérhető beállítások:

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: Igen 

  - **Egyedi küldéses válaszok küldése csoportos küldésű szórásra**  
    **Alapértelmezett**: Igen  

  - **Rejtett mód szükséges**  
    **Alapértelmezett**: Igen 
 
  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: Igen  

  - **A csoportházirend által beolvadt, jóváhagyott alkalmazási szabályok**  
    **Alapértelmezett**: Igen  

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: Igen  

  - **Globális portszabályok a csoportházirendből egyesítve**  
    **Alapértelmezett**: Igen

  - **Rejtett mód blokkolva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve**  
    **Alapértelmezett**: Engedélyezett  

  - **Nincs egyesítve a csoportházirendből származó kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen  

  - **Bejövő forgalom szükséges**  
    **Alapértelmezett**: Igen

  - **A csoportházirend házirend-szabályai nem lettek egyesítve**  
    **Alapértelmezett**: Igen  

- **Tűzfal profil privát** - *FirewallRules/FirewallRuleName/profilok*  
  Meghatározza azokat a profilokat, amelyekre a szabály tartozik: Tartomány, magán, nyilvános. Ez az érték a magánhálózatok profilját jelöli.  

  Elérhető beállítások: 

  - **Bejövő kapcsolatok blokkolva**  
    **Alapértelmezett**: Igen

  - **Egyedi küldéses válaszok küldése csoportos küldésű szórásra**  
    **Alapértelmezett**: Igen

  - **Rejtett mód szükséges**  
    **Alapértelmezett**: Igen

  - **Kimenő kapcsolatok szükségesek**  
    **Alapértelmezett**: Igen

  - **Bejövő értesítések blokkolva**  
    **Alapértelmezett**: Igen

  - **Globális portszabályok a csoportházirendből egyesítve**  
    **Alapértelmezett**: Igen

  - **Rejtett mód blokkolva**  
    **Alapértelmezett**: Igen  

  - **Tűzfal engedélyezve**  
    **Alapértelmezett**: Engedélyezett

  - **A csoportházirendben nem egyesítve lettek a jóváhagyott szabályok**  
    **Alapértelmezett**: Igen

  - **Nincs egyesítve a csoportházirendből származó kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen

  - **Bejövő forgalom szükséges**  
    **Alapértelmezett**: Igen

  - **A csoportházirend házirend-szabályai nem lettek egyesítve**  
    **Alapértelmezett**: Igen  

- **Tűzfallal előre megosztott kulcs kódolási módszere**  
  **Alapértelmezett**: UTF8

- **Visszavont tanúsítványok listájának ellenőrzése**  
  **Alapértelmezett**: Eszköz alapértelmezése

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello  

További információ: [PASSPORTFORWORK CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) a Windows dokumentációjában.

- **Vállalati Windows Hello** *TenantId/házirendek/UsePassportForWork konfigurálása*  -     
  A vállalati Windows Hello egy alternatív módszer a Windowsba való bejelentkezéshez jelszavak, intelligens kártyák és virtuális intelligens kártyák helyett.  

  - Ha az *Igen*értékre van állítva, akkor engedélyezi ezt a házirendet, és az eszköz kiépíti a vállalati Windows Hello-t.  
  - Ha a *nincs konfigurálva*értékre van állítva, az alapterv nem befolyásolja az eszköz házirend-beállítását. Ez azt jelenti, hogy ha a vállalati Windows Hello le van tiltva egy eszközön, az továbbra is le lesz tiltva. Ha engedélyezve van, az továbbra is engedélyezett marad. 

  A vállalati Windows Hello nem tiltható le ezen alapterven keresztül. A Windows Hello for Business letiltható a [Windows-regisztráció](windows-hello.md)konfigurálásakor, vagy az [Identity Protection](identity-protection-configure.md)eszköz konfigurációs profiljának részeként.  

A vállalati Windows Hello egy alternatív módszer a Windowsba való bejelentkezéshez jelszavak, intelligens kártyák és virtuális intelligens kártyák helyett.  

  Ha engedélyezi vagy nem konfigurálja ezt a házirend-beállítást, az eszköz kiépíti a vállalati Windows Hello-t. Ha letiltja ezt a házirend-beállítást, az eszköz semmilyen felhasználó számára nem helyezi üzembe a vállalati Windows Hello-t.

  Az Intune nem támogatja a Windows Hello letiltását. Ehelyett beállíthatja, hogy a Windows Hello for Business (igen), vagy nem konfigurálja a Windows Hello (nincs konfigurálva) beállítást. Ha nincs konfigurálva, egy eszköz más házirenddel is fogadhat konfigurációt, ami engedélyezheti vagy letilthatja a funkciót.  

  **Alapértelmezett**: Igen  

- **Kisbetűk megkövetelése a PIN** - -*TenantId/-házirendekben/PINComplexity/LowercaseLetters*  
  **Alapértelmezett**: Engedélyezett  

- **Speciális karakterek megkövetelése a PIN** - -*TenantId/házirendek/PINComplexity/SpecialCharacters*  
  **Alapértelmezett**: Engedélyezett  

- **Nagybetűk megkövetelése a PIN** - -*TenantId/-házirendekben/PINComplexity/UppercaseLetters*   
  **Alapértelmezett**: Engedélyezett  

