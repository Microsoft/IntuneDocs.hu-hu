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
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122872eff92a37c8724fd4a853091e51a0a54c66
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506529"
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

- **Kapcsolat neve**: Adja meg a kapcsolat nevét. A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Kiszolgálók**: Adjon meg egy vagy több olyan VPN-kiszolgálót, amelyhez az eszközök csatlakozni fognak. Kiszolgáló hozzáadásakor az alábbi információkat adhatja meg:
  - **Leírás**: Adja meg a kiszolgáló leíró nevét (például **Contoso VPN-kiszolgáló**)
  - **IP-cím vagy teljes**tartománynév: adja meg annak a VPN-kiszolgálónak az IP-címét vagy teljes tartománynevét (FQDN), amelyhez az eszközök csatlakoznak, például **192.168.1.1** vagy **VPN.contoso.com**
  - **Alapértelmezett kiszolgáló**: Ezt a kiszolgálót engedélyezi alapértelmezett kiszolgálóként, melyet az eszközök kapcsolat létesítéséhez fognak használni. Csak egy kiszolgálót állítson be alapértelmezett kiszolgálóként.
  - **Importálás**: Tallózással keressen meg egy, a kiszolgálók vesszővel tagolt listáját tartalmazó fájlt, melynek formátuma a következő: leírás, IP-cím vagy teljes tartománynév, alapértelmezett kiszolgáló. A kiszolgálók a **Kiszolgálók** listába történő importálásához kattintson az **OK** gombra.
  - **Exportálás**: Exportálja a kiszolgálók listáját egy vesszővel tagolt (CSV-) fájlba

- **IP-címek regisztrálása belső DNS-sel**: Az **Engedélyezés** lehetőség választásával úgy konfigurálja a Windows 10-es VPN-profilt, hogy dinamikusan regisztrálja a VPN-interfészhez a belső DNS-sel hozzárendelt IP-címeket. Ha a **Tiltás** lehetőséget választja, akkor az IP-címek nem lesznek dinamikusan regisztrálva.

- **Kapcsolat típusa**: Az alábbi listából válassza ki a VPN-kapcsolat típusát:

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
  - **Always On**: válassza az **Engedélyezés** lehetőséget a VPN-kapcsolathoz való automatikus csatlakozáshoz, ha a következő események történnek: 
    - Felhasználói bejelentkezés az eszközre
    - Hálózatváltozás az eszközön
    - Az eszköz képernyője ismét bekapcsol, miután ki volt kapcsolva 

  - **Hitelesítési módszer**: Adja meg, hogy hogyan szeretné hitelesíteni a felhasználókat a VPN-kiszolgálón. A **tanúsítványok** fejlett funkciókkal szolgálnak, például beavatkozás nélküli működés, igény szerinti VPN és alkalmazásonkénti VPN.
  - **Hitelesítő adatok megjegyzése minden bejelentkezéskor**: Ezzel a beállítással gyorsítótárazhatja a hitelesítő adatokat.
  - **Egyéni XML**: Adja meg a VPN-kapcsolatot konfiguráló egyéni XML-parancsokat.
  - **EAP XML**: Adja meg a VPN-kapcsolatot konfiguráló EAP XML-parancsokat

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

Például:

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

- **WIP vagy alkalmazások társítása ezzel a VPN-nel**: Engedélyezze ezt a beállítást, ha azt szeretné, hogy csak bizonyos használják a VPN-kapcsolatot. A választható lehetőségek:

  - **WIP társítása ezzel a kapcsolattal**: Adjon meg egy **WIP-tartományt ehhez a kapcsolathoz**
  - **Alkalmazások társítása ezzel a kapcsolattal**: **Korlátozhatja a VPN-kapcsolat ezekhez az alkalmazásokhoz**, majd hozzáadhat **társított alkalmazásokat**. A megadott alkalmazások automatikusan a VPN-kapcsolatot használják. Az alkalmazás típusa határozza meg az alkalmazás azonosítóját. Univerzális alkalmazások esetén adja meg a Csomagcsalád nevét. Asztali alkalmazások esetén adja meg az alkalmazás fájlelérési útvonalát.
  >[!IMPORTANT]
  >Azt javasoljuk, hogy tegyen biztonságossá minden, alkalmazásonkénti VPN-ekhez létrehozott alkalmazáslistát. Ha a listát esetleg arra nem jogosult felhasználó módosítja, és Ön így importálja azt az alkalmazásonkénti VPN-alkalmazáslistába, azzal olyan alkalmazásoknak is VPN-elérést nyújthat, amelyeknek eredetileg nem szeretett volna. Az alkalmazáslisták védelmének módja lehet a hozzáférés-vezérlési lista (ACL) létrehozása.

