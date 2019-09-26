---
title: Mit jelent az alkalmazáskezelés a Microsoft Intune-ban?
titleSuffix: ''
description: Ismerkedjen meg az ügyfélalkalmazások felügyeleti képességeivel Microsoft Intune platformon.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 063e78fb716d27843ce017389da7a01f12fee70b
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "71303765"
---
# <a name="what-is-microsoft-intune-app-management"></a>A Microsoft Intune-alkalmazásfelügyelet ismertetése


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A rendszergazdák a Microsoft Intune használatával kezelhetik a cég által használt ügyfélalkalmazásokat. Ez a funkció az eszközkezelési és adatvédelmi funkciókat egészíti ki. A rendszergazdák egyik elsődleges feladata annak biztosítása, hogy a végfelhasználók hozzáférjenek a munkájukhoz szükséges alkalmazásokhoz. Ez a célkitűzés kihívást jelenthet, mivel:
- Sokféle eszközplatformot és alkalmazástípust kell kezelnie.
- Előfordulhat, hogy a vállalati eszközökön és a felhasználók saját eszközein található alkalmazásokat egyaránt felügyelnie kell.
- Folyamatosan gondoskodnia kell a hálózat és az adatok biztonságáról.

Emellett előfordulhat, hogy az Intune-ban nem regisztrált eszközökön található alkalmazásokat is szeretne hozzárendelni és felügyelni.

## <a name="mobile-application-management-mam-basics"></a>A Mobile Application Management (MAM) alapjai

Az [Intune mobilalkalmazás-kezelés](app-lifecycle.md) olyan Intune-beli felügyeleti összetevők csoportja, amelyek lehetővé teszik mobilalkalmazások közzétételét és leküldését a felhasználók részére, valamint azok konfigurálását, védelmét, figyelését és frissítését.

