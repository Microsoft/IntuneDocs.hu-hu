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
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1cdfc7d42d3bffe1abe21deddfe146af953b150a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514948"
---
# <a name="implement-your-microsoft-intune-plan"></a>A Microsoft Intune-terv megvalósítása

A bevezetési fázis az Intune éles környezetben való üzembe helyezéséből áll. Az implementálási folyamat során az Intune és (ha szükséges) a külső függőségek telepítése és konfigurálására kerül sor saját [használatieset-követelményei](planning-guide-requirements.md) alapján.

A következő szakasz áttekintést nyújt az Intune implementálási folyamatáról, többek között a követelményekről és az átfogó szintű feladatokról.

## <a name="intune-requirements"></a>Az Intune-ra vonatkozó követelmények

Az önálló Intune-ra vonatkozó követelmények az alábbiak:

- Enterprise Mobility + Security- (EMS) vagy Intune-előfizetés

- Office 365-előfizetés (Office-alkalmazásokhoz és alkalmazásvédelmi szabályzat által kezelt alkalmazásokhoz)

- Apple APNs-tanúsítvány (az iOS/iPadOS-eszközök kezelésének engedélyezéséhez)

- Azure AD Connect (címtár-szinkronizáláshoz)

- Helyszíni Intune-összekötő Exchange-hez (a helyszíni Exchange-hez való feltételes hozzáféréshez, ha szükséges)

- Intune Certificate Connector (SCEP-tanúsítvány telepítéséhez, ha szükséges)

>[!TIP]
> Az Intune-nal kezelhető eszközök teljes névsorát a [támogatott eszközök](supported-devices-browsers.md) listáján tekintheti meg.

## <a name="intune-implementation-process"></a>Az Intune implementációjának folyamata

13 különböző feladatot azonosítottunk az Intune üzembe helyezéséhez. Az üzleti követelményektől, a meglévő infrastruktúrától és az eszközkezelési stratégiától függően előfordulhat, hogy az alábbi feladatok közül néhányat már elvégzett. A terv másokra nem alkalmazható.

### <a name="task-1-get-an-intune-subscription"></a>1\. feladat: Intune-előfizetés vásárlása

Ahogyan azt a fenti Intune-követelmények szakaszban jeleztük, EMS- vagy Intune-előfizetésre van szüksége. Ha a szervezete még nem rendelkezik ezzel, vegye fel a kapcsolatot a Microsofttal vagy a Microsoft-fiók ügyfélszolgálatával az Enterprise Mobility + Security (EMS) vagy az Intune megvásárlásával kapcsolatban.

- További információk a [Microsoft Intune megvásárlásával](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) kapcsolatban.

### <a name="task-2-add-office-365-subscription"></a>2\. feladat: Office 365-előfizetés hozzáadása

Ez a lépés nem kötelező. Office 365-előfizetésre akkor van szüksége, ha az Exchange Online-t szeretné használni, és az Office-mobilalkalmazásokat alkalmazásvédelmi házirendekkel szeretné kezelni. Ha a szervezet még nem rendelkezik Office 365-előfizetéssel, vegye fel a kapcsolatot a Microsofttal vagy a Microsoft-fiók ügyfélszolgálatával az Office 365 megvásárlásával kapcsolatban.

