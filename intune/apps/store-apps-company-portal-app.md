---
title: A Windows 10-es Céges portál alkalmazás manuális hozzáadása
titleSuffix: Microsoft Intune
description: Ismerje meg, hogy a dolgozók Hogyan vehetik fel manuálisan a Windows 10-es Céges portál alkalmazást a Microsoft Store a SZÁMÍTÓGÉPére.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32411e513cec9683faf598c8d73d6d803bcddb3d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507108"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>A Windows 10-es Céges portál alkalmazás manuális hozzáadása a Microsoft Intune-nal

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A felhasználók maguk telepíthetik a Microsoft Store-ból a Céges portál alkalmazást eszközkezelés és alkalmazástelepítés céljából. Ha a cég megköveteli a felhasználókhoz való hozzárendelést, a Windows 10-es Céges portál alkalmazás hozzárendelése manuálisan is elvégezhető közvetlenül az Intune-ból. Erre akkor is van lehetőség, ha még nem integrálta az Intune-t a Microsoft Store Vállalatoknak szolgáltatással.

 > [!NOTE]
 > A jelen cikkben ismertetett lehetőség a frissítések manuális hozzárendelését követeli meg minden egyes alkalommal, amikor egy alkalmazás új frissítése jelenik meg.

## <a name="configure-settings-to-show-offline-apps"></a>A beállítások konfigurálása offline alkalmazások megjelenítéséhez
1. Jelentkezzen be a [Microsoft Store Vállalatoknak](https://www.microsoft.com/business-store) szolgáltatásba a rendszergazdai fiókjával.
2. Válassza a **Felügyelet** lapot az ablak tetején.
3. A bal oldali ablaktáblán válassza a **Beállítások** elemet.
4. A **Vásárlási élmény** terület **Offline alkalmazások megjelenítése** beállítását állítsa **Bekapcsolva** értékre.  
    Megjelennek az offline licencelt alkalmazások.

## <a name="download-the-offline-company-portal-app"></a>Az Intune Céges portál alkalmazás letöltése
1. Keresse meg és válassza ki a **Céges portál** alkalmazást.
2. Állítsa a **licenc típusát** **offline-ra**.
3. Válassza **Az alkalmazás letöltése** lehetőséget az offline Céges portál letöltéséhez és a leltárba való felvételéhez.
4. Válassza a **Felügyelet** lehetőséget a **Céges portál** alkalmazáslapján.
5. A **Platform** listából válassza ki a **Windows 10 minden eszközre** lehetőséget, majd válassza ki a megfelelő értékeket a **Minimális verzió**, az **Architektúra** és az **Alkalmazás metaadatainak letöltése** elemekhez. 
6. Ha a fájlt a helyi gépre szeretné menteni, válassza a **Letöltés** lehetőséget a **csomag részletei** területen.

    ![A Windows 10 rendszerű eszközök, amelyekben az architektúra értéke x86, ki van választva](./media/app-sideload-windows/Win10CP-all-devices.png)

7. Töltse le a „Szükséges keretrendszer” cím alatt található összes csomagot a **Letöltés** elem kiválasztásával.  

    Ezt a műveletet az x86, az x64 és az ARM architektúrák esetében kell végrehajtani:<br> 
    *A 1507-as minimális operációsrendszer-verzióként, 12 csomaggal, a 1511-es és a 15 csomag kiválasztásakor a 1607 kiválasztásakor 9 szükséges keretrendszer-csomag található.*

8. Az Azure Portalon található Microsoft Intune-ban töltse fel a Céges portál alkalmazást új alkalmazásként. Az alkalmazás **hozzáadása** panel alkalmazás **típusa** részén az üzletági alkalmazás lehetőség kiválasztásával adhatja hozzá az alkalmazást. Ezután válassza ki az alkalmazáscsomag-fájlt (kiterjesztés. AppxBundle).

9. A **függőségi alkalmazások kiválasztása** területen válassza ki a 7. lépésben letöltött összes függőséget a shift-click paranccsal, és ellenőrizze, hogy a **hozzáadott** oszlop **Igen** értéket jelenít-e meg a szükséges architektúrák esetében.

     > [!NOTE]
     > Ha a függőségek nem lettek hozzáadva, előfordulhat, hogy az alkalmazás nem lesz telepítve a megadott típusú eszközökön.

10. Kattintson **az OK**gombra, adja meg a kívánt **alkalmazás adatait**, majd kattintson a **Hozzáadás**gombra.

11. Rendelje hozzá a Céges portál alkalmazást kötelező alkalmazásként a kiválasztott felhasználói vagy eszközosztály számára.  

További információ az univerzális alkalmazások függőségeinek Intune általi kezeléséről: [Appxbundle telepítése függőségekkel a Microsoft Intune MDM-en keresztül](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

## <a name="frequently-asked-questions"></a>Gyakori kérdések 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Hogyan frissítsem a Céges portál alkalmazást olyan felhasználói eszközökön, amelyeken telepítve vannak az áruházból származó régebbi alkalmazások?
Ha a felhasználók már telepítették a Microsoft Store-ból a Windows 8.1-es vagy a Windows Phone 8.1-es Céges portál alkalmazást, az eszközöknek automatikusan, saját vagy felhasználói beavatkozás nélkül is frissíteniük kell a legújabb verzióra. Ha a frissítés elmarad, kérje meg a felhasználókat, hogy ellenőrizzék, engedélyezték-e a Store-alkalmazások automatikus frissítését az eszközükön.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hogyan frissítsem a közvetlen telepítésű, Windows 8.1-es Céges portál alkalmazást Windows 10-es Céges portál alkalmazásra?
A javasolt migrálási út a Windows 8.1-es Céges portál alkalmazás hozzárendelésének átállítása az **Eltávolítás** lehetőségre, ami törli az alkalmazás hozzárendelését. Miután kiválasztotta ezt a beállítást, elvégezheti a Windows 10-es Céges portál alkalmazás hozzárendelését a korábbiakban említett lehetőségek bármelyikével.  

Ha közvetlenül kell telepíteni az alkalmazást, és a Windows 8.1-es Céges portált a Symantec Tanúsítvány aláírása nélkül rendelte hozzá, a frissítést a cikk korábbi szakaszaiban található lépések végrehajtásával fejezze be.

Ha közvetlenül kell telepíteni az alkalmazást, és a Windows 8.1-es Céges portál alkalmazást a Symantec kódaláíró tanúsítvány aláírásával rendelte hozzá, a következő szakaszban található lépéseket kövesse.

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hogyan frissítsem az aláírt és közvetlen telepítésű Windows Phone 8.1-es Céges portál alkalmazást vagy Windows 8.1-es Céges portál alkalmazást a Windows 10-es Céges portál alkalmazásra?
A javasolt migrálási út a Windows Phone 8.1-es Céges portál alkalmazás vagy a Windows 8.1-es Céges portál alkalmazás hozzárendelésének átállítása az **Eltávolítás** lehetőségre, ami törli az alkalmazás hozzárendelését. Miután kiválasztotta ezt a beállítást, a szokásos módon végezheti el a Windows 10-es Céges portál alkalmazás hozzárendelését.  

Ellenkező esetben a frissítési út betartásának biztosításához a Windows 10-es Céges portál alkalmazás frissítésére és aláírására van szükség.  

Az így aláírt és hozzárendelt Windows 10-es Céges portál alkalmazás esetében mindig meg kell ismételni ezt a folyamatot, ha az áruházban elérhetővé válik az alkalmazás új frissítése. Az alkalmazás nem frissül automatikusan az áruház frissítésekor.  

Itt ismertetjük az alkalmazás aláírásának és hozzárendelésének ezt a módját:

1. Töltse le a [Microsoft Intune Windows 10-es Céges portál alkalmazás aláírása parancsfájlt](https://aka.ms/win10cpscript).  
    A parancsfájlhoz olyan gazdagépre van szükség, amelyen telepítve van a Windows 10-hez készült Windows SDK. [Töltse le a Windows 10 rendszerhez készült Windows SDK-t](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Töltse le a Windows 10-es Céges portál alkalmazást a Microsoft Store Vállalatoknak szolgáltatásból a fenti útmutató szerint.  
3. A Windows 10-es Céges portál alkalmazás aláírásához futtassa a parancsfájlt az annak fejlécében található bemeneti paraméterekkel, amint az az alábbi táblázatban látható.  
    A függőségeket nem kell hozzáadni a parancsprogramhoz. Csak akkor van rájuk szükség, amikor éppen folyamatban van az alkalmazás feltöltése az Intune felügyeleti konzolra.

| Paraméter |  Description  |
|---|---|
| InputWin10AppxBundle  |  Az appxbundle forrásfájl elérési útja. |
| OutputWin10AppxBundle | Az aláírt appxbundle fájl kimeneti útja. 
| Win81Appx  | A Windows 8.1 vagy Windows Phone 8.1 Céges portál (.APPX) fájljának elérési útja. |
| PfxFilePath  |  A Symantec vállalati mobil-kódaláíró tanúsítvány (.PFX) fájljának elérési útja.  |
| PfxPassword  | A Symantec vállalati mobil-kódaláíró tanúsítvány jelszava. |
| PublisherId | A vállalat gyártóazonosítója. Ha nincs megadva, a rendszer a Symantec vállalati mobil-kódaláíró tanúsítvány tulajdonosi mezőjének értékét használja. |
| SdkPath | A Windows 10-hez készült Windows SDK gyökérmappájának elérési útja. Ezt az argumentumot nem kötelező megadni, és az alapértelmezett értéke: ${env:ProgramFiles(x86)}\Windows Kits\10.  |

A parancsfájl kimenete a futtatás végeztével a Windows 10-es Céges portál alkalmazás aláírt verziója lesz. Ekkor az Intune-on keresztül rendelheti hozzá az alkalmazás aláírt verzióját üzletági alkalmazásként, ami frissíti a jelenleg hozzárendelt verziókat erre az új alkalmazásra.  

## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)

