---
title: "Az Intune által az Apple-nek küldött adatok"
titleSuffix: Microsoft Intune
description: "Az Intune által az Apple-nek küldött adatok listája."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c247cfbd715368f65dfb1ba2ce8b5e88a491d302
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/20/2018
---
# <a name="data-intune-sends-to-apple"></a>Az Intune által az Apple-nek küldött adatok

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Ha a következő Apple-szolgáltatások bármelyike engedélyezve van egy eszközön, a Microsoft Intune kapcsolatot létesít az Apple-lel, és felhasználói és eszközadatokat oszt meg vele: 

- [Apple Készülékregisztrációs program (DEP)](device-enrollment-program-enroll-ios.md)
- [Apple MDM Push-tanúsítvány (APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apple Volume Purchase Program (VPP)](vpp-apps-ios.md)

Mielőtt a Microsoft Intune létrehozhatná a kapcsolatot, Önnek létre kell hoznia egy Apple-fiókot minden Apple-szolgáltatáshoz.

A következő táblázat ismerteti azokat az adatokat, amelyeket a Microsoft Intune az eszközökről az engedélyezett Apple-szolgáltatásoknak küld. 

| Szolgáltatás | Az Apple-nek küldött adatok | Felhasználási mód |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | Ha a kiszolgáló elfogadja az eszközt, az eszköz megadja a leküldéses értesítéses eszközjogkivonatát a kiszolgálónak. A kiszolgáló ezzel a jogkivonattal küld leküldéses értesítéseket az eszköznek. Ez a bejelentkező üzenet is tartalmaz egy PushMagic-karakterláncot. A kiszolgáló megjegyzi ezt a karakterláncot, és belefoglalja minden, az eszköznek küldött leküldéses üzenetbe. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Kiszolgálói jogkivonat | Az Apple-szolgáltatást hitelesítő leküldéses értesítéses eszközjogkivonat. |
| ASM/DEP | kiszolgáló_neve | Az MDM-kiszolgáló azonosítható neve. |
| ASM/DEP | server_uuid | A rendszer által létrehozott kiszolgálóazonosító. |
| ASM/DEP | admin_id | A jelenleg használt jogkivonatokat létrehozó személy Apple ID azonosítója. |
| ASM/DEP | org_name | A szervezet neve. |
| ASM/DEP | org_email | A szervezet e-mail-címe. |
| ASM/DEP | org_phone | A szervezet telefonszáma. |
| ASM/DEP | org_address | A szervezet címe. |
| ASM/DEP | org_id | A DEP-felhasználó azonosítója. Ez a kulcs csak a 3. és újabb protokollverziókban érhető el. |
| ASM/DEP | serial_number | Az eszköz sorozatszáma (karakterlánc). |
| ASM/DEP | modell | A modell neve (karakterlánc). |
| ASM/DEP | leírás | Az eszköz leírása (karakterlánc). |
| ASM/DEP | asset_tag | Az eszköz eszközcímkéje (karakterlánc). |
| ASM/DEP | profile_status | A profil telepítésének állapota. Lehetséges értékek: **üres**, **hozzárendelt**, **leküldött**, vagy **eltávolított**. |
| ASM/DEP | profile_uuid | A hozzárendelt profil egyedi azonosítója. |
| ASM/DEP | device_assigned_by | Az eszközt hozzárendelő személy e-mail-címe. |
| ASM/DEP | os | Az eszköz operációs rendszere: iOS, OSX vagy tvOS. Ez a kulcs a 2. és újabb X-Server-Protocol-verziókban érvényes. |
| ASM/DEP | device_family | Az eszköz Apple-termékcsaládja: iPad, iPhone, iPod, Mac vagy AppleTV. Ez a kulcs a 2. és újabb X-Server-Protocol-verziókban érvényes. |
| ASM/DEP | profile_name | Karakterlánc. A profil természetes nyelven olvasható neve. |
| ASM/DEP | support_phone_number | Nem kötelező. Karakterlánc. A szervezet támogatási telefonszáma. |
| ASM/DEP | support_email_address | Nem kötelező. Karakterlánc. A szervezet támogatási e-mail-címe. Ez a kulcs a 2. és újabb X-Server-Protocol-verziókban érvényes. |
| ASM/DEP | Részleg | Nem kötelező. Karakterlánc. A felhasználó által megadott részleg vagy hely neve. |
| ASM/DEP | eszközök | Az eszközök sorozatszámait tartalmazó karakterláncok tömbje. (Üres is lehet.) |
| VPP | Intune UserId guid | Az Intune által létrehozott GUID. |
| VPP | A felügyelt AppleId egyszerű felhasználóneve | Az az AppleID-azonosító, amelyet a rendszergazda adott meg a VPP-jogkivonat kapcsolatának Apple-lel való konfigurálásakor. |
| VPP | Sorozatszám | A kezelt eszköz sorozatszáma. |

Ha nem szeretné használni az Apple szolgáltatásait az Intune-nal, és törölni szeretné az adatokat, le kell tiltania a Microsoft Intune Apple-jogkivonatot és törölnie kell az Apple-fiókját. A fiókkezelésről az Apple-fiókban tudhat meg többet.


