---
title: Windows rendszerű számítógépekhez használható tűzfalszabályok
titleSuffix: Microsoft Intune
description: Az Intune segítségével több módon is biztonságossá teheti az Intune-ügyféllel kezelt számítógépeket, beleértve a Windows tűzfal beállításainak konfigurálását is.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e5a67ade5f1b3c9efc2674887a042bd828136fa
ms.sourcegitcommit: a2654f3642b43b29ab0e1cbb2dfa2b56aae18d0e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72310748"
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Segítse a Windows rendszerű számítógépek védelmét a Windows tűzfal házirendjeinek használatával Microsoft Intune

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

> [!NOTE]
> A jelen témakörben található információk csak azokra a Windows rendszerű számítógépekre vonatkoznak, amelyeket az Intune-ügyfélszoftver használatával kezel számítógépként. Ha a tűzfal beállításait a mobileszközökként regisztrált Windows rendszerű számítógépeken szeretné kezelni, tekintse meg [az Endpoint Protection-beállítások hozzáadása az Intune-ban](../protect/endpoint-protection-configure.md)című témakört.

Microsoft Intune segítségével számos módon védheti meg az Intune-ügyféllel felügyelt Windows rendszerű számítógépeket. Ennek egyik módja, ha olyan házirendeket biztosít, amelyek lehetővé teszik a Windows tűzfal beállításainak konfigurálását a számítógépeken.

Ha még nem telepítette az Intune Windows PC-ügyfelet a számítógépeken, tekintse meg [a Windows rendszerű számítógép-ügyfél telepítése Microsoft Intunekal](install-the-windows-pc-client-with-microsoft-intune.md)című témakört.

A következő részben található információk segítségével konfigurálhatja, telepítheti és figyelheti a Windows tűzfal házirendjeit Windows rendszerű számítógépeken.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Intune-házirendek használata a Windows tűzfal felügyeletéhez
A Windows tűzfal házirendje lehetővé teszi olyan beállítások létrehozását és központi telepítését, amelyek a Windows tűzfalat vezérlik a felügyelt számítógépeken. A Windows tűzfal egyéni kivételei nem kezelhetők, és ezek a beállítások nincsenek hatással a külső gyártótól származó tűzfalakra.

