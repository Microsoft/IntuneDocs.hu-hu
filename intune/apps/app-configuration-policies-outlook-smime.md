---
title: Az S/MIME konfigurálása az iOS rendszerhez készült Outlook alkalmazásban Microsoft Intune
description: Az S/MIME ismertetése az iOS rendszerhez készült Outlook alkalmazással Microsoft Intuneban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b2f483415d050486ae9979899d9308154a9b131
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74412016"
---
# <a name="configure-smime-with-outlook-for-ios"></a>S/MIME konfigurálása iOS-hez készült Outlookkal

A Secure/Multipurpose Internet Mail Extensions (S/MIME) kiegészítő biztonsági réteget biztosít az Exchange ActiveSync-(EAS-) fiókba küldött e-mailekhez. A [Microsoft Outlook](https://aka.ms/omsmime) az S/MIME használatával lehetővé teszi, hogy a felhasználók titkosítsák a kimenő üzeneteket és a mellékleteket, így biztosítható, hogy csak a címzett tudja olvasni és elérni az üzenet tartalmát az Office 365-fiókok használatakor. A felhasználók digitálisan is aláírnak egy üzenetet, így a címzettek is ellenőrizhetik a küldő identitását, és ellenőrizhetik, hogy az üzenet nem lett-e illetéktelenül módosítva. Ez a képesség a tanúsítványok használatával lehetséges. További információ: az [S/MIME ismertetése](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> Ez a témakör a megbízható főtanúsítványok [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)használatával történő központi telepítését ismerteti. A Microsoft Endpoint Manager egyetlen, integrált végpont-felügyeleti platform az összes végpont kezeléséhez. Ez a Microsoft Endpoint Manager felügyeleti központ integrálja a ConfigMgr és a Microsoft Intune.

## <a name="about-message-encryption"></a>Az üzenetek titkosítása
A felhasználók titkosított üzenetet küldhetnek a szervezeten belüli személyeknek és a szervezeten kívüli személyeknek, ha a titkosítási tanúsítványok nyilvános részét képezik. A titkosítási tanúsítványokhoz társított titkos kulcsokat mindig védeni kell, és biztosítani kell a titkosított üzenet címzettjeinek. A titkosítási tanúsítvány titkos kulcsa az üzenet címzett általi visszafejtésére szolgál.

A titkosított üzeneteket csak azok a címzettek tudják olvasni, akik az üzenetet titkosító tanúsítvánnyal rendelkeznek. Ha olyan címzett (ek) hoz küld titkosított üzenetet, amelynek titkosítási tanúsítványa nem érhető el, az alkalmazás felszólítja, hogy távolítsa el ezeket a címzetteket az e-mail elküldése előtt.

## <a name="about-digital-signatures"></a>Tudnivalók a digitális aláírásokról
A digitálisan aláírt üzenet megerősíti a címzettet, hogy az üzenet nem lett illetéktelenül módosítva, és a küldő személyazonossága is hiteles. A címzettek csak akkor ellenőrizhetik a digitális aláírást, ha olyan e-mail-ügyfélprogramot használnak, amely támogatja az S/MIME-t.

## <a name="prerequisites"></a>Előfeltételek
- Az iOS-es Outlook csak az S/MIME-t támogatja az Office 365-fiókokban.
- Az S/MIME-t az Office 365-hez kell konfigurálni. További információ: [az S/MIME konfigurálása az Office 365-ben](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516).
- Az aláíráshoz és titkosításhoz használható tanúsítványokat kiállító hitelesítésszolgáltatóval kell rendelkeznie.
- Megbízható legfelső szintű tanúsítványok központi telepítése a Endpoint Manager használatával. További információt a [megbízható tanúsítványok profiljainak létrehozása](~/protect/certificates-configure.md#create-trusted-certificate-profiles)című témakörben talál.
- A titkosítási tanúsítványokat a Endpoint Managerbe kell importálni. További információt az [importált PKCS-tanúsítványok konfigurálása és használata az Intune](~/protect/certificates-imported-pfx-configure.md)-nal című témakörben talál.
- Telepítse és konfigurálja a PFX-összekötőt Microsoft Intune számára. További információ: [a pfx tanúsítvány-összekötő letöltése, telepítése és konfigurálása Microsoft Intunehoz](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- Az eszközöknek regisztrálva kell lenniük ahhoz, hogy megbízható legfelső szintű és S/MIME-tanúsítványokat MDM a Endpoint Managerből.

> [!IMPORTANT]
> Le kell töltenie és telepítenie kell a frissített PFX-összekötőt (6.1911.11.0 vagy újabb verzió) ahhoz, hogy az S/MIME titkosítási tanúsítványokat az iOS-hez készült Outlook használatával Microsoft Intune.

## <a name="smime-support-in-outlook-for-ios"></a>S/MIME-támogatás az iOS-hez készült Outlookban
Az iOS-hez készült Outlook támogatja a tanúsítványokat használó üzenetek S/MIME-aláírását és titkosítását. Számos ügyfél külön aláírási és titkosítási tanúsítvánnyal rendelkezik, és nem rendelkezik egyetlen tanúsítvánnyal, amely támogatja az aláírást és a titkosítást is. Az aláíró tanúsítványok általában egyediek az egyes felhasználók regisztrált eszközein, míg a titkosítási tanúsítványok egy adott felhasználó által regisztrált eszközökön vannak megosztva. A felhasználók gyakran használják az S/MIME-t évekre, és az idő múlásával különböző titkosítási tanúsítványokat használtak a tanúsítványok megújítása után. A titkosítási tanúsítvány előzményeinek, beleértve a titkos kulcsokat is, jelen kell lennie a felhasználó eszközén, hogy az esetlegesen titkosított e-mailek a múltban is olvashatók legyenek. Az aláírást és a titkosítást támogató egyetlen tanúsítvánnyal is rendelkezhet.

Az iOS-hez készült Outlook két módszert támogat a tanúsítványok eszközökre való kézbesítésére, hogy azok az S/MIME-hez használhatók legyenek:

- A **felhasználók** saját maguk is elküldhetik az e-mail-EK/MIME-tanúsítványokat, és telepíthetik őket az iOS rendszerű eszközökön lévő mellékletekből mobileszközökön
- A **rendszergazdák** bármely hitelesítésszolgáltatótól importálni tudják a titkosítási tanúsítvány előzményeit a Endpoint Managerbe. A Endpoint Manager ezután automatikusan továbbítja ezeket a tanúsítványokat a felhasználó által regisztrált összes eszközre. A tanúsítványok aláírására általában Egyszerű tanúsítványigénylési protokoll (SCEP) használatos. A SCEP használatával a rendszer létrehozza és tárolja a titkos kulcsot a regisztrált eszközön, és egy egyedi tanúsítványt továbbít minden olyan eszközhöz, amelyet a felhasználó regisztrál, ami nem megtagadásra használható. A rendszergazdák a végfelhasználók számára a Endpoint Managerbe importálják a titkosítási tanúsítvány előzményeit, amely ezután az összes felhasználó titkosítási tanúsítványát továbbítja a regisztrált eszközökhöz. Végül a Endpoint Manager támogatja a származtatott hitelesítő adatokat azon ügyfelek számára, akik támogatást igényelnek a NIST 800-157 szabványhoz. IOS rendszeren a Céges portál az aláírási és titkosítási tanúsítványok Intune-ból való beolvasására szolgál.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Az Outlook konfigurálása iOS S/MIME-hez a Endpoint Managerben
Az Outlook for iOS S/MIME konfigurálásához a Endpoint Managerben, beleértve az iOS-hez használható Outlook által használható S/MIME-tanúsítványok automatikus kézbesítését, az alábbi lépéseket követve:

### <a name="add-the-microsoft-outlook-app"></a>A Microsoft Outlook alkalmazás hozzáadása
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Adja hozzá a Microsoft Outlook iOS-alkalmazást az App Store-ból a Endpoint Managerbe, vagy az iOS-hez készült Outlookot a Apple Volume Purchase Program. További információ: iOS-es [áruházbeli alkalmazások hozzáadása a Microsoft Intunehoz](~/apps/store-apps-ios.md) , vagy [a Apple Volume Purchase Program által a Microsoft Intune használatával vásárolt iOS-és MacOS-alkalmazások kezelése](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Az Outlook for iOS S/MIME-konfigurációs szabályzat létrehozása

A következő lépésekkel hozhatja létre és konfigurálhatja az Outlook for iOS S/MIME-szabályzatot a Endpoint Managerben. Ezek a beállítások biztosítják az aláírási és titkosítási tanúsítványok automatikus kézbesítését.

1. A [Microsoft Endpoint Manager felügyeleti központban](https://go.microsoft.com/fwlink/?linkid=2109431)válassza az **alkalmazások** > **alkalmazások konfigurációs szabályzatok** > **Hozzáadás**elemet.<br>
Ekkor megjelenik a **konfigurációs szabályzat hozzáadása** panel.
2. Adja meg a konfigurációs szabályzat **nevét** és **leírását** .
3. Válassza a **felügyelt eszközök** lehetőséget az **eszköz beléptetési típusaként**.
4. **Platformként**válassza az **iOS/iPadOS** lehetőséget.
5. Kattintson **a szükséges alkalmazás kiválasztása** elemre a korábban hozzáadott Microsoft Outlook iOS-alkalmazás megkereséséhez és hozzárendeléséhez. 
6. A konfigurációs beállítások hozzáadásához kattintson a **konfigurációs beállítások** elemre. 
    - Válassza a Configuration **Designer használata** a **konfigurációs beállítások formátuma** mellett lehetőséget, és fogadja el az alapértelmezett beállításokat. További információ: [Microsoft Outlook konfigurációs beállítások](~/apps/app-configuration-policies-outlook.md).
7. Kattintson az **s/MIME** elemre az **Outlook s/MIME beállításainak**megjelenítéséhez.

    ![Képernyőkép az Outlookról az iOS S/MIME-beállításokhoz](./media/app-configuration-policies-outlook-smime/app-configuration-policies-outlook-smime-01.png)

8. Az **S/MIME engedélyezése** beállítást állítsa **Igen**értékre.
9. Állítsa **az S/MIME-tanúsítványok telepítése az Intune-ból** **Igen értéket**.
10. A **tanúsítvány-profil típusa**melletti **tanúsítványok aláírása** területen válasszon az alábbi lehetőségek közül:
    - **SCEP** – létrehoz egy olyan tanúsítványt, amely egyedi az eszközhöz és a felhasználó számára, amelyet a Microsoft Outlook az aláíráshoz használhat. Kapcsolódó információk: az [infrastruktúra konfigurálása a SCEP támogatásához az Intune](~/protect/certificates-scep-configure.md) -nal és [egy SCEP-tanúsítvány profiljának létrehozása](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **PKCS importált tanúsítványok** – a felhasználó számára egyedi tanúsítványt használ, de az eszközök között megoszthatók, és a rendszergazda által az Endpoint Managerbe importálták a felhasználó nevében. A tanúsítványt minden olyan eszköz megkapja, amelyet a felhasználó regisztrál. A Endpoint Manager automatikusan kiválasztja azt az importált tanúsítványt, amely támogatja az aláírást, hogy az megfeleljen a regisztrált felhasználónak.
    - **Származtatott hitelesítő adatok** – olyan tanúsítványt használ, amely már szerepel az aláíráshoz használható eszközön. A tanúsítványt az Intune-ban található származtatott hitelesítő adatok használatával kell lekérni az eszközön.
11. A **tanúsítvány profilja típusa**melletti **titkosítási tanúsítványok** területen válasszon az alábbi lehetőségek közül:
    - **PKCS importált tanúsítványok** – a rendszergazda által a végpont-kezelőnek importált összes olyan titkosítási tanúsítvány továbbítása, amelyet a felhasználó regisztrál a Endpoint Manager automatikusan kiválasztja az importált tanúsítványt vagy tanúsítványokat, amelyek támogatják a titkosítást a regisztrált felhasználóhoz tartozó eszköz számára.
    - **Származtatott hitelesítő adatok** – olyan tanúsítványt használ, amely már szerepel az aláíráshoz használható eszközön. A tanúsítványt az Intune-ban található származtatott hitelesítő adatok használatával kell lekérni az eszközön.
12. A **végfelhasználói értesítések**mellett válassza a végfelhasználók értesítése lehetőséget, ha **céges portál** vagy **e-mailt** szeretne kapni az iOS-hez készült Outlookhoz tartozó S/MIME-tanúsítványok lekéréséhez.

    IOS rendszeren a felhasználóknak a Céges portál alkalmazást kell használniuk az S/MIME-tanúsítványok lekéréséhez. A Endpoint Manager tájékoztatja a felhasználót, hogy a Céges portál elindításához el kell indítania az S/MIME-tanúsítványokat Céges portál, leküldéses értesítés és/vagy e-mailek értesítések szakaszán keresztül. Ha az egyik értesítésre kattint, a felhasználó egy olyan kezdőlapra kerül, amely tájékoztatja a tanúsítványok lekérésének folyamatáról. A tanúsítványok beolvasása után a felhasználó az iOS-hez készült Microsoft Outlookból is használhatja az S/MIME-t az e-mailek aláírására és titkosítására.
    
    A végfelhasználói értesítések a következő lehetőségeket tartalmazzák:
       - **Céges portál** – ha be van jelölve, a felhasználók leküldéses értesítést küldenek az eszközön, amely az S/MIME-tanúsítványok beolvasására szolgáló céges portál a kezdőlapra kerül.
        - **E-mail** – e-mail küldése a végfelhasználónak, amely tájékoztatja őket arról, hogy az S/MIME-tanúsítványok lekéréséhez el kell indítaniuk céges portál. Ha a felhasználó a regisztrált iOS-eszközön van, amikor az e-mailben található hivatkozásra kattint, a rendszer átirányítja a Céges portál a tanúsítványok lekéréséhez.
    
13. Válassza a **hozzárendelések** lehetőséget az alkalmazás konfigurációs házirendjének az Azure ad-csoportokhoz való hozzárendeléséhez. További információ: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](~/apps/apps-deploy.md).

## <a name="next-steps"></a>További lépések

- További információ: [Microsoft Intune alkalmazás-konfigurációs szabályzatai](app-configuration-policies-overview.md).
