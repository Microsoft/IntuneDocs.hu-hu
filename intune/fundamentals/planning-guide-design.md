---
title: Microsoft Intune terv létrehozása
titleSuffix: Microsoft Intune
description: Ez a cikk segít tervet kidolgozni a kizárólag felhőalapú Microsoft Intune-környezet megtervezéséhez és implementációjához.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 24f15cb179dfc2b12b642f5f196d04dce58d4377
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505204"
---
# <a name="create-a-design"></a>Terv létrehozása

Az Intune-terv [az útmutató más szakaszainak](../planning-guide.md) követése közben gyűjtött adatokon és meghozott döntéseken alapul. Az alábbiak összefogásában nyújt segítséget:

- Aktuális környezet

- Intune-telepítési lehetőségek

- Külső függőségek identitáskövetelményei

- Eszközplatformmal kapcsolatos szempontok

- Teljesítendő követelmények  

Bár a helyszíni infrastruktúrával kapcsolatban csak minimális mennyiségű követelményt támasztunk, egy terv készítése mégis segíthet abban, hogy biztosan a saját céljainak és követelményeinek megfelelő mobileszköz-felügyeleti megoldás legyen a végeredmény.

Vizsgáljuk meg ezeket a területeket részletesebben. 

## <a name="record-your-current-environment"></a>A jelenlegi környezet dokumentálása
Ezenfelül gyakorta előfordul, hogy az implementálási vagy a tesztelési fázisban módosítani kell a terven. A terv használatával azonnal dokumentálhatja ezeket a változásokat az indokaikkal együtt.

A környezet ugyanis befolyásolhatja a tervezési döntéseket, ezért azt dokumentálni kell, és figyelembe kell venni a többi Intune-tervezési döntés meghozatalakor. Alább néhány, az aktuális környezet dokumentálásával kapcsolatos példát olvashat:

- **Felhőbeli identitás**

  - Használják-e a DirSync vagy az Azure Active Directory (Azure AD) Connect szoftvert?

  - Összevont-e a környezet?

  - Engedélyezve van-e a többtényezős hitelesítés (MFA)?

- **E-mail-környezet**

  - Használnak Exchange-et? Helyszíni vagy felhőbeli megoldásban?

  - Folyamatban van-e az Exchange felhőbe való migrálása?

- **Az aktuális mobileszköz-felügyeleti (MDM) megoldás**

  - Használnak-e jelenleg más MDM-megoldásokat?

  - Milyen MDM-megoldást használnak a vállalati, illetve a személyes tulajdonú eszközök esetében?

  - Milyen képességeket használnak (például alkalmazások eszközbeállításai, Wi-Fi konfigurációk)?

  - Milyen eszközplatformokat támogatnak?

  - Hány felhasználó használja az MDM-megoldást, és milyen csoportokra vannak tagolva?

- **Tanúsítványmegoldás**

  - Van-e használatban tanúsítványmegoldás?

  - Milyen típusú tanúsítványokat használnak?

- **Rendszerfelügyelet**

  - Hogyan felügyelik a PC-s és a kiszolgálói környezetet?

  - Használják-e a System Center Configuration Managert? Használnak-e külső gyártótól származó rendszerfelügyeleti platformot?

- **VPN-megoldás**

  - Milyen VPN-megoldást használnak?

  - Használják-e a vállalati, illetve a személyes tulajdonú eszközök esetében is?

Az aktuális MDM-környezet dokumentálásakor mindenképpen jegyezze fel azokat a projekteket és más érvényben lévő terveket, amelyek hatással lehetnek a környezetre. Alább egy példával szemléltetjük, hogyan lehet dokumentálni az aktuális környezetet az Intune-terv elkészítéséhez:

| **Megoldásterület** | **Aktuális környezet** | **Megjegyzések** |
|---|---|---|
| **Identitás** | Azure AD, Azure AD Connect, nem összevont, nincs MFA | Folyamatban lévő projekt: MFA megvalósítása az év végéig |                 
| **E-mail-környezet** | Helyszíni Exchange, online Exchange | Folyamatban van a migrálás a helyszíni Exchange-ről az online-ra. A postafiókok 75%-át már migráltuk, és a maradék 25% migrálása is lezajlik az Intune-próbaüzem megkezdése előtt. |                
| **SharePoint** | Helyszíni SharePoint | Nem tervezzük a SharePoint felhőbe költöztetését |  
| **Aktuális MDM** | Exchange ActiveSync |  |
| **Tanúsítványmegoldás** | Microsoft Server 2012 R2, AD tanúsítványszolgáltatások | Csak nyilvános kulcsú infrastruktúrát használunk a webhelykiszolgálókhoz |
| **Rendszerfelügyelet** | System Center Configuration Manager CB 1606 | Meg szeretnénk vizsgálni a hibrid Intune-megoldás lehetőségét |
| **VPN-megoldás** | Cisco AnyConnect |  |


A saját Intune-tervének kidolgozásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

## <a name="choose-an-intune-deployment-option"></a>Intune-telepítési lehetőség választása

