---
title: Az alkalmazások Microsoft Intune-beli életciklusának áttekintése
description: Ismerkedjen meg a felügyelt alkalmazások Microsoft Intune-beli életciklusával. Az alkalmazás-életciklus az alkalmazások hozzáadását, üzembe helyezését, konfigurálását, védelmét és eltávolítását foglalja magában.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 569906cea8467d568d302f4e44b26c3394213b62
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414967"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Az alkalmazások Microsoft Intune-beli életciklusának áttekintése

Az alkalmazások Microsoft Intune-beli életciklusa az alkalmazás hozzáadásával kezdődik, majd végighalad a további fázisokon egészen az alkalmazás eltávolításáig. Ezeknek a fázisoknak a megismeréséhez az Intune-ban az alkalmazások felügyeletének megkezdéséhez szükséges részleteket kell megadnia.

![Az alkalmazások életciklusa – Hozzáadás, üzembe helyezés, konfigurálás, védelem és kivonás.](./media/app-lifecycle/app-lifecycle.png "az Intune-alkalmazás életciklusa")

## <a name="add"></a>Hozzáadás

Az alkalmazások központi telepítésének első lépéseként fel kell vennie az Intune-ba a felügyelni és hozzárendelni kívánt alkalmazásokat. Jóllehet számos különböző típusú alkalmazással dolgozhat, az alapvető eljárás mindegyiknél ugyanaz. Az Intune-nal különböző típusú alkalmazásokat adhat hozzá, beleértve a házon belüli (üzletági), az áruházból származó alkalmazásokat, a beépített alkalmazásokat és a webes alkalmazásokat. Az egyes alkalmazástípusokról az [Alkalmazás felvétele a Microsoft Intune-ba](apps-add.md) című témakörben talál további információt.

## <a name="deploy"></a>telepítése Telepítse a

Miután felvette az alkalmazást az Intune-ba, [azt felhasználókhoz és felügyelt eszközökhöz rendelheti hozzá](apps-deploy.md). Az Intune megkönnyíti ezt a folyamatot, és az alkalmazás üzembe helyezése után nyomon követheti az üzembe helyezés [sikerességét](apps-monitor.md) az Intune-ban a Azure Portalon belül. Egyes alkalmazás-áruházakban, mint az [Apple](vpp-apps-ios.md) vagy a [Windows](windows-store-for-business.md), nagy tételben is vásárolhat alkalmazáslicenceket cége számára. Az Intune képes szinkronizálni az adatokat ezekkel az áruházakkal, így Ön közvetlenül az Intune felügyeleti konzoljából hajthatja végre a központi telepítést és követheti nyomon a licenchasználatot.

## <a name="configure"></a>Konfigurálás

Az alkalmazások életciklusa során általában az alkalmazás több új verziója is megjelenik. Az Intune számos eszközt kínál a központilag telepített alkalmazások [verziófrissítésére](apps-add.md). Ezen túlmenően bizonyos alkalmazásokhoz további funkciók is konfigurálhatók, például:

- az [iOS-alkalmazás konfigurációs házirendjei](app-configuration-policies-use-ios.md) az alkalmazás futtatásakor használt kompatibilis iOS/iPadOS alkalmazások beállításait biztosítják. Például egyes alkalmazásokhoz szükség lehet bizonyos márkajelzési beállításokra, vagy a célkiszolgáló nevére, amelyhez csatlakoznia kell.
- A [Managed Browser-házirendek](app-configuration-managed-browser.md) segítségével konfigurálhatja a [Microsoft Edge](~/apps/apps-supported-intune-apps.md#microsoft-apps)beállításait, amely lecseréli az alapértelmezett böngészőt, és lehetővé teszi a felhasználók által felkereshető webhelyek korlátozását.

## <a name="protect"></a>Védelem

Az Intune számos módszert kínál az alkalmazásokban tárolt adatok védelmére. A legfontosabb megoldások a következők:

- [Feltételes hozzáférés](../protect/conditional-access.md), amely az Ön által megadott feltételek alapján szabályozza az e-mailekhez és egyéb szolgáltatásokhoz való hozzáférést. Ilyen feltétel lehet az eszköz típusa, vagy az, hogy megfelel-e a központilag telepített [eszközmegfelelőségi szabályzatnak](../protect/device-compliance-get-started.md).
- [Alkalmazásvédelmi szabályzatok](app-protection-policy.md), amelyek az egyes alkalmazásokkal együttműködve nyújtanak védelmet az általuk használt céges adatok számára. Letilthatja például az adatok másolását a nem felügyelt és a felügyelt alkalmazások között, illetve megakadályozhatja az alkalmazások futtatását függetlenített vagy feltört eszközökön.

## <a name="retire"></a>Kivonás

Az idő múlásával a telepített alkalmazások elavulttá válnak, így el kell őket távolítani. Az Intune segítségével egyszerűen [kivonhatja a kívánt alkalmazásokat a szolgáltatásból](../remote-actions/device-management.md).

## <a name="next-steps"></a>További lépések

- Tudnivalók: [Alkalmazáskezelés a Microsoft Intune-ban](app-management.md)
