---
title: IOS-eszközök regisztrálása – felhasználó beléptetése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan állíthatja be az iOS-és a iPadOS-felhasználók regisztrációját.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f201cdac0f881ce03863704dd80d8635de52074a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505459"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>IOS-és iPadOS-felhasználói regisztráció beállítása (előzetes verzió)

Beállíthatja az Intune-t az iOS-és iPadOS-eszközök regisztrálásához az Apple felhasználói beléptetési folyamatával. A felhasználó beléptetésével a rendszergazdák a felügyeleti lehetőségek egyszerűsített részhalmazát érhetik el a többi regisztrációs módszerhez képest.

További információ a felhasználói regisztrációval elérhető lehetőségekről: a [felhasználói regisztráció által támogatott műveletek, jelszavak és egyéb beállítások](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> Az Apple felhasználói regisztrációjának támogatása az Intune-ban jelenleg előzetes verzióban érhető el.

## <a name="prerequisites"></a>Előfeltételek
- [Mobileszköz-felügyeleti (MDM) szolgáltató](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push-tanúsítvány](apple-mdm-push-certificate-get.md)
- [Felügyelt Apple ID azonosítók](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Felhasználói beléptetési profil létrehozása az Intune-ban

A beléptetési profil meghatározza az eszközök egy csoportjára alkalmazott beállításokat a regisztráció során. 

1. Az Intune-portálon válassza az **eszközök beléptetése** > **Apple-regisztráció** > **regisztrációs típus (előzetes verzió)**  > **létrehozási profil** > **iOS**lehetőséget. Ez a profil határozza meg, hogy az iOS-és iPadOS-végfelhasználók milyen regisztrációs élményt kapnak a vállalati Apple-módszerekkel nem regisztrált eszközökön. Ha módosítani szeretné a módosításokat, ezt a profilt a létrehozása után is szerkesztheti.

    ![Apple beléptetési profil létrehozása](./media/ios-user-enrollment/create-profile.png)

2. Az **alapvető beállítások** lapon adja meg a profil **nevét** és **leírását** felügyeleti célból. A felhasználók nem látják ezeket az adatokat. A **Név** mező felhasználásával dinamikus csoportot hozhat létre az Azure Active Directoryban. Használja a profilnevet az enrollmentProfileName paraméter meghatározásához, hogy ezzel a regisztrációs profillal rendelhesse hozzá az eszközöket. További információk az [Azure Active Directory-alapú dinamikus csoportokról](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Alapismeretek lap](./media/ios-user-enrollment/basics-page.png)


3. Válassza a **Tovább** elemet.

4. A **Beállítások** lapon megadhatja, hogy a felhasználók a kívánt regisztrációs típust használják. Másik lehetőségként beállíthatja az alapértelmezett értéket.

    ![Beállítások lap](./media/ios-user-enrollment/settings-page.png)

    - Ha azt szeretné, hogy a profil összes felhasználója használhassa a felhasználói regisztrációt, kövesse az alábbi lépéseket:
        1. Ahhoz, **hogy a felhasználó megkövetelje az eszköz típusának kiválasztását**, válassza a **nincs konfigurálva**lehetőséget.
        2. Az **alapértelmezett regisztráció típusa**beállításnál válassza a **felhasználói regisztráció**lehetőséget.
    - Ha azt szeretné, hogy a profil összes felhasználója használja az eszközök regisztrálását, kövesse az alábbi lépéseket:
        1. Ahhoz, **hogy a felhasználó megkövetelje az eszköz típusának kiválasztását**, válassza a **nincs konfigurálva**lehetőséget.
        2. Az **alapértelmezett regisztráció típusa**beállításnál válassza az **eszközök beléptetése**lehetőséget.
    - Ha az ebben a csoportban lévő összes felhasználó számára meg szeretné adni, hogy melyik regisztrációs típust szeretné használni, válassza a **kötelező** lehetőséget, ha a **felhasználónak az eszköz típusának**kiválasztását igényli. Amikor a felhasználók regisztrálják az eszközeiket, választhatják, hogy az eszköz tulajdonosa és a **(vállalat) tulajdonában** **van** -e az eszköz. Ha az előbbi lehetőséget választja, az eszköz regisztrálása a felhasználói regisztráció használatával történik. Ha az utóbbit választják, az eszköz regisztrálása az eszközök regisztrálásával történik. Ha a felhasználó úgy dönt, hogy az **eszköz tulajdonosa**, akkor egy másik lehetőség is gondoskodik a teljes eszköz védelméről, vagy csak a biztonságos munkavégzéssel kapcsolatos alkalmazások és adatmennyiségek biztonságáról. A végfelhasználó választása, hogy az eszköz csak az eszközön megvalósított regisztrációs típust határozza meg. Ez a felhasználói döntés nem jelenik meg az Intune-ban az eszköz tulajdonjoga attribútumban. További információ a felhasználói élményről: [IOS-eszköz hozzáférésének beállítása a vállalati erőforrásokhoz](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
    > [!NOTE]
    > A következő értesítés pontatlan, és el lesz távolítva a felhasználói felületen.
    > "A felhasználói regisztrációt célzó eszközökön való feltételes hozzáféréshez a Azure Authenticator alkalmazást kötelező alkalmazásként kell leküldeni a felhasználói csoport számára az egyszeri bejelentkezés és a Workplace Join engedélyezéséhez."
    > Rendszergazdaként nem kell végrehajtania semmilyen műveletet a hitelesítő alkalmazás felhasználóknak való leküldéséhez. A rendszer arra Céges portál utasítja a felhasználókat, hogy telepítse a hitelesítő alkalmazást a felhasználó beléptetési folyamatának elvégzéséhez, hogy ezek a forgatókönyvek megfelelően működjenek.

5. Válassza a **Tovább** elemet.

6. A **hozzárendelések** lapon válassza ki azokat a felhasználói csoportokat, amelyek azokat a felhasználókat tartalmazzák, amelyekhez hozzá szeretné rendelni ezt a profilt. Kiválaszthatja, hogy a profilt az összes felhasználóhoz vagy adott csoporthoz rendeli. A kiválasztott csoportokba tartozó összes felhasználó a fent kiválasztott beléptetési típust fogja használni. Az eszközbeállítások nem támogatottak a felhasználói beléptetési forgatókönyvek esetében, mert a szolgáltatás felhasználói identitásokon alapul, és nem az eszközökön. Kiválaszthatja, hogy a profilt az összes felhasználóhoz vagy adott csoporthoz rendeli.

    ![Hozzárendelések lap](./media/ios-user-enrollment/assignments-page.png)

7. Válassza a **Tovább** elemet.

8. A **felülvizsgálat és létrehozás** oldalon tekintse át a kívánt beállításokat, majd válassza a **Létrehozás** lehetőséget a profil felhasználókhoz való hozzárendeléséhez.

    ![Hozzárendelések lap](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Profil prioritása

A több regisztrációs típusú profil létrehozása után módosíthatja a prioritási sorrendet, amelyben alkalmazva vannak.

1. Az Intune-ban a Azure Portal válassza az **eszközök beléptetése** > **Apple-regisztráció** > **regisztrációs típus (előzetes verzió)** lehetőséget.
2. Húzza a listában szereplő profilokat a kívánt sorrendbe.

Bármely felhasználó profiljai közötti ütközés esetén a rendszer a magasabb prioritású profilt alkalmazza a felhasználó számára.


