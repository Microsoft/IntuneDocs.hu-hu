---
title: Androidos áruházbeli alkalmazások hozzáadása a Microsoft Intune-hoz
titleSuffix: ''
description: Ismerje meg, hogyan adhat hozzá androidos áruházbeli alkalmazásokat a Google Play áruházból a Microsoft Intunehoz.
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
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6b9f6a9303e53652959639193633cdcc00dfb99
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755085"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Androidos áruházbeli alkalmazások hozzáadása a Microsoft Intune-hoz

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mielőtt az alkalmazást hozzárendelné egy eszközhöz vagy felhasználói csoporthoz, az eszközt először hozzá kell adnia a Microsoft Intune-hoz. 

## <a name="add-an-app"></a>Alkalmazás hozzáadása

A következő módon adhat hozzá Android-áruházból származó alkalmazást az Intune-hoz az Azure Portalon:

1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **alkalmazások** > **minden alkalmazás** > **Hozzáadás**lehetőséget.
3. Az **alkalmazás típusának kiválasztása** ablaktáblán az elérhető **áruházbeli alkalmazások** típusai területen válassza az **Android áruházbeli alkalmazás**lehetőséget.
4. Kattintson a **Kiválasztás** lehetőségre.<br>
   Megjelenik az **alkalmazás hozzáadása** lépések.
5. Az Android-alkalmazás **alkalmazás-információinak** konfigurálásához keresse meg a [Google Play áruházat](https://play.google.com/store) , és keressen rá a telepíteni kívánt alkalmazásra. Jelenítse meg az alkalmazás lapját, és jegyezze fel az alkalmazás részleteit. 
6. Az **alkalmazás adatai** lapon adja meg az alkalmazás részleteit:
    - **Név**: Itt adhatja meg az alkalmazás céges portálon megjelenítendő nevét. Gondoskodjon róla, hogy az alkalmazás neve egyedi legyen. Ha két alkalmazás neve megegyezik, a felhasználók csak az egyik alkalmazást fogják látni a céges portálon.
    - **Leírás**: Itt adhatja meg az alkalmazás leírását. A leírás a céges portálon jelenik meg a felhasználók számára.
    - **Kiadó:** Adja meg az alkalmazás kiadójának nevét.
    - **Alkalmazás-áruház URL-címe**: Itt adhatja meg a létrehozni kívánt alkalmazás áruházbeli URL-címét. Ha az alkalmazás adatai megjelennek az áruházban, használja az alkalmazás oldalának URL-címét. 
    - **Minimális operációsrendszer-verzió**: A listából válassza ki az operációs rendszer legkorábbi olyan verzióját, amelyre az alkalmazás telepíthető. Ha az alkalmazást régebbi operációs rendszerrel rendelkező eszközhöz rendelik hozzá, akkor nem lesz telepítve.
    - **Kategória:** Választhat egyet vagy többet a beépített alkalmazáskategóriák közül, vagy megadhat egyénileg létrehozott kategóriát is. Ezzel megkönnyítheti a felhasználók számára az alkalmazás megkeresését a céges portálon való böngészés során.
    - **Megjelenítés Kiemelt alkalmazásként a céges portálban**: ezzel a beállítással a vállalati portál főoldalán jelenítheti meg az App Suite-t, amikor a felhasználók megkeresik az alkalmazásokat. Az elérhető szándékkal üzembe helyezett alkalmazásokra vonatkozik.
    - **Információs URL-cím:** Igény szerint megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi nyilatkozat URL-címe:** Igény esetén itt adhatja meg az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztő**: Igény esetén megadhatja az alkalmazás fejlesztőjének nevét.
    - **Tulajdonos**: Igény esetén megadhatja az alkalmazás tulajdonosának nevét (például *HR-osztály*).
    - **Megjegyzések:** : Ide írhatja be igény szerint az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Ikon** (nem kötelező): Itt töltheti fel az alkalmazáshoz hozzárendelni kívánt ikont. Ez az alkalmazásikon jelenik meg a céges portálon böngésző felhasználók számára.
7. Kattintson a **tovább** gombra a **hatókör címkék** oldal megjelenítéséhez.
8. Kattintson a **hatókör címkék kiválasztása** lehetőségre, hogy felvegye a hatókör címkéit az alkalmazáshoz. További információ: [a szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez](~/fundamentals/scope-tags.md).
9. A **hozzárendelések** lap megjelenítéséhez kattintson a **tovább** gombra.
10. Válassza ki az alkalmazás csoportjának hozzárendeléseit. További információ: [csoportok hozzáadása a felhasználók és eszközök rendszerezéséhez](~/fundamentals/groups-add.md). 
11. Kattintson a **tovább** gombra a **felülvizsgálat + létrehozás** lap megjelenítéséhez. Tekintse át az alkalmazáshoz megadott értékeket és beállításokat.
12. Ha elkészült, kattintson a **Létrehozás** gombra, hogy hozzáadja az alkalmazást az Intune-hoz.

Megjelenik a létrehozott alkalmazás **Áttekintés** panelje.

## <a name="next-steps"></a>További lépések

- [Alkalmazások hozzárendelése csoportokhoz](apps-deploy.md)
