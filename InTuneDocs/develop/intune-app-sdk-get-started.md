---
title: "Bevezetés a Microsoft Intune App SDK használatába | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: a042f0c6206e9aaf4ec0eb012a70930aa95ecc47


---

# Bevezetés a Microsoft Intune App SDK használatába

Ez az első lépéseket bemutató útmutató segítséget nyújt a mobilalkalmazás gyors engedélyezéséhez a Microsoft Intune-beli mobilalkalmazás-felügyelet használatával. Javasoljuk, hogy először tájékozódjon az Intune App SDK előnyeiről, amelyekről [Az Intune App SDK áttekintése](intune-app-sdk.md) című témakörben olvashat bővebben.

Ez az útmutató végigvezeti azokon a fő lépéseken, amelyekkel engedélyezheti az alkalmazás Microsoft Intune mobilalkalmazás-felügyeleten keresztüli felügyeletét. Az Intune App SDK a különböző platformokon hasonló lehetőségeket támogat, és célja, hogy egységes, platformfüggetlen felhasználói élményt teremtsen a rendszergazdáknak. A platformok korlátozásai miatt azonban bizonyos funkciók támogatásában kisebb különbségek vannak.

# Első lépések

## Microsoft Connect-regisztráció

Az Intune App SDK jelenleg a Microsoft Connecten keresztül érhető el, és használata regisztrációt igényel. Ehhez a vállalati e-mail címével regisztráljon egy [Microsoft-fiókot](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X).

A regisztráció mindaddig függő állapotban marad, amíg az Intune csapata nem ellenőrzi kérelmét. A szokásos válaszidő legfeljebb 2-3 munkanap. Amennyiben jóváhagyták a regisztrációt, kapni fog egy értesítő e-mailt a megfelelő platform(ok)hoz készült Intune App SDK és az összes kapcsolódó útmutató letöltéséhez szükséges hivatkozásokkal. Ezek az útmutatók az MSDN webhelyén is elérhetők.

## Áruházbeli alkalmazás regisztrálása a Microsoft Intune-nal

**Ha az engedélyezett alkalmazás a vállalat belső használatára készült, és nem lesz elérhető az Apple vagy a Google áruházából**: nem kell regisztrálnia az alkalmazást. Az ilyen belső alkalmazásokat a rendszergazda közvetlenül a Microsoft Intune konzolján betöltve helyezheti üzembe; az Intune észleli, hogy az alkalmazás az SDK-val készült, és a rendszergazdának felkínálja a MAM-házirend alkalmazását. Ez esetben lépjen az [iOS vagy Android rendszerhez készült mobilalkalmazás engedélyezése a MAM-hoz az SDK használatával](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk) című részre.

**Az Apple vagy a Google áruházán keresztül elérhető alkalmazást fejlesztő független szoftverszállítóknak**: először regisztrálja az alkalmazást a Microsoft Intune-ban, és fogadja el a regisztrációs szerződést. Ekkor megadhatja az alkalmazás mélyhivatkozását. A rendszergazda ezt követően alkalmazhatja az Intune MAM-szabályzatot az alkalmazásra. A felügyeleti konzol nem ad lehetőséget az alkalmazás mélyhivatkozásának a MAM-szabályzat alkalmazására, amíg el nem végezte a regisztrációt, és a Microsoft Intune-csapat meg nem erősítette azt. A Microsoft a Microsoft Intune-partnerek webhelyet is fenntartja, ahol az alkalmazás regisztrálva lesz, így az ügyfelek tudni fogják, hogy az támogatja-e a Microsoft Intune MAM-szabályzatot.

A regisztráció megkezdéséhez **tekintse át és írja alá** a [Microsoft Intune-partnerszerződést](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806). Ez a szerződés tartalmazza azokat a feltételeket, amelyeket vállalatának el kell fogadnia ahhoz, hogy Microsoft Intune-alkalmazáspartner lehessen. A dokumentum megtekintéséhez előbb be kell jelentkeznie. A szerződést az Intune App SDK Microsoft Connect-webhely Surveys (Felmérések) lapján, vagy itt találja. Arra is megkérjük, hogy adja meg az alkalmazás nevét, a cégnevét, valamint alkalmazása Google- vagy iTunes-áruházbeli mélyhivatkozását.

![Microsoft Connect](../media/microsoft-connect.png)

A regisztrációs e-mail címet használjuk a regisztrációs folyamat megerősítéséhez és fogadásának befejezéséhez. Emellett regisztrációs e-mail címén vesszük fel a kapcsolatot Önnel, ha bármilyen kétségeink lennének.

