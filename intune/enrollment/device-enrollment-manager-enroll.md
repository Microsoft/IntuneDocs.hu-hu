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
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30191aea892e8409bb6165034256a99f6f32a502
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955405"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>Eszközök regisztrálása az Intune-ban egy eszköz beléptetési kezelői fiók használatával

Készülékregisztráció-kezelői (DEM) fiók használatával akár 1000 mobileszközt is regisztrálhat egyetlen Azure Active Directory-fiókkal. A DEM egy Intune-engedély, amelyet AAD felhasználói fiókokra lehet alkalmazni, és lehetővé teszi, hogy a felhasználó akár 1000 eszközt is regisztráljon. A DEM-fiók olyan forgatókönyvek esetén hasznos, ahol az eszközöket regisztrálják és előkészítik, mielőtt kiadnák azokat a felhasználóknak. A tervezés szerint a Microsoft Intuneban legfeljebb 150 Device beléptetési kezelő (DEM) fiók található.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>A DEM-fiókkal regisztrált eszközökre vonatkozó korlátozások

A DEM-fiókokra és a DEM-fiókokkal regisztrált eszközökre a következő korlátozások vonatkoznak:

- A DEM-fiókhoz tartozó felhasználónak Intune-licenccel kell rendelkeznie.
- Nem végezhető el az összes adat törlése a Céges portálról. A DEM felhasználói fiókkal regisztrált eszközök összes adatának törlése a Azure Portalon az Intune-ból végezhető el.
- A Vállalati portál alkalmazásban vagy a webhelyén csak a helyi eszköz jelenik meg.
- A DEM felhasználói fiókjai nem használhatják az Apple VPP felhasználói licenccel rendelkező Apple Volume Purchase Program (VPP) alkalmazásokat az alkalmazások felügyeletére vonatkozó felhasználónkénti Apple ID-követelmények miatt.
- A DEM-fiókok nem használhatók az Apple Készülékregisztrációs programon (DEP) keresztüli eszközök regisztrálásakor.
- Az eszközök akkor telepíthetnek VPP-alkalmazásokat, ha rendelkeznek Apple VPP-eszközlicenccel.
- Az eszközök feltételes hozzáféréssel való letiltása a Windows 10 1803 + kivételével
- A DEM-fiókkal regisztrált összes eszköznek megfelelő licenccel kell rendelkeznie ahhoz, hogy az Intune kezelje őket. A licenc lehet Intune-beli felhasználói licenc vagy Intune-eszköz licence.
- Ha egy DEM-fiók használatával [regisztrálja az androidos vállalati munkahelyi profilokat](android-work-profile-enroll.md) , akkor a fiókhoz legfeljebb 10 eszköz regisztrálható.


## <a name="add-a-device-enrollment-manager"></a>Eszközregisztráció-kezelő hozzáadása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **eszközök regisztrálása** > **eszköz beléptetési kezelők**lehetőséget.

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

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **eszközök regisztrálása** > **eszköz beléptetési kezelők**lehetőséget.
2. A **Készülékregisztráció-kezelő** panelen válassza ki a készülékregisztráció-kezelő felhasználót, majd válassza az **Eltávolítás** lehetőséget.

