---
title: A zebra Mobility Extensions használata Android-eszközökön Microsoft Intune-Azure-ban | Microsoft Docs
description: Az Android rendszerű Zebra Mobility Extensions (MX) használatával felügyelheti és használhatja a Microsoft Intune-t. Tekintse meg az összes lépést, beleértve a Céges portál alkalmazás telepítését, az alkalmazás Oldalazva társas viszony, az eszköz rendszergazdai szerepkörének hozzárendelését, a StageNow-profil létrehozását és egyebeket.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: jieyan
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 829d8f6b2691f91c14029e4f29e2ef11b070e596
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059621"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Zebra-eszközök használata és kezelése a zebra Mobility Extensions használatával Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune számos funkciót tartalmaz, többek között az alkalmazások kezelését és az eszközbeállítások konfigurálását. Ezek a beépített funkciók és beállítások a zebra Technologies által gyártott Android-eszközöket, más néven "Zebra-eszközöket" kezelnek.

Androidos eszközökön a Zebra 's **Mobility Extensions (MX)** profilok használatával testreszabhatja vagy hozzáadhatja a zebra-specifikus beállításokat.

Ez a cikk bemutatja, hogyan használható a zebra Mobility Extensions (MX) a zebra-eszközökön a Microsoft Intune.

Ez a funkció az alábbiakra vonatkozik:

- Android:

A vállalat felhasználhatja a zebra-eszközöket a lakossági, a gyári szinten, és így tovább. Például Ön egy kiskereskedő, és a környezet több ezer olyan Zebra-mobil eszközt is tartalmaz, amelyeket a Sales Associates használ. Az Intune a mobileszköz-kezelési (MDM) megoldás részeként segíti az eszközök felügyeletét.

Az Intune használatával olyan Zebra-eszközöket regisztrálhat, amelyekkel az üzletági alkalmazásokat az eszközökön helyezheti üzembe. Az "eszköz konfigurációja" profilok lehetővé teszik, hogy MX-profilokat hozzon létre a zebra-specifikus beállítások kezeléséhez.

