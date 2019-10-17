---
title: Védelmi beállítások Windows 10-es eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Windows 10-es eszközökön használja vagy konfigurálja az Endpoint Protection beállításait a Windows Defender szolgáltatásainak engedélyezéséhez, beleértve az Application Guard, a tűzfal, a SmartScreen, a titkosítás és a BitLocker, az őr, az alkalmazás-vezérlés, a Security Center és a biztonság beállítást helyi eszközök Microsoft Intuneban.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40865dcca0b0109ae36f65b6691672c0035732b5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502280"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Windows 10 (és újabb) beállítások az eszközök az Intune-nal való védelemmel való ellátásához  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]  

Microsoft Intune számos olyan beállítást tartalmaz, amelyek segítenek az eszközök védelmében. Ez a cikk a Windows 10 és újabb rendszerű eszközökön engedélyezhető és konfigurálható beállításokat ismerteti. Ezek a beállítások az Intune-beli Endpoint Protection-konfigurációs profilban jönnek létre a biztonság szabályozásához, beleértve a BitLockert és a Windows Defendert is.  

A Windows Defender víruskereső konfigurálásához tekintse meg a [Windows 10-es eszközök korlátozásait](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)ismertető témakört.  

## <a name="before-you-begin"></a>Előkészületek  

[Hozzon létre egy Endpoint Protection-eszköz konfigurációs profilját](endpoint-protection-configure.md).  

További információ a konfigurációs szolgáltatókról (CSP): a [Configuration Service Provider referenciája](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).  

## <a name="windows-defender-application-guard"></a>Windows Defender alkalmazásőr  

A Microsoft Edge használata közben a Windows Defender alkalmazásőr megvédi a környezetét az olyan webhelyektől, amelyek nincsenek megbízhatóként meghatározva a szervezetében. Ha a felhasználók olyan helyeket látogatnak meg, amelyek nem szerepelnek az elszigetelt hálózati határon, a helyek egy Hyper-V virtuális böngészési munkamenetben nyílnak meg. A megbízható helyeket egy hálózati határ definiálja, amely az eszköz konfigurációjában van konfigurálva.  

Az Alkalmazásőr csak a 64 bites Windows 10-eszközöknél érhető el. Ennek a profilnak a használatával telepítve lesz az Alkalmazásőr aktiválásához szükséges Win32-összetevő.  

