---
title: Felügyelt Google Play-alkalmazások kiosztása androidos vállalati eszközökhöz
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan lehet alkalmazásokat szinkronizálni és hozzárendelni androidos vállalati eszközökhöz a felügyelt Google Play áruházból.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 126ea5a1798252f29e988553edfea462eff2fd7e
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256458"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Felügyelt Google Play-alkalmazások hozzáadása androidos vállalati eszközökhöz az Intune-nal

A felügyelt Google Play a Google Enterprise App Store áruháza, és az Android Enterprise rendszerhez készült egyéni alkalmazások forrása. Az Intune-nal a felügyelt Google Play szolgáltatással is összehangolhatja az alkalmazások telepítését bármilyen androidos nagyvállalati forgatókönyv esetén (beleértve a munkahelyi profilt, a dedikált és a teljes körűen felügyelt regisztrációkat). Felügyelt Google Play-alkalmazások hozzáadása az Intune-hoz – eltér attól, hogy az Android-alkalmazások hogyan lesznek hozzáadva a nem androidos vállalatok számára. Az áruházbeli alkalmazásokat, üzletági (LOB) alkalmazásokat és webalkalmazásokat a rendszer jóváhagyja vagy hozzáadja a felügyelt Google Play szolgáltatáshoz, majd szinkronizálja az Intune-nal, hogy megjelenjenek az ügyfélalkalmazások listájában. Miután megjelentek az ügyfélalkalmazások listájának listáján, kezelheti a felügyelt Google Play-alkalmazások hozzárendelését, ahogyan bármely más alkalmazásban.

