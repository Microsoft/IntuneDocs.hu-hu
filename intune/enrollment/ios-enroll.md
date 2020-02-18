---
title: IOS-/iPadOS-eszközök regisztrálása az Intune-ban
titleSuffix: Microsoft Intune
description: IOS-/iPadOS-eszközök regisztrálásának beállítása Microsoft Intuneban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d5aeb17084ea0bb76429b1fa15c9de5855220ab
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415297"
---
# <a name="enroll-iosipados-devices-in-intune"></a>IOS-/iPadOS-eszközök regisztrálása az Intune-ban

Az Intune lehetővé teszi az iPadek és iPhone-eszközök mobileszköz-felügyeletét (MDM), hogy biztonságos hozzáférést biztosítson a felhasználóknak a vállalati levelezéshez, az adatszolgáltatásokhoz és az alkalmazásokhoz

Intune-rendszergazdaként beállíthatja az iOS/iPadOS és a iPadOS eszközök regisztrációját a vállalati erőforrások eléréséhez. Lehetővé teheti a felhasználók számára a személyes tulajdonú eszközök regisztrálását, azaz a "saját eszközök használata" (BYOD) beléptetését. Beállíthatja a vállalati tulajdonú eszközök regisztrálását is.

## <a name="prerequisites-for-iosipados-enrollment"></a>IOS/iPadOS-regisztráció előfeltételei

Az iOS/iPadOS-eszközök engedélyezése előtt végezze el a következő lépéseket:

