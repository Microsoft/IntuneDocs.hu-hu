---
title: E-mail aláírása és titkosítása S/MIME-Microsoft Intune-Azure használatával | Microsoft Docs
description: Megtudhatja, hogyan használhatja az e-mailek digitális tanúsítványait Microsoft Intune az e-mailek eszközökön való aláírására és titkosítására. Ezeket a tanúsítványokat nevezzük S/MIME-nek, és az eszköz konfigurációs profiljaival vannak konfigurálva. Az aláírási és titkosítási tanúsítványok PKCS vagy privát tanúsítványokat használnak, és a tanúsítványokat egy összekötő használatával importálják.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15147a1d9ffd82e2f900d15c4a9d2b4d23ad23e3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515152"
---
# <a name="smime-overview-to-sign-and-encrypt-email-in-intune"></a>S/MIME-áttekintés az e-mailek aláírásához és titkosításához az Intune-ban

Az e-mail-tanúsítványok, más néven az S/MIME-tanúsítvány, a titkosítás és a visszafejtés használatával biztosítanak extra biztonságot az e-mailes kommunikációhoz. A Microsoft Intune az S/MIME-tanúsítványokkal aláírhatja és titkosíthatja az e-maileket a következő platformokat futtató mobileszközök számára:

- Android:
- iOS/iPadOS
- macOS
- Windows 10 és újabb
- Windows Phone

IOS/iPadOS eszközökön létrehozhat egy Intune által felügyelt e-mail-profilt, amely S/MIME-t és tanúsítványokat használ a bejövő és kimenő e-mailek aláírására és titkosítására. Más platformokon az S/MIME lehet támogatott vagy nem támogatott. Ha támogatott, telepítse az S/MIME-aláírást és titkosítást használó tanúsítványokat. Ezután a végfelhasználó engedélyezi az S/MIME használatát az e-mail-alkalmazásban.

