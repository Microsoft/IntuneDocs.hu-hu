---
title: VPN-beállítások hozzáadása az eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
description: Android, Android Enterprise, iOS, macOS és Windows rendszerű eszközök esetén a beépített beállítások használatával virtuális magánhálózati (VPN-) kapcsolatokat hozhat létre Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5628ba39cafe38cc66827d69584d009c15326bd4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72491767"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>VPN-profilok létrehozása a VPN-kiszolgálókhoz való csatlakozáshoz az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A virtuális magánhálózatok (VPN) segítségével biztonságos távoli hozzáférést biztosíthat a felhasználóknak a szervezeti hálózathoz. Az eszközök VPN-kapcsolati profilt használnak a VPN-kiszolgálóval létesített kapcsolat indításához. A **VPN-profilok** a Microsoft Intune VPN-beállításokat rendelhetnek a szervezet felhasználóihoz és eszközeihez, így könnyen és biztonságosan kapcsolódhatnak a szervezeti hálózathoz.

Például az összes iOS-eszközt konfigurálni szeretné a szükséges beállításokkal a szervezeti hálózaton lévő fájlmegosztás csatlakoztatásához. Létre kell hoznia egy VPN-profilt, amely tartalmazza ezeket a beállításokat. Ezt követően ezt a profilt hozzárendelheti az összes iOS-eszközzel rendelkező felhasználóhoz. A felhasználók látni fogják a VPN-kapcsolatot a rendelkezésre álló hálózatok listájában, és könnyen csatlakozhatnak.

> [!NOTE]
> Az [Egyéni Intune-konfigurációs szabályzatok](custom-settings-configure.md) használatával VPN-profilokat hozhat létre a következő platformokhoz:
>
> * Android 4 és újabb verziók
> * A Windows 8.1-es vagy újabb verzióját futtató regisztrált eszközök
> * Windows Phone 8.1 és újabb verziók
> * A Windows 10 asztali verzióját futtató regisztrált eszközök
> * Windows 10 mobil verzió
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN-kapcsolat típusai

A következő kapcsolattípusokkal hozhat létre VPN-profilt:

|Kapcsolat típusa|Platfésm|
|-|-|
|Automatikus|Windows 10|
|Check Point Capsule VPN|– Android<br/>– Androidos vállalati munkahelyi profilok<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8,1<br/>-Windows Phone-telefon 8,1|
|Cisco AnyConnect|– Android<br/>– Androidos vállalati munkahelyi profilok<br/>– Androidos vállalati eszköz tulajdonosa (teljes mértékben felügyelt)<br/>– iOS<br/>– macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|– Android<br/>– Androidos vállalati munkahelyi profilok: [alkalmazás-konfigurációs házirend](../apps/app-configuration-policies-use-android.md) használata<br/>– iOS<br/>– Windows 10|
|Egyéni VPN|– iOS<br/>– macOS|
|F5 Access|– Android<br/>– Androidos vállalati munkahelyi profilok<br/>– Androidos vállalati eszköz tulajdonosa (teljes mértékben felügyelt)<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8,1<br/>-Windows Phone-telefon 8,1|
|IKEv2| – iOS<br/>– Windows 10|
|L2TP|Windows 10|
|Palo Alto Hálózatok GlobalProtect|– Androidos vállalati munkahelyi profilok: [alkalmazás-konfigurációs házirend](../apps/app-configuration-policies-use-android.md) használata<br/>– iOS<br/>– Windows 10|
|PPTP|Windows 10|
|Pulse Secure|– Android<br/>– Androidos vállalati munkahelyi profilok<br/>– Androidos vállalati eszköz tulajdonosa (teljes mértékben felügyelt)<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8,1<br/>-Windows Phone-telefon 8,1|
|SonicWall Mobile Connect|– Android<br/>– Androidos vállalati munkahelyi profilok<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8,1<br/>-Windows Phone-telefon 8,1|
|Zscaler|– Androidos vállalati munkahelyi profilok: [alkalmazás-konfigurációs házirend](../apps/app-configuration-policies-use-android.md) használata<br/>– iOS|

