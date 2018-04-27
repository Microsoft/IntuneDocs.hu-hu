---
title: Windows 8.1-eszközökre vonatkozó VPN-beállítások a Microsoft Intune-ban
titleSuffix: ''
description: A VPN-kapcsolatok Windows 8.1 rendszerű eszközökön való konfigurálásához használható Intune-beállítások ismertetése.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30aa56913cc3bda2d1c8b8b67e982c565c44a2a8
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/26/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>A Windows 8.1 rendszerű eszközökre vonatkozó VPN-beállítások konfigurálása a Microsoft Intune-ban

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A cikk a VPN-kapcsolatoknak a Windows 8.1 rendszerű eszközökön való konfigurálására használható Intune-beállításokat ismerteti.

A megadott beállításoktól függően a következő listában található értékek némelyike nem konfigurálható.

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások


- **Az összes beállítás alkalmazása csak a Windows 8.1-re** – Ezt a beállítást a klasszikus Intune-portálon lehet konfigurálni. Ez a beállítás az Azure Portal webhelyen nem módosítható. Ha ez a beállítás a **Konfigurálva** értékre van állítva, a rendszer minden beállítást csak a Windows 8.1 rendszerű eszközökre alkalmaz. Ha a **Nincs konfigurálva** értékre van állítva, akkor a Windows 10 rendszerű eszközökre is alkalmazza rendszer ezeket a beállításokat.
- **Kapcsolat neve** – Adja meg a kapcsolat nevét. A felhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Kiszolgálók** – Adjon meg egy vagy több olyan VPN-kiszolgálót, amelyhez az eszközök csatlakozni fognak.
    - **Hozzáadás** – Megnyitja a **Sor hozzáadása** lapot, melyen a következőket adhatja meg:
        - **Leírás** – Adja meg a kiszolgáló leíró nevét (például **Contoso VPN-kiszolgáló**).
        - **IP-cím vagy teljes tartománynév** – Adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljes tartománynevét, amelyhez az eszközök csatlakoznak. Példák: **192.168.1.1**, **vpn.contoso.com**.
        - **Alapértelmezett kiszolgáló** – Ezt a kiszolgálót engedélyezi alapértelmezett kiszolgálóként, melyet az eszközök kapcsolat létesítéséhez fognak használni. Mindenképpen csak egy kiszolgálót állítson be alapértelmezett kiszolgálóként.
    - **Importálás** – Tallózással keressen meg egy, a kiszolgálók vesszővel tagolt listáját tartalmazó fájlt, melynek formátuma a következő: leírás, IP-cím vagy teljes tartománynév, alapértelmezett kiszolgáló. Az **OK** gombra kattintva indíthatja el ezek importálását a **Kiszolgálók** listába.
    - **Exportálás** – Exportálja a kiszolgálók listáját egy vesszővel tagolt (CSV-) fájlba.

- **Kapcsolat típusa** – Az alábbi listából válassza ki a VPN-kapcsolat típusát:
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Bejelentkezési csoport vagy tartomány** (csak SonicWall Mobile Connect esetén) – Adja meg annak a bejelentkezési csoportnak vagy tartománynak a nevét, amelyhez csatlakozni szeretne.

- **Szerepkör** (csak Pulse Secure) – Adja meg annak a felhasználói szerepkörnek a nevét, amely hozzáfér ehhez a kapcsolathoz. A felhasználói szerepkörök személyes beállításokat definiálnak, és engedélyeznek vagy letiltanak bizonyos hozzáférési funkciókat.

- **Tartomány** (csak Pulse Secure) – Adja meg a használni kívánt hitelesítési tartomány nevét. A hitelesítési tartomány a Pulse Secure kapcsolattípus által használt hitelesítési erőforrások csoportja.


- **Egyéni XML** – Itt a VPN-kapcsolatot konfiguráló egyéni XML-parancsokat adhat meg.

**Példa a Pulse Secure esetére:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Példa a CheckPoint Mobile VPN esetére:**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Példa a SonicWall Mobile Connect esetére:**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Példa az F5 Edge Client esetére:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Az egyéni XML-parancsok írásával kapcsolatban további információt az egyes gyártók VPN-dokumentációjában talál.


## <a name="proxy-settings"></a>Proxybeállítások

- **Proxybeállítások automatikus észlelése** – Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, adja meg, hogy szeretné-e, ha az eszközök automatikusan észlelnék a kapcsolatbeállításokat. További információt a Windows Server dokumentációjában talál.
- **Automatikus konfigurációs szkript** – A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **Proxykiszolgáló URL-címét** (például **http://proxy.contoso.com**).
- **Proxykiszolgáló használata** – Ha manuálisan szeretné megadni a proxykiszolgáló beállításait, akkor engedélyezze ezt a beállítást.
    - **Cím** – Adja meg a proxykiszolgáló címét (IP-címként).
    - **Portszám** – Adja meg a proxykiszolgálóhoz társított portszámot.
- **Proxy mellőzése helyi címek esetén** – Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, válassza ezt a beállítást, ha a megadott helyi címekhez nem szeretné használni a proxykiszolgálót. További információt a Windows Server dokumentációjában talál.
