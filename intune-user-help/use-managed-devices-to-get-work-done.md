---
title: Mi az eszközök regisztrációja | Microsoft Docs
description: Ismerje meg, mit jelent az eszköz regisztrálása a Céges portál és a Microsoft Intune alkalmazásban.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/13/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca1776915d50858c28b43a49faa7c737c825c67d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72501861"
---
# <a name="what-is-device-enrollment"></a>Mi az eszközregisztrálás?
Ahhoz, hogy az eszközről hozzáférhessen a munkahelyi vagy iskolai erőforrásokhoz, regisztrálnia kell az eszközt a Intune Céges portál alkalmazásban vagy Microsoft Intune alkalmazásban. 

Az eszközök beléptetése során:

* Az eszköz regisztrálva van a szervezetében. Ez a lépés biztosítja, hogy Ön jogosult legyen a szervezete e-mailjeit, alkalmazásait és Wi-Fi elérését. 
* A szervezete eszköz-felügyeleti házirendjeit alkalmazza az eszközre. A szabályzatok tartalmazhatnak olyan műveleteket, mint például az eszközök jelszava és a titkosítás. A követelmények célja, hogy az eszköz és a szervezet adatai biztonságban legyenek a jogosulatlan hozzáféréstől.

Miután frissítette az eszköz beállításait, hogy megfeleljenek a szervezet követelményeinek, a regisztráció befejeződött. Biztonságosan bejelentkezhet a munkahelyi vagy iskolai fiókjába gyakorlatilag bárhonnan.  

Ez a cikk a beléptetés egyéb szempontjait ismerteti, például az alkalmazások beszerzését, a támogatott eszközöket, valamint az eszköz eltávolítását vagy alaphelyzetbe állítását.  

## <a name="company-portal-and-microsoft-intune-app"></a>Céges portál és Microsoft Intune alkalmazás

A Céges portál és a Microsoft Intune alkalmazás figyelmezteti Önt a házirendre vagy a változások beállítására, így a munkahelyi vagy iskolai hozzáférés elvesztése nélkül is elvégezheti a műveletet. 

A Céges portál alkalmazás külön tárolja a személyes és munkahelyi adatokat, így továbbra is produktív és célirányos lehet. Emellett elérhetővé teszi a munkahelyi és iskolai alkalmazásokat is, így megkeresheti és telepítheti a munkahelye számára releváns adatokat.  

### <a name="get-company-portal"></a>Céges portál beolvasása

