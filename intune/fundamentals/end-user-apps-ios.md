---
title: iOS-felhasználói alkalmazások letöltése
description: Módszerek az iOS-alkalmazások elérhetővé tételére végfelhasználók számára
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
ms.openlocfilehash: 06cc977ce8b0b892e1020436f89ada4a40bac3f2
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73413983"
---
# <a name="how-your-ios-users-get-their-apps"></a>iOS-felhasználói alkalmazások letöltése

Ez a témakör ismerteti, hogy végfelhasználói hol és hogyan juthatnak hozzá a Microsoft Intune-ban elérhetővé tett alkalmazásokhoz.

**Kötelező alkalmazások** – A rendszergazda által kötelezően előírt alkalmazások, amelyeknek a telepítéséhez az eszközön az adott platformtól függően minimális felhasználói beavatkozás szükséges.

**Elérhető alkalmazások** – A Vállalati portál alkalmazáslistájában szereplő azon alkalmazások, amelyeknek a telepítése nem kötelező.

**Felügyelt alkalmazások** –  Azok a szabályzatokkal felügyelhető alkalmazások, amelyeket az Intune „burkolt be”, vagy az Intune App szoftverfejlesztői készlettel (SDK) készültek. Ezek az alkalmazások az Intune-nal felügyelhetők, és azokra alkalmazásvédelmi szabályzatok alkalmazhatók.

Nem **felügyelt alkalmazások**– a felhasználók által az INTUNE app SDK-val nem integrált iOS App Store-ból letölthető alkalmazások. Az Intune nem szabályozza az alkalmazások terjesztését, felügyeletét vagy szelektív törlését.  

Az Apple korlátozásai tiltják az üzletági és a felügyelt App Store-alkalmazások listázását a Vállalati portál alkalmazásban. Ezt megkerülendő, az iOS-es Vállalati portál alkalmazás csempéi a felhasználókat valamennyi alkalmazásuk eléréséhez egyetlen hely (a Vállalati portál webhely) különböző nézeteihez irányítják.

A regisztrált felhasználók úgy jutnak hozzá az alkalmazásokhoz, hogy a következő csempékre kattintanak a Munkahelyi portál alkalmazás Alkalmazások képernyőjén:

- A **Minden alkalmazás** csempe a [Munkahelyi portál webhely](https://portal.manage.microsoft.com) ÖSSZES lapjára mutat.

- A **Kiemelt alkalmazások** csempe a Munkahelyi portál webhely KIEMELT lapjára vezet.

- A **Kategóriák** csempe a Munkahelyi portál webhely KATEGÓRIÁK lapjára vezet.

![iOS rendszerű Munkahelyi portál alkalmazás](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

Az alkalmazások hozzáadásáról az [Alkalmazás hozzáadása a Microsoft Intune-hoz](../apps/apps-add.md) című témakörben találhat további információt.

## <a name="see-also"></a>További információ

[Android-felhasználói alkalmazások letöltése](end-user-apps-android.md)

[Windows-felhasználói alkalmazások letöltése](end-user-apps-windows.md)
