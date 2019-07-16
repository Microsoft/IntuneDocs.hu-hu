---
title: Eszközök – Intune-adattárház
titleSuffix: Microsoft Intune
description: Az Intune-adattárház API-ban található entitásgyűjtemények eszközkategóriájára vonatkozó referencia-témakör.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e82ef9cc8e79332665db99d29ed511918f8c77b7
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884711"
---
# <a name="reference-for-devices-entities"></a>Eszközök típusú entitások referenciája

Az **Eszközök** kategória az információkat nyomon követő mobileszközökhöz tartozó entitásokat tartalmazza, egyebek mellett az alábbiakat:

- Eszköz típusa
- Eszköz regisztrációja és a regisztráció állapota
- Az eszközök tulajdonjoga
- Eszközkezelés állapota
- Az eszköz Azure AD-tagságának állapota
- Beléptetés állapota
- Előzményadatok az eszközről
- Az eszközön lévő alkalmazások listája

## <a name="devicetypes"></a>DeviceTypes

A **DeviceTypes** entitás az adattárház más entitásai által hivatkozott eszköztípust jelöli. Az eszköztípus általában leírja az eszköz típusát, gyártóját vagy mindkettőt.

| Tulajdonság  | Leírás |
|---------|------------|
| DeviceTypeID |Az eszköztípus egyedi azonosítója |
| DeviceTypeKey |Az eszköztípus egyedi azonosítója az adattárházban – helyettes kulcs |
| DeviceTypeName |Eszköz típusa |

### <a name="example"></a>Példa

| DeviceTypeID  | Név | Leírás |
|---------|------------|--------|
| 0 |Asztali |Windows asztali eszköz |
| 1 |WindowsRT |Windows RT rendszerű eszköz |
| 2 |WinMO6 |Windows Mobile 6.0 rendszerű eszköz |
| 3 |Nokia |Nokia-eszköz |
| 4 |WindowsPhone |Windows Phone rendszerű eszköz |
| 5 |Mac |Mac rendszerű eszköz |
| 6 |WinCE |Windows CE rendszerű eszköz |
| 7 |WinEmbedded |Windows Embedded-eszköz |
| 8 |IPhone |iPhone-eszköz |
| 9 |IPad |iPad-eszköz |
| 10 |IPod |iPod-eszköz |
| 11 |Android |Az Eszközadminisztrátorral felügyelt Android-eszköz |
| 12 |ISocConsumer |iSoc Consumer-eszköz |
| 14 |MacMDM |A beépített MDM-ügynökkel felügyelt Mac OS X-eszköz |
| 15 |HoloLens |HoloLens-eszköz |
| 16 |SurfaceHub |Surface Hub-eszköz |
| 17 |AndroidForWork |Android Profile Owner használatával felügyelt Android-eszköz |
| 100 |Blackberry |Blackberry-eszköz |
| 101 |Palm |Palm-eszköz |
| 255 |Ismeretlen |Ismeretlen eszköztípus |

## <a name="enrollmentactivities"></a>enrollmentActivities 
Az **EnrollmentActivity** entitás az eszközök regisztrálásának tevékenységét jelzi.

| Tulajdonság                      | Leírás                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | A beléptetési tevékenység rögzítési dátumának kulcsa.               |
| deviceEnrollmentTypeKey       | A beléptetés típusának kulcsa.                                        |
| deviceTypeKey                 | Az eszköz típusának kulcsa.                                                |
| enrollmentEventStatusKey      | A regisztráció sikerességét vagy hibáját jelző állapot kulcsa.    |
| enrollmentFailureCategoryKey  | A beléptetési hiba kategóriájának kulcsa (ha a regisztráció sikertelen volt).        |
| enrollmentFailureReasonKey    | A beléptetési hiba okának kulcsa (ha a regisztráció sikertelen volt).          |
| osVersion                     | Az eszköz operációs rendszerének verziója.                               |
| count                         | A fenti besorolásoknak megfelelő beléptetési tevékenységek teljes száma.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
Az **EnrollmentEventStatus** entitás az eszközök regisztrálásának eredményét jelzi.

