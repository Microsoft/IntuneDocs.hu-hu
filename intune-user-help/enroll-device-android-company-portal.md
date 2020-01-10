---
title: Android-eszköz regisztrálása a Intune Céges portálkal | Microsoft Docs
description: Útmutató androidos eszközök regisztrálásához Intune Céges portál
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e0a2297509d6077d6508adaab96ae6eb3cf9b28f
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856734"
---
# <a name="enroll-your-device-with-company-portal"></a>Az eszköz regisztrálása a Céges portál  
Regisztrálja személyes vagy vállalati tulajdonú Android-eszközét, hogy biztonságos hozzáférést kapjon a vállalati e-mailekhez, alkalmazásokhoz és adatszolgáltatásokhoz. Céges portál támogatja az Android-eszközöket, beleértve a Samsung Knox-t, az Android 4,4-es vagy újabb verzióját.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> A Samsung Knox olyan biztonsági típus, amelyet bizonyos Samsung-eszközök a natív Android által biztosított további védelemhez használnak. Ellenőrizze, hogy rendelkezik-e Samsung Knox-eszközzel, > lépjen a **beállítások** > **az eszköz névjegye**elemre. Ha nem jelenik meg a **Knox-verzió** , akkor natív Android-eszközzel rendelkezik.

## <a name="enroll-device"></a>Eszköz regisztrálása  
Győződjön meg arról, hogy [az ingyenes Intune céges portál alkalmazást a Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)áruházból telepíti. 

A regisztráció során előfordulhat, hogy a rendszer arra kéri, hogy válasszon egy kategóriát, amely a legjobban leírja, hogyan használja az eszközt. A cég informatikai támogatási szolgálata a választ használva vizsgálja meg, hogy milyen alkalmazásokhoz férhet hozzá.  

1. Nyissa meg a Céges portál alkalmazást, és jelentkezzen be a munkahelyi vagy iskolai fiókjával.  

2. Ha a rendszer kéri, hogy fogadja el a szervezet használati feltételeit, koppintson az **összes elfogadása**elemre.  

   ![Példa a Céges portál képre, a feltételek képernyőre, és kiemelve az "összes elfogadása" gombot.](./media/accept-terms-1911.png)  


3. Tekintse át a szervezete által megjelenített és nem látható tudnivalókat. Ezután koppintson a **Folytatás**gombra.


    ![Példa Céges portál kép az adatvédelmi képernyőről, a Folytatás gomb kiemelése.](./media/android-privacy-screen-1911.png)  
4. Tekintse át, mire számíthat a következő lépésekben. Ezután koppintson a **tovább**gombra.  

    ![Példa Céges portál képre, a következő képernyőre, majd a Tovább gombra.](./media/android-whats-next-1911.png)  


5. Az Android-verziójától függően előfordulhat, hogy a rendszer felszólítja, hogy engedélyezze a hozzáférést az eszköz bizonyos részeihez. Ezek a kérések a Google számára szükségesek, és nem a Microsoft vezérli.  

    Koppintson az **Engedélyezés** elemre a következő engedélyekhez:  
    * **Telefonos hívások végrehajtásának engedélyezése céges portál**: ez az engedély lehetővé teszi az eszköz számára, hogy megossza a nemzetközi mobileszköz-azonosító (IMEI) számát az Intune-nal, a szervezet Eszközkezelő szolgáltatójának használatával. Ez az engedély biztonságosan engedélyezhető. A Microsoft soha nem hajtja végre a telefonhívásokat.  
    * **Céges portál a névjegyek elérésének engedélyezése**: ez az engedély lehetővé teszi a céges portál alkalmazás számára a munkahelyi fiók létrehozását, használatát és kezelését.  Ez az engedély biztonságosan engedélyezhető. A Microsoft soha nem fogja elérni a névjegyeket. 

    Ha megtagadja az engedélyt, a rendszer a következő bejelentkezéskor újra rákérdez a Céges portálre. Az üzenetek kikapcsolásához válassza a **Soha ne Kérdezzen újra**lehetőséget. Az alkalmazás engedélyeinek kezeléséhez lépjen a beállítások alkalmazás > **alkalmazások** > **Céges portál** > **engedélyek** > **telefon**elemre.  

