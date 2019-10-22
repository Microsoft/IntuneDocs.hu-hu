---
title: Eszköz alapú feltételes hozzáférés beállítása az Intune-nal
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan hozhat létre egy eszköz-alapú feltételes hozzáférési szabályzatot az eszközök megfelelőségének és a mobileszközök felügyeletének Microsoft Intune alapján.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b775bb09c289733cdc2837984874b7c1c7e286bc
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681368"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Eszköz alapú feltételes hozzáférési szabályzat létrehozása

Az Intune-nal a Azure Active Directory feltételes hozzáférését a mobileszközök megfelelőségének a hozzáférés-vezérléshez való hozzáadásával növelheti. Miután létrehozott egy Intune-os megfelelőségi szabályzatot, amely meghatározza a megfelelő eszközökre vonatkozó követelményeket, az eszköz megfelelőségi állapota alapján engedélyezheti vagy letilthatja az alkalmazásokhoz és szolgáltatásokhoz való hozzáférést. Ezt úgy teheti meg, hogy létrehoz egy feltételes hozzáférési szabályzatot, amely az **eszköz megfelelőként való megjelölésének megkövetelése**beállítást használja.  

A feltételes hozzáférési szabályzat meghatározza a védelemmel ellátni kívánt alkalmazást vagy szolgáltatásokat, az alkalmazások vagy szolgáltatások elérésének feltételeit, valamint azokat a felhasználókat, akikre a szabályzat vonatkozik. A feltételes hozzáférés egy prémium szintű Azure AD-szolgáltatás, amely Azure Active Directoryban konfigurálható, de ugyanezeket a szabályzatokat az Intune-portálon is megadhatja. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.  

