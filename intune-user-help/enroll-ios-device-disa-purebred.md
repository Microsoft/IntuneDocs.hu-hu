---
title: IOS-vagy iPadOS-eszköz regisztrálása a Intune Céges portál és a DISA fajtiszta eszközzel
description: Megtudhatja, hogyan regisztrálhat iOS-vagy iPadOS-eszközöket, és hogyan állíthat be származtatott hitelesítő adatokat a DISA fajtatiszta használatával.
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
ms.openlocfilehash: 5c484b98466c1418016f4ebc6cc805e412d7891e
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415597"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>IOS-vagy iPadOS-eszköz beállítása Céges portál és DISA fajtiszta eszközzel  

Regisztrálja az eszközt a Intune Céges portál alkalmazással, hogy biztonságos, mobil hozzáférést nyerjen a szervezete e-mailjeit, fájljait és alkalmazásait. Az eszköz regisztrálása után a rendszer *felügyeli*. A szervezet a mobileszköz-felügyeleti (MDM-) szolgáltatón (például az Intune-on) keresztül rendelhet szabályzatokat és alkalmazásokat az eszközhöz.  

A regisztráció során a rendszer egy származtatott hitelesítő adatot is telepít az eszközre. Előfordulhat, hogy a szervezete a származtatott hitelesítő adatokat hitelesítési módszerként használja az erőforrások elérésekor, illetve az e-mailek aláírásához és titkosításához. 

Ha intelligens kártyát használ a következőhöz, akkor valószínűleg származtatott hitelesítő adatokat kell beállítania:

* Bejelentkezés az iskolai vagy munkahelyi alkalmazásokhoz, Wi-Fi-és virtuális magánhálózatok (VPN)
* Iskolai vagy munkahelyi e-mailek aláírása és titkosítása S/MIME-tanúsítványok használatával  

Ebben a cikkben a következőket fogja megtekinteni:  

   * Mobil iOS-vagy iPadOS-eszköz regisztrálása a Intune Céges portál.  
   * Származtatott hitelesítő adatok beszerzése a szervezet származtatott hitelesítőadat-szolgáltatójából, a [DISA fajtatiszta](https://cyber.mil/pki-pke/purebred/).  

## <a name="what-are-derived-credentials"></a>Mik azok a származtatott hitelesítő adatok?  
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

A telepítés során is kapcsolatba kell lépnie egy fajtiszta ügynökkel vagy képviselővel.      

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
    a. Koppintson a szervezete által beállított utasításokra mutató hivatkozásra. Ha a szervezet nem nyújt további útmutatást, ezt a cikket küldi el.  
    b. Kattintson a **Megnyitás** gombra a fajtatiszta alkalmazás megnyitásához.  

    ![Példa a mobil intelligens kártya hozzáférési képernyőjének beállítására szolgáló Céges portál képernyőképre.](./media/smart-card-open-disa-purebred.png)  
9. Amikor a rendszer rákérdez, hogy engedélyezi-e a Céges portál számára a fajtatiszta regisztrációs alkalmazás megnyitását, válassza a **Megnyitás**lehetőséget.   

    ![Példa a Céges portál promptjának képernyőképére a DISA fajtatiszta alkalmazás megnyitásához.](./media/open-app-prompt-disa-purbred.png)  
10. Ha az alkalmazás működik, működjön együtt a szervezete fajtiszta ügynökével a fajtatiszta előzetes regisztrációs konfigurációs profil konfigurálásához és letöltéséhez.   
11. Nyissa meg a beállítások alkalmazást > **általános** > **profilok & eszközkezelés** > **telepítse a profilt** , és koppintson a **telepítés**elemre.  
12. Adja meg az eszköz PIN-kódját.  
13. Telepítse a profilt. Előfordulhat, hogy a telepítés elindításához többször is meg kell koppintani a **telepítés** lehetőségre. 
14. Térjen vissza a fajtatiszta regisztrációs alkalmazáshoz. A folytatáshoz kövesse a fajtatiszta ügynök utasításait.  
 
15. A konfigurációs profil letöltése után lépjen a beállítások alkalmazás > **általános** > **profilok & eszközkezelés** > **telepítési profil** elemre, és koppintson a **telepítés**gombra.   
16.  Adja meg az eszköz PIN-kódját.
17. Telepítse a profilt. Előfordulhat, hogy a telepítés elindításához többször is meg kell koppintani a **telepítés** lehetőségre. 
18. A telepítés befejezése után térjen vissza a Céges portál alkalmazáshoz.  
19.  A **mobil intelligens kártya elérésének beállítása** képernyőn koppintson a **Folytatás**elemre.  

20. A **tanúsítványok importálása** képernyőn le kell kérnie és importálnia kell a DISA fajtiszta-ból kapott származtatott hitelesítő adatokat.  

    a. Koppintson a **Tovább** gombra.   

    ![például képernyőkép a Céges portál tanúsítványok importálása képernyőről.](./media/import-certificate-disa-purebred.png)  
    b. Lépjen az iCloud-meghajtó **tallózás** > **helyeire** , és koppintson a **további helyszínek**lehetőségre.  

    ![példa az iCloud meghajtóra, majd a további helyszínek kiemelése lehetőségre.](./media/icloud-drive-more-locations.png)  
    c. Koppintson a kapcsolóra a **fajtatiszta kulcstartó**engedélyezéséhez.  

    ![Példa az iCloud meghajtóra, a Tallózás nézetre, és kiemeli, hogy a fajtatiszta kulcstartó-kapcsoló engedélyezve van.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. Koppintson a **fajtatiszta hitelesítőadat-csomag**elemre.  

    ![egy iOS-képernyő képernyőképét egy választható fajtatiszta hitelesítőadat-csomag lehetőséggel.](./media/purebred-credential-package.png)  
    f. Megjelenik a tanúsítványok listája. Válasszon ki egyet, majd koppintson az **importálási kulcs**elemre.  

    ![Példa képernyőképre a választható tanúsítványok listájáról, egy már kiválasztott lehetőséggel.](./media/import-purebred-keychain.png) 
21. Térjen vissza a Céges portál alkalmazáshoz, és várjon, amíg a Céges portál befejezi az eszköz beállítását.   

## <a name="next-steps"></a>További lépések  
A regisztráció befejezését követően hozzáférhet a munkahelyi erőforrásokhoz, például az e-mailekhez, a Wi-Fi-hez és a szervezet által elérhetővé vált alkalmazásokhoz. További információ az alkalmazások beszerzéséről, kereséséről, telepítéséről és eltávolításáról a Céges portál:

* [Alkalmazások kezelése a Céges portál webhelyről](manage-apps-cpweb.md)  
* [Felügyelt alkalmazások használata az eszközön](use-managed-apps-on-your-device-ios.md)  

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
