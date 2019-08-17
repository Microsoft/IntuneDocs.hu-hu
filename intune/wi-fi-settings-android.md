---
title: Wi-Fi-beállítások konfigurálása Android-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Létrehozhat vagy hozzáadhat egy eszközkonfigurációs Wi-Fi-profilt az Android-eszközökhöz. Megtekintheti a Microsoft Intune különböző beállításait, beleértve a tanúsítványok hozzáadását, az EAP-típusok kiválasztását és a hitelesítési módszer kiválasztását.
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
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d341aeace950f62ae699aa7760a65c0fd2f74fa
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550046"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Android rendszerű eszközökre vonatkozó Wi-Fi-beállítások hozzáadása a Microsoft Intune-ban

Adott Wi-Fi-beállításokkal rendelkező profilt hozhat létre, majd ezt a profilt üzembe helyezheti az Android-eszközökön. A Microsoft Intune számos szolgáltatást nyújt, beleértve a hálózaton való hitelesítést, a PKS- vagy SCEP-tanúsítványok hozzáadását és egyéb lehetőségeket.

Ezek a Wi-Fi-beállítások két kategóriába vannak elkülönítve: Alapszintű beállítások és nagyvállalati szintű beállítások.

Ez a cikk ezeket a beállításokat ismerteti.

## <a name="before-you-begin"></a>Előkészületek

[Eszközprofil létrehozása](device-profile-create.md).

## <a name="basic"></a>Alapszintű

- **Wi-Fi típusa**: Válassza a **Basic** (Egyszerű) lehetőséget.
- **SSID**: Adja meg a **szolgáltatáskészlet azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget a hálózat elrejtéséhez az eszközön elérhető hálózatok listájából. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.

## <a name="enterprise"></a>Vállalati

- **Wi-Fi típusa**: Válassza a **vállalat**lehetőséget.
- **SSID**: Adja meg a **szolgáltatáskészlet azonosítóját**, amely annak a vezeték nélküli hálózatnak a valódi neve, amelyhez az eszközök csatlakoznak. A felhasználók azonban csak a konfigurált **hálózatnevet** látják, amikor kiválasztják a kapcsolatot.
- **Automatikus összekapcsolás**: Az **Engedélyezés** gombra kattintva automatikusan csatlakozhat ehhez a hálózathoz, ha az eszköz hatótávolságon belül van. Válassza a **Letiltás** lehetőséget, ha meg szeretné akadályozni az eszközök automatikus csatlakozását.
- **Rejtett hálózat**: Válassza az **Engedélyezés** lehetőséget a hálózat elrejtéséhez az eszközön elérhető hálózatok listájából. A rendszer ilyenkor nem továbbítja az SSID-t. Válassza a **Letiltás** lehetőséget, ha meg szeretné jeleníteni a hálózatot az eszközön elérhető hálózatok listájában.
- **EAP-típus**: Válassza ki a biztonságos vezeték nélküli kapcsolatok hitelesítéséhez használt bővíthető hitelesítési protokoll (EAP) típust. A választható lehetőségek: 

  - **EAP-TLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány a kiszolgálónak jelenik meg, amikor az ügyfél csatlakozik a hálózathoz. Hitelesíti a kapcsolatokat.

    - Ügyfél-hitelesítési ügyféltanúsítvány ügyfél **-hitelesítéshez (identitás-tanúsítvány):**  -  Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

    - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **EAP-TTLS**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány a kiszolgálónak jelenik meg, amikor az ügyfél csatlakozik a hálózathoz. Hitelesíti a kapcsolatokat.

    - **Ügyfél-hitelesítés**: Válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. Ezt is adja meg:
        - **Nem EAP-módszer (belső identitás)** : Válassza ki a kapcsolatok hitelesítésének módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Titkosítatlan jelszó (PAP)**
          - **Challenge Handshake Authentication Protocol (CHAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

  - **PEAP**: Ezt is adja meg:

    - **Kiszolgálói megbízhatóság** - főtanúsítványa**kiszolgáló érvényesítéséhez**: Válasszon ki egy meglévő megbízható főtanúsítvány-profilt. Ez a tanúsítvány a kiszolgálónak jelenik meg, amikor az ügyfél csatlakozik a hálózathoz. Hitelesíti a kapcsolatokat.

    - **Ügyfél-hitelesítés**: Válasszon **hitelesítési módszert**. A választható lehetőségek:

      - **Felhasználónév és jelszó**: A kapcsolódás hitelesítéséhez kérje meg a felhasználót, hogy adjon meg egy felhasználónevet és egy jelszót. Ezt is adja meg:
        - **Nem EAP hitelesítési módszer (belső identitás)** : Válassza ki a kapcsolatok hitelesítésének módját. Mindenképpen ugyanazt a protokollt válassza, amely a Wi-Fi-hálózathoz van konfigurálva. A választható lehetőségek:

          - **Nincsenek**
          - **Microsoft CHAP 2-es verzió (MS-CHAP v2)**

      - **Tanúsítványok**: Válassza ki azt a SCEP-vagy PKCS-ügyféltanúsítvány-profilt, amely az eszközre is telepítve van. Az eszköz ezt a tanúsítványt adja meg identitásként a kiszolgálónak a kapcsolat hitelesítéséhez.

      - **Személyazonosság védelme (külső identitás)** : Adja meg az EAP-identitásra irányuló kérelemre adott válasz szövegét. Ez a szöveg bármilyen érték lehet, például `anonymous`. A hitelesítés során a rendszer először a névtelen identitást küldi el, majd később egy biztonságos csatornán küldi el a valódi azonosítót.

## <a name="next-steps"></a>További lépések

A profil létrejön, de egyelőre nem csinál semmit. A következő lépés a [profil hozzárendelése](device-profile-assign.md).

## <a name="more-resources"></a>További források

- [Wi-Fi-beállítások áttekintése](wi-fi-settings-configure.md), beleértve a többi platformot is.

- Android Enterprise vagy Android Kiosk rendszerű eszközöket használ? Ha igen, tekintse meg [az Android Enterprise és a dedikált eszközöket futtató eszközök Wi-Fi-beállításait](wi-fi-settings-android-enterprise.md).
