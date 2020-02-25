---
title: Tanúsítványprofil létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Ismerje meg, hogyan használhatja a Egyszerű tanúsítványigénylési protokoll (SCEP) vagy a nyilvános kulcsú titkosítási szabványok (PKCS) tanúsítványait és a tanúsítvány-profilokat Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63fa9f461fc9884d8c21e40cb4b5e3831f3b4b03
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576521"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Tanúsítványok használata a Microsoft Intune történő hitelesítéshez

A tanúsítványokat az Intune-nal használva hitelesítheti a felhasználókat a VPN-, Wi-Fi-vagy e-mail-profilokon keresztül az alkalmazásokban és a vállalati erőforrásokban. Ha tanúsítványokat használ a kapcsolatok hitelesítéséhez, a végfelhasználóknak nem kell megadniuk a felhasználóneveket és a jelszavakat, ami zökkenőmentesvé teheti a hozzáférést. A tanúsítványokat az e-mailek S/MIME használatával történő aláírására és titkosítására is használják.

## <a name="intune-supported-certificates-and-usage"></a>Intune által támogatott tanúsítványok és használat

| Típus              | Hitelesítés | S/MIME-aláírás | S/MIME-titkosítás  |
|--|--|--|--|
| Nyilvános kulcsú titkosítási szabványok (PKCS) importált tanúsítvány |  | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png)|
| PKCS#12 (vagy PFX)    | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) |  |
| SCEP protokoll  | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | |

A tanúsítványok telepítéséhez hozzon létre és rendeljen tanúsítvány-profilokat az eszközökhöz.

Minden egyes létrehozott tanúsítvány egyetlen platformot támogat. Ha például PKCS-tanúsítványokat használ, hozzon létre PKCS-tanúsítványt az Androidhoz, és egy különálló PKCS-tanúsítványt az iOS/iPadOS számára. Ha a két platformhoz is SCEP-tanúsítványokat használ, hozzon létre egy SCEP-tanúsítványt az Androidhoz, és egy másikat az iOS/iPadOS számára.

### <a name="general-considerations-when-you-use-a-microsoft-certification-authority"></a>Általános szempontok Microsoft hitelesítésszolgáltató használata esetén

Microsoft hitelesítésszolgáltató (CA) használata esetén:

- A SCEP-tanúsítványok használatához [be kell állítania egy hálózati eszközök tanúsítványigénylési szolgáltatásának (NDES) kiszolgálóját](certificates-scep-configure.md#set-up-ndes) az Intune-nal való használatra.
- A következő típusú tanúsítvány-profilok használatához [telepítenie kell a Microsoft Intune tanúsítvány-összekötő](certificates-scep-configure.md#install-the-intune-certificate-connector):
  - SCEP-hitelesítési profil
  - PKCS-tanúsítvány profilja

- A PKCS importált tanúsítványok használata:
  - [Telepítse a pfx tanúsítvány-összekötőt a Microsoft Intunehoz](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
  - Exportálja a tanúsítványokat a hitelesítésszolgáltatótól, majd importálja őket a Microsoft Intuneba. Tekintse meg [a PFXImport PowerShell-projektet](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

- Tanúsítványok központi telepítése a következő mechanizmusok használatával:
  - [Megbízható tanúsítványok profiljai](certificates-configure.md#create-trusted-certificate-profiles) a megbízható legfelső szintű hitelesítésszolgáltatói tanúsítvány üzembe helyezéséhez a legfelső szintű vagy köztes (kiállító) hitelesítésszolgáltatótól az eszközökre
  - SCEP-tanúsítványprofilok
  - PKCS-tanúsítványprofilok
  - PKCS importált tanúsítvány-profilok

### <a name="general-considerations-when-you-use-a-third-party-certification-authority"></a>Harmadik féltől származó hitelesítésszolgáltató használata esetén felmerülő általános szempontok

Harmadik féltől származó (nem a Microsofttól származó) hitelesítésszolgáltató (CA) használata esetén:

- SCEP-tanúsítványok használata:
  - Egy harmadik féltől származó HITELESÍTÉSSZOLGÁLTATÓval való integráció beállítása [támogatott partnereink közül](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners). A beállítás a külső HITELESÍTÉSSZOLGÁLTATÓ utasításait követi a HITELESÍTÉSSZOLGÁLTATÓ és az Intune integrálásának befejezéséhez.
  - [Hozzon létre egy alkalmazást az Azure ad-ben](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration) , amely jogosultságokat delegál az Intune-nak az SCEP Certificate Challenge érvényesítéséhez.

- A PKCS importált tanúsítványokhoz [telepíteni kell a pfx tanúsítvány-összekötőt a Microsoft Intunehoz](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).

- Tanúsítványok központi telepítése a következő mechanizmusok használatával:
  - [Megbízható tanúsítványok profiljai](certificates-configure.md#create-trusted-certificate-profiles) a megbízható legfelső szintű hitelesítésszolgáltatói tanúsítvány üzembe helyezéséhez a legfelső szintű vagy köztes (kiállító) hitelesítésszolgáltatótól az eszközökre
  - SCEP-tanúsítványprofilok
  - PKCS-tanúsítványok profiljai *(csak a [Digicert PKI platformmal](certificates-digicert-configure.md)támogatott)*
  - PKCS importált tanúsítvány-profilok

## <a name="supported-platforms-and-certificate-profiles"></a>Támogatott platformok és tanúsítványok profiljai

| Platform              | Megbízható tanúsítvány profilja | PKCS-tanúsítvány profilja | SCEP-tanúsítvány profilja | PKCS importált tanúsítvány profilja  |
|--|--|--|--|---|
| Android-eszköz rendszergazdája | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png)|  ![Támogatott](./media/certificates-configure/green-check.png) |
| Vállalati Android <br> -Teljes körűen felügyelt (eszköz tulajdonosa)   | ![Támogatott](./media/certificates-configure/green-check.png) |   | ![Támogatott](./media/certificates-configure/green-check.png) |   |
| Vállalati Android <br> -Dedikált (eszköz tulajdonosa)   | ![Támogatott](./media/certificates-configure/green-check.png)  |   | ![Támogatott](./media/certificates-configure/green-check.png)  |   |
| Vállalati Android <br> -Munkahelyi profil    | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) |
| iOS/iPadOS                   | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) |
| macOS                 | ![Támogatott](./media/certificates-configure/green-check.png) |  ![Támogatott](./media/certificates-configure/green-check.png) |![Támogatott](./media/certificates-configure/green-check.png)|![Támogatott](./media/certificates-configure/green-check.png)|
| WVPN-profilokdows Phone 8.1     |![Támogatott](./media/certificates-configure/green-check.png)  |  | ![Támogatott](./media/certificates-configure/green-check.png)| ![Támogatott](./media/certificates-configure/green-check.png) |
| Windows 8.1 és újabb |![Támogatott](./media/certificates-configure/green-check.png)  |  |![Támogatott](./media/certificates-configure/green-check.png) |   |
| Windows 10 és újabb  | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>A megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítvány exportálása

A PKCS, a SCEP és a PKCS importált tanúsítványok használatához az eszközöknek meg kell bízniuk a legfelső szintű hitelesítésszolgáltatóban. A megbízhatósági kapcsolat létrehozásához exportálja a megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítványt, valamint a közbenső vagy kiállító hitelesítésszolgáltató tanúsítványait nyilvános tanúsítványként (. cer). Ezeket a tanúsítványokat a kiállító HITELESÍTÉSSZOLGÁLTATÓTÓL vagy bármely olyan eszközről szerezheti be, amely megbízik a kiállító HITELESÍTÉSSZOLGÁLTATÓban.

A tanúsítvány exportálásához tekintse meg a hitelesítésszolgáltató dokumentációját. A nyilvános tanúsítványt. cer fájlként kell exportálnia.  Ne exportálja a titkos kulcsot, a. pfx-fájlt.

Ezt a. cer fájlt fogja használni, amikor [megbízható tanúsítvány-profilokat hoz létre](#create-trusted-certificate-profiles) a tanúsítvány eszközökön való telepítéséhez.

## <a name="create-trusted-certificate-profiles"></a>Megbízható tanúsítványok profiljainak létrehozása

Hozzon létre egy megbízható tanúsítványsablont, mielőtt SCEP, PKCS vagy PKCS importált tanúsítványsablont hozna létre. A megbízható tanúsítvány-profilok üzembe helyezése biztosítja, hogy mindegyik eszköz felismeri a HITELESÍTÉSSZOLGÁLTATÓ legitimitását. A SCEP tanúsítvány-profilok közvetlenül egy megbízható tanúsítvány profiljára hivatkoznak. A PKCS-tanúsítványok profiljai nem hivatkoznak közvetlenül a megbízható tanúsítvány profiljára, de közvetlenül hivatkoznak a HITELESÍTÉSSZOLGÁLTATÓT futtató kiszolgálóra. A PKCS importált tanúsítvány-profilok nem hivatkoznak közvetlenül a megbízható tanúsítvány profiljára, de használhatják azt az eszközön. A megbízható tanúsítvány-profilok eszközökre való telepítése biztosítja ezt a megbízhatósági kapcsolatot. Ha egy eszköz nem bízik meg a legfelső szintű HITELESÍTÉSSZOLGÁLTATÓban, a SCEP-vagy PKCS-tanúsítvány profiljának házirendje sikertelen lesz.

Hozzon létre egy külön megbízható tanúsítványsablont minden támogatni kívánt eszköz platformhoz, ugyanúgy, mint a SCEP, a PKCS és a PKCS importált tanúsítvány-profilok esetében.

### <a name="to-create-a-trusted-certificate-profile"></a>Megbízható tanúsítványprofil létrehozásához

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.

   ![Navigáljon az Intune-hoz, és hozzon létre egy új profilt egy megbízható tanúsítványhoz](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Adja meg a következő tulajdonságokat:

   - **Név** a profil számára
   - **Leírás** megadása opcionálisan
   - **Platform**, amelyen telepíteni kell a profilt
   - A **Profiltípust** állítsa **Megbízható tanúsítványra**

4. Válassza a **Beállítások**lehetőséget, majd keresse meg a megbízható legfelső szintű hitelesítésszolgáltatói tanúsítvány. cer fájlt, amelyet az adott tanúsítvány-profillal való használatra exportált, majd válassza az **OK**gombot.

5. Válassza ki – csak a Windows 8.1- és Windows 10-eszközök esetében – a megbízható tanúsítvány céltárolóját a **Céltároló** mezőben, a következő lehetőségek közül:

   - **Számítógép tanúsítványtárolója – fő**
   - **Számítógép tanúsítványtárolója – köztes**
   - **Felhasználói tanúsítványtároló – köztes**

6. Ha elkészült, válassza az **OK** gombot, lépjen vissza a **Profil létrehozása** panelre, és válassza a **Létrehozás** gombot.

A profil az *eszközök – konfigurációs profilok* ablak profilok listájában jelenik meg, a **megbízható tanúsítvány**profiljának típusától függően. Ügyeljen arra, hogy ezt a profilt olyan eszközökhöz rendelje, amelyek SCEP-vagy PKCS-tanúsítványokat fognak használni. A profil csoportokhoz rendeléséhez lásd: [eszközbeállítások társítása](../configuration/device-profile-assign.md).

> [!NOTE]
> Az Android-eszközökön olyan üzenet jelenhet meg, amely szerint egy harmadik fél megbízható tanúsítványt telepített.

## <a name="additional-resources"></a>További háttéranyagok

- [Eszközprofilok hozzárendelése](../configuration/device-profile-assign.md)  
- [S/MIME használata e-mailek aláírásához és titkosításához](certificates-s-mime-encryption-sign.md)  
- [Harmadik féltől származó hitelesítésszolgáltató használata](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>További lépések

Hozzon létre SCEP, PKCS vagy PKCS importálású tanúsítvány-profilokat a használni kívánt platformokhoz. A folytatáshoz tekintse meg a következő cikkeket:

- [Infrastruktúra konfigurálása az SCEP-tanúsítványok támogatásához az Intune-nal](certificates-scep-configure.md)  
- [PKCS-tanúsítványok konfigurálása és kezelése az Intune-nal](certficates-pfx-configure.md)  
- [PKCS importált tanúsítvány-profil létrehozása](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)
