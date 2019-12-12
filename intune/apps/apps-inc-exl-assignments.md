---
title: Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban
titleSuffix: ''
description: Az Intune az alkalmazás-hozzárendelések belefoglalására vagy kizárására való használatának ismertetése.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40cbb62a620d6e174ab8acb76798ba53080b78cf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563974"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban

Az Intune-ban úgy határozhatja meg, hogy ki férhet hozzá az alkalmazáshoz, ha felhasználói csoportokat rendel hozzá akár az engedélyezéshez, akár a kizáráshoz. Mielőtt csoportokat rendelne az alkalmazáshoz, meg kell adnia az alkalmazás hozzárendelési típusát. A hozzárendelés típusával az alkalmazás elérhetővé vagy kötelezővé tehető, illetve törölhető. 

Egy alkalmazás elérhetőségének megadásakor az alkalmazás-hozzárendeléseket felhasználók vagy eszközök csoportjaira vonatkozóan végezheti el csoport-hozzárendelések belefoglalásával vagy kizárásával. Ez a funkció akkor különösen hasznos, ha nagyobb csoportok számára szeretné elérhetővé tenni az alkalmazást, majd pedig szűkíteni szeretné a felhasználók körét, miközben egy kisebb csoportot is kizárhat. A kisebb csoport lehet például tesztcsoport, vagy egy vezetői csoport. 

Ajánlott eljárásként hozzon létre és rendeljen hozzá alkalmazásokat kifejezetten a felhasználói csoportokhoz, és az eszközök csoportjaihoz külön-külön. A csoportokkal kapcsolatos további információkért lásd: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md).  

Az alkalmazás-hozzárendelések belefoglalása vagy kizárása esetén fontos forgatókönyvek találhatók:

- A kizárás elsőbbséget élvez a következő azonos csoport típusú forgatókönyvek belefoglalásakor:
    - Felhasználói csoportok belefoglalása és felhasználói csoportok kizárása az alkalmazások kiosztásakor
    - Az eszközök csoportjai és az eszközcsoport kizárása az alkalmazások hozzárendeléséhez

    Ha például a **minden vállalati felhasználó felhasználói** csoporthoz rendel hozzá egy eszközcsoport-csoportot, de kizárja a tagokat a **vezető felügyeleti munkatárs** felhasználói csoportban, akkor a **vezető felügyeleti személyzet** kivételével **minden vállalati felhasználó** megkapja a hozzárendelést, mivel mindkét csoport felhasználói csoport.
- Az Intune nem értékeli ki a felhasználók és az eszközök közötti csoportok kapcsolatait. Ha az alkalmazásokat vegyes csoportokhoz rendeli, előfordulhat, hogy az eredmények nem a kívánt vagy várt érték.

    Ha például hozzárendel egy eszközt a **minden felhasználó** felhasználói csoporthoz, de kizárja az **összes személyes** eszköz csoportot. Ebben a vegyes csoportbeli alkalmazás-hozzárendelésben **minden felhasználó** megkapja az alkalmazást. A kizárás nem vonatkozik.

Ennek eredményeképpen az alkalmazások vegyes csoportokhoz való társítása nem ajánlott.

> [!NOTE]
> Alkalmazások csoport-hozzárendelésénél a **Nem alkalmazható** típus nem használható többé, helyette a csoport kizárása lehetőség használható. 
>
> Az Intune előre létrehozott, **Minden felhasználó** és **Minden eszköz** csoportokat biztosít a konzolon. A csoportok beépített optimalizációkkal bírnak a felhasználók kényelme érdekében. Mindenképpen ajánlott ezeket a csoportokat használni az összes felhasználó és az összes eszköz megcélzására az Ön által létrehozott „Minden felhasználó” vagy „Minden eszköz” csoport helyett.  
>
> A vállalati Android támogatja a csoportok belefoglalását és kizárását. Kihasználhatja a beépített **Minden felhasználó** és **Minden eszköz** csoportot a Vállalati Android-alapú alkalmazástársításokhoz. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>Csoportok belefoglalása és kizárása alkalmazások hozzárendelésénél 
Ha csoportokhoz szeretne alkalmazást hozzárendelni a belefoglalás és kizárás használatával, tegye a következőket:
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás**lehetőséget. Megjelenik a hozzáadott alkalmazások listája.
3. Válassza ki a hozzárendelni kívánt alkalmazást. Megjelennek az alkalmazás adatai egy irányítópulton. 
4. A menü **Kezelés** szakaszában válassza a **Hozzárendelések**. elemet. 

    ![Alkalmazás-hozzárendelések belefoglalása alkalmazások hozzárendelésekor](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)

