---
title: A mobileszközök származtatott hitelesítő adatainak használata a Microsoft Intune-Azure-ban | Microsoft Docs
description: Az Intune VPN, e-mailek, Wi-Fi profilok, alkalmazások és az S/MIME és titkosítás hitelesítési módszere a mobileszközök származtatott hitelesítő adatainak használata. A származtatott hitelesítő adatok a 800-157-es speciális kiadványra vonatkozó NIST-irányelvek megvalósítása.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c42e5ef50f8a5a8514bc43670fc743f42b1b2d6
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585928"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Származtatott hitelesítő adatok használata Microsoft Intuneban

*Ez a cikk az iOS-t futtató eszközökre vonatkozik*

Olyan környezetben, ahol intelligens kártyák szükségesek a hitelesítéshez, a titkosításhoz és az aláíráshoz, mostantól használhatja az Intune-t olyan mobileszközök kiépítéséhez, amelyek egy felhasználó intelligens kártyáján alapuló tanúsítvánnyal rendelkeznek. A tanúsítvány neve *származtatott hitelesítő adat*. Az Intune [több származtatott hitelesítőadat](#supported-issuers)-kiállítók használatát is lehetővé teszi, de egyszerre csak egyetlen kiállítót használhat. 

A származtatott hitelesítő adatok a National Institute of Standards and Technology (NIST) irányelvek megvalósítása a származtatott személyes identitás-ellenőrzési (PIV) hitelesítő adatokhoz a speciális kiadvány (SP) 800-157-es részeként.  

**Az Intune implementációja**:  

- Az Intune rendszergazdája úgy konfigurálja a bérlőt, hogy a támogatott származtatott hitelesítőadat-kiállítóval működjenek. Nem kell konfigurálnia az Intune-specifikus beállításokat a származtatott hitelesítőadat-kiállító rendszerében.

- Az Intune rendszergazdája a következő objektumokhoz tartozó *hitelesítési módszerként* adja meg a **származtatott hitelesítő adatokat** :  

  - Gyakori profilok, például Wi-Fi, VPN és e-mailek, beleértve az iOS Native mail alkalmazást 

  - Alkalmazás-hitelesítés

  - S/MIME-aláírás és-titkosítás 

- A felhasználók egy származtatott hitelesítő adatokat kapnak a számítógép intelligens kártyájának használatával, hogy hitelesítsék magukat a származtatott hitelesítő adat kiállítójának. A kiállító ezt követően a mobileszköz számára egy, az intelligens kártyából származtatott tanúsítványt bocsát ki. 

- Miután az eszköz megkapja a származtatott hitelesítő adatokat, használja a rendszer a hitelesítést, az S/MIME-aláírást és a titkosítást, amikor az alkalmazások vagy az erőforrás-hozzáférési profilok a származtatott hitelesítő adatokat igénylik. 

## <a name="prerequisites"></a>Előfeltételek

Mielőtt a bérlőt a származtatott hitelesítő adatok használatára konfigurálja, tekintse át a következő információkat.

### <a name="supported-platforms"></a>Támogatott platformok

Az Intune a következő operációsrendszer-platformokon támogatja a származtatott hitelesítő adatokat:
- iOS/iPadOS
 
### <a name="supported-issuers"></a>Támogatott kibocsátók

Az Intune egyetlen származtatott hitelesítőadat-kiállítót támogat a bérlők esetében. Konfigurálhatja az Intune-t úgy, hogy az a következő kibocsátókkal működjön:  

- **DISA fajtatiszta**: https://cyber.mil/pki-pke/purebred/ 
- **Entrust DataCard**: https://www.entrustdatacard.com/
- **Közbenjárás**: https://www.intercede.com/

A különböző kiállítók használatával kapcsolatos fontos információkért tekintse át az adott kiállítóhoz tartozó útmutatást, beleértve a kibocsátók végfelhasználói munkafolyamatát. További információ: a [származtatott hitelesítő adatok tervezése](#plan-for-derived-credentials) ebben a cikkben.

> [!IMPORTANT]  
> Ha töröl egy származtatott hitelesítő kiállítót a bérlőtől, a kibocsátón keresztül létrehozott származtatott hitelesítő adatok már nem fognak működni.  
> 
> Lásd: [a származtatott hitelesítőadat-kiállító módosítása a](#change-the-derived-credential-issuer) cikk későbbi részében.   

### <a name="company-portal-app"></a>Vállalati portál alkalmazás

Tervezze meg a Intune Céges portál alkalmazás telepítését olyan eszközökre, amelyek egy származtatott hitelesítő adatot fognak regisztrálni. Az eszköz felhasználói a Céges portál alkalmazást használják a hitelesítő adatok regisztrálási folyamatának elindításához. 

IOS-eszközök esetén tekintse [meg az iOS-es áruházbeli alkalmazások hozzáadása a Microsoft Intunehoz](../apps/store-apps-ios.md)című témakört.

## <a name="plan-for-derived-credentials"></a>A származtatott hitelesítő adatok megtervezése

A származtatott hitelesítőadat-kiállító létrehozása előtt tekintse át a következő szempontokat.  

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1.) tekintse át a kiválasztott származtatott hitelesítőadat-kiállító dokumentációját  

A kibocsátó konfigurálása előtt tekintse át a kibocsátó dokumentációját, hogy megtudja, hogyan kézbesíti a rendszer származtatott hitelesítő adatokat az eszközöknek.  

A kiválasztott kibocsátótól függően szükség lehet arra, hogy a felhasználók a beléptetéskor is elérhetők legyenek, hogy segítsenek a felhasználóknak a folyamat befejezésében. Tekintse át a jelenlegi Intune-konfigurációkat is, hogy ne blokkolja az eszközök vagy a felhasználók számára a hitelesítő adatok kérésének befejezéséhez szükséges hozzáférést. 

Előfordulhat például, hogy a feltételes hozzáférés használatával letiltja a nem megfelelő eszközökhöz való hozzáférést az e-mailekhez. Ha e-mailben értesítést küld a felhasználótól a származtatott hitelesítő adatok beléptetési folyamatának elindításához, előfordulhat, hogy a felhasználók nem kapják meg ezeket az utasításokat, amíg nem felelnek meg a házirendnek.  

Hasonlóképpen, egyes származtatott hitelesítőadat-kérelmek munkafolyamataihoz az eszköz kamerájának használata szükséges a képernyőn megjelenő QR-kódok vizsgálatához. Ez a kód a felhasználó intelligens kártyájának hitelesítő adataival hivatkozik arra a hitelesítési kérelemre, amely a származtatott hitelesítő adatok kibocsátóján történt. Ha az eszköz konfigurációja tiltja a fényképezőgép használatát, a felhasználó nem tudja befejezni a származtatott hitelesítő adatok beléptetésére vonatkozó kérelmet.  

Általános információk:  

- Egyszerre csak egyetlen kiállítót lehet beállítani, és a kiállító a bérlő összes felhasználója és támogatott eszköze számára elérhető.

- A felhasználók nem kapnak értesítést arról, hogy regisztrálniuk kell a származtatott hitelesítő adatokat, amíg meg nem célozza azokat olyan házirenddel, amely származtatott hitelesítő adatokat igényel.

- Az értesítés az Céges portál, e-mailben vagy mindkettőn keresztüli alkalmazás-értesítésen keresztül történhet. Ha az e-mailes értesítések használatát választja, és az engedélyezett feltételes hozzáférést használja, előfordulhat, hogy a felhasználók nem kapják meg az e-mailes értesítést, ha az eszközük nem megfelelő.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2.) tekintse át a kiválasztott kiállító végfelhasználói munkafolyamatát

Az alábbiakban az egyes támogatott partnerekkel kapcsolatos legfontosabb szempontokat és a kibocsátók végfelhasználói munkafolyamatára mutató hivatkozásokat talál.  Ismerkedjen meg ezekkel az információkkal, így biztosíthatja, hogy az Intune-szabályzatok és-konfigurációk ne gátolják meg a felhasználókat és az eszközöket abban, hogy a kibocsátótól származó származtatott hitelesítő adatokat bejegyezzenek.

#### <a name="disa-purebred"></a>DISA fajtatiszta

Tekintse át a [DISA fajtatiszta felhasználói munkafolyamatát](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). A munkafolyamat legfontosabb követelményei a következők:  

- A felhasználóknak hozzáférésre van szükségük egy számítógéphez vagy KIOSZKhoz, ahol az intelligens kártyájuk használatával hitelesíthetők a kibocsátóban. 

- A származtatott hitelesítő adatokhoz regisztrálni kívánt eszközöknek telepíteniük kell a Intune Céges portál alkalmazást.

- Az Intune használatával [telepítse a DISA fajtatiszta alkalmazást](#deploy-the-disa-purebred-app) olyan eszközökre, amelyek egy származtatott hitelesítő adatot fognak regisztrálni. Ezt az alkalmazást az Intune-nal kell telepíteni, hogy az felügyelhető legyen, és a Intune Céges portál alkalmazással is működjön. Ezt az alkalmazást az eszköz felhasználói használják a származtatott hitelesítőadat-kérelem elvégzéséhez. 

- A DISA fajtatiszta alkalmazásnak egy [alkalmazásbeli VPN](../configuration/vpn-settings-configure.md) -t kell használnia annak biztosításához, hogy az alkalmazás hozzáférhessen a származtatott hitelesítő adatok beléptetése során a DISA fajtatiszta szolgáltatáshoz. 

- A beléptetési folyamat során az eszköz felhasználóinak működniük kell egy élő ügynökkel. A regisztráció során a rendszer időkorlátos egyszeri PIN-kódot biztosít a felhasználónak a beléptetési folyamat során.   

A DISA fajtatiszta alkalmazás beszerzésével és konfigurálásával kapcsolatos információkért lásd a jelen cikk későbbi, [a DISA fajtatiszta alkalmazás üzembe helyezésével](#deploy-the-disa-purebred-app) foglalkozó témakörét.  

#### <a name="entrust-datacard"></a>Entrust Datacard  
Tekintse át [Entrust DataCard felhasználói munkafolyamatát](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust). A munkafolyamat legfontosabb követelményei a következők: 

- A felhasználóknak hozzáférésre van szükségük egy számítógéphez vagy KIOSZKhoz, ahol az intelligens kártyájuk használatával hitelesíthetők a kibocsátóban. 

- A származtatott hitelesítő adatokhoz regisztrálni kívánt eszközöknek telepíteniük kell a Intune Céges portál alkalmazást.

- Egy eszköz kamerájának használata egy QR-kód bevizsgálatára, amely a hitelesítési kérést a mobileszközön lévő származtatott hitelesítőadat-kéréshez csatolja.

#### <a name="intercede"></a>Közbenjárni
Tekintse át a [felhasználói munkafolyamatot a közbenjáráshoz](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). A munkafolyamat legfontosabb követelményei a következők: 

- A felhasználóknak hozzáférésre van szükségük egy számítógéphez vagy KIOSZKhoz, ahol az intelligens kártyájuk használatával hitelesíthetők a kibocsátóban. 

- A származtatott hitelesítő adatokhoz regisztrálni kívánt eszközöknek telepíteniük kell a Intune Céges portál alkalmazást.

- Egy eszköz kamerájának használata egy QR-kód bevizsgálatára, amely a hitelesítési kérést a mobileszközön lévő származtatott hitelesítőadat-kéréshez csatolja.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) megbízható legfelső szintű tanúsítvány telepítése eszközökre 

A megbízható főtanúsítvány származtatott hitelesítő adatokkal van ellátva annak ellenőrzéséhez, hogy a származtatott hitelesítőadat-tanúsítványlánc érvényes és megbízható-e. A megbízható főtanúsítványt még akkor is meg kell adni, ha a házirend nem hivatkozik rá közvetlenül. Lásd: az [eszközökhöz tartozó tanúsítvány profiljának konfigurálása Microsoft Intuneban](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4.) adja meg a végfelhasználói utasításokat a származtatott hitelesítő adatok lekéréséhez 

Hozzon létre és adjon meg útmutatást a felhasználóknak a származtatott hitelesítő adatok beléptetési folyamatának elindításához, és navigáljon a kiválasztott kiállítóhoz tartozó származtatott hitelesítőadat-beléptetési munkafolyamathoz. 

Javasoljuk, hogy adjon meg egy URL-címet, amely az Ön útmutatását fogja tárolni. Ezt az URL-címet akkor kell megadnia, amikor konfigurálja a származtatott hitelesítőadat-kiállítót a bérlőhöz, és az URL-címet a Céges portál alkalmazásból elérhetővé teszi. Ha nem adja meg a saját URL-címét, az Intune egy általános részletekre mutató hivatkozást biztosít. Ezek az adatok nem fedik le az összes forgatókönyvet, és előfordulhat, hogy a környezete nem pontos. 

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5.) olyan Intune-szabályzatokat helyezhet üzembe, amelyek származtatott hitelesítő adatokat igényelnek 

Hozzon létre új házirendeket, vagy szerkessze a meglévő szabályzatokat a származtatott hitelesítő adatok használatához. A származtatott hitelesítő adatok az alkalmazás-hitelesítés, a Wi-Fi, a VPN, az e-mailek, valamint az S/MIME-aláírás és a titkosítás egyéb hitelesítési módszereit helyettesítik. 

Kerülje a származtatott hitelesítő adatok használatának megkövetelését egy olyan folyamat eléréséhez, amelyet a folyamat részeként fog használni a származtatott hitelesítő adatok beszerzéséhez, mivel ez megakadályozhatja a felhasználók számára a kérés teljesítését. 

## <a name="set-up-a-derived-credential-issuer"></a>Származtatott hitelesítőadat-kiállító beállítása

A származtatott hitelesítő adatok használatát igénylő házirendek létrehozása előtt állítson be egy hitelesítőadat-kiállítót az Intune-konzolon. A származtatott hitelesítőadat-kiállító egy bérlői szintű beállítás. A bérlők egyszerre csak egyetlen kiállítót támogatnak. 

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és nyissa meg az **eszköz konfigurációja**  > **származtatott hitelesítő adatokat**.  

   ![Származtatott hitelesítő adatok konfigurálása a konzolon](./media/derived-credentials/configure-provider.png)   

2. Adja meg a származtatott hitelesítő adatok kiállítói házirendjének felhasználóbarát **megjelenítendő nevét** .  Ez a név nem jelenik meg az eszköz felhasználói számára.

3. A **származtatott hitelesítő adatok kiállítója**mezőben válassza ki a bérlőhöz választott származtatott hitelesítő adatokat:
   - DISA fajtatiszta
   - Entrust Datacard
   - Közbenjárni  

4. A **származtatott hitelesítő adatok URL-címének** megadásával adjon meg egy olyan helyre mutató hivatkozást, amely egyéni utasításokat tartalmaz, amelyek segítségével a felhasználók származtatott hitelesítő adatokat kaphatnak a szervezet számára. Az utasításoknak a szervezet és a munkafolyamathoz kell tartoznia, amely ahhoz szükséges, hogy hitelesítő adatokat kapjon a választott kiállítótól. A hivatkozás megjelenik a Céges portál alkalmazásban, és elérhetőnek kell lennie az eszközről. 

   Ha nem adja meg a saját URL-címét, az Intune olyan általános részletekre mutató hivatkozást biztosít, amelyek nem fedik le az összes forgatókönyvet. Előfordulhat, hogy ez az általános útmutató nem pontos a környezet számára.

5. Válasszon ki egy vagy több lehetőséget az **értesítési típushoz**. Az értesítési típusok azok a módszerek, amelyeket a felhasználók tájékoztatására használ a következő esetekben:

   - Egy új származtatott hitelesítő adat beszerzéséhez regisztráljon egy eszközt egy kiállítóval. 
   - Új származtatott hitelesítő adat beszerzése, ha az aktuális hitelesítő adatok lejárata lejár. 
   - Használjon származtatott hitelesítő adatokat a Wi-Fi, VPN, e-mail vagy alkalmazás hitelesítéséhez, valamint az S/MIME aláíráshoz és a titkosításhoz. 

6. Ha elkészült, válassza a **Mentés** lehetőséget a származtatott hitelesítőadat-kiállító konfigurációjának befejezéséhez. 

A konfiguráció mentése után módosíthatja az összes mezőt, kivéve a *származtatott hitelesítő adat kiállítóját*.  A kibocsátó módosításához tekintse meg [a származtatott hitelesítőadat-kiállító módosítása](#change-the-derived-credential-issuer)című témakört. 

## <a name="deploy-the-disa-purebred-app"></a>A DISA fajtatiszta alkalmazás üzembe helyezése

*Ez a szakasz csak akkor érvényes, ha a DISA fajtatiszta*-t használja.

Ahhoz, hogy a **DISA fajtiszta** -t használja az Intune-hoz tartozó származtatott hitelesítőadat-kiállítóként, be kell szereznie a DISA fajtatiszta alkalmazást, majd az Intune használatával telepítenie kell az alkalmazást az eszközökre. Az eszköz felhasználói az eszközön használják az alkalmazást, hogy a származtatott hitelesítő adatokat a DISA fajtatiszta-ből kérjék. 

Az alkalmazás Intune-nal való üzembe helyezése mellett konfiguráljon egy Intune-os VPN-t a DISA fajtatiszta alkalmazáshoz. 

**Hajtsa végre a következő feladatokat**: 
  
1. Töltse le a [DISA fajtatiszta alkalmazást](https://cyber.mil/pki-pke/purebred/).
2. Telepítse a DISA fajtatiszta alkalmazást az Intune-ban.  Lásd: [iOS-es üzletági alkalmazás hozzáadása Microsoft Intunehoz](../apps/lob-apps-ios.md).
3. [Hozzon létre egy alkalmazásbeli VPN-t](../configuration/vpn-settings-configure.md) a DISA fajtatiszta alkalmazáshoz.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Származtatott hitelesítő adatok használata a hitelesítéshez és az S/MIME-aláíráshoz és-titkosításhoz

**Származtatott hitelesítő adatokat** is megadhat a következő profilok típusaihoz és céljaihoz:  
- [Alkalmazások](#use-derived-credentials-for-app-authentication)
- [E-mail](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [S/MIME-aláírás és-titkosítás](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  A Wi-Fi profilok esetében a *hitelesítési módszer* csak akkor érhető el, ha az **EAP-típus** az alábbi értékek egyikére van beállítva: 
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Származtatott hitelesítő adatok használata az alkalmazás hitelesítéséhez

Származtatott hitelesítő adatok használata a tanúsítványok alapú hitelesítéshez a webhelyek és az alkalmazások számára. Az alkalmazás hitelesítéséhez származtatott hitelesítő adatok továbbításához hajtsa végre az alábbi lépéseket az Intune-konzolon:  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és lépjen az **eszköz konfigurációja**  > **profilok** elemre, és válassza a **profil létrehozása**lehetőséget.

2. A **név**mezőben adjon meg egy rövid nevet a profilhoz.

3. A **Platform** beállításnál adja meg az **iOS** értéket.

4. A **Profil típusa**beállításnál válassza a **származtatott hitelesítő adatok**lehetőséget.

5. Válassza **az OK** , majd a **Létrehozás**lehetőséget.

6. Válassza ki a **hozzárendeléseket** , és válassza ki, hogy mely csoportok kapják meg a szabályzatot.
 
A felhasználók a származtatott hitelesítőadat-kiállító beállításakor megadott beállításoktól függően megkapják az alkalmazást vagy az e-mailes értesítést. Az értesítés tájékoztatja a felhasználót, hogy elindítsa a Céges portál, hogy a származtatott hitelesítőadat-házirendek feldolgozhatók legyenek.

## <a name="renew-a-derived-credential"></a>Származtatott hitelesítő adat megújítása

A származtatott hitelesítő adatokat nem lehet kiterjeszteni vagy megújítani. Ehelyett a felhasználóknak a hitelesítő adatok kérése munkafolyamatot kell használniuk ahhoz, hogy új származtatott hitelesítő adatokat igényeljenek az eszközük számára.

Ha az **értesítési típushoz**egy vagy több metódust konfigurál, az Intune automatikusan értesíti a felhasználókat, ha az aktuálisan származtatott hitelesítő adat eléri az élettartamának 80%-át. Az értesítés arra utasítja a felhasználókat, hogy továbbítsák a hitelesítő adatok kérésének folyamatát egy új származtatott hitelesítő adat beszerzéséhez. 

Miután egy eszköz új származtatott hitelesítő adatokat kap, a származtatott hitelesítő adatokat használó házirendek az adott eszközre való újratelepítése is megtörténjen. 


## <a name="change-the-derived-credential-issuer"></a>A származtatott hitelesítő adat kiállítójának módosítása

A bérlői szinten módosíthatja a hitelesítő adatok kibocsátóját, bár egyszerre csak egy kiállítót támogat a bérlő. 

A kibocsátó módosítása után a rendszer kéri a felhasználókat, hogy új származtatott hitelesítő adatokat kapjanak az új kiállítótól. Ezt csak akkor kell megtenniük, ha származtatott hitelesítő adatokat használnak a hitelesítéshez.

### <a name="change-the-issuer-for-your-tenant"></a>A bérlő kiállítójának módosítása

> [!IMPORTANT]  
> Ha töröl egy kiállítót, és azonnal újrakonfigurálja ugyanezt a kiállítót, akkor továbbra is frissítenie kell a profilokat és az eszközöket a származtatott hitelesítő adatoknak a kiállítótól való használatára. A kibocsátó törlése előtt kapott származtatott hitelesítő adatok már nem érvényesek. 

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és nyissa meg az **eszköz konfigurációja**  > **származtatott hitelesítő adatokat**.

2. Válassza a **Törlés** lehetőséget az aktuális származtatott hitelesítőadat-kiállító eltávolításához.

3. Konfiguráljon egy új kiállítót. 


### <a name="update-profiles-that-use-derived-credentials"></a>Származtatott hitelesítő adatokat használó profilok frissítése

Miután törölt egy kiállítót, és hozzáad egy újat, szerkessze a származtatott hitelesítő adatokat használó profilokat. Ez a szabály akkor is érvényes, ha az előző kiállítót állítja vissza. A profil szerkesztése egy frissítést indít el, beleértve a profil *leírásának*egyszerű szerkesztését is.

### <a name="update-derived-credentials-on-devices"></a>Származtatott hitelesítő adatok frissítése az eszközökön

Miután töröl egy kiállítót, és hozzáad egy újat, az eszköz felhasználóinak új származtatott hitelesítő adatokat kell igényelnie. Ez a szabály akkor is érvényes, ha hozzáadja ugyanazt a kibocsátót, amelyet eltávolított. Az új származtatott hitelesítő adat igénylésének folyamata megegyezik az új eszköz beléptetéséhez vagy egy meglévő hitelesítő adat megújításához. 

## <a name="next-steps"></a>További lépések

[Eszköz konfigurációs profiljainak létrehozása](../configuration/device-profile-create.md)


 