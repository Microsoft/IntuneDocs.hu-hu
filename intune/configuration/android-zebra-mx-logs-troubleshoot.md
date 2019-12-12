---
title: StageNow-naplók használata androidos Zebra-eszközökön a Microsoft Intune-Azure-ban | Microsoft Docs
description: A StageNow androidos eszközökön Microsoft Intune használatával történő használatakor gyakori problémák és megoldások találhatók. Azt is megtudhatja, hogyan kérhet naplókat, és hogyan olvashatja el a naplókat a sikeres vagy sikertelen hibákhoz.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7ed93c86d3fbe7ed7a6ac5d4b1a3494fb55f2bc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506993"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Az androidos Zebra-eszközök lehetséges problémáinak elhárítása és megjelenítése Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune a [Zebra Mobility Extensions (MX) segítségével kezelheti az androidos Zebra-eszközöket](android-zebra-mx-overview.md). A zebra-eszközök használatakor a StageNow profilokat hozhat létre a beállítások kezeléséhez, és feltöltheti őket az Intune-ba. Az Intune a StageNow alkalmazás használatával alkalmazza a beállításokat az eszközökön. A StageNow alkalmazás egy részletes naplófájlt is létrehoz a hibakereséshez használt eszközön.

Ez a funkció az alábbiakra vonatkozik:

- Android:

Például létrehozhat egy profilt a StageNow-ben egy eszköz konfigurálásához. A StageNow-profil létrehozásakor az utolsó lépés létrehoz egy fájlt a profil teszteléséhez. Ezt a fájlt a StageNow alkalmazással használja az eszközön.

Egy másik példában létrehozhat egy profilt a StageNow-ben, és tesztelheti. Az Intune-ban adja hozzá a StageNow-profilt, majd rendelje hozzá a zebra-eszközökhöz. A hozzárendelt profil állapotának ellenőrzésekor a profil magas szintű állapotot mutat be.

Mindkét esetben további részleteket is megtudhat a StageNow naplófájlból, amelyet a rendszer minden alkalommal ment az eszközön, amikor StageNow-profilt alkalmaz.

Néhány probléma nem kapcsolódik a StageNow-profil tartalmához, és nem tükröződik a naplókban.

Ez a cikk bemutatja, hogyan olvashatja el a StageNow-naplókat, és megtekintheti azokat a lehetséges problémákat, amelyek a naplókban esetleg nem látható Zebra-eszközökkel kapcsolatosak.

A zebra [mobilitási bővítménnyel rendelkező Zebra-eszközök használata és kezelése](android-zebra-mx-overview.md) további információkat tartalmaz a szolgáltatással kapcsolatban.

## <a name="get-the-logs"></a>Naplók beolvasása

### <a name="use-the-stagenow-app-on-the-device"></a>A StageNow alkalmazás használata az eszközön
Ha közvetlenül a számítógépen lévő StageNow használatával tesztel egy profilt, ahelyett, [hogy az Intune-t használja a profil üzembe helyezéséhez](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), a StageNow alkalmazás az eszközön menti a naplókat a tesztből. A naplófájl beszerzéséhez használja a StageNow alkalmazás **további (...)** beállítását az eszközön.

### <a name="get-logs-using-android-debug-bridge"></a>Naplók beolvasása az Android hibakeresési híddal
Ha a profil már telepítve van az Intune-nal, a naplók beszerzéséhez az eszközt az [Android debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) használatával (az Android webhelyének megnyitásakor) kapcsolja be.

