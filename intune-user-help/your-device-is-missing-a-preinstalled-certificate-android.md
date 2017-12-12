---
title: "Az eszközhöz hiányzik egy tanúsítvány | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d6bd59800b13539558fbf56afab9fe5293f3e5bd
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/12/2017
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>Az androidos eszközhöz hiányzik egy, rendszerint a telefonon előre telepített tanúsítvány

Ha az eszköz nincs regisztrálva az Intune-ban, és hiányzik róla egy, rendszerint a telefonon előre telepített tanúsítvány, nem fog tudni bejelentkezni a Céges portál alkalmazásba. Amikor megpróbál bejelentkezni, a következő üzenet jelenik meg:

![képernyőfelvétel-hibaüzenet-hiányzó-tanúsítványról](./media/andr-cert_install-1-cert_missing.png)

A probléma megoldásához a megfelelő tanúsítványra lesz szüksége a [Digicert tanúsítványoldaláról](https://www.digicert.com/digicert-root-certificates.htm).

1. Keresse meg és töltse le a __Baltimore CyberTrust legfelsőbb szintű__ tanúsítványát. Ezt közvetlenül is letöltheti [innen](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

2. A legújabb értesítések megjelenítéséhez húzza le az értesítési sávot a képernyő tetejéről , és koppintson a **BaltimoreCyberTrustRoot.crt** elemre.

3. Az eszköze kérni fogja a **Name the Certificate**.(Tanúsítvány elnevezése) lehetőséget. Ne változtassa meg a megjelenő alapértelmezett tanúsítványnevet.

4. Győződjön meg arról, hogy **Credential Use** (Hitelesítő adatok használata) beállítás értéke **Used for VPN and apps** (VPN-hez és az alkalmazásokhoz használt), és koppintson az **OK** gombra.

    ![képernyőfelvétel-tanúsítvány-neve-párbeszédpanel-Baltimore-tanúsítványnévvel](./media/andr-cert_install-2-add_cert_name.png)

5. Zárja be a böngészőt és a Céges portál alkalmazást.

6. Nyissa ismét meg a Céges portál alkalmazást. Ekkor már be kell, hogy tudjon jelentkezni a Céges portál alkalmazásba. Ha még mindig nem tudja használni a Céges portál alkalmazást, további utasításokért lépjen kapcsolatba a cég informatikai támogató szolgálatával a [Céges portál webhelyen](https://portal.manage.microsoft.com#HelpDeskDialog) megadott elérhetőségeken.

>[!NOTE]
> Ha a tanúsítvány telepítése nem oldja meg a problémát és egy újabb „hiányzó tanúsítvány” hibaüzenetet kap, további lépések szükségesek a [hiányzó tanúsítvány telepítéséhez](your-device-is-missing-an-IT-required-certificate-android.md).

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://portal.manage.microsoft.com#HelpDeskDialog).
