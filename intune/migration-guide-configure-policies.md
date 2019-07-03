---
title: Intune-migráció során az eszköz- és megfelelőségi konfigurálása
titleSuffix: Microsoft Intune
description: Ez a cikk az eszközmegfelelőségi és alkalmazáskezelési szabályzatok Microsoft Intune-migráció során történő konfigurálásához szükséges lépéseket ismerteti.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a5f28f01d0c8be6692deaf27391e52619fcdcab
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512272"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>Eszközmegfelelőségi és alkalmazásfelügyeleti szabályzatok konfigurálása Microsoft Intune-migráció során

Az Intune-migráció során a fő cél az, hogy minden eszköz regisztrálva legyen az Intune-ban, és megfeleljenek a rájuk vonatkozó szabályzatoknak. Az eszközszabályzatok nem csak a vállalati tulajdonban lévő egyfelhasználós eszközök felügyeletét segítik, hanem a saját tulajdonú (BYOD), valamint a közösen használt eszközökét is (például kioszkok, POS-eszközök, közös használatú iskolai táblagépek, illetve felhasználó nélküli iOS-es eszközök).

Lehet, hogy minden eszközplatform más beállítási lehetőségeket kínál, de az Intune eszközszabályzatai minden platformmal a következő mobileszköz-felügyeleti képességek alapján működnek együtt:

-   az egyes felhasználók által regisztrálható eszközök számának korlátozása;

-   Eszközbeállítások (például eszközszintű titkosítás, jelszóhossz, kamerahasználat) kezelése.

-   Alkalmazások, e-mail-profilok, VPN-profilok stb. távoli telepítése.

-   eszközszintű feltételek kiértékelése a biztonsági megfelelőségi szabályzatokhoz.

> [!IMPORTANT]
> Az eszközfelügyeleti szabályzatokat nem közvetlenül az egyes eszközökhöz vagy felhasználókhoz rendelik hozzá, hanem felhasználói csoportokhoz. A közvetlenül felhasználói csoportokra alkalmazott szabályzatok a felhasználók eszközeire, az eszközcsoportokra alkalmazottak pedig az adott csoportok tagjaira lesznek érvényesek.

## <a name="task-list-for-device-compliance-policies"></a>Feladatlista az eszközmegfelelőségi szabályzatokhoz

### <a name="task-1-add-device-groups-optional"></a>1\. feladat: Eszközcsoportok létrehozása (nem kötelező)

Létrehozhat eszközcsoportokat, ha bizonyos felügyeleti feladatokat eszközidentitás, nem pedig felhasználói identitás alapján kell elvégeznie.

Az eszközcsoportok elsősorban kioszkok, adott helyszínre telepített vagy műszakonként mások által használt eszközök felügyelete esetén hasznosak, amelyeknek nincs kizárólagos felhasználója.

Ha az eszközök regisztrálása előtt eszközcsoportokat konfigurál, az eszközkategóriák alapján a regisztrációnál automatikusan csoportosíthatja is az eszközöket. Ezután automatikusan megkapják a csoportjukra érvényes eszközszabályzatokat. [Csoportok – első lépések](groups-get-started.md).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>2\. feladat: Erőforrás-hozzáférési profilok (Wi-Fi, VPN és e-mail-tanúsítványok) használata

Az erőforrás-hozzáférési profilok tanúsítványokat és hozzáférési konfigurációkat bocsátanak rendelkezésre a regisztrált eszközökhöz. Ha tanúsítványalapú hitelesítést használ, [konfigurálja a tanúsítványokat](certificates-configure.md).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>3\. feladat: Létrehozása és üzembe helyezése az eszközkonfigurációs profilok

Az eszközszintű beállítások (például kamera letiltása, alkalmazás-áruház, egyalkalmazásos mód, kezdőképernyő stb.) betartatásához eszközkonfigurációs profilt kell létrehozni. További információ az [eszközprofilokról](device-profiles.md).

#### <a name="directly-import-ios-configuration-profiles-optional"></a>iOS-es konfigurációs profilok közvetlen importálása (nem kötelező)

-   **Az Apple Configurator iOS-profilok (iOS 7.1 és újabb verziók):** Ha a meglévő MDM-megoldás Apple Configurator-profilokat (.mobileconfig-fájlokat) használ, az Intune ezeket közvetlenül tudja importálni egyéni konfigurációs szabályzat.

-   **iOS Mobile Application Configuration-szabályzatokat:** Ha a meglévő MDM-megoldás iOS Mobile Application Configuration-szabályzatokat használ, az Intune ezeket közvetlenül tudja importálni, amennyiben azok megfelelnek az Apple által tulajdonságlistákhoz megadott XML-formátumnak.

- Útmutató egyéni szabályzat felvételéhez [iOS-en](custom-settings-ios.md).

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>4\. feladat: (Nem kötelező) eszköz megfelelőségi szabályzatok létrehozása és telepítése

Az eszközmegfelelőségi szabályzatok biztonsági jellegű beállítások értékét vizsgálják, és jelentik, hogy mely eszközök felelnek meg a vállalati előírásoknak, és melyek nem. A beállítások a következők:

-   PIN-kód hossza

-   Feltört állapot

-   Operációs rendszer verziója

További források az eszközmegfelelőségi szabályzatokkal kapcsolatban:

-   Az [eszközmegfelelőségi szabályzatok](device-compliance.md) ismertetése

-   Útmutató [eszközmegfelelőségi szabályzat létrehozásához](device-compliance-get-started.md)

### <a name="task-5-publish-and-deploy-apps"></a>5\. feladat: Alkalmazások közzététele és telepítése

Az Intune MDM használata esetén alkalmazásokat telepíthet automatikus telepítésük megkövetelésével vagy a Céges portálon való közzétételükkel.

-   [Alkalmazások hozzáadása](apps-add.md).

-   [Alkalmazások üzembe helyezése](apps-deploy.md).

### <a name="task-6-enable-device-enrollment"></a>6\. feladat: Eszközök regisztrálásának lehetővé tétele

Az eszköz regisztrálása az eszköz kezeléséhez szükséges. Útmutató [a vállalati és a személyes tulajdonú eszközök regisztrációra való felkészítéséhez](device-enrollment.md)

## <a name="next-steps"></a>További lépések

[Alkalmazásvédelmi szabályzatok konfigurálása (nem kötelező)](migration-guide-app-protection-policies.md).
