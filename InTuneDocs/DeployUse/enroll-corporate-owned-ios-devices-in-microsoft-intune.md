---
title: "A vállalat által birtokolt iOS-eszközök regisztrálása a Microsoft Intune-ban | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 48359b44bec9ac3e1c9510debc01d2cf8abf6d2b


---

# A vállalat által birtokolt iOS-eszközök regisztrálása a Microsoft Intune-ban[1502]
A Microsoft Intune támogatja a vállalat által birtokolt iOS-eszközök regisztrálását az Apple Device Enrollment Program (DEP) vagy a Mac számítógépeken futó [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) eszköz segítségével.

A vállalat által birtokolt iOS-eszközöket háromféleképpen regisztrálhatja:

-   **Regisztráció a telepítő segéddel** – A gyár állítja alaphelyzetbe az eszközt, és felkészíti a beállításhoz az új felhasználó számára. Ennél a módszernél a rendszergazdának a regisztráció előkonfigurálásához az iOS-eszközt USB kapcsolaton keresztül egy Apple Configuratort futtató Mac számítógéphez kell csatlakoztatnia. Az eszközök ezután a felhasználóikhoz kerülnek, akik a Beállítási asszisztens folyamatának futtatása során munkahelyi vagy iskolai hitelesítő adataikkal konfigurálják az eszközt, és befejezik a regisztrációs folyamatot. [Apple Configuratort és Beállítási asszisztenst futtató iOS-eszközök regisztrálása](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   **Közvetlen regisztrálás** – Létrejön egy Apple Configurator-kompatibilis fájl, amely az eszköz előkészítésez szükséges. A regisztrált eszköz nincs gyári alaphelyzetbe állítva, de egyetlen felhasználóhoz sem kapcsolódik. Ennél a módszernél a rendszergazdának az iOS-eszköz regisztrálásához az eszközt USB kapcsolaton keresztül egy Apple Configuratort futtató Mac számítógéphez kell csatlakoznia. [Az Apple Configurator közvetlen regisztrációját használó iOS-eszközök regisztrálása](ios-direct-enrollment-in-microsoft-intune.md)

-   **Készülékregisztrációs program (DEP)** – Vezeték nélkül telepít egy regisztrációs profilt az Apple készülékregisztrációs programjában megvásárolt készülékekre. Amikor a felhasználó a Beállítási asszisztenst futtatja az eszközön, az eszköz regisztrálódik az Intune-ban.  A DEP programon keresztül regisztrált eszközök regisztrációját a felhasználók nem törölhetik. [A készülékregisztrációs programban (DEP) részt vevő iOS-eszközök regisztrálása](ios-device-enrollment-program-in-microsoft-intune.md)




### További információ
[Felkészülés az eszközök regisztrálására a Microsoft Intune-ban](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


