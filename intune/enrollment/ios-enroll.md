---
title: iOS-eszközök regisztrálása az Intune-ban
titleSuffix: Microsoft Intune
description: iOS-eszközök a Microsoft Intune-ban való regisztrációjának beállítása.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80b9091b723e78631a13c9358687ae77c36b8d47
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729687"
---
# <a name="enroll-ios-devices-in-intune"></a>iOS-eszközök regisztrálása az Intune-ban

Az Intune lehetőséget nyújt az iPadek és iPhone-ok mobileszköz-felügyeletére (MDM), és hozzáférést biztosít a felhasználóknak a vállalati e-mailjeikhez és alkalmazásaikhoz.

Intune-rendszergazdaként engedélyezheti az iOS-eszközök regisztrációját. Engedélyezheti a felhasználók számára a személyes tulajdonban lévő eszközök regisztrálását, azaz a BYOD-regisztrációt. Emellett vállalati tulajdonban lévő eszközök is regisztrálását is engedélyezheti.

## <a name="prerequisites-for-ios-enrollment"></a>Az iOS eszközök beléptetésének előfeltételei

iOS-eszközök engedélyezése előtt végezze el az alábbi lépéseket:

- Győződjön [meg arról, hogy az eszköz jogosult az Apple-eszközök regisztrálására](https://support.apple.com/en-us/HT204142#eligibility).
- [Az Intune beállítása](../fundamentals/setup-steps.md) – Ezekkel a lépésekkel állíthatja be az Intune-infrastruktúrát. Különösen fontos, hogy az eszközregisztrációhoz szükség van [saját MDM-szolgáltató beállítására](../fundamentals/mdm-authority-set.md).
- [Apple MDM push-tanúsítvány beszerzése](apple-mdm-push-certificate-get.md) – Az Apple tanúsítványt igényel az iOS- és macOS eszközök felügyeletének lehetővé tételéhez.

## <a name="user-owned-ios-devices-byod"></a>A felhasználó tulajdonában lévő iOS-eszközök (BYOD)

Azt is engedélyezheti, hogy a felhasználók saját személyes eszközeiket regisztrálják az Intune-felügyelethez. Ezt „saját eszköz használata” vagy BYOD (Bring Your Own Device) néven ismerjük. Az előfeltételek teljesítése és a felhasználói licencek hozzárendelése után a felhasználók letölthetik az Intune Céges portál alkalmazást az App Store-ból, és az alkalmazástól kapott utasításokat követve elvégezhetik a regisztrációt. Az iOS-eszközök Céges portál adatvédelmi nyilatkozatát az [adatvédelmi nyilatkozat testreszabása](../apps/company-portal-app.md#privacy-statement-customization)című részben leírtak szerint szabhatja testre.

## <a name="company-owned-ios-devices"></a>Vállalati tulajdonban lévő iOS-eszközök

A felhasználóknak eszközöket vásárló szervezetek számára az Intune a következő módszereket támogatja a vállalati tulajdonban lévő iOS-eszközök regisztrálásához:

- Az Apple készülékregisztrációs programja (DEP)
- Apple School Manager
- Regisztrálás az Apple Configurator és a Beállítási asszisztens segítségével
- Apple Configurator – közvetlen regisztráció

A vállalati tulajdonban lévő iOS-eszközök [készülékregisztráció-kezelő](device-enrollment-manager-enroll.md) fiók használatával is regisztrálhatók.

## <a name="device-enrollment-program"></a>Készülékregisztrációs program

A szervezetek az Apple Device Enrollment készülékregisztrációs programján keresztül vásárolhatnak iOS-eszközöket. A DEP vezeték nélkül képes telepíteni egy regisztrációs profilt, amely felügyelet alá helyezi az eszközöket. További tudnivalók a [Készülékregisztrációs programról](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager

Az Apple School Manager egy eszközvásárlási és -regisztrációs program iskolák részére. A DEP-hez hasonlóan lehetőséget nyújt egy profil üzembe helyezésére az eszközök felügyeletben történő regisztrálásához. További információ az [Apple School Manager](apple-school-manager-set-up-ios.md) programról.

## <a name="apple-configurator"></a>Apple Configurator

iOS-eszközök regisztrálhatók a Mac számítógépen futó Apple Configuratorral is. Az eszközök előkészítéséhez csatlakoztassa őket USB-kapcsolaton keresztül, és telepítsen regisztrációs profilt. Az Apple Configurator használatával kétféle módon lehet regisztrálni az eszközöket:

- Regisztrálás a Beállítási asszisztenssel – ez a folyamat törli az eszköz összes adatát, felkészíti az eszközt a Beállítási asszisztens futtatására, és telepíti a cég szabályzatait az eszköz új felhasználójának.
- Közvetlen regisztrálás – ez a folyamat nem törli az eszköz összes adatát, és előre definiált szabályzattal regisztrálja azt. A módszer felhasználói affinitás nélküli eszközökkel használható.

További információ az [Apple Configurator-regisztrációról](apple-configurator-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>A Vállalati portál használata a DEP vagy az Apple Configurator által regisztrált eszközökkel

A felhasználói affinitással konfigurált eszközökön telepítheti és futtathatja a Vállalati portál alkalmazást az alkalmazások letöltéséhez és az eszközök kezeléséhez. Miután a felhasználók megkapják az eszközeiket, több további lépést kell végrehajtaniuk a Beállítási asszisztens befejezéséhez és a Vállalati portál alkalmazás telepítéséhez.

Felhasználói affinitás szükséges az alábbiak támogatásához:

- Mobilalkalmazás-felügyeleti (MAM) alkalmazások
- Feltételes hozzáférés az e-mailekhez és a vállalati adatszolgáltatásokhoz
- Vállalati portál alkalmazás

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>A vállalat által birtokolt iOS-eszközök regisztrálása felhasználói affinitás használatával

1. Amikor a felhasználók bekapcsolják az eszközüket, megjelenik a Beállítási asszisztens befejezését kérő üzenet.
2. A telepítés befejezése után a rendszer kéri a felhasználóktól az Apple ID azonosítójuk megadását. Az Apple ID azonosítót azért kell megadni, hogy az eszköz telepíthesse a Céges portál alkalmazást.
3. Az iOS-eszköz automatikusan telepíti a Céges portál alkalmazást az App Store-ból.
4. A felhasználóknak el kell indítaniuk a Céges portál alkalmazást, és be kell jelentkezniük az Intune-előfizetésükhöz társított hitelesítő adatok (mint az egyszerű felhasználónév vagy UPN) használatával.
5. Bejelentkezés után a regisztráció kész. A felhasználók ezután az összes funkciójával együtt használhatják az eszközt.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>A felhasználói affinitás nélküli vállalati tulajdonú eszközök áttekintése

A felhasználói affinitás nélkül konfigurált eszközök nem támogatják a Vállalati portált, ezért ezekre az eszközökre ne telepítse az alkalmazást. A Céges portál az olyan felhasználók számára készült, akik rendelkeznek vállalati hitelesítő adatokkal, és hozzá kell férniük a személyre szabott vállalati erőforrásokhoz (például e-mailhez). A felhasználói affinitás nélkül regisztrált eszközökhöz nem tartozhat dedikált felhasználói bejelentkezés. A felhasználói affinitás nélkül regisztrált eszközök jellemző példái közé tartoznak a kioszkok, a pénztári eszközök (POS) és a megosztott segédeszközök.

Ha szükség van a felhasználói affinitásra, az eszköz regisztrálása előtt adja meg a **Felhasználói affinitás** beállítást az eszközregisztrációs profilban. Ha egy eszközön módosítani kell az affinitási állapotot, ki kell vonnia az eszközt, majd újból regisztrálnia kell.

## <a name="see-also"></a>Lásd még:

[IOS-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune](https://support.microsoft.com/help/4039809)
