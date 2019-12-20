---
title: VPN-beállítások konfigurálása Windows 8,1-eszközökön a Microsoft Intune-Azure-ban | Microsoft Docs
description: VPN-konfigurációs profil hozzáadása vagy létrehozása virtuális magánhálózati (VPN) konfigurációs beállításokkal, beleértve a kapcsolat részleteit, valamint az IP-vagy FQDN-címet tartalmazó proxybeállításokat, valamint a Microsoft Intune TCP-portját a Windows 8,1 rendszerű eszközökön.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207043"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>VPN-beállítások hozzáadása a Windows 8,1-eszközökön Microsoft Intune



A cikk a VPN-kapcsolatoknak a Windows 8.1 rendszerű eszközökön való konfigurálására használható Intune-beállításokat ismerteti.

A megadott beállításoktól függően a következő listában található értékek némelyike nem konfigurálható.

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások

- Az **összes beállítás alkalmazása csak Windows 8,1 esetén**: ezt a beállítást a klasszikus Intune-portálon konfigurálhatja. A Microsoft Endpoint Manager felügyeleti központban ez a beállítás nem módosítható. Ha be **van**állítva, a beállítások csak a Windows 8,1 rendszerű eszközökre vonatkoznak. Ha a **nincs konfigurálva**értékre van állítva, ezek a beállítások a Windows 10-es eszközökre is érvényesek.
- **Kapcsolat neve**: Adja meg a kapcsolat nevét. A felhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Kiszolgálók**: Adjon meg egy vagy több olyan VPN-kiszolgálót, amelyhez az eszközök csatlakozni fognak.
  - **Hozzáadás**: megnyitja a **sor hozzáadása** lapot, ahol megadhatja a következő információkat:
    - **Leírás**: adjon meg egy leíró nevet a kiszolgáló számára, például a **contoso VPN-kiszolgálót**.
    - **IP-cím vagy**teljes tartománynév: adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljesen minősített tartománynevét, amelyhez az eszközök csatlakoznak. Példák: **192.168.1.1**, **vpn.contoso.com**.
    - **Alapértelmezett kiszolgáló**: Ezt a kiszolgálót engedélyezi alapértelmezett kiszolgálóként, melyet az eszközök kapcsolat létesítéséhez fognak használni. Csak egy kiszolgálót állítson be alapértelmezett kiszolgálóként.
  - **Importálás**: tallózással keresse meg a kiszolgálók listáját egy vesszővel tagolt fájlban a következő formátumban: Leírás, IP-cím vagy teljes tartománynév, alapértelmezett kiszolgáló. A kiszolgálók a **Kiszolgálók** listába történő importálásához kattintson az **OK** gombra.
  - **Exportálás**: exportálja a kiszolgálók listáját egy vesszővel tagolt (CSV) fájlba.

- **Kapcsolat típusa**: Az alábbi listából válassza ki a VPN-kapcsolat típusát:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Bejelentkezési csoport vagy tartomány** (csak SonicWALL Mobile-kapcsolódás esetén): adja meg annak a bejelentkezési csoportnak vagy tartománynak a nevét, amelyhez csatlakozni szeretne.

- **Szerepkör** (csak Pulse Secure): adja meg annak a felhasználói szerepkörnek a nevét, amely hozzáfér ehhez a kapcsolathoz. A felhasználói szerepkörök személyes beállításokat definiálnak, és engedélyeznek vagy letiltanak bizonyos hozzáférési funkciókat.

- **Tartomány** (csak Pulse Secure): adja meg a használni kívánt hitelesítési tartomány nevét. A hitelesítési tartomány a Pulse Secure kapcsolattípus által használt hitelesítési erőforrások csoportja.

- **Egyéni XML**: adja meg a VPN-kapcsolatokat konfiguráló egyéni XML-parancsokat.

  **Pulse Secure példa**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **Ellenőrzőpont Mobile VPN-példa**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **SonicWALL Mobile-csatlakozási példa**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **F5 Edge Client példa**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  Az egyéni XML-parancsok írásával kapcsolatos további információkért tekintse meg a gyártó VPN-dokumentációját.

## <a name="proxy-settings"></a>Proxybeállítások

- **Proxybeállítások automatikus észlelése**: Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, adja meg, hogy szeretné-e, hogy az eszközök automatikusan azonosítsák a kapcsolódási beállításokat.
- **Automatikus konfigurációs szkript**: A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** . Például írja be a következőt: `http://proxy.contoso.com`.
- **Proxykiszolgáló használata**: engedélyezze ezt a beállítást, ha manuálisan szeretné megadni a proxykiszolgáló beállításait.
  - **Cím**: adja meg a proxykiszolgáló címét (IP-címként).
  - **Portszám**: Adja meg a proxykiszolgálóhoz társított portszámot.
- **Proxy mellőzése helyi címek**esetén: Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, és nem kívánja használni a proxykiszolgálót a megadott helyi címekhez, válassza ezt a lehetőséget.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

VPN-beállítások konfigurálása [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)és [Windows 10 rendszerű](vpn-settings-windows-10.md) eszközökön.
