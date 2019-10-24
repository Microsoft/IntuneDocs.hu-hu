---
title: Tanúsítványprofil létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Ismerje meg, hogyan használhatja a Egyszerű tanúsítványigénylési protokoll (SCEP) vagy a nyilvános kulcsú titkosítási szabványok (PKCS) tanúsítványait és a tanúsítvány-profilokat Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
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
ms.openlocfilehash: 65ced1dfb0fe872129b7437e8dda3dde680b5d07
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72786815"
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

Minden egyes létrehozott tanúsítvány egyetlen platformot támogat. Ha például PKCS-tanúsítványokat használ, hozzon létre PKCS-tanúsítványt az Androidhoz, és egy különálló PKCS-tanúsítvány-profilt iOS-hez. Ha a két platformhoz is SCEP-tanúsítványokat használ, hozzon létre egy SCEP-tanúsítványt az Androidhoz, és egy másikat az iOS-hez.  

**Általános szempontok**:  
- Ha nem rendelkezik vállalati hitelesítésszolgáltatóval (CA), akkor létre kell hoznia egyet, vagy egyet kell használnia a [támogatott partnereink közül](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- Ha a Microsoft Active Directory tanúsítványszolgáltatás használatával SCEP-tanúsítványokat használ, a hálózati eszközök tanúsítványigénylési szolgáltatásának (NDES) kiszolgálóját kell konfigurálnia.
- Ha a SCEP-t az egyik hitelesítésszolgáltatói partnerrel együtt használja, [integrálnia kell azt az Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)-nal.
- A SCEP-és a PKCS-tanúsítványok profiljaihoz a Microsoft Intune Tanúsítvány-összekötő letöltésére, telepítésére és konfigurálására van szükség. 
- A PKCS importált tanúsítványok megkövetelik a PFX tanúsítvány-összekötő letöltését, telepítését és konfigurálását Microsoft Intune számára.
- A PKCS importált tanúsítványok megkövetelik, hogy tanúsítványokat exportáljon a hitelesítésszolgáltatótól, és importálja őket Microsoft Intuneba. Lásd [a PFXImport PowerShell-projektet](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- Ahhoz, hogy egy eszköz SCEP, PKCS vagy PKCS importált tanúsítvány-profilokat használjon, az eszköznek meg kell bíznia a legfelső szintű hitelesítésszolgáltatóban. A megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítvány eszközökre való üzembe helyezéséhez egy *megbízható tanúsítvány-profilt* kell használnia.  

## <a name="supported-platforms-and-certificate-profiles"></a>Támogatott platformok és tanúsítványok profiljai  
| Platfésm              | Megbízható tanúsítvány profilja | PKCS-tanúsítvány profilja | SCEP-tanúsítvány profilja | PKCS importált tanúsítvány profilja  |
|--|--|--|--|---|
| Android-eszköz rendszergazdája | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png)|  ![Támogatott](./media/certificates-configure/green-check.png) |
| Vállalati Android <br> -Teljes körűen felügyelt (eszköz tulajdonosa)   | ![Támogatott](./media/certificates-configure/green-check.png) |   | ![Támogatott](./media/certificates-configure/green-check.png) |   |
| Vállalati Android <br> -Dedikált (eszköz tulajdonosa)   |  |   |  |   |
| Vállalati Android <br> -Munkahelyi profil    | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) |
| iOS                   | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) |
| macOS                 | ![Támogatott](./media/certificates-configure/green-check.png) |  ![Támogatott](./media/certificates-configure/green-check.png) |![Támogatott](./media/certificates-configure/green-check.png)|![Támogatott](./media/certificates-configure/green-check.png)|
| WVPN-profilokdows Phone 8.1     |![Támogatott](./media/certificates-configure/green-check.png)  |  | ![Támogatott](./media/certificates-configure/green-check.png)| ![Támogatott](./media/certificates-configure/green-check.png) |
| Windows 8.1 és újabb |![Támogatott](./media/certificates-configure/green-check.png)  |  |![Támogatott](./media/certificates-configure/green-check.png) |   |
| Windows 10 és újabb  | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) | ![Támogatott](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>A megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítvány exportálása  
A PKCS, a SCEP és a PKCS importált tanúsítványok használatához az eszközöknek meg kell bízniuk a legfelső szintű hitelesítésszolgáltatóban. A megbízhatósági kapcsolat létrehozásához exportálja a megbízható legfelső szintű hitelesítésszolgáltató (CA) tanúsítványát, valamint a közbenső vagy kiállító hitelesítésszolgáltató tanúsítványait nyilvános tanúsítványként (. cer). Ezeket a tanúsítványokat a kiállító HITELESÍTÉSSZOLGÁLTATÓTÓL vagy bármely olyan eszközről szerezheti be, amely megbízik a kiállító HITELESÍTÉSSZOLGÁLTATÓban.  

A tanúsítvány exportálásához tekintse meg a hitelesítésszolgáltató dokumentációját. A nyilvános tanúsítványt. cer fájlként kell exportálnia.  Ne exportálja a titkos kulcsot, a. pfx-fájlt.  

Ezt a. cer fájlt fogja használni, amikor [megbízható tanúsítvány-profilokat hoz létre](#create-trusted-certificate-profiles) a tanúsítvány eszközökön való telepítéséhez.  

## <a name="create-trusted-certificate-profiles"></a>Megbízható tanúsítványok profiljainak létrehozása  
Hozzon létre egy megbízható tanúsítványsablont, mielőtt SCEP, PKCS vagy PKCS importált tanúsítványsablont hozna létre. A megbízható tanúsítvány-profilok üzembe helyezése biztosítja, hogy mindegyik eszköz felismeri a HITELESÍTÉSSZOLGÁLTATÓ legitimitását. A SCEP tanúsítvány-profilok közvetlenül egy megbízható tanúsítvány profiljára hivatkoznak. A PKCS-tanúsítványok profiljai nem hivatkoznak közvetlenül a megbízható tanúsítvány profiljára, de közvetlenül hivatkoznak a HITELESÍTÉSSZOLGÁLTATÓT futtató kiszolgálóra. A PKCS importált tanúsítvány-profilok nem hivatkoznak közvetlenül a megbízható tanúsítvány profiljára, de használhatják azt az eszközön. A megbízható tanúsítvány-profilok eszközökre való telepítése biztosítja ezt a megbízhatósági kapcsolatot. Ha egy eszköz nem bízik meg a legfelső szintű HITELESÍTÉSSZOLGÁLTATÓban, a SCEP-vagy PKCS-tanúsítvány profiljának házirendje sikertelen lesz.  

Hozzon létre egy külön megbízható tanúsítványsablont minden támogatni kívánt eszköz platformhoz, ugyanúgy, mint a SCEP, a PKCS és a PKCS importált tanúsítvány-profilok esetében.  


### <a name="to-create-a-trusted-certificate-profile"></a>Megbízható tanúsítványprofil létrehozásához  

1. Jelentkezzen be az [Intune-portálra](https://aka.ms/intuneportal).  
2. Válassza az **Eszközkonfiguráció** > **Kezelés** > **Profilok** > **Profil létrehozása** lehetőséget.  
3. Adja meg a megbízható tanúsítvány profiljának **nevét és leírását** .  
4. Válassza ki a megbízható tanúsítvány eszközplatformját a **Platform** legördülő listából.  
5. A **Profil típusa** legördülő listában válassza a **Megbízható tanúsítvány** lehetőséget.  
6. Keresse meg a megbízható legfelső szintű HITELESÍTÉSSZOLGÁLTATÓI tanúsítvány. cer fájlját, amelyet a tanúsítvány-profillal való használatra exportált, majd válassza az **OK gombot**.  
7. Válassza ki – csak a Windows 8.1- és Windows 10-eszközök esetében – a megbízható tanúsítvány céltárolóját a **Céltároló** mezőben, a következő lehetőségek közül:  
   - **Számítógép tanúsítványtárolója – fő**
   - **Számítógép tanúsítványtárolója – köztes**
   - **Felhasználói tanúsítványtároló – köztes**
8. Ha elkészült, válassza az **OK** gombot, lépjen vissza a **Profil létrehozása** panelre, és válassza a **Létrehozás** gombot.
A profil megjelenik a profilok listájában az *eszköz konfigurációja – profilok* nézet panelen, a **megbízható tanúsítvány**profiljának típusától függően.  Ügyeljen arra, hogy ezt a profilt olyan eszközökhöz rendelje, amelyek SCEP-vagy PKCS-tanúsítványokat fognak használni. A profil csoportokhoz rendeléséhez lásd: [eszközbeállítások társítása](../configuration/device-profile-assign.md).

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

