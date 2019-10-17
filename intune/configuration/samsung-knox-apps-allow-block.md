---
title: Microsoft Intune-szabályzat alkalmazások engedélyezésére és letiltására Samsung Knox-eszközökön
titleSuffix: ''
description: Egyéni profil létrehozása alkalmazások engedélyezéséhez és letiltásához Samsung Knox Standard-eszközökön.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: afaee427b593cfaed957279b520765242a1aacd3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506649"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Alkalmazások engedélyezése és letiltása egyéni szabályzattal Samsung Knox Standard-eszközökön a Microsoft Intune-ban 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ennek a cikknek az eljárásaival elkészíthet egy egyéni Microsoft Intune-szabályzatot, amellyel az alábbiak egyikét hozhatja létre:

- Az eszközön nem futtatható alkalmazások listája. A listában szereplő alkalmazások le lesznek tiltva, és nem futtathatóak még akkor sem, ha a szabályzat létrehozása előtt lettek telepítve.
- Azon alkalmazások listája, amelyek telepítése engedélyezett az eszköz felhasználói számára a Google Play áruházból. Csak a listán szereplő alkalmazások telepíthetők. Az áruházból más alkalmazások nem telepíthetők.

Ezek a beállítások kizárólag a Samsung Knox Standard rendszerű eszközökön használhatók.

## <a name="create-an-allowed-or-blocked-app-list"></a>Az engedélyezett vagy tiltott alkalmazások listájának létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközkonfiguráció** lehetőséget.
2. Az **Eszközkonfiguráció** panelen válassza a **Kezelés** > **Profilok** lehetőséget.
2. A profilok listáját mutató panelen válassza a **Profil létrehozása** lehetőséget.
3. A **Profil létrehozása** panelen írja be az eszközprofilra vonatkozó **Név** és **Leírás** (nem kötelező) szövegét.
2. Válassza az **Android** lehetőséget a **Platform** beállításnál, valamint az **Egyéni** lehetőséget a **Profiltípus** beállításnál.
3. Kattintson a **Beállítások** elemre.
3. Az **Egyéni OMA-URI beállítások** panelen válassza a **Hozzáadás** lehetőséget.
4. Az **OMA-URI beállítás hozzáadása vagy szerkesztése** párbeszédpanelen adja meg a következő beállításokat:

   Az eszközön nem futtatható alkalmazások listájához:

   - **Név** – Írja be a következőt: **PreventStartPackages**.
   - **Leírás** – Igény esetén beírhat egy leírást. Például: „Nem futtatható alkalmazások listája”.
   - **Adattípus** – A legördülő listából válassza a **Sztring** elemet.
   - **OMA-URI** – Írja be a következőt: **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   - **Érték** – Adja meg az engedélyezni kívánt alkalmazáscsomagok nevének listáját. Elválasztóként használhatja a **; : ,** vagy a **|** karaktereket. (Például csomag1;csomag2;)

   Azon alkalmazások listájához, amelyek telepítése engedélyezett a felhasználók számára a Google Play áruházból, miközben minden más alkalmazás le van tiltva:
   - **Név** – Írja be a következőt: **AllowInstallPackages**.
   - **Leírás** – Igény esetén megadhat egy leírást. Például: „A Google Play áruházból telepíthető alkalmazások listája”.
   - **Adattípus** – A legördülő listából válassza a **Sztring** elemet.
   - **OMA-URI** – Írja be a következőt: **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **Érték** – Adja meg az engedélyezni kívánt alkalmazáscsomagok nevének listáját. Elválasztóként használhatja a **; : ,** vagy a **|** karaktereket. (Például csomag1;csomag2;)

4. Kattintson az **OK** gombra, majd a **Profil létrehozása** panelen válassza a **Létrehozás** lehetőséget.

>[!TIP]
> Az alkalmazás csomagazonosítóját úgy tudja megtalálni, hogy a Google Play áruházban megkeresi az alkalmazás oldalát. A csomagazonosítót az alkalmazáscsomag URL-címe tartalmazza. Például a Microsoft Word alkalmazás azonosítója **com.microsoft.office.word**.

Amikor az egyes megcélzott eszközök legközelebb bejelentkeznek, az alkalmazásbeállítások érvénybe lépnek.


<!---## Assign the custom profile--->
