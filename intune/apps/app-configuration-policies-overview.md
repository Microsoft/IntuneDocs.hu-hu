---
title: Alkalmazáskonfigurációs szabályzatok a Microsoft Intune-hoz
titleSuffix: ''
description: Ismertető a Microsoft Intune alkalmazáskonfigurációs szabályzatainak iOS- vagy Android-eszközön való használatához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 42d17c15a2a32f828c5715dfad51f34c5e531e76
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507548"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Alkalmazáskonfigurációs szabályzatok a Microsoft Intune-hoz

Az alkalmazás-konfigurációs házirendek segíthetnek az alkalmazások telepítésével kapcsolatos problémák elhárításában azáltal, hogy a konfigurációs beállításokat egy olyan házirendhez rendeli hozzá, amely hozzá van rendelve a végfelhasználók számára az alkalmazás futtatása előtt. Ezt követően a rendszer automatikusan megadja a beállításokat, amikor az alkalmazás konfigurálva van a végfelhasználói eszközön, és a végfelhasználóknak nem kell végrehajtaniuk a műveletet. A konfigurációs beállítások minden alkalmazás esetében egyediek. 

Alkalmazás-konfigurációs szabályzatokat hozhat létre és használhat az iOS-és Android-alkalmazások konfigurációs beállításainak megadásához. Ezek a konfigurációs beállítások lehetővé teszik, hogy az alkalmazások testreszabhatók legyenek az alkalmazások konfigurációjának és felügyeletének használatával. A konfigurációs házirend beállításai akkor használatosak, amikor az alkalmazás ellenőrzi ezeket a beállításokat, általában az alkalmazás első futtatásakor. 

Az alkalmazás konfigurációs beállításai például a következők bármelyikének megadását tehetik szükségessé:

- Egyéni portszám
- Nyelvi beállítások
- Biztonsági beállítások
- Márkajelzési beállítások, például a vállalat logója

Ha a végfelhasználók ezeket a beállításokat adtak meg, azok helytelenül is megadhatók. Az alkalmazás-konfigurációs házirendek segítséget nyújthatnak a vállalaton belüli konzisztencia biztosításához, és csökkentik az ügyfélszolgálati hívásokat a végfelhasználók számára a beállítások konfigurálásához. Az alkalmazás-konfigurációs szabályzatok segítségével az új alkalmazások bevezetését egyszerűbbé és gyorsabbá teheti.

Az elérhető konfigurációs paramétereket végül az alkalmazás fejlesztői határozzák meg. Tekintse át az alkalmazás gyártójától származó dokumentációt, és ellenőrizze, hogy az alkalmazás támogatja-e a konfigurációt, és hogy milyen konfigurációk érhetők el. Egyes alkalmazások esetében az Intune feltölti az elérhető konfigurációs beállításokat. 