| Tulajdonság                   | Leírás                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | A regisztrációs állapot egyedi azonosítója az adattárházban (helyettes kulcs)  |
| enrollmentEventStatusName  | A beléptetési állapot neve. Lásd az alábbi példákat.                            |

### <a name="example"></a>Példa

| enrollmentEventStatusName  | Leírás                            |
|----------------------------|----------------------------------------|
| Siker                    | Sikeres eszközök beléptetése         |
| Meghiúsult                     | Sikertelen eszközök beléptetése             |
| Nem érhető el              | A beléptetési állapot nem érhető el.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
A **EnrollmentFailureCategory** entitás jelzi, hogy az eszközök regisztrálásának miért nem sikerült. 

| Tulajdonság                       | Leírás                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | A beléptetési hiba kategóriájának egyedi azonosítója az adattárházban (helyettes kulcs)  |
| enrollmentFailureCategoryName  | A beléptetési hiba kategóriájának neve. Lásd az alábbi példákat.                            |

### <a name="example"></a>Példa

| enrollmentFailureCategoryName   | Leírás                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Nem alkalmazható                  | A beléptetési hiba kategóriája nem alkalmazható.                                                            |
| Nem érhető el                   | A beléptetési hiba kategóriája nem érhető el.                                                             |
| Ismeretlen                         | Ismeretlen hiba.                                                                                                |
| Authentication                  | A hitelesítés sikertelen.                                                                                        |
| Authorization                   | A hívás hitelesítése megtörtént, de nem jogosult a regisztrálásra.                                                         |
| AccountValidation               | Nem sikerült érvényesíteni a fiókot a beléptetéshez. (Fiók letiltva, regisztráció nincs engedélyezve)                      |
| UserValidation                  | A felhasználót nem lehetett érvényesíteni. (A felhasználó nem létezik, hiányzó licenc)                                           |
| DeviceNotSupported              | A mobileszköz-kezelés nem támogatja az eszközt.                                                         |
| Karbantartás                   | A fiók karbantartás alatt áll.                                                                                    |
| BadRequest                      | Az ügyfél elküldte a szolgáltatás által nem értelmezhető/támogatott kérelmet.                                        |
| FeatureNotSupported             | A regisztráció során használt szolgáltatás (ok) nem támogatott ehhez a fiókhoz.                                        |
| EnrollmentRestrictionsEnforced  | A rendszergazda által konfigurált regisztrációs korlátozások blokkolták ezt a beléptetést.                                          |
| ClientDisconnected              | Az ügyfél túllépte az időkorlátot, vagy a felhasználó megszakította a regisztrációt.                                                        |
| UserAbandonment                 | A regisztrációt a végfelhasználó felhagyta. (A végfelhasználó elindította a bevezetést, de nem tudta időben befejezni a végrehajtását)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
A **EnrollmentFailureReason** entitás egy adott meghibásodási kategórián belül egy eszköz regisztrálási hibájának részletesebb okát jelzi.  

| Tulajdonság                     | Leírás                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | A beléptetési hiba okának egyedi azonosítója az adattárházban (helyettes kulcs)  |
| enrollmentFailureReasonName  | A beléptetési hiba okának neve. Lásd az alábbi példákat.                            |

### <a name="example"></a>Példa

