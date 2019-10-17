---
title: Alkalmazás-alapú feltételes hozzáférés az Intune-nal
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan működik az alkalmazás-alapú feltételes hozzáférés az Intune-nal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d3cae06c3ce763fe8ca94bbed9bf35e8abef52c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502597"
---
# <a name="app-based-conditional-access-with-intune"></a>Alkalmazás-alapú feltételes hozzáférés az Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az [Intune alkalmazásvédelmi szabályzataival](../apps/app-protection-policy.md) védheti vállalati adatait az Intune-ban regisztrált eszközökön. Az alkalmazásvédelmi szabályzatokat emellett a munkatársak tulajdonában álló, az Intune-ban felügyeletre nem regisztrált eszközökön is alkalmazhatja. Bár ebben az esetben nem a cég felügyeli az eszközt, mégis fontos, hogy a vállalati adatok és erőforrások védve legyenek.

Az alkalmazás-alapú feltételes hozzáférés és az ügyfélalkalmazások kezelése biztonsági réteg hozzáadásával gondoskodhat arról, hogy csak az Intune app Protection-szabályzatokat támogató ügyfélalkalmazások férhessenek hozzá az Exchange Online-hoz és más Office 365-szolgáltatásokhoz.

> [!NOTE]
> A felügyelt alkalmazásra alkalmazásvédelmi szabályzatok vonatkoznak, és az Intune-nal felügyelhető.

Azzal, hogy csak a Microsoft Outlook alkalmazásnak engedélyezi az Exchange Online elérését, blokkolhatja az iOS és az Android beépített levelezőalkalmazásait. Ezenfelül blokkolhatja az Intune alkalmazásvédelmi szabályzattal el nem látott alkalmazások SharePoint Online-elérését is.

## <a name="prerequisites"></a>Előfeltételek
Az alkalmazás-alapú feltételes hozzáférési szabályzat létrehozása előtt a következőket kell tennie:

- **Enterprise Mobility + Security (EMS)** vagy **Prémium szintű Azure Active Directory- (AD-) előfizetés**
- EMS- vagy Azure AD-licenc a felhasználók számára

További információ: [Enterprise Mobility díjszabás](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) vagy [Azure Active Directory díjszabása](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Támogatott alkalmazások

Az alkalmazás-alapú feltételes hozzáférést támogató alkalmazások listája a [Azure Active Directory feltételes hozzáférés technikai útmutatója dokumentációban található.](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)

Az alkalmazás-alapú feltételes hozzáférés [is támogatja az üzletági (LOB) alkalmazásokat](app-modern-authentication-block.md), de ezeknek az alkalmazásoknak az [Office 365 modern hitelesítést](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)kell használniuk. 

## <a name="how-app-based-conditional-access-works"></a>Az alkalmazás-alapú feltételes hozzáférés működése

Ebben a példában a rendszergazda alkalmazta az alkalmazás-védelmi szabályzatokat az Outlook alkalmazásra, majd egy feltételes hozzáférési szabályt, amely hozzáadja az Outlook alkalmazást a vállalati e-mailek eléréséhez használható alkalmazások jóváhagyott listájához.

> [!NOTE]
> Az alábbi folyamatábra-struktúra más felügyelt alkalmazásokhoz is használható.

![Az alkalmazás-alapú feltételes hozzáférés folyamata ábrán látható](./media/app-based-conditional-access-intune/ca-intune-common-ways-3.png)

1. A felhasználó az Outlook alkalmazásból hitelesítést próbál végezni az Azure AD-val.

2. A felhasználó az első hitelesítési kísérletkor átirányítódik az alkalmazás-áruházba, ahonnan közvetítő alkalmazást kell telepítenie. Ez lehet az iOS-es Microsoft Authenticator vagy az androidos eszközökre készült Microsoft Intune vállalati portál.

   Ha egy felhasználó natív levelezőalkalmazást próbál használni, a rendszer az alkalmazásáruházba irányítja át, hogy telepíthesse az Outlookot.

3. A közvetítő alkalmazás települ az eszközre.

4. A közvetítő alkalmazás elindítja az Azure AD regisztrációs folyamatát, amely létrehoz egy eszköz-rekordot az Azure AD-ben. Ez nem ugyanaz, mint a mobileszköz-felügyeleti (MDM) beléptetési folyamat, de erre a rekordra azért van szükség, hogy a feltételes hozzáférési szabályzatok kényszerítve legyenek az eszközön.

5. A közvetítő alkalmazás ellenőrzi az alkalmazás identitását. Van egy biztonsági réteg, így a közvetítő alkalmazás ellenőrizheti, hogy az alkalmazás engedélyezve van-e a felhasználó általi használatra.

6. A közvetítő alkalmazás a felhasználó-hitelesítési folyamat keretében elküldi az alkalmazás ügyfél-azonosítóját az Azure AD-nek, amely ellenőrzi, hogy szerepel-e a szabályzat engedélyezési listáján.

7. Az Azure AD a szabályzat engedélyezési listája alapján engedélyezi a felhasználónak a hitelesítést és az alkalmazás használatát. Ha az alkalmazás nem szerepel a listán, az Azure AD megtagadja az alkalmazás elérését.

8. Az Outlook alkalmazás az Outlook felhőszolgáltatással kapcsolatba lépve kezdeményezi az Exchange Online-nal való kommunikációt.

9. Az Outlook felhőszolgáltatás az Azure AD-vel kommunikálva lekér egy Exchange Online-szolgáltatás-hozzáférési jogkivonatot a felhasználó részére.

10. Az Outlook alkalmazás az Exchange Online-nal kommunikálva lekéri a felhasználó céges e-mailjeit.

11. A céges e-mailek kézbesítődnek a felhasználó postafiókjába.

## <a name="next-steps"></a>További lépések
[Alkalmazás-alapú feltételes hozzáférési szabályzat létrehozása](app-based-conditional-access-intune-create.md)

[Modern hitelesítés nélküli alkalmazások blokkolása](app-modern-authentication-block.md)
