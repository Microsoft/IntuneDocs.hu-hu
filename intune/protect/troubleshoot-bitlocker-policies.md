---
title: Hibaelhárítási tippek a BitLocker-szabályzatokhoz Microsoft Intune
titleSuffix: Microsoft Intune
description: Ismerteti, hogyan lehet engedélyezni a BitLocker-titkosítást az eszközön az Intune-szabályzattal, és hogy miként ellenőrizhető, hogy a szabályzat sikeresen telepítve van-e az eszközre.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 197ad888dc8a07cc35efbaec538fde93c76c81c3
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817552"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>A Microsoft Intune BitLocker-házirendjeinek hibáinak megoldása

Ez a cikk segítséget nyújt az Intune-rendszergazdáknak arról, hogy a Windows 10-es eszközök hogyan konfigurálhatják a BitLockert az Intune-szabályzat alapján. Ez a cikk útmutatást nyújt az Intune-nal felügyelt eszközök BitLocker-beállításaival kapcsolatos hibák elhárításához.  

## <a name="understanding-bitlocker"></a>A BitLocker ismertetése

A BitLocker meghajtótitkosítás a Microsoft Windows operációs rendszerek által kínált szolgáltatás, amely lehetővé teszi, hogy a felhasználók titkosítsák az adataikat a merevlemezeken. A BitLocker támogatja az operációsrendszer-meghajtók, a cserélhető adathordozó-meghajtók és a rögzített adatmeghajtók titkosítását. A BitLocker az 256 bites titkosítás használatát is támogatja a bizalmas adatok jobb védelme érdekében.  

A Microsoft Intune a következő módszerekkel kezelheti a BitLockert Windows 10-es eszközökön:

- **Eszköz-konfigurációs házirendek** – a beépített házirend-beállítások az Intune felügyeleti konzolon érhetők el az **eszköz konfigurációja**@no__t – 2**Endpoint Protection** > **Windows titkosítási házirend**. A rendelkezésre álló kapcsolók és szolgáltatások itt találhatók: [Windows-titkosítás](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- A **biztonsági**alapkonfigurációk  - [biztonsági alaptervek](security-baselines.md) a beállítások és a megfelelő biztonsági csapat által a Windows-eszközök biztonságossá tételéhez javasolt alapértelmezett értékek. A különböző alapforrások, például a *Mdm biztonsági* alapkonfiguráció vagy a *Microsoft Defender ATP* alapkonfigurációja ugyanazokat a beállításokat és különböző beállításokat is képes kezelni, mint az egymástól. Emellett ugyanúgy kezelhetik az eszköz konfigurációs házirendjeivel felügyelt beállításokat is. 

Az Intune-on kívül lehetséges, hogy a BitLocker beállításait más módon, például a Csoportházirend felügyeli, vagy manuálisan állítja be az eszköz felhasználója.

Függetlenül attól, hogy a beállítások hogyan lesznek alkalmazva egy eszközre, a BitLocker-házirendek a [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) -t használják a titkosítás konfigurálásához az eszközön. A BitLocker CSP be van építve a Windowsba, és amikor az Intune egy BitLocker-házirendet telepít egy hozzárendelt eszközre, az eszközön található BitLocker CSP a megfelelő értékeket írja a Windows beállításjegyzékbe, hogy a házirend beállításai érvénybe lépnek.

Ha többet szeretne megtudni a BitLockerről, tekintse meg az alábbi forrásokat.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [A BitLocker áttekintése és követelményei – gyakori kérdések](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Most, hogy megértette, hogy a szabályzatok mit tesznek, és hogyan működnek, tekintse meg, hogyan ellenőrizheti, hogy a BitLocker-beállítások sikeresen érvényesek-e a Windows-ügyfélre.

## <a name="verify-the-source-of-bitlocker-settings"></a>A BitLocker-beállítások forrásának ellenőrzése

Ha egy Windows 10-es eszközön BitLocker-problémát vizsgál ki, fontos, hogy először meg kell határozni, hogy a probléma Intune-nal kapcsolatos vagy Windows-kapcsolatban van-e. A hiba valószínű forrásainak ismerete után a megfelelő helyre koncentrálhatja a hibaelhárítási erőfeszítéseket, és szükség esetén a megfelelő csapattól kaphat támogatást.  

Első lépésként állapítsa meg, hogy az Intune-szabályzat sikeresen telepítve van-e a céleszköz. A következő példában egy eszköz-konfigurációs szabályzatot telepít, amely telepíti a Windows-titkosítás (BitLocker) beállításait, ahogy az az alábbi ábrán látható: 

![A Windows titkosítási eszköz konfigurációs házirendje a beállításokkal](./media/troubleshooting-bitlocker-policies/settings.png)

Hogyan győződhet meg arról, hogy a beállítások a megadott eszközre lettek alkalmazva? Az alábbiakban néhány módon elvégezheti a műveletet.

### <a name="device-configuration-policy-device-status"></a>Eszköz-konfigurációs házirend eszközének állapota  

Ha eszköz-konfigurációs házirendet használ a BitLocker konfigurálásához, a szabályzat állapotát az Intune-portálon is megtekintheti. A portálon nyissa meg az **eszköz konfigurációja** > **profilok** > válassza ki a BitLocker-beállításokat tartalmazó profilt, majd válassza az **eszköz állapota**lehetőséget. A profilhoz rendelt eszközök listája látható, az Eszközállapot *oszlop pedig* azt jelzi, hogy az eszköz sikeresen telepítette-e a profilt. 

Ne feledje, hogy a BitLocker-házirendet fogadó eszköz között késés lehet, és a meghajtó teljes mértékben titkosítva van.  

 
### <a name="use-control-panel-on-the-client"></a>A Vezérlőpult használata az ügyfélen  

Egy olyan eszközön, amelyen engedélyezve van a BitLocker és a titkosított meghajtó, megtekintheti a BitLocker állapotát az eszközök Vezérlőpultján. Az eszközön nyissa meg a **vezérlőpult** > **rendszer és biztonsági** > **BitLocker meghajtótitkosítás**. A megerősítés a következő képen látható módon jelenik meg.  

![A BitLocker be van kapcsolva a Vezérlőpulton](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Parancssor használata  

Egy olyan eszközön, amelyen engedélyezve van a BitLocker és a titkosított meghajtó, indítsa el a parancssort rendszergazdai hitelesítő adatokkal, majd futtassa `manage-bde -status` parancsot. Az eredmények a következő példához hasonlóak:  
@no__t – a @ no__t-1 0A eredménye

A példában: 
- A **BitLocker-védelem** **be van kapcsolva**,  
- **Titkosított százalék** **100%**  
- A **titkosítási módszer** a **XTS-AES 256**.  

A következő parancs futtatásával is megtekintheti a **kulcs-védőket** :

```cmd
Manage-bde -protectors -get c:
```

Vagy a PowerShell-lel:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Az eszközök beállításjegyzék-kulcs konfigurációjának áttekintése   

Miután sikeresen telepítette a BitLocker-házirendet egy eszközre, tekintse meg a következő beállításkulcsot az eszközön, amelyen áttekintheti a BitLocker-beállítások konfigurációját:  *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. Például:

![BitLocker-beállításkulcs](./media/troubleshooting-bitlocker-policies/registry.png)

Ezeket az értékeket a BitLocker CSP konfigurálja. Ellenőrizze, hogy a kulcsok értékei megegyeznek-e az Intune Windows titkosítási szabályzatának forrásában megadott beállításokkal. Az egyes beállításokkal kapcsolatos további információkért lásd: [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> A Windows Eseménynapló a BitLocker szolgáltatással kapcsolatos különféle adatokat is tartalmazni fog. Túl sok a lista, de a **BITLOCKER API** keresése sok hasznos információt biztosít Önnek.

### <a name="check-the-mdm-diagnostics-report"></a>A MDM diagnosztikai jelentésének megtekintése  

A BitLockert engedélyező eszközön létrehozhat és megtekinthet egy MDM diagnosztikai jelentést a célként megadott eszközről annak ellenőrzéséhez, hogy a BitLocker-házirend megtalálható-e. Ha a jelentésben a házirend-beállítások láthatók, akkor azt is jelzi, hogy a házirend sikeresen telepítve lett. A *Microsoft* a következő hivatkozásra kattintva bemutatja, hogyan RÖGZÍTHET egy Mdm diagnosztikai jelentést egy Windows-eszközről. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

A MDM diagnosztikai jelentés elemzésekor a tartalom egy kicsit zavaró lehet. Az alábbi példa bemutatja, hogyan lehet korrelálni a jelentésben szereplő beállításokkal a szabályzatban:

![MDM diagnosztikai jelentés – példa](./media/troubleshooting-bitlocker-policies/report.png)

A kimeneti eredmény a BitLocker-házirend értékeinek megfelelő értékeket jeleníti meg:

![A kimeneti eredmény az értékeket jeleníti meg ](./media/troubleshooting-bitlocker-policies/output.png)

MDM diagnosztika kimeneti eredményei:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

A [BITLOCKER CSP dokumentációjában](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) megtekintheti, hogy az egyes értékek mit jelentenek. Ebben a példában egy kódrészletet osztanak meg az alábbi képen.

![Értékek célja](./media/troubleshooting-bitlocker-policies/shared-example.png)

 Hasonlóképpen megtekintheti az összes értéket, és ellenőrizheti azokat a BitLocker CSP-hivatkozásán keresztül.

> [!TIP]
> A MDM diagnosztikai jelentés elsődleges célja, hogy segítséget nyújtson Microsoft ügyfélszolgálata a hibák elhárításához. Ha megnyitja az Intune támogatási esetét, és a probléma a Windows-ügyfeleket is magában foglalja, mindig érdemes összegyűjteni ezt a jelentést, és belefoglalni a támogatási kérelembe.

## <a name="troubleshooting-bitlocker-policy"></a>BitLocker-házirend hibaelhárítása

Most érdemes meggyőződnie arról, hogy miként ellenőrizheti, hogy az Intune sikeresen telepítette-e a BitLocker-szabályzatot, amely a BitLocker konfigurációját a WIndows rendszeren lévő BitLocker CSP-re helyezi át.  

**A házirend nem éri el az eszközt** – ha az Intune-szabályzata nem áll rendelkezésre semmilyen kapacitásban:  
- **Megfelelően van-e regisztrálva az eszköz a Microsoft Intuneba?** Ha nem, akkor a szabályzattal kapcsolatos hibák elhárítása előtt kell foglalkoznia. [Itt](../enrollment/troubleshoot-windows-enrollment-errors.md)találhat segítséget a Windows-regisztrációval kapcsolatos problémák elhárításában.  
- **Aktív hálózati kapcsolatok vannak az eszközön?** Ha az eszköz repülőgép üzemmódban van, vagy ki van kapcsolva, vagy ha a felhasználó nem rendelkezik szolgáltatással, akkor a rendszer nem küldi el és nem alkalmazza a házirendet, amíg vissza nem állítja a hálózati kapcsolatot.  
- **A BitLocker-házirend megfelelően települt a megfelelő felhasználóra vagy eszköz csoportra?** Győződjön meg arról, hogy a megfelelő felhasználó vagy eszköz tagja a célként kijelölt csoportoknak.  

A **házirend jelen van, de nem minden beállítás sikeresen konfigurálva** – ha az Intune-szabályzat eléri az eszközt, de nem minden konfiguráció van beállítva:  
- **A teljes házirend központi telepítése meghiúsul, vagy csak bizonyos, nem alkalmazandó beállítások?** Ha úgy találja, hogy egy olyan szituációval szembesül, amelyben csak néhány házirend-beállítás nem érvényes, tekintse meg a következő szempontokat:

  1. Az összes **Windows-verzió nem támogatja a BitLocker összes beállítását**.  
  A házirend egyetlen egységként jut egy eszközhöz, így ha egyes beállítások érvényesek, mások pedig nem, biztos lehet benne, hogy magától a házirendtől érkezik. Ebben az esetben lehetséges, hogy az eszközön futó Windows-verzió nem támogatja a problémás beállításokat. Az egyes beállítások verziószámával kapcsolatos részletekért tekintse meg a Windows dokumentációjában a [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) című témakört.  

  1. **A BitLocker nem támogatott az összes hardveren**.  
  Még ha a Windows megfelelő verziója is van, előfordulhat, hogy az alapul szolgáló eszköz hardvere nem felel meg a BitLocker-titkosítás követelményeinek. A [BitLocker rendszerkövetelményei (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) a Windows dokumentációjában, de a legfontosabb, hogy az eszköz kompatibilis TPM-lapka (1,2 vagy újabb) és egy Trusted Computing Group (TCG) szabványnak megfelelő BIOS vagy UEFI belső vezérlőprogram legyen.

**Példa a vizsgálatra** – a BitLocker-házirendet egy Windows 10-es eszközön helyezheti üzembe, és az **eszközök titkosítása** beállítás a portálon **észlelt hiba** állapotát jeleníti meg.

- Ahogy a neve is sugallja, ez a beállítás lehetővé teszi, hogy a rendszergazda a *BitLocker > eszköz titkosításával*bekapcsolja a titkosítást. A korábban említett hibaelhárítási tippeket követve először tekintse meg a MDM diagnosztikai jelentését. A jelentés megerősíti, hogy a megfelelő házirend telepítve lett az eszközön:

  ![A jelentés megerősíti, hogy az eszközön telepítve van-e a megfelelő házirend](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Azt is ellenőrizze, hogy sikeres volt-e a beállításjegyzékben:

  ![A RequiredDeviceEncryption beállításazonosító 1 értéket jelenít meg](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Ezután ellenőrizze a TPM állapotát a PowerShell használatával, és keresse meg, hogy a TPM nem érhető el az eszközön:

  ![TPM-állapot ellenőrzése a PowerShell használatával](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Mivel a BitLocker a TPM-re támaszkodik, azt is megállapíthatja, hogy a BitLocker nem működik az Intune-nal vagy a házirenddel kapcsolatos probléma miatt, hanem azért, mert maga az eszköz nem rendelkezik TPM-lapka vagy TPM-mel a BIOS-ban.

  További tippként megerősítheti ugyanezt a Windows Eseménynapló **alkalmazások és szolgáltatások naplójában** > **Windows** > **BitLocker API**. A **BITLOCKER API** -eseménynaplóban talál egy 853-es azonosítójú eseményt, amely azt jelenti, hogy a TPM nem érhető el:

  ![853-es AZONOSÍTÓJÚ esemény](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > A TPM állapotát a **TPM. msc** parancs futtatásával is megtekintheti az eszközön.



## <a name="summary"></a>Összegzés

Ha elhárítja az Intune-nal kapcsolatos BitLocker-házirendekkel kapcsolatos problémákat, és ellenőrizheti, hogy a házirend eléri-e a kívánt eszközt, nyugodtan feltételezheti, hogy a probléma nem kapcsolódik közvetlenül az Intune-hoz. A probléma valószínűleg a Windows operációs rendszer vagy a hardver problémája. Ebben az esetben kezdjen más területeken, például a TPM-konfigurációval vagy az UEFI-vel és a biztonságos rendszerindítással.

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>További lépések  

A következőkben további erőforrások érhetők el, amelyek segíthetnek a BitLocker használatakor:

- [BitLocker termékdokumentáció](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [A BitLocker rendszerkövetelményei](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker – gyakori kérdések](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP – dokumentáció](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows titkosítási szabályzat beállításai](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Hardveres független automatikus BitLocker-titkosítás a HRE/MDM használatával](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [CSP-szabályzat a BitLocker-titkosításhoz az Auto-Pilot eszközökön](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [A BitLocker-szabályzatok Intune-nal való létrehozásának és üzembe helyezésének útmutatója](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)