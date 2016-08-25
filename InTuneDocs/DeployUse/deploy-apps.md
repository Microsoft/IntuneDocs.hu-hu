---
title: "Alkalmazások telepítése | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: e6b995118e66fd146a68b49ce4decdcbd1fe3572
ms.openlocfilehash: a68cb85602bd585539147c7d7d38c0d906f2b1f7


---

# Alkalmazások telepítése a Microsoft Intune-ban

Ez a témakör megmagyarázza azokat a fogalmakat, amelyeknek a megértésére feltétlenül szüksége lesz ahhoz, hogy alkalmazásokat telepítsen a Microsoft Intune-ban.


## Alkalmazástelepítési műveletek
Az alkalmazások telepítésekor a következő telepítési műveletek közül választhat:

-   **Szükséges telepítés** – az alkalmazás végfelhasználói beavatkozás nélkül települ az eszközön.

    > [!TIP] Nem felügyelt üzemmódban működő iOS-eszközök és az összes Android-eszköz esetében az alkalmazás csak akkor települ, ha a felhasználó elfogadja az alkalmazásajánlatot.
    > 
    >  Ha egy végfelhasználó törl egy Ön által kötelezőnek jelölt alkalmazást, az Intune a következő leltározási ciklus során (amely általában 7 naponta következik be) automatikusan újratelepíti az alkalmazást.

-   **Elérhető telepítés** – az alkalmazás megjelenik a vállalati portálon, és a végfelhasználók igény szerint telepíthetik.

-   **Eltávolítás** – a rendszer eltávolítja az alkalmazást az eszközről.

-   **Nem alkalmazható** – az alkalmazás nem jelenik meg a vállalati portálon, és nem települ egyik eszközön sem.

#### Az egyes telepítőtípusokhoz elérhető telepítési műveletek

|Telepítő típusa|Szükséges telepítés|Elérhető telepítés|Eltávolítás|Nem alkalmazható|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows-alkalmazáscsomag (felhasználói csoport számára telepített)|Igen|Igen|Igen|Igen|
|Windows-alkalmazáscsomag (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
|Mobileszközökhöz készült alkalmazáscsomag (felhasználói csoport számára telepített)|Igen|Igen|Igen|Igen|
|Mobileszközökhöz készült alkalmazáscsomag (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
|Windows Installer (felhasználói csoport számára telepített)|Nem|Igen|Nem|Igen|
|Windows Installer (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
|Külső hivatkozás (felhasználói csoport számára telepített)|Nem|Igen|Nem|Igen|
|Külső hivatkozás (eszközcsoport számára telepített)|Nem|Nem|Nem|Nem|
|Felügyelt iOS-alkalmazás az App Store-ból (felhasználói csoport számára telepített)|Igen|Igen|Igen|Igen|
|Felügyelt iOS-alkalmazás az App Store-ból (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
> [!TIP] Ha az alkalmazás telepítése során felhasználói és eszközcsoportokat egyaránt megad, az alkalmazást csak **Elérhető telepítés módban** telepítheti.

## A telepítés során fellépő ütközések
Arra az esetre, ha ugyanazon telepítési művelettel két telepítés érkezik egy eszközre, az alábbi szabályok vonatkoznak:

-   Az eszközcsoport számára végrehajtott telepítések elsőbbséget élveznek a felhasználói csoport számára végrehajtott telepítésekkel szemben. Ha azonban egy alkalmazást az **Elérhető** telepítési művelettel telepít egy felhasználói csoport számára, és ugyanazt az alkalmazást egy eszközcsoport számára is telepíti a **Nem alkalmazható**telepítési művelettel, a felhasználók elérhetik az alkalmazást a vállalati portálon, és telepíthetik.

-   A telepítési műveletek elsőbbséget élveznek az eltávolítási műveletekkel szemben.

-   Ha egy eszköz számára egy kötelező és egy elérhető telepítés is rendelkezésre áll, a műveletek közösen hajthatók végre (az alkalmazás egyszerre kötelező és elérhető – a végfelhasználó tehát a vállalati portálról is telepítheti a kötelező telepítés megkezdése előtt).


## További lépések

Ismerje meg, hogyan [telepíthet alkalmazásokat a Microsoft Intune-ban](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Jun16_HO3-->