> [!NOTE]
> A felügyelt Google Play Áruház a konfigurációt támogató alkalmazások a következőképpen lesznek megjelölve:
> 
> ![Egy konfigurált alkalmazás képernyőképe](./media/app-configuration-policies-overview/configured-app.png)
>
> Az Android-eszközök regisztrálási típusaként csak a [felügyelt Google Play áruházból](https://play.google.com/work)származó alkalmazások jelennek meg, nem a [Google Play áruházból](https://play.google.com/store/apps), a felügyelt eszközök használatakor. Felügyelt Google Play Áruház, amelyek az Android for Work (AfW) és az Android Enterprise rendszerhez is ismertek, a munkahelyi profilban található alkalmazások, amelyek az alkalmazás konfigurációját támogató alkalmazásokat tartalmazzák.

Alkalmazás-konfigurációs házirendet a végfelhasználók és az eszközök egy csoportjára is hozzárendelhet a [belefoglalási és kizárási hozzárendelések](apps-inc-exl-assignments.md)együttes használatával. Miután hozzáadta az alkalmazáskonfigurálási szabályzatot, beállíthatja az alkalmazáskonfigurálási szabályzat hozzárendeléseit. A szabályzat hozzárendeléseinek beállításakor kiválaszthatja, hogy kivonja és kizárja azokat a végfelhasználói [csoportokat](../fundamentals/groups-add.md) , amelyekre a szabályzat vonatkozik. Amikor felvesz egy vagy több csoportot, kiválaszthat bizonyos csoportokat, vagy választhat beépített csoportokat. Beépített csoportok a következők: **Minden felhasználó**, **Minden eszköz**, és **Minden felhasználó és minden eszköz**.

Az alkalmazás-konfigurációs szabályzatok Intune-nal való használatának két lehetősége van:
- **Felügyelt eszközök** – Az eszköz mobileszköz-kezelő (MDM) szolgáltatója az Intune. Az alkalmazást úgy kell tervezni, hogy támogassa az alkalmazás konfigurációját.
- **Felügyelt alkalmazások** – az INTUNE app SDK integrálására kifejlesztett alkalmazás. Ez az úgynevezett Mobile Application Management regisztráció nélkül ([MAM-We](app-management.md#mobile-application-management-mam-basics)). Emellett az Intune app SDK megvalósításához és támogatásához is becsomagolhat egy alkalmazást. Az alkalmazások csomagolásával kapcsolatos további információkért lásd: [üzletági alkalmazások előkészítése az App Protection-szabályzatokhoz](../developer/apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Az Intune által felügyelt alkalmazások az Intune-alkalmazás konfigurációs házirendjének állapotaként 30 percet, a Intune App Protection szabályzattal együtt történő üzembe helyezéskor lesznek bejelentkezni. Ha nincs Intune App Protection házirend társítva a felhasználóhoz, akkor az Intune alkalmazás-konfigurációs házirend beadási időköze 720 percre van állítva.

## <a name="apps-that-support-app-configuration"></a>Az alkalmazáskonfigurációt támogató alkalmazások

### <a name="managed-devices"></a>Felügyelt eszközök
Alkalmazás-konfigurációs házirendeket használhat az azt támogató alkalmazásokhoz. Az alkalmazás-konfiguráció Intune-ban való támogatásához az alkalmazásokat az operációs rendszer által meghatározott alkalmazások konfigurációjának támogatásához kell írni. Az alkalmazás gyártójától tájékozódhat az általa támogatott alkalmazás-konfigurációs kulcsokról.

### <a name="managed-apps"></a>Felügyelt alkalmazások
Előkészítheti az üzletági alkalmazásokat az [Intune app SDK](../developer/app-sdk.md) -nak az alkalmazásba való beépítésével, vagy az alkalmazásnak az [Intune alkalmazás-burkoló eszköz](../developer/apps-prepare-mobile-application-management.md)használatával történő becsomagolásával. Az Intune app SDK arra törekszik, hogy minimálisra csökkentse az alkalmazás fejlesztője által igényelt kód módosításának mértékét. További információ: [Az Intune App SDK áttekintése](../developer/app-sdk.md). Az Intune app SDK és az Intune alkalmazás-burkoló eszköz közötti összehasonlításért lásd: [üzletági alkalmazások előkészítése az App Protection-szabályzatokhoz](../developer/apps-prepare-mobile-application-management.md#feature-comparison).

A **felügyelt alkalmazások** kiválasztása az **eszköz beléptetési típusaként** kifejezetten az Intune konfigurációs házirendjei által konfigurált, az Eszközkezelőben nem regisztrált eszközökre vonatkozik, míg a **felügyelt eszközök** az üzembe helyezett alkalmazásokra vonatkoznak. az MDM-csatornán keresztül, így az Intune kezeli. Válassza ki a megfelelő választást a leírások alapján. 

![Eszköz beléptetésének típusa](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> A többszörös identitású alkalmazások, például a Microsoft Outlook esetében a felhasználói beállítások is megtekinthetők. A célzott beérkezett fájlok például figyelembe veszik a felhasználói beállításokat, és nem változtatják meg a konfigurációt. Más paraméterek használatával megadhatja, hogy a felhasználók módosíthatják-e a beállítást. További információ: az [Outlook telepítése iOS-és Android-alkalmazásokhoz konfigurációs beállítások](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Az alkalmazott alkalmazás-konfigurációs házirend ellenőrzése

Az alkalmazás konfigurációs szabályzatát az alábbi három módszer használatával ellenőrizheti:

   1. Látható az eszközön. A célként megadott alkalmazás az alkalmazás-konfigurációs házirendben alkalmazott viselkedést mutatja?
   2. Diagnosztikai naplókon keresztül (lásd alább a diagnosztikai naplók szakaszt).
   3. Az Intune-portálon. A szabályzat **figyelő** szakasza megadhatja a megfelelő állapotot:

      ![Az eszköz telepítési állapotának első képernyőképe](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![Az eszköz telepítési állapotának második képernyőképe](./media/app-configuration-policies-overview/device-install-status-2.png)

      Emellett az **Intune** -> **eszköz** -> **minden eszköz** a képernyő bal oldalán, az **alkalmazás konfigurációja** beállítás megjeleníti az összes hozzárendelt szabályzatot és azok állapotát:

      ![Az alkalmazás konfigurációjának képernyőképe](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>Diagnosztikai naplók

### <a name="ios-configuration-on-unmanaged-devices"></a>iOS-konfiguráció a nem felügyelt eszközökön

Az iOS-konfigurációt az **Intune diagnosztikai naplójában** ellenőrizheti a felügyelt alkalmazások konfigurációjának nem felügyelt eszközein.

1. Ha még nincs telepítve az eszközön, töltse le és telepítse a **Intune Managed Browsert** az App Store áruházból. További információ: [Microsoft Intune védett alkalmazások](apps-supported-intune-apps.md).
2. Indítsa el a **Intune Managed Browser** , majd a navigációs sávon válassza a  > **intunehelp** **névjegye**elemet.
3. Kattintson az első **lépések**elemre.
4. Kattintson a **megosztási naplók**elemre.
5. Az Ön által választott levelezési alkalmazás használatával elküldheti a naplót saját magára, hogy megtekinthető legyen a SZÁMÍTÓGÉPén. 
6. Tekintse át a **IntuneMAMDiagnostics. txt** fájlt a szövegfájl-megjelenítőben.
7. Keresés a következőre: `ApplicationConfiguration` Az eredmények a következőhöz hasonlóan fognak kinézni:

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

Az alkalmazás konfigurációjának részleteinek meg kell egyezniük a bérlőhöz konfigurált alkalmazás-konfigurációs házirendekkel. 

![Megcélzó alkalmazás konfigurációja](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>iOS-konfiguráció a felügyelt eszközökön

Az iOS-konfigurációt érvényesítheti az **Intune diagnosztikai naplóval** a felügyelt eszközökön a felügyelt alkalmazások konfigurálásához.

1. Ha még nincs telepítve az eszközön, töltse le és telepítse a **Intune Managed Browsert** az App Store áruházból. További információ: [Microsoft Intune védett alkalmazások](apps-supported-intune-apps.md).
2. Indítsa el a **Intune Managed Browser** , majd a navigációs sávon válassza a  > **intunehelp** **névjegye**elemet.
3. Kattintson az első **lépések**elemre.
4. Kattintson a **megosztási naplók**elemre.
5. Az Ön által választott levelezési alkalmazás használatával elküldheti a naplót saját magára, hogy megtekinthető legyen a SZÁMÍTÓGÉPén. 
6. Tekintse át a **IntuneMAMDiagnostics. txt** fájlt a szövegfájl-megjelenítőben.
7. Keresés a következőre: `AppConfig` Az eredményeknek meg kell egyezniük a bérlőhöz konfigurált alkalmazás-konfigurációs házirendekkel.

### <a name="android-configuration-on-managed-devices"></a>Android-konfiguráció a felügyelt eszközökön

Az iOS-konfigurációt érvényesítheti az **Intune diagnosztikai naplóval** a felügyelt eszközökön a felügyelt alkalmazások konfigurálásához.

Ha androidos eszközről szeretne naplókat gyűjteni, Önnek vagy a felhasználónak USB-kapcsolaton keresztül le kell töltenie a naplókat az eszközről (vagy az eszközön található **fájlkezelővel** egyenértékű). A lépések a következők:

1. Csatlakoztassa az Android-eszközt a számítógéphez az USB-kábellel.
2. A számítógépen keresse meg az eszköz nevével megegyező nevű könyvtárt. Ebben a könyvtárban keresse meg a `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal` értéket.
3. A `com.microsoft.windowsintune.companyportal` mappában Nyissa meg a Files mappát, és nyissa meg a `OMADMLog_0` fájlt.
3. Keresse meg a `AppConfigHelper` értéket az alkalmazás-konfigurációval kapcsolatos üzenetek kereséséhez. Az eredmények a következő adatblokkhoz hasonlóan jelennek meg:

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>Graph API-támogatás az alkalmazáskonfigurációhoz

Az alkalmazások konfigurációs feladatainak elvégzéséhez Graph API is használhatja. További információk: [Graph API-kézikönyv ‒ MAM célzott konfiguráció](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="using-logs-to-show-a-configuration-parameter"></a>Naplók használata konfigurációs paraméterek megjelenítéséhez
Ha a naplók egy olyan konfigurációs paramétert mutatnak be, amely úgy van megerősítve, hogy alkalmazásra kerül, de úgy tűnik, hogy nem működik, az alkalmazás fejlesztője a konfiguráció megvalósításával kapcsolatos problémát okozhat. Ha először éri el a fejlesztőket, vagy megtekinti a tudásbázist, akkor egy támogatási hívást is megtakaríthat a Microsofttal. Ha probléma merül fel a konfigurációnak az alkalmazáson belüli kezelésével kapcsolatban, az alkalmazás egy későbbi frissített verziójában kellene foglalkoznia.

## <a name="next-steps"></a>További lépések

### <a name="managed-devices"></a>Felügyelt eszközök

- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt az iOS-eszközeivel.  Lásd: [alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt iOS-eszközökhöz](app-configuration-policies-use-ios.md).
- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt az Android-eszközeivel.  Lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása kezelt Android-eszközökhöz](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Felügyelt alkalmazások

- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt a felügyelt alkalmazásokkal. Lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül](app-configuration-policies-managed-app.md).
