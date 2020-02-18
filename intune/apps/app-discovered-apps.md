---
title: Felderített alkalmazások
titleSuffix: Microsoft Intune
description: Az eszközön található Intune által észlelt alkalmazások részleteinek megismerése.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: a727cf03f53ee003c27708a04ad475f0b370c487
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415002"
---
# <a name="intune-discovered-apps"></a>Intune által felderített alkalmazások

Az Intune által **felderített alkalmazások** az észlelt alkalmazások listája az Intune-ban regisztrált eszközökön a bérlőben. A bérlő szoftveres leltárként működik. A **felderített alkalmazások** egy külön jelentés az [alkalmazás telepítési](apps-monitor.md) jelentéseiből. A személyes eszközök esetében az Intune soha nem gyűjt információkat a nem felügyelt alkalmazásokról. A vállalati eszközökön minden alkalmazás felügyelt alkalmazás, vagy nem kerül be a jelentésbe. Az alábbi táblázat a várt viselkedést térképezi fel. Általánosságban elmondható, hogy a jelentés a regisztráció időpontjától számított 7 naponta frissül (a teljes bérlő heti frissítése nélkül). A frissítési időszak egyetlen kivétele a Win32-alkalmazások Intune felügyeleti bővítménye által gyűjtött alkalmazási információk, amelyeket 24 óránként gyűjtünk.

## <a name="monitor-discovered-apps-with-intune"></a>Észlelt alkalmazások figyelése az Intune-nal

Az Intune az észlelt alkalmazások összesített listáját jeleníti meg az Intune-ban regisztrált eszközökön a bérlőben.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **figyelő** > **felderített alkalmazások**elemet.

>[!NOTE]
>A felderített alkalmazások listáját exportálhatja egy. csv-fájlba a **felderített alkalmazások** ablaktáblán az **Exportálás** lehetőség kiválasztásával.
>
>A felderített Win32-alkalmazások esetében jelenleg nincsenek összesített darabszámok. Az ilyen típusú adattípusokat csak eszközönként lehet megtekinteni.

Az Intune a bérlőben lévő egyes eszközök felderített alkalmazásainak listáját is megjeleníti.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **minden eszköz**lehetőséget.
3. Válassza ki az eszközt.
4. Ha meg szeretné tekinteni az eszköz észlelt alkalmazásait, válassza a **figyelő** szakaszban a **felderített alkalmazások** elemet.

## <a name="details-of-discovered-apps"></a>Felderített alkalmazások részletei

Az alábbi lista tartalmazza az alkalmazás platformjának típusát, a személyes eszközök számára figyelt alkalmazásokat, a vállalat által birtokolt eszközökön figyelt alkalmazásokat, valamint a frissítési ciklust. További információ az Intune által támogatott alkalmazás-típusokról: [alkalmazások típusai Microsoft Intuneban](apps-add.md#app-types-in-microsoft-intune).

| Platform | Személyes tulajdonú eszközök esetén | Vállalati tulajdonú eszközök esetén | Frissítési ciklus |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Win32-alkalmazások) Megjegyzés: az [Intune felügyeleti bővítmény szükséges](intune-management-extension.md) az eszközön | Nem alkalmazható | Csak felügyelt alkalmazások | Az eszközök beléptetése 24 óránként |
| Windows 10 (modern alkalmazások) | Csak felügyelt modern alkalmazások | Az eszközre telepített összes modern alkalmazás | Az eszközök regisztrációja 7 naponta |
| Windows 8.1 | Csak felügyelt alkalmazások | Csak felügyelt alkalmazások | Az eszközök regisztrációja 7 naponta |
| Windows Phone 8 | Csak felügyelt alkalmazások | Csak felügyelt alkalmazások | Az eszközök regisztrációja 7 naponta |
| Windows RT | Csak felügyelt alkalmazások | Csak felügyelt alkalmazások | Az eszközök regisztrációja 7 naponta |
| iOS/iPadOS | Csak felügyelt alkalmazások | Az összes, az eszközön telepített alkalmazás | Az eszközök regisztrációja 7 naponta |
| macOS | Csak felügyelt alkalmazások | Az összes, az eszközön telepített alkalmazás | Az eszközök regisztrációja 7 naponta |
| Android: | Csak felügyelt alkalmazások | Az összes, az eszközön telepített alkalmazás | Az eszközök regisztrációja 7 naponta |
| Vállalati Android | Csak felügyelt alkalmazások | Csak a munkahelyi profilba telepített alkalmazások | Az eszközök regisztrációja 7 naponta |

> [!NOTE]
> - A Windows 10 hibrid Azure AD-hez csatlakoztatott eszközök, ahogyan az az alkalmazás-felügyeleti munkaterhelésben Configuration Managerban látható, jelenleg nem gyűjti az alkalmazás-leltárt az Intune felügyeleti bővítménnyel (IME), a fenti ütemterv szerint. A probléma megoldásához a Configuration Manager alkalmazás-felügyeleti munkaterhelését át kell kapcsolni az Intune-ba az eszközre való telepítéshez (IME szükséges a Win32 leltárhoz és a PowerShell telepítéséhez). Vegye figyelembe, hogy a viselkedés változásairól vagy frissítéseiről a [fejlesztés](../fundamentals/in-development.md) és/ [vagy Újdonságok](../fundamentals/whats-new.md)című cikkben van bejelentve.
> - A 2019 novembere előtt regisztrált, személyes tulajdonú macOS-eszközök továbbra is megjeleníthetik az eszközre telepített összes alkalmazást, amíg az eszközök nem lesznek regisztrálva.
> - Az Android Enterprise teljes körűen felügyelt és dedikált nem jeleníti meg a felderített alkalmazásokat.

A felderített alkalmazások száma nem feltétlenül egyezik a telepített állapotú alkalmazások számával. A lehetséges eltérések a következők:

- Egy telepített felügyelt alkalmazás célzási változása miatt előfordulhat, hogy a telepítés száma az állapot ablaktáblán csökken, de az észlelt alkalmazásokban továbbra is jelenteni kell.
- Egy bérlőn belül egyazon alkalmazás több példányának megjelölése esetén a felhasználók és eszközök esetleges átfedései miatt eltérés léphet fel a számok között. Az alkalmazás minden példánya számolja az átfedésben lévő felhasználókat, a felderített alkalmazások esetében azonban a felhasználók többszörösen lesznek számolva.
- A felderített alkalmazásokat és az alkalmazások állapotát a rendszer különböző időközönként gyűjti be, így emiatt is eltérések alakulhatnak ki az alkalmazások számát illetően.

## <a name="next-steps"></a>További lépések

- [Az alkalmazások típusai a Microsoft Intuneban](apps-add.md#app-types-in-microsoft-intune)
- [Alkalmazás-információk és-hozzárendelések figyelése Microsoft Intune](apps-monitor.md)
