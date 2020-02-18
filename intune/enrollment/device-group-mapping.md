---
title: Eszközök az Intune-ban csoportokba sorolása
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
ms.openlocfilehash: f0976ff8e6ec45f1f861fd4a4e0474255d701ae4
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414260"
---
# <a name="categorize-devices-into-groups"></a>Eszközök csoportokba sorolása

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Eszközök kezelésének megkönnyítése érdekében a Microsoft Intune eszközkategóriák segítségével automatikusan adja hozzá az eszközök az Ön által meghatározott kategóriák alapján.

Az eszközkategóriák a következő munkafolyamatot használják:
1. Kategóriák létrehozása, amelyek közül a felhasználók választhatnak az eszközük regisztrálásakor.
2. Ha az iOS/iPadOS és az Android rendszerű eszközök felhasználóinak regisztrálnak egy eszközt, ki kell választaniuk egy kategóriát a konfigurált kategóriák listájáról. Kategória Windows-eszközhöz rendelésekor a felhasználóknak a Céges portál webhelyét kell használniuk.
3. Ezután szabályzatokat és alkalmazásokat telepíthet ezekre a csoportokra.

Bármilyen tetszés szerinti eszközkategóriát létrehozhat. Például:
- Pénztári eszközök
- Bemutatóeszközök
- Értékesítés
- Könyvelés
- Manager

## <a name="how-to-configure-device-categories"></a>Az eszközkategóriák konfigurálása

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>1\. lépés: Eszközkategóriák létrehozása az Azure Portal Intune panelén
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **eszköz kategóriák**elemet.
2. Az **Eszközkategóriák** lapon a **Létrehozás** elemmel hozhat létre új kategóriát.
3. Az **Eszközkategória létrehozása** panelen töltse ki az új kategória **Név** és **Leírás** mezőjét (utóbbi nem kötelező).
4. Amikor elkészült, válassza a **Létrehozás** gombot. Az új kategória megjelenik a kategóriák listájában.

Azure Active Directory (Azure AD) biztonsági csoportok létrehozásakor az eszközkategória nevét fogja használni a 2. lépésben.

### <a name="step-2-create-azure-active-directory-security-groups"></a>2\. lépés: Azure Active Directory biztonsági csoportok létrehozása
Ebben a lépésben az eszközkategória és az eszközkategória-név alapján dinamikus csoportokat fog létrehozni az Azure-portálon.

A folytatáshoz tekintse meg a [Speciális szabályok létrehozása attribútumok használatával](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) című témakört az Azure AD dokumentációjában.

Ezen szakasz információi alapján hozzon létre speciális szabállyal egy eszközcsoportot a **deviceCategory** attribútum segítségével. Például: **device.deviceCategory -eq** "*Azure Portalon lekért eszközkategória-név*".

Ha vannak konfigurált eszközcsoportok, amikor a felhasználók regisztrálják eszközüket, meg fog jelenni számukra az Ön által beállított kategóriák listája. A kategória kiválasztását és a regisztráció befejezését követően az eszköz a kiválasztott kategóriának megfelelő Active Directory biztonsági csoportba kerül.

### <a name="view-the-categories-of-devices-that-you-manage"></a>A felügyelt eszközök kategóriáinak megtekintése

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **minden eszköz**lehetőséget.

2. Az eszközlistában keresse meg az **Eszközkategória** oszlopot.

Ha nem látható az **eszköz kategóriája** oszlop, válassza az **oszlopok** > a **Kategória** > az **alkalmaz**lehetőséget.

### <a name="change-the-category-of-a-device"></a>Eszköz kategóriájának módosítása

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431), válassza az **eszközök** > **minden eszköz** lehetőséget, > Válassza ki a kívánt eszközt > a **Tulajdonságok**elemet.
2. A következő panelen a kijelölt eszköz **Eszközkategória** tulajdonságát átállíthatja a korábban konfigurált kategórianevek bármelyikére.

## <a name="after-you-configure-device-groups"></a>Az eszközcsoportok konfigurálása után

Ha az iOS/iPadOS és az Android rendszerű eszközök felhasználója regisztrálja az eszközét, ki kell választania egy kategóriát a konfigurált kategóriák listájából. A kategória kiválasztását és a regisztráció befejezését követően a rendszer a kiválasztott kategóriának megfelelő Intune-eszközcsoporthoz vagy Active Directory biztonsági csoporthoz adja az eszközüket.

Windows-felhasználóknak a kategória kiválasztásához a Céges portál webhelyet kell használniuk.

Az eszköz regisztrálása után felhasználói a platformtól függetlenül mindig elérhetik a portal.manage.microsoft.com webhelyet. Kérje meg a felhasználót, hogy nyissa meg a Céges portál webhelyet, és válassza a **Saját eszközök** lehetőséget. A felhasználó itt választhat egy regisztrált eszközt a lapon található listából, majd megadhat egy kategóriát.

A kategória kiválasztása után az eszköz automatikusan bekerül az Ön által létrehozott, a kategóriának megfelelő csoportba. Ha az eszköz már a kategóriák konfigurálása előtt regisztrálva lett, akkor a felhasználó értesítést kap az eszközről a Céges portál webhelyen. Ez lehetővé teszi a felhasználó számára, hogy kiválasszon egy kategóriát a következő alkalommal, amikor a Céges portál alkalmazást iOS/iPadOS vagy Android rendszeren érik el.

## <a name="further-information"></a>További információ
- Az Azure Portalon szerkesztheti az eszközkategóriákat, ekkor viszont manuálisan kell módosítania az Azure Active Directoryban az adott kategóriára hivatkozó biztonsági csoportokat.

- Ha töröl egy kategóriát, az ahhoz hozzárendelt eszközöknél a **Nincs hozzárendelve** kategórianév jelenik meg.
