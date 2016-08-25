---
title: "Alkalmazásonkénti VPN Android-eszközökhöz a Pulse Secure használatával | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 05/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.sourcegitcommit: 40e5602a4675bd92a85001827fb43426c41ed1e3
ms.openlocfilehash: fc58e71a9b2279200dee2630aab7dbab727ea128


---

# Egyéni szabályzat használata az Android-eszközök alkalmazásonkénti VPN-profiljainak létrehozásához

Az Intune által felügyelt Android-eszközökhöz alkalmazásonkénti VPN-profilt hozhat létre. Először egy Pulse Secure kapcsolattípust használó VPN-profilt, majd az adott alkalmazásokat használó profilhoz társított egyéni konfigurációs szabályzatot kell létrehoznia. Miután telepítette ezeket a szabályzatokat Android-eszközén vagy a felhasználói csoport számára, a megadott alkalmazások valamelyikének megnyitása elindít az eszközön egy VPN-kapcsolatot az adott alkalmazáshoz. 

### 1. lépés: VPN-profil létrehozása

1. A [Microsoft Intune felügyeleti konzolban](https://manage.microsoft.com) kattintson a **Házirend ** > **Házirend hozzáadása** elemre.
2. Válasszon egy sablont az új szabályzathoz az **Android** elem kibontásával, majd válassza a **VPN-profil (Android 4 és újabb verziók)** lehetőséget.

3. A sablonban a **Kapcsolat típusa** beállításnál válassza a **Pulse Secure** lehetőséget.
4. Fejezze be a beállítást, és mentse a VPN-profilt. A VPN-profilokkal kapcsolatban bővebben lásd a [VPN-kapcsolatok](vpn-connections-in-microsoft-intune.md) témakört.

> [!NOTE]
Jegyezze fel a VPN-profil nevét a következő lépéshez. Például: **AlkVpnProfil**.
   
### 2. lépés: Egyéni konfigurációs szabályzat létrehozása
    
   1. Az Intune felügyeleti konzolon válassza a **Házirend** -> **Házirend hozzáadása** -> **Android** -> **Egyéni konfiguráció** -> **Házirend létrehozása** lehetőséget.
   2. Adja meg a szabályzat nevét.
   3. Az **OMA-URI beállítások** területen kattintson a **Hozzáadás** elemre.
   4. Adja meg a beállítás nevét.
   5. Az **Adattípus** mezőben válassza a **Karakterlánc** lehetőséget.
   6. Az **OMA-URI** mezőbe írja be a következő karakterláncot: **./Vendor/MSFT/VPN/Profile/*Név*/PackageList**, ahol a *Név* az 1. lépésben feljegyzett VPN-profil neve. A fenti példában a karakterlánc a következő lenne: **./Vendor/MSFT/VPN/Profile/AlkVpnProfil/PackageList**.
   7.   Az **Érték** területen adja meg azoknak a csomagoknak a pontosvesszővel tagolt listáját, amelyeket a profilhoz társít.  Ha például azt szeretné, hogy az Excel és a Google Chrome böngésző VPN-kapcsolatot használjon, írja be a következőt: **com.microsoft.office.excel;com.android.chrome**.
  

   ![Példa Android rendszerű, alkalmazásonkénti VPN-hez létrehozott egyéni szabályzatra](..\media\android_per_app_vpn_oma_uri.png) 
#### Az alkalmazáslista Blacklist (Letiltott) vagy Whitelist (Engedélyezett) értékre állítása (nem kötelező)
A **BLACKLIST** (LETILTOTT) érték kiválasztásával megadhatja, hogy az alkalmazáslista *ne* használhasson VPN-kapcsolatot.  Minden más alkalmazás VPN-kapcsolaton keresztül fog csatlakozni az internethez.

Másik megoldásként megadhatja, hogy *csak* adott alkalmazások használhassanak VPN-kapcsolatot. Ehhez a **WHITELIST** (ENGEDÉLYEZETT) értéket kell beállítania.
 

1.  Az OMA-URI beállítások területén kattintson a **Hozzáadás** elemre.
2.  Adja meg a beállítás nevét.
3.  Az **Adattípus** mezőben válassza a **Karakterlánc** lehetőséget.
4.  Az** OMA-URI** mezőbe írja be a következő karakterláncot: **./Vendor/MSFT/VPN/Profile/*Név*/Mode**, ahol a *Név* az 1. lépésben feljegyzett VPN-profil neve. A fenti példában a karakterlánc a következő lenne: **./Vendor/MSFT/VPN/Profile/AlkVpnProfil/Mode**.
5.  Az **Érték** mezőbe írja be a **BLACKLIST** (LETILTOTT) vagy a **WHITELIST** (ENGEDÉLYEZETT) értéket. 


   
### 3. lépés: Mindkét szabályzat telepítése

*Mindkét* szabályzatot *azonos* Intune-csoport számára kell telepítenie.

   1.  A **Házirend** munkaterületen válassza ki a telepíteni kívánt házirendet, majd kattintson a **Központi telepítés kezelése**lehetőségre.

2.  A **Telepítések kezelése** párbeszédpanelen:

    -   **A szabályzat telepítése** – Válasszon ki egy vagy több olyan csoportot, amelynek telepíteni kívánja a szabályzatot, majd kattintson a **Hozzáadás** &gt; **OK** gombra.

    -   **A párbeszédpanel bezárása telepítés nélkül** – Kattintson a **Mégse** gombra.

A **Házirend** munkaterület **Áttekintés** lapján található állapotösszegzés és riasztások segítségével azonosíthatók a szabályzattal kapcsolatos, figyelmet igénylő problémák. Ezen felül egy állapotösszegzés megjelenik az Irányítópult munkaterületen is.




<!--HONumber=Jun16_HO4-->


