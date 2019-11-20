---
title: Eszközprofilok hibaelhárítása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Common questions and answers with device policies and profiles, including profile changes not applied to users or devices, how long it takes for new policies to be pushed to devices, which settings are applied when there are multiple policies, what happens when a profile is deleted or removed, and more with Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a1177a37ddbfa7f760339c4ad0cd7773d670540
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199191"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Common questions, issues, and resolutions with device policies and profiles in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Get answers to common questions when working with device profiles and policies in Intune. This article also lists the check-in time intervals, provides more detains on conflicts, and more.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Miért nem kap a felhasználó új profilt, amikor megváltoztatja a jelszót vagy a hozzáférési kódot egy létező Wi-Fi-profilban?

Ön létrehoz egy vállalati Wi-Fi-profilt, hozzárendeli egy csoporthoz, megváltoztatja a jelszót, és menti a profilt. A profil megváltoztatásakor egyes felhasználók esetleg nem kapják meg az új profilt.

A probléma következményei vendég Wi-Fi beállításával mérsékelhetők. A vállalati Wi-Fi kiesése esetén a felhasználók a vendég Wi-Fi-hez kapcsolódhatnak. Gondoskodjon az automatikus csatlakozás beállításáról. A vendég Wi-Fi profilt rendelje hozzá minden felhasználóhoz.

Néhány további javaslat:  

- If the Wi-Fi network you're connecting to uses a password or passphrase, make sure you can connect to the Wi-Fi router directly. Ezt kipróbálhatja egy iOS-eszközzel.
- A Wi-Fi-végponthoz (Wi-Fi-útválasztóhoz) való sikeres kapcsolódás után jegyezze fel az SSID-t és a használt hitelesítő adatokat (ez a jelszó vagy a hitelesítő kód).
- Adja meg az SSID-t és a hitelesítő adatokat (jelszót vagy hitelesítő kódot) az Előmegosztott kulcs mezőben. 
- Alkalmazza egy tesztcsoportra, amelynek csak néhány tagja van, lehetőleg a rendszergazdák közül. 
- Szinkronizálja az iOS-eszközt az Intune-nal. Regisztráljon, ha ezt még nem tette meg. 
- Próbáljon meg újból kapcsolódni ugyanahhoz a Wi-Fi-végponthoz (az első lépésben leírtak szerint).
- Bővítse ki a kört nagyobb csoportokra és végül mindenkire, aki a szervezetben várhatóan felhasználó lesz. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>How long does it take for devices to get a policy, profile, or app after they are assigned?

Intune notifies the device to check in with the Intune service. The notification times vary, including immediately up to a few hours. These notification times also vary between platforms.

If a device doesn't check in to get the policy or profile after the first notification, Intune makes three more attempts. An offline device, such as turned off, or not connected to a network, may not receive the notifications. In this case, the device gets the policy or profile on its next scheduled check-in with the Intune service, which is **estimated** at:

| Platfésm | Refresh cycle|
| --- | --- |
| iOS | About every 8 hours |
| macOS | About every 8 hours |
| Android: | About every 8 hours |
| Eszközként regisztrált Windows 10 számítógépek | About every 8 hours |
| Windows Phone | About every 8 hours |
| Windows 8.1 | About every 8 hours |

If the device recently enrolled, the compliance and configuration check-in runs more frequently, which is **estimated** at:

| Platfésm | Gyakoriság |
| --- | --- |
| iOS | Every 15 minutes for 1 hour, and then around every 8 hours |  
| macOS | Every 15 minutes for 1 hour, and then around every 8 hours | 
| Android: | Every 3 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 
| Eszközként regisztrált Windows 10 számítógépek | Every 3 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 
| Windows Phone | Every 5 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 
| Windows 8.1 | Every 5 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 

At any time, users can open the Company Portal app, **Settings** > **Sync** to immediately check for policy or profile updates.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Milyen műveletek hatására küld az Intune azonnal értesítést egy eszközre?

There are different actions that trigger a notification, such as when a policy, profile, or app is assigned (or unassigned), updated, deleted, and so on. These action times vary between platforms.

Devices check in with Intune when they receive a notification to check in, or during the scheduled check-in. When you target a device or user with an action, such as lock, passcode reset, app, profile or policy assignment, then Intune immediately notifies the device to check in to receive these updates.

Other changes, such as revising the contact information in the Company Portal app, don't cause an immediate notification to devices.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Ha ugyanazon felhasználóhoz vagy eszközhöz több szabályzat is hozzá van rendelve, honnan tudható, hogy mely beállítások lesznek alkalmazva?

When two or more policies are assigned to the same user or device, then the setting that applies happens at the individual setting level:

- Compliance policy settings always have precedence over configuration profile settings.

- If a compliance policy evaluates against the same setting in another compliance policy, then the most restrictive compliance policy setting applies.

- If a configuration policy setting conflicts with a setting in another configuration policy, this conflict is shown in Intune. Ezeket az ütközéseket manuálisan kell feloldani.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Mi történik, ha ütközés van két alkalmazásvédelmi szabályzat között? Melyik érvényes az alkalmazásra?

