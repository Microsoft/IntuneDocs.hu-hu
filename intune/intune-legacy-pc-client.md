---
title: Örökölt Intune szoftverügyfél és az Intune az Azure-ban
description: Szempontok az Azure-beli Intune használatához cége Windows-eszközeinek felügyeletéhez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 27f3a184e355f63d20a79fd92e8326206f6eee15
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185627"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune az Azure-konzolon és az örökölt Intune szoftverügyfél

Az Intune az Azure-alapú saas alkalmazásszolgáltató architektúrára költözött használ. Az Azure jelentős fejlesztéseket nyújt a méretezés, a kapacitás és a teljesítmény terén. Nyújt a továbbfejlesztett Intune rendszergazdai felügyeletet, és optimalizált munkafolyamatokat az Azure Portalon. 

Ha az Azure-beli Intune-t használja cége Windows-eszközeihez, vegye figyelembe a következő szempontokat:

## <a name="manage-windows-10-devices-by-using-mdm"></a>Windows 10-eszközök felügyelete az MDM segítségével

Azt javasoljuk, hogy a [Windows 10-eszközök felügyeletéhez a mobileszköz-felügyeletet (MDM) válassza](https://docs.microsoft.com/intune/device-restrictions-windows-10) az örökölt Intune szoftverügyfél helyett. Az Azure Portal-beli Intune lehetőséget ad a Windows 10 MDM-alapú felügyeletére. A Windows 10-es MDM számos új felügyeleti és biztonsági képességet nyújt, amelyek az örökölt Intune szoftverügyféllel nem elérhetők.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Az örökölt számítógépügyfelek funkciói csak a Silverlight-konzolon érhetők el

Az Intune-számítógépügyfél felügyeleti munkafolyamatai a [Silverlight-alapú Intune felügyeleti konzolt](https://manage.microsoft.com/) használják, ami az alábbi következményekkel jár:

- Minden olyan felügyeleti feladathoz, amely nem csoportokra vonatkozik, és az Intune-számítógépügyfelet használja, a Silverlight-konzolt kell igénybe vennie.
- Csoportok felügyeleténél az [Azure Portal-beli Intune-t](https://portal.azure.com/) kell használnia. A követelmény oka, hogy az Intune az örökölt Intune-csoportok helyett most már Azure AD-csoportokat használja. 

Miután az Intune áttért az Azure AD-csoportok használatára, a Silverlight-konzol irányítópultjának nézeteiben a „csoportalapú” szűrés némileg megváltozott. Ha a Silverlight frissített felhasználói felületén szeretne szűrést végezni, kövesse az alábbi lépéseket:

1. Válasszon ki egy nézetet.
2. A **Szűrők** mezőbe írja be a szűrni kívánt csoport a nevét, majd nyomja le az Enter billentyűt. Ez a művelet szűrni fogja az eszközök listanézetét a megadott csoportban.

   ![](media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>A Windows 7 további felügyelete az Intune számítógép-ügyféllel

Mivel a Windows 7-et nem lehet az MDM használatával felügyelni, ebben az esetben, csak a Silverlight-konzolon, tovább támogatjuk a meglévő Intune szoftverügyfél funkcióit. Windows 10-re történő frissítés esetén fontolja meg a váltást az MDM-felügyeletre.

## <a name="mdm-capabilities"></a>Az MDM képességei

A szoftverügyfél és az MDM képességeinek összehasonlításához lásd: [Windows-számítógépek számítógépként és mobileszközként való összehasonlítása](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison). Az MDM frissítései továbbra is eljuttatják az új felügyeleti képességeket az MDM által regisztrált Windows 10 rendszerű eszközökre, beleértve a Win 32 alkalmazások lehetőségeinek kiértékelését is. A szolgáltatás legújabb kiegészítéseihez tekintse meg az [Újdonságokat](https://docs.microsoft.com/intune/whats-new).

## <a name="switch-from-pc-client-to-mdm"></a>Váltás a szoftverügyfélről az MDM-re

Kövesse az alábbi lépéseket a Windows 10-eszközök felügyeletének áthelyezéséhez az Intune szoftverügyfélről az MDM-re:

1. Végezzen el egy **szelektív törlést** a Silverlight-konzolon, ezzel visszavonja az eszköz regisztrációját a szoftverügyfélről.
  ![](media/intune-legacy-pc-client/image02.png)
2. Regisztrálja újra az eszközt az [MDM (és/vagy az Azure AD-csatlakozási felület)](https://docs.microsoft.com/intune/windows-enroll) használatával. 

## <a name="next-steps"></a>További lépések
[Windows-eszközök regisztrálása](https://docs.microsoft.com/intune/windows-enroll)

 
