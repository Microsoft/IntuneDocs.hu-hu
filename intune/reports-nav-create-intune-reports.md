---
title: Az Intune-adattárház használata
titleSuffix: Microsoft Intune
description: Az Intune-adattárház használatával a vállalat mobilkörnyezetéről szóló jelentéseket hozhat létre.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0728fefc40bc82db7926faf282a69d0471c3a1ea
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59897136"
---
# <a name="use-the-microsoft-intune-data-warehouse"></a>A Microsoft Intune-adattárház használata

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Az Intune-adattárház használatával a vállalat mobilkörnyezetéről szóló jelentéseket hozhat létre. A jelentésekben például a következők szerepelhetnek:
-   Az Intune-ban regisztráló felhasználók trendje a licencvásárlások optimalizálásához
-   Az alkalmazások és az operációs rendszerek listázása verziók szerinti bontásban a mobileszközök állapotának ellenőrzéséhez
-   Regisztrációs és eszközmegfelelőségi trendek a szabályzatfrissítések zökkenőmentes bevezetéséhez

## <a name="data-warehouse-benefits"></a>Az adattárház előnyei

Az adattárház az Azure Portalnál több információt nyújt a mobilkörnyezettel kapcsolatban. Az Intune-adattárház segítségével a következőkhöz férhet hozzá:

  -  Intune-előzményadatok
  -  Napi szintű frissített adatok
  -  OData-szabványt használó adatmodell

> [!Note]
> Ha Ön egy közös felügyelt mobil Eszközkezelés (MDM) a System Center Configuration Manager és a Microsoft Intune, kell lekérni az adatokat a Configuration Manager alkalmazásból. Az Intune-adattárház csak az Intune-adatokat tartalmazza. Egy Configuration Manager Power BI-irányítópult az egyéni jelentésekhez használhatja. További információ: „[A Power BI-megoldássablon bejelentése a System Center Configuration Managerhez]( https://powerbi.microsoft.com/blog/sccm-solution-template)”, valamint „[Power BI-tartalom a Dynamics 365-höz](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page).”

> [!Important]  
> Most már használható az Intune Adattárház v1.0-ás verziója az  `api-version=v1.0` lekérdezésparaméter megadásával. Az Adattárház gyűjteményeinek frissítései hozzáadó jellegűek, és nem okoznak fennakadást a meglévő forgatókönyvekben.<br><br>
> A bétaverzió használatával kipróbálhatja az adattárház legújabb funkcióit. A bétaverzió használatához URL-címének az  `api-version=beta` lekérdezési paraméterrel kell rendelkeznie. A bétaverzió olyan funkciókat is kínál, amelyek támogatott szolgáltatásként még érhetőek el általánosan. Amikor az Intune új funkciókkal bővíti a szolgáltatást, előfordulhat, hogy a bétaverzió viselkedése és az adategyezmény megváltozik. Frissítések esetén a bétaverziót használó egyéni kódok vagy jelentéskészítő eszközök működésében hibák jelentkezhetnek.

## <a name="next-steps"></a>További lépések

- Kapcsolódjon az adattárházhoz a Power BI használatával, és készítsen információs jelentéseket. További információt a [Csatlakozás az Intune-adattárházhoz a Power BI segítségével](reports-proc-get-a-link-powerbi.md)című témakörben talál.
- A hivatkozást felhasználva készítsen egyéni jelentéseket a Power BI használatával. Ehhez a [Jelentés készítése az OData-adatcsatornából a Power BI használatával](reports-proc-create-with-odata.md) című témakörben talál útmutatót.
- Részletes tájékoztatást nyújt az Intune-adattárház API adatmodell, és az entitások közötti kapcsolatok<!-- , and an example of creating a custom client to retrieve data,--> Lásd: [Intune-adattárház API](reports-nav-intune-data-warehouse.md).
