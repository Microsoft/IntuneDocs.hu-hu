---
title: Oktatóanyag – Exchange Online-levelezés biztosítása a felügyelt eszközökön
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan védheti meg az Exchange Online-t az iOS Intune megfelelőségi szabályzatokkal és az Azure AD feltételes hozzáféréssel a felügyelt eszközök és az Outlook alkalmazás megköveteléséhez.
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
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9deee0dca675d7fd95445131ed98ea195972c6ac
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74409823"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Oktatóanyag: Az Exchange Online e-mailjeinek védelme felügyelt eszközökön

Ismerje meg, hogyan használhatók az eszközök megfelelőségi szabályzatai feltételes hozzáféréssel annak biztosításához, hogy az iOS-eszközök csak akkor férhessenek hozzá az Exchange Online e-mailekhez, ha azokat az Intune felügyeli, és egy jóváhagyott e-mail alkalmazás használatával

Az oktatóanyag segítségével megtanulhatja a következőket:

> [!div class="checklist"]
> * Egy Intune iOS eszközmegfelelőségi szabályzat létrehozása, ahol megadja, hogy milyen feltételeknek kell teljesülnie ahhoz, hogy az eszköz megfelelő legyen.
> * Hozzon létre egy Azure Active Directory (Azure AD) feltételes hozzáférési szabályzatot, amely megköveteli az iOS-eszközök regisztrálását az Intune-ban, teljesíti az Intune-szabályzatokat, és a jóváhagyott Outlook Mobile App használatával fér hozzá az Exchange Online-hoz.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek

Az oktatóanyag végrehajtásához szüksége lesz egy tesztelési bérlőre a következő előfizetésekkel:

- Prémium szintű Azure Active Directory ([ingyenes próbaverzió](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))

