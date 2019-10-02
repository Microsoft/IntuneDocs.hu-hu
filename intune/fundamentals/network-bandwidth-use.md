---
title: A Microsoft Intune hálózati követelményei és sávszélességi adatai
titleSuffix: ''
description: Az Intune hálózati konfigurációja követelményeinek és a sávszélességi adatainak áttekintése.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b4983031d0e5d0723e306a1b9cbefadac2f91fe
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732231"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune – a hálózati konfiguráció követelményei és sávszélessége

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Ezekkel az információkkal megismerheti az Intune-beli üzemelő példányok sávszélességre vonatkozó követelményeit.

## <a name="average-network-traffic"></a>Átlagos hálózati forgalom
A táblázat az egyes ügyfelek esetében a hálózaton áthaladó általános tartalmak hozzávetőleges méretét és gyakoriságát tartalmazza.

> [!NOTE]
> Annak biztosítása érdekében, hogy az eszközök megkapják a frissítéseket és a tartalmakat az Intune-ból, rendszeresen kapcsolódniuk kell az internethez. A frissítések vagy tartalmak fogadásához szükséges idő változó lehet, de az eszközöket minden nap legalább egy óráig folyamatosan az internethez csatlakoztatva kell tartani.

|Tartalom típusa|Hozzávetőleges méret|Gyakoriság és részletek|
|----------------|--------------------|-------------------------|
|Intune-ügyfél telepítése<br /><br />**Az alábbi követelmények az Intune-ügyfél telepítésén kívül értendők**|125 MB|**Egy alkalommal**<br /><br />Az ügyfél letöltési mérete az adott ügyfélszámítógép operációs rendszerétől függ.|
|Ügyfélregisztrációs csomag|15 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Endpoint Protection-ügynök|65 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Operations Manager-ügynök|11 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Házirendügynök|3 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|A Távsegítség a Microsoft Easy Assist használatával szolgáltatás ügynöke|6 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Ügyfél napi szintű működése|6 MB|**Naponta**<br /><br />Az Intune-ügyfél rendszeresen kommunikál az Intune szolgáltatással, hogy ellenőrizze a frissítéseket és a szabályzatokat, és jelentse az ügyfél állapotát a szolgáltatásnak.|
|Az Endpoint Protection szolgáltatás kártevő-definícióinak frissítései|Változó<br /><br />Általában 40 KB és 2 MB között|**Naponta**<br /><br />Naponta legfeljebb három alkalommal.|
|Az Endpoint Protection motor frissítése|5 MB|**Havonta**|
|Szoftverfrissítések|Változó<br /><br />A méret a telepített frissítésektől függ.|**Havonta**<br /><br />Általában minden hónap második keddjén jelennek meg szoftverfrissítések.<br /><br />Az újonnan regisztrált vagy telepített számítógépek a korábban kiadott frissítések teljes készletének letöltésével több hálózati sávszélességet használhatnak.|
|Szervizcsomagok|Változó<br /><br />Az egyes telepített szervizcsomagok mérete változó.|**Változó**<br /><br />A szervizcsomagok telepítésének idejétől függ.|
|Szoftverterjesztés|Változó<br /><br />A méret a telepített szoftverektől függ.|**Változó**<br /><br />A szoftverek telepítésének idejétől függ.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>A hálózatisávszélesség-felhasználás csökkentésének módjai
Az alábbi eljárások közül egynek vagy többnek az alkalmazásával csökkenthető az Intune-ügyfelek által felhasznált hálózati sávszélesség.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Proxykiszolgáló használata a tartalomkérelmek gyorsítótárazásához
A proxykiszolgálók képesek gyorsítótárazni a tartalmakat, amivel csökkenthető az ismétlődő letöltések és az internetről származó tartalmakhoz felhasznált hálózati sávszélesség mennyisége.

Az ügyfelek tartalomkéréseit fogadó gyorsítótárazási proxykiszolgálók be tudják olvasni a megfelelő tartalmakat, és képesek gyorsítótárazni a webes válaszokat és a letöltéseket is. A kiszolgáló az ügyfelek későbbi kérelmeire a gyorsítótárazott adatok alapján ad választ.

Az alábbiakban az Intune-ügyfelek számára tartalmakat gyorsítótárazó proxykiszolgálókhoz használható tipikus beállítások láthatók.


