---
title: Az Outlook beállításai iOS és Android rendszerű eszközökhöz a Microsoft Intune-ban
description: Létrehozhat egy konfigurációs szabályzatot az iOS- és Android-eszközökön futó Microsoft Outlook beállításainak megadásához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: smithre4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43e411b5619c2a2232231ef113b550fc2f20a2a0
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199151"
---
# <a name="microsoft-outlook-configuration-settings"></a>A Microsoft Outlook konfigurációs beállításai 

Az iOS- és Android-eszközökön futó Microsoft Outlook beállításainak elvégzéséhez konfigurációs szabályzatot is használhat. 

For enrolled devices:
- Alkalmazáskonfigurációs szabályzat felügyelt iOS-eszközökhöz történő létrehozásával kapcsolatban lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt iOS-eszközökhöz](app-configuration-policies-use-ios.md). 
- Alkalmazáskonfigurációs szabályzat felügyelt androidos eszközökhöz történő létrehozásával kapcsolatban lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt Android-eszközökhöz](app-configuration-policies-use-android.md). 

For unenrolled devices, see [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md) to create an app configuration policy for Outlook for iOS and Android.

## <a name="configuration-settings"></a>Konfigurációs beállítások

When adding a configuration policy in Intune, you can specify settings to configure Microsoft Outlook for iOS and Android. In the Configuration settings pane, you can specify the email account configuration and configure app-specific settings.

For specific procedural steps and detailed documentation on the app configuration settings Outlook for iOS and Android supports, see [Deploying Outlook for iOS and Android app configuration settings](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="next-steps"></a>További lépések

- For more information, see [App configuration policies for Microsoft Intune](app-configuration-policies-overview.md)
