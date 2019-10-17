---
title: Az adattárház adatmodellje
titleSuffix: Microsoft Intune
description: A Microsoft Intune-adattárház napi adatgyűjtéssel dokumentálja a folyamatosan változó mobilkörnyezet előzményeit.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a0d2e263b651d0f39dc4a8b9f27187da519b3d60
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490347"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Adattárház adatmodell Microsoft Intune

Az Intune-adattárház napi adatgyűjtéssel dokumentálja a mobileszközök folyamatosan változó környezetének előzményeit. A nézet az egymással összefüggő entitások időbeli képe.

## <a name="entities-entity-sets"></a>Entitások: Entitáskészletek

Az adattárház a következő magas szintű területeken tünteti fel az adatokat:

- Alkalmazásvédelem által engedélyezett alkalmazások és használat
- Regisztrált eszközök, tulajdontárgyak és készlet
- Alkalmazások és szoftverleltár
- Eszközkonfigurációs és megfelelőségi szabályzatok

Ezek a területek tartalmazzák az Intune-környezet számára jelentős entitásokat. Az entitáscsoportokról a következő témakörökben talál részletes információt:

- [Alkalmazás](../reports-ref-application.md)
- [Dátum](reports-ref-date.md)
- [Eszközök](reports-ref-devices.md)
- [Intune felügyeleti bővítmény](reports-ref-intunemanagementextension.md)
- [Szabályzat](reports-ref-policy.md)
- [Mobilalkalmazás-felügyelet (MAM)](../apps/app-management.md)
- [Felhasználó](reports-ref-user.md)
- [Jelenlegi felhasználó](../reports-ref-current-user.md)
- [Felhasználók és eszközök társítása](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>Kapcsolatok: Csillagséma-modell

Az adattárház olyan kapcsolatokba rendezi az entitásokat, amelyek fontosak lehetnek a feltenni kívánt kérdések szempontjából. Például áttekintheti egy belső fejlesztésű Android-alkalmazás telepítéseinek számát. Az adattárház szerkezete lehetővé teszi a mobil környezet alapos megismerését. Az olyan elemzési eszközök pedig, mint a Microsoft Power BI, képi megjelenítéseket és dinamikus irányítópultokat hozhatnak létre az adattárház adatmodellje alapján.

Az entitások és a kapcsolatok a csillagséma-modell alapján rendeződnek. A csillagséma az idő dimenziójában kapcsolja össze a tényadatokat. Ebben a modellben a *tényadat* mennyiségi mérőszám, mint például az eszközök száma, az alkalmazások száma, vagy a regisztráció ideje. A ténytáblák nagy mennyiségű adatot tárolnak. Néha igen nagy méretet is elérhetnek, ezért általában 30 napra korlátozzák az információt. A *dimenzió* összefüggésbe helyezi a tényeket. A tény azt jelzi, hogy mi történt, a dimenziók arra mutatnak rá, hogy kivel. A dimenziótáblák, mint például a **Felhasználó** tábla, kisebbek a ténytábláknál, és hosszabb ideig tárolhatják az adatokat. 

A rugalmasságra és adatelemzésre optimalizált csillagséma-modell segít összeállítani a folyamatosan változó mobilkörnyezet megértéséhez szükséges jelentéseket.

## <a name="time-daily-snapshots"></a>Idő: Napi pillanatképek

Az adattárház az Intune alsóbb rétege. Az Intune az egyezményes világidő (UTC) szerint éjfélkor napi pillanatképet készít, és ezt a pillanatképet az adattárházban tárolja. A pillanatképek tárolási ideje ténytábláról ténytáblára változik. Némelyiket hét napig, némelyiket 30 napig, vagy akár tovább is tárolja a rendszer.

## <a name="next-steps"></a>További lépések

- Annak részletesebb megismeréséhez, hogy az adattárház hogyan követi nyomon egy felhasználó Intune-beli élettartamát, lásd: [A felhasználói élettartam reprezentációja az Intune-adattárházban](reports-ref-user-timeline.md).
- Az adattárházak használatáról az [első adattárház létrehozását](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse) ismertető szakaszban talál további információt.
- A Power BI és az adattárház használatának részletesebb megismeréséhez lásd: [Új Power BI-jelentés létrehozása adatkészlet importálásával ](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/). 
