---
title: Eszközök regisztrálása készülékregisztráció-kezelői fiók használatával
titleSuffix: Microsoft Intune
description: Az eszközök Intune-ban való regisztrálásához használja a készülékregisztráció-kezelői fiókot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd870a788ff5cac7e0aff47c5b8175c0bdfacff2
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427299"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>Eszközök regisztrálása az Intune-ban egy eszközregisztráció-kezelői fiók használatával

Készülékregisztráció-kezelői (DEM) fiók használatával akár 1000 mobileszközt is regisztrálhat egyetlen Azure Active Directory-fiókkal. A DEM egy Intune-engedély, amelyet AAD felhasználói fiókokra lehet alkalmazni, és lehetővé teszi, hogy a felhasználó akár 1000 eszközt is regisztráljon. A DEM-fiók olyan forgatókönyvek esetén hasznos, ahol az eszközöket regisztrálják és előkészítik, mielőtt kiadnák azokat a felhasználóknak. A tervezés szerint a Microsoft Intune 25 eszköz beléptetési kezelőjéhez (DEM) tartozó fiókok száma.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>A DEM-fiókkal regisztrált eszközökre vonatkozó korlátozások

A DEM-fiókokra és a DEM-fiókokkal regisztrált eszközökre a következő korlátozások vonatkoznak:

- A DEM-fiókhoz tartozó felhasználónak Intune-licenccel kell rendelkeznie.
- Nem végezhető el az összes adat törlése a Céges portálról. A DEM felhasználói fiókkal regisztrált eszközök összes adatának törlése a Azure Portalon az Intune-ból végezhető el.
- A Vállalati portál alkalmazásban vagy a webhelyén csak a helyi eszköz jelenik meg.
- A DEM felhasználói fiókok nem használhatnak az Apple Volume Purchase Program (VPP) keretében vásárolt alkalmazásokat az Apple VPP felhasználói licencekkel, mivel az alkalmazások kezeléséhez felhasználói Apple ID azonosítóra van szükség.
- Az eszközök akkor telepíthetnek VPP-alkalmazásokat, ha rendelkeznek Apple VPP-eszközlicenccel.
- Eszközei le lettek tiltva a feltételes hozzáférés Windows 10 1803 + kivételével
- A DEM-fiókkal regisztrált összes eszköznek megfelelő licenccel kell rendelkeznie ahhoz, hogy az Intune kezelje őket. A licenc lehet Intune-beli felhasználói licenc vagy Intune-eszköz licence.



## <a name="add-a-device-enrollment-manager"></a>Eszközregisztráció-kezelő hozzáadása

1. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Eszközregisztráció-kezelők** elemet.

2. Válassza a **Hozzáadás** elemet.

3. Adja meg a készülékregisztráció-kezelő felhasználó egyszerű felhasználónevét a **Felhasználó hozzáadása** panelen, majd válassza a **Hozzáadás** elemet. A készülékregisztráció-kezelő felhasználó bekerül a készülékregisztráció-kezelő felhasználók listájába.

## <a name="permissions-for-dem"></a>DEM-engedélyek

Globális vagy Intune-szolgáltatási rendszergazdai Azure AD-szerepkörök szükségesek az alábbiakhoz:
- DEM-engedély hozzárendelése Azure AD felhasználói fiókhoz,
- az összes DEM-felhasználó megtekintéséhez.

Ha egy felhasználó nem rendelkezik hozzárendelt globális rendszergazdai vagy Intune-szolgáltatásrendszergazdai szerepkörrel, de van olvasási jogosultsága a hozzá rendelt készülékregisztráció-kezelői szerepkörhöz, akkor csak az általa létrehozott DEM-felhasználókat láthatja.


## <a name="remove-device-enrollment-manager-permissions"></a>Készülékregisztráció-kezelői engedélyek eltávolítása

A készülékregisztráció-kezelő eltávolítása nincs hatással a regisztrált eszközökre.

**Készülékregisztráció-kezelő eltávolítása**

1. Az [Azure Portalbeli Intune-on](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása**, majd a **Készülékregisztráció-kezelők** lehetőséget.
2. A **Készülékregisztráció-kezelő** panelen válassza ki a készülékregisztráció-kezelő felhasználót, majd válassza az **Eltávolítás** lehetőséget.

