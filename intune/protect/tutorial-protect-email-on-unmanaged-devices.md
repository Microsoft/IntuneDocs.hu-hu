---
title: Oktatóanyag – Exchange Online e-mail küldése nem felügyelt eszközökön
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan védheti meg az Office 365 Exchange Online-t az Intune app Protection-szabályzatokkal és az Azure AD feltételes hozzáférésével.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/10/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e0a01034bc35ddf8fd8eb1ede5fcf4c942dc735
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306805"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Oktatóanyag: az Exchange Online e-mailek felügyelete nem felügyelt eszközökön

Ismerje meg, hogyan használhatja az alkalmazás-védelmi szabályzatokat feltételes hozzáféréssel az Exchange Online védelméhez, még akkor is, ha az eszközök nincsenek regisztrálva az Intune-ban. Az oktatóanyag segítségével megtanulhatja a következőket: 

> [!div class="checklist"]
> * Hozzon létre egy Intune app Protection-szabályzatot az Outlook alkalmazáshoz. A "Mentés másként" lehetőséggel és a kivágási, másolási és beillesztési műveletek korlátozásával korlátozhatja, hogy a felhasználó mit tehet az alkalmazásban. 
> * Hozzon létre Azure Active Directory (Azure AD) feltételes hozzáférési szabályzatokat, amelyekkel csak az Outlook alkalmazás férhet hozzá a vállalati e-mailekhez az Exchange Online-ban. A többtényezős hitelesítés (MFA) is szükséges a modern hitelesítési ügyfelekhez, például az iOS-hez és az Androidhoz készült Outlookhoz.

