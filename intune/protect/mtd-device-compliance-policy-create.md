---
title: MTD-eszközmegfelelőségi szabályzat létrehozása a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Létrehozhat egy olyan Intune-beli eszközmegfelelőségi szabályzatot, amely az MTD-partner fenyegetettségi szintjeivel határozza meg, hogy egy mobileszköz hozzáférhet-e a céges erőforrásokhoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 42500618c5ec753fcabf72b03f175b823c3337d4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504387"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>A Mobile Threat Defense (MTD) eszközmegfelelőségi szabályzatának létrehozása az Intune-nal

> [!NOTE] 
> Ezek az információk minden Mobile Threat Defense-partnerre vonatkoznak.

Az Intune és az MTD együttes használata segíti a mobileszközökön megjelenő fenyegetések észlelését és a kockázat felmérését. Az Intune eszközmegfelelési szabályzaton belül létrehozhat egy szabályt, amely kockázatfelméréssel állapítja meg az eszköz megfelelőségét. Ezután [feltételes hozzáférési szabályzattal](create-conditional-access-intune.md) blokkolhatja a szolgáltatásokhoz való hozzáférést az eszköz megfelelősége alapján.

## <a name="before-you-begin"></a>Előkészületek

Az MTD beállítása során az MTD-partnerkonzolon már létrehozott egy szabályzatot, amely a fenyegetéseket magas, közepes és alacsony szintű csoportba sorolja. Most be kell állítania a Mobile Threat Defense szintjét az Intune megfelelőségi szabályzatában.

Az MTD-eszközmegfelelési szabályzat előfeltételei:

- Az MTD és az Intune közötti integráció beállítása

## <a name="to-create-an-mtd-device-compliance-policy"></a>MTD-eszközmegfelelési szabályzat létrehozása

1. Az [Azure Portalon](https://portal.azure.com/) jelentkezzen be az Intune-os hitelesítő adataival.

2. Az **Azure-irányítópulton** válassza a bal oldali menü **Minden szolgáltatás** pontját, majd írja be a szűrő szövegmezőbe az **Intune** nevet.

3. Ha az **Intune** elemre kattint, megnyílik az **Intune irányítópultja**.

4. Az **Intune-irányítópulton** a **Kezelés** szakaszban kattintson az **Eszköz megfelelősége**, majd a **Szabályzatok** elemre.

5. Kattintson a **Szabályzat létrehozása** elemre, írja be az eszközmegfelelés **Név** és **Leírás** adatait, kattintson a **Platform** elemre, majd a**Beállítás** szakaszban kattintson a **Konfigurálás** elemre.

6. A **Megfelelőségi szabályzat** panelen kattintson az **Eszközállapot** lehetőségre.

7. Az **Eszközállapot** panelen a **Maximálisan elérhető eszközfenyegetettségi szint használata** alatti legördülő menüből válassza ki a mobilfenyegetés védelmi szintjét.

    a.  **Védett**: Ez a szint a legbiztonságosabb. Az eszköz csak akkor fér hozzá a céges erőforrásokhoz, ha semmilyen veszélyforrás nincs rajta. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül.

    b.  **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű veszélyforrások állnak fenn. Bármilyen magasabb szintű fenyegetés esetén az eszköz nem megfelelő státuszúnak minősül.

    c.  **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt veszélyforrások alacsony vagy közepes szintűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.

    d.  **Magas**: Ez a szint a legkevésbé biztonságos. Megadása esetén a rendszer semelyik fenyegetettségi szint mellett nem korlátozza az eszközt, a Mobile Threat Defense szolgáltatást csak jelentéskészítésre használja. Ennek a beállításnak a megadása esetén az eszközökön aktiválni kell az MTD alkalmazást.

8. Kattintson kétszer az **OK** elemre, majd válassza a **Létrehozás** lehetőséget.

> [!IMPORTANT]
> Ha feltételes hozzáférési szabályzatokat hoz létre az Office 365-hez vagy más szolgáltatásokhoz, az eszköz megfelelőségének kiértékelését a rendszer kiértékeli, és a nem megfelelő eszközök nem férnek hozzá a vállalati erőforrásokhoz, amíg a fenyegetés fel nem oldódik az eszközön.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>MTD-eszközmegfelelési szabályzat hozzárendelése

Ha a felhasználókhoz eszközmegfelelőségi szabályzatot kíván rendelni, olyan szabályzatot válasszon, amelyet előzőleg már konfigurált. A meglévő szabályzatokat az **Eszközmegfelelőségi szabályzatok** panelen tekintheti meg.

1. Válassza ki a felhasználókhoz hozzárendelni kívánt szabályzatot, és válassza a **Hozzárendelések** lehetőséget. Ez a művelet megnyitja a panelt, amelyen kiválaszthatja a kívánt **Azure Active Directory-biztonsági csoportokat**, és hozzárendelheti azokat a szabályzathoz.

2. Válassza a **Belefoglalandó csoportok** lehetőséget az Azure AD biztonsági csoportjait megjelenítő lap megnyitásához.  A **Kiválasztás** elem választásával telepítheti a szabályzatot a felhasználók számára.

    > [!NOTE] 
    > Ezzel érvénybe léptette a szabályzatot a felhasználók számára. A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználók által használt eszközök megfelelőségét.

## <a name="next-steps"></a>További lépések

- [MTD engedélyezése az Intune-nal](mtd-connector-enable.md)
