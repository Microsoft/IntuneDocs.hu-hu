---
title: A Microsoft Intune szolgáltatásba való regisztráció vagy bejelentkezés
description: Regisztráljon Microsoft Intune előfizetésre, vagy jelentkezzen be az előfizetésével való kezdéshez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78d38b72c9853a9eadaf71fcdff7567fc66d35ca
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414675"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>A Microsoft Intune szolgáltatásba való regisztráció vagy bejelentkezés

Ez a témakör arról tájékoztatja a rendszergazdákat, hogy miképpen regisztrálhatnak Intune-fiókra.

Mielőtt regisztrálna az Intune-ra, ellenőrizze, hogy rendelkezik-e már Microsoft Online Services-fiókkal, Nagyvállalati Szerződéssel vagy egyenértékű mennyiségi licencszerződéssel. A Microsoft mennyiségi licencszerződései és az egyéb Microsoft-felhőszolgáltatások előfizetései (például az Office 365) általában magukban foglalnak egy munkahelyi vagy iskolai fiókot.

Ha már rendelkezik munkahelyi vagy iskolai fiókkal, **jelentkezzen be** vele, és adja hozzá az Intune-t az előfizetéshez. Ha még nem, **regisztrálhat** egy új fiókot, amellyel használatba veheti az Intune-t a cégében.

>[!WARNING]
>Meglévő munkahelyi vagy iskolai fiókok nem vonhatók össze újonnan regisztrált fiókokkal.

## <a name="how-to-sign-up-for-intune"></a>Regisztráció az Intune-ra

1. Látogasson el az [Intune regisztrációs oldalára](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

   ![Képernyőkép a Microsoft Intune próbaverziójának fiókregisztrációs weboldaláról](./media/account-sign-up/account-sign-up-site.png)

2. Új Intune-előfizetése kezeléséhez lépjen be vagy regisztráljon a regisztrációs oldalon.

## <a name="post-sign-up-considerations"></a>A regisztrációt követően megfontolandó szempontok

Az új előfizetés regisztrálása után e-mailben elküldjük a fiókadatait a regisztráció során megadott e-mail címre. Az e-mail megerősíti, hogy az előfizetés aktív.

A regisztrációs folyamat befejezése után a rendszer átirányítja a Microsoft 365 felügyeleti központba, amely a felhasználók hozzáadására és a licencek hozzárendelésére szolgál. Ha kizárólag az alapértelmezett onmicrosoft.com tartományt használó felhőalapú fiókokkal rendelkezik, akkor már ennél a lépésnél felveheti a felhasználókat, és hozzárendelheti a licenceket. Ha azonban a szervezet [egyéni tartománynevét](custom-domain-name-configure.md) szeretné használni, illetve szeretné [szinkronizálni a felhasználóifiók-adatokat](users-add.md#sync-active-directory-and-add-users-to-intune) a helyi Active Directoryval, zárja be a böngészőablakot.

## <a name="sign-in-to-microsoft-intune"></a>Bejelentkezés Microsoft Intune

Miután regisztrált az Intune-ra, bármilyen, [támogatott böngészővel](supported-devices-browsers.md#intune-supported-web-browsers) rendelkező eszközt használhat az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba való bejelentkezéshez a szolgáltatás felügyeletéhez.

Alapértelmezés szerint a fiókjának a következő engedélyek egyikével kell rendelkeznie az Azure AD-ben:

- Globális rendszergazda
- Intune szolgáltatás-rendszergazda (más néven Intune-rendszergazda)

Ha hozzáférést szeretne biztosítani a szolgáltatás felügyeletéhez más engedélyekkel rendelkező felhasználók számára, tekintse meg a [szerepköralapú Access Control](role-based-access-control.md)

### <a name="intune-admin-portal-url"></a>Intune felügyeleti portál URL-címe

Microsoft 365 felügyeleti központ: https://devicemanagement.microsoft.com

Intune Azure Portal: https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune for Education: https://intuneeducation.portal.azure.com

Klasszikus Intune-portál: https://manage.microsoft.com a klasszikus Intune-portál csak az Intune PC-s szoftverrel regisztrált eszközök felügyeletére használatos.

### <a name="urls-for-intune-services-provided-by-office-365"></a>Az Office 365 által biztosított Intune-szolgáltatások URL-címei

Microsoft 365 Vállalati verzió: https://portal.microsoft.com/adminportal

Office 365 mobileszköz-kezelés: https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>További információ

[Nem lehet bejelentkezni az Office 365-be, az Azure-ba vagy az Intune-ba](https://support.microsoft.com/help/2412085)
