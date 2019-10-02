---
title: Beépített alkalmazások hozzáadása mobileszközökhöz a Microsoft Intune-nal
titleSuffix: ''
description: Annak ismertetése, hogyan egyszerűsíthető a beépített alkalmazások mobileszközökre való telepítése az Intune használatával.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a94542311bc5ff4a25b2f9c6229898b1d891c6c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731295"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Beépített alkalmazások hozzáadása a Microsoft Intune-hoz

A *beépített* alkalmazástípus megkönnyíti, hogy válogatott felügyelt alkalmazásokat, például Office 365-alkalmazásokat rendeljen iOS és Android-eszközökhöz. Az alkalmazástípushoz hozzárendelhet adott alkalmazásokat, például az Excel, a OneDrive, az Outlook, a Skype és egyéb alkalmazásokat. Alkalmazás hozzáadása után a megjelenített alkalmazástípus *Beépített iOS-alkalmazás* vagy *Beépített Android-alkalmazás* lesz. A beépített alkalmazástípus használatával kiválaszthatja, hogy mely alkalmazásokat teszi közzé az eszköz felhasználóinak.

Az Intune-konzol korábbi verzióiban az Intune több alapértelmezett felügyelt Office 365-alkalmazást is rendelkezésre bocsátott, például az Outlookot és a OneDrive-ot. Ezen felügyelt alkalmazások alkalmazástípusát a *Felügyelt iOS Store-alkalmazás* vagy *Felügyelt Android-alkalmazás* címke jelölte. Ajánlott ezek helyett a beépített alkalmazástípust használni. A beépített alkalmazástípus használatával rugalmasabban szerkeszthetők és törölhetők az Office 365-alkalmazások.

>[!NOTE]
>A *Felügyelt iOS Store* és *Felügyelt Android-alkalmazás* címkével rendelkező alapértelmezett Office 365-alkalmazásokat az összes hozzárendelés törlése esetén a rendszer eltávolítja az alkalmazáslistából.

## <a name="add-a-built-in-app"></a>Beépített alkalmazás hozzáadása

Beépített alkalmazást a következő módon adhat hozzá az elérhető alkalmazásokhoz a Microsoft Intune-ban:
1. Jelentkezzen be az Azure portálra.
2. A Microsoft Intune panel megjelenítéséhez válassza a **További szolgáltatások** > **Figyelés és felügyelet** > **Intune** lehetőséget.
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** panelen a **Kezelés** szakaszban válassza az **Alkalmazások** lehetőséget.
5. Válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazás hozzáadása** panelen az **Alkalmazástípus**-listából válassza a **Beépített alkalmazás** lehetőséget.
7. Válassza az **Alkalmazás kiválasztása** lehetőséget.
8. A **Beépített alkalmazás** panelen jelölje ki a belefoglalni kívánt alkalmazásokat.
9. Az **Alkalmazás hozzáadása** panelen válassza a **Hozzáadás** lehetőséget.


## <a name="configure-app-information"></a>Az alkalmazásadatok konfigurálása

Módosíthatja a beépített alkalmazással kapcsolatos információkat. Ezek révén azonosíthatja az alkalmazást az Intune-ban, és segítségükkel a felhasználók is könnyebben megtalálhatják azt a Céges portál alkalmazásban.
1. Az **ügyfélalkalmazások – alkalmazások** panelen válassza ki a módosítani kívánt beépített alkalmazást.  
    Megjelenik a beépített alkalmazás panelje.
2. A **Kezelés** alatt válassza a **Tulajdonságok** lehetőséget.
3. A beépített alkalmazás adatainak módosításához válassza a **Konfigurálás** lehetőséget.
4. Az **Alkalmazásadatok** panelen adja meg az alábbi információkat:
    - **Név**: Adja meg a beépített alkalmazás nevét a vállalati portálon megjelenő módon. Ügyeljen arra, hogy csak egyedi neveket használjon. Ha ugyanazt az alkalmazásnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Description** (Leírás): Adja meg az alkalmazás leírását. 
    - **Közzétevő**: Itt adhatja meg az alkalmazás kiadójának nevét.
    - **Kategória**: Szükség esetén kiválaszthat egy vagy több beépített alkalmazás-kategóriát is. A beállítás megadásával megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálon**: Az alkalmazás jól észrevehető módon való megjelenítése a vállalati portál fő lapján, amikor a felhasználók tallózással alkalmazásokat keresnek.
    - **Információs URL-cím**: Nem kötelező: megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi URL-cím**: Nem kötelező: megadhatja az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő**: Igény szerint megadhatja az alkalmazás-fejlesztő nevét.
    - **Tulajdonos**: Igény szerint megadhatja az alkalmazás tulajdonosának nevét (például *HR-osztály*).
    - **Megjegyzések**: Adja meg az alkalmazáshoz hozzárendelni kívánt megjegyzéseket.
    - **Feltöltés ikonja**: Feltölthet egy ikont, amely megjelenik az alkalmazással, amikor a felhasználók megkeresik a vállalati portált.
4. Kattintson az **OK** gombra.
5. A **Tulajdonságok** panelen válassza a **Mentés** lehetőséget.

## <a name="next-steps"></a>További lépések

- Mostantól hozzárendelheti az alkalmazásokat a kiválasztott csoportokhoz. További információ: [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md).
