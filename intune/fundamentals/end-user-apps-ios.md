---
title: IOS-/iPadOS-felhasználói alkalmazások letöltése
description: Az iOS/iPadOS alkalmazások elérhetővé tételének módszerei a végfelhasználók számára
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344c2e3f3ed53852aa6b749c9ebf6d451dd313ff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514387"
---
# <a name="how-your-iosipados-users-get-their-apps"></a>IOS-/iPadOS-felhasználói alkalmazások letöltése

Ez a témakör ismerteti, hogy végfelhasználói hol és hogyan juthatnak hozzá a Microsoft Intune-ban elérhetővé tett alkalmazásokhoz.

**Kötelező alkalmazások** – A rendszergazda által kötelezően előírt alkalmazások, amelyeknek a telepítéséhez az eszközön az adott platformtól függően minimális felhasználói beavatkozás szükséges.

**Elérhető alkalmazások** – A Vállalati portál alkalmazáslistájában szereplő azon alkalmazások, amelyeknek a telepítése nem kötelező.

**Felügyelt alkalmazások** –  Azok a szabályzatokkal felügyelhető alkalmazások, amelyeket az Intune „burkolt be”, vagy az Intune App szoftverfejlesztői készlettel (SDK) készültek. Ezek az alkalmazások az Intune-nal kezelhetők, és alkalmazásvédelmi szabályzatokkal felügyelhetők.

Nem **felügyelt alkalmazások**– a felhasználók által az INTUNE app SDK-val nem integrált iOS/IPadOS App Store-ból letölthető alkalmazások. Az Intune nem szabályozza az alkalmazások terjesztését, felügyeletét vagy szelektív törlését.  

Az Apple korlátozásai tiltják az üzletági és a felügyelt App Store-alkalmazások listázását a Vállalati portál alkalmazásban. A probléma megkerüléséhez az iOS/iPadOS ponthoz tartozó Céges portál alkalmazás csempéi az összes alkalmazásához egy helyen (a Céges portál webhelyen) különböző nézeteket.

A regisztrált felhasználók úgy jutnak hozzá az alkalmazásokhoz, hogy a következő csempékre kattintanak a Munkahelyi portál alkalmazás Alkalmazások képernyőjén:

- A **Minden alkalmazás** csempe a [Munkahelyi portál webhely](https://portal.manage.microsoft.com) ÖSSZES lapjára mutat.

- A **Kiemelt alkalmazások** csempe a Munkahelyi portál webhely KIEMELT lapjára vezet.

- A **Kategóriák** csempe a Munkahelyi portál webhely KATEGÓRIÁK lapjára vezet.

![iOS rendszerű Munkahelyi portál alkalmazás](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

Az alkalmazások hozzáadásáról az [Alkalmazás hozzáadása a Microsoft Intune-hoz](../apps/apps-add.md) című témakörben találhat további információt.

## <a name="see-also"></a>További információ

[Android-felhasználói alkalmazások letöltése](end-user-apps-android.md)

[Windows-felhasználói alkalmazások letöltése](end-user-apps-windows.md)
