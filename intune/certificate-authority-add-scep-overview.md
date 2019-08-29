---
title: Harmadik féltől származó hitelesítésszolgáltatók (CA) használata az Azure-beli SCEP-val Microsoft Intune-Azure | Microsoft Docs
description: A Microsoft Intuneban hozzáadhat egy gyártót vagy külső hitelesítésszolgáltatót (CA), amely a SCEP protokollt használó mobileszközök számára állít ki tanúsítványokat. Ebben az áttekintő cikkben egy Azure Active Directory (Azure AD) alkalmazás ad engedélyeket a Microsoft Intune-nak tanúsítványok hitelesítésére. Ezután az SCEP-kiszolgáló beállítása következik a tanúsítványok kiadásához, az alkalmazás azonosítója, a hitelesítési kulcs és az AAD-alkalmazás bérlőazonosítója alapján.
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
ms.openlocfilehash: faff917dfafaaedb988cbbfb8174547f0b0ccf3b
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122264"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Partner hitelesítésszolgáltató hozzáadása az Intune-ban SCEP protokollal

Harmadik féltől származó hitelesítésszolgáltatók (CA) használata az Intune-nal. A külső hitelesítésszolgáltatók létrehozhatnak új vagy megújított tanúsítványokat a Egyszerű tanúsítványigénylési protokoll (SCEP) használatával, és támogathatják a Windows, az iOS, az Android és a macOS rendszerű eszközöket.

A funkció használata két részből áll: a nyílt forráskódú API-val kapcsolatos és az Intune-rendszergazdai feladatokból.

**1. rész – Nyílt forráskódú API használata**  
A Microsoft létrehozott egy API-t az Intune-nal való integráláshoz. Bár az API-val ellenőrizheti a tanúsítványokat, elküldheti a sikeres vagy sikertelen értesítéseket, és SSL-t, különösen SSL socket Factoryt használhat az Intune-nal való kommunikációhoz.

Az API az [Intune SCEP API nyilvános GitHub-tárházban](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) érhető el, ahonnan letöltheti és felhasználhatja saját megoldásaiban. Használja ezt az API-t külső SCEP-kiszolgálókkal az egyéni Challenge-ellenőrzés futtatásához az Intune-nal, mielőtt SCEP a tanúsítványt egy eszközhöz.

Az [Intune-integráció SCEP-felügyeleti megoldásról](scep-libraries-apis.md) szóló témakör részletesebben is leírja az API használatát, metódusait és az elkészített megoldások tesztelését.

**2. rész – Az alkalmazás és profil létrehozása**  
Azure Active Directory-alkalmazás használatakor az eszközökről érkező SCEP-kérelmek kezelésének jogosultságai az Intune-nak delegálhatók. Az Azure AD-alkalmazás a fejlesztő által létrehozott API-megoldásban használt alkalmazásazonosítót és hitelesítési kulcsot is tartalmazza. A rendszergazdák ezután SCEP-tanúsítványokat hozhatnak létre és telepíthetnek az Intune-nal, és megtekinthetik a jelentéseket a telepítési állapotáról az eszközökön.

Ez a cikk rendszergazdai szempontból tekinti át ezt a funkciót, beleértve az Azure AD-alkalmazás létrehozását is.

## <a name="overview"></a>Áttekintés

A következő lépések áttekintést nyújtanak a tanúsítványok SCEP való használatáról az Intune-ban:

1. Az Intune-ban egy rendszergazda létrehoz egy SCEP-tanúsítványprofilt, majd a profil céljaként felhasználókat vagy eszközöket jelöl ki.
2. Az eszköz bejelentkezik az Intune-ba.
3. Az Intune létrehoz egy egyedi SCEP ellenőrző kérdést. További integritás-ellenőrző információkat is megad, például a várt tárgyat és SAN-t.
4. Az Intune az ellenőrző kérdést és az integritás-ellenőrző információkat is titkosítja és aláírja, majd az SCEP-kérelemmel együtt elküldi ezt az információt az eszköznek.
5. Az eszköz generál egy tanúsítvány-aláírási kérelmet (CSR) és egy nyilvános/titkos kulcspárt az eszközön az Intune-ból leküldött SCEP-tanúsítványprofil alapján.
6. A CSR és a titkosított/aláírt ellenőrző kérdés van elküldve a külső SCEP-kiszolgálói végponthoz.
7. Az SCEP-kiszolgáló elküldi a CSR-t és az ellenőrző kérdést az Intune-nak. Az Intune ekkor ellenőrzi az aláírást, visszafejti a tartalmat és összeveti a CSR-t az integritás-ellenőrző információval.
8. Az Intune választ küld az SCEP-kiszolgálónak, amelyben tudatja, hogy az ellenőrző kérdésen alapuló hitelesítés sikeres volt vagy sem.  
9. Ha az ellenőrző kérdésen alapuló hitelesítés sikeres, az SCEP-kiszolgáló kiadja a tanúsítványt az eszköznek.

Az alábbi diagram részletesen bemutatja a külső SCEP és az Intune integrációjának folyamatát:

