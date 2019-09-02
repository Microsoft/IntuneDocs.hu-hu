---
title: VPN-beállítások hozzáadása iOS-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: VPN-konfigurációs profil hozzáadása vagy létrehozása virtuális magánhálózati (VPN) konfigurációs beállításokkal, ideértve a kapcsolat adatait, a hitelesítési módszereket és a vegyes alagútkezelést az alapbeállításoknál; az egyéni VPN-beállításokat azonosítóval, és a kulcs és érték párokat; az alkalmazásonkénti VPN-beállításokat, ideértve a Safari URL-eket és az igény szerinti VPN-eket SSID-vel vagy DNS-keresési tartományokkal; valamint a proxybeállításokat konfigurációs parancsfájl, IP- vagy FQDN-cím belefoglalásához, illetve TCP-port Microsoft Intune-ban való beállításához az iOS-t futtató eszközökhöz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1eee827ace5dae92b485a250e6e4e0b9b426fbe6
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713190"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>VPN-beállítások konfigurálása iOS-eszközökön a Microsoft Intune-ban

A Microsoft Intune számos VPN-beállítást tartalmaz, amelyek telepíthetők az iOS-eszközére. Ezek a beállítások VPN-kapcsolatok létrehozására és konfigurálására használhatók a szervezet hálózatához. Ez a cikk ezeket a beállításokat ismerteti. Egyes beállítások csak egyes VPN-ügyfelekhez állnak rendelkezésre, például a Citrix, Zscaler és másokhoz.

## <a name="connection-type"></a>Kapcsolat típusa

A szállítók az alábbi listából válassza ki a VPN-kapcsolat típusa:

- **Check Point Capsule VPN**
- **A Cisco Legacy AnyConnect**: Alkalmazható [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) alkalmazás 4.0.5x és régebbi.
- **Cisco AnyConnect**: Alkalmazható [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) alkalmazás 4.0.7x és újabb verziók.
- **SonicWall Mobile Connect**
- **F5 Eléréséhez örökölt**: F5 hozzáférés alkalmazás 2.1-es verzió érvényes, és a korábbi verziók.
- **F5 Eléréséhez**: F5 hozzáférés alkalmazás 3.0-s verzió érvényes és újabb verziók.
- **Rendszert futtató Palo Alto Networks (örökölt) GlobalProtect**: Palo Alto hálózatok GlobalProtect 4.1-es és korábbi verziója alkalmazandó.
- **Rendszert futtató Palo Alto Networks GlobalProtect**: Alkalmazható Palo Alto hálózatok GlobalProtect 5.0-s vagy újabb verziója.
- **Pulse Secure**
- **Cisco (IPsec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**: Feltételes hozzáférés használata, vagy lehetővé teszik a felhasználók kihagyhatják a Zscaler bejelentkezési képernyő, majd integrálnia kell Zscaler privát hozzáférést (ZPA) az Azure AD-fiókjával. A lépések részletezését a [Zscaler dokumentációja](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad) tartalmazza. 
- **Egyéni VPN**

> [!NOTE]
> A Cisco, a Citrix, az F5 és a Palo Alto bejelentette, hogy régebbi ügyfeleik nem fognak működni az iOS 12-es verziójával. Ajánlott a lehető leghamarabb áttérni az új alkalmazásokra. További információkat a [Microsoft Intune blogjában](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409) talál.

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások

Az alábbi listában látható beállításokat a kiválasztott VPN-kapcsolat típusa határozza meg.  

- **Kapcsolat neve**: A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Egyéni tartománynév** (csak Zscaler): A Zscaler app jelentkezzen be azzal a tartománnyal, a felhasználók tartoznak a mező előre. Ha a felhasználónév például `Joe@contoso.net`, akkor az alkalmazás megnyílásakor a mezőben statikusan a `contoso.net` tartomány jelenik meg. Ha nem ír be tartománynevet, akkor az Azure Active Directoryban tárolt egyszerű felhasználónév tartomány-része lesz használva.
- **IP-cím vagy FQDN**: Az IP-cím vagy a VPN-kiszolgálóban, amelyhez az eszközök csatlakoznak a teljesen minősített tartománynevét (FQDN). Például írja be a következőt: `192.168.1.1` vagy `vpn.contoso.com`.
- **A szervezet felhő neve** (csak Zscaler): Adja meg a felhő nevét, ahol a szervezet van kiépítve. A nevet megtalálhatja a Zscalerbe való bejelentkezéshez használt URL-címben.  
- **Hitelesítési módszer**: Válassza ki, hogyan hitelesítik magukat az eszközök a VPN-kiszolgáló. 
  - **Tanúsítványok**: A **hitelesítési tanúsítvány**válassza egy meglévő SCEP- vagy PKCS-tanúsítványprofilt a kapcsolat hitelesítéséhez. A [Tanúsítványok konfigurálása](certificates-configure.md) című témakörben találhat útmutatást a tanúsítványprofilokról.
  - **Felhasználónév és jelszó**: A végfelhasználók felhasználónévvel és jelszóval bejelentkezni a VPN-kiszolgálót adjon meg.  

    > [!NOTE]
    > Ha a Cisco IPsec VPN-hez felhasználónevet és jelszót használ hitelesítési módszerként, a titkos kulcsot egy egyéni Apple Configurator-profilon keresztül kell továbbítani.

- **Kizárt URL-címek** (csak Zscaler): A Zscaler VPN való csatlakozáskor a Zscaler felhő kívül a felsorolt URL-címek érhetők el. 

- **Vegyes Alagútkezelés**: **Engedélyezése** vagy **letiltása** , hogy az eszközök választhatnak-e a forgalomtól függően használatához. Egy szállodai vendég például a munkahelyi fájlok elérésére a VPN-kapcsolatot, de egyszerű böngészésre a szálloda normál hálózatát használja.

- **VPN-azonosító** (egyéni VPN, Zscaler és a Citrix): A VPN-alkalmazást használja, és a VPN-szolgáltató megadott azonosítója.
  - **Adja meg a kulcs-érték párokat a szervezet egyéni VPN attribútumainak**: Hozzáadásával vagy importálásával **kulcsok** és **értékek** szabhatja testre a VPN-kapcsolatot. Ne feledje, rendszerint ezeket az értékeket is a VPN-szolgáltató biztosítja.

- **Hálózati hozzáférés-vezérlés (NAC) engedélyezése** (Citrix SSO, F5 hozzáférés): Ha úgy dönt **elfogadom**, az eszköz azonosítója a VPN-profil tartalmazza. Ez az azonosító segítségével a VPN-hitelesítés engedélyezése vagy letiltása a hálózati hozzáférést.

  **F5 hozzáférés használatakor**, ügyeljen arra, hogy:

  - Győződjön meg arról, F5 BIG-IP 13.1.1.5 használ. BIG-IP-14 nem támogatott.
  - BIG-IP integrálása az Intune-nal a NAC. Tekintse meg a [áttekintése: APM konfigurálása az eszköz állapotát ellenőrzi a végpont felügyeleti rendszerekkel](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5-útmutatója.
  - A VPN-profil NAC engedélyezése.

  **A Citrix egyszeri bejelentkezés az átjáró használatakor**, ügyeljen arra, hogy:

  - Győződjön meg arról, Citrix átjáró 12.0.59 használ vagy újabb verziója.
  - Erősítse meg a felhasználók a Citrix SSO 1.1.6 vagy újabb verziója szükséges az eszközeiken.
  - A Citrix átjáró integrálása az Intune-nal a NAC. Tekintse meg a [integrálása a Microsoft Intune/nagyvállalati mobilitási csomag-(LDAP + egyszeri Jelszavas forgatókönyv) NetScaler](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) Citrix telepítési útmutatóban.
  - A VPN-profil NAC engedélyezése.

  **Fontos részleteket**:  

  - Ha engedélyezve van a NAC, a VPN 24 óránként le van választva. Azonnal is újra létrehozza a VPN-t.
  - Az eszköz azonosítója a profil része, de nem az Intune-ban jelenik meg. Ezt az azonosítót a Microsoft sehol sem tárolja és nem osztja meg.

  Az eszköz azonosítója a VPN-partnerek által támogatott, ha a VPN-ügyfél, például a Citrix SSO, beszerezheti az azonosítója. Ezután erősítse meg az eszköz regisztrálva van az Intune lekérdezést végezhet, és ha a VPN-profil megfelelő vagy nem megfelelő.

  - A beállítás eltávolításához hozza létre újra a profilt, és ne válassza ki az **Elfogadom** lehetőséget. Ezt követően végezze el a profil újbóli hozzárendelését.

## <a name="automatic-vpn-settings"></a>Automatikus VPN-beállítások

- **Alkalmazásonkénti VPN**: Lehetővé teszi az alkalmazásonkénti VPN. Lehetővé teszi a VPN-kapcsolat automatikus aktiválását bizonyos alkalmazások megnyitásakor. Ezenkívül társítja az alkalmazásokat ehhez a VPN-profilhoz. További információért lásd az [alkalmazásonkénti VPN beállítására vonatkozó utasításokat iOS-hez](vpn-setting-configure-per-app.md).
  - **A szolgáltató típusát**: Csak a Pulse Secure és az egyéni VPN érhető el.
  - Az iOS-es **alkalmazásonkénti VPN**-profilok Pulse Secure-ral vagy egyéni VPN-nel való használatakor választhat az alkalmazásrétegbeli (alkalmazásproxy) és csomagszintű (csomagalagút) alagútkezelés között. A **Szolgáltatótípus** értékét az alkalmazásrétegbeli alagútkezeléshez állítsa az **alkalmazásproxy** lehetőségre, a csomagrétegbeli alagútkezeléshez pedig állítsa a **csomagalagút** lehetőségre. Ha nem biztos a megfelelő értékben, tekintse meg a VPN-szolgáltató dokumentációját.
  - **A VPN-t a Safari URL-címek**: Adjon hozzá egy vagy több webhely URL-címét. Ezeket az URL-címeket az eszköz Safari böngészőjében megnyitva a VPN-kapcsolat automatikusan létrejön.

- **Igény szerinti VPN**: Ha a VPN-kapcsolat indítása szabályozó feltételes szabályok konfigurálása. Létrehozhat például egy olyan feltételt, amelyben a rendszer csak akkor használja a VPN-kapcsolatot, ha az eszköz nem kapcsolódik a vállalati Wi-Fi-hálózathoz. Vagy hozzon létre egy feltételt. Például ha egy eszköz nem férhet hozzá egy DNS-keresési tartományhoz, adja meg, majd a VPN-kapcsolat nincs elindítva.

  - **SSID-k vagy DNS-keresési tartományok**: Válassza ki, hogy a feltétel vezeték nélküli hálózati **SSID-k**, vagy **DNS-keresési tartományok**. Válassza a **Hozzáadás** lehetőséget egy vagy több SSID vagy keresési tartomány konfigurálásához.
  - **URL-sztringminta**: Választható. Adjon meg egy URL-címet, amelyet a szabály teszteléshez használhat. Ha az eszköz a profilhoz fér hozzá ennek az URL-átirányítás nélkül, a VPN-kapcsolatot is el van indítva. És az eszköz csatlakozik a célként megadott URL-címhez. A felhasználó nem látja a teszthez használt URL-célhely sztringjét. URL-sztring tesztelésére példa lehet egy naplózási webkiszolgáló, amely VPN-kapcsolat létrejötte előtt ellenőrzi az eszköz megfelelőségét. Egy másik lehetőség, hogy az URL-cím ellenőrzi a VPN webhelyhez történő kapcsolódási képességét azelőtt, hogy létrejönne a VPN-kapcsolat az eszköz és a célként megadott URL-cím között.
  - **Tartományi művelet**: Válassza ki a következő lehetőségek közül:
    - Szükség esetén kapcsolódás
    - Soha ne legyen kapcsolódás
  - **A művelet**: Válassza ki a következő lehetőségek közül:
    - Kapcsolódás
    - Kapcsolat kiértékelése
    - Kihagyás
    - Kapcsolat bontása

## <a name="proxy-settings"></a>Proxybeállítások

Ha proxyt használ, konfigurálja a következő beállításokat. A proxybeállítások Zscaler VPN-kapcsolatokhoz nem érhetők el.  

- **Automatikus konfigurációs szkript**: Egy fájl segítségével konfigurálhatja a proxykiszolgálót. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** (például: `http://proxy.contoso.com`).
- **Cím**: Adja meg a proxykiszolgáló teljesen minősített állomásnév IP-címét.
- **Portszám**: Adja meg a proxykiszolgálóhoz társított portszámot.

## <a name="next-step"></a>Következő lépés
[VPN-profilok létrehozása az Intune-ban](vpn-settings-configure.md)  
