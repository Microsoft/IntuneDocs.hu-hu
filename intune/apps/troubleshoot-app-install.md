---
title: Alkalmazások telepítésével kapcsolatos problémák elhárítása
titleSuffix: Microsoft Intune
description: A Microsoft Intune hibaelhárítási paneljével elháríthatja az alkalmazások telepítésével kapcsolatos problémákat.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a7216dedf67f6ee9fc8d899756f789d1c0dccc6
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415499"
---
# <a name="troubleshoot-app-installation-issues"></a>Alkalmazások telepítésével kapcsolatos problémák elhárítása

A Microsoft Intune MDM által felügyelt eszközökön néha sikertelenek lehetnek az alkalmazástelepítések. Ilyen esetekben nem könnyű megérteni a hiba okát, illetve elhárítani azt. A Microsoft Intune olyan adatokat szolgáltat az alkalmazástelepítésbeli hibákról, amelyekkel az ügyfélszolgálati operátorok és az Intune-rendszergazdák megtekinthetik az alkalmazásadatokat, és reagálhatnak az ügyfelek kérelmeire. Az Intune hibaelhárítási panelje megjeleníti a hibák adatait, így a felhasználói eszközökön kezelt alkalmazások információit is. Az alkalmazások végpontok közötti életciklusához tartozó adatok a **Felügyelt alkalmazások** panelen, az egyes eszközök alatt tekinthetők meg. Itt megtekintheti a telepítési problémákat, például az alkalmazás létrehozási, módosítási és célzási dátumát, valamint az eszközökre való továbbításának dátumát. 

> [!NOTE]
> Az alkalmazások telepítésével kapcsolatos hibakódokról további információt az [Intune-alkalmazás telepítési hibáinak leírása](~/apps/app-install-error-codes.md)című témakörben talál.

## <a name="app-troubleshooting-details"></a>Alkalmazás-hibaelhárítás részletei

