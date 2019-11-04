---
title: IOS-vagy iPadOS-eszköz regisztrálása Intune Céges portál és Entrust Datacard
description: IOS-vagy iPadOS-eszköz regisztrálása és származtatott hitelesítőadat-hitelesítés beállítása Entrust Datacard használatával.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfafa4f35d0b8f1255d66a70c3f7cd0acf01a889
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415589"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-entrust-datacard"></a>IOS-vagy iPadOS-eszköz beállítása Céges portál és Entrust Datacard

Regisztrálja az eszközt a Intune Céges portál alkalmazással, hogy biztonságos, mobil hozzáférést nyerjen a szervezete e-mailjeit, fájljait és alkalmazásait. Az eszköz regisztrálása után a rendszer *felügyeli*. A szervezet a mobileszköz-felügyeleti (MDM-) szolgáltatón (például az Intune-on) keresztül rendelhet szabályzatokat és alkalmazásokat az eszközhöz.  

A regisztráció során a rendszer egy származtatott hitelesítő adatot is telepít az eszközre. Előfordulhat, hogy a szervezete a származtatott hitelesítő adatokat hitelesítési módszerként használja az erőforrások elérésekor, illetve az e-mailek aláírásához és titkosításához. 

Ha intelligens kártyát használ a következőhöz, akkor valószínűleg származtatott hitelesítő adatokat kell beállítania:  

* Bejelentkezés az iskolai vagy munkahelyi alkalmazásokhoz, Wi-Fi-és virtuális magánhálózatok (VPN)
* Iskolai vagy munkahelyi e-mailek aláírása és titkosítása S/MIME-tanúsítványok használatával  

