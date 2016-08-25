---
title: "A Microsoft Intune Exchange-összekötő konfigurálása szolgáltatott Exchange-hez | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: 6cfc532cba2f53034c4c3ef0c2df3d6c1e6e7841


---

# Intune szolgáltatások közötti összekötő konfigurálása az Exchange Online-hoz

Az alábbi információk segítségével a Microsoft Intune-t az Office 365 által szolgáltatott Exchange Online-hoz csatlakoztathatja.

## A Service to Service Connector alkalmazásra vonatkozó követelmények
A **Service to Service Connector** csak a szolgáltatott Exchange-et támogatja, így nincsenek a helyszíni infrastruktúrára vonatkozó követelményei.

|Követelmény|További információ|
|---------------|--------------------|
|Legyen konfigurálva és fusson a szolgáltatott Exchange|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Mobileszköz-kezelő szolgáltató| [A Microsoft Intune beállítása mobileszköz-kezelő szolgáltatóként](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Microsoft Exchange verzió|Olyan Office 365-előfizetéssel kell rendelkeznie, amelyhez tartozik egy Exchange Server 2013 vagy későbbi verziójú bérlő. Mindaddig, amíg a bérlő az Exchange Server 2013 vagy egy későbbi verzió, az összekötő ugyanabban a környezetben támogatja az Exchange Server 2010-et is.|
|Active Directory-szinkronizálás|Mielőtt bármely összekötővel csatlakoztatná az Intune Connectort az Exchange-kiszolgálóhoz, [állítsa be az Active Directory-szinkronizálást](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3), hogy a helyi felhasználók és biztonsági csoportok szinkronizálva legyenek az Azure AD-példányával.|

### Exchange-parancsmagokkal kapcsolatos követelmények

Létre kell hoznia egy Exchange Online-felhasználói fiókot is, amelyet az Intune Exchange-összekötő fog használni. A fióknak engedéllyel kell rendelkeznie az Intune felügyeleti konzol használatához, illetve a Windows PowerShell Exchange-parancsmagok futtatásához.

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## A szolgáltatások közötti összekötő beállítása

1. Nyissa meg a [Microsoft Intune felügyeleti konzolt](http://manage.microsoft.com) a [fenti](#exchange-cmdlet-requirements) parancsmagokhoz Exchange-rendszergazdai jogosultságokkal és engedélyekkel rendelkező felhasználói fiókkal. A Microsoft Intune az aktuálisan bejelentkezett felhasználó e-mail címét használja a kapcsolat beállításához.

2.  A munkaterület parancsikon-ablaktábláján válassza a **FELÜGYELET** lehetőséget, majd lépjen a **Mobileszköz-kezelés** > **Microsoft Exchange** > **Exchange-kapcsolat beállítása** pontra.
![A Service To Service Connector telepítése oldal](../media/intunesa5cservicetoserviceconnector.png)

3.  Az **Exchange-kapcsolat beállítása** lapon kattintson a **Service To Service Connector telepítése** parancsra.


A Service-to-Service Connector konfigurációja és szinkronizálása az üzemeltetett Exchange-környezettel automatikusan megtörténik.

## Az Exchange-kapcsolat ellenőrzése

Az Exchange Connector sikeres beállítása után kattintson az Intune felügyeleti konzol **FELÜGYELET** munkaterületére, majd a **Mobileszköz-kezelés** > **Microsoft Exchange** elemre, és ellenőrizze, hogy a megadott adatok megjelennek-e az **Exchange-kapcsolat adatai** területen.

Ellenőrizheti a legutóbbi sikeres szinkronizálási kísérlet dátumát és időpontját is.



<!--HONumber=Jun16_HO4-->


