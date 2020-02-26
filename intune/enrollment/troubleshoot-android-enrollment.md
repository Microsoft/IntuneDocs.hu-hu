---
title: Androidos vállalati eszközök hibakeresése Microsoft Intune
description: Javaslatok az Android-eszközök Intune-beli regisztrálásával kapcsolatos leggyakoribb problémák elhárításához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 312f8ee3acb6b8be767d6349b29932ab65ae75d8
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77611029"
---
# <a name="troubleshoot-android-device-enrollment-problems-in-microsoft-intune"></a>Az Android-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune

Ez a cikk segít az Intune-rendszergazdáknak az Android-eszközök Intune-beli regisztrálásakor felmerülő problémák megismerésében és elhárításában.

## <a name="apps-on-android-devices"></a>Alkalmazások Android-eszközökön

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>Az Intune-nal nem telepített felügyelt Google Play-alkalmazások megjelennek a munkahelyi profilban.
A rendszeralkalmazások a munkahelyi profil létrehozásakor az eszköz SZÁMÍTÓGÉPGYÁRTÓja által is engedélyezhetők. Ezt a MDM szolgáltató nem ellenőrzi.

A hibaelhárításhoz kövesse az alábbi lépéseket:

  1. Gyűjtsön Céges portál naplókat.
  2. Figyelje meg, hogy az alkalmazások váratlanul megjelennek a munkahelyi profilban.
  3. Az eszköz regisztrációjának törlése az Intune-ból és az Céges portál eltávolítása.
  4. Telepítse a [test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) alkalmazást, amely lehetővé teszi, hogy a munkahelyi profil létrehozása nem egy, a teszteléshez szükséges.
  5. Az eszközön munkahelyi profil létrehozásához kövesse a [test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) című témakör utasításait.
  6. Tekintse át a munkahelyi profilban megjelenő alkalmazásokat. 
  7. Ha ugyanazok az alkalmazások jelennek meg a tesztelési DPC alkalmazásban, akkor az adott eszköz OEM-je az alkalmazásokat is elvárta.

### <a name="unapproved-google-play-for-work-store-apps-arent-being-removed-from-the-mobile-apps-page-in-intune"></a>Nem engedélyezett Google Play for Work áruházbeli alkalmazások nem törlődnek az Intune Mobile Apps lapjáról
Ez az elvárt működés.

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>A felügyelt Google Play-alkalmazások nem jelennek meg az Intune-portál felderített alkalmazások paneljén
Ez az elvárt működés.

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>Támogatottak-e a webalkalmazások a munkahelyi profilhoz regisztrált eszközökön?
Jelenleg nem.

## <a name="device-management"></a>Eszközkezelés

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>Fájl elérési útja belső tárterület/Android/a. com. microsoft. windowsintune tanúsítványfájlt. companyportal/fájlok hiányoznak a munkahelyi profilban regisztrált eszközökön

  **Válasz**: Ez a várt viselkedés. Ez az elérési út csak az eszköz-rendszergazda (örökölt Android-regisztráció) esetén jön létre.

  Céges portál naplók összegyűjtéséhez kövesse az alábbi lépéseket:

  1. A Céges portál alkalmazásban a jelvény mellett koppintson a **menü** > **Súgó** > **e-mail támogatás**elemre, majd koppintson az **e-mail küldése & feltöltési naplók**elemre. 
  2. Amikor a rendszer kéri, hogy kérjen **segítséget**az alkalmazásban, válassza ki az egyik e-mail alkalmazást.
  3. A rendszer e-mailt küld a rendszergazdának egy incidens-AZONOSÍTÓval, amely a Microsoft terméktámogatási szolgálata számára biztosítható.

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>A felügyelt Google Play utolsó szinkronizálási ideje nem frissült napokban
Ez az elvárt működés. A szinkronizálás csak akkor aktiválódik, ha ezt manuálisan végzi.

### <a name="is-system-center-configuration-manager-hybrid-supported"></a>Támogatott-e a System Center Configuration Manager Hybrid?
A Configuration Manager 1702-es és újabb verzióiban támogatott a munkahelyi profil kezelése. A dedikált eszközök (COSU) nem támogatottak hibrid forgatókönyvekben.

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>Az eszközök regisztrálásakor titkosításra van szükség. Ki lehet kapcsolni?
Nem, a Google a munkahelyi profilhoz szükséges titkosítást igényel. 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>A Samsung-eszközök blokkolja a harmadik féltől származó billentyűzetek, például a SwiftKey használatát
A Samsung megkezdte ennek a korlátozásnak az Android 8.0 + rendszerű eszközökön való betartatását. A Microsoft jelenleg a Samsungnál dolgozik ezzel a problémával, és új információkat küld, ha elérhető.

## <a name="remote-actions"></a>Távoli műveletek

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>A törlés (gyári beállítások visszaállítása) lehetőség nem érhető el a munkahelyi profilhoz regisztrált eszközön
Ez az elvárt működés. A munkahelyi profil forgatókönyvben a MDM-szolgáltató nem rendelkezik teljes körű hozzáféréssel az eszközön. Az egyetlen elérhető lehetőség a kivonás (a vállalati adatmennyiség eltávolítása), amely eltávolítja a teljes munkahelyi profilt és annak teljes tartalmát.

### <a name="is-device-passcode-reset-supported"></a>Támogatott az eszköz PIN-kód alaphelyzetbe állítása?
A munkahelyi profilba beléptetett eszközök esetében csak az Android 8,0 vagy újabb rendszerű eszközök munkahelyi profiljának PIN-kódját állíthatja alaphelyzetbe:
- a munkahelyi profil jelszava felügyelve van
- a végfelhasználó engedélyezte a visszaállítását.

A dedikált eszközökhöz (COSU) az eszköz PIN-kód alaphelyzetbe állítása támogatott.


## <a name="next-steps"></a>További lépések

- [Eszközök regisztrálásával kapcsolatos problémák elhárítása az Intune-ban](../troubleshoot-device-enrollment-in-intune.md)
- [Kérdés feltevése az Intune-fórumon](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [A Microsoft Intune támogatási csapatának blogja](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [A Microsoft nagyvállalati mobilitási és biztonsági blogjának beolvasása](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)