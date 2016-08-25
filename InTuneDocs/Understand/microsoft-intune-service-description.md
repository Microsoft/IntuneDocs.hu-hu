---
title: "A szolgáltatás leírása | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4794a22b3bdd1f28e6951b81e8379dc208fffc89
ms.openlocfilehash: 6cab0bacd9157323e342662609de8c9f20550d78


---

# A Microsoft Intune szolgáltatás leírása

A Microsoft Intune egy felhőalapú szolgáltatás, amellyel Windows és Mac OS X rendszerű számítógépek, illetve iOS, Android és Windows rendszerű mobileszközök is felügyelhetők. Az Intune ezenkívül a vállalati alkalmazások és adatok védelmét is biztosítja. Használható önállóan, vagy a kezelési lehetőségek bővítése céljából a System Center 2012 R2 Configuration Managerrel integrálva.

A Microsoft az Intune bevezetési juttatást a jogosult csomagokban foglalt jogosult szolgáltatások esetében kínálja. Ez lehetővé teszi, hogy távoli segítséget kérjen a Microsoft szakértőitől az Intune-környezet üzembe helyezéséhez. További információ: [A Microsoft Intune szolgáltatási juttatás leírása](http://go.microsoft.com/fwlink/?LinkId=619281).

Az Intune használatát egy 30 napos ingyenes próbaverzióval kezdheti meg, amely 100 felhasználói licencet tartalmaz. Az ingyenes próbaverzió elindításához [kattintson ide, és látogasson el az Intune bejelentkezési oldalára](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Ha szervezete vállalati szerződéssel vagy egy egyenértékű mennyiségi licencszerződéssel rendelkezik, az ingyenes próbaverzió beállítását bízza Microsoft-képviselőjére.

> [!NOTE]
> Ha szervezete a Microsoft Online Services munkahelyi vagy iskolai fiókjával rendelkezik, vagy előfordulhat, hogy a próbaidőszak leteltével élesben folytatja ennek az Intune előfizetésnek a használatát, akkor az oldalon kattintson a **Bejelentkezés** lehetőségre, és a hitelesítéshez használja a szervezet globális rendszergazdai fiókját. Ez a művelet gondoskodik arról, hogy az Intune próbaverzió a meglévő munkahelyi vagy iskolai fiókhoz kapcsolódjon.

A mobileszközökön konfigurálható beállítások listáját itt találja:

-   [A Microsoft Intune mobileszköz-kezelési képességei](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

-   [Mobileszközök megfelelőségi beállításai a Configuration Managerben](https://technet.microsoft.com/en-us/library/dn376523.aspx)

A System Center 2012 R2 Configuration Managerrel kapcsolatos információkért lásd: [A System Center 2012 Configuration Manager dokumentumkönyvtára](https://technet.microsoft.com/library/gg682041.aspx).

## Az Intune szolgáltatásfrissítéseinek hatása a felhasználókra
Mivel az Intune online szolgáltatásként működik, a Microsoft rendszeresen frissítéseket ad ki hozzá.

Ebből a témakörből megtudhatja, hogy milyen gyakran jelennek meg ezek a szolgáltatásfrissítések, és megismerkedhet azzal az előzetes értesítéssel, amelyben tudatjuk a felhasználókkal, hogy egy adott frissítés hatással lehet a szolgáltatás működésére.

Az Intune szolgáltatás változásainak megismeréséhez lásd az [Újdonságok a Microsoft Intune-ban](/intune/deploy-use/Whats-new-in-microsoft-intune.md) című témakört. A [Microsoft Intune blog](http://blogs.technet.com/b/microsoftintune/) ugyancsak ismerteti a szolgáltatást érintő változásokat, ezenkívül hasznos tippekkel szolgál az Intune minél hatékonyabb használatához.

Az [Office 365 felügyeleti portál](https://portal.office.com/Admin/Default.aspx) üzenetközpontja ezenfelül a fontos szolgáltatásfrissítésekről is tájékoztatást nyújt. Az [Office 365 felügyeleti társalkalmazás](https://support.office.com/en-us/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) telepítésével mobileszközén is fogadhatja az értesítéseket.

> [!NOTE] Az [Office 365 felügyeleti portálon](https://portal.office.com/Admin/Default.aspx) az Intune szolgáltatás állapota is figyelemmel követhető. Válassza a bal oldali panel **Szolgáltatás állapota** elemét.  

A Microsoft Intune szolgáltatással kapcsolatos figyelmeztetéseinek típusai a következők:
-   Hogy fel tudjon készülni a szolgáltatás változásaira, a szolgáltatásfrissítést megelőzően legalább 30–90 nappal értesítjük, annak függvényében, hogy milyen hatású a változtatás. Erre a terméken belüli kommunikációs csatornákon (például a hirdetőtáblán közzétett értesítéseken) keresztül kerül majd sor. Ezek a változások a következők lehetnek:
* Megfelelőségi vagy jogszabályi megfeleléssel összefüggő frissítések
* A végfelhasználói élmény, a felhasználói felület és a munkafolyamatok változásai
* Új vagy módosult API-k (értesítés arról, hogy tesztelni kell az egyéni alkalmazások visszamenőleges kompatibilitását)
* A rendszerkövetelmények változásai, például a minimálisan szükséges böngészőverzió
* Minden olyan frissítés, amely felhasználói beavatkozást igényel a funkció engedélyezéséhez vagy a funkció működésének zavartalanságához
-   A Microsoft a havonta esedékes szolgáltatásfrissítés részeként az új szolgáltatásokkal, új funkciókkal és a meglévő funkciók fejlesztéseivel kapcsolatos információkat is biztosít. A Microsoft rendszerint minden hónap 15-e körül adja ki a szolgáltatásfrissítéseket. A frissítések leírását az [Újdonságok a Microsoft Intune-ban](/intune/deploy-use/whats-new-in-microsoft-intune) című témakörben találja.
-   Az Intune szolgáltatás kivonása esetén 12 hónappal korábban értesítjük.

## Válassza ki az Ön számára megfelelő felügyeleti megoldást
Az Intune többféleképpen is konfigurálható annak érdekében, hogy biztosítható legyen (az ebben a dokumentumban **eszközöknek** nevezett) munkahelyi mobileszközök és számítógépek kezelése és védelme.

-   **Az Intune önálló konfigurációja.** A szervezetben lévő mobileszközök felügyelete az Intune webalapú felügyeleti konzoljával végezhető. Az Intune bármilyen helyszíni informatikai infrastruktúra nélkül használható, azonban ha az Intune-t Active Directory tartományi szolgáltatásokkal együtt használja, a tartományi szolgáltatásokkal kezelt tartományi felhasználói fiókokat az Intune-nal is használhatja.

-   **Intune és System Center Configuration Manager.** A Configuration Manager-kezelőkonzollal felügyelheti a vállalat számítógépeit és mobileszközeit. A konfiguráció segítségével a szervezet összes eszközét egyetlen konzolon, a Configuration Manager felügyeleti konzolon felügyelheti. A Configuration Manager nagy mennyiségű mobileszköz, kiszolgáló és számítógép felügyeletét támogatja. További információkért lásd: [Mobileszközök felügyelete a Configuration Manager és a Microsoft Intune használatával](http://go.microsoft.com/fwlink/?LinkID=271118) a [System Center 2012 Configuration Manager dokumentumkönyvtárában](https://technet.microsoft.com/library/gg682041.aspx).  Az Ön számára leginkább megfelelő módszer kiválasztásához további segítséget talál a [Választás a Microsoft Intune önálló és hibrid mobileszköz-kezelése között a Configuration Manager segítségével](https://technet.microsoft.com/en-us/library/mt706478.aspx).


## További tudnivalók az Intune-ról
Az alábbi forrásokból többet is megtudhat az Intune-ról:

-   A [Microsoft Intune Adatvédelmi központja](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) információkkal szolgál az Intune biztonsági, adatvédelmi és megfelelőségi vonatkozásairól, ezenkívül az Intune minősítései közül is bemutat néhányat.

-   [A Microsoft Intune mobileszköz-kezelési képességei](/intune/understand-explore/mobile-device-management-capabilities-in-microsoft-intune)

### További információ
[Microsoft Intune](https://docs.microsoft.com/intune/)
[A System Center 2012 Configuration Manager dokumentumkönyvtára](https://technet.microsoft.com/library/gg682041.aspx)

[Újdonságok a Microsoft Intune-ban](/intune/deploy-use/whats-new-in-microsoft-intune)



<!--HONumber=Jun16_HO5-->


