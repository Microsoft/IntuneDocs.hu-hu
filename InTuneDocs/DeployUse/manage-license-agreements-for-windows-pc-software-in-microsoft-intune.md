---
title: "Windows-számítógépes szoftverek licencszerződéseinek kezelése | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: 575b8525b8b99d06358a911b8deb24ee5de48fe1


---

# Windows-számítógépes szoftverek licencszerződéseinek kezelése a Microsoft Intune-ban
A Microsoft Intune lehetővé teszi a Microsoft mennyiségi licencszerződéseinek keretében beszerzett, valamint a Microsofttól vagy nem a Microsofttól származó, egyéb módon megvásárolt szoftverek licencszerződés-adatainak hozzáadását és kezelését. Ezek az adatok logikai csoportokba is rendezhetők.

> [!IMPORTANT]
> Ez a funkció csupán kényelmi célokat szolgál, és pontossága nem garantált. Ezek az adatok nem használhatók fel a Microsoft mennyiségi licencszerződéseknek való megfelelés ellenőrzésére. A Microsoft nem használja a gyűjtött adatokat a velünk kötött licencszerződések lehetséges megsértésének vagy betartásának vizsgálatára.
> 
> Az Intune-hoz hozzáadott licencek nincsenek hatással a szoftver használatára vonatkozó licencszerződésekre és jogosultságokra.  Ha például töröl egy licencszerződéspárt az Intune-ból, azzal nem törli és nem érvényteleníti az Ön és a Microsoft közötti licencszerződéseket.

Az Intune felügyeleti konzoljának **Licencek** munkaterületén a következőkre van lehetősége:

-   Microsoft mennyiségi licencszerződések hozzáadása és szerkesztése

-   Egyéb szoftverek licencszerződéseinek hozzáadása és szerkesztése

-   Licencek és csoportok kezelése

-   Az Intune által a Mennyiségi licencelési szolgáltatásközpont (VLSC) webhelyéről lekérdezett jogosultsági információk összehasonlítása azon Microsoft-szoftverekkel, amelyeket az Intune az Ön felügyelt Windows-számítógépein észlel.

Emellett olyan jelentéseket is létrehozhat, amelyek megjelenítik a szoftverek telepítés- és licencszámait. A licencjelentések segítséget nyújthatnak a Microsofttól és a nem Microsofttól származó szoftvercímek teljes licenchelyzetének értékelésében.

> [!TIP]
> A **Licencek** munkaterület csak akkor jelenik meg a felügyeleti konzolon, ha már legalább egy Windows-számítógépet felügyel az Intune-ügyféllel.

