---
title: "A feltételes hozzáférés hibaelhárítása| Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4f79d2890c450a803bfb84ffa3c12b0de58a158c
ms.openlocfilehash: 373b9bf9794840f999d5e5b21fc411ff621a23e1


---

# A feltételes hozzáférés hibaelhárítása

Ez a témakör ismerteti a teendőket abban az esetben, ha a felhasználók nem tudnak hozzáférni az erőforrásokhoz az Intune feltételes hozzáférésével. 

### A sikeres feltételes hozzáférés alapjai

A feltételes hozzáférés megfelelő működéséhez az alábbi feltételeknek kell teljesülnie:

-   Az eszköznek az Intune által felügyeltnek kell lennie.
-   A felhasználónak regisztrálva kell lennie az Azure Active Directoryban (AAD)
-   Az eszköznek meg kell felelnie az Intune-ban megadott megfelelőségi házirendeknek. 
-   Az eszközön aktiválni kell az EAS-t, ha a felhasználó nem az Outlookon, hanem az eszköz natív levelezőprogramján keresztül fér hozzá az e-mailjeihez.

Az egyes eszközökre vonatkozó feltételek megtekinthetők az Azure felügyeleti portálon, valamint az eszköz könyvtárjelentésében.





Az e-mailek vagy a SharePoint megnyitásakor a felhasználóknak a rendszer általában egy regisztrálási kérelmet jelenít meg. A kérés a vállalati portálra irányítja a felhasználót. Itt olvashat a helyzet magyarázatairól és a javasolt megoldásokról:

## Modern hitelesítéssel kapcsolatos forgatókönyvek

### Regisztrációs problémák

 -  Az eszköz nincs regisztrálva, így a regisztrálás megoldja a problémát.
 -  A felhasználó regisztrálta az eszközt, de a munkahelyi csatlakoztatás sikertelen volt. A felhasználónak frissítenie kell a regisztrációt a vállalati portálról. 
 
### Megfelelőségi problémák

 -  Az eszköz nem felel meg az Intune házirendjeinek. A leggyakoribb probléma ebben az esetben a titkosítás és a jelszókövetelmények. A rendszer átirányítja a felhasználót a vállalati portálra, ahol konfigurálhatja az eszköz megfelelőségét.
 -  IOS-eszközök esetében egy meglévő, a felhasználó által létrehozott e-mail-profil letilthatja a megfelelő profilnak (amelyet az Intune-rendszergazda hozott létre) az Intune-ból történő telepítését. Ez gyakori probléma, mivel az iOS-felhasználók gyakran hoznak létre egy e-mail-profilt a regisztráció előtt. A vállalati portál tájékoztatja a felhasználót, hogy a manuálisan beállított e-mail-profil sérti a megfelelőségi házirendet, és megkéri, hogy távolítsa el a profilt. A felhasználónak ekkor törölnie kell az e-mail-profilt, hogy az Intune-profilt telepíthesse. A probléma elkerülése érdekében kérje meg a felhasználókat, hogy e-mail-profil telepítése nélkül regisztráljanak, és engedélyezzék az Intune-nak, hogy telepítse a profilt.  
 -  A megfelelőségi adatok regisztrálása az eszközön időbe telhet. Várjon néhány percet, és próbálkozzon újra.

### Szabályzattal kapcsolatos problémák

Ha a megfelelőségi házirend létrehozásakor hozzákapcsolja azt egy e-mail-házirendhez, mindkét házirendet ugyanannál a felhasználónál kell üzembe helyezni, így érdemes jól megfontolni, hogy melyik házirendet melyik csoport számára helyezi üzembe. A csak az egyik házirenddel rendelkező felhasználók eszközei valószínűleg nem fognak megfelelni.


## Exchange ActiveSync-forgatókönyvek


- A regisztrált és megfelelő Android-eszközök is kaphatnak karanténba helyezésről szóló értesítést a vállalati erőforrásokhoz való hozzáféréskor. A **Kezdés** nevű hivatkozásra kattintás előtt a felhasználónak meg kell győződnie arról, hogy a vállalati portál nem volt megnyitva az erőforrásokhoz való hozzáféréskor. A felhasználónak be kell zárnia a vállalati portált, újra meg kell próbálnia hozzáférni a vállalati erőforrásokhoz, majd ez után kell a **Kezdés** nevű hivatkozásra kattintania.

- A kivont eszközök a kivonás után még több óráig rendelkezhetnek hozzáféréssel. Ennek az az oka, hogy az Exchange hat órán át gyorsítótárazza a hozzáférési jogosultságokat. Ebben az esetben érdemes más adatvédelmi megoldást keresnie a kivont eszközökre.
- Lehetséges probléma: az EASID nem javítható az AAD-re. Ennek a problémának az oka leggyakrabban a szabályozás. Várjon néhány percet, és próbálkozzon újra. 

## Az OWA-postaláda naplófájljainak gyűjtése

Ha az Exchange kapcsolódási problémái a hibaelhárítás után is fennállnak, gyűjtse össze az OWA-postaláda naplófájljait, majd vegye fel a kapcsolatot a Microsoft támogatással a [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Hogyan kérhet támogatást az Intune-hoz) című cikkben leírtak szerint.

1. Jelentkezzen be az OWA-n keresztül, és kattintson a jobb felső sarokban, a neve mellett található beállítások (fogaskerék) ikonra. 
2. Kattintson a **Beállítások** lehetőségre
3. Válassza a **Telefon** (vagy **Mobileszközök**) lehetőséget a bal oldali oszlopban.
4. A felső menüben kattintson a **Mobileszközök** elemre. 
5. Válassza ki az eszközét a listából, majd válassza a **Naplózás megkezdése** lehetőséget. 
6. Ha a rendszer kéri, kattintson az **Igen** lehetőségre az előugró párbeszédpanelen. 
7. Hajtsa végre újra a hibát okozó műveletet, hogy reprodukálja azt. 
8. Várjon 1-2 percet, majd térjen vissza az OWA telefonlistájához (győződjön meg arról, hogy kiválasztotta benne a telefonját), és a felső menüben válassza a **Napló beolvasása** lehetőséget. 
9. Ekkor egy melléklettel ellátott e-mailt kell kapnia a saját címéről. A támogatási jegy megnyitásakor küldje el az e-mail tartalmát a Microsoft támogatásnak.


### További lépések
Ha ezek a hibaelhárítási információk nem oldották meg a problémát, forduljon a Microsoft támogatási szolgálatához a [Hogyan kérhet támogatást a Microsoft Intune-hoz](how-to-get-support-for-microsoft-intune.md) című témakörben leírtak szerint.



<!--HONumber=Jun16_HO4-->


