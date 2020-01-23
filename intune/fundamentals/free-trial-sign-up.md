---
title: Rövid útmutató – A Microsoft Intune ingyenes kipróbálása
titleSuffix: ''
description: Ezt a rövid útmutatót követve létrehoz majd egy ingyenes próbaelőfizetést, megismerheti a támogatott konfigurációkat és hálózati követelményeket, és ha kívánja, saját tartománynevét is konfigurálhatja.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/16/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1baf0b4273a9074ac7172c08240a8e3c3a9d7fa
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541115"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Rövid útmutató: A Microsoft Intune ingyenes kipróbálása

A Microsoft Intune lehetővé teszi, hogy az eszközök és alkalmazások kezelésével védje a munkatársak vállalati adatait. Ezt a rövid útmutatót követve létrehoz majd egy ingyenes előfizetést az Intune tesztkörnyezetben történő kipróbálásához.

Az Intune mobileszköz-felügyeletet (MDM) és Mobile App Management (MAM) szolgáltatást biztosít a Microsoft Endpoint Manager felügyeleti központtal felügyelt biztonságos felhőalapú szolgáltatásból. Az Intune használatával vállalata megfelelőségi szabályzatainak és követelményeinek eleget téve biztosíthatja munkatársai vállalati erőforrásainak (adatok, eszközök és alkalmazások) megfelelő konfigurálását, elérését és frissítését.

## <a name="prerequisites"></a>Előfeltételek
A Microsoft Intune beállítása előtt tekintse át az alábbi követelményeket:

