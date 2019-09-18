---
title: Az Intune-regisztráció beállítása Android Enterprise teljes körűen felügyelt eszközökhöz
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan regisztrálhat androidos vállalati teljes körűen felügyelt eszközöket az Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dff37794d6c58094749821748dcc96a4f36e28a
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071629"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices-preview"></a>Az Android Enterprise teljes körűen felügyelt eszközök Intune-regisztrációjának beállítása (előzetes verzió)

Az Android Enterprise teljes körűen felügyelt eszközei olyan vállalati tulajdonú eszközök, amelyek egyetlen felhasználóhoz vannak társítva, és kizárólag munkahelyi és nem személyes használatra használatosak. A rendszergazdák kezelhetik a teljes eszközt, és a házirend-vezérlők nem érhetők el a munkahelyi profilok számára, például:
- Alkalmazások telepítésének engedélyezése csak a felügyelt Google Play áruházból.
- Felügyelt alkalmazások eltávolításának tiltása.
- Megakadályozhatja a gyári beállítások visszaállítását az eszközökön, és így tovább.

Az Intune segítségével alkalmazásokat és beállításokat telepíthet az androidos vállalati eszközökre, beleértve az Android Enterprise teljes körűen felügyelt eszközeit. Az Android Enterprise-ról az [Android Enterprise-követelmények](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)című témakörben olvashat részletesebben.

## <a name="technical-requirements"></a>Technikai követelmények

Az Android Enterprise teljes körűen felügyelt eszközeinek felügyeletéhez önálló Intune-bérlőre van szükség. A teljes körűen felügyelt eszközkezelés nem érhető el hibrid (Configuration Manager csatlakoztatott) módban vagy az örökölt Silverlight felügyeleti konzolon.

Az eszközöknek meg kell felelniük az alábbi követelményeknek, hogy az Android Enterprise teljes körűen felügyelt eszközként legyenek kezelve:

- Android 5.1 vagy újabb operációs rendszer.
- Az eszközöknek a Google Mobile Services (GM) kapcsolattal rendelkező Android-buildet kell futtatniuk. Az eszközöknek el kell érniük a GMS-t, és képesnek kell lenniük a GMS-hez való kapcsolódásra.

Ha a fenti követelmények teljesülnek, az eszköz gyártója vagy OEM-je nem korlátozza a korlátozást.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Az Android Enterprise teljes körűen felügyelt eszközkezelés beállítása

Az Android Enterprise teljes körűen felügyelt eszközkezelés beállításához kövesse az alábbi lépéseket:

