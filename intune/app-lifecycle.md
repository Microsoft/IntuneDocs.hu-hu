---
title: Az alkalmazások Microsoft Intune-beli életciklusának áttekintése
description: Ismerkedjen meg a felügyelt alkalmazások Microsoft Intune-beli életciklusával. Az alkalmazás-életciklus az alkalmazások hozzáadását, üzembe helyezését, konfigurálását, védelmét és eltávolítását foglalja magában.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19c364bda4728880b84cb1a17593bcbd38aa00bc
ms.sourcegitcommit: 76d59edfd5900ce33c64470ae604eb3db016c8ca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/22/2019
ms.locfileid: "71238938"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Az alkalmazások Microsoft Intune-beli életciklusának áttekintése

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Az alkalmazások Microsoft Intune-beli életciklusa az alkalmazás hozzáadásával kezdődik, majd végighalad a további fázisokon egészen az alkalmazás eltávolításáig. Ezeknek a fázisoknak a megismeréséhez az Intune-ban az alkalmazások felügyeletének megkezdéséhez szükséges részleteket kell megadnia.

![Az alkalmazások életciklusa – Hozzáadás, üzembe helyezés, konfigurálás, védelem és] kivonás. (./media/app-lifecycle.png "az Intune-alkalmazás életciklusa")

## <a name="add"></a>Hozzáadás

Az alkalmazások központi telepítésének első lépéseként fel kell vennie az Intune-ba a felügyelni és hozzárendelni kívánt alkalmazásokat. Jóllehet számos különböző típusú alkalmazással dolgozhat, az alapvető eljárás mindegyiknél ugyanaz. Az Intune-nal különböző típusú alkalmazásokat adhat hozzá, beleértve a házon belüli (üzletági), az áruházból származó alkalmazásokat, a beépített alkalmazásokat és a webes alkalmazásokat. Az egyes alkalmazástípusokról az [Alkalmazás felvétele a Microsoft Intune-ba](apps-add.md) című témakörben talál további információt. 

## <a name="deploy"></a>Üzembe helyezés

Miután felvette az alkalmazást az Intune-ba, [azt felhasználókhoz és felügyelt eszközökhöz rendelheti hozzá](apps-deploy.md). Az Intune megkönnyíti ezt a folyamatot, és az alkalmazás üzembe helyezése után nyomon követheti az üzembe helyezés [sikerességét](apps-monitor.md) az Intune-ban a Azure Portalon belül. Egyes alkalmazás-áruházakban, mint az [Apple](vpp-apps-ios.md) vagy a [Windows](windows-store-for-business.md), nagy tételben is vásárolhat alkalmazáslicenceket cége számára. Az Intune képes szinkronizálni az adatokat ezekkel az áruházakkal, így Ön közvetlenül az Intune felügyeleti konzoljából hajthatja végre a központi telepítést és követheti nyomon a licenchasználatot.

## <a name="configure"></a>Konfigurálás

Az alkalmazások életciklusa során általában az alkalmazás több új verziója is megjelenik. Az Intune számos eszközt kínál a központilag telepített alkalmazások [verziófrissítésére](apps-add.md). Ezen túlmenően bizonyos alkalmazásokhoz további funkciók is konfigurálhatók, például:
- Az [iOS-alkalmazáskonfigurációs szabályzatok](app-configuration-policies-use-ios.md) segítségével meghatározhatja, hogy a kompatibilis iOS-alkalmazások futása esetén mely beállítások lépjenek érvénybe. Például egyes alkalmazásokhoz szükség lehet bizonyos márkajelzési beállításokra, vagy a célkiszolgáló nevére, amelyhez csatlakoznia kell.
- A [felügyeltböngésző-szabályzatok](app-configuration-managed-browser.md) segítségével konfigurálhatja az Intune által felügyelt, az eszközök alapértelmezett böngészőjét felváltó böngésző beállításait, illetve korlátozhatja, hogy a felhasználók milyen weboldalakat nyithatnak meg.

## <a name="protect"></a>védelme

Az Intune számos módszert kínál az alkalmazásokban tárolt adatok védelmére. A legfontosabb megoldások a következők:
- [Feltételes hozzáférés](conditional-access.md), amely az Ön által megadott feltételek alapján szabályozza az e-mailekhez és egyéb szolgáltatásokhoz való hozzáférést. Ilyen feltétel lehet az eszköz típusa, vagy az, hogy megfelel-e a központilag telepített [eszközmegfelelőségi szabályzatnak](device-compliance.md).
- [Alkalmazásvédelmi szabályzatok](app-protection-policy.md), amelyek az egyes alkalmazásokkal együttműködve nyújtanak védelmet az általuk használt céges adatok számára. Letilthatja például az adatok másolását a nem felügyelt és a felügyelt alkalmazások között, illetve megakadályozhatja az alkalmazások futtatását függetlenített vagy feltört eszközökön.

## <a name="retire"></a>Kivonás

Az idő múlásával a telepített alkalmazások elavulttá válnak, így el kell őket távolítani. Az Intune segítségével egyszerűen [kivonhatja a kívánt alkalmazásokat a szolgáltatásból](device-management.md).

## <a name="next-steps"></a>További lépések

- Tudnivalók: [Alkalmazáskezelés a Microsoft Intune-ban](app-management.md)
