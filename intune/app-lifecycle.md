---
title: Az alkalmazások Microsoft Intune-beli életciklusának áttekintése
description: Ismerkedjen meg a felügyelt alkalmazások Microsoft Intune-beli életciklusával. Az alkalmazás-életciklus az alkalmazások hozzáadását, üzembe helyezését, konfigurálását, védelmét és eltávolítását foglalja magában.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7e271151afa90680cc3ab46db1b419ec4a32d42
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836268"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Az alkalmazások Microsoft Intune-beli életciklusának áttekintése

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Az alkalmazások Microsoft Intune-beli életciklusa az alkalmazás hozzáadásával kezdődik, majd végighalad a további fázisokon egészen az alkalmazás eltávolításáig. Az Alkalmazáskezelés az Intune-ban – első lépések szükséges akkor fázisok megismerése.

![Az alkalmazás-életciklus - hozzáadása, telepítése, konfigurálása, védelme és kivonása. ](./media/app-lifecycle.png "az Intune alkalmazás-életciklus")

## <a name="add"></a>Hozzáadás

Az alkalmazások központi telepítésének első lépéseként fel kell vennie az Intune-ba a felügyelni és hozzárendelni kívánt alkalmazásokat. Jóllehet számos különböző típusú alkalmazással dolgozhat, az alapvető eljárás mindegyiknél ugyanaz. Az Intune-nal hozzáadhat különböző alkalmazástípust, többek között a fejlesztésű (az üzleti), a tárolót, a beépített alkalmazások és az alkalmazások származó alkalmazások a weben. Az egyes alkalmazástípusokról az [Alkalmazás felvétele a Microsoft Intune-ba](apps-add.md) című témakörben talál további információt. 

## <a name="deploy"></a>Üzembe helyezés

Miután felvette az alkalmazást az Intune-ba, [azt felhasználókhoz és felügyelt eszközökhöz rendelheti hozzá](apps-deploy.md). Az Intune megkönnyíti ezt a folyamatot, és az alkalmazás telepítése után is [sikeres figyelése](apps-monitor.md) az üzembe helyezés az Azure Portalon az Intune-ból. Egyes alkalmazás-áruházakban, mint az [Apple](vpp-apps-ios.md) vagy a [Windows](windows-store-for-business.md), nagy tételben is vásárolhat alkalmazáslicenceket cége számára. Az Intune képes szinkronizálni az adatokat ezekkel az áruházakkal, így Ön közvetlenül az Intune felügyeleti konzoljából hajthatja végre a központi telepítést és követheti nyomon a licenchasználatot.

## <a name="configure"></a>Konfigurálás

Az alkalmazások életciklusa során általában az alkalmazás több új verziója is megjelenik. Az Intune számos eszközt kínál a központilag telepített alkalmazások [verziófrissítésére](apps-add.md). Ezen túlmenően bizonyos alkalmazásokhoz további funkciók is konfigurálhatók, például:
- Az [iOS-alkalmazáskonfigurációs szabályzatok](app-configuration-policies-use-ios.md) segítségével meghatározhatja, hogy a kompatibilis iOS-alkalmazások futása esetén mely beállítások lépjenek érvénybe. Például egyes alkalmazásokhoz szükség lehet bizonyos márkajelzési beállításokra, vagy a célkiszolgáló nevére, amelyhez csatlakoznia kell.
- A [felügyeltböngésző-szabályzatok](app-configuration-managed-browser.md) segítségével konfigurálhatja az Intune által felügyelt, az eszközök alapértelmezett böngészőjét felváltó böngésző beállításait, illetve korlátozhatja, hogy a felhasználók milyen weboldalakat nyithatnak meg.

## <a name="protect"></a>védelme

Az Intune számos módszert kínál az alkalmazásokban tárolt adatok védelmére. A legfontosabb megoldások a következők:
- [Feltételes hozzáférés](conditional-access.md), amely az Ön által megadott feltételek alapján szabályozza az e-mail és egyéb szolgáltatások elérését. Ilyen feltétel lehet az eszköz típusa, vagy az, hogy megfelel-e a központilag telepített [eszközmegfelelőségi szabályzatnak](device-compliance.md).
- [Alkalmazásvédelmi szabályzatok](app-protection-policy.md), amelyek az egyes alkalmazásokkal együttműködve nyújtanak védelmet az általuk használt céges adatok számára. Letilthatja például az adatok másolását a nem felügyelt és a felügyelt alkalmazások között, illetve megakadályozhatja az alkalmazások futtatását függetlenített vagy feltört eszközökön.

## <a name="retire"></a>Kivonás

Az idő múlásával a telepített alkalmazások elavulttá válnak, így el kell őket távolítani. Az Intune segítségével egyszerűen [kivonhatja a kívánt alkalmazásokat a szolgáltatásból](device-management.md).

## <a name="next-steps"></a>További lépések

- Tudnivalók: [Alkalmazáskezelés a Microsoft Intune-ban](app-management.md)