## <a name="prerequisites"></a>Előfeltételek
- Ehhez az oktatóanyaghoz a következő előfizetésekkel rendelkező tesztelési bérlőre lesz szüksége:
  - Prémium szintű Azure Active Directory ([ingyenes próbaverzió](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
  - Intune-előfizetés ([ingyenes próbaverzió](../fundamentals/free-trial-sign-up.md))
  - Office 365 üzleti előfizetés, amely tartalmazza az Exchange-et ([ingyenes próbaverzió](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként. Az Intune a Azure Portalban található az **összes szolgáltatás** > **Intune**kiválasztásával.

## <a name="create-the-app-protection-policy"></a>Az alkalmazás-védelmi szabályzat létrehozása
Ebben az oktatóanyagban egy Intune app Protection-szabályzatot hozunk létre az Outlook alkalmazáshoz, amely az alkalmazás szintjén helyezi el a védelmet. Az alkalmazás munkahelyi környezetben való megnyitásához PIN-kód szükséges. Emellett korlátozza az alkalmazások közötti adatmegosztást, és megakadályozhatja, hogy a vállalati adatok személyes helyre legyenek mentve.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és lépjen az **ügyfélalkalmazások** > **App Protection-szabályzatok** > **házirend létrehozása**elemre.  
2. Konfigurálja a következő beállítást:  
   - **Név**: adja meg az **Outlook app Policy tesztet**.  
   - **Leírás**: adja meg az **Outlook-alkalmazás szabályzatának tesztelését**.  
   - **Platform**: válassza az **iOS**lehetőséget.  
   - Az **összes alkalmazás típusának megcélzása**: válassza a nem lehetőséget, majd az **alkalmazás típusa**mezőben jelölje be a **nem** **felügyelt eszközökön lévő alkalmazások**jelölőnégyzetét.  
3. Válassza az **alkalmazások**lehetőséget. Az alkalmazások listában válassza az **Outlook**lehetőséget, majd válassza a **kiválasztás**lehetőséget.
4. A beállítások panel megnyitásához válassza a **Beállítások** lehetőséget. 
5. A beállítások ablaktáblán válassza az **Adatvédelem**lehetőséget. A *adatátvitel*alatt az adatvédelem ablaktáblán adja meg a következő beállításokat az oktatóanyaghoz:

   - Ha **más alkalmazásokba szeretné elküldeni a szervezeti adatküldést**, válassza a **nincs**lehetőséget.  
   - **Más alkalmazásoktól érkező adatok fogadásához**válassza a **nincs**lehetőséget.  
   - A **szervezeti adatmásolatok mentéséhez**válassza a **Letiltás**lehetőséget.  
   - A **kivágási, másolási és beillesztési műveletek korlátozása más alkalmazások között**válassza a **Letiltva**lehetőséget. 
   - Hagyja meg az összes többi beállítást az alapértelmezett értékeken. 
   
   ![Válassza ki az Outlook-alkalmazás védelmi házirendjének adatáthelyezési beállításait.](./media/tutorial-protect-email-on-unmanaged-devices/data-protection-settings.png)

   A beállítások panelre való visszatéréshez kattintson **az OK gombra** .  

6. Válassza a **hozzáférési követelmények** lehetőséget, majd adja meg a következő beállításokat:  

   - A **PIN-kód eléréséhez**válassza a **kötelező**lehetőséget.
   - A **hozzáféréshez használt munkahelyi vagy iskolai fiók hitelesítő adatai**területen válassza a **kötelező**lehetőséget.
   - Hagyja meg az összes többi beállítást az alapértelmezett értékeken.
 
    ![Válassza ki az Outlook-alkalmazás védelmi házirendjének hozzáférési műveleteit.](./media/tutorial-protect-email-on-unmanaged-devices/access-requirements-settings.png)

    A beállítások panelre való visszatéréshez kattintson **az OK gombra** .  

7. A beállítások ablaktáblán kattintson az **OK gombra**, majd a házirend létrehozása panelen válassza a **Létrehozás**lehetőséget.

Létrejön az Outlook alkalmazás-védelmi szabályzata. Ezután beállíthatja a feltételes hozzáférést, hogy az eszközök az Outlook alkalmazást használják.

## <a name="create-conditional-access-policies"></a>Feltételes hozzáférési szabályzatok létrehozása
Most hozzunk létre két feltételes hozzáférési szabályzatot az összes eszköz platformjának lefedéséhez.  

- Az első szabályzat megköveteli, hogy a modern hitelesítési ügyfelek a jóváhagyott Outlook alkalmazást és multi-Factor Authentication (MFA) hitelesítést használják. A modern hitelesítési ügyfelek közé tartoznak az iOS és az Android rendszerhez készült Outlook.  

- A második szabályzat megköveteli, hogy az Exchange ActiveSync-ügyfelek a jóváhagyott Outlook alkalmazást használják. (A Exchange Active Sync jelenleg nem támogatja az eszköz platformján kívüli feltételeket). A feltételes hozzáférési szabályzatokat az Azure AD-portálon vagy az Intune-portálon is konfigurálhatja. Mivel már az Intune-portálon vagyunk, a szabályzatot itt fogjuk létrehozni.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>MFA-szabályzat létrehozása modern hitelesítési ügyfelek számára  

1. Az Intune-ban válassza a **feltételes hozzáférés** > **házirendek**@no__t – 3**új házirend**elemet.  

2. A **név**mezőben adja meg **a modern hitelesítési ügyfelekhez tartozó tesztelési házirendet**.  

3. A **hozzárendelések**alatt válassza a **felhasználók és csoportok**lehetőséget. A **beágyazás** lapon válassza a **minden felhasználó**lehetőséget, majd válassza a **kész**lehetőséget.

4. A **hozzárendelések**területen válassza a **felhőalapú alkalmazások vagy műveletek**elemet. Mivel az Office 365 Exchange Online e-mail-címét szeretnénk megóvni, a következő lépéseket követve választjuk ki:  
     
   1. A **beágyazás** lapon válassza az **alkalmazások kiválasztása**lehetőséget.  
   2. Válassza a **Kiválasztás** lehetőséget  
   3. Az alkalmazások listában válassza az **Office 365 Exchange Online**lehetőséget, majd válassza a **kiválasztás**lehetőséget.  
   4. Kattintson a **kész** gombra az új házirend panelre való visszatéréshez.  
  
   ![Válassza ki az Office 365 Exchange Online alkalmazást](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5. A **hozzárendelések**területen válassza a **feltételek**@no__t – 2**eszköz platformot**.  
   1. A **Konfigurálás**területen válassza az **Igen**lehetőséget.  
   2. A **beágyazás** lapon válassza a **bármely eszköz**elemet.  
   3. Válassza a **Done** (Kész) lehetőséget.  
   
6. A **feltételek** ablaktáblán válassza az **ügyfélalkalmazások**elemet.  
   1. A **Konfigurálás**területen válassza az **Igen**lehetőséget.  
   2. Válassza a **Mobile apps és az asztali ügyfelek** és a **modern hitelesítési ügyfelek**lehetőséget.  
   3. Törölje a jelet a többi jelölőnégyzetből.  
   4. Az új házirend panelre való visszatéréshez válassza a **kész**@no__t – 1**kész** elemet.  

   ![Mobil alkalmazások és ügyfelek kiválasztása](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7. A **hozzáférés-vezérlés**területen válassza a **támogatás**lehetőséget. 
     
   1. A **támogatás** panelen válassza a **hozzáférés engedélyezése**lehetőséget.
   2. Válassza a **többtényezős hitelesítés megkövetelése**lehetőséget.
   3. Jelölje be a **jóváhagyott ügyfélalkalmazás megkövetelése**jelölőnégyzetet.
   4. **Több vezérlő esetében**válassza **az összes kijelölt vezérlő megkövetelése**lehetőséget. Ezzel a beállítással biztosítható, hogy mindkét kiválasztott követelmény érvénybe lépjen, amikor egy eszköz megpróbál hozzáférni az e-mailekhez.
   5. Válassza a **Kiválasztás** lehetőséget
     
   ![Vezérlők kijelölése](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

7. A **házirend engedélyezése**területen válassza **a**be lehetőséget, majd válassza a **Létrehozás**lehetőséget.  
     
    ![Szabályzat létrehozása](./media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

Létrejön a modern hitelesítési ügyfelek feltételes hozzáférési szabályzata. Most létrehozhat egy házirendet Exchange Active Sync-ügyfelek számára.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Szabályzat létrehozása Exchange Active Sync ügyfelek számára  
1. Az Intune-ban válassza a **feltételes hozzáférés** > **házirendek**@no__t – 3**új házirend**elemet.  
2. A **név**mezőben adja meg **az EAS-ügyfelekhez tartozó tesztelési**szabályzatot.  
3. A **hozzárendelések**alatt válassza a **felhasználók és csoportok**lehetőséget.  
4. A *beágyazás* lapon válassza a **minden felhasználó**lehetőséget, majd válassza a **kész**lehetőséget.  

5. A **hozzárendelések**területen válassza a **felhőalapú alkalmazások vagy műveletek**elemet. Válassza az Office 365 Exchange Online e-mailek elemet a következő lépésekkel:  
   1. A *beágyazás* lapon válassza az **alkalmazások kiválasztása**lehetőséget.  
   2. Válassza a **Kiválasztás** lehetőséget  
   3. Az *alkalmazások*listájából válassza ki az **Office 365 Exchange Online**elemet, majd válassza a **kiválasztás**, majd a **kész**lehetőséget.  
  
6. A **hozzárendelések**területen válassza a **feltételek**@no__t – 2**eszköz platformot**.  
   1. A **Konfigurálás**területen válassza az **Igen**lehetőséget.  
   2. A **beágyazás** lapon válassza ki a kívánt **eszközt**, majd kattintson a **kész**gombra.  

7. A **feltételek** ablaktáblán válassza az **ügyfélalkalmazások**elemet.  
   1. A **Konfigurálás**területen válassza az **Igen**lehetőséget.  
   2. Válassza **a Mobile apps és az asztali ügyfelek**lehetőséget.  
   3. Válassza az **Exchange ActiveSync-ügyfelek** lehetőséget, és **alkalmazza a házirendet csak a támogatott platformokra**.  
   4. Törölje az összes többi jelölőnégyzet jelölését.  
   5. Válassza a **kész**lehetőséget, majd kattintson a **kész** gombra.  
    
   ![Alkalmazás a támogatott platformokra](./media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

7. A **hozzáférés-vezérlés**területen válassza a **támogatás**lehetőséget.  
   1. A **támogatás** panelen válassza a **hozzáférés engedélyezése**lehetőséget.  
   2. Jelölje be a **jóváhagyott ügyfélalkalmazás megkövetelése**jelölőnégyzetet. Törölje az összes többi jelölőnégyzet jelölését.  
   3. Válassza a **Kiválasztás** lehetőséget  
     
   ![Jóváhagyott ügyfélalkalmazás megkövetelése](./media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)  

8. A **Szabályzat engedélyezése** alatt válassza a **Be** lehetőséget.  

9. Kattintson a **Létrehozás** gombra.  

Az alkalmazás-védelmi szabályzatok és a feltételes hozzáférés már érvényben van, és készen áll a tesztelésre.  

## <a name="try-it-out"></a>Próbálja ki!  
A létrehozott házirendekkel az eszközöknek regisztrálniuk kell az Intune-ban, és az Outlook Mobile alkalmazást kell használniuk az Office 365 e-mail eléréséhez. A forgatókönyv iOS-eszközön való teszteléséhez próbáljon meg bejelentkezni az Exchange Online-ba a tesztelési bérlőben lévő felhasználó hitelesítő adatainak használatával.  
1. IPhone-on való teszteléshez lépjen a **beállítások** > **jelszavak & fiókok** > **fiók hozzáadása** > **Exchange**elemre.  
2. Adja meg a tesztelési bérlő egyik felhasználójának e-mail-címét, majd kattintson a **tovább**gombra.  
3. Kattintson **a bejelentkezés**gombra.  
4. Adja meg a felhasználó jelszavát, majd kattintson a **Bejelentkezés**gombra.  
5. Az üzenetnek **további információra van szüksége** , ami azt jelenti, hogy a rendszer felszólítja az MFA beállítására. Folytassa a további ellenőrzési módszer megadásával.  
6. Ezután megjelenik egy üzenet, amely szerint az erőforrást az informatikai részleg által nem jóváhagyott alkalmazással próbálja megnyitni. Az üzenet azt jelenti, hogy a natív posta alkalmazás használatával blokkolva van. A bejelentkezés megszakítása.  
7. Nyissa meg az Outlook alkalmazást, és válassza a **beállítások** > **fiók hozzáadása** > **e-mail fiók hozzáadása**lehetőséget.  
8. Adja meg a tesztelési bérlő egyik felhasználójának e-mail-címét, majd kattintson a **tovább**gombra.  
9. Nyomja meg **az Office 365-vel való bejelentkezést**. A rendszer további hitelesítést és regisztrációt kér. Miután bejelentkezett, tesztelheti az olyan műveleteket, mint például a Kivágás, a másolás, a Beillesztés és a Mentés másként lehetőség.  

## <a name="clean-up-resources"></a>Az erőforrások eltávolítása  
Ha a tesztelési házirendek már nem szükségesek, eltávolíthatja őket.  
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként.  
2. Válassza az **eszköz megfelelősége** > **házirend**elemet.  
3. A **szabályzat neve** listában válassza a tesztelési házirend helyi menüjét ( **...** ), majd válassza a **Törlés**lehetőséget. A megerősítéshez kattintson **az OK gombra** .  
4. Válassza a **feltételes hozzáférés** > **házirendek**elemet.  
5. A **szabályzat neve** listában válassza a helyi menüt ( **..** .) minden egyes tesztelési házirendhez, majd válassza a **Törlés**lehetőséget. Válassza az **Igen** lehetőséget a megerősítéshez.  

## <a name="next-steps"></a>Következő lépések  
Ebben az oktatóanyagban létrehozott egy alkalmazás-védelmi szabályzatot, amely korlátozza, hogy a felhasználó mit tehet az Outlook alkalmazással, és feltételes hozzáférési szabályzatokat hozott létre az Outlook alkalmazás megköveteléséhez, valamint az MFA használatát a modern hitelesítési ügyfelek számára. További információ az Intune és a feltételes hozzáférés használatáról más alkalmazások és szolgáltatások elleni védelemhez: [feltételes hozzáférés beállítása](conditional-access.md).