Az Intune az adott felhasználók eszközein telepített alkalmazások alapján szolgáltat hibaelhárítási információkat.

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza a **hibakeresés + támogatás**lehetőséget.
4. A felhasználó kiválasztásához kattintson a **Felhasználó kijelölése** lehetőségre. Ekkor megjelenik a **Felhasználók kijelölése** panel.
5. Jelöljön ki egy felhasználót a megfelelő név vagy e-mail cím beírásával. Kattintson a **Kijelölés** gombra a lap alján. A felhasználóval kapcsolatos hibaelhárítási információ a **Hibaelhárítás** panelen jelenik meg. 
6. Az **Eszközök** listában jelölje ki azt az eszközt, amelyen hibaelhárítást szeretne végezni.
    ![Az Intune Hibaelhárítás panelje.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. A kijelölt eszköz paneljén válassza a **Felügyelt alkalmazások** lehetőséget. Megjelenik a felügyelt alkalmazások listája.
    ![Az Intune által kezelt eszköz adatai.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Válassza ki azt az alkalmazást, amelynél hibát jelez a **Telepítés állapota**.
    ![A kiválasztott alkalmazás, amelynél megjelennek a telepítési hiba adatai.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > Ugyanazt az alkalmazást eltérő alkalmazásműveleti szándékkal rendelhetik hozzá különböző csoportokhoz. Egy alkalmazás feloldott szándéka például **Kizárva** értéket jelez, ha az alkalmazás ki van zárva egy felhasználó számára az alkalmazás-hozzárendelés során. További információ: [Alkalmazások hozzárendelési ütközéseinek feloldása](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Ha egy szükséges alkalmazás telepítése sikertelen, akkor Ön vagy a segélyszolgálat szinkronizálhatja az eszközt, és újra megkísérelheti az alkalmazás telepítését.

Az alkalmazástelepítési hiba információi ismertetik a problémát. Ezen adatok segítségével meghatározhatja a probléma feloldásához szükséges műveletet. Az alkalmazások telepítési problémáinak elhárításával kapcsolatos további információkért lásd az [Android-alkalmazások telepítési hibáit](app-install-error-codes.md#android-app-installation-errors) és az [iOS-alkalmazások telepítési hibáit](app-install-error-codes.md#ios-app-installation-errors)ismertető témakört.

> [!Note]  
> A **Hibaelhárítás** panel a böngészőben a [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) címen is elérhető.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>A felhasználói csoport megcélzó alkalmazásának telepítése nem érhető el az eszközön
Az alkalmazások telepítésekor a következő műveleteket kell figyelembe venni:
- Ha az alkalmazás nem jelenik meg a Céges portálban, győződjön meg arról, hogy az alkalmazás **elérhető** szándékkal van telepítve, és hogy a felhasználó a céges portálhoz fér hozzá az alkalmazás által támogatott típusú eszközhöz.
- A Windows BYOD eszközökhöz a felhasználónak munkahelyi fiókot kell hozzáadnia az eszközhöz.
- Ellenőrizze, hogy a felhasználó meghaladja-e a HRE-eszköz korlátját:
  1. Navigáljon [Azure Active Directory eszköz beállításaihoz](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Jegyezze fel a **maximális eszközök felhasználónként**való beállításának értékét.
  3. Navigáljon [Azure Active Directory felhasználóhoz](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Válassza ki az érintett felhasználót, és kattintson az **eszközök**elemre.
  5. Ha a felhasználó túllépi a beállított korlátot, törölje azokat az elavult rekordokat, amelyekre már nincs szükség.
- IOS/iPadOS DEP-eszközök esetén győződjön meg arról, hogy a felhasználó **regisztrálva van a felhasználó által** az Intune-eszköz áttekintés paneljén. Ha a NA-t jeleníti meg, akkor telepítsen egy konfigurációs házirendet a Intune Céges portálhoz. További információ: [a céges portál alkalmazás konfigurálása](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Win32-alkalmazás telepítésének hibaelhárítása

Válassza ki az Intune felügyeleti bővítmény használatával üzembe helyezett Win32-alkalmazást. Ha a Win32-alkalmazás telepítése sikertelen, a **naplók összegyűjtése** lehetőség kiválasztásával végezhető el. 

> [!IMPORTANT]
> A **naplók összegyűjtése** beállítás nem lesz engedélyezve, ha a Win32-alkalmazás sikeresen telepítve van az eszközön.<p>A Win32-alkalmazások naplózási adatainak összegyűjtéséhez az Intune felügyeleti bővítményét telepíteni kell a Windows-ügyfélre. Az Intune felügyeleti bővítmény akkor települ, ha PowerShell-parancsfájlt vagy Win32-alkalmazást telepít egy felhasználói vagy eszköz biztonsági csoportba. További információ: [Intune felügyeleti bővítmény – előfeltételek](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Naplófájl gyűjtése

A Win32-alkalmazás telepítési naplóinak összegyűjtéséhez kövesse az [alkalmazás hibaelhárítási részletei](troubleshoot-app-install.md#app-troubleshooting-details)című szakasz lépéseit. Ezután folytassa a következő lépésekkel:

1. Kattintson a **naplók összegyűjtése** lehetőségre a **telepítés részletei** ablaktáblán.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. A naplófájlok gyűjtési folyamatának megkezdéséhez adja meg a fájl elérési útját, és kattintson **az OK**gombra.

    > [!NOTE]
    > A naplózási gyűjtemény kevesebb mint két órát vesz igénybe. Támogatott fájltípusok: *. log,. txt,. dmp,. cab,. zip,. XML,. evtx és. evtl*. Legfeljebb 25 fájlelérési út engedélyezett.

3. A naplófájlok gyűjtése után kiválaszthatja a **naplók** hivatkozást a naplófájlok letöltéséhez.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Ekkor megjelenik egy értesítés, amely az alkalmazás naplójának sikeres sikerességét jelzi.

#### <a name="win32-log-collection-requirements"></a>A Win32-naplók gyűjtésének követelményei

A naplófájlok összegyűjtéséhez konkrét követelményekre van szükség:

- Meg kell adnia a naplófájl teljes elérési útját. 
- Megadhatja a naplózási gyűjtemény környezeti változóit, például a következőket:<br>
  *% PROGRAMFILES%,% PROGRAMDATA%% NYILVÁNOS%,% WINDIR%,% TEMP%,% TMP%*
- Csak a pontos fájlkiterjesztések engedélyezettek, például:<br>
  *. log,. txt,. dmp,. cab,. zip,. XML*
- A feltölteni kívánt maximális naplófájl 60 MB vagy 25 fájl, amelyik előbb megtörténik. 
- A Win32-alkalmazás telepítési naplójának gyűjteménye engedélyezve van azon alkalmazások esetében, amelyek megfelelnek a szükséges, elérhető és eltávolított alkalmazás-hozzárendelési szándéknak.
- A tárolt naplók titkosítva vannak a naplókban tárolt személyes azonosításra alkalmas adatok védelemmel.
- A Win32-alkalmazások támogatási jegyének megnyitása közben csatolja a kapcsolódó hibák naplóit a fenti lépésekkel.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>A Microsoft Áruházból származó alkalmazások hibáinak elhárítása

A [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (A Microsoft Áruházbeli alkalmazások csomagolási, telepítési és lekérdezési hibáinak elhárítása) című cikkben foglaltak segítenek elhárítani az alkalmazásoknak a Microsoft Áruházból akár Intune-nal, akár más módon történő telepítésekor tapasztalt gyakori problémákat.

## <a name="app-troubleshooting-resources"></a>Alkalmazás-hibaelhárítási erőforrások
- [A Visio és a Project üzembe helyezése az Office Pro Plus üzembe helyezésének részeként](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Végezze el az Intune-telepítéssel telepített MSfB alkalmazások Windows 10 1903 rendszeren való telepítését.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [MSI-alkalmazások központi telepítésének hibaelhárítása Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Ajánlott eljárások a szoftverek terjesztéséhez a klasszikus Intune-ban Windows PC-ügynök](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>További lépések

- További információt az Intune hibaelhárításáról a [Segítségnyújtás a céges felhasználóknak a hibaelhárítási portál használatával](../fundamentals/help-desk-operators.md) című témakörben talál. 
- Ismertető a Microsoft Intune esetleges ismert problémáiról. További információ: az [Intune-ügyfél sikeressége](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md).
