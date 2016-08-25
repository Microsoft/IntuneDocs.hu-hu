---
title: "A felhasználói és eszközcsoportok megtervezése | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 82ab2dbfada6c0745195da149d5f0dc1948ceb92
ms.openlocfilehash: e89d8384532b994d810649fc07c698237e2f3cec


---

# A felhasználói és eszközcsoportok megtervezése
Az Intune csoportjai nagyfokú rugalmasságot biztosítanak az eszközök és felhasználók kezeléséhez. Csoportokat állíthat be a szervezet igényeinek megfelelően a következő szempontok szerint:

- Földrajzi hely
- Részleg
- Hardverjellemzők
- Operációs rendszer
- Felhasználói tulajdonú eszköz vagy vállalati tulajdonú eszköz


## Az Intune-csoportok működése


Az Intune felügyeleti konzoljában a Csoportok csomópont alapértelmezett nézete a következő:

![Képernyőfelvétel az Intune felügyeleti konzoljában található Csoportok csomópont alapértelmezett nézetéről](/intune/media/Intune_Planning_Groups_Default_small.png)

A házirendek csoportokra vannak telepítve, ezért a csoporthierarchia az egyik fő tervezési szempont. Azt is fontos tudni, hogy a csoportok szülőcsoportja nem módosítható a csoport létrehozása után, így a csoportok tervezése kritikus fontosságú az Intune szolgáltatás használatának megkezdésétől. A következőben ajánlott eljárásokat találhat a csoporthierarchia a szervezeti igények szerinti tervezéséhez.

## A csoportok tagsági szabályai

1. Egy csoport vagy felhasználókból, vagy eszközökből állhat, de a kettő keverékéből nem.

    * **Eszközcsoportok:** Ide tartoznak a számítógépek és a mobileszközök. A számítógépek csoportokba való felvételéhez be kell léptetnie őket. Mielőtt hozzáadhatna egy mobileszközt egy csoporthoz, a környezetet úgy kell konfigurálni, hogy támogassa a mobileszközöket, és az eszközöket be kell léptetni, vagy az Exchange ActiveSync szolgáltatásnak észlelnie kell az eszközt.

    * **Felhasználói csoportok:** Egy csoport biztonsági csoportokba tartozó felhasználókat is tartalmazhat. Ezek az Active Directoryból szinkronizált csoportok. Ha nem használ Active Directory-szinkronizálást, manuálisan is létrehozhat ilyen csoportokat.

2. Egy eszköz vagy felhasználó több csoporthoz is tartozhat.

3. Egy csoport a következő tagsági szabályok alapján tartalmazhat vagy zárhat ki tagokat:

    * **Feltételalapú tagság:** Ezek olyan dinamikus szabályok, amelyek futtatásával az Intune felveszi vagy kizárja a tagokat. Ezek a feltételek **biztonsági csoportokat** és a helyi Active Directoryból (AD) szinkronizált más információkat használnak. Ha a biztonsági csoport vagy a szinkronizált adatok módosulnak, akkor a csoport tagsága is megváltozhat az Active Directoryval történő szinkronizáláskor.

    * **Közvetlen tagság:** Ezek olyan statikus szabályok, amelyek kifejezetten hozzáadnak vagy kizárnak bizonyos tagokat. A tagsági lista statikus.

4. Az Active Directory tartományi szolgáltatások (AD DS) használata nem szükséges felhasználói csoportok, illetve felhasználókat vagy számítógépeket tartalmazó eszközcsoportok létrehozásához, azonban mobileszközök eszközcsoportokba való felvételéhez a környezetet konfigurálni kell a mobileszközök támogatására.

    Az eszközöket ezenkívül észlelni kell, és hozzá kell adni az Intune-hoz.

## A csoportok kapcsolati szabályai

1. Minden létrehozott csoportnak rendelkeznie kell egy szülőcsoporttal, amely a csoport létrehozása után nem módosítható.