- **A VPN-kapcsolat hálózati forgalmi szabályai**: Állítsa be, hogy a VPN-kapcsolatnál mely protokollok, valamint melyik helyi és távoli portok és címtartományok lesznek engedélyezve. Ha nem hoz létre hálózati forgalmi szabályt, minden protokoll, port és címtartomány engedélyezve lesz. Egy szabály létrehozása után a VPN-kapcsolat csak az Ön által a szabályban megadott protokollokat, portokat és címtartományokat használja.

## <a name="conditional-access"></a>Conditional Access

- **Feltételes hozzáférés ehhez a VPN-kapcsolathoz**: engedélyezi az eszköz megfelelőségi folyamatát az ügyféltől. Ha a beállítás engedélyezve van, a VPN-ügyfél kommunikál az Azure Active Directoryval (AD), hogy megszerezze a hitelesítéshez használandó tanúsítványt. A VPN-t tanúsítványalapú hitelesítés használatára kell beállítani, és a VPN-kiszolgálónak megbízhatóként kell felismernie az Azure AD által visszaadott kiszolgálót.

- **Egyszeri bejelentkezés (SSO) helyettesítő tanúsítvánnyal**: A Kerberos-hitelesítéshez használttól eltérő tanúsítvány használata az eszközmegfelelőség igazolásához. A következő beállításokkal rendelkező tanúsítványt adja meg:

  - **Név**: A kibővített kulcshasználat (EKU) neve
  - **Objektumazonosító**: Az EKU objektumazonosítója
  - **Kibocsátó kivonata**: Az SSO-tanúsítvány ujjlenyomata

## <a name="dns-settings"></a>DNS-beállítások

