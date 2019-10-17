---
title: Windows holografikus üzleti eszköz beállításai – Microsoft Intune – Azure | Microsoft Docs
description: Az Azure-ban elolvashatja és konfigurálhatja a Microsoft Intune a Windows Holographic for Business-eszközökre vonatkozó eszközkorlátozási beállításait, így a regisztrációtörléssel, a földrajzi hellyel, a jelszavakkal, az áruházból telepített alkalmazásokkal, a Microsoft Edge sütijeivel és felugró ablakaival, a Windows Defenderrel, a kereséssel, a felhőtárhellyel, a Bluetooth-kapcsolattal, a rendszeridővel és a használati adatokkal kapcsolatos beállításokat.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e28a697b841d8b264a19d97059d272b7119bc7f4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493918"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Windows holografikus for Business-eszköz beállításai az Intune-t használó szolgáltatások engedélyezéséhez vagy korlátozásához

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ez a cikk felsorolja és ismerteti a Windows holografikus for Business-eszközök, például a Microsoft Hololens által szabályozható beállítások különböző beállításait. A mobileszköz-kezelési (MDM) megoldás részeként ezekkel a beállításokkal engedélyezheti vagy letilthatja a szolgáltatásokat, vezérelheti a biztonságot és egyebeket.

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Általános

- **Regisztráció manuális**törlése: lehetővé teszi a felhasználó számára a munkahelyi fiók manuális törlését az eszközről.
- **Cortana**: engedélyezheti vagy letilthatja a Cortana hangsegédet.
- **Térinformatikai**: Megadja, hogy az eszköz használhat-e Location Services-információkat.

## <a name="password"></a>Jelszó

- **Password (jelszó**): megköveteli a végfelhasználótól, hogy jelszót adjon meg az eszköz eléréséhez.
- **Jelszó megkövetelése, ha az eszköz visszatér az inaktív állapotból**: Megadja, hogy a felhasználónak meg kell adnia egy jelszót az eszköz zárolásának feloldásához.

## <a name="app-store"></a>Alkalmazásáruház

- **Áruházból származó alkalmazások automatikus frissítése**: lehetővé teszi, hogy a Microsoft Store telepített alkalmazások automatikusan frissüljenek.
- **Megbízható alkalmazás telepítése**: lehetővé teszi, hogy a megbízható tanúsítvánnyal aláírt alkalmazások közvetlenül telepített legyenek.
- **Fejlesztői zárolás feloldása**: engedélyezi a Windows fejlesztői beállításait, például lehetővé teszi a közvetlenül telepített alkalmazások módosítását a végfelhasználók számára.

## <a name="microsoft-edge-browser"></a>Microsoft Edge böngésző

- **Cookie-k**: lehetővé teszi, hogy a böngésző internetes cookie-kat mentsen az eszközre.
- **Előugró**ablakok: blokkolja az előugró ablakokat a böngészőben (csak a Windows 10 asztali verzióra vonatkozik).
- **Keresési javaslatok**: lehetővé teszi, hogy a keresőmotor a keresési kifejezések beírásakor javaslatot tegyen a webhelyekre.
- **Password Manager**: engedélyezheti vagy letilthatja a Microsoft Edge Password Manager szolgáltatást.
- Nem **nyomon követett fejlécek küldése**: a Microsoft Edge böngészőt úgy konfigurálja, hogy ne kövesse nyomon a fejléceket a felhasználók által felkeresett webhelyeken.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen a Microsoft Edge**-hez: a Microsoft Edge SmartScreen engedélyezése a hely-és fájlletöltés eléréséhez.

## <a name="search"></a>Keresés

- **Helyadatok kereséshez** – Annak megadása, hogy a keresési funkció használhatja-e a helyadatokat. információ

## <a name="cloud-and-storage"></a>Felhő és tárolás

- **Microsoft-fiók**: lehetővé teszi, hogy a felhasználó egy Microsoft-fiók társítson az eszközhöz.

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

