---
title: Felhasználók és eszközök társítása – Intune-adattárház
titleSuffix: Microsoft Intune
description: A UserDeviceAssociation entitás felhasználói eszközök társításait tartalmazza a szervezetben.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 780422c176b7ab27baf3b6025a42179508e117ff
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730131"
---
# <a name="reference-for-user-device-association-entity"></a>Segédlet a Felhasználók és eszközök társítása entitáshoz

A **userDeviceAssociation** entitás felhasználói eszközök társításait tartalmazza a szervezetben.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Name (Név)        |                                           Leírás                                            |        Példa         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              A felhasználó egyedi azonosítója az adattárházban. (Helyettes kulcs).               |          123           |
|     DeviceKey      |                      Az eszköz egyedi azonosítója az adattárházban.                      |          123           |
| createdDateTimeUTC |           A felhasználói eszköztársítás létrehozásának dátuma és időpontja. UTC formátumban.           | 2016.11.23. 12:00:00 |
|     IsDeleted      | Azt jelzi, hogy a felhasználó megszüntette az eszköz regisztrációját, és a társítás már nem aktuális. |       Igaz/hamis       |
|  endedDateTimeUTC  |              Az IsDeleted paraméter <strong>True</strong> (Igaz) értékre módosulásának dátuma és időpontja (UTC).               | 2017.06.23. 12:00:00 |

## <a name="next-steps"></a>További lépések

- További információ az [Intune](../reports-nav-create-intune-reports.md)-adattárházról.
