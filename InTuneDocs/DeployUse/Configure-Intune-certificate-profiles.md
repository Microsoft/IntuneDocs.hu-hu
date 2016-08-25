---
title: "Tanúsítványprofilok konfigurálása | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ee6b3607688cb02be7316b83e10424dfbea9746b
ms.openlocfilehash: 8343abe8861468bbba27272aa1f3569390cb826b


---

# Intune-tanúsítványprofilok konfigurálása
Ha az [SCEP-tanúsítványinfrastruktúra konfigurálása](configure-certificate-infrastructure-for-scep.md) vagy a [PFX-tanúsítványinfrastruktúra konfigurálása](configure-certificate-infrastructure-for-pfx.md) részben leírtak szerint konfigurálta az infrastruktúrát és a tanúsítványokat, nekiláthat a tanúsítványprofilok konfigurálásának:

**1. feladat** – Megbízható legfelső szintű hitelesítésszolgáltató tanúsítványának exportálása **2. feladat** – Megbízható hitelesítésszolgáltatói tanúsítványprofilok létrehozása **3. feladat** – Két lehetősége van:

SCEP-tanúsítványprofilok létrehozása

.PFX-tanúsítványprofilok létrehozása

### 1. feladat – Megbízható főtanúsítvány exportálása
Exportálja a megbízható legfelső szintű hitelesítésszolgáltató tanúsítványát **.cer** fájlként a vállalati hitelesítésszolgáltatóról vagy az abban megbízó bármelyik eszközről. A titkos kulcsot nem exportálja.

Ezt a tanúsítványt a főtanúsítvány-profil konfigurálásakor kell importálnia.

### 2. feladat – Megbízható tanúsítványprofilok létrehozása
Ahhoz, hogy SCEP- vagy .PFX-tanúsítványprofilt hozhasson létre, először létre kell hoznia egy **megbízható tanúsítványprofilt**. Minden mobileszközplatformhoz külön megbízható tanúsítványprofillal és SCEP. vagy .PFS-profillal kell rendelkeznie.

##### Megbízható tanúsítványprofil létrehozásához