A MAM lehetővé teszi, hogy egy alkalmazáson belül kezelje és védje a szervezet adatait. Ha a **MAM regisztráció nélkül** (MAM-We) dolgozik, a bizalmas adatokat tartalmazó munkahelyi vagy iskolai alkalmazások szinte bármilyen [eszközön](app-management.md#app-management-capabilities-by-platform)kezelhetők, beleértve a **saját** eszközökön (BYOD) lévő személyes eszközöket is. Több irodai alkalmazás is felügyelhető az Intune MAM-mel, például a Microsoft Office-alkalmazások. Tekintse meg a nyilvános használatra elérhető [Microsoft Intune védett alkalmazások](apps-supported-intune-apps.md) hivatalos listáját.

Az Intune MAM két konfigurációt támogat:
- **INTUNE Mdm + MAM**: A rendszergazda csak az Intune mobileszköz-kezelésben (MDM) regisztrált eszközökön felügyelheti az MAM- és alkalmazásvédelmi szabályzatokat használó alkalmazásokat. Az MDM-et és MAM-ot használó alkalmazások felügyeletéhez a https://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt.
- **MAM eszközök regisztrációja nélkül**: A MAM eszközök regisztrációja nélkül, vagy MAM-WE lehetővé teszi a rendszergazdák számára, hogy az Intune MDM-ban nem regisztrált eszközökön a MAM-és az alkalmazás-védelmi szabályzatokat használják az alkalmazások felügyeletére. Ez azt jelenti, hogy az Intune csak külső EMM-szolgáltatóknál regisztrált eszközökön felügyelheti az alkalmazásokat. Az MAM-WE-t használó alkalmazások felügyeletéhez a https://portal.azure.com címen található Azure Portalon elérhető Intune-konzol használata javasolt. Emellett az Intune-nal felügyelheti az alkalmazásokat olyan eszközökön, amelyek harmadik féltől származó nagyvállalati mobilitási felügyeleti (EMM) rendszerben vannak regisztrálva, illetve nincsenek regisztrálva egyetlen mobileszköz-kezelési rendszerben sem. A BYOD és a Microsoft EMS-vel kapcsolatos további információkért lásd: [technológiai döntések a BYOD engedélyezéséhez Microsoft Enterprise Mobility + Security (EMS) segítségével](byod-technology-decisions.md).

## <a name="app-management-capabilities-by-platform"></a>Alkalmazás-felügyeleti szolgáltatások platform szerint

Az Intune számos szolgáltatással segít a szükséges alkalmazások üzembe helyezésében azokon az eszközökön, amelyeken futtatni kívánják azokat. Az alábbi táblázat az alkalmazáskezelési lehetőségeket foglalja össze.

|  | Android/Android Enterprise | iOS | macOS | Windows 10 | Windows Phone 8.1 |
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

<sup>1</sup> Vagye fontolóra a [Windows Információvédelem](windows-information-protection-configure.md) használatát a Windows 10 rendszerű eszközökön futó alkalmazások védelmére.<br>
<sup>2</sup> Csak az Intune által kezelt eszközökre vonatkozik.<br>
<sup>3</sup> az Intune támogatja a felügyelt Google Play áruházból származó, androidos vállalati eszközökön elérhető alkalmazásokat.<br>
<sup>4</sup> az Intune nem biztosít parancsikont webes hivatkozásként a szabványos Android Enterprise-eszközökön. A Weblink-támogatást azonban a [többalkalmazásos dedikált Android Enterprise-eszközökhöz](device-restrictions-android-for-work.md#dedicated-device-settings)is biztosítjuk. 


## <a name="get-started"></a>Bevezetés

Az alkalmazáshoz kapcsolódó legtöbb információ az **Ügyfélalkalmazások** területen található, amely a következőképpen érhető el:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. A **Microsoft Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.

    ![Az Ügyfélalkalmazások tevékenységprofil](./media/apps-workload.png)

A következő négy szakasz az **Ügyfélalkalmazások** ablaktáblán elérhető lehetőségeket ismerteti.

### <a name="manage"></a>A számítógépeken futó
- **Alkalmazások**: Ezzel a beállítással adhatja hozzá, tekintheti meg, rendelheti hozzá és figyelheti a munkaerő által használt alkalmazásokat. További információkért lásd:
  - [Alkalmazások hozzáadása](apps-add.md).
  - [Alkalmazások hozzárendelése](apps-deploy.md).
  - [Alkalmazások figyelése](apps-monitor.md).
- **Alkalmazás-konfigurációs házirendek**: Ezzel a beállítással megadhatja azokat a beállításokat, amelyekre szükség lehet, amikor egy felhasználó futtat egy alkalmazást. További információkért lásd:
  - [Az Intune alkalmazáskonfigurációs szabályzatai](app-configuration-policies-overview.md).
    - [iOS-es alkalmazáskonfigurációs szabályzatok](app-configuration-policies-use-ios.md).
    - [Androidos alkalmazáskonfigurációs szabályzatok](app-configuration-policies-use-android.md).
- **Alkalmazás-védelmi szabályzatok**: Ezzel a beállítással társíthatja a beállításokat egy alkalmazáshoz, és megvédheti az általa használt vállalati adatkészletet. Korlátozhatja például egy alkalmazás más alkalmazásokkal való kommunikációját, vagy előírhatja PIN-kód megadását a felhasználónak egy céges alkalmazás eléréséhez. További információkért lásd:
  - [Alkalmazásvédelmi szabályzatok](app-protection-policies.md).
- **Alkalmazás szelektív törlése**: Válassza ezt a lehetőséget, ha csak a vállalati adatok eltávolítását szeretné eltávolítani a kiválasztott felhasználó eszközéről. További információkért lásd:
  - [Alkalmazások szelektív törlése](apps-selective-wipe.md).
- **iOS-alkalmazáskiépítési profilok**: Az iOS-alkalmazások tartalmaznak egy kiépítési profilt és kódot, tanúsítvánnyal aláírva. Ha a tanúsítvány lejár, az alkalmazás a továbbiakban nem futtatható. Az Intune biztosítja az eszközöket, amelyek segítségével proaktív módon rendelhet hozzá új kiépítési profilt azokhoz az eszközökhöz, amelyeken hamarosan lejárnak az alkalmazások. További információkért lásd:
  - [iOS-alkalmazáskiépítési profilok](app-provisioning-profile-ios.md).

Az e szakasz tartalmával kapcsolatos további információ: [Alkalmazáskezelés](app-management.md).

### <a name="monitor"></a>Figyelés
- **Alkalmazás-licencek**: Mennyiségi programban vásárolt alkalmazások megtekintése, kiosztása és figyelése az alkalmazás-áruházakból. További információkért lásd:
  - [iOS Volume Purchase Program-alkalmazások](vpp-apps-ios.md).
  - [A Microsoft Store Vállalatoknak áruházból mennyiségi programban vásárolt alkalmazások](windows-store-for-business.md).
- **Felderített alkalmazások**: Megtekintheti az Intune által hozzárendelt vagy az eszközre telepített alkalmazásokat. További információ: az [Intune által felderített alkalmazások](app-discovered-apps.md).
- **Alkalmazás telepítési állapota**: Egy Ön által létrehozott alkalmazás-hozzárendelés állapotának megtekintése. További információk: [Alkalmazásadatok és -hozzárendelések figyelése a Microsoft Intune-ban](apps-monitor.md#device-and-user-status-graphs).
- **Alkalmazás védelmi állapota**: Egy Ön által kiválasztott felhasználóhoz tartozó alkalmazás-védelmi szabályzat állapotának megtekintése.
- **Naplók**: Tekintse meg az Intune alkalmazással kapcsolatos tevékenységeit az összes rendszergazda számára.

Az e szakasz tartalmával kapcsolatos további információ: [Alkalmazások figyelése](apps-monitor.md).

### <a name="set-up"></a>Beállítás
- **iOS VPP-tokenek**: Alkalmazza és tekintse meg az iOS Volume Purchase program (VPP) licenceit. További információkért lásd:
  - [mennyiségi programban vásárolt iOS-alkalmazások](vpp-apps-ios.md)
- **Windowsos vállalati tanúsítvány**: Alkalmazza vagy tekintse meg az üzletági alkalmazások felügyelt Windows-eszközökre való terjesztésére szolgáló kód-aláíró tanúsítvány állapotát.
- **Windows Symantec-tanúsítvány**: A XAP és a WP8. x Appx-fájlok Windows 10 Mobile rendszerű eszközökre való terjesztéséhez szükséges Symantec-kód-aláíró tanúsítvány állapotának alkalmazása vagy megtekintése.
- **Vállalati Microsoft Store**: A vállalati Microsoft Store integrációjának beállítása. Ezt követően az Intune-ban szinkronizálhatja és kioszthatja a megvásárolt alkalmazásokat, továbbá nyilvántarthatja a licenchasználatot. További információkért lásd:
  - [A Microsoft Store Vállalatoknak áruházból mennyiségi programban vásárolt alkalmazások](windows-store-for-business.md).
- **Windows-oldali betöltési kulcsok**: Hozzáadhat egy Windows-alapú betöltési kulcsot, amellyel az alkalmazások közvetlenül az eszközökre telepíthetők, és nem lehet az alkalmazást a Windows áruházból közzétenni és letölteni. További információkért lásd:
  - [Windows-alkalmazás közvetlen telepítése](app-sideload-windows.md).
- **Céges portál branding**: Szabja testre a Céges portál, hogy a vállalat arculatát adja meg. További információkért lásd:
  - [Céges portál konfigurálása](company-portal-app.md).
- **Alkalmazások kategóriái**: Alkalmazás-kategóriák nevének hozzáadása, rögzítése és törlése.
- **Androidos munkahelyi profil**: Jóváhagyhatja és szinkronizálhatja a vállalata számára jóváhagyott alkalmazásokat. További információkért lásd:
  - [Androidos munkahelyi profilos alkalmazások](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Súgó és támogatás
- **Súgó és támogatás**: Hibakeresés, támogatás kérése vagy az Intune állapotának megtekintése. További információkért lásd:
  - [Problémák elhárítása](help-desk-operators.md).

## <a name="next-steps"></a>További lépések

- [Alkalmazás hozzáadása a Microsoft Intune-hoz](apps-add.md)
