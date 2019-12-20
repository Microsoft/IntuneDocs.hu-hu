---
title: Egyéni beállítások – Windows holografikus for Business-eszközök – Microsoft Intune
description: 'Hozzáadhat vagy létrehozhat egy egyéni profilt, amelyet a Microsoft Intune-ban Windows Holographic for Businesst futtató eszközök (például a Microsoft Hololens) OMA-URI-beállításaihoz használhat. Az alábbi beállításokat adhatja meg: AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates, valamint az ApplicationLaunchRestrictions szabályzatkonfigurációs szolgáltató (CSP) beállításait.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.article: article
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.topic: reference
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d986097f4f3dda0278d767c911b8c1e957e9c010
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206737"
---
# <a name="use-custom-settings-for-windows-holographic-for-business-devices-in-intune"></a>Egyéni beállítások használata az Intune-ban a Windows Holographic for Business-eszközökhöz

A Microsoft Intune-ban „egyéni profilokkal” adhat meg vagy hozhat létre egyéni beállításokat a Windows Holographic for Business-eszközökhöz. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

A Windows Holographic for Business egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók konfigurálásához. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik az eszközök funkcióit.

A Windows Holographic for Business számos konfigurációs szolgáltatásból származó beállítást támogat. A konfigurációszolgáltatásokról a [Bevezetés a konfigurációszolgáltatásokba (CSP) informatikai szakértők számára](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) című témakörben olvashat. A Windows Holographic által támogatott konkrét konfigurációszolgáltatók listáját a [Windows Holographic által támogatott CSP-k](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) című cikkben találja.

Ha egy adott beállítást keres, ne feledje, hogy a [Windows Holographic for Business eszközkorlátozási profil](device-restrictions-windows-holographic.md) számos beépített beállítást tartalmaz. Így nem feltétlenül kell egyéni értékeket megadnia.

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt a Windows Holographic for Business-eszközökhöz, és a javasolt OMA-URI-beállítások listáját is tartalmazza.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **konfigurációs profilok** lehetőséget > a **profil létrehozása**elemet.
3. Adja meg a következő beállításokat:

    - **Név**: adjon meg egy leíró nevet a profilhoz. Nevezze el a profilokat, hogy később könnyen azonosítható legyen. Egy jó profilnév például **Hololens egyéni profil**.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **Platform**: válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: válassza az **Egyéni**lehetőséget.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név** – Adjon meg egy egyedi nevet az OMA-URI-beállítás számára, amellyel az egyszerűen azonosítható a beállítások listájában.
    - **Leírás**: Adjon meg egy olyan leírást, amely áttekintést ad a beállításról és egyéb fontos részleteket tartalmaz.
    - **OMA-URI** (megkülönbözteti a kis- és nagybetűket) – Adja meg azt az OMA-URI azonosítót, amelyet beállításként kíván használni.
    - **Adattípus**: válassza ki az OMA-URI beállításhoz használni kívánt adattípust. A választható lehetőségek:

        - Sztring
        - Sztring (XML-fájl)
        - Dátum és időpont
        - Egész szám
        - Lebegőpontos szám
        - Logikai
        - Base64 (fájl)

    - **Érték** – Adja meg a megadott OMA-URI azonosítóhoz társítandó értéket. Az érték a választott adattípustól függ. Ha például a **dátum és idő**lehetőséget választja, válassza ki a kívánt értéket a dátumválasztó listából.

    Néhány beállítás megadása után válassza az **Exportálás** lehetőséget. Az **Exportálás** a hozzáadott értékek listáját hozza létre egy vesszővel tagolt (.csv) fájlban.

5. A módosítások mentéséhez válassza az **OK** gombot. Szükség szerint adjon hozzá további beállításokat.
6. Ha elkészült, válassza az **OK** > **Létrehozás** lehetőséget az Intune-profil létrehozásához. Ha elkészült, a profil megjelenik az **eszközök – konfigurációs profilok** listában.

