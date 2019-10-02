---
title: Az Intune által a Google-nek küldött adatok
titleSuffix: Microsoft Intune
description: Az Intune által az Google-nek küldött adatok listája.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f0825d44ba52bee1331fe1d715e4e58806e80f5
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729327"
---
# <a name="data-intune-sends-to-google"></a>Az Intune által a Google-nek küldött adatok

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ha az Android Enterprise eszközkezelése engedélyezve van egy eszközön, a Microsoft Intune kapcsolatot létesít az Google-lel, és felhasználói és eszközadatokat oszt meg vele. Ahhoz, hogy a Microsoft Intune létrehozhassa a kapcsolatot, Önnek létre kell hoznia egy Google-fiókot.

Az alábbi táblázat felsorolja az adatokat, amelyeket az eszközkezelés engedélyezése esetén a Microsoft Intune küld a Google-nek:


| A Google-nek küldött adat | Részletek | Használatban | Példa |
|:---:|:---:|:---:|:---:|
| EnterpriseId | A Google adja meg a Gmail-fiók és az Intune összekapcsolásakor. | Az Intune és a Google közötti kommunikáció során használt elsődleges azonosító.  Ehhez a kommunikációhoz tartozik a szabályzatok beállítása, az eszközök kezelése és az Android Enterprise és az Intune közötti kapcsolat létrehozása és bontása. | Egyedi azonosító, példa formátum: LC04eik8a6 |
| Szabályzattörzs | Az Intune adja meg új alkalmazás- vagy konfigurációs szabályzat mentésekor. | Szabályzatok alkalmazása az eszközökre. | Ez az egy alkalmazás- vagy konfigurációs szabályzathoz konfigurált összes beállítás gyűjteménye. Ha azok egy szabályzatban meg vannak adva, akkor tartalmazhat olyan ügyféladatokat is, mint a hálózati nevek, alkalmazásnevek és alkalmazás-specifikus beállítások. |
| Eszközadatok | Az eszközök munkahelyi profillal való alkalmazása az Intune-ban történő regisztrációval kezdődik. A felügyelt eszközök alkalmazásának első lépése a Google-ben történő regisztráció. | Az Intune és a Google többféle tevékenység során cserélhet eszközadatokat. Ilyen például a szabályzatok alkalmazása, az eszköz kezelése és az általános jelentéskészítés. | **Az eszköz neveként használt egyedi azonosító.** Példa: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**A felhasználó neveként használt egyedi azonosító.** Példa: Vállalatok/LC04ebru7b/felhasználók/116838519924207449711<br>**Eszköz állapota** Példák: Aktív, letiltva, kiépítés.<br>**Megfelelőségi állapotok.** Példák: A beállítás nem támogatott, a szükséges alkalmazások hiányoznak<br>**Szoftveradatok.** Példák: szoftverfrissítések & verzió javítási szintje.<br>**Hálózati adatok.** Példák: IMEI, MEID, WifiMacAddress<br>**Device Settings.** Példák: A titkosítási szintekre vonatkozó információk &, hogy az eszköz engedélyezi-e az ismeretlen alkalmazásokat.<br> A lap alján egy JSON-üzenetminta is található. |
| newPassword | Az Intune adja meg. | Az eszköz PIN-kódjának alaphelyzetbe állítása. | Az új jelszóként használt sztring. |
| Google User | Google | Munkahelyi profil kezelése munkahelyi profil (BYOD) alapú helyzetekben. | Egyedi azonosító a kapcsolt Gmail-fiókhoz. Példa: 114223373813435875042 |
| Alkalmazásadatok | Az Intune adja meg alkalmazásszabályzat mentésekor. |  | Alkalmazásnév sztringje. Példa: app:com.microsoft.windowsintune.companyportal |
| Vállalati szolgáltatásfiók | A Google adja meg az Intune kérelmére válaszolva. | Az adott ügyfelet érintő Intune és Google közötti tranzakciók során használt hitelesítő adat. | Több részből áll:<br> **EnterpriseId**: lásd fent.<br>**UPN**: az ügyfél részéről történő hitelesítéshez generált UPN.<br>Például: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Kulcs**: A hitelesítési kérelmekben használt Base64 kódolású blob a szolgáltatásban titkosítva van, de a blob így néz ki:<br> A felhasználó kulcsaként használt egyedi azonosító<br>Példa: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


Ha nem szeretné használni az Android Enterprise eszközkezelést az Intune-nal, és törölni szeretné az adatokat, le kell tiltania a Microsoft Intune Android Enterprise eszközkezelést, és törölnie kell a Google-fiókját. A fiókkezelésről a Google-fiókban tudhat meg többet.


