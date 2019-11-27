---
title: Feltételes hozzáférés Microsoft Intune
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan határozhatja meg, hogy a felhasználók, eszközök és alkalmazások milyen feltételekkel férhetnek hozzá a vállalati erőforrásokhoz Microsoft Intuneban.
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
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188279"
---
# <a name="learn-about-conditional-access-and-intune"></a>Tudnivalók a feltételes hozzáférésről és az Intune-ról

A feltételes hozzáférés segítségével szabályozhatja az e-mailekhez és a vállalati erőforrásokhoz való kapcsolódáshoz használható eszközöket és alkalmazásokat. 

A Enterprise Mobility + Security (EMS) nem önálló termék. Ez egy olyan megoldás, amely az EMS részét képező összes szolgáltatáson és terméken részt vesz. A feltételes hozzáférés részletes hozzáférés-vezérlést biztosít a vállalati adatok biztonságának megőrzéséhez, miközben a felhasználók számára lehetővé teszi, hogy bármely eszközről és bármely helyről elvégezzék a legjobb munkát.

Olyan feltételeket adhat meg, amelyek a vállalati adatokhoz való hozzáférést helyszín, eszköz, felhasználói állapot vagy az alkalmazás bizalmassági szintje alapján korlátozzák.

> [!NOTE]
> A feltételes hozzáférési funkciók kiterjednek az [Office 365-szolgáltatásokra](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access) is.

![Feltételes hozzáférési diagram](./media/conditional-access/ca-diagram-1.png)

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

    - Saját eszközök használata (BYOD)

- **Alkalmazás-alapú feltételes hozzáférés**

## <a name="next-steps"></a>További lépések

[A feltételes hozzáférés használatának gyakori módjai az Intune-nal](conditional-access-intune-common-ways-use.md)
