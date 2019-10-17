---
title: Tűzfalszabályok Windows rendszerű számítógépekhez
titleSuffix: Microsoft Intune
description: Az Intune-nal számos módon teheti biztonságossá az Intune ügyfélprogrammal kezelt számítógépeket, beleértve a Windows tűzfal beállításainak konfigurálását is.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c736c905045fd3afd40a12243986fbe69452ecd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502824"
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>A Windows rendszerű számítógépek védelme Windows tűzfalházirendek használatával a Microsoft Intune-ban

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> Az ebben a témakörben ismertetett információk csak az Intune-szoftverügyféllel PC-ként felügyelt Windows-számítógépekre vonatkoznak. Ha a tűzfal beállításait a mobileszközökként regisztrált Windows rendszerű számítógépeken szeretné kezelni, tekintse meg [az Endpoint Protection-beállítások hozzáadása az Intune-ban](../protect/endpoint-protection-configure.md)című témakört.

A Microsoft Intune-nal számos módon teheti biztonságossá az Intune ügyfélprogrammal kezelt Windows rendszerű számítógépeket. Többek között olyan szabályzatokat tesz elérhetővé, amelyekkel konfigurálhatja a Windows tűzfal beállításait a számítógépeken.

Ha még nem telepítette a Windows rendszerhez készült Intune ügyfélprogramot a számítógépeken, [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](install-the-windows-pc-client-with-microsoft-intune.md) című témakörben olvashat erről.

Az alábbi szakaszokban található információk segítségével konfigurálhatja, telepítheti és figyelheti a Windows tűzfalházirendeket a Windows rendszerű számítógépeken.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Intune-házirendek használata Windows tűzfal felügyeletéhez
A Windows tűzfalházirenddel a kezelt számítógépeken lévő Windows tűzfalat szabályozó beállításokat hozhat létre és alkalmazhat. A Windows tűzfal egyéni kivételeinek kezelésére nincs lehetősége, és ezek a beállítások nincsenek hatással a külső gyártótól származó tűzfalakra.

