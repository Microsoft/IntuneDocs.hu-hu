---
title: Wi-Fi-beállítások konfigurálása Android-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Létrehozhat vagy hozzáadhat egy eszközkonfigurációs Wi-Fi-profilt az Android-eszközökhöz. Megtekintheti a Microsoft Intune különböző beállításait, beleértve a tanúsítványok hozzáadását, az EAP-típusok kiválasztását és a hitelesítési módszer kiválasztását.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/24/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ea0a60537bb488d3280990747d3e337e73fddc0
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754558"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Android rendszerű eszközökre vonatkozó Wi-Fi-beállítások hozzáadása a Microsoft Intune-ban

Adott Wi-Fi-beállításokkal rendelkező profilt hozhat létre, majd ezt a profilt üzembe helyezheti az Android-eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, a PKS- vagy SCEP-tanúsítványok hozzáadását és egyéb lehetőségeket.

Ezek a Wi-Fi-beállítások két kategóriára vannak osztva, alapszintű és vállalati szintű beállításokra.

Ez a cikk ezeket a beállításokat ismerteti.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](device-profile-create.md).

## <a name="basic"></a>Alapvető

- **Wi-Fi típusa**: válassza az **Alapszintű** lehetőséget.
- **SSID**: adja meg a szolgáltatáskészlet **azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.

## <a name="enterprise"></a>Enterprise

- **Wi-Fi típusa**: Válassza a **Vállalati** elemet.
- **SSID**: adja meg a szolgáltatáskészlet **azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **EAP típusa**: Válassza ki azt az EAP-protokollt, amelyet használni szeretne a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez. A választható lehetőségek:

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány a kiszolgálónak jelenik meg, amikor az ügyfél csatlakozik a hálózathoz. Hitelesíti a kapcsolatokat.

    - **Ügyfél-hitelesítés** - **Ügyféltanúsítvány az ügyfél hitelesítéséhez (identitástanúsítvány)** : Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

    - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

    - **Proxybeállítások**: adja meg a szervezet által használt proxy-konfigurációt. A választható lehetőségek:

      - **Nincs** – nem használ proxykiszolgálót.
      - **Automatikus** – ezzel a beállítással megadhatja a *proxykiszolgáló URL-címét* , amelyet a proxykiszolgáló vagy proxy automatikus konfigurációs (PAC) fájljának megadására használ, amely a proxykiszolgálók listáját tartalmazza.

    - **Proxykiszolgáló URL-címe**: Ez a beállítás akkor érhető el, ha *automatikusra*állítja be a *proxybeállításokat* . Adja meg a következő lehetőségek egyikét az eszközök a proxykiszolgálóhoz való átirányításához:

      - IP-cím. Például: `10.0.0.11`
      - EGY URL-CÍM. Például `http://proxyserver.contoso.com`.
      - A proxy automatikus konfigurációs (PAC) fájljának URL-címe. Példa: `http://proxy.contoso.com/proxy.pac`.

      A PAC-fájlokkal kapcsolatos további információkért lásd: [proxy automatikus konfigurációs (PAC) fájlja](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (egy nem Microsoft-webhely megnyitása).

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány a kiszolgálónak jelenik meg, amikor az ügyfél csatlakozik a hálózathoz. Hitelesíti a kapcsolatokat.

    - **Ügyfél-hitelesítés**: válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Titkosítatlan jelszó (PAP)**
          - **Challenge Handshake Authentication Protocol (CHAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

    - **Proxybeállítások**: adja meg a szervezet által használt proxy-konfigurációt. A választható lehetőségek:

      - **Nincs** – nem használ proxykiszolgálót.
      - **Automatikus** – ezzel a beállítással megadhatja a *proxykiszolgáló URL-címét* , amelyet a proxykiszolgáló vagy proxy automatikus konfigurációs (PAC) fájljának megadására használ, amely a proxykiszolgálók listáját tartalmazza.

    - **Proxykiszolgáló URL-címe**: Ez a beállítás akkor érhető el, ha *automatikusra*állítja be a *proxybeállításokat* . Adja meg a következő lehetőségek egyikét az eszközök a proxykiszolgálóhoz való átirányításához:

      - IP-cím. Például: `10.0.0.11`
      - EGY URL-CÍM. Például `http://proxyserver.contoso.com`.
      - A proxy automatikus konfigurációs (PAC) fájljának URL-címe. Példa: `http://proxy.contoso.com/proxy.pac`.

      A PAC-fájlokkal kapcsolatos további információkért lásd: [proxy automatikus konfigurációs (PAC) fájlja](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (egy nem Microsoft-webhely megnyitása).

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány a kiszolgálónak jelenik meg, amikor az ügyfél csatlakozik a hálózathoz. Hitelesíti a kapcsolatokat.

    - **Ügyfél-hitelesítés**: válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP hitelesítési módszer (belső identitás)** : Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Nincsenek**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

      - **Proxybeállítások**: adja meg a szervezet által használt proxy-konfigurációt. A választható lehetőségek:

        - **Nincs** – nem használ proxykiszolgálót.
        - **Automatikus** – ezzel a beállítással megadhatja a *proxykiszolgáló URL-címét* , amelyet a proxykiszolgáló vagy proxy automatikus konfigurációs (PAC) fájljának megadására használ, amely a proxykiszolgálók listáját tartalmazza.

      - **Proxykiszolgáló URL-címe**: Ez a beállítás akkor érhető el, ha *automatikusra*állítja be a *proxybeállításokat* . Adja meg a következő lehetőségek egyikét az eszközök a proxykiszolgálóhoz való átirányításához:

        - IP-cím. Például: `10.0.0.11`
        - EGY URL-CÍM. Például `http://proxyserver.contoso.com`.
        - A proxy automatikus konfigurációs (PAC) fájljának URL-címe. Példa: `http://proxy.contoso.com/proxy.pac`.

        A PAC-fájlokkal kapcsolatos további információkért lásd: [proxy automatikus konfigurációs (PAC) fájlja](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (egy nem Microsoft-webhely megnyitása).

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. A következő lépés a [profil hozzárendelése](device-profile-assign.md).

## <a name="more-resources"></a>További források

- [Wi-Fi-beállítások áttekintése](wi-fi-settings-configure.md), beleértve a többi platformot is.

- Android Enterprise vagy Android Kiosk rendszerű eszközöket használ? Ha igen, tekintse meg [az Android Enterprise és a dedikált eszközöket futtató eszközök Wi-Fi-beállításait](wi-fi-settings-android-enterprise.md).
