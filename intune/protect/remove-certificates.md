---
title: SCEP- vagy PKCS-tanúsítványok eltávolítása a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: A rendszergazdák az összes adat törlésével, illetve kivonással távolíthatnak el tanúsítványokat a Microsoft Intune-ból. Vannak olyan forgatókönyvek, amelyek során a tanúsítványokat a rendszer automatikusan eltávolítja, például egy eszköz regisztrációjának törlésekor vagy egy megfelelőségi szabályzat eltávolításakor. Olyan forgatókönyvek is vannak, amelyek során a tanúsítványok automatikusan az eszközön maradnak, például az Intune-licenc elvesztésekor vagy eltávolításakor. Tekintse meg az Android, az Android Enterprise, az iOS/iPadOS, a macOS és a Windows rendszerű eszközök különböző módszereit.
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
ms.openlocfilehash: a77780c05b0f637a4ee5100f8c7a1a729c3ec674
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369586"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>SCEP- vagy PKCS-tanúsítványok eltávolítása a Microsoft Intune-ban

Microsoft Intune a tanúsítványok eszközökhöz való hozzáadásához használhatja a Egyszerű tanúsítványigénylési protokoll (SCEP) és a nyilvános kulcsú titkosítási szabvány (PKCS) tanúsítvány-profilokat.

