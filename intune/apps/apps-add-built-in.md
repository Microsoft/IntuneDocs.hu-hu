---
title: Beépített alkalmazások hozzáadása mobileszközökhöz a Microsoft Intune-nal
titleSuffix: ''
description: Annak ismertetése, hogyan egyszerűsíthető a beépített alkalmazások mobileszközökre való telepítése az Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96cd4997029c15396db91e9866bbb387c20f1044
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414449"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Beépített alkalmazások hozzáadása a Microsoft Intune-hoz

A *beépített* alkalmazás típusa megkönnyíti a kezelt felügyelt alkalmazások, például az Office 365 alkalmazások hozzárendelését iOS/IPadOS és Android rendszerű eszközökhöz. Az alkalmazástípushoz hozzárendelhet adott alkalmazásokat, például az Excel, a OneDrive, az Outlook, a Skype és egyéb alkalmazásokat. Alkalmazás hozzáadása után a megjelenített alkalmazástípus *Beépített iOS-alkalmazás* vagy *Beépített Android-alkalmazás* lesz. A beépített alkalmazástípus használatával kiválaszthatja, hogy mely alkalmazásokat teszi közzé az eszköz felhasználóinak.

Az Intune-konzol korábbi verzióiban az Intune több alapértelmezett felügyelt Office 365-alkalmazást is rendelkezésre bocsátott, például az Outlookot és a OneDrive-ot. Ezen felügyelt alkalmazások alkalmazástípusát a *Felügyelt iOS Store-alkalmazás* vagy *Felügyelt Android-alkalmazás* címke jelölte. Ajánlott ezek helyett a beépített alkalmazástípust használni. A beépített alkalmazástípus használatával rugalmasabban szerkeszthetők és törölhetők az Office 365-alkalmazások.

>[!NOTE]
>A *Felügyelt iOS Store* és *Felügyelt Android-alkalmazás* címkével rendelkező alapértelmezett Office 365-alkalmazásokat az összes hozzárendelés törlése esetén a rendszer eltávolítja az alkalmazáslistából.

## <a name="add-a-built-in-app"></a>Beépített alkalmazás hozzáadása

Beépített alkalmazást a következő módon adhat hozzá az elérhető alkalmazásokhoz a Microsoft Intune-ban:
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán, az elérhető **áruházbeli alkalmazások** típusai területen válassza a **beépített alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre. Megjelenik az **alkalmazás hozzáadása** lépések.
5. A **beépített alkalmazások kiválasztása** lapon kattintson az **alkalmazás kiválasztása** elemre a felvenni kívánt alkalmazások kiválasztásához.
6. Válassza ki a beépített alkalmazásokat, amelyeket fel szeretne venni. 
7. Miután kiválasztotta az alkalmazásokat, a **beépített alkalmazások kiválasztása** panelen kattintson a **kiválasztás** elemre.
8. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.
9. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye a hatókör címkéit az alkalmazáshoz. További információ: [a szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez](~/fundamentals/scope-tags.md).
10. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.
11. Válassza ki az alkalmazás csoportjának hozzárendeléseit. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md). 
12. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat.
13. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

    Megjelenik a létrehozott alkalmazás **Áttekintés** panelje.

## <a name="configure-app-information"></a>Az alkalmazásadatok konfigurálása

Módosíthatja a beépített alkalmazással kapcsolatos információkat. Ezek révén azonosíthatja az alkalmazást az Intune-ban, és segítségükkel a felhasználók is könnyebben megtalálhatják azt a Céges portál alkalmazásban.
1. Válassza az **alkalmazások** > **minden alkalmazás** lehetőséget, majd válassza ki a módosítani kívánt beépített alkalmazást.  
   Megjelenik a beépített alkalmazás panelje.
2. Válassza a **Tulajdonságok**lehetőséget.
3. Válassza az **alkalmazás adatai**elem melletti **Szerkesztés** lehetőséget.
4. Az **Alkalmazásadatok** panelen adja meg az alábbi információkat:
    - **Név**: Itt adhatja meg a beépített alkalmazásnak a céges portálon megjelenő nevét. Ügyeljen arra, hogy csak egyedi neveket használjon. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. 
    - **Kiadó**: Adja meg az alkalmazás kiadójának nevét.
    - **Kategória**: Szükség esetén választhat egyet vagy többet a beépített alkalmazáskategóriák közül. A beállítás megadásával megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálon**: jelenítse meg az alkalmazást a céges portál főoldalán, amikor a felhasználók megkeresik az alkalmazásokat.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő**: Igény esetén megadhatja az alkalmazás fejlesztőjének nevét.
    - **Tulajdonos**: Igény esetén megadhatja az alkalmazás tulajdonosának nevét (például *HR-osztály*).
    - **Megjegyzések**: Ide írhatja be az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Ikon feltöltése**: Feltölthet egy ikont, mely megjelenik az alkalmazással a céges portálon böngésző felhasználók számára.
5. A **felülvizsgálat + létrehozás** lap megjelenítéséhez kattintson a **felülvizsgálat + mentés** elemre. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat.
13. Ha elkészült, kattintson a **Mentés** gombra az alkalmazás Intune-beli frissítéséhez.

    Megjelenik a létrehozott alkalmazás **Áttekintés** panelje.

## <a name="next-steps"></a>További lépések

- Mostantól hozzárendelheti az alkalmazásokat a kiválasztott csoportokhoz. További információ: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).
