---
title: Egy Microsoft Intune eszköz elsődleges felhasználójának megkeresése.
titleSuffix: ''
description: Egy Intune-eszköz elsődleges felhasználójának (vagy felhasználó-eszköz kapcsolatának) megkeresése.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b804eccfa6f860c77ab4a1a7f1fe5ae0f5baf101
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781818"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Intune-eszköz elsődleges felhasználójának megkeresése

Az elsődleges felhasználó, más néven a felhasználó-eszköz kapcsolat, az összes Intune-eszköz tulajdonsága. Egy Intune-eszközhöz nulla vagy egy elsődleges felhasználó rendelhető. Ha nincs hozzárendelve elsődleges felhasználó, az eszközt "megosztott eszköznek" nevezzük.

## <a name="find-a-devices-primary-user"></a>Eszköz elsődleges felhasználójának keresése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** lehetőséget > válasszon ki egy eszközt.
3. Az **Áttekintés** oldalon láthatja a felsorolt elsődleges felhasználót.

## <a name="what-is-the-primary-user"></a>Mi az elsődleges felhasználó?
Az elsődleges felhasználó tulajdonság a licenccel rendelkező Intune-felhasználó az eszközre való leképezésére szolgál a következőben:
- A Céges portál alkalmazás
- Végfelhasználói webhely
- INFORMATIKAI szakemberek, például a Azure Portal hibaelhárítási lapjai. Ezek az oldalak a felhasználói fiókokat az elsődleges felhasználó használatával képezik le az eszközökre. 

### <a name="company-portal-app"></a>Vállalati portál alkalmazás
A Céges portál alkalmazás azt várja, hogy a Céges portálbe bejelentkezett felhasználói fiók az adott eszköz elsődleges felhasználója. Ha egy másik felhasználó lett hozzárendelve elsődleges felhasználóként, a Céges portál figyelmeztetést jelenít meg:

"Ez az eszköz már hozzá van rendelve valakinek a szervezetében. Forduljon a cég informatikai támogatási szolgálatához, hogy az elsődleges eszköz felhasználója legyen. Továbbra is használhatja Céges portál, de a funkciók korlátozottak lesznek. "

Ha egy Intune-eszközhöz nincs hozzárendelve elsődleges felhasználó, akkor a Céges portál alkalmazás megosztott eszközként észleli azt. A megosztott eszközök vizuálisan azonosíthatók az eszköz csempén megjelenő "Shared" címkével. Ebben a módban a Céges portál továbbra is használható az elérhető alkalmazások igénylésére és telepítésére. Az önkiszolgáló műveletek (alaphelyzetbe állítás/Átnevezés/kivonás) azonban nem érhetők el.  

Ahhoz, hogy megjelenjenek a megosztott eszközök Céges portálján, az elérhető alkalmazásokat hozzá kell rendelni egy felhasználói csoporthoz. A rendszer a rendszerkörnyezetbe vagy a felhasználói környezetbe telepíti, attól függően, hogy az alkalmazás hogyan lett konfigurálva az informatikai rendszergazda által. Az alkalmazás kontextusával kapcsolatos további információkért lásd: [alkalmazások telepítése Windows 10-es eszközökre](../apps/apps-windows-10-app-deploy.md). A funkció használatához Céges portál 10.3.4651.0 vagy újabb verzió szükséges.


## <a name="who-is-assigned-as-the-primary-user"></a>Ki van rendelve elsődleges felhasználóként?
Az Intune a regisztráció után automatikusan hozzáadja az elsődleges felhasználót az eszközökhöz. A beléptetési módszer határozza meg, hogy mikor kerül be az elsődleges felhasználó egy eszközre.

| Platform | Regisztráció módszere | Elsődleges felhasználó hozzárendelve | Az elsődleges felhasználó hozzá van rendelve |
| ---- | ---- | ---- | ---- |
| Windows | Munkahelyi vagy iskolai (felhasználó által vezérelt) hozzáadása | Felhasználó regisztrálása | Regisztráció során |   
| Windows | Modern alkalmazás-bejelentkezés (felhasználó által vezérelt) | Felhasználó regisztrálása | Regisztráció során | 
| Windows | Csak a MDM regisztrálása (felhasználó által vezérelt) | Felhasználó regisztrálása | Regisztráció során | 
| Windows | Azure AD-csatlakozás (beépített élmény) | Felhasználó regisztrálása | Regisztráció során | 
| Windows | Azure AD JOIN (robotpilóta a box-ban) | Felhasználó regisztrálása | Regisztráció során | 
| Windows | Csak a MDM regisztrálása | Felhasználó regisztrálása | Regisztráció során | 
| Windows | Hibrid AADJ + automatikus regisztrálási csoportházirend-objektum | Első felhasználó a Windowsba való bejelentkezéshez | Amikor az első felhasználó bejelentkezik a Windowsba| 
| Windows | Megosztott kezelés | Első felhasználó a Windowsba való bejelentkezéshez | Amikor az első felhasználó bejelentkezik a Windowsba | 
| Windows | Azure AD JOIN (csoportos beléptetési jogkivonat) | Nincsenek | Nem alkalmazható | 
| Windows | Azure AD JOIN (Autopilot öntelepítő üzemmód) | Nincsenek | Nem alkalmazható | 
| Platformfüggetlen | Felhasználó által vezérelt regisztráció Céges portál alkalmazással | Felhasználó regisztrálása | Regisztráció során |
| Platformfüggetlen | Eszköz beléptetési kezelője (DEM) | DEM-felhasználó regisztrálása | Regisztráció során |
| iOS/iPadOS, macOS | Apple automatikus eszközök beléptetése (DEP felhasználói affinitással | Felhasználó regisztrálása | Regisztráció során |
| iOS/iPadOS, macOS | Apple automatikus eszközök beléptetése (DEP felhasználói affinitás nélkül) | Nincsenek | Nem alkalmazható |
| Android: | Androidos vállalati tulajdonú, dedikált eszközök | Nincsenek | Nem alkalmazható |

## <a name="primary-user-and-azure-ad-device-owner"></a>Elsődleges felhasználó és Azure AD-eszköz tulajdonosa
Bizonyos esetekben előfordulhat, hogy az Intune elsődleges felhasználója nem azonos az Azure AD-eszköz **tulajdonosi** tulajdonságával (a megtekinthető az **eszközök** > **Azure ad-eszközök**területen). Az Azure AD-eszköz tulajdonosát az eszköz regisztrációja során Azure Active Directoryba adja hozzá a rendszer.

## <a name="next-steps"></a>További lépések
[Intune-eszközök kezelése.](device-management.md)
