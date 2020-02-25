---
title: Az iOS és az Android rendszerhez készült Microsoft Edge felügyelete az Intune-nal
titleSuffix: ''
description: A Microsoft Edge Intune app Protection-szabályzatokkal biztosíthatja, hogy a vállalati webhelyek mindig elérhetők legyenek a szükséges védelemmel.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a3436b9590204691201f8341d1e2f896e9ffff6
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576373"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Webes elérés kezelése a Microsoft Edge és a Microsoft Intune használatával

Az Intune app Protection-szabályzatok használata a Microsoft Edge segítségével biztosítható, hogy a vállalati webhelyek mindig elérhetők legyenek a védelemben. Az Intune-szabályzatok által engedélyezett Microsoft Edge Enterprise-funkciók a következők:

- **Kettős identitás.** A felhasználók egy munkahelyi fiókot és egy személyes fiókot is hozzáadhatnak a böngészéshez. A két identitás között teljes elkülönítés áll fenn, amely hasonló az Office 365 és az Outlook architektúrájának és felhasználói felületéhez. Az Intune-rendszergazdák a munkahelyi fiókon belül megadhatják a kívánt házirendeket a védett böngészési élményhez.
- **Intune app Protection-szabályzat-integráció.** Mivel a Microsoft Edge integrálva van az Intune SDK-val, megcélozhatja az adatvédelmi szabályzatokat az adatvesztés elleni védelemhez. Ezek közé tartozik a Kivágás, másolás és beillesztés szabályozása, a képernyőfelvételek megakadályozása, valamint annak biztosítása, hogy a felhasználó által kijelölt hivatkozások csak más felügyelt alkalmazásokban legyenek nyitva.
- **Azure alkalmazásproxy-integráció.** A szoftveres (SaaS) alkalmazások és a webalkalmazások hozzáférését szabályozhatja. Ezzel biztosíthatja, hogy a böngészőalapú alkalmazások csak a biztonságos Microsoft Edge böngészőben fussanak, legyen szó a végfelhasználók a vállalati hálózatról vagy az internetről való kapcsolatról.
- **Alkalmazás konfigurációja.** Az alkalmazás konfigurációs beállításai segítségével megerősítheti a szervezete biztonsági állapotát, és konfigurálhatja a végfelhasználók számára a könnyű használatú szolgáltatásokat. Meghatározhatja például a könyvjelzőket, a Kezdőlap parancsikonját, az engedélyezett vagy letiltott helyeket, valamint a Azure Active Directory (Azure AD) alkalmazásproxy-t.

A Microsoft Edge-hez készült Microsoft Intune védelmi szabályzatok segítenek a szervezet adatainak és erőforrásainak védelmében. A szabályzatok Microsoft Edge használatával történő használata biztosítja, hogy a vállalat erőforrásai ne csak a natív módon telepített alkalmazásokon belül legyenek védve, hanem a webböngészőn keresztül is elérhetők.

## <a name="getting-started"></a>Első lépések

Ön és a végfelhasználók a Microsoft Edge-t tölthetik le nyilvános alkalmazás-áruházakból a szervezetében való használatra. A böngésző-házirendek operációs rendszerre vonatkozó követelményei a következők lehetnek:
- Android 4 és újabb verziók
- iOS 8.0 és újabb verziók

## <a name="application-protection-policies-for-microsoft-edge"></a>Alkalmazás-védelmi szabályzatok a Microsoft Edge-hez

Mivel a Microsoft Edge integrálva van az Intune SDK-val, alkalmazás-védelmi szabályzatokat is alkalmazhat rájuk.

Ezek a beállítások az alábbiakra alkalmazhatók:
- Az Intune-ban regisztrált eszközök.
- Egy másik mobileszköz-felügyeleti termékkel regisztrált eszközök.
- Nem felügyelt eszközök.

Ha a Microsoft Edge nem az Intune-szabályzattal van megcélozva, a felhasználók nem használhatják más Intune által felügyelt alkalmazásokból, például az Office-alkalmazásokból származó adatok elérését. 

## <a name="conditional-access-for-microsoft-edge"></a>Feltételes hozzáférés a Microsoft Edge-hez