- Győződjön [meg arról, hogy az eszköz jogosult az Apple-eszközök regisztrálására](https://support.apple.com/en-us/HT204142#eligibility).
- [Az Intune beállítása](../fundamentals/setup-steps.md) – Ezekkel a lépésekkel állíthatja be az Intune-infrastruktúrát. Különösen fontos, hogy az eszközregisztrációhoz szükség van [saját MDM-szolgáltató beállítására](../fundamentals/mdm-authority-set.md).
- [Apple Mdm push-tanúsítvány beszerzése](apple-mdm-push-certificate-get.md) – az Apple-nek tanúsítványra van szüksége a IOiOS/iPadOS és a MacOS rendszerű eszközök felügyeletének engedélyezéséhez.

## <a name="user-owned-iosipados-and-ipados-devices-byod"></a>Felhasználó által birtokolt iOS-/iPadOS-és iPadOS-eszközök (BYOD)

Azt is engedélyezheti, hogy a felhasználók saját személyes eszközeiket regisztrálják az Intune-felügyelethez. Ezt „saját eszköz használata” vagy BYOD (Bring Your Own Device) néven ismerjük. A felhasználók regisztrálására három lehetőség áll rendelkezésre:
- Az alkalmazás-védelmi szabályzatok a legkönnyebb BYOD élményt biztosítják, és csak az alkalmazás szintjén biztosítanak felügyeletet. Ha azonban egy 6 számjegyű, összetett PIN-kóddal rendelkező eszközt is biztonságossá kíván tenni, ezeket a házirendeket a felhasználó beléptetésével együtt is használhatja.
- Az eszközök regisztrálása a szokásos BYOD-regisztrációnak tekinthető. Számos felügyeleti lehetőséggel látja el a rendszergazdákat.
- A felhasználó beléptetése egy egyszerűbb regisztrációs folyamat, amely az Eszközkezelő lehetőségeinek egy részhalmazát biztosítja a rendszergazdák számára. Ez a szolgáltatás jelenleg előzetes kiadásban elérhető. 

Miután végrehajtotta az előfeltételeket és a hozzárendelt felhasználói licenceket, a felhasználók letöltheti az Intune Céges portál alkalmazást az App Store áruházból, és követheti a regisztrációs utasításokat az alkalmazásban. Az iOS/iPadOS eszközökön a Céges portál adatvédelmi nyilatkozatát az [adatvédelmi nyilatkozat testreszabása](../apps/company-portal-app.md#privacy-statement-customization)című részben leírtak szerint szabhatja testre.

## <a name="company-owned-iosipados-devices"></a>Vállalati tulajdonú iOS/iPadOS-eszközök

A felhasználók számára eszközöket megvásároló szervezetek esetében az Intune a következő iOS/iPadOS vállalati tulajdonú eszközök regisztrálási módszereit támogatja:

- Az Apple készülékregisztrációs programja (DEP)
- Apple School Manager
- Regisztrálás az Apple Configurator és a Beállítási asszisztens segítségével
- Apple Configurator – közvetlen regisztráció

A vállalat által birtokolt iOS-/iPadOS-eszközöket egy [eszköz beléptetési kezelői](device-enrollment-manager-enroll.md) fiókjával is regisztrálhatja.

## <a name="device-enrollment-program"></a>Készülékregisztrációs program

A szervezetek iOS/iPadOS-eszközöket vásárolhatnak az Apple Készülékregisztrációs program (DEP) használatával. A DEP vezeték nélkül képes telepíteni egy regisztrációs profilt, amely felügyelet alá helyezi az eszközöket. További információ: [Készülékregisztrációs program](device-enrollment-program-enroll-ios.md).

## <a name="user-enrollment"></a>Felhasználói regisztráció
A felhasználó regisztrálása a rendszergazdák számára a felügyeleti lehetőségek egy részhalmazát adja meg a többi regisztrációs módszerhez képest. További információkért lásd: [felhasználói regisztráció által támogatott műveletek, jelszavak és egyéb beállítások](ios-user-enrollment-supported-actions.md) , valamint az [iOS/iPadOS és a iPadOS felhasználói regisztrációjának beállítása](ios-user-enrollment.md).

## <a name="apple-school-manager"></a>Apple School Manager

Az Apple School Manager egy eszközvásárlási és -regisztrációs program iskolák részére. A DEP-hez hasonlóan lehetőséget nyújt egy profil üzembe helyezésére az eszközök felügyeletben történő regisztrálásához. További információ az [Apple School Manager](apple-school-manager-set-up-ios.md) programról.

## <a name="apple-configurator"></a>Apple Configurator

IOS/iPadOS-eszközöket regisztrálhat Mac számítógépeken futó Apple konfigurátor használatával. Az eszközök előkészítéséhez csatlakoztassa őket USB-kapcsolaton keresztül, és telepítsen regisztrációs profilt. Az Apple Configurator használatával kétféle módon lehet regisztrálni az eszközöket:

- Regisztrálás a Beállítási asszisztenssel – ez a folyamat törli az eszköz összes adatát, felkészíti az eszközt a Beállítási asszisztens futtatására, és telepíti a cég szabályzatait az eszköz új felhasználójának.
- Közvetlen regisztrálás – ez a folyamat nem törli az eszköz összes adatát, és előre definiált szabályzattal regisztrálja azt. A módszer felhasználói affinitás nélküli eszközökkel használható.

További információ az [Apple Configurator-regisztrációról](apple-configurator-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>A Vállalati portál használata a DEP vagy az Apple Configurator által regisztrált eszközökkel

A felhasználói affinitással konfigurált eszközökön telepítheti és futtathatja a Vállalati portál alkalmazást az alkalmazások letöltéséhez és az eszközök kezeléséhez. Miután a felhasználók megkapják az eszközeiket, több további lépést kell végrehajtaniuk a Beállítási asszisztens befejezéséhez és a Vállalati portál alkalmazás telepítéséhez.

Felhasználói affinitás szükséges az alábbiak támogatásához:

- Mobilalkalmazás-felügyeleti (MAM) alkalmazások
- Feltételes hozzáférés az e-mailekhez és a vállalati adatszolgáltatásokhoz
- Vállalati portál alkalmazás

### <a name="how-users-enroll-corporate-owned-iosipados-devices-with-user-affinity"></a>Vállalati tulajdonú iOS-/iPadOS-eszközök felhasználói affinitással való regisztrálása a felhasználók számára

1. Amikor a felhasználók bekapcsolják az eszközüket, megjelenik a Beállítási asszisztens befejezését kérő üzenet.
2. A telepítés befejezése után a rendszer kéri a felhasználóktól az Apple ID azonosítójuk megadását. Az Apple ID azonosítót azért kell megadni, hogy az eszköz telepíthesse a Céges portál alkalmazást.
3. Az iOS/iPadOS eszköz automatikusan telepíti a Céges portál alkalmazást az App Store áruházból.
4. A felhasználóknak el kell indítaniuk a Céges portál alkalmazást, és be kell jelentkezniük az Intune-előfizetésükhöz társított hitelesítő adatok (mint az egyszerű felhasználónév vagy UPN) használatával.
5. Bejelentkezés után a regisztráció kész. A felhasználók ezután az összes funkciójával együtt használhatják az eszközt.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>A felhasználói affinitás nélküli vállalati tulajdonú eszközök áttekintése

A felhasználói affinitás nélkül konfigurált eszközök nem támogatják a Vállalati portált, ezért ezekre az eszközökre ne telepítse az alkalmazást. A Céges portál az olyan felhasználók számára készült, akik rendelkeznek vállalati hitelesítő adatokkal, és hozzá kell férniük a személyre szabott vállalati erőforrásokhoz (például e-mailhez). A felhasználói affinitás nélkül regisztrált eszközökhöz nem tartozhat dedikált felhasználói bejelentkezés. A felhasználói affinitás nélkül regisztrált eszközök jellemző példái közé tartoznak a kioszkok, a pénztári eszközök (POS) és a megosztott segédeszközök.

Ha szükség van a felhasználói affinitásra, az eszköz regisztrálása előtt adja meg a **Felhasználói affinitás** beállítást az eszközregisztrációs profilban. Ha egy eszközön módosítani kell az affinitási állapotot, ki kell vonnia az eszközt, majd újból regisztrálnia kell.

## <a name="see-also"></a>További információ

[IOS-/iPadOS-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune](https://support.microsoft.com/help/4039809)
