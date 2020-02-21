---
title: Az Android vállalati e-mail-beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Hozzon létre az Exchange-kiszolgálókat használó eszköz-konfigurációs e-mail-profilokat, és kérje le az attribútumokat Azure Active Directory Engedélyezze az SSL-t vagy a SMIME, hitelesítse a felhasználókat tanúsítványokkal vagy felhasználónévvel/jelszóval, és szinkronizálja az e-maileket és az ütemezett adatokat az androidos munkahelyi profilok Microsoft Intune használatával.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 978ddf279dc221a56fddaf99da4dbb2377a93c24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511153"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Az androidos vállalati eszközbeállítások az e-mailek, a hitelesítés és a szinkronizálás konfigurálásához az Intune-ban



Ez a cikk felsorolja és leírja az androidos vállalati eszközökön szabályozható különböző e-mail-beállításokat. A mobileszköz-felügyelet (MDM) megoldás részeként használja ezeket a beállításokat állítson be egy e-mail-kiszolgálót, e-mailek és más titkosítása SSL használatával.

Intune-rendszergazdaként e-mail-beállításokat hozhat létre és rendelhet hozzá az androidos vállalati eszközökhöz a munkahelyi profilban.

Az Intune e-mail profiljaival kapcsolatos további információkért lásd az [e-mail-beállítások konfigurálása](email-settings-configure.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

Hozzon létre egy [eszköz konfigurációs profilt](email-settings-configure.md#create-a-device-profile) (válassza ki a munkahelyi profilt), vagy hozzon létre egy [alkalmazás-konfigurációs házirendet](../apps/app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Vállalati Android

- **Levelezőalkalmazás**: Válassza a **Gmail** vagy a **Nine Work** lehetőséget
- **E-mail-kiszolgáló**: Itt adja meg az Exchange-kiszolgáló állomásnevét. Például írja be a következőt: `outlook.office365.com`.
- **Felhasználói név attribútum az AAD-ből**: Ez a név az Intune által az Azure Active Directoryből (Azure AD) lekért attribútum. A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:

  - **Egyszerű felhasználónév**: A nevet, például `user1` vagy `user1@contoso.com` kéri le.
  - **Felhasználónév**: Csak a nevet olvassa be, például `user1`

- E **-mail-cím attribútum a HRE-ből**: Ez a név az Intune által az Azure ad-től kapott e-mail-attribútum. Az Intune dinamikusan létrehozza a profil által használt e-mail-címet. A választható lehetőségek:
  - **Egyszerű felhasználónév**: a teljes egyszerű nevet (például `user1@contoso.com` vagy `user1`) használja e-mail-címként.
  - **Elsődleges SMTP-címe**: az elsődleges SMTP-címeket (például `user1@contoso.com`) használja az Exchange-be való bejelentkezéshez.

- **Hitelesítési módszer**: válassza a **Felhasználónév és jelszó** vagy a **tanúsítványok** lehetőséget az e-mail profil által használt hitelesítési módszerként.
  - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát az Exchange-kapcsolat hitelesítéséhez.
- **SSL**: válassza az **Engedélyezés** lehetőséget, ha az e-mailek küldésekor, fogadásakor és az Exchange-kiszolgálóval való kommunikációnál SSL (SSL) kommunikációt szeretne használni.
- **Szinkronizálandó e-mailek mennyisége**: válassza ki a szinkronizálni kívánt e-mailek időtartamát. Vagy válassza a **korlátlan** lehetőséget az összes elérhető e-mail szinkronizálásához.
- **Szinkronizálandó tartalomtípus** (csak kilences munka esetén): válassza ki, hogy mely adatokat kívánja szinkronizálni az eszközökön. A választható lehetőségek:
  - **Névjegyek**: válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók szinkronizálják a névjegyeket az eszközeiket.
  - **Naptár**: válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók szinkronizálják a naptárt az eszközeiket.
  - **Feladatok**: válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók bármilyen feladatot szinkronizálják az eszközeiket.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

E-mail-profilokat is létrehozhat [Android Samsung Knox](email-settings-android.md), [iOS/iPadOS](email-settings-ios.md), [Windows 10 és újabb rendszerű](email-settings-windows-10.md)eszközökhöz, valamint [Windows Phone-telefon 8,1](email-settings-windows-phone-8-1.md) -es eszközöket.
