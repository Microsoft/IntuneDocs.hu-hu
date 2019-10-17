---
title: Hogyan kell bejelentkezni a Céges portál alkalmazásba | Microsoft Docs
description: Információk arról, hogyan lehet bejelentkezni a Céges portál alkalmazásba különféle platformokon.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68a44027c14e0a52d72fc032a6ab42413fa8df96
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508303"
---
# <a name="sign-in-to-company-portal"></a>Bejelentkezés Céges portál  

Háromféle módon jelentkezhet be a Céges portál alkalmazásba:

* Jelentkezzen be a munkahelyi e-mail-címével és jelszavával.  
* Tanúsítvány alapú hitelesítéssel jelentkezzen be.  
* Jelentkezzen be egy másik eszközről.    


## <a name="sign-in-with-your-email-address-and-password"></a>Jelentkezzen be az e-mail-címével és jelszavával
A következő lépések az iOS-Céges portál képernyőképeit mutatják be.  

1. Nyissa meg az alkalmazást az eszközön, és koppintson a **Bejelentkezés**elemre.  

   [![Example képernyőkép a Céges portál bejelentkezési oldaláról. @no__t – 2](/intune-user-help/media/intune-ios-cp-signin-lightbox-1908.png#lightbox)  


2. Adja meg **munkahelyi vagy iskolai fiókját**, és koppintson a **Tovább** lehetőségre.

   ![A felhasználónak ugyanazon az oldalon csak az e-mail-címét kell megadnia, nem pedig mind az e-mail-címét, mind a jelszavát.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Adja meg a jelszót, majd koppintson a **Bejelentkezés** elemre.

   ![A felhasználótól csak akkor kéri a rendszer a jelszavát ha már helyesen megadta az e-mail-címét.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. Az alkalmazás ellenőrzi a hitelesítő adatait. Ha elkészült, elérheti a szervezet erőforrásait, és telepítheti az elérhető alkalmazásokat.  

   ![A hitelesítési folyamat után a Céges portál alkalmazás bejelentkezik, és megjeleníti a betöltési sávot.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="sign-in-with-certificate-based-authentication"></a>Bejelentkezés tanúsítványalapú hitelesítéssel

1. Nyissa meg az eszközén a Céges portál alkalmazást.  

2. Adja meg a **munkahelyi vagy iskolai fiókját**.  

3. Koppintson a **Bejelentkezés tanúsítvánnyal** lehetőségre.  

4. A tanúsítvány használatához koppintson a **Folytatás** lehetőségre.  

## <a name="sign-in-from-another-device"></a>Bejelentkezés másik eszközről

Ha a vállalata intelligens kártyák használatával fér hozzá a számítógépekhez, akkor valószínű, hogy a hitelesítést egy másik eszközről kell bejelentkeznie.  

1. Nyissa meg az eszközén a Céges portál alkalmazást. Győződjön meg arról, hogy az eszköz, amelyet használni fog a munkahelyi erőforrások eléréséhez.       

1. Válassza a **bejelentkezés másik eszközről**lehetőséget.  

   ![A bejelentkezési oldal Céges portál bekéri a felhasználót az e-mail-címre.  Megjeleníti a "Next" (tovább) gombot, valamint a "bejelentkezés másik eszközről" hivatkozást. Tartalmaz egy „Nem tud hozzáférni a fiókjához?” hivatkozást is. Az oldal alján látható egy hivatkozás, amely a Microsoft Adatvédelem és cookie-k oldalára mutat.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Ekkor egy egyedi, egyszer használatos kódot kap a Céges portálra történő bejelentkezéshez. Másolja a kódot.

   ![A rendszer arra kéri a felhasználót, hogy látogassa meg az https://microsoft.com/devicelogin oldalt a munkahelyi számítógéphez tartozó, megjelenített egyedi kódot használva a bejelentkezéshez.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. A másik eszközön (amelyet a hitelesítéshez használ) nyissa meg a böngészőt, és lépjen a következőre: [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin). Adja meg vagy illessze be a kódot.  

   ![A felhasználó munkagépén futó böngészőablak képe (nem pedig a Céges portál alkalmazásé). A megjelenített „Eszközbejelentkezés” oldal arra kéri a felhasználót, hogy adja meg a Céges portál alkalmazástól kapott kódot.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Válassza a __Folytatás__ lehetőséget, hogy a céges portál bejelentkezzen a munkahelyi eszközére.   

   ![A felhasználó beírta a mezőbe az egyedi kódját, az „Eszközbejelentkezés” webhely pedig a felhasználó megerősítését kéri, hogy az Intune Céges portálnak kell-e bejelentkezési engedélyt kapnia.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. A kód ellenőrzése után bezárhatja az ablakot.  

   ![Jóváhagyást jelző oldal, amely megerősíti, hogy a felhasználó bejelentkezett a Céges portál alkalmazásra az eszközén, és hogy ez az oldal bezárható.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. A Céges portál alkalmazás aláírja a munkahelyi eszközén.  

   ![Miután a hitelesítési folyamat lezárult, bejelentkezik a Céges portál alkalmazás, és a folyamatot egy betöltést jelző sáv mutatja.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
