---
title: "Tűzfalházirendek Windows rendszerű számítógépekhez | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 9f338efe3ef40da3db40c12d1a18c4122e65dc5d


---

# A Windows rendszerű számítógépek védelme Windows tűzfalházirendek használatával a Microsoft Intune-ban
A Microsoft Intune szolgáltatással számos módon teheti biztonságossá az Intune ügyfélprogrammal kezelt Windows rendszerű számítógépeket, beleértve a Windows tűzfal beállításainak konfigurálását lehetővé tevő házirendek használatát.

Ha még nem telepítette a Windows rendszerhez készült Intune ügyfélprogramot a számítógépeken, [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](install-the-windows-pc-client-with-microsoft-intune.md) című témakörben olvashat erről.

Az alábbi szakaszokban található információk segítségével konfigurálhatja, telepítheti és figyelheti a Windows tűzfalházirendeket a Windows rendszerű számítógépeken.

## Intune-házirendek használata a Windows tűzfal felügyeletéhez
A Windows tűzfalházirenddel a kezelt számítógépeken lévő Windows tűzfalat szabályozó beállításokat hozhat létre és alkalmazhat. A Windows tűzfal egyéni kivételeinek kezelésére nincs lehetősége, és ezek a beállítások nincsenek hatással a külső gyártótól származó tűzfalakra.

