---
title: "GPO és Intune-szabályzatütközések feloldása| Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 211543b75e2bcda85cd74ab34c254d70f036eebd
ms.openlocfilehash: 7fc97e21fa7e57d8585c421ac12ff0d3c4b366a0


---

# Csoportházirend-objektumok (GPO) és Microsoft Intune-szabályzatütközések feloldása
Az Intune szabályzatai megkönnyítik a beállítások kezelését az Ön által felügyelt Windows-számítógépeken. Használhat például egy olyan házirendet, amellyel Windows tűzfal beállításait szabályozhatja a számítógépeken. Az Intune számos beállítása hasonló a Windows csoportházirend-beállításaihoz. Néha előfordulhat azonban, hogy a két módszer ütközik egymással.

Ütközések esetén a tartományszintű csoportházirend elsőbbséget élvez az Intune szabályzatával szemben, kivéve, ha a számítógép nem tud bejelentkezni a tartományba. Ebben az esetben a rendszer az Intune szabályzatát alkalmazza az ügyfélszámítógépen.

## Mi a teendő a Csoportházirend használata esetén?
Ellenőrizze, hogy az Ön által alkalmazott szabályzatokat nem kezeli-e a csoportházirend. Az ütközések megelőzése érdekében fontolja meg az alábbi eljárások alkalmazását:

-   Helyezze át a számítógépeket egy olyan Active Directory-beli szervezeti egységbe (OU-ba), amelyre nem lettek alkalmazva csoportházirend-beállítások az Intune ügyfél telepítése előtt. Letilthatja továbbá a csoportházirend-öröklést azon szervezeti egységek esetében, amelyek olyan Intune-ban regisztrált számítógépeket tartalmaznak, amelyeken nem kívánja alkalmazni a csoportházirend-beállításokat.

-   Biztonságicsoport-szűrő használatával korlátozza a csoportházirend-objektumok alkalmazását kizárólag az Intune által nem kezelt számítógépekre. 

-   Tiltsa le vagy távolítsa el az Intune szabályzataival ütköző csoportházirend-objektumokat.

Az Active Directoryról és a Windows csoportházirendjéről további információt a Windows Server dokumentációjában talál.

## Meglévő csoportházirend-objektumok szűrése az Intune szabályzatával való ütközések elkerülése érdekében
Ha azonosította azokat a csoportházirend-objektumokat (GPO-kat), amelyek beállításai ütköznek az Intune szabályzataival, biztonságicsoport-szűrőkkel az Intune által nem kezelt számítógépekre korlátozhatja a csoportházirend-objektumok alkalmazását.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


A csoportházirend lehetővé teszi, hogy a GPO-kat csak azokra a biztonsági csoportokra alkalmazza, amelyek egy adott GPO Csoportházirend kezelése konzoljának **Biztonsági szűrés** területén vannak megadva. Alapértelmezés szerint a GPO-k a **Hitelesített felhasználók**csoportra vonatkoznak.

-   Az **Active Directory – felhasználók és számítógépek** beépülő modulban hozzon létre egy új biztonsági csoportot, amely az Intune használatával kezelni nem kívánt számítógépeket és felhasználói fiókokat tartalmazza. A csoportnak adhatja például a **Nem Microsoft Intune-beli** nevet.

-   A Csoportházirend kezelése konzolban, a kiválasztott GPO **Delegálás** lapján, kattintson a jobb gombbal az új biztonsági csoportra, és delegálja a megfelelő **olvasási** és **csoportházirend-alkalmazási** engedélyeket a biztonsági csoport felhasználóinak és számítógépeinek. A**csoportházirend-alkalmazási** engedélyek a **Speciális** párbeszédpanelen érhetők el.)

-   Ezután alkalmazza az új biztonságicsoport-szűrőt a kiválasztott GPO-ra, és távolítsa el az alapértelmezett **Hitelesített felhasználók** szűrőt.

Az új biztonsági csoportot regisztrációként kell kezelni az Intune szolgáltatásmódosításaiban.

### További információ
[Windows rendszerű számítógépek felügyelete a Microsoft Intune-nal](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


