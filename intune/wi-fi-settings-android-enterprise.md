---
title: Wi-Fi-beállítások Android Enterprise és kioszk eszközökhöz – Microsoft Intune | Microsoft Docs
description: Wi-Fi eszközkonfigurációs profilokat hozhat létre vagy adhat hozzá az Android Enterprise és Android kioszk rendszerhez. Megtekintheti a Microsoft Intune különböző beállításait, beleértve a tanúsítványok hozzáadását, az EAP-típusok kiválasztását és a hitelesítési módszer kiválasztását. Kioszkeszközök esetén adja meg a hálózat előre megosztott kulcsát is.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51096b4ff42902b5feb8cecdebf9d839821e1bb2
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545932"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Android Enterprise és Android kioszk rendszerű eszközökre vonatkozó Wi-Fi-beállítások hozzáadása a Microsoft Intune-ban

Létrehozhat egy adott WiFi-beállításokkal rendelkező profilt, majd üzembe helyezheti ezt a profilt az Android Enterprise és az Android dedikált eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, az előmegosztott kulcsok használatát és egyebeket.

Ez a cikk ezeket a beállításokat ismerteti. A [Wi-Fi használata](wi-fi-settings-configure.md) az eszközökön több információt tartalmaz a Microsoft Intune Wi-Fi szolgáltatásával kapcsolatban.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Csak az eszköz tulajdonosa

Válassza ezt a lehetőséget, ha androidos vállalati dedikált eszközt használ kioszkként.

### <a name="basic"></a>Alapszintű

- **Wi-Fi típusa**: Válassza a **Basic** (Egyszerű) lehetőséget.
- **Hálózat neve**: Adja meg a Wi-Fi kapcsolat nevét. A végfelhasználók akkor látják ezt a nevet, amikor az elérhető Wi-FI-kapcsolatokhoz böngészhetik az eszközön. Adja meg például a **contoso WiFi**értéket.
- **SSID**: Adja meg a **szolgáltatáskészlet azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget a hálózat elrejtéséhez az eszközön elérhető hálózatok listájából. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **Wi-Fi típusa**: Válassza ki a Wi-Fi-hálózat hitelesítéséhez használandó biztonsági protokollt. A választható lehetőségek:

  - **Megnyitás (nincs hitelesítés)** : Csak akkor használja ezt a beállítást, ha a hálózat nem biztonságos.
  - **Előre megosztott WEP-kulcs**: Adja meg a jelszót **előmegosztott kulcsban**. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként.
  - **WPA-előmegosztott kulcs**: Adja meg a jelszót **előmegosztott kulcsban**. A cég hálózatának beállítása vagy konfigurálása során a rendszer egy jelszót vagy egy hálózati kulcsot is konfigurál. Adja meg ezt a jelszót vagy hálózati kulcsot a PSK értékeként.

### <a name="enterprise"></a>Vállalati

- **Wi-Fi típusa**: Válassza a **vállalat**lehetőséget.
- **SSID**: Adja meg a **szolgáltatáskészlet azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget a hálózat elrejtéséhez az eszközön elérhető hálózatok listájából. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **EAP-típus**: Válassza ki a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez használt bővíthető hitelesítési protokoll (EAP) típust. A választható lehetőségek:

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - Ügyfél-hitelesítési ügyféltanúsítvány ügyfél **-hitelesítéshez (identitás-tanúsítvány):**  -  Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

    - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: Válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolatok hitelesítésének módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Titkosítatlan jelszó (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: Válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. Ezt is adja meg:
        - **Nem EAP hitelesítési módszer (belső identitás)** : Válassza ki a kapcsolatok hitelesítésének módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Nincsenek**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

## <a name="work-profile-only"></a>Csak munkahelyi profil

### <a name="basic"></a>Alapszintű

- **Wi-Fi típusa**: Válassza a **Basic** (Egyszerű) lehetőséget.
- **SSID**: Adja meg a **szolgáltatáskészlet azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget a hálózat elrejtéséhez az eszközön elérhető hálózatok listájából. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.

### <a name="enterprise"></a>Vállalati

- **Wi-Fi típusa**: Válassza a **vállalat**lehetőséget.
- **SSID**: Adja meg a **szolgáltatáskészlet azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget a hálózat elrejtéséhez az eszközön elérhető hálózatok listájából. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **EAP-típus**: Válassza ki a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez használt bővíthető hitelesítési protokoll (EAP) típust. A választható lehetőségek:

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - Ügyfél-hitelesítési ügyféltanúsítvány ügyfél **-hitelesítéshez (identitás-tanúsítvány):**  -  Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

    - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: Válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolatok hitelesítésének módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Titkosítatlan jelszó (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Amikor az ügyfél csatlakozik a hálózathoz, a rendszer ezt a tanúsítványt mutatja be a kiszolgálónak, és hitelesíti a kapcsolatot.

    - **Ügyfél-hitelesítés**: Válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. Ezt is adja meg:
        - **Nem EAP hitelesítési módszer (belső identitás)** : Válassza ki a kapcsolatok hitelesítésének módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Nincsenek**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. Ezután [rendelje hozzá ezt a profilt](device-profile-assign.md) , és [Figyelje annak állapotát.](device-profile-monitor.md)

Az [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [MacOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md)és [Windows 8,1 rendszerű](wi-fi-settings-import-windows-8-1.md) eszközökhöz Wi-Fi profilokat is létrehozhat.
