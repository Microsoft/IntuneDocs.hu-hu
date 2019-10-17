---
title: Office 365 telepítése macOS-eszközökön a Microsoft Intune-nal
titleSuffix: ''
description: 'Ismertető: hogyan telepítheti az Office 365-alkalmazásokat macOS-eszközökön a Microsoft Intune használatával.'
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 796b1709260c7f507e78aa8404129fa996b59088
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72498809"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Az Office 365 hozzárendelése macOS rendszerű eszközökhöz a Microsoft Intune-nal

Ezzel az alkalmazástípussal könnyedén hozzárendelhet Office 365 2016-alkalmazásokat macOS rendszerű eszközökhöz. Ezzel az alkalmazástípussal a Word, az Excel, a PowerPoint, az Outlook és a OneNote alkalmazást telepítheti. Az alkalmazásokhoz a Microsoft automatikus frissítési (MAU) szolgáltatása is rendelkezésre áll, amely segít azokat biztonságosabban és naprakészebben tartani. A kívánt alkalmazások egyetlen alkalmazásként jelennek meg az Intune-konzol alkalmazáslistájában.


## <a name="before-you-start"></a>Előkészületek

Mielőtt elkezdené az Office 365 hozzáadását a macOS-eszközökhöz, érdemes figyelembe vennie az alábbiakat:

- Azokon az eszközökön, melyekre telepíti az alkalmazásokat, a macOS 10.10-es vagy újabb verziójának kell futnia.
- Az Intune csak a Mac Office 2016 csomagban megtalálható Office-alkalmazások hozzáadását támogatja.
- Ha bármely Office-alkalmazás meg van nyitva, amikor az Intune telepíti az alkalmazáscsomagot, előfordulhat, hogy elvesznek a felhasználók adatai a nem mentett fájlokból.

## <a name="create-and-configure-the-app-suite"></a>Az alkalmazáscsomag létrehozása és konfigurálása

Az Office 365 hozzáadása az **Alkalmazások** panelről.
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** tevékenységprofil panelén a **Kezelés** szakaszban válassza az **Alkalmazások** lehetőséget. 
5. Válassza a **Hozzáadás** elemet.
6. Az **Office 365 csomag** csoport **Alkalmazás típusa** listájáról válassza ki a **macOS** lehetőséget.
7. Az **Alkalmazáscsomag adatai** lehetőségre kattintva megtekintheti az alkalmazáscsomagra vonatkozó információkat.  
    Ezek alapján azonosíthatja az alkalmazáscsomagot az Intune-ban, és a felhasználók is ezek alapján találhatják meg azt a céges portálon.
8. Adja meg az alábbi adatokat:
    - **Csomag neve:** Itt adhatja meg az alkalmazáscsomag céges portálon megjelenő nevét. Ügyeljen arra, hogy minden megadott csomagnév egyedi legyen. Ha ugyanazt a csomagnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Csomag leírása:** Itt adhatja meg az alkalmazáscsomag leírását.
    - **Közzétevő:** Közzétevőként a Microsoft jelenik meg.
    - **Kategória:** Választhat egyet vagy többet a beépített kategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ez a beállítás megkönnyíti a Céges portálon kereső felhasználóknak az alkalmazás megtalálását.
    - **Megjelenítés kiemelt alkalmazásként a Céges portálon:** Ezzel a beállítással hangsúlyosan jelenítheti meg az alkalmazáscsomagot a céges portál főoldalán az alkalmazásokat kereső felhasználók számára.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő:** Fejlesztőként a Microsoft jelenik meg.
    - **Tulajdonos:** Tulajdonosként a Microsoft jelenik meg.
    - **Megjegyzések:** : Ide írhatja be igény szerint az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Embléma:** – Amikor a felhasználók a céges portálon keresnek, az alkalmazás mellett megjelenik az Office 365-embléma.
9. Válassza az **OK** gombot.
10. Az **Alkalmazás hozzáadása** panelen válassza a **Hozzáadás** lehetőséget.  
    A csomag egyetlen bejegyzés formájában jelenik meg az alkalmazások listájában.

## <a name="configure-app-assignments"></a>Alkalmazás-hozzárendelések konfigurálása

Ebben a lépésben az alkalmazáscsomag hozzárendeléseit konfigurálhatja. 

1. Az **Office 365** csomagot áttekintő panel megjelenítéséhez válassza az **Office 365** alkalmazáscsomagot az alkalmazások listáján.
2. Az **Office 365** panelen válassza a **Hozzárendelések** lehetőséget.
3. Az alkalmazáscsomagot használó csoport megadásához válassza a **Csoport hozzáadása** lehetőséget.  
    Ekkor megjelenik a **Csoport hozzáadása** panel.
4. A **Hozzárendelés típusa** beállítást állítsa **Kötelező** vagy **Elérhető** értékre.
5. Rendelje hozzá a csomagot a kijelölt csoportokhoz. További információ: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](apps-deploy.md).

    >[!Note]
    > Az Office 365 alkalmazáscsomag az Intune-on keresztül nem távolítható el.

5. A **Hozzárendelés** panelen kattintson az **OK** gombra.
6. A **Csoport hozzáadása** panelen kattintson az **OK** gombra.
7. A hozzárendelés véglegesítéséhez kattintson a **Mentés** lehetőségre.

## <a name="next-steps"></a>További lépések

- Az Office 365-alkalmazások Windows 10-es eszközökhöz való hozzáadásával kapcsolatos további tudnivalókért lásd: [Office 365 ProPlus 2016-alkalmazások hozzárendelése Windows 10-es eszközökhöz a Microsoft Intune-nal](apps-add-office365.md).
- Felhasználói csoportok esetében az alkalmazás-hozzárendelések belefoglalásáról és kizárásáról az [Alkalmazás-hozzárendelések belefoglalása vagy kizárása](apps-inc-exl-assignments.md) című témakörben talál további információkat.
