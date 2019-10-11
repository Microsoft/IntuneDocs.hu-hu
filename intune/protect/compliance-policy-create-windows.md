---
title: Windows 10-es megfelelőségi beállítások az Microsoft Intune-ban – Azure | Microsoft Docs
description: Tekintse meg az összes olyan beállítást, amelyet a Windows 10, Windows holografikus és Surface Hub eszközök megfelelőségének beállításakor használhat a Microsoft Intune. Győződjön meg a minimális és maximális operációs rendszer megfelelőségéről, a jelszó korlátozásának és hosszának beállításáról, a partner víruskereső (AV) megoldások megadásáról, az adattárolási titkosítás engedélyezéséről és egyebekről.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 493db6299aa8242d0ca6ab669b313e85d0dc14c6
ms.sourcegitcommit: b1e97211db7cb949eb39be6776b3a11d434fdab0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251583"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 10 és újabb beállítások az eszközök megfelelőségi vagy nem megfelelőként való megjelöléséhez az Intune használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és ismerteti a Windows 10-es és újabb rendszerű eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használja a BitLocker megköveteléséhez, a minimális és maximális operációs rendszer beállításához, a kockázati szint beállításához a Microsoft Defender komplex veszélyforrások elleni védelem (ATP) használatával, és így tovább.

A szolgáltatás a következőkre vonatkozik:

- Windows 10 és újabb verziók
- Windows holografikus vállalatoknak
- Surface Hub

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előzetes teendők