Az Azure AD feltételes hozzáférés használatával átirányíthatja a felhasználókat, hogy csak a Microsoft Edge használatával férhessenek hozzá a vállalati tartalmakhoz. Ez korlátozza a mobileszköz hozzáférését az Azure AD-hez csatlakoztatott webalkalmazásokhoz a szabályzattal védett Microsoft Edge-hez. Ez blokkolja a más nem védett böngészők, például a Safari vagy a Chrome elérését. Feltételes hozzáférést alkalmazhat az Azure-erőforrásokhoz, például az Exchange Online-hoz és a SharePoint Online-hoz, a Microsoft 365 felügyeleti központhoz, valamint azokhoz a helyszíni helyekhez is, amelyek a külső felhasználók számára elérhetők az [Azure ad Application proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)használatával.

Az Azure AD-hez csatlakozó webalkalmazások korlátozása az iOS-és Android-alapú Microsoft Edge használatára:
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Az Intune csomópontban válassza a **feltételes hozzáférés** > **új házirend**elemet.
3. A panel hozzáférés- **vezérlések** szakaszában válassza a **támogatás** lehetőséget.
4. Válassza ki a **Jóváhagyott ügyfélalkalmazás megkövetelése** elemet.
5. Válassza a **kiválasztás** lehetőséget a **támogatás** ablaktáblán. Ezt a szabályzatot hozzá kell rendelni azokhoz a felhőalkalmazásokhoz, amelyek esetében azt szeretné, hogy csak az Intune Managed Browser alkalmazásból legyenek elérhetők.

    ![A feltételes hozzáférési szabályzat képernyőképe – engedélyezés](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. A hozzárendelések szakaszban válassza a **feltételek** > **alkalmazások**lehetőséget. Megjelenik az **alkalmazások** ablaktábla.
7. A **Konfigurálás**területen válassza az **Igen** lehetőséget, ha a szabályzatot adott ügyfélalkalmazások alkalmazására szeretné alkalmazni.
8. Ellenőrizze, hogy a **Browser** van-e kiválasztva ügyfélalkalmazásként.

    ![A feltételes hozzáférési szabályzat képernyőképe – ügyfélalkalmazások kiválasztása](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Ha korlátozni szeretné, hogy mely natív (nem böngészőbeli) alkalmazások férhetnek hozzá ezekhez a felhőalkalmazásokhoz, válassza a **Mobilalkalmazások és asztali ügyfelek** lehetőséget.

9. A **hozzárendelések** szakaszban válassza a **felhasználók és csoportok**lehetőséget, majd válassza ki azokat a felhasználókat vagy csoportokat, amelyekhez hozzá szeretné rendelni a szabályzatot.

10. A szabályzat védelme alá tartozó alkalmazások megadásához a **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.

A fenti házirend konfigurálása után a felhasználóknak a Microsoft Edge használatára kell használniuk az ezzel a házirenddel védett Azure AD-hez kapcsolódó webalkalmazásokhoz való hozzáférést. Ha ebben a forgatókönyvben a felhasználók nem felügyelt böngészőt próbálnak használni, egy üzenetet kapnak arról, hogy a Microsoft Edge-t kell használniuk.

> [!TIP]
> A feltételes hozzáférés egy Azure AD-technológia. Az Intune-ból elért feltételes hozzáférési csomópont az Azure AD-ből elérhető csomópont.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Egyszeri bejelentkezés az Azure AD-hez csatlakoztatott webalkalmazásokhoz a szabályzattal védett böngészőkben

Az iOS-és Android-alapú Microsoft Edge az egyszeri bejelentkezés (SSO) előnyeit kihasználhatja az Azure AD-hez csatlakozó összes webalkalmazáshoz (SaaS és helyszíni). Az SSO lehetővé teszi, hogy a felhasználók az Azure AD-hez csatlakoztatott webalkalmazásokat a Microsoft Edge használatával férhessenek hozzá anélkül, hogy újra meg kellene adniuk a hitelesítő adataikat.

Az SSO használatához az eszköznek regisztrálnia kell az iOS-eszközök Microsoft Authenticator alkalmazásával, vagy az Androidon futó Intune Céges portál. Ha a felhasználók bármelyike ilyen, a rendszer arra kéri, hogy regisztrálja az eszközét, amikor az Azure AD-hez csatlakozó webalkalmazáshoz egy szabályzat által védett böngészőben csatlakozik. (Ez csak akkor igaz, ha az eszköz még nincs regisztrálva.) Miután az eszköz regisztrálva van az Intune által kezelt felhasználói fiókkal, az Azure AD-hez csatlakozó webalkalmazásokhoz tartozó SSO engedélyezve van.

> [!NOTE]
> Az eszközregisztráció egy egyszerű bejelentkezés az Azure AD szolgáltatással. Nem igényli a teljes eszköz beléptetését, és nem biztosít további jogosultságokat az eszközön.

## <a name="create-a-protected-browser-app-configuration"></a>Egy védett böngésző alkalmazáskonfigurációjának létrehozása

Alkalmazás-konfiguráció létrehozása a Microsoft Edge-hez:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **alkalmazás-konfigurációs házirendek** > **Hozzáadás**elemet.
3. A **konfigurációs szabályzat hozzáadása** panelen adja meg az alkalmazás konfigurációs beállításainak **nevét** és **leírását** (nem kötelező).
4. Az **Eszközregisztráció** típusaként válassza a **Felügyelt alkalmazások** lehetőséget.
5. Válassza **a kötelező alkalmazás kiválasztása**lehetőséget. Ezután a megtekintett **alkalmazások** ablaktáblán válassza az iOS/iPadOS, az Android vagy a (z) rendszerhez tartozó **Managed Browser** vagy **Edge** lehetőséget.
6. A **konfigurációs szabályzat hozzáadása** panelre való visszatéréshez kattintson **az OK gombra** .
7. Válassza a **Konfigurációs beállítások** lehetőséget. A **konfigurációs** panelen kulcs-érték párokat határozhat meg a Microsoft Edge konfigurációinak megadásához. A jelen cikk későbbi részeiben további információt talál a definiálható kulcs-érték párokról.

    > [!NOTE]
    > A Microsoft Edge ugyanazokat a kulcs-érték párokat használja, mint a Managed Browser. Androidon a Microsoft Edge-nek az alkalmazás-konfigurációs szabályzatok érvénybe léptetéséhez az alkalmazás-védelmi szabályzatokat kell megcéloznia.

8. Ha elkészült, kattintson **az OK gombra**.
9. A **konfigurációs szabályzat hozzáadása** panelen válassza a **Hozzáadás**lehetőséget.<br>
    Ekkor létrejön az új konfiguráció, és megjelenik az **alkalmazás konfigurációja** ablaktáblán.

## <a name="assign-the-configuration-settings-you-created"></a>A létrehozott konfigurációs beállítások hozzárendelése 

A beállításokat az Azure AD-ben felhasználói csoportokhoz rendelheti hozzá. Ha az illető felhasználó rendelkezik a célzott védett böngésző telepített példányával, akkor az alkalmazás felügyelete a megadott beállításokkal történik.

1. Az Intune Mobile Application Management irányítópult **alkalmazások** paneljén válassza az alkalmazás- **konfigurációs szabályzatok**lehetőséget.
2. A listából válassza ki a hozzárendelni kívánt alkalmazáskonfigurációt.
3. A következő ablaktáblán válassza a **hozzárendelések**lehetőséget.
4. A **hozzárendelések** ablaktáblán válassza ki azt az Azure ad-csoportot, amelyhez hozzá szeretné rendelni az alkalmazás konfigurációját, majd kattintson az **OK gombra**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>A felhasználókat a Intune Managed Browser helyett a Microsoft Edge-re irányítja 

A Intune Managed Browser és a Microsoft Edge is használható házirend által védett böngészőkként. Annak biztosítása érdekében, hogy a felhasználók a megfelelő böngésző alkalmazás használatára legyenek irányítva, célozza meg az összes Intune által felügyelt alkalmazást (például Outlook, OneDrive és SharePoint) a következő konfigurációs beállítással:

|    Kulcs    |    Érték    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Az érték `true` fogja irányítani a felhasználókat a Microsoft Edge letöltésére és használatára.<br>Az érték `false` lehetővé teszi a felhasználók számára a Intune Managed Browser használatát.    |

Ha az alkalmazás konfigurációs értéke nincs **beállítva,** a következő logika határozza meg, hogy melyik böngészőt fogja használni a vállalati hivatkozások megnyitásához.

Androidon:
- A Intune Managed Browser akkor indul el, ha a felhasználó a Intune Managed Browser és a Microsoft Edge is le van töltve az eszközön. 
- A Microsoft Edge elindítja, ha csak a Microsoft Edge van letöltve az eszközön, és az Intune-szabályzattal van megcélozva.
- Managed Browser elindítja, ha csak Managed Browser van az eszközön, és az Intune-szabályzattal van megcélozva.

IOS/iPadOS esetén olyan alkalmazások esetében, amelyek integrálták az Intune SDK for iOS v-t. 9.0.9+ verziója:
- A Intune Managed Browser akkor indul el, ha a Managed Browser és a Microsoft Edge is az eszközön van.  
- A Microsoft Edge elindítja, ha csak a Microsoft Edge van az eszközön, és az Intune-szabályzattal van megcélozva.
- Managed Browser elindítja, ha csak Managed Browser van az eszközön, és az Intune-szabályzattal van megcélozva.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Alkalmazásproxy-beállítások konfigurálása a Microsoft Edge-hez

A Microsoft Edge és az [Azure ad Application proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) együtt használva hozzáférést biztosíthat a felhasználóknak a mobileszközök intranetes webhelyeihez. 

Íme néhány példa az Azure AD Application Proxy engedélyezésére: 

- A felhasználók az Intune által védett Outlook Mobile alkalmazást használják. Ezután egy e-mailben egy intranetes webhelyre mutató hivatkozásra kattintanak, és a Microsoft Edge felismeri, hogy ez az intranetes hely elérhetővé vált a felhasználó számára az alkalmazásproxy használatával. A rendszer automatikusan átirányítja a felhasználót az Application proxyn keresztül, hogy az intranetes hely elérése előtt hitelesítse magát a megfelelő multi-Factor Authentication és feltételes hozzáféréssel. A felhasználó mostantól hozzáférhet a belső webhelyekhez, még a mobileszközökön is, és az Outlookban található hivatkozás a várt módon működik.
- A felhasználó az iOS-vagy Android-eszközön nyitja meg a Microsoft Edge-t. Ha a Microsoft Edge védelme az Intune-nal történik, és az alkalmazásproxy engedélyezve van, a felhasználó a belső URL-cím használatával megnyithatja az intranetes webhelyet. A Microsoft Edge felismeri, hogy ez az intranetes hely elérhetővé vált a felhasználó számára az alkalmazásproxy használatával. A rendszer automatikusan átirányítja a felhasználót az Application proxyn keresztül a hitelesítéshez az intranetes hely elérése előtt. 

### <a name="before-you-start"></a>Előkészületek

- A belső alkalmazások beállítása az Azure AD Application Proxy használatával.
  - Az Alkalmazásproxy konfigurálásáról és az alkalmazások közzétételéről a [telepítési dokumentációban](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) olvashat.
- A Microsoft Edge alkalmazásnak hozzá kell rendelnie az [Intune app Protection-szabályzatot](app-protection-policy.md) .

> [!NOTE]
> Az Alkalmazásproxy frissített átirányítási adatainak érvénybe lépése a Managed Browserben és a Microsoft Edge-ben akár 24 órát is igénybe vehet.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>1. lépés: automatikus átirányítás engedélyezése a Microsoft Edge-ből az Outlookból
Konfigurálja az Outlookot egy olyan alkalmazás-védelmi szabályzattal, amely lehetővé teszi a **webes tartalom megosztását a szabályzat által felügyelt böngészőkkel**.

![Képernyőkép az alkalmazás-védelmi szabályzatról – webes tartalom megosztása a szabályzattal felügyelt böngészőkkel](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>2. lépés: az alkalmazás-konfigurációs beállítás beállítása az alkalmazásproxy engedélyezéséhez
Célozza meg a Microsoft Edge-t a következő kulcs/érték párokkal, hogy engedélyezze az alkalmazásproxy-t a Microsoft Edge számára:

|    Kulcs    |    Érték    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

További információ arról, hogyan használható a Microsoft Edge és az Azure AD Application Proxy a helyszíni webalkalmazásokhoz való zökkenőmentes (és védett) hozzáféréshez. a jobb együttműködés érdekében lásd: az Intune és a Azure Active Directory összevonása a [felhasználói hozzáférés javítására](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access). Ez a blogbejegyzés a Intune Managed Browserra hivatkozik, de a tartalom a Microsoft Edge-re is vonatkozik.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Kezdőlap parancsikon konfigurálása a Microsoft Edge-hez

Ezzel a beállítással beállíthatja a Microsoft Edge-re mutató parancsikont. Az Ön által konfigurált Kezdőlap a keresősáv alatt első ikonként jelenik meg, amikor a felhasználó új lapot nyit meg a Microsoft Edge-ben. A felhasználó nem tudja szerkeszteni vagy törölni a parancsikont a felügyelt környezetben. A Kezdőlap parancsikon megjeleníti a szervezet nevét, hogy megkülönböztesse azt. 

A Kezdőlap parancsikonjának konfigurálásához használja a következő kulcs/érték párokat:

|    Kulcs    |    Érték    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Adjon meg egy érvényes URL-címet. A helytelen URL-címek biztonsági intézkedésként le vannak tiltva.<br>**Példa:** <`https://www.bing.com`>

## <a name="configure-your-organizations-logo-and-brand-color-for-new-tab-pages-in-microsoft-edge"></a>A szervezet emblémájának és a márka színének konfigurálása új lapokra a Microsoft Edge-ben

Ezekkel a beállításokkal testreszabhatja a Microsoft Edge új lap lapját, hogy az oldal hátterében megjelenjen a szervezet emblémája és a márka színe.

A szervezet emblémájának és színének feltöltéséhez először hajtsa végre a következő lépéseket:
- A Azure Portal belül navigáljon a [Microsoft Endpoint Manager felügyeleti központhoz](https://go.microsoft.com/fwlink/?linkid=2109431) -> **bérlői felügyelet** -> **branding and customization** -> **vállalati identitás arculata**.
- A márka emblémájának beállításához a "Megjelenítés" alatt válassza a "csak vállalati embléma" lehetőséget. A transzparens háttér-emblémák használata javasolt. 
- A márka háttérszínének megadásához a "Megjelenítés" területen válassza a "téma színe" lehetőséget. A Microsoft Edge a szín világosabb árnyalatát alkalmazza az új lap lapon, amely biztosítja, hogy a lap nagy mértékben olvasható legyen. 

Ezután használja a következő kulcs/érték párokat a szervezetek arculatának a Microsoft Edge-be való lekéréséhez:

|    Kulcs    |    Érték    |
|--------------------------------------------------------------------|------------|
|    com. microsoft. Intune. Mam. managedbrowser. NewTabPage. BrandLogo    |    Igaz    |
|    com. microsoft. Intune. Mam. managedbrowser. NewTabPage. BrandColor    |    Igaz    |

## <a name="display-relevant-industry-news-on-new-tab-pages"></a>Releváns iparági Hírek megjelenítése az új lapokon

A Microsoft Edge Mobile szolgáltatásban az új lap felületét az iparági Hírek megjelenítéséhez is beállíthatja, amely a szervezet számára fontos. Ha engedélyezi ezt a funkciót, a Microsoft Edge Mobile a szervezet tartománynevét használja a webes Hírek összesítésére a szervezet, a szervezet iparága és a versenytársak számára, így a felhasználók a központi Újdonságok alapján találhatják meg a releváns külső híreket. Lap lapjai a Microsoft Edge-ben. Az iparági Hírek alapértelmezés szerint ki vannak kapcsolva, és a segítségével a szervezet számára engedélyezhető. 

|    Kulcs    |    Érték    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com. microsoft. Intune. ShowIndustryNews    |    Az **igaz** érték jelenik meg az iparági hírekben a Microsoft Edge Mobile új lapján.<p>A **false** (alapértelmezett) értékkel elrejtheti az iparági híreket az új lap lapról.    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Felügyelt könyvjelzők konfigurálása a Microsoft Edge-hez

A könnyű hozzáférés érdekében beállíthatja, hogy a felhasználók a Microsoft Edge használatakor milyen könyvjelzőket adjanak elérhetővé. 

Íme néhány részlet:

- Ezek a könyvjelzők csak akkor jelennek meg a felhasználók számára, ha a Microsoft Edge [vállalati üzemmódját](https://docs.microsoft.com/intune/apps/app-configuration-managed-browser#how-to-configure-bookmarks-for-a-protected-browser) használják. 
- A felhasználók nem törölhetik és nem módosíthatják ezeket a könyvjelzőket.
- Ezek a könyvjelzők a lista tetején jelennek meg. A felhasználók által létrehozott könyvjelzők a könyvjelzők alatt jelennek meg.
- Ha engedélyezte az alkalmazásproxy átirányítását, akkor a belső vagy külső URL-cím használatával adhat hozzá alkalmazásproxy-webalkalmazásokat.
- Győződjön meg arról, hogy az összes URL-cím előtaggal van **http://** vagy **https://** , amikor beírja őket a listára.

A felügyelt könyvjelzők konfigurálásához használja a következő kulcs/érték párokat:

|    Kulcs    |    Érték    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    A konfiguráció értéke könyvjelzők listája. Mindegyik könyvjelző a könyvjelző és a könyvjelző URL-címét tartalmazza. Válassza el a címet és az URL-címet a `|` karakterrel.      Például:<br>`Microsoft Bing|https://www.bing.com`<br>Több könyvjelző konfigurálásához válassza el az egyes párokat a dupla karakter `||`.<p>Például:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>MyApps megjelenítése a Microsoft Edge-könyvjelzők között

Alapértelmezés szerint a felhasználók a Microsoft Edge-könyvjelzőn belül egy mappában konfigurált MyApps-helyeket jelenítik meg. A mappa a szervezet nevével van megjelölve.

|    Kulcs    |    Érték    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    A **true (igaz** ) érték a Microsoft Edge-könyvjelzőn belüli MyApps mutatja.<p>**Hamis** elrejti a MyApps a Microsoft Edge-n belül.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Engedélyezett vagy letiltott webhelyek listájának megadása a Microsoft Edge-hez
Az alkalmazás konfigurációja segítségével meghatározhatja, hogy a felhasználók mely helyeket érhetik el a munkahelyi profil használatakor. Ha engedélyezési listát használ, a felhasználók csak a már felsorolt webhelyek elérésére képesek. Ha letiltott listát használ, a felhasználók az összes helyet elérhetik, kivéve azokat, amelyeket kifejezetten blokkolt. Csak egy engedélyezett vagy letiltott listát kell kiírnia, mindkettőt nem. Ha mindkettőt bevezeti, a rendszer az engedélyezett listát is tiszteletben tartja.  

A következő kulcs/érték párokkal konfigurálhatja a Microsoft Edge számára engedélyezett vagy letiltott helyek listáját. 

|    Kulcs    |    Érték    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    A következő lehetőségek közül választhat:<p>1. az engedélyezett URL-címek megadása (csak ezek az URL-címek engedélyezettek, más webhelyek nem érhetők el):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. a blokkolt URL-címek megadása (az összes többi hely elérhető):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    A kulcs megfelelő értéke egy URL-címlista. Minden olyan URL-címet meg kell adnia, amelyet egyetlen értékként szeretne engedélyezni vagy letiltani, egy pipe `|` karakterrel elválasztva.<br>**Példák**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Az engedélyezett és a letiltott helyek listájának URL-formátuma 
Az engedélyezett/letiltott webhelyek listája a különböző URL-címek használatával hozható létre. Ezek az engedélyezett minták a következő táblázatban vannak részletezve. Néhány megjegyzés az első lépések előtt: 
- Győződjön meg arról, hogy az összes URL-cím előtaggal van **http://** vagy **https://** , amikor beírja őket a listára.
- A helyettesítő karakteres szimbólumot (\*) a következő engedélyezett minták listájában szereplő szabályok alapján használhatja.
- Egy helyettesítő karakter csak az állomásnév teljes összetevőjével (ponttal elválasztva) vagy az elérési út teljes részével (a továbbítási perjelekkel elválasztva) egyezik. A `http://*contoso.com` például **nem** támogatott.
- A címben portszámokat is megadhat. Ha nem ad meg portszámot, a rendszer a következő értékeket használja:
  - HTTP – 80-as port
  - HTTPS – 443-as port
- A portszám helyettesítő karakterrel való használata **nem** támogatott. Például a `http://www.contoso.com:*` és a `http://www.contoso.com:*/` nem támogatottak. 

    |    URL-cím    |    Részletek    |    Egyezik    |    Nem egyezik    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Egyetlen lapnak felel meg    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Egyetlen lapnak felel meg    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    Az összes `www.contoso.com` karakterlánccal kezdődő URL-cím    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Az összes altartományra illeszkedik `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`
    |    `http://*contoso.com/*`    |    Az összes `contoso.com/` végződésű altartományra illeszkedik    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    Egyetlen mappa    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Egyetlen lapra illeszkedik, egy portszám használatával    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Egyetlen biztonságos lap    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Egyetlen mappa és annak összes almappája    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- A következő példák a nem megadható bemenetekre mutatnak:
  - `*.com`
  - `*.contoso/*`
  - `www.contoso.com/*images`
  - `www.contoso.com/*images*pigs`
  - `www.contoso.com/page*`
  - IP-címek
  - `https://*`
  - `http://*`
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="transition-users-to-their-personal-context-when-trying-to-access-a-blocked-site"></a>Felhasználók átváltása a személyes környezetbe egy letiltott hely elérésére tett kísérlet során

A Microsoft Edge-be épített kettős identitású modellel rugalmasabb felhasználói élményt biztosíthat a végfelhasználók számára, mint amennyire a Intune Managed Browser. Ha a felhasználók egy letiltott helyet észlelnek a Microsoft Edge-ben, a munkakörnyezetük helyett megkérheti, hogy nyissa meg a hivatkozást a személyes környezetében. Ez lehetővé teszi számukra, hogy védve maradjanak, miközben a vállalati erőforrások biztonságban maradhatnak. Ha például egy felhasználó az Outlookon keresztül egy újságcikkre mutató hivatkozást kap, akkor a hivatkozást a személyes kontextusban vagy egy InPrivate lapon nyithatja meg. A munkahelyi környezet nem teszi lehetővé a hírek webhelyeinek használatát. Alapértelmezés szerint ezek a váltások engedélyezettek.

A következő kulcs/érték párokkal konfigurálhatja, hogy engedélyezettek-e az alábbi Soft-váltások:

|    Kulcs    |    Érték    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** (alapértelmezett) – lehetővé teszi a Microsoft Edge számára a felhasználók személyes környezetbe való átváltását a blokkolt helyek megnyitására.<p>**False (hamis** ) – megakadályozza, hogy a Microsoft Edge áttérjen a felhasználóknak. A felhasználók egyszerűen megjelenítenek egy üzenetet arról, hogy az elérni kívánt hely le van tiltva.    |

## <a name="open-restricted-links-directly-in-inprivate-tab-pages"></a>A korlátozott hivatkozások közvetlen megnyitása InPrivate-lapokon

Beállíthatja, hogy a korlátozott hivatkozások közvetlenül az InPrivate-böngészésben legyenek megnyitva, ami zökkenőmentes böngészést biztosít a felhasználóknak. Ezzel a lépéssel megtakaríthatja a felhasználókat, hogy áttérjenek a személyes környezetre a hely megtekintéséhez. A InPrivate-böngészés nem felügyelt, így a felhasználók nem fognak tudni hozzáférni InPrivate-böngészési mód használata esetén.

|    Kulcs    |    Érték    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.openInPrivateIfBlock`    |    Az **igaz** érték automatikusan nyitja meg a helyeket egy InPrivate-lapon anélkül, hogy a felhasználót arra kellene kérni, hogy a személyes fiókjára váltson. <p> A **false** (alapértelmezett) érték letiltja a helyet a Microsoft Edge-en belül, és a rendszer arra kéri a felhasználót, hogy váltson a személyes fiókjára a megtekintéshez.    |

## <a name="disable-microsoft-edge-features-to-customize-the-end-user-experience-for-your-organizations-needs"></a>A Microsoft Edge-funkciók letiltása a szervezet igényeinek megfelelő végfelhasználói élmény testreszabásához

### <a name="disable-prompts-that-offer-to-save-passwords"></a>A jelszavak mentéséhez felkínált kérések letiltása
Alapértelmezés szerint a Microsoft Edge iOS-ben a felhasználók jelszavait mentheti a kulcstartóba. Ha le szeretné tiltani ezt a kérdést a szervezete számára, konfigurálja a következő beállítást:

|    Kulcs    |    Érték    |
|-----------------------|-----------------------|
|    `com.microsoft.intune.mam.managedbrowser.disableFeatures`    |    a **jelszó** letiltja a végfelhasználók jelszavának mentésére vonatkozó kéréseket.    |

### <a name="disable-inprivate-browsing-and-microsoft-accounts-to-restrict-browsing-to-work-only-contexts"></a>Az InPrivate-böngészés és a Microsoft-fiókok letiltása a csak munkahelyi környezetekben való böngészés korlátozására

Ha a szervezete egy magasan szabályozott iparágban működik, vagy egy alkalmazáson belüli VPN-t használ, hogy a felhasználók hozzáférjenek a munkahelyi erőforrásokhoz a Microsoft Edge használatával, dönthet úgy, hogy a Microsoft Edge hatókörét csak MAM-védelemmel ellátott környezetre használja. Ez a funkció csak a MDM által regisztrált eszközökhöz érhető el.

|    Kulcs    |    Érték    |
|-----------|-------------|
|    `com.microsoft.intune.mam.managedbrowser.disableFeatures`    |    **InPrivate** – letiltja az InPrivate-böngészést, <br> a **MSA** letiltja a felhasználók személyes Microsoft-fiókjaik (MSA-EK) hozzáadását a Microsoft Edge-alkalmazásokhoz. <br> Több szolgáltatás letiltásához válassza a `|`az értékeket. Például `inprivate|msa` letiltja az InPrivate-és a személyes fiókokat is.   |

### <a name="restrict-microsoft-edge-use-to-allowed-accounts-only"></a>A Microsoft Edge használatának korlátozása csak a fiókok számára

A InPrivate-és MSA-böngészés letiltása mellett csak akkor engedélyezheti a Microsoft Edge használatát, ha a felhasználó a HRE-fiókjával van bejelentkezve. Ez a funkció csak MDM regisztrált felhasználók számára érhető el. A beállítás konfigurálásával kapcsolatos további információkért tekintse meg a következőt:

- [Android-beállítás](~/apps/app-configuration-policies-use-android.md#allow-only-configured-organization-accounts-in-multi-identity-apps)
- [iOS-beállítás](~/apps/app-configuration-policies-use-ios.md#allow-only-configured-organization-accounts-in-multi-identity-apps)

## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>A Microsoft Edge használata iOS rendszeren a felügyelt alkalmazások naplóihoz való hozzáféréshez 

Az iOS-eszközön telepített Microsoft Edge-felhasználók megtekinthetik a Microsoft által közzétett alkalmazások felügyeleti állapotát. Elküldhetik a naplófájlokat a felügyelt iOS-eszköz hibaelhárítása céljából. Ezt a következőképpen teheti meg:
1. Nyissa meg a Microsoft Edge-t iOS-eszközén.
2. A címsorba gépelje be a következőt: `about:intunehelp` 
3. A Microsoft Edge elindítja a hibaelhárítási módot.

Az alkalmazásnaplókban tárolt beállítások listáját az [Alkalmazásvédelmi naplók áttekintése a Managed Browserben](app-protection-policy-settings-log.md) című témakörben találja.

Ha szeretné megtudni, hogyan tekintheti meg a naplókat az Android-eszközökön, tekintse meg a [naplók elküldése e-mailben](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)című témakört. 

## <a name="security-and-privacy-for-microsoft-edge"></a>Biztonság és adatvédelem a Microsoft Edge-ben

A Microsoft Edge-re vonatkozó további biztonsági és adatvédelmi megfontolások a következők:

- A Microsoft Edge nem használja fel azokat a beállításokat, amelyeket a felhasználók a natív böngészőhttps://docs.microsoft.com/en-us/intune/apps/app-configuration-policies-use-android#allow-only-configured-organization-accounts-in-multi-identity-apps állítanak be az eszközökön, mert a Microsoft Edge nem fér hozzá ezekhez a beállításokhoz.
- Beállíthatja, hogy az **egyszerű PIN-kód megkövetelése a hozzáféréshez** vagy a **vállalati hitelesítő adatok megkövetelése a hozzáféréshez** a Microsoft Edge-hez társított alkalmazás-védelmi szabályzatban. Ha a felhasználó kiválasztja a Súgó hivatkozást a hitelesítés lapon, böngészhet bármely internetes webhelyen, függetlenül attól, hogy hozzáadták-e őket a szabályzat letiltott listájához.
- A Microsoft Edge csak akkor képes blokkolni a hozzáférést a webhelyekhez, ha azokat közvetlenül érik el. Nem blokkolja a hozzáférést, ha a felhasználó köztes szolgáltatásokat (például egy fordítási szolgáltatást) használ a hely eléréséhez.
- A hitelesítés engedélyezéséhez és az Intune-dokumentációhoz való hozzáféréshez a ***. microsoft.com** kivételt képez az engedélyezési vagy tiltólista beállításai alól. Mindig engedélyezve van.
- A felhasználók kikapcsolhatják az adatgyűjtés lehetőségeit. A Microsoft termék- és szolgáltatásfejlesztési célból automatikus módszerekkel név nélküli adatokat gyűjt a Managed Browser teljesítményéről és használatáról. A felhasználók kikapcsolhatják az adatgyűjtést az eszköz **Használati adatok** beállításával. Nem tudja befolyásolni ezen adatok gyűjtését. IOS-eszközökön nem nyithatók meg azok a webhelyek, amelyeken lejárt vagy nem megbízható tanúsítvánnyal rendelkező felhasználók látogatnak.

## <a name="next-steps"></a>További lépések

- [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md) 
