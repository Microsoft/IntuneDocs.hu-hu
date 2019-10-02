---
title: Windows 10 VPN-beállítások a Microsoft Intuneban – Azure | Microsoft Docs
description: Ismerje meg és olvassa el a Microsoft Intune összes elérhető VPN-beállítását, valamint azt, hogy mire használhatók, és mit tesznek, beleértve a forgalmi szabályokat, a feltételes hozzáférést, valamint a Windows 10 és a Windows holografikus for Business rendszerű eszközök DNS-és proxybeállításait.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d5bd16964162bd30e1c246215ce5fafd23df5dd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730443"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Windows 10 és Windows holografikus eszközök beállításai VPN-kapcsolatok hozzáadásához az Intune használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune használatával adhat hozzá és konfigurálhat VPN-kapcsolatokat az eszközökhöz. Ez a cikk a virtuális magánhálózatok (VPN) létrehozásakor leggyakrabban használt beállításokat és szolgáltatásokat sorolja fel és ismerteti. Ezek a VPN-beállítások és szolgáltatások az Intune-ban leküldett vagy az eszközökre telepített konfigurációs profilokban használatosak.

A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, beleértve a VPN-szállító használatát, a mindig bekapcsolt, a DNS-t, a proxy hozzáadását és egyebeket.

Ezek a beállítások a következő rendszert futtató eszközökre vonatkoznak:

- Windows 10
- Windows Holographic for Business

