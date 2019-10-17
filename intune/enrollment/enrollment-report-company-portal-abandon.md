---
title: Hiányos felhasználói regisztrációk jelentése az Intune-ban
titleSuffix: Microsoft Intune
description: További információ a felhasználói regisztrációk hiányos jelentéséről.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae3c2380aa27096be2490d2404858179ea9d222e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503174"
---
# <a name="incomplete-user-enrollments-report"></a>Hiányos felhasználói beléptetési jelentés

Ez a jelentés azt mutatja be, hogy a Céges portál regisztrációs folyamat felhasználói hol nem fejezik be a beléptetési folyamatot.

A jelentés megtekintéséhez válassza az **Intune** > **eszközök beléptetése** > **hiányos felhasználói regisztrációk**lehetőséget.

Ezen információk használatával frissítheti a bevezetési dokumentumokat, hogy a felhasználók teljes beléptetést végezzenek. Ha például sok felhasználó szakítja meg a folyamatot a Felhasználási feltételeknél, akkor megvizsgálhatja ezt a területet, és intuitívebbé teheti a felhasználók számára.

## <a name="what-is-an-incomplete-enrollment"></a>Mi a hiányos regisztráció?

Hiányos regisztráció, ha a felhasználó a következők valamelyikét hajtja végre:

- Explicit módon a regisztrációt leállító műveletet választ
- Bezárja a Céges portált a regisztráció során
- Több mint 30 percet tölt el egy regisztrációs szakasszal, mielőtt a következővel folytatná

Ha egy felhasználó úgy dönt, hogy leállítja a regisztrációt, és többször is újraindul, több kísérletet és több hiányos regisztrációt is megjelenít. Ha a felhasználó 30 percet vár a különböző beléptetési képernyők között, akkor több hiányos regisztrációnak minősül.

## <a name="what-does-the-report-show"></a>Mi mutat meg a jelentés?

A jelentések tartalmazzák az iOS-és Android-eszközökre vonatkozó adatgyűjtést.

A jelentés az elmúlt két hétre vonatkozó adatokat jelenít meg, de szűrheti a jelentést az elmúlt 30 napban bármely időszak megjelenítésére.

Szűrhet a dátumtartomány, az operációs rendszer és a regisztrációs szakasz alapján a **Szűrő** kiválasztásával.

### <a name="number-and-percentage-tiles"></a>Szám és százalékos arány csempék

A jelentés elején megtekintheti a nem teljes regisztrációk számát és százalékos arányát az összes regisztrációhoz viszonyítva.

- Kezdeményezett regisztrációk: A regisztrációs próbálkozások száma.
- Hiányos beléptetések: a megkísérelt regisztrációk száma, amelyek nem eredményeztek teljes mértékben regisztrált és megfelelő eszközt.
- Nem teljes arány: az elhagyott beléptetési kísérletek százalékos aránya (megszakított regisztrációk/kezdeményezett regisztrációk).

### <a name="line-graph"></a>Vonaldiagram

A vonalas diagramon a négy alapvető regisztrációs szakaszban a napi hiányos regisztrációk láthatók:

- Beállítási ellenőrzőlista
- Platformképernyők
- Használati feltételek
- Megfelelőség/aktiválás

### <a name="user-abandonment-actions"></a>Felhasználói megszakítási műveletek

A következő táblázatok a nem teljes beléptetést kérő felhasználói műveletek listáját mutatják be. Regisztrációs képernyők példáinak megtekintéséhez megnézheti az [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) és az [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment) rendszerben történő regisztrációról készült videókat. 


#### <a name="setup-checklist-section"></a>Beállítási ellenőrzőlista szakasz

| Művelet neve | Képernyő vagy folyamat | Platfésm | Művelet |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | A rendszer arra kéri, hogy nyisson meg egy oldalt a Céges portálon. | iOS/Android | **Mégse** |
| EnrollmentWrapUp | Eszközregisztrációs képernyő, ami addig látható, amíg be nem fejeződik a **vállalati erőforrások betöltése** | iOS/Android | Időtartam > 30 perc |
| DeviceCategory | Eszközkategória kiválasztása (ha a rendszergazda beállította), addig látható, amíg rá nem kattint a **Kész** gombra | iOS/Android | Időtartam > 30 perc |
| PreEnrollmentWizard | Hozzáférés-beállítási képernyő, ha megkezdte a regisztrációt, de visszatért a hozzáférés-beállításhoz | iOS/Android| **Halassza el** |
| PreEnrollmentWizard | Hozzáférés-beállítási képernyő, amely addig látható, amíg rá nem kattint a **Tovább** gombra a **Következő lépések** képernyőn | iOS/Android | Időtartam > 30 perc |

#### <a name="platform-screens-section"></a>Platformképernyők szakasz

| Művelet neve | Képernyő vagy folyamat | Platfésm | Művelet |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Rákérdezés a konfigurációs profil megjelenítésére | iOS | **Figyelmen kívül hagyás** |
| iOSProfileLaunch | Profilképernyő telepítése | iOS | **Mégse** |
| iOSProfileLaunch | Rákérdezés, hogy megbízik-e a profil forrásában az eszköz regisztrációjához | iOS | **Mégse** |
| iOSProfileLaunch | Profiltelepítési képernyő, amely a profil telepítésének befejeződéséig látható | iOS | Időtartam > 30 perc |
| AndroidPermissions | Eszközadminisztrátor aktiválása képernyő | Android: | **Mégse** |
| AndroidPermissions | A hívások kezdeményezésének és kezelésének jóváhagyáskérésétől addig, amíg az eszközrendszergazda végre nem hajtja az **aktiválást** | Android: | Időtartam > 30 perc |
| KnoxActivation | KLMS-ügynök aktiválása (csak Samsung) | Android:| **Mégse** |
| KnoxActivation | KLMS-ügynök aktiválása a **megerősítésig** | Android: | Időtartam > 30 perc|

#### <a name="terms-of-use-section"></a>Használati feltételek szakasz

| Művelet neve | Képernyő vagy folyamat | Platfésm | Művelet |
| ---- |---- |---- |---- |
| TermsofUse | Használati feltételek (ha a rendszergazda konfigurálta) | iOS/Android | **Összes elutasítása** |
| TermsofUse | Használati feltételek megjelenítése az **Összes elfogadása** kiválasztásáig | iOS/Android | Időtartam > 30 perc |

#### <a name="complianceactivation-section"></a>Megfelelőség/aktiválás képernyő

| Művelet neve | Képernyő vagy folyamat | Platfésm | Művelet |
| ---- |---- |---- |---- |
| Megfelelőség | Eszközmegfelelőség (ha a rendszergazda beállította) nem zöldként jelenik meg a regisztráció utáni hozzáférés-beállítás esetén| iOS/Android | **Halassza el** |
| Megfelelőség | Az eszközmegfelelőség nem zöldként jelenik meg, amíg nem frissíti zöldként való megjelenítésre | iOS/Android | Időtartam > 30 perc |
| Aktiválás | Regisztrációaktiválás (ha a rendszergazda beállította) nem zöldként jelenik meg a hozzáférés beállításakor | iOS/Android | **Halassza el** |
| Megfelelőség | Az eszközaktiválás nem zöldként jelenik meg, amíg nem frissíti zöldként való megjelenítésre | iOS/Android | Időtartam > 30 perc |

## <a name="next-steps"></a>További lépések

A nem teljes beléptetési arány ellenőrzése után áttekintheti a [regisztrációs beállításokat](enrollment-options.md) , és ellenőrizheti, hogy végezhető-e módosítás a regisztráció javítása érdekében.