| enrollmentFailureReasonName      | Leírás                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nem alkalmazható                   | A beléptetési hiba oka nem alkalmazható.                                                                                                                                                       |
| Nem érhető el                    | A beléptetési hiba oka nem érhető el.                                                                                                                                                        |
| Ismeretlen                          | Ismeretlen hiba.                                                                                                                                                                                         |
| UserNotLicensed                  | A felhasználó nem található az Intune-ban, vagy nem rendelkezik érvényes licenccel.                                                                                                                                     |
| UserUnknown                      | A felhasználó nem ismeri az Intune-t.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Csak egy felhasználó regisztrálhat egy eszközt. Ezt az eszközt korábban egy másik felhasználó regisztrálta.                                                                                                                |
| EnrollmentOnboardingIssue        | Az Intune mobileszköz-felügyeleti (MDM-) szolgáltató még nincs konfigurálva.                                                                                                                                 |
| AppleChallengeIssue              | Az iOS felügyeleti profil telepítése késleltetve vagy sikertelen volt.                                                                                                                                         |
| AppleOnboardingIssue             | Az Intune-ba való regisztráláshoz Apple MDM push-tanúsítvány szükséges.                                                                                                                                       |
| DeviceCap                        | A felhasználó a maximálisan engedélyezettnél több eszközt próbált regisztrálni.                                                                                                                                        |
| AuthenticationRequirementNotMet  | Az Intune-beléptetési szolgáltatás nem tudta engedélyezni a kérelmet.                                                                                                                                            |
| UnsupportedDeviceType            | Ez az eszköz nem felel meg az Intune-regisztráció minimális követelményeinek.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | Az eszközt nem sikerült regisztrálni egy konfigurált regisztrációs korlátozási szabály miatt.                                                                                                                          |
| BulkDeviceNotPreregistered       | Nem található az eszköz nemzetközi mobileszköz-azonosítója (IMEI) vagy sorozatszáma.  Ez az azonosító nélkül az eszközöket a rendszer a jelenleg blokkolt személyes tulajdonú eszközökként ismeri fel.  |
| FeatureNotSupported              | A felhasználó olyan szolgáltatás elérésére tett kísérletet, amely még nem lett közzétéve az összes ügyfél számára, vagy nem kompatibilis az Intune-konfigurációval.                                                            |
| UserAbandonment                  | A regisztrációt a végfelhasználó felhagyta. (A végfelhasználó elindította a bevezetést, de nem tudta időben befejezni a végrehajtását)                                                                                           |
| APNSCertificateExpired           | Az Apple-eszközök nem kezelhetők lejárt Apple MDM push-tanúsítvánnyal.                                                                                                                            |
## <a name="ownertypes"></a>OwnerTypes

Az **EnrollmentTypes** entitás jelzi, hogy az eszköz tulajdonosa a vállalat, magánszemély vagy ismeretlen.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| ownerTypeID |A tulajdonostípus egyedi azonosítója. | |
| ownerTypeKey |A tulajdonostípus egyedi azonosítója az adattárházban – helyettes kulcs. | |
| ownerTypeName |Az eszközök tulajdonosának típusát jelzi:  <br>Vállalati – az eszköz vállalati tulajdonban van. <br>Personal – az eszköz saját tulajdonban van (BYOD).  <br>Unknown – nincs információ az eszközről. |Vállalati személyes ismeretlen |

