---
title: Modern hitelesítés nélküli alkalmazások blokkolása az Intune-ban
titleSuffix: Microsoft Intune
description: Ismerkedjen meg az alkalmazásokkal és a modern hitelesítéssel (ADAL) Microsoft Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8f28663c84ddc9f9b6ebd1a4e0ef60c8485ee02
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729879"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Modern hitelesítést nem használó alkalmazások blokkolása (ADAL)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az alkalmazás-alapú feltételes hozzáférés az App Protection-szabályzatokkal a [modern hitelesítést](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)használó alkalmazásokra támaszkodik, amely a OAuth2 implementációja. A legtöbb aktuális Office mobil-és asztali alkalmazás modern hitelesítést használ. Vannak azonban olyan harmadik féltől származó alkalmazások és régebbi Office-alkalmazások, amelyek más hitelesítési módszereket használnak, például az alapszintű hitelesítéshez és az űrlapalapú hitelesítéshez.

## <a name="block-access-to-apps"></a>Alkalmazások elérésének letiltása

A modern hitelesítést nem használó alkalmazásokhoz való hozzáférés blokkolásához használja az Intune app Protection-szabályzatokat a feltételek elérésének megvalósításához. További információ: [app-based feltételes hozzáférés az Intune](app-based-conditional-access-intune.md)-nal.

## <a name="additional-information"></a>További információ

Az Azure AD feltételes hozzáférésével kapcsolatos további információkért tekintse meg a következő témaköröket:
- [Mi a feltételes hozzáférés a Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Az alkalmazás-alapú feltételes hozzáférés működése](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [A SharePoint Online és az Exchange Online beállítása Azure Active Directory feltételes hozzáféréshez](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>További lépések

- [Alkalmazás-alapú feltételes hozzáférés az Intune-nal](app-based-conditional-access-intune.md)
