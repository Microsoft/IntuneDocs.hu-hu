---
title: "Windows 8.1- vagy Windows RT 8.1-eszköz regisztrálása | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 28b7d99e285762945b746295688fee5d53209b29
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-enroll-your-windows-81-or-windows-rt-81-device-in-intune"></a>Windows 8.1- vagy Windows RT 8.1-eszköz regisztrálása az Intune-ban

Ha munkahelye vagy iskolája a Microsoft Intune-t használja, eszközének regisztrálásával hozzáférhet a vállalati levelezéséhez, fájljaihoz és egyéb vállalati erőforrásaihoz. Ha regisztrálja az eszközeit, azzal a szervezete megóvhatja a vállalati adatokat. További információk a regisztrációval kapcsolatban: [Mi történik a Céges portál alkalmazás telepítésekor és az eszköz Intune-beli regisztrálásakor?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md), illetve [Mit láthat a cég informatikai támogatási szolgálata az eszközén, és mit nem?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) témakörben.


Windows 8.1- vagy Windows RT 8.1-eszköz regisztrálása az Intune-ban:

1.  Nyissa meg az eszközön a **Beállítások** &gt; **Gépház** &gt; **Hálózat** &gt; **Munkahely** lapot.

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  Írja be a felhasználói azonosítójához tartozó munkahelyi vagy iskolai e-mail címét, és koppintson a **Csatlakozás** elemre.

    Ha az alkalmazás nem kéri a felhasználói azonosítót, akkor automatikusan azt az e-mail-címet használja, amelyikkel bejelentkezett az eszközre.

3.  Adja meg a munkahelyi vagy az iskolai e-mail-címéhez tartozó jelszót.

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  Koppintson az **Eszközkezelés bekapcsolása** terület **Bekapcsolás** elemére.

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  Jelölje be az **Alkalmazások és szolgáltatások engedélyezése a cég informatikai támogatási szolgálatának felületéről** párbeszédpanel **Elfogadom** négyzetét, majd koppintson a **Bekapcsolás** elemre.

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    A sikeres regisztrálás után megjelenik a következő képernyő.

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

Azt javasoljuk, hogy telepítse a Vállalati portál alkalmazást, mert azzal egyszerűen megismerheti és letöltheti az Ön és munkaköre szempontjából fontos vállalati alkalmazásokat. Attól függően, hogy a vállalat hogyan állította be az Intune-t, előfordulhat, hogy a Vállalati portál alkalmazás már a regisztrációs folyamat részeként települt. Ha az alkalmazáslistában szerepel a **Vállalati portál**, akkor már megvan Önnek az alkalmazás. Ha a vállalati portál nem jelenik meg az alkalmazáslistán, akkor a következő lépésekkel telepítheti.

1.  Koppintson a **Start** &gt; **Áruház** parancsra.

2.  Koppintson a **Keresés** elemre, majd írja be a **vállalati portál** kifejezést.

3.  Az eredmények listájában koppintson a **Vállalati portál** elemre.

4.  Koppintson a **Telepítés** vagy az **Ingyenes** lehetőségre. Az, hogy melyik beállítás jelenik meg, attól függ, hogy a vállalat hogyan állította be az alkalmazást.

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://portal.manage.microsoft.com#HelpDeskDialog).
