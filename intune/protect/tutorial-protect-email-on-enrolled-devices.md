---
title: Oktatóanyag – Exchange Online-levelezés biztosítása a felügyelt eszközökön
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan védheti meg az Exchange Online-t az iOS Intune megfelelőségi szabályzatokkal és az Azure AD feltételes hozzáféréssel a felügyelt eszközök és az Outlook alkalmazás megköveteléséhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c20c0c1543cd8fcbf7345a02295486aaaa6ddcea
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306863"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Oktatóanyag: Exchange Online-levelezés biztosítása a felügyelt eszközökön
Ismerje meg, hogyan használhatók az eszközök megfelelőségi szabályzatai feltételes hozzáféréssel annak biztosításához, hogy az iOS-eszközök csak akkor férhessenek hozzá az Exchange Online e-mailekhez, ha azokat az Intune felügyeli, és egy jóváhagyott e-mail alkalmazás használatával 

Az oktatóanyag segítségével megtanulhatja a következőket: 
> [!div class="checklist"]
> * Hozzon létre egy Intune iOS-eszköz megfelelőségi szabályzatát, hogy beállítsa, hogy az eszköznek milyen feltételeket kell megfelelnie a megfelelőnek.
> * Hozzon létre egy Azure Active Directory (Azure AD) feltételes hozzáférési szabályzatot, amely megköveteli az iOS-eszközök regisztrálását az Intune-ban, teljesíti az Intune-szabályzatokat, és a jóváhagyott Outlook Mobile App használatával fér hozzá az Exchange Online-hoz.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon az ingyenes próbaverziós fiókra](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
- Ehhez az oktatóanyaghoz a következő előfizetésekkel rendelkező tesztelési bérlőre lesz szüksége:
  - Prémium szintű Azure Active Directory ([ingyenes próbaverzió](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
  - Office 365 üzleti előfizetés, amely tartalmazza az Exchange-et ([ingyenes próbaverzió](https://go.microsoft.com/fwlink/p/?LinkID=510938))
- Mielőtt elkezdené, hozzon létre egy tesztelési eszköz profilt iOS-eszközökhöz a gyors útmutató [: e-mail-profil létrehozása iOS](../configuration/quickstart-email-profile.md)rendszerhez című témakör lépéseit követve.

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune](https://aka.ms/intuneportal) -ba globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként. Ha létrehozott egy Intune próbaverziós előfizetést, akkor az a fiók, amelyhez az előfizetést létrehozta, a globális rendszergazda.

## <a name="create-the-ios-device-compliance-policy"></a>Az iOS-eszköz megfelelőségi szabályzatának létrehozása
Állítson be egy Intune-eszköz megfelelőségi szabályzatát azon feltételek beállításához, amelyeknek az eszköznek meg kell felelnie az előírásoknak. Ebben az oktatóanyagban egy eszköz-megfelelőségi szabályzatot hozunk létre iOS-eszközökhöz. A megfelelőségi házirendek platform-specifikusak, ezért külön megfelelőségi szabályzatra van szükség minden kiértékelni kívánt eszköz platformhoz.

1. Az Intune-ban válassza az **eszközök megfelelősége** > **házirendek** > **házirend létrehozása**lehetőséget.
2. A **név**mezőben adja meg az iOS-es **megfelelőségi szabályzatok tesztelését**. 
3. A **Leírás**mezőben adja meg az iOS-es **megfelelőségi szabályzatok tesztelését**.
4. A **platform**területen válassza az **iOS**lehetőséget. 
5. Válassza a **beállítások** > **e-mail**lehetőséget. 
     
    1. A **felügyelt e-mail-profillal rendelkező mobileszközök megkövetelése**mellett válassza a **kötelező**lehetőséget.
    2. Kattintson az **OK** gombra.

    ![Az e-mailes megfelelőségi szabályzat beállítása a felügyelt e-mail-profil megköveteléséhez](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6. Válassza a **Eszközállapot**lehetőséget. A feltört **eszközök**mellett válassza a **Letiltás**lehetőséget, majd kattintson **az OK gombra**.
7. Válassza a **rendszerbiztonság** lehetőséget, és adja meg a **jelszó** beállításait. Ebben az oktatóanyagban válassza a következő ajánlott beállításokat:
     
    - A **mobileszközök zárolásának feloldásához jelszó megkövetelése**beállításnál válassza a **kötelező**lehetőséget.
    - **Egyszerű jelszavak**esetén válassza a **Letiltás**lehetőséget.
    - A **jelszó minimális hossza**mezőben adja meg a **4**értéket.
    - A **kötelező jelszó típusa mezőben**válassza az **alfanumerikus**lehetőséget.
    - A **jelszó kérése előtt a képernyő zárolásának maximális perce után**válassza a **azonnal**lehetőséget.
    - A **jelszó lejárata (nap)** mezőben adja meg a **41**értéket.
    - Az **újrafelhasználást megakadályozó korábbi jelszavak száma**mezőbe írja be az **5**értéket.
 
    ![Adja meg az e-mail megfelelőségi szabályzatának jelszavas beállításait](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Kattintson **az OK gombra**, majd kattintson ismét **az OK gombra** .
9. Kattintson a **Létrehozás** gombra.

## <a name="create-the-conditional-access-policy"></a>A feltételes hozzáférési szabályzat létrehozása
Most létrehozunk egy feltételes hozzáférési szabályzatot, amelyhez minden eszköz platformjának regisztrálnia kell az Intune-ban, és meg kell felelnie az Intune megfelelőségi szabályzatának az Exchange Online-hoz való hozzáféréshez. Az Outlook alkalmazáshoz is szükség van az e-mail hozzáféréshez. A feltételes hozzáférési szabályzatok az Azure AD-portálon vagy az Intune-portálon konfigurálhatók. Mivel már az Intune-portálon vagyunk, a szabályzatot itt fogjuk létrehozni.
1. Az Intune-ban válassza a **feltételes hozzáférés** > **házirendek**@no__t – 3**új házirend**elemet.
1. A **név**mezőben adja meg **az Office 365-e-mailek tesztelési szabályzatát**. 
3. A **hozzárendelések**alatt válassza a **felhasználók és csoportok**lehetőséget. A **beágyazás** lapon válassza a **minden felhasználó**lehetőséget, majd válassza a **kész**lehetőséget.

4. A **hozzárendelések**területen válassza a **Cloud apps**lehetőséget. Mivel az Office 365 Exchange Online e-mail-címét szeretnénk megóvni, a következő lépéseket követve választjuk ki:
     
    1. A **beágyazás** lapon válassza az **alkalmazások kiválasztása**lehetőséget.
    2. Válassza a **Kiválasztás** lehetőséget 
    3. Az alkalmazások listában válassza az **Office 365 Exchange Online**lehetőséget, majd válassza a **kiválasztás**lehetőséget. 
    4. Válassza a **Done** (Kész) lehetőséget.
  
    ![Válassza ki az Office 365 Exchange Online alkalmazást](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. A **hozzárendelések**területen válassza a **feltételek**@no__t – 2**eszköz platformot**.
     
    1. A **Konfigurálás**területen válassza az **Igen**lehetőséget.
    2. A **beágyazás** lapon válassza ki a kívánt **eszközt**, majd kattintson a **kész**gombra. 
    3. Válassza a **kész** lehetőséget.
   
    ![Bármilyen eszköz belefoglalása](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. A **hozzárendelések**területen válassza a **feltételek** > **ügyfélalkalmazások**lehetőséget.
     
    1. A **Konfigurálás**területen válassza az **Igen**lehetőséget.
    2. Ebben az oktatóanyagban válassza a **Mobile apps és az asztali ügyfelek** és a **modern hitelesítési ügyfelek** lehetőséget (amely az iOS-hez és az Androidhoz készült Outlookhoz hasonló alkalmazásokra vonatkozik). Törölje az összes többi jelölőnégyzet jelölését.
    3. Válassza a **kész**lehetőséget, majd kattintson a **kész** gombra.
    
    ![Alkalmazások és ügyfelek kiválasztása](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. A **hozzáférés-vezérlés**területen válassza a **támogatás**lehetőséget. 
     
    1. A **támogatás** panelen válassza a **hozzáférés engedélyezése**lehetőséget.
    2. Jelölje be az **eszköz megfelelőként való megjelölésének megkövetelése**jelölőnégyzetet. 
    3. Jelölje be a **jóváhagyott ügyfélalkalmazás megkövetelése**jelölőnégyzetet.
    4. **Több vezérlő esetében**válassza **az összes kijelölt vezérlő megkövetelése**lehetőséget. Ezzel a beállítással biztosítható, hogy mindkét kiválasztott követelmény érvénybe lépjen, amikor egy eszköz megpróbál hozzáférni az e-mailekhez.
    5. Válassza a **Kiválasztás** lehetőséget
     
    ![Conrols kiválasztása](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. A **Szabályzat engedélyezése** alatt válassza a **Be** lehetőséget.
     
    ![Házirend engedélyezése](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. Kattintson a **Létrehozás** gombra.

## <a name="try-it-out"></a>Próbálja ki!
A létrehozott szabályzatokkal minden olyan iOS-eszköz, amely az Office 365-ba próbál bejelentkezni, regisztrálnia kell az Intune-ban, és az iOS-hez készült Outlook Mobile alkalmazást kell használnia. A forgatókönyv iOS-eszközön való teszteléséhez próbáljon meg bejelentkezni az Exchange Online-ba a tesztelési bérlőben lévő felhasználó hitelesítő adatainak használatával. A rendszer felszólítja az eszköz regisztrálására és az Outlook Mobile alkalmazás telepítésére.
1. IPhone-on való teszteléshez lépjen a **beállítások** > **jelszavak & fiókok** > **fiók hozzáadása** > **Exchange**elemre.
2. Adja meg a tesztelési bérlő egyik felhasználójának e-mail-címét, majd kattintson a **tovább**gombra.
3. Kattintson **a bejelentkezés**gombra.
4. Adja meg a felhasználó jelszavát, majd kattintson a **Bejelentkezés**gombra.
5. Megjelenik egy üzenet, amely szerint az eszközt felügyelni kell az erőforráshoz való hozzáféréshez, valamint egy regisztrálási lehetőséggel. 

## <a name="clean-up-resources"></a>Az erőforrások eltávolítása
Ha a tesztelési házirendek már nem szükségesek, eltávolíthatja őket.
1. Jelentkezzen be az [Intune](https://aka.ms/intuneportal) -ba globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként.
2. Válassza az **eszköz megfelelősége** > **házirend**elemet.
3. A **szabályzat neve** listában válassza a tesztelési házirend helyi menüjét ( **...** ), majd válassza a **Törlés**lehetőséget. A megerősítéshez kattintson **az OK gombra** .
4. Válassza a **feltételes hozzáférés** > **házirendek**elemet.
5. A **szabályzat neve** listában válassza a tesztelési házirend helyi menüjét ( **...** ), majd válassza a **Törlés**lehetőséget. Válassza az **Igen** lehetőséget a megerősítéshez.

## <a name="next-steps"></a>Következő lépések 
Ebben az oktatóanyagban olyan házirendeket hozott létre, amelyekben az iOS-eszközök regisztrálása szükséges az Intune-ban, és az Outlook alkalmazással hozzáférhet az Exchange Online-hoz. Ha szeretné megtudni, hogyan használhatja az Intune-t feltételes hozzáféréssel más alkalmazások és szolgáltatások, például az Office 365 Exchange ActiveSync-ügyfelek számára az Exchange Online-hoz, tekintse [meg a feltételes hozzáférés beállítása](conditional-access.md)című témakört.
