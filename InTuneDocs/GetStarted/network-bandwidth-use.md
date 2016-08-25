---
title: "Az Intune hálózatisávszélesség-felhasználása | A Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: e104dc52a8a9bdda4b2edb2939d8c7c36e8ecc12


---

# Az Intune hálózatisávszélesség-felhasználása

A [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] beállítása előtt olvassa el ezt a témakört, valamint ismerkedjen meg a [Tudnivalók a Microsoft Intune elindítása előtt](what-to-know-before-you-start-microsoft-intune.md) című témakörben leírt követelményekkel.

Az alábbiakban megadott információk segítségével tervezhető a [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]-ügyfelek hálózati forgalma.

## Átlagos hálózati forgalom
Az alábbi táblázat az egyes ügyfelek esetén a hálózaton áthaladó általános tartalmak hozzávetőleges méretét és gyakoriságát tartalmazza.

> [!NOTE]
> Annak biztosítására, hogy a számítógépek és mobileszközök megkapják a szükséges frissítéseket és tartalmakat az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] szolgáltatástól, azoknak rendszeresen kapcsolódnia kell az internethez. A frissítések vagy tartalmak fogadásához szükséges idő változó, de az eszközöket ajánlott minden nap legalább 1 óráig folyamatosan az internethez csatlakoztatva tartani.

|Tartalom típusa|Hozzávetőleges méret|Gyakoriság és részletek|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] -ügyfél telepítése<br /><br />**Az alábbi követelmények az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ügyfél telepítésén kívül értendők**|125 MB|**Egy alkalommal**<br /><br />Az ügyfél letöltési mérete az adott ügyfélszámítógép operációs rendszerétől függ.|
|Ügyfélregisztrációs csomag|15 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Endpoint Protection-ügynök|65 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Operations Manager-ügynök|11 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Házirendügynök|3 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|A Távsegítség a Microsoft Easy Assist használatával szolgáltatás ügynöke|6 MB|**Egy alkalommal**<br /><br />További letöltések is előfordulhatnak, ha frissítések érhetők el ehhez a tartalomtípushoz.|
|Ügyfél napi szintű működése|6 MB|**Naponta**<br /><br />Az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ügyfél rendszeresen kommunikál az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] szolgáltatással, hogy ellenőrizze a frissítéseket és a házirendeket, és hogy jelentse az ügyfél állapotát a szolgáltatásnak.|
|Az Endpoint Protection szolgáltatás kártevő-definícióinak frissítései|Változó<br /><br />Általában 40 KB és 2 MB között|**Naponta**<br /><br />Naponta legfeljebb három alkalommal.|
|Az Endpoint Protection motor frissítése|5 MB|**Havonta**|
|Szoftverfrissítések|Változó<br /><br />A méret a telepített frissítésektől függ.|**Havonta**<br /><br />Általában minden hónap második keddjén jelennek meg szoftverfrissítések.<br /><br />Az újonnan regisztrált vagy telepített számítógépek a korábban kiadott frissítések teljes készletének letöltésével több hálózati sávszélességet használhatnak.|
|Szervizcsomagok|Változó<br /><br />Az egyes telepített szervizcsomagok mérete változó.|**Változó**<br /><br />A szervizcsomagok telepítésének idejétől függ.|
|Szoftverterjesztés|Változó<br /><br />A méret a telepített szoftverektől függ.|**Változó**<br /><br />A szoftverek telepítésének idejétől függ.|

## A hálózatisávszélesség-felhasználás csökkentésének módjai
Az alábbi eljárások közül egy vagy több alkalmazásával csökkenthető az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ügyfelek által felhasznált hálózati sávszélesség.

### Proxykiszolgáló használata a tartalomkérelmek gyorsítótárazásához
A tartalmak egy proxykiszolgálóval való gyorsítótárazásával csökkenthető az ismétlődő letöltések mennyisége és az internetről tartalmat igénylő ügyfelek által felhasznált hálózati sávszélesség.

A gyorsítótárazási proxykiszolgáló fogadja a hálózaton lévő ügyfélszámítógépek tartalomkérelmeit, beszerzi ezeket a tartalmakat az interneten, és ezután a HTTP-válaszokat és a bináris letöltéseket is képes gyorsítótárazni. A kiszolgáló a gyorsítótárban lévő adatokkal válaszolja meg az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ügyfélszámítógépektől érkező későbbi kérelmeket.

Az alábbiakban az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ügyfelek számára tartalmakat gyorsítótárazó proxykiszolgálókhoz használható tipikus beállítások láthatók.

|Beállítás|Javasolt érték|Részletek|
|-----------|---------------------|-----------|
|Gyorsítótár mérete|5 GB-tól 30 GB-ig|Az érték a hálózatban lévő ügyfélszámítógépek számától és a használt beállításoktól függ. A fájlok túl korai törlésének elkerülése érdekében a gyorsítótár mérete a környezethez igazítható.|
|Egyedi gyorsítótárfájlok mérete|950 MB|Ez a beállítás nem feltétlenül érhető el minden gyorsítótárazási proxykiszolgálón.|
|Gyorsítótárazandó objektumtípusok|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] -csomagok olyan CAB-fájlok, melyeket a rendszer a HTTP protokollon keresztül szerez be a Háttérben futó intelligens átviteli szolgáltatással (BITS) végzett letöltéssel.|
A proxykiszolgálók tartalmak gyorsítótárazására való használatával kapcsolatos további tudnivalókat a proxykiszolgáló-megoldása dokumentációjában találhat.

### A Háttérben futó intelligens átviteli szolgáltatás használata a számítógépeken
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] a beállított időszakokban felhasznált hálózati sávszélesség csökkentése érdekében támogatja a Háttérben futó intelligens átviteli szolgáltatás (BITS) használatát a Windows rendszerű számítógépeken. A BITS szolgáltatáshoz az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ügynök házirendjének **Hálózati sávszélesség** lapján állíthat be házirendet.

A BITS Windows rendszerű számítógépeken való használatáról a TechNet könyvtár a [Háttérben futó intelligens átviteli szolgáltatással foglalkozó témakörében](http://technet.microsoft.com/library/bb968799.aspx) olvashat bővebben.

### A BranchCache használata a számítógépeken
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] -ügyfeleken a BranchCache szolgáltatás használatával is csökkenthető a nagykiterjedésű hálózati (WAN) forgalom. A következő, ügyfélként is támogatott operációs rendszerek támogatják a BranchCache szolgáltatást is:

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

A BranchCache használatához az ügyfélszámítógépen engedélyezni kell a BranchCache-t, majd az **elosztott gyorsítótáras módot** kell beállítani rajta.

A BranchCache és az elosztott gyorsítótáras mód alapértelmezés szerint engedélyezve van azokon a számítógépeken, melyeken telepítve van az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-ügyfél. Ha azonban az ügyfél már rendelkezik egy, a BranchCache szolgáltatást letiltó csoportházirenddel, az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] nem bírálja felül ezt a házirendet, és a BranchCache ezen a számítógépen letiltva marad.

A BranchCache használatakor lépjen kapcsolatba a szervezet más, a Csoportházirendet és a [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] tűzfalházirendjét kezelő rendszergazdákkal annak biztosítására, hogy ne alkalmazzanak a BranchCache szolgáltatást vagy a tűzfalkivételeket letiltó házirendeket. A BranchCache-sel kapcsolatban bővebben lásd: [BranchCache Overview](http://technet.microsoft.com/library/hh831696.aspx) (A BranchCache áttekintése).

### További információ
[Tudnivalók a Microsoft Intune elindítása előtt](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=Jun16_HO4-->


