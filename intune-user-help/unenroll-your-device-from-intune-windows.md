---
title: Windows-eszköz eltávolítása az Intune-ból
description: Egy Windows-eszköz Intune-felügyeletből való törlését mutatja be
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e64911ea9b1b1d3c619a82eac9dc78e4e78a53e9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508127"
---
# <a name="remove-your-windows-device-from-management"></a>Windows-eszköz eltávolítása a felügyelet alól

Eltávolíthatja a regisztrált Windows-eszközét a felügyelet alól, ha már nem szeretné a következőkre használni:  
* Az eszköz munkahelyi vagy iskolai használata. 
* Hozzáférés a munkahelyi vagy iskolai e-mailekhez, alkalmazásokhoz és egyéb erőforrásokhoz.

Miután megszünteti az eszköz regisztrációját, az eszköz már nem fog tudni hozzáférni az iskolai vagy munkahelyi erőforrásokhoz. Az alábbi Windows-eszközöket távolíthatja el felügyelet alól.  
* Windows 10-es eszközök 
* Windows 8.1-es számítógépek
* Windows 8.1-es telefon
 
További információ az eszköz felügyelet alóli kivonásának további következményeiről: [Mi történik, ha eltávolítja az eszközt az Intune-ból?](what-happens-if-you-unenroll-your-device-from-intune-windows.md).  

## <a name="remove-your-windows-10-device"></a>Windows 10 rendszerű eszköz törlése
Az alábbi lépésekkel távolíthat el egy Windows 10-es eszközt a felügyelet alól.

### <a name="remove-in-company-portal-app-home-page"></a>Eltávolítás a Céges portál alkalmazás **Kezdőlap** lapján  

1. Nyissa meg a Vállalati portál alkalmazást.
2. A **Kezdőlap** lapon görgessen le az **Eszközeim** szakaszhoz.
3. Válassza ki az eltávolítani kívánt eszközt.
3. Az alkalmazás jobb felső sarkában kattintson a **Továbbiak** ikonra.
4. Válassza az **Eltávolítás** lehetőséget. 
5. Az eszköz eltávolításának megerősítéséhez válassza az **Eltávolítás** lehetőséget.  

### <a name="remove-in-company-portal-app-device-context-menu"></a>Eltávolítás a Céges portál alkalmazásban az eszköz helyi menüjével  

1. Nyissa meg a Céges portál alkalmazást, majd keresse meg az **Eszközeim** szakaszt.

    ![Példaképernyőkép a Céges portál alkalmazás Kezdőlapjáról a Windowsban, kiemelt Eszközeim szakasszal.](./media/1809_CheckAccess_Context_Select_Device.png)

2. Kattintson a jobb gombbal, vagy tartsa rajta az ujját az eszköz képernyőjén a [helyi menü](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus) megnyitásához.  

3. Válassza az **Eltávolítás** lehetőséget.  

    ![Példaképernyőkép a Céges portál alkalmazás Kezdőlapjáról a Windowsban. Az eszköz helyi menüje látható a lap **Eszközeim** szakaszában az Átnevezés, Eltávolítás és Hozzáférés ellenőrzése műveletekkel.](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. Kattintson a megerősítő képernyőn a **További információ** hivatkozásra annak elolvasásához, hogyan változik a munkahelyi és iskolai erőforrásokhoz való hozzáférése. Az eszköz eltávolításának megerősítéséhez válassza az **Eltávolítás** lehetőséget.   

     ![Példaképernyőkép a Céges portál alkalmazás Kezdőlapjáról a Windowsban. Megjelenik az Átnevezés mező az eszközön, ahol bírhatja az új nevet, és rákattinthat az Átnevezés vagy a Mégse gombra.](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>Eltávolítás az eszköz Beállítások alkalmazásában
1. Nyissa meg a Beállítások alkalmazást. 
2. Lépjen a **Fiókok** > **Hozzáférés munkahelyi vagy iskolai rendszerhez** pontra.
3. Válassza ki az eltávolítani kívánt csatlakoztatott fiókot, majd válassza a **Leválasztás** lehetőséget.
4. Az eszköz eltávolításának megerősítéséhez válassza az **Igen** lehetőséget.

## <a name="remove-your-windows-81-computer"></a>Windows 8.1-es számítógép törlése
Az alábbi lépésekkel eltávolíthat egy Windows 8.1-es számítógépet az Intune-ból.

1. Lépjen a **Gépház** > **Hálózat** > **Munkahely** lehetőséghez.
2. A **Csatlakozás munkahelyhez** területen válassza a **Kilépés** lehetőséget.
3. Válassza az **Eszközkezelés bekapcsolása** terület **Kikapcsolás** lehetőségét.
4. A megjelenő előugró ablakban válassza a **Kikapcsolás** lehetőséget.

## <a name="remove-your-windows-81-phone"></a>Windows 8.1-es telefon eltávolítása
Az alábbi lépésekkel eltávolíthat egy Windows 8.1-es eszközt az Intune-ból.

1. Lépjen a **Beállítások** > **Munkahely** területre.
2. Koppintson a törölni kívánt munkahelyi fiókra.
3. A képernyő alsó részén koppintson a **Törlés** elemre.
4. A **Fiók törlése** párbeszédpanelen koppintson a **Törlés** gombra.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Személyes információk törlése a Céges portál eltávolítása után  

A Céges portál kétféle adatot tárol az Ön windowsos eszközén:

- **Diagnosztikai naplók**: A Microsoft által gyűjtött szabványos alkalmazástevékenység-adatok. Automatikusan törlődnek a Céges portál alkalmazás eltávolításakor. Az alkalmazástevékenységi adatok például az alkalmazás használatának időtartama vagy az összeomlási adatok.
- **Alkalmazás-gyorsítótár**: Olyan támogató fájlok, amelyek tárolása szükséges az alkalmazás működéséhez, például ikonok és beállítások.

A tárolt naplók és gyorsítótár törléséhez kövesse az alábbi lépéseket:

* [Távolítsa el a Céges portál alkalmazást.](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* Állítsa alaphelyzetbe a Céges portál alkalmazást. Nyissa meg a **Beállítások** alkalmazást, és válassza az **Alkalmazások** > **Céges portál** > **Speciális beállítások** > **Alaphelyzetbe állítás** lehetőséget. 

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).
