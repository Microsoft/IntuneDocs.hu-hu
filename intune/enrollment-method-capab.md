---
title: Az Intune regisztrációs módszer lehetőségek Windows-eszközök esetében
titleSuffix: Microsoft Intune
description: Képességek az egyes Windows-eszközökhöz regisztrációs módszer.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b9c427cb019093bdfbf9fe27bbf3b05a48ef6d8
ms.sourcegitcommit: bc3450fc7f19006b500edf5b395c01559b483ea4
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/02/2019
ms.locfileid: "71301980"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Az Intune regisztrációs módszer lehetőségek Windows-eszközök esetében
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Többféleképpen is lehet regisztrálni a dolgozók eszközeit az Intune-ban. Minden módszer eltérő ajánlott eljárásokkal és funkciókkal bír, ahogyan a lenti tábla mutatja.

## <a name="best-practices-by-enrollment-method"></a>Ajánlott eljárások regisztrációs módszer szerint
| **Gyakorlati tanácsok** | **[Azure AD-hez csatlakoztatva](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-hez csatlakozott az Autopilot (felhasználói vezérelt mód)](enrollment-autopilot.md)** |**[Az Azure AD-hez csatlakozott az Autopilot (saját üzembe helyezési mód)](enrollment-autopilot.md)** |**[Tömeges](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[CSOPORTHÁZIREND-OBJEKTUM](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Közös felügyelet](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Az EDU-ban gyakran használt|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Az eszközök megosztott eszközként használhatók|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|A személyes eszközöknek hozzá kell férniük a céges erőforrásokhoz|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Alkalmazások önálló karbantartása|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funkciók regisztrációs módszer szerint

| **Funkciók** | **[Azure AD-hez csatlakoztatva](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-hez csatlakozott az Autopilot (felhasználói vezérelt mód)](enrollment-autopilot.md)** |**[Az Azure AD-hez csatlakozott az Autopilot (saját üzembe helyezési mód)](enrollment-autopilot.md)** |**[Tömeges](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[CSOPORTHÁZIREND-OBJEKTUM](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Közös felügyelet](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Feltételes hozzáférés                                      |![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|
|A felhasználó az eszközhöz van rendelve                    |![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|
|Azure AD Premium szükséges                               |![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|
|Eszköz fel tudja mérni a CA által védett erőforrásokat             |![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|
|A felhasználók nem lehetnek rendszergazdák az eszközeiken               |![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Az eszközbeállítás konfigurálása        |![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Eszközök regisztrálása felhasználói beavatkozás nélkül      |![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|
|PowerShell-parancsfájlok futtatása                       |![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/checkmark.png)\*| 
|Támogatja az automatikus regisztrációt az AD-tartományhoz való csatlakozás után      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|
|Támogatja az automatikus regisztrációt a hibrid Azure AD-hoz való csatlakozás után|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|
|Támogatja az automatikus regisztrációt az Azure AD-hoz való csatlakozás után       |![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![Pipa](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|

\*Configuration Manager az ügyfélalkalmazások munkaterheléseit az Intune Pilot vagy az Intune szolgáltatásba kell áthelyezni.

## <a name="next-steps"></a>További lépések

[Windows-regisztráció beállítása](windows-enroll.md)

