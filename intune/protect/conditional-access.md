---
title: Feltételes hozzáférés Microsoft Intune
titleSuffix: Microsoft Intune
description: Útmutató a felhasználókra, eszközökre és alkalmazásokra vonatkozó feltételek meghatározásához a vállalati adatok eléréséhez a Microsoft Intune-ban.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb9dd31c87d27ec7885d25269988cfd968e81e08
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504559"
---
# <a name="learn-about-conditional-access-and-intune"></a>Tudnivalók a feltételes hozzáférésről és az Intune-ról

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A feltételes hozzáférés arra utal, hogy miként szabályozható az e-mailekhez és a vállalati erőforrásokhoz való kapcsolódásra jogosult eszközök és alkalmazások. Ebben a témakörben megismerheti az eszköz-és az alkalmazás-alapú feltételes hozzáférést, valamint a feltételes hozzáférés Intune-nal való használatának gyakori forgatókönyveit.

Az Enterprise Mobility + Security (EMS) feltételes hozzáférése nem önálló termék, hanem olyan megoldás, amely az EMS részét képező összes szolgáltatásban és a termékben megtalálható. A részletes hozzáférés-vezérlést biztosít a vállalati adatok védelméhez, miközben olyan felhasználói felületet nyújt, amely lehetővé teszi, hogy bármely eszközről, bárhonnan a lehető leghatékonyabban dolgozhassanak a felhasználók.

Olyan feltételeket adhat meg, amelyek a vállalati adatokhoz való hozzáférést helyszín, eszköz, felhasználói állapot vagy az alkalmazás bizalmassági szintje alapján korlátozzák.

> [!NOTE] 
> A feltételes hozzáférési funkciók kiterjednek az [Office 365-szolgáltatásokra](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access) is.

![Feltételes hozzáférés építészeti diagramja](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Feltételes hozzáférés használata az Intune-nal

A feltételes hozzáférés egy prémium szintű Azure Active Directory-licenc részét képező Azure Active Directory képesség. Az Intune ezt a lehetőséget mobileszköz-megfelelőségi és mobilalkalmazás-felügyeleti megoldások hozzáadásával bővíti tovább. 

![Az Intune és a feltételes hozzáférés az EMS használatakor](./media/conditional-access/intune-with-ca-1.png)

A feltételes hozzáférés Intune-nal való használatának módjai:

- **Eszköz alapú feltételes hozzáférés**

  - Feltételes hozzáférés a helyszíni Exchange-hez

  - A hálózati hozzáférés-vezérlésen alapuló feltételes hozzáférés

  - Az eszköz kockázatán alapuló feltételes hozzáférés

  - Feltételes hozzáférés Windows rendszerű számítógépekhez

    - Céges tulajdonú eszközök

    - Saját eszközök használata (Bring Your Own Device, BYOD)

- **Alkalmazás-alapú feltételes hozzáférés**

## <a name="next-steps"></a>További lépések

[A feltételes hozzáférés használatának gyakori módjai az Intune-nal](conditional-access-intune-common-ways-use.md)
