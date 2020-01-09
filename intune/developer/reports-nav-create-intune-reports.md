---
title: Az Intune-adattárház használata
titleSuffix: Microsoft Intune
description: Az Intune-adattárház használatával a vállalat mobilkörnyezetéről szóló jelentéseket hozhat létre.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 58c4db1f4c778050bc91bde79494742e018f5329
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547904"
---
# <a name="use-the-microsoft-intune-data-warehouse"></a>A Microsoft Intune Data Warehouse használata

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune-adattárház használatával a vállalat mobilkörnyezetéről szóló jelentéseket hozhat létre. A jelentésekben például a következők szerepelhetnek:
- Az Intune-ban regisztráló felhasználók trendje a licencvásárlások optimalizálásához
- Az alkalmazások és az operációs rendszerek listázása verziók szerinti bontásban a mobileszközök állapotának ellenőrzéséhez
- Regisztrációs és eszközmegfelelőségi trendek a szabályzatfrissítések zökkenőmentes bevezetéséhez

## <a name="data-warehouse-benefits"></a>Az adatraktár előnyei

Az adattárház az Azure Portalnál több információt nyújt a mobilkörnyezettel kapcsolatban. Az Intune-adattárház segítségével a következőkhöz férhet hozzá:

- Intune-előzményadatok
- Napi szintű frissített adatok
- OData-szabványt használó adatmodell

> [!Note]
> Ha közösen felügyelt mobileszköz-kezelést (MDM) használ a Microsoft Endpoint Configuration Manager és Microsoft Intune segítségével, az adatait Configuration Manager kell lekérnie. Az Intune-adattárház csak az Intune-adatokat tartalmazza. Az egyéni jelentésekhez Configuration Manager Power BI irányítópultot is használhat. További információ: "[a Configuration Manager Power bi megoldás sablonjának bejelentése](https://powerbi.microsoft.com/blog/sccm-solution-template)" és "[Power bi tartalom a Dynamics 365](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page)-hez".

> [!Important]  
> Most már használható az Intune Adattárház v1.0-ás verziója az  `api-version=v1.0` lekérdezésparaméter megadásával. Az Adattárház gyűjteményeinek frissítései hozzáadó jellegűek, és nem okoznak fennakadást a meglévő forgatókönyvekben.<br><br>
> A bétaverzió segítségével az adattárház legújabb funkcióit próbálhatja ki. A bétaverzió használatához URL-címének az  `api-version=beta` lekérdezési paraméterrel kell rendelkeznie. A bétaverzió olyan funkciókat is kínál, amelyek támogatott szolgáltatásként még érhetőek el általánosan. Amikor az Intune új funkciókkal bővíti a szolgáltatást, előfordulhat, hogy a bétaverzió viselkedése és az adategyezmény megváltozik. Frissítések esetén a bétaverziót használó egyéni kódok vagy jelentéskészítő eszközök működésében hibák jelentkezhetnek.

## <a name="next-steps"></a>További lépések

- Kapcsolódjon az adattárházhoz a Power BI használatával, és készítsen információs jelentéseket. További információt a [Csatlakozás az Intune-adattárházhoz a Power BI segítségével](reports-proc-get-a-link-powerbi.md)című témakörben talál.
- A hivatkozást felhasználva készítsen egyéni jelentéseket a Power BI használatával. Ehhez a [Jelentés készítése az OData-adatcsatornából a Power BI használatával](reports-proc-create-with-odata.md) című témakörben talál útmutatót.
- További információ az Intune-adattárház API-ról, az adatmodellről és az entitások közötti kapcsolatokról<!-- , and an example of creating a custom client to retrieve data,--> Lásd: [az Intune-adattárház API](reports-nav-intune-data-warehouse.md)-ját.