Conflict values are the most restrictive settings available in an app protection policy *except* for the number entry fields, such as PIN attempts before reset. The number entry fields are set the same as the values, as if you created a MAM policy using the recommended settings option.

Conflicts happen when two profile settings are the same. Például előfordulhat, hogy a másolás/beillesztés beállításra két megegyező MAM-házirendet konfigurált. Ebben az esetben a másolás/beillesztés a legszigorúbb értékre lesz beállítva, a többi beállítás pedig a konfiguráltak szerint lesz alkalmazva.

A policy is deployed to the app and takes effect. A second policy is deployed. In this scenario, the first policy takes precedence, and stays applied. The second policy shows a conflict. If both are applied at the same time, meaning that there isn't preceding policy, then both are in conflict. Minden ütközésnél a legszigorúbb beállítás lesz érvényes.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Mi történik, ha az egyéni iOS-házirendek ütköznek?

Az Intune nem értékeli a konfigurációs Apple-fájlok vagy az Open Mobile Alliance egységes erőforrás-azonosítóra (OMA-URI) vonatkozó egyéni szabályzatainak tartalmát. Csak kézbesítési mechanizmusként funkcionál.

When you assign a custom policy, confirm that the configured settings don't conflict with compliance, configuration, or other custom policies. If a custom policy and its settings conflict, then the settings are applied randomly.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Mi történik, ha egy profilt törölnek, vagy az már nem érvényes?

When you delete a profile, or you remove a device from a group that has the profile, then the profile and settings are removed from the device as described:

- Wi-Fi, VPN, tanúsítvány és e-mail profilok: Ezek a profilok az összes támogatott regisztrált eszközről el lesznek távolítva.
- Minden más profiltípus esetén:  

  - **Windows and Android devices**: Settings aren't removed from the device
  - **Windows Phone 8.1 rendszerű eszközök**: A következő beállítások törlődnek:  
  
    - Jelszó szükséges a mobileszközök feloldásához
    - Egyszerű jelszavak engedélyezése
    - Jelszó minimális hossza
    - Kötelező jelszótípus
    - Jelszó lejárata (nap)
    - Jelszóelőzmények megjegyzése
    - Sikertelen bejelentkezések engedélyezett száma az eszköz törlése előtt
    - Tétlen percek száma, mielőtt az eszköz újból kéri a jelszót
    - Kötelező jelszótípus – megadandó karakterek minimális száma
    - Kamera használatának engedélyezése
    - Mobileszköz titkosításának kötelezővé tétele
    - Cserélhető tároló használatának engedélyezése
    - Webböngésző használatának engedélyezése
    - Alkalmazástároló használatának engedélyezése
    - Képernyőfelvétel-készítés használatának engedélyezése
    - Földrajzi hely meghatározásának engedélyezése
    - Microsoft-fiók használatának engedélyezése
    - Másolás és beillesztés használatának engedélyezése
    - Wi-Fi alapú internetmegosztás használatának engedélyezése
    - Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése
    - Wi-Fi elérési pontok jelentéskészítésének engedélyezése
    - Összes adat törlésének engedélyezése
    - Bluetooth használatának engedélyezése
    - NFC használatának engedélyezése
    - Wi-Fi használatának engedélyezése

  - **iOS**: Az összes beállítás törlődik, kivéve a következőket:
  
    - Hangroaming engedélyezése
    - Adatroaming engedélyezése
    - Automatikus szinkronizálás engedélyezése roaming közben

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Módosítottam egy eszközkorlátozási profilt, de a módosítások még nem léptek érvénybe

Once set, Windows Phone devices don't allow security policies set using MDM or EAS to be reduced in security. For example, you set a **Minimum number of character password** to 8. You try to reduce it to 4. The more restrictive profile is already applied to the device.

To change the profile to a less secure value, then reset security policies. For example, in Windows 8.1, on the desktop, swipe in from right > select **Settings** > **Control Panel**. Válassza a **Felhasználói fiókok** kisalkalmazást. In the left-hand navigation menu, there's a **Reset Security Policies** link (toward the bottom). Válassza ki ezt, majd a **Szabályzatok alaphelyzetbe állítása** lehetőséget.

Other MDM devices, such as Android, Windows Phone 8.1 and later, iOS, and Windows 10 may need to be retired, and re-enrolled in to Intune to apply a less restrictive profile.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Some settings in a Windows 10 profile return "Not Applicable"

Some settings on Windows 10 devices may show as "Not Applicable". When this happens, that specific setting isn't supported on the version or edition of Windows running on the device. This message can occur for the following reasons:

- The setting is only available for newer versions of Windows, and not the current operating system (OS) version on the device.
- The setting is only available for specific Windows editions or specific SKUs, such as Home, Professional, Enterprise, and Education.

To learn more about the version and SKU requirements for the different settings, see the [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>További lépések

További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](../fundamentals/get-support.md).
