---
title: SCEP- vagy PKCS-tanúsítványok eltávolítása a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: A rendszergazdák az összes adat törlésével, illetve kivonással távolíthatnak el tanúsítványokat a Microsoft Intune-ból. Vannak olyan forgatókönyvek, amelyek során a tanúsítványokat a rendszer automatikusan eltávolítja, például egy eszköz regisztrációjának törlésekor vagy egy megfelelőségi szabályzat eltávolításakor. Olyan forgatókönyvek is vannak, amelyek során a tanúsítványok automatikusan az eszközön maradnak, például az Intune-licenc elvesztésekor vagy eltávolításakor. Lásd az Android, az Android Enterprise, az iOS, a macOS és a Windows rendszerű eszközökre vonatkozó különféle módszereket.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: dbf6d95c8902a95993b972ff7639d4afb4324ac8
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410177"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>SCEP- vagy PKCS-tanúsítványok eltávolítása a Microsoft Intune-ban

In Microsoft Intune, you can use Simple Certificate Enrollment Protocol (SCEP) and Public Key Cryptography Standards (PKCS) certificate profiles to add certificates to devices.

These certificates can be removed when you [wipe](../remote-actions/devices-wipe.md#wipe) or [retire](../remote-actions/devices-wipe.md#retire) the device. There are also scenarios where certificates are automatically removed, and scenarios where certificates stay on the device. Ez a cikk néhány gyakori forgatókönyvet és azok PKCS- és SCEP-tanúsítványokra gyakorolt hatását mutatja be.

> [!NOTE]
> To remove and revoke certificates for a user who's being removed from on-premises Active Directory or Azure Active Directory (Azure AD), follow these steps in order:
>
> 1. Wipe or retire the user's device.
> 2. Remove the user from on-premises Active Directory or Azure AD.

## <a name="manually-deleted-certificates"></a>Manually deleted certificates

Manual deletion of a certificate is a scenario that applies across platforms and certificates provisioned by SCEP or PKCS certificate profiles. For example, a user might delete a certificate from a device, when the device remains targeted by a certificate policy.

In this scenario, after the certificate is deleted, the next time the device checks in with Intune it's found to be out of compliance as it is missing the expected certificate. Intune then issues a new certificate to restore the device to compliance. No additional action is needed to restore the certificate.

## <a name="windows-devices"></a>Windows-eszközök

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.
- The device is removed from an Azure AD group.
- A certificate profile is removed from the group assignment.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- An administrator changes or updates the SCEP profile.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

SCEP certificates *stay* on the device (certificates aren't revoked or removed) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Azure AD.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

A PKCS-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

PKCS certificates *stay* on the device (certificates aren't revoked or removed) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Azure AD.
- An administrator changes or updates the PKCS profile.
- A certificate profile is removed from the group assignment.


## <a name="ios-devices"></a>iOS devices

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.
- The device is removed from the Azure AD group.
- A certificate profile is removed from the group assignment.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- An administrator changes or updates the SCEP profile.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

SCEP certificates *stay* on the device (certificates aren't revoked or removed) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Azure AD.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

A PKCS-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

A PKCS-tanúsítvány eltávolítására a következő esetekben kerül sor:

- A certificate profile is removed from the group assignment.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

PKCS certificates *stay* on the device (certificates aren't revoked or removed) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Azure AD.
- An administrator changes or updates the PKCS profile.

## <a name="android-knox-devices"></a>Android Knox-eszközök

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.
- The device is removed from an Azure AD group.
- A certificate profile is removed from the group assignment.
- An administrator removes the user or group from Azure AD.
- An administrator changes or updates the SCEP profile.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

SCEP certificates *stay* on the device (certificates aren't revoked or removed) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Azure AD.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

A PKCS-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](../remote-actions/devices-wipe.md#wipe) action.
- An administrator runs the [retire](../remote-actions/devices-wipe.md#retire) action.

PKCS certificates *stay* on the device (certificates aren't revoked or removed) when:
- A user loses the Intune license.

- An administrator withdraws the Intune license.
- An administrator removes the user or group from Azure AD.
- An administrator changes or updates the PKCS profile.
- A certificate profile is removed from the group assignment.


> [!NOTE]
> Android for Work devices are not validated for the preceding scenarios.
> Android legacy devices (any non-Samsung, non-work profile devices) are not enabled for certificate removal.

## <a name="macos-certificates"></a>macOS-tanúsítványok

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A user unenrolls.
- An administrator runs a [retire](../remote-actions/devices-wipe.md#retire) action.
- The device is removed from an Azure AD group.
- A certificate profile is removed from the group assignment.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- An administrator changes or updates the SCEP profile.

SCEP certificates *stay* on the device (certificates aren't revoked or removed) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Azure AD.

> [!NOTE]
> Az [összes adatot törlő](../remote-actions/devices-wipe.md#wipe) műveletet nem lehet használni a macOS-eszközök gyári beállításainak visszaállításához.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

PKCS certificates aren't supported on macOS.

## <a name="next-steps"></a>További lépések

[Use certificates for authentication](certificates-configure.md)