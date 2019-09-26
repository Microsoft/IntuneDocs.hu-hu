---
title: A Windows Holographic Business beállításai – Microsoft Intune – Azure |} A Microsoft Docs
description: Az Azure-ban elolvashatja és konfigurálhatja a Microsoft Intune a Windows Holographic for Business-eszközökre vonatkozó eszközkorlátozási beállításait, így a regisztrációtörléssel, a földrajzi hellyel, a jelszavakkal, az áruházból telepített alkalmazásokkal, a Microsoft Edge sütijeivel és felugró ablakaival, a Windows Defenderrel, a kereséssel, a felhőtárhellyel, a Bluetooth-kapcsolattal, a rendszeridővel és a használati adatokkal kapcsolatos beállításokat.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bea8d6d8e3503b9ec6fba7b2eda4842b68786e54
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/19/2019
ms.locfileid: "71302304"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Windows Holographic for Business eszközbeállítások engedélyezett vagy korlátozott funkciók az Intune-nal

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk és szabályozhatja a különböző beállításokat ismerteti a Windows Holographic for Business-eszközök, például a Microsoft Hololens. A mobileszköz-felügyelet (MDM) megoldás részeként használja ezeket a beállításokat engedélyezi vagy letiltja a szolgáltatások, a biztonság szabályozásához és egyéb.

## <a name="before-you-begin"></a>Előkészületek

