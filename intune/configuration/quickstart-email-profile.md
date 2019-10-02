---
title: Rövid útmutató – E-mail-eszközprofil létrehozása iOS-hez
titleSuffix: Microsoft Intune
description: Elsajátíthatja, hogyan használhatja a Microsoft Intune-t e-mailes eszközprofil létrehozására, hogy az iOS-eszközök biztonságosan csatlakozhassanak a vállalati levelező rendszerhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ad26077c00bf4ad4350ebd9ee124d61a69b324
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730547"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>QuickStart E-mail eszköz profil létrehozása iOS rendszerhez

Ez a rövid útmutató bemutatja, hogyan hozhat létre e-mail-eszközprofilt iOS-eszközökhöz. Ez a profil meghatározza az iOS-eszközön a beépített e-mail-alkalmazás céges levelező rendszerhez való csatlakozásához szükséges beállításokat. Az e-mail-eszközprofilok segítenek standard beállítások megadásban a különféle eszközökön, valamint saját kötelező beállítások nélkül is lehetővé teszik a végfelhasználók számára, hogy az eszközükön hozzáférjenek a céges postafiókjukhoz. Az e-mailek további védelme érdekében használhat egy e-mail-profilt, amellyel meghatározhatja, hogy az eszközök megfelelőek-e, majd beállíthatja a feltételes hozzáférést, hogy csak a megfelelő eszközök férhessenek hozzá az e-mailekhez. Az e-mail-profilokra vonatkozó részleteket megtekintheti [Az e-mail-beállítások konfigurálása a Microsoft Intune-ban](email-settings-configure.md) című szakaszban.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon egy ingyenes próbafiókkal](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune-ba](https://aka.ms/intuneportal) globális rendszergazdaként vagy Intune-szolgáltatásadminisztrátorként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="create-an-ios-email-profile"></a>iOS-es e-mail-profil létrehozása
1. Az Intune-ban válassza az **Eszközkonfiguráció**, majd a **Profilok** lehetőséget.
2. Válassza a **Profil létrehozása** lehetőséget.
   
   ![E-mail-profil létrehozása iOS-hez](./media/quickstart-email-profile/ios-create-profile.png)

3. A **Név** alatt adjon meg egy leíró nevet az új profilhoz. Ebben a példában adja meg **Az iOS-hez munkahelyi e-mail-cím szükséges** nevet.
4. Adja meg az alábbi profiladatokat:
   - A **Leírás** mezőben adja meg **Munkahelyi e-mail-cím használatának megkövetelése az iOS-eszközöktől** szöveget.
   - A **Platform** beállításnál adja meg az **iOS** értéket.
   - A **Profiltípus** területen válassza az **E-mail** lehetőséget.
    
     ![Az iOS-hez használható e-mail profil létrehozása](./media/quickstart-email-profile/ios-email-profile-name.png)

5. Válassza a **Beállítások** lehetőséget, és adja meg az alábbi beállításokat (hagyja meg az egyéb beállítások alapértelmezett értékét):
   - **Levelezési kiszolgáló**: Ebben a rövid útmutatóban adja meg a **Outlook.office365.com**. Ez a beállítás határozza meg az iOS levelező alkalmazás által a levelező rendszerhez való csatlakozásra használt levelezési kiszolgáló Exchange-helyét (URL-címét).
   - **Fiók neve**: Adja meg a **vállalati e-mailt**.
   - **Username attribútum a HRE**: Ez a név a Azure Active Directory (Azure AD) által beolvasott Intune-attribútum. Az Intune dinamikusan generálja a felhasználónevet ehhez a profilhoz a név felhasználásával. Ebben a rövid útmutatóban azt feltételezzük, hogy az **Egyszerű felhasználónév** értékét szeretnénk a profil felhasználóneveként használni (például user1@contoso.com).
   - **E-mail-cím attribútum a HRE**: Ez a beállítás az Azure AD e-mail-címe, amely az Exchange-be való bejelentkezéshez lesz használva. Ebben a rövid útmutatóban válassza az **Egyszerű felhasználónév** lehetőséget.
   - **Hitelesítési módszer**: Ebben a rövid útmutatóban válassza a **Felhasználónév és jelszó**lehetőséget. (A **Tanúsítvány** lehetőséget is választhatja, ha már beállította egy tanúsítványt az Intune-hoz.)
    
     ![E-mail-profil létrehozása iOS-használatra](./media/quickstart-email-profile/ios-email-profile.png)

6. Kattintson az **OK** gombra.
7. Kattintson a **Létrehozás** gombra. Az új profil megjelenik a profilok listájában az irányítópulttal együtt, hogy figyelhesse, hogyan rendelték hozzá a profilt iOS-eszközökhöz és iOS-felhasználókhoz.
8. Válassza a **Hozzárendelések** lehetőséget.
9. Válassza a **Belefoglalás** fület, majd a **Minden felhasználó és minden eszköz** lehetőséget. 
10. Kattintson a **Mentés** gombra.

## <a name="clean-up-resources"></a>Az erőforrások eltávolítása
Ha nem kívánja használni a létrehozott profilt további oktatóanyagokhoz vagy tesztelésre, akkor most már törölheti.
1. Az Intune-ban válassza az **Eszközkonfiguráció**, majd a **Profilok** lehetőséget.
2. Válassza ki a létrehozott **Az iOS-hez munkahelyi e-mail-cím szükséges** tesztprofilt.
3. Válassza a profil melletti három pontot ( **...** ), majd a **Törlés** gombot.

## <a name="next-steps"></a>További lépések

Ezt a rövid útmutató követve létrehozott egy e-mail-profilt az iOS-eszközökhöz. Most használhatja ezt a profilt annak megállapítására, hogy egy iOS-eszköz kompatibilis-e, ehhez létre kell hozni egy megfelelőségi profilt, amely nem megfelelőként jelöl meg minden iOS-eszközt, amely nem egyezik a profillal. A további védelem érdekében létrehozhat egy feltételes hozzáférési szabályzatot, amely letiltja a nem megfelelő iOS-eszközök hozzáférését az e-mailekhez. További információk az eszközmegfelelőségi szabályzatokról: [Az Intune eszközmegfelelőségi szabályzatai – első lépések](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Oktatóanyag Exchange Online-levelezés biztosítása a felügyelt eszközökön @ no__t-0
