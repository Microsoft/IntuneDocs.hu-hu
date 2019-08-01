---
title: Windows 10-es alkalmazások telepítése a Microsoft Intune-nal
titleSuffix: ''
description: Ismerkedjen meg a Windows 10-es alkalmazások Microsoft Intunesal elérhető telepítési forgatókönyvével.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e46eae92dfa145f1fc2b38379285dbb45b24590
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/31/2019
ms.locfileid: "68680077"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Windows 10-es alkalmazások telepítése a Microsoft Intune-nal 

A Microsoft Intune jelenleg többféle alkalmazástípust és telepítési helyzetet támogat Windows 10 rendszerű eszközökön. Miután hozzáadott egy alkalmazást az Intune-hoz, azt felhasználókhoz és eszközökhöz rendelheti hozzá. A következő információ a támogatott Windows 10-es alkalmazási helyzetekkel kapcsolatos további részleteket mutat be. Ezenfelül alkalmazásoknak a Windowsban történő telepítésekor figyelembe veendő fontos tudnivalókat is tartalmaz. 

A Windows 10-es eszközökön támogatott alkalmazástípusok az üzleti alkalmazások és a Vállalati Microsoft Áruházbeli alkalmazások. A windowsos alkalmazások fájlnévkiterjesztései közé tartozik az **.msi**, az **.appx** és az **.appxbundle** is.  

