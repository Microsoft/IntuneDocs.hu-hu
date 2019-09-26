---
title: VPN-beállítások használata az Android Enterprise rendszerhez az Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg az összes beállítást a VPN-kapcsolatok létrehozásához az Android Enterprise-eszközökön Microsoft Intuneban. Adja meg a VPN-kiszolgáló kapcsolati nevét, IP-címét vagy teljes tartománynevét, válassza ki a felhasználók hitelesítésének módját, és válassza a Citrix, a SonicWall, a Point kapszula és a Pulse Secure kapcsolati típusok lehetőséget.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eff546c619f6314508c475a98bc29c3f8bc8181b
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "71302821"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Androidos vállalati eszközbeállítások a VPN konfigurálásához az Intune-ban

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk felsorolja és leírja a VPN-kapcsolatoknak az Android rendszerű eszközökön való felügyeletére vonatkozó különböző beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használja a VPN-kapcsolat létrehozásához, a VPN hitelesítésének módjához, a VPN-kiszolgáló típusának kiválasztásához és egyebekhez.

Intune-rendszergazdaként VPN-beállításokat hozhat létre és rendelhet hozzá az Android Enterprise-eszközökhöz. 

Ha többet szeretne megtudni a VPN-profilokról az Intune-ban, lásd: [VPN-profilok](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz-konfigurációs profilt](vpn-settings-configure.md#create-a-device-profile), és válassza az **Android Enterprise**lehetőséget.

## <a name="device-owner-only"></a>Csak az eszköz tulajdonosa

- **Kapcsolatok neve**: Adja meg a kapcsolatok nevét. A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatokat az eszközükön. Például írja be a következőt: `Contoso VPN`.
- **IP-cím vagy teljes tartománynév**: Adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljes tartománynevét (FQDN), amelyhez az eszközök csatlakoznak. Írja be például a **192.168.1.1** vagy a **vpn.contoso.com** címet.

  - **Hitelesítési módszer**: Válassza ki, hogy az eszközök hogyan legyenek hitelesítve a VPN-kiszolgálóval. A választható lehetőségek:
  
    - **Tanúsítványok**: Válasszon ki egy meglévő SCEP-vagy PKCS-tanúsítvány-profilt a kapcsolatok hitelesítéséhez. [Tanúsítványok konfigurálása](certificates-configure.md): felsorolja a tanúsítványprofil létrehozásának lépéseit.
    - **Felhasználónév és jelszó**: A VPN-kiszolgálóra való bejelentkezéskor a végfelhasználóknak meg kell adniuk felhasználónevét és jelszavát.

- **Kapcsolattípus**: Válassza ki a VPN-kapcsolat típusát. A választható lehetőségek:

  - **Cisco AnyConnect**
  - **F5-hozzáférés**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Csak munkahelyi profil

- **Kapcsolatok neve**: Adja meg a kapcsolatok nevét. A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatokat az eszközükön. Például írja be a következőt: `Contoso VPN`.
- **IP-cím vagy teljes tartománynév**: Adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljes tartománynevét (FQDN), amelyhez az eszközök csatlakoznak. Írja be például a **192.168.1.1** vagy a **vpn.contoso.com** címet.

  - **Hitelesítési módszer**: Válassza ki, hogy az eszközök hogyan legyenek hitelesítve a VPN-kiszolgálóval. A választható lehetőségek:
  
    - **Tanúsítványok**: Válasszon ki egy meglévő SCEP-vagy PKCS-tanúsítvány-profilt a kapcsolatok hitelesítéséhez. [Tanúsítványok konfigurálása](certificates-configure.md): felsorolja a tanúsítványprofil létrehozásának lépéseit.
    - **Felhasználónév és jelszó**: A VPN-kiszolgálóra való bejelentkezéskor a végfelhasználóknak meg kell adniuk felhasználónevét és jelszavát.

- **Kapcsolattípus**: Válassza ki a VPN-kapcsolat típusát. A választható lehetőségek:

  - **Cisco AnyConnect**
  - **F5-hozzáférés**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Az [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 és újabb](vpn-settings-windows-10.md), [Windows 8,1](vpn-settings-windows-8-1.md)és [Windows Phone-telefon 8,1](vpn-settings-windows-phone-8-1.md) rendszerű eszközökhöz VPN-profilokat is létrehozhat.
