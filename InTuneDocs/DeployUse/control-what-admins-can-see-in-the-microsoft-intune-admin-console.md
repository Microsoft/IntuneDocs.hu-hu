---
title: "Konzolnézetek testre szabása rendszergazdai szerepkörökhöz | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 52a77e50b3dde24ba270766d4472bdd6176cc415


---

# Az Intune-konzolnézetek testre szabása a rendszergazdai szerepköröknek megfelelően
A Microsoft Intune rendszergazdai konzolnézeteinek szűrésével lehetősége van arra, hogy a rendszergazdáknak csak azokat az elemeket jelenítse meg, amelyeket az adott szerepkör esetén látniuk kell. Engedélyezheti például, hogy kizárólag a felügyeleti konzol operátorai frissíthessék a kártevő szoftverek meghatározásait vagy állíthassák alaphelyzetbe az eszközök jelszavait. Ezt úgy hajthatja végre, ha előre definiált **megjelöléseket** használ, amelyeket az adott felhasználókhoz rendel. A felügyeleti konzol használatakor e felhasználók kizárólag a megjelölésüknek megfelelő elemeket fogják ott látni.

## Egyéni nézet létrehozása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com) válassza a **Felügyelet** &gt; **Szolgáltatás-rendszergazdák** elemet.

2.  A szolgáltatás-rendszergazdák listájából válassza ki azt a felhasználót, akinek megjelölését módosítani kívánja, majd válassza a **Hozzáférés kezelése** lehetőséget.

3.  A **Hozzáférés kezelése** párbeszédpanelen válassza ki azt a hozzáférési szintet, amelyet a kiválasztott felhasználóhoz kíván rendelni. A következő lehetőségek közül választhat:

    -   **Teljes hozzáférés**
    -   **Csak olvasási hozzáférés**
    -   **Segélyszolgálat – Csoportok csomópont**

    A teljes hozzáférés és a csak olvasási hozzáférés jelentése magától értetődő. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    A **Segélyszolgálat – Csoportok csomópont** hozzáférési szint korlátozza, hogy a rendszergazda mit láthat és mit tehet meg az alábbiak közül:

    -   Láthatja a felhasználók és az eszközök listáját. A rendszergazda nem használhat szűrőket a nézet módosításához. Ön azonban csoportszűréssel módosíthatja a rendszergazdai nézeteket. További információkért lásd: [Csoportok használata felhasználók és eszközök kezelésére a Microsoft Intune-nal](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Kinyomtathatja a felhasználók és az eszközök listáját

    -   Exportálja a felhasználók és az eszközök listáját

    -   Megtekintheti egy felhasználó vagy egy eszköz tulajdonságait

    -   Hajtsa végre a következő távoli feladatokat:

        -   Teljes kártevő-ellenőrzés futtatása

        -   Gyors kártevő-ellenőrzés futtatása

        -   A számítógép újraindítása

        -   Kártevő-definíciók frissítése

        -   A házirendek frissítése

        -   A leltár frissítése

        -   Egy eszköz távoli zárolása

        -   PIN-kód alaphelyzetbe állítása

Amikor az így beállított rendszergazda legközelebb megnyitja az Intune felügyeleti konzolt, az Ön által megadott hozzáférési szintet kapja meg.



<!--HONumber=Jun16_HO4-->


