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
ms.openlocfilehash: 0872eef38e3ea5a70ebb64d3ae3c62069045fa97
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754624"
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

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **regisztrációs típusok (előzetes verzió)**  > **profil létrehozása** > **iOS/iPadOS**. Ez a profil határozza meg, hogy az iOS-és iPadOS-végfelhasználók milyen regisztrációs élményt kapnak a vállalati Apple-módszerekkel nem regisztrált eszközökön. Ha módosítani szeretné a módosításokat, ezt a profilt a létrehozása után is szerkesztheti.

    ![Apple beléptetési profil létrehozása](./media/ios-user-enrollment/create-profile.png)

2. Az **alapvető beállítások** lapon adja meg a profil **nevét** és **leírását** felügyeleti célból. A felhasználók nem látják ezeket az adatokat. A **Név** mező felhasználásával dinamikus csoportot hozhat létre az Azure Active Directoryban. Használja a profilnevet az enrollmentProfileName paraméter meghatározásához, hogy ezzel a regisztrációs profillal rendelhesse hozzá az eszközöket. További információk az [Azure Active Directory-alapú dinamikus csoportokról](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Alapismeretek lap](./media/ios-user-enrollment/basics-page.png)


3. Válassza a **Tovább** elemet.

4. A **Beállítások** lapon válassza az alábbi lehetőségek egyikét a **beléptetési típushoz**:

    ![Beállítások lap](./media/ios-user-enrollment/settings-page.png)

    - **Eszközök beléptetése**: a profil összes felhasználója az eszközök regisztrálását fogja használni.
    - **Felhasználó beléptetése**: a profil összes felhasználója a felhasználó beléptetését fogja használni.
    - **Döntés a felhasználó választása alapján**: a csoport összes felhasználója megadhatja, hogy melyik regisztrációs típust kívánja használni. Amikor a felhasználók regisztrálják az eszközeiket, egy lehetőség közül választhatnak, hogy az eszköz tulajdonosa és a **(vállalat) tulajdonában** **van** -e az eszköz. Ha az utóbbit választják, az eszköz regisztrálása az eszközök regisztrálásával történik. Ha a felhasználó úgy dönt, hogy az **eszköz tulajdonosa**, akkor egy másik lehetőség is gondoskodik a teljes eszköz védelméről, vagy csak a biztonságos munkavégzéssel kapcsolatos alkalmazások és adatmennyiségek biztonságáról. A végfelhasználó annak kiválasztása, hogy az eszköz tulajdonosa-e, meghatározza, hogy a regisztráció milyen típusú legyen implementálva az eszközön. Ezt a felhasználói választ az Intune-ban található eszköz tulajdonosi attribútuma is tükrözi. További információ a felhasználói élményről: [IOS-eszköz hozzáférésének beállítása a vállalati erőforrásokhoz](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
5. Válassza a **Tovább** elemet.

6. A **hozzárendelések** lapon válassza ki azokat a felhasználói csoportokat, amelyek azokat a felhasználókat tartalmazzák, amelyekhez hozzá szeretné rendelni ezt a profilt. Kiválaszthatja, hogy a profilt az összes felhasználóhoz vagy adott csoporthoz rendeli. A kiválasztott csoportokba tartozó összes felhasználó a fent kiválasztott beléptetési típust fogja használni. Az eszközbeállítások nem támogatottak a felhasználói beléptetési forgatókönyvek esetében, mert a szolgáltatás felhasználói identitásokon alapul, és nem az eszközökön. Kiválaszthatja, hogy a profilt az összes felhasználóhoz vagy adott csoporthoz rendeli.

    ![Hozzárendelések lap](./media/ios-user-enrollment/assignments-page.png)

7. Válassza a **Tovább** elemet.

8. A **felülvizsgálat és létrehozás** oldalon tekintse át a kívánt beállításokat, majd válassza a **Létrehozás** lehetőséget a profil felhasználókhoz való hozzárendeléséhez.

    ![Hozzárendelések lap](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Profil prioritása

A több regisztrációs típusú profil létrehozása után módosíthatja a prioritási sorrendet, amelyben alkalmazva vannak.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **eszközök** > **ios** > **iOS-regisztráció** > **regisztrációs típusok (előzetes verzió)** lehetőséget.
2. Húzza a listában szereplő profilokat a kívánt sorrendbe.

Bármely felhasználó profiljai közötti ütközés esetén a rendszer a magasabb prioritású profilt alkalmazza a felhasználó számára.


