---
title: Egyéni alkalmazásonkénti Androidos VPN-profil
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan hozhat létre alkalmazásonkénti VPN-profilt a Microsoft Intune-nal felügyelt Android-eszközökhöz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62f418e396c5030a47ea0bcb31914cd4e1069c40
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319844"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Alkalmazásonkénti VPN-profil létrehozása androidos eszközökhöz egyéni Microsoft Intune-profillal

Az Intune által felügyelt Android 5.0-s és újabb rendszerű eszközökhöz alkalmazásonkénti VPN-profilt hozhat létre. Először hozzon létre egy olyan VPN-profit, amely a Pulse Secure vagy a Citrix kapcsolattípust használja. Ezután hozzon létre egy olyan egyéni szabályzatot, amely a VPN-profilt meghatározott alkalmazásokkal társítja.

> [!NOTE]
> Ha az alkalmazáson belüli VPN-t androidos vállalati eszközökön szeretné használni, ezeket a lépéseket is használhatja. A VPN-ügyfélalkalmazás [alkalmazás-konfigurációs szabályzatát](../apps/app-configuration-policies-use-android.md) azonban ajánlott használni.

Miután hozzárendeli a szabályzatot az Android rendszerű eszközhöz vagy felhasználócsoportokhoz, a felhasználóknak el kell indítaniuk a PulseSecure vagy a Citrix VPN-ügyfelet. A VPN-ügyfél ezután csak a megadott alkalmazások adatforgalma számára engedélyezi a nyitott VPN-kapcsolat használatát.

> [!NOTE]
>
> Ez a profil csak a Pulse Secure és a Citrix kapcsolattípust támogatja.

## <a name="step-1-create-a-vpn-profile"></a>1\. lépés: VPN-profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profilnév például a **teljes vállalat androidos/app VPN-profilja**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza az **Android**lehetőséget.
    - **Profil típusa**: válassza a **VPN**lehetőséget.

4. Válassza a **Beállítások** > **Konfigurálás** lehetőséget. Ezután konfigurálja a VPN-profilt. További információ: [VPN-beállítások konfigurálása](vpn-settings-configure.md) és [Intune VPN-beállítások Android-eszközökhöz](vpn-settings-android.md).

Jegyezze le a VPN-profil létrehozásakor megadott **Kapcsolat neve** értéket. Erre szükség lesz a következő lépésben. Például: **AlkVpnProfil**.

## <a name="step-2-create-a-custom-configuration-policy"></a>2\. lépés: Egyéni konfigurációs szabályzat létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet az egyéni profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profilnév például **Egyéni OMA-URI Android VPN-profil a teljes vállalat számára**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza az **Android**lehetőséget.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. Válassza a **Beállítások** > **Konfigurálás** lehetőséget.
5. Az **Egyéni OMA-URI beállítások** panelen válassza a **Hozzáadás** lehetőséget.
    - **Név**: adja meg a beállítás nevét.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **OMA-URI**: írja be `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, ahol a *név* az 1. lépésben feljegyzett név. Ebben a példában a sztring `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Adattípus**: írja be a **karakterláncot**.
    - **Érték**: adja meg a profilhoz társítandó csomagok pontosvesszővel tagolt listáját. Ha például azt szeretné, hogy az Excel és a Google Chrome böngésző használhassa a VPN-kapcsolat használatát, írja be `com.microsoft.office.excel;com.android.chrome`.

![Példa Android rendszerű, alkalmazásonkénti VPN-hez létrehozott egyéni szabályzatra](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Az alkalmazáslista Blacklist (Letiltott) vagy Whitelist (Engedélyezett) értékre állítása (nem kötelező)

A **feketelistás** érték használatával megadhatja azon alkalmazások listáját, amelyek *nem* használhatják a VPN-kapcsolatokat. Minden más alkalmazás VPN-kapcsolaton keresztül fog csatlakozni az internethez. Vagy használja a **WHITELIST** értéket a VPN-kapcsolat használatára *képes* alkalmazások listájának megadásához. A listán nem szereplő alkalmazások nem csatlakoznak a VPN-en keresztül.

1. Az **Egyéni OMA-URI beállítások** panelen válassza a **Hozzáadás** lehetőséget.
2. Adja meg a beállítás nevét.
3. Az **OMA-URI**mezőbe írja be a `./Vendor/MSFT/VPN/Profile/*Name*/Mode`*nevet* , ahol a név az 1. lépésben feljegyzett VPN-profil neve. A példánkban a sztring `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. Az **adattípus**mezőben adja meg a **karakterlánc**értéket.
5. Az **Érték** mezőbe írja be a **BLACKLIST** (LETILTOTT) vagy a **WHITELIST** (ENGEDÉLYEZETT) értéket.

## <a name="step-3-assign-both-policies"></a>3\. lépés: Mindkét szabályzat hozzárendelése

[Rendeljen mindkét eszközt](device-profile-assign.md) a szükséges felhasználókhoz vagy eszközökhöz.
