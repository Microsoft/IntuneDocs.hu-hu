---
title: "A Microsoft Intune-műveletek értelmezése jelentések segítségével | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 06/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ms.reviewer: pbala
ms.suite: ems
ms.sourcegitcommit: 617f1cd42de49f0c8675bd450591a390af674e73
ms.openlocfilehash: b8af36cef1bcb9077d0ab611a14fb88c0f458ece


---

# A Microsoft Intune-műveletek értelmezése jelentések segítségével
Ebből a témakörből megtudhatja, hogy miképpen hozhat létre és kezelhet Microsoft Intune-jelentéseket a szervezetében lévő szoftverekről, hardverekről és szoftverlicencekről.

## A jelentések használata
Az Intune-jelentések információkat nyújtanak a szervezetében lévő szoftverekről, hardverekről és szoftverlicencekről. Segítségükkel áttekintheti a szervezet aktuális szükségleteit, illetve felmérheti a jövőbeli kiadásokat. A jelentések létrehozásának és kezelésének eszközeit a **Jelentések** munkaterületen találhatja meg. A jelentésekkel kapcsolatos további információkért lásd: [A Microsoft Intune-műveletek értelmezése jelentések segítségével](understand-microsoft-intune-operations-by-using-reports.md).

### Jelentéstípusok