Bizonyos esetekben a szervezet a Céges portál alkalmazást fogja telepíteni az eszközére. Az alkalmazás az alkalmazás-áruházakból is telepíthető, például a Microsoft Store, az App Store áruházból és a Google Play áruházból. Ha webböngészőből szeretné elérni az alkalmazást, jelentkezzen be a [céges portál webhelyére](https://go.microsoft.com/fwlink/?linkid=2010980) munkahelyi vagy iskolai fiókjával.  

### <a name="get-microsoft-intune-app"></a>Microsoft Intune alkalmazás beolvasása

Ha a Microsoft Intune alkalmazást kell használnia, a szervezet a saját eszközére fogja telepíteni.  

## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Mi a különbség az alkalmazások és a webhely között?
A Céges portál alkalmazás Windows 10, iOS, macOS és Android rendszerű eszközökhöz érhető el. Zökkenőmentesen integrálható az eszköz megfelelő platformján. A webhely verziója bármely eszközről elérhető, és ugyanazt az univerzális élményt nyújtja, függetlenül attól, hogy milyen eszközt használ. 

A Microsoft Intune alkalmazás a vállalat által birtokolt Android-eszközökhöz tartozik, és nem rendelkezik webhellyel.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Milyen típusú eszközöket regisztrálhat a Céges portál?
A következő eszközöket regisztrálhatja Céges portál használatával:  

- Windows-eszközök
  - Windows 10 mobil verzió
  - Windows 10 asztali verzió
  - WVPN-profilokdows Phone 8.1
  - Windows 8.1
- Apple-eszközök
    - iOS
    - macOS
- Androidos eszközök


## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Milyen típusú eszközök regisztrálhatók a Microsoft Intune alkalmazással?  
Regisztrálhat vállalati tulajdonú Android-eszközöket, amelyeket a szervezete az alkalmazással való használatra beállított. Az alkalmazás az Android 6,0-es és újabb verzióit támogatja. 

## <a name="can-you-remove-a-device-from-the-company-portal"></a>El tud távolítani egy eszközt a Céges portál?
Eltávolíthatja vagy alaphelyzetbe állíthatja az eszközt a Céges portálból. Az **eltávolítás** és az **alaphelyzetbe állítás** között azonban van különbség.

Az eszköz eltávolításakor a Céges portál törli a regisztrációt, és megszünteti az eszköz regisztrációját. Az eszköz elveszti a Céges portál elérését. A munkahelyi vagy iskolai adatmennyiségeket is el lehet távolítani. 

Az eszköz alaphelyzetbe állítása során a Céges portál megkísérli visszaállítani a számítógépet vagy az eszközt a gyártó alapértelmezett beállításaira. A munkahelyi vagy iskolai adatok és az összes személyes adatok törlődnek az eszközről. Az Alaphelyzetbe állítás akkor lehet hasznos, ha például elveszti az eszközét. A Céges portál webhelyről távolról is visszaállíthatja.  

## <a name="can-you-remove-a-device-from-the-microsoft-intune-app"></a>El tud távolítani egy eszközt a Microsoft Intune alkalmazásból?
Nem, a Microsoft Intune alkalmazásból nem lehet eltávolítani a vállalat által birtokolt eszközöket.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Mi a teendő, ha nem látom az eszközt a Céges portál vagy Microsoft Intune alkalmazásban?
Ha Céges portál eszközt szeretne látni, először regisztrálnia kell. Ha a regisztráció után még mindig nem látja az összes eszközt, próbálja meg szinkronizálni vagy ellenőriznie a hozzáférést a Céges portálon keresztül. Nem látja a vállalat tulajdonában lévő és felügyelt eszközöket.

A Microsoft Intune alkalmazásban csak a jelenleg használt eszköz jelenik meg. A többi regisztrált eszköz nem lesz látható az alkalmazásban.  

## <a name="where-else-can-i-go-for-help"></a>Hol találhatok még segítségét?  
A gyakori problémák elhárításához tekintse meg ezeket a platform-specifikus dokumentumokat:  

- [Androidos eszközök gyakori problémáinak elhárítása](check-compliance-on-your-device-android.md)  
- [Az iOS-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-ios.md)
- [A macOS-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-macos.md)
- [A Windows-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-windows.md)

Az informatikai támogatási személynek is felveheti a kapcsolatot. A Céges portál és Microsoft Intune alkalmazás Súgó és támogatás lapokat, amelyek a kapcsolattartási adatokat és a problémák jelentésének módjait listázza. A kapcsolattartási adatok a szervezeti [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980)is elérhetők.  

## <a name="next-steps"></a>További lépések  

Ha már készen áll a munkahelyi vagy iskolai fiókjához való hozzáférésre, kövesse a szervezet utasításait az eszköz regisztrálásához. Az alábbi cikkekben részletes beléptetési útmutatót is talál.

* [Windows 10 rendszerű eszköz regisztrálása](enroll-windows-10-device.md)
* [Android-eszköz regisztrálása](enroll-device-android-company-portal.md)
* [Regisztrálás androidos munkahelyi profillal](enroll-device-android-work-profile.md)
* [Regisztrálás Microsoft Intune-alkalmazással](enroll-device-android-microsoft-intune-app.md)
* [iOS-eszköz regisztrálása](enroll-your-device-in-intune-ios.md)
* [A cég által biztosított iOS-eszköz regisztrálása](enroll-your-device-dep-ios.md)
* [macOS-eszköz regisztrálása](enroll-your-device-in-intune-macos-cp.md)
* [A cég által biztosított macOS-eszköz regisztrálása](enroll-company-device-macos.md)


