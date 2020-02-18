---
title: A Microsoft Intune által kezelt eszközök regisztrációs beállításai
titleSuffix: ''
description: A Microsoft Intune által kezelt eszközökön a rendszergazdák által megadható regisztrációs beállítások.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7c1ff18a7923d7502e12a9bdb33931089fada6e3
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414242"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Az Intune által kezelt eszközök regisztrációs beállításai

Intune-rendszergazdaként konfigurálhatja az eszközregisztrációt, hogy segítségére legyen a felhasználóknak, és kihasználja az Intune képességeit.  Az Intune a következő regisztrálási lehetőségeket tartalmazza:

## <a name="terms-and-conditions"></a>használati feltételei

Ön döntheti el, hogy megköveteli-e a felhasználóktól a cég használati feltételeinek elfogadását, mielőtt a Céges portált használnák saját eszközeik beléptetéséhez, valamint az erőforrások (például céges alkalmazások és e-mailek) eléréséhez. A használati feltételek konfigurálása nem kötelező. További információ [a feltételekről és kikötésekről](terms-and-conditions-create.md).

## <a name="enrollment-restrictions"></a>Regisztrációs korlátozások

Az eszközregisztrációt az alábbiak szerint korlátozhatja:
- Eszközplatform
- Eszközök száma felhasználónként
- Személyes eszközök letiltása

További információ [a regisztrációs korlátozásokról](enrollment-restrictions-set.md).

## <a name="enable-apple-device-enrollment"></a>Az Apple-készülékregisztráció engedélyezése

Az iOS/iPadOS és a macOS rendszerű eszközök regisztrálásához egy MDM push-tanúsítványra van szükség. További információ [az MDM Push-tanúsítványokról](apple-mdm-push-certificate-get.md).

## <a name="corporate-identifiers"></a>Vállalati azonosítók

Nemzetközi mobilkészülék-azonosító (IMEI) számok és sorozatszámok megadásával azonosíthatja a vállalat által birtokolt eszközök listáját. További információ a [vállalati azonosítókról](corporate-identifiers-add.md).
## <a name="multi-factor-authentication"></a>Többtényezős hitelesítés

Megkövetelheti a felhasználóktól további hitelesítési módszer, például telefon, PIN-kód vagy biometrika használatát, amikor regisztrálják eszközüket. További tudnivalók [a többtényezős hitelesítésről](multi-factor-authentication.md).

## <a name="device-enrollment-manager"></a>Készülékregisztráció-kezelő
Felhasználókat tehet meg eszközregisztráció-kezelőnek.  A DEM-felhasználók az Intune használatával nagyszámú mobileszközt regisztrálhatnak egyetlen felhasználói fiókkal. Az eszközregisztráció-kezelői (DEM-) fiók akár ezer eszköz regisztrálására képes. További tudnivalók [az eszközregisztráció-kezelőkről](device-enrollment-manager-enroll.md).

## <a name="device-categories"></a>Eszközkategóriák

Az eszközkategóriák segítségével automatikusan csoportokba veheti fel az eszközöket az Ön által meghatározott kategóriák alapján. Az eszközök csoportokba való rendszerezése megkönnyíti az eszközök kezelését. További tudnivalók az [eszközkategóriákról](device-group-mapping.md).
