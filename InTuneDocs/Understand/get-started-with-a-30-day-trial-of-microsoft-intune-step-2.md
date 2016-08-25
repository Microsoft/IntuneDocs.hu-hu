---
title: "Felhasználók hozzáadása a Microsoft Intune 30 napos próbaidőszakában | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6cb729533107d511fa0cc863ec6ab842e7624982
ms.openlocfilehash: 15e641f4f5f60c4a3eb3a7b09cab8cb9ef788cba


---

# Felhasználók hozzáadása a Microsoft Intune 30 napos próbaidőszakában
A fiók beállítását követően az **Új felhasználók** varázslóval egyenként, a **Felhasználók tömeges hozzáadása** varázslóval pedig egyszerre több felhasználói fiókot adhat hozzá az Intune-hoz (lásd az ebben a részben található útmutatást).  Mielőtt hozzáfogna, fontos tisztában lennie azzal, hogy az Intune miként kezeli a rendszergazdai fiókokat.

A bérlői rendszergazda az Office 365 felügyeleti központja használatával adhat hozzá felhasználókat a Microsoft Intune **Felhasználók** csoportjához. A felhasználók  **Felhasználók** csoporthoz való hozzáadásával Intune-előfizetési licenceket rendel hozzá a felhasználókhoz, és ezzel egyúttal megjeleníti őket a Microsoft Intune felügyeleti konzolján.

Az Office 365 felügyeleti központjában csak normál felhasználói Intune-fiókok hozhatók létre, rendszergazdai fiókok nem. A felhasználókhoz írásvédett vagy teljes hozzáférést biztosító rendszergazdai jogosultságokat rendelhet hozzá a felügyeleti konzol használatával a **Felügyelet** munkaterület **Rendszergazdák kezelése** lapján. Az írásvédett hozzáféréssel rendelkező szolgáltatás-rendszergazdák nem módosíthatják az Intune-beállításokat, de az adatokat megtekinthetik, és jelentéseket is futtathatnak. A teljes hozzáféréssel rendelkező szolgáltatás-rendszergazdák minden elérhető felügyeleti funkció ellátására jogosultak.

Az Intune felügyeleti konzolján megtekintheti a bérlői rendszergazda adatait, bérlői rendszergazdát azonban a konzol használatával nem hozhat létre. Alapértelmezés szerint az előfizetés tulajdonosa a Microsoft Intune szolgáltatás bérlői rendszergazdájaként teljes hozzáféréssel rendelkezik mind az Office 365 felügyeleti központjához, mind az Intune felügyeleti konzoljához. Javasoljuk, hogy hozzon létre legalább egy további bérlői rendszergazdafiókot az Office 365 felügyeleti konzoljának használatával a feladatok delegálására, illetve annak érdekében, hogy elkerülje az Intune szolgáltatás-rendszergazdai fiókjából való kizárást, ha elfelejti a jelszavát.

## Felhasználói fiókok egyesével történő hozzáadása
Az alábbi lépéseket követve adhat hozzá további felhasználói fiókokat próbaverziós bérlői fiókjához. A rendszer minden hozzáadott felhasználói fiókot az Intune ingyenes próbaverziójának részeként rendelkezésre álló 100 licencből von le.

