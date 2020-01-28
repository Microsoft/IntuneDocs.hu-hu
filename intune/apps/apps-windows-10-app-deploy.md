---
title: Windows 10-es alkalmazások központi telepítése Microsoft Intune használatával
titleSuffix: ''
description: Ismerkedjen meg a Windows 10-es alkalmazások Microsoft Intunesal elérhető telepítési forgatókönyvével.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 58f6c4e2c99c7e2c169014a71bb1cfd2bc85219b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755238"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Windows 10-es alkalmazások központi telepítése Microsoft Intune használatával 

A Microsoft Intune számos különböző típusú alkalmazás-és üzembe helyezési forgatókönyvet támogat a Windows 10-es eszközökön. Miután hozzáadott egy alkalmazást az Intune-hoz, azt felhasználókhoz és eszközökhöz rendelheti hozzá. Ez a cikk további részleteket tartalmaz a támogatott Windows 10-es forgatókönyvekről, valamint ismerteti az alkalmazások Windows rendszerre történő központi telepítésével kapcsolatos fontos tudnivalókat is. 

A Windows 10-es eszközökön támogatott alkalmazástípusok az üzleti alkalmazások és a Vállalati Microsoft Áruházbeli alkalmazások. A Windows-alkalmazások fájlkiterjesztés a következő:. msi,. Appx és. appxbundle.  

