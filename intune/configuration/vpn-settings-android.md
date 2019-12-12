---
title: VPN-beállítások használata Android-eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg az összes beállítást, amely VPN-kapcsolatokat hoz létre az Android-eszközökön a Microsoft Intuneban. Adja meg a VPN-kiszolgáló kapcsolati nevét, IP-címét vagy teljes tartománynevét, válassza ki a felhasználók hitelesítésének módját, és válassza a Citrix, a SonicWall, a Point kapszula és a Pulse Secure kapcsolati típusok lehetőséget.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d9fefc2413e2dafbf5d0ad67ea15f5f8406cc1c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506544"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Az Android-eszköz beállításai a VPN konfigurálásához az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és leírja az Android-eszközökön beállítható VPN-kapcsolati beállításokat. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használja a VPN-kapcsolat létrehozásához, a VPN hitelesítésének módjához, a VPN-kiszolgáló típusának kiválasztásához és egyebekhez.

Intune-rendszergazdaként VPN-beállításokat hozhat létre és rendelhet hozzá az Android-eszközökhöz. 

Ha többet szeretne megtudni a VPN-profilokról az Intune-ban, lásd: [VPN-profilok](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](vpn-settings-configure.md#create-a-device-profile), és válassza az **Android**lehetőséget.

## <a name="base-vpn"></a>Alapszintű VPN

- **Kapcsolat neve**: Adja meg a kapcsolat nevét. A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatokat az eszközükön. Például írja be a következőt: `Contoso VPN`.
- **IP-cím vagy teljes tartománynév**: Adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljes tartománynevét (FQDN), amelyhez az eszközök csatlakoznak. Írja be például a **192.168.1.1** vagy a **vpn.contoso.com** címet.

  - **Hitelesítési mód**: Válassza ki, hogy miképpen hitelesítik magukat az eszközök a VPN-kiszolgálón. A választható lehetőségek:

    - **Tanúsítványok**: Válasszon egy meglévő SCEP- vagy PKCS-tanúsítványprofilt a kapcsolat hitelesítéséhez. [Tanúsítványok konfigurálása](../protect/certificates-configure.md): felsorolja a tanúsítványprofil létrehozásának lépéseit.
    - **Felhasználónév és jelszó**: a VPN-kiszolgálóra való bejelentkezéskor a rendszer a végfelhasználókat kéri a Felhasználónév és a jelszó megadására.

- **Kapcsolat típusa**: Válassza ki a VPN-kapcsolat típusát. A választható lehetőségek:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5-hozzáférés**
  - **Pulse Secure**
  - **Citrix SSO**

- **Ujjlenyomat** (Csak Check Point Capsule VPN esetén): Adjon meg egy sztringet, mint például a **Contoso-ujjlenyomatkód**, a VPN-kiszolgáló megbízhatóságának ellenőrzéséhez. A rendszer ujjlenyomatot továbbít az ügyfélnek, így az ügyfél tudni fogja, hogy megbízik-e minden olyan kiszolgálón, amely ugyanazzal az ujjlenyomattal rendelkezik. Ha az eszköz még nem rendelkezik ujjlenyomattal, akkor arra kéri a felhasználót, hogy bízzon meg a VPN-kiszolgálóban, miközben megjeleníti az ujjlenyomatot. A felhasználó manuálisan ellenőrizheti az ujjlenyomatot, és úgy dönt, hogy megbízik a kapcsolódásban.
- **Adja meg a kulcs-érték párokat a Citrix VPN attribútumaihoz** (Csak Citrix esetén): Adja meg a Citrix által megadott kulcs-érték párokat. Ezek az értékek konfigurálják a VPN-kapcsolat tulajdonságait. 

  A vesszővel tagolt értékeket tartalmazó fájlokat (. csv) is **importálhatja** kulcsokkal és érték párokkal. Ügyeljen arra, hogy a **saját adataim fejléceket** és **kulcsokat** tartalmazó tulajdonságokkal rendelkeznek.

  A kulcs-és érték párok hozzáadása után az **exportálással** biztonsági másolatot készíthet az adatokról egy. csv-fájlba.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

VPN-profilokat az [Android Enterprise](vpn-settings-android-enterprise.md), az [iOS](vpn-settings-ios.md), a [MacOS](vpn-settings-macos.md), a [windows 10 és újabb](vpn-settings-windows-10.md), a [Windows 8,1](vpn-settings-windows-8-1.md)és a [Windows Phone-telefon 8,1](vpn-settings-windows-phone-8-1.md) rendszerű eszközökhöz is létrehozhat.
