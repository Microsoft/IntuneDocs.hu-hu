---
title: Windows-számítógép felügyeleti lehetőségeinek összehasonlítása
titleSuffix: Microsoft Intune
description: A vállalat által birtokolt iOS-eszközök regisztrálása az Apple Készülékregisztrációs program (DEP) vagy az Apple Configurator eszköz segítségével.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/13/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8fd53e9d12dd38639d204e214aea03d733e584b
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059202"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Windows-számítógépek számítógépként és mobileszközként való felügyeletének összehasonlítása

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

A vállalatok a Microsoft Intune-ban kezelhetik a Windows-számítógépeket mobileszközként, a mobileszköz-kezelés (MDM) vagy számítógépként az Intune szoftverügyfél használatával.  A Microsoft azt javasolja, hogy az ügyfelek lehetőség szerint az MDM-megoldást válasszák a felügyelethez. A két választási lehetőség közötti különbség jobb megértése érdekében a következő táblázat összehasonlítja a két felügyeleti megoldást.

|**Képesség/forgatókönyv** |**Windows számítógépként**<br>Intune-szoftverügyfél | **Windows mobileszközként**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Operációs rendszerek** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Intune-portál támogatása** |[Silverlight-konzol](https://manage.microsoft.com)|[Azure Portal](https://portal.azure.com) |
|**Feltételes hozzáférés**|Nem érhető el|Elérhető <br>[Mi a feltételes hozzáférés?](../protect/conditional-access.md)|
|**Tömeges beléptetés**|Nem érhető el|Elérhető <br>[Windowsos eszközök csoportos regisztrálása](../enrollment/windows-bulk-enroll.md)|
|**Eszközprofilok**|Nem érhető el|Elérhető <br>[Mik azok a Microsoft Intune-eszközprofilok?](../configuration/device-profiles.md)|
|**Ügynök nélküli regisztráció**|Nem érhető el |Elérhető<br>[Windows-eszközök regisztrálása](../enrollment/windows-enroll.md)|
|**Szoftverfrissítések kezelése**| Windows-frissítések és a Microsoft-alkalmazások frissítése<br>[Windows rendszerű számítógépek naprakészen tartása szoftverfrissítésekkel](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Vállalati Microsoft Áruház a Windows 10-hez és a Microsoft-alkalmazások frissítéséhez<br> [A Vállalati Windows Update beállításainak konfigurálása](../protect/windows-update-for-business-configure.md) |
|**Szoftverlicencek kezelése**|Elérhető <br>[Windows-számítógépes szoftverek licencszerződéseinek kezelése](../manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Vállalat Microsoft Áruház (csak .appx-alkalmazások)<br>[A Vállalati Microsoft Áruházban vásárolt alkalmazások kezelése](../apps/windows-store-for-business.md)|
|**Leltár**|Elérhető <br>[Hardver- és szoftverleltár megtekintése Windows rendszerű számítógépeken](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Elérhető <br>[Alkalmazás-hozzárendelések figyelése](../apps/apps-monitor.md)<br>[Mi az eszközkezelés?](../remote-actions/device-management.md)|
|**Windows tűzfalszabályzat**|Elérhető <br>[A Windows rendszerű számítógépek védelme Windows tűzfalházirendek használatával](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Elérhető <br>[Microsoft Defender-tűzfal](../protect/endpoint-protection-windows-10.md#microsoft-defender-firewall)|
|**Kártevők elleni védelem**|Endpoint Protection<br>[Windows rendszerű számítógépek biztonságossá tétele az Endpoint Protection szolgáltatással](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Microsoft Defender<br>[A Microsoft Defender engedélyezése](../protect/advanced-threat-protection.md)|
|**Távsegítség** |TeamViewer<br>[Távsegítség kérése és nyújtása Windows rendszerű számítógépekhez](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [A TeamViewer használata Intune-eszközök távoli felügyeletéhez](../remote-actions/teamviewer-support.md) |
|**Alkalmazástelepítés** | Nem érhető el a Vállalati Microsoft Áruházhoz,<br>.exe, .appx, és csak a több fájlból álló .msi<br>[Az Intune szoftverügyfelet futtató Windows rendszerű számítógépes alkalmazások hozzáadása](add-apps-for-windows-pcs-in-microsoft-intune.md)|Elérhető a Microsoft Áruház alkalmazásaihoz és az üzletági alkalmazásokhoz<br>[Windows áruházbeli alkalmazások hozzáadása](../apps/store-apps-windows.md)<br>[Windowsos üzletági (LOB) alkalmazások hozzáadása](../apps/lob-apps-windows.md)|
|**Alkalmazásvédelem**|Nem érhető el|Elérhető <br>[Mik azok az alkalmazásvédelmi szabályzatok?](../apps/app-protection-policy.md)|
|**Állapot igazolása**|Nem érhető el|Elérhető|


## <a name="advantages-of-mdm-windows-pc-management"></a>Az MDM Windows-számítógép-felügyelet előnyei
A Windows-számítógépek modern mobileszköz-felügyelettel történő kezelése a következő előnyökkel jár:
- **Méretezhetőség** – A mobileszköz-felügyelet az Intune-felhőkezeléssel együtt méretezhető. Az Intune szoftverügyfél 7000 számítógépre korlátozódik.
- **Egyszerűség** – Az operációs rendszerben foglalt modern felügyeleti képességeket használ anélkül, hogy letöltött szoftverügyfélre kellene támaszkodnia
- **Konzisztencia** – A Windows-számítógépeket ugyanúgy kezelheti, mint az összes többi mobileszközt a cégnél
<!-- - **Cloud optimization** - -->
