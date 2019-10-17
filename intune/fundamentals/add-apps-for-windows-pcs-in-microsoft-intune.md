---
title: Az Intune szoftverügyfelet futtató Windows rendszerű számítógépes alkalmazások hozzáadása
titleSuffix: Microsoft Intune
description: Ebből a témakörből megtudhatja, hogyan adhat hozzá Windows rendszerű számítógépes alkalmazásokat az Intune-hoz a központi telepítésük előtt.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/29/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 23868303d598be1bc2e45f0852edfd3cf8338ab3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509143"
---
# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Az Intune szoftverügyfelet futtató Windows rendszerű számítógépes alkalmazások hozzáadása

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Ebből a témakörből megtudhatja, hogyan adhatja hozzá a kívánt alkalmazásokat az Intune-hoz a központi telepítésük előtt.

> [!IMPORTANT]
> A jelen témakörben ismertetett információk segítik az alkalmazások hozzáadását azokon a Windows-számítógépeken, amelyeket az Intune szoftverügyfél segítségével felügyel. Ha regisztrált Windows-számítógépekhez vagy más mobileszközökhöz szeretne alkalmazásokat adni, olvassa el az [Alkalmazások hozzáadása a Microsoft Intune-hoz](../apps/apps-add.md) című cikket.

Csak olyan alkalmazásokat lehet telepíteni a számítógépekre, amelyek csendesen, felhasználói beavatkozás nélkül telepíthetők. Más esetben a telepítés sikertelen lesz.

## <a name="additional-security-settings-for-windows-installer"></a>A Windows Installer további biztonsági beállításai
Engedélyezheti a felhasználóknak az alkalmazástelepítések szabályozását. Ha engedélyezve van, azok a telepítések, amelyek a biztonság megsértése miatt le lettek volna állítva engedélyt kapnak a folytatásra. Megadhatja, hogy a Windows Installer emelt szintű engedélyeket használjon, amikor programokat telepít a rendszerben. Emellett engedélyezheti a Windows Information Protection (WIP) elemek indexelését és az ezekre vonatkozó metaadatok titkosítatlan helyen való tárolását. A szabályzat tiltásakor a WIP által védett elemek nem lesznek indexelve és nem jelennek meg a Cortana vagy a fájlkezelő eredményei között. Ezeknek a beállításoknak a funkciói alapértelmezés szerint le vannak tiltva. 

## <a name="add-the-app"></a>Az alkalmazás hozzáadása
Az alábbiakban ismertetett eljárással konfigurálhatja az alkalmazás tulajdonságait az Intune Software Publisherrel, és feltöltheti az alkalmazást a felhőtárhelyre.

1. A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com) válassza az **Alkalmazások** &gt; **Alkalmazások felvétele** elemet az Intune Software Publisher elindításához.

   > [!TIP]
   > Előfordulhat, hogy a Software Publisher elindulása előtt meg kell adnia Intune-felhasználónevét és jelszavát.

2. A Software Publisher **Szoftver telepítése** lapján, a **Válassza ki, hogyan szeretné elérhetővé tenni ezt a szoftvert az eszközök számára** beállításnál válassza a **Szoftver telepítője** lehetőséget, majd:

   - **Válassza ki a szoftver telepítőjének fájltípusát**. Itt adhatja meg a telepíteni kívánt szoftver típusát. Windows-számítógép esetén válassza a **Windows Installer** lehetőséget.
   - **Adja meg a szoftver telepítőfájljainak helyét**. Adja meg a telepítőfájlok helyét, vagy kattintson a **Tallózás** gombra a kívánt hely listából való kiválasztásához.
   - **Adja meg a mappában található további fájlokat és almappákat is**. A Windows Installert használó szoftverek némelyikéhez támogató fájlokra is szükség van. Ezeknek a telepítőfájllal azonos mappában kell lenniük. Akkor válassza ezt a lehetőséget, ha ezeket a fájlokat is telepíteni kívánja.

   Ha például egy Application.msi nevű alkalmazást szeretne közzétenni az Intune-ban, ilyen lesz a lap: ![a kiadó szoftvertelepítési lapja](./media/add-apps-for-windows-pcs-in-microsoft-intune/publisher-for-pc.png)

   Ez a telepítési típus némi helykapacitást igényel a felhőbeli tárhelyen.

3. A **Szoftver leírása** lapon állítsa be a következőket.

   > [!NOTE]
   > A telepítőfájl típusától függően előfordulhat, hogy az alábbi értékek némelyike nem jelenik meg, vagy ezeket a rendszer automatikusan megadja.

   - **Kiadó**. Itt adhatja meg az alkalmazás kiadójának nevét.
   - **Név**. Itt adhatja meg az alkalmazás vállalati portálon megjelenő nevét.<br />Ügyeljen arra, hogy a megadott alkalmazásnevek egyediek legyenek. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a vállalati portálon.
   - **Leírás**. Adja meg az alkalmazás leírását. amelyet meg szeretne jeleníteni a felhasználók számára a vállalati portálon.
   - **Szoftveradatok URL-címe** (nem kötelező). Adja meg az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím fog megjelenni a felhasználók számára a vállalati portálon.
   - **Adatvédelmi nyilatkozat URL-címe** (nem kötelező). Itt adhatja meg az alkalmazással kapcsolatos adatvédelmi információkat tartalmazó webhely URL-címét. Ez az URL-cím fog megjelenni a felhasználók számára a vállalati portálon.
   - **Kategória** (nem kötelező). Itt választhatja ki a beépített alkalmazáskategóriák egyikét. Ezzel megkönnyítheti a felhasználók számára az alkalmazás megkeresését a vállalati portálon való böngészés során.
   - **Ikon** (nem kötelező). Itt töltheti fel az alkalmazáshoz hozzárendelni kívánt ikont. Ez az alkalmazásikon jelenik meg a vállalati portálon böngésző felhasználók számára.

