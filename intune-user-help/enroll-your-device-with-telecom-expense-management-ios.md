---
title: iOS-eszköz regisztrálása a távközlésiköltség-kezelőben az Intune-nal
description: Ez a cikk azt ismerteti, hogyan regisztrálhat iOS-es eszközt a távközlésiköltség-kezelőben.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 84098d4d2152d62eda888cdcde1cf88e5081a470
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506173"
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>iOS-eszköz regisztrálása a távközlésiköltség-kezelőben

Elképzelhető, hogy az Ön szervezeténél használnak távközlésiköltség-kezelő szoftvert, hogy biztosítani tudják a hang- és adatcsomagok elfogadható keretek közötti használatát. Az eszköz regisztrálása után felkéri a rendszer, hogy válassza ki az eszköznek leginkább megfelelő kategóriát.

  ![Képernyőkép az eszköznek leginkább megfelelő kategória kiválasztásáról iOS-eszköz esetén. A választható lehetőségek a céges és a személyes regisztrálási mód.](./media/ios-enroll-10-tem-select-best-category.png)

Válassza ki a megfelelő lehetőséget. Ezt követően értesítést kap arról, hogy telepítse a [__Datalert__](https://itunes.apple.com/app/datalert/id771029268?mt=8) alkalmazást az App Store-ból. A Datalert alkalmazás fogja lehetővé tenni, hogy a szervezet mérni tudja az adathasználatot. Ha munkahelyén konfigurálva van a munkahelyi vagy iskolai Microsoft-fiókkal történő regisztráció, akkor a munkahelyi vagy iskolai fiókjával kell bejelentkeznie. Ellenkező esetben személyes információ, például telefonszám alapján, egy kód segítségével kell visszaigazolnia eszközét, hogy az alkalmazásból regisztrálni tudjon a Datalert szolgáltatásba.

  ![A Datalert alkalmazás nyitó képernyőjének képe, amely röviden leírja, hogyan segíti a Datalert az adatcsomag optimális használatát, és hivatkozást tartalmaz a következő képernyőre lépéshez.](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Datalert-regisztráció munkahelyi vagy iskolai Microsoft-fiókkal

> [!NOTE]
> Ehhez a regisztrációs módszerhez telepíteni kell a telefonra a [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) alkalmazást.

1. Válassza az __Enroll with Microsoft account__ (Bejelentkezés Microsoft-fiókkal) gombot.

   ![A Datalert alkalmazás Settings (Beállítások) képernyője, fent az eszközregisztrációhoz szükséges telefonszám megadására szolgáló mezővel, alul pedig az „Enroll with Microsoft account” gombbal – ehhez Microsoft Office 365-fiók és Intune-előfizetés szükséges.](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. Ekkor megjelenik a __"Datalert" wants to open "Authenticator"__ (A Datalert meg szeretné nyitni az Authenticatort) üzenet. Válassza az __Open__ (Megnyitás) lehetőséget.

   ![A felhasználót a Datalert nevében az Authenticator alkalmazás elindítására kérő üzenet.](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. Jelentkezzen be a __Microsoft school or work account__ (Munkahelyi vagy iskolai Microsoft-fiók) lehetőséget választva. A Datalert telepítője néhány másodperc alatt elkészül. Ezután koppintson a __Finish__ (Befejezés) gombra.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Datalert-regisztráció telefonszámmal

1. Adja meg az eszköz telefonszámát.

   ![Képernyőkép arról, hogy a Datalert alkalmazás a telefonszámot kéri megadni.](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. Ezt követően SMS-ben kap egy ellenőrző kódot. Írja be a kódot, és koppintson az __OK__ lehetőségre.

   ![Képernyőkép: a Datalert alkalmazás kéri az SMS-ben elküldött ellenőrző kódot.](./media/ios-enroll-13-tem-datalert-sms.png)

3. Az ellenőrző kód beírása után a Datalert telepítése befejeződött. Koppintson a __Finish__ (Befejezés) elemre. Ezzel készen áll arra, hogy az adathasználatot a Datalert alkalmazással figyelje.

   ![Képernyőkép: a Datalert alkalmazás a mai adatforgalmat jeleníti meg.](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

A regisztrálás után az adathasználati adatok megjelennek a Datalert alkalmazásban.

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