2. Amikor felhasználókat vagy eszközöket ad hozzá egy gyermekcsoporthoz, vegye figyelembe a következőket:

    * A gyermekcsoportok mindig a szülőcsoport részhalmazai.

    * A gyermekcsoporthoz hozzáadott új tagok automatikusan tagjává válnak az adott szülőcsoportnak is.

    * Nem adhat hozzá olyan tagot egy gyermekcsoporthoz, amely ki van zárva a szülőcsoportból.

3. A szülőcsoport tagsága meghatározza a gyermekcsoport rendelkezésre álló tagságát is.

4. Ha töröl egy szülőcsoportot, annak minden gyermekcsoportja is törlődik.

5. Tartalmakat és házirendeket a gyermekcsoportok kihagyásával is telepíthet a szülőcsoportok számára.

6. Egy gyermekcsoporthoz hozzáadhat olyan felhasználót vagy eszközt, amely nem tagja a szülőcsoportnak. Ilyenkor az új tag a szülőcsoport tagjává is válik.

    Nem adhat hozzá azonban olyan tagot egy gyermekcsoporthoz, amely ki van zárva a szülőcsoportból.

7. A csoporttagság rekurzív. Példa:

    * **Pat** csak egyetlen csoport, a **Laptopfelhasználók** biztonsági csoport tagja.

    * A **Laptopfelhasználók** csoport a **Jóváhagyott felhasználók** biztonsági csoport tagja.

    * Létrehoz egy csoportot az Intune-ban, amely a **Jóváhagyott felhasználók** csoport tagjait magában foglaló dinamikus tagságlekérdezést használ. Ennek eredményeképpen **Pat** az Intune felhasználói csoport tagja lesz.

> [!TIP]
> A csoportok létrehozásakor gondolja át a házirend alkalmazási módját. Például rendelkezhet az eszköz operációs rendszerére szabott házirendekkel, illetve a szervezeten belüli különböző szerepeknek vagy az Active Directory-ban már megadott szervezeti egységeknek megfelelő házirendekkel. Bizonyos esetekben hasznos lehet az iOS, Android és Windows operációs rendszerekhez rendelt eszközcsoportok, valamint az egyes szervezeti szerepekhez tartozó felhasználói csoportok létrehozása.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## Beépített csoportok
Az Intune kilenc olyan beépített csoportot tartalmaz, amelyek nem szerkeszthetők vagy törölhetők: <!--maybe a screen shot would be best?-->

-   **Minden felhasználó**
    -   Nem csoportosított felhasználók
-   **Minden eszköz**
    -   Minden számítógép
    -   Minden mobileszköz
        -   Minden közvetlenül felügyelt eszköz
        -   Minden, az Exchange ActiveSync által felügyelt eszköz
    -   Minden vállalati tulajdonú eszköz
    -   Nem csoportosított eszközök

> [!NOTE]
> Mottó: *legyen egyszerű*. Ha a szervezetben nincsenek az alább leírtakhoz hasonló speciális igények, hosszú távon kezelhetőbb lesz a szolgáltatás, ha az egyszerűségre törekszik, és az alapértelmezett csoportszerkezetet és házirendeket használja. A karbantartás egyszerűbb, ha egyformán kezelheti a felhasználókat csoportok szerint, így kevesebb házirendet kell fenntartania.


### A szervezetben lévő összes felhasználó és eszköz
Definiáljon szülőcsoportot a szervezet összes felhasználójához és eszközéhez, mivel valószínűleg lesznek olyan házirendjei, amelyek mindegyikre érvényesek. Erre a célra használhatja az Intune alapértelmezett **Minden felhasználó** és **Minden eszköz** csoportját. A **Minden felhasználó** és a **Minden eszköz** szülőcsoport gyermekei lehetnek azok az alcsoportok, amelyek a jellemzők szerint rendezik az eszközöket, ilyen lehet például a saját tulajdonú eszközök (BYOD) alcsoportja és a vállalati tulajdonú eszközök (CO) alcsoportja.

