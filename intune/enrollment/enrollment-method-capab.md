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
ms.openlocfilehash: 30b46fcbb7ec6963e855c79478dbdef5b5cd8b90
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729939"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Az Intune regisztrációs módszer lehetőségek Windows-eszközök esetében
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Többféleképpen is lehet regisztrálni a dolgozók eszközeit az Intune-ban. Minden módszer eltérő ajánlott eljárásokkal és funkciókkal bír, ahogyan a lenti tábla mutatja.

## <a name="best-practices-by-enrollment-method"></a>Ajánlott eljárások regisztrációs módszer szerint
| **Gyakorlati tanácsok** | **[Azure AD-hez csatlakoztatva](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-hez csatlakozott az Autopilot (felhasználói vezérelt mód)](enrollment-autopilot.md)** |**[Az Azure AD-hez csatlakozott az Autopilot (saját üzembe helyezési mód)](enrollment-autopilot.md)** |**[Tömeges](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[CSOPORTHÁZIREND-OBJEKTUM](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Közös felügyelet](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Az EDU-ban gyakran használt|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Az eszközök megosztott eszközként használhatók|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|A személyes eszközöknek hozzá kell férniük a céges erőforrásokhoz|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Alkalmazások önálló karbantartása|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funkciók regisztrációs módszer szerint

| **Funkciók** | **[Azure AD-hez csatlakoztatva](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-hez csatlakozott az Autopilot (felhasználói vezérelt mód)](enrollment-autopilot.md)** |**[Az Azure AD-hez csatlakozott az Autopilot (saját üzembe helyezési mód)](enrollment-autopilot.md)** |**[Tömeges](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[CSOPORTHÁZIREND-OBJEKTUM](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Közös felügyelet](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Feltételes hozzáférés                                      |![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|![Pipa](./media/enrollment-method-capab/checkmark.png)|
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

\*Configuration Manager az ügyfélalkalmazások munkaterheléseit az Intune Pilot vagy az Intune szolgáltatásba kell áthelyezni.

## <a name="next-steps"></a>További lépések

[Windows-regisztráció beállítása](windows-enroll.md)

