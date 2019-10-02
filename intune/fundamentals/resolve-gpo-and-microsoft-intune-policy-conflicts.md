---
title: A GPO- és Intune-házirendek ütközéseinek feloldása
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan szüntetheti meg az ütközéseket a Csoportházirend és az Intune konfigurációs szabályzatai között.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9834181d4b6c010cc5ca83eadfb424d036ab13d6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732103"
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>Csoportházirend-objektumok (GPO) és Microsoft Intune-szabályzatütközések feloldása

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

> [!NOTE]
> A jelen témakörben ismertetett információk csak azokra a PC-ként felügyelt Windows-számítógépekre vonatkoznak, amelyeket az Intune szoftverügyfél segítségével felügyel.

Az Intune szabályzatai megkönnyítik a Windows-számítógépek beállításainak kezelését. Például szabályzat segítségével felügyelheti a Windows tűzfal beállításait a számítógépeken. Az Intune számos beállítása hasonló a Windows csoportházirend-beállításaihoz. Esetenként azonban előfordulhat, hogy a két módszer ütközik egymással.

Ütközések esetén a tartományszintű csoportházirend elsőbbséget élvez az Intune szabályzatával szemben, kivéve, ha a számítógép nem tud bejelentkezni a tartományba. Ebben az esetben a rendszer az Intune szabályzatát alkalmazza az ügyfélszámítógépen.

## <a name="what-to-do-if-you-are-using-group-policy"></a>Mi a teendő a Csoportházirend használata esetén?
Győződjön meg róla, hogy az Ön által alkalmazott szabályzatok nem állnak-e csoportházirend felügyelete alatt. Az ütközések megelőzése érdekében használjon egyet vagy többet az alábbi módszerek közül:

- Helyezze át a számítógépeket egy olyan Active Directory-beli szervezeti egységbe (OU-ba), amelyre nem lettek alkalmazva csoportházirend-beállítások az Intune ügyfél telepítése előtt. Letilthatja továbbá a csoportházirend-öröklést azon szervezeti egységek esetében, amelyek olyan Intune-ban regisztrált számítógépeket tartalmaznak, amelyeken nem kívánja alkalmazni a csoportházirend-beállításokat.

- Biztonságicsoport-szűrő használatával korlátozza a csoportházirend-objektumok alkalmazását kizárólag az Intune által nem kezelt számítógépekre.

- Tiltsa le vagy távolítsa el az Intune szabályzataival ütköző csoportházirend-objektumokat.

Az Active Directoryról és a Windows csoportházirendjéről további információt a Windows Server dokumentációjában talál.

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>Meglévő csoportházirend-objektumok szűrése az Intune szabályzatával való ütközések elkerülése érdekében
Ha azonosította azokat a csoportházirend-objektumokat, amelyek beállításai ütköznek az Intune szabályzataival, biztonságicsoport-szűrőkkel az Intune által nem kezelt számítógépekre korlátozhatja a csoportházirend-objektumok alkalmazását.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1. Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

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

2. Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3. Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    - For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    - For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4. Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    - For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    - For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


A csoportházirend-objektumok alkalmazását korlátozhatja csak azokra a biztonsági csoportokra, amelyek a kijelölt csoportházirend-objektum Csoportházirend kezelése konzoljának **Biztonsági szűrés** területén vannak megadva. Alapértelmezés szerint a csoportházirend-objektumok a *Hitelesített felhasználók* csoportra vonatkoznak.

- Az **Active Directory – felhasználók és számítógépek** beépülő modulban hozzon létre egy új biztonsági csoportot, amely azokat a számítógépeket és felhasználói fiókokat tartalmazza, amelyeket nem kíván az Intune által kezelni. A csoportnak adhatja például a *Nem szerepel a Microsoft Intune-ban* nevet.

- A Csoportházirend kezelése konzolban, a kiválasztott GPO **Delegálás** lapján, kattintson a jobb gombbal az új biztonsági csoportra, és delegálja a megfelelő **olvasási** és **csoportházirend-alkalmazási** engedélyeket a biztonsági csoport felhasználóinak és számítógépeinek. A**csoportházirend-alkalmazási** engedélyek a **Speciális** párbeszédpanelen érhetők el.)

- Ezután alkalmazza az új biztonságicsoport-szűrőt a kiválasztott GPO-ra, és távolítsa el az alapértelmezett **Hitelesített felhasználók** szűrőt.

Az új biztonsági csoportot regisztrációként kell kezelni az Intune szolgáltatásmódosításaiban.

## <a name="see-also"></a>Lásd még:
[Windows rendszerű számítógépek felügyelete a Microsoft Intune-nal](../manage-windows-pcs-with-microsoft-intune.md)
