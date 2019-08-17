---
title: macOS-eszköz funkciójának beállításai a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg a macOS-eszközök AirPrint való konfigurálásának beállításait, és szabja testre a bejelentkezési ablakot a Microsoft Intune lévő főkapcsoló gombok megjelenítéséhez vagy elrejtéséhez. Tekintse meg a AirPrint-kiszolgáló IP-címének, elérési útjának és portbeállítások beszerzésének lépéseit a hálózaton. Ezeket a beállításokat egy eszköz konfigurációs profiljában a macOS-eszközök funkcióinak konfigurálásához használhatja.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63f2832dd321425efe8092f1bb12dd0d479ef71b
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69549934"
---
# <a name="macos-device-feature-settings-in-intune"></a>macOS-eszköz funkciójának beállításai az Intune-ban

Az Intune tartalmaz néhány beépített beállítást a macOS-eszközök funkcióinak testreszabásához. Ez a cikk felsorolja ezeket a beállításokat, és leírja az egyes beállításokat. Emellett felsorolja azokat a lépéseket, amelyekkel lekérheti a AirPrint-nyomtatók IP-címét, elérési útját és portját a Terminal app (Emulator) használatával.

Ez a funkció az alábbiakra vonatkozik:

- macOS

A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal létrehozhat egy szalagcímet, kiválaszthatja a felhasználók bejelentkezésének módját, a AirPrint-kiszolgáló hozzáadását és egyebeket.

