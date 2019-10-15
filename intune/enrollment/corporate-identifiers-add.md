---
title: Vállalati azonosítók hozzáadása az Intune-hoz
titleSuffix: ''
description: Megtudhatja, hogyan adhat hozzá vállalati azonosítókat (regisztrációs módszert, IMEI-t és sorozatszámokat) a Microsoft Intunehoz.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: afc9d953e1d324adb3f00eb5209732a858bbbcda
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314675"
---
# <a name="identify-devices-as-corporate-owned"></a>Vállalati tulajdonú eszközök azonosítása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune-rendszergazdaként a felügyelet és az azonosítás pontosításához vállalati tulajdonban lévő eszközöket is azonosíthat. Az Intune további felügyeleti feladatokat hajthat végre, és további információkat gyűjthet, például a teljes telefonszámot és a vállalati tulajdonú eszközökből származó alkalmazások leltárát. Megadhatja az eszköz korlátozásait is, hogy blokkolja a vállalati tulajdonú eszközök regisztrációját.

A regisztráláskor az Intune automatikusan vállalati tulajdonú állapotot rendel a következő eszközökhöz:

- Regisztrálva van egy [eszköz beléptetési Manager](device-enrollment-manager-enroll.md) -fiókkal (minden platform)
- Regisztrálva van az Apple [Készülékregisztrációs programban](device-enrollment-program-enroll-ios.md), az [Apple School Managerben](apple-school-manager-set-up-ios.md)vagy az [Apple konfigurátorban](apple-configurator-enroll-ios.md) (csak iOS esetén)
- [Vállalati tulajdonban van azonosítva, mielőtt](#identify-corporate-owned-devices-with-imei-or-serial-number) bejelentkezett volna egy nemzetközi mobileszköz-azonosító (IMEI) számmal (az összes IMEI-számmal rendelkező platformmal) vagy sorozatszámmal (iOS és Android).
- Azure Active Directory munkahelyi vagy iskolai hitelesítő adatokkal. A [Azure Active Directory regisztrált eszközök](https://docs.microsoft.com/azure/active-directory/devices/overview) személyesként lesznek megjelölve.
- Beállítás vállalatiként az [eszköz Tulajdonságok listájában](#change-device-ownership)

A regisztráció után [megváltoztathatja a tulajdonosi beállítást a](#change-device-ownership) **személyes** és a **vállalati**felhasználók között.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>A vállalat által birtokolt eszközök azonosítása IMEI-vagy sorozatszámmal

Intune-rendszergazdaként létrehozhat és importálhat egy olyan vesszővel tagolt (. csv) fájlt, amely 14 számjegyű IMEI-számot vagy sorozatszámot listáz. Az Intune ezeket az azonosítókat használja a vállalati eszközök tulajdonjogának megadásához az eszközök regisztrálásakor. Az egyes IMEI-vagy sorozatszám-azonosítók a listában a felügyeleti célokra is megadhatók.

Ez a funkció a következő platformokon támogatott:

| Platform | IMEI-számok | Sorozatszámok |
|---|---|---|
| Windows | Támogatott (Windows Phone-telefon) | Nem támogatott |
| iOS/macOS | Nem támogatott | Támogatott |
| Eszköz rendszergazdája által felügyelt Android OS v10 | Nem támogatott | Nem támogatott |
| Egyéb Android | Nem támogatott | Támogatott |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Megtudhatja, hogyan keresheti meg az Apple-eszközök sorozatszámát](https://support.apple.com/HT204308).<br>
[Megtudhatja, hogyan keresheti meg az androidos eszköz sorozatszámát](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Vállalati azonosítók hozzáadása. csv-fájl használatával
A lista létrehozásához hozzon létre egy kétoszlopos, vesszővel tagolt (. csv) listát fejléc nélkül. Adja hozzá a 14 számjegyből álló IMEI-t vagy sorozatszámot a bal oldali oszlopban, valamint a jobb oldali oszlopban található adatokat. Egyetlen. csv fájlban csak egy azonosító, IMEI vagy sorozatszám lehet importálható. A részletek legfeljebb 128 karakterből állhatnak, és csak rendszergazdai használatra használhatók. A részletek nem jelennek meg az eszközön. Az aktuális korlát 5 000 sor. csv-fájl.

**Töltsön fel egy sorozatszámmal rendelkező. csv-fájlt** – hozzon létre egy kétoszlopos, vesszővel tagolt (. csv) listát fejléc nélkül, és korlátozza a listát 5 000 eszközre vagy 5 MB/. csv-fájlra.

|||
|-|-|
|&lt;ID #1 &gt;|&lt;Device #1 részletek @ no__t-1|
|&lt;ID #2 &gt;|&lt;Device #2 részletek @ no__t-1|

Ez a. csv-fájl egy szövegszerkesztőben megtekintve a következőképpen jelenik meg:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Egyes Android-és iOS-eszközök több IMEI-számmal rendelkeznek. Az Intune-ban regisztrált eszközökön csak egy IMEI-szám olvasható. Ha olyan IMEI-számot importál, amely nem az Intune által leltározott, akkor az eszköz a vállalat által birtokolt eszköz helyett személyes eszközként lesz besorolva. Ha egy eszközhöz több IMEI-számot importál, a uninventoried száma **ismeretlen** a beléptetési állapotnál.<br>
>Megjegyzés: a sorozatszámok az iOS-eszközök azonosításának ajánlott formája.
>Az Android-sorozatszámok nem garantáltan egyediek vagy jelennek meg. Kérdezze meg az eszköz szállítóját, hogy megtudja, a sorozatszám megbízható eszköz-azonosító-e.
>Előfordulhat, hogy az eszköz által az Intune-nak küldött sorozatszámok nem egyeznek meg az eszközön az Android-beállítások/a menük között. Ellenőrizze az eszköz gyártója által jelentett sorozatszám típusát.
>A pontokat (.) tartalmazó sorozatszámok feltöltésére tett kísérlet miatt a feltöltés sikertelen lesz. A pontokkal rendelkező sorozatszámok nem támogatottak.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Vállalati azonosítók. csv-listájának feltöltése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, válassza az **eszközök beléptetése** > **vállalati eszköz azonosítóját** > **Hozzáadás** > **CSV-fájl feltöltése**elemet.

   ![Vállalati eszköz azonosító munkaterülete a Hozzáadás gombbal kiemelve](./media/corporate-identifiers-add/add-corp-id.png)

2. Az **azonosítók hozzáadása** panelen adja meg az azonosító típusát: **IMEI** vagy **sorozatszám**.

3. Kattintson a mappa ikonra, és válassza ki az importálni kívánt lista elérési útját. Navigáljon a. CSV-fájlhoz, és válassza a **Hozzáadás**lehetőséget. 

4. Ha a. csv-fájl olyan vállalati azonosítókat tartalmaz, amelyek már szerepelnek az Intune-ban, de eltérő adatokkal rendelkeznek, megjelenik a **felülvizsgálati duplikált azonosítók** előugró ablak. Válassza ki az Intune-ba írni kívánt azonosítókat, majd az azonosítók hozzáadásához kattintson **az OK gombra** . Minden azonosító esetében csak az első ismétlődés lesz összehasonlítva.

## <a name="manually-enter-corporate-identifiers"></a>Vállalati azonosítók manuális megadása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, válassza az **eszközök beléptetése** > **vállalati eszköz azonosítóját** >  adja**hozzá**a  > **értéket manuálisan**.

2. Az **azonosítók hozzáadása** panelen adja meg az azonosító típusát: **IMEI** vagy **sorozatszám**.

3. Adja meg a hozzáadni kívánt azonosítók **azonosítóját** és **részleteit** . Ha elkészült az azonosítók beírásával, válassza a **Hozzáadás**lehetőséget.

5. Ha olyan vállalati azonosítókat adott meg, amelyek már szerepelnek az Intune-ban, de eltérő adatokkal rendelkeznek, megjelenik a **felülvizsgálati duplikált azonosítók** előugró ablak. Válassza ki az Intune-ba írni kívánt azonosítókat, majd az azonosítók hozzáadásához kattintson **az OK gombra** . Minden azonosító esetében csak az első ismétlődés lesz összehasonlítva.

A **frissítés** gombra kattintva megtekintheti az új eszközök azonosítóit.

Az importált eszközök nem feltétlenül lettek regisztrálva. Az eszközök lehetnek **regisztráltak** vagy **nincsenek kapcsolatba**. **Nem történt kapcsolat** azt jelenti, hogy az eszköz soha nem kommunikált az Intune szolgáltatással.

## <a name="delete-corporate-identifiers"></a>Vállalati azonosítók törlése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, válassza az **eszközök beléptetése**@no__t – 2**vállalati eszköz azonosítóját**.
2. Válassza ki a törölni kívánt eszközök azonosítóit, és válassza a **Törlés**lehetőséget.
3. Erősítse meg a törlési szándékát.

Egy regisztrált eszköz vállalati azonosítójának törlése nem változtatja meg az eszköz tulajdonjogát. Az eszköz tulajdonjogának módosításához lépjen az **eszközök**elemre, válassza ki az eszközt, válassza a **Tulajdonságok**lehetőséget, és módosítsa az **eszköz tulajdonjogát**.

## <a name="imei-specifications"></a>IMEI-specifikációk
A nemzetközi mobileszközök azonosítóinak részletes leírását lásd: [3GGPP TS 23,003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Eszköz tulajdonjogának módosítása

Az eszközök tulajdonságai megmutatják az Intune-ban lévő minden eszköz rekordjainak **tulajdonjogát** . Rendszergazdaként megadhatja az eszközöket **személyesként** vagy **vállalatiként**.

**Az eszköz tulajdonjogának módosítása:**
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba, lépjen az **eszközök** pontra, és válassza ki az eszközt.
2. Kattintson a **Tulajdonságok** elemre.
3. **Személyes** vagy **céges** **eszközök tulajdonjogának** megadása.

   ![Az eszköz kategóriáját és az eszköz tulajdonjogát megjelenítő eszközbeállítások](./media/corporate-identifiers-add/device-properties.png)
