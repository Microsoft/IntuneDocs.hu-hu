---
title: Mit jelent az alkalmazáskezelés a Microsoft Intune-ban?
titleSuffix: ''
description: Ismerkedjen meg az ügyfélalkalmazások felügyeleti képességeivel Microsoft Intune platformon.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/05/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c7378540d1ec9e19db57baae21c999c80b4d1d9
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856227"
---
# <a name="what-is-microsoft-intune-app-management"></a>A Microsoft Intune-alkalmazásfelügyelet ismertetése


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A rendszergazdák a Microsoft Intune használatával kezelhetik a cég által használt ügyfélalkalmazásokat. Ez a funkció az eszközkezelési és adatvédelmi funkciókat egészíti ki. A rendszergazdák egyik elsődleges feladata annak biztosítása, hogy a végfelhasználók hozzáférjenek a munkájukhoz szükséges alkalmazásokhoz. Ez a célkitűzés kihívást jelenthet, mivel:
- Sokféle eszközplatformot és alkalmazástípust kell kezelnie.
- Előfordulhat, hogy a vállalati eszközökön és a felhasználók saját eszközein található alkalmazásokat egyaránt felügyelnie kell.
- Folyamatosan gondoskodnia kell a hálózat és az adatok biztonságáról.

Emellett előfordulhat, hogy az Intune-ban nem regisztrált eszközökön található alkalmazásokat is szeretne hozzárendelni és felügyelni.

## <a name="mobile-application-management-mam-basics"></a>A Mobile Application Management (MAM) alapjai

Az [Intune mobilalkalmazás-kezelés](app-lifecycle.md) olyan Intune-beli felügyeleti összetevők csoportja, amelyek lehetővé teszik mobilalkalmazások közzétételét és leküldését a felhasználók részére, valamint azok konfigurálását, védelmét, figyelését és frissítését.