Az Intune kétféle telepítési lehetőséget kínál, ezek az önálló és a hibrid. Önálló a felhőben futó Intune szolgáltatásra hivatkozik, amely az Intune és a System Center Configuration Manager közötti integrációra utal. Ez az útmutató elsősorban az önálló telepítésről szól. [Döntse el, melyik lehetőség felel meg az üzleti követelményeknek](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

> [!Important]
>Az új hibrid MDM-ügyfelek bevezetése elavult. További információ: [áttérés hibrid mobileszköz-kezelésről az Intune-ra az Azure-](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) blogbejegyzésben.


## <a name="intune-tenant-location"></a>Az Intune-bérlő földrajzi helye

A globálisan jelen lévő vállalatoknak a szolgáltatásra való előfizetéskor célszerű megtervezniük, hogy hol tartják a bérlőjüket. Az ország/régió akkor van meghatározva, ha első alkalommal regisztrál egy Intune-előfizetésre, és a világ országaihoz/régióihoz rendel hozzá, amelyek alább láthatók:

- Észak-Amerika

- Európa, Közel-Kelet és Afrika

- Ázsia és a Csendes-óceáni térség

>[!IMPORTANT]
> Később nem lehet módosítani az országot/régiót és a bérlő helyét.

## <a name="external-dependencies"></a>Külső függőségek

A külső függőségek olyan szolgáltatások és termékek, amelyek ugyan nem részei az Intune-nak, de vagy követelményei, vagy integrálódhatnak vele. Fontos feltérképezni az esetleges külső függőségekkel kapcsolatos követelményeket és azok konfigurációs sajátságait is. Néhány példa a gyakoribb külső függőségekre:

- Identitás

- Felhasználói és eszközcsoportok

- Nyilvános kulcsú infrastruktúra (PKI)

A következőkben részletesebben ismertetjük ezeket a gyakori külső függőségeket.

### <a name="identity"></a>Identitás

A szervezethez tartozó, eszközt regisztráló felhasználókat az identitásuk révén azonosítjuk. Az Intune-hoz az Azure Active Directoryt (Azure AD) kell használni identitásszolgáltatóként. Ha már ezt a szolgáltatást használják, akkor használhatják a felhőben már meglévő identitásokat. A helyszíni felhasználói identitások és a Microsoft felhőszolgáltatásai közötti szinkronizálást pedig az Azure AD Connect eszközzel ajánlott elvégezni. Ha a szervezet már használja az Office 365-öt, akkor fontos, hogy az Intune is ugyanazt az Azure AD-környezetet használja.

További tudnivalók az Intune-identitással kapcsolatos alábbi követelményekről:

- [Identitáskövetelmények](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions).

- [A címtár-szinkronizálás követelményei](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

- [A többtényezős hitelesítés követelményei](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

### <a name="user-and-device-groups"></a>Felhasználói és eszközcsoportok

A felhasználói és eszközcsoportok határozzák meg a telepített környezet célterületét, beleértve a szabályzatokat, az alkalmazásokat és a profilokat. Önnek kell eldöntenie, hogy milyen felhasználói és eszközcsoportokra lesz szükség.

A helyszíni Active Directoryban célszerű létrehoznia az összes csoportot, majd szinkronizálnia azokat az Azure Active Directoryba. További tudnivalók a felhasználói és eszközcsoportok megtervezéséről és létrehozásáról:

- [A felhasználói és eszközcsoportok megtervezése](users-add.md).

- [A felhasználói és eszközcsoportok létrehozása](groups-add.md).

### <a name="public-key-infrastructure-pki"></a>Nyilvános kulcsú infrastruktúra (PKI)
A nyilvános kulcsú infrastruktúra tanúsítványokat szolgáltat, amelyekkel az eszközök vagy a felhasználók biztonságosan hitelesíthetik magukat egy szolgáltatásban. Az Intune a Microsoft PKI-infrastruktúráit támogatja. A mobileszközökhöz a tanúsítványalapú hitelesítés követelményeinek való megfelelés érdekében felhasználói és eszköztanúsítványokat is ki lehet állítani. A tanúsítványok használata előtt meg kell állapítani, hogy szüksége van-e tanúsítványokra, a hálózati infrastruktúra támogatja-e a tanúsítványalapú hitelesítést, és hogy a jelenlegi környezetben használnak-e tanúsítványokat.

Ha az Intune VPN-, Wi-Fi- vagy e-mail-profiljaihoz tanúsítványokat tervez használni, bizonyosodjon meg róla, hogy a szervezetnél [már ki van alakítva egy támogatott PKI-infrastruktúra](../protect/certificates-configure.md), amely készen áll a tanúsítványprofilok létrehozására és üzembe helyezésére.

Továbbá, ha SCEP-profilokat fog használni, meg kell határoznia, hogy melyik kiszolgáló fogja üzemeltetni a hálózati eszközök tanúsítványigénylési szolgáltatását (NDES), és hogy a kommunikáció hogyan fog történni.

További információk az alábbiakról:

- [Intune-tanúsítványprofilok konfigurálása](../protect/certificates-configure.md)

- [SCEP-tanúsítványinfrastruktúra konfigurálása](../protect/certificates-scep-configure.md)

- [PFX-tanúsítványinfrastruktúra konfigurálása](../protect/certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>Eszközplatformmal kapcsolatos szempontok

Csak az eszközökkel kapcsolatos alábbi szempontok alaposabb ismeretében lehet jól megérteni a helyes konfigurálásuk mikéntjét.

- Támogatott eszközplatformok

- Eszközök

- Az eszközök tulajdonjoga

- Tömeges regisztrálás

Vizsgáljuk meg ezeket a területeket részletesebben.

### <a name="determine-supported-device-platforms"></a>A támogatott eszközplatformok meghatározása

A terv kidolgozásakor tudnia kell, hogy milyen eszközök lesznek a környezetben, és ellenőrizni kell, hogy ezeket az Intune támogatja-e. Az Intune az iOS, az Android és a Windows platformot támogatja.

[A Intune által támogatott eszközök teljes listája](supported-devices-browsers.md).

### <a name="devices"></a>Eszközök

Az Intune a mobileszközök felügyelete révén védi a vállalati adatokat és teszi lehetővé, hogy a végfelhasználók több helyszínen is dolgozhassanak. Az Intune több eszközplatformot is támogat, ezért javasolt a szervezet tervében dokumentálnia a támogatni tervezett eszközöket, OS-platformokat és verziókat. Példa:

| **Eszközplatform** | **Operációsrendszer-verziók** |
|:---:|:---:|
| iOS – iPhone | 10.0+ |                
| iOS – iPad | 10.0+ |               
| Android – Samsung Knox Standard | 4.0+ |
| Windows 10-es táblagépek | 10+ |


A saját eszközlistájának kidolgozásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
### <a name="device-ownership"></a>Az eszközök tulajdonjoga

Az Intune támogatja a vállalati, illetve a személyes tulajdonban lévő eszközöket is. Azok az eszközök minősülnek vállalati tulajdonúaknak, amelyeket egy eszközregisztráció-kezelő vagy egy készülékregisztrációs program regisztrál. Ilyen lehet például egy, az Apple Készülékregisztrációs programmal regisztrált eszköz, amelyet vállalati tulajdonúként jelölnek meg, és egy olyan eszközcsoportba helyezik, amely célzott vállalati szabályzatokat és alkalmazásokat kap.

A vállalati és a személyes tulajdonban lévő eszközökkel kapcsolatos használati esetekről a [3. szakasz: Használatieset-forgatókönyvek követelményeinek meghatározása](planning-guide-requirements.md) nyújt további tájékoztatást.

### <a name="bulk-enrollment"></a>Tömeges regisztrálás

 Az eszközök tömeges regisztrálását a platformtól függően többféleképpen valósíthatja meg. Ha tömeges regisztrálásra lesz szüksége, akkor [döntsön annak módjáról](../enrollment/device-enrollment.md), és a tervet ennek megfelelően dolgozza ki.

## <a name="feature-requirements"></a>Funkciókövetelmények

Ezekben a szakaszokban a következő, a használatieset-forgatókönyvek követelményeihez kapcsolódó funkciókat és képességeket vizsgáljuk meg:

- Használati feltételekkel kapcsolatos szabályzatok

- Konfigurációs szabályzatok

- Erőforrás-profilok

- Apps

- Megfelelőségi szabályzat

- Conditional Access

Vizsgáljuk meg ezeket a területeket részletesebben.

### <a name="terms-and-conditions-policies"></a>Használati feltételekkel kapcsolatos szabályzatok

A [használati feltételekben](../enrollment/terms-and-conditions-create.md) lehet feltüntetni azokat a szabályzatokat vagy kikötéseket, amelyeket a végfelhasználónak el kell fogadnia az eszköze regisztrálása előtt. Az Intune-ban több használati feltételekkel kapcsolatos szabályzatot is fel lehet venni és üzembe lehet helyezni a felhasználói csoportok számára.

Önnek kell eldöntenie, hogy van-e szükség használati feltételekkel kapcsolatos szabályzatokra, illetve ha igen, akkor a szervezetben kinek a feladata ezeket kidolgozni. Alább láthat egy példát a használati feltételekkel kapcsolatos szabályzatok dokumentálására.

| **Feltételek és kikötések neve** | **Használati eset** | **Célcsoport** |
|:---:|:---:|:---:|
| Vállalati feltételek | Vállalati | Vállalati felhasználók |                 
| BYOD-feltételek | BYOD | BYOD-felhasználók |                


A saját felhasználói csoportjai számára feltüntetni kívánt használati feltételek feltérképezéséhez [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

### <a name="configuration-policies"></a>Konfigurációs szabályzatok

A konfigurációs szabályzatok az eszközök biztonsági beállításainak és szolgáltatásainak kezelésére használhatók. A konfigurációs szabályzatok megtervezésekor a használati esetek követelményeit taglaló szakasz alapján határozza meg az Intune-eszközökhöz szükséges konfigurációkat. Dokumentálja a beállításokat, és hogy hogyan kell azokat konfigurálni. Azt is dokumentálja, hogy ezek mely felhasználói vagy eszközcsoportokra vonatkoznak.

Platformonként legalább egy konfigurációs szabályzatot célszerű létrehozni. Szükség esetén platformonként több konfigurációs szabályzatot is létrehozhat. Az alábbi példában négy különféle konfigurációs szabályzat látható, különböző platformokhoz és használatieset-forgatókönyvekhez.

| **Szabályzat neve** | **Eszközplatform** | **Beállítások** | **Célcsoport** |   
|:---:|:---:|:---:|:---:|
| Vállalati – iOS | iOS | PIN-kód szükséges, Hossz: 6, Felhőbeli biztonsági mentés korlátozása | Vállalati eszközök |                                                           
| Vállalati – Android | Android: | PIN-kód szükséges, Hossz: 6, Felhőbeli biztonsági mentés korlátozása | Vállalati eszközök |                                                           
| BYOD – iOS  | iOS | PIN-kód szükséges. Hossz: 4 | BYOD-eszközök |
| BYOD – Android  | Android: | PIN-kód szükséges. Hossz: 4 | BYOD-eszközök |


A saját konfigurációs szabályzatainak meghatározásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

### <a name="profiles"></a>Profilok

A végfelhasználók profilok segítségével kapcsolódnak a vállalati adatokhoz. Az Intune számos profiltípust támogat. A profilok konfigurálásával kapcsolatos döntéseket a használati esetek és követelményeik alapján hozza meg. Az eszközprofilok platformtípusok szerint vannak kategóriákba sorolva, és célszerű belefoglalni őket a tervdokumentációba.

- Tanúsítványprofilok

- Wi-Fi profil

- VPN-profil

- E-mail profil

Vizsgáljuk meg ezeket a profiltípusokat részletesebben.

#### <a name="certificate-profiles"></a>Tanúsítványprofilok

Az Intune a tanúsítványprofilok alapján bocsát ki tanúsítványokat a felhasználók és eszközök számára. Az Intune a következő típusokat támogatja:

- SCEP protokoll

- Megbízható főtanúsítvány

- PFX-tanúsítvány

Ajánlott dokumentálnia, hogy mely felhasználói csoportoknak van szüksége tanúsítványra, hány tanúsítványprofilra lesz szükség, és mely felhasználói csoportokhoz kell őket telepíteni.

>[!NOTE]
> Ne feledje, hogy a SCEP tanúsítvány-profilhoz a megbízható főtanúsítvány szükséges, ezért győződjön meg arról, hogy az SCEP-tanúsítvány profiljának összes felhasználója megbízható főtanúsítványt is kap. Ha SCEP-tanúsítványokra van szüksége, tervezze meg és dokumentálja a szükséges SCEP-tanúsítványsablonokat.

Az alábbi példa szemlélteti, hogyan lehet dokumentálni a tanúsítványokat a tervezés folyamán:

| **Típus** | **Profilnév** | **Eszközplatform** | **Használati esetek** |   
|:---:|:---:|:---:|:---:|
| Legfelső szintű hitelesítésszolgáltató | Vállalati legfelső szintű hitelesítésszolgáltató | Android, iOS, Windows Mobile | Vállalati, BYOD  |                                                           
| SCEP | Felhasználói tanúsítvány | Android, iOS, Windows Mobile | Vállalati, BYOD |                                                           


A saját tanúsítványprofiljainak meghatározásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

#### <a name="wi-fi-profile"></a>Wi-Fi profil

A Wi-Fi-profilok révén a mobileszközök automatikusan csatlakozhatnak a vezeték nélküli hálózatokhoz. Az Intune-ban az összes támogatott platformhoz lehet Wi-Fi-profilt üzembe helyezni. További tudnivalók [az Intune Wi-Fi-profiltámogatásáról.](../configuration/wi-fi-settings-configure.md)

Az alábbi példa a Wi-Fi-profilok tervezését szemlélteti:

| **típusú** | **profilnév** | **eszköz platform** | **használati esetek** | | Wi-Fi | Ázsia Wi-Fi profilja | Android | Vállalat, BYOD Asia-régió | | Wi-Fi | Wi-Fi profil Észak-Amerika | Android, iOS, Windows 10 Mobile | Vállalat, BYOD Észak-Amerika régió |

A saját Wi-Fi-profiljainak meghatározásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

#### <a name="vpn-profile"></a>VPN-profil

A VPN-profilok révén a felhasználók biztonságosan érhetik el a vállalati hálózatot távolról. Az Intune egyaránt támogatja a natív mobil VPN-kapcsolatokon alapuló és a külső gyártók által készített VPN-profilokat. További tudnivalók [a VPN-profilokról és az Intune által támogatott gyártókról](../configuration/vpn-settings-configure.md).

Az alábbi példában egy VPN-profil dokumentálását szemléltetjük.

| **Típus** | **Profilnév** | **Eszközplatform** | **Használati esetek** |
|:---:|:---:|:---:|:---:|
| VPN | VPN, Cisco, bármilyen csatlakozási profil | Android, iOS, Windows 10 Mobile | Vállalati, BYOD, Észak-Amerika és Németország|
| VPN | Pulse Secure | Android: | Vállalati, BYOD, ázsiai régió |

A saját VPN-profiljainak meghatározásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).

#### <a name="email-profile"></a>E-mail profil

Az e-mail-profilokkal automatikusan be lehet állítani a levelezőprogramokban a kapcsolati adatokat és az e-mail-konfigurációt. Az Intune csak bizonyos eszközökön támogatja az e-mail-profilokat. További tudnivalók az [e-mail-profilokról és a támogatott platformokról](../configuration/email-settings-configure.md).

Az alábbi példában az e-mail-profilok dokumentálását szemléltetjük:

| **Típus** | **Profilnév** | **Eszközplatform** | **Használati esetek** |
|:---:|:---:|:---:|:---:|
| E-mail profil | iOS-es e-mail-profil | iOS | Vállalati – Infómunkás BYOD |
| E-mail profil | Android Knox e-mail-profil | Android Knox | BYOD |

A saját e-mail-profiljainak meghatározásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
### <a name="apps"></a>Apps

Az Intune-nal többféleképpen is eljuttathat alkalmazásokat a felhasználókhoz vagy az eszközökre. Az alkalmazás többek között szoftvertelepítő, nyilvános alkalmazás-áruházból származó vagy külső hivatkozással elérhető alkalmazás, illetve felügyelt iOS-alkalmazás lehet. Az egyesével történő alkalmazástelepítésen felül a mennyiségi licencelésű alkalmazásokat az iOS és a Windows mennyiségi licencelési programjai keretében is felügyelheti és telepítheti. További információk az alábbiakról:

- [Az eljuttatható alkalmazások típusai](../apps/app-management.md)

- [iOS Volume Purchase Program for Business (VPP)](../apps/vpp-apps-ios.md)

- [Vállalati Microsoft Áruházbeli alkalmazások](../apps/windows-store-for-business.md)

#### <a name="app-type-requirements"></a>Alkalmazástípusok követelményei

Mivel az alkalmazásokat felhasználók és eszközök számára is lehet telepíteni, célszerű eldöntenie, hogy mely alkalmazásokat felügyelje az Intune. A lista összeállításakor igyekezzen megválaszolni a következő kérdéseket:

- Igényelnek-e az alkalmazások integrációt a felhőszolgáltatásokkal?

- Minden alkalmazás elérhető lesz a BYOD-felhasználók számára?

- Milyen telepítési lehetőségek állnak rendelkezésre az alkalmazásokhoz?

- Kell-e a vállalatnak szolgáltatottszoftver-adatokhoz hozzáférést biztosítania a partnerek számára?

- Igényelnek-e az alkalmazások internet-hozzáférést a felhasználói eszközökön?

- Elérhetők-e az alkalmazások nyilvánosan valamilyen alkalmazás-áruházban, vagy egyedi üzletági (LOB-) alkalmazások?


#### <a name="app-protection-policies"></a>Alkalmazásvédelmi szabályzatok

Az alkalmazásvédelmi szabályzatok azt definiálják, hogyan kezelheti egy alkalmazás a vállalati adatokat, így minimalizálják az adatvesztést. Az Intune minden mobilalkalmazás-felügyelettel kompatibilis alkalmazás esetén támogatja az alkalmazásvédelmi szabályzatok használatát. Az alkalmazásvédelmi szabályzat kialakításakor meg kell határoznia, hogy az adott alkalmazásban hogyan szeretné korlátozni a vállalati adatok elérését. Célszerű megismerkednie az [alkalmazásvédelmi szabályzatok](../apps/app-protection-policy.md) működésével. Az alábbi példával a meglévő alkalmazások és a szükséges védelem dokumentálását mutatjuk be.

| **Alkalmazás** | **Rendeltetés** | **Platformok** | **Használati eset** | **Alkalmazásvédelmi szabályzat** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Elérhető | iOS | Vállalati – Vezetők | Nem lehet jailbreakelni, fájlok titkosítása |                                                         
| Word | Elérhető | iOS, Android – Samsung Knox, nem Knox, Windows 10 Mobile | Vállalati, BYOD | Nem lehet jailbreakelni, fájlok titkosítása |                                                         


A saját alkalmazásvédelmi szabályzatainak meghatározásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
#### <a name="compliance-policies"></a>Megfelelőségi szabályzatok

A megfelelőségi szabályzatok határozzák meg, hogy egy adott eszköz megfelel-e bizonyos követelményeknek. Az Intune megfelelőségi szabályzatokkal határozza meg, hogy az eszközök megfelelőnek minősülnek-e, vagy sem. Ezt követően a megfelelőségi állapot alapján lehet korlátozni vagy engedélyezni a vállalati erőforrások elérését. Ha feltételes hozzáférésre van szükség, javasoljuk, hogy tervezzen egy [eszköz megfelelőségi szabályzatát](../protect/device-compliance-get-started.md).

A követelmények és a használati esetek alapján döntse el, hogy hány eszközmegfelelőségi szabályzatra van szüksége, és hogy ezek mely felhasználói csoportokra fognak vonatkozni. Ezenkívül azt is el kell döntenie, hogy mennyi ideig lehet egy eszköz offline állapotban, mielőtt nem megfelelőnek minősülne.

Az alábbi példa egy megfelelőségi szabályzat tervezését szemlélteti:

| **Szabályzat neve** | **Eszközplatform** | **Beállítások** | **Célcsoport** |
|:---:|:---:|:---:|:---:|
| Megfelelőségi szabályzat | iOS, Android – Samsung Knox, nem Knox, Windows 10 Mobile | PIN-kód szükséges, nem lehet jailbreakelni | Vállalati, BYOD |


A saját megfelelőségi szabályzatainak meghatározásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0).
#### <a name="conditional-access-policies"></a>Feltételes hozzáférési szabályzatok

A feltételes hozzáférés lehetővé teszi, hogy csak a megfelelő eszközök férhessenek hozzá az e-mailekhez és más vállalati erőforrásokhoz. Az Intune a Enterprise Mobility + Security (EMS) csomaggal együttműködve szabályozza a vállalati erőforrások elérését. Döntse el, hogy feltételes hozzáférést igényel-e, és hogy mit kell védeni. További tudnivalók [a feltételes hozzáférésről](../protect/conditional-access.md)

Online hozzáférés esetén döntse el, hogy milyen platformokat és felhasználói csoportokat fog megcélozni feltételes hozzáférési szabályzatok alapján. Azt is állapítsa meg, hogy telepítenie vagy konfigurálnia kell-e az Intune-összekötőt a helyszíni Exchange-hez: 

- [Helyszíni Exchange](../protect/exchange-connector-install.md)

Az alábbi példa bemutatja, hogyan dokumentálhatja a feltételes hozzáférési szabályzatokat:

| **Szolgáltatás** | **Modern hitelesítési platformok** | **Egyszerű hitelesítés** | **Használati esetek** |
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS, Android | A nem megfelelő eszközök letiltása az Intune által támogatott platformokon | Vállalati, BYOD |
| SharePoint Online | iOS, Android |  | Vállalati, BYOD |

A feltételes hozzáférési szabályzatok megadásához [letöltheti a fenti táblázat sablonját](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) .

## <a name="next-steps"></a>További lépések

A következő szakasz [az Intune implementálási folyamatához](planning-guide-onboarding.md) nyújt útmutatást.