**Mire számítson a regisztrációs folyamat során**: Miután elküldte az űrlapot, a Microsoft regisztrációs e-mail címén keresztül felveszi Önnel a kapcsolatot, hogy megerősítse a sikeres fogadást, vagy további információt kérjen a regisztráció befejezéséhez. Akkor is kapcsolatba lépünk Önnel, ha az alkalmazás sikeresen regisztrálva lett a Microsoft Intune rendszerében, illetve ha az megjelent a Microsoft Intune-partnerek webhelyén. Az adatok megerősítését követően alkalmazása mélyhivatkozása szerepelni fog az Intune szolgáltatás következő havi frissítésében. Ha például a regisztrációs adatokat júliusban töltötte ki, az alkalmazás mélyhivatkozása augusztus közepétől támogatott. Ha a jövőben változik az áruházbeli alkalmazás mélyhivatkozása, újra kell regisztrálnia az alkalmazást. Akkor is értesítsen minket, ha az alkalmazást az Intune App SDK új verziójával frissíti.

**Megjegyzés**: A fenti űrlapról és az Intune csapatával váltott e-mailekből gyűjtött összes adat esetében figyelembe vesszük a [Microsoft adatvédelmi nyilatkozatát](https://www.microsoft.com/en-us/privacystatement/default.aspx).

## iOS vagy Android rendszerhez készült mobilalkalmazás engedélyezése a MAM-hoz az SDK használatával

iOS-mobilalkalmazás engedélyezéséhez a következőkre lesz szüksége:

1. **[iOS-hez készült Microsoft Intune App SDK – fejlesztői útmutató](intune-app-sdk-ios.md)**: Ez a dokumentum részletesen ismerteti a mobil iOS-alkalmazásnak az Intune App SDK-val való engedélyezésének lépéseit. A dokumentum az Intune App SDK csomag részeként letöltött dokumentációs mappában található.
2. **Intune App SDK iOS-ban**: A Microsoft Intune-ból letöltött Intune App SDK csomag tartalmaz egy „Intune App SDK for iOS” nevű aláírt mappát. Ebben a mappában megtalálja az iOS rendszerhez készült Intune App SDK teljes tartalmát.

Androidos mobilalkalmazás Intune App SDK-val való engedélyezéséhez a következőkre lesz szüksége:

1. **[Androidhoz készült Microsoft Intune App SDK – fejlesztői útmutató](intune-app-sdk-android.md)**: Ez a dokumentum részletesen ismerteti az androidos mobilalkalmazásnak az Intune App SDK-val való engedélyezésének lépéseit. A dokumentum az Intune App SDK csomag részeként letöltött dokumentációs mappában található.
2. **Intune App SDK Androidban**: A Microsoft Intune-ból letöltött Intune App SDK csomag tartalmaz egy „Intune App SDK for Android” nevű aláírt mappát. Ebben a mappában megtalálja az Android rendszerhez készült Intune App SDK teljes tartalmát.

## Telemetria kikapcsolása az alkalmazásra vonatkozóan

**iOS-hez készült Intune App SDK**: Az SDK alapértelmezés szerint naplózza a használati események SDK-telemetriai adatait. Az adatokat az SDK a Microsoft Intune-nak küldi el.

Ha megadta, hogy nem kíván SDK-ból származó telemetrikus adatokat küldeni a Microsoft Intune-nak az alkalmazásából, le **kell** tiltania az SDK-ban a telemetria-átvitelt az `IntuneMAMSettings` alatt, a `MAMTelemetryDisabled` „YES” (IGEN) értékének megadásával.

**Androidhoz készült Intune App SDK**: Az SDK-telemetriai adatokat a program nem naplózza az SDK használatával.

## A MAM használatát támogató alkalmazás tesztelése a Microsoft Intune-nal

Miután végrehajtotta a szükséges lépéseket az iOS vagy Android rendszerhez készült Intune App SDK felkészítésére (az Intune App SDK integrálására), meg kell győződnie arról, hogy a végfelhasználóknál és a rendszergazdánál engedélyezve vannak és működnek az alkalmazásfelügyeleti szabályzatok. A felkészített alkalmazás teszteléséhez a következőkre lesz szüksége:

1. **A MAM használatát támogató Microsoft Intune-alkalmazás tesztelése**: A jelen dokumentum részletesen ismerteti a MAM használatát támogató iOS- vagy androidos alkalmazások Microsoft Intune-nal való tesztelésének lépéseit. A dokumentum az Intune App SDK csomag részeként letöltött dokumentációs mappában található.
2. **Microsoft Intune-fiók**: A MAM használatát támogató alkalmazásoknak a Microsoft Intune-nal való teszteléséhez szüksége lesz egy Microsoft Intune-fiókra. Ha egy független szoftverszállítóként engedélyezi a MAM-hoz az iOS vagy Android rendszerhez készült áruházbeli alkalmazásait, a regisztráció (az ezt ismertető lépésben leírt módon történő) befejezése után kapni fog egy promóciós kódot. A promóciós kód lehetővé teszi, hogy feliratkozzon a Microsoft Intune próbaverziójának 1 évig meghosszabbított használatára. Az áruházban nem közzéteendő üzleti alkalmazások fejlesztői az adott szervezeten keresztül kaphatnak hozzáférést a Microsoft Intune-hoz. Emellett feliratkozhat a [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) 1 hónapos ingyenes próbaidőszakára is.




<!--HONumber=Jun16_HO4-->


