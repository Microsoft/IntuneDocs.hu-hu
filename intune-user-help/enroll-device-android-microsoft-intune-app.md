---
title: Vállalati eszköz regisztrálása a Microsoft Intune alkalmazással | Microsoft Docs
description: Útmutató vállalati Android-eszköz regisztrálásához az Intune-ban
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: b23323766e91e31c48aec6a51dfae971c3a333e8
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735757"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Vállalati eszköz regisztrálása a Microsoft Intune alkalmazással

Regisztrálja vállalati tulajdonú Android-eszközét, hogy biztonságos hozzáférést kapjon a vállalati e-mailekhez, alkalmazásokhoz és egyéb, a szervezet által elérhetővé vált információhoz. A Microsoft Intune alkalmazás az Android 6,0-es vagy újabb verzióját futtató vállalati tulajdonú eszközöket támogatja. A regisztráció során a rendszer automatikusan telepíti az új és a gyári beállítások visszaállítására szolgáló eszközöket. 

Négyféle módon regisztrálhat. A szervezetnek tudnia kell, hogy melyik lehetőséget kell használni.
 
* Kis hatótávolságú kommunikáció (NFC)  
* Jogkivonat  
* QR-kód   
* Google Zero Touch  

## <a name="enroll-device"></a>Eszköz regisztrálása 
Az eszköz beállításához és regisztrálásához hajtsa végre az alábbi lépéseket.  

> [!NOTE]
> Előfordulhat, hogy az Android-verzió vagy-eszköz gyártója a jelen eljárásban nem szereplő további lépéseket kell végrehajtania. A képernyőképen megjelenő színek és szövegek is eltérőek lehetnek az eszközön.  

1. Kapcsolja be az új vagy a gyári beállítások visszaállítására szolgáló eszközt.  
2. Az **Üdvözlőképernyőn** válasszon nyelvet.   Ha arra utasította, hogy egy QR-kóddal vagy NFC-sel regisztrálja magát, kövesse az alábbi lépéseket, amely megfelel a metódusnak.  
     * NFC: Koppintson az NFC által támogatott eszközre egy programozó eszközön a szervezet hálózatához való kapcsolódáshoz. Kövesse a képernyőn megjelenő utasításokat. Amikor eléri a Chrome szolgáltatási feltételeinek képernyőjét, folytassa az 5. lépéssel.  

     * QR-kód: Hajtsa végre a [QR-kód](#qr-code-enrollment)beléptetésének lépéseit.  

     Ha arra utasította, hogy használjon egy másik módszert, folytassa a 3. lépéssel.    

1. Kapcsolódjon a Wi-Fi-hez, és koppintson a **tovább**gombra. Kövesse a beléptetési módszernek megfelelő lépést. 

    * Jogkivonat A Google bejelentkezési képernyőjének beszerzéséhez hajtsa végre a [jogkivonat-regisztráció](#token-enrollment)lépéseit.    
    * Google Zero Touch: A Wi-Fi-hez való csatlakozás után az eszközt a szervezet felismeri. Folytassa a 4. lépéssel, és kövesse a képernyőn megjelenő utasításokat, amíg a telepítés be nem fejeződik.    
 
       ![Példa a Google-használati feltételek képernyő képére, ha a Google Zero Touch használatát látja, kiemelve az elfogadás & folytatás gombot.](./media/google-zero-touch-intune-app-01.png)   
   
4. Tekintse át a Google használati feltételeit. Ezután koppintson az **elfogadás &AMP; folytatás**gombra.  

      ![Példa a Google feltételek képernyőre, és válassza ki az elfogadás & folytatás gombot.](./media/fully-managed-intune-app-04.png)   

6. Tekintse át a Chrome szolgáltatási feltételeit. Ezután koppintson az **elfogadás &AMP; folytatás**gombra.  

   ![Példa a Chrome használati feltételeinek képére, és válassza ki az elfogadás & folytatás gombot.](./media/fully-managed-intune-app-06.png)   

7. A bejelentkezési képernyőkön jelentkezzen be munkahelyi vagy iskolai fiókjával.   

    a. Adja meg az e-mail címét, és koppintson a **Tovább gombra**.      
    b. Adja meg a jelszót, és koppintson **a bejelentkezés**elemre.  

8. A szervezet követelményeitől függően előfordulhat, hogy a rendszer kérni fogja a beállítások, például a képernyőfelvétel vagy a titkosítás módosítását. Ha ezeket az utasításokat látja, koppintson a **beállítás** elemre, és kövesse a képernyőn megjelenő utasításokat.  

   ![Példa a munkahelyi telefon beállítása képernyőre, a Set gomb kiemelése gombra.](./media/fully-managed-intune-app-10.png)   

9. Ha munkahelyi alkalmazásokat szeretne telepíteni az eszközére, koppintson a **telepítés**gombra. A telepítés befejezése után koppintson a **Tovább gombra**.  

   ![Példa a munkahelyi telefon beállítása képernyőre, a telepítés kiemelése gombra.](./media/fully-managed-intune-app-11.png)   

10. Ha az eszköz készen áll az üzenetre, koppintson a **kész**gombra. 

11. Lépjen az alkalmazásaihoz, és nyissa meg a Microsoft Intune alkalmazást. Válassza **a bejelentkezés**lehetőséget. 

12. A **telepítési hozzáférés** képernyőn megjelenik a függőben lévő feladatok listája. Koppintson a **Folytatás**gombra.  

       ![Példa Microsoft Intune alkalmazásra, amely a függőben lévő feladatokat megjelenítő hozzáférési képernyőt jeleníti meg.](./media/fully-managed-intune-app-14.png)   

13. Ha az eszköz regisztrálása befejeződött, koppintson a **Folytatás**gombra. Előfordulhat, hogy a Microsoft Intune további eszközbeállítások frissítését kéri.   

       ![Példa Microsoft Intune alkalmazás képe, az eszközbeállítások képernyő frissítése.](./media/fully-managed-intune-app-15-2.png)   

14. A telepítés akkor fejeződik be, ha a lista minden eleme zöld kört mutat. Mostantól hozzáférhet a céges erőforrásokhoz.  

       ![Példa Microsoft Intune alkalmazás képe, a kitöltött feladatokat megjelenítő hozzáférés képernyő beállítása.](./media/fully-managed-intune-app-16.png)   


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

   ![Példa az eszköz beléptetése képernyőt ábrázoló képre. Egy QR-kód illusztrációjának megjelenítése; kiemeli a Next (tovább) gombot.](./media/token-intune-app-02.png)  

4. Válassza a **kód megadása**lehetőséget.

   ![Példa egy aktív QR-kód beolvasójának képernyőképére. Kiemeli a kód gomb megadását.](./media/token-intune-app-03.png)  

5. A **vizsgálat vagy a kód megadása** képernyőn írja be azt a kódot, amelyet a szervezet adott meg.  Ezután kattintson a **Next** (Tovább) gombra.  

   ![Példa a vizsgálatra vagy a kód beírása képernyőre, majd a Tovább gombra.](./media/token-intune-app-04.png)  

6. Térjen vissza az [eszköz regisztrálásához](#enroll-device), 4. lépés a telepítés folytatásához.  



## <a name="next-steps"></a>További lépések   
További segítségre van szüksége? Forduljon a cég informatikai támogatási szolgálatához (a kapcsolattartási adatokat a [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja), vagy írjon a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-csapatának</a>.  