> [!NOTE]
> Ha a Microsoft Intune házirendje és a Csoportházirend is konfigurálva van a számítógép ugyanazon beállításának kezeléséhez, a csoportházirend-beállítások felülbírálják a Microsoft Intune házirendjét. Az Intune-házirendek és a Csoportházirend közötti ütközések elkerülésével kapcsolatos további tudnivalókat lásd: [A GPO- és Microsoft Intune-házirendek ütközéseinek feloldása](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Ha Windows Vista rendszerű számítógépekre szeretné alkalmazni a Windows tűzfal beállításait, először telepítenie kell [a KB971800. számú gyorsjavítást](http://support2.microsoft.com/kb/971800) ezeken a számítógépeken.

> [!IMPORTANT]
> A Windows tűzfalnak az Intune szolgáltatással való kezeléséhez a következő két szolgáltatást be kell kapcsolnia a kezelni kívánt számítógépeken:
>
> -   Windows tűzfal
> -   IPsec-házirendügynök

## Windows tűzfalházirend konfigurálása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Házirend** &gt; **Házirend hozzáadása** elemet.

2.  Konfigurálja és alkalmazza a **Windows tűzfal beállításai** házirendet. Használhatja az ajánlott beállításokat, vagy testre is szabhatja a beállításokat. Ha a házirendek létrehozásával és alkalmazásával kapcsolatban további tájékoztatásra van szüksége, [A Windows rendszerű számítógépek a Microsoft Intune számítógépügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) című témakörben olvashat erről bővebben.

    A következő szakaszban azok az értékek található, amelyek beállíthatók a házirendben, továbbá az alapértelmezett értékek, amelyek alkalmazva lesznek, ha nem szabja testre a házirendet.

Az alkalmazott Windows tűzfalházirend állapotát a **Házirend** munkaterület **Minden házirend** lapján tekintheti meg.

## A Windows tűzfal házirend-beállításai

### A Windows tűzfal bekapcsolása

Ezek a házirend-beállítások engedélyezik a Windows tűzfalat a tartományokhoz (például a munkahelyen), a megbízható magánhálózatokhoz (például otthoni hálózathoz) vagy a nem megbízható, nyilvános hálózatokhoz (például egy kávézóban) csatlakoztatott felügyelt számítógépeken. Az egyes beállítások alapértelmezett értéke a legbiztonságosabb **Igen** érték. 



### Az összes bejövő kapcsolat tiltása, az engedélyezett programok listáján lévőket is beleértve

Ezek a házirend-beállítások a bejövő forgalom blokkolására konfigurálják a Windows tűzfalat a tartományokhoz (például a munkahelyen), a megbízható magánhálózatokhoz (például otthoni hálózathoz) vagy a nem megbízható, nyilvános hálózatokhoz (például egy kávézóban) csatlakoztatott felügyelt számítógépeken. Az egyes beállítások alapértelmezett értéke a legbiztonságosabb **Igen** érték. 

> [!IMPORTANT]
> Ha a környezet szervizcsomagok nélküli Windows Vista operációs rendszert futtató számítógépeket tartalmaz, telepítse a Microsoft tudásbázis [971800-as számú cikkéhez](http://go.microsoft.com/fwlink/?LinkId=188405) tartozó frissítést, vagy tiltsa le a **Minden bejövő kapcsolat blokkolása** házirend-beállítást az érintett számítógépekre bevezetett házirendekben.

### A felhasználó értesítése, ha a Windows tűzfal új programot blokkol

Ezek a házirend-beállítások arra konfigurálják a Windows tűzfalat, hogy értesítse-e a felhasználót, amikor bejövő forgalmat blokkol a tartományokhoz (például a munkahelyen), a megbízható magánhálózatokhoz (például otthoni hálózathoz) vagy a nem megbízható, nyilvános hálózatokhoz (például egy kávézóban) csatlakoztatott felügyelt számítógépeken. Az egyes beállítások alapértelmezett értéke az **Igen** érték.


### Előre megadott kivételek

Miután konfigurálta a fenti alapértékeket, megadhat kivételeket, amelyek átengedik a tűzfalon a hálózati forgalom meghatározott részét, függetlenül a fent beállított értékektől. Alapértelmezés szerint a beállítások egyike sincs konfigurálva.

|Beállítás neve|Részletek|
|------------------|--------------------|
|**BranchCache – Tartalombeolvasás**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára, hogy a HTTP protokollal olvassanak be tartalmakat egymástól elosztott módban, a központi gyorsítótárból pedig központi gyorsítótár módban. A beállítás HTTP protokollt használ.|
|**BranchCache – Központi gyorsítótár ügyfele**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára a központi gyorsítótárak használatát. A beállítás HTTPS protokollt használ.|
|**BranchCache – Központi gyorsítótár kiszolgálója**|Lehetővé teszi a BranchCache-ügyfelek számára, hogy központi gyorsítótárakat használjanak a más ügyfelekkel való kommunikációhoz. A beállítás HTTPS protokollt használ.|
|**BranchCache – Társfelderítés**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára, hogy a WS-Discovery protokollal ellenőrizzék a tartalmak elérhetőségét a helyi alhálózaton.|
|**BITS társ-gyorsítótárazás**|Lehetővé teszi, hogy az ügyfelek a Háttérben futó intelligens átviteli szolgáltatással (BITS) keressenek meg és osszanak meg olyan fájlokat, amelyek az ugyanazon az alhálózaton lévő ügyfelek BITS-gyorsítótárában vannak tárolva. A beállítás WSDAPI és RPC technológiát használ.|
|**Kapcsolódás hálózati kivetítőhöz**|Lehetővé teszi a felhasználók számára, hogy bemutatók kivetítése céljából vezetékes vagy vezeték nélküli hálózatokon keresztül kapcsolódjanak kivetítőkhöz. A beállítás WSDAPI technológiát használ.|
|**Hálózati szolgáltatásmag**|Lehetővé teszi, hogy az ügyfelek az IPv4 és az IPv6 használatával is kapcsolódhassanak a hálózati erőforrásokhoz.|
|**Elosztott tranzakciók koordinátora**|Lehetővé teszi a kezelt számítógépek számára, hogy összehangolják a tranzakcióvédett erőforrásokat, például adatbázisokat, üzenetsorokat vagy fájlrendszereket frissítő tranzakciókat.|
|**Fájl- és nyomtatómegosztás**|Lehetővé teszi a felhasználók számára a helyi fájlok és nyomtatók megosztását a hálózaton lévő többi felhasználóval. A beállítás NetBIOS, LLMNR, SMB és RPC protokollt használ.|
|**Otthoni csoport**<br>(Windows 7 vagy újabb)|Lehetővé teszi, hogy a kezelt számítógépek részt vegyenek az Otthoni csoport hálózatban.|
|**iSCSI szolgáltatás**|Lehetővé teszi, hogy a kezelt számítógépek kapcsolódjanak az iSCSI-kiszolgálókhoz és -eszközökhöz.|
|**Kulcskezelő szolgáltatás**|Lehetővé teszi a számítógépek számbavételét vállalati környezetben a licencek ellenőrzése során.|
|**Media Center Extender készülékek**|Lehetővé teszi a Media Center Extender készülékek számára, hogy kommunikáljanak a Windows Media Centert futtató számítógépekkel. A beállítás SSDP protokollt és qWave keretrendszert használ.|
|**Netlogon szolgáltatás**|Egy biztonsági csatornát konfigurál a tartományi ügyfelek és a tartományvezérlők között, aminek célja a felhasználók és a szolgáltatások hitelesítése. A beállítás RPC protokollt használ.|
|**Hálózatfelderítés**|Lehetővé teszi, hogy a számítógépek észleljenek más eszközöket a hálózaton, és azok észleljék a számítógépeket. A beállítás funkciófelderítést (Function Discovery Host and Publication Services), Univerzális Plug and Play, SSDP, NetBIOS és LLMNR protokollt használ.|
|**Teljesítménynaplók és riasztások**|Lehetővé teszi a Teljesítménynaplók és riasztások szolgáltatás távoli kezelését. A beállítás RPC protokollt használ.|
|**Távfelügyelet**|Lehetővé teszi a számítógép távoli felügyeletét.|
|**Távsegítség**|Lehetővé teszi a kezelt számítógépek felhasználói számára, hogy távsegítséget kérjenek más felhasználóktól a hálózaton. A beállítás SSDP, PNRP, Teredo és UPnP protokollt használ.|
|**Távoli asztal**|Lehetővé teszi, hogy a számítógép a Távoli asztal szolgáltatással hozzáférjen más számítógépekhez.|
|**Eseménynapló távoli kezelése**|Lehetővé teszi az ügyfelek eseménynaplóinak távoli megjelenítését és kezelését. A beállítás Named Pipes és RPC protokollt használ.|
|**Ütemezett feladatok távoli felügyelete**|Lehetővé teszi a feladatütemező szolgáltatás távoli kezelését. A beállítás RPC protokollt használ.|
|**Távoli szolgáltatásfelügyelet**|Lehetővé teszi az ügyfelek helyi szolgáltatásainak távoli kezelését. A beállítás Named Pipes és RPC protokollt használ.|
|**Távoli kötetkezelés**|Lehetővé teszi a távoli szoftver- és hardverkötet-kezelést. A beállítás RPC protokollt használ.|
|**Útválasztás és távelérés**|Lehetővé teszi bejövő VPN- és távelérésű kapcsolatok használatát a számítógépeken.|
|**Secure Socket Tunneling Protocol**|Lehetővé teszi a bejövő VPN-kapcsolatok SSTP protokollal való használatát a kezelt számítógépeken. A beállítás HTTPS protokollt használ.|
|**SNMP-trap**|Lehetővé teszi az SNMP-trapszolgáltatás forgalmának fogadását a kezelt számítógépeken.|
|**UPnP-keretrendszer**|Úgy konfigurálja az UPnP keretrendszer szolgáltatást a számítógépeken, hogy azok felderíthessék és használhassák az UPnP hitelesített eszközöket.|
|**Windows együttműködés számítógépnév-regisztrációs szolgáltatása**|Lehetővé teszi, hogy a számítógépek a PNRP protokollal keressenek meg más számítógépeket és kommunikáljanak velük. A beállítás SSDP és PNRP protokollt használ.|
|**Windows Media Player**|Engedélyezi a felhasználóknak a médiafolyamok UDP-n keresztüli fogadását.|
|**A Windows Media Player hálózatmegosztási szolgáltatása**|Engedélyezi a felhasználóknak a hálózati médiamegosztást. A beállítás SSDP, qWave és UPnP hálózati protokollt használ.|
|**Windows Media Player hálózati megosztási szolgáltatás (internet)**<br>(Windows 7 vagy újabb)|Lehetővé teszi a felhasználók számára, hogy otthoni médiatartalmakat osszanak meg az interneten.|
|**Windows Tárgyaló**|Lehetővé teszi, hogy a felhasználók egy hálózaton keresztül együttműködve megosszanak dokumentumokat, programokat vagy az asztalukat. A beállítás DFSR és P2P technológiát használ.|
|**Windows társközi együttműködési alaprendszer**|Különböző társközi programokat és technológiákat konfigurál, hogy azok tudjanak csatlakozni. A beállítás SSDP és PNRP protokollt használ.|
|**Rendszer-felügyeleti webszolgáltatások (kompatibilitás)**|Lehetővé teszi az ügyfelek WS-Management technológián alapuló távoli kezelését. A WS-Management egy webszolgáltatás-alapú protokoll, amely operációs rendszerek és egyéb eszközök távoli kezelésére szolgál.|
|**Rendszer-felügyeleti webszolgáltatások**<br>(Windows 8 vagy újabb).|Lehetővé teszi az ügyfelek WS-Management technológián alapuló távoli kezelését. A WS-Management egy webszolgáltatás-alapú protokoll, amely operációs rendszerek és egyéb eszközök távoli kezelésére szolgál.|
|**Windows Virtual PC**<br>(Windows 7 vagy újabb)|Lehetővé teszi, hogy a virtuális gépek kommunikáljanak más számítógépekkel.|
|**Vezeték nélküli hordozható eszközök**|Lehetővé teszi a hálózatra csatlakoztatható kamerákról vagy egyéb médiaeszközökről a kezelt számítógépek felé irányuló, Media Transfer Protocol (MTP) alapú médiaátvitelt. A beállítás SSDP és UPnP technológiát használ.|

### További információ
[Szabályzatok a Windows rendszerű számítógépek védelméhez](policies-to-protect-windows-pcs-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


