---
title: Jelszó alaphelyzetbe állítása Windows 10 rendszerű eszközökön az Azure-beli Microsoft Intune-nal | Microsoft Docs
description: A jelszó Windows rendszerű eszközökön történő alaphelyzetbe állításához telepítse a Microsoft PIN-kód-átállítási szolgáltatását és a Microsoft PIN-kód-átállítási ügynököt, hozzon létre eszközszabályzatot az Azure Active Directorybeli azonosító használatával, majd a Microsoft Intune segítségével állítsa alaphelyzetbe a jelszót az Azure Portalon.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b643ed41d01b70376dac32c26a66dcf9f9735ceb
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907219"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Jelszó alaphelyzetbe állítása Windows rendszerű eszközökön az Intune-nal

Alaphelyzetbe állíthatja a jelszót Windows rendszerű eszközökön. A jelszót alaphelyzetbe állító funkció a Microsoft PIN-kód-átállítási szolgáltatásával új jelszót hoz létre a Windows 10 Mobile verziót futtató eszközökön. 

## <a name="supported-platforms"></a>Támogatott platformok

- Alkotói frissítéses vagy újabb Windows 10 mobil verzió (Azure AD-hoz csatlakozott).

A következő platformok **nem** támogatottak:
- Windows
- iOS
- macOS
- Android:

## <a name="authorize-the-pin-reset-services"></a>PIN-kód-átállítási szolgáltatás engedélyezése

A jelszó Windows rendszerű eszközökön történő alaphelyzetbe állításához készítse elő a PIN-kód-átállítási szolgáltatást az Intune-bérlőn.

1. Nyissa meg a [Microsoft PIN-kód-átállítási szolgáltatás előállítása](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) lapot, és jelentkezzen be a bérlői rendszergazda fiókjával.
2. Az **Elfogadás** gombra kattintva járuljon hozzá, hogy a PIN-kód-átállítási szolgáltatás hozzáférjen a fiókjához: ![PIN-kód -átállítási szolgáltatás engedélykérésének elfogadása](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. Nyissa meg a [Microsoft PIN-kód-átállítási ügyfél előállítása](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) lapot, és jelentkezzen be a bérlői rendszergazda fiókjával. Az **Elfogadás** gombra kattintva járuljon hozzá, hogy a PIN-kód-átállítási ügyfél hozzáférjen a fiókjához.
4. Az [Azure Portalon](https://portal.azure.com) ellenőrizze, hogy a PIN-kód-átállítási szolgáltatás szerepel-e a vállalati alkalmazások listáján (összes alkalmazás): ![PIN-kód-átállítási szolgáltatás engedélyezése lap](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> Miután elfogadta a PIN-kód-átállítási kérelmet, `Page not found` üzenetet kaphat, de az is előfordulhat, hogy látszólag nem történik semmi. Ez a működésmód nem jelent hibát. Mindenképpen ellenőrizze, hogy a két PIN-kód-átállítási alkalmazás látható-e a bérlő számára.

## <a name="configure-windows-devices-to-use-pin-reset"></a>Windows-eszközök konfigurálása a PIN-kód alaphelyzetbe állításához

A felügyelt Windows rendszerű eszközökön az [Intune Windows 10-es egyéni eszközszabályzat](../configuration/custom-settings-windows-10.md) használatával konfigurálhatja a PIN-kód alaphelyzetbe állítását. A szabályzat az alábbi Windows szabályzatkonfigurációs szolgáltató (CSP) segítségével konfigurálható:

**Az eszközszabályzat használata** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

Cserélje le a *bérlői azonosítót* az [Azure Portalon](https://portal.azure.com), az Azure Active Directory **Tulajdonságok** területén található Azure Active Directory-azonosítóval.

Állítsa ennek a CPS-nek az értékét **True**-ra.

> [!TIP]
> Miután létrehozta a szabályzatot, üzembe helyezheti, vagy hozzárendelheti egy csoporthoz. A szabályzat felhasználói vagy eszközcsoportokhoz rendelhető hozzá. Ha felhasználói csoporthoz rendeli, a csoportban olyan felhasználók is lehetnek, akik más, például iOS rendszerű eszközökkel is rendelkeznek. Bár ezekre az eszközökre technikai értelemben nem alkalmazható a szabályzat, mégis megjelennek az állapotadatok között.

## <a name="reset-the-passcode"></a>A PIN-kód alaphelyzetbe állítása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431). 
2. Válassza az **Eszközök**, majd a **Minden eszköz** lehetőséget.
3. Válassza ki azt az eszközt, amelyen át szeretné állítani a jelszót. Az eszköz tulajdonságai között válassza a **jelszó alaphelyzetbe állítása**lehetőséget.
4. Válassza az **Igen** lehetőséget a megerősítéshez. A PIN-kód létrejön, és a következő hét nap folyamán megtekinthető a portálon.

## <a name="next-step"></a>További lépések

Ha a PIN-kódot nem sikerül alaphelyzetbe állítani, akkor a portál egy hivatkozást ajánl fel a további információkhoz.
