---
title: Vállalati azonosítók hozzáadása az Intune-hoz
titleSuffix: ''
description: Ismerje meg, hogyan adhat hozzá vállalati azonosítókat (regisztrációs módszer, IMEI és sorozatszámok) a Microsoft Intune-bA.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3d98a0e3c5bd2a5c11c9aa72d791306dfbe6578
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503297"
---
# <a name="identify-devices-as-corporate-owned"></a>Eszközök azonosítása vállalati tulajdonúként

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune-rendszergazdaként vállalati tulajdonúként azonosíthat eszközöket, így finomíthatja a felügyeletet és az azonosítást. Az Intune további felügyeleti feladatokat végezhet, valamint további adatokat gyűjthet, például a vállalati tulajdonú eszközök teljes telefonszámát és az eszközökön található alkalmazások leltárát. Eszközkorlátozásokat is beállíthat a nem vállalati tulajdonú eszközök regisztrációjának megakadályozásához.

A regisztrálás idején az Intune automatikusan vállalati tulajdonú státuszt rendel az eszközhöz, ha azt:

- [i](device-enrollment-manager-enroll.md) fiókkal regisztrálták (bármely platformon).
- Az Apple [Készülékregisztrációs programban](device-enrollment-program-enroll-ios.md), az [Apple School Managerrel](apple-school-manager-set-up-ios.md) vagy az [Apple Configuratorral](apple-configurator-enroll-ios.md) regisztrálták (csak iOS esetén).
- [Regisztráció előtt az eszközt céges eszközként azonosították](#identify-corporate-owned-devices-with-imei-or-serial-number) nemzetközi mobilkészülék-azonosító (IMEI-) számmal (minden IMEI-számmal rendelkező platform esetében) vagy sorozatszámmal (csak iOS és Android esetében)
- Azure Active Directory munkahelyi vagy iskolai hitelesítő adatokkal. A [Azure Active Directory regisztrált eszközök](https://docs.microsoft.com/azure/active-directory/devices/overview) személyesként lesznek megjelölve.
- Vállalatiként van beállítva az [eszköz tulajdonságaiban](#change-device-ownership)

A regisztrálás után [a tulajdonosi beállítás módosítható](#change-device-ownership), és beállítható akár **Személyes**, akár **Vállalati** tulajdonra.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Céges eszközök azonosítása IMEI- vagy sorozatszám alapján

Intune-rendszergazdaként létrehozhat és importálhat egy olyan vesszővel tagolt (. csv) fájlt, amely 14 számjegyű IMEI-számot vagy sorozatszámot listáz. Az Intune ezeket az azonosítókat használva határozza meg a regisztráció során, hogy egy adott eszköz céges tulajdonú-e. Adminisztrációs célból minden IMEI-azonosítóhoz vagy sorozatszámhoz megadhat további adatokat is.

Ez a funkció a következő platformokon támogatott:

| Platform | IMEI-számok | Sorozatszámok |
|---|---|---|
| Windows | Támogatott (Windows Phone-telefon) | Nem támogatott |
| iOS/macOS | Nem támogatott | Támogatott |
| Eszköz rendszergazdája által felügyelt Android OS v10 | Nem támogatott | Nem támogatott |
| Egyéb Android | Nem támogatott | Támogatott |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Ismerje meg, hogyan találhatja meg egy Apple-eszköz sorozatszámát](https://support.apple.com/HT204308).<br>
[Ismerje meg, hogyan találhatja meg a saját Apple-eszköz sorozatszámát](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Vállalati azonosítók felvétele .csv-fájlból
Hozzon létre egy kétoszlopos, fejléc nélküli listát .csv formátumban. Adja hozzá a 14 számjegyből álló IMEI-t vagy sorozatszámot a bal oldali oszlopban, valamint a jobb oldali oszlopban található adatokat. Egy .csv-fájlból csak egyféle azonosítót (IMEI-azonosítót vagy sorozatszámot) importálhat. A részletes adatok maximális terjedelme 128 karakter, csak adminisztratív célt szolgálnak, és nem jelennek meg az eszközön. A .csv-fájlok jelenleg legfeljebb 5 000 sorosak lehetnek.

**Sorozatszámokat tartalmazó .csv-fájl feltöltése** – Hozzon létre egy vesszővel elválasztott, kétoszlopos, fejléc nélküli értéklistát (.csv), amelyben maximum 5,000 eszköz szerepel. A csv-fájl mérete nem haladja meg az 5 MB-ot.

|||
|-|-|
|&lt;1. azonosító&gt;|&lt;1. eszköz részletei&gt;|
|&lt;2. azonosító&gt;|&lt;2. eszköz részletei&gt;|

Ez a .csv- fájl egy szövegszerkesztőben megtekintve így jelenik meg:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Egyes Android-és iOS-eszközök több IMEI-számmal rendelkeznek. Az Intune regisztrált eszközönként csak egy IMEI-számot olvas be. Ha olyan IMEI-számot importál, amely nem az Intune által leltározott, akkor az eszköz a vállalat által birtokolt eszköz helyett személyes eszközként lesz besorolva. Ha egy eszközhöz több IMEI-számot importál, a leltárban nem szereplő számok **Ismeretlen** regisztrációs állapottal jelennek meg.<br>
>Megjegyzés: a sorozatszámok az iOS-eszközök azonosításának ajánlott formája.
>Az Android-sorozatszámok nem garantáltan egyediek vagy jelennek meg. Egyeztessen az eszköz szállítójával arról, hogy a sorozatszám tekinthető-e megbízható eszközazonosítónak.
>Elképzelhető, hogy az a sorozatszám, amelyet az eszköz az Intune felé jelez, nem egyezik meg az eszköz Android beállítások/Névjegy (Android Settings/About) menüjében megjelenő azonosítóval. Ellenőrizze, hogy az eszköz gyártója milyen típusú sorozatszámot tüntet fel itt.
>Ha a feltöltendő sorozatszámokból álló fájl pontokat (.) tartalmaz, a feltöltés sikertelen lesz. A pontokat tartalmazó sorozatszámok nem támogatottak.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Céges azonosítók .csv-listájának feltöltése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, válassza az **eszközök beléptetése** > **vállalati eszközök azonosítói** > **Hozzáadás** > a **CSV-fájl feltöltése**lehetőséget.

   ![A céges készülékazonosítók munkaterülete a Hozzáadás gomb kiemelésével](./media/corporate-identifiers-add/add-corp-id.png)

2. Az **Azonosítók hozzáadása** panelen adja meg az azonosító típusát: **IMEI** vagy **Sorozatszám**.

3. Kattintson a mappa ikonra, és adja meg az importálni kívánt lista elérési útját. Keresse meg a .csv-fájlt, és kattintson a **Hozzáadás** elemre. 

4. Ha a .csv-fájl az Intune-ban már meglévő céges azonosítókat tartalmaz, de más részletekkel, megjelenik az **Ismétlődő azonosítók áttekintése** előugró üzenet. Válassza ki azokat az azonosítókat, amelyeket szeretne felülírni az Intune-ban, majd válassza az **OK** gombot az azonosítók hozzáadásához. Az egyes azonosítóknál csak az első ismétlődés lesz összehasonlítva.

## <a name="manually-enter-corporate-identifiers"></a>A céges azonosítók manuális megadása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, válassza az **eszközök beléptetése** > **vállalati eszközök azonosítói** > **Hozzáadás** manuálisan > az **ENTER billentyűt**.

2. Az **Azonosítók hozzáadása** panelen adja meg az azonosító típusát: **IMEI** vagy **Sorozatszám**.

3. Adja meg a hozzáadni kívánt azonosítók **azonosítóját** és **részleteit** . Az azonosítók megadásának befejezése után válassza a **Hozzáadás** gombot.

5. Ha az Intune-ban már meglévő céges azonosítókat adott meg, de más részletekkel, megjelenik az **Ismétlődő azonosítók áttekintése** előugró üzenet. Válassza ki azokat az azonosítókat, amelyeket szeretne felülírni az Intune-ban, majd válassza az **OK** gombot az azonosítók hozzáadásához. Az egyes azonosítóknál csak az első ismétlődés lesz összehasonlítva.

A **Frissítés** elemre kattintva megtekintheti az új eszközazonosítókat.

Az importált eszközöket nem mindig regisztrálja a rendszer. Emiatt az eszközök **Regisztrált** vagy **Nincs kapcsolat** állapotúak lehetnek. Utóbbi állapot azt jelenti, hogy az eszköz még nem lépett kapcsolatba az Intune szolgáltatással.

## <a name="delete-corporate-identifiers"></a>Céges azonosítók törlése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, válassza az **eszközök beléptetése** > **vállalati eszközök azonosítói**lehetőséget.
2. Válassza ki a törölni kívánt eszközazonosítókat, majd kattintson a **Törlés** gombra.
3. Hagyja jóvá a törlést.

Ha törli egy regisztrált eszköz céges azonosítóját, azzal nem változtatja meg az eszköz tulajdonosát. Az eszköz tulajdonosának módosításához nyissa meg az **Eszközök** panelt, válassza ki az eszközt, majd válassza a **Tulajdonságok** lehetőséget, és módosítsa az **Eszköz tulajdonosa** értékét.

## <a name="imei-specifications"></a>IMEI-azonosítók specifikációi
Az IMEI-azonosítók részletes specifikációját a [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729) lapon találja.

## <a name="change-device-ownership"></a>Eszköz tulajdonosának módosítása

Az Intune-ban az eszközök tulajdonságai között mindegyik eszközbejegyzésnél szerepel a **Tulajdonos**. Rendszergazdaként megadhatja, hogy az adott eszköz **Személyes** vagy **Céges**. Ha az eszköz tulajdonosi típusa személyesről Vállalatire változik, az Intune az adott eszközről korábban összegyűjtött összes alkalmazási adatot 7 napon belül törli. Ha alkalmazható, az Intune törli a rekordban szereplő telefonszámot is. 

**Eszköz tulajdonosának módosítása:**
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, lépjen az **eszközök** pontra, és válassza ki az eszközt.
2. Válassza a **Tulajdonságok** lehetőséget.
3. Adja meg az **Eszköz tulajdonosa** beállításnál, hogy az eszköz **Személyes** vagy **Céges**.

   ![Az eszköz tulajdonságai képernyő az Eszközkategória és az Eszköz tulajdonosa beállításokkal](./media/corporate-identifiers-add/device-properties.png)
