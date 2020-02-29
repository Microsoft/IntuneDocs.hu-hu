---
title: A céges erőforrásokhoz iOS-eszközzel történő hozzáférés beállítása | Microsoft Docs
description: Ismerteti az iOS-eszközök Intune-felügyelet alá helyezését
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
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
ms.collection: ''
ms.openlocfilehash: 92d1ca850d8bb542f0b7fe027ab7af8c12089ef8
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181755"
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

2. Amikor a rendszer felszólítja Céges portál értesítések fogadására, koppintson az engedélyezés elemre **.** Céges portál értesítések használatával figyelmezteti, ha például az eszköz beállításait frissíteni kell.  

3. A **hozzáférés beállítása** képernyőn válassza az indítás lehetőséget **.**   

    ![Példa a "hozzáférés beállítása" képernyőn látható Céges portál képernyőképre.](./media/ios-enrollment-checklist-1909.PNG)  

4. Megjelenik az **eszköz és a beléptetési típus kiválasztása** képernyő, és felszólítja az eszköz típusára.  
    * Koppintson a **(szervezet)** elemre az eszköz tulajdonosa, ha az eszközt a szervezettől kapta. Ezután ugorjon a [teljes eszköz védelme](#secure-entire-device) ebben a cikkben a telepítés befejezéséhez.  
    * Koppintson a **saját eszköz** elemre, ha otthonról indított személyes eszközt használ. Ezután folytassa a következő lépéssel.  

    Ha nem látja ezt a képernyőt, ugorjon a [teljes eszköz védelme](#secure-entire-device) a telepítés befejezéséhez.  
    
    ![Példa a Céges portál, "eszköz és beléptetési típus kiválasztása" képernyőre, az eszköz típusának beállításaira.](./media/ios-device-type-1909.PNG)  


5. A regisztrálás után válassza ki, hogyan szeretné védetté tenni az eszközön lévő adatvédelmet.  
    * A **teljes eszköz** biztonsága lehetőségre koppintva gondoskodhat az eszközön található összes alkalmazás és szolgáltatás védelméről. Ezután válassza a [teljes eszköz védelme](enroll-your-device-in-intune-ios.md#secure-entire-device) lehetőséget a telepítés befejezéséhez.
    * A **biztonságos munkavégzéssel kapcsolatos alkalmazások és az adat csak** a munkahelyi fiókhoz hozzáférő alkalmazások és adatmennyiségek védelmére használható. Ezután nyissa meg a [biztonságos munkavégzéssel kapcsolatos alkalmazásokat és az adatforrásokat](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data).  

    ![Példa a Céges portál, "az eszköz és a beléptetési típus kiválasztása" képernyő, a regisztrációs típus beállításai lehetőségre.](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>Teljes eszköz védelme  

1. Az **eszközkezelés és adatvédelem** képernyőn olvassa el a szervezet által megjelenített és nem látható eszközök adatainak listáját. Ezután koppintson a **Folytatás**gombra.  


 > [!IMPORTANT]
> A következő lépések és képernyők az iOS-verziótól függően eltérőek lesznek. Kövesse az iOS-verziójának lépéseit. 

2. A Safari megnyitja a Céges portál webhelyét az eszközön. Amikor a rendszer kéri, hogy töltse le a konfigurációs profilt, koppintson az **Engedélyezés**elemre. Ha olyan eszközt használ, amely a következőket futtatja:  
    * iOS 12,2 és újabb verziók: Ha a letöltés befejeződött, koppintson a **Bezárás**gombra. Ezután folytassa a 3. lépéssel.  
    * iOS 12,1 és korábbi verziók: Ha a letöltés befejeződött, a rendszer automatikusan átirányítja a beállítások alkalmazásba. Ugorjon a 4. lépésre.  
 
    Ha véletlenül koppint a **Mellőzés**lehetőségre, frissítse a lapot. A rendszer felszólítja, hogy nyissa meg a Céges portál alkalmazást. Ha már ott van, koppintson **ismét a letöltés**gombra.

  > [!NOTE]
  > A felügyeleti profilt a letöltés után 8 percen belül a következő lépésekben leírtak szerint kell telepítenie. Ha nem, a profil el lesz távolítva, és újra kell indítania a beléptetést.  

3. Amikor a rendszer rákérdez a Céges portál megnyitására, koppintson a **Megnyitás**gombra. Olvassa el a **felügyeleti profil telepítése** képernyő információit.  

4. Nyissa meg a beállítások alkalmazást, és koppintson a **regisztrálás elemre < szervezet neve >** vagy a **profil letöltése**elemre.  

    ![Példa a Settings (beállítások) alkalmazás képernyőképére a céges beállításban.](./media/enroll-in-organization-ios-1909.PNG)  

   Ha egyik lehetőség sem jelenik meg, nyissa meg az **általános** > **profilok & eszközkezelés**> **felügyeleti profilt**. Ha továbbra sem látja a felügyeleti profilt, előfordulhat, hogy újra le kell töltenie.  

5. Koppintson a **Telepítés** elemre.  
    
6. Adja meg az eszköz jelszavát. Ezután koppintson a **telepítés**gombra.    

7. A következő képernyő egy szabványos rendszer-figyelmeztetés az eszközkezelés terén. A telepítés folytatásához koppintson a **telepítés**gombra. Ha a rendszer felszólítja a Távoli felügyelet megbízhatóságára, koppintson a **megbízhatóság**elemre.  

8. A telepítés befejezése után koppintson a **kész**gombra. Annak ellenőrzéséhez, hogy a profil telepítve van-e, nyissa meg a **profilok & eszköz-felügyeleti** beállítások lapot. A profilt a **mobileszköz-kezelés**területen találja.   

    ![Példa a beállítások alkalmazás képernyőképére, a profilok & Az eszközkezelés beállításai elemre, amely a felügyeleti profilt mutatja.](./media/ios-12-cp-enroll-1904.PNG)  

9. Térjen vissza a Céges portál alkalmazáshoz. Céges portál megkezdi az eszköz szinkronizálását és beállítását. Előfordulhat, hogy a Céges portál további eszközbeállítások frissítését kéri. Ha igen, koppintson a **Folytatás**gombra.  

10. Tudni fogja, hogy a beállítás akkor fejeződik be, ha a lista összes eleme zöld pipa jelenik meg. Koppintson a **Kész** gombra.   

> [!Note]
> Ha a szervezete figyeli a hang-és adatkorlátokat, vagy a vállalat által birtokolt eszközt is tartalmaz, előfordulhat, hogy néhány további lépést is végre kell hajtania. Ha a rendszer kéri, hogy telepítse a **Datalert** alkalmazást, tekintse [meg az eszköz regisztrálása a távközlési költségek kezelése](enroll-your-device-with-telecom-expense-management-ios.md)című témakört. Ha a szervezete az Apple Készülékregisztrációs program részét képezi, tájékozódjon [a vállalati tulajdonú eszközök regisztrálásáról](enroll-your-device-dep-ios.md).  

### <a name="secure-work-related-apps-and-data"></a>Biztonságos munkavégzéssel kapcsolatos alkalmazások és adat  
1. Megjelenik a **Microsoft Authenticator letöltése** képernyő (ha már van hitelesítő, a képernyő nem jelenik meg, így ugorjon a 2. lépésre).  
    1. Koppintson **a letöltés az App Store áruházból**elemre.
    2. Az alkalmazás-áruház megnyitásakor telepítse az alkalmazást. 
    3. Térjen vissza Céges portálhoz, és koppintson a **Folytatás**gombra.    
    
   A Microsoft Authenticator telepítése után nem kell mást tennie az alkalmazással. Csak be kell lennie az eszközön. 

   ![Példa a Céges portál "Microsoft Authenticator letöltése" képernyő képernyőképére.](./media/download-ms-authenticator-1909.PNG)  

2. Az **eszközkezelés és adatvédelem** képernyőn olvassa el a szervezet által megjelenített és nem látható eszközök adatainak listáját. Ezután koppintson a **Folytatás**gombra.  


 > [!IMPORTANT]
> A következő lépések és képernyők az iOS-verziótól függően eltérőek lesznek. Kövesse az iOS-verziójának lépéseit. 

3. A Safari megnyitja a Céges portál webhelyét az eszközön. Amikor a rendszer kéri, hogy töltse le a konfigurációs profilt, koppintson az **Engedélyezés**elemre. Ha olyan eszközt használ, amely a következőket futtatja:  
    * iOS 12,2 és újabb verziók: Ha a letöltés befejeződött, koppintson a **Bezárás**gombra. Ezután folytassa a 4. lépéssel.  
    * iOS 12,1 és korábbi verziók: Ha a letöltés befejeződött, a rendszer automatikusan átirányítja a beállítások alkalmazásba. Ugorjon az 5. lépésre.  
 
    Ha véletlenül koppint a **Mellőzés**lehetőségre, frissítse a lapot. A rendszer felszólítja, hogy nyissa meg a Céges portál alkalmazást. Az alkalmazásból koppintson a **Letöltés újra**lehetőségre.

  > [!NOTE]
  > A felügyeleti profilt a letöltés után 8 percen belül a következő lépésekben leírtak szerint kell telepítenie. Ha nem, a profil el lesz távolítva, és újra kell indítania a beléptetést.  

4. Amikor a rendszer rákérdez a Céges portál megnyitására, koppintson a **Megnyitás**gombra. Olvassa el a **felügyeleti profil telepítése** képernyő információit. 

5. Nyissa meg a beállítások alkalmazást, és koppintson a **regisztrálás elemre < szervezet neve >** vagy a **profil letöltése**elemre.  

    ![Példa a Settings (beállítások) alkalmazás képernyőképére a céges beállításban.](./media/enroll-in-organization-ios-1909.PNG)  

   Ha egyik lehetőség sem jelenik meg, nyissa meg az **általános** > **profilok & eszközkezelés**> **felügyeleti profilt**. Ha továbbra sem látja a felügyeleti profilt, előfordulhat, hogy újra le kell töltenie.   


6. A **felhasználó beléptetése** képernyőn koppintson **az iPhone-regisztráció regisztrálása**elemre.  

    ![Példa a beállítások alkalmazás, a felhasználó beléptetése képernyő, a regisztráció gomb kiemelése képernyőképre.](./media/user-enrollment-information-1909.PNG)  

7. Adja meg az eszköz jelszavát. Ezután koppintson a **telepítés**gombra.  

8. A **Bejelentkezés** képernyőn adja meg a felügyelt Apple ID azonosítóhoz tartozó jelszót. A legtöbb esetben ezek a hitelesítő adatok ugyanazok, mint a munkahelyi vagy iskolai fiókjába való bejelentkezéshez, kivéve, ha a szervezete eltérő hitelesítő adatokat adott meg. 
9. Koppintson **a bejelentkezés**elemre.  
10. Egy sikeres üzenet jelenik meg a képernyőn röviden a profil telepítése után. A profil telepítésének ellenőrzéséhez lépjen a **profilok & eszközkezelés** beállítások elemre. A profilt a **mobileszköz-kezelés** területen találja.  

    ![Példa a beállítások alkalmazás képernyőképére, a profilok & Az eszközkezelés beállításai elemre, amely a felügyeleti profilt mutatja.](./media/ios-12-cp-enroll-1904.PNG)  

11. Térjen vissza a Céges portál alkalmazáshoz. Céges portál megkezdi az eszköz szinkronizálását és beállítását. Előfordulhat, hogy a Céges portál további eszközbeállítások frissítését kéri. Ha igen, koppintson a **Folytatás**gombra.    

12. Tudni fogja, hogy a beállítás akkor fejeződik be, ha a lista összes eleme zöld pipa jelenik meg. Koppintson a **kész**gombra.  

## <a name="it-administrator-support"></a>INFORMATIKAI rendszergazda támogatása  
Ha Ön rendszergazda, és az eszközök regisztrálása során problémákba kerül, tekintse meg [az iOS-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Ez a cikk a gyakori hibákat, azok okait és a megoldás lépéseit sorolja fel.  

## <a name="next-steps"></a>További lépések  
Olyan alkalmazásokat kereshet, amelyek segítséget nyújtanak a munkahelyi vagy iskolai munkához. Ismerje meg, [Hogyan érhetők el az alkalmazások](use-managed-apps-on-your-device-ios.md) céges portálon keresztül.  

További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához. A kapcsolatfelvételi adatait megtalálja a [Munkahelyi portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
