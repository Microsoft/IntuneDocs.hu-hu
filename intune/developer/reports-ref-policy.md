---
title: Házirend entitások referenciája
titleSuffix: Microsoft Intune
description: Az Intune-adattárház API-ban található entitásgyűjtemények szabályzatkategóriájára vonatkozó referencia-témakör.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fe4fabc86e7be647fa161d68fe8a4fe35e9eb6b
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654124"
---
# <a name="reference-for-policy-entities"></a>Házirend entitások referenciája

A **szabályzatok** kategória a mobileszközök olyan entitásait tartalmazza, amelyek a következő információkat követik nyomon:

- Az eszköz- és alkalmazáskonfigurációs profilok, valamint a megfelelőségi szabályzatok készlete  
- A sikeres, függő, sikertelen vagy hibás állapotú eszközök száma naponta  
- A sikeres, függő, sikertelen vagy hibás állapotú felhasználók száma naponta  
- A sikeres, függő, sikertelen vagy hibás állapotú eszközök száma összesen  

## <a name="policies"></a>policies

A **házirend** entitás felsorolja az eszköz konfigurációs profiljait, az alkalmazás konfigurációs profiljait és a megfelelőségi szabályzatokat. A szabályzatokat a Mobileszköz-kezelési (MDM) megoldás segítségével rendelheti hozzá a vállalat valamely csoportjához.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| policyKey |A szabályzat adattárházban való jelölésére szolgáló egyedi kulcs. |123 |
| policyId |A szabályzat egyedi azonosítója az adattárházban. |b66bc706-ffff-7437-0340-032819502773 |
| policyName |A szabályzat neve. |„Windows 10 Baseline” |
| policyVersion |A szabályzat verziója. A szabályzat szerkesztésekor vagy módosításakor új verzió jön létre. |1, 2, 3 |
| isDeleted |Jelzi, hogy frissítve lett-e a szabályzatrekord.  <br>Igaz – a szabályzat új, frissített mezőkkel ellátott rekorddal rendelkezik. <br>Hamis – a szabályzat legújabb rekordja. |Igaz/hamis |
| startDateInclusiveUTC |A szabályzat adattárházban történt létrehozásának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |
| deletedDateUTC |Az IsDeleted paraméter True (Igaz) értékre módosulásának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |
| rowLastModifiedDateTimeUTC |A szabályzat adattárházban történt utolsó módosításának dátuma és időpontja (UTC). |2016.11.23 12:00:00 |

## <a name="policytypes"></a>policyTypes

Az **policyType** entitás az eszköz konfigurációs profiljainak típusát, az alkalmazás konfigurációs profiljait és a megfelelőségi szabályzatokat sorolja fel. A szabályzatokat a Mobileszköz-kezelési (MDM) megoldás segítségével rendelheti hozzá a vállalat valamely csoportjához.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| policyTypeId |A szabályzat egyedi azonosítója a forrásrendszerben. |123 |
| policyTypeKey |A szabályzat egyedi azonosítója az adattárházban. |1 |
| policyTypeName |A szabályzattípus neve. |A Windows 10-re vonatkozó megfelelőségi szabályzat. |

## <a name="device-configuration"></a>Eszközkonfiguráció

A **deviceConfigurationProfileDeviceActivity** entitás naponta listázza a sikeres, függő, sikertelen vagy hibás állapotú **eszközök** számát. A szám az entitáshoz rendelt eszközkonfigurációs profilokat jelöli. Ha például egy **eszköz** sikeres állapotban van az összes hozzárendelt házirend esetében, az adott napra a sikeres számlálót eggyel növeli. Ha az adott eszköz két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor az entitás növeli az értéket a sikeres állapotot jelző számlálón, és hibás állapotba helyezi az eszközt. Az entitás azt sorolja fel, hogy hány eszköz van az egyes állapotokban az elmúlt 30 napon belüli adott napon.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| dateKey |A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése. |20160703 |
| Függőben |A függő állapotú egyedi eszközök száma. |123 |
| Sikerült |A sikeres állapotú egyedi eszközök száma. |12 |
| Hiba |A hibás állapotú egyedi eszközök száma. |10 |
| sikertelen |A sikertelen állapotú egyedi eszközök száma. |2 |

