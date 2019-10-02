---
title: E-mail-beállítások Windows 10-es eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Olyan eszközkonfigurációs e-mail-profilt hozhat létre, amely az Exchange-kiszolgálót használja, és a tulajdonságokat az Azure Active Directoryból olvassa be. SSL-t is engedélyezhet, és a Microsoft Intune használatával szinkronizálhatja az e-maileket és az ütemezéseket Windows 10-es eszközökön.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22db8f4b531d65169d1a0f2289a3221d6760ba05
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730639"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>E-mail-profilbeállítások Windows 10-et futtató eszközökön – Intune

Az e-mail-profil beállításainak használatával konfigurálja a posta alkalmazást a Windows 10 rendszerű eszközökön.

- **Levelezési kiszolgáló**: Adja meg az Exchange-kiszolgáló állomásnevét.
- **Fiók neve**: Adja meg az e-mail-fiók megjelenítendő nevét. Ez a név jelenik meg az eszközön a felhasználók számára.
- **Username attribútum a HRE**: Ez a név az Intune-ból beolvasott attribútum Azure Active Directory (HRE). A profil által használt felhasználónevet az Intune dinamikusan generálja. A választható lehetőségek:
  - **Egyszerű felhasználónév**: Lekéri a nevet, például `user1` vagy`user1@contoso.com`
  - **Elsődleges SMTP-címe**: Lekéri a nevet az e-mail cím formátumában, például:`user1@contoso.com`
  - **sAM-fiók neve**: A tartomány szükséges, például `domain\user1`:.

    Ezt is adja meg:  
    - **Felhasználói tartomány neve forrás**: Válassza a **HRE** (Azure Active Directory) vagy az **Egyéni**lehetőséget.

      Ha azt választja, hogy az attribútumokat az **AAD-ből** kéri le, adja meg ezt is:
      - **A HRE felhasználói tartományneve attribútuma**: Válassza ki a felhasználó **teljes tartománynevét** vagy **NetBIOS-név** attribútumát

      Ha az **Egyéni** attribútumot választja, adja meg a következőt:
      - **Használandó egyéni tartománynév**: Adja meg azt az értéket, amelyet az Intune a tartománynévhez használ `contoso.com` , például: vagy`contoso`

- **E-mail-cím attribútum a HRE**: Válassza ki, hogyan hozza létre a rendszer a felhasználó e-mail címét. Ha e-mail-címként a teljes egyszerű felhasználónevet szeretné használni, válassza az **Egyszerű felhasználónév** (`user1@contoso.com` vagy `user1`) lehetőséget, vagy az **Elsődleges SMTP-cím** (`user1@contoso.com`) lehetőséget, ha az elsődleges SMTP-címet szeretné használni az Exchange-be való bejelentkezéshez.

## <a name="security-settings"></a>Biztonsági beállítások

- **SSL**: SSL-kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikációhoz.

## <a name="synchronization-settings"></a>Szinkronizálási beállítások

- **Szinkronizálandó e-mailek mennyisége**: Válassza ki, hogy hány nap elteltével szeretné szinkronizálni az e-maileket. Vagy válassza a **Korlátlan** lehetőséget az összes elérhető e-mail szinkronizálása.
- **Szinkronizálási ütemterv**: Válassza ki az adatokat az Exchange-kiszolgálóról szinkronizálni kívánt eszközökre vonatkozóan, az **üzenetek érkezésekor**lehetőség kiválasztásával, amely azonnal szinkronizálja az adatokat, amint megérkezik, vagy **manuálisan**, ahol az eszköz felhasználójának el kell indítania a szinkronizálást.

## <a name="content-sync-settings"></a>Tartalomszinkronizálási beállítások

- **Szinkronizálni kívánt tartalom típusa**: Válassza ki az eszközökre szinkronizálni kívánt tartalomtípusokat:
  - **Névjegyek**
  - **Naptár**
  - **Feladatok**

## <a name="next-steps"></a>További lépések
[E-mail-beállítások konfigurálása az Intune-ban](../email-settings-configure.md)
