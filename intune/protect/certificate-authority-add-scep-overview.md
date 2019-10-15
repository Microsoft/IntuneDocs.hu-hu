---
title: Harmadik féltől származó hitelesítésszolgáltatók (CA) használata az Azure-beli SCEP-val Microsoft Intune-Azure | Microsoft Docs
description: A Microsoft Intuneban hozzáadhat egy gyártót vagy külső hitelesítésszolgáltatót (CA), amely a SCEP protokollt használó mobileszközök számára állít ki tanúsítványokat. Ebben az áttekintésben egy Azure Active Directory (Azure AD) alkalmazás Microsoft Intune engedélyeket biztosít a tanúsítványok érvényesítéséhez. Ezután használja a HRE alkalmazás AZONOSÍTÓját, hitelesítési kulcsát és bérlői AZONOSÍTÓját a SCEP-kiszolgáló telepítésekor a tanúsítványok kiállításához.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b82124fe8f6da7116c8333e293f219d7c667f9c
ms.sourcegitcommit: a2654f3642b43b29ab0e1cbb2dfa2b56aae18d0e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72310914"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Partner hitelesítésszolgáltató hozzáadása az Intune-ban az SCEP használatával

Harmadik féltől származó hitelesítésszolgáltatók (CA) használata az Intune-nal. A külső hitelesítésszolgáltatók létrehozhatnak új vagy megújított tanúsítványokat a Egyszerű tanúsítványigénylési protokoll (SCEP) használatával, és támogathatják a Windows, az iOS, az Android és a macOS rendszerű eszközöket.

A szolgáltatás két részből áll: a nyílt forráskódú API-val és az Intune rendszergazdai feladataival.

**1. rész – nyílt forráskódú API használata**  
A Microsoft létrehozott egy API-t az Intune-nal való integráláshoz. Bár az API-val ellenőrizheti a tanúsítványokat, elküldheti a sikeres vagy sikertelen értesítéseket, és SSL-t, különösen SSL socket Factoryt használhat az Intune-nal való kommunikációhoz.

Az API az [INTUNE SCEP API nyilvános GitHub-tárházában](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) érhető el, amellyel letöltheti és használhatja a megoldásait. Használja ezt az API-t külső SCEP-kiszolgálókkal az egyéni Challenge-ellenőrzés futtatásához az Intune-nal, mielőtt SCEP a tanúsítványt egy eszközhöz.

Az [INTUNE SCEP-kezelési megoldással való integráció](scep-libraries-apis.md) részletesen ismerteti az API-k használatát, a módszereiket, valamint a felépített megoldás tesztelését.

**2. rész – az alkalmazás és a profil létrehozása**  
Azure Active Directory-(Azure AD-) alkalmazás használatával jogosultságokat delegálhat az Intune-nak az eszközökről érkező SCEP-kérelmek kezeléséhez. Az Azure AD-alkalmazás tartalmazza a fejlesztő által létrehozott API-megoldásban használt alkalmazás-azonosító és hitelesítési kulcs értékeit. A rendszergazdák ezután SCEP-tanúsítványokat hozhatnak létre és telepíthetnek az Intune-nal, és megtekinthetik a jelentéseket a telepítési állapotáról az eszközökön.

Ez a cikk áttekintést nyújt a szolgáltatásról a rendszergazda szemszögéből, beleértve az Azure AD-alkalmazás létrehozását is.

## <a name="overview"></a>Áttekintés

A következő lépések áttekintést nyújtanak a tanúsítványok SCEP való használatáról az Intune-ban:

1. Az Intune-ban a rendszergazda létrehoz egy SCEP, majd a felhasználók vagy eszközök számára célozza meg a profilt.
2. Az eszköz bejelentkezik az Intune-ba.
3. Az Intune egy egyedi SCEP kihívást hoz létre. Emellett további integritás-ellenőrzési információkat is felvesz, például a várt tárgyat és a SAN-t.
4. Az Intune titkosítja és aláírja a kérdés-és integritás-ellenőrzési információkat, majd elküldi ezeket az adatokat az eszköznek a SCEP-kéréssel.
5. Az eszköz létrehoz egy tanúsítvány-aláírási kérelmet (CSR) és egy nyilvános/titkos kulcspár az eszközön az Intune-ból leküldett SCEP-tanúsítvány alapján.
6. A CSR és a titkosított/aláírt kihívás a külső gyártótól származó SCEP-kiszolgáló végpontja számára lesz elküldve.
7. A SCEP-kiszolgáló a CSR-t és a kihívást az Intune-nak küldi el. Az Intune ezután érvényesíti az aláírást, visszafejti a hasznos adatokat, és összehasonlítja a CSR-ellenőrzési információkat.
8. Az Intune egy választ küld a SCEP-kiszolgálónak, és megállapítja, hogy a kérdéses ellenőrzés sikeres-e.  
9. Ha a probléma ellenőrzése sikeres volt, a SCEP-kiszolgáló kiadja a tanúsítványt az eszköznek.

Az alábbi ábrán az Intune-nal való külső SCEP-integráció részletes folyamata látható:

