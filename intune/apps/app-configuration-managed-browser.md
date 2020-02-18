---
title: Vállalati webes elérés kezelése szabályzattal védett böngészővel
titleSuffix: Microsoft Intune
description: Az Intune által hozzárendelt szabályzattal védett böngésző használatával kezelheti a vállalati webböngészést és a webes adatátvitelt.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7c47a829f8f609528f45b30d0dd9bf56d9d8eb9
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414907"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Webes hozzáférés kezelése Microsoft Intune szabályzattal védett böngésző használatával

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune-szabályzattal védett (Microsoft Edge vagy Intune Managed Browser) böngésző használatával gondoskodhat róla, hogy a vállalati webhelyek hozzáférésére mindig megfelelő biztonsági előírások vonatkozzanak.  Az Intune-nal konfigurált védett böngészők kihasználják az alábbi megoldások előnyeit:

- Alkalmazás-védelmi házirendek
- Conditional Access
- Egyszeri bejelentkezés
- Alkalmazás konfigurációs beállításai
- Azure-alkalmazásproxy integrációja

> [!IMPORTANT]
> A Intune Managed Browser megszűnik. Használja a Microsoft Edge-t a védett Intune-böngésző felhasználói felületéhez. 

## <a name="microsoft-edge-support"></a>Microsoft Edge-támogatás

Az iOS/iPadOS és az Android rendszerű eszközökön használhatja a Microsoft Edge vállalati forgatókönyveket. A Microsoft Edge az összes olyan felügyeleti forgatókönyvet támogatja, mint a Intune Managed Browser a végfelhasználói élmény fokozása mellett. Az Intune-szabályzatok által engedélyezett Microsoft Edge Enterprise-funkciók a következők:

- **Kettős identitás** – a felhasználók egy munkahelyi fiókot és egy személyes fiókot is hozzáadhatnak a böngészéshez. A két identitás között teljes elkülönítés áll fenn, amely hasonló az Office 365 és az Outlook architektúrájának és felhasználói felületéhez. Az Intune-rendszergazdák a munkahelyi fiókon belül megadhatják a védett böngészési élmény kívánt szabályzatait. 
- **Intune app Protection-házirend-integráció** – a rendszergazdák mostantól megcélozhatja az alkalmazás-védelmi szabályzatokat a Microsoft Edge számára, beleértve a kivágási, másolási és beillesztési műveleteket, a képernyőfelvételek megakadályozását, valamint annak biztosítását, hogy a felhasználó által kijelölt hivatkozások csak más kezelt alkalmazásokban legyenek
- **Azure alkalmazásproxy-integráció** – a rendszergazdák vezérelhetik az SaaS-alkalmazásokhoz és a webalkalmazásokhoz való hozzáférést, így biztosítva, hogy a böngészőalapú alkalmazások csak a biztonságos Microsoft Edge böngészőben fussanak, legyen szó a vállalati hálózatról vagy az internetről való csatlakozásról. 
- A **felügyelt kedvencek és a Kezdőlap parancsikonjai** – a könnyű hozzáférés érdekében a rendszergazdák megadhatják, hogy az URL-címek megjelenjenek a Kedvencek területen, amikor a végfelhasználók a vállalati környezetben vannak. A rendszergazdák megadhatnak egy Kezdőlap parancsikont, amely az elsődleges hivatkozásként jelenik meg, amikor a vállalati felhasználó új lapot nyit meg, vagy egy új lapot a Microsoft Edge-ben.

A Microsoft Edge-hez készült Microsoft Intune védelmi szabályzatok segítenek a szervezet adatainak és erőforrásainak védelmében. Az Intune-védelemmel ellátott Microsoft Edge biztosítja, hogy a vállalat erőforrásai ne csak a natív módon telepített alkalmazásokon belül legyenek védve, hanem a webböngésző használatával is.

## <a name="getting-started"></a>Első lépések

A Microsoft Edge és az Intune Managed Browser olyan webböngésző-alkalmazások, amelyeket Ön és végfelhasználói nyilvános alkalmazás-áruházakból tölthetnek le a szervezeten belül használatra. 

