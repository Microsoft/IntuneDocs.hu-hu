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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c0cbc2c7334675e91450b9c2d7129a098498d978
ms.sourcegitcommit: 27e63a96d15bc4062af68c2764905631bd928e7b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71061596"
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
> ![Egy konfigurált alkalmazás képernyőképe](./media/app-configuration-policy-overview/configured-app.png)
>
> Az Android-eszközök regisztrálási típusaként csak a [felügyelt Google Play áruházból](https://play.google.com/work)származó alkalmazások jelennek meg, nem a [Google Play áruházból](https://play.google.com/store/apps), a felügyelt eszközök használatakor. Felügyelt Google Play Áruház, amelyek az Android for Work (AfW) és az Android Enterprise rendszerhez is ismertek, a munkahelyi profilban található alkalmazások, amelyek az alkalmazás konfigurációját támogató alkalmazásokat tartalmazzák.

Alkalmazás-konfigurációs házirendet a végfelhasználók és az eszközök egy csoportjára is hozzárendelhet a [belefoglalási és kizárási hozzárendelések](apps-inc-exl-assignments.md)együttes használatával. Miután hozzáadta az alkalmazáskonfigurálási szabályzatot, beállíthatja az alkalmazáskonfigurálási szabályzat hozzárendeléseit. A szabályzat hozzárendeléseinek beállításakor kiválaszthatja, hogy kivonja és kizárja azokat a végfelhasználói [csoportokat](groups-add.md) , amelyekre a szabályzat vonatkozik. Amikor felvesz egy vagy több csoportot, kiválaszthat bizonyos csoportokat, vagy választhat beépített csoportokat. Beépített csoportok a következők: **Minden felhasználó**, **Minden eszköz**, és **Minden felhasználó és minden eszköz**.

Az alkalmazás-konfigurációs szabályzatok Intune-nal való használatának két lehetősége van:
- **Felügyelt eszközök** – Az eszköz mobileszköz-kezelő (MDM) szolgáltatója az Intune. Az alkalmazást úgy kell tervezni, hogy támogassa az alkalmazás konfigurációját.
- **Felügyelt alkalmazások** – az INTUNE app SDK integrálására kifejlesztett alkalmazás. Ez az úgynevezett Mobile Application Management regisztráció nélkül ([MAM-We](app-management.md#mobile-application-management-mam-basics)). Emellett az Intune app SDK megvalósításához és támogatásához is becsomagolhat egy alkalmazást. Az alkalmazások csomagolásával kapcsolatos további információkért lásd: [üzletági alkalmazások előkészítése az App Protection-szabályzatokhoz](apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Az Intune által felügyelt alkalmazások az Intune-alkalmazás konfigurációs házirendjének állapotaként 30 percet, a Intune App Protection szabályzattal együtt történő üzembe helyezéskor lesznek bejelentkezni. Ha nincs Intune App Protection házirend társítva a felhasználóhoz, akkor az Intune alkalmazás-konfigurációs házirend beadási időköze 720 percre van állítva.

## <a name="apps-that-support-app-configuration"></a>Az alkalmazáskonfigurációt támogató alkalmazások

### <a name="managed-devices"></a>Felügyelt eszközök
Alkalmazás-konfigurációs házirendeket használhat az azt támogató alkalmazásokhoz. Az alkalmazás-konfiguráció Intune-ban való támogatásához az alkalmazásokat az operációs rendszer által meghatározott alkalmazások konfigurációjának támogatásához kell írni. Az alkalmazás gyártójától tájékozódhat az általa támogatott alkalmazás-konfigurációs kulcsokról.

### <a name="managed-apps"></a>Felügyelt alkalmazások
Előkészítheti az üzletági alkalmazásokat az [Intune app SDK](app-sdk.md) -nak az alkalmazásba való beépítésével, vagy az alkalmazásnak az [Intune alkalmazás-burkoló eszköz](apps-prepare-mobile-application-management.md)használatával történő becsomagolásával. Az Intune app SDK arra törekszik, hogy minimálisra csökkentse az alkalmazás fejlesztője által igényelt kód módosításának mértékét. További információ: [Az Intune App SDK áttekintése](app-sdk.md). Az Intune app SDK és az Intune alkalmazás-burkoló eszköz közötti összehasonlításért lásd: [üzletági alkalmazások előkészítése az App Protection-szabályzatokhoz](apps-prepare-mobile-application-management.md#feature-comparison).

A **felügyelt alkalmazások** kiválasztása az **eszköz beléptetési típusaként** kifejezetten az Intune konfigurációs házirendjei által konfigurált, az Eszközkezelőben nem regisztrált eszközökre vonatkozik, míg a **felügyelt eszközök** az üzembe helyezett alkalmazásokra vonatkoznak. az MDM-csatornán keresztül, így az Intune kezeli. Válassza ki a megfelelő választást a leírások alapján. 

![Eszköz beléptetésének típusa](./media/app-configuration-policy-overview/device-enrollment-type.png)

> [!NOTE]
> A többszörös identitású alkalmazások, például a Microsoft Outlook esetében a felhasználói beállítások is megtekinthetők. A célzott beérkezett fájlok például figyelembe veszik a felhasználói beállításokat, és nem változtatják meg a konfigurációt. Más paraméterek használatával megadhatja, hogy a felhasználók módosíthatják-e a beállítást. További információ: az [Outlook telepítése iOS-és Android-alkalmazásokhoz konfigurációs beállítások](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Az alkalmazott alkalmazás-konfigurációs házirend ellenőrzése

Az alkalmazás konfigurációs szabályzatát az alábbi három módszer használatával ellenőrizheti:

   1. Látható az eszközön. A célként megadott alkalmazás az alkalmazás-konfigurációs házirendben alkalmazott viselkedést mutatja?
   2. Diagnosztikai naplókon keresztül (lásd alább a diagnosztikai naplók szakaszt).
   3. Az Intune-portálon. A szabályzat **figyelő** szakasza megadhatja a megfelelő állapotot:

      ![Az eszköz telepítési állapotának első képernyőképe](./media/app-configuration-policy-overview/device-install-status-1.png)

      ![Az eszköz telepítési állapotának második képernyőképe](./media/app-configuration-policy-overview/device-install-status-2.png)

      Emellett az **Intune** -> -**eszközök** -> **minden eszköz** a képernyő bal oldalán az **alkalmazás konfigurációja** lehetőség megjeleníti az összes hozzárendelt szabályzatot és azok állapotát:

      ![Az alkalmazás konfigurációjának képernyőképe](./media/app-configuration-policy-overview/app-configuration.png)

## <a name="graph-api-support-for-app-configuration"></a>Graph API-támogatás az alkalmazáskonfigurációhoz

Az alkalmazások konfigurációs feladatainak elvégzéséhez Graph API is használhatja. További információk: [Graph API-kézikönyv ‒ MAM célzott konfiguráció](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="using-logs-to-show-a-configuration-parameter"></a>Naplók használata konfigurációs paraméterek megjelenítéséhez
Ha a naplók egy olyan konfigurációs paramétert mutatnak be, amely úgy van megerősítve, hogy alkalmazásra kerül, de úgy tűnik, hogy nem működik, az alkalmazás fejlesztője a konfiguráció megvalósításával kapcsolatos problémát okozhat. Ha először éri el a fejlesztőket, vagy megtekinti a tudásbázist, akkor egy támogatási hívást is megtakaríthat a Microsofttal. Ha probléma merül fel a konfigurációnak az alkalmazáson belüli kezelésével kapcsolatban, az alkalmazás egy későbbi frissített verziójában kellene foglalkoznia.

## <a name="next-steps"></a>További lépések

### <a name="managed-devices"></a>Felügyelt eszközök

- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt az iOS-eszközeivel.  Lásd: [alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt iOS](app-configuration-policies-use-ios.md)-eszközökhöz.
- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt az Android-eszközeivel.  Lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása kezelt Android-eszközökhöz](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Felügyelt alkalmazások

- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt a felügyelt alkalmazásokkal. Lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül](app-configuration-policies-managed-app.md).