Ebben a cikkben a következőket fogja megtekinteni:  

   * Mobil iOS-vagy iPadOS-eszköz regisztrálása a Intune Céges portál.  
   * Származtatott hitelesítő adatok beszerzése a szervezet származtatott hitelesítőadat-szolgáltatójából, [Entrust DataCard](https://www.entrustdatacard.com/).  

### <a name="what-are-derived-credentials"></a>Mik azok a származtatott hitelesítő adatok?  
A származtatott hitelesítő adatok olyan tanúsítványok, amelyek az intelligens kártyás hitelesítő adataiból származnak, és telepítve vannak az eszközön. Távelérést biztosít a munkahelyi erőforrásokhoz, miközben megakadályozza a jogosulatlan felhasználók számára a bizalmas adatok elérését.  

A származtatott hitelesítő adatok a következők: 
* Olyan tanulók és alkalmazottak hitelesítése, akik bejelentkeznek az iskolai vagy munkahelyi alkalmazásokba, Wi-Fi-re és VPN-re
* Iskolai vagy munkahelyi e-mailek aláírása és titkosítása S/MIME-tanúsítványokkal

A származtatott hitelesítő adatok a National Institute of Standards and Technology (NIST) irányelvek megvalósítása a származtatott személyes identitás-ellenőrzési (PIV) hitelesítő adatokhoz a speciális kiadvány (SP) 800-157-es részeként.  

## <a name="prerequisites"></a>Előfeltételek

 A regisztráció befejezéséhez a következőket kell tennie:

* Iskolai vagy munkahelyi intelligens kártya
* Hozzáférés egy számítógéphez vagy kioszkhoz, ahol bejelentkezhet az intelligens kártyával
* Mobileszköz
* Az eszközre telepített iOS-és iPadOS Intune Céges portál alkalmazás  


## <a name="enroll-device"></a>Eszköz regisztrálása  
1. Nyissa meg az iOS/iPadOS Céges portál alkalmazást a mobileszközön, és jelentkezzen be a munkahelyi fiókjával.  

2. Írja le a képernyőn megjelenő kódot.  

    ![Példa Céges portál alkalmazás képe a képernyőn megjelenő üzenettel és kóddal.](./media/copy-code-intercede.png)   

3. Váltson az intelligens kártyával kompatibilis eszközre, és lépjen a https://microsoft.com/devicelogin. 
4. Adja meg a korábban írt kódot.  

    ![Példa a Céges portál webhely "kód beírása" üzenetére.](./media/enter-code-intercede.png)   

5. Szúrja be az intelligens kártyát a bejelentkezéshez.   
6. Térjen vissza a mobileszköz Céges portál alkalmazásához, és kövesse a képernyőn megjelenő utasításokat az eszköz regisztrálásához.  
7. A beléptetés befejezése után Céges portál értesíti az intelligens kártya beállításáról. Koppintson az értesítésre. Ha nem kap értesítést, ellenőrizze az e-mailjeit.   

    ![Példa az eszköz kezdőképernyő Céges portál leküldéses értesítésére szolgáló képernyőképre.](./media/action-required-in-app-intercede.png)  

8. A **mobileszköz-hozzáférés beállítása** képernyőn:   
    a. Koppintson a szervezet telepítési utasításainak hivatkozására. Ha a szervezet nem nyújt további útmutatást, ezt a cikket küldi el.  
    b. Koppintson a **kezdés**elemre.  

    ![Példa a mobil intelligens kártya hozzáférési képernyőjének beállítására szolgáló Céges portál képernyőképre.](./media/smart-card-info-intercede.png)

9. Váltson az intelligens kártya használatára képes eszközre, és nyissa meg a IdentityGuard. 
10. Keresse meg az intelligens hitelesítő adatok bejelentkezési felületét, és válassza a bejelentkezés gombot.  
11. Amikor a rendszer rákérdez a tanúsítvány kiválasztására, válassza ki az intelligens kártya hitelesítő adatait. Ezután kattintson **az OK gombra**. 
12. Adja meg az intelligens kártya PIN-kódját.  
13. A rendszer arra kéri, hogy válasszon a műveletek listájáról. Válassza ki azt a lehetőséget, amely lehetővé teszi egy származtatott mobil intelligens hitelesítő adat regisztrálását. Előfordulhat, hogy a hivatkozás vagy a gomb azt jelenti, **hogy egy származtatott mobil intelligens kártya hitelesítő adatait szeretnék regisztrálni.**  
14. Válassza ki, hogy sikeresen letöltötte és telepítette az intelligens hitelesítőadat-kompatibilis alkalmazást. Ezután folytassa a következő képernyővel.   
15. Adja meg a származtatott intelligens kártya hitelesítő adatait.  
    a. Az Identity Name (identitás neve) mezőben adjon meg egy tetszőleges nevet, például egy *származtatott cred*-t.  
    b. A legördülő menüben válassza a **IdentityGudard Mobile intelligens hitelesítő adatok megbízza**lehetőséget.  
    c. Folytassa a következő képernyővel. A QR-kódot egy numerikus jelszóval láthatja.  

16. Térjen vissza a mobil eszközre. A > Céges portál **QR-kód beolvasása** képernyőn koppintson a **Folytatás**gombra. 

    ![Példa a QR-kód beolvasása képernyő Céges portál képernyőképére.](./media/get-qr-code-intercede.png)  
17. Koppintson a **kamera használata** > **OK gombra**.  

    ![Példa a Céges portál prompt képernyőképére, amely a kamera-hozzáférés engedélyezését kéri.](./media/allow-cp-camera-access-intercede.png)  
18. Ellenőrizze az intelligens kártyával kompatibilis eszközön található QR-kód képét.  
19. Adja meg a QR-kód alatt megjelenő numerikus jelszót.  

    ![Példa a jelszó megadásához szükséges Céges portál képernyőképre, írja be a jelszó mezőt.](./media/enter-password-derived-credentials.png)   

20. Várjon, amíg a Céges portál befejezi az eszköz beállítását.  


## <a name="next-steps"></a>További lépések  
A regisztráció befejezését követően hozzáférhet a munkahelyi erőforrásokhoz, például az e-mailekhez, a Wi-Fi-hez és a szervezet által elérhetővé vált alkalmazásokhoz. További információ az alkalmazások beszerzéséről, kereséséről, telepítéséről és eltávolításáról a Céges portál:

* [Alkalmazások kezelése a Céges portál webhelyről](manage-apps-cpweb.md)  
* [Felügyelt alkalmazások használata az eszközön](use-managed-apps-on-your-device-ios.md)  

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  
