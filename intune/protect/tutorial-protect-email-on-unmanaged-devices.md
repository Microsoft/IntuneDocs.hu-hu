---
title: Oktatóanyag – Exchange Online e-mail küldése nem felügyelt eszközökön
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan védheti meg az Office 365 Exchange Online-t az Intune app Protection-szabályzatokkal és az Azure AD feltételes hozzáférésével.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 810a898a3b2d1981babc231f32ed386bde37a856
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465785"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Oktatóanyag: az Exchange Online e-mailek felügyelete nem felügyelt eszközökön

Ismerje meg, hogyan használhatja az alkalmazás-védelmi szabályzatokat feltételes hozzáféréssel az Exchange Online védelméhez, még akkor is, ha az eszközök nincsenek regisztrálva az Intune-ban. Az oktatóanyag segítségével megtanulhatja a következőket:

> [!div class="checklist"]
> * Hozzon létre egy Intune app Protection-szabályzatot az Outlook alkalmazáshoz. A "Mentés másként" lehetőséggel és a kivágási, másolási és beillesztési műveletek korlátozásával korlátozhatja, hogy a felhasználó mit tehet az alkalmazásban.
> * Hozzon létre Azure Active Directory (Azure AD) feltételes hozzáférési szabályzatokat, amelyekkel csak az Outlook alkalmazás férhet hozzá a vállalati e-mailekhez az Exchange Online-ban. A többtényezős hitelesítés (MFA) is szükséges a modern hitelesítési ügyfelekhez, például az iOS-hez és az Androidhoz készült Outlookhoz.

## <a name="prerequisites"></a>Előfeltételek

Az oktatóanyag végrehajtásához szüksége lesz egy tesztelési bérlőre a következő előfizetésekkel:

- Prémium szintű Azure Active Directory ([ingyenes próbaverzió](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune-előfizetés ([ingyenes próbaverzió](../fundamentals/free-trial-sign-up.md))
- Office 365 Vállalati előfizetés, ami magában foglalja az Exchange-et ([ingyenes próbaverzió](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Ebben az oktatóanyagban a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431)való bejelentkezéskor jelentkezzen be [globális rendszergazdaként](../fundamentals/users-add.md#types-of-administrators) vagy Intune szolgáltatás- [rendszergazdaként](../fundamentals/users-add.md#types-of-administrators). Ha létrehozott egy Intune próbaverziós előfizetést, akkor az előfizetést létrehozó fiók a globális rendszergazda.

## <a name="create-the-app-protection-policy"></a>Az alkalmazás-védelmi szabályzat létrehozása

Ebben az oktatóanyagban az iOS-hez készült Intune app Protection-szabályzatot fogjuk beállítani az Outlook alkalmazáshoz, amely az alkalmazás szintjén helyezi el a védelmet. Az alkalmazás munkahelyi környezetben való megnyitásához PIN-kód szükséges. Emellett korlátozza az alkalmazások közötti adatmegosztást, és megakadályozhatja, hogy a vállalati adatok személyes helyre legyenek mentve.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **alkalmazások** > az **alkalmazás-védelmi házirendek** lehetőséget, > **hozzon létre házirendet**, és válassza az **iOS/iPadOS** lehetőséget a platform számára.

3. Az **alapvető** beállítások lapon adja meg a következő beállításokat:

   - **Név**: adja meg az **Outlook app Policy tesztet**.
   - **Leírás**: adja meg az **Outlook-alkalmazás szabályzatának tesztelését**.

   A **platform** értéke az előző választott értékre van állítva.

   A folytatáshoz kattintson a **Tovább** gombra.

4. Az **alkalmazások** oldalon kiválaszthatja, hogyan szeretné alkalmazni a szabályzatot különböző eszközökön futó alkalmazásokra. Adja meg az alábbi lehetőségeket:

   - A **cél az összes alkalmazás típusához**: válassza a nem lehetőséget, majd az alkalmazások **típusainál**jelölje be a **nem** **felügyelt eszközökön lévő alkalmazások**jelölőnégyzetét.
   - Kattintson a **nyilvános alkalmazások kiválasztása**elemre. Az alkalmazások listában válassza az **Outlook**lehetőséget, majd válassza a **kiválasztás**lehetőséget.  Az Outlook most megjelenik a *nyilvános alkalmazások*területen.

   A folytatáshoz kattintson a **Tovább** gombra.

5. Az **Adatvédelem** lap azokat a beállításokat tartalmazza, amelyekkel meghatározható, hogy a felhasználók hogyan használják az adatvédelmi szabályzat hatálya alá eső alkalmazásokban tárolt adatszolgáltatásokat. Adja meg az alábbi lehetőségeket:

   Alább *adatátvitel*konfigurálja a következő beállításokat, és az összes többi beállítást az alapértelmezett értékekre hagyja:

   - Ha **más alkalmazásokba szeretné elküldeni a szervezeti adatküldést**, válassza a **nincs**lehetőséget.  
   - **Más alkalmazásoktól érkező adatok fogadásához**válassza a **nincs**lehetőséget.  
   - A **szervezeti adatmásolatok mentéséhez**válassza a **Letiltás**lehetőséget.  
   - A **kivágási, másolási és beillesztési műveletek korlátozása más alkalmazások között**válassza a **Letiltva**lehetőséget. 

   ![Válassza ki az Outlook-alkalmazás védelmi házirendjének adatáthelyezési beállításait.](./media/tutorial-protect-email-on-unmanaged-devices/data-protection-settings.png)

   A folytatáshoz kattintson a **tovább** gombra.

6. A **hozzáférési követelmények** lapon megadhatja a PIN-kód és a hitelesítő adatok azon követelményeit, amelyeket a felhasználóknak meg kell felelniük az alkalmazások munkahelyi környezetben való eléréséhez. Konfigurálja a következő beállításokat, és az összes többi beállítást hagyja az alapértelmezett értékeken:

   - A **PIN-kód eléréséhez**válassza a **kötelező**lehetőséget.
   - A **hozzáféréshez használt munkahelyi vagy iskolai fiók hitelesítő adatai**területen válassza a **kötelező**lehetőséget.

   ![Válassza ki az Outlook-alkalmazás védelmi házirendjének hozzáférési műveleteit.](./media/tutorial-protect-email-on-unmanaged-devices/access-requirements-settings.png)

   A folytatáshoz kattintson a **tovább** gombra.

7. A **feltételes indítás** lapon megadhatja az alkalmazás-védelmi szabályzat bejelentkezési biztonsági követelményeinek beállításához szükséges beállításokat. Ebben az oktatóanyagban nem kell konfigurálnia ezeket a beállításokat.

   A folytatáshoz kattintson a **Tovább** gombra.

8. A **hozzárendelések** lapon hozzárendelheti az alkalmazás védelmi házirendjét a felhasználók csoportjaihoz. Ebben az oktatóanyagban ezt a házirendet nem rendeli hozzá egy csoporthoz.  
 ezeket a beállításokat nem kell konfigurálnia.

   A folytatáshoz kattintson a **Tovább** gombra.

9. A **következő: Review + létrehozás** oldalon tekintse át az alkalmazás védelmi házirendjéhez megadott értékeket és beállításokat. A **Létrehozás** gombra kattintva hozza létre az alkalmazás-védelmi szabályzatot az Intune-ban.

Létrejön az Outlook alkalmazás-védelmi szabályzata. Ezután beállíthatja a feltételes hozzáférést, hogy az eszközök az Outlook alkalmazást használják.

## <a name="create-conditional-access-policies"></a>Feltételes hozzáférési szabályzatok létrehozása

Most hozzunk létre két feltételes hozzáférési szabályzatot az összes eszköz platformjának lefedéséhez.  

- Az első szabályzat megköveteli, hogy a modern hitelesítési ügyfelek a jóváhagyott Outlook alkalmazást és multi-Factor Authentication (MFA) hitelesítést használják. A modern hitelesítési ügyfelek közé tartoznak az iOS és az Android rendszerhez készült Outlook.  

- A második szabályzat megköveteli, hogy az Exchange ActiveSync-ügyfelek a jóváhagyott Outlook alkalmazást használják. (A Exchange Active Sync jelenleg nem támogatja az eszköz platformján kívüli feltételeket). A feltételes hozzáférési szabályzatokat az Azure AD-portálon vagy az Intune-portálon is konfigurálhatja. Mivel már az Intune portálon vagyunk, itt fogjuk létrehozni a szabályzatot.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>MFA-szabályzat létrehozása modern hitelesítési ügyfelek számára  

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **Endpoint security** >  a **feltételes hozzáférés** > **új szabályzat**lehetőséget.  

3. A **név**mezőben adja meg **a modern hitelesítési ügyfelekhez tartozó tesztelési házirendet**.  

4. A **Hozzárendelések** alatt válassza a **Felhasználók és csoportok** lehetőséget. A **Belefoglalás** lapon válassza a **Minden felhasználó** lehetőséget, majd a **Kész** elemet.

5. A **hozzárendelések**területen válassza a **felhőalapú alkalmazások vagy műveletek**elemet. Mivel az Office 365 Exchange Online e-mailjeit szeretnénk megvédeni, a következő lépések segítségével választhatjuk ki:

   1. A **Belefoglalás** lapon válassza az **Alkalmazások kiválasztása** elemet.
   2. Válassza a **Kijelölés** elemet.
   3. Az alkalmazások listában válassza az **Office 365 Exchange Online**lehetőséget, majd válassza a **kiválasztás**lehetőséget.
   4. Kattintson a **kész** gombra az új házirend panelre való visszatéréshez.

   ![Az Office 365 Exchange Online alkalmazás kiválasztása](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

6. A **Hozzárendelések** alatt válassza a **Feltételek** > **Eszközplatformok** lehetőséget.

   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.
   2. A **beágyazás** lapon válassza a **bármely eszköz**elemet.
   3. Válassza a **Kész** lehetőséget.

7. A **feltételek** ablaktáblán válassza az **ügyfélalkalmazások**elemet.

   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.
   2. Válassza a **Mobile apps és az asztali ügyfelek** és a **modern hitelesítési ügyfelek**lehetőséget.
   3. Törölje a jelet a többi jelölőnégyzetből.
   4. Válassza a **kész** > **kész** lehetőséget az új házirend panelre való visszatéréshez.

   ![Mobil alkalmazások és ügyfelek kiválasztása](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

8. A **Hozzáférés-vezérlés** alatt válassza ki az **Engedélyezés** elemet.

   1. Az **Engedélyezés** lapon válassza az **Engedélyek megadása** lehetőséget.
   2. Válassza a **többtényezős hitelesítés megkövetelése**lehetőséget.
   3. Válassza ki a **Jóváhagyott ügyfélalkalmazás megkövetelése** elemet.
   4. A **Több vezérlő esetén** elem alatt válassza a **minden kiválasztott vezérlő megkövetelésére** szolgáló lehetőséget. Ez a beállítás biztosítja, hogy mindkét kiválasztott követelmény érvényben legyen, amikor egy eszköz hozzá próbál férni az e-mailekhez.
   5. Válassza a **Kijelölés** elemet.

   ![Hozzáférés-vezérlés kiválasztása](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

9. A **házirend engedélyezése**területen válassza **a**be lehetőséget, majd válassza a **Létrehozás**lehetőséget.

   ![Házirend létrehozása](./media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

Létrejön a modern hitelesítési ügyfelek feltételes hozzáférési szabályzata. Most létrehozhat egy házirendet Exchange Active Sync-ügyfelek számára.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Szabályzat létrehozása Exchange Active Sync ügyfelek számára

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **Endpoint security** > a **feltételes hozzáférés** > **új szabályzat**lehetőséget.

3. A **név**mezőben adja meg **az EAS-ügyfelekhez tartozó tesztelési**szabályzatot.

4. A **Hozzárendelések** alatt válassza a **Felhasználók és csoportok** lehetőséget. A *Belefoglalás* lapon válassza a **Minden felhasználó** lehetőséget, majd a **Kész** elemet.

5. A **hozzárendelések**területen válassza a **felhőalapú alkalmazások vagy műveletek**elemet. Válassza az Office 365 Exchange Online e-mailek elemet a következő lépésekkel:

   1. A *Belefoglalás* lapon válassza az **Alkalmazások kiválasztása** elemet.
   2. Válassza a **Kijelölés** elemet.
   3. Az *alkalmazások*listájából válassza ki az **Office 365 Exchange Online**elemet, majd válassza a **kiválasztás**, majd a **kész**lehetőséget.
  
6. A **Hozzárendelések** alatt válassza a **Feltételek** > **Eszközplatformok** lehetőséget.

   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.
   2. A **beágyazás** lapon válassza ki a kívánt **eszközt**, majd kattintson a **kész**gombra.

7. A **feltételek** ablaktáblán válassza az **ügyfélalkalmazások**elemet.

   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.
   2. Válassza **a Mobile apps és az asztali ügyfelek**lehetőséget.
   3. Válassza az **Exchange ActiveSync-ügyfelek** lehetőséget, és **alkalmazza a házirendet csak a támogatott platformokra**.  
   4. Az összes többi jelölőnégyzet jelölését törölje.  
   5. Kattintson a **Kész**, majd ismét a **Kész** gombra.  

   ![Alkalmazás a támogatott platformokra](./media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

8. A **Hozzáférés-vezérlés** alatt válassza ki az **Engedélyezés** elemet.

   1. Az **Engedélyezés** lapon válassza az **Engedélyek megadása** lehetőséget.
   2. Válassza ki a **Jóváhagyott ügyfélalkalmazás megkövetelése** elemet. Az összes többi jelölőnégyzet jelölését törölje.
   3. Válassza a **Kijelölés** elemet.

   ![Jóváhagyott ügyfélalkalmazás megkövetelése](./media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

9. A **házirend engedélyezése**területen válassza **a**be lehetőséget, majd válassza a **Létrehozás**lehetőséget.

Az alkalmazás-védelmi szabályzatok és a feltételes hozzáférés már érvényben van, és készen áll a tesztelésre.

## <a name="try-it-out"></a>Próbálja ki!

A létrehozott házirendekkel az eszközöknek regisztrálniuk kell az Intune-ban, és az Outlook Mobile alkalmazást kell használniuk az Office 365 e-mail eléréséhez. A forgatókönyv teszteléséhez egy iOS-eszközön próbáljon meg a tesztelési bérlő egyik felhasználójának hitelesítő adataival bejelentkezni az Exchange Online-ra.

1. iPhone-on történő teszteléshez válassza a **Beállítások** > **Jelszavak és fiókok** > **Fiók hozzáadása** > **Exchange** elemet.

2. Adja meg a tesztelési bérlő felhasználójának e-mail-címét, és válassza a **Tovább** gombot.  
3. Válassza a **Bejelentkezés** elemet.

4. Adja meg a tesztfelhasználó jelszavát, és válassza a **Bejelentkezés** gombot.

5. Az üzenetnek **további információra van szüksége** , ami azt jelenti, hogy a rendszer felszólítja az MFA beállítására. Folytassa a további ellenőrzési módszer megadásával.

6. Ezután megjelenik egy üzenet, amely szerint az erőforrást az informatikai részleg által nem jóváhagyott alkalmazással próbálja megnyitni. Az üzenet azt jelenti, hogy a natív posta alkalmazás használatával blokkolva van. A bejelentkezés megszakítása.

7. Nyissa meg az Outlook alkalmazást, és válassza a **beállítások** > **fiók hozzáadása** > **e-mail fiók hozzáadása**lehetőséget.

8. Adja meg a tesztelési bérlő felhasználójának e-mail-címét, és válassza a **Tovább** gombot.

9. Nyomja meg **az Office 365-vel való bejelentkezést**. A rendszer további hitelesítést és regisztrációt kér. Miután bejelentkezett, tesztelheti az olyan műveleteket, mint például a Kivágás, a másolás, a Beillesztés és a Mentés másként lehetőség.

## <a name="clean-up-resources"></a>Az erőforrások eltávolítása

Ha már nincs szükség a tesztszabályzatokra, eltávolíthatja őket.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** **megfelelőségi szabályzatok**lehetőséget.

3. A **Szabályzat neve** listában válassza a tesztszabályzat helyi menüjét ( **...** ), majd válassza a **Törlés** elemet. Válassza az **OK** lehetőséget a megerősítéshez.

4. Válassza a **végpontok biztonsága** > **feltételes hozzáférés**lehetőséget.

5. A **szabályzat neve** listában válassza a helyi menüt ( **..** .) minden egyes tesztelési házirendhez, majd válassza a **Törlés**lehetőséget. A megerősítéshez válassza az **Igen** lehetőséget.

## <a name="next-steps"></a>További lépések
Ebben az oktatóanyagban létrehozott egy alkalmazás-védelmi szabályzatot, amely korlátozza, hogy a felhasználó mit tehet az Outlook alkalmazással, és feltételes hozzáférési szabályzatokat hozott létre az Outlook alkalmazás megköveteléséhez, valamint az MFA használatát a modern hitelesítési ügyfelek számára. További információ az Intune és a feltételes hozzáférés használatáról más alkalmazások és szolgáltatások elleni védelemhez: [feltételes hozzáférés beállítása](conditional-access.md).
