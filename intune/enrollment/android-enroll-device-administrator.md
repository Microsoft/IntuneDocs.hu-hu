---
title: Az Android-eszközök rendszergazdai regisztrációja Microsoft Intune
titleSuffix: ''
description: Android-eszközök regisztrálása az Intune-ban az eszköz rendszergazdai regisztrációjának használatával.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08193aa329a1bee4e66638de5c0d7518d15db2a4
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547912"
---
# <a name="android-device-administrator-enrollment"></a>Android-eszköz rendszergazdai regisztrációja

Android-eszköz rendszergazdája (más néven a "régi" Android-kezelés és az Android 2,2 kiadásban megjelent) az androidos eszközök felügyeletének módja. A továbbfejlesztett felügyeleti funkciók azonban mostantól elérhetők az [Android Enterprise](https://www.android.com/enterprise/management/) (Android 5,0) verzióban. A modern, gazdagabb és biztonságosabb eszközkezelés érdekében a Google az új Android-kiadásokban csökkenti az eszköz-rendszergazda támogatását.

Ezért az ilyen csökkentett funkciók elkerülése érdekében javasoljuk, hogy az új eszközök regisztrálását az alább ismertetett eszköz-rendszergazdai folyamat használatával.

Ugyanezen okok miatt javasoljuk, hogy az eszközöket az eszköz rendszergazdai felügyeletén kívülről telepítse át, ha az eszközök az Android 10 rendszerre fognak frissülni. 

Az Android-eszközök rendszergazdai támogatásának Intune-támogatásával kapcsolatos további információkért tekintse meg a [közlemények című szakaszt](../fundamentals/whats-new.md#decreasing-support-for-android-device-administrator).

Ha továbbra is úgy dönt, hogy a felhasználók regisztrálják androidos eszközeiket az eszközök rendszergazdai felügyeletével, folytassa a következő szakasszal.  


> [!Note]  
> Az Android 10 és újabb verziók nem támogatottak a hibrid mobileszköz-kezelésben (hibrid MDM; Az Intune a System Center Configuration Manager-konzollal felügyelt), mert a hibrid MDM a 2019-es szeptember 1-én kikerül a szolgáltatásból. Ha továbbra is hibrid MDM használ, a lehető leghamarabb át kell térnie az Intune önálló verzióra. Ha segítségre van szüksége az áttelepítéshez, forduljon a támogatási szolgálathoz. További információk: [Áttérés a hibrid mobileszköz-kezelésről az Azure-beli Intune-ra](https://aka.ms/hybrid_notification).

A Google androidos vállalati funkcióival kapcsolatos további információkért tekintse meg a következő cikkeket:
- [A Google útmutatója az eszköz-rendszergazdától az Android Enterprise rendszerre való áttelepítéshez](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [A Google dokumentációja az eszköz rendszergazdai API-jával való érvénytelenítésének tervéről](https://developers.google.com/android/work/device-admin-deprecation)


## <a name="set-up-device-administrator-enrollment"></a>Az eszköz rendszergazdai regisztrációjának beállítása

1. A mobileszközök kezelésének előkészítéseként a **Microsoft Intune**-t kell beállítani mobileszköz-kezelő (MDM) szolgáltatóként. Erről [Az MDM-szolgáltató beállítása](../fundamentals/mdm-authority-set.md) című cikk nyújt útmutatást. Ezt a beállítást csak egyszer, az Intune-nak a mobileszközök kezelésére való kezdeti beállítása során kell megadni.
2. Nyissa meg az **Intune** > eszközök **beléptetése** > **Android-regisztráció** > **személyes és vállalati tulajdonú eszközök eszköz-felügyeleti jogosultságokkal** > az eszköz **rendszergazdája által felügyelt eszközöket**.
3. [A felhasználók tájékoztatása arról, hogy miképpen regisztrálhatják az eszközeiket](/intune-user-help/enroll-your-device-in-intune-android).  

Miután a felhasználó elvégezte a regisztrálást, elkezdheti az eszközeik felügyeletét az Intune-ban, így többek között [megfelelőségi szabályzatokat rendelhet hozzájuk](../protect/compliance-policy-create-android.md) vagy [felügyelheti az alkalmazásokat](../apps/app-management.md).

Más felhasználói feladatokkal kapcsolatos további információkért tanulmányozza a következő cikkeket:
- [Információk végfelhasználóknak a Microsoft Intune használatáról](../fundamentals/end-user-educate.md)
- [Android-eszköz használata az Intune-nal](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>Az eszköz rendszergazdai regisztrációjának letiltása
Az androidos eszközök rendszergazdai eszközeinek letiltásához vagy csak a személyes tulajdonú Android-eszközök regisztrációjának letiltásához tekintse [meg az eszközök típusú korlátozások beállítása](enrollment-restrictions-set.md)című témakört.



## <a name="next-steps"></a>További lépések
- [Megfelelőségi szabályzatok kiosztása](../protect/compliance-policy-create-android.md)
- [Alkalmazások kezelése](../apps/app-management.md)
