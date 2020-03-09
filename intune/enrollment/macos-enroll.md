---
title: Regisztráció beállítása macOS-eszközökhöz
titleSuffix: Microsoft Intune
description: Útmutató macOS-eszközök Intune-ban való regisztrációjának beállításához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cddb9b74d9132ace07c17a3156e61148b720d66
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369022"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Regisztráció beállítása macOS-eszközökhöz az Intune-ban

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Az Intune lehetővé teszi a macOS rendszerű eszközök felügyeletét, és hozzáférést biztosít a felhasználók számára a céges levelezéshez és alkalmazásokhoz.

Az Intune rendszergazda beállíthatja a vállalati tulajdonú macOS-eszközök és a személyes tulajdonú macOS-eszközök („saját eszköz használata” vagy BYOD) regisztrációját. 

## <a name="prerequisites"></a>Előfeltételek

macOS-eszközök regisztrációjának indítása előtt végezze el az alábbiakat:

- Győződjön [meg arról, hogy az eszköz jogosult az Apple-eszközök regisztrálására](https://support.apple.com/en-us/HT204142#eligibility).
- [Tartományok beállítása](../fundamentals/custom-domain-name-configure.md)
- [Az MDM-szolgáltató beállítása](../fundamentals/mdm-authority-set.md)
- [Csoportok létrehozása](../fundamentals/groups-add.md)
- [A Céges portál konfigurálása](../apps/company-portal-app.md)
- Felhasználói licencek kiosztása a [Microsoft 365 felügyeleti központban](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Apple MDM push-tanúsítvány beszerzése](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>A felhasználó tulajdonában macOS-eszközök (BYOD)

Lehetővé teheti a felhasználók számára, hogy regisztrálják saját eszközeiket az Intune-felügyeletbe. Ez az úgynevezett "saját eszköz használata" vagy BYOD. Az előfeltételek és a hozzárendelt felhasználói licencek elvégzése után a felhasználók a következő módon regisztrálhatják az eszközeiket:
- a [Céges portál](https://portal.manage.microsoft.com) webhelyre lépve, vagy
- Töltse le a Mac Céges portál alkalmazást a következő címen: [aka.MS/EnrollMyMac](https://aka.ms/EnrollMyMac).

A felhasználók az online regisztráció lépéseire mutató hivatkozást is küldhetnek: [MacOS-eszköz regisztrálása az Intune-ban](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Más végfelhasználói feladatokkal kapcsolatos további információkért tanulmányozza a következő cikkeket:

- [Információk végfelhasználóknak a Microsoft Intune használatáról](../fundamentals/end-user-educate.md)
- [macOS-eszköz használata az Intune-nal](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>Vállalati tulajdonban lévő macOS-eszközök
A felhasználóknak eszközöket vásárló szervezetek számára az Intune a következő módszereket támogatja a vállalati tulajdonban lévő macOS-eszközök regisztrálásához:
- [Az Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-macos.md): A szervezetek macOS-eszközöket vásárolhatnak az Apple Device Enrollment Programján (DEP) keresztül. A DEP vezeték nélkül képes telepíteni egy regisztrációs profilt, amely felügyelet alá helyezi az eszközöket.
- [Eszközregisztráció-kezelő (DEM)](device-enrollment-manager-enroll.md): Egy DEM-fiókba akár 1000 eszköz is regisztrálható.

## <a name="block-macos-enrollment"></a>macOS-regisztráció letiltása
Alapértelmezés szerint az Intune engedélyezi a macOS-eszközök regisztrálását. A macOS-eszközök regisztrálásának letiltásáról a [Típus szerinti korlátozás beállítása](enrollment-restrictions-set.md) című témakörben olvashat.

## <a name="enroll-virtual-macos-machines-for-testing"></a>Virtuális macOS-gépek regisztrálása teszteléshez

> [!NOTE]
> A virtuális macOS-gépekhez csak teszteléshez jár támogatás. A virtuális macOS-gépeket ne használja végfelhasználói termelési eszközökként. 

A virtuális macOS-gépeket a Parallels Desktop vagy a VMWare Fusion segítségével regisztrálhatja tesztelésre. 

A Parallels Desktophoz meg kell adnia a virtuális gépek hardvertípusát és sorozatszámát, hogy az Intune felismerje őket. A teszteléshez szükséges beállítások beállításához kövesse a Parallels utasításait a hardver típusának és [sorozatszámának](http://kb.parallels.com/123455) beállításához. Azt javasoljuk, hogy a virtuális gépeket futtató eszközök hardvertípusa egyezzen meg a létrehozandó virtuális gépek hardvertípusával. A hardvertípust az **Apple menü** > **A Mac névjegye** > **Rendszerjelentés** > **Modellazonosító** területen találhatja meg. 

A VMware Fusion esetében [szerkesztenie kell a .vmx-fájlt](https://kb.vmware.com/s/article/1014782) a virtuális gép hardvermodelljének és sorozatszámának megadásához. Azt javasoljuk, hogy a virtuális gépeket futtató eszközök hardvertípusa egyezzen meg a létrehozandó virtuális gépek hardvertípusával. A hardvertípust az **Apple menü** > **A Mac névjegye** > **Rendszerjelentés** > **Modellazonosító** területen találhatja meg. 

## <a name="user-approved-enrollment"></a>Felhasználó által jóváhagyott regisztráció
A felhasználói jóváhagyott MDM-regisztráció egy olyan macOS-regisztrációs típus, amellyel bizonyos biztonsági szempontból kényes beállításokat kezelhet. További információt az [Apple támogatási dokumentumában találhat](https://support.apple.com/HT208019).  
 
A BYOD beléptetési folyamata során a rendszer kérni fogja a felhasználótól, hogy manuálisan hagyja jóvá az Apple felügyeleti profilt. A macOS rendszerhez készült Céges portál alkalmazásban útmutatást nyújt. Bár a felügyeleti profil jóváhagyása nem szükséges a regisztráció befejezéséhez, az Intune a felhasználó által jóváhagyott regisztrációkat javasolja. Ha a felhasználó nem hagyja jóvá a profilt a regisztráció során, a felhasználó a **Rendszerbeállítások** > a **profilok**lehetőségre, válassza ki a felügyeleti profilt, és válassza a **jóváhagyás**lehetőséget.    

### <a name="find-out-if-a-device-is-user-approved"></a>Annak megállapítása, hogy az eszköz felhasználó által jóváhagyva
1. Jelentkezzen be a [Microsoft Endpoint Manager felügyeleti központjába](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Válassza az **eszközök** > **minden eszköz**lehetőséget, > válassza ki az eszközt > **hardvert**.
3. Keresse meg a **felhasználó által jóváhagyott beléptetés** mezőt.


## <a name="next-steps"></a>További lépések

A macOS-eszközök regisztrációját követően [egyéni beállításokat hozhat létre a macOS-eszközökhöz](../configuration/custom-settings-macos.md).
