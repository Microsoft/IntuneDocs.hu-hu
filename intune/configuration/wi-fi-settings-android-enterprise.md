---
title: Wi-Fi-beállítások Android Enterprise és kioszk eszközökhöz – Microsoft Intune | Microsoft Docs
description: Wi-Fi eszközkonfigurációs profilokat hozhat létre vagy adhat hozzá az Android Enterprise és Android kioszk rendszerhez. Megtekintheti a Microsoft Intune különböző beállításait, beleértve a tanúsítványok hozzáadását, az EAP-típusok kiválasztását és a hitelesítési módszer kiválasztását. Kioszkeszközök esetén adja meg a hálózat előre megosztott kulcsát is.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04d35f49f9e07cb72a1fea92210b05e0a95ec256
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390810"
---
# <a name="add-wi-fi-settings-for-android-enterprise-dedicated-and-fully-managed-devices-in-microsoft-intune"></a>Wi-Fi-beállítások hozzáadása az Android Enterprise dedikált és teljes mértékben felügyelt eszközökhöz Microsoft Intune

Létrehozhat egy profilt adott Wi-Fi-beállításokkal, majd üzembe helyezheti ezt a profilt az Android Enterprise teljes körűen felügyelt és dedikált eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, az előmegosztott kulcsok használatát és egyebeket.

Ez a cikk ezeket a beállításokat ismerteti. A [Wi-Fi használata az eszközökön](wi-fi-settings-configure.md) több információt tartalmaz a Microsoft Intune Wi-Fi szolgáltatásával kapcsolatban.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Csak az eszköz tulajdonosa

Akkor válassza ezt a lehetőséget, ha androidos vállalati dedikált vagy teljes körűen felügyelt eszközre kíván üzembe helyezni.  Az Android Enterprise dedikált és teljes körűen felügyelt eszközei jelenleg támogatják a SCEP tanúsítvány telepítését, de a PKCS nem.

### <a name="basic"></a>Alapszintű

- **Wi-Fi típusa**: válassza az **Alapszintű** lehetőséget.
- **Hálózat neve**: Adja meg a Wi-Fi-kapcsolat nevét. A végfelhasználók akkor látják ezt a nevet, amikor az elérhető Wi-FI-kapcsolatokhoz böngészhetik az eszközön. Adja meg például a **contoso WiFi**értéket.
- **SSID**: adja meg a szolgáltatáskészlet **azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **Wi-Fi típusa**: Válassza ki a Wi-Fi-hálózat hitelesítéséhez használt biztonsági protokollt. A választható lehetőségek:

  - **Nyitott (nincs hitelesítés)** : Csak akkor válassza ezt a lehetőséget, ha a hálózat nem védett.
  - **WEP előmegosztott kulcs**: Írja be a jelszót az **Előmegosztott kulcs** mezőbe. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként.
  - **WPA előre megosztott kulcs**: Írja be a jelszót az **Előmegosztott kulcs** mezőbe. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként.

### <a name="enterprise"></a>Enterprise

- **Wi-Fi típusa**: Válassza a **Vállalati** elemet.
- **SSID**: adja meg a szolgáltatáskészlet **azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **EAP típusa**: Válassza ki azt az EAP-protokollt, amelyet használni szeretne a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez. A választható lehetőségek:

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés - ügyféltanúsítvány** **az ügyfél-hitelesítéshez (Identity Certificate)** : válassza ki az ESZKÖZre is telepített SCEP-ügyféltanúsítvány-profilt. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

    - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Titkosítatlan jelszó (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: válassza ki azt az SCEP-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP hitelesítési módszer (belső identitás)** : Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Nincsenek**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: válassza ki azt az SCEP-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

## <a name="work-profile-only"></a>Csak munkahelyi profil

### <a name="basic"></a>Alapszintű

- **Wi-Fi típusa**: válassza az **Alapszintű** lehetőséget.
- **SSID**: adja meg a szolgáltatáskészlet **azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.

### <a name="enterprise"></a>Enterprise

- **Wi-Fi típusa**: Válassza a **Vállalati** elemet.
- **SSID**: adja meg a szolgáltatáskészlet **azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget, hogy a hálózat ne jelenjen meg az eszközön elérhető hálózatok listájában. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **EAP típusa**: Válassza ki azt az EAP-protokollt, amelyet használni szeretne a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez. A választható lehetőségek:

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés** - **Ügyféltanúsítvány az ügyfél hitelesítéséhez (identitástanúsítvány)** : Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

    - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Titkosítatlan jelszó (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgáló megbízhatósága** - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP hitelesítési módszer (belső identitás)** : Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Nincsenek**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. Ezután [rendelje hozzá ezt a profilt](device-profile-assign.md) , és [Figyelje annak állapotát.](device-profile-monitor.md)

Az [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [MacOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md)és [Windows 8,1 rendszerű](wi-fi-settings-import-windows-8-1.md) eszközökhöz Wi-Fi profilokat is létrehozhat.
