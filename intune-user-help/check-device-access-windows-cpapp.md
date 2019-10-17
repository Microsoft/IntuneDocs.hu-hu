---
title: Eszközhozzáférés ellenőrzése | Microsoft Docs
description: Az eszközhozzáférés ellenőrzésével megtudhatja, hogy eszköze megfelel-e a követelményeknek, valamint hozzáférhet-e munkahelyi vagy iskolai erőforrásokhoz.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49075fd750ade6aaa412d551f4177822b52ce7f2
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490099"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Hozzáférés ellenőrzése a Windowsos Céges portál alkalmazásból

Ellenőrizze, hogy az eszköz hozzáfér-e a munkahelyi vagy iskolai erőforrásokhoz. 

A szervezetek követelményeket kényszeríthetnek &ndash; például titkosítást és jelszókorlátokat &ndash;, amelyekkel meggyőződhetnek arról, hogy csak biztonságos és megbízható eszközök férhetnek hozzá az adataikhoz. A kezelt eszközöknek meg kell felelniük ezeknek a követelményeknek a szervezeti erőforrások eléréséhez.

A **Hozzáférés ellenőrzése** művelet értékeli az eszköz beállításait és hozzáférési állapotát. Az **Eszközadatok** lapon megtalálhatók azok a beállítások, amelyeket módosítania kell a hozzáférés engedélyezéséhez. 

Ha a Windowsos Céges portál alkalmazásban szeretné ellenőrizni a hozzáférést, kövesse a cikk lépéseit.  

## <a name="check-access-from-device-details-page"></a>Hozzáférés ellenőrzése az Eszközadatok lapon  
1. Nyissa meg a Windowsos Céges portál alkalmazást, majd keresse meg az **Eszközeim** szakaszt.  

    ![Példaképernyőkép a Céges portál alkalmazás Kezdőlapjáról a Windowsban, kiemelt Eszközeim szakasszal.](./media/1809_CheckAccess_Context_Select_Device.png)  
2. Válassza ki az eszközt.  
3. Az **Eszközadatok** lapon válassza a **Hozzáférés ellenőrzése** lehetőséget. Az alkalmazás szinkronizálja az eszközt a szervezet jelenlegi követelményeivel, és ellenőrzi, hogy az eszköz biztosan megfelel-e nekik. Ez eltarthat pár percig.  

    ![Példaképernyőkép a Céges portál alkalmazás Eszközadatok lapjáról a Windowsban, kiemelt Hozzáférés ellenőrzése gombbal.](./media/1809_CheckAccess_Checking_Status.png) 

