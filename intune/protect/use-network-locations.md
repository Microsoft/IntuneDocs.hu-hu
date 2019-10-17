---
title: Android-eszközök kötése hálózati hely szerint a Microsoft Intune-ban – Azure | Microsoft Docs
description: Hozzon létre vagy konfiguráljon hálózati helyeket a Microsoft Intune-ban az Android-eszközökhöz. Az eszközök hálózati helye alapján jelölheti meg azokat nem megfelelőként. Ha az eszköz a hálózati helyen kívülre kerül, blokkolhatja a vállalati erőforrásokhoz való hozzáférést.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: edc1a241d327bd98db8ae50187b1e1aed5e00e71
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503552"
---
# <a name="use-locations-network-fence-in-intune"></a>Helyek (hálózati kerítés) használata az Intune-ban

Letilthatja a vállalati hálózathoz való hozzáférést, ha az eszköz elhagy egy bizonyos helyet. Az Intune-ban a **Helyek** funkció biztosítja ezt a szolgáltatást. 

Létrehozhat egy hálózati helyen alapuló megfelelőségi szabályzatot, amelyet másként hálózati kerítésnek is hívnak. A szabályzat biztosítja, hogy az eszköznek munkahelyi hálózathoz kelljen csatlakoznia a megfelelőséghez. Ez a szabályzat feltételes hozzáférési házirendekkel használható, így az eszközök *csak* akkor férhetnek hozzá a munkahelyi erőforrásokhoz, ha az eszköz csatlakoztatva van a munkahelyi hálózathoz. Ha az eszköz nem csatlakozik a munkahelyi hálózathoz, akkor nem megfelelő lesz, és nem fog tudni hozzáférni a munkahelyi erőforrásokhoz.

Vegye figyelembe a következő helyzetet:

A gyártási létesítményben néhány alkalmazott Android-eszközöket használ. Az alkalmazott kiviszi az Android-eszközt a létesítményből vagy üzemből. Az illetéktelen hozzáférés megakadályozásáért a következőket teheti:

1. Hozzon létre egy helyet IPv4-címtartománnyal, amelynek a **Gyártási szint** nevet adja.
2. Hozzon létre egy megfelelőségi szabályzatot, amely megköveteli, hogy ezek az eszközök a vállalati hálózathoz csatlakozzanak, és rendelje hozzá ezt a szabályzatot.
3. Ha az eszköz a gyártási üzemen kívül kerül, akkor nem megfelelőnek minősül, és nem fér hozzá a vállalati erőforrásokhoz.

Hozzáadhat [meg nem felelés esetén végrehajtandó műveleteket](#configure-the-actions-for-noncompliance) is. Amikor az eszköz ismét a helyszínen, a hálózati helyen van, újra hozzáférhet a vállalati erőforrásokhoz.

## <a name="prerequisites"></a>Előfeltételek

Helyalapú megfelelőségi szabályzat létrehozásához tegye a következőket:

- Hozzon létre egy hálózati helyet az IPv4 hálózati tartományban ahhoz az átjárókiszolgálóhoz, DHCP-kiszolgálóhoz és/vagy DNS-kiszolgálóhoz, amelyhez az eszköz csatlakozik
- Hozza létre azt a megfelelőségi szabályzatot, amely ezeket a helyeket használja, és meghatározza, hogy milyen műveletet kell végrehajtani, ha az eszköz már nem csatlakozik a hálózati helyhez
- Android 6.0-s és újabb eszközök frissített Céges portál alkalmazással

## <a name="create-a-location"></a>Hely létrehozása

1. Az Intune-ban válassza az **Eszközmegfelelőség** > **Helyek** > **Létrehozás** lehetőséget.

2. Adja meg a következő tulajdonságokat:  

   - Szükséges. Adja meg a hely **Név** mezejének értékét, például azt, hogy **Gyártási szint** vagy **44-es épület – biztonságos**.
   - Nem kötelező. Adjon meg egy **IPv4-tartományt** CIDR (Classless Interdomain Routing) jelöléssel, például: `aaa.bbb.ccc.ddd/n`.
   - Nem kötelező. Adja meg az **IPv4-átjáró** címét, például: `aaa.bbb.ccc.ddd`.
   - Nem kötelező. Adja meg az **IPv4 DHCP-kiszolgáló** címét, például: `aaa.bbb.ccc.ddd`.
   - Nem kötelező. Adja meg az **IPv4 DNS-kiszolgálók** címeinek listáját. Ezt a beállítás **részhalmaz-egyeztetést** használ. Ha az eszközön lévő IPv4-alapú DNS-kiszolgálók a megadott értékek részhalmazában találhatók, akkor az eszköz a kerítésen BELÜLINEK minősül. Mindenképp egy címet adjon meg soronként, például:  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - Nem kötelező. Adja meg a **DNS-utótagok** listáját. Ezt a beállítás **részhalmaz-egyeztetést** használ. Ha az eszközön lévő DNS-utótagok a megadott értékek részhalmazában találhatók, akkor az eszköz a kerítésen BELÜLINEK minősül. Soronként egy tartománynevet adjon meg, például:  
     `contoso.com`  
     `contoso.org`

3. **Mentse** a változtatásokat.

## <a name="create-the-location-compliance-policy"></a>A helymegfelelőségi szabályzat létrehozása

A megfelelőségi szabályzat létrehozásakor válassza az **Android** lehetőséget a **Platform** megadásakor. A **Helyek** területen kiválaszthat egy vagy több hozzáadott hálózati helyet. Ezek a helyek az eszközhöz létrehozandó hálózati kerítés részét képezik.

[A hálózati helyen alapuló megfelelőségi szabályzat létrehozása](compliance-policy-create-android.md#locations) szakasz nyújt némi útmutatást.

## <a name="configure-the-actions-for-noncompliance"></a>Meg nem felelés esetén végrehajtandó műveletek konfigurálása

A megfelelőségi szabályzat létrehozása után az eszközre a meg nem felelés esetén alkalmazandó alapértelmezett művelet vonatkozik. További műveleteket is hozzáadhat. Például hozzáadhat egy műveletet, amellyel e-mailt küld a felhasználónak, amikor az eszköz már nem megfelelő a helyek alapján.

A [Meg nem felelés esetén végrehajtandó műveletek hozzáadása](actions-for-noncompliance.md) nyújt némi útmutatót.

## <a name="company-portal-app"></a>Vállalati portál alkalmazás

Amikor az eszköz kapcsolódik a megadott helyekhez, az eszköz megfelelőként jelenik meg a Céges portál alkalmazásban. Ha az eszköz nem kapcsolódik valamelyik helyhez, az eszköz nem megfelelőként jelenik meg.

## <a name="next-steps"></a>További lépések
[Eszközmegfelelőségi szabályzatok figyelése](compliance-policy-monitor.md)  
[Első lépések a megfelelőségi szabályzatokkal](device-compliance-get-started.md)
