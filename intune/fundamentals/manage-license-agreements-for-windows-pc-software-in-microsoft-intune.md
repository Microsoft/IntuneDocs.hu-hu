---
title: Intune-ügyfélszoftvert futtató számítógépekhez tartozó szoftverlicenc-szerződések kezelése
titleSuffix: Microsoft Intune
description: Az Intune-ban kezelheti a Microsoft mennyiségi licencszerződéseinek keretében beszerzett, vagy egyéb módon megvásárolt szoftverek licencszerződéseit.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: ab5e5d3e645410b876a5d3d0be0eafed9c790780
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502656"
---
# <a name="manage-license-agreements-for-windows-pc-software-in-microsoft-intune"></a>Windows-számítógépes szoftverek licencszerződéseinek kezelése a Microsoft Intune-ban

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

A Microsoft Intune a Microsoft mennyiségi licencszerződéssel vásárolt szoftverek licencszerződés-információinak felvételét és kezelését teszi lehetővé. Ugyanez lehetséges a Microsofttól vagy nem Microsofttól származó, egyéb módon vásárolt szoftverek esetében is. Ezek az információk logikai csoportokba rendezhetők.

> [!IMPORTANT]
> Ez a funkció kizárólag kényelmi célokat szolgál, és pontossága nem garantált. Ezek az adatok nem használhatók fel a Microsoft mennyiségi licencszerződéseknek való megfelelés ellenőrzésére. A Microsoft nem használja a gyűjtött adatokat a vele kötött licencszerződések lehetséges megsértésének vagy betartásának vizsgálatára.
>
> Az Intune-hoz hozzáadott licencek nincsenek hatással a szoftver használatára vonatkozó licencszerződésekre és jogosultságokra. Ha például töröl egy licencszerződéspárt az Intune-ból, azzal nem törli és nem érvényteleníti az Ön és a Microsoft közötti licencszerződéseket.

Az Intune felügyeleti konzoljának **Licencek** munkaterületén a következőkre van lehetősége:

- Microsoft mennyiségi licencszerződések hozzáadása és szerkesztése.

- Egyéb szoftverlicenc-szerződések hozzáadása és szerkesztése.

- Licencek és csoportok kezelése.

- Az Intune által a Mennyiségi licencelési szolgáltatásközpont (VLSC) webhelyéről lekérdezett jogosultsági információk összehasonlítása azon Microsoft-szoftverekkel, amelyeket az Intune az Ön felügyelt Windows-számítógépein észlel.

Emellett olyan jelentéseket is létrehozhat, amelyek megjelenítik a szoftverek telepítés- és licencszámait. A licencjelentések segítséget nyújthatnak a Microsofttól és a nem Microsofttól származó szoftvercímek teljes licenchelyzetének értékelésében.

> [!TIP]
> A **Licencek** munkaterület csak akkor jelenik meg a felügyeleti konzolon, ha már legalább egy Windows-számítógépet felügyel az Intune-ügyféllel.

