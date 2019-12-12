---
title: Vállalati eszköz regisztrálása a Microsoft Intune alkalmazással | Microsoft Docs
description: Útmutató vállalati Android-eszköz regisztrálásához az Intune-ban
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/07/2019
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81c842eb27b1b9131c164ced5aeed86a78a37353
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506293"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Vállalati eszköz regisztrálása a Microsoft Intune alkalmazással

Regisztrálja vállalati tulajdonú Android-eszközét, hogy biztonságos hozzáférést kapjon a vállalati e-mailekhez, alkalmazásokhoz és egyéb, a szervezet által elérhetővé vált információhoz. A Microsoft Intune alkalmazás az Android 6,0-es vagy újabb verzióját futtató vállalati tulajdonú eszközöket támogatja. A regisztráció során a rendszer automatikusan telepíti az új és a gyári beállítások visszaállítására szolgáló eszközöket. 

Négyféle módon regisztrálhat. A szervezetnek tudnia kell, hogy melyik lehetőséget kell használni.
 
* Kis hatótávolságú kommunikáció (NFC)  
* Azonosító  
* QR-kód   
* Google Zero Touch  

## <a name="enroll-device"></a>Eszköz regisztrálása 
Az eszköz beállításához és regisztrálásához hajtsa végre az alábbi lépéseket.  

> [!NOTE]
> Előfordulhat, hogy az Android-verzió vagy-eszköz gyártója a jelen eljárásban nem szereplő további lépéseket kell végrehajtania. A képernyőképen megjelenő színek és szövegek is eltérőek lehetnek az eszközön.  