- [Támogatott operációs rendszerek és böngészők](supported-devices-browsers.md)
- [A hálózati konfiguráció követelményei és a sávszélesség](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Regisztráció a Microsoft Intune ingyenes próbaverziójára

Az Intune kipróbálása 30 napig ingyenes. Ha már rendelkezik munkahelyi vagy iskolai fiókkal, **jelentkezzen be** vele, és adja hozzá az Intune-t az előfizetéshez. Ha még nem, **regisztrálhat** egy új fiókot, amellyel használatba veheti az Intune-t a cégében.

> [!IMPORTANT]
> Meglévő munkahelyi vagy iskolai fiókok nem vonhatók össze újonnan regisztrált fiókokkal.

1. Nyissa meg a [Microsoft Intune próbaverziójának](https://go.microsoft.com/fwlink/?linkid=2019088) oldalát, és töltse ki az űrlapot.

    ![Képernyőkép a Microsoft Intune próbaverziójának fiókregisztrációs weboldaláról](./media/free-trial-sign-up/account-sign-up-site-full-browser.png)

    Ha az informatikai operatív tevékenység és a felhasználók túlnyomó része nem az Ön földrajzi helyén van, érdemes lehet azt az adott földrajzi helyet kiválasztania az **Ország vagy régió** legördülő listában. Az Azure a regionális információt használja fel, hogy a megfelelő szolgáltatásokat nyújtsa. Ez a beállítás később már nem módosítható.

2. Hozzon létre fiókot a **.onmicrosoft.com** utótaggal kiegészített vállalati nevével. 

    ![Képernyőkép az Intune próbaverziós fiókjának új hitelesítő folyamatáról](./media/free-trial-sign-up/account-sign-up-site-user-id.png)

    Ha a szervezete saját egyéni tartománnyal rendelkezik, amelyet a **. onmicrosoft.com**nélkül kíván használni, akkor a jelen cikk későbbi részében ismertetett Microsoft 365 felügyeleti központban módosíthatja azt.

3. A regisztrációs folyamat végén megtekintheti az új fiók adatait.

    ![Fiókadatok képe](./media/free-trial-sign-up/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Bejelentkezés az Intune-ba a Microsoft Endpoint Managerben

Ha még nem jelentkezett be a portálra, hajtsa végre a következő lépéseket:

1. Nyisson meg egy böngészőablakot, és írja be a címsorba a következőt: **https://devicemanagement.microsoft.com** . 
2. Használja a fenti lépésekben megadott felhasználói azonosítót a bejelentkezéshez ( *yourID@yourdomain* . onmicrosoft.com).

    ![A portál bejelentkezési oldalának képe](./media/free-trial-sign-up/azure-portal-signin.png)

Amikor próbaverziót regisztrál, e-mailben elküldjük a fiókadatait és a regisztráció során megadott e-mail címet. Az e-mail megerősíti, hogy a próbaverzió aktív.

> [!TIP]
> A Microsoft Endpoint Managerrel végzett munka során jobb eredményekkel járhat, ha a böngészőt normál módban, nem pedig privát módban dolgozik.

## <a name="confirm-the-mdm-authority-in-intune"></a>A MDM-szolgáltató megerősítése az Intune-ban

Alapértelmezés szerint az ingyenes próbaverzió létrehozásakor az MDM-szolgáltató van beállítva. A következő lépések végrehajtásával ellenőrizheti, hogy az MDM-szolgáltató be van-e állítva:

1. Ha még nem jelentkezett be, jelentkezzen be a Microsoft Endpoint Managerbe.
2. Kattintson a **bérlői felügyelet**elemre.
3. Tekintse meg a bérlő adatait. Az **Mdm-szolgáltatót** **Microsoft Intune**értékre kell beállítani.

Ha a Microsoft Endpoint Managerbe való bejelentkezés után egy narancssárga szalagcím jelenik meg, amely azt jelzi, hogy még nem állította be a MDM-szolgáltatót, akkor most aktiválhatja. A mobileszköz-felügyeleti (MDM-) szolgáltató beállítása szabja meg, hogy miként kezelheti mobileszközeit. Az MDM-szolgáltatót még azelőtt kell beállítani, hogy a felhasználók eszközöket regisztrálhatnának a kezeléshez.

### <a name="to-set-the-mdm-authority-to-intune-follow-these-steps"></a>Az MDM-szolgáltató Intune-beli beállításához kövesse az alábbi lépéseket:

1. Nyisson meg egy böngészőablakot, és írja be a címsorba a következőt: **https://portal.azure.com** . 
2. Válassza a **Minden szolgáltatás** > **Microsoft Intune** lehetőséget.
3. Válassza azt a sávot, amely jelzi, hogy nem engedélyezte az eszközkezelést, vagy ha még nem látható a sáv, válassza az **Eszközök beléptetése** lehetőséget. Ha még nem engedélyezte az eszközkezelést meg fog jelenni az **MDM-szolgáltató kiválasztása** panel.

    > [!NOTE]
    > Ha beállította a MDM-szolgáltatót, a MDM-szolgáltatói értéket fogja látni az **eszközök beléptetése** panelen. A narancssárga szalagcím csak akkor jelenik meg, ha még nem állított be az MDM-szolgáltatót. 

    ![Az MDM-szolgáltató kiválasztása panel képe](./media/free-trial-sign-up/choose-mdm-authority.png) 

4. Ha a MDM-szolgáltató nincs beállítva, a **Mdm-szolgáltató választása**területen állítsa be a Mdm-szolgáltatót az **Intune Mdm Authority**értékre.

Az MDM-szolgáltatóról további információért lásd [A mobileszköz-felügyeleti szolgáltató beállítása](mdm-authority-set.md) szakaszt.

## <a name="configure-your-custom-domain-name-optional"></a>Egyéni tartománynév konfigurálása (nem kötelező)

Ahogy fent említettük, ha a szervezete rendelkezik a saját egyéni tartománnyal, amelyet a **. onmicrosoft.com**nélkül kíván használni, akkor a Microsoft 365 felügyeleti központban is megváltoztathatja. Az egyéni tartománynevet az alábbi lépésekkel adhatja hozzá, ellenőrizheti és konfigurálhatja.  

> [!IMPORTANT]
> A tartománynév *kezdeti* **onmicrosoft.com** része nem nevezhető át és nem távolítható el. Az Intune-nal használt *Egyéni* tartománynevek azonban hozzáadhatók, ellenőrizhetők vagy eltávolíthatók, így az üzleti identitása is megmarad. További információ: [Egyéni tartománynév konfigurálása](custom-domain-name-configure.md).

1. Lépjen a [Microsoft 365 felügyeleti központba](https://admin.microsoft.com) , és jelentkezzen be a rendszergazdai fiókjával.

2. A navigációs panelen kattintson a **Beállítás** > **Tartományok** > **Tartomány hozzáadása** elemre.

3. Gépelje be egyéni tartománynevét. Végül válassza a **Tovább** lehetőséget.

   ![A Microsoft 365 felügyeleti központ képernyőképe – tartomány hozzáadása](./media/free-trial-sign-up/domain-custom-add.png)

4. Győződjön meg arról, hogy Ön az előző lépésben megadott tartomány tulajdonosa. 
    
    A **Kód küldése e-mailben** lehetőséget választva e-mailt küld a tartománya regisztrált kapcsolattartójának. Az e-mail beérkezése után másolja ki a kódot, és illessze be az **Írja be az ellenőrzőkódot** címkéjű mezőbe. Ha az ellenőrző kód egyezik, a tartomány hozzá lesz adva a bérlőjéhez. Előfordulhat, hogy a megjelenő e-mail nem ismerős. Egyes regisztrátorok elrejtik a valós e-mail-címet. Emellett előfordulhat, hogy az e-mail-cím más, mint a tartomány regisztrálásakor.

   ![A Microsoft 365 felügyeleti központ képernyőképe – tartomány ellenőrzése](./media/free-trial-sign-up/domain-custom-verify.png)

   > [!NOTE]
   > TXT típusú rekordok ellenőrzésének részletes leírását a [DNS-rekordok létrehozása bármely DNS-szolgáltatón az Office 365-höz](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Rendszergazdai felületek

Két, leggyakrabban használt portált használhat:
- A Microsoft Endpoint Manager felügyeleti központjának ([https://devicemanagement.microsoft.com/](https://devicemanagement.microsoft.com/)) segítségével megismerheti az [Intune képességeit](what-is-intune.md). Ebben az esetben a rendszergazda az Intune-nal fog működni.
- A Microsoft 365 felügyeleti központ ([https://admin.microsoft.com](https://admin.microsoft.com)) a felhasználók hozzáadására és kezelésére szolgál, ha nem használja a Azure Active Directory. Továbbá fiókjának számlázási- támogatási- és egyéb aspektusait is kezelheti itt.

## <a name="next-steps"></a>További lépések

Ezt a rövid útmutatót követve létrehozott egy ingyenes előfizetést az Intune tesztkörnyezetben történő kipróbálásához. További információ az Intune beállításáról: [Az Intune beállítása](setup-steps.md).

Kövesse az Intune rövid útmutatóinak sorozatát a következő rövid útmutatóval.

> [!div class="nextstepaction"]
> [Rövid útmutató – Felhasználó létrehozása és licenc hozzárendelése az Intune-ban](quickstart-create-user.md)