- **Application Guard**  
  **Alapértelmezett**: nincs konfigurálva  
   Application Guard CSP: [Beállítások/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Engedélyezve az Edge számára** – bekapcsolja ezt a funkciót, amely nem megbízható helyeket nyit meg egy Hyper-V virtualizált tallózási tárolóban.  
  - **Nincs konfigurálva** – bármely hely (megbízható és nem megbízható) megnyitható az eszközön.  

- **A vágólap viselkedése**  
  **Alapértelmezett**: nincs konfigurálva  
   Application Guard CSP: [Beállítások/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  Válassza ki, hogy mely másolási és beillesztési műveletek engedélyezettek a helyi számítógép és az Application Guard virtuális böngésző között.  
  - **Nincs konfigurálva**  
  - **Csak a SZÁMÍTÓGÉPről a böngészőbe való másolás és beillesztés engedélyezése**  
  - **A böngészőből csak a számítógépre való másolás és beillesztés engedélyezése**  
  - **A számítógép és a böngésző közötti másolás és beillesztés engedélyezése**  
  - **A számítógép és a böngésző közötti másolás és beillesztés tiltása**  

- **Vágólap tartalma**  
  Ez a beállítás csak akkor érhető el, ha a *vágólap viselkedése* az *engedélyezési* beállítások egyikére van beállítva.  
  **Alapértelmezett**: nincs konfigurálva  
  Application Guard CSP: [Beállítások/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  Válassza ki az engedélyezett vágólap tartalmát.  
  - **Nincs konfigurálva**  
  - **Szöveg**  
  - **Képek**  
  - **Szöveg és képek**  

- **Külső tartalom a vállalati webhelyeken**  
  **Alapértelmezett**: nincs konfigurálva  
  Application Guard CSP: [Beállítások/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - A nem jóváhagyott webhelyekről származó tartalom betöltésének **tiltása.**  
  - **Nem konfigurált** – a nem vállalati webhelyek megnyithatók az eszközön.  
 
- **Nyomtatás a virtuális böngészőből**  
  **Alapértelmezett**: nincs konfigurálva  
  Application Guard CSP: [Beállítások/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **Engedélyezés** – engedélyezi a kiválasztott tartalom kinyomtatását a virtuális böngészőből.  
  - **Nincs konfigurálva** Tiltsa le az összes nyomtatási funkciót.  

  Ha *engedélyezi* a nyomtatást, a következő beállításokat állíthatja be:
  - **Nyomtatási típus (ok)** Válasszon egyet vagy többet a következő lehetőségek közül:  
    - PDF  
    - XPS  
    - Helyi nyomtatók
    - Hálózati nyomtatók  

- **Naplók összegyűjtése**  
  **Alapértelmezett**: nincs konfigurálva  
  Application Guard CSP: [audit/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **Engedélyezés** – naplók gyűjtése az Application Guard-böngészési munkamenetben előforduló eseményekhez.  
  - **Nincs konfigurálva** – a böngészési munkameneten belül ne gyűjtsön naplókat.  

- **A felhasználó által létrehozott böngészőbeli adat megőrzése**  
  **Alapértelmezett**: nincs konfigurálva  
  Application Guard CSP: [Beállítások/AllowPersistence](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **Engedélyezés** Az Application Guard virtuális böngészési munkamenet során létrehozott felhasználói adatfájlok (például jelszavak, kedvencek és cookie-k) mentése.  
  - **Nincs konfigurálva** A felhasználó által letöltött fájlok és az adatértékek elvetése az eszköz újraindításakor, vagy amikor egy felhasználó kijelentkezik.  

- **Grafikus gyorsítás**  
 **Alapértelmezett**: nincs konfigurálva  
  Application Guard CSP: [Beállítások/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - A virtuális grafikus processzorhoz való hozzáférés megszerzésével gyorsabbá **teheti** a grafikai igényű webhelyek és videók betöltését.  
  - **Nincs konfigurálva** Az eszköz PROCESSZORának használata grafikus elemekhez; Ne használja a virtuális grafikus feldolgozó egységet.  

- **Fájlok letöltése a gazdagép fájlrendszerére**  
  **Alapértelmezett**: nincs konfigurálva  
  Application Guard CSP: [Beállítások/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **Engedélyezés** – a felhasználók fájlokat tölthetnek le a virtualizált böngészőből a gazda operációs rendszerre.  
  - **Nincs konfigurálva** – megtartja a fájlok helyi beállításait az eszközön, és nem tölti le a fájlokat a gazdagép fájlrendszerére.  

## <a name="windows-defender-firewall"></a>Windows Defender-tűzfal  
 
### <a name="global-settings"></a>Globális beállítások  

Ezek a beállítások minden hálózattípusnál alkalmazhatók.  

- **File Transfer Protocol**  
  **Alapértelmezett**: nincs konfigurálva  
   Tűzfal CSP: [MdmStore/Global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - Állapot **-nyilvántartó FTP letiltásának** letiltása.  
  - **Nincs konfigurálva** – a tűzfal állapot-nyilvántartó FTP-szűrést végez a másodlagos kapcsolatok engedélyezéséhez.  

- **Biztonsági társítás üresjárati ideje törlés előtt**  
  **Alapértelmezett**: *nincs konfigurálva*  
   Tűzfal CSP: [MdmStore/Global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   A biztonsági társítások törlését követő üresjárati idő másodpercben megadva.   

- **Előmegosztott kulcs kódolás**  
  **Alapértelmezett**: nincs konfigurálva  
   Tűzfal CSP: [MdmStore/Global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Engedélyezheti** az előre elnyírt kulcsok kódolását UTF-8 használatával.  
   - **Nincs konfigurálva** – a helyi tároló értékének használatával kódolja az előre lenyírt kulcsokat.  

- **IPsec-kivételek**  
  **Alapértelmezett**: *0 kiválasztva*  
   Tűzfal CSP: [MdmStore/Global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   Válasszon ki egyet vagy többet a következő típusú forgalom alól, amely mentesül az IPsec alól:  
   - **Szomszédfelderítési IPv6 ICMP-típuskódok**  
   - **ICMP**  
   - **Útválasztó-felderítési IPv6 ICMP-típuskódok**  
   - **IPv4-es és IPv6-os DHCP hálózati forgalom**  

- **Visszavont tanúsítványok listájának ellenőrzése**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [MdmStore/Global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  Válassza ki, hogy az eszköz hogyan ellenőrizze a visszavont tanúsítványok listáját. A lehetőségek a következők:  
  - **CRL-ellenőrzés letiltása**  
  - **Sikertelen CRL-ellenőrzés csak visszavont tanúsítványon**  
  - **Sikertelen CRL-ellenőrzés az észlelt hibákon**.  
 

- **A hitelesítési készletek alkalmi egyeztetése egy beírási modulban**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [MdmStore/Global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **Engedélyezés** A beírási moduloknak csak a nem támogatott hitelesítési csomagokat kell figyelmen kívül hagyniuk.  
  - **Nincs konfigurálva**, a beírási moduloknak figyelmen kívül kell hagyniuk a teljes hitelesítési készletet, ha nem támogatják a készletben megadott összes hitelesítési lakosztályt.  


- **Csomagok várólistára helyezése**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [MdmStore/Global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  Itt adhatja meg, hogy a rendszer hogyan engedélyezze a szoftveres skálázást a fogadási oldalon az IPsec Tunnel Gateway-forgatókönyvhöz továbbított titkosított fogadás és tiszta szöveg esetén. Ez a beállítás megerősíti a csomagok sorrendjét. A lehetőségek a következők:  
  - **Nincs konfigurálva**  
  - **Az összes Packet Queuing letiltása**  
  - **Csak bejövő titkosított csomagok várólistára helyezése**  
  - **Várólista-csomagok a visszafejtés után csak továbbításra**  
  - **Bejövő és kimenő csomagok konfigurálása**  

### <a name="network-settings"></a>Hálózati beállítások  

Ebben a cikkben a következő beállítások jelennek meg egyetlen alkalommal, de a három adott hálózati típusra vonatkoznak:  
- **Tartományi (munkahelyi) hálózat**  
- **Privát (felderíthető) hálózat**  
- **Nyilvános (nem felderíthető) hálózat**  

#### <a name="general-settings"></a>Általános beállítások  

- **Windows Defender-tűzfal**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **Engedélyezze** a tűzfal bekapcsolását és a fokozott biztonságot. 
  - **Nincs konfigurálva** Engedélyezi az összes hálózati forgalmat, függetlenül az egyéb házirend-beállításoktól.  

- **Rejtett üzemmód**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **Nincs konfigurálva**  
  - A **Block** -Firewall blokkolva van a rejtett módban való működésben. A rejtett üzemmód tiltásnak a beállítása az **IPsec-et használó csomagok mentességének** letiltását is lehetővé teszi.  
  - **Engedélyezés** – a tűzfal lopakodó üzemmódban működik, ami segít megelőzni a kérelmekre való válaszadást.  

- **IPsec által védett csomagok kivétele rejtett móddal**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  Ezt a beállítást a rendszer figyelmen kívül hagyja, ha a *rejtett mód* *blokkolásra*van beállítva.  

  - **Nincs konfigurálva**  
  - **Letiltás** – az IPSec által védett csomagok nem kapnak kivételeket.  
  - **Engedélyezés** – kivételek engedélyezése. A tűzfal lopakodó üzemmódja nem akadályozhatja meg, hogy a gazdaszámítógép ne válaszoljon az IPsec által védett, kéretlen hálózati forgalomra.  

- **Védett**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [védett](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **Nincs konfigurálva**  
    - **Letiltás** – ha a Windows Defender-tűzfal be van kapcsolva, és ez a beállítás *blokkolásra*van beállítva, az összes bejövő forgalom le lesz tiltva, az egyéb házirend-beállításoktól függetlenül. 
    - **Engedélyezés** – ha engedélyezve értékre van *állítva, ez*a beállítás ki van kapcsolva, és a bejövő forgalom más házirend-beállítások alapján engedélyezett.

- **Egyedi küldéses válaszok a csoportos küldésű szórásokra**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  Csoportos küldésű vagy szórási üzenetekre általában nem kívánatos egyedi küldésű válaszokat kapni, Ezek a válaszok szolgáltatásmegtagadást (DOS) okozó támadást vagy egy támadó által megkísérelt, ismert élő számítógép mintavételét jelezhetik.  
  - **Nincs konfigurálva**  
  - Egyedi küldésű **válaszok letiltása csoportos** küldésű szórásra – letiltás.  
  - **Engedélyezés** – egyedi küldésű válaszok küldése csoportos küldésű szórásra.  

- **Bejövő értesítések**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **Nincs konfigurálva**  
  - **Blokkolhatja** azokat az értesítéseket, amelyeket akkor kell használni, ha egy alkalmazás nem figyeli a portot.  
  - **Engedélyezés** – engedélyezi ezt a beállítást, és értesítéseket jeleníthet meg a felhasználóknak, ha egy alkalmazás nem figyeli a portot.  

- **A kimenő kapcsolatok alapértelmezett művelete**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  Konfigurálja az alapértelmezett műveleti tűzfalat a kimenő kapcsolatokon. Ez a beállítás a Windows 1809-es vagy újabb verziójára lesz alkalmazva.  

  - **Nincs konfigurálva**  
  - **Letiltás** – az alapértelmezett tűzfalszabály nem fut a kimenő forgalomon, kivéve, ha explicit módon nincs megadva a blokkolás.  
  - **Engedélyezés** – az alapértelmezett tűzfalszabályok a kimenő kapcsolatokon futnak.  

- **Bejövő kapcsolatok alapértelmezett művelete**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **Nincs konfigurálva**  
  - **Letiltás** – az alapértelmezett tűzfalszabály nem fut a bejövő kapcsolatokon.  
  - **Engedélyezés** – az alapértelmezett tűzfalszabály a bejövő kapcsolatokon fut.  

#### <a name="rule-merging"></a>Szabályegyesítés  

- **Engedélyezve van az alkalmazás Windows Defender-tűzfalszabályok a helyi tárolóból**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **Nincs konfigurálva**  
  - **Letiltás** – a rendszer figyelmen kívül hagyja a helyi tárolóban lévő, a jogosult alkalmazás tűzfalszabályok szabályait, és nem kényszeríti ki őket.  
  - Engedélyezi, hogy a -
   Choose **engedélyezze** a helyi tárolóban a tűzfalszabályok **használatát** , hogy azok felismerhetők és érvénybe lépjenek.  

- **Globális port a Windows Defender tűzfalszabályok a helyi tárolóból**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **Nincs konfigurálva**  
  - **Letiltás** – a helyi tárolóban a globális porthoz tartozó tűzfalszabályok figyelmen kívül lesznek hagyva, és nincsenek kikényszerítve.  
  - **Engedélyezés** – a globális port tűzfalszabályok alkalmazása a helyi tárolóban felismerhető és érvényesíthető.  

- **Windows Defender-tűzfalszabályok a helyi tárolóban**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [AllowLocalPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **Nincs konfigurálva**  
  - A **rendszer figyelmen** kívül hagyja a tűzfal szabályait a helyi tárolóból, és nem kényszeríti ki.
  - **Engedélyezés** – tűzfalszabályok alkalmazása a helyi tárolóban felismerés és kényszerített állapotba.  

- **Az IPsec-szabályok a helyi tárolóból**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **Nincs konfigurálva**  
  - **Letiltás** – a helyi tárolóban lévő kapcsolatbiztonsági szabályok figyelmen kívül lesznek hagyva és nem kényszerítve, a séma verziójától és a kapcsolatbiztonsági szabály verziójától függetlenül.  
  - **Engedélyezés** – kapcsolatbiztonsági szabályok alkalmazása a helyi tárolóból, a séma vagy a kapcsolatbiztonsági szabály verziójától függetlenül.  

### <a name="firewall-rules"></a>Tűzfalszabályok  

**Hozzáadhat** egy vagy több egyéni tűzfalszabály-szabályt is. További információ: [Egyéni tűzfalszabályok hozzáadása Windows 10-es eszközökhöz](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices).  

Az egyéni tűzfalszabályok a következő beállításokat támogatják:  

#### <a name="general-settings"></a>Általános beállítások:  

- **Név**  
  **Alapértelmezett**: *nincs név*  

  Adjon meg egy rövid nevet a szabálynak. Ez a név fog megjelenni a szabályok listájában, hogy könnyebben azonosítható legyen.  

- **Leírás**  
  **Alapértelmezett**: *nincs Leírás*  

  Adja meg a szabály leírását.  

- **Irány**@no__t – 1  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  Annak meghatározása, hogy ez a szabály a **bejövő**vagy a **kimenő** forgalomra vonatkozik-e. Ha a beállítás **nincs konfigurálva**, a szabály automatikusan a kimenő forgalomra vonatkozik.  

- **Művelet**  
  **Alapértelmezett**: nincs konfigurálva  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)és [FirewallRules/*FirewallRuleName*/Action/type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  Válassza az **Engedélyezés** vagy a **Letiltás**lehetőséget. Ha a **nincs konfigurálva**értékre van állítva, a szabály alapértelmezés szerint engedélyezi a forgalmat.  

- **Hálózat típusa**  
  **Alapértelmezett**: 0 kiválasztva  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  Válasszon legfeljebb három olyan típusú hálózati típust, amelyhez ez a szabály tartozik. A lehetőségek közé tartozik a **tartomány**, a **saját**és a **nyilvános**.  Ha nincs kiválasztva hálózati típus, a szabály mindhárom hálózati típusra vonatkozik.  

#### <a name="application-settings"></a>Alkalmazásbeállítások  

- **Alkalmazás (ok)**  
  **Alapértelmezés**: az összes  

  Egy alkalmazás vagy program kapcsolatainak vezérlése. Válasszon egyet a következő lehetőségek közül, majd fejezze be a további konfigurálást:  
  - **Csomag családjának neve** – adja meg a csomag családjának nevét. A csomag családi nevének megkereséséhez használja a **Get-AppxPackage PowerShell-** parancsot.   
    Tűzfal CSP: [FirewallRules/*FirewallRuleName*/app/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **Fájl elérési útja** – meg kell adnia egy, az eszközön található alkalmazás elérési útját, amely abszolút elérési út vagy relatív elérési út lehet. Például: C:\Windows\System\Notepad.exe vagy%WINDIR%\Notepad.exe.  
    Tűzfal CSP: [FirewallRules/*FirewallRuleName*/app/filepath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Windows-szolgáltatás** – adja meg a Windows-szolgáltatás rövid nevét, ha az szolgáltatás, és nem olyan alkalmazás, amely forgalmat küld vagy fogad. A szolgáltatás rövid nevének megkereséséhez használja a **Get-Service PowerShell-** parancsot.  
    Tűzfal CSP: [FirewallRules/*FirewallRuleName*/app/servicename](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **Összes**– *nem érhető el további konfiguráció*.  

#### <a name="ip-address-settings"></a>IP-cím beállításai  

Itt adhatja meg azokat a helyi és távoli címeket, amelyekre ez a szabály vonatkozik.  

- **Helyi címek**@no__t – 1  
  **Alapértelmezett**: bármely címnek  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  Válassza ki **a kívánt címeket vagy a** **megadott címeket**.  

  Ha *megadott címet*használ, egy vagy több címet ad hozzá a szabály által érintett helyi címek vesszővel tagolt listájához. Az érvényes tokenek a következők:  
  - *Bármely* helyi címként használjon csillagot "*". Ha csillagot használ, az csak az Ön által használt token lehet.  
  - Alhálózat megadásához használja az alhálózati maszkot vagy a hálózati előtag jelölését. Ha nincs megadva alhálózati maszk és hálózati előtag, az alhálózati maszk alapértelmezett értéke 255.255.255.255.  
  - Érvényes IPv6-cím.  
  - Egy IPv4-címtartomány a "kezdő címe-záró címe" formátumban, szóközök nélkül.  
  - Egy IPv6-címtartomány a "kezdő cím-záró cím" formátumban, szóközök nélkül.  

- **Távoli címek**  
  **Alapértelmezett**: bármely címnek  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  Válassza ki **a kívánt címeket vagy a** **megadott címeket**.  

  Ha *megadott címet*használ, egy vagy több címet ad hozzá a szabály által érintett távoli címek vesszővel tagolt listájához. A tokenek nem kis-és nagybetűk. Az érvényes tokenek a következők:  
  - *Bármely* távoli címként használjon csillagot "*". Ha csillagot használ, az csak az Ön által használt token lehet.  
  - "Defaultgateway"  
  - DHCP-  
  - DNS  
  - WINS  
  - "Intranet" (a Windows 1809-es és újabb verzióiban támogatott)  
  - "RmtIntranet" (Windows 1809 és újabb verziók esetén támogatott)  
  - "Internet" (a Windows 1809-es és újabb verzióiban támogatott)  
  - "Ply2Renders" (Windows 1809 és újabb verziók esetén támogatott)  
  - A "LocalSubnet" kifejezés a helyi alhálózaton lévő helyi címeket jelöli.  
  - Alhálózat megadásához használja az alhálózati maszkot vagy a hálózati előtag jelölését. Ha nincs megadva alhálózati maszk és hálózati előtag, az alhálózati maszk alapértelmezett értéke 255.255.255.255.  
  - Érvényes IPv6-cím.  
  - Egy IPv4-címtartomány a "kezdő címe-záró címe" formátumban, szóközök nélkül.  
  - Egy IPv6-címtartomány a "kezdő cím-záró cím" formátumban, szóközök nélkül.  

#### <a name="port-and-protocol-settings"></a>Port és protokoll beállításai  
Itt adhatja meg azokat a helyi és távoli portokat, amelyekre ez a szabály vonatkozik.  

- **Protokoll**  
  **Alapértelmezett**: bármely  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  Válasszon az alábbiak közül, és végezze el az összes szükséges konfigurációt:  
  - **Összes** – nem érhető el további konfiguráció.  
  - **TCP** – helyi és távoli portok konfigurálása. Mindkét beállítás támogatja az összes portot vagy a megadott portokat. Vesszővel tagolt lista használatával adja meg a megadott portokat.  
    - **Helyi portok** – tűzfal CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Távoli portok** – tűzfal CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** – a helyi és a távoli portok konfigurálása. Mindkét beállítás támogatja az összes portot vagy a megadott portokat. Vesszővel tagolt lista használatával adja meg a megadott portokat.  
    - **Helyi portok** – tűzfal CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Távoli portok** – tűzfal CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **Custom (egyéni** ) – a 0 és 255 közötti egyéni **protokoll** -számot ad meg.  

#### <a name="advanced-configuration"></a>Speciális konfiguráció  
- **Illesztőfelület-típusok**  
  **Alapértelmezett**: 0 kiválasztva  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  Válasszon a következő lehetőségek közül:  
  - **Távelérés**  
  - **Szikratávíró**  
  - **Helyi hálózat**  

- **Kapcsolatok engedélyezése csak ezektől a felhasználóktól**  
  **Alapértelmezett**: az összes felhasználó *(alapértelmezés szerint az összes felhasználás, ha nincs megadva lista)*  
  Tűzfal CSP: [FirewallRules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  A szabályhoz tartozó helyi felhasználók listájának megadása. Nem lehet megadni a jogosultsággal rendelkező felhasználók listáját, ha ez a szabály egy Windows-szolgáltatásra vonatkozik.  


## <a name="windows-defender-smartscreen-settings"></a>A Windows Defender SmartScreen beállításai  
 
A Microsoft Edge-nek telepítve kell lennie az eszközön.  

- **SmartScreen alkalmazások és fájlok számára**  
  **Alapértelmezett**: nincs konfigurálva  
   SmartScreen CSP: [SmartScreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **Nincs konfigurálva** – letiltja a SmartScreen használatát.  
  - **Engedélyezés** – a Windows SmartScreen engedélyezése a fájlok végrehajtásához és az alkalmazások futtatásához. A SmartScreen egy felhőalapú, adathalászat elleni és kártevőirtó összetevő.  

- **Nem ellenőrzött fájlok végrehajtása**  
  **Alapértelmezett**: nincs konfigurálva  
   SmartScreen CSP: [SmartScreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **Nincs konfigurálva** – letiltja ezt a funkciót, és lehetővé teszi a végfelhasználók számára a nem ellenőrzött fájlok futtatását.  
  - **Letiltás** – megakadályozza, hogy a végfelhasználók futtassák a Windows SmartScreen által nem ellenőrzött fájlokat.  

## <a name="windows-encryption"></a>Windows-titkosítás  
 
### <a name="windows-settings"></a>Windowsos beállítások  

Ezek a titkosítási beállítások a Windows 10 összes verziójára érvényesek.  

- **Eszközök titkosítása**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [RequireDeviceEncryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **Megkövetelt** – a felhasználóknak az eszközök titkosításának engedélyezését kell kérniük. A Windows kiadásától és a rendszerkonfigurációtól függően a rendszer a következőket kérheti a felhasználóktól:  
    - Annak megerősítéséhez, hogy egy másik szolgáltatótól származó titkosítás nincs engedélyezve.  
    - Szükség van a BitLocker meghajtótitkosítás kikapcsolására, majd a BitLocker újbóli bekapcsolására.  
  - **Nincs konfigurálva**  
  
  Az eszköz ugyanis instabillá válhat, ha a windowsos titkosítást úgy kapcsolják be, hogy közben egy másik titkosítási módszer aktív marad.  

- **Storage-kártya titkosítása (csak mobil)**  
  *Ez a beállítás csak a Windows 10 Mobile rendszerre vonatkozik.*  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - Az eszköz által használt cserélhető tárolók titkosításának **megkövetelése** .  
  - **Nincs konfigurálva** – nincs szükség a Storage Card encryption használatára, és nem kéri a felhasználót, hogy kapcsolja be.  

### <a name="bitlocker-base-settings"></a>BitLocker-alapbeállítások  

Az alapbeállítások minden típusú adatmeghajtóra vonatkozó univerzális BitLocker-beállítások. Ezek a beállítások szabályozzák a végfelhasználók által a különböző típusú adatmeghajtókon módosítható meghajtótitkosítási feladatokat vagy konfigurációs beállításokat.  

- **Figyelmeztetés más lemezes titkosításhoz**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **Letiltás** – a figyelmeztető üzenet letiltása, ha egy másik lemez-titkosítási szolgáltatás van az eszközön.  
  - **Nincs konfigurálva** – engedélyezze a figyelmeztetést más lemezes titkosítás megjelenítéséhez.  

  Ha a *blokkolás*értékre van állítva, akkor a következő beállítást állíthatja be:  

  - **Titkosítás engedélyezése az általános jogú felhasználók számára az Azure AD JOIN szolgáltatásban**  
    *Ez a beállítás csak Azure Active Directory csatlakoztatott (Azure ADJ) eszközökre vonatkozik, és az előző, `Warning for other disk encryption` beállítástól függ.*  
    **Alapértelmezett**: nincs konfigurálva  
    BitLocker CSP: [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **Engedélyezés** – az általános jogú felhasználók (nem rendszergazdák) engedélyezhetik a BitLocker titkosítást a bejelentkezéskor.  
     - **Nincs konfigurálva** , csak a rendszergazdák engedélyezhetik a BitLocker titkosítást az eszközön.  

- **Titkosítási módszerek konfigurálása**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **Engedélyezés** – titkosítási algoritmusok konfigurálása az operációs rendszer, az adattároló és a cserélhető meghajtók számára.  
  - **Nincs konfigurálva** – a BITLOCKER az XTS-AES 128 bitet használja alapértelmezett titkosítási módszerként, vagy pedig a telepítési parancsfájl által megadott titkosítási módszert használja.  

  Az *Engedélyezés*beállításnál a következő beállításokat állíthatja be:  

  - **Operációs rendszer-meghajtók titkosítása**  
    **Alapértelmezett**: XTS-AES 128-bit  
   
    Válassza ki az operációs rendszer meghajtók titkosítási módszerét. Javasoljuk az XTS-AES algoritmus használatát.  
    - **AES – CBC 128 bites**  
    - **AES – CBC 256 bites**  
    - **XTS-AES 128 bites**  
    - **XTS-AES 256 bites**  

  - **Rögzített adatmeghajtók titkosítása**  
    **Alapértelmezett**: AES-CBC 128-bit  
   
    Válassza ki a rögzített (beépített) adatmeghajtók titkosítási módszerét. Javasoljuk az XTS-AES algoritmus használatát.  
    - **AES – CBC 128 bites**  
    - **AES – CBC 256 bites**  
    - **XTS-AES 128 bites**  
    - **XTS-AES 256 bites**  

  - **Cserélhető adatmeghajtók titkosítása**  
    **Alapértelmezett**: AES-CBC 128-bit  

    Válassza ki a cserélhető adatmeghajtók titkosítási módszerét. Ha a cserélhető meghajtót olyan eszközökkel is használja, amelyeken nem Windows 10 operációs rendszer fut, az AES-CBC algoritmus használatát javasoljuk.  
    - **AES – CBC 128 bites**  
    - **AES – CBC 256 bites**  
    - **XTS-AES 128 bites**  
    - **XTS-AES 256 bites**  

### <a name="bitlocker-os-drive-settings"></a>Operációsrendszer-meghajtók BitLocker-beállításai  

Ezek a beállítások kifejezetten az operációsrendszer-adatmeghajtókra érvényesek.  

- **További hitelesítés indításkor**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **Szükséges** – konfigurálja a számítógép indításának hitelesítési követelményeit, beleértve a PLATFORMMEGBÍZHATÓSÁGI modul (TPM) használatát.  
  - **Nincs konfigurálva** – csak az alapszintű beállításokat konfigurálja TPM-sel rendelkező eszközökön.  

  A *kötelező*beállításhoz a következő beállításokat állíthatja be:  

  - **BitLocker nem kompatibilis TPM-lapkával**  
    **Alapértelmezett**: nincs konfigurálva  

    - **Letiltás – a** BitLocker használatának letiltása, ha egy eszközön nincs kompatibilis TPM-lapka.  
    - **Nincs konfigurálva** – a felhasználók a BitLockert kompatibilis TPM-lapka nélkül is használhatják. A BitLockerhez jelszóra vagy indítókulcsra lehet szüksége.  

  - **Kompatibilis TPM-indítás**  
    **Alapértelmezett**: TPM engedélyezése  

    Annak konfigurálása, hogy a TPM engedélyezett, kötelező vagy nem engedélyezett.  

    - **TPM engedélyezése**  
    - **TPM letiltása**  
    - **TPM megkövetelése**  

  - **Kompatibilis TPM-indítási PIN-kód**  
    **Alapértelmezett**: indítási PIN-kód engedélyezése a TPM-sel  

    A TPM-lapka indítási PIN-kódjának használatával engedélyezheti, nem engedélyezheti vagy megkövetelheti a használatát. Indítási PIN-kód engedélyezéséhez végfelhasználói beavatkozás szükséges.  

    - **Indítási PIN-kód engedélyezése a TPM-sel**  
    - **Indítási PIN-kód tiltása a TPM-sel**  
    - **Indítási PIN-kód megkövetelése a TPM-sel**

  - **Kompatibilis TPM-indítási kulcs**  
    **Alapértelmezett**: indítási kulcs engedélyezése a TPM-sel  

    A TPM-lapka használatával engedélyezheti, nem engedélyezheti vagy megkövetelheti az indítási kulcs használatát. Indítókulcs engedélyezéséhez végfelhasználói beavatkozás szükséges.  

    - **Indítási kulcs engedélyezése a TPM-sel**  
    - **Indítási kulcs letiltása a TPM-sel**  
    - **Indítási kulcs megkövetelése a TPM-sel**  

  - **Kompatibilis TPM-indítási kulcs és PIN-kód**  
    **Alapértelmezett**: indítási kulcs és PIN-kód engedélyezése a TPM-sel  

    A TPM-lapka használatával engedélyezheti, nem engedélyezheti vagy megkövetelheti az indítási kulcs használatát és a PIN-kódot. Indítókulcs és indítási PIN-kód engedélyezéséhez végfelhasználói beavatkozás szükséges.  
    - **Indítási kulcs és PIN-kód engedélyezése a TPM-sel**  
    - **Indítási kulcs és PIN-kód tiltása a TPM-sel**  
    - **Indítási kulcs és PIN-kód megkövetelése a TPM-sel**   

- **PIN-kód minimális hossza**  
    **Alapértelmezett**: nincs konfigurálva  
    BitLocker CSP: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **Engedélyezés** Állítsa be a TPM-indítási PIN-kód minimális hosszát.  
    - **Nincs konfigurálva** – a felhasználók tetszőleges hosszúságú indítási PIN-kódot állíthatnak be 6 és 20 számjegy között.  

  Az *Engedélyezés*beállításnál a következő beállítást állíthatja be:  

  - **Minimális karakterek**  
    **Alapértelmezett**: *nincs KONFIGURÁLVA* a BitLocker CSP: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    Adja meg az indítási PIN-kódhoz szükséges karakterek számát **4**-**20**értékkel.  

- **OPERÁCIÓSRENDSZER-meghajtó helyreállítása**  
  **Alapértelmezett**: nincs konfigurálva   
  BitLocker CSP: [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **Engedélyezés** – a BitLocker által védett operációsrendszer-meghajtók helyreállításának szabályozása, ha a szükséges indítási információk nem érhetők el.  
  - **Nincs konfigurálva** – a BitLocker helyreállításhoz az alapértelmezett helyreállítási beállítások támogatottak. Alapértelmezés szerint a DRA engedélyezett, a helyreállítási beállításokat a felhasználó választja ki, beleértve a helyreállítási jelszót és a helyreállítási kulcsot, és a helyreállítási adatokat nem biztonsági másolat készül a AD DS.  

  Az *Engedélyezés*beállításnál a következő beállításokat állíthatja be:  

  - **Tanúsítvány alapú adathelyreállítási ügynök**  
    **Alapértelmezett**: nincs konfigurálva  
     
    - **Letiltás** – megakadályozza az adathelyreállítási ügynök használatát a BitLocker által védett operációsrendszer-meghajtók használatával.  
    - **Nincs konfigurálva** – engedélyezi, hogy a rendszer az adathelyreállítási ügynököket a BitLocker által védett operációsrendszer-meghajtókon használja.  

  - **Helyreállítási jelszó felhasználói létrehozása**  
    **Alapértelmezett**: 48 számjegyű helyreállítási jelszó engedélyezése  

    Válassza ki, hogy a felhasználók számára engedélyezett, kötelező vagy nem engedélyezett-e a 48 számjegyű helyreállítási jelszó létrehozása.  
    - **48 számjegyű helyreállítási jelszó engedélyezése**  
    - **Ne engedélyezze a 48 számjegyű helyreállítási jelszót**  
    - **48 számjegyű helyreállítási jelszó megkövetelése**  

  - **Helyreállítási kulcs felhasználói létrehozása**  
    **Alapértelmezett**: 256 bites helyreállítási kulcs engedélyezése  

    Válassza ki, hogy a felhasználók számára engedélyezett, kötelező vagy nem engedélyezett-e a 256 bites helyreállítási kulcs létrehozása.  
    - **256 bites helyreállítási kulcs engedélyezése**  
    - **Ne engedélyezze a 256 bites helyreállítási kulcsot**  
    - **256 bites helyreállítási kulcs megkövetelése**  

  - **Helyreállítási beállítások a BitLocker telepítővarázsló varázslóban**  
    **Alapértelmezett**: nincs konfigurálva  

    - **Letiltás** – a felhasználók nem látják és nem módosíthatják a helyreállítási beállításokat. Ha be van állítva 
    - **Nincs konfigurálva** – a felhasználók a BitLocker bekapcsolásakor megtekinthetik és módosíthatják a helyreállítási beállításokat. 
 
  - **A BitLocker helyreállítási adatainak mentése a Azure Active Directoryba**  
    **Alapértelmezett**: nincs konfigurálva  

    - **Engedélyezés** – a BitLocker helyreállítási információinak tárolása Azure Active Directoryba (Azure ad).  
    - **Nincs konfigurálva** – a BitLocker helyreállítási információit a rendszer nem TÁROLJA a HRE.  

  - **A BitLocker Azure Active Directory tárolt helyreállítási információi**  
    **Alapértelmezett**: a helyreállítási jelszavak és a kulcscsomagok biztonsági mentése  

    Annak konfigurálása, hogy a BitLocker helyreállítási információinak mely részei legyenek tárolva az Azure AD-ben. A következő lehetőségek közül választhat:  
    - **A helyreállítási jelszavak és a kulcscsomagok biztonsági mentése**  
    - **Csak a helyreállítási jelszavak biztonsági mentése**  

  - **Ügyfél által vezérelt helyreállítási jelszó elforgatása**  
    **Alapértelmezett**: az Azure ad-hez csatlakoztatott eszközökhöz engedélyezett a kulcs elforgatása  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Ez a beállítás az operációsrendszer-meghajtó helyreállítása után kezdeményezi az ügyfél által vezérelt helyreállítási jelszavak rotációját (a Csizmadia vagy a WinRE használatával).  

    - Nincs konfigurálva  
    - Kulcs elforgatása letiltva  
    - Az Azure AD-hez csatlakoztatott elforgatási sebesség engedélyezve  
    - Az Azure AD-hez és a hibridhez csatlakoztatott eszközökhöz engedélyezve van a kulcs elforgatása  

  - **A helyreállítási információk tárolása Azure Active Directory a BitLocker engedélyezése előtt**  
    **Alapértelmezett**: nincs konfigurálva  
 
     Annak megakadályozása, hogy a felhasználók engedélyezzék a BitLocker engedélyezését, kivéve, ha a számítógép sikeresen biztonsági másolatot készít a BitLocker helyreállítási adatairól Azure Active Directory.  

    - **Megkövetelés** – a felhasználók csak akkor kapcsoljuk be a BitLockert, ha a BitLocker helyreállítási adatokat nem sikerült az Azure ad-ben tárolni.  
    - **Nincs konfigurálva** – a felhasználók akkor is bekapcsolhatják a BitLockert, ha a helyreállítási adatok tárolása nem sikerült az Azure ad-ben.  

- **Rendszerindítás előtti helyreállítási üzenet és URL-cím**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **Engedélyezés** – konfigurálja a rendszerindítás előtti kulcs-helyreállítási képernyőn megjelenő üzenetet és URL-címet.  
  - **Nincs konfigurálva** – tiltsa le ezt a funkciót.  
  
  Az *Engedélyezés*beállításnál a következő beállítást állíthatja be:  
  - **Rendszerindítás előtti helyreállítási üzenet**  
    **Alapértelmezett**: az alapértelmezett helyreállítási üzenet és URL-cím használata   
 
    Beállíthatja, hogy a rendszerindítás előtti helyreállítási üzenet hogyan jelenjen meg a felhasználók számára. A következő lehetőségek közül választhat:  
    - **Az alapértelmezett helyreállítási üzenet és URL-cím használata**  
    - **Üres helyreállítási üzenet és URL-cím használata**  
    - **Egyéni helyreállítási üzenet**  
    - **Egyéni helyreállítási URL**  

### <a name="bitlocker-fixed-data-drive-settings"></a>Rögzített adatmeghajtók BitLocker-beállításai  

Ezek a beállítások kifejezetten a rögzített adatmeghajtókra érvényesek.  

- **Írási hozzáférés a BitLocker által nem védett rögzített adatmeghajtóhoz**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **Letiltás** – csak olvasási hozzáférést adhat a BitLocker által nem védett adatmeghajtókhoz.  
  - **Nincs konfigurálva** – alapértelmezés szerint nem titkosított adatmeghajtók olvasási és írási hozzáférése.  

- **Rögzített meghajtó helyreállítása**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **Engedélyezés** – a BitLocker által védett rögzített meghajtók helyreállításának szabályozása, ha a szükséges indítási információk nem érhetők el.  
  - **Nincs konfigurálva** – tiltsa le ezt a funkciót.  

  Az *Engedélyezés*beállításnál a következő beállításokat állíthatja be:  

  - **Az adathelyreállítási ügynök**  
    **Alapértelmezett**: nincs konfigurálva  
 
    - **Letiltás** – megakadályozza az adathelyreállítási ügynök használatát a BitLocker által védett rögzített meghajtók házirend-szerkesztőjével. 
    - **Nincs konfigurálva** – engedélyezi az adathelyreállítási ügynökök használatát a BitLocker által védett rögzített meghajtók használatával.  

  - **Helyreállítási jelszó felhasználói létrehozása**  
    **Alapértelmezett**: 48 számjegyű helyreállítási jelszó engedélyezése  

    Válassza ki, hogy a felhasználók számára engedélyezett, kötelező vagy nem engedélyezett-e a 48 számjegyű helyreállítási jelszó létrehozása.  
    - **48 számjegyű helyreállítási jelszó engedélyezése**  
    - **Ne engedélyezze a 48 számjegyű helyreállítási jelszót**  
    - **48 számjegyű helyreállítási jelszó megkövetelése**  

  - **Helyreállítási kulcs felhasználói létrehozása**  
    **Alapértelmezett**: 256 bites helyreállítási kulcs engedélyezése

    Válassza ki, hogy a felhasználók számára engedélyezett, kötelező vagy nem engedélyezett-e a 256 bites helyreállítási kulcs létrehozása.
    - **256 bites helyreállítási kulcs engedélyezése**  
    - **Ne engedélyezze a 256 bites helyreállítási kulcsot**  
    - **256 bites helyreállítási kulcs megkövetelése**  

  - **Helyreállítási beállítások a BitLocker telepítővarázsló varázslóban**  
    **Alapértelmezett**: nincs konfigurálva  

    - **Letiltás** – a felhasználók nem látják és nem módosíthatják a helyreállítási beállításokat. Ha be van állítva 
    - **Nincs konfigurálva** – a felhasználók a BitLocker bekapcsolásakor megtekinthetik és módosíthatják a helyreállítási beállításokat.
 
  - **A BitLocker helyreállítási adatainak mentése a Azure Active Directoryba**  
    **Alapértelmezett**: nincs konfigurálva  

    - **Engedélyezés** – a BitLocker helyreállítási információinak tárolása Azure Active Directoryba (Azure ad).  
    - **Nincs konfigurálva** – a BitLocker helyreállítási információit a rendszer nem TÁROLJA a HRE.

  - **A BitLocker Azure Active Directory tárolt helyreállítási információi**  
    **Alapértelmezett**: a helyreállítási jelszavak és a kulcscsomagok biztonsági mentése  

    Annak konfigurálása, hogy a BitLocker helyreállítási információinak mely részei legyenek tárolva az Azure AD-ben. A következő lehetőségek közül választhat:  
    - **A helyreállítási jelszavak és a kulcscsomagok biztonsági mentése**  
    - **Csak a helyreállítási jelszavak biztonsági mentése**  

  - **Ügyfél által vezérelt helyreállítási jelszó elforgatása**  
    **Alapértelmezett**: az Azure ad-hez csatlakoztatott eszközökhöz engedélyezett a kulcs elforgatása  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Ez a beállítás az operációsrendszer-meghajtó helyreállítása után kezdeményezi az ügyfél által vezérelt helyreállítási jelszavak rotációját (a Csizmadia vagy a WinRE használatával).  

    - Nincs konfigurálva  
    - Kulcs elforgatása letiltva  
    - Az Azure AD-hez csatlakoztatott elforgatási sebesség engedélyezve  
    - Az Azure AD-hez és a hibridhez csatlakoztatott eszközökhöz engedélyezve van a kulcs elforgatása  

  - **A helyreállítási információk tárolása Azure Active Directory a BitLocker engedélyezése előtt**  
    **Alapértelmezett**: nincs konfigurálva  
 
    Annak megakadályozása, hogy a felhasználók engedélyezzék a BitLocker engedélyezését, kivéve, ha a számítógép sikeresen biztonsági másolatot készít a BitLocker helyreállítási adatairól Azure Active Directory.  

    - **Megkövetelés** – a felhasználók csak akkor kapcsoljuk be a BitLockert, ha a BitLocker helyreállítási adatokat nem sikerült az Azure ad-ben tárolni.  
    - **Nincs konfigurálva** – a felhasználók akkor is bekapcsolhatják a BitLockert, ha a helyreállítási adatok tárolása nem sikerült az Azure ad-ben.  

### <a name="bitlocker-removable-data-drive-settings"></a>Cserélhető adatmeghajtók BitLocker-beállításai  

Ezek a beállítások kifejezetten a cserélhető adatmeghajtókra érvényesek.  

- **Írási hozzáférés a BitLocker által nem védett cserélhető adatmeghajtóhoz**  
  **Alapértelmezett**: nincs konfigurálva  
  BitLocker CSP: [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **Letiltás** – csak olvasási hozzáférést adhat a BitLocker által nem védett adatmeghajtókhoz.  
  - **Nincs konfigurálva** – alapértelmezés szerint nem titkosított adatmeghajtók olvasási és írási hozzáférése.  

  Az *Engedélyezés*beállításnál a következő beállítást állíthatja be:  

  - **Írási hozzáférés más szervezetben konfigurált eszközökhöz**  
    **Alapértelmezett**: nincs konfigurálva  

    - Az írási **hozzáférés letiltása más** szervezetekben konfigurált eszközökhöz.  
    - **Nincs konfigurálva** – írási hozzáférés megtagadása.  
 
## <a name="windows-defender-exploit-guard"></a>Windows Defender – biztonsági rés kiaknázása elleni védelem  

A [védelem kiaknázásával](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) kezelheti és csökkentheti az alkalmazottak által használt alkalmazások támadási felületét.  

### <a name="attack-surface-reduction"></a>Támadási felület csökkentése  

A támadási felület csökkentési szabályai segítenek megakadályozni, hogy a kártevő szoftvereket gyakran használják a kártékony kóddal rendelkező számítógépek megfertőzésére.  

#### <a name="attack-surface-reduction-rules"></a>Támadási felület csökkentésére vonatkozó szabályok  

- **A Windows helyi biztonsági szervezet alrendszeréből történő hitelesítő adatok lopásának megjelölése**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [a Windows helyi biztonsági szervezet alrendszerének (LSASS. exe) által ellopott hitelesítő adatok letiltása](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  Segít megelőzni azokat a műveleteket és alkalmazásokat, amelyeket általában a kártevők elleni támadással a gépek megfertőzésére használnak.  

  - **Nincs konfigurálva**  
  - **Engedélyezheti** a hitelesítő adatok ellopását a Windows helyi biztonsági szervezet alrendszeréről (LSASS. exe).  
  - **Csak naplózás**  

- **Folyamat létrehozása az Adobe Readerből (bétaverzió)**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [az Adobe Reader nem hozhat létre alárendelt folyamatokat](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **Nincs konfigurálva**  
  - **Engedélyezés** – az Adobe Readerből létrehozott alárendelt folyamatok letiltása.  
  - **Csak naplózás**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Veszélyes Office-makrók letiltására szolgáló szabályok  

Az alábbi műveletek elvégzését letilthatja Office-alkalmazások esetén:  

- **Office-alkalmazások más folyamatokba való injektálása (nincs kivétel)**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [az Office-alkalmazások más folyamatokba való behelyezésének tiltása](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - **Nincs konfigurálva**  
  - Az Office-alkalmazások más folyamatokba való beadásának **tiltása.**  
  - **Csak naplózás**  

- **Végrehajtható tartalmat létrehozó Office-alkalmazások és -makrók**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [az Office-alkalmazások nem hozhatnak létre végrehajtható tartalmat](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - **Nincs konfigurálva**  
  - Az Office-alkalmazások és-makrók **letiltásával** végrehajtható tartalom hozható létre.  
  - **Csak naplózás**  

- **Gyermekfolyamatokat elindító Office-alkalmazások**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: az [összes Office-alkalmazás alárendelt folyamatok létrehozásának tiltása](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **Nincs konfigurálva**  
  - **Letilthatja** , hogy az Office-alkalmazások alárendelt folyamatokat indítsanak.  
  - **Csak naplózás**  
  
- **Office-makró-kódból történő Win32-alapú importálás**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [Win32 API-hívások letiltása az Office-makrókban](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - **Nincs konfigurálva**  
  - **Blokkolja** a Win32-alapú importálások blokkolását az Office-ban.  
  - **Csak naplózás**  
  
- **Folyamat létrehozása Office-kommunikációs termékekből**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [az Office kommunikációs alkalmazás nem hozható létre alárendelt folyamatokból](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **Nincs konfigurálva**  
  - **Engedélyezés** – alárendelt folyamat létrehozásának tiltása az Office Communications-alkalmazásokból.  
  - **Csak naplózás**  

#### <a name="rules-to-prevent-script-threats"></a>Veszélyes szkriptek letiltására szolgáló szabályok  

Az alábbiak letiltásával a veszélyes szkriptek ellen védekezhet:  

- **Js-, VBS-, PS-fájlok és makrók rejtjelezett kódja**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [potenciálisan elhomályosított parancsfájlok végrehajtásának letiltása](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - **Nincs konfigurálva**  
  - **Letiltás** – blokkolt js/vbs/PS/Macro kód letiltása.  
  - **Csak naplózás**  

- **Internetről letöltött .js vagy .vbs fájlok végrehajtása (nincs kivétel)**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [blokkolja a JavaScript vagy a VBScript letöltött végrehajtható tartalom indítását](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - **Nincs konfigurálva**  
  - **Blokkolja** a JS/vbs blokkolását az internetről letöltött hasznos adatok végrehajtásához.  
  - **Csak naplózás**  

- **Folyamatlétrehozás a PSExec- és WMI-parancsokból**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [PSExec és WMI-parancsokból származó folyamat-létrehozás tiltása](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - **Nincs konfigurálva**  
  - A PSExec és a WMI-parancsokból származó folyamat-létrehozás **tiltása** .  
  
  - **Csak naplózás**  

- **Nem megbízható és aláíratlan, USB-ről futó folyamatok**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: nem [megbízható és aláíratlan, USB-ről futó folyamatok letiltása](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - **Nincs konfigurálva**  
  - A nem megbízható és aláíratlan, USB-ről futó **folyamatok blokkolása** .  
  - **Csak naplózás**  
  
- **Az elterjedtségre, korra és megbízható listákra vonatkozó kritériumoknak nem megfelelő végrehajtható fájlok**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [a végrehajtható fájlok futtatásának letiltása, kivéve, ha azok nem felelnek meg az előfordulási, az életkori vagy a megbízható lista feltételeinek](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - **Nincs konfigurálva**  
  - **Letiltja** a végrehajtható fájlok futtatását, kivéve, ha azok nem felelnek meg az előfordulási, az életkori vagy a megbízható lista feltételeinek.  
  - **Csak naplózás**  

#### <a name="rules-to-prevent-email-threats"></a>E-mail-fenyegetések megakadályozását szolgáló szabályok  

Az alábbiak letiltásával megakadályozhatja az e-mail-fenyegetéseket:  

- **Webes levelezés vagy az asztali levelezőprogramok e-mailjeiből eltávolított végrehajtható tartalom (például .exe, .dll, .ps, .js, és .vbs fájlok) futtatása (nincs kivétel)**  
  **Alapértelmezett**: nincs konfigurálva  
  Szabály: [végrehajtható tartalom letiltása az e-mail-ügyfélprogramból és webmailből](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - **Nincs konfigurálva**  
  - Az e-mailből (webmail/mail-Client) eldobott végrehajtható tartalom **letiltása** (exe, dll, PS, js, vbs stb.).  
  - **Csak naplózás**  

#### <a name="rules-to-protect-against-ransomware"></a>Zsarolóprogramok elleni szabályok  

- **Zsarolóprogramok elleni speciális védelem**  
  Alapértelmezett: nincs konfigurálva  
  Szabály: [Speciális védelem használata a ransomware](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware) -on  

  - **Nincs konfigurálva**  
  - **Engedélyezés** – agresszív ransomware-védelem használata.  
  - **Csak naplózás**  

#### <a name="attack-surface-reduction-exceptions"></a>Támadási felület csökkentése – kivételek

- **A támadási felület csökkentési szabályaiból kizárandó fájlok és mappák**  
  Defender CSP: [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **Importáljon** egy. csv-fájlt, amely a támadási felület csökkentési szabályaiból kizárandó fájlokat és mappákat tartalmaz.  
  - Manuálisan **adja hozzá** a helyi fájlokat vagy mappákat.  

> [!IMPORTANT]  
> A LOB Win32-alkalmazások megfelelő telepítésének és végrehajtásának engedélyezéséhez a kártevők elleni beállításoknak ki kell zárnia a következő könyvtárakat a vizsgálatból:  
> **X64-es ügyfélszámítógépeken**:  
> *C:\Program Files (x86) \Microsoft Intune felügyeleti Extension\Content*  
> *C:\windows\IMECache*  
>  
> **X86-os ügyfélszámítógépeken**:  
> *C:\Program Files\Microsoft Intune felügyeleti Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>Mappahozzáférés felügyelete  

Segít megvédeni a kártékony alkalmazásokból és fenyegetésekből származó [értékes adatok](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) , például a ransomware.  

- **Mappák védelme**  
  **Alapértelmezett**: nincs konfigurálva  
  Defender CSP: [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  Fájlok és mappák védelme a nemkívánatos alkalmazások által végrehajtott, jogosulatlan módosítások ellen.  

  - **Nincs konfigurálva**  
  - **Engedélyezése**  
  - **Csak naplózás**  
  - **Lemez módosításának letiltása**  
  - **Lemez módosításának naplózása**  

  Ha *nem konfigurált*konfigurációt választ ki, akkor az alábbiakat állíthatja be:  
  - **A védett mappákhoz hozzáférő alkalmazások listája**  
    Defender CSP: [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **Importáljon** egy. csv-fájlt, amely tartalmazza az alkalmazások listáját.  
    - Manuálisan **adja hozzá** az alkalmazásokat a listához.  

  - **A védeni kívánt további mappák listája**  
    Defender CSP: [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **Importáljon** egy. csv kiterjesztésű fájlt, amely tartalmazza a mappalista listáját.  
    - Mappák **hozzáadása** a listához manuálisan.  

### <a name="network-filtering"></a>Hálózatszűrés  

Letiltja a kimenő kapcsolatokat bármely alkalmazásból az IP-címekre vagy-tartományokra alacsony hírnévvel. A hálózati szűrés mind a naplózási, mind a blokkolási módban támogatott.  

- **Hálózati védelem**  
  **Alapértelmezett**: nincs konfigurálva  
  Defender CSP: [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  Ennek a beállításnak a célja, hogy megvédje a végfelhasználókat az adathalászatgal kapcsolatos csalások, a kiaknázást biztosító webhelyek és az interneten található kártékony tartalmak hozzáférésével. Azt is megakadályozza, hogy a harmadik féltől származó böngészők csatlakozzanak a veszélyes helyekhez.  

  - **Nincs konfigurálva** – tiltsa le ezt a funkciót. A felhasználók és az alkalmazások nem blokkolják a veszélyes tartományokhoz való kapcsolódást. A rendszergazdák nem látják ezt a tevékenységet a Windows Defender Security Centerban.  
  - **Engedélyezze** a hálózati védelem bekapcsolását, és tiltsa le a felhasználókat és az alkalmazásokat a veszélyes tartományokhoz való csatlakozáshoz. A rendszergazdák láthatják ezt a tevékenységet a Windows Defender Security Centerban.  
  - **Csak naplózás**: – a felhasználók és az alkalmazások nem blokkolják a veszélyes tartományokhoz való kapcsolódást. A rendszergazdák láthatják ezt a tevékenységet a Windows Defender Security Centerban.  

### <a name="exploit-protection"></a>Biztonsági rés kiaknázása elleni védelem  
 

- **XML feltöltése**  
  **Alapértelmezett**: *nincs konfigurálva*  

  Ha a védelem kiaknázásával védelmet kíván biztosítani az [eszközöknek a](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)biztonsági rések ellen, hozzon létre egy XML-fájlt, amely tartalmazza a kívánt rendszer-és alkalmazás-kockázatcsökkentő beállításokat. Az XML-fájl létrehozása két módszerrel lehetséges:  

  - *PowerShell* – a *Get-ProcessMitigation*, a *set-ProcessMitigation*és a *ConvertTo-ProcessMitigationPolicy* PowerShell-parancsmagok közül egyet vagy többet használhat. A parancsmagokkal konfigurálhatja a kockázatcsökkentési beállításokat, és exportálhatja ezek XML-reprezentációját.  

  - *Windows defender Security Center felhasználói felület* – a windows Defender Security Center kattintson az App & Browser Control elemre, majd görgessen az eredményül kapott képernyő aljára, és keresse meg a kihasználatlan védelmet. Először a Rendszerbeállítások és a Programbeállítások lap használatával konfigurálja a kockázatcsökkentési beállításokat. Ha végzett, a képernyő alján keresse meg az Exportálási beállítások hivatkozást, amellyel exportálhatja ezek XML-reprezentációját.  

- **A védelem kiaknázása felület felhasználó általi szerkesztése**  
  **Alapértelmezett**: nincs konfigurálva  
  ExploitGuard CSP: [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **Blokk** – olyan XML-fájl feltöltése, amely lehetővé teszi a memória, a vezérlési folyamat és a házirendek korlátozásának konfigurálását. Az XML-fájlban található beállításokkal megvédheti az alkalmazást a biztonsági rések ellen.  
  - **Nincs konfigurálva** – egyéni konfiguráció nincs használatban.  

## <a name="windows-defender-application-control"></a>Windows Defender Alkalmazásvezérlés  

Válassza ki azokat a további alkalmazásokat, amelyeket naplózni kell, vagy megbízhatónak kell lennie a Windows Defender alkalmazás-vezérlő futtatásához. A Windows-összetevők és a Windows Áruházból származó alkalmazások automatikusan biztonságosan futtathatóként lesznek besorolva.  


- **Alkalmazás-felügyeleti kód integritási házirendjei**  
  **Alapértelmezett**: nincs konfigurálva  
   CSP: [APPLOCKER CSP](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **Kikényszerítés** – válassza ki az Application Control Code-integritási szabályzatokat a felhasználói eszközökhöz.  
  
    Az eszközön való engedélyezés után az alkalmazás-vezérlő csak akkor tiltható le, ha a mód *kényszerített* állapotból *csak naplózásra*vált. Ha a módot *Kényszerítésről* *Nincs konfigurálva* értékre változtatja, akkor az Alkalmazásvezérlés a hozzárendelt eszközökön továbbra is kényszerítve lesz.  

  - **Nincs konfigurálva** – az alkalmazás vezérlő nincs hozzáadva az eszközökhöz. A korábban hozzáadott beállítások azonban továbbra is érvényben lesznek a hozzárendelt eszközökön. 
 
  - **Csak naplózás** – az alkalmazások nincsenek letiltva. Az összes esemény a helyi ügyfél naplóiban van naplózva.  

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard  

A Windows Defender Credential Guard a hitelesítő adatok ellopása ellen nyújt védelmet. Úgy különíti el a titkos kulcsokat, hogy csak a jogosult rendszerszoftverek férjenek hozzájuk.  

- **Hitelesítőadat-őr**  
  **Alapértelmezett**: letiltás  
  [DeviceGuard CSP](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **Tiltsa le** a hitelesítő adatok távoli kikapcsolását, ha azt korábban már bekapcsolta az **UEFI Lock nélkül engedélyezve** beállítással.  

  - **Az UEFI Lock** -hitelesítőadat-őr használatának engedélyezése nem tiltható le távolról egy beállításkulcs vagy csoportházirend használatával.  

    > [!NOTE]
    > Ha ezt a beállítást használja, majd később le szeretné tiltani a Credential Guardot, a csoportházirendet **letiltott** állapotra kell állítania, majd törölnie kell az UEFI-konfigurációs adatokat minden számítógépről. Amíg megvannak a UEFI-konfigurációk, a Credential Guard engedélyezve marad.  

  - **Engedélyezés UEFI zárolás nélkül** – lehetővé teszi a hitelesítő adatok távoli letiltását csoportházirend használatával. Azokon az eszközökön, amelyek ezt a beállítást használják, a Windows 10 1511-es vagy újabb verziójának kell futnia.  

  A hitelesítőadat-őr *engedélyezésekor* a következő szükséges szolgáltatások is engedélyezve vannak:  
  
  - **Virtualizálás-alapú biztonság** (vbs)  
    A következő újraindításkor bekapcsol. A virtualizálás-alapú biztonság a Windows hipervizorral nyújt támogatást biztonsági szolgáltatásokhoz.  
  - **Biztonságos rendszerindítás a címtár memóriájának elérésével**  
    Bekapcsolja a VBS-et a biztonságos rendszerindítási és a közvetlen memória-hozzáférés (DMA) elleni védelemmel. A DMA-védelemhez hardveres támogatás szükséges, és csak a megfelelően konfigurált eszközökön alkalmazható.  

## <a name="windows-defender-security-center"></a>Windows Defender biztonsági központ  

A Windows Defender biztonsági központ az egyes funkcióktól elkülönített alkalmazásként működik. Az értesítéseket a Műveletközponton keresztül jeleníti meg. Gyűjtőként vagy egyetlen helyen működik az állapot megtekintéséhez és az egyes funkciókhoz tartozó konfiguráció futtatásához. További információt a [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) dokumentációjában talál.  

### <a name="windows-defender-security-center-app-and-notifications"></a>A Windows Defender biztonsági központ alkalmazás és az értesítések  

Letilthatja a felhasználói hozzáférést a Windows Defender biztonsági központ alkalmazás különböző területeihez. Egy szakasz elrejtése a kapcsolódó értesítéseket is letiltja.  

- **Vírusok és veszélyforrások elleni védelem**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e a vírus-és veszélyforrások elleni védelem területén a Windows Defender Security Center. A szakasz elrejtésével a vírus-és veszélyforrások elleni védelemmel kapcsolatos összes értesítés is blokkolva lesz.  

  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Ransomware-védelem**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e a Windows Defender Security Center ransomware-védelmi felületét. A szakasz elrejtésével a ransomware-védelemmel kapcsolatos összes értesítés is blokkolva lesz.  

  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Fiókok védelme**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e a Windows Defender Security Center fiók védelme területén. A szakasz elrejtésével a fiókok védelmével kapcsolatos összes értesítés is blokkolva lesz.  

  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Tűzfal és hálózatvédelem**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e a tűzfal és a hálózat védelmét a Windows Defender biztonsági központban. A szakasz elrejtésével a tűzfal és a hálózat védelmével kapcsolatos összes értesítés is blokkolva lesz.  

  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Alkalmazás-és böngésző-vezérlő**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableAppBrowserUI](https://go.microsoft.com/fwlink/?linkid=873669)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e az alkalmazás és a böngésző vezérlőelem területén a Windows Defender biztonsági központban. A szakasz elrejtésével az alkalmazás-és böngésző-vezérlőkkel kapcsolatos összes értesítés is blokkolva lesz.  

  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Hardveres védelem**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e a Windows Defender Security Center a hardveres védelem részét. A szakasz elrejtésével a hardveres védelemmel kapcsolatos összes értesítés is blokkolva lesz.  

  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Eszközteljesítmény és -állapot**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e az eszköz teljesítményét és állapotát a Windows Defender biztonsági központban. A szakasz elrejtésével az eszköz teljesítményével és állapotával kapcsolatos összes értesítés is blokkolva lesz.  
  
  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Családi beállítások**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  Annak megadása, hogy a végfelhasználók megtekinthetik-e a család beállításait a Windows Defender biztonsági központban. A szakasz elrejtésével az összes, a családra vonatkozó beállítással kapcsolatos értesítés is blokkolva lesz.  
  
  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Az alkalmazás megjelenített területeinek értesítései**  
  **Alapértelmezett**: nincs konfigurálva  
  WindowsDefenderSecurityCenter CSP: [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  Válassza ki, hogy mely értesítések jelenjenek meg a végfelhasználók számára. A nem kritikus értesítések közé tartoznak a Windows Defender víruskereső összefoglalói, például a vizsgálatok befejezését jelző értesítések. Minden más értesítés kritikusnak minősül.  

  - **Nincs konfigurálva**  
  - **Nem kritikus értesítések letiltása**  
  - **Az összes értesítés letiltása**  

- **Windows Security Center ikon a tálcán**  
  **Alapértelmezett**: nincs konfigurálva  

  Az értesítési terület vezérlőelem megjelenítésének konfigurálása. A felhasználónak ki kell jelentkeznie, majd be kell jelentkeznie, vagy újra kell indítania a számítógépet a beállítás érvénybe léptetéséhez.  
  
  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **TPM gomb törlése**  
  **Alapértelmezett**: nincs konfigurálva  

  Konfigurálja a TPM törlése gomb megjelenítését.  
  
  - **Nincs konfigurálva**  
  - **Megbénít**  

- **Figyelmeztetés a TPM belső vezérlőprogram frissítésére**  
  **Alapértelmezett**: nincs konfigurálva  
  
  Konfigurálja a TPM belső vezérlőprogram frissítésének megjelenítését sebezhető belső vezérlőprogram észlelésekor.  

  - **Nincs konfigurálva**  
  - **Elrejtése**  

- **Illetéktelen védelem**  
  **Alapértelmezett**: nincs konfigurálva

  Az eszközökön be-és kikapcsolhatja a jogosulatlan védelmet. A jogosulatlan védelem használatához [integrálnia kell a Microsoft Defender komplex veszélyforrások elleni védelmet az Intune](advanced-threat-protection.md)-nal, és [Enterprise Mobility + Security E5-licencekkel](../fundamentals/licenses.md)kell rendelkeznie.  
  - **Nincs konfigurálva** – az eszközbeállítások nem módosul.
  - Az **engedélyezett** – illetéktelen módosítások elleni védelem be van kapcsolva, és a korlátozások kényszerítve vannak az eszközökön.
  - **Letiltott** – az illetéktelen módosítások elleni védelem ki van kapcsolva, és a rendszer nem kényszeríti a korlátozásokat.

### <a name="it-contact-information"></a>Az informatikai szolgálat kapcsolattartási adatai  

Adja meg az informatikai szolgálat azon elérhetőségeit, amelyek megjelennek majd a Windows Defender biztonsági központ alkalmazásban és az alkalmazásértesítésekben.  

Az alábbi lehetőségek közül választhat: **Az alkalmazásban és az értesítésekben is jelenjen meg**, **Csak az alkalmazásban jelenjen meg**, **Csak az értesítésekben jelenjen meg** és **Ne jelenjen meg**. Adja meg az **IT-szervezet nevét**, és az alábbi kapcsolatfelvételi lehetőségek közül legalább egyet:  


- **Kapcsolattartási adatok**  
  **Alapértelmezett**: ne jelenjen meg  
  WindowsDefenderSecurityCenter CSP: [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  Itt adhatja meg, hogy hol jelenjen meg az informatikai kapcsolattartási adatok a végfelhasználók számára.  
  
  - **Megjelenítés az alkalmazásban és az értesítésekben**  
  - **Csak az alkalmazásban jelenjen meg**  
  - **Csak az értesítésekben jelenjen meg**  
  - **Ne jelenjen meg**  

  Ha a megjelenítésre van konfigurálva, a következő beállításokat állíthatja be:  

  - **INFORMATIKAI szervezet neve**  
    **Alapértelmezett**: *nincs konfigurálva*  
    WindowsDefenderSecurityCenter CSP: [Cégnév](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **IT-részleg telefonszáma vagy Skype-elérhetősége**  
    **Alapértelmezett**: *nincs konfigurálva*  
    WindowsDefenderSecurityCenter CSP: [telefon](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **IT-részleg e-mail címe**  
    **Alapértelmezett**: *nincs konfigurálva*  
    WindowsDefenderSecurityCenter CSP: [e-mail](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **Informatikai támogatási webhely URL-címe**  
    **Alapértelmezett**: *nincs konfigurálva*  
    WindowsDefenderSecurityCenter CSP: [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>Helyi eszközbiztonsági beállítások  

Ezekkel a beállításokkal konfigurálhatja a Windows 10-eszközök helyi biztonsági beállításait.  

### <a name="accounts"></a>Fiókok  

- **Új Microsoft-fiókok hozzáadása**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **Letiltás** Annak megakadályozása, hogy a felhasználók új Microsoft-fiókokat adjanak hozzá az eszközhöz.  
  - **Nincs konfigurálva** – a felhasználók Microsoft-fiókokat használhatnak az eszközön.  

- **Távoli bejelentkezés jelszó nélkül**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **Letiltás** – csak az üres jelszavakkal rendelkező helyi fiókok bejelentkezésének engedélyezése az eszköz billentyűzetén keresztül.  
   - **Nincs konfigurálva** – engedélyezi a helyi fiókok számára az üres jelszavakat a fizikai eszköztől eltérő helyről való bejelentkezéshez.  

#### <a name="admin"></a>Felügyelet  

- **Helyi rendszergazdai fiók**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **Letiltás** Helyi rendszergazdai fiók használatának megakadályozása.  
  - **Nincs konfigurálva**  

- **Rendszergazdai fiók átnevezése**  
  **Alapértelmezett**: *nincs konfigurálva*  
  LocalPoliciesSecurityOptions CSP: [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  Adjon meg egy másik fióknevet, amely társítva lesz a "rendszergazda" fiók biztonsági azonosítójához (SID).  

 #### <a name="guest"></a>Vendég  

- **Vendég fiók**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **Letiltás** – vendég fiók használatának megakadályozása.  
  - **Nincs konfigurálva**  

- **Vendég fiók átnevezése**  
  **Alapértelmezett**: *nincs konfigurálva*  
  LocalPoliciesSecurityOptions CSP: [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  Adjon meg egy másik fióknevet, amely társítva lesz a "vendég" fiók biztonsági azonosítójához (SID).  

### <a name="devices"></a>Eszközök  

- **Eszköz dokkolásának feloldása bejelentkezés nélkül**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **Letiltás** – a felhasználók lenyomhatja a dokkolt hordozható eszköz fizikai kidobási gombját, hogy biztonságosan le tudja tiltani az eszköz dokkolását.  
  - **Nincs konfigurálva** – a felhasználónak be kell jelentkeznie az eszközre, és engedélyt kell kapnia az eszköz dokkolásának feloldására.  

- **Nyomtató-illesztőprogramok telepítése megosztott nyomtatókhoz**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **Engedélyezve** – bármely felhasználó telepíthet egy nyomtatóillesztőt egy megosztott nyomtatóhoz való csatlakozás részeként.  
  - **Nincs konfigurálva** – csak rendszergazdák telepíthetnek nyomtatóillesztőt egy megosztott nyomtatóhoz való csatlakozás részeként.  

- **A CD-ROM-hozzáférés korlátozása helyi aktív felhasználóra**  
  **Alapértelmezett**: nincs konfigurálva  
  CSP: [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **Engedélyezve** – csak az interaktívan bejelentkezett felhasználó használhatja a CD-ROM-adathordozót. Ha a házirend engedélyezve van, és nincs interaktív módon bejelentkezett felhasználó, a CD-ROM-hoz a hálózaton keresztül lehet hozzáférni.  
  - **Nincs konfigurálva** – bárki HOZZÁFÉRHET a CD-ROM-hoz.  

- **Cserélhető adathordozó formázása és kiadása**  
  **Alapértelmezett**: rendszergazdák  
  CSP: [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  A cserélhető NTFS-adathordozók formázására és kiadására jogosult személyek megadása:  
  - **Nincs konfigurálva**  
  - **Rendszergazdák**  
  - **Rendszergazdák és kiemelt felhasználók**  
  - **Rendszergazdák és interaktív felhasználók**  

### <a name="interactive-logon"></a>Interaktív bejelentkezés  

- **A zárolási képernyő inaktivitásának percben, amíg a képernyőkímélő be nem kapcsol**  
  **Alapértelmezett**: *nincs konfigurálva*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  Adja meg az interaktív asztal bejelentkezési képernyőjének maximálisan ennyi perc inaktivitását, amíg a képernyővédő el nem indul. (**0**@no__t – 1**99999**)  

- **CTRL + ALT + DEL használatának megkövetelése a bejelentkezéshez**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **Engedélyezés** – a Ctrl + Alt + Del billentyűkombináció lenyomása nem kötelező a felhasználóknak a bejelentkezéshez.  
  - **Nincs konfigurálva** A CTRL + ALT + DEL billentyűkombináció lenyomásának megkövetelése a felhasználóktól a Windowsba való bejelentkezés előtt.  

- **Intelligens kártya eltávolításának viselkedése**  
  **Alapértelmezett**: munkaállomás zárolása   
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  Meghatározza, hogy mi történjen, ha a bejelentkezett felhasználó intelligens kártyáját eltávolítja az intelligenskártya-olvasóból. A választható lehetőségek:  

  - **Munkaállomás zárolása** – a munkaállomás az intelligens kártya eltávolításakor zárolva van. Ez a beállítás lehetővé teszi a felhasználóknak, hogy elhagyják a helyiséget, magukkal vigyék az intelligens kártyájukat, és továbbra is fenntartsák védett munkamenetüket.  
  - **Nincs művelet**  
  - **Kijelentkezés kényszerítése** – a rendszer automatikusan kijelentkezik a felhasználót az intelligens kártya eltávolításakor.  
  - **Kapcsolat bontása, ha távoli asztali szolgáltatások munkamenet** – az intelligens kártya eltávolítása leválasztja a munkamenetet a felhasználó kijelentkezése nélkül. Ez a beállítás lehetővé teszi, hogy a felhasználó az intelligens kártya újbóli beillesztésével később, vagy más intelligenskártya-olvasóval felszerelt gépnél újbóli bejelentkezés nélkül folytathassa a munkamenetet. Helyi munkamenet esetén ez a szabályzat pontosan úgy működik, mint a Munkaállomás zárolása.  

#### <a name="display"></a>Megjelenítés  

- **Felhasználói információk a zárolási képernyőn**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  A munkamenet zárolásakor megjelenő felhasználói adatok konfigurálása. Ha nincs konfigurálva, a felhasználó megjelenített neve, a tartomány és a felhasználónév látható.  

  - **Nincs konfigurálva**  
  - **Felhasználó megjelenített neve, tartomány- és felhasználónév**  
  - **Csak a felhasználó megjelenített neve**  
  - **Ne jelenjenek meg a felhasználói adatok**  

- **Utolsó bejelentkezett felhasználó elrejtése**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **Engedélyezés** – a Felhasználónév elrejtése.  
  - **Nincs konfigurálva** – az utolsó felhasználónevet jeleníti meg.  

- **Felhasználónév elrejtése a bejelentkezés**
  **alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **Engedélyezés** – a Felhasználónév elrejtése.  
  - **Nincs konfigurálva** – az utolsó felhasználónevet jeleníti meg.  

- **Bejelentkezési üzenet címe**  
  **Alapértelmezett**: *nincs konfigurálva*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  Adja meg az üzenet címét a bejelentkezett felhasználók számára.  

- **Bejelentkezési üzenet szövege**  
  **Alapértelmezett**: *nincs konfigurálva*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  Az üzenet szövegének beállítása a bejelentkezett felhasználók számára.  
  
### <a name="network-access-and-security"></a>Hálózati hozzáférés és biztonság

- **Névtelen hozzáférés nevesített csövekhez és megosztásokhoz**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **Nincs konfigurálva** – a névtelen hozzáférés korlátozása a megosztáshoz és a nevesített pipe-beállításokhoz. A névtelenül megadható beállításokra vonatkozik.  
  - **Tiltsa le** ezt a házirendet, így a névtelen hozzáférés elérhetővé válik.  

- **SAM-fiókok névtelen enumerálása**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **Nincs konfigurálva** – a névtelen felhasználók számba vehetik a SAM-fiókokat.  
  - **Block** – a SAM-fiókok névtelen számbavételének tiltása.  

- **SAM-fiókok és-megosztások névtelen enumerálása**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **Nincs konfigurálva** – a névtelen felhasználók számba vehetik a tartományi fiókok és hálózati megosztások nevét.  
  - **Blokk** – a SAM-fiókok és-megosztások névtelen számbavételének tiltása. 

- **A LAN Manager kivonatának jelszavas változáson tárolt értéke**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  Állapítsa meg, hogy a jelszó kivonatának értékét a rendszer a jelszó következő módosításakor tárolja-e. 
  - **Nincs konfigurálva** – a kivonatoló érték nincs tárolva  
  - **Letiltás** – a LAN-kezelő (LM) tárolja az új jelszó kivonatának értékét.  

- **PKU2U-hitelesítési kérelmek**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **Nincs konfigurálva**– PU2U kérelmek engedélyezése.  
  - **Blokkolja** a PKU2U hitelesítési kérelmeit az eszközön.  

- **Távoli RPC-kapcsolatok korlátozása a SAM-ra**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **Nincs konfigurálva** – használja az alapértelmezett biztonsági leírót, amely lehetővé teheti a felhasználók és csoportok számára, hogy távoli RPC-hívásokat hajtanak végre a SAM-ben.
  - **Engedélyezés** – megtagadhatja a felhasználókat és a csoportokat, hogy távoli RPC-hívásokat hozzanak a biztonsági FIÓKKEZELŐ (SAM) számára, amely a felhasználói fiókokat és jelszavakat tárolja. Az **Engedélyezés** beállítás megadásával megváltoztathatja az alapértelmezett biztonsági leíró definíciójának nyelvét (SDDL), hogy a felhasználók és csoportok explicit módon engedélyezzék vagy megtagadják ezeket a távoli hívásokat.  

    - **Biztonsági leíró**  
      **Alapértelmezett**: *nincs konfigurálva*  
    
- **Minimális munkamenet-biztonság az NTLM SSP-alapú ügyfelek számára**  
  **Alapértelmezett**: nincs  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  Ez a biztonsági beállítás lehetővé teszi a kiszolgáló számára, hogy megkövetelje a 128 bites titkosítás és/vagy az NTLMv2 munkamenet-biztonság egyeztetését.  

  - **Nincsenek**  
  - **NTLMv2-munkamenet biztonságának megkövetelése**  
  - **128 bites titkosítás megkövetelése**  
  - **NTLMv2 és 128 bites titkosítás**  
 
- **Az NTLM SSP-alapú kiszolgáló minimális munkamenet-biztonsága**  
  **Alapértelmezett**: nincs  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  Ez a biztonsági beállítás határozza meg, hogy melyik kérdés-válasz hitelesítési protokollt használja a rendszer a hálózati bejelentkezésekhez.  

  - **Nincsenek**  
  - **NTLMv2-munkamenet biztonságának megkövetelése**  
  - **128 bites titkosítás megkövetelése**  
  - **NTLMv2 és 128 bites titkosítás**  

- **A LAN-kezelő hitelesítési szintje**  
  **Alapértelmezett**: LM és NTLM  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM és NTLM**  
  - **LM, NTLM és NTLMv2**  
  - **NTLM**  
  - **NTLMv2**  
  - **NTLMv2 és nem LM**  
  - **NTLMv2 és nem LM vagy NTLM**  
  
- **Nem biztonságos vendég bejelentkezések**  
  **Alapértelmezett**: nincs konfigurálva  
  LanmanWorkstation CSP: [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  Ha engedélyezi ezt a beállítást, az SMB-ügyfél elutasítja a nem biztonságos vendég bejelentkezéseket.  

  - **Nincs konfigurálva**  
  - **Letiltás** – az SMB-ügyfél elutasítja a nem biztonságos vendég bejelentkezéseket.  

### <a name="recovery-console-and-shutdown"></a>Helyreállítási konzol és leállítás  

- **Virtuális memória lapozófájljának törlése leállításkor**  
  **Alapértelmezett**: nincs konfigurálva  
   LocalPoliciesSecurityOptions CSP: [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **Engedélyezés** – a virtuális memória lapozófájljának törlése, ha az eszköz le van kapcsolva.  
  - **Nincs konfigurálva** – nem törli a virtuális memóriát.  

- **Leállítás bejelentkezés nélkül**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **Letiltás** – a leállítási lehetőség elrejtése a Windows bejelentkezési képernyőjén. A felhasználóknak a leállítás előtt be kell jelentkezniük az eszközbe.  
  - **Nincs konfigurálva** – lehetővé teszi a felhasználók számára az eszköz leállítását a Windows bejelentkezési képernyőjéről.  

### <a name="user-account-control"></a>Felhasználói fiókok felügyelete  

- **UIA épsége biztonságos hely nélkül**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - A fájlrendszer biztonságos helyén lévő alkalmazások csak a UIAccess integritását fogják futtatni.  
  - **Nincs konfigurálva** – lehetővé teszi, hogy az alkalmazások az UIAccess integritásával fussanak, még akkor is, ha az alkalmazások nem biztonságos helyen vannak a fájlrendszerben.  

- **A fájl-és beállításjegyzék-írási hibák virtualizálása felhasználónkénti helyen**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **Engedélyezve** – nem sikerül az olyan alkalmazások, amelyek a védett helyszínekre írnak.  
  - **Nem konfigurált** – az alkalmazások írási hibáit a rendszer futási időben átirányítja a fájlrendszer és a beállításjegyzék meghatározott felhasználói helyeire.  

- **Csak az aláírt és érvényesített végrehajtható fájlok emelése**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **Engedélyezve** – a Futtatás előtt kényszerítse ki a PKI-tanúsítvány elérési útjának érvényesítését egy végrehajtható fájlra.  
  - **Nincs konfigurálva** – a rendszer nem kényszeríti ki a PKI-tanúsítványlánc érvényesítését egy végrehajtható fájl futtatása előtt.  

#### <a name="uia-elevation-prompt-behavior"></a>UIA jogosultságszint-emelési kérések viselkedése  

- **Jogosultságszint-emelési kérés rendszergazdák számára**  
  **Alapértelmezett**: beleegyezés kérése nem Windows rendszerű bináris fájlokhoz  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  Adja meg a rendszergazdák jogosultságszint-emelési kérésének viselkedését rendszergazdai jóváhagyás módban.  

  - **Nincs konfigurálva**  
  - **Jogosultságszint-emelés kérés nélkül**  
  - **Hitelesítő adatok bekérése a biztonságos asztalon**  
  - **Hitelesítő adatok bekérése**  
  - **Beleegyezés kérése**  
  - **Beleegyezés kérése nem Windows rendszerű bináris fájlokhoz**  


- **Jogosultságszint-emelési kérés általános jogú felhasználók számára**  
  **Alapértelmezett**: hitelesítő adatok kérése  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  A jogosultságszint-emelési kérés viselkedésének meghatározása az általános jogú felhasználók számára.  

  - **Nincs konfigurálva**  
  - **Jogosultságszint-emelési kérések automatikus megtagadása**  
  - **Hitelesítő adatok bekérése a biztonságos asztalon**  
  - **Hitelesítő adatok bekérése**  

- **Jogosultságszint-emelési kérések átirányítása a felhasználó interaktív asztalára**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **Engedélyezve** – az összes jogosultságszint-emelési kérelem nem a biztonságos asztal helyett az interaktív felhasználó asztalára lép. A rendszer a rendszergazdákra és az általános jogú felhasználókra vonatkozó kérések viselkedését szabályzó házirend-beállításokat alkalmazza.  
  - **Nincs konfigurálva** – kényszerítse az összes jogosultságszint-emelési kérést a biztonságos asztalra, függetlenül attól, hogy a rendszergazdák és a normál felhasználók milyen figyelmeztetési viselkedési házirend-beállításokkal rendelkeznek.

- **Emelt szintű kérés az alkalmazások telepítéséhez**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **Engedélyezett** – az alkalmazás telepítési csomagjai nem észlelhetők vagy jogosultságszint-emelésre kérik.
   - **Nincs konfigurálva** – a felhasználóknak rendszergazdai felhasználónevet és jelszót kell megadniuk, ha az alkalmazás telepítési csomagja emelt szintű jogosultságokat igényel.

- **UIA jogosultságszint-emelési kérés biztonságos asztal nélkül**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **Engedélyezés – engedélyezi** , hogy a UIAccess alkalmazások jogosultságszint-emelést kérjenek a biztonságos asztal használata nélkül.  
- **Nem konfigurált** – a jogosultságszint-emelési kérések biztonságos asztalt használnak.  

#### <a name="admin-approval-mode"></a>Rendszergazdai jóváhagyási mód  

- **Rendszergazdai jóváhagyási mód a beépített rendszergazda számára**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **Engedélyezve** – engedélyezi a beépített rendszergazdai fiók számára a rendszergazdai jóváhagyási mód használatát. A jogosultságszint-emelést igénylő műveletek felhasználói jóváhagyást kérnek.  
  - **Nincs konfigurálva** – minden alkalmazást teljes rendszergazdai jogosultságokkal futtat.  

- **Összes rendszergazda futtatása rendszergazdai jóváhagyás módban**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **Engedélyezve**– rendszergazdai jóváhagyási mód engedélyezése.  
  - **Nincs konfigurálva** – a rendszergazdai engedélyezési mód és az összes kapcsolódó UAC-házirend-beállítás letiltása.  

### <a name="microsoft-network-client"></a>Microsoft hálózati ügyfél  

- **Kommunikáció digitális aláírása (ha a kiszolgáló egyetért)**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  Meghatározza, hogy az SMB-ügyfél egyeztet-e az SMB-csomagok aláírásával.  
  - **Letiltás** – az SMB-ügyfél soha nem tárgyalja az SMB-csomagok aláírását.
  - **Nincs konfigurálva** – a Microsoft hálózati ügyfél arra kéri a kiszolgálót, hogy futtassa az SMB-csomagot a munkamenet beállításakor. Ha a csomagaláírás engedélyezve van a kiszolgálón, a csomagaláírás egyeztetése megkezdődik.  

- **Titkosítatlan jelszó küldése harmadik féltől származó SMB-kiszolgálókra**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **Blokkolás** – a kiszolgáló-üzenetblokk (SMB) átirányító képes szöveges jelszavakat küldeni a nem Microsoft SMB-kiszolgálókra, amelyek nem támogatják a jelszó titkosítását a hitelesítés során.  
  - **Nincs konfigurálva** – egyszerű szöveges jelszavak küldésének tiltása. A jelszavak titkosítva vannak.  

- **Kommunikáció digitális aláírása (mindig)**  
  **Alapértelmezett**: nincs konfigurálva  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **Engedélyezés** – a Microsoft hálózati ügyfél nem kommunikál Microsoft hálózati kiszolgálóval, kivéve, ha az adott kiszolgáló egyetért az SMB-csomagok aláírásával.  
  - **Nincs konfigurálva** – az SMB-csomagok aláírása egyeztetve van az ügyfél és a kiszolgáló között.  

### <a name="microsoft-network-server"></a>Microsoft hálózati kiszolgáló  
  
- **Kommunikáció digitális aláírása (ha az ügyfél egyetért)**  
  **Alapértelmezett**: nincs konfigurálva  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **Engedélyezés** – a Microsoft hálózati kiszolgáló egyezteti az SMB-csomagokat az ügyfél által kért aláírással. Ez azt jelenti, hogy ha a csomagaláírás engedélyezve van az ügyfélnél, a csomagaláírás egyeztetése megkezdődik.  
  - **Nincs konfigurálva** – az SMB-ügyfél soha nem tárgyalja az SMB-csomagok aláírását.  

- **Kommunikáció digitális aláírása (mindig)**  
  **Alapértelmezett**: nincs konfigurálva  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **Engedélyezés** – a Microsoft hálózati kiszolgáló nem kommunikál a Microsoft hálózati ügyféllel, kivéve, ha az ügyfél elfogadja az SMB-csomagok aláírását.  
  - **Nincs konfigurálva** – az SMB-csomagok aláírása egyeztetve van az ügyfél és a kiszolgáló között.  

## <a name="xbox-services"></a>Xbox-szolgáltatások

- **Xbox-játék mentési feladata**  
  **Alapértelmezett**: nincs konfigurálva  
  CSP: [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  Ez a beállítás határozza meg, hogy az Xbox-játékok mentési feladata engedélyezve van-e vagy le van tiltva.  
  - **Engedélyezve**
  - **Nincs konfigurálva**

- **Xbox-tartozékok kezelési szolgáltatása**  
  **Alapértelmezett**: manuális  
  CSP: [SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  Ez a beállítás határozza meg a tartozék-felügyeleti szolgáltatás indítási típusát.  
  - **Kézi**
  - **Automatikus**
  - **Tiltva**

- **Xbox Live Auth Manager szolgáltatás**  
  **Alapértelmezett**: manuális  
  CSP: [SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  Ez a beállítás határozza meg az élő Auth Manager szolgáltatás indítási típusát.  
  - **Kézi**
  - **Automatikus**
  - **Tiltva**
 
- **Xbox Live game Save szolgáltatás**  
  **Alapértelmezett**: manuális  
  CSP: [SystemServices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  Ez a beállítás határozza meg az élő játékok mentési szolgáltatásának indítási típusát.  
  - **Kézi**
  - **Automatikus**
  - **Tiltva**

- **Xbox Live hálózatkezelési szolgáltatás**  
  **Alapértelmezett**: manuális  
  CSP: [SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  Ez a beállítás határozza meg a hálózati szolgáltatás indítási típusát.  
  - **Kézi**
  - **Automatikus**
  - **Tiltva**

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../configuration/device-profile-assign.md), és [Figyelje annak állapotát](../configuration/device-profile-monitor.md).  

Endpoint Protection-beállítások konfigurálása [MacOS](endpoint-protection-macos.md) -eszközökön.  