> [!NOTE]
> Ha Microsoft Intune házirend és Csoportházirend úgy vannak konfigurálva, hogy ugyanazokat a beállításokat kezeljék a számítógépen, akkor a Csoportházirend beállítás felülbírálja a Microsoft Intune házirendet. További információ az Intune-szabályzat és a Csoportházirend közötti ütközések elkerüléséről: [GPO-k feloldása és Microsoft Intune házirend-ütközések](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Ha a Windows tűzfal beállításait Windows Vista rendszert futtató számítógépekre szeretné telepíteni, előbb telepítenie kell a [gyorsjavítások kb971800 ezeken](https://support2.microsoft.com/kb/971800) ezen számítógépeken.

> [!IMPORTANT]
> A Windows tűzfal Intune-nal való kezeléséhez győződjön meg arról, hogy az alábbi két szolgáltatás engedélyezve van a felügyelt számítógépeken:
>
> - Windows tűzfal
> - IPsec-házirend ügynöke

## <a name="configure-a-windows-firewall-policy"></a>Windows tűzfal házirend konfigurálása

1. A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/)válassza a **házirend** @no__t – 2 **házirend hozzáadása**lehetőséget.

2. Konfigurálja és telepítse a **Windows tűzfal beállításai** házirendet. Használhatja az ajánlott beállításokat, vagy testre is szabhatja a beállításokat. Ha további információra van szüksége a házirendek létrehozásáról és telepítéséről, tekintse meg [a Windows rendszerű számítógépek általános felügyeleti feladatait a Microsoft Intune számítógép-ügyféllel](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)című témakört.

    A következő szakasz felsorolja a házirendben konfigurálható értékeket, valamint azokat az alapértelmezett értékeket is, amelyeket a rendszer akkor használ, ha nem szabja testre a házirendet.

Miután telepített egy Windows tűzfal-házirendet, megtekintheti annak állapotát a **házirend** munkaterület **minden házirend** lapján.

## <a name="specify-policy-settings-for-windows-firewall"></a>A Windows tűzfal házirend-beállításainak megadása

### <a name="turn-on-windows-firewall"></a>A Windows tűzfal bekapcsolása

Ezekkel a házirend-beállításokkal engedélyezheti a Windows tűzfalat a következő felügyelt számítógépeken:
- Csatlakoztatva van egy tartományhoz (például a munkahelyen)
- Csatlakoztatva van egy magánhálózati (megbízható) hálózathoz (például otthoni hálózathoz)
- Nem megbízható nyilvános hálózathoz (például egy kávézóhoz) csatlakozik

Az egyes beállítások alapértelmezett értéke **Igen**, ez a legbiztonságosabb érték.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Az összes bejövő kapcsolat tiltása, az engedélyezett programok listáján szereplőket is beleértve

Ezek a házirend-beállítások a Windows tűzfalat úgy konfigurálja, hogy blokkolja a bejövő hálózati forgalmat a következő felügyelt számítógépeken:
- Csatlakoztatva van egy tartományhoz (például a munkahelyen)
- Csatlakoztatva van egy magánhálózati (megbízható) hálózathoz (például otthoni hálózathoz)
- Nem megbízható nyilvános hálózathoz (például egy kávézóhoz) csatlakozik

Az egyes beállítások alapértelmezett értéke **Igen**, ez a legbiztonságosabb érték.

> [!IMPORTANT]
> Ha a környezet szervizcsomag nélküli Windows Vista rendszerű felügyelt számítógépeket is tartalmaz, akkor telepítenie kell a Microsoft Tudásbázis 971800-es [cikkében](https://go.microsoft.com/fwlink/?LinkId=188405) társított frissítést, vagy le kell tiltania az **összes bejövő blokkolást.** az adott számítógépekre telepített házirendek kapcsolatainak házirend-beállításai.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>A felhasználó értesítése, ha a Windows tűzfal új programot blokkol

Ezek a házirend-beállítások határozzák meg, hogy a Windows tűzfal értesítse-e a számítógép felhasználóit, ha a felügyelt számítógép a következő esetekben blokkolja a bejövő hálózati forgalmat:
- Csatlakoztatva van egy tartományhoz (például a munkahelyen)
- Csatlakoztatva van egy magánhálózati (megbízható) hálózathoz (például otthoni hálózathoz)
- Nem megbízható nyilvános hálózathoz (például egy kávézóhoz) csatlakozik

Az egyes beállítások alapértelmezett értéke **Igen**.


### <a name="configure-predefined-exceptions"></a>Előre definiált kivételek konfigurálása

A korábban konfigurált értékektől függetlenül olyan kivételeket is beállíthat, amelyek engedélyezik a tűzfalon keresztül megadott típusú hálózati forgalmat. Alapértelmezés szerint a beállítások egyike sincs konfigurálva.

|Beállítás neve|Részletek|
|------------------|--------------------|
|**BranchCache – tartalom lekérése**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára, hogy a HTTP használatával beolvassák a más BranchCache-ügyfelektől származó tartalmat elosztott módban, illetve a központi gyorsítótárból a kihelyezett gyorsítótáras módban. Ez a beállítás HTTP protokollt használ.|
|**BranchCache – központi gyorsítótár ügyfele**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára a kihelyezett gyorsítótár használatát. A beállítás HTTPS protokollt használ.|
|**BranchCache – központi gyorsítótár kiszolgálója**|Lehetővé teszi a BranchCache-ügyfelek számára a kihelyezett gyorsítótár használatát más ügyfelekkel való kommunikációhoz. A beállítás HTTPS protokollt használ.|
|**BranchCache – társ-felderítés**<br>(Windows 7 vagy újabb)|Lehetővé teszi a BranchCache-ügyfelek számára a Web Services Dynamic Discovery (WS-Discovery) protokoll használatával megkeresni a tartalom elérhetőségét a helyi alhálózaton.|
|**BITS gyorsítótárazás**|Lehetővé teszi, hogy az ügyfelek Háttérben futó intelligens átviteli szolgáltatás (BITS) használatával megkeressék és megosszák a BITS-gyorsítótárban tárolt fájlokat ugyanazon az alhálózaton lévő ügyfeleken. Ez a beállítás a Web Services on Devices (WSDAPI) és a távoli eljáráshívás (RPC) szolgáltatást használja.|
|**Kapcsolódás hálózati kivetítőhöz**|Lehetővé teszi a felhasználók számára, hogy vezetékes vagy vezeték nélküli hálózatokon keresztül csatlakozhassanak a kivetítőhöz a Project bemutatók számára. Ez a beállítás a WSDAPI-t használja.|
|**Központi hálózatkezelés**|Lehetővé teszi, hogy az ügyfelek IPv4-és IPv6-kapcsolatot használjanak a hálózati erőforrásokhoz való kapcsolódáshoz.|
|**Elosztott tranzakciók koordinátora**|Lehetővé teszi a felügyelt számítógépek számára, hogy összehangolják a tranzakció által védett erőforrásokat, például adatbázisokat, üzenetsor-várólistákat és fájlrendszereket frissítő tranzakciókat.|
|**Fájl-és nyomtatómegosztás**|Lehetővé teszi a felhasználók számára a helyi fájlok és nyomtatók megosztását a hálózaton lévő többi felhasználóval. Ez a beállítás a NetBIOS protokollt, a helyi csoportos küldés névfeloldását (LLMNR), a Server Message Block (SMB) protokollt és az RPC-t használja.|
|**Otthoni csoport**<br>(Windows 7 vagy újabb)|Lehetővé teszi, hogy a felügyelt számítógépek részt vegyenek az otthoni csoport hálózatában.|
|**iSCSI szolgáltatás**|Lehetővé teszi a felügyelt számítógépek számára az iSCSI-kiszolgálókhoz és-eszközökhöz való kapcsolódást.|
|**Kulcskezelő szolgáltatás**|Lehetővé teszi a számítógépek számára a licencek megfelelőségének megszámlálását a vállalati környezetekben.|
|**Media Center Extender készülékek**|Lehetővé teszi a Media Center Extender készülékek számára a Windows Media Centert futtató számítógépekkel való kommunikációt. A beállítás egyszerű Service Discovery protokollt (SSDP) és qWave használ.|
|**Netlogon szolgáltatás**|Egy biztonsági csatornát konfigurál a tartományi ügyfelek és a tartományvezérlők között a felhasználók és a szolgáltatások hitelesítéséhez. Ez a beállítás RPC protokollt használ.|
|**Hálózatfelderítés**|Lehetővé teszi, hogy a számítógépek felfedezzék más eszközöket, és a hálózaton lévő más eszközök is felderítsék őket. Ez a beállítás a Function Discovery Host és a közzétételi szolgáltatások, az SSDP, a NetBIOS, a LLMNR és az UPnP hálózati protokollok használatát használja.|
|**Teljesítménynaplók és riasztások**|Lehetővé teszi, hogy a Teljesítménynaplók és riasztások szolgáltatás távolról felügyelhető legyen. Ez a beállítás RPC protokollt használ.|
|**Távfelügyeleti**|Engedélyezi a számítógép távoli felügyeletét.|
|**Távsegítség**|Lehetővé teszi a felügyelt számítógépek felhasználói számára, hogy távsegítséget kérjenek más felhasználóktól a hálózaton. A beállítás SSDP, Peer Name Resolution Protocol (PNRP), Teredo és UPnP hálózati protokollt használ.|
|**Távoli asztal**|Lehetővé teszi, hogy a számítógép a Távoli asztal használatával hozzáférjen más számítógépekhez.|
|**Eseménynapló távoli kezelése**|Lehetővé teszi az ügyfelek eseménynaplóinak távoli megtekintését és kezelését. Ez a beállítás nevesített csöveket és RPC protokollt használ.|
|**Ütemezett feladatok távoli felügyelete**|Lehetővé teszi a Feladatütemező szolgáltatás távoli kezelését. Ez a beállítás RPC protokollt használ.|
|**Távoli szolgáltatások kezelése**|Lehetővé teszi az ügyfelek helyi szolgáltatásainak távoli kezelését. Ez a beállítás nevesített csöveket és RPC protokollt használ.|
|**Távoli kötetek kezelése**|Lehetővé teszi a távoli szoftverek és a hardveres lemezek mennyiségi felügyeletét. Ez a beállítás RPC protokollt használ.|
|**Útválasztás és távelérés**|Engedélyezi a bejövő VPN-és távelérési kapcsolatok használatát a számítógépeken.|
|**Biztonságos szoftvercsatorna-bújtatási protokoll**|Engedélyezi a bejövő VPN-kapcsolatokat a felügyelt számítógépeken az SSTP protokollal. A beállítás HTTPS protokollt használ.|
|**SNMP-trap**|Lehetővé teszi a felügyelt számítógépek számára Simple Network Management Protocol (SNMP) trap szolgáltatás forgalmának fogadását.|
|**UPnP-keretrendszer**|A számítógépeken konfigurálja a UPnP-keretrendszer szolgáltatást, hogy azok felfedezzék és használhassák az UPnP tanúsítvánnyal rendelkező eszközöket.|
|**Windows együttműködés számítógépnév-regisztrációs szolgáltatása**|Lehetővé teszi, hogy a számítógépek az SSDP és a PNRP használatával keressenek és kommunikáljanak más számítógépekkel.|
|**Windows Media Player**|Lehetővé teszi, hogy a felhasználók az UDP protokollon keresztül fogadják az adatfolyamot.|
|**Windows Media Player hálózati megosztási szolgáltatás**|Lehetővé teszi, hogy a felhasználók médiatartalmakat osszanak meg a hálózaton. A beállítás SSDP, qWave és UPnP hálózati protokollt használ.|
|**Windows Media Player hálózati megosztási szolgáltatás (Internet)**<br>(Windows 7 vagy újabb)|Lehetővé teszi a felhasználóknak az otthoni médiatartalmak megosztását az interneten.|
|**Windows Tárgyaló**|Lehetővé teszi, hogy a felhasználók a hálózaton keresztül működjenek együtt a dokumentumok, a programok és az asztali számítógépek megosztásához. Ez a beállítás elosztott fájlrendszer replikációt (DFSR) és a P2P-t használja.|
|**Windows társközi együttműködési alaprendszer**|Különböző társközi programokat és technológiákat konfigurál, amelyek lehetővé teszik a kapcsolódást. A beállítás SSDP és PNRP protokollt használ.|
|**Rendszerfelügyeleti webszolgáltatások (kompatibilitás)**|Lehetővé teszi a felügyelt számítógépek távoli felügyeletét a WS-Management szolgáltatással, egy webszolgáltatáson alapuló protokollt az operációs rendszerek és eszközök távoli felügyeletéhez.|
|**Rendszerfelügyeleti webszolgáltatások**<br>(Windows 8 vagy újabb)|Lehetővé teszi a felügyelt számítógépek távoli felügyeletét a WS-Management szolgáltatással, egy webszolgáltatáson alapuló protokollt az operációs rendszerek és eszközök távoli felügyeletéhez.|
|**Windows rendszerű virtuális számítógép**<br>(Windows 7 vagy újabb)|Lehetővé teszi, hogy a virtuális gépek kommunikáljanak más számítógépekkel.|
|**Vezeték nélküli hordozható eszközök**|Lehetővé teszi az adathordozó átvitelét hálózati kameráról vagy adathordozóról az MTP protokollt használó felügyelt számítógépekre. A beállítás SSDP és UPnP hálózati protokollt használ.|

## <a name="see-also"></a>Lásd még:
[Szabályzatok a Windows rendszerű számítógépek védelmét](policies-to-protect-windows-pcs-in-microsoft-intune.md)
