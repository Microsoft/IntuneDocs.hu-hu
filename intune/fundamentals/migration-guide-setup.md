---
title: A Microsoft Intune alapszintű beállítása
description: Ez a cikk a Microsoft Intune beállításához szükséges lépéseket ismerteti.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08041a57ab52f395283e57cda596d00ba168aba1
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556482"
---
# <a name="basic-setup"></a>Alapszintű beállítás

A környezet felmérése után a Microsoft Intune-t kell beállítani.

## <a name="external-dependencies-for-an-intune-deployment"></a>Intune-környezet külső függőségei

### <a name="identity"></a>Identitás

Az Intune-hoz az Azure Active Directoryt (AAD) kell használni felhasználóicsoport- és identitásszolgáltatóként. További információk az alábbiakról:

- [Identitáskövetelmények](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [A címtár-szinkronizálás követelményei](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [Multi-Factor Authentication (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [A felhasználói és eszközcsoportok megtervezése](users-add.md)

- [A felhasználói és eszközcsoportok létrehozása](groups-get-started.md)

Ha a szervezet már használja az Office 365-öt, az Intune is ugyanazt az Azure Active Directory-környezetet kell, hogy használja.

### <a name="pki-optional"></a>Nyilvános kulcsú infrastruktúra (nem kötelező)

Ha az Intune VPN-, Wi-Fi- vagy e-mail-profiljaihoz tanúsítványalapú hitelesítést tervez használni, bizonyosodjon meg róla, hogy a szervezetnél már ki van alakítva a tanúsítványprofilok létrehozására és üzembe helyezésére kész, támogatott [PKI-infrastruktúra](../protect/certificates-configure.md). További tudnivalók az Intune-ban történő tanúsítványkonfigurálásról:

- [SCEP-tanúsítványinfrastruktúra konfigurálása](/intune/certificates-scep-configure)

- [PFX-tanúsítványinfrastruktúra konfigurálása](/intune/certficates-pfx-configure)

## <a name="task-list-for-an-intune-setup"></a>Intune-beállítás feladatlistája

### <a name="task-1-intune-subscription"></a>1. feladat: Intune-előfizetés

Az Intune-ba való Migrálás előtt először Intune- [előfizetésre](account-sign-up.md)van szüksége.

### <a name="task-2-assign-intune-user-licenses"></a>2. feladat: Intune felhasználói licencek kiosztása

- Ismerje meg, [hogyan oszthatja ki az Intune felhasználói licenceit](licenses-assign.md).

- Ha új Azure Active Directory-bérlőt hozott létre, ismerje meg, [hogyan lehet új felhasználókat létrehozni vagy a helyszíni Active Directory (AD) felhasználóit ide szinkronizálni.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>3. feladat: az Intune beállítása MDM-szolgáltatóként

Javasoljuk, hogy az Intune-t a [Microsoft Endpoint Manager felügyeleti központjának](https://go.microsoft.com/fwlink/?linkid=2109431)használatával kezelje.

Állítsa be az MDM-szolgáltatót az **Intune**-ra. Ha másik MDM-szolgáltatót használ, akkor az Intune a Microsoft más felügyeleti konzoljainak is átadhatja a mobileszköz-felügyeletet. Ezek a helyzetek elég ritkán fordulnak elő.

> [!IMPORTANT]
> Ha első alkalommal adja át a mobileszköz-felügyeletet az Intune-nak, akkor mindenképpen az Intune-t adja meg MDM-szolgáltatónak.

Ismerje meg, [hogyan állíthatja be a mobileszköz-felügyeleti szolgáltatót](mdm-authority-set.md).

## <a name="next-step"></a>További lépések

[Eszköz- és alkalmazásszabályzatok](../migration-guide-configure-policies.md) konfigurálása.
