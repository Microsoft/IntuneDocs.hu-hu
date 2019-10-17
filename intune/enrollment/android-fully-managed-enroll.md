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
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 755aefb955c2d30652434f2bd2e91981145fc56f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505591"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Az Android Enterprise teljes körűen felügyelt eszközök Intune-regisztrációjának beállítása 

Az Android Enterprise teljes körűen felügyelt eszközei olyan vállalati tulajdonú eszközök, amelyek egyetlen felhasználóhoz vannak társítva, és kizárólag munkahelyi és nem személyes használatra használatosak. A rendszergazdák kezelhetik a teljes eszközt, és a házirend-vezérlők nem érhetők el a munkahelyi profilok számára, például:
- Alkalmazások telepítésének engedélyezése csak a felügyelt Google Play áruházból.
- Felügyelt alkalmazások eltávolításának tiltása.
- Megakadályozhatja a gyári beállítások visszaállítását az eszközökön, és így tovább.

Az Intune segítségével alkalmazásokat és beállításokat telepíthet az androidos vállalati eszközökre, beleértve az Android Enterprise teljes körűen felügyelt eszközeit. Az Android Enterprise-ról az [Android Enterprise-követelmények](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)című témakörben olvashat részletesebben.

## <a name="technical-requirements"></a>Technikai követelmények

Az Android Enterprise teljes körűen felügyelt eszközeinek felügyeletéhez önálló Intune-bérlőre van szükség. A teljes körűen felügyelt eszközkezelés nem érhető el hibrid (Configuration Manager csatlakoztatott) módban vagy az örökölt Silverlight felügyeleti konzolon.

Az eszközöknek meg kell felelniük az alábbi követelményeknek, hogy az Android Enterprise teljes körűen felügyelt eszközként legyenek kezelve:

- Android operációs rendszer 6,0-es vagy újabb verziója.
- Az eszközöknek a Google Mobile Services (GM) kapcsolattal rendelkező Android-buildet kell futtatniuk. Az eszközöknek el kell érniük a GMS-t, és képesnek kell lenniük a GMS-hez való kapcsolódásra.

Ha a fenti követelmények teljesülnek, az eszköz gyártója vagy OEM-je nem korlátozza a korlátozást.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Az Android Enterprise teljes körűen felügyelt eszközkezelés beállítása

Az Android Enterprise teljes körűen felügyelt eszközkezelés beállításához kövesse az alábbi lépéseket:

1. A mobileszközök kezelésének előkészítéséhez [be kell állítania a mobileszköz-felügyeleti (Mdm) szolgáltatót, hogy **Microsoft Intune**](../fundamentals/mdm-authority-set.md). Ezt elég egyszer beállítani, amikor először állítja be az Intune-t a mobileszközök felügyeletére.
2. Az [Intune-bérlői fiókját az Android Enterprise-fiókjával is összekapcsolhatjuk](connect-intune-android-enterprise.md).
3. [Vállalati tulajdonú felhasználói eszközök engedélyezése](#enable-corporate-owned-user-devices)
4. [Regisztrálja a teljes körűen felügyelt eszközöket](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Vállalati tulajdonú felhasználói eszközök engedélyezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza az **eszközök beléptetése** > **Android-regisztráció** > **vállalat által birtokolt, teljes körűen felügyelt felhasználói eszközöket**.
2. A **vállalati tulajdonú felhasználói eszközök regisztrálásának engedélyezése a felhasználók**számára területen válassza az **Igen**lehetőséget.

> [!NOTE]
> Ha rendelkezik egy olyan Azure AD-beli feltételes hozzáférési szabályzattal, amely az *eszköz megfelelőségi vezérlőként való megjelölését* használja, és **minden felhőalapú alkalmazásra**, **Androidra** és **böngészőre** vonatkozik, ki kell zárnia a **Microsoft Intune** a Felhőbeli alkalmazás a szabályzatból. Ennek az az oka, hogy az Android telepítési folyamatai egy Chrome-lappal hitelesítik a felhasználókat a regisztráció során. További információt az [Azure ad feltételes hozzáférési dokumentációjában](https://docs.microsoft.com/azure/active-directory/conditional-access/)talál.

Ha a beállítás értéke **Igen**, akkor egy beléptetési tokent (egy véletlenszerű karakterláncot) és egy QR-kódot biztosít az Intune-bérlőhöz. Ez az egyszeri beléptetési jogkivonat minden felhasználó számára érvényes, és nem jár le. Az eszköz Android operációs rendszertől és verziójától függően az eszköz regisztrálása a jogkivonat vagy a QR-kód használatával végezhető el.

## <a name="enroll-the-fully-managed-devices"></a>A teljes körűen felügyelt eszközök regisztrálása
Most már [regisztrálhat a teljes körűen felügyelt eszközöket](android-dedicated-devices-fully-managed-enroll.md).

## <a name="next-steps"></a>További lépések
- [Androidos vállalati teljes körűen felügyelt eszköz konfigurációs szabályzatok hozzáadása](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [Alkalmazás-konfigurációs szabályzatok konfigurálása androidos vállalati teljes körűen felügyelt eszközökhöz](../apps/app-configuration-policies-use-android.md)

