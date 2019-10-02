---
title: Intune-adattárház API
titleSuffix: Microsoft Intune
description: Az Intune-adattárház API használatával a vállalat mobilkörnyezetéről szóló jelentéseket hozhat létre.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0345bf2246a7bf579b4b46d118d7889442001c30
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730207"
---
# <a name="microsoft-intune-data-warehouse-api"></a>Adattárház-API Microsoft Intune

Az Intune-adattárház API géppel olvasható formában nyújt hozzáférést az Intune-beli adatokhoz, hogy kedvenc elemző eszközével feldolgozhassa azokat. Az API használatával összeállíthatja a cége mobilkörnyezetéről szóló jelentéseket. Az API az OData protokollt használja, amely a szabványos minták szerint kezeli az alábbiakat:

- Kérés- és válaszfejlécek
- Állapotkódok
- HTTP-metódusok
- URL-címre vonatkozó konvenciók
- Adathordozó-típusok
- Adattartalom-formátumok
- Lekérdezési lehetőségek

Az OData (Open Data Protocol – nyílt adatprotokoll) az OASIS (Szervezet a strukturált információs szabványok fejlesztéséért) szabványa, amely ajánlott eljárásokat határoz meg a RESTful API-k kialakításához és használatához. Az Intune-adattárház az OData 4.0-s verzióját használja.

Ez a referenciaszakasz áttekintést nyújt az Intune-adattárház adatmodelljének végpontjairól, támogatott HTTP-metódusairól, adattartalmainak visszaadási formátumairól és dokumentációjáról.

> [!Important]  
> A bétaverzió használatával kipróbálhatja az adattárház legújabb funkcióit. A bétaverzió használatához URL-címének az `api-version=beta` lekérdezési paraméterrel kell rendelkeznie. A bétaverzió olyan funkciókat is kínál, amelyek támogatott szolgáltatásként még érhetőek el általánosan. Amikor az Intune új funkciókkal bővíti a szolgáltatást, előfordulhat, hogy a bétaverzió viselkedése és az adategyezmény megváltozik. Frissítések esetén a bétaverziót használó egyéni kódok vagy jelentéskészítő eszközök működésében hibák jelentkezhetnek. <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

## <a name="odata-custom-client"></a>Egyéni OData-ügyfél

Az Intune-adatárház adatmodellje RESTful végpontokon keresztül érhető el. Ahhoz, hogy hozzáférjen az adatokhoz, az ügyfélnek az OAuth 2.0 protokollt használva igazolnia kell, hogy jogosult az Azure Active Directory (Azure AD) használatára. Ehhez először be kell állítani egy webalkalmazást és egy ügyfelet az Azure-ban, és meg kell adni az ügyfélnek a megfelelő jogosultságokat. A helyi ügyfél megkapja az engedélyt, és kommunikálhat az Adattárház-végpontokkal.

További információért lásd az [Adatok beolvasása az adattárház API-ból REST-ügyféllel](reports-proc-data-rest.md) című cikket.

> [!Note]  
> Kódpéldákat a [GitHub Intune-adattárház tárházban](https://github.com/Microsoft/Intune-Data-Warehouse) találhat a GitHubon.

## <a name="interacting-with-the-api"></a>Az API használata

Az API használatához Azure AD-hitelesítésre van szükség. Az Azure AD az OAuth 2.0-s verzióját használja. A hitelesítés után egy HTTP GET művelet végrehajtásával és a közzétett entitásgyűjteményekhez kapcsolódva hozzáférhet az API adataihoz. További részletek:

- [Hitelesítés](../reports-api-url.md)
- [Az API URL-címének szerkezete](../reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Az Intune-adattárház adatmodellje

Az OData olyan absztrakt adatmodellt és protokollt határoz meg, amely minden ügyfél számára minden adatforrás által közzétett információt hozzáférhetővé tesz. Az adatmodell dokumentációs témaköre magyarázatot nyújt az Intune-adattárház adatmodelljének névtereiről, entitásairól és visszaadott objektumairól. További tudnivalókért lásd: [Az adattárház adatmodellje](reports-ref-data-model.md).

## <a name="next-steps"></a>További lépések

Az Azure AD használatáról további információt kaphat a [Hitelesítési forgatókönyvek az Azure AD-ban](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) című témakörben.

OData-val kapcsolatos forrásokat az [odata.org](https://www.odata.org) webhelyen talál.
  
Az OData 4.0-ás verziójának szabványa az [OData 4.0-ás verzió] (https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  