A **deviceConfigurationProfileUserActivity** entitás naponta listázza a sikeres, függő, sikertelen vagy hibás állapotú **felhasználók** számát. A szám az entitáshoz rendelt eszközkonfigurációs profilokat jelöli. Ha például egy **felhasználó** az összes hozzárendelt szabályzat esetében sikeres állapotú, akkor az adott napra a sikeres számlálót eggyel feljebb helyezi. Ha az adott felhasználó két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor a felhasználót hibás állapotúnak számítjuk.  A **deviceConfigurationProfileUserActivity** entitás azt sorolja fel, hogy hány felhasználó van az adott napon az elmúlt 30 napban.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| dateKey |A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése. |20160703 |
| Függőben |A függő állapotú egyedi felhasználók száma. |123 |
| Sikerült |A sikeres állapotú egyedi felhasználók száma. |12 |
| Hiba |A hibás állapotú egyedi felhasználók száma. |10 |
| sikertelen |A sikertelen állapotú egyedi felhasználók száma. |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

A **policyTypeActivity** entitás a sikeres, függő, sikertelen vagy hibás állapotú eszközök összesített számát sorolja fel. Ezeket az állapotokat az adott eszköz-, illetve alkalmazáskonfigurációs profilra, valamint megfelelőségi szabályzatra vonatkozóan ismerteti.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| dateKey |dateKey, amikor az eszköz konfigurációs profiljának beadását rögzítették az adattárházban. |20160703 |
| policyKey |a policyKey a policyName lekéréséhez csatlakozhat a szabályzathoz. |Windows 10 baseline |
| policyTypeKey |Szabályzatkulcs típusa, amely összekapcsolható a szabályzattípussal a szabályzattípus nevének lekérése érdekében. |Windows 10-es megfelelőségi szabályzat |
| Függőben |A függő állapotú egyedi eszközök száma. |123 |
| Sikerült |A sikeres állapotú egyedi eszközök száma. |12 |
| Hiba |A hibás állapotú egyedi eszközök száma. |10 |
| sikertelen |A sikertelen állapotú egyedi eszközök száma. |2 |

## <a name="compliance-policy"></a>Megfelelőségi szabályzat

A Megfelelőségi szabályzat API-referencia olyan entitásokat tartalmaz, amelyek információval szolgálnak az eszközökhöz rendelt megfelelőségi szabályzatok állapotáról.

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

Az alábbi táblázatban foglaltuk össze az eszközökhöz rendelt megfelelőségi szabályzatok hozzárendelési állapotát. A lista felsorolja az egyes megfelelőségi állapotokban található eszközök számát is.


|Tulajdonság     |Description  |Példa  |
|---------|---------|---------|
|dateKey  |A megfelelőségi szabályzat összefoglalójának létrehozási dátumkulcsa.|20161204 |
|ismeretlen  |Azoknak az eszközöknek a száma, amelyek offline állapotban vannak, vagy valamilyen más okból nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel. |5|
|notApplicable      |Azoknak az eszközöknek a száma, amelyeknél a rendszergazda által meghatározott eszközmegfelelőségi szabályzatok nem alkalmazhatók.|201 |
|megfelelő      |Azoknak az eszközöknek a száma, amelyek megfelelnek a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak. |4083 |
|Türelmi időszakban      |Azoknak az eszközöknek a száma, amelyek nem megfelelőek, de a rendszergazda által meghatározott türelmi időszakban vannak. |57|
|Nem      |Azoknak az eszköznek a száma, amelyek nem felelnek meg a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak, vagy a felhasználó nem a rendszergazda által meghatározott szabályzatoknak megfelelően járt el.|43 |
|Hiba      |Azoknak az eszközöknek a száma, amelyeknek nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel, és hibaüzenetet küldtek. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

Az alábbi táblázatban foglaltuk össze az eszközökhöz rendelt megfelelőségi szabályzatok hozzárendelési állapotát szabályzatonként és szabályzattípusonként. A lista szabályzatonként felsorolja az egyes megfelelőségi állapotokban található eszközök számát.