> [!NOTE]
> Ha a Microsoft Intune házirendje és a Csoportházirend is konfigurálva van a számítógép ugyanazon beállításának kezeléséhez, a csoportházirend-beállítások felülbírálják a Microsoft Intune házirendjét. Az Intune-házirend és a Csoportházirend közötti ütközések elkerülésével kapcsolatos további tudnivalókat lásd: [A GPO- és Microsoft Intune-házirendek ütközéseinek feloldása](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Ha Windows Vista rendszerű számítógépekre szeretné alkalmazni a Windows tűzfal beállításait, először telepítenie kell a [KB971800. számú gyorsjavítást](https://support2.microsoft.com/kb/971800) ezeken a számítógépeken.

> [!IMPORTANT]
> A Windows tűzfalnak az Intune szolgáltatással való kezeléséhez a következő két szolgáltatást be kell kapcsolnia a kezelni kívánt számítógépeken:
>
> - Windows tűzfal
> - IPsec-házirendügynök

## <a name="configure-a-windows-firewall-policy"></a>Windows tűzfalházirend konfigurálása

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Házirend** &gt; **Házirend hozzáadása** elemet.

2. Konfigurálja és alkalmazza a **Windows tűzfal beállításai** házirendet. Használhatja az ajánlott beállításokat, vagy testre is szabhatja azokat. Ha a házirendek létrehozásával és alkalmazásával kapcsolatban további tájékoztatásra van szüksége, [A Windows rendszerű számítógépek a Microsoft Intune számítógépügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) című témakörben olvashat erről bővebben.

    A következő szakaszban azok az értékek találhatók, amelyek beállíthatók a házirendben, továbbá az alapértelmezett értékek, amelyek alkalmazva lesznek, ha nem szabja testre azt.

Az alkalmazott Windows tűzfalházirend állapotát a **Házirend** munkaterület **Minden házirend** lapján tekintheti meg.

## <a name="specify-policy-settings-for-windows-firewall"></a>A Windows tűzfal házirend-beállításainak megadása

### <a name="turn-on-windows-firewall"></a>A Windows tűzfal bekapcsolása

Ezek a házirendbeállítások bekapcsolják a Windows tűzfalat azokon a felügyelt számítógépeken, amelyek:
- Csatlakoztatva vannak egy tartományhoz (például a munkahelyen)
- Csatlakoztatva vannak egy (megbízható) magánhálózathoz (például otthoni hálózathoz)
- Csatlakoztatva vannak egy nem megbízható hálózathoz (például egy kávézóban)

Az egyes beállítások alapértelmezett értéke a legbiztonságosabb **Igen** érték.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Az összes bejövő kapcsolat tiltása, az engedélyezett programok listáján lévőket is beleértve

Ezek a házirendbeállítások a Windows Tűzfalat a bejövő hálózati forgalom blokkolására konfigurálják azokon a felügyelt számítógépeken, amelyek:
- Csatlakoztatva vannak egy tartományhoz (például a munkahelyen)
- Csatlakoztatva vannak egy (megbízható) magánhálózathoz (például otthoni hálózathoz)
- Csatlakoztatva vannak egy nem megbízható hálózathoz (például egy kávézóban)

Az egyes beállítások alapértelmezett értéke a legbiztonságosabb **Igen** érték.

> [!IMPORTANT]
> Ha a környezet szervizcsomagok nélküli Windows Vista operációs rendszert futtató számítógépeket tartalmaz, telepítse a Microsoft tudásbázis [971800-as számú cikkéhez](https://go.microsoft.com/fwlink/?LinkId=188405) tartozó frissítést, vagy tiltsa le a **Minden bejövő kapcsolat blokkolása** házirend-beállítást az érintett számítógépekre bevezetett házirendekben.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>A felhasználó értesítése, ha a Windows tűzfal új programot blokkol

Ezek a házirendbeállítások határozzák meg, hogy a Windows tűzfal értesítse-e a felhasználót a bejövő hálózati forgalom blokkolásáról azokon a felügyelt számítógépeken, amelyek:
- Csatlakoztatva vannak egy tartományhoz (például a munkahelyen)
- Csatlakoztatva vannak egy (megbízható) magánhálózathoz (például otthoni hálózathoz)
- Csatlakoztatva vannak egy nem megbízható hálózathoz (például egy kávézóban)

Az egyes beállítások alapértelmezett értéke az **Igen** érték.


### <a name="configure-predefined-exceptions"></a>Előre megadott kivételek konfigurálása

Konfigurálhatja azokat a kivételeket, amelyek bizonyos típusú hálózati forgalmat engedélyeznek a tűzfalon keresztül, függetlenül a korábban megadott értékektől. Alapértelmezés szerint a beállítások egyike sincs konfigurálva.

|Beállítás neve|Details|
|------------------|--------------------|
|**BranchCache – Tartalombeolvasás**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára, hogy a HTTP protokollal olvassanak be tartalmakat más BranchCache-ügyfelektől elosztott módban, a központi gyorsítótárból pedig központi gyorsítótár módban. A beállítás HTTP protokollt használ.|
|**BranchCache – Központi gyorsítótár ügyfele**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára a központi gyorsítótárak használatát. A beállítás HTTPS protokollt használ.|
|**BranchCache – Központi gyorsítótár kiszolgálója**|Lehetővé teszi a BranchCache-ügyfelek számára, hogy központi gyorsítótárakat használjanak a más ügyfelekkel való kommunikációhoz. A beállítás HTTPS protokollt használ.|
|**BranchCache – Társfelderítés**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára, hogy a WS-Discovery protokollal ellenőrizzék a tartalmak elérhetőségét a helyi alhálózaton.|
|**BITS társ-gyorsítótárazás**|Lehetővé teszi, hogy az ügyfelek a Háttérben futó intelligens átviteli szolgáltatással (BITS) keressenek meg és osszanak meg olyan fájlokat, amelyek az ugyanazon az alhálózaton lévő ügyfelek BITS-gyorsítótárában vannak tárolva. A beállítás WSDAPI és Távoli eljáráshívás (RPC) technológiát használ.|
|**Kapcsolódás hálózati kivetítőhöz**|Lehetővé teszi a felhasználók számára, hogy bemutatók kivetítése céljából vezetékes vagy vezeték nélküli hálózatokon keresztül kapcsolódjanak kivetítőkhöz. A beállítás WSDAPI technológiát használ.|
|**Hálózati szolgáltatásmag**|Lehetővé teszi, hogy az ügyfelek az IPv4 és az IPv6 használatával is kapcsolódhassanak a hálózati erőforrásokhoz.|
|**Elosztott tranzakciók koordinátora**|Lehetővé teszi a felügyelt számítógépek számár a tranzakcióvédett erőforrások, például adatbázisok, üzenetsorok vagy fájlrendszereket frissítő tranzakciók összehangolását.|
|**Fájl- és nyomtatómegosztás**|Lehetővé teszi a felhasználók számára helyi fájlok és nyomtatók megosztását a hálózaton lévő többi felhasználóval. A beállítás NetBIOS, Link Local Multicast Name Resolution (LLMNR), Server Message Block (SMB) protokollt és RPC technológiát használ.|
|**Otthoni csoport**<br>(Windows 7 vagy újabb)|Lehetővé teszi, hogy a felügyelt számítógépek részt vegyenek egy Otthoni csoport típusú hálózatban.|
|**iSCSI szolgáltatás**|Lehetővé teszi, hogy a felügyelt számítógépek kapcsolódjanak az iSCSI-kiszolgálókhoz és -eszközökhöz.|
|**Kulcskezelő szolgáltatás**|Lehetővé teszi a számítógépek számbavételét vállalati környezetben a licencek ellenőrzése során.|
|**Media Center Extender készülékek**|Lehetővé teszi a Media Center Extender készülékek számára, hogy kommunikáljanak a Windows Media Centert futtató számítógépekkel. A beállítás SSDP protokollt és qWave keretrendszert használ.|
|**Netlogon szolgáltatás**|Egy biztonsági csatornát konfigurál a tartományi ügyfelek és a tartományvezérlők között, aminek célja a felhasználók és a szolgáltatások hitelesítése. A beállítás RPC protokollt használ.|
|**Hálózatfelderítés**|Lehetővé teszi, hogy a számítógépek észleljenek más eszközöket a hálózaton, és azok észleljék a számítógépeket. A beállítás funkciófelderítést (Function Discovery Host and Publication Services), Univerzális Plug and Play, SSDP, NetBIOS és LLMNR protokollt használ.|
|**Teljesítménynaplók és riasztások**|Lehetővé teszi a Teljesítménynaplók és riasztások szolgáltatás távoli kezelését. A beállítás RPC protokollt használ.|
|**Távfelügyelet**|Lehetővé teszi a számítógép távoli felügyeletét.|
|**Távsegítség**|Lehetővé teszi a kezelt számítógépek felhasználói számára, hogy távsegítséget kérjenek más felhasználóktól a hálózaton. A beállítás SSDP, PNRP (Peer Name Resolution Protocol), Teredo és UPnP protokollt használ.|
|**Távoli asztal**|Lehetővé teszi, hogy a számítógép a Távoli asztal szolgáltatással hozzáférjen más számítógépekhez.|
|**Eseménynapló távoli kezelése**|Lehetővé teszi az ügyfelek eseménynaplóinak távoli megjelenítését és kezelését. A beállítás Named Pipes és RPC protokollt használ.|
|**Ütemezett feladatok távoli felügyelete**|Lehetővé teszi a feladatütemező szolgáltatás távoli kezelését. A beállítás RPC protokollt használ.|
|**Távoli szolgáltatásfelügyelet**|Lehetővé teszi az ügyfelek helyi szolgáltatásainak távoli kezelését. A beállítás Named Pipes és RPC protokollt használ.|
|**Távoli kötetkezelés**|Lehetővé teszi a távoli szoftver- és hardverkötet-kezelést. A beállítás RPC protokollt használ.|
|**Útválasztás és távelérés**|Lehetővé teszi bejövő VPN- és távelérésű kapcsolatok használatát a számítógépeken.|
|**SSTP protokoll**|Lehetővé teszi a bejövő VPN-kapcsolatok Secure Socket Tunneling Protcol (SSTP) alapú használatát a felügyelt számítógépeken. A beállítás HTTPS protokollt használ.|
|**SNMP-trap**|Lehetővé teszi a Simple Network Management Protocol (SNMP) trapszolgáltatás forgalmának fogadását a kezelt számítógépeken.|
|**UPnP-keretrendszer**|Úgy konfigurálja az UPnP keretrendszer szolgáltatást a számítógépeken, hogy azok felderíthessék és használhassák az UPnP hitelesített eszközöket.|
|**Windows együttműködés számítógépnév-regisztrációs szolgáltatása**|Lehetővé teszi, hogy a számítógépek SSDP és PNRP protokollal keressenek meg más számítógépeket és kommunikáljanak velük.|
|**Windows Media Player**|Engedélyezi a felhasználóknak a médiafolyamok UDP-n (User Datagram Protocol) keresztüli fogadását.|
|**A Windows Media Player hálózatmegosztási szolgáltatása**|Engedélyezi a felhasználóknak a hálózati médiamegosztást. A beállítás SSDP, qWave és UPnP hálózati protokollt használ.|
|**A Windows Media Player hálózati megosztási szolgáltatása (internet)**<br>(Windows 7 vagy újabb)|Lehetővé teszi a felhasználók számára, hogy otthoni médiatartalmakat osszanak meg az interneten.|
|**Windows Meeting Space**|Lehetővé teszi, hogy a felhasználók egy hálózaton keresztül együttműködve megosszanak dokumentumokat, programokat vagy az asztalukat. A beállítás elosztott fájlrendszer replikációs (DFSR) és P2P technológiát használ.|
|**Windows társközi együttműködési alaprendszer**|Különböző társközi programokat és technológiákat konfigurál, hogy azok tudjanak csatlakozni. A beállítás SSDP és PNRP protokollt használ.|
|**Rendszer-felügyeleti webszolgáltatások (kompatibilitás)**|Lehetővé teszi a felügyelt számítógépek WS-Management technológián alapuló távoli kezelését. A WS-Management egy webszolgáltatás-alapú protokoll, amely operációs rendszerek és egyéb eszközök távoli kezelésére szolgál.|
|**Rendszer-felügyeleti webszolgáltatások**<br>(Windows 8 vagy újabb).|Lehetővé teszi a felügyelt számítógépek WS-Management technológián alapuló távoli kezelését. A WS-Management egy webszolgáltatás-alapú protokoll, amely operációs rendszerek és egyéb eszközök távoli kezelésére szolgál.|
|**Windows Virtual PC**<br>(Windows 7 vagy újabb)|Lehetővé teszi, hogy a virtuális gépek kommunikáljanak más számítógépekkel.|
|**Vezeték nélküli hordozható eszközök**|Lehetővé teszi a hálózatra csatlakoztatható kamerákról vagy egyéb médiaeszközökről a felügyelt számítógépek felé irányuló, MTP protokoll alapú médiaátvitelt. A beállítás SSDP és UPnP technológiát használ.|

## <a name="see-also"></a>További információ
[Szabályzatok a Windows rendszerű számítógépek védelméhez](policies-to-protect-windows-pcs-in-microsoft-intune.md)
