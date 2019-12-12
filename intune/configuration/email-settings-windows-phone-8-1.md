---
title: E-mail-beállítások a Microsoft Intune-ban Windows Phone 8.1-es eszközök esetén
titleSuffix: ''
description: Útmutató az e-mail-kapcsolatok Windows Phone 8.1 rendszerű eszközökön való konfigurálásához használható Intune-beállításokhoz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 455d69328f8b70b1de73067c6290b6955df1e710
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506745"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>A Windows Phone 8.1 rendszerű eszközökre vonatkozó e-mail-profilbeállítások a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikk a Windows Phone 8.1 rendszerű eszközökhöz konfigurálható e-mail-profilbeállításokat mutatja be.


- **Az összes beállítás alkalmazása csak Windows Phone 8.1 rendszeren** – Ez a beállítás a klasszikus Intune-portálon konfigurálható. Ez a beállítás az Azure Portalon nem módosítható. Ha ez a beállítás a **Konfigurálva** értékre van állítva, a rendszer minden beállítást csak a Windows Phone 8.1 rendszerű eszközökre alkalmaz. Ha a **Nincs konfigurálva** értékre van állítva, akkor a rendszer a Windows 10 Mobile rendszerű eszközökre is alkalmazza ezeket a beállításokat.
- **E-mail-kiszolgáló** – Itt adja meg az Exchange-kiszolgáló állomásnevét.
- **Fióknév** – Adja meg az e-mail-fiók megjelenítendő nevét (ez a név lesz látható a felhasználók eszközén).
- **Felhasználónév attribútum az AAD-ből** – Ez az Active Directory (AD) vagy az Azure AD egy attribútuma, ennek alapján generálja a rendszer az e-mail-profil felhasználónevét. Válassza az **Elsődleges SMTP-cím** (például **user1@contoso.com** ) lehetőséget, vagy az **Egyszerű felhasználónév** (például **user1** vagy **user1@contoso.com** ) lehetőséget.
- **E-mail-cím attribútuma az AAD-ből** – Válassza ki, hogyan jöjjön létre a felhasználói e-mail-cím az egyes eszközökön. Ha az elsődleges SMTP-cím használatával kíván bejelentkezni az Exchange-be, válassza az **Elsődleges SMTP-cím** lehetőséget; ha e-mail-címként a teljes egyszerű felhasználónevet kívánja használni, válassza az **Egyszerű felhasználónév** lehetőséget.


## <a name="security-settings"></a>Biztonsági beállítások

- **SSL** – SSL-kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikációhoz.



## <a name="synchronization-settings"></a>Szinkronizálási beállítások

- **Szinkronizálandó e-mailek mennyisége** – Válassza ki, hogy hány napra visszamenőleg szeretné szinkronizálni az e-maileket, vagy az összes e-mail szinkronizálásához válassza a **Korlátlan** lehetőséget.
- **Szinkronizálás ütemezése** – Válassza ki azt az ütemezést, amely alapján az eszközök szinkronizálni fogják az adatokat az Exchange Serverrel. **Az üzenetek érkezésekor** lehetőség kiválasztásával a rendszer azonnal szinkronizálja az adatokat, amint megérkeznek, a **Manuális** beállítás esetén pedig a felhasználónak kell kezdeményeznie a szinkronizálást.

## <a name="content-sync-settings"></a>Tartalomszinkronizálási beállítások

- **Szinkronizálandó tartalomtípus** – Válassza ki az eszközökre szinkronizálni kívánt tartalomtípusokat:
  - **Névjegyek**
  - **Naptár**
  - **Feladatok**