[Eszközkonfigurációs profil létrehozása](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Általános

- **Regisztráció manuális**törlése: Lehetővé teszi a felhasználó számára a munkahelyi fiók manuális törlését az eszközről.
- **Cortana**: A Cortana beszédfelismerési asszisztens engedélyezése vagy letiltása.
- Földrajzi **hely:** Meghatározza, hogy az eszköz használhatja-e a helyalapú szolgáltatások adatait.

## <a name="password"></a>Windows 10

- **Jelszó**: Megköveteli a végfelhasználótól, hogy jelszót adjon meg az eszköz eléréséhez.
- **Jelszó megkövetelése, ha az eszköz visszatér az inaktív állapotból**: Megadja, hogy a felhasználónak meg kell adnia egy jelszót az eszköz zárolásának feloldásához.

## <a name="app-store"></a>Alkalmazásáruház

- **Az áruházból származó alkalmazások automatikus frissítése**: Lehetővé teszi, hogy a Microsoft Store telepített alkalmazások automatikusan frissüljenek.
- **Megbízható alkalmazás telepítése**: Lehetővé teszi, hogy a megbízható tanúsítvánnyal aláírt alkalmazások közvetlenül telepített legyenek.
- **Fejlesztői zárolás feloldása**: Engedélyezze a Windows fejlesztői beállításait, például lehetővé teszi a közvetlenül telepített alkalmazások módosítását a végfelhasználók számára.

## <a name="microsoft-edge-browser"></a>Microsoft Edge böngésző

- **Cookie-k**: Lehetővé teszi a böngésző számára az internetes cookie-k mentését az eszközre.
- **Előugró ablakok**: Blokkolja az előugró ablakokat a böngészőben (csak a Windows 10 asztali verzióra vonatkozik).
- **Keresési javaslatok**: Lehetővé teszi, hogy a keresőmotor webhelyeket javasoljon a keresőkifejezések beírása közben.
- **Password Manager**: A Microsoft Edge Password Manager funkció engedélyezése vagy letiltása.
- **Nem nyomon követett fejlécek küldése**: Úgy konfigurálja a Microsoft Edge böngészőt, hogy ne kövesse nyomon a fejléceket a felhasználók által felkeresett webhelyeken.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen a Microsoft Edge-hez**: A Microsoft Edge SmartScreen engedélyezése a hely-és fájlletöltés eléréséhez.

## <a name="search"></a>Keresés

- **Helyadatok kereséshez** – Annak megadása, hogy a keresési funkció használhatja-e a helyadatokat. információ

## <a name="cloud-and-storage"></a>Felhő és tárolás

- **Microsoft-fiók**: Lehetővé teszi, hogy a felhasználó Microsoft-fiókot társítson az eszközhöz.

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

- **Bluetooth**: Azt szabályozza, hogy a felhasználó engedélyezheti és konfigurálhatja-e a Bluetooth-t az eszközön.
- **Bluetooth-felderíthetőség**: Lehetővé teszi, hogy az eszközt más Bluetooth-kompatibilis eszközök is felderítsék.
- **Bluetooth-hirdetés**: Lehetővé teszi, hogy az eszköz hirdetéseket kapjon Bluetooth-kapcsolaton keresztül.

## <a name="control-panel-and-settings"></a>Vezérlőpult és Gépház

- **Rendszeridő módosítása**: Megakadályozza, hogy a végfelhasználó megváltoztassa az eszköz dátumát és időpontját.

## <a name="kiosk---obsolete"></a>Kioszkmód – elavult

Ezek a beállítások csak olvashatók, és nem módosíthatók. A kioszkmód konfigurálásáról a [Kioszkbeállítások](kiosk-settings-holographic.md) című cikkből tájékozódhat.

A kioszkeszközök jellemzően egy adott alkalmazást futtatnak. A rendszer a felhasználóknak csak a kioszkalkalmazáshoz ad hozzáférést, és meggátolja az eszköz más funkcióinak és szolgáltatásainak elérését.

- Teljes **képernyős mód**: Meghatározza a házirend által támogatott kioszk mód típusát. A lehetőségek a következők:

  - **Nincs konfigurálva** (alapértelmezett): A házirend nem engedélyezi a kioszk üzemmódot. 
  - **Egyalkalmazásos kioszk**: A profil lehetővé teszi, hogy az eszköz csak egy alkalmazást futtasson. Amikor a felhasználó bejelentkezik, elindul az adott alkalmazás. Ez a mód emellett meggátolja a felhasználót abban, hogy új alkalmazásokat nyisson meg vagy másik futó alkalmazásra váltson.
  - **Többalkalmazásos kioszk**: A profil lehetővé teszi, hogy az eszköz több alkalmazást futtasson. Csak a hozzáadott alkalmazások lesznek elérhetők a felhasználónak. A többalkalmazásos kioszk (vagy fix célú eszköz) előnye az, hogy egy olyan, könnyen érthető környezetet nyújt a felhasználónak, amelyben csak a szükséges alkalmazások érhetőek el. Azokat az alkalmazásokat pedig, amelyekre nincsen szükség, elrejti a rendszer. 
  
    Amikor egy többalkalmazásos kioszkhoz alkalmazásokat ad hozzá, egy fájlt is meg kell adnia a Start menü elrendezéséhez. A [Start menü elrendezési fájlját](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others) bemutató cikk tartalmaz egy minta XML-fájlt is, amelyet használhat az Intune-ban. 

### <a name="single-app-kiosks"></a>Egyalkalmazásos kioszk

Adja meg a következő beállításokat:

- **Felhasználói fiók**: Adja meg a kioszk alkalmazáshoz társított helyi (eszköz) felhasználói fiókot vagy az Azure AD-fiók bejelentkezési adatait. Azure AD-tartományhoz csatlakozó fiókot a következő formában tud megadni: `domain\username@tenant.org`. 

    Nyilvános környezetben működő, automatikus bejelentkezésű kioszkeszköz esetében ajánlott a legalacsonyabb szintű hozzáféréssel rendelkező felhasználótípust (például egyszerű helyi felhasználó fiókot) választania. Ha Azure Active Directory- (AD-) fiókot kíván konfigurálni a kioszkmódhoz, használja az `AzureAD\user@contoso.com` formátumot.

- **Alkalmazás felhasználói modell-azonosítója (AUMID)** : Adja meg a kioszk alkalmazás AUMID. További információkat a [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Telepített alkalmazás alkalmazásfelhasználói modellben használt azonosítójának megkeresése) című témakörben találhat.

## <a name="reporting-and-telemetry"></a>Jelentéskészítés és telemetria

- **Használati adatok megosztása**: Válassza ki a diagnosztikai adatok beküldésének szintjét.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