Ezek a beállítások hozzáadódnak az Intune-ban lévő eszköz konfigurációs profiljához, majd a macOS-eszközökhöz vannak rendelve vagy telepítve.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy MacOS-eszköz konfigurációs profilt](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **IP-cím**: Adja meg a nyomtató IPv4-vagy IPv6-címeit. Ha állomásneveket használ a nyomtatók azonosítására, akkor az IP-címet a nyomtatónak a terminál alkalmazásban történő pingelésével érheti el. [Az IP-cím és az elérési út](#get-the-ip-address-and-path) lekérése (ebben a cikkben) további részleteket tartalmaz.
- **Elérési út**: Adja meg a nyomtató elérési útját. Az elérési út `ipp/print` általában a hálózatban lévő nyomtatókhoz van. [Az IP-cím és az elérési út](#get-the-ip-address-and-path) lekérése (ebben a cikkben) további részleteket tartalmaz.
- **Port** (iOS 11,0 és újabb verziók): Adja meg a AirPrint célhelyének figyelési portját. Ha üresen hagyja ezt a tulajdonságot, a AirPrint az alapértelmezett portot használja.
- **TLS** (iOS 11,0 és újabb verziók): Válassza az **Engedélyezés** lehetőséget a AirPrint-kapcsolatok TRANSPORT Layer Security (TLS) használatával történő biztonságossá tételéhez.

**Hozzáadás** A AirPrint-kiszolgáló. Több AirPrint-kiszolgálót is hozzáadhat.

- **Importálás** (nem kötelező): Importálhat egy vesszővel tagolt (. csv) fájlt is, amely tartalmazza a AirPrint-nyomtatók listáját. Emellett a AirPrint-nyomtatók Intune-ban való hozzáadása után **exportálhatja** a listát.

A beállítások mentéséhez kattintson **az OK gombra** .

### <a name="get-the-ip-address-and-path"></a>Az IP-cím és az elérési út lekérése

AirPrinter-kiszolgálók hozzáadásához szüksége lesz a nyomtató IP-címére, az erőforrás elérési útjára és a portra. Az alábbi lépések bemutatják, hogyan kérheti le ezeket az információkat.

1. Olyan Mac gépen, amely ugyanahhoz a helyi hálózathoz (alhálózat) csatlakozik, mint a AirPrint-nyomtatók, nyissa meg a terminált (a **/Applications/Utilities alatt**).
2. A terminál alkalmazásban írja be `ippfind`a parancsot, majd kattintson az ENTER (bevitel) gombra.

    Jegyezze fel a nyomtató adatait. Előfordulhat például, hogy a `ipp://myprinter.local.:631/ipp/port1`következőhöz hasonló értéket ad vissza:. Az első rész a nyomtató neve. Az utolsó rész (`ipp/port1`) az erőforrás elérési útja.

3. A terminálon írja be `ping myprinter.local`a parancsot, majd kattintson az ENTER (bevitel) gombra.

   Jegyezze fel az IP-címet. Előfordulhat például, hogy a `PING myprinter.local (10.50.25.21)`következőhöz hasonló értéket ad vissza:.

4. Használja az IP-cím és az erőforrás elérési útjának értékét. Ebben a példában az IP-cím `10.50.25.21`, az erőforrás elérési útja pedig. `/ipp/port1`

## <a name="login-items"></a>Bejelentkezési elemek

- **Fájlok, mappák és egyéni alkalmazások**: **Adja** meg a megnyitni kívánt fájl, mappa, egyéni alkalmazás vagy rendszeralkalmazás elérési útját, amikor egy felhasználó bejelentkezik az eszközre. A szervezete számára létrehozott vagy testre szabott rendszeralkalmazások vagy alkalmazások általában a `Applications` mappában találhatók, a következőhöz `/Applications/AppName.app`hasonló elérési úttal. 

  Számos fájlt, mappát és alkalmazást adhat hozzá. Írja be például a következőt:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Ha bármilyen alkalmazást, mappát vagy fájlt ad hozzá, ügyeljen arra, hogy a helyes elérési utat adja meg. Nem minden elem szerepel a `Applications` mappában. Ha a felhasználó egy elemet helyez át egyik helyről a másikra, az elérési út megváltozik. Ez az áthelyezett tétel nem nyílik meg, amikor a felhasználó bejelentkezik.

## <a name="login-window"></a>Bejelentkezési ablak

### <a name="window-layout"></a>Ablak elrendezése

- **További információk megjelenítése a menüsorban**: Ha a menüsorban az időszak van kiválasztva, az **Engedélyezés** megjeleníti az állomásnév és a MacOS verzióját. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg ezeket az információkat a menüsávon.
- **Szalagcím**: Adja meg az eszköz bejelentkezési képernyőjén látható üzenetet. Adja meg például a szervezeti adatokat, egy üdvözlő üzenetet, az elveszett és a talált információkat, és így tovább.
- **Adja meg a bejelentkezési formátumot**: Válassza ki, hogyan jelentkeznek be a felhasználók az eszközre. A választható lehetőségek:
  - **Felhasználónév és jelszó kérése** (alapértelmezett): Felhasználónevet és jelszót kell megadnia a felhasználóknak.
  - **Az összes felhasználó listázása, jelszó kérése**: A felhasználóknak a felhasználónevet a felhasználói listából kell kiválasztaniuk, majd meg kell adniuk a jelszavukat. Konfigurálja a következőket is:

    - **Helyi felhasználók**: Az **Elrejtés** nem jeleníti meg a felhasználók listájában a helyi felhasználói fiókokat, amelyek magukban foglalhatják a standard és a rendszergazdai fiókokat. Csak a hálózat és a rendszer felhasználói fiókjai jelennek meg. **Nincs konfigurálva** (alapértelmezés) megjeleníti a helyi felhasználói fiókokat a felhasználók listájában.
    - **Mobile-fiókok**: Az **Elrejtés** nem jeleníti meg a mobil fiókokat a felhasználók listájában. **Nincs konfigurálva** (alapértelmezés) megjeleníti a felhasználói listán szereplő mobil fiókokat. Egyes Mobile-fiókok hálózati felhasználóként jelenhetnek meg.
    - **Hálózati felhasználók**: Válassza a **Megjelenítés** lehetőséget a felhasználók listájában szereplő hálózati felhasználók listázásához. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a hálózati felhasználói fiókokat a felhasználók listájában.
    - **Rendszergazda felhasználók**: Az **Elrejtés** nem jeleníti meg a rendszergazdai felhasználói fiókokat a felhasználók listájában. **Nincs konfigurálva** (alapértelmezés) a felhasználók listájában a rendszergazdai felhasználói fiókokat jeleníti meg.
    - **Egyéb felhasználók**: Válassza a **Megjelenítés** elemet a felhasználók listájának **más...** felhasználóinak listázásához. **Nincs konfigurálva** (alapértelmezés) nem jeleníti meg a többi felhasználói fiókot a felhasználók listájában.

### <a name="login-screen-power-settings"></a>Bejelentkezési képernyő energiagazdálkodási beállításai

- **Leállítás gomb**: Az **Elrejtés** gomb nem jelenik meg a bejelentkezési képernyő leállítás gombjával. **Nincs konfigurálva** (alapértelmezés) megjeleníti a Leállítás gombot.
- **Újraindítás gomb**: Az **Elrejtés** gomb nem jeleníti meg az újraindítás gombot a bejelentkezési képernyőn. **Nincs konfigurálva** (alapértelmezés) az újraindítás gombot jeleníti meg.
- **Alvó gomb**: Az **Elrejtés** gomb nem jeleníti meg az alvó gombot a bejelentkezési képernyőn. **Nincs konfigurálva** (alapértelmezés) az alvó gomb megjelenítése.

### <a name="other"></a>Egyéb

- **Felhasználói bejelentkezés letiltása a konzolról**: A **Letiltás letiltja** a bejelentkezéshez használt MacOS-parancssort. A tipikus felhasználók esetében **Tiltsa le** ezt a beállítást. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi, hogy a haladó felhasználók a macOS parancssor használatával jelentkezzenek be. A konzol mód megadásához a `>console` felhasználók a Felhasználónév mezőbe lépnek be, és a konzol ablakban kell hitelesíteniük magukat.

### <a name="apple-menu"></a>Apple menü

Miután a felhasználók bejelentkeznek az eszközökre, a következő beállítások befolyásolhatják, hogy milyen műveleteket végezhetnek el.

- **Leállítás letiltása**: A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a **Leállítás** lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználóknak az eszköz **Leállítás** menüpontjának kiválasztását.
- **Újraindítás letiltása**: A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek az újraindítási lehetőség választásával. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára az újraindítási menüelem kiválasztását az eszközön.
- Kikapcsolás **letiltása**: A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a kikapcsolás lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára , hogy kiválassza a kikapcsolt menüelemet az eszközön.
- Kijelentkezés **letiltása** (macOS 10,13 és újabb verziók): A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a kijelentkezés lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára a kijelentkezés menüpont kiválasztását az eszközön.
- **Zárolási képernyő letiltása** (macOS 10,13 és újabb verziók): A **Letiltás** beállítás megadásával megakadályozható, hogy a felhasználók bejelentkeznek a **zárolási képernyő** lehetőséggel. **Nincs konfigurálva** (alapértelmezés) lehetővé teszi a felhasználók számára, hogy kiválassza a **zárolási képernyő** menüelemét az eszközön.

A beállítások mentéséhez kattintson **az OK gombra** .

## <a name="next-steps"></a>További lépések

- Az [iOS](ios-device-features-settings.md) -eszközök összes beállításának megtekintése.
- [Rendelje hozzá a profilt](device-profile-assign.md) a csoportokhoz, és [Figyelje annak állapotát](device-profile-monitor.md).