> [!Note]
> A modern alkalmazások telepítéséhez minimálisan szükséges Windows 10-frissítések a következők:
> - A Windows 10 1803-as verziójához: [2018. május 23. – KB4100403 (operációs rendszer: 17134.81-es build)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - A Windows 10 1709-es verziójához: [2018. június 21. – KB4284822 (operációs rendszer: 16299.522-es build)](https://support.microsoft.com/help/4284822).
>
> Csak a Windows 10 1803 és újabb verziók támogatják az alkalmazások telepítését, ha nincs elsődleges felhasználó társítva.

## <a name="windows-10-line-of-business-apps"></a>Windows 10-es üzletági alkalmazások

A Windows 10-es üzletági alkalmazások alá vannak írva és fel vannak töltve az Intune felügyeleti konzoljára. Lehetnek olyan modern alkalmazások, mint az Univerzális Windows-platform (UWP) alkalmazások és a Windows-alkalmazáscsomagok (AppX), de Win 32-alkalmazások is, amilyenek az egyszerű Microsoft Installer telepítőcsomag-fájlok (MSI). Az üzletági alkalmazások frissítéseit minden alkalommal a rendszergazdának kell feltöltenie és üzembe helyeznie. Az üzembe helyezett frissítések felhasználói beavatkozás nélkül, automatikusan telepítve lesznek azoknak a végfelhasználóknak az eszközein, akik telepítették az alkalmazást. A felhasználó nem avatkozhat be a frissítésekbe. 

## <a name="microsoft-store-for-business-apps"></a>Vállalati Microsoft Áruházbeli alkalmazások

Az üzleti alkalmazások Microsoft Store a Microsoft Store for Business felügyeleti portálon vásárolt modern alkalmazások, amelyek ezután szinkronizálva lesznek a felügyelethez Microsoft Intune. Az alkalmazások lehetnek **online licencelésűek** vagy **offline licencelésűek**. A Microsoft Store for Business alkalmazások frissítéseit közvetlenül a Microsoft Store kezeli, és nincs szükség további beavatkozásra, a rendszergazdára. Egy egyéni Uniform Resource Identifier (URI) használatával megakadályozhatja, hogy bizonyos alkalmazások frissítései is meglegyenek. További információ: [Vállalati alkalmazásfelügyelet – Alkalmazás automatikus frissítésének megakadályozása](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). Az eszközön a végfelhasználó is letilthatja az eszközön lévő összes Vállalati Microsoft Áruházbeli alkalmazás frissítéseit. 

## <a name="installing-apps-on-windows-10-devices"></a>Alkalmazások telepítése Windows 10-es eszközökön
Az alkalmazás típusától függően az alkalmazás két módszer egyikével telepíthető Windows 10-es eszközre:

- **Felhasználói környezet**: Ha egy alkalmazás felhasználói környezetben van telepítve, akkor a felügyelt alkalmazás a felhasználó számára az eszközön fog települni, amikor a felhasználó bejelentkezik az eszközre. Lényeges, hogy az alkalmazás telepítése csak akkor lesz sikeres, ha a felhasználó bejelentkezik az eszközre. 
  - A modern üzletági és Microsoft Áruházbeli alkalmazások (online vagy offline) telepíthetők felhasználói környezetben, és az Elérhető és Szükséges hozzárendelés-típust is támogatják.
  - A **felhasználói módban** vagy **kettős módban** készült Win32-alkalmazások felhasználói környezetben helyezhetők üzembe, és egyaránt támogatják a **Kötelező** és az **Elérhető** szándékmegjelölésű telepítést. 
- **Eszköz környezete**: Ha egy alkalmazás az eszköz kontextusában van telepítve, a felügyelt alkalmazás közvetlenül az eszközre lesz telepítve az Intune-ban.
  - Csak a modern üzletági alkalmazások és az offline licenccel rendelkező Microsoft Store for Business alkalmazások helyezhetők üzembe az eszköz környezetében, és csak a szükséges szándékot támogatják.
  - A **Számítógép módban** vagy **kettős módban** készült Win32-alkalmazások felhasználói környezetben helyezhetők üzembe, és csak a **Kötelező** szándékmegjelölésű telepítést támogatják.

> [!NOTE]
> A **kettős módban** készült Win32-alkalmazások esetén Önnek (a rendszergazdának) kell kiválasztania, hogy az alkalmazás **felhasználói módban** vagy **Számítógép módban** fog-e működni az adott példányhoz kapcsolódó összes hozzárendelés esetében. Az üzembe helyezési környezet hozzárendelésenként változtatható.  

Ha egy alkalmazás eszközkörnyezetben van üzembe helyezve, a telepítés csak akkor lesz sikeres, ha célja az eszközkörnyezetet támogató eszköz. Az eszközkörnyezetben történő üzembe helyezés ezen felül a következő feltételeknek tesz eleget:
- Ha egy alkalmazás eszközkörnyezetben van üzembe helyezve, célja pedig egy felhasználó, akkor a telepítés sikertelen lesz és a következő állapot- és hibaüzenet jelenik meg a felügyeleti konzolon:
  - Állapot: Sikertelen.
  - Hiba: A felhasználó nem célozhatja meg az eszköz környezetének telepítését.
- Ha egy alkalmazás eszközkörnyezetben van üzembe helyezve, célja azonban egy olyan eszköz, amely nem támogatja az eszközkörnyezetet, akkor a telepítés sikertelen lesz, és a következő állapot- és hibaüzenet jelenik meg a felügyeleti konzolon:
  - Állapot: Sikertelen.
  - Hiba: Ez a platform nem támogatja az eszközök környezetének telepítését. 

> [!Note]
> Ha egy adott üzembe helyezés alkalmazás-hozzárendelése már ki van mentve, ennek a hozzárendelésnek a környezete többé nem módosítható, csak a modern alkalmazások esetén. Modern alkalmazások esetén a környezet felhasználóiról eszközkörnyezetre módosítható. 

Ha egy felhasználó/eszköz esetében a szabályzatok ellentmondanak, az érvényre jutó szabályzat a következő prioritások alapján lesz meghatározva:
- Az eszközkörnyezetek szabályzatai magasabb prioritásúak a felhasználói környezetekéinél. 
- A telepítési szabályzatok magasabb prioritásúak az eltávolításiaknál.

Alkalmazásoknak a Microsoft Intune használatával való hozzárendeléséről az [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](apps-deploy.md) és az [Alkalmazás-hozzárendelések belefoglalása vagy kizárása a Microsoft Intune-ban](apps-inc-exl-assignments.md) című cikkek tartalmaznak további információt. Az Intune-beli alkalmazástípusokat az [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md) című cikk ismerteti.

## <a name="next-steps"></a>További lépések

- További információ az alkalmazások csoportokhoz rendeléséről: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](apps-deploy.md).
- Alkalmazás-hozzárendelések figyelésével kapcsolatos további tudnivalókért lásd: [Alkalmazások figyelése](apps-monitor.md).
