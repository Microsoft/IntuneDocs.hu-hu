---
title: Az Intune Exchange Connector gyakori hibáinak elhárítása
titleSuffix: Microsoft Intune
description: A helyszíni Microsoft Intune Exchange Connector gyakori hibáinak elhárítása és megoldása
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b30a7e843850d6918abc2e76f84397a1f197516f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508856"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Az Intune Exchange Connector gyakori hibáinak elhárítása

Ez a cikk segítséget nyújt az Intune-rendszergazda számára az Intune Exchange Connector működésével kapcsolatos konkrét hibák és üzenetek megoldásában.  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>A konfigurálás sikertelen volt, és a 0x0000001 hibakódot adott vissza.

**Probléma**:  
A Microsoft Intune Exchange Connector konfigurálásakor a következő hibaüzenet jelenik meg:

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

Ez a probléma akkor fordulhat elő, ha az internetes proxy beállításai helytelenül vannak konfigurálva.

**Megoldás**:  
Proxybeállítások konfigurálása:
1. Forduljon a helyi hálózati rendszergazdához, és győződjön meg arról, hogy a proxybeállítások megfelelően vannak konfigurálva. 
2. A **netsh WinHTTP** parancs használatával konfigurálja a proxykiszolgálót, és adja hozzá a szükséges kizárási listát. Példa:  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>A konfigurálás sikertelen volt, és a 0x000000b hibakódot adott vissza.   

**Probléma**:  
A Microsoft Intune Exchange Connector konfigurálásakor a következő hibaüzenet jelenik meg:  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Ez a probléma akkor fordulhat elő, ha az Intune-ba való bejelentkezéshez használt fiók nem egy globális Intune-rendszergazdai fiók.

**Megoldás**:  
Jelentkezzen be az Intune-ba egy globális rendszergazdai fiókkal, vagy vegye fel a fiókját a globális rendszergazdai csoportba. További információ: [szerepköralapú adminisztrációs vezérlés (RBAC) Microsoft Intuneval](../fundamentals/role-based-access-control.md).

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>A konfigurálás sikertelen volt, és a 0x0000006 hibakódot adott vissza.

**Probléma**:  
A Microsoft Intune Exchange Connector konfigurálásakor a következő hibaüzenet jelenik meg:  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
Ez a hiba akkor fordulhat elő, ha egy proxykiszolgáló csatlakozik az internethez, és blokkolja az Intune szolgáltatás felé irányuló forgalmat. Annak megállapításához, hogy a proxy használatban van-e, nyissa meg a **vezérlőpult** > **internetes beállítások**elemét, válassza a **Csatlakozás** lapot, majd kattintson a **LAN-beállítások**elemre.

**Megoldás**:  

- **1. lehetőség** – távolítsa el a proxybeállításokat, hogy a számítógép ne a proxyn keresztül kapcsolódjon az internethez.  

- **2. lehetőség** – konfigurálja úgy a proxykiszolgálót, hogy engedélyezze a kommunikációt az Intune szolgáltatással az [Intune Exchange Connector követelményeinek](exchange-connector-install.md#intune-exchange-connector-requirements)megfelelően.



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>7000-es vagy 7041-os esemény: Microsoft Intune Exchange Connector szolgáltatás nem indul el

**Probléma**:  
Az iOS-eszközök nem regisztrálhatnak az Intune-ban, és a következő hibaüzenetek valamelyikét generálják:  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
Ez a probléma akkor fordulhat elő, ha az **WIEC_User** -fiók nem rendelkezik a helyi házirendben a **Bejelentkezés szolgáltatásként** felhasználói jogosultsággal.

**Megoldás**:  
Az Intune Exchange Connectort futtató számítógépen rendelje hozzá a **Bejelentkezés szolgáltatásként** felhasználói jogosultságot a **WIEC_User** -szolgáltatásfiók számára. Ha a számítógép egy fürt egyik csomópontja, akkor a fürt összes csomópontján ellenőrizze, hogy a *Bejelentkezés szolgáltatásként* felhasználói jogosultsággal van-e hozzárendelve a fürtszolgáltatási fiókhoz.  

Az alábbi lépéseket követve rendelje hozzá a **Bejelentkezés szolgáltatásként** felhasználói jogosultságot a számítógépen lévő **WIEC_User** -szolgáltatásfiók számára:

1. Jelentkezzen be a számítógépre rendszergazdaként vagy a rendszergazdák csoport tagjaként.
2. Futtassa a **secpol. msc fájlt** a helyi biztonsági házirend megnyitásához.
3. Lépjen a **biztonsági beállítások** > **helyi házirendek**elemre, majd válassza a **felhasználói jogok kiosztása**elemet.
4. A jobb oldali ablaktáblán kattintson duplán a **Bejelentkezés szolgáltatásként**lehetőségre.
5. Válassza a **felhasználó vagy csoport hozzáadása**lehetőséget, adja hozzá **WIEC_USER** a Szabályzathoz, majd kattintson kétszer **az OK gombra** .

Ha a **Bejelentkezés szolgáltatásként** felhasználói jogosultság **WIEC_User** , de később el lett távolítva, vegye fel a kapcsolatot a tartományi rendszergazdával, és állapítsa meg, hogy egy csoportházirend-beállítás felülírja-e.  

## <a name="next-steps"></a>További lépések  

A következő cikk az adott hibák megoldásához nyújt segítséget:
- [Az Intune Exchange Connector és a git gyakori problémáinak elhárítása](troubleshoot-exchange-connector-common-problems.md) 

Kérjen segítséget a támogatási szolgálattól vagy az Intune-Közösségtől.
- A probléma megoldásához, illetve a Microsoft támogatási esetének megnyitásához tekintse meg a [támogatás kérése](../fundamentals/get-support.md) az Intune-konzollal való használatát ismertető témakört. 
- A probléma közzététele a [Microsoft Intune fórumokon](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
