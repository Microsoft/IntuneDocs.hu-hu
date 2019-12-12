---
title: A macOS-eszközök vezetékes hálózati beállításainak konfigurálása a Microsoft Intuneban – Azure | Microsoft Docs
titleSuffix: ''
description: Hozzon létre vagy adjon hozzá vezetékes hálózati eszköz konfigurációs profilt macOS-eszközökhöz. Megtekintheti a Microsoft Intune különböző beállításait, beleértve a tanúsítványok hozzáadását, az EAP-típusok kiválasztását és a hitelesítési módszer kiválasztását.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/4/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dba36d03489bcdeee3c3c1f69a4995823dd21ee
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74994293"
---
# <a name="add-wired-network-settings-for-macos-devices-in-microsoft-intune"></a>Vezetékes hálózati beállítások hozzáadása macOS-eszközökhöz Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Létrehozhat egy adott vezetékes hálózati beállításokkal rendelkező profilt, majd telepítheti a profilt macOS-eszközökre. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, a PKS- vagy SCEP-tanúsítványok hozzáadását és egyéb lehetőségeket. 

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](device-profile-create.md).

> [!NOTE]
> Ezek a beállítások minden regisztrációs típushoz elérhetők. A regisztrációs típusokkal kapcsolatos további információkért lásd: [MacOS-regisztráció](../enrollment/macos-enroll.md).

## <a name="profiles"></a>Profilok

- **Profil típusa**: válassza a **vezetékes hálózat**lehetőséget.
- **Hálózati adapter**: 
- **EAP típusa**: Válassza ki azt az EAP-protokollt, amelyet használni szeretne a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez. A választható lehetőségek:
  - **EAP-FAST**: Adja meg a **Védett hitelesítő adatok (PAC) beállításait**. Ez a lehetőség védett hozzáférési hitelesítő adatok használatával hoz létre egy hitelesített csatornát az ügyfél és a hitelesítési kiszolgáló között. A választható lehetőségek:
    - **Ne használja (PAC)**
    - **Használja (PAC)** : Ha rendelkezik meglévő PAC-fájllal, használja azt.
    - **PAC használata és kiépítése**: A PAC-fájl létrehozása és hozzáadása az eszközökhöz.
    - **PAC névtelen használata és kiépítése**: A PAC-fájl létrehozása és hozzáadása az eszközökhöz a kiszolgálón való hitelesítés nélkül.
  - **EAP-TLS**: Ezt is adja meg:
    - **Kiszolgáló megbízhatósága** - **Tanúsítványkiszolgálók nevei**: **Adjon meg** egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványokban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. A rendszer ezt a tanúsítványt adja meg a kiszolgálónak, amikor az ügyfél a hálózathoz csatlakozik, és ezzel hitelesíti a kapcsolatot.
    - **Ügyfél-hitelesítés** - **Ügyféltanúsítvány az ügyfél hitelesítéséhez (identitástanúsítvány)** : Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.
  - **EAP-TTLS**: Ezt is adja meg:
    - **Kiszolgáló megbízhatósága** - **Tanúsítványkiszolgálók nevei**: **Adjon meg** egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványokban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. A rendszer ezt a tanúsítványt adja meg a kiszolgálónak, amikor az ügyfél a hálózathoz csatlakozik, és ezzel hitelesíti a kapcsolatot.
    - **Ügyfél-hitelesítés** – Válasszon egy **hitelesítési módszert**. A választható lehetőségek:
      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolat hitelesítési módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva.
          A választható lehetőségek: **Titkosítatlan jelszó (PAP)** , **Challenge Handshake Authentication Protocol (CHAP)** , **Microsoft CHAP (MS-CHAP)** vagy **Microsoft CHAP 2-es verzió (MS-CHAP v2)**
      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.
      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.
  - **LEAP**
  - **PEAP**: Ezt is adja meg:
    - **Kiszolgáló megbízhatósága** - **Tanúsítványkiszolgálók nevei**: **Adjon meg** egy vagy több, a megbízható hitelesítésszolgáltató (CA) által kiállított tanúsítványokban használt köznapi nevet. Ha megadja ezt az információt, elkerülheti azt a dinamikus megbízhatósági ablakot, amely akkor jelenik meg a felhasználók eszközein, amikor ehhez a Wi-Fi-hálózathoz csatlakoznak.
    - **Főtanúsítvány a kiszolgálóérvényesítéshez**: Válasszon egy meglévő megbízható főtanúsítvány-profilt. A rendszer ezt a tanúsítványt adja meg a kiszolgálónak, amikor az ügyfél a hálózathoz csatlakozik, és ezzel hitelesíti a kapcsolatot.
    - **Ügyfél-hitelesítés** – Válasszon egy **hitelesítési módszert**. A választható lehetőségek:
      - **Felhasználónév és jelszó**: Felhasználónév és jelszó kérése a felhasználótól a kapcsolat hitelesítéséhez. 
      - **Tanúsítványok**: Válassza ki azt az SCEP vagy PKCS ügyféltanúsítvány-profilt, amely szintén üzembe lesz helyezve az eszközön. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.
      - **Identitásvédelem (külső identitás)** : Adja meg az EAP-identitáskérésre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. Ezután [rendelje hozzá ezt a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Wi-Fi-beállítások konfigurálása [Android](wi-fi-settings-android.md), [Android Enterprise](wi-fi-settings-android-enterprise.md), [iOS](wi-fi-settings-ios.md)és [Windows 10 rendszerű](wi-fi-settings-windows.md) eszközökön.