1. Kapcsolja be az új vagy a gyári beállítások visszaállítására szolgáló eszközt.  
2. Az **Üdvözlőképernyőn** válasszon nyelvet.   Ha arra utasította, hogy egy QR-kóddal vagy NFC-sel regisztrálja magát, kövesse az alábbi lépéseket, amely megfelel a metódusnak.  
     * NFC: koppintson az NFC által támogatott eszközre egy programozói eszközön a szervezet hálózatához való kapcsolódáshoz. Kövesse a képernyőn megjelenő utasításokat. Amikor eléri a Chrome szolgáltatási feltételeinek képernyőjét, folytassa az 5. lépéssel.  

     * QR-kód: hajtsa végre a [QR-kód beléptetésének](#qr-code-enrollment)lépéseit.  

     Ha arra utasította, hogy használjon egy másik módszert, folytassa a 3. lépéssel.    

3. Kapcsolódjon a Wi-Fi-hez, és koppintson a **tovább**gombra. Kövesse a beléptetési módszernek megfelelő lépést. 

    * Jogkivonat: Ha a Google bejelentkezési képernyőjére lép, hajtsa végre a [jogkivonat-regisztráció](#token-enrollment)lépéseit.  
    * Google Zero Touch: a Wi-Fi-hez való csatlakozás után az eszközt a szervezet felismeri. Folytassa a 4. lépéssel, és kövesse a képernyőn megjelenő utasításokat, amíg a telepítés be nem fejeződik.    
 
       ![Példa a Google-használati feltételek képernyő képére, ha a Google Zero Touch használatát látja, kiemelve az elfogadás & folytatás gombot.](./media/google-zero-touch-intune-app-01.png)   
   
4. Tekintse át a Google használati feltételeit. Ezután koppintson az **elfogadás & folytatás**gombra.  

      ![Példa a Google feltételek képernyőre, és válassza ki az elfogadás & folytatás gombot.](./media/fully-managed-intune-app-04.png)   

6. Tekintse át a Chrome szolgáltatási feltételeit. Ezután koppintson az **elfogadás & folytatás**gombra.  

   ![Példa a Chrome használati feltételeinek képére, és válassza ki az elfogadás & folytatás gombot.](./media/fully-managed-intune-app-06.png)   

7. A bejelentkezési képernyőkön jelentkezzen be munkahelyi vagy iskolai fiókjával.   

    a. Adja meg az e-mail címét, és koppintson a **Tovább gombra**.      
    b. Adja meg a jelszót, és koppintson **a bejelentkezés**elemre.  

8. A szervezet követelményeitől függően előfordulhat, hogy a rendszer kérni fogja a beállítások, például a képernyőfelvétel vagy a titkosítás módosítását. Ha ezeket az utasításokat látja, koppintson a **beállítás** elemre, és kövesse a képernyőn megjelenő utasításokat.  

   ![Példa a munkahelyi telefon beállítása képernyőre, a Set gomb kiemelése gombra.](./media/fully-managed-intune-app-10.png)   

9. Ha munkahelyi alkalmazásokat szeretne telepíteni az eszközére, koppintson a **telepítés**gombra. A telepítés befejezése után koppintson a **Tovább gombra**.  

   ![Példa a munkahelyi telefon beállítása képernyőre, a telepítés kiemelése gombra.](./media/fully-managed-intune-app-11.png)   

10. A **Start** gombra koppintva nyissa meg a Microsoft Intune alkalmazást, és regisztrálja az eszközt. 

    ![Példa a munkahelyi telefon beállítása képernyőre, kiemelve a Start gombot.](./media/fully-managed-intune-app-17.png)   

11. Koppintson **a bejelentkezés** elemre, és koppintson a **tovább** gombra a regisztráció megkezdéséhez. Ha megjelenik a regisztráció befejezését jelző üzenet, koppintson a **kész**gombra.  

    ![Példa a hozzáférés beállítása, az eszköz regisztrálása képernyő, a kész gomb kiemelése gombra.](./media/fully-managed-intune-app-19.png)   

10. Ha megjelenik az eszközön a kész üzenet, koppintson a **kész**gombra.  

    ![Példa a munkahelyi telefon beállítása képernyőre, kiemelve a kész gombot.](./media/fully-managed-intune-app-18.png)   

Ha nem sikerül hozzáférni a szervezet erőforrásaihoz, előfordulhat, hogy további beállításokat kell frissítenie az eszközön. A szükséges frissítések kereséséhez jelentkezzen be a Microsoft Intune alkalmazásba.   


## <a name="qr-code-enrollment"></a>QR-kód beléptetése  
Ebben a szakaszban átvizsgálja a vállalat által megadott QR-kódot.  Ha elkészült, a rendszer visszairányítja Önt az eszközök regisztrálási lépéseire.     
  
1. Az **üdvözlőképernyőn** koppintson a képernyő ÖTSZÖR a QR-kód telepítésének elindításához.  

   ![Példa az eszközbeállítások üdvözlő képernyőjének képére, kiemelve a képernyőn megjelenő utasításokat.](./media/qr-code-intune-app-01.png)  

2. A Wi-Fi-hez való csatlakozáshoz kövesse a képernyőn megjelenő utasításokat.  
3. Ha az eszköz nem rendelkezik QR-kóddal, a telepítő képernyőjén látható, hogy a képolvasó telepítése folyamatban van. Várjon, amíg a telepítés befejeződik.  
4. Amikor a rendszer kéri, ellenőrizze a beléptetési profil QR-kódját, amelyet a szervezet adott Önnek.  
5. Térjen vissza az [eszköz regisztrálásához](#enroll-device), 4. lépés a telepítés folytatásához.  

## <a name="token-enrollment"></a>Jogkivonat-regisztráció  
Ebben a szakaszban meg kell adnia a vállalat által biztosított tokent. Ha elkészült, a rendszer visszairányítja Önt az eszközök regisztrálási lépéseire.  

1. A Google bejelentkezési képernyőjének **e-mail vagy telefon** mezőjébe írja be a következőt: **AFW # Setup**. Koppintson a **Következő** elemre. 

   ![Példa a Google bejelentkezési képernyőjének képére, amely azt mutatja, hogy a "AFW # Setup" bekerül a mezőbe.](./media/token-intune-app-01.png)   

2. Válassza a **telepítés** lehetőséget az **Android-eszköz házirend** alkalmazáshoz. Folytassa a telepítést. Az eszköztől függően előfordulhat, hogy további feltételeket kell áttekintenie és elfogadnia.    

3. Az **eszköz regisztrálása** képernyőn válassza a **tovább**lehetőséget.  

4. Válassza a **kód megadása**lehetőséget.  

5. A **vizsgálat vagy a kód megadása** képernyőn írja be azt a kódot, amelyet a szervezet adott meg.  Ezután kattintson a **Tovább**gombra.  

   ![Példa a vizsgálatra vagy a kód beírása képernyőre, majd a Tovább gombra.](./media/token-intune-app-04.png)  

6. Térjen vissza az [eszköz regisztrálásához](#enroll-device), 4. lépés a telepítés folytatásához.  



## <a name="next-steps"></a>További lépések   
További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához (a kapcsolattartási adatokat a [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja), vagy írjon a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-csapatának</a>.  