A kiválasztott beállításoktól függően előfordulhat, hogy nem minden érték konfigurálható.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy VPN-eszköz konfigurációs profilt](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások

- **Kapcsolatok neve**: Adja meg a kapcsolatok nevét. A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Kiszolgálók**: Adjon hozzá egy vagy több olyan VPN-kiszolgálót, amelyhez az eszközök csatlakoznak. Kiszolgáló hozzáadásakor az alábbi információkat adhatja meg:
  - **Description** (Leírás): Adjon meg egy leíró nevet a kiszolgáló számára, például: **contoso VPN-kiszolgáló**
  - **IP-cím vagy teljes tartománynév**: Adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljes tartománynevét (FQDN), amelyhez az eszközök csatlakoznak, például **192.168.1.1** vagy **VPN.contoso.com**
  - **Alapértelmezett kiszolgáló**: Engedélyezi ezt a kiszolgálót az eszköz által a kapcsolat létrehozásához használt alapértelmezett kiszolgálóként. Csak egy kiszolgálót állítson be alapértelmezett kiszolgálóként.
  - **Importálás**: Tallózással keresse meg a kiszolgálók listáját tartalmazó vesszővel tagolt fájlt a következő formátumban: Leírás, IP-cím vagy teljes tartománynév, alapértelmezett kiszolgáló. A kiszolgálók a **Kiszolgálók** listába történő importálásához kattintson az **OK** gombra.
  - **Exportálás**: A kiszolgálók listájának exportálása vesszővel tagolt (CSV) fájlba

- **IP-címek regisztrálása belső DNS-sel**: Válassza az **Engedélyezés** lehetőséget a Windows 10-es VPN-profil konfigurálásához a VPN-interfészhez rendelt IP-címek dinamikus regisztrálásához a belső DNS-sel. Ha a **Tiltás** lehetőséget választja, akkor az IP-címek nem lesznek dinamikusan regisztrálva.

- **Kapcsolattípus**: Válassza ki a VPN-kapcsolat típusát a következő szállítók listájáról:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Hálózatok GlobalProtect**
  - **Automatikus**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Amikor kiválasztja a VPN-kapcsolat típusát, előfordulhat, hogy az alábbi beállításokat is meg kell adnia:  
  - **Always On**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat a VPN-kapcsolathoz, ha a következő események történnek: 
    - Felhasználói bejelentkezés az eszközre
    - Hálózatváltozás az eszközön
    - Az eszköz képernyője ismét bekapcsol, miután ki volt kapcsolva 

  - **Hitelesítési módszer**: Válassza ki, hogyan szeretné hitelesíteni a felhasználókat a VPN-kiszolgálón. A **tanúsítványok** fejlett funkciókkal szolgálnak, például beavatkozás nélküli működés, igény szerinti VPN és alkalmazásonkénti VPN.
  - **Hitelesítő adatok megjegyzése minden bejelentkezéskor**: Válassza a hitelesítő adatok gyorsítótárazását.
  - **Egyéni XML**: Adja meg a VPN-kapcsolat konfigurálására szolgáló egyéni XML-parancsokat.
  - **EAP XML**: Adja meg a VPN-kapcsolat konfigurálásához szükséges EAP XML-parancsokat

### <a name="pulse-secure-example"></a>Pulse Secure-példa

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

### <a name="f5-edge-client-example"></a>F5 Edge Client-példa

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

### <a name="sonicwall-mobile-connect-example"></a>SonicWall Mobile Connect-példa
**Bejelentkezési csoport vagy tartomány**: Ez a tulajdonság nem állítható be a VPN-profilban. Ehelyett a Mobile Connect akkor elemzi ezt az értéket, ha a felhasználónév és a tartomány `username@domain` vagy `DOMAIN\username` formátumban van megadva.

Példa:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

### <a name="checkpoint-mobile-vpn-example"></a>CheckPoint Mobile VPN-példa

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

### <a name="writing-custom-xml"></a>Egyéni XML írása
Az egyéni XML-parancsok írásával kapcsolatban további információt az egyes gyártók VPN-dokumentációjában talál.

További információ az egyéni EAP XML-ek létrehozásáról: [EAP-konfiguráció](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Alkalmazások és adatforgalmi szabályok

- Munkafolyamatok **és alkalmazások hozzárendelése ehhez a VPN-hez**: Akkor engedélyezze ezt a beállítást, ha csak bizonyos alkalmazásokat szeretné használni a VPN-kapcsolat használatára. A választható lehetőségek:

  - **Befejező folyamat hozzárendelése a következő kapcsolatban**: Adja meg a **kapcsolatok folyamatban lévő tartományát**
  - **Alkalmazások hozzárendelése a következő kapcsolatban**: **Ezekhez az alkalmazásokhoz korlátozhatja a VPN-kapcsolatokat**, és hozzáadhat hozzájuk **társított alkalmazásokat**is. A megadott alkalmazások automatikusan a VPN-kapcsolatot használják. Az alkalmazás típusa határozza meg az alkalmazás azonosítóját. Univerzális alkalmazások esetén adja meg a Csomagcsalád nevét. Asztali alkalmazások esetén adja meg az alkalmazás fájlelérési útvonalát.
  >[!IMPORTANT]
  >Azt javasoljuk, hogy tegyen biztonságossá minden, alkalmazásonkénti VPN-ekhez létrehozott alkalmazáslistát. Ha a listát esetleg arra nem jogosult felhasználó módosítja, és Ön így importálja azt az alkalmazásonkénti VPN-alkalmazáslistába, azzal olyan alkalmazásoknak is VPN-elérést nyújthat, amelyeknek eredetileg nem szeretett volna. Az alkalmazáslisták védelmének módja lehet a hozzáférés-vezérlési lista (ACL) létrehozása.

- **A VPN-kapcsolat hálózati forgalmi szabályai**: Válassza ki, hogy mely protokollok és mely helyi & távoli portok és címtartományok engedélyezettek a VPN-kapcsolathoz. Ha nem hoz létre hálózati forgalmi szabályt, minden protokoll, port és címtartomány engedélyezve lesz. Egy szabály létrehozása után a VPN-kapcsolat csak az Ön által a szabályban megadott protokollokat, portokat és címtartományokat használja.

## <a name="conditional-access"></a>Feltételes hozzáférés

- **Feltételes hozzáférés ehhez a VPN-kapcsolathoz**: Engedélyezi az eszköz megfelelőségi folyamatát az ügyféltől. Ha a beállítás engedélyezve van, a VPN-ügyfél kommunikál az Azure Active Directoryval (AD), hogy megszerezze a hitelesítéshez használandó tanúsítványt. A VPN-t tanúsítványalapú hitelesítés használatára kell beállítani, és a VPN-kiszolgálónak megbízhatóként kell felismernie az Azure AD által visszaadott kiszolgálót.

- **Egyszeri bejelentkezés (SSO) alternatív tanúsítvánnyal**: Az eszközök megfelelősége érdekében használjon a VPN-hitelesítési tanúsítványtól eltérő tanúsítványt a Kerberos-hitelesítéshez. A következő beállításokkal rendelkező tanúsítványt adja meg:

  - **Név**: A kibővített kulcshasználat (EKU) neve
  - **Objektumazonosító**: EKU-objektumazonosító
  - **Kiállítói kivonat**: SSO-Tanúsítvány ujjlenyomata

## <a name="dns-settings"></a>DNS-beállítások

- **DNS-utótagok keresési listája**: A **DNS-utótagok**mezőben adja meg a DNS-utótagot, és **adja hozzá**a értéket. Számos utótagot adhat hozzá.

  A DNS-utótagok használatakor a rendszer a hálózati erőforrások rövid nevére keres rá a teljes tartománynév (FQDN) helyett. A rövid névvel történő kereséskor az utótagot automatikusan meghatározza a DNS-kiszolgáló. A `utah.contoso.com` például szerepel a DNS-utótagok listájában. Ön pingeli a következőt: `DEV-comp`. Ebben a forgatókönyvben ez a következőt eredményezi: `DEV-comp.utah.contoso.com`.

  A DNS-utótagok a megadott sorrendben oldódnak fel, amely módosítható. Például a `colorado.contoso.com` és a `utah.contoso.com` is szerepel a DNS-utótagok listájában, és mindkettő rendelkezik `DEV-comp` erőforrással. Mivel a `colorado.contoso.com` az első a listában, ez a következőképp oldódik fel: `DEV-comp.colorado.contoso.com`.
  
  A sorrend módosításához kattintson a DNS-utótag bal oldalán található pontokra, majd húzza az utótagot felülre:

  ![Válassza ki a három pontot, majd húzással helyezze át a DNS-utótagot](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- Névfeloldási **házirend táblája (NRPT) szabályai**: A névfeloldási házirend táblája (NRPT) szabályai határozzák meg, hogy a DNS hogyan oldja fel a neveket a VPN-kapcsolathoz való csatlakozáskor. A VPN-kapcsolat létrejötte után kiválaszthatja, hogy a VPN-kapcsolat mely DNS-kiszolgálókat használja.

  A megadott tartomány feloldásához olyan szabályokat adhat hozzá a táblához, amelyek tartalmazzák a tartományt, a DNS-kiszolgálót, a proxyt és egyéb adatokat. A VPN-kapcsolat ezeket a szabályokat használja, amikor a felhasználók csatlakoznak a megadott tartományokhoz.

  Új szabály hozzáadásához válassza a **Hozzáadás** lehetőséget. Minden egyes kiszolgálóhoz adja meg az alábbi adatokat:

  - **Tartomány**: A szabály alkalmazásához adja meg a teljes tartománynevet (FQDN) vagy egy DNS-utótagot. A DNS-utótagok elején is megadhat egy pontot (.). Például írja be a következőt: `contoso.com` vagy `.allcontososubdomains.com`.
  - **DNS-kiszolgálók**: Adja meg azt az IP-címet vagy DNS-kiszolgálót, amely feloldja a tartományt. Például írja be a következőt: `10.0.0.3` vagy `vpn.contoso.com`.
  - **Proxy**: Adja meg a tartományt feloldó webproxy-kiszolgálót. Például írja be a következőt: `http://proxy.com`.
  - **Automatikus összekapcsolás**: Ha **engedélyezve van**, az eszköz automatikusan csatlakozik a VPN-hez, amikor egy eszköz csatlakozik egy megadott tartományhoz, `contoso.com`például:. Ha **nincs konfigurálva** (alapértelmezett), az eszköz nem csatlakozik automatikusan a VPN-hez.
  - **Állandó**: Ha az **engedélyezve**értékre van állítva, a szabály a névfeloldási házirend táblájában (NRPT) marad mindaddig, amíg a szabályt manuálisan nem távolítja el az eszközről, még a VPN leválasztása után is. Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a VPN-profilban lévő NRPT-szabályok el lesznek távolítva az eszközről, amikor a VPN megszakad.

## <a name="proxy-settings"></a>Proxybeállítások

- **Automatikus konfigurációs parancsfájl**: Egy fájl használatával konfigurálja a proxykiszolgálót. Adja meg a konfigurációs fájlt tartalmazó **Proxykiszolgáló URL-címét**, például `http://proxy.contoso.com`.
- **Címe**: Adja meg a proxykiszolgáló címét, például IP-címet vagy`vpn.contoso.com`
- **Portszám**: Adja meg a proxykiszolgáló által használt TCP-port számát
- **Proxy mellőzése helyi címek esetén**: Ha nem szeretne proxykiszolgálót használni helyi címekhez, válassza az Engedélyezés lehetőséget. Ez a beállítás akkor lép érvénybe, ha a VPN-kiszolgálónak proxykiszolgálóra van szüksége a kapcsolathoz.

## <a name="split-tunneling"></a>Vegyes alagútkezelés

- **Megosztott bújtatás**: **Engedélyezheti** vagy **letilthatja** , hogy az eszközök döntsenek a forgalomtól függően, hogy mely kapcsolatok legyenek használatban. Egy szállodai vendég például a munkahelyi fájlok elérésére a VPN-kapcsolatot, de egyszerű böngészésre a szálloda normál hálózatát használja.
- A **VPN-kapcsolat megosztott bújtatási útvonalai**: Választható útvonalak hozzáadása külső VPN-szolgáltatók számára. Minden kapcsolathoz adja meg a célelőtagot és az előtag méretét.

## <a name="trusted-network-detection"></a>Megbízható hálózati észlelés

**Megbízható hálózati DNS-utótagok**: Ha a felhasználók már csatlakoznak egy megbízható hálózathoz, megtilthatja, hogy az eszközök automatikusan csatlakozzanak más VPN-kapcsolatokhoz.

A **DNS-utótagok**mezőben adjon meg egy megbízható DNS-utótagot, például contoso.com, majd válassza a **Hozzáadás**lehetőséget. Tetszőleges számú utótagot hozzáadhat.

Ha a felhasználó a listában szereplő DNS-utótaghoz csatlakozik, akkor a felhasználó nem fog automatikusan csatlakozni egy másik VPN-kapcsolathoz. A felhasználó továbbra is használja a megadott DNS-utótagok megbízható listáját. A megbízható hálózat továbbra is használatban van, még akkor is, ha vannak ilyenek.

Ha például a felhasználó már csatlakoztatva van egy megbízható DNS-utótaghoz, a rendszer figyelmen kívül hagyja a következő autotriggereket. Pontosabban, a listában szereplő DNS-utótagok megszakítják az összes többi hálózati újraindítást, beleértve a következőket:

- Always on
- Alkalmazás-alapú trigger
- DNS-alapú autotrigger

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md), és [Figyelje annak állapotát](device-profile-monitor.md).

VPN-beállítások konfigurálása [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md)és [MacOS](vpn-settings-macos.md) rendszerű eszközökön.