![A harmadik féltől származó hitelesítésszolgáltatók SCEP integrálása Microsoft Intune](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Külső gyártótól származó HITELESÍTÉSSZOLGÁLTATÓI integráció beállítása

### <a name="validate-third-party-certification-authority"></a>Harmadik féltől származó hitelesítésszolgáltató ellenőrzése

A külső hitelesítésszolgáltatók Intune-nal való integrálása előtt ellenőrizze, hogy az Ön által használt HITELESÍTÉSSZOLGÁLTATÓ támogatja-e az Intune-ot. [Harmadik féltől származó hitelesítésszolgáltatói partnerek](#third-party-certification-authority-partners) (ebben a cikkben) tartalmaz egy listát. További információkért tekintse meg a hitelesítésszolgáltató útmutatását is. Előfordulhat, hogy a HITELESÍTÉSSZOLGÁLTATÓ a megvalósításra vonatkozó beállítási utasításokat tartalmaz.

### <a name="authorize-communication-between-ca-and-intune"></a>A CA és az Intune közötti kommunikáció engedélyezése

Ha engedélyezni szeretné, hogy egy külső gyártótól származó SCEP-kiszolgáló egyéni Challenge-ellenőrzést futtasson az Intune-nal, hozzon létre alkalmazást az Azure AD-ben. Ez az alkalmazás delegált jogokat biztosít az Intune-nak a SCEP-kérések érvényesítéséhez.

Győződjön meg arról, hogy rendelkezik az Azure AD-alkalmazás regisztrálásához szükséges engedélyekkel. Tekintse meg a [szükséges engedélyeket](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)az Azure ad dokumentációjában.

#### <a name="create-an-application-in-azure-active-directory"></a>Alkalmazás létrehozása az Azure Active Directoryban  

1. A [Azure Portal](https://portal.azure.com)nyissa meg a **Azure Active Directory** > **alkalmazás regisztrációját**, majd válassza az **új regisztráció**lehetőséget.  

2. Az **alkalmazás regisztrálása** lapon a következő részleteket kell megadnia:  
   - A **név** szakaszban adjon meg egy értelmes alkalmazás nevét.  
   - A **támogatott fióktípus** szakaszban válassza a fiókok lehetőséget **bármely szervezeti címtárban**.  
   - Az **átirányítási URI**esetében hagyja meg az alapértelmezett webes beállítást, majd adja meg a bejelentkezési URL-címet a külső gyártó SCEP-kiszolgálójához.  

3. Válassza a **regisztráció** lehetőséget az alkalmazás létrehozásához és az új alkalmazás Áttekintés lapjának megnyitásához.  

4. Az alkalmazás **áttekintése** lapon másolja az **alkalmazás (ügyfél) azonosító** értékét, és jegyezze fel későbbi használatra. Ezt az értéket később kell megadnia.  

5. Az alkalmazás navigációs ablaktábláján lépjen a **tanúsítványok & titkok** elemre a **kezelés**alatt. Válassza az **új ügyfél titka** gombot. Adjon meg egy értéket a Leírás mezőben, válassza ki a **lejárati**lehetőséget, majd a **Hozzáadás** gombra kattintva adja meg az ügyfél titkos kulcsának *értékét* . 
   > [!IMPORTANT]  
   > Mielőtt elhagyja ezt a lapot, másolja ki az ügyfél titkos kulcsának értékét, és jegyezze fel későbbi használatra a külső HITELESÍTÉSSZOLGÁLTATÓ által megvalósított implementációval. Ez az érték nem jelenik meg újra. Mindenképpen tekintse át a külső HITELESÍTÉSSZOLGÁLTATÓ útmutatását, hogy miként szeretné beállítani az alkalmazás AZONOSÍTÓját, a hitelesítési kulcsot és a bérlő AZONOSÍTÓját.  

6. Jegyezze fel a **bérlő azonosítóját**. A bérlő azonosítója a fiókhoz tartozó @ bejelentkezés után a tartomány szövege. Ha például a fiókja *admin@name.onmicrosoft.com* , akkor a bérlő azonosítója **Name.onmicrosoft.com**.  

7. Az alkalmazás navigációs ablaktábláján nyissa meg az **API-engedélyeket** a **kezelés**területen, majd válassza az **engedély hozzáadása**elemet.  

8. Az **API-engedélyek kérése** lapon válassza az **Intune**lehetőséget, majd válassza az **alkalmazás engedélyei**lehetőséget. Jelölje be a **scep_challenge_provider** jelölőnégyzetét (SCEP Challenge validate).  

   Válassza az **engedélyek hozzáadása** lehetőséget a konfiguráció mentéséhez.  

9. Maradjon az **API-engedélyek** lapon, és válassza a **rendszergazdai jóváhagyás megadása a Microsoft számára**lehetőséget, majd válassza az **Igen**lehetőséget.  
   
   Befejeződött az alkalmazás regisztrációs folyamata az Azure AD-ben.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>SCEP-tanúsítvány profiljának konfigurálása és üzembe helyezése
Rendszergazdaként hozzon létre egy SCEP, amelyet a felhasználók vagy az eszközök célzására szeretne használni. Ezután rendelje hozzá a profilt.

- [SCEP-tanúsítvány profiljának létrehozása](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [A tanúsítvány profiljának kiosztása](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Tanúsítványok eltávolítása

Ha törli vagy törli az eszköz regisztrációját, a rendszer eltávolítja a tanúsítványokat. A tanúsítványok nem vonhatók vissza.

## <a name="third-party-certification-authority-partners"></a>Harmadik féltől származó hitelesítésszolgáltatók partnerei
A következő harmadik féltől származó hitelesítésszolgáltatók támogatják az Intune-t:

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [EJBCA GitHub nyílt forráskódú verziója](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Ha Ön a termék Intune-nal való integrálását segítő, harmadik féltől származó HITELESÍTÉSSZOLGÁLTATÓ, tekintse át az API-útmutatót:

- [Intune SCEP API GitHub-adattár](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API-útmutató harmadik fél hitelesítésszolgáltatóinak](scep-libraries-apis.md)

## <a name="see-also"></a>Lásd még:

- [Tanúsítványok profiljainak konfigurálása](certificates-scep-configure.md)
- [Intune SCEP API GitHub-adattár](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API-útmutató harmadik fél hitelesítésszolgáltatóinak](scep-libraries-apis.md)
