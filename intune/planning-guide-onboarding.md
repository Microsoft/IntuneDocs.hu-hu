---
title: Intune – bevezetési fázis
titleSuffix: Microsoft Intune
description: Ez a cikk részletesen ismerteti azokat a szempontokat, amelyeket figyelembe kell venni a Microsoft Intune kizárólag felhőalapú megoldásának bevezetési folyamatánál saját környezetben.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cd9f14d48c86119acf862e2d335fe88fb2a9a1c
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799458"
---
# <a name="implement-your-microsoft-intune-plan"></a>A Microsoft Intune-terv megvalósítása

A bevezetési fázis az Intune éles környezetben való üzembe helyezéséből áll. Az implementálási folyamat során az Intune és (ha szükséges) a külső függőségek telepítése és konfigurálására kerül sor saját [használatieset-követelményei](planning-guide-requirements.md) alapján.

A következő szakasz áttekintést nyújt az Intune implementálási folyamatáról, többek között a követelményekről és az átfogó szintű feladatokról.

## <a name="intune-requirements"></a>Az Intune-ra vonatkozó követelmények

Az önálló Intune-ra vonatkozó követelmények az alábbiak:

-   Enterprise Mobility + Security- (EMS) vagy Intune-előfizetés

-   Office 365-előfizetés (Office-alkalmazásokhoz és alkalmazásvédelmi szabályzat által kezelt alkalmazásokhoz)

-   Apple APNs-tanúsítvány (iOS eszközplatform kezeléséhez)

-   Azure AD Connect (címtár-szinkronizáláshoz)

-   Exchange-hez készült Intune On-Premises Connector (feltételes hozzáférésű helyszíni Exchange-hez, ha szükséges)

-   Intune Certificate Connector (SCEP-tanúsítvány telepítéséhez, ha szükséges)

>[!TIP]
> Az Intune-nal kezelhető eszközök teljes névsorát a [támogatott eszközök](supported-devices-browsers.md) listáján tekintheti meg.

## <a name="intune-implementation-process"></a>Az Intune implementációjának folyamata

13 különböző feladatot azonosítottunk az Intune üzembe helyezéséhez. Az üzleti követelményektől, a meglévő infrastruktúrától és az eszközkezelési stratégiától függően előfordulhat, hogy az alábbi feladatok közül néhányat már elvégzett. A terv másokra nem alkalmazható.

### <a name="task-1-get-an-intune-subscription"></a>1. feladat: Intune-előfizetés vásárlása

Ahogyan azt a fenti Intune-követelmények szakaszban jeleztük, EMS- vagy Intune-előfizetésre van szüksége. Ha a szervezete még nem rendelkezik ezzel, vegye fel a kapcsolatot a Microsofttal vagy a Microsoft-fiók ügyfélszolgálatával az Enterprise Mobility + Security (EMS) vagy az Intune megvásárlásával kapcsolatban.

-   További információk a [Microsoft Intune megvásárlásával](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) kapcsolatban.

### <a name="task-2-add-office-365-subscription"></a>2. feladat: Office 365-előfizetés hozzáadása

Ez a lépés nem kötelező. Office 365-előfizetésre akkor van szüksége, ha az Exchange Online-t szeretné használni, és az Office-mobilalkalmazásokat alkalmazásvédelmi házirendekkel szeretné kezelni. Ha a szervezet még nem rendelkezik Office 365-előfizetéssel, vegye fel a kapcsolatot a Microsofttal vagy a Microsoft-fiók ügyfélszolgálatával az Office 365 megvásárlásával kapcsolatban.

