---
title: "Az Active Directory szinkronizálása és felhasználók hozzáadása az Intune szolgáltatáshoz | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: 70a2d32de67f0a69bbc29ca68a1c831c9cf38796


---


# Az Active Directory szinkronizálása és felhasználók hozzáadása az Intune szolgáltatáshoz
A címtár-szinkronizálás konfigurálásával importálhatja a helyi Active Directoryban lévő felhasználói fiókokat a Microsoft Azure Active Directory (Azure AD) szolgáltatásba. A helyi Active Directory szolgáltatás Azure Active Directory-alapú szolgáltatásokkal való összekapcsolásával jóval egyszerűbbé válik az identitásfelügyelet. Az egyszeri bejelentkezési funkciók konfigurálásával ismerőssé és könnyebbé teheti a felhasználók számára a hitelesítést.

Hogy ez még egyszerűbb legyen, több szolgáltatás ugyanazon [Azure AD-bérlővel](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) való használata esetén a korábban szinkronizált felhasználói fiókok minden olyan felhőalapú szolgáltatás számára elérhetők lesznek, amelyek ugyanahhoz az Azure AD-bérlői előfizetéshez tartoznak.

## Helyi felhasználók szinkronizálása az Azure AD szolgáltatással
A felhasználói fiókoknak az Azure AD-val való szinkronizálásához kizárólag az [Azure AD Connect varázslóra](https://www.microsoft.com/download/details.aspx?id=47594) van szüksége. Az Azure AD Connect varázsló egyszerűsített és irányított kezelőfelülettel segíti a helyszíni identitási infrastruktúrának a felhőhöz történő csatlakoztatását.  Válassza ki a topológiát és a vonatkozó igényeket (egyetlen vagy többszörös címtárak, jelszavak szinkronizálása vagy összevonása), a varázsló pedig a kapcsolat létrehozásához és működéséhez szükséges valamennyi összetevő telepítését és konfigurálását elvégzi. Ilyen összetevők többek között: a szinkronizálási szolgáltatások, az Active Directory összevonási szolgáltatások (AD FS) és az Azure AD PowerShell modul.

> [!TIP]
> Az Azure AD Connect a korábban Dirsync és Azure AD Sync néven kibocsátott eszközök valamennyi funkcióját tartalmazza. További tájékoztatás a [Címtár-integrációra](http://technet.microsoft.com/library/jj573653.aspx) vonatkozóan. További tudnivalók a helyi címtárban lévő felhasználói fiókok Azure AD-vel való szinkronizálásának előnyeiről: [Similarities between Active Directory and Azure AD](http://technet.microsoft.com/library/dn518177.aspx) (Az Active Directory és az Azure AD közötti hasonlóságok).

## Rendszergazdai jogosultságok engedélyezése
Azt javasoljuk, hogy a felhasználóknak az Intune-előfizetéshez történő hozzáadása után néhány felhasználói fiók számára biztosítson [rendszergazdai jogosultságokat](administrative-accounts-websites-perms.md). A rendszergazdai jogosultságok hozzárendelésére szolgáló konzol a hozzárendelni kívánt rendszergazda típusától függ:

-   **Bérlői rendszergazda**: Ezt a rendszergazdatípust a **[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]** használatával rendelheti hozzá az előfizetés kezelése céljából, beleértve a számlázást, a felhőalapú tárolást és azon felhasználók felügyeletét, akik számára engedélyezte az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] használatát.

-   **Szolgáltatás-rendszergazda**: Ezt a rendszergazdatípust a **[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]** használatával rendelheti hozzá a napi rutinfeladatok elvégzése céljából, beleértve a mobileszközök és számítógépek felügyeletét, a szabályzatok érvénybe léptetését, a szoftverek telepítését és a jelentéskészítést.


### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések* útmutató 3. lépését.

>[!div class="step-by-step"]

>[&larr; **Tartományi beállítások**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Intune-licencek kezelése** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Jun16_HO4-->


