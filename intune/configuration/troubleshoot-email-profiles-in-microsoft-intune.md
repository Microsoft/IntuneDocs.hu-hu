---
title: E-mail-profilok hibakeresése Microsoft Intune-Azure-ban | Microsoft Docs
description: Tekintse meg a gyakori problémákat és megoldásokat a Microsoft Intune e-mail-profiljaival, beleértve az ismétlődő e-mail-profilokat és hibákat a Samsung KNOX standard Android-eszközökön
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/17/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec3a5a5aa4d30dcac0f954057f0cc51ffde6a950
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730519"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>A Microsoft Intune e-mail-profiljaival kapcsolatos gyakori problémák és megoldások

Tekintse át az e-mail-profilokkal kapcsolatos gyakori problémákat, valamint a hibaelhárítást és a problémák megoldását.

## <a name="what-you-need-to-know"></a>Amit még tudnia kell

- Az e-mail profilok az eszközt regisztráló felhasználó számára lettek telepítve. Az e-mail-profil konfigurálásához az Intune a felhasználó e-mail-profiljában lévő Azure Active Directory (AD) tulajdonságokat használja a regisztráció során. Az [eszközökhöz tartozó e-mail-beállítások](email-settings-configure.md) megfelelő erőforrást adhatnak hozzá.
- Az Configuration Manager hibridről az Intune-ba való Migrálás után az e-mail-profilja Configuration Manager Hybrid marad az eszközön 7 napig. Ez a várt viselkedés. Ha előbb el szeretné távolítani az e-mail profilt, forduljon az [Intune támogatási szolgálatához](../fundamentals/get-support.md).
- Android Enterprise esetén a felügyelt Google Play Áruház használatával telepítse a Gmail vagy a Nine for Work szolgáltatást. A [felügyelt Google Play-alkalmazások hozzáadása](../apps/apps-add-android-for-work.md) a lépéseket sorolja fel.
- Az iOS és az Android rendszerhez készült Microsoft Outlook nem támogatja az e-mail-profilokat. Ehelyett helyezzen üzembe egy alkalmazás-konfigurációs házirendet. További információ: [Outlook konfigurációs beállítás](../apps/app-configuration-policies-outlook.md).
- Előfordulhat, hogy az eszközökre irányuló e-mail-profilok (nem felhasználói csoportok) nem lesznek továbbítva az eszközre. Ha az eszköz elsődleges felhasználóval rendelkezik, az eszközök célzásának működnie kell. Ha az e-mail-profil felhasználói tanúsítványokat tartalmaz, ügyeljen arra, hogy a felhasználói csoportokat célozza meg.
- Előfordulhat, hogy a rendszer ismételten kéri a felhasználókat az e-mail-profil jelszavának megadására. Ebben az esetben az e-mail-profilban hivatkozott összes tanúsítványt ellenőriznie kell. Ha az egyik tanúsítvány nem egy felhasználóhoz van rendelve, az Intune megpróbálja telepíteni az e-mail-profilt.

## <a name="device-already-has-an-email-profile-installed"></a>Az eszköz már rendelkezik telepített e-mail profillal

Ha a felhasználók e-mail-profilt hoznak létre az Intune-ban vagy az Office 365-MDM való regisztráció előtt, előfordulhat, hogy az Intune által telepített e-mail-profil nem a várt módon működik:

- **iOS**: Az Intune az állomásnév és az e-mail-cím alapján észleli a meglévő, duplikált e-mail-profilt. A felhasználó által létrehozott e-mail-profil blokkolja az Intune által létrehozott profil telepítését. Ez egy gyakori probléma, mivel az iOS-felhasználók általában létrehoznak egy e-mail-profilt, majd regisztrálhatnak. A Céges portál alkalmazás állapota szerint a felhasználó nem megfelelő, és megkérheti a felhasználót, hogy távolítsa el az e-mail-profilt.

  A felhasználónak el kell távolítania az e-mail-profilt, hogy az Intune-profil üzembe helyezhető legyen. A probléma megelőzése érdekében kérje meg a felhasználókat, hogy regisztráljanak, és engedélyezzék az Intune-nak az e-mail-profil üzembe helyezését. Ezután a felhasználók létrehozhatják az e-mail-profilját.

- **Windows**: Az Intune az állomásnév és az e-mail-cím alapján észleli a meglévő, duplikált e-mail-profilt. Az Intune felülírja a felhasználó által létrehozott meglévő e-mail profilt.

- **Samsung Knox standard**: Az Intune egy duplikált e-mail-fiókot azonosít az e-mail-cím alapján, és felülírja az Intune-profillal. Ha a felhasználó konfigurálja ezt a fiókot, az Intune-profil újra felülírja. Ez zavart okozhat a felhasználónak, akinek a fiókjának konfigurációja felül lesz írva.

A Samsung KNOX nem használja az állomásnevet a profil azonosítására. Azt javasoljuk, hogy ne hozzon létre több e-mail profilt a különböző gazdagépeken lévő ugyanazon e-mail-címre való üzembe helyezéshez, mivel azok felülírják egymást.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Hiba történt a KNOX standard-eszköz 0x87D1FDE8

**Probléma**: Miután létrehozta és üzembe helyezte a Samsung KNOX Standard rendszerhez készült Exchange Active Sync e-mail-profilt a különböző Android-eszközökhöz, a **0x87D1FDE8** vagy a **szervizelés sikertelen** hibát jelez az eszköz tulajdonságok > házirend lapján.

Ellenőrizze a Samsung KNOX EAS-profil és a forrásszabályzat konfigurációját. A Samsung Notes szinkronizálási lehetősége már nem támogatott, és ez a beállítás nem választható ki a profilban. Győződjön meg arról, hogy az eszközökön elegendő idő van a szabályzat feldolgozására, akár 24 óráig is.

## <a name="unable-to-send-images-from--email-account"></a>Nem sikerül képeket küldeni az e-mail fiókból

Azok a felhasználók, akik automatikusan konfiguráltak e-mail-fiókokat, nem tudnak képeket vagy képeket küldeni az eszközeiket. Ez a forgatókönyv akkor fordulhat elő, ha az **e-mailek küldésének engedélyezése harmadik féltől származó alkalmazásokból** nem engedélyezett.

### <a name="intune-solution"></a>Intune-megoldás

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **eszköz konfigurációja** > **profilok**lehetőséget.
3. Válassza ki az e-mail-profilt > **tulajdonságok** > **Beállítások**lehetőséget.
4. Állítsa be az **e-mailek küldésének engedélyezése harmadik féltől származó alkalmazások** számára beállítást az **engedélyezéshez**.

### <a name="configuration-manager-hybrid"></a>Hibrid Configuration Manager

1. Nyissa meg a Configuration Manager konzolt > **eszközök és megfelelőség**.

2. Bontsa ki az **áttekintés** > **megfelelőségi beállítások**@no__t – 3**Vállalati erőforrás-hozzáférés**elemet, és válassza az **e-mail profilok**lehetőséget.

3. Kattintson a jobb gombbal az e-mail-profilra, és nyissa meg a **Tulajdonságok** menüt.

4. A **Szinkronizációs beállítások** lapon válassza a **Harmadik felek alkalmazásaiból is engedélyezett az e-mailek küldése** lehetőséget.

## <a name="next-steps"></a>További lépések

Kérjen [támogatási segítséget](../fundamentals/get-support.md)a Microsofttól, vagy használja a [közösségi fórumokat](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
