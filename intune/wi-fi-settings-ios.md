---
title: Wi-Fi-beállítások konfigurálása iOS-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Létrehozhat vagy hozzáadhat egy eszközkonfigurációs Wi-Fi-profilt az iOS-eszközökhöz. Megtekintheti a Microsoft Intune különböző beállításait, beleértve a tanúsítványok hozzáadását, az EAP-típusok kiválasztását és a hitelesítési módszer kiválasztását.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b864689bce1814eba78dc2435905d4df82e8c0
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69022680"
---
# <a name="add-wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>iOS-eszközökre vonatkozó Wi-Fi-beállítások hozzáadása a Microsoft Intune-ban

Adott Wi-Fi-beállításokkal rendelkező profilt hozhat létre, majd ezt a profilt üzembe helyezheti az iOS-eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, a PKS- vagy SCEP-tanúsítványok hozzáadását és egyéb lehetőségeket.

Ezek a Wi-Fi-beállítások két kategóriába vannak elkülönítve: Alapszintű beállítások és nagyvállalati szintű beállítások.

Ez a cikk ezeket a beállításokat ismerteti.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](device-profile-create.md).

## <a name="basic-profiles"></a>Alapszintű profilok

- **Wi-Fi típusa**: Válassza a **Basic** (Egyszerű) lehetőséget.
- **Hálózat neve**: Adja meg a Wi-Fi kapcsolat nevét. Ez a név jelenik meg a felhasználók számára, amikor az eszközön rendelkezésre álló kapcsolatok listáját böngészik.
- **SSID**: A **szolgáltatáskészlet-azonosító rövid értéke**. Ez a tulajdonság azon vezeték nélküli hálózat valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált hálózatnevet látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, ha a hálózat SSID azonosítója nincs közvetítve. Válassza a **Letiltás** lehetőséget, ha a hálózat SSID-je sugározva és látható.
- **Biztonság típusa**: Válassza ki a Wi-Fi-hálózat hitelesítéséhez használandó biztonsági protokollt. A választható lehetőségek:

  - **Megnyitás (nincs hitelesítés)** : Csak akkor használja ezt a beállítást, ha a hálózat nem biztonságos.
  - **WPA/WPA2-Personal**: Adja meg a jelszót **előmegosztott kulcsban**. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként.
  - **Adattitkosítás**

- **Proxybeállítások**: A választható lehetőségek:
  - **Nincs**: Nincsenek proxybeállítások konfigurálva.
  - **Manuális**: Adja meg a **proxykiszolgáló címét** IP-címként és portszámként.
  - **Automatikus**: Egy fájl használatával konfigurálja a proxykiszolgálót. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** (például: `http://proxy.contoso.com`).

## <a name="enterprise-profiles"></a>Vállalati profilok

- **Wi-Fi típusa**: Válassza a **vállalat**lehetőséget.
- **SSID**: A **szolgáltatáskészlet-azonosító rövid értéke**. Ez a tulajdonság azon vezeték nélküli hálózat valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált hálózatnevet látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget a hálózat elrejtéséhez az eszközön elérhető hálózatok listájából. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.

- **EAP-típus**: Válassza ki a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez használt bővíthető hitelesítési protokoll (EAP) típust. A választható lehetőségek:

  - **EAP-FAST**: Adja meg a **védett hozzáférési hitelesítő adatok (PAC) beállításait**. Ez a lehetőség védett hozzáférési hitelesítő adatok használatával hoz létre egy hitelesített csatornát az ügyfél és a hitelesítési kiszolgáló között. A választható lehetőségek:
    - **Ne használja (PAC)**
    - **Használat (PAC)** : Ha létezik meglévő PAC-fájl, használja azt.
    - **PAC használata és kiépítése**: Hozza létre és adja hozzá a PAC-fájlt az eszközeihez.
    - **PAC használata és kiépítése névtelenül**: A PAC-fájlt a kiszolgáló hitelesítése nélkül hozza létre és adja hozzá az eszközeihez.

  - **EAP-SIM**

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatósági** - **tanúsítványok kiszolgálójának nevei**: **Adjon hozzá** egy vagy több köznapi nevet a megbízható HITELESÍTÉSSZOLGÁLTATÓ (CA) által kiállított tanúsítványokban a vezeték nélküli hálózati hozzáférési kiszolgálókhoz. Adja `mywirelessserver.contoso.com` meg például a következőt: vagy `mywirelessserver`. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Kiszolgáló-ellenőrzés**főtanúsítványa: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány lehetővé teszi az ügyfél számára, hogy megbízzon a vezeték nélküli hálózati hozzáférési kiszolgáló tanúsítványán.

      Válassza ki **OK** a módosítások mentéséhez.

    - Ügyfél-hitelesítési ügyféltanúsítvány ügyfél **-hitelesítéshez (identitás-tanúsítvány):**  -  Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      Válassza ki **OK** a módosítások mentéséhez.

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatósági** - **tanúsítványok kiszolgálójának nevei**: **Adjon hozzá** egy vagy több köznapi nevet a megbízható HITELESÍTÉSSZOLGÁLTATÓ (CA) által kiállított tanúsítványokban a vezeték nélküli hálózati hozzáférési kiszolgálókhoz. Adja `mywirelessserver.contoso.com` meg például a következőt: vagy `mywirelessserver`. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Kiszolgáló-ellenőrzés**főtanúsítványa: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány lehetővé teszi az ügyfél számára, hogy megbízzon a vezeték nélküli hálózati hozzáférési kiszolgáló tanúsítványán.

      Válassza ki **OK** a módosítások mentéséhez.

    - **Ügyfél-hitelesítés** – Válasszon egy **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolatok hitelesítésének módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva.

          A választható lehetőségek: **Titkosítatlan jelszó (PAP)** , **Challenge Handshake Authentication Protocol (CHAP)** , **Microsoft CHAP (ms-CHAP)** vagy **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

        Válassza ki **OK** a módosítások mentéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **LEAP**

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgálói megbízhatósági** - **tanúsítványok kiszolgálójának nevei**: **Adjon hozzá** egy vagy több köznapi nevet a megbízható HITELESÍTÉSSZOLGÁLTATÓ (CA) által kiállított tanúsítványokban a vezeték nélküli hálózati hozzáférési kiszolgálókhoz. Adja `mywirelessserver.contoso.com` meg például a következőt: vagy `mywirelessserver`. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Kiszolgáló-ellenőrzés**főtanúsítványa: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány lehetővé teszi az ügyfél számára, hogy megbízzon a vezeték nélküli hálózati hozzáférési kiszolgáló tanúsítványán.

      Válassza ki **OK** a módosítások mentéséhez.

    - **Ügyfél-hitelesítés** – Válasszon egy **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. 

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

        Válassza ki **OK** a módosítások mentéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

- **Proxybeállítások**: A választható lehetőségek:
  - **Nincs**: Nincsenek proxybeállítások konfigurálva.
  - **Manuális**: Adja meg a **proxykiszolgáló címét** IP-címként és portszámként.
  - **Automatikus**: Egy fájl használatával konfigurálja a proxykiszolgálót. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** (például: `http://proxy.contoso.com`).

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. A következő lépés a [profil hozzárendelése](device-profile-assign.md).

## <a name="more-resources"></a>További források

[Wi-Fi-beállítások áttekintése](wi-fi-settings-configure.md), beleértve a többi rendelkezésre álló platformot is.