- **Bluetooth**: azt szabályozza, hogy a felhasználó engedélyezheti és konfigurálhatja a Bluetooth-t az eszközön.
- **Bluetooth-észlelés**: lehetővé teszi, hogy az eszközt más Bluetooth-kompatibilis eszközök is felderítsék.
- **Bluetooth-hirdetés**: lehetővé teszi, hogy az eszköz hirdetéseket kapjon Bluetooth-kapcsolaton keresztül.

## <a name="control-panel-and-settings"></a>Vezérlőpult és Gépház

- **Rendszeridő módosítása**: megakadályozza, hogy a végfelhasználó megváltoztassa az eszköz dátumát és időpontját.

## <a name="kiosk---obsolete"></a>Kioszkmód – elavult

Ezek a beállítások csak olvashatók, és nem módosíthatók. A kioszkmód konfigurálásáról a [Kioszkbeállítások](kiosk-settings-holographic.md) című cikkből tájékozódhat.

A kioszkeszközök jellemzően egy adott alkalmazást futtatnak. A rendszer a felhasználóknak csak a kioszkalkalmazáshoz ad hozzáférést, és meggátolja az eszköz más funkcióinak és szolgáltatásainak elérését.

- Teljes **képernyős mód**: a szabályzat által támogatott kioszk mód típusát azonosítja. A lehetőségek a következők:

  - **Nincs konfigurálva** (alapértelmezés): A szabályzat nem engedélyezi a teljes képernyős módot. 
  - **Egyalkalmazásos kioszk**: a profil lehetővé teszi, hogy az eszköz csak egy alkalmazást futtasson. Amikor a felhasználó bejelentkezik, elindul az adott alkalmazás. Ez a mód emellett meggátolja a felhasználót abban, hogy új alkalmazásokat nyisson meg vagy másik futó alkalmazásra váltson.
  - **Többalkalmazásos kioszk**: a profil lehetővé teszi, hogy az eszköz több alkalmazást futtasson. Csak a hozzáadott alkalmazások lesznek elérhetők a felhasználónak. A többalkalmazásos kioszk (vagy fix célú eszköz) előnye az, hogy egy olyan, könnyen érthető környezetet nyújt a felhasználónak, amelyben csak a szükséges alkalmazások érhetőek el. Azokat az alkalmazásokat pedig, amelyekre nincsen szükség, elrejti a rendszer. 
  
    Amikor egy többalkalmazásos kioszkhoz alkalmazásokat ad hozzá, egy fájlt is meg kell adnia a Start menü elrendezéséhez. A [Start menü elrendezési fájlját](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others) bemutató cikk tartalmaz egy minta XML-fájlt is, amelyet használhat az Intune-ban. 

### <a name="single-app-kiosks"></a>Egyalkalmazásos kioszk

Adja meg a következő beállításokat:

- **Felhasználói fiók**: adja meg a kioszk alkalmazáshoz társított helyi (eszköz) felhasználói fiókot vagy az Azure ad-fiókhoz tartozó bejelentkezési azonosítót. Azure AD-tartományhoz csatlakozó fiókot a következő formában tud megadni: `domain\username@tenant.org`. 

    Nyilvános környezetben működő, automatikus bejelentkezésű kioszkeszköz esetében ajánlott a legalacsonyabb szintű hozzáféréssel rendelkező felhasználótípust (például egyszerű helyi felhasználó fiókot) választania. Ha Azure Active Directory- (AD-) fiókot kíván konfigurálni a kioszkmódhoz, használja az `AzureAD\user@contoso.com` formátumot.

- **Alkalmazás felhasználói modell azonosítója (AUMID)** : adja meg a KIOSZK alkalmazás AUMID. További információkat a [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Telepített alkalmazás alkalmazásfelhasználói modellben használt azonosítójának megkeresése) című témakörben találhat.

## <a name="reporting-and-telemetry"></a>Jelentéskészítés és telemetria

- **Használati adatok megosztása**: válassza ki a diagnosztikai adatok beküldésének szintjét.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