A MAM lehetővé teszi, hogy egy alkalmazáson belül kezelje és védje a szervezet adatait. Ha a **MAM regisztráció nélkül** (MAM-We) dolgozik, a bizalmas adatokat tartalmazó munkahelyi vagy iskolai alkalmazások szinte bármilyen [eszközön](app-management.md#app-management-capabilities-by-platform)kezelhetők, beleértve a **saját** eszközökön (BYOD) lévő személyes eszközöket is. Több irodai alkalmazás is felügyelhető az Intune MAM-mel, például a Microsoft Office-alkalmazások. Tekintse meg a nyilvános használatra elérhető [Microsoft Intune védett alkalmazások](apps-supported-intune-apps.md) hivatalos listáját.

Az Intune MAM két konfigurációt támogat:
- **Intune MDM és MAM:** A rendszergazda csak az Intune mobileszköz-kezelésben (MDM) regisztrált eszközökön felügyelheti a MAM- és alkalmazásvédelmi szabályzatokat használó alkalmazásokat. Az MDM-et és MAM-ot használó alkalmazások felügyeletéhez a https://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt.
- **MAM eszközregisztráció nélkül:** az eszközregisztráció nélküli MAM (MAM-WE) révén a rendszergazda felügyelheti az Intune MDM-ben nem regisztrált eszközökön található, MAM- és alkalmazásvédelmi szabályzatot használó alkalmazásokat. Ez azt jelenti, hogy az Intune csak külső EMM-szolgáltatóknál regisztrált eszközökön felügyelheti az alkalmazásokat. Az MAM-WE-t használó alkalmazások felügyeletéhez a https://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt. Emellett az Intune-nal felügyelheti az alkalmazásokat olyan eszközökön, amelyek harmadik féltől származó nagyvállalati mobilitási felügyeleti (EMM) rendszerben vannak regisztrálva, illetve nincsenek regisztrálva egyetlen mobileszköz-kezelési rendszerben sem. A BYOD és a Microsoft EMS-vel kapcsolatos további információkért lásd: [technológiai döntések a BYOD engedélyezéséhez Microsoft Enterprise Mobility + Security (EMS) segítségével](../fundamentals/byod-technology-decisions.md).

## <a name="app-management-capabilities-by-platform"></a>Alkalmazás-felügyeleti szolgáltatások platform szerint

Az Intune számos szolgáltatással segít a szükséges alkalmazások üzembe helyezésében azokon az eszközökön, amelyeken futtatni kívánják azokat. Az alábbi táblázat az alkalmazáskezelési lehetőségeket foglalja össze.

|  | Android/Android Enterprise | iOS/iPadOS | macOS | Windows 10 | WVPN-profilokdows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Alkalmazások hozzáadása és hozzárendelése eszközökhöz és felhasználókhoz | Igen | Igen | Igen | Igen | Igen |
| Alkalmazások hozzárendelése az Intune-ban nem regisztrált eszközökhöz | Igen | Igen | Nem | Nem | Nem |
| Az alkalmazások indítási viselkedését vezérlő alkalmazáskonfigurációs szabályzatok használata | Igen | Igen | Nem | Nem | Nem |
| Mobilalkalmazás-kiépítési szabályzatok használata a lejárt alkalmazások megújítására | Nem | Igen | Nem | Nem | Nem |
| Az alkalmazásokban található vállalati adatok védelme alkalmazásvédelmi szabályzatokkal | Igen | Igen | Nem | Nem <sup>1</sup> | Nem |
| Csak a vállalati adatok eltávolítása egy telepített alkalmazásból (alkalmazások szelektív törlése) | Igen | Igen | Nem | Igen | Igen |
| Az alkalmazás-hozzárendelések monitorozása | Igen | Igen | Igen | Igen | Igen |
| Egy alkalmazás-áruházból mennyiségi licencszerződés keretében vásárolt alkalmazások hozzárendelése és nyomon követése | Nem | Nem | Nem | Igen | Nem |
| Alkalmazások kötelező telepítése eszközökön (kötelező) <sup>2</sup> | Igen | Igen | Igen | Igen | Igen |
| Opcionális telepítés az eszközökön a Céges portálról (elérhető telepítés) | Igen <sup>3</sup> | Igen | Igen | Igen | Igen |
| Alkalmazás telepítési hivatkozása az interneten (webes hivatkozás) | Igen <sup>4</sup> | Igen | Igen | Igen | Igen |
| Belső fejlesztésű (üzletági) alkalmazások | Igen | Igen | Igen | Igen | Nem |
| Áruházbeli alkalmazások | Igen | Igen | Nem | Igen | Igen |
| Alkalmazások frissítése | Igen | Igen | Nem | Igen | Igen |

<sup>1</sup> Vagye fontolóra a [Windows Információvédelem](../protect/windows-information-protection-configure.md) használatát a Windows 10 rendszerű eszközökön futó alkalmazások védelmére.<br>
<sup>2</sup> Csak az Intune által kezelt eszközökre vonatkozik.<br>
<sup>3</sup> az Intune támogatja a felügyelt Google Play áruházból származó, androidos vállalati eszközökön elérhető alkalmazásokat.<br>
<sup>4</sup> az Intune nem biztosít parancsikont webes hivatkozásként a szabványos Android Enterprise-eszközökön. A Weblink-támogatást azonban a [többalkalmazásos dedikált Android Enterprise-eszközökhöz](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)is biztosítjuk. 


## <a name="get-started"></a>Első lépések

Az alkalmazásokkal kapcsolatos legtöbb információt megtalálhatja az **alkalmazások** munkaterhelésében, amelyet a következő módon érhet el:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza az **alkalmazások**lehetőséget.

    ![Az alkalmazások munkaterhelése panel](./media/app-management/apps-workload.png)

Az alkalmazások munkaterhelése az alkalmazás általános információinak és funkcióinak elérésére mutató hivatkozásokat biztosít. 

Az alkalmazás munkaterhelésének navigációs menüjének felső részén az alkalmazás általánosan használt adatai láthatók:
- **Áttekintés**: ezzel a beállítással megtekintheti a bérlő nevét, a Mdm-szolgáltatót, a bérlő helyét, a fiók állapotát, az alkalmazás telepítési állapotát és az alkalmazás védelmi szabályzatának állapotát.
- **Minden alkalmazás**: válassza ezt a lehetőséget az összes elérhető alkalmazás listájának megjelenítéséhez. Ezen a lapon további alkalmazásokat is hozzáadhat. Emellett megtekintheti az egyes alkalmazások állapotát, valamint azt is, hogy minden alkalmazás hozzá van-e rendelve. További információ: [Alkalmazások hozzáadása](apps-add.md) és [alkalmazások kiosztása](apps-deploy.md).
- **Alkalmazások figyelése**
    - **Alkalmazáslicencek**: Az alkalmazás-áruházakból vásárolt mennyiségi licencszerződéses alkalmazások megtekintése, hozzárendelése és figyelése. További információkért lásd: [iOS mennyiségi programban vásárolt program (VPP) alkalmazások](vpp-apps-ios.md) és [Microsoft Store az üzleti mennyiségi programban vásárolt alkalmazások számára](windows-store-for-business.md).
    - **Felderített alkalmazások**: megtekintheti az Intune által hozzárendelt vagy az eszközre telepített alkalmazásokat. További információ: az [Intune által felderített alkalmazások](app-discovered-apps.md).
    - **Alkalmazás telepítési állapota**: megtekintheti az Ön által létrehozott alkalmazás-hozzárendelés állapotát. További információk: [Alkalmazásadatok és -hozzárendelések figyelése a Microsoft Intune-ban](apps-monitor.md#device-and-user-status-graphs).
    - **Alkalmazásvédelem állapota**: A kiválasztott felhasználó egy alkalmazásvédelmi szabályzatának állapotát jeleníti meg.
- **Platform szerint**: válassza ki ezeket a platformokat az elérhető alkalmazások platformon való megtekintéséhez.
    - Windows
    - iOS
    - macOS
    - Android:
- **Házirend**:
    - **Alkalmazásvédelmi szabályzatok**: Ezt a lehetőséget választva beállításokat társíthat egy alkalmazáshoz és hozzájárulhat az általa használt céges adatok védelméhez. Korlátozhatja például egy alkalmazás más alkalmazásokkal való kommunikációját, vagy előírhatja PIN-kód megadását a felhasználónak egy céges alkalmazás eléréséhez. További információ: alkalmazás- [védelmi szabályzatok](app-protection-policies.md).
    - **Alkalmazás-konfigurációs szabályzatok**: Ezt a lehetőséget választva megadhatja azokat a beállításokat, amelyekre szükség lehet, amikor egy felhasználó egy alkalmazást futtat. További információ: alkalmazás- [konfigurációs házirendek](app-configuration-policies-use-ios.md), [iOS-alkalmazás konfigurációs házirendjei](app-configuration-policies-use-ios.md)és [Android-alkalmazás konfigurációs szabályzatai](app-configuration-policies-overview.md).
    - **iOS-alkalmazáskiépítési profilok**: Az iOS-alkalmazások tartalmaznak egy kiépítési profilt és kódot, tanúsítvánnyal aláírva. Ha a tanúsítvány lejár, az alkalmazás a továbbiakban nem futtatható. Az Intune biztosítja az eszközöket, amelyek segítségével proaktív módon rendelhet hozzá új kiépítési profilt azokhoz az eszközökhöz, amelyeken hamarosan lejárnak az alkalmazások. További információ: iOS- [alkalmazások létesítési profiljai](app-provisioning-profile-ios.md).
    - **S módú kiegészítő szabályzatok**: ezzel a beállítással engedélyezheti, hogy további alkalmazások fussanak a felügyelt S módú eszközökön. További információ: [S Mode kiegészítő szabályzatok](~/apps/apps-win32-s-mode.md).
    - **Házirendek**: válassza ezt a lehetőséget, ha az alkalmazások, házirendek és egyéb létrehozott felügyeleti objektumok hozzárendelhető gyűjteményét szeretné létrehozni. További információ: házirend- [készletek](~/fundamentals/policy-sets.md).
- **Egyéb**:   
    - **Alkalmazások szelektív törlése**: Ezzel a lehetőséggel csak a céges adatokat törli a kijelölt felhasználók eszközeiről. További információ: [alkalmazás szelektív törlése](apps-selective-wipe.md).
    - **Alkalmazáskategóriák**: Alkalmazáskategória-neveket adhat hozzá, rögzíthet és törölhet.
    - **E-könyvek**: egyes alkalmazás-áruházak lehetővé teszi, hogy több licencet is vásároljon a vállalatnál használni kívánt alkalmazásokhoz vagy könyvekhez. További információ: [Mennyiségi programban vásárolt alkalmazások és könyvek kezelése a Microsoft Intune-nal](~/apps/vpp-apps.md).
- **Súgó és támogatás**: Hibaelhárítási információkat kereshet, támogatást kérhet, és megtekintheti az Intune állapotát. További információ: [hibaelhárítási problémák](../fundamentals/help-desk-operators.md).

## <a name="additional-information"></a>További információ
A konzolon a következő elemek biztosítják az alkalmazással kapcsolatos funkciókat:
- **Microsoft Store Vállalatoknak áruház** – A Microsoft Store Vállalatoknak áruházba történő integráció beállítása. Ezt követően az Intune-ban szinkronizálhatja és kioszthatja a megvásárolt alkalmazásokat, továbbá nyilvántarthatja a licenchasználatot. További információ: [Microsoft Store for Business mennyiségi licencszerződés keretében vásárolt alkalmazások](windows-store-for-business.md).
- **Windowsos vállalati tanúsítvány**: Egy üzletági alkalmazások felügyelt Windows-eszközökre való terjesztésére szolgáló kódaláíró tanúsítvány alkalmazása, vagy az állapota megtekintése.
- **Windowsos Symantec-tanúsítvány**: Egy XAP és WP8.x appx-fájlok Windows 10 Mobile-eszközökre való terjesztéséhez szükséges Symantec kódaláíró tanúsítvány alkalmazása, vagy az állapota megtekintése.
- **Windowsos közvetlen telepítési kulcsok**: Egy windowsos közvetlen telepítési kulcs hozzáadása, mellyel közvetlenül az eszközre telepíthet egy alkalmazást, ahelyett hogy közzétenné azt a Windows Áruházban, majd onnan telepítené. További információ: [Windows-alkalmazás betöltése](app-sideload-windows.md).
- **Apple VPP-tokenek**: az iOS/IPadOS Volume Purchase program-(VPP-) licencek alkalmazása és megtekintése. További információ: [iOS/iPadOS mennyiségi licencszerződés keretében vásárolt alkalmazások](vpp-apps-ios.md).
- **Felügyelt Google Play**: a Google Play a Google nagyvállalati alkalmazás-áruházból és az Android Enterprise-alapú alkalmazások egyetlen forrása. További információ: [felügyelt Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune](~/apps/apps-add-android-for-work.md)-nal.
- **Védjegyezés és testreszabás**: testreszabhatja a céges portál, hogy a vállalat arculatát adja. További információ: [céges portál konfiguráció](company-portal-app.md).

## <a name="next-steps"></a>További lépések

- [Alkalmazás hozzáadása a Microsoft Intune-hoz](apps-add.md)
