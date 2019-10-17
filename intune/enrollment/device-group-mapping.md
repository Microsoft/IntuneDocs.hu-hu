---
title: Eszközök kategorizálása csoportokba az Intune-ban
titleSuffix: Microsoft Intune
description: Információ arról, hogyan lehet az eszközöket csoportokba rendezni a könnyebb kezelhetőség érdekében.
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
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ab720ffee3f468d3700558dfbde460ee8f712ea
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505498"
---
# <a name="categorize-devices-into-groups"></a>Eszközök kategorizálása csoportokba

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az eszközök könnyebb kezeléséhez Microsoft Intune eszközök kategóriáit használhatja, hogy az Ön által meghatározott kategóriák alapján automatikusan hozzáadja az eszközöket a csoportokhoz.

Az eszközkategóriák a következő munkafolyamatot használják:
1. Kategóriák létrehozása, amelyek közül a felhasználók választhatnak az eszközük regisztrálásakor.
2. Az iOS-es és androidos eszközök felhasználóinak egy eszköz regisztrációjakor a konfigurált kategórialistából kell kategóriát választaniuk. Kategória Windows-eszközhöz rendelésekor a felhasználóknak a Céges portál webhelyét kell használniuk.
3. Ezután szabályzatokat és alkalmazásokat telepíthet ezekre a csoportokra.

Bármilyen tetszés szerinti eszközkategóriát létrehozhat. Példa:
- Pénztári eszközök
- Bemutatóeszközök
- Értékesítés
- Könyvelés
- Manager

## <a name="how-to-configure-device-categories"></a>Az eszközkategóriák konfigurálása

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>1\. lépés: Eszközkategóriák létrehozása az Azure Portal Intune panelén
1. Az [Azure Portalbeli Intune-on](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** elemet.
2. Az **Eszközregisztráció** panelen válassza az **Eszközkategóriák** elemet.
3. Az **Eszközkategóriák** lapon a **Létrehozás** elemmel hozhat létre új kategóriát.
4. Az **Eszközkategória létrehozása** panelen töltse ki az új kategória **Név** és **Leírás** mezőjét (utóbbi nem kötelező).
5. Amikor elkészült, válassza a **Létrehozás** gombot. Az új kategória megjelenik a kategóriák listájában.

Azure Active Directory (Azure AD) biztonsági csoportok létrehozásakor az eszközkategória nevét fogja használni a 2. lépésben.

### <a name="step-2-create-azure-active-directory-security-groups"></a>2\. lépés: Azure Active Directory biztonsági csoportok létrehozása
Ebben a lépésben az eszközkategória és az eszközkategória-név alapján dinamikus csoportokat fog létrehozni az Azure-portálon.

A folytatáshoz tekintse meg a [Speciális szabályok létrehozása attribútumok használatával](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) című témakört az Azure AD dokumentációjában.

Ezen szakasz információi alapján hozzon létre speciális szabállyal egy eszközcsoportot a **deviceCategory** attribútum segítségével. Például: **device.deviceCategory -eq** "*Azure Portalon lekért eszközkategória-név*".

Ha vannak konfigurált eszközcsoportok, amikor a felhasználók regisztrálják eszközüket, meg fog jelenni számukra az Ön által beállított kategóriák listája. A kategória kiválasztását és a regisztráció befejezését követően az eszköz a kiválasztott kategóriának megfelelő Active Directory biztonsági csoportba kerül.

### <a name="view-the-categories-of-devices-that-you-manage"></a>A felügyelt eszközök kategóriáinak megtekintése

1. Az [Azure Portalbeli Intune-on](https://aka.ms/intuneportal) válassza az **Eszközök** elemet.

2. A **Felügyelet** alatt válassza a **Minden eszköz** lehetőséget.

3. Az eszközlistában keresse meg az **Eszközkategória** oszlopot.

Ha az **Eszközkategória** oszlop nem jelenik meg, válassza az **Oszlopok** elemet. Jelölje ki a lista **Eszközkategória** elemét majd válassza az **Alkalmaz** lehetőséget.

### <a name="change-the-category-of-a-device"></a>Eszköz kategóriájának módosítása

1. Az [Azure Portalbeli Intune-on](https://aka.ms/intuneportal) válassza az **Eszközök** elemet.
2. A **Felügyelet** szakasz **Eszközök** paneljén válassza a **Minden eszköz** lehetőséget.
3. Jelölje ki a kívánt eszközt az eszközök listájában. Ezután a **Felügyelet** eszköztulajdonságok panelén válassza a **Tulajdonságok** lehetőséget.
4. A következő panelen a kijelölt eszköz **Eszközkategória** tulajdonságát átállíthatja a korábban konfigurált kategórianevek bármelyikére.

## <a name="after-you-configure-device-groups"></a>Az eszközcsoportok konfigurálása után

Az iOS-es és androidos eszközök felhasználóinak eszközük regisztrációjakor a konfigurált kategórialistából kell kategóriát választaniuk. A kategória kiválasztását és a regisztráció befejezését követően a rendszer a kiválasztott kategóriának megfelelő Intune-eszközcsoporthoz vagy Active Directory biztonsági csoporthoz adja az eszközüket.

Windows-felhasználóknak a kategória kiválasztásához a Céges portál webhelyet kell használniuk.

Az eszköz regisztrálása után felhasználói a platformtól függetlenül mindig elérhetik a portal.manage.microsoft.com webhelyet. Kérje meg a felhasználót, hogy nyissa meg a Céges portál webhelyet, és válassza a **Saját eszközök** lehetőséget. A felhasználó itt választhat egy regisztrált eszközt a lapon található listából, majd megadhat egy kategóriát.

A kategória kiválasztása után az eszköz automatikusan bekerül az Ön által létrehozott, a kategóriának megfelelő csoportba. Ha az eszköz már a kategóriák konfigurálása előtt regisztrálva lett, akkor a felhasználó értesítést kap az eszközről a Céges portál webhelyen. A felhasználó innen tudja meg, hogy kategóriát kell választania, amikor legközelebb iOS vagy Android rendszeren éri el a Céges portál alkalmazást.

## <a name="further-information"></a>További információ
- Az Azure Portalon szerkesztheti az eszközkategóriákat, ekkor viszont manuálisan kell módosítania az Azure Active Directoryban az adott kategóriára hivatkozó biztonsági csoportokat.

- Ha töröl egy kategóriát, az ahhoz hozzárendelt eszközöknél a **Nincs hozzárendelve** kategórianév jelenik meg.