> [!IMPORTANT]
> A feltételes hozzáférés beállítása előtt be kell állítania az Intune-eszközök megfelelőségi szabályzatait az eszközök kiértékeléséhez, attól függően, hogy megfelelnek-e az adott követelményeknek. Lásd: [az eszközök megfelelőségi szabályzatának első lépései az Intune-ban](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Feltételes hozzáférési szabályzat létrehozása

1. Az Intune-portálon válassza a **feltételes hozzáférés**  > **házirendek**  > **új házirend**elemet.
   
    ![Új feltételes hozzáférési szabályzat létrehozása](./media/create-conditional-access-intune/create-ca.png)
 
2. A **Hozzárendelések** alatt válassza a **Felhasználók és csoportok** lehetőséget. 
3. A **beágyazás** lapon azonosítsa azokat a felhasználókat vagy csoportokat, akikre alkalmazni kívánja ezt a feltételes hozzáférési szabályzatot. Miután kiválasztotta a belefoglalást, használhatja a **kizárás** lapot, ha vannak olyan felhasználók, szerepkörök vagy csoportok, amelyeket ki szeretne zárni ebből a szabályzatból.  
    - **Minden felhasználó**: válassza ezt a lehetőséget, ha az összes felhasználóra és csoportra alkalmazni szeretné a szabályzatot, beleértve a belső és a vendég felhasználókat is.
  
    - **Felhasználók és csoportok kiválasztása**: válassza ezt a lehetőséget, és adjon meg egyet vagy többet az alábbi lehetőségek közül:
  
      a. **Minden vendég felhasználó**: válassza ezt a lehetőséget a külső vendég felhasználók (például partnerek, külső közreműködők) belefoglalásához vagy kizárásához.
       
      b. **Címtárbeli szerepkörök**: válasszon ki egy vagy több Azure ad-szerepkört a szerepkörökhöz hozzárendelt felhasználók belefoglalásához vagy kizárásához.
      
      c. **Felhasználók és csoportok**: ezzel a beállítással megkeresheti és kiválaszthatja azokat az egyes felhasználókat vagy csoportokat, amelyeket szeretne felvenni vagy kizárni.
     
       > [!TIP]  
       > Tesztelje a házirendet egy kisebb felhasználói csoporttal, hogy biztosan a várt módon működjön.
4. Válassza a **Kész** lehetőséget.
5. A **Hozzárendelések** alatt válassza a **Felhőalkalmazások** lehetőséget. 
6. A **beágyazás lapon**azonosítsa a feltételes hozzáférési szabályzattal védelemmel ellátni kívánt alkalmazásokat és szolgáltatásokat. Ezt követően használhatja a **kizárás** lapot, ha vannak olyan alkalmazások vagy szolgáltatások, amelyeket ki szeretne zárni ebből a szabályzatból.
    - **Minden felhőalapú alkalmazás**: válassza ezt a lehetőséget, ha az összes alkalmazásra alkalmazni szeretné a szabályzatot.
      > [!IMPORTANT]  
      > A lista a Azure Portal eléréséhez Microsoft Azure felügyeleti alkalmazást tartalmazza. Ügyeljen arra, hogy a **kizárás** lapot itt vagy a **felhasználók és csoportok** beállításainál ellenőrizze, hogy a (vagy a kijelölt felhasználók vagy csoportok) be tudja-e jelentkezni a Azure Portalba. 

    - **Alkalmazások kiválasztása**: válassza ezt a lehetőséget, válassza a **kiválasztás**elemet, majd az alkalmazások listában keresse meg és válassza ki a védelemmel ellátni kívánt alkalmazásokat vagy szolgáltatásokat.
    
      ![Hozzárendelések konfigurálása feltételes hozzáférési házirendhez](./media/create-conditional-access-intune/create-ca-select-apps.png)

7. Válassza a **Kész** lehetőséget.
8. A **hozzárendelések**területen válassza a **feltételek**lehetőséget.
    - **Bejelentkezési kockázat**: válassza az Igen lehetőséget, ha Azure ad Identity Protection bejelentkezési kockázati észlelést kíván használni a szabályzattal, majd válassza ki a bejelentkezési kockázati szinteket, amelyekre a házirend vonatkozik.
    - **Eszköz platformok**: a **beágyazás** lapon azonosítsa azokat az eszközöket, amelyekre alkalmazni kívánja a feltételes hozzáférési szabályzatot. A **kizárás** lapon kizárhatja a szabályzatok platformját.
    - **Helyek**: a **Belefoglalás** lapon adja meg, hogy a házirend minden helyre, az informatikai részleg felügyelete alá eső megbízható hálózati helyekre vagy adott hálózati helyekre vonatkozik-e. A **kizárás** lapon kizárhatja a házirendből a hálózati telephelyeket. 
    - **Ügyfélalkalmazások**: válassza az **Igen** lehetőséget annak megadásához, hogy a szabályzat a böngésző alkalmazásaira, a Mobile apps szolgáltatásra és az asztali ügyfelekre vonatkozzon-e. Kiválaszthatja a **modern hitelesítési ügyfeleket** is (például az Outlook for iOS vagy az Outlook for Android alkalmazást) és az **Exchange ActiveSync-ügyfeleket**.
    - **Eszköz állapota**: a feltételes hozzáférési szabályzat minden eszköz állapotra érvényes, kivéve, ha az Igen lehetőséget választja, és kifejezetten kizárja az állapotok eszköz hibrid Azure ad-hez csatlakoztatott vagy megfelelőként megjelölt eszközét (vagy mindkettőt).
    
      ![Feltételes hozzáférési szabályzat feltételeinek beállítása](./media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Ha a **modern hitelesítési** ügyfeleket és az **Exchange ActiveSync-ügyfeleket**egyaránt meg szeretné tenni, hozzon létre két külön feltételes hozzáférési szabályzatot, egyet az egyes ügyfelek típusaihoz. Habár az Exchange ActiveSync támogatja a modern hitelesítést, az Exchange ActiveSync által támogatott egyetlen feltétel a platform. Más feltételek, beleértve a többtényezős hitelesítést, nem támogatottak. Az Exchange Online-hoz az Exchange ActiveSync-hez való hozzáférés hatékony biztosításához hozzon létre egy feltételes hozzáférési szabályzatot, amely meghatározza a Cloud app Office 365 Exchange Online-t és az ügyfélalkalmazás Exchange ActiveSync alkalmazást, és alkalmazza a házirendeket csak a kiválasztott támogatott platformokra.

9. Válassza a **Kész** lehetőséget.
10. A **Hozzáférés-vezérlés** alatt válassza ki az **Engedélyezés** elemet. Konfigurálja, hogy mi történjen a beállított feltételek alapján.  A következő lehetőségek közül választhat:
    - **Hozzáférés letiltása**: az ebben a házirendben megadott felhasználók megtagadják a hozzáférést az alkalmazásokhoz a megadott feltételek szerint.
    - **Hozzáférés biztosítása**: a szabályzatban megadott felhasználók hozzáférést kapnak, de a következő műveletek bármelyikét megkövetelheti:
      - **Többtényezős hitelesítés megkövetelése**: a felhasználónak további biztonsági követelményeket kell végrehajtania, például telefonhívást vagy szöveget.
      - **Eszköz megfelelőként való megjelölésének megkövetelése**: az eszköznek Intune-kompatibilisnek kell lennie. Ha az eszköz nem megfelelő, a felhasználónak lehetősége lesz regisztrálni az eszközt az Intune-ban. 
      - **Hibrid Azure ad-hez csatlakoztatott eszköz megkövetelése**: az eszközöknek hibrid Azure ad-hez kell csatlakozniuk.
      - **Jóváhagyott ügyfélalkalmazás megkövetelése**: az eszköznek jóváhagyott ügyfélalkalmazások használatát kell használnia. 
      - **Több vezérlő esetén**: válassza az **összes kijelölt vezérlő megkövetelése** lehetőséget, hogy az eszköz hozzáférjen az alkalmazáshoz.
    
      ![Hozzáférés-vezérlési beállítások megadása](./media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. A **Szabályzat engedélyezése** alatt válassza a **Bekapcsolás** elemet.
     
     ![Házirend engedélyezése](./media/create-conditional-access-intune/enable-policy.png)

12. Válassza a **Létrehozás** lehetőséget.

## <a name="see-also"></a>További információ
[Alkalmazás-alapú feltételes hozzáférés az Intune-nal](app-based-conditional-access-intune.md)

[Az Intune feltételes hozzáférésének hibaelhárítása](https://support.microsoft.com/help/4456106)