Az S/MIME-alapú e-mailek aláírásával és titkosításával kapcsolatos további információkért lásd: [s/MIME az üzenetek aláírásához és titkosításához](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

Ez a cikk áttekintést nyújt az S/MIME-tanúsítványok használatáról az e-mailek aláírására és titkosítására az eszközökön.

## <a name="signing-certificates"></a>Aláíró tanúsítványok

Az aláíráshoz használt tanúsítványok lehetővé teszik, hogy az ügyfél e-mail-alkalmazás biztonságosan kommunikáljon a levelezési kiszolgálóval.

Az aláíró tanúsítványok használatához hozzon létre egy sablont az aláírásra fókuszáló hitelesítésszolgáltató (CA) számára. A Microsoft Active Directory hitelesítésszolgáltatóhoz [A kiszolgálói tanúsítvány-sablon konfigurálása](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) című cikk ismerteti a tanúsítványsablonok létrehozásának lépéseit.

Az Intune-beli aláíró tanúsítványok PKCS-tanúsítványokat használnak. A [PKCS-tanúsítványok konfigurálása és használata](certficates-pfx-configure.md) című cikk leírja, hogyan telepíthet és használhat PKCS-tanúsítványokat Intune-környezetében. Ezek a lépések a következők:

- A PKCS-tanúsítványkérelmek támogatásához töltse le és telepítse a Microsoft Intune Tanúsítvány-összekötőt.
- Hozzon létre egy megbízható főtanúsítvány-profilt eszközeihez. E lépés során megbízható főtanúsítványokat és köztes tanúsítványokat is használni kell a hitelesítésszolgáltatónál, majd üzembe kell helyezni a profilt az eszközökön.
- Hozzon létre egy PKCS-tanúsítványprofilt az elkészült tanúsítványsablon használatával. Ez a profil adja ki az aláíró tanúsítványokat az eszközöknek, és helyezi üzembe a PKCS-tanúsítványprofilt az eszközökön.

Aláíró tanúsítvány egy adott felhasználó számára is importálható. Az aláíró tanúsítvány minden olyan eszközön telepítve van, amelyet a felhasználó regisztrál. A tanúsítványok Intune-ba való importálásához használja [a GitHubon elérhető PowerShell-parancsmagokat](https://github.com/Microsoft/Intune-Resource-Access). Az Intune-ba importált PKCS-tanúsítványok e-mail-aláíráshoz való üzembe helyezéséhez kövesse a [PKCS-tanúsítványok konfigurálása és használata az Intune-nal](certficates-pfx-configure.md) című témakörben leírt lépéseket. Ezek a lépések a következők:

- Töltse le és telepítse a Microsoft Intune-hoz készült PFX tanúsítvány-összekötőt. Ez az összekötő juttatja el az importált PKCS-tanúsítványokat az eszközökre.
- Importáljon S/MIME e-mail-aláíró tanúsítványokat az Intune-ba.
- Hozzon létre egy importált PKCS-tanúsítványprofilt. Ez a profil juttatja el az importált PKCS-tanúsítványokat a megfelelő felhasználók eszközeire.

## <a name="encryption-certificates"></a>Titkosítási tanúsítványok

A titkosításhoz használt tanúsítványok biztosítják, hogy a titkosított e-mailt csak az a címzett tudja visszafejteni, akinek szánták. A S/MIME-titkosítás az e-mail-kommunikációban használható újabb biztonsági réteg.

Amikor titkosított e-mailt küld egy másik felhasználónak, beszerzi a címzett titkosítási tanúsítványának nyilvános kulcsát, és titkosítja a küldeni kívánt e-mailt. A címzett a titkos kulcsával oldja fel az e-mail titkosítását az eszközén. A felhasználók az e-mailek titkosításához használt korábbi tanúsítványokkal is rendelkezhetnek. Az e-mailek sikeres visszafejtéséhez minden ilyen tanúsítványnak telepítve kell lennie az adott felhasználó összes eszközén.

Az e-mail-titkosítási tanúsítványokat ajánlott nem az Intune-ban létrehozni. Bár az Intune támogatja titkosítást támogató PKCS-tanúsítványok kiállítását, az Intune eszközönként egyedi tanúsítványokat hoz létre. Az eszközönként egyedi tanúsítvány nem ideális S/MIME-titkosítás esetén, amikor a titkosítási tanúsítványnak a felhasználó minden eszközén meg kellene lennie.

S/MIME-tanúsítványok Intune-nal való üzembe helyezéséhez egy felhasználó összes titkosítási tanúsítványát importálnia kell az Intune-ba. Az Intune ezután telepíti az összes tanúsítványt minden olyan eszközre, amelyet a felhasználó regisztrál. A tanúsítványok Intune-ba való importálásához használja [a GitHubon elérhető PowerShell-parancsmagokat](https://github.com/Microsoft/Intune-Resource-Access).

Az Intune-ba importált PKCS-tanúsítványok e-mail-titkosításhoz való üzembe helyezéséhez kövesse a [PKCS-tanúsítványok konfigurálása és használata az Intune-nal](certficates-pfx-configure.md) című témakörben leírt lépéseket. Ezek a lépések a következők:

- Töltse le és telepítse a Microsoft Intune-hoz készült PFX tanúsítvány-összekötőt. Ez az összekötő juttatja el az importált PKCS-tanúsítványokat az eszközökre.
- Importáljon S/MIME e-mail-titkosítási tanúsítványokat az Intune-ba.
- Hozzon létre egy importált PKCS-tanúsítványprofilt. Ez a profil juttatja el az importált PKCS-tanúsítványokat a megfelelő felhasználók eszközeire.

 > [!NOTE]
 > Az importált S/MIME titkosítási tanúsítványok el lesznek távolítva az Intune-ból, ha törlik a céges adatokat, vagy ha a felhasználók regisztrációját törlik a felügyeleti rendszerben. A tanúsítványok azonban nem lesznek visszavonva a hitelesítésszolgáltatónál.

## <a name="smime-email-profiles"></a>S/MIME e-mail-profilok

Miután létrehozta az S/MIME-aláírási és titkosítási tanúsítvány profilokat, [engedélyezheti az s/MIME-t iOS/iPadOS natív levelezéshez](../configuration/email-settings-ios.md).

## <a name="next-steps"></a>További lépések

- [SCEP használata tanúsítványokhoz](certificates-scep-configure.md)
- [PKCS-tanúsítványok használata](certficates-pfx-configure.md)
- [Partneri HITELESÍTÉSSZOLGÁLTATÓ használata](certificate-authority-add-scep-overview.md)
- [PKCS-tanúsítványok kiállítása a Symantec PKI Manager webszolgáltatásból](certificates-digicert-configure.md)
