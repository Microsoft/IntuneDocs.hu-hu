---
title: Mobile Threat Defense telepítése mobileszközön
description: Ismerje meg, hogyan telepítheti a Mobile Threat Defense szolgáltatást mobileszközön.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f395a9cedc72a8184cfe3e29d6fcd3117a1473d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72987449"
---
# <a name="install-mobile-threat-defense"></a>Mobile Threat Defense telepítése   

A szervezet biztonsági követelményeinek részeként szükség lehet a Mobile Threat Defense (MTD) szállítói alkalmazás telepítésére. Az ilyen típusú alkalmazások észlelik és riasztásokat küldenek az eszközön észlelt fenyegetésekről, például a gyanús alkalmazásokról, a hálózatokról vagy az operációs rendszer biztonsági réseit.  

Ha nem rendelkezik a szükséges MTD alkalmazással, a rendszer letiltja a védett alkalmazásokhoz való bejelentkezést munkahelyi vagy iskolai fiókjával. Ebből a cikkből megtudhatja, [hogyan telepíthet egy MTD-alkalmazást](set-up-mobile-threat-defense.md#install-app) a blokkolás feloldásához.  

A telepítéshez számos MTD-gyártói alkalmazás érhető el; a szervezet tudatja Önnel, hogy melyiket érdemes használni. 


## <a name="information-your-organization-can-see"></a>A szervezet által látható információk   

A szervezet nem láthat semmilyen olyan információt, mint a szövegek, az e-mailek és a képek a személyes alkalmazásaiban. A MTD alkalmazás az alkalmazásokkal kapcsolatos információkat, például a nevet és a verziót jelenti a szervezet számára. A jelentett tényleges információk a vállalat által használt MTD-gyártótól függenek. Előfordulhat, hogy a szervezete a következőket látja:   

* Alkalmazás neve  
* Alkalmazás azonosítója: az alkalmazást a Google Play-ben azonosító egyedi név.  
* Az alkalmazás verziószáma és rövid verziószáma: az alkalmazás adott kiadási száma.  
* Alkalmazáscsomag és dinamikus méret: az alkalmazás által az eszközön használt terület nagysága. 


## <a name="install-app"></a>Az alkalmazás telepítése    
Ha egy védett alkalmazásba jelentkezik be, a rendszer automatikusan kéri, hogy telepítsen egy MTD alkalmazást. A telepítés befejezéséhez kövesse a képernyőn megjelenő lépéseket. További segítségért kövesse az ebben a szakaszban található lépéseket.  
 
A rendszer kérheti az eszköz regisztrálását is. A regisztrációhoz meg kell erősítenie az identitását, és össze kell kapcsolnia az eszközét vagy munkahelyi fiókját. Ha nincs regisztrálva, a MTD alkalmazás telepítése előtt automatikusan végigvezeti az adott beállításon. A **hozzáférés beolvasása** képernyő elindításával elindíthatja a telepítési lépéseket.  

További információ az eszközök regisztrálásáról: [személyes eszköz regisztrálása a szervezet hálózatán](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network).  

### <a name="ios-setup"></a>iOS-telepítés  

1. A **hozzáférés lekérése** képernyőn kövesse az utasításokat a szervezete számára szükséges MTD alkalmazás telepítéséhez.   
2. Térjen vissza a **hozzáférés beolvasása** képernyőhöz, és válassza a **Megnyitás**lehetőséget.  
3. A MTD alkalmazás engedélyt kér a Microsoft Authenticator megnyitására. Válassza az **Open** (Megnyitás) lehetőséget. 
4. A bejelentkezéshez válassza ki a munkahelyi fiókot. 
5. Várjon, amíg a MTD alkalmazás biztonsági fenyegetéseket keres az eszközön. 
6. Térjen vissza az iskolába vagy a Work alkalmazásba, amelyet eredetileg próbált elérni. Ezen a ponton a szervezet kérheti, hogy más alkalmazás biztonsági követelményeit is konfigurálja, például PIN-kód létrehozását.   
7. Most már hozzáférhet az alkalmazáshoz. Ha továbbra is le van tiltva:  
    * A **hozzáférés lekérése** képernyőn válassza az ismételt **vizsgálat**lehetőséget.  
    * Nyissa meg a MTD alkalmazást, és keresse meg a meglévő fenyegetéseket. A fenyegetés feloldásához és a hozzáférés visszaszerzéséhez hajtsa végre a javasolt lépéseket.    

### <a name="android-setup"></a>Android-beállítás 

1. A **hozzáférés lekérése** képernyőn kövesse az utasításokat a szervezete számára szükséges MTD alkalmazás telepítéséhez.  
2. Térjen vissza a **hozzáférés beolvasása** képernyőhöz, és válassza a **Megnyitás**lehetőséget.  
3. A MTD alkalmazás arra kéri az engedélyt, hogy hozzáférjen az eszköz bizonyos területeihez, ha szükséges. Ahhoz, hogy az alkalmazás megfelelően működjön, engedélyeznie kell a **névjegyek elérését** . A kért engedélyek a MTD-szállítókon eltérőek lesznek.  
4. A bejelentkezéshez válassza ki a munkahelyi fiókot.  
5. Várjon, amíg a MTD alkalmazás biztonsági fenyegetéseket keres az eszközön.  
6. Térjen vissza az iskolába vagy a Work alkalmazásba, amelyet eredetileg próbált elérni. Ezen a ponton a szervezet kérheti, hogy más alkalmazás biztonsági követelményeit is konfigurálja, például PIN-kód létrehozását.  
7. Most már hozzáférhet az alkalmazáshoz. Ha továbbra is le van tiltva:  
    * A **hozzáférés lekérése** képernyőn válassza az ismételt **vizsgálat**lehetőséget.  
    * Nyissa meg a MTD alkalmazást, és keresse meg a meglévő fenyegetéseket. A fenyegetés feloldásához és a hozzáférés visszaszerzéséhez hajtsa végre a javasolt lépéseket.  

### <a name="installation-failed"></a>Sikertelen telepítés  

Ha a telepítés sikertelen, lépjen kapcsolatba az informatikai támogatási személlyel. Lépjen a [céges portál webhelyére](https://go.microsoft.com/fwlink/?linkid=2010980) , ahol megkeresheti a szervezet kapcsolattartási adatait.  

Az alkalmazás naplófájljait az informatikai támogatási személynek is elküldheti, hogy a telepítéssel kapcsolatos további kontextust biztosítson számukra.  
* Android-felhasználók: [a naplók feltöltése és e-mailek](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android) céges portálból való elküldése.   

* iOS-eszközök felhasználói: [a naplók lekérése és elküldése](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs) a Microsoft Edge-ből iOS-re.  

## <a name="resolve-a-threat"></a>Fenyegetés feloldása  
Ha a fenyegetés meghaladja a szervezete által meghatározott veszélyforrást, a szervezete a következőket teszi:  
   
* Hozzáférés letiltása: blokkolja a szervezete által védett alkalmazások használatát a munkahelyi vagy iskolai fiókba való bejelentkezéskor.  
* Adatok törlése: törli a munkahelyi vagy iskolai adatait a szervezete által védett alkalmazások közül.  

A fenyegetés feloldásához és a hozzáférés visszaszerzéséhez nyissa meg az eszközön a MTD alkalmazást. Olvassa el a megadott információkat, amelyből megtudhatja, hogyan érintheti a fenyegetés az eszközt, és hogyan oldhatja meg. Miután követte a fenyegetés feloldásának lépéseit, térjen vissza a MTD alkalmazáshoz, és kezdeményezzen új vizsgálatot. A szervezethez való hozzáférés visszanyerése néhány percet is igénybe vehet.  

## <a name="next-steps"></a>További lépések  

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).

