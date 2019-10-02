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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd36b0827a2981f404772ee75441573264debfb3
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732015"
---
# <a name="how-your-ios-users-get-their-apps"></a>iOS-felhasználói alkalmazások letöltése

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

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

## <a name="see-also"></a>Lásd még:
[Android-felhasználói alkalmazások letöltése](end-user-apps-android.md)

[Windows-felhasználói alkalmazások letöltése](end-user-apps-windows.md)