> [!Note]  
> Az eszközökhöz tartozó dinamikus csoportok létrehozásakor a AzureAD a szűrő `Company`értékét `deviceOwnership` kell beállítania. `ownerTypeName` További információ: [eszközök szabályai](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="managementstates"></a>ManagementStates

A **ManagementStates** entitás az eszköz állapotáról ad információt. Ezek a részletek hasznosak lehetnek távoli műveletek végrehajtásakor és jailbreakelt vagy rootolt eszköz esetén.

| Tulajdonság  | Leírás |
|---------|------------|
| managementStateID | A kezelés állapotának egyedi azonosítója. |
| managementStateKey | A kezelés állapotának egyedi azonosítója az adattárházban – helyettes kulcs. |
| managementStateName | Az eszközön végrehajtott távoli művelet állapotát jelöli. |

### <a name="example"></a>Példa

| managementStateID  | Név | Leírás |
|---------|------------|--------|
| 0 |Kezelt | Kezelt, függőben lévő távoli műveletek nélkül. |
| 1 |RetirePending | Az eszköz kivonására vonatkozó parancs van függőben. |
| 2 |RetireFailed | A kivonás parancs sikertelen volt az eszközön. |
| 3 |WipePending | Az eszközön lévő összes adat törlésére vonatkozó parancs van függőben. |
| 4 |WipeFailed | Az eszközön lévő összes adat törlésére vonatkozó parancs sikertelen volt az eszközön. |
| 5 |Nem kifogástalan | Nem kifogástalan állapot. |
| 6 |DeletePending | Törlés parancs van függőben. |
| 7 |RetireIssued | Kivonás parancs van kiadva az eszközre. |
| 8 |WipeIssued | Parancs van kiadva az összes adat törlésére. |
| 9 |WipeCanceled | Az összes adat törlésére vonatkozó parancsot visszavonták. |
| 10 |RetireCanceled | A kivonási parancsot visszavonták. |
| 11 |Discovered | Az eszközt újonnan derítette fel az Intune, és amint az első alkalommal bejelentkezik, Managed (kezelt) állapotba fog kerülni. |

## <a name="managementagenttypes"></a>ManagementAgentTypes

A **ManagementAgentTypes** az eszköz kezelésére szolgáló ügynököket jelöli.

| Tulajdonság  | Leírás |
|---------|------------|
| ManagementAgentTypeID | A kezelőügynök típusának egyedi azonosítója. |
| ManagementAgentTypeKey | A kezelőügynök típusának egyedi azonosítója az adattárházban – helyettes kulcs. |
| ManagementAgentTypeName |Megadja, hogy milyen ügynök szolgál az eszköz kezelésére. |

### <a name="example"></a>Példa

| ManagementAgentTypeID  | Név | Leírás |
|---------|------------|--------|
| 1 |EAS | Az Exchange Active Sync szolgáltatással kezelt eszköz |
| 2 |MDM | MDM-ügynökkel kezelt eszköz |
| 3 |EasMdm | Az Exchange Active Sync szolgáltatással és MDM-ügynökkel kezelt eszköz |
| 4 |IntuneClient | Az Intune PC-ügynökkel kezelt eszköz |
| 5 |EasIntuneClient | Az Exchange Active Sync szolgáltatással és Intune PC-ügynökkel kezelt eszköz |
| 8 |ConfigManagerClient | A System Center Configuration Manager-ügynökkel kezelt eszköz |
| 16 |Ismeretlen | A kezelőügynök típusa ismeretlen |

## <a name="devices"></a>Eszközök

A **Devices** entitás felsorolja az összes kezelt regisztrált eszközt és azok lényeges tulajdonságait.

|          Tulajdonság          |                                                                                       Leírás                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Az eszköz egyedi azonosítója az adattárházban – helyettes kulcs.                                                                                                               |
| DeviceId                   | Az eszköz egyedi azonosítója.                                                                                                                                                     |
| Eszköznév                 | Az eszköz neve az eszközök elnevezését megengedő platformokon. Más platformokon az Intune más tulajdonságok alapján hoz létre nevet. Ez az attribútum nem lehet elérhető az összes eszköz számára. |
| DeviceTypeKey              | Az eszközhöz tartozó eszköztípus attribútum kulcsa.                                                                                                                                    |
| DeviceRegistrationState    | Az eszközhöz tartozó ügyfél-regisztrációs állapot attribútum kulcsa.                                                                                                                      |
| OwnerTypeKey               | Az eszközhöz tartozó tulajdonostípus attribútum (corporate, personal, vagy unknown) kulcsa.                                                                                                    |
| EnrolledDateTime           | Az eszköz regisztrálásának dátuma és időpontja.                                                                                                                                         |
| LastSyncDateTime           | Az eszköz utolsó Intune-bejelentkezése.                                                                                                                                              |
| ManagementAgentKey         | Az eszközhöz társított kezelőügynök kulcsa.                                                                                                                             |
| ManagementStateKey         | Az eszközhöz társított kezelési állapot, beleértve a távoli műveletek utolsó állapotát, és hogy az eszköz jailbreakelt vagy rootolt-e.                                                |
| AzureADDeviceId            | Az Azure-eszközazonosító ehhez az eszközhöz.                                                                                                                                                  |
| AzureADRegistered          | Regisztrálva van-e az eszköz az Azure Active Directoryban.                                                                                                                             |
| DeviceCategoryKey          | Az eszközhöz társított kategória kulcsa.                                                                                                                                     |
| DeviceEnrollmentType       | Az eszközhöz társított, a regisztráció módját jelző regisztrációtípus kulcsa.                                                                                             |
| ComplianceStateKey         | Az eszközhöz társított megfelelőségi állapot kulcsa.                                                                                                                             |
| OSVersion                  | Az eszközön futó operációs rendszer verziószáma.                                                                                                                                                |
| EasDeviceId                | Az eszköz Exchange ActiveSync-azonosítója.                                                                                                                                                  |
| a sorozatszám               | a sorozatszám                                                                                                                                                                           |
| UserId                     | Az eszközhöz társított felhasználó egyedi azonosítója.                                                                                                                           |
| RowLastModifiedDateTimeUTC | Az eszköz adattárházban történő utolsó módosításának dátuma és időpontja (UTC).                                                                                                       |
| Gyártó               | Az eszköz gyártója                                                                                                                                                             |
| Modell                      | Az eszköz típusa                                                                                                                                                                    |
| OperatingSystem            | Az eszközön futó operációs rendszer. Windows, iOS stb.                                                                                                                                   |
| IsDeleted                  | Bináris érték, amely azt jelzi, hogy az eszköz törölve van vagy sem.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Az Android biztonsági javítási szintje                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Az eszköz felügyeleti állapota                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Szabad tárterület bájtban.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Összes tárterület bájtban.                                                                                                                                                                |
| EncryptionState            | Az eszköz titkosítási állapota.                                                                                                                                                      |
| SubscriberCarrier          | Az eszköz előfizetői szolgáltatója                                                                                                                                                       |
| PhoneNumber                | Az eszköz telefonszáma                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Az eszköz mobiltechnológiája                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

A **DevicePropertyHistory** entitásban ugyanazon tulajdonságok szerepelnek, mint a Devices (Eszközök) táblában, amely minden eszközről napi pillanatképet tárol 90 napra visszamenőleg. A DateKey mező az egyes sorok napját jelzi.

|          Tulajdonság          |                                                                                      Leírás                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | A napot megadó dátumtáblázat-hivatkozás.                                                                                                                                          |
| DeviceKey                  | Az eszköz egyedi azonosítója az adattárházban – helyettes kulcs. Az Intune-eszközazonosítót tartalmazó eszköztáblára mutató hivatkozás.                               |
| Eszköznév                 | Az eszköz neve az eszközök elnevezését megengedő platformokon. Más platformokon az Intune hoz létre nevet más tulajdonságok alapján. Ez az attribútum nem lehet elérhető az összes eszköz számára. |
| DeviceRegistrationStateKey | Az eszközhöz tartozó eszközregisztrációs állapot attribútum kulcsa.                                                                                                                    |
| OwnerTypeKey               | Az eszközhöz tartozó tulajdonostípus attribútum kulcsa: corporate (vállalati), personal (személyes), vagy unknown (ismeretlen).                                                                                                  |
| ManagementStateKey         | Az eszközhöz társított kezelési állapot, beleértve a távoli műveletek utolsó állapotát, és hogy az eszköz jailbreakelt vagy rootolt-e.                                                |
| AzureADRegistered          | Regisztrálva van-e az eszköz az Azure Active Directoryban.                                                                                                                             |
| ComplianceStateKey         | Kulcs a ComplianceState-hez.                                                                                                                                                            |
| OSVersion                  | Operációs rendszer verziója.                                                                                                                                                                          |
| JailBroken                 | Az, hogy az eszköz jailbreakelve vagy rootolva van-e.                                                                                                                                         |
| DeviceCategoryKey          | Az eszközhöz tartozó eszközkategória attribútum kulcsa. 

## <a name="applicationinventory"></a>ApplicationInventory

Az **ApplicationInventory** entitás a leltárkészítés pillanatában az eszközön talált alkalmazásokat sorolja fel.


|      Tulajdonság      |                       Leírás                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              Hivatkozás az Eszközök táblára.               |
|   ApplicationKey   | ? (ExchangeDeviceService\DeviceApplication helyről másolva). |
|  Alkalmazásnév   | ? (ExchangeDeviceService\DeviceApplication helyről másolva). |
| ApplicationVersion | ? (ExchangeDeviceService\DeviceApplication helyről másolva). |
|     BundleSize     | ? (ExchangeDeviceService\DeviceApplication helyről másolva). |

