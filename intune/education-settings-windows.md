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
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07d3488d509339fc48eb8449b12725b757775eb5
ms.sourcegitcommit: 98f2597eec28c6096985d5a1acae72430c2afb1a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877971"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>A tesztelési alkalmazás konfigurálása Windows 10-es eszközökön az Intune használatával

A Take a test alkalmazással biztonságosan felügyelheti az online teszteket az osztályterem Windows 10-es eszközein. A teszt alkalmazás beállításához létre kell hoznia egy eszköz-konfigurációs profilt az Intune-ban, és konfigurálnia kell a biztonságos értékelés beállításait. Ez a cikk ismerteti azokat a beállításokat, amelyeket a vizsga alkalmazáshoz fog találni. 

Miután konfigurálta a profilt, rendeljen hozzá és telepítse azt a tanulók számára. 

A szolgáltatással kapcsolatos további információkért tekintse meg a [tesztelési alkalmazást az Intune-ban](education-settings-configure.md) .

## <a name="before-you-begin"></a>Előkészületek

[Eszközkonfigurációs profil létrehozása](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Tesztelési beállítások
Az eszköz konfigurációs profiljának létrehozása után nyissa meg a **profil típusát** , és válassza a **biztonságos értékelés (oktatás)** lehetőséget. Az alábbi lépéseket követve tesztelheti az alkalmazás beállításait. 


- **Fiók típusa**: Válassza ki, hogy a felhasználók hogyan jelentkezzenek be a tesztbe. A választható lehetőségek:
  - Azure AD-fiók
  - Tartományi fiók
  - Helyi fiók
  - Helyi vendég fiók: Csak a Windows 10 1903-es vagy újabb verzióját futtató eszközökön érhető el.    
- **Fiók felhasználóneve**: Adja meg annak a fióknak a felhasználónevét, amelyet a Take a test alkalmazással használ. A fiókokat a következő formátumban adhatja meg:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Fiók neve**: Helyi vendég fiók típusának beállításához adja meg a teszt alkalmazáshoz használt fiók nevét. A fiók neve csempeként fog megjelenni a bejelentkezési képernyőn. A teszt elindításához a tanulók a csempére kattintanak.  
- **Assessment URL-címe**: Adja meg annak a tesztnek az URL-címét, amelyet el szeretne végezni a felhasználók számára. Az URL-cím beszerzésével kapcsolatos további információkért tekintse meg a [teszt dokumentációját](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Nyomtatókapcsolat**: Válassza a **kötelező** lehetőséget, hogy csak a nyomtatóhoz csatlakozó eszközökről engedélyezze a teszt alkalmazáshoz való hozzáférést. Ez a beállítás azt is lehetővé teszi, hogy az alkalmazás nyomtatás gombja elérhető legyen a tesztek elfogadói számára. A **nincs konfigurálva** beállítás lehetővé teszi a tanulók számára az alkalmazás elérését olyan eszközökön, amelyek nem csatlakoznak a nyomtatóhoz.  
- **Képernyő figyelése**: Válassza az **Engedélyezés lehetőséget** a képernyő tevékenység monitorozásához, miközben a felhasználók tesztet vesznek. A **nincs konfigurálva beállítás** megakadályozza a képernyő figyelését a teszt során.
- **Szöveges javaslatok**: Válassza az **Engedélyezés lehetőséget** , hogy a teszt elfogadók megjelenjenek a szöveges javaslatok. **Nincs konfigurálva** a szöveges javaslatok blokkolása a felhasználók számára.

## <a name="next-steps"></a>További lépések

Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md), és [Figyelje annak állapotát](device-profile-monitor.md).