Ezek a tanúsítványok [eltávolíthatók az eszköz](../remote-actions/devices-wipe.md#retire) kivonásakor [vagy](../remote-actions/devices-wipe.md#wipe) kivonásakor. Vannak olyan forgatókönyvek is, ahol a rendszer automatikusan eltávolítja a tanúsítványokat, és olyan forgatókönyveket, amelyekben a tanúsítványok az eszközön maradnak. Ez a cikk néhány gyakori forgatókönyvet és azok PKCS- és SCEP-tanúsítványokra gyakorolt hatását mutatja be.

> [!NOTE]
> A helyszíni Active Directory vagy Azure Active Directory (Azure AD) által eltávolított felhasználó tanúsítványainak eltávolításához és visszavonásához hajtsa végre az alábbi lépéseket a sorrendben:
>
> 1. A felhasználó eszközének törlése vagy kivonása.
> 2. Távolítsa el a felhasználót a helyszíni Active Directory vagy az Azure AD-ből.

## <a name="manually-deleted-certificates"></a>Tanúsítványok manuális törlése

A tanúsítványok manuális törlése olyan forgatókönyv, amely az SCEP-vagy PKCS-tanúsítvány-profilok által kiosztott platformok és tanúsítványok esetében érvényes. Előfordulhat például, hogy egy felhasználó töröl egy tanúsítványt egy eszközről, ha az eszközt egy tanúsítvány-házirend is megcélozta.

Ebben a forgatókönyvben a tanúsítvány törlését követően az eszköz következő bejelentkezésekor a rendszer nem felel meg az Intune-nak, mert hiányzik a várt tanúsítvány. Az Intune ezután kiad egy új tanúsítványt az eszköz megfelelőségének visszaállításához. A tanúsítvány visszaállításához nincs szükség további műveletre.

## <a name="windows-devices"></a>Windows-eszközök

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.
- Az eszköz el lett távolítva egy Azure AD-csoportból.
- A rendszer eltávolítja a tanúsítvány-profilt a csoport-hozzárendelésből.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- A rendszergazda módosítja vagy frissíti a SCEP-profilt.

A főtanúsítvány törlődik, ha:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A SCEP-tanúsítványok az eszközön *maradnak* (a tanúsítványok nem vonhatók vissza vagy nem törlődnek), ha:

- A felhasználó elveszíti az Intune-licencet.
- A rendszergazda visszavonja az Intune-licencet.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

A PKCS-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A főtanúsítvány törlődik, ha:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A PKCS-tanúsítványok az eszközön *maradnak* (a tanúsítványok nem vonhatók vissza és nem távolíthatók el), ha:

- A felhasználó elveszíti az Intune-licencet.
- A rendszergazda visszavonja az Intune-licencet.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.
- A rendszergazda módosítja vagy frissíti a PKCS-profilt.
- A rendszer eltávolítja a tanúsítvány-profilt a csoport-hozzárendelésből.


## <a name="ios-devices"></a>iOS-eszközök

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.
- Az eszköz el lesz távolítva az Azure AD-csoportból.
- A rendszer eltávolítja a tanúsítvány-profilt a csoport-hozzárendelésből.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- A rendszergazda módosítja vagy frissíti a SCEP-profilt.

A főtanúsítvány törlődik, ha:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A SCEP-tanúsítványok az eszközön *maradnak* (a tanúsítványok nem vonhatók vissza vagy nem törlődnek), ha:

- A felhasználó elveszíti az Intune-licencet.
- A rendszergazda visszavonja az Intune-licencet.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

A PKCS-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A PKCS-tanúsítvány eltávolítására a következő esetekben kerül sor:

- A rendszer eltávolítja a tanúsítvány-profilt a csoport-hozzárendelésből.

A főtanúsítvány törlődik, ha:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A PKCS-tanúsítványok az eszközön *maradnak* (a tanúsítványok nem vonhatók vissza és nem távolíthatók el), ha:

- A felhasználó elveszíti az Intune-licencet.
- A rendszergazda visszavonja az Intune-licencet.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.
- A rendszergazda módosítja vagy frissíti a PKCS-profilt.

## <a name="android-knox-devices"></a>Android Knox-eszközök

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.
- Az eszköz el lett távolítva egy Azure AD-csoportból.
- A rendszer eltávolítja a tanúsítvány-profilt a csoport-hozzárendelésből.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.
- A rendszergazda módosítja vagy frissíti a SCEP-profilt.

A főtanúsítvány törlődik, ha:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A SCEP-tanúsítványok az eszközön *maradnak* (a tanúsítványok nem vonhatók vissza vagy nem törlődnek), ha:

- A felhasználó elveszíti az Intune-licencet.
- A rendszergazda visszavonja az Intune-licencet.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

A PKCS-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A főtanúsítvány törlődik, ha:

- A felhasználó törli A regisztrációt.
- Egy rendszergazda futtatja a [törlési](../remote-actions/devices-wipe.md#wipe) műveletet.
- A rendszergazda futtatja [a](../remote-actions/devices-wipe.md#retire) kivonási műveletet.

A PKCS-tanúsítványok az eszközön *maradnak* (a tanúsítványok nem vonhatók vissza és nem távolíthatók el), ha:
- A felhasználó elveszíti az Intune-licencet.

- A rendszergazda visszavonja az Intune-licencet.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.
- A rendszergazda módosítja vagy frissíti a PKCS-profilt.
- A rendszer eltávolítja a tanúsítvány-profilt a csoport-hozzárendelésből.


> [!NOTE]
> Az előző forgatókönyvek esetében a rendszer nem érvényesíti az Android for Work-eszközöket.
> Az Android örökölt eszközök (a nem Samsung, nem munkahelyi profilok eszközei) nincsenek engedélyezve a tanúsítványok eltávolításához.

## <a name="macos-certificates"></a>macOS-tanúsítványok

### <a name="scep-certificates"></a>SCEP-tanúsítványok

Az SCEP-tanúsítvány visszavonására *és* eltávolítására a következő esetekben kerül sor:

- A felhasználó törli A regisztrációt.
- A rendszergazda kivonási [műveletet futtat](../remote-actions/devices-wipe.md#retire) .
- Az eszköz el lett távolítva egy Azure AD-csoportból.
- A rendszer eltávolítja a tanúsítvány-profilt a csoport-hozzárendelésből.

Az SCEP-tanúsítvány visszavonására a következő esetekben kerül sor:

- A rendszergazda módosítja vagy frissíti a SCEP-profilt.

A SCEP-tanúsítványok az eszközön *maradnak* (a tanúsítványok nem vonhatók vissza vagy nem törlődnek), ha:

- A felhasználó elveszíti az Intune-licencet.
- A rendszergazda visszavonja az Intune-licencet.
- A rendszergazda eltávolítja a felhasználót vagy csoportot az Azure AD-ből.

> [!NOTE]
> Az [összes adatot törlő](../remote-actions/devices-wipe.md#wipe) műveletet nem lehet használni a macOS-eszközök gyári beállításainak visszaállításához.

### <a name="pkcs-certificates"></a>PKCS-tanúsítványok

A PKCS-tanúsítványok nem támogatottak macOS rendszeren.

## <a name="next-steps"></a>További lépések

[Tanúsítványok használata a hitelesítéshez](certificates-configure.md)