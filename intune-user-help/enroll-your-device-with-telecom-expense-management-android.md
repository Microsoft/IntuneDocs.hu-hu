---
title: Android-eszköz regisztrálása a távközlésiköltség-kezelőben az Intune-nal
description: Ez a cikk azt ismerteti, hogyan regisztrálhat androidos eszközt a távközlésiköltség-kezelőben.
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
ms.assetid: 26aa3698-7e4d-453a-8852-ab75e72b6485
searchScope:
- User help
ROBOTS: ''
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1a6e2a001e8c323ba73dd7e9ad4dd82df968e6d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506201"
---
# <a name="enroll-your-android-device-in-telecom-expense-management"></a>Android-eszköz regisztrálása a távközlésiköltség-kezelőben

Elképzelhető, hogy az Ön szervezeténél használnak távközlésiköltség-kezelő szoftvert, hogy biztosítani tudják a hang- és adatcsomagok elfogadható keretek közötti használatát. Az eszköz regisztrálása után felkéri a rendszer, hogy válassza a ki az eszköznek leginkább megfelelő kategóriát.

![Képernyőkép az eszköznek leginkább megfelelő kategória kiválasztásáról iOS-eszköz esetén. A választható lehetőségek a céges és a személyes regisztrálási mód.](./media/and-enroll-11-tem-select-best-category.png)

Válassza ki a megfelelő lehetőséget. Ezt követően értesítést kap arról, hogy telepítse a [__Datalert__](https://play.google.com/store/apps/details?id=fr.memobox.databox) alkalmazást a Google Play Áruházból. A Datalert alkalmazás fogja lehetővé tenni, hogy a szervezet mérni tudja az adathasználatot. Ha munkahelyén konfigurálva van a munkahelyi vagy iskolai fiókkal történő regisztráció, akkor a munkahelyi vagy iskolai fiókjával kell bejelentkeznie. Ellenkező esetben személyes információ, például telefonszám alapján, egy kód segítségével kell visszaigazolnia eszközét, hogy az alkalmazásból regisztrálni tudjon a Datalert szolgáltatásba.

A továbblépéshez koppintson a képernyő jobb felső sarkában található __következő__ nyílra. A cég informatikai támogató szolgálata nyújthat segítséget abban a kérdésben, hogy __munkahelyi vagy iskolai Microsoft-fiókjával__, illetve __telefonszámával__ tud-e regisztrálni.

  ![A Datalert alkalmazás nyitó képernyőjének képe, amely röviden leírja, hogyan segíti a Datalert az adatcsomag optimális használatát, és hivatkozást tartalmaz a következő képernyőre lépéshez.](./media/and-enroll-12-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Datalert-regisztráció munkahelyi vagy iskolai Microsoft-fiókkal

1. Válassza az __Enroll with Microsoft account__ (Bejelentkezés Microsoft-fiókkal) gombot.

   ![A Datalert alkalmazás Settings (Beállítások) képernyője, fent az eszközregisztrációhoz szükséges telefonszám megadására szolgáló mezővel, alul pedig az „Enroll with Microsoft account” gombbal – ehhez Microsoft Office 365-fiók és Intune-előfizetés szükséges.](./media/and-enroll-12a-tem-datalert-enroll-msft-account.png)

2. A rendelkezésre álló fiókok közül válassza ki munkahelyi vagy iskolai fiókját. Ha a fiók nem látható, az **Add account** (Fiók hozzáadása) gombbal tud bejelentkezni.

   ![A Pick account (Fiókválasztás) képernyő egy példafiókkal és az Add account gombbal.](./media/and-enroll-12b-tem-datalert-enroll-select-msft-account.png)

3. A Datalert telepítője néhány másodperc alatt elkészül. Ezután koppintson a __Finish__ (Befejezés) gombra.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Datalert-regisztráció telefonszámmal

1. Adja meg az eszköz telefonszámát.

   ![Képernyőkép arról, hogy a Datalert alkalmazás a telefonszámot kéri megadni.](./media/and-enroll-13-tem-datalert-phone-number.png)

2. Ezt követően SMS-ben kap egy ellenőrző kódot. Írja be a kódot, és koppintson az __OK__ lehetőségre.

   ![Képernyőkép: a Datalert alkalmazás kéri az SMS-ben elküldött ellenőrző kódot.](./media/and-enroll-14-tem-datalert-sms.png)

3. Az ellenőrző kód beírása után a Datalert telepítése befejeződött. Koppintson a __Finish__ (Befejezés) elemre. Ezzel készen áll arra, hogy az adathasználatot a Datalert alkalmazással figyelje.

   ![Képernyőkép: a Datalert alkalmazás a mai adatforgalmat jeleníti meg.](./media/and-enroll-15-tem-datalert-monitoring-active.png)

A regisztrálás után az adathasználati adatok megjelennek a Datalert alkalmazásban.

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
