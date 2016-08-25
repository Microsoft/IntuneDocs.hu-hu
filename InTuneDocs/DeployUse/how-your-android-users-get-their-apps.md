---
title: "Android-felhasználói alkalmazások letöltése | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3bcf89636f9da8fd8bfa5cc52391742a9ce9f92
ms.openlocfilehash: 25571ce1b214c927f3dc2ea3968d00970621e474


---


# Android-felhasználói alkalmazások letöltése
Ez a témakör ismerteti, hogy végfelhasználói hol és hogyan juthatnak hozzá a Microsoft Intune-ban elérhetővé tett alkalmazásokhoz. 

**Kötelező alkalmazások** – A rendszergazda által kötelezően előírt alkalmazások, amelyeknek a telepítéséhez az adott platformtól függően minimális felhasználói beavatkozás szükséges.
 
- **Samsung Knox-eszközök**: ha kötelező alkalmazást Samsung Knox-eszközre telepít, a telepítés automatikusan és értesítések nélkül történik.
- **Natív (nem Samsung Knox) eszközök**: ha kötelező alkalmazást nem Samsung Knox-eszközre telepít, a telepítés a felhasználó eszközére nem automatikusan történik. A felhasználókat ebben az esetben felkéri a rendszer az alkalmazás telepítésére. Ha a felkérésre a felhasználó igennel válaszol, az alkalmazás letöltődik, majd a felhasználó értesítést kap arról, hogy a telepítést el kell végeznie. 

**Elérhető alkalmazások** – A Vállalati portál alkalmazáslistájában szereplő azon alkalmazások, amelyeknek a telepítése nem kötelező.

**Felügyelt alkalmazások** – Az Intune által szabályzatokkal felügyelt és „becsomagolt”, illetve az Intune Mobile Application Management (MAM) SDK-val készített alkalmazások. Ezek az alkalmazások az Intune-nal kezelhetők, és alkalmazás-házirendekkel felügyelhetők.

**Nem felügyelt alkalmazások** – Azok az alkalmazások, amelyeket nem az Intune csomagolt be, illetve amelyek nem foglalják magukban az Intune MAM SDK-t. Ezekre az alkalmazásokra nem alkalmazhatók alkalmazás-házirendek.

###További információ
[Alkalmazások hozzáadása Microsoft Intune-ban](/intune/deploy-use/add-apps)
[iOS felhasználói alkalmazások letöltése](how-your-ios-users-get-their-apps.md)
[Windows felhasználói alkalmazások letöltése](how-your-windows-users-get-their-apps.md)


<!--HONumber=Jul16_HO1-->


