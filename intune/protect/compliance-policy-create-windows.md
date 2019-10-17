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
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2e427fe0889dcfb51ba5be322ed4db566cc29e9d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502465"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 10 és újabb beállítások az eszközök megfelelőségi vagy nem megfelelőként való megjelöléséhez az Intune használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és ismerteti a Windows 10-es és újabb rendszerű eszközökön az Intune-ban konfigurálható különböző megfelelőségi beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használja a BitLocker megköveteléséhez, a minimális és maximális operációs rendszer beállításához, a kockázati szint beállításához a Microsoft Defender komplex veszélyforrások elleni védelem (ATP) használatával, és így tovább.

Ez a funkció az alábbiakra vonatkozik:

- Windows 10 és újabb
- Windows Holographic for Business
- Surface Hub

Intune-rendszergazdaként ezeket a megfelelőségi beállításokat használhatja a szervezeti erőforrások védelméhez. Ha többet szeretne megtudni a megfelelőségi szabályzatokról és azokról, tekintse meg [az eszközök megfelelőségének megkezdése](device-compliance-get-started.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Megfelelőségi szabályzat létrehozása](create-compliance-policy.md#create-the-policy). A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.

## <a name="device-health"></a>Device health

- **BitLocker megkövetelése**: Ha a beállítás **kötelező**, az eszköz a rendszer kikapcsolásakor vagy a hibernált állapotában a meghajtón tárolt adatok védelme érdekében a jogosulatlan hozzáférés ellen biztosíthatja a meghajtót. A Windows BitLocker meghajtótitkosítás a Windows operációs rendszer kötetén tárolt összes adatot titkosítja. A BitLocker a TPM-mel segíti elő a Windows operációs rendszer és a felhasználói adatok védelmét. Azt is segít megerősíteni, hogy a számítógép nincs-e illetéktelenül megoldva, még akkor is, ha annak felügyelet nélküli, elveszett vagy ellopták. Ha a számítógépen kompatibilis TPM található, a BitLocker a TPM-mel zárolja az adatokat védő titkosítási kulcsokat. Ennek eredményeképpen a kulcsok nem érhetők el, amíg a TPM nem ellenőrzi a számítógép állapotát.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

- A **biztonságos rendszerindítás engedélyezésének megkövetelése az eszközön**: Ha a beállítás a **szükséges**értékre van állítva, a rendszer kényszerítve van a gyári megbízható állapotba való rendszerindításra. Ha ez a beállítás engedélyezve van, a gép rendszerindításához használt alapvető összetevőknek megfelelő titkosítási aláírásokkal kell rendelkezniük, amelyeket az eszközt gyártó szervezet megbízhatónak tekint. Az UEFI belső vezérlőprogram ellenőrzi az aláírást, mielőtt engedélyezi a számítógép elindítását. Ha bármely fájl illetéktelenül van módosítva, amely megszakítja az aláírását, a rendszer nem indul el.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

  > [!NOTE]
  > A **biztonságos rendszerindítás engedélyezésének megkövetelése az eszköz** beállításában bizonyos TPM 1,2-és 2,0-eszközökön támogatott. Azon eszközök esetében, amelyek nem támogatják a TPM 2.0-s vagy újabb verzióit, az Intune-ban a szabályzat állapotánál a **Nem megfelelő** érték jelenik meg. További információ a támogatott verziókról: [Eszközállapot-igazolás](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Kódintegritás megkövetelése**: A kódintegritás olyan szolgáltatás, amely ellenőrzi az illesztők vagy rendszerfájlok integritását, amikor azokat betölti a memóriába. Ha a **kötelező**beállításra van beállítva, a kód integritása észleli, ha aláíratlan illesztőprogramot vagy rendszerfájlt tölt be a kernelbe. Azt is észleli, ha egy rendszerfájlt egy olyan kártevő szoftver módosít, amely rendszergazdai jogosultságokkal rendelkező felhasználói fiókkal fut.

  Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a rendszer nem értékeli ki a megfelelőségi és a nem megfelelőségi beállítást.

További források:

- Az [állapot igazolása CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) részletesen ismerteti a szolgáltatás működésének módját.
- [Támogatási Tipp: Eszközállapot-igazolás beállítások használata az Intune megfelelőségi szabályzatának részeként](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>Eszköztulajdonságok

- **Operációs rendszer minimális verziója**: Adja meg a minimálisan megkövetelt verziót a **főverzió.alverzió.build.CU szám** formátumban. A helyes érték megtekintéséhez nyisson meg egy parancssort, és írja be a következőt: `ver`. A `ver` parancs visszaadja a verziószámot a következő formátumban:

  `Microsoft Windows [Version 10.0.17134.1]`

  Ha egy eszközön a megadott operációsrendszer-verziónál korábbi verzió szerepel, nem megfelelőként fog megjelenni. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. A frissítés után hozzáférhetnek a vállalati erőforrásokhoz.

- **Operációs rendszer maximális verziója**: Adja meg a maximálisan megengedhető verziót a **főverzió.alverzió.build.változatszám** formátumban. A helyes érték megtekintéséhez nyisson meg egy parancssort, és írja be a következőt: `ver`. A `ver` parancs visszaadja a verziószámot a következő formátumban:

  `Microsoft Windows [Version 10.0.17134.1]`

  Ha egy eszköz a megadott verziónál újabb operációsrendszer-verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg a szabály meg nem változtatja az operációs rendszer verzióját.

- **Operációs rendszer minimális verziója mobileszközöknél**: Adja meg a minimálisan megkövetelt verziót a főverzió.alverzió.build formátumban.

  Ha egy eszközön a megadott operációsrendszer-verzió korábbi verziója szerepel, nem megfelelőként fog megjelenni. Megjelenik egy hivatkozás, amelyen a verziófrissítésre vonatkozó információk érhetők el. A végfelhasználó dönthet úgy, hogy frissíti az eszközét. A frissítés után hozzáférhetnek a vállalati erőforrásokhoz.

- **Operációs rendszer maximális verziója mobileszközöknél**: Adja meg a maximálisan megengedett verziót a főverzió.alverzió.build formátumban.

  Ha egy eszköz a megadott verziónál újabb operációsrendszer-verziót használ, a rendszer letiltja a szervezeti erőforrásokhoz való hozzáférést. A végfelhasználónak kapcsolatba kell lépnie a rendszergazdával. Az eszköz addig nem fér hozzá a szervezeti erőforrásokhoz, amíg a szabály meg nem változtatja az operációs rendszer verzióját.

- **Érvényes operációsrendszer-buildek**: Megadható az elfogadható operációsrendszer-verziók minimumot és maximumot is tartalmazó tartománya. Az elfogadható OS-buildszámok listáját vesszővel tagolt (CSV) fájlban **exportálhatja**.

## <a name="configuration-manager-compliance"></a>Configuration Manager megfelelőség

Csak a Windows 10 és újabb rendszerű, közösen felügyelt eszközökre vonatkozik. A csak Intune-eszközök nem elérhető állapotot adnak vissza.

- **Eszköz megfelelőségének megkövetelése a System Center Configuration Managertól**: válassza a **kötelező** lehetőséget, ha a System Center Configuration Manager összes beállítását (konfigurációs elemeit) szeretné kényszeríteni. 

  Megkövetelhető például, hogy minden szoftverfrissítés telepítve legyen az eszközökön. A Configuration Managerben az ehhez a követelményhez tartozó állapot a „Telepítve”. Ha az eszközön bármely program ismeretlen állapotban van, akkor az eszköz nem megfelelő az Intune-ban.
  
  Ha **nincs konfigurálva**, az Intune nem vizsgálja meg a megfelelőség Configuration Manager beállításait.

## <a name="system-security"></a>Rendszerbiztonság

### <a name="password"></a>Jelszó

- **Jelszó megkövetelése a mobileszköz-zárolás feloldásához**: A felhasználók **kötelesek** jelszót megadni az eszköz eléréséhez. Ha **nincs konfigurálva**, az Intune nem értékeli ki, hogy az eszköz megfelel-e a megfelelőségi jelszó beállításainak.
- **Egyszerű jelszavak**: Ha nem szeretné engedélyezni, hogy a felhasználók olyan egyszerű jelszavakat használhassanak, mint az **1234** vagy az **1111**, válassza a **Tiltás** lehetőséget. A **Nincs konfigurálva** beállítással a felhasználók olyan jelszavakat is létrehozhatnak, mint az **1234** vagy az **1111**.
- **Jelszó típusa**: válassza ki, hogy milyen típusú jelszót vagy PIN-kódot kell megadnia. A választható lehetőségek:

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

- **Jelszó minimális hossza**: Meghatározhatja a jelszóban szereplő számjegyek vagy karakterek minimális számát.
- **Jelszó kérése legfeljebb ennyi perc inaktivitás után**: Arra a tétlenségi időre vonatkozik, amelynek elteltével a felhasználónak újra meg kell adnia a jelszavát.
- **Jelszó érvényessége (napokban)** : adja meg, hogy hány nap elteltével járjon le a jelszó, és újat kell létrehoznia a 1-730-ból.
- Az **újrafelhasználást megakadályozó korábbi jelszavak száma**: megadhatja, hogy hány korábban használt jelszót ne lehessen használni.
- **Jelszó megkövetelése amikor az eszköz visszatér az inaktív állapotból (mobil és Holographic rendszer esetén)** : A felhasználóknak minden alkalommal meg kell adniuk a jelszót, amikor az eszköz visszatér az inaktív állapotból.

  > [!IMPORTANT]
  > Ha a jelszóra vonatkozó követelményt egy Windows asztalon módosítják, a felhasználók a következő bejelentkezéskor jelentkeznek, ahogy az az eszköz tétlenről aktív állapotba kerül. A követelménynek megfelelő jelszóval rendelkező felhasználókat a rendszer továbbra is megkéri a jelszavuk módosítására.

### <a name="encryption"></a>Encryption

- **Adattároló titkosítása az eszközön**: A **Kötelező** lehetőséget választva az adattárolók titkosítva lesznek az eszközökön.

  > [!NOTE]
  > Az **Adattárolás titkosítása az eszközön** beállítás általánosságban ellenőrzi, hogy van-e titkosítás az eszközön. Robusztusabb titkosítási beállítás megadásához fontolja meg a **BitLocker megkövetelése** beállítás használatát, amely a windowsos Eszközállapot-igazolást használja a Bitlocker-állapot ellenőrzéséhez a TPM szintjén.

### <a name="device-security"></a>Eszközbiztonság

- **Tűzfal**: állítsa be a **kötelező** beállítást a Microsoft Defender-tűzfal bekapcsolásához, és a felhasználók kikapcsolásának megakadályozása. **Nincs konfigurálva** (alapértelmezés) nem szabályozza a Microsoft Defender-tűzfalat, és nem változtatja meg a meglévő beállításokat.

  [Tűzfal CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Ha az eszköz azonnal szinkronizál az újraindítás után, vagy azonnal szinkronizálja az alvó állapotból való felébresztést, akkor ez a beállítás **hibát**jelenthet. Előfordulhat, hogy ez a forgatókönyv nem érinti a teljes eszköz megfelelőségi állapotát. A megfelelőségi állapot újbóli kiértékeléséhez manuálisan [szinkronizálja az eszközt](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Platformmegbízhatósági modul (TPM)** : Ha a beállítás **kötelező**, az Intune ellenőrzi a verzió megfelelőségét. Az eszköz akkor megfelelő, ha a TPM-lapka verziója nagyobb nullánál (nulla). Az eszköz nem megfelelő, ha az eszközön nincs TPM-verzió. Ha **nincs konfigurálva**, az Intune nem vizsgálja meg a TPM-lapka verziójának eszközét.

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion csomópont](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Víruskereső**: Ha **kötelező**beállításra van beállítva, a [Windows Security Centerban](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)regisztrált víruskereső-megoldásokkal, például a Symantec és a Microsoft Defender alkalmazással is ellenőrizhetők a megfelelőség. A **Nincs konfigurálva** beállítás esetén az Intune nem ellenőrzi az eszközön telepített vírusvédelmi megoldásokat.
- **Kémprogram-elhárító**: Ha **kötelező**beállításra van beállítva, a [Windows Security Centerban](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)regisztrált kémprogram-elhárító megoldásokkal, például a Symantec és a Microsoft Defender alkalmazással is megtekintheti a megfelelőséget. A **Nincs konfigurálva** beállítás esetén az Intune nem ellenőrzi az eszközön telepített kémprogram-elhárító megoldásokat.

### <a name="defender"></a>Defender

- **Microsoft Defender antimalware**: állítsa be **a beállítást** a Microsoft Defender kártevő-elhárító szolgáltatásának bekapcsolásához, és megakadályozza a felhasználók kikapcsolását. **Nincs konfigurálva** (az alapértelmezett) nem szabályozza a szolgáltatást, és nem változtatja meg a meglévő beállításokat.
- **Microsoft Defender antimalware minimális verziója**: adja meg a Microsoft Defender kártevő-elhárító szolgáltatásának minimálisan engedélyezett verzióját. Például írja be a következőt: `4.11.0.0`. Ha üresen hagyja, a Microsoft Defender anti-malware szolgáltatás bármely verzióját használhatja.
- **Microsoft Defender antimalware biztonsági intelligencia naprakész**: szabályozza a Windows biztonsági vírus-és veszélyforrások elleni védelem frissítéseit az eszközökön. **Szükséges** kényszeríteni a Microsoft Defender biztonsági intelligencia naprakészen kell lennie. **Nincs konfigurálva** (az alapértelmezett) nem kényszeríti a követelményeket.

  A [Microsoft Defender Antivirus és más Microsoft antimalware biztonsági intelligenciával kapcsolatos frissítései több információt biztosítanak](https://www.microsoft.com/en-us/wdsi/defenderupdates) a biztonsági intelligenciáról.

- **Valós idejű védelem** **: a** valós idejű védelem bekapcsolása a kártevők, kémprogramok és más nemkívánatos szoftverek keresésével. **Nincs konfigurálva** (alapértelmezés) nem szabályozza ezt a funkciót, és nem változtatja meg a meglévő beállításokat.

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

- **A következő vagy ez alatti számítógép-kockázati pontszám megkövetelése**: Ezzel a beállítással a fenyegetéseket elhárító szolgáltatásoktól származó kockázatbecslés lesz a megfelelőség feltétele. Megadható a legnagyobb megengedett fenyegetettségi szint:

  - **Tiszta**: Ez a legbiztonságosabb beállítás, mivel az eszköz esetében semmilyen fenyegetés nem engedélyezett. Ha az eszköz bármilyen szintű fenyegetést észlel, azt a rendszer nem megfelelőként értékeli.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt fenyegetések alacsony vagy közepes szintűek. Ha az eszköz magas szintű fenyegetéseket észlel, azt a rendszer nem megfelelőként határozza meg.
  - **Magas**: Ez a legkevésbé biztonságos, minden fenyegetettségi szintet megengedő beállítás. Akkor lehet hasznos, ha ezt a megoldást kizárólag jelentéskészítési célokra használja.
  
  A Microsoft Defender ATP (komplex veszélyforrások elleni védelem) a védelmi fenyegetés szolgáltatásként való beállításával kapcsolatban lásd: a [Microsoft DEFENDER ATP engedélyezése feltételes hozzáféréssel](advanced-threat-protection.md).

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

A Windows Holographic for Business **Windows 10 vagy újabb** platformot használ. A Windows Holographic for Business az alábbi beállításokat támogatja:

- **Rendszerbiztonság** > **Titkosítás** > **Adattároló titkosítása az eszközön**.

A Microsoft Hololens eszköz titkosításának ellenőrzéséhez tekintse meg az [Eszköztitkosítás ellenőrzése](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption) című témakört.

## <a name="surface-hub"></a>Surface Hub

A Surface Hub **Windows 10 vagy újabb** platformot használ. A felszíni hubok mind a megfelelőségi, mind a feltételes hozzáférés esetében támogatottak. A funkciók Surface hubokon való engedélyezéséhez javasoljuk, hogy [engedélyezze a Windows 10 automatikus regisztrációját](../enrollment/windows-enroll.md) az Intune-ban (Azure Active Directory (Azure ad)), és a Surface hub eszközöket az eszközökön. A Surface hub-nak az Azure AD-hez kell csatlakoznia ahhoz, hogy a megfelelőség és a feltételes hozzáférés működjön.

Erről a [Windowsos eszközök regisztrációjának beállítása](../enrollment/windows-enroll.md) című cikk nyújt útmutatást.

## <a name="next-steps"></a>További lépések

- [Műveletek hozzáadása a nem megfelelő eszközökhöz](actions-for-noncompliance.md) és [a hatókör-címkék használata a házirendek szűréséhez](../fundamentals/scope-tags.md).
- [A megfelelőségi szabályzatok figyelése](compliance-policy-monitor.md).
- Tekintse [meg a Windows 8,1 rendszerű eszközök megfelelőségi szabályzatának beállításait](compliance-policy-create-windows-8-1.md) .