[Hozzon létre egy megfelelőségi szabályzatot](create-compliance-policy.md#create-the-policy). A **platform**területen válassza a **Windows 10 és újabb**lehetőséget.

## <a name="device-health"></a>Eszközállapot

- **BitLocker megkövetelése**: Ha a beállítás **kötelező**, az eszköz a rendszer kikapcsolásakor vagy a hibernált állapotában a meghajtón tárolt adatok védelme érdekében a jogosulatlan hozzáférés ellen biztosíthatja a meghajtót. A Windows BitLocker meghajtótitkosítás titkosítja a Windows operációs rendszer kötetén tárolt összes adatmennyiséget. A BitLocker a TPM használatával segíti a Windows operációs rendszer és a felhasználói adatainak védelmében. Azt is segít megerősíteni, hogy a számítógép nincs-e illetéktelenül megoldva, még akkor is, ha annak felügyelet nélküli, elveszett vagy ellopták. Ha a számítógép kompatibilis TPM-mel rendelkezik, a BitLocker a TPM használatával zárolja az adatvédelmet biztosító titkosítási kulcsokat. Ennek eredményeképpen a kulcsok nem érhetők el, amíg a TPM nem ellenőrzi a számítógép állapotát.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

- A **biztonságos rendszerindítás engedélyezésének megkövetelése az eszközön**: Ha a beállítás a **szükséges**értékre van állítva, a rendszer kényszerítve van a gyári megbízható állapotba való rendszerindításra. Ha ez a beállítás engedélyezve van, a gép rendszerindításához használt alapvető összetevőknek megfelelő titkosítási aláírásokkal kell rendelkezniük, amelyeket az eszközt gyártó szervezet megbízhatónak tekint. Az UEFI belső vezérlőprogram ellenőrzi az aláírást, mielőtt lehetővé tenné a gép indítását. Ha bármely fájl illetéktelenül van módosítva, amely megszakítja az aláírását, a rendszer nem indul el.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

  > [!NOTE]
  > A **biztonságos rendszerindítás engedélyezésének megkövetelése az eszköz** beállításában bizonyos TPM 1,2-és 2,0-eszközökön támogatott. Azon eszközök esetében, amelyek nem támogatják a TPM 2,0-es vagy újabb verzióját, az Intune-beli házirend állapota **nem megfelelőként**jelenik meg. További információ a támogatott verziókról: [Eszközállapot-igazolás](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Kód megkövetelése integritás**: a kód integritása egy olyan szolgáltatás, amely a memóriába betöltött minden egyes alkalommal ellenőrzi az illesztőprogram vagy a rendszerfájl integritását. Ha a **kötelező**beállításra van beállítva, a kód integritása észleli, ha aláíratlan illesztőprogramot vagy rendszerfájlt tölt be a kernelbe. Azt is észleli, ha egy rendszerfájlt egy olyan kártevő szoftver módosít, amely rendszergazdai jogosultságokkal rendelkező felhasználói fiókkal fut.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

További források:

- Az [állapot igazolása CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) részletesen ismerteti a szolgáltatás működésének módját.
- [Támogatási Tipp: Eszközállapot-igazolás beállítások használata az Intune megfelelőségi szabályzatának részeként](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>Eszköztulajdonságok

- **Operációs rendszer minimális verziója**: adja meg a minimálisan megengedett verziót a **Major.Minor.Build.cu** . A megfelelő érték beszerzéséhez nyisson meg egy parancssort, és írja be a következőt: `ver`. A `ver` parancs a következő formátumban adja vissza a verziót:

  `Microsoft Windows [Version 10.0.17134.1]`

  Ha egy eszközön a megadott operációsrendszer-verziónál korábbi verzió szerepel, nem megfelelőként fog megjelenni. Megjelenik egy hivatkozás, amelyen a frissítésre vonatkozó információk láthatók. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. A frissítés után hozzáférhetnek a vállalati erőforrásokhoz.

- **Maximális operációsrendszer-verzió**: adja meg a maximálisan engedélyezett verziót, a főverzió. **alverzió. Build. változat számformátum** . A megfelelő érték beszerzéséhez nyisson meg egy parancssort, és írja be a következőt: `ver`. A `ver` parancs a következő formátumban adja vissza a verziót:

  `Microsoft Windows [Version 10.0.17134.1]`

  Ha egy eszköz a megadott verziónál újabb operációsrendszer-verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg a szabály meg nem változtatja az operációs rendszer verzióját.

- A **mobileszközök minimálisan szükséges operációs rendszere**: adja meg a minimálisan engedélyezett verziót a főverzió. alverzió.

  Ha egy eszközön a megadott operációsrendszer-verzió korábbi verziója szerepel, nem megfelelőként fog megjelenni. Megjelenik egy hivatkozás, amelyen a frissítésre vonatkozó információk láthatók. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. A frissítés után hozzáférhetnek a vállalati erőforrásokhoz.

- A **mobileszközök számára maximálisan szükséges operációs rendszer**: adja meg a maximálisan engedélyezett verziót, a főverzió. alverziójának verziószámában.

  Ha egy eszköz a megadott verziónál újabb operációsrendszer-verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg a szabály meg nem változtatja az operációs rendszer verzióját.

- **Érvényes operációsrendszer-buildek**: adjon meg egy tartományt az elfogadható operációsrendszer-verziók számára, beleértve a minimális és a maximális értéket is. Ezen elfogadható operációsrendszer-összeállítási számok vesszővel tagolt (CSV) fájljának listáját is **exportálhatja** .

## <a name="configuration-manager-compliance"></a>Configuration Manager megfelelőség

Csak a Windows 10 és újabb rendszerű, közösen felügyelt eszközökre vonatkozik. A csak Intune-eszközök nem elérhető állapotot adnak vissza.

- **Eszköz megfelelőségének megkövetelése a System Center Configuration Managertól**: válassza a **kötelező** lehetőséget, ha a System Center Configuration Manager összes beállítását (konfigurációs elemeit) szeretné kényszeríteni. 

  Tegyük fel, hogy az összes szoftverfrissítést telepíteni kell az eszközökre. Configuration Managerban ez a követelmény a "telepített" állapottal rendelkezik. Ha az eszközön bármely program ismeretlen állapotban van, akkor az eszköz nem megfelelő az Intune-ban.
  
  Ha **nincs konfigurálva**, az Intune nem vizsgálja meg a megfelelőség Configuration Manager beállításait.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához** **: a felhasználóknak jelszót kell** megadniuk ahhoz, hogy hozzáférjenek az eszközhöz. Ha **nincs konfigurálva**, az Intune nem értékeli ki, hogy az eszköz megfelel-e a megfelelőségi jelszó beállításainak.
- **Egyszerű jelszavak**: a **Letiltás** beállítás megadása esetén a felhasználók nem hozhatnak létre egyszerű jelszavakat, például **1234** vagy **1111**. Ha úgy **van** beállítva, hogy a felhasználók olyan jelszavakat hozzanak létre, mint például a **1234** vagy a **1111**.
- **Jelszó típusa**: válassza ki, hogy milyen típusú jelszót vagy PIN-kódot kell megadnia. A lehetőségek:

  - **Eszköz alapértelmezése**: jelszó, numerikus PIN kód vagy alfanumerikus PIN kód megkövetelése
  - **Numerikus**: jelszó vagy numerikus PIN-kód megkövetelése
  - **Alfanumerikus**: jelszó vagy alfanumerikus PIN-kód megkövetelése. Válassza a **jelszó bonyolultságát**is: 
    
    - **Számjegyek és kisbetűk megkövetelése**
    - **Számjegyek, kisbetűk és nagybetűk megkövetelése**
    - **Számjegyek, kisbetűk, nagybetűk és speciális karakterek megkövetelése**

    > [!TIP]
    > Az alfanumerikus jelszavas házirendek összetettek lehetnek. Javasoljuk, hogy a rendszergazdák további információért olvassa el a kriptográfiai szolgáltatókat:
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Jelszó minimális hossza**: Itt adhatja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát.
- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát.
- **Jelszó érvényessége (napokban)** : adja meg, hogy hány nap elteltével járjon le a jelszó, és újat kell létrehoznia a 1-730-ból.
- Az **újrafelhasználást megakadályozó korábbi jelszavak száma**: megadhatja, hogy hány korábban használt jelszót ne lehessen használni.
- **Jelszó megkövetelése, ha az eszköz visszatér az inaktív állapotból (mobil és holografikus)** : kényszerítse a felhasználókat, hogy adja meg a jelszót minden alkalommal, amikor az eszköz visszatér inaktív állapotból.

  > [!IMPORTANT]
  > Ha a jelszóra vonatkozó követelményt egy Windows asztalon módosítják, a felhasználók a következő bejelentkezéskor jelentkeznek, ahogy az az eszköz tétlenről aktív állapotba kerül. A követelménynek megfelelő jelszóval rendelkező felhasználókat a rendszer továbbra is megkéri a jelszavuk módosítására.

### <a name="encryption"></a>Titkosítás

- **Adattároló titkosítása az eszközön**: válassza a **szükséges** lehetőséget az adattárolók titkosításához az eszközökön.

  > [!NOTE]
  > Az **eszközön lévő adattárolás titkosítása** általános időközönként ellenőrzi az eszközön a titkosítás jelenlétét. Robusztusabb titkosítási beállítások esetén érdemes lehet a **BitLocker megkövetelése**, amely a Windows Eszközállapot-igazolás segítségével ellenőrzi a BitLocker-állapotot a TPM szintjén.

### <a name="device-security"></a>Eszköz biztonsága

- **Tűzfal**: állítsa be a **kötelező** beállítást a Microsoft Defender-tűzfal bekapcsolásához, és a felhasználók kikapcsolásának megakadályozása. **Nincs konfigurálva** (alapértelmezés) nem szabályozza a Microsoft Defender-tűzfalat, és nem változtatja meg a meglévő beállításokat.

  [Tűzfal CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Ha az eszköz azonnal szinkronizál az újraindítás után, vagy azonnal szinkronizálja az alvó állapotból való felébresztést, akkor ez a beállítás **hibát**jelenthet. Előfordulhat, hogy ez a forgatókönyv nem érinti a teljes eszköz megfelelőségi állapotát. A megfelelőségi állapot újbóli kiértékeléséhez manuálisan [szinkronizálja az eszközt](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Platformmegbízhatósági modul (TPM)** : Ha a beállítás **kötelező**, az Intune ellenőrzi a verzió megfelelőségét. Az eszköz akkor megfelelő, ha a TPM-lapka verziója nagyobb nullánál (nulla). Az eszköz nem megfelelő, ha az eszközön nincs TPM-verzió. Ha **nincs konfigurálva**, az Intune nem vizsgálja meg a TPM-lapka verziójának eszközét.

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion csomópont](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Víruskereső**: Ha **kötelező**beállításra van beállítva, a [Windows Security Centerban](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)regisztrált víruskereső-megoldásokkal, például a Symantec és a Microsoft Defender alkalmazással is ellenőrizhetők a megfelelőség. Ha **nincs konfigurálva**, az Intune nem keres az eszközre telepített összes AV-megoldást.
- **Kémprogram-elhárító**: Ha **kötelező**beállításra van beállítva, a [Windows Security Centerban](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)regisztrált kémprogram-elhárító megoldásokkal, például a Symantec és a Microsoft Defender alkalmazással is megtekintheti a megfelelőséget. Ha **nincs konfigurálva**, az Intune nem keres az eszközre telepített kémprogram-elhárító megoldásokat.

### <a name="defender"></a>Védő

- **Microsoft Defender antimalware**: állítsa be **a beállítást** a Microsoft Defender kártevő-elhárító szolgáltatásának bekapcsolásához, és megakadályozza a felhasználók kikapcsolását. **Nincs konfigurálva** (az alapértelmezett) nem szabályozza a szolgáltatást, és nem változtatja meg a meglévő beállításokat.
- **Microsoft Defender antimalware minimális verziója**: adja meg a Microsoft Defender kártevő-elhárító szolgáltatásának minimálisan engedélyezett verzióját. Adja meg például a következőt: `4.11.0.0`. Ha üresen hagyja, a Microsoft Defender anti-malware szolgáltatás bármely verzióját használhatja.
- **Microsoft Defender antimalware biztonsági intelligencia naprakész**: szabályozza a Windows biztonsági vírus-és veszélyforrások elleni védelem frissítéseit az eszközökön. **Szükséges** kényszeríteni a Microsoft Defender biztonsági intelligencia naprakészen kell lennie. **Nincs konfigurálva** (az alapértelmezett) nem kényszeríti a követelményeket.

  A [Microsoft Defender Antivirus és más Microsoft antimalware biztonsági intelligenciával kapcsolatos frissítései több információt biztosítanak](https://www.microsoft.com/en-us/wdsi/defenderupdates) a biztonsági intelligenciáról.

- **Valós idejű védelem** **: a** valós idejű védelem bekapcsolása a kártevők, kémprogramok és más nemkívánatos szoftverek keresésével. **Nincs konfigurálva** (alapértelmezés) nem szabályozza ezt a funkciót, és nem változtatja meg a meglévő beállításokat.

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Windows Defender ATP

- A **számítógép kockázati pontszámának megkövetelése az eszközön**: ezzel a beállítással a megfelelőségi feltételként a kockázatkezelési szolgáltatásokból kiértékelheti a kockázatértékelést. A maximálisan engedélyezett veszélyforrások szintjének kiválasztása:

  - **Clear (Törlés**): Ez a lehetőség a legbiztonságosabb, mert az eszköz nem rendelkezhet fenyegetésekkel. Ha az eszköz bármilyen szintű fenyegetést észlel, azt a rendszer nem megfelelőként értékeli.
  - **Alacsony**: az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Minden magasabb érték nem megfelelő állapotba helyezi az eszközt.
  - **Közepes**: az eszköz abban az esetben minősül megfelelőnek, ha az eszközön fennálló fenyegetések alacsony vagy közepes szintűek. Ha az eszköz magas szintű fenyegetéseket észlel, azt a rendszer nem megfelelőként határozza meg.
  - **Magas**: Ez a beállítás a legkevésbé biztonságos, és lehetővé teszi az összes veszélyforrás szintjét. Hasznos lehet, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.
  
  A Microsoft Defender ATP (komplex veszélyforrások elleni védelem) a védelmi fenyegetés szolgáltatásként való beállításával kapcsolatban lásd: a [Microsoft DEFENDER ATP engedélyezése feltételes hozzáféréssel](advanced-threat-protection.md).

A módosítások mentéséhez kattintson **az OK** > **Létrehozás** gombra.

## <a name="windows-holographic-for-business"></a>Windows holografikus vállalatoknak

A Windows holografikus for Business a **Windows 10-es és újabb** platformot használja. A Windows holografikus for Business a következő beállítást támogatja:

- **Rendszerbiztonság**@no__t – 1**titkosítás**@no__t – az**adattároló titkosítása az eszközön**.

Az eszközök titkosításának ellenőrzéséhez a Microsoft HoloLens tekintse meg az [eszközök titkosításának ellenőrzése](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)című témakört.

## <a name="surface-hub"></a>Surface Hub

Surface Hub a **Windows 10-es és újabb** platformot használja. A felszíni hubok mind a megfelelőségi, mind a feltételes hozzáférés esetében támogatottak. A funkciók Surface hubokon való engedélyezéséhez javasoljuk, hogy [engedélyezze a Windows 10 automatikus regisztrációját](../enrollment/windows-enroll.md) az Intune-ban (Azure Active Directory (Azure ad)), és a Surface hub eszközöket az eszközökön. A Surface hub-nak az Azure AD-hez kell csatlakoznia ahhoz, hogy a megfelelőség és a feltételes hozzáférés működjön.

Lásd: a [Windows-eszközök regisztrálásának beállítása](../enrollment/windows-enroll.md) útmutatásként.

## <a name="next-steps"></a>Következő lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg a Windows 8,1 rendszerű eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-windows-8-1.md) .
