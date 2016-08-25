---
title: "Szabályzatokkal kapcsolatos problémák elhárítása | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: ac3417781df0a5b092a70620aa7343849b1e8c82
ms.openlocfilehash: 3ac6b06b7eb85503786b4d8b0b9bd2a30d2a15e6


---

# Szabályzatokkal kapcsolatos problémák elhárítása a Microsoft Intune-ban

Az alábbiakban néhány, a Microsoft Intune szabályzatkonfigurációjából eredő problémát, valamint az elhárításukra vonatkozó javaslatot ismertetünk.

Ha ezekkel az információkkal nem tudja megoldani a problémát, a [Hogyan kérhet támogatást az Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben talál további részleteket a segítségkéréshez.


## Vonatkozik szabályzat az eszközre?
**Probléma:** Nem egyértelmű, hogy vonatkozik-e az eszközre adott szabályzat, vagy az eszköz egy szabályzattal ellentétesen viselkedik-e.

Az egyes eszközökre vonatkozó szabályzat adatainak tanulmányozásával állapítsa meg, hogy milyen hatással van egy szabályzat egy adott eszközre.

Az Intune felügyeleti konzoljában az **Eszköztulajdonságok**csoportban minden eszközhöz tartozik egy szabályzatlap. Ha nincs lap, akkor lehetséges, hogy az eszköz regisztrálása még folyamatban van, vagy nem tartozik hozzá szabályzat. Minden egyes házirend rendelkezik egy **Kívánt érték** és egy **Állapot**jellemzővel. A kívánt érték az az érték, amelyet a házirend hozzárendelésekor el kívánt érni. Az állapot az eszközre érvényes összes házirend alkalmazása, valamint a hardver és az operációs rendszer által szabott korlátozások és rendszerkövetelmények együttese alapján elért érték. A lehetséges állapotok az alábbiak:

-   **Megfelelő:**Az eszköz megkapta a szabályzatot, és jelenti a szolgáltatásnak, hogy megfelel a beállításnak.

-   **Nem alkalmazható:**A szabályzatbeállítás nem alkalmazható. Az iOS-eszközök e-mail beállításai például nem alkalmazhatók az androidos eszközökre.

-   **Folyamatban:**A rendszer elküldte a szabályzatot az eszköznek, de az nem jelentette az állapotot a szolgáltatásnak. Például az Android rendszeren csak akkor működik a titkosítás, ha a felhasználó engedélyezi, ezért függőben lehet.

Az alábbi képernyőképen két világos példa látható:

-   Az **Egyszerű jelszavak engedélyezése** beállított értéke **Igen**, ahogy az a **Kívánt érték** oszlopban látható, az **Állapot** értéke azonban **Nem alkalmazható**. Ez azért van, mert az egyszerű jelszavak az Android-eszközökön nem támogatottak.

-   Ehhez hasonlóan az **iOS-eszközök e-mail beállításai** kiterjesztett szabályzat erre az eszközre nem alkalmazható, mert ez Android-eszköz.

![Az Intune eszközszabályzat](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE] Ne felejtse el, hogy ha két különböző korlátozási szintű házirend vonatkozik egy eszközre vagy felhasználóra, akkor a gyakorlatban a szigorúbb házirend lesz érvényes.

## Házirendfrissítés és frissítési időközök
Vegye figyelembe, hogy a házirendek rendszeres időközönként frissülnek. Általában a házirendeknek a módosítások elvégzése után legfeljebb 15 perccel érvénybe kell lépniük az eszközökön. Az alábbiakban további részleteket talál a házirendek frissítésének rendszeres időközeiről:

-   **MDM-mel regisztrált Windows-eszköz**: A házirend Windows 8.1-es és Windows 10-es eszközökön 8 óránként, míg Windows RT-eszközökön 24 óránkét frissül.

-   **Windows Phone-telefon:** A házirend 8 óránként frissül. Ez a vállalati portálról történő frissítéssel kényszeríthető, a **Beállítások** területen.

-   **iOS:** A házirend naponta egyszer frissül, véletlenszerű időközönként. Ez is kényszeríthető a Vállalati portál megnyitásával, majd az eszköz kiválasztásával, és a **Szinkronizálás** lehetőség kiválasztásával.

-   **Android:** A házirend naponta egyszer frissül, véletlenszerű időközönként. Ez is kényszeríthető a Vállalati portál megnyitásával, majd az eszköz kiválasztásával, és a **Szinkronizálás** lehetőség kiválasztásával.

## Microsoft Intune-házirendekkel kapcsolatos hibák a policyplatform.log fájlban
Nem mobileszköz-felügyelet alá tartozó Windows-eszközök esetén a policyplatform.log fájlban lévő házirendhibák az eszközön lévő Windows Felhasználói fiókok felügyelete (UAC) nem alapértelmezett beállításainak eredményei lehetnek. Néhány nem alapértelmezett UAC-beállítás hatással lehet a Microsoft Intune ügyféltelepítéseire és a házirendek érvénybe léptetésére.

### Az UAC-problémák megoldása

1.  Vonja ki a számítógépet az [Eszközök kivonása a Microsoft Intune-nal való felügyelet alól](/intune/deploy-use/retire-devices-from-microsoft-intune-management) szakaszban leírtak szerint.

2.  Várjon 20 percet az ügyfélszoftver eltávolításáig.

    > [!NOTE] Ne próbálja meg eltávolítani az ügyfelet a Programok és szolgáltatások területről.

3.  A Start menüben írja be az **UAC** kifejezést a Felhasználói fiókok felügyelete beállításainak megnyitásához.

4.  Mozgassa az értesítési csúszkát az alapértelmezett beállításhoz.

## KNOX-eszköz 0x87D1FDE8-as hibája
**Probléma:** Miután létrehozott és telepített egy Samsung KNOX Exchange Active Sync e-mail-profilt különféle androidos eszközökhöz, azok az eszköz tulajdonságok &gt; szabályzat lapján jelentik a **0x87D1FDE8**-as vagy a **sikertelen szervizelés** hibát.

Ellenőrizze a Samsung KNOX EAS-profil és a forrásszabályzat konfigurációját. A Samsung Note eszközök szinkronizálási lehetősége a továbbiakban nem támogatott, és ez a lehetőség nem választható a profilban. Ellenőrizze, hogy az eszközök rendelkezésére állt-e elegendő idő (akár 24 óra) a szabályzat feldolgozásához.

## Figyelmeztetés: A hozzáférési szabályok mentése az Exchange szolgáltatásba sikertelen
**Probléma:**A felügyeleti konzolban megjelenik **A hozzáférési szabályok mentése az Exchange szolgáltatásba sikertelen**  figyelmeztetés.

Ha a felügyeleti konzol Helyszíni Exchange-szabályzat munkaterületén szabályzatot hozott létre, de O365-öt használ, az Intune nem kényszeríti ki a konfigurált szabályzatbeállítások használatát. Jegyezze fel a figyelmeztetésben szereplő szabályzatforrást.  A Helyszíni Exchange-szabályzat munkaterületen törölje az örökölt szabályokat, mivel azok a helyszíni Exchange-hez készült Intune-on belüli globális Exchange-szabályok, és nem vonatkoznak az O365-re. Ezután hozzon létre új szabályzatot az O365-höz.

## HIBA: Nem szerezhető be érték a számítógépről, 0x80041013
Ez akkor fordulhat elő, ha a helyi rendszeren lévő idő legalább öt perccel eltér a szinkronizált értéktől. Ha a helyi számítógépen lévő idő nincs szinkronban, a biztonságos tranzakciók meghiúsulnak, mert az időbélyegek érvénytelenek lesznek.

A hiba megoldásához állítsa a helyi időt a lehető legközelebb az internetes időhöz, vagy a hálózaton lévő tartományvezérlőkben megadott időhöz.

## Nem módosítható a különféle MDM-eszközök biztonsági szabályzata
A Windows Phone-telefonok és a Windows RT-eszközök nem teszik lehetővé, hogy a beállításukat követően csökkentse az MDM-en vagy az EAS-on keresztül megadott biztonsági szabályzatok biztonságát. Ilyen eset például, ha beállítja a **jelszó minimális karakterszámát** 8-ra, majd megpróbálja 4-re csökkenteni. Az eszközhöz már a szigorúbb szabályzat tartozik.

Az eszköz platformjától függően előfordulhat, hogy ha módosítani szeretné a szabályzatot egy kevésbé biztonságos értékre, alaphelyzetbe kell állítania a biztonsági szabályzatokat.
Windows RT rendszerben például pöccintsen jobbról a **Gombok** sáv megnyitásához, majd válassza a **Beállítások** &gt; **Vezérlőpult** lehetőséget.  Válassza a **Felhasználói fiókok** kisalkalmazást.
A bal oldali navigációs menü alján található egy **Biztonsági házirendek mellőzése** hivatkozás. Válassza ki, majd kattintson a **Házirendek mellőzése** gombra.
Előfordulhat, hogy egyéb MDM-eszközöket (például Android, Windows Phone 8.1 és újabb, valamint iOS) ki kell vonni, majd újból regisztrálni kell a szolgáltatásba egy kevésbé korlátozó szabályzat alkalmazásához.

## Az androidos eszközök nem kényszerítik ki a biztonságiszabályzat-változásokat a végfelhasználó jóváhagyása nélkül
Az Android MDM a többi platformtól eltérően nem teszi lehetővé a szolgáltatásnak a kezdeti szabályzatváltozások kényszerítését az eszközökön. Ez az Android működése miatt van így, és nem az Intune szolgáltatással kapcsolatos. Az androidos eszközök az értesítési ablakban figyelmeztetik a végfelhasználókat a kapcsolódó szabályzatváltozásokra (vagyis a jelszó, titkosítás stb. változására).  A végfelhasználónak válaszolnia kell a figyelmeztetésre, és az elfogadását követően alkalmaznia kell a szabályzatot.

## Nem lehet szabályzatot létrehozni vagy ügyfeleket regisztrálni, ha a vállalat neve speciális karaktereket tartalmaz.
**Hiba:** nem lehet szabályzatot létrehozni vagy ügyfeleket regisztrálni.

**Megoldás:** Az [Office 365 felügyeleti központban](https://portal.office.com/) törölje a speciális karaktereket a vállalat nevéből, és mentse a vállalati adatokat.

### További lépések
Ha ezek a hibaelhárítási információk nem oldották meg a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben leírtak szerint.



<!--HONumber=Jun16_HO3-->


