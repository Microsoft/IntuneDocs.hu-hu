---
title: Windows 10-es oktatási beállítások a Microsoft Intune-ban – Azure | Microsoft Docs
description: Tekintse meg a Windows 10-es eszközökre vonatkozó oktatási beállítások listáját. Ezeket a beállításokat egy eszköz konfigurációs profiljában használhatja a teszt alkalmazással, kiválaszthatja, hogy a felhasználók vagy tanulók hogyan jelentkeznek be, figyelheti a képernyőt a teszt során, és többet az Intune-ban.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d89f512c06dcfbf6f6ddaba5e17ac9ca6f0becf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506809"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>A tesztelési alkalmazás konfigurálása Windows 10-es eszközökön az Intune használatával

A Take a test alkalmazással biztonságosan felügyelheti az online teszteket az osztályterem Windows 10-es eszközein. A teszt alkalmazás beállításához létre kell hoznia egy eszköz-konfigurációs profilt az Intune-ban, és konfigurálnia kell a biztonságos értékelés beállításait. Ez a cikk ismerteti azokat a beállításokat, amelyeket a vizsga alkalmazáshoz fog találni. 

Miután konfigurálta a profilt, rendeljen hozzá és telepítse azt a tanulók számára. 

A szolgáltatással kapcsolatos további információkért tekintse meg a [tesztelési alkalmazást az Intune-ban](education-settings-configure.md) .

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy eszköz konfigurációs profilt](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Tesztelési beállítások
Az eszköz konfigurációs profiljának létrehozása után nyissa meg a **profil típusát** , és válassza a **biztonságos értékelés (oktatás)** lehetőséget. Az alábbi lépéseket követve tesztelheti az alkalmazás beállításait. 


- **Fióktípus**: válassza ki, hogyan jelentkeznek be a felhasználók a tesztbe. A választható lehetőségek:
  - Azure AD-fiók
  - Tartományi fiók
  - Helyi fiók
  - Helyi vendég fiók: csak a Windows 10 1903-es vagy újabb verzióját futtató eszközökön érhető el.    
- **Fiók felhasználóneve**: adja meg a vizsga alkalmazással használt fiók felhasználónevét. A fiókokat a következő formátumban adhatja meg:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Fióknév**: egy helyi vendég fiók típusának beállításához adja meg a teszt alkalmazáshoz használt fiók nevét. A fiók neve csempeként fog megjelenni a bejelentkezési képernyőn. A teszt elindításához a tanulók a csempére kattintanak.  
- **Assessment URL-cím**: adja meg annak a tesztnek az URL-címét, amelyet el szeretne végezni a felhasználók számára. Az URL-cím beszerzésével kapcsolatos további információkért tekintse meg a [teszt dokumentációját](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Nyomtatókapcsolat**: válassza a **szükséges** lehetőséget, hogy csak a nyomtatóhoz csatlakozó eszközökről engedélyezze a tesztelési alkalmazáshoz való hozzáférést. Ez a beállítás azt is lehetővé teszi, hogy az alkalmazás nyomtatás gombja elérhető legyen a tesztek elfogadói számára. A **nincs konfigurálva** beállítás lehetővé teszi a tanulók számára az alkalmazás elérését olyan eszközökön, amelyek nem csatlakoznak a nyomtatóhoz.  
- **Képernyő-figyelés**: válassza az **Engedélyezés lehetőséget** a képernyő tevékenység figyeléséhez, miközben a felhasználók tesztet vesznek. A **nincs konfigurálva beállítás** megakadályozza a képernyő figyelését a teszt során.
- **Szöveggel kapcsolatos javaslatok**: válassza az engedélyezés a teszt elfogadók **számára** lehetőséget, és tekintse meg a szöveget. **Nincs konfigurálva** a szöveges javaslatok blokkolása a felhasználók számára.

## <a name="next-steps"></a>További lépések

Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md), és [Figyelje annak állapotát](device-profile-monitor.md).
