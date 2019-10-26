---
title: Windows 10-es megfelelőségi beállítások az Microsoft Intune-ban – Azure | Microsoft Docs
description: Tekintse meg az összes olyan beállítást, amelyet a Windows 10, Windows holografikus és Surface Hub eszközök megfelelőségének beállításakor használhat a Microsoft Intune. Győződjön meg a minimális és maximális operációs rendszer megfelelőségéről, a jelszó korlátozásának és hosszának beállításáról, a partner víruskereső (AV) megoldások megadásáról, az adattárolási titkosítás engedélyezéséről és egyebekről.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3c6c029a5c5864eda46a68832b2f9f655553846
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889543"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 10 és újabb beállítások az eszközök megfelelőségi vagy nem megfelelőként való megjelöléséhez az Intune használatával

Ez a cikk felsorolja és ismerteti a Windows 10-es és újabb rendszerű eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használja a BitLocker megköveteléséhez, a minimális és maximális operációs rendszer beállításához, a kockázati szint beállításához a Microsoft Defender komplex veszélyforrások elleni védelem (ATP) használatával, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- Windows 10 és újabb
- Windows Holographic for Business
- Surface Hub

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.

## <a name="device-health"></a>Eszközállapot

### <a name="windows-health-attestation-service-evaluation-rules"></a>A Windows Health igazolási szolgáltatás kiértékelési szabályai

- **BitLocker megkövetelése**:  
   A Windows BitLocker meghajtótitkosítás a Windows operációs rendszer kötetén tárolt összes adatot titkosítja. A BitLocker a platformmegbízhatósági modul (TPM) segítségével gondoskodik a Windows operációs rendszer és a felhasználói adatainak védelméről. Azt is segít megerősíteni, hogy a számítógép nincs-e illetéktelenül megoldva, még akkor is, ha annak felügyelet nélküli, elveszett vagy ellopták. Ha a számítógépen kompatibilis TPM található, a BitLocker a TPM-mel zárolja az adatokat védő titkosítási kulcsokat. Ennek eredményeképpen a kulcsok nem érhetők el, amíg a TPM nem ellenőrzi a számítógép állapotát.  

   - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
   - **Kötelező** – az eszköz a rendszer kikapcsolásakor vagy hibernálása esetén a meghajtón tárolt adatok védelme a jogosulatlan hozzáféréstől.  


