---
title: IntuneManagementExtension entitás
titleSuffix: Microsoft Intune
description: Az Intune-adattárház API-ban található entitásgyűjtemények IntuneManagementExtension entitáskategóriájára vonatkozó referencia-témakör.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19b63172c8901059239c44aaf56fc49f0d7a01ad
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940398"
---
# <a name="reference-for-intune-management-extensions"></a>Az Intune felügyeleti bővítményeinek referenciája

A **intuneManagementExtensions** kategória a mobileszközök olyan entitásait tartalmazza, amelyek a következő információkat követik nyomon:

- Egy IntuneManagementExtension verziói
- Egy IntuneManagementExtension telepítési állapota

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

A **intuneManagementExtensionVersion** entitás felsorolja a intuneManagementExtensions által használt összes verziót.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| ExtensionVersionKey |A intuneManagementExtensions verziójának egyedi azonosítója. | 1 |
| ExtensionVersion |A négyjegyű verziószám. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

A **intuneManagementExtensionHealthState** felsorolja a intuneManagementExtensions összes lehetséges állapotát.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| ExtensionStateKey |Az állapot egyedi azonosítója. | 2 |
| ExtensionState |Az IntuneManagementExtension állapota. | Kifogástalan |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

A **intuneManagementExtension** naponta listázza a Windows 10 rendszerű eszközök IntuneManagementExtensions állapotát.
Az entitás az utolsó 60 nap adatait őrzi meg. 


|      Tulajdonság       |                         Leírás                         | Példa |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               A dátum egyedi azonosítója.                |   123   |
|      TenantKey      |              A bérlő egyedi azonosítója.               |   456   |
|      DeviceKey      |              Az eszköz egyedi azonosítója.               |   789   |
| ExtensionVersionKey | A intuneManagementExtension verziójának egyedi azonosítója. |    1    |
|  ExtensionStateKey  |             Az állapot egyedi azonosítója.              |    2    |