1.  Nyissa meg az [Intune felügyeleti konzolját](https://manage.microsoft.com), és kattintson a **Házirend** &gt; **Házirend hozzáadása** elemre.

2.  Konfigurálja a következő házirendtípusok egyikét:

    **Android &gt; Megbízható tanúsítványprofil (Android 4 és újabb)**

    **iOS &gt; Megbízható tanúsítványprofil (iOS 7.1 és újabb)**

    **Mac OS X &gt; Megbízható tanúsítványprofil (Mac OS X 10.9 és újabb)**

    **Windows &gt; Megbízható tanúsítványprofil (Windows 8.1 és újabb)**

    **Windows &gt; Megbízható tanúsítványprofil (Windows Phone 8.1 és újabb)**

    További információ: [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Konfigurálja a megbízható tanúsítványprofil beállításait az Android, iOS, Mac OS X, Windows 8.1 vagy Windows Phone 8.1. rendszerhez az alábbi információk megadásával: A **Tanúsítványfájl** beállításnál importálja a kiállító hitelesítésszolgáltatótól exportált megbízható legfelső szintű hitelesítésszolgáltató tanúsítványát (**.cer-fájl**). A **Céltár** beállítás kizárólag olyan Windows 8.1-es vagy újabb rendszerrel futó eszközökre vonatkozik, amelyeken egynél több tanúsítványtár érhető el.


4.  Ha elkészült, kattintson a **Házirend mentése**gombra.

Ekkor megjelenik az új házirend a **Házirend** munkaterületen, és készen áll a központi telepítésre.

### 3. feladat – SCEP- vagy .PFX-tanúsítványprofilok létrehozása
Ha létrehozott egy megbízható hitelesítésszolgáltatói tanúsítványprofilt, akkor létre kell hoznia a használni kívánt egyes platformok SCEP- vagy .PFX-tanúsítványprofilját is. Az SCEP-tanúsítványprofil létrehozásakor meg kell adnia egy ugyanarra a platformra vonatkozó megbízható tanúsítványprofilt. Ez a művelet összeköti a két tanúsítványprofilt, de a profilok központi telepítését külön-külön kell elvégeznie.

##### SCEP-tanúsítványprofil létrehozásához

1.  Nyissa meg az [Intune felügyeleti konzolját](https://manage.microsoft.com), és kattintson a **Házirend** &gt; **Házirend hozzáadása** elemre.

2.  Konfigurálja a következő házirendtípusok egyikét:

    **Android &gt; SCEP-tanúsítványprofil (Android 4 és újabb)**

    **iOS &gt; SCEP-tanúsítványprofil (iOS 7.1 és újabb)**

    **Mac OS X &gt; SCEP-tanúsítványprofil (Mac OS X 10.9 és újabb)**

    **Windows &gt; SCEP-tanúsítványprofil (Windows 8.1 és újabb)**

    **Windows &gt; SCEP-tanúsítványprofil (Windows Phone 8.1 és újabb)**

    További információ: [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  A profilkonfigurációs oldalon szereplő utasításokat követve végezze el az SCEP-tanúsítványprofil beállítását.

4.  Ha elkészült, kattintson a **Házirend mentése**gombra.

Ekkor megjelenik az új házirend a **Házirend** munkaterületen, és készen áll a központi telepítésre.

##### .PFX-tanúsítványprofil létrehozásához

1.  Nyissa meg az [Intune felügyeleti konzolját](https://manage.microsoft.com), és kattintson a **Házirend** &gt; **Házirend hozzáadása** elemre.

2.  Konfigurálja a következő házirendtípusok egyikét:



-   **Android &gt; .PFX-tanúsítványprofil (Android 4 és újabb)**

    -   **Windows &gt; PKCS #12 (.PFX) tanúsítványprofil (Windows 10 és újabb)**

    -   **Windows &gt; PKCS #12 (.PFX) tanúsítványprofil (Windows Phone 10 és újabb)**

    -    **iOS > PKCS #12 (.PFX) tanúsítványprofil (iOS 7.1 és újabb)**    

    További információ: [Az eszközök beállításainak és funkcióinak kezelése a Microsoft Intune-házirendek használatával](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Adja meg a tanúsítványűrlapon kért adatokat.

4.  Ha elkészült, kattintson a **Házirend mentése**gombra.

Ekkor megjelenik az új házirend a **Házirend** munkaterületen, és készen áll a központi telepítésre.

## Tanúsítványprofilok központi telepítése
A tanúsítványprofilok telepítésekor a rendszer telepíti a megbízható hitelesítésszolgáltatói tanúsítványprofilból származó tanúsítványfájlt az eszközökre, és az eszközök létrehoznak egy tanúsítványkérelmet az SCEP- vagy a .PFX-tanúsítványprofil segítségével.

A tanúsítványprofilok csak a megfelelő eszközökre települnek, a profil létrehozásakor használt platformtípus alapján.

-   A tanúsítványprofilokat telepítheti felhasználócsoportokra és eszközcsoportokra is.

    > [!TIP]
    > Ahhoz, hogy a tanúsítványok gyorsan meg tudjanak jelenni az eszközökön az eszközök regisztrálása után, ajánlott felhasználócsoporthoz való telepítést választani a tanúsítványprofilhoz (az eszközcsoporthoz való telepítés helyett). Ha eszközcsoportra telepít, akkor teljes eszközregisztráció szükséges, mielőtt az eszköz megkaphatná a házirendet.

-   Az egyes profilok telepítése ugyan külön történik, de a megbízható főtanúsítvány-profilt és az SCEP/.PFX-profilt egyaránt telepítenie kell, különben az SCEP/.PFX-tanúsítási házirend alkalmazása sikertelen lesz.

A tanúsítványprofilok központi telepítése ugyanúgy zajlik, mint az Intune más házirendjeinek telepítése.

1.  A **Házirend** munkaterületen válassza ki a telepíteni kívánt házirendet, majd kattintson a **Központi telepítés kezelése**lehetőségre.

2.  A **Telepítések kezelése** párbeszédpanelen:

    -   **A szabályzat telepítése** – Válasszon ki egy vagy több olyan csoportot, amelynek telepíteni kívánja a szabályzatot, majd kattintson a **Hozzáadás** &gt; **OK** gombra.

    -   **A párbeszédpanel bezárása telepítés nélkül** – Kattintson a **Mégse** gombra.

Ha egy már telepített házirendet választ ki, a házirendlista alsó részén további információkat láthat róla.
###  További lépések

Ezt követően a tanúsítványok segítségével biztonságosabbá teheti az e-mail-, Wi-Fi- és VPN-profilok használatát:

-  [Vállalati levelezéshez való hozzáférés konfigurálása e-mail profilokkal](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Wi-Fi-kapcsolatok a Microsoft Intune-ban](wi-fi-connections-in-microsoft-intune.md)
-  [VPN-kapcsolatok a Microsoft Intune-ban](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