- Office 365 Vállalati előfizetés, ami magában foglalja az Exchange-et ([ingyenes próbaverzió](https://go.microsoft.com/fwlink/p/?LinkID=510938))

Mielőtt elkezdené, hozzon létre az iOS eszközök számára egy teszteszközprofilt a következő oktatóanyag lépéseit követve: [Rövid útmutató: E-mail-profil létrehozása iOS operációs rendszeren](../configuration/quickstart-email-profile.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) [globális rendszergazdaként](../fundamentals/users-add.md#types-of-administrators) vagy Intune [szolgáltatás-rendszergazdaként](../fundamentals/users-add.md#types-of-administrators). Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="create-the-ios-device-compliance-policy"></a>Az iOS eszközmegfelelőségi szabályzat létrehozása

Hozzon létre egy Intune eszközmegfelelőségi szabályzatot, ahol megadja, hogy milyen feltételeknek kell teljesülnie ahhoz, hogy az eszköz megfelelő legyen. Ebben az oktatóanyagban iOS-eszközökhöz hozunk létre eszközmegfelelőségi szabályzatot. A megfelelőségi szabályzatok platformspecifikusak, így külön megfelelőségi szabályzatot kell létrehoznia minden értékelni kívánt eszközplatformhoz.

1. Az Intune-ban válassza az **eszközök** > **megfelelőségi szabályzatok** > **házirend létrehozása**lehetőséget.

2. A **név**mezőben adja meg az iOS-es **megfelelőségi szabályzatok tesztelését**.

3. A **Leírás**mezőben adja meg az iOS-es **megfelelőségi szabályzatok tesztelését**.

4. A **platform**területen válassza az **iOS/iPadOS**lehetőséget.

5. Kattintson a **Beállítások** > **E-mail** elemre.

   1. **A mobileszközöktől felügyelt e-mail-profilt megkövetelő beállítás** mellett válassza a **Kötelező** lehetőséget.

   2. Válassza az **OK** gombot.

   ![A felügyelt e-mail-profil megkövetelése az e-mail-megfelelőségi szabályzatban](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)

6. Válassza az **Eszközállapot** lehetőséget. A **Jailbreakelt eszközök** mellett válassza a **Letiltás** lehetőséget, majd kattintson az **OK** gombra.

7. Válassza a **Rendszerbiztonság** elemet, és adja meg **Jelszó** beállításait. Az oktatóanyag végrehajtásához válassza a következő ajánlott beállításokat:

   - A **Jelszó szükséges a mobileszközök feloldásához** elemnél válassza a **Kötelező** lehetőséget.

   - Az **Egyszerű jelszavak** elemnél válassza a **Letiltás** lehetőséget.

   - A **jelszó minimális hosszához** adja meg a **4** értéket.

     > [!TIP]
     > A szürke és a dőlt alapértelmezett értékek csak javaslatok. A beállítások konfigurálásához javasolt értékeket kell cserélnie.

   - A **Kötelező jelszótípus** elemnél válassza ki az **Alfanumerikus** lehetőséget.

   - A **Jelszó kérése ennyi perccel a képernyőzárolás után** elemnél válassza az **Azonnal** lehetőséget.

   - A **Jelszó érvényessége (napokban)** elemnél adja meg a **41** értéket.

   - Az **Újból nem használható jelszavak száma** elemnél adjon meg **5-öt**.
 
   ![Az e-mail-megfelelőségi szabályzat jelszóbeállításainak megadása](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Válassza az **OK**, majd újra az **OK** elemet.

9. Válassza a **Létrehozás** lehetőséget.

## <a name="create-the-conditional-access-policy"></a>A feltételes hozzáférési szabályzat létrehozása

Most létrehozunk egy feltételes hozzáférési szabályzatot, amelyhez minden eszköz platformjának regisztrálnia kell az Intune-ban, és meg kell felelnie az Intune megfelelőségi szabályzatának az Exchange Online-hoz való hozzáféréshez. Ezenkívül az Outlook alkalmazásra is szükség lesz az e-mailek eléréséhez. A feltételes hozzáférési szabályzatok az Azure AD-portálon vagy az Intune-portálon konfigurálhatók. Mivel már az Intune portálon vagyunk, itt fogjuk létrehozni a szabályzatot.

1. Az Intune-ban válassza az **Endpoint security** > a **feltételes hozzáférés** > **új szabályzat**lehetőséget.

2. A **név**mezőben adja meg **az Office 365-e-mailek tesztelési szabályzatát**.

3. A **Hozzárendelések** alatt válassza a **Felhasználók és csoportok** lehetőséget. A **Belefoglalás** lapon válassza a **Minden felhasználó** lehetőséget, majd a **Kész** elemet.

4. A **hozzárendelések**területen válassza a **felhőalapú alkalmazások vagy műveletek**elemet. Mivel az Office 365 Exchange Online e-mailjeit szeretnénk megvédeni, a következő lépések segítségével választhatjuk ki:

   1. A **Belefoglalás** lapon válassza az **Alkalmazások kiválasztása** elemet.

   2. Válassza a **Kijelölés** elemet. 

   3. A felsorolt alkalmazások közül válassza ki az **Office 365 Exchange Online-t**, majd kattintson a **Kiválasztás** gombra. 

   4. Válassza a **Kész** lehetőséget.
  
   ![Az Office 365 Exchange Online alkalmazás kiválasztása](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. A **Hozzárendelések** alatt válassza a **Feltételek** > **Eszközplatformok** lehetőséget.

   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.

   2. A **beágyazás** lapon válassza ki a kívánt **eszközt**, majd kattintson a **kész**gombra. 

   3. Ismét válassza a **Kész** gombot.

   ![Bármilyen eszköz belefoglalása](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. A **Hozzárendelések** alatt válassza a **Feltételek** > **Ügyfélalkalmazások** lehetőséget.

   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.

   2. A jelen oktatóanyag esetében válassza ki a **Mobilalkalmazások és asztali ügyfelek** és a **Modern hitelesítési ügyfelek** (amely olyan alkalmazásokra vonatkozik, mint az Outlook iOS rendszerhez vagy az Outlook Android rendszerhez) lehetőségeket. Az összes többi jelölőnégyzet jelölését törölje.

   3. Kattintson a **Kész**, majd ismét a **Kész** gombra.

   ![Alkalmazások és ügyfelek kiválasztása](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. A **Hozzáférés-vezérlés** alatt válassza ki az **Engedélyezés** elemet.

   1. Az **Engedélyezés** lapon válassza az **Engedélyek megadása** lehetőséget.

   2. Válassza ki az **Eszköz megfelelőként való megjelölésének megkövetelése** elemet.

   3. Válassza ki a **Jóváhagyott ügyfélalkalmazás megkövetelése** elemet.

   4. A **Több vezérlő esetén** elem alatt válassza a **minden kiválasztott vezérlő megkövetelésére** szolgáló lehetőséget. Ez a beállítás biztosítja, hogy mindkét kiválasztott követelmény érvényben legyen, amikor egy eszköz hozzá próbál férni az e-mailekhez.

   5. Válassza a **Kijelölés** elemet.

   ![Conrols kiválasztása](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. A **Szabályzat engedélyezése** alatt válassza a **Bekapcsolás** elemet.

   ![Szabályzat engedélyezése](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. Válassza a **Létrehozás** lehetőséget.

## <a name="try-it-out"></a>Próbálja ki!

A létrehozott szabályzat megköveteli, hogy az Office 365 e-mail-alkalmazásába történő belépést megkísérlő iOS-eszközök mindegyikének regisztrálnia kell az Intune-ban, és az iOS rendszerhez készült Office mobilalkalmazást kell használnia. A forgatókönyv teszteléséhez egy iOS-eszközön próbáljon meg a tesztelési bérlő egyik felhasználójának hitelesítő adataival bejelentkezni az Exchange Online-ra. A rendszer kérni fogja, hogy regisztrálja az eszközt és telepítse az Outlook mobilalkalmazást.

1. iPhone-on történő teszteléshez válassza a **Beállítások** > **Jelszavak és fiókok** > **Fiók hozzáadása** > **Exchange** elemet.

2. Adja meg a tesztelési bérlő felhasználójának e-mail-címét, és válassza a **Tovább** gombot.

3. Válassza a **Bejelentkezés** elemet.

4. Adja meg a tesztfelhasználó jelszavát, és válassza a **Bejelentkezés** gombot.

5. Megjelenik egy üzenet, amely figyelmezteti, hogy az eszköznek felügyeltnek kell lennie az erőforráshoz történő hozzáféréshez, és felkínálja a regisztráció lehetőségét.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha már nincs szükség a tesztszabályzatokra, eltávolíthatja őket.
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként.

2. Válassza az **eszközök** > **megfelelőségi szabályzatok**lehetőséget.

3. A **Szabályzat neve** listában válassza a tesztszabályzat helyi menüjét ( **...** ), majd válassza a **Törlés** elemet. Válassza az **OK** lehetőséget a megerősítéshez.

4. Válassza a **végpontok biztonsága** > **feltételes hozzáférés**lehetőséget.

5. A **Szabályzat neve** listában válassza a tesztszabályzat helyi menüjét ( **...** ), majd válassza a **Törlés** elemet. Válassza az **Igen** lehetőséget a megerősítéshez.

## <a name="next-steps"></a>További lépések

Az oktatóanyag során olyan szabályzatokat hozott létre, amelyek megkövetelik, hogy az Exchange Online e-mail-alkalmazásába belépni kívánó iOS-eszközök regisztráljanak az Intune-ban és az Outlook alkalmazást használják. Ha szeretné megtudni, hogyan használhatja az Intune-t feltételes hozzáféréssel más alkalmazások és szolgáltatások, például az Office 365 Exchange ActiveSync-ügyfelek számára az Exchange Online-hoz, tekintse [meg a feltételes hozzáférés beállítása](conditional-access.md)című témakört.
