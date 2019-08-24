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
ms.openlocfilehash: 4593fd5e76bf51b11ef9796bacc8c562241eaca2
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001742"
---
# <a name="reference-for-user-device-association-entity"></a>Segédlet a Felhasználók és eszközök társítása entitáshoz

A **userDeviceAssociation** entitás felhasználói eszközök társításait tartalmazza a szervezetben.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Name (Név)        |                                           Leírás                                            |        Példa         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              A felhasználó egyedi azonosítója az adattárházban. (Helyettes kulcs).               |          123           |
|     deviceKey      |                      Az eszköz egyedi azonosítója az adattárházban.                      |          123           |
| createdDateTimeUTC |           A felhasználói eszköztársítás létrehozásának dátuma és időpontja. UTC formátumban.           | 2016.11.23. 12:00:00 |
|     IsDeleted      | Azt jelzi, hogy a felhasználó megszüntette az eszköz regisztrációját, és a társítás már nem aktuális. |       Igaz/hamis       |
|  endedDateTimeUTC  |              Az IsDeleted paraméter <strong>True</strong> (Igaz) értékre módosulásának dátuma és időpontja (UTC).               | 2017.06.23. 12:00:00 |

## <a name="next-steps"></a>További lépések

- További információ az [Intune](reports-nav-create-intune-reports.md)-adattárházról.
