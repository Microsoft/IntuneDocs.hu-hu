---
title: VPN-beállítások konfigurálása iOS-eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
description: VPN-konfigurációs profil hozzáadása vagy létrehozása virtuális magánhálózati (VPN) konfigurációs beállításokkal, ideértve a kapcsolat adatait, a hitelesítési módszereket és a vegyes alagútkezelést az alapbeállításoknál; az egyéni VPN-beállításokat azonosítóval, és a kulcs és érték párokat; az alkalmazásonkénti VPN-beállításokat, ideértve a Safari URL-eket és az igény szerinti VPN-eket SSID-vel vagy DNS-keresési tartományokkal; valamint a proxybeállításokat konfigurációs parancsfájl, IP- vagy FQDN-cím belefoglalásához, illetve TCP-port Microsoft Intune-ban való beállításához az iOS-t futtató eszközökhöz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e45d51feb91e0e188971133185ac0f0f13e5b1f4
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74781141"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>VPN-beállítások hozzáadása iOS-eszközökön Microsoft Intune

A Microsoft Intune számos VPN-beállítást tartalmaz, amelyek telepíthetők az iOS-eszközére. Ezek a beállítások VPN-kapcsolatok létrehozására és konfigurálására használhatók a szervezet hálózatához. Ez a cikk ezeket a beállításokat ismerteti. Egyes beállítások csak egyes VPN-ügyfelekhez állnak rendelkezésre, például a Citrix, Zscaler és másokhoz.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](vpn-settings-configure.md).

> [!NOTE]
> Ezek a beállítások minden regisztrációs típushoz elérhetők. A regisztrációs típusokkal kapcsolatos további információkért lásd: [iOS-regisztráció](../enrollment/ios-enroll.md).

## <a name="connection-type"></a>Kapcsolat típusa