## Microsoft mennyiségi licencszerződések hozzáadása
Az Intune mennyiségi licencelszerződések a Microsoft mennyiségi licencszerződéseken keresztül vásárolt szoftverek licencinformációit tartalmazzák. Ha Microsoft mennyiségi licencszerződéseket szeretne hozzáadni az Intune-hoz, adja meg a szerződésszámok egyeztetett párjait. A szerződés- vagy engedélyezési számokat egyeztetni kell a megfelelő licenc- vagy regisztrációs számokkal. A szerződésszámpárokat akkor kapja meg, amikor licencszerződéseket vásárol a [Mennyiségi Licencelési Szolgáltatásközpontból (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842).

1.  A [Microsoft Intune felügyeleti konzolon](https://account.manage.microsoft.com/admin/default.aspx)kattintson az **Licencek**elemre.

2.  A **Szerződések hozzáadása** lap **Szerződés típusának kiválasztása** területén válassza a **Mennyiségi licencszerződés** lehetőséget.

3.  A **Szerződés adatainak hozzáadása** területen válasszon az alábbi lehetőségek közül:

    -   **Szerződésadatokat tartalmazó CSV-fájl feltöltése** – Kattintson a Tallózás gombra, és válassza ki a feltölteni kívánt CSV-fájlt.

        -   A fájl két vagy három oszlopot tartalmazhat: kettőt csak a szerződéspárokhoz, vagy hármat abban az esetben, ha az egyes szerződéspárokhoz rövid nevet is szeretne megadni.

        -   A szerződésszámpárokban lévő karakterek összesített száma nem lehet több 16 ASCII-karakternél.

        -   Csak az ASCII-karakterek támogatottak.

        -   A következő karakterek nem engedélyezettek a szerződés nevében: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. A szóközök engedélyezettek a névben.

        -   A fájl neve nem lehet hosszabb 128 karakternél.

        -   A fájlnak legalább egy szerződéspárt kell tartalmaznia és nem tartalmazhat 5000 szerződéspárnál többet.

        **A fájl formátuma**

        A fájl létrehozásához adja meg a szerződéspárokat egy egyszerű szöveges dokumentumban a következő formátumok egyikében, a VLSC webhelyen regisztrált szervezettípustól függően. Soronként egy szerződésszámpár szerepeljen.

        -   **Nyitottértékügyfelek:** *Szerződésszám*, *a szerződésszám ismétlése*, *szerződésnév*

        -   **Nyitott ügyfelek:** *Engedély száma*, *kapcsolódó licencszám*, *szerződésnév*

        -   **Kiemelt és vállalati ügyfelek:** *Szerződésszám*, *kapcsolódó regisztrációs szám*, *szerződésnév*

        A **Szerződések hozzáadása** űrlap új szerződések hozzáadásakor megkéri, hogy keresse meg az adott fájlt.

        A következő példában egy .csv fájl tartalma látható egy Nyitottértékügyfél esetén.

        `01-07001, 01-07001, Office agreements`

    -   **Szerződés adatainak manuális hozzáadása** – Adja meg az alábbi adatokat, majd írja be a szerződésszámpárokat az **Engedély/szerződés száma** és a **Licenc/igyénylés/ügyfél száma** mezőbe. Miután beírta mindkét számot, kattintson a **Pár hozzáadása** ikonra a számok mentéséhez, majd ha szükséges, hozzáadhat további párokat.

        -   **Szerződés neve** – Adja meg a szerződés egyedi nevét.

            A szerződésnév legfeljebb 256 karakterből állhat, és nem tartalmazhatja a következő karaktereket: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. A szóközök engedélyezettek a névben.

        -   **Engedély/szerződés száma **– Adja meg a licencpár engedély-/szerződésszámát.

        -   **Licenc/igénylés/ügyfél száma** – Adja meg a licencpár licenc-/igénylés-/ügyfélszámát.

        > [!NOTE]
        > Ha több szerződésszámpárt ad hozzá, az Intune egy szerződést hoz létre a megadott névvel, és a hozzáadott összes pár ezen szerződés részét fogja képezni.

    A **+** jelre kattintva adhat hozzá másik szerződésszámpárt, a **-** jelre kattintva pedig eltávolíthat egy korábban már megadott szerződésszámpárt.

4.  A **Licenccsoport kiválasztása** területen tegye a következők valamelyikét:

    -   **A szerződések hozzáadása a Hozzá nem rendelt szerződések csoporthoz** Válassza ezt a lehetőséget, ha az új szerződéseket nem szeretné licenccsoporthoz adni.

    -   **A szerződések hozzáadása új licenccsoporthoz** – Adja meg a használni kívánt új licenccsoport nevét.

    -   **A szerződések hozzáadása meglévő licenccsoporthoz** – A **Csoport neve** listában válassza ki azt a licenccsoportot, amelyhez a szerződéseket hozzá szeretné adni.

5.  Kattintson az **OK**gombra.

Megjelenik a **Minden szerződés** nézet, és az Intune a megadott szerződésszámpárok érvényesítése érdekében kapcsolódik a Microsoft mennyiségi licencszolgáltatási központjához.

Ha a licencszerződéseknek az Intune-hoz való hozzáadását követően szeretné frissíteni a mennyiségi licencekre vonatkozó információkat, kattintson a **Licencek – áttekintés** lap **Frissítés most** elemére. Ez a művelet lekérdezi az aktuális licencinformációkat a [Microsoft Mennyiségi Licencelési Szolgáltatásközpontból (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT]
> A mennyiségi licencelési információk frissítéséig más adatokat láthat a szerződéslistában és a **Szerződések áttekintése** lap jogosultsági információinál.

A mennyiségi licencelési információk frissítése után összehasonlíthatja a licencinformációkat az észlelt Microsoft-szoftverekkel az **Alkalmazások** munkaterületen. A következő licencjelentéseket is futtathatja:

-   **Licencvásárlási jelentések** – Lehetővé teszi a kiválasztott licenccsoportokban lévő licencelt szoftverek megtekintését a lefedettségi hézagok meghatározása érdekében.

-   **Licenctelepítési jelentések** – Megkönnyíti annak meghatározását, hogy elegendő licencszerződéssel rendelkezik-e.

> [!NOTE]
> Az összes Microsoft mennyiségi licencszerződésnél megjelenített **Terméknév** a **Nem érhető el**.

## Egyéb szoftverlicenc-szerződések hozzáadása és szerkesztése
Az Intune-hoz a Microsoft mennyiségi licencszerződésektől eltérő típusú licencszerződéseket is hozzáadhat. Ezek a szerződések kereskedőktől vásárolt Microsoft- vagy nem Microsoft-szoftvereket tartalmazhatnak.

> [!IMPORTANT]
> A szerződések hozzáadása előtt legalább egy Windows-számítógépet regisztrálnia kell az Intune-ban.  Ezenkívül legalább egy regisztrált számítógépre fel kell tölteni azt a licencelhető szoftvercsomagot, amellyel a licencszerződéseket hozzá szeretné adni.

### Egyéb szoftverszerződések hozzáadása

1.  A [Microsoft Intune felügyeleti konzolon](https://account.manage.microsoft.com/admin/default.aspx)kattintson az **Licencek**elemre.

2.  Kattintson az **Egyéb szoftverlicenc-szerződések** szakasz **Szerződések hozzáadása** elemére.

3.  Válassza a **Szerződések hozzáadása** lap **Szerződéstípus választása** szakaszának **Egyéb szoftverlicenc-szerződések** elemét.

4.  A **Szerződésadatok hozzáadása** területen adja meg a következőket:

    -   **Agreement name** (kötelező). A szerződésnév legfeljebb 256 karakterből állhat, és nem tartalmazhatja a következő karaktereket: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. A szóközök engedélyezettek a névben.

    -   **Kiadó** (kötelező). Amikor elkezdi beírni a kiadó nevét, a szolgáltatás lekérdezi a beírt betűket tartalmazó összes kiadónevet. Ha például a „soft” karaktereket írja be, a szolgáltatás lekérdezi a „soft” karakterláncot tartalmazó összes kiadónevet, például a „Microsoft” és a „Microsoft Research” kiadókat. A kiadóneveket a rendszer a Szoftverállomány-katalógusból kérdezi le. A terméknév beírása előtt ki kell választania a kiadót.

        > [!IMPORTANT]
        > Előfordulhat, hogy a hozzáadni kívánt vállalat nem jelenik meg a listán. Szoftverszerződést kizárólag a szoftverállomány-katalógusban szereplő vállalatok számára adhat hozzá. A Microsoft azonban folyamatosan igyekszik bővíteni a legnépszerűbb szoftverek listáját. Ha szeretné, hogy egy adott vállalat felkerüljön a listára, az [Intune Uservoice webhelyén](https://microsoftintune.uservoice.com/) küldheti be erre vonatkozó kérelmét.

    -   **Terméknév** (kötelező). Amikor elkezdi beírni a terméknevet, a szolgáltatás lekérdezi a beírt betűket tartalmazó összes terméknevet. A **Terméknév** megadása előtt meg kell adnia egy **Kiadót**.

    -   **Licencszám** (kötelező). Adja meg a megvásárolt licencek számát.

    -   **Licenc kezdő dátuma**. Adja meg a licenc érvényességének kezdő dátumát.

    -   **Licenc záró dátuma**. Adja meg a licenc érvényességének záró dátumát.

    -   **Szerződésadatok**. Opcionálisan megadhat kapcsolattartási adatokat, regisztrációs kulcsokat és más információkat.

5.  A **Licenccsoport kiválasztása** területen tegye a következők valamelyikét:

    -   Válassza **A szerződések hozzáadása a Nem hozzárendelt szerződések csoporthoz** lehetőséget, ha az új szerződéseket nem szeretné hozzáadni egy új vagy meglévő licenccsoporthoz. A szerződéseket bármikor hozzáadhatja felhasználói licenccsoportokhoz.

    -   Válassza a **Szerződések hozzáadása új licenccsoporthoz** lehetőséget az új szerződések hozzáadásához egy új licenccsoporthoz. Meg kell adnia az új licenccsoport nevét.

    -   Válassza a **Szerződések hozzáadása meglévő licenccsoporthoz** lehetőséget az új szerződések hozzáadásához egy meglévő licenccsoporthoz. A **Csoport neve** listában válassza ki azt a licenccsoportot, amelyhez a szerződéseket hozzá szeretné adni.

6.  Kattintson az **OK**gombra.

Megjelenik a **Minden szerződés** listanézet.

## Licencszerződések kezelése
A szoftverlicenc-szerződéseket licenccsoportokhoz lehet hozzáadni. A licenccsoportokkal a szervezete számára ésszerű egységekbe rendezheti a licencszerződéseket. Ezenkívül törölheti a korábban létrehozott licencszerződéseket.

|||
|-|-|
|Feladat|Részletek|
|Licenccsoport létrehozása|A **Licencek** munkaterület **Áttekintés** lapján kattintson a **Feladatok** menü **Licenccsoport létrehozása** parancsára. **Megjegyzés:** legfeljebb 500 licenccsoportot hozhat létre.|
|Licenccsoport átnevezése|Válasszon egy licenccsoportot a **Licencek** munkaterületen, majd kattintson a **Feladatok** menü **Licenccsoport szerkesztése** elemére.|
|Licenccsoport törlése|Válasszon egy licenccsoportot a **Licencek** munkaterületen, majd kattintson a **Feladatok** menü **Licenccsoport törlése** parancsára. **Tipp:** a törölt csoportban lévő összes licenc a **Hozzá nem rendelt szerződések** licenccsoportba kerül.|
|Licencszerződések törlése|A **Licencek** munkaterületen válasszon ki egy szerződést, majd kattintson a **Törlés** elemre. **Tipp:** Mennyiségi licencszerződések törlése után a licencinformációk frissítéséhez kattintson a **Licencek áttekintése** lap vagy az adott licenccsoport **Általános** lapjának **Frissítés most** gombjára.|






<!--HONumber=Jun16_HO4-->


