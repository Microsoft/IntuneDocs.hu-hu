---
title: "Vállalati erőforrások elérésének lehetővé tétele tanúsítványprofilokkal | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 1d2e6676714daba76a9b54553b4ad1af23a0f880


---

# Az erőforrások biztonságos elérése a Microsoft Intune tanúsítványprofiljai segítségével
Amikor engedélyezi a vállalati erőforrások VPN-en, Wi-Fi-n vagy e-mailes profilokon keresztüli hozzáférését, biztonságossá teheti ezt a hozzáférést az egyes felhasználói eszközökre telepített tanúsítvánnyal. Működési elv:

1. Győződjön meg arról, hogy már működik a megfelelő tanúsítványinfrastruktúra a [Configure certificate infrastructure for SCEP](configure-certificate-infrastructure-for-scep.md) (SCEP-tanúsítványinfrastruktúra konfigurálása) vagy a [Configure certificate infrastructure for PFX](configure-certificate-infrastructure-for-pfx.md) (PFX-tanúsítványinfrastruktúra konfigurálása) című témakörben foglaltak szerint.

2. Telepítsen egy főtanúsítványt (vagy köztes hitelesítésszolgáltatói tanúsítványt) minden eszközön, hogy az eszköz felismerje a hitelesítésszolgáltató érvényességét. Ezt egy **megbízhatótanúsítvány-profil** létrehozásával és telepítésével teheti meg. A profil telepítésekor az Intune-nal felügyelt eszközök lekérik és megkapják a főtanúsítványt. Mindegyik platformhoz különálló profilt kell létrehoznia. A **megbízható tanúsítványprofil** a következő platformokhoz érhető el:
 -  iOS 7.1-es és újabb verziók
 -  Mac OS X 10.9 és újabb verziók
 -  Android 4.0 és újabb verziók
 -  Windows 8.1 és újabb
 -  Windows Phone 8.1 és újabb verziók

3. Állítsa be a következő témakörnek megfelelően, hogy mindegyik eszköz tanúsítványt kérjen az e-mailes, VPN- és Wi-Fi-hozzáférés hitelesítéséhez: [Intune-tanúsítványprofilok konfigurálása](configure-intune-certificate-profiles.md). **PKCS #12 (.PFX) tanúsítványt** vagy **SCEP-tanúsítványt** telepíthet a következő platformot használó eszközökre:

-  Android 4.0 és újabb verziók
-  iOS 7.1-es és újabb verziók
-  Windows 10 (asztali és mobilverzió), illetve újabb

Használja az **SCEP-tanúsítványprofilt** a következőkhöz:
-   Mac OS X 10.9 és újabb verziók
-   Windows Phone 8.1 és újabb verziók

Mindegyik platformhoz különálló profilt kell létrehoznia. A profil létrehozásakor a már létrehozott **megbízható főtanúsítvány-profillal** társítja azt.

> [!NOTE]           
> -    Ha nem rendelkezik vállalati hitelesítésszolgáltatóval, létre kell hoznia egyet.
>- Ha az eszközplatformjai alapján úgy dönt, hogy SCEP-profilt használ, egy NDES-kiszolgálót is konfigurálnia kell.
>-  SCEP- vagy .PFX-profilok használatához le kell töltenie és konfigurálnia kell a Microsoft Intune tanúsítvány-összekötőjét.
> Mindegyik említett eset konfigurálását a következő témakör ismerteti: [Tanúsítványinfrastruktúra konfigurálása](configure-certificate-infrastructure.md).

### További lépések
- [SCEP-tanúsítványinfrastruktúra konfigurálása](configure-certificate-infrastructure-for-scep.md)
- [PFX-tanúsítványinfrastruktúra konfigurálása](configure-certificate-infrastructure-for-pfx.md)
- [Intune-tanúsítványprofilok konfigurálása](configure-intune-certificate-profiles.md)



<!--HONumber=Jul16_HO1-->


