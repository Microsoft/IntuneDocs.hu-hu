---
title: Preferencia-fájl beállításainak hozzáadása macOS-eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
titleSuffix: ''
description: Adjon hozzá egy XML-vagy plist-fájlt, amely az alkalmazással kapcsolatos legfontosabb információkat tartalmazza. A konfigurációs profilban megváltoztathatja a legfontosabb információkat a tulajdonságok listájának fájljában, és hozzárendelheti a macOS-eszközökhöz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d226a5b8ee448b7b168a03fe6b8a1c63bc1be432
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827785"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Tulajdonság-listaelem hozzáadása macOS-eszközökhöz Microsoft Intune használatával

A Microsoft Intune használatával a MacOS-eszközökhöz, illetve macOS-eszközökön lévő alkalmazásokhoz (. plist) adhat hozzá.

Ez a funkció az alábbiakra vonatkozik:

- 10,7 és újabb rendszerű macOS-eszközök

A tulajdonságok listázása általában a macOS-alkalmazásokkal kapcsolatos információkat tartalmaz. További információ: információk [a fájlok listázásáról](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (Apple webhelye) és az [Egyéni adattartalom-beállításokról](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

Ez a cikk felsorolja és ismerteti a macOS-eszközökhöz hozzáadható különböző tulajdonságokat felsoroló fájlok beállításait. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a beállításokat használhatja az alkalmazáscsomag-azonosító (`com.company.application`) hozzáadásához és a. plist fájl hozzáadásához.

Ezek a beállítások hozzáadódnak az Intune-ban lévő eszköz konfigurációs profiljához, majd a macOS-eszközökhöz vannak rendelve vagy telepítve.

## <a name="before-you-begin"></a>Előkészületek

[Hozza létre a profilt](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Amit még tudnia kell

- Ezek a beállítások nincsenek érvényesítve. Győződjön meg arról, hogy teszteli a módosításokat, mielőtt hozzárendeli a profilt az eszközökhöz.
- Ha nem tudja, hogyan kell megadnia az alkalmazás kulcsát, módosítsa a beállítást az alkalmazáson belül. Ezt követően tekintse át az alkalmazás preferencia-fájlját a [Xcode](https://developer.apple.com/xcode/) használatával, hogy megtekintse a beállítás konfigurációját. Az Apple javasolja a nem felügyelhető beállítások eltávolítását a Xcode használatával a fájl importálása előtt.
- Csak néhány alkalmazás felügyelt beállításokkal működik, és előfordulhat, hogy nem teszi lehetővé az összes beállítás kezelését.
- Ügyeljen arra, hogy feltöltse azokat a tulajdonságlap-fájlokat, amelyek az eszköz csatornájának beállításait célozzák meg, nem pedig a felhasználói csatornák beállításait. A tulajdonságmezők fájljai a teljes eszközt célozzák meg.

## <a name="preference-file"></a>Preferenciafájl

- **Preferencia tartomány neve**: a rendszer általában a webböngészők (Microsoft Edge), a [Microsoft Defender komplex veszélyforrások elleni védelem](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)és az egyéni alkalmazások számára használják a tulajdonságok listáját. A preferencia tartomány létrehozásakor létrejön egy köteg-azonosító is. Adja meg a csomag AZONOSÍTÓját, például `com.company.application`. Adja meg például a következőt: `com.Contoso.applicationName`, `com.Microsoft.Edge`vagy `com.microsoft.wdav`.
- **Tulajdonságlap fájlja**: válassza ki az alkalmazáshoz társított tulajdonságlap-fájlt. Győződjön meg róla, hogy `.plist` vagy `.xml` fájl. Töltse fel például `YourApp-Manifest.plist` vagy `YourApp-Manifest.xml` fájlt.
- **Fájl tartalma**: a tulajdonság-lista fájljának legfontosabb adatai láthatók. Ha módosítania kell a legfontosabb adatokat, nyissa meg a fájlt egy másik szerkesztőben, majd töltse fel újra a fájlt az Intune-ban.

Győződjön meg arról, hogy a fájl megfelelően van formázva. A fájlnak csak kulcs-érték párokkal kell rendelkeznie, és nem szabad becsomagolni `<dict>`, `<plist>`vagy `<xml>` címkékbe. Például a következő fájlnak hasonlónak kell lennie a tulajdonság-lista fájljához:

```xml
<key>SomeKey</key>
<string>someString</string>
<key>AnotherKey</key>
<false/>
...
```

A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a profil, és megjelenik a profilok listájában.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

A Microsoft Edge-hez készült preferencia-fájlokkal kapcsolatos további információkért lásd: [a Microsoft Edge Policy beállításainak konfigurálása MacOS rendszeren](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
