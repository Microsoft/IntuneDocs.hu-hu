---
title: "Windows 8.1- vagy Windows RT 8.1-eszköz regisztrálása az Intune-ban | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f83a539e9bec5207d7c1c682942b4bb6797d616c
ms.openlocfilehash: 6607ea6c355e0ec767e514ac0097789b83c5d8c7


---


# Windows 8.1- vagy Windows RT 8.1-eszköz regisztrálása az Intune-ban

Ha munkahelye vagy iskolája a Microsoft Intune-t használja, eszközének regisztrálásával hozzáférhet a vállalati levelezéséhez, fájljaihoz és egyéb vállalati erőforrásaihoz. Az eszközök regisztrálása lehetővé teszi munkahelye számára, hogy megóvhassa a vállalati adatokat. További információk a regisztrációval kapcsolatban: [Mi történik a Vállalati portál alkalmazás telepítésekor és az eszköz Intune-beli regisztrálásakor?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md), illetve [Mit láthat a rendszergazda az eszközén, és mit nem?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md) témakörben.


Windows 8.1- vagy Windows RT 8.1-eszköz regisztrálása az Intune-ban:

1.  Nyissa meg az eszközön a **Beállítások** &gt; **Gépház** &gt; **Hálózat** &gt; **Munkahely** lapot.

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  Írja be a felhasználói azonosítójához tartozó munkahelyi vagy iskolai e-mail címét, és koppintson a **Csatlakozás** elemre.

    Ha az alkalmazás nem kéri a felhasználói azonosítóját, akkor az eszközre való bejelentkezéskor megadott e-mail címét használja a szoftver.

3.  Írja be a munkahelyi vagy az iskolai e-mail címéhez tartozó jelszót.

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  Koppintson az **Eszközkezelés bekapcsolása** terület **Bekapcsolás** elemére.

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  Jelölje be az **Alkalmazások és szolgáltatások engedélyezése az IT rendszergazdai felületről** párbeszédpanel **Elfogadom** jelölőnégyzetét, majd koppintson a **Bekapcsolás** elemre.

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    A sikeres regisztrálás után megjelenik a következő képernyő.

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

Azt javasoljuk, hogy telepítse a Vállalati portál alkalmazást, mert azzal egyszerűen megismerheti és letöltheti az Ön és munkaköre szempontjából fontos vállalati alkalmazásokat. Attól függően, hogy vállalata hogyan konfigurálta az Intune-t, előfordulhat,  hogy a Vállalati portál alkalmazás már a regisztrációs folyamat részeként települt. Ha az alkalmazáslistában szerepel a **Vállalati portál**, akkor már megvan Önnek az alkalmazás. Ha a vállalati portál nem jelenik meg az alkalmazáslistán, akkor a következő lépésekkel telepítheti.

1.  Koppintson a **Start** &gt; **Áruház** parancsra.

2.  Koppintson a **Keresés** elemre, és írja be a **vállalati portál** kifejezést.

3.  Az eredmények listájában koppintson a **Vállalati portál** elemre.

4.  Koppintson a **Telepítés** vagy az **Ingyenes** lehetőségre. Attól függ, hogy melyik beállítás jelenik meg, hogy a vállalat hogyan konfigurálta az alkalmazást.

További segítségre van szüksége? Forduljon a rendszergazdához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).

### További információ
[Windows-eszköz regisztrálása az Intune-ban](enroll-your-device-in-intune-windows.md)</br>
[Windows-eszköz használata az Intune-nal](using-your-windows-device-with-intune.md)



<!--HONumber=Jun16_HO4-->


