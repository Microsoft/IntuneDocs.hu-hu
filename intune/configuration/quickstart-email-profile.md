---
title: Rövid útmutató – e-mail-profil létrehozása iOS-es/iPadOS-eszközökhöz
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan használhatja a Microsoft Intunet e-mail profil létrehozásához, hogy az iOS/iPadOS-eszközök biztonságosan csatlakozhassanak a vállalati e-mailekhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: af2576c44e0486dbd859a56896db3b7d0ffc6cff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511068"
---
# <a name="quickstart-create-an-email-device-profile-for-iosipados"></a>Gyors útmutató: e-mail eszköz profiljának létrehozása iOS/iPadOS

Ebből a rövid útmutatóból megtudhatja, hogyan hozhat létre egy e-mail-profilt iOS/iPadOS-eszközökhöz. Ez a profil határozza meg azokat a beállításokat, amelyek szükségesek az iOS/iPadOS eszközön lévő beépített e-mail-alkalmazáshoz a vállalati e-mailekhez való kapcsolódáshoz. Az e-mail-eszközprofilok segítenek standard beállítások megadásban a különféle eszközökön, valamint saját kötelező beállítások nélkül is lehetővé teszik a végfelhasználók számára, hogy az eszközükön hozzáférjenek a céges postafiókjukhoz. Az e-mailek további védelme érdekében használhat egy e-mail-profilt, amellyel meghatározhatja, hogy az eszközök megfelelőek-e, majd beállíthatja a feltételes hozzáférést, hogy csak a megfelelő eszközök férhessenek hozzá az e-mailekhez. Az e-mail-profilokra vonatkozó részleteket megtekintheti [Az e-mail-beállítások konfigurálása a Microsoft Intune-ban](email-settings-configure.md) című szakaszban.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központba](https://go.microsoft.com/fwlink/?linkid=2109431) globális rendszergazdaként vagy Intune szolgáltatás-rendszergazdaként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel létrehozta azt.

## <a name="create-an-iosipados-email-profile"></a>IOS/iPadOS e-mail profil létrehozása

1. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

   ![E-mail-profil létrehozása iOS/iPadOS az Intune-ban](./media/quickstart-email-profile/ios-create-profile.png)

2. A **Név** alatt adjon meg egy leíró nevet az új profilhoz. Ebben a példában adja meg **Az iOS-hez munkahelyi e-mail-cím szükséges** nevet.
3. Adja meg az alábbi profiladatokat:
    - A **Leírás**mezőben adja meg az **iOS/iPadOS eszközök munkahelyi e-mailek használatára való használatának megkövetelését**.
    - A **platform**területen válassza az **iOS/iPadOS**lehetőséget.
    - A **Profiltípus** területen válassza az **E-mail** lehetőséget.

        ![E-mail-profil létrehozása iOS/iPadOS-eszközökhöz az Intune-ban](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Válassza a **Beállítások** lehetőséget, és adja meg az alábbi beállításokat (hagyja meg az egyéb beállítások alapértelmezett értékét):
   - **Levelezési kiszolgáló**: Ehhez a rövid útmutatóhoz adja meg az **outlook.office365.com** címet. Ez a beállítás határozza meg az e-mail-kiszolgáló Exchange-helyét (URL-címét), amelyet az iOS/iPadOS levelezési alkalmazás fog használni az e-mailekhez való kapcsolódáshoz.
   - **Fiók neve**: Adja meg a **vállalati e-mail-címét**.
   - **Felhasználói név attribútum az AAD-ből**: Ez a név az Intune által az Azure Active Directoryből (Azure AD) lekért attribútum. Az Intune dinamikusan generálja a felhasználónevet ehhez a profilhoz a név felhasználásával. Ebben a rövid útmutatóban azt feltételezzük, hogy az **Egyszerű felhasználónév** értékét szeretnénk a profil felhasználóneveként használni (például user1@contoso.com).
   - **E-mail-cím attribútuma az AAD-ből**: Ez a beállítás az Azure AD-ből származó e-mail-cím, amelyet az Exchange-be való bejelentkezésre használunk. Ebben a rövid útmutatóban válassza az **Egyszerű felhasználónév** lehetőséget.
   - **Hitelesítési módszer**: Ehhez a rövid útmutatóhoz válassza **Felhasználónév és jelszó** lehetőséget. (A **Tanúsítvány** lehetőséget is választhatja, ha már beállította egy tanúsítványt az Intune-hoz.)

        ![E-mail-profil létrehozása iOS/iPadOS használatra](./media/quickstart-email-profile/ios-email-profile.png)

5. Válassza **az OK** > **Létrehozás**elemet. Az új profil megjelenik a profilok listán a megjelenő irányítópulton, így nyomon követheti, hogy a profil hogyan lett hozzárendelve az iOS/iPadOS-eszközökhöz és az iOS/iPadOS-felhasználókhoz.
6. Válassza a **Hozzárendelések** lehetőséget.
7. Válassza a **Belefoglalás** fület, majd a **Minden felhasználó és minden eszköz** lehetőséget. 
8. Válassza a **Mentés** lehetőséget.

## <a name="clean-up-resources"></a>Erőforrások eltávolítása

Ha nem kívánja használni a létrehozott profilt további oktatóanyagokhoz vagy tesztelésre, akkor most már törölheti.

1. Az Intune-ban válassza az **Eszközkonfiguráció**, majd a **Profilok** lehetőséget.
2. Válassza ki a létrehozott tesztelési profilt, **iOS/iPadOS munkahelyi e-mail-címre van szükség**.
3. Válassza a profil melletti három pontot ( **...** ), majd a **Törlés** gombot.

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban létrehozott egy e-mail-profilt iOS/iPadOS-eszközökhöz. Ezzel a profillal meghatározhatja, hogy egy iOS-/iPadOS-eszköz megfelel-e egy megfelelőségi szabályzat létrehozásával, amely nem megfelelőként jelöli meg azokat az iOS-/iPadOS-eszközöket, amelyek nem felelnek meg a profilnak. A további védelem érdekében létrehozhat egy feltételes hozzáférési szabályzatot, amely letiltja a nem megfelelő iOS/iPadOS-eszközök hozzáférését az e-mailekhez. További információk az eszközmegfelelőségi szabályzatokról: [Az Intune eszközmegfelelőségi szabályzatai – első lépések](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Oktatóanyag: Az Exchange Online e-mailjeinek védelme felügyelt eszközökön](../tutorial-protect-email-on-enrolled-devices.md)