4. A **Követelmények** lapon adja meg az alkalmazás telepítéséhez szükséges követelményeket, amelyeket teljesíteni kell az alkalmazás telepítése előtt. A következő lehetőségek közül választhat:

   - **Architektúra**. Válassza ki, hogy az alkalmazás 32 bites vagy 64 bites operációs rendszeren, illetve mindkettőn telepíthető-e.
   - **Operációs rendszer**. Válassza ki azt a legrégebbi operációsrendszer-verziót, amelyen még telepíthető az alkalmazás.

5. Az **Észlelési szabályok** lapon állíthatja be azokat a szabályokat, amelyek alapján a rendszer észleli, hogy a konfigurálni kívánt alkalmazás már telepítve van-e a számítógépen. Ha az alapértelmezett észlelési szabályokat alkalmazza, a rendszer automatikusan felülírja az alkalmazás valamennyi korábban telepített verzióját. Ez a beállítás a Windows Installer szolgáltatáshoz tartozik (csak .exe fájlok).

   A következő szabályokat állíthatja be:
   - **A fájl létezik**. Adja meg az észlelni kívánt fájl elérési útját. A kereséshez a következő helyeket adhatja meg: **%ProgramFiles%** (ami a **Program Files**\&lt;elérési út&gt; és a **Program Files (x86)** \&lt;elérési út&gt; mappában keres) vagy **%SystemDrive%** (ami a számítógép gyökérmeghajtója, általában a C: meghajtó).
   - **Az MSI-termékkód létezik**. Válassza a **Tallózás** elemet az észlelni kívánt Windows Installer-fájl (.msi) kiválasztásához.
   - <strong>A beállításkulcs létezik</strong>. Adjon meg egy beállításkulcsot, amely a következővel kezdődik: <strong>HKEY_LOCAL_MACHINE\</strong>. A keresés a beállításjegyzék 32 bites és 64 bites elérési útjaira egyaránt kiterjed. Ha a megadott kulcs megtalálható az egyik helyen, az észlelési szabály teljesül.

   Ha az alkalmazás megfelel a konfigurált szabályok valamelyikének, nem lesz telepítve.

6. Csak a **Windows Installer** fájltípusai (.msi és .exe) esetében: a **Parancssori argumentumok** lapon adja meg, hogy szeretne-e opcionális parancssori argumentumokat megadni a telepítőhöz.
   Az Intune automatikusan megadja a következő paramétereket:
   - Az .exe fájlokhoz az **/install** paramétert fűzi.
   - Az .msi fájlokhoz a **/quiet** paramétert fűzi.
   Ne feledje, hogy ezek a paraméterek csak akkor működnek, ha az alkalmazáscsomag készítője engedélyezte a nekik megfelelő funkciókat.

7. Csak a **Windows Installer** fájltípus (.exe) esetében: a **Visszatérési kódok** lapon olyan új hibakódokat vehet fel, amelyeket az Intune az alkalmazás felügyelt Windows-számítógépre való telepítésekor értelmez.

   Alapértelmezés szerint az Intune az iparági szabványnak megfelelő visszatérési kódok segítségével jelenti az alkalmazáscsomagok telepítésének sikerességét vagy sikertelenségét: **0** – Sikeres vagy **3010** – Sikeres, újraindítással. Ehhez a listához saját visszatérési kódjait is hozzáadhatja. Ha megad egy visszatérésikód-listát, és az alkalmazás telepítőprogramja olyan kódot ad vissza, amely nem szerepel a listán, a rendszer a kódot hibaként értelmezi.

8. Az **Összefoglalás** lapon ellenőrizze a megadott adatokat. Ha elkészült, válassza a **Feltöltés** elemet.

9. A befejezéshez válassza a **Bezárás** elemet.

Az alkalmazás megjelenik az **Alkalmazások** munkaterület **Alkalmazások** csomópontjában.

## <a name="next-steps"></a>További lépések

Ha létrehozta az alkalmazást, a következő lépés a telepítés. További tudnivalók: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](../apps/apps-deploy.md).

Ha a szoftverek Windows-számítógépekre való telepítésével kapcsolatos tippekről és trükkökről szeretne tájékozódni, [ebből a blogbejegyzésből megismerkedhet a számítógépekre az Intune-nal történő szoftverterjesztés ajánlott eljárásaival](https://support.microsoft.com/en-US/help/2583929).
