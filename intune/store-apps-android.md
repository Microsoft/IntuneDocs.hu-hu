---
title: Androidos áruházbeli alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Ismerje meg, hogyan adhat hozzá androidos áruházbeli alkalmazásokat a Google Play áruházból a Microsoft Intunehoz.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93ea735121432c99c93ffe35c96c344160de3e22
ms.sourcegitcommit: 6c74ff568267d85fd1d44fda75e3e24ead87cb2b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/28/2019
ms.locfileid: "71303149"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Androidos áruházbeli alkalmazások hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mielőtt az alkalmazást hozzárendelné egy eszközhöz vagy felhasználói csoporthoz, az eszközt először hozzá kell adnia a Microsoft Intune-hoz. 

## <a name="add-an-app"></a>Alkalmazás hozzáadása

A következő módon adhat hozzá Android-áruházból származó alkalmazást az Intune-hoz az Azure Portalon:

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** tevékenységprofil panelén a **Kezelés** szakaszban válassza az **Alkalmazások** lehetőséget.
5. Válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazás hozzáadása** panelen az elérhető **Áruházbeli alkalmazások** típusai közül válassza az **Android** lehetőséget.
7. Az alkalmazás adatainak megadásához válassza a **Konfigurálás** lehetőséget, majd adja meg a következő adatokat. Android-alkalmazások esetén keresse fel a [Google Play áruházat](https://play.google.com/store), és keresse meg az üzembe helyezni kívánt alkalmazást. Válassza ki az alkalmazást, és jegyezze fel az alkalmazás adatait. A választott alkalmazástól függően előfordulhat, hogy egyes értékek automatikusan ki vannak töltve a panelen:
    - **Név**: Adja meg az alkalmazásnak a vállalati portálon megjelenítendő nevét. Gondoskodjon róla, hogy az alkalmazás neve egyedi legyen. Ha két alkalmazás neve megegyezik, a felhasználók csak az egyik alkalmazást fogják látni a céges portálon.
    - **Description** (Leírás): Adja meg az alkalmazás leírását. A leírás a céges portálon jelenik meg a felhasználók számára.
    - **Közzétevő**: Itt adhatja meg az alkalmazás kiadójának nevét.
    - **AppStore URL-cím**: Adja meg a létrehozni kívánt alkalmazás alkalmazás-áruházbeli URL-címét.
    - **Minimális operációs rendszer**: A listából válassza ki az operációs rendszer legkorábbi verzióját, amelyre az alkalmazás telepíthető. Ha az alkalmazást régebbi operációs rendszerrel rendelkező eszközhöz rendelik hozzá, akkor nem lesz telepítve.
    - **Kategória**: Szükség esetén kiválaszthat egy vagy több beépített alkalmazás-kategóriát vagy egy Ön által létrehozott kategóriát is. Ezzel megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: Ezzel a beállítással Kiemelt módon jelenítheti meg az App Suite-t a vállalati portál főoldalán, amikor a felhasználók megkeresik az alkalmazásokat. Az elérhető szándékkal üzembe helyezett alkalmazásokra vonatkozik.
    - **Információs URL-cím**: Nem kötelező: megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi URL-cím**: Nem kötelező: megadhatja az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő**: Igény szerint megadhatja az alkalmazás-fejlesztő nevét.
    - **Tulajdonos**: Igény szerint megadhatja az alkalmazás tulajdonosának nevét (például *HR-osztály*).
    - **Megjegyzések**: Igény szerint megadhatja az alkalmazáshoz társítandó megjegyzéseket.
    - **Embléma**: Igény szerint feltöltheti az alkalmazáshoz hozzárendelni kívánt ikont is. Ez az alkalmazásikon jelenik meg a céges portálon böngésző felhasználók számára.
8. Kattintson az **OK** gombra.
9. Válassza a **Hozzáadás** lehetőséget.

A létrehozott alkalmazás megjelenik az alkalmazáslistában, ahol hozzárendelheti a kiválasztott csoportokhoz. 

## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
