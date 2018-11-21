---
title: Wi-Fi-beállítások konfigurálása macOS-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Létrehozhat vagy hozzáadhat egy eszközkonfigurációs Wi-Fi-profilt a macOS-eszközökhöz. Megtekintheti a Microsoft Intune különböző beállításait, beleértve a tanúsítványok hozzáadását, az EAP-típusok kiválasztását és a hitelesítési módszer kiválasztását.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6602a5507e4357899259722a7a8d095d540e2826
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181139"
---
# <a name="add-wi-fi-settings-for-macos-devices-in-microsoft-intune"></a>macOS-eszközökre vonatkozó Wi-Fi-beállítások hozzáadása a Microsoft Intune-ban

Adott Wi-Fi-beállításokkal rendelkező profilt hozhat létre, majd ezt a profilt üzembe helyezheti a macOS-eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, a PKS- vagy SCEP-tanúsítványok hozzáadását és egyéb lehetőségeket.

Ezek a Wi-Fi-beállítások két kategóriára vannak osztva, alapszintű és vállalati szintű beállításokra.

Ez a cikk ezeket a beállításokat ismerteti.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](device-profile-create.md).

## <a name="basic-profiles"></a>Alapszintű profilok

- **Wi-Fi típusa**: válassza az **Alapszintű** lehetőséget.
- **Hálózat neve**: Adja meg a Wi-Fi-kapcsolat nevét. Ez a név jelenik meg a felhasználók számára, amikor az eszközön rendelkezésre álló kapcsolatok listáját böngészik.
- **SSID**: A **szolgáltatáskészlet-azonosító** rövidítése. Ez a tulajdonság azon vezeték nélküli hálózat valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált hálózatnevet látják, amikor kiválasztják a kapcsolatot.
- **Automatikus csatlakozás**: Válassza az **Engedélyezés** lehetőséget, hogy automatikusan csatlakozzon ehhez a hálózathoz, amikor az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **Biztonság típusa**: Válassza ki a Wi-Fi-hálózat hitelesítéséhez használt biztonsági protokollt. A választható lehetőségek:

  - **Nyitott (nincs hitelesítés)**: Csak akkor válassza ezt a lehetőséget, ha a hálózat nem védett.
  - **WPA/WPA2 – Személyes**: Írja be a jelszót az **Előmegosztott kulcs** mezőbe. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként.
  - **Adattitkosítás**

- **Proxybeállítások**: A választható lehetőségek:
  - **Nincs**: Semmilyen proxybeállítás nincs konfigurálva.
  - **Manuális**: Adja meg IP-címként a **proxykiszolgáló címét**, és adja meg a **portszámát**.
  - **Automatikus**: A proxykiszolgálót egy fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** (például: `http://proxy.contoso.com`).

## <a name="enterprise-profiles"></a>Vállalati profilok

- **Wi-Fi típusa**: Válassza a **Vállalati** elemet.
- **SSID**: A **szolgáltatáskészlet-azonosító** rövidítése. Ez a tulajdonság azon vezeték nélküli hálózat valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált hálózatnevet látják, amikor kiválasztják a kapcsolatot.
- **Automatikus csatlakozás**: Válassza az **Engedélyezés** lehetőséget, hogy automatikusan csatlakozzon ehhez a hálózathoz, amikor az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.

- **EAP típusa**: Válassza ki azt az EAP-protokollt, amelyet használni szeretne a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez. A választható lehetőségek:

  - **EAP-FAST**: Adja meg a **Védett hitelesítő adatok (PAC) beállításait**. Ez a lehetőség védett hozzáférési hitelesítő adatok használatával hoz létre egy hitelesített csatornát az ügyfél és a hitelesítési kiszolgáló között. A választható lehetőségek:
    - **Ne használja (PAC)**
    - **Használja (PAC)**: Ha rendelkezik meglévő PAC-fájllal, használja azt.
    - **PAC használata és kiépítése**: A PAC-fájl létrehozása és hozzáadása az eszközökhöz.
    - **PAC névtelen használata és kiépítése**: A PAC-fájl létrehozása és hozzáadása az eszközökhöz a kiszolgálón való hitelesítés nélkül.

  - **EAP-SIM**

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Tanúsítványkiszolgálók nevei**: **Adjon meg** egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványokban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. A rendszer ezt a tanúsítványt adja meg a kiszolgálónak, amikor az ügyfél a hálózathoz csatlakozik, és ezzel hitelesíti a kapcsolatot.

      A módosítások mentéséhez válassza az **OK** gombot.

    - **Ügyfél-hitelesítés** - **Ügyféltanúsítvány az ügyfél hitelesítéséhez (identitástanúsítvány)**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      A módosítások mentéséhez válassza az **OK** gombot.

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Tanúsítványkiszolgálók nevei**: **Adjon meg** egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványokban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. A rendszer ezt a tanúsítványt adja meg a kiszolgálónak, amikor az ügyfél a hálózathoz csatlakozik, és ezzel hitelesíti a kapcsolatot.

      A módosítások mentéséhez válassza az **OK** gombot.

    - **Ügyfél-hitelesítés** – Válasszon egy **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)**: Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva.

          A választható lehetőségek: **Titkosítatlan jelszó (PAP)**, **Challenge Handshake Authentication Protocol (CHAP)**, **Microsoft CHAP (MS-CHAP)** vagy **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

        A módosítások mentéséhez válassza az **OK** gombot.

      - **Identitásvédelem (külső identitás)**: Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **LEAP**

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Tanúsítványkiszolgálók nevei**: **Adjon meg** egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványokban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. A rendszer ezt a tanúsítványt adja meg a kiszolgálónak, amikor az ügyfél a hálózathoz csatlakozik, és ezzel hitelesíti a kapcsolatot.

      A módosítások mentéséhez válassza az **OK** gombot.

    - **Ügyfél-hitelesítés** – Válasszon egy **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. 

      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

        A módosítások mentéséhez válassza az **OK** gombot.

      - **Identitásvédelem (külső identitás)**: Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

- **Proxybeállítások**: A választható lehetőségek:
  - **Nincs**: Semmilyen proxybeállítás nincs konfigurálva.
  - **Manuális**: Adja meg IP-címként a **proxykiszolgáló címét**, és adja meg a **portszámát**.
  - **Automatikus**: A proxykiszolgálót egy fájl segítségével konfigurálja. Adja meg a konfigurációs fájlt tartalmazó **proxykiszolgáló URL-címét** (például: `http://proxy.contoso.com`).

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. A következő lépés a [profil hozzárendelése](device-profile-assign.md).

## <a name="more-resources"></a>További források

[Wi-Fi-beállítások áttekintése](wi-fi-settings-configure.md), beleértve a többi rendelkezésre álló platformot is.