Válassza ki a VPN-kapcsolat típusát a következő szállítók listájáról:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**: A [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) alkalmazás 4.0.5x és annál korábbi verzióihoz használható.
- **Cisco AnyConnect**: A [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) alkalmazás 4.0.7x és annál újabb verzióihoz használható.
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: Az F5 Access alkalmazás 2.1 és annál korábbi verzióihoz használható.
- **F5 Access**: Az F5 Access alkalmazás 3.0 és annál újabb verzióihoz használható.
- **Palo Alto Networks GlobalProtect (Legacy)** : A Palo Alto Networks GlobalProtect alkalmazás 4.1 és annál korábbi verzióihoz használható.
- **Palo Alto Networks GlobalProtect**: A Palo Alto Networks GlobalProtect alkalmazás 5.0 és annál újabb verzióihoz használható.
- **Pulse Secure**
- **Cisco (IPsec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**: a feltételes hozzáférés használatához, vagy a Zscaler bejelentkezési képernyő megkerülésének engedélyezése a felhasználók számára, az Azure ad-fiókjával integrálnia kell a Zscaler privát hozzáférését (ZPA). A lépések részletezését a [Zscaler dokumentációja](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad) tartalmazza. 
- **IKEv2**: a [IKEv2 beállításai](#ikev2-settings) (ebben a cikkben) a tulajdonságokat ismertetik.
- **Egyéni VPN**

> [!NOTE]
> A Cisco, a Citrix, az F5 és a Palo Alto bejelentette, hogy régebbi ügyfeleik nem fognak működni az iOS 12-es verziójával. Ajánlott a lehető leghamarabb áttérni az új alkalmazásokra. További információkat a [Microsoft Intune blogjában](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409) talál.

## <a name="base-vpn-settings"></a>Alapvető VPN-beállítások

Az alábbi listában látható beállításokat a kiválasztott VPN-kapcsolat típusa határozza meg.  

- **Kapcsolat neve**: A végfelhasználók akkor látják ezt a nevet, amikor megkeresik a rendelkezésre álló VPN-kapcsolatok listáját az eszközükön.
- **Egyéni tartománynév** (csak Zscaler): előre feltölti a Zscaler alkalmazás bejelentkezési mezőjét azzal a tartománnyal, amelyhez a felhasználók tartoznak. Ha a felhasználónév például `Joe@contoso.net`, akkor az alkalmazás megnyílásakor a mezőben statikusan a `contoso.net` tartomány jelenik meg. Ha nem ír be tartománynevet, akkor az Azure Active Directoryban tárolt egyszerű felhasználónév tartomány-része lesz használva.
- **IP-cím vagy teljes tartománynév**: Annak a VPN-kiszolgálónak az IP-címe vagy teljes tartományneve (FQDN), amelyhez az eszközök csatlakoznak. Például írja be a következőt: `192.168.1.1` vagy `vpn.contoso.com`.
- **Felhőbeli cégnév** (csak Zscaler): Írja be annak a felhőnek a nevét, amelyben a vállalata ki van építve. A nevet megtalálhatja a Zscalerbe való bejelentkezéshez használt URL-címben.  
- **Hitelesítési mód**: Válassza ki, hogy miképpen hitelesítik magukat az eszközök a VPN-kiszolgálón. 
  - **Tanúsítványok**: A **Hitelesítési tanúsítvány** szakaszban válasszon egy meglévő SCEP- vagy PKCS-tanúsítványprofilt a kapcsolat hitelesítéséhez. A [Tanúsítványok konfigurálása](../protect/certificates-configure.md) című témakörben találhat útmutatást a tanúsítványprofilokról.
  - **Felhasználónév és jelszó**: A végfelhasználóknak felhasználónevet és jelszót kell megadniuk, ha szeretnének bejelentkezni a VPN-kiszolgálóra.  

    > [!NOTE]
    > Ha a Cisco IPsec VPN-hez felhasználónevet és jelszót használ hitelesítési módszerként, a titkos kulcsot egy egyéni Apple Configurator-profilon keresztül kell továbbítani.

  - **Származtatott hitelesítő adatok**: a felhasználó intelligens kártyáján származtatott tanúsítvány használata. Ha nincs beállítva származtatott hitelesítő adat kiállítója, az Intune kérni fogja, hogy adjon hozzá egyet. További információ: [származtatott hitelesítő adatok használata Microsoft Intuneban](../protect/derived-credentials.md).

- **Kizárt URL-címek** (csak Zscaler): A Zscaler VPN-hez csatlakozva a felsorolt URL-címek érhetők el a Zscaler-felhőn kívülről. 

- **Bújtatás megosztása**: Az **Engedélyezés** vagy a **Letiltás** beállítással szabályozhatja, hogy az eszközök választhatnak-e a forgalomtól függően a kapcsolatok közül. Egy szállodai vendég például a munkahelyi fájlok elérésére a VPN-kapcsolatot, de egyszerű böngészésre a szálloda normál hálózatát használja.

- **VPN-azonosító** (egyéni VPN, Zscaler és Citrix): a használt VPN-alkalmazás azonosítója, amelyet a VPN-szolgáltató biztosít.
  - **Kulcs-érték párok megadása vállalata egyéni VPN attribútumainak konfigurálásához**: **Kulcsok** és **Értékek** hozzáadásával vagy importálásával szabhatja testre a VPN-kapcsolatot. Ne feledje, rendszerint ezeket az értékeket is a VPN-szolgáltató biztosítja.

- **Hálózati hozzáférés-vezérlés engedélyezése** (Citrix SSO, F5 Access): Ha az **Elfogadom**lehetőséget választja, az eszköz azonosítója szerepel a VPN-profilban. Ez az azonosító a VPN hitelesítéséhez használható a hálózati hozzáférés engedélyezéséhez vagy letiltásához.

  **F5-hozzáférés használata esetén**ügyeljen a következőre:

  - Erősítse meg, hogy az F5 BIG-IP 13.1.1.5 használja. A BIG-IP 14 nem támogatott.
  - A BIG-IP integrálása az Intune-nal a NAC-hoz. Tekintse [meg az Áttekintés: az APM konfigurálása eszköz-testhelyzeti ellenőrzésekhez az Endpoint Management Systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 útmutatót.
  - Engedélyezze a NAC-t a VPN-profilban.

  **Ha a CITRIX SSO-t átjáróval használja**, ügyeljen arra, hogy:

  - Erősítse meg, hogy a Citrix Gateway 12.0.59 vagy újabb verzióját használja.
  - Erősítse meg, hogy a felhasználók Citrix SSO 1.1.6 vagy újabb verzióra vannak telepítve az eszközökön.
  - A Citrix Gateway integrálása az Intune-nal a NAC-nal. Tekintse meg az [integrációs Microsoft Intune/Enterprise Mobility Suite NetScaler (LDAP + OTP-forgatókönyv)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) Citrix telepítési útmutatót.
  - Engedélyezze a NAC-t a VPN-profilban.

  **Fontos részletek**:  

  - Ha a NAC engedélyezve van, a VPN-kapcsolat 24 óránként megszakad. A VPN-t azonnal újra lehet kapcsolni.
  - Az eszköz azonosítója a profil része, de nem jelenik meg az Intune-ban. Ezt az azonosítót a Microsoft sehol sem tárolja és nem osztja meg.

  Az eszköz AZONOSÍTÓját támogató VPN-partnerek esetében a VPN-ügyfél (például a Citrix SSO) lekérheti az azonosítót. Ezután lekérdezheti az Intune-t az eszköz regisztrálásának megerősítéséhez, és ha a VPN-profil megfelelő vagy nem megfelelő.

  - A beállítás eltávolításához hozza létre újra a profilt, és ne válassza ki az **Elfogadom** lehetőséget. Ezt követően végezze el a profil újbóli hozzárendelését.

## <a name="ikev2-settings"></a>IKEv2-beállítások

Ezek a beállítások akkor érvényesek, ha a **kapcsolattípus** > **IKEv2**lehetőséget választja.

- **Távoli azonosító**: adja meg a IKEv2-kiszolgáló hálózati IP-címét, FQDN-jét, USERFQDN vagy ASN1DN. Például írja be a következőt: `10.0.0.3` vagy `vpn.contoso.com`. Általában ugyanazt az értéket adja meg, mint a [**kapcsolatok neve**](#base-vpn-settings) (ebben a cikkben). Ez azonban a IKEv2-kiszolgáló beállításaitól függ.

- **Ügyfél-hitelesítés típusa**: válassza ki, hogyan hitelesíti a VPN-ügyfelet a VPN-ben. A választható lehetőségek:
  - **Felhasználói hitelesítés** (alapértelmezett): felhasználói hitelesítő adatok hitelesítése a VPN-ben.
  - **Számítógép-hitelesítés**: az eszköz hitelesítő adatai hitelesítve vannak a VPN-ben.

- **Hitelesítési módszer**: válassza ki a kiszolgálónak küldendő ügyfél-hitelesítő adatok típusát. A választható lehetőségek:
  - **Tanúsítványok**: egy meglévő tanúsítványsablont használ a VPN-hitelesítéshez. Győződjön meg arról, hogy a tanúsítvány profilja már hozzá van rendelve a felhasználóhoz vagy az eszközhöz. Ellenkező esetben a VPN-kapcsolat meghiúsul.
    - **Tanúsítvány típusa**: válassza ki a tanúsítvány által használt titkosítási típust. Győződjön meg arról, hogy a VPN-kiszolgáló úgy van konfigurálva, hogy fogadja el az ilyen típusú tanúsítványokat. A választható lehetőségek:
      - **RSA** (alapértelmezett)
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - **Felhasználónév és jelszó** (csak felhasználói hitelesítés esetén): amikor a felhasználók csatlakoznak a VPN-hez, a rendszer kéri a felhasználónevet és a jelszót.
  - **Közös titok** (csak gépi hitelesítés esetén): lehetővé teszi a VPN-kiszolgálónak küldendő közös titok megadását.
    - **Közös titkos**kulcs: adja meg a közös titkot, más néven előmegosztott kulcsot (PSK). Győződjön meg arról, hogy az érték megegyezik a VPN-kiszolgálón konfigurált közös titokkal.

- **Kiszolgálói tanúsítvány kiállítójának köznapi neve**: lehetővé teszi, hogy a VPN-kiszolgáló hitelesítse magát a VPN-ügyfélen. Adja meg az eszköz VPN-ügyfelének eljuttatott VPN-kiszolgálói tanúsítvány tanúsítvány-kiállítói köznapi nevét (CN). Győződjön meg arról, hogy a CN-érték megegyezik a VPN-kiszolgáló konfigurációjával. Ellenkező esetben a VPN-kapcsolat meghiúsul.
- **Kiszolgálói tanúsítvány köznapi neve**: adja meg a tanúsítványhoz tartozó CN-t. Ha üresen hagyja, a rendszer a távoli azonosító értékét használja.

- **Elhalt társ-észlelési arány**: válassza ki, hogy a VPN-ügyfél milyen gyakran ellenőrizze, hogy a VPN-alagút aktív-e. A választható lehetőségek:
  - **Nincs konfigurálva**: az iOS rendszer alapértelmezett beállítását használja, amely a **közepes**érték megadásával megegyező lehet.
  - **Nincs**: letiltja a kézbesítetlen társ-észlelést.
  - **Alacsony**: egy életben tartási üzenetet küld 30 percenként.
  - **Közepes** (alapértelmezett): 10 percenként elküld egy életben tartási üzenetet.
  - **Magas**: minden 60 másodpercenként elküld egy életben tartási üzenetet.

- **TLS-verzió minimális**száma: adja meg a használni kívánt TLS-verziót. Adja meg `1.0`, `1.1`vagy `1.2`. Ha üresen hagyja, a rendszer a `1.0` alapértelmezett értékét használja.
- **TLS-verzió maximális**száma: adja meg a használni kívánt TLS-verziót. Adja meg `1.0`, `1.1`vagy `1.2`. Ha üresen hagyja, a rendszer a `1.2` alapértelmezett értékét használja.
- **Tökéletes továbbítási titoktartás**: válassza az **Engedélyezés** lehetőséget a tökéletes továbbítási titoktartás (PFS) bekapcsolásához. A PFS egy olyan IP-biztonsági szolgáltatás, amely csökkenti annak hatását, ha egy munkamenetkulcs biztonsága sérül. A **Letiltás** (alapértelmezett) nem használ PFS-t.
- **Tanúsítvány visszavonásának ellenőrzése**: válassza az **Engedélyezés** lehetőséget, hogy a rendszer ne vonja vissza a tanúsítványokat, mielőtt engedélyezné a VPN-kapcsolat sikerességét. Ez az ellenőrzési lehetőség a legjobb megoldás. Ha a VPN-kiszolgáló túllépi az időkorlátot a tanúsítvány visszavonásának meghatározása előtt, akkor a rendszer a hozzáférést is megadja. A **Letiltás** (alapértelmezett) nem vizsgálja a visszavont tanúsítványokat.

- A **biztonsági társítás paramétereinek konfigurálása**: **nincs konfigurálva** (alapértelmezés) az iOS rendszer alapértelmezett értékeit használja. Válassza az **Engedélyezés** lehetőséget a biztonsági TÁRSÍTÁSOK VPN-kiszolgálóval való létrehozásakor használt paraméterek megadásához:
  - **Titkosítási algoritmus**: válassza ki a kívánt algoritmust:
    - DES
    - 3DES
    - AES-128
    - AES-256 (alapértelmezett)
    - AES-128 – GCM
    - AES-256 – GCM
  - **Integritási algoritmus**: válassza ki a kívánt algoritmust:
    - SHA1 – 96
    - SHA1 – 160
    - SHA2 – 256 (alapértelmezett)
    - SHA2 – 384
    - SHA2 – 512
  - **Diffie-Hellman csoport**: válassza ki a kívánt csoportot. Az alapértelmezett érték a Group `2`.
  - **Élettartam** (perc): válassza ki, hogy mennyi ideig marad aktív a biztonsági társítás a kulcsok elforgatása előtt. `10` és `1440` közötti egész értéket adjon meg (1440 perc 24 óra). Az alapértelmezett érték a `1440`.

- **Külön paraméterek beállítása a gyermek biztonsági társításokhoz**: az iOS lehetővé teszi, hogy külön paramétereket konfiguráljon az IKE-kapcsolathoz és az alárendelt kapcsolatokhoz. 

  **Nincs konfigurálva** (alapértelmezés) az előző **biztonsági társítás paramétereinek** beállítása beállításban megadott értékeket használja. Válassza az **Engedélyezés** lehetőséget a *gyermek* biztonsági társítások VPN-kiszolgálóval való létrehozásakor használt paraméterek megadásához:
  - **Titkosítási algoritmus**: válassza ki a kívánt algoritmust:
    - DES
    - 3DES
    - AES-128
    - AES-256 (alapértelmezett)
    - AES-128 – GCM
    - AES-256 – GCM
  - **Integritási algoritmus**: válassza ki a kívánt algoritmust:
    - SHA1 – 96
    - SHA1 – 160
    - SHA2 – 256 (alapértelmezett)
    - SHA2 – 384
    - SHA2 – 512
  - **Diffie-Hellman csoport**: válassza ki a kívánt csoportot. Az alapértelmezett érték a Group `2`.
  - **Élettartam** (perc): válassza ki, hogy mennyi ideig marad aktív a biztonsági társítás a kulcsok elforgatása előtt. `10` és `1440` közötti egész értéket adjon meg (1440 perc 24 óra). Az alapértelmezett érték a `1440`.

## <a name="automatic-vpn-settings"></a>Automatikus VPN-beállítások

- **Alkalmazásonkénti VPN**: Engedélyezi az alkalmazásonkénti VPN használatát. Lehetővé teszi a VPN-kapcsolat automatikus aktiválását bizonyos alkalmazások megnyitásakor. Ezenkívül társítja az alkalmazásokat ehhez a VPN-profilhoz. Az alkalmazáson belüli VPN használata nem támogatott a IKEv2 esetében. További információért lásd az [alkalmazásonkénti VPN beállítására vonatkozó utasításokat iOS-hez](vpn-setting-configure-per-app.md). 
  - **Szolgáltatótípus**: Csak a Pulse Secure-hoz és az egyéni VPN-hez érhető el.
  - Az iOS-es **alkalmazásonkénti VPN**-profilok Pulse Secure-ral vagy egyéni VPN-nel való használatakor választhat az alkalmazásrétegbeli (alkalmazásproxy) és csomagszintű (csomagalagút) alagútkezelés között. A **Szolgáltatótípus** értékét az alkalmazásrétegbeli alagútkezeléshez állítsa az **alkalmazásproxy** lehetőségre, a csomagrétegbeli alagútkezeléshez pedig állítsa a **csomagalagút** lehetőségre. Ha nem biztos a megfelelő értékben, tekintse meg a VPN-szolgáltató dokumentációját.
  - **A VPN-t aktiváló Safari URL-címek**: Megadhat egy vagy több webhelycímet. Ezeket az URL-címeket az eszköz Safari böngészőjében megnyitva a VPN-kapcsolat automatikusan létrejön.

- **Igény szerinti VPN**: Ezzel a beállítással feltételes szabályokat állíthat be, melyek a VPN-kapcsolat indítását vezérlik. Létrehozhat például egy olyan feltételt, amelyben a rendszer csak akkor használja a VPN-kapcsolatot, ha az eszköz nem kapcsolódik a vállalati Wi-Fi-hálózathoz. Vagy hozzon létre egy feltételt. Ha például egy eszköz nem fér hozzá egy megadott DNS-keresési tartományhoz, akkor a VPN-kapcsolat nem indul el.

  - **SSID-k vagy DNS-keresési tartományok**: Megadhatja, hogy ez a feltétel vezeték nélküli hálózatok **SSID-it** használja, vagy **DNS-keresési tartományokat**. Válassza a **Hozzáadás** lehetőséget egy vagy több SSID vagy keresési tartomány konfigurálásához.
  - **Az URL-cím sztringjének vizsgálata**: Nem kötelező. Adjon meg egy URL-címet, amelyet a szabály teszteléshez használhat. Ha az eszköz átirányítás nélkül fér hozzá az URL-címhez, akkor a VPN-kapcsolat elindult. És az eszköz csatlakozik a célként megadott URL-címhez. A felhasználó nem látja a teszthez használt URL-célhely sztringjét.

    Egy URL-karakterlánc-mintavétel például egy olyan webes naplózási webkiszolgáló URL-címe, amely a VPN csatlakoztatása előtt ellenőrzi az eszköz megfelelőségét. Az URL-cím azt is ellenőrzi, hogy a VPN képes-e csatlakozni a helyhez, mielőtt a VPN-en keresztül csatlakoztatná az eszközt a célként megadott URL-címhez.
.
  - **Tartományi művelet**: Válasszon a következő lehetőségek közül:
    - Szükség esetén kapcsolódás
    - Soha ne legyen kapcsolódás
  - **Művelet**: Válasszon a következő lehetőségek közül:
    - Kapcsolódás
    - Kapcsolat kiértékelése
    - Mellőzés
    - Kapcsolat bontása

## <a name="proxy-settings"></a>Proxybeállítások

Ha proxyt használ, konfigurálja a következő beállításokat. A proxybeállítások Zscaler VPN-kapcsolatokhoz nem érhetők el.  

- **Automatikus konfigurációs szkript**: A proxykiszolgálót egy konfigurációs fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** (például: `http://proxy.contoso.com`).
- **Cím**: Adja meg a proxykiszolgáló IP-címét vagy teljesen minősített állomásnevét.
- **Portszám**: Adja meg a proxykiszolgálóhoz társított portszámot.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

VPN-beállítások konfigurálása [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)és [Windows 10 rendszerű](vpn-settings-windows-10.md) eszközökön.