1. A mobileszközök kezelésének előkészítéséhez [be kell állítania a mobileszköz-felügyeleti (Mdm) szolgáltatót, hogy **Microsoft Intune**](mdm-authority-set.md). Ezt elég egyszer beállítani, amikor először állítja be az Intune-t a mobileszközök felügyeletére.
2. Az [Intune-bérlői fiókját az Android Enterprise-fiókjával is](connect-intune-android-enterprise.md)összekapcsolhatjuk.
3. [Vállalati tulajdonú felhasználói eszközök engedélyezése](#enable-corporate-owned-user-devices)
4. [Regisztrálja a teljes körűen felügyelt eszközöket](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Vállalati tulajdonú felhasználói eszközök engedélyezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza az **eszközök** > beléptetése**Android-regisztráció** > **vállalat által birtokolt, teljes mértékben felügyelt felhasználói eszközök (előzetes verzió)**
2. A **vállalati tulajdonú felhasználói eszközök regisztrálásának engedélyezése a felhasználók**számára területen válassza az **Igen**lehetőséget.

> [!NOTE]
> Ha rendelkezik egy olyan Azure AD-beli feltételes hozzáférési szabályzattal, amely az *eszköz megfelelőségi* vezérlőként való megjelölését használja, és **minden felhőalapú alkalmazásra**, **Androidra** és **böngészőre** vonatkozik, ki kell zárnia a **Microsoft Intune** a Felhőbeli alkalmazás a szabályzatból. Ennek az az oka, hogy az Android telepítési folyamatai egy Chrome-lappal hitelesítik a felhasználókat a regisztráció során. További információt az [Azure ad feltételes hozzáférési dokumentációjában](https://docs.microsoft.com/azure/active-directory/conditional-access/)talál.

Ha a beállítás értéke **Igen**, akkor egy beléptetési tokent (egy véletlenszerű karakterláncot) és egy QR-kódot biztosít az Intune-bérlőhöz. Ez az egyszeri beléptetési jogkivonat minden felhasználó számára érvényes, és nem jár le. Az eszköz Android operációs rendszerének és verziójától függően használhatja a jogkivonatot vagy a QR-kódot a kioszk eszköz regisztrálásához.

## <a name="enroll-the-fully-managed-devices"></a>A teljes körűen felügyelt eszközök regisztrálása
Most már [regisztrálhat a teljes körűen felügyelt eszközöket](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Az előzetes verzió funkciójának szempontjai
Ez a nyilvános előzetes verzió az Android Enterprise teljes körűen felügyelt megoldásához tartozó funkciók alapkészletét tartalmazza. Azt szeretnénk, ha az előzetes verziójú funkciókkal az aktuális kommunikációs csatornákkal (például a [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)) használja a felhasználói élményt.

Ez az előzetes verzió a következő funkciókat támogatja az Android Enterprise teljes körűen felügyelt eszközökhöz:
- Eszközök beléptetése az NFC, a jogkivonat-bejegyzés, a QR-kód és a Zero Touch használatával
- Felhasználói csoportok eszköz-konfigurációja
- Alkalmazás-terjesztés és-konfiguráció felhasználói csoportokhoz


Az előzetes verziójú szolgáltatások használatakor tartsa szem előtt a következőket:
- Az előzetes verzió funkciói nem ajánlottak a kritikus fontosságú vagy éles környezetben üzemelő példányokhoz. 
- Az előzetes verziójú funkciók Microsoft Intune a termelési szabványok megvalósítására szolgálnak. Azonban nem minden Intune-funkció érhető el az Android Enterprise teljes körűen felügyelt felhasználói eszközeivel. Az előzetes verziójú funkciók egyértelműen az "(előzetes verzió)" címkével rendelkeznek az Intune-konzolon. 
- Az előzetes verziójú funkciók teljes mértékben támogatottak a szokásos Intune-támogatási csatornákon keresztül.
- Az Android Enterprise teljes körűen felügyelt, Samsung Knox Mobile-regisztrációt használó eszközök regisztrációja nem támogatott az előzetes verzióban. 
- A Intune Céges portál alkalmazás használata nem támogatott az Android Enterprise teljes körűen felügyelt eszközökön. 
- Az Intune funkciói, például a feltételes hozzáférés, az alkalmazás-védelmi szabályzatok és a tanúsítványok telepítése nem támogatott az előzetes verzióban. 
- Az összes profil vagy alkalmazás eszközcsoport általi célzása nem támogatott az előzetes verzióban. Csak a felhasználói csoportok célzása támogatott. 
- Az e-mailek, a Wi-Fi és a VPN konfigurálásához nem áll rendelkezésre első osztályú KEZELŐFELÜLET. Alkalmazás-konfigurációs házirendek használatával konfigurálhatja a támogatott alkalmazások konfigurációs beállításait.

## <a name="next-steps"></a>További lépések
- [Androidos vállalati teljes körűen felügyelt eszköz konfigurációs szabályzatok hozzáadása](device-restrictions-android-for-work.md#device-owner-only)
- [Alkalmazás-konfigurációs szabályzatok konfigurálása androidos vállalati teljes körűen felügyelt eszközökhöz](app-configuration-policies-use-android.md)

