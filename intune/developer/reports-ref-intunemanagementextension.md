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
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae99e747f9c0540418c15f24fbe0c27c585f869c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490300"
---
# <a name="reference-for-intune-management-extensions"></a>Az Intune felügyeleti bővítményeinek referenciája

A **intuneManagementExtensions** kategória a mobileszközök olyan entitásait tartalmazza, amelyek a következő információkat követik nyomon:

- Egy IntuneManagementExtension verziói
- Egy IntuneManagementExtension telepítési állapota

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

A **intuneManagementExtensionVersion** entitás felsorolja a intuneManagementExtensions által használt összes verziót.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| extensionVersionKey |A intuneManagementExtensions verziójának egyedi azonosítója. | 1 |
| extensionVersion |A négyjegyű verziószám. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

A **intuneManagementExtensionHealthState** felsorolja a intuneManagementExtensions összes lehetséges állapotát.

| Tulajdonság  | Description | Példa |
|---------|------------|--------|
| extensionStateKey |Az állapot egyedi azonosítója. | 2 |
| extensionState |Az IntuneManagementExtension állapota. | Kifogástalan |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

A **intuneManagementExtension** naponta listázza a Windows 10 rendszerű eszközök IntuneManagementExtensions állapotát.
Az entitás az utolsó 60 nap adatait őrzi meg. 


|      Tulajdonság       |                         Description                         | Példa |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               A dátum egyedi azonosítója.                |   123   |
|      tenantKey      |              A bérlő egyedi azonosítója.               |   456   |
|      deviceKey      |              Az eszköz egyedi azonosítója.               |   789   |
| extensionVersionKey | A intuneManagementExtension verziójának egyedi azonosítója. |    1    |
|  extensionStateKey  |             Az állapot egyedi azonosítója.              |    2    |