## <a name="add-microsoft-volume-licensing-agreements"></a>Microsoft mennyiségi licencszerződések hozzáadása
Az Intune mennyiségi licencelszerződések a Microsoft mennyiségi licencszerződéseken keresztül vásárolt szoftverek licencinformációit tartalmazzák. Ha Microsoft mennyiségi licencszerződéseket szeretne hozzáadni az Intune-hoz, adja meg a szerződésszámok egyeztetett párjait. A szerződés- vagy engedélyezési számokat egyeztetni kell a megfelelő licenc- vagy regisztrációs számokkal. A szerződésszámpárokat akkor kapja meg, amikor licencszerződéseket vásárol a [Mennyiségi Licencelési Szolgáltatásközpontból (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842).

1. A [Microsoft Intune felügyeleti konzolon](https://admin.manage.microsoft.com/) válassza a **Licencek** elemet.

2. A **Szerződések hozzáadása** lap **Szerződés típusának kiválasztása** területén válassza a **Mennyiségi licencszerződés** lehetőséget.

3. A **Szerződés adatainak hozzáadása** szakaszban válasszon a fájlfeltöltés vagy az adatok manuális hozzáadása közül.

    - **Szerződésadatokat tartalmazó CSV-fájl feltöltése**. Kattintson a **Tallózás** elemre, és válassza ki a feltöltendő CSV-fájlt.

        - A fájl két vagy három oszlopot tartalmazhat: kettőt csak a szerződéspárokhoz, vagy hármat abban az esetben, ha az egyes szerződéspárokhoz rövid nevet is szeretne megadni.

        - A szerződésszámpárokban lévő karakterek összesített száma nem lehet több 16 ASCII-karakternél.

        - Csak az ASCII-karakterek támogatottak.

        - A szerződés nevében nem használhatóak a következő karakterek: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /** . A szóközök engedélyezettek a névben.

        - A fájl neve nem lehet hosszabb 128 karakternél.

        - A fájlnak legalább egy szerződéspárt kell tartalmaznia, és nem szerepelhet benne 5000 szerződéspárnál több.

        **A fájl formátuma**

        A fájl létrehozásához adja meg a szerződéspárokat egy egyszerű szöveges dokumentumban a következő formátumok egyikében, a VLSC webhelyen regisztrált szervezettípustól függően. Soronként egy szerződésszámpár szerepeljen.

        - **Open Value-ügyfelek:** *szerződésszám*, *szerződésszám ismétlése*, *szerződés neve*

        - **Open-ügyfelek:** *engedélyezési szám*, *kapcsolódó licencszám*, *szerződésnév*

        - **Select- és nagyvállalati ügyfelek:** *szerződésszám*, *kapcsolódó regisztrációs szám*, *szerződésnév*

        A **Szerződések hozzáadása** űrlap új szerződések hozzáadásakor megkéri, hogy keresse meg az adott fájlt.

        A következő példában egy .csv fájl tartalma látható egy Nyitottértékügyfél esetén.

        `01-07001, 01-07001, Office agreements`

    - **Szerződés adatainak manuális hozzáadása**. Adja meg az alábbi adatokat, majd írja be a szerződésszámpárokat az **Engedély/szerződés száma** és a **Licenc/igyénylés/ügyfél száma** mezőbe. Miután beírta mindkét számot, válassza a **Pár hozzáadása** ikont a számok mentéséhez, majd ha szükséges, hozzáadhat további párokat.

        - **Szerződés neve** – Adja meg a szerződés egyedi nevét.

            A szerződés neve legfeljebb 256 karakterből állhat, és nem tartalmazhatja a következő karaktereket: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /** . A szóközök engedélyezettek a névben.

        - **Engedély/szerződés száma** – Adja meg a licencpár engedély-/szerződésszámát.

        - **Licenc/igénylés/ügyfél száma** – Adja meg a licencpár licenc-/igénylés-/ügyfélszámát.

        > [!NOTE]
        > Ha több szerződésszámpárt ad hozzá, az Intune egy szerződést hoz létre a megadott névvel, és a hozzáadott összes pár ezen szerződés részét fogja képezni.

    A **+** jel kiválasztásával adhat hozzá másik szerződésszámpárt, a **-** jel kiválasztásával pedig eltávolíthat egy korábban már megadott szerződésszámpárt.

4. A **Licenccsoport kiválasztása** területen tegye a következők valamelyikét:

    - **A szerződések hozzáadása a Hozzá nem rendelt szerződések csoporthoz**. Válassza ezt a lehetőséget, ha nem szeretne új szerződéseket hozzáadni egy licenccsoporthoz.

    - **A szerződések hozzáadása új licenccsoporthoz**. Adja meg az új licenccsoport nevét.

    - **A szerződések hozzáadása meglévő licenccsoporthoz**. A **Csoport neve** listában válassza ki azt a licenccsoportot, amelyhez a szerződéseket hozzá szeretné adni.

5. Válassza az **OK** gombot.

Megjelenik a **Minden szerződés** nézet, és az Intune a megadott szerződésszámpárok érvényesítése céljából kapcsolódik a Microsoft VLSC webhelyhez.

Ha a licencszerződéseknek az Intune-hoz való hozzáadását követően szeretné frissíteni a mennyiségi licencekre vonatkozó információkat, válassza a **Licencek – áttekintés** lap **Frissítés most** elemét. Ez a művelet lekérdezi az aktuális licencinformációkat a [Microsoft Mennyiségi Licencelési Szolgáltatásközpontból (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT]
> A mennyiségi licencelési információk frissítéséig más adatokat láthat a szerződéslistában és a **Szerződések áttekintése** lap jogosultsági információinál.

A mennyiségi licencelési információk frissítése után összehasonlíthatja a licencinformációkat az észlelt Microsoft-szoftverekkel az **Alkalmazások** munkaterületen. A következő licencjelentéseket is futtathatja:

- **Licencvásárlási jelentések** – Lehetővé teszi a kiválasztott licenccsoportokban lévő licencelt szoftverek megtekintését a lefedettségi hézagok meghatározása érdekében.

- **Licenctelepítési jelentések** – Megkönnyíti annak meghatározását, hogy elegendő licencszerződéssel rendelkezik-e.

> [!NOTE]
> Az összes Microsoft mennyiségi licencszerződésnél megjelenített **Terméknév** a **Nem érhető el**.

## <a name="add-and-edit-other-software-licensing-agreements"></a>Egyéb szoftverlicenc-szerződések hozzáadása és szerkesztése
Az Intune-hoz a Microsoft mennyiségi licencszerződésektől eltérő típusú licencszerződéseket is hozzáadhat. Ezek a szerződések kereskedőktől vásárolt Microsoft- vagy nem Microsoft-szoftvereket tartalmazhatnak.

> [!IMPORTANT]
> A szerződések hozzáadása előtt legalább egy Windows-számítógépet regisztrálnia kell az Intune-ban.  Ezenkívül legalább egy regisztrált számítógépre fel kell tölteni azt a licencelhető szoftvercsomagot, amellyel a licencszerződéseket hozzá szeretné adni.

### <a name="to-add-other-software-agreements"></a>Egyéb szoftverszerződések hozzáadása

1. A [Microsoft Intune felügyeleti konzolon](https://admin.manage.microsoft.com/) válassza a **Licencek** elemet.

2. Válassza az **Egyéb szoftverlicenc-szerződések** szakasz **Szerződések hozzáadása** elemét.

3. Válassza a **Szerződések hozzáadása** lap **Szerződéstípus választása** szakaszának **Egyéb szoftverlicenc-szerződések** elemét.

4. A **Szerződésadatok hozzáadása** területen adja meg a következőket:

    - **Agreement name** (kötelező). A szerződés neve legfeljebb 256 karakterből állhat, és nem tartalmazhatja a következő karaktereket: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /** . A szóközök engedélyezettek a névben.

    - **Kiadó** (kötelező). Amikor elkezdi beírni a kiadó nevét, a szolgáltatás lekérdezi a beírt betűket tartalmazó összes kiadónevet. Ha például a „soft” karaktereket írja be, a szolgáltatás lekérdezi a „soft” karakterláncot tartalmazó összes kiadónevet, például a „Microsoft” és a „Microsoft Research” kiadókat. A kiadóneveket a rendszer a Szoftverállomány-katalógusból kérdezi le. A terméknév beírása előtt ki kell választania a kiadót.

        > [!IMPORTANT]
        > Előfordulhat, hogy a hozzáadni kívánt vállalat nem jelenik meg a listán. Szoftverszerződést kizárólag a szoftverállomány-katalógusban szereplő vállalatok számára adhat hozzá. A Microsoft azonban folyamatosan igyekszik bővíteni a legnépszerűbb szoftverek listáját. Ha szeretné, hogy egy adott vállalat felkerüljön a listára, az [Intune Uservoice webhelyén](https://microsoftintune.uservoice.com/) küldheti be erre vonatkozó kérelmét.

    - **Terméknév** (kötelező). Amikor elkezdi beírni a terméknevet, a szolgáltatás lekérdezi a beírt betűket tartalmazó összes terméknevet. A **Terméknév** megadása előtt meg kell adnia egy **Kiadót**.

    - **Licencszám** (kötelező). Adja meg a megvásárolt licencek számát.

    - **Licenc kezdő dátuma**. Adja meg a licenc érvényességének kezdő dátumát.

    - **Licenc záró dátuma**. Adja meg a licenc érvényességének záró dátumát.

    - **Szerződésadatok**. Opcionálisan megadhat kapcsolattartási adatokat, regisztrációs kulcsokat és más információkat.

5. A **Licenccsoport kiválasztása** területen tegye a következők valamelyikét:

    - Válassza **A szerződések hozzáadása a Nem hozzárendelt szerződések csoporthoz** lehetőséget, ha az új szerződéseket nem szeretné hozzáadni egy új vagy meglévő licenccsoporthoz. A szerződéseket bármikor hozzáadhatja felhasználói licenccsoportokhoz.

    - Válassza a **Szerződések hozzáadása új licenccsoporthoz** lehetőséget az új szerződések hozzáadásához egy új licenccsoporthoz. Meg kell adnia az új licenccsoport nevét.

    - Válassza a **Szerződések hozzáadása meglévő licenccsoporthoz** lehetőséget az új szerződések hozzáadásához egy meglévő licenccsoporthoz. A **Csoport neve** listában válassza ki azt a licenccsoportot, amelyhez a szerződéseket hozzá szeretné adni.

6. Válassza az **OK** gombot.

Megjelenik a **Minden szerződés** listanézet.

## <a name="manage-license-agreements"></a>Licencszerződések kezelése
A szoftverlicenc-szerződéseket licenccsoportokhoz lehet hozzáadni. A licenccsoportokkal a szervezete számára ésszerű egységekbe rendezheti a licencszerződéseket. Ezenkívül törölheti a korábban létrehozott licencszerződéseket.


|                            |                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Feladat            |                                                                                                                                                                                 Details                                                                                                                                                                                  |
|   Licenccsoport létrehozása   |                                                            A <strong>Licencek</strong> munkaterület <strong>Áttekintés</strong> lapján válassza a <strong>Feladatok</strong> menü <strong>Licenccsoport létrehozása</strong> parancsát. <strong>Megjegyzés:</strong> legfeljebb 500 licenccsoportot hozhat létre.                                                             |
|   Licenccsoport átnevezése   |                                                                                                      Válasszon egy licenccsoportot a <strong>Licencek</strong> munkaterületen, majd válassza a <strong>Feladatok</strong> menü <strong>Licenccsoport szerkesztése</strong> elemét.                                                                                                       |
|   Licenccsoport törlése   |                                 Válasszon egy licenccsoportot a <strong>Licencek</strong> munkaterületen, majd válassza a <strong>Feladatok</strong> menü <strong>Licenccsoport törlése</strong> parancsát. <strong>Tipp:</strong> a törölt csoportban lévő összes licenc a <strong>Hozzá nem rendelt szerződések</strong> licenccsoportba kerül.                                 |
| Licencszerződések törlése | A <strong>Licencek</strong> munkaterületen válasszon egy szerződést, majd válassza a <strong>Törlés</strong> elemet. <strong>Tipp:</strong> Mennyiségi licencszerződések törlése után a licencinformációk frissítéséhez válassza a <strong>Licencek áttekintése</strong> lap vagy az adott licenccsoport <strong>Általános</strong> lapjának <strong>Frissítés most</strong> elemét. |