Ahhoz, hogy az Intune-bérlőt a felügyelt Google Play szolgáltatáshoz csatlakoztassa, könnyebben konfigurálhatja és használhatja az androidos vállalati felügyeletet, az Intune-nal automatikusan négy általános Android-alapú nagyvállalati alkalmazást fog hozzáadni az Intune felügyeleti konzolhoz. A négy alkalmazás a következő:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – az Android Enterprise teljes körűen felügyelt forgatókönyvekhez használható. Ez az alkalmazás automatikusan települ a teljes körűen felügyelt eszközökre az eszköz beléptetési folyamata során.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – segít bejelentkezni a fiókjába, ha kétfaktoros ellenőrzést használ. Ez az alkalmazás automatikusan települ a teljes körűen felügyelt eszközökre az eszköz beléptetési folyamata során.
- **[Intune céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – az alkalmazás-és az Android Enterprise Work-profil forgatókönyvek esetében használatos.
- **[Felügyelt kezdőképernyő](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** – az Android Enterprise dedikált többalkalmazásos kioszk-forgatókönyvekhez használható. A rendszergazdáknak létre kell hozniuk egy hozzárendelést az alkalmazás telepítéséhez olyan dedikált eszközökön, amelyeket többalkalmazásos kioszk-forgatókönyvekben fog használni.

>[!NOTE]
>Amikor egy végfelhasználó regisztrálja az Android Enterprise teljes mértékben felügyelt eszközét, a Intune Céges portál alkalmazás automatikusan települ, és az alkalmazás ikonja látható lesz a végfelhasználó számára. Ha a végfelhasználó megpróbálja elindítani a Intune Céges portál alkalmazást, a rendszer átirányítja a felhasználót a Microsoft Intune alkalmazásba, és a Céges portál alkalmazás ikonja el lesz rejtve.

## <a name="before-you-start"></a>Előkészületek
- Győződjön meg arról, hogy az Intune-bérlőt a felügyelt Google Play szolgáltatáshoz csatlakoztatta.  További információ: [az Intune-fiók összekötése a felügyelt Google Play-fiókkal](../enrollment/connect-intune-android-enterprise.md).
- Ha munkahelyi profilokat szeretne regisztrálni, győződjön meg arról, hogy az Intune-t és az Android munkahelyi profilokat úgy konfigurálta, hogy együtt működjenek a Azure Portal **eszköz-regisztrálási** munkaterhelésében. További információ: [Android-eszközök regisztrálása](../enrollment/android-work-profile-enroll.md).

>[!NOTE]
>A Microsoft Intune használatához javasoljuk, hogy a Microsoft Edge vagy a Google Chrome böngészőt használja.

## <a name="managed-google-play-app-types"></a>Felügyelt Google Play-alkalmazások típusai
A felügyelt Google Play szolgáltatásban háromféle alkalmazás érhető el:

- **Felügyelt Google Play áruházbeli alkalmazás** – a Play áruház általánosan elérhető nyilvános alkalmazások. Ezeket az alkalmazásokat az Intune-ban kezelheti, ha megkeresi a felügyelni kívánt alkalmazásokat, jóváhagyja őket, majd szinkronizálja őket az Intune-ban.
- **Felügyelt Google Play Private-alkalmazás** – ezek azok a LOB-alkalmazások, amelyeket az Intune-rendszergazdák felügyelnek a Google Play szolgáltatásban.  Ezek az alkalmazások magánjellegűek, és csak az Intune-bérlő számára érhetők el. A LOB-alkalmazások felügyelete és üzembe helyezése a felügyelt Google Play és az Android Enterprise platformon történik.
- **Felügyelt Google Play webes hivatkozás** – a webes hivatkozások az androidos vállalati eszközökre telepíthető, rendszergazda által definiált ikonokkal. Ezek az eszközök alkalmazás-listájában jelennek meg, ugyanúgy, mint a normál alkalmazások.

## <a name="managed-google-play-store-apps"></a>Felügyelt Google Play áruházbeli alkalmazások
A felügyelt Google Play áruházbeli alkalmazások az Intune-nal való tallózásának és jóváhagyásának két módja van:

1. Közvetlenül az Intune-konzolon – az áruházbeli alkalmazások tallózása és jóváhagyása az Intune-ban üzemeltetett nézetben. Ez közvetlenül az Intune-konzolon nyílik meg, és nem igényli, hogy egy másik fiókkal újra hitelesítenie kell magát.
1. A felügyelt Google Play konzolon lehetőség van a felügyelt Google Play-konzol közvetlen megnyitására és az alkalmazások jóváhagyására is. További információt a [felügyelt Google Play-alkalmazás szinkronizálása az Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune) -nal című témakörben talál.  Ehhez külön bejelentkezésre van szükség az Intune-bérlőnek a felügyelt Google Play szolgáltatáshoz való összekapcsolásához használt fiókkal.

### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Felügyelt Google Play áruházbeli alkalmazás hozzáadása közvetlenül az Intune-konzolon

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán az elérhető **áruházbeli alkalmazások** típusai területen válassza a **felügyelt Google Play-alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik a **felügyelt Google Play** App Store áruház.

    > [!NOTE]
    > Az Intune-bérlő fiókjának csatlakoznia kell az androidos vállalati fiókjához a felügyelt Google Play áruházbeli alkalmazások tallózásához. További információ: [az Intune-fiók összekötése a felügyelt Google Play-fiókkal](../enrollment/connect-intune-android-enterprise.md).

5. Válasszon ki egy alkalmazást az alkalmazás részleteinek megtekintéséhez.
6. Az alkalmazást megjelenítő oldalon kattintson a **jóváhagyás**elemre. Ekkor megjelenik egy ablak, amelyben az alkalmazás engedélyt kér bizonyos műveletek végrehajtására.
7. Az engedélyek elfogadásához és a folytatáshoz válassza a **Jóváhagyás** lehetőséget.
8. Válassza a jóváhagyás **megtartása, ha az alkalmazás új engedélyeket kér** a **jóváhagyási beállítások** lapon, majd kattintson a **kész**gombra. 

    > [!IMPORTANT]
    > Ha nem ezt a lehetőséget választja, akkor manuálisan jóvá kell hagynia az új engedélyeket, ha az alkalmazás fejlesztője közzétesz egy frissítést. Ez azt eredményezi, hogy az alkalmazás telepítései és frissítései leállnak az engedélyek jóváhagyása előtt. Ezért javasoljuk, hogy válassza az új engedélyek automatikus jóváhagyása lehetőséget. 

9. Kattintson a **kiválasztás** elemre az alkalmazás kiválasztásához.
10. Kattintson a panel tetején található **szinkronizálás** gombra, hogy szinkronizálja az alkalmazást a felügyelt Google Play szolgáltatással.
11. Az alkalmazások listájának frissítéséhez és az újonnan hozzáadott alkalmazás megjelenítéséhez kattintson a **frissítés** gombra.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Felügyelt Google Play áruházbeli alkalmazás hozzáadása a felügyelt Google Play-konzolon (alternatív)
Ha a felügyelt Google Play-alkalmazást az Intune-nal közvetlenül az Intune-nal való hozzáadása helyett szeretné szinkronizálni, kövesse az alábbi lépéseket.

> [!IMPORTANT]
> Az alábbi információk egy másik módszer a felügyelt Google Play-alkalmazások Intune-nal való hozzáadására a fentiekben leírtak alapján.

1. Keresse fel a [Felügyelt Google Play áruházat](https://play.google.com/work). Jelentkezzen be ugyanazzal a fiókkal, amelyet az Intune és az Android Enterprise közötti kapcsolat konfigurálásához használt.
2. Az áruházban keresse meg és válassza ki az Intune-nal hozzárendelendő alkalmazást.
3. Az alkalmazást megjelenítő oldalon kattintson a **jóváhagyás**elemre.  
    A következő példákban a Microsoft Excel alkalmazás van kiválasztva.

    ![A Jóváhagyás gomb a Felügyelt Google Play áruházban](./media/apps-add-android-for-work/approve.png)

   Ekkor megjelenik egy ablak, amelyben az alkalmazás engedélyt kér bizonyos műveletek végrehajtására.

4. Az engedélyek elfogadásához és a folytatáshoz válassza a **Jóváhagyás** lehetőséget.

    ![Jóváhagyás gomb az alkalmazásengedélyekhez](./media/apps-add-android-for-work/approve-app-permissions.png)

5. Adja meg, hogyan szeretné kezelni az új alkalmazásengedély-kérelmeket, majd válassza a **Mentés** lehetőséget.

    ![Új alkalmazásengedély-kérelmek kezelési lehetőségei](./media/apps-add-android-for-work/approve-app-settings.png)

    A jóváhagyás megtörténik, és az alkalmazás megjelenik a rendszergazdai konzolon. Ezután [szinkronizálhatja az Android munkahelyi profil alkalmazást az Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)-nal.

## <a name="managed-google-play-private-lob-apps"></a>Felügyelt Google Play Private-(LOB-) alkalmazások

Az ÜZLETÁGI alkalmazások a felügyelt Google Play szolgáltatással kétféleképpen vehetők fel:

1. Közvetlenül az Intune-konzolon – ez lehetővé teszi a LOB-alkalmazások hozzáadását úgy, hogy csak az alkalmazás APK-t és egy címet küldi el közvetlenül az Intune-on belül. Ehhez a módszerhez nincs szükség Google Developer-fiókra, és nem kell fizetnie a Google-nak fejlesztőként való regisztrálás díját.  Ez a módszer egyszerűbb, és lényegesen kevesebb lépésből áll, és a LOB-alkalmazások számára elérhetővé teszi a felügyeletet mindössze tíz perc alatt.
1. A Google Play fejlesztői konzolon – ha rendelkezik Google Developer-fiókkal, vagy olyan speciális terjesztési funkciókat szeretne konfigurálni, amelyek csak a Google Play fejlesztői konzolon érhetők el (például további alkalmazás-képernyőképek hozzáadásával), használhatja a [Google Play fejlesztői konzolt](https://play.google.com/apps/publish). 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Felügyelt Google Play Private-(LOB-) alkalmazások közzététele közvetlenül az Intune-konzolon

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán az elérhető **áruházbeli alkalmazások** típusai területen válassza a **felügyelt Google Play-alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. A **felügyelt Google Play** App Store áruház az Intune-ban jelenik meg.
5. A Google Play ablakban válassza a **privát alkalmazások** elemet (a *zárolás* ikon mellett). 
6. Új alkalmazás hozzáadásához kattintson a jobb alsó sarokban található **"+"** gombra.
7. Vegyen fel egy alkalmazás **címét** , és kattintson az **apk feltöltése** elemre az apk-alkalmazáscsomag hozzáadásához.
8. Kattintson a **Létrehozás** gombra.
9. Ha elkészült az alkalmazások hozzáadásával, akkor a felügyelt Google Play panel bezárásához.
10. Kattintson a **szinkronizálás** elemre az **app app** panelen a felügyelt Google Play szolgáltatással való szinkronizáláshoz. 

    > [!NOTE]
    > A privát alkalmazások több percet is igénybe vehetnek a szinkronizáláshoz. Ha az alkalmazás nem jelenik meg az első alkalommal, amikor szinkronizálást hajt végre, várjon néhány percet, és kezdeményezzen új szinkronizálást.

A felügyelt Google Play Private-alkalmazásokkal kapcsolatos további információkért, beleértve a gyakori kérdéseket is, tekintse meg a Google támogatási cikkét: https://support.google.com/googleplay/work/answer/9146439

>[!IMPORTANT]
>Az ezzel a módszerrel hozzáadott privát alkalmazások soha nem tehetők közzé. Csak akkor használja ezt a közzétételi lehetőséget, ha biztos benne, hogy az alkalmazás mindig privát lesz a szervezet számára.

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Felügyelt Google Play Private (LOB) alkalmazások közzététele a Google fejlesztői konzol használatával

1. Jelentkezzen be a [Google Play fejlesztői konzolba](https://play.google.com/apps/publish) ugyanazzal a fiókkal, amelyet az Intune és az Android Enterprise közötti kapcsolat konfigurálásához használt.  
    Az első bejelentkezés előtt regisztrálni kell, továbbá megfizetni a Google Developer-program regisztrációs díját.
2. A konzolon válassza az **Új alkalmazás hozzáadása** elemet.
3. Az alkalmazások és azok információinak feltöltése ugyanúgy történik, mint bármelyik alkalmazás közzététele a Google Play áruházban. Ugyanakkor ki kell választani **Az alkalmazás elérhetővé tétele csak a saját cég tagjai számára (<*cég neve*>)** lehetőséget.

    ![Az alkalmazás elérhetővé tétele csak a saját vállalat számára](./media/apps-add-android-for-work/restrict.png)

    Ez a művelet az alkalmazást csak a saját cége számára teszi elérhetővé. A nyilvános Google Play áruházban azonban nem lesz elérhető.

    Az androidos alkalmazások feltöltéséről és közzétételéről a [Google Play fejlesztői központ súgójában](https://support.google.com/googleplay/android-developer/answer/113469) talál további információt.
4. Miután közzétette az alkalmazást, jelentkezzen be a [felügyelt Google Play áruházba](https://play.google.com/work) ugyanazzal a fiókkal, amelyet az Intune és az Android Enterprise közötti kapcsolat konfigurálásához használt.
5. Az áruház **Alkalmazások** csomópontjában ellenőrizze, hogy megjelenik-e a közzétett alkalmazás.  
    Az alkalmazás automatikusan megkapja az engedélyt az Intune-nal való szinkronizálásra.

## <a name="managed-google-play-web-links"></a>Felügyelt Google Play webes hivatkozások

A felügyelt Google Play-webhivatkozások telepíthetők és kezelhetők ugyanúgy, mint más Android-alkalmazások. Az eszközön való telepítéskor a rendszer a felhasználó alkalmazás-listájában fogja megjelenni az általuk telepített többi alkalmazás mellett. A rendszer az eszköz böngészőjében indít el.

A webhivatkozások a Microsoft Edge vagy bármely más, a telepítéshez kiválasztott böngésző alkalmazásban nyílnak meg. Ügyeljen arra, hogy legalább egy böngészőt helyezzen üzembe az eszközökön ahhoz, hogy a webhivatkozások megfelelően meg tudják nyitni a webhelyeket. A webes hivatkozások (teljes képernyős, önálló és minimális felhasználói felület) összes **megjelenítési** lehetősége azonban csak a Chrome böngészővel használható. 

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán az elérhető **áruházbeli alkalmazások** típusai területen válassza a **felügyelt Google Play-alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. A **felügyelt Google Play** App Store áruház az Intune-ban jelenik meg.
5. A Google Play ablakban válassza a **Web Apps** (a *Globe* ikon mellett) lehetőséget.
6. Új alkalmazás hozzáadásához kattintson a jobb alsó sarokban található **"+"** gombra.
7. Vegyen fel egy alkalmazás **címét**, a webalkalmazás **URL-címét**, válassza ki, hogyan jelenjen meg az alkalmazás, és válassza ki az alkalmazás ikonját.
8. Kattintson a **Létrehozás** gombra.
9. Ha elkészült az alkalmazások hozzáadásával, akkor a felügyelt Google Play panel bezárásához.
10. Kattintson a **szinkronizálás** elemre az **app app** panelen a felügyelt Google Play szolgáltatással való szinkronizáláshoz. 

    > [!NOTE]
    > A Web Apps több percet is igénybe vehet a szinkronizáláshoz. Ha az alkalmazás nem jelenik meg az első alkalommal, amikor szinkronizálást hajt végre, várjon néhány percet, és kezdeményezzen új szinkronizálást.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Felügyelt Google Play áruházbeli alkalmazás szinkronizálása az Intune-nal

Ha jóváhagyta az alkalmazást az áruházból, és nem látja az **alkalmazások** munkaterhelésében, a következőképpen kényszerítheti az azonnali szinkronizálást:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Válassza az **alkalmazások** > **bérlői felügyelet** > **összekötők és tokenek** > **felügyelt Google Play**lehetőséget.
5. A **Felügyelt Google Play** panelen válassza a **Frissítés** lehetőséget.  
    A lapon frissül az utolsó szinkronizálás időpontja és állapota.
6. A Microsoft Endpoint Manager felügyeleti központban válassza az **alkalmazások** > **minden alkalmazás**lehetőséget.  
    Megjelenik az elérhetővé vált Felügyelt Google Play-alkalmazás.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Felügyelt Google Play-alkalmazás kiosztása androidos vállalati munkahelyi Profilos eszközökhöz

Ha az alkalmazás megjelenik az **alkalmazások** munkaterhelése ablaktábla **alkalmazás-licencek** csomópontjában, akkor [ugyanúgy rendelheti hozzá, mint bármely más alkalmazást](/intune-azure/manage-apps/deploy-apps) , ha az alkalmazást felhasználók csoportjaihoz rendeli hozzá.

Az alkalmazás hozzárendelését követően a rendszer telepíti (vagy telepíthető) a célként kijelölt felhasználók eszközeire. A rendszer nem kér telepítési jóváhagyást az eszköz felhasználójától. Az androidos vállalati munkahelyi profil eszközeivel kapcsolatos további információkért lásd: [az androidos vállalati munkahelyi profilok regisztrációjának beállítása](../enrollment/android-work-profile-enroll.md). 

> [!NOTE] 
> Csak a hozzárendelt alkalmazások jelennek meg a felügyelt Google Play áruházban a végfelhasználók számára. Ez egy fontos lépés ahhoz, hogy a rendszergazda elvégezze a felügyelt Google Play-alkalmazásokkal rendelkező alkalmazások beállítását.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Felügyelt Google Play-alkalmazás kiosztása Android Enterprise teljes körűen felügyelt eszközökhöz

Az [Android Enterprise teljes körűen felügyelt eszközei](../enrollment/android-fully-managed-enroll.md) olyan vállalati tulajdonú eszközök, amelyek egyetlen felhasználóhoz vannak társítva, és kizárólag munkahelyi és nem személyes használatra használatosak. A teljes körűen felügyelt eszközökön lévő felhasználók a felügyelt Google Play alkalmazásból szerezhetik be elérhető vállalati alkalmazásaikat az eszközön.

Alapértelmezés szerint az Android Enterprise teljes körűen felügyelt eszköze nem teszi lehetővé az alkalmazottak számára a szervezet által nem jóváhagyott alkalmazások telepítését. Emellett az alkalmazottak nem tudják eltávolítani a telepített alkalmazásokat a szabályzattal szemben. Ha engedélyezni szeretné a felhasználók számára a teljes Google Play áruház elérését az alkalmazások telepítéséhez, és nem csak a felügyelt Google Play áruházban lévő jóváhagyott alkalmazásokhoz való hozzáférést, akkor a **Google Play áruházban lévő összes alkalmazás** **számára engedélyezheti**a hozzáférést. Ezzel a beállítással a felhasználók a Google Play áruházban lévő összes alkalmazást a vállalati fiók használatával érhetik el, de a vásárlások korlátozottak lehetnek. A korlátozott vásárlások korlátozását úgy távolíthatja el, hogy lehetővé teszi a felhasználók számára új fiókok hozzáadását az eszközhöz. Ez lehetővé teszi a végfelhasználók számára, hogy a Google Play áruházból származó alkalmazásokat a személyes fiókok használatával, valamint az alkalmazáson belüli vásárlásokkal is megvásárolják. További információ: [androidos vállalati eszközbeállítások az Intune-nal kapcsolatos szolgáltatások engedélyezéséhez vagy korlátozásához](../configuration/device-restrictions-android-for-work.md). 

> [!NOTE]
> A Microsoft Intune alkalmazás és a Microsoft Authenticator alkalmazás a bevezetéskor szükséges alkalmazásként lesz telepítve az összes teljes körűen felügyelt eszközre. Ha ezek az alkalmazások automatikusan telepítve vannak, a feltételes hozzáférési támogatást biztosít, és Microsoft Intune alkalmazás felhasználói láthatják és elhárítják a megfelelőségi problémákat. 

## <a name="manage-android-enterprise-app-permissions"></a>Androidos vállalati alkalmazás engedélyeinek kezelése
Az Android Enterprise a felügyelt Google Play webkonzolon lévő alkalmazások jóváhagyását igényli, mielőtt szinkronizálja őket az Intune-nal, és hozzárendeli azokat a felhasználókhoz. Mivel az Android Enterprise lehetővé teszi az alkalmazások csendes és automatikus leküldését a felhasználói eszközökre, el kell fogadnia az alkalmazás engedélyeit az összes felhasználó nevében. A végfelhasználóknak az alkalmazások telepítésénél nem jelennek meg alkalmazásengedélyek, ezért fontos, hogy Ön megértse ezeket az engedélyeket.

Ha az alkalmazás fejlesztője megváltozott engedélyekkel rendelkező új alkalmazásverziót tesz közzé, az új engedélyek nem lesznek automatikusan elfogadva akkor sem, ha Ön az előző verzió engedélykéréseit elfogadta. Az alkalmazás korábbi verzióját futtató eszközök továbbra is használhatják az alkalmazást. Az alkalmazás frissítése azonban nem történik meg, amíg el nem fogadja az új engedélyeket. Az alkalmazással még nem rendelkező eszközökre az új engedélyek elfogadásáig nem telepíthető az alkalmazás. 

### <a name="update-app-permissions"></a>Alkalmazásengedélyek frissítése

Ellenőrizze rendszeresen a felügyelt Google Play-konzolon az új alkalmazásengedélyeket. Beállíthatja, hogy a Google Play e-mailt küldjön Önnek vagy másoknak, ha új engedélyekre van szükség egy jóváhagyott alkalmazáshoz. Ha egy alkalmazás a hozzárendelése után sincs telepítve az eszközökön, az alábbiak alapján ellenőrizheti, hogy vannak-e új alkalmazásengedélyek:

1. Nyissa meg a [Google Play Áruházat](https://play.google.com/work).
2. Jelentkezzen be azzal a Google-fiókkal, amelyet az alkalmazások közzétételénél és jóváhagyásánál használt.
3. Válassza a **Frissítések** lapot és ellenőrizze, hogy van-e frissítést igénylő alkalmazás.  
    A listában szereplő összes alkalmazás új engedélyeket kér, és a hozzárendelés addig nem lehetséges, amíg az engedélyeket meg nem adják.

Alternatív megoldásként beállíthatja, hogy a Google Play alkalmazásalapon automatikusan végezze el az engedélyek ismételt megadását.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>További felügyelt Google Play-alkalmazások jelentéskészítése androidos vállalati munkahelyi Profilos eszközökhöz

Az Android Enterprise Work profiling-eszközökre telepített felügyelt Google Play-alkalmazások esetében az Intune használatával megtekintheti az eszközön telepített alkalmazás állapotát és verziószámát. 

## <a name="delete-managed-google-play-apps"></a>Felügyelt Google Play-alkalmazások törlése
Ha szükséges, törölheti a felügyelt Google Play-alkalmazásokat Microsoft Intuneról. A felügyelt Google Play-alkalmazások törléséhez nyissa meg Microsoft Intune a Azure Portalban, és válassza az **alkalmazások** > **minden alkalmazás**lehetőséget. Az alkalmazás listából válassza a felügyelt Google Play alkalmazás jobb oldalán található három pontot (...), majd válassza a **Törlés** lehetőséget a megjelenített listából. Ha töröl egy felügyelt Google Play-alkalmazást az alkalmazások listájáról, a felügyelt Google Play-alkalmazás automatikusan nem lesz jóváhagyva.

> [!NOTE]
> Ha egy alkalmazás jóváhagyása nem engedélyezett, vagy törölve lett a felügyelt Google Play áruházból, a rendszer nem távolítja el az Intune Client appss listáról. Így továbbra is megcélozhat egy eltávolítási szabályzatot a felhasználók számára, még akkor is, ha az alkalmazás nincs jóváhagyva.

## <a name="android-enterprise-system-apps"></a>A Vállalati Android rendszeralkalmazásai

Az androidos vállalati rendszeralkalmazások az [Android Enterprise dedikált eszközökhöz](../enrollment/android-kiosk-enroll.md) vagy [teljes körűen felügyelt eszközökhöz](../enrollment/android-fully-managed-enroll.md)is engedélyezhetők. Az androidos nagyvállalati rendszeralkalmazások hozzáadásával kapcsolatos további információkért lásd: [az androidos nagyvállalati rendszeralkalmazások hozzáadása a Microsoft Intunehoz](apps-ae-system.md).

## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