|Jelentés típusa|Leírás|
|---------------|---------------|
|**Frissítési jelentés**|Megjeleníti a szervezetben lévő számítógépeken végrehajtott sikeres szoftverfrissítéseket, illetve a sikertelen, függőben lévő és szükséges frissítésekről is nyújt információt. A szoftverfrissítéssel kapcsolatos további információkért lásd: [Windows rendszerű számítógépek naprakészen tartása szoftverfrissítésekkel a Microsoft Intune-ban](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Észlelt szoftverekről szóló jelentés**|Megjeleníti a szervezetben lévő számítógépeken telepített szoftvereket, a szoftver verziójával együtt. A megjelenített információkat a szoftver gyártója és kategóriája szerint szűrheti is. A listában lévő frissítések kibontásával, a listaelem mellett lévő, irányt mutató nyílra kattintva részletes információkat jeleníthet meg (például a számítógépeket, amelyeken telepítve van).<br /><br />Ha számítógépeket von ki vagy csoporttagságot módosít az Intune-ban, akkor több percig is eltarthat, mire a módosítások megjelennek az észlelt szoftverekről szóló jelentésben. Ha szeretné, hogy a szoftverleltár a lehető legpontosabb legyen, akkor a számítógépek kivonása vagy a csoporttagságuk módosítása után várjon néhány percet, mielőtt az érintett számítógépeket magában foglaló jelentést készítene.|
|**Számítógépleltár jelentés**|Információkat jelenít meg a szervezetben lévő felügyelt számítógépekről. Ezzel a jelentéssel megtervezheti a hardvervásárlásokat, és jobban átláthatja a szervezeti felhasználók hardverszükségleteit. A felügyelt számítógépekkel folytatott munkáról bővebben a következő témakörben olvashat: [Windows rendszerű számítógépek felügyelete a Microsoft Intune-nal](manage-windows-pcs-with-microsoft-intune.md).|
|**Mobileszközleltár jelentés**|Információkat jelenít meg a szervezetben használt mobileszközökről. A megjelenített információkat szűrheti csoportok és operációs rendszerek szerint, illetve aszerint, hogy az eszköz jailbreakelt vagy rootolt-e.|
|**Megvásárolt licencek jelentése**|Megjeleníti az összes licencelt szoftvert a licencszerződés típusa szerint csoportosítva. Ha a szoftverlicencadatok több mint 24 órája nem frissültek, akkor a licencjelentés generálásakor frissíti őket a rendszer. A licencjelentés nem ad garantáltan pontos képet a használt szoftverekről, és nem használható szerződéses kötelezettségek teljesítésének igazolására. A jelentés egy olyan eszköz, amely segít a vállalat licenckezelési döntéseinek a meghozatalában. Előfordulhat, hogy az Intune nem észleli az összes olyan terméket, amelyre kiterjedhet a Microsoft mennyiségi licencprogramja. A rendelkezésre álló szűrők a következők:<br /><br />A **Minden szerződés** szűrő az Intune által kezelt összes licencelt szoftvert megjeleníti.<br /><br />A **Mennyiségi licencszerződések** szűrő csak a mennyiségi licencszolgáltatási központ által kezelt szoftvertermékeket jeleníti meg.<br /><br />Az **Egyéb szoftverlicenc-szerződések** szűrő a mennyiségi licencszolgáltatási központon kívül kezelt szoftvertermékeket jeleníti meg.|
|**Licenctelepítési jelentés**|A vállalati számítógépeken telepített szoftvereket összehasonlítja a mennyiségi licencszolgáltatási központ (VLSC) adatain alapuló vállalati licencjogosultságokkal. A szűrők a következők:<br /><br />A **Minden szerződés** szűrő az Intune által kezelt összes licencelt szoftvert megjeleníti.<br /><br />A **Mennyiségi licencszerződések** szűrő csak a mennyiségi licencszolgáltatási központ által kezelt szoftvertermékeket jeleníti meg.<br /><br />Az **Egyéb szoftverlicenc-szerződések** szűrő a mennyiségi licencszolgáltatási központon kívül kezelt szoftvertermékeket jeleníti meg.|
|**Feltételek és kikötések jelentés**|Azt ismerteti, hogy a felhasználók elfogadták-e az alkalmazott használati feltételeket, és ha igen, akkor azoknak mely verzióját fogadták el. Legfeljebb 10 olyan felhasználót adhat meg, amelyeknél a rendszer megjeleníti a rájuk vonatkozó használati feltételek elfogadásának meglétét, de azt is megteheti, hogy egy rájuk vonatkozó adott feltétel elfogadási állapotát jeleníti meg.|
|**Meg nem felelő alkalmazások jelentés**|Információkat jelenít meg azokról a felhasználókról, akiknek olyan telepített alkalmazásaik vannak, amelyek szerepelnek az Ön megfelelő és meg nem felelő alkalmazásokat tartalmazó listáján. Ezzel a jelentéssel megtalálhatja azokat a felhasználókat és eszközöket, akik és amelyek nem felelnek meg a szervezete alkalmazás-házirendjeinek.|
|**Tanúsítványmegfelelőségi jelentés**|Megjeleníti, hogy mely tanúsítványok lettek kibocsátva a felhasználóknak és az eszközöknek az SCEP vagy PKCS #12 (.PFX) formátumban. Ezzel a jelentéssel megtalálhatja a kibocsátott, lejárt és visszavont tanúsítványokat.|
|**Eszközelőzmények jelentés**|Megjeleníti a korábbi kivonási, tartalomtörlési és egyéb törlési műveletek naplóját. Ezzel a jelentéssel megállapíthatja, hogy korábban ki indított műveleteket az egyes eszközökön.|
|**Állapotigazolási jelentések**|Megjeleníti a mobileszközök állapotát.|
|**Mac OS X hardverjelentés**|A kijelölt csoportokban megjeleníti az összes regisztrált Mac OS X-alapú eszköz hardveres jellemzőit. Az eszközökről gyűjtött hardverleltárakkal kapcsolatos további információkért lásd: [A regisztrált eszközök áttekintése a Microsoft Intune leltárfunkciójával](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Mac OS X szoftverjelentés**|A kijelölt csoportokban megjeleníti az összes regisztrált Mac OS X-alapú eszközön telepített szoftvereket. A jelentés a szoftver nevét (csomagazonosítóként), a rövid (vagy valódi) nevet, a verziót és a szoftverrel telepített eszközök számát tünteti fel.|

#### Jelentés létrehozása

1.  Az Intune felügyeleti konzolban kattintson a **Jelentések** lehetőségre, majd kattintson a létrehozandó jelentés típusára (az egyes típusokról bővebben a fenti leírásban olvashat).

2.  Az **Új jelentés létrehozása** lapon fogadja el az alapértelmezett értékeket, vagy állítsa be őket a jelentés által visszaadott eredmények szűrésére. Megadhatja például, hogy csak a Microsoft által kiadott szoftverek jelenjenek meg az észlelt szoftverek jelentésében.

3.  Kattintson a **Jelentés megtekintése** lehetőségre a jelentés új ablakban való megnyitásához.

Ha rendezni szeretné a jelentést az egyik megjelenített oszlop alapján, kattintson az oszlopfejlécre. Ezenkívül egyes jelentésekben a listaelemek kibontásával is további információkhoz juthat.

## A jelentésekkel végezhető további műveletek
A fentiek mellett a jelentések az alábbi műveleteket támogatják:

|Művelet|További információ|
|----------|--------------------|
|**Nyomtatás**|Kattintson a jelentésben a nyomtatás ikonjára, és kövesse az utasításokat.|
|**Exportálás**|Kattintson a jelentésben az exportálás ikonjára, és kövesse az utasításokat. Az exportáláshoz választhat CSV és HTML formátumot.|
|**Mentés**|Az **Új jelentés létrehozása** lapon minden egyes felhasználó menthet legfeljebb 100 jelentést. Adja meg a jelentés paramétereit az igényeinek megfelelően, majd kattintson a **Mentés**gombra, vagy másik név megadásához a **Mentés másként** gombra.|
|**Betöltés**|Az **Új jelentés létrehozása** lapon kattintson a **Betöltés** lehetőségre a jelentésparaméterek korábban mentett készleteinek betöltéséhez.|
|**Törlés**|A **Jelentések** munkaterületen válassza ki a kívánt jelentéstípust, kattintson a **Betöltés**lehetőségre, majd a jelentések listájában kattintson a jelentés melletti törlés (x) ikonra.|

### További információ
[Figyelés és jelentéskészítés a Microsoft Intune-ban](monitoring-and-reports-with-microsoft-intune.md)




<!--HONumber=Jun16_HO3-->


