---
title: VPN-beállítások konfigurálása macOS-eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
description: 'Virtuális magánhálózati (VPN) konfigurációs profil hozzáadása vagy létrehozása, beleértve a kapcsolat részleteit, a megosztott bújtatást, az egyéni VPN-beállításokat az azonosítóval, a kulcs-érték párokkal, a proxy beállításait konfigurációs parancsfájllal, IP-címmel vagy teljes tartománynévvel, valamint a TCP-portot a következőben: Microsoft Intune macOS rendszerű eszközökön.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 044b35b34a9a5b01537e82dcfddca74a284ebdcc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72491013"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>VPN-beállítások hozzáadása macOS-eszközökön Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikk a VPN-kapcsolatoknak a macOS rendszerű eszközökön való konfigurálására használható Intune-beállításokat ismerteti.

A megadott beállításoktól függően a következő listában található értékek némelyike nem konfigurálható.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](vpn-settings-configure.md).

> [!NOTE]
> Ezek a beállítások minden regisztrációs típushoz elérhetők. A regisztrációs típusokkal kapcsolatos további információkért lásd: [MacOS-regisztráció](../enrollment/macos-enroll.md).

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások

**Kapcsolat neve**: Adja meg a kapcsolat nevét. A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **IP-cím vagy**teljes tartománynév: adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljesen minősített tartománynevét, amelyhez az eszközök csatlakoznak. Példák: **192.168.1.1**, **vpn.contoso.com**.
- **Hitelesítési módszer**: Válassza ki a következő lehetőségek közül, hogy miképpen hitelesítik magukat az eszközök a VPN-kiszolgálón:
  - **Tanúsítványok**: a **hitelesítési tanúsítvány**területen válassza ki a korábban létrehozott SCEP vagy PKCS-tanúsítvány profilját a kapcsolódás hitelesítéséhez. A tanúsítványprofilokról további információt a [How to configure certificates](../protect/certificates-configure.md) (Tanúsítványok konfigurálása) című cikkben találhat.
  - **Felhasználónév és jelszó**: a végfelhasználóknak felhasználónevet és jelszót kell megadniuk a VPN-kiszolgálóra való bejelentkezéshez.
- **Kapcsolat típusa**: Az alábbi listából válassza ki a VPN-kapcsolat típusát:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Egyéni VPN**
- **Megosztott bújtatás**: **engedélyezheti** vagy **letilthatja** ezt a beállítást, amely lehetővé teszi, hogy az eszközök döntsenek a forgalomtól függően, hogy melyik kapcsolatokat használják. Egy szállodai vendég például a munkahelyi fájlok elérésére a VPN-kapcsolatot, de egyszerű böngészésre a szálloda normál hálózatát használja.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Egyéni VPN-beállítások

Ha az **Egyéni VPN** lehetőséget választotta, konfigurálja ezeket a beállításokat is:

- **VPN-azonosító**: adja meg a használt VPN-alkalmazás azonosítóját. Ezt az azonosítót a VPN-szolgáltató biztosítja.
- **Adja meg a kulcs-érték párokat az egyéni VPN attribútumainak konfigurálásához**: **Kulcsok** és **Értékek** hozzáadásával vagy importálásával szabhatja testre a VPN-kapcsolatot. Ezeket az értékeket általában a VPN-szolgáltató biztosítja.

## <a name="proxy-settings"></a>Proxybeállítások

- **Automatikus konfigurációs szkript**: A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** . Például írja be a következőt: `http://proxy.contoso.com`.
- **Cím**: adja meg a proxykiszolgáló címét (IP-címként).
- **Portszám**: Adja meg a proxykiszolgálóhoz társított portszámot.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

VPN-beállítások konfigurálása [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [iOS](vpn-settings-ios.md)és [Windows 10 rendszerű](vpn-settings-windows-10.md) eszközökön.
