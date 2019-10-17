---
title: Korábbi Intune PC-ügyfél és Intune az Azure-ban
description: Szempontok az Azure-beli Intune használatához cége Windows-eszközeinek felügyeletéhez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 1f104923-12df-453c-9c20-942ef65a0945
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ab1be3d34d52e824d1ff06124e28206fb7b07a1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510185"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune az Azure-konzolon és a régi Intune számítógép-ügyfél

Az Intune egy Azure-alapú SaaS Application Service-architektúrát használ. Az Azure jelentős fejlesztéseket nyújt a méretezés, a kapacitás és a teljesítmény terén. Ez fejlett Intune-rendszergazdai élményt és optimalizált munkafolyamatokat kínál a Azure Portalban. 

Ha az Azure-beli Intune-t használja cége Windows-eszközeihez, vegye figyelembe a következő szempontokat:

## <a name="manage-windows-10-devices-by-using-mdm"></a>Windows 10-eszközök felügyelete az MDM segítségével

Azt javasoljuk, hogy a [Windows 10-eszközök felügyeletéhez a mobileszköz-felügyeletet (MDM) válassza](../configuration/device-restrictions-windows-10.md) az örökölt Intune szoftverügyfél helyett. Az Azure Portal-beli Intune lehetőséget ad a Windows 10 MDM-alapú felügyeletére. A Windows 10-es MDM számos új felügyeleti és biztonsági képességet nyújt, amelyek az örökölt Intune szoftverügyféllel nem elérhetők.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Az örökölt számítógépügyfelek funkciói csak a Silverlight-konzolon érhetők el

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Az Intune-számítógépügyfél felügyeleti munkafolyamatai a [Silverlight-alapú Intune felügyeleti konzolt](https://manage.microsoft.com/) használják, ami az alábbi következményekkel jár:

- Minden olyan felügyeleti feladathoz, amely nem csoportokra vonatkozik, és az Intune-számítógépügyfelet használja, a Silverlight-konzolt kell igénybe vennie.
- Csoportok felügyeleténél az [Azure Portal-beli Intune-t](https://portal.azure.com/) kell használnia. A követelmény oka, hogy az Intune az örökölt Intune-csoportok helyett most már Azure AD-csoportokat használja. 

Miután az Intune áttért az Azure AD-csoportok használatára, a Silverlight-konzol irányítópultjának nézeteiben a „csoportalapú” szűrés némileg megváltozott. Ha a Silverlight frissített felhasználói felületén szeretne szűrést végezni, kövesse az alábbi lépéseket:

1. Válasszon ki egy nézetet.
2. A **Szűrők** mezőbe írja be a szűrni kívánt csoport a nevét, majd nyomja le az Enter billentyűt. Ez a művelet szűrni fogja az eszközök listanézetét a megadott csoportban.

   ![Legördülő lista bemenetének szűrése nincs kijelölve](./media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>A Windows 7 további felügyelete az Intune számítógép-ügyféllel

Mivel a Windows 7-et nem lehet az MDM használatával felügyelni, ebben az esetben, csak a Silverlight-konzolon, tovább támogatjuk a meglévő Intune szoftverügyfél funkcióit. Windows 10-re történő frissítés esetén fontolja meg a váltást az MDM-felügyeletre.

## <a name="mdm-capabilities"></a>Az MDM képességei

A szoftverügyfél és az MDM képességeinek összehasonlításához lásd: [Windows-számítógépek számítógépként és mobileszközként való összehasonlítása](pc-management-comparison.md). Az MDM frissítései továbbra is eljuttatják az új felügyeleti képességeket az MDM által regisztrált Windows 10 rendszerű eszközökre, beleértve a Win 32 alkalmazások lehetőségeinek kiértékelését is. A szolgáltatás legújabb kiegészítéseihez tekintse meg az [Újdonságokat](whats-new.md).

## <a name="switch-from-pc-client-to-mdm"></a>Váltás a szoftverügyfélről az MDM-re

Kövesse az alábbi lépéseket a Windows 10-eszközök felügyeletének áthelyezéséhez az Intune szoftverügyfélről az MDM-re:

1. Végezzen el egy **szelektív törlést** a Silverlight-konzolon, ezzel visszavonja az eszköz regisztrációját a szoftverügyfélről.
  ![Warning felugró ablak a "kiválasztva az eszköz szelektív törlése" választógomb kiválasztott @ no__t-1
2. Regisztrálja újra az eszközt az [MDM (és/vagy az Azure AD-csatlakozási felület)](../enrollment/windows-enroll.md) használatával.

## <a name="next-steps"></a>További lépések
[Windows-eszközök regisztrálása](../enrollment/windows-enroll.md)