4. Tekintse meg az állapotfrissítést. Itt láthatja, hogy az eszköze **hozzáférhet-e a szervezeti erőforrásokhoz** vagy **nem férhet hozzá a szervezeti erőforrásokhoz**.  

   ![Példaképernyőkép a Céges portál alkalmazás Eszközadatok lapjáról a Windowsban, kiemelt Állapot szakasszal.](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. Ha az eszköz nem tud hozzáférni az erőforrásokhoz, lépjen az oldal tetején látható riasztásra. Kattintson a **Továbbiak** lehetőségre a részletek kibontásához. Kattintson a **Kevesebb** lehetőségre az összecsukáshoz.  

    ![Példaképernyőkép a Céges portál alkalmazás Eszközadatok lapjáról a Windowsban, az oldal tetején kiemelt riasztással.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Az üzenet további súgóhivatkozásokat és megoldási műveleteket kínál, amennyiben elérhetők ilyenek. Az azonnali hibaelhárításhoz válasszon ki egyet ezek közül. Az &ndash; alább ismertetett &ndash; feloldási, szinkronizálási és kapcsolati műveletek csak akkor láthatók, ha a Céges portált az érintett eszközön használja.  

     * Az **Útmutató a probléma megoldásához** egy kapcsolódó súgócikket nyit meg, amennyiben van ilyen.  
     * A **Feloldás** lehetőség átirányítja Önt az eszköz beállítására.  
     * A **Szinkronizálás** értékeli az eszközt, és meggyőződik arról, hogy az megfelel a szervezeti követelményeknek.  
     * Az **IT-csoport elérhetősége** lehetőség megnyitja az informatikai csoport kapcsolattartási adatait.   
 
6. A beállítások frissítése után kattintson a **Hozzáférés ellenőrzése** lehetőségre az eszközállapot megerősítéséhez.  

    ![Példaképernyőkép a Céges portál alkalmazás Eszközadatok lapjáról a Windowsban, kiemelt Állapot szakasszal.](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>Hozzáférés ellenőrzése az eszköz helyi menüjében  
1. Nyissa meg a Windowsos Céges portál alkalmazást, majd keresse meg az **Eszközeim** szakaszt.  

    ![Példaképernyőkép a Céges portál alkalmazás Kezdőlapjáról a Windowsban, kiemelt Eszközeim szakasszal.](./media/1809_CheckAccess_Context_Select_Device.png)  

2. Kattintson a jobb gombbal, vagy tartsa rajta az ujját az eszköz képernyőjén a [helyi menü](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus) megnyitásához.  

    ![Példaképernyőkép a Céges portál alkalmazás Kezdőlapjáról a Windowsban. Az eszköz helyi menüje látható a lap **Eszközeim** szakaszában az Átnevezés, Eltávolítás és Hozzáférés ellenőrzése műveletekkel.](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. Válassza a **Hozzáférés ellenőrzése** lehetőséget. Az alkalmazás szinkronizálja az eszközt a szervezet jelenlegi követelményeivel, és ellenőrzi, hogy az eszköz biztosan megfelel-e nekik. Ez eltarthat pár percig.  
 
4. Az eszköz alatt egy üzenet jelzi, hogy az eszköz **hozzáférhet-e a szervezeti erőforrásokhoz** vagy **nem férhet hozzá a szervezeti erőforrásokhoz**. 

    ![Példaképernyőkép a Céges portál alkalmazás Eszközadatok lapjáról a Windowsban, kiemelt Állapot szakasszal.](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. Ha az eszköz nem tud hozzáférni az erőforrásokhoz, jelölje ki.  
6. Az **Eszközadatok** lapon lépjen a lap tetején látható riasztásra. Kattintson a **Továbbiak** lehetőségre a részletek kibontásához. Kattintson a **Kevesebb** lehetőségre az összecsukáshoz.  

    ![Példaképernyőkép a Céges portál alkalmazás Eszközadatok lapjáról a Windowsban, az oldal tetején kiemelt riasztással.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Az üzenet további súgóhivatkozásokat és megoldási műveleteket kínál, amennyiben elérhetők ilyenek. Az azonnali hibaelhárításhoz válasszon ki egyet ezek közül. Az &ndash; alább ismertetett &ndash; feloldási, szinkronizálási és kapcsolati műveletek csak akkor láthatók, ha a Céges portált az érintett eszközön használja.  

     * Az **Útmutató a probléma megoldásához** egy kapcsolódó súgócikket nyit meg, amennyiben van ilyen.  
     * A **Feloldás** lehetőség átirányítja Önt az eszköz beállítására.  
     * A **Szinkronizálás** értékeli az eszközt, és meggyőződik arról, hogy az megfelel a szervezeti követelményeknek.  
     * Az **IT-csoport elérhetősége** lehetőség megnyitja az informatikai csoport kapcsolattartási adatait.    

7. A beállítások frissítése után kattintson a lap alján látható **Hozzáférés ellenőrzése** lehetőségre.  

    ![Példaképernyőkép a Céges portál alkalmazás Eszközadatok lapjáról a Windowsban, kiemelt Hozzáférés ellenőrzése művelettel.](./media/1809_CheckAccess_Device_details_button.png) 


További segítségre van szüksége? A cég informatikai ügyfélszolgálatának elérhetőségét a [Céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja.