Az eszközön a rendszer menti a naplókat `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Naplók beolvasása e-mailben
A naplók az Intune-nal való üzembe helyezését követően a végfelhasználók e-mailben elérhetik a naplókat az eszközön lévő e-mail-alkalmazás használatával. A zebra eszközön nyissa meg a Céges portál alkalmazást, és [küldje el a naplókat](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). A naplók küldése funkcióval egy PowerLift-incidens AZONOSÍTÓját is létrehozhatja, amelyet akkor hivatkozhat, ha kapcsolatba lép a Microsoft ügyfélszolgálatával.

## <a name="read-the-logs"></a>Naplók olvasása

Amikor megtekinti a naplókat, hiba történt, amikor megjelenik a `<characteristic-error>` címkéje. A hiba részletei a `<parm-error>` címkére > `desc` tulajdonságra íródnak.

## <a name="error-types"></a>Hibák típusai

A zebra-eszközök különböző hibajelentési szinteket tartalmaznak:

- A CSP nem támogatott az eszközön. Például az eszköz nem egy mobil eszköz, és nem rendelkezik mobil kezelővel.
- Az MX vagy az OSX verziója nem egyezik. Minden CSP verziója. A teljes támogatási mátrixért lásd a [Zebra dokumentációját](http://techdocs.zebra.com/mx/) (a zebra webhelyének megnyitása).
- Az eszköz egy másik problémát vagy hibát jelez.

## <a name="examples"></a>Példák

Például a következő bemeneti profillal rendelkezik:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

A naplóban az XML megegyezik a bemenettel. Ez a megfelelő kimenet azt jelenti, hogy a profil sikeresen alkalmazva lett az eszközre, hibák nélkül:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

Egy másik példában a következő adatok szerepelnek:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

A napló hibaüzenetet jelenít meg, mivel `<characteristic-error>` címkét tartalmaz. Ebben az esetben a profil olyan Android-csomagot (APK) próbált meg telepíteni, amely nem létezik a megadott elérési úton:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Egyéb lehetséges problémák a zebra-eszközökkel

Ez a szakasz a zebra-eszközök az eszköz rendszergazdájával való használatakor esetlegesen megjelenő esetleges problémákat sorolja fel. Ezek a problémák nem szerepelnek a StageNow-naplókban.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView elavult

Ha a régebbi eszközök bejelentkeznek a céges portál alkalmazással, a felhasználók egy üzenetet láthatnak arról, hogy a webnézet összetevő elavult, és frissítenie kell a szolgáltatást. Ha az eszközön telepítve van a Google Play, kapcsolja össze az internettel, és keressen frissítéseket. Ha az eszközön nincs telepítve a Google Play, szerezze be az összetevő frissített verzióját, és alkalmazza azt az eszközökre. Vagy frissítsen a zebra által kiadott legújabb eszköz operációs rendszerre.

### <a name="management-actions-take-a-long-time"></a>A felügyeleti műveletek hosszú ideig tartanak

Ha a Google Play-szolgáltatások nem érhetők el, néhány feladat akár 8 órát is igénybe vehet. [Az Androidhoz készült Intune céges portál alkalmazás korlátai](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (egy másik Microsoft-webhely megnyitása) jó erőforrás lehet.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Az eszköz hamisításának gyanúja" mutatja az Intune-ban

Ez a hiba azt jelenti, hogy az Intune egy nem Zebra típusú Android-eszközt jelent, amely a modelljét és a gyártóját Zebra-eszközként jelenti.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Céges portál alkalmazás régebbi a minimálisan szükséges verziónál

Előfordulhat, hogy az Intune frissíti a Céges portál alkalmazás minimálisan szükséges verzióját. Ha a Google Play nincs telepítve az eszközön, a Céges portál alkalmazás nem lesz automatikusan frissítve. Ha a minimálisan szükséges verzió újabb, mint a telepített verzió, akkor a Céges portál-alkalmazás működése leáll. Frissítsen a legújabb Céges portál alkalmazásra a [közvetlen telepítési használatával a zebra-eszközökön](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>További lépések

[Zebra-vitafórumok](https://developer.zebra.com/community/home/discussions) (a zebra webhely megnyitása)

[Zebra-eszközök használata és kezelése a zebra Mobility-bővítményekkel az Intune-ban](android-zebra-mx-overview.md)
