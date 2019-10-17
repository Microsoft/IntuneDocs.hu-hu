---
title: Androidos e-mail-beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Hozzon létre egy eszköz-konfigurációs e-mail-profilt, amely Exchange-kiszolgálókat használ, és adja meg az attribútumokat Azure Active Directory. Engedélyezze az SSL-t vagy SMIME, hitelesítse a felhasználókat tanúsítványokkal vagy felhasználónévvel/jelszóval, és szinkronizálja az e-maileket és az ütemezett adatokat az Android Samsung Knox-eszközökön Microsoft Intune használatával
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43a2b00ae824656621c8a586e41ba6425c69ed40
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506767"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Az e-mailek, a hitelesítés és a szinkronizálás konfigurálása az Intune-ban Android-eszközbeállítások

Ez a cikk felsorolja és leírja az Android Samsung Knox-eszközök Intune-ban való vezérlésére szolgáló különböző e-mail-beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal konfigurálhatja az e-mail-kiszolgálókat, az SSL használatával titkosíthatja az e-maileket, és egyéb műveleteket is elvégezheti.

Intune-rendszergazdaként e-mail-beállításokat hozhat létre és rendelhet hozzá az Android Samsung Knox standard-eszközökhöz.

Az Intune e-mail profiljaival kapcsolatos további információkért lásd az [e-mail-beállítások konfigurálása](email-settings-configure.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **E-mail-kiszolgáló**: Itt adja meg az Exchange-kiszolgáló állomásnevét. Például írja be a következőt: `outlook.office365.com`.
- **Fiók neve**: Adja meg az e-mail-fiók megjelenítendő nevét. Ez a név jelenik meg az eszközön a felhasználók számára.
- **Felhasználói név attribútum az AAD-ből**: Ez a név az Intune által az Azure Active Directoryből (Azure AD) lekért attribútum. A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:
  - **Egyszerű felhasználónév**: A nevet, például `user1` vagy `user1@contoso.com` kéri le.
  - **Felhasználónév**: Csak a nevet olvassa be, például `user1`
  - **SAM-fiók neve**: Tartomány szükséges hozzá, például `domain\user1`. a sAM-fiók neve csak Android-eszközökhöz használható.

    Ezt is adja meg:  
    - **Felhasználói tartománynév forrása**: Válassza az **AAD** (Azure Active Directory) vagy az **Egyéni** lehetőséget.

      Ha azt választja, hogy az attribútumokat az **AAD-ből** kéri le, adja meg ezt is:
      - **Felhasználói tartománynév attribútuma az AAD-ból**: Választhatja a felhasználóhoz tartozó **Teljes tartománynév** vagy a **NetBIOS-név** attribútum lehetőséget

      Ha az **Egyéni** attribútumot választja, adja meg a következőt:
      - **Használandó egyéni tartománynév**: Adja meg az Intune által a tartománynévhez használt értéket, például `contoso.com` vagy `contoso`

- E **-mail-cím attribútum a HRE-ből**: Ez a név az Intune által az Azure ad-től kapott e-mail-attribútum. Az Intune dinamikusan létrehozza a profil által használt e-mail-címet. A választható lehetőségek:
  - **Egyszerű felhasználónév**: a teljes egyszerű nevet (például `user1@contoso.com` vagy `user1`) használja e-mail-címként.
  - **Elsődleges SMTP-címe**: az elsődleges SMTP-címeket (például `user1@contoso.com`) használja az Exchange-be való bejelentkezéshez.

- **Hitelesítési módszer**: Az e-mail-profil által használandó hitelesítési módszernek válassza a **Felhasználónév és jelszó** vagy a **Tanúsítványok** lehetőséget.
  - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát az Exchange-kapcsolat hitelesítéséhez.

### <a name="security-settings"></a>Biztonsági beállítások

- **SSL**: SSL-kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikációhoz.
- **S/MIME**: Kimenő e-mailek küldése S/MIME titkosítással.
  - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát az Exchange-kapcsolat hitelesítéséhez.

### <a name="synchronization-settings"></a>Szinkronizálási beállítások

- **Szinkronizálandó e-mailek mennyisége**: Válassza ki, hogy hány napra visszamenőleg szeretné szinkronizálni az e-maileket, vagy az összes e-mail szinkronizálásához válassza a **Korlátlan** lehetőséget.
- **Szinkronizálás ütemezése**: Válassza ki azt az ütemezést, amely alapján az eszközök szinkronizálni fogják az adatokat az Exchange-kiszolgálóval. **Az üzenetek érkezésekor** lehetőség kiválasztásával a rendszer azonnal szinkronizálja az adatokat, amint megérkeznek, a **Manuális** beállítás esetén pedig a felhasználónak kell kezdeményeznie a szinkronizálást.

### <a name="content-sync-settings"></a>Tartalomszinkronizálási beállítások

- **Szinkronizálandó tartalomtípus**: válassza ki az eszközökön szinkronizálni kívánt tartalomtípusokat. A **nincs konfigurálva** beállítás letiltja ezt a beállítást. Ha a **nincs konfigurálva**értékre van állítva, ha egy végfelhasználó engedélyezi a szinkronizálást az eszközön, akkor a szinkronizálás újra le lesz tiltva, amikor az eszköz szinkronizál az Intune-nal, mivel a szabályzatot megerősítették. 

  A következő tartalmakat szinkronizálhatja:  
  - **Névjegyek**: válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók szinkronizálják a névjegyeket az eszközeiket.
  - **Naptár**: válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók szinkronizálják a naptárt az eszközeiket.
  - **Feladatok**: válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók bármilyen feladatot szinkronizálják az eszközeiket.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

E-mail-profilokat az [Android Enterprise-Work profil](email-settings-android-enterprise.md), az [iOS](email-settings-ios.md), a [Windows 10 és az újabb verziók](email-settings-windows-10.md), valamint a [Windows Phone-telefon 8,1](email-settings-windows-phone-8-1.md)is létrehozhat.