- További információk az [Office 365 megvásárlásával](https://products.office.com/business/compare-office-365-for-business-plans) kapcsolatban.

### <a name="task-3-add-users-groups-in-azure-ad"></a>3\. feladat: felhasználói csoportok hozzáadása az Azure AD-ben

Az Intune üzembe helyezésének használatieset-forgatókönyvei és a követelmények függvényében szükség lehet felhasználók vagy biztonsági csoportok hozzáadására az Active Directoryban vagy az Azure Active Directoryban. Tekintse át az Active Directory vagy az Azure Active Directory jelenlegi felhasználóit és biztonsági csoportjait, és ellenőrizze, hogy mindenben megfelelnek-e a szükségleteknek. Új felhasználók és biztonsági csoportok hozzáadásakor javasoljuk, hogy az Active Directoryban adja őket hozzá, majd az Azure Active Directory Azure AD Connect szolgáltatásával szinkronizálja őket.

- További információk: [felhasználók és csoportok hozzáadása az Intune-ban](users-add.md).
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect--->


### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>4\. feladat: Intune és Office 365 felhasználói licencek hozzárendelése

Az EMS/Intune és az Office 365 bevezetésével érintett minden felhasználónak rendelkeznie kell egy hozzá rendelt licenccel. Az EMS/Intune és az Office 365-licencek hozzárendelését a Microsoft 365 felügyeleti központban végezheti el.

- További információ: [Intune-licencek hozzárendelése](licenses-assign.md).

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>5\. feladat: az Intune beállítása mobileszköz-kezelő szolgáltatóként

Mielőtt elkezdené az eszközök beállítását, konfigurálását, felügyeletét és regisztrálását az Intune-ban, először be kell állítania az Intune-t mobileszköz-kezelő szolgáltatóként.

- További információ: [a mobileszköz-kezelő szolgáltató beállítása](mdm-authority-set.md).

### <a name="task-6-enable-device-platforms"></a>6\. feladat: eszközplatformok engedélyezése

Alapértelmezés szerint a legtöbb eszköz-platform engedélyezve van az Apple-eszközök kivételével (iOS/iPadOS és Mac). Az iOS/iPadOS-eszközök Intune-ban való regisztrálása és kezelése előtt engedélyezni kell az eszköz platformját. Ehhez létre kell hoznia egy MDM leküldéses tanúsítványt, amelyet az Intune-hoz kell adnia.

- További információ [az Apple-eszközök regisztrációjának engedélyezéséről](../enrollment/apple-mdm-push-certificate-get.md).

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>7\. feladat: használati feltételekre vonatkozó szabályzatok hozzáadása és telepítése

Az Intune támogatja használati feltételekre vonatkozó szabályzatokat. A használati feltételekre vonatkozó szabályzatokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

- További információk: [A használati feltételekre vonatkozó szabályzatok hozzáadása és telepítése](../enrollment/terms-and-conditions-create.md).

### <a name="task-8-add-and-deploy-configuration-policies"></a>8\. feladat: konfigurációs szabályzatok hozzáadása és telepítése

Az Intune kétféle konfigurációs szabályzatot támogat: általános és egyéni. A konfigurációs szabályzatokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

- További információk: [konfigurációs szabályzatok hozzáadása és telepítése](../configuration/device-profiles.md).

### <a name="task-9-add-and-deploy-resource-profiles"></a>9\. feladat: erőforrásprofilok hozzáadása és telepítése

Az Intune E-mail-, Wi-Fi- és VPN-profilokat támogat. A profilokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

- További információ [a vállalati erőforrások hozzáférésének az Intune-nal való engedélyezéséről](../configuration/device-profiles.md).

### <a name="task-10-add-and-deploy-apps"></a>10. feladat: alkalmazások hozzáadása és telepítése

Az Intune a webes, üzletági és a nyilvános áruházból származó alkalmazások telepítését támogatja. Ezen kívül kezelhet olyan alkalmazásokat is, amelyekkel alkalmazásvédelmi szabályzatok alkalmazásával integrálva van az Intune SDK. Az alkalmazásokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

- További információ [az alkalmazások hozzáadásáról és üzembe helyezéséről](../apps/app-management.md).

### <a name="task-11-add-and-deploy-compliance-policies"></a>11. feladat: megfelelőségi szabályzatok hozzáadása és telepítése

Az Intune támogatja a megfelelőségi szabályzatok használatát. A megfelelőségi szabályzatokat szükség szerint adja hozzá, és az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket figyelembe véve telepítse őket a célcsoportoknál.

- További információ: [megfelelőségi szabályzatok](../protect/device-compliance-get-started.md).

### <a name="task-12-enable-conditional-access-policies"></a>12. feladat: feltételes hozzáférési szabályzatok engedélyezése

Az Intune támogatja a feltételes hozzáférést az Exchange Online-hoz, a helyszíni Exchange-hez, a SharePoint Online-hoz, a Skype vállalati online verzióhoz és a Dynamics CRM Online-hoz. A feltételes hozzáférést az Intune üzembe helyezési használati eseteinek és követelményeinek megfelelően engedélyezheti és konfigurálhatja.

- További tudnivalók [a feltételes hozzáférésről](../protect/conditional-access.md)

### <a name="task-13-enroll-devices"></a>13. feladat: eszközök regisztrálása

Az Intune az iOS/iPadOS, a Mac OS, az Android, a Windows Desktop és a Windows Mobile Device platformokat támogatja. A mobileszköz-platformokat szükség szerint regisztrálja, figyelembe véve az Intune üzembe helyezésének használatieset-forgatókönyveit és a követelményeket.

- További információk: [eszközök regisztrálása](../enrollment/device-enrollment.md).


## <a name="next-steps"></a>További lépések
Útmutató az [Intune üzembe helyezésének teszteléséről és ellenőrzéséről](planning-guide-test-validation.md).