1.  Az [Office 365 felügyeleti központjában](http://go.microsoft.com/fwlink/?LinkID=787455) válassza a **Felhasználó hozzáadása** &gt; **Új**&gt; **Felhasználó** elemet az **Új felhasználók** varázsló elindításához.

2.  A **Rrészletek** lapon töltse ki a kötelező mezőket.

3.  A **Beállítások** lapon állítsa be a felhasználói **helyet** .

4.  Az alapértelmezések elfogadásához és a felhasználói fiók Intune-licenccel való ellátásához a **Csoport** oldalon válassza **Tovább** lehetőséget.

5.  Az **E-mail** lapon adjon meg legfeljebb öt e-mail címet, amelyekre értesítés fog érkezi a fiókhoz tartozó felhasználónévvel és ideiglenes jelszóval. Az e-mail címeket pontosvesszővel (;) válassza el. Ha elkészült, kattintson a **Létrehozás** gombra a felhasználónak az előfizetéséhez való hozzáadásához.

6.  Az **Eredmények** lapon megtekintheti az új fióknevet és az ahhoz tartozó ideiglenes jelszót. Az Intune automatikusan létrehozza az ideiglenes jelszót.

7.  Ha az új felhasználó megjelenik az Office 365 felügyeleti konzoljában, ellenőrizze, hogy az új felhasználó létrehozása sikeres volt-e:

    1.  Az [Intune felügyeleti konzoljában](https://manage.microsoft.com/) válassza a **Felügyelet** &gt; **Vállalati portál** elemet, majd görgessen a képernyő aljára. Másolja a **Munkahelyi Intune-portál** mezőben látható URL-címet.

    2.  Nyisson új böngészőablakot „adatvédelmi üzemmódban” (az Internet Explorerben kattintson az **Eszközök** &gt; **InPrivate-böngészés** parancsra), vagy nyisson új böngészőablakot egy másik eszközön, és navigáljon arra az URL-címre, amelyet az előző lépésben a vágólapra másolt. Amikor a felhasználók első alkalommal jelentkeznek be, meg kell adniuk egy új jelszót a fiókhoz.

## Több felhasználó hozzáadása egyszerre
Egyszerre több felhasználót is hozzáadhat az Intune-ban. Ehhez a **Felhasználók tömeges hozzáadása** varázslóban fel kell töltenie egy felhasználói adatokat tartalmazó CSV-fájlt. A varázslóban található hivatkozások segítségével letölthet egy üres sablont és egy CSV-mintafájlt. A CSV-fájl első sorának a felhasználói adatok oszlopainak megfelelő sorrendben megadott feliratait kell tartalmaznia. Ezután a CSV-fájlban szereplő minden felhasználó esetében meg kell adni a **felhasználónevet** (például **tibor@contoso.com**) és a **megjelenítendő nevet** (például **Lukács Tibor**).

1.  Az [Office 365 felügyeleti központjában](http://go.microsoft.com/fwlink/?LinkID=787455) válassza a **Felhasználók** &gt; **Új** elemet.

2.  Válassza a **Tömeges hozzáadás** elemet a Felhasználók tömeges hozzáadása varázsló elindításához.

3.  A **Fájl kijelölése** lapon válassza a **Tallózás** lehetőséget egy meglévő CSV-fájl megadásához és a számítógépről való betöltéséhez. Letölthet egy CSV-mintafájlt vagy üres sablonfájlt is a varázslóban található hivatkozások segítségével.

4.  Az **Ellenőrzés** lapon ellenőrizze a művelet eredményét, majd válassza a **Megjelenítés** lehetőséget a további részletek megtekintéséhez.

5.  A **Beállítások** lapon győződjön meg róla, hogy a bejelentkezési állapotnál az **Engedélyezett** érték szerepel-e, majd állítsa be a **helyet**. Ezek a beállítások a CSV-fájl által hozzáadott minden felhasználói fiókra érvényesek.

6.  A **Csoportba foglalás** lapon kattintson a **Tovább** gombra az alapértelmezések elfogadásához és egy Intune használatára feljogosító licencnek a CSV-fájl által hozzáadott felhasználói fiókokhoz történő hozzárendeléséhez. Alapértelmezés szerint a jelölőnégyzet be van jelölve, ami azt jelenti, hogy a rendszer minden felhasználói fiókhoz hozzárendel egy az Intune használatára feljogosító licencet.

7.  Az **E-mail** lapon adjon meg legfeljebb öt e-mail címet, amelyeken fogadni szeretné az Intune által az egyes fiókok számára létrehozott felhasználóneveket és ideiglenes jelszavakat tartalmazó értesítést. Az e-mail címeket pontosvesszővel (;) válassza el. Válassza a **Létrehozás** elemet a felhasználóknak az előfizetéshez való hozzáadásához.

8.  Az **Eredmények** lapon megtekintheti az egyes felhasználói fiókokhoz tartozó fiókneveket és ideiglenes jelszavakat.

Az importálással hozzáadott felhasználói fiókok ezt követően megjelennek az Office 365 felügyeleti központjának **Felhasználók** csomópontjában is. Az első alkalommal bejelentkező új felhasználóknak új jelszót kell megadniuk felhasználói fiókjukhoz.

### További lépések
Gratulálunk! Befejezte a *Microsoft Intune próbaverzió* útmutatójának 2. lépését.

>[!div class="step-by-step"]

>[&larr; **Regisztrálás próbaverzióra**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [**Csoportok létrehozása** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  



<!--HONumber=Jun16_HO4-->


