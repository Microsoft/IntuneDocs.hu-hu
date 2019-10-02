---
title: A vállalat által biztosított iOS-eszköz felügyeleti regisztrálása. | Microsoft Docs
description: A cég által vásárolt és rendelkezésére bocsátott iOS-eszköz Intune-beli regisztrálásának leírása
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: bca7ff55653d12d352b4fb90163f4622a9e573ab
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721007"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>A vállalat által biztosított iOS-eszköz felügyeleti regisztrálása

Útmutató új iOS-eszköz Intune-felügyelet alá helyezéséhez.  

A munkahely vagy iskola által biztosított iOS-eszközöket gyakran előre konfigurálják, mielőtt Ön megkapja azokat. A vállalat akkor küldi az eszközre ezeket az előre konfigurált beállításokat, miután Ön először bekapcsolta azt, és bejelentkezett. Miután az eszköz elvégezte a beállításokat, Ön hozzáférhet munkahelyi vagy iskolai erőforrásaihoz.  

A beállítások megkezdéséhez kapcsolja be az eszközt, majd jelentkezzen be a munkahelyi vagy iskolai hitelesítő adataival. A cikk a továbbiakban azokat a lépéseket és képernyőket ismerteti, amelyekkel a Beállítási asszisztensben találkozni fog.

## <a name="what-is-apple-dep"></a>Mi az Apple DEP?

Lehetséges, hogy vállalata az úgynevezett *Apple Készülékregisztrációs programon* (DEP) keresztül vásárolta meg eszközeit. Az Apple DEP nagy mennyiségű iOS- vagy macOS-eszköz vásárlását teszi lehetővé a vállalatok számára. Ezt követően ezeket az eszközöket egy általuk preferált mobileszköz-felügyeleti szolgáltatóval, például az Intune-nal konfigurálják és felügyelik. Ha Ön rendszergazda, és információt szeretne az Apple DEP-vel kapcsolatban, tekintse át az [iOS-eszközök automatikus regisztrálása az Apple készülékregisztrációs programjával (DEP)](https://docs.microsoft.com/intune/enrollment/device-enrollment-program-enroll-ios.md) című cikket.  

## <a name="set-up-your-ios-device"></a>Az iOS-eszköz beállítása

Ha nem a vállalat által biztosított, hanem saját iOS-eszközt használ, kövesse a [személyes és saját eszközökre](enroll-your-device-in-intune-ios.md) vonatkozó lépéseket.  

1. Kapcsolja be az iOS-eszközt.
2. A **nyelv** kiválasztása után csatlakozzon egy Wi-Fi-hálózathoz.
3. Az **iOS-eszköz beállítása** képernyőn válasszon az alábbi lehetőségek közül:
   - **Beállítás új eszközként**
   - **iCloud biztonsági másolat visszaállítása**
   - **iTunes biztonsági másolat visszaállítása**

4. Miután csatlakozott, megjelenik a **Konfiguráció** képernyő. Ez tudatja Önnel, hogy **[a cége] automatikusan konfigurálja az eszközét.**

   **A konfiguráció lehetővé teszi, hogy [az Ön cége] távolról kezelje ezt az eszközt. A rendszergazdák távolról segíthetnek e-mail- ás hálózati fiókok beállításában, alkalmazások telepítésében és konfigurálásában és a beállítások kezelésében. A rendszergazdák funkciókat tilthatnak le, alkalmazásokat telepíthetnek és távolíthatnak el, megfigyelhetik és korlátozhatják az internetes forgalmat és távolról törölhetik az eszköz tartalmát.**

   **A konfiguráció beállítója: [Az Ön cége] iOS-csoportja [Cím]**

5. Jelentkezzen be az Apple ID azonosítójával. A bejelentkezés után telepítheti a Céges portál alkalmazást, valamint a felügyeleti profilt, amellyel a cége hozzáférést adhat Önnek az erőforrásokhoz, például az e-mailekhez és az alkalmazásokhoz.
6. Fogadja el a **feltételeket és kikötéseket**, majd döntse el, hogy szeretne-e diagnosztikai adatokat küldeni az Apple-nek.
7. A regisztráció befejeztével az eszköz további műveletek elvégzését kérheti. Ezek között szerepelhet az e-mail-hozzáféréshez szükséges jelszó megadása vagy egy PIN-kód beállítása.

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