|Tulajdonság  |Description  |Példa  |
|---------|---------|---------|
|dateKey  |A megfelelőségi szabályzat összefoglalójának létrehozási dátumkulcsa.|20161219|
|policyKey     |Annak a megfelelőségi szabályzatnak a kulcsa, amelyhez az összefoglalás készült. |10178 |
|policyPlatformKey      |Annak a megfelelőségi szabályzathoz tartozó platformnak a kulcsa, amelyhez az összefoglalás készült.|5|
|ismeretlen     |Azoknak az eszközöknek a száma, amelyek offline állapotban vannak, vagy valamilyen más okból nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel.|13|
|notApplicable     |Azoknak az eszközöknek a száma, amelyeknél a rendszergazda által meghatározott eszközmegfelelőségi szabályzatok nem alkalmazhatók.|3|
|megfelelő      |Azoknak az eszközöknek a száma, amelyek megfelelnek a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak. |45|
|Türelmi időszakban      |Azoknak az eszközöknek a száma, amelyek nem megfelelőek, de a rendszergazda által meghatározott türelmi időszakban vannak. |3|
|Nem      |Azoknak az eszköznek a száma, amelyek nem felelnek meg a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak, vagy a felhasználó nem a rendszergazda által meghatározott szabályzatoknak megfelelően járt el.|7|
|Hiba      |Azoknak az eszközöknek a száma, amelyeknek nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel, és hibaüzenetet küldtek. |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

Az alábbi táblázat felsorolja minden hozzárendelt szabályzat platformtípusát. A táblázat nem sorolja fel azokat a szabályzatplatform-típusokat, amelyeket még soha nem rendeltek hozzá eszközökhöz.


|Tulajdonság  |Description  |Példa  |
|---------|---------|---------|
|policyPlatformTypeKey      |A szabályzatplatform típusának egyedi kulcsa. |20170519 |
|policyPlatformTypeId      |A szabályzatplatform típusának egyedi azonosítója.|1|
|policyPlatformTypeName      |A szabályzatplatform típusának neve.|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

Az alábbi táblázat a sikeres, függő, sikertelen vagy hibás állapotú eszközök napi számát tartalmazza. A szám a szabályzattípus-profilok szerinti adatot jelöli. Ha például az adott eszköz valamennyi hozzárendelt szabályzata tekintetében sikeres állapotú, akkor az entitás azon a napon eggyel növeli az értéket a sikeres állapotot jelző számlálón. Ha az adott eszköz két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor az entitás növeli az értéket a sikeres állapotot jelző számlálón, és hibás állapotba helyezi az eszközt. A policyDeviceActivity entitás azt sorolja fel, hogy hány eszköz van az elmúlt 30 napban megadott napon belül.

|Tulajdonság  |Description  |Példa  |
|---------|---------|---------|
|dateKey|A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése.|20160703|
|Függőben|A függő állapotú egyedi eszközök száma.|123|
|Sikerült|A sikeres állapotú egyedi eszközök száma.|12|
|policyKey|a policyKey a policyName lekéréséhez csatlakozhat a szabályzathoz.|Windows 10 baseline|
|Hiba|A hibás állapotú egyedi eszközök száma.|10|
|sikertelen|A sikertelen állapotú egyedi eszközök száma.|2|

### <a name="policyuseractivities"></a>policyUserActivities

Az alábbi táblázat a sikeres, függő, sikertelen vagy hibás állapotú felhasználók napi számát tartalmazza. A szám a szabályzattípus-profilok szerinti adatot jelöli. Ha például az egyik felhasználó valamennyi hozzárendelt szabályzata tekintetében sikeres állapotú, akkor az entitás azon a napon eggyel növeli az értéket a sikeres állapotot jelző számlálón. Ha az adott felhasználó két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor a felhasználót hibás állapotúnak számítjuk. A PolicyUserActivity entitás azt sorolja fel, hogy hány felhasználó van az egyes állapotokban az elmúlt 30 napon belüli adott napon.


| Tulajdonság  |                                         Description                                         |       Példa       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése. |      20160703       |
|  Függőben  |                         A függő állapotú egyedi eszközök száma.                          |         123         |
| Sikerült |                         A sikeres állapotú egyedi eszközök száma.                          |         12          |
| policyKey |                 a policyKey a policyName lekéréséhez csatlakozhat a szabályzathoz.                 | Windows 10 baseline |
|   Hiba   |                          A hibás állapotú egyedi eszközök száma.                           |         10          |

