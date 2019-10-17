---
title: Oktatóanyag – a Slack konfigurálása az Intune és az alkalmazások konfigurációjának használatára
titleSuffix: Microsoft Intune
description: Ebben az oktatóanyagban a Slack konfigurálását fogja beállítani az Intune és az alkalmazások konfigurációjának használatához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86e9d100847641064f472f0c3da0c9ec694f72dd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72496720"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Oktatóanyag: a Slack konfigurálása az Intune és az alkalmazások konfigurációjának használatára

A Slack egy csoportmunka-alkalmazás, amelyet Microsoft Intune használhat.   

Ebben az oktatóanyagban a következőket fogja elsajátítani:
> [!div class="checklist"]
> - Állítsa be az Intune-t nagyvállalati mobilitási felügyeleti (ã) szolgáltatóként a Slack Enterprise Griden. A Grid terv munkaterületeinek hozzáférését korlátozhatja az Intune által felügyelt eszközökre.
> - Alkalmazás-konfigurációs szabályzatok létrehozásával kezelheti az iOS-es és az androidos munkahelyi profilú eszközökhöz készült Slack-alkalmazáshoz készült Slack alkalmazást.
> - Hozzon létre Intune-os megfelelőségi szabályzatokat az Android és iOS rendszerű eszközök feltételeinek megadásához.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon ingyenes próbafiókot](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
Az oktatóanyag végrehajtásához szüksége lesz egy tesztelési bérlőre a következő előfizetésekkel:
- Prémium szintű Azure Active Directory ([ingyenes próbaverzió](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune-előfizetés ([ingyenes próbaverzió](../fundamentals/free-trial-sign-up.md))

A [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) -csomagra is szüksége lesz.

## <a name="configure-your-slack-enterprise-grid-plan"></a>A Slack Enterprise Grid-csomag konfigurálása
A Slack [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) [utasításait](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) követve kapcsolja be a (z) a Slack Enterprise Grid-csomaghoz az

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba
Jelentkezzen be az [Intune-ba](https://go.microsoft.com/fwlink/?linkid=2090973) globális rendszergazdaként vagy Intune-beli szolgáltatásadminisztrátorként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>A Slack beállítása az iOS-eszközökön
Adja hozzá az iOS-alapú alkalmazáshoz készült Slack for az Intune-bérlőt, és hozzon létre egy alkalmazás-konfigurációs szabályzatot, amely lehetővé teszi, hogy a szervezet iOS-felhasználói hozzáférhessenek az Intune-hoz az Intune-nal

### <a name="add-slack-for-emm-to-intune"></a>Tartalékidő hozzáadása az Intune-hoz
Adja hozzá a Slack for az az az az az a-hez, amely felügyelt iOS-alkalmazás az Intune-ban, és rendeljen Az alkalmazások platform-specifikusak, ezért hozzá kell adnia egy külön Intune-alkalmazást a Slack-felhasználók számára az Android-eszközökön.
1. Az Intune-ban válassza a **Client apps** > **alkalmazások** > **Hozzáadás**elemet.
2. Az alkalmazás típusa területen válassza az **áruház alkalmazás-iOS**lehetőséget.
3. Válassza a **Keresés az App Store-ban** lehetőséget. Adja meg a "Slack for ír" keresési kifejezést, és válassza ki az alkalmazást.
4. Válassza **az** alkalmazásadatok lehetőséget, és konfigurálja az összes módosítást, ahogy az illik.
5. Válassza a **Hozzáadás** elemet.
6. A keresősáv mezőben adja meg a "Slack for a" kifejezést, és válassza ki az imént hozzáadott alkalmazást.
7. A kezelés területen válassza a **hozzárendelések**lehetőséget.
8. Válassza a **Csoport hozzáadása**lehetőséget. Attól függően, hogy ki és milyen hatással van a (z) a Slack-ra való bekapcsolására, a **hozzárendelés típusa** területen érdemes választania:
    - **A regisztrált eszközökhöz érhető el** , ha a "minden tag (beleértve a vendégek is)" lehetőséget választotta, vagy
    - **Regisztrációval vagy anélkül érhető el** , ha a "minden tag (kivéve a vendégek nélkül") vagy a "nem kötelező" lehetőséget választotta.
9. Válassza a **befoglalt csoportok** lehetőséget, majd az alkalmazás elérhetővé tétele az összes felhasználó számára lehetőséget. Válassza az **Igen**lehetőséget.
10. Kattintson **az OK**gombra, majd kattintson ismét **az OK** gombra.
11. Kattintson a **Mentés**gombra.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Alkalmazás-konfigurációs szabályzat hozzáadása a Slackhez
Adja hozzá a Slack iOS-hez készült alkalmazás-konfigurációs szabályzatát. A felügyelt eszközökre vonatkozó alkalmazás-konfigurációs szabályzatok platform-specifikusak, ezért külön szabályzatot kell hozzáadnia a Slack-felhasználók számára az Android-eszközökön.
1. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** > **Hozzáadás**lehetőséget.
2. A név mezőben adja meg a Slack-alkalmazás konfigurációs szabályzatának tesztjét.
3. Az eszközök regisztrálása területen válassza a **felügyelt eszközök**elemet.
4. A platform területen válassza az **iOS**lehetőséget.
5. Válassza a **társított alkalmazás**lehetőséget.
6. A keresősáv mezőben adja meg a "Slack for a" kifejezést, és válassza ki az alkalmazást.
7. Kattintson **az OK**, majd a **konfigurációs beállítások**elemre. 
8. Válassza **az OK**, majd a **Hozzáadás**lehetőséget.
9. A keresősáv mezőben adja meg a "Slack app Configuration Policy test" kifejezést, és válassza ki az imént hozzáadott szabályzatot.
10. A kezelés területen válassza a **hozzárendelések**lehetőséget.
11. A hozzárendelés a következőhöz területen válassza a **minden felhasználó és minden eszköz**lehetőséget.
12. Kattintson a **Mentés**gombra.

### <a name="optional-create-an-ios-device-compliance-policy"></a>Választható IOS-eszköz megfelelőségi szabályzatának létrehozása
Hozzon létre egy Intune eszközmegfelelőségi szabályzatot, ahol megadja, hogy milyen feltételeknek kell teljesülnie ahhoz, hogy az eszköz megfelelő legyen. Ebben az oktatóanyagban iOS-eszközökhöz hozunk létre eszközmegfelelőségi szabályzatot. A megfelelőségi szabályzatok platform-specifikusak, ezért létre kell hoznia egy külön szabályzatot a Slack-felhasználók számára az Android-eszközökön.
1. Az Intune-ban válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
2. A név mezőbe írja be az "iOS-megfelelőségi szabályzat tesztelése" kifejezést.
3. A Leírás mezőbe írja be az "iOS-megfelelőségi szabályzat tesztelése" kifejezést.
4. A platform területen válassza az **iOS**lehetőséget.
5. Válassza az **Eszközállapot** lehetőséget. A feltört eszközök mellett válassza a **Letiltás**lehetőséget, majd kattintson **az OK gombra**.
6. Válassza a **rendszerbiztonság** lehetőséget, és adja meg a jelszó beállításait. Az oktatóanyag végrehajtásához válassza a következő ajánlott beállításokat:
    - A mobileszközök zárolásának feloldásához jelszó megkövetelése beállításnál válassza a **kötelező**lehetőséget.
    - Egyszerű jelszavak esetén válassza a **Letiltás**lehetőséget.
    - A jelszó minimális hossza mezőben adja meg a 4 értéket.
    - A kötelező jelszó típusa mezőben válassza az **alfanumerikus**lehetőséget.
    - A jelszó kérése előtt a képernyő zárolásának maximális perce után válassza a **azonnal**lehetőséget.
    - A jelszó lejárata (nap) mezőben adja meg a 41 értéket.
    - Az újrafelhasználást megakadályozó korábbi jelszavak száma mezőbe írja be az 5 értéket.
7. Kattintson **az OK**gombra, majd válassza ismét **az OK** gombot.
8. Kattintson a **Létrehozás** gombra.

## <a name="set-up-slack-on-android-work-profile-devices"></a>A Slack beállítása androidos munkahelyi profilú eszközökön
Adja hozzá a Slack felügyelt Google Play alkalmazást az Intune-bérlőhöz, és hozzon létre egy alkalmazás-konfigurációs szabályzatot, amely lehetővé teszi, hogy a szervezetek Android-felhasználói hozzáférhessenek a Slackhez az Intune-nal.

### <a name="add-slack-to-intune"></a>Tartalékidő hozzáadása az Intune-hoz
A Slack hozzáadása felügyelt Google Play-alkalmazásként az Intune-ban, és a Slack-felhasználók kiosztása. Az alkalmazások platform-specifikusak, ezért hozzá kell adnia egy külön Intune-alkalmazást a Slack-felhasználók számára iOS-eszközökön.
1. Az Intune-ban válassza a **Client apps** > **alkalmazások** > **Hozzáadás**elemet.
2. Az alkalmazás típusa területen válassza az **áruházbeli alkalmazás – felügyelt Google Play**lehetőséget.
3. Válassza a **felügyelt Google Play-jóváhagyás**lehetőséget. Adja meg a "Slack for ír" keresési kifejezést, és válassza ki az alkalmazást.
4. Válassza a **jóváhagyás**lehetőséget.
5. A keresősáv mezőben adja meg a "Slack" kifejezést, és válassza ki az imént hozzáadott alkalmazást.
6. A kezelés területen válassza a **hozzárendelések**lehetőséget.
7. Válassza a **Csoport hozzáadása**lehetőséget. Attól függően, hogy ki és milyen hatással van a (z) a Slack-ra való bekapcsolására, a **hozzárendelés típusa** területen érdemes választania:
    - **A regisztrált eszközökhöz érhető el** , ha a "minden tag (beleértve a vendégek is)" lehetőséget választotta, vagy
    - **Regisztrációval vagy anélkül érhető el** , ha a "minden tag (kivéve a vendégek nélkül") vagy a "nem kötelező" lehetőséget választotta.
8. Válassza a befoglalt csoportok lehetőséget, majd az alkalmazás elérhetővé tétele az összes felhasználó számára lehetőséget. Válassza az **Igen**lehetőséget.
9. Kattintson **az OK**gombra, majd kattintson ismét **az OK** gombra.
10. Kattintson a **Mentés**gombra.

### <a name="add-an-app-configuration-policy-for-slack"></a>Alkalmazás-konfigurációs szabályzat hozzáadása a Slackhez
Alkalmazás-konfigurációs szabályzat hozzáadása a Slackhez. A felügyelt eszközökre vonatkozó alkalmazás-konfigurációs házirendek platform-specifikusak, ezért külön szabályzatot kell hozzáadnia a Slack-felhasználók számára iOS-eszközökön.
1. Az Intune-ban válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** > **Hozzáadás**lehetőséget.
2. A név mezőben adja meg a Slack-alkalmazás konfigurációs szabályzatának tesztjét.
3. Az eszközök regisztrálása területen válassza a **felügyelt eszközök**elemet.
4. A platform területen válassza az **Android**lehetőséget.
5. Válassza a **társított alkalmazás**lehetőséget.
6. A keresősáv mezőben adja meg a "Slack" kifejezést, és válassza ki az alkalmazást.
7. Válassza **az OK**, majd a **konfigurációs beállítások**lehetőséget.
    - A konfigurációs kulcsokkal és azok értékeivel kapcsolatos információkért olvassa el a [Slack AppConfig weboldalának](https://www.appconfig.org/company/slack/)"technikai" lapján található dokumentációt.
8. Kattintson **az OK gombra**, majd válassza a **Hozzáadás**lehetőséget.
9. A keresősáv mezőben adja meg a "Slack app Configuration Policy test" kifejezést, és válassza ki az imént hozzáadott szabályzatot.
10. A kezelés területen válassza a **hozzárendelések**lehetőséget.
11. A hozzárendelés a következőhöz területen válassza a **minden felhasználó és minden eszköz**lehetőséget.
12. Kattintson a **Mentés**gombra.

### <a name="optional-create-an-android-device-compliance-policy"></a>Választható Android-eszköz megfelelőségi szabályzatának létrehozása
Hozzon létre egy Intune eszközmegfelelőségi szabályzatot, ahol megadja, hogy milyen feltételeknek kell teljesülnie ahhoz, hogy az eszköz megfelelő legyen. Ebben az oktatóanyagban egy eszköz-megfelelőségi szabályzatot hozunk létre Android-eszközökhöz. A megfelelőségi szabályzatok platform-specifikusak, ezért külön szabályzatot kell létrehoznia a Slack-felhasználók számára iOS-eszközökön.
1. Az Intune-ban válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
2. A név mezőben adja meg az "Android-megfelelőségi szabályzat tesztelése" kifejezést.
3. A Leírás mezőbe írja be az "Android-megfelelőségi szabályzat tesztelése" kifejezést.
4. A platform területen válassza az **Android Enterprise**lehetőséget.
5. A profil típusa területen válassza a **munkahelyi profil**lehetőséget.
6. Válassza az **Eszközállapot** lehetőséget. A feltört eszközök mellett válassza a **Letiltás**lehetőséget, majd kattintson **az OK gombra**.
7. Válassza a **rendszerbiztonság** lehetőséget, és adja meg a **jelszó beállításait**. Az oktatóanyag végrehajtásához válassza a következő ajánlott beállításokat:
    - A mobileszközök zárolásának feloldásához jelszó megkövetelése beállításnál válassza a **kötelező**lehetőséget.
    - A kötelező jelszó típusa mezőben válasszon ki **legalább alfanumerikus**karaktereket.
    - A jelszó minimális hossza mezőben adja meg a 4 értéket.
    - A jelszó kérése előtt a képernyő zárolása után legfeljebb **15**percet válasszon.
    - A jelszó lejárata (nap) mezőben adja meg a 41 értéket.
    - Az újrafelhasználást megakadályozó korábbi jelszavak száma mezőbe írja be az 5 értéket.
8. Kattintson **az OK**gombra, majd kattintson ismét **az OK** gombra.
9. Kattintson a **Létrehozás** gombra.

## <a name="launch-slack"></a>Tartalékidő elindítása

Az imént létrehozott szabályzatokkal minden olyan iOS-vagy Android-alapú munkahelyi profil-eszközre, amely megpróbál bejelentkezni az egyik munkaterületre, az Intune-ban regisztrálni kell. Ennek a forgatókönyvnek a teszteléséhez próbálja meg a Slack for az az, hogy egy Intune-ban regisztrált iOS-eszközön, vagy egy Intune-ban regisztrált Android munkahelyi profil eszközön indítsa el a slacket. 

## <a name="next-steps"></a>További lépések

Ebben az oktatóanyagban:
- Az Intune-t nagyvállalati mobilitási szolgáltatásként (am) kell beállítania a Slack Enterprise Gridben. 
- Alkalmazás-konfigurációs szabályzatokat hozott létre az iOS-es és az androidos munkahelyi profilú eszközökhöz készült Slack alkalmazás kezeléséhez.
- Az Android és az iOS rendszerű eszközök megfelelőségi feltételeinek megadásához az Intune-eszközök megfelelőségi szabályzatait kell létrehoznia.

Az alkalmazás-konfigurációs házirendekkel kapcsolatos további információkért lásd: [alkalmazás-konfigurációs házirendek a Microsoft Intunehoz](app-configuration-policies-overview.md). Az eszközök megfelelőségi házirendjeivel kapcsolatos további tudnivalókért lásd: [szabályok beállítása eszközökön a szervezet erőforrásaihoz való hozzáférés engedélyezéséhez az Intune használatával](../protect/device-compliance-get-started.md).