## <a name="recommended-custom-settings"></a>Ajánlott egyéni beállítások

Az alábbi beállítások a Windows Holographic for Business rendszert futtató eszközökön lehetnek hasznosak:

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Egész szám<br/>0 – Nem engedélyezett<br/>1 – engedélyezett (alapértelmezés)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Egész szám<br/>0 – A frissítési szolgáltatás nincs engedélyezve <br/>1 – A frissítési szolgáltatás engedélyezve van (alapértelmezés).|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Egész szám<br/>0 – Nem engedélyezett<br/>1 – engedélyezett (alapértelmezés)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Egész szám<br/>0 – Nincs konfigurálva. Az eszköz minden alkalmazható frissítést telepít.<br/>1 – Az eszköz csak azokat a frissítéseket telepíti, amelyek alkalmazhatók és a jóváhagyott frissítések listáján is szerepelnek. Állítsa ezt a szabályzatot 1 értékre, ha azt szeretné, hogy az informatikai részleg vezérelje az eszközfrissítések üzembe helyezését, például ha az üzembe helyezés előtt tesztelésre van szükség.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|0 és 23 közötti egész szám, amelynél a 0=éjfél és 23=este 11 óra<br/>Az alapértelmezett érték 3.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Sztring<br/>URL – Az eszköz frissítéseket keres a WSUS-kiszolgálótól a megadott URL-címen.<br/>Nincs beállítva – Az eszköz a Microsoft Update szolgáltatásból keres frissítéseket.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**Fontos**<br/>El kell olvasnia és el kell fogadnia a végfelhasználói nevében a frissítési licencfeltételeket. Amennyiben ezt nem teszi meg, az a jogi vagy szerződéses kötelezettségek megszegésének számít.|A frissítések jóváhagyásának és a licencfeltételek a végfelhasználók nevében történő elfogadásának csomópontja.<br/><br/>További információ: [Frissítési CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp).|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**Fontos**<br/>Az AppLocker CSP-cikk escape-karakterrel jelölt XML-példákat használ. A beállítások egyéni Intune-profilokkal való konfigurálásához hagyományos XML-t kell használnia.|Sztring<br/>További információ: [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp).|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Egész szám<br/>0 – azonnal törölje, ha az eszköz aktív felhasználók nélküli állapotba tér vissza<br/>1 – törölje a tárolókapacitási küszöbérték elérése esetén (alapértelmezett)<br/>2 – törölje a tárolókapacitási küszöbérték elérése esetén is és inaktív profil esetén is|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|Logikai<br/>True – engedélyezés<br/>False – letiltás (alapértelmezés)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|Egész szám<br/>Az alapértelmezett érték 30.|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|Egész szám<br/>Az alapértelmezett érték 25.|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Adattípus|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|Egész szám<br/>Az alapértelmezett érték 50.|

## <a name="find-the-policies-you-can-configure"></a>A konfigurálható szabályzatok megkeresése

A [Windows Holographic for Business által támogatott CSP-k](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) című cikkben megtalálja Windows Holographic által támogatott konfigurációszolgáltatók teljes listáját. Nem minden beállítás kompatibilis a Windows Holographic összes verziójával. A [Windows Holographic által támogatott CSP-ket](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) felsoroló cikkben szereplő táblázat tartalmazza az egyes CSP-hez tartozó támogatott verziók listáját.

Az Intune nem támogatja a [Windows Holographic által támogatott CSP-ket](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) ismertető cikkben felsorolt összes beállítást. Ha tudni szeretné, hogy az Intune támogatja-e a kívánt beállítást, nyissa meg a beállításhoz tartozó cikket. Minden beállítás oldalán szerepelnek az általa támogatott műveletek. Az Intune használatához a beállításnak támogatnia kell a **Hozzáadás** vagy a **Csere** műveletet.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Ezután [rendelje hozzá a profilt](../device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

Hozzon létre egy [egyéni profilt a Windows 10-es eszközökön](../custom-settings-windows-10.md).
