---
title: Rövid útmutató – E-mail-eszközprofil létrehozása iOS-hez
titleSuffix: Microsoft Intune
description: Elsajátíthatja, hogyan használhatja a Microsoft Intune-t e-mailes eszközprofil létrehozására, hogy az iOS-eszközök biztonságosan csatlakozhassanak a vállalati levelező rendszerhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b2f1372a6d7ced09a9ebdfc11cbad69501827bc
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059333"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Rövid útmutató: E-mail-eszközprofil létrehozása iOS-hez

Ez a rövid útmutató bemutatja, hogyan hozhat létre e-mail-eszközprofilt iOS-eszközökhöz. Ez a profil meghatározza az iOS-eszközön a beépített e-mail-alkalmazás céges levelező rendszerhez való csatlakozásához szükséges beállításokat. Az e-mail-eszközprofilok segítenek standard beállítások megadásban a különféle eszközökön, valamint saját kötelező beállítások nélkül is lehetővé teszik a végfelhasználók számára, hogy az eszközükön hozzáférjenek a céges postafiókjukhoz. Az e-mailek további védelme érdekében használhat egy e-mail-profilt, amellyel meghatározhatja, hogy az eszközök megfelelőek-e, majd beállíthatja a feltételes hozzáférést, hogy csak a megfelelő eszközök férhessenek hozzá az e-mailekhez. Az e-mail-profilokra vonatkozó részleteket megtekintheti [Az e-mail-beállítások konfigurálása a Microsoft Intune-ban](email-settings-configure.md) című szakaszban.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="create-an-ios-email-profile"></a>iOS-es e-mail-profil létrehozása

1. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

   ![E-mail-profil létrehozása iOS-hez](./media/quickstart-email-profile/ios-create-profile.png)

2. A **Név** alatt adjon meg egy leíró nevet az új profilhoz. Ebben a példában adja meg **Az iOS-hez munkahelyi e-mail-cím szükséges** nevet.
3. Adja meg az alábbi profiladatokat:
    - A **Leírás** mezőben adja meg **Munkahelyi e-mail-cím használatának megkövetelése az iOS-eszközöktől** szöveget.
    - A **Platform** beállításnál adja meg az **iOS** értéket.
    - A **Profiltípus** területen válassza az **E-mail** lehetőséget.

        ![Az iOS-hez használható e-mail profil létrehozása](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Válassza a **Beállítások** lehetőséget, és adja meg az alábbi beállításokat (hagyja meg az egyéb beállítások alapértelmezett értékét):
   - **Levelezési kiszolgáló**: Ehhez a rövid útmutatóhoz adja meg az **outlook.office365.com** címet. Ez a beállítás határozza meg az iOS levelező alkalmazás által a levelező rendszerhez való csatlakozásra használt levelezési kiszolgáló Exchange-helyét (URL-címét).
   - **Fiók neve**: Adja meg a **vállalati e-mail-címét**.
   - **Felhasználói név attribútum az AAD-ből**: Ez a név az Intune által az Azure Active Directoryből (Azure AD) lekért attribútum. Az Intune dinamikusan generálja a felhasználónevet ehhez a profilhoz a név felhasználásával. Ebben a rövid útmutatóban azt feltételezzük, hogy az **Egyszerű felhasználónév** értékét szeretnénk a profil felhasználóneveként használni (például user1@contoso.com).
   - **E-mail-cím attribútuma az AAD-ből**: Ez a beállítás az Azure AD-ből származó e-mail-cím, amelyet az Exchange-be való bejelentkezésre használunk. Ebben a rövid útmutatóban válassza az **Egyszerű felhasználónév** lehetőséget.
   - **Hitelesítési módszer**: Ehhez a rövid útmutatóhoz válassza **Felhasználónév és jelszó** lehetőséget. (A **Tanúsítvány** lehetőséget is választhatja, ha már beállította egy tanúsítványt az Intune-hoz.)

        ![E-mail-profil létrehozása iOS-használatra](./media/quickstart-email-profile/ios-email-profile.png)

5. Válassza **az OK** > **Létrehozás**elemet. Az új profil megjelenik a profilok listájában az irányítópulttal együtt, hogy figyelhesse, hogyan rendelték hozzá a profilt iOS-eszközökhöz és iOS-felhasználókhoz.
6. Válassza a **Hozzárendelések** lehetőséget.
7. Válassza a **Belefoglalás** fület, majd a **Minden felhasználó és minden eszköz** lehetőséget. 
8. Válassza a **Mentés** lehetőséget.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha nem kívánja használni a létrehozott profilt további oktatóanyagokhoz vagy tesztelésre, akkor most már törölheti.

1. Az Intune-ban válassza az **Eszközkonfiguráció**, majd a **Profilok** lehetőséget.
2. Válassza ki a létrehozott **Az iOS-hez munkahelyi e-mail-cím szükséges** tesztprofilt.
3. Válassza a profil melletti három pontot ( **...** ), majd a **Törlés** gombot.

## <a name="next-steps"></a>További lépések

Ezt a rövid útmutató követve létrehozott egy e-mail-profilt az iOS-eszközökhöz. Most használhatja ezt a profilt annak megállapítására, hogy egy iOS-eszköz kompatibilis-e, ehhez létre kell hozni egy megfelelőségi profilt, amely nem megfelelőként jelöl meg minden iOS-eszközt, amely nem egyezik a profillal. A további védelem érdekében létrehozhat egy feltételes hozzáférési szabályzatot, amely letiltja a nem megfelelő iOS-eszközök hozzáférését az e-mailekhez. További információk az eszközmegfelelőségi szabályzatokról: [Az Intune eszközmegfelelőségi szabályzatai – első lépések](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Oktatóanyag: Az Exchange Online e-mailjeinek védelme felügyelt eszközökön](../tutorial-protect-email-on-enrolled-devices.md)