5. Az alkalmazáshoz hozzárendelt felhasználói csoportok hozzáadásához válassza a **Csoport hozzáadása** lehetőséget. 
6. A **Csoport hozzáadása** panelen válasszon egy **Hozzárendelési típust** az elérhető típusok közül.
7. Hozzárendelési típusként válassza ki az **Elérhető regisztrációval és anélkül** lehetőséget.

    ![Alkalmazás-hozzárendelések az Intune-ban – Csoport hozzáadása](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
8. A **Belefoglalt csoportok** lehetőséggel választhatja ki azokat a felhasználói csoportokat, amelyek számára elérhetővé szeretné tenni az alkalmazást.

    > [!NOTE]
    > Csoportok hozzáadásakor, ha bármely más csoport már bele lett foglalva egy adott hozzárendelés-típus esetében, az alkalmazás előre ki van jelölve, és nem módosítható más belefoglalási hozzárendelés-típusok esetében. Az használatba vett csoport nem használható belefoglalt csoportként.

9. Az **Igen** választásával teheti elérhetővé az alkalmazást minden felhasználó számára.

    ![Alkalmazás-hozzárendelések az Intune-ban – Csoportok belefoglalása](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
10. Kattintson az **OK** gombra a csoport belefoglalásához.
11. A **Kizárt csoportok** lehetőséggel válassza ki azokat a felhasználói csoportokat, amelyek számára nem szeretné elérhetővé tenni az alkalmazást. 
12. Válassza ki a kizárni kívánt csoportokat. Így az alkalmazás nem érhető el ezekhez a csoportokhoz.

    ![Alkalmazás-hozzárendelések az Intune-ban – Csoportok kizárása](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
13. A csoportkiválasztás befejezéséhez kattintson a **Kiválasztás** lehetőségre.
14. A **Csoport hozzáadása** panelen kattintson az **OK** gombra. Megjelenik az alkalmazáshoz tartozó **Hozzárendelések** listája.
15. A **Mentés** lehetőségre kattintva aktiválhatja az alkalmazásra vonatkozó csoport-hozzárendeléseket.

Csoport-hozzárendelések esetén a már hozzárendelt csoportok nem módosíthatók. Ha jelenleg nem elérhető csoportot szeretne kiválasztani, akkor először távolítsa el az alkalmazást az alkalmazás hozzárendelési listájából. 

A hozzárendelések szerkesztéséhez az alkalmazás **Hozzárendelések** listájában válassza ki azt a sort, amely a módosítandó hozzárendelést tartalmazza. Ezen kívül úgy is eltávolíthat hozzárendelést, ha a sor végén található három pontra ( **…** ) kattint, majd az **Eltávolítás** lehetőséget választja. A **Hozzárendelések** lista megjelenítésének módosításához **Hozzárendelési típus** vagy **Belefoglalt/Kizárt** állapot szerint csoportosíthat.

![Alkalmazás-hozzárendelések az Intune-ban – befejezés](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>További lépések

- További információt az alkalmazások csoport-hozzárendelésénél alkalmazható belefoglalásról és kizárásról a [Microsoft Intune blogján](https://aka.ms/new_app_assignment_process) találhat.
- További információ az [alkalmazásadatok és -hozzárendelések figyeléséről](apps-monitor.md).