![Külső hitelesítésszolgáltató SCEP-jének együttműködése a Microsoft Intune-nal](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Külső hitelesítésszolgáltatóval való integráció beállítása

### <a name="validate-third-party-certification-authority"></a>Külső hitelesítésszolgáltató ellenőrzése

Külső hitelesítésszolgáltatók Intune-nal való integrálása előtt győződjön meg arról, hogy az igénybe vett hitelesítésszolgáltató támogatja az Intune-t. A [Külső hitelesítésszolgáltató partnerek](#third-party-certification-authority-partners) című szakasz (ebben a cikkben) tartalmazza ezek felsorolását. Alaposabban is tájékozódhat hitelesítésszolgáltatója útmutatója alapján. A hitelesítésszolgáltatók saját megvalósítási módjukra vonatkozó telepítési utasításokat is megadhatnak.

### <a name="authorize-communication-between-ca-and-intune"></a>A hitelesítésszolgáltató és az Intune közötti kommunikáció engedélyezése

Ahhoz, hogy egy külső SCEP-kiszolgáló egyéni kérdésen alapuló ellenőrzést végezhessen az Intune-nal, készítsen egy alkalmazást az Azure AD-ban. Ez az alkalmazás delegált jogosultságokat ad az Intune-nak az SCEP-kérelmek ellenőrzéséhez.

Ehhez mindenképpen rendelkeznie kell az Azure AD-alkalmazás regisztrálásához szükséges engedélyekkel. Tekintse meg a [szükséges engedélyeket](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)az Azure ad dokumentációjában.

#### <a name="create-an-application-in-azure-active-directory"></a>Alkalmazás létrehozása Azure Active Directory  

1. A [Azure Portal](https://portal.azure.com)válassza a **Azure Active Directory** > **alkalmazás**-regisztrációk, majd az **új regisztráció**lehetőséget.  

2. Az **alkalmazás regisztrálása** lapon a következő részleteket kell megadnia:  
   - A **név** szakaszban adjon meg egy értelmes alkalmazás nevét.  
   - A **támogatott fióktípus** szakaszban válassza a fiókok lehetőséget **bármely szervezeti címtárban**.  
   - Az **átirányítási URI**esetében hagyja meg az alapértelmezett webes beállítást, majd adja meg a bejelentkezési URL-címet a külső gyártó SCEP-kiszolgálójához.  

3. Válassza a **regisztráció** lehetőséget az alkalmazás létrehozásához és az új alkalmazás Áttekintés lapjának megnyitásához.  

4. Az alkalmazás **áttekintése** lapon másolja az **alkalmazás (ügyfél) azonosító** értékét, és jegyezze fel későbbi használatra. Ezt az értéket később kell megadnia.  

5. Az alkalmazás navigációs ablaktábláján lépjen a **tanúsítványok & titkok** elemre a **kezelés**alatt. Válassza az **új ügyfél titka** gombot. Adjon meg egy értéket a Leírás mezőben, válassza kia lejárati lehetőséget, majd a **Hozzáadás** gombra kattintva adja meg az ügyfél titkos kulcsának *értékét* . 
   > [!IMPORTANT]  
   > Mielőtt elhagyja ezt a lapot, másolja ki az ügyfél titkos kulcsának értékét, és jegyezze fel későbbi használatra a külső HITELESÍTÉSSZOLGÁLTATÓ által megvalósított implementációval. Ez az érték nem jelenik meg újra. Mindenképpen tekintse át a külső HITELESÍTÉSSZOLGÁLTATÓ útmutatását, hogy miként szeretné beállítani az alkalmazás AZONOSÍTÓját, a hitelesítési kulcsot és a bérlő AZONOSÍTÓját.  

6. Jegyezze fel a **bérlő azonosítóját**. A bérlő azonosítója a fiókhoz tartozó @ bejelentkezés után a tartomány szövege. Ha például a fiókja *admin@name.onmicrosoft.com* , akkor a bérlő azonosítója **Name.onmicrosoft.com**.  

7. Az alkalmazás navigációs ablaktábláján nyissa meg az **API-engedélyeket** a **kezelés**területen, majd válassza az **engedély hozzáadása**elemet.  

8. Az **API-engedélyek kérése** lapon válassza az **Intune**lehetőséget, majd válassza az **alkalmazás engedélyei**lehetőséget. Jelölje be a **scep_challenge_provider** jelölőnégyzetét (SCEP Challenge validate).  

   Válassza az **engedélyek hozzáadása** lehetőséget a konfiguráció mentéséhez.  

9. Maradjon az **API-engedélyek** lapon, és válassza a **rendszergazdai jóváhagyás megadása a Microsoft számára**lehetőséget, majd válassza az **Igen**lehetőséget.  
   
   Befejeződött az alkalmazás regisztrációs folyamata az Azure AD-ben.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>SCEP-tanúsítványprofil konfigurálása és telepítése
Rendszergazdaként hozzon létre egy felhasználóknak vagy eszközöknek szánt SCEP-tanúsítványprofilt. Ezt követően végezze el a profil hozzárendelését.

- [SCEP-tanúsítványprofil létrehozása](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [A tanúsítványprofil felhasználókhoz vagy eszközökhöz rendelése](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Tanúsítványok eltávolítása

Ha törli az eszköz regisztrációját vagy teljes tartalmát, a tanúsítványok törölve lesznek. A tanúsítványok nem lesznek visszavonva.

## <a name="third-party-certification-authority-partners"></a>Külső hitelesítésszolgáltató partnerek
Az alábbi külső hitelesítésszolgáltatók támogatják az Intune-t:

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [EJBCA GitHub nyílt forráskódú verzió](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Ha Ön a terméke Intune-nal való integrálása iránt érdeklődő külső hitelesítésszolgáltatót képvisel, tekintse át az API-val kapcsolatos útmutatót:

- [Intune SCEP API GitHub-tárház](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API útmutató külső hitelesítésszolgáltatóknak](scep-libraries-apis.md)

## <a name="see-also"></a>Lásd még:

- [Tanúsítványprofilok konfigurálása](certificates-scep-configure.md)
- [Intune SCEP API GitHub-tárház](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API útmutató külső hitelesítésszolgáltatóknak](scep-libraries-apis.md)