- **DNS-utótagok keresési listája**: A **DNS-utótagok** területen adjon meg egy DNS-utótagot, majd válassza a **Hozzáadás** lehetőséget. Számos utótagot adhat hozzá.

  A DNS-utótagok használatakor a rendszer a hálózati erőforrások rövid nevére keres rá a teljes tartománynév (FQDN) helyett. A rövid névvel történő kereséskor az utótagot automatikusan meghatározza a DNS-kiszolgáló. A `utah.contoso.com` például szerepel a DNS-utótagok listájában. Ön pingeli a következőt: `DEV-comp`. Ebben a forgatókönyvben ez a következőt eredményezi: `DEV-comp.utah.contoso.com`.

  A DNS-utótagok a megadott sorrendben oldódnak fel, amely módosítható. Például a `colorado.contoso.com` és a `utah.contoso.com` is szerepel a DNS-utótagok listájában, és mindkettő rendelkezik `DEV-comp` erőforrással. Mivel a `colorado.contoso.com` az első a listában, ez a következőképp oldódik fel: `DEV-comp.colorado.contoso.com`.
  
  A sorrend módosításához kattintson a DNS-utótag bal oldalán található pontokra, majd húzza az utótagot felülre:

  ![Válassza ki a három pontot, majd húzással helyezze át a DNS-utótagot](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- Névfeloldási **házirend táblája (NRPT) szabályai**: névfeloldási házirend tábla (NRPT) szabályai határozzák meg, hogy a DNS hogyan oldja fel a neveket a VPN-kapcsolathoz való csatlakozáskor. A VPN-kapcsolat létrejötte után kiválaszthatja, hogy a VPN-kapcsolat mely DNS-kiszolgálókat használja.

  A megadott tartomány feloldásához olyan szabályokat adhat hozzá a táblához, amelyek tartalmazzák a tartományt, a DNS-kiszolgálót, a proxyt és egyéb adatokat. A VPN-kapcsolat ezeket a szabályokat használja, amikor a felhasználók csatlakoznak a megadott tartományokhoz.

  Új szabály hozzáadásához válassza a **Hozzáadás** lehetőséget. Minden egyes kiszolgálóhoz adja meg az alábbi adatokat:

  - **Tartomány**: a szabály alkalmazásához adja meg a teljes tartománynevet (FQDN) vagy egy DNS-utótagot. A DNS-utótagok elején is megadhat egy pontot (.). Például írja be a következőt: `contoso.com` vagy `.allcontososubdomains.com`.
  - **DNS-kiszolgálók**: adja meg azt az IP-címet vagy DNS-kiszolgálót, amely feloldja a tartományt. Például írja be a következőt: `10.0.0.3` vagy `vpn.contoso.com`.
  - **Proxy**: adja meg azt a webproxy-kiszolgálót, amely feloldja a tartományt. Például írja be a következőt: `http://proxy.com`.
  - **Automatikus csatlakozás**: Ha **engedélyezve van**, az eszköz automatikusan csatlakozik a VPN-hez, amikor egy eszköz csatlakozik egy megadott tartományhoz, például `contoso.com`. Ha **nincs konfigurálva** (alapértelmezett), az eszköz nem csatlakozik automatikusan a VPN-hez.
  - **Állandó**: Ha az Engedélyezve értékre **van**állítva, a szabály a névfeloldási házirend táblájában (NRPT) marad mindaddig, amíg a szabályt manuálisan nem távolítja el az eszközről, még a VPN leválasztása után is. Ha a **nincs konfigurálva** értékre van állítva (alapértelmezett), a VPN-profilban lévő NRPT-szabályok el lesznek távolítva az eszközről, amikor a VPN megszakad.

## <a name="proxy-settings"></a>Proxybeállítások

- **Automatikus konfigurációs szkript**: A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **Proxykiszolgáló URL-címét**, például `http://proxy.contoso.com`.
- **Cím**: Adja meg a proxykiszolgáló címét, amely egy IP-cím vagy egy `vpn.contoso.com`
- **Portszám** – Adja meg a proxykiszolgáló TCP-portszámát.
- **Proxy megkerülése helyi címeknél**: Ha nem szeretne proxykiszolgálót használni a helyi címekhez, válassza az Engedélyezés lehetőséget. Ez a beállítás akkor lép érvénybe, ha a VPN-kiszolgálónak proxykiszolgálóra van szüksége a kapcsolathoz.

## <a name="split-tunneling"></a>Vegyes alagútkezelés

- **Bújtatás megosztása**: Az **Engedélyezés** vagy a **Letiltás** beállítással szabályozhatja, hogy az eszközök választhatnak-e a forgalomtól függően a kapcsolatok közül. Egy szállodai vendég például a munkahelyi fájlok elérésére a VPN-kapcsolatot, de egyszerű böngészésre a szálloda normál hálózatát használja.
- **A VPN-kapcsolat megosztott protokollbújtatási útvonalai**: Választható útvonalak hozzáadása külső VPN-szolgáltatók számára. Minden kapcsolathoz adja meg a célelőtagot és az előtag méretét.

## <a name="trusted-network-detection"></a>Megbízható hálózati észlelés

**Megbízható hálózati DNS-utótagok**: Ha a felhasználók már csatlakoznak egy megbízható hálózathoz, megakadályozhatja, hogy az eszközök automatikusan csatlakozzanak más VPN-kapcsolatokhoz.

A **DNS-utótagok**mezőben adjon meg egy megbízható DNS-utótagot, például contoso.com, majd válassza a **Hozzáadás**lehetőséget. Tetszőleges számú utótagot hozzáadhat.

Ha a felhasználó a listában szereplő DNS-utótaghoz csatlakozik, akkor a felhasználó nem fog automatikusan csatlakozni egy másik VPN-kapcsolathoz. A felhasználó továbbra is használja a megadott DNS-utótagok megbízható listáját. A megbízható hálózat továbbra is használatban van, még akkor is, ha vannak ilyenek.

Ha például a felhasználó már csatlakoztatva van egy megbízható DNS-utótaghoz, a rendszer figyelmen kívül hagyja a következő autotriggereket. Pontosabban, a listában szereplő DNS-utótagok megszakítják az összes többi hálózati újraindítást, beleértve a következőket:

- Always on
- Alkalmazás-alapú trigger
- DNS-alapú autotrigger

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md), és [Figyelje annak állapotát](device-profile-monitor.md).

VPN-beállítások konfigurálása [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md)és [MacOS](vpn-settings-macos.md) rendszerű eszközökön.
