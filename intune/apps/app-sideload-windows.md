---
title: Windows-és Windows Phone-telefon-alkalmazások Oldalazva társas viszony
titleSuffix: Microsoft Intune
description: A cikkből megtudhatja, hogyan írhatja alá az üzleti alkalmazásokat, hogy az Intune segítségével telepíthesse őket.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a4c6d40dc729fb72210c455c7819baaf89de3b
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691825"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Üzleti alkalmazások aláírása, hogy telepíteni lehessen őket Windows-eszközökre az Intune segítségével

Intune-rendszergazdaként üzletági (LOB) univerzális alkalmazásokat telepíthet a Windows 8,1 asztali vagy Windows 10 asztali & mobileszközökön, beleértve a Céges portál alkalmazást is. A. Appx alkalmazások Windows 8,1 asztali vagy Windows 10 rendszerű asztali & mobileszközökön való üzembe helyezéséhez a Windows-eszközök által már megbízhatóként használt nyilvános hitelesítésszolgáltatótól származó kód-aláíró tanúsítványt használhat, vagy használhatja saját hitelesítésszolgáltatóját is.

 > [!NOTE]
 > A Windows 8,1 Desktophoz vállalati házirend szükséges a közvetlen telepítési engedélyezéséhez vagy a közvetlen telepítési kulcsok használatához (automatikusan engedélyezve a tartományhoz csatlakoztatott eszközök esetében). További információ: [Windows 8 közvetlen telepítési](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Windows 10 közvetlen telepítési

A Windows 10-es verzióban a közvetlen telepítési eltér a Windows korábbi verzióiban:

- A közvetlen telepítési egy vállalati házirend segítségével oldhatja fel az eszköz zárolását. Az Intune egy "megbízható alkalmazás telepítése" nevű eszköz-konfigurációs szabályzatot biztosít. Ha ezt a beállítást <allow> értékre állítja, akkor a Appx alkalmazás aláírásához használt tanúsítványnak már megbízható eszközökre van szüksége.

- A Symantec Phone-tanúsítványok és a közvetlen telepítési-licenc kulcsa nem szükséges. Ha azonban egy helyszíni hitelesítésszolgáltató nem érhető el, előfordulhat, hogy egy kód-aláíró tanúsítványt kell beszereznie egy nyilvános hitelesítésszolgáltatótól. További információ: [Bevezetés a kód aláírására](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Az alkalmazás kódjának aláírása

Első lépésként írja alá a Appx-csomagot. Részletekért lásd: [alkalmazáscsomag aláírása a SignTool használatával](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Alkalmazás feltöltése

Ezután fel kell töltenie az aláírt Appx fájlt. Részletekért lásd: [Windows rendszerű üzletági alkalmazás hozzáadása Microsoft Intunehoz](lob-apps-windows.md).

Ha a felhasználók vagy eszközök számára szükséges módon telepíti az alkalmazást, akkor nincs szüksége a Inutne Céges portál alkalmazásra. Ha azonban a felhasználók számára elérhetővé teszi az alkalmazást, akkor használhatja a Céges portál alkalmazást a nyilvános Microsoft Storeból, az Céges portál alkalmazást használhatja a vállalati privát Microsoft Store, vagy be kell jelentkeznie és manuálisan telepítenie kell az Intune-céget. Portál alkalmazás.

### <a name="upload-the-code-signing-certificate"></a>A kód aláíró tanúsítványának feltöltése

Ha a Windows 10-es eszköze még nem bízik meg a hitelesítésszolgáltatóban, akkor a Appx-csomag aláírása és az Intune szolgáltatásba való feltöltése után fel kell töltenie a kód aláíró tanúsítványát az Intune-portálra:

1. Kattintson az ügyfélalkalmazások lehetőségre
2. Kattintson a Windows Enterprise-tanúsítványok elemre.
3. Válassza a fájl kiválasztása elemet a kód aláíró tanúsítványa alatt.
4. Válassza ki a. cer fájlt, és kattintson a feltöltés gombra.

Most, hogy az Intune szolgáltatás által Appx üzemelő Windows 10 asztali & mobileszköz automatikusan letölti a megfelelő vállalati tanúsítványt, és az alkalmazás a telepítés után is elindítható.

Az Intune csak a feltöltött legújabb. cer fájlt telepíti. Ha több, a szervezete számára nem társított fejlesztő által létrehozott Appx-fájllal rendelkezik, akkor az aláírás nélküli Appx-fájlokat is meg kell adnia a tanúsítvánnyal való bejelentkezéshez, vagy meg kell adnia nekik a kód által használt aláírási tanúsítványt. a szervezete.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>A Symantec vállalati kódaláíró tanúsítvány megújítása

A Windows Phone-telefon 8,1 Mobile apps üzembe helyezéséhez használt tanúsítvány a 28 2019 februárjában megszűnt, és már nem érhető el a Symantec megújításához. Ha a WIndows 10 Mobile rendszerre végzi a telepítést, a [Windows 10 közvetlen telepítési](app-sideload-windows.md#windows-10-sideloading) utasításait követve továbbra is használhatja a Symantec asztali vállalati kódú aláírási tanúsítványait.

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>A frissített alkalmazások telepítése az üzleti alkalmazások számára

WVPN-profilokdows Phone 8.1

Az Intune szolgáltatás már nem tud LOB-alkalmazásokat telepíteni ehhez a platformhoz, ha a meglévő Symantec Mobile Enterprise-kód-aláíró tanúsítvány lejár. Az aláíratlan XAP/APPX-fájlok Oldalazva társas viszony SD-kártyával vagy a fájlnak az eszközre való letöltésével továbbra is lehetséges. További információ: XAP- [fájlok telepítése Windows Phone-telefonon](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280).

Windows 8,1 asztali/Windows 10 asztali & Mobile

Ha a tanúsítvány időtartama lejárt, a Appx-fájlok elindítása leállhat. Szerezzen be egy új. cer fájlt, és kövesse az utasításokat az egyes telepített Appx-fájlok kódjának aláírásához, majd töltse fel újra az összes Appx-fájlt és a frissített. cer fájlt az Intune-portál Windows Enterprise-tanúsítványok szakaszába.

## <a name="manually-deploy-windows-10-company-portal-app"></a>A Windows 10-es Céges portál alkalmazás manuális telepítése

Ha nem kíván hozzáférést biztosítani a Microsoft Storehoz, manuálisan telepítheti a Windows 10 Céges portál alkalmazást az Intune-ból, még akkor is, ha az Intune-t nem integrálta a vállalati Microsoft Store (MSFB). Ha integrált, akkor a Céges portál alkalmazást a MSFB használatával telepítheti az [alkalmazások telepítése](store-apps-windows.md)használatával.

 > [!NOTE]
 > Ha ezt a lehetőséget választja, manuális frissítést kell végrehajtania minden alkalommal, amikor új frissítés válik elérhetővé az alkalmazáshoz.

1. Jelentkezzen be a fiókjába a [vállalati Microsoft Storeban](https://www.microsoft.com/business-store) , és szerezze be a céges portál alkalmazás **Offline licenccel** rendelkező verzióját.  
2. Miután beszerezte az alkalmazást, válassza ki a **Készlet** lapon.  
3. A **Platform** listából válassza ki a **Windows 10 minden eszközre** lehetőséget, majd válassza ki a megfelelő **architektúrát**, és töltse le az alkalmazást. Ehhez az alkalmazáshoz nincs szükség alkalmazás-licencfájlra.
   a Windows 10-es x86 csomag ![képe a letöltéshez](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Töltse le a „Szükséges keretrendszer” cím alatt található összes csomagot. Ezt az x86, az x64 és az ARM architektúrákkal kell elvégezni, összesen 9 csomaggal, ahogy az alábbi ábrán látható.

   ![Kép a letöltendő függőségi fájlokról ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Mielőtt feltöltené a Céges portál alkalmazást az Intune-ra, hozzon létre egy mappát (pl. C:&#92;Céges portál) a következőképpen felépített csomagokkal:
   1. Helyezze el a Céges portál csomagot a C:\Céges portál helyen. Ugyanitt hozzon létre egy Függőségek almappát is.  
      ![APPXBUN fájllal mentett Függőségek mappa képe](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Helyezze el a kilenc függőségcsomagot a Függőségek mappában.  
      Ha a függőségeket nem ebben a formátumban helyezi el, az Intune nem tudja majd felismerni és feltölteni őket a csomag feltöltésekor, így a folyamat sikertelen lesz a következő hiba miatt.  
      ![Hibaüzenet – meg kell adni a Windows-alkalmazás függőségét.](./media/app-sideload-windows/Win10CP-error-message.png)
6. Lépjen vissza az Intune-ba, és töltse fel a Céges portál alkalmazást új alkalmazásként. Telepítse szükséges alkalmazásként a kívánt felhasználói célcsoport számára.  

Itt talál további információkat arról, hogy az Intune miképpen kezeli az univerzális alkalmazások függőségeit: [appxbundle telepítése függőségekkel a Microsoft Intune MDM-en keresztül](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Hogyan frissítsem a Céges portált olyan felhasználói eszközökön, amelyeken telepítve vannak az áruházból származó régebbi alkalmazások?

Ha a felhasználók már telepítették az áruházból a Windows 8.1-es vagy a Windows Phone 8.1-es Céges portál alkalmazást, az eszközöknek automatikusan, saját vagy felhasználói beavatkozás nélkül is frissíteniük kell az új verzióra. Ha a frissítés elmarad, kérje meg a felhasználókat, hogy ellenőrizzék, engedélyezték-e az áruház-alkalmazások automatikus frissítését az eszközükön.

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hogyan frissítsem a közvetlen telepítésű, Windows 8.1-es Céges portál alkalmazást Windows 10-es Céges portál alkalmazásra?

A javasolt áttelepítési út a Windows 8.1-es Céges portál alkalmazás telepítési műveletének átállítása az „Eltávolítás” lehetőségre, ami törli az alkalmazás telepítését. Miután ez megtörtént, a Windows 10-es Céges portál alkalmazás a fenti lehetőségek bármelyikével telepíthető lesz.  

Ha közvetlenül kell telepíteni az alkalmazást, és a Windows 8.1-es Céges portált a Symantec Tanúsítvány aláírása nélkül telepítette, a frissítéshez kövesse az Intune-on keresztül történő közvetlen telepítés fentebb leírt lépéseit.

Ha közvetlenül kell telepíteni az alkalmazást, és a Windows 8.1-es Céges portált a Symantec kódaláíró tanúsítvány aláírásával telepítette, kövesse az alábbi részben olvasható lépéseket.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hogyan frissítsem az aláírt és közvetlen telepítésű Windows Phone 8.1-es Céges portál alkalmazást vagy Windows 8.1-es Céges portál alkalmazást a Windows 10-es Céges portál alkalmazásra?

A javasolt áttelepítési út a Windows Phone 8.1-es Céges portál alkalmazás vagy a Windows 8.1-es Céges portál alkalmazás telepítési műveletének átállítása az „Eltávolítás” lehetőségre, ami törli az alkalmazás telepítését. Miután ez megtörtént, a Windows 10-es Céges portál alkalmazás a szokásos módon telepíthető.  

Ellenkező esetben a frissítési út betartásának biztosításához a Windows 10-es Céges portál alkalmazás frissítésére és aláírására van szükség.  

Az így aláírt és telepített Windows 10-es Céges portál alkalmazás esetében mindig meg kell ismételni ezt a folyamatot, ha az áruházban elérhetővé válik az alkalmazás új frissítése. Az alkalmazás nem frissül automatikusan az áruház frissítésekor.  

Itt ismertetjük az alkalmazás aláírásának és telepítésének ezt a módját:

1. Töltse le a Microsoft Intune Windows 10-es Céges portál alkalmazás aláírása parancsfájlt a [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) lapról.  A parancsfájlhoz olyan gazdagépre van szükség, amelyen telepítve van a Windows 10-hez készült Windows SDK. A Windows 10 rendszerhez készült Windows SDK letöltéséhez látogasson el a [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296) lapra.
2. Töltse le a Windows 10-es Céges portál alkalmazást a Vállalati Microsoft Áruházból a fenti útmutató szerint.  
3. Futtassa a parancsfájlt azokkal a bemeneti paraméterekkel, amelyek a Windows 10-es Céges portál alkalmazás aláírásához használt parancsfájl fejlécén találhatók (alább kivonatolva). A függőségeket nem kell hozzáadni a parancsprogramhoz. Csak akkor van rájuk szükség, amikor éppen folyamatban van az alkalmazás feltöltése az Intune felügyeleti konzolra.

|       Paraméter       |                                                                    Description                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Az appxbundle forrásfájl elérési útja.                                              |
| OutputWin10AppxBundle |                                                  Az aláírt appxbundle fájl kimeneti útja.                                                  |
|       Win81Appx       |                          A Windows 8.1 vagy Windows Phone 8.1 Céges portál (.APPX) fájl elérési útja.                           |
|      PfxFilePath      |                                   A Symantec vállalati mobil-kódaláíró tanúsítvány (.PFX) fájl elérési útja.                                    |
|      PfxPassword      |                                     A Symantec vállalati mobil-kódaláíró tanúsítvány jelszava.                                      |
|      PublisherId      |      A vállalat gyártóazonosítója. Ha nincs megadva, a program a Symantec Enterprise Mobile Code Signing Certificate tanúsítvány Subject (Tulajdonos) mezőjének értékét használja.       |
|        SdkPath        | A Windows 10-hez készült Windows SDK gyökérmappájának elérési útja. Ezt az argumentumot nem kötelező megadni, és az alapértelmezett értéke ${env:ProgramFiles(x86)}\Windows Kits\10 |

A parancsfájl kimenete a futtatás végeztével a Windows 10-es Céges portál alkalmazás aláírt verziója lesz. Ekkor az Intune-on keresztül telepítheti az alkalmazás aláírt verzióját LOB-alkalmazásként, ami frissíteni fogja a jelenleg telepített verziókat erre a új alkalmazásra.  
