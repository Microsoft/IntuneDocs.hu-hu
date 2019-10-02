---
title: A Mobile Threat Defense-összekötő engedélyezése a Microsoft Intune-ban
titleSuffix: Microsoft Intune
description: A Mobile Threat Defense (MTD) partner és a Microsoft Intune közötti összekötő engedélyezése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac49edcd4ea71bdbc83cfa093f2bb5e42aefd54
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729563"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>A Mobile Threat Defense-összekötő engedélyezése az Intune-ban

> [!NOTE] 
> Ez a témakör minden Mobile Threat Defense-partnerre vonatkozik.

A Mobile Threat Defense (MTD) beállítása során konfigurált egy, az MTD-partnerkonzolra vonatkozó fenyegetésosztályozási szabályzatot, és létrehozta az eszközmegfelelőségi szabályzatot az Intune-ban. Ha már konfigurálta az Intune-összekötőt a MTD-partner konzolon, most már engedélyezheti a MTD-MTD kapcsolatát.

Amikor új alkalmazást integrál az Intune Mobile Threat Defense-be, és engedélyezi az Intune-nal való kapcsolatot, az Intune egy klasszikus feltételes hozzáférési szabályzatot hoz létre Azure Active Directoryban. Minden olyan MTD-alkalmazás, amelyet integrál, beleértve a [DEFENDER ATP](advanced-threat-protection.md) -t vagy bármely további [MTD-partnert](mobile-threat-defense.md#mobile-threat-defense-partners), új klasszikus feltételes hozzáférési szabályzatot hoz létre. Ezek a szabályzatok figyelmen kívül hagyhatók, de nem szerkeszthetők, nem törölhetők és nem tilthatók le.

Klasszikus feltételes hozzáférési szabályzatok a MTD-alkalmazásokhoz: 

- Az Intune-MTD arra használják, hogy az eszközök regisztrálva legyenek az Azure AD-ben, hogy a MTD-partnerekkel való kommunikáció előtt rendelkezzenek az eszköz azonosítójával. Az azonosító megadása kötelező, hogy az eszközök és az állapotuk sikeresen jelentse az Intune-nak.  
- Semmilyen más felhőalapú alkalmazásra vagy erőforrásra nincs hatással.  
- Nem különböznek a MTD kezeléséhez esetlegesen létrehozott feltételes hozzáférési házirendektől.
- Alapértelmezés szerint a kiértékeléshez használt egyéb feltételes hozzáférési szabályzatok nem működnek együtt.  

A klasszikus feltételes hozzáférési szabályzatok megjelenítéséhez [Az Azure](https://portal.azure.com/#home)-ban lépjen **Azure Active Directory** > a**feltételes hozzáférés** > **klasszikus házirendjei**elemre.


## <a name="to-enable-the-mtd-connector"></a>Az MTD-összekötő engedélyezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

4. Az **Intune-irányítópulton** válassza az **Eszközmegfelelőség**, majd a **Beállítás** szakaszban a **Mobile Threat Defense** elemet.

5. A **Mobile Threat Defense** panelen válassza a **Hozzáadás** elemet.

6. A legördülő listában jelölje ki a saját MTD-megoldását mint **Beállítani kívánt Mobile Threat Defense-összekötőt**.

    ![Az MTD beállítása az Azure-beli Intune-portálon](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. A szervezet igényeinek megfelelően adja meg a kapcsolós beállításokat. Az elérhető kapcsolós megoldások az MTD-partnertől függenek.

## <a name="mtd-toggle-options"></a>Az MTD kapcsolós megoldásai

A cég igényei alapján eldöntheti, hogy az MTD mely kapcsolós beállításait kell engedélyeznie. További részletek:

- **Android 4.1 + rendszerű eszközök csatlakoztatása a (z) [MTD-partner neve] for Work MTD**: Ha engedélyezi ezt a beállítást, az Android 4.1 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.
  - **Nem megfelelőként való megjelölés, ha nem érkezik ilyen érték**: Ha az Intune nem kap információt a platformon található eszközről az MTD-partnertől, vegye figyelembe, hogy az eszköz nem megfelelő.
<br></br>
- **IOS 8.0 + rendszerű eszközök csatlakoztatása a (z) [MTD partner neve] for Work MTD**: Ha engedélyezi ezt a beállítást, az iOS 8.0 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.
  - **Nem megfelelőként való megjelölés, ha nem érkezik ilyen érték**: Ha az Intune nem kap információt a platformon található eszközről az MTD-partnertől, vegye figyelembe, hogy az eszköz nem megfelelő.
<br></br>
- **Alkalmazások szinkronizálásának engedélyezése iOS**-eszközökhöz: Lehetővé teszi a Mobile Threat Defense-partner számára, hogy az Intune-ból származó iOS-alkalmazások metaadatait a veszélyforrások elemzése céljából használja.

- Nem **támogatott operációsrendszer-verziók letiltása**: Letiltja, ha az eszköz a minimális támogatott verziónál kisebb operációs rendszert futtat.

- **A partnernek nem válaszoló napok száma**: Ennyi nap inaktivitás után veszi figyelembe, hogy az Intune nem válaszol a partnernek, mert a kapcsolat megszakad. Az Intune nem veszi figyelembe a nem válaszoló MTD-partnerek megfelelőségi állapotát.

> [!IMPORTANT] 
> Ha lehetséges, javasoljuk, hogy az eszköz megfelelőségének és a feltételes hozzáférési szabályzat szabályainak létrehozása előtt vegye fel és rendelje hozzá a MTD-alkalmazásokat. Ez segít biztosítani, hogy a MTD alkalmazás készen álljon, és elérhető legyen a végfelhasználók számára az e-mailekhez vagy más vállalati erőforrásokhoz való hozzáféréshez.

> [!TIP]
> A Mobile Threat Defense panelen látható a **Kapcsolat állapota** és a **Legutóbb szinkronizálva**, mely utóbbi az Intune és az MTD-partner közötti szinkronizálásra vonatkozik.