Az operációs rendszerre vonatkozó követelmények a böngésző szabályzataival kapcsolatban:
- Android 4 és újabb verziók, vagy
- iOS/iPadOS 8,0 és újabb verziók.

Az Android és az iOS/iPadOS korábbi verziói továbbra is használhatják a Managed Browser, de nem fogják tudni telepíteni az alkalmazás új verzióit, és előfordulhat, hogy nem tudnak hozzáférni az összes alkalmazási lehetőséghez. Javasoljuk, hogy frissítse az ilyen eszközök operációs rendszerét egy támogatott verzióra.

>[!NOTE]
>A Managed Browser nem támogatja a Secure Sockets Layer 3-as verziójú (SSLv3) titkosítási protokollját.


## <a name="application-protection-policies-for-protected-browsers"></a>Alkalmazásvédelmi szabályzatok a védelemmel ellátott böngészőkhöz

Mivel a Microsoft Edge és a Managed Browser rendelkeznek Intune SDK-integrációval, így alkalmazásvédelmi szabályzatok is alkalmazhatók rájuk, például a következők:
- Kivágás, másolás és beillesztés műveletek korlátozása.
- Képernyőmentés megakadályozása.
- Annak biztosítása, hogy a vállalati hivatkozásokat csak a felügyelt alkalmazásokon és böngészőkön belül lehessen megnyitni.

További információt a [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md) című témakörben talál.

Ezek a beállítások az alábbiakra alkalmazhatók:

- Az Intune-ban regisztrált eszközök
- Más MDM-termékben regisztrált eszközök
- Nem felügyelt eszközök

>[!NOTE]
>Ha a felhasználók telepítik a Managed Browser alkalmazást az alkalmazásáruházból, és azt nem az Intune felügyeli, akkor az egyszerű webböngészőként használható, amely a Microsoft MyApps webhelyen keresztül támogatja az egyszeri bejelentkezést. A felhasználók közvetlenül a MyApps webhelyére vannak irányítva, ahol megjelenik az összes számukra kiosztott SaaS-alkalmazás.
Ha a Microsoft Edge vagy a Managed Browser böngészőt nem az Intune felügyeli, nem tudják elérni az Intune által kezelt más alkalmazások adatait. 


## <a name="conditional-access-for-protected-browsers"></a>Feltételes hozzáférés védett böngészőkhöz

A Managed Browser már egy feltételes hozzáféréshez jóváhagyott ügyfélalkalmazás. Ez azt jelenti, hogy úgy korlátozhatja a mobilböngészők hozzáférését az Azure AD-hez csatlakozó webalkalmazásokhoz, hogy a felhasználók csak a Managed Browsert használhassák, valamint letilthat minden más nem védett böngészőt, például a Safarit vagy a Chrome-ot. Ez a védelem alkalmazható az Azure-erőforrásokra, például az Exchange Online-ra és a SharePoint Online-ra, a Microsoft 365 felügyeleti központra, valamint a külső felhasználók számára az [Azure ad Application proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)használatával elérhetővé tett helyszíni helyekre is. 

Ha az Azure AD-hez csatlakozó webalkalmazásokat az Intune Managed Browser használatára korlátozza mobilplatformokon, hozzon létre egy feltételes hozzáférési szabályzatot, amelyhez jóváhagyott ügyfélalkalmazások szükségesek. 

