---
title: A céges erőforrásokhoz iOS-eszközzel történő hozzáférés beállítása | Microsoft Docs
description: Ismerteti az iOS-eszközök Intune-felügyelet alá helyezését
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e468042ab81d563c9fa4b272661508a340d61aa9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506245"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>A céges erőforrásokhoz iOS-eszközzel történő hozzáférés beállítása  

Regisztrálja iOS-eszközét az Intune Céges portál alkalmazással, hogy biztonságos hozzáférést kapjon vállalata levelezéséhez, fájljaihoz és alkalmazásaihoz.

Az eszköz regisztrálása után a rendszer *felügyeli*. A szervezet a mobileszköz-felügyeleti (MDM-) szolgáltatón (például az Intune-on) keresztül rendelhet szabályzatokat és alkalmazásokat az eszközhöz.  

> [!NOTE]
> A szolgáltatás által gyűjtött adatokat semmilyen okból nem adjuk át harmadik félnek.  

Az eszközről a munkahelyi vagy iskolai adatokhoz való hozzáférés fenntartásához konfigurálnia kell az eszközt úgy, hogy az megfeleljen a szervezete által preferált beállításoknak. Ez a cikk azt ismerteti, hogyan lehet a Céges portál segítségével regisztrálni az eszközt, és karbantartani a szervezet beállítási követelményeit.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Ha a vállalati e-maileket a Mail alkalmazással próbálta elérni, és kapott egy felszólítást, hogy helyezze felügyelet alá az eszközét, akkor a megfelelő helyen jár. Ahhoz, hogy iOS-eszközén is hozzá tudjon férni a céges e-mailekhez és más erőforrásokhoz, kövesse az alábbi útmutatót.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Ami a Céges portál alkalmazástól elvárható  

### <a name="security"></a>Biztonság  
Első beállítása során az alkalmazás megköveteli, hogy hitelesítse magát vállalatánál. Ez után tájékoztatja az összes eszközbeállításról, amelyeket frissítenie kell. A vállalatok gyakran megadják például a jelszavak minimális vagy maximális karakterszámát, és ezt Önnek be kell tartania.

### <a name="protection"></a>Protection  
Eszköze regisztrálása után a Céges portál alkalmazás folyamatosan gondoskodik az eszköz védelméről. Ha például nem megbízható forrásból telepít valamit, az alkalmazás riasztást küld Önnek, és olykor meg is vonja a vállalati adatokhoz való hozzáférést. Ez a fajta házirend gyakori a szervezeteknél, és gyakran megköveteli a nem megbízható alkalmazás eltávolítását a hozzáférés visszanyerése előtt.  

### <a name="setting-notifications"></a>Értesítések beállítása  
Ha a regisztráció után a vállalat új biztonsági követelményt, például többtényezős hitelesítést vezet be, a Céges portál alkalmazás értesíti Önt. Lehetősége lesz módosítani beállításait, hogy továbbra is dolgozhasson az eszközéről.  

