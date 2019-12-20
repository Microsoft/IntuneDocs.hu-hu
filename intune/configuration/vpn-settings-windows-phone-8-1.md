---
title: VPN-beállítások konfigurálása Windows Phone-telefon 8,1-eszközökön Microsoft Intune-Azure-ban | Microsoft Docs
description: VPN-konfigurációs profil hozzáadása vagy létrehozása virtuális magánhálózati (VPN) konfigurációs beállításokkal, beleértve a kapcsolat részleteit, valamint az IP-vagy FQDN-címet tartalmazó proxybeállításokat, valamint a Windows Phone-telefon 8,1-at futtató eszközökön Microsoft Intune TCP-portot.
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
ms.openlocfilehash: 70f33fe132eb6c3dbf91c5dc313369d75f4f3e24
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207026"
---
# <a name="add-vpn-settings-on-windows-phone-81-devices-in-microsoft-intune"></a>VPN-beállítások hozzáadása Windows Phone-telefon 8,1-eszközökön Microsoft Intune



A cikk a VPN-kapcsolatoknak a Windows Phone 8.1 rendszerű eszközökön való konfigurálására használható Intune-beállításokat ismerteti. 

A megadott beállításoktól függően a következő listában található értékek némelyike nem konfigurálható.

>[!IMPORTANT]
>A Windows Phone-telefon 8,1 VPN-profilok a Windows 10-es eszközökre is alkalmazhatók.

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások

- Az **összes beállítás alkalmazása csak Windows Phone-telefon 8,1-** re: ezt a beállítást a klasszikus Intune-portálon konfigurálhatja. A Microsoft Endpoint Manager felügyeleti központban ez a beállítás nem módosítható. Ha be **van**állítva, a rendszer a beállításokat csak Windows Phone-telefon 8,1-es eszközökre alkalmazza. Ha a **nincs konfigurálva**értékre van állítva, ezek a beállítások a Windows 10 Mobile rendszerű eszközökre is érvényesek.
- **Kapcsolat neve**: Adja meg a kapcsolat nevét. A felhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Hitelesítési módszer**: Válassza ki a következő lehetőségek közül, hogy miképpen hitelesítik magukat az eszközök a VPN-kiszolgálón:
  - **Tanúsítványok**: a **hitelesítési tanúsítvány**területen válassza ki a korábban létrehozott SCEP vagy PKCS-tanúsítvány profilját a kapcsolódás hitelesítéséhez. A tanúsítványprofilokról további információt a [How to configure certificates](../protect/certificates-configure.md) (Tanúsítványok konfigurálása) című cikkben találhat.
  - **Felhasználónév és jelszó**: a végfelhasználóknak felhasználónevet és jelszót kell megadniuk a VPN-kiszolgálóra való bejelentkezéshez.
- **Kiszolgálók**: Adjon meg egy vagy több olyan VPN-kiszolgálót, amelyhez az eszközök csatlakozni fognak.
  - **Hozzáadás**: megnyitja a **sor hozzáadása** panelt, ahol megadhatja a következő adatokat:
    - **Leírás**: adjon meg egy leíró nevet a kiszolgáló számára, például a **contoso VPN-kiszolgálót**.
    - **IP-cím vagy**teljes tartománynév: adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljesen minősített tartománynevét, amelyhez az eszközök csatlakoznak. Példák: **192.168.1.1**, **vpn.contoso.com**.
    - **Alapértelmezett kiszolgáló**: Ezt a kiszolgálót engedélyezi alapértelmezett kiszolgálóként, melyet az eszközök kapcsolat létesítéséhez fognak használni. Csak egy kiszolgálót állítson be alapértelmezett kiszolgálóként.
  - **Importálás**: tallózással keresse meg a kiszolgálók listáját tartalmazó vesszővel tagolt fájlt a következő formátumban: Leírás, IP-cím vagy teljes tartománynév, alapértelmezett kiszolgáló. A kiszolgálók a **Kiszolgálók** listába történő importálásához kattintson az **OK** gombra.
  - **Exportálás**: exportálja a kiszolgálók listáját egy vesszővel tagolt (CSV) fájlba.

- **VPN mellőzése a vállalati Wi-Fi-hálózaton**: Ha engedélyezi ezt a beállítást, megadhatja, hogy a rendszer ne használja a VPN-kapcsolatokat, amikor az eszköz a vállalati Wi-Fi-hálózathoz csatlakozik.
- **VPN mellőzése az otthoni Wi-Fi-hálózaton**: engedélyezze ezt a beállítást annak megadásához, hogy a VPN-kapcsolat ne legyen használatban, amikor az eszköz otthoni Wi-Fi-hálózathoz csatlakozik.

- **Kapcsolat típusa**: Az alábbi listából válassza ki a VPN-kapcsolat típusát:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **Bejelentkezési csoport vagy tartomány** (csak SonicWALL Mobile-kapcsolódás esetén): adja meg annak a bejelentkezési csoportnak vagy tartománynak a nevét, amelyhez csatlakozni szeretne.
- **Szerepkör** (csak Pulse Secure): adja meg annak a felhasználói szerepkörnek a nevét, amely hozzáfér ehhez a kapcsolathoz. A felhasználói szerepkörök személyes beállításokat definiálnak, és engedélyeznek vagy letiltanak bizonyos hozzáférési funkciókat.
- **Tartomány** (csak Pulse Secure): adja meg a használni kívánt hitelesítési tartomány nevét. A hitelesítési tartomány a Pulse Secure kapcsolattípus által használt hitelesítési erőforrások csoportja.

- **DNS-utótagok keresési listája**: **adjon hozzá** egy vagy több DNS-t. A rendszer minden egyes megadott DNS-utótagra rákeres, amikor egy rövid nevet használó webhelyhez csatlakozik. Adja meg például a **tartomany1.contoso.com** és a **tartomany2.contoso.com** DNS-utótagot, majd látogasson el a `http://mywebsite` URL-címre. Ekkora a `http://mywebsite.domain1.contoso.com` és a `http://mywebsite.domain2.contoso.com` URL-címre fog keresni.

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

- **Megosztott bújtatás**: **engedélyezheti** vagy **letilthatja** ezt a beállítást, amely lehetővé teszi, hogy az eszközök döntsenek a forgalomtól függően, hogy melyik kapcsolatokat használják. Egy szállodai vendég például a munkahelyi fájlok elérésére a VPN-kapcsolatot, de egyszerű böngészésre a szálloda normál hálózatát használja.

## <a name="proxy-settings"></a>Proxybeállítások

- **Proxybeállítások automatikus észlelése**: Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, adja meg, hogy szeretné-e, hogy az eszközök automatikusan azonosítsák a kapcsolódási beállításokat.
- **Automatikus konfigurációs szkript**: A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **Proxykiszolgáló URL-címét** (például `http://proxy.contoso.com`).
- **Proxykiszolgáló használata**: engedélyezze ezt a beállítást, ha manuálisan szeretné megadni a proxykiszolgáló beállításait.
  - **Cím**: adja meg a proxykiszolgáló címét (IP-címként).
  - **Portszám**: Adja meg a proxykiszolgálóhoz társított portszámot.
- **Proxy mellőzése helyi címek**esetén: Ha a VPN-kiszolgáló proxykiszolgálót igényel a kapcsolathoz, és nem kívánja használni a proxykiszolgálót a megadott helyi címekhez, válassza ezt a lehetőséget.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

VPN-beállítások konfigurálása [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)és [Windows 10 rendszerű](vpn-settings-windows-10.md) eszközökön.
