---
title: Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban
titleSuffix: ''
description: Az Intune az alkalmazás-hozzárendelések belefoglalására vagy kizárására való használatának ismertetése.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e32b40283410a53a9cbb65a27d0d614da0169d6c
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001793"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban

Az Intune-ban úgy határozhatja meg, hogy ki férhet hozzá az alkalmazáshoz, ha felhasználói csoportokat rendel hozzá akár az engedélyezéshez, akár a kizáráshoz. Mielőtt csoportokat rendelne az alkalmazáshoz, meg kell adnia az alkalmazás hozzárendelési típusát. A hozzárendelés típusával az alkalmazás elérhetővé vagy kötelezővé tehető, illetve törölhető. 

Egy alkalmazás elérhetőségének megadásakor az alkalmazás-hozzárendeléseket felhasználók vagy eszközök csoportjaira vonatkozóan végezheti el csoport-hozzárendelések belefoglalásával vagy kizárásával. Ez a funkció akkor különösen hasznos, ha nagyobb csoportok számára szeretné elérhetővé tenni az alkalmazást, majd pedig szűkíteni szeretné a felhasználók körét, miközben egy kisebb csoportot is kizárhat. A kisebb csoport lehet például tesztcsoport, vagy egy vezetői csoport. 

Amikor csoportot zár ki egy alkalmazás-hozzárendelésből, akkor vagy csak felhasználói vagy csak eszközcsoportot kell kizárnia. Nem zárhat ki vegyes, felhasználói és eszközcsoportokat is. 

Az Intune nem veszi számításba a felhasználók és eszközök közötti társításokat a csoportok kizárásánál. Felhasználói csoportok belefoglalása és eszközcsoportok egyidejű kizárása minden bizonnyal nem éri el a kívánt eredményt. A belefoglalás elsőbbséget élvez a kizárással szemben. Ha például egy iOS-alkalmazást **Minden felhasználóra** céloz, és kizárja a **Minden iPad** csoportot, az eredmény az lesz, hogy minden iPadet használó felhasználó továbbra is hozzáfér az alkalmazáshoz. Ha azonban az iOS-alkalmazás célzása **Minden eszköz**, és kizárja a **Minden iPad** csoportot, akkor a beállítás sikeres lesz.  

> [!NOTE]
> Alkalmazások csoport-hozzárendelésénél a **Nem alkalmazható** típus nem használható többé, helyette a csoport kizárása lehetőség használható. 
>
> Az Intune előre létrehozott, **Minden felhasználó** és **Minden eszköz** csoportokat biztosít a konzolon. A csoportok beépített optimalizációkkal bírnak a felhasználók kényelme érdekében. Mindenképpen ajánlott ezeket a csoportokat használni az összes felhasználó és az összes eszköz megcélzására az Ön által létrehozott „Minden felhasználó” vagy „Minden eszköz” csoport helyett.  
>
> A vállalati Android támogatja a csoportok belefoglalását és kizárását. Kihasználhatja a beépített **Minden felhasználó** és **Minden eszköz** csoportot a Vállalati Android-alapú alkalmazástársításokhoz. 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>Csoportok belefoglalása és kizárása alkalmazások hozzárendelésénél 
Ha csoportokhoz szeretne alkalmazást hozzárendelni a belefoglalás és kizárás használatával, tegye a következőket:
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** panelen válassza az **Alkalmazások** lehetőséget. Megjelenik a hozzáadott alkalmazások listája.
5. Válassza ki a hozzárendelni kívánt alkalmazást. Megjelennek az alkalmazás adatai egy irányítópulton. 
6. A menü **Kezelés** szakaszában válassza a **Hozzárendelések** elemet. 

    ![Alkalmazás-hozzárendelések belefoglalása alkalmazások hozzárendelésekor](./media/apps-inc-exl-01.png)
7. Az alkalmazáshoz hozzárendelt felhasználói csoportok hozzáadásához válassza a **Csoport hozzáadása** lehetőséget. 
8. A **Csoport hozzáadása** panelen válasszon egy **Hozzárendelési típust** az elérhető típusok közül.
9. Hozzárendelési típusként válassza ki az **Elérhető regisztrációval és anélkül** lehetőséget.

    ![Alkalmazás-hozzárendelések az Intune-ban – Csoport hozzáadása](./media/apps-inc-exl-02.png)
10. A **Belefoglalt csoportok** lehetőséggel választhatja ki azokat a felhasználói csoportokat, amelyek számára elérhetővé szeretné tenni az alkalmazást.

    > [!NOTE]
    > Csoportok hozzáadásakor, ha bármely más csoport már bele lett foglalva egy adott hozzárendelés-típus esetében, az alkalmazás előre ki van jelölve, és nem módosítható más belefoglalási hozzárendelés-típusok esetében. Az használatba vett csoport nem használható belefoglalt csoportként.

11. Az **Igen** választásával teheti elérhetővé az alkalmazást minden felhasználó számára.

    ![Alkalmazás-hozzárendelések az Intune-ban – Csoportok belefoglalása](./media/apps-inc-exl-03.png)
12. Kattintson az **OK** gombra a csoport belefoglalásához.
13. A **Kizárt csoportok** lehetőséggel válassza ki azokat a felhasználói csoportokat, amelyek számára nem szeretné elérhetővé tenni az alkalmazást. 
14. Válassza ki a kizárni kívánt csoportokat. Így az alkalmazás nem érhető el ezekhez a csoportokhoz.

    ![Alkalmazás-hozzárendelések az Intune-ban – Csoportok kizárása](./media/apps-inc-exl-04.png)
15. A csoportkiválasztás befejezéséhez kattintson a **Kiválasztás** lehetőségre.
16. A **Csoport hozzáadása** panelen kattintson az **OK** gombra. Megjelenik az alkalmazáshoz tartozó **Hozzárendelések** listája.
17. A **Mentés** lehetőségre kattintva aktiválhatja az alkalmazásra vonatkozó csoport-hozzárendeléseket.

Csoport-hozzárendelések esetén a már hozzárendelt csoportok nem módosíthatók. Ha jelenleg nem elérhető csoportot szeretne kiválasztani, akkor először távolítsa el az alkalmazást az alkalmazás hozzárendelési listájából. 

A hozzárendelések szerkesztéséhez az alkalmazás **Hozzárendelések** listájában válassza ki azt a sort, amely a módosítandó hozzárendelést tartalmazza. Ezen kívül úgy is eltávolíthat hozzárendelést, ha a sor végén található három pontra ( **…** ) kattint, majd az **Eltávolítás** lehetőséget választja. A **Hozzárendelések** lista megjelenítésének módosításához **Hozzárendelési típus** vagy **Belefoglalt/Kizárt** állapot szerint csoportosíthat.

![Alkalmazás-hozzárendelések az Intune-ban – befejezés](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>További lépések

- További információt az alkalmazások csoport-hozzárendelésénél alkalmazható belefoglalásról és kizárásról a [Microsoft Intune blogján](https://aka.ms/new_app_assignment_process) találhat.
- További információ az [alkalmazásadatok és -hozzárendelések figyeléséről](apps-monitor.md).