- **A biztonságos rendszerindítás engedélyezésének megkövetelése az eszközön**:  
    - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
    - **Required (kötelező** ) – a rendszer kénytelen a gyári megbízható állapotba indítani. A gép rendszerindításához használt alapvető összetevőknek megfelelő titkosítási aláírásokkal kell rendelkezniük, amelyeket az eszközt gyártó szervezet megbízhatónak tekint. Az UEFI belső vezérlőprogram ellenőrzi az aláírást, mielőtt engedélyezi a számítógép elindítását. Ha bármely fájl illetéktelenül van módosítva, amely megszakítja az aláírását, a rendszer nem indul el.

  > [!NOTE]
  > A **biztonságos rendszerindítás engedélyezésének megkövetelése az eszköz** beállításában bizonyos TPM 1,2-és 2,0-eszközökön támogatott. Azon eszközök esetében, amelyek nem támogatják a TPM 2.0-s vagy újabb verzióit, az Intune-ban a szabályzat állapotánál a **Nem megfelelő** érték jelenik meg. További információ a támogatott verziókról: [Eszközállapot-igazolás](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Kód sértetlenségének megkövetelése**:  
  A kód integritása egy olyan szolgáltatás, amely a memóriába való betöltéskor ellenőrzi az illesztőprogram vagy a rendszerfájl integritását.
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  -  **Kötelező** – kód megkövetelése integritás, amely észleli, ha egy Aláíratlan illesztőprogram vagy rendszerfájl betöltődik a kernelbe. Azt is észleli, ha egy rendszerfájlt kártevő szoftver módosít, vagy egy rendszergazdai jogosultságokkal rendelkező felhasználói fiók futtat.

További források:

- Az állapotfigyelő szolgáltatás működésével kapcsolatos részletekért lásd: [Health igazolási CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Támogatási Tipp: Eszközállapot-igazolás beállítások használata az Intune megfelelőségi szabályzatának részeként](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643).

## <a name="device-properties"></a>Eszköztulajdonságok

### <a name="operating-system-version"></a>Operációs rendszer verziója

- **Operációs rendszer minimális verziója**:  
  Adja meg a minimálisan megengedett verziót a **Major.Minor.Build.cu** . A helyes érték megtekintéséhez nyisson meg egy parancssort, és írja be a következőt: `ver`. A `ver` parancs visszaadja a verziószámot a következő formátumban:

  `Microsoft Windows [Version 10.0.17134.1]`

  Ha egy eszközön a megadott operációsrendszer-verziónál korábbi verzió szerepel, nem megfelelőként fog megjelenni. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. A frissítés után hozzáférhetnek a vállalati erőforrásokhoz.

- **Maximális operációsrendszer-verzió**:  
  Adja meg a maximálisan engedélyezett verziót a főverzió. **alverzió. Build. változat számformátum** . A helyes érték megtekintéséhez nyisson meg egy parancssort, és írja be a következőt: `ver`. A `ver` parancs visszaadja a verziószámot a következő formátumban:

  `Microsoft Windows [Version 10.0.17134.1]`

  Ha egy eszköz a megadott verziónál újabb operációsrendszer-verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg a szabály meg nem változtatja az operációs rendszer verzióját.

- **A mobileszközök minimálisan szükséges operációs rendszere**:  
  Adja meg a minimálisan engedélyezett verziót, a főverzió. alverzió. Build számformátumot.

  Ha egy eszközön a megadott operációsrendszer-verzió korábbi verziója szerepel, nem megfelelőként fog megjelenni. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. A frissítés után hozzáférhetnek a vállalati erőforrásokhoz.

- **A mobileszközök számára maximálisan szükséges operációs rendszer**:  
  Adja meg a maximálisan engedélyezett verziót a főverzió. alverzió. alverzió. Build számában.

  Ha egy eszköz a megadott verziónál újabb operációsrendszer-verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg a szabály meg nem változtatja az operációs rendszer verzióját.

- **Érvényes operációsrendszer-buildek**:  
  Adjon meg egy tartományt az elfogadható operációsrendszer-verziókhoz, beleértve a minimális és a maximális értéket is. Az elfogadható OS-buildszámok listáját vesszővel tagolt (CSV) fájlban **exportálhatja**.

## <a name="configuration-manager-compliance"></a>Configuration Manager megfelelőség

Csak a Windows 10 és újabb rendszerű, közösen felügyelt eszközökre vonatkozik. A csak Intune-eszközök nem elérhető állapotot adnak vissza.

- **Eszköz megfelelőségének Megkövetelése System Center Configuration Manager**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem vizsgálja meg a megfelelőség Configuration Manager beállításait.
  - **Kötelező** – kötelezővé kell tennie az összes beállítást (a konfigurációs elemeket) a System Center Configuration Manager.  

    Megkövetelhető például, hogy minden szoftverfrissítés telepítve legyen az eszközökön. A Configuration Managerben az ehhez a követelményhez tartozó állapot a „Telepítve”. Ha az eszközön bármely program ismeretlen állapotban van, akkor az eszköz nem megfelelő az Intune-ban.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszközök zárolásának feloldásához**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.
  - **Kötelező** – a felhasználóknak jelszót kell megadniuk ahhoz, hogy hozzáférjenek az eszközhöz. 

- **Egyszerű jelszavak**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – a felhasználók egyszerű jelszavakat hozhatnak létre, például **1234** vagy **1111**.
  - **Letiltás** – a felhasználók nem hozhatnak létre egyszerű jelszavakat, például **1234** vagy **1111**.

- **Jelszó típusa**:  
  Válassza ki a jelszó vagy a PIN-kód típusát. A választható lehetőségek:
  - **Eszköz alapértelmezett értéke** (*alapértelmezett*) – jelszó, numerikus PIN kód vagy alfanumerikus PIN-kód megkövetelése
  - **Numerikus** – jelszó vagy numerikus PIN-kód megkövetelése
  - **Alfanumerikus** – jelszó vagy alfanumerikus PIN-kód megkövetelése.  
  
  Ha *alfanumerikus*értékre van állítva, a következő beállítások érhetők el:  
  - **Jelszó bonyolultsága**:  
    A választható lehetőségek: 
    - **Számjegyek és kisbetűk megkövetelése** (*alapértelmezett*)
    - **Számjegyek, kisbetűk és nagybetűk megkövetelése**
    - **Számjegyek, kisbetűk, nagybetűk és speciális karakterek megkövetelése**

    > [!TIP]
    > Az alfanumerikus jelszavas házirendek összetettek lehetnek. Javasoljuk, hogy a rendszergazdák további információért olvassa el a kriptográfiai szolgáltatókat:
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Jelszó minimális hossza**:  
  Adja meg a jelszóban szereplő számjegyek vagy karakterek minimális számát.

- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**:  
  Adja meg azt az üresjárati időt, ameddig a felhasználónak újra meg kell adnia a jelszavát.

- **Jelszó érvényessége (napokban)** :  
  Adja meg, hogy hány nap elteltével járjon le a jelszó, és újat kell létrehoznia a 1-730-ból.

- **Az újrafelhasználást megakadályozó korábbi jelszavak száma**:  
  Adja meg a nem használható korábban használt jelszavak számát.

- **Jelszó megkövetelése, ha az eszköz visszatér az inaktív állapotból (mobil és holografikus)** :  
  - **Nincs konfigurálva** (*alapértelmezett*)
  - **Megkövetelt** – az eszköz felhasználóinak meg kell adniuk a jelszót minden alkalommal, amikor az eszköz visszatér inaktív állapotból.

  > [!IMPORTANT]
  > Ha a jelszóra vonatkozó követelményt egy Windows asztalon módosítják, a felhasználók a következő bejelentkezéskor jelentkeznek, ahogy az az eszköz tétlenről aktív állapotba kerül. A követelménynek megfelelő jelszóval rendelkező felhasználókat a rendszer továbbra is megkéri a jelszavuk módosítására.

### <a name="encryption"></a>Encryption

- **Az eszközön lévő adattárolás titkosítása**:  
  - **Nincs konfigurálva** (*alapértelmezett*)
  - **Kötelező** – az adattárolást az eszközökön *titkosítani kell.*

  > [!NOTE]
  > Az **Adattárolás titkosítása az eszközön** beállítás általánosságban ellenőrzi, hogy van-e titkosítás az eszközön. Robusztusabb titkosítási beállítás megadásához fontolja meg a **BitLocker megkövetelése** beállítás használatát, amely a windowsos Eszközállapot-igazolást használja a Bitlocker-állapot ellenőrzéséhez a TPM szintjén.

### <a name="device-security"></a>Eszközbiztonság  

- **Tűzfal**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem szabályozza a Microsoft Defender-tűzfalat, és nem változtatja meg a meglévő beállításokat.
  - A Microsoft Defender-tűzfal bekapcsolásának **megkövetelése** , és a felhasználók kikapcsolásának megakadályozása.  

  [Tűzfal CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Ha az eszköz azonnal szinkronizál az újraindítás után, vagy azonnal szinkronizálja az alvó állapotból való felébresztést, akkor ez a beállítás **hibát**jelenthet. Előfordulhat, hogy ez a forgatókönyv nem érinti a teljes eszköz megfelelőségi állapotát. A megfelelőségi állapot újbóli kiértékeléséhez manuálisan [szinkronizálja az eszközt](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Platformmegbízhatósági modul (TPM)** :  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem vizsgálja meg a TPM-lapka verziójának eszközét.
  - **Kötelező** – az Intune ellenőrzi, hogy a TPM-lapka verziója megfelel-e a megfelelőségnek. Az eszköz akkor megfelelő, ha a TPM-lapka verziója nagyobb **nullánál (nulla** ). Az eszköz nem megfelelő, ha az eszközön nincs TPM-verzió.  

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion csomópont](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Víruskereső**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem keres az eszközre telepített vírusvédelmi megoldásokat. 
  - A megfelelőség ellenőrzése a [Windows Security Centerban](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)regisztrált **víruskereső-** megoldásokkal, például a Symantec és a Microsoft Defender használatával.

- **Kémprogram-elhárító**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem keres az eszközre telepített kémprogram-elhárító megoldásokat.
  - A [Windows Security Centerban](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)regisztrált kémprogram-elhárító megoldások (például a Symantec és a Microsoft Defender) használatának **megkövetelése** a megfelelőség ellenőrzéséhez.  

### <a name="defender"></a>Defender

*A Windows 10 asztali verziójában a következő megfelelőségi beállítások támogatottak.*

- **Microsoft Defender antimalware**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem szabályozza a szolgáltatást, és nem változtatja meg a meglévő beállításokat.
  - A Microsoft Defender **kártevő-** elhárító szolgáltatásának bekapcsolása, valamint a felhasználók kikapcsolásának megakadályozása. 

- **Microsoft Defender antimalware minimális verziója**:  
  Adja meg a Microsoft Defender kártevő-elhárító szolgáltatásának minimálisan engedélyezett verzióját. Például írja be a következőt: `4.11.0.0`. Ha üresen hagyja, a Microsoft Defender anti-malware szolgáltatás bármely verzióját használhatja.  

  *Alapértelmezés szerint nincs konfigurálva a verzió*.

- **Microsoft Defender antimalware biztonsági intelligencia naprakész**:  
  A Windows biztonsági vírus-és veszélyforrások elleni védelem frissítéseit szabályozza az eszközökön.  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem kényszeríti ki a követelményeket.
  - **Kötelező** – kényszerítse a Microsoft Defender biztonsági intelligencia naprakészen. 

  További információ: [biztonsági intelligencia frissítései a Microsoft Defender Antivirus és más Microsoft antimalware](https://www.microsoft.com/en-us/wdsi/defenderupdates).

- **Valós idejű védelem**:  
  - **Nincs konfigurálva** (*alapértelmezett*) – az Intune nem szabályozza ezt a funkciót, és nem változtatja meg a meglévő beállításokat.
  - **Szükséges** – a valós idejű védelem bekapcsolása, amely kártevőket, kémprogramokat és más nemkívánatos szoftvereket keres.  

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Microsoft Defender komplex veszélyforrások elleni védelem szabályai

- A **gép kockázati pontszámának megkövetelése az eszközön**:  
  Ezzel a beállítással a megfelelőségi feltételként a Defense Threat Services kockázatértékelését végezheti el. Megadható a legnagyobb megengedett fenyegetettségi szint:
  - **Nincs konfigurálva** (*alapértelmezett*)  
  - **Clear (Törlés** ) – Ez a lehetőség a legbiztonságosabb, mert az eszköz nem rendelkezhet fenyegetésekkel. Ha az eszköz bármilyen szintű fenyegetést észlel, azt a rendszer nem megfelelőként értékeli.
  - **Alacsony** – az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes** – az eszköz abban az esetben minősül megfelelőnek, ha az eszközön fennálló fenyegetések alacsony vagy közepes szintűek. Ha az eszköz magas szintű fenyegetéseket észlel, azt a rendszer nem megfelelőként határozza meg.
  - **Magas** – ez a legkevésbé biztonságos beállítás, és lehetővé teszi az összes veszélyforrás szintjét. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.
  
  A Microsoft Defender ATP (komplex veszélyforrások elleni védelem) a védelmi fenyegetés szolgáltatásként való beállításával kapcsolatban lásd: a [Microsoft DEFENDER ATP engedélyezése feltételes hozzáféréssel](advanced-threat-protection.md).


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

A Windows Holographic for Business **Windows 10 vagy újabb** platformot használ. A Windows Holographic for Business az alábbi beállításokat támogatja:

- **Rendszerbiztonság** > **Titkosítás** > **Adattároló titkosítása az eszközön**.

A Microsoft Hololens eszköz titkosításának ellenőrzéséhez tekintse meg az [Eszköztitkosítás ellenőrzése](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption) című témakört.

## <a name="surface-hub"></a>Surface Hub

A Surface Hub **Windows 10 vagy újabb** platformot használ. A felszíni hubok mind a megfelelőségi, mind a feltételes hozzáférés esetében támogatottak. A funkciók Surface hubokon való engedélyezéséhez javasoljuk, hogy [engedélyezze a Windows 10 automatikus regisztrációját](../enrollment/windows-enroll.md) az Intune-ban (Azure Active Directory (Azure ad)), és a Surface hub eszközöket az eszközökön. A Surface hub-nak az Azure AD-hez kell csatlakoznia ahhoz, hogy a megfelelőség és a feltételes hozzáférés működjön.

Útmutatásért lásd: [Windows rendszerű eszközök regisztrálásának beállítása](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg a Windows 8,1 rendszerű eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-windows-8-1.md) .
