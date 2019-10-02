---
title: Androidos e-mail-beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Egy konfigurációs e-mail profilok létrehozása, amelyek Exchange-kiszolgálók, és attribútumok lekérése az Azure Active Directoryból. Engedélyezze az SSL-t vagy SMIME, hitelesítse a felhasználókat tanúsítványokkal vagy felhasználónévvel/jelszóval, és szinkronizálja az e-maileket és az ütemezett adatokat az Android Samsung Knox-eszközökön Microsoft Intune használatával
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 647e1cd6925df27d42186599ad6786e866742b44
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730675"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Az e-mailek, a hitelesítés és a szinkronizálás konfigurálása az Intune-ban Android-eszközbeállítások

Ez a cikk felsorolja és leírja az Android Samsung Knox-eszközök Intune-ban való vezérlésére szolgáló különböző e-mail-beállításokat. A mobileszköz-felügyelet (MDM) megoldás részeként használja ezeket a beállításokat állítson be egy e-mail-kiszolgálót, e-mailek és más titkosítása SSL használatával.

Intune-rendszergazdaként e-mail-beállításokat hozhat létre és rendelhet hozzá az Android Samsung Knox standard-eszközökhöz.

Az Intune e-mail profiljaival kapcsolatos további információkért lásd az [e-mail-beállítások konfigurálása](email-settings-configure.md)című témakört.

## <a name="before-you-begin"></a>Előkészületek

[Eszközkonfigurációs profil létrehozása](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Levelezési kiszolgáló**: Adja meg az Exchange-kiszolgáló állomásnevét. Például írja be a következőt: `outlook.office365.com`.
- **Fiók neve**: Adja meg az e-mail-fiók megjelenítendő nevét. Ez a név jelenik meg az eszközön a felhasználók számára.
- **Username attribútum a HRE**: Ez a név a Azure Active Directory (Azure AD) által beolvasott Intune-attribútum. A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:
  - **Egyszerű felhasználónév**: Lekéri a nevet, például `user1` vagy`user1@contoso.com`
  - **Felhasználónév**: Csak a nevet kapja, például`user1`
  - **sAM-fiók neve**: A tartomány szükséges, például `domain\user1`:. a sAM-fiók neve csak Android-eszközökhöz használható.

    Ezt is adja meg:  
    - **Felhasználói tartomány neve forrás**: Válassza a **HRE** (Azure Active Directory) vagy az **Egyéni**lehetőséget.

      Ha azt választja, hogy az attribútumokat az **AAD-ből** kéri le, adja meg ezt is:
      - **A HRE felhasználói tartományneve attribútuma**: Válassza ki a felhasználó **teljes tartománynevét** vagy **NetBIOS-név** attribútumát

      Ha az **Egyéni** attribútumot választja, adja meg a következőt:
      - **Használandó egyéni tartománynév**: Adja meg azt az értéket, amelyet az Intune a tartománynévhez használ `contoso.com` , például: vagy`contoso`

- **E-mail-cím attribútum a HRE**: Ez a név az Intune által az Azure AD-től kapott e-mail-attribútum. Az Intune dinamikusan létrehozza a profil által használt e-mail-címet. A választható lehetőségek:
  - **Egyszerű felhasználónév**:  A teljes egyszerű nevet `user1@contoso.com` (például vagy `user1`) használja e-mail-címként.
  - **Elsődleges SMTP-címe**: Az elsődleges SMTP- `user1@contoso.com`címeket (például) használja az Exchange-be való bejelentkezéshez.

- **Hitelesítési módszer**: Az e-mail-profil által használandó hitelesítési módszernek válassza a **Felhasználónév és jelszó** vagy a **Tanúsítványok** lehetőséget.
  - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát az Exchange-kapcsolat hitelesítéséhez.

### <a name="security-settings"></a>Biztonsági beállítások

- **SSL**: SSL-kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikációhoz.
- **S/MIME**: Kimenő e-mailek küldése S/MIME titkosítással.
  - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát az Exchange-kapcsolat hitelesítéséhez.

### <a name="synchronization-settings"></a>Szinkronizálási beállítások

- **Szinkronizálandó e-mailek mennyisége**: Válassza ki, hogy hány nap elteltével szeretné szinkronizálni az e-maileket, vagy válassza a **korlátlan** lehetőséget az összes elérhető e-mail szinkronizálásához.
- **Szinkronizálási ütemterv**: Válassza ki az eszközöket az Exchange-kiszolgálóról szinkronizálni kívánt eszközökhöz. **Az üzenetek érkezésekor** lehetőség kiválasztásával a rendszer azonnal szinkronizálja az adatokat, amint megérkeznek, a **Manuális** beállítás esetén pedig a felhasználónak kell kezdeményeznie a szinkronizálást.

### <a name="content-sync-settings"></a>Tartalomszinkronizálási beállítások

- **Szinkronizálni kívánt tartalom típusa**: Válassza ki az eszközökön szinkronizálni kívánt tartalomtípusokat. A **nincs konfigurálva** beállítás letiltja ezt a beállítást. Ha a **nincs konfigurálva**értékre van állítva, ha egy végfelhasználó engedélyezi a szinkronizálást az eszközön, akkor a szinkronizálás újra le lesz tiltva, amikor az eszköz szinkronizál az Intune-nal, mivel a szabályzatot megerősítették. 

  A következő tartalmakat szinkronizálhatja:  
  - **Névjegyek**: Válassza az **Engedélyezés** lehetőséget, hogy a végfelhasználók szinkronizálják a névjegyeket az eszközeiket.
  - **Naptár**: Az **Engedélyezés** lehetőség kiválasztásával engedélyezheti a végfelhasználók számára, hogy szinkronizálják a naptárat az eszközeiket.
  - **Feladatok**: Az **Engedélyezés** lehetőség kiválasztásával engedélyezheti a végfelhasználók számára, hogy bármilyen feladatot szinkronizálnak az eszközeiket.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

E-mail-profilokat az [Android Enterprise-Work profil](email-settings-android-enterprise.md), az [iOS](email-settings-ios.md), a [Windows 10 és az újabb verziók](email-settings-windows-10.md), valamint a [Windows Phone-telefon 8,1](email-settings-windows-phone-8-1.md)is létrehozhat.