> [!IMPORTANT]
> Az eszközökre alkalmazott VPN-profilok használatához telepíteni kell a megfelelő VPN-alkalmazást a profilhoz. Az alkalmazás Intune-nal történő hozzárendeléséhez [A Microsoft Intune-alkalmazásfelügyelet ismertetése](../apps/app-management.md) című témakörben talál segítséget.  

Az [Egyéni beállításokkal rendelkező profil létrehozása](custom-settings-configure.md) című témakörből tájékozódhat arról, hogy hogyan hozhat létre egyéni VPN-profilokat URI-beállításokkal.

## <a name="create-a-device-profile"></a>Eszközprofil létrehozása

1. Az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ban válassza az **eszköz konfigurációja** > **profilok** > **profil létrehozása**lehetőséget.
2. Adja meg a következő tulajdonságokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profilnév például a **teljes vállalat VPN-profilja**.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza ki az eszközök platformját. A választható lehetőségek:

      - **Android--**
      - **Android Enterprise**@no__t – 1**eszköz tulajdonosa**
      - **Android Enterprise**@no__t – 1**munkahelyi profil**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 és újabb verziók**
      - **Windows 10 és újabb**

    - **Profil típusa**: válassza a **VPN**lehetőséget.

3. A kiválasztott platformtól függően a konfigurálható beállítások eltérőek. Az egyes platformokon az alábbi cikkekben talál részletes beállításokat:

    - [Android-beállítások](vpn-settings-android.md)
    - [Androidos vállalati beállítások](vpn-settings-android-enterprise.md)
    - [iOS-/iPadOS-beállítások](vpn-settings-ios.md)
    - [macOS-beállítások](vpn-settings-macos.md)
    - [Windows Phone 8.1-beállítások](vpn-settings-windows-phone-8-1.md)
    - [Windows 8.1-beállítások](vpn-settings-windows-8-1.md)
    - [Windows 10-beállítások](vpn-settings-windows-10.md) (beleértve a Windows Holographic for Businesst is)

4. Ha elkészült, **hozza létre** a profilt.

Ekkor létrejön a profil, és megjelenik a profilok listájában. Ha csoportokhoz szeretné hozzárendelni a profilt, tekintse meg az [eszközprofilok hozzárendelését](device-profile-assign.md) ismertető cikket.

## <a name="secure-your-vpn-profiles"></a>VPN-profilok biztonságossá tétele

A VPN-profilok számos különböző kapcsolattípust és különféle gyártóktól származó protokollt használhatnak. Ezek a kapcsolatok általában a következő módszerekkel biztonságosak.

### <a name="certificates"></a>Tanúsítványok

A VPN-profil létrehozásakor ki kell választania egy SCEP-vagy PKCS-tanúsítványprofilt, amelyet korábban az Intune-ban hozott létre. Ez a profil identitástanúsítványként is ismert. Ennek segítségével hajtja végre a rendszer a hitelesítést egy olyan megbízható tanúsítványprofillal (vagy *főtanúsítvánnyal*), amelyet Ön a felhasználói eszköz csatlakozásának engedélyezéséhez hozott létre. A megbízható tanúsítványt a rendszer a VPN-kapcsolatot hitelesítő számítógépre alkalmazza, amely általában a VPN-kiszolgáló.

A tanúsítványprofiloknak az Intune-ban történő létrehozásáról és használatáról a következő dokumentumban olvashat bővebben: [Tanúsítványok konfigurálása a Microsoft Intune-nal](../protect/certificates-configure.md).

### <a name="user-name-and-password"></a>Felhasználónév és jelszó

A felhasználó a VPN-kiszolgálón felhasználónév és jelszó megadásával végzi el a hitelesítést.

## <a name="next-steps"></a>További lépések

A létrehozott profil egyelőre semmit sem csinál. Ezután [rendelje hozzá a profilt](device-profile-assign.md) bizonyos eszközökhöz.

Az alkalmazáson belüli VPN-eket [Android](android-pulse-secure-per-app-vpn.md) -és [iOS](vpn-setting-configure-per-app.md) -eszközökön is létrehozhatja és használhatja.
