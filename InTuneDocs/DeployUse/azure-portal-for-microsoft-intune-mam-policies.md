---
title: "Azure-portál a mobilalkalmazás-felügyeleti szabályzatok kezeléséhez | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
ms.sourcegitcommit: ded7bd6c971a9448ad6e6492ebc5e42dfcb5d76e
ms.openlocfilehash: 519bde55966d88f516553d509af60e34a6af62a9


---

# Azure-portál a Microsoft Intune mobilalkalmazás-felügyeleti szabályzatainak kezeléséhez
## Az Azure-portál elérése
Az **Azure-portálon** lehetősége van mobilalkalmazás-felügyeleti szabályzatok létrehozására és kezelésére.

Az Azure-portálon az alábbiakhoz támogatott a MAM-szabályzatok létrehozása:
- Az **Intune-ban regisztrált és általa kezelt** eszközökön futó alkalmazások.
- Semmilyen MDM-megoldásban **nem regisztrált** eszközökön futó alkalmazások.
- **Harmadik féltől származó MDM-megoldásban regisztrált** eszközökön futó alkalmazások.

Ha jelenleg az **Intune felügyeleti konzolját** használja eszközei kezelésére, az [Intune felügyeleti konzol](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) segítségével létrehozhat egy olyan MAM-szabályzatot, amely az Intune-ban regisztrált eszközökön futó alkalmazásokat támogatja.
>[!IMPORTANT]
> Előfordulhat, hogy az Intune felügyeleti konzolon nem lát minden MAM-szabályzatbeállítást. A MAM-szabályzatok létrehozására szolgáló új felügyeleti konzol az Azure-portál. Ha mind az Intune felügyeleti konzoljában, mind az Azure-portálon létrehoz MAM-szabályzatokat, a rendszer az Azure-portálon érvényes szabályzatot alkalmazza az alkalmazásokra, illetve telepíti a felhasználók számára.

## Bejelentkezés az Azure-portálra és a kezdőlap testreszabása

1.  Az [Azure-portálon](https://portal.azure.com) jelentkezzen be [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-os hitelesítő adataival.

    ![Az Azure-portál bejelentkezési oldalának képernyőképe](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Miután sikeresen bejelentkezett, megjelenik az **Irányítópult**. Az **Irányítópulton** az alapértelmezett csempék láthatók. Ezeket eltávolíthatja, és újak hozzáadásával testre szabhatja a lapot.

    ![Az Azure-portál irányítópultjának képernyőképe](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  A **Tallózás** menüben keresse meg az **Intune** elemet.![A Tallózás menü képernyőképe az Intune kiemelésével](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Kattintson az **Intune > Intune mobilalkalmazás-kezelés > Beállítások** elemre.

    ![Az Intune mobilalkalmazás-felügyelet panel képernyőfelvétele](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Ha rögzíteni szeretne egy panelt a **kezdőlapon** , válassza a **Rögzítés** lehetőséget a panelen.  Az **Intune-alapú mobilalkalmazás-felügyelet**panelt a rögzítés ikonjára kattintva rögzítheti a **kezdőlapon** .

    ![Az Intune mobilalkalmazás-felügyeleti paneljének képernyőképe, a rögzítés ikonja kiemelve](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Az irányítópult és a rögzített Intune csempe képernyőképe](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## További lépések
[Felkészülés a mobilalkalmazás-felügyeleti szabályzatok konfigurálására](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


