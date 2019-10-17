---
title: Egyéni alkalmazásonkénti Androidos VPN-profil
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan hozhat létre alkalmazásonkénti VPN-profilt a Microsoft Intune-nal felügyelt Android-eszközökhöz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/05/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 524f4cd77d85460940a885bc7950e7d476097e72
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72496127"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Alkalmazásonkénti VPN-profil létrehozása androidos eszközökhöz egyéni Microsoft Intune-profillal

[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Az Intune által felügyelt Android 5.0-s és újabb rendszerű eszközökhöz alkalmazásonkénti VPN-profilt hozhat létre. Először hozzon létre egy olyan VPN-profit, amely a Pulse Secure vagy a Citrix kapcsolattípust használja. Ezután hozzon létre egy olyan egyéni szabályzatot, amely a VPN-profilt meghatározott alkalmazásokkal társítja.

Miután hozzárendeli a szabályzatot az Android rendszerű eszközhöz vagy felhasználócsoportokhoz, a felhasználóknak el kell indítaniuk a PulseSecure vagy a Citrix VPN-ügyfelet. A VPN-ügyfél ezután csak a megadott alkalmazások adatforgalma számára engedélyezi a nyitott VPN-kapcsolat használatát.

> [!NOTE]
>
> Ez a profil csak a Pulse Secure és a Citrix kapcsolattípust támogatja.


## <a name="step-1-create-a-vpn-profile"></a>1\. lépés: VPN-profil létrehozása


1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközkonfiguráció** lehetőséget.
2. Az **Eszközkonfiguráció** panel **Kezelés** területén válassza a **Profilok** lehetőséget.
2. A profilok listáját mutató panelen válassza a **Profil létrehozása** lehetőséget.
3. A **Profil létrehozása** panelen adja meg az egyéni VPN-profil **Nevét** és **Leírását** (nem kötelező).
4. A **Platform** legördülő listájában válassza az **Android** lehetőséget.
5. A **Profil típusa** legördülő listában válassza a **VPN** lehetőséget.
3. Válassza a **Beállítások** > **Konfigurálás** lehetőséget, majd konfigurálja a VPN-profilt a [VPN-beállítások konfigurálása](vpn-settings-configure.md) és az [Intune VPN-beállítások androidos eszközökhöz](vpn-settings-android.md) részekben ismertetett beállítások alapján.

Jegyezze le a VPN-profil létrehozásakor megadott **Kapcsolat neve** értéket. Erre szükség lesz a következő lépésben. Például: **AlkVpnProfil**.

## <a name="step-2-create-a-custom-configuration-policy"></a>2\. lépés: Egyéni konfigurációs szabályzat létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** panelen válassza az **Eszközkonfiguráció** lehetőséget.
2. Az **Eszközkonfiguráció** panel **Kezelés** területén válassza a **Profilok** lehetőséget.
3. A profilok panelen kattintson a **Profil létrehozása** lehetőségre.
4. A **Profil létrehozása** panelen adja meg az egyéni profil **Nevét** és **Leírását**.
5. A **Platform** legördülő listájában válassza az **Android** lehetőséget.
6. A **Profil típusa** legördülő listában válassza az **Egyéni** lehetőséget.
7. Válassza a **Beállítások** > **Konfigurálás** lehetőséget.
3. Az **Egyéni OMA-URI beállítások** panelen válassza a **Hozzáadás** lehetőséget.
    - Adja meg a beállítás nevét.
    - Az **OMA-URI** mezőbe írja be a következő sztringet: **./Vendor/MSFT/VPN/Profile/*Név*/PackageList**, ahol a *Név* a kapcsolatnak az 1. lépésben feljegyzett neve. A jelen példában a sztring a következő lenne: **./Vendor/MSFT/VPN/Profile/AlkVpnProfil/PackageList**.
    - Az **Adattípus** mezőben válassza a **Sztring** lehetőséget.
    - Az **Érték** területen adja meg azoknak a csomagoknak a pontosvesszővel tagolt listáját, amelyeket a profilhoz társít. Ha például azt szeretné, hogy az Excel és a Google Chrome böngésző VPN-kapcsolatot használjon, írja be a következőt: **com.microsoft.office.excel;com.android.chrome**.

![Példa Android rendszerű, alkalmazásonkénti VPN-hez létrehozott egyéni szabályzatra](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Az alkalmazáslista Blacklist (Letiltott) vagy Whitelist (Engedélyezett) értékre állítása (nem kötelező)
  A **BLACKLIST** (LETILTOTT) érték kiválasztásával megadhatja azoknak az alkalmazásoknak a listáját, amelyek *nem* használhatják a VPN-kapcsolatot. Minden más alkalmazás VPN-kapcsolaton keresztül fog csatlakozni az internethez.
Másik megoldásként használhatja a **WHITELIST** (ENGEDÉLYEZETT) értéket, és megadhatja azon alkalmazások listáját, amelyek *használhatják* a VPN-kapcsolatot. A listán nem szereplő alkalmazások nem csatlakozhatnak az internethez a VPN-kapcsolaton keresztül.
  1. Az **Egyéni OMA-URI beállítások** panelen válassza a **Hozzáadás** lehetőséget.
  2. Adja meg a beállítás nevét.
  3. Az **OMA-URI** mezőbe írja be a következő sztringet: **./Vendor/MSFT/VPN/Profile/*Név*/Mode**, ahol a *Név* az 1. lépésben feljegyzett VPN-profil neve. A fenti példában a sztring a következő lenne: **./Vendor/MSFT/VPN/Profile/AlkVpnProfil/Mode**.
  4. Az **Adattípus** mezőben válassza a **Sztring** lehetőséget.
  5. Az **Érték** mezőbe írja be a **BLACKLIST** (LETILTOTT) vagy a **WHITELIST** (ENGEDÉLYEZETT) értéket.



## <a name="step-3-assign-both-policies"></a>3\. lépés: Mindkét szabályzat hozzárendelése

Használja a következő témakör utasításait mindkét profil hozzárendelésére a szükséges felhasználókhoz vagy eszközökhöz: [Eszközprofilok hozzárendelése](device-profile-assign.md).
