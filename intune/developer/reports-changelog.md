---
title: Intune-adattárház – módosítási napló
titleSuffix: Microsoft Intune
description: Ez a témakör a Microsoft Intune adattárház API változásainak listáját tartalmazza.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a37699542c5a9fe5268541aadc91b4c5d3ab5e9a
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78370176"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Az Intune-adattárház API módosítási naplója

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Maradjon naprakész az Intune-adattárház frissítéseivel kapcsolatban.

## <a name="1903-part-2"></a>1903 (2. rész)
_Kiadás dátuma 2019 április_

### <a name="beta-changes"></a>Béta-változások

A következő táblázat felsorolja a közelmúltban eltávolított gyűjteményeket és az Intune-adattárházban található cserék gyűjteményeket.

|    Gyűjtemény                          |    Változás     |    További információ                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    Eltávolítva    |    Használja helyette a [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts) .                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    Eltávolítva    |    Használja helyette a [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes) .                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    Eltávolítva    |    Használja helyette a [complianceStates](intune-data-warehouse-collections.md#compliancestates) .                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    Eltávolítva    |    Ehelyett használja az [eszközök](intune-data-warehouse-collections.md#devices) és [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) gyűjtemények `azureAdRegistered` tulajdonságát.                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    Eltávolítva    |    Használja helyette a [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates) .                                                                                                                                                                                                                                                                             |
|    currentUser                         |    Eltávolítva    |    Használja helyette a [felhasználók](intune-data-warehouse-collections.md#users) gyűjteményét.                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    Eltávolítva    |    A tulajdonságok többsége redundáns volt, vagy már a [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) vagy az [eszközök](intune-data-warehouse-collections.md#devices) gyűjteményében is megtalálható. A két gyűjteményben még nem szereplő **mdmDeviceInventoryHistories** -tulajdonságok már nem érhetők el. Tekintse meg az alábbi részleteket.    |

A következő táblázat felsorolja a korábban a **mdmDeviceInventoryHistories** -gyűjteményben és a módosítás/csere során megtalált régi tulajdonságokat. A **mdmDeviceInventoryHistories** összes olyan tulajdonsága el lett távolítva, amely nem szerepel az alábbi listában.

|    Régi tulajdonság                |    Módosítás/csere                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    cellularTechnology az eszközök gyűjteményében                                     |
|    deviceClientId              |    deviceId az eszközök gyűjteményében                                               |
|    deviceManufacturer          |    gyártó az eszközök gyűjteményében                                           |
|    deviceModel                 |    modell az eszközök gyűjteményében                                                  |
|    deviceName                  |    deviceName az eszközök gyűjteményében                                             |
|    deviceOsPlatform            |    deviceTypeKey az eszközök gyűjteményében                                          |
|    deviceOsVersion             |    osVersion a devicePropertyHistories-gyűjteményben                              |
|    deviceType                  |    deviceTypeKey az eszközök gyűjteményében, hivatkozó deviceTypes-gyűjtemény    |
|    encryptionState             |    encryptionState tulajdonság az eszközök gyűjteményében                           |
|    exchangeActiveSyncId        |    easDeviceId tulajdonság az eszközök gyűjteményében                               |
|    exchangeDeviceId            |    easDeviceId az eszközök gyűjteményében                                            |
|    IMEI                        |    IMEI az eszközök gyűjteményében                                                   |
|    isSupervised                |    isSupervised tulajdonság az eszközök gyűjteményében                              |
|    jailBroken                  |    feltört a devicePropertyHistories-gyűjteményben                             |
|    MEID                        |    meid tulajdonság az eszközök gyűjteményében                                      |
|    OEM                         |    gyártó az eszközök gyűjteményében                                           |
|    osName                      |    deviceTypeKey az eszközök gyűjteményében, hivatkozó deviceTypes-gyűjtemény    |
|    Telefonszám                 |    Telefonszám az eszközök gyűjteményében                                            |
|    platformType                |    modell az eszközök gyűjteményében                                                  |
|    termék                     |    deviceTypeKey az eszközök gyűjteményében                                          |
|    productVersion              |    osVersion a devicePropertyHistories-gyűjteményben                              |
|    serialNumber                |    serialNumber az eszközök gyűjteményében                                           |
|    storageFree                 |    freeStorageSpaceInBytes tulajdonság az eszközök gyűjteményében                   |
|    storageTotal                |    totalStorageSpaceInBytes tulajdonság az eszközök gyűjteményében                |
|    subscriberCarrierNetwork    |    subscriberCarrier tulajdonság az eszközök gyűjteményében                         |
|    wifimac                     |    wiFiMacAddress az eszközök gyűjteményében                                         |

A következő táblázat a [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) -gyűjteményben található tulajdonságok változásait sorolja fel: 

|    Régi tulajdonság                  |    Módosítás/csere                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, hivatkozó deviceCategories-gyűjtemény       |
|    certExpirationDate            |    Eltávolítva                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime az eszközök gyűjteményében                           |
|    deviceTypeKey                 |    deviceTypeKey az eszközök gyűjteményében                              |
|    easID                         |    easDeviceId az eszközök gyűjteményében                                |
|    enrolledByUser                |    Felhasználóazonosító az eszközök gyűjteményében                                     |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey az eszközök gyűjteményében                    |
|    graphDeviceIsCompliant        |    Eltávolítva                                                          |
|    graphDeviceIsManaged          |    Eltávolítva                                                          |
|    lastContact                   |    lastSyncDateTime az eszközök gyűjteményében                           |
|    lastContactNotification       |    Eltávolítva                                                          |
|    lastContactWorkplaceJoin      |    Eltávolítva                                                          |
|    lastExchangeStatusUtc         |    Eltávolítva                                                          |
|    lastModifiedDateTimeUTC       |    Eltávolítva                                                          |
|    lastPolicyUpdateUtc           |    Eltávolítva                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    gyártó                  |    gyártó az eszközök gyűjteményében                               |
|    mdmStatusKey                  |    complianceStateKey, hivatkozó complianceStates-gyűjtemény    |
|    modell                         |    modell az eszközök gyűjteményében                                      |
|    osFamily                      |    operatingSystem az eszközök gyűjteményében                            |
|    osRevisionNumber              |    osVersion az eszközök gyűjteményében                                  |
|    processorArchitecture         |    Eltávolítva                                                          |
|    referenceId                   |    azureAdDeviceId az eszközök gyűjteményében                            |
|    serialNumber                  |    serialNumber az eszközök gyűjteményében                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

A következő táblázat az [eszközök](intune-data-warehouse-collections.md#devices) gyűjteményében található tulajdonságok változásait sorolja fel: 

|    Régi tulajdonság                  |    Módosítás/csere                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, hivatkozó deviceCategories-gyűjtemény       |
|    certExpirationDate            |    Eltávolítva                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    Eltávolítva                                                          |
|    graphDeviceIsManaged          |    Eltávolítva                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    Eltávolítva                                                          |
|    lastContactWorkplaceJoin      |    Eltávolítva                                                          |
|    lastExchangeStatusUtc         |    Eltávolítva                                                          |
|    lastPolicyUpdateUtc           |    Eltávolítva                                                          |
|    mdmStatusKey                  |    complianceStateKey, hivatkozó complianceStates-gyűjtemény    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    Eltávolítva                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

A következő táblázat a [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities) -gyűjteményben található tulajdonságok változásait sorolja fel: 

|    Régi tulajdonság         |    Módosítás/csere         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

A következő táblázat a [mamApplications](intune-data-warehouse-collections.md#mamapplications) -gyűjteményben található tulajdonságok változásait sorolja fel: 

|    Régi tulajdonság       |    Módosítás/csere    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

A következő táblázat a [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances) -gyűjteményben található tulajdonságok változásait sorolja fel: 

|    Régi tulajdonság     |    Módosítás/csere    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

A következő táblázat a [mamCheckins](intune-data-warehouse-collections.md#mamcheckins) -gyűjteményben található tulajdonságok változásait sorolja fel: 

|    Régi tulajdonság      |    Módosítás/csere    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

A következő táblázat a [felhasználók](intune-data-warehouse-collections.md#users) gyűjteményében található tulajdonságok változásait sorolja fel: 

|    Régi tulajdonság             |    Módosítás/csere    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    Eltávolítva               |
|    endDateInclusiveUtc      |    Eltávolítva               |
|    isCurrent                |    Eltávolítva               |

## <a name="1903"></a>1903
_Kiadás dátuma 2019_

### <a name="v10-changes-reflecting-back-to-beta"></a>A Beta-re visszatükröző v 1.0-változások
Ha a 1.0-s verzió először mutatkozott be a 1808-ben, a Beta API néhány jelentős módon eltért. 1903 ezek a változások a Beta API-verzióba kerülnek vissza. Ha olyan fontos jelentésekkel rendelkezik, amelyek a Beta API verzióját használják, javasoljuk, hogy a módosítások elvégzése érdekében váltson át a jelentéseket a 1.0-s verzióra. Az adatraktár API-verzióival és a visszamenőleges kompatibilitással kapcsolatos további információkért tekintse meg az [API-verzióval kapcsolatos információkat](../reports-api-url.md) . 

## <a name="1902"></a>1902 
_Megjelent február 2019_

### <a name="power-bi-compliance-app"></a>Megfelelőségi alkalmazás Power BI 

Az Intune [megfelelőségi (adattárház-)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) alkalmazásával érheti el az Intune-adattárházat Power bi online-ban. Ezzel a Power BI alkalmazással mostantól a telepítés nélkül is elérheti és megoszthatja az előre létrehozott jelentéseket anélkül, hogy a böngészőt el kellene hagynia. 

> [!NOTE]
> Az Intune megfelelőségi alkalmazásához két további szűrő is alkalmazható.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>További szűrők hozzáadása az Intune megfelelőségi alkalmazásához
1. Nyissa meg az [Intune megfelelőségi (adattárház-)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) alkalmazását a böngészőben.
2. Kattintson a **nem megfelelő eszközök** elemre, és válassza a **nem megfelelő** elemet a **complianceStatus** szűrőben. 
3. Kattintson az **ismeretlen eszközök** elemre, és válassza a **még nem érhető el** lehetőséget a **complianceStatus** szűrőben. 

## <a name="1812"></a>1812 
_Megjelent december 2018_

### <a name="enrollment-activities-collection-released-to-v10"></a>Regisztrációs tevékenységek gyűjteménye 1.0-s verzióban 

A beléptetési tevékenységek gyűjteménye mostantól a 1.0-s verzióban érhető el. Ezt a gyűjteményt használhatja a regisztrálási hibák mennyiségének és a környezet trendjeinek a megismeréséhez. További információ: [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories)és [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons).

## <a name="1808"></a>1808
_Kiadás dátuma: 2018. augusztus_

### <a name="v10-collections"></a>v1.0 gyűjtemények  

Most már használható az Intune Adattárház v1.0-ás verziója az `api-version=v1.0` lekérdezésparaméter megadásával. Az Adattárház gyűjteményeinek frissítései hozzáadó jellegűek, és nem okoznak fennakadást a meglévő forgatókönyvekben.

### <a name="enrollment-activities-collection-released-to-beta"></a>Beléptetési tevékenységek gyűjteménye a Beta kiadásban

Az új `Enrollment Activities` gyűjtemény elérhető béta verzióban Ennek a gyűjteménynek a használatával megismerheti a regisztrálás előrehaladását, és megtekintheti a leggyakoribb hibákat. 


## <a name="1805"></a>1805
_Kiadás dátuma: 2018. május_

### <a name="correction-to-device-count-in-devices-collection"></a>Az **Eszközök** gyűjteményben megjelenő eszközszámmal kapcsolatos javítás 

Javítottuk az **Eszközök** gyűjteményt, amelyben így előfordulhat, hogy kevesebb eszköz fog megjelenni az `isDeleted` attribútum alapján történő szűrés esetén. Ez a csökkenés nem hiba, hanem a javítás eredménye. Az **Eszközök** csoportról bővebben az [Eszközök típusú entitások referenciája](reports-ref-devices.md) című témakörben olvashat. 


## <a name="1801"></a>1801
_Kiadás dátuma: 2018. január_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Alkalmazásalapú hitelesítés az Intune-adattárházban <!-- 1867540 -->

Beállíthat alkalmazásokat az Azure Active Directory (Azure AD) segítségével úgy, hogy hitelesítsék magukat az Intune-adattárházban. További információ: [Alkalmazásalapú hitelesítés az Intune-adattárházban](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Az Azure AD-beli és az Intune-beli hitelesítő adatokra vonatkozó követelmények <!-- 2077525 -->

- Már nincs szükség egy felhasználóhoz rendelt Intune-licencre, ha az Intune Data Warehouse-hoz szeretne hozzáférni (beleértve az API-t).
- Az Intune szerepkörének neve **Jelentések**ről **Intune Data Warehouse**-ra módosult. 

    További információ: [Az Azure AD-beli és az Intune-beli hitelesítő adatokra vonatkozó követelmények](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>Az OData-lekérdezés beállításai <!-- 2077711 -->

OData-lekérdezési paraméterként a következőt is használhatja: <code>$select</code>. A jelenlegi verzió a következő OData-lekérdezésparamétereket támogatja: <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> és <code>$top</code>. További információt [Az OData-lekérdezés beállításai](reports-api-url.md#odata-query-options) című témakörben találhat.

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Új entitások az adattárház adatmodelljében <!-- 2077804 -->

- A [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) entitást hozzáadtuk. A **MobileAppDeviceUserInstallStatus** a mobilalkalmazás telepítési állapotát jelöli egy adott eszközre és felhasználóra vonatkozóan.
- Az entitás ( [**MobileAppInstallStates**](reports-ref-application.md#mobileappinstallstates)) hozzá lett adva. A **MobileAppInstallState** entitás egy mobilalkalmazás telepítési állapotát jelöli, miután az hozzá lett rendelve egy eszközöket, felhasználókat vagy mindkettőt tartalmazó csoporthoz. 

## <a name="1710"></a>1710
_Kiadás dátuma: 2017. november_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Az aktuális felhasználó nevű új entitás jelenleg aktív felhasználói adatként van korlátozva <!-- 1544273 -->

A **Felhasználók** entitásgyűjtemény a vállalaton belül hozzárendelt licenccel rendelkező összes Azure Active Directory- (Azure AD-) felhasználót tartalmazza. A rekordok között akkor is ott vannak az adatgyűjtési időszakon belüli felhasználói állapotok, ha a felhasználót azóta eltávolították. Például az elmúlt egy hónap során hozzáadhattak az Intune-hoz egy felhasználót, majd el is távolíthatták onnan. A felhasználó a jelentés időpontjában nincs jelen, de az adatok tartalmazzák a felhasználót és állapotát. Ekkor létrehozhat egy olyan jelentést, amely megjeleníti a felhasználó korábbi jelenlétének időtartamát az adatokban.

Ezzel szemben az új **Aktuális felhasználó** entitásgyűjtemény csak azokat a felhasználókat tartalmazza, akiket nem távolítottak el. Az **Aktuális felhasználó** entitásgyűjtemény csak a jelenleg aktív felhasználókat tartalmazza. Az **Aktuális felhasználó** entitásgyűjteménnyel kapcsolatban az [Aktuális felhasználó típusú entitás referenciája](../reports-ref-current-user.md) oldalon talál további információkat.

## <a name="1709"></a>1709
_Kiadás dátuma: 2017. október_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Az Intune-adattárház adatmodelljébe felvett felhasználó-eszköz társítási entitások gyűjteménye <!-- 1187917 -->

A felhasználók és eszközök gyűjteményének társítását végző felhasználói eszköztársítási információ használatával jelentéseket és adatvizualizációkat hozhat létre. Az adatmodell a Power BI-fájlon (PBIX) keresztül érhető el az adattárház Intune-oldaláról az OData-végpont használatával vagy egyéni ügyfél létrehozásával. További információkért lásd: [Felhasználók és eszközök társítása](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Új entitások az adattárház adatmodelljében <!-- 1479526 --><!-- -->

- Új entitás: [**UserDeviceAssociation**](reports-ref-user-device.md). A **UserDeviceAssociation** tartalmazza a szervezet felhasználói hozzárendeléseit. A felhasználók és eszközök gyűjteményének társítását végző felhasználói eszköztársítási információ használatával jelentéseket és adatvizualizációkat hozhat létre.  
- Megjelent az [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md) entitás. Az **IntuneManagementExtension** mobileszközökhöz készült entitásokat tartalmaz, amelyek többek között a verziószámot és a telepítési állapotot követik nyomon.

## <a name="next-steps"></a>További lépések
- Heti összesítésben [olvashat az Intune újdonságairól](../fundamentals/whats-new.md). Emellett tájékozódhat a jövőbeni változtatásokról, a szolgáltatással kapcsolatos fontos bejelentésekről és a korábbi verziókról is.
- Tekintse meg [a Microsoft Intune blogját](https://go.microsoft.com/fwlink/?LinkID=273882).
