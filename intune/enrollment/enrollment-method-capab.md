---
title: Intune regisztrációs módszer képességei Windows-eszközökhöz
titleSuffix: Microsoft Intune
description: A Windows-eszközök regisztrálási módszereinek képességei.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6b12bb0066c37eb470065a169a3ad7866c69a17
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503262"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Intune regisztrációs módszer képességei Windows-eszközökhöz
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Több módszer is van a munkaerő eszközeinek Intune-ban való regisztrálására. Minden módszer eltérő ajánlott eljárásokkal és funkciókkal bír, ahogyan a lenti tábla mutatja.

## <a name="best-practices-by-enrollment-method"></a>Ajánlott eljárások regisztrációs módszer szerint
| **Gyakorlati tanácsok** | **[Azure AD-hez csatlakoztatva](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-hez csatlakozott az Autopilot (felhasználói vezérelt mód)](enrollment-autopilot.md)** |**[Az Azure AD-hez csatlakozott az Autopilot (saját üzembe helyezési mód)](enrollment-autopilot.md)** |**[Tömeges](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[CSOPORTHÁZIREND-objektum](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Közös felügyelet](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Az EDU-ban gyakran használt|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Az eszközök megosztott eszközként használhatók|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|A személyes eszközöknek hozzá kell férniük a céges erőforrásokhoz|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Alkalmazások önálló karbantartása|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funkciók regisztrációs módszer szerint

| **Funkciók** | **[Azure AD-hez csatlakoztatva](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-hez csatlakozott az Autopilot (felhasználói vezérelt mód)](enrollment-autopilot.md)** |**[Az Azure AD-hez csatlakozott az Autopilot (saját üzembe helyezési mód)](enrollment-autopilot.md)** |**[Tömeges](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[CSOPORTHÁZIREND-objektum](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Közös felügyelet](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Conditional Access                                      |![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
|A felhasználó az eszközhöz van rendelve                    |![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
|Azure AD Premium szükséges                               |![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
|Eszköz fel tudja mérni a CA által védett erőforrásokat             |![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
|A felhasználók nem lehetnek rendszergazdák az eszközeiken               |![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Az eszközbeállítás konfigurálása        |![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Eszközök regisztrálása felhasználói beavatkozás nélkül      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
|PowerShell-parancsfájlok futtatása                       |![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/checkmark.png)\*| 
|Támogatja az automatikus regisztrációt az AD-tartományhoz való csatlakozás után      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
|Támogatja az automatikus regisztrációt a hibrid Azure AD-hoz való csatlakozás után|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
|Támogatja az automatikus regisztrációt az Azure AD-hoz való csatlakozás után       |![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|

@no__t – 0 ügyfélalkalmazások munkaterhelését Configuration Manager kell áthelyezni az Intune Pilot vagy az Intune-ba.

## <a name="next-steps"></a>További lépések

[Windows-regisztráció beállítása](windows-enroll.md)