## A csoportok testreszabása a szervezetnek megfelelően

### BYOD és vállalati tulajdonú eszközök
Ha a szervezet engedélyezi a dolgozóknak a saját eszközök használatát a munkahelyen (BYOD), vállalati tulajdonú eszközöket (CO) biztosít a dolgozóknak, vagy mindkét módszert használja, azt javasoljuk, hogy a házirendeket e két eszközkategória alapján alkalmazza.

BYOD vagy vegyes használat esetében a házirendek tervezésekor ügyeljen arra, hogy ne sértse meg a helyi adatvédelmi előírásokat. Hozzon létre egy szülőcsoportot minden felhasználóhoz, aki a saját eszközét fogja használni. Ezzel a csoporttal azután a kategória összes felhasználójára érvényes házirendeket alkalmazhat.

![Képernyőfelvétel a BYOD szülőcsoport létrehozásáról](/intune/media/Intune_Planning_Groups_BYOD_small.png)

Hasonlóképpen létrehozhat egy csoportot a szervezetben lévő CO-felhasználók számára:

![Képernyőfelvétel a BYOD és a CO felhasználói testvércsoportról](/intune/media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### Csoportok földrajzi régiókhoz
Ha a szervezetének adott régiókhoz van szüksége házirendekre, az adott földrajzi régió alapján hozhat létre csoportokat. Ezeket a csoportokat létrehozhatja az Active Directoryban (AD) már létrehozott regionális csoportok alapján, és szinkronizálhatja azokat Azure AD-be. Másik megoldásként közvetlenül az Azure AD-ben is létrehozhatja a csoportokat.

Ezek a képernyőfelvételek a helyszíni AD-ről szinkronizált csoportokon alapuló Intune-csoportok létrehozását mutatják be. Ezek a példák feltételezik, hogy egy **US Users Group** nevű AD biztonsági csoporttal rendelkezik.

1. Először adja meg az általános információkat.

![Képernyőfelvétel a Csoport szerkesztése területről](/intune/media/Intune_Planning_Groups_AD_General_small.png)

A Tagság területen válassza az Active Directoryból szinkronizált **US Users Group** csoportot a tagsági szabályok alatt használni kívánt biztonsági csoportként.

![Csoport szerkesztése párbeszédpanel](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

Tekintse át ezt, majd kattintson a **Befejezés** gombra a csoport létrehozásának befejezéséhez.

![Csoport szerkesztése párbeszédpanel](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

A példánkban egy Middle East and Asia (MEA) csoportot is létrehoztunk.

> [!NOTE]
> [!NOTE] Ha a csoporttagság nem a biztonsági csoport tagsága alapján van feltöltve, ellenőrizze, hogy Intune-licenceket rendelt-e ezekhez a tagokhoz.

### Csoportok adott hardverekhez
Ha a szervezetének olyan házirendekre van szüksége, amelyek adott hardvertípusokra vonatkoznak, ezen követelmény alapján hozhatja létre a csoportokat. Ezeket a csoportokat létrehozhatja a helyszíni AD-ben már létrehozott csoportok alapján, és szinkronizálhatja azokat Azure AD-be. Másik megoldásként közvetlenül az Azure AD-ben is létrehozhatja a csoportokat. Ebben a példában a **US Users Group** csoportot használjuk a **Laptop Users** csoport szülőjeként.

![A Biztonsági csoport kiválasztása párbeszédpanel](/intune/media/Intune_Planning_Groups_Laptop_small.png)

Ezen a ponton a csoportok hierarchiája az alábbi módon jelenik meg. Ahogyan a képen látható, tagok találhatóak a **Laptop Users** Intune-csoportban. Az erre a csoportra alkalmazott házirendek a US régió BYOD laptopfelhasználóira érvényesek.

![A Laptopfelhasználók csoport](/intune/media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### Csoportok adott operációs rendszerekhez
Ha a szervezetének olyan házirendekre van szüksége, amelyek meghatározott operációs rendszerre, például Android, iOS vagy Windows rendszerre vonatkoznak, ezen követelmény alapján hozhatja létre a csoportokat. Az előző példához hasonlóan ezeket az operációs rendszerre vonatkozó csoportokat létrehozhatja a helyszíni AD-ben már létrehozott csoportok alapján, és szinkronizálhatja azokat Azure AD-be. Másik megoldásként közvetlenül az Azure AD-ben is létrehozhatja a csoportokat.

Az előző példákban bemutatott módszerrel létrehozhatunk olyan csoportokat,<!--devices?--> amelyek az egyes operációs rendszereket használó felhasználókat tartalmazzák.

> [!NOTE]
> [!NOTE] Ha a felhasználói többféle mobilplatformot/operációs rendszert használnak, és nincs automatikus módszere a felhasználók kategorizálására Android-felhasználóként, iOS-felhasználóként vagy Windows-felhasználóként, érdemes lehet eszközszinten alkalmazni házirendeket, mivel ez nagyobb rugalmasságot nyújt az operációs rendszerre jellemző házirendek alkalmazásában.
>
> Nem létesíthet csoportokat dinamikusan az eszköz operációs rendszere alapján. Ezt AD vagy AAD biztonsági csoportokkal tegye.

![A Laptopfelhasználók csoport](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

Ha az összes felhasználói csoport fel van töltve ezen szervezeti követelmények alapján, a csoporthierarchiának a következőképpen kell kinéznie:

![A csoportok hierarchikus nézete](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Ezzel a hierarchiával megfelelően alkalmazhatja a szervezet házirendjeit.

### Eszközcsoportok
Az alábbi módon is létrehozhat hasonló csoportokat az eszközökhöz, egy szélesebb körű csoporttal kezdve, amelybe beletartozik az összes alkalmazotti tulajdonú eszköz a BYOD forgatókönyvhöz:

![Csoport létrehozása párbeszédpanel](/intune/media/Intune_Planning_Groups_Device_General_small.png)

Válassza a **Minden eszköz (számítógépek és mobil)** elemet, hogy a csoport tartalmazza az összes BYO eszközt:

![A Tagság feltételeinek meghatározása oldal](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

Tekintse át ezt, majd kattintson a **Befejezés** gombra a BYOD csoport létrehozásához.

![Csoport létrehozása párbeszédpanel](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

Folytassa az eszközcsoportok létrehozását, amíg a felhasználóicsoport-hierarchiához hasonló eszközcsoport-hierarchiával nem rendelkezik. Ezután az Intune-konzolon a csoportcsomópontnak ehhez hasonlóan kell kinéznie:

![Az Intune-csoportok hierarchikus nézete](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## Csoporthierarchiák és elnevezési konvenciók
A házirendek felügyeletének megkönnyítéséhez az javasoljuk, hogy a cél, a platform és azon hatókör alapján nevezze el az egyes házirendeket, amelyre alkalmazza azokat. Az elnevezési szabványnak érdemes követnie a házirendek alkalmazásának előkészítésekor létrehozott csoportszerkezetet.

A US regionális szinten az összes szervezeti, androidos és mobileszközre alkalmazott Android-házirend esetén például a házirend neve a következő lehet: **CO_US_Mob_Android_General**.

![Android-házirend létrehozása](/intune/media/Intune_planning_policy_android_small.png)

A házirendek ilyen módon történő elnevezésével gyorsan azonosíthatja a házirendeket, valamint azok kívánt célját és hatókörét a konzol házirendcsomópontjából, ahogy ezt a következő ábra is szemlélteti:

![Intune-házirendek listája](/intune/media/Intune_planning_policy_view_small.png)

## További lépések
[Csoportok létrehozása](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


