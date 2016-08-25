---
title: "Intune-licencek kezelése | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2847c9af38ae0ddddc8d76d548ae7abddc63e4c1
ms.openlocfilehash: e764dc73492db984fcbb118597ad1d08491d3427


---

# Intune licencek kezelése
Mielőtt a felhasználók bejelentkezhetnek az Intune szolgáltatásba, vagy regisztrálhatnák az eszközeiket a felügyeletbe, Önnek egy, az Intune-előfizetéséhez tartozó licencet kell hozzárendelnie minden felhasználóhoz az [Office 365 portállal](http://go.microsoft.com/fwlink/p/?LinkId=698854). A licenc hozzárendelése után a felhasználó neve megjelenik az Intune felügyeleti konzolján. A felhasználók ezt követően maximum öt eszközt regisztrálhatnak.

Előfordulhat, hogy a Microsoft Nagyvállalati mobilitási csomag (EMS) megoldást használó szervezeteknek vannak felhasználói, akik csak az EMS csomagban foglalt Azure Active Directory Premium vagy Intune szolgáltatást igénylik. Az [Azure Active Directory PowerShell-parancsmagok](https://msdn.microsoft.com/library/jj151815.aspx) használatával egy-egy szolgáltatás vagy a szolgáltatások egy részhalmaza is hozzárendelhető. További információ: [Intune-licencek kezelése a PowerShell használatával](start-with-a-paid-subscription-to-microsoft-intune-step-4-posh.md).

## Az Intune-licencek hozzárendelésének módja
Ha a felhasználói fiókok szinkronizálása a helyszíni Active Directoryból történik, vagy az [Office 365 portál](http://go.microsoft.com/fwlink/p/?LinkId=698854) segítségével manuálisan veszi fel azokat a felhőalapú szolgáltatások előfizetésébe, akkor a rendszer nem rendel hozzájuk automatikusan Intune-licencet. Ehelyett egy későbbi időpontban egy Intune bérlői rendszergazdának az Office 365 portálról kell egy licencet a felhasználóhoz rendelnie a felhasználói fiók szerkesztésével.

Ha az előfizetése a hozzá társított más felhőalapú szolgáltatásokkal közösen használja az Azure AD-t, Ön hozzáférhet az ezekbe a szolgáltatásokba felvett felhasználókhoz. Ezek a felhasználók mindaddig nem jogosultak a [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] használatára, amíg hozzájuk nem rendel egy licencet.

> [!TIP]
> Ha az [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] használatára jogosító licenc hozzárendelésére vagy visszavonására szolgáló beállítás nem érhető el, előfordulhat, hogy az előfizetés olyan mennyiségi licencelési lehetőségeket tartalmaz, mint amilyenek például a [Nagyvállalati mobilitási csomag](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx) használatakor érhetők el. A licencek hozzárendeléséről vagy visszavonásáról a licencelési lehetőségek dokumentációjában tájékozódhat.

## Intune felhasználói licenc hozzárendelése

Az [Office 365 portál](http://go.microsoft.com/fwlink/p/?LinkId=698854) használatával a felhőalapú felhasználók és licencek manuálisan hozzáadhatók, illetve hozzárendelhetők a felhőalapú felhasználói fiókokhoz és a helyszíni Active Directoryból az Azure AD-be szinkronizált fiókokhoz is.

1.  Jelentkezzen be az [Office 365 portálon](http://go.microsoft.com/fwlink/p/?LinkId=698854) bérlői rendszergazdai hitelesítő adataival, majd válassza a **Személyek** > **Minden felhasználó** lehetőséget.

2.  Válassza ki azt a felhasználói fiókot, amelyhez Intune felhasználói licencet kíván hozzárendelni, majd válassza vagy a **Microsoft Intune** (önálló), vagy az **Enterprise Mobility Suite** lehetőséget.

3.  A felhasználói fiókot most már rendelkezik a szolgáltatás használatához és az eszközöknek a felügyelet alá való regisztrálásához szükséges engedélyekkel.

### Az EMS felhasználói licencek szelektív kezelése a PowerShell segítségével
Előfordulhat, hogy a Microsoft Nagyvállalati mobilitási csomag (EMS) megoldást használó szervezeteknek vannak felhasználói, akik csak az EMS csomagban foglalt Azure Active Directory Premium vagy Intune szolgáltatást igénylik. Az [Azure Active Directory PowerShell-parancsmagok](https://msdn.microsoft.com/library/jj151815.aspx) használatával egy-egy szolgáltatás vagy a szolgáltatások egy részhalmaza is hozzárendelhető. 

A felhasználói licencek EMS-szolgáltatásokhoz való szelektív hozzárendeléséhez nyissa meg a PowerShellt rendszergazdaként egy olyan számítógépen, amelyre telepítve van a [Windows PowerShellhez készült Microsoft Azure Active Directory-modul ](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) megoldással rendelkező számítógépen. A PowerShell helyi számítógépre vagy ADFS-kiszolgálóra telepíthető.

Létre kell hoznia egy új licenctermékváltozat-definíciót, amely csak a szükséges szolgáltatáscsomagokra vonatkozik. Ehhez tiltsa le az alkalmazni nem kívánt csomagokat. Például létrehozhat olyan licenctermékváltozat-definíciót, amely nem rendel hozzá Intune-licencet. Az elérhető szolgáltatások listájának megtekintéséhez írja be:
 
    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus 

Az Intune szolgáltatáscsomag kizárásához a következő parancsot futtathatja. Ugyanezzel a módszerrel kibonthat egy teljes biztonsági csoportot, vagy még részletesebb szűrőket is használhat. 

**1. példa** Új felhasználó létrehozása a parancssorból, és EMS-licenc hozzárendelése a licenc Intune-részének engedélyezése nélkül:

    Connect-MsolService 
        
    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS 
    

Ellenőrizze a következővel:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**2. példa** Az Intune-rész letiltása a hozzárendelt licenccel már rendelkező felhasználó EMS-licencéből:

    Connect-MsolService 
    
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS
 
Ellenőrizze a következővel:
 
    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések* útmutató 4. lépését.
>[!div class="step-by-step"]

>[&larr; **Felhasználók szinkronizálása az Intune-nal**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Felhasználók és eszközök rendszerezése** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  



<!--HONumber=Jun16_HO4-->