További információk a regisztrációval kapcsolatban: [Mi történik a Céges portál alkalmazás telepítésekor és az eszköz regisztrálásakor?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>IOS-eszköz regisztrálása  

Nyissa meg az App Store-t a [Intune céges portál alkalmazás](install-and-sign-in-to-the-intune-company-portal-app-ios.md) letöltéséhez és telepítéséhez az eszközön. Emellett egy Wi-Fi-kapcsolatot kell fenntartania, és hozzáféréssel kell rendelkeznie a Safarihoz a regisztráció során. 

Előfordulhat, hogy a regisztráció során a rendszer több, mint néhány percen belül szünetelteti az alkalmazást a telepítés befejezéséhez. Ha ez történik, nyissa meg a Céges portál alkalmazást, és próbálkozzon újra.  

1. Nyissa meg Céges portál, és jelentkezzen be munkahelyi vagy iskolai fiókjával. 

    ![Példa a Céges portál alkalmazás képernyőképére, majd jelentkezzen be.](./media/ios-01-cp-enroll-1904.PNG)  

2. Amikor a rendszer felszólítja Céges portál értesítések fogadására, koppintson az engedélyezés elemre **.** Céges portál értesítések használatával figyelmezteti, ha például az eszköz beállításait frissíteni kell. 

    ![Példa a Céges portál Kezdőlap "értesítések" üzenetére.](./media/ios-02-cp-enroll-1904.PNG)  

3. A **hozzáférés beállítása** képernyőn válassza az indítás lehetőséget **.**  

     ![Példa a "hozzáférés beállítása" képernyőn látható Céges portál képernyőképre.](./media/ios-03-cp-enroll-1904.PNG)  

4. Olvassa el a szervezet által megjelenített és nem látható eszköz-információk listáját. Ezután koppintson a **Folytatás**gombra.  

5. Olvassa el a **Mi a következő lépés?** képernyőn megjelenő utasításokat. Ha készen áll a felügyeleti profil letöltésére és telepítésére, koppintson a **Folytatás**gombra.  

 > [!IMPORTANT]
> A következő lépések és képernyők az iOS-verziótól függően eltérőek lesznek. Kövesse az iOS-verziójának lépéseit. 

6. A Safari megnyitja a Céges portál webhelyét az eszközön. Amikor a rendszer kéri, hogy töltse le a konfigurációs profilt, koppintson az **Engedélyezés**elemre. Ha olyan eszközt használ, amely a következőket futtatja:  
    * iOS 12,2 és újabb verziók: Ha a letöltés befejeződött, koppintson a **Kész gombra.** Folytassa a cikk 7. lépésével.
    * iOS 12,1 és korábbi verziók: a rendszer automatikusan átirányítja a beállításokat az alkalmazásba. Ugorjon a jelen cikk 8. lépésére.  
 
    Ha véletlenül koppint a **Mellőzés**lehetőségre, frissítse a lapot. A rendszer felszólítja, hogy nyissa meg a Céges portál alkalmazást. Az alkalmazásból koppintson a **Letöltés újra**lehetőségre.

  > [!NOTE]
  > A felügyeleti profilt a letöltés után 8 percen belül a következő lépésekben leírtak szerint kell telepítenie. Ha nem, a profil el lesz távolítva, és újra kell indítania a beléptetést.  

7. iOS 12,2 és újabb verziók esetén: Ha a rendszer kéri, hogy nyissa meg Céges portál, koppintson a **Megnyitás**gombra. A **felügyeleti profil telepítése** képernyő felsorolja a profil telepítésének lépéseit.

    ![Példa a Céges portál képernyőképére, a felügyeleti profil képernyőjének telepítése.](./media/ios-07-cp-enroll-1904.PNG)  

8. Nyissa meg a beállítások alkalmazást, és koppintson a **profil letöltése**elemre.  

    Ha a **profil letöltése** nem jelenik meg lehetőségként, lépjen az **általános** > **profilok**elemre. Ha továbbra sem látja a profilt, lehetséges, hogy újra le kell töltenie.  

    ![Példa a beállítások alkalmazás, a profil letöltött beállítása képernyőképre.](./media/ios-1904-settings-badge.PNG)  

9. Koppintson a **Telepítés** elemre.  
    
10. Adja meg az eszköz jelszavát. Ezután koppintson a **telepítés**gombra.    

    ![Példa a beállítások alkalmazásra, a profil beállítása képernyőre a * * telepítés * * gomb kurzorával.](./media/ios-10-cp-enroll-1904.PNG)  


11. A következő képernyő az eszközkezelés szabványos rendszerfigyelmeztetése. A telepítés folytatásához koppintson a **telepítés**gombra. Ha a rendszer felszólítja a Távoli felügyelet megbízhatóságára, koppintson a **megbízhatóság**elemre.  

    ![Példa a beállítások alkalmazás képernyőképére, a főtanúsítvány és a mobileszköz-kezelés szabványos rendszerfigyelmeztetési képernyőjére.](./media/ios-11-cp-enroll-1904.PNG)  

12. A telepítés befejezése után koppintson a **kész**gombra. Annak ellenőrzéséhez, hogy a profil telepítve van-e, nyissa meg a **profilok & eszköz-felügyeleti** beállítások lapot. A profilt a **mobileszköz-kezelés**területen találja.   

    ![Példa a beállítások alkalmazás képernyőképére, a profilok & Az eszközkezelés beállításai elemre, amely a felügyeleti profilt mutatja.](./media/ios-12-cp-enroll-1904.PNG)  

13. Térjen vissza a Céges portál alkalmazáshoz. Céges portál megkezdi az eszköz szinkronizálását és beállítását. Előfordulhat, hogy a Céges portál további eszközbeállítások frissítését kéri. Ha igen, koppintson a **Folytatás**gombra.  

    ![Képernyőkép a Céges portálról: "hozzáférés beállítása" képernyő, sárga háromszög mellett a beállítás követelménye mellett.](./media/ios-13-cp-enroll-1904.PNG)  

14. Arról is tájékozódhat, hogy a beállítás akkor fejeződik be, ha a lista minden eleme zöld kört mutat. Koppintson a **Kész** gombra.   
    
    ![Példa a Céges portál képernyőképére: "készen vagyunk!" képernyő, amely az összes zöld kört mutatja.](./media/ios-14-cp-enroll-1904.PNG)  

> [!Note]
> Ha a szervezete figyeli a hang-és adatkorlátokat, vagy a vállalat által birtokolt eszközt is tartalmaz, előfordulhat, hogy néhány további lépést is végre kell hajtania. Ha a rendszer kéri, hogy telepítse a **Datalert** alkalmazást, tekintse [meg az eszköz regisztrálása a távközlési költségek kezelése](enroll-your-device-with-telecom-expense-management-ios.md)című témakört. Ha a szervezete az Apple Készülékregisztrációs program részét képezi, tájékozódjon [a vállalati tulajdonú eszközök regisztrálásáról](enroll-your-device-dep-ios.md).  

## <a name="it-administrator-support"></a>INFORMATIKAI rendszergazda támogatása  
Ha Ön rendszergazda, és az eszközök regisztrálása során problémákba kerül, tekintse meg [az iOS-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Ez a cikk a gyakori hibákat, azok okait és a megoldás lépéseit sorolja fel.  

## <a name="next-steps"></a>További lépések  
Olyan alkalmazásokat kereshet, amelyek segítséget nyújtanak a munkahelyi vagy iskolai munkához. Ismerje meg, [Hogyan érhetők el az alkalmazások](use-managed-apps-on-your-device-ios.md) céges portálon keresztül.  

További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához. A kapcsolatfelvételi adatait megtalálja a [Munkahelyi portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
