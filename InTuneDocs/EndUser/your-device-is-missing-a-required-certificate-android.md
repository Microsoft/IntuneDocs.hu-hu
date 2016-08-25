---
title: "Az eszközhöz hiányzik egy szükséges tanúsítvány | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
ms.reviewer: arnab
ms.suite: ems
ms.sourcegitcommit: 0bb435b87c937ea118a0794c8332b9a8f268d36e
ms.openlocfilehash: 6e887d226228d073dc136b50ba9320ada996a6cd


---


# Az eszközhöz hiányzik egy szükséges tanúsítvány
Ha az androidos eszköz nincs regisztrálva az Intune-ban, és hiányzik róla egy, rendszerint a telefonon előre telepített tanúsítvány, nem fog tudni bejelentkezni az androidos Vállalati portál alkalmazásba. Amikor megpróbál bejelentkezni, a következő üzenet jelenik meg:

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

A probléma megoldásához és a szükséges tanúsítvány beszerzéséhez hajtsa végre a következő lépéseket:

1.  Böngészőben nyissa meg a [Digicert tanúsítványlapját](https://www.digicert.com/digicert-root-certificates.htm).

2.  Keresse meg és töltse le a Baltimore CyberTrust legfelső szintű tanúsítványát (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

3.  Húzza le az értesítéseket fentről, és koppintson a **BaltimoreCyberTrustRoot.crt** elemre az értesítések listájában.

4.  A **Name the Certificate** (A tanúsítvány elnevezése) képernyőn fogadja el az alapértelmezett tanúsítványnevet.

5. Győződjön meg arról, hogy **Credential Use** (Hitelesítő adatok használata) beállítás értéke **Used for VPN and apps** (VPN-hez és az alkalmazásokhoz használt), és koppintson az **OK** gombra.

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. Zárja be a böngészőt és a Vállalati portál alkalmazást.

7. Nyissa ismét meg a Vállalati portál alkalmazást. Ekkor már be kell, hogy tudjon jelentkezni a Vállalati portál alkalmazásba. Ha segítségre van szüksége, lépjen kapcsolatba a rendszergazdával.

További segítségre van szüksége? Forduljon a rendszergazdához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).


<!--HONumber=Jun16_HO4-->