6. Aktiválja az eszköz rendszergazdai alkalmazását. 

    Céges portál az eszköz biztonságos kezeléséhez az eszköz rendszergazdai engedélyei szükségesek. Az alkalmazás aktiválása lehetővé teszi, hogy a szervezet azonosítsa a lehetséges biztonsági problémákat, például az eszköz zárolásának ismételt sikertelen kísérleteit, és megfelelően válaszoljon.  

    ![Az eszköz adminisztrátorának aktiválása képernyő képe, az aktiválás gomb kiemelése.](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> A Microsoft nem szabályozza az üzenetküldést ezen a képernyőn. Megértettük, hogy a megfogalmazás némileg drasztikusnak tűnhet. Céges portál nem tudja megadni, hogy mely korlátozások és hozzáférések legyenek relevánsak a szervezet számára. Ha kérdése van arról, hogy a szervezet hogyan használja az alkalmazást, lépjen kapcsolatba az informatikai támogatási személlyel. Lépjen a [céges portál webhelyére](https://go.microsoft.com/fwlink/?linkid=2010980) , ahol megkeresheti a szervezet kapcsolattartási adatait.  


7. Az eszköz regisztrálása megkezdődik. Ha Samsung Knox-eszközt használ, a rendszer kérni fogja, hogy először tekintse át és fogadja el az ELM ügynök adatvédelmi szabályzatát.   

    ![Példa a Samsung Knox adatvédelmi szabályzat képernyőre, amely megjelenik a regisztráció során.](./media/and-enroll-7-knox-privacy-policy.png)  

8. A **vállalati hozzáférés beállítása** képernyőn győződjön meg arról, hogy az eszköz regisztrálva van. Ezután koppintson a **Folytatás**gombra.  

    ![Példa Céges portálre, a vállalati hozzáférés beállítása képernyőre, amely megmutatja, hogy az eszköz felügyelt beolvasása befejeződött.](./media/update-settings-1911.png)  

9. Előfordulhat, hogy a szervezetnek frissítenie kell az eszköz beállításait. A beállítások módosításához koppintson a **feloldás** elemre. Ha elkészült a beállítások frissítésével, koppintson a **Folytatás**gombra.  

   ![Példa Céges portál képe, az eszközbeállítások frissítése, a feloldás és a Folytatás gomb kiemelése.](./media/resolve-settings-1911.png)  

10. Ha a telepítés befejeződött, koppintson a **kész**gombra.    

    ![Példa a Céges portál, a vállalati hozzáférés beállítása képernyőre, amely a befejezett telepítőt és a kész gomb kiemelését jeleníti meg.](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>További lépések  

Mielőtt megpróbál telepíteni egy iskolai vagy munkahelyi alkalmazást, lépjen a **beállítások** > **Biztonság**elemre, és kapcsolja be az **ismeretlen forrásokat**. Ha nem kapcsolja be ezt a beállítást, a következő üzenet jelenik meg, amikor megpróbál telepíteni egy alkalmazást: "a telepítés letiltva. Biztonsági okokból az eszköz blokkolja az ismeretlen forrásból származó alkalmazások telepítését.” Az üzenet **beállításaira** koppintva közvetlenül az **ismeretlen forrásokhoz**juthat.  

> [!Note]
> Ha a szervezete távközlésiköltség-kezelő szoftvert használ, az eszköz teljes regisztrálásához még néhány lépést el kell végezni. További információért [kattintson ide](enroll-your-device-with-telecom-expense-management-android.md).

Ha hibaüzenet jelenik meg az eszköz Intune-beli regisztrálásakor, [e-mailt küldhet a cég informatikai támogatási szolgálatának](send-logs-to-your-it-admin-by-email-android.md).  

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  