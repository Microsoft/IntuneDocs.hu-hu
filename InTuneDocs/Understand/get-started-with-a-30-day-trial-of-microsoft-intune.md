---
title: "Útmutató az Intune próbaverziójához | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 4af13629986e7cef814104f3d1f298eb2be240ac
ms.openlocfilehash: 26ecc3dfe8816da9f30829901d929af53b1bedc0


---

# Útmutató az Intune próbaverziójához
A Microsoft Intune 30 napos ingyenes próbaidőszakának a mobileszközök és számítógépek kezelése céljából történő beállítása gyorsan és könnyen elvégezhető. Néhány egyszerű lépésben felvehet akár 100 felhasználót vagy eszközt is, beállíthatja a csoportokat, konfigurálhatja a megfelelőségi szabályzatokat, valamint regisztrálhatja az eszközöket és a számítógépeket, és megkezdheti a felügyeletüket.

Ebben a témakörben megismerkedhet az Intune-próbaidőszak használatának első lépéseivel, és a szolgáltatás áttekintése révén kiértékelheti az Intune szolgáltatásait és funkcióit.

Nézze meg ezt az ötperces bemutatóvideót, amelyből megtudhatja, milyen egyszerűen megkezdheti a Microsoft Intune ingyenes próbaverziójának használatát, és ezzel eszközei felügyeletét. A videó első része egy olyan portált említ, amely már nem aktuális. Noha egy másik portált fog használni, a lépések lényegileg ugyanazok lesznek. A portálról további információkat [itt](https://docs.microsoft.com/intune/deploy-use/account-portal-merged-with-Office-365) talál.

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## Előkészületek
Az Intune használatának megkezdéséhez a következőkre lesz szüksége:

-   Silverlight-kompatibilis webböngészőt tartalmazó eszköz, amellyel meg tudja nyitni a webhelyeket, amelyeken Intune-felhasználói fiókokat kíván létrehozni (az **Office 365 felügyeleti központját**), és azokat, amelyeken kezelheti az eszközöket, csoportokat és házirendeket (az **Intune felügyeleti konzolját**).

-   Webböngészőt tartalmazó második eszköz, amellyel tesztelheti, hogy az Intune-felhasználók hogyan fogják regisztrálni és kezelni eszközekeit a Vállalati portál használatával. Azt is tesztelni fogja, hogy a felhasználók miként telepítik az alkalmazásokat, és kérnek segítséget a rendszergazdáktól. Ha nem rendelkezik második eszközzel, használja az Intune-felügyelethez használt böngésző „privát böngészés” funkcióját (az Internet Explorerben például válassza az **Eszközök** &gt; **InPrivate-böngészés** lehetőséget).

-   Ha van Microsoft Online Services-fiókja, szüksége lesz a fiók rendszergazdájának hitelesítő adataira. Ha nincs ilyen fiókja, vagy ha az adott Intune-bérlőt csak kiértékelési célokra szeretné használni, nincs szükség a bérlői rendszergazda hitelesítésére.

-   Ha iOS- vagy Windows Phone-eszközöket fog kezelni az Intune próbaverziójával, a tanúsítványok lekéréséhez tanúsítványokra (vagy kulcsokra) és fiókokra lesz szüksége (lásd az alábbi táblázatot). Android-eszközök esetén nincs szükség külön tanúsítványokra.

    |Platfésm|Tanúsítványokkal kapcsolatos követelmények|További információ|
    |------------|----------------------------|--------------------|
    |Windows Phone 8.1 és Windows Phone 8 |A Windows Phone 8.1 azon felhasználói számára, akik az Áruházból telepítik a Vállalati portál alkalmazást, nem szükséges tanúsítvány. Windows Phone 8.0 használata esetén, illetve abban az esetben, ha a Vállalati portál alkalmazást az Intune-szolgáltatással kívánja Windows Phone 8.1-eszközre telepíteni, Symantec-tanúsítvány szükséges.|Ez az útmutató azt feltételezi, hogy az Ön felhasználói az Áruházból származó Vállalati portál alkalmazást Windows Phone 8.1 vagy újabb rendszerű eszközön telepítik. A Windows Phone 8.0 támogatásával kapcsolatos információkat lásd: [Windows Phone rendszerű telefonok kezelésének beállítása a Microsoft Intune-nal](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune).|
    |Windows 10, Windows RT 8.1, Windows RT vagy Windows 8.1 rendszerű eszközök|A Windows RT és Windows rendszerű eszközök regisztrálásának nincsenek tanúsítványokkal kapcsolatos követelményei.|[Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](/Intune/Deploy-Use/install-the-windows-pc-client-with-microsoft-intune).|
    |iOS 7.1 vagy újabb|Szerezzen be egy tanúsítványt az Apple leküldéses értesítési szolgáltatáshoz.|Igényeljen Apple Push Notification szolgáltatásbeli tanúsítványt az Apple-től a következő helyen leírtak szerint: [Az iOS és Mac kezelésének beállítása a Microsoft Intune-nal](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).|

## Az Intune 30 napos kipróbálásához szükséges lépések
- [1. lépés: Bejelentkezés, vagy regisztráció a 30 napos próbaverzióra](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md). Mielőtt regisztrál vagy bejelentkezik az Intune-ba, fontolja meg, hogy egy meglévő fiókot szeretne-e használni, vagy inkább létrehoz egy ideiglenes fiókot, amelyet kizárólag a Microsoft Intune 30 napos kipróbálásához használ.
- [2. lépés: Felhasználók hozzáadása](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md). A fiók beállítását követően adja hozzá egyesével a felhasználói fiókokat, vagy használja az Intune tömeges hozzáadási funkcióját (az utasításokat lásd alább). Mielőtt hozzáfogna, fontos tisztában lennie azzal, hogy az Intune miként kezeli a rendszergazdai fiókokat.
- [3. lépés: Csoportok létrehozása a felhasználók és eszközök rendszerezéséhez](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md). Az Intune csoportjai az eszközök és felhasználók rendkívül rugalmas kezelését teszik lehetővé. A szervezet saját igényeinek megfelelően csoportokat is létrehozhat (például földrajzi hely, részleg vagy hardverjellemzők alapján), amelyekkel számos felügyeleti feladatot elvégezhet, a felhasználói csoportok számára beállított házirendektől az alkalmazások eszközcsoportokra való telepítéséig.
- [4. lépés: Szabályzatok létrehozása és alkalmazások közzététele](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md). Az Intune-szabályzatok lehetőséget biztosítanak a mobileszközök biztonsági beállításainak kezelésére, a Windows tűzfal és az Endpoint Protection szolgáltatás számítógépeken alkalmazott beállításainak karbantartására, illetve alkalmazások telepítésére.
- [5. lépés: Mobileszközök regisztrálása és alkalmazások telepítése](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md). Az Intune-szolgáltatással történő mobileszköz-kezelés beállításához mobileszköz-kezelő szolgáltatót kell beállítania, engedélyeznie kell a mobileszköz-kezelést az adott eszközplatformhoz, majd regisztrálnia kell az eszközöket a Vállalati portál alkalmazás segítségével. Ezután telepítheti a közzétett Microsoft Skype alkalmazást.
- [6. lépés: Egyéb beállítások és kiegészítő funkciók](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md). Adja meg, hogyan szeretné használni a riasztásokat, jelentéseket és az Intune további funkcióit szervezete igényeinek megfelelően.
- [7. lépés: További lépések](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md). Készüljön fel a fizetett Intune-előfizetésre történő átállásra, és használja ki az Intune FastTrack Center által kínált előnyöket.


### További lépések
Itt az ideje, hogy megkezdje a 30 napos próba-előfizetés használatát!

>[!div class="step-by-step"]
[**Regisztráció az Intune-ban** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### További információ
[Az Intune bemutatása](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)



<!--HONumber=Jun16_HO4-->