> [!Note]
> Modern alkalmazások telepítéséhez legalább a következőkre van szükség:
> - A Windows 10 1803-as verziójához: [2018. május 23. – KB4100403 (operációs rendszer: 17134.81-es build)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - A Windows 10 1709-es verziójához: [2018. június 21. – KB4284822 (operációs rendszer: 16299.522-es build)](https://support.microsoft.com/help/4284822).
>
> Csak a Windows 10 1803-es és újabb verziói támogatják az alkalmazások telepítését, ha nincs hozzárendelve elsődleges felhasználó.
>
> A LOB-alkalmazások telepítése nem támogatott a Windows 10 Home kiadásait futtató eszközökön.

## <a name="supported-windows-10-app-types"></a>Támogatott Windows 10-es alkalmazások típusai

Az egyes alkalmazás-típusok a Windows 10 azon verziója alapján támogatottak, amelyen a felhasználók futnak. A következő táblázat az alkalmazás típusát és a Windows 10 támogatását tartalmazza.

| Alkalmazás típusa | Otthoni | Pro | Üzleti | Enterprise | Oktatás | S üzemmód | Hololense | SurfaceHub | WCOS | Mobil |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  . MSI | Nem | Igen | Igen | Igen | Igen | Nem | Nem | Nem | Nem | Nem |
| . IntuneWin | Nem | Igen | Igen | Igen | Igen | 19H2 + | Nem | Nem | Nem | Nem |
| Office-C2R | Nem | Igen | Igen | Igen | Igen | Nem | Nem | Nem | Nem | Nem |
| LOB: APPX/MSIX | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen |
| MSFB offline | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen |
| Online MSFB | Igen | Igen | Igen | Igen | Igen | Igen | RS4 + | Igen | Igen | Igen |
| Webalkalmazások | Igen | Igen | Igen | Igen | Igen | Igen | Igen<sup>1 | Igen<sup>1 | Igen | Igen |
| Tár hivatkozása | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen | Igen |

<sup>1</sup> indítás csak a vállalati portálról.

> [!NOTE]
> Minden Windows-alkalmazás típusához regisztráció szükséges.

## <a name="windows-10-lob-apps"></a>Windows 10 LOB-alkalmazások

Windows 10 LOB-alkalmazásokat az Intune felügyeleti konzolra lehet aláírni és feltölteni. Ezek közé tartozhatnak a modern alkalmazások, például a Univerzális Windows-platform (UWP) alkalmazások és a Windows-alkalmazáscsomag (AppX), valamint a Win 32-alkalmazások, például a Microsoft Installer-csomagok egyszerű fájljai (MSI). A rendszergazdának manuálisan kell feltöltenie és telepítenie a LOB-alkalmazások frissítéseit. Ezeket a frissítéseket a rendszer automatikusan telepíti az alkalmazást telepítő felhasználói eszközökre. Nincs szükség felhasználói beavatkozásra, és a felhasználónak nincs hozzáférése a frissítésekhez. 

## <a name="microsoft-store-for-business-apps"></a>Vállalati Microsoft Áruházbeli alkalmazások

Az üzleti alkalmazások Microsoft Store a Microsoft Store for Business felügyeleti portálon vásárolt modern alkalmazások. Ezután szinkronizálva lesznek a Microsoft Intune a felügyelethez. Az alkalmazások lehetnek Online licenccel vagy offline licenccel rendelkezők. A Microsoft Store közvetlenül kezeli a frissítéseket, és nem igényel további műveletet a rendszergazda. Egy egyéni Uniform Resource Identifier (URI) használatával megakadályozhatja, hogy bizonyos alkalmazások frissítései is meglegyenek. További információ: [Vállalati alkalmazásfelügyelet – Alkalmazás automatikus frissítésének megakadályozása](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). A felhasználó emellett letilthatja a frissítéseket az összes Microsoft Store for Business-alkalmazáshoz az eszközön. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Üzleti alkalmazások kategorizálása Microsoft Store 
A Microsoft Store for Business alkalmazások kategorizálása: 

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás**lehetőséget. 
3. Válasszon egy Microsoft Store vállalati alkalmazáshoz. Ezután válassza a **tulajdonságok** > az **alkalmazás adatai** > **kategóriát**. 
4. Válasszon ki egy kategóriát.

## <a name="install-apps-on-windows-10-devices"></a>Alkalmazások telepítése Windows 10-es eszközökre
Az alkalmazás típusától függően a következő két módszer egyikével telepítheti az alkalmazást egy Windows 10-es eszközre:

- **Felhasználói környezet**: Ha egy alkalmazás felhasználói környezetben van telepítve, a felügyelt alkalmazás az adott felhasználó számára az eszközre kerül, amikor a felhasználó bejelentkezik az eszközre. Vegye figyelembe, hogy az alkalmazás telepítése nem sikerül, amíg a felhasználó be nem jelentkezik az eszközre. 
  - A modern üzletági alkalmazások és a Microsoft Store for Business-alkalmazások (online és offline) felhasználói környezetben is üzembe helyezhetők. Az alkalmazások támogatják mind a szükséges, mind az elérhető szándékot.
  - A felhasználói módban vagy kettős módban létrehozott Win32-alkalmazások felhasználói környezetben is üzembe helyezhetők, és mind a szükséges, mind a rendelkezésre álló szándékot támogatják. 
- **Eszköz környezete**: Ha az alkalmazás az eszköz kontextusában van telepítve, a felügyelt alkalmazás közvetlenül az Intune-ba települ az eszközre.
  - Csak a modern üzletági alkalmazások és az offline licenccel rendelkező Microsoft Store for Business alkalmazások helyezhetők üzembe az eszköz környezetében. Ezek az alkalmazások csak a szükséges szándékot támogatják.
  - A gépi mód vagy kettős mód használatával létrehozott Win32-alkalmazások az eszköz kontextusában telepíthetők, és csak a szükséges szándékot támogatják.

> [!NOTE]
> A kettős üzemmódú alkalmazásokként létrehozott Win32-alkalmazások esetében a rendszergazdának ki kell választania, hogy az alkalmazás felhasználói vagy gépi üzemmódú alkalmazásként fog működni az adott példánnyal társított összes hozzárendeléshez. A telepítési környezet nem módosítható hozzárendelés alapján.  

Ha egy alkalmazás az eszköz kontextusában van telepítve, a telepítés csak akkor lesz sikeres, ha az eszköz környezetét támogató eszközre irányul. Az eszközkörnyezetben történő üzembe helyezés ezen felül a következő feltételeknek tesz eleget:
- Ha egy alkalmazás az eszköz kontextusában van telepítve, és egy felhasználóra irányul, a telepítés sikertelen lesz. A következő állapot és hiba jelenik meg a felügyeleti konzolon:
  - Állapot: Sikertelen.
  - Hiba: A felhasználó nem célozhatja meg az eszköz környezetének telepítését.
- Ha egy alkalmazás az eszköz kontextusában van telepítve, de olyan eszközre irányul, amely nem támogatja az eszköz kontextusát, a telepítés sikertelen lesz. A következő állapot és hiba jelenik meg a felügyeleti konzolon:
  - Állapot: Sikertelen.
  - Hiba: A platform nem támogatja az eszközkörnyezetben történő telepítést. 

> [!Note]
> Ha egy adott központi telepítéssel ment egy alkalmazás-hozzárendelést, az adott hozzárendelés kontextusa nem módosítható, kivéve a modern alkalmazásokat. Modern alkalmazások esetén a kontextust a felhasználói környezetből az eszköz környezetére módosíthatja. 

Ha egyetlen felhasználó vagy eszköz házirendje ütközik, a következő prioritások érvényesek:
- Az eszközkörnyezetek szabályzatai magasabb prioritásúak a felhasználói környezetekéinél. 
- A telepítési szabályzatok magasabb prioritásúak az eltávolításiaknál.

További információért lásd: [Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban](apps-inc-exl-assignments.md). Az Intune-beli alkalmazástípusokat az [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md) című cikk ismerteti.

## <a name="next-steps"></a>További lépések

- [Alkalmazások társítása a csoportokhoz Microsoft Intune](apps-deploy.md)
- [Alkalmazások figyelése](apps-monitor.md)