> [!TIP]  
> A feltételes hozzáférés az Azure Active Directory (Azure AD) technológiája. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.  

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **feltételes hozzáférés** > **új szabályzat**lehetőséget.
3. Adja hozzá a szabályzat **nevét**. 
4. A **Hozzárendelések** szakaszban válassza a **Feltételek** > **Ügyfélalkalmazások** lehetőséget. Megjelenik az **ügyfélalkalmazások** ablaktábla.
5. A **Konfigurálás** területen kattintson az **Igen** lehetőségre a szabályzat adott ügyfélalkalmazásokra való érvényesítéséhez.
6. Ellenőrizze, hogy a **Browser** van-e kiválasztva ügyfélalkalmazásként.

    ![Azure AD – Managed Browser – Ügyfélalkalmazások kiválasztása](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Ha korlátozni szeretné, hogy mely natív (nem böngészőbeli) alkalmazások férhetnek hozzá ezekhez a felhőalkalmazásokhoz, válassza a **Mobilalkalmazások és asztali ügyfelek** lehetőséget.

7. Kattintson a **kész** > **kész**gombra.
8. A **hozzárendelések** szakaszban válassza a **felhasználók és csoportok** lehetőséget, majd válassza ki azokat a felhasználókat vagy csoportokat, akikkel hozzá szeretné rendelni a szabályzatot. A panel bezárásához kattintson a **kész** gombra.
9. A **hozzárendelések** szakaszban válassza ki a **felhőalapú alkalmazások vagy műveletek** lehetőséget, hogy kiválassza, mely alkalmazásokat kívánja védelemmel ellátni a szabályzattal. A panel bezárásához kattintson a **kész** gombra.
10. A panel hozzáférés- **vezérlések** szakaszában válassza a **támogatás** lehetőséget. 
11. Kattintson a **hozzáférés engedélyezése** elemre, majd kattintson a **jóváhagyott ügyfélalkalmazás megkövetelése**lehetőségre. 
12. Kattintson a **kiválasztás** elemre a **támogatás** ablaktáblán. Ezt a szabályzatot hozzá kell rendelni azokhoz a felhőalkalmazásokhoz, amelyek esetében azt szeretné, hogy csak az Intune Managed Browser alkalmazásból legyenek elérhetők.

    ![Azure AD – Managed Browser feltételes hozzáférési szabályzat](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)



Miután konfigurálta a fenti szabályzatot, a felhasználók csak az Intune Managed Browserrel férhetnek hozzá az Azure AD-hez kapcsolódó, a szabályzat védelme alá tartozó webalkalmazásokhoz. Ha a felhasználók egy nem kezelt böngészőt próbálnak meg használni ehhez, egy értesítés jelenik meg az eszközükön, amely tudatja velük, hogy csak az Intune Managed Browsert használhatják.

A Managed Browser nem támogatja a klasszikus feltételes hozzáférési szabályzatokat. További információért lásd: [Klasszikus szabályzatok áttelepítése az Azure Portalon](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Egyszeri bejelentkezés az Azure AD-hez kapcsolódó webalkalmazásokba a szabályzat által védett böngészőkben

A Microsoft Edge és a Intune Managed Browser iOS/iPadOS és Android rendszereken az Azure AD-hez csatlakozó webalkalmazások (SaaS és helyszíni) számára is kihasználhatják az egyszeri bejelentkezést. Ha a Microsoft Authenticator alkalmazás iOS/iPadOS vagy az Androidon futó Intune Céges portál alkalmazásban található, akkor a szabályzattal védett böngésző felhasználói hozzáférhetnek az Azure AD-hez csatlakozó webalkalmazásokhoz anélkül, hogy újra meg kellene adniuk a hitelesítő adataikat.

Az SSO megköveteli, hogy az eszközt a Microsoft Authenticator alkalmazás regisztrálja az iOS-/iPadOS-vagy az Android-Intune Céges portál. Az Authenticator vagy az Intune Céges portál alkalmazással rendelkező felhasználóknak regisztrálniuk kell az eszközüket, amikor megnyitnak egy Azure AD-hez csatlakozó webalkalmazást egy szabályzat által védett böngészőben, amennyiben az eszközüket még nem regisztrálta egy másik alkalmazás. Miután az eszközt regisztrálták az Intune által kezelt fiókkal, a fiók az Azure AD-hez csatlakozó webalkalmazások esetében SSO-val fog rendelkezni. 

> [!NOTE]
> Az eszközregisztráció egy egyszerű bejelentkezés az Azure AD szolgáltatással. Nem igényel teljes eszközregisztrációt, és nem ad az eszközre vonatkozó további jogosultságokat az informatikai részlegnek.

## <a name="create-a-protected-browser-app-configuration"></a>Egy védett böngésző alkalmazáskonfigurációjának létrehozása

>[!IMPORTANT]
>Az alkalmazáskonfigurációk érvényre jutásához az szükséges, hogy a felhasználó védelemmel ellátott böngészőjét vagy az eszközön lévő alkalmazások egyikét már az [Intune alkalmazásvédelmi szabályzata]( ../app-protection-policy.md) felügyelje.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **alkalmazás-konfigurációs házirendek** >  > **felügyelt alkalmazások** **hozzáadása** lehetőséget.
3. Az **alkalmazás-konfigurációs házirend létrehozása** panel **alapismeretek** lapján adja meg az alkalmazás konfigurációs beállításainak **nevét** és opcionális **leírását** .
4. Válassza **a nyilvános alkalmazás kiválasztása** lehetőséget, és válassza az iOS/iPadOS, az Android vagy a **Managed Browser** és/vagy az **Edge** lehetőséget.
5. Kattintson a **kiválasztás** gombra az **alkalmazás-konfigurációs házirend létrehozása** panelre való visszatéréshez.
6. A **Beállítások** lap megjelenítéséhez kattintson a **tovább** gombra.
7. A **Beállítások** lapon megadhatja a kulcs-érték párokat az alkalmazás konfigurációinak megadásához. A jelen cikk későbbi részeiben további információt talál a definiálható kulcs-érték párokról.
8. Kattintson a **tovább** gombra a **hozzárendelés** lap megjelenítéséhez, majd kattintson a **csoportok kiválasztása** elemre, és/vagy **válassza ki a kizárni kívánt csoportokat**.
9. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez.
10. Az alkalmazás konfigurációs házirendjének áttekintése után kattintson a **Létrehozás** gombra.

Ekkor létrejön az új konfiguráció, és megjelenik az **alkalmazás-konfigurációs házirend** ablaktáblán.


## <a name="assign-the-configuration-settings-you-created"></a>A létrehozott konfigurációs beállítások hozzárendelése

A beállításokat Azure AD-beli felhasználói csoportokhoz lehet hozzárendelni. Ha az illető felhasználó rendelkezik a célzott védett böngésző telepített példányával, akkor az alkalmazás felügyelete a megadott beállításokkal történik.

1. Az Intune Mobile Application Management irányítópult **alkalmazások** paneljén válassza az alkalmazás- **konfigurációs szabályzatok**lehetőséget.
2. A listából válassza ki a hozzárendelni kívánt alkalmazáskonfigurációt.
3. A következő ablaktáblán válassza a **hozzárendelések**lehetőséget.
4. A **hozzárendelések** ablaktáblán válassza ki azt az Azure ad-csoportot, amelyhez hozzá szeretné rendelni az alkalmazás konfigurációját, majd kattintson az **OK gombra**.

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>A Microsoft Edge beállítása védett böngészőként a szervezet számára

Ezzel a beállítással beállíthatja, hogy a felhasználók a Microsoft Edge vagy a Intune Managed Browser legyenek átirányítva, feltéve, hogy mindkét böngészőt az alkalmazás védelmi szabályzata célozza meg. **Az alkalmazás-konfigurációs házirend beállítását olyan Intune által felügyelt alkalmazásoknak kell megcélozni, amelyekről a webhivatkozást nyitják meg.** 

Ha a beállítás értéke "true" (igaz):

- A felhasználók az Intune által felügyelt alkalmazásokra mutató hivatkozásokat nyitnak meg a Microsoft Edge-ben. 
- Ha még nem rendelkezik az alkalmazással, a rendszer kérni fogja a Microsoft Edge letöltését az áruházból, függetlenül attól, hogy a Intune Managed Browser le lettek-e töltve.

Ha a beállítás értéke "false" (hamis):

- Ha a felhasználóknál a Managed Browser és a Microsoft **Edge is le van töltve** , a Managed Browser elindul. 
- Ha a felhasználók vagy **a Managed Browser** **vagy** a Microsoft Edge le van töltve, a böngésző alkalmazás elindul. 
- Ha a felhasználók nem töltik le a böngésző alkalmazást, a rendszer kérni fogja a Managed Browser letöltésére.

A Microsoft Edge-alkalmazások konfigurációjának létrehozásához használja a fenti eljárást. Adja meg a következő kulcs-érték párokat, amikor kiválasztja a konfigurációs **beállításokat** a **konfigurációs** ablaktáblán (9. lépés):

| Kulcs                              |  Érték   |
|----------------------------------|----------|
| **com. microsoft. Intune. useEdge** | **true** |

> [!NOTE]
> A Microsoft Edge és az alkalmazás konfigurációjában megadott társított alkalmazások felügyeletére szolgáló app Protection-házirendben győződjön meg arról, hogy a következő adatvédelmi házirend-beállítások vannak beállítva:
> - Szervezeti adatküldés más alkalmazásokba: **szabályzattal felügyelt alkalmazások**
> - Webes tartalmak átvitelének korlátozása más alkalmazásokkal: **szabályzat által felügyelt böngészők**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Alkalmazásproxy-beállítások konfigurálása a védett böngészőkhöz

A Microsoft Edge és a Intune Managed Browser és az [Azure ad Application proxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) együtt használhatók az iOS-/iPadOS-és Android-eszközök felhasználói számára a következő forgatókönyvek támogatásához:

- Egy felhasználó letölti a Microsoft Outlook alkalmazást és bejelentkezik. Az Intune alkalmazásvédelmi szabályzatai automatikusan érvényre jutnak. Titkosítják az elmentett adatokat, és megakadályozzák, hogy a felhasználó vállalati fájlokat továbbítson az eszközön lévő nem felügyelt alkalmazások vagy helyek felé. Megadható, hogy amikor a felhasználó egy intranetes webhelyre mutató hivatkozásra kattint az Outlookban, akkor a hivatkozás egy másik böngésző helyett a védett böngészőalkalmazásban nyíljon meg. A védett böngésző felismeri, hogy az adott intranetes webhely az Alkalmazásproxyn keresztül megnyílt a felhasználónak. A rendszer automatikusan átirányítja a felhasználót az alkalmazásproxy használatával, hogy a hitelesítés a megfelelő többtényezős hitelesítéssel történjen, és az intranetes hely elérése előtt feltételes hozzáféréssel. Ez a webhely, amely távoli felhasználók számára korábban nem volt megtalálható, most már elérhető, és az Outlook-beli hivatkozás is az elvárható módon működik.
- Egy távoli felhasználó megnyitja a védett böngészőalkalmazást, és a belső URL-cím segítségével megnyit egy intranetes webhelyet. A védett böngésző felismeri, hogy az adott intranetes webhely az Alkalmazásproxyn keresztül megnyílt a felhasználónak. A rendszer automatikusan átirányítja a felhasználót az alkalmazásproxy használatával, hogy a hitelesítés a megfelelő többtényezős hitelesítéssel történjen, és az intranetes hely elérése előtt feltételes hozzáféréssel. Ez a webhely, amely távoli felhasználók számára korábban nem volt megtalálható, most már elérhető.

### <a name="before-you-start"></a>Előkészületek

- Állítsa be a belső alkalmazásokat az Azure AD alkalmazásproxyban.
  - Az Alkalmazásproxy konfigurálásáról és az alkalmazások közzétételéről a [telepítési dokumentációban](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) olvashat. 
  - A [felhasználókat hozzá kell rendelni](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing) ahhoz a vállalati alkalmazáshoz, amelyhez az átirányítás bekövetkezik. Ezt akkor is meg kell tenni, ha az alkalmazás továbbítási módra van beállítva az előhitelesítéshez, és ha a felhasználó-hozzárendelési követelmény ki van kapcsolva az alkalmazásproxy beállításaiban.
- A Managed Browser alkalmazás 1.2.0-s vagy annál újabb verzióját kell használnia.
- A Managed Browser és a Microsoft Edge alkalmazások felhasználói rendelkezzenek az alkalmazáshoz rendelt [Intune alkalmazásvédelmi szabályzattal](app-protection-policy.md).

    > [!NOTE]
    > Az Alkalmazásproxy frissített átirányítási adatainak érvénybe lépése a Managed Browserben és a Microsoft Edge-ben akár 24 órát is igénybe vehet.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>1\. lépés: Automatikus átirányítás engedélyezése az Outlookból egy védett böngészőhöz
Az Outlookot olyan alkalmazásvédelmi szabályzattal kell konfigurálni, amelyben engedélyezett a **Webes tartalom megjelenítésének korlátozása a Managed Browser alkalmazásra** beállítás.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>2\. lépés: a védett böngészőhöz hozzárendelt alkalmazás-konfigurációs szabályzat hozzárendelése
Ez az eljárás az Alkalmazásproxy átirányítás használatára konfigurálja a Managed Browser vagy a Microsoft Edge alkalmazást. 

Nyissa meg az **Edge** fület a házirend konfigurációs beállításai között, és válassza az **Engedélyezés** lehetőséget az alkalmazásproxy-átirányítás értékhez. A beállítás engedélyezése lehetővé teszi a felhasználóknak az Azure alkalmazásproxy használatával közzétett vállalati és helyszíni webalkalmazásokhoz való hozzáférést.

További információt a Managed Browser, a Microsoft Edge és az Azure AD Alkalmazásproxy a helyszíni webalkalmazásokhoz való zökkenőmentes (és védett) hozzáféréséhez szükséges együttes használatáról az Enterprise Mobility + Security blog [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Együtt jobb: Az Intune és az Azure Active Directory együtt teszi jobbá a felhasználói hozzáférést) című blogbejegyzésében találhat.

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>Védett böngésző kezdőlapjának beállítása

Ezzel a beállítással adható meg a kezdőlap, amelyet a felhasználók egy védett böngésző elindításakor vagy egy új lap létrehozásakor látnak. 
- Ezzel a beállítással megjeleníti a weblapot a Managed Browserben.  A Microsoft Edge ehelyett a kezdőlapra mutató parancsikont jelenít meg.
- A kezdőlap parancsikonja a keresési vezérlőelem alatt ikonként jelenik meg.  Nem lehet szerkeszteni vagy törölni.
- A kezdőlap parancsikonja megjeleníti a szervezet nevét a megkülönböztethetőség érdekében.  Mindig az első ikonként fog megjelenni.

A Microsoft Edge vagy a Managed Browser alkalmazás konfigurációjának létrehozására vonatkozó eljárással adja meg az alábbi kulcs-érték párt:

|                                Kulcs                                |                                                           Érték                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Adjon meg egy érvényes URL-címet. A helytelen URL-címek biztonsági intézkedésként le vannak tiltva.<br>Például: `https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>Védett böngésző könyvjelzőinek konfigurálása

Ezzel a beállítással konfigurálhatók a Microsoft Edge vagy a Managed Browser felhasználói számára elérhető könyvjelzők.

- Ezeket a könyvjelzőket a felhasználók nem törölhetik és nem módosíthatják
- Ezek a könyvjelzők a lista tetején jelennek meg. A felhasználók által készített könyvjelzők ezek alá kerülnek.
- Ha engedélyezte az alkalmazásproxy-átirányítást, akkor alkalmazásproxyval rendelkező webalkalmazásokat akár belső, akár külső URL-cím használatával is hozzáadhat.

A Microsoft Edge vagy a Managed Browser alkalmazás konfigurációjának létrehozására vonatkozó eljárással adja meg az alábbi kulcs-érték párt:

|                                Kulcs                                 |                                                                                                                                                                                                                                                         Érték                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | Ennek a konfigurációnak egy könyvjelzőlista az értéke. Minden könyvjelző egy címből és egy URL-címből áll. A címet és az URL-címet a <strong>&#124;</strong> karakter választja el.<br><br>Például:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>Több könyvjelző megadásakor az egyes párokat a <strong>&#124;&#124;</strong> karakter választja el.<br><br>Például:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>Engedélyezett és letiltott URL-címek meghatározása egy védett böngésző számára

A Microsoft Edge vagy a Managed Browser alkalmazás konfigurációjának létrehozására vonatkozó eljárással adja meg az alábbi kulcs-érték párt:

|Kulcs|Érték|
|-|-|
|A következő lehetőségek közül választhat:<br><ul><li>Engedélyezett URL-címek megadása (csak ezek az URL-címek engedélyezettek, más webhelyek nem érhetők el):<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Tiltott URL-címek megadása (minden más webhely elérhető lesz):<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|A kulcs megfelelő értéke egy URL-címlista. Az engedélyezni vagy letiltani kívánt URL-címeket egyetlen értékként kell megadni, az egyes tételeket függőleges vonal **&#124;** karakterrel elválasztva egymástól.<br><br>Például:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>Mindkét kulcsot ne adja meg. Ha ugyanahhoz a felhasználóhoz mindkét kulcs meg van adva, akkor az engedélyezett kulcs érvényesül, mert az jelent nagyobb korlátozást.
>Ügyeljen továbbá arra, hogy ne tiltson le fontos webhelyeket, például a céges webhelyet.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Az engedélyezett és a blokkolt URL-címek URL-formátuma
Az alábbi táblázat azokat az engedélyezett formátumokat és helyettesítő karaktereket ismerteti, amelyek az URL-címek engedélyezési és blokklistákban való megadásakor használhatók:

- A csillag ( **&#42;** ) helyettesítő karakter és szimbólum a megengedett minták alábbi listájának szabályai szerint használható:

- Az URL-címek listába történő bevitelekor ellenőrizze, hogy az URL-címet a **http** vagy a **https** előtaggal adta-e meg.

- A címben portszámokat is megadhat. Ha nem ad meg portszámot, a rendszer a következő értékeket használja:

  - HTTP – 80-as port

  - HTTPS – 443-as port

  A portszám helyettesítő karakterrel való megadása nem támogatott. Például a `http://www.contoso.com:;` és a `http://www.contoso.com: /;` nem támogatottak.

- Az alábbi táblázat az URL-címek megadásakor használható mintákat ismerteti:

|                  URL-cím                  |                     Részletek                      |                                                Egyezik                                                |                                Nem egyezik                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              Egyetlen lapnak felel meg               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              Egyetlen lapnak felel meg               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | Az összes `www.contoso.com` karakterlánccal kezdődő URL-cím |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     A contoso.com összes altartománya     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             Egyetlen mappa              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  Egyetlen lap, amely portszámot használ   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          Egyetlen biztonságos lap           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    Egyetlen mappa és annak összes almappája    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- Az alábbi példák nem engedélyezett beviteleket szemléltetnek:

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - IP-címek

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>A munkahelyi és a személyes fiókok közötti rugalmas áttérés

A Microsoft Edge Mobile Enterprise felhasználói felületének sarokköve a kettős identitású modell, ami azt jelenti, hogy a Microsoft Edge a munkahelyi és a személyes identitást is támogatja. Csakúgy, mint az Office 365 és az Outlook alkalmazásokban, ez a kettős identitású modell lehetővé teszi a végfelhasználók számára, hogy a Microsoft Edge-t használják az összes böngészési igényhez, és a rendszergazda által meghatározott tartalmi szabályzatok alapján könnyedén mozoghatnak a két élmény között. A személyes kontextusban való böngészés nem érinti a vállalati adatokat, és a munkahelyi környezet teljes mértékben a Microsoft Edge-en belül marad. 

A modell egyik előnye, hogy amikor a felhasználók megpróbálnak megnyitni egy hivatkozást (például egy újságcikket stb.) egy olyan webhelyre, amelyet a szervezet nem engedélyez, azt a személyes kontextusban tehetik meg, amely teljesen el lesz különítve a munkahelyi környezettől. A rendszer alapértelmezés szerint engedélyezi ezeket a lágy átmeneteket. 

A Microsoft Edge vagy a Managed Browser alkalmazás konfigurációjának létrehozására vonatkozó eljárással adja meg az alábbi kulcs-érték párt:

| Kulcs                                                                | Érték                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com. microsoft. Intune. Mam. managedbrowser. AllowTransitionOnBlock** | **Hamis** blokkok esetén ezek a gyenge átmenetek |

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>A felügyelt alkalmazások naplóinak elérése a Managed Browser használatával iOS rendszeren

Az iOS-/iPadOS-eszközön telepített felügyelt böngészővel rendelkező végfelhasználók megtekinthetik az összes Microsoft által közzétett alkalmazás felügyeleti állapotát. Küldhetnek naplókat a felügyelt iOS/iPadOS-alkalmazásokkal kapcsolatos hibák elhárításához.

1. Nyissa meg az iOS/iPadOS **beállításait**.
2. Válassza ki a **Managed Browser** alkalmazás beállításait.
3. Az **Intune-diagnosztika engedélyezése** kapcsolóval állítsa át a böngészőt hibaelhárítási módba.
4. Nyissa meg a **Managed Browsert**. Kattintson az **Intune-alkalmazás állapotának megtekintése** lehetőségre az egyéni alkalmazásszabályzat-beállítások áttekintéséhez.
5. Az **Első lépések**, majd a **Naplók megosztása** vagy a **Naplók küldése a Microsoftnak** lehetőséget választva küldje el a hibaelhárítási naplófájlokat a rendszergazdának vagy a Microsoftnak.

A böngésző az alkalmazásban is megnyitható hibaelhárítási módban.

1. Nyissa meg a Managed Browsert.
2. A címsorba gépelje be a következőt: `about:intunehelp`
A böngésző hibaelhárítási módban indul el.

Az alkalmazásnaplókban tárolt beállítások listáját az [Alkalmazásvédelmi naplók áttekintése a Managed Browserben](app-protection-policy-settings-log.md) című témakörben találja.

## <a name="security-and-privacy-for-the-managed-browser"></a>Biztonság és adatvédelem a Managed Browser használatánál

- A Managed Browser nem használja a felhasználók eszközein futó beépített böngésző egyedi beállításait. Ezekhez a beállításokhoz a Managed Browser nem fér hozzá.

- Ha engedélyezi az **Egyszerű PIN-kód megkövetelése a hozzáféréshez** vagy a **Vállalati hitelesítő adatok megkövetelése a hozzáféréshez** beállítást a Managed Browser böngészőhöz hozzárendelt alkalmazásvédelmi szabályzatban, és a felhasználó a hitelesítési lapon a súgóhivatkozásra kattint, bármely internetes webhelyet elérhet, függetlenül attól, hogy azok hozzá lettek-e adva a felügyeltböngésző-szabályzat blokklistájához.

- A Managed Browser csak akkor képes blokkolni a hozzáférést a webhelyekhez, ha azokat közvetlenül érik el. Nem blokkolja a hozzáférést, ha a felhasználó köztes szolgáltatások (például egy fordítási szolgáltatás) használatával éri el a webhelyet.

- A hitelesítés lehetővé tétele és az Intune-dokumentáció elérése érdekében a **&#42;.microsoft.com** mentesül az engedélyezési és blokkolási beállítások alól, és És mindig engedélyezve van.

### <a name="turn-off-usage-data"></a>A használatra vonatkozó adatok kikapcsolása
A Microsoft termék- és szolgáltatásfejlesztési célból automatikus módszerekkel név nélküli adatokat gyűjt a Managed Browser teljesítményéről és használatáról. A felhasználók kikapcsolhatják az adatgyűjtést az eszköz **Használati adatok** beállításával. Nem tudja befolyásolni ezen adatok gyűjtését.

- IOS/iPadOS-eszközökön a felhasználók által meglátogatott, lejárt vagy nem megbízható tanúsítvánnyal rendelkező webhelyek nem nyithatók meg.

## <a name="next-steps"></a>További lépések

- [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md) 