> [!NOTE]
> Alapértelmezés szerint a zebra MX API-k nincsenek zárolva az eszközökön. Az eszköz az Intune-ban való regisztrálása előtt lehetséges, hogy az eszköz rosszindulatú módon sérülhet. Ha az eszköz tiszta állapotban van, javasoljuk, hogy zárolja az MX API-kat az Access Manager (AccessMgr) használatával. Kiválaszthatja például, hogy csak a megbízható Céges portál alkalmazás és alkalmazások számára engedélyezett az MX API-k hívása.
>
> További információ: [az eszköz zárolása](https://developer.zebra.com/community/home/blog/2017/04/11/locking-down-your-device) a zebra webhelyén.

## <a name="before-you-begin"></a>Előkészületek

- Győződjön meg arról, hogy a StageNow asztali alkalmazás legújabb verziója található a zebra Technologies-től.
- Ügyeljen arra, hogy a [Zebra teljes MX-szolgáltatásának mátrixát](http://techdocs.zebra.com/mx/compatibility) (a zebra webhelyének megnyitása) ellenőrizze, hogy az Ön által létrehozott profilok kompatibilisek-e az eszköz MX verziójával, az operációs rendszer verziójával és a modellel.
- Bizonyos eszközök, például a TC20/25 eszközök, nem támogatják az összes elérhető MX-funkciót a StageNow-ben. Győződjön meg arról, hogy a [Zebra funkciójának mátrixa](http://techdocs.zebra.com/mx/tc2x/) (a zebra webhelyének megnyitása) a frissített támogatási információkra vonatkozik.

## <a name="step-1-install-the-latest-company-portal-app"></a>1\. lépés: a legújabb Céges portál alkalmazás telepítése

Az eszközön nyissa meg a Google Play áruházat. Töltse le és telepítse a Intune Céges portál alkalmazást a Microsofttól. A Google Play áruházból való telepítéskor a Céges portál alkalmazás automatikusan frissítéseket és javításokat kap.

Ha a Google Play nem érhető el, töltse le az [Androidhoz készült Microsoft Intune céges portál](https://www.microsoft.com/download/details.aspx?id=49140) (megnyílik egy másik Microsoft-webhely), és [Oldalazva társas viszony](#sideload-the-company-portal-app) (ebben a cikkben). Ha így van telepítve, az alkalmazás nem kap automatikusan frissítéseket vagy javításokat. Győződjön meg arról, hogy rendszeresen frissíti az alkalmazást, és manuálisan javítja a javítást.

### <a name="sideload-the-company-portal-app"></a>A Céges portál alkalmazás Oldalazva társas viszony

"Közvetlen telepítési", ha nem használja a Google Play alkalmazást az alkalmazások telepítéséhez. A Céges portál alkalmazás Oldalazva társas viszony használja a StageNow. 

A következő lépések áttekintést nyújtanak. További részletekért lásd a zebra dokumentációját. [Regisztráljon egy Mdm a StageNow használatával](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (a zebra webhelyének megnyitása) lehet jó erőforrás.

1. A StageNow-ben hozzon létre egy profilt a **regisztráláshoz egy Mdm**.
2. Az **üzembe helyezés**területen válassza a Mdm-ügynök fájljának letöltését.
3. Állítsa be a **támogatási alkalmazást** , és **töltse le a konfigurációs** lépéseket a **nem**értékre.
4. A **Mdm letöltése**lapon válassza a **fájl átvitele/másolása**lehetőséget. Adja hozzá a Céges portál android-csomag (APK) forrását és célját.
5. Az **Indítás Mdm**területen hagyja meg az alapértelmezett értékeket. Adja hozzá a következő adatokat:

    - **Csomag neve**: `com.microsoft.windowsintune.companyportal`
    - **Osztály neve**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Folytassa a profil közzétételével, és használja a StageNow alkalmazással az eszközön. A Céges portál alkalmazás telepítve van és meg van nyitva az eszközön.

> [!TIP]
> További információ a StageNow-ről és azokról: [StageNow Android-eszközök átmeneti](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) beállítása (a zebra webhely megnyitása).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>2\. lépés: Győződjön meg arról, hogy a Céges portál alkalmazás rendelkezik az eszköz rendszergazdai szerepkörével

Az Céges portál alkalmazásnak az Android-eszközök felügyeletéhez az eszköz rendszergazdájának kell lennie. Az eszköz rendszergazdai szerepkörének aktiválásához néhány Zebra-eszköz tartalmaz egy felhasználói felületet (UI) az eszközön. Ha az eszköz felhasználói felületet tartalmaz, a Céges portál alkalmazás bekéri a felhasználót, hogy a [regisztráció](#step-3-enroll-the-device-in-to-intune) során adja meg az eszköz rendszergazdáját (ebben a cikkben).

Ha a felhasználói felület nem érhető el, a StageNow **DevAdmin-kezelőjével** létrehozhat egy profilt, amely manuálisan engedélyezi az eszköz rendszergazdájának az céges portál alkalmazást.

A következő lépések áttekintést nyújtanak. További részletekért lásd a zebra dokumentációját. 
Az eszköz rendszergazdájaként (a zebra webhelyének megnyitása) [állítsa be az akkumulátor swap üzemmódját](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) . lehet, hogy jó erőforrás.

1. A StageNow-ben hozzon létre egy profilt, és válassza a **Xpert mód**lehetőséget.
2. Adja hozzá a **DevAdmin-kezelőt** a profilhoz.
3. Eszköz- **rendszergazdaként való bekapcsoláshoz**állítsa be az **eszközkezelés műveletet** .
4. Az **eszköz-felügyeleti csomag nevének** beállítása `com.microsoft.windowsintune.companyportal`.
5. Adja meg az **eszköz rendszergazdai osztályának nevét** a következőre: `com.microsoft.omadm.client.PolicyManagerReceiver`.

Folytassa a profil közzétételével, és használja a StageNow alkalmazással az eszközön. A Céges portál alkalmazás megkapja az eszköz rendszergazdai szerepkörét.

## <a name="step-3-enroll-the-device-in-to-intune"></a>3\. lépés: az eszköz regisztrálása az Intune-ban

Az első két lépés elvégzése után a Céges portál alkalmazás telepítve van az eszközön. Az eszköz készen áll az Intune-ba való regisztrálásra.

Az [Android-eszközök regisztrálása](../enrollment/android-enroll.md) a lépéseket tartalmazza. Ha sok Zebra-eszközzel rendelkezik, érdemes lehet egy [eszköz beléptetési kezelő (DEM) fiókot](../enrollment/device-enrollment-manager-enroll.md)használni. A DEM-fiók használatával eltávolítja a Céges portál alkalmazásból való regisztráció törlésének lehetőségét is, így a felhasználók nem tudják törölni az eszköz regisztrációját.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>4\. lépés: eszközkezelés-profil létrehozása a StageNow-ben

A StageNow használatával hozzon létre egy profilt, amely az eszközön kezelni kívánt beállításokat konfigurálja. További részletekért lásd a zebra dokumentációját. A [profilok](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (a zebra webhelyének megnyitása) jó erőforrás lehet.

Amikor létrehozza a profilt a StageNow-ben, az utolsó lépésben válassza az **EXPORTÁLÁS Mdm**lehetőséget. Ez a lépés létrehoz egy XML-fájlt. Mentse el ezt a fájlt. Egy későbbi lépésben szüksége lesz rá.

- Javasoljuk, hogy tesztelje a profilt, mielőtt üzembe helyezné a szervezetében lévő eszközökön. Ha tesztelni szeretné, az utolsó lépésben, amikor a StageNow használatával hoz létre profilokat a számítógépen, használja a **tesztelési** lehetőségeket. Ezután használja fel a StageNow által generált fájlt a StageNow alkalmazással az eszközön.

  A StageNow alkalmazás az eszközön megjeleníti a profil tesztelésekor generált naplókat. A [StageNow-naplók használata az Android rendszerű Zebra-eszközökön az Intune-ban](android-zebra-mx-logs-troubleshoot.md) található információk a StageNow-naplók használatáról a hibák megismerése érdekében.

- Ha az alkalmazásokra hivatkozik, frissíti a csomagokat, vagy frissít más fájlokat a StageNow-profilban, azt szeretné, hogy az eszköz megkapja ezeket a frissítéseket. A frissítések beszerzéséhez az eszköznek csatlakoznia kell a StageNow központi telepítési kiszolgálójához a profil alkalmazása során. 

  Az Intune beépített funkciói az alábbi módosításokat is igénybe vehetik, többek között:

  - Alkalmazás-felügyeleti funkciók alkalmazások [hozzáadásához](../apps/apps-add.md), [üzembe helyezéséhez](../apps/apps-deploy.md), frissítéséhez és [figyeléséhez](../apps/apps-monitor.md) .
  - A [rendszer-és alkalmazás-frissítések](device-restrictions-android-for-work.md#device-owner-only) kezelése az Android Enterprise rendszert futtató eszközökön

A fájl tesztelése után a következő lépés a profil üzembe helyezése az eszközökön az Intune használatával.

- Egy vagy több MX-profilt is üzembe helyezhet egy eszközön.
- Több StageNow-profilt is exportálhat, és egyetlen XML-fájlba egyesítheti a beállításokat. Ezután töltse fel az XML-fájlt az Intune-ba az eszközökre való üzembe helyezéshez.

  > [!WARNING]
  > Ha több MX-profil is ugyanahhoz a csoporthoz van rendelve, és ugyanazt a tulajdonságot konfigurálja, ütközések lesznek az eszközön.
  >
  > Ha ugyanaz a tulajdonság többször van konfigurálva egyetlen MX-profilban, akkor az utolsó konfiguráció WINS.

## <a name="step-5-create-a-profile-in-intune"></a>5\. lépés: profil létrehozása az Intune-ban

Az Intune-ban hozzon létre egy eszköz konfigurációs profilt:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adja meg az új profil leíró nevét.
    - **Leírás:** Itt adhatja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: válassza az **Android**lehetőséget.
    - **Profil típusa**: válassza az **MX-profil lehetőséget (csak a zebra)** .

4. A **. XML formátumú MX-profilban**adja hozzá a [StageNow exportált](#step-4-create-a-device-management-profile-in-stagenow) XML-profil fájlját (ebben a cikkben).
5. A módosítások mentéséhez válassza az **OK** > **Létrehozás** lehetőséget. Ekkor létrejön a szabályzat, és megjelenik a listában.

    > [!TIP]
    > Biztonsági okokból a mentés után nem jelenik meg a profil XML-szövege. A szöveg titkosítva van, és csak csillagok (`****`) láthatók. A hivatkozáshoz ajánlott az MX-profilok másolatait menteni, mielőtt hozzáadja őket az Intune-hoz.

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Amikor az eszköz legközelebb ellenőrzi a konfigurációs frissítéseket, a rendszer az MX-profilt telepíti az eszközre. Az eszközök az Intune-nal szinkronizálhatók, ha az eszközök regisztrálva vannak, majd körülbelül 8 óránként. [A szinkronizálást is kényszerítheti az Intune-ban](../remote-actions/device-sync.md). Vagy az eszközön nyissa meg a **céges portál alkalmazás** > **Beállítások** > **szinkronizálás**lehetőséget. 

## <a name="update-a-zebra-mx-configuration-after-its-assigned"></a>A zebra MX konfigurációjának frissítése a hozzárendelés után

A zebra-eszközök MX-specifikus konfigurációjának frissítéséhez a következőket teheti: 

- Hozzon létre egy frissített StageNow XML-fájlt, szerkessze a meglévő Intune MX-profilt, és töltse fel az új StageNow XML-fájlt. Ez az új fájl felülírja az előző szabályzatot a profilban, és lecseréli az előző konfigurációt.
- Hozzon létre egy új StageNow XML-fájlt, amely különböző beállításokat konfigurál, hozzon létre egy új Intune MX-profilt, töltse fel az új StageNow XML-fájlt, és rendelje hozzá ugyanahhoz a csoporthoz. Több profil is telepítve van. Ha az új profil olyan beállításokat konfigurál, amelyek már létező profilokban vannak, akkor ütközések történnek.

## <a name="next-steps"></a>További lépések

- [Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
- [Használjon StageNow-naplókat a zebra-eszközök hibakereséséhez](android-zebra-mx-logs-troubleshoot.md).
