---
title: A Microsoft Intune Windows Phone 8.1-es eszközökre vonatkozó VPN-beállításai
titleSuffix: ''
description: Útmutató a VPN-kapcsolatok Windows Phone 8.1 rendszerű eszközökön való konfigurálásához használható Intune-beállításokhoz.
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
ms.openlocfilehash: 69de660e65ed2a0f3b6c9c7e4ce774a6fcde2676
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506518"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>A Windows Phone 8.1 rendszerű eszközökre vonatkozó VPN-beállítások konfigurálása a Microsoft Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A cikk a VPN-kapcsolatoknak a Windows Phone 8.1 rendszerű eszközökön való konfigurálására használható Intune-beállításokat ismerteti.


A megadott beállításoktól függően a következő listában található értékek némelyike nem konfigurálható.

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások

- **Az összes beállítás alkalmazása csak Windows Phone 8.1 rendszeren** – Ez a beállítás a klasszikus Intune-portálon konfigurálható. Ez a beállítás az Azure Portalon nem módosítható. Ha ez a beállítás a **Konfigurálva** értékre van állítva, a rendszer minden beállítást csak a Windows Phone 8.1 rendszerű eszközökre alkalmaz. Ha a **Nincs konfigurálva** értékre van állítva, akkor a rendszer a Windows 10 Mobile rendszerű eszközökre is alkalmazza ezeket a beállításokat.
- **Kapcsolat neve** – Nevezze el a kapcsolatot. A felhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Hitelesítési módszer** – Válassza ki a következő lehetőségek közül, hogy miképpen hitelesítik magukat az eszközök a VPN-kiszolgálón:
  - **Tanúsítványok** – A **Hitelesítési tanúsítvány** szakaszban adja meg a kapcsolat hitelesítéséhez korábban létrehozott SCEP- vagy PKCS-tanúsítványprofilok valamelyikét. A tanúsítványprofilokról további információt a [How to configure certificates](../protect/certificates-configure.md) (Tanúsítványok konfigurálása) című cikkben találhat.
  - **Felhasználónév és jelszó** – A végfelhasználóknak felhasználónevet és jelszót kell megadniuk, ha szeretnének bejelentkezni a VPN-kiszolgálóra.
- **Kiszolgálók** – Adjon meg egy vagy több olyan VPN-kiszolgálót, amelyhez az eszközök csatlakozni fognak.
  - **Hozzáadás** – Megnyitja a **Sor hozzáadása** panelt, melyen a következőket adhatja meg:
    - **Leírás** – Adja meg a kiszolgáló leíró nevét (például **Contoso VPN-kiszolgáló**).
    - **IP-cím vagy teljes tartománynév** – Adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljes tartománynevét, amelyhez az eszközök csatlakoznak. Példák: **192.168.1.1**, **vpn.contoso.com**.
    - **Alapértelmezett kiszolgáló** – Ezt a kiszolgálót engedélyezi alapértelmezett kiszolgálóként, melyet az eszközök kapcsolat létesítéséhez fognak használni. Csak egy kiszolgálót állítson be alapértelmezett kiszolgálóként.
  - **Importálás** – Tallózással keressen meg egy, a kiszolgálók vesszővel tagolt listáját tartalmazó fájlt, melynek formátuma a következő: leírás, IP-cím vagy teljes tartománynév, alapértelmezett kiszolgáló. Indítsa el ezeknek a **Kiszolgálók** listába való importálását az **OK** gombra kattintva.
  - **Exportálás** – Exportálja a kiszolgálók listáját egy vesszővel tagolt (CSV-) fájlba.

- **VPN mellőzése a céges Wi-Fi-hálózatban** – Ezzel a beállítással letilthatja a VPN-kapcsolatot, amikor az eszköz a vállalati Wi-Fi-hálózathoz csatlakozik.
- **VPN mellőzése az otthoni Wi-Fi-hálózatban** – Ezzel a beállítással letilthatja a VPN-kapcsolatot, amikor az eszköz otthoni Wi-Fi-hálózathoz csatlakozik.

- **Kapcsolat típusa** – Az alábbi listából válassza ki a VPN-kapcsolat típusát:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **Bejelentkezési csoport vagy tartomány** (csak SonicWall Mobile Connect esetén) – Adja meg annak a bejelentkezési csoportnak vagy tartománynak a nevét, amelyhez csatlakozni szeretne.
- **Szerepkör** (csak Pulse Secure) – Adja meg annak a felhasználói szerepkörnek a nevét, amely hozzáfér ehhez a kapcsolathoz. A felhasználói szerepkörök személyes beállításokat definiálnak, és engedélyeznek vagy letiltanak bizonyos hozzáférési funkciókat.
- **Tartomány** (csak Pulse Secure) – Adja meg a használni kívánt hitelesítési tartomány nevét. A hitelesítési tartomány a Pulse Secure kapcsolattípus által használt hitelesítési erőforrások csoportja.

- **DNS-utótagok keresési listája**  -  Vegyen fel egy vagy több DNS-utótagot a **Hozzáadás** gombra kattintva. A rendszer minden egyes megadott DNS-utótagra rákeres, amikor egy rövid nevet használó webhelyhez csatlakozik. Adja meg például a **tartomany1.contoso.com** és a **tartomany2.contoso.com** DNS-utótagot, majd látogasson el a `http://mywebsite` URL-címre. Ekkora a `http://mywebsite.domain1.contoso.com` és a `http://mywebsite.domain2.contoso.com` URL-címre fog keresni.

- **Egyéni XML** – Itt a VPN-kapcsolatot konfiguráló egyéni XML-parancsokat adhat meg.

    **Példa a Pulse Secure esetére:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Példa a CheckPoint Mobile VPN esetére:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Példa a SonicWall Mobile Connect esetére:**

```xml
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Példa az F5 Edge Client esetére:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Az egyéni XML-parancsok írásával kapcsolatban további információt az egyes gyártók VPN-dokumentációjában talál.

- **Bújtatás megosztása** - Az **Engedélyezés** vagy a **Letiltás** beállítással szabályozhatja, hogy az eszközök választhatnak-e a forgalomtól függően a kapcsolatok közül. Egy szállodai vendég például a munkahelyi fájlok elérésére a VPN-kapcsolatot, de egyszerű böngészésre a szálloda normál hálózatát használja.




## <a name="proxy-settings"></a>Proxybeállítások

- **Proxybeállítások automatikus észlelése** – Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, adja meg, hogy szeretné-e, ha az eszközök automatikusan észlelnék a kapcsolatbeállításokat. További információt a Windows Server dokumentációjában talál.
- **Automatikus konfigurációs szkript** – A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **Proxykiszolgáló URL-címét** (például `http://proxy.contoso.com`).
- **Proxykiszolgáló használata** – Ha manuálisan szeretné megadni a proxykiszolgáló beállításait, akkor engedélyezze ezt a beállítást.
  - **Cím** – Adja meg a proxykiszolgáló címét (IP-címként).
  - **Portszám** – Adja meg a proxykiszolgálóhoz társított portszámot.
- **Proxy mellőzése helyi címek esetén** – Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, válassza ezt a beállítást, ha a megadott helyi címekhez nem szeretné használni a proxykiszolgálót. További információt a Windows Server dokumentációjában talál.
