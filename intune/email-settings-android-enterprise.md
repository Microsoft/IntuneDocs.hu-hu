---
title: Az Android vállalati e-mail-beállításai a Microsoft Intuneban – Azure | Microsoft Docs
description: Hozzon létre az Exchange-kiszolgálókat használó eszköz-konfigurációs e-mail-profilokat, és kérje le az attribútumokat Azure Active Directory Engedélyezze az SSL-t vagy a SMIME, hitelesítse a felhasználókat tanúsítványokkal vagy felhasználónévvel/jelszóval, és szinkronizálja az e-maileket és az ütemezett adatokat az androidos munkahelyi profilok Microsoft Intune használatával.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e13c2dce5e8da2ce71b97de496d5234096c3b22
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "71301957"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Az androidos vállalati eszközbeállítások az e-mailek, a hitelesítés és a szinkronizálás konfigurálásához az Intune-ban

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk felsorolja és leírja az androidos vállalati eszközökön szabályozható különböző e-mail-beállításokat. A mobileszköz-felügyelet (MDM) megoldás részeként használja ezeket a beállításokat állítson be egy e-mail-kiszolgálót, e-mailek és más titkosítása SSL használatával.

Intune-rendszergazdaként e-mail-beállításokat hozhat létre és rendelhet hozzá az androidos vállalati eszközökhöz a munkahelyi profilban.

Az Intune e-mail profiljaival kapcsolatos további információkért lásd az [e-mail-beállítások konfigurálása](email-settings-configure.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

Hozzon létre egy [eszköz konfigurációs profilt](email-settings-configure.md#create-a-device-profile) (válassza ki a munkahelyi profilt), vagy hozzon létre egy [alkalmazás-konfigurációs házirendet](app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Vállalati Android

- **E-mail alkalmazás**: Válassza a **Gmail** vagy a **Nine Work** lehetőséget.
- **Levelezési kiszolgáló**: Az Exchange-kiszolgáló állomásneve. Például írja be a következőt: `outlook.office365.com`.
- **Username attribútum a HRE**: Ez a név a Azure Active Directory (Azure AD) által beolvasott Intune-attribútum. A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:

  - **Egyszerű felhasználónév**: Lekéri a nevet, például `user1` vagy`user1@contoso.com`
  - **Felhasználónév**: Csak a nevet kapja, például`user1`

- **E-mail-cím attribútum a HRE**: Ez a név az Intune által az Azure AD-től kapott e-mail-attribútum. Az Intune dinamikusan létrehozza a profil által használt e-mail-címet. A választható lehetőségek:
  - **Egyszerű felhasználónév**:  A teljes egyszerű nevet `user1@contoso.com` (például vagy `user1`) használja e-mail-címként.
  - **Elsődleges SMTP-címe**: Az elsődleges SMTP- `user1@contoso.com`címeket (például) használja az Exchange-be való bejelentkezéshez.

- **Hitelesítési módszer**: Válassza ki a **felhasználónevet és a jelszót** vagy a **tanúsítványokat** az e-mail-profil által használt hitelesítési módszerként.
  - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát az Exchange-kapcsolat hitelesítéséhez.
- **SSL**: Az **Engedélyezés** gombra kattintva SSL (SSL) kommunikációt küldhet e-mailek küldésekor, fogadásakor és az Exchange-kiszolgálóval folytatott kommunikációban.
- **Szinkronizálandó e-mailek mennyisége**: Válassza ki a szinkronizálni kívánt e-mailek időtartamát. Vagy válassza a **korlátlan** lehetőséget az összes elérhető e-mail szinkronizálásához.
- **Szinkronizálni kívánt tartalom típusa** (Csak kilenc munka): Válassza ki, hogy mely adatokat szeretné szinkronizálni az eszközökön. A választható lehetőségek:
  - **Névjegyek**: Válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók szinkronizálják a névjegyeket az eszközeiket.
  - **Naptár**: Az **Engedélyezés** lehetőség kiválasztásával engedélyezheti a végfelhasználók számára, hogy szinkronizálják a naptárat az eszközeiket.
  - **Feladatok**: Az **Engedélyezés** lehetőség kiválasztásával engedélyezheti a végfelhasználók számára, hogy bármilyen feladatot szinkronizálnak az eszközeiket.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az [Android Samsung Knox](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 és újabb rendszerű](email-settings-windows-10.md)eszközökön is létrehozhat e-mail-profilokat, valamint [Windows Phone-telefon 8,1](email-settings-windows-phone-8-1.md) -es eszközöket.