|          Beállítás           |           Javasolt érték           |                                                                                                  Részletek                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Gyorsítótár mérete         |             5 GB-tól 30 GB-ig             | Az érték a hálózatban lévő ügyfélszámítógépek számától és a használt beállításoktól függ. A fájlok túl korai törlésének elkerülése érdekében a gyorsítótár mérete a környezethez igazítható. |
| Egyedi gyorsítótárfájlok mérete |                950 MB                 |                                                                     Ez a beállítás nem feltétlenül érhető el minden gyorsítótárazási proxykiszolgálón.                                                                     |
|   Gyorsítótárazandó objektumtípusok    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Az Intune-csomagok olyan CAB-fájlok, amelyeket a Háttérben futó intelligens átviteli szolgáltatás (BITS) tölt le HTTP protokollal.                                               |
> [!NOTE]
> Ha proxykiszolgálót használ a tartalmi kérések gyorsítótárazásához, a kommunikációt csak az ügyfél és a proxy, illetve a proxy és az Intune között titkosítja a rendszer. Az ügyfél és az Intune közötti kapcsolatok nem lesznek teljes körűen titkosítva.

A proxykiszolgálók tartalmak gyorsítótárazására való használatával kapcsolatos további tudnivalókat a proxykiszolgáló-megoldása dokumentációjában találhat.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Háttérben futó intelligens átviteli szolgáltatás (BITS) használata a számítógépeken
A konfigurált órákban a Windows rendszerű számítógépek BITS szolgáltatásával csökkentheti a hálózati sávszélességet. A BITS-szabályzatot az Intune-ügynök házirendjének **hálózati sávszélesség** lapján állíthatja be.

> [!NOTE]
> A Windows MDM-kezeléséhez a MobileMSI csak az operációs rendszer felügyeleti felülete használ BITS-t a letöltéshez. A AppX/MsiX a saját, nem BITS-letöltési verem-és Win32-alkalmazásokat az Intune-ügynökön keresztül a BITS helyett kézbesítési optimalizálással használják.

A BITS Windows rendszerű számítógépeken való használatáról a TechNet könyvtár a [Háttérben futó intelligens átviteli szolgáltatással foglalkozó témakörében](https://technet.microsoft.com/library/bb968799.aspx) olvashat bővebben.

### <a name="delivery-optimization"></a>Kézbesítési optimalizálás
A kézbesítés optimalizálása lehetővé teszi, hogy az Intune használatával csökkentse a sávszélesség-használatot, amikor a Windows 10-es eszközök letöltik az alkalmazásokat és a frissítéseket. A saját szervezésű elosztott gyorsítótár használatával a letöltések a hagyományos kiszolgálókról és más forrásokból (például hálózati társokból) tölthetők le.

A kézbesítési optimalizálás által támogatott Windows 10-es verziók és tartalomtípusok teljes listájának megtekintéséhez tekintse meg a [Windows 10-es frissítések kézbesítésének optimalizálásával foglalkozó cikket](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements).

Az eszköz konfigurációs profiljainak részeként [beállíthatja a kézbesítés optimalizálását](../configuration/delivery-optimization-settings.md) .


### <a name="use-branchcache-on-computers"></a>A BranchCache használata a számítógépeken
Az Intune-ügyfeleken a BranchCache szolgáltatással is csökkenthető a nagykiterjedésű hálózati (WAN) forgalom. A következő operációs rendszerek támogatják a BranchCache használatát:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

A BranchCache használatához az ügyfélszámítógépen engedélyezni kell a BranchCache-t, majd az **elosztott gyorsítótáras módot** kell beállítani rajta.

Ha az Intune-ügyfél telepítve van a számítógépekre, a BranchCache és az elosztott gyorsítótáras mód alapértelmezés szerint engedélyezve van. Ha azonban Csoportházirend letiltotta a BranchCache-t, az Intune nem bírálja felül ezt a házirendet, és a BranchCache le lesz tiltva.

A BranchCache használatakor a szervezet más rendszergazdáival együttműködve kezeljék a Csoportházirendet és az Intune-tűzfalházirendet. Győződjön meg arról, hogy nem telepítik a BranchCache-vagy tűzfal-kivételeket letiltó házirendet. A BranchCache-sel kapcsolatban bővebben lásd: [BranchCache Overview](https://technet.microsoft.com/library/hh831696.aspx) (A BranchCache áttekintése).

> [!NOTE]
> A Microsoft Intune segítségével kezelheti a Windows rendszerű számítógépeket mobileszköz- [felügyeleti (Mdm)](../enrollment/windows-enroll.md) vagy Intune-ügyfélszoftverrel rendelkező számítógépekként. A Microsoft azt javasolja, hogy az ügyfelek, amikor csak lehetséges, [a Mdm-kezelési megoldást használják](../enrollment/windows-enroll.md) . Ha ezt a módszert felügyeli, a BranchCache nem támogatott. További információ: a [Windows rendszerű számítógépek számítógépként vagy mobileszközökként való kezelésének összehasonlítása](../pc-management-comparison.md).


## <a name="next-steps"></a>További lépések

[Az Intune-végpontok áttekintése](../intune-endpoints.md)