-   További információk az [Office 365 megvásárlásával](https://products.office.com/business/compare-office-365-for-business-plans) kapcsolatban.

### <a name="task-3-add-users-groups-in-azure-ad"></a>3. feladat: Felhasználói csoportok hozzáadása az Azure ad-ben

Az Intune üzembe helyezésének használatieset-forgatókönyvei és a követelmények függvényében szükség lehet felhasználók vagy biztonsági csoportok hozzáadására az Active Directoryban vagy az Azure Active Directoryban. Tekintse át az Active Directory vagy az Azure Active Directory jelenlegi felhasználóit és biztonsági csoportjait, és ellenőrizze, hogy mindenben megfelelnek-e a szükségleteknek. Új felhasználók és biztonsági csoportok hozzáadásakor javasoljuk, hogy az Active Directoryban adja őket hozzá, majd az Azure Active Directory Azure AD Connect szolgáltatásával szinkronizálja őket.


-   További információk: [felhasználók és csoportok hozzáadása az Intune-ban](users-permissions-add.md).
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect--->



### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>4. feladat: Az Intune és az Office 365 felhasználói licencek hozzárendelése

Az EMS/Intune és az Office 365 bevezetésével érintett minden felhasználónak rendelkeznie kell egy hozzá rendelt licenccel. Az EMS/Intune és Office 365-licencek, a Microsoft 365 felügyeleti központban rendelhet.

-   További információ: [Intune-licencek hozzárendelése](licenses-assign.md).

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>5. feladat: Mobileszköz-kezelő szolgáltató beállítása az Intune-hoz

Mielőtt elkezdené az eszközök beállítását, konfigurálását, felügyeletét és regisztrálását az Intune-ban, először be kell állítania az Intune-t mobileszköz-kezelő szolgáltatóként.

-   További információ: [a mobileszköz-kezelő szolgáltató beállítása](mdm-authority-set.md).

### <a name="task-6-enable-device-platforms"></a>6. feladat: Eszközplatformok engedélyezése

Alapértelmezés szerint a legtöbb eszközplatform engedélyezve van, kivéve az Apple-eszközöket (iOS és Mac). Az iOS-eszközök Intune-beli regisztrálása és felügyelete előtt az eszközplatformot engedélyezni kell. Ehhez létre kell hoznia egy MDM leküldéses tanúsítványt, amelyet az Intune-hoz kell adnia.

-   További információ [az Apple-eszközök regisztrációjának engedélyezéséről](apple-mdm-push-certificate-get.md).

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>7. feladat: Használati feltételekre vonatkozó szabályzatok hozzáadása és telepítése

Az Intune támogatja használati feltételekre vonatkozó szabályzatokat. A használati feltételekre vonatkozó szabályzatokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

-   További információk: [A használati feltételekre vonatkozó szabályzatok hozzáadása és telepítése](terms-and-conditions-create.md).

### <a name="task-8-add-and-deploy-configuration-policies"></a>8. feladat: Konfigurációs szabályzatok hozzáadása és telepítése

Az Intune kétféle konfigurációs szabályzatot támogat: általános és egyéni. A konfigurációs szabályzatokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

-   További információk: [konfigurációs szabályzatok hozzáadása és telepítése](device-profiles.md).

### <a name="task-9-add-and-deploy-resource-profiles"></a>9. feladat: Adja hozzá, és erőforrás-profilok központi telepítése

Az Intune E-mail-, Wi-Fi- és VPN-profilokat támogat. A profilokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

-   További információ [a vállalati erőforrások hozzáférésének az Intune-nal való engedélyezéséről](device-profiles.md).

### <a name="task-10-add-and-deploy-apps"></a>10. feladat: Alkalmazások felvétele és telepítése

Az Intune a webes, üzletági és a nyilvános áruházból származó alkalmazások telepítését támogatja. Ezen kívül kezelhet olyan alkalmazásokat is, amelyekkel alkalmazásvédelmi szabályzatok alkalmazásával integrálva van az Intune SDK. Az alkalmazásokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

-   További információ [az alkalmazások hozzáadásáról és üzembe helyezéséről](app-management.md).

### <a name="task-11-add-and-deploy-compliance-policies"></a>11. feladat: Megfelelőségi szabályzatok hozzáadása és telepítése

Az Intune támogatja a megfelelőségi szabályzatok használatát. A megfelelőségi szabályzatokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

-   További információ: [megfelelőségi szabályzatok](device-compliance.md).

### <a name="task-12-enable-conditional-access-policies"></a>12. feladat: Feltételes hozzáférési szabályzat engedélyezése

Az Intune támogatja a feltételes hozzáférési folyamatot a helyszíni Exchange, az Exchange Online, a SharePoint Online, a Skype Vállalati online verzió és a Dynamics CRM Online esetén. A feltételes hozzáférési szabályzatokat szükség szerint engedélyezze, figyelembe véve az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket.

-   További információk a [feltételes hozzáférésről](conditional-access.md).

### <a name="task-13-enroll-devices"></a>13. feladat: Eszközök regisztrálása

Az Intune az iOS, Mac OS, Android, Windows asztali és Windows Mobile eszközplatformokat támogatja. A mobileszköz-platformokat szükség szerint regisztrálja, figyelembe véve az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket.

-   További információk: [eszközök regisztrálása](device-enrollment.md).


## <a name="next-steps"></a>További lépések

Az Intune bevezetési folyamatáról további információkat talál a [Microsoft Virtual Academy Intune-ról szóló részében](https://mva.microsoft.com/en-US/training-courses/deploying-microsoft-enterprise-mobility-suite-16408).


Útmutató az [Intune üzembe helyezésének teszteléséről és ellenőrzéséről](planning-guide-test-validation.md).
